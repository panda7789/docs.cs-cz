---
title: Dotazování na XDocument vs. dotazování na XElement
ms.date: 07/20/2015
ms.assetid: 2d111f84-0ded-4cde-8d93-5440557a726d
ms.openlocfilehash: 3cd79c8f2cde101de43a9b9e983709e2e0d11814
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396295"
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-visual-basic"></a><span data-ttu-id="3d5c8-102">Dotazování na XDocument a dotazování na XElement (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d5c8-102">Querying an XDocument vs. Querying an XElement (Visual Basic)</span></span>
<span data-ttu-id="3d5c8-103">Když načtete dokument prostřednictvím <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> , všimnete si, že budete muset psát dotazy trochu jinak než při načítání prostřednictvím <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3d5c8-103">When you load a document via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, you will notice that you have to write queries slightly differently than when you load via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a><span data-ttu-id="3d5c8-104">Porovnání XDocument. Load a XElement. Load</span><span class="sxs-lookup"><span data-stu-id="3d5c8-104">Comparison of XDocument.Load and XElement.Load</span></span>  
 <span data-ttu-id="3d5c8-105">Když načtete dokument XML do <xref:System.Xml.Linq.XElement> Via, v <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XElement> kořenu stromu XML obsahuje kořenový prvek načteného dokumentu.</span><span class="sxs-lookup"><span data-stu-id="3d5c8-105">When you load an XML document into an <xref:System.Xml.Linq.XElement> via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, the <xref:System.Xml.Linq.XElement> at the root of the XML tree contains the root element of the loaded document.</span></span> <span data-ttu-id="3d5c8-106">Nicméně když načtete stejný dokument XML do <xref:System.Xml.Linq.XDocument> Via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> , kořen stromové struktury je <xref:System.Xml.Linq.XDocument> uzel a kořenový prvek načteného dokumentu je jeden povolený podřízený <xref:System.Xml.Linq.XElement> uzel <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="3d5c8-106">However, when you load the same XML document into an <xref:System.Xml.Linq.XDocument> via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, the root of the tree is an <xref:System.Xml.Linq.XDocument> node, and the root element of the loaded document is the one allowed child <xref:System.Xml.Linq.XElement> node of the <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="3d5c8-107">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Osy pracují relativně ke kořenovému uzlu.</span><span class="sxs-lookup"><span data-stu-id="3d5c8-107">The [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axes operate relative to the root node.</span></span>  
  
 <span data-ttu-id="3d5c8-108">Tento první příklad načte strom XML pomocí <xref:System.Xml.Linq.XElement.Load%2A> .</span><span class="sxs-lookup"><span data-stu-id="3d5c8-108">This first example loads an XML tree using <xref:System.Xml.Linq.XElement.Load%2A>.</span></span> <span data-ttu-id="3d5c8-109">Pak se dotazuje na podřízené prvky kořenového adresáře stromu.</span><span class="sxs-lookup"><span data-stu-id="3d5c8-109">It then queries for the child elements of the root of the tree.</span></span>  
  
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
  
 <span data-ttu-id="3d5c8-110">Jak je očekáváno, tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3d5c8-110">As expected, this example produces the following output:</span></span>  
  
```console
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 <span data-ttu-id="3d5c8-111">Následující příklad je stejný jako ten výše, s výjimkou, že je strom XML načten do <xref:System.Xml.Linq.XDocument> namísto <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="3d5c8-111">The following example is the same as the one above, with the exception that the XML tree is loaded into an <xref:System.Xml.Linq.XDocument> instead of an <xref:System.Xml.Linq.XElement>.</span></span>  
  
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
  
 <span data-ttu-id="3d5c8-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3d5c8-112">This example produces the following output:</span></span>  
  
```console
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 <span data-ttu-id="3d5c8-113">Všimněte si, že stejný dotaz vrátil jeden `Root` uzel místo tří podřízených uzlů.</span><span class="sxs-lookup"><span data-stu-id="3d5c8-113">Notice that the same query returned the one `Root` node instead of the three child nodes.</span></span>  
  
 <span data-ttu-id="3d5c8-114">Jedním z přístupů k tomu, abyste se s ním mohli pracovat, je použít <xref:System.Xml.Linq.XDocument.Root%2A> vlastnost před přístupem k metodám OS následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="3d5c8-114">One approach to dealing with this is to use the <xref:System.Xml.Linq.XDocument.Root%2A> property before accessing the axes methods, as follows:</span></span>  
  
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
  
 <span data-ttu-id="3d5c8-115">Tento dotaz teď funguje stejným způsobem jako dotaz na stromové struktuře, ve které se nachází root <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="3d5c8-115">This query now performs in the same way as the query on the tree rooted in <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="3d5c8-116">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3d5c8-116">The example produces the following output:</span></span>  
  
```console
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3d5c8-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="3d5c8-117">See also</span></span>

- [<span data-ttu-id="3d5c8-118">Základní dotazy (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d5c8-118">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](basic-queries-linq-to-xml.md)
