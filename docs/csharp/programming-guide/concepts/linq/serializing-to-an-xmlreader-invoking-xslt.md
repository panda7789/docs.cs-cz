---
title: Serializace pro objekt XmlReader (volajícím XSLT) (C#)
ms.date: 07/20/2015
ms.assetid: 4cc3ee03-ef4c-429b-a408-fedd10b728cd
ms.openlocfilehash: 0663bf2e2c83524e94c91f436ca0146f2dcd68ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329167"
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-c"></a><span data-ttu-id="309e7-102">Serializace pro objekt XmlReader (volajícím XSLT) (C#)</span><span class="sxs-lookup"><span data-stu-id="309e7-102">Serializing to an XmlReader (Invoking XSLT) (C#)</span></span>
<span data-ttu-id="309e7-103">Při použití <xref:System.Xml?displayProperty=nameWithType> interoperabilita možnosti [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], můžete použít <xref:System.Xml.Linq.XNode.CreateReader%2A> vytvořit <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="309e7-103">When you use the <xref:System.Xml?displayProperty=nameWithType> interoperability capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can use <xref:System.Xml.Linq.XNode.CreateReader%2A> to create an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="309e7-104">Modul, který čte z tohoto <xref:System.Xml.XmlReader> čte uzly ve stromové struktuře XML a zpracovává je odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="309e7-104">The module that reads from this <xref:System.Xml.XmlReader> reads the nodes from the XML tree and processes them accordingly.</span></span>  
  
## <a name="invoking-an-xslt-transformation"></a><span data-ttu-id="309e7-105">Vyvolání transformaci XSLT</span><span class="sxs-lookup"><span data-stu-id="309e7-105">Invoking an XSLT Transformation</span></span>  
 <span data-ttu-id="309e7-106">Možné použití této metody je při použití transformace XSLT.</span><span class="sxs-lookup"><span data-stu-id="309e7-106">One possible use for this method is when invoking an XSLT transformation.</span></span> <span data-ttu-id="309e7-107">Můžete vytvořit strom XML, vytvořit <xref:System.Xml.XmlReader> ve stromové struktuře XML vytvoříte nový textový dokument a poté vytvořit <xref:System.Xml.XmlWriter> k zápisu do nový dokument.</span><span class="sxs-lookup"><span data-stu-id="309e7-107">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and then create an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="309e7-108">Potom můžete vyvolat transformace XSLT, předávání v <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="309e7-108">Then, you can invoke the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="309e7-109">Po úspěšném dokončení transformace, se zobrazí v stromu nové XML výsledky transformace.</span><span class="sxs-lookup"><span data-stu-id="309e7-109">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
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
  
 <span data-ttu-id="309e7-110">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="309e7-110">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="309e7-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="309e7-111">See Also</span></span>  
 [<span data-ttu-id="309e7-112">Serializace XML stromů (C#)</span><span class="sxs-lookup"><span data-stu-id="309e7-112">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
