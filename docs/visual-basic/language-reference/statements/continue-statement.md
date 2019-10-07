---
title: Continue – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: 9ee5fb19db6eafeb7e4bed12935d0b950d6368d6
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005100"
---
# <a name="continue-statement-visual-basic"></a>Continue – příkaz (Visual Basic)
Okamžitě přenese řízení na další iteraci smyčky.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a>Poznámky  
 V rámci smyčky `Do`, `For` nebo `While` se můžete přenést do další iterace této smyčky. Řízení se okamžitě předává do testu podmínky smyčky, který odpovídá přenosu do příkazu `For` nebo `While` nebo do příkazu `Do` nebo `Loop`, který obsahuje klauzuli `Until` nebo `While`.  
  
 Můžete použít `Continue` v jakémkoli umístění smyčky, která umožňuje přenosy. Pravidla umožňující přenos řízení se shodují s [příkazem goto](../../../visual-basic/language-reference/statements/goto-statement.md).  
  
 Například pokud je smyčka úplně obsažena v bloku `Try`, bloku `Catch` nebo bloku `Finally`, můžete k přenosu ze smyčky použít `Continue`. Je-li na druhé straně struktura `Try`... `End Try` obsažena v rámci smyčky, nelze použít `Continue` pro přenos řízení z bloku `Finally` a můžete ho použít k přenosu z bloku `Try` nebo `Catch` pouze v případě, že jste přenesli zcela z @no_ – 6... `End Try` struktura.  
  
 Pokud máte vnořené smyčky stejného typu, například smyčka `Do` v rámci jiné smyčky `Do`, příkaz `Continue Do` přeskočí na další iteraci nejvnitřnější smyčky `Do`, která ho obsahuje. @No__t-0 nelze použít k přeskočení na další iteraci obsahující smyčky stejného typu.  
  
 Pokud máte vnořené smyčky různých typů, například smyčka `Do` v rámci smyčky `For`, můžete přeskočit na další iteraci smyčky buď pomocí `Continue Do` nebo `Continue For`.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá příkaz `Continue While` k přeskočení na další sloupec pole, pokud je dělitel nula. @No__t-0 je uvnitř smyčky `For`. Přenáší na příkaz `While col < lastcol`, což je další iterace nejvnitřnější smyčky "`While`", která obsahuje smyčku `For`.  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Příkaz For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Příkaz While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Příkaz Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
