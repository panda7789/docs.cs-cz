---
title: C#Typy a proměnné – připravuje C# jazyka
description: Další informace o definování typů a deklarace proměnné vC#
ms.date: 08/10/2016
ms.assetid: f8a8051e-0049-43f1-b594-9c84cc7b1224
ms.openlocfilehash: f06894d986973e4394b0586906d67ef41a9d9152
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661071"
---
# <a name="types-and-variables"></a>Typy a proměnné

Existují dva druhy typů v jazyce C#: *typů hodnot* a *referenční typy*. Proměnné typů hodnoty přímo obsahovat svá data, zatímco proměnné typů odkazu ukládají odkazy na svá data, ten se označuje jako objekty. V případě typů odkazu je možné pro dvě proměnné odkazovat na stejný objekt a proto je možné pro operace v rámci jedné proměnné ovlivňovat objekt odkazovaný jinou proměnnou. S typy hodnot proměnných každý vlastní kopii dat a není možné pro operace se na nich se má vliv na jinou (s výjimkou v případě třídy `ref` a `out` proměnných parametrů).

C#pro typy hodnot se dále dělí do *jednoduché typy*, *typy výčtu*, *typy struktury*, a *typy s možnou hodnotou*. C#pro typy odkazů se dále dělí do *typy tříd*, *typy rozhraní*, *pole typů*, a *typy delegátů*.

Následující text uvádí přehled C#na systém typů.

* [Typy hodnot][ValueTypes]
  - [Jednoduché typy][SimpleTypes]
    * Podepsané celé číslo: `sbyte`, `short`, `int`, `long`
    * Celočíselný typ bez znaménka: `byte`, `ushort`, `uint`, `ulong`
    * Znaky Unicode: `char`
    * S plovoucí desetinnou čárkou IEEE binární: `float`, `double`
    * Desetinné číslo vysokou přesnost s plovoucí desetinnou čárkou: `decimal`
    * Logická hodnota: `bool`
  - [Výčtové typy][EnumTypes]
    * Uživatelem definované typy formuláře `enum E {...}`
  - [Typy struktury][StructTypes]
    * Uživatelem definované typy formuláře `struct S {...}`
  - [Typy s možnou hodnotou Null][NullableTypes]
    * Rozšíření všechny ostatní typy hodnot s `null` hodnota
* [Odkazové typy][ReferenceTypes]
  - [Typy tříd][ClassTypes]
    * Ultimate základní třídy pro všechny ostatní typy: `object`
    * Řetězce Unicode: `string`
    * Uživatelem definované typy formuláře `class C {...}`
  - [Typy rozhraní][InterfaceTypes]
    * Uživatelem definované typy formuláře `interface I {...}`
  - [Typy polí][ArrayTypes]
    * Jeden – a s multidimenzionálním, například `int[]` a `int[,]`
  - [Typy delegátů][DelegateTypes]
    * Uživatelem definované typy formuláře `delegate int D(...)`

[ValueTypes]: ../language-reference/keywords/value-types-table.md
[SimpleTypes]: ../language-reference/keywords/value-types.md#simple-types
[EnumTypes]: ../language-reference/keywords/enum.md
[StructTypes]: ../language-reference/keywords/struct.md
[NullableTypes]: ../programming-guide/nullable-types/index.md
[ReferenceTypes]: ../language-reference/keywords/reference-types.md
[ClassTypes]: ../language-reference/keywords/class.md
[InterfaceTypes]: ../language-reference/keywords/interface.md
[DelegateTypes]: ../language-reference/keywords/delegate.md
[ArrayTypes]: ../programming-guide/arrays/index.md

Další informace o typech čísel najdete v tématu [integrální typy](../language-reference/builtin-types/integral-numeric-types.md) a [Tabulka typů s plovoucí desetinnou čárkou](../language-reference/builtin-types/floating-point-numeric-types.md).

C#společnosti `bool` typ se používá k reprezentaci logické hodnoty – hodnoty, které jsou buď `true` nebo `false`.

Znakové a řetězcové zpracování v jazyce C# používá kódování Unicode. `char` Typ představuje jednotku kódu UTF-16 a `string` typ představuje posloupnost jednotkami kódu kódování UTF-16.

C# programy používají *typ deklarace* pro vytvoření nových typů. Deklarace typu Určuje název a členy nového typu. Pět C#společnosti jsou kategorie typů definovaných uživatelem: Třída typy, typy struktury, rozhraní typy, výčtové typy a typy delegátů.

A `class` typ definuje datová struktura, která obsahuje data (pole) a funkční členy (metody, vlastnosti a ostatní). Typy tříd podporují jednoduché dědičnosti a polymorfismu, mechanismy jeho prostřednictvím odvozené třídy můžete rozšířit a specialize základní třídy.

A `struct` typ je podobný typu třídy, v tom, že představuje strukturu dat a funkční členy. Na rozdíl od tříd však struktury jsou typy hodnot a obvykle nevyžadují přidělení haldy. Typy struktury nepodporují dědičnosti zadané uživatelem, a všechny typy struktury implicitně dědí z typu `object`.

`interface` Typ definuje kontrakt jako pojmenovanou sadu funkce veřejné členy. A `class` nebo `struct` , který implementuje `interface` nezajistil implementace členů rozhraní funkce. `interface` Může dědit z více základních rozhraních a `class` nebo `struct` může implementovat více rozhraní.

A `delegate` typ představuje odkazy na metody se seznamem konkrétních parametrů a návratovým typem. Delegáty umožňují považovat za entity, které může být přiřazena k proměnné a předány jako parametry metod. Delegáti jsou obdobou na typy funkcí poskytovaných funkčních jazyků. Jsou také podobný koncept ukazatelů na funkce v některých jiných jazycích, ale na rozdíl od ukazatelů na funkce, Delegáti jsou objektově orientované a typově bezpečné.

`class`, `struct`, `interface` a `delegate` typy všechny obecné typy podpory, které mohou být parametrizovány s jinými typy.

`enum` Je typ odlišný typ se pojmenovaných konstant. Každý `enum` typ má základní typ, který musí mít jednu z osmi integrální typy. Sada hodnot, které `enum` typ je stejný jako sadu hodnot ze základního typu.

C# podporuje jeden a více trojrozměrným pole libovolného typu. Na rozdíl od výše uvedené typy typy polí nemusí být deklarované před použitím. Místo toho typy pole jsou vytvořeny podle názvu typu do složených závorek. Například `int[]` je jednorozměrné pole `int`, `int[,]` je dvourozměrné pole `int`, a `int[][]` je jednorozměrné pole jednorozměrné pole `int`.

Typy s možnou hodnotou také nemusíte předtím, než je možné deklarovat. Pro jednotlivé typy neumožňující hodnotu `T` neexistuje odpovídající typ s možnou hodnotou Null `T?`, který může obsahovat další hodnotu `null`. Například `int?` je typ, který může pojmout všechny 32bitové celé číslo nebo hodnota `null`.

C#v systému typů je jednotný tak, že lze považovat hodnotu libovolného typu `object`. Všechny typy v jazyce C# přímo nebo nepřímo odvozuje od `object` typ, třídy a `object` je ultimate základní třída všech typů. Hodnoty odkazové typy jsou považovány za objekty jednoduše tak, že zobrazení hodnoty jako typ `object`. Hodnoty typy hodnot jsou považovány za objekty pomocí provádí *zabalení* a *rozbalení operace*. V následujícím příkladu `int` hodnota je převedena na `object` a zpět znovu na `int`.

[!code-csharp[Boxing](../../../samples/snippets/csharp/tour/types-and-variables/Program.cs#L1-L10)]

Pokud je hodnota typu hodnoty převést na typ `object`, `object` instance, také nazývané "pole", je přidělená k uchování hodnoty a zkopírování hodnoty do tohoto pole. Naopak, když `object` odkaz je přetypován na typ hodnoty, která se provede kontrola odkazované `object` je pole typu správné hodnoty a v případě zaškrtnutí bude úspěšné, je hodnota v poli zkopírována.

C#společnosti unified typ systému efektivně znamená, že typy hodnot se může stát objekty "na vyžádání." Z důvodu sjednocení pro obecné účely knihoven, které používají typ `object` jde použít s typy odkazů a typy hodnot.

Existuje několik typů z *proměnné* v jazyce C#, včetně polí, prvky pole, místní proměnné a parametry. Umístění úložiště představují proměnné a každá proměnná má typ, který určuje, jaké hodnoty můžou být uložené v proměnné, jak je znázorněno níže.

* Typ neumožňující hodnotu
  - Hodnota tohoto přesné typu
* Typ s možnou hodnotou Null
  - A `null` hodnotu nebo hodnotu přesně podle tohoto typu
* odkazy objektů
  - A `null` odkazu, odkaz na objekt typu odkazu nebo odkaz zabalené hodnoty libovolného typu hodnoty
* Typ třídy.
  - A `null` odkazu, odkaz na instanci daného typu třídy nebo odkaz na instanci třídy odvozené z typu třídy
* Typ rozhraní
  - A `null` odkazu, odkaz na instanci typu třídy, která implementuje rozhraní typu nebo odkaz na hodnotu zabalený typ hodnoty, která implementuje rozhraní typu
* Typ pole
  - A `null` odkazu, odkaz na instanci daného typu pole nebo odkaz na instanci typu kompatibilní pole
* Typ delegáta
  - A `null` odkaz nebo odkaz na instanci typu kompatibilní delegáta

> [!div class="step-by-step"]
> [Předchozí](program-structure.md)
> [další](expressions.md)
