---
title: Navigace v sadě uzlů pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1a954b41-7173-40bc-8544-d430f209b1e5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 58adf0251fdc7427f493e8bf9947c081bfccd2a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698814"
---
# <a name="node-set-navigation-using-xpathnavigator"></a>Navigace v sadě uzlů pomocí XPathNavigator
Můžete přejít přes uzly v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objektu pomocí uzel nastavení metody navigace <xref:System.Xml.XPath.XPathNavigator> třídy. Můžete přejít přes všechny uzly nebo vybrané sady uzlů, které vrátí jednu z metod výběr <xref:System.Xml.XPath.XPathNavigator> třídy.  
  
## <a name="element-node-set-navigation"></a>Navigace v sadě uzlů – element  
 <xref:System.Xml.XPath.XPathNavigator> Třída poskytuje několik metod pro pohyb mezi uzly element. V následující tabulce jsou uvedeny navigační metody, které jsou k dispozici a jak přecházejí; popis To nezahrnuje metody použít pro účely navigace uzly atributu a oboru názvů.  
  
 Další informace o výběru uzlů v <xref:System.Xml.XPath.XPathNavigator> objektu, najdete v článku [výběr, vyhodnocení a spárování dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md). Další informace o procházení atributu a oboru názvů uzlů najdete v tématu [atribut a Namespace uzlu navigace pomocí XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>|Přesune <xref:System.Xml.XPath.XPathNavigator> na stejné pozici <xref:System.Xml.XPath.XPathNavigator> zadané.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>|Přesune <xref:System.Xml.XPath.XPathNavigator> na podřízený uzel pro aktuální uzel.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>|Přesune <xref:System.Xml.XPath.XPathNavigator> do prvního uzlu na stejné úrovni pro aktuální uzel.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>|Přesune <xref:System.Xml.XPath.XPathNavigator> na první podřízený uzel pro aktuální uzel.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>|Přesune <xref:System.Xml.XPath.XPathNavigator> pro zadaný element v pořadí dokumentů.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>|Přesune <xref:System.Xml.XPath.XPathNavigator> k uzlu, který má atribut typu `ID` s hodnotou, která odpovídá daný <xref:System.String>.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>|Přesune <xref:System.Xml.XPath.XPathNavigator> k dalšímu uzlu na stejné úrovni pro aktuální uzel.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>|Přesune <xref:System.Xml.XPath.XPathNavigator> na nadřazený uzel pro aktuální uzel.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>|Přesune <xref:System.Xml.XPath.XPathNavigator> do předchozího uzlu na stejné úrovni pro aktuální uzel.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>|Přesune <xref:System.Xml.XPath.XPathNavigator> pro kořenový uzel dokumentu XML.|  
  
## <a name="comments-and-processing-instruction-node-navigation"></a>Komentáře a navigační uzel zpracování instrukcí  
 Následující <xref:System.Xml.XPath.XPathNavigator> metody třídy jsou platné pro přesun do komentáře nebo zpracování pokyny z jiných uzlů v dokumentu XML.  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Navigace v uzlu oborů názvů a atributů pomocí XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [Extrahování dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
- [Přístup k datům XML silného typu pomocí XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
