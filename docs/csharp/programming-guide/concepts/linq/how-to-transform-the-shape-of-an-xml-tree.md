---
title: 'Postupy: Transformace tvaru stromu XML (C#)'
ms.date: 07/20/2015
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
ms.openlocfilehash: 535f528d347e0c72ddaaab74ea78b47993a873a5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701707"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-c"></a>Postupy: Transformace tvaru stromu XML (C#)
*Tvar* formátu XML dokumentu odkazuje na jeho názvy elementů, názvy atributů a vlastnosti ve své hierarchii.  
  
 Někdy je nutné změnit tvar dokumentu XML. Například budete muset odeslat existující dokument XML do jiného systému, který vyžaduje jiný element a názvy atributů. Dokument, může projít, odstranění a přejmenování prvky jako povinné, ale pomocí funkční konstrukce výsledky v čitelnější a udržovatelný kód. Další informace o funkční konstrukce najdete v tématu [funkční konstrukce (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).  
  
 V prvním příkladu se změní uspořádání dokumentu XML. Komplexních prvků z jednoho umístění ve stromu přesunu do jiného.  
  
 Ve druhém příkladu v tomto tématu vytvoří dokument XML s obrazcem jiný než zdrojový dokument. Změní velká a malá písmena názvy elementů, přejmenuje některé prvky a ponechá některé prvky ze stromu zdrojového kódu z transformovaných stromu.  
  
## <a name="example"></a>Příklad  
 Následující kód změní tvaru souborů XML pomocí dotazu vložené výrazy.  
  
 Zdrojovém dokumentu XML v tomto příkladu obsahuje `Customers` element v rámci `Root` element, který obsahuje všechny zákazníky. Obsahuje taky `Orders` element v rámci `Root` element, který obsahuje všechny objednávky. Tento příklad vytvoří nový stromu XML, ve které jsou součástí objednávky pro každého zákazníka `Orders` element v rámci `Customer` elementu. Původní dokument obsahuje také `CustomerID` element v `Order` element; tento element budou odstraněny z znovu upravená dokumentu.  
  
 Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
```csharp  
XElement co = XElement.Load("CustomersOrders.xml");  
XElement newCustOrd =  
    new XElement("Root",  
        from cust in co.Element("Customers").Elements("Customer")  
        select new XElement("Customer",  
            cust.Attributes(),  
            cust.Elements(),  
            new XElement("Orders",  
                from ord in co.Element("Orders").Elements("Order")  
                where (string)ord.Element("CustomerID") == (string)cust.Attribute("CustomerID")  
                select new XElement("Order",  
                    ord.Attributes(),  
                    ord.Element("EmployeeID"),  
                    ord.Element("OrderDate"),  
                    ord.Element("RequiredDate"),  
                    ord.Element("ShipInfo")  
                )  
            )  
        )  
    );  
Console.WriteLine(newCustOrd);  
```  
  
 Tento kód vytvoří následující výstup:  
  
```xml  
<Root>  
  <Customer CustomerID="GREAL">  
    <CompanyName>Great Lakes Food Market</CompanyName>  
    <ContactName>Howard Snyder</ContactName>  
    <ContactTitle>Marketing Manager</ContactTitle>  
    <Phone>(503) 555-7555</Phone>  
    <FullAddress>  
      <Address>2732 Baker Blvd.</Address>  
      <City>Eugene</City>  
      <Region>OR</Region>  
      <PostalCode>97403</PostalCode>  
      <Country>USA</Country>  
    </FullAddress>  
    <Orders />  
  </Customer>  
  <Customer CustomerID="HUNGC">  
    <CompanyName>Hungry Coyote Import Store</CompanyName>  
    <ContactName>Yoshi Latimer</ContactName>  
    <ContactTitle>Sales Representative</ContactTitle>  
    <Phone>(503) 555-6874</Phone>  
    <Fax>(503) 555-2376</Fax>  
    <FullAddress>  
      <Address>City Center Plaza 516 Main St.</Address>  
      <City>Elgin</City>  
      <Region>OR</Region>  
      <PostalCode>97827</PostalCode>  
      <Country>USA</Country>  
    </FullAddress>  
    <Orders />  
  </Customer>  
  . . .  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad přejmenuje některé prvky a převede některé atributy elementů.  
  
 Kód volá `ConvertAddress`, který vrátí seznam hodnot <xref:System.Xml.Linq.XElement> objekty. Argument k metodě je dotaz, který určuje `Address` komplexních prvků kde `Type` atribut má hodnotu `"Shipping"`.  
  
 Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Typická nákupní objednávka (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
```csharp  
static IEnumerable<XElement> ConvertAddress(XElement add)  
{  
    List<XElement> fragment = new List<XElement>() {  
        new XElement("NAME", (string)add.Element("Name")),  
        new XElement("STREET", (string)add.Element("Street")),  
        new XElement("CITY", (string)add.Element("City")),  
        new XElement("ST", (string)add.Element("State")),  
        new XElement("POSTALCODE", (string)add.Element("Zip")),  
        new XElement("COUNTRY", (string)add.Element("Country"))  
    };  
    return fragment;  
}  
  
static void Main(string[] args)  
{  
    XElement po = XElement.Load("PurchaseOrder.xml");  
    XElement newPo = new XElement("PO",  
        new XElement("ID", (string)po.Attribute("PurchaseOrderNumber")),  
        new XElement("DATE", (DateTime)po.Attribute("OrderDate")),  
        ConvertAddress(  
            (from el in po.Elements("Address")  
            where (string)el.Attribute("Type") == "Shipping"  
            select el)  
            .First()  
        )  
    );  
    Console.WriteLine(newPo);  
}  
```  
  
 Tento kód vytvoří následující výstup:  
  
```xml  
<PO>  
  <ID>99503</ID>  
  <DATE>1999-10-20T00:00:00</DATE>  
  <NAME>Ellen Adams</NAME>  
  <STREET>123 Maple Street</STREET>  
  <CITY>Mill Valley</CITY>  
  <ST>CA</ST>  
  <POSTALCODE>10999</POSTALCODE>  
  <COUNTRY>USA</COUNTRY>  
</PO>  
```  
  
## <a name="see-also"></a>Viz také:

- [Projekce a transformace (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
