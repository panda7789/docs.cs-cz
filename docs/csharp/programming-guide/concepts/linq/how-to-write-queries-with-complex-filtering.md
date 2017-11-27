---
title: "Postupy: zápis dotazů s komplexní filtrování (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0d663b777b0d1b02462a6557097938831ef870b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a><span data-ttu-id="ddb59-102">Postupy: zápis dotazů s komplexní filtrování (C#)</span><span class="sxs-lookup"><span data-stu-id="ddb59-102">How to: Write Queries with Complex Filtering (C#)</span></span>
<span data-ttu-id="ddb59-103">Někdy budete chtít zapisovat XML dotazů LINQ s komplexní filtry.</span><span class="sxs-lookup"><span data-stu-id="ddb59-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="ddb59-104">Například můžete chtít najít všechny elementy, které mají podřízený element s určitým názvem a hodnotou.</span><span class="sxs-lookup"><span data-stu-id="ddb59-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="ddb59-105">Toto téma poskytuje příklad zápisu dotaz s komplexní filtrování.</span><span class="sxs-lookup"><span data-stu-id="ddb59-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddb59-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="ddb59-106">Example</span></span>  
 <span data-ttu-id="ddb59-107">Tento příklad ukazuje, jak najít všechny `PurchaseOrder` prvky, které podřízený `Address` element, který má `Type` atribut rovno "Přesouvání" a podřízená `State` element rovno "NY".</span><span class="sxs-lookup"><span data-stu-id="ddb59-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="ddb59-108">Používá vnořený dotaz v `Where` klauzuli a `Any` vrátí operátor `true` Pokud kolekce obsahuje všechny elementy v ní.</span><span class="sxs-lookup"><span data-stu-id="ddb59-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `true` if the collection has any elements in it.</span></span> <span data-ttu-id="ddb59-109">Informace o použití syntaxe dotazu na základě metod najdete v tématu [syntaxe dotazů a syntaxe využívající metody v technologii LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).</span><span class="sxs-lookup"><span data-stu-id="ddb59-109">For information about using method-based query syntax, see [Query Syntax and Method Syntax in LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
 <span data-ttu-id="ddb59-110">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: více nákupních objednávek (technologie LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ddb59-110">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="ddb59-111">Další informace o `Any` operátor, najdete v části [operace kvantifikátoru (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md).</span><span class="sxs-lookup"><span data-stu-id="ddb59-111">For more information about the `Any` operator, see [Quantifier Operations (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md).</span></span>  
  
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
  
 <span data-ttu-id="ddb59-112">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="ddb59-112">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="ddb59-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="ddb59-113">Example</span></span>  
 <span data-ttu-id="ddb59-114">Následující příklad ukazuje stejný dotaz pro formát XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ddb59-114">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="ddb59-115">Další informace najdete v tématu [práci s obory názvů XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="ddb59-115">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="ddb59-116">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: více nákupních objednávek v Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="ddb59-116">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="ddb59-117">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="ddb59-117">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="ddb59-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="ddb59-118">See Also</span></span>  
 <xref:System.Xml.Linq.XElement.Attribute%2A>  
 <xref:System.Xml.Linq.XContainer.Elements%2A>  
 [<span data-ttu-id="ddb59-119">Základní dotazy (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ddb59-119">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)  
 [<span data-ttu-id="ddb59-120">Operace projekce (C#)</span><span class="sxs-lookup"><span data-stu-id="ddb59-120">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)  
 [<span data-ttu-id="ddb59-121">Operace kvantifikátoru (C#)</span><span class="sxs-lookup"><span data-stu-id="ddb59-121">Quantifier Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)
