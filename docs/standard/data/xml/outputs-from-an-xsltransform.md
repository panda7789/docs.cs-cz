---
title: Výstupy z XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
ms.openlocfilehash: 5fa8c8228382f7f326a8d2243ed0450fca31f6fb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288690"
---
# <a name="outputs-from-an-xsltransform"></a>Výstupy z XslTransform
Vzhledem k tomu, že šablony stylů mohou určit výstupní formát pomocí `<xsl:output>` příkazu s `method` atributem, následující tabulka popisuje, co je výstupní formát při použití <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody k zápisu výstupu a výstupní formát je deklarován jako <xref:System.IO.Stream> nebo <xref:System.IO.TextWriter> .  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform>Třída je zastaralá v .NET Framework 2,0. Transformace XSLT (Extensible Stylesheet Language) můžete použít k transformaci pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy. Další informace najdete v tématu [použití třídy XslCompiledTransform](using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](migrating-from-the-xsltransform-class.md) .  
  
 Vzhledem k tomu, že šablony stylů mohou určit výstupní formát pomocí `<xsl:output>` příkazu s `method` atributem, následující tabulka popisuje, co je výstupní formát při použití <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody k zápisu výstupu a výstupní formát je deklarován jako <xref:System.IO.Stream> nebo <xref:System.IO.TextWriter> . Následující tabulka popisuje, co se stane, když je typ výstupu deklarován <xref:System.Xml.Xsl.XslTransform.Transform%2A> metodou ve spojení s použitím `<xsl:output>` příkazu:  
  
|Atribut \<xsl:output method = >|Výsledný formát|  
|-----------------------------------------|-------------------|  
|Method = "XML"|XML|  
|Metoda = "HTML"|HTML|  
|Method = "text"|Text|  
  
> [!NOTE]
> Poznámka: `<xsl:output>` příkaz je ignorován, pokud je výstupem <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XmlWriter> .  
  
 Následující atributy jsou podporovány, pokud <xref:System.Xml.Xsl.XslTransform.Transform%2A> je výstupem metody <xref:System.IO.Stream> nebo <xref:System.IO.TextWriter> :  
  
- kódování  
  
- vynechat – XML-deklarace  
  
- samostatný  
  
- DOCTYPE – veřejné  
  
- DOCTYPE – systém  
  
- CDATA-Section-Elements  
  
- rážce  
  
    > [!NOTE]
    > \*Atribut Encoding je ignorován, pokud <xref:System.Xml.Xsl.XslTransform.Transform%2A> Metoda posílá svůj výstup do <xref:System.IO.TextWriter> . Místo toho se použije vlastnost Encoding v <xref:System.IO.TextWriter> .
  
 Následující atribut je ignorován, pokud <xref:System.Xml.Xsl.XslTransform.Transform%2A> je výstupem metody <xref:System.IO.Stream> :  
  
- verze: verze je vždycky 1,0.  
  
- typ média: typ média  
  
## <a name="escaping-special-characters"></a>Speciální znaky pro uvozovací znaky  
 Tato `<xsl:text disable-output-escaping>` značka slouží k označení, zda je nutné zadat speciální znaky do formuláře XML (například pomocí `<&lt>` místo `"<"` symbolu) nebo vlevo v aktuální podmínce. `disable-output-escaping`Atribut je ignorován při transformaci na <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> objekt nebo a nemá žádný vliv na speciální znaky.  
  
## <a name="see-also"></a>Viz také

- [Třída XslTransform implementuje procesor XSLT](xsltransform-class-implements-the-xslt-processor.md)
