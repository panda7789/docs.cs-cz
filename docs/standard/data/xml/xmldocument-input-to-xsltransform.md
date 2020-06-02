---
title: Vstup XmlDocument do XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 97115892-410a-4657-ab47-1e14dfba73f8
ms.openlocfilehash: e990c8ca3bb2a7145157fcedd06da4ea769c6ad3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290250"
---
# <a name="xmldocument-input-to-xsltransform"></a><span data-ttu-id="36744-102">Vstup XmlDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="36744-102">XmlDocument Input to XslTransform</span></span>
<span data-ttu-id="36744-103"><xref:System.Xml.XmlDocument>Třída poskytuje možnosti úprav dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="36744-103">The <xref:System.Xml.XmlDocument> class provides editing capabilities for an XML document.</span></span> <span data-ttu-id="36744-104">Pokud je nutné XML upravit nebo upravit před odesláním do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody, načtěte XML do <xref:System.Xml.XmlDocument> , upravte jej a odešlete do <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="36744-104">If the XML needs to be edited or modified before being sent to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, load the XML into an <xref:System.Xml.XmlDocument>, edit it, and send it in to the <xref:System.Xml.Xsl.XslTransform>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="36744-105"><xref:System.Xml.Xsl.XslTransform>Třída je zastaralá v .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="36744-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="36744-106">Transformace XSLT (Extensible Stylesheet Language) můžete použít k transformaci pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="36744-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="36744-107">Další informace najdete v tématu [použití třídy XslCompiledTransform](using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="36744-107">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="36744-108"><xref:System.Xml.XmlDocument>Implementuje <xref:System.Xml.XPath.IXPathNavigable> rozhraní, aby bylo možné dokument předat <xref:System.Xml.Xsl.XslTransform.Transform%2A> metodě po úpravě.</span><span class="sxs-lookup"><span data-stu-id="36744-108">The <xref:System.Xml.XmlDocument> implements the <xref:System.Xml.XPath.IXPathNavigable> interface, so the document can be passed to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method after editing.</span></span>  
  
 <span data-ttu-id="36744-109">Vzhledem k možnosti úprav objektu je <xref:System.Xml.XmlDocument> použití <xref:System.Xml.XmlDocument> třídy jako vstupu do transformace pomalejší než použití <xref:System.Xml.XPath.XPathDocument> pro transformace XSLT (Extensible Stylesheet Language), protože <xref:System.Xml.XPath.XPathDocument> je optimalizována pro dotazy jazyka XML Path (XPath) z důvodu interního úložiště.</span><span class="sxs-lookup"><span data-stu-id="36744-109">Due to the editing capability of the <xref:System.Xml.XmlDocument>, using the <xref:System.Xml.XmlDocument> class as input to a transformation is slower than using an <xref:System.Xml.XPath.XPathDocument> for the Extensible Stylesheet Language for Transformations (XSLT) transformations, as the <xref:System.Xml.XPath.XPathDocument> is optimized for XML Path Language (XPath) queries due to the internal storage.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36744-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="36744-110">Example</span></span>  
 <span data-ttu-id="36744-111">Následující příklad kódu ukazuje <xref:System.Xml.XmlDocument> , jak lze dodávat do <xref:System.Xml.Xsl.XslTransform> , s výstupem odeslaným do <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="36744-111">The following code example shows how an <xref:System.Xml.XmlDocument> can be supplied to the <xref:System.Xml.Xsl.XslTransform>, with the output sent to an <xref:System.Xml.XmlReader>.</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.Load("books.xml")  
Dim trans As XslTransform = new XslTransform()  
trans.Load("book.xsl")  
Dim rdr As XmlReader = trans.Transform(doc, Nothing, Nothing)  
while (rdr.Read())  
end while  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.Load("books.xml");  
XslTransform trans = new XslTransform();  
trans.Load("book.xsl");  
XmlReader rdr = trans.Transform(doc, null, null);  
while (rdr.Read()) {}  
```  
  
## <a name="see-also"></a><span data-ttu-id="36744-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="36744-112">See also</span></span>

- <xref:System.Xml.XmlDocument>
- [<span data-ttu-id="36744-113">Transformace XSLT s třídou XslTransform</span><span class="sxs-lookup"><span data-stu-id="36744-113">XSLT Transformations with the XslTransform Class</span></span>](xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="36744-114">Třída XslTransform implementuje procesor XSLT</span><span class="sxs-lookup"><span data-stu-id="36744-114">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
- [<span data-ttu-id="36744-115">XPathNavigator v transformacích</span><span class="sxs-lookup"><span data-stu-id="36744-115">XPathNavigator in Transformations</span></span>](xpathnavigator-in-transformations.md)
- [<span data-ttu-id="36744-116">XPathNodeIterator v transformacích</span><span class="sxs-lookup"><span data-stu-id="36744-116">XPathNodeIterator in Transformations</span></span>](xpathnodeiterator-in-transformations.md)
- [<span data-ttu-id="36744-117">Vstup XPathDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="36744-117">XPathDocument Input to XslTransform</span></span>](xpathdocument-input-to-xsltransform.md)
- [<span data-ttu-id="36744-118">Vstup XmlDataDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="36744-118">XmlDataDocument Input to XslTransform</span></span>](xmldatadocument-input-to-xsltransform.md)
