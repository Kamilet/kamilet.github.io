---
layout: javascript
title: "Photoshop脚本：替换字体"
date: 2020-08-21 16:25:36 +0800
lang: cn
nav: post
category: javascript
tags: [website]
---

* content
{:toc}

用法：
将脚本内容另存为.jsx文件。
打开有文字图层的文档，并在Photoshop中打开本脚本。
弹出的第1个对话框会显示所有字体的Postscript名称，输入其中1个用于被替换。
在弹出的第2个对话框里，输入另1个用于替换。

<!-- more -->
{% highlight ruby lineno %}
// Enhanced by Kamilet From Kamilet.cn
// List and Replace Fonts in Photoshop
// Original Script by frontendbeast:
// https://github.com/frontendbeast/list-fonts/

var refPSD = new ActionReference();

function arrayUnique(a){
    var temp = []
        i = a.length;

    // ExtendScript has no indexOf function
    while(i--) {
        var found = false,
        n = temp.length;

        while (n--) {
            if(a[i] === temp[n]) {
                found = true;
            }
        }

        if(!found) {
            temp.push(a[i]);
        }
    }

    return temp;
}

function findFonts() {
    refPSD.putEnumerated( charIDToTypeID('Dcmn'), charIDToTypeID('Ordn'), charIDToTypeID('Trgt') );

    // Get layers from PSD
    var countLayers = executeActionGet(refPSD).getInteger(charIDToTypeID('NmbL'))+1,
        fonts = [];

    // Loop through each layer
    while(countLayers--) {
        var refLayer = new ActionReference(),
            descLayer,
            layerStyles,
            countStyles;

        refLayer.putIndex( charIDToTypeID( 'Lyr ' ), countLayers );

        // Catch error when no backgroundLayer is present
        try {
            descLayer = executeActionGet(refLayer);
        } catch (e) {
            continue;
        }

        // Only proceed if text layer
        if(!descLayer.hasKey(stringIDToTypeID( 'textKey' ))) continue;

        // Get list of styles (in case of multiple fonts in a text layer)
        layerStyles = descLayer.getObjectValue(stringIDToTypeID('textKey')).getList(stringIDToTypeID('textStyleRange'));
        countStyles = layerStyles.count;

        // Loop through each style and get the font name
        while(countStyles--) {
            try {
                var fontName = layerStyles.getObjectValue(countStyles).getObjectValue(stringIDToTypeID('textStyle')).getString(stringIDToTypeID('fontPostScriptName'));
                fonts.push(fontName);
            } catch (e) {
                continue;
            }
        }
    }

    // Return a unique and sorted array of font names
    return arrayUnique(fonts).sort();
}

function replaceFont(target,fontToReplace,replacementFont)
{
    var layers = target.layers;
    for (var i = 0; i < layers.length; i++) {

        if (layers[i].typename == "LayerSet") {

            replaceFont(layers[i]);

        } else if (layers[i].kind == LayerKind.TEXT) {

            if (layers[i].textItem.font == fontToReplace) {
                layers[i].textItem.font = replacementFont;
            }
        };
    };
};

if (documents.length) {
    var fontsFound = findFonts();
    //alert(fontsFound.length +' fonts found \n'+fontsFound.join('\n'));
	var fontToReplace = prompt(fontsFound.length+" Fonts Fond: \[ "+fontsFound.join(' | ')+" \ :","\(One Font Code Above\)","Next");
	var replacementFont = prompt("\[ "+fontsFound.join(' | ')+" \] Replace with:","\(One Font Code Above\)","Do it!");
	//show font names and replace by Kamilet from Kamilet.cn
	var doc = app.activeDocument;
	replaceFont(doc,fontToReplace,replacementFont);
} else {
    alert('No fonts found \nOpen a PSD before running this script',);
}