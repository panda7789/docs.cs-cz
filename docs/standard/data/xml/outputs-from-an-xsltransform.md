---
title: Výstupy z XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
ms.openlocfilehash: 93cbf7807630a605e17e7f513055c052aad0d08e
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159634"
---
# <a name="outputs-from-an-xsltransform"></a>Výstupy z XslTransform
Vzhledem k tomu, že šablony stylů mohou určit výstupní `<xsl:output>` formát pomocí příkazu `method` s atributem, následující tabulka popisuje, co je výstupní formát při <xref:System.Xml.Xsl.XslTransform.Transform%2A> použití metody k zápisu výstupu a výstupní formát je deklarován jako <xref:System.IO.Stream> nebo. <xref:System.IO.TextWriter>  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá v .NET Framework 2,0. Transformace XSLT (Extensible Stylesheet Language) můžete použít k <xref:System.Xml.Xsl.XslCompiledTransform> transformaci pomocí třídy. Další informace najdete v tématu [použití třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 Vzhledem k tomu, že šablony stylů mohou určit výstupní `<xsl:output>` formát pomocí příkazu `method` s atributem, následující tabulka popisuje, co je výstupní formát při <xref:System.Xml.Xsl.XslTransform.Transform%2A> použití metody k zápisu výstupu a výstupní formát je deklarován jako <xref:System.IO.Stream> nebo. <xref:System.IO.TextWriter> Následující tabulka popisuje, co se stane, když je typ výstupu deklarován <xref:System.Xml.Xsl.XslTransform.Transform%2A> metodou ve spojení s použitím `<xsl:output>` příkazu:  
  
|\<XSL: Output – metoda = > – atribut|Výsledný formát|  
|-----------------------------------------|-------------------|  
|Method = "XML"|XML|  
|Metoda = "HTML"|HTML|  
|Method = "text"|Text|  
  
> [!NOTE]
> Poznámka: `<xsl:output>` příkaz je ignorován, pokud je výstupem <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody <xref:System.Xml.XmlReader> nebo. <xref:System.Xml.XmlWriter>  
  
 Následující atributy jsou podporovány, pokud je <xref:System.Xml.Xsl.XslTransform.Transform%2A> výstupem metody <xref:System.IO.Stream> nebo <xref:System.IO.TextWriter>:  
  
- kódování  
  
- vynechat – XML-deklarace  
  
- samostatný  
  
- DOCTYPE – veřejné  
  
- DOCTYPE – systém  
  
- CDATA-Section-Elements  
  
- rážce  
  
    > [!NOTE]
    > \*Atribut Encoding je ignorován, pokud <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda posílá svůj výstup do. <xref:System.IO.TextWriter> Místo toho se použije vlastnost <xref:System.IO.TextWriter> Encoding v.
  
 Následující atribut je ignorován, pokud je <xref:System.Xml.Xsl.XslTransform.Transform%2A> výstupem metody <xref:System.IO.Stream>:  
  
- verze: verze je vždycky 1,0.  
  
- typ média: typ média  
  
## <a name="escaping-special-characters"></a>Speciální znaky pro uvozovací znaky  
 Tato `<xsl:text disable-output-escaping>` značka slouží k označení, zda je nutné zadat speciální znaky do formuláře XML (například pomocí `<&lt>` místo `"<"` symbolu) nebo vlevo v aktuální podmínce. `disable-output-escaping` Atribut je ignorován při transformaci na objekt <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XmlWriter> a nemá žádný vliv na speciální znaky.  
  
## <a name="see-also"></a>Viz také

- [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
