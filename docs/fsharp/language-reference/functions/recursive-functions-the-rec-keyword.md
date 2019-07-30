---
title: 'Rekurzivní funkce: Klíčové slovo REC'
description: Zjistěte, F# jak se klíčové slovo REC používá s klíčovým slovem let k definování rekurzivní funkce.
ms.date: 05/16/2016
ms.openlocfilehash: 7edaa7206b2109c7b1a405624b9b2330968f9c52
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630654"
---
# <a name="recursive-functions-the-rec-keyword"></a>Rekurzivní funkce: Klíčové slovo REC

Klíčové slovo se používá společně `let` s klíčovým slovem k definování rekurzivní funkce. `rec`

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

Rekurzivní funkce, funkce, které volají samy sebe, jsou identifikovány F# explicitně v jazyce. Tím se identifikátorem, které je definováno v oboru funkce.

Následující kód ilustruje rekurzivní funkci, která vypočítá n-<sup>tý</sup> Fibonacci číslo.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> V praxi kód podobný výše je wasteful paměti a času procesoru, protože zahrnuje recompute dříve počítaných hodnot.

Metody jsou implicitně rekurzivní v rámci typu; není nutné přidávat `rec` klíčové slovo. Umožňuje, aby vazby v rámci tříd nebyly implicitně rekurzivní.

## <a name="mutually-recursive-functions"></a>Vzájemně rekurzivní funkce

Funkce jsou někdy *vzájemně rekurzivní*, což znamená, že volání tvoří kruh, kde jedna funkce volá metodu, která zavolá první, s libovolným počtem volání mezi. Tyto funkce musíte definovat společně v jedné `let` vazbě `and` pomocí klíčového slova k jejich propojení.

Následující příklad ukazuje dvě vzájemně rekurzivní funkce.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a>Viz také:

- [Funkce](index.md)
