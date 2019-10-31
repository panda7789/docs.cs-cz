---
title: Provádění porovnávání řetězců nezávislých na jazykové verzi
ms.date: 08/22/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- String.CompareTo method
- String.Compare method
- string comparison [.NET Framework], culture-insensitive
- strings [.NET Framework], comparing
- culture-insensitive string operations, comparisons
- culture parameter
ms.assetid: abae50ef-32f7-4a50-a540-fd256fd1aed0
ms.openlocfilehash: 85ba91b63ab0edbccc768e2d1ad4aaef31fd2f21
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120837"
---
# <a name="performing-culture-insensitive-string-comparisons"></a>Provádění porovnávání řetězců nezávislých na jazykové verzi
Ve výchozím nastavení provádí metoda <xref:System.String.Compare%2A?displayProperty=nameWithType> porovnávání zohledňující jazykovou verzi a rozlišuje velká a malá písmena. Tato metoda také obsahuje několik přetížení, která poskytují parametr `culture`, který umožňuje určit jazykovou verzi, která se má použít, a parametr `comparisonType`, který umožňuje určit pravidla porovnávání, která se mají použít. Volání těchto metod namísto výchozího přetížení odstraní jakoukoli nejednoznačnost týkající se pravidel používaných při volání konkrétní metody a objasňuje, zda je konkrétní porovnání závislé na jazykové verzi či nikoli.  
  
> [!NOTE]
> Obě přetížení metody <xref:System.String.CompareTo%2A?displayProperty=nameWithType> provádějí porovnání zohledňující jazykovou verzi a rozlišování velkých a malých písmen; tuto metodu nelze použít pro porovnání nezávisle na jazykové verzi. Pro přehlednost kódu doporučujeme místo toho použít metodu <xref:System.String.Compare%2A?displayProperty=nameWithType>.  
  
 V případě operací závislých na jazykové verzi zadejte hodnotu výčtu <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> nebo <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> jako parametr `comparisonType`. Chcete-li provést porovnání zohledňující jazykovou verzi pomocí určené kultury jiné než aktuální jazykové verze, určete <xref:System.Globalization.CultureInfo> objekt, který představuje tuto jazykovou verzi jako parametr `culture`.  
  
 Porovnávání řetězců nezávislé na jazykové verzi podporované metodou <xref:System.String.Compare%2A?displayProperty=nameWithType> je jazyk (založený na konvencích řazení neutrální jazykové verze) nebo nelingvisted (na základě pořadových hodnot znaků v řetězci). Většina porovnání řetězců nezávislých na jazykové verzi je nejazykových. Pro tato porovnání zadejte hodnotu výčtu <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> nebo <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> jako parametr `comparisonType`. Pokud je například bezpečnostní rozhodnutí (jako je porovnání uživatelského jména a hesla) založeno na výsledku porovnání řetězců, operace by měla být nezávislá na jazykové verzi a jazyce, aby výsledek nemohl být ovlivněn konvencemi konkrétní jazykové verze nebo jazyka.  
  
 Pokud chcete zpracovávat jazykově odpovídající řetězce z několika jazykových verzí konzistentním způsobem, použijte porovnání lingvistických řetězců nezávislé na jazykové verzi. Jestliže vaše aplikace zobrazuje například slova, která používají více znakových sad v seznamu, budete pravděpodobně chtít zobrazit slova ve stejném pořadí bez ohledu na aktuální jazykovou verzi. Pro jazyková porovnání nezávislá na jazykových verzích definuje rozhraní .NET Framework neutrální jazykovou verzi, která bude založena na jazykových konvencích angličtiny. Chcete-li provést jazykové porovnání nezávislé na jazykové verzi, zadejte jako parametr `comparisonType` <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> nebo <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType>.  
  
 Následující příklad provádí dvě nejazyková porovnání řetězců nezávislá na jazykové verzi. V prvním porovnání se rozlišují velká a malá písmena, ve druhém nikoli.  
  
 [!code-csharp[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/cs/cultureinsensitive1.cs#1)]
 [!code-vb[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/vb/cultureinsensitive1.vb#1)]  

Můžete si stáhnout [tabulky váhy řazení](https://www.microsoft.com/download/details.aspx?id=10921), sadu textových souborů, které obsahují informace o váhu znaků používaných při řazení a porovnávání operací pro operační systémy Windows, a [výchozí tabulku prvků kolace sady Unicode](https://www.unicode.org/Public/UCA/latest/allkeys.txt), řazení Tabulka váhy pro Linux a macOS.

## <a name="see-also"></a>Viz také:

- <xref:System.String.Compare%2A?displayProperty=nameWithType>
- <xref:System.String.CompareTo%2A?displayProperty=nameWithType>
- [Provádění řetězcových operací nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- [Doporučené postupy pro používání řetězců](../../../docs/standard/base-types/best-practices-strings.md)
