---
title: "Doplňování řetězců v .NET"
ms.custom: 
ms.date: 03/15/2018
ms.prod: .net
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: bf90c841c8fff21dd423fcd19613b5eb46a2c80c
ms.sourcegitcommit: 1c0b0f082b3f300e54b4d069b317ac724c88ddc3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2018
---
# <a name="padding-strings-in-net"></a>Doplňování řetězců v .NET

Použijte jednu z následujících <xref:System.String> metody pro vytvoření nového řetězce, který se skládá z původního řetězce, který doplněno počáteční nebo koncové znaky zadané celkové délky. Znak odsazení může být mezery nebo je zadaný znak. Výsledný řetězec pravděpodobně zarovnaný doprava nebo zarovnaný doleva. Pokud délka původního řetězce je již roven nebo větší než požadované celková délka, metody odsazení vrátí původní řetězec beze změny; Další informace najdete v tématu **vrátí** části dvě přetížení <xref:System.String.PadLeft%2A?displayProperty=nameWithType> a <xref:System.String.PadRight%2A?displayProperty=nameWithType> metody.
  
|Název metody|Použití|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|Ohraničí řetězec počátečními znaky na zadané celkové délky.|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|Ohraničí řetězec koncové znaky k zadané celkové délky.|  
  
## <a name="padleft"></a>padLeft  
 <xref:System.String.PadLeft%2A?displayProperty=nameWithType> Metoda vytvoří nový řetězec zřetězením dostatek úvodní znaků na původní řetězec k dosažení zadané celkové délky. <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> Metoda používá prázdné znaky jako znak odsazení a <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> metoda umožňuje zadat vlastní znak odsazení.  
  
 Následující příklad kódu používá <xref:System.String.PadLeft%2A> metodu pro vytvoření nového řetězce, který je 20 znaků. V příkladu se zobrazí "`--------Hello World!`" ke konzole.  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a>PadRight –  
 <xref:System.String.PadRight%2A?displayProperty=nameWithType> Metoda vytvoří nový řetězec zřetězením dostatek koncových znaků pro původního řetězce pro dosažení zadané celkové délky. <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> Metoda používá prázdné znaky jako znak odsazení a <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> metoda umožňuje zadat vlastní znak odsazení.  
  
 Následující příklad kódu používá <xref:System.String.PadRight%2A> metodu pro vytvoření nového řetězce, který je 20 znaků. V příkladu se zobrazí "`Hello World!--------`" ke konzole.  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a>Viz také  
 [Základní operace s řetězci](../../../docs/standard/base-types/basic-string-operations.md)
