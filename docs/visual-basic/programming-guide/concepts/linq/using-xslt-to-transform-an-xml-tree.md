---
title: Použití XSLT transformace stromu XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 3390ca68-c270-4e1d-b64b-6a063a77017c
ms.openlocfilehash: 37fd25a327906327f33106ae145d45c5387cae47
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690394"
---
# <a name="using-xslt-to-transform-an-xml-tree-visual-basic"></a><span data-ttu-id="62f67-102">Použití XSLT transformace stromu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62f67-102">Using XSLT to Transform an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="62f67-103">Můžete vytvořit stromu XML, vytvořit <xref:System.Xml.XmlReader> ze stromu XML vytvoříte nový textový dokument a vytvoření <xref:System.Xml.XmlWriter> , která bude zapisovat do nového dokumentu.</span><span class="sxs-lookup"><span data-stu-id="62f67-103">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and create an <xref:System.Xml.XmlWriter> that will write into the new document.</span></span> <span data-ttu-id="62f67-104">Potom můžete vyvolat transformace XSLT, předá <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter> k transformaci.</span><span class="sxs-lookup"><span data-stu-id="62f67-104">Then, you can invoke the XSLT transformation, passing the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to the transformation.</span></span> <span data-ttu-id="62f67-105">Po úspěšném dokončení transformace nového stromu XML je vyplněno pomocí výsledků transformace.</span><span class="sxs-lookup"><span data-stu-id="62f67-105">After the transformation successfully completes, the new XML tree is populated with the results of the transform.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62f67-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="62f67-106">Example</span></span>  
  
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
  
Dim xmlTree As XElement = _   
    <Parent>  
        <Child1>Child1 data</Child1>  
        <Child2>Child2 data</Child2>  
    </Parent>  
  
Dim newTree As XDocument = New XDocument()  
  
Using writer As XmlWriter = newTree.CreateWriter()  
    ' Load the style sheet.  
    Dim xslt As XslCompiledTransform = _  
        New XslCompiledTransform()  
    xslt.Load(xslMarkup.CreateReader())  
  
    ' Execute the transform and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer)  
End Using  
  
Console.WriteLine(newTree)  
```  
  
 <span data-ttu-id="62f67-107">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="62f67-107">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="62f67-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="62f67-108">See also</span></span>
- <xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=nameWithType>
- [<span data-ttu-id="62f67-109">Pokročilé technologie LINQ to XML programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62f67-109">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
