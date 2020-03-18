---
title: Odsazení řetězců v rozhraní .NET
ms.date: 03/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strings [.NET Framework], padding
- white space
- PadRight method
- PadLeft method
- padding strings
ms.assetid: 84a9f142-3244-4c90-ba02-21af9bbaff71
ms.openlocfilehash: 2cf114296005456f354d286aa2804fa8a95160dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127629"
---
# <a name="padding-strings-in-net"></a>Odsazení řetězců v rozhraní .NET

Pomocí jedné z <xref:System.String> následujících metod vytvořte nový řetězec, který se skládá z původního řetězce, který je doplněn úvodními nebo koncovými znaky na zadanou celkovou délku. Znak odsazení může být mezera nebo zadaný znak. Výsledný řetězec se zdá být buď zarovnaný doprava nebo doleva. Pokud je délka původního řetězce již rovna nebo větší než požadovaná celková délka, metody odsazení vrátí původní řetězec beze změny; další informace naleznete v části **Vrátí** dvě přetížení <xref:System.String.PadLeft%2A?displayProperty=nameWithType> <xref:System.String.PadRight%2A?displayProperty=nameWithType> metody a.
  
|Název metody|Použití|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|Vykázne řetězec s úvodními znaky na zadanou celkovou délku.|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|Vykácí řetězec s koncovými znaky na zadanou celkovou délku.|  
  
## <a name="padleft"></a>PadLeft  
 Metoda <xref:System.String.PadLeft%2A?displayProperty=nameWithType> vytvoří nový řetězec zřetězením dostatečného počtu znaků úvodní podložky do původního řetězce, aby bylo dosaženo zadané celkové délky. Metoda <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> používá prázdné místo jako znak <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> odsazení a metoda umožňuje zadat vlastní znak odsazení.  
  
 Následující příklad kódu <xref:System.String.PadLeft%2A> používá metodu k vytvoření nového řetězce, který je dlouhý dvacet znaků. V příkladu`--------Hello World!`se zobrazí " " " do konzoly.  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a>PadRight  
 Metoda <xref:System.String.PadRight%2A?displayProperty=nameWithType> vytvoří nový řetězec zřetězením dostatečného počtu znaků koncové podložky na původní řetězec, aby bylo dosaženo zadané celkové délky. Metoda <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> používá prázdné místo jako znak <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> odsazení a metoda umožňuje zadat vlastní znak odsazení.  
  
 Následující příklad kódu <xref:System.String.PadRight%2A> používá metodu k vytvoření nového řetězce, který je dlouhý dvacet znaků. V příkladu`Hello World!--------`se zobrazí " " " do konzoly.  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a>Viz také

- [Základní operace s řetězci](../../../docs/standard/base-types/basic-string-operations.md)
