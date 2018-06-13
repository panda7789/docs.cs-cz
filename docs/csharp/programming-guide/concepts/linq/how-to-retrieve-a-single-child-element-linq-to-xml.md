---
title: 'Postupy: načtení jeden podřízený Element (technologie LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: 664b9496c8411055fcd09a1ea0709cdfdae79524
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33321334"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a><span data-ttu-id="44955-102">Postupy: načtení jeden podřízený Element (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="44955-102">How to: Retrieve a Single Child Element (LINQ to XML) (C#)</span></span>
<span data-ttu-id="44955-103">Toto téma vysvětluje, jak načíst jeden podřízený element zadaný název podřízeného prvku.</span><span class="sxs-lookup"><span data-stu-id="44955-103">This topic explains how to retrieve a single child element, given the name of the child element.</span></span> <span data-ttu-id="44955-104">Pokud znáte název podřízeného elementu, a že je pouze jeden element, který má tento název, může být vhodnější načíst pouze jeden prvek místo kolekce.</span><span class="sxs-lookup"><span data-stu-id="44955-104">When you know the name of the child element and that there is only one element that has this name, it can be convenient to retrieve just one element, instead of a collection.</span></span>  
  
 <span data-ttu-id="44955-105"><xref:System.Xml.Linq.XContainer.Element%2A> Metoda vrací prvního podřízeného <xref:System.Xml.Linq.XElement> se zadaným <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="44955-105">The <xref:System.Xml.Linq.XContainer.Element%2A> method returns the first child <xref:System.Xml.Linq.XElement> with the specified <xref:System.Xml.Linq.XName>.</span></span>  
  
 <span data-ttu-id="44955-106">Pokud chcete načíst jeden podřízený element v jazyku Visual Basic, je běžný postup použijte vlastnost XML a následně načíst první prvek notaci indexer pole.</span><span class="sxs-lookup"><span data-stu-id="44955-106">If you want to retrieve a single child element in Visual Basic, a common approach is to use the XML property, and then retrieve the first element using array indexer notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44955-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="44955-107">Example</span></span>  
 <span data-ttu-id="44955-108">Následující příklad ukazuje použití <xref:System.Xml.Linq.XContainer.Element%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="44955-108">The following example demonstrates the use of the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="44955-109">Tento příklad trvá stromu XML s názvem `po` a vyhledá první prvek s názvem `Comment`.</span><span class="sxs-lookup"><span data-stu-id="44955-109">This example takes the XML tree named `po` and finds the first element named `Comment`.</span></span>  
  
 <span data-ttu-id="44955-110">Visual Basic příklad ukazuje, notaci indexer pole načíst jediným elementem.</span><span class="sxs-lookup"><span data-stu-id="44955-110">The Visual Basic example shows using array indexer notation to retrieve a single element.</span></span>  
  
 <span data-ttu-id="44955-111">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: typické nákupní objednávka (technologie LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="44955-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
XElement e = po.Element("DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="44955-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="44955-112">This example produces the following output:</span></span>  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a><span data-ttu-id="44955-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="44955-113">Example</span></span>  
 <span data-ttu-id="44955-114">Následující příklad ukazuje stejný kód pro formát XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="44955-114">The following example shows the same code for XML that is in a namespace.</span></span> <span data-ttu-id="44955-115">Další informace najdete v tématu [práci s obory názvů XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="44955-115">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="44955-116">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: typické nákupní objednávka v Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="44955-116">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement e = po.Element(aw + "DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="44955-117">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="44955-117">This example produces the following output:</span></span>  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="44955-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="44955-118">See Also</span></span>  
 [<span data-ttu-id="44955-119">Technologie LINQ to XML osy (C#)</span><span class="sxs-lookup"><span data-stu-id="44955-119">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
