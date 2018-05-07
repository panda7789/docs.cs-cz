---
title: 'Postupy: připojení dvě kolekce (technologie LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5a5758d4-906b-4285-908d-5b930db192e6
ms.openlocfilehash: 3ceb9cf7dfdd1d18a07e93d15624fd8fac045d07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-join-two-collections-linq-to-xml-visual-basic"></a>Postupy: připojení dvě kolekce (technologie LINQ to XML) (Visual Basic)
Elementu nebo atributu v dokumentu XML mohou někdy odkazovat na jiné elementu nebo atributu. Například [ukázkový soubor XML: Zákazníci a objednávky (technologie LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md) dokumentu XML obsahuje seznam zákazníků a seznam objednávky. Každý `Customer` obsahuje element `CustomerID` atribut. Každý `Order` obsahuje element `CustomerID` elementu. `CustomerID` Element v každé pořadí odkazuje `CustomerID` atribut v zákazníka.  
  
 Téma [ukázkový soubor XSD: Zákazníci a objednávky](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md) obsahuje XSD, který slouží k ověření tohoto dokumentu. Použije `xs:key` a `xs:keyref` funkce XSD zajistit, že `CustomerID` atribut `Customer` element je klíč a k vytvoření vztahu mezi `CustomerID` element v každé `Order` element a `CustomerID` atribut v každé `Customer` elementu.  
  
 S [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], můžete využít výhod této relace pomocí `Join` klauzule.  
  
 Všimněte si, protože není k dispozici žádný index, takové připojení že běhový snížený výkon.  
  
 Podrobné informace o `Join`, najdete v části [připojení operací (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad spojení `Customer` elementů `Order` prvky a vygeneruje nový dokument XML, který zahrnuje `CompanyName` element v objednávky.  
  
 Před provedením dotazu, příklad ověří, že dokument v souladu se schéma v [ukázkový soubor XSD: Zákazníci a objednávky](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md). Tím se zajistí, že bude vždy fungovat klauzuli join.  
  
 Tento dotaz nejprve načte všechny `Customer` prvky a potom připojí, aby `Order` elementy. Vybere pouze příkazy pro zákazníky s `CustomerID` větší než "K". Ji pak projekty novou `Order` elementu, který obsahuje informace o zákazníkovi v rámci každé pořadí.  
  
 Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: Zákazníci a objednávky (technologie LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
 Tento příklad používá následující schéma XSD: [ukázkový soubor XSD: Zákazníci a objednávky](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).  
  
 Všimněte si, že připojení tímto způsobem nebude provádět velmi dobře. Spojení se provádí prostřednictvím lineárního hledání. Neexistují žádné tabulky hash nebo indexy, které pomáhají s výkonem.  
  
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
 [Pokročilé techniky dotazu (technologie LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
