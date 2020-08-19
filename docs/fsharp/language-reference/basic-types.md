---
title: Základní typy
description: 'Objevte základní základní typy, které se používají v jazyce F #.'
ms.date: 08/15/2020
ms.openlocfilehash: 659ac8424c62985affcca1741e1b2a74c9c3ee8d
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557695"
---
# <a name="basic-types"></a>Základní typy

Toto téma obsahuje seznam základních typů, které jsou definovány v jazyce F #. Tyto typy jsou nejdůležitější v jazyce F #, který vytváří základ skoro každého programu F #. Jsou nadmnožinou primitivních typů .NET.

|Typ|Typ .NET|Popis|Příklad|
|----|---------|-----------|-------|
|`bool`|<xref:System.Boolean>|Možné hodnoty jsou `true` a `false` .|`true`/`false`|
|`byte`|<xref:System.Byte>|Hodnoty od 0 do 255.|`1uy`|
|`sbyte`|<xref:System.SByte>|Hodnoty od-128 do 127.|`1y`|
|`int16`|<xref:System.Int16>|Hodnoty od-32768 do 32767.|`1s`|
|`uint16`|<xref:System.UInt16>|Hodnoty od 0 do 65535.|`1us`|
|`int`|<xref:System.Int32>|Hodnoty od-2 147 483 648 do 2 147 483 647.|`1`|
|`uint`|<xref:System.UInt32>|Hodnoty od 0 do 4 294 967 295.|`1u`|
|`int64`|<xref:System.Int64>|Hodnoty od-9223372036854775808 do 9 223 372 036 854 775 807.|`1L`|
|`uint64`|<xref:System.UInt64>|Hodnoty od 0 do 18446744073709551615.|`1UL`|
|`nativeint`|<xref:System.IntPtr>|Nativní ukazatel jako celé číslo se znaménkem.|`nativeint 1`|
|`unativeint`|<xref:System.UIntPtr>|Nativní ukazatel jako unsigned integer.|`unativeint 1`|
|`decimal`|<xref:System.Decimal>|Datový typ s plovoucí desetinnou čárkou, který má alespoň 28 platných číslic.|`1.0`|
|`float`, `double`|<xref:System.Double>|64 typ s plovoucí desetinnou čárkou.|`1.0`|
|`float32`, `single`|<xref:System.Single>|32 typ s plovoucí desetinnou čárkou.|`1.0f`|
|`char`|<xref:System.Char>|Hodnoty znaků Unicode.|`'c'`|
|`string`|<xref:System.String>|Text v kódu Unicode.|`"str"`|
|`unit`|nelze použít|Označuje absenci skutečné hodnoty. Typ má pouze jednu formální hodnotu, která je označena `()` . Hodnota jednotky, `()` , se často používá jako zástupný symbol, kde je hodnota potřebná, ale není k dispozici žádná skutečná hodnota, ani smysl.|`()`|

> [!NOTE]
> Můžete provádět výpočty s celými čísly, která jsou příliš velká pro 64 celočíselný typ Integer pomocí typu [bigint](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-bigint.html) . `bigint` není považován za základní typ; Jedná se o zkratku pro `System.Numerics.BigInteger` .

## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka F #](index.md)
