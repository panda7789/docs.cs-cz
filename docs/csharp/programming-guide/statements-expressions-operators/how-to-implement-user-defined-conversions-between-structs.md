---
title: "Postupy: Implementace uživatelem definovaných převodů mezi strukturami (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: user-defined conversions [C#]
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7d86cbd48347e6951f6b6883a385d80d68697c9c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-user-defined-conversions-between-structs-c-programming-guide"></a>Postupy: Implementace uživatelem definovaných převodů mezi strukturami (Průvodce programováním v C#)
Tento příklad definuje dvě struktury `RomanNumeral` a `BinaryNumeral`a předvádí převody mezi nimi.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideStatements#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_1.cs)]  
  
## <a name="robust-programming"></a>Robustní programování  
  
-   V předchozím příkladu, příkaz:  
  
     [!code-csharp[csProgGuideStatements#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_2.cs)]  
  
     provede převod z `RomanNumeral` k `BinaryNumeral`. Protože není k dispozici žádný přímý převod z `RomanNumeral` k `BinaryNumeral`, přetypování slouží k převodu z `RomanNumeral` k `int`a jiné přetypování převést z `int` k `BinaryNumeral`.  
  
-   Také příkaz  
  
     [!code-csharp[csProgGuideStatements#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_3.cs)]  
  
     provede převod z `BinaryNumeral` k `RomanNumeral`. Protože `RomanNumeral` definuje implicitní převod z `BinaryNumeral`, není třeba žádné přetypování.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Operátory převodu](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
