---
title: Typy F#
description: 'Další informace o typy, které se používají v F # a jak jsou s názvem a popsané typů F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 42521ed75a76753af81d3bbb9693ec5af29536ad
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="f-types"></a>Typy F#

Toto téma popisuje typy, které se používají v F # a jak jsou s názvem a popsané typů F #.


## <a name="summary-of-f-types"></a>Souhrn typů F #
Některé typy jsou považovány za *primitivní typy*, jako je například typ Boolean `bool` a typy bodů plovoucí a integrální různých velikostí, které zahrnují typy znaků a bajtů. Tyto typy jsou popsané v [primitivní typy](primitive-types.md).

Jiné typy, které jsou integrované do jazyka zahrnují řazené kolekce členů, seznamy, pole, pořadí, záznamy a rozlišované sjednocení. Pokud máte zkušenosti s jinými jazyky rozhraní .NET a jsou učení F #, přečtěte si témata pro každou z těchto typů. Odkazy na další informace o těchto typech jsou součástí [Příbuzná témata](https://msdn.microsoft.com/library/#rel) části tohoto tématu. Tyto F # – konkrétní typy podporují styly programování, které jsou společné pro funkční programovací jazyky. Mnoho z těchto typů mít přidružené moduly v knihovně F #, které podporují běžných operací pro tyto typy.

Typ funkce obsahuje informace o typy parametrů a návratovým typem.

Rozhraní .NET Framework je zdrojem typy objektů, rozhraní typy, typy delegáta a ostatní. Můžete definovat vlastní typy objektů, stejně jako v kterémkoli jazyce platformy .NET.

F # – kód můžete navíc definovat aliasy, které jsou s názvem *typ – zkratky*, které jsou pro typy alternativní názvy. Zkratky typů může použít, když typ může v budoucnu změnit a vy chcete vyhnout změně kód, který závisí na typu. Nebo můžete použít jako popisný název pro typ, který může usnadnit kódu ke čtení a pochopení zkratka typu.

F # obsahuje typy užitečné kolekce, které jsou navrženy s funkčního programování v paměti. Pomocí těchto typů kolekce umožňuje psát kód, který je v styl více funkční. Další informace najdete v tématu [typy kolekcí F #](fsharp-collection-types.md).


## <a name="syntax-for-types"></a>Syntaxe pro typy
V F # – kód budete muset často zapsat názvy typů. Každý typ má syntaktické formuláře a použijte tyto syntaktické formulářů v typu poznámky, abstraktní metodu deklarací, delegát deklarace, podpisy a jiných objektů. Vždy, když je deklarovat nové konstrukce program v překladač, vytiskne překladač název konstruktu a syntaxe pro jeho typu. Tuto syntaxi může být právě identifikátor pro uživatelem definovaný typ nebo integrované identifikátor takové jako u `int` nebo `string`, ale pro složitější typy syntaxe je složitější.

V následující tabulce jsou uvedeny aspektů typ syntaxe typů F #.



|Typ|Typ syntaxe|Příklady|
|----|-----------|--------|
|primitivní typ|*Název typu*|`int`<br /><br />`float`<br /><br />`string`|
|Agregační typ (třídy, struktury, sjednocení, záznam, výčtu a tak dále)|*Název typu*|`System.DateTime`<br /><br />`Color`|
|– Zkratka typu|*Název – zkratka typu*|`bigint`|
|plně kvalifikovaný typ|*Název namespaces.Type*<br /><br />or<br /><br />*Název Modules.Type*<br /><br />or<br /><br />*Název namespaces.Modules.Type*|`System.IO.StreamWriter`|
|pole|*Název typu*[] nebo<br /><br />*Název typu* pole|`int[]`<br /><br />`array<int>`<br /><br />`int array`|
|Dvourozměrná pole|*Název typu*[,]|`int[,]`<br /><br />`float[,]`|
|trojrozměrné pole|*Název typu*[,]|`float[,,]`|
|řazené kolekce členů|*Typ name1* &#42; *typ name2* ...|Například `(1,'b',3)` má typ `int * char * int`|
|Obecný typ|*parametr typu* *název obecného typu*<br /><br />or<br /><br />*název obecného typu*&lt;*seznam parametrů typu*&gt;|`'a list`<br /><br />`list<'a>`<br /><br />`Dictionary<'key, 'value>`|
|vytvořený typ (obecného typu, který má zadaný argument konkrétního typu)|*argument typu* *název obecného typu*<br /><br />or<br /><br />*název obecného typu*&lt;*seznam typu argumentů*&gt;|`int option`<br /><br />`string list`<br /><br />`int ref`<br /><br />`option<int>`<br /><br />`list<string>`<br /><br />`ref<int>`<br /><br />`Dictionary<int, string>`|
|typ funkce, který má jeden parametr|*Parametr type1*  - &gt; *návratový typ*|Funkce, která přebírá `int` a vrátí `string` má typ `int -> string`|
|typ funkce, která má několik parametrů|*Parametr type1*  - &gt; *parametr type2*  - &gt; ... -&gt; *návratový typ*|Funkce, která přebírá `int` a `float` a vrátí `string` má typ `int -> float -> string`|
|vyšší pořadí funkce jako parametr|(*typ funkce*)|`List.map` má typ `('a -> 'b) -> 'a list -> 'b list`|
|delegát|Delegovat z *typ funkce*|`delegate of unit -> int`|
|flexibilní typu|#*Název typu*|`#System.Windows.Forms.Control`<br /><br />`#seq<int>`|

## <a name="related-topics"></a>Související témata


|Téma|Popis|
|-----|-----------|
|[Primitivní typy](primitive-types.md)|Popisuje předdefinované jednoduché typy, jako je například integrální typy, typem logická hodnota a typů znaků.|
|[Typ jednotky](unit-type.md)|Popisuje `unit` typu, typ, který má jednu hodnotu a je indikován (); ekvivalent `void` v jazyce C# a `Nothing` v jazyce Visual Basic.|
|[Řazené kolekce členů](tuples.md)|Popisuje typ řazené kolekce členů, typ, který se skládá z přidružené hodnoty libovolného typu seskupené do párů, triples, quadruples a tak dále.|
|[Možnosti](options.md)|Popisuje typ možnosti, typ, který může mít hodnotu nebo být prázdný.|
|[Seznamy](lists.md)|Popisuje seznamy, které jsou seřazené, neměnné řadu elementy všechny stejného typu.|
|[Pole](arrays.md)|Popisuje pole, které jsou seřazené sady měnitelný elementů stejného typu, které zabírají blok souvislé paměti a mají pevnou velikost.|
|[Sekvence](sequences.md)|Popisuje pořadí typu, který představuje řadu logických hodnot. jednotlivé hodnoty se vypočítávají pouze v případě potřeby.|
|[Záznamy](records.md)|Popisuje typ záznamu, malé agregace s názvem hodnot.|
|[Rozlišovaná sjednocení](discriminated-unions.md)|Popisuje rozlišovaná sjednocení typu, typ, jejichž hodnoty může být jakýkoli sadu možné typy.|
|[Funkce](functions/index.md)|Popisuje funkce hodnot.|
|[Třídy](classes.md)|Popisuje typ třída typ objektu, který odpovídá typu odkazu rozhraní .NET. Typy tříd může obsahovat členy, vlastnosti, implementovaných a základního typu.|
|[Struktury](structures.md)|Popisuje `struct` typu, typ objektu, který odpovídá typu .NET hodnoty. `struct` Typ obvykle reprezentuje malé agregaci dat.|
|[Rozhraní](interfaces.md)|Popisuje typy rozhraní, které jsou typy, které představují sadu členů, které poskytují určité funkce, ale které neobsahují žádná data. Typ rozhraní musí implementovat typ objektu, který bude funkční.|
|[Delegáti](delegates.md)|Popisuje typ delegáta, který reprezentuje funkce jako objekt.|
|[Výčty](enumerations.md)|Popisuje výčtové typy, jejichž hodnoty patří do skupiny s názvem hodnot.|
|[Atributy](attributes.md)|Popisuje atributy, které se používají k určení metadata pro jiného typu.|
|[Typy výjimek](exception-handling/exception-types.md)|Popisuje výjimky, které určují informace o chybě.|
