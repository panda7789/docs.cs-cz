---
title: 'Postupy: Filtrovat podle atributu (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 208d6256-1bd7-4237-b2c9-909f26dfd0e2
ms.openlocfilehash: 2537fbbac4f16a56d8a7f074b5fd10a4fcd0c09c
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205295"
---
# <a name="how-to-filter-on-an-attribute-xpath-linq-to-xml-c"></a><span data-ttu-id="d1e02-102">Postupy: Filtrovat podle atributu (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d1e02-102">How to: Filter on an Attribute (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="d1e02-103">Toto téma ukazuje, jak získat odvozené prvky se zadaným názvem a s atributem se zadanou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="d1e02-103">This topic shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>  
  
 <span data-ttu-id="d1e02-104">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="d1e02-104">The XPath expression is:</span></span>  
  
 `.//Address[@Type='Shipping']`  
  
## <a name="example"></a><span data-ttu-id="d1e02-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="d1e02-105">Example</span></span>  
 <span data-ttu-id="d1e02-106">Tento příklad vyhledá všechny prvky následníků s názvem `Address`a `Type` s atributem s hodnotou "expedice".</span><span class="sxs-lookup"><span data-stu-id="d1e02-106">This example finds all descendants elements with the name of `Address`, and with a `Type` attribute with a value of "Shipping".</span></span>  
  
 <span data-ttu-id="d1e02-107">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Více nákupních objednávek (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d1e02-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    from el in po.Descendants("Address")  
    where (string)el.Attribute("Type") == "Shipping"  
    select el;  
  
// XPath expression  
IEnumerable<XElement> list2 = po.XPathSelectElements(".//Address[@Type='Shipping']");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="d1e02-108">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d1e02-108">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<Address Type="Shipping">  
  <Name>Ellen Adams</Name>  
  <Street>123 Maple Street</Street>  
  <City>Mill Valley</City>  
  <State>CA</State>  
  <Zip>10999</Zip>  
  <Country>USA</Country>  
</Address>  
<Address Type="Shipping">  
  <Name>Cristian Osorio</Name>  
  <Street>456 Main Street</Street>  
  <City>Buffalo</City>  
  <State>NY</State>  
  <Zip>98112</Zip>  
  <Country>USA</Country>  
</Address>  
<Address Type="Shipping">  
  <Name>Jessica Arnold</Name>  
  <Street>4055 Madison Ave</Street>  
  <City>Seattle</City>  
  <State>WA</State>  
  <Zip>98112</Zip>  
  <Country>USA</Country>  
</Address>  
```  
