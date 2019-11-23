---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394352"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a>Identita: SignInAsync vyvolá výjimku pro neověřenou identitu.

Ve výchozím nastavení `SignInAsync` vyvolá výjimku pro objekty zabezpečení/identity, ve kterých `IsAuthenticated` `false`.

#### <a name="version-introduced"></a>Představená verze

3,0

#### <a name="old-behavior"></a>Staré chování

`SignInAsync` přijímá všechny objekty zabezpečení a identity včetně identit, ve kterých `IsAuthenticated` `false`.

#### <a name="new-behavior"></a>Nové chování

Ve výchozím nastavení `SignInAsync` vyvolá výjimku pro objekty zabezpečení/identity, ve kterých `IsAuthenticated` `false`. Pro potlačení tohoto chování je k dispozici nový příznak, ale došlo ke změně výchozího chování.

#### <a name="reason-for-change"></a>Důvod změny

Původní chování bylo problematické, protože ve výchozím nastavení byly tyto objekty zabezpečení odmítnuty `[Authorize]` / `RequireAuthenticatedUser()`.

#### <a name="recommended-action"></a>Doporučená akce

V ASP.NET Core 3,0 Preview 6 je `RequireAuthenticatedSignIn` příznak na `AuthenticationOptions`, který je ve výchozím nastavení `true`. Nastavením tohoto příznaku `false` obnovíte původní chování.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
