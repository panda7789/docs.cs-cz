---
ms.openlocfilehash: 959f3959c28c7d0159be7a213986345e2865b9a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394441"
---
### <a name="shared-framework-removed-microsoftaspnetcoreall"></a>Sdílený rámec: Odebránmicrosoft.AspNetCore.All

Počínaje ASP.NET jádrem 3.0, `Microsoft.AspNetCore.All` metabalíček a odpovídající `Microsoft.AspNetCore.All` sdílené rozhraní jsou již vyrábí. Tento balíček je k dispozici v ASP.NET Core 2.2 a bude i nadále dostávat aktualizace údržby v ASP.NET Core 2.1.

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Aplikace mohou `Microsoft.AspNetCore.All` metabalíček použít `Microsoft.AspNetCore.All` k cílení na sdílený rámec na rozhraní .NET Core.

#### <a name="new-behavior"></a>Nové chování

.NET Core 3.0 neobsahuje `Microsoft.AspNetCore.All` sdílený rámec.

#### <a name="reason-for-change"></a>Důvod změny

Metabalíček `Microsoft.AspNetCore.All` obsahoval velký počet externích závislostí.

#### <a name="recommended-action"></a>Doporučená akce

Migrujte projekt `Microsoft.AspNetCore.App` a použijte rámec. Součásti, které byly `Microsoft.AspNetCore.All` dříve k dispozici v jsou stále k dispozici na NuGet. Tyto součásti se teď nasazují s vaší aplikací, místo aby byly zahrnuty do sdíleného rozhraní.

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádný

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
