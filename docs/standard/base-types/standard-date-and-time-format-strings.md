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
ms.openlocfilehash: cfa44187d846c72f0dfd4fb131cacbe41648dd32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579805"
---
# <a name="standard-date-and-time-format-strings"></a>Standardní řetězce formátu data a času
Řetězec standardního formátu data a času používá pro definování textového vyjádření hodnoty data a času jeden specifikátor formátu. Formátovací řetězec datum a čas, který obsahuje více než jeden znak, včetně mezer, interpretována jako vlastní data a času řetězec formátu; Další informace najdete v tématu [vlastní řetězců data a času formát](../../../docs/standard/base-types/custom-date-and-time-format-strings.md). Řetězec standardního nebo vlastního formátu lze používat dvěma způsoby:  
  
-   Chcete-li definovat řetězec, který je výsledkem operace formátování.  
  
-   Chcete-li definovat textovou reprezentaci hodnoty data a času, který lze převést na <xref:System.DateTime> nebo <xref:System.DateTimeOffset> hodnoty operaci analýzy.  
  
 Standardní hodnoty data a řetězce formátu časových lze použít s oběma <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnoty.  
  
> [!TIP]
>  Si můžete stáhnout [formátování nástroj](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d), aplikace, která umožňuje použití formátu řetězce na hodnotu numerické nebo datum a čas hodnoty a zobrazí výsledný řetězec.  
  
<a name="table"></a> Následující tabulka popisuje standardní hodnoty data a času specifikátory formátu. Pokud není uvedeno jinak, konkrétní standardní formátu data a času specifikátor vytváří identické řetězcové vyjádření bez ohledu na to, zda je použit s <xref:System.DateTime> nebo <xref:System.DateTimeOffset> hodnotu. Najdete v článku [poznámky](#Notes) části Další informace o používání standardní řetězců data a času formátu.  
  
|Specifikátor formátu|Popis|Příklady|  
|----------------------|-----------------|--------------|  
|"d"|Vzor krátkého formátu data.<br /><br /> Další informace:[The krátkého data ("d") specifikátor formátu](#ShortDate).|2009-06-15T13:45:30 -> 6/15/2009 (en US)<br /><br /> 2009-06-15T13:45:30 -> 15/06/2009 (fr-FR)<br /><br /> 2009-06-15T13:45:30 -> 2009/06/15 (ja-JP)|  
|"D"|Vzor dlouhého formátu data.<br /><br /> Další informace:[specifikátor formát dlouhého data ("D")](#LongDate).|2009-06-15T13:45:30 -> pondělí, 15 června 2009 (en US)<br /><br /> 2009-06-15T13:45:30 -> 15 г июня 2009. (ru-RU)<br /><br /> 2009-06-15T13:45:30 -> Montag, 15. Juni 2009 (de-DE)|  
|"f"|Vzor úplného formátu data/času (krátkého formátu času).<br /><br /> Další informace: [úplné data a krátkého času ("f") specifikátor formátu](#FullDateShortTime).|2009-06-15T13:45:30 -> pondělí 15. června 2009 1:45 odp (en US)<br /><br /> 2009-06-15T13:45:30 -> LIB 15 juni 2009 13:45 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 1:45 μμ (el-GR)|  
|"F"|Vzor úplného formátu data/času (dlouhého formátu času).<br /><br /> Další informace: [úplné dlouho specifikátor data a času ("F") formát](#FullDateLongTime).|2009-06-15T13:45:30 -> pondělí 15. června 2009 1:45:30 odp (en US)<br /><br /> 2009-06-15T13:45:30 -> LIB 15 juni 2009 13:45:30 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 1:45:30 μμ (el-GR)|  
|"g"|Vzor obecného formátu data/času (krátkého formátu času).<br /><br /> Další informace: [obecné data a krátkého času ("g") specifikátor formátu](#GeneralDateShortTime).|2009-06-15T13:45:30 -> 6/15/2009 1:45 odp (en US)<br /><br /> 2009-06-15T13:45:30 -> 15/06/2009 13:45 (es-ES)<br /><br /> 2009-06-15T13:45:30 -> 2009/6/15 13:45 (zh-CN)|  
|"G"|Vzor obecného formátu data a času (dlouhého formátu času).<br /><br /> Další informace: [obecné dlouho specifikátor data a času ("G") formát](#GeneralDateLongTime).|2009-06-15T13:45:30 -> 6/15/2009 1:45:30 odp (en US)<br /><br /> 2009-06-15T13:45:30 -> 15/06/2009 13:45:30 (es-ES)<br /><br /> 2009-06-15T13:45:30 -> 2009/6/15 13:45:30 (zh-CN)|  
|"M", "m"|Vzor formátu měsíce/dne.<br /><br /> Další informace: [specifikátor formátu měsíci ("M", "m")](#MonthDay).|2009-06-15T13:45:30 -> 15. června (en US)<br /><br /> 2009-06-15T13:45:30 -&GT; 15. juni (da-DK)<br /><br /> 2009-06-15T13:45:30 -> 15 Juni (id-ID)|  
|"O", "o"|Vzor formátu data/času zpátečního převodu.<br /><br /> Další informace: [specifikátor formátu Round-trip ("O", "o")](#Roundtrip).|<xref:System.DateTime> Hodnoty:<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Local)--> 2009-06-15T13:45:30.0000000-07:00<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Utc)--> 2009-06-15T13:45:30.0000000Z<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Unspecified)--> 2009-06-15T13:45:30.0000000<br /><br /> <xref:System.DateTimeOffset> Hodnoty:<br /><br /> 2009-06-15T13:45:30-07:00--&GT; 2009-06-15T13:45:30.0000000-07:00|  
|"R", "r"|Vzor RFC1123.<br /><br /> Další informace: [RFC1123 ("R", "r") specifikátor formátu](#RFC1123).|2009-06-15T13:45:30 -> Mon, 15 června 2009 20:45:30 GMT|  
|"s"|Vzor seřaditelného formátu data/času.<br /><br /> Další informace: [řazení ("s") specifikátor formátu](#Sortable).|2009-06-15T13:45:30 (DateTimeKind.Local) -> 2009-06-15T13:45:30<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Utc) -> 2009-06-15T13:45:30|  
|"t"|Vzor krátkého formátu času.<br /><br /> Další informace: [The krátkého času ("t") specifikátor formátu](#ShortTime).|2009-06-15T13:45:30 -> 1:45 odp (en US)<br /><br /> 2009-06-15T13:45:30 -> 13:45 (personálního oddělení lidských zdrojů)<br /><br /> 2009-06-15T13:45:30 -> 01:45 م (ar – TEDY)|  
|"T"|Vzor dlouhého formátu času.<br /><br /> Další informace: [specifikátor formátu dlouhého času ("T")](#LongTime).|2009-06-15T13:45:30 -> 1:45:30 odp (en US)<br /><br /> 2009-06-15T13:45:30 -> 13:45:30 (personálního oddělení lidských zdrojů)<br /><br /> 2009-06-15T13:45:30 -> 01:45:30 م (ar – TEDY)|  
|"u"|Vzor univerzálního seřaditelného formátu data/času.<br /><br /> Další informace: [The Univerzální seřaditelný ("u") specifikátor formátu](#UniversalSortable).|S <xref:System.DateTime> hodnota: 2009-06-15T13:45:30 -> 2009-06-15 13:45:30Z<br /><br /> S <xref:System.DateTimeOffset> hodnota: 2009-06-15T13:45:30 -> 2009-06-15 20:45:30Z|  
|"U"|Vzor univerzálního úplného formátu data/času.<br /><br /> Další informace: [The univerzální úplný ("U") specifikátor formátu](#UniversalFull).|2009-06-15T13:45:30 -> pondělí 15. června 2009 8:45:30 PM (en US)<br /><br /> 2009-06-15T13:45:30 -> LIB 15 juni 2009 20:45:30 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 8:45:30 μμ (el-GR)|  
|"Y", "y"|Vzor formátu roku a měsíce.<br /><br /> Další informace: [specifikátor formátu měsíce roce ("Y")](#YearMonth).|2009-06-15T13:45:30 -> června 2009 (en US)<br /><br /> 2009-06-15T13:45:30 -> juni 2009 (da-DK)<br /><br /> 2009-06-15T13:45:30 -> Juni 2009 (id-ID)|  
|Jakýkoli jiný samostatný znak|Neznámý specifikátor.|Vyvolá za běhu <xref:System.FormatException>.|  
  
## <a name="how-standard-format-strings-work"></a>Jak fungují řetězce standardního formátu  
 V rámci operace formátování je řetězec standardního formátu pouze aliasem pro řetězec vlastního formátu. Výhodou používání aliasu pro odkaz na řetězec vlastního formátu je skutečnost, že ačkoli alias zůstane neutrální, řetězec vlastního formátu se může změnit. Toto je důležité, protože řetězcová reprezentace hodnot data a času se obvykle liší podle jazykové verze. Například řetězec standardního formátu "d" označuje, že hodnota data a času má být zobrazena pomocí vzoru krátkého formátu data. Pro neutrální jazykovou verzi je použit formát "MM/dd/yyyy". Pro jazykovou verzi fr-FR je to formát "dd/MM/yyyy". Pro jazykovou verzi ja-JP je to formát "yyyy/MM/dd".  
  
 Pokud je řetězec standardního formátu v rámci operace formátování namapován na řetězec vlastního formátu konkrétní jazykové verze, může vaše aplikace definovat konkrétní jazykovou verzi, jejíž řetězce vlastního formátu se používají jedním z těchto způsobů:  
  
-   Můžete použít výchozí (nebo aktuální) jazykovou verzi. Následující příklad zobrazí datum pomocí krátkého formátu data aktuální jazykové verze. V tomto případě je aktuální jazyková verze nastavena na en-US.  
  
     [!code-csharp[System.DateTime.Conceptual.Formatting#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#1)]
     [!code-vb[System.DateTime.Conceptual.Formatting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#1)]  
  
-   Můžete předat <xref:System.Globalization.CultureInfo> objekt představující jazykovou verzi, jejíž formátování má být použita na metodu, která má <xref:System.IFormatProvider> parametr. Následující příklad zobrazí datum pomocí formátu krátkého data jazykové verze pt-BR.  
  
     [!code-csharp[System.DateTime.Conceptual.Formatting#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#2)]
     [!code-vb[System.DateTime.Conceptual.Formatting#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#2)]  
  
-   Můžete předat <xref:System.Globalization.DateTimeFormatInfo> objekt, který poskytuje informace o metodě, která má formátování <xref:System.IFormatProvider> parametr. Následující příklad zobrazí datum ve formátu krátkého data z <xref:System.Globalization.DateTimeFormatInfo> objekt pro jazykovou verzi personálního oddělení lidských zdrojů.  
  
     [!code-csharp[System.DateTime.Conceptual.Formatting#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#3)]
     [!code-vb[System.DateTime.Conceptual.Formatting#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#3)]  
  
> [!NOTE]
>  Informace o přizpůsobení vzory nebo řetězce použité při formátování hodnoty data a času najdete v tématu <xref:System.Globalization.NumberFormatInfo> třída tématu.  
  
 V některých případech slouží řetězec standardního formátu jako vhodná zkratka pro řetězec vlastního delšího formátu, který je neutrální. Do této kategorie patří čtyři řetězce standardního formátu: "O" (nebo "o"), "R" (nebo "r"), "s" a "u". Tyto řetězce odpovídají řetězcům vlastního formátu, které jsou definovány neutrální jazykovou verzí. Vytvářejí řetězcové reprezentace hodnot data a času, které mají být identické napříč jazykovými verzemi. Následující tabulka obsahuje informace o těchto čtyřech řetězcích standardního formátu data a času.  
  
|Řetězec standardního formátu|Definovaný vlastností DateTimeFormatInfo.InvariantInfo|Řetězec vlastního formátu|  
|----------------------------|----------------------------------------------------------|--------------------------|  
|"O" nebo "o"|Žádné|yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffzz|  
|"R" nebo "r"|<xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A>|ddd, dd MMM yyyy HH':'mm':'ss 'GMT'|  
|"s"|<xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern%2A>|yyyy'-'MM'-'dd'T'HH':'mm':'ss|  
|"u"|<xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>|yyyy'-'MM'-'dd HH':'mm':'ss'Z'|  
  
 Standardní řetězce formátu lze také v operacích s analýzy <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> metody, které vyžadují vstupní řetězec tak, aby odpovídala přesně určitý vzor pro operace analýzy proběhla úspěšně. Mnoho řetězců standardního formátu je namapováno na několik řetězců vlastního formátu. Hodnotu data a času lze tedy vyjádřit v celé řadě formátů a operace analýzy i tak proběhne úspěšně. Můžete určit vlastní řetězec formátu nebo řetězců, které odpovídají na standardní formát řetězec voláním <xref:System.Globalization.DateTimeFormatInfo.GetAllDateTimePatterns%28System.Char%29?displayProperty=nameWithType> metoda. Následující příklad zobrazí řetězce vlastního formátu, které mapují řetězec standardního formátu "d" (vzor krátkého formátu data).  
  
 [!code-csharp[Formatting.DateAndTime.Standard#17](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/stdandparsing1.cs#17)]
 [!code-vb[Formatting.DateAndTime.Standard#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/stdandparsing1.vb#17)]  
  
 Následující části popisují specifikátory standardní formát pro <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnoty.  
  
<a name="ShortDate"></a>   
## <a name="the-short-date-d-format-specifier"></a>Specifikátor krátkého formátu data ("d")  
 Specifikátor standardní formát "d" představuje vlastní data a času řetězec formátu, který je definován pomocí konkrétní jazykové verze <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> vlastnost. Například řetězec vlastní formát, který je vrácený <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A> vlastnosti neutrální jazykové verze je "MM/dd/rrrr".  
  
 Následující tabulka uvádí <xref:System.Globalization.DateTimeFormatInfo> objektu vlastnosti, které řídí formátování vrácený řetězec.  
  
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
 Specifikátor standardní formát "D" představuje vlastní data a času řetězec formátu, který je definován aktuální <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> vlastnost. Například řetězec vlastního formátu pro neutrální jazykovou verzi je "dddd, dd MMMM yyyy".  
  
 Následující tabulka uvádí vlastnosti <xref:System.Globalization.DateTimeFormatInfo> objekt, který řídí formátování vrácený řetězec.  
  
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
  
 Výsledný řetězec je vliv informace o konkrétní formátování <xref:System.Globalization.DateTimeFormatInfo> objektu. Následující tabulka uvádí <xref:System.Globalization.DateTimeFormatInfo> objektu vlastnosti, které mohou řídit formátování vrácený řetězec. Specifikátor vlastní formát vrácený <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> a <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> některých jazykových verzí nemusí mít používat všechny vlastnosti.  
  
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
 Standardní formát specifikátor "F" představuje vlastní data a času řetězec formátu, který je definován aktuální <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> vlastnost. Například řetězec vlastního formátu pro neutrální jazykovou verzi je "dddd, dd MMMM yyyy HH:mm:ss".  
  
 Následující tabulka uvádí <xref:System.Globalization.DateTimeFormatInfo> objektu vlastnosti, které mohou řídit formátování vrácený řetězec. Specifikátor vlastní formát, který je vrácený <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A> nemusí mít vlastnost některých jazykových verzí používat všechny vlastnosti.  
  
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
  
 Výsledný řetězec je vliv informace o konkrétní formátování <xref:System.Globalization.DateTimeFormatInfo> objektu. Následující tabulka uvádí <xref:System.Globalization.DateTimeFormatInfo> objektu vlastnosti, které mohou řídit formátování vrácený řetězec. Specifikátor vlastní formát, který je vrácený <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> a <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> některých jazykových verzí nemusí mít používat všechny vlastnosti.  
  
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
  
 Výsledný řetězec je vliv informace o konkrétní formátování <xref:System.Globalization.DateTimeFormatInfo> objektu. Následující tabulka uvádí <xref:System.Globalization.DateTimeFormatInfo> objektu vlastnosti, které mohou řídit formátování vrácený řetězec. Specifikátor vlastní formát, který je vrácený <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> a <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> některých jazykových verzí nemusí mít používat všechny vlastnosti.  
  
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
 Standardní formát specifikátor "M" nebo "m" představuje vlastní data a času řetězec formátu, který je definován aktuální <xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern%2A?displayProperty=nameWithType> vlastnost. Například řetězec vlastního formátu pro neutrální jazykovou verzi je "MMMM dd".  
  
 Následující tabulka uvádí <xref:System.Globalization.DateTimeFormatInfo> objektu vlastnosti, které řídí formátování vrácený řetězec.  
  
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
 Standardní formát specifikátor "O" nebo "o" představuje vlastní data a času řetězec formátu pomocí vzoru, která uchovává informace o časovém pásmu a vysílá výsledný řetězec, který splňuje normu ISO 8601. Pro <xref:System.DateTime> hodnoty, tento specifikátor formátu slouží k zachování hodnoty data a času spolu s <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> vlastnost v textu. Formátovaný řetězec může být analyzován zpět pomocí <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> nebo <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> metoda Pokud `styles` parametr je nastaven na <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>.  
  
 Standardní formát specifikátor "O" nebo "o" odpovídá "rrrr '-' MM'-'dd'T' HH': 'mm':'ss '." fffffffK"vlastní řetězec formátu pro <xref:System.DateTime> hodnoty a" rrrr '-' MM'-'dd'T' HH': 'mm':'ss '. " fffffffzzz"vlastní řetězec formátu pro <xref:System.DateTimeOffset> hodnoty. Dvojice jednoduchých uvozovek v tomto řetězci oddělující jednotlivé znaky, jako jsou například spojovníky, dvojtečky a písmeno "T", označují, že jednotlivé znaky jsou literály, které nelze změnit. Apostrofy se ve výstupním řetězci nezobrazují.  
  
 Standardní formát specifikátor "O" nebo "o" (a "rrrr '-' MM'-'dd'T' HH': 'mm':'ss '." fffffffK"vlastní řetězec formátu) využívá výhod tři způsoby, které ISO 8601 představuje informace o časovém pásmu pro zachování <xref:System.DateTime.Kind%2A> vlastnost <xref:System.DateTime> hodnoty:  
  
-   Časové pásmo součást <xref:System.DateTimeKind.Local?displayProperty=nameWithType> hodnoty data a času je posun od času UTC (například + 01:00, -07:00). Všechny <xref:System.DateTimeOffset> hodnoty jsou také reprezentované v tomto formátu.  
  
-   Časové pásmo součást <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> hodnoty data a času "Z" (který zastupuje nula posun) používá k reprezentaci UTC.  
  
-   <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> hodnoty data a času mít žádné informace o časovém pásmu.  
  
 Protože O "nebo"o"standardní formát specifikátor vyhovuje mezinárodní standard, formátování nebo analýza operace, která používá specifikátor vždy používá neutrální jazykovou verzi a gregoriánském kalendáři.  
  
 Řetězce, které se budou předávat `Parse`, `TryParse`, `ParseExact`, a `TryParseExact` metody <xref:System.DateTime> a <xref:System.DateTimeOffset> lze analyzovat pomocí specifikátor formátu "O" nebo "o", pokud jsou v jednom z těchto formátů. U <xref:System.DateTime> objekty, musí rovněž zahrnovat analýzy přetížení, které zavoláte `styles` parametr s hodnotou <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>. Všimněte si, že pokud volání metody analýzy řetězcem vlastní formát, který odpovídá "O" nebo "o" formátovací řetězec, nebude získat stejné výsledky jako "O" nebo "o". To je proto analýza metody, které používají vlastní řetězec formátu nelze analyzovat řetězcovou reprezentaci hodnoty data a času, které nemají komponentu časového pásma nebo používá se k označení UTC "Z".  
  
 Následující příklad používá specifikátor formátu "o" zobrazíte řadu <xref:System.DateTime> hodnoty a <xref:System.DateTimeOffset> hodnotu v systému v USA Tichomořském časovém pásmu.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/o1.cs#8)]
 [!code-vb[Formatting.DateAndTime.Standard#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/o1.vb#8)]  
  
 Následující příklad používá specifikátor formátu "o" k vytvoření formátovaný řetězec a poté obnoví původní hodnota data a času voláním datum a čas `Parse` metoda.  
  
 [!code-csharp[Formatting.DateandTime.Standard#16](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Roundtrip1.cs#16)]
 [!code-vb[Formatting.DateandTime.Standard#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/RoundTrip1.vb#16)]  
  
 [Zpět k tabulce](#table)  
  
<a name="RFC1123"></a>   
## <a name="the-rfc1123-r-r-format-specifier"></a>Specifikátor formátu RFC1123 ("R", "r")  
 Standardní formát specifikátor "R" nebo "r" představuje vlastní data a času řetězec formátu, který je definován <xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A?displayProperty=nameWithType> vlastnost. Tento vzor odpovídá definovanému standardu a příslušná vlastnost je určena jen pro čtení. Proto je vždy stejný bez ohledu na použitou jazykovou verzi nebo dodaného poskytovatele formátu. Řetězec vlastního formátu je "ddd, dd MMM yyyy HH':'mm':'ss 'GMT'". Při použití tohoto standardního specifikátoru formátu používá operace formátování nebo analýzy vždy neutrální jazykovou verzi.  
  
 Výsledný řetězec je vliv následující vlastnosti <xref:System.Globalization.DateTimeFormatInfo> objekt vrácený <xref:System.Globalization.DateTimeFormatInfo.InvariantInfo%2A?displayProperty=nameWithType> vlastnost, která představuje neutrální jazykovou verzi.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A>|Definuje formát výsledného řetězce.|  
|<xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A>|Definuje zkrácené názvy dní, které mohou být zobrazeny ve výsledném řetězci.|  
|<xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames%2A>|Definuje zkrácené názvy měsíců, které mohou být zobrazeny ve výsledném řetězci.|  
  
 Ačkoli standard RFC 1123 vyjadřuje čas jako koordinovaný světový čas (UTC), formátování operaci nelze změnit hodnotu <xref:System.DateTime> objektu, která je formátována. Proto je nutné převést <xref:System.DateTime> hodnotu na čas UTC voláním <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> metoda před provedením operace formátování. Naproti tomu <xref:System.DateTimeOffset> hodnoty provést tento převod automaticky, není nutné volat <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> metoda před provedením operace formátování.  
  
 Následující příklad používá specifikátor formátu "r" k zobrazení <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnotu v systému v USA Tichomořském časovém pásmu.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#9)]
 [!code-vb[Formatting.DateAndTime.Standard#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#9)]  
  
 [Zpět k tabulce](#table)  
  
<a name="Sortable"></a>   
## <a name="the-sortable-s-format-specifier"></a>Specifikátor seřaditelného formátu ("s")  
 Specifikátor standardní formát "s" představuje vlastní data a času řetězec formátu, který je definován <xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern%2A?displayProperty=nameWithType> vlastnost. Tento vzor odpovídá definovanému standardu (ISO 8601) a příslušná vlastnost je určena jen pro čtení. Proto je vždy stejný bez ohledu na použitou jazykovou verzi nebo dodaného poskytovatele formátu. Řetězec vlastního formátu je "yyyy'-'MM'-'dd'T'HH':'mm':'ss".  
  
 Účelem specifikátor formátu "s" je vytvořit výsledek řetězce, které konzistentně seřadit ve vzestupném nebo sestupném pořadí podle hodnoty data a času. Výsledkem je, ačkoli specifikátor standardní formát "s" představuje hodnotu Datum a čas ve formátu konzistentní, formátování operaci nezmění hodnota, datum a čas objektu, který je právě formátován tak, aby odrážela jeho <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> vlastnost nebo jeho <xref:System.DateTimeOffset.Offset%2A?displayProperty=nameWithType> hodnotu. Například řetězce výsledek produkovaný formátování data a času hodnoty 2014-11-15T18:32:17 + 00:00 a 2014-11-15T18:32:17 + 08:00 jsou identické.  
  
 Při použití tohoto standardního specifikátoru formátu používá operace formátování nebo analýzy vždy neutrální jazykovou verzi.  
  
 Následující příklad používá specifikátor formátu "s" k zobrazení <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnotu v systému v USA Tichomořském časovém pásmu.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#10)]
 [!code-vb[Formatting.DateAndTime.Standard#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#10)]  
  
 [Zpět k tabulce](#table)  
  
<a name="ShortTime"></a>   
## <a name="the-short-time-t-format-specifier"></a>Specifikátor krátkého formátu času ("t")  
 Specifikátor standardní formát "t" představuje vlastní data a času řetězec formátu, který je definován aktuální <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> vlastnost. Například řetězec vlastního formátu pro neutrální jazykovou verzi je "HH:mm".  
  
 Výsledný řetězec je vliv informace o konkrétní formátování <xref:System.Globalization.DateTimeFormatInfo> objektu. Následující tabulka uvádí <xref:System.Globalization.DateTimeFormatInfo> objektu vlastnosti, které mohou řídit formátování vrácený řetězec. Specifikátor vlastní formát, který je vrácený <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> nemusí mít vlastnost některých jazykových verzí používat všechny vlastnosti.  
  
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
 Specifikátor standardní formát "T" představuje vlastní data a času řetězec formátu, který je definován pomocí konkrétní jazykové verze <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> vlastnost. Například řetězec vlastního formátu pro neutrální jazykovou verzi je "HH:mm:ss".  
  
 Následující tabulka uvádí <xref:System.Globalization.DateTimeFormatInfo> objektu vlastnosti, které mohou řídit formátování vrácený řetězec. Specifikátor vlastní formát, který je vrácený <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> nemusí mít vlastnost některých jazykových verzí používat všechny vlastnosti.  
  
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
 Specifikátor standardní formát "u" představuje vlastní data a času řetězec formátu, který je definován <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A?displayProperty=nameWithType> vlastnost. Tento vzor odpovídá definovanému standardu a příslušná vlastnost je určena jen pro čtení. Proto je vždy stejný bez ohledu na použitou jazykovou verzi nebo dodaného poskytovatele formátu. Řetězec vlastního formátu je "yyyy'-'MM'-'dd HH':'mm':'ss'Z'". Při použití tohoto standardního specifikátoru formátu používá operace formátování nebo analýzy vždy neutrální jazykovou verzi.  
  
 I když výsledný řetězec by měl vyjadřovat čas jako koordinovaný světový čas (UTC), žádný převod původní <xref:System.DateTime> hodnota provádí během operace formátování. Proto je nutné převést <xref:System.DateTime> hodnotu na čas UTC voláním <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> metoda před jejím formátováním.  Naproti tomu <xref:System.DateTimeOffset> hodnoty provést tento převod automaticky, není nutné volat <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> metoda před provedením operace formátování.  
  
 Následující příklad používá specifikátor formátu "u" k zobrazení hodnoty data a času.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Standard#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#13)]  
  
 [Zpět k tabulce](#table)  
  
<a name="UniversalFull"></a>   
## <a name="the-universal-full-u-format-specifier"></a>Specifikátor univerzálního úplného formátu ("U")  
 Specifikátor standardní formát "U" představuje vlastní data a času řetězec formátu, který je definován zadanou jazykovou verzi <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> vlastnost. Tento vzor je stejný jako vzor "F". Ale <xref:System.DateTime> hodnota je automaticky převeden na čas UTC dříve, než je naformátována.  
  
 Následující tabulka uvádí <xref:System.Globalization.DateTimeFormatInfo> objektu vlastnosti, které mohou řídit formátování vrácený řetězec. Specifikátor vlastní formát, který je vrácený <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A> nemusí mít vlastnost některých jazykových verzí používat všechny vlastnosti.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A>|Definuje celkový formát výsledného řetězce.|  
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Definuje lokalizované názvy dní, které mohou být zobrazeny ve výsledném řetězci.|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Definuje lokalizované názvy měsíců, které mohou být zobrazeny ve výsledném řetězci.|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Definuje řetězec, který odděluje komponenty hodiny, minuty a sekundy v časovém údaji.|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Definuje řetězec, který označuje dobu od půlnoci do doby před polednem ve 12hodinovém formátu.|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Definuje řetězec, který označuje dobu od poledne do doby před půlnocí ve 12hodinovém formátu.|  
  
 Specifikátor formátu "U" není podporována <xref:System.DateTimeOffset> typ a vrátí <xref:System.FormatException> Pokud je použita k formátování <xref:System.DateTimeOffset> hodnotu.  
  
 Následující příklad používá specifikátor formátu "U" k zobrazení hodnoty data a času.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#14)]
 [!code-vb[Formatting.DateAndTime.Standard#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#14)]  
  
 [Zpět k tabulce](#table)  
  
<a name="YearMonth"></a>   
## <a name="the-year-month-y-y-format-specifier"></a>Specifikátor formátu roku a měsíce ("Y", "y")  
 Standardní formát specifikátor "Y" nebo "y" představuje vlastní data a času řetězec formátu, který je definován <xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern%2A?displayProperty=nameWithType> vlastnost zadanou jazykovou verzi. Například řetězec vlastního formátu pro neutrální jazykovou verzi je "yyyy MMMM".  
  
 Následující tabulka uvádí <xref:System.Globalization.DateTimeFormatInfo> objektu vlastnosti, které řídí formátování vrácený řetězec.  
  
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
 Nastavení v **místní a jazykové nastavení** položky v Ovládacích panelech vliv výsledný řetězec vytvořený při operaci formátování. Tato nastavení slouží k inicializaci <xref:System.Globalization.DateTimeFormatInfo> objekt přidružený k aktuální jazykovou verzi vlákna, které poskytuje hodnoty použité k řízení formátování. Počítače, které používají různá nastavení, generují různé výsledné řetězce.  
  
 Kromě toho, pokud použijete <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> konstruktor k vytvoření instance nového <xref:System.Globalization.CultureInfo> objekt, který reprezentuje stejnou jazykovou verzi jako aktuální systémovou kulturu jakékoli vlastní nastavení **místní a jazykové nastavení** na ovládacím panelu se použijí k novému <xref:System.Globalization.CultureInfo> objektu. Můžete použít <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> konstruktor k vytvoření <xref:System.Globalization.CultureInfo> objekt, který vlastní nastavení systému.  
  
### <a name="datetimeformatinfo-properties"></a>Vlastnosti DateTimeFormatInfo  
 Formátování je ovlivněno vlastnosti aktuální <xref:System.Globalization.DateTimeFormatInfo> objekt, který je poskytnut implicitně aktuální jazykovou verzi vlákna nebo explicitně pomocí <xref:System.IFormatProvider> parametru metody, která vyvolá formátování. Pro <xref:System.IFormatProvider> parametr, vaše aplikace měla určit <xref:System.Globalization.CultureInfo> objekt, který představuje jazykovou verzi, nebo <xref:System.Globalization.DateTimeFormatInfo> objekt, který představuje datum a čas – formátování konvence konkrétní jazykové verzi. Spousta standardní hodnoty data a času specifikátory formátu jsou aliasy pro formátování vzory definované vlastnosti aktuální <xref:System.Globalization.DateTimeFormatInfo> objektu. Aplikace můžete změnit výsledku vytvořeného některé standardní hodnoty data a času specifikátory formátu změnou odpovídající datum a čas vzorky formátu k odpovídající položce <xref:System.Globalization.DateTimeFormatInfo> vlastnost.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.DateTime?displayProperty=nameWithType>  
 <xref:System.DateTimeOffset?displayProperty=nameWithType>  
 [Typy formátování](../../../docs/standard/base-types/formatting-types.md)  
 [Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)  
 [Ukázka: Rozhraní .NET Framework 4 formátování nástroj](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
