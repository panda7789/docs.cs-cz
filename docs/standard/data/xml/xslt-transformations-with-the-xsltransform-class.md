---
title: Transformace XSLT pomocí XslTransform – třída
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 500335af-f9b5-413b-968a-e6d9a824478c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ece159b35cfbc83e05432b93ce7df06a5ca9fcac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576165"
---
# <a name="xslt-transformations-with-the-xsltransform-class"></a><span data-ttu-id="0d59f-102">Transformace XSLT pomocí XslTransform – třída</span><span class="sxs-lookup"><span data-stu-id="0d59f-102">XSLT Transformations with the XslTransform Class</span></span>
> [!NOTE]
>  <span data-ttu-id="0d59f-103"><xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0d59f-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="0d59f-104">Můžete provést jazyk XSL pro transformace transformace XSLT () pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="0d59f-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="0d59f-105">V tématu [pomocí třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="0d59f-105">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="0d59f-106">Cílem XSLT je k transformaci obsah zdrojový dokument XML do jiného dokumentu, který se liší ve formátu nebo strukturu (například transformace XML do kódu HTML k použití na webu a transformují je na dokument, který obsahuje pouze pole požadované b y aplikace).</span><span class="sxs-lookup"><span data-stu-id="0d59f-106">The goal of the XSLT is to transform the content of a source XML document into another document that is different in format or structure (for example, to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application).</span></span> <span data-ttu-id="0d59f-107">Tento proces transformace je zadána v www.w3.org/TR/xslt doporučení XSLT World Wide Web Consortium (W3C) verze 1.0.</span><span class="sxs-lookup"><span data-stu-id="0d59f-107">This transformation process is specified by the World Wide Web Consortium (W3C) XSLT version 1.0 recommendation located at www.w3.org/TR/xslt.</span></span> <span data-ttu-id="0d59f-108">V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], <xref:System.Xml.Xsl.XslTransform> nalezena v třída <xref:System.Xml.Xsl> obor názvů, je procesor XSLT, která implementuje funkce této specifikace.</span><span class="sxs-lookup"><span data-stu-id="0d59f-108">In the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], the <xref:System.Xml.Xsl.XslTransform> class, found in the <xref:System.Xml.Xsl> namespace, is the XSLT processor that implements the functionality of this specification.</span></span> <span data-ttu-id="0d59f-109">Existuje malé množství funkcí, které nejsou implementované z doporučení W3C XSLT 1.0, uvedené v [výstupy z XslTransform](../../../../docs/standard/data/xml/outputs-from-an-xsltransform.md).</span><span class="sxs-lookup"><span data-stu-id="0d59f-109">There are a small number of features that have not been implemented from the W3C XSLT 1.0 recommendation, listed in [Outputs from an XslTransform](../../../../docs/standard/data/xml/outputs-from-an-xsltransform.md).</span></span> <span data-ttu-id="0d59f-110">Následující obrázek znázorňuje architekturu transformace [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0d59f-110">The following figure shows the transformation architecture of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="overview"></a><span data-ttu-id="0d59f-111">Přehled</span><span class="sxs-lookup"><span data-stu-id="0d59f-111">Overview</span></span>  
 <span data-ttu-id="0d59f-112">![Architektura transformace XSLT](../../../../docs/standard/data/xml/media/xslttransformationswithxsltransformclass.gif "xsltTransformationsWithXslTransformClass")</span><span class="sxs-lookup"><span data-stu-id="0d59f-112">![XSLT Transformation Architecture](../../../../docs/standard/data/xml/media/xslttransformationswithxsltransformclass.gif "xsltTransformationsWithXslTransformClass")</span></span>  
<span data-ttu-id="0d59f-113">Architektura transformace</span><span class="sxs-lookup"><span data-stu-id="0d59f-113">Transformation Architecture</span></span>  
  
 <span data-ttu-id="0d59f-114">Doporučení XSLT použije k výběru části dokumentu XML, kde XPath je dotazovací jazyk použít pro účely navigace uzlů ve stromu dokumentu XML Path Language (XPath).</span><span class="sxs-lookup"><span data-stu-id="0d59f-114">The XSLT recommendation uses XML Path Language (XPath) to select parts of an XML document, where XPath is a query language used to navigate nodes of a document tree.</span></span> <span data-ttu-id="0d59f-115">Jak je znázorněno na obrázku [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] implementace XPath slouží k výběru částí XML uložené v několik tříd, jako například <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument>a <xref:System.Xml.XPath.XPathDocument>.</span><span class="sxs-lookup"><span data-stu-id="0d59f-115">As shown in the diagram, the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] implementation of XPath is used to select parts of XML stored in several classes, such as an <xref:System.Xml.XmlDocument>, an <xref:System.Xml.XmlDataDocument>, and an <xref:System.Xml.XPath.XPathDocument>.</span></span> <span data-ttu-id="0d59f-116"><xref:System.Xml.XPath.XPathDocument> Je optimalizované XSLT datové úložiště a pokud se používá s <xref:System.Xml.Xsl.XslTransform>, poskytuje transformace XSLT pomocí dobrý výkon.</span><span class="sxs-lookup"><span data-stu-id="0d59f-116">An <xref:System.Xml.XPath.XPathDocument> is an optimized XSLT data store, and when used with <xref:System.Xml.Xsl.XslTransform>, it provides XSLT transformations with good performance.</span></span>  
  
 <span data-ttu-id="0d59f-117">Následující seznam tabulek běžně používá třídy při práci s <xref:System.Xml.Xsl.XslTransform> a XPath a jejich funkce.</span><span class="sxs-lookup"><span data-stu-id="0d59f-117">The following table list commonly uses classes when working with <xref:System.Xml.Xsl.XslTransform> and XPath and their function.</span></span>  
  
|<span data-ttu-id="0d59f-118">Třídy nebo rozhraní</span><span class="sxs-lookup"><span data-stu-id="0d59f-118">Class or Interface</span></span>|<span data-ttu-id="0d59f-119">Funkce</span><span class="sxs-lookup"><span data-stu-id="0d59f-119">Function</span></span>|  
|------------------------|--------------|  
|<xref:System.Xml.XPath.XPathNavigator>|<span data-ttu-id="0d59f-120">Je rozhraní API, které poskytuje model styl kurzor pro navigaci přes úložiště, společně s podporou dotaz XPath.</span><span class="sxs-lookup"><span data-stu-id="0d59f-120">It is an API that provides a cursor style model for navigating over a store, along with XPath query support.</span></span> <span data-ttu-id="0d59f-121">Neposkytuje úpravy základní úložiště.</span><span class="sxs-lookup"><span data-stu-id="0d59f-121">It does not provide editing of the underlying store.</span></span> <span data-ttu-id="0d59f-122">Pro úpravy, použijte <xref:System.Xml.XmlDocument> třídy.</span><span class="sxs-lookup"><span data-stu-id="0d59f-122">For editing, use the <xref:System.Xml.XmlDocument> class.</span></span>|  
|<xref:System.Xml.XPath.IXPathNavigable>|<span data-ttu-id="0d59f-123">Je rozhraní, které poskytuje `CreateNavigator` metodu <xref:System.Xml.XPath.XPathNavigator> pro úložiště.</span><span class="sxs-lookup"><span data-stu-id="0d59f-123">It is an interface that provides a `CreateNavigator` method to an <xref:System.Xml.XPath.XPathNavigator> for the store.</span></span>|  
|<xref:System.Xml.XmlDocument>|<span data-ttu-id="0d59f-124">Umožňuje úpravy tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="0d59f-124">It enables editing of this document.</span></span> <span data-ttu-id="0d59f-125">Implementuje <xref:System.Xml.XPath.IXPathNavigable>, povolení úprav dokumentu scénáře, kde jsou následně vyžadovány transformace XSLT.</span><span class="sxs-lookup"><span data-stu-id="0d59f-125">It implements <xref:System.Xml.XPath.IXPathNavigable>, allowing document-editing scenarios where XSLT transformations are subsequently required.</span></span> <span data-ttu-id="0d59f-126">Další informace najdete v tématu [třídou XMLDocument nastavenou na vstup XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md).</span><span class="sxs-lookup"><span data-stu-id="0d59f-126">For more information, see [XmlDocument Input to XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md).</span></span>|  
|<xref:System.Xml.XmlDataDocument>|<span data-ttu-id="0d59f-127">Je odvozený od <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="0d59f-127">It is derived from the <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="0d59f-128">Přemosťuje relační a světů XML pomocí <xref:System.Data.DataSet> za účelem optimalizace ukládání strukturovaných dat v dokumentu XML podle zadaného mapování na <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="0d59f-128">It bridges the relational and XML worlds by using a <xref:System.Data.DataSet> to optimize storage of structured data within the XML document according to specified mappings on the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="0d59f-129">Implementuje <xref:System.Xml.XPath.IXPathNavigable>, umožňuje scénáře, kde lze provádět transformace XSLT přes relační data načtená z databáze.</span><span class="sxs-lookup"><span data-stu-id="0d59f-129">It implements <xref:System.Xml.XPath.IXPathNavigable>, allowing scenarios where XSLT transformations can be performed over relational data retrieved from a database.</span></span> <span data-ttu-id="0d59f-130">Další informace najdete v tématu [XML integrace s relačních dat a ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md).</span><span class="sxs-lookup"><span data-stu-id="0d59f-130">For more information, see [XML Integration with Relational Data and ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md).</span></span>|  
|<xref:System.Xml.XPath.XPathDocument>|<span data-ttu-id="0d59f-131">Tato třída je optimalizována pro <xref:System.Xml.Xsl.XslTransform> zpracování a dotazů XPath a poskytuje mezipaměť jen pro čtení vysoký výkon.</span><span class="sxs-lookup"><span data-stu-id="0d59f-131">This class is optimized for <xref:System.Xml.Xsl.XslTransform> processing and XPath queries, and it provides a read-only high performance cache.</span></span> <span data-ttu-id="0d59f-132">Implementuje <xref:System.Xml.XPath.IXPathNavigable> a je upřednostňovaný úložiště, které chcete použít pro transformace XSLT.</span><span class="sxs-lookup"><span data-stu-id="0d59f-132">It implements <xref:System.Xml.XPath.IXPathNavigable> and is the preferred store to use for XSLT transformations.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeIterator>|<span data-ttu-id="0d59f-133">Zajišťuje navigace v uzlu sady XPath.</span><span class="sxs-lookup"><span data-stu-id="0d59f-133">It provides navigation over XPath node sets.</span></span> <span data-ttu-id="0d59f-134">Všechny metody výběru XPath na <xref:System.Xml.XPath.XPathNavigator> vrátit <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="0d59f-134">All XPath selection methods on the <xref:System.Xml.XPath.XPathNavigator> return an <xref:System.Xml.XPath.XPathNodeIterator>.</span></span> <span data-ttu-id="0d59f-135">Více <xref:System.Xml.XPath.XPathNodeIterator> objekty mohou být vytvořeny přes stejné úložiště, každý představuje vybrané sada uzlů.</span><span class="sxs-lookup"><span data-stu-id="0d59f-135">Multiple <xref:System.Xml.XPath.XPathNodeIterator> objects can be created over the same store, each representing a selected set of nodes.</span></span>|  
  
## <a name="msxml-xslt-extensions"></a><span data-ttu-id="0d59f-136">Rozšíření MSXML XSLT</span><span class="sxs-lookup"><span data-stu-id="0d59f-136">MSXML XSLT Extensions</span></span>  
 <span data-ttu-id="0d59f-137">`msxsl:script` a `msxsl:node-set` funkce se podporuje jenom rozšíření XSLT Microsoft XML Core Services (MSXML) <xref:System.Xml.Xsl.XslTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="0d59f-137">The `msxsl:script` and `msxsl:node-set` functions are the only Microsoft XML Core Services (MSXML) XSLT extensions supported by the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d59f-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="0d59f-138">Example</span></span>  
 <span data-ttu-id="0d59f-139">Následující příklad kódu načte stylů XSLT, přečte soubor s názvem data.XML do <xref:System.Xml.XPath.XPathDocument>a provádí transformaci dat na smyšlené soubor s názvem myStyleSheet.xsl, odesílání formátovaný výstup do konzoly.</span><span class="sxs-lookup"><span data-stu-id="0d59f-139">The following code example loads an XSLT style sheet, reads a file called mydata.xml into an <xref:System.Xml.XPath.XPathDocument>, and performs a transformation on the data on a fictitious file called myStyleSheet.xsl, sending the formatted output to the console.</span></span>  
  
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
    XPathDocument xpathdocument = new  
    XPathDocument(filename);  
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
    writer.Formatting=Formatting.Indented;  
  
    xslt.Transform(xpathdocument, null, writer, null);      
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d59f-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d59f-140">See Also</span></span>  
 <xref:System.Xml.Xsl.XslTransform>  
 [<span data-ttu-id="0d59f-141">Třída XslTransform implementuje procesor XSLT</span><span class="sxs-lookup"><span data-stu-id="0d59f-141">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
 [<span data-ttu-id="0d59f-142">Implementace volitelného chování ve třídě XslTransform</span><span class="sxs-lookup"><span data-stu-id="0d59f-142">Implementation of Discretionary Behaviors in the XslTransform Class</span></span>](../../../../docs/standard/data/xml/implementation-of-discretionary-behaviors-in-the-xsltransform-class.md)  
 [<span data-ttu-id="0d59f-143">XPathNavigator v transformacích</span><span class="sxs-lookup"><span data-stu-id="0d59f-143">XPathNavigator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [<span data-ttu-id="0d59f-144">XPathNodeIterator v transformacích</span><span class="sxs-lookup"><span data-stu-id="0d59f-144">XPathNodeIterator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [<span data-ttu-id="0d59f-145">Vstup XPathDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="0d59f-145">XPathDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [<span data-ttu-id="0d59f-146">Vstup XmlDataDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="0d59f-146">XmlDataDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
 [<span data-ttu-id="0d59f-147">Vstup XmlDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="0d59f-147">XmlDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
