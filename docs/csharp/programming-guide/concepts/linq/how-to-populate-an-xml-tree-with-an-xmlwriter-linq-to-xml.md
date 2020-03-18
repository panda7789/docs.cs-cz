---
title: Jak naplnit strom XML pomocí xmlwriteru (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: cd5674d1-5c54-4efc-ba68-e23b2875295f
ms.openlocfilehash: f48843af403f2ee0e6d2850deab009a143f55dc7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345764"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-c"></a>Jak naplnit strom XML pomocí xmlwriteru (LINQ to XML) (C#)
Jedním ze způsobů, jak naplnit strom XML, je použít <xref:System.Xml.Linq.XContainer.CreateWriter%2A> k vytvoření <xref:System.Xml.XmlWriter>a následnému zápisu do souboru <xref:System.Xml.XmlWriter>. Strom XML je naplněn všemi uzly, <xref:System.Xml.XmlWriter>které jsou zapsány do .  
  
 Tuto metodu byste obvykle použili při použití [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] s jinou <xref:System.Xml.XmlWriter>třídou, která očekává zápis do , například <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
## <a name="example"></a>Příklad  
 Jedním z <xref:System.Xml.Linq.XContainer.CreateWriter%2A> možných použití pro je při vyvolání transformace XSLT. Tento příklad vytvoří strom XML, vytvoří ze <xref:System.Xml.XmlReader> stromu XML, vytvoří <xref:System.Xml.XmlWriter> nový dokument a potom vytvoří pro zápis do nového dokumentu. Potom vyvolá xslt transformace, předávání <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter>a . Po úspěšném dokončení transformace je nový strom XML naplněn výsledky transformace.  
  
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
using (XmlWriter writer = newTree.CreateWriter())  
{  
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

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A>
- <xref:System.Xml.XmlWriter>
- <xref:System.Xml.Xsl.XslCompiledTransform>
- [Vytváření stromů XML (C#)](./linq-to-xml-overview.md)
