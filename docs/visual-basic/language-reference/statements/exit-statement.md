---
title: Exit – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Exit
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- Exit statement [Visual Basic]
- program termination
- execution [Visual Basic], stopping
ms.assetid: 760bfb32-5c3f-4bdb-a432-9a6001c92db7
ms.openlocfilehash: 1f386694bd7425ee530b9305ab684b730f9b73c8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638113"
---
# <a name="exit-statement-visual-basic"></a>Exit – příkaz (Visual Basic)
Ukončí proceduru nebo blok a okamžitě přenese ovládací prvek do příkazu za voláním procedury nebo definicí bloku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Exit { Do | For | Function | Property | Select | Sub | Try | While }  
```  
  
## <a name="statements"></a>Příkazy  
 `Exit Do`  
 Okamžitě ukončí `Do` smyčky v kterém se zobrazí. Provádění pokračuje pomocí následujícího příkazu `Loop` příkazu. `Exit Do` může být použit pouze uvnitř `Do` smyčky. Při použití v rámci vnořené `Do` smyčky, `Exit Do` ukončení vnitřní smyčky a přenese ovládací prvek na další vyšší úroveň vnoření.  
  
 `Exit For`  
 Okamžitě ukončí `For` smyčky v kterém se zobrazí. Provádění pokračuje pomocí následujícího příkazu `Next` příkazu. `Exit For` může být použit pouze uvnitř `For`... `Next` nebo `For Each`... `Next` smyčky. Při použití v rámci vnořené `For` smyčky, `Exit For` ukončení vnitřní smyčky a přenese ovládací prvek na další vyšší úroveň vnoření.  
  
 `Exit Function`  
 Okamžitě ukončí `Function` procedura, ve kterém se zobrazí. Pokračuje s příkazu za příkazem, který volá se, `Function` postup. `Exit Function` může být použit pouze uvnitř `Function` postup.  
  
 K určení návratovou hodnotu, můžete přiřadit hodnotu k názvu funkce na řádku před `Exit Function` příkazu. Pro přiřazení návratovou hodnotu a ukončení funkce v jednom příkazu, můžete místo toho použít [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 `Exit Property`  
 Okamžitě ukončí `Property` procedura, ve kterém se zobrazí. Provádění pokračuje s příkazem, který volá `Property` procedury, to znamená, s příkazem požádat nebo nastavení hodnoty vlastnosti. `Exit Property` může být použit pouze uvnitř vlastnosti `Get` nebo `Set` postup.  
  
 K určení návratovou hodnotu v `Get` postup, můžete přiřadit hodnotu k názvu funkce na řádku před `Exit Property` příkazu. K přiřazení návratovou hodnotu a ukončení `Get` postupu v jednom příkazu, můžete místo toho použít `Return` příkazu.  
  
 V `Set` postupu `Exit Property` je ekvivalentní příkazu `Return` příkazu.  
  
 `Exit Select`  
 Okamžitě ukončí `Select Case` blok, ve kterém se zobrazí. Provádění pokračuje pomocí následujícího příkazu `End Select` příkazu. `Exit Select` může být použit pouze uvnitř `Select Case` příkazu.  
  
 `Exit Sub`  
 Okamžitě ukončí `Sub` procedura, ve kterém se zobrazí. Pokračuje s příkazu za příkazem, který volá se, `Sub` postup. `Exit Sub` může být použit pouze uvnitř `Sub` postup.  
  
 V `Sub` postupu `Exit Sub` je ekvivalentní příkazu `Return` příkazu.  
  
 `Exit Try`  
 Okamžitě ukončí `Try` nebo `Catch` blok, ve kterém se zobrazí. Provádění pokračuje `Finally` blokovat, pokud existuje, nebo pomocí následujícího příkazu `End Try` příkaz jinak. `Exit Try` může být použit pouze uvnitř `Try` nebo `Catch` bloku a ne uvnitř `Finally` bloku.  
  
 `Exit While`  
 Okamžitě ukončí `While` smyčky v kterém se zobrazí. Provádění pokračuje pomocí následujícího příkazu `End While` příkazu. `Exit While` může být použit pouze uvnitř `While` smyčky. Při použití v rámci vnořené `While` smyčky, `Exit While` předá řízení smyčky, která je jednu úroveň vnořeného nad smyčky kde `Exit While` dojde k.  
  
## <a name="remarks"></a>Poznámky  
 Nezaměňujte `Exit` příkazy `End` příkazy. `Exit` konec příkazu není definován.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu podmínka smyčky zastaví smyčky při `index` proměnnou je větší než 100. `If` Příkaz ve smyčce, ale způsobí, že `Exit Do` příkaz zastaví smyčky, pokud indexovaná proměnná je větší než 10.  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a>Příklad  
 Následující příklad přiřadí název funkce návratová hodnota `myFunction`a potom použije `Exit Function` vrácení z funkce.  
  
 [!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md) přiřazovat návratovou hodnotu a ukončení funkce.  
  
 [!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Continue](../../../visual-basic/language-reference/statements/continue-statement.md)
- [Příkaz Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Příkaz End](../../../visual-basic/language-reference/statements/end-statement.md)
- [Příkaz For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [Příkaz For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md)
- [Příkaz Stop](../../../visual-basic/language-reference/statements/stop-statement.md)
- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Příkaz Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
