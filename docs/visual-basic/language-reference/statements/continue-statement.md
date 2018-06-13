---
title: Continue – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: eb8596c43bf6232eec4bcb844e6202c5de373404
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602720"
---
# <a name="continue-statement-visual-basic"></a>Continue – příkaz (Visual Basic)
Řízení přenosů okamžitě do další iterace smyčky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a>Poznámky  
 Můžete přenést z uvnitř `Do`, `For`, nebo `While` smyčky do další iterace této smyčky. Řízení předává okamžitě do testu podmínku smyčky, která je ekvivalentní přenosu do `For` nebo `While` prohlášení, nebo `Do` nebo `Loop` příkazu, který obsahuje `Until` nebo `While` klauzule.  
  
 Můžete použít `Continue` v libovolném umístění ve smyčce, která umožňuje přenosy. Pravidla umožňující přenos řízení jsou stejné jako s [GoTo – příkaz](../../../visual-basic/language-reference/statements/goto-statement.md).  
  
 Například, pokud je zcela obsažené v rámci smyčku `Try` bloku `Catch` bloku nebo `Finally` blok, můžete použít `Continue` přenos mimo smyčku. Pokud na druhé straně, `Try`... `End Try` struktura je obsažena v smyčky, nemůžete použít `Continue` přenos řízení z `Finally` blok a může použít k přenosu z `Try` nebo `Catch` blokovat jenom při přenosu zcela z `Try`... `End Try` struktura.  
  
 Pokud máte vnořené smyčky stejného typu, například `Do` smyčky v rámci jiného `Do` smyčky, `Continue Do` příkaz přeskočí na další iterace nejvnitřnější `Do` smyčky, který jej obsahuje. Nemůžete použít `Continue` tak, aby přeskočil do další iterace smyčky obsahující stejného typu.  
  
 Pokud například máte vnořené smyčky různých typů `Do` cykly v rámci `For` smyčku, můžete přejít na další iterace buď smyčky pomocí `Continue Do` nebo `Continue For`.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá `Continue While` příkaz a přejděte k další sloupec pole, pokud dělitel je nulová. `Continue While` Je uvnitř `For` smyčky. Přenosu do `While col < lastcol` příkaz, který je další iterace nejvnitřnější `While` smyčky, který obsahuje `For` smyčky.  
  
 [!code-vb[VbVbalrStatements#14](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/continue-statement_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [Příkaz For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Příkaz While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [Příkaz Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
