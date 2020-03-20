---
ms.openlocfilehash: 439a4976482639cd2e4e17315ec1a53ca54aa477
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803202"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a>Profilování ASP.Net aplikací MVC4 může vést k závažné chybě spuštění motoru

|   |   |
|---|---|
|Podrobnosti|Profilovací programy používající sestavení NGEN /Profile mohou při spuštění s chybně závažnou výjimkou modulu provádění dojít k chybě ASP.NET aplikacích MVC4.|
|Návrh|Tento problém je vyřešen v rozhraní .NET Framework 4.5.2. Případně profiler může zabránit tomuto problému <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> zadáním v jeho maska události.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|
