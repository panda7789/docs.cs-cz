---
title: 'Postupy: Spojení dvou kolekcí (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 5a5758d4-906b-4285-908d-5b930db192e6
ms.openlocfilehash: dc3cfd19d990fa81e00f4781cb15bf07eb9a80ea
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398048"
---
# <a name="how-to-join-two-collections-linq-to-xml-visual-basic"></a>Postupy: spojení dvou kolekcí (LINQ to XML) (Visual Basic)
Element nebo atribut v dokumentu XML může někdy odkazovat na jiný element nebo atribut. Například [ukázkový soubor XML: zákazníci a objednávky (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md) dokument XML obsahuje seznam zákazníků a seznam objednávek. Každý `Customer` prvek obsahuje `CustomerID` atribut. Každý `Order` prvek obsahuje `CustomerID` element. `CustomerID`Element v každé objednávce odkazuje na `CustomerID` atribut v zákazníkovi.  
  
 [Ukázkový soubor XSD: zákazníci a objednávky](sample-xsd-file-customers-and-orders.md) obsahují XSD, které lze použít k ověření tohoto dokumentu. Používá `xs:key` `xs:keyref` funkce a XSD k určení toho, že `CustomerID` atribut `Customer` prvku je klíč, a k navázání vztahu mezi `CustomerID` prvkem v jednotlivých `Order` prvcích a `CustomerID` atributem v každém `Customer` elementu.  
  
 Pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] můžete tuto relaci využít pomocí `Join` klauzule.  
  
 Všimněte si, že protože není k dispozici žádný index, takové spojení bude mít špatný běhový výkon.  
  
 Podrobnější informace o `Join` najdete v tématu [operace Join (Visual Basic)](join-operations.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad spojuje `Customer` prvky s `Order` prvky a generuje nový dokument XML, který obsahuje `CompanyName` prvek v objednávkách.  
  
 Před provedením dotazu v příkladu se ověří, že dokument vyhovuje schématu v [ukázkovém souboru XSD: zákazníci a objednávky](sample-xsd-file-customers-and-orders.md). Tím se zajistí, že klauzule JOIN bude vždycky fungovat.  
  
 Tento dotaz nejprve načte všechny `Customer` prvky a pak je spojí s `Order` prvky. Vybere pouze objednávky pro zákazníky s `CustomerID` větší než "K". Potom projekty vytvoří nový `Order` prvek, který obsahuje informace o zákaznících v rámci jednotlivých objednávek.  
  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: zákazníci a objednávky (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
 V tomto příkladu se používá následující schéma XSD: [ukázkový soubor XSD: zákazníci a objednávky](sample-xsd-file-customers-and-orders.md).  
  
 Všimněte si, že připojení tímto způsobem nebude fungovat velmi dobře. Spojení se provádí pomocí lineárního hledání. Neexistují žádné zatřiďovací tabulky ani indexy, které by měly pomáhat s výkonem.  
  
```vb  
Public Class Program  
    Public Shared errors As Boolean = False  
  
    Public Shared Function LamValidEvent(ByVal o As Object, _  
                 ByVal e As ValidationEventArgs) As Boolean  
        Console.WriteLine("{0}", e.Message)  
        errors = True  
    End Function  
  
    Shared Sub Main()  
        Dim schemas As New XmlSchemaSet()  
        schemas.Add("", "CustomersOrders.xsd")  
  
        Console.Write("Attempting to validate, ")  
        Dim custOrdDoc As XDocument = XDocument.Load("CustomersOrders.xml")  
  
        custOrdDoc.Validate(schemas, Function(o, e) LamValidEvent(0, e))  
        If errors Then  
            Console.WriteLine("custOrdDoc did not validate")  
        Else  
            Console.WriteLine("custOrdDoc validated")  
        End If  
  
        If Not errors Then  
            'Join customers and orders, and create a new XML document with  
            ' a different shape.  
            'The new document contains orders only for customers with a  
            ' CustomerID > 'K'.  
            Dim custOrd As XElement = custOrdDoc.<Root>.FirstOrDefault  
            Dim newCustOrd As XElement = _  
                <Root>  
                    <%= From c In custOrd.<Customers>.<Customer> _  
                        Join o In custOrd.<Orders>.<Order> _  
                        On c.@CustomerID Equals o.<CustomerID>.Value _  
                        Where c.@CustomerID.CompareTo("K") > 0 _  
                        Select _  
                        <Order>  
                            <CustomerID><%= c.@CustomerID %></CustomerID>  
                            <%= c.<CompanyName> %>  
                            <%= c.<ContactName> %>  
                            <%= o.<EmployeeID> %>  
                            <%= o.<OrderDate> %>  
                        </Order> _  
                    %>  
                </Root>  
            Console.WriteLine(newCustOrd)  
        End If  
    End Sub  
End Class  
```  
  
 Výsledkem tohoto kódu je následující výstup:  
  
```console
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

- [Pokročilé techniky dotazů (LINQ to XML) (Visual Basic)](advanced-query-techniques-linq-to-xml.md)
