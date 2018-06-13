---
title: Automatická generalizace (F#)
description: 'Zjistěte, jak F # automaticky umožňuje zobecnit argumentů a typy funkce tak, aby fungovaly s více typy, pokud je to možné.'
ms.date: 05/16/2016
ms.openlocfilehash: 858c8bab4a1a37f44a700744e70ebfa8a5abf12c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565072"
---
# <a name="automatic-generalization"></a>Automatická generalizace

F # používá odvození typu k vyhodnocení typy výrazů a funkce. Toto téma popisuje, jak F # automaticky umožňuje zobecnit argumentů a typy funkce tak, aby pracují s více typy, když je to možné.


## <a name="automatic-generalization"></a>Automatická generalizace
Kompilátor F # při provádění odvození typu na funkce, určuje, zda daný parametr může být obecný. Kompilátor prozkoumá každý parametr a určuje, zda funkce má závislost na konkrétní typ tohoto parametru. Pokud ne, je odvodit typ být obecný.

Následující příklad kódu představuje funkci, která kompilátor odvodí být obecný.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

Je potřeba odvodit typ `'a -> 'a -> 'a`.

Typ uvádí, že toto je funkce, která má dva argumenty stejné Neznámý typ a vrátí hodnotu stejného typu. Jedním z důvodů, které může být předchozí funkce obecné je, že delší – než – operátor (`>`) je sám Obecné. Delší – než operátor podpis `'a -> 'a -> bool`. Ne všechny operátory jsou obecné, a pokud kód ve funkci používá typ parametru společně s neobecnou funkce nebo operátor, parametr typu nemůže být zobecněn.

Protože `max` je obecný, se dá použít s typy, jako `int`, `float`a tak dále, jak je znázorněno v následujících příkladech.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

Dva argumenty, ale musí být stejného typu. Podpis je `'a -> 'a -> 'a`, nikoli `'a -> 'b -> 'a`. Proto následující kód vytvoří chybu, protože typy se neshodují.

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

`max` Funkce funguje taky s žádný typ, který podporuje větší – než – operátor. Proto můžete také použít ho na řetězec, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet104.fs)]
    
## <a name="value-restriction"></a>Omezení hodnoty
Kompilátor provede automatická generalizace pouze na definice dokončení funkcí, které mají explicitní argumenty a na jednoduchý neměnné hodnoty.

To znamená, že kompilátor problémy chybu, pokud se pokusíte zkompilovat kód, který není dostatečně omezené na konkrétní typ, ale není také generalizovatelného. Chybová zpráva pro tento problém odkazuje na toto omezení na automatická generalizace pro hodnoty jako *hodnoty omezení*.

Hodnotu omezení chybě obvykle dochází, když chcete konstrukce jako obecný ale kompilátor má dostatek informací ke generalizaci ho nebo pokud nechtěně vynechat dostatek informací o typu v neobecné konstrukce. Řešení chyby omezení hodnota je poskytují podrobnější informace, které podrobněji omezit problém odvození typu, v jednom z následujících způsobů:


- Zadat omezení typu být neobecné přidáním anotaci typu explicitní hodnota nebo parametr.

- Pokud tento problém je pomocí konstrukce nongeneralizable k definování obecné funkce, jako je například funkce složení nebo úplně použili argumenty curryfikované funkce, zkuste přepisování funkce jako definici běžné funkce.

- Pokud tento problém je výraz, který je příliš složitý zobecněny, nastavte do funkce přidáním parametru navíc, nepoužívá.

- Přidání parametrů explicitní obecného typu. Tato možnost se používá zřídka.

- Následující příklady kódu ilustrují každého z těchto scénářů.

Případ 1: Příliš složitý výraz. V tomto příkladu seznamu `counter` má být `int option ref`, ale není definován jako hodnotu simple neměnné.

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

Případ 2: Definování obecné funkce pomocí nongeneralizable konstrukce. V tomto příkladu je konstruktu nongeneralizable, protože se týká částečné aplikace argumenty funkce.

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

Případ 3: Přidání parametru navíc, nepoužívá. Protože tento výraz není dostatečně jednoduchá pro generalizace, vydá chyba omezení hodnotu.

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

V případě poslední tato hodnota začne typ funkce, které mohou být použity k vytvoření hodnoty mnoho různých typů, například takto:

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a>Viz také
[Odvození typu](../type-inference.md)

[Obecné typy](index.md)

[Statisticky vyřešené parametry typu](statically-resolved-type-parameters.md)

[Omezení](constraints.md)

