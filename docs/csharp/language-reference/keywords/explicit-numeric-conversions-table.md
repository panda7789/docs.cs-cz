---
title: Tabulka explicitních číselných převodů (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], explicit numeric
- numeric conversions [C#], explicit
- explicit numeric conversion [C#]
- numeric data types [C#]
- types [C#], explicit numeric conversions
- type conversion [C#], explicit numeric
ms.assetid: f3bb9e76-6b92-4df7-bc36-f866c24e1dfd
ms.openlocfilehash: 5ca052dea4ee4abc866d2b02055188b0707499d4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43475930"
---
# <a name="explicit-numeric-conversions-table-c-reference"></a>Tabulka explicitních číselných převodů (Referenční dokumentace jazyka C#)
Explicitní číselný převod je použít pro převod libovolného číselného typu na jiný číselný typ, pro který neexistuje žádný implicitní převod, pomocí výrazu přetypování. V následující tabulce jsou uvedeny tyto převody.  
  
 Další informace o převodech viz [přetypování a převody typů](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
|From|Chcete-li|  
|----------|--------|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`byte`, `ushort`, `uint`, `ulong`, nebo `char`|  
|[byte](../../../csharp/language-reference/keywords/byte.md)|`Sbyte` Nebo `char`|  
|[short](../../../csharp/language-reference/keywords/short.md)|`sbyte`, `byte`, `ushort`, `uint`, `ulong`, nebo `char`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`sbyte`, `byte`, `short`, nebo `char`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong`, nebo `char`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, nebo `char`|  
|[long](../../../csharp/language-reference/keywords/long.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `ulong`, nebo `char`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, nebo `char`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`sbyte`, `byte`, nebo `short`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, nebo `decimal`|  
|[double](../../../csharp/language-reference/keywords/double.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, nebo `decimal`|  
|[decimal](../../../csharp/language-reference/keywords/decimal.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, nebo `double`|  
  
## <a name="remarks"></a>Poznámky  
  
-   Explicitní číselný převod může způsobit ztrátu přesnosti nebo výsledek v aktivační výjimky.  
  
-   Při převodu `decimal` hodnota na integrální typ., tato hodnota zaokrouhlena směrem k nule na nejbližší celočíselnou hodnotu. Pokud je výsledný celočíselné hodnoty mimo rozsah cílového typu <xref:System.OverflowException> je vyvolána výjimka.  
  
-   Při převodu z `double` nebo `float` hodnota integrálního typu, hodnota je oříznutá. Je-li výslednou celočíselné hodnoty mimo rozsah hodnoty cílové, výsledek závisí na kontextu kontroly přetečení. Ve zkontrolovaném kontextu `OverflowException` je vyvolána, když v nekontrolovaném kontextu, výsledek je neurčená hodnota cílového typu.  
  
-   Při převodu `double` k `float`, `double` hodnota je zaokrouhlená na nejbližší `float` hodnotu. Pokud `double` hodnota je příliš malá nebo příliš velký a nevejde do cílového typu, výsledkem bude nula nebo nekonečno.  
  
-   Při převodu `float` nebo `double` k `decimal`, zdrojová hodnota je převedena na `decimal` vyjádření a zaokrouhlí na nejbližší číslo po 28 desetinné místo podle potřeby. V závislosti na hodnotě zdrojovou hodnotu může dojít jednu z následujících výsledků:  
  
    -   Pokud zdrojová hodnota je příliš malá, aby se dala vyjádřit jako `decimal`, výsledkem bude nule.  
  
    -   Pokud zdrojová hodnota NaN (není číslo), nekonečno, nebo příliš velký, aby se dala vyjádřit jako `decimal`, `OverflowException` je vyvolána výjimka.  
  
-   Při převodu `decimal` k `float` nebo `double`, `decimal` hodnota je zaokrouhlená na nejbližší `double` nebo `float` hodnotu.  
  
 Další informace o explicitní převod najdete v článku explicitní ve specifikaci jazyka C#. Další informace o tom, jak přistupovat k specifikace najdete v tématu [specifikace jazyka C#](../../../csharp/language-reference/language-specification/index.md).  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Přetypování a převody typů](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
- [() – operátor](../../../csharp/language-reference/operators/invocation-operator.md)  
- [Tabulka celočíselných typů](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [Tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [Tabulka implicitních číselných převodů](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
