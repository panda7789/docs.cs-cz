---
title: Vyplňování řetězců v .NET
description: Naučte se, jak odblokovat řetězce v .NET. Použijte metody String. PadLeft a String. PadRight pro přidání počátečních nebo koncových znaků k dosažení zadané celkové délky.
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
ms.openlocfilehash: 5bf7023a3429e932a44ad0a0bd3409012f77cbf9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594527"
---
# <a name="padding-strings-in-net"></a>Vyplňování řetězců v .NET

Použijte jednu z následujících <xref:System.String> metod pro vytvoření nového řetězce, který se skládá z původního řetězce, který je doplněn počátečními nebo koncovými znaky na určenou celkovou délku. Znak odsazení může být mezerou nebo zadaným znakem. Výsledný řetězec je pravděpodobně zarovnán vpravo nebo vlevo. Pokud je délka původního řetězce již rovna nebo větší než požadovaná celková délka, metody odsazení vrátí původní řetězec beze změny; Další informace naleznete v oddílech **vrátí** v částech dvou přetížení <xref:System.String.PadLeft%2A?displayProperty=nameWithType> <xref:System.String.PadRight%2A?displayProperty=nameWithType> metod a.
  
|Název metody|Použití|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|Vyplní řetězec úvodními znaky o zadanou celkovou délku.|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|Vyplní řetězec koncovými znaky o zadanou celkovou délku.|  
  
## <a name="padleft"></a>PadLeft  
 <xref:System.String.PadLeft%2A?displayProperty=nameWithType>Metoda vytvoří nový řetězec zřetězením dostatečného znaku přední plochy do původního řetězce, aby bylo možné dosáhnout zadané celkové délky. <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType>Metoda používá prázdné znaky jako ohraničující znak a <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> Metoda umožňuje zadat vlastní ohraničující znak.  
  
 Následující příklad kódu používá <xref:System.String.PadLeft%2A> metodu k vytvoření nového řetězce, který je dvacet znaků dlouhé. Příklad zobrazí " `--------Hello World!` " do konzoly.  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a>PadRight  
 <xref:System.String.PadRight%2A?displayProperty=nameWithType>Metoda vytvoří nový řetězec zřetězením dostatek koncových znaků do původního řetězce pro dosažení zadané celkové délky. <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType>Metoda používá prázdné znaky jako ohraničující znak a <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> Metoda umožňuje zadat vlastní ohraničující znak.  
  
 Následující příklad kódu používá <xref:System.String.PadRight%2A> metodu k vytvoření nového řetězce, který je dvacet znaků dlouhé. Příklad zobrazí " `Hello World!--------` " do konzoly.  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a>Viz také

- [Základní operace s řetězci](basic-string-operations.md)
