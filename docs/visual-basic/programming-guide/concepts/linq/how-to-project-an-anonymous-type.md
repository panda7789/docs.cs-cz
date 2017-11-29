---
title: "Postupy: projektu anonymní typ (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 30b42987-0e0e-4b2b-adb1-5255ddfbcd7b
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b383b0a7e0fc0aa22bdcc8ed87628947858986da
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-project-an-anonymous-type-visual-basic"></a><span data-ttu-id="eaace-102">Postupy: projektu anonymní typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eaace-102">How to: Project an Anonymous Type (Visual Basic)</span></span>
<span data-ttu-id="eaace-103">V některých případech můžete chtít projektu dotaz pro nový typ, i když víte, že použijete tento typ se pouze na krátkou dobu.</span><span class="sxs-lookup"><span data-stu-id="eaace-103">In some cases you might want to project a query to a new type, even though you know you will only use this type for a short while.</span></span> <span data-ttu-id="eaace-104">Je velké množství práce navíc k vytvoření nového typu jenom pro použití v projekci.</span><span class="sxs-lookup"><span data-stu-id="eaace-104">It is a lot of extra work to create a new type just to use in the projection.</span></span> <span data-ttu-id="eaace-105">V takovém případě má efektivnější přístup projekt anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="eaace-105">A more efficient approach in this case is to project to an anonymous type.</span></span> <span data-ttu-id="eaace-106">Anonymní typy umožňují definovat třídu, pak deklarovat a inicializovat objekt třídy, bez nutnosti poskytnutí název třídy.</span><span class="sxs-lookup"><span data-stu-id="eaace-106">Anonymous types allow you to define a class, then declare and initialize an object of that class, without giving the class a name.</span></span>  
  
 <span data-ttu-id="eaace-107">Anonymní typy jsou implementace C# matematickém koncept *řazené kolekce členů*.</span><span class="sxs-lookup"><span data-stu-id="eaace-107">Anonymous types are the C# implementation of the mathematical concept of a *tuple*.</span></span> <span data-ttu-id="eaace-108">Matematický výraz řazené kolekce členů, pochází z pořadí jednoho, double, triple, čtyřikrát, pětkrát, n řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="eaace-108">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span></span> <span data-ttu-id="eaace-109">Odkazuje na konečné pořadí objektů, každý z konkrétního typu.</span><span class="sxs-lookup"><span data-stu-id="eaace-109">It refers to a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="eaace-110">To se někdy říká seznam dvojic název hodnota.</span><span class="sxs-lookup"><span data-stu-id="eaace-110">Sometimes this is called a list of name/value pairs.</span></span> <span data-ttu-id="eaace-111">Například obsah adresy [ukázkový soubor XML: typické nákupní objednávka (technologie LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md) dokumentu XML může být vyjádřena takto:</span><span class="sxs-lookup"><span data-stu-id="eaace-111">For example, the contents of an address in the [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md) XML document could be expressed as follows:</span></span>  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 <span data-ttu-id="eaace-112">Když vytvoříte instanci anonymního typu, je vhodné si ho představit jako vytváření pořadí n řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="eaace-112">When you create an instance of an anonymous type, it is convenient to think of it as creating a tuple of order n.</span></span> <span data-ttu-id="eaace-113">Pokud píšete dotaz, který vytvoří řazené kolekce členů v `Select` klauzule, dotaz vrátí `IEnumerable` řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="eaace-113">If you write a query that creates a tuple in the `Select` clause, the query returns an `IEnumerable` of the tuple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eaace-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="eaace-114">Example</span></span>  
 <span data-ttu-id="eaace-115">V tomto příkladu `Select` klauzule projekty anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="eaace-115">In this example, the `Select` clause projects an anonymous type.</span></span> <span data-ttu-id="eaace-116">V příkladu se pak použije `Dim` vytvořit `IEnumerable` objektu.</span><span class="sxs-lookup"><span data-stu-id="eaace-116">The example then uses `Dim` to create the `IEnumerable` object.</span></span> <span data-ttu-id="eaace-117">V rámci `For Each` smyčky, proměnné iterace stane instanci anonymního typu vytvořen ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="eaace-117">Within the `For Each` loop, the iteration variable becomes an instance of the anonymous type created in the query expression.</span></span>  
  
 <span data-ttu-id="eaace-118">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: Zákazníci a objednávky (technologie LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="eaace-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="eaace-119">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="eaace-119">This code produces the following output:</span></span>  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="eaace-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="eaace-120">See Also</span></span>  
 [<span data-ttu-id="eaace-121">Projekce a transformace (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eaace-121">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
