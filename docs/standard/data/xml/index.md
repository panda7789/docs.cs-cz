---
title: Dokumenty a data XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: e695047f-3c0f-4045-8708-5baea91cc380
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d9cc44b8a5d43a3fe0414ddeeb51f37e239480b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647902"
---
# <a name="xml-documents-and-data"></a><span data-ttu-id="249db-102">Dokumenty a data XML</span><span class="sxs-lookup"><span data-stu-id="249db-102">XML Documents and Data</span></span>
<span data-ttu-id="249db-103">Rozhraní .NET Framework poskytuje komplexního a integrovaného sadu tříd, které vám umožní snadno vytvářet aplikace pracující s XML.</span><span class="sxs-lookup"><span data-stu-id="249db-103">The .NET Framework provides a comprehensive and integrated set of classes that enable you to build XML-aware apps easily.</span></span> <span data-ttu-id="249db-104">Třídy v následující obory názvů podporují analýzu a zápis dat XML v paměti, ověřování dat a transformace XSLT pro úpravy XML.</span><span class="sxs-lookup"><span data-stu-id="249db-104">The classes in the following namespaces support parsing and writing XML, editing XML data in memory, data validation, and XSLT transformation.</span></span>  
  
- <xref:System.Xml>  
  
- <xref:System.Xml.XPath>  
  
- <xref:System.Xml.Xsl>  
  
- <xref:System.Xml.Schema>  
  
- <xref:System.Xml.Linq>  
  
 <span data-ttu-id="249db-105">Úplný seznam, vyhledejte "System.Xml" na [.NET API browseru](https://docs.microsoft.com/dotnet/api/?term=system.xml).</span><span class="sxs-lookup"><span data-stu-id="249db-105">For a full list, search for "System.Xml" on the [.NET API browser](https://docs.microsoft.com/dotnet/api/?term=system.xml).</span></span>  
  
 <span data-ttu-id="249db-106">Třídy v tyto obory názvů podporují World Wide Web Consortium (W3C) doporučení.</span><span class="sxs-lookup"><span data-stu-id="249db-106">The classes in these namespaces support World Wide Web Consortium (W3C) recommendations.</span></span> <span data-ttu-id="249db-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="249db-107">For example:</span></span>  
  
- <span data-ttu-id="249db-108"><xref:System.Xml.XmlDocument?displayProperty=nameWithType> Implementuje třída [W3C Document Object Model (DOM) úrovně 1 jádro](https://www.w3.org/TR/REC-DOM-Level-1/) a [modelu DOM úroveň 2 jádra](https://www.w3.org/TR/DOM-Level-2-Core/) doporučení.</span><span class="sxs-lookup"><span data-stu-id="249db-108">The <xref:System.Xml.XmlDocument?displayProperty=nameWithType> class implements the [W3C Document Object Model (DOM) Level 1 Core](https://www.w3.org/TR/REC-DOM-Level-1/) and [DOM Level 2 Core](https://www.w3.org/TR/DOM-Level-2-Core/) recommendations.</span></span>  
  
- <span data-ttu-id="249db-109"><xref:System.Xml.XmlReader?displayProperty=nameWithType> a <xref:System.Xml.XmlWriter?displayProperty=nameWithType> třídy podporu [W3C XML 1.0](https://www.w3.org/TR/2006/REC-xml-20060816/) a [obory názvů v XML](https://www.w3.org/TR/REC-xml-names/) doporučení.</span><span class="sxs-lookup"><span data-stu-id="249db-109">The <xref:System.Xml.XmlReader?displayProperty=nameWithType> and <xref:System.Xml.XmlWriter?displayProperty=nameWithType> classes support the [W3C XML 1.0](https://www.w3.org/TR/2006/REC-xml-20060816/) and the [Namespaces in XML](https://www.w3.org/TR/REC-xml-names/) recommendations.</span></span>  
  
- <span data-ttu-id="249db-110">Schémata <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> třídy podporu [části 1 W3C XML schématu: Struktury](https://www.w3.org/TR/xmlschema-1/) a [XML schématu část 2: Datové typy](https://www.w3.org/TR/xmlschema-2/) doporučení.</span><span class="sxs-lookup"><span data-stu-id="249db-110">Schemas in the <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> class support the [W3C XML Schema Part 1: Structures](https://www.w3.org/TR/xmlschema-1/) and [XML Schema Part 2: Datatypes](https://www.w3.org/TR/xmlschema-2/) recommendations.</span></span>  
  
- <span data-ttu-id="249db-111">Třídy v <xref:System.Xml.Xsl?displayProperty=nameWithType> transformace XSLT podpora oboru názvů, které odpovídají [W3C XSLT 1.0](https://www.w3.org/TR/xslt) doporučení.</span><span class="sxs-lookup"><span data-stu-id="249db-111">Classes in the <xref:System.Xml.Xsl?displayProperty=nameWithType> namespace support XSLT transformations that conform to the [W3C XSLT 1.0](https://www.w3.org/TR/xslt) recommendation.</span></span>  
  
 <span data-ttu-id="249db-112">XML tříd v rozhraní .NET Framework poskytuje tyto výhody:</span><span class="sxs-lookup"><span data-stu-id="249db-112">The XML classes in the .NET Framework provide these benefits:</span></span>  
  
- <span data-ttu-id="249db-113">**Zvýšení produktivity.**</span><span class="sxs-lookup"><span data-stu-id="249db-113">**Productivity.**</span></span> <span data-ttu-id="249db-114">[Technologie LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) a [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) usnadňuje programu pomocí XML a poskytuje možnosti dotazu, který je podobný SQL.</span><span class="sxs-lookup"><span data-stu-id="249db-114">[LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) makes it easier to program with XML and provides a query experience that is similar to SQL.</span></span>  
  
- <span data-ttu-id="249db-115">**Rozšiřitelnost.**</span><span class="sxs-lookup"><span data-stu-id="249db-115">**Extensibility.**</span></span> <span data-ttu-id="249db-116">XML tříd v rozhraní .NET Framework je rozšiřitelný prostřednictvím použití základních tříd abstraktu a virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="249db-116">The XML classes in the .NET Framework are extensible through the use of abstract base classes and virtual methods.</span></span> <span data-ttu-id="249db-117">Můžete například vytvořit odvozenou třídu <xref:System.Xml.XmlUrlResolver> třída, která obsahuje datový proud mezipaměti na místní disk.</span><span class="sxs-lookup"><span data-stu-id="249db-117">For example, you can create a derived class of the <xref:System.Xml.XmlUrlResolver> class that stores the cache stream to the local disk.</span></span>  
  
- <span data-ttu-id="249db-118">**Připojitelná architektura.**</span><span class="sxs-lookup"><span data-stu-id="249db-118">**Pluggable architecture.**</span></span> <span data-ttu-id="249db-119">Rozhraní .NET Framework poskytuje architekturu, ve kterém komponenty se mezi sebou můžou využívat a Streamovat data mezi komponentami.</span><span class="sxs-lookup"><span data-stu-id="249db-119">The .NET Framework provides an architecture in which components can utilize one another, and data can be streamed between components.</span></span> <span data-ttu-id="249db-120">Například úložiště dat, například <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objektu, lze je transformovat pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy a výstup je pak možné Streamovat buď do jiného úložiště nebo vrácena jako datový proud z webové služby.</span><span class="sxs-lookup"><span data-stu-id="249db-120">For example, a data store, such as an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object, can be transformed with the <xref:System.Xml.Xsl.XslCompiledTransform> class, and the output can then be streamed either into another store or returned as a stream from a web service.</span></span>  
  
- <span data-ttu-id="249db-121">**Výkon.**</span><span class="sxs-lookup"><span data-stu-id="249db-121">**Performance.**</span></span> <span data-ttu-id="249db-122">Pro lepší výkon aplikace a některé třídy XML v rozhraní .NET Framework podporují jako model založený na datových proudů s následujícími charakteristikami:</span><span class="sxs-lookup"><span data-stu-id="249db-122">For better app performance, some of the XML classes in the .NET Framework support a streaming-based model with the following characteristics:</span></span>  
  
    - <span data-ttu-id="249db-123">Minimální ukládání do mezipaměti pro dopředné, pull model analýzu (<xref:System.Xml.XmlReader>).</span><span class="sxs-lookup"><span data-stu-id="249db-123">Minimal caching for forward-only, pull-model parsing (<xref:System.Xml.XmlReader>).</span></span>  
  
    - <span data-ttu-id="249db-124">Dopředné ověření (<xref:System.Xml.XmlReader>).</span><span class="sxs-lookup"><span data-stu-id="249db-124">Forward-only validation (<xref:System.Xml.XmlReader>).</span></span>  
  
    - <span data-ttu-id="249db-125">Kurzor styl navigace, která minimalizuje vytvoření uzlu na jeden virtuální uzel poskytuje náhodný přístup k tomuto dokumentu (<xref:System.Xml.XPath.XPathNavigator>).</span><span class="sxs-lookup"><span data-stu-id="249db-125">Cursor style navigation that minimizes node creation to a single virtual node while providing random access to the document (<xref:System.Xml.XPath.XPathNavigator>).</span></span>  
  
     <span data-ttu-id="249db-126">Pro zajištění lepšího výkonu při každém zpracování XSLT je nutné použít, můžete použít <xref:System.Xml.XPath.XPathDocument> třídu, která je optimalizovaná, jen pro čtení obchod pro dotazy XPath, které jsou navržené tak, aby efektivně pracovat <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="249db-126">For better performance whenever XSLT processing is required, you can use the <xref:System.Xml.XPath.XPathDocument> class, which is an optimized, read-only store for XPath queries designed to work efficiently with the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
- <span data-ttu-id="249db-127">**Integrace s ADO.NET.**</span><span class="sxs-lookup"><span data-stu-id="249db-127">**Integration with ADO.NET.**</span></span> <span data-ttu-id="249db-128">XML tříd a [ADO.NET](../../../../docs/framework/data/adonet/index.md) jsou pevně integrovány spojit relační data a XML.</span><span class="sxs-lookup"><span data-stu-id="249db-128">The XML classes and [ADO.NET](../../../../docs/framework/data/adonet/index.md) are tightly integrated to bring together relational data and XML.</span></span> <span data-ttu-id="249db-129"><xref:System.Data.DataSet> Třída je mezipaměti z dat načtených z databáze.</span><span class="sxs-lookup"><span data-stu-id="249db-129">The <xref:System.Data.DataSet> class is an in-memory cache of data retrieved from a database.</span></span> <span data-ttu-id="249db-130"><xref:System.Data.DataSet> Má možnost číst a zapisovat XML pomocí třídy <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter> třídy, a zachová své interní schéma relační struktury jako schématu XML (XSD) a k odvození schématu strukturu dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="249db-130">The <xref:System.Data.DataSet> class has the ability to read and write XML by using the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> classes, to persist its internal relational schema structure as XML schemas (XSD), and to infer the schema structure of an XML document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="249db-131">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="249db-131">In This Section</span></span>  
 [<span data-ttu-id="249db-132">Možnosti zpracování XML</span><span class="sxs-lookup"><span data-stu-id="249db-132">XML Processing Options</span></span>](../../../../docs/standard/data/xml/xml-processing-options.md)  
 <span data-ttu-id="249db-133">Tento článek popisuje možnosti pro zpracování dat XML.</span><span class="sxs-lookup"><span data-stu-id="249db-133">Discusses options for processing XML data.</span></span>  
  
 [<span data-ttu-id="249db-134">Zpracování dat XML v paměti</span><span class="sxs-lookup"><span data-stu-id="249db-134">Processing XML Data In-Memory</span></span>](../../../../docs/standard/data/xml/processing-xml-data-in-memory.md)  
 <span data-ttu-id="249db-135">Tento článek popisuje tři modely pro zpracování XML dat v paměti: [Technologie LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) a [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md), <xref:System.Xml.XmlDocument> třídy (založené na modelu objektu dokumentu W3C) a <xref:System.Xml.XPath.XPathDocument> třídy (založené na modelu dat XPath).</span><span class="sxs-lookup"><span data-stu-id="249db-135">Discusses the three models for processing XML data in-memory: [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md), the <xref:System.Xml.XmlDocument> class (based on the W3C Document Object Model), and the <xref:System.Xml.XPath.XPathDocument> class (based on the XPath data model).</span></span>  
  
 [<span data-ttu-id="249db-136">Transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="249db-136">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
 <span data-ttu-id="249db-137">Popisuje způsob použití procesoru XSLT.</span><span class="sxs-lookup"><span data-stu-id="249db-137">Describes how to use the XSLT processor.</span></span>  
  
 [<span data-ttu-id="249db-138">Model objektu schématu (SOM) XML</span><span class="sxs-lookup"><span data-stu-id="249db-138">XML Schema Object Model (SOM)</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 <span data-ttu-id="249db-139">Popisuje třídy používané pro vytváření a manipulaci s schémat XML (XSD) tím, že poskytuje <xref:System.Xml.Schema.XmlSchema> třídy pro načtení a upravit schéma.</span><span class="sxs-lookup"><span data-stu-id="249db-139">Describes the classes used for building and manipulating XML Schemas (XSD) by providing an <xref:System.Xml.Schema.XmlSchema> class to load and edit a schema.</span></span>  
  
 [<span data-ttu-id="249db-140">Integrace XML s relačními daty a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="249db-140">XML Integration with Relational Data and ADO.NET</span></span>](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md)  
 <span data-ttu-id="249db-141">Popisuje, jak rozhraní .NET Framework umožňuje v reálném čase, která je synchronní přístup k relačních a hierarchických reprezentace dat prostřednictvím <xref:System.Data.DataSet> objektu a <xref:System.Xml.XmlDataDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="249db-141">Describes how the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the <xref:System.Data.DataSet> object and the <xref:System.Xml.XmlDataDocument> object.</span></span>  
  
 [<span data-ttu-id="249db-142">Správa oborů názvů v dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="249db-142">Managing Namespaces in an XML Document</span></span>](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)  
 <span data-ttu-id="249db-143">Popisuje, jak <xref:System.Xml.XmlNamespaceManager> třída se používá k ukládání a správě informace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="249db-143">Describes how the <xref:System.Xml.XmlNamespaceManager> class is used to store and maintain namespace information.</span></span>  
  
 [<span data-ttu-id="249db-144">Podpora typu v třídách System.Xml</span><span class="sxs-lookup"><span data-stu-id="249db-144">Type Support in the System.Xml Classes</span></span>](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)  
 <span data-ttu-id="249db-145">Popisuje, jak mapa typy dat XML do CLR typy, jak převést datové typy XML a další funkce podpory typu <xref:System.Xml> třídy.</span><span class="sxs-lookup"><span data-stu-id="249db-145">Describes how XML data types map to CLR types, how to convert XML data types, and other type support features in the <xref:System.Xml> classes.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="249db-146">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="249db-146">Related Sections</span></span>  
 [<span data-ttu-id="249db-147">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="249db-147">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)  
 <span data-ttu-id="249db-148">Poskytuje informace o tom, jak získat přístup k datům pomocí technologie ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="249db-148">Provides information on how to access data using ADO.NET.</span></span>  
  
 [<span data-ttu-id="249db-149">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="249db-149">Security</span></span>](../../../../docs/standard/security/index.md)  
 <span data-ttu-id="249db-150">Poskytuje přehled o systém zabezpečení rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="249db-150">Provides an overview of the .NET Framework security system.</span></span>  
