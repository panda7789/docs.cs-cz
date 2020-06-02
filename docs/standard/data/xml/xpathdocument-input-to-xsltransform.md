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
# <a name="xpathdocument-input-to-xsltransform"></a>Vstup XPathDocument do XslTransform
<xref:System.Xml.XPath.XPathDocument>Je mezipaměť jen pro čtení, která slouží ke zpracování dokumentů pomocí <xref:System.Xml.Xsl.XslTransform> . Je strukturálně podobně jako XML model DOM (Document Object Model) (DOM), ale je vysoce optimalizovaný pro zpracování transformací XSLT (Extensible Stylesheet Language) a datový model jazyka XML Path (XPath) pomocí funkcí optimalizace XPath na <xref:System.Xml.XPath.XPathNavigator> .  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform>Třída je zastaralá v .NET Framework 2,0. Transformace XSLT (Extensible Stylesheet Language) můžete použít k transformaci pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy. Další informace najdete v tématu [použití třídy XslCompiledTransform](using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](migrating-from-the-xsltransform-class.md) .  
  
 Následující ukázka kódu vytvoří <xref:System.Xml.XPath.XPathDocument> transformaci jako vstup do transformace.  
  
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

- [Třída XslTransform implementuje procesor XSLT](xsltransform-class-implements-the-xslt-processor.md)
