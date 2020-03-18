---
title: Jak psát dotazy se složitým filtrováním (C#)
ms.date: 07/20/2015
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: bc85d7f1e5c5305407ad22f3ada908523313d964
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168515"
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a><span data-ttu-id="649dd-102">Jak psát dotazy se složitým filtrováním (C#)</span><span class="sxs-lookup"><span data-stu-id="649dd-102">How to write queries with complex filtering (C#)</span></span>
<span data-ttu-id="649dd-103">Někdy chcete zapsat LINQ do dotazů XML se složitými filtry.</span><span class="sxs-lookup"><span data-stu-id="649dd-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="649dd-104">Například budete muset najít všechny prvky, které mají podřízený prvek s určitým názvem a hodnotou.</span><span class="sxs-lookup"><span data-stu-id="649dd-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="649dd-105">Toto téma uvádí příklad psaní dotazu se složitým filtrováním.</span><span class="sxs-lookup"><span data-stu-id="649dd-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="649dd-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="649dd-106">Example</span></span>  
 <span data-ttu-id="649dd-107">Tento příklad ukazuje, `PurchaseOrder` jak najít všechny `Address` prvky, `Type` které mají podřízený prvek, který má atribut rovný "Doprava" a podřízený `State` prvek rovnající se "NY".</span><span class="sxs-lookup"><span data-stu-id="649dd-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="649dd-108">Používá vnořený dotaz `Where` v klauzuli a `Any` operátor vrátí, `true` pokud kolekce má nějaké prvky v něm.</span><span class="sxs-lookup"><span data-stu-id="649dd-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `true` if the collection has any elements in it.</span></span> <span data-ttu-id="649dd-109">Informace o použití syntaxe dotazu založeného na metodách naleznete [v tématu Syntaxe dotazu a syntaxe metody v LINQ](./query-syntax-and-method-syntax-in-linq.md).</span><span class="sxs-lookup"><span data-stu-id="649dd-109">For information about using method-based query syntax, see [Query Syntax and Method Syntax in LINQ](./query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
 <span data-ttu-id="649dd-110">Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Více nákupních objednávek (LINQ to XML).](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="649dd-110">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="649dd-111">Další informace o `Any` operátoru naleznete v tématu [Kvantifikátor operace (C#)](./quantifier-operations.md).</span><span class="sxs-lookup"><span data-stu-id="649dd-111">For more information about the `Any` operator, see [Quantifier Operations (C#)](./quantifier-operations.md).</span></span>  
  
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
  
 <span data-ttu-id="649dd-112">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="649dd-112">This code produces the following output:</span></span>  
  
```output  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="649dd-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="649dd-113">Example</span></span>  
 <span data-ttu-id="649dd-114">Následující příklad ukazuje stejný dotaz pro jazyk XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="649dd-114">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="649dd-115">Další informace naleznete [v tématu Přehled oborů názvů (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="649dd-115">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="649dd-116">Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Více nákupních objednávek v oboru názvů](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="649dd-116">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="649dd-117">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="649dd-117">This code produces the following output:</span></span>  
  
```output  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="649dd-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="649dd-118">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="649dd-119">Projekční operace (C#)</span><span class="sxs-lookup"><span data-stu-id="649dd-119">Projection Operations (C#)</span></span>](./projection-operations.md)
- [<span data-ttu-id="649dd-120">Operace kvantifikátoru (C#)</span><span class="sxs-lookup"><span data-stu-id="649dd-120">Quantifier Operations (C#)</span></span>](./quantifier-operations.md)
