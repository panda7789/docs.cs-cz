---
title: 'Postupy: Vytváření dotazů s komplexním filtrováním (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: bf286ffc-7990-4b00-a4eb-ee3d70129950
ms.openlocfilehash: ac58394619b83e2b862e87926f0b6a722fdc3c7e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61614841"
---
# <a name="how-to-write-queries-with-complex-filtering-visual-basic"></a><span data-ttu-id="b373b-102">Postupy: Vytváření dotazů s komplexním filtrováním (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b373b-102">How to: Write Queries with Complex Filtering (Visual Basic)</span></span>
<span data-ttu-id="b373b-103">Někdy budete chtít napsat LINQ dotazy XML se složitějšími filtry.</span><span class="sxs-lookup"><span data-stu-id="b373b-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="b373b-104">Například budete muset najít všechny elementy, které mají podřízený element s určitým názvem a hodnotou.</span><span class="sxs-lookup"><span data-stu-id="b373b-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="b373b-105">V tomto tématu poskytuje příklad zápisu dotazů s komplexním filtrováním.</span><span class="sxs-lookup"><span data-stu-id="b373b-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b373b-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="b373b-106">Example</span></span>  
 <span data-ttu-id="b373b-107">Tento příklad ukazuje, jak najít všechny `PurchaseOrder` prvky, které mají podřízený `Address` element, který má `Type` atribut rovná "Přesouvání" a podřízená `State` prvek s hodnotou "USA".</span><span class="sxs-lookup"><span data-stu-id="b373b-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="b373b-108">Používá vnořené dotaz v `Where` klauzule a `Any` operátor vrátí `True` Pokud kolekce obsahuje všechny prvky v ní.</span><span class="sxs-lookup"><span data-stu-id="b373b-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `True` if the collection has any elements in it.</span></span>  
  
 <span data-ttu-id="b373b-109">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Více nákupních objednávek (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b373b-109">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="b373b-110">Další informace o `Any` operátoru, naleznete v tématu [operace kvantifikátoru (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).</span><span class="sxs-lookup"><span data-stu-id="b373b-110">For more information about the `Any` operator, see [Quantifier Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).</span></span>  
  
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
  
 <span data-ttu-id="b373b-111">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b373b-111">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="b373b-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="b373b-112">Example</span></span>  
 <span data-ttu-id="b373b-113">Následující příklad ukazuje stejný dotaz pro soubor XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b373b-113">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="b373b-114">Další informace najdete v tématu [práce s názvovými prostory XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="b373b-114">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="b373b-115">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Více nákupních objednávek v Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="b373b-115">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="b373b-116">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b373b-116">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="b373b-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b373b-117">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="b373b-118">Základní dotazy (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b373b-118">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [<span data-ttu-id="b373b-119">Vlastnost osy podřízeného XML</span><span class="sxs-lookup"><span data-stu-id="b373b-119">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="b373b-120">Vlastnost osy atributu XML</span><span class="sxs-lookup"><span data-stu-id="b373b-120">XML Attribute Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
- [<span data-ttu-id="b373b-121">Vlastnost hodnoty XML</span><span class="sxs-lookup"><span data-stu-id="b373b-121">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="b373b-122">Operace projekce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b373b-122">Projection Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
- [<span data-ttu-id="b373b-123">Operace kvantifikátoru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b373b-123">Quantifier Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)
