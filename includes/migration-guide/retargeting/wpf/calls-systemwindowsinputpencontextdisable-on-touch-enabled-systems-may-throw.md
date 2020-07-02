---
ms.openlocfilehash: a44458484ea09c566defeabc9b604bd55d994e93
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617527"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a>Volání System. Windows. Input. PenContext. disable pro systémy s podporou dotykového ovládání může vyvolat výjimku ArgumentException.

#### <a name="details"></a>Podrobnosti

Za určitých okolností může volání interní metody **System. Windows. Intput. PenContext. disable** u systémů s podporou dotykového ovládání vyvolat neošetřený `T:System.ArgumentException` z důvodu Vícenásobný přístup.

#### <a name="suggestion"></a>Návrh

Tento problém byl vyřešen v .NET Framework 4,7. Chcete-li zabránit výjimce, upgradujte na verzi .NET Framework počínaje .NET Framework 4,7.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.6.1       |
| Typ    | Změna cílení |
