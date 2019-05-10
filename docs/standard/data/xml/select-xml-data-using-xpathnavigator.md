---
title: Výběr dat XML pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: c268c49e-32b9-4171-b782-dcb7b065fa73
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ab2dbe79e1b4b89070d07e0f2c966cb54f6e500
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64589989"
---
# <a name="select-xml-data-using-xpathnavigator"></a>Výběr dat XML pomocí XPathNavigator
<xref:System.Xml.XPath.XPathNavigator> Třída poskytuje sadu metod, které jsou použity k výběru sada uzlů v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> pomocí výrazu XPath. Po výběru neprovedete iteraci vybrané sady uzlů.  
  
## <a name="xpathnavigator-selection-methods"></a>Metody výběru objektem XPathNavigator nastaveným na  
 <xref:System.Xml.XPath.XPathNavigator> Třída poskytuje sadu metod, které jsou použity k výběru sada uzlů v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> pomocí výrazu XPath. <xref:System.Xml.XPath.XPathNavigator> Třída rovněž poskytuje sadu metod optimalizovaný pro rychlejší než při použití výrazu XPath výběru uzlů nadřazeného, podřízené domény a následníka. Vybrané sady uzlů je vrácený v <xref:System.Xml.XPath.XPathNodeIterator> objektu nebo <xref:System.Xml.XPath.XPathNavigator> objektu v případě jednoho vybraného uzlu.  
  
### <a name="selecting-nodes-using-xpath-expressions"></a>Výběr uzlů pomocí výrazů XPath  
 Vybrat sadu uzlů pomocí výraz XPath, použijte jednu z následujících metod výběr.  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 Při volání těchto metod vrátí sadu uzlů, které můžete přejít pomocí volně <xref:System.Xml.XPath.XPathNodeIterator> objektu nebo <xref:System.Xml.XPath.XPathNavigator> objektu v případě jednoho vybraného uzlu.  
  
 Navigace pomocí <xref:System.Xml.XPath.XPathNodeIterator> objekt nemá vliv na umístění <xref:System.Xml.XPath.XPathNavigator> objekt použitý k jeho vytvoření. <xref:System.Xml.XPath.XPathNavigator> Objekt vrácený z <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> metody je umístěn na jeden uzel vrácený a také nemá vliv na umístění <xref:System.Xml.XPath.XPathNavigator> objekt použitý k jeho vytvoření.  
  
 Následující příklad ukazuje vytvoření objektu <xref:System.Xml.XPath.XPathNavigator> objektu z <xref:System.Xml.XPath.XPathDocument> objektu, použití <xref:System.Xml.XPath.XPathNavigator.Select%2A> pro výběr uzlů v <xref:System.Xml.XPath.XPathDocument> objektu a použití <xref:System.Xml.XPath.XPathNodeIterator> objektu k iteraci přes vybrané uzly.  
  
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
  
 V příkladu přebírá `books.xml` souboru jako vstup.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="optimized-selection-methods"></a>Optimalizované výběr metody  
 <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, A <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> metody <xref:System.Xml.XPath.XPathNavigator> třídy představují výrazů XPath používaných k načtení uzly podřízené, následník a předchůdce. Tyto metody jsou optimalizované pro výkon a jsou rychlejší než jejich odpovídající výrazy XPath. <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, A <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> metody vybere nadřazený, podřízený a podřízených uzlů na základě <xref:System.Xml.XPath.XPathNodeType> hodnotu nebo místní název a obor názvů URI uzlů vybrat. Vybraný nadřazený, podřízený a podřízených uzlů, které jsou vráceny v <xref:System.Xml.XPath.XPathNodeIterator> objektu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Vyhodnocení výrazů XPath pomocí XPathNavigator](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [Párování uzlů pomocí XPathNavigator](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [Rozpoznané typy uzlů s dotazy XPath](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [Dotazy XPath a obory názvů](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [Zkompilované výrazy XPath](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
