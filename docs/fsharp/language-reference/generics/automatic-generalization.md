---
title: Automatická generalizace
description: Zjistěte, jak F# automaticky zobecňuje argumenty a typy funkce tak, aby fungovaly s více typy, pokud je to možné.
ms.date: 05/16/2016
ms.openlocfilehash: 8fc61b5e0c227474a5e913b37f4c0dad9b235a6f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641875"
---
# <a name="automatic-generalization"></a>Automatická generalizace

F#používá typ odvození posoudíte typy vašich funkce a výrazy. Toto téma popisuje, jak F# automaticky zobecňuje argumenty a typy funkce tak, aby fungovaly s více typy kdykoli je to možné.

## <a name="automatic-generalization"></a>Automatická generalizace

F# Kompilátoru, když ji provede odvození typu na funkci, určuje, zda daný parametr může být obecný. Kompilátor zkontroluje každý parametr a určuje, zda funkce má závislosti na konkrétní typ tohoto parametru. Pokud tomu tak není, typ je odvozen je obecný.

Následující příklad kódu ukazuje funkci, která kompilátor odvodí z nich je obecný.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

Typ je odvozen bude `'a -> 'a -> 'a`.

Typ uvádí, že se jedná o funkci, která přebírá dva argumenty stejného Neznámý typ a vrátí hodnotu stejného typu. Jedním z důvodů, které mohou být předchozí funkce obecného je, že větší-než – operátor (`>`) je samotný obecný. Větší-než operátor nemá podpis `'a -> 'a -> bool`. Ne všechny operátory jsou obecné, a pokud kód ve funkci používá typ parametru spolu s neobecné funkce nebo operátoru, tento typ parametru nelze zobecněný.

Protože `max` je obecný, ho jde použít s typy, jako `int`, `float`, a tak dále, jak je znázorněno v následujícím příkladu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

Dva argumenty, ale musí být stejného typu. Podpis je `'a -> 'a -> 'a`, nikoli `'a -> 'b -> 'a`. Následující kód proto vygeneruje chybu, protože typy se neshodují.

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

`max` Funkce také funguje s jakýmkoli typem, který podporuje větší-než operátor. Proto můžete také použít ho na řetězec, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet104.fs)]

## <a name="value-restriction"></a>Omezení hodnoty

Kompilátor provede automatická generalizace jenom u definic dokončení funkcí, které mají explicitní argumenty a na jednoduché neměnné hodnoty.

To znamená, že kompilátor vyvolá chybu při kompilaci kódu, který není dostatečně omezen na konkrétní typ, ale není také generalizovatelného. Chybová zpráva pro tento problém odkazuje na toto omezení na automatická generalizace pro hodnoty jako *hodnota omezení*.

Na hodnotu omezení chybě obvykle dochází, když chcete použít konstrukce je obecný, ale kompilátor má dostatek informací k zobecnění ho nebo Pokud vynecháte neúmyslně dostatek informací o typu v neobecné konstrukce. Řešení tak, aby chyba omezení hodnoty má obsahují podrobnější informace, které podrobněji omezit problém odvození typu, v jednom z následujících způsobů:

- Omezení typu bude neobecné přidáním anotace explicitního typu hodnoty nebo parametr.

- Pokud se problém nongeneralizable konstruktor používá k definování obecné funkce, jako je například funkce – složení nebo neúplně použita curryfikované argumenty, zkuste přepsání funkce jako definici běžné funkce.

- Pokud se jedná o výraz, který je příliš složitý pro zobecnit, převeďte na funkci tak, že přidáte další, nepoužité parametr.

- Přidáte explicitní obecné parametry typu. Tato možnost se používá jen zřídka.

- Následující příklady kódu ukazují každý z těchto scénářů.

Případ 1: Příliš složitý výraz. V tomto příkladu seznamu `counter` má být `int option ref`, ale není definován jako jednoduchý neměnný hodnota.

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

Případ 2: Chcete-li definovat obecnou funkci pomocí konstrukce nongeneralizable. V tomto příkladu je konstrukce nongeneralizable, protože se týká částečné použití argumentů funkce.

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

Případ 3: Přidat parametr navíc, nevyužité. Vzhledem k tomu, že tento výraz není dostatečně jednoduchá pro generalizaci, kompilátor vyvolá chybu omezení hodnoty.

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

Případ 4: Přidání parametrů typu.

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

V posledním případě tato hodnota začne – funkce typu, který může být použit k vytvoření hodnot typu mnoho různých typů, třeba takto:

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a>Viz také:

- [Odvození typu](../type-inference.md)
- [Obecné typy](index.md)
- [Statisticky vyřešené parametry typu](statically-resolved-type-parameters.md)
- [Omezení](constraints.md)
