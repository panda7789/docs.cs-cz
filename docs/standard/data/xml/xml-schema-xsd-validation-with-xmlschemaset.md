---
title: "Ověření schématu (XSD) XML s XmlSchemaSet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 99e2f66a1aedafe316ab65ae302113ea553146ed
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a><span data-ttu-id="df5cb-102">Ověření schématu (XSD) XML s XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="df5cb-102">XML Schema (XSD) Validation with XmlSchemaSet</span></span>
<span data-ttu-id="df5cb-103">Dokumenty XML můžete ověřit pomocí schématu XML schéma definition language (XSD) v <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="df5cb-103">XML documents can be validated against an XML schema definition language (XSD) schema in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
## <a name="validating-xml-documents"></a><span data-ttu-id="df5cb-104">Ověření XML – dokumenty</span><span class="sxs-lookup"><span data-stu-id="df5cb-104">Validating XML Documents</span></span>  
 <span data-ttu-id="df5cb-105">Dokumenty XML ověřuje <xref:System.Xml.XmlReader.Create%2A> metodu <xref:System.Xml.XmlReader> třídy.</span><span class="sxs-lookup"><span data-stu-id="df5cb-105">XML documents are validated by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class.</span></span> <span data-ttu-id="df5cb-106">K ověření dokument XML, vytvořit <xref:System.Xml.XmlReaderSettings> objekt, který obsahuje schématu XML schématu definition language (XSD) ke které má být ověření v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="df5cb-106">To validate an XML document, construct an <xref:System.Xml.XmlReaderSettings> object that contains an XML schema definition language (XSD) schema with which to validate the XML document.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df5cb-107"><xref:System.Xml.Schema> Obor názvů obsahuje rozšiřující metody, které usnadňují ověření strom XML proti soubor XSD při použití [technologie LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</span><span class="sxs-lookup"><span data-stu-id="df5cb-107">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XSD file when using [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</span></span> <span data-ttu-id="df5cb-108">Další informace o ověřování dokumentů XML pomocí LINQ to XML, najdete v části [postupy: ověření pomocí XSD](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b).</span><span class="sxs-lookup"><span data-stu-id="df5cb-108">For more information on validating XML documents with LINQ to XML, see [How to: Validate Using XSD](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b).</span></span>  
  
 <span data-ttu-id="df5cb-109">Jednotlivé schéma nebo sadu schémata (jako <xref:System.Xml.Schema.XmlSchemaSet>) mohou být přidány do <xref:System.Xml.Schema.XmlSchemaSet> předáním buď jeden jako parametr, který se <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metodu <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="df5cb-109">An individual schema or a set of schemas (as an <xref:System.Xml.Schema.XmlSchemaSet>) can be added to an <xref:System.Xml.Schema.XmlSchemaSet> by passing either one as a parameter to the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="df5cb-110">Všimněte si, že při ověřování dokumentu se musí shodovat cílový obor názvů dokumentu cílový obor názvů schématu v sadě schématu.</span><span class="sxs-lookup"><span data-stu-id="df5cb-110">Note that when validating a document the target namespace of the document must match the target namespace of the schema in the schema set.</span></span>  
  
 <span data-ttu-id="df5cb-111">Následuje příklad XML dokumentu.</span><span class="sxs-lookup"><span data-stu-id="df5cb-111">The following is an example XML document.</span></span>  
  
 [!code-xml[XSDInference Examples#5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 <span data-ttu-id="df5cb-112">Toto je schématu, která ověřuje ukázkový dokument XML.</span><span class="sxs-lookup"><span data-stu-id="df5cb-112">The following is the schema that validates the example XML document.</span></span>  
  
 [!code-xml[XSDInference Examples#6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 <span data-ttu-id="df5cb-113">V následujícím příkladu kódu je do výše uvedeného schématu <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> vlastnost <xref:System.Xml.XmlReaderSettings> objektu.</span><span class="sxs-lookup"><span data-stu-id="df5cb-113">In the code example that follows, the schema above is added to the <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> property of the <xref:System.Xml.XmlReaderSettings> object.</span></span> <span data-ttu-id="df5cb-114"><xref:System.Xml.XmlReaderSettings> Objekt je předán jako parametr, který se <xref:System.Xml.XmlReader.Create%2A> metodu <xref:System.Xml.XmlReader> objekt, který ověří výše dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="df5cb-114">The <xref:System.Xml.XmlReaderSettings> object is passed as a parameter to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> object, which validates the XML document above.</span></span>  
  
 <span data-ttu-id="df5cb-115"><xref:System.Xml.XmlReaderSettings.ValidationType%2A> Vlastnost <xref:System.Xml.XmlReaderSettings> objektu na hodnotu `Schema` k vynucení ověřování dokumentu XML pomocí <xref:System.Xml.XmlReader.Create%2A> metodu <xref:System.Xml.XmlReader> objektu.</span><span class="sxs-lookup"><span data-stu-id="df5cb-115">The <xref:System.Xml.XmlReaderSettings.ValidationType%2A> property of the <xref:System.Xml.XmlReaderSettings> object is set to `Schema` to enforce validation of the XML document by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="df5cb-116">A <xref:System.Xml.Schema.ValidationEventHandler> je přidán do <xref:System.Xml.XmlReaderSettings> objekt zpracována <xref:System.Xml.Schema.XmlSeverityType.Warning> nebo <xref:System.Xml.Schema.XmlSeverityType.Error> události vyvolané službou chyby nalezené během procesu ověřování v dokumentu XML a schéma.</span><span class="sxs-lookup"><span data-stu-id="df5cb-116">A <xref:System.Xml.Schema.ValidationEventHandler> is added to the <xref:System.Xml.XmlReaderSettings> object to handle any <xref:System.Xml.Schema.XmlSeverityType.Warning> or <xref:System.Xml.Schema.XmlSeverityType.Error> events raised by errors found during the validation process of both the XML document and the schema.</span></span>  
  
 [!code-cpp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="df5cb-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="df5cb-117">See Also</span></span>  
 [<span data-ttu-id="df5cb-118">XmlSchemaSet pro kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="df5cb-118">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [<span data-ttu-id="df5cb-119">Práce se schématy XML</span><span class="sxs-lookup"><span data-stu-id="df5cb-119">Working with XML Schemas</span></span>](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
