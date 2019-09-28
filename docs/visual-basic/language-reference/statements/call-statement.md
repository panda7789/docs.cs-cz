---
title: Call – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
ms.openlocfilehash: af0b62d6cfacbcf94f527e049e07e51bf496a6cf
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392756"
---
# <a name="call-statement-visual-basic"></a>Call – příkaz (Visual Basic)

Přenáší řízení na proceduru `Function`, `Sub` nebo Dynamic-Link Library (DLL).

## <a name="syntax"></a>Syntaxe

```vb
[ Call ] procedureName [ (argumentList) ]
```

## <a name="parts"></a>Součásti

|||
|---|---|
|`procedureName`|Povinný parametr. Název procedury, kterou chcete volat.|
|`argumentList`|Volitelný parametr. Seznam proměnných nebo výrazů představujících argumenty, které jsou předány proceduře při volání. Více argumentů je odděleno čárkami. Pokud zahrnete `argumentList`, musíte ho uzavřít do závorek.|
|||
  
## <a name="remarks"></a>Poznámky

 Při volání procedury můžete použít klíčové slovo `Call`. U většiny volání procedur nemusíte používat toto klíčové slovo.

 Pokud pojmenovaný výraz nezačíná identifikátorem, obvykle se používá klíčové slovo `Call`. Použití klíčového slova `Call` pro jiné použití se nedoporučuje.

 Pokud procedura vrátí hodnotu, příkaz `Call` ho zahodí.

## <a name="example"></a>Příklad

 Následující kód ukazuje dva příklady, kde klíčové slovo `Call` je nezbytné pro volání procedury. V obou příkladech se u volaného výrazu nezahájí identifikátor.

 [!code-vb[VbVbalrStatements#97](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#97)]  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Function](function-statement.md)
- [Příkaz Sub](sub-statement.md)
- [Příkaz Declare](declare-statement.md)
- [Výrazy lambda](../../programming-guide/language-features/procedures/lambda-expressions.md)
