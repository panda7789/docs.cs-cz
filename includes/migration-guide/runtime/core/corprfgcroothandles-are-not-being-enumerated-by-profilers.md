---
ms.openlocfilehash: 4f52535e54607cc824500f9c6a14964a1dec9d32
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619957"
---
### <a name="cor_prf_gc_root_handles-are-not-being-enumerated-by-profilers"></a>COR_PRF_GC_ROOT_HANDLEs nejsou vytvářeny pomocí profilovacích programů

#### <a name="details"></a>Podrobnosti

V .NET Framework v 4.5.1 se rozhraní API profilování <code>RootReferences2()</code> nevrátí správně <code>COR_PRF_GC_ROOT_HANDLE</code> (vrátí se jako <code>COR_PRF_GC_ROOT_OTHER</code> místo). Tento problém je vyřešen od .NET Framework 4,6.

#### <a name="suggestion"></a>Návrh

Tento problém byl opravený v .NET Framework 4,6 a může se řešit upgradem na verzi .NET Framework.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.5.1|
|Typ|Modul runtime|
