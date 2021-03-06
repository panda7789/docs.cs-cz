---
title: Možnosti výstupu na třídě XslCompiledTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 91ce8cba-386c-411e-bb38-0891a0393c0a
ms.openlocfilehash: e9ffdc1377dbf124f042802279e7e7a275222eff
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288703"
---
# <a name="output-options-on-the-xslcompiledtransform-class"></a>Možnosti výstupu na třídě XslCompiledTransform
Toto téma popisuje dostupné možnosti výstupu XSLT. Můžete zadat možnosti výstupu v šabloně stylů nebo v <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metodě.  
  
## <a name="xsloutput-element"></a>Element xsl: Output  
 `xsl:output`Element určuje možnosti výstupu. Typ výstupu určený <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metodou určuje chování `xsl:output` možností.  
  
 Následující tabulka popisuje chování pro všechny atributy, které jsou k dispozici v `xsl:output` prvku, když je výstupní typ datový proud nebo <xref:System.IO.TextWriter> .  
  
|Název atributu|Chování|  
|--------------------|--------------|  
|method|Podporuje se.|  
|verze|Přeskočen. Verze je vždy 1,0 pro XML a 4,0 pro formát HTML.|  
|encoding|Ignoruje se při výstupu do <xref:System.IO.TextWriter> . <xref:System.IO.TextWriter.Encoding%2A?displayProperty=nameWithType>Místo toho se použije vlastnost.|  
|vynechat – XML-deklarace|Podporuje se.|  
|samostatný|Podporuje se.|  
|DOCTYPE – veřejné|Podporuje se.|  
|DOCTYPE – systém|Podporuje se.|  
|CDATA-Section-Elements|Podporuje se.|  
|rážce|Podporuje se.|  
|typ média|Podporuje se.|  
  
#### <a name="sending-output-to-an-xmlwriter"></a>Odeslání výstupu do XmlWriter  
 Pokud vaše předloha se styly používá `xsl:output` prvek a výstupní typ je <xref:System.Xml.XmlWriter> objekt, měli byste <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> při vytváření objektu použít vlastnost <xref:System.Xml.XmlWriter> . <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType>Vlastnost vrátí <xref:System.Xml.XmlWriterSettings> objekt, který obsahuje informace odvozené z `xsl:output` prvku zkompilované předlohy se styly. Tento <xref:System.Xml.XmlWriterSettings> objekt lze předat <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> metodě pro vytvoření <xref:System.Xml.XmlWriter> objektu se správnými nastaveními.  
  
## <a name="output-types"></a>Výstupní typy  
 Následující seznam popisuje výstupní typy dostupné v <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> příkazu.  
  
#### <a name="xmlwriter"></a>XmlWriter  
 <xref:System.Xml.XmlWriter>Třída zapisuje streamy XML nebo soubory. Můžete určit funkce pro podporu <xref:System.Xml.XmlWriter> objektu, včetně možností výstupu, pomocí <xref:System.Xml.XmlWriterSettings> třídy. <xref:System.Xml.XmlWriter>Třída je nedílnou součástí <xref:System.Xml> rozhraní. Tento typ výstupu slouží k kanálu výstupních výsledků do jiného procesu XML.  
  
#### <a name="string"></a>Řetězec  
 Tento typ výstupu použijte k určení identifikátoru URI výstupního souboru.  
  
#### <a name="stream"></a>Stream  
 Stream je abstrakce posloupnosti bajtů, jako je například soubor, vstupní/výstupní zařízení, komunikační kanál mezi procesy nebo soket protokolu TCP/IP. <xref:System.IO.Stream>Třída a její odvozené třídy poskytují obecné zobrazení těchto různých typů vstupu a výstupu a izolují programátora od konkrétních podrobností o operačním systému a základních zařízeních.  
  
 Tento typ výstupu použijte k odeslání dat do <xref:System.IO.FileStream> , <xref:System.IO.MemoryStream> nebo výstupního datového proudu ( `Response.OutputStream` ).  
  
#### <a name="textwriter"></a>TextWriter  
 <xref:System.IO.TextWriter>Zápisy po sobě jdoucích znaků. Je implementována v <xref:System.IO.StringWriter> <xref:System.IO.StreamWriter> třídách a, které zapisují znaky do řetězců nebo datových proudů v uvedeném pořadí. Tento typ výstupu použijte, pokud chcete výstup do řetězce.  
  
## <a name="notes"></a>Poznámky  
  
- Při zápisu prázdných značek je mezera zapsána mezi posledním znakem názvu prvku a zpětným lomítkem, například `<myElement />` . To umožňuje, aby starší prohlížeče správně zobrazovaly vygenerované stránky HTML.  
  
## <a name="see-also"></a>Viz také

- [Transformace XSLT](xslt-transformations.md)
