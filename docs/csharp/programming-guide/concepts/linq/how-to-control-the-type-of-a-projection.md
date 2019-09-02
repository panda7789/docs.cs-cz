---
title: 'Postupy: Řízení typu projekce (C#)'
ms.date: 07/20/2015
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
ms.openlocfilehash: a44f7616beba3e07f6e44cc279c67468abc779e3
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204089"
---
# <a name="how-to-control-the-type-of-a-projection-c"></a><span data-ttu-id="22459-102">Postupy: Řízení typu projekce (C#)</span><span class="sxs-lookup"><span data-stu-id="22459-102">How to: Control the Type of a Projection (C#)</span></span>
<span data-ttu-id="22459-103">Projekcí je proces pořízení jedné sady dat, její filtrování, změna jejího tvaru a dokonce i změna jejího typu.</span><span class="sxs-lookup"><span data-stu-id="22459-103">Projection is the process of taking one set of data, filtering it, changing its shape, and even changing its type.</span></span> <span data-ttu-id="22459-104">Většina výrazů dotazů provádí projekce.</span><span class="sxs-lookup"><span data-stu-id="22459-104">Most query expressions perform projections.</span></span> <span data-ttu-id="22459-105">Většina výrazů dotazu zobrazených v této části je <xref:System.Collections.Generic.IEnumerable%601> vyhodnocena <xref:System.Xml.Linq.XElement>jako z, ale můžete řídit typ projekce pro vytváření kolekcí jiných typů.</span><span class="sxs-lookup"><span data-stu-id="22459-105">Most of the query expressions shown in this section evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, but you can control the type of the projection to create collections of other types.</span></span> <span data-ttu-id="22459-106">V tomto tématu se dozvíte, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="22459-106">This topic shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22459-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="22459-107">Example</span></span>  
 <span data-ttu-id="22459-108">Následující příklad definuje nový typ, `Customer`.</span><span class="sxs-lookup"><span data-stu-id="22459-108">The following example defines a new type, `Customer`.</span></span> <span data-ttu-id="22459-109">Výraz dotazu pak vytvoří instanci nových `Customer` objektů `Select` v klauzuli.</span><span class="sxs-lookup"><span data-stu-id="22459-109">The query expression then instantiates new `Customer` objects in the `Select` clause.</span></span> <span data-ttu-id="22459-110">To způsobí, že typ výrazu dotazu bude <xref:System.Collections.Generic.IEnumerable%601>. `Customer`</span><span class="sxs-lookup"><span data-stu-id="22459-110">This causes the type of the query expression to be <xref:System.Collections.Generic.IEnumerable%601> of `Customer`.</span></span>  
  
 <span data-ttu-id="22459-111">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="22459-111">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="22459-112">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="22459-112">This code produces the following output:</span></span>  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="22459-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="22459-113">See also</span></span>

- <xref:System.Linq.Enumerable.Select%2A>
