---
title: "Práce s XML schémata"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbbcc70c-bf9a-4f6a-af72-1bab5384a187
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e21d402dce02ecb332d041f0cda651df911979ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="working-with-xml-schemas"></a><span data-ttu-id="13ca7-102">Práce s XML schémata</span><span class="sxs-lookup"><span data-stu-id="13ca7-102">Working with XML Schemas</span></span>
<span data-ttu-id="13ca7-103">Chcete-li definovat strukturu dokumentu XML, jakož i jeho element relace, datové typy a obsahu omezení, použít definice typu dokumentu (DTD) nebo schématu XML definition language (XSD) schématu.</span><span class="sxs-lookup"><span data-stu-id="13ca7-103">To define the structure of an XML document, as well as its element relationships, data types, and content constraints, you use a document type definition (DTD) or XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="13ca7-104">I když dokumentu XML se považuje za ve správném formátu, pokud splňuje všechny požadavky syntaktické definované doporučení jazyka XML (Extensible Markup) 1.0 World Wide Web Consortium (W3C), není to považováno za platný pokud obě je ve správném formátu a vyhovuje omezení podle DTD nebo schéma.</span><span class="sxs-lookup"><span data-stu-id="13ca7-104">Although an XML document is considered to be well-formed if it meets all the syntactical requirements defined by the World Wide Web Consortium (W3C) Extensible Markup Language (XML) 1.0 Recommendation, it is not considered valid unless it is both well-formed and conforms to the constraints defined by its DTD or schema.</span></span> <span data-ttu-id="13ca7-105">Proto i když jsou všechny platné dokumenty XML ve správném formátu, ne všechny dokumenty ve správném formátu XML nejsou platné.</span><span class="sxs-lookup"><span data-stu-id="13ca7-105">Therefore, although all valid XML documents are well-formed, not all well-formed XML documents are valid.</span></span>  
  
 <span data-ttu-id="13ca7-106">Další informace o XML, najdete v článku [W3C XML 1.0 doporučení](http://go.microsoft.com/fwlink/?linkid=7269).</span><span class="sxs-lookup"><span data-stu-id="13ca7-106">For more information about XML, see the [W3C XML 1.0 Recommendation](http://go.microsoft.com/fwlink/?linkid=7269).</span></span> <span data-ttu-id="13ca7-107">Další informace o schématu XML, najdete v článku [W3C XML schéma část 1: doporučení struktury](http://go.microsoft.com/fwlink/?linkid=48881) a [W3C XML schéma část 2: datové typy doporučení](http://go.microsoft.com/fwlink/?linkid=17392) doporučení.</span><span class="sxs-lookup"><span data-stu-id="13ca7-107">For more information about XML Schema, see the [W3C XML Schema Part 1: Structures Recommendation](http://go.microsoft.com/fwlink/?linkid=48881) and the [W3C XML Schema Part 2: Datatypes Recommendation](http://go.microsoft.com/fwlink/?linkid=17392) recommendations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="13ca7-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="13ca7-108">In This Section</span></span>  
 [<span data-ttu-id="13ca7-109">Objektový Model schématu XML (SOM)</span><span class="sxs-lookup"><span data-stu-id="13ca7-109">XML Schema Object Model (SOM)</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 <span data-ttu-id="13ca7-110">Popisuje Model objektu schématu (SOM) v <xref:System.Xml.Schema?displayProperty=nameWithType> vytvořit obor názvů, který nabízí sadu tříd, které umožňuje číst schéma schématu definice jazyka (XSD) ze souboru nebo prostřednictvím kódu programu schéma v paměti.</span><span class="sxs-lookup"><span data-stu-id="13ca7-110">Discusses the Schema Object Model (SOM) in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that provides a set of classes that allows you to read a Schema definition language (XSD) schema from a file or programmatically create a schema in-memory.</span></span>  
  
 [<span data-ttu-id="13ca7-111">XmlSchemaSet pro kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="13ca7-111">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 <span data-ttu-id="13ca7-112">Popisuje <xref:System.Xml.Schema.XmlSchemaSet> třídy tedy mezipaměti, kde můžete ukládat a ověřit XSD schémata.</span><span class="sxs-lookup"><span data-stu-id="13ca7-112">Discusses the <xref:System.Xml.Schema.XmlSchemaSet> class that is a cache where XSD schemas can be stored and validated.</span></span>  
  
 [<span data-ttu-id="13ca7-113">Ověření nabízené XmlSchemaValidator</span><span class="sxs-lookup"><span data-stu-id="13ca7-113">XmlSchemaValidator Push-Based Validation</span></span>](../../../../docs/standard/data/xml/xmlschemavalidator-push-based-validation.md)  
 <span data-ttu-id="13ca7-114">Popisuje <xref:System.Xml.Schema.XmlSchemaValidator> třídu, která poskytuje mechanismus efektivní, vysoce výkonných ověřit data XML oproti XSD schémata nabízené způsobem.</span><span class="sxs-lookup"><span data-stu-id="13ca7-114">Discusses the <xref:System.Xml.Schema.XmlSchemaValidator> class that provides an efficient, high-performance mechanism to validate XML data against XSD schemas in a push-based manner.</span></span>  
  
 [<span data-ttu-id="13ca7-115">Odvození schématu XML</span><span class="sxs-lookup"><span data-stu-id="13ca7-115">Inferring an XML Schema</span></span>](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)  
 <span data-ttu-id="13ca7-116">Popisuje postup použití <xref:System.Xml.Schema.XmlSchemaInference> třídy odvození schéma XSD ze struktury dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="13ca7-116">Discusses how to use the <xref:System.Xml.Schema.XmlSchemaInference> class to infer an XSD schema from the structure of an XML document.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="13ca7-117">Odkaz</span><span class="sxs-lookup"><span data-stu-id="13ca7-117">Reference</span></span>  
 <span data-ttu-id="13ca7-118"><xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="13ca7-118"><xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader></span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="13ca7-119">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="13ca7-119">Related Sections</span></span>  
 [<span data-ttu-id="13ca7-120">Ověřování dokumentu XML v modelu DOM</span><span class="sxs-lookup"><span data-stu-id="13ca7-120">Validating an XML Document in the DOM</span></span>](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)  
 <span data-ttu-id="13ca7-121">Popisuje, jak ověřit XML v objektu modelu dokumentu (DOM).</span><span class="sxs-lookup"><span data-stu-id="13ca7-121">Discusses how to validate the XML in the Document Object Model (DOM).</span></span> <span data-ttu-id="13ca7-122">Můžete ověřit XML, jako je načten do modelu DOM nebo ověřit dříve neověřený dokumentu XML v modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="13ca7-122">You can validate the XML as it is loaded into the DOM, or validate a previously unvalidated XML document in the DOM.</span></span>  
  
 [<span data-ttu-id="13ca7-123">Ověření schématu pomocí objektem XPathNavigator nastaveným na</span><span class="sxs-lookup"><span data-stu-id="13ca7-123">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 <span data-ttu-id="13ca7-124">Popisuje, jak ověřit XML se navigaci a upravit pomocí <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="13ca7-124">Discusses how to validate XML being navigated and edited using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>
