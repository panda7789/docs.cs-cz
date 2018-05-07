---
title: Vstupní bod (F#)
description: 'Zjistěte, jak nastavit vstupní bod programu F #, který se zkompiluje jako spustitelného souboru, kde oficiálně spustí provádění.'
ms.date: 05/16/2016
ms.openlocfilehash: 3d6cab755dd89f2d3d669a8763aa08660432a0ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="entry-point"></a>Vstupní bod

Toto téma popisuje metodu, můžete použít k nastavení vstupní bod programu F #.


## <a name="syntax"></a>Syntaxe

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a>Poznámky
V předchozích syntaxi *vazba funkce umožňují* je definice funkce v `let` vazby.

Vstupní bod k programu, který se zkompiluje jako spustitelný soubor je, kde oficiálně spustí provádění. Zadejte vstupní bod aplikace F # s použitím `EntryPoint` atribut program `main` funkce. Tato funkce (vytvořili pomocí `let` vazba) musí být poslední funkce v poslední zkompilovaný soubor. Poslední zkompilovaný soubor je posledního souboru v projektu nebo posledního souboru, který je předán do příkazového řádku.

Funkce vstupního bodu má typ `string array -> int`. Argumenty zadat na příkazovém řádku `main` funkce v poli řetězců. První prvek pole je první argument; název spustitelného souboru není součástí pole, protože je v některých dalších jazycích. Návratová hodnota slouží jako kód ukončení procesu. Nula obvykle označuje úspěch; nenulové hodnoty udávající chybu. Neexistuje žádné názvů pro zvláštní význam nenulové hodnoty návratových kódů; významy návratových kódů jsou specifické pro aplikaci.

Následující příklad ukazuje jednoduchý `main` funkce.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/entry-point/snippet501.fs)]

Při spuštění tohoto kódu s příkazovým řádkem `EntryPoint.exe 1 2 3`, výstup je následující.

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a>Implicitní vstupního bodu
Když program neobsahuje žádné **EntryPoint** atribut, který explicitně určuje vstupní bod, vazby nejvyšší úrovně v posledního souboru mají být zkompilovány, do se používají jako vstupní bod.


## <a name="see-also"></a>Viz také
[Funkce](index.md)

[Vazby let](let-bindings.md)
