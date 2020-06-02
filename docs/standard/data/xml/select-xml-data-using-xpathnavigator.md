---
title: Výběr dat XML pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: c268c49e-32b9-4171-b782-dcb7b065fa73
ms.openlocfilehash: d5e7074fc8c68a0a0243ea4ad237e713e0a729b3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289054"
---
# <a name="select-xml-data-using-xpathnavigator"></a><span data-ttu-id="a85b6-102">Výběr dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a85b6-102">Select XML Data Using XPathNavigator</span></span>
<span data-ttu-id="a85b6-103"><xref:System.Xml.XPath.XPathNavigator>Třída poskytuje sadu metod, které slouží k výběru sady uzlů v <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> objektu nebo pomocí výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="a85b6-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="a85b6-104">Po výběru můžete iterovat přes vybranou sadu uzlů.</span><span class="sxs-lookup"><span data-stu-id="a85b6-104">Once selected, you can iterate over the selected set of nodes.</span></span>  
  
## <a name="xpathnavigator-selection-methods"></a><span data-ttu-id="a85b6-105">Metody výběru XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a85b6-105">XPathNavigator Selection Methods</span></span>  
 <span data-ttu-id="a85b6-106"><xref:System.Xml.XPath.XPathNavigator>Třída poskytuje sadu metod, které slouží k výběru sady uzlů v <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> objektu nebo pomocí výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="a85b6-106">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="a85b6-107"><xref:System.Xml.XPath.XPathNavigator>Třída také poskytuje sadu optimalizovaných metod pro výběr nadřazených a podřízených uzlů rychleji než použití výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="a85b6-107">The <xref:System.Xml.XPath.XPathNavigator> class also provides a set of optimized methods for selecting ancestor, child and descendant nodes faster than using an XPath expression.</span></span> <span data-ttu-id="a85b6-108">Vybraná sada uzlů je vrácena v <xref:System.Xml.XPath.XPathNodeIterator> objektu nebo <xref:System.Xml.XPath.XPathNavigator> objektu v případě jednoho vybraného uzlu.</span><span class="sxs-lookup"><span data-stu-id="a85b6-108">The selected set of nodes is returned in an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
### <a name="selecting-nodes-using-xpath-expressions"></a><span data-ttu-id="a85b6-109">Výběr uzlů pomocí výrazů XPath</span><span class="sxs-lookup"><span data-stu-id="a85b6-109">Selecting Nodes Using XPath Expressions</span></span>  
 <span data-ttu-id="a85b6-110">Chcete-li vybrat sadu uzlů pomocí výrazu XPath, použijte jednu z následujících metod výběru.</span><span class="sxs-lookup"><span data-stu-id="a85b6-110">To select a set of nodes using an XPath expression, use one of the following selection methods.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 <span data-ttu-id="a85b6-111">Při volání tyto metody vrátí sadu uzlů, které můžete volně procházet pomocí <xref:System.Xml.XPath.XPathNodeIterator> objektu nebo <xref:System.Xml.XPath.XPathNavigator> objektu v případě jednoho vybraného uzlu.</span><span class="sxs-lookup"><span data-stu-id="a85b6-111">When called, these methods return a set of nodes that you can navigate freely using an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
 <span data-ttu-id="a85b6-112">Navigace s <xref:System.Xml.XPath.XPathNodeIterator> objektem nemá vliv na pozici <xref:System.Xml.XPath.XPathNavigator> objektu používaného k jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="a85b6-112">Navigating with an <xref:System.Xml.XPath.XPathNodeIterator> object does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span> <span data-ttu-id="a85b6-113"><xref:System.Xml.XPath.XPathNavigator>Objekt vrácený z <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> metod je umístěn na jednom vráceném uzlu a také nemá vliv na pozici <xref:System.Xml.XPath.XPathNavigator> objektu používaného k jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="a85b6-113">The <xref:System.Xml.XPath.XPathNavigator> object returned from the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> methods is positioned on the single returned node and also does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span>  
  
 <span data-ttu-id="a85b6-114">Následující příklad ukazuje vytvoření <xref:System.Xml.XPath.XPathNavigator> objektu z <xref:System.Xml.XPath.XPathDocument> objektu, použití <xref:System.Xml.XPath.XPathNavigator.Select%2A> metody k výběru uzlů v <xref:System.Xml.XPath.XPathDocument> objektu a použití <xref:System.Xml.XPath.XPathNodeIterator> objektu k iterování na vybraných uzlech.</span><span class="sxs-lookup"><span data-stu-id="a85b6-114">The following example shows the creation of an <xref:System.Xml.XPath.XPathNavigator> object from an <xref:System.Xml.XPath.XPathDocument> object, the use of the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method to select nodes in the <xref:System.Xml.XPath.XPathDocument> object, and the use of the <xref:System.Xml.XPath.XPathNodeIterator> object to iterate over the selected nodes.</span></span>  
  
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
  
 <span data-ttu-id="a85b6-115">Příklad přebírá `books.xml` soubor jako vstup.</span><span class="sxs-lookup"><span data-stu-id="a85b6-115">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="optimized-selection-methods"></a><span data-ttu-id="a85b6-116">Metody optimalizovaného výběru</span><span class="sxs-lookup"><span data-stu-id="a85b6-116">Optimized Selection Methods</span></span>  
 <span data-ttu-id="a85b6-117"><xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>Metody, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A> a <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> <xref:System.Xml.XPath.XPathNavigator> třídy reprezentují výrazy XPath běžně používané k načtení uzlů podřízenosti, následníka a předchůdce.</span><span class="sxs-lookup"><span data-stu-id="a85b6-117">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class represent XPath expressions commonly used to retrieve child, descendant, and ancestor nodes.</span></span> <span data-ttu-id="a85b6-118">Tyto metody jsou optimalizované pro výkon a jsou rychlejší než jejich odpovídající výrazy XPath.</span><span class="sxs-lookup"><span data-stu-id="a85b6-118">These methods are optimized for performance and are faster than their corresponding XPath expressions.</span></span> <span data-ttu-id="a85b6-119"><xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>Metody, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A> a slouží <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> k výběru nadřazených uzlů, podřízených uzlů a následníků na základě <xref:System.Xml.XPath.XPathNodeType> hodnoty nebo místního názvu a identifikátoru URI uzlů, které chcete vybrat.</span><span class="sxs-lookup"><span data-stu-id="a85b6-119">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods selects ancestor, child, and descendant nodes based on an <xref:System.Xml.XPath.XPathNodeType> value or the local name and namespace URI of the nodes to select.</span></span> <span data-ttu-id="a85b6-120">Vybrané předchůdce, podřízené uzly a následníky jsou vráceny v <xref:System.Xml.XPath.XPathNodeIterator> objektu.</span><span class="sxs-lookup"><span data-stu-id="a85b6-120">The selected ancestor, child, and descendant nodes are returned in an <xref:System.Xml.XPath.XPathNodeIterator> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a85b6-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="a85b6-121">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="a85b6-122">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="a85b6-122">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="a85b6-123">Vyhodnocení výrazů XPath pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a85b6-123">Evaluate XPath Expressions using XPathNavigator</span></span>](evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="a85b6-124">Párování uzlů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a85b6-124">Matching Nodes using XPathNavigator</span></span>](matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="a85b6-125">Rozpoznané typy uzlů s dotazy XPath</span><span class="sxs-lookup"><span data-stu-id="a85b6-125">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="a85b6-126">Dotazy a obory názvů XPath</span><span class="sxs-lookup"><span data-stu-id="a85b6-126">XPath Queries and Namespaces</span></span>](xpath-queries-and-namespaces.md)
- [<span data-ttu-id="a85b6-127">Zkompilované výrazy XPath</span><span class="sxs-lookup"><span data-stu-id="a85b6-127">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)
