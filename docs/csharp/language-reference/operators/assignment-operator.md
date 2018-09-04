---
title: = – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 9cd1af400a9afdb7942a49dee7e7f7bb78387f2d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507351"
---
# <a name="-operator-c-reference"></a>= – operátor (Referenční dokumentace jazyka C#)
Operátor přiřazení (`=`) ukládá hodnota jeho operandu pravé v umístění úložiště, vlastnost nebo indexer udávají jeho operand na levé straně a jako svůj výsledek vrátí hodnotu. Operandy musí být stejného typu (nebo zpracovával pravý operand musí být implicitně převoditelná na typ operandu vlevo).  
  
## <a name="remarks"></a>Poznámky  
 Operátor přiřazení nelze přetížit. Ale můžete definovat operátory implicitního převodu typu, které vám umožní použít operátor přiřazení s těmito typy. Další informace najdete v tématu [použití operátorů převodu](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#49](../../../csharp/language-reference/operators/codesnippet/CSharp/assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
