---
title: Vlastní formátovací řetězce data a času
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
ms.assetid: 98b374e3-0cc2-4c78-ab44-efb671d71984
ms.openlocfilehash: b33366922677b26f8fe99454206cacd5bb124f32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159270"
---
# <a name="custom-date-and-time-format-strings"></a>Vlastní formátovací řetězce data a času

Řetězec formátu data a času definuje <xref:System.DateTime> textovou <xref:System.DateTimeOffset> reprezentaci hodnoty nebo hodnotu, která je výsledkem operace formátování. Může také definovat reprezentaci hodnoty data a času nezbytnou v rámci operace analýzy a úspěšně tak řetězec převést na datum a čas. Řetězec vlastního formátu se skládá z jednoho nebo více vlastních specifikátorů formátu data a času. Každý řetězec, který není [standardnířetězec formátu data a času,](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) je interpretován jako vlastní řetězec formátu data a času.

> [!TIP]
> Můžete si stáhnout **nástroj Formátování**, aplikaci .NET Core Windows Forms, která umožňuje použít formátovací řetězce na číselné hodnoty nebo hodnoty data a času a zobrazí výsledný řetězec. Zdrojový kód je k dispozici pro [c#](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs) a [visual basic](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb).

Vlastní řetězce formátu data a času <xref:System.DateTime> lze <xref:System.DateTimeOffset> použít s hodnotami i s hodnotami.

[!INCLUDE[C# interactive-note](~/includes/csharp-interactive-with-utc-partial-note.md)]

<a name="table"></a>Při operacích formátování lze vlastní řetězce formátu data a `ToString` času použít buď s metodou instance data a času, nebo s metodou, která podporuje složené formátování. Následující příklad znázorňuje oba způsoby použití.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#17](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/custandformatting1.cs#17)]
[!code-vb[Formatting.DateAndTime.Custom#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/custandformatting1.vb#17)]

Při operacích analýzy lze pomocí metod <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, a metod <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> použít vlastní řetězce formátu data a času. Tyto metody vyžadují, aby vstupní řetězec přesně odpovídá určitému vzoru pro operaci analýzy úspěšné. Následující příklad ilustruje volání <xref:System.DateTimeOffset.ParseExact%28System.String%2CSystem.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody analyzovat datum, které musí obsahovat den, měsíc a dvouciferný rok.

[!code-csharp[Formatting.DateAndTime.Custom#18](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/custandparsing1.cs#18)]
[!code-vb[Formatting.DateAndTime.Custom#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/custandparsing1.vb#18)]

Následující tabulka popisuje specifikátory vlastního formátu data a času a zobrazuje výsledný řetězec, který je vytvořen jednotlivými specifikátory formátu. Ve výchozím nastavení odráží výsledný řetězec konvence formátování jazykové verze en-US. Pokud konkrétní specifikátor formátu vytváří lokalizovaný výsledný řetězec, je v příkladu rovněž uvedena jazyková verze, na kterou se výsledný řetězec vztahuje. Další informace o používání vlastních formátovacích řetězců data a času naleznete v části [Poznámky.](#notes)

| Specifikátor formátu | Popis | Příklady |
| ---------------------- | ----------------- | -------------- |
|"d"|Den měsíce, od 1 do 31.<br /><br /> Další informace: [Vlastní specifikátor formátu "d"](#dSpecifier).|2009-06-01T13:45:30 -> 1<br /><br /> 2009-06-15T13:45:30 -> 15|
|"dd"|Den měsíce, od 01 do 31.<br /><br /> Další informace: [Vlastní specifikátor formátu dd](#ddSpecifier).|2009-06-01T13:45:30 -> 01<br /><br /> 2009-06-15T13:45:30 -> 15|
|"ddd"|Zkrácený název dne v týdnu.<br /><br /> Další informace: [Vlastní specifikátor formátu ddd](#dddSpecifier).|2009-06-15T13:45:30 -> Po (cs-US)<br /><br /> 2009-06-15T13:45:30 -> Пн (ru-RU)<br /><br /> 2009-06-15T13:45:30 -> lun. (fr-FR)|
|"dddd"|Úplný název dne v týdnu.<br /><br /> Další informace: [Vlastní specifikátor formátu dddd](#ddddSpecifier).|2009-06-15T13:45:30 -> pondělí (en-US)<br /><br /> 2009-06-15T13:45:30 -> понедельник (ru-RU)<br /><br /> 2009-06-15T13:45:30 -> lundi (fr-FR)|
|"f"|Desetiny sekundy v hodnotě data a času.<br /><br /> Další informace: [Vlastní specifikátor formátu "f"](#fSpecifier).|2009-06-15T13:45:30.6170000 -> 6<br /><br /> 2009-06-15T13:45:30.05 -> 0|
|"ff"|Setiny sekundy v hodnotě data a času.<br /><br /> Další informace: [Vlastní specifikátor formátu ff](#ffSpecifier).|2009-06-15T13:45:30.6170000 -> 61<br /><br /> 2009-06-15T13:45:30.0050000 -> 00|
|"fff"|Milisekundy v hodnotě data a času.<br /><br /> Další informace: [Vlastní specifikátor formátu fff](#fffSpecifier).|15.6.2009 13:45:30.617 -> 617<br /><br /> 15.6.2009 13:45:30.0005 -> 000|
|"ffff"|Desetitisíciny sekundy v hodnotě data a času.<br /><br /> Další informace: [Vlastní specifikátor formátu FFFF](#ffffSpecifier).|2009-06-15T13:45:30.6175000 -> 6175<br /><br /> 2009-06-15T13:45:30.0000500 -> 0000|
|"fffff"|Stotisíciny sekundy v hodnotě data a času.<br /><br /> Další informace: [Vlastní specifikátor formátu fffff](#fffffSpecifier).|2009-06-15T13:45:30.6175400 -> 61754<br /><br /> 15.6.2009 13:45:30.000005 -> 00000|
|"ffffff"|Miliontiny sekundy v hodnotě data a času.<br /><br /> Další informace: [Vlastní specifikátor formátu ffffff](#ffffffSpecifier).|2009-06-15T13:45:30.6175420 -> 617542<br /><br /> 2009-06-15T13:45:30.0000005 -> 000000|
|"fffffff"|Desetimiliontiny sekundy v hodnotě data a času.<br /><br /> Další informace: [Vlastní specifikátor formátu fffffff](#fffffffSpecifier).|2009-06-15T13:45:30.6175425 -> 6175425<br /><br /> 2009-06-15T13:45:30.0001150 -> 0001150|
|"F"|Pokud je hodnota nenulová, jedná se o desetiny sekundy v hodnotě data a času.<br /><br /> Další informace: [Vlastní specifikátor formátu "F"](#F_Specifier).|2009-06-15T13:45:30.6170000 -> 6<br /><br /> 2009-06-15T13:45:30.0500000 -> (bez výstupu)|
|"FF"|Pokud je hodnota nenulová, jedná se o setiny sekundy v hodnotě data a času.<br /><br /> Další informace: [Vlastní specifikátor formátu FF](#FF_Specifier).|2009-06-15T13:45:30.6170000 -> 61<br /><br /> 2009-06-15T13:45:30.0050000 -> (bez výstupu)|
|"FFF"|Pokud je hodnota nenulová, jedná se o milisekundy v hodnotě data a času.<br /><br /> Další informace: [Vlastní specifikátor formátu FFF](#FFF_Specifier).|2009-06-15T13:45:30.6170000 -> 617<br /><br /> 2009-06-15T13:45:30.0005000 -> (bez výstupu)|
|"FFFF"|Pokud je hodnota nenulová, jedná se o desetitisíciny sekundy v hodnotě data a času.<br /><br /> Další informace: [Vlastní specifikátor formátu FFFF](#FFFF_Specifier).|2009-06-15T13:45:30.5275000 -> 5275<br /><br /> 2009-06-15T13:45:30.0000500 -> (bez výstupu)|
|"FFFFF"|Pokud je hodnota nenulová, jedná se o stotisíciny sekundy v hodnotě data a času.<br /><br /> Další informace: [Vlastní specifikátor formátu FFFFF](#FFFFF_Specifier).|2009-06-15T13:45:30.6175400 -> 61754<br /><br /> 2009-06-15T13:45:30.0000050 -> (bez výstupu)|
|"FFFFFF"|Pokud je hodnota nenulová, jedná se o miliontiny sekundy v hodnotě data a času.<br /><br /> Další informace: [Vlastní specifikátor formátu FFFFFF](#FFFFFF_Specifier).|2009-06-15T13:45:30.6175420 -> 617542<br /><br /> 2009-06-15T13:45:30.0000005 -> (bez výstupu)|
|"FFFFFFF"|Pokud je hodnota nenulová, jedná se o desetimiliontiny sekundy v hodnotě data a času.<br /><br /> Další informace: [Vlastní specifikátor formátu FFFFFFF](#FFFFFFF_Specifier).|2009-06-15T13:45:30.6175425 -> 6175425<br /><br /> 2009-06-15T13:45:30.0001150 -> 000115|
|"g", "gg"|Období nebo éra.<br /><br /> Další informace: [Vlastní specifikátor formátu "g" nebo "gg"](#gSpecifier).|2009-06-15T13:45:30.6170000 -> ND|
|"h"|Hodiny ve 12hodinovém formátu, od 1 do 12.<br /><br /> Další informace: [Vlastní specifikátor formátu "h"](#hSpecifier).|2009-06-15T01:45:30 -> 1<br /><br /> 2009-06-15T13:45:30 -> 1|
|"hh"|Hodiny ve 12hodinovém formátu, od 01 do 12.<br /><br /> Další informace: [Vlastní specifikátor formátu hh](#hhSpecifier).|2009-06-15T01:45:30 -> 01<br /><br /> 2009-06-15T13:45:30 -> 01|
|"H"|Hodiny ve 24hodinovém formátu, od 0 do 23.<br /><br /> Další informace: [Vlastní specifikátor formátu "H"](#H_Specifier).|2009-06-15T01:45:30 -> 1<br /><br /> 2009-06-15T13:45:30 -> 13|
|"HH"|Hodiny ve 24hodinovém formátu, od 00 do 23.<br /><br /> Další informace: [Vlastní specifikátor formátu HH](#HH_Specifier).|2009-06-15T01:45:30 -> 01<br /><br /> 2009-06-15T13:45:30 -> 13|
|"K"|Informace o časovém pásmu.<br /><br /> Další informace: [Vlastní specifikátor formátu "K"](#KSpecifier).|S <xref:System.DateTime> hodnotami:<br /><br /> 2009-06-15T13:45:30, Druh Nespecifikovaný -><br /><br /> 2009-06-15T13:45:30, Druh Utc -> Z<br /><br /> 2009-06-15T13:45:30, Kind Local -> -07:00 (závisí na nastavení místního počítače)<br /><br /> S <xref:System.DateTimeOffset> hodnotami:<br /><br /> 2009-06-15T01:45:30-07:00 --> -07:00<br /><br /> 2009-06-15T08:45:30+00:00 --> +00:00|
|"m"|Minuty, od 0 do 59.<br /><br /> Další informace: [Vlastní specifikátor formátu "m"](#mSpecifier).|2009-06-15T01:09:30 -> 9<br /><br /> 2009-06-15T13:29:30 -> 29|
|"mm"|Minuty, od 00 do 59.<br /><br /> Další informace: [Vlastní specifikátor formátu "mm"](#mmSpecifier).|2009-06-15T01:09:30 -> 09<br /><br /> 2009-06-15T01:45:30 -> 45|
|"M"|Měsíc, od 1 do 12.<br /><br /> Další informace: [Vlastní specifikátor formátu "M"](#M_Specifier).|2009-06-15T13:45:30 -> 6|
|"MM"|Měsíc, od 01 do 12.<br /><br /> Další informace: [Vlastní specifikátor formátu MM](#MM_Specifier).|2009-06-15T13:45:30 -> 06|
|"MMM"|Zkrácený název měsíce.<br /><br /> Další informace: [Vlastní specifikátor formátu MMM](#MMM_Specifier).|2009-06-15T13:45:30 -> červen (cs-US)<br /><br /> 2009-06-15T13:45:30 -> juin (fr-FR)<br /><br /> 2009-06-15T13:45:30 -> června (zu-ZA)|
|"MMMM"|Úplný název měsíce.<br /><br /> Další informace: [Vlastní specifikátor formátu MMMM](#MMMM_Specifier).|2009-06-15T13:45:30 -> červen (en-US)<br /><br /> 2009-06-15T13:45:30 -> juni (da-DK)<br /><br /> 2009-06-15T13:45:30 -> uJuni (zu-ZA)|
|"s"|Sekundy, od 0 do 59.<br /><br /> Další informace: [Vlastní specifikátor formátu "s"](#sSpecifier).|2009-06-15T13:45:09 -> 9|
|"ss"|Sekundy, od 00 do 59.<br /><br /> Další informace: [Vlastní specifikátor formátu ss](#ssSpecifier).|2009-06-15T13:45:09 -> 09|
|"t"|První znak označení pro dopoledne/odpoledne.<br /><br /> Další informace: [Vlastní specifikátor formátu "t"](#tSpecifier).|2009-06-15T13:45:30 -> P (cs-US)<br /><br /> 2009-06-15T13:45:30 -> (ja-JP)<br /><br /> 2009-06-15T13:45:30 -> (fr-FR)|
|"tt"|Označení pro dopoledne/odpoledne.<br /><br /> Další informace: [Vlastní specifikátor formátu TT](#ttSpecifier).|2009-06-15T13:45:30 -> PM (cs-US)<br /><br /> 2009-06-15T13:45:30 -> (ja-JP)<br /><br /> 2009-06-15T13:45:30 -> (fr-FR)|
|"y"|Rok, od 0 do 99.<br /><br /> Další informace: [Vlastní specifikátor formátu y](#ySpecifier).|0001-01-01T00:00:00 -> 1<br /><br /> 0900-01-01T00:00:00 -> 0<br /><br /> 1900-01-01T00:00:00 -> 0<br /><br /> 2009-06-15T13:45:30 -> 9<br /><br /> 2019-06-15T13:45:30 -> 19|
|"yy"|Rok, od 00 do 99.<br /><br /> Další informace: [Vlastní specifikátor formátu yy](#yySpecifier).|0001-01-01T00:00:00 -> 01<br /><br /> 0900-01-01T00:00:00 -> 00<br /><br /> 1900-01-01T00:00:00 -> 00<br /><br /> 2019-06-15T13:45:30 -> 19|
|"yyy"|Rok s nejméně třemi číslicemi.<br /><br /> Další informace: [Vlastní specifikátor formátu "yyy"](#yyySpecifier).|0001-01-01T00:00:00 -> 001<br /><br /> 0900-01-01T00:00:00 -> 900<br /><br /> 1900-01-01T00:00:00 -> 1900<br /><br /> 2009-06-15T13:45:30 -> 2009|
|"yyyy"|Rok jako čtyřmístné číslo.<br /><br /> Další informace: [Vlastní specifikátor formátu "yyyy"](#yyyySpecifier).|0001-01-01T00:00:00 -> 0001<br /><br /> 0900-01-01T00:00:00 -> 0900<br /><br /> 1900-01-01T00:00:00 -> 1900<br /><br /> 2009-06-15T13:45:30 -> 2009|
|"yyyyy"|Rok jako pětimístné číslo.<br /><br /> Další informace: [Vlastní specifikátor formátu "yyyyy"](#yyyyySpecifier).|0001-01-01T00:00:00 -> 00001<br /><br /> 2009-06-15T13:45:30 -> 02009|
|"z"|Posun hodin od času UTC, bez počátečních nul.<br /><br /> Další informace: [Vlastní specifikátor formátu "z"](#zSpecifier).|2009-06-15T13:45:30-07:00 -> -7|
|"zz"|Posun hodin od času UTC, s počáteční nulou pro jednocifernou hodnotu.<br /><br /> Další informace: [Vlastní specifikátor formátu zz](#zzSpecifier).|2009-06-15T13:45:30-07:00 -> -07|
|"zzz"|Posun v hodinách a minutách od času UTC.<br /><br /> Další informace: [Vlastní specifikátor formátu "zzz"](#zzzSpecifier).|2009-06-15T13:45:30-07:00 -> -07:00|
|":"|Oddělovač času.<br /><br /> Další informace: [The ":" Custom Format Specifier](#timeSeparator).|2009-06-15T13:45:30 -> : (cs-US)<br /><br /> 2009-06-15T13:45:30 -> . (it-IT)<br /><br /> 2009-06-15T13:45:30 -> : (ja-JP)|
|"/"|Oddělovač data.<br /><br /> Další informace: [Vlastní specifikátor formátu "/"](#dateSeparator).|2009-06-15T13:45:30 -> / (cs-US)<br /><br /> 2009-06-15T13:45:30 -> - (ar-DZ)<br /><br /> 2009-06-15T13:45:30 -> . (tr-TR)|
|"*řetězec*"<br /><br /> '*řetězec*'|Oddělovač řetězcového literálu.<br /><br /> Další informace: [Literály znaků](#Literals).|2009-06-15T13:45:30 ("arr:" h:m t) -> arr: 1:45 P<br /><br /> 2009-06-15T13:45:30 ('arr:' h:m t) -> arr: 1:45 P|
|%|Definuje následující znak jako specifikátor vlastního formátu.<br /><br /> Další informace:[Použití specifikátorů jednoho vlastního formátu](#UsingSingleSpecifiers).|2009-06-15T13:45:30 (%h) -> 1|
|&#92;|Řídicí znak.<br /><br /> Další informace: [Literály znaků](#Literals) a [Použití řídicího znaku](#escape).|2009-06-15T13:45:30 (h \h) -> 1 h|
|Jakýkoli jiný znak|Znak je zkopírován do výsledného řetězce beze změny.<br /><br /> Další informace: [Literály znaků](#Literals).|2009-06-15T01:45:30 (arr hh:mm t) -> arr 01:45 A|

Následující oddíly poskytují další informace o jednotlivých specifikátorech vlastního formátu data a času. Není-li uvedeno jinak, každý specifikátor vytvoří identickou řetězcovou <xref:System.DateTime> reprezentaci <xref:System.DateTimeOffset> bez ohledu na to, zda se používá s hodnotou nebo hodnotou.

## <a name="dSpecifier"></a>Vlastní specifikátor formátu "d"

Specifikátor vlastního formátu "d" představuje den v měsíci jako číslo od 1 do 31. Jednociferné číslo dne je formátováno bez počáteční nuly.

Pokud je specifikátor formátu "d" použit bez jiných vlastních specifikátorů formátu, je interpretován jako standardní specifikátor formátu "d" a času. Další informace o použití jednoho specifikátoru formátu naleznete [v tématu Použití specifikátorů jednoho vlastního formátu](#UsingSingleSpecifiers) dále v tomto článku.

Následující příklad obsahuje specifikátor vlastního formátu "d" v několika řetězcích formátu.

[!code-csharp[Formatting.DateAndTime.Custom#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#1)]
[!code-vb[Formatting.DateAndTime.Custom#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#1)]

[Zpět na stůl](#table)

## <a name="ddSpecifier"></a>Vlastní specifikátor formátu "dd"

Řetězec vlastního formátu "dd" představuje den v měsíci jako číslo od 01 do 31. Jednociferné číslo dne je formátováno s počáteční nulou.

Následující příklad obsahuje specifikátor vlastního formátu "dd" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#2)]
[!code-vb[Formatting.DateAndTime.Custom#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#2)]

[Zpět na stůl](#table)

## <a name="dddSpecifier"></a>Vlastní specifikátor formátu "ddd"

Specifikátor vlastního formátu "ddd" představuje zkrácený název dne v týdnu. Lokalizovaný zkrácený název dne v týdnu je načten <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A?displayProperty=nameWithType> z vlastnosti aktuální nebo zadané jazykové verze.

Následující příklad obsahuje specifikátor vlastního formátu "ddd" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#3)]
[!code-vb[Formatting.DateAndTime.Custom#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#3)]

[Zpět na stůl](#table)

## <a name="ddddSpecifier"></a>Vlastní specifikátor formátu "dddd"

Specifikátor vlastního formátu "dddd" (a libovolný počet dalších specifikátorů "d") představuje úplný název dne v týdnu. Lokalizovaný název dne v týdnu je <xref:System.Globalization.DateTimeFormatInfo.DayNames%2A?displayProperty=nameWithType> načten z vlastnosti aktuální nebo zadané jazykové verze.

Následující příklad obsahuje specifikátor vlastního formátu "dddd" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#4)]
[!code-vb[Formatting.DateAndTime.Custom#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#4)]

[Zpět na stůl](#table)

## <a name="fSpecifier"></a>Vlastní specifikátor formátu "f"

Specifikátor vlastního formátu "f" představuje nejvýznamnější číslici zlomku sekund. Představuje tedy desetiny sekundy v hodnotě data a času.

Pokud je specifikátor formátu "f" použit bez jiných specifikátorů formátu, je interpretován jako standardní specifikátor formátu "f". Další informace o použití jednoho specifikátoru formátu naleznete [v tématu Použití specifikátorů jednoho vlastního formátu](#UsingSingleSpecifiers) dále v tomto článku.

Použijete-li specifikátory formátu "f" jako součást <xref:System.DateTime.ParseExact%2A> <xref:System.DateTime.TryParseExact%2A>formátovacího řetězce dodávaného metodě , , <xref:System.DateTimeOffset.ParseExact%2A>nebo <xref:System.DateTimeOffset.TryParseExact%2A> metodě, označuje počet specifikátorů formátu "f" počet nejvýznamnějších číslic zlomku sekund, který musí být přítomen, aby byl řetězec úspěšně analyzován.

Následující příklad obsahuje specifikátor vlastního formátu "f" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Zpět na stůl](#table)

## <a name="ffSpecifier"></a>Vlastní specifikátor formátu "ff"

Specifikátor vlastního formátu "ff" představuje dvě nejvýznamnější číslice zlomku sekund. Představuje tedy setiny sekundy v hodnotě data a času.

Následující příklad obsahuje specifikátor vlastního formátu "ff" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Zpět na stůl](#table)

## <a name="fffSpecifier"></a>Vlastní specifikátor formátu "fff"

Specifikátor vlastního formátu "fff" představuje tři nejvýznamnější číslice zlomku sekund. Představuje tedy milisekundy v hodnotě data a času.

Následující příklad obsahuje specifikátor vlastního formátu "fff" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Zpět na stůl](#table)

## <a name="ffffSpecifier"></a>Vlastní specifikátor formátu ffff

Specifikátor vlastního formátu "ffff" představuje čtyři nejvýznamnější číslice zlomku sekund. Představuje tedy desetitisíciny sekundy v hodnotě data a času.

I když je možné zobrazit deset tisícin druhé součásti časové hodnoty, tato hodnota nemusí být smysluplná. Přesnost hodnot data a času závisí na rozlišení systémových hodin. V systémech Windows NT verze 3.5 (a vyšší) a Windows Vista je rozlišení hodin přibližně 10–15 milisekund.

[Zpět na stůl](#table)

## <a name="fffffSpecifier"></a>Vlastní specifikátor formátu "fffff"

Specifikátor vlastního formátu "fffff" představuje pět nejvýznamnějších číslic zlomku sekund. Představuje tedy stotisíciny sekundy v hodnotě data a času.

I když je možné zobrazit sto tisícin druhé součásti časové hodnoty, tato hodnota nemusí být smysluplná. Přesnost hodnot data a času závisí na rozlišení systémových hodin. V systémech Windows NT verze 3.5 (a vyšší) a Windows Vista je rozlišení hodin přibližně 10–15 milisekund.

[Zpět na stůl](#table)

## <a name="ffffffSpecifier"></a>Vlastní specifikátor formátu ffffff

Specifikátor vlastního formátu "ffffff" představuje šest nejvýznamnějších číslic zlomku sekund. Představuje tedy miliontiny sekundy v hodnotě data a času.

I když je možné zobrazit miliontiny druhé součásti časové hodnoty, tato hodnota nemusí být smysluplná. Přesnost hodnot data a času závisí na rozlišení systémových hodin. V systémech Windows NT verze 3.5 (a vyšší) a Windows Vista je rozlišení hodin přibližně 10–15 milisekund.

[Zpět na stůl](#table)

## <a name="fffffffSpecifier"></a>Vlastní specifikátor formátu fffffff

Specifikátor vlastního formátu "fffffff" představuje sedm nejvýznamnějších číslic zlomku sekund. Představuje tedy desetimiliontiny sekundy v hodnotě data a času.

I když je možné zobrazit deset milliontin druhé součásti časové hodnoty, tato hodnota nemusí být smysluplná. Přesnost hodnot data a času závisí na rozlišení systémových hodin. V systémech Windows NT verze 3.5 (a vyšší) a Windows Vista je rozlišení hodin přibližně 10–15 milisekund.

[Zpět na stůl](#table)

## <a name="F_Specifier"></a>Vlastní specifikátor formátu "F"

Specifikátor vlastního formátu "F" představuje nejvýznamnější číslici zlomku sekund. Představuje tedy desetiny sekundy v hodnotě data a času. Pokud je číslice nula, nezobrazí se žádná hodnota.

Pokud je specifikátor formátu "F" použit bez jiných specifikátorů formátu, je interpretován jako standardní specifikátor formátu "F" a času. Další informace o použití jednoho specifikátoru formátu naleznete [v tématu Použití specifikátorů jednoho vlastního formátu](#UsingSingleSpecifiers) dále v tomto článku.

Počet specifikátorů formátu "F" <xref:System.DateTime.ParseExact%2A>použitých <xref:System.DateTimeOffset.ParseExact%2A>s <xref:System.DateTimeOffset.TryParseExact%2A> metodou , <xref:System.DateTime.TryParseExact%2A>nebo metodu označuje maximální počet nejvýznamnějších číslic zlomku sekund, který může být přítomen, aby byl řetězec úspěšně analyzovat.

Následující příklad obsahuje specifikátor vlastního formátu "F" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Zpět na stůl](#table)

## <a name="FF_Specifier"></a>Vlastní specifikátor formátu "FF"

Specifikátor vlastního formátu "FF" představuje dvě nejvýznamnější číslice zlomku sekund. Představuje tedy setiny sekundy v hodnotě data a času. Koncové nuly nebo dvě nulové číslice se však nezobrazí.

Následující příklad obsahuje specifikátor vlastního formátu "FF" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Zpět na stůl](#table)

## <a name="FFF_Specifier"></a>Vlastní specifikátor formátu FFF

Specifikátor vlastního formátu "FFF" představuje tři nejvýznamnější číslice zlomku sekund. Představuje tedy milisekundy v hodnotě data a času. Koncové nuly nebo tři nulové číslice se však nezobrazí.

Následující příklad obsahuje specifikátor vlastního formátu "FFF" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Zpět na stůl](#table)

## <a name="FFFF_Specifier"></a>Vlastní specifikátor formátu FFFF

Specifikátor vlastního formátu "FFFF" představuje čtyři nejvýznamnější číslice zlomku sekund. Představuje tedy desetitisíciny sekundy v hodnotě data a času. Koncové nuly nebo čtyři nulové číslice se však nezobrazí.

I když je možné zobrazit deset tisícin druhé součásti časové hodnoty, tato hodnota nemusí být smysluplná. Přesnost hodnot data a času závisí na rozlišení systémových hodin. V systémech Windows NT verze 3.5 (a vyšší) a Windows Vista je rozlišení hodin přibližně 10–15 milisekund.

[Zpět na stůl](#table)

## <a name="FFFFF_Specifier"></a>Vlastní specifikátor formátu FFFFF

Specifikátor vlastního formátu "FFFFF" představuje pět nejvýznamnějších číslic zlomku sekund. Představuje tedy stotisíciny sekundy v hodnotě data a času. Koncové nuly nebo pět nulových číslic se však nezobrazí.

I když je možné zobrazit sto tisícin druhé součásti časové hodnoty, tato hodnota nemusí být smysluplná. Přesnost hodnot data a času závisí na rozlišení systémových hodin. V systémech Windows NT verze 3.5 (a vyšší) a Windows Vista je rozlišení hodin přibližně 10–15 milisekund.

[Zpět na stůl](#table)

## <a name="FFFFFF_Specifier"></a>Vlastní specifikátor formátu FFFFFF

Specifikátor vlastního formátu "FFFFFF" představuje šest nejvýznamnějších číslic zlomku sekund. Představuje tedy miliontiny sekundy v hodnotě data a času. Koncové nuly nebo šest nulových číslic se však nezobrazí.

I když je možné zobrazit miliontiny druhé součásti časové hodnoty, tato hodnota nemusí být smysluplná. Přesnost hodnot data a času závisí na rozlišení systémových hodin. V systémech Windows NT verze 3.5 (a vyšší) a Windows Vista je rozlišení hodin přibližně 10–15 milisekund.

[Zpět na stůl](#table)

## <a name="FFFFFFF_Specifier"></a>Vlastní specifikátor formátu FFFFFFF

Specifikátor vlastního formátu "FFFFFFF" představuje sedm nejvýznamnějších číslic zlomku sekund. Představuje tedy desetimiliontiny sekundy v hodnotě data a času. Koncové nuly nebo sedm nulových číslic se však nezobrazí.

I když je možné zobrazit deset milliontin druhé součásti časové hodnoty, tato hodnota nemusí být smysluplná. Přesnost hodnot data a času závisí na rozlišení systémových hodin. V systémech Windows NT verze 3.5 (a vyšší) a Windows Vista je rozlišení hodin přibližně 10–15 milisekund.

[Zpět na stůl](#table)

## <a name="gSpecifier"></a>Vlastní specifikátor formátu "g" nebo "gg"

Specifikátor vlastního formátu "g" nebo "gg" (plus libovolný počet dalších specifikátorů "g") představuje období nebo éru, jako je například n. l. Operace formátování ignoruje tento specifikátor, pokud datum, které má být formátováno, nemá přidružený řetězec období nebo éry.

Pokud je specifikátor formátu "g" použit bez jiných vlastních specifikátorů formátu, je interpretován jako standardní specifikátor formátu "g". Další informace o použití jednoho specifikátoru formátu naleznete [v tématu Použití specifikátorů jednoho vlastního formátu](#UsingSingleSpecifiers) dále v tomto článku.

Následující příklad obsahuje specifikátor vlastního formátu "g" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#6)]
[!code-vb[Formatting.DateAndTime.Custom#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#6)]

[Zpět na stůl](#table)

## <a name="hSpecifier"></a>Vlastní specifikátor formátu "h"

Specifikátor vlastního formátu "h" představuje hodiny jako číslo od 1 do 12. Hodiny jsou tedy reprezentovány ve 12hodinovém formátu, který počítá celé hodiny od půlnoci nebo od poledne. Konkrétní hodina po půlnoci je nerozeznatelná od stejné hodiny po poledni. Hodiny nejsou zaokrouhleny a jednociferné číslo hodiny je formátováno bez počáteční nuly. Například pro čas 5:43 dopoledne nebo odpoledne tento specifikátor vlastního formátu zobrazí hodnotu "5".

Pokud je specifikátor formátu h použit bez jiných vlastních specifikátorů formátu, je interpretován jako standardní <xref:System.FormatException>specifikátor formátu data a času a vyvolá . Další informace o použití jednoho specifikátoru formátu naleznete [v tématu Použití specifikátorů jednoho vlastního formátu](#UsingSingleSpecifiers) dále v tomto článku.

Následující příklad obsahuje specifikátor vlastního formátu "h" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Zpět na stůl](#table)

## <a name="hhSpecifier"></a>Vlastní specifikátor formátu "hh"

Specifikátor vlastního formátu "hh" (plus libovolný počet dalších specifikátorů "h") představuje hodiny jako čísla od 01 do 12. Představuje tedy hodiny ve 12hodinovém formátu, který počítá celé hodiny od půlnoci nebo od poledne. Konkrétní hodina po půlnoci je nerozeznatelná od stejné hodiny po poledni. Hodiny nejsou zaokrouhleny a jednociferné číslo hodiny je formátováno s počáteční nulou. Například pro čas 5:43 dopoledne nebo odpoledne tento specifikátor formátu zobrazí hodnotu "05".

Následující příklad obsahuje specifikátor vlastního formátu "hh" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Zpět na stůl](#table)

## <a name="H_Specifier"></a>Vlastní specifikátor formátu "H"

Specifikátor vlastního formátu "H" představuje hodiny jako číslo od 0 do 23. Představuje tedy hodiny ve 24hodinovém formátu počítaném od nuly, který počítá celé hodiny od půlnoci. Jednociferné číslo hodiny je formátováno bez počáteční nuly.

Pokud je specifikátor formátu H použit bez jiných vlastních specifikátorů formátu, je interpretován jako standardní <xref:System.FormatException>specifikátor formátu data a času a vyvolá . Další informace o použití jednoho specifikátoru formátu naleznete [v tématu Použití specifikátorů jednoho vlastního formátu](#UsingSingleSpecifiers) dále v tomto článku.

Následující příklad obsahuje specifikátor vlastního formátu "H" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#9](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#9)]
[!code-vb[Formatting.DateAndTime.Custom#9](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#9)]

[Zpět na stůl](#table)

## <a name="HH_Specifier"></a>Vlastní specifikátor formátu "HH"

Specifikátor vlastního formátu "HH" (plus libovolný počet dalších specifikátorů "H") představuje hodiny jako čísla od 00 do 23. Představuje tedy hodiny ve 24hodinovém formátu počítaném od nuly, který počítá celé hodiny od půlnoci. Jednociferné číslo hodiny je formátováno s počáteční nulou.

Následující příklad obsahuje specifikátor vlastního formátu "HH" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#10](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#10)]
[!code-vb[Formatting.DateAndTime.Custom#10](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#10)]

[Zpět na stůl](#table)

## <a name="KSpecifier"></a>Vlastní specifikátor formátu "K"

Specifikátor vlastního formátu "K" představuje informace o časovém pásmu hodnoty data a času. Při použití tohoto specifikátoru formátu s <xref:System.DateTime> hodnotami je výsledný <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> řetězec definován hodnotou vlastnosti:

- Pro místní časové pásmo (hodnota <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> vlastnosti ) je tento specifikátor ekvivalentní specifikátoru "zzz" a vytvoří výsledný řetězec obsahující místní posun od koordinovaného světového <xref:System.DateTimeKind.Local?displayProperty=nameWithType>času (UTC); například "-07:00".

- Pro čas UTC <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> (hodnota <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>vlastnosti ) výsledný řetězec obsahuje znak "Z", který představuje datum UTC.

- Pro čas z neurčené časové pásmo <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> (čas, jehož vlastnost se rovná <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>), výsledek je ekvivalentní <xref:System.String.Empty?displayProperty=nameWithType>.

U <xref:System.DateTimeOffset> hodnot je specifikátor formátu "K" ekvivalentní specifikátoru formátu "zzz" a vytváří <xref:System.DateTimeOffset> výsledný řetězec obsahující posun hodnoty od času UTC.

Pokud je specifikátor formátu "K" použit bez jiných vlastních specifikátorů formátu, je interpretován jako <xref:System.FormatException>standardní specifikátor formátu data a času a vyvolá . Další informace o použití jednoho specifikátoru formátu naleznete [v tématu Použití specifikátorů jednoho vlastního formátu](#UsingSingleSpecifiers) dále v tomto článku.

Následující příklad zobrazí řetězec, který je výsledkem použití vlastního <xref:System.DateTime> specifikátoru formátu "K" s různými a <xref:System.DateTimeOffset> hodnotami v systému v časovém pásmu USA tichomoří.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#12](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#12)]
[!code-vb[Formatting.DateAndTime.Custom#12](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#12)]

[Zpět na stůl](#table)

## <a name="mSpecifier"></a>Vlastní specifikátor formátu "m"

Specifikátor vlastního formátu "m" představuje minuty jako čísla od 0 do 59. Minuta představuje celé minuty, které uplynuly od poslední hodiny. Jednociferné číslo minuty je formátováno bez počáteční nuly.

Pokud je specifikátor formátu "m" použit bez jiných vlastních specifikátorů formátu, je interpretován jako specifikátor formátu "m" standardní ho data a času. Další informace o použití jednoho specifikátoru formátu naleznete [v tématu Použití specifikátorů jednoho vlastního formátu](#UsingSingleSpecifiers) dále v tomto článku.

Následující příklad obsahuje specifikátor vlastního formátu "m" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Zpět na stůl](#table)

## <a name="mmSpecifier"></a>Vlastní specifikátor formátu "mm"

Specifikátor vlastního formátu "mm" (plus libovolný počet dalších specifikátorů "m") představuje minuty jako čísla od 00 do 59. Minuta představuje celé minuty, které uplynuly od poslední hodiny. Jednociferné číslo minut je formátováno s počáteční nulou.

Následující příklad obsahuje specifikátor vlastního formátu "mm" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Zpět na stůl](#table)

## <a name="M_Specifier"></a>Vlastní specifikátor formátu "M"

Specifikátor vlastního formátu "M" představuje měsíc jako číslo od 1 do 12 (nebo od 1 do 13 pro kalendáře, které mají 13 měsíců). Jednociferné číslo měsíce je formátováno bez počáteční nuly.

Pokud je specifikátor formátu "M" použit bez jiných vlastních specifikátorů formátu, je interpretován jako specifikátor formátu "M" standardního data a času. Další informace o použití jednoho specifikátoru formátu naleznete [v tématu Použití specifikátorů jednoho vlastního formátu](#UsingSingleSpecifiers) dále v tomto článku.

Následující příklad obsahuje specifikátor vlastního formátu "M" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#11](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#11)]
[!code-vb[Formatting.DateAndTime.Custom#11](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#11)]

[Zpět na stůl](#table)

## <a name="MM_Specifier"></a>Vlastní specifikátor formátu "MM"

Specifikátor vlastního formátu "MM" představuje měsíc jako číslo od 01 do 12 (nebo od 1 do 13 pro kalendáře, které mají 13 měsíců). Jednociferné číslo měsíce je formátováno s počáteční nulou.

Následující příklad obsahuje specifikátor vlastního formátu "MM" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#2)]
[!code-vb[Formatting.DateAndTime.Custom#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#2)]

[Zpět na stůl](#table)

## <a name="MMM_Specifier"></a>Vlastní specifikátor formátu MMM

Specifikátor vlastního formátu "MMM" představuje zkrácený název měsíce. Lokalizovaný zkrácený název měsíce je načten z <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames%2A?displayProperty=nameWithType> vlastnosti aktuální nebo zadané jazykové verze.

Následující příklad obsahuje specifikátor vlastního formátu "MMM" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#3)]
[!code-vb[Formatting.DateAndTime.Custom#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#3)]

[Zpět na stůl](#table)

## <a name="MMMM_Specifier"></a>Vlastní specifikátor formátu MMMM

Specifikátor vlastního formátu "MMMM" představuje úplný název měsíce. Lokalizovaný název měsíce je načten <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A?displayProperty=nameWithType> z vlastnosti aktuální nebo zadané jazykové verze.

Následující příklad obsahuje specifikátor vlastního formátu "MMMM" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#4)]
[!code-vb[Formatting.DateAndTime.Custom#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#4)]

[Zpět na stůl](#table)

## <a name="sSpecifier"></a>Vlastní specifikátor formátu "s"

Specifikátor vlastního formátu "s" představuje sekundy jako čísla od 0 do 59. Výsledek představuje celé sekundy, které uplynuly od poslední minuty. Jednociferné číslo sekundy je formátováno bez počáteční nuly.

Pokud je specifikátor formátu "s" použit bez jiných vlastních specifikátorů formátu, je interpretován jako specifikátor standardního formátu "s" data a času. Další informace o použití jednoho specifikátoru formátu naleznete [v tématu Použití specifikátorů jednoho vlastního formátu](#UsingSingleSpecifiers) dále v tomto článku.

Následující příklad obsahuje specifikátor vlastního formátu "s" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Zpět na stůl](#table)

## <a name="ssSpecifier"></a>Vlastní specifikátor formátu "ss"

Specifikátor vlastního formátu "ss" (plus libovolný počet dalších specifikátorů "s") představuje sekundy jako čísla od 00 do 59. Výsledek představuje celé sekundy, které uplynuly od poslední minuty. Jednociferné číslo sekundy je formátováno s počáteční nulou.

Následující příklad obsahuje specifikátor vlastního formátu "ss" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Zpět na stůl](#table)

## <a name="tSpecifier"></a>Vlastní specifikátor formátu "t"

Specifikátor vlastního formátu "t" představuje první znak označení dopoledne/odpoledne. Příslušné lokalizované označení je načten <xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A?displayProperty=nameWithType> <xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A?displayProperty=nameWithType> z nebo vlastnost aktuální nebo konkrétní jazykové verze. Označení dopoledne (AM) se používá pro všechny hodnoty času od 0:00:00 (půlnoc) do 11:59:59.999. Označení odpoledne (PM) se používá pro všechny hodnoty času od 12:00:00 (poledne) do 23:59:59.999.

Pokud je specifikátor formátu "t" použit bez jiných vlastních specifikátorů formátu, je interpretován jako standardní specifikátor formátu data a času "t". Další informace o použití jednoho specifikátoru formátu naleznete [v tématu Použití specifikátorů jednoho vlastního formátu](#UsingSingleSpecifiers) dále v tomto článku.

Následující příklad obsahuje specifikátor vlastního formátu "t" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Zpět na stůl](#table)

## <a name="ttSpecifier"></a>Vlastní specifikátor formátu "tt"

Specifikátor vlastního formátu "tt" (plus libovolný počet dalších specifikátorů "t") představuje celé označení dopoledne/odpoledne. Příslušné lokalizované označení je načten <xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A?displayProperty=nameWithType> <xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A?displayProperty=nameWithType> z nebo vlastnost aktuální nebo konkrétní jazykové verze. Označení dopoledne (AM) se používá pro všechny hodnoty času od 0:00:00 (půlnoc) do 11:59:59.999. Označení odpoledne (PM) se používá pro všechny hodnoty času od 12:00:00 (poledne) do 23:59:59.999.

Ujistěte se, že používáte specifikátor "tt" pro jazyky, pro které je nutné zachovat rozdíl mezi AM a PM. Pro ukázku je uvedena japonština, pro kterou se liší určení dopoledne a odpoledne (AM a PM) v druhém znaku namísto prvního znaku.

Následující příklad obsahuje specifikátor vlastního formátu "tt" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Zpět na stůl](#table)

## <a name="ySpecifier"></a>Vlastní specifikátor formátu "y"

Specifikátor vlastního formátu "y" představuje rok jako jednociferné nebo dvouciferné číslo. Pokud rok obsahuje více než dvě číslice, zobrazí se ve výsledku pouze dvě číslice nižšího řádu. Pokud první číslice dvoumístného čísla roku začíná nulou (například 2008), je číslo formátováno bez počáteční nuly.

Pokud je specifikátor formátu y použit bez jiných vlastních specifikátorů formátu, je interpretován jako standardní specifikátor formátu "y". Další informace o použití jednoho specifikátoru formátu naleznete [v tématu Použití specifikátorů jednoho vlastního formátu](#UsingSingleSpecifiers) dále v tomto článku.

Následující příklad obsahuje specifikátor vlastního formátu "y" v řetězci vlastního formátu.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Zpět na stůl](#table)

## <a name="yySpecifier"></a>Vlastní specifikátor formátu "yy"

Specifikátor vlastního formátu "yy" představuje rok jako dvouciferné číslo. Pokud rok obsahuje více než dvě číslice, zobrazí se ve výsledku pouze dvě číslice nižšího řádu. Pokud má dvoumístný rok méně než dvě platné číslice, je číslo doplněno počátečními nulami za účelem vytvoření dvouciferného čísla.

V operaci analýzy dvoumístný rok, který je analyzován pomocí specifikátoru vlastního formátu "yy", je interpretován na základě <xref:System.Globalization.Calendar.TwoDigitYearMax%2A?displayProperty=nameWithType> vlastnosti aktuálního kalendáře poskytovatele formátu. Následující příklad analyzuje řetězcovou reprezentaci data s rokem vyjádřeným dvěma číslicemi pomocí výchozího gregoriánského kalendáře jazykové verze en_US, což v tomto případě představuje aktuální jazykovou verzi. Potom změní aktuální jazykovou <xref:System.Globalization.CultureInfo> verzi objektu použít objekt, <xref:System.Globalization.GregorianCalendar> jehož <xref:System.Globalization.GregorianCalendar.TwoDigitYearMax%2A> vlastnost byla změněna.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#19](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/parseexact2digityear1.cs#19)]
[!code-vb[Formatting.DateAndTime.Custom#19](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/parseexact2digityear1.vb#19)]

Následující příklad obsahuje specifikátor vlastního formátu "yy" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Zpět na stůl](#table)

## <a name="yyySpecifier"></a>Vlastní specifikátor formátu "yyy"

Specifikátor vlastního formátu "yyy" představuje rok nejméně se třemi číslicemi. Pokud rok obsahuje více než tři platné číslice, budou obsaženy ve výsledném řetězci. Pokud má rok méně než tři číslice, je číslo doplněno počátečními nulami tak, aby bylo vytvořeno trojciferné číslo.

> [!NOTE]
> Pro thajský buddhistický kalendář, který může mít pět číslic roku, zobrazí tento specifikátor formátu všechny platné číslice.

Následující příklad obsahuje specifikátor vlastního formátu "yyy" v řetězci vlastního formátu.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Zpět na stůl](#table)

## <a name="yyyySpecifier"></a>Vlastní specifikátor formátu "yyyy"

Specifikátor vlastního formátu "yyyy" představuje rok nejméně se čtyřmi číslicemi. Pokud rok obsahuje více než čtyři platné číslice, budou obsaženy ve výsledném řetězci. Pokud má rok méně než čtyři číslice, je číslo doplněno počátečními nulami tak, aby bylo vytvořeno čtyřciferné číslo.

> [!NOTE]
> Pro thajský buddhistický kalendář, který může mít pět číslic roku, zobrazí tento specifikátor formátu minimálně čtyři číslice.

Následující příklad obsahuje specifikátor vlastního formátu "yyyy" v řetězci vlastního formátu.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Zpět na stůl](#table)

## <a name="yyyyySpecifier"></a>Vlastní specifikátor formátu "yyyyy"

Specifikátor vlastního formátu "yyyyy" (plus libovolný počet dalších specifikátorů "y") představuje rok nejméně s pěti číslicemi. Pokud rok obsahuje více než pět platných číslic, budou obsaženy ve výsledném řetězci. Pokud má rok méně než pět číslic, je číslo doplněno počátečními nulami tak, aby bylo vytvořeno pěticiferné číslo.

Pokud existují další specifikátory "y", je číslo doplněno tolika počátečními nulami, kolik je třeba pro vytvoření čísla podle specifikátorů "y".

Následující příklad obsahuje specifikátor vlastního formátu "yyyyy" v řetězci vlastního formátu.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Zpět na stůl](#table)

## <a name="zSpecifier"></a>Vlastní specifikátor formátu "z"

S <xref:System.DateTime> hodnotami vlastní specifikátor formátu "z" představuje podepsaný posun časového pásma místního operačního systému od koordinovaného světového času (UTC), měřeno v hodinách. Neodráží hodnotu <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> vlastnosti instance. Z tohoto důvodu se specifikátor formátu "z" <xref:System.DateTime> nedoporučuje používat s hodnotami.

U <xref:System.DateTimeOffset> hodnot představuje tento specifikátor formátu posun <xref:System.DateTimeOffset> hodnoty od času UTC v hodinách.

Posun je vždy zobrazen s počátečním znaménkem. Znaménko plus (+) označuje hodiny před časem UTC a symbol mínus (-) označuje hodiny za časem UTC. Jednociferné číslo posunu je formátováno bez počáteční nuly.

Pokud je specifikátor formátu "z" použit bez jiných vlastních specifikátorů formátu, je interpretován jako <xref:System.FormatException>standardní specifikátor formátu data a času a vyvolá . Další informace o použití jednoho specifikátoru formátu naleznete [v tématu Použití specifikátorů jednoho vlastního formátu](#UsingSingleSpecifiers) dále v tomto článku.

Následující příklad obsahuje specifikátor vlastního formátu "z" v řetězci vlastního formátu.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
[!code-vb[Formatting.DateAndTime.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]

[Zpět na stůl](#table)

## <a name="zzSpecifier"></a>Vlastní specifikátor formátu "zz"

S <xref:System.DateTime> hodnotami vlastní specifikátor formátu "zz" představuje podepsaný posun časového pásma místního operačního systému od Času UTC, měřeno v hodinách. Neodráží hodnotu <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> vlastnosti instance. Z tohoto důvodu se specifikátor formátu "zz" <xref:System.DateTime> nedoporučuje používat s hodnotami.

U <xref:System.DateTimeOffset> hodnot představuje tento specifikátor formátu posun <xref:System.DateTimeOffset> hodnoty od času UTC v hodinách.

Posun je vždy zobrazen s počátečním znaménkem. Znaménko plus (+) označuje hodiny před časem UTC a symbol mínus (-) označuje hodiny za časem UTC. Jednociferné číslo posunu je formátováno s počáteční nulou.

Následující příklad obsahuje specifikátor vlastního formátu "zz" v řetězci vlastního formátu.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
[!code-vb[Formatting.DateAndTime.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]

[Zpět na stůl](#table)

## <a name="zzzSpecifier"></a>Vlastní specifikátor formátu "zzz"

S <xref:System.DateTime> hodnotami vlastní specifikátor formátu "zzz" představuje podepsaný posun časového pásma místního operačního systému od Času UTC, měřeno v hodinách a minutách. Neodráží hodnotu <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> vlastnosti instance. Z tohoto důvodu se pro použití s <xref:System.DateTime> hodnotami nedoporučuje specifikátor formátu zzz.

U <xref:System.DateTimeOffset> hodnot představuje tento specifikátor formátu posun <xref:System.DateTimeOffset> hodnoty od času UTC v hodinách a minutách.

Posun je vždy zobrazen s počátečním znaménkem. Znaménko plus (+) označuje hodiny před časem UTC a symbol mínus (-) označuje hodiny za časem UTC. Jednociferné číslo posunu je formátováno s počáteční nulou.

Následující příklad obsahuje specifikátor vlastního formátu "zzz" ve vlastním řetězci formátu.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
[!code-vb[Formatting.DateAndTime.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]

[Zpět na stůl](#table)

## <a name="timeSeparator"></a>Specifikátor vlastního formátu ":"
Specifikátor vlastního formátu ":" představuje oddělovač času, který se používá k rozlišení hodin, minut a sekund. Příslušný lokalizovaný oddělovač času <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A?displayProperty=nameWithType> je načten z vlastnosti aktuální nebo zadané jazykové verze.

> [!NOTE]
> Chcete-li změnit oddělovač času pro určitý řetězec data a času, zadejte znak oddělovače v oddělovači literálu. Například vlastní formátovací `hh'_'dd'_'ss` řetězec vytvoří výsledný řetězec, ve kterém "\_" (podtržítko) se vždy používá jako oddělovač času. Chcete-li změnit oddělovač času pro všechna data pro <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A?displayProperty=nameWithType> jazykovou verzi, změňte hodnotu <xref:System.Globalization.DateTimeFormatInfo> vlastnosti aktuální jazykové <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A> verze nebo vytvořte instanci objektu, <xref:System.IFormatProvider> přiřaďte znak jeho vlastnosti a zavolejte přetížení metody formátování, která obsahuje parametr.

Pokud je specifikátor formátu ":"použit bez jiných vlastních specifikátorů formátu, je interpretován jako standardní <xref:System.FormatException>specifikátor formátu data a času a vyvolá . Další informace o použití jednoho specifikátoru formátu naleznete [v tématu Použití specifikátorů jednoho vlastního formátu](#UsingSingleSpecifiers) dále v tomto článku.

[Zpět na stůl](#table)

## <a name="dateSeparator"></a>Vlastní specifikátor formátu "/"

Specifikátor vlastního formátu "/" představuje oddělovač dat, který se používá k rozlišení roků, měsíců a dnů. Příslušný lokalizovaný oddělovač data <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A?displayProperty=nameWithType> je načten z vlastnosti aktuální nebo zadané jazykové verze.

> [!NOTE]
> Chcete-li změnit oddělovač data pro určitý řetězec data a času, zadejte znak oddělovače v oddělovači literálu. Například vlastní formátovací `mm'/'dd'/'yyyy` řetězec vytvoří výsledný řetězec, ve kterém "/" se vždy používá jako oddělovač data. Chcete-li změnit oddělovač kalendářních dat pro všechna <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A?displayProperty=nameWithType> data pro jazykovou verzi, změňte <xref:System.Globalization.DateTimeFormatInfo> hodnotu vlastnosti <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A> aktuální jazykové verze nebo vytvořte instanci <xref:System.IFormatProvider> objektu, přiřaďte znak jeho vlastnosti a zavolejte přetížení metody formátování, která obsahuje parametr.

Pokud je specifikátor formátu "/" použit bez jiných vlastních specifikátorů formátu, je interpretován jako <xref:System.FormatException>standardní specifikátor formátu data a času a vyvolá . Další informace o použití jednoho specifikátoru formátu naleznete [v tématu Použití specifikátorů jednoho vlastního formátu](#UsingSingleSpecifiers) dále v tomto článku.

[Zpět na stůl](#table)

## <a name="Literals"></a>Literály znaků

Následující znaky ve vlastním řetězci formátu data a času jsou vyhrazeny a jsou vždy interpretovány jako formátovací znaky nebo v případě ", ', /, a \\, jako speciální znaky.

||||||
|-|-|-|-|-|
|F|H|K|M|d|
|f|g|h|m|s|
|t|y|z|%|:|
|/|"|'|&#92;||

Všechny ostatní znaky jsou vždy interpretovány jako literály znaků a v operaci formátování jsou zahrnuty do výsledného řetězce beze změny.  V operaci analýzy musí přesně odpovídat znakům ve vstupním řetězci; porovnání se rozlišuje malá a velká písmena.

Následující příklad obsahuje literálové znaky "PST" (pro tichomořský standardní čas) a "PDT" (pro tichomořský letní čas) představující místní časové pásmo ve formátu řetězce. Všimněte si, že řetězec je součástí výsledkového řetězce a že řetězec, který obsahuje řetězec místního časového pásma také analyzuje úspěšně.

[!code-csharp[Formatting.DateAndTime.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx1.cs#20)]
[!code-vb[Formatting.DateAndTime.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx1.vb#20)]

Existují dva způsoby, jak označit, že znaky mají být interpretovány jako literálové znaky a nikoli jako rezervní znaky, aby mohly být zahrnuty do výsledného řetězce nebo úspěšně analyzovány ve vstupním řetězci:

- Tím, že unikne každý vyhrazený znak. Další informace naleznete [v tématu Použití řídicího znaku](#escape).

Následující příklad obsahuje literál znaky "pst" (pro tichomořský standardní čas) představující místní časové pásmo ve formátu řetězce. Vzhledem k tomu, že "s" a "t" jsou řetězce vlastního formátu, musí být oba znaky uvozeny, aby byly interpretovány jako literály znaků.

[!code-csharp[Formatting.DateAndTime.Custom#21](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx2.cs#21)]
[!code-vb[Formatting.DateAndTime.Custom#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx2.vb#21)]

- Uzavřením celého řetězce literálu do uvozovek nebo apostrofů. Následující příklad je jako předchozí, s tím rozdílem, že "pst" je uzavřen v uvozovkách, což znamená, že celý řetězec oddělených by měl být interpretován jako literály znaků.

[!code-csharp[Formatting.DateAndTime.Custom#22](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx3.cs#22)]
[!code-vb[Formatting.DateAndTime.Custom#22](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx3.vb#22)]

## <a name="notes"></a>Poznámky

### <a name="UsingSingleSpecifiers"></a>Použití jednotlivých vlastních specifikátorů formátu

Řetězec vlastního formátu data a času se skládá ze dvou nebo několika znaků. Metody formátování data a času interpretují jakýkoli řetězec s jediným znakem jako řetězec standardního formátu data a času. Pokud nerozpoznají znak jako platný specifikátor formátu, <xref:System.FormatException>hodí . Například řetězec formátu, který se skládá pouze ze specifikátoru "h", je interpretován jako řetězec standardního formátu data a času. V tomto konkrétním případě je však vyvolána výjimka, protože neexistuje žádný standardní specifikátor data a časového formátu "h".

Chcete-li použít kterýkoli ze specifikátorů vlastního formátu data a času jako jediný specifikátor v řetězci formátu (to znamená, že chcete použít samotné specifikátory formátu "d", "f", "F", "g", "h", "H", "K", "m", "M", "s", "t", "y", "z", ":" nebo "/"), vložte před nebo za specifikátor mezeru, nebo vložte před jednoduchý specifikátor vlastního formátu specifikátor formátu procento %.

Například "`%h"` je interpretován jako vlastní řetězec formátu data a času, který zobrazuje hodinu reprezentovanou aktuální hodnotou data a času. Můžete také použít řetězec formátu " h" nebo "h ", ačkoli tato hodnota vloží ve výsledném řetězci vedle hodin mezeru. Následující příklad znázorňuje tyto tři řetězce formátu.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#16](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/literal1.cs#16)]
[!code-vb[Formatting.DateAndTime.Custom#16](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/literal1.vb#16)]

### <a name="escape"></a>Použití řídicího znaku

Znaky "d", "f", "F", "g", "h", "H", "K", "m", "M", "s", "t", "y", "z", ":", nebo "/" v řetězci formátu jsou interpretovány jako specifikátory vlastního formátu, nikoli jako literální znaky. Chcete-li zabránit tomu, aby byl znak interpretován jako specifikátor formátu,\\můžete mu předcházet zpětným lomítkem ( ), což je řídicí znak. Řídicí znak označuje, že následující znak je literální znak, který by měl být zařazen do výsledného řetězce beze změny.

Chcete-li zahrnout zpětné lomítko do výsledného řetězce,`\\`musíte jej uniknout s jiným zpětným lomítkem ( ).

> [!NOTE]
> Některé kompilátory, jako jsou například kompilátory jazyka C++ a jazyka C#, mohou také interpretovat jedno zpětné lomítko jako řídicí znak. Abyste se ujistili, zda je řetězec interpretován při formátování správně, můžete v jazyce C# použít literální řetězcový znak verbatim (znak @) před řetězcem, nebo v jazyce C# a C++ přidat další znak zpětného lomítka před každé zpětné lomítko. Následující příklad jazyka C# ukazuje oba přístupy.

Následující příklad používá řídicí znak, aby zamezil operacím formátování v interpretaci znaků "h" a "m" jako specifikátorů formátu.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#15](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/escape1.cs#15)]
[!code-vb[Formatting.DateAndTime.Custom#15](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/escape1.vb#15)]

### <a name="control-panel-settings"></a>Nastavení Ovládacích panelů

Nastavení **Místní a jazykové možnosti** v Ovládacích panelech ovlivňuje výsledný řetězec vytvořený operací formátování, která zahrnuje mnoho vlastních specifikátorů formátu data a času. Tato nastavení slouží k inicializaci objektu <xref:System.Globalization.DateTimeFormatInfo> přidruženého k aktuální jazykové verzi vlákna, který poskytuje hodnoty používané k řízení formátování. Počítače, které používají různá nastavení, generují různé výsledné řetězce.

Kromě toho pokud <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> použijete konstruktor k vytvoření <xref:System.Globalization.CultureInfo> instance nového objektu, který představuje stejnou jazykovou verzi jako aktuální jazyková verze systému, <xref:System.Globalization.CultureInfo> budou na nový objekt použita všechna vlastní nastavení vytvořená položkou **Místní a jazykové možnosti** v Ovládacích panelech. Pomocí konstruktoru <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> <xref:System.Globalization.CultureInfo> můžete vytvořit objekt, který neodráží vlastní nastavení systému.

### <a name="datetimeformatinfo-properties"></a>Vlastnosti DateTimeFormatInfo

Formátování je ovlivněno vlastnostmi aktuálního <xref:System.Globalization.DateTimeFormatInfo> objektu, který je implicitně poskytován aktuální <xref:System.IFormatProvider> jazykovou verzí vlákna nebo explicitně parametrem metody, která vyvolá formátování. Pro <xref:System.IFormatProvider> parametr byste měli <xref:System.Globalization.CultureInfo> zadat objekt, který představuje <xref:System.Globalization.DateTimeFormatInfo> jazykovou verzi, nebo objekt.

Výsledný řetězec vytvořený mnoha vlastními specifikátory formátu data a času <xref:System.Globalization.DateTimeFormatInfo> také závisí na vlastnostech aktuálního objektu. Aplikace může změnit výsledek vytvořený některými vlastními specifikátory <xref:System.Globalization.DateTimeFormatInfo> formátu data a času změnou odpovídající vlastnosti. Například specifikátor formátu "ddd" přidá ke výslednému řetězci zkrácený název dne v týdnu nalezený v řetězcovém <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A> poli. Podobně specifikátor formátu MMMM přidá do výsledného řetězce <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A> úplný název měsíce nalezený v řetězci řetězce.

## <a name="see-also"></a>Viz také

- <xref:System.DateTime?displayProperty=nameWithType>
- <xref:System.IFormatProvider?displayProperty=nameWithType>
- [Typy formátování](../../../docs/standard/base-types/formatting-types.md)
- [Standardní řetězce formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [Ukázka: Nástroj pro formátování WinForms .NET (C#)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs)
- [Ukázka: Nástroj pro formátování WinForms .NET (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb)
