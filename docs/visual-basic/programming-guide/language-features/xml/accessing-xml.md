---
title: Přístup k XML
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
ms.openlocfilehash: 1fa1d94fc710272ac0ba9ea7167989da42a51fcd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351750"
---
# <a name="accessing-xml-in-visual-basic"></a>Přístup ke XML v jazyce Visual Basic
Visual Basic poskytuje vlastnosti osy XML pro přístup k [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] strukturám a jejich procházení. Tyto vlastnosti používají speciální syntaxi k umožnění přístupu k prvkům a atributům zadáním názvů XML.  
  
 V následující tabulce jsou uvedeny funkce jazyka, které vám umožní přístup k elementům a atributům XML v Visual Basic.  
  
### <a name="xml-axis-properties"></a>Vlastnosti osy XML  
  
|Popis vlastnosti|Příklad|Popis|  
|--------------------------|-------------|-----------------|  
|*podřízená osa*|`contact.<phone>`|Získá všechny prvky `phone`, které jsou podřízenými prvky elementu `contact`.|  
|*osa atributu*|`phone.@type`|Získá všechny atributy `type` `phone` elementu.|  
|*osa následníka*|`contacts...<name>`|Získá všechny `name` prvky `contacts` elementu bez ohledu na to, jak hluboko v hierarchii nastanou.|  
|*Indexer rozšíření*|`contacts...<name>(0)`|Získá první prvek `name` z sekvence.|  
|*value*|`contacts...<name>.Value`|Získá řetězcovou reprezentaci prvního objektu v sekvenci nebo `Nothing`, pokud je sekvence prázdná.|  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Přístup k následnickým elementům XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 Ukazuje, jak použít vlastnost následníka pro přístup ke všem elementům XML, které mají zadaný název a které jsou obsaženy v zadaném elementu XML.  
  
 [Postupy: Přístup k podřízeným elementům XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 Ukazuje, jak použít vlastnost podřízené osy pro přístup ke všem podřízeným elementům XML, které mají zadaný název v elementu XML.  
  
 [Postupy: Přístup k atributům XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 Ukazuje, jak použít vlastnost osy atributu pro přístup ke všem atributům XML, které mají zadaný název v elementu XML.  
  
 [Postupy: Deklarace a používání předpon názvového prostoru XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 Ukazuje, jak deklarovat předponu oboru názvů XML a použít ji k vytvoření a přístup k elementům XML.  
  
## <a name="related-sections"></a>Související oddíly  
 [Vlastnosti osy XML](../../../../visual-basic/language-reference/xml-axis/index.md)  
 Obsahuje odkazy na oddíly popisující různé vlastnosti přístupu XML.  
  
 [Přehled LINQ to XML v Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 Představuje úvod k použití [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] v Visual Basic.  
  
 [Vytváření XML v Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 Poskytuje Úvod k použití literálů XML v Visual Basic.  
  
 [Manipulace s XML v Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 Obsahuje odkazy na oddíly o načítání a úpravách XML v Visual Basic.  
  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 Obsahuje odkazy na části, které popisují, jak používat [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] v Visual Basic.
