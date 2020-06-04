---
title: Serializace do třídy XmlReader (vyvolání XSLT)
ms.date: 07/20/2015
ms.assetid: 8b64f95a-e8f6-40f7-99f9-a8002c63af96
ms.openlocfilehash: e51bfc031ad6d5d0eb98718f5d547fb18eb45295
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357371"
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-visual-basic"></a>Serializace do objektu XmlReader (vyvolání XSLT) (Visual Basic)
Pokud používáte <xref:System.Xml?displayProperty=nameWithType> Možnosti interoperability [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , můžete použít <xref:System.Xml.Linq.XNode.CreateReader%2A> k vytvoření <xref:System.Xml.XmlReader> . Modul, který čte z tohoto <xref:System.Xml.XmlReader> kódu čte uzly ze stromu XML a odpovídajícím způsobem je zpracovává.  
  
## <a name="invoking-an-xslt-transformation"></a>Vyvolání transformace XSLT  
 Jedním z možných způsobů použití této metody je vyvolání transformace XSLT. Můžete vytvořit strom XML, vytvořit <xref:System.Xml.XmlReader> z stromu XML, vytvořit nový dokument a pak vytvořit <xref:System.Xml.XmlWriter> pro zápis do nového dokumentu. Pak můžete vyvolat transformaci XSLT, předat do <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter> . Po úspěšném dokončení transformace se nový strom XML naplní výsledky transformace.  
  
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

- [Serializace stromů XML (Visual Basic)](serializing-xml-trees.md)
