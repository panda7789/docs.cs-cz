---
title: Postup připojení dvou kolekcí (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: a5044778bbfd9529faf5fe63c72076f6a973c815
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345862"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a>Postup připojení dvou kolekcí (LINQ to XML) (C#)

Element nebo atribut v dokumentu XML může někdy odkazovat na jiný element nebo atribut. Například [ukázkový soubor XML: zákazníci a objednávky (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) dokument XML obsahuje seznam zákazníků a seznam objednávek. Každý prvek `Customer` obsahuje atribut `CustomerID`. Každý prvek `Order` obsahuje prvek `CustomerID`. Prvek `CustomerID` v každé objednávce odkazuje na atribut `CustomerID` zákazníka.

[Ukázkový soubor XSD: zákazníci a objednávky](./sample-xsd-file-customers-and-orders1.md) obsahují XSD, které lze použít k ověření tohoto dokumentu. Používá funkce `xs:key` a `xs:keyref` XSD k určení toho, že atribut `CustomerID` elementu `Customer` je klíč a k navázání vztahu mezi `CustomerID` prvkem v každém `Order` elementu a atributem `CustomerID` v každém prvku `Customer`.

Pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]můžete využít výhod tohoto vztahu pomocí klauzule `join`.

Vzhledem k tomu, že není k dispozici žádný index, takové připojení bude mít nedostatečný výkon za běhu.

Podrobnější informace o `join`naleznete v tématu [Join OperationsC#()](./join-operations.md).

## <a name="example"></a>Příklad

Následující příklad spojuje prvky `Customer` do `Order` prvků a generuje nový dokument XML, který obsahuje prvek `CompanyName` v objednávkách.

Před provedením dotazu v příkladu se ověří, že dokument vyhovuje schématu v [ukázkovém souboru XSD: zákazníci a objednávky](./sample-xsd-file-customers-and-orders1.md). Tím se zajistí, že klauzule JOIN bude vždycky fungovat.

Tento dotaz nejprve načte všechny prvky `Customer` a pak je připojí k prvkům `Order`. Vybere pouze objednávky zákazníků s `CustomerID` větší než K. Potom projekty vytvoří nový prvek `Order`, který obsahuje informace o zákaznících v rámci jednotlivých objednávek.

Tento příklad používá následující dokument XML: [ukázkový soubor XML: zákazníci a objednávky (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).

V tomto příkladu se používá následující schéma XSD: [ukázkový soubor XSD: zákazníci a objednávky](./sample-xsd-file-customers-and-orders1.md).

Spojení tímto způsobem nebude fungovat dobře. Spojení se provádí pomocí lineárního hledání. Neexistují žádné zatřiďovací tabulky ani indexy, které by měly pomáhat s výkonem.

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
