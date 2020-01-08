---
title: Vlastní řetězce formátu TimeSpan
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- format specifiers, custom time interval
- format strings
- formatting [.NET Framework], time interval
- custom time interval format strings
- formatting [.NET Framework], time
- custom TimeSpan format strings
ms.assetid: a63ebf55-7269-416b-b4f5-286f6c03bf0e
ms.openlocfilehash: a5963f9afe422206627a1baea47339ecb81becf0
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348323"
---
# <a name="custom-timespan-format-strings"></a>Vlastní řetězce formátu TimeSpan

Řetězec formátu <xref:System.TimeSpan> definuje řetězcovou reprezentaci hodnoty <xref:System.TimeSpan>, která je výsledkem operace formátování. Vlastní formátovací řetězec se skládá z jednoho nebo více vlastních specifikátorů formátu <xref:System.TimeSpan> spolu s libovolným počtem literálních znaků. Libovolný řetězec, který není [standardním řetězcem formátu TimeSpan](standard-timespan-format-strings.md) , je interpretován jako řetězec formátu vlastního <xref:System.TimeSpan>.

> [!IMPORTANT]
> Specifikátory vlastního formátu <xref:System.TimeSpan> neobsahují zástupné symboly oddělovačů, jako jsou například symboly, které oddělují dny od hodin, hodin od minut nebo sekund od zlomků sekund. Místo toho je nutné tyto symboly zahrnout do vlastního řetězce formátu jako řetězcové literály. `"dd\.hh\:mm"` například definuje tečku (.) jako oddělovač mezi dny a hodiny a dvojtečku (:) jako oddělovač mezi hodinami a minutami.
>
> Vlastní specifikátory formátu <xref:System.TimeSpan> také nezahrnují symbol znaménka, který umožňuje odlišit záporné a kladné časové intervaly. Chcete-li zahrnout symbol znaménka, je nutné sestavit řetězec formátu pomocí podmíněné logiky. Část s [dalšími znaky](#other-characters) obsahuje příklad.

Řetězcové reprezentace hodnot <xref:System.TimeSpan> jsou vytvářeny voláním přetížení <xref:System.TimeSpan.ToString%2A?displayProperty=nameWithType> metody a metodami, které podporují složené formátování, jako je například <xref:System.String.Format%2A?displayProperty=nameWithType>. Další informace najdete v tématu [typy formátování](formatting-types.md) a [složené formátování](composite-formatting.md). Následující příklad ukazuje použití vlastních řetězců formátu při formátování operací.

[!code-csharp[Conceptual.TimeSpan.Custom#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customformatexample1.cs#1)]
[!code-vb[Conceptual.TimeSpan.Custom#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customformatexample1.vb#1)]

Vlastní řetězce formátu <xref:System.TimeSpan> jsou také používány metodami <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> a <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> k definování požadovaného formátu vstupních řetězců k analýze operací. (Analýza převede řetězcovou reprezentaci hodnoty na tuto hodnotu.) Následující příklad ilustruje použití standardního formátovacího řetězce při analýze operací.

[!code-csharp[Conceptual.TimeSpan.Custom#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customparseexample1.cs#2)]
[!code-vb[Conceptual.TimeSpan.Custom#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customparseexample1.vb#2)]

<a name="table"></a>Následující tabulka popisuje specifikátory vlastního formátu data a času.

| Specifikátor formátu | Popis | Příklad |
|----------------------|-----------------|-------------|
|"d", "% d"|Počet celých dnů v časovém intervalu.<br /><br /> Další informace: [Specifikátor vlastního formátu "d"](#dSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `%d` --> "6"<br /><br /> `d\.hh\:mm` --> "6.14:32"|
|"dd" – "dddddddd"|Počet celých dnů v časovém intervalu, doplněno počátečními nulami podle potřeby.<br /><br /> Další informace: [specifikátory "dd" – "dddddddd" vlastního formátu](#ddSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `ddd` --> "006"<br /><br /> `dd\.hh\:mm` --> "06.14:32"|
|"h", "% h"|Počet celých hodin v časovém intervalu, které se nepočítají jako součást dnů. Jednociferné číslo hodiny nemá počáteční nulu.<br /><br /> Další informace: [specifikátor "h" vlastního formátu](#hSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `%h` --> "14"<br /><br /> `hh\:mm` --> "14:32"|
|"hh"|Počet celých hodin v časovém intervalu, které se nepočítají jako součást dnů. Jednociferné číslo hodiny má počáteční nulu.<br /><br /> Další informace: [specifikátor "HH" vlastního formátu](#hhSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `hh` --> "14"<br /><br /> `new TimeSpan(6, 8, 32, 17, 685):`<br /><br /> `hh` --> 08|
|"m", "% m"|Počet celých minut v časovém intervalu, které nejsou zahrnuté jako součást hodin nebo dnů. Jednociferné číslo minut nemá počáteční nulu.<br /><br /> Další informace: [Specifikátor vlastního formátu "m"](#mSpecifier).|`new TimeSpan(6, 14, 8, 17, 685):`<br /><br /> `%m` --> "8"<br /><br /> `h\:m` --> "14:8"|
|"mm"|Počet celých minut v časovém intervalu, které nejsou zahrnuté jako součást hodin nebo dnů. Jednociferné číslo minut má počáteční nulu.<br /><br /> Další informace: [specifikátor "mm" vlastního formátu](#mmSpecifier).|`new TimeSpan(6, 14, 8, 17, 685):`<br /><br /> `mm` --> "08"<br /><br /> `new TimeSpan(6, 8, 5, 17, 685):`<br /><br /> `d\.hh\:mm\:ss` --> 6.08:05:17|
|"s", "% s"|Počet celých sekund v časovém intervalu, které nejsou zahrnuté jako součást hodin, dnů nebo minut. Jednociferné číslo sekund nemá počáteční nulu.<br /><br /> Další informace: [Specifikátor vlastního formátu "s"](#sSpecifier).|`TimeSpan.FromSeconds(12.965)`:<br /><br /> `%s` --> 12<br /><br /> `s\.fff` --> 12.965|
|"ss"|Počet celých sekund v časovém intervalu, které nejsou zahrnuté jako součást hodin, dnů nebo minut.  Jednociferné číslo sekund má počáteční nulu.<br /><br /> Další informace: [Specifikátor vlastního formátu "SS"](#ssSpecifier).|`TimeSpan.FromSeconds(6.965)`:<br /><br /> `ss` --> 06<br /><br /> `ss\.fff` --> 06.965|
|"f", "% f"|Desetiny sekundy v časovém intervalu.<br /><br /> Další informace: [specifikátor "f" vlastního formátu](#fSpecifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `f` --> 8<br /><br /> `ss\.f` --> 06.8|
|"ff"|Setiny sekundy v časovém intervalu.<br /><br /> Další informace: [specifikátor "FF" vlastního formátu](#ffSpecifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `ff` --> 89<br /><br /> `ss\.ff` --> 06.89|
|"fff"|Milisekundy v časovém intervalu.<br /><br /> Další informace: [specifikátor "fff" vlastního formátu](#f3Specifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `fff` --> 895<br /><br /> `ss\.fff` --> 06.895|
|"ffff"|Deset – sekundy sekundy v časovém intervalu.<br /><br /> Další informace: [Specifikátor vlastního formátu "FFFF"](#f4Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `ffff` --> 8954<br /><br /> `ss\.ffff` --> 06.8954|
|"fffff"|Set-sekundy sekundy v časovém intervalu.<br /><br /> Další informace: [Specifikátor vlastního formátu "fffff"](#f5Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `fffff` --> 89543<br /><br /> `ss\.fffff` --> 06.89543|
|"ffffff"|Desetimiliontiny sekundy v časovém intervalu.<br /><br /> Další informace: [Specifikátor vlastního formátu "FFFFFF"](#f6Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `ffffff` --> 895432<br /><br /> `ss\.ffffff` --> 06.895432|
|"fffffff"|Desítkový Desetimiliontiny sekundy (nebo zlomkové takty) v časovém intervalu.<br /><br /> Další informace: [Specifikátor vlastního formátu "fffffff"](#f7Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `fffffff` --> 8954321<br /><br /> `ss\.fffffff` --> 06.8954321|
|"F", "% F"|Desetiny sekundy v časovém intervalu. Pokud je číslice nula, nezobrazí se žádná hodnota.<br /><br /> Další informace: [specifikátor "F" vlastního formátu](#F_Specifier).|`TimeSpan.Parse("00:00:06.32")`:<br /><br /> `%F`: 3<br /><br /> `TimeSpan.Parse("0:0:3.091")`:<br /><br /> `ss\.F`: 03.|
|"FF"|Setiny sekundy v časovém intervalu. Nezahrnují se žádné zlomkové koncové nuly nebo dvě číslice nula.<br /><br /> Další informace: [specifikátor "FF" vlastního formátu](#FF_Specifier).|`TimeSpan.Parse("00:00:06.329")`:<br /><br /> `FF`: 32<br /><br /> `TimeSpan.Parse("0:0:3.101")`:<br /><br /> `ss\.FF`: 03.1|
|"FFF"|Milisekundy v časovém intervalu. Žádné zlomkové koncové nuly nejsou zahrnuty.<br /><br /> Další informace:|`TimeSpan.Parse("00:00:06.3291")`:<br /><br /> `FFF`: 329<br /><br /> `TimeSpan.Parse("0:0:3.1009")`:<br /><br /> `ss\.FFF`: 03.1|
|"FFFF"|Deset – sekundy sekundy v časovém intervalu. Žádné zlomkové koncové nuly nejsou zahrnuty.<br /><br /> Další informace: [Specifikátor vlastního formátu "FFFF"](#F4_Specifier).|`TimeSpan.Parse("00:00:06.32917")`:<br /><br /> `FFFFF`: 3291<br /><br /> `TimeSpan.Parse("0:0:3.10009")`:<br /><br /> `ss\.FFFF`: 03.1|
|"FFFFF"|Set-sekundy sekundy v časovém intervalu. Žádné zlomkové koncové nuly nejsou zahrnuty.<br /><br /> Další informace: [Specifikátor vlastního formátu "fffff"](#F5_Specifier).|`TimeSpan.Parse("00:00:06.329179")`:<br /><br /> `FFFFF`: 32917<br /><br /> `TimeSpan.Parse("0:0:3.100009")`:<br /><br /> `ss\.FFFFF`: 03.1|
|"FFFFFF"|Desetimiliontiny sekundy v časovém intervalu. Nezobrazí se žádné zlomkové koncové nuly.<br /><br /> Další informace: [Specifikátor vlastního formátu "FFFFFF"](#F6_Specifier).|`TimeSpan.Parse("00:00:06.3291791")`:<br /><br /> `FFFFFF`: 329179<br /><br /> `TimeSpan.Parse("0:0:3.1000009")`:<br /><br /> `ss\.FFFFFF`: 03.1|
|"FFFFFFF"|Deset milionů sekund v časovém intervalu. Nezobrazí se žádné zlomkové koncové nuly nebo sedm nul.<br /><br /> Další informace: [Specifikátor vlastního formátu "fffffff"](#F7_Specifier).|`TimeSpan.Parse("00:00:06.3291791")`:<br /><br /> `FFFFFF`: 3291791<br /><br /> `TimeSpan.Parse("0:0:3.1900000")`:<br /><br /> `ss\.FFFFFF`: 03.19|
|*řetězec "String*"|Oddělovač řetězcového literálu.<br /><br /> Další informace: [jiné znaky](#other-characters).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh':'mm':'ss` --> "14:32:17"|
|&#92;|Řídicí znak.<br /><br /> Další informace: [jiné znaky](#other-characters).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh\:mm\:ss` --> "14:32:17"|
|Jakýkoli jiný znak|Jakýkoli jiný znak bez řídicího znaku je interpretován jako specifikátor vlastního formátu.<br /><br /> Další informace: [jiné znaky](#other-characters).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh\:mm\:ss` --> "14:32:17"|

## <a name="dSpecifier"></a>Specifikátor vlastního formátu "d"

Specifikátor vlastního formátu "d" vypíše hodnotu vlastnosti <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType>, která představuje počet celých dnů v časovém intervalu. Výstupem je celý počet dnů ve <xref:System.TimeSpan> hodnotě, i když má hodnota více než jednu číslici. Pokud je hodnota vlastnosti <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> nula, výstup specifikátoru "0".

Pokud je specifikátor vlastního formátu "d" použit samostatně, zadejte "% d", aby nebyl špatně interpretován jako řetězec standardního formátu. V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.TimeSpan.Custom#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#3)]
[!code-vb[Conceptual.TimeSpan.Custom#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#3)]

Následující příklad ilustruje použití specifikátoru vlastního formátu "d".

[!code-csharp[Conceptual.TimeSpan.Custom#4](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#4)]
[!code-vb[Conceptual.TimeSpan.Custom#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#4)]

[Zpět na tabulku](#table)

## <a name="ddSpecifier"></a>Specifikátory vlastního formátu "dd"-"dddddddd"

Specifikátor vlastního formátu "dd", "ddd", "dddd", "ddddd", "DDDDDD", "ddddddd" a "dddddddd" mají výstup hodnoty vlastnosti <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType>, která představuje počet celých dnů v časovém intervalu.

Výstupní řetězec obsahuje minimální počet číslic určený počtem "d" znaků ve specifikátoru formátu a je doplněn počátečními nulami podle potřeby. Pokud číslice v počtu dní překročí počet znaků "d" ve specifikátoru formátu, je celý počet dní výstup ve výsledném řetězci.

Následující příklad používá tyto specifikátory formátu k zobrazení řetězcové reprezentace dvou hodnot <xref:System.TimeSpan>. Hodnota komponenty dní v prvním časovém intervalu je nulová. hodnota složky dní druhé hodnoty je 365.

[!code-csharp[Conceptual.TimeSpan.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#5)]
[!code-vb[Conceptual.TimeSpan.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#5)]

[Zpět na tabulku](#table)

## <a name="hSpecifier"></a>Specifikátor vlastního formátu "h"

Specifikátor vlastního formátu "h" vypíše hodnotu vlastnosti <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType>, která představuje počet celých hodin v časovém intervalu, který není počítán jako součást jeho komponenty Day. Vrátí jednociferné číslo řetězce, pokud je hodnota vlastnosti <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> 0 až 9 a vrátí hodnotu řetězce se dvěma číslicemi, pokud je hodnota vlastnosti <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> od 10 do 23.

Pokud je specifikátor vlastního formátu "h" použit samostatně, zadejte "% h" tak, že není špatně interpretován jako řetězec standardního formátu. V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.TimeSpan.Custom#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#6)]
[!code-vb[Conceptual.TimeSpan.Custom#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#6)]

V rámci operace analýzy obvykle je vstupní řetězec, který obsahuje pouze jedno číslo, interpretován jako počet dní. Pomocí specifikátoru vlastního formátu "% h" můžete místo toho interpretovat číselný řetězec jako počet hodin. V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.TimeSpan.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#8)]
[!code-vb[Conceptual.TimeSpan.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#8)]

Následující příklad ilustruje použití specifikátoru vlastního formátu "h".

[!code-csharp[Conceptual.TimeSpan.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#7)]
[!code-vb[Conceptual.TimeSpan.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#7)]

[Zpět na tabulku](#table)

## <a name="hhSpecifier"></a>Specifikátor vlastního formátu "HH"

Specifikátor vlastního formátu "HH" vypíše hodnotu vlastnosti <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType>, která představuje počet celých hodin v časovém intervalu, který není počítán jako součást jeho komponenty Day. V případě hodnot od 0 do 9 obsahuje výstupní řetězec úvodní nuly.

V rámci operace analýzy obvykle je vstupní řetězec, který obsahuje pouze jedno číslo, interpretován jako počet dní. Místo toho můžete použít Specifikátor vlastního formátu "HH" k interpretaci číselného řetězce jako počet hodin. V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.TimeSpan.Custom#9](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#9)]
[!code-vb[Conceptual.TimeSpan.Custom#9](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#9)]

Následující příklad ilustruje použití specifikátoru vlastního formátu "HH".

[!code-csharp[Conceptual.TimeSpan.Custom#10](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#10)]
[!code-vb[Conceptual.TimeSpan.Custom#10](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#10)]

[Zpět na tabulku](#table)

## <a name="mSpecifier"></a>Specifikátor vlastního formátu "m"

Specifikátor vlastního formátu "m" vypíše hodnotu vlastnosti <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType>, která představuje počet celých minut v časovém intervalu, který není počítán jako součást jeho komponenty Day. Vrátí jednociferné číslo řetězce, pokud je hodnota vlastnosti <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> 0 až 9 a vrátí hodnotu řetězce s dvojnásobnou hodnotou, pokud je hodnota vlastnosti <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> rozsahu od 10 do 59.

Pokud je specifikátor vlastního formátu "m" použit samostatně, zadejte "% m" tak, že není špatně interpretován jako standardní formátovací řetězec. V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.TimeSpan.Custom#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#6)]
[!code-vb[Conceptual.TimeSpan.Custom#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#6)]

V rámci operace analýzy obvykle je vstupní řetězec, který obsahuje pouze jedno číslo, interpretován jako počet dní. Místo toho můžete pomocí specifikátoru vlastního formátu "% m" interpretovat číselný řetězec jako počet minut. V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.TimeSpan.Custom#11](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#11)]
[!code-vb[Conceptual.TimeSpan.Custom#11](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#11)]

Následující příklad ilustruje použití specifikátoru vlastního formátu "m".

[!code-csharp[Conceptual.TimeSpan.Custom#12](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#12)]
[!code-vb[Conceptual.TimeSpan.Custom#12](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#12)]

[Zpět na tabulku](#table)

## <a name="mmSpecifier"></a>Specifikátor vlastního formátu "mm"

Specifikátor vlastního formátu "mm" vyprodukuje hodnotu vlastnosti <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType>, která představuje počet celých minut v časovém intervalu, který není zahrnutý jako součást jeho hodin nebo dnů. V případě hodnot od 0 do 9 obsahuje výstupní řetězec úvodní nuly.

V rámci operace analýzy obvykle je vstupní řetězec, který obsahuje pouze jedno číslo, interpretován jako počet dní. Místo toho můžete použít Specifikátor vlastního formátu "mm" k interpretaci číselného řetězce jako počet minut. V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.TimeSpan.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#13)]
[!code-vb[Conceptual.TimeSpan.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#13)]

Následující příklad ilustruje použití specifikátoru vlastního formátu "mm".

[!code-csharp[Conceptual.TimeSpan.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#14)]
[!code-vb[Conceptual.TimeSpan.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#14)]

[Zpět na tabulku](#table)

## <a name="sSpecifier"></a>Specifikátor vlastního formátu "s"

Specifikátor vlastního formátu "s" obsahuje hodnotu vlastnosti <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType>, která představuje počet celých sekund v časovém intervalu, který není zahrnutý jako součást jeho hodin, dnů nebo minut. Vrátí jednociferné číslo řetězce, pokud je hodnota vlastnosti <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> 0 až 9 a vrátí hodnotu řetězce s dvojnásobnou hodnotou, pokud je hodnota vlastnosti <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> rozsahu od 10 do 59.

Pokud je specifikátor vlastního formátu "s" použit samostatně, zadejte "% s", aby nebyl špatně interpretován jako řetězec standardního formátu. V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.TimeSpan.Custom#15](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#15)]
[!code-vb[Conceptual.TimeSpan.Custom#15](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#15)]

V rámci operace analýzy obvykle je vstupní řetězec, který obsahuje pouze jedno číslo, interpretován jako počet dní. Pomocí specifikátoru vlastního formátu "% s" můžete místo toho interpretovat číselný řetězec jako počet sekund. V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.TimeSpan.Custom#17](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#17)]
[!code-vb[Conceptual.TimeSpan.Custom#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#17)]

Následující příklad ilustruje použití specifikátoru vlastního formátu "s".

[!code-csharp[Conceptual.TimeSpan.Custom#16](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#16)]
[!code-vb[Conceptual.TimeSpan.Custom#16](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#16)]

[Zpět na tabulku](#table)

## <a name="ssSpecifier"></a>Specifikátor vlastního formátu "SS"

Specifikátor vlastního formátu "SS" vypíše hodnotu vlastnosti <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType>, která představuje počet celých sekund v časovém intervalu, který není zahrnutý jako součást své hodiny, dny nebo minuty. V případě hodnot od 0 do 9 obsahuje výstupní řetězec úvodní nuly.

V rámci operace analýzy obvykle je vstupní řetězec, který obsahuje pouze jedno číslo, interpretován jako počet dní. Specifikátor vlastního formátu "SS" můžete použít místo toho k interpretaci číselného řetězce jako počtu sekund. V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.TimeSpan.Custom#18](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#18)]
[!code-vb[Conceptual.TimeSpan.Custom#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#18)]

Následující příklad ilustruje použití specifikátoru vlastního formátu "SS".

[!code-csharp[Conceptual.TimeSpan.Custom#19](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#19)]
[!code-vb[Conceptual.TimeSpan.Custom#19](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#19)]

[Zpět na tabulku](#table)

## <a name="fSpecifier"></a>Specifikátor vlastního formátu "f"

Specifikátor vlastního formátu "f" vyprodukuje desetiny sekundy v časovém intervalu. V operaci formátování se zkrátí zbývající zlomkové číslice. V operaci analýzy, která volá metodu <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, musí vstupní řetězec obsahovat právě jednu zlomkovou číslici.

Pokud specifikátor vlastního formátu "f" použijete samostatně, zadejte "% f", takže není špatně interpretován jako standardní formátovací řetězec.

Následující příklad používá specifikátor vlastního formátu "f" k zobrazení desetiny sekundy ve <xref:System.TimeSpan> hodnotě. "f" se používá jako jediný specifikátor formátu a v kombinaci se specifikátorem "s" ve vlastním formátovacím řetězci.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Zpět na tabulku](#table)

## <a name="ffSpecifier"></a>Specifikátor vlastního formátu "FF"

Specifikátor vlastního formátu "FF" vyprodukuje setiny sekundy v časovém intervalu. V operaci formátování se zkrátí zbývající zlomkové číslice. V operaci analýzy, která volá metodu <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, musí vstupní řetězec obsahovat přesně dvě zlomkové číslice.

Následující příklad používá specifikátor vlastního formátu "FF" pro zobrazení setiny sekundy ve <xref:System.TimeSpan> hodnotě. "FF" se používá jako jediný specifikátor formátu a v kombinaci se specifikátorem "s" ve vlastním formátovacím řetězci.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Zpět na tabulku](#table)

## <a name="f3Specifier"></a>Specifikátor vlastního formátu "fff"

Specifikátor vlastního formátu "fff" (se třemi "f" znaky) vytvoří výstup milisekund v časovém intervalu. V operaci formátování se zkrátí zbývající zlomkové číslice. V operaci analýzy, která volá metodu <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, musí vstupní řetězec obsahovat přesně tři zlomkové číslice.

Následující příklad používá specifikátor vlastního formátu "fff" k zobrazení milisekund v hodnotě <xref:System.TimeSpan>. "fff" se používá jako jediný specifikátor formátu a v kombinaci se specifikátorem "s" ve vlastním formátovacím řetězci.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Zpět na tabulku](#table)

## <a name="f4Specifier"></a>Specifikátor vlastního formátu "FFFF"

Specifikátor vlastního formátu "FFFF" (se čtyřmi znaky "f") vytvoří výstup deseti sekundy sekundy v časovém intervalu. V operaci formátování se zkrátí zbývající zlomkové číslice. V operaci analýzy, která volá metodu <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, musí vstupní řetězec obsahovat přesně čtyři zlomkové číslice.

Následující příklad používá specifikátor vlastního formátu "FFFF" pro zobrazení deseti sekundy sekundy ve <xref:System.TimeSpan> hodnotě. "FFFF" se používá jako jediný specifikátor formátu a v kombinaci se specifikátorem "s" ve vlastním formátovacím řetězci.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Zpět na tabulku](#table)

## <a name="f5Specifier"></a>Specifikátor vlastního formátu "fffff"

Specifikátor vlastního formátu "fffff" (s pěti znaky "f") zapisuje stovky-sekundy sekundy v časovém intervalu. V operaci formátování se zkrátí zbývající zlomkové číslice. V operaci analýzy, která volá metodu <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, musí vstupní řetězec obsahovat přesně pět zlomkových číslic.

Následující příklad používá specifikátor vlastního formátu "fffff" pro zobrazení hodnoty set-sekundy sekundy ve <xref:System.TimeSpan> hodnotě. "fffff" slouží jako první specifikátor formátu a v kombinaci se specifikátorem "s" v řetězci vlastního formátu.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Zpět na tabulku](#table)

## <a name="f6Specifier"></a>Specifikátor vlastního formátu "FFFFFF"

Specifikátor vlastního formátu "FFFFFF" (obsahující šest znaků f) výstupuje Desetimiliontiny sekundy v časovém intervalu. V operaci formátování se zkrátí zbývající zlomkové číslice. V operaci analýzy, která volá metodu <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, musí vstupní řetězec obsahovat přesně šest zlomkových číslic.

V následujícím příkladu je použit Specifikátor vlastního formátu "FFFFFF" pro zobrazení Desetimiliontiny sekundy v hodnotě <xref:System.TimeSpan>. Slouží jako první specifikátor formátu a v kombinaci se specifikátorem "s" ve vlastním formátovacím řetězci.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Zpět na tabulku](#table)

## <a name="f7Specifier"></a>Specifikátor vlastního formátu "fffffff"

Specifikátor vlastního formátu "fffffff" (se sedmi "f" znaky) vytvoří výstup deseti Desetimiliontiny sekundy (nebo desetinné číslo tiků) v časovém intervalu. V operaci analýzy, která volá metodu <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, musí vstupní řetězec obsahovat přesně sedm zlomkových číslic.

Následující příklad používá specifikátor vlastního formátu "fffffff" pro zobrazení desetinného počtu tiků v <xref:System.TimeSpan> hodnotě. Slouží jako první specifikátor formátu a v kombinaci se specifikátorem "s" ve vlastním formátovacím řetězci.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Zpět na tabulku](#table)

## <a name="F_Specifier"></a>Specifikátor vlastního formátu "F"

Specifikátor vlastního formátu "F" vyprodukuje desetiny sekundy v časovém intervalu. V operaci formátování se zkrátí zbývající zlomkové číslice. Pokud je hodnota počtu desetin časových intervalů sekundy nula, není součástí výsledného řetězce. V operaci analýzy, která volá metodu <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, je přítomnost desetin druhé číslice volitelná.

Pokud specifikátor vlastního formátu "F" použijete samostatně, zadejte "% F", takže není špatně interpretován jako standardní formátovací řetězec.

Následující příklad používá specifikátor vlastního formátu "F" k zobrazení desetiny sekundy ve <xref:System.TimeSpan> hodnotě. Používá také tento vlastní specifikátor formátu v operaci analýzy.

[!code-csharp[Conceptual.TimeSpan.Custom#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#21)]
[!code-vb[Conceptual.TimeSpan.Custom#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#21)]

[Zpět na tabulku](#table)

## <a name="FF_Specifier"></a>Specifikátor vlastního formátu "FF"

Specifikátor vlastního formátu "FF" vyprodukuje setiny sekundy v časovém intervalu. V operaci formátování se zkrátí zbývající zlomkové číslice. Pokud jsou žádné koncové zlomky nula, nejsou zahrnuty ve výsledném řetězci. V operaci analýzy, která volá metodu <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, je přítomnost desátého a setiny druhé číslice volitelná.

Následující příklad používá specifikátor vlastního formátu "FF" pro zobrazení setiny sekundy ve <xref:System.TimeSpan> hodnotě. Používá také tento vlastní specifikátor formátu v operaci analýzy.

[!code-csharp[Conceptual.TimeSpan.Custom#22](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#22)]
[!code-vb[Conceptual.TimeSpan.Custom#22](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#22)]

[Zpět na tabulku](#table)

## <a name="F3_Specifier"></a>Specifikátor vlastního formátu "FFF"

Specifikátor vlastního formátu "FFF" (se třemi "F" znaky) vytvoří výstup milisekund v časovém intervalu. V operaci formátování se zkrátí zbývající zlomkové číslice. Pokud jsou žádné koncové zlomky nula, nejsou zahrnuty ve výsledném řetězci. V operaci analýzy, která volá metodu <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, je přítomnost desetin, setinách a sekundy druhé číslice volitelná.

Následující příklad používá specifikátor vlastního formátu "FFF" pro zobrazení sekundy sekundy v hodnotě <xref:System.TimeSpan>. Používá také tento vlastní specifikátor formátu v operaci analýzy.

[!code-csharp[Conceptual.TimeSpan.Custom#23](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#23)]
[!code-vb[Conceptual.TimeSpan.Custom#23](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#23)]

[Zpět na tabulku](#table)

## <a name="F4_Specifier"></a>Specifikátor vlastního formátu "FFFF"

Specifikátor vlastního formátu "FFFF" (se čtyřmi znaky "F") vytvoří výstup deseti sekundy sekundy v časovém intervalu. V operaci formátování se zkrátí zbývající zlomkové číslice. Pokud jsou žádné koncové zlomky nula, nejsou zahrnuty ve výsledném řetězci. V operaci analýzy, která volá metodu <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, je přítomnost desetin, setinách, sekundy a desíti-sekundy druhé číslice volitelná.

Následující příklad používá specifikátor vlastního formátu "FFFF" pro zobrazení deseti sekundy sekundy ve <xref:System.TimeSpan> hodnotě. Používá také specifikátor vlastního formátu "FFFF" v operaci analýzy.

[!code-csharp[Conceptual.TimeSpan.Custom#24](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#24)]
[!code-vb[Conceptual.TimeSpan.Custom#24](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#24)]

[Zpět na tabulku](#table)

## <a name="F5_Specifier"></a>Specifikátor vlastního formátu "FFFFF"

Specifikátor vlastního formátu "FFFFF" (s pěti znaky "F") zapisuje stovky-sekundy sekundy v časovém intervalu. V operaci formátování se zkrátí zbývající zlomkové číslice. Pokud jsou žádné koncové zlomky nula, nejsou zahrnuty ve výsledném řetězci. V operaci analýzy, která volá metodu <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, je přítomnost desetin, setinách, sekundy, deseti sekundy a stě-sekundy druhé číslice volitelná.

Následující příklad používá specifikátor vlastního formátu "FFFFF" pro zobrazení hodnoty set-sekundy sekundy ve <xref:System.TimeSpan> hodnotě. Používá také specifikátor vlastního formátu "FFFFF" v operaci analýzy.

[!code-csharp[Conceptual.TimeSpan.Custom#25](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#25)]
[!code-vb[Conceptual.TimeSpan.Custom#25](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#25)]

[Zpět na tabulku](#table)

## <a name="F6_Specifier"></a>Specifikátor vlastního formátu "FFFFFF"

Specifikátor vlastního formátu "FFFFFF" (obsahující šest znaků F) výstupuje Desetimiliontiny sekundy v časovém intervalu. V operaci formátování se zkrátí zbývající zlomkové číslice. Pokud jsou žádné koncové zlomky nula, nejsou zahrnuty ve výsledném řetězci. V operaci analýzy, která volá metodu <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, je jako volitelná existence desátých, setinách, sekundy, deseti-sekundy, stě-sekundy a Desetimiliontiny druhé číslice.

V následujícím příkladu je použit Specifikátor vlastního formátu "FFFFFF" pro zobrazení Desetimiliontiny sekundy v hodnotě <xref:System.TimeSpan>. Používá také tento vlastní specifikátor formátu v operaci analýzy.

[!code-csharp[Conceptual.TimeSpan.Custom#26](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#26)]
[!code-vb[Conceptual.TimeSpan.Custom#26](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#26)]

[Zpět na tabulku](#table)

## <a name="F7_Specifier"></a>Specifikátor vlastního formátu "FFFFFFF"

Specifikátor vlastního formátu "FFFFFFF" (se sedmi "F" znaky) vytvoří výstup deseti Desetimiliontiny sekundy (nebo desetinné číslo tiků) v časovém intervalu. Pokud jsou žádné koncové zlomky nula, nejsou zahrnuty ve výsledném řetězci. V operaci analýzy, která volá metodu <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType>, je přítomnost sedmi zlomkových číslic ve vstupním řetězci volitelná.

Následující příklad používá specifikátor vlastního formátu "FFFFFFF" pro zobrazení zlomkových částí sekundy ve <xref:System.TimeSpan> hodnotě. Používá také tento vlastní specifikátor formátu v operaci analýzy.

[!code-csharp[Conceptual.TimeSpan.Custom#27](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#27)]
[!code-vb[Conceptual.TimeSpan.Custom#27](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#27)]

[Zpět na tabulku](#table)

## <a name="other-characters"></a>Jiné znaky

Jakýkoli jiný znak bez řídicího znaku ve formátovacím řetězci, včetně prázdného znaku, je interpretován jako specifikátor vlastního formátu. Ve většině případů přítomnost jakéhokoli jiného neřídicího znaku má za následek <xref:System.FormatException>.

Existují dva způsoby, jak zahrnout literální znak do formátovacího řetězce:

- Uzavřete ho do jednoduchých uvozovek (literální řetězcový oddělovač).

- Před něj uveďte zpětné lomítko ("\\"), které je interpretováno jako řídicí znak. To znamená, že v C#nástroji musí být formátovací řetězec buď @-quoted, nebo znak literálu musí předcházet další zpětné lomítko.

  V některých případech může být nutné použít podmíněnou logiku pro zahrnutí řídicího literálu do řetězce formátu. V následujícím příkladu je použita podmíněná logika pro zahrnutí symbol znaménka pro záporné časové intervaly.

  [!code-csharp[Conceptual.TimeSpan.Custom#29](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/negativevalues1.cs#29)]
  [!code-vb[Conceptual.TimeSpan.Custom#29](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/negativevalues1.vb#29)]

.NET nedefinuje gramatiku pro oddělovače v časových intervalech. To znamená, že oddělovače mezi dny a hodiny, hodiny a minuty, minuty a sekundy a sekundy a zlomky sekund musí být zpracovány jako znakové literály v řetězci formátu.

Následující příklad používá řídicí znak i jednoduchou uvozovku k definování vlastního formátovacího řetězce, který obsahuje slovo "minuty" ve výstupním řetězci.

[!code-csharp[Conceptual.TimeSpan.Custom#28](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/literal1.cs#28)]
[!code-vb[Conceptual.TimeSpan.Custom#28](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/literal1.vb#28)]

[Zpět na tabulku](#table)

## <a name="see-also"></a>Viz také:

- [Typy formátování](formatting-types.md)
- [Standardní řetězce formátu TimeSpan](standard-timespan-format-strings.md)
