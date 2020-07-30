---
title: Serializace do objektu XmlReader (vyvolání XSLT) (C#)
description: Naučte se používat CreateReader k vytvoření objektu XmlReader v jazyce C#. Modul, který čte z tohoto objektu XmlReader, přečte uzly ze stromu XML a zpracuje je.
ms.date: 07/20/2015
ms.assetid: 4cc3ee03-ef4c-429b-a408-fedd10b728cd
ms.openlocfilehash: aa5a232c74c5314cb7f1cf03c2a8875ca1cd04df
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302409"
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-c"></a><span data-ttu-id="a4b63-104">Serializace do objektu XmlReader (vyvolání XSLT) (C#)</span><span class="sxs-lookup"><span data-stu-id="a4b63-104">Serializing to an XmlReader (Invoking XSLT) (C#)</span></span>
<span data-ttu-id="a4b63-105">Pokud používáte <xref:System.Xml?displayProperty=nameWithType> Možnosti interoperability [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , můžete použít <xref:System.Xml.Linq.XNode.CreateReader%2A> k vytvoření <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="a4b63-105">When you use the <xref:System.Xml?displayProperty=nameWithType> interoperability capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can use <xref:System.Xml.Linq.XNode.CreateReader%2A> to create an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="a4b63-106">Modul, který čte z tohoto <xref:System.Xml.XmlReader> kódu čte uzly ze stromu XML a odpovídajícím způsobem je zpracovává.</span><span class="sxs-lookup"><span data-stu-id="a4b63-106">The module that reads from this <xref:System.Xml.XmlReader> reads the nodes from the XML tree and processes them accordingly.</span></span>  
  
## <a name="invoking-an-xslt-transformation"></a><span data-ttu-id="a4b63-107">Vyvolání transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="a4b63-107">Invoking an XSLT Transformation</span></span>  
 <span data-ttu-id="a4b63-108">Jedním z možných způsobů použití této metody je vyvolání transformace XSLT.</span><span class="sxs-lookup"><span data-stu-id="a4b63-108">One possible use for this method is when invoking an XSLT transformation.</span></span> <span data-ttu-id="a4b63-109">Můžete vytvořit strom XML, vytvořit <xref:System.Xml.XmlReader> z stromu XML, vytvořit nový dokument a pak vytvořit <xref:System.Xml.XmlWriter> pro zápis do nového dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a4b63-109">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and then create an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="a4b63-110">Pak můžete vyvolat transformaci XSLT, předat do <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="a4b63-110">Then, you can invoke the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="a4b63-111">Po úspěšném dokončení transformace se nový strom XML naplní výsledky transformace.</span><span class="sxs-lookup"><span data-stu-id="a4b63-111">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
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
  
 <span data-ttu-id="a4b63-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a4b63-112">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a4b63-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4b63-113">See also</span></span>

- [<span data-ttu-id="a4b63-114">Serializace stromů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="a4b63-114">Serializing XML Trees (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
