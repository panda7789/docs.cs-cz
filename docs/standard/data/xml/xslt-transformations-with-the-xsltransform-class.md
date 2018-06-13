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
# <a name="xslt-transformations-with-the-xsltransform-class"></a>Transformace XSLT pomocí XslTransform – třída
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Můžete provést jazyk XSL pro transformace transformace XSLT () pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy. V tématu [pomocí třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.  
  
 Cílem XSLT je k transformaci obsah zdrojový dokument XML do jiného dokumentu, který se liší ve formátu nebo strukturu (například transformace XML do kódu HTML k použití na webu a transformují je na dokument, který obsahuje pouze pole požadované b y aplikace). Tento proces transformace je zadána v www.w3.org/TR/xslt doporučení XSLT World Wide Web Consortium (W3C) verze 1.0. V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], <xref:System.Xml.Xsl.XslTransform> nalezena v třída <xref:System.Xml.Xsl> obor názvů, je procesor XSLT, která implementuje funkce této specifikace. Existuje malé množství funkcí, které nejsou implementované z doporučení W3C XSLT 1.0, uvedené v [výstupy z XslTransform](../../../../docs/standard/data/xml/outputs-from-an-xsltransform.md). Následující obrázek znázorňuje architekturu transformace [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
## <a name="overview"></a>Přehled  
 ![Architektura transformace XSLT](../../../../docs/standard/data/xml/media/xslttransformationswithxsltransformclass.gif "xsltTransformationsWithXslTransformClass")  
Architektura transformace  
  
 Doporučení XSLT použije k výběru části dokumentu XML, kde XPath je dotazovací jazyk použít pro účely navigace uzlů ve stromu dokumentu XML Path Language (XPath). Jak je znázorněno na obrázku [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] implementace XPath slouží k výběru částí XML uložené v několik tříd, jako například <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument>a <xref:System.Xml.XPath.XPathDocument>. <xref:System.Xml.XPath.XPathDocument> Je optimalizované XSLT datové úložiště a pokud se používá s <xref:System.Xml.Xsl.XslTransform>, poskytuje transformace XSLT pomocí dobrý výkon.  
  
 Následující seznam tabulek běžně používá třídy při práci s <xref:System.Xml.Xsl.XslTransform> a XPath a jejich funkce.  
  
|Třídy nebo rozhraní|Funkce|  
|------------------------|--------------|  
|<xref:System.Xml.XPath.XPathNavigator>|Je rozhraní API, které poskytuje model styl kurzor pro navigaci přes úložiště, společně s podporou dotaz XPath. Neposkytuje úpravy základní úložiště. Pro úpravy, použijte <xref:System.Xml.XmlDocument> třídy.|  
|<xref:System.Xml.XPath.IXPathNavigable>|Je rozhraní, které poskytuje `CreateNavigator` metodu <xref:System.Xml.XPath.XPathNavigator> pro úložiště.|  
|<xref:System.Xml.XmlDocument>|Umožňuje úpravy tohoto dokumentu. Implementuje <xref:System.Xml.XPath.IXPathNavigable>, povolení úprav dokumentu scénáře, kde jsou následně vyžadovány transformace XSLT. Další informace najdete v tématu [třídou XMLDocument nastavenou na vstup XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md).|  
|<xref:System.Xml.XmlDataDocument>|Je odvozený od <xref:System.Xml.XmlDocument>. Přemosťuje relační a světů XML pomocí <xref:System.Data.DataSet> za účelem optimalizace ukládání strukturovaných dat v dokumentu XML podle zadaného mapování na <xref:System.Data.DataSet>. Implementuje <xref:System.Xml.XPath.IXPathNavigable>, umožňuje scénáře, kde lze provádět transformace XSLT přes relační data načtená z databáze. Další informace najdete v tématu [XML integrace s relačních dat a ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md).|  
|<xref:System.Xml.XPath.XPathDocument>|Tato třída je optimalizována pro <xref:System.Xml.Xsl.XslTransform> zpracování a dotazů XPath a poskytuje mezipaměť jen pro čtení vysoký výkon. Implementuje <xref:System.Xml.XPath.IXPathNavigable> a je upřednostňovaný úložiště, které chcete použít pro transformace XSLT.|  
|<xref:System.Xml.XPath.XPathNodeIterator>|Zajišťuje navigace v uzlu sady XPath. Všechny metody výběru XPath na <xref:System.Xml.XPath.XPathNavigator> vrátit <xref:System.Xml.XPath.XPathNodeIterator>. Více <xref:System.Xml.XPath.XPathNodeIterator> objekty mohou být vytvořeny přes stejné úložiště, každý představuje vybrané sada uzlů.|  
  
## <a name="msxml-xslt-extensions"></a>Rozšíření MSXML XSLT  
 `msxsl:script` a `msxsl:node-set` funkce se podporuje jenom rozšíření XSLT Microsoft XML Core Services (MSXML) <xref:System.Xml.Xsl.XslTransform> třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu načte stylů XSLT, přečte soubor s názvem data.XML do <xref:System.Xml.XPath.XPathDocument>a provádí transformaci dat na smyšlené soubor s názvem myStyleSheet.xsl, odesílání formátovaný výstup do konzoly.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Xsl.XslTransform>  
 [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
 [Implementace volitelného chování ve třídě XslTransform](../../../../docs/standard/data/xml/implementation-of-discretionary-behaviors-in-the-xsltransform-class.md)  
 [XPathNavigator v transformacích](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [XPathNodeIterator v transformacích](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [Vstup XPathDocument do XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [Vstup XmlDataDocument do XslTransform](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
 [Vstup XmlDocument do XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
