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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84b1c10b655fefcd420a0c3cf038dba00e688d3e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43461654"
---
# <a name="performing-culture-insensitive-string-comparisons"></a>Provádění porovnávání řetězců nezávislých na jazykové verzi
Ve výchozím nastavení <xref:System.String.Compare%2A?displayProperty=nameWithType> metoda provádí porovnání citlivé na jazykovou verzi a malá a velká písmena. Tato metoda zahrnuje také několik přetížení, které poskytují `culture` parametr, který umožňuje zadat jazykovou verzi, pokud chcete použít, a `comparisonType` parametr, který umožňuje určit použitá pravidla porovnávání. Volání těchto metod namísto výchozího přetížení odstraní jakoukoli nejednoznačnost týkající se pravidel používaných při volání konkrétní metody a objasňuje, zda je konkrétní porovnání závislé na jazykové verzi či nikoli.  
  
> [!NOTE]
>  Obě přetížení <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metoda provést porovnání citlivé na jazykovou verzi a malá a velká písmena; tuto metodu nelze použít k provádění porovnání nezávislá na jazykové verzi. Přehlednosti kódu doporučujeme použít <xref:System.String.Compare%2A?displayProperty=nameWithType> metoda místo.  
  
 Operace zohledňující jazykovou verzi, zadejte <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> nebo <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> hodnotu výčtu, jako `comparisonType` parametru. Pokud chcete provést porovnání citlivé na jazykovou verzi pomocí jiné určené jazykové verze než aktuální jazykovou verzi, zadejte <xref:System.Globalization.CultureInfo> objekt, který představuje tuto jazykovou verzi jako `culture` parametru.  
  
 Porovnání řetězců nezávislá na jazykové verzi, podporuje <xref:System.String.Compare%2A?displayProperty=nameWithType> jsou buď jazyková (založená na konvencích řazení invariantní jazyková verze) nebo nejazyková (založená na pořadovém čísle znaků v řetězci). Většina porovnání řetězců nezávislých na jazykové verzi je nejazykových. Pro tato porovnání zadejte <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> nebo <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> hodnotu výčtu, jako `comparisonType` parametru. Pokud je například bezpečnostní rozhodnutí (jako je porovnání uživatelského jména a hesla) založeno na výsledku porovnání řetězců, operace by měla být nezávislá na jazykové verzi a jazyce, aby výsledek nemohl být ovlivněn konvencemi konkrétní jazykové verze nebo jazyka.  
  
 Pokud chcete zpracovávat jazykově odpovídající řetězce z několika jazykových verzí konzistentním způsobem, použijte porovnání lingvistických řetězců nezávislé na jazykové verzi. Jestliže vaše aplikace zobrazuje například slova, která používají více znakových sad v seznamu, budete pravděpodobně chtít zobrazit slova ve stejném pořadí bez ohledu na aktuální jazykovou verzi. Pro jazyková porovnání nezávislá na jazykových verzích definuje rozhraní .NET Framework neutrální jazykovou verzi, která bude založena na jazykových konvencích angličtiny. Chcete-li provést jazykové porovnání nezávislé na jazykové verzi, zadejte <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> nebo <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType> jako `comparisonType` parametru.  
  
 Následující příklad provádí dvě nejazyková porovnání řetězců nezávislá na jazykové verzi. V prvním porovnání se rozlišují velká a malá písmena, ve druhém nikoli.  
  
 [!code-csharp[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/cs/cultureinsensitive1.cs#1)]
 [!code-vb[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/vb/cultureinsensitive1.vb#1)]  

Můžete stáhnout [řazení váhy tabulky](https://www.microsoft.com/en-us/download/details.aspx?id=10921), sadu textové soubory, které obsahují informace o tom váhy znaků použitých v operacích řazení a porovnávání pro operační systémy Windows.

## <a name="see-also"></a>Viz také:

- <xref:System.String.Compare%2A?displayProperty=nameWithType>  
- <xref:System.String.CompareTo%2A?displayProperty=nameWithType>  
- [Provádění řetězcových operací nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)  
- [Doporučené postupy pro používání řetězců](../../../docs/standard/base-types/best-practices-strings.md)
