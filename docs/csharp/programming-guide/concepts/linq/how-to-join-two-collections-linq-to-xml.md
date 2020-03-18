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
# <a name="how-to-join-two-collections-linq-to-xml-c"></a>Jak se připojit dvě kolekce (LINQ do XML) (C#)

Prvek nebo atribut v dokumentu XML může někdy odkazovat na jiný prvek nebo atribut. Například [ukázkový dokument XML: Zákazníci a objednávky (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) obsahuje seznam zákazníků a seznam objednávek. Každý `Customer` prvek `CustomerID` obsahuje atribut. Každý `Order` prvek `CustomerID` obsahuje prvek. Prvek `CustomerID` v každé objednávce `CustomerID` odkazuje na atribut v zákazníkovi.

Téma [Ukázkový soubor XSD: Zákazníci a objednávky](./sample-xsd-file-customers-and-orders1.md) obsahuje xsd, které lze použít k ověření tohoto dokumentu. Používá `xs:key` a `xs:keyref` funkce XSD k `CustomerID` vytvoření, že `Customer` atribut prvku je klíč a vytvořit `CustomerID` vztah `Order` mezi element `CustomerID` v `Customer` každém prvku a atribut v každém prvku.

Pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]aplikace můžete tento vztah využít `join` pomocí klauzule.

Vzhledem k tomu, že není k dispozici žádný index, takové spojení bude mít nízký výkon za běhu.

Podrobnější informace o `join` [tématu Operace spojení (C#)](./join-operations.md).

## <a name="example"></a>Příklad

Následující příklad spojuje `Customer` prvky `Order` s prvky a generuje nový dokument `CompanyName` XML, který obsahuje prvek v objednávkách.

Před provedením dotazu příklad ověří, zda dokument vyhovuje schématu v [ukázkovém souboru XSD: Zákazníci a objednávky](./sample-xsd-file-customers-and-orders1.md). Tím je zajištěno, že klauzule join bude vždy fungovat.

Tento dotaz nejprve `Customer` načte všechny prvky `Order` a potom je spojí s prvky. Vybírá pouze objednávky pro zákazníky s `CustomerID` větším než "K". Potom projekty `Order` nový prvek, který obsahuje informace o zákazníkovi v rámci každé objednávky.

Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML).](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)

Tento příklad používá následující schéma XSD: [Ukázkový soubor XSD: Zákazníci a objednávky](./sample-xsd-file-customers-and-orders1.md).

Spojení tímto způsobem nebude fungovat dobře. Spojení se provádějí lineárním vyhledáváním. Neexistují žádné tabulky hash nebo indexy, které by pomohly s výkonem.

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

Výsledkem tohoto kódu je následující výstup:

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
