---
title: Výběr dat XML pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: c268c49e-32b9-4171-b782-dcb7b065fa73
ms.openlocfilehash: 99b6b3b6959abf4c8adc313364ad641249bd9bc3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710164"
---
# <a name="select-xml-data-using-xpathnavigator"></a><span data-ttu-id="2388f-102">Výběr dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="2388f-102">Select XML Data Using XPathNavigator</span></span>
<span data-ttu-id="2388f-103">Třída <xref:System.Xml.XPath.XPathNavigator> poskytuje sadu metod, které slouží k výběru sady uzlů v objektu <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> pomocí výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="2388f-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="2388f-104">Po výběru můžete iterovat přes vybranou sadu uzlů.</span><span class="sxs-lookup"><span data-stu-id="2388f-104">Once selected, you can iterate over the selected set of nodes.</span></span>  
  
## <a name="xpathnavigator-selection-methods"></a><span data-ttu-id="2388f-105">Metody výběru XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="2388f-105">XPathNavigator Selection Methods</span></span>  
 <span data-ttu-id="2388f-106">Třída <xref:System.Xml.XPath.XPathNavigator> poskytuje sadu metod, které slouží k výběru sady uzlů v objektu <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> pomocí výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="2388f-106">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="2388f-107">Třída <xref:System.Xml.XPath.XPathNavigator> také poskytuje sadu optimalizovaných metod pro výběr nadřazených a podřízených uzlů rychleji než použití výrazu XPath.</span><span class="sxs-lookup"><span data-stu-id="2388f-107">The <xref:System.Xml.XPath.XPathNavigator> class also provides a set of optimized methods for selecting ancestor, child and descendant nodes faster than using an XPath expression.</span></span> <span data-ttu-id="2388f-108">Vybraná sada uzlů se vrátí v objektu <xref:System.Xml.XPath.XPathNodeIterator> nebo objektu <xref:System.Xml.XPath.XPathNavigator> v případě jednoho vybraného uzlu.</span><span class="sxs-lookup"><span data-stu-id="2388f-108">The selected set of nodes is returned in an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
### <a name="selecting-nodes-using-xpath-expressions"></a><span data-ttu-id="2388f-109">Výběr uzlů pomocí výrazů XPath</span><span class="sxs-lookup"><span data-stu-id="2388f-109">Selecting Nodes Using XPath Expressions</span></span>  
 <span data-ttu-id="2388f-110">Chcete-li vybrat sadu uzlů pomocí výrazu XPath, použijte jednu z následujících metod výběru.</span><span class="sxs-lookup"><span data-stu-id="2388f-110">To select a set of nodes using an XPath expression, use one of the following selection methods.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 <span data-ttu-id="2388f-111">Při volání tyto metody vrátí sadu uzlů, které můžete volně procházet pomocí objektu <xref:System.Xml.XPath.XPathNodeIterator> nebo objektu <xref:System.Xml.XPath.XPathNavigator> v případě jednoho vybraného uzlu.</span><span class="sxs-lookup"><span data-stu-id="2388f-111">When called, these methods return a set of nodes that you can navigate freely using an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
 <span data-ttu-id="2388f-112">Navigace s objektem <xref:System.Xml.XPath.XPathNodeIterator> nemá vliv na pozici objektu <xref:System.Xml.XPath.XPathNavigator> používaného k jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="2388f-112">Navigating with an <xref:System.Xml.XPath.XPathNodeIterator> object does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span> <span data-ttu-id="2388f-113">Objekt <xref:System.Xml.XPath.XPathNavigator> vrácený z <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>ch metod je umístěn na jednom vráceném uzlu a také nemá vliv na pozici objektu <xref:System.Xml.XPath.XPathNavigator>, který se používá k jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="2388f-113">The <xref:System.Xml.XPath.XPathNavigator> object returned from the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> methods is positioned on the single returned node and also does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span>  
  
 <span data-ttu-id="2388f-114">Následující příklad ukazuje vytvoření objektu <xref:System.Xml.XPath.XPathNavigator> z objektu <xref:System.Xml.XPath.XPathDocument>, použití metody <xref:System.Xml.XPath.XPathNavigator.Select%2A> k výběru uzlů v objektu <xref:System.Xml.XPath.XPathDocument> a použití objektu <xref:System.Xml.XPath.XPathNodeIterator> k iterování na vybraných uzlech.</span><span class="sxs-lookup"><span data-stu-id="2388f-114">The following example shows the creation of an <xref:System.Xml.XPath.XPathNavigator> object from an <xref:System.Xml.XPath.XPathDocument> object, the use of the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method to select nodes in the <xref:System.Xml.XPath.XPathDocument> object, and the use of the <xref:System.Xml.XPath.XPathNodeIterator> object to iterate over the selected nodes.</span></span>  
  
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
  
 <span data-ttu-id="2388f-115">V příkladu se jako vstup používá soubor `books.xml`.</span><span class="sxs-lookup"><span data-stu-id="2388f-115">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="optimized-selection-methods"></a><span data-ttu-id="2388f-116">Metody optimalizovaného výběru</span><span class="sxs-lookup"><span data-stu-id="2388f-116">Optimized Selection Methods</span></span>  
 <span data-ttu-id="2388f-117">Metody <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>a <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> třídy <xref:System.Xml.XPath.XPathNavigator> reprezentují výrazy XPath běžně používané k načtení uzlů podřízenosti, následníka a předchůdce.</span><span class="sxs-lookup"><span data-stu-id="2388f-117">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class represent XPath expressions commonly used to retrieve child, descendant, and ancestor nodes.</span></span> <span data-ttu-id="2388f-118">Tyto metody jsou optimalizované pro výkon a jsou rychlejší než jejich odpovídající výrazy XPath.</span><span class="sxs-lookup"><span data-stu-id="2388f-118">These methods are optimized for performance and are faster than their corresponding XPath expressions.</span></span> <span data-ttu-id="2388f-119">Metody <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>a <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> vyberou nadřazené, podřízené a odvozené uzly na základě hodnoty <xref:System.Xml.XPath.XPathNodeType> nebo místního názvu a identifikátoru URI oboru názvů uzlů k výběru.</span><span class="sxs-lookup"><span data-stu-id="2388f-119">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods selects ancestor, child, and descendant nodes based on an <xref:System.Xml.XPath.XPathNodeType> value or the local name and namespace URI of the nodes to select.</span></span> <span data-ttu-id="2388f-120">Vybrané uzly předchůdce, podřízené a následníka jsou vráceny v objektu <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="2388f-120">The selected ancestor, child, and descendant nodes are returned in an <xref:System.Xml.XPath.XPathNodeIterator> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2388f-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2388f-121">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="2388f-122">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="2388f-122">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="2388f-123">Vyhodnocení výrazů XPath pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="2388f-123">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="2388f-124">Párování uzlů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="2388f-124">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="2388f-125">Rozpoznané typy uzlů s dotazy XPath</span><span class="sxs-lookup"><span data-stu-id="2388f-125">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="2388f-126">Dotazy XPath a obory názvů</span><span class="sxs-lookup"><span data-stu-id="2388f-126">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [<span data-ttu-id="2388f-127">Zkompilované výrazy XPath</span><span class="sxs-lookup"><span data-stu-id="2388f-127">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
