---
title: 'Postupy: Implementace uživatelem definovaných převodů mezi strukturami (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- user-defined conversions [C#]
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
ms.openlocfilehash: 178d9e2f92c5c1989253a16d866052a1fc42c10e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339927"
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
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Operátory převodu](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
