---
title: "Postupy: připojení dvě kolekce (technologie LINQ to XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a5758d4-906b-4285-908d-5b930db192e6
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c4850013184b35dcb0b30455a62cead30394103c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-join-two-collections-linq-to-xml-visual-basic"></a><span data-ttu-id="0d1f0-102">Postupy: připojení dvě kolekce (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d1f0-102">How to: Join Two Collections (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="0d1f0-103">Elementu nebo atributu v dokumentu XML mohou někdy odkazovat na jiné elementu nebo atributu.</span><span class="sxs-lookup"><span data-stu-id="0d1f0-103">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="0d1f0-104">Například [ukázkový soubor XML: Zákazníci a objednávky (technologie LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md) dokumentu XML obsahuje seznam zákazníků a seznam objednávky.</span><span class="sxs-lookup"><span data-stu-id="0d1f0-104">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="0d1f0-105">Každý `Customer` obsahuje element `CustomerID` atribut.</span><span class="sxs-lookup"><span data-stu-id="0d1f0-105">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="0d1f0-106">Každý `Order` obsahuje element `CustomerID` elementu.</span><span class="sxs-lookup"><span data-stu-id="0d1f0-106">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="0d1f0-107">`CustomerID` Element v každé pořadí odkazuje `CustomerID` atribut v zákazníka.</span><span class="sxs-lookup"><span data-stu-id="0d1f0-107">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>  
  
 <span data-ttu-id="0d1f0-108">Téma [ukázkový soubor XSD: Zákazníci a objednávky](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md) obsahuje XSD, který slouží k ověření tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="0d1f0-108">The topic [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="0d1f0-109">Použije `xs:key` a `xs:keyref` funkce XSD zajistit, že `CustomerID` atribut `Customer` element je klíč a k vytvoření vztahu mezi `CustomerID` element v každé `Order` element a `CustomerID` atribut v každé `Customer` elementu.</span><span class="sxs-lookup"><span data-stu-id="0d1f0-109">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>  
  
 <span data-ttu-id="0d1f0-110">S [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], můžete využít výhod této relace pomocí `Join` klauzule.</span><span class="sxs-lookup"><span data-stu-id="0d1f0-110">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can take advantage of this relationship by using the `Join` clause.</span></span>  
  
 <span data-ttu-id="0d1f0-111">Všimněte si, protože není k dispozici žádný index, takové připojení že běhový snížený výkon.</span><span class="sxs-lookup"><span data-stu-id="0d1f0-111">Note that because there is no index available, such joining will have poor runtime performance.</span></span>  
  
 <span data-ttu-id="0d1f0-112">Podrobné informace o `Join`, najdete v části [připojení operací (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md).</span><span class="sxs-lookup"><span data-stu-id="0d1f0-112">For more detailed information about `Join`, see [Join Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d1f0-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="0d1f0-113">Example</span></span>  
 <span data-ttu-id="0d1f0-114">Následující příklad spojení `Customer` elementů `Order` prvky a vygeneruje nový dokument XML, který zahrnuje `CompanyName` element v objednávky.</span><span class="sxs-lookup"><span data-stu-id="0d1f0-114">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>  
  
 <span data-ttu-id="0d1f0-115">Před provedením dotazu, příklad ověří, že dokument v souladu se schéma v [ukázkový soubor XSD: Zákazníci a objednávky](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span><span class="sxs-lookup"><span data-stu-id="0d1f0-115">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span></span> <span data-ttu-id="0d1f0-116">Tím se zajistí, že bude vždy fungovat klauzuli join.</span><span class="sxs-lookup"><span data-stu-id="0d1f0-116">This ensures that the join clause will always work.</span></span>  
  
 <span data-ttu-id="0d1f0-117">Tento dotaz nejprve načte všechny `Customer` prvky a potom připojí, aby `Order` elementy.</span><span class="sxs-lookup"><span data-stu-id="0d1f0-117">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="0d1f0-118">Vybere pouze příkazy pro zákazníky s `CustomerID` větší než "K".</span><span class="sxs-lookup"><span data-stu-id="0d1f0-118">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="0d1f0-119">Ji pak projekty novou `Order` elementu, který obsahuje informace o zákazníkovi v rámci každé pořadí.</span><span class="sxs-lookup"><span data-stu-id="0d1f0-119">It then projects a new `Order` element that contains the customer information within each order.</span></span>  
  
 <span data-ttu-id="0d1f0-120">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: Zákazníci a objednávky (technologie LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0d1f0-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="0d1f0-121">Tento příklad používá následující schéma XSD: [ukázkový soubor XSD: Zákazníci a objednávky](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span><span class="sxs-lookup"><span data-stu-id="0d1f0-121">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span></span>  
  
 <span data-ttu-id="0d1f0-122">Všimněte si, že připojení tímto způsobem nebude provádět velmi dobře.</span><span class="sxs-lookup"><span data-stu-id="0d1f0-122">Note that joining in this fashion will not perform very well.</span></span> <span data-ttu-id="0d1f0-123">Spojení se provádí prostřednictvím lineárního hledání.</span><span class="sxs-lookup"><span data-stu-id="0d1f0-123">Joins are performed via a linear search.</span></span> <span data-ttu-id="0d1f0-124">Neexistují žádné tabulky hash nebo indexy, které pomáhají s výkonem.</span><span class="sxs-lookup"><span data-stu-id="0d1f0-124">There are no hash tables or indexes to help with performance.</span></span>  
  
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
  
 <span data-ttu-id="0d1f0-125">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="0d1f0-125">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0d1f0-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d1f0-126">See Also</span></span>  
 [<span data-ttu-id="0d1f0-127">Pokročilé techniky dotazu (technologie LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d1f0-127">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
