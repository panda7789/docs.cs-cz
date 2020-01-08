---
title: Typy
description: Seznamte se s typy, které se F# používají v F# nástroji a jak jsou typy pojmenovány a popsány.
ms.date: 05/16/2016
ms.openlocfilehash: 70d79525318c8d2eb0711d6a1b50be1ac0cf0226
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348218"
---
# <a name="f-types"></a>Typy F#

V tomto tématu jsou popsány typy používané F# v a F# způsob pojmenování a popsaných typů.

## <a name="summary-of-f-types"></a>Souhrn F# typů

Některé typy jsou považovány za *primitivní typy*, jako například typ Boolean `bool` a integrální a plovoucí desetinná čárka různých velikostí, které zahrnují typy bajtů a znaků. Tyto typy jsou popsány v [primitivních typech](basic-types.md).

Mezi další typy, které jsou součástí jazyka, patří řazené kolekce členů, seznamy, pole, sekvence, záznamy a rozlišené sjednocení. Pokud máte zkušenosti s dalšími jazyky .NET a naučíte F#se, měli byste si přečíst témata pro každý z těchto typů. Odkazy na Další informace o těchto typech jsou uvedené v části [související témata](https://msdn.microsoft.com/library/#rel) tohoto tématu. Tyto F#typy specifických typů podporují styly programování, které jsou běžné pro funkční programovací jazyky. Mnohé z těchto typů mají přidružené moduly v F# knihovně, které podporují běžné operace s těmito typy.

Typ funkce obsahuje informace o typech parametrů a návratovém typu.

.NET Framework je zdroj typů objektů, typů rozhraní, typů delegátů a dalších. Můžete definovat vlastní typy objektů stejně jako v jakémkoli jiném jazyce .NET.

F# Kód také může definovat aliasy, které jsou pojmenované *zkratky typu*, které jsou alternativní názvy pro typy. Můžete použít zkratky typů, pokud se typ může v budoucnu změnit a chcete se vyhnout změnám kódu, který závisí na typu. Nebo můžete použít zkratku typu jako popisný název pro typ, který může usnadnit čtení a pochopení kódu.

F#poskytuje užitečné typy kolekcí, které jsou navrženy s ohledem na funkční programování. Použití těchto typů kolekcí vám pomůže napsat kód, který je více funkční ve stylu. Další informace najdete v tématu [ F# typy kolekcí](fsharp-collection-types.md).

## <a name="syntax-for-types"></a>Syntaxe pro typy

V F# kódu je často nutné napsat názvy typů. Každý typ má syntaktický tvar a tyto syntaktické formuláře lze použít v anotacích typu, deklaracích abstraktních metod, deklaracích delegátů, podpisech a dalších konstrukcích. Kdykoli deklarujete novou konstrukci programu v překladači, Interpret vytiskne název konstrukce a syntaxi pro svůj typ. Tato syntaxe může být jenom identifikátorem uživatelsky definovaného typu nebo předdefinovaným identifikátorem, jako je například pro `int` nebo `string`, ale u složitějších typů je syntaxe složitější.

V následující tabulce jsou uvedeny aspekty syntaxe typu pro F# typy.

|Type|Syntaxe typu|Příklady|
|----|-----------|--------|
|Primitivní typ|*název typu*|`int`<br /><br />`float`<br /><br />`string`|
|agregační typ (třída, struktura, sjednocení, záznam, výčet atd.)|*název typu*|`System.DateTime`<br /><br />`Color`|
|zkratka typu|*type-abbreviation-name*|`bigint`|
|plně kvalifikovaný typ|*namespaces.type-name*<br /><br />nebo<br /><br />*modules.type-name*<br /><br />nebo<br /><br />*namespaces.modules.type-name*|`System.IO.StreamWriter`|
|pole|*název typu*[] nebo<br /><br />pole *název typu*|`int[]`<br /><br />`array<int>`<br /><br />`int array`|
|dvojrozměrné pole|*název typu*[,]|`int[,]`<br /><br />`float[,]`|
|trojrozměrné pole|*název typu*[,,]|`float[,,]`|
|tuple|typ *-název1* &#42; *typ – název2* ...|Například `(1,'b',3)` má typ `int * char * int`|
|obecný typ|*typ parametr-* Type- *název-typu*<br /><br />nebo<br /><br />*Generic-type-name*&lt;*Type-parameter-list*&gt;|`'a list`<br /><br />`list<'a>`<br /><br />`Dictionary<'key, 'value>`|
|konstruovaný typ (obecný typ, který má zadaný argument konkrétního typu)|*typ-argument* *Obecné-typ – název*<br /><br />nebo<br /><br />*Generic-type-name*&lt;*Type-argument-seznam*&gt;|`int option`<br /><br />`string list`<br /><br />`int ref`<br /><br />`option<int>`<br /><br />`list<string>`<br /><br />`ref<int>`<br /><br />`Dictionary<int, string>`|
|typ funkce, která má jeden parametr|*parametr-typ1* -&gt; *návratový typ*|Funkce, která přebírá `int` a vrací `string` typu `int -> string`|
|typ funkce, která má více parametrů|*parametr-typ1* -&gt; *parametr-typ2* -&gt;...-&gt; *návratový typ*|Funkce, která přebírá `int` a `float` a vrací `string` typu `int -> float -> string`|
|vyšší pořadí funkce jako parametr|(*typ funkce*)|`List.map` je typu `('a -> 'b) -> 'a list -> 'b list`|
|delegát|delegát *typu funkce*|`delegate of unit -> int`|
|flexibilní typ|název #ho *typu*|`#System.Windows.Forms.Control`<br /><br />`#seq<int>`|

## <a name="related-topics"></a>Související témata

|Téma|Popis|
|-----|-----------|
|[Primitivní typy](basic-types.md)|Popisuje předdefinované jednoduché typy, jako jsou například celočíselné typy, logický typ a typy znaků.|
|[Typ jednotky](unit-type.md)|Popisuje typ `unit`, typ, který má jednu hodnotu a který je označen hodnotou (); ekvivalent `void` v C# a `Nothing` v Visual Basic.|
|[Řazené kolekce členů](tuples.md)|Popisuje typ řazené kolekce členů, typ, který se skládá z přidružených hodnot libovolného typu seskupených ve dvojicích, trojích, čtyřikrát a tak dále.|
|[Možnosti](options.md)|Popisuje typ možnosti, typ, který může mít buď hodnotu, nebo být prázdný.|
|[Seznamy](lists.md)|Popisuje seznamy, které jsou seřazené, neměnné řady prvků stejného typu.|
|[Pole](arrays.md)|Popisuje pole, která jsou seřazené sady proměnlivých prvků stejného typu, které zaujímají souvislý blok paměti a mají pevnou velikost.|
|[Sekvence](sequences.md)|Popisuje typ sekvence, který představuje logickou řadu hodnot; jednotlivé hodnoty jsou vypočítány pouze v případě potřeby.|
|[Záznamy](records.md)|Popisuje typ záznamu, malou agregaci pojmenovaných hodnot.|
|[Rozlišovaná sjednocení](discriminated-unions.md)|Popisuje typ rozlišeného sjednocení, typ, jehož hodnoty mohou být libovolné ze sady možných typů.|
|[Funkce](./functions/index.md)|Popisuje hodnoty funkcí.|
|[Třídy](classes.md)|Popisuje typ třídy, typ objektu, který odpovídá typu odkazu .NET. Typy tříd mohou obsahovat členy, vlastnosti, implementovaná rozhraní a základní typ.|
|[Struktury](structures.md)|Popisuje typ `struct`, typ objektu, který odpovídá typu hodnoty .NET. Typ `struct` obvykle představuje malou agregaci dat.|
|[Rozhraní](interfaces.md)|Popisuje typy rozhraní, které jsou typy reprezentující sadu členů, které poskytují určité funkce, ale neobsahují žádná data. Typ rozhraní musí být implementován typem objektu, aby byl užitečný.|
|[Delegáti](delegates.md)|Popisuje typ delegáta, který představuje funkci jako objekt.|
|[Výčty](enumerations.md)|Popisuje typy výčtů, jejichž hodnoty patří do sady pojmenovaných hodnot.|
|[Atributy](attributes.md)|Popisuje atributy, které se používají k zadání metadat pro jiný typ.|
|[Typy výjimek](./exception-handling/exception-types.md)|Popisuje výjimky, které určují informace o chybě.|
