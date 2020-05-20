---
title: Vlastní řetězce formátu data a času
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
ms.openlocfilehash: ae2711aac8bd864e623efe18e698c8de75a3ac32
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83440990"
---
# <a name="custom-date-and-time-format-strings"></a>Vlastní řetězce formátu data a času

Formátovací řetězec data a času definuje textovou reprezentaci <xref:System.DateTime> <xref:System.DateTimeOffset> hodnoty nebo, která je výsledkem operace formátování. Může také definovat reprezentaci hodnoty data a času nezbytnou v rámci operace analýzy a úspěšně tak řetězec převést na datum a čas. Řetězec vlastního formátu se skládá z jednoho nebo více vlastních specifikátorů formátu data a času. Libovolný řetězec, který není [standardním řetězcem formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) , je interpretován jako řetězec vlastního formátu data a času.

> [!TIP]
> Můžete si stáhnout **formátovací nástroj**, aplikaci .net Core model Windows Forms, která umožňuje použití řetězců formátu na číselné hodnoty nebo hodnoty data a času a zobrazuje výsledný řetězec. Zdrojový kód je k dispozici pro [C#](https://docs.microsoft.com/samples/dotnet/samples/windowsforms-formatting-utility-cs) a [Visual Basic](https://docs.microsoft.com/samples/dotnet/samples/windowsforms-formatting-utility-vb).

Vlastní řetězce formátu data a času lze použít s hodnotami i <xref:System.DateTime> <xref:System.DateTimeOffset> .

[!INCLUDE[C# interactive-note](~/includes/csharp-interactive-with-utc-partial-note.md)]

<a name="table"></a>V operacích formátování lze použít vlastní formátovací řetězce data a času buď s `ToString` metodou instance data a času, nebo s metodou, která podporuje složené formátování. Následující příklad znázorňuje oba způsoby použití.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#17](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/custandformatting1.cs#17)]
[!code-vb[Formatting.DateAndTime.Custom#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/custandformatting1.vb#17)]

Při analýze operací lze použít vlastní formátovací řetězce data a času s <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> metodami,, a <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> . Tyto metody vyžadují, aby byl vstupní řetězec přesně na konkrétní vzor, aby operace analýzy proběhla úspěšně. Následující příklad ukazuje volání <xref:System.DateTimeOffset.ParseExact%28System.String%2CSystem.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody k analýze data, které musí zahrnovat den, měsíc a rok se dvěma číslicemi.

[!code-csharp[Formatting.DateAndTime.Custom#18](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/custandparsing1.cs#18)]
[!code-vb[Formatting.DateAndTime.Custom#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/custandparsing1.vb#18)]

Následující tabulka popisuje specifikátory vlastního formátu data a času a zobrazuje výsledný řetězec, který je vytvořen jednotlivými specifikátory formátu. Ve výchozím nastavení odráží výsledný řetězec konvence formátování jazykové verze en-US. Pokud konkrétní specifikátor formátu vytváří lokalizovaný výsledný řetězec, je v příkladu rovněž uvedena jazyková verze, na kterou se výsledný řetězec vztahuje. Další informace o použití vlastních formátovacích řetězců data a času naleznete v části [poznámky](#notes) .

| Specifikátor formátu | Popis | Příklady |
| ---------------------- | ----------------- | -------------- |
|"d"|Den měsíce, od 1 do 31.<br /><br /> Další informace: [Specifikátor vlastního formátu "d"](#dSpecifier).|2009-06-01T13:45:30-> 1<br /><br /> 2009-06-15T13:45:30 – > 15|
|"dd"|Den měsíce, od 01 do 31.<br /><br /> Další informace: [Specifikátor vlastního formátu "dd"](#ddSpecifier).|2009-06-01T13:45:30 – > 01<br /><br /> 2009-06-15T13:45:30 – > 15|
|"ddd"|Zkrácený název dne v týdnu.<br /><br /> Další informace: [Specifikátor vlastního formátu "ddd"](#dddSpecifier).|2009-06-15T13:45:30-> Mon (EN-US)<br /><br /> 2009-06-15T13:45:30-> Пн (ru-RU)<br /><br /> 2009-06-15T13:45:30-> LUN. (fr-FR)|
|"dddd"|Úplný název dne v týdnu.<br /><br /> Další informace: [specifikátor "dddd" vlastního formátu](#ddddSpecifier).|2009-06-15T13:45:30-> pondělí (EN-US)<br /><br /> 2009-06-15T13:45:30-> понедельник (ru-RU)<br /><br /> 2009-06-15T13:45:30-> Lundi (fr-FR)|
|"f"|Desetiny sekundy v hodnotě data a času.<br /><br /> Další informace: [specifikátor "f" vlastního formátu](#fSpecifier).|2009-06-15T13:45:30.6170000-> 6<br /><br /> 2009-06-15T13:45:30.05-> 0|
|"ff"|Setiny sekundy v hodnotě data a času.<br /><br /> Další informace: [specifikátor "FF" vlastního formátu](#ffSpecifier).|2009-06-15T13:45:30.6170000-> 61<br /><br /> 2009-06-15T13:45:30.0050000-> 00|
|"fff"|Milisekundy v hodnotě data a času.<br /><br /> Další informace: [specifikátor "fff" vlastního formátu](#fffSpecifier).|6/15/2009 13:45:30.617-> 617<br /><br /> 6/15/2009 13:45:30.0005-> 000|
|"ffff"|Desetitisíciny sekundy v hodnotě data a času.<br /><br /> Další informace: [Specifikátor vlastního formátu "FFFF"](#ffffSpecifier).|2009-06-15T13:45:30.6175000-> 6175<br /><br /> 2009-06-15T13:45:30.0000500-> 0000|
|"fffff"|Stotisíciny sekundy v hodnotě data a času.<br /><br /> Další informace: [Specifikátor vlastního formátu "fffff"](#fffffSpecifier).|2009-06-15T13:45:30.6175400-> 61754<br /><br /> 6/15/2009 13:45:30.000005-> 00000|
|"ffffff"|Miliontiny sekundy v hodnotě data a času.<br /><br /> Další informace: [Specifikátor vlastního formátu "FFFFFF"](#ffffffSpecifier).|2009-06-15T13:45:30.6175420-> 617542<br /><br /> 2009-06-15T13:45:30.0000005-> 000000|
|"fffffff"|Desetimiliontiny sekundy v hodnotě data a času.<br /><br /> Další informace: [Specifikátor vlastního formátu "fffffff"](#fffffffSpecifier).|2009-06-15T13:45:30.6175425-> 6175425<br /><br /> 2009-06-15T13:45:30.0001150-> 0001150|
|"F"|Pokud je hodnota nenulová, jedná se o desetiny sekundy v hodnotě data a času.<br /><br /> Další informace: [specifikátor "F" vlastního formátu](#F_Specifier).|2009-06-15T13:45:30.6170000-> 6<br /><br /> 2009-06-15T13:45:30.0500000-> (žádný výstup)|
|"FF"|Pokud je hodnota nenulová, jedná se o setiny sekundy v hodnotě data a času.<br /><br /> Další informace: [specifikátor "FF" vlastního formátu](#FF_Specifier).|2009-06-15T13:45:30.6170000-> 61<br /><br /> 2009-06-15T13:45:30.0050000-> (žádný výstup)|
|"FFF"|Pokud je hodnota nenulová, jedná se o milisekundy v hodnotě data a času.<br /><br /> Další informace: [specifikátor "fff" vlastního formátu](#FFF_Specifier).|2009-06-15T13:45:30.6170000-> 617<br /><br /> 2009-06-15T13:45:30.0005000-> (žádný výstup)|
|"FFFF"|Pokud je hodnota nenulová, jedná se o desetitisíciny sekundy v hodnotě data a času.<br /><br /> Další informace: [Specifikátor vlastního formátu "FFFF"](#FFFF_Specifier).|2009-06-15T13:45:30.5275000-> 5275<br /><br /> 2009-06-15T13:45:30.0000500-> (žádný výstup)|
|"FFFFF"|Pokud je hodnota nenulová, jedná se o stotisíciny sekundy v hodnotě data a času.<br /><br /> Další informace: [Specifikátor vlastního formátu "fffff"](#FFFFF_Specifier).|2009-06-15T13:45:30.6175400-> 61754<br /><br /> 2009-06-15T13:45:30.0000050-> (žádný výstup)|
|"FFFFFF"|Pokud je hodnota nenulová, jedná se o miliontiny sekundy v hodnotě data a času.<br /><br /> Další informace: [Specifikátor vlastního formátu "FFFFFF"](#FFFFFF_Specifier).|2009-06-15T13:45:30.6175420-> 617542<br /><br /> 2009-06-15T13:45:30.0000005-> (žádný výstup)|
|"FFFFFFF"|Pokud je hodnota nenulová, jedná se o desetimiliontiny sekundy v hodnotě data a času.<br /><br /> Další informace: [Specifikátor vlastního formátu "fffffff"](#FFFFFFF_Specifier).|2009-06-15T13:45:30.6175425-> 6175425<br /><br /> 2009-06-15T13:45:30.0001150-> 000115|
|"g", "gg"|Období nebo éra.<br /><br /> Další informace: [Specifikátor vlastního formátu "g" nebo "GG"](#gSpecifier).|2009-06-15T13:45:30.6170000-> N.L.|
|"h"|Hodiny ve 12hodinovém formátu, od 1 do 12.<br /><br /> Další informace: [specifikátor "h" vlastního formátu](#hSpecifier).|2009-06-15T01:45:30-> 1<br /><br /> 2009-06-15T13:45:30-> 1|
|"hh"|Hodiny ve 12hodinovém formátu, od 01 do 12.<br /><br /> Další informace: [specifikátor "HH" vlastního formátu](#hhSpecifier).|2009-06-15T01:45:30 – > 01<br /><br /> 2009-06-15T13:45:30 – > 01|
|"H"|Hodiny ve 24hodinovém formátu, od 0 do 23.<br /><br /> Další informace: [specifikátor "H" vlastního formátu](#H_Specifier).|2009-06-15T01:45:30-> 1<br /><br /> 2009-06-15T13:45:30 – > 13|
|"HH"|Hodiny ve 24hodinovém formátu, od 00 do 23.<br /><br /> Další informace: [specifikátor "HH" vlastního formátu](#HH_Specifier).|2009-06-15T01:45:30 – > 01<br /><br /> 2009-06-15T13:45:30 – > 13|
|"K"|Informace o časovém pásmu.<br /><br /> Další informace: [Specifikátor vlastního formátu "K"](#KSpecifier).|S <xref:System.DateTime> hodnotami:<br /><br /> 2009-06-15T13:45:30, neurčený druh – ><br /><br /> 2009-06-15T13:45:30, druh UTC-> Z<br /><br /> 2009-06-15T13:45:30, druh Local->-07:00 (závisí na nastavení místního počítače)<br /><br /> S <xref:System.DateTimeOffset> hodnotami:<br /><br /> 2009-06-15T01:45:30.07:00-->-07:00<br /><br /> 2009-06-15T08:45:30 + 00:00--> + 00:00|
|"m"|Minuty, od 0 do 59.<br /><br /> Další informace: [Specifikátor vlastního formátu "m"](#mSpecifier).|2009-06-15T01:09:30 – > 9<br /><br /> 2009-06-15T13:29:30-> 29|
|"mm"|Minuty, od 00 do 59.<br /><br /> Další informace: [specifikátor "mm" vlastního formátu](#mmSpecifier).|2009-06-15T01:09:30-> 09<br /><br /> 2009-06-15T01:45:30 – > 45|
|"M"|Měsíc, od 1 do 12.<br /><br /> Další informace: [Specifikátor vlastního formátu "M"](#M_Specifier).|2009-06-15T13:45:30 – > 6|
|"MM"|Měsíc, od 01 do 12.<br /><br /> Další informace: [specifikátor "mm" vlastního formátu](#MM_Specifier).|2009-06-15T13:45:30-> 06|
|"MMM"|Zkrácený název měsíce.<br /><br /> Další informace: [Specifikátor vlastního formátu "MMM"](#MMM_Specifier).|2009-06-15T13:45:30. >. června (EN-US)<br /><br /> 2009-06-15T13:45:30-> juin (fr-FR)<br /><br /> 2009-06-15T13:45:30-> června (zu-ZA)|
|"MMMM"|Úplný název měsíce.<br /><br /> Další informace: [Specifikátor vlastního formátu "MMMM"](#MMMM_Specifier).|2009-06-15T13:45:30-> června (EN-US)<br /><br /> 2009-06-15T13:45:30-> Juni (da-DK)<br /><br /> 2009-06-15T13:45:30-> uJuni (zu-ZA)|
|"s"|Sekundy, od 0 do 59.<br /><br /> Další informace: [Specifikátor vlastního formátu "s"](#sSpecifier).|2009-06-15T13:45:09-> 9|
|"ss"|Sekundy, od 00 do 59.<br /><br /> Další informace: [Specifikátor vlastního formátu "SS"](#ssSpecifier).|2009-06-15T13:45:09-> 09|
|"t"|První znak označení pro dopoledne/odpoledne.<br /><br /> Další informace: [Specifikátor vlastního formátu "t"](#tSpecifier).|2009-06-15T13:45:30-> P (EN-US)<br /><br /> 2009-06-15T13:45:30-> 午 (ja-JP)<br /><br /> 2009-06-15T13:45:30-> (fr-FR)|
|"tt"|Označení pro dopoledne/odpoledne.<br /><br /> Další informace: [Specifikátor vlastního formátu "tt"](#ttSpecifier).|2009-06-15T13:45:30-> ODP. (EN-US)<br /><br /> 2009-06-15T13:45:30-> 午後 (ja-JP)<br /><br /> 2009-06-15T13:45:30-> (fr-FR)|
|"y"|Rok, od 0 do 99.<br /><br /> Další informace: [Specifikátor vlastního formátu "y"](#ySpecifier).|0001-01-01T00:00:00-> 1<br /><br /> 0900-01-01T00:00:00-> 0<br /><br /> 1900-01-01T00:00:00-> 0<br /><br /> 2009-06-15T13:45:30 – > 9<br /><br /> 2019-06-15T13:45:30 – > 19|
|"yy"|Rok, od 00 do 99.<br /><br /> Další informace: [Specifikátor vlastního formátu "yy"](#yySpecifier).|0001-01-01T00:00:00-> 01<br /><br /> 0900-01-01T00:00:00-> 00<br /><br /> 1900-01-01T00:00:00-> 00<br /><br /> 2019-06-15T13:45:30 – > 19|
|"yyy"|Rok s nejméně třemi číslicemi.<br /><br /> Další informace: [Specifikátor vlastního formátu "yyy"](#yyySpecifier).|0001-01-01T00:00:00-> 001<br /><br /> 0900-01-01T00:00:00-> 900<br /><br /> 1900-01-01T00:00:00-> 1900<br /><br /> 2009-06-15T13:45:30 – > 2009|
|"yyyy"|Rok jako čtyřmístné číslo.<br /><br /> Další informace: [Specifikátor vlastního formátu "rrrr"](#yyyySpecifier).|0001-01-01T00:00:00-> 0001<br /><br /> 0900-01-01T00:00:00-> 0900<br /><br /> 1900-01-01T00:00:00-> 1900<br /><br /> 2009-06-15T13:45:30 – > 2009|
|"yyyyy"|Rok jako pětimístné číslo.<br /><br /> Další informace: [Specifikátor vlastního formátu "yyyyy"](#yyyyySpecifier).|0001-01-01T00:00:00-> 00001<br /><br /> 2009-06-15T13:45:30 – > 02009|
|"z"|Posun hodin od času UTC, bez počátečních nul.<br /><br /> Další informace: [Specifikátor vlastního formátu "z"](#zSpecifier).|2009-06-15T13:45:30.07:00->-7|
|"zz"|Posun hodin od času UTC, s počáteční nulou pro jednocifernou hodnotu.<br /><br /> Další informace: [Specifikátor vlastního formátu "ZZ"](#zzSpecifier).|2009-06-15T13:45:30.07:00->-07|
|"zzz"|Posun v hodinách a minutách od času UTC.<br /><br /> Další informace: [Specifikátor vlastního formátu "ZZZ"](#zzzSpecifier).|2009-06-15T13:45:30.07:00->-07:00|
|":"|Oddělovač času.<br /><br /> Další informace: [Specifikátor vlastního formátu ":"](#timeSeparator).|2009-06-15T13:45:30->: (EN-US)<br /><br /> 2009-06-15T13:45:30->. (it-IT)<br /><br /> 2009-06-15T13:45:30->: (ja-JP)|
|"/"|Oddělovač data.<br /><br /> Další informace: [specifikátor "/" vlastního formátu](#dateSeparator).|2009-06-15T13:45:30->/(EN-US)<br /><br /> 2009-06-15T13:45:30-> – (ar-DZ)<br /><br /> 2009-06-15T13:45:30->. (tr-TR)|
|*řetězec "String*"<br /><br /> *řetězec "String*"|Oddělovač řetězcového literálu.<br /><br /> Další informace: [znakové literály](#Literals).|2009-06-15T13:45:30 ("ARR:" h:m t)-> ARR: 1:45 P<br /><br /> 2009-06-15T13:45:30 (' ARR: ' h:m t)-> ARR: 1:45 P|
|%|Definuje následující znak jako specifikátor vlastního formátu.<br /><br /> Další informace:[použití jednoduchých specifikátorů vlastního formátu](#UsingSingleSpecifiers).|2009-06-15T13:45:30 (% h)-> 1|
|&#92;|Řídicí znak.<br /><br /> Další informace: [literály znaků](#Literals) a [Použití řídicího znaku](#escape).|2009-06-15T13:45:30 (h \h) – > 1 h|
|Jakýkoli jiný znak|Znak je zkopírován do výsledného řetězce beze změny.<br /><br /> Další informace: [znakové literály](#Literals).|2009-06-15T01:45:30 (ARR hh: mm t)-> ARR 01:45 A|

Následující oddíly poskytují další informace o jednotlivých specifikátorech vlastního formátu data a času. Není-li uvedeno jinak, každý specifikátor Vytvoří identickou řetězcovou reprezentaci bez ohledu na to, zda se používá s <xref:System.DateTime> hodnotou nebo <xref:System.DateTimeOffset> hodnotou.

## <a name="the-d-custom-format-specifier"></a><a name="dSpecifier"></a>Specifikátor vlastního formátu "d"

Specifikátor vlastního formátu "d" představuje den v měsíci jako číslo od 1 do 31. Jednociferné číslo dne je formátováno bez počáteční nuly.

Pokud je specifikátor formátu "d" použit bez dalšího vlastního specifikátoru formátu, je interpretován jako specifikátor standardního formátu data a času "d". Další informace o použití jednoduchého specifikátoru formátu naleznete v části [použití jednoduchých specifikátorů vlastního formátu](#UsingSingleSpecifiers) dále v tomto článku.

Následující příklad obsahuje specifikátor vlastního formátu "d" v několika řetězcích formátu.

[!code-csharp[Formatting.DateAndTime.Custom#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#1)]
[!code-vb[Formatting.DateAndTime.Custom#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#1)]

[Zpět na tabulku](#table)

## <a name="the-dd-custom-format-specifier"></a><a name="ddSpecifier"></a>Specifikátor vlastního formátu "dd"

Řetězec vlastního formátu "dd" představuje den v měsíci jako číslo od 01 do 31. Jednociferné číslo dne je formátováno s počáteční nulou.

Následující příklad obsahuje specifikátor vlastního formátu "dd" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#2)]
[!code-vb[Formatting.DateAndTime.Custom#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#2)]

[Zpět na tabulku](#table)

## <a name="the-ddd-custom-format-specifier"></a><a name="dddSpecifier"></a>Specifikátor vlastního formátu "ddd"

Specifikátor vlastního formátu "ddd" představuje zkrácený název dne v týdnu. Lokalizovaný zkrácený název dne v týdnu je načten z <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A?displayProperty=nameWithType> vlastnosti aktuální nebo zadané jazykové verze.

Následující příklad obsahuje specifikátor vlastního formátu "ddd" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#3)]
[!code-vb[Formatting.DateAndTime.Custom#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#3)]

[Zpět na tabulku](#table)

## <a name="the-dddd-custom-format-specifier"></a><a name="ddddSpecifier"></a>Specifikátor vlastního formátu "dddd"

Specifikátor vlastního formátu "dddd" (a libovolný počet dalších specifikátorů "d") představuje úplný název dne v týdnu. Lokalizovaný název dne v týdnu je načten z <xref:System.Globalization.DateTimeFormatInfo.DayNames%2A?displayProperty=nameWithType> vlastnosti aktuální nebo zadané jazykové verze.

Následující příklad obsahuje specifikátor vlastního formátu "dddd" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#4)]
[!code-vb[Formatting.DateAndTime.Custom#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#4)]

[Zpět na tabulku](#table)

## <a name="the-f-custom-format-specifier"></a><a name="fSpecifier"></a>Specifikátor vlastního formátu "f"

Specifikátor vlastního formátu "f" představuje nejvýznamnější číslici zlomku sekund. Představuje tedy desetiny sekundy v hodnotě data a času.

Pokud specifikátor formátu "f" použijete bez dalšího specifikátoru formátu, je interpretován jako specifikátor standardního formátu data a času "f". Další informace o použití jednoduchého specifikátoru formátu naleznete v části [použití jednoduchých specifikátorů vlastního formátu](#UsingSingleSpecifiers) dále v tomto článku.

Použijete-li specifikátory formátu "f" jako součást formátovacího řetězce dodaného <xref:System.DateTime.ParseExact%2A> <xref:System.DateTime.TryParseExact%2A> metodě,, <xref:System.DateTimeOffset.ParseExact%2A> nebo <xref:System.DateTimeOffset.TryParseExact%2A> , počet specifikátorů formátu "f" označuje počet nejvýznamnějších číslic zlomků sekund, které musí být k dispozici pro úspěšné analyzování řetězce.

Následující příklad obsahuje specifikátor vlastního formátu "f" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Zpět na tabulku](#table)

## <a name="the-ff-custom-format-specifier"></a><a name="ffSpecifier"></a>Specifikátor vlastního formátu "FF"

Specifikátor vlastního formátu "ff" představuje dvě nejvýznamnější číslice zlomku sekund. Představuje tedy setiny sekundy v hodnotě data a času.

Následující příklad obsahuje specifikátor vlastního formátu "ff" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Zpět na tabulku](#table)

## <a name="the-fff-custom-format-specifier"></a><a name="fffSpecifier"></a>Specifikátor vlastního formátu "fff"

Specifikátor vlastního formátu "fff" představuje tři nejvýznamnější číslice zlomku sekund. Představuje tedy milisekundy v hodnotě data a času.

Následující příklad obsahuje specifikátor vlastního formátu "fff" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Zpět na tabulku](#table)

## <a name="the-ffff-custom-format-specifier"></a><a name="ffffSpecifier"></a>Specifikátor vlastního formátu "FFFF"

Specifikátor vlastního formátu "ffff" představuje čtyři nejvýznamnější číslice zlomku sekund. Představuje tedy desetitisíciny sekundy v hodnotě data a času.

I když je možné zobrazit deset sekundy druhé komponenty časové hodnoty, tato hodnota nemusí být smysluplná. Přesnost hodnot data a času závisí na rozlišení systémových hodin. V systémech Windows NT verze 3.5 (a vyšší) a Windows Vista je rozlišení hodin přibližně 10–15 milisekund.

[Zpět na tabulku](#table)

## <a name="the-fffff-custom-format-specifier"></a><a name="fffffSpecifier"></a>Specifikátor vlastního formátu "fffff"

Specifikátor vlastního formátu "fffff" představuje pět nejvýznamnějších číslic zlomku sekund. Představuje tedy stotisíciny sekundy v hodnotě data a času.

I když je možné zobrazit stovky sekundy druhé komponenty časové hodnoty, tato hodnota nemusí být smysluplná. Přesnost hodnot data a času závisí na rozlišení systémových hodin. V systémech Windows NT verze 3.5 (a vyšší) a Windows Vista je rozlišení hodin přibližně 10–15 milisekund.

[Zpět na tabulku](#table)

## <a name="the-ffffff-custom-format-specifier"></a><a name="ffffffSpecifier"></a>Specifikátor vlastního formátu "FFFFFF"

Specifikátor vlastního formátu "ffffff" představuje šest nejvýznamnějších číslic zlomku sekund. Představuje tedy miliontiny sekundy v hodnotě data a času.

I když je možné zobrazit Desetimiliontiny druhé komponenty časové hodnoty, tato hodnota nemusí být smysluplná. Přesnost hodnot data a času závisí na rozlišení systémových hodin. V systémech Windows NT verze 3.5 (a vyšší) a Windows Vista je rozlišení hodin přibližně 10–15 milisekund.

[Zpět na tabulku](#table)

## <a name="the-fffffff-custom-format-specifier"></a><a name="fffffffSpecifier"></a>Specifikátor vlastního formátu "fffffff"

Specifikátor vlastního formátu "fffffff" představuje sedm nejvýznamnějších číslic zlomku sekund. Představuje tedy desetimiliontiny sekundy v hodnotě data a času.

I když je možné zobrazit deset Desetimiliontiny druhé komponenty časové hodnoty, tato hodnota nemusí být smysluplná. Přesnost hodnot data a času závisí na rozlišení systémových hodin. V systémech Windows NT verze 3.5 (a vyšší) a Windows Vista je rozlišení hodin přibližně 10–15 milisekund.

[Zpět na tabulku](#table)

## <a name="the-f-custom-format-specifier"></a><a name="F_Specifier"></a>Specifikátor vlastního formátu "F"

Specifikátor vlastního formátu "F" představuje nejvýznamnější číslici zlomku sekund. Představuje tedy desetiny sekundy v hodnotě data a času. Pokud je číslice nula, nezobrazí se žádná hodnota.

Pokud specifikátor formátu "F" použijete bez dalšího specifikátoru formátu, je interpretován jako specifikátor standardního formátu data a času "F". Další informace o použití jednoduchého specifikátoru formátu naleznete v části [použití jednoduchých specifikátorů vlastního formátu](#UsingSingleSpecifiers) dále v tomto článku.

Počet specifikátorů formátu "F" použitých s <xref:System.DateTime.ParseExact%2A> <xref:System.DateTime.TryParseExact%2A> metodou,, <xref:System.DateTimeOffset.ParseExact%2A> nebo <xref:System.DateTimeOffset.TryParseExact%2A> označuje maximální počet nejvýznamnějších číslic zlomků sekund, které mohou být k dispozici pro úspěšné analyzování řetězce.

Následující příklad obsahuje specifikátor vlastního formátu "F" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Zpět na tabulku](#table)

## <a name="the-ff-custom-format-specifier"></a><a name="FF_Specifier"></a>Specifikátor vlastního formátu "FF"

Specifikátor vlastního formátu "FF" představuje dvě nejvýznamnější číslice zlomku sekund. Představuje tedy setiny sekundy v hodnotě data a času. Avšak koncové nuly nebo dvě číslice nuly nejsou zobrazeny.

Následující příklad obsahuje specifikátor vlastního formátu "FF" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Zpět na tabulku](#table)

## <a name="the-fff-custom-format-specifier"></a><a name="FFF_Specifier"></a>Specifikátor vlastního formátu "FFF"

Specifikátor vlastního formátu "FFF" představuje tři nejvýznamnější číslice zlomku sekund. Představuje tedy milisekundy v hodnotě data a času. Koncové nuly nebo tři číslice nuly však nejsou zobrazeny.

Následující příklad obsahuje specifikátor vlastního formátu "FFF" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
[!code-vb[Formatting.DateAndTime.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

[Zpět na tabulku](#table)

## <a name="the-ffff-custom-format-specifier"></a><a name="FFFF_Specifier"></a>Specifikátor vlastního formátu "FFFF"

Specifikátor vlastního formátu "FFFF" představuje čtyři nejvýznamnější číslice zlomku sekund. Představuje tedy desetitisíciny sekundy v hodnotě data a času. Koncové nuly nebo čísla se čtyřmi nulami se však nezobrazují.

I když je možné zobrazit deset sekundy druhé komponenty časové hodnoty, tato hodnota nemusí být smysluplná. Přesnost hodnot data a času závisí na rozlišení systémových hodin. V systémech Windows NT verze 3.5 (a vyšší) a Windows Vista je rozlišení hodin přibližně 10–15 milisekund.

[Zpět na tabulku](#table)

## <a name="the-fffff-custom-format-specifier"></a><a name="FFFFF_Specifier"></a>Specifikátor vlastního formátu "FFFFF"

Specifikátor vlastního formátu "FFFFF" představuje pět nejvýznamnějších číslic zlomku sekund. Představuje tedy stotisíciny sekundy v hodnotě data a času. Koncové nuly nebo čísla s pěti nulami se však nezobrazují.

I když je možné zobrazit stovky sekundy druhé komponenty časové hodnoty, tato hodnota nemusí být smysluplná. Přesnost hodnot data a času závisí na rozlišení systémových hodin. V systémech Windows NT verze 3.5 (a vyšší) a Windows Vista je rozlišení hodin přibližně 10–15 milisekund.

[Zpět na tabulku](#table)

## <a name="the-ffffff-custom-format-specifier"></a><a name="FFFFFF_Specifier"></a>Specifikátor vlastního formátu "FFFFFF"

Specifikátor vlastního formátu "FFFFFF" představuje šest nejvýznamnějších číslic zlomku sekund. Představuje tedy miliontiny sekundy v hodnotě data a času. Koncové nuly nebo čísla šesti nul však nejsou zobrazeny.

I když je možné zobrazit Desetimiliontiny druhé komponenty časové hodnoty, tato hodnota nemusí být smysluplná. Přesnost hodnot data a času závisí na rozlišení systémových hodin. V systémech Windows NT verze 3.5 (a vyšší) a Windows Vista je rozlišení hodin přibližně 10–15 milisekund.

[Zpět na tabulku](#table)

## <a name="the-fffffff-custom-format-specifier"></a><a name="FFFFFFF_Specifier"></a>Specifikátor vlastního formátu "FFFFFFF"

Specifikátor vlastního formátu "FFFFFFF" představuje sedm nejvýznamnějších číslic zlomku sekund. Představuje tedy desetimiliontiny sekundy v hodnotě data a času. Nezobrazuje se ale koncová nula nebo sedm číslic nula.

I když je možné zobrazit deset Desetimiliontiny druhé komponenty časové hodnoty, tato hodnota nemusí být smysluplná. Přesnost hodnot data a času závisí na rozlišení systémových hodin. V systémech Windows NT verze 3.5 (a vyšší) a Windows Vista je rozlišení hodin přibližně 10–15 milisekund.

[Zpět na tabulku](#table)

## <a name="the-g-or-gg-custom-format-specifier"></a><a name="gSpecifier"></a>Specifikátor vlastního formátu "g" nebo "GG"

Specifikátor vlastního formátu "g" nebo "gg" (plus libovolný počet dalších specifikátorů "g") představuje období nebo éru, jako je například n. l. Operace formátování ignoruje tento specifikátor, pokud datum, které má být formátováno, nemá přidružený řetězec tečky nebo období.

Pokud je specifikátor formátu "g" použit bez dalšího vlastního specifikátoru formátu, je interpretován jako specifikátor standardního formátu data a času "g". Další informace o použití jednoduchého specifikátoru formátu naleznete v části [použití jednoduchých specifikátorů vlastního formátu](#UsingSingleSpecifiers) dále v tomto článku.

Následující příklad obsahuje specifikátor vlastního formátu "g" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#6)]
[!code-vb[Formatting.DateAndTime.Custom#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#6)]

[Zpět na tabulku](#table)

## <a name="the-h-custom-format-specifier"></a><a name="hSpecifier"></a>Specifikátor vlastního formátu "h"

Specifikátor vlastního formátu "h" představuje hodiny jako číslo od 1 do 12. Hodiny jsou tedy reprezentovány ve 12hodinovém formátu, který počítá celé hodiny od půlnoci nebo od poledne. Konkrétní hodina po půlnoci je nerozeznatelná od stejné hodiny po poledni. Hodiny nejsou zaokrouhleny a jednociferné číslo hodiny je formátováno bez počáteční nuly. Například pro čas 5:43 dopoledne nebo odpoledne tento specifikátor vlastního formátu zobrazí hodnotu "5".

Pokud je specifikátor formátu "h" použit bez dalšího vlastního specifikátoru formátu, je interpretován jako specifikátor standardního formátu data a času a vyvolá <xref:System.FormatException> . Další informace o použití jednoduchého specifikátoru formátu naleznete v části [použití jednoduchých specifikátorů vlastního formátu](#UsingSingleSpecifiers) dále v tomto článku.

Následující příklad obsahuje specifikátor vlastního formátu "h" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Zpět na tabulku](#table)

## <a name="the-hh-custom-format-specifier"></a><a name="hhSpecifier"></a>Specifikátor vlastního formátu "HH"

Specifikátor vlastního formátu "hh" (plus libovolný počet dalších specifikátorů "h") představuje hodiny jako čísla od 01 do 12. Představuje tedy hodiny ve 12hodinovém formátu, který počítá celé hodiny od půlnoci nebo od poledne. Konkrétní hodina po půlnoci je nerozeznatelná od stejné hodiny po poledni. Hodiny nejsou zaokrouhleny a jednociferné číslo hodiny je formátováno s počáteční nulou. Například pro čas 5:43 dopoledne nebo odpoledne tento specifikátor formátu zobrazí hodnotu "05".

Následující příklad obsahuje specifikátor vlastního formátu "hh" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Zpět na tabulku](#table)

## <a name="the-h-custom-format-specifier"></a><a name="H_Specifier"></a>Specifikátor vlastního formátu "H"

Specifikátor vlastního formátu "H" představuje hodiny jako číslo od 0 do 23. Představuje tedy hodiny ve 24hodinovém formátu počítaném od nuly, který počítá celé hodiny od půlnoci. Jednociferné číslo hodiny je formátováno bez počáteční nuly.

Pokud je specifikátor formátu "H" použit bez dalšího vlastního specifikátoru formátu, je interpretován jako specifikátor standardního formátu data a času a vyvolá <xref:System.FormatException> . Další informace o použití jednoduchého specifikátoru formátu naleznete v části [použití jednoduchých specifikátorů vlastního formátu](#UsingSingleSpecifiers) dále v tomto článku.

Následující příklad obsahuje specifikátor vlastního formátu "H" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#9](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#9)]
[!code-vb[Formatting.DateAndTime.Custom#9](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#9)]

[Zpět na tabulku](#table)

## <a name="the-hh-custom-format-specifier"></a><a name="HH_Specifier"></a>Specifikátor vlastního formátu "HH"

Specifikátor vlastního formátu "HH" (plus libovolný počet dalších specifikátorů "H") představuje hodiny jako čísla od 00 do 23. Představuje tedy hodiny ve 24hodinovém formátu počítaném od nuly, který počítá celé hodiny od půlnoci. Jednociferné číslo hodiny je formátováno s počáteční nulou.

Následující příklad obsahuje specifikátor vlastního formátu "HH" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#10](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#10)]
[!code-vb[Formatting.DateAndTime.Custom#10](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#10)]

[Zpět na tabulku](#table)

## <a name="the-k-custom-format-specifier"></a><a name="KSpecifier"></a>Specifikátor vlastního formátu "K"

Specifikátor vlastního formátu "K" představuje informace o časovém pásmu hodnoty data a času. Při použití tohoto specifikátoru formátu s <xref:System.DateTime> hodnotami je výsledný řetězec definován hodnotou <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> vlastnosti:

- Pro místní časové pásmo ( <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> hodnota vlastnosti <xref:System.DateTimeKind.Local?displayProperty=nameWithType> ) je tento specifikátor ekvivalentní specifikátoru "ZZZ" a vytváří výsledný řetězec obsahující místní posun od koordinovaného světového času (UTC), například "-07:00".

- Pro čas UTC ( <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> hodnota vlastnosti <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> ) výsledný řetězec obsahuje znak "Z", který představuje datum UTC.

- Po dobu od nespecifikovaného časového pásma (čas <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> , jehož vlastnost se rovná <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> ) je výsledek ekvivalentem <xref:System.String.Empty?displayProperty=nameWithType> .

Pro <xref:System.DateTimeOffset> hodnoty je specifikátor formátu "K" ekvivalentní specifikátoru formátu "ZZZ" a vytváří výsledný řetězec obsahující <xref:System.DateTimeOffset> posun hodnoty od času UTC.

Pokud je specifikátor formátu "K" použit bez dalšího vlastního specifikátoru formátu, je interpretován jako specifikátor standardního formátu data a času a vyvolá <xref:System.FormatException> . Další informace o použití jednoduchého specifikátoru formátu naleznete v části [použití jednoduchých specifikátorů vlastního formátu](#UsingSingleSpecifiers) dále v tomto článku.

Následující příklad zobrazí řetězec, který je výsledkem použití specifikátoru vlastního formátu "K" s různými <xref:System.DateTime> hodnotami a <xref:System.DateTimeOffset> v systému v tichomořském časovém pásmu v USA.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#12](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#12)]
[!code-vb[Formatting.DateAndTime.Custom#12](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#12)]

[Zpět na tabulku](#table)

## <a name="the-m-custom-format-specifier"></a><a name="mSpecifier"></a>Specifikátor vlastního formátu "m"

Specifikátor vlastního formátu "m" představuje minuty jako čísla od 0 do 59. Minuta představuje celé minuty, které uplynuly od poslední hodiny. Jednociferné číslo minuty je formátováno bez počáteční nuly.

Pokud je specifikátor formátu "m" použit bez dalšího vlastního specifikátoru formátu, je interpretován jako specifikátor standardního formátu data a času "m". Další informace o použití jednoduchého specifikátoru formátu naleznete v části [použití jednoduchých specifikátorů vlastního formátu](#UsingSingleSpecifiers) dále v tomto článku.

Následující příklad obsahuje specifikátor vlastního formátu "m" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Zpět na tabulku](#table)

## <a name="the-mm-custom-format-specifier"></a><a name="mmSpecifier"></a>Specifikátor vlastního formátu "mm"

Specifikátor vlastního formátu "mm" (plus libovolný počet dalších specifikátorů "m") představuje minuty jako čísla od 00 do 59. Minuta představuje celé minuty, které uplynuly od poslední hodiny. Jednociferné číslo minut je formátováno s počáteční nulou.

Následující příklad obsahuje specifikátor vlastního formátu "mm" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Zpět na tabulku](#table)

## <a name="the-m-custom-format-specifier"></a><a name="M_Specifier"></a>Specifikátor vlastního formátu "M"

Specifikátor vlastního formátu "M" představuje měsíc jako číslo od 1 do 12 (nebo od 1 do 13 pro kalendáře, které mají 13 měsíců). Jednociferné číslo měsíce je formátováno bez počáteční nuly.

Pokud je specifikátor formátu "M" použit bez dalšího vlastního specifikátoru formátu, je interpretován jako specifikátor standardního formátu data a času "M". Další informace o použití jednoduchého specifikátoru formátu naleznete v části [použití jednoduchých specifikátorů vlastního formátu](#UsingSingleSpecifiers) dále v tomto článku.

Následující příklad obsahuje specifikátor vlastního formátu "M" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#11](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#11)]
[!code-vb[Formatting.DateAndTime.Custom#11](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#11)]

[Zpět na tabulku](#table)

## <a name="the-mm-custom-format-specifier"></a><a name="MM_Specifier"></a>Specifikátor vlastního formátu "MM"

Specifikátor vlastního formátu "MM" představuje měsíc jako číslo od 01 do 12 (nebo od 1 do 13 pro kalendáře, které mají 13 měsíců). Jednociferné číslo měsíce je formátováno s počáteční nulou.

Následující příklad obsahuje specifikátor vlastního formátu "MM" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#2)]
[!code-vb[Formatting.DateAndTime.Custom#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#2)]

[Zpět na tabulku](#table)

## <a name="the-mmm-custom-format-specifier"></a><a name="MMM_Specifier"></a>Specifikátor vlastního formátu "MMM"

Specifikátor vlastního formátu "MMM" představuje zkrácený název měsíce. Lokalizovaný zkrácený název měsíce je načten z <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames%2A?displayProperty=nameWithType> vlastnosti aktuální nebo zadané jazykové verze.

Následující příklad obsahuje specifikátor vlastního formátu "MMM" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#3)]
[!code-vb[Formatting.DateAndTime.Custom#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#3)]

[Zpět na tabulku](#table)

## <a name="the-mmmm-custom-format-specifier"></a><a name="MMMM_Specifier"></a>Specifikátor vlastního formátu "MMMM"

Specifikátor vlastního formátu "MMMM" představuje úplný název měsíce. Lokalizovaný název měsíce je načten z <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A?displayProperty=nameWithType> vlastnosti aktuální nebo zadané jazykové verze.

Následující příklad obsahuje specifikátor vlastního formátu "MMMM" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#4)]
[!code-vb[Formatting.DateAndTime.Custom#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#4)]

[Zpět na tabulku](#table)

## <a name="the-s-custom-format-specifier"></a><a name="sSpecifier"></a>Specifikátor vlastního formátu "s"

Specifikátor vlastního formátu "s" představuje sekundy jako čísla od 0 do 59. Výsledek představuje celé sekundy, které uplynuly od poslední minuty. Jednociferné číslo sekundy je formátováno bez počáteční nuly.

Pokud je specifikátor formátu "s" použit bez dalšího vlastního specifikátoru formátu, je interpretován jako specifikátor standardního formátu data a času "s". Další informace o použití jednoduchého specifikátoru formátu naleznete v části [použití jednoduchých specifikátorů vlastního formátu](#UsingSingleSpecifiers) dále v tomto článku.

Následující příklad obsahuje specifikátor vlastního formátu "s" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Zpět na tabulku](#table)

## <a name="the-ss-custom-format-specifier"></a><a name="ssSpecifier"></a>Specifikátor vlastního formátu "SS"

Specifikátor vlastního formátu "ss" (plus libovolný počet dalších specifikátorů "s") představuje sekundy jako čísla od 00 do 59. Výsledek představuje celé sekundy, které uplynuly od poslední minuty. Jednociferné číslo sekundy je formátováno s počáteční nulou.

Následující příklad obsahuje specifikátor vlastního formátu "ss" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Zpět na tabulku](#table)

## <a name="the-t-custom-format-specifier"></a><a name="tSpecifier"></a>Specifikátor vlastního formátu "t"

Specifikátor vlastního formátu "t" představuje první znak označení dopoledne/odpoledne. Odpovídající lokalizovaný specifikátor specifikátoru je načten z <xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A?displayProperty=nameWithType> vlastnosti nebo <xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A?displayProperty=nameWithType> aktuální nebo konkrétní jazykové verze. Označení dopoledne (AM) se používá pro všechny hodnoty času od 0:00:00 (půlnoc) do 11:59:59.999. Označení odpoledne (PM) se používá pro všechny hodnoty času od 12:00:00 (poledne) do 23:59:59.999.

Pokud je specifikátor formátu "t" použit bez dalšího vlastního specifikátoru formátu, je interpretován jako specifikátor standardního formátu data a času "t". Další informace o použití jednoduchého specifikátoru formátu naleznete v části [použití jednoduchých specifikátorů vlastního formátu](#UsingSingleSpecifiers) dále v tomto článku.

Následující příklad obsahuje specifikátor vlastního formátu "t" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
[!code-vb[Formatting.DateAndTime.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

[Zpět na tabulku](#table)

## <a name="the-tt-custom-format-specifier"></a><a name="ttSpecifier"></a>Specifikátor vlastního formátu "tt"

Specifikátor vlastního formátu "tt" (plus libovolný počet dalších specifikátorů "t") představuje celé označení dopoledne/odpoledne. Odpovídající lokalizovaný specifikátor specifikátoru je načten z <xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A?displayProperty=nameWithType> vlastnosti nebo <xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A?displayProperty=nameWithType> aktuální nebo konkrétní jazykové verze. Označení dopoledne (AM) se používá pro všechny hodnoty času od 0:00:00 (půlnoc) do 11:59:59.999. Označení odpoledne (PM) se používá pro všechny hodnoty času od 12:00:00 (poledne) do 23:59:59.999.

Ujistěte se, že používáte specifikátor "tt" pro jazyky, pro které je nezbytné zachovat rozdíl mezi dopolednem a ODPOLEDNEm. Pro ukázku je uvedena japonština, pro kterou se liší určení dopoledne a odpoledne (AM a PM) v druhém znaku namísto prvního znaku.

Následující příklad obsahuje specifikátor vlastního formátu "tt" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
[!code-vb[Formatting.DateAndTime.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

[Zpět na tabulku](#table)

## <a name="the-y-custom-format-specifier"></a><a name="ySpecifier"></a>Specifikátor vlastního formátu "y"

Specifikátor vlastního formátu "y" představuje rok jako jednociferné nebo dvouciferné číslo. Pokud rok obsahuje více než dvě číslice, zobrazí se ve výsledku pouze dvě číslice nižšího řádu. Pokud první číslice dvoumístného čísla roku začíná nulou (například 2008), je číslo formátováno bez počáteční nuly.

Pokud je specifikátor formátu "y" použit bez dalšího vlastního specifikátoru formátu, je interpretován jako specifikátor standardního formátu data a času "y". Další informace o použití jednoduchého specifikátoru formátu naleznete v části [použití jednoduchých specifikátorů vlastního formátu](#UsingSingleSpecifiers) dále v tomto článku.

Následující příklad obsahuje specifikátor vlastního formátu "y" v řetězci vlastního formátu.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Zpět na tabulku](#table)

## <a name="the-yy-custom-format-specifier"></a><a name="yySpecifier"></a>Specifikátor vlastního formátu "yy"

Specifikátor vlastního formátu "yy" představuje rok jako dvouciferné číslo. Pokud rok obsahuje více než dvě číslice, zobrazí se ve výsledku pouze dvě číslice nižšího řádu. Pokud má dvoumístný rok méně než dvě platné číslice, je číslo doplněno počátečními nulami za účelem vytvoření dvouciferného čísla.

V rámci operace analýzy je dvoumístný rok, který je analyzován pomocí specifikátoru vlastního formátu "yy", interpretován na základě <xref:System.Globalization.Calendar.TwoDigitYearMax%2A?displayProperty=nameWithType> vlastnosti aktuálního kalendáře poskytovatele formátu. Následující příklad analyzuje řetězcovou reprezentaci data s rokem vyjádřeným dvěma číslicemi pomocí výchozího gregoriánského kalendáře jazykové verze en_US, což v tomto případě představuje aktuální jazykovou verzi. Poté změní objekt aktuální jazykové verze <xref:System.Globalization.CultureInfo> na použití <xref:System.Globalization.GregorianCalendar> objektu, jehož vlastnost byla <xref:System.Globalization.GregorianCalendar.TwoDigitYearMax%2A> změněna.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#19](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/parseexact2digityear1.cs#19)]
[!code-vb[Formatting.DateAndTime.Custom#19](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/parseexact2digityear1.vb#19)]

Následující příklad obsahuje specifikátor vlastního formátu "yy" v řetězci vlastního formátu.

[!code-csharp[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Zpět na tabulku](#table)

## <a name="the-yyy-custom-format-specifier"></a><a name="yyySpecifier"></a>Specifikátor vlastního formátu "yyy"

Specifikátor vlastního formátu "yyy" představuje rok nejméně se třemi číslicemi. Pokud rok obsahuje více než tři platné číslice, budou obsaženy ve výsledném řetězci. Pokud má rok méně než tři číslice, je číslo doplněno počátečními nulami tak, aby bylo vytvořeno trojciferné číslo.

> [!NOTE]
> Pro thajský buddhistický kalendář, který může mít pět číslic roku, zobrazí tento specifikátor formátu všechny platné číslice.

Následující příklad obsahuje specifikátor vlastního formátu "yyy" v řetězci vlastního formátu.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Zpět na tabulku](#table)

## <a name="the-yyyy-custom-format-specifier"></a><a name="yyyySpecifier"></a>Specifikátor vlastního formátu "rrrr"

Specifikátor vlastního formátu "yyyy" představuje rok nejméně se čtyřmi číslicemi. Pokud rok obsahuje více než čtyři platné číslice, budou obsaženy ve výsledném řetězci. Pokud má rok méně než čtyři číslice, je číslo doplněno počátečními nulami tak, aby bylo vytvořeno čtyřciferné číslo.

> [!NOTE]
> Pro thajský buddhistický kalendář, který může mít pět číslic roku, zobrazí tento specifikátor formátu minimálně čtyři číslice.

Následující příklad obsahuje specifikátor vlastního formátu "yyyy" v řetězci vlastního formátu.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Zpět na tabulku](#table)

## <a name="the-yyyyy-custom-format-specifier"></a><a name="yyyyySpecifier"></a>Specifikátor vlastního formátu "yyyyy"

Specifikátor vlastního formátu "yyyyy" (plus libovolný počet dalších specifikátorů "y") představuje rok nejméně s pěti číslicemi. Pokud rok obsahuje více než pět platných číslic, budou obsaženy ve výsledném řetězci. Pokud má rok méně než pět číslic, je číslo doplněno počátečními nulami tak, aby bylo vytvořeno pěticiferné číslo.

Pokud existují další specifikátory "y", je číslo doplněno tolika počátečními nulami, kolik je třeba pro vytvoření čísla podle specifikátorů "y".

Následující příklad obsahuje specifikátor vlastního formátu "yyyyy" v řetězci vlastního formátu.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
[!code-vb[Formatting.DateAndTime.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

[Zpět na tabulku](#table)

## <a name="the-z-custom-format-specifier"></a><a name="zSpecifier"></a>Specifikátor vlastního formátu "z"

S <xref:System.DateTime> hodnotami vlastní specifikátor formátu "z" představuje posun místního časového pásma operačního systému od koordinovaného světového času (UTC), měřeno v hodinách. Nereflektuje hodnotu <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> vlastnosti instance. Z tohoto důvodu specifikátor formátu "z" není doporučeno používat s <xref:System.DateTime> hodnotami.

S <xref:System.DateTimeOffset> hodnotami představuje tento specifikátor formátu <xref:System.DateTimeOffset> posun hodnoty od času UTC v hodinách.

Posun je vždy zobrazen s počátečním znaménkem. Znaménko plus (+) označuje hodiny před časem UTC a symbol mínus (-) označuje hodiny za časem UTC. Jednociferné číslo posunu je formátováno bez počáteční nuly.

Pokud je specifikátor formátu "z" použit bez dalšího vlastního specifikátoru formátu, je interpretován jako specifikátor standardního formátu data a času a vyvolá <xref:System.FormatException> . Další informace o použití jednoduchého specifikátoru formátu naleznete v části [použití jednoduchých specifikátorů vlastního formátu](#UsingSingleSpecifiers) dále v tomto článku.

Následující příklad obsahuje specifikátor vlastního formátu "z" v řetězci vlastního formátu.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
[!code-vb[Formatting.DateAndTime.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]

[Zpět na tabulku](#table)

## <a name="the-zz-custom-format-specifier"></a><a name="zzSpecifier"></a>Specifikátor vlastního formátu "ZZ"

S <xref:System.DateTime> hodnotami Specifikátor vlastního formátu "ZZ" představuje posun místního časového pásma operačního systému od času UTC, měřený v hodinách. Nereflektuje hodnotu <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> vlastnosti instance. Z tohoto důvodu specifikátor formátu "ZZ" není doporučeno používat s <xref:System.DateTime> hodnotami.

S <xref:System.DateTimeOffset> hodnotami představuje tento specifikátor formátu <xref:System.DateTimeOffset> posun hodnoty od času UTC v hodinách.

Posun je vždy zobrazen s počátečním znaménkem. Znaménko plus (+) označuje hodiny před časem UTC a symbol mínus (-) označuje hodiny za časem UTC. Jednociferné číslo posunu je formátováno s počáteční nulou.

Následující příklad obsahuje specifikátor vlastního formátu "zz" v řetězci vlastního formátu.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
[!code-vb[Formatting.DateAndTime.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]

[Zpět na tabulku](#table)

## <a name="the-zzz-custom-format-specifier"></a><a name="zzzSpecifier"></a>Specifikátor vlastního formátu "ZZZ"

S <xref:System.DateTime> hodnotami vlastní specifikátor formátu "ZZZ" představuje posun místního časového pásma operačního systému od času UTC, měřený v hodinách a minutách. Nereflektuje hodnotu <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> vlastnosti instance. Z tohoto důvodu specifikátor formátu "ZZZ" není doporučeno používat s <xref:System.DateTime> hodnotami.

S <xref:System.DateTimeOffset> hodnotami představuje tento specifikátor formátu <xref:System.DateTimeOffset> posun hodnoty od času UTC v hodinách a minutách.

Posun je vždy zobrazen s počátečním znaménkem. Znaménko plus (+) označuje hodiny před časem UTC a symbol mínus (-) označuje hodiny za časem UTC. Jednociferné číslo posunu je formátováno s počáteční nulou.

Následující příklad obsahuje specifikátor vlastního formátu "zzz" ve vlastním řetězci formátu.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
[!code-vb[Formatting.DateAndTime.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]

[Zpět na tabulku](#table)

## <a name="the--custom-format-specifier"></a><a name="timeSeparator"></a>Specifikátor vlastního formátu ":"
Specifikátor vlastního formátu ":" představuje oddělovač času, který se používá k rozlišení hodin, minut a sekund. Odpovídající lokalizovaný oddělovač času je načten z <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A?displayProperty=nameWithType> vlastnosti aktuální nebo zadané jazykové verze.

> [!NOTE]
> Chcete-li změnit oddělovač času pro určitý řetězec data a času, zadejte znak oddělovače v oddělovači řetězcového literálu. Například řetězec vlastního formátu `hh'_'dd'_'ss` vytvoří výsledný řetězec, ve kterém je znak " \_ " (podtržítko) vždy použit jako oddělovač času. Chcete-li změnit časový oddělovač pro všechna data jazykové verze, buď změňte hodnotu <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A?displayProperty=nameWithType> vlastnosti aktuální jazykové verze, nebo vytvořte instanci <xref:System.Globalization.DateTimeFormatInfo> objektu, přiřaďte znak k <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A> vlastnosti a zavolejte přetížení metody formátování, která obsahuje <xref:System.IFormatProvider> parametr.

Pokud je specifikátor formátu ":" použit bez dalšího vlastního specifikátoru formátu, je interpretován jako specifikátor standardního formátu data a času a vyvolá <xref:System.FormatException> . Další informace o použití jednoduchého specifikátoru formátu naleznete v části [použití jednoduchých specifikátorů vlastního formátu](#UsingSingleSpecifiers) dále v tomto článku.

[Zpět na tabulku](#table)

## <a name="the--custom-format-specifier"></a><a name="dateSeparator"></a>Specifikátor vlastního formátu "/"

Specifikátor vlastního formátu "/" představuje oddělovač dat, který se používá k rozlišení roků, měsíců a dnů. Odpovídající lokalizovaný oddělovač data je načten z <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A?displayProperty=nameWithType> vlastnosti aktuální nebo zadané jazykové verze.

> [!NOTE]
> Chcete-li změnit oddělovač data pro určitý řetězec data a času, zadejte znak oddělovače v oddělovači řetězcového literálu. Například řetězec vlastního formátu `mm'/'dd'/'yyyy` vytvoří výsledný řetězec, ve kterém je znak "/" vždy použit jako oddělovač data. Chcete-li změnit oddělovač data pro všechna data jazykové verze, buď změňte hodnotu <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A?displayProperty=nameWithType> vlastnosti aktuální jazykové verze, nebo vytvořte instanci <xref:System.Globalization.DateTimeFormatInfo> objektu, přiřaďte znak k <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A> vlastnosti a zavolejte přetížení metody formátování, která obsahuje <xref:System.IFormatProvider> parametr.

Pokud je specifikátor formátu "/" použit bez dalšího vlastního specifikátoru formátu, je interpretován jako specifikátor standardního formátu data a času a vyvolá <xref:System.FormatException> . Další informace o použití jednoduchého specifikátoru formátu naleznete v části [použití jednoduchých specifikátorů vlastního formátu](#UsingSingleSpecifiers) dále v tomto článku.

[Zpět na tabulku](#table)

## <a name="character-literals"></a><a name="Literals"></a>Literály znaků

Následující znaky v řetězci vlastního formátu data a času jsou vyhrazeny a jsou vždy interpretovány jako znaky formátování nebo, v případě ",",/a \\ , jako speciální znaky.

||||||
|-|-|-|-|-|
|F|H|K|M|d|
|f|g|h|m|s|
|t|y|z|%|:|
|/|"|'|&#92;||

Všechny ostatní znaky jsou vždy interpretovány jako znakové literály a v operaci formátování jsou zahrnuty ve výsledném řetězci beze změny.  V operaci analýzy musí přesně odpovídat znakům ve vstupním řetězci; Porovnávání rozlišuje velká a malá písmena.

Následující příklad obsahuje literálové znaky "PST" (pro Tichomoří (běžný čas)) a "PDT" (pro Tichomoří (letní čas)) představující místní časové pásmo ve formátu řetězce. Všimněte si, že řetězec je zahrnut ve výsledném řetězci a že řetězec, který obsahuje řetězec místního časového pásma, se také úspěšně analyzuje.

[!code-csharp[Formatting.DateAndTime.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx1.cs#20)]
[!code-vb[Formatting.DateAndTime.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx1.vb#20)]

Existují dva způsoby, jak označit, že znaky se mají interpretovat jako literální znaky, a ne jako vyhrazené znaky, aby je bylo možné zahrnout do výsledného řetězce nebo úspěšně analyzovat ve vstupním řetězci:

- Pomocí uvozovacího znaku každého rezervovaného znaku. Další informace naleznete v tématu [Použití řídicího znaku](#escape).

Následující příklad obsahuje literálové znaky "PST" (pro Tichomoří (běžný čas)), které reprezentují místní časové pásmo ve formátu řetězce. Vzhledem k tomu, že obě "s" i "t" jsou vlastní formátovací řetězce, oba znaky musí být uvozeny, aby je bylo možné interpretovat jako znakové literály.

[!code-csharp[Formatting.DateAndTime.Custom#21](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx2.cs#21)]
[!code-vb[Formatting.DateAndTime.Custom#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx2.vb#21)]

- Uzavřením celého literálového řetězce v uvozovkách nebo apostrofech. Následující příklad je podobný předchozímu, s tím rozdílem, že "PST" je uzavřen v uvozovkách k označení toho, že celý řetězec s oddělovači by měl být interpretován jako znaková literály.

[!code-csharp[Formatting.DateAndTime.Custom#22](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx3.cs#22)]
[!code-vb[Formatting.DateAndTime.Custom#22](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx3.vb#22)]

## <a name="notes"></a>Poznámky

### <a name="using-single-custom-format-specifiers"></a><a name="UsingSingleSpecifiers"></a>Použití jednoduchých specifikátorů vlastního formátu

Řetězec vlastního formátu data a času se skládá ze dvou nebo několika znaků. Metody formátování data a času interpretují jakýkoli řetězec s jediným znakem jako řetězec standardního formátu data a času. Pokud nerozpoznají znak jako platný specifikátor formátu, vyvolají <xref:System.FormatException> . Například řetězec formátu, který se skládá pouze ze specifikátoru "h", je interpretován jako řetězec standardního formátu data a času. V tomto konkrétním případě je však vyvolána výjimka, protože není k dispozici žádné standardní datum a TimeFormat specifikátoru "h".

Chcete-li použít kterýkoli ze specifikátorů vlastního formátu data a času jako jediný specifikátor v řetězci formátu (to znamená, že chcete použít samotné specifikátory formátu "d", "f", "F", "g", "h", "H", "K", "m", "M", "s", "t", "y", "z", ":" nebo "/"), vložte před nebo za specifikátor mezeru, nebo vložte před jednoduchý specifikátor vlastního formátu specifikátor formátu procento %.

Například " `%h"` je interpretován jako řetězec vlastního formátu data a času, který zobrazuje hodinu reprezentovanou aktuální hodnotou data a času. Můžete také použít řetězec formátu " h" nebo "h ", ačkoli tato hodnota vloží ve výsledném řetězci vedle hodin mezeru. Následující příklad znázorňuje tyto tři řetězce formátu.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#16](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/literal1.cs#16)]
[!code-vb[Formatting.DateAndTime.Custom#16](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/literal1.vb#16)]

### <a name="using-the-escape-character"></a><a name="escape"></a>Použití řídicího znaku

Znaky "d", "f", "F", "g", "h", "H", "K", "m", "M", "s", "t", "y", "z", ":", nebo "/" v řetězci formátu jsou interpretovány jako specifikátory vlastního formátu, nikoli jako literální znaky. Chcete-li zabránit interpretaci znaku jako specifikátoru formátu, můžete před něj zadat zpětné lomítko ( \\ ), což je řídicí znak. Řídicí znak označuje, že následující znak je literální znak, který by měl být zařazen do výsledného řetězce beze změny.

Chcete-li do výsledného řetězce zahrnout zpětné lomítko, je nutné ho vytvořit pomocí jiného zpětného lomítka ( `\\` ).

> [!NOTE]
> Některé kompilátory, jako jsou například kompilátory jazyka C++ a jazyka C#, mohou také interpretovat jedno zpětné lomítko jako řídicí znak. Abyste se ujistili, zda je řetězec interpretován při formátování správně, můžete v jazyce C# použít literální řetězcový znak verbatim (znak @) před řetězcem, nebo v jazyce C# a C++ přidat další znak zpětného lomítka před každé zpětné lomítko. Následující příklad jazyka C# ukazuje oba přístupy.

Následující příklad používá řídicí znak, aby zamezil operacím formátování v interpretaci znaků "h" a "m" jako specifikátorů formátu.

[!code-csharp-interactive[Formatting.DateAndTime.Custom#15](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/escape1.cs#15)]
[!code-vb[Formatting.DateAndTime.Custom#15](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/escape1.vb#15)]

### <a name="control-panel-settings"></a>Nastavení ovládacích panelů

Nastavení **místní a jazykové** nastavení v Ovládacích panelech ovlivní výsledný řetězec vytvořený pomocí operace formátování, která zahrnuje mnoho vlastních specifikátorů formátu data a času. Tato nastavení slouží k inicializaci <xref:System.Globalization.DateTimeFormatInfo> objektu přidruženého k aktuální jazykové verzi vlákna, které poskytuje hodnoty použité k řízení formátování. Počítače, které používají různá nastavení, generují různé výsledné řetězce.

Kromě toho, pokud použijete <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29> konstruktor k vytvoření instance nového <xref:System.Globalization.CultureInfo> objektu, který představuje stejnou jazykovou verzi jako aktuální jazyková verze systému, všechna přizpůsobení, která jsou vytvořena položkou **místní a jazykové nastavení** v Ovládacích panelech, budou použita pro nový <xref:System.Globalization.CultureInfo> objekt. Konstruktor můžete použít <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29> k vytvoření <xref:System.Globalization.CultureInfo> objektu, který nereflektuje vlastní nastavení systému.

### <a name="datetimeformatinfo-properties"></a>Vlastnosti DateTimeFormatInfo

Formátování je ovlivněno vlastnostmi aktuálního <xref:System.Globalization.DateTimeFormatInfo> objektu, který je poskytnut implicitně aktuální jazykovou verzí vlákna nebo explicitně <xref:System.IFormatProvider> parametrem metody, která vyvolá formátování. Pro <xref:System.IFormatProvider> parametr je nutné zadat <xref:System.Globalization.CultureInfo> objekt, který představuje jazykovou verzi nebo <xref:System.Globalization.DateTimeFormatInfo> objekt.

Výsledný řetězec vytvořený mnoha specifikátory vlastního formátu data a času závisí také na vlastnostech aktuálního <xref:System.Globalization.DateTimeFormatInfo> objektu. Vaše aplikace může změnit výsledek vytvořený některými vlastními specifikátory formátu data a času změnou odpovídající <xref:System.Globalization.DateTimeFormatInfo> Vlastnosti. Například specifikátor formátu "ddd" přidá zkrácený název dne v týdnu nalezený v <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A> poli řetězců k výslednému řetězci. Podobně specifikátor formátu "MMMM" přidá do výsledného řetězce úplný název měsíce nalezený v poli <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A> řetězců.

## <a name="see-also"></a>Viz také

- <xref:System.DateTime?displayProperty=nameWithType>
- <xref:System.IFormatProvider?displayProperty=nameWithType>
- [Typy formátování](../../../docs/standard/base-types/formatting-types.md)
- [Řetězce standardního formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [Ukázka: nástroj formátování WinForms pro .NET Core (C#)](https://docs.microsoft.com/samples/dotnet/samples/windowsforms-formatting-utility-cs)
- [Ukázka: nástroj formátování WinForms pro .NET Core (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/windowsforms-formatting-utility-vb)
