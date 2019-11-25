---
title: 'How to: Retrieve a Single Child Element (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 0033e258-d9c4-4569-86f6-79b7c06d1204
ms.openlocfilehash: 2e89df700c505eca9d1c91634e4cce8594a1d599
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347547"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-visual-basic"></a><span data-ttu-id="bdfee-102">How to: Retrieve a Single Child Element (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bdfee-102">How to: Retrieve a Single Child Element (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="bdfee-103">This topic explains how to retrieve a single child element, given the name of the child element.</span><span class="sxs-lookup"><span data-stu-id="bdfee-103">This topic explains how to retrieve a single child element, given the name of the child element.</span></span> <span data-ttu-id="bdfee-104">When you know the name of the child element and that there is only one element that has this name, it can be convenient to retrieve just one element, instead of a collection.</span><span class="sxs-lookup"><span data-stu-id="bdfee-104">When you know the name of the child element and that there is only one element that has this name, it can be convenient to retrieve just one element, instead of a collection.</span></span>  
  
 <span data-ttu-id="bdfee-105">The <xref:System.Xml.Linq.XContainer.Element%2A> method returns the first child <xref:System.Xml.Linq.XElement> with the specified <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="bdfee-105">The <xref:System.Xml.Linq.XContainer.Element%2A> method returns the first child <xref:System.Xml.Linq.XElement> with the specified <xref:System.Xml.Linq.XName>.</span></span>  
  
 <span data-ttu-id="bdfee-106">If you want to retrieve a single child element in Visual Basic, a common approach is to use the XML property, and then retrieve the first element using array indexer notation.</span><span class="sxs-lookup"><span data-stu-id="bdfee-106">If you want to retrieve a single child element in Visual Basic, a common approach is to use the XML property, and then retrieve the first element using array indexer notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdfee-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="bdfee-107">Example</span></span>  
 <span data-ttu-id="bdfee-108">The following example demonstrates the use of the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span><span class="sxs-lookup"><span data-stu-id="bdfee-108">The following example demonstrates the use of the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="bdfee-109">This example takes the XML tree named `po` and finds the first element named `Comment`.</span><span class="sxs-lookup"><span data-stu-id="bdfee-109">This example takes the XML tree named `po` and finds the first element named `Comment`.</span></span>  
  
 <span data-ttu-id="bdfee-110">The Visual Basic example shows using array indexer notation to retrieve a single element.</span><span class="sxs-lookup"><span data-stu-id="bdfee-110">The Visual Basic example shows using array indexer notation to retrieve a single element.</span></span>  
  
 <span data-ttu-id="bdfee-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="bdfee-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim e As XElement = po.<DeliveryNotes>(0)  
Console.WriteLine(e)  
```  
  
 <span data-ttu-id="bdfee-112">This example produces the following output:</span><span class="sxs-lookup"><span data-stu-id="bdfee-112">This example produces the following output:</span></span>  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a><span data-ttu-id="bdfee-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="bdfee-113">Example</span></span>  
 <span data-ttu-id="bdfee-114">The following example shows the same code for XML that is in a namespace.</span><span class="sxs-lookup"><span data-stu-id="bdfee-114">The following example shows the same code for XML that is in a namespace.</span></span> <span data-ttu-id="bdfee-115">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="bdfee-115">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="bdfee-116">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="bdfee-116">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="bdfee-117">This example produces the following output:</span><span class="sxs-lookup"><span data-stu-id="bdfee-117">This example produces the following output:</span></span>  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bdfee-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bdfee-118">See also</span></span>

- [<span data-ttu-id="bdfee-119">LINQ to XML Axes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bdfee-119">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
