---
title: Používání třídy XslCompiledTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a524b80d8789567dc2aa943d7321fd49fe3c7c33
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939421"
---
# <a name="using-the-xslcompiledtransform-class"></a>Používání třídy XslCompiledTransform
<xref:System.Xml.Xsl.XslCompiledTransform> Třída je procesorem Microsoft .NET Framework XSLT. Tato třída se používá ke kompilaci šablon stylů a provádění transformací XSLT.  
  
> [!NOTE]
> I <xref:System.Xml.Xsl.XslCompiledTransform> když je celkový výkon třídy lepší <xref:System.Xml.Xsl.XslTransform> než třída <xref:System.Xml.Xsl.XslCompiledTransform> , <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metoda třídy může při prvním výskytu <xref:System.Xml.Xsl.XslTransform.Load%2A> <xref:System.Xml.Xsl.XslTransform> metody provádět pomaleji než metoda třídy. je volána pro transformaci. Důvodem je, že soubor XSLT musí být zkompilován před jeho načtením. Další informace najdete v tomto blogovém příspěvku: [XslCompiledTransform pomaleji než XslTransform?](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/)  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vstupy do třídy XslCompiledTransform](../../../../docs/standard/data/xml/inputs-to-the-xslcompiledtransform-class.md)  
 Popisuje dostupné možnosti vstupu XSLT.  
  
 [Možnosti výstupu na třídě XslCompiledTransform](../../../../docs/standard/data/xml/output-options-on-the-xslcompiledtransform-class.md)  
 Popisuje dostupné možnosti výstupu XSLT.  
  
 [Překlad externích prostředků během zpracování XSLT](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 Popisuje použití <xref:System.Xml.XmlResolver> třídy k překladu externích prostředků.  
  
 [Rozšíření šablon stylů XSLT](../../../../docs/standard/data/xml/extending-xslt-style-sheets.md)  
 Popisuje, jak jsou podporována rozšíření XSLT.  
  
|||  
|-|-|  
|[Chyby XSLT s možností zotavení](../../../../docs/standard/data/xml/recoverable-xslt-errors.md)|Uvádí volitelné chování, které povoluje doporučení konsorcium World Wide Web (W3C) XSLT 1,0, a popisuje, jak toto chování zpracovává <xref:System.Xml.Xsl.XslCompiledTransform> třída.|  
|[Postupy: Transformace fragmentu uzlu](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md)|Popisuje, jak transformovat fragment uzlu.|  
  
## <a name="related-sections"></a>Související oddíly  
 [Migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 Popisuje, jak migrovat kód z <xref:System.Xml.Xsl.XslTransform> třídy.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Xsl.XsltSettings>
- <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
