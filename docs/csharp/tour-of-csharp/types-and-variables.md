---
title: C#Typy a proměnné – prohlídka C# jazyka
description: Informace o definování typů a deklaraci proměnných vC#
ms.date: 08/10/2016
ms.assetid: f8a8051e-0049-43f1-b594-9c84cc7b1224
ms.openlocfilehash: f06894d986973e4394b0586906d67ef41a9d9152
ms.sourcegitcommit: 46c68557bf6395f0ab9915f7558f2faae0097695
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/12/2019
ms.locfileid: "67661071"
---
# <a name="types-and-variables"></a>Typy a proměnné

Existují dva druhy typů v C#: *typy hodnot* a *typy odkazů*. Proměnné typů hodnot přímo obsahují svá data, zatímco proměnné typu odkazu ukládají odkazy na jejich data, přičemž ta se označují jako objekty. U typů odkazů je možné, aby dvě proměnné odkazovaly na stejný objekt a bylo tak možné, aby operace s jednou proměnnou ovlivnily objekt, na který je odkazováno z jiné proměnné. S typy hodnot mají proměnné, které mají svou vlastní kopii dat, a není možné, aby operace na jednom byly ovlivněny druhou (kromě případu `ref` a `out` proměnných parametrů).

C#typy hodnot jsou dále rozděleny na *jednoduché typy*, *výčtové typy*, *typy struktury*a *typy*s možnou hodnotou null. C#odkazové typy jsou dále rozděleny do *typů tříd*, *typů rozhraní*, *typů polí*a *typů delegátů*.

Následující text uvádí přehled C#systému typů.

* [Typy hodnot][ValueTypes]
  - [Jednoduché typy][SimpleTypes]
    * Podepsané integrály `sbyte`: `short`, `int`,,`long`
    * Unsigned integrál: `byte`, `ushort`, `uint`,`ulong`
    * Znaky Unicode:`char`
    * Binární bod IEEE s plovoucí desetinnou čárkou: `float`,`double`
    * Desetinná čárka s vysokou přesností:`decimal`
    * Datového`bool`
  - [Výčtové typy][EnumTypes]
    * Uživatelem definované typy formuláře`enum E {...}`
  - [Typy struktury][StructTypes]
    * Uživatelem definované typy formuláře`struct S {...}`
  - [Typy hodnot s možnou hodnotou null][NullableTypes]
    * Rozšíření všech ostatních typů hodnot s `null` hodnotou
* [Typy odkazů][ReferenceTypes]
  - [Typy tříd][ClassTypes]
    * Nejvyšší základní třída všech ostatních typů:`object`
    * Řetězce Unicode:`string`
    * Uživatelem definované typy formuláře`class C {...}`
  - [Typy rozhraní][InterfaceTypes]
    * Uživatelem definované typy formuláře`interface I {...}`
  - [Typy polí][ArrayTypes]
    * Jednoduché a multidimenzionální, například `int[]` a`int[,]`
  - [Typy delegátů][DelegateTypes]
    * Uživatelem definované typy formuláře`delegate int D(...)`

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

Další informace o číselných typech naleznete v tématu [celočíselné typy](../language-reference/builtin-types/integral-numeric-types.md) a [tabulky typů s plovoucí desetinnou](../language-reference/builtin-types/floating-point-numeric-types.md)čárkou.

C#typ se používá k reprezentaci logických hodnot – hodnot, které `true` jsou buď nebo `false`. `bool`

Zpracování znaků a řetězců v C# nástroji používá kódování Unicode. Typ představuje jednotku kódu UTF-16 `string` a typ představuje sekvenci jednotek kódu UTF-16. `char`

C#programy používají *deklarace typů* k vytváření nových typů. Deklarace typu Určuje název a členy nového typu. C#Pět kategorií typů je uživatelsky definované: typy tříd, typy struktury, typy rozhraní, výčtové typy a typy delegátů.

`class` Typ definuje datovou strukturu obsahující datové členy (pole) a členy funkce (metody, vlastnosti a další). Typy tříd podporují jednu dědičnost a polymorfismus, mechanismy, které mohou odvozené třídy roztáhnout a specializovat základní třídy.

`struct` Typ je podobný typu třídy v tom, že představuje strukturu s datovými členy a členy funkce. Nicméně na rozdíl od tříd jsou struktury typy hodnot a obvykle nevyžadují přidělení haldy. Typy struktury nepodporují uživatelem zadanou dědičnost a všechny typy struktury implicitně dědí z typu `object`.

`interface` Typ definuje kontrakt jako pojmenovanou sadu členů veřejné funkce. Nebo, který implementuje`interface` , musí poskytnout implementace členů funkce rozhraní. `struct` `class` Může dědit z více základních rozhraní `class` a nebo `struct` může implementovat více rozhraní. `interface`

`delegate` Typ představuje odkazy na metody s konkrétním seznamem parametrů a návratovým typem. Delegáti umožňují zacházet s metodami jako s entitami, které lze přiřadit proměnným a předávat jako parametry. Delegáti jsou analogické jako typy funkcí poskytované funkčními jazyky. Jsou také podobné konceptu ukazatelů na funkce nalezených v některých jiných jazycích, ale na rozdíl od ukazatelů na funkce jsou delegáti objektově orientované a typově bezpečné.

Typy `class` ,`struct` a`delegate`podporují obecné typy, na jejichž základě lze parametry používat s jinými typy. `interface`

`enum` Typ je odlišný typ s pojmenovanými konstantami. Každý `enum` typ má nadřízený typ, který musí být jedním z osmi integrálních typů. Sada hodnot `enum` typu je stejná jako sada hodnot základního typu.

C#podporuje jedno a multidimenzionální pole libovolného typu. Na rozdíl od typů uvedených výše nemusí být typy polí deklarovány dříve, než mohou být použity. Místo toho jsou typy polí konstruovány pomocí názvu typu s hranatými závorkami. `int[]` Například je `int` `int` `int[][]` jednorozměrné pole `int[,]` , je dvourozměrné pole, a je jednorozměrné pole jednorozměrného pole v poli. `int`

Typy hodnot s možnou hodnotou null také nemusí být deklarovány dříve, než mohou být použity. Pro každý typ `T` hodnoty, která není null, existuje odpovídající typ `T?`hodnoty s možnou hodnotou null, který může obsahovat `null`další hodnotu,. Například je typ, který může obsahovat libovolné 32 celé číslo nebo hodnotu `null`. `int?`

C#systém typů je sjednocený tak, že hodnota libovolného typu může být považována `object`za. Každý typ C# přímo nebo nepřímo je odvozen z `object` typu třídy a `object` je nejvyšší základní třídou všech typů. Hodnoty typů odkazů se považují za objekty pouhým zobrazením hodnot jako typu `object`. Hodnoty typů hodnot se považují za objekty prováděním *operací*zabalení a rozbalení. V následujícím příkladu `int` je hodnota převedena na `object` a zpět na `int`.

[!code-csharp[Boxing](../../../samples/snippets/csharp/tour/types-and-variables/Program.cs#L1-L10)]

Když je hodnota typu hodnoty převedena na typ `object` `object` , instance, která se také označuje jako "box", je přidělena pro uchování hodnoty a hodnota je zkopírována do tohoto pole. Naopak, pokud `object` je odkaz přetypování na typ hodnoty, je proveden odkaz `object` na pole správného typu hodnoty, a pokud je ověření úspěšné, je hodnota v poli zkopírována.

C#Sjednocený typ systému efektivně znamená, že typy hodnot se můžou stát objekty na vyžádání. Z důvodu sjednocení, knihovny pro obecné účely, které používají typ `object` , lze použít s oběma typy odkazů i s typy hodnot.

Existuje několik druhů *proměnných* v C#, včetně polí, prvků pole, místních proměnných a parametrů. Proměnné reprezentují umístění úložiště a každá proměnná má typ, který určuje, jaké hodnoty mohou být uloženy v proměnné, jak je znázorněno níže.

* Typ hodnoty, která není null
  - Hodnota, která má přesný typ
* Typ hodnoty s možnou hodnotou null
  - `null` Hodnota nebo hodnota daného přesného typu
* odkazy objektů
  - `null` Odkaz, odkaz na objekt libovolného typu odkazu, nebo odkaz na zabalenou hodnotu libovolného typu hodnoty
* Typ třídy
  - `null` Odkaz, odkaz na instanci tohoto typu třídy nebo odkaz na instanci třídy odvozené z tohoto typu třídy
* Typ rozhraní
  - `null` Odkaz, odkaz na instanci typu třídy, která implementuje tento typ rozhraní, nebo odkaz na zabalenou hodnotu typu hodnoty, který implementuje tento typ rozhraní
* Typ pole
  - `null` Odkaz, odkaz na instanci tohoto typu pole nebo odkaz na instanci kompatibilního typu pole
* Typ delegáta
  - `null` Odkaz nebo odkaz na instanci kompatibilního typu delegáta

> [!div class="step-by-step"]
> [Předchozí](program-structure.md)Další
> [](expressions.md)
