---
title: C#Typy a proměnné – prohlídka C# jazyka
description: Informace o definování typů a deklaraci proměnných vC#
ms.date: 08/10/2016
ms.assetid: f8a8051e-0049-43f1-b594-9c84cc7b1224
ms.openlocfilehash: 28ba01f7d3f9c71e99945a5d5e813d95389b3b79
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737630"
---
# <a name="types-and-variables"></a>Typy a proměnné

Existují dva druhy typů v C#: *typy hodnot* a *typy odkazů*. Proměnné typů hodnot přímo obsahují svá data, zatímco proměnné typu odkazu ukládají odkazy na jejich data, přičemž ta se označují jako objekty. U typů odkazů je možné, aby dvě proměnné odkazovaly na stejný objekt a bylo tak možné, aby operace s jednou proměnnou ovlivnily objekt, na který je odkazováno z jiné proměnné. S typy hodnot mají proměnné, které mají svou vlastní kopii dat, a není možné, aby operace s jedním z nich ovlivnily jiný (kromě případu, kdy `ref` a `out` proměnné parametru).

C#typy hodnot jsou dále rozděleny na *jednoduché typy*, *výčtové typy*, *typy struktury*a *typy s možnou hodnotou null*. C#odkazové typy jsou dále rozděleny do *typů tříd*, *typů rozhraní*, *typů polí*a *typů delegátů*.

Následující text uvádí přehled C#systému typů.

- [Typy hodnot][ValueTypes]
  - [Jednoduché typy][SimpleTypes]
    - Signed integrální: `sbyte`, `short`, `int``long`
    - Unsigned integrál: `byte`, `ushort`, `uint``ulong`
    - Znaky Unicode: `char`
    - Binární typ s plovoucí desetinnou čárkou IEEE: `float``double`
    - Desetinná čárka s vysokou přesností: `decimal`
    - Logická hodnota: `bool`
  - [Výčtové typy][EnumTypes]
    - Uživatelem definované typy formuláře `enum E {...}`
  - [Typy struktury][StructTypes]
    - Uživatelem definované typy formuláře `struct S {...}`
  - [Typy hodnot s možnou hodnotou null][NullableTypes]
    - Rozšíření všech ostatních typů hodnot s hodnotou `null`
- [Typy odkazů][ReferenceTypes]
  - [Typy tříd][ClassTypes]
    - Nejvyšší základní třída všech ostatních typů: `object`
    - Řetězce Unicode: `string`
    - Uživatelem definované typy formuláře `class C {...}`
  - [Typy rozhraní][InterfaceTypes]
    - Uživatelem definované typy formuláře `interface I {...}`
  - [Typy polí][ArrayTypes]
    - Jednoduché a multidimenzionální, například `int[]` a `int[,]`
  - [Typy delegátů][DelegateTypes]
    - Uživatelem definované typy formuláře `delegate int D(...)`

[ValueTypes]: ../language-reference/builtin-types/value-types.md
[SimpleTypes]: ../language-reference/builtin-types/value-types.md#built-in-value-types
[EnumTypes]: ../language-reference/builtin-types/enum.md
[StructTypes]: ../language-reference/keywords/struct.md
[NullableTypes]: ../language-reference/builtin-types/nullable-value-types.md
[ReferenceTypes]: ../language-reference/keywords/reference-types.md
[ClassTypes]: ../language-reference/keywords/class.md
[InterfaceTypes]: ../language-reference/keywords/interface.md
[DelegateTypes]: ../language-reference/keywords/delegate.md
[ArrayTypes]: ../programming-guide/arrays/index.md

Další informace o číselných typech naleznete v tématu [celočíselné typy](../language-reference/builtin-types/integral-numeric-types.md) a [tabulky typů s plovoucí desetinnou](../language-reference/builtin-types/floating-point-numeric-types.md)čárkou.

C#typ `bool` slouží k reprezentaci logických hodnot – hodnot, které jsou buď `true` nebo `false`.

Zpracování znaků a řetězců v C# nástroji používá kódování Unicode. Typ `char` představuje jednotku kódu UTF-16 a typ `string` představuje sekvenci kódových jednotek UTF-16.

C#programy používají *deklarace typů* k vytváření nových typů. Deklarace typu Určuje název a členy nového typu. C#Pět kategorií typů je uživatelsky definované: typy tříd, typy struktury, typy rozhraní, výčtové typy a typy delegátů.

Typ `class` definuje datovou strukturu obsahující datové členy (pole) a členy funkce (metody, vlastnosti a další). Typy tříd podporují jednu dědičnost a polymorfismus, mechanismy, které mohou odvozené třídy roztáhnout a specializovat základní třídy.

Typ `struct` je podobný typu třídy v tom, že představuje strukturu s datovými členy a členy funkce. Nicméně na rozdíl od tříd jsou struktury typy hodnot a obvykle nevyžadují přidělení haldy. Typy struktury nepodporují uživatelem zadanou dědičnost a všechny typy struktury implicitně dědí z typu `object`.

Typ `interface` definuje kontrakt jako pojmenovanou sadu členů veřejné funkce. `class` nebo `struct`, které implementují `interface`, musí poskytovat implementace členů funkcí rozhraní. `interface` může dědit z více základních rozhraní a `class` nebo `struct` mohou implementovat více rozhraní.

Typ `delegate` představuje odkazy na metody s konkrétním seznamem parametrů a návratovým typem. Delegáti umožňují zacházet s metodami jako s entitami, které lze přiřadit proměnným a předávat jako parametry. Delegáti jsou analogické jako typy funkcí poskytované funkčními jazyky. Jsou také podobné konceptu ukazatelů na funkce nalezených v některých jiných jazycích, ale na rozdíl od ukazatelů na funkce jsou delegáti objektově orientované a typově bezpečné.

`class`, `struct`, `interface` a `delegate` typy podporují obecné typy, kde mohou být parametrizovany s jinými typy.

Typ `enum` je odlišný typ s pojmenovanými konstantami. Každý typ `enum` má podkladový typ, který musí být jedním z osmi integrálních typů. Sada hodnot typu `enum` je stejná jako sada hodnot základního typu.

C#podporuje jedno a multidimenzionální pole libovolného typu. Na rozdíl od typů uvedených výše nemusí být typy polí deklarovány dříve, než mohou být použity. Místo toho jsou typy polí konstruovány pomocí názvu typu s hranatými závorkami. Například `int[]` je jednorozměrné pole `int`, `int[,]` je dvourozměrné pole `int`a `int[][]` je jednorozměrné pole s jednorozměrném polem `int`y.

Typy hodnot s možnou hodnotou null také nemusí být deklarovány dříve, než mohou být použity. U každého typu hodnot bez hodnoty null `T` existuje odpovídající typ hodnoty s možnou hodnotou null `T?`, která může obsahovat další hodnotu `null`. Například `int?` je typ, který může obsahovat libovolné 32 celé číslo se znaménkem nebo hodnotu `null`.

C#systém typů je sjednocený tak, že hodnota libovolného typu může být považována za `object`. Každý typ C# přímo nebo nepřímo je odvozen z typu `object` třídy a `object` je nejvyšší základní třídou všech typů. Hodnoty typů odkazů se považují za objekty pouhým zobrazením hodnot jako typu `object`. Hodnoty typů hodnot se považují za objekty prováděním operací *zabalení* a *rozbalení*. V následujícím příkladu je `int` hodnota převedena na `object` a zpět na `int`.

[!code-csharp[Boxing](../../../samples/snippets/csharp/tour/types-and-variables/Program.cs#L1-L10)]

Když je hodnota typu hodnoty převedena na typ `object`, je `object` instance, která se označuje také jako "box", přidělena pro uchování hodnoty a hodnota je zkopírována do tohoto pole. Naopak, pokud je odkaz `object` přetypování na typ hodnoty, je provedena kontrolu, že odkazovaná `object` je pole správného typu hodnoty, a pokud je ověření úspěšné, je hodnota v poli zkopírována.

C#Sjednocený typ systému efektivně znamená, že typy hodnot se můžou stát objekty na vyžádání. Z důvodu sjednocení, knihovny pro obecné účely, které používají typ `object` lze použít s oběma typy odkazů i s typy hodnot.

Existuje několik druhů *proměnných* v C#, včetně polí, prvků pole, místních proměnných a parametrů. Proměnné reprezentují umístění úložiště a každá proměnná má typ, který určuje, jaké hodnoty mohou být uloženy v proměnné, jak je znázorněno níže.

- Typ hodnoty, která není null
  - Hodnota, která má přesný typ
- Typ hodnoty s možnou hodnotou null
  - `null` hodnota nebo hodnota daného přesného typu
- objekt
  - Odkaz na `null`, odkaz na objekt libovolného typu odkazu, nebo odkaz na zabalenou hodnotu libovolného typu hodnoty
- Typ třídy
  - Odkaz na `null`, odkaz na instanci tohoto typu třídy nebo odkaz na instanci třídy odvozené z tohoto typu třídy
- Typ rozhraní
  - Odkaz na `null`, odkaz na instanci typu třídy, která implementuje tento typ rozhraní, nebo odkaz na zabalenou hodnotu typu hodnoty, který implementuje tento typ rozhraní
- Typ pole
  - Odkaz na `null`, odkaz na instanci tohoto typu pole nebo odkaz na instanci kompatibilního typu pole
- Typ delegáta
  - Odkaz na `null` nebo odkaz na instanci kompatibilního typu delegáta

> [!div class="step-by-step"]
> [Předchozí](program-structure.md)
> [Další](expressions.md)
