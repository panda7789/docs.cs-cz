---
title: "Standardní řetězce formátu TimeSpan"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c4c486728ee4f98a6718c4d019976fccd6f380d7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="standard-timespan-format-strings"></a>Standardní řetězce formátu TimeSpan
<a name="Top"></a>Standardní <xref:System.TimeSpan> řetězec formátu používá jeden specifikátor formátu pro definování textovou reprezentaci hodnoty <xref:System.TimeSpan> hodnotu, která je výsledkem operace formátování. Formátovací řetězec, který obsahuje více než jeden znak, včetně mezer, interpretována jako vlastní <xref:System.TimeSpan> řetězec formátu. Další informace najdete v tématu [vlastní řetězce formátu TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md) .  
  
 Řetězcové vyjádření <xref:System.TimeSpan> hodnoty jsou vytvářeny voláním přetížení <xref:System.TimeSpan.ToString%2A?displayProperty=nameWithType> metoda, stejně jako metodami, které podporují složené formátování, jako například <xref:System.String.Format%2A?displayProperty=nameWithType>. Další informace najdete v tématu [typy formátování](../../../docs/standard/base-types/formatting-types.md) a [složené formátování](../../../docs/standard/base-types/composite-formatting.md). Následující příklad ukazuje použití standardní řetězce formátu v operacích formátování.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/formatexample1.cs#2)]
 [!code-vb[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/formatexample1.vb#2)]  
  
 Standardní <xref:System.TimeSpan> řetězce formátu jsou také používány <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> a <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> metody k definování požadovaný formát vstupu řetězců pro operace analýzy. (Analýza převede řetězcovou reprezentaci hodnoty na tuto hodnotu.) Následující příklad ukazuje použití standardní řetězce formátu v operacích analýzy.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/parseexample1.cs#3)]
 [!code-vb[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/parseexample1.vb#3)]  
  
<a name="top"></a>Následující tabulka uvádí specifikátory formátu intervalu (běžný čas).  
  
|Specifikátor formátu|Název|Popis|Příklady|  
|----------------------|----------|-----------------|--------------|  
|"c"|Konstantní (neutrální) formátu|Tento specifikátor není zohledňující jazykovou verzi. Používá formát `[-][d’.’]hh’:’mm’:’ss[‘.’fffffff]`.<br /><br /> ("T" a "T" řetězce formátu poskytovat stejné výsledky.)<br /><br /> Další informace: [The konstantní ("c") specifikátor formátu](#Constant).|`TimeSpan.Zero` -> 00:00:00<br /><br /> `New TimeSpan(0, 0, 30, 0)` -> 00:30:00<br /><br /> `New TimeSpan(3, 17, 25, 30, 500)` -> 3.17:25:30.5000000|  
|"g"|Obecné krátké formátu|Tento specifikátor výstupy pouze to, co je potřeba. Je zohledňující jazykovou verzi a má podobu `[-][d’:’]h’:’mm’:’ss[.FFFFFFF]`.<br /><br /> Další informace: [obecné krátké ("g") specifikátor formátu](#GeneralShort).|`New TimeSpan(1, 3, 16, 50, 500)`-> 1:3:16:50.5 (en US)<br /><br /> `New TimeSpan(1, 3, 16, 50, 500)`-> 1:3:16:50, 5 (fr-FR)<br /><br /> `New TimeSpan(1, 3, 16, 50, 599)`-> 1:3:16:50.599 (en US)<br /><br /> `New TimeSpan(1, 3, 16, 50, 599)`-> 1:3:16:50 599 (fr-FR)|  
|"G"|Obecný dlouhý formát|Tento specifikátor vždy výstupy dny a sedm míst za desetinnou čárkou. Je zohledňující jazykovou verzi a má podobu `[-]d’:’hh’:’mm’:’ss.fffffff`.<br /><br /> Další informace: [obecné dlouho ("G") specifikátor formátu](#GeneralLong).|`New TimeSpan(18, 30, 0)`-> 0:18:30:00.0000000 (en US)<br /><br /> `New TimeSpan(18, 30, 0)`-> 0:18:30:00 0000000 (fr-FR)|  
  
<a name="Constant"></a>   
## <a name="the-constant-c-format-specifier"></a>Specifikátor formátu konstantní ("c")  
 Vrátí řetězcovou reprezentaci specifikátor "c" formátu <xref:System.TimeSpan> hodnotu v následující podobě:  
  
 [-] [*d*.] *hh*:*mm*:*ss*[. *fffffff*]  
  
 Prvky v hranatých závorek ([a]) jsou volitelné. Tečka (.) a dvojtečka (:) jsou symboly literálu. Následující tabulka popisuje zbývající prvky.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|*-*|Volitelné záporné znaménko, který označuje záporné časovém intervalu.|  
|*d*|Volitelné počet dní, bez počátečních nul.|  
|*hh*|Počet hodin, který se pohybuje od "00" do "23".|  
|*mm*|Počet minut, který se pohybuje od "00" do "59".|  
|*ss*|Počet sekund, který se pohybuje od "0" do "59".|  
|*fffffff*|Volitelné část sekundy.  Jeho hodnota může být v rozsahu od "0000001" (jedna značka nebo jeden millionth deset sekund) do "9999999 tak" (9 999 999 Desetimiliontiny sekundy, nebo druhý menší jeden značek).|  
  
 Na rozdíl od specifikátorů formátu "G" a "g" specifikátor "c" Formát není zohledňující jazykovou verzi. Vyvolá řetězcovou reprezentaci <xref:System.TimeSpan> hodnotu výchozí a která je společná pro všechny předchozí verze rozhraní .NET Framework, než [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Výchozí hodnota je "c" <xref:System.TimeSpan> řetězec formátu; <xref:System.TimeSpan.ToString?displayProperty=nameWithType> metoda formátuje hodnotu časového intervalu pomocí řetězce "c" formátu.  
  
> [!NOTE]
>  <xref:System.TimeSpan>také podporuje "t" a "T" standardní řetězce formátu, které jsou stejné chování jako standardní formátovací řetězec "c".  
  
 Následující příklad vytvoří dvě instance <xref:System.TimeSpan> objekty, je používá k provádění aritmetických operací a zobrazuje výsledek. V každém případě používá složené formátování pro zobrazení <xref:System.TimeSpan> hodnotu na základě specifikace formátu "c".  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardc1.cs#1)]
 [!code-vb[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardc1.vb#1)]  
  
 [Zpět k tabulce](#Top)  
  
<a name="GeneralShort"></a>   
## <a name="the-general-short-g-format-specifier"></a>Specifikátor formátu krátkého obecné ("g")  
 "g" <xref:System.TimeSpan> specifikátor formátu vrátí řetězcovou reprezentaci <xref:System.TimeSpan> hodnoty ve formuláři compact zahrnutím jenom prvky, které jsou nezbytné. Má následující tvar:  
  
 [-] [*d*:]*h*:*mm*:*ss*[. *FFFFFFF*]  
  
 Prvky v hranatých závorek ([a]) jsou volitelné. Dvojtečkou (:) je literál symbol. Následující tabulka popisuje zbývající prvky.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|*-*|Volitelné záporné znaménko, který označuje záporné časovém intervalu.|  
|*d*|Volitelné počet dní, bez počátečních nul.|  
|*h*|Počet hodin, který se pohybuje od "0" a "23", bez počátečních nul.|  
|*mm*|Počet minut, který se pohybuje od "00" do "59"...|  
|*ss*|Počet sekund, který se pohybuje od "00" do "59"...|  
|*.*|Oddělovač zlomků sekund. Ta je ekvivalentní zadanou jazykovou verzi <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> vlastnost bez uživatele potlačuje.|  
|*FFFFFFF*|Zlomky sekund. Počet číslic, co se zobrazí.|  
  
 Jako "" specifikátor formátu je lokalizované specifikátor formátu "g". Jeho oddělovač zlomků sekund je založena na aktuální jazykové verze nebo zadaná jazyková verze <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> vlastnost.  
  
 Následující příklad vytvoří dvě instance <xref:System.TimeSpan> objekty, je používá k provádění aritmetických operací a zobrazuje výsledek. V každém případě používá složené formátování pro zobrazení <xref:System.TimeSpan> hodnotu na základě specifikace formátu "g". Kromě toho formáty <xref:System.TimeSpan> hodnotu na základě konvencí formátování aktuální systémovou kulturu (která je v tomto případě Czech - Czech Republic nebo en US) a francouzštinu - Francie (fr-FR) jazykovou verzi.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardshort1.cs#4)]
 [!code-vb[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardshort1.vb#4)]  
  
 [Zpět k tabulce](#Top)  
  
<a name="GeneralLong"></a>   
## <a name="the-general-long-g-format-specifier"></a>Specifikátor formátu obecného dlouhého ("G")  
 "G" <xref:System.TimeSpan> specifikátor formátu vrátí řetězcovou reprezentaci <xref:System.TimeSpan> hodnota v dlouhém formátu, který vždy obsahuje dnů a zlomků sekund. Řetězec, který je výsledkem specifikátor standardní formát "G" má následující formát:  
  
 [-] *d*:*hh*:*mm*:*ss*. *fffffff*  
  
 Prvky v hranatých závorek ([a]) jsou volitelné. Dvojtečkou (:) je literál symbol. Následující tabulka popisuje zbývající prvky.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|*-*|Volitelné záporné znaménko, který označuje záporné časovém intervalu.|  
|*d*|Počet dnů bez počátečních nul.|  
|*hh*|Počet hodin, který se pohybuje od "00" do "23".|  
|*mm*|Počet minut, který se pohybuje od "00" do "59".|  
|*ss*|Počet sekund, který se pohybuje od "00" do "59".|  
|*.*|Oddělovač zlomků sekund. Ta je ekvivalentní zadanou jazykovou verzi <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> vlastnost bez uživatele potlačuje.|  
|*fffffff*|Zlomky sekund.|  
  
 Jako "" specifikátor formátu je lokalizované specifikátor formátu "g". Jeho oddělovač zlomků sekund je založena na aktuální jazykové verze nebo zadaná jazyková verze <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> vlastnost.  
  
 Následující příklad vytvoří dvě instance <xref:System.TimeSpan> objekty, je používá k provádění aritmetických operací a zobrazuje výsledek. V každém případě používá složené formátování pro zobrazení <xref:System.TimeSpan> hodnotu na základě specifikace formátu "G". Kromě toho formáty <xref:System.TimeSpan> hodnotu na základě konvencí formátování aktuální systémovou kulturu (která je v tomto případě Czech - Czech Republic nebo en US) a francouzštinu - Francie (fr-FR) jazykovou verzi.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardlong1.cs#5)]
 [!code-vb[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardlong1.vb#5)]  
  
 [Zpět k tabulce](#Top)  
  
## <a name="see-also"></a>Viz také  
 [Typy formátování](../../../docs/standard/base-types/formatting-types.md)  
 [Vlastní řetězce formátu TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)  
 [Analýza řetězců](../../../docs/standard/base-types/parsing-strings.md)
