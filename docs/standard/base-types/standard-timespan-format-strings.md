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
ms.openlocfilehash: bc2ca7a94ffb19f62f354bdfc3040490b57e2689
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968553"
---
# <a name="standard-timespan-format-strings"></a>Standardní řetězce formátu TimeSpan
<a name="Top"></a>Standardní <xref:System.TimeSpan> formátovací řetězec používá jeden specifikátor formátu pro definování textové reprezentace <xref:System.TimeSpan> hodnoty, která je výsledkem operace formátování. Libovolný formátovací řetězec, který obsahuje více než jeden znak, včetně prázdných znaků, je interpretován jako <xref:System.TimeSpan> řetězec vlastního formátu. Další informace najdete v tématu [Vlastní řetězce formátu TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md) .  
  
 Řetězcové reprezentace <xref:System.TimeSpan> hodnot jsou vytvářeny voláním přetížení <xref:System.TimeSpan.ToString%2A?displayProperty=nameWithType> metody, stejně jako metody, které podporují složené formátování, jako je <xref:System.String.Format%2A?displayProperty=nameWithType>například. Další informace najdete v tématu [typy formátování](../../../docs/standard/base-types/formatting-types.md) a [složené formátování](../../../docs/standard/base-types/composite-formatting.md). Následující příklad ilustruje použití standardního formátovacího řetězce při formátování operací.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/formatexample1.cs#2)]
 [!code-vb[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/formatexample1.vb#2)]  
  
 Standardní <xref:System.TimeSpan> formátovací řetězce jsou také používány <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> metodami a <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> k definování požadovaného formátu vstupních řetězců k analýze operací. (Analýza převede řetězcovou reprezentaci hodnoty na tuto hodnotu.) Následující příklad ilustruje použití standardního formátovacího řetězce při analýze operací.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/parseexample1.cs#3)]
 [!code-vb[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/parseexample1.vb#3)]  
  
<a name="top"></a>V následující tabulce jsou uvedeny specifikátory formátu standardního časového intervalu.  
  
|Specifikátor formátu|Name|Popis|Příklady|  
|----------------------|----------|-----------------|--------------|  
|r|Konstantní (invariantní) formát|Tento specifikátor není závislý na jazykové verzi. Má formu `[-][d'.']hh':'mm':'ss['.'fffffff]`.<br /><br /> (Řetězce formátu "t" a "T" vytváří stejné výsledky.)<br /><br /> Další informace: [Specifikátor formátu konstanty ("c")](#Constant).|`TimeSpan.Zero` -> 00:00:00<br /><br /> `New TimeSpan(0, 0, 30, 0)` -> 00:30:00<br /><br /> `New TimeSpan(3, 17, 25, 30, 500)` -> 3.17:25:30.5000000|  
|"g"|Obecný krátký formát|Tento specifikátor výstupuje pouze to, co je potřeba. Je závislý na jazykové verzi a má formu `[-][d':']h':'mm':'ss[.FFFFFFF]`.<br /><br /> Další informace: [Obecný specifikátor krátkého formátu ("g")](#GeneralShort).|`New TimeSpan(1, 3, 16, 50, 500)`-> 1:3: 16:50.5 (EN-US)<br /><br /> `New TimeSpan(1, 3, 16, 50, 500)`-> 1:3: 16:50, 5 (fr-FR)<br /><br /> `New TimeSpan(1, 3, 16, 50, 599)`-> 1:3: 16:50.599 (EN-US)<br /><br /> `New TimeSpan(1, 3, 16, 50, 599)`-> 1:3: 16:50599 (fr-FR)|  
|"G"|Obecný formát Long|Tento specifikátor vždy vypíše dny a sedm zlomkových číslic. Je závislý na jazykové verzi a má formu `[-]d':'hh':'mm':'ss.fffffff`.<br /><br /> Další informace: [Obecný specifikátor formátu Long ("G")](#GeneralLong).|`New TimeSpan(18, 30, 0)`-> 0:18:30:00.0000000 (EN-US)<br /><br /> `New TimeSpan(18, 30, 0)` -> 0:18:30:00,0000000 (fr-FR)|  
  
<a name="Constant"></a>   
## <a name="the-constant-c-format-specifier"></a>Specifikátor formátu konstanty ("c")  
 Specifikátor formátu "c" vrátí řetězcovou reprezentaci <xref:System.TimeSpan> hodnoty v následujícím tvaru:  
  
 [-] [*d*.] *HH*:*mm*:*SS*[. *fffffff*]  
  
 Prvky v hranatých závorkách ([a]) jsou volitelné. Tečka (.) a dvojtečka (:) jsou literálové symboly. Zbývající prvky jsou popsány v následující tabulce.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|*-*|Volitelné záporné znaménko, které označuje záporný časový interval.|  
|*d*|Volitelný počet dnů bez úvodní nuly.|  
|*hh*|Počet hodin, které jsou v rozsahu od "00" do "23".|  
|*mm*|Počet minut, které jsou v rozsahu od "00" do "59".|  
|*ss*|Počet sekund, které jsou v rozsahu od "0" do "59".|  
|*fffffff*|Volitelná desetinná část sekundy.  Jeho hodnota může být v rozsahu od "0000001" (jedna značka nebo 1 10-millionth sekundy) na "9999999" (9 999 999 10-Desetimiliontiny sekundy nebo jedna sekunda méně než jedna značka).|  
  
 Na rozdíl od specifikátorů formátu "g" a "G" specifikátor formátu "c" nezohledňuje jazykovou verzi. Vytváří řetězcové vyjádření <xref:System.TimeSpan> hodnoty, která je invariantní a je společná pro všechny předchozí verze .NET Framework před .NET Framework 4. "c" je výchozí <xref:System.TimeSpan> formátovací řetězec <xref:System.TimeSpan.ToString?displayProperty=nameWithType> ; Metoda formátuje hodnotu časového intervalu pomocí formátovacího řetězce "c".  
  
> [!NOTE]
> <xref:System.TimeSpan>také podporuje standardní formátovací řetězce "t" a "T", které jsou identické v chování jako standardní formátovací řetězec "c".  
  
 Následující příklad vytvoří instanci dvou <xref:System.TimeSpan> objektů, používá je k provádění aritmetických operací a zobrazí výsledek. V každém případě používá složené formátování k zobrazení <xref:System.TimeSpan> hodnoty pomocí specifikátoru formátu "c".  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardc1.cs#1)]
 [!code-vb[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardc1.vb#1)]  
  
 [Zpět na tabulku](#Top)  
  
<a name="GeneralShort"></a>   
## <a name="the-general-short-g-format-specifier"></a>Obecný specifikátor krátkého formátu ("g")  
 Specifikátor formátu "g <xref:System.TimeSpan> " vrátí řetězcovou reprezentaci <xref:System.TimeSpan> hodnoty v kompaktní podobě tím, že zahrne pouze prvky, které jsou nezbytné. Má následující formát:  
  
 [-][*d*:]*h*:*mm*:*ss*[.*FFFFFFF*]  
  
 Prvky v hranatých závorkách ([a]) jsou volitelné. Dvojtečka (:) je literálový symbol. Zbývající prvky jsou popsány v následující tabulce.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|*-*|Volitelné záporné znaménko, které označuje záporný časový interval.|  
|*d*|Volitelný počet dnů bez úvodní nuly.|  
|*h*|Počet hodin, které jsou v rozsahu od "0" do "23", bez počátečních nul.|  
|*mm*|Počet minut, které jsou v rozsahu od "00" do "59".|  
|*ss*|Počet sekund, které jsou v rozsahu od "00" do "59"..|  
|*.*|Oddělovač zlomků sekund Je ekvivalentní se zadanou <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> vlastností jazykové verze bez přepsání uživatelem.|  
|*FFFFFFF*|Zlomky sekund. Zobrazí se co nejvíce číslic.|  
  
 Podobně jako specifikátor formátu "g" je lokalizovaný specifikátor formátu "g". Oddělovač zlomků sekund je založen buď na aktuální jazykové verzi, nebo na <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> vlastnosti zadané jazykové verze.  
  
 Následující příklad vytvoří instanci dvou <xref:System.TimeSpan> objektů, používá je k provádění aritmetických operací a zobrazí výsledek. V každém případě používá složené formátování k zobrazení <xref:System.TimeSpan> hodnoty pomocí specifikátoru formátu "g". Kromě toho formátuje <xref:System.TimeSpan> hodnotu pomocí formátovacích úmluv aktuální jazykové verze systému (což je v tomto případě anglické USA nebo en-us) a jazyková verze francouzština-France (fr-FR).  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardshort1.cs#4)]
 [!code-vb[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardshort1.vb#4)]  
  
 [Zpět na tabulku](#Top)  
  
<a name="GeneralLong"></a>   
## <a name="the-general-long-g-format-specifier"></a>Obecný specifikátor formátu Long ("G")  
 Specifikátor formátu "G <xref:System.TimeSpan> " vrátí řetězcovou reprezentaci <xref:System.TimeSpan> hodnoty v dlouhé podobě, která vždy zahrnuje jak dny, tak i zlomky sekund. Řetězec, který je výsledkem specifikátoru standardního formátu "G", má následující formát:  
  
 [-] *d*:*HH*:*mm*:*SS*. *fffffff*  
  
 Prvky v hranatých závorkách ([a]) jsou volitelné. Dvojtečka (:) je literálový symbol. Zbývající prvky jsou popsány v následující tabulce.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|*-*|Volitelné záporné znaménko, které označuje záporný časový interval.|  
|*d*|Počet dnů bez úvodní nuly.|  
|*hh*|Počet hodin, které jsou v rozsahu od "00" do "23".|  
|*mm*|Počet minut, které jsou v rozsahu od "00" do "59".|  
|*ss*|Počet sekund, které jsou v rozsahu od "00" do "59".|  
|*.*|Oddělovač zlomků sekund Je ekvivalentní se zadanou <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> vlastností jazykové verze bez přepsání uživatelem.|  
|*fffffff*|Zlomky sekund.|  
  
 Podobně jako specifikátor formátu "g" je lokalizovaný specifikátor formátu "g". Oddělovač zlomků sekund je založen buď na aktuální jazykové verzi, nebo na <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> vlastnosti zadané jazykové verze.  
  
 Následující příklad vytvoří instanci dvou <xref:System.TimeSpan> objektů, používá je k provádění aritmetických operací a zobrazí výsledek. V každém případě používá složené formátování k zobrazení <xref:System.TimeSpan> hodnoty pomocí specifikátoru formátu "G". Kromě toho formátuje <xref:System.TimeSpan> hodnotu pomocí formátovacích úmluv aktuální jazykové verze systému (což je v tomto případě anglické USA nebo en-us) a jazyková verze francouzština-France (fr-FR).  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardlong1.cs#5)]
 [!code-vb[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardlong1.vb#5)]  
  
 [Zpět na tabulku](#Top)  
  
## <a name="see-also"></a>Viz také:

- [Typy formátování](../../../docs/standard/base-types/formatting-types.md)
- [Vlastní řetězce formátu TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)
- [Analýza řetězců](../../../docs/standard/base-types/parsing-strings.md)
