---
title: Vlastní řetězce formátu TimeSpan
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- format spexifiers, custom time interval
- format strings
- formatting [.NET Framework], time interval
- custom time interval format strings
- formatting [.NET Framework], time
- custom TimeSpan format strings
ms.assetid: a63ebf55-7269-416b-b4f5-286f6c03bf0e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0cf81b5a86d55cf3d7872e0e5281c35f41ad1c31
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43563990"
---
# <a name="custom-timespan-format-strings"></a>Vlastní řetězce formátu TimeSpan

A <xref:System.TimeSpan> formátovací řetězec definuje řetězcovou reprezentaci <xref:System.TimeSpan> hodnotu, která je výsledkem operace formátování. Řetězec vlastního formátu se skládá z jednoho nebo více vlastních <xref:System.TimeSpan> spolu s literálními znaky libovolný počet specifikátory formátu. Jakýkoli řetězec, který není [standardní řetězce formátu TimeSpan](standard-timespan-format-strings.md) je interpretován jako vlastní <xref:System.TimeSpan> řetězec formátu.

> [!IMPORTANT]
> Vlastní <xref:System.TimeSpan> specifikátory formátu nezahrnují zástupné symboly oddělovače, jako jsou symboly, které oddělují dny od hodin, hodiny od minuty nebo sekundy od zlomků sekund. Místo toho tyto symboly musí být součástí vlastní řetězec formátu jako řetězcové literály. Například `"dd\.hh\:mm"` definuje tečku (.) jako oddělovač mezi dny a hodiny a dvojtečky (:) jako oddělovač mezi hodinách a minutách.
>
> Vlastní <xref:System.TimeSpan> specifikátory formátu také nezahrnují symbolem, která umožňuje rozlišovat mezi kladnému i časové intervaly. Zahrnout symbolem, budete muset sestavit řetězec formátu pomocí podmíněnou logiku. [Ostatní znaky](#Other) část obsahuje příklad.

Řetězcové vyjádření <xref:System.TimeSpan> hodnoty jsou vytvářeny voláním přetížení <xref:System.TimeSpan.ToString%2A?displayProperty=nameWithType> metody a metodami, které podporují také složené formátování, jako například <xref:System.String.Format%2A?displayProperty=nameWithType>. Další informace najdete v tématu [Formatting Types](formatting-types.md) a [složené formátování](composite-formatting.md). Následující příklad ukazuje použití řetězců vlastního formátu v operacích formátování.

[!code-csharp[Conceptual.TimeSpan.Custom#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customformatexample1.cs#1)]
[!code-vb[Conceptual.TimeSpan.Custom#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customformatexample1.vb#1)]

Vlastní <xref:System.TimeSpan> formátovací řetězce jsou také používány <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> a <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody, které definují požadovaný formát ze vstupních řetězců pro operace analýzy. (Analýza kódu převede řetězcové vyjádření hodnoty této hodnotě.) Následující příklad ukazuje použití standardního formátovacího řetězce v operacích analýzy.

[!code-csharp[Conceptual.TimeSpan.Custom#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customparseexample1.cs#2)]
[!code-vb[Conceptual.TimeSpan.Custom#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customparseexample1.vb#2)]

<a name="table"></a> Následující tabulka popisuje vlastní datum a čas specifikátorů formátu.

| Specifikátor formátu | Popis | Příklad |
|----------------------|-----------------|-------------|
|"d", "%d.|Počet celých dnů v časovém intervalu.<br /><br /> Další informace: [specifikátor vlastního formátu "d"](#dSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `%d` --> "6"<br /><br /> `d\.hh\:mm` --> "6.14:32"|
|"dd"-"dddddddd"|Počet celých dnů v časovém intervalu doplněno počátečními nulami, podle potřeby.<br /><br /> Další informace: ["dd"-"dddddddd" specifikátorů vlastního formátu](#ddSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `ddd` --> "006"<br /><br /> `dd\.hh\:mm` --> "06.14:32"|
|"h", "%h"|Počet celé hodiny v časovém intervalu, který se nepočítají jako součást dnů. Jednociferné hodin nemají úvodní nuly.<br /><br /> Další informace: [specifikátor vlastního formátu "h"](#hSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `%h` --> "14"<br /><br /> `hh\:mm` --> "14:32"|
|"hh"|Počet celé hodiny v časovém intervalu, který se nepočítají jako součást dnů. Jednociferné hodin obsahovat úvodní nuly.<br /><br /> Další informace: [specifikátor vlastního formátu "hh"](#hhSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `hh` --> "14"<br /><br /> `new TimeSpan(6, 8, 32, 17, 685):`<br /><br /> `hh` --> 08|
|"m", "%m"|Počet celých minut časového období, které nejsou součástí hodiny nebo i dny. Jednociferné minut nemají úvodní nuly.<br /><br /> Další informace: [specifikátor vlastního formátu "m"](#mSpecifier).|`new TimeSpan(6, 14, 8, 17, 685):`<br /><br /> `%m` --> "8"<br /><br /> `h\:m` --> "14:8"|
|"mm"|Počet celých minut časového období, které nejsou součástí hodiny nebo i dny. Jednociferné minut obsahovat úvodní nuly.<br /><br /> Další informace: [specifikátor vlastního formátu "mm"](#mmSpecifier).|`new TimeSpan(6, 14, 8, 17, 685):`<br /><br /> `mm` --> "08"<br /><br /> `new TimeSpan(6, 8, 5, 17, 685):`<br /><br /> `d\.hh\:mm\:ss` --> 6.08:05:17|
|"s", "%s"|Počet celé sekundy v časovém intervalu, které nejsou součástí hodinách, dnech nebo minut. Jednociferné sekund nemají úvodní nuly.<br /><br /> Další informace: [specifikátor vlastního formátu "s"](#sSpecifier).|`TimeSpan.FromSeconds(12.965)`:<br /><br /> `%s` --> 12<br /><br /> `s\.fff` --> 12.965|
|"ss"|Počet celé sekundy v časovém intervalu, které nejsou součástí hodinách, dnech nebo minut.  Jednociferné sekund obsahovat úvodní nuly.<br /><br /> Další informace: [specifikátor vlastního formátu "ss"](#ssSpecifier).|`TimeSpan.FromSeconds(6.965)`:<br /><br /> `ss` --> 06<br /><br /> `ss\.fff` --> 06.965|
|"f", "%f"|Desetiny sekundy v časovém intervalu.<br /><br /> Další informace: [specifikátor vlastního formátu "f"](#fSpecifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `f` --> 8<br /><br /> `ss\.f` --> 06.8|
|"ff"|Setiny sekundy v časovém intervalu.<br /><br /> Další informace:[specifikátor vlastního formátu "ff"](#ffSpecifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `ff` --> 89<br /><br /> `ss\.ff` --> 06.89|
|"fff"|Milisekundy v časovém intervalu.<br /><br /> Další informace: [specifikátor vlastního formátu "fff"](#f3Specifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `fff` --> 895<br /><br /> `ss\.fff` --> 06.895|
|"ffff"|Desetitisíciny sekundy v časovém intervalu.<br /><br /> Další informace: [specifikátor vlastního formátu "ffff"](#f4Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `ffff` --> 8954<br /><br /> `ss\.ffff` --> 06.8954|
|"fffff"|Stotisíciny sekundy v časovém intervalu.<br /><br /> Další informace: [specifikátor vlastního formátu "fffff"](#f5Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `fffff` --> 89543<br /><br /> `ss\.fffff` --> 06.89543|
|"ffffff"|Miliontiny sekundy v časovém intervalu.<br /><br /> Další informace: [specifikátor vlastního formátu "ffffff"](#f6Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `ffffff` --> 895432<br /><br /> `ss\.ffffff` --> 06.895432|
|"fffffff"|-Desetimiliontiny sekundy (nebo desetinné dílků) v časovém intervalu.<br /><br /> Další informace: [specifikátor vlastního formátu "fffffff"](#f7Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `fffffff` --> 8954321<br /><br /> `ss\.fffffff` --> 06.8954321|
|"F", "%F"|Desetiny sekundy v časovém intervalu. Pokud je číslice nula, nezobrazí se žádná hodnota.<br /><br /> Další informace: [specifikátor formátu "F" vlastního](#F_Specifier).|`TimeSpan.Parse("00:00:06.32")`:<br /><br /> `%F`: 3<br /><br /> `TimeSpan.Parse("0:0:3.091")`:<br /><br /> `ss\.F`: 03.|
|"FF"|Setiny sekundy v časovém intervalu. Všechny koncové nuly nebo dvě desetinné nul nejsou zahrnuty.<br /><br /> Další informace: [specifikátor vlastního formátu "FF"](#FF_Specifier).|`TimeSpan.Parse("00:00:06.329")`:<br /><br /> `FF`: 32<br /><br /> `TimeSpan.Parse("0:0:3.101")`:<br /><br /> `ss\.FF`: 03.1|
|"FFF"|Milisekundy v časovém intervalu. Žádné desetinné části koncové nuly nejsou zahrnuty.<br /><br /> Další informace:|`TimeSpan.Parse("00:00:06.3291")`:<br /><br /> `FFF`: 329<br /><br /> `TimeSpan.Parse("0:0:3.1009")`:<br /><br /> `ss\.FFF`: 03.1|
|"FFFF"|Desetitisíciny sekundy v časovém intervalu. Žádné desetinné části koncové nuly nejsou zahrnuty.<br /><br /> Další informace: [specifikátor vlastního formátu "FFFF"](#F4_Specifier).|`TimeSpan.Parse("00:00:06.32917")`:<br /><br /> `FFFFF`: 3291<br /><br /> `TimeSpan.Parse("0:0:3.10009")`:<br /><br /> `ss\.FFFF`: 03.1|
|"FFFFF"|Stotisíciny sekundy v časovém intervalu. Žádné desetinné části koncové nuly nejsou zahrnuty.<br /><br /> Další informace: [specifikátor vlastního formátu "FFFFF"](#F5_Specifier).|`TimeSpan.Parse("00:00:06.329179")`:<br /><br /> `FFFFF`: 32917<br /><br /> `TimeSpan.Parse("0:0:3.100009")`:<br /><br /> `ss\.FFFFF`: 03.1|
|"FFFFFF"|Miliontiny sekundy v časovém intervalu. Nejsou zobrazeny žádné desetinné části koncové nuly.<br /><br /> Další informace: [specifikátor vlastního formátu "FFFFFF"](#F6_Specifier).|`TimeSpan.Parse("00:00:06.3291791")`:<br /><br /> `FFFFFF`: 329179<br /><br /> `TimeSpan.Parse("0:0:3.1000009")`:<br /><br /> `ss\.FFFFFF`: 03.1|
|"FFFFFFF"|Desetimiliontiny sekundy v časovém intervalu. Nejsou zobrazeny žádné desetinné části koncové nuly nebo sedmi nul.<br /><br /> Další informace: [specifikátor vlastního formátu "FFFFFFF"](#F7_Specifier).|`TimeSpan.Parse("00:00:06.3291791")`:<br /><br /> `FFFFFF`: 3291791<br /><br /> `TimeSpan.Parse("0:0:3.1900000")`:<br /><br /> `ss\.FFFFFF`: 03.19|
|"*řetězec*.|Oddělovač řetězcového literálu.<br /><br /> Další informace: [ostatní znaky](#Other).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh':'mm':'ss` --> "14:32:17"|
|\\| Řídicí znak.<br /><br /> Další informace:[ostatní znaky](#Other).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh\:mm\:ss` --> "14:32:17"|
|Jakýkoli jiný znak|Další znak bez řídícího znaku je interpretován jako specifikátor vlastního formátu.<br /><br /> Další informace: [jiné znaky](#Other).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh\:mm\:ss` --> "14:32:17"|

<a name="dSpecifier"></a> 

## <a name="the-d-custom-format-specifier"></a>Specifikátor vlastního formátu "d".

Specifikátor vlastního formátu "d" vypíše hodnoty <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> vlastnost, která představuje počet celých dní v časovém intervalu. Vypíše úplné počet dní v <xref:System.TimeSpan> oceníme i v případě, že hodnota má více než jednu číslici. Pokud hodnota <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> vlastnost je nula, výstupy specifikátor "0".

Pokud je specifikátor vlastního formátu "d" použitý samostatně, zadejte tak, aby se chybně interpretován jako řetězec standardního formátu "%d". V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.TimeSpan.Custom#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#3)]
[!code-vb[Conceptual.TimeSpan.Custom#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#3)]

Následující příklad ukazuje použití specifikátoru vlastního formátu "d".

[!code-csharp[Conceptual.TimeSpan.Custom#4](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#4)]
[!code-vb[Conceptual.TimeSpan.Custom#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#4)]

[Zpět k tabulce](#table)

<a name="ddSpecifier"></a> 

## <a name="the-dd-dddddddd-custom-format-specifiers"></a>"dd"-"dddddddd" specifikátorů vlastního formátu
"Dd", "ddd", "dddd", "ddddd", "dddddd", "ddddddd" a specifikátoru vlastního formátu "dddddddd" výstupní hodnota <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> vlastnost, která představuje počet celých dní v časovém intervalu.

Výstupní řetězec obsahuje minimální počet číslic určený počet znaků "d" ve specifikátoru formátu a je doplněno počátečními nulami, podle potřeby. Pokud číslice za počet dnů delší než počet znaků "d" ve specifikátoru formátu, je plný počet dnů výstup ve výsledném řetězci.

Následující příklad používá tyto specifikátory formátu k zobrazení řetězcovou reprezentaci dvou <xref:System.TimeSpan> hodnoty. Komponentu dnů první časový interval hodnotu nula; komponentu dnů druhého hodnotu 365.

[!code-csharp[Conceptual.TimeSpan.Custom#5](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#5)]
[!code-vb[Conceptual.TimeSpan.Custom#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#5)]

[Zpět k tabulce](#table)

<a name="hSpecifier"></a> 

## <a name="the-h-custom-format-specifier"></a>Specifikátor vlastního formátu "h"
Specifikátor vlastního formátu "h" vypíše hodnoty <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> vlastnost, která představuje počet celé hodiny v časovém intervalu, který se počítá jako součást své komponentě den. Vrací řetězec jednocifernou hodnotu, pokud hodnota <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> vlastnost je 0 až 9, a vrátí hodnotu řetězce dvěma číslicemi, pokud hodnota <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> vlastností v rozsahu od 10 do 23.

Pokud je specifikátor vlastního formátu "h" použitý samostatně, zadejte "%h", aby se chybně interpretován jako řetězec standardního formátu. V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.TimeSpan.Custom#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#6)]
[!code-vb[Conceptual.TimeSpan.Custom#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#6)]

Při operaci parsování, obvykle vstupní řetězec, který obsahuje pouze jedno číslo interpretována jako počet dnů. Specifikátor vlastního formátu "%h" můžete použít místo toho Interpretace číselných řetězců jako počet hodin. V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.TimeSpan.Custom#8](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#8)]
[!code-vb[Conceptual.TimeSpan.Custom#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#8)]

Následující příklad ukazuje použití specifikátoru vlastního formátu "h".

[!code-csharp[Conceptual.TimeSpan.Custom#7](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#7)]
[!code-vb[Conceptual.TimeSpan.Custom#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#7)]

[Zpět k tabulce](#table)

<a name="hhSpecifier"></a> 

## <a name="the-hh-custom-format-specifier"></a>Specifikátor vlastního formátu "hh"
Specifikátor vlastního formátu "hh" vypíše hodnoty <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> vlastnost, která představuje počet celé hodiny v časovém intervalu, který se počítá jako součást své komponentě den. Výstupní řetězec obsahuje hodnoty od 0 do 9, počáteční nuly.

Při operaci parsování, obvykle vstupní řetězec, který obsahuje pouze jedno číslo interpretována jako počet dnů. Specifikátor vlastního formátu "hh" místo toho můžete použít k interpretaci číselných řetězců jako počet hodin. V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.TimeSpan.Custom#9](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#9)]
[!code-vb[Conceptual.TimeSpan.Custom#9](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#9)]

Následující příklad ukazuje použití specifikátoru vlastního formátu "hh".

[!code-csharp[Conceptual.TimeSpan.Custom#10](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#10)]
[!code-vb[Conceptual.TimeSpan.Custom#10](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#10)]

[Zpět k tabulce](#table)

<a name="mSpecifier"></a> 

## <a name="the-m-custom-format-specifier"></a>Specifikátor vlastního formátu "m"
Specifikátor vlastního formátu "m" vypíše hodnoty <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> vlastnost, která představuje počet celých minut v časovém intervalu, který se počítá jako součást své komponentě den. Vrací řetězec jednocifernou hodnotu, pokud hodnota <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> vlastnost je 0 až 9, a vrátí hodnotu řetězce dvěma číslicemi, pokud hodnota <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> vlastností v rozsahu od 10 do 59.

Pokud je specifikátor vlastního formátu "m" použitý samostatně, zadejte tak, aby se chybně interpretován jako řetězec standardního formátu "%m". V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.TimeSpan.Custom#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#6)]
[!code-vb[Conceptual.TimeSpan.Custom#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#6)]

Při operaci parsování, obvykle vstupní řetězec, který obsahuje pouze jedno číslo interpretována jako počet dnů. Specifikátor vlastního formátu "%m" můžete místo toho použít k interpretaci číselných řetězců jako počet minut. V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.TimeSpan.Custom#11](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#11)]
[!code-vb[Conceptual.TimeSpan.Custom#11](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#11)]

Následující příklad ukazuje použití specifikátoru vlastního formátu "m".

[!code-csharp[Conceptual.TimeSpan.Custom#12](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#12)]
[!code-vb[Conceptual.TimeSpan.Custom#12](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#12)]

[Zpět k tabulce](#table)

<a name="mmSpecifier"></a> 

## <a name="the-mm-custom-format-specifier"></a>Specifikátor vlastního formátu "mm"
Specifikátor vlastního formátu "mm" vypíše hodnoty <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> vlastnost, která představuje počet celých minut v časovém intervalu, který není zahrnut jako součást hodiny nebo i dny. Výstupní řetězec obsahuje hodnoty od 0 do 9, počáteční nuly.

Při operaci parsování, obvykle vstupní řetězec, který obsahuje pouze jedno číslo interpretována jako počet dnů. Specifikátor vlastního formátu "mm" můžete místo toho použít k interpretaci číselných řetězců jako počet minut. V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.TimeSpan.Custom#13](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#13)]
[!code-vb[Conceptual.TimeSpan.Custom#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#13)]

Následující příklad ukazuje použití specifikátoru vlastního formátu "mm".

[!code-csharp[Conceptual.TimeSpan.Custom#14](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#14)]
[!code-vb[Conceptual.TimeSpan.Custom#14](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#14)]

[Zpět k tabulce](#table)

<a name="sSpecifier"></a> 

## <a name="the-s-custom-format-specifier"></a>Specifikátor vlastního formátu "s"
Specifikátor vlastního formátu "s" vypíše hodnoty <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> vlastnost, která představuje počet celé sekundy v časovém intervalu, který není součástí jeho komponenty minut, hodin nebo dnů. Vrací řetězec jednocifernou hodnotu, pokud hodnota <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> vlastnost je 0 až 9, a vrátí hodnotu řetězce dvěma číslicemi, pokud hodnota <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> vlastností v rozsahu od 10 do 59.

Pokud je specifikátor vlastního formátu "s" použitý samostatně, zadejte "%s" tak, aby se chybně interpretován jako řetězec standardního formátu. V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.TimeSpan.Custom#15](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#15)]
[!code-vb[Conceptual.TimeSpan.Custom#15](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#15)]

Při operaci parsování, obvykle vstupní řetězec, který obsahuje pouze jedno číslo interpretována jako počet dnů. Specifikátor vlastního formátu "%s" můžete použít místo toho Interpretace číselných řetězců jako počet sekund. V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.TimeSpan.Custom#17](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#17)]
[!code-vb[Conceptual.TimeSpan.Custom#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#17)]

Následující příklad ukazuje použití specifikátoru vlastního formátu "s".

[!code-csharp[Conceptual.TimeSpan.Custom#16](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#16)]
[!code-vb[Conceptual.TimeSpan.Custom#16](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#16)]

[Zpět k tabulce](#table)

<a name="ssSpecifier"></a> 

## <a name="the-ss-custom-format-specifier"></a>Specifikátor vlastního formátu "ss"
Specifikátor vlastního formátu "ss" vypíše hodnoty <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> vlastnost, která představuje počet celé sekundy v časovém intervalu, který není součástí jeho komponenty minut, hodin nebo dnů. Výstupní řetězec obsahuje hodnoty od 0 do 9, počáteční nuly.

Při operaci parsování, obvykle vstupní řetězec, který obsahuje pouze jedno číslo interpretována jako počet dnů. Specifikátor vlastního formátu "ss" můžete místo toho použít Interpretace číselných řetězců jako počet sekund. V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.TimeSpan.Custom#18](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#18)]
[!code-vb[Conceptual.TimeSpan.Custom#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#18)]

Následující příklad ukazuje použití specifikátoru vlastního formátu "ss".

[!code-csharp[Conceptual.TimeSpan.Custom#19](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#19)]
[!code-vb[Conceptual.TimeSpan.Custom#19](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#19)]

[Zpět k tabulce](#table)

<a name="fSpecifier"></a> 

## <a name="thef-custom-format-specifier"></a>Specifikátor vlastního formátu "f"
Specifikátor vlastního formátu "f" výstupy desetiny sekundy v časovém intervalu. V rámci operace formátování se zkrátí všechny zbývající zlomkové číslice. Při operaci parsování, která volá <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody vstupní řetězec musí obsahovat přesně jeden zlomková číslice.

Pokud je specifikátor vlastního formátu "f" použitý samostatně, zadejte tak, aby se chybně interpretován jako řetězec standardního formátu "%f".

Následující příklad používá specifikátor vlastního formátu "f" k zobrazení desetiny sekundy v <xref:System.TimeSpan> hodnotu. "f" používá nejprve jako jediný specifikátor formátu a následně se spojí dohromady se specifikátorem "s" v řetězci vlastního formátu.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Zpět k tabulce](#table)

<a name="ffSpecifier"></a> 

## <a name="the-ff-custom-format-specifier"></a>Specifikátor vlastního formátu "ff"
Specifikátor vlastního formátu "ff" výstupy setiny sekundy v časovém intervalu. V rámci operace formátování se zkrátí všechny zbývající zlomkové číslice. Při operaci parsování, která volá <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody vstupní řetězec musí obsahovat přesně dvě desetinné číslice.

Následující příklad používá specifikátor vlastního formátu "ff" k zobrazení setiny sekundy v <xref:System.TimeSpan> hodnotu. "ff" používá nejprve jako jediný specifikátor formátu a následně se spojí dohromady se specifikátorem "s" v řetězci vlastního formátu.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Zpět k tabulce](#table)

<a name="f3Specifier"></a> 

## <a name="the-fff-custom-format-specifier"></a>Specifikátor vlastního formátu "fff"
Specifikátor vlastního formátu "fff" (se třemi znaky "f") výstupů milisekundy v časovém intervalu. V rámci operace formátování se zkrátí všechny zbývající zlomkové číslice. Při operaci parsování, která volá <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody vstupní řetězec musí obsahovat přesně tři číslice desetinné části.

Následující příklad používá specifikátor vlastního formátu "fff" k zobrazení milisekund v <xref:System.TimeSpan> hodnotu. "fff" používá nejprve jako jediný specifikátor formátu a následně se spojí dohromady se specifikátorem "s" v řetězci vlastního formátu.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Zpět k tabulce](#table)

<a name="f4Specifier"></a> 

## <a name="the-ffff-custom-format-specifier"></a>Specifikátor vlastního formátu "ffff"
Specifikátor vlastního formátu "ffff" (s 4 znaky "f") výstupů desetitisíciny sekundy v časovém intervalu. V rámci operace formátování se zkrátí všechny zbývající zlomkové číslice. Při operaci parsování, která volá <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody vstupní řetězec musí obsahovat přesně čtyři číslice desetinné části.

Následující příklad používá specifikátor vlastního formátu "ffff" k zobrazení desetitisíciny sekundy v <xref:System.TimeSpan> hodnotu. "ffff" používá nejprve jako jediný specifikátor formátu a následně se spojí dohromady se specifikátorem "s" v řetězci vlastního formátu.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Zpět k tabulce](#table)

<a name="f5Specifier"></a> 

## <a name="the-fffff-custom-format-specifier"></a>Specifikátor vlastního formátu "fffff"
Specifikátor vlastního formátu "fffff" (má pět znaků "f") výstupů stotisíciny sekundy v časovém intervalu. V rámci operace formátování se zkrátí všechny zbývající zlomkové číslice. Při operaci parsování, která volá <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody vstupní řetězec musí obsahovat přesně pěti zlomkové číslice.

Následující příklad používá specifikátor vlastního formátu "fffff" k zobrazení stotisíciny sekundy v <xref:System.TimeSpan> hodnotu. "fffff" používá nejprve jako jediný specifikátor formátu a následně se spojí dohromady se specifikátorem "s" v řetězci vlastního formátu.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Zpět k tabulce](#table)

<a name="f6Specifier"></a> 

## <a name="the-ffffff-custom-format-specifier"></a>Specifikátor vlastního formátu "ffffff"
Specifikátor vlastního formátu "ffffff" (s šest znaků "f") výstupů miliontiny sekundy v časovém intervalu. V rámci operace formátování se zkrátí všechny zbývající zlomkové číslice. Při operaci parsování, která volá <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody vstupní řetězec musí obsahovat přesně šesti zlomkové číslice.

Následující příklad používá specifikátor vlastního formátu "ffffff" k zobrazení miliontiny sekundy v <xref:System.TimeSpan> hodnotu. Je použita jako první jako jediný specifikátor formátu a následně se spojí dohromady se specifikátorem "s" v řetězci vlastního formátu.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Zpět k tabulce](#table)

<a name="f7Specifier"></a> 

## <a name="the-fffffff-custom-format-specifier"></a>Specifikátor vlastního formátu "fffffff"
Specifikátor vlastního formátu "fffffff" (s 7 znaků "f") výstupů Desetimiliontiny sekundy (nebo desetinné číslo značky) v časovém intervalu. Při operaci parsování, která volá <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody vstupní řetězec musí obsahovat přesně sedm zlomkové číslice.

Následující příklad používá specifikátor vlastního formátu "fffffff" k zobrazení desetinné počet taktů v <xref:System.TimeSpan> hodnotu. Je použita jako první jako jediný specifikátor formátu a následně se spojí dohromady se specifikátorem "s" v řetězci vlastního formátu.

[!code-csharp[Conceptual.TimeSpan.Custom#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
[!code-vb[Conceptual.TimeSpan.Custom#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]

[Zpět k tabulce](#table)

<a name="F_Specifier"></a> 

## <a name="the-f-custom-format-specifier"></a>Specifikátor vlastního formátu "F"
Specifikátor vlastního formátu "F" výstupy desetiny sekundy v časovém intervalu. V rámci operace formátování se zkrátí všechny zbývající zlomkové číslice. Pokud hodnota časový interval desetiny sekundy je nula, není zahrnut ve výsledném řetězci. Při operaci parsování, která volá <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metoda, přítomnost desetiny druhou číslici je volitelná.

Pokud je specifikátor vlastního formátu "F" použitý samostatně, zadejte tak, aby se chybně interpretován jako řetězec standardního formátu "%F".

Následující příklad používá specifikátor vlastního formátu "F" k zobrazení desetiny sekundy v <xref:System.TimeSpan> hodnotu. Také používá tento specifikátor vlastního formátu v rámci operace analýzy.

[!code-csharp[Conceptual.TimeSpan.Custom#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#21)]
[!code-vb[Conceptual.TimeSpan.Custom#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#21)]

[Zpět k tabulce](#table)

<a name="FF_Specifier"></a> 

## <a name="the-ff-custom-format-specifier"></a>Specifikátor vlastního formátu "FF"
Specifikátor vlastního formátu "FF" výstupy setiny sekundy v časovém intervalu. V rámci operace formátování se zkrátí všechny zbývající zlomkové číslice. Pokud jsou všechny koncové nuly desetinné části, nejsou zahrnuty ve výsledném řetězci. Při operaci parsování, která volá <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metoda, přítomnost desetin a setiny druhou číslici je volitelná.

Následující příklad používá specifikátor vlastního formátu "FF" k zobrazení setiny sekundy v <xref:System.TimeSpan> hodnotu. Také používá tento specifikátor vlastního formátu v rámci operace analýzy.

[!code-csharp[Conceptual.TimeSpan.Custom#22](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#22)]
[!code-vb[Conceptual.TimeSpan.Custom#22](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#22)]

[Zpět k tabulce](#table)

<a name="F3_Specifier"></a> 

## <a name="the-fff-custom-format-specifier"></a>Specifikátor vlastního formátu "FFF"
Specifikátor vlastního formátu "FFF" (se třemi znaky "F") výstupů milisekundy v časovém intervalu. V rámci operace formátování se zkrátí všechny zbývající zlomkové číslice. Pokud jsou všechny koncové nuly desetinné části, nejsou zahrnuty ve výsledném řetězci. Při operaci parsování, která volá <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metoda, přítomnost desetin, setinách a tisícin druhou číslici je volitelná.

Následující příklad používá specifikátor vlastního formátu "FFF" k zobrazení tisícin sekundy v <xref:System.TimeSpan> hodnotu. Také používá tento specifikátor vlastního formátu v rámci operace analýzy.

[!code-csharp[Conceptual.TimeSpan.Custom#23](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#23)]
[!code-vb[Conceptual.TimeSpan.Custom#23](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#23)]

[Zpět k tabulce](#table)

<a name="F4_Specifier"></a> 

## <a name="the-ffff-custom-format-specifier"></a>Specifikátor vlastního formátu "FFFF"
Specifikátor vlastního formátu "FFFF" (s 4 znaky "F") výstupů desetitisíciny sekundy v časovém intervalu. V rámci operace formátování se zkrátí všechny zbývající zlomkové číslice. Pokud jsou všechny koncové nuly desetinné části, nejsou zahrnuty ve výsledném řetězci. Při operaci parsování, která volá <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metoda, přítomnost desetin, setinách, tisícin a desetitisíciny druhou číslici je volitelná.

Následující příklad používá specifikátor vlastního formátu "FFFF" k zobrazení desetitisíciny sekundy v <xref:System.TimeSpan> hodnotu. Specifikátor vlastního formátu "FFFF" také používá v rámci operace analýzy.

[!code-csharp[Conceptual.TimeSpan.Custom#24](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#24)]
[!code-vb[Conceptual.TimeSpan.Custom#24](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#24)]

[Zpět k tabulce](#table)

<a name="F5_Specifier"></a> 

## <a name="the-fffff-custom-format-specifier"></a>Specifikátor vlastního formátu "FFFFF"
Specifikátor vlastního formátu "FFFFF" (má pět znaků "F") výstupů stotisíciny sekundy v časovém intervalu. V rámci operace formátování se zkrátí všechny zbývající zlomkové číslice. Pokud jsou všechny koncové nuly desetinné části, nejsou zahrnuty ve výsledném řetězci. Při operaci parsování, která volá <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metoda, přítomnost desetin, setinách, tisícin, desetitisíciny a stotisíciny druhou číslici je volitelná.

Následující příklad používá specifikátor vlastního formátu "FFFFF" k zobrazení stotisíciny sekundy v <xref:System.TimeSpan> hodnotu. Specifikátor vlastního formátu "FFFFF" také používá v rámci operace analýzy.

[!code-csharp[Conceptual.TimeSpan.Custom#25](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#25)]
[!code-vb[Conceptual.TimeSpan.Custom#25](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#25)]

[Zpět k tabulce](#table)

<a name="F6_Specifier"></a> 

## <a name="the-ffffff-custom-format-specifier"></a>Specifikátor vlastního formátu "FFFFFF"
Specifikátor vlastního formátu "FFFFFF" (s šest znaků "F") výstupů miliontiny sekundy v časovém intervalu. V rámci operace formátování se zkrátí všechny zbývající zlomkové číslice. Pokud jsou všechny koncové nuly desetinné části, nejsou zahrnuty ve výsledném řetězci. Při operaci parsování, která volá <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metoda, přítomnost desetin, setinách, tisícin, desetitisíciny, stotisíciny a miliontiny druhou číslici je volitelná.

Následující příklad používá specifikátor vlastního formátu "FFFFFF" k zobrazení miliontiny sekundy v <xref:System.TimeSpan> hodnotu. Také používá tento specifikátor vlastního formátu v rámci operace analýzy.

[!code-csharp[Conceptual.TimeSpan.Custom#26](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#26)]
[!code-vb[Conceptual.TimeSpan.Custom#26](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#26)]

[Zpět k tabulce](#table)

<a name="F7_Specifier"></a> 

## <a name="the-fffffff-custom-format-specifier"></a>Specifikátor vlastního formátu "FFFFFFF"
Specifikátor vlastního formátu "FFFFFFF" (s 7 znaků "F") výstupů Desetimiliontiny sekundy (nebo desetinné číslo značky) v časovém intervalu. Pokud jsou všechny koncové nuly desetinné části, nejsou zahrnuty ve výsledném řetězci. Při operaci parsování, která volá <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metoda, přítomnost sedm zlomkových číslic ve vstupním řetězci je volitelná.

Následující příklad používá specifikátor vlastního formátu "FFFFFFF" k zobrazení zlomkové části sekundy v <xref:System.TimeSpan> hodnotu. Také používá tento specifikátor vlastního formátu v rámci operace analýzy.

[!code-csharp[Conceptual.TimeSpan.Custom#27](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#27)]
[!code-vb[Conceptual.TimeSpan.Custom#27](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#27)]

[Zpět k tabulce](#table)

<a name="Other"></a> 

## <a name="other-characters"></a>Jiné znaky

Další znak bez řídícího znaku v řetězci formátu, včetně prázdných znaků, je interpretován jako specifikátor vlastního formátu. Ve většině případů přítomnost jiných znaků bez řídících znaků za následek <xref:System.FormatException>.

Existují dva způsoby, jak zahrnout literální znak v řetězci formátu:

- Uzavřete ho do jednoduchých uvozovek (oddělovač řetězcového literálu).

- Vložte před něj zpětné lomítko ("\\"), který je interpretován jako řídicí znak. To znamená, že v jazyce C#, formátovací řetězec musí být buď @-quoted, nebo znak musí být předcházen další zpětné lomítko.

  V některých případech budete muset používat podmíněnou logiku zahrnout uvozený uvozovacím znakem literálu v řetězci formátu. Následující příklad používá podmíněnou logiku zahrnout znaménko symbolu pro záporné časové intervaly.

  [!code-csharp[Conceptual.TimeSpan.Custom#29](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/negativevalues1.cs#29)]
  [!code-vb[Conceptual.TimeSpan.Custom#29](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/negativevalues1.vb#29)]

.NET nedefinuje gramatiku pro oddělovače v časových intervalech. To znamená, že oddělovače mezi dny a hodiny, hodiny a minuty, minut a sekund a sekund a zlomků sekund musí být zacházeno jako literální znak v řetězci formátu.

Následující příklad používá řídicí znak a jednoduché uvozovky k definování vlastní formátovací řetězec, který obsahuje slovo "minutes" ve výstupním řetězci.

[!code-csharp[Conceptual.TimeSpan.Custom#28](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/literal1.cs#28)]
[!code-vb[Conceptual.TimeSpan.Custom#28](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/literal1.vb#28)]

[Zpět k tabulce](#table)

## <a name="see-also"></a>Viz také

[Typy formátování](formatting-types.md)  
[Standardní řetězce formátu TimeSpan](standard-timespan-format-strings.md)  
