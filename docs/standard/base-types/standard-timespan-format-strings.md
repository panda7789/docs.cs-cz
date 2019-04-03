---
title: Standardní řetězce formátu TimeSpan
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- format specifiers, standard time interval
- format strings
- standard time interval format strings
- standard format strings, time intervals
- format specifiers, time intervals
- time intervals [.NET Framework], formatting
- time [.NET Framework], formatting
- formatting [.NET Framework], time
- standard TimeSpan format strings
- formatting [.NET Framework], time intervals
ms.assetid: 9f6c95eb-63ae-4dcc-9c32-f81985c75794
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1bf7424c8aa2ae816340f6fa641e5c79a56ae0dc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834124"
---
# <a name="standard-timespan-format-strings"></a>Standardní řetězce formátu TimeSpan
<a name="Top"></a> Standardní <xref:System.TimeSpan> formátovací řetězec se používá jeden specifikátor formátu definovat textové vyjádření <xref:System.TimeSpan> hodnotu, která je výsledkem operace formátování. Formátovací řetězec, který obsahuje více než jeden znak, včetně prázdných znaků, je interpretován jako vlastní <xref:System.TimeSpan> řetězec formátu. Další informace najdete v tématu [Custom TimeSpan Format Strings](../../../docs/standard/base-types/custom-timespan-format-strings.md) .  
  
 Řetězcové vyjádření <xref:System.TimeSpan> hodnoty jsou vytvářeny voláním přetížení <xref:System.TimeSpan.ToString%2A?displayProperty=nameWithType> metody, stejně jako metody, které podporují také složené formátování, jako například <xref:System.String.Format%2A?displayProperty=nameWithType>. Další informace najdete v tématu [Formatting Types](../../../docs/standard/base-types/formatting-types.md) a [složené formátování](../../../docs/standard/base-types/composite-formatting.md). Následující příklad ukazuje použití standardního formátovacího řetězce v operacích formátování.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/formatexample1.cs#2)]
 [!code-vb[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/formatexample1.vb#2)]  
  
 Standardní <xref:System.TimeSpan> formátovací řetězce jsou také používány <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> a <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody, které definují požadovaný formát ze vstupních řetězců pro operace analýzy. (Analýza kódu převede řetězcové vyjádření hodnoty této hodnotě.) Následující příklad ukazuje použití standardního formátovacího řetězce v operacích analýzy.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/parseexample1.cs#3)]
 [!code-vb[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/parseexample1.vb#3)]  
  
<a name="top"></a> Následující tabulka uvádí specifikátory formátu interval (běžný čas).  
  
|Specifikátor formátu|Název|Popis|Příklady|  
|----------------------|----------|-----------------|--------------|  
|"c"|Konstantní (neutrální) formát|Tento specifikátor není zohledňující jazykovou verzi. Má podobu `[-][d'.']hh':'mm':'ss['.'fffffff]`.<br /><br /> (Řetězce formátu "T" a "t" vytvářejí stejné výsledky.)<br /><br /> Další informace: [Specifikátor konstanty ("c") formátu](#Constant).|`TimeSpan.Zero` -> 00:00:00<br /><br /> `New TimeSpan(0, 0, 30, 0)` -> 00:30:00<br /><br /> `New TimeSpan(3, 17, 25, 30, 500)` -> 3.17:25:30.5000000|  
|"g"|Obecném krátkém formátu|Tento specifikátor výstupem jenom to, co je potřeba. Jazykové a má podobu `[-][d':']h':'mm':'ss[.FFFFFFF]`.<br /><br /> Další informace: [Specifikátor formátu Obecný krátký ("g")](#GeneralShort).|`New TimeSpan(1, 3, 16, 50, 500)` -> 1:3:16:50.5 (en US)<br /><br /> `New TimeSpan(1, 3, 16, 50, 500)` -> 1:3:16:50,5 (fr-FR)<br /><br /> `New TimeSpan(1, 3, 16, 50, 599)` -> 1:3:16:50.599 (en US)<br /><br /> `New TimeSpan(1, 3, 16, 50, 599)` -> 1:3:16:50,599 (fr-FR)|  
|"G"|Obecném dlouhém formátu|Tento specifikátor vždy vypíše dnů a sedm zlomkové číslice. Jazykové a má podobu `[-]d':'hh':'mm':'ss.fffffff`.<br /><br /> Další informace: [Specifikátor formátu Obecný dlouhý ("G")](#GeneralLong).|`New TimeSpan(18, 30, 0)` -> 0:18:30:00.0000000 (en US)<br /><br /> `New TimeSpan(18, 30, 0)` -> 0:18:30:00,0000000 (fr-FR)|  
  
<a name="Constant"></a>   
## <a name="the-constant-c-format-specifier"></a>Specifikátor konstanty formátu ("c")  
 Vrátí řetězcovou reprezentaci specifikátor formátu "c" <xref:System.TimeSpan> hodnotu v následujícím tvaru:  
  
 [-] [*d*.] *hh*:*mm*:*ss*[. *fffffff*]  
  
 Prvky v hranatých závorkách ([a]) jsou volitelné. Tečka (.) a dvojtečka (:) jsou symboly literálu. Následující tabulka popisuje zbývající prvky.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|*-*|Volitelným záporným znaménkem, který označuje záporný časový interval.|  
|*d*|Volitelné počet dní, bez počátečních nul.|  
|*hh*|Počet hodin, které od "00" do "23".|  
|*mm*|Počet minut, který se pohybuje od "00" do "59".|  
|*ss*|Počet sekund, který se pohybuje od "0" do "59".|  
|*fffffff*|Volitelné necelá část hodnoty sekundy.  Jeho hodnota může být v rozsahu od "0000001" (jedna značka nebo jedné sekundy millionth deset) do "9999999" (9 999 999 Desetimiliontiny sekundy nebo druhý menší jedna značka).|  
  
 Na rozdíl od specifikátory formátu "G" a "g" specifikátor formátu "c" není zohledňující jazykovou verzi. Vytváří řetězcovou reprezentaci <xref:System.TimeSpan> hodnotu, která je neutrální a která je společná pro všechny předchozí verze rozhraní .NET Framework před [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Výchozí hodnota je "c" <xref:System.TimeSpan> formátovací řetězec; <xref:System.TimeSpan.ToString?displayProperty=nameWithType> metoda formátuje hodnotu časového intervalu pomocí formátovacího řetězce "c".  
  
> [!NOTE]
>  <xref:System.TimeSpan> podporuje také "t" a "T" standardní formátovací řetězce, které jsou stejné chování jako řetězec standardního formátu "c".  
  
 Následující příklad vytvoří dvě <xref:System.TimeSpan> objekty, používá k provedení aritmetické operace a zobrazí výsledek. V obou případech používá složeného formátování pro zobrazení <xref:System.TimeSpan> hodnotu ho jde pomocí specifikátoru formátu "c".  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardc1.cs#1)]
 [!code-vb[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardc1.vb#1)]  
  
 [Zpět k tabulce](#Top)  
  
<a name="GeneralShort"></a>   
## <a name="the-general-short-g-format-specifier"></a>Specifikátor formátu Obecný krátký ("g")  
 "g" <xref:System.TimeSpan> specifikátor formátu vrátí řetězcovou reprezentaci <xref:System.TimeSpan> hodnotu v kompaktním formátu zahrnutím pouze prvky, které jsou nezbytné. Má následující tvar:  
  
 [-][*d*:]*h*:*mm*:*ss*[.*FFFFFFF*]  
  
 Prvky v hranatých závorkách ([a]) jsou volitelné. Dvojtečka (:) je literál symbol. Následující tabulka popisuje zbývající prvky.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|*-*|Volitelným záporným znaménkem, který označuje záporný časový interval.|  
|*d*|Volitelné počet dní, bez počátečních nul.|  
|*h*|Počet hodin, který se pohybuje od "0" až "23", bez počátečních nul.|  
|*mm*|Počet minut, který se pohybuje od "00" do "59"...|  
|*ss*|Počet sekund, který se pohybuje od "00" do "59"...|  
|*.*|Oddělovač zlomků sekund. Je ekvivalentní se zadanou jazykovou verzi <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> přepíše vlastnost bez uživatele.|  
|*FFFFFFF*|Zlomků sekund. Počet číslic nejdříve jsou zobrazeny.|  
  
 Například specifikátor formátu "G" je specifikátor formátu "g" lokalizována. Jeho desetinné části sekund oddělovač je založen na aktuální jazykovou verzi nebo zadané jazykové verze <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> vlastnost.  
  
 Následující příklad vytvoří dvě <xref:System.TimeSpan> objekty, používá k provedení aritmetické operace a zobrazí výsledek. V obou případech používá složeného formátování pro zobrazení <xref:System.TimeSpan> hodnotu ho jde pomocí specifikátoru formátu "g". Kromě toho formáty <xref:System.TimeSpan> hodnotu pomocí formátovacích úmluv aktuální systémovou kulturu (která je v tomto případě Angličtina - Spojené státy nebo en US) a Francouzština – Francie (fr-FR) jazykovou verzi.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardshort1.cs#4)]
 [!code-vb[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardshort1.vb#4)]  
  
 [Zpět k tabulce](#Top)  
  
<a name="GeneralLong"></a>   
## <a name="the-general-long-g-format-specifier"></a>Specifikátor formátu Obecný dlouhý ("G")  
 "G" <xref:System.TimeSpan> specifikátor formátu vrátí řetězcovou reprezentaci <xref:System.TimeSpan> hodnotu v dlouhém formátu, který obsahuje vždy dnů a zlomků sekund. Řetězec, který je výsledkem specifikátor standardního formátu "G" má následující formát:  
  
 [-] *d*:*hh*:*mm*:*ss*. *fffffff*  
  
 Prvky v hranatých závorkách ([a]) jsou volitelné. Dvojtečka (:) je literál symbol. Následující tabulka popisuje zbývající prvky.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|*-*|Volitelným záporným znaménkem, který označuje záporný časový interval.|  
|*d*|Počet dní, bez počátečních nul.|  
|*hh*|Počet hodin, které od "00" do "23".|  
|*mm*|Počet minut, který se pohybuje od "00" do "59".|  
|*ss*|Počet sekund, který se pohybuje od "00" do "59".|  
|*.*|Oddělovač zlomků sekund. Je ekvivalentní se zadanou jazykovou verzi <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> přepíše vlastnost bez uživatele.|  
|*fffffff*|Zlomků sekund.|  
  
 Například specifikátor formátu "G" je specifikátor formátu "g" lokalizována. Jeho desetinné části sekund oddělovač je založen na aktuální jazykovou verzi nebo zadané jazykové verze <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> vlastnost.  
  
 Následující příklad vytvoří dvě <xref:System.TimeSpan> objekty, používá k provedení aritmetické operace a zobrazí výsledek. V obou případech používá složeného formátování pro zobrazení <xref:System.TimeSpan> hodnotu ho jde pomocí specifikátoru formátu "G". Kromě toho formáty <xref:System.TimeSpan> hodnotu pomocí formátovacích úmluv aktuální systémovou kulturu (která je v tomto případě Angličtina - Spojené státy nebo en US) a Francouzština – Francie (fr-FR) jazykovou verzi.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardlong1.cs#5)]
 [!code-vb[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardlong1.vb#5)]  
  
 [Zpět k tabulce](#Top)  
  
## <a name="see-also"></a>Viz také:

- [Typy formátování](../../../docs/standard/base-types/formatting-types.md)
- [Vlastní řetězce formátu TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)
- [Analýza řetězců](../../../docs/standard/base-types/parsing-strings.md)
