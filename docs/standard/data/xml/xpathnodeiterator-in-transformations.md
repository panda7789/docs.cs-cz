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
# <a name="xpathnodeiterator-in-transformations"></a><span data-ttu-id="f05c3-102">XPathNodeIterator v transformacích</span><span class="sxs-lookup"><span data-stu-id="f05c3-102">XPathNodeIterator in Transformations</span></span>
<span data-ttu-id="f05c3-103"><xref:System.Xml.XPath.XPathNodeIterator> poskytuje metody pro iterování v rámci sady uzlů vytvořených jako výsledek dotazu jazyka XML Path (XPath) nebo fragmentu stromu výsledku převedený na uzel, který používá metodu sady uzlů.</span><span class="sxs-lookup"><span data-stu-id="f05c3-103">The <xref:System.Xml.XPath.XPathNodeIterator> provides methods to iterate over a set of nodes created as the result of an XML Path Language (XPath) query or a result tree fragment converted to a node set by use of the node-set method.</span></span> <span data-ttu-id="f05c3-104"><xref:System.Xml.XPath.XPathNodeIterator> umožňuje iterovat uzly v rámci této sady uzlů.</span><span class="sxs-lookup"><span data-stu-id="f05c3-104">The <xref:System.Xml.XPath.XPathNodeIterator> enables you to iterate over the nodes within that node set.</span></span> <span data-ttu-id="f05c3-105">Po načtení sady uzlů poskytuje třída <xref:System.Xml.XPath.XPathNodeIterator> pouze kurzor, který je jen pro čtení, do vybrané sady uzlů.</span><span class="sxs-lookup"><span data-stu-id="f05c3-105">Once a node set is retrieved, the <xref:System.Xml.XPath.XPathNodeIterator> class provides a read-only, forward-only cursor to the selected set of nodes.</span></span> <span data-ttu-id="f05c3-106">Sada uzlů je vytvořena v pořadí dokumentů, takže volání této metody se přesune na další uzel v pořadí dokumentů.</span><span class="sxs-lookup"><span data-stu-id="f05c3-106">The node set is created in document order, so calling this method moves to the next node in document order.</span></span> <span data-ttu-id="f05c3-107"><xref:System.Xml.XPath.XPathNodeIterator> nevytváří strom uzlů všech uzlů v sadě.</span><span class="sxs-lookup"><span data-stu-id="f05c3-107"><xref:System.Xml.XPath.XPathNodeIterator> does not build a node tree of all the nodes in the set.</span></span> <span data-ttu-id="f05c3-108">Místo toho poskytuje jedno okno s jedním uzlem na data a zveřejňuje základní uzel, na který směřuje při přesunu ve stromu.</span><span class="sxs-lookup"><span data-stu-id="f05c3-108">Instead, it provides a single node window into the data, exposing the underlying node it points to as you move around in the tree.</span></span> <span data-ttu-id="f05c3-109">Metody a vlastnosti, které jsou k dispozici z <xref:System.Xml.XPath.XPathNodeIterator> třídy, umožňují získat informace z aktuálního uzlu.</span><span class="sxs-lookup"><span data-stu-id="f05c3-109">The methods and properties available from the <xref:System.Xml.XPath.XPathNodeIterator> class enable you to get information from the current node.</span></span> <span data-ttu-id="f05c3-110">Seznam dostupných metod a vlastností naleznete v tématu <xref:System.Windows.Forms.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="f05c3-110">For a list of the available methods and properties, see <xref:System.Windows.Forms.ToolBar>.</span></span>  
  
 <span data-ttu-id="f05c3-111">Vzhledem k tomu, že se <xref:System.Xml.XPath.XPathNodeIterator> přesune přes sadu uzlů vytvořených z dotazu XPath a přesune se pouze vpřed, způsob přesunutí je pomocí metody <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A>.</span><span class="sxs-lookup"><span data-stu-id="f05c3-111">Since an <xref:System.Xml.XPath.XPathNodeIterator> moves over a set of nodes created from an XPath query and moves forward only, the way to move is by using the <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> method.</span></span> <span data-ttu-id="f05c3-112">Návratový typ této metody je `Boolean`, vrácení `true`, pokud se přesune k dalšímu vybranému uzlu, a `false`, pokud neexistují žádné další vybrané uzly.</span><span class="sxs-lookup"><span data-stu-id="f05c3-112">The return type of this method is `Boolean`, returning `true` if it moves to the next selected node, and `false` if there are no more selected nodes.</span></span> <span data-ttu-id="f05c3-113">Pokud vrátí `true`, zobrazí se v následujícím seznamu vlastnosti, které jsou k dispozici:</span><span class="sxs-lookup"><span data-stu-id="f05c3-113">If it returns `true`, the following list shows the properties available:</span></span>  
  
- <xref:System.Xml.XPath.XPathNodeIterator.Current%2A>  
  
- <xref:System.Xml.XPath.XPathNodeIterator.CurrentPosition%2A>  
  
- <xref:System.Xml.XPath.XPathNodeIterator.Count%2A>  
  
 <span data-ttu-id="f05c3-114">Při prvním pohledu na uzel, který je nastaven poprvé, musí být provedeno volání <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> pro umístění <xref:System.Xml.XPath.XPathNodeIterator> na prvním uzlu vybrané sady.</span><span class="sxs-lookup"><span data-stu-id="f05c3-114">When you are looking at a node set for the first time, a call to <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> must be made to position the <xref:System.Xml.XPath.XPathNodeIterator> on the first node of the selected set.</span></span> <span data-ttu-id="f05c3-115">To umožňuje zapsat smyčku while.</span><span class="sxs-lookup"><span data-stu-id="f05c3-115">This allows a while loop to be written.</span></span>  
  
 <span data-ttu-id="f05c3-116">Následující příklad kódu ukazuje, jak předat <xref:System.Xml.XPath.XPathNodeIterator> do <xref:System.Xml.Xsl.XslTransform> jako parametr v <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="f05c3-116">The following code example shows how to pass an <xref:System.Xml.XPath.XPathNodeIterator> to an <xref:System.Xml.Xsl.XslTransform> as a parameter in the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span> <span data-ttu-id="f05c3-117">Vstup do kódu je **Books. XML**a předloha se styly je **text. xsl**.</span><span class="sxs-lookup"><span data-stu-id="f05c3-117">The input to the code is **books.xml**, and the style sheet is **text.xsl**.</span></span> <span data-ttu-id="f05c3-118">Soubor **test. XML** je <xref:System.Xml.XPath.XPathDocument>.</span><span class="sxs-lookup"><span data-stu-id="f05c3-118">The file **test.xml** is the <xref:System.Xml.XPath.XPathDocument>.</span></span>  
  
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
  
## <a name="booksxml"></a><span data-ttu-id="f05c3-119">Books. XML</span><span class="sxs-lookup"><span data-stu-id="f05c3-119">books.xml</span></span>  
  
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
  
## <a name="testxsl"></a><span data-ttu-id="f05c3-120">test. xsl</span><span class="sxs-lookup"><span data-stu-id="f05c3-120">test.xsl</span></span>  
  
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
  
## <a name="testxml"></a><span data-ttu-id="f05c3-121">test. XML</span><span class="sxs-lookup"><span data-stu-id="f05c3-121">test.xml</span></span>  
  
```xml  
<Title attr="Test">this is a test</Title>  
```  
  
## <a name="output-outxml"></a><span data-ttu-id="f05c3-122">Výstup (out. XML)</span><span class="sxs-lookup"><span data-stu-id="f05c3-122">Output (out.xml)</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<out>  
  <title>Seven Years in Trenton</title>  
  <title>History of Trenton</title>  
</out>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f05c3-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f05c3-123">See also</span></span>

- [<span data-ttu-id="f05c3-124">Třída XslTransform implementuje procesor XSLT</span><span class="sxs-lookup"><span data-stu-id="f05c3-124">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
