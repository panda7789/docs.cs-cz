---
title: Vložené funkce
description: Naučte se používat F# vložené funkce, které jsou integrovány přímo do kódu volajícího.
ms.date: 05/16/2016
ms.openlocfilehash: 2830d1ada5b3005c3fcae975a44e85a7c84554f7
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630675"
---
# <a name="inline-functions"></a>Vložené funkce

*Vložené funkce* jsou funkce, které jsou integrovány přímo do kódu volajícího.

## <a name="using-inline-functions"></a>Používání vložených funkcí

Při použití parametrů statického typu musí být všechny funkce, které jsou parametrizované parametry typu, vloženy. To zaručuje, že kompilátor dokáže tyto parametry typu vyřešit. Pokud používáte běžné parametry obecného typu, neexistuje takové omezení.

Kromě povolení použití omezení členů mohou být vložené funkce užitečné v rámci optimalizace kódu. Nicméně nadměrné využití vložených funkcí může způsobit, že váš kód bude méně odolný vůči změnám v optimalizacích kompilátoru a implementaci funkcí knihovny. Z tohoto důvodu byste se měli vyhnout použití vložených funkcí pro optimalizaci, pokud jste nezkoušeli všechny ostatní techniky optimalizace. Vytvoření vložené funkce nebo metody může někdy zlepšit výkon, ale to není vždy v případě případu. Proto byste měli použít také měření výkonu k ověření, že je fakt, že by jakákoli z vložených funkcí měla pozitivní účinek.

`inline` Modifikátor lze použít na funkce na nejvyšší úrovni, na úrovni modulu nebo na úrovni metody ve třídě.

Následující příklad kódu ukazuje vloženou funkci na nejvyšší úrovni, vloženou metodu instance a vloženou statickou metodu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet201.fs)]

## <a name="inline-functions-and-type-inference"></a>Vložené funkce a odvození typu

Přítomnost `inline` má vliv na odvození typu. Je to proto, že vložené funkce mohou mít staticky vyřešené parametry typu, zatímco nevložená funkce nemůže. Následující příklad kódu ukazuje případ, kde `inline` je užitečné, protože používáte funkci, která má staticky vyřešený parametr typu `float` , operátor převodu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

Bez modifikátoru vynutí odvození typu funkci, aby v tomto případě `int`vybrala konkrétní typ. `inline` Ale s `inline` modifikátorem, je funkce také odvozena pro statický vyřešený parametr typu. `inline` Pomocí modifikátoru je typ odvozen jako následující:

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

To znamená, že funkce přijímá libovolný typ, který podporuje převod na typ **float**.

## <a name="see-also"></a>Viz také:

- [Funkce](index.md)
- [Omezení](../generics/constraints.md)
- [Statisticky vyřešené parametry typu](../generics/statically-resolved-type-parameters.md)
