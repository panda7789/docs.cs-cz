---
title: Direktivy list stylu vložených v dokumentu
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2fa671304c611db571b160cd1d960b83bf451c9a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="style-sheet-directives-embedded-in-a-document"></a>Direktivy list stylu vložených v dokumentu
V některých případech existující soubor XML obsahuje direktiva list stylu z `<?xml:stylesheet?>`. Aplikace Microsoft Internet Explorer to přijímá jako alternativu k `<?xml-stylesheet?>` syntaxe. Když se XML data obsahuje `<?xml:stylesheet?>` direktivy, jak je uvedené v následující data pokusu o načtení tato data do XML modelu DOM (Document Object) vyvolá výjimku.  
  
```xml  
<?xml version="1.0" ?>  
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>  
<root>  
    <test>Node 1</test>  
    <test>Node 2</test>  
</root>  
```  
  
 K tomu dochází, protože `<?xml:stylesheet?>` se považuje za neplatný **ProcessingInstruction** do modelu DOM. Všechny **ProcessingInstruction**, podle obory názvů ve specifikaci XML, může být pouze názvy ne dvojtečka (NCNames), a kvalifikované názvy (QNames).  
  
 Z části 6 oborů názvů ve specifikaci XML, účinek toho, že **zatížení** a **příkaz LoadXml** metody v souladu s specifikace je, že v dokumentu:  
  
-   Všechny typy elementů a atributů názvy obsahovat jednou nebo středníkem.  
  
-   Žádné entity názvů, ProcessingInstruction cíle nebo zápis obsahovat dvojtečku.  
  
 Pomocí `<?xml:stylesheet?>` obsahující dvojtečkou, můžete nyní porušují pravidlo v druhém bodě.  
  
 Podle World Wide Web Consortium (W3C) přidružení šablony stylů s dokumenty XML verze 1.0 doporučení, nacházející se v www.w3.org/TR/xml-stylesheet, pokyny pro zpracování stylů XSLT přidružit dokument XML je `<?xml-stylesheet?>`, s pomlčkou nahrazení dvojtečkou.  
  
## <a name="see-also"></a>Viz také  
 [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
