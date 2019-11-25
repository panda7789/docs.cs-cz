---
title: Serializace pomocí deklarace XML
ms.date: 07/20/2015
ms.assetid: 8726f79e-2bb0-4ba0-969d-197cca591647
ms.openlocfilehash: 96c95b4c94290016684721a194ca31a836a49740
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350624"
---
# <a name="serializing-with-an-xml-declaration-visual-basic"></a><span data-ttu-id="b5de5-102">Serializing with an XML Declaration (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5de5-102">Serializing with an XML Declaration (Visual Basic)</span></span>
<span data-ttu-id="b5de5-103">This topic describes how to control whether serialization generates an XML declaration.</span><span class="sxs-lookup"><span data-stu-id="b5de5-103">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="b5de5-104">XML Declaration Generation</span><span class="sxs-lookup"><span data-stu-id="b5de5-104">XML Declaration Generation</span></span>  
 <span data-ttu-id="b5de5-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span><span class="sxs-lookup"><span data-stu-id="b5de5-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="b5de5-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span><span class="sxs-lookup"><span data-stu-id="b5de5-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="b5de5-107">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span><span class="sxs-lookup"><span data-stu-id="b5de5-107">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="b5de5-108">Serializace pomocí deklarace XML</span><span class="sxs-lookup"><span data-stu-id="b5de5-108">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="b5de5-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span><span class="sxs-lookup"><span data-stu-id="b5de5-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```vb  
Dim root As XElement = <Root>  
                           <Child>child content</Child>  
                       </Root>  
root.Save("Root.xml")  
Dim str As String = File.ReadAllText("Root.xml")  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="b5de5-110">This example produces the following output:</span><span class="sxs-lookup"><span data-stu-id="b5de5-110">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="b5de5-111">Serializing without an XML Declaration</span><span class="sxs-lookup"><span data-stu-id="b5de5-111">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="b5de5-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="b5de5-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
```vb  
Dim sb As StringBuilder = New StringBuilder()  
Dim xws As XmlWriterSettings = New XmlWriterSettings()  
xws.OmitXmlDeclaration = True  
  
Using xw As XmlWriter = XmlWriter.Create(sb, xws)  
    Dim root = <Root>  
                   <Child>child content</Child>  
               </Root>  
    root.Save(xw)  
End Using  
Console.WriteLine(sb.ToString())  
```  
  
 <span data-ttu-id="b5de5-113">This example produces the following output:</span><span class="sxs-lookup"><span data-stu-id="b5de5-113">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b5de5-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5de5-114">See also</span></span>

- [<span data-ttu-id="b5de5-115">Serializing XML Trees (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5de5-115">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
