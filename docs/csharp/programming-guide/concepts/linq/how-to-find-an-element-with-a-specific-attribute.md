---
title: Vyhledání elementu s konkrétním atributem (C#)
description: Naučte se najít element, který má atribut s konkrétní hodnotou. Podívejte se na příklady kódu a další zdroje informací.
ms.date: 07/20/2015
ms.assetid: b92591aa-3cfb-490e-99f6-da8de335e362
ms.openlocfilehash: 44875ca2104e7a8f83e83da983af49ef85c89f0a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303280"
---
# <a name="how-to-find-an-element-with-a-specific-attribute-c"></a><span data-ttu-id="8c7b1-104">Vyhledání elementu s konkrétním atributem (C#)</span><span class="sxs-lookup"><span data-stu-id="8c7b1-104">How to find an element with a specific attribute (C#)</span></span>
<span data-ttu-id="8c7b1-105">Toto téma ukazuje, jak najít element, který má atribut, který má konkrétní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8c7b1-105">This topic shows how to find an element that has an attribute that has a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c7b1-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="8c7b1-106">Example</span></span>  
 <span data-ttu-id="8c7b1-107">Příklad ukazuje, jak najít `Address` prvek, který má `Type` atribut s hodnotou "vyúčtování".</span><span class="sxs-lookup"><span data-stu-id="8c7b1-107">The example shows how to find the `Address` element that has a `Type` attribute with a value of "Billing".</span></span>  
  
 <span data-ttu-id="8c7b1-108">Tento příklad používá následující dokument XML: [vzorový soubor XML: typická nákupní objednávka (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="8c7b1-108">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> address =  
    from el in root.Elements("Address")  
    where (string)el.Attribute("Type") == "Billing"  
    select el;  
foreach (XElement el in address)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="8c7b1-109">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="8c7b1-109">This code produces the following output:</span></span>  
  
```xml  
<Address Type="Billing">  
  <Name>Tai Yee</Name>  
  <Street>8 Oak Avenue</Street>  
  <City>Old Town</City>  
  <State>PA</State>  
  <Zip>95819</Zip>  
  <Country>USA</Country>  
</Address>  
```  
  
## <a name="example"></a><span data-ttu-id="8c7b1-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="8c7b1-110">Example</span></span>  
 <span data-ttu-id="8c7b1-111">Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="8c7b1-111">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="8c7b1-112">Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8c7b1-112">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="8c7b1-113">Tento příklad používá následující dokument XML: [ukázkový soubor XML: typická nákupní objednávka v oboru názvů](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="8c7b1-113">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> address =  
    from el in root.Elements(aw + "Address")  
    where (string)el.Attribute(aw + "Type") == "Billing"  
    select el;  
foreach (XElement el in address)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="8c7b1-114">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="8c7b1-114">This code produces the following output:</span></span>  
  
```xml  
<aw:Address aw:Type="Billing" xmlns:aw="http://www.adventure-works.com">  
  <aw:Name>Tai Yee</aw:Name>  
  <aw:Street>8 Oak Avenue</aw:Street>  
  <aw:City>Old Town</aw:City>  
  <aw:State>PA</aw:State>  
  <aw:Zip>95819</aw:Zip>  
  <aw:Country>USA</aw:Country>  
</aw:Address>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8c7b1-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c7b1-115">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="8c7b1-116">Přehled standardních operátorů dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="8c7b1-116">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="8c7b1-117">Operace projekce (C#)</span><span class="sxs-lookup"><span data-stu-id="8c7b1-117">Projection Operations (C#)</span></span>](./projection-operations.md)
