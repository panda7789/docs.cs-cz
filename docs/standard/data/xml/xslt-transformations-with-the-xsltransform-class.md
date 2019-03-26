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
ms.openlocfilehash: db10dda3cbb328cd143afa48e300588ccc7667a6
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463069"
---
# <a name="xslt-transformations-with-the-xsltransform-class"></a><span data-ttu-id="862d2-102">Transformace XSLT s třídou XslTransform</span><span class="sxs-lookup"><span data-stu-id="862d2-102">XSLT Transformations with the XslTransform Class</span></span>

> [!NOTE]
> <span data-ttu-id="862d2-103"><xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="862d2-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="862d2-104">Můžete provádět rozšiřitelný jazyk šablony stylů transformace XSLT () transformaci pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="862d2-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="862d2-105">Zobrazit [používání třídy XslCompiledTransform](using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](migrating-from-the-xsltransform-class.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="862d2-105">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>

<span data-ttu-id="862d2-106">Cílem XSLT je transformace do jiného dokumentu, který se liší ve formátu nebo strukturu (například pro transformaci XML do kódu HTML k použití na webové stránce nebo k transformaci do dokumentu, který obsahuje pouze požadovaná b pole obsahu zdrojovém dokumentu XML y aplikace).</span><span class="sxs-lookup"><span data-stu-id="862d2-106">The goal of the XSLT is to transform the content of a source XML document into another document that is different in format or structure (for example, to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application).</span></span> <span data-ttu-id="862d2-107">Tento proces transformace je určená World Wide Web Consortium (W3C)[XSLT verze 1.0 doporučení](https://www.w3.org/TR/1999/REC-xslt-19991116).</span><span class="sxs-lookup"><span data-stu-id="862d2-107">This transformation process is specified by the World Wide Web Consortium (W3C)[XSLT version 1.0 recommendation](https://www.w3.org/TR/1999/REC-xslt-19991116).</span></span> <span data-ttu-id="862d2-108">V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], <xref:System.Xml.Xsl.XslTransform> třída součástí <xref:System.Xml.Xsl> je obor názvů, procesoru XSLT, který implementuje funkce téhle specifikaci.</span><span class="sxs-lookup"><span data-stu-id="862d2-108">In the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], the <xref:System.Xml.Xsl.XslTransform> class, found in the <xref:System.Xml.Xsl> namespace, is the XSLT processor that implements the functionality of this specification.</span></span> <span data-ttu-id="862d2-109">Malý počet funkcí, které nejsou implementované v doporučení W3C XSLT 1.0, uvedené v [výstupy z XslTransform](outputs-from-an-xsltransform.md).</span><span class="sxs-lookup"><span data-stu-id="862d2-109">There are a small number of features that have not been implemented from the W3C XSLT 1.0 recommendation, listed in [Outputs from an XslTransform](outputs-from-an-xsltransform.md).</span></span> <span data-ttu-id="862d2-110">Následující obrázek ukazuje architekturu transformace [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="862d2-110">The following figure shows the transformation architecture of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span>

## <a name="overview"></a><span data-ttu-id="862d2-111">Přehled</span><span class="sxs-lookup"><span data-stu-id="862d2-111">Overview</span></span>

![Diagram znázorňující architekturu transformace XSLT.](./media/xslt-transformations-with-the-xsltransform-class/xslt-transformation-architecture.gif) 

<span data-ttu-id="862d2-113">Doporučení XSLT používá jazyk XML Path (XPath) pro výběr součástí dokumentu XML, pokud výraz XPath je dotazovací jazyk pro pohyb mezi uzly stromu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="862d2-113">The XSLT recommendation uses XML Path Language (XPath) to select parts of an XML document, where XPath is a query language used to navigate nodes of a document tree.</span></span> <span data-ttu-id="862d2-114">Jak je znázorněno na diagramu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] implementace XPath slouží k výběru součástí jazyka XML uložené v několik tříd, jako například <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument>a <xref:System.Xml.XPath.XPathDocument>.</span><span class="sxs-lookup"><span data-stu-id="862d2-114">As shown in the diagram, the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] implementation of XPath is used to select parts of XML stored in several classes, such as an <xref:System.Xml.XmlDocument>, an <xref:System.Xml.XmlDataDocument>, and an <xref:System.Xml.XPath.XPathDocument>.</span></span> <span data-ttu-id="862d2-115"><xref:System.Xml.XPath.XPathDocument> Je optimalizované XSLT datové úložiště a při použití s <xref:System.Xml.Xsl.XslTransform>, poskytuje transformace XSLT s dobrého výkonu.</span><span class="sxs-lookup"><span data-stu-id="862d2-115">An <xref:System.Xml.XPath.XPathDocument> is an optimized XSLT data store, and when used with <xref:System.Xml.Xsl.XslTransform>, it provides XSLT transformations with good performance.</span></span>

<span data-ttu-id="862d2-116">V následujícím seznamu tabulku běžně používá třídy při práci s <xref:System.Xml.Xsl.XslTransform> a XPath a jejich funkce.</span><span class="sxs-lookup"><span data-stu-id="862d2-116">The following table list commonly uses classes when working with <xref:System.Xml.Xsl.XslTransform> and XPath and their function.</span></span>

|<span data-ttu-id="862d2-117">Třída nebo rozhraní</span><span class="sxs-lookup"><span data-stu-id="862d2-117">Class or Interface</span></span>|<span data-ttu-id="862d2-118">Funkce</span><span class="sxs-lookup"><span data-stu-id="862d2-118">Function</span></span>|
|------------------------|--------------|
|<xref:System.Xml.XPath.XPathNavigator>|<span data-ttu-id="862d2-119">Je rozhraní API, které poskytuje model styl kurzoru pro navigaci v úložišti, společně s podporou dotaz XPath.</span><span class="sxs-lookup"><span data-stu-id="862d2-119">It is an API that provides a cursor style model for navigating over a store, along with XPath query support.</span></span> <span data-ttu-id="862d2-120">Neposkytuje úpravy základní úložiště.</span><span class="sxs-lookup"><span data-stu-id="862d2-120">It does not provide editing of the underlying store.</span></span> <span data-ttu-id="862d2-121">Pro úpravy, použijte <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="862d2-121">For editing, use the <xref:System.Xml.XmlDocument> class.</span></span>|
|<xref:System.Xml.XPath.IXPathNavigable>|<span data-ttu-id="862d2-122">Je rozhraní, které poskytuje `CreateNavigator` metodu <xref:System.Xml.XPath.XPathNavigator> pro úložiště.</span><span class="sxs-lookup"><span data-stu-id="862d2-122">It is an interface that provides a `CreateNavigator` method to an <xref:System.Xml.XPath.XPathNavigator> for the store.</span></span>|
|<xref:System.Xml.XmlDocument>|<span data-ttu-id="862d2-123">Umožňuje úpravy tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="862d2-123">It enables editing of this document.</span></span> <span data-ttu-id="862d2-124">Implementuje <xref:System.Xml.XPath.IXPathNavigable>, umožňující úpravy dokumentu scénáře, kde se následně vyžadují transformace XSLT.</span><span class="sxs-lookup"><span data-stu-id="862d2-124">It implements <xref:System.Xml.XPath.IXPathNavigable>, allowing document-editing scenarios where XSLT transformations are subsequently required.</span></span> <span data-ttu-id="862d2-125">Další informace najdete v tématu [vstup XmlDocument do XslTransform](xmldocument-input-to-xsltransform.md).</span><span class="sxs-lookup"><span data-stu-id="862d2-125">For more information, see [XmlDocument Input to XslTransform](xmldocument-input-to-xsltransform.md).</span></span>|
|<xref:System.Xml.XmlDataDocument>|<span data-ttu-id="862d2-126">Je odvozen z <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="862d2-126">It is derived from the <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="862d2-127">Překlenuje relační a světů XML pomocí <xref:System.Data.DataSet> pro optimalizaci úložiště strukturovaných dat v dokumentu XML podle zadaného mapování na <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="862d2-127">It bridges the relational and XML worlds by using a <xref:System.Data.DataSet> to optimize storage of structured data within the XML document according to specified mappings on the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="862d2-128">Implementuje <xref:System.Xml.XPath.IXPathNavigable>, umožňuje scénáře, kde lze provádět transformace XSLT nad relační data načtená z databáze.</span><span class="sxs-lookup"><span data-stu-id="862d2-128">It implements <xref:System.Xml.XPath.IXPathNavigable>, allowing scenarios where XSLT transformations can be performed over relational data retrieved from a database.</span></span> <span data-ttu-id="862d2-129">Další informace najdete v tématu [integrace XML s relačními daty a ADO.NET](xml-integration-with-relational-data-and-adonet.md).</span><span class="sxs-lookup"><span data-stu-id="862d2-129">For more information, see [XML Integration with Relational Data and ADO.NET](xml-integration-with-relational-data-and-adonet.md).</span></span>|
|<xref:System.Xml.XPath.XPathDocument>|<span data-ttu-id="862d2-130">Tato třída je optimalizována pro <xref:System.Xml.Xsl.XslTransform> zpracování a dotazů XPath a poskytuje jen pro čtení vysoký výkon mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="862d2-130">This class is optimized for <xref:System.Xml.Xsl.XslTransform> processing and XPath queries, and it provides a read-only high performance cache.</span></span> <span data-ttu-id="862d2-131">Implementuje <xref:System.Xml.XPath.IXPathNavigable> a je upřednostňovaný úložiště pro transformace XSLT.</span><span class="sxs-lookup"><span data-stu-id="862d2-131">It implements <xref:System.Xml.XPath.IXPathNavigable> and is the preferred store to use for XSLT transformations.</span></span>|
|<xref:System.Xml.XPath.XPathNodeIterator>|<span data-ttu-id="862d2-132">Poskytuje navigace prostřednictvím sady uzlu XPath.</span><span class="sxs-lookup"><span data-stu-id="862d2-132">It provides navigation over XPath node sets.</span></span> <span data-ttu-id="862d2-133">Všechny metody výběr XPath <xref:System.Xml.XPath.XPathNavigator> vrátit <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="862d2-133">All XPath selection methods on the <xref:System.Xml.XPath.XPathNavigator> return an <xref:System.Xml.XPath.XPathNodeIterator>.</span></span> <span data-ttu-id="862d2-134">Více <xref:System.Xml.XPath.XPathNodeIterator> objekty mohou být vytvořeny prostřednictvím stejné úložiště, ve nichž každý představuje vybrané sady uzlů.</span><span class="sxs-lookup"><span data-stu-id="862d2-134">Multiple <xref:System.Xml.XPath.XPathNodeIterator> objects can be created over the same store, each representing a selected set of nodes.</span></span>|

## <a name="msxml-xslt-extensions"></a><span data-ttu-id="862d2-135">Rozšíření MSXML XSLT</span><span class="sxs-lookup"><span data-stu-id="862d2-135">MSXML XSLT Extensions</span></span>

<span data-ttu-id="862d2-136">`msxsl:script` a `msxsl:node-set` funkce jsou pouze rozšíření XSLT Microsoft XML Core Services (MSXML) podporuje <xref:System.Xml.Xsl.XslTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="862d2-136">The `msxsl:script` and `msxsl:node-set` functions are the only Microsoft XML Core Services (MSXML) XSLT extensions supported by the <xref:System.Xml.Xsl.XslTransform> class.</span></span>

## <a name="example"></a><span data-ttu-id="862d2-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="862d2-137">Example</span></span>

<span data-ttu-id="862d2-138">Následující příklad kódu načte šablony stylů XSLT, načte soubor s názvem data.XML do <xref:System.Xml.XPath.XPathDocument>a provede transformaci na data na fiktivní soubor s názvem myStyleSheet.xsl odesílání formátovaný výstup do konzoly.</span><span class="sxs-lookup"><span data-stu-id="862d2-138">The following code example loads an XSLT style sheet, reads a file called mydata.xml into an <xref:System.Xml.XPath.XPathDocument>, and performs a transformation on the data on a fictitious file called myStyleSheet.xsl, sending the formatted output to the console.</span></span>

```vb
Imports System
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

## <a name="see-also"></a><span data-ttu-id="862d2-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="862d2-139">See also</span></span>

- <xref:System.Xml.Xsl.XslTransform>
- [<span data-ttu-id="862d2-140">Třída XslTransform implementuje procesor XSLT</span><span class="sxs-lookup"><span data-stu-id="862d2-140">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
- [<span data-ttu-id="862d2-141">Implementace volitelného chování ve třídě XslTransform</span><span class="sxs-lookup"><span data-stu-id="862d2-141">Implementation of Discretionary Behaviors in the XslTransform Class</span></span>](implementation-of-discretionary-behaviors-in-the-xsltransform-class.md)
- [<span data-ttu-id="862d2-142">XPathNavigator v transformacích</span><span class="sxs-lookup"><span data-stu-id="862d2-142">XPathNavigator in Transformations</span></span>](xpathnavigator-in-transformations.md)
- [<span data-ttu-id="862d2-143">XPathNodeIterator v transformacích</span><span class="sxs-lookup"><span data-stu-id="862d2-143">XPathNodeIterator in Transformations</span></span>](xpathnodeiterator-in-transformations.md)
- [<span data-ttu-id="862d2-144">Vstup XPathDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="862d2-144">XPathDocument Input to XslTransform</span></span>](xpathdocument-input-to-xsltransform.md)
- [<span data-ttu-id="862d2-145">Vstup XmlDataDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="862d2-145">XmlDataDocument Input to XslTransform</span></span>](xmldatadocument-input-to-xsltransform.md)
- [<span data-ttu-id="862d2-146">Vstup XmlDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="862d2-146">XmlDocument Input to XslTransform</span></span>](xmldocument-input-to-xsltransform.md)
