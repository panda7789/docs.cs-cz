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
ms.openlocfilehash: 354b9fe1171e8e41702db001ab3c0e5daa65431e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="custom-timespan-format-strings"></a>Vlastní řetězce formátu TimeSpan
A <xref:System.TimeSpan> řetězec formátu definuje řetězcovou reprezentaci <xref:System.TimeSpan> hodnotu, která je výsledkem operace formátování. Vlastní řetězec formátu se skládá z jednoho nebo více vlastních <xref:System.TimeSpan> specifikátory společně s libovolný počet literály formátu. Libovolný řetězec, který není [standardní řetězce formátu TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md) interpretována jako vlastní <xref:System.TimeSpan> řetězec formátu.  
  
> [!IMPORTANT]
>  Vlastní <xref:System.TimeSpan> specifikátory formátu nezahrnují zástupné symboly oddělovače, jako je například symboly, které oddělují dnů od hodin, hodiny od minut nebo sekundy od zlomků sekund. Místo toho tyto symboly musí být obsaženy ve vlastní řetězec formátu jako textové literály. Například `"dd\.hh\:mm"` definuje tečku (.) jako oddělovač mezi dny a hodiny a dvojtečkou (:) jako oddělovač mezi hodinách a minutách.  
>   
>  Vlastní <xref:System.TimeSpan> specifikátory formátu také nezahrnují symbol znaku, který umožňuje rozlišit mezi kladné a záporné časové intervaly. Chcete-li zahrnout symbol znaku, budete muset vytvořit řetězec formátu pomocí podmíněnou logiku. [Ostatní znaky](#Other) část obsahuje příklady.  
  
 Řetězcové vyjádření <xref:System.TimeSpan> hodnoty jsou vytvářeny voláním přetížení <xref:System.TimeSpan.ToString%2A?displayProperty=nameWithType> metoda a metody, které podporují složené formátování, jako například <xref:System.String.Format%2A?displayProperty=nameWithType>. Další informace najdete v tématu [typy formátování](../../../docs/standard/base-types/formatting-types.md) a [složené formátování](../../../docs/standard/base-types/composite-formatting.md). Následující příklad ukazuje použití řetězců vlastního formátu v operacích formátování.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customformatexample1.cs#1)]
 [!code-vb[Conceptual.TimeSpan.Custom#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customformatexample1.vb#1)]  
  
 Vlastní <xref:System.TimeSpan> řetězce formátu jsou také používány <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> a <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody k definování požadovaný formát vstupu řetězců pro operace analýzy. (Analýza převede řetězcovou reprezentaci hodnoty na tuto hodnotu.) Následující příklad ukazuje použití standardní řetězce formátu v operacích analýzy.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customparseexample1.cs#2)]
 [!code-vb[Conceptual.TimeSpan.Custom#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customparseexample1.vb#2)]  
  
<a name="table"></a> Následující tabulka popisuje vlastní datum a čas specifikátory formátu.  
  
|Specifikátor formátu|Popis|Příklad|  
|----------------------|-----------------|-------------|  
|"d", "%d"|Počet celých dní v časovém intervalu.<br /><br /> Další informace: ["D" vlastní formát specifikátor](#dSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `%d` --> "6"<br /><br /> `d\.hh\:mm` --> "6.14:32"|  
|"dd"-"dddddddd"|Počet celých dní v časovém intervalu, vyplní úvodními nulami podle potřeby.<br /><br /> Další informace: ["dd"-"dddddddd" specifikátory formátu vlastní](#ddSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `ddd` --> "006"<br /><br /> `dd\.hh\:mm` --> "06.14:32"|  
|"h", "%h"|Počet celých hodin v časovém intervalu, který se počítají jako součást dnů. Hodin nemají úvodní nuly.<br /><br /> Další informace: ["H" vlastní formát specifikátor](#hSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `%h` --> "14"<br /><br /> `hh\:mm` --> "14:32"|  
|"hh"|Počet celých hodin v časovém intervalu, který se počítají jako součást dnů. Hodin mít úvodní nuly.<br /><br /> Další informace: [vlastní specifikátor formátu "hh"](#hhSpecifier).|`new TimeSpan(6, 14, 32, 17, 685):`<br /><br /> `hh` --> "14"<br /><br /> `new TimeSpan(6, 8, 32, 17, 685):`<br /><br /> `hh` --> 08|  
|"m", "%m"|Počet celých minut v časovém intervalu, které nejsou součástí hodin nebo dnů. Řádu minut nemají úvodní nuly.<br /><br /> Další informace: ["M" vlastní formát specifikátor](#mSpecifier).|`new TimeSpan(6, 14, 8, 17, 685):`<br /><br /> `%m` --> "8"<br /><br /> `h\:m` --> "14:8"|  
|"mm"|Počet celých minut v časovém intervalu, které nejsou součástí hodin nebo dnů. Řádu minut mají počáteční nulu.<br /><br /> Další informace: ["Mm" vlastní formát specifikátor](#mmSpecifier).|`new TimeSpan(6, 14, 8, 17, 685):`<br /><br /> `mm` --> "08"<br /><br /> `new TimeSpan(6, 8, 5, 17, 685):`<br /><br /> `d\.hh\:mm\:ss` --> 6.08:05:17|  
|"s", "%s.|Počet celých sekund v časovém intervalu, které nejsou součástí hodiny, dny nebo minut. Řádu sekund nemají úvodní nuly.<br /><br /> Další informace: ["S" vlastní formát specifikátor](#sSpecifier).|`TimeSpan.FromSeconds(12.965)`:<br /><br /> `%s` --> 12<br /><br /> `s\.fff` --> 12.965|  
|"ss"|Počet celých sekund v časovém intervalu, které nejsou součástí hodiny, dny nebo minut.  Řádu sekund mají počáteční nulu.<br /><br /> Další informace: ["Ss" vlastní formát specifikátor](#ssSpecifier).|`TimeSpan.FromSeconds(6.965)`:<br /><br /> `ss` --> 06<br /><br /> `ss\.fff` --> 06.965|  
|"f", "%f"|Desetin sekundy v určitém časovém intervalu.<br /><br /> Další informace: ["F" vlastní formát specifikátor](#fSpecifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `f` --> 8<br /><br /> `ss\.f` --> 06.8|  
|"ff"|Setiny sekundy v určitém časovém intervalu.<br /><br /> Další informace:["Vypnuto" vlastní formát specifikátor](#ffSpecifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `ff` --> 89<br /><br /> `ss\.ff` --> 06.89|  
|"fff"|Počet milisekund v určitém časovém intervalu.<br /><br /> Další informace: ["Fff" vlastní formát specifikátor](#f3Specifier).|`TimeSpan.FromSeconds(6.895)`:<br /><br /> `fff` --> 895<br /><br /> `ss\.fff` --> 06.895|  
|"ffff"|Desetitisíciny sekundy v časovém intervalu.<br /><br /> Další informace: [ffff. vlastní formát specifikátor](#f4Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `ffff` --> 8954<br /><br /> `ss\.ffff` --> 06.8954|  
|"fffff"|Stotisíciny sekundy v časovém intervalu.<br /><br /> Další informace: ["Fffff" vlastní formát specifikátor](#f5Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `fffff` --> 89543<br /><br /> `ss\.fffff` --> 06.89543|  
|"ffffff"|Miliontin sekundy v určitém časovém intervalu.<br /><br /> Další informace: [vlastní specifikátor formátu "ffffff"](#f6Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `ffffff` --> 895432<br /><br /> `ss\.ffffff` --> 06.895432|  
|"fffffff"|Desetimiliontin druhý (nebo zlomkové rysky) v určitém časovém intervalu.<br /><br /> Další informace: ["Fffffff" vlastní formát specifikátor](#f7Specifier).|`TimeSpan.Parse("0:0:6.8954321")`:<br /><br /> `fffffff` --> 8954321<br /><br /> `ss\.fffffff` --> 06.8954321|  
|"F", "%F"|Desetin sekundy v určitém časovém intervalu. Pokud je číslice nula, nezobrazí se žádná hodnota.<br /><br /> Další informace: [The "F" vlastní formát specifikátor](#F_Specifier).|`TimeSpan.Parse("00:00:06.32")`:<br /><br /> `%F`: 3<br /><br /> `TimeSpan.Parse("0:0:3.091")`:<br /><br /> `ss\.F`: 03.|  
|"FF"|Setiny sekundy v určitém časovém intervalu. Jakékoli koncové nuly nebo dvě zlomkové nuly nejsou zahrnuty.<br /><br /> Další informace: ["Vypnuto" vlastní formát specifikátor](#FF_Specifier).|`TimeSpan.Parse("00:00:06.329")`:<br /><br /> `FF`: 32<br /><br /> `TimeSpan.Parse("0:0:3.101")`:<br /><br /> `ss\.FF`: 03.1|  
|"FFF"|Počet milisekund v určitém časovém intervalu. Jakékoli zlomkové koncové nuly nejsou zahrnuty.<br /><br /> Další informace:|`TimeSpan.Parse("00:00:06.3291")`:<br /><br /> `FFF`: 329<br /><br /> `TimeSpan.Parse("0:0:3.1009")`:<br /><br /> `ss\.FFF`: 03.1|  
|"FFFF"|Desetitisíciny sekundy v časovém intervalu. Jakékoli zlomkové koncové nuly nejsou zahrnuty.<br /><br /> Další informace: [specifikátor formátu "FFFF" vlastní](#F4_Specifier).|`TimeSpan.Parse("00:00:06.32917")`:<br /><br /> `FFFFF`: 3291<br /><br /> `TimeSpan.Parse("0:0:3.10009")`:<br /><br /> `ss\.FFFF`: 03.1|  
|"FFFFF"|Stotisíciny sekundy v časovém intervalu. Jakékoli zlomkové koncové nuly nejsou zahrnuty.<br /><br /> Další informace: [vlastní specifikátor formátu "FFFFF"](#F5_Specifier).|`TimeSpan.Parse("00:00:06.329179")`:<br /><br /> `FFFFF`: 32917<br /><br /> `TimeSpan.Parse("0:0:3.100009")`:<br /><br /> `ss\.FFFFF`: 03.1|  
|"FFFFFF"|Miliontin sekundy v určitém časovém intervalu. Jakékoli zlomkové koncové nuly nejsou zobrazeny.<br /><br /> Další informace: [vlastní specifikátor formátu "FFFFFF"](#F6_Specifier).|`TimeSpan.Parse("00:00:06.3291791")`:<br /><br /> `FFFFFF`: 329179<br /><br /> `TimeSpan.Parse("0:0:3.1000009")`:<br /><br /> `ss\.FFFFFF`: 03.1|  
|"FFFFFFF"|Do 10 milionů sekundy v určitém časovém intervalu. Jakékoli zlomkové koncové nuly nebo sedm nul se nezobrazí.<br /><br /> Další informace: [vlastní specifikátor formátu "FFFFFFF"](#F7_Specifier).|`TimeSpan.Parse("00:00:06.3291791")`:<br /><br /> `FFFFFF`: 3291791<br /><br /> `TimeSpan.Parse("0:0:3.1900000")`:<br /><br /> `ss\.FFFFFF`: 03.19|  
|*' řetězec*.|Oddělovač řetězcového literálu.<br /><br /> Další informace: [ostatní znaky](#Other).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh':'mm':'ss` --> "14:32:17"|  
|\|Řídicí znak.<br /><br /> Další informace:[ostatní znaky](#Other).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh\:mm\:ss` --> "14:32:17"|  
|Jakýkoli jiný znak|Libovolný znak neuvozené interpretována jako vlastní specifikátor formátu.<br /><br /> Další informace: [dalšími znaky](#Other).|`new TimeSpan(14, 32, 17):`<br /><br /> `hh\:mm\:ss` --> "14:32:17"|  
  
<a name="dSpecifier"></a>   
## <a name="the-d-custom-format-specifier"></a>Specifikátor vlastního formátu "d".  
 Specifikátor vlastní formát "d" výstupy hodnotu <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> vlastnosti, která představuje počet celých dní v časovém intervalu. Vyprodukuje úplné počet dní v <xref:System.TimeSpan> hodnoty, i když hodnota má více než jednu číslici. Pokud hodnota <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> vlastnost nula, specifikátor výstupy "0".  
  
 Pokud je specifikátor "d" vlastní formát použitý samostatně, zadejte "%d" tak, aby nebyl chybně interpretován jako standardní formátovací řetězec. V následujícím příkladu je uvedena ukázka.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#3)]
 [!code-vb[Conceptual.TimeSpan.Custom#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#3)]  
  
 Následující příklad ukazuje použití specifikátor vlastní formát "d".  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#4)]
 [!code-vb[Conceptual.TimeSpan.Custom#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#4)]  
  
 [Zpět k tabulce](#table)  
  
<a name="ddSpecifier"></a>   
## <a name="the-dd-dddddddd-custom-format-specifiers"></a>"dd"-"dddddddd" vlastní specifikátory formátu  
 "Dd", "ddd", "dddd", "ddddd", "dddddd", "ddddddd" a "dddddddd" vlastní formát specifikátory výstupní hodnotu <xref:System.TimeSpan.Days%2A?displayProperty=nameWithType> vlastnosti, která představuje počet celých dní v časovém intervalu.  
  
 Výstupní řetězec obsahuje minimální počet číslic určený počet znaků "d" v specifikátor formátu a je doplněn úvodními nulami podle potřeby. Pokud číslic v počtu dní překračuje počet znaků "d" v specifikátor formátu, úplná počet dní, je výstup ve výsledném řetězci.  
  
 Následující příklad používá tyto specifikátory formátu zobrazíte řetězcovou reprezentaci dva <xref:System.TimeSpan> hodnoty. Komponentu dnů v prvním časovém intervalu hodnotu nula; Hodnota komponentu dnů druhý je 365.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#5)]
 [!code-vb[Conceptual.TimeSpan.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#5)]  
  
 [Zpět k tabulce](#table)  
  
<a name="hSpecifier"></a>   
## <a name="the-h-custom-format-specifier"></a>Specifikátor vlastního formátu "h"  
 Specifikátor vlastní formát "h" výstupy hodnotu <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> vlastnosti, která představuje počet celých hodin v časovém intervalu, které nejsou počítány jako součást komponenty dní. Vrátí jedna číslice řetězcovou hodnotu, pokud hodnota <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> vlastnost je 0 až 9, a vrátí letopočty řetězcovou hodnotu, pokud hodnota <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> vlastnost rozsahu od 10 do 23.  
  
 Pokud je "h" vlastní specifikátor formátu použitý samostatně, zadejte "%h" tak, aby nebyl chybně interpretován jako standardní formátovací řetězec. V následujícím příkladu je uvedena ukázka.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#6)]
 [!code-vb[Conceptual.TimeSpan.Custom#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#6)]  
  
 V operaci analýzy normálně, vstupní řetězec, který obsahuje pouze jedno číslo interpretována jako počet dnů. Můžete použít specifikátor vlastní formát "%h" místo interpretace číselných řetězců, jako je počet hodin. V následujícím příkladu je uvedena ukázka.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#8)]
 [!code-vb[Conceptual.TimeSpan.Custom#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#8)]  
  
 Následující příklad ukazuje použití specifikátor vlastní formát "h".  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#7)]
 [!code-vb[Conceptual.TimeSpan.Custom#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#7)]  
  
 [Zpět k tabulce](#table)  
  
<a name="hhSpecifier"></a>   
## <a name="the-hh-custom-format-specifier"></a>Specifikátor vlastního formátu "hh"  
 Specifikátor vlastní formátu "hh" výstupy hodnotu <xref:System.TimeSpan.Hours%2A?displayProperty=nameWithType> vlastnosti, která představuje počet celých hodin v časovém intervalu, které nejsou počítány jako součást komponenty dní. Pro hodnoty od 0 do 9 obsahuje výstupní řetězec úvodní nuly.  
  
 V operaci analýzy normálně, vstupní řetězec, který obsahuje pouze jedno číslo interpretována jako počet dnů. Můžete použít specifikátor vlastního formátu "hh" místo interpretace číselných řetězců, jako je počet hodin. V následujícím příkladu je uvedena ukázka.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#9)]
 [!code-vb[Conceptual.TimeSpan.Custom#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#9)]  
  
 Následující příklad ukazuje použití specifikátor vlastní formátu "hh".  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#10)]
 [!code-vb[Conceptual.TimeSpan.Custom#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#10)]  
  
 [Zpět k tabulce](#table)  
  
<a name="mSpecifier"></a>   
## <a name="the-m-custom-format-specifier"></a>Specifikátor vlastního formátu "m"  
 Specifikátor vlastní formát "m" výstupy hodnotu <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> vlastnosti, která představuje počet celých minut v časovém intervalu, které nejsou počítány jako součást komponenty dní. Vrátí jedna číslice řetězcovou hodnotu, pokud hodnota <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> vlastnost je 0 až 9, a vrátí letopočty řetězcovou hodnotu, pokud hodnota <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> vlastnost rozsahu od 10 do 59.  
  
 Pokud je specifikátor "m" vlastní formát použitý samostatně, zadejte "%m" tak, aby nebyl chybně interpretován jako standardní formátovací řetězec. V následujícím příkladu je uvedena ukázka.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#6)]
 [!code-vb[Conceptual.TimeSpan.Custom#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#6)]  
  
 V operaci analýzy normálně, vstupní řetězec, který obsahuje pouze jedno číslo interpretována jako počet dnů. Můžete použít vlastní formát specifikátor "%m" místo interpretace číselných řetězců jako počet minut. V následujícím příkladu je uvedena ukázka.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#11)]
 [!code-vb[Conceptual.TimeSpan.Custom#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#11)]  
  
 Následující příklad ukazuje použití specifikátor vlastní formát "m".  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#12)]
 [!code-vb[Conceptual.TimeSpan.Custom#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#12)]  
  
 [Zpět k tabulce](#table)  
  
<a name="mmSpecifier"></a>   
## <a name="the-mm-custom-format-specifier"></a>Specifikátor vlastního formátu "mm"  
 Specifikátor vlastní formát "mm" výstupy hodnotu <xref:System.TimeSpan.Minutes%2A?displayProperty=nameWithType> vlastnosti, která představuje počet celých minut v časovém intervalu, který není součástí hodin a dnů. Pro hodnoty od 0 do 9 obsahuje výstupní řetězec úvodní nuly.  
  
 V operaci analýzy normálně, vstupní řetězec, který obsahuje pouze jedno číslo interpretována jako počet dnů. Můžete použít vlastní formát specifikátor "mm" místo interpretace číselných řetězců jako počet minut. V následujícím příkladu je uvedena ukázka.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#13)]
 [!code-vb[Conceptual.TimeSpan.Custom#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#13)]  
  
 Následující příklad ukazuje použití specifikátor vlastní formát "mm".  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#14)]
 [!code-vb[Conceptual.TimeSpan.Custom#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#14)]  
  
 [Zpět k tabulce](#table)  
  
<a name="sSpecifier"></a>   
## <a name="the-s-custom-format-specifier"></a>Specifikátor vlastního formátu "s"  
 Specifikátor vlastní formát "s" výstupy hodnotu <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> vlastnosti, která představuje počet celých sekund v časovém intervalu, který není součástí jeho komponenty minut, hodin nebo dnů. Vrátí jedna číslice řetězcovou hodnotu, pokud hodnota <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> vlastnost je 0 až 9, a vrátí letopočty řetězcovou hodnotu, pokud hodnota <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> vlastnost rozsahu od 10 do 59.  
  
 Pokud je "s" vlastní specifikátor formátu použitý samostatně, zadejte "%s" tak, aby nebyl chybně interpretován jako standardní formátovací řetězec. V následujícím příkladu je uvedena ukázka.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#15)]
 [!code-vb[Conceptual.TimeSpan.Custom#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#15)]  
  
 V operaci analýzy normálně, vstupní řetězec, který obsahuje pouze jedno číslo interpretována jako počet dnů. Můžete použít specifikátor vlastní formát "%s" místo číselných řetězců interpretovat jako počet sekund. V následujícím příkladu je uvedena ukázka.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#17)]
 [!code-vb[Conceptual.TimeSpan.Custom#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#17)]  
  
 Následující příklad ukazuje použití specifikátor vlastní formát "s".  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#16)]
 [!code-vb[Conceptual.TimeSpan.Custom#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#16)]  
  
 [Zpět k tabulce](#table)  
  
<a name="ssSpecifier"></a>   
## <a name="the-ss-custom-format-specifier"></a>Specifikátor vlastního formátu "ss"  
 Specifikátor vlastní formát "ss" výstupy hodnotu <xref:System.TimeSpan.Seconds%2A?displayProperty=nameWithType> vlastnosti, která představuje počet celých sekund v časovém intervalu, který není součástí jeho komponenty minut, hodin nebo dnů. Pro hodnoty od 0 do 9 obsahuje výstupní řetězec úvodní nuly.  
  
 V operaci analýzy normálně, vstupní řetězec, který obsahuje pouze jedno číslo interpretována jako počet dnů. Můžete použít vlastní formát specifikátor "ss" místo interpretace číselných řetězců jako počet sekund. V následujícím příkladu je uvedena ukázka.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#18)]
 [!code-vb[Conceptual.TimeSpan.Custom#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#18)]  
  
 Následující příklad ukazuje použití vlastní formát specifikátor "ss".  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/customexamples1.cs#19)]
 [!code-vb[Conceptual.TimeSpan.Custom#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/customexamples1.vb#19)]  
  
 [Zpět k tabulce](#table)  
  
<a name="fSpecifier"></a>   
## <a name="thef-custom-format-specifier"></a>Specifikátor vlastní formát "f"  
 Specifikátor vlastní formát "f" výstupy desetin sekundy v určitém časovém intervalu. V operaci formátování se zkrátí všechny zbývající míst za desetinnou čárkou. V operaci analýzy, která volá <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metoda, vstupní řetězec musí obsahovat přesně jeden zlomkové číslice.  
  
 Pokud je specifikátor "f" vlastní formát použitý samostatně, zadejte "%f" tak, aby nebyl chybně interpretován jako standardní formátovací řetězec.  
  
 Následující příklad používá specifikátor "f" vlastní formát pro zobrazení desetin sekundy v <xref:System.TimeSpan> hodnotu. "f" používá nejdříve jako jediný specifikátor formátu a potom v kombinaci s specifikátor "s" v řetězci vlastní formát.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
 [!code-vb[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]  
  
 [Zpět k tabulce](#table)  
  
<a name="ffSpecifier"></a>   
## <a name="the-ff-custom-format-specifier"></a>Specifikátor vlastního formátu "ff"  
 Specifikátor vlastní formát "vypnuto" výstupy setiny sekundy v určitém časovém intervalu. V operaci formátování se zkrátí všechny zbývající míst za desetinnou čárkou. V operaci analýzy, která volá <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metoda, vstupní řetězec musí obsahovat přesně dvě míst za desetinnou čárkou.  
  
 Následující příklad používá specifikátor "vypnuto" vlastní formát pro zobrazení setin sekundy v <xref:System.TimeSpan> hodnotu. "vypnuto" používá nejdříve jako jediný specifikátor formátu a potom v kombinaci s specifikátor "s" v řetězci vlastní formát.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
 [!code-vb[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]  
  
 [Zpět k tabulce](#table)  
  
<a name="f3Specifier"></a>   
## <a name="the-fff-custom-format-specifier"></a>Specifikátor vlastního formátu "fff"  
 Specifikátor vlastní formát "fff" (s tři znaky "f") výstupy milisekundy v určitém časovém intervalu. V operaci formátování se zkrátí všechny zbývající míst za desetinnou čárkou. V operaci analýzy, která volá <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metoda, vstupní řetězec musí obsahovat přesně tři míst za desetinnou čárkou.  
  
 Následující příklad používá k zobrazení milisekund v specifikátor vlastní formát "fff" <xref:System.TimeSpan> hodnotu. "fff" používá nejdříve jako jediný specifikátor formátu a potom v kombinaci s specifikátor "s" v řetězci vlastní formát.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
 [!code-vb[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]  
  
 [Zpět k tabulce](#table)  
  
<a name="f4Specifier"></a>   
## <a name="the-ffff-custom-format-specifier"></a>Specifikátor vlastního formátu "ffff"  
 Specifikátor vlastní formát "ffff" (s čtyři znaky "f") výstupy desetitisíciny sekundy v časovém intervalu. V operaci formátování se zkrátí všechny zbývající míst za desetinnou čárkou. V operaci analýzy, která volá <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metoda, vstupní řetězec musí obsahovat přesně čtyři míst za desetinnou čárkou.  
  
 Následující příklad používá specifikátor "ffff" vlastní formát pro zobrazení desetitisícín sekundy v <xref:System.TimeSpan> hodnotu. "ffff" používá nejdříve jako jediný specifikátor formátu a potom v kombinaci s specifikátor "s" v řetězci vlastní formát.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
 [!code-vb[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]  
  
 [Zpět k tabulce](#table)  
  
<a name="f5Specifier"></a>   
## <a name="the-fffff-custom-format-specifier"></a>Specifikátor vlastního formátu "fffff"  
 Specifikátor vlastní formát "fffff" (s pěti "znaky f) výstupy stotisíciny sekundy v časovém intervalu. V operaci formátování se zkrátí všechny zbývající míst za desetinnou čárkou. V operaci analýzy, která volá <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metoda, vstupní řetězec musí obsahovat přesně pět míst za desetinnou čárkou.  
  
 Následující příklad používá k zobrazení stotisícin sekundy v vlastní formátu "fffff" <xref:System.TimeSpan> hodnotu. "fffff" používá nejdříve jako jediný specifikátor formátu a potom v kombinaci s specifikátor "s" v řetězci vlastní formát.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
 [!code-vb[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]  
  
 [Zpět k tabulce](#table)  
  
<a name="f6Specifier"></a>   
## <a name="the-ffffff-custom-format-specifier"></a>Specifikátor vlastního formátu "ffffff"  
 Specifikátor vlastní formát "ffffff" (s šest znaků "f") výstupy miliontin sekundy v určitém časovém intervalu. V operaci formátování se zkrátí všechny zbývající míst za desetinnou čárkou. V operaci analýzy, která volá <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metoda, vstupní řetězec musí obsahovat přesně šest míst za desetinnou čárkou.  
  
 Následující příklad používá pro zobrazení miliontin sekundy v vlastní formátu "ffffff" <xref:System.TimeSpan> hodnotu. Je použita jako první jako jediný specifikátor formátu a potom v kombinaci s specifikátor "s" v řetězci vlastní formát.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
 [!code-vb[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]  
  
 [Zpět k tabulce](#table)  
  
<a name="f7Specifier"></a>   
## <a name="the-fffffff-custom-format-specifier"></a>Specifikátor vlastního formátu "fffffff"  
 Specifikátor vlastní formát "fffffff" (s sedm "znaky f) výstupy Desetimiliontiny druhý (nebo zlomkové počet značek) v určitém časovém intervalu. V operaci analýzy, která volá <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metoda, vstupní řetězec musí obsahovat přesně sedm míst za desetinnou čárkou.  
  
 Následující příklad používá vlastní formátu "FFFFFFF" zobrazíte zlomkové počet značek v <xref:System.TimeSpan> hodnotu. Je použita jako první jako jediný specifikátor formátu a potom v kombinaci s specifikátor "s" v řetězci vlastní formát.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/fspecifiers1.cs#20)]
 [!code-vb[Conceptual.TimeSpan.Custom#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/fspecifiers1.vb#20)]  
  
 [Zpět k tabulce](#table)  
  
<a name="F_Specifier"></a>   
## <a name="the-f-custom-format-specifier"></a>Specifikátor vlastního formátu "F"  
 Specifikátor vlastní formát "F" výstupy desetin sekundy v určitém časovém intervalu. V operaci formátování se zkrátí všechny zbývající míst za desetinnou čárkou. Pokud časový interval desetin sekundy hodnotu nula, není zahrnut ve výsledném řetězci. V operaci analýzy, která volá <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody přítomnost druhý číslice desetin je volitelný.  
  
 Pokud je specifikátor "F" vlastní formát použitý samostatně, zadejte "%F" tak, aby nebyl chybně interpretován jako standardní formátovací řetězec.  
  
 Následující příklad používá specifikátor "F" vlastní formát pro zobrazení desetin sekundy v <xref:System.TimeSpan> hodnotu. V operaci analýzy také používá vlastní specifikátor formátu.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#21)]
 [!code-vb[Conceptual.TimeSpan.Custom#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#21)]  
  
 [Zpět k tabulce](#table)  
  
<a name="FF_Specifier"></a>   
## <a name="the-ff-custom-format-specifier"></a>Specifikátor vlastního formátu "FF"  
 Specifikátor vlastní formát "Vypnuto" výstupy setiny sekundy v určitém časovém intervalu. V operaci formátování se zkrátí všechny zbývající míst za desetinnou čárkou. Pokud jsou všechny koncové zlomkové nuly, nejsou zahrnuty ve výsledném řetězci. V operaci analýzy, která volá <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody přítomnost desetin a druhý číslice setin je volitelný.  
  
 Následující příklad používá specifikátor "Vypnuto" vlastní formát pro zobrazení setin sekundy v <xref:System.TimeSpan> hodnotu. V operaci analýzy také používá vlastní specifikátor formátu.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#22)]
 [!code-vb[Conceptual.TimeSpan.Custom#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#22)]  
  
 [Zpět k tabulce](#table)  
  
<a name="F3_Specifier"></a>   
## <a name="the-fff-custom-format-specifier"></a>Specifikátor vlastního formátu "FFF"  
 Specifikátor vlastní formát "FFF" (s tři znaky "F") výstupy milisekundy v určitém časovém intervalu. V operaci formátování se zkrátí všechny zbývající míst za desetinnou čárkou. Pokud jsou všechny koncové zlomkové nuly, nejsou zahrnuty ve výsledném řetězci. V operaci analýzy, která volá <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody přítomnost desetin, setin a tisícin druhý číslice je volitelný.  
  
 Následující příklad používá specifikátor "FFF" vlastní formát pro zobrazení tisícín sekundy v <xref:System.TimeSpan> hodnotu. V operaci analýzy také používá vlastní specifikátor formátu.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#23)]
 [!code-vb[Conceptual.TimeSpan.Custom#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#23)]  
  
 [Zpět k tabulce](#table)  
  
<a name="F4_Specifier"></a>   
## <a name="the-ffff-custom-format-specifier"></a>Specifikátor vlastního formátu "FFFF"  
 Specifikátor vlastní formát "FFFF" (s čtyři znaky "F") výstupy desetitisíciny sekundy v časovém intervalu. V operaci formátování se zkrátí všechny zbývající míst za desetinnou čárkou. Pokud jsou všechny koncové zlomkové nuly, nejsou zahrnuty ve výsledném řetězci. V operaci analýzy, která volá <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody přítomnost desetin, setin, tisícin a desetitisícín druhý číslice je volitelný.  
  
 Následující příklad používá specifikátor "FFFF" vlastní formát pro zobrazení desetitisícín sekundy v <xref:System.TimeSpan> hodnotu. V operaci analýzy také používá vlastní formát specifikátor "FFFF".  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#24](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#24)]
 [!code-vb[Conceptual.TimeSpan.Custom#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#24)]  
  
 [Zpět k tabulce](#table)  
  
<a name="F5_Specifier"></a>   
## <a name="the-fffff-custom-format-specifier"></a>Specifikátor vlastního formátu "FFFFF"  
 Specifikátor vlastní formát "FFFFF" (s pěti "znaky F) výstupy stotisíciny sekundy v časovém intervalu. V operaci formátování se zkrátí všechny zbývající míst za desetinnou čárkou. Pokud jsou všechny koncové zlomkové nuly, nejsou zahrnuty ve výsledném řetězci. V operaci analýzy, která volá <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody přítomnost desetin, setin, tisícin, desetitisícín a stotisícin druhý číslice je volitelný.  
  
 Následující příklad používá k zobrazení stotisícin sekundy v vlastní formátu "fffff" <xref:System.TimeSpan> hodnotu. V operaci analýzy také používá vlastní formátu "fffff".  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#25](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#25)]
 [!code-vb[Conceptual.TimeSpan.Custom#25](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#25)]  
  
 [Zpět k tabulce](#table)  
  
<a name="F6_Specifier"></a>   
## <a name="the-ffffff-custom-format-specifier"></a>Specifikátor vlastního formátu "FFFFFF"  
 Specifikátor vlastní formát "FFFFFF" (s šest znaků "F") výstupy miliontin sekundy v určitém časovém intervalu. V operaci formátování se zkrátí všechny zbývající míst za desetinnou čárkou. Pokud jsou všechny koncové zlomkové nuly, nejsou zahrnuty ve výsledném řetězci. V operaci analýzy, která volá <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody přítomnost desetin, setin, tisícin, desetitisícín, stotisícin a miliontin druhý číslice je volitelný.  
  
 Následující příklad používá pro zobrazení miliontin sekundy v vlastní formátu "ffffff" <xref:System.TimeSpan> hodnotu. V operaci analýzy také používá vlastní specifikátor formátu.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#26](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#26)]
 [!code-vb[Conceptual.TimeSpan.Custom#26](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#26)]  
  
 [Zpět k tabulce](#table)  
  
<a name="F7_Specifier"></a>   
## <a name="the-fffffff-custom-format-specifier"></a>Specifikátor vlastního formátu "FFFFFFF"  
 Specifikátor vlastní formát "FFFFFFF" (s sedm "znaky F) výstupy Desetimiliontiny druhý (nebo zlomkové počet značek) v určitém časovém intervalu. Pokud jsou všechny koncové zlomkové nuly, nejsou zahrnuty ve výsledném řetězci. V operaci analýzy, která volá <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> nebo <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody přítomnost sedm míst za desetinnou čárkou ve vstupním řetězci je volitelný.  
  
 Následující příklad používá vlastní formátu "FFFFFFF" zobrazíte zlomkové části sekundy v <xref:System.TimeSpan> hodnotu. V operaci analýzy také používá vlastní specifikátor formátu.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#27](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/f_specifiers1.cs#27)]
 [!code-vb[Conceptual.TimeSpan.Custom#27](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/f_specifiers1.vb#27)]  
  
 [Zpět k tabulce](#table)  
  
<a name="Other"></a>   
## <a name="other-characters"></a>Dalšími znaky  
 Další neuvozené znaky v řetězci formátu, včetně prázdný znak, interpretována jako vlastní specifikátor formátu. Ve většině případů přítomnost jiných znaků bez řídících znak za následek <xref:System.FormatException>.  
  
 Existují dva způsoby, jak použít literálu znak v řetězci formátu:  
  
-   Vložte jej do jednoduchých uvozovek (řetězcového literálu oddělovač).  
  
-   Předcházet obráceným lomítkem ("\\"), který je interpretován jako řídicí znak. To znamená, že v jazyce C#, buď musí být řetězec formátu @-quoted, nebo se literál musí předcházet další zpětné lomítko.  
  
     V některých případech budete muset použít podmíněnou logiku zahrnout uvozený literál ve formátovacím řetězci. Následující příklad používá podmíněnou logiku pro zahrnutí symbol znaku záporné časové intervaly.  
  
     [!code-csharp[Conceptual.TimeSpan.Custom#29](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/negativevalues1.cs#29)]
     [!code-vb[Conceptual.TimeSpan.Custom#29](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/negativevalues1.vb#29)]  
  
 Rozhraní .NET nedefinuje gramatiku pro oddělovače v časových intervalech. To znamená, že oddělovače mezi dny a hodiny, hodin a minut, minut a sekund a sekund a zlomků sekund musí být zacházeno jako znakové literály ve formátovacím řetězci.  
  
 Následující příklad používá k definování vlastní formát řetězec, který obsahuje slovo "minutes" do výstupního řetězce řídicí znak a jednoduché uvozovky.  
  
 [!code-csharp[Conceptual.TimeSpan.Custom#28](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.custom/cs/literal1.cs#28)]
 [!code-vb[Conceptual.TimeSpan.Custom#28](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.custom/vb/literal1.vb#28)]  
  
 [Zpět k tabulce](#table)  
  
## <a name="see-also"></a>Viz také  
 [Typy formátování](../../../docs/standard/base-types/formatting-types.md)  
 [Standardní řetězce formátu TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)
