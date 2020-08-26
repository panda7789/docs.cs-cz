---
title: Typy
description: 'Seznamte se s typy, které se používají v F # a jak jsou typy F # pojmenované a popsány.'
ms.date: 08/15/2020
ms.openlocfilehash: a86d8e8f672d8399b02bb193ae04e1f0d46720b6
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812065"
---
# <a name="f-types"></a>Typy F#

Toto téma popisuje typy, které se používají v F # a jak jsou typy F # pojmenovány a popsány.

## <a name="summary-of-f-types"></a>Souhrn typů F #

Některé typy jsou považovány za *primitivní typy*, jako je typ Boolean `bool` a integrální a plovoucí desetinná čárka různých velikostí, které zahrnují typy bajtů a znaků. Tyto typy jsou popsány v [primitivních typech](basic-types.md).

Mezi další typy, které jsou součástí jazyka, patří řazené kolekce členů, seznamy, pole, sekvence, záznamy a rozlišené sjednocení. Pokud máte zkušenosti s jinými jazyky rozhraní .NET a naučíte F #, měli byste si přečíst témata pro každý z těchto typů. Tyto typy specifické pro jazyk F # podporují styly programování, které jsou společné pro funkční programovací jazyky. Mnohé z těchto typů mají přidružené moduly v knihovně F #, které podporují běžné operace s těmito typy.

Typ funkce obsahuje informace o typech parametrů a návratovém typu.

.NET Framework je zdroj typů objektů, typů rozhraní, typů delegátů a dalších. Můžete definovat vlastní typy objektů stejně jako v jakémkoli jiném jazyce .NET.

Kód jazyka F # může také definovat aliasy, které jsou pojmenované *zkratky typu*, které jsou alternativní názvy pro typy. Můžete použít zkratky typů, pokud se typ může v budoucnu změnit a chcete se vyhnout změnám kódu, který závisí na typu. Nebo můžete použít zkratku typu jako popisný název pro typ, který může usnadnit čtení a pochopení kódu.

Jazyk F # poskytuje užitečné typy kolekcí, které jsou navrženy s ohledem na funkční programování. Použití těchto typů kolekcí vám pomůže napsat kód, který je více funkční ve stylu. Další informace naleznete v tématu [typy kolekcí F #](fsharp-collection-types.md).

## <a name="syntax-for-types"></a>Syntaxe pro typy

V kódu F # často musíte napsat názvy typů. Každý typ má syntaktický tvar a tyto syntaktické formuláře lze použít v anotacích typu, deklaracích abstraktních metod, deklaracích delegátů, podpisech a dalších konstrukcích. Kdykoli deklarujete novou konstrukci programu v překladači, Interpret vytiskne název konstrukce a syntaxi pro svůj typ. Tato syntaxe může být jenom identifikátorem uživatelsky definovaného typu nebo předdefinovaným identifikátorem, jako je například pro `int` nebo `string` , ale pro složitější typy je syntaxe složitější.

V následující tabulce jsou uvedeny aspekty syntaxe typu pro typy F #.

|Typ|Syntaxe typu|Příklady|
|----|-----------|--------|
|primitivní typ|*název typu*|`int`<br /><br />`float`<br /><br />`string`|
|agregační typ (třída, struktura, sjednocení, záznam, výčet atd.)|*název typu*|`System.DateTime`<br /><br />`Color`|
|zkratka typu|*typ – zkratka – název*|`bigint`|
|plně kvalifikovaný typ|*obory názvů. typ – název*<br /><br />nebo<br /><br />*moduly. Type-Name*<br /><br />nebo<br /><br />*obory názvů. Modules. Type-Name*|`System.IO.StreamWriter`|
|array|*název typu*[] nebo<br /><br />pole *název typu*|`int[]`<br /><br />`array<int>`<br /><br />`int array`|
|dvojrozměrné pole|*název typu*[,]|`int[,]`<br /><br />`float[,]`|
|trojrozměrné pole|*název typu*[,,]|`float[,,]`|
|tuple|*typ-název1* &#42; *typ-název2* ...|Například `(1,'b',3)` typ je `int * char * int`|
|obecný typ|*typ parametr-* Type- *název-typu*<br /><br />nebo<br /><br />*název* &lt; obecného typu *typ parametru-seznam*&gt;|`'a list`<br /><br />`list<'a>`<br /><br />`Dictionary<'key, 'value>`|
|konstruovaný typ (obecný typ, který má zadaný argument konkrétního typu)|*typ-argument* *Obecné-typ – název*<br /><br />nebo<br /><br />*název* &lt; obecného typu *typ – argument-seznam*&gt;|`int option`<br /><br />`string list`<br /><br />`int ref`<br /><br />`option<int>`<br /><br />`list<string>`<br /><br />`ref<int>`<br /><br />`Dictionary<int, string>`|
|typ funkce, která má jeden parametr|*parametr-typ1*  - &gt; *návratový typ*|Funkce, která přijímá `int` a vrací `string` typ `int -> string`|
|typ funkce, která má více parametrů|*parametr-typ1*  - &gt; *parametr-typ2*  - &gt; ...- &gt; *návratový-typ*|Funkce, která přebírá `int` typ a `float` a a a a a a a a. `string``int -> float -> string`|
|vyšší pořadí funkce jako parametr|(*typ funkce*)|`List.map` má typ `('a -> 'b) -> 'a list -> 'b list`|
|delegát|delegát *typu funkce*|`delegate of unit -> int`|
|flexibilní typ|#*název typu*|`#System.Windows.Forms.Control`<br /><br />`#seq<int>`|

## <a name="related-topics"></a>Související témata

|Téma|Popis|
|-----|-----------|
|[Primitivní typy](basic-types.md)|Popisuje předdefinované jednoduché typy, jako jsou například celočíselné typy, logický typ a typy znaků.|
|[Typ jednotky](unit-type.md)|Popisuje `unit` typ, typ, který má jednu hodnotu a která je označena (); ekvivalentem `void` v jazyce C# a `Nothing` v Visual Basic.|
|[Řazené kolekce členů](tuples.md)|Popisuje typ řazené kolekce členů, typ, který se skládá z přidružených hodnot libovolného typu seskupených ve dvojicích, trojích, čtyřikrát a tak dále.|
|[Možnosti](options.md)|Popisuje typ možnosti, typ, který může mít buď hodnotu, nebo být prázdný.|
|[Seznamy](lists.md)|Popisuje seznamy, které jsou seřazené, neměnné řady prvků stejného typu.|
|[Pole](arrays.md)|Popisuje pole, která jsou seřazené sady proměnlivých prvků stejného typu, které zaujímají souvislý blok paměti a mají pevnou velikost.|
|[Sekvence](sequences.md)|Popisuje typ sekvence, který představuje logickou řadu hodnot; jednotlivé hodnoty jsou vypočítány pouze v případě potřeby.|
|[Záznamy](records.md)|Popisuje typ záznamu, malou agregaci pojmenovaných hodnot.|
|[Rozlišovaná sjednocení](discriminated-unions.md)|Popisuje typ rozlišeného sjednocení, typ, jehož hodnoty mohou být libovolné ze sady možných typů.|
|[Functions](./functions/index.md)|Popisuje hodnoty funkcí.|
|[Třídy](classes.md)|Popisuje typ třídy, typ objektu, který odpovídá typu odkazu .NET. Typy tříd mohou obsahovat členy, vlastnosti, implementovaná rozhraní a základní typ.|
|[Struktury](structures.md)|Popisuje `struct` typ, typ objektu, který odpovídá typu hodnoty .NET. `struct`Typ obvykle představuje malou agregaci dat.|
|[Rozhraní](interfaces.md)|Popisuje typy rozhraní, které jsou typy reprezentující sadu členů, které poskytují určité funkce, ale neobsahují žádná data. Typ rozhraní musí být implementován typem objektu, aby byl užitečný.|
|[Delegáti](delegates.md)|Popisuje typ delegáta, který představuje funkci jako objekt.|
|[Výčty](enumerations.md)|Popisuje typy výčtů, jejichž hodnoty patří do sady pojmenovaných hodnot.|
|[Atributy](attributes.md)|Popisuje atributy, které se používají k zadání metadat pro jiný typ.|
|[Typy výjimek](./exception-handling/exception-types.md)|Popisuje výjimky, které určují informace o chybě.|
