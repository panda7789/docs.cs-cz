---
ms.openlocfilehash: ad624a665dbe8e989ea05acc20213809e515e6ac
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236582"
---
### <a name="incorrect-code-generation-when-passing-and-comparing-uint16-values"></a>Nesprávné generování kódu při předávání a porovnávání hodnot UInt16

|   |   |
|---|---|
|Podrobnosti|Z důvodu změny zavedené v rozhraní .NET Framework 4.7, v některých případech kód generovaný kompilátorem JIT v aplikacích spuštěných na rozhraní .NET Framework 4.7 nesprávně porovná dva <code>T:System.UInt16</code> hodnoty. Další informace najdete v tématu [11508 # problému: Bezobslužná nesprávná funkce codegen při předávání a porovnávání argumentů ushort](https://github.com/dotnet/coreclr/issues/11508) na webu GitHub.com.|
|Doporučení|Pokud narazíte na problémy při porovnání hodnoty bez znaménka 16 bitů v rozhraní .NET Framework 4.7, upgradujte na rozhraní .NET Framework 4.7.1.|
|Rozsah|Edge|
|Version|4.7|
|Type|Modul runtime|
