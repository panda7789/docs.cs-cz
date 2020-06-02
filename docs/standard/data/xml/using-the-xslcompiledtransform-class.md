---
title: Používání třídy XslCompiledTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
ms.openlocfilehash: 8705b4c6324ce20a1f37d3ee864ab494adcdd6a5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281764"
---
# <a name="using-the-xslcompiledtransform-class"></a>Používání třídy XslCompiledTransform
<xref:System.Xml.Xsl.XslCompiledTransform>Třída je procesorem Microsoft .NET Framework XSLT. Tato třída se používá ke kompilaci šablon stylů a provádění transformací XSLT.  
  
> [!NOTE]
> I když je celkový výkon <xref:System.Xml.Xsl.XslCompiledTransform> třídy lepší než <xref:System.Xml.Xsl.XslTransform> třída, <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> Metoda <xref:System.Xml.Xsl.XslCompiledTransform> třídy může při prvním volání transformace pracovat pomaleji než <xref:System.Xml.Xsl.XslTransform.Load%2A> Metoda <xref:System.Xml.Xsl.XslTransform> třídy. Důvodem je, že soubor XSLT musí být zkompilován před jeho načtením. Další informace najdete v tomto blogovém příspěvku: [XslCompiledTransform pomalejší než XslTransform?](https://docs.microsoft.com/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vstupy do třídy XslCompiledTransform](inputs-to-the-xslcompiledtransform-class.md)  
 Popisuje dostupné možnosti vstupu XSLT.  
  
 [Možnosti výstupu na třídě XslCompiledTransform](output-options-on-the-xslcompiledtransform-class.md)  
 Popisuje dostupné možnosti výstupu XSLT.  
  
 [Překlad externích prostředků během zpracování XSLT](resolving-external-resources-during-xslt-processing.md)  
 Popisuje použití <xref:System.Xml.XmlResolver> třídy k překladu externích prostředků.  
  
 [Rozšíření šablon stylů XSLT](extending-xslt-style-sheets.md)  
 Popisuje, jak jsou podporována rozšíření XSLT.  
  
|||  
|-|-|  
|[Chyby XSLT s možností zotavení](recoverable-xslt-errors.md)|Uvádí volitelné chování, které povoluje doporučení konsorcium World Wide Web (W3C) XSLT 1,0, a popisuje, jak toto chování zpracovává <xref:System.Xml.Xsl.XslCompiledTransform> Třída.|  
|[Postupy: Transformace fragmentu uzlu](how-to-transform-a-node-fragment.md)|Popisuje, jak transformovat fragment uzlu.|  
  
## <a name="related-sections"></a>Související oddíly  
 [Migrace z třídy XslTransform](migrating-from-the-xsltransform-class.md)  
 Popisuje, jak migrovat kód z <xref:System.Xml.Xsl.XslTransform> třídy.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.Xsl.XsltSettings>
- <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
