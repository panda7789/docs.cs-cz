---
title: 'Postupy: spojení dvou kolekcí (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: 00db2decfb8595c32e86f76c8aa139d91e75d112
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43513527"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a>Postupy: spojení dvou kolekcí (LINQ to XML) (C#)
Prvek nebo atribut v dokumentu XML mohou někdy odkazovat na jiné elementu nebo atributu. Například [ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md) dokument XML obsahuje seznam zákazníků a seznam objednávek. Každý `Customer` obsahuje element `CustomerID` atribut. Každý `Order` obsahuje element `CustomerID` elementu. `CustomerID` Element z každé objednávky odkazuje `CustomerID` atribut v zákazníka.  
  
 Téma [ukázkový soubor XSD: Zákazníci a objednávky](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md) obsahuje XSD, který slouží k ověření tohoto dokumentu. Používá `xs:key` a `xs:keyref` funkce XSD zajistit, že `CustomerID` atribut `Customer` element je klíč a k vytvoření vztahu mezi `CustomerID` element v každé `Order` elementu a `CustomerID` atributy v každém `Customer` elementu.  
  
 S [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], pomocí můžete využít tuto relaci `join` klauzuli.  
  
 Mějte na paměti, protože není k dispozici žádný index, tato připojení budou mít runtime nízký výkon.  
  
 Podrobné informace o `join`, naleznete v tématu [operace Join (C#)](../../../../csharp/programming-guide/concepts/linq/join-operations.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad připojí `Customer` prvků, které mají `Order` prvky a vytvoří nový dokument XML, který zahrnuje `CompanyName` prvek objednávky.  
  
 Před provedením dotazu, v příkladu ověřuje, že dokument vyhovuje schématu v [ukázkový soubor XSD: Zákazníci a objednávky](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md). Tím se zajistí, že budou vždy fungovat klauzule join.  
  
 Tento dotaz načte prvních všechny `Customer` prvky a poté je připojen `Order` prvky. Vybere pouze příkazy pro zákazníky s `CustomerID` větší než "K". To potom projekty nový `Order` element, který obsahuje informace o zákaznících v rámci každé objednávky.  
  
 Tento příklad používá následujícího dokumentu XML: [ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
 Tento příklad používá následující schéma XSD: [ukázkový soubor XSD: Zákazníci a objednávky](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).  
  
 Všimněte si, že připojení tímto způsobem nebude fungují velmi dobře. Spojení se provádí prostřednictvím lineárního hledání. Neexistují žádné zatřiďovacích tabulek nebo indexy, které vám pomůžou s výkonem.  
  
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
  
 Tento kód vytvoří následující výstup:  
  
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
  
## <a name="see-also"></a>Viz také

- [Pokročilé techniky dotazování (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
