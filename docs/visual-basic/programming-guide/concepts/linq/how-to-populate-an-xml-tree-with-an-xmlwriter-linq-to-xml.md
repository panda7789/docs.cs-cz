---
title: 'Postupy: naplnění stromu XML pomocí funkce XmlWriter (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 5792a0eb-94ee-440d-b601-58cca8c0ee0b
ms.openlocfilehash: ec44f6e21453a1333f842030bae0c4f80dedb9c3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333762"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-visual-basic"></a>Postupy: naplnění stromu XML pomocí funkce XmlWriter (LINQ to XML) (Visual Basic)
Jedním ze způsobů, jak naplnit strom XML, je použít <xref:System.Xml.Linq.XContainer.CreateWriter%2A> k vytvoření <xref:System.Xml.XmlWriter>a pak zapisovat do <xref:System.Xml.XmlWriter>. Do stromu XML se naplní všechny uzly, které jsou zapsány do <xref:System.Xml.XmlWriter>.  
  
 Tuto metodu byste obvykle použili při použití [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] s jinou třídou, která očekává zápis do <xref:System.Xml.XmlWriter>, jako je například <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
## <a name="example"></a>Příklad  
 Jedním z možných použití <xref:System.Xml.Linq.XContainer.CreateWriter%2A> je při vyvolání transformace XSLT. Tento příklad vytvoří strom XML, vytvoří <xref:System.Xml.XmlReader> ze stromu XML, vytvoří nový dokument a potom vytvoří <xref:System.Xml.XmlWriter> k zápisu do nového dokumentu. Poté vyvolá transformaci XSLT, která předává <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter>. Po úspěšném dokončení transformace se nový strom XML naplní výsledky transformace.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A>
- <xref:System.Xml.XmlWriter>
- <xref:System.Xml.Xsl.XslCompiledTransform>
- [Vytváření stromů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
