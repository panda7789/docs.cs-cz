---
title: Změna velikosti písmen v .NET
description: Zjistěte, jak změnit v případě řetězců v .NET.
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
author: rpetrusha
ms.author: ronpet
ms.custom: seodec18
ms.openlocfilehash: ce495ce01c970fb46cc7e7e374994fd34a7730a7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051569"
---
# <a name="changing-case-in-net"></a>Změna velikosti písmen v .NET
Pokud píšete aplikaci, která přijímá vstup od uživatele, nikdy lze zajistit co případ uživatel použije k zadání data. Často chcete řetězců, které mají být notaci, zejména v případě, že jsou zobrazeny v uživatelském rozhraní. Následující tabulka popisuje tři metody změny velikosti písmen. První dvě metody poskytují přetížení přijímající jazykovou verzi.  
  
|Název metody|Použití|  
|-----------------|---------|  
|<xref:System.String.ToUpper%2A?displayProperty=nameWithType>|Převede všechny znaky v řetězci na velká písmena.|  
|<xref:System.String.ToLower%2A?displayProperty=nameWithType>|Převede všechny znaky v řetězci na malá písmena.|  
|<xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType>|Převede řetězec na první velká písmena.|  
  
> [!WARNING]
>  Všimněte si, <xref:System.String.ToUpper%2A?displayProperty=nameWithType> a <xref:System.String.ToLower%2A?displayProperty=nameWithType> metody nesmějí být používány pro převod řetězců za účelem jejich porovnání nebo test rovnosti. Další informace najdete v tématu [porovnávání řetězců smíšené znakové](#Comparing) oddílu.  
  
<a name="Comparing"></a>   
## <a name="comparing-strings-of-mixed-case"></a>Porovnávání řetězců smíšené případu  
 Porovnat řetězce smíšené znakové určit jejich pořadí, volání jednoho z přetížení <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody `comparisonType` parametr a zadat hodnotu buď <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType>, <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType>, nebo <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> pro `comparisonType` argument. Porovnání pomocí konkrétní jazykové verze, než aktuální jazykové verze, volejte přetížení <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metoda s oběma `culture` a `options` parametr a zadejte hodnotu <xref:System.Globalization.CompareOptions.IgnoreCase?displayProperty=nameWithType> jako `options` argument.  
  
 Porovnat řetězce smíšené velikosti písmen určí, jestli jsou shodné, jejich, volání jednoho z přetížení <xref:System.String.Equals%2A?displayProperty=nameWithType> metody `comparisonType` parametr a zadat hodnotu buď <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType>, <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType>, nebo <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> pro `comparisonType` argument.  
  
 Další informace najdete v tématu [osvědčené postupy pro používání řetězců](../../../docs/standard/base-types/best-practices-strings.md).  
  
## <a name="toupper"></a>toUpper  
 <xref:System.String.ToUpper%2A?displayProperty=nameWithType> Metoda změní všechny znaky v řetězci na velká písmena. Následující příklad převádí řetězec "Hello World!" z smíšené případu na velká písmena.  
  
 [!code-csharp[Strings.ChangingCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#1)]
 [!code-vb[Strings.ChangingCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#1)]  
  
 V předchozím příkladu je zohledňující jazykovou verzi ve výchozím nastavení; používá konvence pro malá a velká písmena aktuální jazykové verze. K provedení změny nezávislých na jazykové verzi nebo použití konvencí konkrétní jazykové verze, použijte <xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> metody přetížení a zadat hodnotu <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> nebo <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> objekt, který reprezentuje zadanou jazykovou verzi *jazykovou verzi* parametru. Příklad, který ukazuje, jak používat <xref:System.String.ToUpper%2A> možností, jak provést změnu velikosti písmen nezávislých na jazykové verzi, najdete v článku [provádění změny nezávislých na jazykové verzi případ](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md).  
  
## <a name="tolower"></a>toLower  
 <xref:System.String.ToLower%2A?displayProperty=nameWithType> Metoda je podobná metodě předchozí, ale místo toho převede všechny znaky v řetězci na malá písmena. Následující příklad převádí řetězec "Hello World!" na malá písmena.  
  
 [!code-csharp[Strings.ChangingCase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#2)]
 [!code-vb[Strings.ChangingCase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#2)]  
  
 V předchozím příkladu je zohledňující jazykovou verzi ve výchozím nastavení; používá konvence pro malá a velká písmena aktuální jazykové verze. K provedení změny nezávislých na jazykové verzi nebo použití konvencí konkrétní jazykové verze, použijte <xref:System.String.ToLower%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> metody přetížení a zadat hodnotu <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> nebo <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> objekt, který reprezentuje zadanou jazykovou verzi *jazykovou verzi* parametru. Příklad, který ukazuje, jak používat <xref:System.String.ToLower%28System.Globalization.CultureInfo%29> možností, jak provést změnu velikosti písmen nezávislých na jazykové verzi, najdete v článku [provádění změny nezávislých na jazykové verzi případ](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md).  
  
## <a name="totitlecase"></a>ToTitleCase  
 <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> Převede první znak každého slova na velká a ostatní písmena na malá písmena. Slova, která jsou zcela velká však budou považovat za zkratky a nepřevádějí.  
  
 <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> Zohledňující jazykovou verzi je metoda; to znamená, používá konvence malých a velkých písmen konkrétní jazykové verze. Aby bylo možné volat metodu, můžete nejdřív načtěte <xref:System.Globalization.TextInfo> objekt, který představuje konkrétní jazykovou verzi z konvencí <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType> vlastnost konkrétní jazykové verze.  
  
 Následující příklad předá každý řetězec v matici <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> metody.  Řetězce zahrnovat správný název řetězce a zkratky. Řetězce jsou převedeny na první velká písmena pomocí malých a velkých písmen úmluv jazykové verze Angličtina (Spojené státy).  
  
 [!code-csharp[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/cs/totitlecase2.cs#1)]
 [!code-vb[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/vb/totitlecase2.vb#1)]  
  
 Všimněte si, že i když je zohledňující jazykovou verzi <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> metoda neposkytuje pravidla lingvistických správná velká a malá písmena. Například v předchozím příkladu, metoda převede "činnosti z měst" do "A činnosti z dvou Cities". Ale je velká a malá písmena lingvistických správný název jazykové verze en US "Činnosti dvou města."  
  
## <a name="see-also"></a>Viz také:

- [Základní operace s řetězci](../../../docs/standard/base-types/basic-string-operations.md)
- [Provádění řetězcových operací nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
