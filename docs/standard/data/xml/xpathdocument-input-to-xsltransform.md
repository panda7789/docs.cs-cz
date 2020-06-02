---
title: Vstup XPathDocument do XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 7d1bbe8b-ed43-4e62-a5ba-d602d244f4ae
ms.openlocfilehash: 66cdbae8b52ca1b7ed46e8f040fcbf51c969dea2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282971"
---
# <a name="xpathdocument-input-to-xsltransform"></a><span data-ttu-id="0676c-102">Vstup XPathDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="0676c-102">XPathDocument Input to XslTransform</span></span>
<span data-ttu-id="0676c-103"><xref:System.Xml.XPath.XPathDocument>Je mezipaměť jen pro čtení, která slouží ke zpracování dokumentů pomocí <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="0676c-103">The <xref:System.Xml.XPath.XPathDocument> is a read-only cache, for processing documents with <xref:System.Xml.Xsl.XslTransform>.</span></span> <span data-ttu-id="0676c-104">Je strukturálně podobně jako XML model DOM (Document Object Model) (DOM), ale je vysoce optimalizovaný pro zpracování transformací XSLT (Extensible Stylesheet Language) a datový model jazyka XML Path (XPath) pomocí funkcí optimalizace XPath na <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="0676c-104">It is structurally similar to the XML Document Object Model (DOM), but it is highly optimized for Extensible Stylesheet Language for Transformations (XSLT) processing and the XML Path Language (XPath) data model using the XPath optimization functions on the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0676c-105"><xref:System.Xml.Xsl.XslTransform>Třída je zastaralá v .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="0676c-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="0676c-106">Transformace XSLT (Extensible Stylesheet Language) můžete použít k transformaci pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="0676c-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="0676c-107">Další informace najdete v tématu [použití třídy XslCompiledTransform](using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="0676c-107">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="0676c-108">Následující ukázka kódu vytvoří <xref:System.Xml.XPath.XPathDocument> transformaci jako vstup do transformace.</span><span class="sxs-lookup"><span data-stu-id="0676c-108">The following code sample creates an <xref:System.Xml.XPath.XPathDocument> as input to a transform.</span></span>  
  
```vb  
Dim xslt as XslTransform = new XslTransform()  
Xslt.Load(someStylesheet)  
Dim doc as XPathDocument = New XPathDocument("books.xml")  
Dim fs as StringWriter = new StringWriter()  
Xslt.Transform(doc, Nothing, fs, Nothing);  
```  
  
```csharp  
XslTransform xslt = new XslTransform();  
Xslt.Load(someStylesheet);  
XPathDocument doc = XPathDocument("books.xml");  
StringWriter fs = new StringWriter();  
Xslt.Transform(doc, null, fs, null);  
```  
  
## <a name="see-also"></a><span data-ttu-id="0676c-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="0676c-109">See also</span></span>

- [<span data-ttu-id="0676c-110">Třída XslTransform implementuje procesor XSLT</span><span class="sxs-lookup"><span data-stu-id="0676c-110">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
