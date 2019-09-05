---
title: 'Postupy: Projekt anonymního typu (C#)'
ms.date: 07/20/2015
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
ms.openlocfilehash: 3ed14ae6e7bc4b84ae9dc416b76e37443b831c73
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253511"
---
# <a name="how-to-project-an-anonymous-type-c"></a><span data-ttu-id="3dfa2-102">Postupy: Projekt anonymního typu (C#)</span><span class="sxs-lookup"><span data-stu-id="3dfa2-102">How to: Project an Anonymous Type (C#)</span></span>
<span data-ttu-id="3dfa2-103">V některých případech můžete chtít vytvořit dotaz na nový typ, i když víte, že tento typ budete používat jenom krátce.</span><span class="sxs-lookup"><span data-stu-id="3dfa2-103">In some cases you might want to project a query to a new type, even though you know you will only use this type for a short while.</span></span> <span data-ttu-id="3dfa2-104">Je to mnoho dalších práce pro vytvoření nového typu pouze k použití v projekci.</span><span class="sxs-lookup"><span data-stu-id="3dfa2-104">It is a lot of extra work to create a new type just to use in the projection.</span></span> <span data-ttu-id="3dfa2-105">Efektivnější přístup v tomto případě je projekt na anonymní typ.</span><span class="sxs-lookup"><span data-stu-id="3dfa2-105">A more efficient approach in this case is to project to an anonymous type.</span></span> <span data-ttu-id="3dfa2-106">Anonymní typy umožňují definovat třídu a pak deklarovat a inicializovat objekt této třídy, aniž by bylo nutné zadat název třídy.</span><span class="sxs-lookup"><span data-stu-id="3dfa2-106">Anonymous types allow you to define a class, then declare and initialize an object of that class, without giving the class a name.</span></span>  
  
 <span data-ttu-id="3dfa2-107">Anonymní typy jsou C# implementace matematického konceptu *řazené kolekce členů*.</span><span class="sxs-lookup"><span data-stu-id="3dfa2-107">Anonymous types are the C# implementation of the mathematical concept of a *tuple*.</span></span> <span data-ttu-id="3dfa2-108">Matematická pojem řazené kolekce členů pochází z sekvence Single, Double, Triple, čtyřnásobná, quintuple, n-Tuple.</span><span class="sxs-lookup"><span data-stu-id="3dfa2-108">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span></span> <span data-ttu-id="3dfa2-109">Odkazuje na konečnou sekvenci objektů, každého konkrétního typu.</span><span class="sxs-lookup"><span data-stu-id="3dfa2-109">It refers to a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="3dfa2-110">Někdy se označuje jako seznam párů název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="3dfa2-110">Sometimes this is called a list of name/value pairs.</span></span> <span data-ttu-id="3dfa2-111">Například obsah adresy v [ukázkovém souboru XML: Typický dokument XML s nákupní objednávkou (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) může být vyjádřený takto:</span><span class="sxs-lookup"><span data-stu-id="3dfa2-111">For example, the contents of an address in the [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) XML document could be expressed as follows:</span></span>  
  
```text  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 <span data-ttu-id="3dfa2-112">Když vytváříte instanci anonymního typu, je vhodné ji považovat za vytváření řazené kolekce členů objednávky n.</span><span class="sxs-lookup"><span data-stu-id="3dfa2-112">When you create an instance of an anonymous type, it is convenient to think of it as creating a tuple of order n.</span></span> <span data-ttu-id="3dfa2-113">Pokud napíšete dotaz, který v `select` klauzuli vytvoří řazenou kolekci členů, dotaz `IEnumerable` vrátí kolekci řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="3dfa2-113">If you write a query that creates a tuple in the `select` clause, the query returns an `IEnumerable` of the tuple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3dfa2-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="3dfa2-114">Example</span></span>  
 <span data-ttu-id="3dfa2-115">V tomto příkladu je `select` klauzule projekt anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="3dfa2-115">In this example, the `select` clause projects an anonymous type.</span></span> <span data-ttu-id="3dfa2-116">Příklad následně používá `var` k `IEnumerable` vytvoření objektu.</span><span class="sxs-lookup"><span data-stu-id="3dfa2-116">The example then uses `var` to create the `IEnumerable` object.</span></span> <span data-ttu-id="3dfa2-117">V rámci `foreach` smyčky se proměnná iterace stala instancí anonymního typu vytvořeného ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="3dfa2-117">Within the `foreach` loop, the iteration variable becomes an instance of the anonymous type created in the query expression.</span></span>  
  
 <span data-ttu-id="3dfa2-118">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="3dfa2-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="3dfa2-119">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3dfa2-119">This code produces the following output:</span></span>  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  