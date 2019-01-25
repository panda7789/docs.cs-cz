---
title: 'Postupy: Transformace tvaru stromu XML (C#)'
ms.date: 07/20/2015
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
ms.openlocfilehash: 535f528d347e0c72ddaaab74ea78b47993a873a5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491620"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-c"></a><span data-ttu-id="d460e-102">Postupy: Transformace tvaru stromu XML (C#)</span><span class="sxs-lookup"><span data-stu-id="d460e-102">How to: Transform the Shape of an XML Tree (C#)</span></span>
<span data-ttu-id="d460e-103">*Tvar* formátu XML dokumentu odkazuje na jeho názvy elementů, názvy atributů a vlastnosti ve své hierarchii.</span><span class="sxs-lookup"><span data-stu-id="d460e-103">The *shape* of an XML document refers to its element names, attribute names, and the characteristics of its hierarchy.</span></span>  
  
 <span data-ttu-id="d460e-104">Někdy je nutné změnit tvar dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="d460e-104">Sometimes you will have to change the shape of an XML document.</span></span> <span data-ttu-id="d460e-105">Například budete muset odeslat existující dokument XML do jiného systému, který vyžaduje jiný element a názvy atributů.</span><span class="sxs-lookup"><span data-stu-id="d460e-105">For example, you might have to send an existing XML document to another system that requires different element and attribute names.</span></span> <span data-ttu-id="d460e-106">Dokument, může projít, odstranění a přejmenování prvky jako povinné, ale pomocí funkční konstrukce výsledky v čitelnější a udržovatelný kód.</span><span class="sxs-lookup"><span data-stu-id="d460e-106">You could go through the document, deleting and renaming elements as required, but using functional construction results in more readable and maintainable code.</span></span> <span data-ttu-id="d460e-107">Další informace o funkční konstrukce najdete v tématu [funkční konstrukce (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d460e-107">For more information about functional construction, see [Functional Construction (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="d460e-108">V prvním příkladu se změní uspořádání dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="d460e-108">The first example changes the organization of the XML document.</span></span> <span data-ttu-id="d460e-109">Komplexních prvků z jednoho umístění ve stromu přesunu do jiného.</span><span class="sxs-lookup"><span data-stu-id="d460e-109">It moves complex elements from one location in the tree to another.</span></span>  
  
 <span data-ttu-id="d460e-110">Ve druhém příkladu v tomto tématu vytvoří dokument XML s obrazcem jiný než zdrojový dokument.</span><span class="sxs-lookup"><span data-stu-id="d460e-110">The second example in this topic creates an XML document with a different shape than the source document.</span></span> <span data-ttu-id="d460e-111">Změní velká a malá písmena názvy elementů, přejmenuje některé prvky a ponechá některé prvky ze stromu zdrojového kódu z transformovaných stromu.</span><span class="sxs-lookup"><span data-stu-id="d460e-111">It changes the casing of the element names, renames some elements, and leaves some elements from the source tree out of the transformed tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d460e-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="d460e-112">Example</span></span>  
 <span data-ttu-id="d460e-113">Následující kód změní tvaru souborů XML pomocí dotazu vložené výrazy.</span><span class="sxs-lookup"><span data-stu-id="d460e-113">The following code changes the shape of an XML file using embedded query expressions.</span></span>  
  
 <span data-ttu-id="d460e-114">Zdrojovém dokumentu XML v tomto příkladu obsahuje `Customers` element v rámci `Root` element, který obsahuje všechny zákazníky.</span><span class="sxs-lookup"><span data-stu-id="d460e-114">The source XML document in this example contains a `Customers` element under the `Root` element that contains all customers.</span></span> <span data-ttu-id="d460e-115">Obsahuje taky `Orders` element v rámci `Root` element, který obsahuje všechny objednávky.</span><span class="sxs-lookup"><span data-stu-id="d460e-115">It also contains an `Orders` element under the `Root` element that contains all orders.</span></span> <span data-ttu-id="d460e-116">Tento příklad vytvoří nový stromu XML, ve které jsou součástí objednávky pro každého zákazníka `Orders` element v rámci `Customer` elementu.</span><span class="sxs-lookup"><span data-stu-id="d460e-116">This example creates a new XML tree in which the orders for each customer are contained in an `Orders` element within the `Customer` element.</span></span> <span data-ttu-id="d460e-117">Původní dokument obsahuje také `CustomerID` element v `Order` element; tento element budou odstraněny z znovu upravená dokumentu.</span><span class="sxs-lookup"><span data-stu-id="d460e-117">The original document also contains a `CustomerID` element in the `Order` element; this element will be removed from the re-shaped document.</span></span>  
  
 <span data-ttu-id="d460e-118">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="d460e-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="d460e-119">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d460e-119">This code produces the following output:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="d460e-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="d460e-120">Example</span></span>  
 <span data-ttu-id="d460e-121">Tento příklad přejmenuje některé prvky a převede některé atributy elementů.</span><span class="sxs-lookup"><span data-stu-id="d460e-121">This example renames some elements and converts some attributes to elements.</span></span>  
  
 <span data-ttu-id="d460e-122">Kód volá `ConvertAddress`, který vrátí seznam hodnot <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="d460e-122">The code calls `ConvertAddress`, which returns a list of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="d460e-123">Argument k metodě je dotaz, který určuje `Address` komplexních prvků kde `Type` atribut má hodnotu `"Shipping"`.</span><span class="sxs-lookup"><span data-stu-id="d460e-123">The argument to the method is a query that determines the `Address` complex element where the `Type` attribute has a value of `"Shipping"`.</span></span>  
  
 <span data-ttu-id="d460e-124">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Typická nákupní objednávka (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="d460e-124">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
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
  
 <span data-ttu-id="d460e-125">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d460e-125">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d460e-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d460e-126">See also</span></span>

- [<span data-ttu-id="d460e-127">Projekce a transformace (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d460e-127">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
