---
title: 'Postupy: naplnění strom XML s XmlWriter (technologie LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: cd5674d1-5c54-4efc-ba68-e23b2875295f
ms.openlocfilehash: cc3aeb8e8fbef3b109c9bc591084f0d033f5f476
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323671"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-c"></a><span data-ttu-id="5c5da-102">Postupy: naplnění strom XML s XmlWriter (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="5c5da-102">How to: Populate an XML Tree with an XmlWriter (LINQ to XML) (C#)</span></span>
<span data-ttu-id="5c5da-103">Je možné naplnit strom XML používat <xref:System.Xml.Linq.XContainer.CreateWriter%2A> vytvořit <xref:System.Xml.XmlWriter>a pak zápis do <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="5c5da-103">One way to populate an XML tree is to use <xref:System.Xml.Linq.XContainer.CreateWriter%2A> to create an <xref:System.Xml.XmlWriter>, and then write to the <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="5c5da-104">Všechny uzly, které se zapisují do naplněný stromu XML <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="5c5da-104">The XML tree is populated with all nodes that are written to the <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="5c5da-105">By obvykle použijete tuto metodu použijete [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] s jiné třídy, která očekává k zápisu do <xref:System.Xml.XmlWriter>, jako například <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="5c5da-105">You would typically use this method when you use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] with another class that expects to write to an <xref:System.Xml.XmlWriter>, such as <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c5da-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="5c5da-106">Example</span></span>  
 <span data-ttu-id="5c5da-107">Možné použití <xref:System.Xml.Linq.XContainer.CreateWriter%2A> je při použití transformace XSLT.</span><span class="sxs-lookup"><span data-stu-id="5c5da-107">One possible use for <xref:System.Xml.Linq.XContainer.CreateWriter%2A> is when invoking an XSLT transformation.</span></span> <span data-ttu-id="5c5da-108">Tento příklad vytvoří strom XML, vytvoří <xref:System.Xml.XmlReader> ve stromové struktuře XML vytvoří nový dokument a poté vytvoří <xref:System.Xml.XmlWriter> k zápisu do nový dokument.</span><span class="sxs-lookup"><span data-stu-id="5c5da-108">This example creates an XML tree, creates an <xref:System.Xml.XmlReader> from the XML tree, creates a new document, and then creates an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="5c5da-109">Poté vyvolá transformace XSLT, předávání v <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="5c5da-109">It then invokes the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="5c5da-110">Po úspěšném dokončení transformace, se zobrazí v stromu nové XML výsledky transformace.</span><span class="sxs-lookup"><span data-stu-id="5c5da-110">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
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
  
 <span data-ttu-id="5c5da-111">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="5c5da-111">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5c5da-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="5c5da-112">See Also</span></span>  
 <xref:System.Xml.Linq.XContainer.CreateWriter%2A>  
 <xref:System.Xml.XmlWriter>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 [<span data-ttu-id="5c5da-113">Vytváření stromů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="5c5da-113">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
