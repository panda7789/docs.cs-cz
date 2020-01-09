---
title: Používání třídy XslCompiledTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
ms.openlocfilehash: 8212e37171ce693ee5624541f7886ef33a33b1da
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710047"
---
# <a name="using-the-xslcompiledtransform-class"></a>Používání třídy XslCompiledTransform
Třída <xref:System.Xml.Xsl.XslCompiledTransform> je procesorem Microsoft .NET Framework XSLT. Tato třída se používá ke kompilaci šablon stylů a provádění transformací XSLT.  
  
> [!NOTE]
> I když je celkový výkon <xref:System.Xml.Xsl.XslCompiledTransform> třídy lepší než <xref:System.Xml.Xsl.XslTransform> třídy, metoda <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> třídy <xref:System.Xml.Xsl.XslCompiledTransform> může při prvním volání na transformaci pracovat pomaleji než metoda <xref:System.Xml.Xsl.XslTransform.Load%2A> třídy <xref:System.Xml.Xsl.XslTransform>. Důvodem je, že soubor XSLT musí být zkompilován před jeho načtením. Další informace najdete v tomto blogovém příspěvku: [XslCompiledTransform pomalejší než XslTransform?](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/)  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vstupy do třídy XslCompiledTransform](../../../../docs/standard/data/xml/inputs-to-the-xslcompiledtransform-class.md)  
 Popisuje dostupné možnosti vstupu XSLT.  
  
 [Možnosti výstupu na třídě XslCompiledTransform](../../../../docs/standard/data/xml/output-options-on-the-xslcompiledtransform-class.md)  
 Popisuje dostupné možnosti výstupu XSLT.  
  
 [Překlad externích prostředků během zpracování XSLT](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 Popisuje použití třídy <xref:System.Xml.XmlResolver> k překladu externích prostředků.  
  
 [Rozšíření šablon stylů XSLT](../../../../docs/standard/data/xml/extending-xslt-style-sheets.md)  
 Popisuje, jak jsou podporována rozšíření XSLT.  
  
|||  
|-|-|  
|[Chyby XSLT s možností zotavení](../../../../docs/standard/data/xml/recoverable-xslt-errors.md)|Uvádí volitelné chování, které povoluje doporučení XSLT 1,0 pro konsorcium World Wide Web (W3C) a popisuje, jak jsou tato chování zpracována <xref:System.Xml.Xsl.XslCompiledTransform> třídou.|  
|[Postupy: Transformace fragmentu uzlu](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md)|Popisuje, jak transformovat fragment uzlu.|  
  
## <a name="related-sections"></a>Související oddíly  
 [Migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 Popisuje, jak migrovat kód z <xref:System.Xml.Xsl.XslTransform> třídy.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Xsl.XsltSettings>
- <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
