---
title: 'Postupy: Spojit dvě kolekce (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: aa774e23cfd232709f9824826f5084fe6049ef37
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593195"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a><span data-ttu-id="81ef1-102">Postupy: Spojit dvě kolekce (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="81ef1-102">How to: Join Two Collections (LINQ to XML) (C#)</span></span>
<span data-ttu-id="81ef1-103">Element nebo atribut v dokumentu XML může někdy odkazovat na jiný element nebo atribut.</span><span class="sxs-lookup"><span data-stu-id="81ef1-103">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="81ef1-104">Například [ukázkový soubor XML: Dokument XML Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) obsahuje seznam zákazníků a seznam objednávek.</span><span class="sxs-lookup"><span data-stu-id="81ef1-104">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="81ef1-105">Každý `Customer` prvek`CustomerID` obsahuje atribut.</span><span class="sxs-lookup"><span data-stu-id="81ef1-105">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="81ef1-106">Každý `Order` prvek`CustomerID` obsahuje element.</span><span class="sxs-lookup"><span data-stu-id="81ef1-106">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="81ef1-107">Element v každé objednávce odkazuje `CustomerID` na atribut v zákazníkovi. `CustomerID`</span><span class="sxs-lookup"><span data-stu-id="81ef1-107">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>  
  
 <span data-ttu-id="81ef1-108">Ukázkový soubor [XSD v tématu: Zákazníci a objednávky](./sample-xsd-file-customers-and-orders1.md) obsahují XSD, které lze použít k ověření tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="81ef1-108">The topic [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="81ef1-109">Používá `xs:key` funkce `CustomerID` a `xs:keyref` `Order` XSD k určení`Customer` toho, že atribut prvku je klíč, a k navázání vztahu mezi prvkem v jednotlivých prvcích a `CustomerID` atribut v každém `Customer`elementu. `CustomerID`</span><span class="sxs-lookup"><span data-stu-id="81ef1-109">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>  
  
 <span data-ttu-id="81ef1-110">Pomocí můžete tuto relaci využít `join` pomocí klauzule. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81ef1-110">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can take advantage of this relationship by using the `join` clause.</span></span>  
  
 <span data-ttu-id="81ef1-111">Všimněte si, že protože není k dispozici žádný index, takové spojení bude mít špatný běhový výkon.</span><span class="sxs-lookup"><span data-stu-id="81ef1-111">Note that because there is no index available, such joining will have poor runtime performance.</span></span>  
  
 <span data-ttu-id="81ef1-112">Podrobnější informace o `join`najdete v tématu [operace join (C#)](./join-operations.md).</span><span class="sxs-lookup"><span data-stu-id="81ef1-112">For more detailed information about `join`, see [Join Operations (C#)](./join-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="81ef1-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="81ef1-113">Example</span></span>  
 <span data-ttu-id="81ef1-114">Následující příklad spojuje `Customer` prvky `Order` s prvky a generuje nový dokument `CompanyName` XML, který obsahuje prvek v objednávkách.</span><span class="sxs-lookup"><span data-stu-id="81ef1-114">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>  
  
 <span data-ttu-id="81ef1-115">Před provedením dotazu v příkladu se ověří, že dokument vyhovuje schématu v [ukázkovém souboru XSD: Zákazníci a objednávky](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="81ef1-115">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="81ef1-116">Tím se zajistí, že klauzule JOIN bude vždycky fungovat.</span><span class="sxs-lookup"><span data-stu-id="81ef1-116">This ensures that the join clause will always work.</span></span>  
  
 <span data-ttu-id="81ef1-117">Tento dotaz nejprve načte všechny `Customer` prvky a pak je spojí `Order` s prvky.</span><span class="sxs-lookup"><span data-stu-id="81ef1-117">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="81ef1-118">Vybere pouze objednávky pro zákazníky s `CustomerID` větší než "K".</span><span class="sxs-lookup"><span data-stu-id="81ef1-118">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="81ef1-119">Potom projekty vytvoří nový `Order` prvek, který obsahuje informace o zákaznících v rámci jednotlivých objednávek.</span><span class="sxs-lookup"><span data-stu-id="81ef1-119">It then projects a new `Order` element that contains the customer information within each order.</span></span>  
  
 <span data-ttu-id="81ef1-120">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="81ef1-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
 <span data-ttu-id="81ef1-121">V tomto příkladu se používá následující schéma XSD: [Ukázkový soubor XSD: Zákazníci a objednávky](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="81ef1-121">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span>  
  
 <span data-ttu-id="81ef1-122">Všimněte si, že připojení tímto způsobem nebude fungovat velmi dobře.</span><span class="sxs-lookup"><span data-stu-id="81ef1-122">Note that joining in this fashion will not perform very well.</span></span> <span data-ttu-id="81ef1-123">Spojení se provádí pomocí lineárního hledání.</span><span class="sxs-lookup"><span data-stu-id="81ef1-123">Joins are performed via a linear search.</span></span> <span data-ttu-id="81ef1-124">Neexistují žádné zatřiďovací tabulky ani indexy, které by měly pomáhat s výkonem.</span><span class="sxs-lookup"><span data-stu-id="81ef1-124">There are no hash tables or indexes to help with performance.</span></span>  
  
```csharp  
XmlSchemaSet schemas = new XmlSchemaSet();  
schemas.Add("", "CustomersOrders.xsd");  
  
Console.Write("Attempting to validate, ");  
XDocument custOrdDoc = XDocument.Load("CustomersOrders.xml");  
  
bool errors = false;  
custOrdDoc.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");  
  
if (!errors)  
{  
    // Join customers and orders, and create a new XML document with  
    // a different shape.  
  
    // The new document contains orders only for customers with a  
    // CustomerID > 'K'  
    XElement custOrd = custOrdDoc.Element("Root");  
    XElement newCustOrd = new XElement("Root",  
        from c in custOrd.Element("Customers").Elements("Customer")  
        join o in custOrd.Element("Orders").Elements("Order")  
                   on (string)c.Attribute("CustomerID") equals  
                      (string)o.Element("CustomerID")  
        where ((string)c.Attribute("CustomerID")).CompareTo("K") > 0  
        select new XElement("Order",  
            new XElement("CustomerID", (string)c.Attribute("CustomerID")),  
            new XElement("CompanyName", (string)c.Element("CompanyName")),  
            new XElement("ContactName", (string)c.Element("ContactName")),  
            new XElement("EmployeeID", (string)o.Element("EmployeeID")),  
            new XElement("OrderDate", (DateTime)o.Element("OrderDate"))  
        )  
    );  
    Console.WriteLine(newCustOrd);  
}  
```  
  
 <span data-ttu-id="81ef1-125">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="81ef1-125">This code produces the following output:</span></span>  
  
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
