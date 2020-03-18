---
title: C# Typy a proměnné - prohlídka jazyka C#
description: 'Informace o definování typů a deklarování proměnných v C #'
ms.date: 02/25/2020
ms.assetid: f8a8051e-0049-43f1-b594-9c84cc7b1224
ms.openlocfilehash: b2a5255a243c12543a1cd59b5724b6c826306e04
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159088"
---
# <a name="types-and-variables"></a>Typy a proměnné

Existují dva typy v C#: *typy hodnot* a *typy odkazů*. Proměnné typů hodnot přímo obsahují jejich data, zatímco proměnné referenčních typů ukládají odkazy na jejich data, která jsou označována jako objekty. S typy odkazů je možné, že dvě proměnné odkazují na stejný objekt a proto mohou operace na jedné proměnné ovlivnit objekt, na který odkazuje druhá proměnná. S typy hodnot mají proměnné, z nichž každá má vlastní kopii dat, a není možné, `ref` `out` aby operace na jednom ovlivnily ostatní (s výjimkou proměnných parametrů).

Typy hodnot jazyka C# jsou dále rozděleny do *jednoduchých typů*, *typů výčtu*, *typů struktur*a typů hodnot *s možnou hodnotou s hodnotou s možnou hodnotou.* C # 's typy odkazů jsou dále rozděleny do *typů tříd*, *typy rozhraní*, typy *polí*a *typy delegátů*.

Následující osnova obsahuje přehled systému typu Jazyka C#.

- [Typy hodnot][ValueTypes]
  - [Jednoduché typy][SimpleTypes]
    - Podepsaný integrál: `sbyte`, `short`, `int`,`long`
    - Nepodepsaný integrál: `byte`, `ushort`, `uint`,`ulong`
    - Znaky Unicode:`char`
    - IEEE binární plovoucí `float`bod: ,`double`
    - Vysoce přesná desetinná čárka s plovoucí čárkou:`decimal`
    - Boolean:`bool`
  - [Výčet typy][EnumTypes]
    - Uživatelem definované typy formuláře`enum E {...}`
  - [Typy struktury][StructTypes]
    - Uživatelem definované typy formuláře`struct S {...}`
  - [Typy hodnot s možnou hodnotou s hodnotou Null][NullableTypes]
    - Rozšíření všech ostatních typů `null` hodnot s hodnotou
- [Referenční typy][ReferenceTypes]
  - [Typy tříd][ClassTypes]
    - Nejvyšší základní třída všech ostatních typů:`object`
    - Řetězce Unicode:`string`
    - Uživatelem definované typy formuláře`class C {...}`
  - [Typy rozhraní][InterfaceTypes]
    - Uživatelem definované typy formuláře`interface I {...}`
  - [Typy polí][ArrayTypes]
    - Například jednorozměrné a vícerozměrné `int[]` a`int[,]`
  - [Typy delegátů][DelegateTypes]
    - Uživatelem definované typy formuláře`delegate int D(...)`

[ValueTypes]: ../language-reference/builtin-types/value-types.md
[SimpleTypes]: ../language-reference/builtin-types/value-types.md#built-in-value-types
[EnumTypes]: ../language-reference/builtin-types/enum.md
[StructTypes]: ../language-reference/builtin-types/struct.md
[NullableTypes]: ../language-reference/builtin-types/nullable-value-types.md
[ReferenceTypes]: ../language-reference/keywords/reference-types.md
[ClassTypes]: ../language-reference/keywords/class.md
[InterfaceTypes]: ../language-reference/keywords/interface.md
[DelegateTypes]: ../language-reference/keywords/delegate.md
[ArrayTypes]: ../programming-guide/arrays/index.md

Další informace o číselných typech naleznete v tématu [Integral types](../language-reference/builtin-types/integral-numeric-types.md) a [Floating-point types table](../language-reference/builtin-types/floating-point-numeric-types.md).

`bool` Typ jazyka C# se používá k reprezentaci `true` logických hodnot – hodnot, které jsou buď nebo `false`.

Zpracování znaků a řetězců v c# používá kódování Unicode. Typ `char` představuje jednotku kódu UTF-16 `string` a typ představuje posloupnost jednotek kódu UTF-16.

C# programy používají *deklarace typu* k vytvoření nových typů. Deklarace typu určuje název a členy nového typu. Pět c# kategorie typů jsou uživatelem definovatelné: typy tříd, typy struktur, typy rozhraní, typy výčtu a typy delegátů.

Typ `class` definuje datovou strukturu, která obsahuje datové členy (pole) a členy funkce (metody, vlastnosti a další). Typy tříd podporují jednu dědičnost a polymorfismus, mechanismy, kterými odvozené třídy mohou rozšířit a specializovat základní třídy.

Typ `struct` je podobný typu třídy v tom, že představuje strukturu s datovými členy a členy funkce. Však na rozdíl od tříd, struktury jsou typy hodnot a obvykle nevyžadují přidělení haldy. Typy struktury nepodporují dědičnost zadanou uživatelem a všechny typy `object`struktury implicitně dědí z typu .

Typ `interface` definuje smlouvu jako pojmenovanou sadu členů veřejné funkce. A `class` `struct` nebo, který `interface` implementuje musí poskytnout implementace členů funkce rozhraní. Může `interface` dědit z více základních `class` rozhraní `struct` a nebo může implementovat více rozhraní.

Typ `delegate` představuje odkazy na metody s určitým seznamem parametrů a návratovým typem. Delegáti umožňují považovat metody za entity, které lze přiřadit proměnným a předat jako parametry. Delegáti jsou analogické typy funkcí poskytované funkční jazyky. Jsou také podobné konceptu ukazatelů funkce, které se nacházejí v některých jiných jazycích. Na rozdíl od ukazatelů funkce jsou delegáti objektově orientovaní a typově bezpeční.

Typy `class` `struct`, `interface`, `delegate` a všechny podporují obecné typy, přičemž mohou být parametrizovány s jinými typy.

Typ `enum` je odlišný typ s pojmenovanými konstantami. Každý `enum` typ má základní typ, který musí být jedním z osmi integrální chod. Sada hodnot `enum` typu je stejná jako sada hodnot základního typu.

C# podporuje jednorozměrná a vícerozměrná pole libovolného typu. Na rozdíl od výše uvedených typů nemusí být typy polí deklarovány před jejich použitím. Místo toho jsou typy polí vytvořeny podle názvu typu se čtvercovými závorkami. `int[]` Například jednorozměrné `int`pole , `int[,]` je dvourozměrné pole `int`a `int[][]` jednorozměrné pole jednorozměrného pole `int`.

Nullable typy hodnot také není třeba deklarovat před jejich použití. Pro každý typ `T`hodnoty, který nelze hodnotit, `T?`nelze uvážit hodnotu `null`, který může obsahovat další hodnotu . Například `int?` je typ, který může obsahovat libovolné 32bitové celé číslo nebo hodnotu `null`.

Systém typů jazyka C# je jednotný tak, že hodnotu `object`libovolného typu lze považovat za . Každý typ v C# přímo nebo `object` nepřímo pochází `object` z typu třídy a je nejvyšší základní třídy všech typů. Hodnoty referenčních typů jsou považovány za objekty `object`jednoduše zobrazením hodnot jako typu . Hodnoty typů hodnot jsou považovány za objekty provedením *operací zabalení* a *rozbalení*. V následujícím příkladu `int` je hodnota `object` převedena na `int`a zpět na .

[!code-csharp[Boxing](../../../samples/snippets/csharp/tour/types-and-variables/Program.cs#L1-L10)]

Pokud je hodnota typu hodnoty převedena `object`na `object` typ , instance, označovaná také jako "box", je přidělena k uložení hodnoty a hodnota je zkopírována do tohoto pole. Naopak, když `object` je odkaz přetypován na typ hodnoty, `object` je provedena kontrola, že odkazovaný je pole správného typu hodnoty a pokud je kontrola úspěšná, hodnota v poli je zkopírována.

Systém jednotného typu jazyka C# efektivně znamená, že typy hodnot se mohou stát objekty "na vyžádání". Z důvodu sjednocení lze s typy odkazů `object` i s typy hodnot použít univerzální knihovny, které používají typ.

Existuje několik druhů *proměnných* v jazyce C#, včetně polí, prvky pole, místní proměnné a parametry. Proměnné představují umístění úložiště a každá proměnná má typ, který určuje, jaké hodnoty mohou být uloženy v proměnné, jak je znázorněno níže.

- Typ hodnoty s hodnotou, která neselžou hodnotu,
  - Hodnota tohoto přesného typu
- Typ hodnoty s možnou hodnotou s hodnotou Null
  - Hodnota `null` nebo hodnota tohoto přesného typu
- objekt
  - Odkaz, `null` odkaz na objekt jakéhokoli typu odkazu nebo odkaz na zabalenou hodnotu libovolného typu hodnoty
- Typ třídy
  - Odkaz, `null` odkaz na instanci tohoto typu třídy nebo odkaz na instanci třídy odvozené z tohoto typu třídy
- Typ rozhraní
  - Odkaz, `null` odkaz na instanci typu třídy, který implementuje tento typ rozhraní, nebo odkaz na zabalenou hodnotu typu hodnoty, která implementuje tento typ rozhraní
- Typ pole
  - Odkaz, `null` odkaz na instanci tohoto typu pole nebo odkaz na instanci kompatibilního typu pole
- Typ delegáta
  - Odkaz `null` nebo odkaz na instanci kompatibilního typu delegáta

> [!div class="step-by-step"]
> [Předchozí](program-structure.md)
> [další](expressions.md)
