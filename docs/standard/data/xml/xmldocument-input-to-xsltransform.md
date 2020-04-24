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
# <a name="xmldocument-input-to-xsltransform"></a>Vstup XmlDocument do XslTransform
<xref:System.Xml.XmlDocument> Třída poskytuje možnosti úprav dokumentu XML. Pokud je nutné XML upravit nebo upravit před odesláním do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody, načtěte XML do <xref:System.Xml.XmlDocument>, upravte jej a odešlete do. <xref:System.Xml.Xsl.XslTransform>  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá v .NET Framework 2,0. Transformace XSLT (Extensible Stylesheet Language) můžete použít k <xref:System.Xml.Xsl.XslCompiledTransform> transformaci pomocí třídy. Další informace najdete v tématu [použití třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 Implementuje rozhraní, aby bylo možné dokument předat <xref:System.Xml.Xsl.XslTransform.Transform%2A> metodě po úpravě. <xref:System.Xml.XPath.IXPathNavigable> <xref:System.Xml.XmlDocument>  
  
 Vzhledem k <xref:System.Xml.XmlDocument>možnosti úprav objektu je použití <xref:System.Xml.XmlDocument> třídy jako vstupu do transformace pomalejší než použití <xref:System.Xml.XPath.XPathDocument> pro transformace XSLT (Extensible Stylesheet Language), protože <xref:System.Xml.XPath.XPathDocument> je optimalizována pro dotazy jazyka XML Path (XPath) z důvodu interního úložiště.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje <xref:System.Xml.XmlDocument> <xref:System.Xml.Xsl.XslTransform>, jak lze dodávat do, s výstupem odeslaným do. <xref:System.Xml.XmlReader>  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.XmlDocument>
- [Transformace XSLT s třídou XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
- [XPathNavigator v transformacích](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [XPathNodeIterator v transformacích](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [Vstup XPathDocument do XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [Vstup XmlDataDocument do XslTransform](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
