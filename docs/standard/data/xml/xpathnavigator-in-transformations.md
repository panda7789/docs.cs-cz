---
title: XPathNavigator v transformacích
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 118f97d1-7110-4d1b-b0bd-4143252c0bb0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57290af1df8d370c928a97aba1622e41a6a33589
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45519429"
---
# <a name="xpathnavigator-in-transformations"></a>XPathNavigator v transformacích
<xref:System.Xml.XPath.XPathNavigator> Třída poskytuje náhodný přístup jen pro čtení k datům a je určený pro použití jako vstup do šablony stylů jazyk pro transformace XSLT (). Je implementován v <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDataDocument>, a <xref:System.Xml.XmlDocument>. <xref:System.Xml.XPath.XPathNavigator> Je založena na datovém modelu World Wide Web Consortium (W3C), jak je popsáno v části 5 doporučení jazyk XML Path (XPath).  
  
 <xref:System.Xml.XPath.XPathNavigator> Definuje model kurzoru nad jakékoli úložiště a poskytuje rychlý a jen pro čtení dotazy XPath přes jakékoli úložiště dat. <xref:System.Xml.XPath.XPathNavigator> Je také třída pro iterace přes fragmenty stromu výsledek.  
  
 Rozhraní API umožňuje získat informace z aktuálního uzlu v úložišti a přesunout do propojených uzlů. <xref:System.Xml.XPath.XPathNavigator> Je model styl kurzor, který provádí přechod zálohovaných store pomocí sady **přesunout** metody. <xref:System.Xml.XPath.XPathNavigator> Vždy je umístěn na uzlu. Žádné **přesunout** metody, které se nedaří listy <xref:System.Xml.XPath.XPathNavigator> beze změny.  
  
 <xref:System.Xml.XPath.XPathNavigator> Je třída pro iterace přes fragmenty stromu výsledek. Následující vzorový kód vytvoří fragment stromu výsledek předloze se styly voláním funkce s parametrem `fragment`, který obsahuje XML.  
  
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
 Výsledek transformace se nachází v souboru **out.xml**:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>Joe  
```  
  
## <a name="see-also"></a>Viz také:

- [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
