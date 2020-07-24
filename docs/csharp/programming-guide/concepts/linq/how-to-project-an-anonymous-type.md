---
title: Jak promítnout anonymní typ (C#)
description: Naučte se, jak projektovat dotaz anonymnímu typu v jazyce C#. Použití anonymního typu může být snazší než vytváření nového typu pro použití pouze krátce.
ms.date: 07/20/2015
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
ms.openlocfilehash: 6598796a4ba95362340f2551b1da6ac6d857eaae
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104634"
---
# <a name="how-to-project-an-anonymous-type-c"></a><span data-ttu-id="2c5ef-104">Jak promítnout anonymní typ (C#)</span><span class="sxs-lookup"><span data-stu-id="2c5ef-104">How to project an anonymous type (C#)</span></span>
<span data-ttu-id="2c5ef-105">V některých případech můžete chtít vytvořit dotaz na nový typ, i když víte, že tento typ budete používat jenom krátce.</span><span class="sxs-lookup"><span data-stu-id="2c5ef-105">In some cases you might want to project a query to a new type, even though you know you will only use this type for a short while.</span></span> <span data-ttu-id="2c5ef-106">Je to mnoho dalších práce pro vytvoření nového typu pouze k použití v projekci.</span><span class="sxs-lookup"><span data-stu-id="2c5ef-106">It is a lot of extra work to create a new type just to use in the projection.</span></span> <span data-ttu-id="2c5ef-107">Efektivnější přístup v tomto případě je projekt na anonymní typ.</span><span class="sxs-lookup"><span data-stu-id="2c5ef-107">A more efficient approach in this case is to project to an anonymous type.</span></span> <span data-ttu-id="2c5ef-108">Anonymní typy umožňují definovat třídu a pak deklarovat a inicializovat objekt této třídy, aniž by bylo nutné zadat název třídy.</span><span class="sxs-lookup"><span data-stu-id="2c5ef-108">Anonymous types allow you to define a class, then declare and initialize an object of that class, without giving the class a name.</span></span>  
  
 <span data-ttu-id="2c5ef-109">Anonymní typy jsou implementace matematického konceptu *řazené kolekce členů*v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="2c5ef-109">Anonymous types are the C# implementation of the mathematical concept of a *tuple*.</span></span> <span data-ttu-id="2c5ef-110">Matematická pojem řazené kolekce členů pochází z sekvence Single, Double, Triple, čtyřnásobná, quintuple, n-Tuple.</span><span class="sxs-lookup"><span data-stu-id="2c5ef-110">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span></span> <span data-ttu-id="2c5ef-111">Odkazuje na konečnou sekvenci objektů, každého konkrétního typu.</span><span class="sxs-lookup"><span data-stu-id="2c5ef-111">It refers to a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="2c5ef-112">Někdy se označuje jako seznam párů název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="2c5ef-112">Sometimes this is called a list of name/value pairs.</span></span> <span data-ttu-id="2c5ef-113">Například obsah adresy v [ukázkovém souboru XML: typický dokument XML s nákupní objednávkou (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) může být vyjádřen následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="2c5ef-113">For example, the contents of an address in the [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) XML document could be expressed as follows:</span></span>  
  
```text  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 <span data-ttu-id="2c5ef-114">Když vytváříte instanci anonymního typu, je vhodné ji považovat za vytváření řazené kolekce členů objednávky n.</span><span class="sxs-lookup"><span data-stu-id="2c5ef-114">When you create an instance of an anonymous type, it is convenient to think of it as creating a tuple of order n.</span></span> <span data-ttu-id="2c5ef-115">Pokud napíšete dotaz, který v klauzuli vytvoří řazenou kolekci členů `select` , dotaz vrátí `IEnumerable` kolekci řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="2c5ef-115">If you write a query that creates a tuple in the `select` clause, the query returns an `IEnumerable` of the tuple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c5ef-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="2c5ef-116">Example</span></span>  
 <span data-ttu-id="2c5ef-117">V tomto příkladu je `select` klauzule projekt anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="2c5ef-117">In this example, the `select` clause projects an anonymous type.</span></span> <span data-ttu-id="2c5ef-118">Příklad následně používá `var` k vytvoření `IEnumerable` objektu.</span><span class="sxs-lookup"><span data-stu-id="2c5ef-118">The example then uses `var` to create the `IEnumerable` object.</span></span> <span data-ttu-id="2c5ef-119">V rámci `foreach` smyčky se proměnná iterace stala instancí anonymního typu vytvořeného ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="2c5ef-119">Within the `foreach` loop, the iteration variable becomes an instance of the anonymous type created in the query expression.</span></span>  
  
 <span data-ttu-id="2c5ef-120">Tento příklad používá následující dokument XML: [ukázkový soubor XML: zákazníci a objednávky (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="2c5ef-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
XElement custOrd = XElement.Load("CustomersOrders.xml");  
var custList =  
    from el in custOrd.Element("Customers").Elements("Customer")  
    select new {  
        CustomerID = (string)el.Attribute("CustomerID"),  
        CompanyName = (string)el.Element("CompanyName"),  
        ContactName = (string)el.Element("ContactName")  
    };  
foreach (var cust in custList)  
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName);  
```  
  
 <span data-ttu-id="2c5ef-121">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="2c5ef-121">This code produces the following output:</span></span>  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  