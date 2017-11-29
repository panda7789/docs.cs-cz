---
title: "Výstupy z XslTransform"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 92bf2d7184ca2eb8b17c1d83130c66d1f33f0483
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="outputs-from-an-xsltransform"></a>Výstupy z XslTransform
Vzhledem k tomu, že šablony stylů můžete určit formát výstupu pomocí `<xsl:output>` příkaz s `method` atribut, následující tabulka popisuje formát výstupu je, když <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda se používá k zápisu výstupu a formát výstupu se deklarovaný jako <xref:System.IO.Stream> nebo <xref:System.IO.TextWriter>.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Můžete provést jazyk XSL pro transformace transformace XSLT () pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy. V tématu [pomocí třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.  
  
 Vzhledem k tomu, že šablony stylů můžete určit formát výstupu pomocí `<xsl:output>` příkaz s `method` atribut, následující tabulka popisuje formát výstupu je, když <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda se používá k zápisu výstupu a formát výstupu se deklarovaný jako <xref:System.IO.Stream> nebo <xref:System.IO.TextWriter>. Následující tabulka popisuje, co se stane, když je deklarovaná výstupní typ <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda ve spojení s používáním `<xsl:output>` příkaz:  
  
|\<Metoda elementu xsl: Output = > atribut|Výsledný formát|  
|-----------------------------------------|-------------------|  
|Metoda = "xml"|XML|  
|Metoda = "html"|HTML|  
|Metoda = "text"|Text|  
  
> [!NOTE]
>  Poznámka: `<xsl:output>` příkaz se ignoruje při výstup <xref:System.Xml.Xsl.XslTransform.Transform%2A> je metoda <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XmlWriter>.  
  
 Následující atributy jsou podporovány při <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda výstup <xref:System.IO.Stream> nebo <xref:System.IO.TextWriter>:  
  
-   kódování *  
  
-   vynechat Deklarace xml  
  
-   samostatný  
  
-   veřejná DOCTYPE  
  
-   DOCTYPE systému  
  
-   prvky CDATA oddílu  
  
-   odsazení  
  
    > [!NOTE]
    >  * kódování atributu se ignoruje při <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda odesílá výstup do <xref:System.IO.TextWriter>. Vlastnost kódování na <xref:System.IO.TextWriter> bude místo něj použita.  
  
 Následující atribut se ignoruje při <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda výstup <xref:System.IO.Stream>:  
  
-   verze: verze je vždy 1.0  
  
-   typ média: typ média  
  
## <a name="escaping-special-characters"></a>Speciální uvozovací znaky  
 `<xsl:text disable-output-escaping>` Značky slouží k označení, zda speciální znaky musí být uvozena do formuláře XML (například pomocí `<&lt>` místě `"<"` symbol) a levé ve stavu, existuje. `disable-output-escaping` Atribut se ignoruje, pokud transformace na <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XmlWriter> objektu a nemá žádný vliv na speciální znaky.  
  
## <a name="see-also"></a>Viz také  
 [Třída XslTransform implementuje procesoru XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
