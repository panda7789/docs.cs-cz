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
ms.openlocfilehash: efa3abdcb7aa9db6dee4f772c1c1564947151c96
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949601"
---
# <a name="standard-date-and-time-format-strings"></a>Standardní řetězce formátu data a času
Řetězec standardního formátu data a času používá pro definování textového vyjádření hodnoty data a času jeden specifikátor formátu. Libovolný řetězec formátu data a času, který obsahuje více než jeden znak, včetně prázdných znaků, je interpretován jako řetězec vlastního formátu data a času. Další informace naleznete v tématu [Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md). Řetězec standardního nebo vlastního formátu lze používat dvěma způsoby:  
  
- Chcete-li definovat řetězec, který je výsledkem operace formátování.  
  
- Chcete-li definovat textovou reprezentaci hodnoty data a času, která může být převedena <xref:System.DateTimeOffset> na <xref:System.DateTime> hodnotu nebo pomocí operace analýzy.  

> [!TIP]
>  Můžete si stáhnout [formátovací nástroj](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d), aplikaci, která umožňuje použít řetězce formátu buď na číselné, nebo na hodnoty data a času a zobrazuje výsledný řetězec.  

Řetězce standardního formátu data a času lze použít s <xref:System.DateTime> <xref:System.DateTimeOffset> hodnotami i.  
  
[!INCLUDE[C# interactive-note](~/includes/csharp-interactive-with-utc-partial-note.md)] 

<a name="table"></a>Následující tabulka popisuje standardní specifikátory formátu data a času. Není-li uvedeno jinak, konkrétní specifikátor standardního formátu data a času vytváří identickou řetězcovou reprezentaci bez ohledu na to, zda <xref:System.DateTime> je použit <xref:System.DateTimeOffset> s hodnotou nebo. Další informace o použití řetězců standardního formátu data a času naleznete v části [poznámky](#Notes) .  
  
|Specifikátor formátu|Popis|Příklady|  
|----------------------|-----------------|--------------|  
|"d"|Vzor krátkého formátu data.<br /><br /> Další informace:[specifikátor krátkého formátu data ("d")](#ShortDate).|2009-06-15T13:45:30 > 6/15/2009 (EN-US)<br /><br /> 2009-06-15T13:45:30. > 15/06/2009 (fr-FR)<br /><br /> 2009-06-15T13:45:30 -> 2009/06/15 (ja-JP)|  
|"D"|Vzor dlouhého formátu data.<br /><br /> Další informace:[specifikátor dlouhého formátu data ("D")](#LongDate).|2009-06-15T13:45:30 > pondělí, 15. června 2009 (EN-US)<br /><br /> 2009-06-15T13:45:30 -> 15 июня 2009 г. (ru-RU)<br /><br /> 2009-06-15T13:45:30-> Montag, 15. Juni 2009 (de-DE)|  
|"f"|Vzor úplného formátu data/času (krátkého formátu času).<br /><br /> Další informace: [Specifikátor úplného formátu data a krátkého formátu času ("f")](#FullDateShortTime).|2009-06-15T13:45:30-> pondělí, 15. června 2009 1:45 odp. (EN-US)<br /><br /> 2009-06-15T13:45:30-> den 15 Juni 2009 13:45 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 1:45 μμ (el-GR)|  
|"F"|Vzor úplného formátu data/času (dlouhého formátu času).<br /><br /> Další informace: [Specifikátor úplného formátu data a dlouhého formátu času ("F")](#FullDateLongTime).|2009-06-15T13:45:30-> pondělí, 15. června 2009 1:45:30 ODP. (EN-US)<br /><br /> 2009-06-15T13:45:30-> den 15 Juni 2009 13:45:30 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 1:45:30 μμ (el-GR)|  
|"g"|Vzor obecného formátu data/času (krátkého formátu času).<br /><br /> Další informace: [Specifikátor obecného formátu data a krátkého formátu času ("g")](#GeneralDateShortTime).|2009-06-15T13:45:30-> 6/15/2009 1:45 odp. (EN-US)<br /><br /> 2009-06-15T13:45:30 -> 15/06/2009 13:45 (es-ES)<br /><br /> 2009-06-15T13:45:30. > 2009/6/15 13:45 (zh-CN)|  
|"G"|Vzor obecného formátu data a času (dlouhého formátu času).<br /><br /> Další informace: [Specifikátor obecného formátu data a dlouhého formátu času ("G")](#GeneralDateLongTime).|2009-06-15T13:45:30-> 6/15/2009 1:45:30 ODP. (EN-US)<br /><br /> 2009-06-15T13:45:30 -> 15/06/2009 13:45:30 (es-ES)<br /><br /> 2009-06-15T13:45:30. > 2009/6/15 13:45:30 (zh-CN)|  
|"M", "m"|Vzor formátu měsíce/dne.<br /><br /> Další informace: [Specifikátor formátu měsíce ("m", "m")](#MonthDay).|2009-06-15T13:45:30-> 15. června (EN-US)<br /><br /> 2009-06-15T13:45:30 -> 15. Juni (da-DK)<br /><br /> 2009-06-15T13:45:30 – > 15 Juni (ID-ID)|  
|"O", "o"|Vzor formátu data/času zpátečního převodu.<br /><br /> Další informace: [Specifikátor formátu Round-Trip ("o", "o")](#Roundtrip).|<xref:System.DateTime>hodnota<br /><br /> 2009-06-15T13:45:30 (DateTimeKind. Local)--> 2009-06-15T13:45:30.0000000-07:00<br /><br /> 2009-06-15T13:45:30 (DateTimeKind. UTC)--> 2009-06-15T13:45:30.0000000 Z<br /><br /> 2009-06-15T13:45:30 (DateTimeKind. unspecifikovaná)--> 2009-06-15T13:45:30.0000000<br /><br /> <xref:System.DateTimeOffset>hodnota<br /><br /> 2009-06-15T13:45:30-07:00 --> 2009-06-15T13:45:30.0000000-07:00|  
|"R", "r"|Vzor RFC1123.<br /><br /> Další informace: [Specifikátor formátu RFC1123 ("r", "r")](#RFC1123).|2009-06-15T13:45:30-> Mon, 15. června 2009 20:45:30 GMT|  
|"s"|Vzor seřaditelného formátu data/času.<br /><br /> Další informace: [Specifikátor formátu, který lze seřadit ("s")](#Sortable).|2009-06-15T13:45:30 (DateTimeKind. Local)-> 2009-06-15T13:45:30<br /><br /> 2009-06-15T13:45:30 (DateTimeKind. UTC)-> 2009-06-15T13:45:30|  
|"t"|Vzor krátkého formátu času.<br /><br /> Další informace: [Specifikátor krátkého formátu času ("t")](#ShortTime).|2009-06-15T13:45:30-> 1:45 odp. (EN-US)<br /><br /> 2009-06-15T13:45:30 > 13:45 (HR-HR)<br /><br /> 2009-06-15T13:45:30-> 01:45 م (ar-EG)|  
|"T"|Vzor dlouhého formátu času.<br /><br /> Další informace: [Specifikátor dlouhého formátu času ("T")](#LongTime).|2009-06-15T13:45:30-> 1:45:30 ODP. (EN-US)<br /><br /> 2009-06-15T13:45:30 > 13:45:30 (HR-HR)<br /><br /> 2009-06-15T13:45:30-> 01:45:30 م (ar-EG)|  
|"u"|Vzor univerzálního seřaditelného formátu data/času.<br /><br /> Další informace: [Univerzální specifikátor formátu ("u")](#UniversalSortable).|<xref:System.DateTime> S hodnotou: 2009-06-15T13:45:30 -> 2009-06-15 13:45:30Z<br /><br /> <xref:System.DateTimeOffset> S hodnotou: 2009-06-15T13:45:30 -> 2009-06-15 20:45:30Z|  
|"U"|Vzor univerzálního úplného formátu data/času.<br /><br /> Další informace: [Specifikátor univerzálního úplného formátu ("U")](#UniversalFull).|2009-06-15T13:45:30-> pondělí, 15. června 2009 8:45:30 ODP. (EN-US)<br /><br /> 2009-06-15T13:45:30-> den 15 Juni 2009 20:45:30 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 8:45:30 μμ (el-GR)|  
|"Y", "y"|Vzor formátu roku a měsíce.<br /><br /> Další informace: [Specifikátor formátu roku a měsíce ("Y")](#YearMonth).|2009-06-15T13:45:30-> června, 2009 (EN-US)<br /><br /> 2009-06-15T13:45:30-> Juni 2009 (da-DK)<br /><br /> 2009-06-15T13:45:30-> Juni 2009 (ID-ID)|  
|Jakýkoli jiný samostatný znak|Neznámý specifikátor.|Vyvolá dobu <xref:System.FormatException>běhu.|  
  
## <a name="how-standard-format-strings-work"></a>Jak fungují řetězce standardního formátu  
 V rámci operace formátování je řetězec standardního formátu pouze aliasem pro řetězec vlastního formátu. Výhodou používání aliasu pro odkaz na řetězec vlastního formátu je skutečnost, že ačkoli alias zůstane neutrální, řetězec vlastního formátu se může změnit. Toto je důležité, protože řetězcová reprezentace hodnot data a času se obvykle liší podle jazykové verze. Například řetězec standardního formátu "d" označuje, že hodnota data a času má být zobrazena pomocí vzoru krátkého formátu data. Pro neutrální jazykovou verzi je použit formát "MM/dd/yyyy". Pro jazykovou verzi fr-FR je to formát "dd/MM/yyyy". Pro jazykovou verzi ja-JP je to formát "yyyy/MM/dd".  
  
 Pokud je řetězec standardního formátu v rámci operace formátování namapován na řetězec vlastního formátu konkrétní jazykové verze, může vaše aplikace definovat konkrétní jazykovou verzi, jejíž řetězce vlastního formátu se používají jedním z těchto způsobů:  
  
- Můžete použít výchozí (nebo aktuální) jazykovou verzi. Následující příklad zobrazí datum pomocí krátkého formátu data aktuální jazykové verze. V tomto případě je aktuální jazyková verze nastavena na en-US.  
  
     [!code-csharp-interactive[System.DateTime.Conceptual.Formatting#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#1)]
     [!code-vb[System.DateTime.Conceptual.Formatting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#1)]  
  
- Můžete předat <xref:System.Globalization.CultureInfo> objekt reprezentující jazykovou verzi, jejíž formátování má být použito pro metodu, která <xref:System.IFormatProvider> má parametr. Následující příklad zobrazí datum pomocí formátu krátkého data jazykové verze pt-BR.  
  
     [!code-csharp[System.DateTime.Conceptual.Formatting#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#2)]
     [!code-vb[System.DateTime.Conceptual.Formatting#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#2)]  
  
- Můžete předat <xref:System.Globalization.DateTimeFormatInfo> objekt, který poskytuje informace o formátování metodě, která <xref:System.IFormatProvider> má parametr. Následující příklad zobrazí datum pomocí formátu krátkého data z <xref:System.Globalization.DateTimeFormatInfo> objektu pro jazykovou verzi hr-hr.  
  
     [!code-csharp[System.DateTime.Conceptual.Formatting#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#3)]
     [!code-vb[System.DateTime.Conceptual.Formatting#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#3)]  
  
> [!NOTE]
> Informace o přizpůsobení vzorů nebo řetězců použitých při formátování hodnot data a času naleznete <xref:System.Globalization.NumberFormatInfo> v tématu třídy.  
  
 V některých případech slouží řetězec standardního formátu jako vhodná zkratka pro řetězec vlastního delšího formátu, který je neutrální. Do této kategorie patří čtyři standardní formátovací řetězce: "O" (nebo "o"), "R" (nebo "r"), "s" a "u". Tyto řetězce odpovídají řetězcům vlastního formátu, které jsou definovány neutrální jazykovou verzí. Vytvářejí řetězcové reprezentace hodnot data a času, které mají být identické napříč jazykovými verzemi. Následující tabulka obsahuje informace o těchto čtyřech řetězcích standardního formátu data a času.  
  
|Řetězec standardního formátu|Definovaný vlastností DateTimeFormatInfo.InvariantInfo|Řetězec vlastního formátu|  
|----------------------------|----------------------------------------------------------|--------------------------|  
|"O" nebo "o"|Žádné|yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffzz|  
|"R" nebo "r"|<xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A>|ddd, dd MMM yyyy HH':'mm':'ss 'GMT'|  
|"s"|<xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern%2A>|yyyy'-'MM'-'dd'T'HH':'mm':'ss|  
|"u"|<xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>|yyyy'-'MM'-'dd HH':'mm':'ss'Z'|  
  
 Standardní formátovací řetězce lze také použít při analýze operací s <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> metodami nebo <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> , které vyžadují, aby vstupní řetězec přesně splňoval konkrétní vzor, aby operace analýzy mohla být úspěšná. Mnoho řetězců standardního formátu je namapováno na několik řetězců vlastního formátu. Hodnotu data a času lze tedy vyjádřit v celé řadě formátů a operace analýzy i tak proběhne úspěšně. Můžete určit řetězec vlastního formátu nebo řetězce, které odpovídají standardnímu formátovacímu řetězci voláním <xref:System.Globalization.DateTimeFormatInfo.GetAllDateTimePatterns%28System.Char%29?displayProperty=nameWithType> metody. Následující příklad zobrazí řetězce vlastního formátu, které mapují řetězec standardního formátu "d" (vzor krátkého formátu data).  
  
 [!code-csharp[Formatting.DateAndTime.Standard#17](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/stdandparsing1.cs#17)]
 [!code-vb[Formatting.DateAndTime.Standard#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/stdandparsing1.vb#17)]  
  
 Následující části popisují standardní specifikátory formátu pro <xref:System.DateTime> hodnoty a. <xref:System.DateTimeOffset>  
  
<a name="ShortDate"></a>   
## <a name="the-short-date-d-format-specifier"></a>Specifikátor krátkého formátu data ("d")  
 Standardní specifikátor formátu "d" představuje řetězec vlastního formátu data a času, který je definován <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> vlastností konkrétní jazykové verze. Například řetězec vlastního formátu, který je vrácen <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A> vlastností invariantní jazykové verze, je "mm/dd/rrrr".  
  
 V následující tabulce jsou uvedeny <xref:System.Globalization.DateTimeFormatInfo> vlastnosti objektu, které řídí formátování vráceného řetězce.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A>|Definuje celkový formát výsledného řetězce.|  
|<xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A>|Definuje řetězec, který u data odděluje komponenty roku, měsíce a dne.|  
  
 Následující příklad používá specifikátor formátu "d" k zobrazení hodnoty data a času.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#1)]
 [!code-vb[Formatting.DateAndTime.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#1)]  
  
 [Zpět na tabulku](#table)  
  
<a name="LongDate"></a>   
## <a name="the-long-date-d-format-specifier"></a>Specifikátor dlouhého formátu data ("D")  
 Standardní specifikátor formátu "D" představuje řetězec vlastního formátu data a času, který je definován aktuální <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> vlastností. Například řetězec vlastního formátu pro neutrální jazykovou verzi je "dddd, dd MMMM yyyy".  
  
 V následující tabulce jsou uvedeny vlastnosti <xref:System.Globalization.DateTimeFormatInfo> objektu, které řídí formátování vráceného řetězce.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A>|Definuje celkový formát výsledného řetězce.|  
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Definuje lokalizované názvy dní, které mohou být zobrazeny ve výsledném řetězci.|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Definuje lokalizované názvy měsíců, které mohou být zobrazeny ve výsledném řetězci.|  
  
 Následující příklad používá specifikátor formátu "D" k zobrazení hodnoty data a času.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#2)]
 [!code-vb[Formatting.DateAndTime.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#2)]  
  
 [Zpět na tabulku](#table)  
  
<a name="FullDateShortTime"></a>   
## <a name="the-full-date-short-time-f-format-specifier"></a>Specifikátor úplného formátu data a krátkého formátu času ("f")  
 Standardní specifikátor formátu "f" představuje kombinaci vzorů dlouhého formátu data "D" a krátkého formátu času "t", která je oddělena mezerou.  
  
 Výsledný řetězec je ovlivněn informacemi o formátování konkrétního <xref:System.Globalization.DateTimeFormatInfo> objektu. V následující tabulce jsou uvedeny <xref:System.Globalization.DateTimeFormatInfo> vlastnosti objektu, které mohou řídit formátování vráceného řetězce. Vlastní specifikátor formátu vrácený <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> vlastnostmi a <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> některých kultur nemusí využívat všechny vlastnosti.  
  
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
  
 [Zpět na tabulku](#table)  
  
<a name="FullDateLongTime"></a>   
## <a name="the-full-date-long-time-f-format-specifier"></a>Specifikátor úplného formátu data a dlouhého formátu času ("F")  
 Standardní specifikátor formátu "F" představuje řetězec vlastního formátu data a času, který je definován aktuální <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> vlastností. Například řetězec vlastního formátu pro neutrální jazykovou verzi je "dddd, dd MMMM yyyy HH:mm:ss".  
  
 V následující tabulce jsou uvedeny <xref:System.Globalization.DateTimeFormatInfo> vlastnosti objektu, které mohou řídit formátování vráceného řetězce. Specifikátor vlastního formátu, který je vrácen <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A> vlastností některých kultur, nemusí využívat všechny vlastnosti.  
  
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
  
 [Zpět na tabulku](#table)  
  
<a name="GeneralDateShortTime"></a>   
## <a name="the-general-date-short-time-g-format-specifier"></a>Specifikátor obecného formátu data a krátkého formátu času ("g")  
 Standardní specifikátor formátu "g" představuje kombinaci vzorů krátkého formátu data "d" a krátkého formátu času "t", která je oddělena mezerou.  
  
 Výsledný řetězec je ovlivněn informacemi o formátování konkrétního <xref:System.Globalization.DateTimeFormatInfo> objektu. V následující tabulce jsou uvedeny <xref:System.Globalization.DateTimeFormatInfo> vlastnosti objektu, které mohou řídit formátování vráceného řetězce. Specifikátor vlastního formátu, který je vrácen <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> vlastnostmi a <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> v některých jazykových verzích, nemusí využívat všechny vlastnosti.  
  
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
  
 [Zpět na tabulku](#table)  
  
<a name="GeneralDateLongTime"></a>   
## <a name="the-general-date-long-time-g-format-specifier"></a>Specifikátor obecného formátu data a dlouhého formátu času ("G")  
 Standardní specifikátor formátu "G" představuje kombinaci vzorů krátkého formátu data "d" a dlouhého formátu času "T", která je oddělena mezerou.  
  
 Výsledný řetězec je ovlivněn informacemi o formátování konkrétního <xref:System.Globalization.DateTimeFormatInfo> objektu. V následující tabulce jsou uvedeny <xref:System.Globalization.DateTimeFormatInfo> vlastnosti objektu, které mohou řídit formátování vráceného řetězce. Specifikátor vlastního formátu, který je vrácen <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> vlastnostmi a <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> v některých jazykových verzích, nemusí využívat všechny vlastnosti.  
  
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
  
 [Zpět na tabulku](#table)  
  
<a name="MonthDay"></a>   
## <a name="the-month-m-m-format-specifier"></a>Specifikátor formátu měsíce ("M", "m")  
 Standardní specifikátor formátu "M" nebo "M" představuje řetězec vlastního formátu data a času, který je definován aktuální <xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern%2A?displayProperty=nameWithType> vlastností. Například řetězec vlastního formátu pro neutrální jazykovou verzi je "MMMM dd".  
  
 V následující tabulce jsou uvedeny <xref:System.Globalization.DateTimeFormatInfo> vlastnosti objektu, které řídí formátování vráceného řetězce.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern%2A>|Definuje celkový formát výsledného řetězce.|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Definuje lokalizované názvy měsíců, které mohou být zobrazeny ve výsledném řetězci.|  
  
 Následující příklad používá specifikátor formátu "m" k zobrazení hodnoty data a času.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#7)]
 [!code-vb[Formatting.DateAndTime.Standard#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#7)]  
  
 [Zpět na tabulku](#table)  
  
<a name="Roundtrip"></a>   
## <a name="the-round-trip-o-o-format-specifier"></a>Specifikátor formátu zpátečního převodu ("O", "o")  
 Standardní specifikátor formátu "O" nebo "o" představuje řetězec vlastního formátu data a času pomocí vzoru, který zachovává informace o časovém pásmu a generuje výsledný řetězec, který odpovídá normě ISO 8601. Pro <xref:System.DateTime> hodnoty je tento specifikátor formátu navržen tak, aby zachoval hodnoty data a času spolu <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> s vlastností v textu. Formátovaný řetězec lze <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> analyzovat zpět pomocí metody nebo <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> , pokud `styles` je parametr nastaven na <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>hodnotu.  
  
 Standardní specifikátor formátu "O" nebo "o" odpovídá "yyyy-yyyy '-DD 't": ' mm ': ' mm ': ' ss '. ' fffffffK "řetězec vlastního formátu pro <xref:System.DateTime> hodnoty a" yyyy-yyyy '-DD 't ":" mm ":" SS ". fffffffzzz řetězec vlastního formátu pro <xref:System.DateTimeOffset> hodnoty. Dvojice jednoduchých uvozovek v tomto řetězci oddělující jednotlivé znaky, jako jsou například spojovníky, dvojtečky a písmeno "T", označují, že jednotlivé znaky jsou literály, které nelze změnit. Apostrofy se ve výstupním řetězci nezobrazují.  
  
 Standardní specifikátor formátu "O" nebo "o" (a "yyyy-yyyy '-DD 't": ' mm ': ' ss '. ' fffffffK "řetězec vlastního formátu") využívá tři způsoby, které ISO 8601 představuje informace o časovém pásmu, <xref:System.DateTime.Kind%2A> aby zachovala <xref:System.DateTime> vlastnost hodnot:  
  
- Komponenta časového pásma hodnot <xref:System.DateTimeKind.Local?displayProperty=nameWithType> data a času je posun od času UTC (například + 01:00,-07:00). Všechny <xref:System.DateTimeOffset> hodnoty jsou také vyjádřeny v tomto formátu.  
  
- Komponenta časového pásma hodnot <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> data a času používá "Z" (což představuje nulový posun) k reprezentaci UTC.  
  
- <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>hodnoty data a času nemají žádné informace o časovém pásmu.  
  
 Vzhledem k tomu, že standardní specifikátor formátu "O" nebo "o" odpovídá mezinárodnímu standardu, operace formátování nebo analýzy, která používá specifikátor, vždy používá invariantní jazykovou verzi a gregoriánský kalendář.  
  
 Řetězce, které jsou předány `Parse`do `TryParse` `TryParseExact` metod `ParseExact` <xref:System.DateTime> ,,alzeanalyzovatpomocíspecifikátoruformátu"O"nebo"o",pokudjsouvjednomztěchtoformátů.<xref:System.DateTimeOffset> V případě <xref:System.DateTime> objektů by mělo přetížení analýzy, které voláte, `styles` zahrnovat také <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>parametr s hodnotou. Všimněte si, že pokud zavoláte metodu analýzy s vlastním řetězcem formátu, který odpovídá specifikátoru formátu "O" nebo "o", nezískáte stejné výsledky jako "O" nebo "o". Důvodem je, že analýza metod, které používají řetězec vlastního formátu, nemůže analyzovat řetězcovou reprezentaci hodnot data a času, které chybí komponenty časového pásma, nebo použít "Z" k označení času UTC.  
  
 Následující příklad používá specifikátor formátu "o" pro zobrazení řady <xref:System.DateTime> hodnot <xref:System.DateTimeOffset> a hodnoty v systému v USA. Časové pásmo v Tichomoří.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/o1.cs#8)]
 [!code-vb[Formatting.DateAndTime.Standard#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/o1.vb#8)]  
  
 Následující příklad používá specifikátor formátu "o" pro vytvoření formátovaného řetězce a následně obnoví původní hodnotu data a času voláním metody data a času `Parse` .  
  
 [!code-csharp[Formatting.DateandTime.Standard#16](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Roundtrip1.cs#16)]
 [!code-vb[Formatting.DateandTime.Standard#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/RoundTrip1.vb#16)]  
  
 [Zpět na tabulku](#table)  
  
<a name="RFC1123"></a>   
## <a name="the-rfc1123-r-r-format-specifier"></a>Specifikátor formátu RFC1123 ("R", "r")  
 Standardní specifikátor formátu "r" nebo "r" představuje řetězec vlastního formátu data a času, který je definován <xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A?displayProperty=nameWithType> vlastností. Tento vzor odpovídá definovanému standardu a příslušná vlastnost je určena jen pro čtení. Proto je vždy stejný bez ohledu na použitou jazykovou verzi nebo dodaného poskytovatele formátu. Řetězec vlastního formátu je "ddd, dd MMM yyyy HH':'mm':'ss 'GMT'". Při použití tohoto standardního specifikátoru formátu používá operace formátování nebo analýzy vždy neutrální jazykovou verzi.  
  
 Výsledný řetězec je ovlivněn následujícími vlastnostmi <xref:System.Globalization.DateTimeFormatInfo> objektu vráceného <xref:System.Globalization.DateTimeFormatInfo.InvariantInfo%2A?displayProperty=nameWithType> vlastností, která představuje invariantní jazykovou verzi.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A>|Definuje formát výsledného řetězce.|  
|<xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A>|Definuje zkrácené názvy dní, které mohou být zobrazeny ve výsledném řetězci.|  
|<xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames%2A>|Definuje zkrácené názvy měsíců, které mohou být zobrazeny ve výsledném řetězci.|  
  
 I když standard RFC 1123 vyjadřuje čas jako koordinovaný světový čas (UTC), operace formátování neupraví hodnotu <xref:System.DateTime> objektu, který se formátuje. Proto je nutné převést <xref:System.DateTime> hodnotu na čas UTC <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> voláním metody před provedením operace formátování. Naopak <xref:System.DateTimeOffset> hodnoty provádějí tento převod automaticky; před operací formátování není nutné <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> volat metodu.  
  
 Následující příklad používá specifikátor formátu "r" pro zobrazení <xref:System.DateTime> <xref:System.DateTimeOffset> a a hodnotu v systému v USA. Časové pásmo v Tichomoří.  
  
 [!code-csharp-interactive[Formatting.DateAndTime.Standard#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#9)]
 [!code-vb[Formatting.DateAndTime.Standard#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#9)]  
  
 [Zpět na tabulku](#table)  
  
<a name="Sortable"></a>   
## <a name="the-sortable-s-format-specifier"></a>Specifikátor seřaditelného formátu ("s")  
 Standardní specifikátor formátu "s" představuje řetězec vlastního formátu data a času, který je definován <xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern%2A?displayProperty=nameWithType> vlastností. Tento vzor odpovídá definovanému standardu (ISO 8601) a příslušná vlastnost je určena jen pro čtení. Proto je vždy stejný bez ohledu na použitou jazykovou verzi nebo dodaného poskytovatele formátu. Řetězec vlastního formátu je "yyyy'-'MM'-'dd'T'HH':'mm':'ss".  
  
 Účelem specifikátoru formátu "s" je vytváření výsledných řetězců, které se konzistentně řadí ve vzestupném nebo sestupném pořadí podle hodnot data a času. V důsledku toho i když standardní specifikátor formátu "s" představuje hodnotu data a času v konzistentním formátu, operace formátování neupravuje hodnotu objektu data a času, který je formátován tak, aby odrážel jeho <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> vlastnost nebo jeho <xref:System.DateTimeOffset.Offset%2A?displayProperty=nameWithType> hodnota. Například výsledné řetězce vytvořené formátováním hodnot data a času 2014-11-15T18:32:17 + 00:00 a 2014-11-15T18:32:17 + 08:00 jsou identické.  
  
 Při použití tohoto standardního specifikátoru formátu používá operace formátování nebo analýzy vždy neutrální jazykovou verzi.  
  
 Následující příklad používá specifikátor formátu "s" pro zobrazení <xref:System.DateTime> <xref:System.DateTimeOffset> a a hodnotu v systému v USA. Časové pásmo v Tichomoří.  
  
 [!code-csharp-interactive[Formatting.DateAndTime.Standard#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#10)]
 [!code-vb[Formatting.DateAndTime.Standard#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#10)]  
  
 [Zpět na tabulku](#table)  
  
<a name="ShortTime"></a>   
## <a name="the-short-time-t-format-specifier"></a>Specifikátor krátkého formátu času ("t")  
 Standardní specifikátor formátu "t" představuje řetězec vlastního formátu data a času, který je definován aktuální <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> vlastností. Například řetězec vlastního formátu pro neutrální jazykovou verzi je "HH:mm".  
  
 Výsledný řetězec je ovlivněn informacemi o formátování konkrétního <xref:System.Globalization.DateTimeFormatInfo> objektu. V následující tabulce jsou uvedeny <xref:System.Globalization.DateTimeFormatInfo> vlastnosti objektu, které mohou řídit formátování vráceného řetězce. Specifikátor vlastního formátu, který je vrácen <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> vlastností některých kultur, nemusí využívat všechny vlastnosti.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A>|Definuje formát komponenty času výsledného řetězce.|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Definuje řetězec, který odděluje komponenty hodiny, minuty a sekundy v časovém údaji.|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Definuje řetězec, který označuje dobu od půlnoci do doby před polednem ve 12hodinovém formátu.|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Definuje řetězec, který označuje dobu od poledne do doby před půlnocí ve 12hodinovém formátu.|  
  
 Následující příklad používá specifikátor formátu "t" k zobrazení hodnoty data a času.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#11)]
 [!code-vb[Formatting.DateAndTime.Standard#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#11)]  
  
 [Zpět na tabulku](#table)  
  
<a name="LongTime"></a>   
## <a name="the-long-time-t-format-specifier"></a>Specifikátor dlouhého formátu času ("T")  
 Standardní specifikátor formátu "T" představuje řetězec vlastního formátu data a času, který je definován <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> vlastností konkrétní jazykové verze. Například řetězec vlastního formátu pro neutrální jazykovou verzi je "HH:mm:ss".  
  
 V následující tabulce jsou uvedeny <xref:System.Globalization.DateTimeFormatInfo> vlastnosti objektu, které mohou řídit formátování vráceného řetězce. Specifikátor vlastního formátu, který je vrácen <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> vlastností některých kultur, nemusí využívat všechny vlastnosti.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A>|Definuje formát komponenty času výsledného řetězce.|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Definuje řetězec, který odděluje komponenty hodiny, minuty a sekundy v časovém údaji.|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Definuje řetězec, který označuje dobu od půlnoci do doby před polednem ve 12hodinovém formátu.|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Definuje řetězec, který označuje dobu od poledne do doby před půlnocí ve 12hodinovém formátu.|  
  
 Následující příklad používá specifikátor formátu "T" k zobrazení hodnoty data a času.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#12)]
 [!code-vb[Formatting.DateAndTime.Standard#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#12)]  
  
 [Zpět na tabulku](#table)  
  
<a name="UniversalSortable"></a>   
## <a name="the-universal-sortable-u-format-specifier"></a>Specifikátor univerzálního seřaditelného formátu ("u")  
 Standardní specifikátor formátu "u" představuje řetězec vlastního formátu data a času, který je definován <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A?displayProperty=nameWithType> vlastností. Tento vzor odpovídá definovanému standardu a příslušná vlastnost je určena jen pro čtení. Proto je vždy stejný bez ohledu na použitou jazykovou verzi nebo dodaného poskytovatele formátu. Řetězec vlastního formátu je "yyyy'-'MM'-'dd HH':'mm':'ss'Z'". Při použití tohoto standardního specifikátoru formátu používá operace formátování nebo analýzy vždy neutrální jazykovou verzi.  
  
 I když by výsledný řetězec měl vyjadřovat čas koordinovaný světový čas (UTC), během operace formátování se neprovede <xref:System.DateTime> žádný převod původní hodnoty. Proto je nutné převést <xref:System.DateTime> hodnotu na čas UTC <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> voláním metody před formátováním.  Naopak <xref:System.DateTimeOffset> hodnoty provádějí tento převod automaticky; před operací formátování není nutné <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> volat metodu.  
  
 Následující příklad používá specifikátor formátu "u" k zobrazení hodnoty data a času.  
  
 [!code-csharp-interactive[Formatting.DateAndTime.Standard#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Standard#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#13)]  
  
 [Zpět na tabulku](#table)  
  
<a name="UniversalFull"></a>   
## <a name="the-universal-full-u-format-specifier"></a>Specifikátor univerzálního úplného formátu ("U")  
 Standardní specifikátor formátu "U" představuje řetězec vlastního formátu data a času, který je definován zadanou <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> vlastností jazykové verze. Tento vzor je stejný jako vzor "F". <xref:System.DateTime> Hodnota je však automaticky převedena na UTC před formátováním.  
  
 V následující tabulce jsou uvedeny <xref:System.Globalization.DateTimeFormatInfo> vlastnosti objektu, které mohou řídit formátování vráceného řetězce. Specifikátor vlastního formátu, který je vrácen <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A> vlastností některých kultur, nemusí využívat všechny vlastnosti.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A>|Definuje celkový formát výsledného řetězce.|  
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Definuje lokalizované názvy dní, které mohou být zobrazeny ve výsledném řetězci.|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Definuje lokalizované názvy měsíců, které mohou být zobrazeny ve výsledném řetězci.|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Definuje řetězec, který odděluje komponenty hodiny, minuty a sekundy v časovém údaji.|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Definuje řetězec, který označuje dobu od půlnoci do doby před polednem ve 12hodinovém formátu.|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Definuje řetězec, který označuje dobu od poledne do doby před půlnocí ve 12hodinovém formátu.|  
  
 Specifikátor formátu "U" není tímto <xref:System.DateTimeOffset> typem podporován a <xref:System.FormatException> vyvolá výjimku, pokud <xref:System.DateTimeOffset> je použita k formátování hodnoty.  
  
 Následující příklad používá specifikátor formátu "U" k zobrazení hodnoty data a času.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#14)]
 [!code-vb[Formatting.DateAndTime.Standard#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#14)]  
  
 [Zpět na tabulku](#table)  
  
<a name="YearMonth"></a>   
## <a name="the-year-month-y-y-format-specifier"></a>Specifikátor formátu roku a měsíce ("Y", "y")  
 Standardní specifikátor formátu "Y" nebo "y" představuje řetězec vlastního formátu data a času, který je definován <xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern%2A?displayProperty=nameWithType> vlastností zadané jazykové verze. Například řetězec vlastního formátu pro neutrální jazykovou verzi je "yyyy MMMM".  
  
 V následující tabulce jsou uvedeny <xref:System.Globalization.DateTimeFormatInfo> vlastnosti objektu, které řídí formátování vráceného řetězce.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern%2A>|Definuje celkový formát výsledného řetězce.|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Definuje lokalizované názvy měsíců, které mohou být zobrazeny ve výsledném řetězci.|  
  
 Následující příklad používá specifikátor formátu "y" k zobrazení hodnoty data a času.  
  
 [!code-csharp[Formatting.DateAndTime.Standard#15](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#15)]
 [!code-vb[Formatting.DateAndTime.Standard#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#15)]  
  
 [Zpět na tabulku](#table)  
  
<a name="Notes"></a>   
## <a name="notes"></a>Poznámky  
  
### <a name="control-panel-settings"></a>Nastavení části Ovládací panely  
 Nastavení v položce **místní a jazykové** nastavení v Ovládacích panelech ovlivní výsledný řetězec vytvořený při operaci formátování. Tato nastavení slouží k inicializaci <xref:System.Globalization.DateTimeFormatInfo> objektu přidruženého k aktuální jazykové verzi vlákna, které poskytuje hodnoty použité k řízení formátování. Počítače, které používají různá nastavení, generují různé výsledné řetězce.  
  
 Kromě toho, pokud použijete <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> konstruktor k vytvoření instance nového <xref:System.Globalization.CultureInfo> objektu, který představuje stejnou jazykovou verzi jako aktuální jazyková verze systému, jakákoli vlastní nastavení, která byla vytvořena položkou **místní a jazykové nastavení** v Ovládacích panelech bude použito pro nový <xref:System.Globalization.CultureInfo> objekt. <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> Konstruktor můžete použít k <xref:System.Globalization.CultureInfo> vytvoření objektu, který nereflektuje vlastní nastavení systému.  
  
### <a name="datetimeformatinfo-properties"></a>Vlastnosti DateTimeFormatInfo  
 Formátování je ovlivněno vlastnostmi aktuálního <xref:System.Globalization.DateTimeFormatInfo> objektu, který je poskytnut implicitně aktuální jazykovou verzí vlákna nebo explicitně <xref:System.IFormatProvider> parametrem metody, která vyvolá formátování. Pro parametr by měla vaše aplikace <xref:System.Globalization.CultureInfo> určovat objekt, který představuje jazykovou verzi, nebo <xref:System.Globalization.DateTimeFormatInfo> objekt, který představuje konvence formátování data a času konkrétní jazykové verze. <xref:System.IFormatProvider> Mnohé standardní specifikátory formátu data a času jsou aliasy pro vzory formátování definované vlastnostmi aktuálního <xref:System.Globalization.DateTimeFormatInfo> objektu. Vaše aplikace může změnit výsledek vytvořený některými specifikátory standardního formátu data a času změnou odpovídajících vzorů formátu data a času odpovídající <xref:System.Globalization.DateTimeFormatInfo> vlastnosti.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.DateTime?displayProperty=nameWithType>
- <xref:System.DateTimeOffset?displayProperty=nameWithType>
- [Typy formátování](../../../docs/standard/base-types/formatting-types.md)
- [Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
- [Ukázka: Nástroj pro formátování .NET Framework 4](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
