---
title: Postup řízení typu projekce (C#)
ms.date: 07/20/2015
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
ms.openlocfilehash: cb7c272fbe67c0700b5740691befc483993f4e29
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141351"
---
# <a name="how-to-control-the-type-of-a-projection-c"></a><span data-ttu-id="b5084-102">Postup řízení typu projekce (C#)</span><span class="sxs-lookup"><span data-stu-id="b5084-102">How to control the type of a projection (C#)</span></span>
<span data-ttu-id="b5084-103">Projekcí je proces pořízení jedné sady dat, její filtrování, změna jejího tvaru a dokonce i změna jejího typu.</span><span class="sxs-lookup"><span data-stu-id="b5084-103">Projection is the process of taking one set of data, filtering it, changing its shape, and even changing its type.</span></span> <span data-ttu-id="b5084-104">Většina výrazů dotazů provádí projekce.</span><span class="sxs-lookup"><span data-stu-id="b5084-104">Most query expressions perform projections.</span></span> <span data-ttu-id="b5084-105">Většina výrazů dotazů zobrazených v této části vyhodnocuje <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>, ale můžete řídit typ projekce pro vytváření kolekcí jiných typů.</span><span class="sxs-lookup"><span data-stu-id="b5084-105">Most of the query expressions shown in this section evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, but you can control the type of the projection to create collections of other types.</span></span> <span data-ttu-id="b5084-106">V tomto tématu se dozvíte, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="b5084-106">This topic shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5084-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="b5084-107">Example</span></span>  
 <span data-ttu-id="b5084-108">Následující příklad definuje nový typ `Customer`.</span><span class="sxs-lookup"><span data-stu-id="b5084-108">The following example defines a new type, `Customer`.</span></span> <span data-ttu-id="b5084-109">Výraz dotazu potom vytvoří instanci nových objektů `Customer` v klauzuli `Select`.</span><span class="sxs-lookup"><span data-stu-id="b5084-109">The query expression then instantiates new `Customer` objects in the `Select` clause.</span></span> <span data-ttu-id="b5084-110">To způsobí, že typ výrazu dotazu bude <xref:System.Collections.Generic.IEnumerable%601> `Customer`.</span><span class="sxs-lookup"><span data-stu-id="b5084-110">This causes the type of the query expression to be <xref:System.Collections.Generic.IEnumerable%601> of `Customer`.</span></span>  
  
 <span data-ttu-id="b5084-111">Tento příklad používá následující dokument XML: [ukázkový soubor XML: zákazníci a objednávky (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="b5084-111">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="b5084-112">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b5084-112">This code produces the following output:</span></span>  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="b5084-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5084-113">See also</span></span>

- <xref:System.Linq.Enumerable.Select%2A>
