---
title: Přístup ke XML v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
ms.openlocfilehash: b000b3f6846f800b2a96ce10cdd408a355f78a81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649591"
---
# <a name="accessing-xml-in-visual-basic"></a>Přístup ke XML v jazyce Visual Basic
Visual Basic poskytuje vlastnosti osy XML pro přístup k informacím a navigace [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] struktury. Tyto vlastnosti pomocí speciální syntaxe vám umožní přístup zadáním názvů XML elementů a atributů.  
  
 Následující tabulka uvádí funkce jazyka, které vám umožní přístup k XML elementů a atributů v jazyce Visual Basic.  
  
### <a name="xml-axis-properties"></a>Vlastnosti osy XML  
  
|Popis vlastnosti|Příklad|Popis|  
|--------------------------|-------------|-----------------|  
|*podřízené osy*|`contact.<phone>`|Získá všechny `phone` prvky, které jsou podřízených elementů `contact` elementu.|  
|*atribut osy*|`phone.@type`|Získá všechny `type` atributy `phone` elementu.|  
|*Následnické osy*|`contacts...<name>`|Získá všechny `name` prvky `contacts` elementu, bez ohledu na to, jak hluboko v hierarchii k nim dojde.|  
|*Indexovací modul rozšíření*|`contacts...<name>(0)`|Získá první `name` element z pořadí.|  
|*value*|`contacts...<name>.Value`|Získá řetězcovou reprezentaci objektu první v pořadí, nebo `Nothing` Pokud sekvenci je prázdný.|  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Přístup k následnickým elementům XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 Ukazuje, jak používat vlastnost osy nástupce pro přístup k všech elementů XML, které jsou obsažené v rámci zadaného elementu XML, které mají zadaný název.  
  
 [Postupy: Přístup k podřízeným elementům XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 Ukazuje způsob použití podřízená osa – vlastnost přístup všech podřízených elementů XML, které mají zadaný název v elementu XML.  
  
 [Postupy: Přístup k atributům XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 Ukazuje, jak používat vlastnost osy atributu pro přístup k všechny atributy XML, které mají zadaný název v elementu XML.  
  
 [Postupy: Deklarace a používání předpon názvového prostoru XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 Ukazuje, jak deklarovat předponu oboru názvů XML a použít ho k vytváření a přístup k elementům XML.  
  
## <a name="related-sections"></a>Související oddíly  
 [Vlastnosti osy XML](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 Obsahuje odkazy na oddíly, které popisují různé vlastnosti přístup XML.  
  
 [Přehled technologie LINQ to XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 Obsahuje úvod do používání [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] v jazyce Visual Basic.  
  
 [Vytvoření XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 Poskytuje úvod do používání literálů XML v jazyce Visual Basic.  
  
 [Zacházení s XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 Obsahuje odkazy na části o načítání a úprava XML v jazyce Visual Basic.  
  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 Obsahuje odkazy na části popisující, jak používat [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] v jazyce Visual Basic.
