---
title: "Změna velikosti písmen v .NET Frameworku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8b03dec350d38d15faaa6a0afc6a1f2c31d5c58f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="changing-case-in-net"></a>Změna velikosti písmen v rozhraní .NET
Pokud píšete aplikaci, která přijímá vstup od uživatele, nikdy lze zajistit co případu mu bude používat k zadání data. Často chcete řetězců, které mají být použita konzistentně, zejména v případě, že jste se zobrazení v uživatelském rozhraní. Následující tabulka popisuje tři metody změny velikosti písmen. První dvě metody poskytují přetížení, které přijímá jazykové verze.  
  
|Název metody|Použití|  
|-----------------|---------|  
|<xref:System.String.ToUpper%2A?displayProperty=nameWithType>|Převede všechny znaky v řetězci na velká písmena.|  
|<xref:System.String.ToLower%2A?displayProperty=nameWithType>|Převede všechny znaky v řetězci na malá písmena.|  
|<xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType>|Převede řetězec na první písmeno velké.|  
  
> [!WARNING]
>  Všimněte si, že <xref:System.String.ToUpper%2A?displayProperty=nameWithType> a <xref:System.String.ToLower%2A?displayProperty=nameWithType> metody by neměla být použity pro převod řetězců za účelem jejich porovnání nebo je test rovnosti. Další informace najdete v tématu [porovnávání řetězců smíšený případu](#Comparing) části.  
  
<a name="Comparing"></a>   
## <a name="comparing-strings-of-mixed-case"></a>Porovnávání řetězců smíšený případu  
 Pro porovnání řetězců smíšený případu určit jejich řazení, volání jednoho z přetížení <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metoda s `comparisonType` parametr a zadat hodnotu buď <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType>, <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType>, nebo <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> pro `comparisonType` argument. Pro porovnání, pomocí konkrétní jazykové verzi než aktuální jazykové verze, volejte přetížení <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metoda s oběma `culture` a `options` parametr a zadejte hodnotu <xref:System.Globalization.CompareOptions.IgnoreCase?displayProperty=nameWithType> jako `options` argument.  
  
 Pro porovnání řetězců smíšený velikosti písmen určí, zda jsou stejné, jejich, volání jednoho z přetížení <xref:System.String.Equals%2A?displayProperty=nameWithType> metoda s `comparisonType` parametr a zadat hodnotu buď <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType>, <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType>, nebo <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> pro `comparisonType` argument.  
  
 Další informace najdete v tématu [osvědčené postupy pro používání řetězců](../../../docs/standard/base-types/best-practices-strings.md).  
  
## <a name="toupper"></a>toUpper  
 <xref:System.String.ToUpper%2A?displayProperty=nameWithType> Metoda mění všechny znaky v řetězci na velká písmena. Následující příklad převede text "Hello, World!" z smíšený případ na velká písmena.  
  
 [!code-csharp[Strings.ChangingCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#1)]
 [!code-vb[Strings.ChangingCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#1)]  
  
 V předchozím příkladu je jazykovou ve výchozím nastavení; používá konvence velká a malá písmena aktuální jazykové verze. K provedení změny na jazykové verzi nebo pro použití konvencí konkrétní jazykové verzi, použijte <xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> metoda přetížení a s hodnotou <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> nebo <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> objekt, který představuje zadanou jazykovou verzi *jazykovou verzi* parametr. Pro příklad, který ukazuje, jak používat <xref:System.String.ToUpper%2A> metodu za účelem provedení nezávislé na jazykových změny, najdete v části [provádění změny nezávislé na jazykových případ](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md).  
  
## <a name="tolower"></a>toLower  
 <xref:System.String.ToLower%2A?displayProperty=nameWithType> Metoda je podobná předchozí metodě, ale místo toho převede všechny znaky v řetězci na malá písmena. Následující příklad převede text "Hello, World!" na malá písmena.  
  
 [!code-csharp[Strings.ChangingCase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#2)]
 [!code-vb[Strings.ChangingCase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#2)]  
  
 V předchozím příkladu je jazykovou ve výchozím nastavení; používá konvence velká a malá písmena aktuální jazykové verze. K provedení změny na jazykové verzi nebo pro použití konvencí konkrétní jazykové verzi, použijte <xref:System.String.ToLower%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> metoda přetížení a s hodnotou <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> nebo <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> objekt, který představuje zadanou jazykovou verzi *jazykovou verzi* parametr. Pro příklad, který ukazuje, jak používat <xref:System.String.ToLower%28System.Globalization.CultureInfo%29> metodu za účelem provedení nezávislé na jazykových změny, najdete v části [provádění změny nezávislé na jazykových případ](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md).  
  
## <a name="totitlecase"></a>ToTitleCase  
 <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> Převede první znak každého slova na velká písmena a ostatní písmena na malá písmena. Ale slova, která jsou zcela velká písmena se předpokládá, že režim a nejsou převést.  
  
 <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> Metoda zohledňující jazykovou verzi, tedy používá konvencí konkrétní jazykové verzi. Aby bylo možné volat metodu, je třeba nejprve načíst <xref:System.Globalization.TextInfo> objekt, který reprezentuje konvencí konkrétní jazykové verze z <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType> vlastnosti konkrétní jazykové verze.  
  
 Následující příklad předá pole na každý řetězec <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> metoda.  Řetězce zahrnují správný název řetězce, jakož i režim. Řetězce jsou převedeny na první písmeno velké pomocí konvencí jazykové verze Angličtina (Spojené státy).  
  
 [!code-csharp[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/cs/totitlecase2.cs#1)]
 [!code-vb[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/vb/totitlecase2.vb#1)]  
  
 Všimněte si, že i když je závislé na jazykové verzi, <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> metoda neposkytuje pravidla jazykově správné velká a malá písmena. Například v předchozím příkladu metoda převede "indikaci dvě měst" na "A činnosti z dvě města". Jazykově správný název velká a malá písmena pro jazykovou verzi en US je však "Indikaci dva měst."  
  
## <a name="see-also"></a>Viz také  
 [Základní operace s řetězci](../../../docs/standard/base-types/basic-string-operations.md)  
 [Provádění řetězcových operací nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
