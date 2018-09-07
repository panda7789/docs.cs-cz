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
ms.openlocfilehash: 0540c52cf3e4cd7594f051c10832ea99cf58a34e
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44078892"
---
# <a name="accessing-xml-in-visual-basic"></a>Přístup ke XML v jazyce Visual Basic
Visual Basic poskytuje vlastnosti osy XML pro přístup k a navigace [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] struktury. Tyto vlastnosti pomocí speciální syntaxe umožňuje přístup k prvkům a atributům tak, že zadáte názvy XML.  
  
 V následující tabulce jsou uvedeny vlastnosti jazyka, které vám umožní přístup k XML elementů a atributů v jazyce Visual Basic.  
  
### <a name="xml-axis-properties"></a>Vlastnosti osy XML  
  
|Popis vlastnosti|Příklad|Popis|  
|--------------------------|-------------|-----------------|  
|*podřízená osa*|`contact.<phone>`|Získá všechny `phone` prvky, které jsou podřízené prvky `contact` elementu.|  
|*atribut osy*|`phone.@type`|Získá všechny `type` atributy `phone` elementu.|  
|*Následnické osy*|`contacts...<name>`|Získá všechny `name` prvky `contacts` elementu, bez ohledu na to, jak hluboko v hierarchii k nim dojde.|  
|*Indexovací modul rozšíření*|`contacts...<name>(0)`|Získá první `name` element z pořadí.|  
|*value*|`contacts...<name>.Value`|Získá řetězcovou reprezentaci objektu první v pořadí, nebo `Nothing` Pokud sekvence je prázdný.|  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Přístup k následnickým elementům XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 Ukazuje, jak používat vlastnost Následnické osy pro přístup k všech elementů XML, které jsou obsaženy v rámci zadaného elementu XML, které mají zadaný název.  
  
 [Postupy: Přístup k podřízeným elementům XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 Ukazuje, jak používat podřízený – vlastnost osy pro přístup k všechny podřízené prvky XML, které mají zadaný název v elementu jazyka XML.  
  
 [Postupy: Přístup k atributům XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 Ukazuje, jak pomocí vlastnost osy atributu přístup ke všem atributům XML, které mají zadaný název v elementu jazyka XML.  
  
 [Postupy: Deklarace a používání předpon názvového prostoru XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 Ukazuje, jak deklarovat předponu oboru názvů XML a použít ho k vytváření a přístup k elementům XML.  
  
## <a name="related-sections"></a>Související oddíly  
 [Vlastnosti osy XML](../../../../visual-basic/language-reference/xml-axis/index.md)  
 Obsahuje odkazy na oddíly popisují různé vlastnosti přístupu XML.  
  
 [Přehled technologie LINQ to XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 Poskytuje úvod do používání [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] v jazyce Visual Basic.  
  
 [Vytvoření XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 Poskytuje úvod do používání literály XML v jazyce Visual Basic.  
  
 [Manipulace s kódem XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 Poskytuje odkazy na části o načítání a úpravy XML v jazyce Visual Basic.  
  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 Poskytuje odkazy na části popisující, jak používat [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] v jazyce Visual Basic.
