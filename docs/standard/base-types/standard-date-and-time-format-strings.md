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
ms.openlocfilehash: b67b00fdb4a5c484c112cc2f3321ce2268d4dad7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121711"
---
# <a name="standard-date-and-time-format-strings"></a>Standardní řetězce formátu data a času

Řetězec standardního formátu data a času používá pro definování textového vyjádření hodnoty data a času jeden specifikátor formátu. Libovolný řetězec formátu data a času, který obsahuje více než jeden znak, včetně prázdných znaků, je interpretován jako řetězec vlastního formátu data a času. Další informace naleznete v tématu [Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md). Řetězec standardního nebo vlastního formátu lze používat dvěma způsoby:

- Chcete-li definovat řetězec, který je výsledkem operace formátování.

- Chcete-li definovat textovou reprezentaci hodnoty data a času, která může být převedena na <xref:System.DateTime> nebo <xref:System.DateTimeOffset> hodnoty pomocí operace analýzy.

> [!TIP]
> Můžete si stáhnout **formátovací nástroj**, aplikaci .net Core model Windows Forms, která umožňuje použití řetězců formátu na číselné hodnoty nebo hodnoty data a času a zobrazuje výsledný řetězec. Zdrojový kód je k dispozici pro [C#](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs) a [Visual Basic](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb).

Řetězce standardního formátu data a času lze použít s hodnotami <xref:System.DateTime> i <xref:System.DateTimeOffset>.

[!INCLUDE[C# interactive-note](~/includes/csharp-interactive-with-utc-partial-note.md)]

<a name="table"></a>Následující tabulka popisuje standardní specifikátory formátu data a času. Není-li uvedeno jinak, konkrétní specifikátor standardního formátu data a času vytváří identickou řetězcovou reprezentaci bez ohledu na to, zda je použit s <xref:System.DateTime> nebo <xref:System.DateTimeOffset> hodnotou. Další informace o použití řetězců standardního formátu data a času naleznete v části [poznámky](#Notes) .

|Specifikátor formátu|Popis|Příklady|
|----------------------|-----------------|--------------|
|"d"|Vzor krátkého formátu data.<br /><br /> Další informace:[specifikátor krátkého formátu data ("d")](#ShortDate).|2009-06-15T13:45:30 > 6/15/2009 (EN-US)<br /><br /> 2009-06-15T13:45:30. > 15/06/2009 (fr-FR)<br /><br /> 2009-06-15T13:45:30. > 2009/06/15 (ja-JP)|
|"D"|Vzor dlouhého formátu data.<br /><br /> Další informace:[specifikátor dlouhého formátu data ("D")](#LongDate).|2009-06-15T13:45:30 > pondělí, 15. června 2009 (EN-US)<br /><br /> 2009-06-15T13:45:30-> 15 июня 2009 г. (ru-RU)<br /><br /> 2009-06-15T13:45:30-> Montag, 15. Juni 2009 (de-DE)|
|"f"|Vzor úplného formátu data/času (krátkého formátu času).<br /><br /> Další informace: [Specifikátor úplného formátu data a krátkého formátu času ("f")](#FullDateShortTime).|2009-06-15T13:45:30-> pondělí, 15. června 2009 1:45 odp. (EN-US)<br /><br /> 2009-06-15T13:45:30-> den 15 Juni 2009 13:45 (sv-SE)<br /><br /> 2009-06-15T13:45:30-> Δευτέρα, 15 Ιουνίου 2009 1:45 μμ (El-GR)|
|"F"|Vzor úplného formátu data/času (dlouhého formátu času).<br /><br /> Další informace: [Specifikátor úplného formátu data a dlouhého formátu času ("F")](#FullDateLongTime).|2009-06-15T13:45:30-> pondělí, 15. června 2009 1:45:30 ODP. (EN-US)<br /><br /> 2009-06-15T13:45:30-> den 15 Juni 2009 13:45:30 (sv-SE)<br /><br /> 2009-06-15T13:45:30-> Δευτέρα, 15 Ιουνίου 2009 1:45:30 μμ (El-GR)|
|"g"|Vzor obecného formátu data/času (krátkého formátu času).<br /><br /> Další informace: [specifikátor obecného formátu data a krátkého formátu času ("g")](#GeneralDateShortTime).|2009-06-15T13:45:30-> 6/15/2009 1:45 odp. (EN-US)<br /><br /> 2009-06-15T13:45:30. > 15/06/2009 13:45 (ES-ES)<br /><br /> 2009-06-15T13:45:30. > 2009/6/15 13:45 (zh-CN)|
|"G"|Vzor obecného formátu data a času (dlouhého formátu času).<br /><br /> Další informace: [specifikátor obecného formátu data a dlouhého formátu času ("G")](#GeneralDateLongTime).|2009-06-15T13:45:30-> 6/15/2009 1:45:30 ODP. (EN-US)<br /><br /> 2009-06-15T13:45:30. > 15/06/2009 13:45:30 (ES-ES)<br /><br /> 2009-06-15T13:45:30. > 2009/6/15 13:45:30 (zh-CN)|
|"M", "m"|Vzor formátu měsíce/dne.<br /><br /> Další informace: [specifikátor formátu month ("m", "m")](#MonthDay).|2009-06-15T13:45:30-> 15. června (EN-US)<br /><br /> 2009-06-15T13:45:30 – > 15. Juni (da-DK)<br /><br /> 2009-06-15T13:45:30 – > 15 Juni (ID-ID)|
|"O", "o"|Vzor formátu data/času zpátečního převodu.<br /><br /> Další informace: [specifikátor formátu Round-Trip ("o", "o")](#Roundtrip).|hodnoty <xref:System.DateTime>:<br /><br /> 2009-06-15T13:45:30 (DateTimeKind. Local)--> 2009-06-15T13:45:30.0000000-07:00<br /><br /> 2009-06-15T13:45:30 (DateTimeKind. UTC)--> 2009-06-15T13:45:30.0000000 Z<br /><br /> 2009-06-15T13:45:30 (DateTimeKind. unspecifikovaná)--> 2009-06-15T13:45:30.0000000<br /><br /> hodnoty <xref:System.DateTimeOffset>:<br /><br /> 2009-06-15T13:45:30.07:00--> 2009-06-15T13:45:30.0000000-07:00|
|"R", "r"|Vzor RFC1123.<br /><br /> Další informace: [specifikátor formátu RFC1123 ("r", "r")](#RFC1123).|2009-06-15T13:45:30-> Mon, 15. června 2009 20:45:30 GMT|
|"s"|Vzor seřaditelného formátu data/času.<br /><br /> Další informace: [specifikátor formátu ("s")](#Sortable).|2009-06-15T13:45:30 (DateTimeKind. Local)-> 2009-06-15T13:45:30<br /><br /> 2009-06-15T13:45:30 (DateTimeKind. UTC)-> 2009-06-15T13:45:30|
|"t"|Vzor krátkého formátu času.<br /><br /> Další informace: [specifikátor krátkého formátu času ("t")](#ShortTime).|2009-06-15T13:45:30-> 1:45 odp. (EN-US)<br /><br /> 2009-06-15T13:45:30 > 13:45 (HR-HR)<br /><br /> 2009-06-15T13:45:30-> 01:45 م (ar-EG)|
|"T"|Vzor dlouhého formátu času.<br /><br /> Další informace: [specifikátor dlouhého formátu času ("T")](#LongTime).|2009-06-15T13:45:30-> 1:45:30 ODP. (EN-US)<br /><br /> 2009-06-15T13:45:30 > 13:45:30 (HR-HR)<br /><br /> 2009-06-15T13:45:30-> 01:45:30 م (ar-EG)|
|"u"|Vzor univerzálního seřaditelného formátu data/času.<br /><br /> Další informace: [Specifikátor univerzálního formátu ("u")](#UniversalSortable).|S <xref:System.DateTime> hodnotou: 2009-06-15T13:45:30-> 2009-06-15 13:45:30Z<br /><br /> S <xref:System.DateTimeOffset> hodnotou: 2009-06-15T13:45:30-> 2009-06-15 20:45:30Z|
|"U"|Vzor univerzálního úplného formátu data/času.<br /><br /> Další informace: [Specifikátor univerzálního úplného formátu ("U")](#UniversalFull).|2009-06-15T13:45:30-> pondělí, 15. června 2009 8:45:30 ODP. (EN-US)<br /><br /> 2009-06-15T13:45:30-> den 15 Juni 2009 20:45:30 (sv-SE)<br /><br /> 2009-06-15T13:45:30-> Δευτέρα, 15 Ιουνίου 2009 8:45:30 μμ (El-GR)|
|"Y", "y"|Vzor formátu roku a měsíce.<br /><br /> Další informace: [specifikátor formátu roku a měsíce ("Y")](#YearMonth).|2009-06-15T13:45:30-> června, 2009 (EN-US)<br /><br /> 2009-06-15T13:45:30-> Juni 2009 (da-DK)<br /><br /> 2009-06-15T13:45:30-> Juni 2009 (ID-ID)|
|Jakýkoli jiný samostatný znak|Neznámý specifikátor.|Vyvolá dobu běhu <xref:System.FormatException>.|

## <a name="how-standard-format-strings-work"></a>Jak fungují řetězce standardního formátu

V rámci operace formátování je řetězec standardního formátu pouze aliasem pro řetězec vlastního formátu. Výhodou používání aliasu pro odkaz na řetězec vlastního formátu je skutečnost, že ačkoli alias zůstane neutrální, řetězec vlastního formátu se může změnit. Toto je důležité, protože řetězcová reprezentace hodnot data a času se obvykle liší podle jazykové verze. Například řetězec standardního formátu "d" označuje, že hodnota data a času má být zobrazena pomocí vzoru krátkého formátu data. Pro neutrální jazykovou verzi je použit formát "MM/dd/yyyy". Pro jazykovou verzi fr-FR je to formát "dd/MM/yyyy". Pro jazykovou verzi ja-JP je to formát "yyyy/MM/dd".

Pokud je řetězec standardního formátu v rámci operace formátování namapován na řetězec vlastního formátu konkrétní jazykové verze, může vaše aplikace definovat konkrétní jazykovou verzi, jejíž řetězce vlastního formátu se používají jedním z těchto způsobů:

- Můžete použít výchozí (nebo aktuální) jazykovou verzi. Následující příklad zobrazí datum pomocí krátkého formátu data aktuální jazykové verze. V tomto případě je aktuální jazyková verze nastavena na en-US.

  [!code-csharp-interactive[System.DateTime.Conceptual.Formatting#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#1)]
  [!code-vb[System.DateTime.Conceptual.Formatting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#1)]

- Můžete předat objekt <xref:System.Globalization.CultureInfo> reprezentující jazykovou verzi, jejíž formátování má být použito pro metodu, která má <xref:System.IFormatProvider> parametr. Následující příklad zobrazí datum pomocí formátu krátkého data jazykové verze pt-BR.

  [!code-csharp[System.DateTime.Conceptual.Formatting#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#2)]
  [!code-vb[System.DateTime.Conceptual.Formatting#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#2)]

- Můžete předat objekt <xref:System.Globalization.DateTimeFormatInfo>, který poskytuje informace o formátování metodě s parametrem <xref:System.IFormatProvider>. Následující příklad zobrazí datum pomocí krátkého formátu data z <xref:System.Globalization.DateTimeFormatInfo> objektu pro jazykovou verzi HR-HR.

  [!code-csharp[System.DateTime.Conceptual.Formatting#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#3)]
  [!code-vb[System.DateTime.Conceptual.Formatting#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#3)]

> [!NOTE]
> Informace o přizpůsobení vzorů nebo řetězců použitých při formátování hodnot data a času naleznete v tématu <xref:System.Globalization.NumberFormatInfo> třídy.

V některých případech slouží řetězec standardního formátu jako vhodná zkratka pro řetězec vlastního delšího formátu, který je neutrální. Do této kategorie patří čtyři řetězce standardního formátu: "O" (nebo "o"), "R" (nebo "r"), "s" a "u". Tyto řetězce odpovídají řetězcům vlastního formátu, které jsou definovány neutrální jazykovou verzí. Vytvářejí řetězcové reprezentace hodnot data a času, které mají být identické napříč jazykovými verzemi. Následující tabulka obsahuje informace o těchto čtyřech řetězcích standardního formátu data a času.

|Řetězec standardního formátu|Definovaný vlastností DateTimeFormatInfo.InvariantInfo|Řetězec vlastního formátu|
|----------------------------|----------------------------------------------------------|--------------------------|
|"O" nebo "o"|Žádné|yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffzz|
|"R" nebo "r"|<xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A>|ddd, dd MMM yyyy HH':'mm':'ss 'GMT'|
|"s"|<xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern%2A>|yyyy'-'MM'-'dd'T'HH':'mm':'ss|
|"u"|<xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>|yyyy'-'MM'-'dd HH':'mm':'ss'Z'|

Standardní formátovací řetězce lze také použít při analýze operací s metodami <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, která vyžaduje, aby vstupní řetězec přesně odpovídal konkrétnímu vzoru pro úspěšné provedení operace analýzy. Mnoho řetězců standardního formátu je namapováno na několik řetězců vlastního formátu. Hodnotu data a času lze tedy vyjádřit v celé řadě formátů a operace analýzy i tak proběhne úspěšně. Můžete určit řetězec vlastního formátu nebo řetězce, které odpovídají standardnímu formátovacímu řetězci, voláním metody <xref:System.Globalization.DateTimeFormatInfo.GetAllDateTimePatterns%28System.Char%29?displayProperty=nameWithType>. Následující příklad zobrazí řetězce vlastního formátu, které mapují řetězec standardního formátu "d" (vzor krátkého formátu data).

[!code-csharp[Formatting.DateAndTime.Standard#17](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/stdandparsing1.cs#17)]
[!code-vb[Formatting.DateAndTime.Standard#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/stdandparsing1.vb#17)]

Následující části popisují standardní specifikátory formátu pro hodnoty <xref:System.DateTime> a <xref:System.DateTimeOffset>.

<a name="ShortDate"></a>

## <a name="the-short-date-d-format-specifier"></a>Specifikátor krátkého formátu data ("d")

Standardní specifikátor formátu "d" představuje řetězec vlastního formátu data a času, který je definován vlastností <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> konkrétní jazykové verze. Například řetězec vlastního formátu, který je vrácen vlastností <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A> neutrální jazykové verze, je "MM/dd/rrrr".

V následující tabulce jsou uvedeny vlastnosti objektů <xref:System.Globalization.DateTimeFormatInfo>, které řídí formátování vráceného řetězce.

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

Standardní specifikátor formátu "D" představuje řetězec vlastního formátu data a času, který je definován aktuální vlastností <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType>. Například řetězec vlastního formátu pro neutrální jazykovou verzi je "dddd, dd MMMM yyyy".

V následující tabulce jsou uvedeny vlastnosti objektu <xref:System.Globalization.DateTimeFormatInfo>, které řídí formátování vráceného řetězce.

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

Výsledný řetězec je ovlivněn informacemi o formátování určitého objektu <xref:System.Globalization.DateTimeFormatInfo>. V následující tabulce jsou uvedeny vlastnosti objektů <xref:System.Globalization.DateTimeFormatInfo>, které mohou řídit formátování vráceného řetězce. Vlastní specifikátor formátu vrácený <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> a <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> vlastností některých kultur nemusí využívat všechny vlastnosti.

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

Standardní specifikátor formátu "F" představuje řetězec vlastního formátu data a času, který je definován aktuální vlastností <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType>. Například řetězec vlastního formátu pro neutrální jazykovou verzi je "dddd, dd MMMM yyyy HH:mm:ss".

V následující tabulce jsou uvedeny vlastnosti objektů <xref:System.Globalization.DateTimeFormatInfo>, které mohou řídit formátování vráceného řetězce. Specifikátor vlastního formátu, který je vrácen vlastností <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A> některých kultur, nemusí využívat všechny vlastnosti.

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

Výsledný řetězec je ovlivněn informacemi o formátování určitého objektu <xref:System.Globalization.DateTimeFormatInfo>. V následující tabulce jsou uvedeny vlastnosti objektů <xref:System.Globalization.DateTimeFormatInfo>, které mohou řídit formátování vráceného řetězce. Specifikátor vlastního formátu, který je vrácen <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> a <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> vlastností některých kultur, nemusí využívat všechny vlastnosti.

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

Výsledný řetězec je ovlivněn informacemi o formátování určitého objektu <xref:System.Globalization.DateTimeFormatInfo>. V následující tabulce jsou uvedeny vlastnosti objektů <xref:System.Globalization.DateTimeFormatInfo>, které mohou řídit formátování vráceného řetězce. Specifikátor vlastního formátu, který je vrácen <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> a <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> vlastností některých kultur, nemusí využívat všechny vlastnosti.

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

Standardní specifikátor formátu "M" nebo "M" představuje řetězec vlastního formátu data a času, který je definován aktuální vlastností <xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern%2A?displayProperty=nameWithType>. Například řetězec vlastního formátu pro neutrální jazykovou verzi je "MMMM dd".

V následující tabulce jsou uvedeny vlastnosti objektů <xref:System.Globalization.DateTimeFormatInfo>, které řídí formátování vráceného řetězce.

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

Standardní specifikátor formátu "O" nebo "o" představuje řetězec vlastního formátu data a času pomocí vzoru, který zachovává informace o časovém pásmu a generuje výsledný řetězec, který odpovídá normě ISO 8601. Pro <xref:System.DateTime> hodnoty je tento specifikátor formátu navržen tak, aby zachoval hodnoty data a času spolu s vlastností <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> v textu. Formátovaný řetězec lze analyzovat zpět pomocí metody <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> nebo <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>, je-li parametr `styles` nastaven na <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>.

Standardní specifikátor formátu "O" nebo "o" odpovídá "yyyy-yyyy '-DD 't": ' mm ': ' mm ': ' ss '. ' fffffffK "řetězec vlastního formátu pro hodnoty <xref:System.DateTime> a na" yyyy-yyyy '-DD 't ":" mm ":" SS ". fffffffzzz řetězec vlastního formátu pro hodnoty <xref:System.DateTimeOffset>. Dvojice jednoduchých uvozovek v tomto řetězci oddělující jednotlivé znaky, jako jsou například spojovníky, dvojtečky a písmeno "T", označují, že jednotlivé znaky jsou literály, které nelze změnit. Apostrofy se ve výstupním řetězci nezobrazují.

Standardní specifikátor formátu "O" nebo "o" (a "yyyy-yyyy '-DD 't": ' mm ': ' ss '. ' fffffffK "řetězec vlastního formátu") využívá tři způsoby, které ISO 8601 představuje informace o časovém pásmu pro zachování vlastnosti <xref:System.DateTime.Kind%2A> <xref:System.DateTime> hodnot:

- Komponenta časového pásma <xref:System.DateTimeKind.Local?displayProperty=nameWithType> hodnoty data a času je posun od času UTC (například + 01:00,-07:00). Všechny hodnoty <xref:System.DateTimeOffset> jsou také reprezentovány v tomto formátu.

- Komponenta časového pásma <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> hodnoty data a času používá "Z" (který představuje nulový posun) k reprezentaci UTC.

- <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> hodnoty data a času nemají žádné informace o časovém pásmu.

Vzhledem k tomu, že standardní specifikátor formátu "O" nebo "o" odpovídá mezinárodnímu standardu, operace formátování nebo analýzy, která používá specifikátor, vždy používá invariantní jazykovou verzi a gregoriánský kalendář.

Řetězce, které jsou předány `Parse`, `TryParse`, `ParseExact`a metody `TryParseExact` <xref:System.DateTime> a <xref:System.DateTimeOffset> lze analyzovat pomocí specifikátoru formátu "O" nebo "o", pokud jsou v jednom z těchto formátů. V případě <xref:System.DateTime> objektů by přetěžování při analýze mělo zahrnovat také parametr `styles` s hodnotou <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>. Všimněte si, že pokud zavoláte metodu analýzy s vlastním řetězcem formátu, který odpovídá specifikátoru formátu "O" nebo "o", nezískáte stejné výsledky jako "O" nebo "o". Důvodem je, že analýza metod, které používají řetězec vlastního formátu, nemůže analyzovat řetězcovou reprezentaci hodnot data a času, které chybí komponenty časového pásma, nebo použít "Z" k označení času UTC.

Následující příklad používá specifikátor formátu "o" pro zobrazení řady <xref:System.DateTime> hodnoty a hodnotu <xref:System.DateTimeOffset> v systému v americké tichomořském časovém pásmu.

[!code-csharp[Formatting.DateAndTime.Standard#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/o1.cs#8)]
[!code-vb[Formatting.DateAndTime.Standard#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/o1.vb#8)]

Následující příklad používá specifikátor formátu "o" pro vytvoření formátovaného řetězce a následně obnoví původní hodnotu data a času voláním metody data a času `Parse`.

[!code-csharp[Formatting.DateandTime.Standard#16](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Roundtrip1.cs#16)]
[!code-vb[Formatting.DateandTime.Standard#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/RoundTrip1.vb#16)]

[Zpět na tabulku](#table)

<a name="RFC1123"></a>

## <a name="the-rfc1123-r-r-format-specifier"></a>Specifikátor formátu RFC1123 ("R", "r")

Standardní specifikátor formátu "R" nebo "r" představuje řetězec vlastního formátu data a času, který je definován vlastností <xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A?displayProperty=nameWithType>. Tento vzor odpovídá definovanému standardu a příslušná vlastnost je určena jen pro čtení. Proto je vždy stejný bez ohledu na použitou jazykovou verzi nebo dodaného poskytovatele formátu. Řetězec vlastního formátu je "ddd, dd MMM yyyy HH':'mm':'ss 'GMT'". Při použití tohoto standardního specifikátoru formátu používá operace formátování nebo analýzy vždy neutrální jazykovou verzi.

Výsledný řetězec je ovlivněn následujícími vlastnostmi objektu <xref:System.Globalization.DateTimeFormatInfo> vráceného vlastností <xref:System.Globalization.DateTimeFormatInfo.InvariantInfo%2A?displayProperty=nameWithType>, která představuje invariantní jazykovou verzi.

|Vlastnost|Popis|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A>|Definuje formát výsledného řetězce.|
|<xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A>|Definuje zkrácené názvy dní, které mohou být zobrazeny ve výsledném řetězci.|
|<xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames%2A>|Definuje zkrácené názvy měsíců, které mohou být zobrazeny ve výsledném řetězci.|

I když standard RFC 1123 vyjadřuje čas jako koordinovaný světový čas (UTC), operace formátování neupraví hodnotu objektu <xref:System.DateTime>, který se formátuje. Proto je nutné převést <xref:System.DateTime> hodnoty na čas UTC voláním metody <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> před provedením operace formátování. Naproti tomu <xref:System.DateTimeOffset> hodnoty provádějí tento převod automaticky; před operací formátování není nutné volat metodu <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType>.

Následující příklad používá specifikátor formátu "r" pro zobrazení <xref:System.DateTime> a hodnoty <xref:System.DateTimeOffset> v systému v americké tichomořském časovém pásmu.

[!code-csharp-interactive[Formatting.DateAndTime.Standard#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#9)]
[!code-vb[Formatting.DateAndTime.Standard#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#9)]

[Zpět na tabulku](#table)

<a name="Sortable"></a>

## <a name="the-sortable-s-format-specifier"></a>Specifikátor seřaditelného formátu ("s")

Standardní specifikátor formátu "s" představuje řetězec vlastního formátu data a času, který je definován vlastností <xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern%2A?displayProperty=nameWithType>. Tento vzor odpovídá definovanému standardu (ISO 8601) a příslušná vlastnost je určena jen pro čtení. Proto je vždy stejný bez ohledu na použitou jazykovou verzi nebo dodaného poskytovatele formátu. Řetězec vlastního formátu je "yyyy'-'MM'-'dd'T'HH':'mm':'ss".

Účelem specifikátoru formátu "s" je vytváření výsledných řetězců, které se konzistentně řadí ve vzestupném nebo sestupném pořadí podle hodnot data a času. V důsledku toho i když standardní specifikátor formátu "s" představuje hodnotu data a času v konzistentním formátu, operace formátování neupravuje hodnotu objektu data a času, který je formátován tak, aby odrážel jeho vlastnost <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> nebo jeho <xref:System.DateTimeOffset.Offset%2A?displayProperty=nameWithType> osa. Například výsledné řetězce vytvořené formátováním hodnot data a času 2014-11-15T18:32:17 + 00:00 a 2014-11-15T18:32:17 + 08:00 jsou identické.

Při použití tohoto standardního specifikátoru formátu používá operace formátování nebo analýzy vždy neutrální jazykovou verzi.

Následující příklad používá specifikátor formátu "s" pro zobrazení <xref:System.DateTime> a hodnoty <xref:System.DateTimeOffset> v systému v americké tichomořském časovém pásmu.

[!code-csharp-interactive[Formatting.DateAndTime.Standard#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#10)]
[!code-vb[Formatting.DateAndTime.Standard#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#10)]

[Zpět na tabulku](#table)

<a name="ShortTime"></a>

## <a name="the-short-time-t-format-specifier"></a>Specifikátor krátkého formátu času ("t")

Standardní specifikátor formátu "t" představuje řetězec vlastního formátu data a času, který je definován aktuální vlastností <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType>. Například řetězec vlastního formátu pro neutrální jazykovou verzi je "HH:mm".

Výsledný řetězec je ovlivněn informacemi o formátování určitého objektu <xref:System.Globalization.DateTimeFormatInfo>. V následující tabulce jsou uvedeny vlastnosti objektů <xref:System.Globalization.DateTimeFormatInfo>, které mohou řídit formátování vráceného řetězce. Specifikátor vlastního formátu, který je vrácen vlastností <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> některých kultur, nemusí využívat všechny vlastnosti.

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

Standardní specifikátor formátu "T" představuje řetězec vlastního formátu data a času, který je definován vlastností <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> konkrétní jazykové verze. Například řetězec vlastního formátu pro neutrální jazykovou verzi je "HH:mm:ss".

V následující tabulce jsou uvedeny vlastnosti objektů <xref:System.Globalization.DateTimeFormatInfo>, které mohou řídit formátování vráceného řetězce. Specifikátor vlastního formátu, který je vrácen vlastností <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> některých kultur, nemusí využívat všechny vlastnosti.

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

Standardní specifikátor formátu "u" představuje řetězec vlastního formátu data a času, který je definován vlastností <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A?displayProperty=nameWithType>. Tento vzor odpovídá definovanému standardu a příslušná vlastnost je určena jen pro čtení. Proto je vždy stejný bez ohledu na použitou jazykovou verzi nebo dodaného poskytovatele formátu. Řetězec vlastního formátu je "yyyy'-'MM'-'dd HH':'mm':'ss'Z'". Při použití tohoto standardního specifikátoru formátu používá operace formátování nebo analýzy vždy neutrální jazykovou verzi.

I když by výsledný řetězec měl vyjadřovat čas koordinovaný světový čas (UTC), během operace formátování se neprovede žádný převod původní <xref:System.DateTime> hodnoty. Proto je nutné převést <xref:System.DateTime> hodnoty na čas UTC voláním metody <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> před jejím formátováním.  Naproti tomu <xref:System.DateTimeOffset> hodnoty provádějí tento převod automaticky; před operací formátování není nutné volat metodu <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType>.

Následující příklad používá specifikátor formátu "u" k zobrazení hodnoty data a času.

[!code-csharp-interactive[Formatting.DateAndTime.Standard#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#13)]
[!code-vb[Formatting.DateAndTime.Standard#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#13)]

[Zpět na tabulku](#table)

<a name="UniversalFull"></a>

## <a name="the-universal-full-u-format-specifier"></a>Specifikátor univerzálního úplného formátu ("U")

Standardní specifikátor formátu "U" představuje řetězec vlastního formátu data a času, který je definován vlastností <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> zadané jazykové verze. Tento vzor je stejný jako vzor "F". Hodnota <xref:System.DateTime> je však automaticky převedena na UTC před formátováním.

V následující tabulce jsou uvedeny vlastnosti objektů <xref:System.Globalization.DateTimeFormatInfo>, které mohou řídit formátování vráceného řetězce. Specifikátor vlastního formátu, který je vrácen vlastností <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A> některých kultur, nemusí využívat všechny vlastnosti.

|Vlastnost|Popis|
|--------------|-----------------|
|<xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A>|Definuje celkový formát výsledného řetězce.|
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|Definuje lokalizované názvy dní, které mohou být zobrazeny ve výsledném řetězci.|
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|Definuje lokalizované názvy měsíců, které mohou být zobrazeny ve výsledném řetězci.|
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|Definuje řetězec, který odděluje komponenty hodiny, minuty a sekundy v časovém údaji.|
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|Definuje řetězec, který označuje dobu od půlnoci do doby před polednem ve 12hodinovém formátu.|
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|Definuje řetězec, který označuje dobu od poledne do doby před půlnocí ve 12hodinovém formátu.|

Specifikátor formátu "U" není podporován typem <xref:System.DateTimeOffset> a vyvolá <xref:System.FormatException>, pokud je použit k formátování <xref:System.DateTimeOffset> hodnoty.

Následující příklad používá specifikátor formátu "U" k zobrazení hodnoty data a času.

[!code-csharp[Formatting.DateAndTime.Standard#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#14)]
[!code-vb[Formatting.DateAndTime.Standard#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#14)]

[Zpět na tabulku](#table)

<a name="YearMonth"></a>

## <a name="the-year-month-y-y-format-specifier"></a>Specifikátor formátu roku a měsíce ("Y", "y")

Standardní specifikátor formátu "Y" nebo "y" představuje řetězec vlastního formátu data a času, který je definován vlastností <xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern%2A?displayProperty=nameWithType> zadané jazykové verze. Například řetězec vlastního formátu pro neutrální jazykovou verzi je "yyyy MMMM".

V následující tabulce jsou uvedeny vlastnosti objektů <xref:System.Globalization.DateTimeFormatInfo>, které řídí formátování vráceného řetězce.

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

Nastavení v položce **místní a jazykové** nastavení v Ovládacích panelech ovlivní výsledný řetězec vytvořený při operaci formátování. Tato nastavení slouží k inicializaci objektu <xref:System.Globalization.DateTimeFormatInfo> přidruženého k aktuální jazykové verzi vlákna, což poskytuje hodnoty používané k řízení formátování. Počítače, které používají různá nastavení, generují různé výsledné řetězce.

Kromě toho, pokud použijete konstruktor <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> k vytvoření instance nového objektu <xref:System.Globalization.CultureInfo>, který představuje stejnou jazykovou verzi jako aktuální jazyková verze systému, všechna přizpůsobení, která jsou vytvořena položkou **místní a jazykové nastavení** v Ovládacích panelech, budou použito pro nový objekt <xref:System.Globalization.CultureInfo>. Konstruktor <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> lze použít k vytvoření objektu <xref:System.Globalization.CultureInfo>, který nereflektuje vlastní nastavení systému.

### <a name="datetimeformatinfo-properties"></a>Vlastnosti DateTimeFormatInfo

Formátování je ovlivněno vlastnostmi aktuálního objektu <xref:System.Globalization.DateTimeFormatInfo>, který je poskytnut implicitně aktuální jazykovou verzí vlákna nebo explicitně parametrem <xref:System.IFormatProvider> metody, která vyvolá formátování. Pro parametr <xref:System.IFormatProvider> by měla vaše aplikace určovat <xref:System.Globalization.CultureInfo> objekt, který představuje jazykovou verzi, nebo objekt <xref:System.Globalization.DateTimeFormatInfo>, který představuje konvence formátování data a času konkrétní jazykové verze. Mnohé standardní specifikátory formátu data a času jsou aliasy pro vzory formátování definované vlastnostmi aktuálního objektu <xref:System.Globalization.DateTimeFormatInfo>. Vaše aplikace může změnit výsledek vytvořený některými specifikátory standardního formátu data a času změnou odpovídajícího vzoru formátu data a času odpovídající vlastnosti <xref:System.Globalization.DateTimeFormatInfo>.

## <a name="see-also"></a>Viz také:

- <xref:System.DateTime?displayProperty=nameWithType>
- <xref:System.DateTimeOffset?displayProperty=nameWithType>
- [Typy formátování](../../../docs/standard/base-types/formatting-types.md)
- [Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
- [Ukázka: nástroj formátování WinForms pro .NET CoreC#()](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs)
- [Ukázka: nástroj formátování WinForms pro .NET Core (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb)
