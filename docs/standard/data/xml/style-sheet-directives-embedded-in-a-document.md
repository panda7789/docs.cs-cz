---
title: Direktivy šablon stylů vložené v dokumentu
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
ms.openlocfilehash: 19e25ab7262bb006144eea71e74bd7454066b3f6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710151"
---
# <a name="style-sheet-directives-embedded-in-a-document"></a>Direktivy šablon stylů vložené v dokumentu

Existující kód XML může občas obsahovat direktivu šablon stylů `<?xml:stylesheet?>`. Aplikace Microsoft Internet Explorer přijímá jako alternativu k `<?xml-stylesheet?>` syntaxi. Pokud data XML obsahují `<?xml:stylesheet?>` direktivu, jak je znázorněno na následujících datech, pokus o načtení těchto dat do XML model DOM (Document Object Model) (DOM) vyvolá výjimku.

```xml
<?xml version="1.0" ?>
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>
<root>
    <test>Node 1</test>
    <test>Node 2</test>
</root>
```

K tomu dochází, `<?xml:stylesheet?>` protože se v modelu DOM považuje neplatný **ProcessingInstruction** . Jakékoli **ProcessingInstruction**, v závislosti na oborech názvů ve specifikaci XML, mohou být pouze názvy bez dvojtečky (NCNames), nikoli kvalifikované názvy (QName).

Z oddílu 6 specifikací oboru názvů ve specifikaci XML je účinek, aby metody **Load** a **LoadXml** splňovaly specifikace je v dokumentu:

- Všechny typy prvků a názvy atributů obsahují buď žádnou, nebo jednu dvojtečku.

- Názvy entit, cíle ProcessingInstruction ani názvy Notation neobsahují žádné dvojtečky.

V případě `<?xml:stylesheet?>` , že obsahuje dvojtečku, jste teď poznamenali pravidlo ve druhé odrážce.

V závislosti na konsorcium World Wide Web (W3C), které spojují [šablony stylů s dokumenty XML verze 1,0](https://www.w3.org/TR/xml-stylesheet/), je `<?xml-stylesheet?>`pokyn ke zpracování k přidružení šablony stylů XSLT k dokumentu XML s pomlčkou, která nahrazuje dvojtečku.

## <a name="see-also"></a>Viz také

- [model DOM (Document Object Model) dokumentu XML](xml-document-object-model-dom.md)
