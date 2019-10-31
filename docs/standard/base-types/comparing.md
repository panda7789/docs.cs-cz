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
ms.openlocfilehash: e63b2a8ac44d6171f9c48990882780ea420f8c76
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73101674"
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
  
## <a name="compare"></a>Porovnán  
 Metoda static <xref:System.String.Compare%2A?displayProperty=nameWithType> poskytuje důkladný způsob porovnávání dvou řetězců. Tato metoda je kulturně zavědoma. Tuto funkci můžete použít k porovnání dvou řetězců nebo podřetězců dvou řetězců. Navíc jsou k dispozici přetížení, která se týkají nebo netýkají případu a kulturní odchylky. Následující tabulka uvádí tři celočíselné hodnoty, které může tato metoda vracet.  
  
|Návratová hodnota|Podmínka|  
|------------------|---------------|  
|Záporné celé číslo|První řetězec předchází druhému řetězci v pořadí řazení.<br /><br /> -nebo-<br /><br /> První řetězec je `null`.|  
|0,8|První řetězec a druhý řetězec jsou stejné.<br /><br /> -nebo-<br /><br /> Oba řetězce jsou `null`.|  
|Kladné celé číslo<br /><br /> -nebo-<br /><br /> první|První řetězec následuje za druhým řetězcem v pořadí řazení.<br /><br /> -nebo-<br /><br /> Druhý řetězec je `null`.|  
  
> [!IMPORTANT]
> Metoda <xref:System.String.Compare%2A?displayProperty=nameWithType> je primárně určena pro použití při řazení nebo řazení řetězců. Nepoužívejte metodu <xref:System.String.Compare%2A?displayProperty=nameWithType> k otestování rovnosti (to znamená pro explicitní vyhledání návratové hodnoty 0 bez ohledu na to, zda je jeden řetězec menší nebo větší než druhý). Místo toho pro určení, zda jsou dva řetězce stejné, použijte metodu <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType>.  
  
 Následující příklad používá metodu <xref:System.String.Compare%2A?displayProperty=nameWithType> k určení relativních hodnot dvou řetězců.  
  
 [!code-cpp[Conceptual.String.BasicOps#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#6)]
 [!code-csharp[Conceptual.String.BasicOps#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#6)]
 [!code-vb[Conceptual.String.BasicOps#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#6)]  
  
 Tento příklad zobrazuje `-1` do konzoly.  
  
 V předchozím příkladu je standardně závislá na jazykové verzi. Chcete-li provést porovnání řetězců nezávisle na jazykové verzi, použijte přetížení metody <xref:System.String.Compare%2A?displayProperty=nameWithType>, která umožňuje zadat jazykovou verzi, kterou chcete použít, zadáním parametru *jazykové verze* . Příklad, který ukazuje, jak použít metodu <xref:System.String.Compare%2A?displayProperty=nameWithType> k provedení porovnání nezávisle na jazykové verzi, naleznete v tématu [provádění porovnávání řetězců nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md).  
  
## <a name="compareordinal"></a>CompareOrdinal  
 Metoda <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> Porovná dva řetězcové objekty bez zvážení místní kultury. Návratové hodnoty této metody jsou shodné s hodnotami vrácenými metodou **Compare** v předchozí tabulce.  
  
> [!IMPORTANT]
> Metoda <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> je primárně určena pro použití při řazení nebo řazení řetězců. Nepoužívejte metodu <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> k otestování rovnosti (to znamená pro explicitní vyhledání návratové hodnoty 0 bez ohledu na to, zda je jeden řetězec menší nebo větší než druhý). Místo toho pro určení, zda jsou dva řetězce stejné, použijte metodu <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType>.  
  
 Následující příklad používá metodu **CompareOrdinal** pro porovnání hodnot dvou řetězců.  
  
 [!code-cpp[Conceptual.String.BasicOps#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#7)]
 [!code-csharp[Conceptual.String.BasicOps#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#7)]
 [!code-vb[Conceptual.String.BasicOps#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#7)]  
  
 Tento příklad zobrazuje `-32` do konzoly.  
  
## <a name="compareto"></a>CompareTo  
 Metoda <xref:System.String.CompareTo%2A?displayProperty=nameWithType> porovná řetězec, který je aktuálním objektem řetězce zapouzdřený do jiného řetězce nebo objektu. Návratové hodnoty této metody jsou shodné s hodnotami vrácenými metodou <xref:System.String.Compare%2A?displayProperty=nameWithType> v předchozí tabulce.  
  
> [!IMPORTANT]
> Metoda <xref:System.String.CompareTo%2A?displayProperty=nameWithType> je primárně určena pro použití při řazení nebo řazení řetězců. Nepoužívejte metodu <xref:System.String.CompareTo%2A?displayProperty=nameWithType> k otestování rovnosti (to znamená pro explicitní vyhledání návratové hodnoty 0 bez ohledu na to, zda je jeden řetězec menší nebo větší než druhý). Místo toho pro určení, zda jsou dva řetězce stejné, použijte metodu <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType>.  
  
 Následující příklad používá metodu <xref:System.String.CompareTo%2A?displayProperty=nameWithType> pro porovnání objektu `string1` s objektem `string2`.  
  
 [!code-cpp[Conceptual.String.BasicOps#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#8)]
 [!code-csharp[Conceptual.String.BasicOps#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#8)]
 [!code-vb[Conceptual.String.BasicOps#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#8)]  
  
 Tento příklad zobrazuje `-1` do konzoly.  
  
 Všechna přetížení metody <xref:System.String.CompareTo%2A?displayProperty=nameWithType> provádějí porovnání zohledňující jazykovou verzi a rozlišování velkých a malých písmen ve výchozím nastavení. Žádná přetížení této metody nejsou k dispozici, aby bylo možné provádět porovnání nezávislé na jazykové verzi. Pro přehlednost kódu doporučujeme místo toho použít metodu **String. Compare** a zadat <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> pro operace závislé na jazykové verzi nebo <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> pro operace nezávislé na jazykové verzi. Příklady, které ukazují, jak použít metodu **String. Compare** k provedení porovnávání závislých na jazykové verzi a nezávisle na jazykové verzi, naleznete v tématu [provádění porovnávání řetězců nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md).  
  
## <a name="equals"></a>Rovná  
 Metoda **String. Equals** umožňuje snadno určit, zda jsou dva řetězce stejné. Tato metoda rozlišování velkých a malých písmen vrátí logickou hodnotu **true** nebo **false** . Dá se použít z existující třídy, jak je znázorněno v následujícím příkladu. Následující příklad používá metodu **Equals** k určení, zda objekt řetězce obsahuje frázi "Hello World".  
  
 [!code-cpp[Conceptual.String.BasicOps#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#9)]
 [!code-csharp[Conceptual.String.BasicOps#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#9)]
 [!code-vb[Conceptual.String.BasicOps#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#9)]  
  
 Tento příklad zobrazuje `True` do konzoly.  
  
 Tuto metodu lze také použít jako statickou metodu. Následující příklad porovnává dva řetězcové objekty pomocí statické metody.  
  
 [!code-cpp[Conceptual.String.BasicOps#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#10)]
 [!code-csharp[Conceptual.String.BasicOps#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#10)]
 [!code-vb[Conceptual.String.BasicOps#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#10)]  
  
 Tento příklad zobrazuje `True` do konzoly.  
  
## <a name="startswith-and-endswith"></a>StartsWith a EndsWith  
 Můžete použít metodu **String. StartsWith** k určení, zda objekt řetězce začíná stejnými znaky, které zahrnují jiný řetězec. Tato metoda rozlišování velkých a malých písmen vrátí **hodnotu true** , pokud aktuální objekt řetězce začíná předaným řetězcem a **hodnotu false** , pokud tomu tak není. Následující příklad používá tuto metodu k určení, zda objekt řetězce začíná řetězcem "Hello".  
  
 [!code-cpp[Conceptual.String.BasicOps#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#11)]
 [!code-csharp[Conceptual.String.BasicOps#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#11)]
 [!code-vb[Conceptual.String.BasicOps#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#11)]  
  
 Tento příklad zobrazuje `True` do konzoly.  
  
 Metoda **String. EndsWith** porovná předaný řetězec znakům, které existují na konci aktuálního objektu řetězce. Vrátí také logickou hodnotu. Následující příklad zkontroluje konec řetězce pomocí metody **endsWith** .  
  
 [!code-cpp[Conceptual.String.BasicOps#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#12)]
 [!code-csharp[Conceptual.String.BasicOps#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#12)]
 [!code-vb[Conceptual.String.BasicOps#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#12)]  
  
 Tento příklad zobrazuje `False` do konzoly.  
  
## <a name="indexof-and-lastindexof"></a>IndexOf a LastIndexOf  
 Můžete použít metodu **String. IndexOf** k určení pozice prvního výskytu určitého znaku v řetězci. Tato metoda rozlišování velkých a malých písmen začíná počítat od začátku řetězce a vrací pozici předaného znaku pomocí indexu založeného na nule. Pokud znak nelze nalézt, je vrácena hodnota – 1.  
  
 Následující příklad používá metodu **IndexOf** k hledání prvního výskytu znaku '`l`' v řetězci.  
  
 [!code-cpp[Conceptual.String.BasicOps#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#13)]
 [!code-csharp[Conceptual.String.BasicOps#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#13)]
 [!code-vb[Conceptual.String.BasicOps#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#13)]  
  
 Tento příklad zobrazuje `2` do konzoly.  
  
 Metoda **String. LastIndexOf** je podobná metodě **String. IndexOf** s tím rozdílem, že vrátí pozici posledního výskytu určitého znaku v řetězci. Rozlišuje velká a malá písmena a používá index založený na nule.  
  
 Následující příklad používá metodu **LastIndexOf** k hledání posledního výskytu znaku '`l`' v řetězci.  
  
 [!code-cpp[Conceptual.String.BasicOps#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#14)]
 [!code-csharp[Conceptual.String.BasicOps#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#14)]
 [!code-vb[Conceptual.String.BasicOps#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#14)]  
  
 Tento příklad zobrazuje `9` do konzoly.  
  
 Obě metody jsou užitečné při použití ve spojení s metodou **String. Remove** . Můžete použít buď metody **IndexOf** nebo **LastIndexOf** k načtení pozice znaku, a pak zadáním této pozice do metody **Remove** odebrat znak nebo slovo, které začíná tímto znakem.  
  
## <a name="see-also"></a>Viz také:

- [Základní operace s řetězci](../../../docs/standard/base-types/basic-string-operations.md)
- [Provádění řetězcových operací nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- [Řazení tabulek váhy (pro .NET ve Windows)](https://www.microsoft.com/download/details.aspx?id=10921)
- [Výchozí tabulka prvků kolace Unicode (pro .NET Core v systémech Linux a macOS)](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
