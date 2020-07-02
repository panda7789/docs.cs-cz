---
ms.openlocfilehash: 349854b0dec5a585990b9c5e7c0b575df5bf70f3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615731"
---
### <a name="xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a>Ověřování schématu XSD teď správně detekuje porušení jedinečných omezení, pokud se používají složené klíče a jeden klíč je prázdný.

#### <a name="details"></a>Podrobnosti

Verze .NET Framework před 4,6 obsahovaly chybu, která způsobila, že ověření XSD nedetekuje jedinečná omezení u složených klíčů, pokud byl jeden z klíčů prázdný. V .NET Framework 4,6 se tento problém opravuje. Výsledkem bude přesnější ověření, ale může to mít také za následek, že některé XML neověřují, které dříve by měly.

#### <a name="suggestion"></a>Návrh

Pokud je potřeba ověření k dis.NET Framework 4,0, ověření aplikace může cílit na verzi 4,5 (nebo starší) .NET Framework. Při přecílení na .NET Framework 4,6 je však nutné provést revizi kódu, aby bylo zajištěno, že nebudou ověřeny duplicitní složené klíče (jak je popsáno v popisu tohoto problému).

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.6         |
| Typ    | Změna cílení |
