---
title: Ověření schématu XML (XSD) s třídou XmlSchemaSet
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9bdcfe785d6f5f81d721acd45eebb580b08b2d14
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916074"
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a><span data-ttu-id="7f382-102">Ověření schématu XML (XSD) s třídou XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="7f382-102">XML Schema (XSD) Validation with XmlSchemaSet</span></span>
<span data-ttu-id="7f382-103">Dokumenty XML lze ověřit podle schématu XML schématu definice jazyka (XSD) v <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="7f382-103">XML documents can be validated against an XML schema definition language (XSD) schema in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
## <a name="validating-xml-documents"></a><span data-ttu-id="7f382-104">Ověřování dokumentů XML</span><span class="sxs-lookup"><span data-stu-id="7f382-104">Validating XML Documents</span></span>  
 <span data-ttu-id="7f382-105">Dokumenty XML jsou ověřovány <xref:System.Xml.XmlReader.Create%2A> metodou <xref:System.Xml.XmlReader> třídy.</span><span class="sxs-lookup"><span data-stu-id="7f382-105">XML documents are validated by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class.</span></span> <span data-ttu-id="7f382-106">Chcete-li ověřit dokument XML, sestavte <xref:System.Xml.XmlReaderSettings> objekt, který obsahuje schéma XML schématu definice jazyk (XSD), pomocí kterého lze ověřit dokument XML.</span><span class="sxs-lookup"><span data-stu-id="7f382-106">To validate an XML document, construct an <xref:System.Xml.XmlReaderSettings> object that contains an XML schema definition language (XSD) schema with which to validate the XML document.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7f382-107">Obor názvů obsahuje metody rozšíření, které usnadňují ověření stromu XML proti souboru XSD při použití [LINQ to XMLC#()](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) a [LINQ to XML (Visual Basic).](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) <xref:System.Xml.Schema></span><span class="sxs-lookup"><span data-stu-id="7f382-107">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XSD file when using [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span></span> <span data-ttu-id="7f382-108">Další informace o ověřování dokumentů XML pomocí LINQ to XML naleznete v tématu [How to: Ověřte pomocí XSD (LINQ to XML) (C#)](../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) a [postupy: Ověřte pomocí XSD (LINQ to XML) (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7f382-108">For more information on validating XML documents with LINQ to XML, see [How to: Validate Using XSD (LINQ to XML) (C#)](../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) and [How to: Validate Using XSD (LINQ to XML) (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="7f382-109">Jednotlivá schémata nebo sada <xref:System.Xml.Schema.XmlSchemaSet>schémat (jako) lze přidat do prvku <xref:System.Xml.Schema.XmlSchemaSet> předáním jednoho <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> jako <xref:System.Xml.Schema.XmlSchemaSet>parametru metodě.</span><span class="sxs-lookup"><span data-stu-id="7f382-109">An individual schema or a set of schemas (as an <xref:System.Xml.Schema.XmlSchemaSet>) can be added to an <xref:System.Xml.Schema.XmlSchemaSet> by passing either one as a parameter to the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="7f382-110">Všimněte si, že při ověřování dokumentu se cílový obor názvů dokumentu musí shodovat s cílovým oborem názvů schématu v sadě schémat.</span><span class="sxs-lookup"><span data-stu-id="7f382-110">Note that when validating a document the target namespace of the document must match the target namespace of the schema in the schema set.</span></span>  
  
 <span data-ttu-id="7f382-111">Následuje příklad dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="7f382-111">The following is an example XML document.</span></span>  
  
 [!code-xml[XSDInference Examples#5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 <span data-ttu-id="7f382-112">Následuje schéma, které ověřuje ukázkový dokument XML.</span><span class="sxs-lookup"><span data-stu-id="7f382-112">The following is the schema that validates the example XML document.</span></span>  
  
 [!code-xml[XSDInference Examples#6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 <span data-ttu-id="7f382-113">V následujícím příkladu kódu je schéma přidáno do <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> vlastnosti <xref:System.Xml.XmlReaderSettings> objektu.</span><span class="sxs-lookup"><span data-stu-id="7f382-113">In the code example that follows, the schema above is added to the <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> property of the <xref:System.Xml.XmlReaderSettings> object.</span></span> <span data-ttu-id="7f382-114">Objekt je předán jako parametr <xref:System.Xml.XmlReader.Create%2A> metodě <xref:System.Xml.XmlReader> objektu, který ověřuje dokument XML výše. <xref:System.Xml.XmlReaderSettings></span><span class="sxs-lookup"><span data-stu-id="7f382-114">The <xref:System.Xml.XmlReaderSettings> object is passed as a parameter to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> object, which validates the XML document above.</span></span>  
  
 <span data-ttu-id="7f382-115">`Schema` <xref:System.Xml.XmlReader.Create%2A> Vlastnost objektu je nastavena na hodnotu pro vymáhání ověřování dokumentu XML metodou <xref:System.Xml.XmlReader> objektu. <xref:System.Xml.XmlReaderSettings> <xref:System.Xml.XmlReaderSettings.ValidationType%2A></span><span class="sxs-lookup"><span data-stu-id="7f382-115">The <xref:System.Xml.XmlReaderSettings.ValidationType%2A> property of the <xref:System.Xml.XmlReaderSettings> object is set to `Schema` to enforce validation of the XML document by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="7f382-116">A <xref:System.Xml.Schema.ValidationEventHandler> je přidán <xref:System.Xml.XmlReaderSettings> k objektu, který bude zpracovávat <xref:System.Xml.Schema.XmlSeverityType.Warning> události <xref:System.Xml.Schema.XmlSeverityType.Error> , které byly vyvolány chybami zjištěnými během procesu ověřování dokumentu XML i schématu.</span><span class="sxs-lookup"><span data-stu-id="7f382-116">A <xref:System.Xml.Schema.ValidationEventHandler> is added to the <xref:System.Xml.XmlReaderSettings> object to handle any <xref:System.Xml.Schema.XmlSeverityType.Warning> or <xref:System.Xml.Schema.XmlSeverityType.Error> events raised by errors found during the validation process of both the XML document and the schema.</span></span>  
  
 [!code-cpp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7f382-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7f382-117">See also</span></span>

- [<span data-ttu-id="7f382-118">XmlSchemaSet pro kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="7f382-118">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="7f382-119">Práce se schématy XML</span><span class="sxs-lookup"><span data-stu-id="7f382-119">Working with XML Schemas</span></span>](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
