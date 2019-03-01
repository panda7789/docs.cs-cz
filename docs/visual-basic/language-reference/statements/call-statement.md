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
ms.openlocfilehash: 6d8fd8060789c4035fd38e41c5de7e43f6330e64
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977016"
---
# <a name="call-statement-visual-basic"></a>Call – příkaz (Visual Basic)
Přenosy ovládacího prvku `Function`, `Sub`, nebo procedura dynamická knihovna (DLL).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a>Součásti  
|||
|---|---|
|`procedureName`|Povinný parametr. Název procedury pro volání.|
|`argumentList`|Volitelné. Seznam proměnných a výrazů představujících argumenty, které jsou předány na postup, když je volána. Více argumentů jsou odděleny čárkami. Pokud zahrnete `argumentList`, je nutné uzavřít do závorek.|
|||
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `Call` – klíčové slovo při volání procedury. Pro většinu volání procedur není nutné používat toto klíčové slovo.  
  
 Obvykle se používá `Call` – klíčové slovo volané výrazu nelze spustit s identifikátorem. Použití `Call` – klíčové slovo pro jiné účely se nedoporučuje.  
  
 Pokud se proces vrátí hodnotu, která `Call` příkaz zahodí ji.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje dva příklady kde `Call` – klíčové slovo je potřeba volání procedury. V obou příkladech nezačíná názvem výraz identifikátor.  
  
 [!code-vb[VbVbalrStatements#97](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#97)]  
  
## <a name="see-also"></a>Viz také:
- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Výrazy lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
