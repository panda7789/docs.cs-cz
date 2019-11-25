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
ms.openlocfilehash: c699ed68606293b1a49a540e00636cf7f56bdf2f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73972097"
---
# <a name="standard-timespan-format-strings"></a>Standardní řetězce formátu TimeSpan

Řetězec formátu standardního <xref:System.TimeSpan> používá jeden specifikátor formátu pro definování textové reprezentace <xref:System.TimeSpan> hodnoty, která je výsledkem operace formátování. Libovolný formátovací řetězec, který obsahuje více než jeden znak, včetně prázdných znaků, je interpretován jako řetězec formátu vlastního <xref:System.TimeSpan>. Další informace najdete v tématu [Vlastní řetězce formátu TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md) .  
  
 Řetězcové reprezentace hodnot <xref:System.TimeSpan> jsou vytvářeny voláním přetížení <xref:System.TimeSpan.ToString%2A?displayProperty=nameWithType> metody a také metodami, které podporují složené formátování, jako je například <xref:System.String.Format%2A?displayProperty=nameWithType>. Další informace najdete v tématu [typy formátování](../../../docs/standard/base-types/formatting-types.md) a [složené formátování](../../../docs/standard/base-types/composite-formatting.md). Následující příklad ilustruje použití standardního formátovacího řetězce při formátování operací.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/formatexample1.cs#2)]
 [!code-vb[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/formatexample1.vb#2)]  
  
 Řetězce formátu standard <xref:System.TimeSpan> jsou také používány metodami <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> a <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> k definování požadovaného formátu vstupních řetězců pro analýzu operací. (Analýza převede řetězcovou reprezentaci hodnoty na tuto hodnotu.) Následující příklad ilustruje použití standardního formátovacího řetězce při analýze operací.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/parseexample1.cs#3)]
 [!code-vb[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/parseexample1.vb#3)]  
  
V následující tabulce jsou uvedeny specifikátory formátu standardního časového intervalu.  
  
|Specifikátor formátu|Name|Popis|Příklady|  
|----------------------|----------|-----------------|--------------|  
|r|Konstantní (invariantní) formát|Tento specifikátor není závislý na jazykové verzi. Převezme `[-][d'.']hh':'mm':'ss['.'fffffff]`formuláře.<br /><br /> (Řetězce formátu "t" a "T" vytváří stejné výsledky.)<br /><br /> Další informace: [specifikátor formátu konstanty ("c")](#the-constant-c-format-specifier).|`TimeSpan.Zero` – > 00:00:00<br /><br /> `New TimeSpan(0, 0, 30, 0)` – > 00:30:00<br /><br /> `New TimeSpan(3, 17, 25, 30, 500)`-> 3.17:25:30.5000000|  
|"g"|Obecný krátký formát|Tento specifikátor výstupuje pouze to, co je potřeba. Je závislá na jazykové verzi a má `[-][d':']h':'mm':'ss[.FFFFFFF]`formuláře.<br /><br /> Další informace: [specifikátor obecného krátkého formátu ("g")](#the-general-short-g-format-specifier).|`New TimeSpan(1, 3, 16, 50, 500)`-> 1:3: 16:50.5 (EN-US)<br /><br /> `New TimeSpan(1, 3, 16, 50, 500)`-> 1:3: 16:50, 5 (fr-FR)<br /><br /> `New TimeSpan(1, 3, 16, 50, 599)`-> 1:3: 16:50.599 (EN-US)<br /><br /> `New TimeSpan(1, 3, 16, 50, 599)`-> 1:3: 16:50599 (fr-FR)|  
|"G"|Obecný formát Long|Tento specifikátor vždy vypíše dny a sedm zlomkových číslic. Je závislá na jazykové verzi a má `[-]d':'hh':'mm':'ss.fffffff`formuláře.<br /><br /> Další informace: [specifikátor obecného dlouhého formátu ("G")](#the-general-long-g-format-specifier).|`New TimeSpan(18, 30, 0)`-> 0:18:30:00.0000000 (EN-US)<br /><br /> `New TimeSpan(18, 30, 0)`-> 0:18:30:00, 0000000 (fr-FR)|  

## <a name="the-constant-c-format-specifier"></a>Specifikátor formátu konstanty ("c")  
 Specifikátor formátu "c" Vrací řetězcovou reprezentaci hodnoty <xref:System.TimeSpan> v následujícím tvaru:  
  
 [-] [*d*.] *HH*:*mm*:*SS*[. *fffffff*]  
  
 Prvky v hranatých závorkách ([a]) jsou volitelné. Tečka (.) a dvojtečka (:) jsou literálové symboly. Zbývající prvky jsou popsány v následující tabulce.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|*-*|Volitelné záporné znaménko, které označuje záporný časový interval.|  
|*trojrozměrné*|Volitelný počet dnů bez úvodní nuly.|  
|*HH*|Počet hodin, které jsou v rozsahu od "00" do "23".|  
|*výšce*|Počet minut, které jsou v rozsahu od "00" do "59".|  
|*SS*|Počet sekund, které jsou v rozsahu od "0" do "59".|  
|*fffffff*|Volitelná desetinná část sekundy.  Jeho hodnota může být v rozsahu od "0000001" (jedna značka nebo 1 10-millionth sekundy) na "9999999" (9 999 999 10-Desetimiliontiny sekundy nebo jedna sekunda méně než jedna značka).|  
  
 Na rozdíl od specifikátorů formátu "g" a "G" specifikátor formátu "c" nezohledňuje jazykovou verzi. Vytváří řetězcovou reprezentaci <xref:System.TimeSpan> hodnoty, která je invariantovaná a je společná pro všechny předchozí verze .NET Framework před .NET Framework 4. "c" je výchozí řetězec formátu <xref:System.TimeSpan>; Metoda <xref:System.TimeSpan.ToString?displayProperty=nameWithType> formátuje hodnotu časového intervalu pomocí formátovacího řetězce "c".  
  
> [!NOTE]
> <xref:System.TimeSpan> také podporuje standardní formátovací řetězce "t" a "T", které jsou ve stejném chování jako standardní formátovací řetězec "c".  
  
 Následující příklad vytvoří instanci dvou objektů <xref:System.TimeSpan>, používá je k provádění aritmetických operací a zobrazí výsledek. V každém případě používá složené formátování k zobrazení <xref:System.TimeSpan> hodnoty pomocí specifikátoru formátu "c".  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardc1.cs#1)]
 [!code-vb[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardc1.vb#1)]  

## <a name="the-general-short-g-format-specifier"></a>Obecný specifikátor krátkého formátu ("g")  
 Specifikátor formátu "g" <xref:System.TimeSpan> vrátí řetězcovou reprezentaci hodnoty <xref:System.TimeSpan> v kompaktní podobě tím, že zahrne pouze prvky, které jsou nezbytné. Má následující formát:  
  
 [-] [*d*:] *h*:*mm*:*SS*[. *FFFFFFF*]  
  
 Prvky v hranatých závorkách ([a]) jsou volitelné. Dvojtečka (:) je literálový symbol. Zbývající prvky jsou popsány v následující tabulce.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|*-*|Volitelné záporné znaménko, které označuje záporný časový interval.|  
|*trojrozměrné*|Volitelný počet dnů bez úvodní nuly.|  
|*y*|Počet hodin, které jsou v rozsahu od "0" do "23", bez počátečních nul.|  
|*výšce*|Počet minut, které jsou v rozsahu od "00" do "59".|  
|*SS*|Počet sekund, které jsou v rozsahu od "00" do "59"..|  
|*.*|Oddělovač zlomků sekund Je ekvivalentní s vlastností <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> zadané jazykové verze bez přepsání uživatelem.|  
|*FFFFFFF*|Zlomky sekund. Zobrazí se co nejvíce číslic.|  
  
 Podobně jako specifikátor formátu "g" je lokalizovaný specifikátor formátu "g". Oddělovač zlomků sekund je založen buď na aktuální jazykové verzi, nebo na vlastnosti <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> zadané jazykové verze.  
  
 Následující příklad vytvoří instanci dvou objektů <xref:System.TimeSpan>, používá je k provádění aritmetických operací a zobrazí výsledek. V každém případě používá složené formátování k zobrazení <xref:System.TimeSpan> hodnoty pomocí specifikátoru formátu "g". Kromě toho formátuje <xref:System.TimeSpan> hodnoty pomocí formátovacích úmluv aktuální jazykové verze systému (což je v tomto případě anglické USA nebo en-US) a jazyková verze francouzština-Francie (fr-FR).  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardshort1.cs#4)]
 [!code-vb[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardshort1.vb#4)]  

## <a name="the-general-long-g-format-specifier"></a>Obecný specifikátor formátu Long ("G")  
 Specifikátor formátu "G" <xref:System.TimeSpan> vrátí řetězcovou reprezentaci hodnoty <xref:System.TimeSpan> v dlouhé podobě, která vždy zahrnuje jak dny, tak i zlomky sekund. Řetězec, který je výsledkem specifikátoru standardního formátu "G", má následující formát:  
  
 [-] *d*:*HH*:*mm*:*SS*. *fffffff*  
  
 Prvky v hranatých závorkách ([a]) jsou volitelné. Dvojtečka (:) je literálový symbol. Zbývající prvky jsou popsány v následující tabulce.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|*-*|Volitelné záporné znaménko, které označuje záporný časový interval.|  
|*trojrozměrné*|Počet dnů bez úvodní nuly.|  
|*HH*|Počet hodin, které jsou v rozsahu od "00" do "23".|  
|*výšce*|Počet minut, které jsou v rozsahu od "00" do "59".|  
|*SS*|Počet sekund, které jsou v rozsahu od "00" do "59".|  
|*.*|Oddělovač zlomků sekund Je ekvivalentní s vlastností <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> zadané jazykové verze bez přepsání uživatelem.|  
|*fffffff*|Zlomky sekund.|  
  
 Podobně jako specifikátor formátu "g" je lokalizovaný specifikátor formátu "g". Oddělovač zlomků sekund je založen buď na aktuální jazykové verzi, nebo na vlastnosti <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> zadané jazykové verze.  
  
 Následující příklad vytvoří instanci dvou objektů <xref:System.TimeSpan>, používá je k provádění aritmetických operací a zobrazí výsledek. V každém případě používá složené formátování k zobrazení <xref:System.TimeSpan> hodnoty pomocí specifikátoru formátu "G". Kromě toho formátuje <xref:System.TimeSpan> hodnoty pomocí formátovacích úmluv aktuální jazykové verze systému (což je v tomto případě anglické USA nebo en-US) a jazyková verze francouzština-Francie (fr-FR).  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardlong1.cs#5)]
 [!code-vb[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardlong1.vb#5)]
  
## <a name="see-also"></a>Viz také:

- [Typy formátování](../../../docs/standard/base-types/formatting-types.md)
- [Vlastní řetězce formátu TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)
- [Analýza řetězců](../../../docs/standard/base-types/parsing-strings.md)
