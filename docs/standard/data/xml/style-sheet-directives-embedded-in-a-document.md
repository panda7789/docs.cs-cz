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

V některých případech existující XML obsahuje direktivu šablon stylů `<?xml:stylesheet?>`. Aplikace Microsoft Internet Explorer přijímá jako alternativu k syntaxi `<?xml-stylesheet?>`. Pokud data XML obsahují direktivu `<?xml:stylesheet?>`, jak je znázorněno na následujících datech, pokus o načtení těchto dat do XML model DOM (Document Object Model) (DOM) vyvolá výjimku.

```xml
<?xml version="1.0" ?>
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>
<root>
    <test>Node 1</test>
    <test>Node 2</test>
</root>
```

K tomu dochází, protože `<?xml:stylesheet?>` se považuje za neplatný **ProcessingInstruction** do modelu DOM. Jakékoli **ProcessingInstruction**, v závislosti na oborech názvů ve specifikaci XML, mohou být pouze názvy bez dvojtečky (NCNames), nikoli kvalifikované názvy (QName).

Z oddílu 6 specifikací oboru názvů ve specifikaci XML je účinek, aby metody **Load** a **LoadXml** splňovaly specifikace je v dokumentu:

- Všechny typy prvků a názvy atributů obsahují buď žádnou, nebo jednu dvojtečku.

- Názvy entit, cíle ProcessingInstruction ani názvy Notation neobsahují žádné dvojtečky.

U `<?xml:stylesheet?>`, který obsahuje dvojtečku, jste teď poznamenali pravidlo ve druhé odrážce.

V souladu s konsorcium World Wide Web (W3C), který [přiřazuje šablony stylů s dokumenty XML verze 1,0](https://www.w3.org/TR/xml-stylesheet/), je pokyn ke zpracování k přidružení šablony stylů XSLT k dokumentu XML `<?xml-stylesheet?>`a pomlčkou nahrazuje dvojtečku.

## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](xml-document-object-model-dom.md)
