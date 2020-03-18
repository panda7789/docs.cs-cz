---
title: Jak ověřit pomocí XSD (LINQ na XML) (C#)
ms.date: 07/20/2015
ms.assetid: 6a7f83a9-2d74-4c2b-8417-0a8595879516
ms.openlocfilehash: 29830457b63f36dd401a412364060339344f35cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347253"
---
# <a name="how-to-validate-using-xsd-linq-to-xml-c"></a><span data-ttu-id="7e59a-102">Jak ověřit pomocí XSD (LINQ na XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="7e59a-102">How to validate using XSD (LINQ to XML) (C#)</span></span>
<span data-ttu-id="7e59a-103">Obor <xref:System.Xml.Schema> názvů obsahuje metody rozšíření, které usnadňují ověření stromu XML proti souboru jazyka XSD (Xml Schema Definition Language).</span><span class="sxs-lookup"><span data-stu-id="7e59a-103">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XML Schema Definition Language (XSD) file.</span></span> <span data-ttu-id="7e59a-104">Další informace naleznete <xref:System.Xml.Schema.Extensions.Validate%2A> v dokumentaci k metodě.</span><span class="sxs-lookup"><span data-stu-id="7e59a-104">For more information, see the <xref:System.Xml.Schema.Extensions.Validate%2A> method documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e59a-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="7e59a-105">Example</span></span>  
 <span data-ttu-id="7e59a-106">Následující příklad vytvoří <xref:System.Xml.Schema.XmlSchemaSet>, pak <xref:System.Xml.Linq.XDocument> ověří dva objekty proti sadě schématu.</span><span class="sxs-lookup"><span data-stu-id="7e59a-106">The following example creates an <xref:System.Xml.Schema.XmlSchemaSet>, then validates two <xref:System.Xml.Linq.XDocument> objects against the schema set.</span></span> <span data-ttu-id="7e59a-107">Jeden z dokumentů je platný, druhý ne.</span><span class="sxs-lookup"><span data-stu-id="7e59a-107">One of the documents is valid, the other is not.</span></span>  
  
```csharp  
string xsdMarkup =  
    @"<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'>  
       <xsd:element name='Root'>  
        <xsd:complexType>  
         <xsd:sequence>  
          <xsd:element name='Child1' minOccurs='1' maxOccurs='1'/>  
          <xsd:element name='Child2' minOccurs='1' maxOccurs='1'/>  
         </xsd:sequence>  
        </xsd:complexType>  
       </xsd:element>  
      </xsd:schema>";  
XmlSchemaSet schemas = new XmlSchemaSet();  
schemas.Add("", XmlReader.Create(new StringReader(xsdMarkup)));  
  
XDocument doc1 = new XDocument(  
    new XElement("Root",  
        new XElement("Child1", "content1"),  
        new XElement("Child2", "content1")  
    )  
);  
  
XDocument doc2 = new XDocument(  
    new XElement("Root",  
        new XElement("Child1", "content1"),  
        new XElement("Child3", "content1")  
    )  
);  
  
Console.WriteLine("Validating doc1");  
bool errors = false;  
doc1.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("doc1 {0}", errors ? "did not validate" : "validated");  
  
Console.WriteLine();  
Console.WriteLine("Validating doc2");  
errors = false;  
doc2.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("doc2 {0}", errors ? "did not validate" : "validated");  
```  
  
 <span data-ttu-id="7e59a-108">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="7e59a-108">This example produces the following output:</span></span>  
  
```output  
Validating doc1  
doc1 validated  
  
Validating doc2  
The element 'Root' has invalid child element 'Child3'. List of possible elements expected: 'Child2'.  
doc2 did not validate  
```  
  
## <a name="example"></a><span data-ttu-id="7e59a-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="7e59a-109">Example</span></span>  
 <span data-ttu-id="7e59a-110">Následující příklad ověří, zda je dokument XML z [ukázkového souboru XML: Zákazníci a objednávky (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) je platný podle schématu z [ukázkového souboru XSD: Zákazníci a objednávky](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="7e59a-110">The following example validates that the XML document from [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) is valid per the schema from [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="7e59a-111">Poté upraví zdrojový dokument XML.</span><span class="sxs-lookup"><span data-stu-id="7e59a-111">It then modifies the source XML document.</span></span> <span data-ttu-id="7e59a-112">Změní `CustomerID` atribut u prvního zákazníka.</span><span class="sxs-lookup"><span data-stu-id="7e59a-112">It changes the `CustomerID` attribute on the first customer.</span></span> <span data-ttu-id="7e59a-113">Po změně budou objednávky odkazovat na zákazníka, který neexistuje, takže dokument XML již nebude ověřovat.</span><span class="sxs-lookup"><span data-stu-id="7e59a-113">After the change, orders will then refer to a customer that does not exist, so the XML document will no longer validate.</span></span>  
  
 <span data-ttu-id="7e59a-114">Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML).](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)</span><span class="sxs-lookup"><span data-stu-id="7e59a-114">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
 <span data-ttu-id="7e59a-115">Tento příklad používá následující schéma XSD: [Ukázkový soubor XSD: Zákazníci a objednávky](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="7e59a-115">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span>  
  
```csharp  
XmlSchemaSet schemas = new XmlSchemaSet();  
schemas.Add("", "CustomersOrders.xsd");  
  
Console.WriteLine("Attempting to validate");  
XDocument custOrdDoc = XDocument.Load("CustomersOrders.xml");  
bool errors = false;  
custOrdDoc.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");  
  
Console.WriteLine();  
// Modify the source document so that it will not validate.  
custOrdDoc.Root.Element("Orders").Element("Order").Element("CustomerID").Value = "AAAAA";  
Console.WriteLine("Attempting to validate after modification");  
errors = false;  
custOrdDoc.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");  
```  
  
 <span data-ttu-id="7e59a-116">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="7e59a-116">This example produces the following output:</span></span>  
  
```output  
Attempting to validate  
custOrdDoc validated  
  
Attempting to validate after modification  
The key sequence 'AAAAA' in Keyref fails to refer to some key.  
custOrdDoc did not validate  
```  
  
## <a name="see-also"></a><span data-ttu-id="7e59a-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e59a-117">See also</span></span>

- <xref:System.Xml.Schema.Extensions.Validate%2A>
- [<span data-ttu-id="7e59a-118">Vytváření stromů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="7e59a-118">Creating XML Trees (C#)</span></span>](creating-xml-trees-linq-to-xml-2.md)
