---
title: 'Postupy: Transformace tvaru stromu XML (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 84b60854-48b2-452c-87f2-77d53e1d653a
ms.openlocfilehash: 067bf56b8dff994080ba78147d992b97a56867cb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61614996"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-visual-basic"></a>Postupy: Transformace tvaru stromu XML (Visual Basic)
*Tvar* formátu XML dokumentu odkazuje na jeho názvy elementů, názvy atributů a vlastnosti ve své hierarchii.  
  
 Někdy je nutné změnit tvar dokumentu XML. Například budete muset odeslat existující dokument XML do jiného systému, který vyžaduje jiný element a názvy atributů. Dokument, může projít, odstranění a přejmenování prvky jako povinné, ale pomocí funkční konstrukce výsledky v čitelnější a udržovatelný kód. Další informace o funkční konstrukce najdete v tématu [funkční konstrukce (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).  
  
 V prvním příkladu se změní uspořádání dokumentu XML. Komplexních prvků z jednoho umístění ve stromu přesunu do jiného.  
  
 Ve druhém příkladu v tomto tématu vytvoří dokument XML s obrazcem jiný než zdrojový dokument. Změní velká a malá písmena názvy elementů, přejmenuje některé prvky a ponechá některé prvky ze stromu zdrojového kódu z transformovaných stromu.  
  
## <a name="example"></a>Příklad  
 Následující kód změní tvaru souborů XML pomocí dotazu vložené výrazy.  
  
 Zdrojovém dokumentu XML v tomto příkladu obsahuje `Customers` element v rámci `Root` element, který obsahuje všechny zákazníky. Obsahuje taky `Orders` element v rámci `Root` element, který obsahuje všechny objednávky. Tento příklad vytvoří nový stromu XML, ve které jsou součástí objednávky pro každého zákazníka `Orders` element v rámci `Customer` elementu. Původní dokument obsahuje také `CustomerID` element v `Order` element; tento element budou odstraněny z znovu upravená dokumentu.  
  
 Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
```vb  
Dim co As XElement = XElement.Load("CustomersOrders.xml")  
Dim newCustOrd = _  
    <Root>  
        <%= From cust In co.<Customers>.<Customer> _  
            Select _  
            <Customer>  
                <%= cust.Attributes() %>  
                <%= cust.Elements() %>  
                <Orders>  
                    <%= From ord In co.<Orders>.<Order> _  
                        Where ord.<CustomerID>.Value = cust.@CustomerID _  
                        Select _  
                        <Order>  
                            <%= ord.Attributes() %>  
                            <%= ord.<EmployeeID> %>  
                            <%= ord.<OrderDate> %>  
                            <%= ord.<RequiredDate> %>  
                            <%= ord.<ShipInfo> %>  
                        </Order> _  
                    %>  
                </Orders>  
            </Customer> _  
        %>  
    </Root>  
Console.WriteLine(newCustOrd)  
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
  
 Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Typická nákupní objednávka (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
```vb  
Function ConvertAddress(ByVal add As XElement) As IEnumerable(Of XElement)  
    Dim fragment = New List(Of XElement)  
    fragment.Add(<NAME><%= add.<Name>.Value %></NAME>)  
    fragment.Add(<STREET><%= add.<Street>.Value %></STREET>)  
    fragment.Add(<CITY><%= add.<City>.Value %></CITY>)  
    fragment.Add(<ST><%= add.<State>.Value %></ST>)  
    fragment.Add(<POSTALCODE><%= add.<Zip>.Value %></POSTALCODE>)  
    fragment.Add(<COUNTRY><%= add.<Country>.Value %></COUNTRY>)  
    Return fragment  
End Function  
  
Sub Main()  
    Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
    Dim newPo As XElement = _  
        <PO>  
            <ID><%= po.@PurchaseOrderNumber %></ID>  
            <DATE><%= CDate(po.@OrderDate) %></DATE>  
            <%= _  
                ConvertAddress( _  
                (From el In po.<Address> _  
                Where el.@Type = "Shipping" _  
                Select el) _  
                .First() _  
                ) _  
            %>  
        </PO>  
    Console.WriteLine(newPo)  
End Sub  
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

- [Projekce a transformace (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
