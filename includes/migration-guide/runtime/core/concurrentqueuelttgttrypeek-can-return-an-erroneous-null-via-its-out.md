---
ms.openlocfilehash: a93fbbd787aa50f080337a6170cf8f56d0d24e31
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664305"
---
### <a name="concurrentqueuettrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a>ConcurrentQueue\<T >. Metodě TryPeek může vrátit chybné null prostřednictvím jeho výstupní parametr

|   |   |
|---|---|
|Podrobnosti|V některých scénářích s více procesy <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=name> může vrátit hodnotu true, ale vyplnit výstupní parametr s hodnotou null (místo hodnoty správné, nahlédnout).|
|Doporučení|Tento problém je vyřešen v rozhraní .NET Framework 4.5.1. Upgrade na tento rámec se vyřešit problém.|
|Rozsah|Hlavní|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType></li></ul>|
