---
title: IsNot – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 616506f64d20e1f150b443433f1b69040136a5ba
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336066"
---
# <a name="isnot-operator-visual-basic"></a>IsNot – operátor (Visual Basic)

Porovná dvě proměnné odkazu na objekt.

## <a name="syntax"></a>Syntaxe

```vb
result = object1 IsNot object2
```

## <a name="parts"></a>Součásti
 `result` nutné. Hodnota `Boolean`.

 `object1` nutné. Jakákoli `Object`ová proměnná nebo výraz.

 `object2` nutné. Jakákoli `Object`ová proměnná nebo výraz.

## <a name="remarks"></a>Poznámky
 Operátor `IsNot` určuje, zda dva odkazy na objekt odkazují na různé objekty. Ale neprovádí porovnávání hodnot. Pokud `object1` a `object2` odkazují na přesnou stejnou instanci objektu, `result` je `False`; Pokud ne, `result` je `True`.

 `IsNot` je opakem operátoru `Is`. Výhodou `IsNot` je, že se můžete vyhnout nevhodným syntaxem s `Not` a `Is`, což může být obtížné přečíst.

 Operátory `Is` a `IsNot` můžete použít k otestování objektů s časnou vazbou i s pozdní vazbou.

## <a name="example"></a>Příklad
 Následující příklad kódu používá operátor `Is` a operátor `IsNot` k provedení stejného porovnání.

 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="see-also"></a>Viz také:

- [Operátor Is](is-operator.md)
- [Operátor Typeof](typeof-operator.md)
- [Priorita operátorů v Visual Basic](operator-precedence.md)
- [Postupy: Test, zda jsou dva objekty stejné](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
