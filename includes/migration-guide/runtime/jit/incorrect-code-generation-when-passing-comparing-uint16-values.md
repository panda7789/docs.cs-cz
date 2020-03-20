---
ms.openlocfilehash: ad624a665dbe8e989ea05acc20213809e515e6ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802485"
---
### <a name="incorrect-code-generation-when-passing-and-comparing-uint16-values"></a>Nesprávné generování kódu při předávání a porovnávání hodnot UInt16

|   |   |
|---|---|
|Podrobnosti|Z důvodu změn zavedených v rozhraní .NET Framework 4.7, v některých případech kód generovaný kompilátorem JIT <code>T:System.UInt16</code> v aplikacích spuštěných v rozhraní .NET Framework 4.7 nesprávně porovnává dvě hodnoty. Další informace naleznete [v tématu Problém #11508: Silent bad codegen při předávání a porovnávání ushort args](https://github.com/dotnet/coreclr/issues/11508) na GitHub.com.|
|Návrh|Pokud narazíte na problémy při porovnávání 16bitových nepodepsaných hodnot v rozhraní .NET Framework 4.7, upgradujte na rozhraní .NET Framework 4.7.1.|
|Rozsah|Edge|
|Version|4.7|
|Typ|Modul runtime|
