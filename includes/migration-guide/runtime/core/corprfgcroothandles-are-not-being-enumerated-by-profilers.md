---
ms.openlocfilehash: 8dc98b2d9c2c0b5f145ebce48cf8f5e054975c6e
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858419"
---
### <a name="corprfgcroothandles-are-not-being-enumerated-by-profilers"></a>COR_PRF_GC_ROOT_HANDLEs nejsou výčtu podle profilovací programy

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework v4.5.1, rozhraní API profilování <code>RootReferences2()</code> nesprávně nikdy vrací <code>COR_PRF_GC_ROOT_HANDLE</code> (se vrátí jako <code>COR_PRF_GC_ROOT_OTHER</code> místo). Tento problém vyřešen, počínaje .NET Framework 4.6.|
|Doporučení|Tento problém jsme opravili v rozhraní .NET Framework 4.6 a může vyřešit upgradem na verzi rozhraní .NET Framework.|
|Scope|Vedlejší|
|Version|4.5.1|
|type|Modul runtime|

