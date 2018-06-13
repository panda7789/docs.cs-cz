---
title: into (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
ms.openlocfilehash: 9bc7d50b77fe42861f92cc5bec946678d11d73d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33266861"
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
 [group – klauzule](../../../csharp/language-reference/keywords/group-clause.md)
