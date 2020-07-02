---
ms.openlocfilehash: 5c949b79eefa68ea6f8d4ad27c716c438e24f170
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619960"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a>Deserializace objektů napříč doménami aplikace může selhat.

#### <a name="details"></a>Podrobnosti

V některých případech, když aplikace používá dvě nebo více domén aplikace s různými základy aplikace, se snaží deserializovat objekty v logickém kontextu volání napříč doménami aplikace vyvolá výjimku.

#### <a name="suggestion"></a>Návrh

Viz [zmírnění rizika: deserializace objektů napříč doménami aplikací](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5.1|
|Typ|Modul runtime|
