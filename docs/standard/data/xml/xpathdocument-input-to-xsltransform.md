---
title: Vstup XPathDocument XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 7d1bbe8b-ed43-4e62-a5ba-d602d244f4ae
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 030f1117cc7974b4b5d85b35b14a8d0dbc3d87cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569782"
---
# <a name="xpathdocument-input-to-xsltransform"></a>Vstup XPathDocument XslTransform
<xref:System.Xml.XPath.XPathDocument> Je jen pro čtení mezipaměti pro zpracování dokumentů s <xref:System.Xml.Xsl.XslTransform>. Je strukturálně podobné k XML modelu DOM (Document Object), ale je vysoce optimalizovaný pro jazyk XSL pro zpracování transformace XSLT () a datový model XML Path Language (XPath) pomocí funkcí optimalizace XPath na <xref:System.Xml.XPath.XPathNavigator>.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Můžete provést jazyk XSL pro transformace transformace XSLT () pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy. V tématu [pomocí třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.  
  
 Následující příklad kódu vytvoří <xref:System.Xml.XPath.XPathDocument> jako vstup pro transformace.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
