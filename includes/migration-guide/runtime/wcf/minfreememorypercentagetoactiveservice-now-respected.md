---
ms.openlocfilehash: f8e5dee9e97956cea78b7c8ec999af1afe9ac66b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620050"
---
### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a>MinFreeMemoryPercentageToActiveService se teď dodržuje.

#### <a name="details"></a>Podrobnosti

Toto nastavení určuje minimální velikost paměti, která musí být k dispozici na serveru, než bude možné aktivovat službu WCF. Je navržena tak, aby nedocházelo k <xref:System.OutOfMemoryException?displayProperty=fullName> výjimkám. V .NET Framework 4,5 Toto nastavení nemá žádný vliv. V .NET Framework 4.5.1 je nastavení pozorováno.

#### <a name="suggestion"></a>Návrh

K výjimce dojde, pokud je volná paměť na webovém serveru menší než procento definované konfiguračním nastavením. Některé služby WCF, které úspěšně začaly a běžely v prostředí omezené paměti, teď můžou selhat.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.5.1|
|Typ|Modul runtime|
