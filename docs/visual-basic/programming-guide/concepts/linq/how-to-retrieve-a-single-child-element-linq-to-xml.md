---
title: 'Postupy: Načtení jednoho podřízeného elementu (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 0033e258-d9c4-4569-86f6-79b7c06d1204
ms.openlocfilehash: ab28ddd960374b22f44ac0c8fc7bddfe0608b8c5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397840"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-visual-basic"></a><span data-ttu-id="4731a-102">Postupy: načtení jednoho podřízeného elementu (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4731a-102">How to: Retrieve a Single Child Element (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="4731a-103">Toto téma vysvětluje, jak načíst jeden podřízený prvek s názvem podřízeného prvku.</span><span class="sxs-lookup"><span data-stu-id="4731a-103">This topic explains how to retrieve a single child element, given the name of the child element.</span></span> <span data-ttu-id="4731a-104">Pokud znáte název podřízeného prvku a že existuje pouze jeden prvek, který má tento název, může být vhodné načíst pouze jeden prvek namísto kolekce.</span><span class="sxs-lookup"><span data-stu-id="4731a-104">When you know the name of the child element and that there is only one element that has this name, it can be convenient to retrieve just one element, instead of a collection.</span></span>  
  
 <span data-ttu-id="4731a-105"><xref:System.Xml.Linq.XContainer.Element%2A>Metoda vrací první podřízenou položku <xref:System.Xml.Linq.XElement> se zadaným parametrem <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="4731a-105">The <xref:System.Xml.Linq.XContainer.Element%2A> method returns the first child <xref:System.Xml.Linq.XElement> with the specified <xref:System.Xml.Linq.XName>.</span></span>  
  
 <span data-ttu-id="4731a-106">Pokud chcete načíst jeden podřízený prvek v Visual Basic, společný přístup je použít vlastnost XML a poté načíst první prvek pomocí notace Array indexer.</span><span class="sxs-lookup"><span data-stu-id="4731a-106">If you want to retrieve a single child element in Visual Basic, a common approach is to use the XML property, and then retrieve the first element using array indexer notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4731a-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="4731a-107">Example</span></span>  
 <span data-ttu-id="4731a-108">Následující příklad ukazuje použití <xref:System.Xml.Linq.XContainer.Element%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4731a-108">The following example demonstrates the use of the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="4731a-109">Tento příklad převezme strom XML s názvem `po` a vyhledá první prvek s názvem `Comment` .</span><span class="sxs-lookup"><span data-stu-id="4731a-109">This example takes the XML tree named `po` and finds the first element named `Comment`.</span></span>  
  
 <span data-ttu-id="4731a-110">Visual Basic příklad ukazuje použití notace indexeru pole k načtení jednoho prvku.</span><span class="sxs-lookup"><span data-stu-id="4731a-110">The Visual Basic example shows using array indexer notation to retrieve a single element.</span></span>  
  
 <span data-ttu-id="4731a-111">Tento příklad používá následující dokument XML: [vzorový soubor XML: typická nákupní objednávka (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4731a-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim e As XElement = po.<DeliveryNotes>(0)  
Console.WriteLine(e)  
```  
  
 <span data-ttu-id="4731a-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="4731a-112">This example produces the following output:</span></span>  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a><span data-ttu-id="4731a-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="4731a-113">Example</span></span>  
 <span data-ttu-id="4731a-114">Následující příklad ukazuje stejný kód pro XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4731a-114">The following example shows the same code for XML that is in a namespace.</span></span> <span data-ttu-id="4731a-115">Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4731a-115">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="4731a-116">Tento příklad používá následující dokument XML: [ukázkový soubor XML: typická nákupní objednávka v oboru názvů](sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="4731a-116">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="4731a-117">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="4731a-117">This example produces the following output:</span></span>  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4731a-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="4731a-118">See also</span></span>

- [<span data-ttu-id="4731a-119">LINQ to XML osy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4731a-119">LINQ to XML Axes (Visual Basic)</span></span>](linq-to-xml-axes.md)
