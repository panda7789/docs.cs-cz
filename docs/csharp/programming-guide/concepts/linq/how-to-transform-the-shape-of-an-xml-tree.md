---
title: Jak transformovat tvar stromu XML (C#)
description: Přečtěte si, jak transformovat tvar stromu XML. Tvar stromu XML odkazuje na jeho element a názvy atributů a jeho vlastnosti hierarchie.
ms.date: 07/20/2015
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
ms.openlocfilehash: 4fa3cc18f235d061ae1778c177c4ac9b626f4b71
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302643"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-c"></a><span data-ttu-id="0b809-104">Jak transformovat tvar stromu XML (C#)</span><span class="sxs-lookup"><span data-stu-id="0b809-104">How to transform the shape of an XML tree (C#)</span></span>
<span data-ttu-id="0b809-105">*Tvar* dokumentu XML odkazuje na jeho názvy elementů, názvy atributů a charakteristiky jeho hierarchie.</span><span class="sxs-lookup"><span data-stu-id="0b809-105">The *shape* of an XML document refers to its element names, attribute names, and the characteristics of its hierarchy.</span></span>  
  
 <span data-ttu-id="0b809-106">Někdy budete muset změnit tvar dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0b809-106">Sometimes you will have to change the shape of an XML document.</span></span> <span data-ttu-id="0b809-107">Například může být nutné odeslat existující dokument XML do jiného systému, který vyžaduje různé názvy elementů a atributů.</span><span class="sxs-lookup"><span data-stu-id="0b809-107">For example, you might have to send an existing XML document to another system that requires different element and attribute names.</span></span> <span data-ttu-id="0b809-108">Můžete procházet dokumentem, odstraňovat a předávat prvky podle potřeby, ale použití funkční konstrukce má za následek čitelnější a udržovatelný kód.</span><span class="sxs-lookup"><span data-stu-id="0b809-108">You could go through the document, deleting and renaming elements as required, but using functional construction results in more readable and maintainable code.</span></span> <span data-ttu-id="0b809-109">Další informace o konstrukci funkčnosti najdete v tématu [funkční konstrukce (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0b809-109">For more information about functional construction, see [Functional Construction (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="0b809-110">První příklad změní organizaci dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0b809-110">The first example changes the organization of the XML document.</span></span> <span data-ttu-id="0b809-111">Přesouvá komplexní prvky z jednoho umístění ve stromové struktuře do jiného.</span><span class="sxs-lookup"><span data-stu-id="0b809-111">It moves complex elements from one location in the tree to another.</span></span>  
  
 <span data-ttu-id="0b809-112">Druhý příklad v tomto tématu vytvoří dokument XML s jiným tvarem, než zdrojový dokument.</span><span class="sxs-lookup"><span data-stu-id="0b809-112">The second example in this topic creates an XML document with a different shape than the source document.</span></span> <span data-ttu-id="0b809-113">Změní velká a malá písmena názvů prvků, přejmenuje některé prvky a ponechá některé prvky ze zdrojového stromu z transformované stromové struktury.</span><span class="sxs-lookup"><span data-stu-id="0b809-113">It changes the casing of the element names, renames some elements, and leaves some elements from the source tree out of the transformed tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b809-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b809-114">Example</span></span>  
 <span data-ttu-id="0b809-115">Následující kód změní tvar souboru XML pomocí vložených výrazů dotazů.</span><span class="sxs-lookup"><span data-stu-id="0b809-115">The following code changes the shape of an XML file using embedded query expressions.</span></span>  
  
 <span data-ttu-id="0b809-116">Zdrojový dokument XML v tomto příkladu obsahuje `Customers` element pod `Root` prvkem, který obsahuje všechny zákazníky.</span><span class="sxs-lookup"><span data-stu-id="0b809-116">The source XML document in this example contains a `Customers` element under the `Root` element that contains all customers.</span></span> <span data-ttu-id="0b809-117">Obsahuje také `Orders` element pod `Root` prvkem, který obsahuje všechny objednávky.</span><span class="sxs-lookup"><span data-stu-id="0b809-117">It also contains an `Orders` element under the `Root` element that contains all orders.</span></span> <span data-ttu-id="0b809-118">Tento příklad vytvoří nový strom XML, ve kterém jsou objednávky pro každého zákazníka obsaženy v `Orders` elementu v rámci `Customer` elementu.</span><span class="sxs-lookup"><span data-stu-id="0b809-118">This example creates a new XML tree in which the orders for each customer are contained in an `Orders` element within the `Customer` element.</span></span> <span data-ttu-id="0b809-119">Původní dokument také obsahuje `CustomerID` element v `Order` elementu; tento prvek bude odebrán z dokumentu, ve kterém se nachází.</span><span class="sxs-lookup"><span data-stu-id="0b809-119">The original document also contains a `CustomerID` element in the `Order` element; this element will be removed from the re-shaped document.</span></span>  
  
 <span data-ttu-id="0b809-120">Tento příklad používá následující dokument XML: [ukázkový soubor XML: zákazníci a objednávky (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="0b809-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="0b809-121">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="0b809-121">This code produces the following output:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="0b809-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b809-122">Example</span></span>  
 <span data-ttu-id="0b809-123">Tento příklad přejmenuje některé prvky a převede některé atributy na prvky.</span><span class="sxs-lookup"><span data-stu-id="0b809-123">This example renames some elements and converts some attributes to elements.</span></span>  
  
 <span data-ttu-id="0b809-124">Kód volá `ConvertAddress` , který vrátí seznam <xref:System.Xml.Linq.XElement> objektů.</span><span class="sxs-lookup"><span data-stu-id="0b809-124">The code calls `ConvertAddress`, which returns a list of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="0b809-125">Argumentem metody je dotaz, který určuje `Address` komplexní prvek, kde `Type` atribut má hodnotu `"Shipping"` .</span><span class="sxs-lookup"><span data-stu-id="0b809-125">The argument to the method is a query that determines the `Address` complex element where the `Type` attribute has a value of `"Shipping"`.</span></span>  
  
 <span data-ttu-id="0b809-126">Tento příklad používá následující dokument XML: [vzorový soubor XML: typická nákupní objednávka (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="0b809-126">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
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
  
 <span data-ttu-id="0b809-127">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="0b809-127">This code produces the following output:</span></span>  
  
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
