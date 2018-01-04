---
title: "Možnosti výstupu na XslCompiledTransform – třída"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91ce8cba-386c-411e-bb38-0891a0393c0a
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 84171c92a56a9970b5ffc16ce8f30c85d61cc678
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="output-options-on-the-xslcompiledtransform-class"></a>Možnosti výstupu na XslCompiledTransform – třída
Toto téma popisuje dostupné možnosti výstupu XSLT. Možnosti výstupu můžete určit v šabloně stylů nebo na <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metoda.  
  
## <a name="xsloutput-element"></a>elementu xsl: Output – Element  
 `xsl:output` Element určuje možnosti pro výstup. Výstupní typ určeného <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metoda určuje chování `xsl:output` možnosti.  
  
 Následující tabulka popisuje chování pro jednotlivé atributy, které jsou k dispozici na `xsl:output` elementu, pokud je typ výstupního datového proudu nebo <xref:System.IO.TextWriter>.  
  
|Název atributu|Chování|  
|--------------------|--------------|  
|– metoda|Podporováno.|  
|verze|Ignorovat. Verze, je vždy 1.0 pro formát XML a 4.0 pro kód HTML.|  
|encoding|Ignorovat výstupního <xref:System.IO.TextWriter>. <xref:System.IO.TextWriter.Encoding%2A?displayProperty=nameWithType> Vlastnost se používá místo.|  
|vynechat Deklarace xml|Podporováno.|  
|samostatný|Podporováno.|  
|veřejná DOCTYPE|Podporováno.|  
|DOCTYPE systému|Podporováno.|  
|prvky CDATA oddílu|Podporováno.|  
|odsazení|Podporováno.|  
|typ média|Podporováno.|  
  
#### <a name="sending-output-to-an-xmlwriter"></a>Odeslání výstupu do XmlWriter  
 Pokud vaše šablony stylů používá `xsl:output` elementu a výstupní typ je <xref:System.Xml.XmlWriter> objektu, měli byste použít <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> vlastnost při vytváření <xref:System.Xml.XmlWriter> objektu. <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> Vlastnost vrátí <xref:System.Xml.XmlWriterSettings> objekt, který obsahuje informace o odvozen od `xsl:output` element kompilované šablony stylů. To <xref:System.Xml.XmlWriterSettings> objekt se dá předat do <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> metodu pro vytvoření <xref:System.Xml.XmlWriter> objektu se správnými nastaveními.  
  
## <a name="output-types"></a>Výstup typy  
 Následující seznam popisuje výstup typy, které jsou dostupné na <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> příkaz.  
  
#### <a name="xmlwriter"></a>Objekt XmlWriter  
 <xref:System.Xml.XmlWriter> Třída vypisuje datové proudy XML nebo soubory. Můžete zadat funkce, které chcete podporovat na <xref:System.Xml.XmlWriter> objektu, včetně možnosti výstupu pomocí <xref:System.Xml.XmlWriterSettings> třídy. <xref:System.Xml.XmlWriter> Třída je nedílnou součástí <xref:System.Xml> framework. Pomocí tohoto typu výstupu můžete kanálu výstup výsledků do jiného procesu XML.  
  
#### <a name="string"></a>String  
 Tento typ výstupu použijte k určení identifikátor URI výstupního souboru.  
  
#### <a name="stream"></a>Stream  
 Datový proud je abstrakcí pořadí bajtů, například soubor, zařízení se systémem vstupu a výstupu, kanálu komunikaci mezi procesy nebo soketů protokolu TCP/IP. <xref:System.IO.Stream> Třídy a jejich odvozené třídy poskytují obecné zobrazení tyto různé typy vstup a výstup, izolace programátorů z konkrétní podrobnosti operačního systému a základní zařízení.  
  
 Pomocí tohoto typu výstupu můžete odesílat data <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, nebo výstupního datového proudu (`Response.OutputStream`).  
  
#### <a name="textwriter"></a>TextWriter  
 <xref:System.IO.TextWriter> Zapisovat sekvenční znaky. Je implementována ve <xref:System.IO.StringWriter> a <xref:System.IO.StreamWriter> třídy, které zápis znaků do řetězců nebo datové proudy, v uvedeném pořadí. Tento typ výstupu použijte, pokud chcete výstup na řetězec.  
  
## <a name="notes"></a>Poznámky  
  
-   Při zápisu se prázdné značky, je zapsán mezeru mezi poslední znak názvu elementu a zpětné lomítko, `<myElement />` třeba. To umožňuje zobrazit generované stránky HTML správně starší prohlížeče.  
  
## <a name="see-also"></a>Viz také  
 [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
