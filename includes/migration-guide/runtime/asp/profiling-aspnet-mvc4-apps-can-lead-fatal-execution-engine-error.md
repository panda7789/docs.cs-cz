---
ms.openlocfilehash: 439a4976482639cd2e4e17315ec1a53ca54aa477
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61648997"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a>Profilace aplikací ASP.Net MVC4 může vést k závažné chybě

|   |   |
|---|---|
|Podrobnosti|Profilovací programy pomocí sestavení NGEN/Profile dojít k chybě profilovaných aplikací technologie ASP.NET MVC4 při spuštění s "závažnou spuštění modulu výjimku.|
|Doporučení|Tento problém je vyřešen v rozhraní .NET Framework 4.5.2. Alternativně může profiler vyhnout tomuto problému zadáním <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> v jeho masky události.|
|Rozsah|Edge|
|Version|4.5|
|Type|Modul runtime|
