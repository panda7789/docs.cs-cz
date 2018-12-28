---
title: Metody
description: Zjistěte, jak F# metoda je funkce související s typem, který slouží k vystavení a implementují funkce a chování objektů a typy.
ms.date: 05/16/2016
ms.openlocfilehash: 03150cc67f79bfde58cf27e4a9d4dfa9e9ff3f55
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53614022"
---
# <a name="methods"></a>Metody

A *metoda* je funkce, který je přidružený k typu. V objektově orientované programování metody se používají k vystavení a implementaci funkce a chování objektů a typy.

## <a name="syntax"></a>Syntaxe

```fsharp
// Instance method definition.
[ attributes ]
member [inline] self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Static method definition.
[ attributes ]
static member [inline] method-name parameter-list [ : return-type ] =
    method-body

// Abstract method declaration or virtual dispatch slot.
[ attributes ]
abstract member method-name : type-signature

// Virtual method declaration and default implementation.
[ attributes ]
abstract member method-name : type-signature
[ attributes ]
default self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Override of inherited virtual method.
[ attributes ]
override self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Optional and DefaultParameterValue attributes on input parameters
[ attributes ]
[ modifier ] member [inline] self-identifier.method-name ([<Optional; DefaultParameterValue( default-value )>] input) [ : return-type ]
```

## <a name="remarks"></a>Poznámky

V předchozí syntaxi zobrazí se různé formy metoda deklarace a definice. V delší těl metod zalomení řádku následuje rovnítko (=) a tělo metody celý odsazena.

Atributy lze použít pro všechny deklarace metody. Tyto předcházet syntaxe pro definici metody a obvykle jsou uvedeny na samostatném řádku. Další informace najdete v tématu [atributy](../attributes.md).

Metody mohou být označeny `inline`. Informace o `inline`, naleznete v tématu [vložené funkce](../functions/inline-functions.md).

Non-inline metod může být použité rekurzivně v rámci typu; není nutné explicitně `rec` – klíčové slovo.

## <a name="instance-methods"></a>Instance metody

Instance metody jsou deklarovány pomocí `member` – klíčové slovo a *vlastní identifikátor*, následované tečkou (.) a název metody a parametrů. Stejně jako v případě pro `let` vazeb *seznam parametrů* může být vzoru. Obvykle, použijte metodu parametry v závorkách v podobě řazené kolekce členů, což je způsob, jak metody se zobrazí v F# když jsou vytvořeny v jiných jazycích rozhraní .NET Framework. Ale curryfikované formuláře (parametry oddělené mezerami) je také obvyklé a dalších vzorech jsou také podporovány.

Následující příklad ukazuje definici a využívání instance neabstraktní metoda.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

V rámci metody instance nepoužívejte k přístupu pole definovaná pomocí vazby let identifikátoru samotného. Při přístupu k ostatním členům a vlastnosti, použijte vlastní identifikátor.

## <a name="static-methods"></a>Statické metody

Klíčové slovo `static` slouží k určení, že metodu lze volat bez instance a není přidružen k instanci objektu. V opačném případě metody jsou metody instance.

V příkladu v následující části zobrazuje pole deklarovaná s `let` – klíčové slovo, vlastnost členy deklarované s `member` – klíčové slovo a statické metody deklarované s `static` – klíčové slovo.

Následující příklad ukazuje definici a použití statické metody. Předpokládejme, že jsou tyto definice metod v `SomeType` třídy v předchozí části.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a>Abstraktní a virtuální metody

Klíčové slovo `abstract` označuje, že metoda má virtuální odeslání slot a nemusí obsahovat definici třídy. A *virtuální odeslání slotu* je záznam v tabulce vnitřně udržované funkcí, který se používá v době běhu k vyhledání virtuální funkce se volá v typu objektově orientovaný. Mechanismus virtuální odeslání je mechanismus, který implementuje *polymorfismus*, důležitou funkcí objektově orientované programování. Je třída, která má alespoň jeden abstraktní metody bez definice *abstraktní třída*, což znamená, že nemohou být vytvořeny žádné instance této třídy. Další informace o abstraktních tříd naleznete v tématu [abstraktní třídy](../abstract-classes.md).

Deklarace abstraktní metody nezahrnují tělo metody. Název metody je místo, následovaný dvojtečkou (:) a podpis typu metody. Podpis typu metody je stejný jako uvedeny technologií IntelliSense při pozastavení ukazatele myši nad název metody v editoru Visual Studio Code, s výjimkou bez názvy parametrů. Typ signatury jsou také zobrazí interpret, fsi.exe, když interaktivně pracovat. Podpis typu metody je tvořen přidáním výpis na typy parametrů, za nímž následuje návratový typ se symboly příslušné oddělovače. Curryfikované parametrů je odděleno `->` a parametry řazené kolekce členů jsou odděleny `*`. Vrácená hodnota je vždy oddělená od argumenty podle `->` symbol. Závorky lze použít k seskupení složité parametry, například když typ funkce je parametr, nebo k označení, když řazené kolekce členů je zpracováván jako jediný parametr, nikoli jako dva parametry.

Můžete také udělit abstraktní metody výchozí definice přidání definice třídy a použitím `default` – klíčové slovo, jak je znázorněno v syntaxi bloku v tomto tématu. Abstraktní metody, která má definici ve stejné třídě, je ekvivalentní virtuální metody v jiných jazycích rozhraní .NET Framework. Určuje, jestli existuje definice, `abstract` – klíčové slovo vytvoří nový slot odbavení v tabulce virtuální funkce třídy.

Bez ohledu na to, zda základní třída implementuje abstraktní metody mohou odvozené třídy poskytují implementace abstraktní metody. Chcete-li implementovat abstraktní metoda v odvozené třídě, definujte metodu, která má stejný název a signaturu v odvozené třídě, s výjimkou použití `override` nebo `default` – klíčové slovo a poskytnout tělo metody. Klíčová slova `override` a `default` přesně stejný význam. Použít `override` Pokud přepisuje nová metoda implementaci základní třídy; použijte `default` při vytváření implementaci ve třídě stejný jako původní deklarace abstraktní. Nepoužívejte `abstract` – klíčové slovo v metodě, která implementuje metodu, která byla deklarovaná jako abstraktní základní třídy.

Následující příklad ukazuje abstraktní metody `Rotate` , který má výchozí implementaci ekvivalent virtuální metody rozhraní .NET Framework.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

Následující příklad ukazuje odvozené třídy, která přepíše metodu základní třídy. V takovém případě přepsání mění chování tak, aby metoda nemá žádný účinek.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a>Přetížené metody

Přetížené metody jsou metody, které mají stejný název v daného typu, ale mají různé argumenty. V F#, volitelné argumenty se obvykle používají místo přetížené metody. Ale přetížené metody jsou povoleny v jazyce, za předpokladu, že jsou argumenty v podobě řazené kolekce členů, není curryfikované formuláře.

## <a name="optional-arguments"></a>Nepovinné argumenty.

Počínaje F# 4.1, je také možné volitelné argumenty s výchozí hodnotou parametru do metody.  Toto je usnadňují spolupráci s kódem C#.  Následující příklad ukazuje syntaxi:

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    __.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

Všimněte si, že hodnota předaná pro `DefaultParameterValue` musí shodovat s typem vstupu.  V ukázce výše, je `int`.  Pokus o předání hodnot jiných než celých čísel do `DefaultParameterValue` způsobí chybu kompilace.

## <a name="example-properties-and-methods"></a>Příklad: Vlastnosti a metody

Následující příklad obsahuje typ, který obsahuje příklady polí, soukromé funkce, vlastnosti a statické metody.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a>Viz také:

- [Členové](index.md)