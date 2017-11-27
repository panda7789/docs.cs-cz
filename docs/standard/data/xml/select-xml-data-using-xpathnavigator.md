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
# <a name="select-xml-data-using-xpathnavigator"></a><span data-ttu-id="ce805-102">Vyberte pomocí objektem XPathNavigator nastaveným na Data XML</span><span class="sxs-lookup"><span data-stu-id="ce805-102">Select XML Data Using XPathNavigator</span></span>
<span data-ttu-id="ce805-103"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje sadu metod, které jsou použity k výběru sada uzlů v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> pomocí výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="ce805-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="ce805-104">Po výběru, můžete postup opakovat přes vybrané sada uzlů.</span><span class="sxs-lookup"><span data-stu-id="ce805-104">Once selected, you can iterate over the selected set of nodes.</span></span>  
  
## <a name="xpathnavigator-selection-methods"></a><span data-ttu-id="ce805-105">Objektem XPathNavigator nastaveným na výběr metody</span><span class="sxs-lookup"><span data-stu-id="ce805-105">XPathNavigator Selection Methods</span></span>  
 <span data-ttu-id="ce805-106"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje sadu metod, které jsou použity k výběru sada uzlů v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> pomocí výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="ce805-106">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="ce805-107"><xref:System.Xml.XPath.XPathNavigator> Třída rovněž poskytuje sadu metod optimalizované pro výběr nadřazené a podřízené následník uzly rychleji než pomocí výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="ce805-107">The <xref:System.Xml.XPath.XPathNavigator> class also provides a set of optimized methods for selecting ancestor, child and descendant nodes faster than using an XPath expression.</span></span> <span data-ttu-id="ce805-108">Vybraná sada uzlů je vrácený v <xref:System.Xml.XPath.XPathNodeIterator> objekt nebo <xref:System.Xml.XPath.XPathNavigator> objektu v případě jedné vybraný uzel.</span><span class="sxs-lookup"><span data-stu-id="ce805-108">The selected set of nodes is returned in an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
### <a name="selecting-nodes-using-xpath-expressions"></a><span data-ttu-id="ce805-109">Výběr uzlů pomocí výrazech XPath</span><span class="sxs-lookup"><span data-stu-id="ce805-109">Selecting Nodes Using XPath Expressions</span></span>  
 <span data-ttu-id="ce805-110">Pokud chcete vybrat sadu uzlů pomocí výrazu jazyka XPath, použijte jednu z následujících metod výběr.</span><span class="sxs-lookup"><span data-stu-id="ce805-110">To select a set of nodes using an XPath expression, use one of the following selection methods.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 <span data-ttu-id="ce805-111">Při volání, tyto metody vrací sadu uzlů, které můžete přejít pomocí volně <xref:System.Xml.XPath.XPathNodeIterator> objekt nebo <xref:System.Xml.XPath.XPathNavigator> objektu v případě jedné vybraný uzel.</span><span class="sxs-lookup"><span data-stu-id="ce805-111">When called, these methods return a set of nodes that you can navigate freely using an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
 <span data-ttu-id="ce805-112">Navigace s <xref:System.Xml.XPath.XPathNodeIterator> objekt nemá vliv na pozici <xref:System.Xml.XPath.XPathNavigator> objekt použitý k jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="ce805-112">Navigating with an <xref:System.Xml.XPath.XPathNodeIterator> object does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span> <span data-ttu-id="ce805-113"><xref:System.Xml.XPath.XPathNavigator> Objekt vrácený <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> metody je umístěn na jeden uzel vrácený a také nemá vliv na pozici <xref:System.Xml.XPath.XPathNavigator> objekt použitý k jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="ce805-113">The <xref:System.Xml.XPath.XPathNavigator> object returned from the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> methods is positioned on the single returned node and also does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span>  
  
 <span data-ttu-id="ce805-114">Následující příklad ukazuje vytvoření <xref:System.Xml.XPath.XPathNavigator> objektu z <xref:System.Xml.XPath.XPathDocument> objekt, použití <xref:System.Xml.XPath.XPathNavigator.Select%2A> metoda a vyberte uzly ve <xref:System.Xml.XPath.XPathDocument> objekt a použití <xref:System.Xml.XPath.XPathNodeIterator> objekt Iterujte přes vybrané uzly.</span><span class="sxs-lookup"><span data-stu-id="ce805-114">The following example shows the creation of an <xref:System.Xml.XPath.XPathNavigator> object from an <xref:System.Xml.XPath.XPathDocument> object, the use of the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method to select nodes in the <xref:System.Xml.XPath.XPathDocument> object, and the use of the <xref:System.Xml.XPath.XPathNodeIterator> object to iterate over the selected nodes.</span></span>  
  
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
  
 <span data-ttu-id="ce805-115">V příkladu trvá `books.xml` souboru jako vstup.</span><span class="sxs-lookup"><span data-stu-id="ce805-115">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="optimized-selection-methods"></a><span data-ttu-id="ce805-116">Optimalizované výběr metody</span><span class="sxs-lookup"><span data-stu-id="ce805-116">Optimized Selection Methods</span></span>  
 <span data-ttu-id="ce805-117"><xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, A <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> metody <xref:System.Xml.XPath.XPathNavigator> třída reprezentuje výrazech XPath běžně používá k načtení podřízené následník a nadřazenými uzly.</span><span class="sxs-lookup"><span data-stu-id="ce805-117">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class represent XPath expressions commonly used to retrieve child, descendant, and ancestor nodes.</span></span> <span data-ttu-id="ce805-118">Tyto metody jsou optimalizované pro výkon a rychlejší než jejich odpovídající výrazech XPath.</span><span class="sxs-lookup"><span data-stu-id="ce805-118">These methods are optimized for performance and are faster than their corresponding XPath expressions.</span></span> <span data-ttu-id="ce805-119"><xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, A <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> metody vybere předchůdce, podřízené a následné uzly na základě <xref:System.Xml.XPath.XPathNodeType> hodnotu nebo místní název a identifikátor URI uzlů vybrat oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ce805-119">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods selects ancestor, child, and descendant nodes based on an <xref:System.Xml.XPath.XPathNodeType> value or the local name and namespace URI of the nodes to select.</span></span> <span data-ttu-id="ce805-120">Vybrané nadřazené, podřízené a následné uzly jsou vráceny v <xref:System.Xml.XPath.XPathNodeIterator> objektu.</span><span class="sxs-lookup"><span data-stu-id="ce805-120">The selected ancestor, child, and descendant nodes are returned in an <xref:System.Xml.XPath.XPathNodeIterator> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce805-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce805-121">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="ce805-122">Zpracování kódu XML dat pomocí jazyka XPath datový Model</span><span class="sxs-lookup"><span data-stu-id="ce805-122">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="ce805-123">Vyhodnocení výrazů jazyka XPath pomocí objektem XPathNavigator nastaveným na</span><span class="sxs-lookup"><span data-stu-id="ce805-123">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [<span data-ttu-id="ce805-124">Odpovídající pomocí objektem XPathNavigator nastaveným na uzly</span><span class="sxs-lookup"><span data-stu-id="ce805-124">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [<span data-ttu-id="ce805-125">Typy uzlů rozpoznána s dotazy XPath</span><span class="sxs-lookup"><span data-stu-id="ce805-125">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [<span data-ttu-id="ce805-126">Dotazy XPath a obory názvů</span><span class="sxs-lookup"><span data-stu-id="ce805-126">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [<span data-ttu-id="ce805-127">Výrazy kompilované XPath</span><span class="sxs-lookup"><span data-stu-id="ce805-127">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
