---
title: Continue – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: 23bb57ec022e62cd586c533d4ed4c792789a0b38
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627002"
---
# <a name="continue-statement-visual-basic"></a>Continue – příkaz (Visual Basic)
Přenosy ovládacího prvku okamžitě na další iteraci smyčky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a>Poznámky  
 Můžete přenášet z uvnitř `Do`, `For`, nebo `While` smyčky na další iteraci smyčky. Ovládací prvek ihned přejde k testovací podmínky smyčky, který je ekvivalentem k přenosu do `For` nebo `While` příkazu, nebo `Do` nebo `Loop` příkazu, který obsahuje `Until` nebo `While` klauzuli.  
  
 Můžete použít `Continue` v libovolném umístění v smyčky, která umožňuje přenosy. Pravidla povolení přenos řízení jsou stejné jako [příkazu GoTo](../../../visual-basic/language-reference/statements/goto-statement.md).  
  
 Například, pokud je zcela obsažený v rámci smyčky `Try` bloku, `Catch` bloku nebo `Finally` blok, můžete použít `Continue` přenos ze smyčky. Pokud na druhou stranu, `Try`... `End Try` struktura je obsažen v rámci smyčky, nebude možné použít `Continue` k přenosu řízení z celkového počtu `Finally` bloku a vy můžete použít k převodu z `Try` nebo `Catch` blokovat jenom v případě, že je úplně přenést z celkového počtu `Try`... `End Try` struktury.  
  
 Pokud třeba máte vnořené smyčky stejného typu `Do` smyčky v jiném `Do` smyčky, `Continue Do` příkaz přeskočí na další iteraci nejvnitřnější `Do` smyčku, která ji obsahuje. Nemůžete použít `Continue` přeskočit na další iteraci smyčky obsahující stejného typu.  
  
 Pokud máte vnořené smyčky různých typů, třeba `Do` smyčky v rámci `For` smyčky, můžete přeskočit na další iteraci smyčky, buď pomocí `Continue Do` nebo `Continue For`.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá `Continue While` příkaz přejděte tak do dalšího sloupce pole, pokud dělitel je nula. `Continue While` Se nachází uvnitř `For` smyčky. Přenese na `While col < lastcol` příkazu, který je na další iteraci nejvnitřnější `While` smyčku, která obsahuje `For` smyčky.  
  
 [!code-vb[VbVbalrStatements#14](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/continue-statement_1.vb)]  
  
## <a name="see-also"></a>Viz také:
- [Příkaz Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Příkaz For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Příkaz While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Příkaz Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
