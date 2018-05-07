---
title: Serializace pro objekt XmlReader (volajícím XSLT) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 8b64f95a-e8f6-40f7-99f9-a8002c63af96
ms.openlocfilehash: 05754593f4f30683ffabecaa8e16c35bf836a3f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-visual-basic"></a>Serializace pro objekt XmlReader (volajícím XSLT) (Visual Basic)
Při použití <xref:System.Xml?displayProperty=nameWithType> interoperabilita možnosti [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], můžete použít <xref:System.Xml.Linq.XNode.CreateReader%2A> vytvořit <xref:System.Xml.XmlReader>. Modul, který čte z tohoto <xref:System.Xml.XmlReader> čte uzly ve stromové struktuře XML a zpracovává je odpovídajícím způsobem.  
  
## <a name="invoking-an-xslt-transformation"></a>Vyvolání transformaci XSLT  
 Možné použití této metody je při použití transformace XSLT. Můžete vytvořit strom XML, vytvořit <xref:System.Xml.XmlReader> ve stromové struktuře XML vytvoříte nový textový dokument a poté vytvořit <xref:System.Xml.XmlWriter> k zápisu do nový dokument. Potom můžete vyvolat transformace XSLT, předávání v <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter>. Po úspěšném dokončení transformace, se zobrazí v stromu nové XML výsledky transformace.  
  
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
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a>Viz také  
 [Serializace XML stromů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
