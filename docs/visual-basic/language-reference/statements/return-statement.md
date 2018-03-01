---
title: "Return – příkaz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b66d16a249164b8989f05f10c785b97055bfde9e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="return-statement-visual-basic"></a>Return – příkaz (Visual Basic)
Vrátí ovládací prvek na kód, který volá `Function`, `Sub`, `Get`, `Set`, nebo `Operator` postupu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a>Část  
 `expression`  
 V požadován `Function`, `Get`, nebo `Operator` postupu. Výraz, který představuje hodnotu, která má být vrácen pro volací kód.  
  
## <a name="remarks"></a>Poznámky  
 V `Sub` nebo `Set` postupu `Return` příkaz je ekvivalentní `Exit Sub` nebo `Exit Property` příkaz, a `expression` nesmí být zadaný.  
  
 V `Function`, `Get`, nebo `Operator` postupu `Return` musí zahrnovat příkaz `expression`, a `expression` se musí vyhodnotit datový typ, který je převést na návratový typ procedury. V `Function` nebo `Get` postup, můžete si taky alternativní přiřazování výraz název procedury, která bude sloužit jako návratovou hodnotu a pak provedením `Exit Function` nebo `Exit Property` příkaz. V `Operator` postup, musíte použít `Return``expression`.  
  
 Můžete zahrnout tolik `Return` příkazy podle potřeby v stejným způsobem.  
  
> [!NOTE]
>  Kód v `Finally` bloku se spouští po `Return` příkaz v `Try` nebo `Catch` blok je zjištěno, ale před `Return` provede příkaz. A `Return` nemůže být součástí příkazu `Finally` bloku.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Return` příkaz několikrát vrácené volání kódu v případě postup není potřeba dělat žádné další kroky.  
  
 [!code-vb[VbVbalrStatements#53](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/return-statement_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub – příkaz](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Get – příkaz](../../../visual-basic/language-reference/statements/get-statement.md)  
 [Set – příkaz](../../../visual-basic/language-reference/statements/set-statement.md)  
 [Operator – příkaz](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Exit – příkaz](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Try... Catch... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
