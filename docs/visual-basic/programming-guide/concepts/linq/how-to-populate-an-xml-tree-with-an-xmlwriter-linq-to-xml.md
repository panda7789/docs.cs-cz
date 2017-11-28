---
title: "Postupy: naplnění strom XML s XmlWriter (technologie LINQ to XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5792a0eb-94ee-440d-b601-58cca8c0ee0b
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 548e931a120a319bbd45885e6d1b60685d983c01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-visual-basic"></a>Postupy: naplnění strom XML s XmlWriter (technologie LINQ to XML) (Visual Basic)
Je možné naplnit strom XML používat <xref:System.Xml.Linq.XContainer.CreateWriter%2A> vytvořit <xref:System.Xml.XmlWriter>a pak zápis do <xref:System.Xml.XmlWriter>. Všechny uzly, které se zapisují do naplněný stromu XML <xref:System.Xml.XmlWriter>.  
  
 By obvykle použijete tuto metodu použijete [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] s jiné třídy, která očekává k zápisu do <xref:System.Xml.XmlWriter>, jako například <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
## <a name="example"></a>Příklad  
 Možné použití <xref:System.Xml.Linq.XContainer.CreateWriter%2A> je při použití transformace XSLT. Tento příklad vytvoří strom XML, vytvoří <xref:System.Xml.XmlReader> ve stromové struktuře XML vytvoří nový dokument a poté vytvoří <xref:System.Xml.XmlWriter> k zápisu do nový dokument. Poté vyvolá transformace XSLT, předávání v <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter>. Po úspěšném dokončení transformace, se zobrazí v stromu nové XML výsledky transformace.  
  
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
 <xref:System.Xml.Linq.XContainer.CreateWriter%2A>  
 <xref:System.Xml.XmlWriter>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 [Vytváření stromů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
