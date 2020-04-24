---
title: Navigace v sadě uzlů pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1a954b41-7173-40bc-8544-d430f209b1e5
ms.openlocfilehash: 91115af03b635d7660721fac5ce8bd749953e4ff
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710567"
---
# <a name="node-set-navigation-using-xpathnavigator"></a>Navigace v sadě uzlů pomocí XPathNavigator
Můžete procházet uzly v objektu <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> pomocí uzlu nastavit navigační metody <xref:System.Xml.XPath.XPathNavigator> třídy. Můžete procházet všechny uzly nebo přes vybranou sadu uzlů, kterou vrátí jedna z metod výběru <xref:System.Xml.XPath.XPathNavigator> třídy.  
  
## <a name="element-node-set-navigation"></a>Uzel elementu – nastavení navigace  
 <xref:System.Xml.XPath.XPathNavigator> Třída poskytuje několik metod, které slouží k procházení uzlů prvků. V následující tabulce jsou uvedeny dostupné metody navigace a popis jejich přesunu; nezahrnuje metody používané pro navigaci v uzlech atributu a oboru názvů.  
  
 Další informace o výběru uzlů v <xref:System.Xml.XPath.XPathNavigator> objektu naleznete v tématu [výběr, vyhodnocení a porovnání dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md). Další informace o navigaci v uzlech atributů a oboru názvů naleznete v tématu [navigace pomocí atributů a uzlu oboru názvů pomocí XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>|Přesune rozhraní <xref:System.Xml.XPath.XPathNavigator> do stejné pozice <xref:System.Xml.XPath.XPathNavigator> zadaného.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>|Přesune objekt <xref:System.Xml.XPath.XPathNavigator> do podřízeného uzlu aktuálního uzlu.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>|<xref:System.Xml.XPath.XPathNavigator> Přesune na první uzel na stejné úrovni aktuálního uzlu.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>|Přesune <xref:System.Xml.XPath.XPathNavigator> do prvního podřízeného uzlu aktuálního uzlu.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>|<xref:System.Xml.XPath.XPathNavigator> Přesune na zadaný element v pořadí dokumentů.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>|<xref:System.Xml.XPath.XPathNavigator> Přesune na uzel, který má atribut typu `ID` s hodnotou, která odpovídá danému <xref:System.String>.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>|<xref:System.Xml.XPath.XPathNavigator> Přesune na další uzel na stejné úrovni aktuálního uzlu.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>|Přesune objekt <xref:System.Xml.XPath.XPathNavigator> do nadřazeného uzlu aktuálního uzlu.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>|<xref:System.Xml.XPath.XPathNavigator> Přesune na předchozí uzel na stejné úrovni jako aktuální uzel.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>|Přesune uzel <xref:System.Xml.XPath.XPathNavigator> do kořenového uzlu dokumentu XML.|  
  
## <a name="comments-and-processing-instruction-node-navigation"></a>Komentáře a zpracování – navigace uzlu instrukcí  
 Následující <xref:System.Xml.XPath.XPathNavigator> metody třídy jsou platné pro přesun na komentáře nebo pokyny pro zpracování z jiných uzlů v dokumentu XML.  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Navigace v uzlu oborů názvů a atributů pomocí XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [Extrahování dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
- [Přístup k datům XML silného typu pomocí XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
