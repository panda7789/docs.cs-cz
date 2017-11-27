---
title: "Vyberte pomocí objektem XPathNavigator nastaveným na Data XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c268c49e-32b9-4171-b782-dcb7b065fa73
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9f63f23b1a07fbe77e77598cd05dcd25ee8ec158
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="select-xml-data-using-xpathnavigator"></a>Vyberte pomocí objektem XPathNavigator nastaveným na Data XML
<xref:System.Xml.XPath.XPathNavigator> Třída poskytuje sadu metod, které jsou použity k výběru sada uzlů v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> pomocí výrazu XPath. Po výběru, můžete postup opakovat přes vybrané sada uzlů.  
  
## <a name="xpathnavigator-selection-methods"></a>Objektem XPathNavigator nastaveným na výběr metody  
 <xref:System.Xml.XPath.XPathNavigator> Třída poskytuje sadu metod, které jsou použity k výběru sada uzlů v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> pomocí výrazu XPath. <xref:System.Xml.XPath.XPathNavigator> Třída rovněž poskytuje sadu metod optimalizované pro výběr nadřazené a podřízené následník uzly rychleji než pomocí výrazu XPath. Vybraná sada uzlů je vrácený v <xref:System.Xml.XPath.XPathNodeIterator> objekt nebo <xref:System.Xml.XPath.XPathNavigator> objektu v případě jedné vybraný uzel.  
  
### <a name="selecting-nodes-using-xpath-expressions"></a>Výběr uzlů pomocí výrazech XPath  
 Pokud chcete vybrat sadu uzlů pomocí výrazu jazyka XPath, použijte jednu z následujících metod výběr.  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 Při volání, tyto metody vrací sadu uzlů, které můžete přejít pomocí volně <xref:System.Xml.XPath.XPathNodeIterator> objekt nebo <xref:System.Xml.XPath.XPathNavigator> objektu v případě jedné vybraný uzel.  
  
 Navigace s <xref:System.Xml.XPath.XPathNodeIterator> objekt nemá vliv na pozici <xref:System.Xml.XPath.XPathNavigator> objekt použitý k jeho vytvoření. <xref:System.Xml.XPath.XPathNavigator> Objekt vrácený <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> metody je umístěn na jeden uzel vrácený a také nemá vliv na pozici <xref:System.Xml.XPath.XPathNavigator> objekt použitý k jeho vytvoření.  
  
 Následující příklad ukazuje vytvoření <xref:System.Xml.XPath.XPathNavigator> objektu z <xref:System.Xml.XPath.XPathDocument> objekt, použití <xref:System.Xml.XPath.XPathNavigator.Select%2A> metoda a vyberte uzly ve <xref:System.Xml.XPath.XPathDocument> objekt a použití <xref:System.Xml.XPath.XPathNodeIterator> objekt Iterujte přes vybrané uzly.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
Dim nodes As XPathNodeIterator = navigator.Select("/bookstore/book")  
  
While nodes.MoveNext()  
    Console.WriteLine(nodes.Current.Name)  
End While  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
XPathNodeIterator nodes = navigator.Select("/bookstore/book");  
  
while(nodes.MoveNext())  
{  
    Console.WriteLine(nodes.Current.Name);  
}  
```  
  
 V příkladu trvá `books.xml` souboru jako vstup.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="optimized-selection-methods"></a>Optimalizované výběr metody  
 <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, A <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> metody <xref:System.Xml.XPath.XPathNavigator> třída reprezentuje výrazech XPath běžně používá k načtení podřízené následník a nadřazenými uzly. Tyto metody jsou optimalizované pro výkon a rychlejší než jejich odpovídající výrazech XPath. <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, A <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> metody vybere předchůdce, podřízené a následné uzly na základě <xref:System.Xml.XPath.XPathNodeType> hodnotu nebo místní název a identifikátor URI uzlů vybrat oboru názvů. Vybrané nadřazené, podřízené a následné uzly jsou vráceny v <xref:System.Xml.XPath.XPathNodeIterator> objektu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Zpracování kódu XML dat pomocí jazyka XPath datový Model](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Vyhodnocení výrazů jazyka XPath pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [Odpovídající pomocí objektem XPathNavigator nastaveným na uzly](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [Typy uzlů rozpoznána s dotazy XPath](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [Dotazy XPath a obory názvů](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [Výrazy kompilované XPath](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
