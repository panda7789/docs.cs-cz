---
title: 'Postupy: Projektování anonymního typu (C#)'
ms.date: 07/20/2015
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
ms.openlocfilehash: 68b008d70474c927a7911dc77e60afb634035b77
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485124"
---
# <a name="how-to-project-an-anonymous-type-c"></a><span data-ttu-id="748c4-102">Postupy: Projektování anonymního typu (C#)</span><span class="sxs-lookup"><span data-stu-id="748c4-102">How to: Project an Anonymous Type (C#)</span></span>
<span data-ttu-id="748c4-103">V některých případech můžete chtít dotaz na nový typ projektu i v případě, že víte, že použijete tento typ se jenom na krátkou dobu.</span><span class="sxs-lookup"><span data-stu-id="748c4-103">In some cases you might want to project a query to a new type, even though you know you will only use this type for a short while.</span></span> <span data-ttu-id="748c4-104">Je hodně práce navíc k vytvoření nového typu pouze pro použití v projekci.</span><span class="sxs-lookup"><span data-stu-id="748c4-104">It is a lot of extra work to create a new type just to use in the projection.</span></span> <span data-ttu-id="748c4-105">V tomto případě je efektivnější přístup k projektu anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="748c4-105">A more efficient approach in this case is to project to an anonymous type.</span></span> <span data-ttu-id="748c4-106">Anonymní typy umožňují definovat třídu, pak deklarovat a inicializovat objekt této třídy bez názvu třídy.</span><span class="sxs-lookup"><span data-stu-id="748c4-106">Anonymous types allow you to define a class, then declare and initialize an object of that class, without giving the class a name.</span></span>  
  
 <span data-ttu-id="748c4-107">Anonymní typy jsou implementace jazyka C# matematické konceptu *řazené kolekce členů*.</span><span class="sxs-lookup"><span data-stu-id="748c4-107">Anonymous types are the C# implementation of the mathematical concept of a *tuple*.</span></span> <span data-ttu-id="748c4-108">Matematický výraz řazené kolekce členů, pochází z pořadí jeden, double, triple, čtyřikrát, pětkrát, n řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="748c4-108">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span></span> <span data-ttu-id="748c4-109">Odkazuje na konečnou sekvenci objektů, každý z určitého typu.</span><span class="sxs-lookup"><span data-stu-id="748c4-109">It refers to a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="748c4-110">To se říká se jim seznam dvojic název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="748c4-110">Sometimes this is called a list of name/value pairs.</span></span> <span data-ttu-id="748c4-111">Například obsah adresy [ukázkový soubor XML: Typická nákupní objednávka (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md) dokument XML může být vyjádřen takto:</span><span class="sxs-lookup"><span data-stu-id="748c4-111">For example, the contents of an address in the [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md) XML document could be expressed as follows:</span></span>  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 <span data-ttu-id="748c4-112">Když vytvoříte instanci anonymního typu, je vhodné si ho představit jako vytvoření n-tice n pořadí.</span><span class="sxs-lookup"><span data-stu-id="748c4-112">When you create an instance of an anonymous type, it is convenient to think of it as creating a tuple of order n.</span></span> <span data-ttu-id="748c4-113">Pokud píšete dotaz, který vytvoří řazenou kolekci členů v `select` klauzule, dotaz vrátí `IEnumerable` řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="748c4-113">If you write a query that creates a tuple in the `select` clause, the query returns an `IEnumerable` of the tuple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="748c4-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="748c4-114">Example</span></span>  
 <span data-ttu-id="748c4-115">V tomto příkladu `select` klauzule projekty anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="748c4-115">In this example, the `select` clause projects an anonymous type.</span></span> <span data-ttu-id="748c4-116">Příklad poté použije `var` vytvořit `IEnumerable` objektu.</span><span class="sxs-lookup"><span data-stu-id="748c4-116">The example then uses `var` to create the `IEnumerable` object.</span></span> <span data-ttu-id="748c4-117">V rámci `foreach` smyčky, iterační proměnná stane instanci anonymního typu vytvořené ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="748c4-117">Within the `foreach` loop, the iteration variable becomes an instance of the anonymous type created in the query expression.</span></span>  
  
 <span data-ttu-id="748c4-118">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="748c4-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="748c4-119">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="748c4-119">This code produces the following output:</span></span>  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  