---
title: Transformace XSLT s třídou XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 500335af-f9b5-413b-968a-e6d9a824478c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d534553fcc6ee63d560e731a535d44c3acd1a214
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347900"
---
# <a name="xslt-transformations-with-the-xsltransform-class"></a><span data-ttu-id="a0696-102">Transformace XSLT s třídou XslTransform</span><span class="sxs-lookup"><span data-stu-id="a0696-102">XSLT Transformations with the XslTransform Class</span></span>

> [!NOTE]
> <span data-ttu-id="a0696-103">Třída <xref:System.Xml.Xsl.XslTransform> je v .NET Framework 2,0 zastaralá.</span><span class="sxs-lookup"><span data-stu-id="a0696-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="a0696-104">Pomocí třídy <xref:System.Xml.Xsl.XslCompiledTransform> můžete provádět transformace XSLT (Extensible Stylesheet Language).</span><span class="sxs-lookup"><span data-stu-id="a0696-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="a0696-105">Další informace najdete v tématu [použití třídy XslCompiledTransform](using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="a0696-105">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>

<span data-ttu-id="a0696-106">Cílem XSLT je převést obsah zdrojového dokumentu XML do jiného dokumentu, který je odlišný ve formátu nebo struktuře (například pro transformaci XML na HTML pro použití na webu nebo k jeho transformaci na dokument obsahující pouze požadovaná pole b). y aplikace).</span><span class="sxs-lookup"><span data-stu-id="a0696-106">The goal of the XSLT is to transform the content of a source XML document into another document that is different in format or structure (for example, to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application).</span></span> <span data-ttu-id="a0696-107">Tento proces transformace je určen[doporučením XSLT verze 1,0](https://www.w3.org/TR/1999/REC-xslt-19991116)pro konsorcium World Wide Web (W3C).</span><span class="sxs-lookup"><span data-stu-id="a0696-107">This transformation process is specified by the World Wide Web Consortium (W3C)[XSLT version 1.0 recommendation](https://www.w3.org/TR/1999/REC-xslt-19991116).</span></span> <span data-ttu-id="a0696-108">V .NET Framework Třída <xref:System.Xml.Xsl.XslTransform>, která se nachází v oboru názvů <xref:System.Xml.Xsl>, je procesor XSLT, který implementuje funkce této specifikace.</span><span class="sxs-lookup"><span data-stu-id="a0696-108">In the .NET Framework, the <xref:System.Xml.Xsl.XslTransform> class, found in the <xref:System.Xml.Xsl> namespace, is the XSLT processor that implements the functionality of this specification.</span></span> <span data-ttu-id="a0696-109">Existuje malý počet funkcí, které nebyly implementovány z doporučení W3C XSLT 1,0 uvedených v části [výstupy z XslTransform](outputs-from-an-xsltransform.md).</span><span class="sxs-lookup"><span data-stu-id="a0696-109">There are a small number of features that have not been implemented from the W3C XSLT 1.0 recommendation, listed in [Outputs from an XslTransform](outputs-from-an-xsltransform.md).</span></span> <span data-ttu-id="a0696-110">Následující obrázek ukazuje architekturu transformace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a0696-110">The following figure shows the transformation architecture of the .NET Framework.</span></span>

## <a name="overview"></a><span data-ttu-id="a0696-111">Přehled</span><span class="sxs-lookup"><span data-stu-id="a0696-111">Overview</span></span>

![Diagram znázorňující architekturu transformace XSLT.](./media/xslt-transformations-with-the-xsltransform-class/xslt-transformation-architecture.gif) 

<span data-ttu-id="a0696-113">Doporučení XSLT používá jazyk XML Path (XPath) pro výběr částí dokumentu XML, kde XPath je dotazovací jazyk, který slouží k navigaci uzlů stromu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a0696-113">The XSLT recommendation uses XML Path Language (XPath) to select parts of an XML document, where XPath is a query language used to navigate nodes of a document tree.</span></span> <span data-ttu-id="a0696-114">Jak je znázorněno v diagramu, .NET Framework implementace XPath slouží k výběru částí jazyka XML uložených v několika třídách, například <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument>a <xref:System.Xml.XPath.XPathDocument>.</span><span class="sxs-lookup"><span data-stu-id="a0696-114">As shown in the diagram, the .NET Framework implementation of XPath is used to select parts of XML stored in several classes, such as an <xref:System.Xml.XmlDocument>, an <xref:System.Xml.XmlDataDocument>, and an <xref:System.Xml.XPath.XPathDocument>.</span></span> <span data-ttu-id="a0696-115"><xref:System.Xml.XPath.XPathDocument> je optimalizované úložiště dat XSLT a při použití s <xref:System.Xml.Xsl.XslTransform>poskytuje transformace XSLT s dobrým výkonem.</span><span class="sxs-lookup"><span data-stu-id="a0696-115">An <xref:System.Xml.XPath.XPathDocument> is an optimized XSLT data store, and when used with <xref:System.Xml.Xsl.XslTransform>, it provides XSLT transformations with good performance.</span></span>

<span data-ttu-id="a0696-116">Následující tabulka často používá třídy při práci s <xref:System.Xml.Xsl.XslTransform> a XPath a jejich funkce.</span><span class="sxs-lookup"><span data-stu-id="a0696-116">The following table list commonly uses classes when working with <xref:System.Xml.Xsl.XslTransform> and XPath and their function.</span></span>

|<span data-ttu-id="a0696-117">Třída nebo rozhraní</span><span class="sxs-lookup"><span data-stu-id="a0696-117">Class or Interface</span></span>|<span data-ttu-id="a0696-118">Funkce</span><span class="sxs-lookup"><span data-stu-id="a0696-118">Function</span></span>|
|------------------------|--------------|
|<xref:System.Xml.XPath.XPathNavigator>|<span data-ttu-id="a0696-119">Je to rozhraní API, které poskytuje model stylu kurzoru pro navigaci přes obchod spolu s podporou dotazů XPath.</span><span class="sxs-lookup"><span data-stu-id="a0696-119">It is an API that provides a cursor style model for navigating over a store, along with XPath query support.</span></span> <span data-ttu-id="a0696-120">Neposkytuje úpravy základního úložiště.</span><span class="sxs-lookup"><span data-stu-id="a0696-120">It does not provide editing of the underlying store.</span></span> <span data-ttu-id="a0696-121">Pro úpravy použijte třídu <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="a0696-121">For editing, use the <xref:System.Xml.XmlDocument> class.</span></span>|
|<xref:System.Xml.XPath.IXPathNavigable>|<span data-ttu-id="a0696-122">Jedná se o rozhraní, které poskytuje `CreateNavigator` metodu pro <xref:System.Xml.XPath.XPathNavigator> úložiště.</span><span class="sxs-lookup"><span data-stu-id="a0696-122">It is an interface that provides a `CreateNavigator` method to an <xref:System.Xml.XPath.XPathNavigator> for the store.</span></span>|
|<xref:System.Xml.XmlDocument>|<span data-ttu-id="a0696-123">Umožňuje úpravy tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a0696-123">It enables editing of this document.</span></span> <span data-ttu-id="a0696-124">Implementuje <xref:System.Xml.XPath.IXPathNavigable>a umožňuje scénáře úprav dokumentů, kde jsou následně požadovány transformace XSLT.</span><span class="sxs-lookup"><span data-stu-id="a0696-124">It implements <xref:System.Xml.XPath.IXPathNavigable>, allowing document-editing scenarios where XSLT transformations are subsequently required.</span></span> <span data-ttu-id="a0696-125">Další informace najdete v tématu [vstupní hodnoty XmlDocument pro XslTransform](xmldocument-input-to-xsltransform.md).</span><span class="sxs-lookup"><span data-stu-id="a0696-125">For more information, see [XmlDocument Input to XslTransform](xmldocument-input-to-xsltransform.md).</span></span>|
|<xref:System.Xml.XmlDataDocument>|<span data-ttu-id="a0696-126">Je odvozen z <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="a0696-126">It is derived from the <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="a0696-127">Mostuje relační a XML světů pomocí <xref:System.Data.DataSet> k optimalizaci úložiště strukturovaných dat v rámci dokumentu XML podle zadaného mapování <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="a0696-127">It bridges the relational and XML worlds by using a <xref:System.Data.DataSet> to optimize storage of structured data within the XML document according to specified mappings on the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="a0696-128">Implementuje <xref:System.Xml.XPath.IXPathNavigable>a umožňuje scénáře, kde lze provádět transformace XSLT prostřednictvím relačních dat načtených z databáze.</span><span class="sxs-lookup"><span data-stu-id="a0696-128">It implements <xref:System.Xml.XPath.IXPathNavigable>, allowing scenarios where XSLT transformations can be performed over relational data retrieved from a database.</span></span> <span data-ttu-id="a0696-129">Další informace najdete v tématu [integrace XML s relačními daty a ADO.NET](xml-integration-with-relational-data-and-adonet.md).</span><span class="sxs-lookup"><span data-stu-id="a0696-129">For more information, see [XML Integration with Relational Data and ADO.NET](xml-integration-with-relational-data-and-adonet.md).</span></span>|
|<xref:System.Xml.XPath.XPathDocument>|<span data-ttu-id="a0696-130">Tato třída je optimalizovaná pro <xref:System.Xml.Xsl.XslTransform> zpracování a dotazy XPath a poskytuje mezipaměť s vysokým výkonem jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="a0696-130">This class is optimized for <xref:System.Xml.Xsl.XslTransform> processing and XPath queries, and it provides a read-only high performance cache.</span></span> <span data-ttu-id="a0696-131">Implementuje <xref:System.Xml.XPath.IXPathNavigable> a je preferovaným úložištěm, které se má použít pro transformace XSLT.</span><span class="sxs-lookup"><span data-stu-id="a0696-131">It implements <xref:System.Xml.XPath.IXPathNavigable> and is the preferred store to use for XSLT transformations.</span></span>|
|<xref:System.Xml.XPath.XPathNodeIterator>|<span data-ttu-id="a0696-132">Poskytuje navigaci nad sadami uzlů XPath.</span><span class="sxs-lookup"><span data-stu-id="a0696-132">It provides navigation over XPath node sets.</span></span> <span data-ttu-id="a0696-133">Všechny metody výběru XPath na <xref:System.Xml.XPath.XPathNavigator> vrátí <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="a0696-133">All XPath selection methods on the <xref:System.Xml.XPath.XPathNavigator> return an <xref:System.Xml.XPath.XPathNodeIterator>.</span></span> <span data-ttu-id="a0696-134">V rámci stejného úložiště lze vytvořit více objektů <xref:System.Xml.XPath.XPathNodeIterator>, z nichž každá představuje vybranou sadu uzlů.</span><span class="sxs-lookup"><span data-stu-id="a0696-134">Multiple <xref:System.Xml.XPath.XPathNodeIterator> objects can be created over the same store, each representing a selected set of nodes.</span></span>|

## <a name="msxml-xslt-extensions"></a><span data-ttu-id="a0696-135">Rozšíření MSXML XSLT</span><span class="sxs-lookup"><span data-stu-id="a0696-135">MSXML XSLT Extensions</span></span>

<span data-ttu-id="a0696-136">Funkce `msxsl:script` a `msxsl:node-set` jsou jediná rozšíření XSLT služby Microsoft XML Core Services (MSXML), která podporuje třída <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="a0696-136">The `msxsl:script` and `msxsl:node-set` functions are the only Microsoft XML Core Services (MSXML) XSLT extensions supported by the <xref:System.Xml.Xsl.XslTransform> class.</span></span>

## <a name="example"></a><span data-ttu-id="a0696-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0696-137">Example</span></span>

<span data-ttu-id="a0696-138">Následující příklad kódu načte šablonu stylů XSLT, přečte soubor s názvem Mojedata. XML do <xref:System.Xml.XPath.XPathDocument>a provede transformaci dat v fiktivním souboru s názvem myStyleSheet. XSL, který odesílá formátovaný výstup do konzoly.</span><span class="sxs-lookup"><span data-stu-id="a0696-138">The following code example loads an XSLT style sheet, reads a file called mydata.xml into an <xref:System.Xml.XPath.XPathDocument>, and performs a transformation on the data on a fictitious file called myStyleSheet.xsl, sending the formatted output to the console.</span></span>

```vb
Imports System.IO
Imports System.Xml
Imports System.Xml.XPath
Imports System.Xml.Xsl

Public Class Sample
    Private filename As [String] = "mydata.xml"
    Private stylesheet As [String] = "myStyleSheet.xsl"

    Public Shared Sub Main()
        Dim xslt As New XslTransform()
        xslt.Load(stylesheet)
        Dim xpathdocument As New XPathDocument(filename)
        Dim writer As New XmlTextWriter(Console.Out)
        writer.Formatting = Formatting.Indented

        xslt.Transform(xpathdocument, Nothing, writer, Nothing)
    End Sub 'Main
End Class 'Sample
```

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.XPath;
using System.Xml.Xsl;

public class Sample 
{
    private const String filename = "mydata.xml";
    private const String stylesheet = "myStyleSheet.xsl";

    public static void Main()
    {
        XslTransform xslt = new XslTransform();
        xslt.Load(stylesheet);
        XPathDocument xpathdocument = new XPathDocument(filename);
        XmlTextWriter writer = new XmlTextWriter(Console.Out);
        writer.Formatting = Formatting.Indented;

        xslt.Transform(xpathdocument, null, writer, null);
    }
}
```

## <a name="see-also"></a><span data-ttu-id="a0696-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0696-139">See also</span></span>

- <xref:System.Xml.Xsl.XslTransform>
- [<span data-ttu-id="a0696-140">Třída XslTransform implementuje procesor XSLT</span><span class="sxs-lookup"><span data-stu-id="a0696-140">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
- [<span data-ttu-id="a0696-141">Implementace volitelného chování ve třídě XslTransform</span><span class="sxs-lookup"><span data-stu-id="a0696-141">Implementation of Discretionary Behaviors in the XslTransform Class</span></span>](implementation-of-discretionary-behaviors-in-the-xsltransform-class.md)
- [<span data-ttu-id="a0696-142">XPathNavigator v transformacích</span><span class="sxs-lookup"><span data-stu-id="a0696-142">XPathNavigator in Transformations</span></span>](xpathnavigator-in-transformations.md)
- [<span data-ttu-id="a0696-143">XPathNodeIterator v transformacích</span><span class="sxs-lookup"><span data-stu-id="a0696-143">XPathNodeIterator in Transformations</span></span>](xpathnodeiterator-in-transformations.md)
- [<span data-ttu-id="a0696-144">Vstup XPathDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="a0696-144">XPathDocument Input to XslTransform</span></span>](xpathdocument-input-to-xsltransform.md)
- [<span data-ttu-id="a0696-145">Vstup XmlDataDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="a0696-145">XmlDataDocument Input to XslTransform</span></span>](xmldatadocument-input-to-xsltransform.md)
- [<span data-ttu-id="a0696-146">Vstup XmlDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="a0696-146">XmlDocument Input to XslTransform</span></span>](xmldocument-input-to-xsltransform.md)
