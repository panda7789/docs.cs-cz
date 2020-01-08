---
title: Zápis dotazů se složitým filtrováním (C#)
ms.date: 07/20/2015
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: a4918631fed21967b402c5c56cfb8a211d44c139
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337364"
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a><span data-ttu-id="569f6-102">Zápis dotazů se složitým filtrováním (C#)</span><span class="sxs-lookup"><span data-stu-id="569f6-102">How to write queries with complex filtering (C#)</span></span>
<span data-ttu-id="569f6-103">Někdy budete chtít zapisovat LINQ to XML dotazy se složitými filtry.</span><span class="sxs-lookup"><span data-stu-id="569f6-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="569f6-104">Například může být nutné najít všechny prvky, které mají podřízený element s určitým názvem a hodnotou.</span><span class="sxs-lookup"><span data-stu-id="569f6-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="569f6-105">Toto téma poskytuje příklad zápisu dotazu se složitým filtrováním.</span><span class="sxs-lookup"><span data-stu-id="569f6-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="569f6-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="569f6-106">Example</span></span>  
 <span data-ttu-id="569f6-107">Tento příklad ukazuje, jak najít všechny `PurchaseOrder` prvky, které mají podřízený element `Address`, který má atribut `Type` roven "dodávání" a podřízený element `State` roven "NY".</span><span class="sxs-lookup"><span data-stu-id="569f6-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="569f6-108">Používá vnořený dotaz v klauzuli `Where` a operátor `Any` vrací `true`, pokud má kolekce nějaké prvky.</span><span class="sxs-lookup"><span data-stu-id="569f6-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `true` if the collection has any elements in it.</span></span> <span data-ttu-id="569f6-109">Informace o použití syntaxe dotazů založených na metodách naleznete [v tématu Syntaxe dotazu a syntaxe metody v jazyce LINQ](./query-syntax-and-method-syntax-in-linq.md).</span><span class="sxs-lookup"><span data-stu-id="569f6-109">For information about using method-based query syntax, see [Query Syntax and Method Syntax in LINQ](./query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
 <span data-ttu-id="569f6-110">Tento příklad používá následující dokument XML: [ukázkový soubor XML: více nákupních objednávek (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="569f6-110">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="569f6-111">Další informace o operátoru `Any` naleznete v části [operace kvantifikátoru (C#)](./quantifier-operations.md).</span><span class="sxs-lookup"><span data-stu-id="569f6-111">For more information about the `Any` operator, see [Quantifier Operations (C#)](./quantifier-operations.md).</span></span>  
  
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
  
 <span data-ttu-id="569f6-112">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="569f6-112">This code produces the following output:</span></span>  
  
```output  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="569f6-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="569f6-113">Example</span></span>  
 <span data-ttu-id="569f6-114">Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="569f6-114">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="569f6-115">Další informace najdete v tématu [obory názvů Overview (LINQ to XMLC#) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="569f6-115">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="569f6-116">Tento příklad používá následující dokument XML: [ukázkový soubor XML: více nákupních objednávek v oboru názvů](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="569f6-116">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="569f6-117">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="569f6-117">This code produces the following output:</span></span>  
  
```output  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="569f6-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="569f6-118">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="569f6-119">Operace projekce (C#)</span><span class="sxs-lookup"><span data-stu-id="569f6-119">Projection Operations (C#)</span></span>](./projection-operations.md)
- [<span data-ttu-id="569f6-120">Operace kvantifikátoru (C#)</span><span class="sxs-lookup"><span data-stu-id="569f6-120">Quantifier Operations (C#)</span></span>](./quantifier-operations.md)
