---
title: 'Postupy: Spojit dvě kolekce (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: 82083a24da9a5356a8ff8e8430b61bb5d41f7c72
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253581"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a>Postupy: Spojit dvě kolekce (LINQ to XML) (C#)
Element nebo atribut v dokumentu XML může někdy odkazovat na jiný element nebo atribut. Například [ukázkový soubor XML: Dokument XML Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) obsahuje seznam zákazníků a seznam objednávek. Každý `Customer` prvek`CustomerID` obsahuje atribut. Každý `Order` prvek`CustomerID` obsahuje element. Element v každé objednávce odkazuje `CustomerID` na atribut v zákazníkovi. `CustomerID`  
  
 Ukázkový soubor [XSD v tématu: Zákazníci a objednávky](./sample-xsd-file-customers-and-orders1.md) obsahují XSD, které lze použít k ověření tohoto dokumentu. Používá `xs:key` funkce `CustomerID` a `xs:keyref` `Order` XSD k určení`Customer` toho, že atribut prvku je klíč, a k navázání vztahu mezi prvkem v jednotlivých prvcích a `CustomerID` atribut v každém `Customer`elementu. `CustomerID`  
  
 Pomocí můžete tuto relaci využít `join` pomocí klauzule. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]  
  
 Všimněte si, že protože není k dispozici žádný index, takové spojení bude mít špatný běhový výkon.  
  
 Podrobnější informace o `join`najdete v tématu [operace join (C#)](./join-operations.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad spojuje `Customer` prvky `Order` s prvky a generuje nový dokument `CompanyName` XML, který obsahuje prvek v objednávkách.  
  
 Před provedením dotazu v příkladu se ověří, že dokument vyhovuje schématu v [ukázkovém souboru XSD: Zákazníci a objednávky](./sample-xsd-file-customers-and-orders1.md). Tím se zajistí, že klauzule JOIN bude vždycky fungovat.  
  
 Tento dotaz nejprve načte všechny `Customer` prvky a pak je spojí `Order` s prvky. Vybere pouze objednávky pro zákazníky s `CustomerID` větší než "K". Potom projekty vytvoří nový `Order` prvek, který obsahuje informace o zákaznících v rámci jednotlivých objednávek.  
  
 V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
 V tomto příkladu se používá následující schéma XSD: [Ukázkový soubor XSD: Zákazníci a objednávky](./sample-xsd-file-customers-and-orders1.md).  
  
 Všimněte si, že připojení tímto způsobem nebude fungovat velmi dobře. Spojení se provádí pomocí lineárního hledání. Neexistují žádné zatřiďovací tabulky ani indexy, které by měly pomáhat s výkonem.  
  
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
  
 Tento kód generuje následující výstup:  
  
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
