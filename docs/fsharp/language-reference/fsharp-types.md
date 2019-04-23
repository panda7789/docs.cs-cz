---
title: Typy F#
description: Další informace o typech, které se používají v F# a jak F# jsou typy s názvem a popsané.
ms.date: 05/16/2016
ms.openlocfilehash: b48376c80b48df210bf7bc699a769d40fec60864
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59193587"
---
# <a name="f-types"></a>Typy F#

Toto téma popisuje typy, které se používají v F# a jak F# jsou typy s názvem a popsané.

## <a name="summary-of-f-types"></a>Souhrn F# typy
Některé typy se považují za *primitivní typy*, jako je například typ Boolean `bool` a typy s plovoucí desetinnou čárkou a integrální bodů různých velikostí, mezi které patří typy bajtů a znaků. Tyto typy jsou popsány v [primitivní typy](primitive-types.md).

Jiné typy, které jsou integrované do jazyka zahrnují řazených kolekcí členů, seznamů, polí, sekvencí, záznamů a rozlišovaná sjednocení. Pokud máte zkušenosti s jinými jazyky rozhraní .NET a budou learning F#, byste si měli přečíst témata pro každý z těchto typů. Odkazy na další informace o těchto typech jsou součástí [související témata](https://msdn.microsoft.com/library/#rel) části tohoto tématu. Tyto F#-konkrétní typy podporují styly programování, které jsou společné pro funkčních programovacích jazyků. Mnohé z těchto typů mít přidružené moduly ve službě F# knihovnu, která podporují běžné operace u těchto typů.

Typ funkce zahrnuje informace o typech parametrů a návratový typ.

Rozhraní .NET Framework je zdrojem typy objektů, rozhraní typy, typy delegátů a dalších. Můžete definovat vlastní typy objektů, stejně jako v kterémkoli jazyce platformy .NET.

Navíc F# kódu můžete definovat aliasy, které jsou pojmenovány *typ – zkratky*, které jsou alternativní názvy typů. Zkratky typů můžete použít, když typ může být v budoucnu změnit a chcete se vyhnout změnou kódu, který závisí na typu. Nebo můžete použít jako popisný název pro typ, který mohou učinit kód čitelnější a pochopit – zkratka typu.

F#poskytuje typy užitečné kolekcí, které jsou navržené tak, funkční programování v paměti. Pomocí těchto typů kolekce umožňuje napsat kód, který je ve stylu více funkcí. Další informace najdete v tématu [ F# typy kolekcí](fsharp-collection-types.md).

## <a name="syntax-for-types"></a>Syntaxe pro typy
V F# kódu, je často nutné vypsat názvy typů. Každý typ má syntaktické formuláře a tyto syntaktické formuláře v anotace typu deklarace abstraktní metody, deklarace delegáta, podpisy a jiných objektů, které používáte. Pokaždé, když deklarujete konstrukci program novou interpreta, překladač vytiskne název konstrukce a syntaxe jeho typu. Tato syntaxe může být pouze identifikátor uživatelem definovaného typu nebo integrované identifikátor takové jako u `int` nebo `string`, ale pro složitější typy, syntaxe je složitější.

V následující tabulce jsou uvedeny aspekty syntaxe typu pro F# typy.

|Type|Syntaxe typu|Příklady|
|----|-----------|--------|
|primitivní typ|*Název typu*|`int`<br /><br />`float`<br /><br />`string`|
|požadovaný typ agregace (třída, struktura, sjednocení, záznamu, výčet a tak dále)|*Název typu*|`System.DateTime`<br /><br />`Color`|
|– Zkratka typu|*type-abbreviation-name*|`bigint`|
|plně kvalifikovaný typ|*namespaces.type-name*<br /><br />or<br /><br />*modules.type-name*<br /><br />or<br /><br />*namespaces.modules.type-name*|`System.IO.StreamWriter`|
|pole|*Název typu*[] nebo<br /><br />*Název typu* pole|`int[]`<br /><br />`array<int>`<br /><br />`int array`|
|dvourozměrné pole|*Název typu*[,]|`int[,]`<br /><br />`float[,]`|
|trojrozměrného pole|*Název typu*[,]|`float[,,]`|
|tuple|*Typ name1* &#42; *typ name2* ...|Například `(1,'b',3)` má typ `int * char * int`|
|Obecný typ|*parametr typu* *název obecného typu*<br /><br />or<br /><br />*Název typu pro obecný*&lt;*seznam parametrů typu*&gt;|`'a list`<br /><br />`list<'a>`<br /><br />`Dictionary<'key, 'value>`|
|konstruovaný typ. (obecný typ, který má konkrétní typ argumentu zadaný)|*argument typu* *název obecného typu*<br /><br />or<br /><br />*Název typu pro obecný*&lt;*seznam argumentů typu*&gt;|`int option`<br /><br />`string list`<br /><br />`int ref`<br /><br />`option<int>`<br /><br />`list<string>`<br /><br />`ref<int>`<br /><br />`Dictionary<int, string>`|
|typ funkce, která má jeden parametr|*Parametr type1*  - &gt; *návratový typ*|Funkce, která přebírá `int` a vrátí `string` má typ `int -> string`|
|typ funkce, která má více parametrů|*Parametr type1*  - &gt; *parametr type2*  - &gt; ... –&gt; *návratový typ*|Funkce, která přebírá `int` a `float` a vrátí `string` má typ `int -> float -> string`|
|vyšší funkcí jako parametr|(*typ funkce*)|`List.map` má typ `('a -> 'b) -> 'a list -> 'b list`|
|delegát|delegování z *typ funkce*|`delegate of unit -> int`|
|flexibilní typu|#*Název typu*|`#System.Windows.Forms.Control`<br /><br />`#seq<int>`|

## <a name="related-topics"></a>Související témata

|Téma|Popis|
|-----|-----------|
|[Primitivní typy](primitive-types.md)|Popisuje předdefinované jednoduché typy, například celočíselných typů, typu Boolean a typů znaků.|
|[Typ jednotky](unit-type.md)|Popisuje `unit` typ, typ, který má jednu hodnotu a je indikován (); ekvivalent `void` v C# a `Nothing` v jazyce Visual Basic.|
|[Řazené kolekce členů](tuples.md)|Popisuje typ řazené kolekce členů, typ, který se skládá z přidružené hodnoty libovolného typu, které jsou seskupené ve dvojicích, trojic, quadruples a tak dále.|
|[Možnosti](options.md)|Popisuje typ možnosti, typ, který může mít hodnotu nebo být prázdný.|
|[Seznamy](lists.md)|Popisuje, seznamy, které jsou seřazené, neměnné řadu prvků všechny stejného typu.|
|[Pole](arrays.md)|Popisuje pole, která jsou seřazené sady proměnlivé prvků stejného typu, které zabírají blok souvislé paměti a mají pevnou velikost.|
|[Sekvence](sequences.md)|Popisuje pořadí typ, který představuje logické řady hodnot. jednotlivé hodnoty se vypočítávají pouze v případě potřeby.|
|[Záznamy](records.md)|Popisuje typ záznamu, malé agregace pojmenovaných hodnot.|
|[Rozlišovaná sjednocení](discriminated-unions.md)|Popisuje diskriminovaného typu sjednocení, typ, jehož hodnoty může nabývat kterékoliv sadu možných typů.|
|[Funkce](functions/index.md)|Popisuje funkce hodnoty.|
|[Třídy](classes.md)|Popisuje typ třídy, typ objektu, který odpovídá typu odkaz na rozhraní .NET. Typy tříd může obsahovat členy, vlastnosti, implementovaná rozhraní a základního typu.|
|[Struktury](structures.md)|Popisuje `struct` typ, typ objektu, který odpovídá typu hodnoty .NET. `struct` Typ obvykle představuje malé agregace data.|
|[Rozhraní](interfaces.md)|Popisuje typy rozhraní, které jsou typy, které představují sadu členů, které poskytují určité funkce, ale která neobsahují žádná data. Typ rozhraní musí být implementované podle typu objektu, aby byla užitečná.|
|[Delegáti](delegates.md)|Popisuje typ delegáta, který reprezentuje funkce jako objekt.|
|[Výčty](enumerations.md)|Popisuje typy výčtu, jehož hodnoty patří do sady pojmenovaných hodnot.|
|[Atributy](attributes.md)|Popisuje atributy, které se používají k určení metadata pro jiného typu.|
|[Typy výjimek](exception-handling/exception-types.md)|Popisuje výjimky, které určují informace o chybě.|
