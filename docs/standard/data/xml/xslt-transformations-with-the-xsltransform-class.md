---
title: Transformace XSLT s třídou XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 500335af-f9b5-413b-968a-e6d9a824478c
ms.openlocfilehash: e03eb08c71ff2d031ac61a702683e3950d94f2be
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160232"
---
# <a name="xslt-transformations-with-the-xsltransform-class"></a><span data-ttu-id="95897-102">Transformace XSLT s třídou XslTransform</span><span class="sxs-lookup"><span data-stu-id="95897-102">XSLT Transformations with the XslTransform Class</span></span>

> [!NOTE]
> <span data-ttu-id="95897-103"><xref:System.Xml.Xsl.XslTransform> Třída je zastaralá v .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="95897-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="95897-104">Transformace XSLT (Extensible Stylesheet Language) můžete použít k <xref:System.Xml.Xsl.XslCompiledTransform> transformaci pomocí třídy.</span><span class="sxs-lookup"><span data-stu-id="95897-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="95897-105">Další informace najdete v tématu [použití třídy XslCompiledTransform](using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="95897-105">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>

<span data-ttu-id="95897-106">Cílem XSLT je převést obsah zdrojového dokumentu XML do jiného dokumentu, který je odlišný ve formátu nebo struktuře (například pro transformaci XML na HTML pro použití na webu nebo k jeho transformaci na dokument, který obsahuje pouze pole požadovaná aplikací).</span><span class="sxs-lookup"><span data-stu-id="95897-106">The goal of the XSLT is to transform the content of a source XML document into another document that is different in format or structure (for example, to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application).</span></span> <span data-ttu-id="95897-107">Tento proces transformace je určen[doporučením XSLT verze 1,0](https://www.w3.org/TR/1999/REC-xslt-19991116)pro konsorcium World Wide Web (W3C).</span><span class="sxs-lookup"><span data-stu-id="95897-107">This transformation process is specified by the World Wide Web Consortium (W3C)[XSLT version 1.0 recommendation](https://www.w3.org/TR/1999/REC-xslt-19991116).</span></span> <span data-ttu-id="95897-108">V .NET Framework <xref:System.Xml.Xsl.XslTransform> třída, která je nalezena v <xref:System.Xml.Xsl> oboru názvů, je procesor XSLT, který implementuje funkce této specifikace.</span><span class="sxs-lookup"><span data-stu-id="95897-108">In the .NET Framework, the <xref:System.Xml.Xsl.XslTransform> class, found in the <xref:System.Xml.Xsl> namespace, is the XSLT processor that implements the functionality of this specification.</span></span> <span data-ttu-id="95897-109">Existuje malý počet funkcí, které nebyly implementovány z doporučení W3C XSLT 1,0 uvedených v části [výstupy z XslTransform](outputs-from-an-xsltransform.md).</span><span class="sxs-lookup"><span data-stu-id="95897-109">There are a small number of features that have not been implemented from the W3C XSLT 1.0 recommendation, listed in [Outputs from an XslTransform](outputs-from-an-xsltransform.md).</span></span> <span data-ttu-id="95897-110">Následující obrázek ukazuje architekturu transformace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="95897-110">The following figure shows the transformation architecture of the .NET Framework.</span></span>

## <a name="overview"></a><span data-ttu-id="95897-111">Přehled</span><span class="sxs-lookup"><span data-stu-id="95897-111">Overview</span></span>

![Diagram znázorňující architekturu transformace XSLT.](./media/xslt-transformations-with-the-xsltransform-class/xslt-transformation-architecture.gif)

<span data-ttu-id="95897-113">Doporučení XSLT používá jazyk XML Path (XPath) pro výběr částí dokumentu XML, kde XPath je dotazovací jazyk, který slouží k navigaci uzlů stromu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="95897-113">The XSLT recommendation uses XML Path Language (XPath) to select parts of an XML document, where XPath is a query language used to navigate nodes of a document tree.</span></span> <span data-ttu-id="95897-114">Jak je znázorněno v diagramu, .NET Framework implementace XPath slouží k výběru částí jazyka XML uložených v několika třídách, například <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument>a. <xref:System.Xml.XPath.XPathDocument></span><span class="sxs-lookup"><span data-stu-id="95897-114">As shown in the diagram, the .NET Framework implementation of XPath is used to select parts of XML stored in several classes, such as an <xref:System.Xml.XmlDocument>, an <xref:System.Xml.XmlDataDocument>, and an <xref:System.Xml.XPath.XPathDocument>.</span></span> <span data-ttu-id="95897-115"><xref:System.Xml.XPath.XPathDocument> Je optimalizované úložiště dat XSLT a při použití s nástrojem <xref:System.Xml.Xsl.XslTransform>poskytuje transformace XSLT s dobrým výkonem.</span><span class="sxs-lookup"><span data-stu-id="95897-115">An <xref:System.Xml.XPath.XPathDocument> is an optimized XSLT data store, and when used with <xref:System.Xml.Xsl.XslTransform>, it provides XSLT transformations with good performance.</span></span>

<span data-ttu-id="95897-116">Následující tabulka často používá třídy při práci s <xref:System.Xml.Xsl.XslTransform> a XPath a jejich funkci.</span><span class="sxs-lookup"><span data-stu-id="95897-116">The following table list commonly uses classes when working with <xref:System.Xml.Xsl.XslTransform> and XPath and their function.</span></span>

|<span data-ttu-id="95897-117">Třída nebo rozhraní</span><span class="sxs-lookup"><span data-stu-id="95897-117">Class or Interface</span></span>|<span data-ttu-id="95897-118">Funkce</span><span class="sxs-lookup"><span data-stu-id="95897-118">Function</span></span>|
|------------------------|--------------|
|<xref:System.Xml.XPath.XPathNavigator>|<span data-ttu-id="95897-119">Je to rozhraní API, které poskytuje model stylu kurzoru pro navigaci přes obchod spolu s podporou dotazů XPath.</span><span class="sxs-lookup"><span data-stu-id="95897-119">It is an API that provides a cursor style model for navigating over a store, along with XPath query support.</span></span> <span data-ttu-id="95897-120">Neposkytuje úpravy základního úložiště.</span><span class="sxs-lookup"><span data-stu-id="95897-120">It does not provide editing of the underlying store.</span></span> <span data-ttu-id="95897-121">Pro úpravy použijte <xref:System.Xml.XmlDocument> třídu.</span><span class="sxs-lookup"><span data-stu-id="95897-121">For editing, use the <xref:System.Xml.XmlDocument> class.</span></span>|
|<xref:System.Xml.XPath.IXPathNavigable>|<span data-ttu-id="95897-122">Jedná se o rozhraní, které poskytuje `CreateNavigator` metodu <xref:System.Xml.XPath.XPathNavigator> pro úložiště.</span><span class="sxs-lookup"><span data-stu-id="95897-122">It is an interface that provides a `CreateNavigator` method to an <xref:System.Xml.XPath.XPathNavigator> for the store.</span></span>|
|<xref:System.Xml.XmlDocument>|<span data-ttu-id="95897-123">Umožňuje úpravy tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="95897-123">It enables editing of this document.</span></span> <span data-ttu-id="95897-124">Implementuje <xref:System.Xml.XPath.IXPathNavigable>a povoluje scénáře úprav dokumentů, kde jsou následně požadovány transformace XSLT.</span><span class="sxs-lookup"><span data-stu-id="95897-124">It implements <xref:System.Xml.XPath.IXPathNavigable>, allowing document-editing scenarios where XSLT transformations are subsequently required.</span></span> <span data-ttu-id="95897-125">Další informace najdete v tématu [vstupní hodnoty XmlDocument pro XslTransform](xmldocument-input-to-xsltransform.md).</span><span class="sxs-lookup"><span data-stu-id="95897-125">For more information, see [XmlDocument Input to XslTransform](xmldocument-input-to-xsltransform.md).</span></span>|
|<xref:System.Xml.XmlDataDocument>|<span data-ttu-id="95897-126">Je odvozen z <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="95897-126">It is derived from the <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="95897-127">Předává relační a XML světů pomocí a <xref:System.Data.DataSet> k optimalizaci úložiště strukturovaných dat v rámci dokumentu XML podle zadaných mapování v. <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="95897-127">It bridges the relational and XML worlds by using a <xref:System.Data.DataSet> to optimize storage of structured data within the XML document according to specified mappings on the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="95897-128">Implementuje <xref:System.Xml.XPath.IXPathNavigable>a povoluje scénáře, kde lze provádět transformace XSLT prostřednictvím relačních dat načtených z databáze.</span><span class="sxs-lookup"><span data-stu-id="95897-128">It implements <xref:System.Xml.XPath.IXPathNavigable>, allowing scenarios where XSLT transformations can be performed over relational data retrieved from a database.</span></span> <span data-ttu-id="95897-129">Další informace najdete v tématu [integrace XML s relačními daty a ADO.NET](xml-integration-with-relational-data-and-adonet.md).</span><span class="sxs-lookup"><span data-stu-id="95897-129">For more information, see [XML Integration with Relational Data and ADO.NET](xml-integration-with-relational-data-and-adonet.md).</span></span>|
|<xref:System.Xml.XPath.XPathDocument>|<span data-ttu-id="95897-130">Tato třída je optimalizována <xref:System.Xml.Xsl.XslTransform> pro zpracování a dotazy XPath a poskytuje mezipaměť s vysokým výkonem jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="95897-130">This class is optimized for <xref:System.Xml.Xsl.XslTransform> processing and XPath queries, and it provides a read-only high performance cache.</span></span> <span data-ttu-id="95897-131">Implementuje <xref:System.Xml.XPath.IXPathNavigable> a je preferovaným úložištěm, které se má použít pro transformace XSLT.</span><span class="sxs-lookup"><span data-stu-id="95897-131">It implements <xref:System.Xml.XPath.IXPathNavigable> and is the preferred store to use for XSLT transformations.</span></span>|
|<xref:System.Xml.XPath.XPathNodeIterator>|<span data-ttu-id="95897-132">Poskytuje navigaci nad sadami uzlů XPath.</span><span class="sxs-lookup"><span data-stu-id="95897-132">It provides navigation over XPath node sets.</span></span> <span data-ttu-id="95897-133">Všechny metody výběru XPath při <xref:System.Xml.XPath.XPathNavigator> vrácení. <xref:System.Xml.XPath.XPathNodeIterator></span><span class="sxs-lookup"><span data-stu-id="95897-133">All XPath selection methods on the <xref:System.Xml.XPath.XPathNavigator> return an <xref:System.Xml.XPath.XPathNodeIterator>.</span></span> <span data-ttu-id="95897-134">V <xref:System.Xml.XPath.XPathNodeIterator> rámci stejného úložiště lze vytvořit více objektů, z nichž každý představuje vybranou sadu uzlů.</span><span class="sxs-lookup"><span data-stu-id="95897-134">Multiple <xref:System.Xml.XPath.XPathNodeIterator> objects can be created over the same store, each representing a selected set of nodes.</span></span>|

## <a name="msxml-xslt-extensions"></a><span data-ttu-id="95897-135">Rozšíření MSXML XSLT</span><span class="sxs-lookup"><span data-stu-id="95897-135">MSXML XSLT Extensions</span></span>

<span data-ttu-id="95897-136">Funkce `msxsl:script` a `msxsl:node-set` jsou jediná rozšíření XSLT služby Microsoft XML Core Services (MSXML), která <xref:System.Xml.Xsl.XslTransform> třída podporuje.</span><span class="sxs-lookup"><span data-stu-id="95897-136">The `msxsl:script` and `msxsl:node-set` functions are the only Microsoft XML Core Services (MSXML) XSLT extensions supported by the <xref:System.Xml.Xsl.XslTransform> class.</span></span>

## <a name="example"></a><span data-ttu-id="95897-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="95897-137">Example</span></span>

<span data-ttu-id="95897-138">Následující příklad kódu načte šablonu stylů XSLT, přečte soubor s názvem Mojedata. XML do <xref:System.Xml.XPath.XPathDocument>a a provede transformaci dat v fiktivním souboru s názvem MyStylesheet. XSL, který odesílá formátovaný výstup do konzoly.</span><span class="sxs-lookup"><span data-stu-id="95897-138">The following code example loads an XSLT style sheet, reads a file called mydata.xml into an <xref:System.Xml.XPath.XPathDocument>, and performs a transformation on the data on a fictitious file called myStyleSheet.xsl, sending the formatted output to the console.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="95897-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="95897-139">See also</span></span>

- <xref:System.Xml.Xsl.XslTransform>
- [<span data-ttu-id="95897-140">Třída XslTransform implementuje procesor XSLT</span><span class="sxs-lookup"><span data-stu-id="95897-140">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
- [<span data-ttu-id="95897-141">Implementace volitelného chování ve třídě XslTransform</span><span class="sxs-lookup"><span data-stu-id="95897-141">Implementation of Discretionary Behaviors in the XslTransform Class</span></span>](implementation-of-discretionary-behaviors-in-the-xsltransform-class.md)
- [<span data-ttu-id="95897-142">XPathNavigator v transformacích</span><span class="sxs-lookup"><span data-stu-id="95897-142">XPathNavigator in Transformations</span></span>](xpathnavigator-in-transformations.md)
- [<span data-ttu-id="95897-143">XPathNodeIterator v transformacích</span><span class="sxs-lookup"><span data-stu-id="95897-143">XPathNodeIterator in Transformations</span></span>](xpathnodeiterator-in-transformations.md)
- [<span data-ttu-id="95897-144">Vstup XPathDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="95897-144">XPathDocument Input to XslTransform</span></span>](xpathdocument-input-to-xsltransform.md)
- [<span data-ttu-id="95897-145">Vstup XmlDataDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="95897-145">XmlDataDocument Input to XslTransform</span></span>](xmldatadocument-input-to-xsltransform.md)
- [<span data-ttu-id="95897-146">Vstup XmlDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="95897-146">XmlDocument Input to XslTransform</span></span>](xmldocument-input-to-xsltransform.md)
