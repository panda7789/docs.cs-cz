---
title: Metody
description: Zjistěte, jak F# metoda je funkce spojená s typem, které se používají k vystavení a implementaci funkce a chování objektů a typů.
ms.date: 11/04/2019
ms.openlocfilehash: 6f5ae76ea450b07763eb58d0c95b18b30f634551
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400209"
---
# <a name="methods"></a>Metody

*Metoda* je funkce, která je přidružena k typu. V objektově orientovaném programování se metody používají k vystavení a implementaci funkcí a chování objektů a typů.

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

V předchozí syntaxi můžete zobrazit různé formy deklarací metod a definic. V delších tělech metod následuje zalomení řádku za rovnítkem (=) a celé tělo metody je odsazeno.

Atributy lze použít pro libovolnou deklaraci metody. Předcházejí syntaxi definice metody a jsou obvykle uvedeny na samostatném řádku. Další informace naleznete v [tématu Atributy](../attributes.md).

Metody mohou `inline`být označeny . Informace o `inline`aplikaci naleznete [v tématu Inline Functions](../functions/inline-functions.md).

Non-inline metody lze použít rekurzivně v rámci typu; není nutné explicitně používat `rec` klíčové slovo.

## <a name="instance-methods"></a>Metody instance

Metody instance jsou `member` deklarovány pomocí klíčového slova a *vlastního identifikátoru*, následované tečkou (.) a názvem a parametry metody. Stejně jako `let` v případě vazby, *seznam parametrů* může být vzor. Parametry metody obvykle uzavřete do závorek ve formě n-tice, což je způsob, jakým se metody zobrazují v jazyce F#, když jsou vytvořeny v jiných jazycích rozhraní .NET Framework. Curried formulář (parametry oddělené mezerami) je však také běžné a další vzory jsou podporovány také.

Následující příklad ilustruje definici a použití metody neabstraktní instance.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

V rámci metod instance nepoužívejte vlastní identifikátor pro přístup k polím definovaným pomocí vazby let. Při přístupu k ostatním členům a vlastnostem použijte vlastní identifikátor.

## <a name="static-methods"></a>Statické metody

Klíčové `static` slovo se používá k určení, že metodu lze volat bez instance a není přidružena k instanci objektu. V opačném případě jsou metody instance.

Příklad v další části zobrazuje pole `let` deklarovaná s `member` klíčovým slovem, členy `static` vlastností deklarované pomocí klíčového slova a statickou metodu deklarovanou pomocí klíčového slova.

Následující příklad ilustruje definici a použití statických metod. Předpokládejme, že tyto definice `SomeType` metod jsou ve třídě v předchozí části.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a>Abstraktní a virtuální metody

Klíčové `abstract` slovo označuje, že metoda má virtuální odeslání slot u nemusí mít definici ve třídě. *Virtuální dispečerský slot* je položka v interně udržované tabulce funkcí, která se používá za běhu k vyhlídání volání virtuálních funkcí v objektově orientovaném typu. Virtuální expediční mechanismus je mechanismus, který implementuje *polymorfismus*, důležitý rys objektově orientovaného programování. Třída, která má alespoň jednu abstraktní metodu bez definice, je *abstraktní třída*, což znamená, že z této třídy nelze vytvořit žádné instance. Další informace o abstraktních třídách naleznete v [tématu Abstraktní třídy](../abstract-classes.md).

Deklarace abstraktní metody neobsahují tělo metody. Místo toho název metody následuje dvojtečka (:) a podpis typu pro metodu. Typ podpisu metody je stejný jako uvidíte IntelliSense při pozastavení ukazatele myši nad název metody v Editoru kódu Visual Studio, s výjimkou bez názvů parametrů. Typ podpisy jsou také zobrazeny interpret, fsi.exe, když pracujete interaktivně. Podpis typu metody je tvořen výpisem typů parametrů následovaných návratovým typem s příslušnými oddělovacími symboly. Curried parametry jsou `->` odděleny a řazené kolekce členů parametry jsou odděleny `*`. Vrácená hodnota je vždy oddělena `->` od argumentů symbolem. Závorky lze použít k seskupení složitých parametrů, například když je parametrem typ funkce, nebo k označení, kdy je řazená kolekce členů považována za jeden parametr, nikoli za dva parametry.

Abstraktní metody můžete také poskytnout výchozí definice přidáním definice `default` do třídy a použitím klíčového slova, jak je znázorněno v bloku syntaxe v tomto tématu. Abstraktní metoda, která má definici ve stejné třídě, je ekvivalentní virtuální metodě v jiných jazycích rozhraní .NET Framework. Bez ohledu na to, `abstract` zda definice existuje, klíčové slovo vytvoří nový slot odeslání v tabulce virtuálních funkcí pro třídu.

Bez ohledu na to, zda základní třída implementuje své abstraktní metody, odvozené třídy mohou poskytovat implementace abstraktních metod. Chcete-li implementovat abstraktní metodu v odvozené třídě, definujte metodu, která má `override` `default` stejný název a podpis v odvozené třídě, s výjimkou použití klíčového slova nebo a zadejte tělo metody. Klíčová `override` slova `default` a znamenají přesně totéž. Použijte, `override` pokud nová metoda přepíše implementaci základní třídy; použijte `default` při vytváření implementace ve stejné třídě jako původní abstraktní deklarace. Nepoužívejte `abstract` klíčové slovo na metodu, která implementuje metodu, která byla deklarována abstraktní v základní třídě.

Následující příklad ilustruje abstraktní `Rotate` metodu, která má výchozí implementaci, ekvivalent virtuální metody rozhraní .NET Framework.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

Následující příklad ilustruje odvozenou třídu, která přepíše metodu základní třídy. V tomto případě přepsání změní chování tak, aby metoda neprovede žádnou akci.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a>Přetížené metody

Přetížené metody jsou metody, které mají identické názvy v daném typu, ale které mají různé argumenty. V F# volitelné argumenty se obvykle používají namísto přetížené metody. Přetížené metody jsou však povoleny v jazyce, za předpokladu, že argumenty jsou ve formě n-tice, nikoli curried formě.

## <a name="optional-arguments"></a>Volitelné argumenty

Počínaje F# 4.1, můžete také mít volitelné argumenty s výchozí hodnotou parametru v metodách.  To pomáhá usnadnit spolupráci s kódem Jazyka C#.  Následující příklad ukazuje syntaxi:

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    _.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

Všimněte si, že `DefaultParameterValue` hodnota předaná pro musí odpovídat vstupnímu typu.  Ve výše uvedeném vzorku `int`se jedná o .  Pokus o předání hodnoty necelého `DefaultParameterValue` čísla by mělo za následek chybu kompilace.

## <a name="example-properties-and-methods"></a>Příklad: Vlastnosti a metody

Následující příklad obsahuje typ, který obsahuje příklady polí, soukromých funkcí, vlastností a statické metody.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a>Viz také

- [Členové](index.md)
