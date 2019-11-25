---
title: Jak najít související elementy (XPath-LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 41b386ee-562d-4841-bd6b-e44a7eb69f26
ms.openlocfilehash: cdc281d0b08ee7b7f93ac28b14e82fa113a3379d
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141029"
---
# <a name="how-to-find-related-elements-xpath-linq-to-xml-c"></a><span data-ttu-id="7b14c-102">Jak najít související elementy (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="7b14c-102">How to find related elements (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="7b14c-103">Toto téma ukazuje, jak získat prvek pro výběr atributu, na který odkazuje hodnota jiného prvku.</span><span class="sxs-lookup"><span data-stu-id="7b14c-103">This topic shows how to get an element selecting on an attribute that is referred to by the value of another element.</span></span>  
  
 <span data-ttu-id="7b14c-104">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="7b14c-104">The XPath expression is:</span></span>  
  
 `.//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]`  
  
## <a name="example"></a><span data-ttu-id="7b14c-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="7b14c-105">Example</span></span>  
 <span data-ttu-id="7b14c-106">Tento příklad najde 12 `Order` prvek a potom vyhledá zákazníka pro tuto objednávku.</span><span class="sxs-lookup"><span data-stu-id="7b14c-106">This example finds the 12th `Order` element, and then finds the customer for that order.</span></span>  
  
 <span data-ttu-id="7b14c-107">Všimněte si, že indexování do seznamu v rozhraní .NET je založené na nule.</span><span class="sxs-lookup"><span data-stu-id="7b14c-107">Note that indexing into a list in .NET is 'zero' based.</span></span> <span data-ttu-id="7b14c-108">Indexování do kolekce uzlů v predikátu XPath je založené na "One".</span><span class="sxs-lookup"><span data-stu-id="7b14c-108">Indexing into a collection of nodes in an XPath predicate is 'one' based.</span></span> <span data-ttu-id="7b14c-109">Tento příklad odráží tento rozdíl.</span><span class="sxs-lookup"><span data-stu-id="7b14c-109">This example reflects this difference.</span></span>  
  
 <span data-ttu-id="7b14c-110">Tento příklad používá následující dokument XML: [ukázkový soubor XML: zákazníci a objednávky (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="7b14c-110">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
XDocument co = XDocument.Load("CustomersOrders.xml");  
  
// LINQ to XML query  
XElement customer1 =  
    (from el in co.Descendants("Customer")  
     where (string)el.Attribute("CustomerID") ==  
          (string)(co  
              .Element("Root")  
              .Element("Orders")  
              .Elements("Order")  
              .ToList()[11]  
              .Element("CustomerID"))  
    select el)  
    .First();  
  
// An alternate way to write the query that avoids creation  
// of a System.Collections.Generic.List:  
XElement customer2 =  
    (from el in co.Descendants("Customer")  
     where (string)el.Attribute("CustomerID") ==  
          (string)(co  
              .Element("Root")  
              .Element("Orders")  
              .Elements("Order")  
              .Skip(11).First()  
              .Element("CustomerID"))  
    select el)  
    .First();  
  
// XPath expression  
XElement customer3 = co.XPathSelectElement(  
  ".//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]");  
  
if (customer1 == customer2 && customer1 == customer3)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(customer1);  
```  
  
 <span data-ttu-id="7b14c-111">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="7b14c-111">This example produces the following output:</span></span>  
  
```output  
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
 