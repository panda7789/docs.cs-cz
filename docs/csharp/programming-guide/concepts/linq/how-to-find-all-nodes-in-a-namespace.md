---
title: Vyhledání všech uzlů v oboru názvů (C#)
description: Naučte se filtrovat obor názvů každého elementu nebo atributu pro vyhledání všech uzlů v daném oboru názvů.
ms.date: 07/20/2015
ms.assetid: 3a38b913-a53e-4d0e-a19d-8782bffd3364
ms.openlocfilehash: bf739480c6b4e2c53d5c430d47ff833e8995f6a4
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303306"
---
# <a name="how-to-find-all-nodes-in-a-namespace-c"></a><span data-ttu-id="d6ca6-103">Vyhledání všech uzlů v oboru názvů (C#)</span><span class="sxs-lookup"><span data-stu-id="d6ca6-103">How to find all nodes in a namespace (C#)</span></span>
<span data-ttu-id="d6ca6-104">Můžete filtrovat podle oboru názvů každého elementu nebo atributu, aby bylo možné najít všechny uzly v daném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d6ca6-104">You can filter on the namespace of each element or attribute to find all nodes in that particular namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6ca6-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6ca6-105">Example</span></span>  
 <span data-ttu-id="d6ca6-106">Následující příklad vytvoří strom XML se dvěma obory názvů.</span><span class="sxs-lookup"><span data-stu-id="d6ca6-106">The following example creates an XML tree with two namespaces.</span></span> <span data-ttu-id="d6ca6-107">Pak projde stromovou strukturou a vytiskne názvy všech prvků a atributů v jednom z těchto oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="d6ca6-107">It then iterates through the tree and prints the names of all the elements and attributes in one of those namespaces.</span></span>  
  
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
  
 <span data-ttu-id="d6ca6-108">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d6ca6-108">This code produces the following output:</span></span>  
  
```output  
Nodes in the http://www.adventure-works.com namespace  
{http://www.adventure-works.com}Child3  
{http://www.adventure-works.com}GrandChild2  
```  
  
## <a name="example"></a><span data-ttu-id="d6ca6-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6ca6-109">Example</span></span>  
 <span data-ttu-id="d6ca6-110">Soubor XML, ke kterému má přistup následující dotaz, obsahuje objednávky nákupu ve dvou různých oborech názvů.</span><span class="sxs-lookup"><span data-stu-id="d6ca6-110">The XML file accessed by the following query contains purchase orders in two different namespaces.</span></span> <span data-ttu-id="d6ca6-111">Dotaz vytvoří nový strom s pouze prvky v jednom z oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="d6ca6-111">The query creates a new tree with just the elements in one of the namespaces.</span></span>  
  
 <span data-ttu-id="d6ca6-112">Tento příklad používá následující dokument XML: [vzorový soubor XML: konsolidované nákupní objednávky](./sample-xml-file-consolidated-purchase-orders.md).</span><span class="sxs-lookup"><span data-stu-id="d6ca6-112">This example uses the following XML document: [Sample XML File: Consolidated Purchase Orders](./sample-xml-file-consolidated-purchase-orders.md).</span></span>  
  
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
  
 <span data-ttu-id="d6ca6-113">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d6ca6-113">This code produces the following output:</span></span>  
  
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
