---
title: 'Postupy: Řízení typu projekce (C#)'
ms.date: 07/20/2015
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
ms.openlocfilehash: 020e847545d62709da091a9645d39f8fd0a5ce25
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561020"
---
# <a name="how-to-control-the-type-of-a-projection-c"></a><span data-ttu-id="0ff52-102">Postupy: Řízení typu projekce (C#)</span><span class="sxs-lookup"><span data-stu-id="0ff52-102">How to: Control the Type of a Projection (C#)</span></span>
<span data-ttu-id="0ff52-103">Projekce je proces trvá jednu sadu dat, filtrovat, změně jeho tvar a změnu i jejího typu.</span><span class="sxs-lookup"><span data-stu-id="0ff52-103">Projection is the process of taking one set of data, filtering it, changing its shape, and even changing its type.</span></span> <span data-ttu-id="0ff52-104">Většina výrazy dotazu provést sami.</span><span class="sxs-lookup"><span data-stu-id="0ff52-104">Most query expressions perform projections.</span></span> <span data-ttu-id="0ff52-105">Většina výrazy dotazu uvedené v této části vyhodnotit <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, ale můžete řídit typ projekce k vytvoření kolekce jiných typů.</span><span class="sxs-lookup"><span data-stu-id="0ff52-105">Most of the query expressions shown in this section evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, but you can control the type of the projection to create collections of other types.</span></span> <span data-ttu-id="0ff52-106">Toto téma ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="0ff52-106">This topic shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ff52-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="0ff52-107">Example</span></span>  
 <span data-ttu-id="0ff52-108">Následující příklad definuje nový typ `Customer`.</span><span class="sxs-lookup"><span data-stu-id="0ff52-108">The following example defines a new type, `Customer`.</span></span> <span data-ttu-id="0ff52-109">Výraz dotazu poté vytvoří nový `Customer` objekty v `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="0ff52-109">The query expression then instantiates new `Customer` objects in the `Select` clause.</span></span> <span data-ttu-id="0ff52-110">To způsobí, že typ výrazu dotazu bude <xref:System.Collections.Generic.IEnumerable%601> z `Customer`.</span><span class="sxs-lookup"><span data-stu-id="0ff52-110">This causes the type of the query expression to be <xref:System.Collections.Generic.IEnumerable%601> of `Customer`.</span></span>  
  
 <span data-ttu-id="0ff52-111">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="0ff52-111">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="0ff52-112">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="0ff52-112">This code produces the following output:</span></span>  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="0ff52-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0ff52-113">See also</span></span>

- <xref:System.Linq.Enumerable.Select%2A>
- [<span data-ttu-id="0ff52-114">Projekce a transformace (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0ff52-114">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
