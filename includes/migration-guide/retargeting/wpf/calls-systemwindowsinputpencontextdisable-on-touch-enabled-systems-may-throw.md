---
ms.openlocfilehash: 6bb8c87af66e744514fb43e628c6423487342ac2
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72887754"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a>Volání System. Windows. Input. PenContext. disable pro systémy s podporou dotykového ovládání může vyvolat výjimku ArgumentException.

|   |   |
|---|---|
|Podrobnosti|Za určitých okolností můžou volání interní metody **System. Windows. Intput. PenContext. disable** u systémů s podporou dotykového ovládání vyvolat neošetřený <code>T:System.ArgumentException</code> z důvodu Vícenásobný přístup.|
|Doporučení|Tento problém byl vyřešen v .NET Framework 4,7. Chcete-li zabránit výjimce, upgradujte na verzi .NET Framework počínaje .NET Framework 4,7.|
|Rozsah|Edge|
|Version|4.6.1|
|Typ|Změna cílení|
