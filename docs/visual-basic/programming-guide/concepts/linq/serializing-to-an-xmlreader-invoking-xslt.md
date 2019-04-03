---
title: Serializace do třídy XmlReader (vyvolání XSLT) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 8b64f95a-e8f6-40f7-99f9-a8002c63af96
ms.openlocfilehash: c557230d1ae350d5f542b79a2c210ce5ce3f73fa
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829288"
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-visual-basic"></a><span data-ttu-id="9aa20-102">Serializace do třídy XmlReader (vyvolání XSLT) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9aa20-102">Serializing to an XmlReader (Invoking XSLT) (Visual Basic)</span></span>
<span data-ttu-id="9aa20-103">Při použití <xref:System.Xml?displayProperty=nameWithType> funkce interoperability [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], můžete použít <xref:System.Xml.Linq.XNode.CreateReader%2A> k vytvoření <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="9aa20-103">When you use the <xref:System.Xml?displayProperty=nameWithType> interoperability capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can use <xref:System.Xml.Linq.XNode.CreateReader%2A> to create an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="9aa20-104">Modul, který čte z tohoto <xref:System.Xml.XmlReader> přečte uzlů ze stromu XML a zpracovává je odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="9aa20-104">The module that reads from this <xref:System.Xml.XmlReader> reads the nodes from the XML tree and processes them accordingly.</span></span>  
  
## <a name="invoking-an-xslt-transformation"></a><span data-ttu-id="9aa20-105">Vyvolání transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="9aa20-105">Invoking an XSLT Transformation</span></span>  
 <span data-ttu-id="9aa20-106">Jedním z využití pro tuto metodu je při vyvolání transformace XSLT.</span><span class="sxs-lookup"><span data-stu-id="9aa20-106">One possible use for this method is when invoking an XSLT transformation.</span></span> <span data-ttu-id="9aa20-107">Můžete vytvořit stromu XML, vytvořit <xref:System.Xml.XmlReader> ze stromu XML vytvoříte nový textový dokument a pak vytvořte <xref:System.Xml.XmlWriter> k zápisu do nového dokumentu.</span><span class="sxs-lookup"><span data-stu-id="9aa20-107">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and then create an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="9aa20-108">Potom můžete vyvolat transformace XSLT, při předávání v <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="9aa20-108">Then, you can invoke the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="9aa20-109">Po úspěšném dokončení transformace stromu XML nové naplněný výsledky transformace.</span><span class="sxs-lookup"><span data-stu-id="9aa20-109">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
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
  
 <span data-ttu-id="9aa20-110">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="9aa20-110">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9aa20-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9aa20-111">See also</span></span>

- [<span data-ttu-id="9aa20-112">Serializace stromů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9aa20-112">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
