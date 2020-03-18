---
title: Změna případu v rozhraní .NET
description: Přečtěte si, jak změnit v případě řetězců v rozhraní .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET Framework], case
- case sensitivity
- ToUpper method
- ToLower method
- uppercase
- lowercase
ms.assetid: 6805f81b-e9ad-4387-9f4c-b9bdb21b87c0
ms.openlocfilehash: 19795cbed27ca979af813b6060163e76fc5b3780
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187218"
---
# <a name="change-case-in-net"></a>Změnit případ v rozhraní .NET

Pokud napíšete aplikaci, která přijímá vstup od uživatele, nikdy si nemůžete být jisti, jaký případ (horní nebo dolní) budou používat k zadání dat. Často chcete řetězce, které mají být cased konzistentně, zejména v případě, že jsou jejich zobrazení v uživatelském rozhraní. Následující tabulka popisuje tři metody změny případu. První dvě metody poskytují přetížení, které přijímá jazykovou verzi.  
  
|Název metody|Použití|  
|-----------------|---------|  
|<xref:System.String.ToUpper%2A?displayProperty=nameWithType>|Převede všechny znaky v řetězci na velká písmena.|  
|<xref:System.String.ToLower%2A?displayProperty=nameWithType>|Převede všechny znaky v řetězci na malá písmena.|  
|<xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType>|Převede řetězec na velká a velká písmena.|  
  
> [!WARNING]
> Všimněte <xref:System.String.ToUpper%2A?displayProperty=nameWithType> si, že a <xref:System.String.ToLower%2A?displayProperty=nameWithType> metody by neměly být použity k převodu řetězců za účelem jejich porovnání nebo testování rovnosti. Další informace naleznete [v části Porovnání řetězců smíšených případů.](#Comparing)  
  
<a name="Comparing"></a>
## <a name="compare-strings-of-mixed-case"></a>Porovnat řetězce smíšených případů  

 Chcete-li porovnat řetězce smíšené případ k určení jejich řazení, <xref:System.String.CompareTo%2A?displayProperty=nameWithType> volání `comparisonType` jednoho z přetížení metody <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType>s <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType>parametrem a zadejte hodnotu buď , nebo <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> pro `comparisonType` argument. Pro porovnání pomocí konkrétní jazykové verze než aktuální jazykové <xref:System.String.CompareTo%2A?displayProperty=nameWithType> verze volání `culture` přetížení `options` metody s a <xref:System.Globalization.CompareOptions.IgnoreCase?displayProperty=nameWithType> a `options` parametr a zadejte hodnotu jako argument.  
  
 Chcete-li porovnat řetězce smíšené případ k určení, zda jsou stejné, <xref:System.String.Equals%2A?displayProperty=nameWithType> jejich, `comparisonType` volání jednoho z přetížení <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType>metody <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType>s <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> parametrem a poskytnout hodnotu , , nebo pro `comparisonType` argument.  
  
 Další informace naleznete [v tématu Doporučené postupy pro použití řetězců](../../../docs/standard/base-types/best-practices-strings.md).  
  
## <a name="toupper"></a>Toupper  
 Metoda <xref:System.String.ToUpper%2A?displayProperty=nameWithType> změní všechny znaky v řetězci na velká písmena. Následující příklad převádí řetězec "Hello World!" od smíšených písmen k velkými písmeny.  
  
 [!code-csharp[Strings.ChangingCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#1)]
 [!code-vb[Strings.ChangingCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#1)]  
  
 Předchozí příklad je ve výchozím nastavení citlivý na jazykovou verzi; použije konvence písmen aktuální jazykové verze. Chcete-li provést změnu malých a necitlivých na jazykovou verzi <xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> nebo použít konvence písmen <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> určité <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> jazykové verze, použijte přetížení metody a zařazujte hodnotu nebo objekt, který představuje zadanou jazykovou verzi pro parametr *jazykové verze.* Příklad, který ukazuje, jak <xref:System.String.ToUpper%2A> použít metodu k provedení změny malých a nerozlišující jazykovou verzi, naleznete [v tématu provádění změn velkých a malých písmen necitlivé jazykovou verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md).  
  
## <a name="tolower"></a>Tolower  
 Metoda <xref:System.String.ToLower%2A?displayProperty=nameWithType> je podobná předchozí metodě, ale místo toho převede všechny znaky v řetězci na malá písmena. Následující příklad převádí řetězec "Hello World!" na malá písmena.  
  
 [!code-csharp[Strings.ChangingCase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#2)]
 [!code-vb[Strings.ChangingCase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#2)]  
  
 Předchozí příklad je ve výchozím nastavení citlivý na jazykovou verzi; použije konvence písmen aktuální jazykové verze. Chcete-li provést změnu malých a necitlivých na jazykovou verzi <xref:System.String.ToLower%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> nebo použít konvence písmen <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> určité <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> jazykové verze, použijte přetížení metody a zařazujte hodnotu nebo objekt, který představuje zadanou jazykovou verzi pro parametr *jazykové verze.* Příklad, který ukazuje, jak <xref:System.String.ToLower%28System.Globalization.CultureInfo%29> použít metodu k provedení změny malých a nerozlišující jazykovou verzi, naleznete [v tématu provádění změn velkých a malých písmen necitlivé jazykovou verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md).  
  
## <a name="totitlecase"></a>Název  
 Převede <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> první znak každého slova na velká písmena a zbývající znaky na malá písmena. Slova, která jsou zcela velká písmena jsou však považovány za zkratky a nejsou převedeny.  
  
 Metoda <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> je citlivá na jazykovou verzi; to znamená, že používá konvence krytu určité jazykové verze. Chcete-li volat metodu, nejprve načíst <xref:System.Globalization.TextInfo> objekt, který představuje konvencí písmen konkrétní jazykové verze z <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType> vlastnosti konkrétní jazykové verze.  
  
 Následující příklad předá každý řetězec <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> v poli metodě.  Řetězce obsahují správné řetězce nadpisu a zkratky. Řetězce jsou převedeny na případ názvu pomocí konvencí skříně jazykové verze angličtiny (Spojené státy).  
  
 [!code-csharp[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/cs/totitlecase2.cs#1)]
 [!code-vb[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/vb/totitlecase2.vb#1)]  
  
 Všimněte si, že i <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> když je jazyková verze citlivé, metoda neposkytuje jazykově správná pravidla kasem. Například v předchozím příkladu metoda převede "příběh dvou měst" na "Příběh dvou měst". Nicméně, jazykově správný název kryt pro en-US kultury je "Příběh dvou měst."  
  
## <a name="see-also"></a>Viz také

- [Základní operace s řetězci](../../../docs/standard/base-types/basic-string-operations.md)
- [Provádění řetězcových operací nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
