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
ms.openlocfilehash: 91996bc721db55b24521be97e4d9accd53ef7924
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288612"
---
# <a name="performing-culture-insensitive-string-comparisons"></a>Provádění porovnávání řetězců nezávislých na jazykové verzi
Ve výchozím nastavení tato <xref:System.String.Compare%2A?displayProperty=nameWithType> metoda provádí porovnání zohledňující jazykovou verzi a rozlišuje velká a malá písmena. Tato metoda také obsahuje několik přetížení, která poskytují `culture` parametr, který umožňuje určit jazykovou verzi, která se má použít, a `comparisonType` parametr, který umožňuje zadat pravidla porovnávání, která chcete použít. Volání těchto metod namísto výchozího přetížení odstraní jakoukoli nejednoznačnost týkající se pravidel používaných při volání konkrétní metody a objasňuje, zda je konkrétní porovnání závislé na jazykové verzi či nikoli.  
  
> [!NOTE]
> Obě přetížení <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody provádějí porovnání zohledňující jazykovou verzi a rozlišování velkých a malých písmen; tuto metodu nelze použít pro porovnání nezávislé na jazykové verzi. Pro přehlednost kódu doporučujeme <xref:System.String.Compare%2A?displayProperty=nameWithType> místo toho použít metodu.  
  
 V případě operací závislých na jazykové verzi <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> Zadejte <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> hodnotu výčtu nebo jako `comparisonType` parametr. Chcete-li provést porovnání zohledňující jazykovou verzi pomocí určené kultury jiné než aktuální jazykové verze, určete <xref:System.Globalization.CultureInfo> objekt, který představuje tuto jazykovou verzi jako `culture` parametr.  
  
 Porovnávání řetězců nezávislé na jazykové verzi, které metoda podporuje, <xref:System.String.Compare%2A?displayProperty=nameWithType> je jazyk (založený na konvencích řazení neutrální jazykové verze) nebo nelingvisted (na základě pořadových hodnot znaků v řetězci). Většina porovnání řetězců nezávislých na jazykové verzi je nejazykových. Pro tato porovnání zadejte <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> hodnotu výčtu nebo jako `comparisonType` parametr. Pokud je například bezpečnostní rozhodnutí (jako je porovnání uživatelského jména a hesla) založeno na výsledku porovnání řetězců, operace by měla být nezávislá na jazykové verzi a jazyce, aby výsledek nemohl být ovlivněn konvencemi konkrétní jazykové verze nebo jazyka.  
  
 Pokud chcete zpracovávat jazykově odpovídající řetězce z několika jazykových verzí konzistentním způsobem, použijte porovnání lingvistických řetězců nezávislé na jazykové verzi. Jestliže vaše aplikace zobrazuje například slova, která používají více znakových sad v seznamu, budete pravděpodobně chtít zobrazit slova ve stejném pořadí bez ohledu na aktuální jazykovou verzi. Pro jazyková porovnání nezávislá na jazykových verzích definuje rozhraní .NET Framework neutrální jazykovou verzi, která bude založena na jazykových konvencích angličtiny. Chcete-li provést jazykové porovnání nezávislé na jazykové verzi, zadejte <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> nebo <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType> jako `comparisonType` parametr.  
  
 Následující příklad provádí dvě nejazyková porovnání řetězců nezávislá na jazykové verzi. V prvním porovnání se rozlišují velká a malá písmena, ve druhém nikoli.  
  
 [!code-csharp[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/cs/cultureinsensitive1.cs#1)]
 [!code-vb[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/vb/cultureinsensitive1.vb#1)]  

Můžete stáhnout tabulky [váhy řazení](https://www.microsoft.com/download/details.aspx?id=10921), sadu textových souborů, které obsahují informace o váhu znaků používaných při řazení a porovnávání operací pro operační systémy Windows, a [výchozí tabulku prvků kolace sady Unicode](https://www.unicode.org/Public/UCA/latest/allkeys.txt)pro systém Linux a MacOS.

## <a name="see-also"></a>Viz také

- <xref:System.String.Compare%2A?displayProperty=nameWithType>
- <xref:System.String.CompareTo%2A?displayProperty=nameWithType>
- [Provádění řetězcových operací nezávislých na jazykové verzi](performing-culture-insensitive-string-operations.md)
- [Osvědčené postupy pro používání řetězců](../base-types/best-practices-strings.md)
