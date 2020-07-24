---
title: Postup řízení typu projekce (C#)
description: Přečtěte si o tom, jak řídit typ projekce v LINQ v jazyce C# a vytvořit kolekce jiných typů než IEnumerable <T> typu XElement.
ms.date: 07/20/2015
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
ms.openlocfilehash: 32b019b5e1574e7160b4dce5fb0322caa3c1ca71
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103347"
---
# <a name="how-to-control-the-type-of-a-projection-c"></a>Postup řízení typu projekce (C#)
Projekcí je proces pořízení jedné sady dat, její filtrování, změna jejího tvaru a dokonce i změna jejího typu. Většina výrazů dotazů provádí projekce. Většina výrazů dotazu zobrazených v této části je vyhodnocena jako <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> , ale můžete řídit typ projekce pro vytváření kolekcí jiných typů. V tomto tématu se dozvíte, jak to provést.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje nový typ, `Customer` . Výraz dotazu pak vytvoří instanci nových `Customer` objektů v `Select` klauzuli. To způsobí, že typ výrazu dotazu bude <xref:System.Collections.Generic.IEnumerable%601> `Customer` .  
  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: zákazníci a objednávky (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
```csharp  
public class Customer  
{  
    private string customerID;  
    public string CustomerID{ get{return customerID;} set{customerID = value;}}  
  
    private string companyName;  
    public string CompanyName{ get{return companyName;} set{companyName = value;}}  
  
    private string contactName;  
    public string ContactName { get{return contactName;} set{contactName = value;}}  
  
    public Customer(string customerID, string companyName, string contactName)  
    {  
        CustomerID = customerID;  
        CompanyName = companyName;  
        ContactName = contactName;  
    }  
  
    public override string ToString()  
    {  
        return $"{this.customerID}:{this.companyName}:{this.contactName}";
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        XElement custOrd = XElement.Load("CustomersOrders.xml");  
        IEnumerable<Customer> custList =  
            from el in custOrd.Element("Customers").Elements("Customer")  
            select new Customer(  
                (string)el.Attribute("CustomerID"),  
                (string)el.Element("CompanyName"),  
                (string)el.Element("ContactName")  
            );  
        foreach (Customer cust in custList)  
            Console.WriteLine(cust);  
    }  
}  
```  
  
 Výsledkem tohoto kódu je následující výstup:  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq.Enumerable.Select%2A>
