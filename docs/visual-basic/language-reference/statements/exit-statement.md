---
title: Exit – příkaz
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
ms.openlocfilehash: 1bfe81428fd3c50663fd8978e05c6a945cd47df8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345942"
---
# <a name="exit-statement-visual-basic"></a>Exit – příkaz (Visual Basic)

Ukončí proceduru nebo blok a okamžitě přenese řízení do příkazu za voláním procedury nebo definicí bloku.

## <a name="syntax"></a>Syntaxe

```vb
Exit { Do | For | Function | Property | Select | Sub | Try | While }
```

## <a name="statements"></a>Příkazy

 `Exit Do`  
 Okamžitě ukončí `Do` smyčku, ve které se zobrazí. Provádění pokračuje s příkazem za příkazem `Loop`. `Exit Do` lze použít pouze uvnitř smyčky `Do`. Při použití ve vnořených cyklech `Do` `Exit Do` ukončí vnitřní smyčku a přenáší řízení na další vyšší úroveň vnoření.

 `Exit For`  
 Okamžitě ukončí `For` smyčku, ve které se zobrazí. Provádění pokračuje s příkazem za příkazem `Next`. `Exit For` lze použít pouze uvnitř `For`...`Next` nebo `For Each`...`Next` smyčka. Při použití ve vnořených cyklech `For` `Exit For` ukončí vnitřní smyčku a přenáší řízení na další vyšší úroveň vnoření.

 `Exit Function`  
 Okamžitě ukončí `Function` postup, ve kterém se zobrazí. Provádění pokračuje příkazem po příkazu, který se nazývá `Function` procedura. `Exit Function` lze použít pouze v rámci `Function` procedury.

 Chcete-li zadat návratovou hodnotu, můžete hodnotu přiřadit názvu funkce na řádku před příkazem `Exit Function`. Chcete-li přiřadit návratovou hodnotu a ukončit funkci v jednom příkazu, můžete místo toho použít [příkaz return](return-statement.md).

 `Exit Property`  
 Okamžitě ukončí `Property` postup, ve kterém se zobrazí. Provádění pokračuje s příkazem, který se nazývá `Property` procedura, to znamená s příkazem požadujícím nebo nastavením hodnoty vlastnosti. `Exit Property` lze použít pouze uvnitř vlastnosti `Get` nebo `Set` procedury.

 Chcete-li zadat návratovou hodnotu v `Get` proceduře, lze hodnotu přiřadit názvu funkce na řádku před příkazem `Exit Property`. Chcete-li přiřadit návratovou hodnotu a ukončit `Get` procedura v jednom příkazu, můžete místo toho použít příkaz `Return`.

 V `Set` proceduře je příkaz `Exit Property` ekvivalentní příkazu `Return`.

 `Exit Select`  
 Okamžitě ukončí `Select Case` blok, ve kterém se zobrazí. Provádění pokračuje s příkazem za příkazem `End Select`. `Exit Select` lze použít pouze uvnitř příkazu `Select Case`.

 `Exit Sub`  
 Okamžitě ukončí `Sub` postup, ve kterém se zobrazí. Provádění pokračuje příkazem po příkazu, který se nazývá `Sub` procedura. `Exit Sub` lze použít pouze v rámci `Sub` procedury.

 V `Sub` proceduře je příkaz `Exit Sub` ekvivalentní příkazu `Return`.

 `Exit Try`  
 Okamžitě ukončí `Try` nebo `Catch` blok, ve kterém se zobrazí. Provádění pokračuje s blokem `Finally`, pokud existuje, nebo s příkazem, který následuje za příkazem `End Try` jinak. `Exit Try` lze použít pouze uvnitř bloku `Try` nebo `Catch` a nikoli uvnitř `Finally` bloku.

 `Exit While`  
 Okamžitě ukončí `While` smyčku, ve které se zobrazí. Provádění pokračuje s příkazem za příkazem `End While`. `Exit While` lze použít pouze uvnitř smyčky `While`. Při použití ve vnořených cyklech `While` `Exit While` přenáší řízení na smyčku, která je jednou vnořenou úrovní nad smyčkou, kde `Exit While` nastane.

## <a name="remarks"></a>Poznámky

Nepleťte si `Exit` příkazy s příkazy `End`. `Exit` nedefinuje konec příkazu.

## <a name="example"></a>Příklad

V následujícím příkladu podmínka smyčky zastaví smyčku, když je proměnná `index` větší než 100. Příkaz `If` ve smyčce ale způsobí, že příkaz `Exit Do` zastaví smyčku v případě, že je proměnná indexu větší než 10.

[!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]

## <a name="example"></a>Příklad

Následující příklad přiřadí návratovou hodnotu k názvu funkce `myFunction`a poté používá `Exit Function` k návratu z funkce:

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

## <a name="example"></a>Příklad

Následující příklad používá [příkaz return](return-statement.md) k přiřazení návratové hodnoty a ukončení funkce:

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

## <a name="see-also"></a>Viz také:

- [Příkaz Continue](continue-statement.md)
- [Příkaz Do...Loop](do-loop-statement.md)
- [Příkaz End](end-statement.md)
- [Příkaz For Each...Next](for-each-next-statement.md)
- [Příkaz For...Next](for-next-statement.md)
- [Příkaz Function](function-statement.md)
- [Příkaz Return](return-statement.md)
- [Příkaz Stop](stop-statement.md)
- [Příkaz Sub](sub-statement.md)
- [Příkaz Try...Catch...Finally](try-catch-finally-statement.md)
