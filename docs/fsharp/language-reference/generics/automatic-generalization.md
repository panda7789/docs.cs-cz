---
title: Automatická generalizace
description: Přečtěte F# si, jak automaticky zobecnit argumenty a typy funkcí tak, aby fungovaly s více typy, pokud je to možné.
ms.date: 05/16/2016
ms.openlocfilehash: 501749a190d9770cbcd9848e3d528cba32fe6762
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630621"
---
# <a name="automatic-generalization"></a>Automatická generalizace

F#používá odvození typu pro vyhodnocení typů funkcí a výrazů. Toto téma popisuje, F# jak automaticky zobecnit argumenty a typy funkcí tak, aby fungovaly s více typy, pokud je to možné.

## <a name="automatic-generalization"></a>Automatická generalizace

F# Kompilátor, když provádí odvození typu na funkci, určuje, zda daný parametr může být obecný. Kompilátor prověřuje každý parametr a určí, zda má funkce závislost na konkrétním typu daného parametru. Pokud tomu tak není, typ je odvozen jako obecný.

Následující příklad kódu ukazuje funkci, která kompilátor odvodí jako obecný.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

Typ je odvozený `'a -> 'a -> 'a`.

Typ označuje, že se jedná o funkci, která přijímá dva argumenty stejného neznámého typu a vrací hodnotu stejného typu. Jedním z důvodů, proč může být funkce Previous obecná, je, že operátor větší než (`>`) je obecný. Operátor větší než má signaturu `'a -> 'a -> bool`. Ne všechny operátory jsou obecné a pokud kód ve funkci používá typ parametru společně s neobecnou funkcí nebo operátorem, tento typ parametru nejde zobecnit.

Vzhledem `max` k tomu, že je obecný, lze použít s typy `int`, `float`jako jsou, a tak dále, jak je znázorněno v následujících příkladech.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

Dva argumenty však musí být stejného typu. Podpis není `'a -> 'a -> 'a`. `'a -> 'b -> 'a` Proto následující kód vytvoří chybu, protože typy se neshodují.

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

`max` Funkce také funguje s jakýmkoli typem, který podporuje operátor větší než. Proto jej můžete použít také na řetězec, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet104.fs)]

## <a name="value-restriction"></a>Omezení hodnoty

Kompilátor provádí automatickou generalizaci pouze v úplných definicích funkcí, které mají explicitní argumenty a na jednoduchých neměnných hodnotách.

To znamená, že kompilátor vyvolá chybu, pokud se pokusíte zkompilovat kód, který není dostatečně omezený na konkrétní typ, ale není možné jej zobecnit. Chybová zpráva pro tento problém odkazuje na toto omezení automatické generalizace pro hodnoty jako *omezení hodnoty*.

Obvykle dojde k chybě omezení hodnoty, pokud chcete, aby konstrukce byla obecná, ale kompilátor nemá dostatek informací pro generalizaci, nebo Pokud neúmyslně vynecháte dostatečné informace o typu v neobecném konstruktoru. Řešení chyby omezení hodnoty je poskytnout explicitní informace pro větší omezení problému typu odvození typu jedním z následujících způsobů:

- Omezení typu na neobecný přidáním anotace explicitního typu k hodnotě nebo parametru.

- Pokud problém používá nezobecnitelné konstrukce k definování obecné funkce, jako je například složení funkce nebo nedokončené použití argumentů funkce curryfikované, zkuste funkci přepsat jako běžnou definici funkce.

- Pokud je problém výrazem, který je příliš složitý, aby jej bylo možné zobecnit, udělejte ho do funkce přidáním nadbytečného, nepoužívaného parametru.

- Přidejte explicitní parametry obecného typu. Tato možnost se používá zřídka.

- Následující příklady kódu ilustrují každý z těchto scénářů.

Případ 1: Výraz je příliš složitý. V tomto příkladu je seznam `counter` určen `int option ref`jako, ale není definován jako jednoduchá neměnná hodnota.

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

Případ 2: Použití negeneralizované konstrukce k definování obecné funkce. V tomto příkladu je konstrukce negeneralizovaná, protože zahrnuje částečnou aplikaci argumentů funkce.

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

Případ 3: Přidání nadbytečného, nepoužívaného parametru. Vzhledem k tomu, že tento výraz není pro generalizaci dostatečně jednoduchý, vyvolá kompilátor chybu omezení hodnoty.

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

Případ 4: Přidávání parametrů typu.

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

V posledním případě se hodnota stala funkcí typu, která může být použita k vytvoření hodnot mnoha různých typů, například následujícím způsobem:

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a>Viz také:

- [Odvození typu](../type-inference.md)
- [Obecné typy](index.md)
- [Statisticky vyřešené parametry typu](statically-resolved-type-parameters.md)
- [Omezení](constraints.md)
