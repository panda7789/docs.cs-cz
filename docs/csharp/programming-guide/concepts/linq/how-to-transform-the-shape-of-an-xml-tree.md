---
title: Jak transformovat tvar stromu XML (C#)
ms.date: 07/20/2015
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
ms.openlocfilehash: 91f91ed6fea5371fae2ce67a413f4825f37af6c3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347308"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-c"></a>Jak transformovat tvar stromu XML (C#)
*Tvar* dokumentu XML odkazuje na jeho názvy elementů, názvy atributů a charakteristiky jeho hierarchie.  
  
 Někdy budete muset změnit tvar dokumentu XML. Například může být nutné odeslat existující dokument XML do jiného systému, který vyžaduje různé názvy elementů a atributů. Můžete procházet dokumentem, odstraňovat a předávat prvky podle potřeby, ale použití funkční konstrukce má za následek čitelnější a udržovatelný kód. Další informace o konstrukci funkčnosti naleznete v tématu [funkční konstrukce (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).  
  
 První příklad změní organizaci dokumentu XML. Přesouvá komplexní prvky z jednoho umístění ve stromové struktuře do jiného.  
  
 Druhý příklad v tomto tématu vytvoří dokument XML s jiným tvarem, než zdrojový dokument. Změní velká a malá písmena názvů prvků, přejmenuje některé prvky a ponechá některé prvky ze zdrojového stromu z transformované stromové struktury.  
  
## <a name="example"></a>Příklad  
 Následující kód změní tvar souboru XML pomocí vložených výrazů dotazů.  
  
 Zdrojový dokument XML v tomto příkladu obsahuje element `Customers` pod prvkem `Root`, který obsahuje všechny zákazníky. Obsahuje také prvek `Orders` pod prvkem `Root`, který obsahuje všechny objednávky. Tento příklad vytvoří nový strom XML, ve kterém jsou objednávky pro každého zákazníka obsaženy v prvku `Orders` v rámci `Customer` elementu. Původní dokument obsahuje také prvek `CustomerID` v prvku `Order`; Tento prvek bude odebrán z dokumentu opětovného tvaru.  
  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: zákazníci a objednávky (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
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
 Tento příklad přejmenuje některé prvky a převede některé atributy na prvky.  
  
 Kód volá `ConvertAddress`, která vrací seznam objektů <xref:System.Xml.Linq.XElement>. Argumentem metody je dotaz, který určuje `Address` složitý prvek, kde `Type` atribut má hodnotu `"Shipping"`.  
  
 Tento příklad používá následující dokument XML: [vzorový soubor XML: typická nákupní objednávka (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
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
