---
title: 'Postupy: Vyhledání souvisejících elementů (XPath – LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 6b0ef058-d704-48a5-98cd-33f00d088af9
ms.openlocfilehash: 5819ef216f767367aa16b20f818b2bbc537d54b7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364653"
---
# <a name="how-to-find-related-elements-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="3ea02-102">Postupy: hledání souvisejících elementů (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ea02-102">How to: Find Related Elements (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="3ea02-103">Toto téma ukazuje, jak získat prvek pro výběr atributu, na který odkazuje hodnota jiného prvku.</span><span class="sxs-lookup"><span data-stu-id="3ea02-103">This topic shows how to get an element selecting on an attribute that is referred to by the value of another element.</span></span>  
  
 <span data-ttu-id="3ea02-104">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="3ea02-104">The XPath expression is:</span></span>  
  
 `.//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]`  
  
## <a name="example"></a><span data-ttu-id="3ea02-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="3ea02-105">Example</span></span>  
 <span data-ttu-id="3ea02-106">Tento příklad vyhledá 12 `Order` . element pak vyhledá zákazníka pro tuto objednávku.</span><span class="sxs-lookup"><span data-stu-id="3ea02-106">This example finds the 12th `Order` element, and then finds the customer for that order.</span></span>  
  
 <span data-ttu-id="3ea02-107">Všimněte si, že indexování do seznamu v rozhraní .NET je založené na nule.</span><span class="sxs-lookup"><span data-stu-id="3ea02-107">Note that indexing into a list in .NET is 'zero' based.</span></span> <span data-ttu-id="3ea02-108">Indexování do kolekce uzlů v predikátu XPath je založené na "One".</span><span class="sxs-lookup"><span data-stu-id="3ea02-108">Indexing into a collection of nodes in an XPath predicate is 'one' based.</span></span> <span data-ttu-id="3ea02-109">Tento příklad odráží tento rozdíl.</span><span class="sxs-lookup"><span data-stu-id="3ea02-109">This example reflects this difference.</span></span>  
  
 <span data-ttu-id="3ea02-110">Tento příklad používá následující dokument XML: [ukázkový soubor XML: zákazníci a objednávky (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3ea02-110">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim co As XDocument = XDocument.Load("CustomersOrders.xml")  
  
' LINQ to XML query  
Dim customer1 As XElement = ( _  
    From el In co...<Customer> _  
    Where el.@CustomerID = co.<Root>.<Orders>.<Order>. _  
        ToList()(11).<CustomerID>(0).Value _  
    Select el).First()  
  
' An alternate way to write the query that avoids creation  
' of a System.Collections.Generic.List:  
Dim customer2 As XElement = ( _  
    From el In co...<Customer> _  
    Where el.@CustomerID = co.<Root>.<Orders>.<Order>. _  
        Skip(11).First().<CustomerID>(0).Value _  
    Select el).First()  
  
' XPath expression  
Dim customer3 As XElement = co.XPathSelectElement _  
    (".//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]")  
  
If customer1 Is customer2 And customer1 Is customer3 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(customer1)  
```  
  
 <span data-ttu-id="3ea02-111">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3ea02-111">This example produces the following output:</span></span>  
  
```console
Results are identical  
<Customer CustomerID="HUNGC">  
  <CompanyName>Hungry Coyote Import Store</CompanyName>  
  <ContactName>Yoshi Latimer</ContactName>  
  <ContactTitle>Sales Representative</ContactTitle>  
  <Phone>(503) 555-6874</Phone>  
  <Fax>(503) 555-2376</Fax>  
  <FullAddress>  
    <Address>City Center Plaza 516 Main St.</Address>  
    <City>Elgin</City>  
    <Region>OR</Region>  
    <PostalCode>97827</PostalCode>  
    <Country>USA</Country>  
  </FullAddress>  
</Customer>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3ea02-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ea02-112">See also</span></span>

- [<span data-ttu-id="3ea02-113">LINQ to XML pro uživatele XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ea02-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](linq-to-xml-for-xpath-users.md)
