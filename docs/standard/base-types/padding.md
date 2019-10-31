---
title: Vyplňování řetězců v .NET
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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127629"
---
# <a name="padding-strings-in-net"></a>Vyplňování řetězců v .NET

Použijte jednu z následujících metod <xref:System.String> k vytvoření nového řetězce, který se skládá z původního řetězce, který je doplněn počátečními nebo koncovými znaky na určenou celkovou délku. Znak odsazení může být mezerou nebo zadaným znakem. Výsledný řetězec je pravděpodobně zarovnán vpravo nebo vlevo. Pokud je délka původního řetězce již rovna nebo větší než požadovaná celková délka, metody odsazení vrátí původní řetězec beze změny; Další informace naleznete v oddílech **vrátí** v částech dvou přetížení <xref:System.String.PadLeft%2A?displayProperty=nameWithType> a <xref:System.String.PadRight%2A?displayProperty=nameWithType> metod.
  
|Název metody|Použití|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|Vyplní řetězec úvodními znaky o zadanou celkovou délku.|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|Vyplní řetězec koncovými znaky o zadanou celkovou délku.|  
  
## <a name="padleft"></a>PadLeft  
 Metoda <xref:System.String.PadLeft%2A?displayProperty=nameWithType> vytvoří nový řetězec zřetězením dostatečného vodicího znaku k původnímu řetězci, abyste dosáhli zadané celkové délky. Metoda <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> používá prázdné znaky jako ohraničující znak a metoda <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> umožňuje zadat vlastní ohraničující znak.  
  
 Následující příklad kódu používá metodu <xref:System.String.PadLeft%2A> k vytvoření nového řetězce, který je dvacet znaků dlouhé. V příkladu se zobrazí zpráva "`--------Hello World!`" do konzoly.  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a>PadRight  
 Metoda <xref:System.String.PadRight%2A?displayProperty=nameWithType> vytvoří nový řetězec zřetězením dostatek koncových znaků do původního řetězce, aby bylo možné dosáhnout zadané celkové délky. Metoda <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> používá prázdné znaky jako ohraničující znak a metoda <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> umožňuje zadat vlastní ohraničující znak.  
  
 Následující příklad kódu používá metodu <xref:System.String.PadRight%2A> k vytvoření nového řetězce, který je dvacet znaků dlouhé. V příkladu se zobrazí zpráva "`Hello World!--------`" do konzoly.  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a>Viz také:

- [Základní operace s řetězci](../../../docs/standard/base-types/basic-string-operations.md)
