---
title: "Postupy: tvoří řetěz volání metod osy (technologie LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7cf5cb445dc64dfa5f4734ae58e6e921a5a92148
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-c"></a><span data-ttu-id="b4720-102">Postupy: tvoří řetěz volání metod osy (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b4720-102">How to: Chain Axis Method Calls (LINQ to XML) (C#)</span></span>
<span data-ttu-id="b4720-103">Volání metody osy a pak volání některá z rozšíření metoda OS je běžný vzor, který budete používat v kódu.</span><span class="sxs-lookup"><span data-stu-id="b4720-103">A common pattern that you will use in your code is to call an axis method, then call one of the extension method axes.</span></span>  
  
 <span data-ttu-id="b4720-104">Existují dvě osy s názvem `Elements` kolekci elementů, které vracejí: <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> metoda a <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="b4720-104">There are two axes with the name of `Elements` that return a collection of elements: the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method and the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b4720-105">Tyto dvě osy najít všechny elementy zadaným názvem v daném hloubce ve stromové struktuře můžete kombinovat.</span><span class="sxs-lookup"><span data-stu-id="b4720-105">You can combine these two axes to find all elements of a specified name at a given depth in the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4720-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="b4720-106">Example</span></span>  
 <span data-ttu-id="b4720-107">Tento příklad používá <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> a <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> najdete všechny `Name` elementy ve všech `Address` elementy ve všech `PurchaseOrder` elementy.</span><span class="sxs-lookup"><span data-stu-id="b4720-107">This example uses <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> and <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> to find all `Name` elements in all `Address` elements in all `PurchaseOrder` elements.</span></span>  
  
 <span data-ttu-id="b4720-108">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: více nákupních objednávek (technologie LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b4720-108">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XElement purchaseOrders = XElement.Load("PurchaseOrders.xml");  
IEnumerable<XElement> names =  
    from el in purchaseOrders  
        .Elements("PurchaseOrder")  
        .Elements("Address")  
        .Elements("Name")  
    select el;  
foreach (XElement e in names)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="b4720-109">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b4720-109">This example produces the following output:</span></span>  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 <span data-ttu-id="b4720-110">Toto funguje, protože jeden z implementace `Elements` osy je jako metody rozšíření na <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="b4720-110">This works because one of the implementations of the `Elements` axis is as an extension method on <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="b4720-111"><xref:System.Xml.Linq.XElement>odvozená z <xref:System.Xml.Linq.XContainer>, takže můžete volat <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> metodu výsledky volání <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="b4720-111"><xref:System.Xml.Linq.XElement> derives from <xref:System.Xml.Linq.XContainer>, so you can call the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method on the results of a call to the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4720-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="b4720-112">Example</span></span>  
 <span data-ttu-id="b4720-113">V některých případech můžete obnovit všechny elementy při hloubce určitý element když existuje může nebo nemusí být použité nadřazených.</span><span class="sxs-lookup"><span data-stu-id="b4720-113">Sometimes you want to retrieve all elements at a particular element depth when there might or might not be intervening ancestors.</span></span> <span data-ttu-id="b4720-114">Například v následujícím dokumentu, můžete chtít načíst všechny `ConfigParameter` prvky, které jsou podřízené objekty `Customer` elementu, ale ne `ConfigParameter` tedy podřízenou `Root` elementu.</span><span class="sxs-lookup"><span data-stu-id="b4720-114">For example, in the following document, you might want to retrieve all the `ConfigParameter` elements that are children of the `Customer` element, but not the `ConfigParameter` that is a child of the `Root` element.</span></span>  
  
```xml  
<Root>  
  <ConfigParameter>RootConfigParameter</ConfigParameter>  
  <Customer>  
    <Name>Frank</Name>  
    <Config>  
      <ConfigParameter>FirstConfigParameter</ConfigParameter>  
    </Config>  
  </Customer>  
  <Customer>  
    <Name>Bob</Name>  
    <!--This customer doesn't have a Config element-->  
  </Customer>  
  <Customer>  
    <Name>Bill</Name>  
    <Config>  
      <ConfigParameter>SecondConfigParameter</ConfigParameter>  
    </Config>  
  </Customer>  
</Root>  
```  
  
 <span data-ttu-id="b4720-115">Chcete-li to provést, můžete použít <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> osy, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="b4720-115">To do this, you can use the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> axis, as follows:</span></span>  
  
```csharp  
XElement root = XElement.Load("Irregular.xml");  
IEnumerable<XElement> configParameters =   
    root.Elements("Customer").Elements("Config").  
    Elements("ConfigParameter");  
foreach (XElement cp in configParameters)  
    Console.WriteLine(cp);  
```  
  
 <span data-ttu-id="b4720-116">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b4720-116">This example produces the following output:</span></span>  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a><span data-ttu-id="b4720-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="b4720-117">Example</span></span>  
 <span data-ttu-id="b4720-118">Následující příklad ukazuje stejným způsobem pro formát XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b4720-118">The following example shows the same technique for XML that is in a namespace.</span></span> <span data-ttu-id="b4720-119">Další informace najdete v tématu [práci s obory názvů XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="b4720-119">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="b4720-120">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: více nákupních objednávek v Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="b4720-120">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement purchaseOrders = XElement.Load("PurchaseOrdersInNamespace.xml");  
IEnumerable<XElement> names =  
    from el in purchaseOrders  
        .Elements(aw + "PurchaseOrder")  
        .Elements(aw + "Address")  
        .Elements(aw + "Name")  
    select el;  
foreach (XElement e in names)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="b4720-121">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b4720-121">This example produces the following output:</span></span>  
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b4720-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="b4720-122">See Also</span></span>  
 [<span data-ttu-id="b4720-123">Technologie LINQ to XML osy (C#)</span><span class="sxs-lookup"><span data-stu-id="b4720-123">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
