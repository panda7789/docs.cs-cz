---
title: Vlastní formátovací řetězce TimeSpan
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75348323"
---
# <a name="custom-timespan-format-strings"></a>Vlastní formátovací řetězce TimeSpan

Formátovací <xref:System.TimeSpan> řetězec definuje řetězcovou <xref:System.TimeSpan> reprezentaci hodnoty, která je výsledkem operace formátování. Vlastní formátovací řetězec se skládá <xref:System.TimeSpan> z jednoho nebo více vlastních specifikátorů formátu spolu s libovolným počtem literálových znaků. Libovolný řetězec, který není [formátovací řetězec Standard TimeSpan,](standard-timespan-format-strings.md) je interpretován jako vlastní <xref:System.TimeSpan> formátovací řetězec.

> [!IMPORTANT]
> Vlastní <xref:System.TimeSpan> specifikátory formátu neobsahují zástupné oddělovací symboly, například symboly, které oddělují dny od hodin, hodin od minut nebo sekund od zlomkových sekund. Místo toho tyto symboly musí být zahrnuty ve vlastním řetězci formátu jako literály řetězce. Například `"dd\.hh\:mm"` definuje tečku (.) jako oddělovač mezi dny a hodinami a dvojtečku (:) jako separátor mezi hodinami a minutami.
>
> Vlastní <xref:System.TimeSpan> specifikátory formátu také neobsahují symbol znaménku, který umožňuje rozlišovat mezi negativními a kladnýmčasovými intervaly. Chcete-li zahrnout symbol znaménku, musíte vytvořit formátovací řetězec pomocí podmíněné logiky. Sekce [Další znaky](#other-characters) obsahuje příklad.

Řetězcové reprezentace <xref:System.TimeSpan> hodnot jsou vytvářeny voláním <xref:System.TimeSpan.ToString%2A?displayProperty=nameWithType> přetížení metody a metodami, které podporují <xref:System.String.Format%2A?displayProperty=nameWithType>složené formátování, například . Další informace naleznete [v tématu Typy formátování](formatting-types.md) a Složené [formátování](composite-formatting.md). Následující příklad ilustruje použití vlastních formátovacích řetězců při operacích formátování.

[!code-csharp[Conceptual.TimeSpan.Custom#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customformatexample1.cs#1)]
[!code-vb[Conceptual.TimeSpan.Custom#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customformatexample1.vb#1)]

Vlastní <xref:System.TimeSpan> formátovací řetězce jsou <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> také <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> používány a metody k definování požadovaného formátu vstupních řetězců pro analýzu operací. (Analýza převede řetězcovou reprezentaci hodnoty na tuto hodnotu.) Následující příklad ilustruje použití standardních formátovacích řetězců v operacích analýzy.

[!code-csharp[Conceptual.TimeSpan.Custom#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customparseexample1.cs#2)]
[!code-vb[Conceptual.TimeSpan.Custom#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customparseexample1.vb#2)]

<a name="table"></a>Následující tabulka popisuje vlastní specifikátory formátu data a času.

| Specifikátor formátu | Popis | Příklad |
|----------------------|-----------------|-------------|
|"d", "%d"|Počet celých dnů v časovém intervalu.<br /><br /> Další informace: [Vlastní specifikátor formátu "d"](#dSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `%d`--> "6"<br /><br /> `d\.hh\:mm`--> "6.14:32"|
|"dd"-"dddddddd"|Počet celých dnů v časovém intervalu, doplněný úvodními nulami podle potřeby.<br /><br /> Další informace: [Vlastní specifikátory formátu "dd"-"ddddddd"](#ddSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `ddd`--> "006"<br /><br /> `dd\.hh\:mm`--> "06.14:32"|
|"h", "%h"|Počet celých hodin v časovém intervalu, které se nepočítají jako součást dnů. Jednociferné hodiny nemají úvodní nulu.<br /><br /> Další informace: [Vlastní specifikátor formátu "h"](#hSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `%h`--> "14"<br /><br /> `hh\:mm`--> "14:32"|
|"hh"|Počet celých hodin v časovém intervalu, které se nepočítají jako součást dnů. Jednociferné hodiny mají počáteční nulu.<br /><br /> Další informace: [Vlastní specifikátor formátu "hh"](#hhSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `hh`--> "14"<br /><br /> `new TimeSpan(6, 8, 32, 17, 685):`<br /><br /> `hh`--> 08|
|"m", "%m"|Počet celých minut v časovém intervalu, které nejsou zahrnuty jako součást hodin nebo dnů. Jednociferné minuty nemají úvodní nulu.<br /><br /> Další informace: [Vlastní specifikátor formátu "m"](#mSpecifier).|`new TimeSpan(6, 14, 8, 17, 685):`<br /><br /> `%m`--> "8"<br /><br /> `h\:m`--> "14:8"|
|"mm"|Počet celých minut v časovém intervalu, které nejsou zahrnuty jako součást hodin nebo dnů. Jednociferné minuty mají počáteční nulu.<br /><br /> Další informace: [Vlastní specifikátor formátu "mm"](#mmSpecifier).|`new TimeSpan(6, 14, 8, 17, 685):`<br /><br /> `mm`--> "08"<br /><br /> `new TimeSpan(6, 8, 5, 17, 685):`<br /><br /> `d\.hh\:mm\:ss`--> 6.08:05:17.|
|"s", "%s"|Počet celých sekund v časovém intervalu, které nejsou zahrnuty jako součást hodin, dnů nebo minut. Jednociferné sekundy nemají úvodní nulu.<br /><br /> Další informace: [Vlastní specifikátor formátu "s"](#sSpecifier).|`TimeSpan.FromSeconds(12.965)`:<br /><br /> `%s`--> 12.<br /><br /> `s\.fff`--> 12.965.|
|"ss"|Počet celých sekund v časovém intervalu, které nejsou zahrnuty jako součást hodin, dnů nebo minut.  Jednociferné sekundy mají počáteční nulu.<br /><br /> Další informace: [Vlastní specifikátor formátu "ss"](#ssSpecifier).|`TimeSpan.FromSeconds(6.965)`:<br /><br /> `ss`--> 06<br /><br /> `ss\.fff`--> 6.965.|
|"f", "%f"|Desetiny sekundy v časovém intervalu.<br /><br /> Další informace: [Vlastní specifikátor formátu "f"](#fSpecifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `f`--> 8<br /><br /> `ss\.f`--> 06,8.|
|"ff"|Setiny sekundy v časovém intervalu.<br /><br /> Další informace: [Vlastní specifikátor formátu "ff"](#ffSpecifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `ff`--> 89.<br /><br /> `ss\.ff`--> 6,89 .|
|"fff"|Milisekundy v časovém intervalu.<br /><br /> Další informace: [Vlastní specifikátor formátu "fff"](#f3Specifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `fff`--> 895.<br /><br /> `ss\.fff`--> 6.895.|
|"ffff"|Deset tisícin sekundy v časovém intervalu.<br /><br /> Další informace: [Vlastní specifikátor formátu ffff](#f4Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `ffff`--> 8954.<br /><br /> `ss\.ffff`--> 6.8954.|
|"fffff"|Sto tisícin sekundy v časovém intervalu.<br /><br /> Další informace: [Vlastní specifikátor formátu "fffff"](#f5Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `fffff`--> 89543<br /><br /> `ss\.fffff`--> 06.89543|
|"ffffff"|Miliontiny sekundy v časovém intervalu.<br /><br /> Další informace: [Vlastní specifikátor formátu ffffff](#f6Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `ffffff`--> 895432<br /><br /> `ss\.ffffff`--> 06.895432|
|"fffffff"|Deset miliontin sekundy (nebo zlomkové klíšťata) v časovém intervalu.<br /><br /> Další informace: [Vlastní specifikátor formátu fffffff](#f7Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `fffffff`--> 8954321<br /><br /> `ss\.fffffff`--> 06.8954321|
|"F", "%F"|Desetiny sekundy v časovém intervalu. Pokud je číslice nula, nezobrazí se žádná hodnota.<br /><br /> Další informace: [Vlastní specifikátor formátu "F"](#F_Specifier).|`TimeSpan.Parse("00:00:06.32")`:<br /><br /> `%F`: 3<br /><br /> `TimeSpan.Parse("0:0:3.091")`:<br /><br /> `ss\.F`: 03.|
|"FF"|Setiny sekundy v časovém intervalu. Nejsou zahrnuty žádné zlomkové koncové nuly nebo dvě nulová číslice.<br /><br /> Další informace: [Vlastní specifikátor formátu "FF"](#FF_Specifier).|`TimeSpan.Parse("00:00:06.329")`:<br /><br /> `FF`: 32<br /><br /> `TimeSpan.Parse("0:0:3.101")`:<br /><br /> `ss\.FF`: 03.1|
|"FFF"|Milisekundy v časovém intervalu. Žádné zlomkové koncové nuly nejsou zahrnuty.<br /><br /> Další informace:|`TimeSpan.Parse("00:00:06.3291")`:<br /><br /> `FFF`: 329<br /><br /> `TimeSpan.Parse("0:0:3.1009")`:<br /><br /> `ss\.FFF`: 03.1|
|"FFFF"|Deset tisícin sekundy v časovém intervalu. Žádné zlomkové koncové nuly nejsou zahrnuty.<br /><br /> Další informace: [Vlastní specifikátor formátu FFFF](#F4_Specifier).|`TimeSpan.Parse("00:00:06.32917")`:<br /><br /> `FFFFF`: 3291<br /><br /> `TimeSpan.Parse("0:0:3.10009")`:<br /><br /> `ss\.FFFF`: 03.1|
|"FFFFF"|Sto tisícin sekundy v časovém intervalu. Žádné zlomkové koncové nuly nejsou zahrnuty.<br /><br /> Další informace: [Vlastní specifikátor formátu FFFFF](#F5_Specifier).|`TimeSpan.Parse("00:00:06.329179")`:<br /><br /> `FFFFF`: 32917<br /><br /> `TimeSpan.Parse("0:0:3.100009")`:<br /><br /> `ss\.FFFFF`: 03.1|
|"FFFFFF"|Miliontiny sekundy v časovém intervalu. Nejsou zobrazeny žádné zlomkové koncové nuly.<br /><br /> Další informace: [Vlastní specifikátor formátu FFFFFF](#F6_Specifier).|`TimeSpan.Parse("00:00:06.3291791")`:<br /><br /> `FFFFFF`: 329179<br /><br /> `TimeSpan.Parse("0:0:3.1000009")`:<br /><br /> `ss\.FFFFFF`: 03.1|
|"FFFFFFF"|Deset milionů sekundy v časovém intervalu. Nejsou zobrazeny žádné zlomkové koncové nuly nebo sedm nul.<br /><br /> Další informace: [Vlastní specifikátor formátu FFFFFFF](#F7_Specifier).|`TimeSpan.Parse("00:00:06.3291791")`:<br /><br /> `FFFFFF`: 3291791<br /><br /> `TimeSpan.Parse("0:0:3.1900000")`:<br /><br /> `ss\.FFFFFF`: 03.19|
|'*řetězec*'|Oddělovač řetězcového literálu.<br /><br /> Další informace: [Další znaky](#other-characters).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh':'mm':'ss`--> "14:32:17"|
|&#92;|Řídicí znak.<br /><br /> Další informace: [Další znaky](#other-characters).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh\:mm\:ss`--> "14:32:17"|
|Jakýkoli jiný znak|Jakýkoli jiný neuvozený znak je interpretován jako vlastní specifikátor formátu.<br /><br /> Další informace: [Další znaky](#other-characters).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh\:mm\:ss`--> "14:32:17"|

## <a name="dSpecifier"></a>Vlastní specifikátor formátu "d"

Vlastní specifikátor formátu "d" vyvodí hodnotu <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> vlastnosti, která představuje počet celých dnů v časovém intervalu. Výstupy celý počet dní v <xref:System.TimeSpan> hodnotě, i v případě, že hodnota má více než jednu číslici. Pokud je hodnota <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> vlastnosti nulová, specifikátor vydělá "0".

Pokud je vlastní specifikátor formátu "d" použit samostatně, zadejte "%d", aby nebyl nesprávně interpretován jako standardní formátovací řetězec. V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.TimeSpan.Custom#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#3)]
[!code-vb[Conceptual.TimeSpan.Custom#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#3)]

Následující příklad ilustruje použití vlastního specifikátoru formátu "d".

[!code-csharp[Conceptual.TimeSpan.Custom#4](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#4)]
[!code-vb[Conceptual.TimeSpan.Custom#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#4)]

[Zpět na stůl](#table)

## <a name="ddSpecifier"></a>Vlastní specifikátory formátu "dd"-"dddddddd"

Vlastní specifikátory formátu "dd", "dddd", "ddddd", "ddddd", "ddddddd" a "dddddddd" vlastní specifikátory formátu vyhotovují hodnotu <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> vlastnosti, která představuje počet celých dnů v časovém intervalu.

Výstupní řetězec obsahuje minimální počet číslic určený počtem znaků "d" v specifikátoru formátu a je podle potřeby doplněn počátečními nulami. Pokud číslice v počtu dní překročí počet znaků "d" v specifikátoru formátu, je ve výsledném řetězci výstup emitovaný celý počet dní.

Následující příklad používá tyto specifikátory formátu k <xref:System.TimeSpan> zobrazení řetězcové reprezentace dvou hodnot. Hodnota složky days prvního časového intervalu je nulová; hodnota složky dnů druhé je 365.

[!code-csharp[Conceptual.TimeSpan.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#5)]
[!code-vb[Conceptual.TimeSpan.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#5)]

[Zpět na stůl](#table)

## <a name="hSpecifier"></a>Vlastní specifikátor formátu "h"

Vlastní specifikátor formátu "h" vyvodí hodnotu <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> vlastnosti, která představuje počet celých hodin v časovém intervalu, který se nepočítá jako součást jeho denní součásti. Vrátí hodnotu jednomístného řetězce, pokud <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> je hodnota vlastnosti 0 až 9, a vrátí dvoumístnou řetězcovou hodnotu, pokud se hodnota <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> vlastnosti pohybuje od 10 do 23.

Pokud je vlastní specifikátor formátu "h" použit samostatně, zadejte %h, aby nebyl nesprávně interpretován jako standardní formátovací řetězec. V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.TimeSpan.Custom#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#6)]
[!code-vb[Conceptual.TimeSpan.Custom#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#6)]

Obvykle v operaci analýzy vstupní řetězec, který obsahuje pouze jedno číslo je interpretován jako počet dní. Pomocí vlastního specifikátoru formátu %h můžete místo toho interpretovat číselný řetězec jako počet hodin. V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.TimeSpan.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#8)]
[!code-vb[Conceptual.TimeSpan.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#8)]

Následující příklad ilustruje použití vlastního specifikátoru formátu "h".

[!code-csharp[Conceptual.TimeSpan.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#7)]
[!code-vb[Conceptual.TimeSpan.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#7)]

[Zpět na stůl](#table)

## <a name="hhSpecifier"></a>Vlastní specifikátor formátu "hh"

Vlastní specifikátor formátu "hh" vyvodí hodnotu <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> vlastnosti, která představuje počet celých hodin v časovém intervalu, který se nepočítá jako součást jeho denní součásti. Pro hodnoty od 0 do 9 obsahuje výstupní řetězec počáteční nulu.

Obvykle v operaci analýzy vstupní řetězec, který obsahuje pouze jedno číslo je interpretován jako počet dní. Vlastní specifikátor formátu "hh" můžete místo toho interpretovat číselný řetězec jako počet hodin. V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.TimeSpan.Custom#9](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#9)]
[!code-vb[Conceptual.TimeSpan.Custom#9](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#9)]

Následující příklad ilustruje použití vlastního specifikátoru formátu "hh".

[!code-csharp[Conceptual.TimeSpan.Custom#10](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#10)]
[!code-vb[Conceptual.TimeSpan.Custom#10](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#10)]

[Zpět na stůl](#table)

## <a name="mSpecifier"></a>Vlastní specifikátor formátu "m"

Vlastní specifikátor formátu "m" vyvodí hodnotu <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> vlastnosti, která představuje počet celých minut v časovém intervalu, který se nepočítá jako součást jeho denní součásti. Vrátí hodnotu jednomístného řetězce, pokud <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> je hodnota vlastnosti 0 až 9, a vrátí dvoumístnou řetězcovou hodnotu, pokud se hodnota <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> vlastnosti pohybuje od 10 do 59.

Pokud je vlastní specifikátor formátu "m" použit samostatně, zadejte %m, aby nebyl nesprávně interpretován jako standardní formátovací řetězec. V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.TimeSpan.Custom#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#6)]
[!code-vb[Conceptual.TimeSpan.Custom#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#6)]

Obvykle v operaci analýzy vstupní řetězec, který obsahuje pouze jedno číslo je interpretován jako počet dní. Pomocí vlastního specifikátoru formátu %m můžete místo toho interpretovat číselný řetězec jako počet minut. V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.TimeSpan.Custom#11](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#11)]
[!code-vb[Conceptual.TimeSpan.Custom#11](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#11)]

Následující příklad ilustruje použití vlastního specifikátoru formátu "m".

[!code-csharp[Conceptual.TimeSpan.Custom#12](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#12)]
[!code-vb[Conceptual.TimeSpan.Custom#12](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#12)]

[Zpět na stůl](#table)

## <a name="mmSpecifier"></a>Vlastní specifikátor formátu "mm"

Vlastní specifikátor formátu "mm" vyvezuje hodnotu <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> vlastnosti, která představuje počet celých minut v časovém intervalu, který není zahrnut jako součást součásti hodin nebo dnů. Pro hodnoty od 0 do 9 obsahuje výstupní řetězec počáteční nulu.

Obvykle v operaci analýzy vstupní řetězec, který obsahuje pouze jedno číslo je interpretován jako počet dní. Vlastní specifikátor formátu "mm" můžete místo toho interpretovat číselný řetězec jako počet minut. V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.TimeSpan.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#13)]
[!code-vb[Conceptual.TimeSpan.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#13)]

Následující příklad ilustruje použití vlastního specifikátoru formátu "mm".

[!code-csharp[Conceptual.TimeSpan.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#14)]
[!code-vb[Conceptual.TimeSpan.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#14)]

[Zpět na stůl](#table)

## <a name="sSpecifier"></a>Vlastní specifikátor formátu "s"

Vlastní specifikátor formátu "s" vyvodí hodnotu <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> vlastnosti, která představuje počet celých sekund v časovém intervalu, který není zahrnut jako součást součásti hodin, dnů nebo minut. Vrátí hodnotu jednomístného řetězce, pokud <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> je hodnota vlastnosti 0 až 9, a vrátí dvoumístnou řetězcovou hodnotu, pokud se hodnota <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> vlastnosti pohybuje od 10 do 59.

Pokud je vlastní specifikátor formátu "s" použit samostatně, zadejte %s, aby nebyl nesprávně interpretován jako standardní formátovací řetězec. V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.TimeSpan.Custom#15](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#15)]
[!code-vb[Conceptual.TimeSpan.Custom#15](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#15)]

Obvykle v operaci analýzy vstupní řetězec, který obsahuje pouze jedno číslo je interpretován jako počet dní. Vlastní specifikátor formátu %s můžete místo toho interpretovat číselný řetězec jako počet sekund. V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.TimeSpan.Custom#17](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#17)]
[!code-vb[Conceptual.TimeSpan.Custom#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#17)]

Následující příklad ilustruje použití vlastního specifikátoru formátu "s".

[!code-csharp[Conceptual.TimeSpan.Custom#16](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#16)]
[!code-vb[Conceptual.TimeSpan.Custom#16](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#16)]

[Zpět na stůl](#table)

## <a name="ssSpecifier"></a>Vlastní specifikátor formátu "ss"

Vlastní specifikátor formátu "ss" vyvezuje hodnotu <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> vlastnosti, která představuje počet celých sekund v časovém intervalu, který není zahrnut jako součást součásti hodin, dnů nebo minut. Pro hodnoty od 0 do 9 obsahuje výstupní řetězec počáteční nulu.

Obvykle v operaci analýzy vstupní řetězec, který obsahuje pouze jedno číslo je interpretován jako počet dní. Vlastní specifikátor formátu "ss" můžete místo toho interpretovat číselný řetězec jako počet sekund. V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.TimeSpan.Custom#18](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#18)]
[!code-vb[Conceptual.TimeSpan.Custom#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#18)]

Následující příklad ilustruje použití vlastního specifikátoru formátu "ss".

[!code-csharp[Conceptual.TimeSpan.Custom#19](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#19)]
[!code-vb[Conceptual.TimeSpan.Custom#19](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#19)]

[Zpět na stůl](#table)

## <a name="fSpecifier"></a>Vlastní specifikátor formátu "f"

Vlastní specifikátor formátu "f" vyvezuu desetiny sekundy v časovém intervalu. Při operaci formátování jsou všechny zbývající zlomkové číslice zkráceny. V operaci analýzy, která <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> volá metodu or, musí vstupní řetězec obsahovat přesně jednu zlomkovou číslici.

Pokud je vlastní specifikátor formátu "f" použit samostatně, zadejte "%f", aby nebyl nesprávně interpretován jako standardní formátovací řetězec.

Následující příklad používá vlastní specifikátor formátu "f" k zobrazení desetin sekundy v hodnotě. <xref:System.TimeSpan> "f" se používá nejprve jako jediný specifikátor formátu a poté v kombinaci s specifikátorem "s" ve vlastním formátovacím řetězci.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Zpět na stůl](#table)

## <a name="ffSpecifier"></a>Vlastní specifikátor formátu "ff"

Vlastní specifikátor formátu "ff" vyvezuje setiny sekundy v časovém intervalu. Při operaci formátování jsou všechny zbývající zlomkové číslice zkráceny. V operaci analýzy, která <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> volá metodu or, musí vstupní řetězec obsahovat přesně dvě zlomkové číslice.

Následující příklad používá specifikátor vlastního formátu "ff" k zobrazení setin <xref:System.TimeSpan> sekundy v hodnotě. "ff" se používá nejprve jako jediný specifikátor formátu a poté v kombinaci s specifikátorem "s" ve vlastním formátovacím řetězci.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Zpět na stůl](#table)

## <a name="f3Specifier"></a>Vlastní specifikátor formátu "fff"

Vlastní specifikátor formátu "fff" (se třemi znaky "f") vyvodí milisekundy v časovém intervalu. Při operaci formátování jsou všechny zbývající zlomkové číslice zkráceny. V operaci analýzy, která <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> volá metodu or, musí vstupní řetězec obsahovat přesně tři zlomkové číslice.

Následující příklad používá vlastní specifikátor formátu "fff" k zobrazení <xref:System.TimeSpan> milisekund v hodnotě. "fff" se používá nejprve jako jediný specifikátor formátu a poté v kombinaci s specifikátorem "s" ve vlastním formátovacím řetězci.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Zpět na stůl](#table)

## <a name="f4Specifier"></a>Vlastní specifikátor formátu ffff

Vlastní specifikátor formátu "ffff" (se čtyřmi znaky "f") vyráží deset tisícin sekundy v časovém intervalu. Při operaci formátování jsou všechny zbývající zlomkové číslice zkráceny. V operaci analýzy, která <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> volá metodu or, musí vstupní řetězec obsahovat přesně čtyři zlomkové číslice.

Následující příklad používá specifikátor vlastního formátu ffff k zobrazení deseti tisícin sekundy v hodnotě. <xref:System.TimeSpan> "ffff" se používá nejprve jako jediný specifikátor formátu a poté v kombinaci s specifikátorem "s" ve vlastním formátovacím řetězci.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Zpět na stůl](#table)

## <a name="f5Specifier"></a>Vlastní specifikátor formátu "fffff"

Vlastní specifikátor formátu "fffff" (s pěti znaky "f" ) vyráží stotisícinsekundy sekundy v časovém intervalu. Při operaci formátování jsou všechny zbývající zlomkové číslice zkráceny. V operaci analýzy, která <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> volá metodu or, musí vstupní řetězec obsahovat přesně pět zlomkových číslic.

Následující příklad používá vlastní specifikátor formátu fffff k zobrazení stotisícin sekundy v hodnotě. <xref:System.TimeSpan> "fffff" se používá nejprve jako jediný specifikátor formátu a poté v kombinaci s specifikátorem "s" ve vlastním formátovacím řetězci.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Zpět na stůl](#table)

## <a name="f6Specifier"></a>Vlastní specifikátor formátu ffffff

Vlastní specifikátor formátu "ffffff" (se šesti znaky "f") vyvodí miliontiny sekundy v časovém intervalu. Při operaci formátování jsou všechny zbývající zlomkové číslice zkráceny. V operaci analýzy, která <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> volá metodu or, musí vstupní řetězec obsahovat přesně šest zlomkových číslic.

Následující příklad používá vlastní specifikátor formátu ffffff k zobrazení miliontin <xref:System.TimeSpan> sekundy v hodnotě. Používá se nejprve jako jediný specifikátor formátu a poté v kombinaci s specifikátorem "s" ve vlastním formátovacím řetězci.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Zpět na stůl](#table)

## <a name="f7Specifier"></a>Vlastní specifikátor formátu fffffff

Vlastní specifikátor formátu "fffffff" (se sedmi znaky "f" ) vyráží deset miliontin sekundy (nebo zlomkový počet značek) v časovém intervalu. V operaci analýzy, která <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> volá metodu or, musí vstupní řetězec obsahovat přesně sedm zlomkových číslic.

Následující příklad používá vlastní specifikátor formátu fffffff k zobrazení zlomkového <xref:System.TimeSpan> počtu značek v hodnotě. Používá se nejprve jako jediný specifikátor formátu a poté v kombinaci s specifikátorem "s" ve vlastním formátovacím řetězci.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Zpět na stůl](#table)

## <a name="F_Specifier"></a>Vlastní specifikátor formátu "F"

Vlastní specifikátor formátu "F" vyvezuje desetiny sekundy v časovém intervalu. Při operaci formátování jsou všechny zbývající zlomkové číslice zkráceny. Pokud je hodnota desetin y sekundy časového intervalu nulová, není zahrnuta do výsledného řetězce. V operaci analýzy, která <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> volá metodu nebo, je přítomnost desetin druhé číslice nepovinná.

Pokud je vlastní specifikátor formátu "F" použit samostatně, zadejte %F, aby nebyl nesprávně interpretován jako standardní formátovací řetězec.

Následující příklad používá vlastní specifikátor formátu "F" k zobrazení desetin sekundy v hodnotě. <xref:System.TimeSpan> Používá také tento vlastní specifikátor formátu v operaci analýzy.

[!code-csharp[Conceptual.TimeSpan.Custom#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#21)]
[!code-vb[Conceptual.TimeSpan.Custom#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#21)]

[Zpět na stůl](#table)

## <a name="FF_Specifier"></a>Vlastní specifikátor formátu "FF"

Vlastní specifikátor formátu "FF" vyvezuje setiny sekundy v časovém intervalu. Při operaci formátování jsou všechny zbývající zlomkové číslice zkráceny. Pokud existují nějaké koncové zlomkové nuly, nejsou zahrnuty do výsledného řetězce. V operaci analýzy, která <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> volá metodu or, je přítomnost desetin a setin druhé číslice nepovinná.

Následující příklad používá vlastní specifikátor formátu FF k zobrazení setin sekundy v hodnotě. <xref:System.TimeSpan> Používá také tento vlastní specifikátor formátu v operaci analýzy.

[!code-csharp[Conceptual.TimeSpan.Custom#22](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#22)]
[!code-vb[Conceptual.TimeSpan.Custom#22](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#22)]

[Zpět na stůl](#table)

## <a name="F3_Specifier"></a>Vlastní specifikátor formátu FFF

Vlastní specifikátor formátu "FFF" (se třemi znaky "F") vyvázne milisekundy v časovém intervalu. Při operaci formátování jsou všechny zbývající zlomkové číslice zkráceny. Pokud existují nějaké koncové zlomkové nuly, nejsou zahrnuty do výsledného řetězce. V operaci analýzy, která <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> volá metodu or, je přítomnost desetin, setin a tisícin druhé číslice nepovinná.

Následující příklad používá vlastní specifikátor formátu "FFF" k zobrazení tisícin <xref:System.TimeSpan> sekundy v hodnotě. Používá také tento vlastní specifikátor formátu v operaci analýzy.

[!code-csharp[Conceptual.TimeSpan.Custom#23](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#23)]
[!code-vb[Conceptual.TimeSpan.Custom#23](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#23)]

[Zpět na stůl](#table)

## <a name="F4_Specifier"></a>Vlastní specifikátor formátu FFFF

Vlastní specifikátor formátu FFFF (se čtyřmi znaky "F") vyráží deset tisícin sekundy v časovém intervalu. Při operaci formátování jsou všechny zbývající zlomkové číslice zkráceny. Pokud existují nějaké koncové zlomkové nuly, nejsou zahrnuty do výsledného řetězce. V operaci analýzy, která <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> volá metodu nebo, je přítomnost desetin, setin, tisícin a deseti tisícin druhé číslice nepovinná.

Následující příklad používá vlastní specifikátor formátu FFFF k zobrazení deseti tisícin sekundy v hodnotě. <xref:System.TimeSpan> Používá také vlastní specifikátor formátu FFFF v operaci analýzy.

[!code-csharp[Conceptual.TimeSpan.Custom#24](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#24)]
[!code-vb[Conceptual.TimeSpan.Custom#24](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#24)]

[Zpět na stůl](#table)

## <a name="F5_Specifier"></a>Vlastní specifikátor formátu FFFFF

Vlastní specifikátor formátu "FFFFF" (s pěti znaky "F") vyráží stotisícinsekundy sekundy v časovém intervalu. Při operaci formátování jsou všechny zbývající zlomkové číslice zkráceny. Pokud existují nějaké koncové zlomkové nuly, nejsou zahrnuty do výsledného řetězce. V operaci analýzy, která <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> volá metodu nebo, je přítomnost desetin, setin, tisícin, deseti tisícin a stotisícin druhé číslice nepovinná.

Následující příklad používá vlastní specifikátor formátu "FFFFF" k zobrazení stotisícin <xref:System.TimeSpan> sekundy v hodnotě. Používá také vlastní specifikátor formátu "FFFFF" v operaci analýzy.

[!code-csharp[Conceptual.TimeSpan.Custom#25](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#25)]
[!code-vb[Conceptual.TimeSpan.Custom#25](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#25)]

[Zpět na stůl](#table)

## <a name="F6_Specifier"></a>Vlastní specifikátor formátu FFFFFF

Vlastní specifikátor formátu FFFFFF (se šesti znaky "F") vyvodí miliontiny sekundy v časovém intervalu. Při operaci formátování jsou všechny zbývající zlomkové číslice zkráceny. Pokud existují nějaké koncové zlomkové nuly, nejsou zahrnuty do výsledného řetězce. V operaci analýzy, která <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> volá metodu nebo, je přítomnost desetin, setin, tisícin, deseti tisícin, stotisícin a miliontin druhé číslice nepovinná.

Následující příklad používá vlastní specifikátor formátu FFFFFF k zobrazení miliontin <xref:System.TimeSpan> sekundy v hodnotě. Používá také tento vlastní specifikátor formátu v operaci analýzy.

[!code-csharp[Conceptual.TimeSpan.Custom#26](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#26)]
[!code-vb[Conceptual.TimeSpan.Custom#26](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#26)]

[Zpět na stůl](#table)

## <a name="F7_Specifier"></a>Vlastní specifikátor formátu FFFFFFF

Vlastní specifikátor formátu "FFFFFFF" (se sedmi znaky "F") vydezuje deset miliontin sekundy (nebo zlomkový počet značek) v časovém intervalu. Pokud existují nějaké koncové zlomkové nuly, nejsou zahrnuty do výsledného řetězce. V operaci analýzy, která <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> volá metodu or, je přítomnost sedmi desetinných číslic ve vstupním řetězci volitelná.

Následující příklad používá vlastní specifikátor formátu FFFFFFF k zobrazení zlomkových <xref:System.TimeSpan> částí sekundy v hodnotě. Používá také tento vlastní specifikátor formátu v operaci analýzy.

[!code-csharp[Conceptual.TimeSpan.Custom#27](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#27)]
[!code-vb[Conceptual.TimeSpan.Custom#27](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#27)]

[Zpět na stůl](#table)

## <a name="other-characters"></a>Další znaky

Jakýkoli jiný neuvozený znak ve formátovacím řetězci, včetně prázdného znaku, je interpretován jako vlastní specifikátor formátu. Ve většině případů přítomnost jiného neuvozeného <xref:System.FormatException>znaku má za následek .

Existují dva způsoby, jak zahrnout literál znak do řetězce formátu:

- Uzavřete ji do jednoduchých uvozovek (oddělovač literálu řetězce).

- Před ním s zpětné lomítko ("\\"), který je interpretován jako řídicí znak. To znamená, že v c#musí být @-quotedformátovací řetězec buď , nebo znak literálu musí předcházet další zpětné lomítko.

  V některých případech bude pravděpodobně muset použít podmíněnou logiku zahrnout uvozený literál ve formátu řetězce. Následující příklad používá podmíněnou logiku k zahrnutí symbolu znaménku pro záporné časové intervaly.

  [!code-csharp[Conceptual.TimeSpan.Custom#29](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/negativevalues1.cs#29)]
  [!code-vb[Conceptual.TimeSpan.Custom#29](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/negativevalues1.vb#29)]

Rozhraní .NET nedefinuje gramatiku pro oddělovače v časových intervalech. To znamená, že oddělovače mezi dny a hodinami, hodinami a minutami, minutami a sekundami a sekundami a zlomky sekundy musí být všechny považovány za literály znaků ve formátovacím řetězci.

Následující příklad používá řídicí znak a jednu uvozovku k definování vlastního formátovacího řetězce, který obsahuje slovo "minuty" ve výstupním řetězci.

[!code-csharp[Conceptual.TimeSpan.Custom#28](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/literal1.cs#28)]
[!code-vb[Conceptual.TimeSpan.Custom#28](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/literal1.vb#28)]

[Zpět na stůl](#table)

## <a name="see-also"></a>Viz také

- [Typy formátování](formatting-types.md)
- [Standardní řetězce formátu TimeSpan](standard-timespan-format-strings.md)
