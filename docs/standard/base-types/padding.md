---
title: "Doplňování řetězců v .NET"
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
- cpp
helpviewer_keywords:
- strings [.NET Framework], padding
- white space
- PadRight method
- PadLeft method
- padding strings
ms.assetid: 84a9f142-3244-4c90-ba02-21af9bbaff71
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ea903c1f950e7c226e043c1fa7276a66126b2512
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="padding-strings-in-net"></a>Doplňování řetězců v .NET
Použijte jednu z následujících <xref:System.String> metody pro vytvoření nového řetězce, který se skládá z původního řetězce, který doplněno počáteční nebo koncové znaky zadané celkové délky. Znak odsazení může být mezery nebo je zadaný znak a proto se zobrazí se vpravo zarovnaný nebo zarovnaný doleva.  
  
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
