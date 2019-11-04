---
title: 'Postupy: generování textových souborů z formátu XML (C#)'
ms.date: 07/20/2015
ms.assetid: 9ad283f7-7cac-42ff-bf32-92aa866e6883
ms.openlocfilehash: 8e36bbda60bea207707dcf869afc059e645ec8ad
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418307"
---
# <a name="how-to-generate-text-files-from-xml-c"></a><span data-ttu-id="51085-102">Postupy: generování textových souborů z formátu XML (C#)</span><span class="sxs-lookup"><span data-stu-id="51085-102">How to: Generate Text Files from XML (C#)</span></span>
<span data-ttu-id="51085-103">Tento příklad ukazuje, jak vygenerovat soubor hodnot oddělených čárkami (CSV) ze souboru XML.</span><span class="sxs-lookup"><span data-stu-id="51085-103">This example shows how to generate a comma-separated values (CSV) file from an XML file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51085-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="51085-104">Example</span></span>  
 <span data-ttu-id="51085-105">C# Verze v tomto příkladu používá syntaxi metody a operátor `Aggregate` k vygenerování souboru CSV z dokumentu XML v jednom výrazu.</span><span class="sxs-lookup"><span data-stu-id="51085-105">The C# version of this example uses method syntax and the `Aggregate` operator to generate a CSV file from an XML document in a single expression.</span></span> <span data-ttu-id="51085-106">Další informace naleznete v tématu [syntaxe dotazu a syntaxe metody v jazyce LINQ](./query-syntax-and-method-syntax-in-linq.md).</span><span class="sxs-lookup"><span data-stu-id="51085-106">For more information, see [Query Syntax and Method Syntax in LINQ](./query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
 <span data-ttu-id="51085-107">Tento příklad používá následující dokument XML: [ukázkový soubor XML: zákazníci a objednávky (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="51085-107">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
XElement custOrd = XElement.Load("CustomersOrders.xml");  
string csv =  
    (from el in custOrd.Element("Customers").Elements("Customer")  
    select  
        String.Format("{0},{1},{2},{3},{4},{5},{6},{7},{8},{9}{10}",  
            (string)el.Attribute("CustomerID"),  
            (string)el.Element("CompanyName"),  
            (string)el.Element("ContactName"),  
            (string)el.Element("ContactTitle"),  
            (string)el.Element("Phone"),  
            (string)el.Element("FullAddress").Element("Address"),  
            (string)el.Element("FullAddress").Element("City"),  
            (string)el.Element("FullAddress").Element("Region"),  
            (string)el.Element("FullAddress").Element("PostalCode"),  
            (string)el.Element("FullAddress").Element("Country"),  
            Environment.NewLine  
        )  
    )  
    .Aggregate(  
        new StringBuilder(),  
        (sb, s) => sb.Append(s),  
        sb => sb.ToString()  
    );  
Console.WriteLine(csv);  
```  
  
 <span data-ttu-id="51085-108">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="51085-108">This code produces the following output:</span></span>  
  
```output  
GREAL,Great Lakes Food Market,Howard Snyder,Marketing Manager,(503) 555-7555,2732 Baker Blvd.,Eugene,OR,97403,USA  
HUNGC,Hungry Coyote Import Store,Yoshi Latimer,Sales Representative,(503) 555-6874,City Center Plaza 516 Main St.,Elgin,OR,97827,USA  
LAZYK,Lazy K Kountry Store,John Steel,Marketing Manager,(509) 555-7969,12 Orchestra Terrace,Walla Walla,WA,99362,USA  
LETSS,Let's Stop N Shop,Jaime Yorres,Owner,(415) 555-5938,87 Polk St. Suite 5,San Francisco,CA,94117,USA  
```  
  
## <a name="see-also"></a><span data-ttu-id="51085-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="51085-109">See also</span></span>

- [<span data-ttu-id="51085-110">Projekce a transformace (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="51085-110">Projections and Transformations (LINQ to XML) (C#)</span></span>](how-to-work-with-dictionaries-using-linq-to-xml.md)
