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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 665c90ca9950424be21539a83992e1c36dc51ba7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="custom-date-and-time-format-strings"></a>Vlastní řetězce formátu data a času
Řetězec formátu data a času definuje textovou reprezentaci hodnoty <xref:System.DateTime> nebo <xref:System.DateTimeOffset> hodnotu, která je výsledkem operace formátování. Může také definovat reprezentaci hodnoty data a času nezbytnou v rámci operace analýzy a úspěšně tak řetězec převést na datum a čas. Řetězec vlastního formátu se skládá z jednoho nebo více vlastních specifikátorů formátu data a času. Libovolný řetězec, který není [řetězec formátu standardní hodnoty data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) interpretována jako vlastní data a času řetězec formátu.  
  
 Vlastní hodnota data a řetězce formátu časových lze použít s oběma <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnoty.  
  
> [!TIP]
>  Si můžete stáhnout [formátování nástroj](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d), aplikace, která umožňuje použití formátu řetězce na datum a čas nebo číselné hodnoty a zobrazí výsledný řetězec.  
  
<a name="table"></a> V operacích formátování, může být vlastní řetězců data a času formát použít buď pomocí `ToString` metoda instance data a času nebo s metodu, která podporuje složené formátování. Následující příklad znázorňuje oba způsoby použití.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#17](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/custandformatting1.cs#17)]
 [!code-vb[Formatting.DateAndTime.Custom#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/custandformatting1.vb#17)]  
  
 Při analýze operace, vlastní řetězců data a času formát lze použít s <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, a <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> metody. Aby operace analýzy mohla být úspěšně provedena, požadují tyto metody, aby vstupní řetězec přesně odpovídal určitému vzoru. Následující příklad ukazuje volání <xref:System.DateTimeOffset.ParseExact%28System.String%2CSystem.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metoda analyzovat data, která musí zahrnovat za den, měsíc a rok letopočty.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#18](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/custandparsing1.cs#18)]
 [!code-vb[Formatting.DateAndTime.Custom#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/custandparsing1.vb#18)]  
  
 Následující tabulka popisuje specifikátory vlastního formátu data a času a zobrazuje výsledný řetězec, který je vytvořen jednotlivými specifikátory formátu. Ve výchozím nastavení odráží výsledný řetězec konvence formátování jazykové verze en-US. Pokud konkrétní specifikátor formátu vytváří lokalizovaný výsledný řetězec, je v příkladu rovněž uvedena jazyková verze, na kterou se výsledný řetězec vztahuje. Další informace o používání řetězců vlastního formátu data a času naleznete v oddílu Poznámky.  
  
|Specifikátor formátu|Popis|Příklady|  
|----------------------|-----------------|--------------|  
|"d"|Den měsíce, od 1 do 31.<br /><br /> Další informace: ["D" vlastní formát specifikátor](#dSpecifier).|2009-06-01T13:45:30 -> 1<br /><br /> 2009-06-15T13:45:30 -> 15|  
|"dd"|Den měsíce, od 01 do 31.<br /><br /> Další informace: [vlastní specifikátor formátu "dd"](#ddSpecifier).|2009-06-01T13:45:30 -> 01<br /><br /> 2009-06-15T13:45:30 -> 15|  
|"ddd"|Zkrácený název dne v týdnu.<br /><br /> Další informace: [vlastní specifikátor formátu "ddd"](#dddSpecifier).|2009-06-15T13:45:30 -> Mon (en US)<br /><br /> 2009-06-15T13:45:30 -> Пн (ru-RU)<br /><br /> 2009-06-15T13:45:30 -> logické jednotky. (fr-FR)|  
|"dddd"|Úplný název dne v týdnu.<br /><br /> Další informace: [vlastní specifikátor formátu "dddd"](#ddddSpecifier).|2009-06-15T13:45:30 -> pondělí (en US)<br /><br /> 2009-06-15T13:45:30 -> понедельник (ru-RU)<br /><br /> 2009-06-15T13:45:30 -> lundi (fr-FR)|  
|"f"|Desetiny sekundy v hodnotě data a času.<br /><br /> Další informace: ["F" vlastní formát specifikátor](#fSpecifier).|2009-06-15T13:45:30.6170000 -&GT; 6<br /><br /> 2009-06-15T13:45:30.05 -&GT; 0|  
|"ff"|Setiny sekundy v hodnotě data a času.<br /><br /> Další informace: ["Vypnuto" vlastní formát specifikátor](#ffSpecifier).|2009-06-15T13:45:30.6170000 -&GT; 61<br /><br /> 2009-06-15T13:45:30.0050000 -&GT; 00|  
|"fff"|Milisekundy v hodnotě data a času.<br /><br /> Další informace: ["Fff" vlastní formát specifikátor](#fffSpecifier).|6/15/2009 13:45:30.617 -> 617<br /><br /> 6/15/2009 13:45:30.0005 -> 000|  
|"ffff"|Desetitisíciny sekundy v hodnotě data a času.<br /><br /> Další informace: [ffff. vlastní formát specifikátor](#ffffSpecifier).|2009-06-15T13:45:30.6175000 -&GT; 6175<br /><br /> 2009-06-0000-15T13:45:30.0000500 &GT;|  
|"fffff"|Stotisíciny sekundy v hodnotě data a času.<br /><br /> Další informace: ["Fffff" vlastní formát specifikátor](#fffffSpecifier).|2009-06-15T13:45:30.6175400 -&GT; 61754<br /><br /> 6/15/2009 13:45:30.000005 -> 00000|  
|"ffffff"|Miliontiny sekundy v hodnotě data a času.<br /><br /> Další informace: [vlastní specifikátor formátu "ffffff"](#ffffffSpecifier).|2009-06-15T13:45:30.6175420 -&GT; 617542<br /><br /> 2009-06-15T13:45:30.0000005 -&GT; 000000|  
|"fffffff"|Desetimiliontiny sekundy v hodnotě data a času.<br /><br /> Další informace: ["Fffffff" vlastní formát specifikátor](#fffffffSpecifier).|2009-06-15T13:45:30.6175425 -&GT; 6175425<br /><br /> 2009-06-15T13:45:30.0001150 -&GT; 0001150|  
|"F"|Pokud je hodnota nenulová, jedná se o desetiny sekundy v hodnotě data a času.<br /><br /> Další informace: [The "F" vlastní formát specifikátor](#F_Specifier).|2009-06-15T13:45:30.6170000 -&GT; 6<br /><br /> 2009-06-15T13:45:30.0500000 -> (žádný výstup)|  
|"FF"|Pokud je hodnota nenulová, jedná se o setiny sekundy v hodnotě data a času.<br /><br /> Další informace: ["Vypnuto" vlastní formát specifikátor](#FF_Specifier).|2009-06-15T13:45:30.6170000 -&GT; 61<br /><br /> 2009-06-15T13:45:30.0050000 -> (žádný výstup)|  
|"FFF"|Pokud je hodnota nenulová, jedná se o milisekundy v hodnotě data a času.<br /><br /> Další informace: [vlastní specifikátor formátu "FFF"](#FFF_Specifier).|2009-06-15T13:45:30.6170000 -&GT; 617<br /><br /> 2009-06-15T13:45:30.0005000 -> (žádný výstup)|  
|"FFFF"|Pokud je hodnota nenulová, jedná se o desetitisíciny sekundy v hodnotě data a času.<br /><br /> Další informace: [specifikátor formátu "FFFF" vlastní](#FFFF_Specifier).|2009-06-15T13:45:30.5275000 -&GT; 5275<br /><br /> 2009-06-15T13:45:30.0000500 -> (žádný výstup)|  
|"FFFFF"|Pokud je hodnota nenulová, jedná se o stotisíciny sekundy v hodnotě data a času.<br /><br /> Další informace: [vlastní specifikátor formátu "FFFFF"](#FFFFF_Specifier).|2009-06-15T13:45:30.6175400 -&GT; 61754<br /><br /> 2009-06-15T13:45:30.0000050 -> (žádný výstup)|  
|"FFFFFF"|Pokud je hodnota nenulová, jedná se o miliontiny sekundy v hodnotě data a času.<br /><br /> Další informace: [vlastní specifikátor formátu "FFFFFF"](#FFFFFF_Specifier).|2009-06-15T13:45:30.6175420 -&GT; 617542<br /><br /> 2009-06-15T13:45:30.0000005 -> (žádný výstup)|  
|"FFFFFFF"|Pokud je hodnota nenulová, jedná se o desetimiliontiny sekundy v hodnotě data a času.<br /><br /> Další informace: [vlastní specifikátor formátu "FFFFFFF"](#FFFFFFF_Specifier).|2009-06-15T13:45:30.6175425 -&GT; 6175425<br /><br /> 2009-06-15T13:45:30.0001150 -&GT; 000115|  
|"g", "gg"|Období nebo éra.<br /><br /> Další informace: ["g" nebo "gg" vlastní formát specifikátor](#gSpecifier).|2009-06-15T13:45:30.6170000 -> A.D.|  
|"h"|Hodiny ve 12hodinovém formátu, od 1 do 12.<br /><br /> Další informace: ["H" vlastní formát specifikátor](#hSpecifier).|2009-06-15T01:45:30 -> 1<br /><br /> 2009-06-15T13:45:30 -> 1|  
|"hh"|Hodiny ve 12hodinovém formátu, od 01 do 12.<br /><br /> Další informace: [vlastní specifikátor formátu "hh"](#hhSpecifier).|2009-06-15T01:45:30 -> 01<br /><br /> 2009-06-15T13:45:30 -> 01|  
|"H"|Hodiny ve 24hodinovém formátu, od 0 do 23.<br /><br /> Další informace: [The "H" vlastní formát specifikátor](#H_Specifier).|2009-06-15T01:45:30 -> 1<br /><br /> 2009-06-15T13:45:30 -> 13|  
|"HH"|Hodiny ve 24hodinovém formátu, od 00 do 23.<br /><br /> Další informace: [vlastní specifikátor formátu "HH"](#HH_Specifier).|2009-06-15T01:45:30 -> 01<br /><br /> 2009-06-15T13:45:30 -> 13|  
|"K"|Informace o časovém pásmu.<br /><br /> Další informace: ["K" vlastní formát specifikátor](#KSpecifier).|S <xref:System.DateTime> hodnoty:<br /><br /> 2009-06--> typ neurčené 15T13:45:30,<br /><br /> 2009-06-15T13:45:30, druh Utc -> Z<br /><br /> 2009-06-15T13:45:30, druh Local->-07:00 (závisí na nastavení místního počítače)<br /><br /> S <xref:System.DateTimeOffset> hodnoty:<br /><br /> 2009-06-15T01:45:30-07:00 --> -07:00<br /><br /> 2009-06-15T08:45:30+00:00 --> +00:00|  
|"m"|Minuty, od 0 do 59.<br /><br /> Další informace: ["M" vlastní formát specifikátor](#mSpecifier).|2009-06-15T01:09:30 -&GT; 9<br /><br /> 2009-06-15T13:29:30 -> 29|  
|"mm"|Minuty, od 00 do 59.<br /><br /> Další informace: ["Mm" vlastní formát specifikátor](#mmSpecifier).|2009-06-15T01:09:30 -> 09<br /><br /> 2009-06-15T01:45:30 -> 45|  
|"M"|Měsíc, od 1 do 12.<br /><br /> Další informace: [vlastní specifikátor formátu "M"](#M_Specifier).|2009-06-15T13:45:30 -> 6|  
|"MM"|Měsíc, od 01 do 12.<br /><br /> Další informace: ["MM" vlastní formát specifikátor](#MM_Specifier).|2009-06-15T13:45:30 -> 06|  
|"MMM"|Zkrácený název měsíce.<br /><br /> Další informace: [vlastní specifikátor formátu "MMMM"](#MMM_Specifier).|2009-06-15T13:45:30 -> června (en US)<br /><br /> 2009-06-15T13:45:30 -> juin (fr-FR)<br /><br /> 2009-06-15T13:45:30 -> června (zu-ZA)|  
|"MMMM"|Úplný název měsíce.<br /><br /> Další informace: [vlastní specifikátor formátu "MMMM"](#MMMM_Specifier).|2009-06-15T13:45:30 -> června (en US)<br /><br /> 2009-06-15T13:45:30 -> juni (da-DK)<br /><br /> 2009-06-15T13:45:30 -> uJuni (zu-ZA)|  
|"s"|Sekundy, od 0 do 59.<br /><br /> Další informace: ["S" vlastní formát specifikátor](#sSpecifier).|2009-06-15T13:45:09 -> 9|  
|"ss"|Sekundy, od 00 do 59.<br /><br /> Další informace: ["Ss" vlastní formát specifikátor](#ssSpecifier).|2009-06-15T13:45:09 -> 09|  
|"t"|První znak označení pro dopoledne/odpoledne.<br /><br /> Další informace: ["T" vlastní formát specifikátor](#tSpecifier).|2009-06-15T13:45:30 -> P (en US)<br /><br /> 2009-06-15T13:45:30 -> 午 (ja-JP)<br /><br /> 2009-06-15T13:45:30 -> (fr-FR)|  
|"tt"|Označení pro dopoledne/odpoledne.<br /><br /> Další informace: [vlastní specifikátor formátu "tt"](#ttSpecifier).|2009-06-15T13:45:30 -> PM (en US)<br /><br /> 2009-06-15T13:45:30 -> 午後 (ja-JP)<br /><br /> 2009-06-15T13:45:30 -> (fr-FR)|  
|"y"|Rok, od 0 do 99.<br /><br /> Další informace: ["Y" vlastní formát specifikátor](#ySpecifier).|0001-01-01T00:00:00 -> 1<br /><br /> 0900-01-01T00:00:00 -> 0<br /><br /> 1900-01-01T00:00:00 -> 0<br /><br /> 2009-06-15T13:45:30 -> 9<br /><br /> 2019-06-15T13:45:30 -> 19|  
|"yy"|Rok, od 00 do 99.<br /><br /> Další informace: ["Rr" vlastní formát specifikátor](#yySpecifier).|0001-01-01T00:00:00 -> 01<br /><br /> 0900-01-01T00:00:00 -> 00<br /><br /> 1900-01-01T00:00:00 -> 00<br /><br /> 2019-06-15T13:45:30 -> 19|  
|"yyy"|Rok s nejméně třemi číslicemi.<br /><br /> Další informace: [vlastní specifikátor formátu "yyy"](#yyySpecifier).|0001-01-01T00:00:00 -> 001<br /><br /> 0900-01-01T00:00:00 -> 900<br /><br /> 1900-01-01T00:00:00 -> 1900<br /><br /> 2009-06-15T13:45:30 -&GT; 2009|  
|"yyyy"|Rok jako čtyřmístné číslo.<br /><br /> Další informace: ["Rrrr" vlastní formát specifikátor](#yyyySpecifier).|0001-01-01T00:00:00 -> 0001<br /><br /> 0900-01-01T00:00:00 -> 0900<br /><br /> 1900-01-01T00:00:00 -> 1900<br /><br /> 2009-06-15T13:45:30 -&GT; 2009|  
|"yyyyy"|Rok jako pětimístné číslo.<br /><br /> Další informace: [vlastní specifikátor formátu "yyyyy"](#yyyyySpecifier).|0001-01-01T00:00:00 -> 00001<br /><br /> 2009-06-15T13:45:30 -> 02009|  
|"z"|Posun hodin od času UTC, bez počátečních nul.<br /><br /> Další informace: ["Z" vlastní formát specifikátor](#zSpecifier).|2009-06-15T13:45:30-07:00 -> -7|  
|"zz"|Posun hodin od času UTC, s počáteční nulou pro jednocifernou hodnotu.<br /><br /> Další informace: [vlastní specifikátor formátu "zz"](#zzSpecifier).|2009-06-15T13:45:30-07:00 -> -07|  
|"zzz"|Posun v hodinách a minutách od času UTC.<br /><br /> Další informace: [vlastní specifikátor formátu "zzz"](#zzzSpecifier).|2009-06-15T13:45:30-07:00 -> -07:00|  
|":"|Oddělovač času.<br /><br /> Další informace: [":" vlastní formát specifikátor](#timeSeparator).|2009-06-15T13:45:30 ->: (en US)<br /><br /> 2009-06-15T13:45:30 -> . (it-IT)<br /><br /> 2009-06-15T13:45:30 -> : (ja-JP)|  
|"/"|Oddělovač data.<br /><br /> Další informace: [vlastní formát specifikátor "/"](#dateSeparator).|2009-06-15T13:45:30 -> / (en US)<br /><br /> 2009-06-15T13:45:30 -> - (ar-DZ)<br /><br /> 2009-06-15T13:45:30 -> . (tr-TR)|  
|"*řetězec*"<br /><br /> '*řetězec*.|Oddělovač řetězcového literálu.<br /><br /> Další informace: [znak literály](#Literals).|2009-06-15T13:45:30 ("směrování žádostí na aplikace:" h:m t) -> směrování žádostí na aplikace: 1:45 P<br /><br /> 2009-06-15T13:45:30 (' směrování žádostí na aplikace:' h:m t) -> směrování žádostí na aplikace: 1:45 P|  
|%|Definuje následující znak jako specifikátor vlastního formátu.<br /><br /> Další informace:[pomocí jednoho specifikátory formátu vlastní](#UsingSingleSpecifiers).|2009-06-15T13:45:30 (%h) -> 1|  
|\|Řídicí znak.<br /><br /> Další informace: [znak literály](#Literals) a [pomocí řídicí znak](#escape).|2009-06-15T13:45:30 (h \h) -> 1 hod|  
|Jakýkoli jiný znak|Znak je zkopírován do výsledného řetězce beze změny.<br /><br /> Další informace: [znak literály](#Literals).|2009-06-15T01:45:30 (hh: mm t směrování žádostí na aplikace) -> směrování žádostí na aplikace dop.|  
  
 Následující oddíly poskytují další informace o jednotlivých specifikátorech vlastního formátu data a času. Pokud není uvedeno jinak, každý specifikátor vytváří identické řetězcové vyjádření bez ohledu na to, zda je použit s <xref:System.DateTime> hodnotu nebo <xref:System.DateTimeOffset> hodnotu.  
  
<a name="dSpecifier"></a>   
## <a name="the-d-custom-format-specifier"></a>Specifikátor vlastní formát "d"  
 Specifikátor vlastního formátu "d" představuje den v měsíci jako číslo od 1 do 31. Jednociferné číslo dne je formátováno bez počáteční nuly.  
  
 Pokud specifikátor formátu "d" použijete bez dalších specifikátorů vlastního formátu, je interpretován jako specifikátor standardního formátu data a času "d". Další informace o používání jeden specifikátor formátu najdete v tématu [pomocí jednoho specifikátory formátu vlastní](#UsingSingleSpecifiers) dál v tomto tématu.  
  
 Následující příklad obsahuje specifikátor vlastního formátu "d" v několika řetězcích formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#1)]
 [!code-vb[Formatting.DateAndTime.Custom#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#1)]  
  
 [Zpět k tabulce](#table)  
  
<a name="ddSpecifier"></a>   
## <a name="the-dd-custom-format-specifier"></a>Specifikátor vlastní formát "dd"  
 Řetězec vlastního formátu "dd" představuje den v měsíci jako číslo od 01 do 31. Jednociferné číslo dne je formátováno s počáteční nulou.  
  
 Následující příklad obsahuje specifikátor vlastního formátu "dd" v řetězci vlastního formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#2)]
 [!code-vb[Formatting.DateAndTime.Custom#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#2)]  
  
 [Zpět k tabulce](#table)  
  
<a name="dddSpecifier"></a>   
## <a name="the-ddd-custom-format-specifier"></a>Specifikátor vlastní formát "ddd"  
 Specifikátor vlastního formátu "ddd" představuje zkrácený název dne v týdnu. Lokalizovaný zkrácený název dne v týdnu je načten z <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A?displayProperty=nameWithType> vlastnost zadané nebo aktuální jazykové verze.  
  
 Následující příklad obsahuje specifikátor vlastního formátu "ddd" v řetězci vlastního formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#3)]
 [!code-vb[Formatting.DateAndTime.Custom#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#3)]  
  
 [Zpět k tabulce](#table)  
  
<a name="ddddSpecifier"></a>   
## <a name="the-dddd-custom-format-specifier"></a>Specifikátor vlastní formát "dddd"  
 Specifikátor vlastního formátu "dddd" (a libovolný počet dalších specifikátorů "d") představuje úplný název dne v týdnu. Lokalizovaný název dne v týdnu je načten z <xref:System.Globalization.DateTimeFormatInfo.DayNames%2A?displayProperty=nameWithType> vlastnost zadané nebo aktuální jazykové verze.  
  
 Následující příklad obsahuje specifikátor vlastního formátu "dddd" v řetězci vlastního formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#4)]
 [!code-vb[Formatting.DateAndTime.Custom#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#4)]  
  
 [Zpět k tabulce](#table)  
  
<a name="fSpecifier"></a>   
## <a name="the-f-custom-format-specifier"></a>Specifikátor vlastní formát "f"  
 Specifikátor vlastního formátu "f" představuje nejvýznamnější číslici zlomku sekund. Představuje tedy desetiny sekundy v hodnotě data a času.  
  
 Pokud specifikátor formátu "f" použijete bez dalšího specifikátoru vlastního formátu, je interpretován jako specifikátor standardního formátu data a času "f". Další informace o používání jeden specifikátor formátu najdete v tématu [pomocí jednoho specifikátory formátu vlastní](#UsingSingleSpecifiers) dál v tomto tématu.  
  
 Při použití specifikátorů formátu "f" jako součást řetězce formátu dodaná do <xref:System.DateTime.ParseExact%2A>, <xref:System.DateTime.TryParseExact%2A>, <xref:System.DateTimeOffset.ParseExact%2A>, nebo <xref:System.DateTimeOffset.TryParseExact%2A> metoda, počet specifikátorů formátu "f" Určuje počet platných číslic zlomků sekund musí být úspěšně analyzovat řetězec.  
  
 Následující příklad obsahuje specifikátor vlastního formátu "f" v řetězci vlastního formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]  
  
 [Zpět k tabulce](#table)  
  
<a name="ffSpecifier"></a>   
## <a name="the-ff-custom-format-specifier"></a>Specifikátor vlastní formát "vypnuto"  
 Specifikátor vlastního formátu "ff" představuje dvě nejvýznamnější číslice zlomku sekund. Představuje tedy setiny sekundy v hodnotě data a času.  
  
 Následující příklad obsahuje specifikátor vlastního formátu "ff" v řetězci vlastního formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]  
  
 [Zpět k tabulce](#table)  
  
<a name="fffSpecifier"></a>   
## <a name="the-fff-custom-format-specifier"></a>Specifikátor vlastní formát "fff"  
 Specifikátor vlastního formátu "fff" představuje tři nejvýznamnější číslice zlomku sekund. Představuje tedy milisekundy v hodnotě data a času.  
  
 Následující příklad obsahuje specifikátor vlastního formátu "fff" v řetězci vlastního formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]  
  
 [Zpět k tabulce](#table)  
  
<a name="ffffSpecifier"></a>   
## <a name="the-ffff-custom-format-specifier"></a>Specifikátor formátu ffff. vlastní  
 Specifikátor vlastního formátu "ffff" představuje čtyři nejvýznamnější číslice zlomku sekund. Představuje tedy desetitisíciny sekundy v hodnotě data a času.  
  
 Ačkoli je možné zobrazit komponentu desetitisícin sekundy časové hodnoty, tato hodnota nemusí být smysluplná. Přesnost hodnot data a času závisí na rozlišení systémových hodin. V systémech Windows NT verze 3.5 (a vyšší) a Windows Vista je rozlišení hodin přibližně 10–15 milisekund.  
  
 [Zpět k tabulce](#table)  
  
<a name="fffffSpecifier"></a>   
## <a name="the-fffff-custom-format-specifier"></a>Vlastní formátu "fffff"  
 Specifikátor vlastního formátu "fffff" představuje pět nejvýznamnějších číslic zlomku sekund. Představuje tedy stotisíciny sekundy v hodnotě data a času.  
  
 Ačkoli je možné zobrazit komponentu stotisícin sekundy časové hodnoty, tato hodnota nemusí být smysluplná. Přesnost hodnot data a času závisí na rozlišení systémových hodin. V systémech Windows NT verze 3.5 (a vyšší) a Windows Vista je rozlišení hodin přibližně 10–15 milisekund.  
  
 [Zpět k tabulce](#table)  
  
<a name="ffffffSpecifier"></a>   
## <a name="the-ffffff-custom-format-specifier"></a>Vlastní formátu "ffffff"  
 Specifikátor vlastního formátu "ffffff" představuje šest nejvýznamnějších číslic zlomku sekund. Představuje tedy miliontiny sekundy v hodnotě data a času.  
  
 Ačkoli je možné zobrazit komponentu miliontin sekundy časové hodnoty, tato hodnota nemusí být smysluplná. Přesnost hodnot data a času závisí na rozlišení systémových hodin. V systémech Windows NT verze 3.5 (a vyšší) a Windows Vista je rozlišení hodin přibližně 10–15 milisekund.  
  
 [Zpět k tabulce](#table)  
  
<a name="fffffffSpecifier"></a>   
## <a name="the-fffffff-custom-format-specifier"></a>Vlastní formátu "FFFFFFF"  
 Specifikátor vlastního formátu "fffffff" představuje sedm nejvýznamnějších číslic zlomku sekund. Představuje tedy desetimiliontiny sekundy v hodnotě data a času.  
  
 Ačkoli je možné zobrazit komponentu desetimiliontin sekundy časové hodnoty, tato hodnota nemusí být smysluplná. Přesnost hodnot data a času závisí na rozlišení systémových hodin. V systémech Windows NT verze 3.5 (a vyšší) a Windows Vista je rozlišení hodin přibližně 10–15 milisekund.  
  
 [Zpět k tabulce](#table)  
  
<a name="F_Specifier"></a>   
## <a name="the-f-custom-format-specifier"></a>Specifikátor vlastní formát "F"  
 Specifikátor vlastního formátu "F" představuje nejvýznamnější číslici zlomku sekund. Představuje tedy desetiny sekundy v hodnotě data a času. Pokud je číslice nula, nezobrazí se žádná hodnota.  
  
 Pokud specifikátor formátu "F" použijete bez dalšího specifikátoru vlastního formátu, je interpretován jako specifikátor standardního formátu data a času "F". Další informace o používání jeden specifikátor formátu najdete v tématu [pomocí jednoho specifikátory formátu vlastní](#UsingSingleSpecifiers) dál v tomto tématu.  
  
 Počet specifikátorů formátu "F" použít s <xref:System.DateTime.ParseExact%2A>, <xref:System.DateTime.TryParseExact%2A>, <xref:System.DateTimeOffset.ParseExact%2A>, nebo <xref:System.DateTimeOffset.TryParseExact%2A> metoda určuje maximální počet platných číslic zlomků sekund, které můžou být úspěšně analyzovat řetězec.  
  
 Následující příklad obsahuje specifikátor vlastního formátu "F" v řetězci vlastního formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]  
  
 [Zpět k tabulce](#table)  
  
<a name="FF_Specifier"></a>   
## <a name="the-ff-custom-format-specifier"></a>Specifikátor vlastní formát "Vypnuto"  
 Specifikátor vlastního formátu "FF" představuje dvě nejvýznamnější číslice zlomku sekund. Představuje tedy setiny sekundy v hodnotě data a času. Koncové nuly nebo čísla složená ze dvou nul však nejsou zobrazeny.  
  
 Následující příklad obsahuje specifikátor vlastního formátu "FF" v řetězci vlastního formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]  
  
 [Zpět k tabulce](#table)  
  
<a name="FFF_Specifier"></a>   
## <a name="the-fff-custom-format-specifier"></a>Specifikátor vlastní formát "FFF"  
 Specifikátor vlastního formátu "FFF" představuje tři nejvýznamnější číslice zlomku sekund. Představuje tedy milisekundy v hodnotě data a času. Koncové nuly nebo čísla složená ze tří nul však nejsou zobrazeny.  
  
 Následující příklad obsahuje specifikátor vlastního formátu "FFF" v řetězci vlastního formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]  
  
 [Zpět k tabulce](#table)  
  
<a name="FFFF_Specifier"></a>   
## <a name="the-ffff-custom-format-specifier"></a>Specifikátor vlastní formát "FFFF"  
 Specifikátor vlastního formátu "FFFF" představuje čtyři nejvýznamnější číslice zlomku sekund. Představuje tedy desetitisíciny sekundy v hodnotě data a času. Koncové nuly nebo čísla složená ze čtyř nul však nejsou zobrazeny.  
  
 Ačkoli je možné zobrazit komponentu desetitisícin sekundy časové hodnoty, tato hodnota nemusí být smysluplná. Přesnost hodnot data a času závisí na rozlišení systémových hodin. V systémech Windows NT verze 3.5 (a vyšší) a Windows Vista je rozlišení hodin přibližně 10–15 milisekund.  
  
 [Zpět k tabulce](#table)  
  
<a name="FFFFF_Specifier"></a>   
## <a name="the-fffff-custom-format-specifier"></a>Vlastní formátu "fffff"  
 Specifikátor vlastního formátu "FFFFF" představuje pět nejvýznamnějších číslic zlomku sekund. Představuje tedy stotisíciny sekundy v hodnotě data a času. Koncové nuly nebo čísla složená z pěti nul však nejsou zobrazeny.  
  
 Ačkoli je možné zobrazit komponentu stotisícin sekundy časové hodnoty, tato hodnota nemusí být smysluplná. Přesnost hodnot data a času závisí na rozlišení systémových hodin. V systémech Windows NT verze 3.5 (a vyšší) a Windows Vista je rozlišení hodin přibližně 10–15 milisekund.  
  
 [Zpět k tabulce](#table)  
  
<a name="FFFFFF_Specifier"></a>   
## <a name="the-ffffff-custom-format-specifier"></a>Vlastní formátu "ffffff"  
 Specifikátor vlastního formátu "FFFFFF" představuje šest nejvýznamnějších číslic zlomku sekund. Představuje tedy miliontiny sekundy v hodnotě data a času. Koncové nuly nebo čísla složená ze šesti nul však nejsou zobrazeny.  
  
 Ačkoli je možné zobrazit komponentu miliontin sekundy časové hodnoty, tato hodnota nemusí být smysluplná. Přesnost hodnot data a času závisí na rozlišení systémových hodin. V systémech Windows NT verze 3.5 (a vyšší) a Windows Vista je rozlišení hodin přibližně 10–15 milisekund.  
  
 [Zpět k tabulce](#table)  
  
<a name="FFFFFFF_Specifier"></a>   
## <a name="the-fffffff-custom-format-specifier"></a>Vlastní formátu "FFFFFFF"  
 Specifikátor vlastního formátu "FFFFFFF" představuje sedm nejvýznamnějších číslic zlomku sekund. Představuje tedy desetimiliontiny sekundy v hodnotě data a času. Koncové nuly nebo čísla složená ze sedmi nul však nejsou zobrazeny.  
  
 Ačkoli je možné zobrazit komponentu desetimiliontin sekundy časové hodnoty, tato hodnota nemusí být smysluplná. Přesnost hodnot data a času závisí na rozlišení systémových hodin. V systémech Windows NT verze 3.5 (a vyšší) a Windows Vista je rozlišení hodin přibližně 10–15 milisekund.  
  
 [Zpět k tabulce](#table)  
  
<a name="gSpecifier"></a>   
## <a name="the-g-or-gg-custom-format-specifier"></a>Specifikátor vlastní formát "g" nebo "gg"  
 Specifikátor vlastního formátu "g" nebo "gg" (plus libovolný počet dalších specifikátorů "g") představuje období nebo éru, jako je například n. l. Operace formátování tento specifikátor ignorují, pokud k datu, které má být formátováno, nebyl přidružen řetězec období nebo éry.  
  
 Pokud specifikátor formátu "g" použijete bez dalšího specifikátoru vlastního formátu, je interpretován jako specifikátor standardního formátu data a času "g". Další informace o používání jeden specifikátor formátu najdete v tématu [pomocí jednoho specifikátory formátu vlastní](#UsingSingleSpecifiers) dál v tomto tématu.  
  
 Následující příklad obsahuje specifikátor vlastního formátu "g" v řetězci vlastního formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#6)]
 [!code-vb[Formatting.DateAndTime.Custom#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#6)]  
  
 [Zpět k tabulce](#table)  
  
<a name="hSpecifier"></a>   
## <a name="the-h-custom-format-specifier"></a>Specifikátor vlastní formát "h"  
 Specifikátor vlastního formátu "h" představuje hodiny jako číslo od 1 do 12. Hodiny jsou tedy reprezentovány ve 12hodinovém formátu, který počítá celé hodiny od půlnoci nebo od poledne. Konkrétní hodina po půlnoci je nerozeznatelná od stejné hodiny po poledni. Hodiny nejsou zaokrouhleny a jednociferné číslo hodiny je formátováno bez počáteční nuly. Například pro čas 5:43 dopoledne nebo odpoledne tento specifikátor vlastního formátu zobrazí hodnotu "5".  
  
 Pokud specifikátor "h" formát je použit bez dalších specifikátory vlastní formát, je interpretován jako standardní hodnoty data a času a vyvolá <xref:System.FormatException>. Další informace o používání jeden specifikátor formátu najdete v tématu [pomocí jednoho specifikátory formátu vlastní](#UsingSingleSpecifiers) dál v tomto tématu.  
  
 Následující příklad obsahuje specifikátor vlastního formátu "h" v řetězci vlastního formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
 [!code-vb[Formatting.DateAndTime.Custom#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]  
  
 [Zpět k tabulce](#table)  
  
<a name="hhSpecifier"></a>   
## <a name="the-hh-custom-format-specifier"></a>Specifikátor vlastní formátu "hh"  
 Specifikátor vlastního formátu "hh" (plus libovolný počet dalších specifikátorů "h") představuje hodiny jako čísla od 01 do 12. Představuje tedy hodiny ve 12hodinovém formátu, který počítá celé hodiny od půlnoci nebo od poledne. Konkrétní hodina po půlnoci je nerozeznatelná od stejné hodiny po poledni. Hodiny nejsou zaokrouhleny a jednociferné číslo hodiny je formátováno s počáteční nulou. Například pro čas 5:43 dopoledne nebo odpoledne tento specifikátor formátu zobrazí hodnotu "05".  
  
 Následující příklad obsahuje specifikátor vlastního formátu "hh" v řetězci vlastního formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
 [!code-vb[Formatting.DateAndTime.Custom#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]  
  
 [Zpět k tabulce](#table)  
  
<a name="H_Specifier"></a>   
## <a name="the-h-custom-format-specifier"></a>Specifikátor vlastní formát "H"  
 Specifikátor vlastního formátu "H" představuje hodiny jako číslo od 0 do 23. Představuje tedy hodiny ve 24hodinovém formátu počítaném od nuly, který počítá celé hodiny od půlnoci. Jednociferné číslo hodiny je formátováno bez počáteční nuly.  
  
 Pokud specifikátor formátu "H" je použit bez dalších specifikátory vlastní formát, je interpretován jako standardní hodnoty data a času a vyvolá <xref:System.FormatException>. Další informace o používání jeden specifikátor formátu najdete v tématu [pomocí jednoho specifikátory formátu vlastní](#UsingSingleSpecifiers) dál v tomto tématu.  
  
 Následující příklad obsahuje specifikátor vlastního formátu "H" v řetězci vlastního formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#9)]
 [!code-vb[Formatting.DateAndTime.Custom#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#9)]  
  
 [Zpět k tabulce](#table)  
  
<a name="HH_Specifier"></a>   
## <a name="the-hh-custom-format-specifier"></a>Specifikátor vlastní formátu "HH"  
 Specifikátor vlastního formátu "HH" (plus libovolný počet dalších specifikátorů "H") představuje hodiny jako čísla od 00 do 23. Představuje tedy hodiny ve 24hodinovém formátu počítaném od nuly, který počítá celé hodiny od půlnoci. Jednociferné číslo hodiny je formátováno s počáteční nulou.  
  
 Následující příklad obsahuje specifikátor vlastního formátu "HH" v řetězci vlastního formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#10)]
 [!code-vb[Formatting.DateAndTime.Custom#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#10)]  
  
 [Zpět k tabulce](#table)  
  
<a name="KSpecifier"></a>   
## <a name="the-k-custom-format-specifier"></a>Specifikátor vlastní formát "K"  
 Specifikátor vlastního formátu "K" představuje informace o časovém pásmu hodnoty data a času. Pokud se používá tento specifikátor formátu s <xref:System.DateTime> hodnoty, výsledný řetězec je definován hodnotou <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> vlastnost:  
  
-   Pro místní časové pásmo ( <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> hodnota vlastnosti <xref:System.DateTimeKind.Local?displayProperty=nameWithType>), tato specifikace je ekvivalentní specifikátor "zzz" a vytváří výsledný řetězec obsahující místní posun od koordinovaného světového času (UTC); například "-07:00".  
  
-   Pro čas UTC ( <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> hodnota vlastnosti <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>), výsledný řetězec obsahuje znak "Z" představující datum UTC.  
  
-   Po dobu z neurčené časové pásmo (čas jejichž <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> vlastnost rovná <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>), výsledkem je ekvivalentní <xref:System.String.Empty?displayProperty=nameWithType>.  
  
 Pro <xref:System.DateTimeOffset> hodnoty, specifikátor formátu "K" je ekvivalentní specifikátor formátu "zzz" a vytváří výsledný řetězec obsahující <xref:System.DateTimeOffset> posun od času UTC.  
  
 Pokud specifikátor formátu "K" je použit bez dalších specifikátory vlastní formát, je interpretován jako standardní hodnoty data a času a vyvolá výjimku <xref:System.FormatException>. Další informace o používání jeden specifikátor formátu najdete v tématu [pomocí jednoho specifikátory formátu vlastní](#UsingSingleSpecifiers) dál v tomto tématu.  
  
 Následující příklad zobrazí řetězec, který je výsledkem použití vlastní formát specifikátor "K" s různými <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnoty v systému v USA Tichomořském časovém pásmu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#12)]
 [!code-vb[Formatting.DateAndTime.Custom#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#12)]  
  
 [Zpět k tabulce](#table)  
  
<a name="mSpecifier"></a>   
## <a name="the-m-custom-format-specifier"></a>Specifikátor vlastní formát "m"  
 Specifikátor vlastního formátu "m" představuje minuty jako čísla od 0 do 59. Minuta představuje celé minuty, které uplynuly od poslední hodiny. Jednociferné číslo minuty je formátováno bez počáteční nuly.  
  
 Pokud specifikátor formátu "m" použijete bez dalšího specifikátoru vlastního formátu, je interpretován jako specifikátor standardního formátu data a času "m". Další informace o používání jeden specifikátor formátu najdete v tématu [pomocí jednoho specifikátory formátu vlastní](#UsingSingleSpecifiers) dál v tomto tématu.  
  
 Následující příklad obsahuje specifikátor vlastního formátu "m" v řetězci vlastního formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
 [!code-vb[Formatting.DateAndTime.Custom#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]  
  
 [Zpět k tabulce](#table)  
  
<a name="mmSpecifier"></a>   
## <a name="the-mm-custom-format-specifier"></a>"Mm" vlastní formátovací řetězec  
 Specifikátor vlastního formátu "mm" (plus libovolný počet dalších specifikátorů "m") představuje minuty jako čísla od 00 do 59. Minuta představuje celé minuty, které uplynuly od poslední hodiny. Jednociferné číslo minut je formátováno s počáteční nulou.  
  
 Následující příklad obsahuje specifikátor vlastního formátu "mm" v řetězci vlastního formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
 [!code-vb[Formatting.DateAndTime.Custom#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]  
  
 [Zpět k tabulce](#table)  
  
<a name="M_Specifier"></a>   
## <a name="the-m-custom-format-specifier"></a>Specifikátor vlastní formát "M"  
 Specifikátor vlastního formátu "M" představuje měsíc jako číslo od 1 do 12 (nebo od 1 do 13 pro kalendáře, které mají 13 měsíců). Jednociferné číslo měsíce je formátováno bez počáteční nuly.  
  
 Pokud specifikátor formátu "M" použijete bez dalšího specifikátoru vlastního formátu, je interpretován jako specifikátor standardního formátu data a času "M". Další informace o používání jeden specifikátor formátu najdete v tématu [pomocí jednoho specifikátory formátu vlastní](#UsingSingleSpecifiers) dál v tomto tématu.  
  
 Následující příklad obsahuje specifikátor vlastního formátu "M" v řetězci vlastního formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#11)]
 [!code-vb[Formatting.DateAndTime.Custom#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#11)]  
  
 [Zpět k tabulce](#table)  
  
<a name="MM_Specifier"></a>   
## <a name="the-mm-custom-format-specifier"></a>Specifikátor vlastní formát "MM"  
 Specifikátor vlastního formátu "MM" představuje měsíc jako číslo od 01 do 12 (nebo od 1 do 13 pro kalendáře, které mají 13 měsíců). Jednociferné číslo měsíce je formátováno s počáteční nulou.  
  
 Následující příklad obsahuje specifikátor vlastního formátu "MM" v řetězci vlastního formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#2)]
 [!code-vb[Formatting.DateAndTime.Custom#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#2)]  
  
 [Zpět k tabulce](#table)  
  
<a name="MMM_Specifier"></a>   
## <a name="the-mmm-custom-format-specifier"></a>Specifikátor vlastní formát "MMMM"  
 Specifikátor vlastního formátu "MMM" představuje zkrácený název měsíce. Lokalizovaný zkrácený název v měsíci je načten z <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames%2A?displayProperty=nameWithType> vlastnost zadané nebo aktuální jazykové verze.  
  
 Následující příklad obsahuje specifikátor vlastního formátu "MMM" v řetězci vlastního formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#3)]
 [!code-vb[Formatting.DateAndTime.Custom#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#3)]  
  
 [Zpět k tabulce](#table)  
  
<a name="MMMM_Specifier"></a>   
## <a name="the-mmmm-custom-format-specifier"></a>Specifikátor vlastní formát "MMMM"  
 Specifikátor vlastního formátu "MMMM" představuje úplný název měsíce. Lokalizovaný název měsíce se načítají <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A?displayProperty=nameWithType> vlastnost zadané nebo aktuální jazykové verze.  
  
 Následující příklad obsahuje specifikátor vlastního formátu "MMMM" v řetězci vlastního formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#4)]
 [!code-vb[Formatting.DateAndTime.Custom#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#4)]  
  
 [Zpět k tabulce](#table)  
  
<a name="sSpecifier"></a>   
## <a name="the-s-custom-format-specifier"></a>Specifikátor vlastní formát "s"  
 Specifikátor vlastního formátu "s" představuje sekundy jako čísla od 0 do 59. Výsledek představuje celé sekundy, které uplynuly od poslední minuty. Jednociferné číslo sekundy je formátováno bez počáteční nuly.  
  
 Pokud specifikátor formátu "s" použijete bez dalšího specifikátoru vlastního formátu, je interpretován jako specifikátor standardního formátu data a času "s". Další informace o používání jeden specifikátor formátu najdete v tématu [pomocí jednoho specifikátory formátu vlastní](#UsingSingleSpecifiers) dál v tomto tématu.  
  
 Následující příklad obsahuje specifikátor vlastního formátu "s" v řetězci vlastního formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
 [!code-vb[Formatting.DateAndTime.Custom#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]  
  
 [Zpět k tabulce](#table)  
  
<a name="ssSpecifier"></a>   
## <a name="the-ss-custom-format-specifier"></a>Specifikátor vlastní formát "ss"  
 Specifikátor vlastního formátu "ss" (plus libovolný počet dalších specifikátorů "s") představuje sekundy jako čísla od 00 do 59. Výsledek představuje celé sekundy, které uplynuly od poslední minuty. Jednociferné číslo sekundy je formátováno s počáteční nulou.  
  
 Následující příklad obsahuje specifikátor vlastního formátu "ss" v řetězci vlastního formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
 [!code-vb[Formatting.DateAndTime.Custom#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]  
  
 [Zpět k tabulce](#table)  
  
<a name="tSpecifier"></a>   
## <a name="the-t-custom-format-specifier"></a>Specifikátor vlastní formát "t"  
 Specifikátor vlastního formátu "t" představuje první znak označení dopoledne/odpoledne. Odpovídající lokalizovaný označení se načítají z <xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A?displayProperty=nameWithType> nebo <xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A?displayProperty=nameWithType> vlastnosti aktuální nebo konkrétní jazykové verze. Označení dopoledne (AM) se používá pro všechny hodnoty času od 0:00:00 (půlnoc) do 11:59:59.999. Označení odpoledne (PM) se používá pro všechny hodnoty času od 12:00:00 (poledne) do 23:59:59.999.  
  
 Pokud specifikátor formátu "t" použijete bez dalšího specifikátoru vlastního formátu, je interpretován jako specifikátor standardního formátu data a času "t". Další informace o používání jeden specifikátor formátu najdete v tématu [pomocí jednoho specifikátory formátu vlastní](#UsingSingleSpecifiers) dál v tomto tématu.  
  
 Následující příklad obsahuje specifikátor vlastního formátu "t" v řetězci vlastního formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
 [!code-vb[Formatting.DateAndTime.Custom#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]  
  
 [Zpět k tabulce](#table)  
  
<a name="ttSpecifier"></a>   
## <a name="the-tt-custom-format-specifier"></a>Specifikátor vlastní formát "tt"  
 Specifikátor vlastního formátu "tt" (plus libovolný počet dalších specifikátorů "t") představuje celé označení dopoledne/odpoledne. Odpovídající lokalizovaný označení se načítají z <xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A?displayProperty=nameWithType> nebo <xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A?displayProperty=nameWithType> vlastnosti aktuální nebo konkrétní jazykové verze. Označení dopoledne (AM) se používá pro všechny hodnoty času od 0:00:00 (půlnoc) do 11:59:59.999. Označení odpoledne (PM) se používá pro všechny hodnoty času od 12:00:00 (poledne) do 23:59:59.999.  
  
 Ujistěte se, že používáte specifikátor "tt" pro jazyky, pro které je nezbytné zachovat rozdíl mezi dopolednem a odpolednem. Pro ukázku je uvedena japonština, pro kterou se liší určení dopoledne a odpoledne (AM a PM) v druhém znaku namísto prvního znaku.  
  
 Následující příklad obsahuje specifikátor vlastního formátu "tt" v řetězci vlastního formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
 [!code-vb[Formatting.DateAndTime.Custom#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]  
  
 [Zpět k tabulce](#table)  
  
<a name="ySpecifier"></a>   
## <a name="the-y-custom-format-specifier"></a>Specifikátor vlastní formát "y"  
 Specifikátor vlastního formátu "y" představuje rok jako jednociferné nebo dvouciferné číslo. Pokud rok obsahuje více než dvě číslice, zobrazí se ve výsledku pouze dvě číslice nižšího řádu. Pokud první číslice dvoumístného čísla roku začíná nulou (například 2008), je číslo formátováno bez počáteční nuly.  
  
 Pokud specifikátor formátu "y" použijete bez dalšího specifikátoru vlastního formátu, je interpretován jako specifikátor standardního formátu data a času "y". Další informace o používání jeden specifikátor formátu najdete v tématu [pomocí jednoho specifikátory formátu vlastní](#UsingSingleSpecifiers) dál v tomto tématu.  
  
 Následující příklad obsahuje specifikátor vlastního formátu "y" v řetězci vlastního formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Custom#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]  
  
 [Zpět k tabulce](#table)  
  
<a name="yySpecifier"></a>   
## <a name="the-yy-custom-format-specifier"></a>Specifikátor vlastní formát "rr"  
 Specifikátor vlastního formátu "yy" představuje rok jako dvouciferné číslo. Pokud rok obsahuje více než dvě číslice, zobrazí se ve výsledku pouze dvě číslice nižšího řádu. Pokud má dvoumístný rok méně než dvě platné číslice, je číslo doplněno počátečními nulami za účelem vytvoření dvouciferného čísla.  
  
 V operaci analýzy, se interpretují podle letopočty roku, který je analyzovat pomocí specifikátor vlastní formát "rr" <xref:System.Globalization.Calendar.TwoDigitYearMax%2A?displayProperty=nameWithType> vlastnost aktuální kalendáře zprostředkovatele formátu. Následující příklad analyzuje řetězcovou reprezentaci data s rokem vyjádřeným dvěma číslicemi pomocí výchozího gregoriánského kalendáře jazykové verze en_US, což v tomto případě představuje aktuální jazykovou verzi. Poté změní aktuální jazykovou verzi <xref:System.Globalization.CultureInfo> objekt, který chcete použít <xref:System.Globalization.GregorianCalendar> objekt, jehož <xref:System.Globalization.GregorianCalendar.TwoDigitYearMax%2A> vlastnost byla změněna.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#19](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/parseexact2digityear1.cs#19)]
 [!code-vb[Formatting.DateAndTime.Custom#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/parseexact2digityear1.vb#19)]  
  
 Následující příklad obsahuje specifikátor vlastního formátu "yy" v řetězci vlastního formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Custom#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]  
  
 [Zpět k tabulce](#table)  
  
<a name="yyySpecifier"></a>   
## <a name="the-yyy-custom-format-specifier"></a>Specifikátor vlastní formát "yyy"  
 Specifikátor vlastního formátu "yyy" představuje rok nejméně se třemi číslicemi. Pokud rok obsahuje více než tři platné číslice, budou obsaženy ve výsledném řetězci. Pokud má rok méně než tři číslice, je číslo doplněno počátečními nulami tak, aby bylo vytvořeno trojciferné číslo.  
  
> [!NOTE]
>  Pro thajský buddhistický kalendář, který může mít pět číslic roku, zobrazí tento specifikátor formátu všechny platné číslice.  
  
 Následující příklad obsahuje specifikátor vlastního formátu "yyy" v řetězci vlastního formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Custom#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]  
  
 [Zpět k tabulce](#table)  
  
<a name="yyyySpecifier"></a>   
## <a name="the-yyyy-custom-format-specifier"></a>Specifikátor vlastní formát "rrrr"  
 Specifikátor vlastního formátu "yyyy" představuje rok nejméně se čtyřmi číslicemi. Pokud rok obsahuje více než čtyři platné číslice, budou obsaženy ve výsledném řetězci. Pokud má rok méně než čtyři číslice, je číslo doplněno počátečními nulami tak, aby bylo vytvořeno čtyřciferné číslo.  
  
> [!NOTE]
>  Pro thajský buddhistický kalendář, který může mít pět číslic roku, zobrazí tento specifikátor formátu minimálně čtyři číslice.  
  
 Následující příklad obsahuje specifikátor vlastního formátu "yyyy" v řetězci vlastního formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Custom#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]  
  
 [Zpět k tabulce](#table)  
  
<a name="yyyyySpecifier"></a>   
## <a name="the-yyyyy-custom-format-specifier"></a>Specifikátor vlastní formát "yyyyy"  
 Specifikátor vlastního formátu "yyyyy" (plus libovolný počet dalších specifikátorů "y") představuje rok nejméně s pěti číslicemi. Pokud rok obsahuje více než pět platných číslic, budou obsaženy ve výsledném řetězci. Pokud má rok méně než pět číslic, je číslo doplněno počátečními nulami tak, aby bylo vytvořeno pěticiferné číslo.  
  
 Pokud existují další specifikátory "y", je číslo doplněno tolika počátečními nulami, kolik je třeba pro vytvoření čísla podle specifikátorů "y".  
  
 Následující příklad obsahuje specifikátor vlastního formátu "yyyyy" v řetězci vlastního formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Custom#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]  
  
 [Zpět k tabulce](#table)  
  
<a name="zSpecifier"></a>   
## <a name="the-z-custom-format-specifier"></a>Specifikátor vlastní formát "z"  
 S <xref:System.DateTime> hodnoty, specifikátor vlastní formát "z" představuje posun časového pásma místního operačního systému z koordinovaný světový čas (UTC), měřená v hodinách. Nezohledňuje hodnotu instance <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> vlastnost. Z tohoto důvodu se nedoporučuje specifikátor formátu "z" pro použití s <xref:System.DateTime> hodnoty.  
  
 S <xref:System.DateTimeOffset> představuje tento specifikátor formátu hodnoty, <xref:System.DateTimeOffset> posun od času UTC v hodinách.  
  
 Posun je vždy zobrazen s počátečním znaménkem. Znaménko plus (+) označuje hodiny před časem UTC a symbol mínus (-) označuje hodiny za časem UTC. Jednociferné číslo posunu je formátováno bez počáteční nuly.  
  
 Pokud specifikátor formátu "z" je použit bez dalších specifikátory vlastní formát, je interpretován jako standardní hodnoty data a času a vyvolá <xref:System.FormatException>. Další informace o používání jeden specifikátor formátu najdete v tématu [pomocí jednoho specifikátory formátu vlastní](#UsingSingleSpecifiers) dál v tomto tématu.  
  
 Následující příklad obsahuje specifikátor vlastního formátu "z" v řetězci vlastního formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
 [!code-vb[Formatting.DateAndTime.Custom#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]  
  
 [Zpět k tabulce](#table)  
  
<a name="zzSpecifier"></a>   
## <a name="the-zz-custom-format-specifier"></a>Specifikátor vlastní formát "zz"  
 S <xref:System.DateTime> hodnoty, vlastní formát specifikátor "zz" představuje posun časového pásma místního operačního systému od času UTC, měřený v hodinách. Nezohledňuje hodnotu instance <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> vlastnost. Z tohoto důvodu se nedoporučuje specifikátor formátu "zz" pro použití s <xref:System.DateTime> hodnoty.  
  
 S <xref:System.DateTimeOffset> představuje tento specifikátor formátu hodnoty, <xref:System.DateTimeOffset> posun od času UTC v hodinách.  
  
 Posun je vždy zobrazen s počátečním znaménkem. Znaménko plus (+) označuje hodiny před časem UTC a symbol mínus (-) označuje hodiny za časem UTC. Jednociferné číslo posunu je formátováno s počáteční nulou.  
  
 Následující příklad obsahuje specifikátor vlastního formátu "zz" v řetězci vlastního formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
 [!code-vb[Formatting.DateAndTime.Custom#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]  
  
 [Zpět k tabulce](#table)  
  
<a name="zzzSpecifier"></a>   
## <a name="the-zzz-custom-format-specifier"></a>Specifikátor vlastní formát "zzz"  
 S <xref:System.DateTime> hodnoty, specifikátor vlastní formát "zzz" představuje posun časového pásma místního operačního systému od času UTC, měřená v hodinách a minutách. Nezohledňuje hodnotu instance <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> vlastnost. Z tohoto důvodu se nedoporučuje specifikátor formátu "zzz" pro použití s <xref:System.DateTime> hodnoty.  
  
 S <xref:System.DateTimeOffset> představuje tento specifikátor formátu hodnoty, <xref:System.DateTimeOffset> posun od času UTC v hodinách a minutách.  
  
 Posun je vždy zobrazen s počátečním znaménkem. Znaménko plus (+) označuje hodiny před časem UTC a symbol mínus (-) označuje hodiny za časem UTC. Jednociferné číslo posunu je formátováno s počáteční nulou.  
  
 Následující příklad obsahuje specifikátor vlastního formátu "zzz" ve vlastním řetězci formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
 [!code-vb[Formatting.DateAndTime.Custom#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]  
  
 [Zpět k tabulce](#table)  
  
<a name="timeSeparator"></a>   
## <a name="the--custom-format-specifier"></a>":" Vlastní specifikátor formátu.  
 Specifikátor vlastního formátu ":" představuje oddělovač času, který se používá k rozlišení hodin, minut a sekund. Odpovídající lokalizovaný oddělovač je načten z <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A?displayProperty=nameWithType> vlastnost zadané nebo aktuální jazykové verze.  
  
> [!NOTE]
>  Chcete-li změnit oddělovač času pro konkrétní datum a čas řetězec, zadejte znak oddělovače v rámci oddělovač řetězcového literálu. Například vlastní řetězec formátu `hh'_'dd'_'ss` vytváří výsledný řetězec, ve kterém "\_" (podtržítko) se vždy používá jako oddělovač času. Chcete-li změnit oddělovač času pro všechna data pro jazykovou verzi, změňte hodnotu <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A?displayProperty=nameWithType> vlastnost aktuální jazykovou verzi, nebo vytvořit instanci <xref:System.Globalization.DateTimeFormatInfo> objektu, přiřaďte znak, který má jeho <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A> vlastnost a Volejte přetížení formátování metoda, která zahrnuje <xref:System.IFormatProvider> parametr.  
  
 Pokud ":" specifikátor formátu je použit bez dalších specifikátory vlastní formát, je interpretován jako standardní hodnoty data a času a vyvolá <xref:System.FormatException>. Další informace o používání jeden specifikátor formátu najdete v tématu [pomocí jednoho specifikátory formátu vlastní](#UsingSingleSpecifiers) dál v tomto tématu.  
  
 [Zpět k tabulce](#table)  
  
<a name="dateSeparator"></a>   
## <a name="the--custom-format-specifier"></a>Specifikátor vlastní formát "/"  
 Specifikátor vlastního formátu "/" představuje oddělovač dat, který se používá k rozlišení roků, měsíců a dnů. Odpovídající lokalizovaný oddělovač data získává z <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A?displayProperty=nameWithType> vlastnost zadané nebo aktuální jazykové verze.  
  
> [!NOTE]
>  Chcete-li změnit oddělovač data pro konkrétní datum a čas řetězec, zadejte znak oddělovače v rámci oddělovač řetězcového literálu. Například vlastní řetězec formátu `mm'/'dd'/'yyyy` vytváří výsledný řetězec, ve kterém "/" se vždy používá jako oddělovač data. Chcete-li změnit oddělovač data pro všechna data pro jazykovou verzi, změňte hodnotu <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A?displayProperty=nameWithType> vlastnost aktuální jazykovou verzi, nebo vytvořit instanci <xref:System.Globalization.DateTimeFormatInfo> objektu, přiřaďte znak, který má jeho <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A> vlastnost a Volejte přetížení formátování metoda, která zahrnuje <xref:System.IFormatProvider> parametr.  
  
 Pokud specifikátor formátu "/" se používá bez dalších specifikátory vlastní formát, je interpretován jako standardní hodnoty data a času a vyvolá výjimku <xref:System.FormatException>. Další informace o používání jeden specifikátor formátu najdete v tématu [pomocí jednoho specifikátory formátu vlastní](#UsingSingleSpecifiers) dál v tomto tématu.  
  
 [Zpět k tabulce](#table)  
  
<a name="Literals"></a>   
## <a name="character-literals"></a>Znakové literály  
 Následující znaky v vlastní datum a čas řetězec formátu jsou vyhrazeny a nejsou vždy interpretovat jako formátovací znaky nebo u ",", /, a \\, jako speciální znaky.  
  
||||||  
|-|-|-|-|-|  
|F|H|K|M|d|  
|f|G|h|m|s|  
|t|y|Z|%|:|  
|/|"|'|\||  
  
 Všechny ostatní znaky jsou vždy interpretuje jako znakové literály a v operaci formátování, které jsou zahrnuté ve výsledném řetězci beze změny.  V operaci analýzy musí se shodovat s znaky ve vstupním řetězci přesně; porovnání rozlišuje velká a malá písmena.  
  
 Následující příklad obsahuje literály "PST" (pro Tichomořský běžný čas) a "PDT" (pro tichomořského letního času) představují místní časové pásmo v řetězci formátu. Všimněte si, že řetězec je zahrnutá ve výsledném řetězci a že řetězec, který obsahuje řetězec místního časového pásma také analyzuje úspěšně.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#20](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx1.cs#20)]
 [!code-vb[Formatting.DateAndTime.Custom#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx1.vb#20)]  
  
 Existují dva způsoby, které určují, že znaky se budou interpretovat jako literály a ne jako vyhrazené znaky, abyste mohli být součástí výsledný řetězec nebo úspěšně analyzovat ve vstupním řetězci:  
  
-   Podle uvozovací znaky jednotlivé vyhrazené znaky. Další informace najdete v tématu [pomocí řídicí znak](#escape).  
  
     Následující příklad obsahuje literály "pst" (pro Tichomořský běžný čas) představují místní časové pásmo v řetězci formátu. Protože "s" a "t" vlastní řetězce formátu, je nutné uvést oba znaky budou interpretovat jako znakové literály.  
  
     [!code-csharp[Formatting.DateAndTime.Custom#21](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx2.cs#21)]
     [!code-vb[Formatting.DateAndTime.Custom#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx2.vb#21)]  
  
-   Uzavřené v uvozovkách nebo apostrofy celý řetězcového literálu. Následující příklad je stejný, jako je předchozí s tím rozdílem, že "pst" je uzavřena v uvozovkách indikující, že by měl celý řetězec oddělený interpretovat jako znakové literály.  
  
     [!code-csharp[Formatting.DateAndTime.Custom#22](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx3.cs#22)]
     [!code-vb[Formatting.DateAndTime.Custom#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx3.vb#22)]  
  
<a name="Notes"></a>   
## <a name="notes"></a>Poznámky  
  
<a name="UsingSingleSpecifiers"></a>   
### <a name="using-single-custom-format-specifiers"></a>Použití specifikátorů formátu jeden vlastní  
 Řetězec vlastního formátu data a času se skládá ze dvou nebo několika znaků. Metody formátování data a času interpretují jakýkoli řetězec s jediným znakem jako řetězec standardního formátu data a času. Pokud jako platný formát specifikátor nerozpoznají znak, vyvolají <xref:System.FormatException>. Například řetězec formátu, který se skládá pouze ze specifikátoru "h", je interpretován jako řetězec standardního formátu data a času. V tomto případě, je však výjimka vyvolána, protože neexistuje žádná "h" standardní specifikátor data a timeformat.  
  
 Chcete-li použít kterýkoli ze specifikátorů vlastního formátu data a času jako jediný specifikátor v řetězci formátu (to znamená, že chcete použít samotné specifikátory formátu "d", "f", "F", "g", "h", "H", "K", "m", "M", "s", "t", "y", "z", ":" nebo "/"), vložte před nebo za specifikátor mezeru, nebo vložte před jednoduchý specifikátor vlastního formátu specifikátor formátu procento %.  
  
 Například "`%h"` interpretována jako vlastní data a času řetězec formátu, který zobrazí hodinu reprezentována aktuální hodnota data a času. Můžete také použít řetězec formátu " h" nebo "h ", ačkoli tato hodnota vloží ve výsledném řetězci vedle hodin mezeru. Následující příklad znázorňuje tyto tři řetězce formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#16](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/literal1.cs#16)]
 [!code-vb[Formatting.DateAndTime.Custom#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/literal1.vb#16)]  
  
<a name="escape"></a>   
### <a name="using-the-escape-character"></a>Použití řídicích znaků  
 Znaky "d", "f", "F", "g", "h", "H", "K", "m", "M", "s", "t", "y", "z", ":", nebo "/" v řetězci formátu jsou interpretovány jako specifikátory vlastního formátu, nikoli jako literální znaky. Abyste zabránili interpretaci jako specifikátor formátu znak, můžete jí předchází zpětné lomítko (\\), což je řídicí znak. Řídicí znak označuje, že následující znak je literální znak, který by měl být zařazen do výsledného řetězce beze změny.  
  
 Zahrnout výsledek řetězec zpětné lomítko, musí vyhnuli ho další zpětné lomítko (`\\`).  
  
> [!NOTE]
>  Některé kompilátory, jako jsou například kompilátory jazyka C++ a jazyka C#, mohou také interpretovat jedno zpětné lomítko jako řídicí znak. Abyste se ujistili, zda je řetězec interpretován při formátování správně, můžete v jazyce C# použít literální řetězcový znak verbatim (znak @) před řetězcem, nebo v jazyce C# a C++ přidat další znak zpětného lomítka před každé zpětné lomítko. Následující příklad jazyka C# ukazuje oba přístupy.  
  
 Následující příklad používá řídicí znak, aby zamezil operacím formátování v interpretaci znaků "h" a "m" jako specifikátorů formátu.  
  
 [!code-csharp[Formatting.DateAndTime.Custom#15](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/escape1.cs#15)]
 [!code-vb[Formatting.DateAndTime.Custom#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/escape1.vb#15)]  
  
### <a name="control-panel-settings"></a>Nastavení ovládacího panelu  
 **Místní a jazykové nastavení** nastavení v Ovládacích panelech ovlivní výsledný řetězec formátování operací, která zahrnuje celou řadu vlastní datum a čas specifikátory formátu. Tato nastavení slouží k inicializaci <xref:System.Globalization.DateTimeFormatInfo> objekt přidružený k aktuální jazykovou verzi vlákna, které poskytuje hodnoty použité k řízení formátování. Počítače, které používají různá nastavení, generují různé výsledné řetězce.  
  
 Kromě toho, pokud použijete <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> konstruktor k vytvoření instance nového <xref:System.Globalization.CultureInfo> objekt, který reprezentuje stejnou jazykovou verzi jako aktuální systémovou kulturu jakékoli vlastní nastavení **místní a jazykové nastavení** na ovládacím panelu se použijí k novému <xref:System.Globalization.CultureInfo> objektu. Můžete použít <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> konstruktor k vytvoření <xref:System.Globalization.CultureInfo> objekt, který vlastní nastavení systému.  
  
### <a name="datetimeformatinfo-properties"></a>Vlastnosti DateTimeFormatInfo  
 Formátování je ovlivněno vlastnosti aktuální <xref:System.Globalization.DateTimeFormatInfo> objekt, který je poskytnut implicitně aktuální jazykovou verzi vlákna nebo explicitně pomocí <xref:System.IFormatProvider> parametru metody, která vyvolá formátování. Pro <xref:System.IFormatProvider> musíte zadat parametr, <xref:System.Globalization.CultureInfo> objekt, který představuje jazykovou verzi, nebo <xref:System.Globalization.DateTimeFormatInfo> objektu.  
  
 Výsledný řetězec vytvořený při spoustu času specifikátorů vlastní data a také závisí na vlastnosti aktuální <xref:System.Globalization.DateTimeFormatInfo> objektu. Aplikace můžete změnit výsledku vytvořeného některé vlastní datum a čas specifikátory formátu změnou odpovídající <xref:System.Globalization.DateTimeFormatInfo> vlastnost. Například specifikátor formátu "ddd" přidá zkrácený název dne v nalezen <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A> pole řetězce pro výsledný řetězec. Podobně specifikátor formátu "MMMM" Přidá název měsíce v nalezen <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A> pole řetězce pro výsledný řetězec.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.DateTime?displayProperty=nameWithType>  
 <xref:System.IFormatProvider?displayProperty=nameWithType>  
 [Typy formátování](../../../docs/standard/base-types/formatting-types.md)  
 [Standardní řetězce formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)  
 [Ukázka: Rozhraní .NET Framework 4 formátování nástroj](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
