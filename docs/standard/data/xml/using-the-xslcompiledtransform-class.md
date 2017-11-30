---
title: "Používání třídy XslCompiledTransform"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5a5c71a7796790343bf39de5bbfd03997c25d5f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-the-xslcompiledtransform-class"></a>Používání třídy XslCompiledTransform
<xref:System.Xml.Xsl.XslCompiledTransform> Třída je Microsoft .NET Framework XSLT procesoru. Tato třída se používá pro kompilaci šablony stylů a provést transformace XSLT.  
  
> [!NOTE]
>  I když celkový výkon <xref:System.Xml.Xsl.XslCompiledTransform> třída je lepší, než <xref:System.Xml.Xsl.XslTransform> třídy, <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metodu <xref:System.Xml.Xsl.XslCompiledTransform> třída může provádět další pomalu než <xref:System.Xml.Xsl.XslTransform.Load%2A> metodu <xref:System.Xml.Xsl.XslTransform> třída první, když je volána na transformaci. Je to proto, že soubor XSLT musí být zkompilovány, než je načten. Další informace najdete v příspěvku blogu: [XslCompiledTransform nižší než XslTransform?](http://go.microsoft.com/fwlink/?LinkId=130590)  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vstupy XslCompiledTransform – třída](../../../../docs/standard/data/xml/inputs-to-the-xslcompiledtransform-class.md)  
 Popisuje dostupné možnosti vstupní XSLT.  
  
 [Možnosti výstupu na XslCompiledTransform – třída](../../../../docs/standard/data/xml/output-options-on-the-xslcompiledtransform-class.md)  
 Popisuje dostupné možnosti výstupu XSLT.  
  
 [Řešení externím prostředkům během zpracování XSLT](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 Popisuje použití <xref:System.Xml.XmlResolver> třída přeložit externí zdroje.  
  
 [Rozšíření šablony stylů XSLT](../../../../docs/standard/data/xml/extending-xslt-style-sheets.md)  
 Popisuje, jak jsou podporovány XSLT rozšíření.  
  
|||  
|-|-|  
|[Chyby obnovitelné XSLT](../../../../docs/standard/data/xml/recoverable-xslt-errors.md)|Volitelné chování povolenou XSLT World Wide Web Consortium (W3C) 1.0 doporučení uvádí a popisuje, jak jsou zpracovávány těchto projevů <xref:System.Xml.Xsl.XslCompiledTransform> třídy.|  
|[Postupy: transformace Fragment uzlu](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md)|Popisuje, jak k transformaci fragment uzlu.|  
  
## <a name="related-sections"></a>Související oddíly  
 [Migrace z XslTransform – třída](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 Popisuje, jak do migrace kódu z <xref:System.Xml.Xsl.XslTransform> – třída  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Xsl.XsltSettings>  
 <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
