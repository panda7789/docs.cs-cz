---
title: 'Rekurzivní funkce: Klíčové slovo rec (F#)'
description: "Zjistěte, jak se používá F # 'rec' – klíčové slovo se – klíčové slovo 'let' Definice rekurzivní funkce."
ms.date: 05/16/2016
ms.openlocfilehash: 6039a48eae2b16aa1d82617176460d727a878d87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="recursive-functions-the-rec-keyword"></a>Rekurzivní funkce: Klíčové slovo rec

`rec` – Klíčové slovo je použít v kombinaci s `let` – klíčové slovo definice rekurzivní funkce.


## <a name="syntax"></a>Syntaxe

```fsharp
// Recursive function:
let rec function-nameparameter-list =
function-body

// Mutually recursive functions:
let rec function1-nameparameter-list =
function1-body
and function2-nameparameter-list =
function2-body
...
```

## <a name="remarks"></a>Poznámky
Rekurzivní funkce, funkce, které se označují, jsou identifikovány explicitně v jazyce F #. To zpřístupňuje identifikátor, který je definovaný v oboru funkce.

Následující kód ukazuje rekurzivní funkci, která vypočítá *n*tý Fibonacciho číslo.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

>[!NOTE]
V praxi jako je například výše uvedený kód je plýtvání paměti a procesoru času, protože se týká recomputation dříve počítaných hodnot.


Metody jsou implicitně rekurzivní v rámci typu; je nutné přidat `rec` – klíčové slovo. Umožňují vazby v rámci třídy nejsou implicitně rekurzivní.


## <a name="mutually-recursive-functions"></a>Vzájemně rekurzivní funkce
V některých případech se funkce *vzájemně rekurzivní*, což znamená, že volání tvoří kruh, kde jeden funkce volá jiné, které volá první, s libovolný počet volání v rozmezí. Je nutné definovat takové funkce společně do jedné `let` vazby, pomocí `and` – klíčové slovo je propojit dohromady.

Následující příklad ukazuje dva vzájemně rekurzivní funkce.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a>Viz také
[Funkce](index.md)
