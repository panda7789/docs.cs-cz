---
title: 'Rekurzivní funkce: Klíčové slovo rec'
description: Zjistěte, jak se klíčové slovo REC používá s klíčovým slovem let k definování rekurzivní funkce.
ms.date: 08/12/2020
ms.openlocfilehash: 389357bd13cef39b1d07972c1a3167320b61612b
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558709"
---
# <a name="recursive-functions-the-rec-keyword"></a>Rekurzivní funkce: Klíčové slovo rec

`rec`Klíčové slovo se používá společně s `let` klíčovým slovem k definování rekurzivní funkce.

## <a name="syntax"></a>Syntax

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

Rekurzivní funkce – funkce, které volají samy – jsou identifikovány explicitně v jazyce F # s `rec` klíčovým slovem. `rec`Klíčové slovo vytvoří název vazby, která je `let` k dispozici v těle.

Následující příklad ukazuje rekurzivní funkci, která vypočítá *n*-<sup>tý</sup> Fibonacci číslo pomocí matematické definice.

```fsharp
let fib n =
    match n with
    | 0 | 1 -> 1
    | n -> fib (n-1) + fib (n-2)
```

> [!NOTE]
> V praxi není kód podobný předchozí ukázce ideální, protože unecessarily přepočítá hodnoty, které již byly vypočítány. Důvodem je to, že není rekurzivní, což je vysvětleno dále v tomto článku.

Metody jsou implicitně rekurzivní v rámci typu, který je definován v, což znamená, že není nutné přidávat `rec` klíčové slovo. Příklad:

```fsharp
type MyClass() =
    member this.Fib(n) =
        match n with
        | 0 | 1 -> 1
        | n -> this.Fib(n-1) + this.Fib(n-2)
```

Umožňuje, aby vazby v rámci tříd nebyly implicitně rekurzivní, ale. Všechny `let` funkce svázané s `rec` klíčovým slovem vyžadují klíčové slovo.

## <a name="tail-recursion"></a>Koncová rekurze

U některých rekurzivních funkcí je nutné Refaktorovat více "čisté" definice na hodnotu, která je [argumentem rekurzivně](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion). To brání zbytečnému přepočítání. Například může přepsat předchozí generátor čísel Fibonacci takto:

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

## <a name="recursive-values"></a>Rekurzivní hodnoty

Můžete také definovat `let` hodnotu vazby, která má být rekurzivní. Tato situace se někdy provádí pro protokolování. V F # 5 a `nameof` funkci to můžete udělat:

```fsharp
let rec nameDoubles = nameof nameDoubles + nameof nameDoubles
```

## <a name="see-also"></a>Viz také

- [Functions](index.md)
