---
title: "Abstraktní třídy (F#)"
description: "Další informace o F # abstraktní třídy, které nechte některé nebo všechny členy Neimplementovaný a představují běžné funkce různého typu typy objektů."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: a3dcc335-433b-4672-ac2d-ae6b11b816f3
ms.openlocfilehash: 209bcca70318db59506011b1f2bb74a09bf3814a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="abstract-classes"></a>Abstraktní třídy

*Abstraktní třídy* jsou třídy, která opouští některé nebo všechny členy Neimplementovaný, tak, aby implementace lze zadat odvozené třídy.

## <a name="syntax"></a>Syntaxe

```fsharp
// Abstract class syntax.
[<AbstractClass>]
type [ accessibility-modifier ] abstract-class-name =
[ inherit base-class-or-interface-name ]
[ abstract-member-declarations-and-member-definitions ]

// Abstract member syntax.
abstract member member-name : type-signature
```

## <a name="remarks"></a>Poznámky
V objektově orientované programování abstraktní třída se používá jako základní třída hierarchie a představuje běžné funkce různého typu typy objektů. Jako název "abstraktní" znamená, abstraktní třídy často neodpovídají přímo na konkrétní entity v doméně problému. Však představují co mnoho různých konkrétní entit mají společnou.

Abstraktní třídy musí mít `AbstractClass` atribut. Může být implementováno a Neimplementovaný členy. Použití podmínek *abstraktní* při použití třídy je stejný jako jinými jazyky rozhraní .NET; však použití podmínek *abstraktní* při použití metody (a vlastnosti) je mírně liší v F # z jeho použijte v jinými jazyky rozhraní .NET. V F #, když je označené jako metodu `abstract` – klíčové slovo, to znamená, že člen má položku, označuje jako *virtuální odesílání slotu*, do interní tabulky pro tento typ virtuální funkce. Jinými slovy, že je metoda virtuální, i když `virtual` – klíčové slovo se nepoužívá v jazyce F #. Klíčové slovo `abstract` se používá pro virtuální metody bez ohledu na to, zda je metoda implementována. Prohlášení o slot virtuální odesílání je oddělené od definici metody pro tento slot odesílání. Proto ekvivalentní F # virtuální metoda deklarace a definice v jiném jazyce .NET je kombinací deklarace abstraktní metody i samostatné definice, pomocí `default` – klíčové slovo nebo `override` – klíčové slovo. Další informace a příklady naleznete v tématu [metody](members/methods.md).

Třída je považován za abstraktní pouze v případě, že existují abstraktní metody, které jsou deklarované, ale není definován. Proto tříd, které mají abstraktní metody nejsou nezbytně abstraktní třídy. Pokud třída má undefined abstraktní metody, nepoužívejte **abstractclass –** atribut.

V předchozích syntaxi *modifikátor dostupnosti* může být `public`, `private` nebo `internal`. Další informace najdete v tématu [řízení přístupu](access-control.md).

Jako u jiných typů, může mít abstraktní třídy základní třídy a jeden nebo více základní rozhraní. Každý základní třídy nebo rozhraní se zobrazí na samostatném řádku společně s `inherit` – klíčové slovo.

Definici typu abstraktní třídy mohou obsahovat plně definované členy, ale může také obsahovat abstraktní členy. Syntaxe pro abstraktní členy se zobrazí samostatně v předchozí syntaxi. V této syntaxe *podpis typu* člena je seznam, který obsahuje parametr typy v pořadí a návratové typy oddělená `->` tokeny nebo `*` tokeny podle potřeby pro curryfikované a tupled Parametry. Syntaxe pro podpisy člen abstraktní typ je stejný jako použitého v podpisu souborů a zobrazená technologii IntelliSense v editoru kódu sady Visual Studio.

Následující kód ukazuje abstraktní třídu tvar, který má jinou než abstraktní odvozené třídy hranaté a kruh. Příklad ukazuje postup používání abstraktních tříd, metod a vlastností. V příkladu představuje abstraktní třídu tvar běžných elementech kruh konkrétní entity a hranaté. Běžné funkce všech tvarů (v dvourozměrná souřadnicový systém) jsou abstrahované odhlašování do třídy tvaru: pozici na mřížky, úhel otočení a vlastnosti oblasti a hraniční. To může být přepsána, s výjimkou pozice, chování, které nelze změnit jednotlivých tvarů.

Jako kruh třída, která je otočení neutrální z důvodu jeho symetrie lze přepsat metodu otočení. Proto v třídě kruh metodu otočení nahrazuje metodu, která se nic nestane.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

**Výstup:**

```
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a>Viz také
[Třídy](classes.md)

[Členy](members/index.md)

[Metody](members/methods.md)

[Vlastnosti](members/Properties.md)
