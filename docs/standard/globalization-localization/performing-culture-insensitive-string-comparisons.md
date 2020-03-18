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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73120837"
---
# <a name="performing-culture-insensitive-string-comparisons"></a>Provádění porovnávání řetězců nezávislých na jazykové verzi
Ve výchozím <xref:System.String.Compare%2A?displayProperty=nameWithType> nastavení metoda provádí porovnání rozlišující jazykovou verzi a malá a velká písmena. Tato metoda také zahrnuje několik `culture` přetížení, které poskytují parametr, který umožňuje `comparisonType` určit jazykovou verzi, která má být používána, a parametr, který umožňuje zadat pravidla porovnání, která se mají použít. Volání těchto metod namísto výchozího přetížení odstraní jakoukoli nejednoznačnost týkající se pravidel používaných při volání konkrétní metody a objasňuje, zda je konkrétní porovnání závislé na jazykové verzi či nikoli.  
  
> [!NOTE]
> Obě přetížení <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody provádět porovnání zjiskřit jazykovou metodou a malá a velká písmena porovnání; Tuto metodu nelze použít k porovnání necitlivé ho jazykové verze. Pro přehlednost kódu doporučujeme <xref:System.String.Compare%2A?displayProperty=nameWithType> použít metodu místo.  
  
 Pro operace citlivé na <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> jazykovou verzi zadejte hodnotu nebo <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> výčtu `comparisonType` jako parametr. Pokud chcete provést porovnání citlivé na jazykovou verzi pomocí určené jazykové <xref:System.Globalization.CultureInfo> verze než aktuální `culture` jazykové verze, zadejte objekt, který představuje tuto jazykovou verzi jako parametr.  
  
 Porovnání řetězců necitlivých na jazykovou <xref:System.String.Compare%2A?displayProperty=nameWithType> verzi podporovaná metodou jsou buď jazykové (založené na konvencích řazení invariantní jazykové verze) nebo nejazykové (na základě ordinální hodnoty znaků v řetězci). Většina porovnání řetězců nezávislých na jazykové verzi je nejazykových. Pro tato porovnání zadejte hodnotu <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> nebo <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> `comparisonType` výčtu jako parametr. Pokud je například bezpečnostní rozhodnutí (jako je porovnání uživatelského jména a hesla) založeno na výsledku porovnání řetězců, operace by měla být nezávislá na jazykové verzi a jazyce, aby výsledek nemohl být ovlivněn konvencemi konkrétní jazykové verze nebo jazyka.  
  
 Pokud chcete zpracovávat jazykově odpovídající řetězce z několika jazykových verzí konzistentním způsobem, použijte porovnání lingvistických řetězců nezávislé na jazykové verzi. Jestliže vaše aplikace zobrazuje například slova, která používají více znakových sad v seznamu, budete pravděpodobně chtít zobrazit slova ve stejném pořadí bez ohledu na aktuální jazykovou verzi. Pro jazyková porovnání nezávislá na jazykových verzích definuje rozhraní .NET Framework neutrální jazykovou verzi, která bude založena na jazykových konvencích angličtiny. Chcete-li provést jazykové porovnání necitlivé <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType> na `comparisonType` jazykové verzi, zadejte <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> nebo jako parametr.  
  
 Následující příklad provádí dvě nejazyková porovnání řetězců nezávislá na jazykové verzi. V prvním porovnání se rozlišují velká a malá písmena, ve druhém nikoli.  
  
 [!code-csharp[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/cs/cultureinsensitive1.cs#1)]
 [!code-vb[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/vb/cultureinsensitive1.vb#1)]  

Můžete si stáhnout [tabulku tloušťky řazení](https://www.microsoft.com/download/details.aspx?id=10921), sadu textových souborů, které obsahují informace o hmotnosti znaků používané při řazení a porovnávání operací pro operační systémy Windows, a [výchozí tabulku prvků řazení Unicode](https://www.unicode.org/Public/UCA/latest/allkeys.txt), tabulku hmotnosti řazení pro Linux a macOS.

## <a name="see-also"></a>Viz také

- <xref:System.String.Compare%2A?displayProperty=nameWithType>
- <xref:System.String.CompareTo%2A?displayProperty=nameWithType>
- [Provádění řetězcových operací nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- [Doporučené postupy pro používání řetězců](../../../docs/standard/base-types/best-practices-strings.md)
