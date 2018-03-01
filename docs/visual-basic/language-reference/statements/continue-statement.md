---
title: "Continue – příkaz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4a47819600a6c1d58f09c2f8ed3443632e9dab68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Provést... Příkaz smyčky](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [Pro... Next – příkaz](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Chvíli... End While – příkaz](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [Try... Catch... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
