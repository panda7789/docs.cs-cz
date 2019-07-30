---
title: let – vazby
description: Naučte se používat F# vazbu let, která přidruží identifikátor k hodnotě nebo funkci.
ms.date: 05/16/2016
ms.openlocfilehash: 654631c7d1c48d8737e6098c98efee54cfdd91be
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630636"
---
# <a name="let-bindings"></a>let – vazby

*Vazba* přidruží identifikátor k hodnotě nebo funkci. `let` Klíčové slovo slouží k vytvoření vazby názvu k hodnotě nebo funkci.

## <a name="syntax"></a>Syntaxe

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a>Poznámky

`let` Klíčové slovo se používá ve výrazech vazby k definování hodnot nebo hodnot funkcí pro jeden nebo více názvů. Nejjednodušší forma `let` výrazu váže název k jednoduché hodnotě, jak je znázorněno níže.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

Pokud oddělíte výraz od identifikátoru pomocí nového řádku, je nutné odsadit každý řádek výrazu, jak je uvedeno v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

Namísto pouze názvu lze zadat vzor, který obsahuje názvy, například řazené kolekce členů, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

*Výraz body* je výraz, ve kterém jsou názvy použity. Výraz textu se zobrazí na vlastním řádku, odsazený tak, aby přesně odpovídal prvnímu znaku v `let` klíčovém slově:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

`let` Vazba se může zobrazit na úrovni modulu, v definici typu třídy nebo v místních oborech, jako je například v definici funkce. `let` Vazba na nejvyšší úrovni v modulu nebo v typu třídy nemusí mít výraz body, ale v jiných úrovních oboru je požadován výraz textu. Vázané názvy jsou použitelné po bodě definice, ale ne v jakémkoli bodě před `let` zobrazením vazby, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]

## <a name="function-bindings"></a>Vazby funkcí

Vazby funkcí následují pravidla pro vazby hodnot, s výjimkou, že vazby funkcí zahrnují název funkce a parametry, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

Obecně platí, že parametry jsou vzory, jako je například vzor řazené kolekce členů:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

Výraz `let` vazby se vyhodnocuje na hodnotu posledního výrazu. Proto v následujícím příkladu kódu `result` je hodnota vypočítána z `100 * function3 (1, 2)` `300`, která je vyhodnocena jako.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

Další informace najdete v tématu [funkce](index.md).

## <a name="type-annotations"></a>Anotace typu

Můžete určit typy pro parametry zahrnutím dvojtečky (:) následováno názvem typu, který je uzavřen v závorkách. Můžete také zadat typ návratové hodnoty připojením dvojtečky a typu za posledním parametrem. Úplné poznámky typu pro `function1`, s celými čísly jako typy parametrů, by byly následující.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

Pokud nejsou k dispozici žádné explicitní parametry typu, použije se odvození typu k určení typů parametrů funkcí. To může zahrnovat automatické generalizace typu parametru, který má být obecný.

Další informace naleznete v tématu [automatické generalizace](../generics/automatic-generalization.md) a [odvození typu](../type-inference.md).

## <a name="let-bindings-in-classes"></a>Vazby let ve třídách

`let` Vazba se může objevit v typu třídy, ale ne v typu struktury nebo záznamu. Chcete-li použít vazbu let v typu třídy, třída musí mít primární konstruktor. Parametry konstruktoru se musí vyskytovat za názvem typu v definici třídy. Vazba v typu třídy definuje soukromá pole a členy pro daný typ třídy a společně s `do` vazbami v typu tvoří kód pro primární konstruktor pro daný typ. `let` Následující příklady kódu ukazují třídu `MyClass` s privátními poli `field1` a `field2`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

Obory `field1` a `field2` jsou omezeny na typ, ve kterém jsou deklarovány. Další informace naleznete v tématu [ `let` vazby v třídách](../members/let-bindings-in-classes.md) a [třídách](../classes.md).

## <a name="type-parameters-in-let-bindings"></a>Parametry typu ve vazbách let

`let` Vazba na úrovni modulu, v typu nebo ve výrazu výpočtu může mít explicitní parametry typu. Vazba let ve výrazu, například v rámci definice funkce, nemůže mít parametry typu. Další informace najdete v tématu [Obecné typy](../generics/index.md).

## <a name="attributes-on-let-bindings"></a>Atributy u vazeb let

Atributy lze použít u vazeb nejvyšší úrovně `let` v modulu, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]

## <a name="scope-and-accessibility-of-let-bindings"></a>Rozsah a přístupnost pro vazby let

Rozsah entity deklarované pomocí vazby let je omezen na část nadřazeného oboru (například funkce, modulu, souboru nebo třídy) Po zobrazení vazby. Proto je možné říci, že vazba let zavádí název do oboru. V modulu je pro klienty modulu přístupná hodnota nebo funkce s vazbou, pokud je modul dostupný, protože vazby let v modulu jsou kompilovány do veřejných funkcí modulu. Naproti tomu mají vazby ve třídě pro třídu privátní.

Funkce v modulech musí být obvykle kvalifikovány názvem modulu při použití klientským kódem. Například pokud má modul `Module1` funkci `function1`, uživatelé zadávají `Module1.function1` odkaz na funkci.

Uživatelé modulu mohou použít deklaraci import, aby byly funkce v rámci tohoto modulu dostupné pro použití bez kvalifikovaného názvu modulu. V příkladu, který je právě zmíněn, uživatelé modulu můžou v takovém případě otevřít modul pomocí otevřené `Module1` deklarace importu a následně na `function1` odkaz přímo.

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

Některé moduly mají atribut [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), což znamená, že funkce, které zveřejňují, musí být kvalifikovány názvem modulu. Například modul F# seznamu má tento atribut.

Další informace o modulech a řízení přístupu najdete v tématech [moduly](../modules.md) a [Access Control](../access-control.md).

## <a name="see-also"></a>Viz také:

- [Funkce](index.md)
- [`let`Vazby ve třídách](../members/let-bindings-in-classes.md)
