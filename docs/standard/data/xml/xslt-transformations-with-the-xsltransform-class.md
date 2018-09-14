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
ms.openlocfilehash: 67062ab87182bcb42793cb166323020178ac1688
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45570402"
---
# <a name="xslt-transformations-with-the-xsltransform-class"></a><span data-ttu-id="9657e-102">Transformace XSLT s třídou XslTransform</span><span class="sxs-lookup"><span data-stu-id="9657e-102">XSLT Transformations with the XslTransform Class</span></span>

> [!NOTE]
> <span data-ttu-id="9657e-103"><xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9657e-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="9657e-104">Můžete provádět rozšiřitelný jazyk šablony stylů transformace XSLT () transformaci pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="9657e-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="9657e-105">Zobrazit [používání třídy XslCompiledTransform](using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](migrating-from-the-xsltransform-class.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="9657e-105">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>

<span data-ttu-id="9657e-106">Cílem XSLT je transformace do jiného dokumentu, který se liší ve formátu nebo strukturu (například pro transformaci XML do kódu HTML k použití na webové stránce nebo k transformaci do dokumentu, který obsahuje pouze požadovaná b pole obsahu zdrojovém dokumentu XML y aplikace).</span><span class="sxs-lookup"><span data-stu-id="9657e-106">The goal of the XSLT is to transform the content of a source XML document into another document that is different in format or structure (for example, to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application).</span></span> <span data-ttu-id="9657e-107">Tento proces transformace je určená World Wide Web Consortium (W3C)[XSLT verze 1.0 doporučení](https://www.w3.org/TR/1999/REC-xslt-19991116).</span><span class="sxs-lookup"><span data-stu-id="9657e-107">This transformation process is specified by the World Wide Web Consortium (W3C)[XSLT version 1.0 recommendation](https://www.w3.org/TR/1999/REC-xslt-19991116).</span></span> <span data-ttu-id="9657e-108">V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], <xref:System.Xml.Xsl.XslTransform> třída součástí <xref:System.Xml.Xsl> je obor názvů, procesoru XSLT, který implementuje funkce téhle specifikaci.</span><span class="sxs-lookup"><span data-stu-id="9657e-108">In the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], the <xref:System.Xml.Xsl.XslTransform> class, found in the <xref:System.Xml.Xsl> namespace, is the XSLT processor that implements the functionality of this specification.</span></span> <span data-ttu-id="9657e-109">Malý počet funkcí, které nejsou implementované v doporučení W3C XSLT 1.0, uvedené v [výstupy z XslTransform](outputs-from-an-xsltransform.md).</span><span class="sxs-lookup"><span data-stu-id="9657e-109">There are a small number of features that have not been implemented from the W3C XSLT 1.0 recommendation, listed in [Outputs from an XslTransform](outputs-from-an-xsltransform.md).</span></span> <span data-ttu-id="9657e-110">Následující obrázek ukazuje architekturu transformace [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9657e-110">The following figure shows the transformation architecture of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span>

## <a name="overview"></a><span data-ttu-id="9657e-111">Přehled</span><span class="sxs-lookup"><span data-stu-id="9657e-111">Overview</span></span>

<span data-ttu-id="9657e-112">![Architektura transformace XSLT](media/xslttransformationswithxsltransformclass.gif "xsltTransformationsWithXslTransformClass")</span><span class="sxs-lookup"><span data-stu-id="9657e-112">![XSLT Transformation Architecture](media/xslttransformationswithxsltransformclass.gif "xsltTransformationsWithXslTransformClass")</span></span>  
<span data-ttu-id="9657e-113">Architektura transformace</span><span class="sxs-lookup"><span data-stu-id="9657e-113">Transformation Architecture</span></span>

<span data-ttu-id="9657e-114">Doporučení XSLT používá jazyk XML Path (XPath) pro výběr součástí dokumentu XML, pokud výraz XPath je dotazovací jazyk pro pohyb mezi uzly stromu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="9657e-114">The XSLT recommendation uses XML Path Language (XPath) to select parts of an XML document, where XPath is a query language used to navigate nodes of a document tree.</span></span> <span data-ttu-id="9657e-115">Jak je znázorněno na diagramu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] implementace XPath slouží k výběru součástí jazyka XML uložené v několik tříd, jako například <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument>a <xref:System.Xml.XPath.XPathDocument>.</span><span class="sxs-lookup"><span data-stu-id="9657e-115">As shown in the diagram, the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] implementation of XPath is used to select parts of XML stored in several classes, such as an <xref:System.Xml.XmlDocument>, an <xref:System.Xml.XmlDataDocument>, and an <xref:System.Xml.XPath.XPathDocument>.</span></span> <span data-ttu-id="9657e-116"><xref:System.Xml.XPath.XPathDocument> Je optimalizované XSLT datové úložiště a při použití s <xref:System.Xml.Xsl.XslTransform>, poskytuje transformace XSLT s dobrého výkonu.</span><span class="sxs-lookup"><span data-stu-id="9657e-116">An <xref:System.Xml.XPath.XPathDocument> is an optimized XSLT data store, and when used with <xref:System.Xml.Xsl.XslTransform>, it provides XSLT transformations with good performance.</span></span>

<span data-ttu-id="9657e-117">V následujícím seznamu tabulku běžně používá třídy při práci s <xref:System.Xml.Xsl.XslTransform> a XPath a jejich funkce.</span><span class="sxs-lookup"><span data-stu-id="9657e-117">The following table list commonly uses classes when working with <xref:System.Xml.Xsl.XslTransform> and XPath and their function.</span></span>

|<span data-ttu-id="9657e-118">Třída nebo rozhraní</span><span class="sxs-lookup"><span data-stu-id="9657e-118">Class or Interface</span></span>|<span data-ttu-id="9657e-119">Funkce</span><span class="sxs-lookup"><span data-stu-id="9657e-119">Function</span></span>|
|------------------------|--------------|
|<xref:System.Xml.XPath.XPathNavigator>|<span data-ttu-id="9657e-120">Je rozhraní API, které poskytuje model styl kurzoru pro navigaci v úložišti, společně s podporou dotaz XPath.</span><span class="sxs-lookup"><span data-stu-id="9657e-120">It is an API that provides a cursor style model for navigating over a store, along with XPath query support.</span></span> <span data-ttu-id="9657e-121">Neposkytuje úpravy základní úložiště.</span><span class="sxs-lookup"><span data-stu-id="9657e-121">It does not provide editing of the underlying store.</span></span> <span data-ttu-id="9657e-122">Pro úpravy, použijte <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="9657e-122">For editing, use the <xref:System.Xml.XmlDocument> class.</span></span>|
|<xref:System.Xml.XPath.IXPathNavigable>|<span data-ttu-id="9657e-123">Je rozhraní, které poskytuje `CreateNavigator` metodu <xref:System.Xml.XPath.XPathNavigator> pro úložiště.</span><span class="sxs-lookup"><span data-stu-id="9657e-123">It is an interface that provides a `CreateNavigator` method to an <xref:System.Xml.XPath.XPathNavigator> for the store.</span></span>|
|<xref:System.Xml.XmlDocument>|<span data-ttu-id="9657e-124">Umožňuje úpravy tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="9657e-124">It enables editing of this document.</span></span> <span data-ttu-id="9657e-125">Implementuje <xref:System.Xml.XPath.IXPathNavigable>, umožňující úpravy dokumentu scénáře, kde se následně vyžadují transformace XSLT.</span><span class="sxs-lookup"><span data-stu-id="9657e-125">It implements <xref:System.Xml.XPath.IXPathNavigable>, allowing document-editing scenarios where XSLT transformations are subsequently required.</span></span> <span data-ttu-id="9657e-126">Další informace najdete v tématu [vstup XmlDocument do XslTransform](xmldocument-input-to-xsltransform.md).</span><span class="sxs-lookup"><span data-stu-id="9657e-126">For more information, see [XmlDocument Input to XslTransform](xmldocument-input-to-xsltransform.md).</span></span>|
|<xref:System.Xml.XmlDataDocument>|<span data-ttu-id="9657e-127">Je odvozen z <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="9657e-127">It is derived from the <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="9657e-128">Překlenuje relační a světů XML pomocí <xref:System.Data.DataSet> pro optimalizaci úložiště strukturovaných dat v dokumentu XML podle zadaného mapování na <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="9657e-128">It bridges the relational and XML worlds by using a <xref:System.Data.DataSet> to optimize storage of structured data within the XML document according to specified mappings on the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="9657e-129">Implementuje <xref:System.Xml.XPath.IXPathNavigable>, umožňuje scénáře, kde lze provádět transformace XSLT nad relační data načtená z databáze.</span><span class="sxs-lookup"><span data-stu-id="9657e-129">It implements <xref:System.Xml.XPath.IXPathNavigable>, allowing scenarios where XSLT transformations can be performed over relational data retrieved from a database.</span></span> <span data-ttu-id="9657e-130">Další informace najdete v tématu [integrace XML s relačními daty a ADO.NET](xml-integration-with-relational-data-and-adonet.md).</span><span class="sxs-lookup"><span data-stu-id="9657e-130">For more information, see [XML Integration with Relational Data and ADO.NET](xml-integration-with-relational-data-and-adonet.md).</span></span>|
|<xref:System.Xml.XPath.XPathDocument>|<span data-ttu-id="9657e-131">Tato třída je optimalizována pro <xref:System.Xml.Xsl.XslTransform> zpracování a dotazů XPath a poskytuje jen pro čtení vysoký výkon mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="9657e-131">This class is optimized for <xref:System.Xml.Xsl.XslTransform> processing and XPath queries, and it provides a read-only high performance cache.</span></span> <span data-ttu-id="9657e-132">Implementuje <xref:System.Xml.XPath.IXPathNavigable> a je upřednostňovaný úložiště pro transformace XSLT.</span><span class="sxs-lookup"><span data-stu-id="9657e-132">It implements <xref:System.Xml.XPath.IXPathNavigable> and is the preferred store to use for XSLT transformations.</span></span>|
|<xref:System.Xml.XPath.XPathNodeIterator>|<span data-ttu-id="9657e-133">Poskytuje navigace prostřednictvím sady uzlu XPath.</span><span class="sxs-lookup"><span data-stu-id="9657e-133">It provides navigation over XPath node sets.</span></span> <span data-ttu-id="9657e-134">Všechny metody výběr XPath <xref:System.Xml.XPath.XPathNavigator> vrátit <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="9657e-134">All XPath selection methods on the <xref:System.Xml.XPath.XPathNavigator> return an <xref:System.Xml.XPath.XPathNodeIterator>.</span></span> <span data-ttu-id="9657e-135">Více <xref:System.Xml.XPath.XPathNodeIterator> objekty mohou být vytvořeny prostřednictvím stejné úložiště, ve nichž každý představuje vybrané sady uzlů.</span><span class="sxs-lookup"><span data-stu-id="9657e-135">Multiple <xref:System.Xml.XPath.XPathNodeIterator> objects can be created over the same store, each representing a selected set of nodes.</span></span>|

## <a name="msxml-xslt-extensions"></a><span data-ttu-id="9657e-136">Rozšíření MSXML XSLT</span><span class="sxs-lookup"><span data-stu-id="9657e-136">MSXML XSLT Extensions</span></span>

<span data-ttu-id="9657e-137">`msxsl:script` a `msxsl:node-set` funkce jsou pouze rozšíření XSLT Microsoft XML Core Services (MSXML) podporuje <xref:System.Xml.Xsl.XslTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="9657e-137">The `msxsl:script` and `msxsl:node-set` functions are the only Microsoft XML Core Services (MSXML) XSLT extensions supported by the <xref:System.Xml.Xsl.XslTransform> class.</span></span>

## <a name="example"></a><span data-ttu-id="9657e-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="9657e-138">Example</span></span>

<span data-ttu-id="9657e-139">Následující příklad kódu načte šablony stylů XSLT, načte soubor s názvem data.XML do <xref:System.Xml.XPath.XPathDocument>a provede transformaci na data na fiktivní soubor s názvem myStyleSheet.xsl odesílání formátovaný výstup do konzoly.</span><span class="sxs-lookup"><span data-stu-id="9657e-139">The following code example loads an XSLT style sheet, reads a file called mydata.xml into an <xref:System.Xml.XPath.XPathDocument>, and performs a transformation on the data on a fictitious file called myStyleSheet.xsl, sending the formatted output to the console.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9657e-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9657e-140">See also</span></span>

- <xref:System.Xml.Xsl.XslTransform>  
- [<span data-ttu-id="9657e-141">Třída XslTransform implementuje procesor XSLT</span><span class="sxs-lookup"><span data-stu-id="9657e-141">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)  
- [<span data-ttu-id="9657e-142">Implementace volitelného chování ve třídě XslTransform</span><span class="sxs-lookup"><span data-stu-id="9657e-142">Implementation of Discretionary Behaviors in the XslTransform Class</span></span>](implementation-of-discretionary-behaviors-in-the-xsltransform-class.md)  
- [<span data-ttu-id="9657e-143">XPathNavigator v transformacích</span><span class="sxs-lookup"><span data-stu-id="9657e-143">XPathNavigator in Transformations</span></span>](xpathnavigator-in-transformations.md)  
- [<span data-ttu-id="9657e-144">XPathNodeIterator v transformacích</span><span class="sxs-lookup"><span data-stu-id="9657e-144">XPathNodeIterator in Transformations</span></span>](xpathnodeiterator-in-transformations.md)  
- [<span data-ttu-id="9657e-145">Vstup XPathDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="9657e-145">XPathDocument Input to XslTransform</span></span>](xpathdocument-input-to-xsltransform.md)  
- [<span data-ttu-id="9657e-146">Vstup XmlDataDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="9657e-146">XmlDataDocument Input to XslTransform</span></span>](xmldatadocument-input-to-xsltransform.md)  
- [<span data-ttu-id="9657e-147">Vstup XmlDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="9657e-147">XmlDocument Input to XslTransform</span></span>](xmldocument-input-to-xsltransform.md)  
