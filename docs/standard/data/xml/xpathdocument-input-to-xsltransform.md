---
title: Vstup XPathDocument do XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 7d1bbe8b-ed43-4e62-a5ba-d602d244f4ae
ms.openlocfilehash: e19e0d18dc0f4aceb38bf006c3b9b80276455510
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709761"
---
# <a name="xpathdocument-input-to-xsltransform"></a>Vstup XPathDocument do XslTransform
Je <xref:System.Xml.XPath.XPathDocument> mezipaměť jen pro čtení, která slouží ke zpracování dokumentů pomocí <xref:System.Xml.Xsl.XslTransform>. Je strukturálně podobně jako XML model DOM (Document Object Model) (DOM), ale je vysoce optimalizovaný pro zpracování transformací XSLT (Extensible Stylesheet Language) a datový model jazyka XML Path (XPath) pomocí funkcí optimalizace XPath na <xref:System.Xml.XPath.XPathNavigator>.  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá v .NET Framework 2,0. Transformace XSLT (Extensible Stylesheet Language) můžete použít k <xref:System.Xml.Xsl.XslCompiledTransform> transformaci pomocí třídy. Další informace najdete v tématu [použití třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 Následující ukázka kódu vytvoří transformaci <xref:System.Xml.XPath.XPathDocument> jako vstup do transformace.  
  
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

- [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
