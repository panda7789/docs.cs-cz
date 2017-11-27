---
title: "Postupy: vyhledání všech uzlů v Namespace (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 3a38b913-a53e-4d0e-a19d-8782bffd3364
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 766b0b4ff535703e6acdfeb409a51bb09a265e43
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-all-nodes-in-a-namespace-c"></a><span data-ttu-id="39248-102">Postupy: vyhledání všech uzlů v Namespace (C#)</span><span class="sxs-lookup"><span data-stu-id="39248-102">How to: Find All Nodes in a Namespace (C#)</span></span>
<span data-ttu-id="39248-103">Můžete filtrovat podle oboru názvů jednotlivých elementu nebo atributu najít všechny uzly v tomto konkrétním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="39248-103">You can filter on the namespace of each element or attribute to find all nodes in that particular namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39248-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="39248-104">Example</span></span>  
 <span data-ttu-id="39248-105">Následující příklad vytvoří strom XML s dva obory názvů.</span><span class="sxs-lookup"><span data-stu-id="39248-105">The following example creates an XML tree with two namespaces.</span></span> <span data-ttu-id="39248-106">Potom iteruje v rámci stromu a vytiskne názvy všech elementů a atributů v jednom z těchto oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="39248-106">It then iterates through the tree and prints the names of all the elements and attributes in one of those namespaces.</span></span>  
  
```csharp  
string markup = @"<aw:Root xmlns:aw='http://www.adventure-works.com' xmlns:fc='www.fourthcoffee.com'>  
  <fc:Child1>abc</fc:Child1>  
  <fc:Child2>def</fc:Child2>  
  <aw:Child3>ghi</aw:Child3>  
  <fc:Child4>  
    <fc:GrandChild1>jkl</fc:GrandChild1>  
    <aw:GrandChild2>mno</aw:GrandChild2>  
  </fc:Child4>  
</aw:Root>";  
XElement xmlTree = XElement.Parse(markup);  
Console.WriteLine("Nodes in the http://www.adventure-works.com namespace");  
IEnumerable<XElement> awElements =  
    from el in xmlTree.Descendants()  
    where el.Name.Namespace == "http://www.adventure-works.com"  
    select el;  
foreach (XElement el in awElements)  
    Console.WriteLine(el.Name.ToString());  
```  
  
 <span data-ttu-id="39248-107">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="39248-107">This code produces the following output:</span></span>  
  
```  
Nodes in the http://www.adventure-works.com namespace  
{http://www.adventure-works.com}Child3  
{http://www.adventure-works.com}GrandChild2  
```  
  
## <a name="example"></a><span data-ttu-id="39248-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="39248-108">Example</span></span>  
 <span data-ttu-id="39248-109">Soubor XML přístup následující dotaz obsahuje nákupních objednávek ve dvou různých oborech názvů.</span><span class="sxs-lookup"><span data-stu-id="39248-109">The XML file accessed by the following query contains purchase orders in two different namespaces.</span></span> <span data-ttu-id="39248-110">Dotaz vytvoří novou větev se jenom elementy v jednom z oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="39248-110">The query creates a new tree with just the elements in one of the namespaces.</span></span>  
  
 <span data-ttu-id="39248-111">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: konsolidovat nákupních objednávek](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-consolidated-purchase-orders.md).</span><span class="sxs-lookup"><span data-stu-id="39248-111">This example uses the following XML document: [Sample XML File: Consolidated Purchase Orders](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-consolidated-purchase-orders.md).</span></span>  
  
```csharp  
XDocument cpo = XDocument.Load("ConsolidatedPurchaseOrders.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement newTree = new XElement("Root",  
    from el in cpo.Root.Elements()  
    where el.Name.Namespace == aw  
    select el  
);  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="39248-112">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="39248-112">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="39248-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="39248-113">See Also</span></span>  
 [<span data-ttu-id="39248-114">Základní dotazy (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="39248-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
