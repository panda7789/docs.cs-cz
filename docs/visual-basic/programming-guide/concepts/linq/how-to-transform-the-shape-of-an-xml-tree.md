---
title: 'Postupy: Transformace tvaru stromu XML (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 84b60854-48b2-452c-87f2-77d53e1d653a
ms.openlocfilehash: 067bf56b8dff994080ba78147d992b97a56867cb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833656"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-visual-basic"></a><span data-ttu-id="48adb-102">Postupy: Transformace tvaru stromu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48adb-102">How to: Transform the Shape of an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="48adb-103">*Tvar* formátu XML dokumentu odkazuje na jeho názvy elementů, názvy atributů a vlastnosti ve své hierarchii.</span><span class="sxs-lookup"><span data-stu-id="48adb-103">The *shape* of an XML document refers to its element names, attribute names, and the characteristics of its hierarchy.</span></span>  
  
 <span data-ttu-id="48adb-104">Někdy je nutné změnit tvar dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="48adb-104">Sometimes you will have to change the shape of an XML document.</span></span> <span data-ttu-id="48adb-105">Například budete muset odeslat existující dokument XML do jiného systému, který vyžaduje jiný element a názvy atributů.</span><span class="sxs-lookup"><span data-stu-id="48adb-105">For example, you might have to send an existing XML document to another system that requires different element and attribute names.</span></span> <span data-ttu-id="48adb-106">Dokument, může projít, odstranění a přejmenování prvky jako povinné, ale pomocí funkční konstrukce výsledky v čitelnější a udržovatelný kód.</span><span class="sxs-lookup"><span data-stu-id="48adb-106">You could go through the document, deleting and renaming elements as required, but using functional construction results in more readable and maintainable code.</span></span> <span data-ttu-id="48adb-107">Další informace o funkční konstrukce najdete v tématu [funkční konstrukce (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="48adb-107">For more information about functional construction, see [Functional Construction (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="48adb-108">V prvním příkladu se změní uspořádání dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="48adb-108">The first example changes the organization of the XML document.</span></span> <span data-ttu-id="48adb-109">Komplexních prvků z jednoho umístění ve stromu přesunu do jiného.</span><span class="sxs-lookup"><span data-stu-id="48adb-109">It moves complex elements from one location in the tree to another.</span></span>  
  
 <span data-ttu-id="48adb-110">Ve druhém příkladu v tomto tématu vytvoří dokument XML s obrazcem jiný než zdrojový dokument.</span><span class="sxs-lookup"><span data-stu-id="48adb-110">The second example in this topic creates an XML document with a different shape than the source document.</span></span> <span data-ttu-id="48adb-111">Změní velká a malá písmena názvy elementů, přejmenuje některé prvky a ponechá některé prvky ze stromu zdrojového kódu z transformovaných stromu.</span><span class="sxs-lookup"><span data-stu-id="48adb-111">It changes the casing of the element names, renames some elements, and leaves some elements from the source tree out of the transformed tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48adb-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="48adb-112">Example</span></span>  
 <span data-ttu-id="48adb-113">Následující kód změní tvaru souborů XML pomocí dotazu vložené výrazy.</span><span class="sxs-lookup"><span data-stu-id="48adb-113">The following code changes the shape of an XML file using embedded query expressions.</span></span>  
  
 <span data-ttu-id="48adb-114">Zdrojovém dokumentu XML v tomto příkladu obsahuje `Customers` element v rámci `Root` element, který obsahuje všechny zákazníky.</span><span class="sxs-lookup"><span data-stu-id="48adb-114">The source XML document in this example contains a `Customers` element under the `Root` element that contains all customers.</span></span> <span data-ttu-id="48adb-115">Obsahuje taky `Orders` element v rámci `Root` element, který obsahuje všechny objednávky.</span><span class="sxs-lookup"><span data-stu-id="48adb-115">It also contains an `Orders` element under the `Root` element that contains all orders.</span></span> <span data-ttu-id="48adb-116">Tento příklad vytvoří nový stromu XML, ve které jsou součástí objednávky pro každého zákazníka `Orders` element v rámci `Customer` elementu.</span><span class="sxs-lookup"><span data-stu-id="48adb-116">This example creates a new XML tree in which the orders for each customer are contained in an `Orders` element within the `Customer` element.</span></span> <span data-ttu-id="48adb-117">Původní dokument obsahuje také `CustomerID` element v `Order` element; tento element budou odstraněny z znovu upravená dokumentu.</span><span class="sxs-lookup"><span data-stu-id="48adb-117">The original document also contains a `CustomerID` element in the `Order` element; this element will be removed from the re-shaped document.</span></span>  
  
 <span data-ttu-id="48adb-118">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="48adb-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="48adb-119">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="48adb-119">This code produces the following output:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="48adb-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="48adb-120">Example</span></span>  
 <span data-ttu-id="48adb-121">Tento příklad přejmenuje některé prvky a převede některé atributy elementů.</span><span class="sxs-lookup"><span data-stu-id="48adb-121">This example renames some elements and converts some attributes to elements.</span></span>  
  
 <span data-ttu-id="48adb-122">Kód volá `ConvertAddress`, který vrátí seznam hodnot <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="48adb-122">The code calls `ConvertAddress`, which returns a list of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="48adb-123">Argument k metodě je dotaz, který určuje `Address` komplexních prvků kde `Type` atribut má hodnotu `"Shipping"`.</span><span class="sxs-lookup"><span data-stu-id="48adb-123">The argument to the method is a query that determines the `Address` complex element where the `Type` attribute has a value of `"Shipping"`.</span></span>  
  
 <span data-ttu-id="48adb-124">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Typická nákupní objednávka (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="48adb-124">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="48adb-125">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="48adb-125">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="48adb-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="48adb-126">See also</span></span>

- [<span data-ttu-id="48adb-127">Projekce a transformace (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48adb-127">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
