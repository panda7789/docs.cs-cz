---
title: 'Rekurzivní funkce: Klíčové slovo rec (F#)'
description: Zjistěte, jak F# – klíčové slovo "dop." pomocí klíčového slova "let" slouží k definování rekurzivní funkce.
ms.date: 05/16/2016
ms.openlocfilehash: 0db3ed7f85a1380654f2827b4773985b661589c7
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127729"
---
# <a name="recursive-functions-the-rec-keyword"></a>Rekurzivní funkce: Klíčové slovo rec

`rec` – Klíčové slovo se používá spolu s `let` – klíčové slovo do definuje rekurzivní funkce.

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

Rekurzivní funkce, funkce, které volají samy, jsou uvedené v explicitně F# jazyka. Díky tomu identifikátor, který definuje dostupné v oboru funkce.

Následující kód ukazuje rekurzivní funkci, která vypočítá *n*<sup>th</sup> Fibonacciho číslo.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> V praxi jako je například výše uvedený kód totiž plýtváním paměti a času procesoru zahrnuje kterémkoli dříve vypočítané hodnoty.

Metody jsou implicitně rekurzivní v rámci typu; není nutné přidat `rec` – klíčové slovo. Vazby let v rámci třídy nejsou implicitně rekurzivní.

## <a name="mutually-recursive-functions"></a>Vzájemně rekurzivní funkce

Někdy jsou funkce *vzájemně rekurzivní*, což znamená, že volání tvoří kruh, kde jedna funkce volá jinou která pak volá první, s libovolným počtem volání mezi. Je nutné definovat tyto funkce dohromady do jedné `let` vazba, pomocí `and` – klíčové slovo je propojit dohromady.

Následující příklad ukazuje dva vzájemně rekurzivní funkce.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a>Viz také:

- [Funkce](index.md)
