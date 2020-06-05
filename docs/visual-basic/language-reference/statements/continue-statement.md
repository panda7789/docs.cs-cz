---
title: Continue – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: fd604b281a590073a5e76398788d7648cadd145c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84382091"
---
# <a name="continue-statement-visual-basic"></a>Continue – příkaz (Visual Basic)
Okamžitě přenese řízení na další iteraci smyčky.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a>Poznámky  
 Z smyčky dovnitř, nebo můžete přenášet `Do` `For` `While` do další iterace této smyčky. Řízení se okamžitě předává do testu podmínky smyčky, který je ekvivalentní k přenosu do `For` příkazu nebo nebo `While` k `Do` `Loop` příkazu nebo, který obsahuje `Until` `While` klauzuli OR.  
  
 Můžete použít v `Continue` jakémkoli umístění smyčky, která umožňuje přenosy. Pravidla umožňující přenos řízení se shodují s [příkazem goto](goto-statement.md).  
  
 Například pokud je smyčka úplně obsažena v `Try` bloku, `Catch` bloku nebo `Finally` bloku, můžete použít `Continue` k přenosu mimo smyčku. Je-li na druhé straně `Try` Struktura... `End Try` obsažena v rámci smyčky, nelze použít `Continue` k přenosu řízení mimo `Finally` blok a lze jej použít k přenosu z `Try` bloku nebo pouze v případě, že `Catch` se přenáší zcela ze `Try` struktury... `End Try` .  
  
 Pokud máte vnořené smyčky stejného typu, například `Do` smyčka v rámci jiné `Do` smyčky, `Continue Do` příkaz se přeskočí na další iteraci nejvnitřnější `Do` smyčky, která ho obsahuje. Nelze použít `Continue` k přeskočení na další iteraci obsahující smyčky stejného typu.  
  
 Máte-li vnořené smyčky různých typů, například `Do` smyčka ve `For` smyčce, můžete přeskočit na další iteraci smyčky buď pomocí `Continue Do` nebo `Continue For` .  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá `Continue While` příkaz k přeskočení na další sloupec pole, pokud je dělitel nula. `Continue While`Je uvnitř `For` smyčky. Převede na `While col < lastcol` příkaz, což je další iterace nejvnitřnější `While` smyčky, která obsahuje `For` smyčku.  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>Viz také

- [Do...Loop – příkaz](do-loop-statement.md)
- [For...Next – příkaz](for-next-statement.md)
- [While...End While – příkaz](while-end-while-statement.md)
- [Try...Catch....Finally – příkaz](try-catch-finally-statement.md)
