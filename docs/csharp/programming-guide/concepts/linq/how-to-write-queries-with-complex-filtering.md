---
title: Zápis dotazů se složitým filtrováním (C#)
description: Naučte se psát LINQ to XML dotazy pomocí složitých filtrů. Podívejte se na příklady kódu a zobrazte další prostředky.
ms.date: 07/20/2015
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: 5d2c1aafc210b35d4d6b1f1b2d74b11966d90c80
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303423"
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a><span data-ttu-id="40774-104">Zápis dotazů se složitým filtrováním (C#)</span><span class="sxs-lookup"><span data-stu-id="40774-104">How to write queries with complex filtering (C#)</span></span>
<span data-ttu-id="40774-105">Někdy budete chtít zapisovat LINQ to XML dotazy se složitými filtry.</span><span class="sxs-lookup"><span data-stu-id="40774-105">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="40774-106">Například může být nutné najít všechny prvky, které mají podřízený element s určitým názvem a hodnotou.</span><span class="sxs-lookup"><span data-stu-id="40774-106">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="40774-107">Toto téma poskytuje příklad zápisu dotazu se složitým filtrováním.</span><span class="sxs-lookup"><span data-stu-id="40774-107">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40774-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="40774-108">Example</span></span>  
 <span data-ttu-id="40774-109">Tento příklad ukazuje, jak najít všechny `PurchaseOrder` prvky, které mají podřízený `Address` element, který má `Type` atribut se rovná "dodávání" a podřízený `State` element se rovná "ny".</span><span class="sxs-lookup"><span data-stu-id="40774-109">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="40774-110">Používá vnořený dotaz v `Where` klauzuli a `Any` operátor vrátí, `true` Pokud má kolekce nějaké prvky.</span><span class="sxs-lookup"><span data-stu-id="40774-110">It uses a nested query in the `Where` clause, and the `Any` operator returns `true` if the collection has any elements in it.</span></span> <span data-ttu-id="40774-111">Informace o použití syntaxe dotazů založených na metodách naleznete [v tématu Syntaxe dotazu a syntaxe metody v jazyce LINQ](./query-syntax-and-method-syntax-in-linq.md).</span><span class="sxs-lookup"><span data-stu-id="40774-111">For information about using method-based query syntax, see [Query Syntax and Method Syntax in LINQ](./query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
 <span data-ttu-id="40774-112">Tento příklad používá následující dokument XML: [ukázkový soubor XML: více nákupních objednávek (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="40774-112">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="40774-113">Další informace o `Any` operátoru naleznete v tématu [operace kvantifikátoru (C#)](./quantifier-operations.md).</span><span class="sxs-lookup"><span data-stu-id="40774-113">For more information about the `Any` operator, see [Quantifier Operations (C#)](./quantifier-operations.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrders.xml");  
IEnumerable<XElement> purchaseOrders =  
    from el in root.Elements("PurchaseOrder")  
    where
        (from add in el.Elements("Address")  
        where  
            (string)add.Attribute("Type") == "Shipping" &&  
            (string)add.Element("State") == "NY"  
        select add)  
        .Any()  
    select el;  
foreach (XElement el in purchaseOrders)  
    Console.WriteLine((string)el.Attribute("PurchaseOrderNumber"));  
```  
  
 <span data-ttu-id="40774-114">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="40774-114">This code produces the following output:</span></span>  
  
```output  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="40774-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="40774-115">Example</span></span>  
 <span data-ttu-id="40774-116">Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="40774-116">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="40774-117">Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="40774-117">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="40774-118">Tento příklad používá následující dokument XML: [ukázkový soubor XML: více nákupních objednávek v oboru názvů](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="40774-118">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrdersInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> purchaseOrders =  
    from el in root.Elements(aw + "PurchaseOrder")  
    where  
        (from add in el.Elements(aw + "Address")  
         where  
             (string)add.Attribute(aw + "Type") == "Shipping" &&  
             (string)add.Element(aw + "State") == "NY"  
         select add)  
        .Any()  
    select el;  
foreach (XElement el in purchaseOrders)  
    Console.WriteLine((string)el.Attribute(aw + "PurchaseOrderNumber"));  
```  
  
 <span data-ttu-id="40774-119">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="40774-119">This code produces the following output:</span></span>  
  
```output  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="40774-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40774-120">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="40774-121">Operace projekce (C#)</span><span class="sxs-lookup"><span data-stu-id="40774-121">Projection Operations (C#)</span></span>](./projection-operations.md)
- [<span data-ttu-id="40774-122">Operace kvantifikátoru (C#)</span><span class="sxs-lookup"><span data-stu-id="40774-122">Quantifier Operations (C#)</span></span>](./quantifier-operations.md)
