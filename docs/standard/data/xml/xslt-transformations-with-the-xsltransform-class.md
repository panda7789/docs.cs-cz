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
# <a name="xslt-transformations-with-the-xsltransform-class"></a>Transformace XSLT s třídou XslTransform

> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá v .NET Framework 2,0. Transformace XSLT (Extensible Stylesheet Language) můžete použít k <xref:System.Xml.Xsl.XslCompiledTransform> transformaci pomocí třídy. Další informace najdete v tématu [použití třídy XslCompiledTransform](using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](migrating-from-the-xsltransform-class.md) .

Cílem XSLT je převést obsah zdrojového dokumentu XML do jiného dokumentu, který je odlišný ve formátu nebo struktuře (například pro transformaci XML na HTML pro použití na webu nebo k jeho transformaci na dokument, který obsahuje pouze pole požadovaná aplikací). Tento proces transformace je určen[doporučením XSLT verze 1,0](https://www.w3.org/TR/1999/REC-xslt-19991116)pro konsorcium World Wide Web (W3C). V .NET Framework <xref:System.Xml.Xsl.XslTransform> třída, která je nalezena v <xref:System.Xml.Xsl> oboru názvů, je procesor XSLT, který implementuje funkce této specifikace. Existuje malý počet funkcí, které nebyly implementovány z doporučení W3C XSLT 1,0 uvedených v části [výstupy z XslTransform](outputs-from-an-xsltransform.md). Následující obrázek ukazuje architekturu transformace .NET Framework.

## <a name="overview"></a>Přehled

![Diagram znázorňující architekturu transformace XSLT.](./media/xslt-transformations-with-the-xsltransform-class/xslt-transformation-architecture.gif)

Doporučení XSLT používá jazyk XML Path (XPath) pro výběr částí dokumentu XML, kde XPath je dotazovací jazyk, který slouží k navigaci uzlů stromu dokumentu. Jak je znázorněno v diagramu, .NET Framework implementace XPath slouží k výběru částí jazyka XML uložených v několika třídách, například <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument>a. <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XPath.XPathDocument> Je optimalizované úložiště dat XSLT a při použití s nástrojem <xref:System.Xml.Xsl.XslTransform>poskytuje transformace XSLT s dobrým výkonem.

Následující tabulka často používá třídy při práci s <xref:System.Xml.Xsl.XslTransform> a XPath a jejich funkci.

|Třída nebo rozhraní|Funkce|
|------------------------|--------------|
|<xref:System.Xml.XPath.XPathNavigator>|Je to rozhraní API, které poskytuje model stylu kurzoru pro navigaci přes obchod spolu s podporou dotazů XPath. Neposkytuje úpravy základního úložiště. Pro úpravy použijte <xref:System.Xml.XmlDocument> třídu.|
|<xref:System.Xml.XPath.IXPathNavigable>|Jedná se o rozhraní, které poskytuje `CreateNavigator` metodu <xref:System.Xml.XPath.XPathNavigator> pro úložiště.|
|<xref:System.Xml.XmlDocument>|Umožňuje úpravy tohoto dokumentu. Implementuje <xref:System.Xml.XPath.IXPathNavigable>a povoluje scénáře úprav dokumentů, kde jsou následně požadovány transformace XSLT. Další informace najdete v tématu [vstupní hodnoty XmlDocument pro XslTransform](xmldocument-input-to-xsltransform.md).|
|<xref:System.Xml.XmlDataDocument>|Je odvozen z <xref:System.Xml.XmlDocument>. Předává relační a XML světů pomocí a <xref:System.Data.DataSet> k optimalizaci úložiště strukturovaných dat v rámci dokumentu XML podle zadaných mapování v. <xref:System.Data.DataSet> Implementuje <xref:System.Xml.XPath.IXPathNavigable>a povoluje scénáře, kde lze provádět transformace XSLT prostřednictvím relačních dat načtených z databáze. Další informace najdete v tématu [integrace XML s relačními daty a ADO.NET](xml-integration-with-relational-data-and-adonet.md).|
|<xref:System.Xml.XPath.XPathDocument>|Tato třída je optimalizována <xref:System.Xml.Xsl.XslTransform> pro zpracování a dotazy XPath a poskytuje mezipaměť s vysokým výkonem jen pro čtení. Implementuje <xref:System.Xml.XPath.IXPathNavigable> a je preferovaným úložištěm, které se má použít pro transformace XSLT.|
|<xref:System.Xml.XPath.XPathNodeIterator>|Poskytuje navigaci nad sadami uzlů XPath. Všechny metody výběru XPath při <xref:System.Xml.XPath.XPathNavigator> vrácení. <xref:System.Xml.XPath.XPathNodeIterator> V <xref:System.Xml.XPath.XPathNodeIterator> rámci stejného úložiště lze vytvořit více objektů, z nichž každý představuje vybranou sadu uzlů.|

## <a name="msxml-xslt-extensions"></a>Rozšíření MSXML XSLT

Funkce `msxsl:script` a `msxsl:node-set` jsou jediná rozšíření XSLT služby Microsoft XML Core Services (MSXML), která <xref:System.Xml.Xsl.XslTransform> třída podporuje.

## <a name="example"></a>Příklad

Následující příklad kódu načte šablonu stylů XSLT, přečte soubor s názvem Mojedata. XML do <xref:System.Xml.XPath.XPathDocument>a a provede transformaci dat v fiktivním souboru s názvem MyStylesheet. XSL, který odesílá formátovaný výstup do konzoly.

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

## <a name="see-also"></a>Viz také

- <xref:System.Xml.Xsl.XslTransform>
- [Třída XslTransform implementuje procesor XSLT](xsltransform-class-implements-the-xslt-processor.md)
- [Implementace volitelného chování ve třídě XslTransform](implementation-of-discretionary-behaviors-in-the-xsltransform-class.md)
- [XPathNavigator v transformacích](xpathnavigator-in-transformations.md)
- [XPathNodeIterator v transformacích](xpathnodeiterator-in-transformations.md)
- [Vstup XPathDocument do XslTransform](xpathdocument-input-to-xsltransform.md)
- [Vstup XmlDataDocument do XslTransform](xmldatadocument-input-to-xsltransform.md)
- [Vstup XmlDocument do XslTransform](xmldocument-input-to-xsltransform.md)
