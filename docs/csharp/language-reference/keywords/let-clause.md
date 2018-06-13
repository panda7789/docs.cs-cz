---
title: let – klauzule (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: 9d625db1231687cdad2e24303b2e08ecf736a50c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269637"
---
# <a name="let-clause-c-reference"></a>let – klauzule (Referenční dokumentace jazyka C#)
Ve výrazu dotazu je někdy užitečné k ukládání výsledků dílčí výrazu, aby bylo možné používat v dalších klauzule. Můžete to provést pomocí `let` – klíčové slovo, které vytvoří novou proměnnou rozsahu a inicializuje s výsledkem výrazu zadáte. Jakmile inicializovaný s hodnotou, proměnnou rozsahu nelze použít k uložení jinou hodnotu. Ale pokud proměnnou rozsahu obsahuje dotazovatelné typu, může být dotazován.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `let` slouží dvěma způsoby:  
  
1.  Chcete-li vytvořit vyčíslitelná typ, který je možné samotné dotázat.  
  
2.  Chcete-li povolit dotaz pro volání `ToLower` jenom jednou na proměnnou rozsahu `word`. Bez použití `let`, budete muset volat `ToLower` v každé predikát `where` klauzule.  
  
 [!code-csharp[cscsrefQueryKeywords#28](../../../csharp/language-reference/keywords/codesnippet/CSharp/let-clause_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Klíčová slova dotazu (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
 [LINQ – výrazy dotazů](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Začínáme s dotazy LINQ v jazyce C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Postupy: zpracování výjimek ve výrazech dotazů](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md)
