---
title: 'Postupy: spojení dvou kolekcí (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5a5758d4-906b-4285-908d-5b930db192e6
ms.openlocfilehash: 3ceb9cf7dfdd1d18a07e93d15624fd8fac045d07
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245697"
---
# <a name="how-to-join-two-collections-linq-to-xml-visual-basic"></a><span data-ttu-id="005ae-102">Postupy: spojení dvou kolekcí (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="005ae-102">How to: Join Two Collections (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="005ae-103">Prvek nebo atribut v dokumentu XML mohou někdy odkazovat na jiné elementu nebo atributu.</span><span class="sxs-lookup"><span data-stu-id="005ae-103">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="005ae-104">Například [ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md) dokument XML obsahuje seznam zákazníků a seznam objednávek.</span><span class="sxs-lookup"><span data-stu-id="005ae-104">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="005ae-105">Každý `Customer` obsahuje element `CustomerID` atribut.</span><span class="sxs-lookup"><span data-stu-id="005ae-105">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="005ae-106">Každý `Order` obsahuje element `CustomerID` elementu.</span><span class="sxs-lookup"><span data-stu-id="005ae-106">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="005ae-107">`CustomerID` Element z každé objednávky odkazuje `CustomerID` atribut v zákazníka.</span><span class="sxs-lookup"><span data-stu-id="005ae-107">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>  
  
 <span data-ttu-id="005ae-108">Téma [ukázkový soubor XSD: Zákazníci a objednávky](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md) obsahuje XSD, který slouží k ověření tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="005ae-108">The topic [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="005ae-109">Používá `xs:key` a `xs:keyref` funkce XSD zajistit, že `CustomerID` atribut `Customer` element je klíč a k vytvoření vztahu mezi `CustomerID` element v každé `Order` elementu a `CustomerID` atributy v každém `Customer` elementu.</span><span class="sxs-lookup"><span data-stu-id="005ae-109">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>  
  
 <span data-ttu-id="005ae-110">S [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], pomocí můžete využít tuto relaci `Join` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="005ae-110">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can take advantage of this relationship by using the `Join` clause.</span></span>  
  
 <span data-ttu-id="005ae-111">Mějte na paměti, protože není k dispozici žádný index, tato připojení budou mít runtime nízký výkon.</span><span class="sxs-lookup"><span data-stu-id="005ae-111">Note that because there is no index available, such joining will have poor runtime performance.</span></span>  
  
 <span data-ttu-id="005ae-112">Podrobné informace o `Join`, naleznete v tématu [operace spojení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md).</span><span class="sxs-lookup"><span data-stu-id="005ae-112">For more detailed information about `Join`, see [Join Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="005ae-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="005ae-113">Example</span></span>  
 <span data-ttu-id="005ae-114">Následující příklad připojí `Customer` prvků, které mají `Order` prvky a vytvoří nový dokument XML, který zahrnuje `CompanyName` prvek objednávky.</span><span class="sxs-lookup"><span data-stu-id="005ae-114">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>  
  
 <span data-ttu-id="005ae-115">Před provedením dotazu, v příkladu ověřuje, že dokument vyhovuje schématu v [ukázkový soubor XSD: Zákazníci a objednávky](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span><span class="sxs-lookup"><span data-stu-id="005ae-115">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span></span> <span data-ttu-id="005ae-116">Tím se zajistí, že budou vždy fungovat klauzule join.</span><span class="sxs-lookup"><span data-stu-id="005ae-116">This ensures that the join clause will always work.</span></span>  
  
 <span data-ttu-id="005ae-117">Tento dotaz načte prvních všechny `Customer` prvky a poté je připojen `Order` prvky.</span><span class="sxs-lookup"><span data-stu-id="005ae-117">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="005ae-118">Vybere pouze příkazy pro zákazníky s `CustomerID` větší než "K".</span><span class="sxs-lookup"><span data-stu-id="005ae-118">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="005ae-119">To potom projekty nový `Order` element, který obsahuje informace o zákaznících v rámci každé objednávky.</span><span class="sxs-lookup"><span data-stu-id="005ae-119">It then projects a new `Order` element that contains the customer information within each order.</span></span>  
  
 <span data-ttu-id="005ae-120">Tento příklad používá následujícího dokumentu XML: [ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="005ae-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="005ae-121">Tento příklad používá následující schéma XSD: [ukázkový soubor XSD: Zákazníci a objednávky](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span><span class="sxs-lookup"><span data-stu-id="005ae-121">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span></span>  
  
 <span data-ttu-id="005ae-122">Všimněte si, že připojení tímto způsobem nebude fungují velmi dobře.</span><span class="sxs-lookup"><span data-stu-id="005ae-122">Note that joining in this fashion will not perform very well.</span></span> <span data-ttu-id="005ae-123">Spojení se provádí prostřednictvím lineárního hledání.</span><span class="sxs-lookup"><span data-stu-id="005ae-123">Joins are performed via a linear search.</span></span> <span data-ttu-id="005ae-124">Neexistují žádné zatřiďovacích tabulek nebo indexy, které vám pomůžou s výkonem.</span><span class="sxs-lookup"><span data-stu-id="005ae-124">There are no hash tables or indexes to help with performance.</span></span>  
  
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
  
 <span data-ttu-id="005ae-125">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="005ae-125">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="005ae-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="005ae-126">See Also</span></span>  
 [<span data-ttu-id="005ae-127">Pokročilé techniky dotazování (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="005ae-127">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
