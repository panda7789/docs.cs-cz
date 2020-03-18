---
title: Jak promítat anonymní typ (C#)
ms.date: 07/20/2015
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
ms.openlocfilehash: 7797c8bfb12943af1ce7f975b170bf002aa7d6fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345724"
---
# <a name="how-to-project-an-anonymous-type-c"></a><span data-ttu-id="75654-102">Jak promítat anonymní typ (C#)</span><span class="sxs-lookup"><span data-stu-id="75654-102">How to project an anonymous type (C#)</span></span>
<span data-ttu-id="75654-103">V některých případech můžete chtít promítnout dotaz na nový typ, i když víte, že tento typ budete používat pouze na krátkou dobu.</span><span class="sxs-lookup"><span data-stu-id="75654-103">In some cases you might want to project a query to a new type, even though you know you will only use this type for a short while.</span></span> <span data-ttu-id="75654-104">Je to hodně práce navíc vytvořit nový typ jen pro použití v projekci.</span><span class="sxs-lookup"><span data-stu-id="75654-104">It is a lot of extra work to create a new type just to use in the projection.</span></span> <span data-ttu-id="75654-105">Efektivnější přístup v tomto případě je projekt na anonymní typ.</span><span class="sxs-lookup"><span data-stu-id="75654-105">A more efficient approach in this case is to project to an anonymous type.</span></span> <span data-ttu-id="75654-106">Anonymní typy umožňují definovat třídu, pak deklarovat a inicializovat objekt této třídy, aniž by třídy název.</span><span class="sxs-lookup"><span data-stu-id="75654-106">Anonymous types allow you to define a class, then declare and initialize an object of that class, without giving the class a name.</span></span>  
  
 <span data-ttu-id="75654-107">Anonymní typy jsou implementace C# matematického konceptu *řazené kolekce členů*.</span><span class="sxs-lookup"><span data-stu-id="75654-107">Anonymous types are the C# implementation of the mathematical concept of a *tuple*.</span></span> <span data-ttu-id="75654-108">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span><span class="sxs-lookup"><span data-stu-id="75654-108">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span></span> <span data-ttu-id="75654-109">Odkazuje na konečnou sekvenci objektů, každý z určitého typu.</span><span class="sxs-lookup"><span data-stu-id="75654-109">It refers to a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="75654-110">Někdy se tomu říká seznam párů název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="75654-110">Sometimes this is called a list of name/value pairs.</span></span> <span data-ttu-id="75654-111">Například obsah adresy v [ukázkovém souboru XML: Typická nákupní objednávka (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) XML dokument může být vyjádřen a to to toto:</span><span class="sxs-lookup"><span data-stu-id="75654-111">For example, the contents of an address in the [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) XML document could be expressed as follows:</span></span>  
  
```text  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 <span data-ttu-id="75654-112">Když vytvoříte instanci anonymního typu, je vhodné si ji myslet jako vytvoření řazené kolekce členů pořadí n.</span><span class="sxs-lookup"><span data-stu-id="75654-112">When you create an instance of an anonymous type, it is convenient to think of it as creating a tuple of order n.</span></span> <span data-ttu-id="75654-113">Pokud napíšete dotaz, který vytvoří `select` řazenou `IEnumerable` kolekce členů v klauzuli, dotaz vrátí n-tice.</span><span class="sxs-lookup"><span data-stu-id="75654-113">If you write a query that creates a tuple in the `select` clause, the query returns an `IEnumerable` of the tuple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75654-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="75654-114">Example</span></span>  
 <span data-ttu-id="75654-115">V tomto příkladu klauzule `select` projekty anonymní typ.</span><span class="sxs-lookup"><span data-stu-id="75654-115">In this example, the `select` clause projects an anonymous type.</span></span> <span data-ttu-id="75654-116">Příklad pak `var` používá k `IEnumerable` vytvoření objektu.</span><span class="sxs-lookup"><span data-stu-id="75654-116">The example then uses `var` to create the `IEnumerable` object.</span></span> <span data-ttu-id="75654-117">V `foreach` rámci smyčky se iterace proměnná stane instanci anonymního typu vytvořeného ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="75654-117">Within the `foreach` loop, the iteration variable becomes an instance of the anonymous type created in the query expression.</span></span>  
  
 <span data-ttu-id="75654-118">Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML).](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)</span><span class="sxs-lookup"><span data-stu-id="75654-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="75654-119">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="75654-119">This code produces the following output:</span></span>  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  