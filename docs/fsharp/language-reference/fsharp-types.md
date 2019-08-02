---
title: Typy F#
description: Seznamte se s typy, které se F# používají v F# nástroji a jak jsou typy pojmenovány a popsány.
ms.date: 05/16/2016
ms.openlocfilehash: 826bcb56aad3b50fbfcf8f807bb34e9cdcdecaf7
ms.sourcegitcommit: 8c6426a3d2adff5fbcbe1fed0f28eda718c15351
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2019
ms.locfileid: "68733492"
---
# <a name="f-types"></a>Typy F#

V tomto tématu jsou popsány typy používané F# v a F# způsob pojmenování a popsaných typů.

## <a name="summary-of-f-types"></a>Souhrn F# typů
Některé typy jsou považovány za *primitivní typy*, jako je typ `bool` Boolean a integrální a plovoucí desetinná čárka různých velikostí, které zahrnují typy bajtů a znaků. Tyto typy jsou popsány v [primitivních typech](primitive-types.md).

Mezi další typy, které jsou součástí jazyka, patří řazené kolekce členů, seznamy, pole, sekvence, záznamy a rozlišené sjednocení. Pokud máte zkušenosti s dalšími jazyky .NET a naučíte F#se, měli byste si přečíst témata pro každý z těchto typů. Odkazy na Další informace o těchto typech jsou uvedené v části [související témata](https://msdn.microsoft.com/library/#rel) tohoto tématu. Tyto F#typy specifických typů podporují styly programování, které jsou běžné pro funkční programovací jazyky. Mnohé z těchto typů mají přidružené moduly v F# knihovně, které podporují běžné operace s těmito typy.

Typ funkce obsahuje informace o typech parametrů a návratovém typu.

.NET Framework je zdroj typů objektů, typů rozhraní, typů delegátů a dalších. Můžete definovat vlastní typy objektů stejně jako v jakémkoli jiném jazyce .NET.

F# Kód také může definovat aliasy, které jsou pojmenované *zkratky typu*, které jsou alternativní názvy pro typy. Můžete použít zkratky typů, pokud se typ může v budoucnu změnit a chcete se vyhnout změnám kódu, který závisí na typu. Nebo můžete použít zkratku typu jako popisný název pro typ, který může usnadnit čtení a pochopení kódu.

F#poskytuje užitečné typy kolekcí, které jsou navrženy s ohledem na funkční programování. Použití těchto typů kolekcí vám pomůže napsat kód, který je více funkční ve stylu. Další informace najdete v tématu [ F# typy kolekcí](fsharp-collection-types.md).

## <a name="syntax-for-types"></a>Syntaxe pro typy
V F# kódu je často nutné napsat názvy typů. Každý typ má syntaktický tvar a tyto syntaktické formuláře lze použít v anotacích typu, deklaracích abstraktních metod, deklaracích delegátů, podpisech a dalších konstrukcích. Kdykoli deklarujete novou konstrukci programu v překladači, Interpret vytiskne název konstrukce a syntaxi pro svůj typ. Tato syntaxe může být jenom identifikátorem uživatelsky definovaného typu nebo předdefinovaným identifikátorem, jako je například `int` pro `string`nebo, ale pro složitější typy je syntaxe složitější.

V následující tabulce jsou uvedeny aspekty syntaxe typu pro F# typy.

|type|Syntaxe typu|Příklady|
|----|-----------|--------|
|primitivní typ|*název typu*|`int`<br /><br />`float`<br /><br />`string`|
|agregační typ (třída, struktura, sjednocení, záznam, výčet atd.)|*název typu*|`System.DateTime`<br /><br />`Color`|
|zkratka typu|*type-abbreviation-name*|`bigint`|
|plně kvalifikovaný typ|*namespaces.type-name*<br /><br />or<br /><br />*modules.type-name*<br /><br />or<br /><br />*namespaces.modules.type-name*|`System.IO.StreamWriter`|
|pole|*název typu* [] nebo<br /><br />pole *název typu*|`int[]`<br /><br />`array<int>`<br /><br />`int array`|
|dvojrozměrné pole|*název typu* [,]|`int[,]`<br /><br />`float[,]`|
|trojrozměrné pole|*název typu* [,,]|`float[,,]`|
|tuple|*typ – název1* &#42; *Zadejte-název2* ...|Například `(1,'b',3)` typ je`int * char * int`|
|obecný typ|*typ – parametr* *název obecného typu*<br /><br />or<br /><br />&lt;*typ parametru-Parameter* -Name typu Generic-Type&gt;|`'a list`<br /><br />`list<'a>`<br /><br />`Dictionary<'key, 'value>`|
|konstruovaný typ (obecný typ, který má zadaný argument konkrétního typu)|*argument typu* *název obecného typu*<br /><br />or<br /><br />*typ názvu*&lt;*typu argumentu* -typ – seznam&gt;|`int option`<br /><br />`string list`<br /><br />`int ref`<br /><br />`option<int>`<br /><br />`list<string>`<br /><br />`ref<int>`<br /><br />`Dictionary<int, string>`|
|typ funkce, která má jeden parametr|*parametr-typ1*  - &gt; *návratový typ*|Funkce, která přijímá `int` a `string` vrací typ`int -> string`|
|typ funkce, která má více parametrů|*parametr-typ1*  - parametr- - typ2&gt; ...-návratový-Type&gt; &gt;|Funkce, která přebírá `int` typ `float` a a a a `string` a a a a a.`int -> float -> string`|
|vyšší pořadí funkce jako parametr|(*typ funkce*)|`List.map`má typ`('a -> 'b) -> 'a list -> 'b list`|
|delegát|delegát *typu funkce*|`delegate of unit -> int`|
|flexibilní typ|#*název typu*|`#System.Windows.Forms.Control`<br /><br />`#seq<int>`|

## <a name="related-topics"></a>Související témata

|Téma|Popis|
|-----|-----------|
|[Primitivní typy](primitive-types.md)|Popisuje předdefinované jednoduché typy, jako jsou například celočíselné typy, logický typ a typy znaků.|
|[Typ jednotky](unit-type.md)|Popisuje typ, typ, který má jednu hodnotu a která je označena (); `void` ekvivalentem v C# a `Nothing` v Visual Basic. `unit`|
|[Řazené kolekce členů](tuples.md)|Popisuje typ řazené kolekce členů, typ, který se skládá z přidružených hodnot libovolného typu seskupených ve dvojicích, trojích, čtyřikrát a tak dále.|
|[Možnosti](options.md)|Popisuje typ možnosti, typ, který může mít buď hodnotu, nebo být prázdný.|
|[Seznamy](lists.md)|Popisuje seznamy, které jsou seřazené, neměnné řady prvků stejného typu.|
|[Pole](arrays.md)|Popisuje pole, která jsou seřazené sady proměnlivých prvků stejného typu, které zaujímají souvislý blok paměti a mají pevnou velikost.|
|[Sekvence](sequences.md)|Popisuje typ sekvence, který představuje logickou řadu hodnot; jednotlivé hodnoty jsou vypočítány pouze v případě potřeby.|
|[Záznamy](records.md)|Popisuje typ záznamu, malou agregaci pojmenovaných hodnot.|
|[Rozlišovaná sjednocení](discriminated-unions.md)|Popisuje typ rozlišeného sjednocení, typ, jehož hodnoty mohou být libovolné ze sady možných typů.|
|[Funkce](./functions/index.md)|Popisuje hodnoty funkcí.|
|[Třídy](classes.md)|Popisuje typ třídy, typ objektu, který odpovídá typu odkazu .NET. Typy tříd mohou obsahovat členy, vlastnosti, implementovaná rozhraní a základní typ.|
|[Struktury](structures.md)|`struct` Popisuje typ, typ objektu, který odpovídá typu hodnoty .NET. `struct` Typ obvykle představuje malou agregaci dat.|
|[Rozhraní](interfaces.md)|Popisuje typy rozhraní, které jsou typy reprezentující sadu členů, které poskytují určité funkce, ale neobsahují žádná data. Typ rozhraní musí být implementován typem objektu, aby byl užitečný.|
|[Delegáti](delegates.md)|Popisuje typ delegáta, který představuje funkci jako objekt.|
|[Výčty](enumerations.md)|Popisuje typy výčtů, jejichž hodnoty patří do sady pojmenovaných hodnot.|
|[Atributy](attributes.md)|Popisuje atributy, které se používají k zadání metadat pro jiný typ.|
|[Typy výjimek](./exception-handling/exception-types.md)|Popisuje výjimky, které určují informace o chybě.|
