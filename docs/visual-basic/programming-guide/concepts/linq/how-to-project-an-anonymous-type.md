---
title: 'Postupy: Projektování anonymního typu (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 30b42987-0e0e-4b2b-adb1-5255ddfbcd7b
ms.openlocfilehash: 613bf97556306503c427a70720272dd985495b13
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527754"
---
# <a name="how-to-project-an-anonymous-type-visual-basic"></a><span data-ttu-id="6757c-102">Postupy: Projektování anonymního typu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6757c-102">How to: Project an Anonymous Type (Visual Basic)</span></span>
<span data-ttu-id="6757c-103">V některých případech můžete chtít dotaz na nový typ projektu i v případě, že víte, že použijete tento typ se jenom na krátkou dobu.</span><span class="sxs-lookup"><span data-stu-id="6757c-103">In some cases you might want to project a query to a new type, even though you know you will only use this type for a short while.</span></span> <span data-ttu-id="6757c-104">Je hodně práce navíc k vytvoření nového typu pouze pro použití v projekci.</span><span class="sxs-lookup"><span data-stu-id="6757c-104">It is a lot of extra work to create a new type just to use in the projection.</span></span> <span data-ttu-id="6757c-105">V tomto případě je efektivnější přístup k projektu anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="6757c-105">A more efficient approach in this case is to project to an anonymous type.</span></span> <span data-ttu-id="6757c-106">Anonymní typy umožňují definovat třídu, pak deklarovat a inicializovat objekt této třídy bez názvu třídy.</span><span class="sxs-lookup"><span data-stu-id="6757c-106">Anonymous types allow you to define a class, then declare and initialize an object of that class, without giving the class a name.</span></span>  
  
 <span data-ttu-id="6757c-107">Anonymní typy jsou implementace jazyka C# matematické konceptu *řazené kolekce členů*.</span><span class="sxs-lookup"><span data-stu-id="6757c-107">Anonymous types are the C# implementation of the mathematical concept of a *tuple*.</span></span> <span data-ttu-id="6757c-108">Matematický výraz řazené kolekce členů, pochází z pořadí jeden, double, triple, čtyřikrát, pětkrát, n řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="6757c-108">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span></span> <span data-ttu-id="6757c-109">Odkazuje na konečnou sekvenci objektů, každý z určitého typu.</span><span class="sxs-lookup"><span data-stu-id="6757c-109">It refers to a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="6757c-110">To se říká se jim seznam dvojic název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="6757c-110">Sometimes this is called a list of name/value pairs.</span></span> <span data-ttu-id="6757c-111">Například obsah adresy [ukázkový soubor XML: Typická nákupní objednávka (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md) dokument XML může být vyjádřen takto:</span><span class="sxs-lookup"><span data-stu-id="6757c-111">For example, the contents of an address in the [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md) XML document could be expressed as follows:</span></span>  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 <span data-ttu-id="6757c-112">Když vytvoříte instanci anonymního typu, je vhodné si ho představit jako vytvoření n-tice n pořadí.</span><span class="sxs-lookup"><span data-stu-id="6757c-112">When you create an instance of an anonymous type, it is convenient to think of it as creating a tuple of order n.</span></span> <span data-ttu-id="6757c-113">Pokud píšete dotaz, který vytvoří řazenou kolekci členů v `Select` klauzule, dotaz vrátí `IEnumerable` řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="6757c-113">If you write a query that creates a tuple in the `Select` clause, the query returns an `IEnumerable` of the tuple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6757c-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="6757c-114">Example</span></span>  
 <span data-ttu-id="6757c-115">V tomto příkladu `Select` klauzule projekty anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="6757c-115">In this example, the `Select` clause projects an anonymous type.</span></span> <span data-ttu-id="6757c-116">Příklad poté použije `Dim` vytvořit `IEnumerable` objektu.</span><span class="sxs-lookup"><span data-stu-id="6757c-116">The example then uses `Dim` to create the `IEnumerable` object.</span></span> <span data-ttu-id="6757c-117">V rámci `For Each` smyčky, iterační proměnná stane instanci anonymního typu vytvořené ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="6757c-117">Within the `For Each` loop, the iteration variable becomes an instance of the anonymous type created in the query expression.</span></span>  
  
 <span data-ttu-id="6757c-118">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="6757c-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="6757c-119">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6757c-119">This code produces the following output:</span></span>  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="6757c-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6757c-120">See also</span></span>
- [<span data-ttu-id="6757c-121">Projekce a transformace (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6757c-121">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
