---
title: IsNot – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 32e8f9532244679d2994b0e3d98279d75f7e77b4
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701041"
---
# <a name="isnot-operator-visual-basic"></a>IsNot – operátor (Visual Basic)

Porovná dvě proměnné odkazu na objekt.

## <a name="syntax"></a>Syntaxe

```vb
result = object1 IsNot object2
```

## <a name="parts"></a>Součásti
 Vyžaduje se `result`. Hodnota `Boolean`.

 Vyžaduje se `object1`. Jakákoli proměnná nebo výraz `Object`.

 Vyžaduje se `object2`. Jakákoli proměnná nebo výraz `Object`.

## <a name="remarks"></a>Poznámky
 Operátor `IsNot` určuje, zda dva odkazy na objekt odkazují na různé objekty. Ale neprovádí porovnávání hodnot. Pokud `object1` a `object2` odkazují na přesnou stejnou instanci objektu, `result` je `False`; Pokud ne, `result` je `True`.

 `IsNot` je opakem operátoru `Is`. Výhodou `IsNot` je, že se můžete vyhnout nevhodným syntaxem `Not` a `Is`, což může být obtížné přečíst.

 Operátory `Is` a `IsNot` můžete použít k otestování objektů s časnou vazbou i s pozdní vazbou.

## <a name="example"></a>Příklad
 Následující příklad kódu používá operátor `Is` a operátor `IsNot` k provedení stejného porovnání.

 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="see-also"></a>Viz také:

- [Operátor Is](is-operator.md)
- [Operátor Typeof](typeof-operator.md)
- [Priorita operátorů v Visual Basic](operator-precedence.md)
- [Postupy: Test, zda jsou dva objekty stejné](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
