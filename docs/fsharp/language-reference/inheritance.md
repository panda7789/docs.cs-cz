---
title: Dědičnost
description: Zjistěte, jak určit F# vztahy dědičnosti pomocí klíčového slova 'inherit'.
ms.date: 05/16/2016
ms.openlocfilehash: 2fad2ddafbc0174903d3d24be3ce5412f7e1f9ed
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641825"
---
# <a name="inheritance"></a>Dědičnost

Dědičnost se používají k modelování vztah "je a", nebo vytvoření podtypů v objektově orientované programování.

## <a name="specifying-inheritance-relationships"></a>Určení vztahy dědičnosti

Zadejte vztahy dědičnosti pomocí `inherit` – klíčové slovo v deklaraci třídy. Základní formulář syntaktické je znázorněno v následujícím příkladu.

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

Třída může mít maximálně jednu přímou základní třídu. Pokud nezadáte základní třídy pomocí `inherit` – klíčové slovo, třídy implicitně dědí z `System.Object`.

## <a name="inherited-members"></a>Zděděné členy

Pokud třída dědí z jiné třídy, metody a členy základní třídy jsou dostupné uživatelům odvozené třídy, jako by byly přímé členy odvozené třídy.

Některé vazby let a parametry konstruktoru jsou privátní pro třídu a proto ji nejde přistupovat z odvozených tříd.

Klíčové slovo `base` je k dispozici v odvozených třídách a odkazuje na základní třídu instance. Používá se jako vlastní identifikátor.

## <a name="virtual-methods-and-overrides"></a>Virtuální metody a přepsání

Virtuální metody (a vlastnosti) pracují trochu odlišně v F# porovnání s jinými jazyky rozhraní .NET. Chcete-li deklarovat nový virtuální člen, můžete použít `abstract` – klíčové slovo. Můžete to provést bez ohledu na to, zda poskytuje výchozí implementaci pro danou metodu. Kompletní definici virtuální metodu v základní třídě proto používá tento vzor:

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

A přepsání této virtuální metody v odvozené třídě, následuje tento model:

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

Vynecháte-li výchozí implementace v základní třídě, stane základní třídy abstraktní třídy.

Následující příklad kódu znázorňuje deklaraci novou virtuální metodu `function1` v základní třídě a jak přepsat v odvozené třídě.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a>Konstruktory a dědičnost

Musí být volána konstruktor základní třídy v odvozené třídě. Argumenty pro konstruktor základní třídy se zobrazí v seznamu argumentů v `inherit` klauzuli. Argumenty předány konstruktoru odvozené třídy musí určit hodnoty, které se používají.

Následující kód ukazuje základní třídu a odvozené třídy, kde odvozená třída volá konstruktor základní třídy v klauzuli dědičnosti:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

V případě více konstruktorů můžete použít následující kód. První řádek konstruktory odvozené třídy je `inherit` klauzule a pole se zobrazí jako explicitní pole, které jsou deklarovány pomocí `val` – klíčové slovo. Další informace najdete v tématu [explicitní pole: `val` – Klíčové slovo](members/explicit-fields-the-val-keyword.md).

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

V případech, kdy se vyžaduje méně závažnou změnu typu zvažte použití výrazu objektu jako alternativu k dědičnosti. Následující příklad ukazuje použití výrazu objektu jako alternativu k vytváření nového odvozeného typu:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

Další informace o objektových výrazů naleznete v tématu [objektové výrazy](object-expressions.md).

Při vytváření hierarchie objektů, zvažte použití diskriminované sjednocení namísto dědičnosti. Rozlišovaná sjednocení můžou také modelu měnit chování různých objektů, které sdílejí společný typ celkové. Jeden diskriminované sjednocení může často eliminovat potřebu počet odvozených tříd, které jsou menší variant. Informace o rozlišovaná sjednocení, naleznete v tématu [Rozlišované sjednocení](discriminated-unions.md).

## <a name="see-also"></a>Viz také:

- [Objektové výrazy](object-expressions.md)
- [Referenční dokumentace jazyka F#](index.md)
