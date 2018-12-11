---
title: Standardní řetězce formátu data a času
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [.NET Framework], dates
- custom DateTime format string
- format specifiers, custom date and time
- format strings
- custom date and time format strings
- formatting [.NET Framework], time
- date and time strings
ms.assetid: bb79761a-ca08-44ee-b142-b06b3e2fc22b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4c6d10fad075a70d80bf6e5aa32edf0f89c42dc
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53151288"
---
# <a name="standard-date-and-time-format-strings"></a>Standardní řetězce formátu data a času
Řetězec standardního formátu data a času používá pro definování textového vyjádření hodnoty data a času jeden specifikátor formátu. Formátovací řetězec data a času, který obsahuje více než jeden znak, včetně prázdných znaků, je interpretován jako vlastní data a času formátovací řetězec; Další informace najdete v tématu [vlastní data a řetězce formátu časových](../../../docs/standard/base-types/custom-date-and-time-format-strings.md). Řetězec standardního nebo vlastního formátu lze používat dvěma způsoby:  
  
-   Chcete-li definovat řetězec, který je výsledkem operace formátování.  
  
-   Chcete-li definovat textové vyjádření hodnoty data a času, který lze převést na <xref:System.DateTime> nebo <xref:System.DateTimeOffset> hodnotu pomocí operace analýzy.  

> [!TIP]
>  Můžete stáhnout [formátování nástroj](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d), aplikaci, která umožňuje použití formátu řetězců pro číselné nebo datum a čas, hodnoty a zobrazí se výsledný řetězec.  

Standardní hodnoty data a času formátovací řetězce lze použít s oběma <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnoty.  
  
[!INCLUDE[C# interactive-note](~/includes/csharp-interactive-with-utc-partial-note.md)] 

<a name="table"></a> Následující tabulka popisuje specifikátory formátu času a data. Pokud není uvedeno jinak, konkrétní standardního formátu data a času specifikátor vytváří identickou řetězcovou reprezentaci bez ohledu na to, zda je použit s <xref:System.DateTime> nebo <xref:System.DateTimeOffset> hodnotu. Najdete v článku [poznámky](#Notes) části Další informace o použití standardní hodnoty data a času formátovací řetězce.  
  
|Specifikátor formátu|Popis|Příklady|  
|----------------------|-----------------|--------------|  
|"d"|Vzor krátkého formátu data.<br /><br /> Další informace:[The krátkého formátu data ("d") specifikátor formátu](#ShortDate).|2009-06-15T13:45:30 -> 6/15/2009 (en US)<br /><br /> 2009-06-15T13:45:30 -> 15/06/2009 (fr-FR)<br /><br /> 2009-06-15T13:45:30 -> 2009/06/15 (ja-JP)|  
|"D"|Vzor dlouhého formátu data.<br /><br /> Další informace:[The dlouhého data ("D") formátu specifikátor](#LongDate).|2009-06-15T13:45:30 -> Monday, June 15, 2009 (en US)<br /><br /> 2009-06-15 г июня 2009-15T13:45:30 >. (ru-RU)<br /><br /> 2009-06-15T13:45:30 -> Montag, 15. Juni 2009 (de-DE)|  
|"f"|Vzor úplného formátu data/času (krátkého formátu času).<br /><br /> Další informace: [Specifikátor krátkého formátu času ("f") formátu úplné datum](#FullDateShortTime).|2009-06-15T13:45:30 -> Monday, June 15, 2009 1:45 PM (en US)<br /><br /> 2009-06-15T13:45:30 -> juni den 15, 2009 13:45 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 1:45 μμ (el-GR)|  
|"F"|Vzor úplného formátu data/času (dlouhého formátu času).<br /><br /> Další informace: [Úplného data a dlouhého času ("F") formátu specifikátor](#FullDateLongTime).|2009-06-15T13:45:30 -> Monday, June 15, 2009 1:45:30 odp (en US)<br /><br /> 2009-06-15T13:45:30 -> juni den 15, 2009 13:45:30 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 1:45:30 μμ (el-GR)|  
|"g"|Vzor obecného formátu data/času (krátkého formátu času).<br /><br /> Další informace: [Specifikátor obecného data a krátkého času ("g") formátu](#GeneralDateShortTime).|2009-06-15T13:45:30 -> 6/15/2009 1:45 PM (en US)<br /><br /> 2009-06-15T13:45:30-06/15/2009 > 13:45 (es-ES)<br /><br /> 2009-06-15T13:45:30 -> 2009/6/15 13:45 (zh-CN)|  
|"G"|Vzor obecného formátu data a času (dlouhého formátu času).<br /><br /> Další informace: [Specifikátor obecného data a dlouhého času ("G") formátu](#GeneralDateLongTime).|2009-06-15T13:45:30 -> 6/15/2009 1:45:30 odp (en US)<br /><br /> 2009-06-06/15/2009-15T13:45:30 > 13:45:30 (es-ES)<br /><br /> 2009-06-15T13:45:30 -> 2009/6/15 13:45:30 (zh-CN)|  
|"M", "m"|Vzor formátu měsíce/dne.<br /><br /> Další informace: [Specifikátor formátu měsíce ("M", "m")](#MonthDay).|2009-06-15T13:45:30 -> June 15 (en US)<br /><br /> 2009-06-15-15T13:45:30 &GT;. juni (da-DK)<br /><br /> 2009-06-15T13:45:30 -> Juni 15 (id-ID)|  
|"O", "o"|Vzor formátu data/času zpátečního převodu.<br /><br /> Další informace: [Specifikátor formátu zpátečního převodu ("O", "o")](#Roundtrip).|<xref:System.DateTime> Hodnoty:<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Local)--> 2009-06-15T13:45:30.0000000-07:00<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Utc)--> 2009-06-15T13:45:30.0000000Z<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Unspecified)--> 2009-06-15T13:45:30.0000000<br /><br /> <xref:System.DateTimeOffset> Hodnoty:<br /><br /> 2009-06-15T13:45:30-07:00--&GT; 2009-06-15T13:45:30.0000000-07:00|  
|"R", "r"|Vzor RFC1123.<br /><br /> Další informace: [RFC1123 ("R", "r") specifikátor formátu](#RFC1123).|2009-06-15T13:45:30 -> pondělí, 15 Jun 2009 20:45:30 GMT|  
|"s"|Vzor seřaditelného formátu data/času.<br /><br /> Další informace: [Specifikátor Seřaditelného ("s") formátu](#Sortable).|2009-06-15T13:45:30 (DateTimeKind.Local) -> 2009-06-15T13:45:30<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Utc) -> 2009-06-15T13:45:30|  
|"t"|Vzor krátkého formátu času.<br /><br /> Další informace: [Specifikátor krátkého formátu času ("t") formátu](#ShortTime).|2009-06-15T13:45:30 -> 1:45 PM (en US)<br /><br /> 2009-06-15T13:45:30 -> 13:45 (hr-HR)<br /><br /> 2009-06-01:45-15T13:45:30 > م (ar – třeba)|  
|"T"|Vzor dlouhého formátu času.<br /><br /> Další informace: [Specifikátor dlouhého času ("T") formátu](#LongTime).|2009-06-15T13:45:30 -> 1:45:30 odp (en US)<br /><br /> 2009-06-15T13:45:30 -> 13:45:30 (hr-HR)<br /><br /> 2009-06-01:45:30-15T13:45:30 > م (ar – třeba)|  
|"u"|Vzor univerzálního seřaditelného formátu data/času.<br /><br /> Další informace: [Specifikátor formátu Univerzální seřaditelný ("u")](#UniversalSortable).|S <xref:System.DateTime> hodnotu: 2009-06-2009-06-15-15T13:45:30 &GT; 13:45:30Z<br /><br /> S <xref:System.DateTimeOffset> hodnotu: 2009-06-2009-06-15-15T13:45:30 &GT; 20:45:30Z|  
|"U"|Vzor univerzálního úplného formátu data/času.<br /><br /> Další informace: [Specifikátor univerzálního úplného ("U") formátu](#UniversalFull).|2009-06-15T13:45:30 -> Monday, June 15, 2009 20:45:30: 00 (en US)<br /><br /> 2009-06-15T13:45:30 -> juni den 15, 2009 20:45:30 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 8:45:30 μμ (el-GR)|  
|"Y", "y"|Vzor formátu roku a měsíce.<br /><br /> Další informace: [Specifikátor formátu měsíce ("Y") rok](#YearMonth).|2009-06-15T13:45:30 -> June, 2009 (en US)<br /><br /> 2009-06-15T13:45:30 -> juni (da-DK) 2009<br /><br /> 2009-06-15T13:45:30 -> Juni 2009 (id-ID)|  
|Jakýkoli jiný samostatný znak|Neznámý specifikátor.|Vyvolá výjimku za běhu <xref:System.FormatException>.|  
  
## <a name="how-standard-format-strings-work"></a>Jak fungují řetězce standardního formátu  
 V rámci operace formátování je řetězec standardního formátu pouze aliasem pro řetězec vlastního formátu. Výhodou používání aliasu pro odkaz na řetězec vlastního formátu je skutečnost, že ačkoli alias zůstane neutrální, řetězec vlastního formátu se může změnit. Toto je důležité, protože řetězcová reprezentace hodnot data a času se obvykle liší podle jazykové verze. Například řetězec standardního formátu "d" označuje, že hodnota data a času má být zobrazena pomocí vzoru krátkého formátu data. Pro neutrální jazykovou verzi je použit formát "MM/dd/yyyy". Pro jazykovou verzi fr-FR je to formát "dd/MM/yyyy". Pro jazykovou verzi ja-JP je to formát "yyyy/MM/dd".  
  
 Pokud je řetězec standardního formátu v rámci operace formátování namapován na řetězec vlastního formátu konkrétní jazykové verze, může vaše aplikace definovat konkrétní jazykovou verzi, jejíž řetězce vlastního formátu se používají jedním z těchto způsobů:  
  
-   Můžete použít výchozí (nebo aktuální) jazykovou verzi. Následující příklad zobrazí datum pomocí krátkého formátu data aktuální jazykové verze. V tomto případě je aktuální jazyková verze nastavena na en-US.  
  
     [!code-csharp-interactive[System.DateTime.Conceptual.Formatting#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#1)]
     [!code-vb[System.DateTime.Conceptual.Formatting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#1)]  
  
-   Můžete předat <xref:System.Globalization.CultureInfo> objektu, který představuje jazykovou verzi, jejíž formátování má být použita na metodu, která má <xref:System.IFormatProvider> parametru. Následující příklad zobrazí datum pomocí formátu krátkého data jazykové verze pt-BR.  
  
     [!code-csharp[System.DateTime.Conceptual.Formatting#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#2)]
     [!code-vb[System.DateTime.Conceptual.Formatting#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#2)]  
  
-   Můžete předat <xref:System.Globalization.DateTimeFormatInfo> objekt, který poskytuje informace o formátování metodě, která má <xref:System.IFormatProvider> parametru. Následující příklad zobrazí datum pomocí krátkého formátu data z <xref:System.Globalization.DateTimeFormatInfo> pro jazykovou verzi hr-HR.  
  
     [!code-csharp[System.DateTime.Conceptual.Formatting#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#3)]
     [!code-vb[System.DateTime.Conceptual.Formatting#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#3)]  
  
> [!NOTE]
>  Informace o přizpůsobení vzorů nebo řetězců použitých ve formátování hodnot data a času naleznete v tématu <xref:System.Globalization.NumberFormatInfo> třídě.  
  
 V některých případech slouží řetězec standardního formátu jako vhodná zkratka pro řetězec vlastního delšího formátu, který je neutrální. Do této kategorie patří čtyři řetězce standardního formátu: "O" (nebo "o"), "R" (nebo "r"), "s" a "u". Tyto řetězce odpovídají řetězcům vlastního formátu, které jsou definovány neutrální jazykovou verzí. Vytvářejí řetězcové reprezentace hodnot data a času, které mají být identické napříč jazykovými verzemi. Následující tabulka obsahuje informace o těchto čtyřech řetězcích standardního formátu data a času.  
  
|Řetězec standardního formátu|Definovaný vlastností DateTimeFormatInfo.InvariantInfo|Řetězec vlastního formátu|  
|----------------------------|----------------------------------------------------------|--------------------------|  
|"O" nebo "o"|Žádná|yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffzz|  
|"R" nebo "r"|<xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A>|ddd, dd MMM yyyy HH':'mm':'ss 'GMT'|  
|"s"|<xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern%2A>|yyyy'-'MM'-'dd'T'HH':'mm':'ss|  
|"u"|<xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>|yyyy'-'MM'-'dd HH':'mm':'ss'Z'|  
  
 Standardní formátovací řetězce můžete také použít při operacích analýzy pomocí <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> metody, které vyžadují vstupní řetězec tak, aby přesně odpovídal určitému vzoru k úspěšnému provedení operace analýzy. Mnoho řetězců standardního formátu je namapováno na několik řetězců vlastního formátu. Hodnotu data a času lze tedy vyjádřit v celé řadě formátů a operace analýzy i tak proběhne úspěšně. Můžete určit vlastní formátovací řetězec nebo řetězce, které odpovídají standardní formátovací řetězec voláním <xref:System.Globalization.DateTimeFormatInfo.GetAllDateTimePatterns%28System.Char%29?displayProperty=nameWithType> metody. Následující příklad zobrazí řetězce vlastního formátu, které mapují řetězec standardního formátu "d" (vzor krátkého formátu data).  
  
 [!code-csharp-interactive[Formatting.DateAndTime.Standard#17](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/stdandparsing1.cs#17)]
 [!code-vb[Formatting.DateAndTime.Standard#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/stdandparsing1.vb#17)]  
  
 Následující oddíly popisují standardní specifikátory formátu pro <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnoty.  
  
<a name="ShortDate"></a>   
## <a name="the-short-date-d-format-specifier"></a>Specifikátor krátkého formátu data ("d")  
 Specifikátor standardního formátu "d" představuje vlastní data a času formátovací řetězec, který je definován konkrétní jazykovou verzi <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> vlastnost. Například řetězec vlastního formátu, který je vrácen <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A> vlastnost invariantní jazykové verzi je "MM/dd/yyyy".  
  
 Následující tabulce jsou uvedeny <xref:System.Globalization.DateTimeFormatInfo> objektu vlastnosti, které řídí formátování vráceného řetězce.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A>|Definuje celkový formát výsledného řetězce.|  
|<xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A>|Definuje řetězec, který u data odděluje komponenty roku, měsíce a dne.|  
  
 Následující příklad používá specifikátor formátu "d" k zobrazení hodnoty data a času.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#1)]
 [!code-vb[Formatting.DateAndTime.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#1)]  
  
 [Zpět k tabulce](#table)  
  
<a name="LongDate"></a>   
## <a name="the-long-date-d-format-specifier"></a>Specifikátor dlouhého formátu data ("D")  
 Specifikátor standardního formátu "D" představuje vlastní data a času formátovací řetězec, který je definován aktuální <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> vlastnost. Například řetězec vlastního formátu pro neutrální jazykovou verzi je "dddd, dd MMMM yyyy".  
  
 V následující tabulce jsou uvedeny vlastnosti <xref:System.Globalization.DateTimeFormatInfo> , které řídí formátování vráceného řetězce.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A>|Definuje celkový formát výsledného řetězce.|  
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Definuje lokalizované názvy dní, které mohou být zobrazeny ve výsledném řetězci.|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Definuje lokalizované názvy měsíců, které mohou být zobrazeny ve výsledném řetězci.|  
  
 Následující příklad používá specifikátor formátu "D" k zobrazení hodnoty data a času.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#2)]
 [!code-vb[Formatting.DateAndTime.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#2)]  
  
 [Zpět k tabulce](#table)  
  
<a name="FullDateShortTime"></a>   
## <a name="the-full-date-short-time-f-format-specifier"></a>Specifikátor úplného formátu data a krátkého formátu času ("f")  
 Standardní specifikátor formátu "f" představuje kombinaci vzorů dlouhého formátu data "D" a krátkého formátu času "t", která je oddělena mezerou.  
  
 Výsledný řetězec je ovlivněn informace o formátování specifického <xref:System.Globalization.DateTimeFormatInfo> objektu. Následující tabulce jsou uvedeny <xref:System.Globalization.DateTimeFormatInfo> objektu vlastnosti, které mohou řídit formátování vráceného řetězce. Specifikátor vlastního formátu vrácený <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> a <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> vlastnosti některých jazykových verzí nemusí mít používat všechny vlastnosti.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A>|Definuje formát komponenty data výsledného řetězce.|  
|<xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A>|Definuje formát komponenty času výsledného řetězce.|  
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Definuje lokalizované názvy dní, které mohou být zobrazeny ve výsledném řetězci.|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Definuje lokalizované názvy měsíců, které mohou být zobrazeny ve výsledném řetězci.|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Definuje řetězec, který odděluje komponenty hodiny, minuty a sekundy v časovém údaji.|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Definuje řetězec, který označuje dobu od půlnoci do doby před polednem ve 12hodinovém formátu.|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Definuje řetězec, který označuje dobu od poledne do doby před půlnocí ve 12hodinovém formátu.|  
  
 Následující příklad používá specifikátor formátu "f" k zobrazení hodnoty data a času.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#3)]
 [!code-vb[Formatting.DateAndTime.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#3)]  
  
 [Zpět k tabulce](#table)  
  
<a name="FullDateLongTime"></a>   
## <a name="the-full-date-long-time-f-format-specifier"></a>Specifikátor úplného formátu data a dlouhého formátu času ("F")  
 Specifikátor standardního formátu "F" představuje vlastní data a času formátovací řetězec, který je definován aktuální <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> vlastnost. Například řetězec vlastního formátu pro neutrální jazykovou verzi je "dddd, dd MMMM yyyy HH:mm:ss".  
  
 Následující tabulce jsou uvedeny <xref:System.Globalization.DateTimeFormatInfo> objektu vlastnosti, které mohou řídit formátování vráceného řetězce. Specifikátor vlastního formátu, který je vrácen <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A> vlastnost některých jazykových verzí nemusí mít používat všechny vlastnosti.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A>|Definuje celkový formát výsledného řetězce.|  
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Definuje lokalizované názvy dní, které mohou být zobrazeny ve výsledném řetězci.|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Definuje lokalizované názvy měsíců, které mohou být zobrazeny ve výsledném řetězci.|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Definuje řetězec, který odděluje komponenty hodiny, minuty a sekundy v časovém údaji.|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Definuje řetězec, který označuje dobu od půlnoci do doby před polednem ve 12hodinovém formátu.|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Definuje řetězec, který označuje dobu od poledne do doby před půlnocí ve 12hodinovém formátu.|  
  
 Následující příklad používá specifikátor formátu "F" k zobrazení hodnoty data a času.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#4)]
 [!code-vb[Formatting.DateAndTime.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#4)]  
  
 [Zpět k tabulce](#table)  
  
<a name="GeneralDateShortTime"></a>   
## <a name="the-general-date-short-time-g-format-specifier"></a>Specifikátor obecného formátu data a krátkého formátu času ("g")  
 Standardní specifikátor formátu "g" představuje kombinaci vzorů krátkého formátu data "d" a krátkého formátu času "t", která je oddělena mezerou.  
  
 Výsledný řetězec je ovlivněn informace o formátování specifického <xref:System.Globalization.DateTimeFormatInfo> objektu. Následující tabulce jsou uvedeny <xref:System.Globalization.DateTimeFormatInfo> objektu vlastnosti, které mohou řídit formátování vráceného řetězce. Specifikátor vlastního formátu, který je vrácen <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> a <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> vlastnosti některých jazykových verzí nemusí mít používat všechny vlastnosti.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A>|Definuje formát komponenty data výsledného řetězce.|  
|<xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A>|Definuje formát komponenty času výsledného řetězce.|  
|<xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A>|Definuje řetězec, který u data odděluje komponenty roku, měsíce a dne.|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Definuje řetězec, který odděluje komponenty hodiny, minuty a sekundy v časovém údaji.|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Definuje řetězec, který označuje dobu od půlnoci do doby před polednem ve 12hodinovém formátu.|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Definuje řetězec, který označuje dobu od poledne do doby před půlnocí ve 12hodinovém formátu.|  
  
 Následující příklad používá specifikátor formátu "g" k zobrazení hodnoty data a času.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#5)]  
  
 [Zpět k tabulce](#table)  
  
<a name="GeneralDateLongTime"></a>   
## <a name="the-general-date-long-time-g-format-specifier"></a>Specifikátor obecného formátu data a dlouhého formátu času ("G")  
 Standardní specifikátor formátu "G" představuje kombinaci vzorů krátkého formátu data "d" a dlouhého formátu času "T", která je oddělena mezerou.  
  
 Výsledný řetězec je ovlivněn informace o formátování specifického <xref:System.Globalization.DateTimeFormatInfo> objektu. Následující tabulce jsou uvedeny <xref:System.Globalization.DateTimeFormatInfo> objektu vlastnosti, které mohou řídit formátování vráceného řetězce. Specifikátor vlastního formátu, který je vrácen <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> a <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> vlastnosti některých jazykových verzí nemusí mít používat všechny vlastnosti.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A>|Definuje formát komponenty data výsledného řetězce.|  
|<xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A>|Definuje formát komponenty času výsledného řetězce.|  
|<xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A>|Definuje řetězec, který u data odděluje komponenty roku, měsíce a dne.|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Definuje řetězec, který odděluje komponenty hodiny, minuty a sekundy v časovém údaji.|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Definuje řetězec, který označuje dobu od půlnoci do doby před polednem ve 12hodinovém formátu.|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Definuje řetězec, který označuje dobu od poledne do doby před půlnocí ve 12hodinovém formátu.|  
  
 Následující příklad používá specifikátor formátu "G" k zobrazení hodnoty data a času.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#6)]
 [!code-vb[Formatting.DateAndTime.Standard#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#6)]  
  
 [Zpět k tabulce](#table)  
  
<a name="MonthDay"></a>   
## <a name="the-month-m-m-format-specifier"></a>Specifikátor formátu měsíce ("M", "m")  
 Specifikátor standardního formátu "M" nebo "m" představuje vlastní data a času formátovací řetězec, který je definován aktuální <xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern%2A?displayProperty=nameWithType> vlastnost. Například řetězec vlastního formátu pro neutrální jazykovou verzi je "MMMM dd".  
  
 Následující tabulce jsou uvedeny <xref:System.Globalization.DateTimeFormatInfo> objektu vlastnosti, které řídí formátování vráceného řetězce.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern%2A>|Definuje celkový formát výsledného řetězce.|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Definuje lokalizované názvy měsíců, které mohou být zobrazeny ve výsledném řetězci.|  
  
 Následující příklad používá specifikátor formátu "m" k zobrazení hodnoty data a času.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#7)]
 [!code-vb[Formatting.DateAndTime.Standard#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#7)]  
  
 [Zpět k tabulce](#table)  
  
<a name="Roundtrip"></a>   
## <a name="the-round-trip-o-o-format-specifier"></a>Specifikátor formátu zpátečního převodu ("O", "o")  
 Specifikátor standardního formátu "O" nebo "o" představuje vlastní datum a čas formátovací řetězec pomocí vzoru, který uchovává informace o časovém pásmu a vysílá výsledný řetězec, který splňuje normu ISO 8601. Pro <xref:System.DateTime> hodnoty, tento specifikátor formátu je navržená pro zachování hodnot data a času spolu s <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> vlastnost text. Formátovaný řetězec může být analyzován zpět pomocí <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> nebo <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> metoda Pokud `styles` parametr je nastaven na <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>.  
  
 Specifikátor standardního formátu "O" nebo "o" odpovídá "yyyy '-' MM'-'dd'T' HH': 'mm':'ss '." řetězec fffffffK"vlastního formátu pro <xref:System.DateTime> hodnoty a" yyyy '-' MM'-'dd'T' HH': 'mm':'ss "." řetězec vlastního formátu fffffffzzz"pro <xref:System.DateTimeOffset> hodnoty. Dvojice jednoduchých uvozovek v tomto řetězci oddělující jednotlivé znaky, jako jsou například spojovníky, dvojtečky a písmeno "T", označují, že jednotlivé znaky jsou literály, které nelze změnit. Apostrofy se ve výstupním řetězci nezobrazují.  
  
 Specifikátor standardního formátu "O" nebo "o" (a "yyyy '-' MM'-'dd'T' HH': 'mm':'ss '." řetězec vlastního formátu fffffffK") využívá výhod tři způsoby, které ISO 8601 představuje informace o časovém pásmu zachovat <xref:System.DateTime.Kind%2A> vlastnost <xref:System.DateTime> hodnoty:  
  
-   Časové pásmo součást <xref:System.DateTimeKind.Local?displayProperty=nameWithType> hodnoty data a času je posun od času UTC (například + 01:00, -07:00). Všechny <xref:System.DateTimeOffset> hodnoty jsou také reprezentované v tomto formátu.  
  
-   Časové pásmo součást <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> hodnoty data a času "Z" (který zastupuje nulové posunutí) používá k reprezentaci UTC.  
  
-   <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> hodnoty data a času mít žádné informace o časovém pásmu.  
  
 Protože specifikátor standardního formátu "O" nebo "o" odpovídá mezinárodní standard, formátování nebo analýzy operace, která používá specifikátor vždy používá invariantní jazyková verze a gregoriánský kalendář.  
  
 Řetězce, které jsou předány `Parse`, `TryParse`, `ParseExact`, a `TryParseExact` metody <xref:System.DateTime> a <xref:System.DateTimeOffset> může být analyzován pomocí specifikátoru formátu "O" nebo "o", když jsou v jednom z následujících formátů. V případě třídy <xref:System.DateTime> objekty, analýzy, na které můžete volat přetížení by mělo rovněž zahrnovat `styles` parametr s hodnotou <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>. Všimněte si, že pokud zavoláte metodu analýzy s řetězci vlastního formátu, který odpovídá "O" nebo "o" specifikátorem formátu, nebudete získáte stejné výsledky jako "O" nebo "o". Je to proto, že analýza metody, které používají vlastní formátovací řetězec nelze analyzovat řetězcové vyjádření hodnoty data a času, které nemají komponentu časového pásma, nebo použijte "Z" označuje čas UTC.  
  
 Následující příklad používá specifikátor formátu "o" k zobrazení řadu <xref:System.DateTime> hodnoty a <xref:System.DateTimeOffset> hodnotu v rámci systému v USA Tichomořské časové pásmo.  
  
 [!code-csharp-interactive[Formatting.DateAndTime.Standard#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/o1.cs#8)]
 [!code-vb[Formatting.DateAndTime.Standard#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/o1.vb#8)]  
  
 Následující příklad používá specifikátor formátu "o" pro vytvoření naformátovaného řetězce a potom obnoví původní hodnoty data a času voláním datum a čas `Parse` metody.  
  
 [!code-csharp[Formatting.DateandTime.Standard#16](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Roundtrip1.cs#16)]
 [!code-vb[Formatting.DateandTime.Standard#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/RoundTrip1.vb#16)]  
  
 [Zpět k tabulce](#table)  
  
<a name="RFC1123"></a>   
## <a name="the-rfc1123-r-r-format-specifier"></a>Specifikátor formátu RFC1123 ("R", "r")  
 Specifikátor standardního formátu "R" nebo "r" představuje vlastní data a času formátovací řetězec, který je definován <xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A?displayProperty=nameWithType> vlastnost. Tento vzor odpovídá definovanému standardu a příslušná vlastnost je určena jen pro čtení. Proto je vždy stejný bez ohledu na použitou jazykovou verzi nebo dodaného poskytovatele formátu. Řetězec vlastního formátu je "ddd, dd MMM yyyy HH':'mm':'ss 'GMT'". Při použití tohoto standardního specifikátoru formátu používá operace formátování nebo analýzy vždy neutrální jazykovou verzi.  
  
 Výsledný řetězec je ovlivněn následujícími vlastnostmi objektu <xref:System.Globalization.DateTimeFormatInfo> vrácený <xref:System.Globalization.DateTimeFormatInfo.InvariantInfo%2A?displayProperty=nameWithType> vlastnost, která představuje neutrální jazykovou verzi.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A>|Definuje formát výsledného řetězce.|  
|<xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A>|Definuje zkrácené názvy dní, které mohou být zobrazeny ve výsledném řetězci.|  
|<xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames%2A>|Definuje zkrácené názvy měsíců, které mohou být zobrazeny ve výsledném řetězci.|  
  
 Ačkoli standard RFC 1123 vyjadřuje čas jako koordinovaný univerzální čas (UTC), operace formátování nezmění hodnotu <xref:System.DateTime> objekt, který se chystáte formátovat. Proto je nutné převést <xref:System.DateTime> hodnotu na čas UTC pomocí volání <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> metoda před provedením operace formátování. Naproti tomu <xref:System.DateTimeOffset> provede tento převod automaticky; není nutné volat <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> metoda před operací formátování.  
  
 Následující příklad používá specifikátor formátu "r" k zobrazení <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnotu v rámci systému v USA Tichomořské časové pásmo.  
  
 [!code-csharp-interactive[Formatting.DateAndTime.Standard#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#9)]
 [!code-vb[Formatting.DateAndTime.Standard#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#9)]  
  
 [Zpět k tabulce](#table)  
  
<a name="Sortable"></a>   
## <a name="the-sortable-s-format-specifier"></a>Specifikátor seřaditelného formátu ("s")  
 Specifikátor standardního formátu "s" představuje vlastní data a času formátovací řetězec, který je definován <xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern%2A?displayProperty=nameWithType> vlastnost. Tento vzor odpovídá definovanému standardu (ISO 8601) a příslušná vlastnost je určena jen pro čtení. Proto je vždy stejný bez ohledu na použitou jazykovou verzi nebo dodaného poskytovatele formátu. Řetězec vlastního formátu je "yyyy'-'MM'-'dd'T'HH':'mm':'ss".  
  
 Vytvoří výsledek řetězce, které soustavně seřadit ve vzestupném nebo sestupném pořadí podle hodnoty data a času je účelem specifikátor formátu "s". V důsledku toho Ačkoli specifikátor standardního formátu "s" představuje hodnotu Datum a čas ve formátu konzistentní vzhledem k aplikacím, operace formátování nezmění hodnotu objektu datum a čas, který je právě formátován tak, aby odrážely jeho <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> vlastnost nebo její <xref:System.DateTimeOffset.Offset%2A?displayProperty=nameWithType> hodnotu. Například výsledný řetězec produkovaný formátování hodnot data a času 2014-11-15T18:32:17 + 00:00 a 2014-11-15T18:32:17 + 08:00 jsou identické.  
  
 Při použití tohoto standardního specifikátoru formátu používá operace formátování nebo analýzy vždy neutrální jazykovou verzi.  
  
 Následující příklad používá specifikátor formátu "s" k zobrazení <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnotu v rámci systému v USA Tichomořské časové pásmo.  
  
 [!code-csharp-interactive[Formatting.DateAndTime.Standard#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#10)]
 [!code-vb[Formatting.DateAndTime.Standard#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#10)]  
  
 [Zpět k tabulce](#table)  
  
<a name="ShortTime"></a>   
## <a name="the-short-time-t-format-specifier"></a>Specifikátor krátkého formátu času ("t")  
 Specifikátor standardního formátu "t" představuje vlastní data a času formátovací řetězec, který je definován aktuální <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> vlastnost. Například řetězec vlastního formátu pro neutrální jazykovou verzi je "HH:mm".  
  
 Výsledný řetězec je ovlivněn informace o formátování specifického <xref:System.Globalization.DateTimeFormatInfo> objektu. Následující tabulce jsou uvedeny <xref:System.Globalization.DateTimeFormatInfo> objektu vlastnosti, které mohou řídit formátování vráceného řetězce. Specifikátor vlastního formátu, který je vrácen <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> vlastnost některých jazykových verzí nemusí mít používat všechny vlastnosti.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A>|Definuje formát komponenty času výsledného řetězce.|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Definuje řetězec, který odděluje komponenty hodiny, minuty a sekundy v časovém údaji.|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Definuje řetězec, který označuje dobu od půlnoci do doby před polednem ve 12hodinovém formátu.|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Definuje řetězec, který označuje dobu od poledne do doby před půlnocí ve 12hodinovém formátu.|  
  
 Následující příklad používá specifikátor formátu "t" k zobrazení hodnoty data a času.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#11)]
 [!code-vb[Formatting.DateAndTime.Standard#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#11)]  
  
 [Zpět k tabulce](#table)  
  
<a name="LongTime"></a>   
## <a name="the-long-time-t-format-specifier"></a>Specifikátor dlouhého formátu času ("T")  
 Specifikátor standardního formátu "T" představuje vlastní data a času formátovací řetězec, který je definován konkrétní jazykovou verzi <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> vlastnost. Například řetězec vlastního formátu pro neutrální jazykovou verzi je "HH:mm:ss".  
  
 Následující tabulce jsou uvedeny <xref:System.Globalization.DateTimeFormatInfo> objektu vlastnosti, které mohou řídit formátování vráceného řetězce. Specifikátor vlastního formátu, který je vrácen <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> vlastnost některých jazykových verzí nemusí mít používat všechny vlastnosti.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A>|Definuje formát komponenty času výsledného řetězce.|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Definuje řetězec, který odděluje komponenty hodiny, minuty a sekundy v časovém údaji.|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Definuje řetězec, který označuje dobu od půlnoci do doby před polednem ve 12hodinovém formátu.|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Definuje řetězec, který označuje dobu od poledne do doby před půlnocí ve 12hodinovém formátu.|  
  
 Následující příklad používá specifikátor formátu "T" k zobrazení hodnoty data a času.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#12)]
 [!code-vb[Formatting.DateAndTime.Standard#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#12)]  
  
 [Zpět k tabulce](#table)  
  
<a name="UniversalSortable"></a>   
## <a name="the-universal-sortable-u-format-specifier"></a>Specifikátor univerzálního seřaditelného formátu ("u")  
 Specifikátor standardního formátu "u" představuje vlastní data a času formátovací řetězec, který je definován <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A?displayProperty=nameWithType> vlastnost. Tento vzor odpovídá definovanému standardu a příslušná vlastnost je určena jen pro čtení. Proto je vždy stejný bez ohledu na použitou jazykovou verzi nebo dodaného poskytovatele formátu. Řetězec vlastního formátu je "yyyy'-'MM'-'dd HH':'mm':'ss'Z'". Při použití tohoto standardního specifikátoru formátu používá operace formátování nebo analýzy vždy neutrální jazykovou verzi.  
  
 Ačkoli výsledný řetězec by měl vyjadřovat čas jako koordinovaný univerzální čas (UTC), žádný převod původní <xref:System.DateTime> hodnota se provádí během operace formátování. Proto je nutné převést <xref:System.DateTime> hodnotu na čas UTC pomocí volání <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> metoda před formátováním.  Naproti tomu <xref:System.DateTimeOffset> provede tento převod automaticky; není nutné volat <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> metoda před operací formátování.  
  
 Následující příklad používá specifikátor formátu "u" k zobrazení hodnoty data a času.  
  
 [!code-csharp-interactive[Formatting.DateAndTime.Standard#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Standard#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#13)]  
  
 [Zpět k tabulce](#table)  
  
<a name="UniversalFull"></a>   
## <a name="the-universal-full-u-format-specifier"></a>Specifikátor univerzálního úplného formátu ("U")  
 Specifikátor standardního formátu "U" představuje vlastní data a času formátovací řetězec, který je definován zadaná jazyková verze <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> vlastnost. Tento vzor je stejný jako vzor "F". Ale <xref:System.DateTime> hodnota se automaticky převede na UTC ještě před naformátováním.  
  
 Následující tabulce jsou uvedeny <xref:System.Globalization.DateTimeFormatInfo> objektu vlastnosti, které mohou řídit formátování vráceného řetězce. Specifikátor vlastního formátu, který je vrácen <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A> vlastnost některých jazykových verzí nemusí mít používat všechny vlastnosti.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A>|Definuje celkový formát výsledného řetězce.|  
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Definuje lokalizované názvy dní, které mohou být zobrazeny ve výsledném řetězci.|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Definuje lokalizované názvy měsíců, které mohou být zobrazeny ve výsledném řetězci.|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Definuje řetězec, který odděluje komponenty hodiny, minuty a sekundy v časovém údaji.|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Definuje řetězec, který označuje dobu od půlnoci do doby před polednem ve 12hodinovém formátu.|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Definuje řetězec, který označuje dobu od poledne do doby před půlnocí ve 12hodinovém formátu.|  
  
 Specifikátor formátu "U" není podporován <xref:System.DateTimeOffset> a vyvolá výjimku <xref:System.FormatException> Pokud je použita k formátování <xref:System.DateTimeOffset> hodnotu.  
  
 Následující příklad používá specifikátor formátu "U" k zobrazení hodnoty data a času.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#14)]
 [!code-vb[Formatting.DateAndTime.Standard#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#14)]  
  
 [Zpět k tabulce](#table)  
  
<a name="YearMonth"></a>   
## <a name="the-year-month-y-y-format-specifier"></a>Specifikátor formátu roku a měsíce ("Y", "y")  
 Specifikátor standardního formátu "Y" nebo "y" představuje vlastní data a času formátovací řetězec, který je definován <xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern%2A?displayProperty=nameWithType> vlastnosti zadané jazykové verze. Například řetězec vlastního formátu pro neutrální jazykovou verzi je "yyyy MMMM".  
  
 Následující tabulce jsou uvedeny <xref:System.Globalization.DateTimeFormatInfo> objektu vlastnosti, které řídí formátování vráceného řetězce.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern%2A>|Definuje celkový formát výsledného řetězce.|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Definuje lokalizované názvy měsíců, které mohou být zobrazeny ve výsledném řetězci.|  
  
 Následující příklad používá specifikátor formátu "y" k zobrazení hodnoty data a času.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#15](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#15)]
 [!code-vb[Formatting.DateAndTime.Standard#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#15)]  
  
 [Zpět k tabulce](#table)  
  
<a name="Notes"></a>   
## <a name="notes"></a>Poznámky  
  
### <a name="control-panel-settings"></a>Nastavení části Ovládací panely  
 Nastavení **místní a jazykové nastavení** položky v Ovládacích panelech ovlivní výsledný řetězec vytvořený při operaci formátování. Tato nastavení slouží k inicializaci <xref:System.Globalization.DateTimeFormatInfo> objekt přidružený k aktuální jazykové verzi vlákna, které poskytuje hodnoty použité k řízení formátování. Počítače, které používají různá nastavení, generují různé výsledné řetězce.  
  
 Kromě toho, pokud použijete <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> konstruktor k vytvoření instance nového <xref:System.Globalization.CultureInfo> objekt, který představuje stejnou jazykovou verzi jako aktuální jazyková verze systému, jakákoli vlastní nastavení podle **místní a jazykové nastavení** v Ovládacích panelech budou použita pro nový <xref:System.Globalization.CultureInfo> objektu. Můžete použít <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> konstruktor k vytvoření <xref:System.Globalization.CultureInfo> objekt, který nepředstavuje vlastní nastavení systému.  
  
### <a name="datetimeformatinfo-properties"></a>Vlastnosti DateTimeFormatInfo  
 Formátování je ovlivněno vlastnostmi aktuálního <xref:System.Globalization.DateTimeFormatInfo> objekt, který je poskytnut implicitně aktuální jazykovou verzí vlákna nebo explicitně parametrem <xref:System.IFormatProvider> parametru metody, která vyvolá formátování. Pro <xref:System.IFormatProvider> parametr, vaše aplikace měla určit <xref:System.Globalization.CultureInfo> objektu, který představuje jazykovou verzi, nebo <xref:System.Globalization.DateTimeFormatInfo> objektu, který představuje datum a čas konvence formátování konkrétní jazykové verze. Standardní hodnoty data a specifikátory formátu času jsou aliasy pro vzory, které jsou definované vlastnostmi aktuálního objektu formátování <xref:System.Globalization.DateTimeFormatInfo> objektu. Aplikace může změnit výsledek produkovaný některé standardní hodnoty data a specifikátory formátu času změnou odpovídající data a času naformátovat vzorů <xref:System.Globalization.DateTimeFormatInfo> vlastnost.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.DateTime?displayProperty=nameWithType>  
- <xref:System.DateTimeOffset?displayProperty=nameWithType>  
- [Typy formátování](../../../docs/standard/base-types/formatting-types.md)  
- [Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)  
- [Ukázka: Formátovací nástroj rozhraní .NET Framework 4](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
