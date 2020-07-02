---
ms.openlocfilehash: c20d5fb3d700ba7649e423a79e4598b327c50a00
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622234"
---
### <a name="incorrect-code-generation-when-passing-and-comparing-uint16-values"></a>Nesprávné generování kódu při předávání a porovnávání hodnot UInt16

#### <a name="details"></a>Podrobnosti

Z důvodu změn zavedených v .NET Framework 4,7, v některých případech kód generovaný kompilátorem JIT v aplikacích spuštěných v .NET Framework 4,7 nesprávně porovnává dvě <code>T:System.UInt16</code> hodnoty. Další informace najdete v tématu [problémová #11508: tiché chybné CodeGen při předávání a porovnávání UShort argumentů](https://github.com/dotnet/coreclr/issues/11508) v GitHub.com.

#### <a name="suggestion"></a>Návrh

Pokud narazíte na problémy s porovnáním 16bitových hodnot bez znaménka v .NET Framework 4,7, upgradujte na .NET Framework 4.7.1.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4,7|
|Typ|Modul runtime|
