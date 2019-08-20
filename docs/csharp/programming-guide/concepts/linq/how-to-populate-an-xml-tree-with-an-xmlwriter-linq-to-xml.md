---
title: 'Postupy: Naplnění stromu XML pomocí funkce XmlWriter (LINQ to XML)C#()'
ms.date: 07/20/2015
ms.assetid: cd5674d1-5c54-4efc-ba68-e23b2875295f
ms.openlocfilehash: 88b088ddad54d1fef67cb4c86f8df4eee7bf3662
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593102"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-c"></a><span data-ttu-id="72447-102">Postupy: Naplnění stromu XML pomocí funkce XmlWriter (LINQ to XML)C#()</span><span class="sxs-lookup"><span data-stu-id="72447-102">How to: Populate an XML Tree with an XmlWriter (LINQ to XML) (C#)</span></span>
<span data-ttu-id="72447-103">Jedním ze způsobů <xref:System.Xml.XmlWriter>, jak naplnit strom XML, <xref:System.Xml.Linq.XContainer.CreateWriter%2A> je použít k vytvoření <xref:System.Xml.XmlWriter>a zápis do.</span><span class="sxs-lookup"><span data-stu-id="72447-103">One way to populate an XML tree is to use <xref:System.Xml.Linq.XContainer.CreateWriter%2A> to create an <xref:System.Xml.XmlWriter>, and then write to the <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="72447-104">Do stromu XML se naplní všechny uzly, které jsou zapsány do <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="72447-104">The XML tree is populated with all nodes that are written to the <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="72447-105">Tuto metodu byste obvykle použili při použití [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] s jinou třídou, která očekává zápis <xref:System.Xml.XmlWriter>do, například <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="72447-105">You would typically use this method when you use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] with another class that expects to write to an <xref:System.Xml.XmlWriter>, such as <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72447-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="72447-106">Example</span></span>  
 <span data-ttu-id="72447-107">Jedním z možných použití <xref:System.Xml.Linq.XContainer.CreateWriter%2A> je při vyvolání transformace XSLT.</span><span class="sxs-lookup"><span data-stu-id="72447-107">One possible use for <xref:System.Xml.Linq.XContainer.CreateWriter%2A> is when invoking an XSLT transformation.</span></span> <span data-ttu-id="72447-108">Tento příklad vytvoří strom XML, vytvoří <xref:System.Xml.XmlReader> ze stromu XML, vytvoří nový dokument a pak <xref:System.Xml.XmlWriter> vytvoří pro zápis do nového dokumentu.</span><span class="sxs-lookup"><span data-stu-id="72447-108">This example creates an XML tree, creates an <xref:System.Xml.XmlReader> from the XML tree, creates a new document, and then creates an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="72447-109">Poté vyvolá transformaci XSLT, do <xref:System.Xml.XmlReader> které se přecházejí a. <xref:System.Xml.XmlWriter></span><span class="sxs-lookup"><span data-stu-id="72447-109">It then invokes the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="72447-110">Po úspěšném dokončení transformace se nový strom XML naplní výsledky transformace.</span><span class="sxs-lookup"><span data-stu-id="72447-110">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
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
  
 <span data-ttu-id="72447-111">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="72447-111">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="72447-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="72447-112">See also</span></span>

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A>
- <xref:System.Xml.XmlWriter>
- <xref:System.Xml.Xsl.XslCompiledTransform>
- [<span data-ttu-id="72447-113">Vytváření stromů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="72447-113">Creating XML Trees (C#)</span></span>](./linq-to-xml-overview.md)
