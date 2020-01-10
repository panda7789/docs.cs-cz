---
title: Vstup XmlDocument do XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 97115892-410a-4657-ab47-1e14dfba73f8
ms.openlocfilehash: c7819c3cb6b1430dcdb8a78c43f7138f64e691a8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709839"
---
# <a name="xmldocument-input-to-xsltransform"></a><span data-ttu-id="34576-102">Vstup XmlDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="34576-102">XmlDocument Input to XslTransform</span></span>
<span data-ttu-id="34576-103">Třída <xref:System.Xml.XmlDocument> poskytuje možnosti úprav dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="34576-103">The <xref:System.Xml.XmlDocument> class provides editing capabilities for an XML document.</span></span> <span data-ttu-id="34576-104">Pokud je nutné XML upravit nebo upravit před odesláním do metody <xref:System.Xml.Xsl.XslTransform.Transform%2A>, načtěte XML do <xref:System.Xml.XmlDocument>, upravte jej a odešlete ho do <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="34576-104">If the XML needs to be edited or modified before being sent to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, load the XML into an <xref:System.Xml.XmlDocument>, edit it, and send it in to the <xref:System.Xml.Xsl.XslTransform>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34576-105">Třída <xref:System.Xml.Xsl.XslTransform> je v .NET Framework 2,0 zastaralá.</span><span class="sxs-lookup"><span data-stu-id="34576-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="34576-106">Pomocí třídy <xref:System.Xml.Xsl.XslCompiledTransform> můžete provádět transformace XSLT (Extensible Stylesheet Language).</span><span class="sxs-lookup"><span data-stu-id="34576-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="34576-107">Další informace najdete v tématu [použití třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="34576-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="34576-108"><xref:System.Xml.XmlDocument> implementuje rozhraní <xref:System.Xml.XPath.IXPathNavigable>, aby bylo možné dokument před úpravou předat metodě <xref:System.Xml.Xsl.XslTransform.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="34576-108">The <xref:System.Xml.XmlDocument> implements the <xref:System.Xml.XPath.IXPathNavigable> interface, so the document can be passed to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method after editing.</span></span>  
  
 <span data-ttu-id="34576-109">Vzhledem k možnosti úprav <xref:System.Xml.XmlDocument>, použití <xref:System.Xml.XmlDocument> třídy jako vstupu transformace je pomalejší než použití <xref:System.Xml.XPath.XPathDocument> pro transformace XSLT (Extensible Stylesheet Language), protože <xref:System.Xml.XPath.XPathDocument> je optimalizována pro dotazy jazyka XML Path (XPath) z důvodu interního úložiště.</span><span class="sxs-lookup"><span data-stu-id="34576-109">Due to the editing capability of the <xref:System.Xml.XmlDocument>, using the <xref:System.Xml.XmlDocument> class as input to a transformation is slower than using an <xref:System.Xml.XPath.XPathDocument> for the Extensible Stylesheet Language for Transformations (XSLT) transformations, as the <xref:System.Xml.XPath.XPathDocument> is optimized for XML Path Language (XPath) queries due to the internal storage.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34576-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="34576-110">Example</span></span>  
 <span data-ttu-id="34576-111">Následující příklad kódu ukazuje, jak lze <xref:System.Xml.XmlDocument> dodávat do <xref:System.Xml.Xsl.XslTransform>s výstupem odesílaným do <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="34576-111">The following code example shows how an <xref:System.Xml.XmlDocument> can be supplied to the <xref:System.Xml.Xsl.XslTransform>, with the output sent to an <xref:System.Xml.XmlReader>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="34576-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="34576-112">See also</span></span>

- <xref:System.Xml.XmlDocument>
- [<span data-ttu-id="34576-113">Transformace XSLT s třídou XslTransform</span><span class="sxs-lookup"><span data-stu-id="34576-113">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="34576-114">Třída XslTransform implementuje procesor XSLT</span><span class="sxs-lookup"><span data-stu-id="34576-114">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
- [<span data-ttu-id="34576-115">XPathNavigator v transformacích</span><span class="sxs-lookup"><span data-stu-id="34576-115">XPathNavigator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [<span data-ttu-id="34576-116">XPathNodeIterator v transformacích</span><span class="sxs-lookup"><span data-stu-id="34576-116">XPathNodeIterator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [<span data-ttu-id="34576-117">Vstup XPathDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="34576-117">XPathDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [<span data-ttu-id="34576-118">Vstup XmlDataDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="34576-118">XmlDataDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
