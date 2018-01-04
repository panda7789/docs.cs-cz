---
title: "Třídou XMLDocument nastavenou na vstup XslTransform"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 97115892-410a-4657-ab47-1e14dfba73f8
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3900432a08bb525df75b15cf83956f3b92d96e00
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="xmldocument-input-to-xsltransform"></a>Třídou XMLDocument nastavenou na vstup XslTransform
<xref:System.Xml.XmlDocument> Třída poskytuje možnosti úprav pro dokument XML. Pokud soubor XML je nutné upravit nebo změnit před odesláním do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody načtení XML do <xref:System.Xml.XmlDocument>, upravovat a odeslat ho do <xref:System.Xml.Xsl.XslTransform>.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Můžete provést jazyk XSL pro transformace transformace XSLT () pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy. V tématu [pomocí třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.  
  
 <xref:System.Xml.XmlDocument> Implementuje <xref:System.Xml.XPath.IXPathNavigable> rozhraní, takže dokumentu se dá předat do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda po dokončení úprav.  
  
 Z důvodu úprav schopnosti produktu <xref:System.Xml.XmlDocument>pomocí <xref:System.Xml.XmlDocument> třídy jako vstup pro transformaci je pomalejší než použití <xref:System.Xml.XPath.XPathDocument> pro jazyk XSL pro transformace transformace XSLT (), jako <xref:System.Xml.XPath.XPathDocument> je optimalizované pro dotazy XML Path Language (XPath) z důvodu interní úložiště.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje jak <xref:System.Xml.XmlDocument> mohou být poskytnuty <xref:System.Xml.Xsl.XslTransform>, s výstupem posílá <xref:System.Xml.XmlReader>.  
  
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
 <xref:System.Xml.XmlDocument>  
 [Transformace XSLT s třídou XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
 [XPathNavigator v transformacích](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [XPathNodeIterator v transformacích](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [Vstup XPathDocument do XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [Vstup XmlDataDocument do XslTransform](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
