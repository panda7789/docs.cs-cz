---
title: Dědičnost
description: Naučte se určit F# vztahy dědičnosti pomocí klíčového slova Inherit.
ms.date: 05/16/2016
ms.openlocfilehash: 5ab891a93528427a66e4eb8f7bfeccbf6e4d2c7e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627664"
---
# <a name="inheritance"></a>Dědičnost

Dědičnost slouží k modelování vztahu "je-a", nebo v objektově orientovaném programování.

## <a name="specifying-inheritance-relationships"></a>Určení vztahů dědičnosti

Vztahy dědičnosti určíte pomocí `inherit` klíčového slova v deklaraci třídy. V následujícím příkladu je uvedena základní syntaktická forma.

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

Třída může mít maximálně jednu přímou základní třídu. Pokud nezadáte základní třídu pomocí `inherit` klíčového slova, třída implicitně dědí z. `System.Object`

## <a name="inherited-members"></a>Zděděné členy

Pokud třída dědí z jiné třídy, metody a členy základní třídy jsou k dispozici uživatelům odvozené třídy, jako kdyby byly přímými členy odvozené třídy.

Všechny vazby let a parametry konstruktoru jsou soukromé pro třídu, a proto nemohou být z odvozených tříd k dispozici.

Klíčové slovo `base` je k dispozici v odvozených třídách a odkazuje na instanci základní třídy. Používá se jako identifikátor držitele.

## <a name="virtual-methods-and-overrides"></a>Virtuální metody a přepsání

Virtuální metody (a vlastnosti) fungují trochu jinak v F# porovnání s jinými jazyky .NET. Chcete-li deklarovat nového virtuálního člena, použijte `abstract` klíčové slovo. Provedete to bez ohledu na to, zda pro tuto metodu zadáte výchozí implementaci. Tedy úplná definice virtuální metody v základní třídě se řídí tímto vzorem:

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

A v odvozené třídě, toto přepsání této virtuální metody se řídí tímto vzorem:

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

Vynecháte-li výchozí implementaci v základní třídě, bude základní třídou abstraktní třída.

Následující příklad kódu ukazuje deklaraci nové virtuální metody `function1` v základní třídě a jak ji přepsat v odvozené třídě.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a>Konstruktory a dědičnost

V odvozené třídě musí být volán konstruktor pro základní třídu. Argumenty konstruktoru základní třídy se zobrazí v seznamu argumentů v `inherit` klauzuli. Hodnoty, které se používají, musí být určeny z argumentů dodaných konstruktoru odvozené třídy.

Následující kód ukazuje základní třídu a odvozenou třídu, kde odvozená třída volá konstruktor základní třídy v klauzuli Inherit:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

V případě více konstruktorů lze použít následující kód. První řádek konstruktorů odvozené třídy je `inherit` klauzule a pole se zobrazí jako explicitní pole, která jsou deklarována `val` pomocí klíčového slova. Další informace najdete v tématu [explicitní pole: `val` Klíčové slovo](./members/explicit-fields-the-val-keyword.md).

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

## <a name="alternatives-to-inheritance"></a>Alternativy dědičnosti

V případech, kdy je vyžadován menší modifikace typu, zvažte použití výrazu objektu jako alternativy dědičnosti. Následující příklad ilustruje použití výrazu objektu jako alternativu k vytvoření nového odvozeného typu:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

Další informace o objektových výrazech naleznete v tématu [Object Expressions](object-expressions.md).

Při vytváření hierarchií objektů zvažte použití rozlišeného sjednocení namísto dědičnosti. Rozlišené sjednocení mohou také modelovat proměnlivé chování různých objektů, které sdílejí společný celkový typ. Jedno rozlišené sjednocení často může eliminovat potřebu řady odvozených tříd, které jsou drobné variace. Informace o rozlišených sjednoceních naleznete v tématu [rozlišené sjednocení](discriminated-unions.md).

## <a name="see-also"></a>Viz také:

- [Objektové výrazy](object-expressions.md)
- [Referenční dokumentace jazyka F#](index.md)
