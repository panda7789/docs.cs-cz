---
title: Jak načíst jeden podřízený prvek (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: 0e10cf230a73e6419f2d9c663766f9a24a0930af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347478"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a><span data-ttu-id="b843d-102">Jak načíst jeden podřízený prvek (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b843d-102">How to retrieve a single child element (LINQ to XML) (C#)</span></span>
<span data-ttu-id="b843d-103">Toto téma vysvětluje, jak načíst jeden podřízený prvek, zadaný název podřízeného prvku.</span><span class="sxs-lookup"><span data-stu-id="b843d-103">This topic explains how to retrieve a single child element, given the name of the child element.</span></span> <span data-ttu-id="b843d-104">Pokud znáte název podřízeného prvku a že existuje pouze jeden prvek, který má tento název, může být vhodné načíst pouze jeden prvek, namísto kolekce.</span><span class="sxs-lookup"><span data-stu-id="b843d-104">When you know the name of the child element and that there is only one element that has this name, it can be convenient to retrieve just one element, instead of a collection.</span></span>  
  
 <span data-ttu-id="b843d-105">Metoda <xref:System.Xml.Linq.XContainer.Element%2A> vrátí první <xref:System.Xml.Linq.XElement> podřízenou <xref:System.Xml.Linq.XName>položku se zadaným .</span><span class="sxs-lookup"><span data-stu-id="b843d-105">The <xref:System.Xml.Linq.XContainer.Element%2A> method returns the first child <xref:System.Xml.Linq.XElement> with the specified <xref:System.Xml.Linq.XName>.</span></span>  
  
 <span data-ttu-id="b843d-106">Pokud chcete načíst jeden podřízený prvek v jazyce Visual Basic, běžným přístupem je použití vlastnosti XML a potom načíst první prvek pomocí zápisu indexeru pole.</span><span class="sxs-lookup"><span data-stu-id="b843d-106">If you want to retrieve a single child element in Visual Basic, a common approach is to use the XML property, and then retrieve the first element using array indexer notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b843d-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="b843d-107">Example</span></span>  
 <span data-ttu-id="b843d-108">Následující příklad ukazuje použití <xref:System.Xml.Linq.XContainer.Element%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b843d-108">The following example demonstrates the use of the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="b843d-109">Tento příklad přebírá strom `po` XML s názvem `Comment`a vyhledá první pojmenovanou prvek .</span><span class="sxs-lookup"><span data-stu-id="b843d-109">This example takes the XML tree named `po` and finds the first element named `Comment`.</span></span>  
  
 <span data-ttu-id="b843d-110">Příklad jazyka ukazuje pomocí zápisu indexeru pole k načtení jednoho prvku.</span><span class="sxs-lookup"><span data-stu-id="b843d-110">The Visual Basic example shows using array indexer notation to retrieve a single element.</span></span>  
  
 <span data-ttu-id="b843d-111">Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Typický nákupní objednávka (LINQ to XML).](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)</span><span class="sxs-lookup"><span data-stu-id="b843d-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
XElement e = po.Element("DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="b843d-112">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b843d-112">This example produces the following output:</span></span>  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a><span data-ttu-id="b843d-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="b843d-113">Example</span></span>  
 <span data-ttu-id="b843d-114">Následující příklad ukazuje stejný kód pro JAZYK XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b843d-114">The following example shows the same code for XML that is in a namespace.</span></span> <span data-ttu-id="b843d-115">Další informace naleznete [v tématu Přehled oborů názvů (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b843d-115">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="b843d-116">Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Typická nákupní objednávka v oboru názvů](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="b843d-116">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement e = po.Element(aw + "DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="b843d-117">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b843d-117">This example produces the following output:</span></span>  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b843d-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="b843d-118">See also</span></span>

- [<span data-ttu-id="b843d-119">LINQ na osy XML (C#)</span><span class="sxs-lookup"><span data-stu-id="b843d-119">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
