---
title: 'Postupy: ověření pomocí XSD (technologie LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 6a7f83a9-2d74-4c2b-8417-0a8595879516
ms.openlocfilehash: 9b26481eb1e0fd103f92ed56e0e2f7c83d2ccbb5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33321594"
---
# <a name="how-to-validate-using-xsd-linq-to-xml-c"></a><span data-ttu-id="6d5b8-102">Postupy: ověření pomocí XSD (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="6d5b8-102">How to: Validate Using XSD (LINQ to XML) (C#)</span></span>
<span data-ttu-id="6d5b8-103"><xref:System.Xml.Schema> Obor názvů obsahuje rozšiřující metody, které usnadňují ověření strom XML proti soubor schématu definice jazyka XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="6d5b8-103">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XML Schema Definition Language (XSD) file.</span></span> <span data-ttu-id="6d5b8-104">Další informace najdete v tématu <xref:System.Xml.Schema.Extensions.Validate%2A> metoda dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="6d5b8-104">For more information, see the <xref:System.Xml.Schema.Extensions.Validate%2A> method documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d5b8-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="6d5b8-105">Example</span></span>  
 <span data-ttu-id="6d5b8-106">Následující příklad vytvoří <xref:System.Xml.Schema.XmlSchemaSet>, pak ověří dva <xref:System.Xml.Linq.XDocument> objektů pro sadu schématu.</span><span class="sxs-lookup"><span data-stu-id="6d5b8-106">The following example creates an <xref:System.Xml.Schema.XmlSchemaSet>, then validates two <xref:System.Xml.Linq.XDocument> objects against the schema set.</span></span> <span data-ttu-id="6d5b8-107">Jeden z dokumentů je platný, druhý není.</span><span class="sxs-lookup"><span data-stu-id="6d5b8-107">One of the documents is valid, the other is not.</span></span>  
  
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
  
 <span data-ttu-id="6d5b8-108">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6d5b8-108">This example produces the following output:</span></span>  
  
```  
Validating doc1  
doc1 validated  
  
Validating doc2  
The element 'Root' has invalid child element 'Child3'. List of possible elements expected: 'Child2'.  
doc2 did not validate  
```  
  
## <a name="example"></a><span data-ttu-id="6d5b8-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="6d5b8-109">Example</span></span>  
 <span data-ttu-id="6d5b8-110">Následující příklad ověří, že dokument XML z [ukázkový soubor XML: Zákazníci a objednávky (technologie LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md) platný podle schématu z [ukázkový soubor XSD: Zákazníci a objednávky](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="6d5b8-110">The following example validates that the XML document from [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md) is valid per the schema from [Sample XSD File: Customers and Orders](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="6d5b8-111">Pak upravením zdrojový dokument XML.</span><span class="sxs-lookup"><span data-stu-id="6d5b8-111">It then modifies the source XML document.</span></span> <span data-ttu-id="6d5b8-112">Změní `CustomerID` atribut na první zákazníka.</span><span class="sxs-lookup"><span data-stu-id="6d5b8-112">It changes the `CustomerID` attribute on the first customer.</span></span> <span data-ttu-id="6d5b8-113">Po provedení změny objednávky bude pak odkazovat zákazníkovi, který neexistuje, abyste v dokumentu XML se už ověřit.</span><span class="sxs-lookup"><span data-stu-id="6d5b8-113">After the change, orders will then refer to a customer that does not exist, so the XML document will no longer validate.</span></span>  
  
 <span data-ttu-id="6d5b8-114">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: Zákazníci a objednávky (technologie LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="6d5b8-114">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
 <span data-ttu-id="6d5b8-115">Tento příklad používá následující schéma XSD: [ukázkový soubor XSD: Zákazníci a objednávky](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="6d5b8-115">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span></span>  
  
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
  
 <span data-ttu-id="6d5b8-116">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6d5b8-116">This example produces the following output:</span></span>  
  
```  
Attempting to validate  
custOrdDoc validated  
  
Attempting to validate after modification  
The key sequence 'AAAAA' in Keyref fails to refer to some key.  
custOrdDoc did not validate  
```  
  
## <a name="see-also"></a><span data-ttu-id="6d5b8-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d5b8-117">See Also</span></span>  
 <xref:System.Xml.Schema.Extensions.Validate%2A>  
 [<span data-ttu-id="6d5b8-118">Vytváření stromů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="6d5b8-118">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
