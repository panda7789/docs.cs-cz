---
title: let – vazby (F#)
description: Další informace o použití jazyka F# nechat vazbu, která přidruží hodnotě nebo funkci identifikátor.
ms.date: 05/16/2016
ms.openlocfilehash: 1a35b5a39f2768a18665b5c7fe768af0e7714577
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "43777467"
---
# <a name="let-bindings"></a>let – vazby

A *vazby* identifikátor přidruží k hodnotě nebo funkci. Můžete použít `let` – klíčové slovo k vytvoření vazby názvu s hodnotě nebo funkci.

## <a name="syntax"></a>Syntaxe

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a>Poznámky

`let` – Klíčové slovo se používá ve vazbě výrazy k definování hodnot nebo funkce jednoho nebo více názvů. Nejjednodušší forma `let` výraz vytvoří vazbu názvu jednoduchých hodnot, následujícím způsobem.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

Pokud samostatné výrazu z identifikátoru s použitím nového řádku, musíte odsadit každý řádek výrazu, stejně jako v následujícím kódu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

Namísto pouze název, můžete zadat vzor, který obsahuje názvy, například řazená kolekce členů, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

*Výraz těla* je výraz, ve kterém se používají názvy. Výraz těla se objeví na samostatném řádku odsazen řádek nahoru přesně prvního znaku v `let` – klíčové slovo:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

A `let` vazby se může zobrazit na úrovni modulu v definici typu třídy nebo v místní obory, jako je definicí funkce. A `let` vazby na nejvyšší úrovni v modulu nebo typ třídy není nutné mít tělo výrazu, ale na jiných úrovních oboru, je nutné tělo výrazu. Vázané názvy jsou použitelné od chvíle, definice, ale ne v libovolném okamžiku před `let` vazby se zobrazí, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]

## <a name="function-bindings"></a>Vazby – funkce

Vazby funkcí postupujte z pravidel pro vazby hodnoty, s tím rozdílem, že funkce zahrnují název funkce a parametry, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

Obecně platí parametry jsou vzory, třeba vzor řazené kolekce členů:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

A `let` vazby výraz vyhodnocen jako hodnota posledního výrazu. Proto v následujícím příkladu kódu, hodnota `result` je vypočítán z `100 * function3 (1, 2)`, který se hodnotí jako `300`.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

Další informace najdete v tématu [funkce](index.md).

## <a name="type-annotations"></a>Anotace typu

Je-li zadat typy jako parametry, včetně dvojtečky (:), za nímž následuje název typu, všechny uzavřené v závorkách. Můžete také určit typ vrácené hodnoty přidáním dvojtečkou a typem po posledním parametrem. Poznámky typu k `function1`, s celými čísly jako typy parametrů, by měl vypadat takto.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

Pokud neexistují žádné explicitní parametry typu, odvození typu proměnné se používá k určení typů parametrů funkcí. To může zahrnovat automaticky zobecňuje typ parametru je obecný.

Další informace najdete v tématu [Automatická generalizace](../generics/automatic-generalization.md) a [odvození typu](../type-inference.md).

## <a name="let-bindings-in-classes"></a>Vazby let ve třídách

A `let` vazby se může objevit v typu třídy, ale ne v struktury nebo typu záznamu. Pokud chcete používat let vazby v typu třídy, musí mít třídu primární konstruktor. Parametry konstruktoru musí následovat za názvem typu v definici třídy. A `let` vazby v typu třídy definuje privátní pole a členy typu třídy a společně s `do` vazby typu formuláře kód k primárnímu konstruktoru pro typ. Následující příklady kódu ukazují třídu `MyClass` s privátní pole `field1` a `field2`.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

Obory `field1` a `field2` jsou omezené na typ, ve kterém jsou deklarovány. Další informace najdete v tématu [ `let` vazby ve třídách](../members/let-bindings-in-classes.md) a [třídy](../classes.md).

## <a name="type-parameters-in-let-bindings"></a>Let – vazby parametrů typu v

A `let` vazby na úrovni modulu, typu nebo ve výrazu výpočtu může mít explicitní parametry typu. Umožňují vazby ve výrazu, například uvnitř definice funkce nemůže mít parametry typu. Další informace najdete v tématu [obecných typů](../generics/index.md).

## <a name="attributes-on-let-bindings"></a>Atributy u let – vazby

Atributy lze použít na nejvyšší úrovni `let` vazby v modulu, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]

## <a name="scope-and-accessibility-of-let-bindings"></a>Rozsah a usnadnění přístupu vám umožňují vazeb

Rozsah entity deklarované s vazbou let je omezen na část z nadřazeného oboru (například funkce, modulu, souboru nebo třídy), po zobrazení vazby. Proto lze říci, že umožňují vazby zavádí název do oboru. V modulu umožňují datově závislé hodnoty nebo funkce je přístupný pro klienty modulu jako modul je přístupný, protože umožňují vazby v modulu jsou kompilovány do veřejných funkcí modulu. Vazby let ve třídě jsou naopak privátní třídy.

Za normálních okolností funkce v modulech musí být kvalifikován názvem modulu při použití kódem na straně klienta. Například, pokud modul `Module1` má funkci `function1`, zadejte uživatele `Module1.function1` odkazovat na funkci.

Uživatelé modulu může používat deklarace importu Chcete-li k dispozici pro použití funkcí v rámci tohoto modulu bez je kvalifikován názvem modulu. V příkladu výše zmíněné body, můžete otevřít uživatelé modulu v takovém případě modulu s využitím open deklarace importu `Module1` a po tomto datu si `function1` přímo.

```fsharp
module Module1 =
    let function1 x = x + 1.0

module Module2 =
    let function2 x =
        Module1.function1 x

open Module1

let function3 x =
    function1 x
```

Některé moduly mají atribut [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), což znamená, že funkce, které vystavují musí být kvalifikován s názvem modulu. Tento atribut má například modulu F# seznam.

Další informace o modulů a řízení přístupu najdete v tématu [moduly](../modules.md) a [řízení přístupu](../access-control.md).

## <a name="see-also"></a>Viz také:

- [Funkce](index.md)
- [`let` Vazby ve třídách](../members/let-bindings-in-classes.md)
