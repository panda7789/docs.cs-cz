---
title: Dědičnost
description: Naučte se, jak zadat f# dědičnost vztahy pomocí 'inherit' klíčové slovo.
ms.date: 05/16/2016
ms.openlocfilehash: 5ab891a93528427a66e4eb8f7bfeccbf6e4d2c7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400286"
---
# <a name="inheritance"></a>Dědičnost

Dědičnost se používá k modelování vztahu "is-a" nebo subtypingu v objektově orientovaném programování.

## <a name="specifying-inheritance-relationships"></a>Určení vztahů dědičnosti

Vztahy dědičnosti zadejte `inherit` pomocí klíčového slova v deklaraci třídy. Základní syntaktická forma je uvedena v následujícím příkladu.

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

Třída může mít maximálně jednu přímou základní třídu. Pokud nezadáte základní třídu pomocí `inherit` klíčového slova, třída `System.Object`implicitně dědí z .

## <a name="inherited-members"></a>Zdědění členové

Pokud třída dědí z jiné třídy, metody a členy základní třídy jsou k dispozici uživatelům odvozené třídy, jako by byli přímými členy odvozené třídy.

Všechny let vazby a parametry konstruktoru jsou soukromé třídy a proto nelze přistupovat z odvozené třídy.

Klíčové `base` slovo je k dispozici v odvozených třídách a odkazuje na instanci základní třídy. Používá se jako vlastní identifikátor.

## <a name="virtual-methods-and-overrides"></a>Virtuální metody a lokální změny

Virtuální metody (a vlastnosti) fungují v jazyce F# poněkud odlišně ve srovnání s jinými jazyky .NET. Chcete-li deklarovat nový `abstract` virtuální člen, použijte klíčové slovo. To bez ohledu na to, zda zadáte výchozí implementaci pro tuto metodu. Úplná definice virtuální metody v základní třídě se tedy řídí tímto vzorem:

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

A v odvozené třídě přepsání této virtuální metody následuje tento vzor:

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

Pokud vyneche výchozí implementaci v základní třídě, základní třída se stane abstraktní třídou.

Následující příklad kódu ilustruje deklaraci nové `function1` virtuální metody v základní třídě a jak ji přepsat v odvozené třídě.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a>Konstruktory a dědičnost

Konstruktor pro základní třídu musí být volána v odvozené třídě. Argumenty pro konstruktor základní třídy se zobrazí `inherit` v seznamu argumentů v klauzuli. Hodnoty, které jsou použity, musí být určeny z argumentů poskytnutých konstruktoru odvozené třídy.

Následující kód ukazuje základní třídu a odvozenou třídu, kde odvozená třída volá konstruktor základní třídy v klauzuli inherit:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

V případě více konstruktorů lze použít následující kód. První řádek konstruktorů odvozené třídy `inherit` je klauzule a pole se zobrazí `val` jako explicitní pole, která jsou deklarována pomocí klíčového slova. Další informace naleznete [v tématu Explicitní pole: `val` Klíčové slovo](./members/explicit-fields-the-val-keyword.md).

```fsharp
type BaseClass =
    val string1 : string
    new (str) = { string1 = str }
    new () = { string1 = "" }

type DerivedClass =
    inherit BaseClass

    val string2 : string
    new (str1, str2) = { inherit BaseClass(str1); string2 = str2 }
    new (str2) = { inherit BaseClass(); string2 = str2 }

let obj1 = DerivedClass("A", "B")
let obj2 = DerivedClass("A")
```

## <a name="alternatives-to-inheritance"></a>Alternativy k dědičnosti

V případech, kdy je požadována menší změna typu, zvažte použití výrazu objektu jako alternativy k dědičnosti. Následující příklad ilustruje použití výrazu objektu jako alternativu k vytvoření nového odvozeného typu:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

Další informace o výrazech objektů naleznete v [tématu Object Expressions](object-expressions.md).

Při vytváření hierarchií objektů zvažte použití discriminated unie namísto dědičnosti. Discriminated sjednocení můžete také modelovat různé chování různých objektů, které sdílejí společný celkový typ. Jeden discriminated unie může často eliminovat potřebu počet odvozených tříd, které jsou malé varianty navzájem. Informace o discriminated sjednocení, naleznete [v tématu discriminated sjednocení](discriminated-unions.md).

## <a name="see-also"></a>Viz také

- [Objektové výrazy](object-expressions.md)
- [Referenční příručka jazyka F#](index.md)
