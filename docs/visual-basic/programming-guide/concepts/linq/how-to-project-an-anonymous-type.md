---
title: 'How to: Project an Anonymous Type'
ms.date: 07/20/2015
ms.assetid: 30b42987-0e0e-4b2b-adb1-5255ddfbcd7b
ms.openlocfilehash: f60c55b9bc25e4691edd275c6e7417fccf5798ab
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347743"
---
# <a name="how-to-project-an-anonymous-type-visual-basic"></a><span data-ttu-id="46ce5-102">How to: Project an Anonymous Type (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46ce5-102">How to: Project an Anonymous Type (Visual Basic)</span></span>
<span data-ttu-id="46ce5-103">In some cases you might want to project a query to a new type, even though you know you will only use this type for a short while.</span><span class="sxs-lookup"><span data-stu-id="46ce5-103">In some cases you might want to project a query to a new type, even though you know you will only use this type for a short while.</span></span> <span data-ttu-id="46ce5-104">It is a lot of extra work to create a new type just to use in the projection.</span><span class="sxs-lookup"><span data-stu-id="46ce5-104">It is a lot of extra work to create a new type just to use in the projection.</span></span> <span data-ttu-id="46ce5-105">A more efficient approach in this case is to project to an anonymous type.</span><span class="sxs-lookup"><span data-stu-id="46ce5-105">A more efficient approach in this case is to project to an anonymous type.</span></span> <span data-ttu-id="46ce5-106">Anonymous types allow you to define a class, then declare and initialize an object of that class, without giving the class a name.</span><span class="sxs-lookup"><span data-stu-id="46ce5-106">Anonymous types allow you to define a class, then declare and initialize an object of that class, without giving the class a name.</span></span>  
  
 <span data-ttu-id="46ce5-107">Anonymous types are the C# implementation of the mathematical concept of a *tuple*.</span><span class="sxs-lookup"><span data-stu-id="46ce5-107">Anonymous types are the C# implementation of the mathematical concept of a *tuple*.</span></span> <span data-ttu-id="46ce5-108">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span><span class="sxs-lookup"><span data-stu-id="46ce5-108">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span></span> <span data-ttu-id="46ce5-109">It refers to a finite sequence of objects, each of a specific type.</span><span class="sxs-lookup"><span data-stu-id="46ce5-109">It refers to a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="46ce5-110">Sometimes this is called a list of name/value pairs.</span><span class="sxs-lookup"><span data-stu-id="46ce5-110">Sometimes this is called a list of name/value pairs.</span></span> <span data-ttu-id="46ce5-111">For example, the contents of an address in the [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md) XML document could be expressed as follows:</span><span class="sxs-lookup"><span data-stu-id="46ce5-111">For example, the contents of an address in the [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md) XML document could be expressed as follows:</span></span>  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 <span data-ttu-id="46ce5-112">When you create an instance of an anonymous type, it is convenient to think of it as creating a tuple of order n.</span><span class="sxs-lookup"><span data-stu-id="46ce5-112">When you create an instance of an anonymous type, it is convenient to think of it as creating a tuple of order n.</span></span> <span data-ttu-id="46ce5-113">If you write a query that creates a tuple in the `Select` clause, the query returns an `IEnumerable` of the tuple.</span><span class="sxs-lookup"><span data-stu-id="46ce5-113">If you write a query that creates a tuple in the `Select` clause, the query returns an `IEnumerable` of the tuple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46ce5-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="46ce5-114">Example</span></span>  
 <span data-ttu-id="46ce5-115">In this example, the `Select` clause projects an anonymous type.</span><span class="sxs-lookup"><span data-stu-id="46ce5-115">In this example, the `Select` clause projects an anonymous type.</span></span> <span data-ttu-id="46ce5-116">The example then uses `Dim` to create the `IEnumerable` object.</span><span class="sxs-lookup"><span data-stu-id="46ce5-116">The example then uses `Dim` to create the `IEnumerable` object.</span></span> <span data-ttu-id="46ce5-117">Within the `For Each` loop, the iteration variable becomes an instance of the anonymous type created in the query expression.</span><span class="sxs-lookup"><span data-stu-id="46ce5-117">Within the `For Each` loop, the iteration variable becomes an instance of the anonymous type created in the query expression.</span></span>  
  
 <span data-ttu-id="46ce5-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="46ce5-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="46ce5-119">This code produces the following output:</span><span class="sxs-lookup"><span data-stu-id="46ce5-119">This code produces the following output:</span></span>  
  
```console  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="46ce5-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="46ce5-120">See also</span></span>

- [<span data-ttu-id="46ce5-121">Projections and Transformations (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46ce5-121">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
