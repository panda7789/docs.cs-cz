---
title: 'Postupy: Vyhledání všech uzlů v Namespace (C#)'
ms.date: 07/20/2015
ms.assetid: 3a38b913-a53e-4d0e-a19d-8782bffd3364
ms.openlocfilehash: d94a6c517a76e8ed91f20a17e798ad3806a34a70
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486817"
---
# <a name="how-to-find-all-nodes-in-a-namespace-c"></a><span data-ttu-id="44c3a-102">Postupy: Vyhledání všech uzlů v Namespace (C#)</span><span class="sxs-lookup"><span data-stu-id="44c3a-102">How to: Find All Nodes in a Namespace (C#)</span></span>
<span data-ttu-id="44c3a-103">Můžete filtrovat podle oboru názvů jednotlivých elementu nebo atributu k vyhledání všech uzlů v tomto konkrétním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="44c3a-103">You can filter on the namespace of each element or attribute to find all nodes in that particular namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44c3a-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="44c3a-104">Example</span></span>  
 <span data-ttu-id="44c3a-105">Následující příklad vytvoří stromu XML pomocí dva obory názvů.</span><span class="sxs-lookup"><span data-stu-id="44c3a-105">The following example creates an XML tree with two namespaces.</span></span> <span data-ttu-id="44c3a-106">Pak Iteruje přes stromu a Vypíše názvy všech elementů a atributů v jednom z těchto oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="44c3a-106">It then iterates through the tree and prints the names of all the elements and attributes in one of those namespaces.</span></span>  
  
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
  
 <span data-ttu-id="44c3a-107">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="44c3a-107">This code produces the following output:</span></span>  
  
```  
Nodes in the http://www.adventure-works.com namespace  
{http://www.adventure-works.com}Child3  
{http://www.adventure-works.com}GrandChild2  
```  
  
## <a name="example"></a><span data-ttu-id="44c3a-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="44c3a-108">Example</span></span>  
 <span data-ttu-id="44c3a-109">Soubor XML přistupuje následující dotaz obsahuje nákupních objednávek ve dvou různých oborech názvů.</span><span class="sxs-lookup"><span data-stu-id="44c3a-109">The XML file accessed by the following query contains purchase orders in two different namespaces.</span></span> <span data-ttu-id="44c3a-110">Dotaz vytvoří nové větve s prvky v jednom z oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="44c3a-110">The query creates a new tree with just the elements in one of the namespaces.</span></span>  
  
 <span data-ttu-id="44c3a-111">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Konsolidované nákupní objednávky](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-consolidated-purchase-orders.md).</span><span class="sxs-lookup"><span data-stu-id="44c3a-111">This example uses the following XML document: [Sample XML File: Consolidated Purchase Orders](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-consolidated-purchase-orders.md).</span></span>  
  
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
  
 <span data-ttu-id="44c3a-112">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="44c3a-112">This code produces the following output:</span></span>  
  
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
