---
title: Metody
description: Zjistěte, jak F# je metoda přidružená k typu, který slouží k vystavení a implementaci funkcí a chování objektů a typů.
ms.date: 11/04/2019
ms.openlocfilehash: 6f5ae76ea450b07763eb58d0c95b18b30f634551
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976649"
---
# <a name="methods"></a>Metody

*Metoda* je funkce, která je přidružena k typu. V objektově orientovaném programování metody slouží k vystavení a implementaci funkcí a chování objektů a typů.

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

V předchozí syntaxi vidíte různé formy deklarací a definic metod. V delších textech metod zalomení řádku následuje znaménko rovná se (=) a tělo celé metody se odsadí.

Atributy lze použít pro jakoukoliv deklaraci metody. Předcházejí syntaxi pro definici metody a jsou obvykle uvedeny na samostatném řádku. Další informace najdete v tématu [atributy](../attributes.md).

Metody mohou být označeny `inline`. Informace o `inline`naleznete v tématu [inline Functions](../functions/inline-functions.md).

Nevložené metody lze v rámci typu rekurzivně použít. nemusíte explicitně používat klíčové slovo `rec`.

## <a name="instance-methods"></a>Metody instance

Metody instance jsou deklarovány s klíčovým slovem `member` a *držitelem s identifikátorem*, za kterým následuje tečka (.) a název metody a parametry. Stejně jako v případě vazeb `let` může být *seznam parametrů* vzorem. Obvykle jsou parametry metody uzavřeny v závorkách v podobě řazené kolekce členů, což je způsob, jakým F# se tyto metody zobrazují v případě, že jsou vytvořeny v jiných .NET Frameworkch jazycích. Nicméně formulář curryfikované (parametry oddělené mezerami) je také společný a další vzory jsou podporovány také.

Následující příklad ukazuje definici a použití neabstraktní metody instance.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

V rámci metod instance nepoužívejte vlastní identifikátor pro přístup k polím definovaným pomocí vazeb let. Použijte samotný identifikátor při přístupu k ostatním členům a vlastnostem.

## <a name="static-methods"></a>Statické metody

Klíčové slovo `static` slouží k určení, že metodu lze volat bez instance a není přidružena k instanci objektu. V opačném případě metody jsou metody instance.

Příklad v další části zobrazuje pole deklarovaná s klíčovým slovem `let`, členy vlastnosti deklarované s klíčovým slovem `member` a statickou metodou deklarovanou klíčovým slovem `static`.

Následující příklad ukazuje definici a použití statických metod. Předpokládají, že tyto definice metod jsou v předchozí části v třídě `SomeType`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a>Abstraktní a virtuální metody

Klíčové slovo `abstract` označuje, že metoda má virtuální slot pro expedici a nemusí mít definici ve třídě. *Virtuální slot pro expedici* je položka ve interně udržované tabulce funkcí, která se používá v době běhu k vyhledání volání virtuální funkce v objektově orientovaném typu. Mechanizmus pro virtuální expedici je mechanismus, který implementuje *polymorfismus*, což je důležitá funkce pro objektově orientované programování. Třída, která má alespoň jednu abstraktní metodu bez definice, je *abstraktní třída*, což znamená, že nelze vytvořit žádné instance této třídy. Další informace o abstraktních třídách naleznete v tématu [abstraktní třídy](../abstract-classes.md).

Deklarace abstraktní metody neobsahují tělo metody. Místo toho je název metody následován dvojtečkou (:) a podpis typu pro metodu. Podpis typu metody je stejný jako typ, který je zobrazen technologií IntelliSense při pozastavení ukazatele myši nad názvem metody v editoru Visual Studio Code, s výjimkou názvů parametrů. Signatury typů se zobrazí také překladačem FSI. exe, když pracujete interaktivně. Podpis typu metody je tvořen výpisem typů parametrů následovaných návratovým typem s příslušnými symboly oddělovače. Parametry curryfikované jsou oddělené `->` a parametry řazené kolekce členů jsou oddělené `*`. Vrácená hodnota je vždy oddělená od argumentů symbolem `->`. Kulaté závorky lze použít k seskupení složitých parametrů, například, když je typ funkce parametr nebo chcete-li určit, kdy se řazená kolekce členů považuje za jeden parametr, nikoli jako dva parametry.

Můžete také poskytnout abstraktní metody jako výchozí definice přidáním definice ke třídě a použitím klíčového slova `default`, jak je znázorněno v bloku syntaxe v tomto tématu. Abstraktní metoda, která má definici ve stejné třídě, je ekvivalentní virtuální metodě v jiných .NET Framework jazycích. Bez ohledu na to, zda definice existuje, klíčové slovo `abstract` vytvoří novou patici pro expedici v tabulce virtuálních funkcí pro danou třídu.

Bez ohledu na to, zda základní třída implementuje své abstraktní metody, mohou odvozené třídy poskytnout implementace abstraktních metod. Chcete-li implementovat abstraktní metodu v odvozené třídě, definujte metodu, která má stejný název a signaturu v odvozené třídě, s výjimkou použití klíčového slova `override` nebo `default` a zadejte tělo metody. Klíčová slova `override` a `default` znamenají naprosto stejnou věc. Použijte `override`, pokud nová metoda přepisuje implementaci základní třídy; Použijte `default` při vytváření implementace ve stejné třídě jako původní abstraktní deklarace. Nepoužívejte klíčové slovo `abstract` pro metodu, která implementuje metodu, která byla deklarována jako abstraktní v základní třídě.

Následující příklad ukazuje abstraktní metodu `Rotate`, která má výchozí implementaci, ekvivalent .NET Framework virtuální metody.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

Následující příklad znázorňuje odvozenou třídu, která přepisuje metodu základní třídy. V tomto případě přepsání změní chování tak, aby metoda nedělá nic.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a>Přetížené metody

Přetížené metody jsou metody, které mají stejné názvy v daném typu, ale mají různé argumenty. V F#se obvykle používají volitelné argumenty namísto přetížených metod. V jazyce jsou však povoleny přetížené metody za předpokladu, že argumenty jsou v podobě řazené kolekce členů, nikoli curryfikované Form.

## <a name="optional-arguments"></a>Nepovinné argumenty

Počínaje F# 4,1 můžete mít v metodách také volitelné argumenty s výchozí hodnotou parametru.  To usnadňuje práci s C# kódem.  Následující příklad ukazuje syntaxi:

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    _.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

Všimněte si, že hodnota předaná pro `DefaultParameterValue` musí odpovídat vstupnímu typu.  Ve výše uvedeném příkladu se jedná o `int`.  Při pokusu o předání hodnoty, která není celočíselná, do `DefaultParameterValue` dojde k chybě kompilace.

## <a name="example-properties-and-methods"></a>Příklad: vlastnosti a metody

Následující příklad obsahuje typ obsahující příklady polí, privátních funkcí, vlastností a statické metody.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a>Viz také:

- [Členové](index.md)
