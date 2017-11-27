---
title: "Serializace pro objekt XmlReader (volajícím XSLT) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b64f95a-e8f6-40f7-99f9-a8002c63af96
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ea4a8a17e938b22d6e307ebe307c69481e44e6d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-visual-basic"></a><span data-ttu-id="43933-102">Serializace pro objekt XmlReader (volajícím XSLT) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43933-102">Serializing to an XmlReader (Invoking XSLT) (Visual Basic)</span></span>
<span data-ttu-id="43933-103">Při použití <xref:System.Xml?displayProperty=nameWithType> interoperabilita možnosti [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], můžete použít <xref:System.Xml.Linq.XNode.CreateReader%2A> vytvořit <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="43933-103">When you use the <xref:System.Xml?displayProperty=nameWithType> interoperability capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can use <xref:System.Xml.Linq.XNode.CreateReader%2A> to create an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="43933-104">Modul, který čte z tohoto <xref:System.Xml.XmlReader> čte uzly ve stromové struktuře XML a zpracovává je odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="43933-104">The module that reads from this <xref:System.Xml.XmlReader> reads the nodes from the XML tree and processes them accordingly.</span></span>  
  
## <a name="invoking-an-xslt-transformation"></a><span data-ttu-id="43933-105">Vyvolání transformaci XSLT</span><span class="sxs-lookup"><span data-stu-id="43933-105">Invoking an XSLT Transformation</span></span>  
 <span data-ttu-id="43933-106">Možné použití této metody je při použití transformace XSLT.</span><span class="sxs-lookup"><span data-stu-id="43933-106">One possible use for this method is when invoking an XSLT transformation.</span></span> <span data-ttu-id="43933-107">Můžete vytvořit strom XML, vytvořit <xref:System.Xml.XmlReader> ve stromové struktuře XML vytvoříte nový textový dokument a poté vytvořit <xref:System.Xml.XmlWriter> k zápisu do nový dokument.</span><span class="sxs-lookup"><span data-stu-id="43933-107">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and then create an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="43933-108">Potom můžete vyvolat transformace XSLT, předávání v <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="43933-108">Then, you can invoke the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="43933-109">Po úspěšném dokončení transformace, se zobrazí v stromu nové XML výsledky transformace.</span><span class="sxs-lookup"><span data-stu-id="43933-109">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
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
  
 <span data-ttu-id="43933-110">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="43933-110">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="43933-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="43933-111">See Also</span></span>  
 [<span data-ttu-id="43933-112">Serializace XML stromů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43933-112">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
