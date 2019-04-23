---
ms.openlocfilehash: 439a4976482639cd2e4e17315ec1a53ca54aa477
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803717"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a>Profilace aplikací ASP.Net MVC4 může vést k závažné chybě

|   |   |
|---|---|
|Podrobnosti|Profilovací programy pomocí sestavení NGEN/Profile dojít k chybě profilovaných aplikací technologie ASP.NET MVC4 při spuštění s "závažnou spuštění modulu výjimku.|
|Doporučení|Tento problém je vyřešen v rozhraní .NET Framework 4.5.2. Alternativně může profiler vyhnout tomuto problému zadáním <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> v jeho masky události.|
|Rozsah|Edge|
|Version|4.5|
|Type|Modul runtime|
