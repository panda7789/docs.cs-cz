---
title: Jak se připojit dvě kolekce (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: a5044778bbfd9529faf5fe63c72076f6a973c815
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345862"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a><span data-ttu-id="0ca59-102">Jak se připojit dvě kolekce (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0ca59-102">How to join two collections (LINQ to XML) (C#)</span></span>

<span data-ttu-id="0ca59-103">Prvek nebo atribut v dokumentu XML může někdy odkazovat na jiný prvek nebo atribut.</span><span class="sxs-lookup"><span data-stu-id="0ca59-103">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="0ca59-104">Například [ukázkový dokument XML: Zákazníci a objednávky (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) obsahuje seznam zákazníků a seznam objednávek.</span><span class="sxs-lookup"><span data-stu-id="0ca59-104">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="0ca59-105">Každý `Customer` prvek `CustomerID` obsahuje atribut.</span><span class="sxs-lookup"><span data-stu-id="0ca59-105">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="0ca59-106">Každý `Order` prvek `CustomerID` obsahuje prvek.</span><span class="sxs-lookup"><span data-stu-id="0ca59-106">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="0ca59-107">Prvek `CustomerID` v každé objednávce `CustomerID` odkazuje na atribut v zákazníkovi.</span><span class="sxs-lookup"><span data-stu-id="0ca59-107">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>

<span data-ttu-id="0ca59-108">Téma [Ukázkový soubor XSD: Zákazníci a objednávky](./sample-xsd-file-customers-and-orders1.md) obsahuje xsd, které lze použít k ověření tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="0ca59-108">The topic [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="0ca59-109">Používá `xs:key` a `xs:keyref` funkce XSD k `CustomerID` vytvoření, že `Customer` atribut prvku je klíč a vytvořit `CustomerID` vztah `Order` mezi element `CustomerID` v `Customer` každém prvku a atribut v každém prvku.</span><span class="sxs-lookup"><span data-stu-id="0ca59-109">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>

<span data-ttu-id="0ca59-110">Pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]aplikace můžete tento vztah využít `join` pomocí klauzule.</span><span class="sxs-lookup"><span data-stu-id="0ca59-110">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can take advantage of this relationship by using the `join` clause.</span></span>

<span data-ttu-id="0ca59-111">Vzhledem k tomu, že není k dispozici žádný index, takové spojení bude mít nízký výkon za běhu.</span><span class="sxs-lookup"><span data-stu-id="0ca59-111">Because there is no index available, such joining will have poor run-time performance.</span></span>

<span data-ttu-id="0ca59-112">Podrobnější informace o `join` [tématu Operace spojení (C#)](./join-operations.md).</span><span class="sxs-lookup"><span data-stu-id="0ca59-112">For more detailed information about `join`, see [Join Operations (C#)](./join-operations.md).</span></span>

## <a name="example"></a><span data-ttu-id="0ca59-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="0ca59-113">Example</span></span>

<span data-ttu-id="0ca59-114">Následující příklad spojuje `Customer` prvky `Order` s prvky a generuje nový dokument `CompanyName` XML, který obsahuje prvek v objednávkách.</span><span class="sxs-lookup"><span data-stu-id="0ca59-114">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>

<span data-ttu-id="0ca59-115">Před provedením dotazu příklad ověří, zda dokument vyhovuje schématu v [ukázkovém souboru XSD: Zákazníci a objednávky](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="0ca59-115">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="0ca59-116">Tím je zajištěno, že klauzule join bude vždy fungovat.</span><span class="sxs-lookup"><span data-stu-id="0ca59-116">This ensures that the join clause will always work.</span></span>

<span data-ttu-id="0ca59-117">Tento dotaz nejprve `Customer` načte všechny prvky `Order` a potom je spojí s prvky.</span><span class="sxs-lookup"><span data-stu-id="0ca59-117">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="0ca59-118">Vybírá pouze objednávky pro zákazníky s `CustomerID` větším než "K".</span><span class="sxs-lookup"><span data-stu-id="0ca59-118">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="0ca59-119">Potom projekty `Order` nový prvek, který obsahuje informace o zákazníkovi v rámci každé objednávky.</span><span class="sxs-lookup"><span data-stu-id="0ca59-119">It then projects a new `Order` element that contains the customer information within each order.</span></span>

<span data-ttu-id="0ca59-120">Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML).](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)</span><span class="sxs-lookup"><span data-stu-id="0ca59-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>

<span data-ttu-id="0ca59-121">Tento příklad používá následující schéma XSD: [Ukázkový soubor XSD: Zákazníci a objednávky](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="0ca59-121">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span>

<span data-ttu-id="0ca59-122">Spojení tímto způsobem nebude fungovat dobře.</span><span class="sxs-lookup"><span data-stu-id="0ca59-122">Joining in this fashion will not perform well.</span></span> <span data-ttu-id="0ca59-123">Spojení se provádějí lineárním vyhledáváním.</span><span class="sxs-lookup"><span data-stu-id="0ca59-123">Joins are performed via a linear search.</span></span> <span data-ttu-id="0ca59-124">Neexistují žádné tabulky hash nebo indexy, které by pomohly s výkonem.</span><span class="sxs-lookup"><span data-stu-id="0ca59-124">There are no hash tables or indexes to help with performance.</span></span>

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

<span data-ttu-id="0ca59-125">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="0ca59-125">This code produces the following output:</span></span>

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
