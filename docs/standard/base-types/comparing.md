---
title: Porovnání řetězců v rozhraní .NET
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73101674"
---
# <a name="comparing-strings-in-net"></a>Porovnání řetězců v rozhraní .NET
Rozhraní .NET poskytuje několik metod pro porovnání hodnot řetězců. V následující tabulce jsou uvedeny a popsány metody porovnání hodnot.  
  
|Název metody|Použití|  
|-----------------|---------|  
|<xref:System.String.Compare%2A?displayProperty=nameWithType>|Porovná hodnoty dvou řetězců. Vrátí hodnotu celéčíslo.|  
|<xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType>|Porovná dva řetězce bez ohledu na místní jazykovou verzi. Vrátí hodnotu celéčíslo.|  
|<xref:System.String.CompareTo%2A?displayProperty=nameWithType>|Porovná aktuální objekt řetězce s jiným řetězcem. Vrátí hodnotu celéčíslo.|  
|<xref:System.String.StartsWith%2A?displayProperty=nameWithType>|Určuje, zda řetězec začíná předaným řetězcem. Vrátí logickou hodnotu.|  
|<xref:System.String.EndsWith%2A?displayProperty=nameWithType>|Určuje, zda řetězec končí předaným řetězcem. Vrátí logickou hodnotu.|  
|<xref:System.String.Equals%2A?displayProperty=nameWithType>|Určuje, zda jsou dva řetězce stejné. Vrátí logickou hodnotu.|  
|<xref:System.String.IndexOf%2A?displayProperty=nameWithType>|Vrátí pozici indexu znaku nebo řetězce počínaje začátkem řetězce, který zkoumáte. Vrátí hodnotu celéčíslo.|  
|<xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>|Vrátí pozici indexu znaku nebo řetězce počínaje koncem řetězce, který zkoumáte. Vrátí hodnotu celéčíslo.|  
  
## <a name="compare"></a>Porovnání  
 Statická <xref:System.String.Compare%2A?displayProperty=nameWithType> metoda poskytuje důkladný způsob porovnání dvou řetězců. Tato metoda je kulturně vědom. Tuto funkci můžete použít k porovnání dvou řetězců nebo podřetězců dvou řetězců. Navíc přetížení jsou poskytovány, že ohledem nebo ignorovat případ a kulturní odchylky. V následující tabulce jsou uvedeny tři celé hodnoty, které by tato metoda mohla vrátit.  
  
|Návratová hodnota|Podmínka|  
|------------------|---------------|  
|Záporné celé číslo|První řetězec předchází druhý řetězec v pořadí řazení.<br /><br /> -nebo-<br /><br /> První řetězec `null`je .|  
|0|První řetězec a druhý řetězec jsou stejné.<br /><br /> -nebo-<br /><br /> Oba řetězce `null`jsou .|  
|Kladné celé číslo<br /><br /> -nebo-<br /><br /> 1|První řetězec následuje druhý řetězec v pořadí řazení.<br /><br /> -nebo-<br /><br /> Druhý řetězec `null`je .|  
  
> [!IMPORTANT]
> Metoda <xref:System.String.Compare%2A?displayProperty=nameWithType> je primárně určena pro použití při řazení nebo řazení řetězců. Neměli byste <xref:System.String.Compare%2A?displayProperty=nameWithType> použít metodu k testování rovnosti (to znamená explicitně hledat vrácenou hodnotu 0 bez ohledu na to, zda jeden řetězec je menší nebo větší než ostatní). Místo toho chcete-li zjistit, zda <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> jsou dva řetězce stejné, použijte metodu.  
  
 Následující příklad používá <xref:System.String.Compare%2A?displayProperty=nameWithType> metodu k určení relativníhodnoty dvou řetězců.  
  
 [!code-cpp[Conceptual.String.BasicOps#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#6)]
 [!code-csharp[Conceptual.String.BasicOps#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#6)]
 [!code-vb[Conceptual.String.BasicOps#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#6)]  
  
 Tento příklad `-1` se zobrazí do konzoly.  
  
 Předchozí příklad je ve výchozím nastavení citlivý na jazykovou verzi. Chcete-li provést porovnání řetězců necitlivé na <xref:System.String.Compare%2A?displayProperty=nameWithType> jazykové verzi, použijte přetížení metody, která umožňuje určit jazykovou verzi, která má být používána, zadáním parametru *jazykové verze.* Příklad, který ukazuje, jak <xref:System.String.Compare%2A?displayProperty=nameWithType> použít metodu k provedení porovnání necitlivé jazykové verze, naleznete v tématu provádění porovnání [řetězců necitlivé jazykovou verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md).  
  
## <a name="compareordinal"></a>PorovnáníOrdinální  
 Metoda <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> porovnává dva objekty řetězce bez ohledu na místní jazykovou verzi. Vrácené hodnoty této metody jsou shodné s hodnotami vrácenými metodou **Compare** v předchozí tabulce.  
  
> [!IMPORTANT]
> Metoda <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> je primárně určena pro použití při řazení nebo řazení řetězců. Neměli byste <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> použít metodu k testování rovnosti (to znamená explicitně hledat vrácenou hodnotu 0 bez ohledu na to, zda jeden řetězec je menší nebo větší než ostatní). Místo toho chcete-li zjistit, zda <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> jsou dva řetězce stejné, použijte metodu.  
  
 Následující příklad používá **CompareOrdinal** metoda porovnat hodnoty dvou řetězců.  
  
 [!code-cpp[Conceptual.String.BasicOps#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#7)]
 [!code-csharp[Conceptual.String.BasicOps#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#7)]
 [!code-vb[Conceptual.String.BasicOps#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#7)]  
  
 Tento příklad `-32` se zobrazí do konzoly.  
  
## <a name="compareto"></a>Compareto  
 Metoda <xref:System.String.CompareTo%2A?displayProperty=nameWithType> porovná řetězec, který aktuální objekt řetězce zapouzdřuje s jiným řetězcem nebo objektem. Vrácené hodnoty této metody jsou shodné <xref:System.String.Compare%2A?displayProperty=nameWithType> s hodnotami vrácenými metodou v předchozí tabulce.  
  
> [!IMPORTANT]
> Metoda <xref:System.String.CompareTo%2A?displayProperty=nameWithType> je primárně určena pro použití při řazení nebo řazení řetězců. Neměli byste <xref:System.String.CompareTo%2A?displayProperty=nameWithType> použít metodu k testování rovnosti (to znamená explicitně hledat vrácenou hodnotu 0 bez ohledu na to, zda jeden řetězec je menší nebo větší než ostatní). Místo toho chcete-li zjistit, zda <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> jsou dva řetězce stejné, použijte metodu.  
  
 Následující příklad používá <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metodu `string1` k porovnání `string2` objektu s objektem.  
  
 [!code-cpp[Conceptual.String.BasicOps#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#8)]
 [!code-csharp[Conceptual.String.BasicOps#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#8)]
 [!code-vb[Conceptual.String.BasicOps#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#8)]  
  
 Tento příklad `-1` se zobrazí do konzoly.  
  
 Všechna přetížení <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody provádět porovnání rozlišující jazykovou verzi a malá a velká písmena ve výchozím nastavení. Nejsou k dispozici žádné přetížení této metody, které umožňují provádět porovnání necitlivé jazykovou verzi. Pro přehlednost kódu doporučujeme použít **String.Compare** metoda <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> místo, určení pro <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> operace citlivé na jazykovou verzi nebo pro operace necitlivé na jazykové verzi. Příklady, které ukazují, jak použít **String.Compare** metoda provádět porovnání citlivé na jazykovou verzi a jazykovou verzi necitlivé, naleznete [v tématu provádění porovnání řetězců necitlivé na jazykovou verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md).  
  
## <a name="equals"></a>Rovná se  
 **String.Equals** Metoda lze snadno určit, pokud dva řetězce jsou stejné. Tato metoda rozlišující malá a velká písmena vrátí **hodnotu true** nebo **false** Boolean. Lze jej použít z existující třídy, jak je znázorněno v následujícím příkladu. Následující příklad používá **Metodu Equals** k určení, zda objekt řetězce obsahuje frázi "Hello World".  
  
 [!code-cpp[Conceptual.String.BasicOps#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#9)]
 [!code-csharp[Conceptual.String.BasicOps#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#9)]
 [!code-vb[Conceptual.String.BasicOps#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#9)]  
  
 Tento příklad `True` se zobrazí do konzoly.  
  
 Tuto metodu lze také použít jako statickou metodu. Následující příklad porovnává dva objekty řetězce pomocí statické metody.  
  
 [!code-cpp[Conceptual.String.BasicOps#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#10)]
 [!code-csharp[Conceptual.String.BasicOps#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#10)]
 [!code-vb[Conceptual.String.BasicOps#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#10)]  
  
 Tento příklad `True` se zobrazí do konzoly.  
  
## <a name="startswith-and-endswith"></a>StartsWith a endsWith  
 Metodu **String.StartsWith** můžete použít k určení, zda objekt řetězce začíná stejnými znaky, které zahrnují jiný řetězec. Tato metoda rozlišující malá a velká písmena vrátí **hodnotu true,** pokud aktuální objekt řetězce začíná předaným řetězcem a **false,** pokud tomu tak není. Následující příklad používá tuto metodu k určení, pokud objekt řetězce začíná "Hello".  
  
 [!code-cpp[Conceptual.String.BasicOps#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#11)]
 [!code-csharp[Conceptual.String.BasicOps#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#11)]
 [!code-vb[Conceptual.String.BasicOps#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#11)]  
  
 Tento příklad `True` se zobrazí do konzoly.  
  
 Metoda **String.EndsWith** porovnává předávaný řetězec se znaky, které existují na konci aktuálního objektu řetězce. Vrátí také logickou hodnotu. Následující příklad zkontroluje konec řetězce pomocí **EndsWith** metody.  
  
 [!code-cpp[Conceptual.String.BasicOps#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#12)]
 [!code-csharp[Conceptual.String.BasicOps#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#12)]
 [!code-vb[Conceptual.String.BasicOps#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#12)]  
  
 Tento příklad `False` se zobrazí do konzoly.  
  
## <a name="indexof-and-lastindexof"></a>IndexOf a LastIndexOf  
 Metodu **String.IndexOf** můžete použít k určení pozice prvního výskytu určitého znaku v řetězci. Tato metoda rozlišující malá a velká písmena začíná počítat od začátku řetězce a vrací pozici předaného znaku pomocí indexu založeného na nule. Pokud znak nelze nalézt, je vrácena hodnota -1.  
  
 Následující příklad používá metodu **IndexOf** k vyhledání`l`prvního výskytu znaku ' v řetězci.  
  
 [!code-cpp[Conceptual.String.BasicOps#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#13)]
 [!code-csharp[Conceptual.String.BasicOps#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#13)]
 [!code-vb[Conceptual.String.BasicOps#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#13)]  
  
 Tento příklad `2` se zobrazí do konzoly.  
  
 Metoda **String.LastIndexOf** je podobná metodě **String.IndexOf** s tím rozdílem, že vrátí pozici posledního výskytu určitého znaku v řetězci. Rozlišuje malá a velká písmena a používá index založený na nule.  
  
 Následující příklad používá metodu **LastIndexOf** k vyhledání`l`posledního výskytu znaku ' v řetězci.  
  
 [!code-cpp[Conceptual.String.BasicOps#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#14)]
 [!code-csharp[Conceptual.String.BasicOps#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#14)]
 [!code-vb[Conceptual.String.BasicOps#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#14)]  
  
 Tento příklad `9` se zobrazí do konzoly.  
  
 Obě metody jsou užitečné při použití ve spojení s **String.Remove** metoda. Můžete použít buď **IndexOf** nebo **LastIndexOf** metody načíst pozici znaku a potom zadat tuto pozici **Remove** metoda k odebrání znak nebo slovo, které začíná tímto znakem.  
  
## <a name="see-also"></a>Viz také

- [Základní operace s řetězci](../../../docs/standard/base-types/basic-string-operations.md)
- [Provádění řetězcových operací nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- [Řazení tabulek hmotnosti (pro rozhraní .NET v systému Windows)](https://www.microsoft.com/download/details.aspx?id=10921)
- [Výchozí tabulka prvků řazení unicode (pro .NET Core v Linuxu a macOS)](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
