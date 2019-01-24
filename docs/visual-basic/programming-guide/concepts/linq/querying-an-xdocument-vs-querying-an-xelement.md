---
title: Dotazování na XDocument vs. Dotazování na XElement (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 2d111f84-0ded-4cde-8d93-5440557a726d
ms.openlocfilehash: 8d13276b6d66d0ec3768182df7b4324678174fae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54579842"
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-visual-basic"></a><span data-ttu-id="e2ede-102">Dotazování na XDocument vs. Dotazování na XElement (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2ede-102">Querying an XDocument vs. Querying an XElement (Visual Basic)</span></span>
<span data-ttu-id="e2ede-103">Při načtení dokumentu prostřednictvím <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, všimnete si, že budete muset psát dotazy trochu jinak než při načtení prostřednictvím <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e2ede-103">When you load a document via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, you will notice that you have to write queries slightly differently than when you load via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a><span data-ttu-id="e2ede-104">Porovnání XDocument.Load a XElement.Load</span><span class="sxs-lookup"><span data-stu-id="e2ede-104">Comparison of XDocument.Load and XElement.Load</span></span>  
 <span data-ttu-id="e2ede-105">Při načtení dokumentu XML do <xref:System.Xml.Linq.XElement> prostřednictvím <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement> v kořenovém adresáři XML stromu obsahuje kořenový element načtený dokument.</span><span class="sxs-lookup"><span data-stu-id="e2ede-105">When you load an XML document into an <xref:System.Xml.Linq.XElement> via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, the <xref:System.Xml.Linq.XElement> at the root of the XML tree contains the root element of the loaded document.</span></span> <span data-ttu-id="e2ede-106">Ale při načtení stejný dokument XML do <xref:System.Xml.Linq.XDocument> prostřednictvím <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, je kořen stromu <xref:System.Xml.Linq.XDocument> uzel a kořenový element načtený dokument je jeden podřízený prvek povolený <xref:System.Xml.Linq.XElement> uzlu <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="e2ede-106">However, when you load the same XML document into an <xref:System.Xml.Linq.XDocument> via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, the root of the tree is an <xref:System.Xml.Linq.XDocument> node, and the root element of the loaded document is the one allowed child <xref:System.Xml.Linq.XElement> node of the <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="e2ede-107">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Osy pracovat vzhledem k kořenového uzlu.</span><span class="sxs-lookup"><span data-stu-id="e2ede-107">The [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axes operate relative to the root node.</span></span>  
  
 <span data-ttu-id="e2ede-108">Tento první příklad načte stromu XML pomocí <xref:System.Xml.Linq.XElement.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="e2ede-108">This first example loads an XML tree using <xref:System.Xml.Linq.XElement.Load%2A>.</span></span> <span data-ttu-id="e2ede-109">Následně dotazy pro podřízené prvky kořen stromu.</span><span class="sxs-lookup"><span data-stu-id="e2ede-109">It then queries for the child elements of the root of the tree.</span></span>  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XElement.Load")  
Console.WriteLine("----")  
Dim doc As XElement = XElement.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 <span data-ttu-id="e2ede-110">Podle očekávání, tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="e2ede-110">As expected, this example produces the following output:</span></span>  
  
```  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 <span data-ttu-id="e2ede-111">Následující příklad je stejný jako ten výše, s tím rozdílem, který je načten stromu XML do <xref:System.Xml.Linq.XDocument> místo <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="e2ede-111">The following example is the same as the one above, with the exception that the XML tree is loaded into an <xref:System.Xml.Linq.XDocument> instead of an <xref:System.Xml.Linq.XElement>.</span></span>  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XDocument.Load")  
Console.WriteLine("----")  
Dim doc As XDocument = XDocument.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 <span data-ttu-id="e2ede-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="e2ede-112">This example produces the following output:</span></span>  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 <span data-ttu-id="e2ede-113">Všimněte si, že stejný dotaz vrátil ten `Root` uzlu namísto tří podřízených uzlů.</span><span class="sxs-lookup"><span data-stu-id="e2ede-113">Notice that the same query returned the one `Root` node instead of the three child nodes.</span></span>  
  
 <span data-ttu-id="e2ede-114">Jedním z přístupů k práci s tímto je použít <xref:System.Xml.Linq.XDocument.Root%2A> vlastnost před použitím metody osy následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e2ede-114">One approach to dealing with this is to use the <xref:System.Xml.Linq.XDocument.Root%2A> property before accessing the axes methods, as follows:</span></span>  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XDocument.Load")  
Console.WriteLine("----")  
Dim doc As XDocument = XDocument.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Root.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 <span data-ttu-id="e2ede-115">Tento dotaz teď provádí stejným způsobem jako dotazu ve stromové struktuře integrován <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="e2ede-115">This query now performs in the same way as the query on the tree rooted in <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="e2ede-116">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="e2ede-116">The example produces the following output:</span></span>  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e2ede-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2ede-117">See also</span></span>
- [<span data-ttu-id="e2ede-118">Základní dotazy (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2ede-118">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
