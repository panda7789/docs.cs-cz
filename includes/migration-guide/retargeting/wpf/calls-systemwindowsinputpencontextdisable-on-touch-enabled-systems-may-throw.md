---
ms.openlocfilehash: 6bb8c87af66e744514fb43e628c6423487342ac2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "72887754"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a>Volání System.Windows.Input.PenContext.Disable v systémech s podporou dotykového ovládání může vyvolat výjimku ArgumentException

|   |   |
|---|---|
|Podrobnosti|Za určitých okolností volání interní **System.Windows.Intput.PenContext.Disable** metoda v systémech s <code>T:System.ArgumentException</code> podporou dotykového ovládání může vyvolat neošetřené z důvodu reentrancy.|
|Návrh|Tento problém byl vyřešen v rozhraní .NET Framework 4.7. Chcete-li této výjimce zabránit, upgradujte na verzi rozhraní .NET Framework počínaje rozhraním .NET Framework 4.7.|
|Rozsah|Edge|
|Version|4.6.1|
|Typ|Změna cílení|
