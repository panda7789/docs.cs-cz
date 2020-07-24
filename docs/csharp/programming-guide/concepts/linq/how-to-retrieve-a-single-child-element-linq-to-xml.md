---
title: Jak načíst jeden podřízený element (LINQ to XML) (C#)
description: Naučte se, jak pomocí LINQ to XML načíst jeden podřízený prvek podle názvu. V tomto příkladu jazyka C# vrací metoda elementu první zadaný podřízený element.
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: c3a044f30cf2e411bdff52586c7a370b626f41bc
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103280"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a><span data-ttu-id="de208-104">Jak načíst jeden podřízený element (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="de208-104">How to retrieve a single child element (LINQ to XML) (C#)</span></span>
<span data-ttu-id="de208-105">Toto téma vysvětluje, jak načíst jeden podřízený prvek s názvem podřízeného prvku.</span><span class="sxs-lookup"><span data-stu-id="de208-105">This topic explains how to retrieve a single child element, given the name of the child element.</span></span> <span data-ttu-id="de208-106">Pokud znáte název podřízeného prvku a že existuje pouze jeden prvek, který má tento název, může být vhodné načíst pouze jeden prvek namísto kolekce.</span><span class="sxs-lookup"><span data-stu-id="de208-106">When you know the name of the child element and that there is only one element that has this name, it can be convenient to retrieve just one element, instead of a collection.</span></span>  
  
 <span data-ttu-id="de208-107"><xref:System.Xml.Linq.XContainer.Element%2A>Metoda vrací první podřízenou položku <xref:System.Xml.Linq.XElement> se zadaným parametrem <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="de208-107">The <xref:System.Xml.Linq.XContainer.Element%2A> method returns the first child <xref:System.Xml.Linq.XElement> with the specified <xref:System.Xml.Linq.XName>.</span></span>  
  
 <span data-ttu-id="de208-108">Pokud chcete načíst jeden podřízený prvek v Visual Basic, společný přístup je použít vlastnost XML a poté načíst první prvek pomocí notace Array indexer.</span><span class="sxs-lookup"><span data-stu-id="de208-108">If you want to retrieve a single child element in Visual Basic, a common approach is to use the XML property, and then retrieve the first element using array indexer notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de208-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="de208-109">Example</span></span>  
 <span data-ttu-id="de208-110">Následující příklad ukazuje použití <xref:System.Xml.Linq.XContainer.Element%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="de208-110">The following example demonstrates the use of the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="de208-111">Tento příklad převezme strom XML s názvem `po` a vyhledá první prvek s názvem `Comment` .</span><span class="sxs-lookup"><span data-stu-id="de208-111">This example takes the XML tree named `po` and finds the first element named `Comment`.</span></span>  
  
 <span data-ttu-id="de208-112">Visual Basic příklad ukazuje použití notace indexeru pole k načtení jednoho prvku.</span><span class="sxs-lookup"><span data-stu-id="de208-112">The Visual Basic example shows using array indexer notation to retrieve a single element.</span></span>  
  
 <span data-ttu-id="de208-113">Tento příklad používá následující dokument XML: [vzorový soubor XML: typická nákupní objednávka (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="de208-113">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
XElement e = po.Element("DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="de208-114">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="de208-114">This example produces the following output:</span></span>  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a><span data-ttu-id="de208-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="de208-115">Example</span></span>  
 <span data-ttu-id="de208-116">Následující příklad ukazuje stejný kód pro XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="de208-116">The following example shows the same code for XML that is in a namespace.</span></span> <span data-ttu-id="de208-117">Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="de208-117">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="de208-118">Tento příklad používá následující dokument XML: [ukázkový soubor XML: typická nákupní objednávka v oboru názvů](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="de208-118">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement e = po.Element(aw + "DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="de208-119">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="de208-119">This example produces the following output:</span></span>  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="de208-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="de208-120">See also</span></span>

- [<span data-ttu-id="de208-121">LINQ to XML osy (C#)</span><span class="sxs-lookup"><span data-stu-id="de208-121">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
