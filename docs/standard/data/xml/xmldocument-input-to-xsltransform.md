---
title: Třídou XMLDocument nastavenou na vstup XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 97115892-410a-4657-ab47-1e14dfba73f8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3179425597173e09a8c1ef1fbdfc582f8f4538e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570595"
---
# <a name="xmldocument-input-to-xsltransform"></a><span data-ttu-id="663d5-102">Třídou XMLDocument nastavenou na vstup XslTransform</span><span class="sxs-lookup"><span data-stu-id="663d5-102">XmlDocument Input to XslTransform</span></span>
<span data-ttu-id="663d5-103"><xref:System.Xml.XmlDocument> Třída poskytuje možnosti úprav pro dokument XML.</span><span class="sxs-lookup"><span data-stu-id="663d5-103">The <xref:System.Xml.XmlDocument> class provides editing capabilities for an XML document.</span></span> <span data-ttu-id="663d5-104">Pokud soubor XML je nutné upravit nebo změnit před odesláním do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody načtení XML do <xref:System.Xml.XmlDocument>, upravovat a odeslat ho do <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="663d5-104">If the XML needs to be edited or modified before being sent to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, load the XML into an <xref:System.Xml.XmlDocument>, edit it, and send it in to the <xref:System.Xml.Xsl.XslTransform>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="663d5-105"><xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="663d5-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="663d5-106">Můžete provést jazyk XSL pro transformace transformace XSLT () pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="663d5-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="663d5-107">V tématu [pomocí třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="663d5-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="663d5-108"><xref:System.Xml.XmlDocument> Implementuje <xref:System.Xml.XPath.IXPathNavigable> rozhraní, takže dokumentu se dá předat do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda po dokončení úprav.</span><span class="sxs-lookup"><span data-stu-id="663d5-108">The <xref:System.Xml.XmlDocument> implements the <xref:System.Xml.XPath.IXPathNavigable> interface, so the document can be passed to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method after editing.</span></span>  
  
 <span data-ttu-id="663d5-109">Z důvodu úprav schopnosti produktu <xref:System.Xml.XmlDocument>pomocí <xref:System.Xml.XmlDocument> třídy jako vstup pro transformaci je pomalejší než použití <xref:System.Xml.XPath.XPathDocument> pro jazyk XSL pro transformace transformace XSLT (), jako <xref:System.Xml.XPath.XPathDocument> je optimalizované pro dotazy XML Path Language (XPath) z důvodu interní úložiště.</span><span class="sxs-lookup"><span data-stu-id="663d5-109">Due to the editing capability of the <xref:System.Xml.XmlDocument>, using the <xref:System.Xml.XmlDocument> class as input to a transformation is slower than using an <xref:System.Xml.XPath.XPathDocument> for the Extensible Stylesheet Language for Transformations (XSLT) transformations, as the <xref:System.Xml.XPath.XPathDocument> is optimized for XML Path Language (XPath) queries due to the internal storage.</span></span>  
  
## <a name="example"></a><span data-ttu-id="663d5-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="663d5-110">Example</span></span>  
 <span data-ttu-id="663d5-111">Následující příklad kódu ukazuje jak <xref:System.Xml.XmlDocument> mohou být poskytnuty <xref:System.Xml.Xsl.XslTransform>, s výstupem posílá <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="663d5-111">The following code example shows how an <xref:System.Xml.XmlDocument> can be supplied to the <xref:System.Xml.Xsl.XslTransform>, with the output sent to an <xref:System.Xml.XmlReader>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="663d5-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="663d5-112">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 [<span data-ttu-id="663d5-113">Transformace XSLT s třídou XslTransform</span><span class="sxs-lookup"><span data-stu-id="663d5-113">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [<span data-ttu-id="663d5-114">Třída XslTransform implementuje procesor XSLT</span><span class="sxs-lookup"><span data-stu-id="663d5-114">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
 [<span data-ttu-id="663d5-115">XPathNavigator v transformacích</span><span class="sxs-lookup"><span data-stu-id="663d5-115">XPathNavigator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [<span data-ttu-id="663d5-116">XPathNodeIterator v transformacích</span><span class="sxs-lookup"><span data-stu-id="663d5-116">XPathNodeIterator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [<span data-ttu-id="663d5-117">Vstup XPathDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="663d5-117">XPathDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [<span data-ttu-id="663d5-118">Vstup XmlDataDocument do XslTransform</span><span class="sxs-lookup"><span data-stu-id="663d5-118">XmlDataDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
