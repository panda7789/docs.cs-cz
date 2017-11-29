---
title: "while (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords: while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 420b409689d877c3e1ac744e8d7a65500cf8f964
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="while-c-reference"></a>while (Referenční dokumentace jazyka C#)
`while` Příkaz spustí příkaz nebo blok příkazy, dokud vyhodnotí zadaný výraz pro `false`.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csrefKeywordsIteration#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_1.cs)]  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csrefKeywordsIteration#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_2.cs)]  
  
## <a name="example"></a>Příklad  
 Protože test `while` výraz probíhá před každou provádění smyčky, `while` smyčky spustí vícekrát nebo. Tím se liší od [provést](../../../csharp/language-reference/keywords/do.md) smyčky, které provede jeden či více krát.  
  
 A `while` můžete ukončit smyčky, kdy [zalomení](../../../csharp/language-reference/keywords/break.md), [goto](../../../csharp/language-reference/keywords/goto.md), [vrátit](../../../csharp/language-reference/keywords/return.md), nebo [throw](../../../csharp/language-reference/keywords/throw.md) příkaz předá řízení mimo smyčky. Chcete-li předat řízení do další iterace bez ukončení opakování, použijte [pokračovat](../../../csharp/language-reference/keywords/continue.md) příkaz. Všimněte si rozdíl ve výstupu v předchozí tři příklady, v závislosti na tom, kde `int n` se zvýší. V příkladu níže žádný výstup se generuje.  
  
 [!code-csharp[csrefKeywordsIteration#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_3.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [while – příkaz (C++)](/cpp/cpp/while-statement-cpp)  
 [Příkazy iterace](../../../csharp/language-reference/keywords/iteration-statements.md)
