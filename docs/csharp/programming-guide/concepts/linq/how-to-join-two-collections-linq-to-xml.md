---
title: "Postupy: připojení dvě kolekce (technologie LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9fdbd442e0974dfcf5183a237eecd94c4c925ee4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a>Postupy: připojení dvě kolekce (technologie LINQ to XML) (C#)
Elementu nebo atributu v dokumentu XML mohou někdy odkazovat na jiné elementu nebo atributu. Například [ukázkový soubor XML: Zákazníci a objednávky (technologie LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md) dokumentu XML obsahuje seznam zákazníků a seznam objednávky. Každý `Customer` obsahuje element `CustomerID` atribut. Každý `Order` obsahuje element `CustomerID` elementu. `CustomerID` Element v každé pořadí odkazuje `CustomerID` atribut v zákazníka.  
  
 Téma [ukázkový soubor XSD: Zákazníci a objednávky](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md) obsahuje XSD, který slouží k ověření tohoto dokumentu. Použije `xs:key` a `xs:keyref` funkce XSD zajistit, že `CustomerID` atribut `Customer` element je klíč a k vytvoření vztahu mezi `CustomerID` element v každé `Order` element a `CustomerID` atribut v každé `Customer` elementu.  
  
 S [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], můžete využít výhod této relace pomocí `join` klauzule.  
  
 Všimněte si, protože není k dispozici žádný index, takové připojení že běhový snížený výkon.  
  
 Podrobné informace o `join`, najdete v části [připojení operace (C#)](../../../../csharp/programming-guide/concepts/linq/join-operations.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad spojení `Customer` elementů `Order` prvky a vygeneruje nový dokument XML, který zahrnuje `CompanyName` element v objednávky.  
  
 Před provedením dotazu, příklad ověří, že dokument v souladu se schéma v [ukázkový soubor XSD: Zákazníci a objednávky](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md). Tím se zajistí, že bude vždy fungovat klauzuli join.  
  
 Tento dotaz nejprve načte všechny `Customer` prvky a potom připojí, aby `Order` elementy. Vybere pouze příkazy pro zákazníky s `CustomerID` větší než "K". Ji pak projekty novou `Order` elementu, který obsahuje informace o zákazníkovi v rámci každé pořadí.  
  
 Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: Zákazníci a objednávky (technologie LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
 Tento příklad používá následující schéma XSD: [ukázkový soubor XSD: Zákazníci a objednávky](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).  
  
 Všimněte si, že připojení tímto způsobem nebude provádět velmi dobře. Spojení se provádí prostřednictvím lineárního hledání. Neexistují žádné tabulky hash nebo indexy, které pomáhají s výkonem.  
  
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
 [Pokročilé techniky dotazu (technologie LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
