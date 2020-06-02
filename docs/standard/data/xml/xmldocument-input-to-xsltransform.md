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
# <a name="xmldocument-input-to-xsltransform"></a>Vstup XmlDocument do XslTransform
<xref:System.Xml.XmlDocument>Třída poskytuje možnosti úprav dokumentu XML. Pokud je nutné XML upravit nebo upravit před odesláním do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody, načtěte XML do <xref:System.Xml.XmlDocument> , upravte jej a odešlete do <xref:System.Xml.Xsl.XslTransform> .  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform>Třída je zastaralá v .NET Framework 2,0. Transformace XSLT (Extensible Stylesheet Language) můžete použít k transformaci pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy. Další informace najdete v tématu [použití třídy XslCompiledTransform](using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](migrating-from-the-xsltransform-class.md) .  
  
 <xref:System.Xml.XmlDocument>Implementuje <xref:System.Xml.XPath.IXPathNavigable> rozhraní, aby bylo možné dokument předat <xref:System.Xml.Xsl.XslTransform.Transform%2A> metodě po úpravě.  
  
 Vzhledem k možnosti úprav objektu je <xref:System.Xml.XmlDocument> použití <xref:System.Xml.XmlDocument> třídy jako vstupu do transformace pomalejší než použití <xref:System.Xml.XPath.XPathDocument> pro transformace XSLT (Extensible Stylesheet Language), protože <xref:System.Xml.XPath.XPathDocument> je optimalizována pro dotazy jazyka XML Path (XPath) z důvodu interního úložiště.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje <xref:System.Xml.XmlDocument> , jak lze dodávat do <xref:System.Xml.Xsl.XslTransform> , s výstupem odeslaným do <xref:System.Xml.XmlReader> .  
  
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
- [Transformace XSLT s třídou XslTransform](xslt-transformations-with-the-xsltransform-class.md)
- [Třída XslTransform implementuje procesor XSLT](xsltransform-class-implements-the-xslt-processor.md)
- [XPathNavigator v transformacích](xpathnavigator-in-transformations.md)
- [XPathNodeIterator v transformacích](xpathnodeiterator-in-transformations.md)
- [Vstup XPathDocument do XslTransform](xpathdocument-input-to-xsltransform.md)
- [Vstup XmlDataDocument do XslTransform](xmldatadocument-input-to-xsltransform.md)
