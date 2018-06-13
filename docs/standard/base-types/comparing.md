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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c925b734c6d89bfa7240a7946c5bae4d8062a47a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577814"
---
# <a name="comparing-strings-in-net"></a>Porovnávání řetězců v .NET
Rozhraní .NET poskytuje několik metod pro porovnání hodnot řetězců. Následující tabulka uvádí a popisuje metody porovnání hodnoty.  
  
|Název metody|Použití|  
|-----------------|---------|  
|<xref:System.String.Compare%2A?displayProperty=nameWithType>|Porovnává dva řetězce hodnoty. Vrací celočíselnou hodnotu.|  
|<xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType>|Porovnává dva řetězce bez ohledu na místní jazykovou verzi. Vrací celočíselnou hodnotu.|  
|<xref:System.String.CompareTo%2A?displayProperty=nameWithType>|Porovná aktuální objekt řetězce k jiným řetězcem. Vrací celočíselnou hodnotu.|  
|<xref:System.String.StartsWith%2A?displayProperty=nameWithType>|Určuje, zda řetězec začíná řetězcem předán. Vrátí logickou hodnotu.|  
|<xref:System.String.EndsWith%2A?displayProperty=nameWithType>|Určuje, zda řetězec končí řetězcem předán. Vrátí logickou hodnotu.|  
|<xref:System.String.Equals%2A?displayProperty=nameWithType>|Určuje, zda jsou dva řetězce stejné. Vrátí logickou hodnotu.|  
|<xref:System.String.IndexOf%2A?displayProperty=nameWithType>|Vrátí index umístění znaku nebo řetězec, od začátku řetězce, který je zkoumán. Vrací celočíselnou hodnotu.|  
|<xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>|Vrátí index umístění znaku nebo řetězec, od konce řetězce, který je zkoumán. Vrací celočíselnou hodnotu.|  
  
## <a name="compare"></a>Porovnat  
 Statické <xref:System.String.Compare%2A?displayProperty=nameWithType> metoda poskytuje důkladné porovnání dvou řetězců. Tato metoda je zohledňuje. Tato funkce slouží k porovnání dvou řetězců nebo dílčích řetězců dvou řetězců. Kromě toho přetížení jsou k dispozici tomto ohledu nebo ignorovat případ a kulturního odchylky. V následující tabulce jsou tři celočíselné hodnoty, tato metoda může vrátit.  
  
|Návratová hodnota|Podmínka|  
|------------------|---------------|  
|Záporné celé číslo|První řetězec předchází druhý řetězec v pořadí řazení.<br /><br /> -nebo-<br /><br /> Je první řetězec `null`.|  
|0|Řetězec, který první a druhý řetězec jsou stejné.<br /><br /> -nebo-<br /><br /> Oba řetězce jsou `null`.|  
|Kladné celé číslo<br /><br /> -nebo-<br /><br /> 1|První řetězec odpovídá druhý řetězec v pořadí řazení.<br /><br /> -nebo-<br /><br /> Druhý řetězec je `null`.|  
  
> [!IMPORTANT]
>  <xref:System.String.Compare%2A?displayProperty=nameWithType> Metoda je primárně určený pro použití při řazení nebo řazení řetězců. Neměli byste používat <xref:System.String.Compare%2A?displayProperty=nameWithType> metodu za účelem testování rovnosti (explicitně hledání vrácená hodnota 0, bez ohledu na jestli jednoho řetězce je menší než nebo je větší než druhá). Místo toho použijte k určení, zda jsou dva řetězce stejné, <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metoda.  
  
 Následující příklad používá <xref:System.String.Compare%2A?displayProperty=nameWithType> metoda, jak určit relativní hodnoty dvou řetězců.  
  
 [!code-cpp[Conceptual.String.BasicOps#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#6)]
 [!code-csharp[Conceptual.String.BasicOps#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#6)]
 [!code-vb[Conceptual.String.BasicOps#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#6)]  
  
 Tento příklad zobrazí `-1` ke konzole.  
  
 V předchozím příkladu je jazykovou ve výchozím nastavení. Chcete-li provést porovnání řetězců nezávislých na jazykové verzi, použijte přetížení <xref:System.String.Compare%2A?displayProperty=nameWithType> metoda, která umožňuje zadat jazykovou verzi pro použití zadáním *jazykovou verzi* parametr. Pro příklad, který ukazuje, jak používat <xref:System.String.Compare%2A?displayProperty=nameWithType> metodu za účelem nezávislé na jazykových porovnání najdete v tématu [provádění porovnávání řetězců nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md).  
  
## <a name="compareordinal"></a>CompareOrdinal –  
 <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> Metoda porovná dva objekty řetězce bez ohledu na místní jazykovou verzi. Návratové hodnoty této metody jsou identické s hodnotami vrácený **porovnat** metoda v předchozí tabulce.  
  
> [!IMPORTANT]
>  <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> Metoda je primárně určený pro použití při řazení nebo řazení řetězců. Neměli byste používat <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> metodu za účelem testování rovnosti (explicitně hledání vrácená hodnota 0, bez ohledu na jestli jednoho řetězce je menší než nebo je větší než druhá). Místo toho použijte k určení, zda jsou dva řetězce stejné, <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metoda.  
  
 Následující příklad používá **CompareOrdinal –** metoda pro porovnání hodnot dva řetězce.  
  
 [!code-cpp[Conceptual.String.BasicOps#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#7)]
 [!code-csharp[Conceptual.String.BasicOps#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#7)]
 [!code-vb[Conceptual.String.BasicOps#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#7)]  
  
 Tento příklad zobrazí `-32` ke konzole.  
  
## <a name="compareto"></a>CompareTo  
 <xref:System.String.CompareTo%2A?displayProperty=nameWithType> Metoda srovnává řetězec, který zapouzdřuje aktuálního objektu řetězce na jiný řetězec nebo objekt. Návratové hodnoty této metody jsou identické s hodnotami vrácený <xref:System.String.Compare%2A?displayProperty=nameWithType> metoda v předchozí tabulce.  
  
> [!IMPORTANT]
>  <xref:System.String.CompareTo%2A?displayProperty=nameWithType> Metoda je primárně určený pro použití při řazení nebo řazení řetězců. Neměli byste používat <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metodu za účelem testování rovnosti (explicitně hledání vrácená hodnota 0, bez ohledu na jestli jednoho řetězce je menší než nebo je větší než druhá). Místo toho použijte k určení, zda jsou dva řetězce stejné, <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metoda.  
  
 Následující příklad používá <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metoda k porovnání `string1` do objektu `string2` objektu.  
  
 [!code-cpp[Conceptual.String.BasicOps#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#8)]
 [!code-csharp[Conceptual.String.BasicOps#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#8)]
 [!code-vb[Conceptual.String.BasicOps#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#8)]  
  
 Tento příklad zobrazí `-1` ke konzole.  
  
 Všechny přetížení <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metoda provést porovnání zohledňující jazykovou verzi a velká a malá písmena ve výchozím nastavení. Žádné přetížení této metody jsou k dispozici, které umožňují nezávislé na jazykových porovnání. Pro přehlednost kódu, doporučujeme použít **String.Compare** metoda místo toho zadat <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> pro operace zohledňující jazykovou verzi nebo <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> pro nezávislé na jazykových operace. Příklady, které ukazují, jak používat **String.Compare** metodu za účelem porovnávání zohledňující jazykovou verzi a nezávislé na jazykových, najdete v části [provádění nezávislé na jazykových porovnání řetězců](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md).  
  
## <a name="equals"></a>Rovná se  
 **String.Equals** metoda může snadno zjistit, zda jsou dva řetězce stejné. Vrátí tato metoda velká a malá písmena **true** nebo **false** logická hodnota. Dá se použít z existující třídy, jak je znázorněno v následujícím příkladu. Následující příklad používá **rovná** metoda k určení, zda objekt řetězec obsahuje frázi "Hello World".  
  
 [!code-cpp[Conceptual.String.BasicOps#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#9)]
 [!code-csharp[Conceptual.String.BasicOps#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#9)]
 [!code-vb[Conceptual.String.BasicOps#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#9)]  
  
 Tento příklad zobrazí `True` ke konzole.  
  
 Tato metoda slouží také jako statickou metodu. Následující příklad porovná dva objekty řetězce pomocí statické metody.  
  
 [!code-cpp[Conceptual.String.BasicOps#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#10)]
 [!code-csharp[Conceptual.String.BasicOps#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#10)]
 [!code-vb[Conceptual.String.BasicOps#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#10)]  
  
 Tento příklad zobrazí `True` ke konzole.  
  
## <a name="startswith-and-endswith"></a>StartsWith a EndsWith  
 Můžete použít **String.StartsWith** metoda k určení, zda objekt string začíná stejné znaky, které zahrnuje další řetězec. Vrátí tato metoda malá a velká písmena **true** Pokud aktuální objekt řetězce začíná předaný řetězec a **false** Pokud neexistuje. Následující příklad používá tato metoda k určení, zda objekt string začíná text "Hello".  
  
 [!code-cpp[Conceptual.String.BasicOps#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#11)]
 [!code-csharp[Conceptual.String.BasicOps#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#11)]
 [!code-vb[Conceptual.String.BasicOps#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#11)]  
  
 Tento příklad zobrazí `True` ke konzole.  
  
 **String.EndsWith** metoda srovnává předaný řetězec znaků, které existují na konci aktuální objekt řetězce. Také vrací logickou hodnotu. Následující příklad zkontroluje konec řetězec pomocí **EndsWith** metoda.  
  
 [!code-cpp[Conceptual.String.BasicOps#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#12)]
 [!code-csharp[Conceptual.String.BasicOps#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#12)]
 [!code-vb[Conceptual.String.BasicOps#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#12)]  
  
 Tento příklad zobrazí `False` ke konzole.  
  
## <a name="indexof-and-lastindexof"></a>IndexOf a LastIndexOf  
 Můžete použít **String.IndexOf** metoda k určení pozice první výskyt určitého znaku v řetězci. Tato metoda malá a velká písmena spustí, počítáno od začátku řetězce a vrátí pozici předaného znaku pomocí index počítaný od nuly. Pokud nebyl nalezen znak, bude vrácena hodnota -1.  
  
 Následující příklad používá **IndexOf** metody na hledání pro první výskyt '`l`' znak v řetězci.  
  
 [!code-cpp[Conceptual.String.BasicOps#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#13)]
 [!code-csharp[Conceptual.String.BasicOps#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#13)]
 [!code-vb[Conceptual.String.BasicOps#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#13)]  
  
 Tento příklad zobrazí `2` ke konzole.  
  
 **String.LastIndexOf** metoda je podobná **String.IndexOf** s výjimkou, že metoda vrátí pozici posledního výskytu určitého znaku v řetězci. Je malá a velká písmena a používá index počítaný od nuly.  
  
 Následující příklad používá **LastIndexOf** metody na hledání pro poslední výskyt '`l`' znak v řetězci.  
  
 [!code-cpp[Conceptual.String.BasicOps#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#14)]
 [!code-csharp[Conceptual.String.BasicOps#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#14)]
 [!code-vb[Conceptual.String.BasicOps#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#14)]  
  
 Tento příklad zobrazí `9` ke konzole.  
  
 Obě metody jsou užitečné při použití ve spojení s **String.Remove** metoda. Můžete použít buď **IndexOf** nebo **LastIndexOf** metody pro načtení umístění znaku a potom předat tuto pozici k **odebrat** za účelem odebrání znak nebo slovo, které začíná tento znak.  
  
## <a name="see-also"></a>Viz také  
 [Základní operace s řetězci](../../../docs/standard/base-types/basic-string-operations.md)  
 [Provádění řetězcových operací nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
