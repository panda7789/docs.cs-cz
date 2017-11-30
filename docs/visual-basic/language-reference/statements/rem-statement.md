---
title: "REM – příkaz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.'
- vb.Rem
- Rem
- "'"
helpviewer_keywords:
- REM statement [Visual Basic]
- comments, Visual Basic code
- code comments, Visual Basic
- Visual Basic code, comments
- "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d64ce970e3e74437f5e8c63c8a4d578900902192
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="rem-statement-visual-basic"></a>REM – příkaz (Visual Basic)
Umožňuje zahrnout poznámky vysvětlující ve zdrojovém kódu programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
REM comment  
' comment  
```  
  
## <a name="parts"></a>Součásti  
 `comment`  
 Volitelné. Text jakékoli komentáře, které chcete zahrnout. Je vyžadován mezi mezeru `REM` – klíčové slovo a `comment`.  
  
## <a name="remarks"></a>Poznámky  
 Můžete vložit `REM` příkaz samostatně na řádku, nebo ji umístit na řádku za jiný příkaz. `REM` Příkaz musí být poslední příkaz v řádku. Pokud postupuje jiný příkaz `REM` musí být oddělené od tohoto příkazu mezerou.  
  
 Můžete provádět jednoduché uvozovky (`'`) místo `REM`. To platí, jestli váš komentář následuje jiný příkaz na stejném řádku umístěn nebo samostatně na řádek.  
  
> [!NOTE]
>  Nelze pokračovat, `REM` příkaz s použitím posloupnost pokračování řádku (`_`). Jakmile začne komentář, kompilátor není zkontrolujte znaků pro zvláštní význam. Pro více řádků komentář, použít jiný `REM` příkaz nebo symbol komentáře (`'`) na každém řádku.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `REM` příkaz, který se používá k zahrnují vysvětlující poznámky v programu. Také ukazuje použití znak jednoduché uvozovky (`'`) místo `REM`.  
  
 [!code-vb[VbVbalrStatements#6](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/rem-statement_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Komentáře v kódu](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 [Postupy: přerušení a kombinace příkazů v kódu](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
