---
title: Typy C# a proměnné - přehled používání jazyka C#
description: Další informace o definování typů a deklarace proměnné v jazyce C#
ms.date: 08/10/2016
ms.assetid: f8a8051e-0049-43f1-b594-9c84cc7b1224
ms.openlocfilehash: 752ff490ec91919dc54539c3e39f6d0c527d6260
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="types-and-variables"></a>Typy a proměnné

Existují dva druhy typy v jazyku C#: *typů hodnot* a *odkazové typy*. Proměnné typů hodnot obsahovat svá data přímo, zatímco proměnné odkazové typy ukládání odkazů na svá data, k tomu se označuje jako objekty. Pro odkazové typy je možné pro dvě proměnné tak, aby odkazovaly na stejný objekt a proto možná pro operace na jednu proměnnou ovlivnit objekt odkazují jiné proměnné. Typy hodnot proměnných každý mají své vlastní kopie dat, a není možné pro operace na jeden, který bude mít vliv na dalších (s výjimkou u `ref` a `out` proměnné parametrů).

Typy hodnot C# na se dále dělí do *jednoduché typy*, *typy výčtu*, *struktura typy*, a *typy s možnou hodnotou Null hodnot*. Odkazové typy C# na se dále dělí do *třídy typy*, *typy rozhraní*, *pole typů*, a *delegovat typy*.

Následující část obsahuje přehled C# na typ systému.

* Typy hodnot
    - Jednoduché typy
        * Podepsané integrální: `sbyte`, `short`, `int`, `long`
        * Celé číslo bez znaménka: `byte`, `ushort`, `uint`, `ulong`
        * Znaky znakové sady Unicode: `char`
        * IEEE plovoucí desetinnou čárkou: `float`, `double`
        * Decimal vysokou přesnost: `decimal`
        * Logická hodnota: `bool`
    - Typy výčtu
        * Uživatelem definované typy formuláře `enum E {...}`
    - Struktura typy
        * Uživatelem definované typy formuláře `struct S {...}`
    - typy hodnot s povolenou hodnotou Null
        * Rozšíření všechny ostatní typy hodnot s `null` hodnota
* Odkazové typy
    - Typy tříd
        * Ultimate základní třídu všechny ostatní typy: `object`
        * Řetězců v kódu Unicode: `string`
        * Uživatelem definované typy formuláře `class C {...}`
    - Typy rozhraní
        * Uživatelem definované typy formuláře `interface I {...}`
    - Typy polí
        * Jeden a více dimenzí, například `int[]` a `int[,]`
    - Typů delegátů.
        * Uživatelem definované typy formuláře `delegate int D(...)`

Osm integrální typy poskytuje podporu pro hodnoty 8bitové, 16bitové, 32bitové a 64bitové verze v podobě podepsaný držitelem nebo bez znaménka.

Existují dva typy s plovoucí desetinnou čárkou `float` a `double`, jsou reprezentované pomocí 32bitové jednoduchou přesností a 64-bit Dvojitá přesnost IEC 60559 formáty, v uvedeném pořadí.

`decimal` Typ je 128-bit datový typ, který je vhodný pro finanční a peněžní výpočty.

C# na `bool` typ se používá k reprezentování logické hodnoty – hodnoty, které jsou buď `true` nebo `false`.

Řetězec zpracování v jazyce C# a znak používá kódování Unicode. `char` Typ reprezentuje jednotka kódu UTF-16 a `string` typ reprezentuje pořadí jednotek kódu UTF-16.

To shrnuje C# na číselné typy.

* Podepsaný celé číslo
    - `sbyte`: bity 8, rozsahu od -128 127
    - `short`: 16 bitů, rozsahu od-32 768-32 767
    - `int`  : 32 bity v rozsahu od--2,147,483,648 2 147 483 647
    - `long` : 64 bitů, v rozsahu od –9,223,372,036,854,775,808 9,223,372,036,854,775,807
* Celé číslo bez znaménka
    - `byte`   : bity 8, v rozsahu od 0 – 255
    - `ushort` : 16 bitů v rozsahu od 0 – 65 535
    - `uint`   : 32 bity v rozsahu od 0 - 4 294 967 295
    - `ulong`  : 64 bitů, v rozsahu od 0 - 18,446,744,073,709,551,615
* Plovoucí desetinné čárky
    - `float`  : v rozsahu od 1.5 × 10 32 bity<sup>−45</sup> -3,4 × 10<sup>38</sup>, přesností 7 číslic
    - `double` : 64 bitů, v rozsahu od 5.0 × 10<sup>−324</sup> -1.7 × 10<sup>308</sup>, přesností na 15 číslic
* Desetinné číslo
    - `decimal` : 128 bitů, rozsah je alespoň –7.9 × 10<sup>−28</sup> -7.9 × 10<sup>28</sup>, s přesností alespoň 28 číslic
    
Programy C#, používají *typ deklarace* k vytvoření nové typy. Deklarace typu Určuje název a členů nového typu. Pěti kategorií C# na typů jsou uživatelské: typy, typy struktura, rozhraní typy, typy výčtu tříd a delegovat typy.

A `class` typ definuje datová struktura, která obsahuje datové členy (pole) a funkce členy (metody, vlastnosti a dalších). Typy tříd podporují jedna dědičnost a polymorfismus, mechanismy, které odvozené třídy můžete rozšířit a specialize základní třídy.

A `struct` typ je podobný typu třídy v tomto reprezentuje struktura s členy data a funkce členy. Na rozdíl od třídy, ale struktury jsou typy hodnot a obvykle nevyžadují přidělení haldy. Struktura typy nepodporují dědičnosti definované uživatelem, a všechny typy struktura implicitně dědí od typu `object`.

`interface` Typ definuje kontrakt jako pojmenovanou sadu funkce veřejné členy. A `class` nebo `struct` , která implementuje `interface` musí poskytovat implementace členů rozhraní funkce. `interface` Mohou dědit z více základní rozhraní a `class` nebo `struct` může implementovat více rozhraní.

A `delegate` typ reprezentuje odkazy na metody s návratový typ a konkrétní parametr seznamu. Delegáti umožňují považovat za entit, které může být přiřazena k proměnné a předány jako parametry metody. Delegáti jsou obdobou typy funkce poskytované funkčních jazyků. Jsou taky podobné koncept ukazatelů na funkce najít v některých jiných jazycích, ale na rozdíl od ukazatelů na funkce, jsou delegáti objektově orientované a bezpečnost typů.

`class`, `struct`, `interface` a `delegate` typy všechny obecné typy podpory, které lze nastavit parametry s jinými typy.

`enum` Typ je typu distinct s pojmenované konstanty. Každý `enum` typ má základní typ, který musí mít jednu z osm integrální typy. Sada hodnot, které `enum` typ je stejný jako sadu hodnot základního typu.

C# podporuje jeden a více trojrozměrným pole libovolného typu. Na rozdíl od typů uvedených výše typy polí nemají deklarovat, než mohou být použity. Typy polí místo toho se vytvářejí pomocí následujících název typu do složených závorek. Například `int[]` je jednorozměrná pole `int`, `int[,]` je dvourozměrná pole `int`, a `int[][]` je jednorozměrná pole jednorozměrná pole `int`.

Typy s možnou hodnotou Null hodnot také nemají deklarovat, než mohou být použity. Pro jednotlivé typy hodnot neumožňující hodnotu Null `T` neexistuje odpovídající typ s možnou hodnotou Null hodnotu `T?`, která může pojmout hodnotou další `null`. Například `int?` je typu, který může obsahovat všechny 32bitové celé číslo nebo hodnotu `null`.

Systém typů jazyka C# na je jednotná tak, aby hodnota jakéhokoli typu lze zacházet jako `object`. Všechny typy v jazyku C# přímo nebo nepřímo odvozená z `object` typ, třídy a `object` je ultimate základní třída všech typů. Hodnoty odkazové typy jsou považovány za objekty jednoduše tak, že zobrazení hodnoty jako typ `object`. Hodnoty typů hodnot se považují za objekty provedením *zabalení* a *rozbalení operations*. V následujícím příkladu se `int` hodnota je převedena na `object` a zpět znovu do `int`.

[!code-csharp[Boxing](../../../samples/snippets/csharp/tour/types-and-variables/Program.cs#L1-L10)]

Pokud je hodnota typu hodnoty převést na typ `object`, `object` instance, označované taky jako "pole", je přidělená k uložení hodnota a hodnota se zkopíruje do tohoto pole. Na druhé straně, když `object` odkaz je převést na typ hodnoty, je provedena kontrola odkazovaná `object` je pole správný typ hodnoty, a pokud je kontrola proběhne úspěšně, hodnota v poli se zkopíruje.

C# pro systém jednotná typů efektivně znamená, že typů hodnot se může stát objekty "na vyžádání." Z důvodu sjednocení, pro obecné účely knihovny, které používají typ `object` lze použít s typy odkazů a hodnotových typů.

Existuje několik typů z *proměnné* v jazyce C#, včetně polí, elementy pole, místní proměnné a parametry. Proměnné představují umístění úložiště, a každá proměnná má typ, který určuje, jaké hodnoty mohou být uložené v proměnné, jak je uvedeno níže.

* Typ hodnoty hodnotu Null
    - Hodnota přesný typu
* Typ s možnou hodnotou Null hodnoty
    - A `null` hodnotu nebo hodnotu přesný typu
* odkazy objektů
    - A `null` odkazu, odkaz na objekt jakéhokoli typu odkaz nebo odkaz na zabalené hodnoty libovolného typu hodnota
* Typ třídy
    - A `null` odkazu, odkaz na instanci typu třídy nebo odkaz na instanci třídy odvozené od typu – třída
* Typ rozhraní
    - A `null` odkazu, odkaz na instanci typu třídy, který implementuje rozhraní typu nebo odkaz na hodnotu typu, který implementuje rozhraní typu zabalené hodnoty
* Typ pole.
    - A `null` odkazu, odkaz na instanci typu pole nebo odkaz na instanci typu kompatibilní pole
* Typ delegáta
    - A `null` odkaz nebo odkaz na instanci typu kompatibilní delegáta

>[!div class="step-by-step"]
[Předchozí](program-structure.md)
[další](expressions.md)
