---
ms.openlocfilehash: 5844dbc2c3c89baeb39b69f16846f92ac10e97f1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804414"
---
### <a name="xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a>Ověření schématu XSD nyní správně detekuje porušení jedinečných omezení, pokud jsou použity složené klíče a jeden klíč je prázdný

|   |   |
|---|---|
|Podrobnosti|Verze rozhraní .NET Framework před verzí 4.6 měly chybu, která způsobovala, že ověření XSD nezjistilo jedinečná omezení složených klíčů, pokud byl jeden z klíčů prázdný. V rozhraní .NET Framework 4.6 je tento problém opraven. Výsledkem bude správnější ověření, ale může to také vést k tomu, že některé položky XML nebudou ověřovat, které dříve budou mít.|
|Návrh|Pokud je potřeba volnější ověření rozhraní .NET Framework 4.0, ověřovací aplikace může cílit na verzi 4.5 (nebo starší) rozhraní .NET Framework. Při retargeting rozhraní .NET Framework 4.6, ale revize kódu by mělo být provedeno, aby se ujistil, že duplicitní složené klíče (jak je popsáno v popisu tohoto problému) se neočekává, že k ověření.|
|Rozsah|Edge|
|Version|4.6|
|Typ|Změna cílení|
