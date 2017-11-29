---
title: "Primitivní typy (F#)"
description: "Zjistit základní primitivní typy, které se používají v jazyce F #."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2f23d98b-551b-4fd2-9f4f-0fd7254288ed
ms.openlocfilehash: b493cdf7116d94f66940d03b86e584bcecbbb0f1
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/08/2017
---
# <a name="primitive-types"></a>Primitivní typy

Toto téma obsahuje základní primitivní typy, které se používají v jazyce F #. Poskytuje taky odpovídající typy .NET a minimální a maximální hodnoty pro každý typ.

## <a name="summary-of-primitive-types"></a>Souhrn primitivní typy
Následující tabulka shrnuje vlastnosti primitivních typů F #.

|Typ|Typ formátu .NET|Popis|
|----|---------|-----------|
|`bool`|`System.Boolean`|Možné hodnoty jsou `true` a `false`.|
|`byte`|`System.Byte`|Hodnoty od 0 do 255.|
|`sbyte`|`System.SByte`|Hodnoty z -128 127 znaků.|
|`int16`|`System.Int16`|Hodnoty z-32 768 do 32 767.|
|`uint16`|`System.UInt16`|Hodnoty od 0 do 65535.|
|`int`|`System.Int32`|Hodnoty z-2,147,483,648 na 2 147 483 647.|
|`uint32`|`System.UInt32`|Hodnoty od 0 do 4 294 967 295.|
|`int64`|`System.Int64`|Hodnoty z-9,223,372,036,854,775,808 9,223,372,036,854,775,807.|
|`uint64`|`System.UInt64`|Hodnoty od 0 do 18,446,744,073,709,551,615.|
|`nativeint`|`System.IntPtr`|Nativní ukazatel jako znaménkem.|
|`unativeint`|`System.UIntPtr`|Nativní ukazatel jako celé číslo bez znaménka.|
|`char`|`System.Char`|Hodnoty znaků Unicode.|
|`string`|`System.String`|Text v kódu Unicode.|
|`decimal`|`System.Decimal`|Plovoucí bodu datový typ, který obsahuje alespoň 28 platných číslic.|
|`unit`|Není k dispozici|Ukazuje na nepřítomnost skutečnou hodnotu. Typ s jedinou hodnotou formální, které je označené `()`. Hodnotu jednotek `()`, se často používá jako zástupný znak, kde je potřeba hodnotu, ale je k dispozici žádná skutečná hodnota nebo smysl.|
|`void`|`System.Void`|Označuje žádný typ nebo hodnota.|
|`float32, single`|`System.Single`|32-bit plovoucí bod typu.|
|`float, double`|`System.Double`|64bitová verze plovoucí bod typu.|

>[!NOTE]
Výpočty s celými čísly příliš velký pro typ 64bitové celé číslo můžete provádět pomocí [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) typu. `bigint`není považována za primitivní typ; je zkratkou pro `System.Numerics.BigInteger`.

## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F #](index.md)
