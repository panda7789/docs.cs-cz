---
title: Používání třídy XslCompiledTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ce9a06c14141bb658eb665e643d8da27e18dd94f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590365"
---
# <a name="using-the-xslcompiledtransform-class"></a>Používání třídy XslCompiledTransform
<xref:System.Xml.Xsl.XslCompiledTransform> Procesoru Microsoft .NET Framework XSLT je třída. Tato třída se používá ke kompilaci šablony stylů a provedení transformace XSLT.  
  
> [!NOTE]
>  I když celkový výkon <xref:System.Xml.Xsl.XslCompiledTransform> třída je lepší, než <xref:System.Xml.Xsl.XslTransform> třídy, <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metodu <xref:System.Xml.Xsl.XslCompiledTransform> třídy můžou provádět více pomalu než <xref:System.Xml.Xsl.XslTransform.Load%2A> metodu <xref:System.Xml.Xsl.XslTransform> třída první, když je volán na transformaci. Je to proto musí být kompilován soubor XSLT, předtím, než je načten. Další informace najdete v následujícím blogovém příspěvku: [Pomalejší než XslTransform XslCompiledTransform?](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/)  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vstupy do třídy XslCompiledTransform](../../../../docs/standard/data/xml/inputs-to-the-xslcompiledtransform-class.md)  
 Popisuje dostupné možnosti vstupu XSLT.  
  
 [Možnosti výstupu na třídě XslCompiledTransform](../../../../docs/standard/data/xml/output-options-on-the-xslcompiledtransform-class.md)  
 Popisuje dostupné možnosti výstup XSLT.  
  
 [Překlad externích prostředků během zpracování XSLT](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 Popisuje použití <xref:System.Xml.XmlResolver> třídy k vyřešení externích prostředků.  
  
 [Rozšíření šablon stylů XSLT](../../../../docs/standard/data/xml/extending-xslt-style-sheets.md)  
 Tento článek popisuje, jak jsou podporovány přípony XSLT.  
  
|||  
|-|-|  
|[Chyby XSLT s možností zotavení](../../../../docs/standard/data/xml/recoverable-xslt-errors.md)|Volitelného chování dovolují XSLT World Wide Web Consortium (W3C) 1.0 doporučení uvádí a popisuje, jak jsou zpracovávány těchto projevů <xref:System.Xml.Xsl.XslCompiledTransform> třídy.|  
|[Postupy: Transformace fragmentu uzlu](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md)|Popisuje, jak transformace fragmentu uzlu.|  
  
## <a name="related-sections"></a>Související oddíly  
 [Migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 Tento článek popisuje postup migrace kódu z <xref:System.Xml.Xsl.XslTransform> třídy  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Xsl.XsltSettings>
- <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
