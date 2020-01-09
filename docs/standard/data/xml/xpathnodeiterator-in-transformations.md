---
title: XPathNodeIterator v transformacích
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2bc6ddc6-674a-4f75-b264-abc35e4e5857
ms.openlocfilehash: 63beeb3ca9d3f3cb6e6bde418e99ee2bd0a12e20
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709735"
---
# <a name="xpathnodeiterator-in-transformations"></a>XPathNodeIterator v transformacích
<xref:System.Xml.XPath.XPathNodeIterator> poskytuje metody pro iterování v rámci sady uzlů vytvořených jako výsledek dotazu jazyka XML Path (XPath) nebo fragmentu stromu výsledku převedený na uzel, který používá metodu sady uzlů. <xref:System.Xml.XPath.XPathNodeIterator> umožňuje iterovat uzly v rámci této sady uzlů. Po načtení sady uzlů poskytuje třída <xref:System.Xml.XPath.XPathNodeIterator> pouze kurzor, který je jen pro čtení, do vybrané sady uzlů. Sada uzlů je vytvořena v pořadí dokumentů, takže volání této metody se přesune na další uzel v pořadí dokumentů. <xref:System.Xml.XPath.XPathNodeIterator> nevytváří strom uzlů všech uzlů v sadě. Místo toho poskytuje jedno okno s jedním uzlem na data a zveřejňuje základní uzel, na který směřuje při přesunu ve stromu. Metody a vlastnosti, které jsou k dispozici z <xref:System.Xml.XPath.XPathNodeIterator> třídy, umožňují získat informace z aktuálního uzlu. Seznam dostupných metod a vlastností naleznete v tématu <xref:System.Windows.Forms.ToolBar>.  
  
 Vzhledem k tomu, že se <xref:System.Xml.XPath.XPathNodeIterator> přesune přes sadu uzlů vytvořených z dotazu XPath a přesune se pouze vpřed, způsob přesunutí je pomocí metody <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A>. Návratový typ této metody je `Boolean`, vrácení `true`, pokud se přesune k dalšímu vybranému uzlu, a `false`, pokud neexistují žádné další vybrané uzly. Pokud vrátí `true`, zobrazí se v následujícím seznamu vlastnosti, které jsou k dispozici:  
  
- <xref:System.Xml.XPath.XPathNodeIterator.Current%2A>  
  
- <xref:System.Xml.XPath.XPathNodeIterator.CurrentPosition%2A>  
  
- <xref:System.Xml.XPath.XPathNodeIterator.Count%2A>  
  
 Při prvním pohledu na uzel, který je nastaven poprvé, musí být provedeno volání <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> pro umístění <xref:System.Xml.XPath.XPathNodeIterator> na prvním uzlu vybrané sady. To umožňuje zapsat smyčku while.  
  
 Následující příklad kódu ukazuje, jak předat <xref:System.Xml.XPath.XPathNodeIterator> do <xref:System.Xml.Xsl.XslTransform> jako parametr v <xref:System.Xml.Xsl.XsltArgumentList>. Vstup do kódu je **Books. XML**a předloha se styly je **text. xsl**. Soubor **test. XML** je <xref:System.Xml.XPath.XPathDocument>.  
  
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
  
## <a name="booksxml"></a>Books. XML  
  
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
  
## <a name="testxsl"></a>test. xsl  
  
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
  
## <a name="testxml"></a>test. XML  
  
```xml  
<Title attr="Test">this is a test</Title>  
```  
  
## <a name="output-outxml"></a>Výstup (out. XML)  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<out>  
  <title>Seven Years in Trenton</title>  
  <title>History of Trenton</title>  
</out>  
```  
  
## <a name="see-also"></a>Viz také:

- [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
