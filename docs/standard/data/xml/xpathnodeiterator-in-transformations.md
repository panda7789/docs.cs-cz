---
title: XPathNodeIterator v transformacích
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2bc6ddc6-674a-4f75-b264-abc35e4e5857
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6f71d409729707f4af93fd7f8d5b82a99404579b
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44270890"
---
# <a name="xpathnodeiterator-in-transformations"></a>XPathNodeIterator v transformacích
<xref:System.Xml.XPath.XPathNodeIterator> Poskytuje metody k iteraci v rámci sady uzlů, které jsou vytvořené jako výsledek dotazu jazyk XML Path (XPath) nebo fragment stromu výsledek převeden na uzlu nastavte pomocí metody sada uzlů. <xref:System.Xml.XPath.XPathNodeIterator> Umožňuje iterovat přes uzly v rámci této sady uzlu. Jakmile se načte sadu uzlu, <xref:System.Xml.XPath.XPathNodeIterator> třída poskytuje jen pro čtení, dopředné kurzoru vybrané sady uzlů. Sada uzlů je vytvořen v pořadí dokumentů, takže volání této metody přesune na další uzel v pořadí dokumentů. <xref:System.Xml.XPath.XPathNodeIterator> uzel stromu všech uzlů v sadě nesestaví. Místo toho poskytuje okno s jedním uzlem data, odhalují základní uzel, na který odkazuje na při pohybu ve stromové struktuře. Metody a vlastnosti, které jsou k dispozici <xref:System.Xml.XPath.XPathNodeIterator> třídy umožňují získat informace z aktuálního uzlu. Seznam dostupných metod a vlastností najdete v tématu <xref:System.Windows.Forms.ToolBar>.  
  
 Protože <xref:System.Xml.XPath.XPathNodeIterator> přejde v rámci sady uzlů vytvořené z dotazu XPath a přesune pouze vpřed, je způsob, jak přesunout pomocí <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> metody. Návratový typ této metody je `Boolean`, vracející `true` Pokud je přesune k dalšímu vybraného uzlu, a `false` Pokud neexistují žádné další vybrané uzly. Vrátí-li `true`, v následujícím seznamu jsou uvedeny dostupné vlastnosti:  
  
-   <xref:System.Xml.XPath.XPathNodeIterator.Current%2A>  
  
-   <xref:System.Xml.XPath.XPathNodeIterator.CurrentPosition%2A>  
  
-   <xref:System.Xml.XPath.XPathNodeIterator.Count%2A>  
  
 Při hledání v uzlu nastavení při prvním volání <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> třeba umístit <xref:System.Xml.XPath.XPathNodeIterator> na prvním uzlu vybrané sady. To umožňuje nějakou smyčku, která má být proveden zápis.  
  
 Následující příklad kódu ukazuje, jak předat <xref:System.Xml.XPath.XPathNodeIterator> do <xref:System.Xml.Xsl.XslTransform> jako parametr v <xref:System.Xml.Xsl.XsltArgumentList>. Vstup do kódu je **books.xml**, a šablona stylů je **text.xsl**. Soubor **test.xml** je <xref:System.Xml.XPath.XPathDocument>.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.Xsl  
Imports System.Xml.XPath  
Imports System.Text  
  
Public Class sample  
  
   Public Shared Sub Main()  
      Dim Doc As New XPathDocument("books.xml")  
      Dim nav As XPathNavigator = Doc.CreateNavigator()  
      Dim Iterator As XPathNodeIterator = nav.Select("/bookstore/book")  
  
      Dim arg As New XsltArgumentList()  
      arg.AddParam("param1", "", Iterator)  
  
      Dim xslt As New XslTransform()  
      xslt.Load("test.xsl")  
  
      Dim xd As New XPathDocument("test.xml")  
  
      Dim strmTemp = New FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite)  
      xslt.Transform(xd, arg, strmTemp, Nothing)  
   End Sub 'Main  
End Class 'sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.Xsl;  
using System.Xml.XPath;  
using System.Text;  
  
public class sample  
{  
    public static void Main()  
    {  
        XPathDocument Doc = new XPathDocument("books.xml");  
        XPathNavigator nav = Doc.CreateNavigator();  
        XPathNodeIterator Iterator = nav.Select("/bookstore/book");  
  
        XsltArgumentList arg = new XsltArgumentList();  
        arg.AddParam("param1", "", Iterator);  
  
        XslTransform xslt = new XslTransform();  
        xslt.Load("test.xsl");  
  
        XPathDocument xd = new XPathDocument("test.xml");  
  
        Stream strmTemp = new FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite);  
        xslt.Transform(xd, arg, strmTemp, null);  
    }  
}  
```  
  
## <a name="booksxml"></a>Books.XML  
  
```xml  
<?xml version='1.0'?>  
<!-- This file represents a fragment of a book store inventory database. -->  
<bookstore specialty="novel">  
    <book style="autobiography">  
    <title>Seven Years in Trenton</title>  
        <author>  
            <first-name>Jay</first-name>  
            <last-name>Adams</last-name>  
            <award>Trenton Literary Review Honorable Mention</award>  
            <country>USA</country>  
        </author>  
        <price>12</price>  
    </book>  
    <book style="textbook">  
        <title>History of Trenton</title>  
        <author>  
            <first-name>Kim</first-name>  
            <last-name>Akers</last-name>  
            <publication>  
                Selected Short Stories of  
                <first-name>Scott</first-name>  
                <last-name>Bishop</last-name>  
                <country>US</country>  
            </publication>  
        </author>  
        <price>55</price>  
    </book>  
</bookstore>  
```  
  
## <a name="testxsl"></a>test.xsl  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
xmlns:msxsl="urn:schemas-microsoft-com:xslt" exclude-result-prefixes="msxsl">  
  
<xsl:output method="xml" indent="yes"/>  
<xsl:param name="param1"/>  
  
<xsl:template match="/">  
    <out>  
        <xsl:for-each select="$param1/title">  
            <title><xsl:value-of select="."/></title>  
        </xsl:for-each>  
    </out>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
## <a name="testxml"></a>test.XML  
  
```xml  
<Title attr="Test">this is a test</Title>  
```  
  
## <a name="output-outxml"></a>Výstup (out.xml)  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<out>  
  <title>Seven Years in Trenton</title>  
  <title>History of Trenton</title>  
</out>  
```  
  
## <a name="see-also"></a>Viz také:

- [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
