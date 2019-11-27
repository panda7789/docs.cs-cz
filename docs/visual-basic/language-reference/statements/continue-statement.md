---
title: Continue – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: 20140cafb68c7e5518bf3d5fa80e56ca1c1de2c6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354114"
---
# <a name="continue-statement-visual-basic"></a>Continue – příkaz (Visual Basic)
Okamžitě přenese řízení na další iteraci smyčky.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a>Poznámky  
 Můžete přenášet z `Do`, `For`nebo `While` smyčky do další iterace této smyčky. Řízení se okamžitě předává do testu podmínky smyčky, který je ekvivalentní k přenosu do příkazu `For` nebo `While` nebo k příkazu `Do` nebo `Loop`, který obsahuje klauzuli `Until` nebo `While`.  
  
 `Continue` můžete použít v jakémkoli umístění smyčky, která umožňuje přenosy. Pravidla umožňující přenos řízení se shodují s [příkazem goto](../../../visual-basic/language-reference/statements/goto-statement.md).  
  
 Například pokud je smyčka úplně obsažena v bloku `Try`, bloku `Catch` nebo bloku `Finally`, můžete použít `Continue` k přenosu ze smyčky. Je-li na druhé straně struktura `Try`...`End Try` obsažena v rámci smyčky, nelze použít `Continue` k přenosu řízení z bloku `Finally` a můžete jej použít k přenosu z `Try` nebo `Catch` bloku pouze v případě, že jste přenesli z `Try`struktury...`End Try`.  
  
 Pokud máte vnořené smyčky stejného typu, například `Do` smyčka v rámci jiné smyčky `Do`, příkaz `Continue Do` skočí na další iteraci nejvnitřnějšího `Do` cyklu, který jej obsahuje. `Continue` nelze použít k přeskočení na další iteraci obsahující smyčky stejného typu.  
  
 Pokud máte vnořené smyčky různých typů, například `Do` smyčka v rámci `For` smyčky, můžete přeskočit na další iteraci smyčky buď pomocí `Continue Do` nebo `Continue For`.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá příkaz `Continue While` pro přechod k dalšímu sloupci pole, je-li dělitel nula. `Continue While` je uvnitř smyčka `For`. Přenáší na příkaz `While col < lastcol`, což je další iterace nejvnitřnější `While` smyčky, která obsahuje `For` smyčku.  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Příkaz For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Příkaz While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Příkaz Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
