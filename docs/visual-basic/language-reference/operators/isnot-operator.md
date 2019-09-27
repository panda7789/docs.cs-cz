---
title: IsNot – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 7e1ac1004e671f592c03bd44ee7ec2e8cc572933
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71331621"
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
- [Postupy: Otestuje, zda jsou dva objekty stejné @ no__t-0
