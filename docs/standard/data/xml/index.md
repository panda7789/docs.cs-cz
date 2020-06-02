---
title: Dokumenty a data XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: e695047f-3c0f-4045-8708-5baea91cc380
ms.openlocfilehash: a752d634141a56df1caa61eb5d375dd2a402832f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287685"
---
# <a name="xml-documents-and-data"></a><span data-ttu-id="5e8d0-102">Dokumenty a data XML</span><span class="sxs-lookup"><span data-stu-id="5e8d0-102">XML Documents and Data</span></span>

<span data-ttu-id="5e8d0-103">.NET Framework poskytuje komplexní a integrovanou sadu tříd, které vám umožní snadno vytvářet aplikace podporující XML.</span><span class="sxs-lookup"><span data-stu-id="5e8d0-103">The .NET Framework provides a comprehensive and integrated set of classes that enable you to build XML-aware apps easily.</span></span> <span data-ttu-id="5e8d0-104">Třídy v následujících oborech názvů podporují analýzu a zápis XML, úpravu dat XML v paměti, ověřování dat a transformaci XSLT.</span><span class="sxs-lookup"><span data-stu-id="5e8d0-104">The classes in the following namespaces support parsing and writing XML, editing XML data in memory, data validation, and XSLT transformation.</span></span>

- <xref:System.Xml>

- <xref:System.Xml.XPath>

- <xref:System.Xml.Xsl>

- <xref:System.Xml.Schema>

- <xref:System.Xml.Linq>

<span data-ttu-id="5e8d0-105">Úplný seznam najdete v tématu "System. XML" v [prohlížeči rozhraní .NET API](https://docs.microsoft.com/dotnet/api/?term=system.xml).</span><span class="sxs-lookup"><span data-stu-id="5e8d0-105">For a full list, search for "System.Xml" on the [.NET API browser](https://docs.microsoft.com/dotnet/api/?term=system.xml).</span></span>

<span data-ttu-id="5e8d0-106">Třídy v těchto oborech názvů podporují doporučení konsorcium World Wide Web (W3C).</span><span class="sxs-lookup"><span data-stu-id="5e8d0-106">The classes in these namespaces support World Wide Web Consortium (W3C) recommendations.</span></span> <span data-ttu-id="5e8d0-107">Například:</span><span class="sxs-lookup"><span data-stu-id="5e8d0-107">For example:</span></span>

- <span data-ttu-id="5e8d0-108"><xref:System.Xml.XmlDocument?displayProperty=nameWithType>Třída implementuje základní doporučení na úrovni [W3C model DOM (Document Object Model) (DOM) 1 Core](https://www.w3.org/TR/REC-DOM-Level-1/) a [DOM úrovně 2](https://www.w3.org/TR/DOM-Level-2-Core/) .</span><span class="sxs-lookup"><span data-stu-id="5e8d0-108">The <xref:System.Xml.XmlDocument?displayProperty=nameWithType> class implements the [W3C Document Object Model (DOM) Level 1 Core](https://www.w3.org/TR/REC-DOM-Level-1/) and [DOM Level 2 Core](https://www.w3.org/TR/DOM-Level-2-Core/) recommendations.</span></span>

- <span data-ttu-id="5e8d0-109"><xref:System.Xml.XmlReader?displayProperty=nameWithType>Třídy a <xref:System.Xml.XmlWriter?displayProperty=nameWithType> podporují [W3C XML 1,0](https://www.w3.org/TR/2006/REC-xml-20060816/) a [obory názvů v](https://www.w3.org/TR/REC-xml-names/) doporučeních XML.</span><span class="sxs-lookup"><span data-stu-id="5e8d0-109">The <xref:System.Xml.XmlReader?displayProperty=nameWithType> and <xref:System.Xml.XmlWriter?displayProperty=nameWithType> classes support the [W3C XML 1.0](https://www.w3.org/TR/2006/REC-xml-20060816/) and the [Namespaces in XML](https://www.w3.org/TR/REC-xml-names/) recommendations.</span></span>

- <span data-ttu-id="5e8d0-110">Schémata ve <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> třídě podporují [součást 1 W3C XML schématu: struktury](https://www.w3.org/TR/xmlschema-1/) a [schéma XML – část 2: doporučení k datatypeům](https://www.w3.org/TR/xmlschema-2/) .</span><span class="sxs-lookup"><span data-stu-id="5e8d0-110">Schemas in the <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> class support the [W3C XML Schema Part 1: Structures](https://www.w3.org/TR/xmlschema-1/) and [XML Schema Part 2: Datatypes](https://www.w3.org/TR/xmlschema-2/) recommendations.</span></span>

- <span data-ttu-id="5e8d0-111">Třídy v <xref:System.Xml.Xsl?displayProperty=nameWithType> oboru názvů podporují transformace XSLT, které odpovídají doporučením [W3C XSLT 1,0](https://www.w3.org/TR/xslt) .</span><span class="sxs-lookup"><span data-stu-id="5e8d0-111">Classes in the <xref:System.Xml.Xsl?displayProperty=nameWithType> namespace support XSLT transformations that conform to the [W3C XSLT 1.0](https://www.w3.org/TR/xslt) recommendation.</span></span>

<span data-ttu-id="5e8d0-112">Třídy XML v .NET Framework poskytují tyto výhody:</span><span class="sxs-lookup"><span data-stu-id="5e8d0-112">The XML classes in the .NET Framework provide these benefits:</span></span>

- <span data-ttu-id="5e8d0-113">**Produktivitu.**</span><span class="sxs-lookup"><span data-stu-id="5e8d0-113">**Productivity.**</span></span> <span data-ttu-id="5e8d0-114">[LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) a [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) usnadňují program s XML a poskytuje podobné prostředí jako SQL.</span><span class="sxs-lookup"><span data-stu-id="5e8d0-114">[LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) makes it easier to program with XML and provides a query experience that is similar to SQL.</span></span>

- <span data-ttu-id="5e8d0-115">**Možností.**</span><span class="sxs-lookup"><span data-stu-id="5e8d0-115">**Extensibility.**</span></span> <span data-ttu-id="5e8d0-116">Třídy XML v .NET Framework jsou rozšiřitelné prostřednictvím použití abstraktních základních tříd a virtuálních metod.</span><span class="sxs-lookup"><span data-stu-id="5e8d0-116">The XML classes in the .NET Framework are extensible through the use of abstract base classes and virtual methods.</span></span> <span data-ttu-id="5e8d0-117">Můžete například vytvořit odvozenou třídu <xref:System.Xml.XmlUrlResolver> třídy, která ukládá datový proud mezipaměti na místní disk.</span><span class="sxs-lookup"><span data-stu-id="5e8d0-117">For example, you can create a derived class of the <xref:System.Xml.XmlUrlResolver> class that stores the cache stream to the local disk.</span></span>

- <span data-ttu-id="5e8d0-118">**Připojitelné architektury.**</span><span class="sxs-lookup"><span data-stu-id="5e8d0-118">**Pluggable architecture.**</span></span> <span data-ttu-id="5e8d0-119">.NET Framework poskytuje architekturu, ve které komponenty mohou být vzájemně využívány, a data lze streamovat mezi komponentami.</span><span class="sxs-lookup"><span data-stu-id="5e8d0-119">The .NET Framework provides an architecture in which components can utilize one another, and data can be streamed between components.</span></span> <span data-ttu-id="5e8d0-120">Například úložiště dat, jako je <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> objekt nebo, lze transformovat s <xref:System.Xml.Xsl.XslCompiledTransform> třídou a výstup může být následně streamování do jiného úložiště nebo vráceno jako datový proud z webové služby.</span><span class="sxs-lookup"><span data-stu-id="5e8d0-120">For example, a data store, such as an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object, can be transformed with the <xref:System.Xml.Xsl.XslCompiledTransform> class, and the output can then be streamed either into another store or returned as a stream from a web service.</span></span>

- <span data-ttu-id="5e8d0-121">**Předepsané.**</span><span class="sxs-lookup"><span data-stu-id="5e8d0-121">**Performance.**</span></span> <span data-ttu-id="5e8d0-122">Pro lepší výkon aplikace některé třídy XML v .NET Framework podporují model založený na streamování s následujícími charakteristikami:</span><span class="sxs-lookup"><span data-stu-id="5e8d0-122">For better app performance, some of the XML classes in the .NET Framework support a streaming-based model with the following characteristics:</span></span>

  - <span data-ttu-id="5e8d0-123">Minimální ukládání do mezipaměti pro analýzu, která je jen pro čtení ( <xref:System.Xml.XmlReader> ).</span><span class="sxs-lookup"><span data-stu-id="5e8d0-123">Minimal caching for forward-only, pull-model parsing (<xref:System.Xml.XmlReader>).</span></span>

  - <span data-ttu-id="5e8d0-124">Ověřování jen pro čtení ( <xref:System.Xml.XmlReader> ).</span><span class="sxs-lookup"><span data-stu-id="5e8d0-124">Forward-only validation (<xref:System.Xml.XmlReader>).</span></span>

  - <span data-ttu-id="5e8d0-125">Navigace ve stylu kurzoru, která minimalizuje vytváření uzlů na jeden virtuální uzel při poskytování náhodného přístupu k dokumentu ( <xref:System.Xml.XPath.XPathNavigator> ).</span><span class="sxs-lookup"><span data-stu-id="5e8d0-125">Cursor style navigation that minimizes node creation to a single virtual node while providing random access to the document (<xref:System.Xml.XPath.XPathNavigator>).</span></span>

  <span data-ttu-id="5e8d0-126">Pro lepší výkon vždy, když je vyžadováno zpracování XSLT, můžete použít <xref:System.Xml.XPath.XPathDocument> třídu, což je optimalizované úložiště jen pro čtení pro dotazy XPath navržené pro efektivní práci s <xref:System.Xml.Xsl.XslCompiledTransform> třídou.</span><span class="sxs-lookup"><span data-stu-id="5e8d0-126">For better performance whenever XSLT processing is required, you can use the <xref:System.Xml.XPath.XPathDocument> class, which is an optimized, read-only store for XPath queries designed to work efficiently with the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>

- <span data-ttu-id="5e8d0-127">**Integrace s ADO.NET.**</span><span class="sxs-lookup"><span data-stu-id="5e8d0-127">**Integration with ADO.NET.**</span></span> <span data-ttu-id="5e8d0-128">Třídy XML a [ADO.NET](../../../framework/data/adonet/index.md) jsou pevně integrované pro spojování relačních dat a XML.</span><span class="sxs-lookup"><span data-stu-id="5e8d0-128">The XML classes and [ADO.NET](../../../framework/data/adonet/index.md) are tightly integrated to bring together relational data and XML.</span></span> <span data-ttu-id="5e8d0-129"><xref:System.Data.DataSet>Třída je mezipaměť dat načtená z databáze z paměti.</span><span class="sxs-lookup"><span data-stu-id="5e8d0-129">The <xref:System.Data.DataSet> class is an in-memory cache of data retrieved from a database.</span></span> <span data-ttu-id="5e8d0-130"><xref:System.Data.DataSet>Třída má možnost číst a zapisovat XML pomocí <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> tříd a, aby bylo možné zachovat vnitřní relační strukturu schématu jako schéma XML (XSD) a jak odvodit strukturu schématu dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="5e8d0-130">The <xref:System.Data.DataSet> class has the ability to read and write XML by using the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> classes, to persist its internal relational schema structure as XML schemas (XSD), and to infer the schema structure of an XML document.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="5e8d0-131">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="5e8d0-131">In This Section</span></span>

<span data-ttu-id="5e8d0-132">[Možnosti zpracování XML](xml-processing-options.md) Popisuje možnosti zpracování dat XML.</span><span class="sxs-lookup"><span data-stu-id="5e8d0-132">[XML Processing Options](xml-processing-options.md) Discusses options for processing XML data.</span></span>

<span data-ttu-id="5e8d0-133">[Zpracování dat XML v paměti](processing-xml-data-in-memory.md) Popisuje tři modely pro zpracování dat XML v paměti: [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) a [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md), <xref:System.Xml.XmlDocument> třídy (založené na model DOM (Document Object Model) konsorcia W3C) a <xref:System.Xml.XPath.XPathDocument> třídě (na základě datového modelu XPath).</span><span class="sxs-lookup"><span data-stu-id="5e8d0-133">[Processing XML Data In-Memory](processing-xml-data-in-memory.md) Discusses the three models for processing XML data in-memory: [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md), the <xref:System.Xml.XmlDocument> class (based on the W3C Document Object Model), and the <xref:System.Xml.XPath.XPathDocument> class (based on the XPath data model).</span></span>

<span data-ttu-id="5e8d0-134">[Transformace XSLT](xslt-transformations.md)</span><span class="sxs-lookup"><span data-stu-id="5e8d0-134">[XSLT Transformations](xslt-transformations.md)</span></span>\
<span data-ttu-id="5e8d0-135">Popisuje, jak používat procesor XSLT.</span><span class="sxs-lookup"><span data-stu-id="5e8d0-135">Describes how to use the XSLT processor.</span></span>

<span data-ttu-id="5e8d0-136">[Model objektu XML schématu (SOM)](xml-schema-object-model-som.md)</span><span class="sxs-lookup"><span data-stu-id="5e8d0-136">[XML Schema Object Model (SOM)](xml-schema-object-model-som.md)</span></span>\
<span data-ttu-id="5e8d0-137">Popisuje třídy používané pro sestavování a manipulaci se schématy XML (XSD) poskytnutím <xref:System.Xml.Schema.XmlSchema> třídy pro načtení a úpravu schématu.</span><span class="sxs-lookup"><span data-stu-id="5e8d0-137">Describes the classes used for building and manipulating XML Schemas (XSD) by providing an <xref:System.Xml.Schema.XmlSchema> class to load and edit a schema.</span></span>

<span data-ttu-id="5e8d0-138">[Integrace XML s relačními daty a ADO.NET](xml-integration-with-relational-data-and-adonet.md)</span><span class="sxs-lookup"><span data-stu-id="5e8d0-138">[XML Integration with Relational Data and ADO.NET](xml-integration-with-relational-data-and-adonet.md)</span></span>\
<span data-ttu-id="5e8d0-139">Popisuje, jak .NET Framework umožňuje synchronní přístup v reálném čase do relačních i hierarchických reprezentace dat prostřednictvím <xref:System.Data.DataSet> objektu a <xref:System.Xml.XmlDataDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="5e8d0-139">Describes how the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the <xref:System.Data.DataSet> object and the <xref:System.Xml.XmlDataDocument> object.</span></span>

<span data-ttu-id="5e8d0-140">[Správa oborů názvů v dokumentu XML](managing-namespaces-in-an-xml-document.md)</span><span class="sxs-lookup"><span data-stu-id="5e8d0-140">[Managing Namespaces in an XML Document](managing-namespaces-in-an-xml-document.md)</span></span>\
<span data-ttu-id="5e8d0-141">Popisuje, jak <xref:System.Xml.XmlNamespaceManager> se třída používá k ukládání a údržbě informací o oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5e8d0-141">Describes how the <xref:System.Xml.XmlNamespaceManager> class is used to store and maintain namespace information.</span></span>

<span data-ttu-id="5e8d0-142">[Podpora typů v třídách System. XML](type-support-in-the-system-xml-classes.md)</span><span class="sxs-lookup"><span data-stu-id="5e8d0-142">[Type Support in the System.Xml Classes](type-support-in-the-system-xml-classes.md)</span></span>\
<span data-ttu-id="5e8d0-143">Popisuje, jak jsou datové typy XML mapovány na typy CLR, jak převést datové typy XML a další funkce podpory typu ve <xref:System.Xml> třídách.</span><span class="sxs-lookup"><span data-stu-id="5e8d0-143">Describes how XML data types map to CLR types, how to convert XML data types, and other type support features in the <xref:System.Xml> classes.</span></span>

## <a name="related-sections"></a><span data-ttu-id="5e8d0-144">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="5e8d0-144">Related Sections</span></span>

<span data-ttu-id="5e8d0-145">[ADO.NET](../../../framework/data/adonet/index.md)</span><span class="sxs-lookup"><span data-stu-id="5e8d0-145">[ADO.NET](../../../framework/data/adonet/index.md)</span></span>\
<span data-ttu-id="5e8d0-146">Poskytuje informace o tom, jak přistupovat k datům pomocí ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="5e8d0-146">Provides information on how to access data using ADO.NET.</span></span>

<span data-ttu-id="5e8d0-147">[Bezpečnost](../../security/index.md)</span><span class="sxs-lookup"><span data-stu-id="5e8d0-147">[Security](../../security/index.md)</span></span>\
<span data-ttu-id="5e8d0-148">V této části najdete přehled systému .NET Framework Security.</span><span class="sxs-lookup"><span data-stu-id="5e8d0-148">Provides an overview of the .NET Framework security system.</span></span>
