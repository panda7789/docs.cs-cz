---
title: ~ – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- ~_CSharpKeyword
helpviewer_keywords:
- tilde (~) one's complement operator [C#]
- ~ operator [C#]
- ~ [C#], bitwise complement operator
- bitwise complement operator [C#]
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
ms.openlocfilehash: 25b157fafde7d2b75cd8b112848a01e9b3fb0db2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a>~ – operátor (Referenční dokumentace jazyka C#)
`~` Operátor provádí operaci bitového doplňku na jeho operand, což má za následek Prohodit každý bit. Operátory bitového doplňku jsou předdefinované pro [int](../../../csharp/language-reference/keywords/int.md), [Celé_číslo](../../../csharp/language-reference/keywords/uint.md), [dlouho](../../../csharp/language-reference/keywords/long.md), a [ulong](../../../csharp/language-reference/keywords/ulong.md).  
  
> [!NOTE]
>  `~` Symbol také se používá k deklaraci finalizační metody. Další informace najdete v tématu [finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md).  
  
## <a name="remarks"></a>Poznámky  
 Uživatelem definované typy může přetížit `~` operátor. Další informace najdete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md). Operace u celočíselných typů jsou obecně povoleny na výčtu.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#25](../../../csharp/language-reference/operators/codesnippet/CSharp/bitwise-complement-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)  
 [Finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md)
