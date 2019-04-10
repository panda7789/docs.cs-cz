---
ms.openlocfilehash: 891c29b731214fb0028e960256b79cfc267d86b9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235249"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a>Deserializace objektů mezi doménami appdomains může selhat.

|   |   |
|---|---|
|Podrobnosti|V některých případech kdy aplikace používá dvě nebo více domén aplikace s různými základy cesty aplikace, při pokusu o deserializaci objektů v logického kontextu volání mezi doménami aplikace výjimku.|
|Doporučení|Zobrazit [omezení rizik: Deserializace objektů mezi doménami aplikace](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)|
|Rozsah|Edge|
|Version|4.5.1|
|Type|Modul runtime|
