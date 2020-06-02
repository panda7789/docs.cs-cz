---
title: Porovnávání řetězců v .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- value comparisons of strings
- LastIndexOf method
- CompareTo method
- IndexOf method
- Compare method
- strings [.NET Framework], comparing
- CompareOrdinal method
- EndsWith method
- Equals method
- StartsWith method
ms.assetid: 977dc094-fe19-4955-98ec-d2294d04a4ba
ms.openlocfilehash: 7997f3098265b76f8fe2ef4fc7ab0e17f6e81d69
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289327"
---
# <a name="comparing-strings-in-net"></a>Porovnávání řetězců v .NET
Rozhraní .NET poskytuje několik metod pro porovnání hodnot řetězců. Následující tabulka uvádí a popisuje metody porovnání hodnot.  
  
|Název metody|Použití|  
|-----------------|---------|  
|<xref:System.String.Compare%2A?displayProperty=nameWithType>|Porovná hodnoty dvou řetězců. Vrací celočíselnou hodnotu.|  
|<xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType>|Porovná dva řetězce bez ohledu na místní jazykovou verzi. Vrací celočíselnou hodnotu.|  
|<xref:System.String.CompareTo%2A?displayProperty=nameWithType>|Porovná aktuální objekt řetězce s jiným řetězcem. Vrací celočíselnou hodnotu.|  
|<xref:System.String.StartsWith%2A?displayProperty=nameWithType>|Určuje, zda řetězec začíná předaným řetězcem. Vrací logickou hodnotu.|  
|<xref:System.String.EndsWith%2A?displayProperty=nameWithType>|Určuje, zda řetězec končí předaným řetězcem. Vrací logickou hodnotu.|  
|<xref:System.String.Equals%2A?displayProperty=nameWithType>|Určuje, zda jsou dva řetězce stejné. Vrací logickou hodnotu.|  
|<xref:System.String.IndexOf%2A?displayProperty=nameWithType>|Vrátí pozici indexu znaku nebo řetězce, počínaje od začátku řetězce, který zkoumáte. Vrací celočíselnou hodnotu.|  
|<xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>|Vrátí pozici indexu znaku nebo řetězce, počínaje od konce řetězce, který zkoumáte. Vrací celočíselnou hodnotu.|  
  
## <a name="compare"></a>Porovnání  
 Statická <xref:System.String.Compare%2A?displayProperty=nameWithType> Metoda poskytuje důkladný způsob porovnávání dvou řetězců. Tato metoda je kulturně zavědoma. Tuto funkci můžete použít k porovnání dvou řetězců nebo podřetězců dvou řetězců. Navíc jsou k dispozici přetížení, která se týkají nebo netýkají případu a kulturní odchylky. Následující tabulka uvádí tři celočíselné hodnoty, které může tato metoda vracet.  
  
|Vrácená hodnota|Podmínka|  
|------------------|---------------|  
|Záporné celé číslo|První řetězec předchází druhému řetězci v pořadí řazení.<br /><br /> -nebo-<br /><br /> První řetězec je `null` .|  
|0|První řetězec a druhý řetězec jsou stejné.<br /><br /> -nebo-<br /><br /> Oba řetězce jsou `null` .|  
|Kladné celé číslo<br /><br /> -nebo-<br /><br /> 1|První řetězec následuje za druhým řetězcem v pořadí řazení.<br /><br /> -nebo-<br /><br /> Druhý řetězec je `null` .|  
  
> [!IMPORTANT]
> <xref:System.String.Compare%2A?displayProperty=nameWithType>Metoda je primárně určena pro použití při řazení nebo řazení řetězců. Tuto metodu byste neměli používat <xref:System.String.Compare%2A?displayProperty=nameWithType> k otestování rovnosti (to znamená pro explicitní vyhledání návratové hodnoty 0 bez ohledu na to, zda je jeden řetězec menší nebo větší než druhý). Místo toho pro určení, zda jsou dva řetězce stejné, použijte <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metodu.  
  
 Následující příklad používá <xref:System.String.Compare%2A?displayProperty=nameWithType> metodu k určení relativních hodnot dvou řetězců.  
  
 [!code-cpp[Conceptual.String.BasicOps#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#6)]
 [!code-csharp[Conceptual.String.BasicOps#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#6)]
 [!code-vb[Conceptual.String.BasicOps#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#6)]  
  
 Tento příklad `-1` se zobrazí v konzole nástroje.  
  
 V předchozím příkladu je standardně závislá na jazykové verzi. Chcete-li provést porovnání řetězců nezávisle na jazykové verzi, použijte přetížení <xref:System.String.Compare%2A?displayProperty=nameWithType> metody, která umožňuje určit jazykovou verzi, která má být použita, zadáním parametru *jazykové verze* . Příklad, který ukazuje, jak použít <xref:System.String.Compare%2A?displayProperty=nameWithType> metodu k provedení porovnání nezávislého na jazykové verzi, naleznete v tématu [provádění porovnávání řetězců nezávislých na jazykové verzi](../globalization-localization/performing-culture-insensitive-string-comparisons.md).  
  
## <a name="compareordinal"></a>CompareOrdinal  
 <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType>Metoda porovná dva řetězcové objekty bez zvážení místní kultury. Návratové hodnoty této metody jsou shodné s hodnotami vrácenými metodou **Compare** v předchozí tabulce.  
  
> [!IMPORTANT]
> <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType>Metoda je primárně určena pro použití při řazení nebo řazení řetězců. Tuto metodu byste neměli používat <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> k otestování rovnosti (to znamená pro explicitní vyhledání návratové hodnoty 0 bez ohledu na to, zda je jeden řetězec menší nebo větší než druhý). Místo toho pro určení, zda jsou dva řetězce stejné, použijte <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metodu.  
  
 Následující příklad používá metodu **CompareOrdinal** pro porovnání hodnot dvou řetězců.  
  
 [!code-cpp[Conceptual.String.BasicOps#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#7)]
 [!code-csharp[Conceptual.String.BasicOps#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#7)]
 [!code-vb[Conceptual.String.BasicOps#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#7)]  
  
 Tento příklad `-32` se zobrazí v konzole nástroje.  
  
## <a name="compareto"></a>CompareTo  
 <xref:System.String.CompareTo%2A?displayProperty=nameWithType>Metoda porovnává řetězec, který je aktuálním objektem řetězce zapouzdřen do jiného řetězce nebo objektu. Návratové hodnoty této metody jsou shodné s hodnotami vrácenými <xref:System.String.Compare%2A?displayProperty=nameWithType> metodou v předchozí tabulce.  
  
> [!IMPORTANT]
> <xref:System.String.CompareTo%2A?displayProperty=nameWithType>Metoda je primárně určena pro použití při řazení nebo řazení řetězců. Tuto metodu byste neměli používat <xref:System.String.CompareTo%2A?displayProperty=nameWithType> k otestování rovnosti (to znamená pro explicitní vyhledání návratové hodnoty 0 bez ohledu na to, zda je jeden řetězec menší nebo větší než druhý). Místo toho pro určení, zda jsou dva řetězce stejné, použijte <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metodu.  
  
 Následující příklad používá <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metodu pro porovnání `string1` objektu s `string2` objektem.  
  
 [!code-cpp[Conceptual.String.BasicOps#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#8)]
 [!code-csharp[Conceptual.String.BasicOps#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#8)]
 [!code-vb[Conceptual.String.BasicOps#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#8)]  
  
 Tento příklad `-1` se zobrazí v konzole nástroje.  
  
 Všechna přetížení <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody provádějí porovnání zohledňující jazykovou verzi a rozlišování velkých a malých písmen ve výchozím nastavení. Žádná přetížení této metody nejsou k dispozici, aby bylo možné provádět porovnání nezávislé na jazykové verzi. Pro přehlednost kódu doporučujeme použít místo toho metodu **String. Compare** , zadat <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> pro operace závislé na jazykové verzi nebo <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> pro operace nezávislé na jazykové verzi. Příklady, které ukazují, jak použít metodu **String. Compare** k provedení porovnávání závislých na jazykové verzi a nezávisle na jazykové verzi, naleznete v tématu [provádění porovnávání řetězců nezávislých na jazykové verzi](../globalization-localization/performing-culture-insensitive-string-comparisons.md).  
  
## <a name="equals"></a>Rovná se  
 Metoda **String. Equals** umožňuje snadno určit, zda jsou dva řetězce stejné. Tato metoda rozlišování velkých a malých písmen vrátí logickou hodnotu **true** nebo **false** . Dá se použít z existující třídy, jak je znázorněno v následujícím příkladu. Následující příklad používá metodu **Equals** k určení, zda objekt řetězce obsahuje frázi "Hello World".  
  
 [!code-cpp[Conceptual.String.BasicOps#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#9)]
 [!code-csharp[Conceptual.String.BasicOps#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#9)]
 [!code-vb[Conceptual.String.BasicOps#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#9)]  
  
 Tento příklad `True` se zobrazí v konzole nástroje.  
  
 Tuto metodu lze také použít jako statickou metodu. Následující příklad porovnává dva řetězcové objekty pomocí statické metody.  
  
 [!code-cpp[Conceptual.String.BasicOps#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#10)]
 [!code-csharp[Conceptual.String.BasicOps#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#10)]
 [!code-vb[Conceptual.String.BasicOps#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#10)]  
  
 Tento příklad `True` se zobrazí v konzole nástroje.  
  
## <a name="startswith-and-endswith"></a>StartsWith a EndsWith  
 Můžete použít metodu **String. StartsWith** k určení, zda objekt řetězce začíná stejnými znaky, které zahrnují jiný řetězec. Tato metoda rozlišování velkých a malých písmen vrátí **hodnotu true** , pokud aktuální objekt řetězce začíná předaným řetězcem a **hodnotu false** , pokud tomu tak není. Následující příklad používá tuto metodu k určení, zda objekt řetězce začíná řetězcem "Hello".  
  
 [!code-cpp[Conceptual.String.BasicOps#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#11)]
 [!code-csharp[Conceptual.String.BasicOps#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#11)]
 [!code-vb[Conceptual.String.BasicOps#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#11)]  
  
 Tento příklad `True` se zobrazí v konzole nástroje.  
  
 Metoda **String. EndsWith** porovná předaný řetězec znakům, které existují na konci aktuálního objektu řetězce. Vrátí také logickou hodnotu. Následující příklad zkontroluje konec řetězce pomocí metody **endsWith** .  
  
 [!code-cpp[Conceptual.String.BasicOps#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#12)]
 [!code-csharp[Conceptual.String.BasicOps#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#12)]
 [!code-vb[Conceptual.String.BasicOps#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#12)]  
  
 Tento příklad `False` se zobrazí v konzole nástroje.  
  
## <a name="indexof-and-lastindexof"></a>IndexOf a LastIndexOf  
 Můžete použít metodu **String. IndexOf** k určení pozice prvního výskytu určitého znaku v řetězci. Tato metoda rozlišování velkých a malých písmen začíná počítat od začátku řetězce a vrací pozici předaného znaku pomocí indexu založeného na nule. Pokud znak nelze nalézt, je vrácena hodnota – 1.  
  
 Následující příklad používá metodu **IndexOf** k hledání prvního výskytu `l` znaku v řetězci.  
  
 [!code-cpp[Conceptual.String.BasicOps#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#13)]
 [!code-csharp[Conceptual.String.BasicOps#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#13)]
 [!code-vb[Conceptual.String.BasicOps#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#13)]  
  
 Tento příklad `2` se zobrazí v konzole nástroje.  
  
 Metoda **String. LastIndexOf** je podobná metodě **String. IndexOf** s tím rozdílem, že vrátí pozici posledního výskytu určitého znaku v řetězci. Rozlišuje velká a malá písmena a používá index založený na nule.  
  
 Následující příklad používá metodu **LastIndexOf** k hledání posledního výskytu `l` znaku v řetězci.  
  
 [!code-cpp[Conceptual.String.BasicOps#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#14)]
 [!code-csharp[Conceptual.String.BasicOps#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#14)]
 [!code-vb[Conceptual.String.BasicOps#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#14)]  
  
 Tento příklad `9` se zobrazí v konzole nástroje.  
  
 Obě metody jsou užitečné při použití ve spojení s metodou **String. Remove** . Můžete použít buď metody **IndexOf** nebo **LastIndexOf** k načtení pozice znaku, a pak zadáním této pozice do metody **Remove** odebrat znak nebo slovo, které začíná tímto znakem.  
  
## <a name="see-also"></a>Viz také

- [Základní operace s řetězci](basic-string-operations.md)
- [Provádění řetězcových operací nezávislých na jazykové verzi](../globalization-localization/performing-culture-insensitive-string-operations.md)
- [Řazení tabulek váhy (pro .NET ve Windows)](https://www.microsoft.com/download/details.aspx?id=10921)
- [Výchozí tabulka prvků kolace Unicode (pro .NET Core v systémech Linux a macOS)](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
