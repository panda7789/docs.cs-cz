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
# <a name="xslt-transformations-with-the-xsltransform-class"></a>Transformace XSLT s třídou XslTransform

> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Můžete provádět rozšiřitelný jazyk šablony stylů transformace XSLT () transformaci pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy. Zobrazit [používání třídy XslCompiledTransform](using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](migrating-from-the-xsltransform-class.md) Další informace.

Cílem XSLT je transformace do jiného dokumentu, který se liší ve formátu nebo strukturu (například pro transformaci XML do kódu HTML k použití na webové stránce nebo k transformaci do dokumentu, který obsahuje pouze požadovaná b pole obsahu zdrojovém dokumentu XML y aplikace). Tento proces transformace je určená World Wide Web Consortium (W3C)[XSLT verze 1.0 doporučení](https://www.w3.org/TR/1999/REC-xslt-19991116). V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], <xref:System.Xml.Xsl.XslTransform> třída součástí <xref:System.Xml.Xsl> je obor názvů, procesoru XSLT, který implementuje funkce téhle specifikaci. Malý počet funkcí, které nejsou implementované v doporučení W3C XSLT 1.0, uvedené v [výstupy z XslTransform](outputs-from-an-xsltransform.md). Následující obrázek ukazuje architekturu transformace [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].

## <a name="overview"></a>Přehled

![Architektura transformace XSLT](media/xslttransformationswithxsltransformclass.gif "xsltTransformationsWithXslTransformClass")  
Architektura transformace

Doporučení XSLT používá jazyk XML Path (XPath) pro výběr součástí dokumentu XML, pokud výraz XPath je dotazovací jazyk pro pohyb mezi uzly stromu dokumentu. Jak je znázorněno na diagramu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] implementace XPath slouží k výběru součástí jazyka XML uložené v několik tříd, jako například <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument>a <xref:System.Xml.XPath.XPathDocument>. <xref:System.Xml.XPath.XPathDocument> Je optimalizované XSLT datové úložiště a při použití s <xref:System.Xml.Xsl.XslTransform>, poskytuje transformace XSLT s dobrého výkonu.

V následujícím seznamu tabulku běžně používá třídy při práci s <xref:System.Xml.Xsl.XslTransform> a XPath a jejich funkce.

|Třída nebo rozhraní|Funkce|
|------------------------|--------------|
|<xref:System.Xml.XPath.XPathNavigator>|Je rozhraní API, které poskytuje model styl kurzoru pro navigaci v úložišti, společně s podporou dotaz XPath. Neposkytuje úpravy základní úložiště. Pro úpravy, použijte <xref:System.Xml.XmlDocument> třídy.|
|<xref:System.Xml.XPath.IXPathNavigable>|Je rozhraní, které poskytuje `CreateNavigator` metodu <xref:System.Xml.XPath.XPathNavigator> pro úložiště.|
|<xref:System.Xml.XmlDocument>|Umožňuje úpravy tohoto dokumentu. Implementuje <xref:System.Xml.XPath.IXPathNavigable>, umožňující úpravy dokumentu scénáře, kde se následně vyžadují transformace XSLT. Další informace najdete v tématu [vstup XmlDocument do XslTransform](xmldocument-input-to-xsltransform.md).|
|<xref:System.Xml.XmlDataDocument>|Je odvozen z <xref:System.Xml.XmlDocument>. Překlenuje relační a světů XML pomocí <xref:System.Data.DataSet> pro optimalizaci úložiště strukturovaných dat v dokumentu XML podle zadaného mapování na <xref:System.Data.DataSet>. Implementuje <xref:System.Xml.XPath.IXPathNavigable>, umožňuje scénáře, kde lze provádět transformace XSLT nad relační data načtená z databáze. Další informace najdete v tématu [integrace XML s relačními daty a ADO.NET](xml-integration-with-relational-data-and-adonet.md).|
|<xref:System.Xml.XPath.XPathDocument>|Tato třída je optimalizována pro <xref:System.Xml.Xsl.XslTransform> zpracování a dotazů XPath a poskytuje jen pro čtení vysoký výkon mezipaměti. Implementuje <xref:System.Xml.XPath.IXPathNavigable> a je upřednostňovaný úložiště pro transformace XSLT.|
|<xref:System.Xml.XPath.XPathNodeIterator>|Poskytuje navigace prostřednictvím sady uzlu XPath. Všechny metody výběr XPath <xref:System.Xml.XPath.XPathNavigator> vrátit <xref:System.Xml.XPath.XPathNodeIterator>. Více <xref:System.Xml.XPath.XPathNodeIterator> objekty mohou být vytvořeny prostřednictvím stejné úložiště, ve nichž každý představuje vybrané sady uzlů.|

## <a name="msxml-xslt-extensions"></a>Rozšíření MSXML XSLT

`msxsl:script` a `msxsl:node-set` funkce jsou pouze rozšíření XSLT Microsoft XML Core Services (MSXML) podporuje <xref:System.Xml.Xsl.XslTransform> třídy.

## <a name="example"></a>Příklad

Následující příklad kódu načte šablony stylů XSLT, načte soubor s názvem data.XML do <xref:System.Xml.XPath.XPathDocument>a provede transformaci na data na fiktivní soubor s názvem myStyleSheet.xsl odesílání formátovaný výstup do konzoly.

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

## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Xsl.XslTransform>  
- [Třída XslTransform implementuje procesor XSLT](xsltransform-class-implements-the-xslt-processor.md)  
- [Implementace volitelného chování ve třídě XslTransform](implementation-of-discretionary-behaviors-in-the-xsltransform-class.md)  
- [XPathNavigator v transformacích](xpathnavigator-in-transformations.md)  
- [XPathNodeIterator v transformacích](xpathnodeiterator-in-transformations.md)  
- [Vstup XPathDocument do XslTransform](xpathdocument-input-to-xsltransform.md)  
- [Vstup XmlDataDocument do XslTransform](xmldatadocument-input-to-xsltransform.md)  
- [Vstup XmlDocument do XslTransform](xmldocument-input-to-xsltransform.md)  
