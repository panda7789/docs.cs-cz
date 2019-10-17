---
ms.openlocfilehash: 959f3959c28c7d0159be7a213986345e2865b9a2
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394441"
---
### <a name="shared-framework-removed-microsoftaspnetcoreall"></a>Sdílené rozhraní: odebrali jsme Microsoft. AspNetCore. All.

Počínaje ASP.NET Core 3,0 se již nevyrábí `Microsoft.AspNetCore.All` Metapackage a porovnání `Microsoft.AspNetCore.All` sdílené rozhraní. Tento balíček je k dispozici v ASP.NET Core 2,2 a bude nadále získávat aktualizace údržby v ASP.NET Core 2,1.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Aplikace můžou použít `Microsoft.AspNetCore.All` Metapackage k cílení na sdílenou architekturu `Microsoft.AspNetCore.All` v .NET Core.

#### <a name="new-behavior"></a>Nové chování

.NET Core 3,0 neobsahuje sdílené rozhraní `Microsoft.AspNetCore.All`.

#### <a name="reason-for-change"></a>Důvod změny

@No__t-0 Metapackage zahrnoval velký počet externích závislostí.

#### <a name="recommended-action"></a>Doporučená akce

Migrujte projekt tak, aby používal rozhraní `Microsoft.AspNetCore.App`. Komponenty, které byly dříve dostupné v `Microsoft.AspNetCore.All`, jsou stále k dispozici v NuGet. Tyto komponenty se teď nasazují s vaší aplikací, takže se nezahrne do sdíleného rozhraní.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
