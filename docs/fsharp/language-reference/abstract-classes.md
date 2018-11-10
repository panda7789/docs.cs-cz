---
title: Abstraktní třídy (F#)
description: Další informace o F# abstraktní třídy, které ponechte některé nebo všechny členy neimplementované a představují běžné funkce různé typy objektů.
ms.date: 05/16/2016
ms.openlocfilehash: 7e1bb9daca7e8a3b442cd7fb02ef99bb6a2085cb
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "43745447"
---
# <a name="abstract-classes"></a>Abstraktní třídy

*Abstraktní třídy* jsou třídy, které ponechte některé nebo všechny členy neimplementované, takže může být poskytnuty implementace z odvozených tříd.

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

Objektově orientované programování v abstraktní třída se používá jako základní třída v hierarchii a představuje běžné funkce různé typy objektů. Jak již název "abstraktní" napovídá, abstraktní třídy často nemusí odpovídat přímo na konkrétní entity v doméně problému. Však představují co mnoho entit různých konkrétní mají společnou.

Abstraktní třídy musí mít `AbstractClass` atribut. Může být implementována a neimplementované členy. Používání pojmů *abstraktní* při použití u třídy je stejný jako v jiných jazycích .NET, ale používání pojmů *abstraktní* při použití metody (a vlastnosti) je trochu jiné v jazyce F# z jeho použijte v jiných jazycích rozhraní .NET. V jazyce F#, pokud metoda je označena `abstract` – klíčové slovo, to znamená, že člen má záznam, označované jako *virtuální odeslání slotu*, do interní tabulky virtuálních funkcí pro daný typ. Jinými slovy, metoda je virtuální, i když `virtual` – klíčové slovo v jazyce F# nepoužívá. Klíčové slovo `abstract` se používá pro virtuální metody bez ohledu na to, zda je metoda implementována. Deklarace slot virtuální odeslání nesouvisí s definicí metody pro tento slot odeslání. Proto ekvivalent F# virtuální metoda deklarace a definice v jiném jazyce .NET je kombinace deklarací abstraktní metody a samostatné definice, buď `default` – klíčové slovo nebo `override` – klíčové slovo. Další informace a příklady najdete v tématu [metody](members/methods.md).

Třída je považován za abstraktní pouze v případě, že existují abstraktní metody, které jsou deklarovány, ale není definovaný. Třídy obsahující abstraktní metody proto nejsou nutně abstraktní třídy. Pokud třída má nedefinované abstraktní metody, nepoužívejte **AbstractClass** atribut.

V předchozí syntaxi *modifikátor dostupnosti* může být `public`, `private` nebo `internal`. Další informace najdete v tématu [řízení přístupu](access-control.md).

Stejně jako u jiných typů abstraktní třídy může mít základní třídu a jeden nebo více základní rozhraní. Každá základní třídu nebo rozhraní se objeví na samostatném řádku spolu s `inherit` – klíčové slovo.

Definice typu abstraktní třídy mohou obsahovat členy plně definovaná, ale může také obsahovat abstraktní členy. Syntaxe pro abstraktní členy se zobrazí samostatně v předchozí syntaxi. V této syntaxe *podpis typu* členu je seznam, který obsahuje parametr typů v pořadí a návratové typy oddělené `->` tokeny a/nebo `*` tokeny podle potřeby pro curryfikované a řazené kolekce členů Parametry. Syntaxe pro signatury typů abstraktní člen je stejná jako, který používá v podpisu souborů a, který se zobrazí v IntelliSense v editoru kódu sady Visual Studio.

Následující kód znázorňuje abstraktní třídu obrazec, který má dvě neabstraktní odvozené třídy, hranaté a kruh. Tento příklad ukazuje, jak použít abstraktní třídy, metody a vlastnosti. V tomto příkladu představuje abstraktní třídu tvar společné prvky konkrétní entity kruhu a hranaté. Společné funkce všech tvarů (v dvojrozměrné souřadnice systému) do třídy tvar abstrahují out: pozice v mřížce, úhel otáčení a obsah a obvod vlastnosti. Ty lze přepsat, s výjimkou pozici, chování, které nelze změnit jednotlivých tvarů.

Stejně jako v kruhu třídy, která je neutrální otočení z důvodu jeho symetrie lze přepsat metodu otočení. Proto ve třídě kruh otočení metoda nahrazuje metodu, která nemá žádný účinek.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

**Výstup:**

```
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a>Viz také:

- [Třídy](classes.md)
- [Členové](members/index.md)
- [Metody](members/methods.md)
- [Vlastnosti](members/Properties.md)
