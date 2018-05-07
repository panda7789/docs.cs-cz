---
title: let – vazby (F#)
description: 'Naučte se používat F # umožní vazby, která přidruží identifikátor hodnota nebo funkce.'
ms.date: 05/16/2016
ms.openlocfilehash: bcdf01747c2a1d0ba9a894188dae1d42acdf9104
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="let-bindings"></a>let – vazby

A *vazby* přidruží identifikátor hodnota nebo funkce. Můžete použít `let` – klíčové slovo vytvořit vazbu název hodnotu nebo funkce.

## <a name="syntax"></a>Syntaxe

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a>Poznámky

`let` – Klíčové slovo se používá v vazby výrazy a definovat hodnoty nebo funkce hodnoty pro jeden nebo více názvů. Nejjednodušší forma útoku `let` výraz váže název na hodnotu simple následujícím způsobem.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

Pokud oddělíte výraz z identifikátor pomocí nového řádku, musíte odsazovat každý řádek výrazu, jako v následujícím kódu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

Místo pouze název můžete zadat vzor, který obsahuje názvy, například řazené kolekce členů, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

*Textu výraz* je výraz, ve kterém se používají názvy. Výraz text se zobrazí na vlastním řádku odsazeny řádek až přesně s první znak argumentu `let` – klíčové slovo:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

A `let` vazby můžete zobrazit na úrovni modulu, v definici typu třídy nebo v místní obory, například definici funkce. A `let` vazba na nejvyšší úrovni v modulu nebo typ třídy nemusí obsahovat výraz text, ale na jiných úrovních oboru, je vyžadován výraz textu. Vázané názvy jsou použitelné za bod definice, ale ne v libovolném bodě před `let` vazby zobrazí se, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]
    
## <a name="function-bindings"></a>Vazby funkce

Vazby funkce v podle pravidla pro hodnotu vazby, s tím rozdílem, že funkce vazby obsahovat název funkce a parametry, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

Parametry jsou obecně vzory, třeba vzor řazené kolekce členů:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

A `let` vazby výraz vyhodnocen jako hodnota poslední výrazu. Proto v následujícím příkladu kódu, hodnota `result` se počítá z `100 * function3 (1, 2)`, který se vyhodnocuje `300`.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

Další informace najdete v tématu [funkce](index.md).

## <a name="type-annotations"></a>Typ poznámky

Můžete určit typy parametrů zahrnutím dvojtečkou (:), za nímž následuje název typu, všechny uzavřený v závorkách. Můžete také určit typ vrácené hodnoty připojením dvojtečkou a typ po poslední parametr. Úplný typ poznámky pro `function1`, s celými čísly jako typy parametrů, vypadat takto.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

Pokud neexistují žádné parametry explicitního typu, odvození typu slouží k určení typů parametrů funkce. To může zahrnovat automaticky generalizací typ parametru být obecný.

Další informace najdete v tématu [Automatická generalizace](../generics/automatic-generalization.md) a [odvození typu](../type-inference.md).

## <a name="let-bindings-in-classes"></a>Vazby let ve třídách

A `let` vazba může vyskytovat typu třídy, ale není v struktura nebo typu záznamu. Pokud chcete používat umožňují vazby v typu třídy, třídu musí mít primární konstruktor. Konstruktor parametry musí být uvedena po název typu v definici třídy. A `let` vazby v typu třídy definuje privátní pole a členů pro tento typ třídy a, společně s `do` vazeb v typu, forms kód pro primární konstruktor pro typ. Následující příklady kódu ukazují třídu `MyClass` s privátním polím `field1` a `field2`.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

Obory z `field1` a `field2` jsou omezeny na typ, ve které jsou deklarované. Další informace najdete v tématu [ `let` vazby do ve třídách](../members/let-bindings-in-classes.md) a [třídy](../classes.md).

## <a name="type-parameters-in-let-bindings"></a>Parametry typu v let – vazby

A `let` vazby na úrovni modulu v typu, nebo výpočetní výraz může mít parametry explicitní typu. Umožňují vazby ve výrazu, například v definici funkce nemůže mít parametry typu. Další informace najdete v tématu [obecné typy](../generics/index.md).

## <a name="attributes-on-let-bindings"></a>Atributy na let – vazby

Atributy lze použít na nejvyšší úrovni `let` vazby v modulu, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]
    
## <a name="scope-and-accessibility-of-let-bindings"></a>Obor a usnadnění umožňují vazby

Rozsah entity deklarovat s umožňují vazba je omezený na část obsahující oboru (například funkce, modul, soubor nebo třída), jakmile se objeví vazby. Proto lze říci, že umožňují vazbu představuje název do oboru. V modulu umožňují vázané hodnota nebo funkce je dostupné klientům modulu tak dlouho, dokud je přístupný, modul, protože umožňují vazby v modulu se zkompiluje do veřejných funkcí modulu. Umožňují vazby v třídě jsou naopak privátní k třídě.

Za normálních okolností funkce v modulech musí být kvalifikovaný název modulu při použití kódem na straně klienta. Například, pokud modul `Module1` má funkci `function1`, by uživatelé zadat `Module1.function1` odkazovat na funkce.

Uživatelé modulu mohou využít importu deklarace, aby se funkce v rámci tohoto modulu k dispozici pro použití jako kvalifikované název modulu. V příkladu právě uvedený, můžete otevřít uživatelé modulu v takovém případě modul pomocí otevřete deklarace importu `Module1` a následně odkazovat na `function1` přímo.

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

Některé moduly mají atribut [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), což znamená, že funkce, které se zveřejňují musí být kvalifikovaný pomocí názvu modulu. Například modul F # seznamu má tento atribut.

Další informace o moduly a řízení přístupu najdete v tématu [moduly](../modules.md) a [řízení přístupu](../access-control.md).

## <a name="see-also"></a>Viz také

[Funkce](index.md)

[`let` Vazby do ve třídách](../members/let-bindings-in-classes.md)
