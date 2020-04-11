---
title: Vestavěné číselné převody – odkaz jazyka C#
ms.date: 10/22/2019
helpviewer_keywords:
- implicit numeric conversions [C#]
- explicit numeric conversion [C#]
- numeric conversions [C#], implicit
- numeric conversions [C#], explicit
- conversions [C#], implicit numeric
- conversions [C#], explicit numeric
ms.openlocfilehash: b7d53e508e4d585c746a3cc61824cdace7707deb
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121454"
---
# <a name="built-in-numeric-conversions-c-reference"></a>Předdefinované číselné převody (odkaz C#)

C# poskytuje sadu [integrální](integral-numeric-types.md) a [plovoucí desetinnou desetinnou desetinnou](floating-point-numeric-types.md) desetinnou hodnotu číselné typy. Existuje převod mezi libovolnými dvěma číselnými typy, implicitními nebo explicitními. K explicitnímu převodu je nutné použít [výraz přetypování.](../operators/type-testing-and-cast.md#cast-expression)

## <a name="implicit-numeric-conversions"></a>Implicitní číselné převody

V následující tabulce jsou uvedeny předdefinované implicitní převody mezi předdefinovanými číselnými typy:

|From|Akce|
|----------|--------|
|[Sbyte](integral-numeric-types.md)|`short`, `int` `long`, `float` `double`, , , nebo`decimal`|
|[Bajt](integral-numeric-types.md)|`short`, `ushort` `int`, `uint` `long`, `ulong` `float`, `double`, , , , nebo`decimal`|
|[short](integral-numeric-types.md)|`int`, `long` `float`, `double`, , nebo`decimal`|
|[ushort](integral-numeric-types.md)|`int`, `uint` `long`, `ulong` `float`, `double`, , , nebo`decimal`|
|[int](integral-numeric-types.md)|`long`, `float` `double`, , nebo`decimal`|
|[uint](integral-numeric-types.md)|`long`, `ulong` `float`, `double`, , nebo`decimal`|
|[long](integral-numeric-types.md)|`float`, `double`, nebo`decimal`|
|[ulong](integral-numeric-types.md)|`float`, `double`, nebo`decimal`|
|[float](floating-point-numeric-types.md)|`double`|

> [!NOTE]
> Implicitní převody `int` `uint`z `long`, `ulong` `float` , `long` nebo `ulong` `double` do a nebo do může způsobit ztrátu přesnosti, ale nikdy ztrátu řádově. Ostatní implicitní číselné převody nikdy neztratí žádné informace.

Všimněte si také, že

- Všechny [integrální číselné typy](integral-numeric-types.md) jsou implicitně převodně na libovolný [číselný typ s plovoucí desetinnou desetinnou desetinnou hodnotou](floating-point-numeric-types.md).

- Neexistují žádné implicitní převody na `byte` typy a. `sbyte` Neexistují žádné implicitní převody z `double` `decimal` a typy.

- Neexistují žádné implicitní převody mezi `float` `double` typem `decimal` a typem nebo.

- Hodnota konstantního výrazu `int` typu (například hodnota reprezentovaná literálem celého `sbyte`čísla) může být implicitně převedena na , `byte`, `short` `ushort`, `uint`, nebo `ulong`, pokud je v rozsahu cílového typu:

  ```csharp
  byte a = 13;
  byte b = 300;  // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

  Jak ukazuje předchozí příklad, pokud konstantní hodnota není v rozsahu cílového typu, dojde k chybě kompilátoru [CS0031.](../../misc/cs0031.md)

## <a name="explicit-numeric-conversions"></a>Explicitní číselné převody

V následující tabulce jsou uvedeny předdefinované explicitní převody mezi předdefinovanými číselnými typy, pro které neexistuje žádný [implicitní převod](#implicit-numeric-conversions):

|From|Akce|
|----------|--------|
|[Sbyte](integral-numeric-types.md)|`byte`, `ushort` `uint`, , nebo`ulong`|
|[Bajt](integral-numeric-types.md)|`sbyte`|
|[short](integral-numeric-types.md)|`sbyte`, `byte` `ushort`, `uint`, , nebo`ulong`|
|[ushort](integral-numeric-types.md)|`sbyte`, `byte`, nebo`short`|
|[int](integral-numeric-types.md)|`sbyte`, `byte` `short`, `ushort` `uint`, , , nebo`ulong`|
|[uint](integral-numeric-types.md)|`sbyte`, `byte` `short`, `ushort`, , nebo`int`|
|[long](integral-numeric-types.md)|`sbyte`, `byte` `short`, `ushort` `int`, `uint`, , , nebo`ulong`|
|[ulong](integral-numeric-types.md)|`sbyte`, `byte` `short`, `ushort` `int`, `uint`, , , nebo`long`|
|[float](floating-point-numeric-types.md)|`sbyte`, `byte` `short`, `ushort` `int`, `uint` `long`, `ulong`, , , , nebo`decimal`|
|[double](floating-point-numeric-types.md)|`sbyte`, `byte` `short`, `ushort` `int`, `uint` `long`, `ulong` `float`, , , , , nebo`decimal`|
|[decimal](floating-point-numeric-types.md)|`sbyte`, `byte` `short`, `ushort` `int`, `uint` `long`, `ulong` `float`, , , , , nebo`double`|

> [!NOTE]
> Explicitní číselný převod může mít za následek ztrátu <xref:System.OverflowException>dat nebo vyvolat výjimku, obvykle .

Všimněte si také, že

- Při převodu hodnoty integrálního typu na jiný integrální typ, výsledek závisí na [kontextu kontroly](../keywords/checked-and-unchecked.md)přetečení . V kontrolovaném kontextu je převod úspěšný, pokud je zdrojová hodnota v rozsahu cílového typu. V opačném <xref:System.OverflowException> případě je vyvolána. V nekontrolovaném kontextu převod vždy uspěje a pokračuje následujícím způsobem:

  - Pokud je typ zdroje větší než cílový typ, je zdrojová hodnota zkrácena zahozením jeho "extra" nejvýznamnějších bitů. Výsledek je pak považován za hodnotu cílového typu.

  - Pokud je typ zdroje menší než cílový typ, je zdrojová hodnota buď znaménko rozšířené nebo nulové rozšířené tak, aby mělo stejnou velikost jako cílový typ. Rozšíření podpisu se používá, pokud je typ zdroje podepsán; nula-rozšíření se používá, pokud typ zdroje není podepsán. Výsledek je pak považován za hodnotu cílového typu.

  - Pokud má typ zdroje stejnou velikost jako cílový typ, bude hodnota zdroje považována za hodnotu cílového typu.

- Když převedete hodnotu `decimal` na integrální typ, tato hodnota se zaokrouhlí na nulu na nejbližší integrální hodnotu. Pokud výsledná integrální hodnota je mimo <xref:System.OverflowException> rozsah cílového typu, je vyvolána.

- Při převodu `double` `float` hodnoty nebo na integrální typ je tato hodnota zaokrouhlena na nulu na nejbližší integrální hodnotu. Pokud je výsledná integrální hodnota mimo rozsah cílového typu, výsledek závisí na [kontextu kontroly](../keywords/checked-and-unchecked.md)přetečení . V kontrolovaném kontextu <xref:System.OverflowException> je vyvolána, zatímco v nekontrolovaném kontextu je výsledkem nespecifikovaná hodnota cílového typu.

- Při `double` převodu `float`na `double` , hodnota je zaokrouhlena na nejbližší `float` hodnotu. Pokud `double` je hodnota příliš malá nebo příliš `float` velká, aby se vešla do typu, výsledek je nula nebo nekonečno.

- Při `float` převodu `double` `decimal`nebo na , je `decimal` hodnota zdroje převedena na reprezentaci a v případě potřeby zaokrouhlena na nejbližší číslo za 28 desetinným místem. V závislosti na hodnotě zdrojové hodnoty může dojít k jednomu z následujících výsledků:

  - Pokud je hodnota zdroje příliš malá `decimal`na to, aby byla reprezentována jako , výsledek se změní na nulu.

  - Pokud je zdrojová hodnota NaN (nikoli číslo), nekonečno `decimal`nebo <xref:System.OverflowException> příliš velké, aby bylo možné být reprezentovánjako , je vyvolána.

- `decimal` Při převodu `float` `double`na nebo , je hodnota zdroje `float` `double` zaokrouhlena na nejbližší nebo hodnotu.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v následujících částech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):

- [Implicitní číselné převody](~/_csharplang/spec/conversions.md#implicit-numeric-conversions)
- [Explicitní číselné převody](~/_csharplang/spec/conversions.md#explicit-numeric-conversions)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Převody přetypování a typu](../../programming-guide/types/casting-and-type-conversions.md)
