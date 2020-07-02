---
ms.openlocfilehash: d606fbc4048421bc572cfe3db2e06bbcd4529e25
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620005"
---
### <a name="sql_variant-data-uses-sql_variant-collation-rather-than-database-collation"></a>Sql_variant dat používá místo řazení databáze sql_variant kolaci.

#### <a name="details"></a>Podrobnosti

<code>sql_variant</code>data používají <code>sql_variant</code> řazení místo řazení databáze.

#### <a name="suggestion"></a>Návrh

Tato změna řeší možné poškození dat, pokud se řazení databáze liší od <code>sql_variant</code> řazení. Aplikace využívající poškozená data mohou selhat.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Průhlednost|
|Verze|4.5|
|Typ|Modul runtime|
