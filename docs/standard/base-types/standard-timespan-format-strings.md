---
title: Formátové řetězce Standard TimeSpan
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
ms.openlocfilehash: ec06edc16829c6d4caf8c760922aac1471e365c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75346633"
---
# <a name="standard-timespan-format-strings"></a>Formátové řetězce Standard TimeSpan

Standardní <xref:System.TimeSpan> formátovací řetězec používá specifikátor jednoho formátu k <xref:System.TimeSpan> definování textové reprezentace hodnoty, která je výsledkem operace formátování. Libovolný formátovací řetězec, který obsahuje více než jeden znak, <xref:System.TimeSpan> včetně prázdného místa, je interpretován jako vlastní formátovací řetězec. Další informace naleznete [v tématu Vlastní formátovací řetězce TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md) .  
  
 Řetězcové reprezentace <xref:System.TimeSpan> hodnot jsou vytvářeny voláním <xref:System.TimeSpan.ToString%2A?displayProperty=nameWithType> přetížení metody, stejně jako metodami, které <xref:System.String.Format%2A?displayProperty=nameWithType>podporují složené formátování, například . Další informace naleznete [v tématu Typy formátování](../../../docs/standard/base-types/formatting-types.md) a Složené [formátování](../../../docs/standard/base-types/composite-formatting.md). Následující příklad ilustruje použití standardních formátovacích řetězců při operacích formátování.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/formatexample1.cs#2)]
 [!code-vb[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/formatexample1.vb#2)]  
  
 Standardní <xref:System.TimeSpan> formátovací řetězce jsou <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> také <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> používány a metody k definování požadovaného formátu vstupních řetězců pro analýzu operací. (Analýza převede řetězcovou reprezentaci hodnoty na tuto hodnotu.) Následující příklad ilustruje použití standardních formátovacích řetězců v operacích analýzy.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/parseexample1.cs#3)]
 [!code-vb[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/parseexample1.vb#3)]  
  
V následující tabulce jsou uvedeny specifikátory formátu standardního časového intervalu.  
  
|Specifikátor formátu|Name (Název)|Popis|Příklady|  
|----------------------|----------|-----------------|--------------|  
|"c"|Konstantní (invariantní) formát|Tento specifikátor není citlivý na jazykovou verzi. Má podobu `[-][d'.']hh':'mm':'ss['.'fffffff]`.<br /><br /> (Formátovací řetězce "t" a "T" vytvářejí stejné výsledky.)<br /><br /> Další informace: [Specifikátor formátu Konstanta ("c")](#the-constant-c-format-specifier).|`TimeSpan.Zero`-> 00:00:00.<br /><br /> `New TimeSpan(0, 0, 30, 0)`-> 00:30:00.<br /><br /> `New TimeSpan(3, 17, 25, 30, 500)`-> 3.17:25:30.500000|  
|"g"|Obecný krátký formát|Tento specifikátor vyvezuje pouze to, co je potřeba. Je citlivé na jazykovou `[-][d':']h':'mm':'ss[.FFFFFFF]`verzi a má podobu .<br /><br /> Další informace: [Obecný krátký ("g") Specifikátor formátu](#the-general-short-g-format-specifier).|`New TimeSpan(1, 3, 16, 50, 500)`-> 1:3:16:50.5 (cs)-> 1:3:16:50.5 (en-US)<br /><br /> `New TimeSpan(1, 3, 16, 50, 500)`-> 1:3:16:50,5 (fr-FR)<br /><br /> `New TimeSpan(1, 3, 16, 50, 599)`-> 1:3:16:50.599 (cs.)<br /><br /> `New TimeSpan(1, 3, 16, 50, 599)`-> 1:3:16:50,599 (fr-FR)|  
|"G"|Obecný dlouhý formát|Tento specifikátor vždy vynese dny a sedm desetinných míst. Je citlivé na jazykovou `[-]d':'hh':'mm':'ss.fffffff`verzi a má podobu .<br /><br /> Další informace: [Specifikátor formátu General Long ("G")](#the-general-long-g-format-specifier).|`New TimeSpan(18, 30, 0)`-> 0:18:30:00.000000 (cs-US)<br /><br /> `New TimeSpan(18, 30, 0)`-> 0:18:30:00,0000000 (fr-FR)|  

## <a name="the-constant-c-format-specifier"></a>Specifikátor formátu Konstanta ("c")  
 Specifikátor formátu c vrátí řetězcovou reprezentaci <xref:System.TimeSpan> hodnoty v následujícím formuláři:  
  
 [-] *[d*.] *hh*:*mm*:*ss*[.* fffffff*]  
  
 Prvky v hranatých závorkách ([ a ]) jsou volitelné. Tečka (.) a dvojtečka (:) jsou doslovné symboly. Následující tabulka popisuje zbývající prvky.  
  
|Element|Popis|  
|-------------|-----------------|  
|*-*|Volitelné záporné znaménko, které označuje záporný časový interval.|  
|*D*|Volitelný počet dní bez počátečních nul.|  
|*hh*|Počet hodin, který se pohybuje od "00" do "23".|  
|*Mm*|Počet minut, který se pohybuje od "00" do "59".|  
|*Ss*|Počet sekund, který se pohybuje od "0" do "59".|  
|*fffffffff*|Volitelná zlomková část sekundy.  Jeho hodnota se může pohybovat od "0000001" (jedno klíště nebo jedna desetimiliontina sekundy) do "9999999" (9 999 999 deset millionin sekundy nebo o jednu sekundu méně jednoho klíštěte).|  
  
 Na rozdíl od specifikátorů formátu "g" a "G" není specifikátor formátu "c" citlivý na jazykovou verzi. Vytváří řetězcovou reprezentaci <xref:System.TimeSpan> hodnoty, která je invariantní a která je společná pro všechny předchozí verze rozhraní .NET Framework před rozhraním .NET Framework 4. "c" je <xref:System.TimeSpan> výchozí formátovací řetězec; metoda <xref:System.TimeSpan.ToString?displayProperty=nameWithType> formátuje hodnotu časového intervalu pomocí formátovacího řetězce "c".  
  
> [!NOTE]
> <xref:System.TimeSpan>také podporuje řetězce standardního formátu "t" a "T", které jsou v chování identické s řetězcem standardního formátu "c".  
  
 Následující příklad inkonzisuje dva <xref:System.TimeSpan> objekty, používá je k provádění aritmetické operace a zobrazí výsledek. V každém případě používá složené formátování k <xref:System.TimeSpan> zobrazení hodnoty pomocí specifikátoru formátu "c".  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardc1.cs#1)]
 [!code-vb[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardc1.vb#1)]  

## <a name="the-general-short-g-format-specifier"></a>Specifikátor formátu Obecné krátké ("g")  
 Specifikátor formátu <xref:System.TimeSpan> "g" vrátí řetězcovou <xref:System.TimeSpan> reprezentaci hodnoty v kompaktním formuláři zahrnutím pouze prvků, které jsou nezbytné. Má následující formu:  
  
 [-] *[d]]* *h*:*mm*:*ss*[.* FFFFFFF*]  
  
 Prvky v hranatých závorkách ([ a ]) jsou volitelné. Dvojtečka (:) je doslovný symbol. Následující tabulka popisuje zbývající prvky.  
  
|Element|Popis|  
|-------------|-----------------|  
|*-*|Volitelné záporné znaménko, které označuje záporný časový interval.|  
|*D*|Volitelný počet dní bez počátečních nul.|  
|*H*|Počet hodin, který se pohybuje od "0" do "23", bez počátečnínuly.|  
|*Mm*|Počet minut, který se pohybuje od "00" do "59"..|  
|*Ss*|Počet sekund, který se pohybuje od "00" do "59"..|  
|*.*|Oddělovač vteřin ve zlomcích. Je ekvivalentní zadané <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> vlastnosti jazykové verze bez přepsání uživatele.|  
|*FFFFFFF*|Zlomkové vteřiny. Zobrazí se co nejméně číslic.|  
  
 Podobně jako specifikátor formátu "G" je lokalizován specifikátor formátu "g". Jeho oddělovač vteřin zlomku je založen na aktuální <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> jazykové verzi nebo na vlastnosti zadané jazykové verze.  
  
 Následující příklad inkonzisuje dva <xref:System.TimeSpan> objekty, používá je k provádění aritmetické operace a zobrazí výsledek. V každém případě používá složené formátování k <xref:System.TimeSpan> zobrazení hodnoty pomocí specifikátoru formátu "g". Kromě toho formátuje <xref:System.TimeSpan> hodnotu pomocí konvencí formátování aktuální jazykové verze systému (což je v tomto případě angličtina - Spojené státy nebo en US) a verze Francouzština - Francie (fr-FR).  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardshort1.cs#4)]
 [!code-vb[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardshort1.vb#4)]  

## <a name="the-general-long-g-format-specifier"></a>Specifikátor formátu Obecné dlouhé ("G")  
 Specifikátor formátu <xref:System.TimeSpan> "G" vrátí řetězcovou <xref:System.TimeSpan> reprezentaci hodnoty v dlouhé podobě, která vždy obsahuje dny i vteřiny zlomku. Řetězec, který je výsledkem standardního specifikátoru formátu "G", má následující tvar:  
  
 [-] *d*:*hh*:*mm*:*ss*. *fffffffff*  
  
 Prvky v hranatých závorkách ([ a ]) jsou volitelné. Dvojtečka (:) je doslovný symbol. Následující tabulka popisuje zbývající prvky.  
  
|Element|Popis|  
|-------------|-----------------|  
|*-*|Volitelné záporné znaménko, které označuje záporný časový interval.|  
|*D*|Počet dní bez úvodních nul.|  
|*hh*|Počet hodin, který se pohybuje od "00" do "23".|  
|*Mm*|Počet minut, který se pohybuje od "00" do "59".|  
|*Ss*|Počet sekund, který se pohybuje od "00" do "59".|  
|*.*|Oddělovač vteřin ve zlomcích. Je ekvivalentní zadané <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> vlastnosti jazykové verze bez přepsání uživatele.|  
|*fffffffff*|Zlomkové vteřiny.|  
  
 Podobně jako specifikátor formátu "G" je lokalizován specifikátor formátu "g". Jeho oddělovač vteřin zlomku je založen na aktuální <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> jazykové verzi nebo na vlastnosti zadané jazykové verze.  
  
 Následující příklad inkonzisuje dva <xref:System.TimeSpan> objekty, používá je k provádění aritmetické operace a zobrazí výsledek. V každém případě používá složené formátování k <xref:System.TimeSpan> zobrazení hodnoty pomocí specifikátoru formátu "G". Kromě toho formátuje <xref:System.TimeSpan> hodnotu pomocí konvencí formátování aktuální jazykové verze systému (což je v tomto případě angličtina - Spojené státy nebo en US) a verze Francouzština - Francie (fr-FR).  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardlong1.cs#5)]
 [!code-vb[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardlong1.vb#5)]
  
## <a name="see-also"></a>Viz také

- [Typy formátování](../../../docs/standard/base-types/formatting-types.md)
- [Vlastní řetězce formátu TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)
- [Analýza řetězců](../../../docs/standard/base-types/parsing-strings.md)
