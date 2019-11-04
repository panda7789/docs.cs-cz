---
title: Dokumenty a data XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: e695047f-3c0f-4045-8708-5baea91cc380
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 60614a95e4091b4d7bd9ae3a71e2ddeca53e29ba
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424856"
---
# <a name="xml-documents-and-data"></a><span data-ttu-id="a5404-102">Dokumenty a data XML</span><span class="sxs-lookup"><span data-stu-id="a5404-102">XML Documents and Data</span></span>

<span data-ttu-id="a5404-103">.NET Framework poskytuje komplexní a integrovanou sadu tříd, které vám umožní snadno vytvářet aplikace podporující XML.</span><span class="sxs-lookup"><span data-stu-id="a5404-103">The .NET Framework provides a comprehensive and integrated set of classes that enable you to build XML-aware apps easily.</span></span> <span data-ttu-id="a5404-104">Třídy v následujících oborech názvů podporují analýzu a zápis XML, úpravu dat XML v paměti, ověřování dat a transformaci XSLT.</span><span class="sxs-lookup"><span data-stu-id="a5404-104">The classes in the following namespaces support parsing and writing XML, editing XML data in memory, data validation, and XSLT transformation.</span></span>

- <xref:System.Xml>

- <xref:System.Xml.XPath>

- <xref:System.Xml.Xsl>

- <xref:System.Xml.Schema>

- <xref:System.Xml.Linq>

<span data-ttu-id="a5404-105">Úplný seznam najdete v tématu "System. XML" v [prohlížeči rozhraní .NET API](https://docs.microsoft.com/dotnet/api/?term=system.xml).</span><span class="sxs-lookup"><span data-stu-id="a5404-105">For a full list, search for "System.Xml" on the [.NET API browser](https://docs.microsoft.com/dotnet/api/?term=system.xml).</span></span>

<span data-ttu-id="a5404-106">Třídy v těchto oborech názvů podporují doporučení konsorcium World Wide Web (W3C).</span><span class="sxs-lookup"><span data-stu-id="a5404-106">The classes in these namespaces support World Wide Web Consortium (W3C) recommendations.</span></span> <span data-ttu-id="a5404-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a5404-107">For example:</span></span>

- <span data-ttu-id="a5404-108">Třída <xref:System.Xml.XmlDocument?displayProperty=nameWithType> implementuje základní doporučení úrovně 1 základní a [DOM úrovně 2](https://www.w3.org/TR/DOM-Level-2-Core/) pro [W3C model DOM (Document Object Model) (DOM)](https://www.w3.org/TR/REC-DOM-Level-1/) .</span><span class="sxs-lookup"><span data-stu-id="a5404-108">The <xref:System.Xml.XmlDocument?displayProperty=nameWithType> class implements the [W3C Document Object Model (DOM) Level 1 Core](https://www.w3.org/TR/REC-DOM-Level-1/) and [DOM Level 2 Core](https://www.w3.org/TR/DOM-Level-2-Core/) recommendations.</span></span>

- <span data-ttu-id="a5404-109">Třídy <xref:System.Xml.XmlReader?displayProperty=nameWithType> a <xref:System.Xml.XmlWriter?displayProperty=nameWithType> podporují [W3C XML 1,0](https://www.w3.org/TR/2006/REC-xml-20060816/) a [obory názvů v](https://www.w3.org/TR/REC-xml-names/) doporučeních XML.</span><span class="sxs-lookup"><span data-stu-id="a5404-109">The <xref:System.Xml.XmlReader?displayProperty=nameWithType> and <xref:System.Xml.XmlWriter?displayProperty=nameWithType> classes support the [W3C XML 1.0](https://www.w3.org/TR/2006/REC-xml-20060816/) and the [Namespaces in XML](https://www.w3.org/TR/REC-xml-names/) recommendations.</span></span>

- <span data-ttu-id="a5404-110">Schémata ve třídě <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> podporují rozhraní [W3C XML schématu část 1: struktury](https://www.w3.org/TR/xmlschema-1/) a [schéma XML – část 2: doporučení pro DataTypes](https://www.w3.org/TR/xmlschema-2/) .</span><span class="sxs-lookup"><span data-stu-id="a5404-110">Schemas in the <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> class support the [W3C XML Schema Part 1: Structures](https://www.w3.org/TR/xmlschema-1/) and [XML Schema Part 2: Datatypes](https://www.w3.org/TR/xmlschema-2/) recommendations.</span></span>

- <span data-ttu-id="a5404-111">Třídy v oboru názvů <xref:System.Xml.Xsl?displayProperty=nameWithType> podporují transformace XSLT, které odpovídají doporučením [W3C XSLT 1,0](https://www.w3.org/TR/xslt) .</span><span class="sxs-lookup"><span data-stu-id="a5404-111">Classes in the <xref:System.Xml.Xsl?displayProperty=nameWithType> namespace support XSLT transformations that conform to the [W3C XSLT 1.0](https://www.w3.org/TR/xslt) recommendation.</span></span>

<span data-ttu-id="a5404-112">Třídy XML v .NET Framework poskytují tyto výhody:</span><span class="sxs-lookup"><span data-stu-id="a5404-112">The XML classes in the .NET Framework provide these benefits:</span></span>

- <span data-ttu-id="a5404-113">**Produktivitu.**</span><span class="sxs-lookup"><span data-stu-id="a5404-113">**Productivity.**</span></span> <span data-ttu-id="a5404-114">[LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) a [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) usnadňují program s XML a poskytuje dotazové prostředí podobné SQL.</span><span class="sxs-lookup"><span data-stu-id="a5404-114">[LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) makes it easier to program with XML and provides a query experience that is similar to SQL.</span></span>

- <span data-ttu-id="a5404-115">**Možností.**</span><span class="sxs-lookup"><span data-stu-id="a5404-115">**Extensibility.**</span></span> <span data-ttu-id="a5404-116">Třídy XML v .NET Framework jsou rozšiřitelné prostřednictvím použití abstraktních základních tříd a virtuálních metod.</span><span class="sxs-lookup"><span data-stu-id="a5404-116">The XML classes in the .NET Framework are extensible through the use of abstract base classes and virtual methods.</span></span> <span data-ttu-id="a5404-117">Můžete například vytvořit odvozenou třídu třídy <xref:System.Xml.XmlUrlResolver>, která ukládá datový proud mezipaměti na místní disk.</span><span class="sxs-lookup"><span data-stu-id="a5404-117">For example, you can create a derived class of the <xref:System.Xml.XmlUrlResolver> class that stores the cache stream to the local disk.</span></span>

- <span data-ttu-id="a5404-118">**Připojitelné architektury.**</span><span class="sxs-lookup"><span data-stu-id="a5404-118">**Pluggable architecture.**</span></span> <span data-ttu-id="a5404-119">.NET Framework poskytuje architekturu, ve které komponenty mohou být vzájemně využívány, a data lze streamovat mezi komponentami.</span><span class="sxs-lookup"><span data-stu-id="a5404-119">The .NET Framework provides an architecture in which components can utilize one another, and data can be streamed between components.</span></span> <span data-ttu-id="a5404-120">Například úložiště dat, například objekt <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument>, lze transformovat pomocí třídy <xref:System.Xml.Xsl.XslCompiledTransform> a výstup lze následně streamovat buď do jiného úložiště, nebo vráceného jako datový proud z webové služby.</span><span class="sxs-lookup"><span data-stu-id="a5404-120">For example, a data store, such as an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object, can be transformed with the <xref:System.Xml.Xsl.XslCompiledTransform> class, and the output can then be streamed either into another store or returned as a stream from a web service.</span></span>

- <span data-ttu-id="a5404-121">**Předepsané.**</span><span class="sxs-lookup"><span data-stu-id="a5404-121">**Performance.**</span></span> <span data-ttu-id="a5404-122">Pro lepší výkon aplikace některé třídy XML v .NET Framework podporují model založený na streamování s následujícími charakteristikami:</span><span class="sxs-lookup"><span data-stu-id="a5404-122">For better app performance, some of the XML classes in the .NET Framework support a streaming-based model with the following characteristics:</span></span>

  - <span data-ttu-id="a5404-123">Minimální ukládání do mezipaměti pouze pro analýzu modelu vyžádání obsahu (<xref:System.Xml.XmlReader>).</span><span class="sxs-lookup"><span data-stu-id="a5404-123">Minimal caching for forward-only, pull-model parsing (<xref:System.Xml.XmlReader>).</span></span>

  - <span data-ttu-id="a5404-124">Ověřování pouze s dopředné (<xref:System.Xml.XmlReader>).</span><span class="sxs-lookup"><span data-stu-id="a5404-124">Forward-only validation (<xref:System.Xml.XmlReader>).</span></span>

  - <span data-ttu-id="a5404-125">Navigace ve stylu kurzoru, která minimalizuje vytváření uzlů na jeden virtuální uzel při poskytování náhodného přístupu k dokumentu (<xref:System.Xml.XPath.XPathNavigator>).</span><span class="sxs-lookup"><span data-stu-id="a5404-125">Cursor style navigation that minimizes node creation to a single virtual node while providing random access to the document (<xref:System.Xml.XPath.XPathNavigator>).</span></span>

  <span data-ttu-id="a5404-126">Pro lepší výkon vždy, když je vyžadováno zpracování XSLT, můžete použít třídu <xref:System.Xml.XPath.XPathDocument>, což je optimalizované úložiště jen pro čtení pro dotazy XPath navržené pro efektivní práci s třídou <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="a5404-126">For better performance whenever XSLT processing is required, you can use the <xref:System.Xml.XPath.XPathDocument> class, which is an optimized, read-only store for XPath queries designed to work efficiently with the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>

- <span data-ttu-id="a5404-127">**Integrace s ADO.NET.**</span><span class="sxs-lookup"><span data-stu-id="a5404-127">**Integration with ADO.NET.**</span></span> <span data-ttu-id="a5404-128">Třídy XML a [ADO.NET](../../../../docs/framework/data/adonet/index.md) jsou pevně integrované pro spojování relačních dat a XML.</span><span class="sxs-lookup"><span data-stu-id="a5404-128">The XML classes and [ADO.NET](../../../../docs/framework/data/adonet/index.md) are tightly integrated to bring together relational data and XML.</span></span> <span data-ttu-id="a5404-129">Třída <xref:System.Data.DataSet> je mezipaměť dat načtená z databáze z paměti.</span><span class="sxs-lookup"><span data-stu-id="a5404-129">The <xref:System.Data.DataSet> class is an in-memory cache of data retrieved from a database.</span></span> <span data-ttu-id="a5404-130">Třída <xref:System.Data.DataSet> má možnost číst a zapisovat XML pomocí tříd <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter>, aby zachovala svou interní relační strukturu schématu jako schémata XML (XSD), a k odvození struktury schématu dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="a5404-130">The <xref:System.Data.DataSet> class has the ability to read and write XML by using the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> classes, to persist its internal relational schema structure as XML schemas (XSD), and to infer the schema structure of an XML document.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a5404-131">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a5404-131">In This Section</span></span>

<span data-ttu-id="a5404-132">[Možnosti zpracování XML](../../../../docs/standard/data/xml/xml-processing-options.md) Popisuje možnosti zpracování dat XML.</span><span class="sxs-lookup"><span data-stu-id="a5404-132">[XML Processing Options](../../../../docs/standard/data/xml/xml-processing-options.md) Discusses options for processing XML data.</span></span>

<span data-ttu-id="a5404-133">[Zpracování dat XML v paměti](../../../../docs/standard/data/xml/processing-xml-data-in-memory.md) Popisuje tři modely pro zpracování dat XML v paměti: [LINQ to XMLC#()](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) a [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md), třídu <xref:System.Xml.XmlDocument> (na základě model DOM (Document Object Model) W3C) a třídu <xref:System.Xml.XPath.XPathDocument> (na základě datového modelu XPath).</span><span class="sxs-lookup"><span data-stu-id="a5404-133">[Processing XML Data In-Memory](../../../../docs/standard/data/xml/processing-xml-data-in-memory.md) Discusses the three models for processing XML data in-memory: [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md), the <xref:System.Xml.XmlDocument> class (based on the W3C Document Object Model), and the <xref:System.Xml.XPath.XPathDocument> class (based on the XPath data model).</span></span>

<span data-ttu-id="a5404-134">[Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)</span><span class="sxs-lookup"><span data-stu-id="a5404-134">[XSLT Transformations](../../../../docs/standard/data/xml/xslt-transformations.md)</span></span>\
<span data-ttu-id="a5404-135">Popisuje, jak používat procesor XSLT.</span><span class="sxs-lookup"><span data-stu-id="a5404-135">Describes how to use the XSLT processor.</span></span>

<span data-ttu-id="a5404-136">[Model objektu XML schématu (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)</span><span class="sxs-lookup"><span data-stu-id="a5404-136">[XML Schema Object Model (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)</span></span>\
<span data-ttu-id="a5404-137">Popisuje třídy používané pro sestavování a manipulaci se schématy XML (XSD) poskytnutím <xref:System.Xml.Schema.XmlSchema> třídy pro načtení a úpravu schématu.</span><span class="sxs-lookup"><span data-stu-id="a5404-137">Describes the classes used for building and manipulating XML Schemas (XSD) by providing an <xref:System.Xml.Schema.XmlSchema> class to load and edit a schema.</span></span>

<span data-ttu-id="a5404-138">[Integrace XML s relačními daty a ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md)</span><span class="sxs-lookup"><span data-stu-id="a5404-138">[XML Integration with Relational Data and ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md)</span></span>\
<span data-ttu-id="a5404-139">Popisuje, jak .NET Framework umožňuje synchronní přístup v reálném čase do relačních i hierarchických reprezentace dat prostřednictvím objektu <xref:System.Data.DataSet> a objektu <xref:System.Xml.XmlDataDocument>.</span><span class="sxs-lookup"><span data-stu-id="a5404-139">Describes how the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the <xref:System.Data.DataSet> object and the <xref:System.Xml.XmlDataDocument> object.</span></span>

<span data-ttu-id="a5404-140">[Správa oborů názvů v dokumentu XML](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)</span><span class="sxs-lookup"><span data-stu-id="a5404-140">[Managing Namespaces in an XML Document](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)</span></span>\
<span data-ttu-id="a5404-141">Popisuje, jak se třída <xref:System.Xml.XmlNamespaceManager> používá k ukládání a údržbě informací o oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a5404-141">Describes how the <xref:System.Xml.XmlNamespaceManager> class is used to store and maintain namespace information.</span></span>

<span data-ttu-id="a5404-142">[Podpora typů v třídách System. Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)</span><span class="sxs-lookup"><span data-stu-id="a5404-142">[Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)</span></span>\
<span data-ttu-id="a5404-143">Popisuje, jak jsou datové typy XML mapovány na typy CLR, jak převést datové typy XML a jiné funkce podpory typu v <xref:System.Xml> třídy.</span><span class="sxs-lookup"><span data-stu-id="a5404-143">Describes how XML data types map to CLR types, how to convert XML data types, and other type support features in the <xref:System.Xml> classes.</span></span>

## <a name="related-sections"></a><span data-ttu-id="a5404-144">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="a5404-144">Related Sections</span></span>

<span data-ttu-id="a5404-145">[ADO.NET](../../../../docs/framework/data/adonet/index.md)</span><span class="sxs-lookup"><span data-stu-id="a5404-145">[ADO.NET](../../../../docs/framework/data/adonet/index.md)</span></span>\
<span data-ttu-id="a5404-146">Poskytuje informace o tom, jak přistupovat k datům pomocí ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="a5404-146">Provides information on how to access data using ADO.NET.</span></span>

<span data-ttu-id="a5404-147">\ [zabezpečení](../../../../docs/standard/security/index.md)</span><span class="sxs-lookup"><span data-stu-id="a5404-147">[Security](../../../../docs/standard/security/index.md)\</span></span>
<span data-ttu-id="a5404-148">V této části najdete přehled systému .NET Framework Security.</span><span class="sxs-lookup"><span data-stu-id="a5404-148">Provides an overview of the .NET Framework security system.</span></span>
