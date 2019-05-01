---
title: Práce se schématy XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: bbbcc70c-bf9a-4f6a-af72-1bab5384a187
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83fddd00f44b184fa066f6c47b90b01fac7ef7bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959105"
---
# <a name="working-with-xml-schemas"></a><span data-ttu-id="8840d-102">Práce se schématy XML</span><span class="sxs-lookup"><span data-stu-id="8840d-102">Working with XML Schemas</span></span>
<span data-ttu-id="8840d-103">Pokud chcete definovat strukturu dokumentu XML, jakož i jeho element relace, datových typů a omezení obsahu, použijete definice typu dokumentu (DTD) nebo jazyk (XSD) schématu definice schématu XML.</span><span class="sxs-lookup"><span data-stu-id="8840d-103">To define the structure of an XML document, as well as its element relationships, data types, and content constraints, you use a document type definition (DTD) or XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="8840d-104">I když dokumentu XML se považuje za ve správném formátu, pokud splňuje všechny požadavky syntaktické určené World Wide Web Consortium (W3C) doporučení značek XML (Extensible Language) 1.0, není považováno za platný i není ve správném formátu a podřídí omezením určené jeho DTD nebo schématu.</span><span class="sxs-lookup"><span data-stu-id="8840d-104">Although an XML document is considered to be well-formed if it meets all the syntactical requirements defined by the World Wide Web Consortium (W3C) Extensible Markup Language (XML) 1.0 Recommendation, it is not considered valid unless it is both well-formed and conforms to the constraints defined by its DTD or schema.</span></span> <span data-ttu-id="8840d-105">Proto i když jsou všechny platné dokumenty XML ve správném formátu, ne všechny dokumenty ve správném formátu XML jsou platné.</span><span class="sxs-lookup"><span data-stu-id="8840d-105">Therefore, although all valid XML documents are well-formed, not all well-formed XML documents are valid.</span></span>  
  
 <span data-ttu-id="8840d-106">Další informace o XML, najdete v článku [W3C XML 1.0 doporučení](https://www.w3.org/TR/REC-xml/).</span><span class="sxs-lookup"><span data-stu-id="8840d-106">For more information about XML, see the [W3C XML 1.0 Recommendation](https://www.w3.org/TR/REC-xml/).</span></span> <span data-ttu-id="8840d-107">Další informace o schématu XML, najdete v článku [části 1 W3C XML schématu: Struktury doporučení](https://www.w3.org/TR/xmlschema-1/) a [W3C XML schématu část 2: Datové typy doporučení](https://www.w3.org/TR/xmlschema-2/) doporučení.</span><span class="sxs-lookup"><span data-stu-id="8840d-107">For more information about XML Schema, see the [W3C XML Schema Part 1: Structures Recommendation](https://www.w3.org/TR/xmlschema-1/) and the [W3C XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/) recommendations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8840d-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="8840d-108">In This Section</span></span>  
 [<span data-ttu-id="8840d-109">Model objektu schématu (SOM) XML</span><span class="sxs-lookup"><span data-stu-id="8840d-109">XML Schema Object Model (SOM)</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 <span data-ttu-id="8840d-110">Tento článek popisuje Model objektu schématu (SOM) v <xref:System.Xml.Schema?displayProperty=nameWithType> obor názvů, který obsahuje sadu tříd, který umožňuje načtení schématu jazyk (XSD) schématu definice, ze souboru nebo prostřednictvím kódu programu vytvořit schéma v paměti.</span><span class="sxs-lookup"><span data-stu-id="8840d-110">Discusses the Schema Object Model (SOM) in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that provides a set of classes that allows you to read a Schema definition language (XSD) schema from a file or programmatically create a schema in-memory.</span></span>  
  
 [<span data-ttu-id="8840d-111">XmlSchemaSet pro kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="8840d-111">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 <span data-ttu-id="8840d-112">Tento článek popisuje <xref:System.Xml.Schema.XmlSchemaSet> třídy, který je v mezipaměti, kde můžete ukládat a ověřit schémata XSD.</span><span class="sxs-lookup"><span data-stu-id="8840d-112">Discusses the <xref:System.Xml.Schema.XmlSchemaSet> class that is a cache where XSD schemas can be stored and validated.</span></span>  
  
 [<span data-ttu-id="8840d-113">Přímé ověření XmlSchemaValidator</span><span class="sxs-lookup"><span data-stu-id="8840d-113">XmlSchemaValidator Push-Based Validation</span></span>](../../../../docs/standard/data/xml/xmlschemavalidator-push-based-validation.md)  
 <span data-ttu-id="8840d-114">Tento článek popisuje <xref:System.Xml.Schema.XmlSchemaValidator> třídu, která poskytuje mechanismus efektivního, vysoce výkonné ověřit data XML oproti schémata XSD nabízené způsobem.</span><span class="sxs-lookup"><span data-stu-id="8840d-114">Discusses the <xref:System.Xml.Schema.XmlSchemaValidator> class that provides an efficient, high-performance mechanism to validate XML data against XSD schemas in a push-based manner.</span></span>  
  
 [<span data-ttu-id="8840d-115">Odvození schématu XML</span><span class="sxs-lookup"><span data-stu-id="8840d-115">Inferring an XML Schema</span></span>](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)  
 <span data-ttu-id="8840d-116">Tento článek popisuje způsob použití <xref:System.Xml.Schema.XmlSchemaInference> třídy odvodit schéma XSD ze struktury dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="8840d-116">Discusses how to use the <xref:System.Xml.Schema.XmlSchemaInference> class to infer an XSD schema from the structure of an XML document.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8840d-117">Odkaz</span><span class="sxs-lookup"><span data-stu-id="8840d-117">Reference</span></span>  
 <span data-ttu-id="8840d-118"><xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="8840d-118"><xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader></span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8840d-119">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="8840d-119">Related Sections</span></span>  
 [<span data-ttu-id="8840d-120">Ověřování dokumentu XML v modelu DOM</span><span class="sxs-lookup"><span data-stu-id="8840d-120">Validating an XML Document in the DOM</span></span>](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)  
 <span data-ttu-id="8840d-121">Popisuje, jak ověřit kód XML v modelu Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="8840d-121">Discusses how to validate the XML in the Document Object Model (DOM).</span></span> <span data-ttu-id="8840d-122">Ověřit kód XML, jako je načten do modelu DOM nebo ověřit dřív neověřených dokument XML v modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="8840d-122">You can validate the XML as it is loaded into the DOM, or validate a previously unvalidated XML document in the DOM.</span></span>  
  
 [<span data-ttu-id="8840d-123">Ověření schématu pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="8840d-123">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 <span data-ttu-id="8840d-124">Popisuje, jak ověřit XML se přejde poté a upravit pomocí <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="8840d-124">Discusses how to validate XML being navigated and edited using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>
