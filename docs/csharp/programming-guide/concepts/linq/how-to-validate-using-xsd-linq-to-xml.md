---
title: Jak ověřit pomocí XSD (LINQ to XML) (C#)
description: Přečtěte si, jak ověřit strom XML proti souboru XSD (Schema Definition Language) XML. Podívejte se na příklady kódu a zobrazte další prostředky.
ms.date: 07/20/2015
ms.assetid: 6a7f83a9-2d74-4c2b-8417-0a8595879516
ms.openlocfilehash: 3b4d2137d511efbe20e4d31ad27e4975d5444ec9
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302630"
---
# <a name="how-to-validate-using-xsd-linq-to-xml-c"></a><span data-ttu-id="d0489-104">Jak ověřit pomocí XSD (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d0489-104">How to validate using XSD (LINQ to XML) (C#)</span></span>
<span data-ttu-id="d0489-105"><xref:System.Xml.Schema>Obor názvů obsahuje metody rozšíření, které usnadňují ověřování stromu XML proti souboru XSD (XML Schema Definition Language).</span><span class="sxs-lookup"><span data-stu-id="d0489-105">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XML Schema Definition Language (XSD) file.</span></span> <span data-ttu-id="d0489-106">Další informace najdete v <xref:System.Xml.Schema.Extensions.Validate%2A> dokumentaci k metodě.</span><span class="sxs-lookup"><span data-stu-id="d0489-106">For more information, see the <xref:System.Xml.Schema.Extensions.Validate%2A> method documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0489-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="d0489-107">Example</span></span>  
 <span data-ttu-id="d0489-108">Následující příklad vytvoří <xref:System.Xml.Schema.XmlSchemaSet> a potom ověří dva <xref:System.Xml.Linq.XDocument> objekty proti sadě schémat.</span><span class="sxs-lookup"><span data-stu-id="d0489-108">The following example creates an <xref:System.Xml.Schema.XmlSchemaSet>, then validates two <xref:System.Xml.Linq.XDocument> objects against the schema set.</span></span> <span data-ttu-id="d0489-109">Jeden z dokumentů je platný, druhý není.</span><span class="sxs-lookup"><span data-stu-id="d0489-109">One of the documents is valid, the other is not.</span></span>  
  
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
  
 <span data-ttu-id="d0489-110">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d0489-110">This example produces the following output:</span></span>  
  
```output  
Validating doc1  
doc1 validated  
  
Validating doc2  
The element 'Root' has invalid child element 'Child3'. List of possible elements expected: 'Child2'.  
doc2 did not validate  
```  
  
## <a name="example"></a><span data-ttu-id="d0489-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="d0489-111">Example</span></span>  
 <span data-ttu-id="d0489-112">Následující příklad ověřuje, že dokument XML z [ukázkového souboru XML: zákazníci a objednávky (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) jsou platné pro schéma z [ukázkového souboru XSD: zákazníci a objednávky](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="d0489-112">The following example validates that the XML document from [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) is valid per the schema from [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="d0489-113">Pak upraví zdrojový dokument XML.</span><span class="sxs-lookup"><span data-stu-id="d0489-113">It then modifies the source XML document.</span></span> <span data-ttu-id="d0489-114">Změní `CustomerID` atribut prvního zákazníka.</span><span class="sxs-lookup"><span data-stu-id="d0489-114">It changes the `CustomerID` attribute on the first customer.</span></span> <span data-ttu-id="d0489-115">Po změně budou objednávky odkazovat na zákazníka, který neexistuje, takže dokument XML nebude nadále ověřen.</span><span class="sxs-lookup"><span data-stu-id="d0489-115">After the change, orders will then refer to a customer that does not exist, so the XML document will no longer validate.</span></span>  
  
 <span data-ttu-id="d0489-116">Tento příklad používá následující dokument XML: [ukázkový soubor XML: zákazníci a objednávky (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="d0489-116">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
 <span data-ttu-id="d0489-117">V tomto příkladu se používá následující schéma XSD: [ukázkový soubor XSD: zákazníci a objednávky](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="d0489-117">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span>  
  
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
  
 <span data-ttu-id="d0489-118">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d0489-118">This example produces the following output:</span></span>  
  
```output  
Attempting to validate  
custOrdDoc validated  
  
Attempting to validate after modification  
The key sequence 'AAAAA' in Keyref fails to refer to some key.  
custOrdDoc did not validate  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0489-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d0489-119">See also</span></span>

- <xref:System.Xml.Schema.Extensions.Validate%2A>
- [<span data-ttu-id="d0489-120">Vytváření stromů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="d0489-120">Creating XML Trees (C#)</span></span>](creating-xml-trees-linq-to-xml-2.md)
