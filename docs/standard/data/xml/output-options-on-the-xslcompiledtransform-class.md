---
title: Možnosti výstupu na třídě XslCompiledTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 91ce8cba-386c-411e-bb38-0891a0393c0a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 694d2be51d025ab054caf19e4aa2900216ad5b2e
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44494041"
---
# <a name="output-options-on-the-xslcompiledtransform-class"></a>Možnosti výstupu na třídě XslCompiledTransform
Toto téma popisuje dostupné možnosti výstup XSLT. Možnosti výstupu můžete zadat v šabloně stylů nebo na <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.  
  
## <a name="xsloutput-element"></a>elementu xsl: Output – Element  
 `xsl:output` Prvek určuje možnosti pro výstup. Výstupní typ určený <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody určuje chování `xsl:output` možnosti.  
  
 Následující tabulka popisuje chování pro každého z atributů, které jsou k dispozici na `xsl:output` prvku, když je typ výstupního datového proudu nebo <xref:System.IO.TextWriter>.  
  
|Název atributu|Chování|  
|--------------------|--------------|  
|– metoda|Podporované.|  
|verze|Ignorovat. Verze je vždy 1.0 pro XML a 4.0 pro kód HTML.|  
|encoding|Při výstupu na ignorováno <xref:System.IO.TextWriter>. <xref:System.IO.TextWriter.Encoding%2A?displayProperty=nameWithType> Vlastnost se používá místo toho.|  
|vynechat Deklarace xml|Podporované.|  
|samostatný|Podporované.|  
|veřejná DOCTYPE|Podporované.|  
|DOCTYPE systému|Podporované.|  
|prvky CDATA oddílu|Podporované.|  
|odsazení|Podporované.|  
|typ média|Podporované.|  
  
#### <a name="sending-output-to-an-xmlwriter"></a>Odesílající výstup do třídy XmlWriter  
 Pokud vaše šablony stylů využívá `xsl:output` elementu a výstupní typ je <xref:System.Xml.XmlWriter> objekt, měli byste použít <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> vlastnost při vytváření <xref:System.Xml.XmlWriter> objektu. <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> Vrátí vlastnost <xref:System.Xml.XmlWriterSettings> objekt, který obsahuje informace odvozené z `xsl:output` element zkompilované šablony stylů. To <xref:System.Xml.XmlWriterSettings> objekt může být předán <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> metodu pro vytvoření <xref:System.Xml.XmlWriter> objekt se správným nastavením.  
  
## <a name="output-types"></a>Výstupní typy  
 Následující seznam popisuje výstupní typy, které jsou k dispozici na <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> příkazu.  
  
#### <a name="xmlwriter"></a>Objekt XmlWriter  
 <xref:System.Xml.XmlWriter> Třídy zapíše datové proudy XML nebo souborů. Můžete určit funkce, které se podporují <xref:System.Xml.XmlWriter> objektu, včetně možnosti výstupu pomocí <xref:System.Xml.XmlWriterSettings> třídy. <xref:System.Xml.XmlWriter> Třída je nedílnou součástí toho, <xref:System.Xml> framework. Pomocí tohoto typu výstupu do kanálu výstup do jiného procesu XML.  
  
#### <a name="string"></a>String  
 Pomocí tohoto typu výstupu můžete určit identifikátor URI výstupního souboru.  
  
#### <a name="stream"></a>Stream  
 Datový proud je abstrakcí posloupnost bajtů, jako je například soubor, vstupně výstupní zařízení, kanálu komunikace mezi procesy nebo soket TCP/IP. <xref:System.IO.Stream> Třída a odvozené třídy poskytují obecné zobrazení těchto různých typů vstupu a výstupu, izolování programátora od konkrétních podrobností operačního systému a použitých zařízení.  
  
 Pomocí tohoto typu výstupu můžete odesílat data <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, nebo výstupní datový proud (`Response.OutputStream`).  
  
#### <a name="textwriter"></a>TextWriter  
 <xref:System.IO.TextWriter> Zapisuje po sobě jdoucích znaků. Je implementován v <xref:System.IO.StringWriter> a <xref:System.IO.StreamWriter> třídy, které zápis znaků do řetězce nebo datových proudů, v uvedeném pořadí. Pokud chcete výstup do řetězce, pomocí tohoto typu výstupu.  
  
## <a name="notes"></a>Poznámky  
  
-   Při výpisu prázdné značky, je zapsán mezeru mezi poslední znak názvu elementu a zpětné lomítko, `<myElement />` třeba. To umožňuje starší prohlížeče správně zobrazit vygenerované stránky HTML.  
  
## <a name="see-also"></a>Viz také:

- [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
