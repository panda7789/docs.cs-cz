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
ms.openlocfilehash: 282b7d91ec7cfe2f587c67bc9a982f0da22ad925
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410306"
---
# <a name="accessing-xml-in-visual-basic"></a>Přístup ke XML v jazyce Visual Basic
Visual Basic poskytuje vlastnosti osy XML pro přístup k strukturám a jejich navigaci [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] . Tyto vlastnosti používají speciální syntaxi k umožnění přístupu k prvkům a atributům zadáním názvů XML.  
  
 V následující tabulce jsou uvedeny funkce jazyka, které vám umožní přístup k elementům a atributům XML v Visual Basic.  
  
### <a name="xml-axis-properties"></a>Vlastnosti osy XML  
  
|Popis vlastnosti|Příklad|Description|  
|--------------------------|-------------|-----------------|  
|*podřízená osa*|`contact.<phone>`|Načte všechny `phone` prvky, které jsou podřízenými prvky `contact` elementu.|  
|*osa atributu*|`phone.@type`|Získá všechny `type` atributy `phone` elementu.|  
|*osa následníka*|`contacts...<name>`|Načte všechny `name` prvky `contacts` elementu bez ohledu na to, jak hluboko v hierarchii nastanou.|  
|*Indexer rozšíření*|`contacts...<name>(0)`|Získá první `name` prvek z sekvence.|  
|*osa*|`contacts...<name>.Value`|Získá řetězcovou reprezentaci prvního objektu v sekvenci nebo je- `Nothing` li sekvence prázdná.|  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Přístup k následnickým elementům XML](how-to-access-xml-descendant-elements.md)  
 Ukazuje, jak použít vlastnost následníka pro přístup ke všem elementům XML, které mají zadaný název a které jsou obsaženy v zadaném elementu XML.  
  
 [Postupy: Přístup k podřízeným elementům XML](how-to-access-xml-child-elements.md)  
 Ukazuje, jak použít vlastnost podřízené osy pro přístup ke všem podřízeným elementům XML, které mají zadaný název v elementu XML.  
  
 [Postupy: Přístup k atributům XML](how-to-access-xml-attributes.md)  
 Ukazuje, jak použít vlastnost osy atributu pro přístup ke všem atributům XML, které mají zadaný název v elementu XML.  
  
 [Postupy: Deklarace a používání předpon oboru názvů XML](how-to-declare-and-use-xml-namespace-prefixes.md)  
 Ukazuje, jak deklarovat předponu oboru názvů XML a použít ji k vytvoření a přístup k elementům XML.  
  
## <a name="related-sections"></a>Související oddíly  
 [Vlastnosti osy XML](../../../language-reference/xml-axis/index.md)  
 Obsahuje odkazy na oddíly popisující různé vlastnosti přístupu XML.  
  
 [Přehled technologie LINQ to XML v jazyce Visual Basic](overview-of-linq-to-xml.md)  
 Poskytuje Úvod k použití [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] v Visual Basic.  
  
 [Vytvoření XML v jazyce Visual Basic](creating-xml.md)  
 Poskytuje Úvod k použití literálů XML v Visual Basic.  
  
 [Zacházení s XML v jazyce Visual Basic](manipulating-xml.md)  
 Obsahuje odkazy na oddíly o načítání a úpravách XML v Visual Basic.  
  
 [XML](index.md)  
 Obsahuje odkazy na oddíly, které popisují použití [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] v Visual Basic.
