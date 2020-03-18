---
title: Jak řídit typ projekce (C#)
ms.date: 07/20/2015
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
ms.openlocfilehash: cb7c272fbe67c0700b5740691befc483993f4e29
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141351"
---
# <a name="how-to-control-the-type-of-a-projection-c"></a>Jak řídit typ projekce (C#)
Projekce je proces přijímání jedné sady dat, filtrování, změny tvaru a dokonce i změny jejího typu. Většina výrazů dotazu provádí projekce. Většina výrazů dotazu zobrazených <xref:System.Collections.Generic.IEnumerable%601> v <xref:System.Xml.Linq.XElement>této části vyhodnocuje do aplikace , ale můžete řídit typ projekce a vytvářet kolekce jiných typů. Toto téma ukazuje, jak to udělat.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje nový typ `Customer`. Výraz dotazu pak konkretizovat nové `Customer` objekty v klauzuli. `Select` To způsobí, že typ výrazu `Customer`dotazu být <xref:System.Collections.Generic.IEnumerable%601> .  
  
 Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML).](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)  
  
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
