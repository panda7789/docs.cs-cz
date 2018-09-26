---
title: Použití XSLT transformace stromu XML (C#)
ms.date: 07/20/2015
ms.assetid: 373a2699-d4c5-471b-9bda-c1f0ab73b477
ms.openlocfilehash: 3fa850c0f09404da49b2963e980d15e1ed54316f
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47207543"
---
# <a name="using-xslt-to-transform-an-xml-tree-c"></a>Použití XSLT transformace stromu XML (C#)
Můžete vytvořit stromu XML, vytvořit <xref:System.Xml.XmlReader> ze stromu XML vytvoříte nový textový dokument a vytvoření <xref:System.Xml.XmlWriter> , která bude zapisovat do nového dokumentu. Potom můžete vyvolat transformace XSLT, předá <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter> k transformaci. Po úspěšném dokončení transformace nového stromu XML je vyplněno pomocí výsledků transformace.  
  
## <a name="example"></a>Příklad  
  
```csharp  
string xslMarkup = @"<?xml version='1.0'?>  
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
</xsl:stylesheet>";  
  
XDocument xmlTree = new XDocument(  
    new XElement("Parent",  
        new XElement("Child1", "Child1 data"),  
        new XElement("Child2", "Child2 data")  
    )  
);  
  
XDocument newTree = new XDocument();  
using (XmlWriter writer = newTree.CreateWriter()) {  
    // Load the style sheet.  
    XslCompiledTransform xslt = new XslCompiledTransform();  
    xslt.Load(XmlReader.Create(new StringReader(xslMarkup)));  
  
    // Execute the transform and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer);  
}  
  
Console.WriteLine(newTree);  
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
- [Pokročilé technologie LINQ to XML programování (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
