---
title: 'Postupy: Načtení jednoho podřízeného elementu (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 0033e258-d9c4-4569-86f6-79b7c06d1204
ms.openlocfilehash: 52b626cfa7227312b1251a6fc998112268564084
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521917"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-visual-basic"></a><span data-ttu-id="160f4-102">Postupy: Načtení jednoho podřízeného elementu (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="160f4-102">How to: Retrieve a Single Child Element (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="160f4-103">Toto téma vysvětluje, jak načíst jeden podřízený prvek, název podřízeného prvku.</span><span class="sxs-lookup"><span data-stu-id="160f4-103">This topic explains how to retrieve a single child element, given the name of the child element.</span></span> <span data-ttu-id="160f4-104">Pokud znáte název podřízeného prvku a že je pouze jeden element, který má tento název, může být vhodné k načtení pouze jednoho prvku, namísto kolekce.</span><span class="sxs-lookup"><span data-stu-id="160f4-104">When you know the name of the child element and that there is only one element that has this name, it can be convenient to retrieve just one element, instead of a collection.</span></span>  
  
 <span data-ttu-id="160f4-105"><xref:System.Xml.Linq.XContainer.Element%2A> Metoda vrací prvního podřízeného <xref:System.Xml.Linq.XElement> se zadaným <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="160f4-105">The <xref:System.Xml.Linq.XContainer.Element%2A> method returns the first child <xref:System.Xml.Linq.XElement> with the specified <xref:System.Xml.Linq.XName>.</span></span>  
  
 <span data-ttu-id="160f4-106">Pokud chcete načíst jeden podřízený prvek v jazyce Visual Basic, běžným přístupem je použít vlastnost XML a pak načíst první prvek pomocí notace indexeru pole.</span><span class="sxs-lookup"><span data-stu-id="160f4-106">If you want to retrieve a single child element in Visual Basic, a common approach is to use the XML property, and then retrieve the first element using array indexer notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="160f4-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="160f4-107">Example</span></span>  
 <span data-ttu-id="160f4-108">Následující příklad ukazuje použití <xref:System.Xml.Linq.XContainer.Element%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="160f4-108">The following example demonstrates the use of the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="160f4-109">V tomto příkladu má stromové struktuře XML s názvem `po` a vyhledá první prvek s názvem `Comment`.</span><span class="sxs-lookup"><span data-stu-id="160f4-109">This example takes the XML tree named `po` and finds the first element named `Comment`.</span></span>  
  
 <span data-ttu-id="160f4-110">Příklad jazyka Visual Basic zobrazí notaci indexeru pro načtení jednoho elementu pole.</span><span class="sxs-lookup"><span data-stu-id="160f4-110">The Visual Basic example shows using array indexer notation to retrieve a single element.</span></span>  
  
 <span data-ttu-id="160f4-111">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Typická nákupní objednávka (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="160f4-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim e As XElement = po.<DeliveryNotes>(0)  
Console.WriteLine(e)  
```  
  
 <span data-ttu-id="160f4-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="160f4-112">This example produces the following output:</span></span>  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a><span data-ttu-id="160f4-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="160f4-113">Example</span></span>  
 <span data-ttu-id="160f4-114">Následující příklad ukazuje stejný kód pro soubor XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="160f4-114">The following example shows the same code for XML that is in a namespace.</span></span> <span data-ttu-id="160f4-115">Další informace najdete v tématu [práce s názvovými prostory XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="160f4-115">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="160f4-116">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Typická nákupní objednávka v Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="160f4-116">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim e As XElement = po.<aw:DeliveryNotes>(0)  
        Console.WriteLine(e)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="160f4-117">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="160f4-117">This example produces the following output:</span></span>  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="160f4-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="160f4-118">See also</span></span>
- [<span data-ttu-id="160f4-119">Osy LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="160f4-119">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
