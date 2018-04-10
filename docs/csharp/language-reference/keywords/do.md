---
title: do (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d24078d3fb985f643fb66aa456900d03d2ff3fce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="do-c-reference"></a>do (Referenční dokumentace jazyka C#)
`do` Příkaz spustí příkaz nebo blok příkazů opakovaně dokud vyhodnotí zadaný výraz pro `false`. V závorkách, musí být uzavřena do těla smyčky `{}`, pokud se skládá z jednoho příkazu. V takovém případě jsou volitelné složené závorky.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `do-while` smyčky příkazy spustit stejně dlouho jako proměnnou `x` je menší než 5.  
  
 [!code-csharp[csrefKeywordsIteration#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/do_1.cs)]  
  
 Na rozdíl od [při](../../../csharp/language-reference/keywords/while.md) příkaz, `do-while` smyčky se spustí jednou předtím, než je vyhodnocena podmíněným výrazem.  
  
 Na kterémkoli bodu v `do-while` bloku, může dojít k narušení mimo pomocí smyčky [zalomení](../../../csharp/language-reference/keywords/break.md) příkaz. Můžete přímo na krok `while` příkaz vyhodnocení výrazu pomocí [pokračovat](../../../csharp/language-reference/keywords/continue.md) příkaz. Pokud `while` výraz vyhodnocen jako true, provádění pokračuje první příkaz ve smyčce. Pokud je výsledkem na hodnotu false, pokračuje první příkaz po spuštění `do-while` smyčky.  
  
 A `do-while` smyčky můžete také měly být byl ukončen ve [goto](../../../csharp/language-reference/keywords/goto.md), [vrátit](../../../csharp/language-reference/keywords/return.md), nebo [throw](../../../csharp/language-reference/keywords/throw.md) příkazy.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Proveďte-while – příkaz (C++)](/cpp/cpp/do-while-statement-cpp)  
 [Příkazy iterace](../../../csharp/language-reference/keywords/iteration-statements.md)
