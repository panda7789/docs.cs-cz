---
title: 'Postupy: vyhledání všech uzlů v oboru názvů'
ms.date: 07/20/2015
ms.assetid: b735d7da-5727-48a3-ab57-a16378adc32e
ms.openlocfilehash: f6bc38140bc2ea43393133d78c798469d26671c5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352972"
---
# <a name="how-to-find-all-nodes-in-a-namespace-visual-basic"></a><span data-ttu-id="9f53b-102">Postupy: vyhledání všech uzlů v oboru názvů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f53b-102">How to: Find All Nodes in a Namespace (Visual Basic)</span></span>
<span data-ttu-id="9f53b-103">Můžete filtrovat podle oboru názvů každého elementu nebo atributu, aby bylo možné najít všechny uzly v daném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="9f53b-103">You can filter on the namespace of each element or attribute to find all nodes in that particular namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f53b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f53b-104">Example</span></span>  
 <span data-ttu-id="9f53b-105">Následující příklad vytvoří strom XML se dvěma obory názvů.</span><span class="sxs-lookup"><span data-stu-id="9f53b-105">The following example creates an XML tree with two namespaces.</span></span> <span data-ttu-id="9f53b-106">Pak projde stromovou strukturou a vytiskne názvy všech prvků a atributů v jednom z těchto oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="9f53b-106">It then iterates through the tree and prints the names of all the elements and attributes in one of those namespaces.</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
    Sub Main()  
        Dim xmlTree As XElement = _  
            <aw:Root>  
                <fc:Child1>abc</fc:Child1>  
                <fc:Child2>def</fc:Child2>  
                <aw:Child3>ghi</aw:Child3>  
                <fc:Child4>  
                    <fc:GrandChild1>jkl</fc:GrandChild1>  
                    <aw:GrandChild2>mno</aw:GrandChild2>  
                </fc:Child4>  
            </aw:Root>  
        Console.WriteLine("Nodes in the http://www.adventure-works.com namespace")  
        Dim awElements As IEnumerable(Of XElement) = _  
            From el In xmlTree.Descendants() _  
            Where (el.Name.Namespace = GetXmlNamespace(aw)) _  
            Select el  
        For Each el As XElement In awElements  
            Console.WriteLine(el.Name.ToString())  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="9f53b-107">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="9f53b-107">This code produces the following output:</span></span>  
  
```console  
Nodes in the http://www.adventure-works.com namespace  
{http://www.adventure-works.com}Child3  
{http://www.adventure-works.com}GrandChild2  
```  
  
## <a name="example"></a><span data-ttu-id="9f53b-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f53b-108">Example</span></span>  
 <span data-ttu-id="9f53b-109">Soubor XML, ke kterému má přistup následující dotaz, obsahuje objednávky nákupu ve dvou různých oborech názvů.</span><span class="sxs-lookup"><span data-stu-id="9f53b-109">The XML file accessed by the following query contains purchase orders in two different namespaces.</span></span> <span data-ttu-id="9f53b-110">Dotaz vytvoří nový strom s pouze prvky v jednom z oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="9f53b-110">The query creates a new tree with just the elements in one of the namespaces.</span></span>  
  
 <span data-ttu-id="9f53b-111">Tento příklad používá následující dokument XML: [vzorový soubor XML: konsolidované nákupní objednávky](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-consolidated-purchase-orders.md).</span><span class="sxs-lookup"><span data-stu-id="9f53b-111">This example uses the following XML document: [Sample XML File: Consolidated Purchase Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-consolidated-purchase-orders.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim cpo As XDocument = XDocument.Load("ConsolidatedPurchaseOrders.xml")  
        Dim newTree As XElement = _  
            <Root>  
                <%= From el In cpo.Root.Elements() _  
                    Where el.Name.Namespace = GetXmlNamespace(aw) _  
                    Select el %>  
            </Root>  
        Console.WriteLine(newTree)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="9f53b-112">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="9f53b-112">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <aw:PurchaseOrder PONumber="11223" Date="2000-01-15" xmlns:aw="http://www.adventure-works.com">  
    <aw:ShippingAddress>  
      <aw:Name>Chris Preston</aw:Name>  
      <aw:Street>123 Main St.</aw:Street>  
      <aw:City>Seattle</aw:City>  
      <aw:State>WA</aw:State>  
      <aw:Zip>98113</aw:Zip>  
      <aw:Country>USA</aw:Country>  
    </aw:ShippingAddress>  
    <aw:BillingAddress>  
      <aw:Name>Chris Preston</aw:Name>  
      <aw:Street>123 Main St.</aw:Street>  
      <aw:City>Seattle</aw:City>  
      <aw:State>WA</aw:State>  
      <aw:Zip>98113</aw:Zip>  
      <aw:Country>USA</aw:Country>  
    </aw:BillingAddress>  
    <aw:DeliveryInstructions>Ship only complete order.</aw:DeliveryInstructions>  
    <aw:Item PartNum="LIT-01">  
      <aw:ProductID>Litware Networking Card</aw:ProductID>  
      <aw:Qty>1</aw:Qty>  
      <aw:Price>20.99</aw:Price>  
    </aw:Item>  
    <aw:Item PartNum="LIT-25">  
      <aw:ProductID>Litware 17in LCD Monitor</aw:ProductID>  
      <aw:Qty>1</aw:Qty>  
      <aw:Price>199.99</aw:Price>  
    </aw:Item>  
  </aw:PurchaseOrder>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9f53b-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f53b-113">See also</span></span>

- [<span data-ttu-id="9f53b-114">Základní dotazy (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f53b-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
