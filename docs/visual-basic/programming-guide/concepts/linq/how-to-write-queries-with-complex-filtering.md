---
title: 'Postupy: Vytváření dotazů s komplexním filtrováním'
ms.date: 07/20/2015
ms.assetid: bf286ffc-7990-4b00-a4eb-ee3d70129950
ms.openlocfilehash: 18ed4379b7ec9c8007cc3c189fc45571b5161911
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397619"
---
# <a name="how-to-write-queries-with-complex-filtering-visual-basic"></a><span data-ttu-id="7e243-102">Postupy: zápis dotazů se složitým filtrováním (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e243-102">How to: Write Queries with Complex Filtering (Visual Basic)</span></span>
<span data-ttu-id="7e243-103">Někdy budete chtít zapisovat LINQ to XML dotazy se složitými filtry.</span><span class="sxs-lookup"><span data-stu-id="7e243-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="7e243-104">Například může být nutné najít všechny prvky, které mají podřízený element s určitým názvem a hodnotou.</span><span class="sxs-lookup"><span data-stu-id="7e243-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="7e243-105">Toto téma poskytuje příklad zápisu dotazu se složitým filtrováním.</span><span class="sxs-lookup"><span data-stu-id="7e243-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e243-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="7e243-106">Example</span></span>  
 <span data-ttu-id="7e243-107">Tento příklad ukazuje, jak najít všechny `PurchaseOrder` prvky, které mají podřízený `Address` element, který má `Type` atribut se rovná "dodávání" a podřízený `State` element se rovná "ny".</span><span class="sxs-lookup"><span data-stu-id="7e243-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="7e243-108">Používá vnořený dotaz v `Where` klauzuli a `Any` operátor vrátí, `True` Pokud má kolekce nějaké prvky.</span><span class="sxs-lookup"><span data-stu-id="7e243-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `True` if the collection has any elements in it.</span></span>  
  
 <span data-ttu-id="7e243-109">Tento příklad používá následující dokument XML: [ukázkový soubor XML: více nákupních objednávek (LINQ to XML)](sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7e243-109">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="7e243-110">Další informace o `Any` operátoru naleznete v tématu [operace kvantifikátoru (Visual Basic)](quantifier-operations.md).</span><span class="sxs-lookup"><span data-stu-id="7e243-110">For more information about the `Any` operator, see [Quantifier Operations (Visual Basic)](quantifier-operations.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("PurchaseOrders.xml")  
Dim purchaseOrders As IEnumerable(Of XElement) = _  
    From el In root.<PurchaseOrder> _  
    Where _  
        (From add In el.<Address> _  
        Where _  
             add.@Type = "Shipping" And _  
             add.<State>.Value = "NY" _  
        Select add) _  
    .Any() _  
    Select el  
For Each el As XElement In purchaseOrders  
    Console.WriteLine(el.@PurchaseOrderNumber)  
Next  
```  
  
 <span data-ttu-id="7e243-111">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="7e243-111">This code produces the following output:</span></span>  
  
```console  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="7e243-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="7e243-112">Example</span></span>  
 <span data-ttu-id="7e243-113">Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7e243-113">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="7e243-114">Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7e243-114">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="7e243-115">Tento příklad používá následující dokument XML: [ukázkový soubor XML: více nákupních objednávek v oboru názvů](sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="7e243-115">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")  
        Dim purchaseOrders As IEnumerable(Of XElement) = _  
            From el In root.<aw:PurchaseOrder> _  
            Where _  
                (From add In el.<aw:Address> _  
                Where _  
                     add.@aw:Type = "Shipping" And _  
                     add.<aw:State>.Value = "NY" _  
                Select add) _  
            .Any() _  
            Select el  
        For Each el As XElement In purchaseOrders  
            Console.WriteLine(el.@aw:PurchaseOrderNumber)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="7e243-116">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="7e243-116">This code produces the following output:</span></span>  
  
```console  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="7e243-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e243-117">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="7e243-118">Základní dotazy (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e243-118">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](basic-queries-linq-to-xml.md)
- [<span data-ttu-id="7e243-119">Vlastnost osy podřízeného XML</span><span class="sxs-lookup"><span data-stu-id="7e243-119">XML Child Axis Property</span></span>](../../../language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="7e243-120">Vlastnost osy atributu XML</span><span class="sxs-lookup"><span data-stu-id="7e243-120">XML Attribute Axis Property</span></span>](../../../language-reference/xml-axis/xml-attribute-axis-property.md)
- [<span data-ttu-id="7e243-121">Vlastnost hodnoty XML</span><span class="sxs-lookup"><span data-stu-id="7e243-121">XML Value Property</span></span>](../../../language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="7e243-122">Operace projekce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e243-122">Projection Operations (Visual Basic)</span></span>](projection-operations.md)
- [<span data-ttu-id="7e243-123">Operace kvantifikátoru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e243-123">Quantifier Operations (Visual Basic)</span></span>](quantifier-operations.md)
