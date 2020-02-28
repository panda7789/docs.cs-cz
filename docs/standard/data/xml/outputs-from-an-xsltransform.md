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
Vzhledem k tomu, že šablony stylů mohou určit výstupní formát pomocí příkazu `<xsl:output>` s atributem `method`, následující tabulka popisuje, co je výstupní formát při použití <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody k zápisu výstupu a výstupní formát je deklarován jako <xref:System.IO.Stream> nebo <xref:System.IO.TextWriter>.  
  
> [!NOTE]
> Třída <xref:System.Xml.Xsl.XslTransform> je v .NET Framework 2,0 zastaralá. Pomocí třídy <xref:System.Xml.Xsl.XslCompiledTransform> můžete provádět transformace XSLT (Extensible Stylesheet Language). Další informace najdete v tématu [použití třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 Vzhledem k tomu, že šablony stylů mohou určit výstupní formát pomocí příkazu `<xsl:output>` s atributem `method`, následující tabulka popisuje, co je výstupní formát při použití <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody k zápisu výstupu a výstupní formát je deklarován jako <xref:System.IO.Stream> nebo <xref:System.IO.TextWriter>. Následující tabulka popisuje, co se stane, když je typ výstupu deklarován metodou <xref:System.Xml.Xsl.XslTransform.Transform%2A> ve spojení s použitím příkazu `<xsl:output>`:  
  
|\<xsl: Output – metoda = > atributu|Výsledný formát|  
|-----------------------------------------|-------------------|  
|method="xml"|XML|  
|method="html"|HTML|  
|method="text"|Text|  
  
> [!NOTE]
> Poznámka: příkaz `<xsl:output>` je ignorován, pokud je výstupem metody <xref:System.Xml.Xsl.XslTransform.Transform%2A> <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XmlWriter>.  
  
 Pokud je výstupem metody <xref:System.Xml.Xsl.XslTransform.Transform%2A> <xref:System.IO.Stream> nebo <xref:System.IO.TextWriter>, jsou podporovány následující atributy:  
  
- kódování  
  
- omit-xml-declaration  
  
- samostatný  
  
- DOCTYPE – veřejné  
  
- DOCTYPE – systém  
  
- CDATA-Section-Elements  
  
- Rážce  
  
    > [!NOTE]
    > \*atribut Encoding je ignorován, pokud metoda <xref:System.Xml.Xsl.XslTransform.Transform%2A> posílá svůj výstup do <xref:System.IO.TextWriter>. Místo toho se použije vlastnost Encoding <xref:System.IO.TextWriter>.
  
 Následující atribut je ignorován, pokud je výstupem metody <xref:System.Xml.Xsl.XslTransform.Transform%2A> <xref:System.IO.Stream>:  
  
- verze: verze je vždycky 1,0.  
  
- typ média: typ média  
  
## <a name="escaping-special-characters"></a>Speciální znaky pro uvozovací znaky  
 Značka `<xsl:text disable-output-escaping>` slouží k označení, zda je nutné zadat speciální znaky do formuláře XML (například pomocí `<&lt>` místo symbolu `"<"`) nebo vlevo v aktuální podmínce. Atribut `disable-output-escaping` je ignorován při transformaci na objekt <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XmlWriter> a nemá žádný vliv na speciální znaky.  
  
## <a name="see-also"></a>Viz také

- [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
