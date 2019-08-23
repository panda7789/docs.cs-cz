---
title: Výstupy z XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a6c2ea2fe2f02dc1897cb1348f4c2585b730036
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924958"
---
# <a name="outputs-from-an-xsltransform"></a>Výstupy z XslTransform
Vzhledem k tomu, že šablony stylů mohou určit výstupní `<xsl:output>` formát pomocí příkazu `method` s atributem, následující tabulka popisuje, co je <xref:System.Xml.Xsl.XslTransform.Transform%2A> výstupní formát při použití metody k zápisu výstupu a výstupní formát je deklarováno jako <xref:System.IO.Stream> nebo <xref:System.IO.TextWriter>.  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá v .NET Framework 2,0. Transformace XSLT (Extensible Stylesheet Language) můžete použít k <xref:System.Xml.Xsl.XslCompiledTransform> transformaci pomocí třídy. Další informace najdete v tématu [použití třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 Vzhledem k tomu, že šablony stylů mohou určit výstupní `<xsl:output>` formát pomocí příkazu `method` s atributem, následující tabulka popisuje, co je <xref:System.Xml.Xsl.XslTransform.Transform%2A> výstupní formát při použití metody k zápisu výstupu a výstupní formát je deklarováno jako <xref:System.IO.Stream> nebo <xref:System.IO.TextWriter>. Následující tabulka popisuje, co se stane, když je typ výstupu deklarován <xref:System.Xml.Xsl.XslTransform.Transform%2A> metodou ve spojení s použitím `<xsl:output>` příkazu:  
  
|\<XSL: Output – metoda = > – atribut|Výsledný formát|  
|-----------------------------------------|-------------------|  
|method="xml"|XML|  
|method="html"|HTML|  
|method="text"|Text|  
  
> [!NOTE]
> Poznámka: Příkaz je ignorován, pokud <xref:System.Xml.XmlReader> je výstupem <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody nebo <xref:System.Xml.XmlWriter>. `<xsl:output>`  
  
 Následující atributy jsou podporovány, pokud <xref:System.Xml.Xsl.XslTransform.Transform%2A> <xref:System.IO.Stream> je výstupem metody nebo <xref:System.IO.TextWriter>:  
  
- kódování  
  
- omit-xml-declaration  
  
- samostatný  
  
- DOCTYPE – veřejné  
  
- DOCTYPE – systém  
  
- CDATA-Section-Elements  
  
- rážce  
  
    > [!NOTE]
    > \*Atribut Encoding je ignorován, pokud <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda posílá svůj výstup <xref:System.IO.TextWriter>do. Místo toho se použije vlastnost <xref:System.IO.TextWriter> Encoding v. 
  
 Následující atribut je ignorován, pokud <xref:System.Xml.Xsl.XslTransform.Transform%2A> <xref:System.IO.Stream>je výstupem metody:  
  
- verze: verze je vždycky 1,0.  
  
- typ média: typ média  
  
## <a name="escaping-special-characters"></a>Speciální znaky pro uvozovací znaky  
 Tato `<xsl:text disable-output-escaping>` značka slouží k označení, zda je nutné zadat speciální znaky do formuláře XML (například pomocí `<&lt>` místo `"<"` symbolu) nebo vlevo v aktuální podmínce. Atribut je ignorován při transformaci <xref:System.Xml.XmlReader> na objekt nebo <xref:System.Xml.XmlWriter> a nemá žádný vliv na speciální znaky. `disable-output-escaping`  
  
## <a name="see-also"></a>Viz také:

- [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
