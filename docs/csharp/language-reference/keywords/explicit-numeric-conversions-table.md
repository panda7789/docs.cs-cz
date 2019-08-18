---
title: Tabulka explicitních číselných C# převodů – referenční informace
ms.custom: seodec18
ms.date: 09/06/2018
helpviewer_keywords:
- conversions [C#], explicit numeric
- numeric conversions [C#], explicit
- explicit numeric conversion [C#]
- numeric data types [C#]
- types [C#], explicit numeric conversions
- type conversion [C#], explicit numeric
ms.assetid: f3bb9e76-6b92-4df7-bc36-f866c24e1dfd
ms.openlocfilehash: 4dee46d075ea3d45d53ac0f64b539231188cf867
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566328"
---
# <a name="explicit-numeric-conversions-table-c-reference"></a>Tabulka explicitních převodůC# čísel (referenční)

V následující tabulce jsou uvedeny předdefinované explicitní převody mezi číselnými typy .NET, pro které neexistuje žádný [implicitní převod](implicit-numeric-conversions-table.md).

|From|Chcete-li|  
|----------|--------|  
|[sbyte](../builtin-types/integral-numeric-types.md)|`byte`, `ushort` ,`uint`,nebo `ulong``char`|  
|[byte](../builtin-types/integral-numeric-types.md)|`sbyte` Nebo `char`|  
|[short](../builtin-types/integral-numeric-types.md)|`sbyte`, `byte` ,`ushort`, ,nebo`uint` `ulong``char`|  
|[ushort](../builtin-types/integral-numeric-types.md)|`sbyte`, `byte`, `short`nebo`char`|  
|[int](../builtin-types/integral-numeric-types.md)|`sbyte`, `byte` ,`short`, ,`uint`,nebo `ulong` `ushort``char`|  
|[uint](../builtin-types/integral-numeric-types.md)|`sbyte`, `byte` ,`short`, ,nebo`ushort` `int``char`|  
|[long](../builtin-types/integral-numeric-types.md)|`sbyte`, `byte` ,`short`, ,`uint`,, ,`ulong`nebo `ushort` `int``char`|  
|[ulong](../builtin-types/integral-numeric-types.md)|`sbyte`, `byte` ,`short`, ,`uint`,, ,`long`nebo `ushort` `int``char`|  
|[char](char.md)|`sbyte`, `byte`nebo`short`|  
|[float](../builtin-types/floating-point-numeric-types.md)|`sbyte`, `byte` ,`short`, ,`int`, ,`long`,, nebo`char` `ushort` `uint` `ulong``decimal`|  
|[double](../builtin-types/floating-point-numeric-types.md)|`sbyte`, `byte` ,`short`, ,`int`, ,`long`,,, ,`float`nebo `ushort` `uint` `ulong` `char``decimal`|  
|[decimal](../builtin-types/floating-point-numeric-types.md)|`sbyte`, `byte` ,`short`, ,`int`, ,`long`,,, ,`float`nebo `ushort` `uint` `ulong` `char``double`|  
  
## <a name="remarks"></a>Poznámky  
  
- Explicitní číselný převod může způsobit ztrátu přesnosti nebo výsledek vyvolání výjimky, obvykle <xref:System.OverflowException>.  

- Pokud převedete hodnotu integrálního typu na jiný celočíselný typ, výsledek závisí na [kontextu kontroly](checked-and-unchecked.md)přetečení. V kontrolovaném kontextu je převod úspěšný, pokud je zdrojová hodnota v rozsahu cílového typu. V opačném případě je vyvolána výjimka. <xref:System.OverflowException> V nekontrolovaném kontextu je převod vždy úspěšný a pokračuje následujícím způsobem:

  - Pokud je typ zdroje větší než cílový typ, je zdrojová hodnota zkrácena tím, že zahodí "extra" nejvýznamnější bity. Výsledek je pak zpracován jako hodnota cílového typu.

  - Pokud je typ zdroje menší než cílový typ, pak je zdrojová hodnota buď znaménko, nebo nula – rozšířená, aby měla stejnou velikost jako cílový typ. Podpisové rozšíření se používá, pokud je typ zdroje podepsaný; Pokud je zdrojový typ bez znaménka, je použita nulová přípona. Výsledek je pak zpracován jako hodnota cílového typu.

  - Pokud má typ zdroje stejnou velikost jako cílový typ, pak je zdrojová hodnota zpracována jako hodnota cílového typu.
  
- Při převodu `decimal` hodnoty na celočíselný typ je tato hodnota zaokrouhlena směrem k nule na nejbližší celočíselnou hodnotu. Pokud výsledná celočíselná hodnota je mimo rozsah cílového typu, <xref:System.OverflowException> je vyvolána výjimka.  
  
- Při převodu `double` hodnoty nebo `float` na celočíselný typ je tato hodnota zaokrouhlena směrem k nule na nejbližší celočíselnou hodnotu. Pokud výsledná celočíselná hodnota je mimo rozsah cílového typu, výsledek závisí na [kontextu kontroly](checked-and-unchecked.md)přetečení. V kontrolovaném kontextu <xref:System.OverflowException> je vyvolána výjimka, zatímco v nekontrolovaném kontextu je výsledek nespecifikovanou hodnotou cílového typu.  
  
- Při převodu `double` `float` na `float` se`double` hodnota zaokrouhluje na nejbližší hodnotu. Pokud je `double` hodnota příliš malá nebo příliš velká, aby se vešla do cílového typu, bude výsledek nula nebo nekonečno.  
  
- Když `float` převedete `double` nebo `decimal`na, zdrojová hodnota se převede na `decimal` reprezentaci a v případě potřeby se zaokrouhluje na nejbližší číslo za 28 desetinným místem. V závislosti na hodnotě zdrojové hodnoty může dojít k jednomu z následujících výsledků:  

  - Pokud je zdrojová hodnota příliš malá `decimal`, aby byla reprezentována jako, výsledkem bude nula.  

  - Je-li zdrojová hodnota NaN (není číslo), nekonečno nebo příliš velká, aby byla reprezentována `decimal`jako <xref:System.OverflowException> , je vyvolána.  
  
- Při `decimal` převodu `float` na `float` nebo `double`se hodnota zaokrouhluje na nejbližší `double` hodnotu nebo. `decimal`  
  
 Další informace o explicitních převodech naleznete v části [explicitní převody](~/_csharplang/spec/conversions.md#explicit-conversions) [ C# specifikace jazyka](../language-specification/index.md).
  
## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Přetypování a převody typů](../../programming-guide/types/casting-and-type-conversions.md)
- [() – operátor](../operators/type-testing-and-cast.md#cast-operator-)
- [Celočíselné typy](../builtin-types/integral-numeric-types.md)
- [Tabulka typů s plovoucí desetinnou čárkou](../builtin-types/floating-point-numeric-types.md)
- [Tabulka předdefinovaných typů](built-in-types-table.md)
- [Tabulka implicitních převodů čísel](implicit-numeric-conversions-table.md)
