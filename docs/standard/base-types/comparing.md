---
title: Porovnání řetězců v .NET
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 48331c1b62fa536b905f1288ebb1632f8da15615
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053594"
---
# <a name="comparing-strings-in-net"></a>Porovnání řetězců v .NET
.NET nabízí několik metod pro porovnání hodnot řetězců. Následující tabulka uvádí a popisuje metody porovnání hodnoty.  
  
|Název metody|Použití|  
|-----------------|---------|  
|<xref:System.String.Compare%2A?displayProperty=nameWithType>|Porovná dva řetězce hodnoty. Vrací celočíselnou hodnotu.|  
|<xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType>|Porovná dva řetězce bez ohledu na místní jazykové verze. Vrací celočíselnou hodnotu.|  
|<xref:System.String.CompareTo%2A?displayProperty=nameWithType>|Porovná aktuální objekt řetězce do jiného řetězce. Vrací celočíselnou hodnotu.|  
|<xref:System.String.StartsWith%2A?displayProperty=nameWithType>|Určuje, jestli řetězec začíná předal řetězec. Vrátí logickou hodnotu.|  
|<xref:System.String.EndsWith%2A?displayProperty=nameWithType>|Určuje, jestli řetězec končí řetězcem, který je předán. Vrátí logickou hodnotu.|  
|<xref:System.String.Equals%2A?displayProperty=nameWithType>|Určuje, zda jsou dva řetězce stejný. Vrátí logickou hodnotu.|  
|<xref:System.String.IndexOf%2A?displayProperty=nameWithType>|Vrátí pozici indexu znak nebo řetězec, od začátku řetězce, které se, že zkoumáte. Vrací celočíselnou hodnotu.|  
|<xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>|Vrátí pozici indexu znaků nebo řetězce, počínaje od konce řetězce, které se, že zkoumáte. Vrací celočíselnou hodnotu.|  
  
## <a name="compare"></a>Porovnat  
 Statické <xref:System.String.Compare%2A?displayProperty=nameWithType> metoda poskytuje důkladné porovnání dvou řetězců. Tato metoda je zohledňuje. Tato funkce slouží k porovnání dvou řetězců nebo dvou řetězců podřetězců. Kromě toho přetížení jsou k dispozici tomto ohledu nebo ignorovat případ a kulturní variance. V následující tabulce jsou uvedeny tři celočíselných hodnot, že tato metoda může vrátit.  
  
|Návratová hodnota|Podmínka|  
|------------------|---------------|  
|Záporné celé číslo|První řetězec, který předchází druhý řetězec v pořadí řazení.<br /><br /> -nebo-<br /><br /> První řetězec, který je `null`.|  
|0|První řetězec a druhý řetězec jsou si rovny.<br /><br /> -nebo-<br /><br /> Oba řetězce jsou `null`.|  
|Kladné celé číslo<br /><br /> -nebo-<br /><br /> 1|První řetězec, který následuje druhý řetězec v pořadí řazení.<br /><br /> -nebo-<br /><br /> Druhý řetězec je `null`.|  
  
> [!IMPORTANT]
>  <xref:System.String.Compare%2A?displayProperty=nameWithType> Metoda je primárně určena pro použití při řazení nebo řazení řetězců. Neměli byste používat <xref:System.String.Compare%2A?displayProperty=nameWithType> metody testování rovnosti (to znamená, výslovně vás pod rouškou návratovou hodnotu 0, bez ohledu na to, jestli se jeden řetězec je menší nebo větší než ten druhý). Místo toho použijte k určení, zda jsou dva řetězce stejné, <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metody.  
  
 V následujícím příkladu <xref:System.String.Compare%2A?displayProperty=nameWithType> metodou ke zjištění relativní hodnoty dvou řetězců.  
  
 [!code-cpp[Conceptual.String.BasicOps#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#6)]
 [!code-csharp[Conceptual.String.BasicOps#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#6)]
 [!code-vb[Conceptual.String.BasicOps#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#6)]  
  
 Tento příklad zobrazuje `-1` do konzoly.  
  
 V předchozím příkladu je zohledňující jazykovou verzi ve výchozím nastavení. Porovnání řetězců nezávislých na jazykové verzi, použijte přetížení <xref:System.String.Compare%2A?displayProperty=nameWithType> metodu, která vám umožní určit jazyková verze použitá zadáním *jazykovou verzi* parametr. Příklad, který ukazuje, jak používat <xref:System.String.Compare%2A?displayProperty=nameWithType> metodu za účelem porovnání nezávislá na jazykové verzi, najdete v článku [provádění porovnávání řetězců nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md).  
  
## <a name="compareordinal"></a>CompareOrdinal –  
 <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> Metoda porovná dva objekty řetězec bez zohlednění místní jazykové verze. Návratové hodnoty této metody jsou stejné jako hodnot vrácených **porovnání** metoda v předchozí tabulce.  
  
> [!IMPORTANT]
>  <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> Metoda je primárně určena pro použití při řazení nebo řazení řetězců. Neměli byste používat <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> metody testování rovnosti (to znamená, výslovně vás pod rouškou návratovou hodnotu 0, bez ohledu na to, jestli se jeden řetězec je menší nebo větší než ten druhý). Místo toho použijte k určení, zda jsou dva řetězce stejné, <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metody.  
  
 V následujícím příkladu **CompareOrdinal** metoda srovnává hodnoty dvou řetězců.  
  
 [!code-cpp[Conceptual.String.BasicOps#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#7)]
 [!code-csharp[Conceptual.String.BasicOps#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#7)]
 [!code-vb[Conceptual.String.BasicOps#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#7)]  
  
 Tento příklad zobrazuje `-32` do konzoly.  
  
## <a name="compareto"></a>CompareTo  
 <xref:System.String.CompareTo%2A?displayProperty=nameWithType> Metoda porovnává řetězce, který zapouzdřuje na aktuální objekt řetězce do jiného řetězec nebo objekt. Návratové hodnoty této metody jsou stejné jako hodnot vrácených <xref:System.String.Compare%2A?displayProperty=nameWithType> metoda v předchozí tabulce.  
  
> [!IMPORTANT]
>  <xref:System.String.CompareTo%2A?displayProperty=nameWithType> Metoda je primárně určena pro použití při řazení nebo řazení řetězců. Neměli byste používat <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody testování rovnosti (to znamená, výslovně vás pod rouškou návratovou hodnotu 0, bez ohledu na to, jestli se jeden řetězec je menší nebo větší než ten druhý). Místo toho použijte k určení, zda jsou dva řetězce stejné, <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metody.  
  
 V následujícím příkladu <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metodu porovnání `string1` objektu `string2` objektu.  
  
 [!code-cpp[Conceptual.String.BasicOps#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#8)]
 [!code-csharp[Conceptual.String.BasicOps#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#8)]
 [!code-vb[Conceptual.String.BasicOps#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#8)]  
  
 Tento příklad zobrazuje `-1` do konzoly.  
  
 Všechna přetížení <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metoda provést porovnání citlivé na jazykovou verzi a malá a velká písmena ve výchozím nastavení. Žádné přetížení této metody jsou k dispozici, které umožňují provést porovnání nezávislá na jazykové verzi. Přehlednosti kódu doporučujeme použít **String.Compare** metoda místo toho zadáte <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> pro operace zohledňující jazykovou verzi nebo <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> operací nezávislých na jazykové verzi. Příklady, které ukazují, jak používat **String.Compare** metodu za účelem porovnání zohledňující jazykovou verzi a nezávislé na jazykové verzi, najdete v článku [provádění nezávislých na jazykové verzi porovnávání řetězců](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md).  
  
## <a name="equals"></a>Je rovno  
 **String.Equals** metoda můžete snadno zjistit, zda jsou dva řetězce stejný. Vrátí tato metoda velká a malá písmena **true** nebo **false** logickou hodnotu. To je možné z existující třídy, jak je znázorněno v následujícím příkladu. V následujícím příkladu **rovná** metodou ke zjištění, zda objekt string obsahuje frázi "Hello World".  
  
 [!code-cpp[Conceptual.String.BasicOps#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#9)]
 [!code-csharp[Conceptual.String.BasicOps#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#9)]
 [!code-vb[Conceptual.String.BasicOps#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#9)]  
  
 Tento příklad zobrazuje `True` do konzoly.  
  
 Tato metoda slouží také jako statické metody. Následující příklad porovná dva objekty řetězce pomocí statické metody.  
  
 [!code-cpp[Conceptual.String.BasicOps#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#10)]
 [!code-csharp[Conceptual.String.BasicOps#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#10)]
 [!code-vb[Conceptual.String.BasicOps#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#10)]  
  
 Tento příklad zobrazuje `True` do konzoly.  
  
## <a name="startswith-and-endswith"></a>StartsWith a EndsWith  
 Můžete použít **String.StartsWith** metodou ke zjištění, zda objekt string začíná stejné znaky, které zahrnuje jiného řetězce. Vrátí tato metoda malá a velká písmena **true** Pokud aktuální objekt řetězec začíná předaný řetězec a **false** Pokud tomu tak není. Následující příklad používá tuto metodu k určení, zda objekt string začíná "Hello".  
  
 [!code-cpp[Conceptual.String.BasicOps#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#11)]
 [!code-csharp[Conceptual.String.BasicOps#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#11)]
 [!code-vb[Conceptual.String.BasicOps#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#11)]  
  
 Tento příklad zobrazuje `True` do konzoly.  
  
 **String.EndsWith** metoda srovnává předaný řetězec znaků, které existují na konci aktuálního objektu string. Také vrátí hodnotu typu Boolean. Následující příklad ověří konec řetězce pomocí **EndsWith** metody.  
  
 [!code-cpp[Conceptual.String.BasicOps#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#12)]
 [!code-csharp[Conceptual.String.BasicOps#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#12)]
 [!code-vb[Conceptual.String.BasicOps#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#12)]  
  
 Tento příklad zobrazuje `False` do konzoly.  
  
## <a name="indexof-and-lastindexof"></a>IndexOf a LastIndexOf  
 Můžete použít **String.IndexOf** metody lze určit pozici prvního výskytu určitý znak v řetězci. Tato malá a velká písmena metoda spustí, počítáno od začátku řetězce a vrátí pozici znaku předaných pomocí index založený na nule. Pokud nebyl nalezen znak, vrátí hodnotu – 1.  
  
 V následujícím příkladu **IndexOf** metody na hledání pro první výskyt "`l`" znak v řetězci.  
  
 [!code-cpp[Conceptual.String.BasicOps#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#13)]
 [!code-csharp[Conceptual.String.BasicOps#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#13)]
 [!code-vb[Conceptual.String.BasicOps#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#13)]  
  
 Tento příklad zobrazuje `2` do konzoly.  
  
 **String.LastIndexOf** metoda je podobná **String.IndexOf** metoda s výjimkou, že vrátí pozici posledního výskytu určitý znak v řetězci. Velká a malá písmena a používá index založený na nule.  
  
 V následujícím příkladu **LastIndexOf** metody na hledání pro poslední výskyt "`l`" znak v řetězci.  
  
 [!code-cpp[Conceptual.String.BasicOps#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#14)]
 [!code-csharp[Conceptual.String.BasicOps#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#14)]
 [!code-vb[Conceptual.String.BasicOps#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#14)]  
  
 Tento příklad zobrazuje `9` do konzoly.  
  
 Obě metody jsou užitečné při použití ve spojení s **String.Remove** metody. Můžete použít buď **IndexOf** nebo **LastIndexOf** metody načíst umístění znaku, a pak zadat na této pozici **odebrat** metodu, pokud chcete odebrat znaky nebo slovo, který začíná tento znak.  
  
## <a name="see-also"></a>Viz také:

- [Základní operace s řetězci](../../../docs/standard/base-types/basic-string-operations.md)
- [Provádění řetězcových operací nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- [Řazení váhy tabulky (pro .NET pro Windows)](https://www.microsoft.com/download/details.aspx?id=10921)
- [Výchozí kódování Unicode kolace Element tabulky (pro .NET Core v Linuxu a macOS)](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
