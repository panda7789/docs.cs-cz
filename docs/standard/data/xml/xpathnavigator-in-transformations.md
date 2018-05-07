---
title: Objektem XPathNavigator nastaveným v transformace
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 118f97d1-7110-4d1b-b0bd-4143252c0bb0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 76cfa51c7d434a6dfdcdc1e6852779decaa601e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="xpathnavigator-in-transformations"></a>Objektem XPathNavigator nastaveným v transformace
<xref:System.Xml.XPath.XPathNavigator> Třída poskytuje náhodný přístup jen pro čtení k datům a je určená pro použití jako vstup pro jazyk XSL pro transformace XSLT (). Se implementuje na <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDataDocument>, a <xref:System.Xml.XmlDocument>. <xref:System.Xml.XPath.XPathNavigator> Je založena na datový Model World Wide Web Consortium (W3C), jak je popsáno v části 5 doporučení XML Path Language (XPath).  
  
 <xref:System.Xml.XPath.XPathNavigator> Definuje model kurzoru přes jakékoli úložiště a nabízí v porovnání s jakékoli úložiště dat rychlé, jen pro čtení dotazů XPath. <xref:System.Xml.XPath.XPathNavigator> Je také třída pro iterování přes fragmenty stromu výsledek.  
  
 Rozhraní API umožňuje získat informace z aktuálního uzlu v úložišti a přesunout do připojených uzlů. <xref:System.Xml.XPath.XPathNavigator> Je model styl kurzor, který provádí traversal přes do úložiště pomocí sadu **přesunout** metody. <xref:System.Xml.XPath.XPathNavigator> Je vždycky nastavený na uzlu. Všechny **přesunout** metoda, který selže nechá <xref:System.Xml.XPath.XPathNavigator> beze změny.  
  
 <xref:System.Xml.XPath.XPathNavigator> Je třída, která chcete použít pro iterování přes fragmenty stromu výsledek. Následující příklad kódu vytvoří fragment výsledek stromové struktury v rámci šablony stylů voláním funkce s parametrem `fragment`, který obsahuje XML.  
  
## <a name="testxsl"></a>test.xsl  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl ="urn:schemas-microsoft-com:xslt"  
                xmlns:user="http://www.adventure-works.com"  
                version="1.0">  
  
<xsl:variable name="fragment">  
    <authorlist>  
       <author>Joe</author>  
    </authorlist>  
</xsl:variable>  
  
<msxsl:script language="C#" implements-prefix="user">  
<![CDATA[  
   string NodeFragment(XPathNavigator nav)  
   {  
      if (nav.HasChildren)  
        return nav.Value;  
      else  
        return "";  
   }  
]]>  
</msxsl:script>  
  
<xsl:template match="/">  
     <xsl:value-of select="user:NodeFragment($fragment)"/>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
## <a name="testxml"></a>test.XML  
  
```xml  
<root>Some text</root>  
```  
  
 Následující kód používá **test.xsl** šablony stylů a **test.xml** vstupní data.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.Xsl  
Imports System.Xml.XPath  
Imports System.Text  
Public Class sample  
  
    Public Shared Sub Main()  
        Dim xslt As New XslTransform()  
        xslt.Load("test.xsl")  
  
        Dim xd As New XPathDocument("test.xml")  
  
        Dim strmTemp = New FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite)  
        xslt.Transform(xd, Nothing, strmTemp, Nothing)  
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
        XslTransform xslt = new XslTransform();  
        xslt.Load("test.xsl");  
  
        XPathDocument xd = new XPathDocument("test.xml");  
  
        Stream strmTemp = new FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite);  
        xslt.Transform(xd, null, strmTemp, null);  
    }  
}  
```  
  
## <a name="output"></a>Výstup  
 Výsledek transformace se nacházejí v souboru **out.xml**:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>Joe  
```  
  
## <a name="see-also"></a>Viz také  
 [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
