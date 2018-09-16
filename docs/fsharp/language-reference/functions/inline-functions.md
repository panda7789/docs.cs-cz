---
title: Vložené funkce (F#)
description: 'Další informace o použití F # vložené funkce, které jsou integrované přímo do kódu volajícího.'
ms.date: 05/16/2016
ms.openlocfilehash: 47fca0fe34630792aeb0908b0cee02a927e2567d
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45685670"
---
# <a name="inline-functions"></a>Vložené funkce

*Vložené funkce* jsou funkce, které jsou integrované přímo do kódu volajícího.

## <a name="using-inline-functions"></a>Použití vložených funkcí

Při použití parametrů statického typu musí být všechny funkce, které jsou parametrizovány parametry typu inline. Zaručí se tak, že kompilátor může rozpoznat tyto parametry typu. Při použití parametrů obecného typu obyčejné neexistuje žádné takové omezení.

Než povoluje použití členská omezení, může být užitečné při optimalizaci kódu vložených funkcí. Nadměrné využití vložených funkcí však může způsobit menší odolné vůči změny v optimalizace kompilátoru a implementaci funkce knihovny kódu. Z tohoto důvodu byste neměli používat vložené funkce optimalizace, pokud jste vyzkoušeli všechny jiné techniky optimalizace. Provádění vložené funkce nebo metoda může někdy zlepšit výkon, ale není to vždy. Měření výkonu proto měli také používat k ověření pozitivní účinek nemá ve skutečnosti provádění jakékoli vložené dané funkce.

`inline` Modifikátor lze použít u funkcí na nejvyšší úrovni, na úrovni modulu nebo na úrovni metody ve třídě.

Následující příklad kódu ukazuje vloženou funkcí na nejvyšší úrovni, vložená metoda instance a vložená metoda statická.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet201.fs)]

## <a name="inline-functions-and-type-inference"></a>Vložené funkce a odvození typu

Přítomnost `inline` odvození typu ovlivňuje. Je to proto vložených funkcí lze staticky řešené parametry typu, že nelze jiných než vložených funkcí. Následující příklad kódu ukazuje případ kde `inline` je užitečné, protože používáte funkci, která má parametr staticky řešeného typu `float` operátoru převodu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

Bez `inline` modifikátor, vynutí odvození typu funkce v tomto případě se konkrétní typ `int`. Ale `inline` modifikátor funkce je také odvozen, aby měl parametr staticky řešeného typu. S `inline` modifikátor, typ je odvozen bude následující:

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

To znamená, že funkce přijímá libovolný typ, který podporuje převod na **float**.

## <a name="see-also"></a>Viz také:

- [Funkce](index.md)
- [Omezení](../generics/constraints.md)
- [Statisticky vyřešené parametry typu](../generics/statically-resolved-type-parameters.md)
