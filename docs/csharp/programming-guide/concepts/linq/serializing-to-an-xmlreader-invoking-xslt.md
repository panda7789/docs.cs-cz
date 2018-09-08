---
title: Serializace do třídy XmlReader (vyvolání XSLT) (C#)
ms.date: 07/20/2015
ms.assetid: 4cc3ee03-ef4c-429b-a408-fedd10b728cd
ms.openlocfilehash: b1f5bc8bd71036636df9da152c4e364ea5ec6b6e
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44140174"
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-c"></a>Serializace do třídy XmlReader (vyvolání XSLT) (C#)
Při použití <xref:System.Xml?displayProperty=nameWithType> funkce interoperability [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], můžete použít <xref:System.Xml.Linq.XNode.CreateReader%2A> k vytvoření <xref:System.Xml.XmlReader>. Modul, který čte z tohoto <xref:System.Xml.XmlReader> přečte uzlů ze stromu XML a zpracovává je odpovídajícím způsobem.  
  
## <a name="invoking-an-xslt-transformation"></a>Vyvolání transformace XSLT  
 Jedním z využití pro tuto metodu je při vyvolání transformace XSLT. Můžete vytvořit stromu XML, vytvořit <xref:System.Xml.XmlReader> ze stromu XML vytvoříte nový textový dokument a pak vytvořte <xref:System.Xml.XmlWriter> k zápisu do nového dokumentu. Potom můžete vyvolat transformace XSLT, při předávání v <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter>. Po úspěšném dokončení transformace stromu XML nové naplněný výsledky transformace.  
  
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
  
    // Execute the transformation and output the results to a writer.  
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

- [Serializace stromů XML (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
