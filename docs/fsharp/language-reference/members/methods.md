---
title: Metody (F#)
description: "Zjistěte, jak metodu F # je přidružený k typu, které se používají k vystavení a implementovat funkce a chování objekty a typy funkce."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 1febab3b-c922-49c6-889f-c22db107710c
ms.openlocfilehash: dae31abe6bb0773671b889646c9cceb410a492cd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="methods"></a>Metody

A *metoda* je funkce, který je přidružený k typu. V objektově orientované programování metody se používají k vystavení a implementovat funkce a chování objekty a typy.


## <a name="syntax"></a>Syntaxe

```fsharp
// Instance method definition.
[ attributes ]
member [inline] self-identifier.method-nameparameter-list [ : return-type ]=
    method-body

// Static method definition.
[ attributes ]
static member [inline] method-nameparameter-list [ : return-type ]=
    method-body

// Abstract method declaration or virtual dispatch slot.
[ attributes ]
abstract member self-identifier.method-name : type-signature

// Virtual method declaration and default implementation.
[ attributes ]
abstract member [inline] self-identifier.method-name : type-signature
[ attributes ]
default member [inline] self-identifier.method-nameparameter-list[ : return-type ] =
    method-body

// Override of inherited virtual method.
[ attributes ]
override member [inline] self-identifier.method-nameparameter-list [ : return-type ]=
    method-body

// Optional and DefaultParameterValue attributes on input parameters
[ attributes ]
[ modifier ] member [inline] self-identifier.method-name ([<Optional; DefaultParameterValue([ default-value ])>] input) [ : return-type ]
```

## <a name="remarks"></a>Poznámky
V předchozích syntaxe se zobrazí různé formy metoda deklarace a definice. V delší metoda subjekty konec řádku následuje rovná se (=) a metoda celý text odsazeno.

Atributy je použít pro všechny deklarace metody. Tyto předcházet syntaxe definici metody a obvykle jsou uvedeny na samostatném řádku. Další informace najdete v tématu [atributy](../attributes.md).

Může být označen metody `inline`. Informace o `inline`, najdete v části [vložené funkce](../functions/inline-functions.md).

Metody bez vložené může být použité rekurzivně v rámci typu; není nutné explicitně povoleno používat `rec` – klíčové slovo.


## <a name="instance-methods"></a>Instance metody
Instance metody jsou deklarovány s `member` – klíčové slovo a *vlastní identifikátor*, za nímž následují tečkou (.) a název metody a parametry. Stejně jako v případě pro `let` vazeb *seznam parametrů* může být vzorek. Obvykle je uzavřít metoda objevit parametry v závorkách v podobě řazené kolekce členů, což je způsob, jak metody v jazyce F # při jejich vytváření v jiných jazycích rozhraní .NET Framework. Ale curryfikované formuláře (parametry, oddělené mezerami) je běžné, že a dalšími vzory jsou také podporovány.

Následující příklad ilustruje definice a použití metody neabstraktní instance.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

V rámci metody instance nepoužívejte vlastní identifikátor přístup pole definované za použití umožňují vazby. Při přístupu k ostatním členům a vlastnosti, použijte vlastní identifikátor.


## <a name="static-methods"></a>Statické metody
Klíčové slovo `static` slouží k určení, zda metoda může být volána bez instance a není přidružen k instanci objektu. Jinak jsou metody instance metody.

Příklad v další části ukazuje pole deklarovat s `let` – klíčové slovo, vlastnost členy deklarovat s `member` – klíčové slovo a statickou metodu deklarovat s `static` – klíčové slovo.

Následující příklad ilustruje definice a používání statických metod. Předpokládejme, že jsou tyto definice metoda v `SomeType` – třída v předchozí části.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a>Abstraktní a virtuální metody
Klíčové slovo `abstract` označuje, že metoda má slot virtuální odesílání a nemusí mít definici ve třídě. A *virtuální odesílání slotu* je záznam v tabulce interně zachována funkcí, která se používá v době běhu k vyhledání virtuální funkce volá typ objektově orientovaný. Tento mechanismus virtuální odesílání je mechanismus, který implementuje *polymorfismus*, důležitou součást objektově orientované programování. Je třída, která má alespoň jednu metodu abstraktní bez definice *abstraktní třída*, což znamená, že nelze vytvořit žádné instance této třídy. Další informace o abstraktní třídy najdete v tématu [abstraktní třídy](../abstract-classes.md).

Deklarace abstraktní metodu nezahrnují těla metody. Název metody, je místo toho následovaný dvojtečkou (:) a typ podpis metody. Typ podpis metody je stejný jako zobrazená technologii IntelliSense, když krátce umístit ukazatel myši nad název metody v editoru Visual Studio Code, s výjimkou bez názvy parametrů. Typ podpisy zobrazena překladač fsi.exe, také, když pracujete interaktivně. Typ podpis metody je tvořen výpis se typy parametrů, za nímž následuje návratový typ se symboly odpovídající oddělovače. Curryfikované parametry jsou odděleny `->` a jsou odděleny řazené kolekce členů parametry `*`. Návratová hodnota je vždy oddělená od argumenty podle `->` symbol. Závorky lze použít k seskupení komplexní parametrů, třeba když typ funkce je parametr, a určit, kdy řazené kolekce členů je zpracováván jako jeden parametr a nikoli jako dva parametry.

Můžete také udělit abstraktní metody výchozí definice přidáním definice pro třídu a pomocí `default` – klíčové slovo, jak je znázorněno v syntaxi bloku v tomto tématu. Abstraktní metodu, která má definice ve stejné třídě je ekvivalentní virtuální metodu v jiných jazycích rozhraní .NET Framework. Tom, jestli existuje definice, `abstract` – klíčové slovo vytvoří nový odesílání slot v tabulce virtuální funkce pro třídu.

Bez ohledu na to, jestli základní třída implementuje její abstraktní metody odvozené třídy můžete poskytovat implementace metod abstraktní. Chcete-li implementovat abstraktní metodu v odvozené třídě, definujte metodu, která má stejný název a podpis v odvozené třídě, s výjimkou použití `override` nebo `default` – klíčové slovo a zadejte text metoda. Klíčová slova `override` a `default` přesně mají stejný význam. Použít `override` Pokud nová metoda přepsání základní třída implementace; použijte `default` při vytváření implementaci ve třídě stejné jako původní abstraktní deklaraci. Nepoužívejte `abstract` – klíčové slovo na metodu, která implementuje metodu, která byla definována jako abstraktní základní třídy.

Následující příklad ilustruje abstraktní metodu `Rotate` má výchozí implementace ekvivalentní virtuální metody rozhraní .NET Framework.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

Následující příklad ilustruje odvozené třídy, který přepíše metodu základní třídy. V takovém případě přepsání změní chování tak, aby metoda neprovede žádnou akci.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a>Přetížené metody
Přetížené metody jsou metody, které mají stejné názvy v daného typu, ale které mají různé argumenty. V jazyce F # jsou volitelné argumenty obvykle používají místo přetížené metody. Přetížené metody však nejsou povolené v jazyce, za předpokladu, že argumenty, které jsou v podobě řazené kolekce členů, není curryfikované formuláře.

## <a name="optional-arguments"></a>Nepovinné argumenty

Od verze 4.1 F #, může také mít volitelné argumenty s výchozí hodnotou parametru v metodách.  Toto je proces zefektivnit vzájemná spolupráce pomocí kódu jazyka C#.  Následující příklad ukazuje syntaxi:

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    __.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

Všimněte si, že hodnota předaná pro `DefaultParameterValue` vstupní typ se musí shodovat.  V ukázce výše je `int`.  Probíhá pokus o předání-celé číslo hodnoty do `DefaultParameterValue` by způsobilo chyby kompilace.

## <a name="example-properties-and-methods"></a>Příklad: Vlastnosti a metody
Následující příklad obsahuje typ, který se příklady pole, privátní funkce, vlastnosti a statickou metodu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a>Viz také
[Členy](index.md)
