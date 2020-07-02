---
ms.openlocfilehash: 2e13268d4983af5d2fdd6d12b4d9e67d61d07f3d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622029"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a>Profilace aplikací ASP.Net MVC4 může vést k závažné chybě spouštěcího modulu.

#### <a name="details"></a>Podrobnosti

Profilery používající sestavení NGEN/Profile můžou při spuštění selhat ASP.NET MVC4 aplikací s závažnou výjimkou modulu provádění.

#### <a name="suggestion"></a>Návrh

Tento problém je opravený v .NET Framework 4.5.2. Případně se může Profiler vyhnout tomuto problému zadáním <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> v jeho masce události.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime|
