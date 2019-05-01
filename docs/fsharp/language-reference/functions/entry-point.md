---
title: Vstupní bod
description: Zjistěte, jak nastavit vstupní bod F# program zkompilovaný jako spustitelný soubor, ve kterém formálně spuštění.
ms.date: 05/16/2016
ms.openlocfilehash: 915ab17b9a4fc7fd4d0ae344cb273b1d348a02f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996824"
---
# <a name="entry-point"></a>Vstupní bod

Toto téma popisuje metody, která se používá k nastavení vstupní bod F# programu.

## <a name="syntax"></a>Syntaxe

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a>Poznámky

V předchozí syntaxi *vazba funkce umožňují* je definice funkce v `let` vazby.

Vstupní bod programu, který je zkompilován je spustitelný soubor, ve kterém formálně spuštění. Zadejte vstupní bod do F# aplikace s použitím `EntryPoint` atribut programu `main` funkce. Tato funkce (vytvořené využitím `let` vazby) musí být poslední funkci v poslední zkompilovaný soubor. Poslední zkompilovaný soubor je poslední soubor v projektu nebo poslední soubor, který je předán do příkazového řádku.

Funkci vstupního bodu má typ `string array -> int`. Argumenty příkazového řádku k dispozici jsou předány `main` funkce v poli řetězců. Prvním prvkem pole je první argument; název spustitelného souboru, který není zahrnutý v poli, je to v některých jiných jazycích. Návratová hodnota se používá jako ukončovací kód procesu. Nula obvykle znamená úspěšné nenulové hodnoty udávající chybu. Neexistuje žádné vytváření názvů pro zvláštní význam nenulové návratové kódy; význam návratové kódy jsou specifické pro aplikaci.

Následující příklad ukazuje jednoduchý `main` funkce.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/entry-point/snippet501.fs)]

Při spuštění tohoto kódu s příkazovým řádkem `EntryPoint.exe 1 2 3`, výstup je následující.

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a>Implicitní vstupní bod

Pokud program nemá žádné **EntryPoint** atribut, který explicitně určuje vstupní bod vazeb nejvyšší úrovně v posledním souboru ke kompilaci se používají jako vstupní bod.

## <a name="see-also"></a>Viz také:

- [Funkce](index.md)
- [Vazby let](let-bindings.md)