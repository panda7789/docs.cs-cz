---
title: 'Postupy: Spojení dvou kolekcí (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: fb158427afd59caea5eecdad29fa0a68686f6381
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667961"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a><span data-ttu-id="5614e-102">Postupy: Spojení dvou kolekcí (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="5614e-102">How to: Join Two Collections (LINQ to XML) (C#)</span></span>
<span data-ttu-id="5614e-103">Prvek nebo atribut v dokumentu XML mohou někdy odkazovat na jiné elementu nebo atributu.</span><span class="sxs-lookup"><span data-stu-id="5614e-103">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="5614e-104">Například [ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md) dokument XML obsahuje seznam zákazníků a seznam objednávek.</span><span class="sxs-lookup"><span data-stu-id="5614e-104">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="5614e-105">Každý `Customer` obsahuje element `CustomerID` atribut.</span><span class="sxs-lookup"><span data-stu-id="5614e-105">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="5614e-106">Každý `Order` obsahuje element `CustomerID` elementu.</span><span class="sxs-lookup"><span data-stu-id="5614e-106">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="5614e-107">`CustomerID` Element z každé objednávky odkazuje `CustomerID` atribut v zákazníka.</span><span class="sxs-lookup"><span data-stu-id="5614e-107">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>  
  
 <span data-ttu-id="5614e-108">Téma [ukázkový soubor XSD: Zákazníci a objednávky](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md) obsahuje XSD, který slouží k ověření tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="5614e-108">The topic [Sample XSD File: Customers and Orders](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="5614e-109">Používá `xs:key` a `xs:keyref` funkce XSD zajistit, že `CustomerID` atribut `Customer` element je klíč a k vytvoření vztahu mezi `CustomerID` element v každé `Order` elementu a `CustomerID` atributy v každém `Customer` elementu.</span><span class="sxs-lookup"><span data-stu-id="5614e-109">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>  
  
 <span data-ttu-id="5614e-110">S [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], pomocí můžete využít tuto relaci `join` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="5614e-110">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can take advantage of this relationship by using the `join` clause.</span></span>  
  
 <span data-ttu-id="5614e-111">Mějte na paměti, protože není k dispozici žádný index, tato připojení budou mít runtime nízký výkon.</span><span class="sxs-lookup"><span data-stu-id="5614e-111">Note that because there is no index available, such joining will have poor runtime performance.</span></span>  
  
 <span data-ttu-id="5614e-112">Podrobné informace o `join`, naleznete v tématu [operace Join (C#)](../../../../csharp/programming-guide/concepts/linq/join-operations.md).</span><span class="sxs-lookup"><span data-stu-id="5614e-112">For more detailed information about `join`, see [Join Operations (C#)](../../../../csharp/programming-guide/concepts/linq/join-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5614e-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="5614e-113">Example</span></span>  
 <span data-ttu-id="5614e-114">Následující příklad připojí `Customer` prvků, které mají `Order` prvky a vytvoří nový dokument XML, který zahrnuje `CompanyName` prvek objednávky.</span><span class="sxs-lookup"><span data-stu-id="5614e-114">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>  
  
 <span data-ttu-id="5614e-115">Před provedením dotazu, v příkladu ověřuje, že dokument vyhovuje schématu v [ukázkový soubor XSD: Zákazníci a objednávky](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="5614e-115">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="5614e-116">Tím se zajistí, že budou vždy fungovat klauzule join.</span><span class="sxs-lookup"><span data-stu-id="5614e-116">This ensures that the join clause will always work.</span></span>  
  
 <span data-ttu-id="5614e-117">Tento dotaz načte prvních všechny `Customer` prvky a poté je připojen `Order` prvky.</span><span class="sxs-lookup"><span data-stu-id="5614e-117">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="5614e-118">Vybere pouze příkazy pro zákazníky s `CustomerID` větší než "K".</span><span class="sxs-lookup"><span data-stu-id="5614e-118">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="5614e-119">To potom projekty nový `Order` element, který obsahuje informace o zákaznících v rámci každé objednávky.</span><span class="sxs-lookup"><span data-stu-id="5614e-119">It then projects a new `Order` element that contains the customer information within each order.</span></span>  
  
 <span data-ttu-id="5614e-120">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="5614e-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
 <span data-ttu-id="5614e-121">Tento příklad používá následující schéma XSD: [Ukázkový soubor XSD: Zákazníci a objednávky](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="5614e-121">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span></span>  
  
 <span data-ttu-id="5614e-122">Všimněte si, že připojení tímto způsobem nebude fungují velmi dobře.</span><span class="sxs-lookup"><span data-stu-id="5614e-122">Note that joining in this fashion will not perform very well.</span></span> <span data-ttu-id="5614e-123">Spojení se provádí prostřednictvím lineárního hledání.</span><span class="sxs-lookup"><span data-stu-id="5614e-123">Joins are performed via a linear search.</span></span> <span data-ttu-id="5614e-124">Neexistují žádné zatřiďovacích tabulek nebo indexy, které vám pomůžou s výkonem.</span><span class="sxs-lookup"><span data-stu-id="5614e-124">There are no hash tables or indexes to help with performance.</span></span>  
  
```csharp  
XmlSchemaSet schemas = new XmlSchemaSet();  
schemas.Add("", "CustomersOrders.xsd");  
  
Console.Write("Attempting to validate, ");  
XDocument custOrdDoc = XDocument.Load("CustomersOrders.xml");  
  
bool errors = false;  
custOrdDoc.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");  
  
if (!errors)  
{  
    // Join customers and orders, and create a new XML document with  
    // a different shape.  
  
    // The new document contains orders only for customers with a  
    // CustomerID > 'K'  
    XElement custOrd = custOrdDoc.Element("Root");  
    XElement newCustOrd = new XElement("Root",  
        from c in custOrd.Element("Customers").Elements("Customer")  
        join o in custOrd.Element("Orders").Elements("Order")  
                   on (string)c.Attribute("CustomerID") equals  
                      (string)o.Element("CustomerID")  
        where ((string)c.Attribute("CustomerID")).CompareTo("K") > 0  
        select new XElement("Order",  
            new XElement("CustomerID", (string)c.Attribute("CustomerID")),  
            new XElement("CompanyName", (string)c.Element("CompanyName")),  
            new XElement("ContactName", (string)c.Element("ContactName")),  
            new XElement("EmployeeID", (string)o.Element("EmployeeID")),  
            new XElement("OrderDate", (DateTime)o.Element("OrderDate"))  
        )  
    );  
    Console.WriteLine(newCustOrd);  
}  
```  
  
 <span data-ttu-id="5614e-125">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="5614e-125">This code produces the following output:</span></span>  
  
```  
Attempting to validate, custOrdDoc validated  
<Root>  
  <Order>  
    <CustomerID>LAZYK</CustomerID>  
    <CompanyName>Lazy K Kountry Store</CompanyName>  
    <ContactName>John Steel</ContactName>  
    <EmployeeID>1</EmployeeID>  
    <OrderDate>1997-03-21T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LAZYK</CustomerID>  
    <CompanyName>Lazy K Kountry Store</CompanyName>  
    <ContactName>John Steel</ContactName>  
    <EmployeeID>8</EmployeeID>  
    <OrderDate>1997-05-22T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>1</EmployeeID>  
    <OrderDate>1997-06-25T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>8</EmployeeID>  
    <OrderDate>1997-10-27T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>6</EmployeeID>  
    <OrderDate>1997-11-10T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>4</EmployeeID>  
    <OrderDate>1998-02-12T00:00:00</OrderDate>  
  </Order>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5614e-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5614e-126">See also</span></span>

- [<span data-ttu-id="5614e-127">Pokročilé techniky dotazování (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="5614e-127">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
