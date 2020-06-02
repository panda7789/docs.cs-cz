---
title: Ověření schématu XML (XSD) s třídou XmlSchemaSet
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
ms.openlocfilehash: 1729380180d4440ac107885a39eff706c7fc8e5c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290289"
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a><span data-ttu-id="5154c-102">Ověřování schématu XML (XSD) pomocí jazyka XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="5154c-102">XML schema (XSD) validation with XmlSchemaSet</span></span>

<span data-ttu-id="5154c-103">Dokumenty XML lze ověřit podle schématu XML schématu definice jazyka (XSD) v <xref:System.Xml.Schema.XmlSchemaSet> .</span><span class="sxs-lookup"><span data-stu-id="5154c-103">XML documents can be validated against an XML schema definition language (XSD) schema in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
## <a name="validate-xml-documents"></a><span data-ttu-id="5154c-104">Ověřit dokumenty XML</span><span class="sxs-lookup"><span data-stu-id="5154c-104">Validate XML documents</span></span>  
 <span data-ttu-id="5154c-105">Dokumenty XML jsou ověřovány <xref:System.Xml.XmlReader.Create%2A> metodou <xref:System.Xml.XmlReader> třídy.</span><span class="sxs-lookup"><span data-stu-id="5154c-105">XML documents are validated by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class.</span></span> <span data-ttu-id="5154c-106">Chcete-li ověřit dokument XML, sestavte <xref:System.Xml.XmlReaderSettings> objekt, který obsahuje schéma XML schématu definice jazyk (XSD), pomocí kterého lze ověřit dokument XML.</span><span class="sxs-lookup"><span data-stu-id="5154c-106">To validate an XML document, construct an <xref:System.Xml.XmlReaderSettings> object that contains an XML schema definition language (XSD) schema with which to validate the XML document.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5154c-107"><xref:System.Xml.Schema>Obor názvů obsahuje metody rozšíření, které usnadňují ověření stromu XML proti souboru XSD při použití [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) a [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="5154c-107">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XSD file when using [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span></span> <span data-ttu-id="5154c-108">Další informace o ověřování dokumentů XML pomocí LINQ to XML naleznete v tématu [Jak ověřit pomocí XSD (LINQ to XML) (C#)](../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) a [Postupy: ověřování pomocí XSD (LINQ to XML) (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="5154c-108">For more information on validating XML documents with LINQ to XML, see [How to validate using XSD (LINQ to XML) (C#)](../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) and [How to: Validate Using XSD (LINQ to XML) (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md).</span></span>
  
 <span data-ttu-id="5154c-109">Jednotlivá schémata nebo sada schémat (jako <xref:System.Xml.Schema.XmlSchemaSet> ) lze přidat do prvku <xref:System.Xml.Schema.XmlSchemaSet> předáním jednoho jako parametru <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metodě <xref:System.Xml.Schema.XmlSchemaSet> .</span><span class="sxs-lookup"><span data-stu-id="5154c-109">An individual schema or a set of schemas (as an <xref:System.Xml.Schema.XmlSchemaSet>) can be added to an <xref:System.Xml.Schema.XmlSchemaSet> by passing either one as a parameter to the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="5154c-110">Při ověřování dokumentu se cílový obor názvů dokumentu musí shodovat s cílovým oborem názvů schématu v sadě schémat.</span><span class="sxs-lookup"><span data-stu-id="5154c-110">When validating a document the target namespace of the document must match the target namespace of the schema in the schema set.</span></span>  
  
 <span data-ttu-id="5154c-111">Následuje příklad dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="5154c-111">The following is an example XML document.</span></span>  
  
 [!code-xml[XSDInference Examples #5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 <span data-ttu-id="5154c-112">Následuje schéma, které ověřuje ukázkový dokument XML.</span><span class="sxs-lookup"><span data-stu-id="5154c-112">The following is the schema that validates the example XML document.</span></span>  
  
 [!code-xml[XSDInference Examples #6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 <span data-ttu-id="5154c-113">V následujícím příkladu kódu je schéma přidáno do <xref:System.Xml.XmlReaderSettings.Schemas%2A> vlastnosti <xref:System.Xml.XmlReaderSettings> objektu.</span><span class="sxs-lookup"><span data-stu-id="5154c-113">In the code example that follows, the schema above is added to the <xref:System.Xml.XmlReaderSettings.Schemas%2A> property of the <xref:System.Xml.XmlReaderSettings> object.</span></span> <span data-ttu-id="5154c-114"><xref:System.Xml.XmlReaderSettings>Objekt je předán jako parametr <xref:System.Xml.XmlReader.Create%2A> metodě <xref:System.Xml.XmlReader> objektu, který ověřuje dokument XML výše.</span><span class="sxs-lookup"><span data-stu-id="5154c-114">The <xref:System.Xml.XmlReaderSettings> object is passed as a parameter to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> object, which validates the XML document above.</span></span>  
  
 <span data-ttu-id="5154c-115"><xref:System.Xml.XmlReaderSettings.ValidationType%2A>Vlastnost <xref:System.Xml.XmlReaderSettings> objektu je nastavena na hodnotu `Schema` pro vymáhání ověřování dokumentu XML <xref:System.Xml.XmlReader.Create%2A> metodou <xref:System.Xml.XmlReader> objektu.</span><span class="sxs-lookup"><span data-stu-id="5154c-115">The <xref:System.Xml.XmlReaderSettings.ValidationType%2A> property of the <xref:System.Xml.XmlReaderSettings> object is set to `Schema` to enforce validation of the XML document by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="5154c-116">A <xref:System.Xml.Schema.ValidationEventHandler> je přidán k <xref:System.Xml.XmlReaderSettings> objektu, který bude zpracovávat <xref:System.Xml.Schema.XmlSeverityType.Warning> události, které <xref:System.Xml.Schema.XmlSeverityType.Error> byly vyvolány chybami zjištěnými během procesu ověřování dokumentu XML i schématu.</span><span class="sxs-lookup"><span data-stu-id="5154c-116">A <xref:System.Xml.Schema.ValidationEventHandler> is added to the <xref:System.Xml.XmlReaderSettings> object to handle any <xref:System.Xml.Schema.XmlSeverityType.Warning> or <xref:System.Xml.Schema.XmlSeverityType.Error> events raised by errors found during the validation process of both the XML document and the schema.</span></span>  
  
 [!code-cpp[XmlSchemaSetOverall Example #1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example #1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example #1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5154c-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="5154c-117">See also</span></span>

- [<span data-ttu-id="5154c-118">XmlSchemaSet pro kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="5154c-118">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="5154c-119">Práce se schématy XML</span><span class="sxs-lookup"><span data-stu-id="5154c-119">Working with XML Schemas</span></span>](working-with-xml-schemas.md)
