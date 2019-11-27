---
title: 'Postupy: zřetězení volání metod osy (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: e4e22942-39bd-460f-b3c0-9f09e53d3aa9
ms.openlocfilehash: de6fbec9fa7948c618252415774ff6a2e9289c74
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346939"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-visual-basic"></a><span data-ttu-id="1bd11-102">Postupy: zřetězení volání metod osy (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1bd11-102">How to: Chain Axis Method Calls (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="1bd11-103">Běžným vzorem, který použijete v kódu, je zavolat metodu osy a pak zavolat jednu z OS rozšiřujících metod.</span><span class="sxs-lookup"><span data-stu-id="1bd11-103">A common pattern that you will use in your code is to call an axis method, then call one of the extension method axes.</span></span>  
  
 <span data-ttu-id="1bd11-104">Existují dvě osy s názvem `Elements`, které vracejí kolekci prvků: metoda <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> a metoda <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1bd11-104">There are two axes with the name of `Elements` that return a collection of elements: the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method and the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="1bd11-105">Tyto dvě osy můžete kombinovat a vyhledat všechny prvky zadaného názvu v dané hloubce stromu.</span><span class="sxs-lookup"><span data-stu-id="1bd11-105">You can combine these two axes to find all elements of a specified name at a given depth in the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bd11-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="1bd11-106">Example</span></span>  
 <span data-ttu-id="1bd11-107">V tomto příkladu se používá <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> a <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> k nalezení všech prvků `Name` ve všech elementech `Address` ve všech `PurchaseOrder` prvcích.</span><span class="sxs-lookup"><span data-stu-id="1bd11-107">This example uses <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> and <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> to find all `Name` elements in all `Address` elements in all `PurchaseOrder` elements.</span></span>  
  
 <span data-ttu-id="1bd11-108">Tento příklad používá následující dokument XML: [ukázkový soubor XML: více nákupních objednávek (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1bd11-108">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim purchaseOrders As XElement = XElement.Load("PurchaseOrders.xml")  
Dim names As IEnumerable(Of XElement) = _  
    From el In purchaseOrders.<PurchaseOrder>.<Address>.<Name> _  
    Select el  
For Each e As XElement In names  
    Console.WriteLine(e)  
Next  
```  
  
 <span data-ttu-id="1bd11-109">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="1bd11-109">This example produces the following output:</span></span>  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 <span data-ttu-id="1bd11-110">Tato funkce funguje, protože jedna z implementací osy `Elements` je jako metoda rozšíření v <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="1bd11-110">This works because one of the implementations of the `Elements` axis is as an extension method on <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="1bd11-111"><xref:System.Xml.Linq.XElement> jsou odvozeny z <xref:System.Xml.Linq.XContainer>, takže můžete volat metodu <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> pro výsledky volání metody <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1bd11-111"><xref:System.Xml.Linq.XElement> derives from <xref:System.Xml.Linq.XContainer>, so you can call the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method on the results of a call to the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bd11-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="1bd11-112">Example</span></span>  
 <span data-ttu-id="1bd11-113">Někdy je vhodné načíst všechny prvky na konkrétní hloubku prvku, pokud může nebo nemusí být zasahovat do nadřazených prvků.</span><span class="sxs-lookup"><span data-stu-id="1bd11-113">Sometimes you want to retrieve all elements at a particular element depth when there might or might not be intervening ancestors.</span></span> <span data-ttu-id="1bd11-114">Například v následujícím dokumentu můžete chtít načíst všechny `ConfigParameter` prvky, které jsou podřízené prvku `Customer`, ale ne `ConfigParameter`, který je podřízenou položkou `Root` prvku.</span><span class="sxs-lookup"><span data-stu-id="1bd11-114">For example, in the following document, you might want to retrieve all the `ConfigParameter` elements that are children of the `Customer` element, but not the `ConfigParameter` that is a child of the `Root` element.</span></span>  
  
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
  
 <span data-ttu-id="1bd11-115">K tomu můžete použít <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> osu, a to následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="1bd11-115">To do this, you can use the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> axis, as follows:</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Irregular.xml")  
Dim configParameters As IEnumerable(Of XElement) = _  
    root.<Customer>.<Config>.<ConfigParameter>  
For Each cp As XElement In configParameters  
    Console.WriteLine(cp)  
Next  
```  
  
 <span data-ttu-id="1bd11-116">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="1bd11-116">This example produces the following output:</span></span>  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a><span data-ttu-id="1bd11-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="1bd11-117">Example</span></span>  
 <span data-ttu-id="1bd11-118">Následující příklad ukazuje stejnou techniku pro XML, která je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1bd11-118">The following example shows the same technique for XML that is in a namespace.</span></span> <span data-ttu-id="1bd11-119">Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1bd11-119">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="1bd11-120">Tento příklad používá následující dokument XML: [ukázkový soubor XML: více nákupních objednávek v oboru názvů](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="1bd11-120">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim purchaseOrders As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")  
        Dim names As IEnumerable(Of XElement) = _  
            From el In purchaseOrders.<aw:PurchaseOrder>.<aw:Address>.<aw:Name> _  
            Select el  
        For Each e As XElement In names  
            Console.WriteLine(e)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="1bd11-121">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="1bd11-121">This example produces the following output:</span></span>  
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1bd11-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1bd11-122">See also</span></span>

- [<span data-ttu-id="1bd11-123">LINQ to XML osy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1bd11-123">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
