---
title: Standardní formátovací řetězce data a času
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
ms.openlocfilehash: 883902142a91e275ab64ad5d12c197c665bd9b36
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400335"
---
# <a name="standard-date-and-time-format-strings"></a>Standardní formátovací řetězce data a času

Řetězec standardního formátu data a času používá pro definování textového vyjádření hodnoty data a času jeden specifikátor formátu. Libovolný řetězec formátu data a času, který obsahuje více než jeden znak, včetně prázdného místa, je interpretován jako vlastní řetězec formátu data a času; Další informace naleznete [v tématu Vlastní formátovací řetězce data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md). Řetězec standardního nebo vlastního formátu lze používat dvěma způsoby:

- Chcete-li definovat řetězec, který je výsledkem operace formátování.

- Chcete-li definovat textovou reprezentaci hodnoty data a <xref:System.DateTime> <xref:System.DateTimeOffset> času, kterou lze převést na hodnotu nebo pomocí operace analýzy.

> [!TIP]
> Můžete si stáhnout **nástroj Formátování**, aplikaci .NET Core Windows Forms, která umožňuje použít formátovací řetězce na číselné hodnoty nebo hodnoty data a času a zobrazí výsledný řetězec. Zdrojový kód je k dispozici pro [c#](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs) a [visual basic](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb).

Standardní řetězce formátu data a času <xref:System.DateTime> lze <xref:System.DateTimeOffset> použít s hodnotami i s hodnotami.

[!INCLUDE[C# interactive-note](~/includes/csharp-interactive-with-utc-partial-note.md)]

<a name="table"></a>V následující tabulce jsou popsány standardní specifikátory formátu data a času. Není-li uvedeno jinak, konkrétní specifikátor formátu data a času vytvoří identickou <xref:System.DateTime> řetězcovou <xref:System.DateTimeOffset> reprezentaci bez ohledu na to, zda je použit s hodnotou nebo hodnotou. Další informace o používání standardních formátovacích řetězců data a času naleznete v části [Poznámky.](#Notes)

|Specifikátor formátu|Popis|Příklady|
|----------------------|-----------------|--------------|
|"d"|Vzor krátkého formátu data.<br /><br /> Další informace:[Specifikátor formátu Krátké datum ("d".](#ShortDate)|2009-06-15T13:45:30 -> 6/15/2009 (cs-US)<br /><br /> 2009-06-15T13:45:30 -> 15/06/2009 (fr-FR)<br /><br /> 2009-06-15T13:45:30 -> 2009/06/15 (ja-JP)|
|"D"|Vzor dlouhého formátu data.<br /><br /> Další informace:[Specifikátor formátu Long Date ("D")](#LongDate).|2009-06-15T13:45:30 -> pondělí 15.června 2009 (en-US)<br /><br /> 2009-06-15T13:45:30 -> 15 июня 2009 г. (ru-RU)<br /><br /> 2009-06-15T13:45:30 -> Montag, 15. Juni 2009 (de-DE)|
|"f"|Vzor úplného formátu data/času (krátkého formátu času).<br /><br /> Další informace: [Specifikátor formátu Full Date Short Time ("f")](#FullDateShortTime).|2009-06-15T13:45:30 -> pondělí 15.června 2009 13:45 (en-US)<br /><br /> 2009-06-15T13:45:30 -> den 15 juni 2009 13:45 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτρρα, 15 Ιουνίου 2009 1:45 μμ (el-GR)|
|"F"|Vzor úplného formátu data/času (dlouhého formátu času).<br /><br /> Další informace: [Specifikátor formátu Úplné datum ("F")](#FullDateLongTime).|2009-06-15T13:45:30 -> pondělí 15.června 2009 13:45:30 (en-US)<br /><br /> 2009-06-15T13:45:30 -> den 15 juni 2009 13:45:30 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτρρα, 15 Ιουνίου 2009 1:45:30 μμ (el-GR)|
|"g"|Vzor obecného formátu data/času (krátkého formátu času).<br /><br /> Další informace: [Specifikátor formátu Obecné datum ("g")](#GeneralDateShortTime).|2009-06-15T13:45:30 -> 6/15/2009 13:45 (cs-US)<br /><br /> 2009-06-15T13:45:30 -> 15/06/2009 13:45 (es-ES)<br /><br /> 2009-06-15T13:45:30 -> 2009/6/15 13:45 (zh-CN)|
|"G"|Vzor obecného formátu data a času (dlouhého formátu času).<br /><br /> Další informace: [Specifikátor formátu Obecné datum ("G")](#GeneralDateLongTime).|2009-06-15T13:45:30 -> 6/15/2009 13:45:30 (en-US)<br /><br /> 2009-06-15T13:45:30 -> 15/06/2009 13:45:30 (es-ES)<br /><br /> 2009-06-15T13:45:30 -> 2009/6/15 13:45:30 (zh-CN)|
|"M", "m"|Vzor formátu měsíce/dne.<br /><br /> Další informace: [The Month ("M", "m") Format Specifier](#MonthDay).|2009-06-15T13:45:30 -> 15. června (cs-US)<br /><br /> 2009-06-15T13:45:30 -> 15. juni (da-DK)<br /><br /> 2009-06-15T13:45:30 -> 15 Juni (id-ID)|
|"O", "o"|Vzor formátu data/času zpátečního převodu.<br /><br /> Další informace: [Specifikátor formátu Round-trip ("O", "o")](#Roundtrip).|<xref:System.DateTime>Hodnoty:<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Local) --> 2009-06-15T13:45:30.000000-07:00<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Utc) --> 2009-06-15T13:45:30.0000000Z<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Unspecified) --> 2009-06-15T13:45:30.0000000<br /><br /> <xref:System.DateTimeOffset>Hodnoty:<br /><br /> 2009-06-15T13:45:30-07:00 --> 2009-06-15T13:45:30.000000-07:00|
|"R", "r"|Vzor RFC1123.<br /><br /> Další informace: [Specifikátor formátu RFC1123 ("R", "r")](#RFC1123).|2009-06-15T13:45:30 -> Po, 15 Čer 2009 20:45:30 GMT|
|"s"|Vzor seřaditelného formátu data/času.<br /><br /> Další informace: [Specifikátor formátu Seřaditelný ("s")](#Sortable).|2009-06-15T13:45:30 (DateTimeKind.Local) -> 2009-06-15T13:45:30<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Utc) -> 2009-06-15T13:45:30|
|"t"|Vzor krátkého formátu času.<br /><br /> Další informace: [Specifikátor formátu Short Time ("t")](#ShortTime).|2009-06-15T13:45:30 -> 13:45 (cs-US)<br /><br /> 2009-06-15T13:45:30 -> 13:45 (hr-HR)<br /><br /> 2009-06-15T13:45:30 -> 01:45 م (ar-EG)|
|"T"|Vzor dlouhého formátu času.<br /><br /> Další informace: [Specifikátor formátu Long Time ("T")](#LongTime).|2009-06-15T13:45:30 -> 13:45:30 (cs-US)<br /><br /> 2009-06-15T13:45:30 -> 13:45:30 (hr-HR)<br /><br /> 2009-06-15T13:45:30 -> 01:45:30 م (ar-EG)|
|"u"|Vzor univerzálního seřaditelného formátu data/času.<br /><br /> Další informace: [Univerzální specifikátor formátu ("u")](#UniversalSortable).|S <xref:System.DateTime> hodnotou: 2009-06-15T13:45:30 -> 2009-06-15 13:45:30Z<br /><br /> S <xref:System.DateTimeOffset> hodnotou: 2009-06-15T13:45:30 -> 2009-06-15 20:45:30Z|
|"U"|Vzor univerzálního úplného formátu data/času.<br /><br /> Další informace: [Univerzální úplný ("U") Specifikátor formátu](#UniversalFull).|2009-06-15T13:45:30 -> pondělí 15.června 2009 20:45:30 (en-US)<br /><br /> 2009-06-15T13:45:30 -> den 15 juni 2009 20:45:30 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτρρα, 15 Ιουνίου 2009 8:45:30 μμ (el-GR)|
|"Y", "y"|Vzor formátu roku a měsíce.<br /><br /> Další informace: [Roční měsíc ("Y") Specifikátor formátu](#YearMonth).|2009-06-15T13:45:30 -> červen 2009 (cs-US)<br /><br /> 2009-06-15T13:45:30 -> juni 2009 (da-DK)<br /><br /> 2009-06-15T13:45:30 -> Juni 2009 (id-ID)|
|Jakýkoli jiný samostatný znak|Neznámý specifikátor.|Vyvolá run-time <xref:System.FormatException>.|

## <a name="how-standard-format-strings-work"></a>Jak fungují řetězce standardního formátu

V rámci operace formátování je řetězec standardního formátu pouze aliasem pro řetězec vlastního formátu. Výhodou používání aliasu pro odkaz na řetězec vlastního formátu je skutečnost, že ačkoli alias zůstane neutrální, řetězec vlastního formátu se může změnit. Toto je důležité, protože řetězcová reprezentace hodnot data a času se obvykle liší podle jazykové verze. Například řetězec standardního formátu "d" označuje, že hodnota data a času má být zobrazena pomocí vzoru krátkého formátu data. Pro neutrální jazykovou verzi je použit formát "MM/dd/yyyy". Pro jazykovou verzi fr-FR je to formát "dd/MM/yyyy". Pro jazykovou verzi ja-JP je to formát "yyyy/MM/dd".

Pokud je řetězec standardního formátu v rámci operace formátování namapován na řetězec vlastního formátu konkrétní jazykové verze, může vaše aplikace definovat konkrétní jazykovou verzi, jejíž řetězce vlastního formátu se používají jedním z těchto způsobů:

- Můžete použít výchozí (nebo aktuální) jazykovou verzi. Následující příklad zobrazí datum pomocí krátkého formátu data aktuální jazykové verze. V tomto případě je aktuální jazyková verze nastavena na en-US.

  [!code-csharp-interactive[System.DateTime.Conceptual.Formatting#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#1)]
  [!code-vb[System.DateTime.Conceptual.Formatting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#1)]

- Můžete předat <xref:System.Globalization.CultureInfo> objekt představující jazykovou verzi, jejíž formátování má být <xref:System.IFormatProvider> použito pro metodu, která má parametr. Následující příklad zobrazí datum pomocí formátu krátkého data jazykové verze pt-BR.

  [!code-csharp[System.DateTime.Conceptual.Formatting#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#2)]
  [!code-vb[System.DateTime.Conceptual.Formatting#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#2)]

- Objekt, <xref:System.Globalization.DateTimeFormatInfo> který poskytuje informace o formátování, můžete předat <xref:System.IFormatProvider> metodě, která má parametr. Následující příklad zobrazuje datum pomocí krátkého <xref:System.Globalization.DateTimeFormatInfo> formátu data z objektu pro jazykovou verzi hr-HR.

  [!code-csharp[System.DateTime.Conceptual.Formatting#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#3)]
  [!code-vb[System.DateTime.Conceptual.Formatting#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#3)]

> [!NOTE]
> Informace o přizpůsobení vzorků nebo řetězců použitých při formátování hodnot data <xref:System.Globalization.NumberFormatInfo> a času naleznete v tématu třídy.

V některých případech slouží řetězec standardního formátu jako vhodná zkratka pro řetězec vlastního delšího formátu, který je neutrální. Do této kategorie patří čtyři řetězce standardního formátu: "O" (nebo "o"), "R" (nebo "r"), "s" a "u". Tyto řetězce odpovídají řetězcům vlastního formátu, které jsou definovány neutrální jazykovou verzí. Vytvářejí řetězcové reprezentace hodnot data a času, které mají být identické napříč jazykovými verzemi. Následující tabulka obsahuje informace o těchto čtyřech řetězcích standardního formátu data a času.

|Řetězec standardního formátu|Definovaný vlastností DateTimeFormatInfo.InvariantInfo|Řetězec vlastního formátu|
|----------------------------|----------------------------------------------------------|--------------------------|
|"O" nebo "o"|Žádný|yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffzz|
|"R" nebo "r"|<xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A>|ddd, dd MMM yyyy HH':'mm':'ss 'GMT'|
|"s"|<xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern%2A>|yyyy'-'MM'-'dd'T'HH':'mm':'ss|
|"u"|<xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>|yyyy'-'MM'-'dd HH':'mm':'ss'Z'|

Standardní formátovací řetězce lze také použít v <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> parsování operace s nebo <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> metody, které vyžadují vstupní řetězec přesně přizpůsobit konkrétní vzor pro operaci analýzy úspěšné. Mnoho řetězců standardního formátu je namapováno na několik řetězců vlastního formátu. Hodnotu data a času lze tedy vyjádřit v celé řadě formátů a operace analýzy i tak proběhne úspěšně. Vlastní formátovací řetězec nebo řetězce, které odpovídají standardnímu formátovacímu řetězci, můžete určit voláním <xref:System.Globalization.DateTimeFormatInfo.GetAllDateTimePatterns%28System.Char%29?displayProperty=nameWithType> metody. Následující příklad zobrazí řetězce vlastního formátu, které mapují řetězec standardního formátu "d" (vzor krátkého formátu data).

[!code-csharp[Formatting.DateAndTime.Standard#17](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/stdandparsing1.cs#17)]
[!code-vb[Formatting.DateAndTime.Standard#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/stdandparsing1.vb#17)]

Následující části popisují standardní specifikátory formátu a <xref:System.DateTime> <xref:System.DateTimeOffset> hodnoty.

<a name="ShortDate"></a>

## <a name="the-short-date-d-format-specifier"></a>Specifikátor krátkého formátu data ("d")

Specifikátor standardního formátu "d" představuje vlastní řetězec formátu data a času, který je definován <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> vlastností konkrétní jazykové verze. Například vlastní formátovací řetězec, který <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A> je vrácen vlastností invariantní jazykové verze, je "MM/dd/yyyy".

V následující tabulce <xref:System.Globalization.DateTimeFormatInfo> jsou uvedeny vlastnosti objektu, které řídí formátování vráceného řetězce.

|Vlastnost|Popis|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A>|Definuje celkový formát výsledného řetězce.|
|<xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A>|Definuje řetězec, který u data odděluje komponenty roku, měsíce a dne.|

Následující příklad používá specifikátor formátu "d" k zobrazení hodnoty data a času.

[!code-csharp[Formatting.DateAndTime.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#1)]
[!code-vb[Formatting.DateAndTime.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#1)]

[Zpět na stůl](#table)

<a name="LongDate"></a>

## <a name="the-long-date-d-format-specifier"></a>Specifikátor dlouhého formátu data ("D")

Specifikátor standardního formátu "D" představuje vlastní řetězec formátu data <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> a času, který je definován aktuální vlastností. Například řetězec vlastního formátu pro neutrální jazykovou verzi je "dddd, dd MMMM yyyy".

V následující tabulce jsou <xref:System.Globalization.DateTimeFormatInfo> uvedeny vlastnosti objektu, který řídí formátování vráceného řetězce.

|Vlastnost|Popis|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A>|Definuje celkový formát výsledného řetězce.|
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Definuje lokalizované názvy dní, které mohou být zobrazeny ve výsledném řetězci.|
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Definuje lokalizované názvy měsíců, které mohou být zobrazeny ve výsledném řetězci.|

Následující příklad používá specifikátor formátu "D" k zobrazení hodnoty data a času.

[!code-csharp[Formatting.DateAndTime.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#2)]
[!code-vb[Formatting.DateAndTime.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#2)]

[Zpět na stůl](#table)

<a name="FullDateShortTime"></a>

## <a name="the-full-date-short-time-f-format-specifier"></a>Specifikátor úplného formátu data a krátkého formátu času ("f")

Standardní specifikátor formátu "f" představuje kombinaci vzorů dlouhého formátu data "D" a krátkého formátu času "t", která je oddělena mezerou.

Výsledný řetězec je ovlivněn informacemi o formátování <xref:System.Globalization.DateTimeFormatInfo> určitého objektu. V následující tabulce <xref:System.Globalization.DateTimeFormatInfo> jsou uvedeny vlastnosti objektu, které mohou řídit formátování vráceného řetězce. Vlastní specifikátor formátu <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> vrácené <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> vlastnosti a některé jazykové verze nemusí využívat všechny vlastnosti.

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

[Zpět na stůl](#table)

<a name="FullDateLongTime"></a>

## <a name="the-full-date-long-time-f-format-specifier"></a>Specifikátor úplného formátu data a dlouhého formátu času ("F")

Specifikátor standardního formátu "F" představuje vlastní řetězec formátu data <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> a času, který je definován aktuální vlastností. Například řetězec vlastního formátu pro neutrální jazykovou verzi je "dddd, dd MMMM yyyy HH:mm:ss".

V následující tabulce <xref:System.Globalization.DateTimeFormatInfo> jsou uvedeny vlastnosti objektu, které mohou řídit formátování vráceného řetězce. Vlastní specifikátor formátu, který <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A> je vrácen vlastností některých kultur, nemusí využívat všechny vlastnosti.

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

[Zpět na stůl](#table)

<a name="GeneralDateShortTime"></a>

## <a name="the-general-date-short-time-g-format-specifier"></a>Specifikátor obecného formátu data a krátkého formátu času ("g")

Standardní specifikátor formátu "g" představuje kombinaci vzorů krátkého formátu data "d" a krátkého formátu času "t", která je oddělena mezerou.

Výsledný řetězec je ovlivněn informacemi o formátování <xref:System.Globalization.DateTimeFormatInfo> určitého objektu. V následující tabulce <xref:System.Globalization.DateTimeFormatInfo> jsou uvedeny vlastnosti objektu, které mohou řídit formátování vráceného řetězce. Vlastní specifikátor formátu, který <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> je <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> vrácen a vlastnosti některých kultur nemusí využívat všechny vlastnosti.

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

[Zpět na stůl](#table)

<a name="GeneralDateLongTime"></a>

## <a name="the-general-date-long-time-g-format-specifier"></a>Specifikátor obecného formátu data a dlouhého formátu času ("G")

Standardní specifikátor formátu "G" představuje kombinaci vzorů krátkého formátu data "d" a dlouhého formátu času "T", která je oddělena mezerou.

Výsledný řetězec je ovlivněn informacemi o formátování <xref:System.Globalization.DateTimeFormatInfo> určitého objektu. V následující tabulce <xref:System.Globalization.DateTimeFormatInfo> jsou uvedeny vlastnosti objektu, které mohou řídit formátování vráceného řetězce. Vlastní specifikátor formátu, který <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> je <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> vrácen a vlastnosti některých kultur nemusí využívat všechny vlastnosti.

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

[Zpět na stůl](#table)

<a name="MonthDay"></a>

## <a name="the-month-m-m-format-specifier"></a>Specifikátor formátu měsíce ("M", "m")

Specifikátor standardního formátu "M" nebo "m" představuje vlastní řetězec formátu <xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern%2A?displayProperty=nameWithType> data a času, který je definován aktuální vlastností. Například řetězec vlastního formátu pro neutrální jazykovou verzi je "MMMM dd".

V následující tabulce <xref:System.Globalization.DateTimeFormatInfo> jsou uvedeny vlastnosti objektu, které řídí formátování vráceného řetězce.

|Vlastnost|Popis|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern%2A>|Definuje celkový formát výsledného řetězce.|
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Definuje lokalizované názvy měsíců, které mohou být zobrazeny ve výsledném řetězci.|

Následující příklad používá specifikátor formátu "m" k zobrazení hodnoty data a času.

[!code-csharp[Formatting.DateAndTime.Standard#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#7)]
[!code-vb[Formatting.DateAndTime.Standard#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#7)]

[Zpět na stůl](#table)

<a name="Roundtrip"></a>

## <a name="the-round-trip-o-o-format-specifier"></a>Specifikátor formátu zpátečního převodu ("O", "o")

Specifikátor standardního formátu "O" nebo "o" představuje vlastní řetězec formátu data a času pomocí vzoru, který zachová informace o časovém pásmu a vydává výsledný řetězec, který vyhovuje normě ISO 8601. U <xref:System.DateTime> hodnot je tento specifikátor formátu navržen tak, <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> aby uchovával hodnoty data a času spolu s vlastností v textu. Formátovaný řetězec lze analyzovat zpět pomocí <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> metody <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> nebo, `styles` pokud je <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>parametr nastaven na hodnotu .

Specifikátor standardního formátu "O" nebo "o" odpovídá specifikátoru formátu "yyyy'-'MM'-dd'T'HH': 'mm':'ss'. fffffffK" vlastní formátovací řetězec pro <xref:System.DateTime> hodnoty a na "yyyy'-'MM'-'dd'T'HH':'mm':'ss'. fffffffzzz" vlastní formátovací řetězec pro <xref:System.DateTimeOffset> hodnoty. Dvojice jednoduchých uvozovek v tomto řetězci oddělující jednotlivé znaky, jako jsou například spojovníky, dvojtečky a písmeno "T", označují, že jednotlivé znaky jsou literály, které nelze změnit. Apostrofy se ve výstupním řetězci nezobrazují.

Specifikátor standardního formátu "O" nebo "o" (a "yyyy'-'MM'-dd'T'HH':'mm':'ss'. fffffffK" vlastní formátovací řetězec) využívá tři způsoby, které ISO 8601 představuje informace o časovém pásmu zachovat <xref:System.DateTime.Kind%2A> vlastnost <xref:System.DateTime> hodnot:

- Součást časového pásma <xref:System.DateTimeKind.Local?displayProperty=nameWithType> hodnot data a času je posun od času UTC (například +01:00, -07:00). V <xref:System.DateTimeOffset> tomto formátu jsou také reprezentovány všechny hodnoty.

- Součást časového pásma <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> hodnot data a času používá "Z" (což znamená nulový posun) k reprezentaci času UTC.

- <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>hodnoty data a času nemají žádné informace o časovém pásmu.

Vzhledem k tomu, že specifikátor standardního formátu "O" nebo "o" odpovídá mezinárodnímu standardu, operace formátování nebo analýzy, která používá specifikátor, vždy používá invariantní jazykovou verzi a gregoriánský kalendář.

Řetězce, které jsou `Parse`předány `TryParse`, `TryParseExact` , <xref:System.DateTime> `ParseExact` <xref:System.DateTimeOffset> , a metody a mohou být analyzovány pomocí specifikátoru formátu "O" nebo "o", pokud jsou v jednom z těchto formátů. V případě <xref:System.DateTime> objektů by mělo přetížení analýzy, které `styles` voláte, obsahovat také parametr s hodnotou <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>. Všimněte si, že pokud zavoláte metodu analýzy s vlastním formátovacím řetězcem, který odpovídá specifikátoru formátu "O" nebo "o", nezískáte stejné výsledky jako "O" nebo "o". Důvodem je, že metody analýzy, které používají vlastní formátovací řetězec, nemohou analyzovat řetězcovou reprezentaci hodnot data a času, které postrádají komponentu časového pásma, nebo použít "Z" k označení Času UTC.

Následující příklad používá specifikátor formátu o k zobrazení <xref:System.DateTime> řady <xref:System.DateTimeOffset> hodnot a hodnoty v systému v časovém pásmu Usa tichomoří.

[!code-csharp[Formatting.DateAndTime.Standard#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/o1.cs#8)]
[!code-vb[Formatting.DateAndTime.Standard#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/o1.vb#8)]

Následující příklad používá specifikátor formátu o k vytvoření formátovaného řetězce a potom obnoví původní hodnotu `Parse` data a času voláním metody data a času.

[!code-csharp[Formatting.DateandTime.Standard#16](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Roundtrip1.cs#16)]
[!code-vb[Formatting.DateandTime.Standard#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/RoundTrip1.vb#16)]

[Zpět na stůl](#table)

<a name="RFC1123"></a>

## <a name="the-rfc1123-r-r-format-specifier"></a>Specifikátor formátu RFC1123 ("R", "r")

Specifikátor standardního formátu "R" nebo "r" představuje vlastní řetězec formátu <xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A?displayProperty=nameWithType> data a času, který je definován vlastností. Tento vzor odpovídá definovanému standardu a příslušná vlastnost je určena jen pro čtení. Proto je vždy stejný bez ohledu na použitou jazykovou verzi nebo dodaného poskytovatele formátu. Řetězec vlastního formátu je "ddd, dd MMM yyyy HH':'mm':'ss 'GMT'". Při použití tohoto standardního specifikátoru formátu používá operace formátování nebo analýzy vždy neutrální jazykovou verzi.

Výsledný řetězec je ovlivněn následujícími <xref:System.Globalization.DateTimeFormatInfo> vlastnostmi objektu vráceného <xref:System.Globalization.DateTimeFormatInfo.InvariantInfo%2A?displayProperty=nameWithType> vlastností, která představuje invariantní jazykovou verzi.

|Vlastnost|Popis|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A>|Definuje formát výsledného řetězce.|
|<xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A>|Definuje zkrácené názvy dní, které mohou být zobrazeny ve výsledném řetězci.|
|<xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames%2A>|Definuje zkrácené názvy měsíců, které mohou být zobrazeny ve výsledném řetězci.|

Přestože standard RFC 1123 vyjadřuje čas jako koordinovaný světový čas (UTC), operace formátování <xref:System.DateTime> nezmění hodnotu objektu, který je formátován. Proto je nutné <xref:System.DateTime> převést hodnotu na <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> UTC voláním metody před provedením operace formátování. Naproti tomu <xref:System.DateTimeOffset> hodnoty provádějí tento převod automaticky; před operací formátování není <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> nutné volat metodu.

Následující příklad používá specifikátor formátu "r" <xref:System.DateTime> k <xref:System.DateTimeOffset> zobrazení hodnoty a hodnoty v systému v časovém pásmu Tichomoří USA.

[!code-csharp-interactive[Formatting.DateAndTime.Standard#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#9)]
[!code-vb[Formatting.DateAndTime.Standard#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#9)]

[Zpět na stůl](#table)

<a name="Sortable"></a>

## <a name="the-sortable-s-format-specifier"></a>Specifikátor seřaditelného formátu ("s")

Specifikátor standardního formátu "s" představuje vlastní řetězec formátu data <xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern%2A?displayProperty=nameWithType> a času, který je definován vlastností. Tento vzor odpovídá definovanému standardu (ISO 8601) a příslušná vlastnost je určena jen pro čtení. Proto je vždy stejný bez ohledu na použitou jazykovou verzi nebo dodaného poskytovatele formátu. Řetězec vlastního formátu je "yyyy'-'MM'-'dd'T'HH':'mm':'ss".

Účelem specifikátoru formátu "s" je vytvořit řetězce výsledků, které se řadí konzistentně vzestupně nebo sestupně na základě hodnot data a času. V důsledku toho, i když specifikátor standardního formátu "s" představuje hodnotu data a času v konzistentním formátu, operace formátování nezmění <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> hodnotu <xref:System.DateTimeOffset.Offset%2A?displayProperty=nameWithType> objektu data a času, který je formátován tak, aby odrážel jeho vlastnost nebo jeho hodnotu. Například řetězce výsledků vytvořené formátováním hodnot data a času 2014-11-15T18:32+00:00a 2014-11-15T18:32:17+08:00 jsou identické.

Při použití tohoto standardního specifikátoru formátu používá operace formátování nebo analýzy vždy neutrální jazykovou verzi.

Následující příklad používá specifikátor formátu "s" <xref:System.DateTime> k <xref:System.DateTimeOffset> zobrazení hodnoty a hodnoty v systému v časovém pásmu Usa tichomoří.

[!code-csharp-interactive[Formatting.DateAndTime.Standard#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#10)]
[!code-vb[Formatting.DateAndTime.Standard#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#10)]

[Zpět na stůl](#table)

<a name="ShortTime"></a>

## <a name="the-short-time-t-format-specifier"></a>Specifikátor krátkého formátu času ("t")

Specifikátor standardního formátu "t" představuje vlastní řetězec formátu data <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> a času, který je definován aktuální vlastností. Například řetězec vlastního formátu pro neutrální jazykovou verzi je "HH:mm".

Výsledný řetězec je ovlivněn informacemi o formátování <xref:System.Globalization.DateTimeFormatInfo> určitého objektu. V následující tabulce <xref:System.Globalization.DateTimeFormatInfo> jsou uvedeny vlastnosti objektu, které mohou řídit formátování vráceného řetězce. Vlastní specifikátor formátu, který <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> je vrácen vlastností některých kultur, nemusí využívat všechny vlastnosti.

|Vlastnost|Popis|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A>|Definuje formát komponenty času výsledného řetězce.|
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Definuje řetězec, který odděluje komponenty hodiny, minuty a sekundy v časovém údaji.|
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Definuje řetězec, který označuje dobu od půlnoci do doby před polednem ve 12hodinovém formátu.|
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Definuje řetězec, který označuje dobu od poledne do doby před půlnocí ve 12hodinovém formátu.|

Následující příklad používá specifikátor formátu "t" k zobrazení hodnoty data a času.

[!code-csharp[Formatting.DateAndTime.Standard#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#11)]
[!code-vb[Formatting.DateAndTime.Standard#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#11)]

[Zpět na stůl](#table)

<a name="LongTime"></a>

## <a name="the-long-time-t-format-specifier"></a>Specifikátor dlouhého formátu času ("T")

Specifikátor standardního formátu "T" představuje vlastní řetězec formátu data a času, který je definován <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> vlastností konkrétní jazykové verze. Například řetězec vlastního formátu pro neutrální jazykovou verzi je "HH:mm:ss".

V následující tabulce <xref:System.Globalization.DateTimeFormatInfo> jsou uvedeny vlastnosti objektu, které mohou řídit formátování vráceného řetězce. Vlastní specifikátor formátu, který <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> je vrácen vlastností některých kultur, nemusí využívat všechny vlastnosti.

|Vlastnost|Popis|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A>|Definuje formát komponenty času výsledného řetězce.|
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Definuje řetězec, který odděluje komponenty hodiny, minuty a sekundy v časovém údaji.|
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Definuje řetězec, který označuje dobu od půlnoci do doby před polednem ve 12hodinovém formátu.|
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Definuje řetězec, který označuje dobu od poledne do doby před půlnocí ve 12hodinovém formátu.|

Následující příklad používá specifikátor formátu "T" k zobrazení hodnoty data a času.

[!code-csharp[Formatting.DateAndTime.Standard#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#12)]
[!code-vb[Formatting.DateAndTime.Standard#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#12)]

[Zpět na stůl](#table)

<a name="UniversalSortable"></a>

## <a name="the-universal-sortable-u-format-specifier"></a>Specifikátor univerzálního seřaditelného formátu ("u")

Specifikátor standardního formátu "u" představuje vlastní řetězec formátu data <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A?displayProperty=nameWithType> a času, který je definován vlastností. Tento vzor odpovídá definovanému standardu a příslušná vlastnost je určena jen pro čtení. Proto je vždy stejný bez ohledu na použitou jazykovou verzi nebo dodaného poskytovatele formátu. Řetězec vlastního formátu je "yyyy'-'MM'-'dd HH':'mm':'ss'Z'". Při použití tohoto standardního specifikátoru formátu používá operace formátování nebo analýzy vždy neutrální jazykovou verzi.

Přestože výsledný řetězec by měl vyjádřit čas jako koordinovaný světový čas <xref:System.DateTime> (UTC), během operace formátování se neprovádí žádný převod původní hodnoty. Proto je nutné <xref:System.DateTime> převést hodnotu na <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> UTC voláním metody před formátováním.  Naproti tomu <xref:System.DateTimeOffset> hodnoty provádějí tento převod automaticky; před operací formátování není <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> nutné volat metodu.

Následující příklad používá specifikátor formátu "u" k zobrazení hodnoty data a času.

[!code-csharp-interactive[Formatting.DateAndTime.Standard#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#13)]
[!code-vb[Formatting.DateAndTime.Standard#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#13)]

[Zpět na stůl](#table)

<a name="UniversalFull"></a>

## <a name="the-universal-full-u-format-specifier"></a>Specifikátor univerzálního úplného formátu ("U")

Specifikátor standardního formátu "U" představuje vlastní řetězec formátu data a času, který je definován <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> vlastností zadané jazykové verze. Tento vzor je stejný jako vzor "F". <xref:System.DateTime> Hodnota je však automaticky převedena na Čas UTC před jeho formátováním.

V následující tabulce <xref:System.Globalization.DateTimeFormatInfo> jsou uvedeny vlastnosti objektu, které mohou řídit formátování vráceného řetězce. Vlastní specifikátor formátu, který <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A> je vrácen vlastností některých kultur, nemusí využívat všechny vlastnosti.

|Vlastnost|Popis|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A>|Definuje celkový formát výsledného řetězce.|
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Definuje lokalizované názvy dní, které mohou být zobrazeny ve výsledném řetězci.|
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Definuje lokalizované názvy měsíců, které mohou být zobrazeny ve výsledném řetězci.|
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Definuje řetězec, který odděluje komponenty hodiny, minuty a sekundy v časovém údaji.|
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Definuje řetězec, který označuje dobu od půlnoci do doby před polednem ve 12hodinovém formátu.|
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Definuje řetězec, který označuje dobu od poledne do doby před půlnocí ve 12hodinovém formátu.|

Specifikátor formátu "U" není podporován <xref:System.DateTimeOffset> typem a <xref:System.FormatException> vyvolá, pokud se <xref:System.DateTimeOffset> používá k formátování hodnoty.

Následující příklad používá specifikátor formátu "U" k zobrazení hodnoty data a času.

[!code-csharp[Formatting.DateAndTime.Standard#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#14)]
[!code-vb[Formatting.DateAndTime.Standard#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#14)]

[Zpět na stůl](#table)

<a name="YearMonth"></a>

## <a name="the-year-month-y-y-format-specifier"></a>Specifikátor formátu roku a měsíce ("Y", "y")

Specifikátor standardního formátu "Y" nebo "y" představuje vlastní řetězec formátu <xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern%2A?displayProperty=nameWithType> data a času, který je definován vlastností zadané jazykové verze. Například řetězec vlastního formátu pro neutrální jazykovou verzi je "yyyy MMMM".

V následující tabulce <xref:System.Globalization.DateTimeFormatInfo> jsou uvedeny vlastnosti objektu, které řídí formátování vráceného řetězce.

|Vlastnost|Popis|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern%2A>|Definuje celkový formát výsledného řetězce.|
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Definuje lokalizované názvy měsíců, které mohou být zobrazeny ve výsledném řetězci.|

Následující příklad používá specifikátor formátu "y" k zobrazení hodnoty data a času.

[!code-csharp[Formatting.DateAndTime.Standard#15](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#15)]
[!code-vb[Formatting.DateAndTime.Standard#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#15)]

[Zpět na stůl](#table)

<a name="Notes"></a>

## <a name="notes"></a>Poznámky

### <a name="control-panel-settings"></a>Nastavení části Ovládací panely

Nastavení v ovládacím panelu **Místní a jazykové možnosti** ovlivňují výsledný řetězec vytvořený operací formátování. Tato nastavení slouží k inicializaci objektu <xref:System.Globalization.DateTimeFormatInfo> přidruženého k aktuální jazykové verzi vlákna, který poskytuje hodnoty používané k řízení formátování. Počítače, které používají různá nastavení, generují různé výsledné řetězce.

Kromě toho pokud <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> použijete konstruktor k vytvoření <xref:System.Globalization.CultureInfo> instance nového objektu, který představuje stejnou jazykovou verzi jako aktuální jazyková verze systému, <xref:System.Globalization.CultureInfo> budou na nový objekt použita všechna vlastní nastavení vytvořená položkou **Místní a jazykové možnosti** v Ovládacích panelech. <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> Konstruktor můžete použít k <xref:System.Globalization.CultureInfo> vytvoření objektu, který neodráží vlastní nastavení systému.

### <a name="datetimeformatinfo-properties"></a>Vlastnosti DateTimeFormatInfo

Formátování je ovlivněno vlastnostmi aktuálního <xref:System.Globalization.DateTimeFormatInfo> objektu, který je implicitně poskytován aktuální <xref:System.IFormatProvider> jazykovou verzí vlákna nebo explicitně parametrem metody, která vyvolá formátování. Pro <xref:System.IFormatProvider> parametr aplikace by měla <xref:System.Globalization.CultureInfo> určit objekt, který představuje <xref:System.Globalization.DateTimeFormatInfo> jazykovou verzi nebo objekt, který představuje konkrétní jazykovou verzi datum a čas formátování konvence. Mnoho standardních specifikátorů formátu data a času jsou aliasy pro formátování <xref:System.Globalization.DateTimeFormatInfo> vzorů definovaných vlastnostmi aktuálního objektu. Aplikace může změnit výsledek vytvořený některými standardními specifikátory formátu data a času změnou odpovídajících vzorů formátu data a času odpovídající <xref:System.Globalization.DateTimeFormatInfo> vlastnosti.

## <a name="see-also"></a>Viz také

- <xref:System.DateTime?displayProperty=nameWithType>
- <xref:System.DateTimeOffset?displayProperty=nameWithType>
- [Typy formátování](../../../docs/standard/base-types/formatting-types.md)
- [Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
- [Ukázka: Nástroj pro formátování WinForms .NET (C#)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs)
- [Ukázka: Nástroj pro formátování WinForms .NET (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb)
