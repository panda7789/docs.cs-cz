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
ms.openlocfilehash: 2074f44aedf59f1570e73c898a9bf64e57034923
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="call-statement-visual-basic"></a>Call – příkaz (Visual Basic)
Přenos řízení `Function`, `Sub`, nebo postup dynamická knihovna (DLL).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a>Součásti  
 `procedureName`  
 Požadováno. Název procedury k volání.  
  
 `argumentList`  
 Volitelné. Seznam proměnných nebo výrazů představující argumenty, které se budou předávat procesu při jejím volání. Více argumentů jsou oddělené čárkami. Pokud zahrnete `argumentList`, je nutné uzavřít do závorek.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `Call` – klíčové slovo při volání procedury. Pro většinu volání procedur není nutné používat toto klíčové slovo.  
  
 Obvykle se používá `Call` – klíčové slovo volané výraz nezačíná identifikátor. Použití `Call` – klíčové slovo pro jiné účely se nedoporučuje.  
  
 Pokud postup vrátí hodnotu, `Call` příkaz zruší ho.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje dva příklady kde `Call` – klíčové slovo je potřeba volání procedury. V obou příkladech volané výraz nezačíná identifikátor.  
  
 [!code-vb[VbVbalrStatements#97](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/call-statement_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Výrazy lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
