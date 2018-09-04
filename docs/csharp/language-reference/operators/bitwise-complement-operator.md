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
ms.openlocfilehash: 8af25217f9e7e66796192783a0b8e3415604dc90
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510108"
---
# <a name="-operator-c-reference"></a>~ – operátor (Referenční dokumentace jazyka C#)
`~` Operátor provádí operaci s bitový doplněk svého operandu, což má za následek vrácení každý bit. Operátory bitového doplňku jsou předdefinované pro [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [dlouhé](../../../csharp/language-reference/keywords/long.md), a [ulong](../../../csharp/language-reference/keywords/ulong.md).  
  
> [!NOTE]
>  `~` Symbol se také používá k deklaraci finalizační metody. Další informace najdete v tématu [finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md).  
  
## <a name="remarks"></a>Poznámky  
 Lze přetěžovat uživatelsky definované typy `~` operátor. Další informace najdete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md). Operace interních typů jsou obecně povoleny na výčet.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#25](../../../csharp/language-reference/operators/codesnippet/CSharp/bitwise-complement-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)  
- [Finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md)
