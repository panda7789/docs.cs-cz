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
ms.openlocfilehash: fea54d36759b12b01fa7a68748d069c7890d84e4
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45507925"
---
# <a name="select-xml-data-using-xpathnavigator"></a><span data-ttu-id="11ddf-102">Výběr dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="11ddf-102">Select XML Data Using XPathNavigator</span></span>
<span data-ttu-id="11ddf-103"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje sadu metod, které jsou použity k výběru sada uzlů v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> pomocí výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="11ddf-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="11ddf-104">Po výběru neprovedete iteraci vybrané sady uzlů.</span><span class="sxs-lookup"><span data-stu-id="11ddf-104">Once selected, you can iterate over the selected set of nodes.</span></span>  
  
## <a name="xpathnavigator-selection-methods"></a><span data-ttu-id="11ddf-105">Metody výběru objektem XPathNavigator nastaveným na</span><span class="sxs-lookup"><span data-stu-id="11ddf-105">XPathNavigator Selection Methods</span></span>  
 <span data-ttu-id="11ddf-106"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje sadu metod, které jsou použity k výběru sada uzlů v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> pomocí výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="11ddf-106">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="11ddf-107"><xref:System.Xml.XPath.XPathNavigator> Třída rovněž poskytuje sadu metod optimalizovaný pro rychlejší než při použití výrazu XPath výběru uzlů nadřazeného, podřízené domény a následníka.</span><span class="sxs-lookup"><span data-stu-id="11ddf-107">The <xref:System.Xml.XPath.XPathNavigator> class also provides a set of optimized methods for selecting ancestor, child and descendant nodes faster than using an XPath expression.</span></span> <span data-ttu-id="11ddf-108">Vybrané sady uzlů je vrácený v <xref:System.Xml.XPath.XPathNodeIterator> objektu nebo <xref:System.Xml.XPath.XPathNavigator> objektu v případě jednoho vybraného uzlu.</span><span class="sxs-lookup"><span data-stu-id="11ddf-108">The selected set of nodes is returned in an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
### <a name="selecting-nodes-using-xpath-expressions"></a><span data-ttu-id="11ddf-109">Výběr uzlů pomocí výrazů XPath</span><span class="sxs-lookup"><span data-stu-id="11ddf-109">Selecting Nodes Using XPath Expressions</span></span>  
 <span data-ttu-id="11ddf-110">Vybrat sadu uzlů pomocí výraz XPath, použijte jednu z následujících metod výběr.</span><span class="sxs-lookup"><span data-stu-id="11ddf-110">To select a set of nodes using an XPath expression, use one of the following selection methods.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 <span data-ttu-id="11ddf-111">Při volání těchto metod vrátí sadu uzlů, které můžete přejít pomocí volně <xref:System.Xml.XPath.XPathNodeIterator> objektu nebo <xref:System.Xml.XPath.XPathNavigator> objektu v případě jednoho vybraného uzlu.</span><span class="sxs-lookup"><span data-stu-id="11ddf-111">When called, these methods return a set of nodes that you can navigate freely using an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
 <span data-ttu-id="11ddf-112">Navigace pomocí <xref:System.Xml.XPath.XPathNodeIterator> objekt nemá vliv na umístění <xref:System.Xml.XPath.XPathNavigator> objekt použitý k jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="11ddf-112">Navigating with an <xref:System.Xml.XPath.XPathNodeIterator> object does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span> <span data-ttu-id="11ddf-113"><xref:System.Xml.XPath.XPathNavigator> Objekt vrácený z <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> metody je umístěn na jeden uzel vrácený a také nemá vliv na umístění <xref:System.Xml.XPath.XPathNavigator> objekt použitý k jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="11ddf-113">The <xref:System.Xml.XPath.XPathNavigator> object returned from the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> methods is positioned on the single returned node and also does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span>  
  
 <span data-ttu-id="11ddf-114">Následující příklad ukazuje vytvoření objektu <xref:System.Xml.XPath.XPathNavigator> objektu z <xref:System.Xml.XPath.XPathDocument> objektu, použití <xref:System.Xml.XPath.XPathNavigator.Select%2A> pro výběr uzlů v <xref:System.Xml.XPath.XPathDocument> objektu a použití <xref:System.Xml.XPath.XPathNodeIterator> objektu k iteraci přes vybrané uzly.</span><span class="sxs-lookup"><span data-stu-id="11ddf-114">The following example shows the creation of an <xref:System.Xml.XPath.XPathNavigator> object from an <xref:System.Xml.XPath.XPathDocument> object, the use of the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method to select nodes in the <xref:System.Xml.XPath.XPathDocument> object, and the use of the <xref:System.Xml.XPath.XPathNodeIterator> object to iterate over the selected nodes.</span></span>  
  
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
  
 <span data-ttu-id="11ddf-115">V příkladu přebírá `books.xml` souboru jako vstup.</span><span class="sxs-lookup"><span data-stu-id="11ddf-115">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="optimized-selection-methods"></a><span data-ttu-id="11ddf-116">Optimalizované výběr metody</span><span class="sxs-lookup"><span data-stu-id="11ddf-116">Optimized Selection Methods</span></span>  
 <span data-ttu-id="11ddf-117"><xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, A <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> metody <xref:System.Xml.XPath.XPathNavigator> třídy představují výrazů XPath používaných k načtení uzly podřízené, následník a předchůdce.</span><span class="sxs-lookup"><span data-stu-id="11ddf-117">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class represent XPath expressions commonly used to retrieve child, descendant, and ancestor nodes.</span></span> <span data-ttu-id="11ddf-118">Tyto metody jsou optimalizované pro výkon a jsou rychlejší než jejich odpovídající výrazy XPath.</span><span class="sxs-lookup"><span data-stu-id="11ddf-118">These methods are optimized for performance and are faster than their corresponding XPath expressions.</span></span> <span data-ttu-id="11ddf-119"><xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, A <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> metody vybere nadřazený, podřízený a podřízených uzlů na základě <xref:System.Xml.XPath.XPathNodeType> hodnotu nebo místní název a obor názvů URI uzlů vybrat.</span><span class="sxs-lookup"><span data-stu-id="11ddf-119">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods selects ancestor, child, and descendant nodes based on an <xref:System.Xml.XPath.XPathNodeType> value or the local name and namespace URI of the nodes to select.</span></span> <span data-ttu-id="11ddf-120">Vybraný nadřazený, podřízený a podřízených uzlů, které jsou vráceny v <xref:System.Xml.XPath.XPathNodeIterator> objektu.</span><span class="sxs-lookup"><span data-stu-id="11ddf-120">The selected ancestor, child, and descendant nodes are returned in an <xref:System.Xml.XPath.XPathNodeIterator> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11ddf-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="11ddf-121">See also</span></span>

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [<span data-ttu-id="11ddf-122">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="11ddf-122">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [<span data-ttu-id="11ddf-123">Vyhodnocení výrazů XPath pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="11ddf-123">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
- [<span data-ttu-id="11ddf-124">Párování uzlů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="11ddf-124">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
- [<span data-ttu-id="11ddf-125">Rozpoznané typy uzlů s dotazy XPath</span><span class="sxs-lookup"><span data-stu-id="11ddf-125">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
- [<span data-ttu-id="11ddf-126">Dotazy XPath a obory názvů</span><span class="sxs-lookup"><span data-stu-id="11ddf-126">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
- [<span data-ttu-id="11ddf-127">Zkompilované výrazy XPath</span><span class="sxs-lookup"><span data-stu-id="11ddf-127">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
