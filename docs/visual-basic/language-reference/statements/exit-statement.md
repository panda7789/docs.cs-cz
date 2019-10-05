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
ms.openlocfilehash: 9c25653809c51662ea5b606ab97be6a9b50d5986
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2019
ms.locfileid: "71956936"
---
# <a name="exit-statement-visual-basic"></a>Exit – příkaz (Visual Basic)

Ukončí proceduru nebo blok a okamžitě přenese řízení do příkazu za voláním procedury nebo definicí bloku.

## <a name="syntax"></a>Syntaxe

```vb
Exit { Do | For | Function | Property | Select | Sub | Try | While }
```

## <a name="statements"></a>Příkazy

 `Exit Do`  
 Okamžitě ukončí cyklus `Do`, ve kterém se zobrazí. Provádění pokračuje s příkazem za příkazem `Loop`. `Exit Do` se dá použít jenom uvnitř smyčky `Do`. Při použití v rámci vnořených `Do` smyčky `Exit Do` ukončí vnitřní smyčku a přenáší řízení na další vyšší úroveň vnoření.

 `Exit For`  
 Okamžitě ukončí cyklus `For`, ve kterém se zobrazí. Provádění pokračuje s příkazem za příkazem `Next`. `Exit For` se dá použít jenom uvnitř smyčky `For`... `Next` nebo `For Each`... `Next`. Při použití v rámci vnořených `For` smyčky `Exit For` ukončí vnitřní smyčku a přenáší řízení na další vyšší úroveň vnoření.

 `Exit Function`  
 Okamžitě ukončí postup @no__t 0, ve kterém se zobrazí. Provádění pokračuje příkazem po příkazu, který volal postup `Function`. `Exit Function` se dá použít jenom uvnitř procedury `Function`.

 Chcete-li zadat návratovou hodnotu, můžete hodnotu přiřadit názvu funkce na řádku před příkazem `Exit Function`. Chcete-li přiřadit návratovou hodnotu a ukončit funkci v jednom příkazu, můžete místo toho použít [příkaz return](return-statement.md).

 `Exit Property`  
 Okamžitě ukončí postup @no__t 0, ve kterém se zobrazí. Provádění pokračuje s příkazem, který se nazývá postup `Property`, to znamená pomocí příkazu, který požaduje nebo nastavuje hodnotu vlastnosti. `Exit Property` se dá použít jenom uvnitř procedury vlastnosti `Get` nebo `Set`.

 Chcete-li zadat návratovou hodnotu v proceduře `Get`, můžete hodnotu přiřadit názvu funkce na řádku před příkazem `Exit Property`. Chcete-li přiřadit návratovou hodnotu a ukončit proceduru `Get` v jednom příkazu, můžete místo toho použít příkaz `Return`.

 V proceduře `Set` je příkaz `Exit Property` ekvivalentní příkazu `Return`.

 `Exit Select`  
 Okamžitě ukončí blok `Select Case`, ve kterém se zobrazí. Provádění pokračuje s příkazem za příkazem `End Select`. `Exit Select` se dá použít jenom uvnitř příkazu `Select Case`.

 `Exit Sub`  
 Okamžitě ukončí postup @no__t 0, ve kterém se zobrazí. Provádění pokračuje příkazem po příkazu, který volal postup `Sub`. `Exit Sub` se dá použít jenom uvnitř procedury `Sub`.

 V proceduře `Sub` je příkaz `Exit Sub` ekvivalentní příkazu `Return`.

 `Exit Try`  
 Okamžitě ukončí `Try` nebo `Catch` blok, ve kterém se zobrazí. Provádění pokračuje s blokem `Finally`, pokud existuje, nebo s příkazem, který následuje za příkazem `End Try` v opačném případě. `Exit Try` se dá použít jenom uvnitř bloku `Try` nebo `Catch`, a ne uvnitř bloku `Finally`.

 `Exit While`  
 Okamžitě ukončí cyklus `While`, ve kterém se zobrazí. Provádění pokračuje s příkazem za příkazem `End While`. `Exit While` se dá použít jenom uvnitř smyčky `While`. Při použití v rámci vnořených smyček `While` `Exit While` přenáší řízení do smyčky, která je jednou vnořenou úrovní nad smyčkou, kde se vyskytuje `Exit While`.

## <a name="remarks"></a>Poznámky

Nezaměňujte příkazy `Exit` s příkazy `End`. `Exit` nedefinuje konec příkazu.

## <a name="example"></a>Příklad

V následujícím příkladu podmínka smyčky zastaví smyčku, když je proměnná `index` větší než 100. Příkaz `If` ve smyčce ale způsobí, že příkaz `Exit Do` zastaví smyčku v případě, že je proměnná indexu větší než 10.

[!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]

## <a name="example"></a>Příklad

Následující příklad přiřadí návratovou hodnotu k názvu funkce `myFunction` a poté pomocí `Exit Function` vrátí z funkce:

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
