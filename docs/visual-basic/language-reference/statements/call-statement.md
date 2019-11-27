---
title: Call – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
ms.openlocfilehash: 7de194ea23827e08c49f4519c1000708a4bd91b4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350164"
---
# <a name="call-statement-visual-basic"></a>Call – příkaz (Visual Basic)

Přenáší řízení do procedury `Function`, `Sub`nebo dynamické knihovny (DLL).  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a>Součásti  

|||
|---|---|
|`procedureName`|Požadováno. Název procedury, kterou chcete volat.|
|`argumentList`|Volitelná. Seznam proměnných nebo výrazů představujících argumenty, které jsou předány proceduře při volání. Více argumentů je odděleno čárkami. Pokud zahrnete `argumentList`, musíte ho uzavřít do závorek.|
|||
  
## <a name="remarks"></a>Poznámky

 Klíčové slovo `Call` lze použít při volání procedury. U většiny volání procedur nemusíte používat toto klíčové slovo.

 Klíčové slovo `Call` obvykle používáte, pokud se pojmenovaný výraz nespustí s identifikátorem. Použití klíčového slova `Call` pro jiné použití se nedoporučuje.

 Pokud procedura vrátí hodnotu, příkaz `Call` ji zahodí.

## <a name="example"></a>Příklad

 Následující kód ukazuje dva příklady, kde klíčové slovo `Call` je nezbytné pro volání procedury. V obou příkladech se u volaného výrazu nezahájí identifikátor.

 [!code-vb[VbVbalrStatements#97](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#97)]  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Function](function-statement.md)
- [Příkaz Sub](sub-statement.md)
- [Příkaz Declare](declare-statement.md)
- [Výrazy lambda](../../programming-guide/language-features/procedures/lambda-expressions.md)
