---
title: Doplňování řetězců v .NET
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f58e1c3a9e42f48ecc219a2db1649051f9ca20b
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43890724"
---
# <a name="padding-strings-in-net"></a>Doplňování řetězců v .NET

Použijte jednu z následujících <xref:System.String> metody k vytvoření nového řetězce, který se skládá z původního řetězce, který je vyplněna úvodní a koncové znaky na zadané celkové délky. Znak odsazení může být mezera nebo je zadaný znak. Výsledný řetězec se zdá být zarovnaný doprava nebo doleva. Pokud délka původního řetězce je již roven nebo větší než požadovaný celková délka, odsazení metody vrací původního řetězce beze změny; Další informace najdete v tématu **vrátí** oddíly dvě přetížení <xref:System.String.PadLeft%2A?displayProperty=nameWithType> a <xref:System.String.PadRight%2A?displayProperty=nameWithType> metody.
  
|Název metody|Použití|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|Vyplní řetězec s počátečními znaky na zadané celkové délky.|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|Vyplní řetězec s koncové znaky na zadané celkové délky.|  
  
## <a name="padleft"></a>padLeft  
 <xref:System.String.PadLeft%2A?displayProperty=nameWithType> Metoda vytvoří nový řetězec zřetězením dostatek přední znaků na původní řetězec k dosažení zadané celkové délky. <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> Metoda používá prázdný znak jako znak odsazení a <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> metoda vám umožňuje určit vlastní odsazení znaku.  
  
 Následující příklad kódu používá <xref:System.String.PadLeft%2A> metodu pro vytvoření nového řetězce, který je 20 znaků. V příkladu se zobrazí "`--------Hello World!`" do konzoly.  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a>PadRight –  
 <xref:System.String.PadRight%2A?displayProperty=nameWithType> Metoda vytvoří nový řetězec zřetězením dostatek koncových znaků na původní řetězec k dosažení zadané celkové délky. <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> Metoda používá prázdný znak jako znak odsazení a <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> metoda vám umožňuje určit vlastní odsazení znaku.  
  
 Následující příklad kódu používá <xref:System.String.PadRight%2A> metodu pro vytvoření nového řetězce, který je 20 znaků. V příkladu se zobrazí "`Hello World!--------`" do konzoly.  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a>Viz také:

- [Základní operace s řetězci](../../../docs/standard/base-types/basic-string-operations.md)
