---
title: "Rekurzivní funkce: Klíčové slovo rec (F#)"
description: "Zjistěte, jak se používá F # 'rec' – klíčové slovo se – klíčové slovo 'let' Definice rekurzivní funkce."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 1a95639f-9bfe-4f1d-a5e2-246d1d37776e
ms.openlocfilehash: b837d2c0f8e2b1d28980620103097ccc8345c098
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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

Následující kód ukazuje rekurzivní funkci, která vypočítá  *n* tý Fibonacciho číslo.

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
