---
title: 'Postupy: Projektování anonymního typu'
ms.date: 07/20/2015
ms.assetid: 30b42987-0e0e-4b2b-adb1-5255ddfbcd7b
ms.openlocfilehash: 459602eb7ede0bd055e00d3c7620cb95ec5408ff
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396477"
---
# <a name="how-to-project-an-anonymous-type-visual-basic"></a><span data-ttu-id="58a97-102">Postupy: projektování anonymního typu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58a97-102">How to: Project an Anonymous Type (Visual Basic)</span></span>
<span data-ttu-id="58a97-103">V některých případech můžete chtít vytvořit dotaz na nový typ, i když víte, že tento typ budete používat jenom krátce.</span><span class="sxs-lookup"><span data-stu-id="58a97-103">In some cases you might want to project a query to a new type, even though you know you will only use this type for a short while.</span></span> <span data-ttu-id="58a97-104">Je to mnoho dalších práce pro vytvoření nového typu pouze k použití v projekci.</span><span class="sxs-lookup"><span data-stu-id="58a97-104">It is a lot of extra work to create a new type just to use in the projection.</span></span> <span data-ttu-id="58a97-105">Efektivnější přístup v tomto případě je projekt na anonymní typ.</span><span class="sxs-lookup"><span data-stu-id="58a97-105">A more efficient approach in this case is to project to an anonymous type.</span></span> <span data-ttu-id="58a97-106">Anonymní typy umožňují definovat třídu a pak deklarovat a inicializovat objekt této třídy, aniž by bylo nutné zadat název třídy.</span><span class="sxs-lookup"><span data-stu-id="58a97-106">Anonymous types allow you to define a class, then declare and initialize an object of that class, without giving the class a name.</span></span>  
  
 <span data-ttu-id="58a97-107">Anonymní typy jsou implementace matematického konceptu *řazené kolekce členů*v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="58a97-107">Anonymous types are the C# implementation of the mathematical concept of a *tuple*.</span></span> <span data-ttu-id="58a97-108">Matematická pojem řazené kolekce členů pochází z sekvence Single, Double, Triple, čtyřnásobná, quintuple, n-Tuple.</span><span class="sxs-lookup"><span data-stu-id="58a97-108">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span></span> <span data-ttu-id="58a97-109">Odkazuje na konečnou sekvenci objektů, každého konkrétního typu.</span><span class="sxs-lookup"><span data-stu-id="58a97-109">It refers to a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="58a97-110">Někdy se označuje jako seznam párů název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="58a97-110">Sometimes this is called a list of name/value pairs.</span></span> <span data-ttu-id="58a97-111">Například obsah adresy v [ukázkovém souboru XML: typický dokument XML s nákupní objednávkou (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md) může být vyjádřen následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="58a97-111">For example, the contents of an address in the [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md) XML document could be expressed as follows:</span></span>  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 <span data-ttu-id="58a97-112">Když vytváříte instanci anonymního typu, je vhodné ji považovat za vytváření řazené kolekce členů objednávky n.</span><span class="sxs-lookup"><span data-stu-id="58a97-112">When you create an instance of an anonymous type, it is convenient to think of it as creating a tuple of order n.</span></span> <span data-ttu-id="58a97-113">Pokud napíšete dotaz, který v klauzuli vytvoří řazenou kolekci členů `Select` , dotaz vrátí `IEnumerable` kolekci řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="58a97-113">If you write a query that creates a tuple in the `Select` clause, the query returns an `IEnumerable` of the tuple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58a97-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="58a97-114">Example</span></span>  
 <span data-ttu-id="58a97-115">V tomto příkladu je `Select` klauzule projekt anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="58a97-115">In this example, the `Select` clause projects an anonymous type.</span></span> <span data-ttu-id="58a97-116">Příklad následně používá `Dim` k vytvoření `IEnumerable` objektu.</span><span class="sxs-lookup"><span data-stu-id="58a97-116">The example then uses `Dim` to create the `IEnumerable` object.</span></span> <span data-ttu-id="58a97-117">V rámci `For Each` smyčky se proměnná iterace stala instancí anonymního typu vytvořeného ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="58a97-117">Within the `For Each` loop, the iteration variable becomes an instance of the anonymous type created in the query expression.</span></span>  
  
 <span data-ttu-id="58a97-118">Tento příklad používá následující dokument XML: [ukázkový soubor XML: zákazníci a objednávky (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="58a97-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")  
Dim custList = _  
    From el In custOrd.<Customers>.<Customer> _  
    Select New With { _  
        .CustomerID = el.@<CustomerID>, _  
        .CompanyName = el.<CompanyName>.Value, _  
        .ContactName = el.<ContactName>.Value _  
    }  
For Each cust In custList  
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName)  
Next  
```  
  
 <span data-ttu-id="58a97-119">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="58a97-119">This code produces the following output:</span></span>  
  
```console  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="58a97-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="58a97-120">See also</span></span>

- [<span data-ttu-id="58a97-121">Projekce a transformace (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58a97-121">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](projections-and-transformations-linq-to-xml.md)
