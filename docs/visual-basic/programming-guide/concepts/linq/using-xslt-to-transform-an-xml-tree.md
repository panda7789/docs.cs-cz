---
title: Transformace stromu XML pomocí XSLT
ms.date: 07/20/2015
ms.assetid: 3390ca68-c270-4e1d-b64b-6a063a77017c
ms.openlocfilehash: 5332eb0a4fa8a2bd855421d674fe9f0de2ccb5f3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364432"
---
# <a name="using-xslt-to-transform-an-xml-tree-visual-basic"></a>Transformace stromu XML pomocí XSLT (Visual Basic)

Můžete vytvořit strom XML, vytvořit <xref:System.Xml.XmlReader> z stromu XML, vytvořit nový dokument a vytvořit <xref:System.Xml.XmlWriter> , který bude zapisovat do nového dokumentu. Pak můžete vyvolat transformaci XSLT, předáním <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter> k transformaci. Po úspěšném dokončení transformace se nový strom XML naplní výsledky transformace.

## <a name="example"></a>Příklad

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

Tento příklad vytvoří následující výstup:

```xml
<Root>
  <C1>Child1 data</C1>
  <C2>Child2 data</C2>
</Root>
```

## <a name="see-also"></a>Viz také

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=nameWithType>
- [Rozšířené programování LINQ to XML (Visual Basic)](advanced-linq-to-xml-programming.md)
