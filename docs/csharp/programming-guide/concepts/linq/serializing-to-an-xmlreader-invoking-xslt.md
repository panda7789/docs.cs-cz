---
title: Serializace na xmlreader (vyvolání XSLT) (C#)
ms.date: 07/20/2015
ms.assetid: 4cc3ee03-ef4c-429b-a408-fedd10b728cd
ms.openlocfilehash: b079fe05fa8c230f644e011dcb62ec54f55cae60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "66487190"
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-c"></a>Serializace na xmlreader (vyvolání XSLT) (C#)
Používáte-li možnosti [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]interoperability aplikace <xref:System.Xml.Linq.XNode.CreateReader%2A> , <xref:System.Xml.XmlReader>můžete použít k vytvoření aplikace . <xref:System.Xml?displayProperty=nameWithType> Modul, který čte <xref:System.Xml.XmlReader> z tohoto čte uzly ze stromu XML a zpracovává je odpovídajícím způsobem.  
  
## <a name="invoking-an-xslt-transformation"></a>Vyvolání transformace XSLT  
 Jedním z možných použití pro tuto metodu je při vyvolání transformace XSLT. Můžete vytvořit strom XML, <xref:System.Xml.XmlReader> vytvořit ze stromu XML, vytvořit nový <xref:System.Xml.XmlWriter> dokument a pak vytvořit a zapisovat do nového dokumentu. Potom můžete vyvolat xslt transformace, <xref:System.Xml.XmlReader> předávání <xref:System.Xml.XmlWriter>a . Po úspěšném dokončení transformace je nový strom XML naplněn výsledky transformace.  
  
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
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a>Viz také

- [Serializace stromů XML (C#)](serializing-to-files-textwriters-and-xmlwriters.md)
