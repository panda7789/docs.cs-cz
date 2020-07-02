---
ms.openlocfilehash: 02a15f6b9c02002b60c568b9e1d871af49744092
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622052"
---
### <a name="concurrentqueuelttgttrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a>ConcurrentQueue &lt; T &gt; . Metodě trypeek může vrátit chybnou hodnotu null prostřednictvím parametru out.

#### <a name="details"></a>Podrobnosti

V některých scénářích s více vlákny <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=fullName> může vrátit hodnotu true, ale vyplnit výstupní parametr hodnotou null (namísto správné, prohlížené hodnoty).

#### <a name="suggestion"></a>Návrh

Tento problém je opravený ve .NET Framework 4.5.1. Upgrade na tuto architekturu vyřeší tento problém.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Hlavní|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType></li></ul>|
