---
title: "Provádění porovnávání řetězců nezávislých na jazykové verzi"
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
- String.CompareTo method
- String.Compare method
- string comparison [.NET Framework], culture-insensitive
- strings [.NET Framework], comparing
- culture-insensitive string operations, comparisons
- culture parameter
ms.assetid: abae50ef-32f7-4a50-a540-fd256fd1aed0
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fa689a685a58868ccd34b8bcbc4a779b9f826473
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="performing-culture-insensitive-string-comparisons"></a>Provádění porovnávání řetězců nezávislých na jazykové verzi
Ve výchozím nastavení <xref:System.String.Compare%2A?displayProperty=nameWithType> metoda provádí porovnání zohledňující jazykovou verzi a velká a malá písmena. Tato metoda také zahrnuje několik přetížení, které poskytují `culture` parametr, který umožňuje zadat jazykovou verzi, pokud chcete použít, a `comparisonType` parametr, který slouží k určení pravidel porovnání, které můžete použít. Volání těchto metod namísto výchozího přetížení odstraní jakoukoli nejednoznačnost týkající se pravidel používaných při volání konkrétní metody a objasňuje, zda je konkrétní porovnání závislé na jazykové verzi či nikoli.  
  
> [!NOTE]
>  Obě přetížení <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metoda provést porovnání zohledňující jazykovou verzi a velká a malá písmena, tuto metodu nelze použít k provádění porovnávání na jazykové verzi. Pro přehlednost kódu, doporučujeme použít <xref:System.String.Compare%2A?displayProperty=nameWithType> metoda místo.  
  
 Pro operace zohledňující jazykovou verzi, zadejte <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> nebo <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> hodnota výčtu jako `comparisonType` parametr. Pokud chcete provést porovnání zohledňující jazykovou verzi pomocí určené jazykové verze než aktuální jazykovou verzi, zadejte <xref:System.Globalization.CultureInfo> objekt, který představuje tuto jazykovou verzi, jako `culture` parametr.  
  
 Porovnávání řetězců nezávislých na jazykové verzi nepodporuje <xref:System.String.Compare%2A?displayProperty=nameWithType> metoda jsou buď lingvistické (na základě konvence řazení neutrální jazykovou verzi) nebo jiných jazykové (založené na pořadovém čísle znaků v řetězci). Většina porovnání řetězců nezávislých na jazykové verzi je nejazykových. Pro tyto porovnání, zadejte <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> nebo <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> hodnota výčtu jako `comparisonType` parametr. Pokud je například bezpečnostní rozhodnutí (jako je porovnání uživatelského jména a hesla) založeno na výsledku porovnání řetězců, operace by měla být nezávislá na jazykové verzi a jazyce, aby výsledek nemohl být ovlivněn konvencemi konkrétní jazykové verze nebo jazyka.  
  
 Pokud chcete zpracovávat jazykově odpovídající řetězce z několika jazykových verzí konzistentním způsobem, použijte porovnání lingvistických řetězců nezávislé na jazykové verzi. Jestliže vaše aplikace zobrazuje například slova, která používají více znakových sad v seznamu, budete pravděpodobně chtít zobrazit slova ve stejném pořadí bez ohledu na aktuální jazykovou verzi. Pro jazyková porovnání nezávislá na jazykových verzích definuje rozhraní .NET Framework neutrální jazykovou verzi, která bude založena na jazykových konvencích angličtiny. Chcete-li provést porovnání nezávislé na jazykových lingvistické, zadejte <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> nebo <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType> jako `comparisonType` parametr.  
  
 Následující příklad provádí dvě nejazyková porovnání řetězců nezávislá na jazykové verzi. V prvním porovnání se rozlišují velká a malá písmena, ve druhém nikoli.  
  
 [!code-csharp[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/cs/cultureinsensitive1.cs#1)]
 [!code-vb[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/vb/cultureinsensitive1.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.String.Compare%2A?displayProperty=nameWithType>  
 <xref:System.String.CompareTo%2A?displayProperty=nameWithType>  
 [Provádění řetězcových operací nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)  
 [Doporučené postupy pro používání řetězců](../../../docs/standard/base-types/best-practices-strings.md)
