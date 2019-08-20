---
title: 'Postupy: Transformace tvaru stromu XML (C#)'
ms.date: 07/20/2015
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
ms.openlocfilehash: c6f78decdcc32d202f4a0f1e51a012dce8aa7d6c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592218"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-c"></a><span data-ttu-id="68d75-102">Postupy: Transformace tvaru stromu XML (C#)</span><span class="sxs-lookup"><span data-stu-id="68d75-102">How to: Transform the Shape of an XML Tree (C#)</span></span>
<span data-ttu-id="68d75-103">*Tvar* dokumentu XML odkazuje na jeho názvy elementů, názvy atributů a charakteristiky jeho hierarchie.</span><span class="sxs-lookup"><span data-stu-id="68d75-103">The *shape* of an XML document refers to its element names, attribute names, and the characteristics of its hierarchy.</span></span>  
  
 <span data-ttu-id="68d75-104">Někdy budete muset změnit tvar dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="68d75-104">Sometimes you will have to change the shape of an XML document.</span></span> <span data-ttu-id="68d75-105">Například může být nutné odeslat existující dokument XML do jiného systému, který vyžaduje různé názvy elementů a atributů.</span><span class="sxs-lookup"><span data-stu-id="68d75-105">For example, you might have to send an existing XML document to another system that requires different element and attribute names.</span></span> <span data-ttu-id="68d75-106">Můžete procházet dokumentem, odstraňovat a předávat prvky podle potřeby, ale použití funkční konstrukce má za následek čitelnější a udržovatelný kód.</span><span class="sxs-lookup"><span data-stu-id="68d75-106">You could go through the document, deleting and renaming elements as required, but using functional construction results in more readable and maintainable code.</span></span> <span data-ttu-id="68d75-107">Další informace o konstrukci funkčnosti naleznete v tématu [funkční konstrukce (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="68d75-107">For more information about functional construction, see [Functional Construction (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="68d75-108">První příklad změní organizaci dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="68d75-108">The first example changes the organization of the XML document.</span></span> <span data-ttu-id="68d75-109">Přesouvá komplexní prvky z jednoho umístění ve stromové struktuře do jiného.</span><span class="sxs-lookup"><span data-stu-id="68d75-109">It moves complex elements from one location in the tree to another.</span></span>  
  
 <span data-ttu-id="68d75-110">Druhý příklad v tomto tématu vytvoří dokument XML s jiným tvarem, než zdrojový dokument.</span><span class="sxs-lookup"><span data-stu-id="68d75-110">The second example in this topic creates an XML document with a different shape than the source document.</span></span> <span data-ttu-id="68d75-111">Změní velká a malá písmena názvů prvků, přejmenuje některé prvky a ponechá některé prvky ze zdrojového stromu z transformované stromové struktury.</span><span class="sxs-lookup"><span data-stu-id="68d75-111">It changes the casing of the element names, renames some elements, and leaves some elements from the source tree out of the transformed tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68d75-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="68d75-112">Example</span></span>  
 <span data-ttu-id="68d75-113">Následující kód změní tvar souboru XML pomocí vložených výrazů dotazů.</span><span class="sxs-lookup"><span data-stu-id="68d75-113">The following code changes the shape of an XML file using embedded query expressions.</span></span>  
  
 <span data-ttu-id="68d75-114">Zdrojový dokument XML v tomto příkladu obsahuje `Customers` element `Root` pod prvkem, který obsahuje všechny zákazníky.</span><span class="sxs-lookup"><span data-stu-id="68d75-114">The source XML document in this example contains a `Customers` element under the `Root` element that contains all customers.</span></span> <span data-ttu-id="68d75-115">Obsahuje `Orders` také element `Root` pod prvkem, který obsahuje všechny objednávky.</span><span class="sxs-lookup"><span data-stu-id="68d75-115">It also contains an `Orders` element under the `Root` element that contains all orders.</span></span> <span data-ttu-id="68d75-116">Tento příklad vytvoří nový strom XML, ve kterém jsou objednávky pro každého zákazníka obsaženy v `Orders` elementu `Customer` v rámci elementu.</span><span class="sxs-lookup"><span data-stu-id="68d75-116">This example creates a new XML tree in which the orders for each customer are contained in an `Orders` element within the `Customer` element.</span></span> <span data-ttu-id="68d75-117">Původní dokument také obsahuje `CustomerID` element `Order` v elementu; tento prvek bude odebrán z dokumentu, ve kterém se nachází.</span><span class="sxs-lookup"><span data-stu-id="68d75-117">The original document also contains a `CustomerID` element in the `Order` element; this element will be removed from the re-shaped document.</span></span>  
  
 <span data-ttu-id="68d75-118">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="68d75-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="68d75-119">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="68d75-119">This code produces the following output:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="68d75-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="68d75-120">Example</span></span>  
 <span data-ttu-id="68d75-121">Tento příklad přejmenuje některé prvky a převede některé atributy na prvky.</span><span class="sxs-lookup"><span data-stu-id="68d75-121">This example renames some elements and converts some attributes to elements.</span></span>  
  
 <span data-ttu-id="68d75-122">Kód volá `ConvertAddress`, který vrátí <xref:System.Xml.Linq.XElement> seznam objektů.</span><span class="sxs-lookup"><span data-stu-id="68d75-122">The code calls `ConvertAddress`, which returns a list of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="68d75-123">Argumentem metody je dotaz, který určuje `Address` komplexní prvek, `Type` kde `"Shipping"`atribut má hodnotu.</span><span class="sxs-lookup"><span data-stu-id="68d75-123">The argument to the method is a query that determines the `Address` complex element where the `Type` attribute has a value of `"Shipping"`.</span></span>  
  
 <span data-ttu-id="68d75-124">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Typická nákupní objednávka (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="68d75-124">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
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
  
 <span data-ttu-id="68d75-125">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="68d75-125">This code produces the following output:</span></span>  
  
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
