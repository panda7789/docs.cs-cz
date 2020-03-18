---
title: Jak zřetězit volání metod osy (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
ms.openlocfilehash: 56fa5c9e8358883d838b68e99664240aa97f347f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169464"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-c"></a><span data-ttu-id="7f812-102">Jak zřetězit volání metod osy (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="7f812-102">How to chain axis method calls (LINQ to XML) (C#)</span></span>
<span data-ttu-id="7f812-103">Běžný vzor, který budete používat v kódu je volání metody osy, pak volání jedné z os metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="7f812-103">A common pattern that you will use in your code is to call an axis method, then call one of the extension method axes.</span></span>  
  
 <span data-ttu-id="7f812-104">Existují dvě osy s `Elements` názvem, které vrátí <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> kolekci <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> prvků: metoda a metoda.</span><span class="sxs-lookup"><span data-stu-id="7f812-104">There are two axes with the name of `Elements` that return a collection of elements: the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method and the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7f812-105">Tyto dvě osy můžete zkombinovat a najít všechny prvky zadaného názvu v dané hloubce ve stromu.</span><span class="sxs-lookup"><span data-stu-id="7f812-105">You can combine these two axes to find all elements of a specified name at a given depth in the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f812-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="7f812-106">Example</span></span>  
 <span data-ttu-id="7f812-107">Tento příklad <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> používá a `Name` najít `Address` všechny prvky ve všech prvků ve všech `PurchaseOrder` prvků.</span><span class="sxs-lookup"><span data-stu-id="7f812-107">This example uses <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> and <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> to find all `Name` elements in all `Address` elements in all `PurchaseOrder` elements.</span></span>  
  
 <span data-ttu-id="7f812-108">Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Více nákupních objednávek (LINQ to XML).](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="7f812-108">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="7f812-109">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="7f812-109">This example produces the following output:</span></span>  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 <span data-ttu-id="7f812-110">To funguje, protože jedna z `Elements` implementací osy je jako metoda rozšíření na <xref:System.Collections.Generic.IEnumerable%601> . <xref:System.Xml.Linq.XContainer></span><span class="sxs-lookup"><span data-stu-id="7f812-110">This works because one of the implementations of the `Elements` axis is as an extension method on <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="7f812-111"><xref:System.Xml.Linq.XElement>odvozuje <xref:System.Xml.Linq.XContainer>z , takže <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> můžete volat metodu na <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> výsledky volání metody.</span><span class="sxs-lookup"><span data-stu-id="7f812-111"><xref:System.Xml.Linq.XElement> derives from <xref:System.Xml.Linq.XContainer>, so you can call the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method on the results of a call to the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f812-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="7f812-112">Example</span></span>  
 <span data-ttu-id="7f812-113">Někdy chcete načíst všechny prvky v určité hloubce prvku, když může nebo nemusí být zasahující předkové.</span><span class="sxs-lookup"><span data-stu-id="7f812-113">Sometimes you want to retrieve all elements at a particular element depth when there might or might not be intervening ancestors.</span></span> <span data-ttu-id="7f812-114">Například v následujícím dokumentu můžete chtít načíst `ConfigParameter` všechny prvky, `Customer` které jsou `ConfigParameter` podřízené prvku, `Root` ale ne, který je podřízený prvku.</span><span class="sxs-lookup"><span data-stu-id="7f812-114">For example, in the following document, you might want to retrieve all the `ConfigParameter` elements that are children of the `Customer` element, but not the `ConfigParameter` that is a child of the `Root` element.</span></span>  
  
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
  
 <span data-ttu-id="7f812-115">Chcete-li to provést, <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> můžete použít osu takto:</span><span class="sxs-lookup"><span data-stu-id="7f812-115">To do this, you can use the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> axis, as follows:</span></span>  
  
```csharp  
XElement root = XElement.Load("Irregular.xml");  
IEnumerable<XElement> configParameters =
    root.Elements("Customer").Elements("Config").  
    Elements("ConfigParameter");  
foreach (XElement cp in configParameters)  
    Console.WriteLine(cp);  
```  
  
 <span data-ttu-id="7f812-116">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="7f812-116">This example produces the following output:</span></span>  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a><span data-ttu-id="7f812-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="7f812-117">Example</span></span>  
 <span data-ttu-id="7f812-118">Následující příklad ukazuje stejnou techniku pro XML, která je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7f812-118">The following example shows the same technique for XML that is in a namespace.</span></span> <span data-ttu-id="7f812-119">Další informace naleznete [v tématu Přehled oborů názvů (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7f812-119">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="7f812-120">Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Více nákupních objednávek v oboru názvů](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="7f812-120">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="7f812-121">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="7f812-121">This example produces the following output:</span></span>  
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7f812-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f812-122">See also</span></span>

- [<span data-ttu-id="7f812-123">LINQ na osy XML (C#)</span><span class="sxs-lookup"><span data-stu-id="7f812-123">LINQ to XML Axes (C#)</span></span>](linq-to-xml-axes-overview.md)
