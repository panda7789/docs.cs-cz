---
title: REM – příkaz (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 3bd526b08e1ba3be856e1e823cf8ef49ea9b6c97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
 [Postupy: Přerušení a kombinace příkazů v kódu](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
