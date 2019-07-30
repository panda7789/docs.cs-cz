---
title: Vstupní bod
description: Naučte se, jak nastavit vstupní bod na F# program, který je kompilován jako spustitelný soubor, kde se spouští formulář pro spuštění.
ms.date: 05/16/2016
ms.openlocfilehash: 5e13416131d4dfd22583439fedf51f18f7a461da
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630517"
---
# <a name="entry-point"></a>Vstupní bod

Toto téma popisuje metodu, kterou použijete k nastavení vstupního bodu na F# program.

## <a name="syntax"></a>Syntaxe

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a>Poznámky

V předchozí syntaxi je *let-Function-Binding* definicí funkce ve `let` vazbě.

Vstupním bodem programu, který je kompilován jako spustitelný soubor, je místo, kde se spouští formulář pro spuštění. Vstupní bod do F# aplikace určíte tak, že použijete `EntryPoint` atribut `main` pro funkci programu. Tato funkce (vytvořená pomocí `let` vazby) musí být poslední funkcí v posledním kompilovaném souboru. Poslední kompilovaný soubor je poslední soubor v projektu nebo poslední soubor, který je předán do příkazového řádku.

Funkce vstupního bodu má typ `string array -> int`. Argumenty uvedené na příkazovém řádku jsou předány `main` funkci v poli řetězců. Prvním prvkem pole je první argument; název spustitelného souboru není zahrnutý v poli, protože je v některých jiných jazycích. Návratová hodnota se používá jako ukončovací kód pro daný proces. Nula obvykle indikuje úspěch; nenulové hodnoty označují chybu. Neexistuje žádná úmluva pro konkrétní význam nenulových návratových kódů; význam návratových kódů je specifický pro aplikaci.

Následující příklad ilustruje jednoduchou `main` funkci.

[!code-fsharp[Main](~/samples/snippets/fsharp/entry-point/snippet501.fs)]

Když se tento kód spustí s příkazovým řádkem `EntryPoint.exe 1 2 3`, výstup je následující.

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a>Implicitní vstupní bod

Pokud program nemá žádný atribut **EntryPoint** , který explicitně indikuje vstupní bod, použijí se jako vstupní bod vazby nejvyšší úrovně v posledním souboru, který se má zkompilovat.

## <a name="see-also"></a>Viz také:

- [Funkce](index.md)
- [Vazby let](let-bindings.md)
