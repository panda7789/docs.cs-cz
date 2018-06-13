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
ms.openlocfilehash: 05a65dd84a00478f52c8cd7d8b46341644512718
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605274"
---
# <a name="exit-statement-visual-basic"></a>Exit – příkaz (Visual Basic)
Ukončí proceduru nebo bloku a předá řízení příkaz následující volání procedury nebo definici bloku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Exit { Do | For | Function | Property | Select | Sub | Try | While }  
```  
  
## <a name="statements"></a>Příkazy  
 `Exit Do`  
 Okamžitě ukončí `Do` smyčky v zobrazí. Provádění pokračuje následující příkaz `Loop` příkaz. `Exit Do` dá se použít jenom uvnitř `Do` smyčky. Při použití uvnitř vnořené `Do` smyčky, `Exit Do` ukončí nejvnitřnější smyčky a předá řízení další vyšší úroveň vnoření.  
  
 `Exit For`  
 Okamžitě ukončí `For` smyčky v zobrazí. Provádění pokračuje následující příkaz `Next` příkaz. `Exit For` dá se použít jenom uvnitř `For`... `Next` nebo `For Each`... `Next` smyčky. Při použití uvnitř vnořené `For` smyčky, `Exit For` ukončí nejvnitřnější smyčky a předá řízení další vyšší úroveň vnoření.  
  
 `Exit Function`  
 Okamžitě ukončí `Function` postup, ve kterém se zobrazí. Provádění pokračuje příkaz následující příkaz, který volá `Function` postupu. `Exit Function` dá se použít jenom uvnitř `Function` postupu.  
  
 K určení návratovou hodnotu, lze přiřadit hodnotu na řádek před název funkce `Exit Function` příkaz. Pokud chcete přiřadit návratovou hodnotu a ukončete funkce v jednom příkazu, místo toho můžete [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 `Exit Property`  
 Okamžitě ukončí `Property` postup, ve kterém se zobrazí. Provádění pokračuje příkaz, který volá `Property` postup, který je s příkazem požaduje nebo nastavení hodnoty vlastnosti. `Exit Property` dá se použít jenom uvnitř vlastnost `Get` nebo `Set` postupu.  
  
 K určení návratovou hodnotu v `Get` postup, můžete přiřadit hodnotu název funkce na řádku před `Exit Property` příkaz. K přiřazení návratovou hodnotu a ukončení `Get` postup v jednom příkazu, místo toho můžete `Return` příkaz.  
  
 V `Set` postupu `Exit Property` je ekvivalentní příkaz `Return` příkaz.  
  
 `Exit Select`  
 Okamžitě ukončí `Select Case` blok, ve kterém zobrazí. Provádění pokračuje následující příkaz `End Select` příkaz. `Exit Select` dá se použít jenom uvnitř `Select Case` příkaz.  
  
 `Exit Sub`  
 Okamžitě ukončí `Sub` postup, ve kterém se zobrazí. Provádění pokračuje příkaz následující příkaz, který volá `Sub` postupu. `Exit Sub` dá se použít jenom uvnitř `Sub` postupu.  
  
 V `Sub` postupu `Exit Sub` je ekvivalentní příkaz `Return` příkaz.  
  
 `Exit Try`  
 Okamžitě ukončí `Try` nebo `Catch` blok, ve kterém zobrazí. Provádění pokračuje `Finally` blokování, pokud existuje, nebo s následující příkaz `End Try` příkaz, jinak hodnota. `Exit Try` dá se použít jenom uvnitř `Try` nebo `Catch` blok a není uvnitř `Finally` bloku.  
  
 `Exit While`  
 Okamžitě ukončí `While` smyčky v zobrazí. Provádění pokračuje následující příkaz `End While` příkaz. `Exit While` dá se použít jenom uvnitř `While` smyčky. Při použití uvnitř vnořené `While` smyčky, `Exit While` předá řízení smyčky, která je jednu úroveň vnořené nad smyčky kde `Exit While` dojde.  
  
## <a name="remarks"></a>Poznámky  
 Nezaměňujte `Exit` příkazy s `End` příkazy. `Exit` nedefinuje konec příkazu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu smyčku zastaví smyčky při `index` proměnné je větší než 100. `If` Příkaz ve smyčce, ale způsobuje `Exit Do` příkaz k zastavení smyčky do proměnné index je větší než 10.  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_1.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad přiřadí návratovou hodnotu pro název funkce `myFunction`a pak používá `Exit Function` vrátit z funkce.  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_2.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md) přiřadit návratovou hodnotu a ukončení funkce.  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_3.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Continue](../../../visual-basic/language-reference/statements/continue-statement.md)  
 [Příkaz Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [Příkaz End](../../../visual-basic/language-reference/statements/end-statement.md)  
 [Příkaz For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [Příkaz For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md)  
 [Příkaz Stop](../../../visual-basic/language-reference/statements/stop-statement.md)  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Příkaz Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
