---
title: 'Postupy: Naplnění stromu XML pomocí třídy XmlWriter (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 5792a0eb-94ee-440d-b601-58cca8c0ee0b
ms.openlocfilehash: b3a36326175eeba8cd692a2c71f1f9b0fde24b5f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397970"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-visual-basic"></a><span data-ttu-id="350e1-102">Postupy: naplnění stromu XML pomocí funkce XmlWriter (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="350e1-102">How to: Populate an XML Tree with an XmlWriter (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="350e1-103">Jedním ze způsobů, jak naplnit strom XML, je použít <xref:System.Xml.Linq.XContainer.CreateWriter%2A> k vytvoření <xref:System.Xml.XmlWriter> a zápis do <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="350e1-103">One way to populate an XML tree is to use <xref:System.Xml.Linq.XContainer.CreateWriter%2A> to create an <xref:System.Xml.XmlWriter>, and then write to the <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="350e1-104">Do stromu XML se naplní všechny uzly, které jsou zapsány do <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="350e1-104">The XML tree is populated with all nodes that are written to the <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="350e1-105">Tuto metodu byste obvykle použili při použití [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] s jinou třídou, která očekává zápis do <xref:System.Xml.XmlWriter> , například <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="350e1-105">You would typically use this method when you use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] with another class that expects to write to an <xref:System.Xml.XmlWriter>, such as <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="350e1-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="350e1-106">Example</span></span>  
 <span data-ttu-id="350e1-107">Jedním z možných použití <xref:System.Xml.Linq.XContainer.CreateWriter%2A> je při vyvolání transformace XSLT.</span><span class="sxs-lookup"><span data-stu-id="350e1-107">One possible use for <xref:System.Xml.Linq.XContainer.CreateWriter%2A> is when invoking an XSLT transformation.</span></span> <span data-ttu-id="350e1-108">Tento příklad vytvoří strom XML, vytvoří <xref:System.Xml.XmlReader> ze stromu XML, vytvoří nový dokument a pak vytvoří <xref:System.Xml.XmlWriter> pro zápis do nového dokumentu.</span><span class="sxs-lookup"><span data-stu-id="350e1-108">This example creates an XML tree, creates an <xref:System.Xml.XmlReader> from the XML tree, creates a new document, and then creates an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="350e1-109">Poté vyvolá transformaci XSLT, do které se přecházejí <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="350e1-109">It then invokes the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="350e1-110">Po úspěšném dokončení transformace se nový strom XML naplní výsledky transformace.</span><span class="sxs-lookup"><span data-stu-id="350e1-110">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
```vb  
Dim xslMarkup As XDocument = _  
    <?xml version='1.0'?>
    <xsl:stylesheet xmlns:xsl='http://www.w3.org/1999/XSL/Transform' version='1.0'>  
        <xsl:template match='/Parent'>  
            <Root>  
                <C1>  
                    <xsl:value-of select='Child1'/>  
                </C1>  
                <C2>  
                    <xsl:value-of select='Child2'/>  
                </C2>  
            </Root>  
        </xsl:template>  
    </xsl:stylesheet>  
  
Dim xmlTree As XDocument = _  
    <?xml version='1.0'?>  
    <Parent>  
        <Child1>Child1 data</Child1>  
        <Child2>Child2 data</Child2>  
    </Parent>  
  
Dim newTree As XDocument = New XDocument()  
Using writer As XmlWriter = newTree.CreateWriter()  
    ' Load the style sheet.  
    Dim xslt As XslCompiledTransform = New XslCompiledTransform()  
    xslt.Load(xslMarkup.CreateReader())  
  
    ' Execute the transformation and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer)  
End Using  
  
Console.WriteLine(newTree)  
```  
  
 <span data-ttu-id="350e1-111">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="350e1-111">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="350e1-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="350e1-112">See also</span></span>

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A>
- <xref:System.Xml.XmlWriter>
- <xref:System.Xml.Xsl.XslCompiledTransform>
- [<span data-ttu-id="350e1-113">Vytváření stromů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="350e1-113">Creating XML Trees (Visual Basic)</span></span>](creating-xml-trees.md)
