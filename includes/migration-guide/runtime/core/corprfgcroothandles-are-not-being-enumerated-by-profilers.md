---
ms.openlocfilehash: 8433899058c6f569e380999800557dbe8ed0a169
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858419"
---
### <a name="cor_prf_gc_root_handles-are-not-being-enumerated-by-profilers"></a>COR_PRF_GC_ROOT_HANDLEs nejsou vyjmenovány profilovacími programy

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework v4.5.1 <code>RootReferences2()</code> profilování rozhraní API <code>COR_PRF_GC_ROOT_HANDLE</code> je nesprávně <code>COR_PRF_GC_ROOT_OTHER</code> vrací (jsou vráceny jako místo). Tento problém je vyřešen počínaje rozhraním .NET Framework 4.6.|
|Návrh|Tento problém byl vyřešen v rozhraní .NET Framework 4.6 a může být vyřešen upgradem na tuto verzi rozhraní .NET Framework.|
|Rozsah|Vedlejší|
|Version|4.5.1|
|Typ|Modul runtime|
