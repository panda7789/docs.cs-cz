---
title: Dokumenty a data XML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e695047f-3c0f-4045-8708-5baea91cc380
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 22a2eb72dc06a644171c143a61698e661d2c66c6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="xml-documents-and-data"></a><span data-ttu-id="5ec42-102">Dokumenty a data XML</span><span class="sxs-lookup"><span data-stu-id="5ec42-102">XML Documents and Data</span></span>
<span data-ttu-id="5ec42-103">Rozhraní .NET Framework poskytuje komplexní a integrované sadu tříd, které vám umožní snadno vytvářet aplikace podporující rozhraní XML.</span><span class="sxs-lookup"><span data-stu-id="5ec42-103">The .NET Framework provides a comprehensive and integrated set of classes that enable you to build XML-aware apps easily.</span></span> <span data-ttu-id="5ec42-104">Třídy v následujících oborů názvů podporují analýzy a zápis dat XML v paměti, ověřování dat a transformace XSLT pro úpravy XML.</span><span class="sxs-lookup"><span data-stu-id="5ec42-104">The classes in the following namespaces support parsing and writing XML, editing XML data in memory, data validation, and XSLT transformation.</span></span>  
  
-   <xref:System.Xml>  
  
-   <xref:System.Xml.XPath>  
  
-   <xref:System.Xml.Xsl>  
  
-   <xref:System.Xml.Schema>  
  
-   <xref:System.Xml.Linq>  
  
 <span data-ttu-id="5ec42-105">Úplný seznam najdete v tématu [obory názvů System.Xml](http://msdn.microsoft.com/library/gg145036.aspx) webovou stránku.</span><span class="sxs-lookup"><span data-stu-id="5ec42-105">For a full list, see the [System.Xml Namespaces](http://msdn.microsoft.com/library/gg145036.aspx) webpage.</span></span>  
  
 <span data-ttu-id="5ec42-106">Třídy v tyto obory názvů podporují doporučení World Wide Web Consortium (W3C).</span><span class="sxs-lookup"><span data-stu-id="5ec42-106">The classes in these namespaces support World Wide Web Consortium (W3C) recommendations.</span></span> <span data-ttu-id="5ec42-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5ec42-107">For example:</span></span>  
  
-   <span data-ttu-id="5ec42-108"><xref:System.Xml.XmlDocument?displayProperty=nameWithType> Třída implementuje [základní úroveň 1 W3C Model Document Object (DOM)](http://www.w3.org/TR/REC-DOM-Level-1/) a [DOM úroveň 2 jádra](http://www.w3.org/TR/DOM-Level-2-Core/) doporučení.</span><span class="sxs-lookup"><span data-stu-id="5ec42-108">The <xref:System.Xml.XmlDocument?displayProperty=nameWithType> class implements the [W3C Document Object Model (DOM) Level 1 Core](http://www.w3.org/TR/REC-DOM-Level-1/) and [DOM Level 2 Core](http://www.w3.org/TR/DOM-Level-2-Core/) recommendations.</span></span>  
  
-   <span data-ttu-id="5ec42-109"><xref:System.Xml.XmlReader?displayProperty=nameWithType> a <xref:System.Xml.XmlWriter?displayProperty=nameWithType> třídy podpory [W3C XML 1.0](http://www.w3.org/TR/2006/REC-xml-20060816/) a [obory názvů v kódu XML](http://www.w3.org/TR/REC-xml-names/) doporučení.</span><span class="sxs-lookup"><span data-stu-id="5ec42-109">The <xref:System.Xml.XmlReader?displayProperty=nameWithType> and <xref:System.Xml.XmlWriter?displayProperty=nameWithType> classes support the [W3C XML 1.0](http://www.w3.org/TR/2006/REC-xml-20060816/) and the [Namespaces in XML](http://www.w3.org/TR/REC-xml-names/) recommendations.</span></span>  
  
-   <span data-ttu-id="5ec42-110">Schémata v <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> třídy podpory [W3C XML schéma část 1: struktury](http://www.w3.org/TR/xmlschema-1/) a [XML schéma část 2: datové typy](http://www.w3.org/TR/xmlschema-2/) doporučení.</span><span class="sxs-lookup"><span data-stu-id="5ec42-110">Schemas in the <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> class support the [W3C XML Schema Part 1: Structures](http://www.w3.org/TR/xmlschema-1/) and [XML Schema Part 2: Datatypes](http://www.w3.org/TR/xmlschema-2/) recommendations.</span></span>  
  
-   <span data-ttu-id="5ec42-111">Třídy v <xref:System.Xml.Xsl?displayProperty=nameWithType> transformace XSLT podporu obor názvů, které odpovídají [W3C XSLT 1.0](http://www.w3.org/TR/xslt) doporučení.</span><span class="sxs-lookup"><span data-stu-id="5ec42-111">Classes in the <xref:System.Xml.Xsl?displayProperty=nameWithType> namespace support XSLT transformations that conform to the [W3C XSLT 1.0](http://www.w3.org/TR/xslt) recommendation.</span></span>  
  
 <span data-ttu-id="5ec42-112">Třídy XML v rozhraní .NET Framework poskytovat i tyto výhody:</span><span class="sxs-lookup"><span data-stu-id="5ec42-112">The XML classes in the .NET Framework provide these benefits:</span></span>  
  
-   <span data-ttu-id="5ec42-113">**Produktivitu.**</span><span class="sxs-lookup"><span data-stu-id="5ec42-113">**Productivity.**</span></span> <span data-ttu-id="5ec42-114">[Technologie LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) usnadňuje program s XML a poskytuje možnosti dotazu, které je podobná SQL.</span><span class="sxs-lookup"><span data-stu-id="5ec42-114">[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) makes it easier to program with XML and provides a query experience that is similar to SQL.</span></span>  
  
-   <span data-ttu-id="5ec42-115">**Rozšiřitelnost.**</span><span class="sxs-lookup"><span data-stu-id="5ec42-115">**Extensibility.**</span></span> <span data-ttu-id="5ec42-116">Třídy XML v rozhraní .NET Framework jsou extensible prostřednictvím abstraktní základní třídy a virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="5ec42-116">The XML classes in the .NET Framework are extensible through the use of abstract base classes and virtual methods.</span></span> <span data-ttu-id="5ec42-117">Například můžete vytvořit třídu odvozenou z <xref:System.Xml.XmlUrlResolver> třídu, která ukládá stream mezipaměti na místní disk.</span><span class="sxs-lookup"><span data-stu-id="5ec42-117">For example, you can create a derived class of the <xref:System.Xml.XmlUrlResolver> class that stores the cache stream to the local disk.</span></span>  
  
-   <span data-ttu-id="5ec42-118">**Modulární architektura.**</span><span class="sxs-lookup"><span data-stu-id="5ec42-118">**Pluggable architecture.**</span></span> <span data-ttu-id="5ec42-119">Rozhraní .NET Framework poskytuje architekturu, ve kterém součásti můžete využít jednu na druhou a Streamovat data mezi komponentami.</span><span class="sxs-lookup"><span data-stu-id="5ec42-119">The .NET Framework provides an architecture in which components can utilize one another, and data can be streamed between components.</span></span> <span data-ttu-id="5ec42-120">Například úložiště dat, například <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objektu, lze je transformovat s <xref:System.Xml.Xsl.XslCompiledTransform> třídy a výstup pak může být buď do jiného úložiště datového proudu či vrácena jako datový proud z webové služby.</span><span class="sxs-lookup"><span data-stu-id="5ec42-120">For example, a data store, such as an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object, can be transformed with the <xref:System.Xml.Xsl.XslCompiledTransform> class, and the output can then be streamed either into another store or returned as a stream from a web service.</span></span>  
  
-   <span data-ttu-id="5ec42-121">**Výkon.**</span><span class="sxs-lookup"><span data-stu-id="5ec42-121">**Performance.**</span></span> <span data-ttu-id="5ec42-122">Pro lepší výkon aplikace některé třídy XML v rozhraní .NET Framework podporují model na základě streamování s následujícími charakteristikami:</span><span class="sxs-lookup"><span data-stu-id="5ec42-122">For better app performance, some of the XML classes in the .NET Framework support a streaming-based model with the following characteristics:</span></span>  
  
    -   <span data-ttu-id="5ec42-123">Minimální ukládání do mezipaměti pro dopředné, pull model analýzu (<xref:System.Xml.XmlReader>).</span><span class="sxs-lookup"><span data-stu-id="5ec42-123">Minimal caching for forward-only, pull-model parsing (<xref:System.Xml.XmlReader>).</span></span>  
  
    -   <span data-ttu-id="5ec42-124">Dopředné ověření (<xref:System.Xml.XmlReader>).</span><span class="sxs-lookup"><span data-stu-id="5ec42-124">Forward-only validation (<xref:System.Xml.XmlReader>).</span></span>  
  
    -   <span data-ttu-id="5ec42-125">Navigace styl kurzor, který minimalizuje vytvoření uzlu do jednoho virtuálního uzlu při současném poskytování náhodný přístup k dokumentu (<xref:System.Xml.XPath.XPathNavigator>).</span><span class="sxs-lookup"><span data-stu-id="5ec42-125">Cursor style navigation that minimizes node creation to a single virtual node while providing random access to the document (<xref:System.Xml.XPath.XPathNavigator>).</span></span>  
  
     <span data-ttu-id="5ec42-126">Pro lepší výkon při každém zpracování XSLT je požadováno, můžete použít <xref:System.Xml.XPath.XPathDocument> třída, která je úložišti optimalizované, jen pro čtení pro dotazy jazyka XPath navržený tak, aby efektivně pracovat <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="5ec42-126">For better performance whenever XSLT processing is required, you can use the <xref:System.Xml.XPath.XPathDocument> class, which is an optimized, read-only store for XPath queries designed to work efficiently with the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
-   <span data-ttu-id="5ec42-127">**Integrace s ADO.NET.**</span><span class="sxs-lookup"><span data-stu-id="5ec42-127">**Integration with ADO.NET.**</span></span> <span data-ttu-id="5ec42-128">Třídy XML a [ADO.NET](../../../../docs/framework/data/adonet/index.md) jsou pevně integrovány sdružujícího relačních dat a XML.</span><span class="sxs-lookup"><span data-stu-id="5ec42-128">The XML classes and [ADO.NET](../../../../docs/framework/data/adonet/index.md) are tightly integrated to bring together relational data and XML.</span></span> <span data-ttu-id="5ec42-129"><xref:System.Data.DataSet> Třída je mezipaměť v paměti se data načtená z databáze.</span><span class="sxs-lookup"><span data-stu-id="5ec42-129">The <xref:System.Data.DataSet> class is an in-memory cache of data retrieved from a database.</span></span> <span data-ttu-id="5ec42-130"><xref:System.Data.DataSet> Třída má možnost číst a zapisovat XML pomocí <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter> třídy zachována jeho vnitřní relační schéma struktura jako schémat XML (XSD) a odvodit strukturu schématu dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="5ec42-130">The <xref:System.Data.DataSet> class has the ability to read and write XML by using the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> classes, to persist its internal relational schema structure as XML schemas (XSD), and to infer the schema structure of an XML document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5ec42-131">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="5ec42-131">In This Section</span></span>  
 [<span data-ttu-id="5ec42-132">Možnosti zpracování XML</span><span class="sxs-lookup"><span data-stu-id="5ec42-132">XML Processing Options</span></span>](../../../../docs/standard/data/xml/xml-processing-options.md)  
 <span data-ttu-id="5ec42-133">Popisuje možnosti pro zpracování dat XML.</span><span class="sxs-lookup"><span data-stu-id="5ec42-133">Discusses options for processing XML data.</span></span>  
  
 [<span data-ttu-id="5ec42-134">Zpracování dat XML v paměti</span><span class="sxs-lookup"><span data-stu-id="5ec42-134">Processing XML Data In-Memory</span></span>](../../../../docs/standard/data/xml/processing-xml-data-in-memory.md)  
 <span data-ttu-id="5ec42-135">Popisuje tři modely pro zpracování XML data v paměti.</span><span class="sxs-lookup"><span data-stu-id="5ec42-135">Discusses the three models for processing XML data in-memory.</span></span> <span data-ttu-id="5ec42-136">[Technologie LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13), <xref:System.Xml.XmlDocument> – třída (podle W3C Document Object Model) a <xref:System.Xml.XPath.XPathDocument> třídu (založenou na datovém modelu XPath).</span><span class="sxs-lookup"><span data-stu-id="5ec42-136">[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13), the <xref:System.Xml.XmlDocument> class (based on the W3C Document Object Model), and the <xref:System.Xml.XPath.XPathDocument> class (based on the XPath data model).</span></span>  
  
 [<span data-ttu-id="5ec42-137">Transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="5ec42-137">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
 <span data-ttu-id="5ec42-138">Popisuje způsob použití procesoru XSLT.</span><span class="sxs-lookup"><span data-stu-id="5ec42-138">Describes how to use the XSLT processor.</span></span>  
  
 [<span data-ttu-id="5ec42-139">Model objektu schématu (SOM) XML</span><span class="sxs-lookup"><span data-stu-id="5ec42-139">XML Schema Object Model (SOM)</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 <span data-ttu-id="5ec42-140">Popisuje třídy používané pro vytváření a manipulace s schémat XML (XSD) tím, že poskytuje <xref:System.Xml.Schema.XmlSchema> třídy se načíst a upravit schéma.</span><span class="sxs-lookup"><span data-stu-id="5ec42-140">Describes the classes used for building and manipulating XML Schemas (XSD) by providing an <xref:System.Xml.Schema.XmlSchema> class to load and edit a schema.</span></span>  
  
 [<span data-ttu-id="5ec42-141">Integrace XML s relačními daty a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5ec42-141">XML Integration with Relational Data and ADO.NET</span></span>](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md)  
 <span data-ttu-id="5ec42-142">Popisuje, jak rozhraní .NET Framework umožňuje v reálném čase, synchronní přístup k hierarchické a relační reprezentace dat prostřednictvím <xref:System.Data.DataSet> objektu a <xref:System.Xml.XmlDataDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="5ec42-142">Describes how the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the <xref:System.Data.DataSet> object and the <xref:System.Xml.XmlDataDocument> object.</span></span>  
  
 [<span data-ttu-id="5ec42-143">Správa oborů názvů v dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="5ec42-143">Managing Namespaces in an XML Document</span></span>](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)  
 <span data-ttu-id="5ec42-144">Popisuje, jak <xref:System.Xml.XmlNamespaceManager> třída se používá k uložení a správě informace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5ec42-144">Describes how the <xref:System.Xml.XmlNamespaceManager> class is used to store and maintain namespace information.</span></span>  
  
 [<span data-ttu-id="5ec42-145">Podpora typu v třídách System.Xml</span><span class="sxs-lookup"><span data-stu-id="5ec42-145">Type Support in the System.Xml Classes</span></span>](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)  
 <span data-ttu-id="5ec42-146">Popisuje, jak mapování typů dat XML do CLR typy, jak převést datové typy XML a další funkce, typ podpory v <xref:System.Xml> třídy.</span><span class="sxs-lookup"><span data-stu-id="5ec42-146">Describes how XML data types map to CLR types, how to convert XML data types, and other type support features in the <xref:System.Xml> classes.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5ec42-147">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="5ec42-147">Related Sections</span></span>  
 [<span data-ttu-id="5ec42-148">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5ec42-148">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)  
 <span data-ttu-id="5ec42-149">Poskytuje informace o tom, jak získat přístup k datům s použitím technologie ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="5ec42-149">Provides information on how to access data using ADO.NET.</span></span>  
  
 [<span data-ttu-id="5ec42-150">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="5ec42-150">Security</span></span>](../../../../docs/standard/security/index.md)  
 <span data-ttu-id="5ec42-151">Obsahuje přehled systému zabezpečení rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5ec42-151">Provides an overview of the .NET Framework security system.</span></span>  
  
 [<span data-ttu-id="5ec42-152">Středisko pro vývojáře XML</span><span class="sxs-lookup"><span data-stu-id="5ec42-152">XML Developer Center</span></span>](http://go.microsoft.com/fwlink/?linkid=42458)  
 <span data-ttu-id="5ec42-153">Poskytuje další technické informace, soubory ke stažení, diskusní skupiny a další prostředky pro vývojáře XML.</span><span class="sxs-lookup"><span data-stu-id="5ec42-153">Provides additional technical information, downloads, newsgroups, and other resources for XML developers.</span></span>
