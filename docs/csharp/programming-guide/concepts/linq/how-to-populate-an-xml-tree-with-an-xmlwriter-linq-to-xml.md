---
title: "Postupy: naplnění strom XML s XmlWriter (technologie LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: cd5674d1-5c54-4efc-ba68-e23b2875295f
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2df0626d0376973aeaa09876c6737c93dd671da4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-c"></a>Postupy: naplnění strom XML s XmlWriter (technologie LINQ to XML) (C#)
Je možné naplnit strom XML používat <xref:System.Xml.Linq.XContainer.CreateWriter%2A> vytvořit <xref:System.Xml.XmlWriter>a pak zápis do <xref:System.Xml.XmlWriter>. Všechny uzly, které se zapisují do naplněný stromu XML <xref:System.Xml.XmlWriter>.  
  
 By obvykle použijete tuto metodu použijete [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] s jiné třídy, která očekává k zápisu do <xref:System.Xml.XmlWriter>, jako například <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
## <a name="example"></a>Příklad  
 Možné použití <xref:System.Xml.Linq.XContainer.CreateWriter%2A> je při použití transformace XSLT. Tento příklad vytvoří strom XML, vytvoří <xref:System.Xml.XmlReader> ve stromové struktuře XML vytvoří nový dokument a poté vytvoří <xref:System.Xml.XmlWriter> k zápisu do nový dokument. Poté vyvolá transformace XSLT, předávání v <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter>. Po úspěšném dokončení transformace, se zobrazí v stromu nové XML výsledky transformace.  
  
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
 <xref:System.Xml.Linq.XContainer.CreateWriter%2A>  
 <xref:System.Xml.XmlWriter>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 [Vytváření stromů XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
