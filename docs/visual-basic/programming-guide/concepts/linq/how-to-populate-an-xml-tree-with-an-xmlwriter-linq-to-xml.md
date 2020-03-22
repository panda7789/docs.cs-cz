---
title: 'Postup: Naplnění stromu XML jazykem XMLWriter (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 5792a0eb-94ee-440d-b601-58cca8c0ee0b
ms.openlocfilehash: fecf57eac570a9ca57dd1fe2f7a0b54cd78c33b5
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266999"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-visual-basic"></a><span data-ttu-id="334df-102">Postup: Naplnění stromu XML pomocí xmlwriteru (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="334df-102">How to: Populate an XML Tree with an XmlWriter (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="334df-103">Jedním ze způsobů, jak naplnit strom XML, je použít <xref:System.Xml.Linq.XContainer.CreateWriter%2A> k vytvoření <xref:System.Xml.XmlWriter>a následnému zápisu do souboru <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="334df-103">One way to populate an XML tree is to use <xref:System.Xml.Linq.XContainer.CreateWriter%2A> to create an <xref:System.Xml.XmlWriter>, and then write to the <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="334df-104">Strom XML je naplněn všemi uzly, <xref:System.Xml.XmlWriter>které jsou zapsány do .</span><span class="sxs-lookup"><span data-stu-id="334df-104">The XML tree is populated with all nodes that are written to the <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="334df-105">Tuto metodu byste obvykle použili při použití [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] s jinou <xref:System.Xml.XmlWriter>třídou, která očekává zápis do , například <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="334df-105">You would typically use this method when you use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] with another class that expects to write to an <xref:System.Xml.XmlWriter>, such as <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="334df-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="334df-106">Example</span></span>  
 <span data-ttu-id="334df-107">Jedním z <xref:System.Xml.Linq.XContainer.CreateWriter%2A> možných použití pro je při vyvolání transformace XSLT.</span><span class="sxs-lookup"><span data-stu-id="334df-107">One possible use for <xref:System.Xml.Linq.XContainer.CreateWriter%2A> is when invoking an XSLT transformation.</span></span> <span data-ttu-id="334df-108">Tento příklad vytvoří strom XML, vytvoří ze <xref:System.Xml.XmlReader> stromu XML, vytvoří <xref:System.Xml.XmlWriter> nový dokument a potom vytvoří pro zápis do nového dokumentu.</span><span class="sxs-lookup"><span data-stu-id="334df-108">This example creates an XML tree, creates an <xref:System.Xml.XmlReader> from the XML tree, creates a new document, and then creates an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="334df-109">Potom vyvolá xslt transformace, předávání <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter>a .</span><span class="sxs-lookup"><span data-stu-id="334df-109">It then invokes the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="334df-110">Po úspěšném dokončení transformace je nový strom XML naplněn výsledky transformace.</span><span class="sxs-lookup"><span data-stu-id="334df-110">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
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
  
 <span data-ttu-id="334df-111">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="334df-111">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="334df-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="334df-112">See also</span></span>

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A>
- <xref:System.Xml.XmlWriter>
- <xref:System.Xml.Xsl.XslCompiledTransform>
- [<span data-ttu-id="334df-113">Vytváření stromů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="334df-113">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
