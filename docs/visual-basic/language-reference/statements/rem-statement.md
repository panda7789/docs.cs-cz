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
ms.openlocfilehash: a3ad63472f6a3f7ae1ec13742185790667c7bcf0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54699048"
---
# <a name="rem-statement-visual-basic"></a>REM – příkaz (Visual Basic)
Používá se k zahrnutí poznámky vysvětlující ve zdrojovém kódu programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
REM comment  
' comment  
```  
  
## <a name="parts"></a>Součásti  
 `comment`  
 Volitelné. Text všechny komentáře, které chcete zahrnout. Mezera mezi vyžádáním `REM` – klíčové slovo a `comment`.  
  
## <a name="remarks"></a>Poznámky  
 Můžete vložit `REM` příkaz samostatně na řádku, nebo můžete umístit na řádek po jiného příkazu. `REM` Příkaz musí být poslední příkaz na řádku. Pokud následuje jiný příkaz, `REM` musí být odděleny od, který tento příkaz oddělte mezerou.  
  
 Můžete použít jednoduchou uvozovkou (`'`) namísto `REM`. To platí, jestli váš komentář následuje jiný příkaz na stejném řádku nebo samostatně uložených na řádku.  
  
> [!NOTE]
>  Nejde pokračovat `REM` příkaz s použitím posloupností pokračování řádku (`_`). Po zahájení komentář, kompilátor nezkoumá znaků pro zvláštní význam. Komentář k více řádků, použijte jiný `REM` příkazu nebo symbol komentáře (`'`) na každém řádku.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, `REM` příkaz, který se používá k zahrnutí do programu poznámky vysvětlující. Ukazuje také použití znak jednoduché uvozovky (`'`) namísto `REM`.  
  
 [!code-vb[VbVbalrStatements#6](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/rem-statement_1.vb)]  
  
## <a name="see-also"></a>Viz také:
- [Komentáře v kódu](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)
- [Postupy: Přerušení a kombinování příkazů v kódu](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
