---
title: IsNot – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- comparison operators [Visual Basic]
- TypeOf...IsNot expression
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: ea978f8874cee20fb3a005189fd846f7564da777
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811038"
---
# <a name="isnot-operator-visual-basic"></a>IsNot – operátor (Visual Basic)

Porovná dvě proměnné odkazu na objekt.

## <a name="syntax"></a>Syntax

```vb
result = object1 IsNot object2
```

## <a name="parts"></a>Součásti

- `result`

  Povinná hodnota. `Boolean`Hodnota.

- `object1`

  Povinná hodnota. Jakákoli `Object` proměnná nebo výraz.

- `object2`

  Povinná hodnota. Jakákoli `Object` proměnná nebo výraz.

## <a name="remarks"></a>Poznámky

`IsNot`Operátor určuje, zda dva odkazy na objekt odkazují na různé objekty. Ale neprovádí porovnávání hodnot. Pokud `object1` a `object2` obě odkazují na přesnou stejnou instanci objektu, `result` je `False` . Pokud ne, `result` je `True` .

`IsNot` je opakem `Is` operátoru. Výhodou `IsNot` je, že se můžete vyhnout nevhodným syntaxem s `Not` a `Is` , což může být obtížné ho přečíst.

 Operátory a můžete použít `Is` `IsNot` k otestování objektů s časnou vazbou i s pozdní vazbou.

## <a name="example"></a>Příklad

Následující příklad kódu používá `Is` operátor i `IsNot` operátor k provedení stejného porovnání.

[!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="use-typeof-operator-with-isnot-operator"></a>Použití operátoru TypeOf s operátorem IsNot

Počínaje Visual Basic 14 můžete `TypeOf` operátor s `IsNot` operátorem použít k otestování, zda objekt není kompatibilní s datovým typem. *not* Příklad:

```vb
If TypeOf sender IsNot Button Then
```

## <a name="see-also"></a>Viz také

- [Is – operátor](is-operator.md)
- [TypeOf – operátor](typeof-operator.md)
- [Priorita operátorů v jazyce Visual Basic](operator-precedence.md)
- [Postupy: Test, zda jsou dva objekty stejné.](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
