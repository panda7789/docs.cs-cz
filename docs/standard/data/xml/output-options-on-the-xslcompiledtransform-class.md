---
title: Možnosti výstupu na třídě XslCompiledTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 91ce8cba-386c-411e-bb38-0891a0393c0a
ms.openlocfilehash: 504057bd5e10498d39b2bce908742fc20b112c52
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710502"
---
# <a name="output-options-on-the-xslcompiledtransform-class"></a>Možnosti výstupu na třídě XslCompiledTransform
Toto téma popisuje dostupné možnosti výstupu XSLT. Můžete zadat možnosti výstupu v šabloně stylů nebo v metodě <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>.  
  
## <a name="xsloutput-element"></a>Element xsl: Output  
 Element `xsl:output` Určuje možnosti výstupu. Typ výstupu určený metodou <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> určuje chování možností `xsl:output`.  
  
 Následující tabulka popisuje chování pro všechny atributy, které jsou k dispozici v prvku `xsl:output`, pokud je typ výstupu datový proud nebo <xref:System.IO.TextWriter>.  
  
|Název atributu|Chování|  
|--------------------|--------------|  
|metoda|Podporováno.|  
|Verze nástroje|Přeskočen. Verze je vždy 1,0 pro XML a 4,0 pro formát HTML.|  
|encoding|Ignoruje se při výstupu do <xref:System.IO.TextWriter>. Místo toho se použije vlastnost <xref:System.IO.TextWriter.Encoding%2A?displayProperty=nameWithType>.|  
|omit-xml-declaration|Podporováno.|  
|samostatný|Podporováno.|  
|DOCTYPE – veřejné|Podporováno.|  
|DOCTYPE – systém|Podporováno.|  
|CDATA-Section-Elements|Podporováno.|  
|rážce|Podporováno.|  
|media-type|Podporováno.|  
  
#### <a name="sending-output-to-an-xmlwriter"></a>Odeslání výstupu do XmlWriter  
 Pokud vaše předloha se styly používá prvek `xsl:output` a výstupní typ je <xref:System.Xml.XmlWriter> objekt, měli byste při vytváření objektu <xref:System.Xml.XmlWriter> použít vlastnost <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType>. Vlastnost <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> vrací objekt <xref:System.Xml.XmlWriterSettings>, který obsahuje informace odvozené z prvku `xsl:output` zkompilované předlohy se styly. Tento objekt <xref:System.Xml.XmlWriterSettings> lze předat metodě <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> a vytvořit tak objekt <xref:System.Xml.XmlWriter> se správným nastavením.  
  
## <a name="output-types"></a>Výstupní typy  
 Následující seznam popisuje výstupní typy dostupné v příkazu <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>.  
  
#### <a name="xmlwriter"></a>XmlWriter  
 Třída <xref:System.Xml.XmlWriter> zapisuje datové proudy XML nebo soubory. Můžete určit funkce pro podporu objektu <xref:System.Xml.XmlWriter>, včetně možností výstupu, pomocí <xref:System.Xml.XmlWriterSettings> třídy. Třída <xref:System.Xml.XmlWriter> je nedílnou součástí <xref:System.Xml> architektury. Tento typ výstupu slouží k kanálu výstupních výsledků do jiného procesu XML.  
  
#### <a name="string"></a>String  
 Tento typ výstupu použijte k určení identifikátoru URI výstupního souboru.  
  
#### <a name="stream"></a>Stream  
 Stream je abstrakce posloupnosti bajtů, jako je například soubor, vstupní/výstupní zařízení, komunikační kanál mezi procesy nebo soket protokolu TCP/IP. Třída <xref:System.IO.Stream> a její odvozené třídy poskytují obecný pohled na tyto různé typy vstupů a výstupů a izoluje programátora od konkrétních podrobností o operačním systému a základních zařízeních.  
  
 Tento typ výstupu použijte k odeslání dat do <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>nebo výstupního datového proudu (`Response.OutputStream`).  
  
#### <a name="textwriter"></a>TextWriter  
 <xref:System.IO.TextWriter> zapisuje sekvenční znaky. Je implementována v třídách <xref:System.IO.StringWriter> a <xref:System.IO.StreamWriter>, které zapisují znaky do řetězců nebo datových proudů v uvedeném pořadí. Tento typ výstupu použijte, pokud chcete výstup do řetězce.  
  
## <a name="notes"></a>Poznámky  
  
- Při zápisu prázdných značek je mezera zapsána mezi posledním znakem názvu prvku a zpětným lomítkem, `<myElement />` například. To umožňuje, aby starší prohlížeče správně zobrazovaly vygenerované stránky HTML.  
  
## <a name="see-also"></a>Viz také:

- [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
