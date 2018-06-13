---
title: Uzel navigační sady pomocí objektem XPathNavigator nastaveným na
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1a954b41-7173-40bc-8544-d430f209b1e5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b6dfba9bb6cd253f4bc866f445a324a046c8cad2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570630"
---
# <a name="node-set-navigation-using-xpathnavigator"></a>Uzel navigační sady pomocí objektem XPathNavigator nastaveným na
Můžete přejít přes uzly v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objektu pomocí uzlu nastavit metody navigace <xref:System.Xml.XPath.XPathNavigator> třídy. Můžete přejít přes všechny uzly nebo přes vybraná sada uzlů, které vrátí jednu z metod výběr <xref:System.Xml.XPath.XPathNavigator> třídy.  
  
## <a name="element-node-set-navigation"></a>Element uzlu sady navigace  
 <xref:System.Xml.XPath.XPathNavigator> Třída poskytuje několik metod používaných k přejděte uzly elementu. Následující tabulka uvádí metody navigace, která je k dispozici a jak se přesouvají; popis nezahrnuje metody použité k přejděte uzly atribut a obor názvů.  
  
 Další informace o výběru uzlů v <xref:System.Xml.XPath.XPathNavigator> objektu, najdete v části [zvolíte, Evaluating a porovnávání dat XML pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md). Další informace o navigace uzly atribut a obor názvů najdete v tématu [atribut a Namespace uzlu navigace pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>|Přesune <xref:System.Xml.XPath.XPathNavigator> na stejné pozici <xref:System.Xml.XPath.XPathNavigator> zadaný.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>|Přesune <xref:System.Xml.XPath.XPathNavigator> na aktuálním uzlu podřízený uzel.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>|Přesune <xref:System.Xml.XPath.XPathNavigator> na první uzel na stejné úrovni aktuální uzel.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>|Přesune <xref:System.Xml.XPath.XPathNavigator> na první podřízený uzel aktuální uzel.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>|Přesune <xref:System.Xml.XPath.XPathNavigator> na zadaný prvek v pořadí dokumentů.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>|Přesune <xref:System.Xml.XPath.XPathNavigator> na uzlu, který má atribut typu `ID` s hodnotou, která odpovídá danou <xref:System.String>.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>|Přesune <xref:System.Xml.XPath.XPathNavigator> na další uzel na stejné úrovni jako aktuální uzel.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>|Přesune <xref:System.Xml.XPath.XPathNavigator> na nadřazený uzel aktuální uzel.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>|Přesune <xref:System.Xml.XPath.XPathNavigator> předchozí uzel na stejné úrovni jako aktuální uzel.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>|Přesune <xref:System.Xml.XPath.XPathNavigator> do kořenového uzlu dokumentu XML.|  
  
## <a name="comments-and-processing-instruction-node-navigation"></a>Komentáře a zpracování instrukcí uzlu navigace  
 Následující <xref:System.Xml.XPath.XPathNavigator> metody třídy jsou platné pro přechod komentáře nebo zpracování pokyny z jiných uzlů v dokumentu XML.  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Navigace v uzlu oborů názvů a atributů pomocí XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
 [Extrahování dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)  
 [Přístup k datům XML silného typu pomocí XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
