---
title: XPathNodeIterator v transformace
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2bc6ddc6-674a-4f75-b264-abc35e4e5857
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0d30760ef018c9b2d1264b323b57172417e4ef0c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571321"
---
# <a name="xpathnodeiterator-in-transformations"></a>XPathNodeIterator v transformace
<xref:System.Xml.XPath.XPathNodeIterator> Poskytuje metody k iteraci v rámci sady uzlů vytvořené v důsledku dotaz XML Path Language (XPath) nebo fragment stromu výsledek převést na uzlu nastavte pomocí metody sada uzlů. <xref:System.Xml.XPath.XPathNodeIterator> Umožňuje iterovat uzlů v rámci dané sadě uzlu. Jakmile se načte sada uzlů, <xref:System.Xml.XPath.XPathNodeIterator> třída poskytuje jen pro čtení, dopředné kurzoru vybrané sada uzlů. Sada uzlů se vytvoří v pořadí dokumentů, voláním této metody přesune na další uzel v pořadí dokumentů. <xref:System.Xml.XPath.XPathNodeIterator> Nelze sestavit uzlu stromu všech uzlů v sadě. Namísto toho poskytuje okno jednoho uzlu do data vystavení základní uzlu, na který odkazuje jako pohyb ve stromové struktuře. Metody a vlastnosti, které jsou dostupné na <xref:System.Xml.XPath.XPathNodeIterator> třída umožňují získat informace z aktuálního uzlu. Seznam dostupných metod a vlastností, najdete v tématu <xref:System.Windows.Forms.ToolBar>.  
  
 Protože <xref:System.Xml.XPath.XPathNodeIterator> přesune přes sada uzlů vytvořené z dotaz XPath a přejde vpřed pouze, je způsob, jak přesunout pomocí <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> metoda. Návratový typ této metody `Boolean`, vracejících `true` pokud ji přesune na další vybraný uzel, a `false` Pokud neexistují žádné další vybrané uzly. Vrátí-li `true`, v následujícím seznamu jsou dostupné vlastnosti:  
  
-   <xref:System.Xml.XPath.XPathNodeIterator.Current%2A>  
  
-   <xref:System.Xml.XPath.XPathNodeIterator.CurrentPosition%2A>  
  
-   <xref:System.Xml.XPath.XPathNodeIterator.Count%2A>  
  
 Při hledání v uzlu nastavení při prvním volání <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> musí být provedeny na pozici <xref:System.Xml.XPath.XPathNodeIterator> na prvním uzlu vybrané sady. To umožňuje chvíli smyčky k zapsání.  
  
 Následující příklad kódu ukazuje, jak předat <xref:System.Xml.XPath.XPathNodeIterator> k <xref:System.Xml.Xsl.XslTransform> jako parametr v <xref:System.Xml.Xsl.XsltArgumentList>. Vstup kód je **books.xml**, a je šablony stylů **text.xsl**. Soubor **test.xml** je <xref:System.Xml.XPath.XPathDocument>.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
