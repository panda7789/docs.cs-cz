---
title: Transformace tvaru stromu XML (C#)
ms.date: 07/20/2015
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
ms.openlocfilehash: 91f91ed6fea5371fae2ce67a413f4825f37af6c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347308"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-c"></a>Transformace tvaru stromu XML (C#)
*Obrazec* dokumentu XML odkazuje na jeho názvy prvků, názvy atributů a charakteristiky jeho hierarchie.  
  
 Někdy budete muset změnit tvar dokumentu XML. Může být například pravděpodobně možné odeslat existující dokument XML do jiného systému, který vyžaduje různé názvy prvků a atributů. Můžete projít dokument, odstranění a přejmenování prvků podle potřeby, ale pomocí funkční konstrukce má za následek čitelnější a udržovatelný kód. Další informace o funkční konstrukci naleznete v [tématu Funkční konstrukce (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).  
  
 První příklad změní uspořádání dokumentu XML. Přesune složité prvky z jednoho umístění ve stromu do jiného.  
  
 Druhý příklad v tomto tématu vytvoří dokument XML s jiným obrazcem než zdrojový dokument. Změní velikost písmen názvů prvků, přejmenuje některé prvky a ponechá některé prvky ze zdrojového stromu z transformovaného stromu.  
  
## <a name="example"></a>Příklad  
 Následující kód změní obrazec souboru XML pomocí vložených výrazů dotazu.  
  
 Zdrojový dokument XML v tomto `Customers` příkladu `Root` obsahuje prvek pod elementem, který obsahuje všechny zákazníky. Obsahuje také `Orders` prvek pod `Root` element, který obsahuje všechny objednávky. Tento příklad vytvoří nový strom XML, ve kterém jsou `Orders` objednávky `Customer` pro každého zákazníka obsaženy v elementu v rámci prvku. Původní dokument také `CustomerID` obsahuje prvek `Order` v elementu; tento prvek bude odebrán z přetvarovaného dokumentu.  
  
 Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML).](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)  
  
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
  
 Výsledkem tohoto kódu je následující výstup:  
  
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
 Tento příklad přejmenuje některé prvky a převede některé atributy na elementy.  
  
 Volání `ConvertAddress`kódu , který vrací <xref:System.Xml.Linq.XElement> seznam objektů. Argument metody je dotaz, který určuje `Address` komplexní prvek, `Type` kde má `"Shipping"`atribut hodnotu .  
  
 Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Typický nákupní objednávka (LINQ to XML).](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)  
  
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
  
 Výsledkem tohoto kódu je následující výstup:  
  
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
