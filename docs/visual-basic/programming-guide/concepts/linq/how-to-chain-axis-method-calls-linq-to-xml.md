---
title: 'Postupy: Zřetězení volání metod osy (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: e4e22942-39bd-460f-b3c0-9f09e53d3aa9
ms.openlocfilehash: 2b74bcd9b9b61ddbfddcdbdf4c48af6b2fbd68a2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61855267"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-visual-basic"></a><span data-ttu-id="c6b39-102">Postupy: Zřetězení volání metod osy (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6b39-102">How to: Chain Axis Method Calls (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="c6b39-103">Běžným vzorem, který budete používat ve vašem kódu je volání metodu osy, následná volání, jeden z OS – metoda rozšíření.</span><span class="sxs-lookup"><span data-stu-id="c6b39-103">A common pattern that you will use in your code is to call an axis method, then call one of the extension method axes.</span></span>  
  
 <span data-ttu-id="c6b39-104">Existují dvě osy názvem `Elements` , které vracejí kolekci elementů: <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> metoda a <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="c6b39-104">There are two axes with the name of `Elements` that return a collection of elements: the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method and the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c6b39-105">Tyto dvě osy najít všechny prvky zadaný název daného hloubce ve stromové struktuře můžete kombinovat.</span><span class="sxs-lookup"><span data-stu-id="c6b39-105">You can combine these two axes to find all elements of a specified name at a given depth in the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6b39-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="c6b39-106">Example</span></span>  
 <span data-ttu-id="c6b39-107">Tento příklad používá <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> a <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> k nalezení všech `Name` elementy ve všech `Address` elementy ve všech `PurchaseOrder` elementy.</span><span class="sxs-lookup"><span data-stu-id="c6b39-107">This example uses <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> and <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> to find all `Name` elements in all `Address` elements in all `PurchaseOrder` elements.</span></span>  
  
 <span data-ttu-id="c6b39-108">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Více nákupních objednávek (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c6b39-108">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim purchaseOrders As XElement = XElement.Load("PurchaseOrders.xml")  
Dim names As IEnumerable(Of XElement) = _  
    From el In purchaseOrders.<PurchaseOrder>.<Address>.<Name> _  
    Select el  
For Each e As XElement In names  
    Console.WriteLine(e)  
Next  
```  
  
 <span data-ttu-id="c6b39-109">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c6b39-109">This example produces the following output:</span></span>  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 <span data-ttu-id="c6b39-110">Tento postup funguje, protože jeden z implementace `Elements` osy je jako metodu rozšíření na <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="c6b39-110">This works because one of the implementations of the `Elements` axis is as an extension method on <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="c6b39-111"><xref:System.Xml.Linq.XElement> je odvozen od <xref:System.Xml.Linq.XContainer>, takže můžete volat <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> metodu na výsledky volání <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="c6b39-111"><xref:System.Xml.Linq.XElement> derives from <xref:System.Xml.Linq.XContainer>, so you can call the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method on the results of a call to the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6b39-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="c6b39-112">Example</span></span>  
 <span data-ttu-id="c6b39-113">Někdy budete chtít získat všechny prvky v hloubce konkrétní element když existuje může nebo nemusí být použité předchůdce.</span><span class="sxs-lookup"><span data-stu-id="c6b39-113">Sometimes you want to retrieve all elements at a particular element depth when there might or might not be intervening ancestors.</span></span> <span data-ttu-id="c6b39-114">Například v následujícím dokumentu, můžete chtít načíst všechny `ConfigParameter` prvky, které jsou podřízené objekty daného `Customer` elementu, ale ne `ConfigParameter` , který je podřízený `Root` elementu.</span><span class="sxs-lookup"><span data-stu-id="c6b39-114">For example, in the following document, you might want to retrieve all the `ConfigParameter` elements that are children of the `Customer` element, but not the `ConfigParameter` that is a child of the `Root` element.</span></span>  
  
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
  
 <span data-ttu-id="c6b39-115">K tomuto účelu můžete použít <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> osy, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="c6b39-115">To do this, you can use the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> axis, as follows:</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Irregular.xml")  
Dim configParameters As IEnumerable(Of XElement) = _  
    root.<Customer>.<Config>.<ConfigParameter>  
For Each cp As XElement In configParameters  
    Console.WriteLine(cp)  
Next  
```  
  
 <span data-ttu-id="c6b39-116">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c6b39-116">This example produces the following output:</span></span>  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a><span data-ttu-id="c6b39-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="c6b39-117">Example</span></span>  
 <span data-ttu-id="c6b39-118">Následující příklad ukazuje stejný postup pro soubor XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c6b39-118">The following example shows the same technique for XML that is in a namespace.</span></span> <span data-ttu-id="c6b39-119">Další informace najdete v tématu [práce s názvovými prostory XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="c6b39-119">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="c6b39-120">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Více nákupních objednávek v Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="c6b39-120">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="c6b39-121">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c6b39-121">This example produces the following output:</span></span>  
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c6b39-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6b39-122">See also</span></span>

- [<span data-ttu-id="c6b39-123">Osy LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6b39-123">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
