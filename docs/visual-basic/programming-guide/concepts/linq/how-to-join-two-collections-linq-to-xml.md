---
title: 'Postupy: spojení dvou kolekcí (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5a5758d4-906b-4285-908d-5b930db192e6
ms.openlocfilehash: cb39895ec5916eb417fb2a161e7c1307087c09c5
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320568"
---
# <a name="how-to-join-two-collections-linq-to-xml-visual-basic"></a><span data-ttu-id="fa2d6-102">Postupy: spojení dvou kolekcí (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa2d6-102">How to: Join Two Collections (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="fa2d6-103">Element nebo atribut v dokumentu XML může někdy odkazovat na jiný element nebo atribut.</span><span class="sxs-lookup"><span data-stu-id="fa2d6-103">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="fa2d6-104">Například [ukázkový soubor XML: zákazníci a objednávky (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md) dokument XML obsahuje seznam zákazníků a seznam objednávek.</span><span class="sxs-lookup"><span data-stu-id="fa2d6-104">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="fa2d6-105">Každý prvek `Customer` obsahuje atribut `CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="fa2d6-105">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="fa2d6-106">Každý prvek `Order` obsahuje prvek `CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="fa2d6-106">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="fa2d6-107">Element `CustomerID` v každé objednávce odkazuje na atribut `CustomerID` zákazníka.</span><span class="sxs-lookup"><span data-stu-id="fa2d6-107">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>  
  
 <span data-ttu-id="fa2d6-108">[Ukázkový soubor XSD: zákazníci a objednávky](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md) obsahují XSD, které lze použít k ověření tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="fa2d6-108">The topic [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="fa2d6-109">Používá funkce `xs:key` a `xs:keyref` v XSD k určení toho, že atribut `CustomerID` elementu `Customer` je klíč a k navázání vztahu mezi prvkem `CustomerID` v každém prvku `Order` a atribut `CustomerID` v každém prvku `Customer`.</span><span class="sxs-lookup"><span data-stu-id="fa2d6-109">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>  
  
 <span data-ttu-id="fa2d6-110">U [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] můžete využít výhod tohoto vztahu pomocí klauzule `Join`.</span><span class="sxs-lookup"><span data-stu-id="fa2d6-110">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can take advantage of this relationship by using the `Join` clause.</span></span>  
  
 <span data-ttu-id="fa2d6-111">Všimněte si, že protože není k dispozici žádný index, takové spojení bude mít špatný běhový výkon.</span><span class="sxs-lookup"><span data-stu-id="fa2d6-111">Note that because there is no index available, such joining will have poor runtime performance.</span></span>  
  
 <span data-ttu-id="fa2d6-112">Podrobnější informace o `Join` najdete v tématu [operace join (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md).</span><span class="sxs-lookup"><span data-stu-id="fa2d6-112">For more detailed information about `Join`, see [Join Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa2d6-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="fa2d6-113">Example</span></span>  
 <span data-ttu-id="fa2d6-114">Následující příklad spojuje prvky `Customer` s prvky `Order` a generuje nový dokument XML, který obsahuje prvek `CompanyName` v objednávkách.</span><span class="sxs-lookup"><span data-stu-id="fa2d6-114">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>  
  
 <span data-ttu-id="fa2d6-115">Před provedením dotazu v příkladu se ověří, že dokument vyhovuje schématu v [ukázkovém souboru XSD: zákazníci a objednávky](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span><span class="sxs-lookup"><span data-stu-id="fa2d6-115">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span></span> <span data-ttu-id="fa2d6-116">Tím se zajistí, že klauzule JOIN bude vždycky fungovat.</span><span class="sxs-lookup"><span data-stu-id="fa2d6-116">This ensures that the join clause will always work.</span></span>  
  
 <span data-ttu-id="fa2d6-117">Tento dotaz nejprve načte všechny prvky `Customer` a pak je spojí s prvky `Order`.</span><span class="sxs-lookup"><span data-stu-id="fa2d6-117">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="fa2d6-118">Vybere pouze objednávky pro zákazníky s `CustomerID` větší než "K".</span><span class="sxs-lookup"><span data-stu-id="fa2d6-118">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="fa2d6-119">Potom projekty vytvoří nový prvek `Order`, který obsahuje informace o zákaznících v rámci jednotlivých objednávek.</span><span class="sxs-lookup"><span data-stu-id="fa2d6-119">It then projects a new `Order` element that contains the customer information within each order.</span></span>  
  
 <span data-ttu-id="fa2d6-120">Tento příklad používá následující dokument XML: [ukázkový soubor XML: zákazníci a objednávky (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="fa2d6-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="fa2d6-121">V tomto příkladu se používá následující schéma XSD: [ukázkový soubor XSD: zákazníci a objednávky](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span><span class="sxs-lookup"><span data-stu-id="fa2d6-121">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span></span>  
  
 <span data-ttu-id="fa2d6-122">Všimněte si, že připojení tímto způsobem nebude fungovat velmi dobře.</span><span class="sxs-lookup"><span data-stu-id="fa2d6-122">Note that joining in this fashion will not perform very well.</span></span> <span data-ttu-id="fa2d6-123">Spojení se provádí pomocí lineárního hledání.</span><span class="sxs-lookup"><span data-stu-id="fa2d6-123">Joins are performed via a linear search.</span></span> <span data-ttu-id="fa2d6-124">Neexistují žádné zatřiďovací tabulky ani indexy, které by měly pomáhat s výkonem.</span><span class="sxs-lookup"><span data-stu-id="fa2d6-124">There are no hash tables or indexes to help with performance.</span></span>  
  
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
  
 <span data-ttu-id="fa2d6-125">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="fa2d6-125">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fa2d6-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fa2d6-126">See also</span></span>

- [<span data-ttu-id="fa2d6-127">Pokročilé techniky dotazů (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa2d6-127">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
