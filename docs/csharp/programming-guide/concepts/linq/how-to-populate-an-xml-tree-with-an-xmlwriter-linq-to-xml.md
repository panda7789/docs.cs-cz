---
title: Postup naplnění stromu XML pomocí funkce XmlWriter (LINQ to XML) (C#)
description: Naučte se, jak naplnit strom XML pomocí CreateWriter k vytvoření XmlWriter a pak zapisovat do XmlWriter v LINQ to XML v jazyce C#.
ms.date: 07/20/2015
ms.assetid: cd5674d1-5c54-4efc-ba68-e23b2875295f
ms.openlocfilehash: 9639c5947583bccf4f8ba427fc8611e181ef1536
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104795"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-c"></a>Postup naplnění stromu XML pomocí funkce XmlWriter (LINQ to XML) (C#)
Jedním ze způsobů, jak naplnit strom XML, je použít <xref:System.Xml.Linq.XContainer.CreateWriter%2A> k vytvoření <xref:System.Xml.XmlWriter> a zápis do <xref:System.Xml.XmlWriter> . Do stromu XML se naplní všechny uzly, které jsou zapsány do <xref:System.Xml.XmlWriter> .  
  
 Tuto metodu byste obvykle použili při použití [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] s jinou třídou, která očekává zápis do <xref:System.Xml.XmlWriter> , například <xref:System.Xml.Xsl.XslCompiledTransform> .  
  
## <a name="example"></a>Příklad  
 Jedním z možných použití <xref:System.Xml.Linq.XContainer.CreateWriter%2A> je při vyvolání transformace XSLT. Tento příklad vytvoří strom XML, vytvoří <xref:System.Xml.XmlReader> ze stromu XML, vytvoří nový dokument a pak vytvoří <xref:System.Xml.XmlWriter> pro zápis do nového dokumentu. Poté vyvolá transformaci XSLT, do které se přecházejí <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter> . Po úspěšném dokončení transformace se nový strom XML naplní výsledky transformace.  
  
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
  
 Tento příklad vytvoří následující výstup:  
  
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
