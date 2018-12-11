---
title: 'Postupy: Implementace uživatelem definovaných převodů mezi strukturami - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- user-defined conversions [C#]
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
ms.openlocfilehash: 85345203982679c0ab8dc9a6ae899312204c3230
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241571"
---
# <a name="how-to-implement-user-defined-conversions-between-structs-c-programming-guide"></a>Postupy: Implementace uživatelem definovaných převodů mezi strukturami (C# Průvodce programováním v)
Tento příklad definuje dvě struktury `RomanNumeral` a `BinaryNumeral`a ukazuje převody mezi nimi.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideStatements#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_1.cs)]  
  
## <a name="robust-programming"></a>Robustní programování  
  
-   V předchozím příkladu, příkaz:  
  
     [!code-csharp[csProgGuideStatements#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_2.cs)]  
  
     provede konverzi `RomanNumeral` k `BinaryNumeral`. Protože neexistuje žádný přímý převod z `RomanNumeral` k `BinaryNumeral`, přetypování se používá k převodu z `RomanNumeral` do `int`a jiné přetypování pro převod z `int` k `BinaryNumeral`.  
  
-   Také – příkaz  
  
     [!code-csharp[csProgGuideStatements#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_3.cs)]  
  
     provede konverzi `BinaryNumeral` k `RomanNumeral`. Protože `RomanNumeral` definuje implicitní převod z `BinaryNumeral`, žádné přetypování je povinný.  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory převodu](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
