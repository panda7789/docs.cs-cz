---
title: 'Postupy: Ověření pomocí XSD (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 6a7f83a9-2d74-4c2b-8417-0a8595879516
ms.openlocfilehash: eea274380cd9b1a601059c12ee7bf654dff10437
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667506"
---
# <a name="how-to-validate-using-xsd-linq-to-xml-c"></a><span data-ttu-id="56a51-102">Postupy: Ověření pomocí XSD (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="56a51-102">How to: Validate Using XSD (LINQ to XML) (C#)</span></span>
<span data-ttu-id="56a51-103"><xref:System.Xml.Schema> Obor názvů obsahuje rozšiřující metody, které usnadňují ověřit stromu XML pro soubor jazyka pro definici schématu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="56a51-103">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XML Schema Definition Language (XSD) file.</span></span> <span data-ttu-id="56a51-104">Další informace najdete v tématu <xref:System.Xml.Schema.Extensions.Validate%2A> metoda dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="56a51-104">For more information, see the <xref:System.Xml.Schema.Extensions.Validate%2A> method documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56a51-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="56a51-105">Example</span></span>  
 <span data-ttu-id="56a51-106">Následující příklad vytvoří <xref:System.Xml.Schema.XmlSchemaSet>, pak ověří dvě <xref:System.Xml.Linq.XDocument> objekty oproti sadě schémat.</span><span class="sxs-lookup"><span data-stu-id="56a51-106">The following example creates an <xref:System.Xml.Schema.XmlSchemaSet>, then validates two <xref:System.Xml.Linq.XDocument> objects against the schema set.</span></span> <span data-ttu-id="56a51-107">Jeden z dokumentů je platný, druhý není.</span><span class="sxs-lookup"><span data-stu-id="56a51-107">One of the documents is valid, the other is not.</span></span>  
  
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
  
 <span data-ttu-id="56a51-108">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="56a51-108">This example produces the following output:</span></span>  
  
```  
Validating doc1  
doc1 validated  
  
Validating doc2  
The element 'Root' has invalid child element 'Child3'. List of possible elements expected: 'Child2'.  
doc2 did not validate  
```  
  
## <a name="example"></a><span data-ttu-id="56a51-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="56a51-109">Example</span></span>  
 <span data-ttu-id="56a51-110">Následující příklad ověří, že dokument XML z [ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md) je platný podle schématu z [ukázkový soubor XSD: Zákazníci a objednávky](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="56a51-110">The following example validates that the XML document from [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md) is valid per the schema from [Sample XSD File: Customers and Orders](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="56a51-111">Poté změní zdrojovém dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="56a51-111">It then modifies the source XML document.</span></span> <span data-ttu-id="56a51-112">Změní `CustomerID` atribut na první zákazníka.</span><span class="sxs-lookup"><span data-stu-id="56a51-112">It changes the `CustomerID` attribute on the first customer.</span></span> <span data-ttu-id="56a51-113">Po provedení změny objednávky pak vrátíme se k zákazníkovi, který neexistuje, tak se již neověřují dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="56a51-113">After the change, orders will then refer to a customer that does not exist, so the XML document will no longer validate.</span></span>  
  
 <span data-ttu-id="56a51-114">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Zákazníci a objednávky (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="56a51-114">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
 <span data-ttu-id="56a51-115">Tento příklad používá následující schéma XSD: [Ukázkový soubor XSD: Zákazníci a objednávky](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="56a51-115">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span></span>  
  
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
  
 <span data-ttu-id="56a51-116">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="56a51-116">This example produces the following output:</span></span>  
  
```  
Attempting to validate  
custOrdDoc validated  
  
Attempting to validate after modification  
The key sequence 'AAAAA' in Keyref fails to refer to some key.  
custOrdDoc did not validate  
```  
  
## <a name="see-also"></a><span data-ttu-id="56a51-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56a51-117">See also</span></span>

- <xref:System.Xml.Schema.Extensions.Validate%2A>
- [<span data-ttu-id="56a51-118">Vytváření stromů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="56a51-118">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
