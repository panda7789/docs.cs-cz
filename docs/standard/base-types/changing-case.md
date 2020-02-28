---
title: Změna velikosti písmen v .NET
description: Přečtěte si, jak změnit v případě řetězců v .NET.
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
ms.openlocfilehash: 135cfa815c10d1a9dd9056604a4601678da9d5c4
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159348"
---
# <a name="changing-case-in-net"></a>Změna velikosti písmen v .NET
Pokud napíšete aplikaci, která přijímá vstup od uživatele, nikdy nemusíte mít jistotu, v jakém případě bude tento případ použit k zadání dat. Často chcete, aby byly řetězce použita konzistentně, zejména v případě, že je zobrazujete v uživatelském rozhraní. Následující tabulka popisuje tři metody změny velikosti písmen. První dvě metody poskytují přetížení, které přijímá jazykovou verzi.  
  
|Název metody|Použití|  
|-----------------|---------|  
|<xref:System.String.ToUpper%2A?displayProperty=nameWithType>|Převede všechny znaky v řetězci na velká písmena.|  
|<xref:System.String.ToLower%2A?displayProperty=nameWithType>|Převede všechny znaky v řetězci na malá písmena.|  
|<xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType>|Převede řetězec na název Case.|  
  
> [!WARNING]
> Všimněte si, že metody <xref:System.String.ToUpper%2A?displayProperty=nameWithType> a <xref:System.String.ToLower%2A?displayProperty=nameWithType> by se neměly používat k převodu řetězců, aby je bylo možné porovnat nebo otestovat pro rovnost. Další informace najdete v části [porovnávání řetězců smíšeného případu](#Comparing) .  
  
<a name="Comparing"></a>
## <a name="comparing-strings-of-mixed-case"></a>Porovnávání řetězců smíšeného případu  
 Chcete-li porovnat řetězce kombinovaného případu s určením jejich řazení, zavolejte jedno z přetížení metody <xref:System.String.CompareTo%2A?displayProperty=nameWithType> s parametrem `comparisonType` a zadejte hodnotu buď <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType>, <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType>nebo <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> pro argument `comparisonType`. Pro porovnání s použitím jiné jazykové verze než aktuální jazykové verze volejte přetížení metody <xref:System.String.CompareTo%2A?displayProperty=nameWithType> s parametrem `culture` a `options` a zadejte hodnotu <xref:System.Globalization.CompareOptions.IgnoreCase?displayProperty=nameWithType> jako argument `options`.  
  
 Chcete-li porovnat řetězce smíšeného případu a určit, zda jsou stejné, volejte jedno z přetížení metody <xref:System.String.Equals%2A?displayProperty=nameWithType> s parametrem `comparisonType` a zadejte hodnotu buď <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType>, <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType>nebo <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> pro argument `comparisonType`.  
  
 Další informace najdete v tématu [osvědčené postupy pro používání řetězců](../../../docs/standard/base-types/best-practices-strings.md).  
  
## <a name="toupper"></a>toUpper  
 Metoda <xref:System.String.ToUpper%2A?displayProperty=nameWithType> změní všechny znaky v řetězci na velká písmena. Následující příklad převede řetězec "Hello World!" ze smíšené velikosti písmen na velká písmena.  
  
 [!code-csharp[Strings.ChangingCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#1)]
 [!code-vb[Strings.ChangingCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#1)]  
  
 V předchozím příkladu je standardně závislý na jazykové verzi; aplikuje konvence pro velká a malá písmena aktuální jazykové verze. Chcete-li provést změnu velikosti písmen nezávisle na jazykové verzi nebo použít konvence pro velká a malá písmena konkrétní jazykové verze, použijte přetížení metody <xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> a zadejte hodnotu <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> nebo objekt <xref:System.Globalization.CultureInfo?displayProperty=nameWithType>, který představuje zadanou jazykovou verzi parametru *jazykové verze* . Příklad, jak použít metodu <xref:System.String.ToUpper%2A> k provedení změny velikosti písmen nezávisle na jazykové verzi, naleznete v tématu [provádění změn velikosti písmen nezávisle na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md).  
  
## <a name="tolower"></a>toLower  
 Metoda <xref:System.String.ToLower%2A?displayProperty=nameWithType> je podobná předchozí metodě, ale místo toho převádí všechny znaky v řetězci na malá písmena. Následující příklad převede řetězec "Hello World!" na malá písmena.  
  
 [!code-csharp[Strings.ChangingCase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#2)]
 [!code-vb[Strings.ChangingCase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#2)]  
  
 V předchozím příkladu je standardně závislý na jazykové verzi; aplikuje konvence pro velká a malá písmena aktuální jazykové verze. Chcete-li provést změnu velikosti písmen nezávisle na jazykové verzi nebo použít konvence pro velká a malá písmena konkrétní jazykové verze, použijte přetížení metody <xref:System.String.ToLower%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> a zadejte hodnotu <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> nebo objekt <xref:System.Globalization.CultureInfo?displayProperty=nameWithType>, který představuje zadanou jazykovou verzi parametru *jazykové verze* . Příklad, jak použít metodu <xref:System.String.ToLower%28System.Globalization.CultureInfo%29> k provedení změny velikosti písmen nezávisle na jazykové verzi, naleznete v tématu [provádění změn velikosti písmen nezávisle na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md).  
  
## <a name="totitlecase"></a>ToTitleCase  
 <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> převede první znak každého slova na velká a zbývající znaky na malá. Slova, která jsou zcela velká, se však považují za zkratky a nebudou převedena.  
  
 Metoda <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> je závislá na jazykové verzi; To znamená, že používá konvence pro velká a malá písmena konkrétní jazykové verze. Pro volání metody nejprve načtěte <xref:System.Globalization.TextInfo> objekt, který představuje konvence pro velká a malá písmena konkrétní jazykové verze z vlastnosti <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType> konkrétní jazykové verze.  
  
 Následující příklad předává každý řetězec v poli do metody <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType>.  Řetězce obsahují správné řetězce nadpisu i akronymy. Řetězce jsou převedeny na velká písmena pomocí konvencí pro používání velkých a malých písmen jazykové verze anglické (USA).  
  
 [!code-csharp[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/cs/totitlecase2.cs#1)]
 [!code-vb[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/vb/totitlecase2.vb#1)]  
  
 Všimněte si, že i když je závislá na jazykové verzi, metoda <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> neposkytuje lingvisticky správná pravidla pro velká písmena. Například metoda v předchozím příkladu převede "sdělovač dvou měst" na "sdělovač dvou měst". Lingvisticky správná velikost nadpisu pro jazykovou verzi en-US je ale "sdělovačem dvou měst".  
  
## <a name="see-also"></a>Viz také

- [Základní operace s řetězci](../../../docs/standard/base-types/basic-string-operations.md)
- [Provádění řetězcových operací nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
