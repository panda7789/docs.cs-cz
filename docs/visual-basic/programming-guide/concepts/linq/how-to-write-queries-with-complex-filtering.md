---
title: "Postupy: zápis dotazů s komplexní filtrování (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf286ffc-7990-4b00-a4eb-ee3d70129950
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 15ed0dcf87ad05b1da984aca494d28c1b19eb685
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-queries-with-complex-filtering-visual-basic"></a><span data-ttu-id="48071-102">Postupy: zápis dotazů s komplexní filtrování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48071-102">How to: Write Queries with Complex Filtering (Visual Basic)</span></span>
<span data-ttu-id="48071-103">Někdy budete chtít zapisovat XML dotazů LINQ s komplexní filtry.</span><span class="sxs-lookup"><span data-stu-id="48071-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="48071-104">Například můžete chtít najít všechny elementy, které mají podřízený element s určitým názvem a hodnotou.</span><span class="sxs-lookup"><span data-stu-id="48071-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="48071-105">Toto téma poskytuje příklad zápisu dotaz s komplexní filtrování.</span><span class="sxs-lookup"><span data-stu-id="48071-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48071-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="48071-106">Example</span></span>  
 <span data-ttu-id="48071-107">Tento příklad ukazuje, jak najít všechny `PurchaseOrder` prvky, které podřízený `Address` element, který má `Type` atribut rovno "Přesouvání" a podřízená `State` element rovno "NY".</span><span class="sxs-lookup"><span data-stu-id="48071-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="48071-108">Používá vnořený dotaz v `Where` klauzuli a `Any` vrátí operátor `True` Pokud kolekce obsahuje všechny elementy v ní.</span><span class="sxs-lookup"><span data-stu-id="48071-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `True` if the collection has any elements in it.</span></span>  
  
 <span data-ttu-id="48071-109">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: více nákupních objednávek (technologie LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="48071-109">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="48071-110">Další informace o `Any` operátor, najdete v části [operace kvantifikátoru (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).</span><span class="sxs-lookup"><span data-stu-id="48071-110">For more information about the `Any` operator, see [Quantifier Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).</span></span>  
  
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
  
 <span data-ttu-id="48071-111">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="48071-111">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="48071-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="48071-112">Example</span></span>  
 <span data-ttu-id="48071-113">Následující příklad ukazuje stejný dotaz pro formát XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="48071-113">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="48071-114">Další informace najdete v tématu [práci s obory názvů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="48071-114">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="48071-115">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: více nákupních objednávek v Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="48071-115">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="48071-116">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="48071-116">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="48071-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="48071-117">See Also</span></span>  
 <xref:System.Xml.Linq.XElement.Attribute%2A>  
 <xref:System.Xml.Linq.XContainer.Elements%2A>  
 [<span data-ttu-id="48071-118">Základní dotazy (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48071-118">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)  
 [<span data-ttu-id="48071-119">Vlastnost osy podřízeného souboru XML</span><span class="sxs-lookup"><span data-stu-id="48071-119">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [<span data-ttu-id="48071-120">Vlastnost osy atributu XML</span><span class="sxs-lookup"><span data-stu-id="48071-120">XML Attribute Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)  
 [<span data-ttu-id="48071-121">Vlastnost hodnoty XML</span><span class="sxs-lookup"><span data-stu-id="48071-121">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)  
 [<span data-ttu-id="48071-122">Operace projekce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48071-122">Projection Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)  
 [<span data-ttu-id="48071-123">Operace kvantifikátoru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48071-123">Quantifier Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)
