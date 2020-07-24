---
title: Postup připojení dvou kolekcí (LINQ to XML) (C#)
description: Tento příklad jazyka C# spojuje prvky ve LINQ to XML s jinými prvky a generuje nový dokument XML.
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: 10792ed4907e778b41821c9b32574bd8fc0ab35f
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104993"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a><span data-ttu-id="a0544-103">Postup připojení dvou kolekcí (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="a0544-103">How to join two collections (LINQ to XML) (C#)</span></span>

<span data-ttu-id="a0544-104">Element nebo atribut v dokumentu XML může někdy odkazovat na jiný element nebo atribut.</span><span class="sxs-lookup"><span data-stu-id="a0544-104">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="a0544-105">Například [ukázkový soubor XML: zákazníci a objednávky (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) dokument XML obsahuje seznam zákazníků a seznam objednávek.</span><span class="sxs-lookup"><span data-stu-id="a0544-105">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="a0544-106">Každý `Customer` prvek obsahuje `CustomerID` atribut.</span><span class="sxs-lookup"><span data-stu-id="a0544-106">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="a0544-107">Každý `Order` prvek obsahuje `CustomerID` element.</span><span class="sxs-lookup"><span data-stu-id="a0544-107">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="a0544-108">`CustomerID`Element v každé objednávce odkazuje na `CustomerID` atribut v zákazníkovi.</span><span class="sxs-lookup"><span data-stu-id="a0544-108">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>

<span data-ttu-id="a0544-109">[Ukázkový soubor XSD: zákazníci a objednávky](./sample-xsd-file-customers-and-orders1.md) obsahují XSD, které lze použít k ověření tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a0544-109">The topic [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="a0544-110">Používá `xs:key` `xs:keyref` funkce a XSD k určení toho, že `CustomerID` atribut `Customer` prvku je klíč, a k navázání vztahu mezi `CustomerID` prvkem v jednotlivých `Order` prvcích a `CustomerID` atributem v každém `Customer` elementu.</span><span class="sxs-lookup"><span data-stu-id="a0544-110">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>

<span data-ttu-id="a0544-111">Pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] můžete tuto relaci využít pomocí `join` klauzule.</span><span class="sxs-lookup"><span data-stu-id="a0544-111">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can take advantage of this relationship by using the `join` clause.</span></span>

<span data-ttu-id="a0544-112">Vzhledem k tomu, že není k dispozici žádný index, takové připojení bude mít nedostatečný výkon za běhu.</span><span class="sxs-lookup"><span data-stu-id="a0544-112">Because there is no index available, such joining will have poor run-time performance.</span></span>

<span data-ttu-id="a0544-113">Podrobnější informace o `join` naleznete v tématu [operace join (C#)](./join-operations.md).</span><span class="sxs-lookup"><span data-stu-id="a0544-113">For more detailed information about `join`, see [Join Operations (C#)](./join-operations.md).</span></span>

## <a name="example"></a><span data-ttu-id="a0544-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0544-114">Example</span></span>

<span data-ttu-id="a0544-115">Následující příklad spojuje `Customer` prvky s `Order` prvky a generuje nový dokument XML, který obsahuje `CompanyName` prvek v objednávkách.</span><span class="sxs-lookup"><span data-stu-id="a0544-115">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>

<span data-ttu-id="a0544-116">Před provedením dotazu v příkladu se ověří, že dokument vyhovuje schématu v [ukázkovém souboru XSD: zákazníci a objednávky](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="a0544-116">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="a0544-117">Tím se zajistí, že klauzule JOIN bude vždycky fungovat.</span><span class="sxs-lookup"><span data-stu-id="a0544-117">This ensures that the join clause will always work.</span></span>

<span data-ttu-id="a0544-118">Tento dotaz nejprve načte všechny `Customer` prvky a pak je spojí s `Order` prvky.</span><span class="sxs-lookup"><span data-stu-id="a0544-118">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="a0544-119">Vybere pouze objednávky pro zákazníky s `CustomerID` větší než "K".</span><span class="sxs-lookup"><span data-stu-id="a0544-119">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="a0544-120">Potom projekty vytvoří nový `Order` prvek, který obsahuje informace o zákaznících v rámci jednotlivých objednávek.</span><span class="sxs-lookup"><span data-stu-id="a0544-120">It then projects a new `Order` element that contains the customer information within each order.</span></span>

<span data-ttu-id="a0544-121">Tento příklad používá následující dokument XML: [ukázkový soubor XML: zákazníci a objednávky (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="a0544-121">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>

<span data-ttu-id="a0544-122">V tomto příkladu se používá následující schéma XSD: [ukázkový soubor XSD: zákazníci a objednávky](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="a0544-122">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span>

<span data-ttu-id="a0544-123">Spojení tímto způsobem nebude fungovat dobře.</span><span class="sxs-lookup"><span data-stu-id="a0544-123">Joining in this fashion will not perform well.</span></span> <span data-ttu-id="a0544-124">Spojení se provádí pomocí lineárního hledání.</span><span class="sxs-lookup"><span data-stu-id="a0544-124">Joins are performed via a linear search.</span></span> <span data-ttu-id="a0544-125">Neexistují žádné zatřiďovací tabulky ani indexy, které by měly pomáhat s výkonem.</span><span class="sxs-lookup"><span data-stu-id="a0544-125">There are no hash tables or indexes to help with performance.</span></span>

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

<span data-ttu-id="a0544-126">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a0544-126">This code produces the following output:</span></span>

```output
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
