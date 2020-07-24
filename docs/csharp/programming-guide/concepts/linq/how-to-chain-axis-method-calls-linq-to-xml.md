---
title: Postup řetězení volání metody osy (LINQ to XML) (C#)
description: Tyto LINQ to XML Příklady v jazyce C# ukazují volání dvou OS, aby bylo možné najít všechny prvky zadaného názvu v dané hloubkě stromu.
ms.date: 07/20/2015
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
ms.openlocfilehash: f26efd2ca918fd36916eb4f01462af70066219a0
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105390"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-c"></a><span data-ttu-id="9f9c8-103">Postup řetězení volání metody osy (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="9f9c8-103">How to chain axis method calls (LINQ to XML) (C#)</span></span>
<span data-ttu-id="9f9c8-104">Běžným vzorem, který použijete v kódu, je zavolat metodu osy a pak zavolat jednu z OS rozšiřujících metod.</span><span class="sxs-lookup"><span data-stu-id="9f9c8-104">A common pattern that you will use in your code is to call an axis method, then call one of the extension method axes.</span></span>  
  
 <span data-ttu-id="9f9c8-105">Existují dvě osy s názvem `Elements` , který vrací kolekci prvků: <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> Metoda a <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="9f9c8-105">There are two axes with the name of `Elements` that return a collection of elements: the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method and the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9f9c8-106">Tyto dvě osy můžete kombinovat a vyhledat všechny prvky zadaného názvu v dané hloubce stromu.</span><span class="sxs-lookup"><span data-stu-id="9f9c8-106">You can combine these two axes to find all elements of a specified name at a given depth in the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f9c8-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f9c8-107">Example</span></span>  
 <span data-ttu-id="9f9c8-108">Tento příklad používá <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> a <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> k nalezení všech prvků všech prvků ve `Name` `Address` všech `PurchaseOrder` prvcích.</span><span class="sxs-lookup"><span data-stu-id="9f9c8-108">This example uses <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> and <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> to find all `Name` elements in all `Address` elements in all `PurchaseOrder` elements.</span></span>  
  
 <span data-ttu-id="9f9c8-109">Tento příklad používá následující dokument XML: [ukázkový soubor XML: více nákupních objednávek (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9f9c8-109">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="9f9c8-110">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="9f9c8-110">This example produces the following output:</span></span>  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 <span data-ttu-id="9f9c8-111">To funguje, protože jedna z implementací `Elements` osy je jako metoda rozšíření na <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XContainer> .</span><span class="sxs-lookup"><span data-stu-id="9f9c8-111">This works because one of the implementations of the `Elements` axis is as an extension method on <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="9f9c8-112"><xref:System.Xml.Linq.XElement>je odvozen z <xref:System.Xml.Linq.XContainer> , takže můžete volat <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> metodu pro výsledky volání <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="9f9c8-112"><xref:System.Xml.Linq.XElement> derives from <xref:System.Xml.Linq.XContainer>, so you can call the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method on the results of a call to the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f9c8-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f9c8-113">Example</span></span>  
 <span data-ttu-id="9f9c8-114">Někdy je vhodné načíst všechny prvky na konkrétní hloubku prvku, pokud může nebo nemusí být zasahovat do nadřazených prvků.</span><span class="sxs-lookup"><span data-stu-id="9f9c8-114">Sometimes you want to retrieve all elements at a particular element depth when there might or might not be intervening ancestors.</span></span> <span data-ttu-id="9f9c8-115">Například v následujícím dokumentu můžete chtít načíst všechny `ConfigParameter` prvky, které jsou podřízené `Customer` prvku, ale nikoli `ConfigParameter` podřízený `Root` prvek elementu.</span><span class="sxs-lookup"><span data-stu-id="9f9c8-115">For example, in the following document, you might want to retrieve all the `ConfigParameter` elements that are children of the `Customer` element, but not the `ConfigParameter` that is a child of the `Root` element.</span></span>  
  
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
  
 <span data-ttu-id="9f9c8-116">K tomu můžete použít <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> osu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9f9c8-116">To do this, you can use the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> axis, as follows:</span></span>  
  
```csharp  
XElement root = XElement.Load("Irregular.xml");  
IEnumerable<XElement> configParameters =
    root.Elements("Customer").Elements("Config").  
    Elements("ConfigParameter");  
foreach (XElement cp in configParameters)  
    Console.WriteLine(cp);  
```  
  
 <span data-ttu-id="9f9c8-117">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="9f9c8-117">This example produces the following output:</span></span>  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a><span data-ttu-id="9f9c8-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f9c8-118">Example</span></span>  
 <span data-ttu-id="9f9c8-119">Následující příklad ukazuje stejnou techniku pro XML, která je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="9f9c8-119">The following example shows the same technique for XML that is in a namespace.</span></span> <span data-ttu-id="9f9c8-120">Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9f9c8-120">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="9f9c8-121">Tento příklad používá následující dokument XML: [ukázkový soubor XML: více nákupních objednávek v oboru názvů](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="9f9c8-121">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="9f9c8-122">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="9f9c8-122">This example produces the following output:</span></span>  
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9f9c8-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f9c8-123">See also</span></span>

- [<span data-ttu-id="9f9c8-124">LINQ to XML osy (C#)</span><span class="sxs-lookup"><span data-stu-id="9f9c8-124">LINQ to XML Axes (C#)</span></span>](linq-to-xml-axes-overview.md)
