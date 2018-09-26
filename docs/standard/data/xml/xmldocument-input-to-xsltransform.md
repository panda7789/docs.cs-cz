---
title: Vstup XmlDocument do XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 97115892-410a-4657-ab47-1e14dfba73f8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e83cf82aee57b1f40f695700d8d0b38c12e0ac39
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47108881"
---
# <a name="xmldocument-input-to-xsltransform"></a>Vstup XmlDocument do XslTransform
<xref:System.Xml.XmlDocument> Třída poskytuje možnosti úprav pro dokument XML. Pokud XML se musí upravit nebo změnit před odesláním do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody načtení XML do <xref:System.Xml.XmlDocument>, upravit ji a odeslat ho do <xref:System.Xml.Xsl.XslTransform>.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Můžete provádět rozšiřitelný jazyk šablony stylů transformace XSLT () transformaci pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy. Zobrazit [používání třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.  
  
 <xref:System.Xml.XmlDocument> Implementuje <xref:System.Xml.XPath.IXPathNavigable> rozhraní, tak může být předán dokumentu <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda po dokončení úprav.  
  
 Z důvodu úprav schopnost <xref:System.Xml.XmlDocument>s použitím <xref:System.Xml.XmlDocument> třídy jako vstup pro transformaci je nižší než při použití <xref:System.Xml.XPath.XPathDocument> pro rozšiřitelné jazyk šablony stylů transformace XSLT () transformaci jako <xref:System.Xml.XPath.XPathDocument> je optimalizované pro dotazy jazyk XML Path (XPath) z důvodu interní úložiště.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje jak <xref:System.Xml.XmlDocument> mohou být poskytnuty <xref:System.Xml.Xsl.XslTransform>, s výstupem odesílat <xref:System.Xml.XmlReader>.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlDocument>  
- [Transformace XSLT s třídou XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
- [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
- [XPathNavigator v transformacích](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
- [XPathNodeIterator v transformacích](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
- [Vstup XPathDocument do XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
- [Vstup XmlDataDocument do XslTransform](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
