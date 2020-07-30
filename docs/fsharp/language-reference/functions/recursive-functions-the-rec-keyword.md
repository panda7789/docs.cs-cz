---
title: 'Rekurzivní funkce: Klíčové slovo rec'
description: Zjistěte, jak se klíčové slovo REC používá s klíčovým slovem let k definování rekurzivní funkce.
ms.date: 05/16/2016
ms.openlocfilehash: c9a3b7dc27f4ed86948a08b7783d7e8e8b60e57f
ms.sourcegitcommit: 32f0d6f4c01ddc6ca78767c3a30e3305f8cd032c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2020
ms.locfileid: "87426973"
---
# <a name="recursive-functions-the-rec-keyword"></a>Rekurzivní funkce: Klíčové slovo rec

`rec`Klíčové slovo se používá společně s `let` klíčovým slovem k definování rekurzivní funkce.

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

Rekurzivní funkce, funkce, které volají samy sebe, jsou identifikovány explicitně v jazyce F #. Tím se identifikátorem, které je definováno v oboru funkce.

Následující kód ilustruje rekurzivní funkci, která vypočítá n- *n*<sup>tý</sup> Fibonacci číslo pomocí matematické definice.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> V praxi není kód podobný předchozí ukázce ideální, protože unecessarily přepočítá hodnoty, které již byly vypočítány. Důvodem je to, že není rekurzivní, což je vysvětleno dále v tomto článku.

Metody jsou implicitně rekurzivní v rámci typu; není nutné přidávat `rec` klíčové slovo. Umožňuje, aby vazby v rámci tříd nebyly implicitně rekurzivní.

## <a name="tail-recursion"></a>Koncová rekurze

U některých rekurzivních funkcí je nutné Refaktorovat více "čisté" definice na hodnotu, která je [argumentem rekurzivně](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion). Tím zabráníte reunecessarym recompute. Například může přepsat předchozí generátor čísel Fibonacci takto:

```fsharp
let fib n =
    let rec loop acc1 acc2 n =
        match n with
        | 0 -> acc1
        | 1 -> acc2
        | _ ->
            loop acc2 (acc1 + acc2) (n - 1)
    loop 0 1 n
```

Toto je složitější implementace. Generování Fibonacci čísla je skvělým příkladem algoritmu "Naive", který je matematicky čistý, ale v praxi je neefektivní. Několik aspektů je efektivní v F #, ale stále ještě zbývá rekurzivně definovat:

* Rekurzivní vnitřní funkce s názvem `loop` , což je vzor Idiomatickou F #.
* Dva parametry akumulátoru, které předají hodnoty do rekurzivních volání.
* Kontrolu hodnoty `n` pro vrácení konkrétního hromadění.

Pokud byl tento příklad napsán cyklicky se smyčkou, kód by vypadal podobně jako dvě různé hodnoty nahromadění čísel, dokud nebyla splněna určitá podmínka.

Důvod, proč je to zakončené – rekurzivní je, protože rekurzivní volání nemusí ukládat žádné hodnoty do zásobníku volání. Všechny vypočtené mezilehlé hodnoty jsou shromažďovány prostřednictvím vstupů do vnitřní funkce. To také umožňuje kompilátoru F # optimalizovat kód tak, aby byl přesně tak rychle, jako kdyby byl napsán jako `while` smyčka.

Je běžné psát kód F #, který rekurzivně zpracovává něco s vnitřní a vnější funkcí, jak ukazuje předchozí příklad. Vnitřní funkce používá funkci Tail s koncovou rekurzí, zatímco vnější funkce má lepší rozhraní pro volající.

## <a name="mutually-recursive-functions"></a>Vzájemně rekurzivní funkce

Funkce jsou někdy *vzájemně rekurzivní*, což znamená, že volání tvoří kruh, kde jedna funkce volá metodu, která zavolá první, s libovolným počtem volání mezi. Tyto funkce musíte definovat společně v jedné `let` vazbě pomocí `and` klíčového slova k jejich propojení.

Následující příklad ukazuje dvě vzájemně rekurzivní funkce.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a>Viz také:

- [Functions](index.md)
