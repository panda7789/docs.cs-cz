---
title: 'Postupy: Zřetězení volání metod osy (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
ms.openlocfilehash: 39113c1b96ea7376d61c606aaa5f79715dbe3cab
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485918"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-c"></a><span data-ttu-id="edc74-102">Postupy: Zřetězení volání metod osy (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="edc74-102">How to: Chain Axis Method Calls (LINQ to XML) (C#)</span></span>
<span data-ttu-id="edc74-103">Běžným vzorem, který budete používat ve vašem kódu je volání metodu osy, následná volání, jeden z OS – metoda rozšíření.</span><span class="sxs-lookup"><span data-stu-id="edc74-103">A common pattern that you will use in your code is to call an axis method, then call one of the extension method axes.</span></span>  
  
 <span data-ttu-id="edc74-104">Existují dvě osy názvem `Elements` , které vracejí kolekci elementů: <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> metoda a <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="edc74-104">There are two axes with the name of `Elements` that return a collection of elements: the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method and the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="edc74-105">Tyto dvě osy najít všechny prvky zadaný název daného hloubce ve stromové struktuře můžete kombinovat.</span><span class="sxs-lookup"><span data-stu-id="edc74-105">You can combine these two axes to find all elements of a specified name at a given depth in the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="edc74-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="edc74-106">Example</span></span>  
 <span data-ttu-id="edc74-107">Tento příklad používá <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> a <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> k nalezení všech `Name` elementy ve všech `Address` elementy ve všech `PurchaseOrder` elementy.</span><span class="sxs-lookup"><span data-stu-id="edc74-107">This example uses <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> and <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> to find all `Name` elements in all `Address` elements in all `PurchaseOrder` elements.</span></span>  
  
 <span data-ttu-id="edc74-108">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Více nákupních objednávek (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="edc74-108">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="edc74-109">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="edc74-109">This example produces the following output:</span></span>  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 <span data-ttu-id="edc74-110">Tento postup funguje, protože jeden z implementace `Elements` osy je jako metodu rozšíření na <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="edc74-110">This works because one of the implementations of the `Elements` axis is as an extension method on <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="edc74-111"><xref:System.Xml.Linq.XElement> je odvozen od <xref:System.Xml.Linq.XContainer>, takže můžete volat <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> metodu na výsledky volání <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="edc74-111"><xref:System.Xml.Linq.XElement> derives from <xref:System.Xml.Linq.XContainer>, so you can call the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method on the results of a call to the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="edc74-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="edc74-112">Example</span></span>  
 <span data-ttu-id="edc74-113">Někdy budete chtít získat všechny prvky v hloubce konkrétní element když existuje může nebo nemusí být použité předchůdce.</span><span class="sxs-lookup"><span data-stu-id="edc74-113">Sometimes you want to retrieve all elements at a particular element depth when there might or might not be intervening ancestors.</span></span> <span data-ttu-id="edc74-114">Například v následujícím dokumentu, můžete chtít načíst všechny `ConfigParameter` prvky, které jsou podřízené objekty daného `Customer` elementu, ale ne `ConfigParameter` , který je podřízený `Root` elementu.</span><span class="sxs-lookup"><span data-stu-id="edc74-114">For example, in the following document, you might want to retrieve all the `ConfigParameter` elements that are children of the `Customer` element, but not the `ConfigParameter` that is a child of the `Root` element.</span></span>  
  
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
  
 <span data-ttu-id="edc74-115">K tomuto účelu můžete použít <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> osy, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="edc74-115">To do this, you can use the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> axis, as follows:</span></span>  
  
```csharp  
XElement root = XElement.Load("Irregular.xml");  
IEnumerable<XElement> configParameters =   
    root.Elements("Customer").Elements("Config").  
    Elements("ConfigParameter");  
foreach (XElement cp in configParameters)  
    Console.WriteLine(cp);  
```  
  
 <span data-ttu-id="edc74-116">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="edc74-116">This example produces the following output:</span></span>  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a><span data-ttu-id="edc74-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="edc74-117">Example</span></span>  
 <span data-ttu-id="edc74-118">Následující příklad ukazuje stejný postup pro soubor XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="edc74-118">The following example shows the same technique for XML that is in a namespace.</span></span> <span data-ttu-id="edc74-119">Další informace najdete v tématu [práce s názvovými prostory XML (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="edc74-119">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="edc74-120">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Více nákupních objednávek v Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="edc74-120">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="edc74-121">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="edc74-121">This example produces the following output:</span></span>  
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="edc74-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="edc74-122">See also</span></span>

- [<span data-ttu-id="edc74-123">Osy LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="edc74-123">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
