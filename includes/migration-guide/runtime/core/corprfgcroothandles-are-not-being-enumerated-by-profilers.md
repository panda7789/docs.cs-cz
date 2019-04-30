---
ms.openlocfilehash: 8433899058c6f569e380999800557dbe8ed0a169
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649091"
---
### <a name="corprfgcroothandles-are-not-being-enumerated-by-profilers"></a>COR_PRF_GC_ROOT_HANDLEs nejsou výčtu podle profilovací programy

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework v4.5.1, rozhraní API profilování <code>RootReferences2()</code> nesprávně nikdy vrací <code>COR_PRF_GC_ROOT_HANDLE</code> (se vrátí jako <code>COR_PRF_GC_ROOT_OTHER</code> místo). Tento problém vyřešen, počínaje .NET Framework 4.6.|
|Doporučení|Tento problém jsme opravili v rozhraní .NET Framework 4.6 a může vyřešit upgradem na verzi rozhraní .NET Framework.|
|Rozsah|Vedlejší|
|Version|4.5.1|
|Type|Modul runtime|
