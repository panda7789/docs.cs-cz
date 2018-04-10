---
title: into (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7f2400143e66c68942cdec3ebfa04cfdd8cfe983
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="into-c-reference"></a>into (Referenční dokumentace jazyka C#)
`into` Kontextové klíčové slovo lze použít k vytvoření dočasného identifikátor k ukládání výsledků [skupiny](../../../csharp/language-reference/keywords/group-clause.md), [spojení](../../../csharp/language-reference/keywords/join-clause.md) nebo [vyberte](../../../csharp/language-reference/keywords/select-clause.md) klauzule do nový identifikátor. Tento identifikátor může být sám generátor pro příkazy další dotaz. Při použití v `group` nebo `select` klauzuli použití nový identifikátor se někdy označuje jako *pokračování*.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití `into` – klíčové slovo povolit dočasné identifikátor `fruitGroup` jehož typ odvozené `IGrouping`. Pomocí identifikátor můžete vyvolat <xref:System.Linq.Enumerable.Count%2A> metoda na každé skupiny a vybrat jenom skupiny, které obsahují dvě nebo více slov.  
  
 [!code-csharp[cscsrefQueryKeywords#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/into_1.cs)]  
  
 Použití `into` v `group` klauzule je potřeba, pouze pokud chcete provádět operace další dotaz pro každou skupinu. Další informace najdete v tématu [group – klauzule](../../../csharp/language-reference/keywords/group-clause.md).  
  
 Příklad použití `into` v `join` klauzule, najdete v části [klauzuli join](../../../csharp/language-reference/keywords/join-clause.md).  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova dotazu (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
 [LINQ – výrazy dotazů](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Group – klauzule](../../../csharp/language-reference/keywords/group-clause.md)
