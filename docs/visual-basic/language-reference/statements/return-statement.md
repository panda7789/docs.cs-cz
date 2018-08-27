---
title: Return – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: fe200add4e29fe4bbe0fdf335dcd94107b8ff1eb
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932589"
---
# <a name="return-statement-visual-basic"></a>Return – příkaz (Visual Basic)
Vrátí ovládací prvek kódu, který volá `Function`, `Sub`, `Get`, `Set`, nebo `Operator` postup.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a>Část  
 `expression`  
 Vyžaduje `Function`, `Get`, nebo `Operator` postup. Výraz, který představuje hodnotu, která má být vrácen volajícímu kódu.  
  
## <a name="remarks"></a>Poznámky  
 V `Sub` nebo `Set` postupu `Return` příkaz je ekvivalentní `Exit Sub` nebo `Exit Property` příkaz, a `expression` nesmí být zadaný.  
  
 V `Function`, `Get`, nebo `Operator` postupu `Return` musí obsahovat příkaz `expression`, a `expression` se musí vyhodnotit na datový typ, který lze převést na typ vrácené hodnoty procedury. V `Function` nebo `Get` postup, budete mít taky alternativní přiřazení výraz pro název procedury, která bude sloužit jako návratovou hodnotu a potom provádění `Exit Function` nebo `Exit Property` příkazu. V `Operator` postup, musíte použít `Return expression`.  
  
 Můžete vytvořit tolik `Return` příkazy podle potřeby ve stejné proceduře.  
  
> [!NOTE]
>  Kód v `Finally` blok se spustí po `Return` příkaz v `Try` nebo `Catch` blok je došlo k chybě, ale před tímto `Return` spuštění příkazů. A `Return` nemůže být součástí příkazu `Finally` bloku.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Return` příkaz několikrát k vrácení volajícímu kódu, když není potřeba dělat nic dalšího postupu.  
  
 [!code-vb[VbVbalrStatements#53](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/return-statement_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Příkaz Get](../../../visual-basic/language-reference/statements/get-statement.md)  
 [Příkaz Set](../../../visual-basic/language-reference/statements/set-statement.md)  
 [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Příkaz Exit](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Příkaz Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
