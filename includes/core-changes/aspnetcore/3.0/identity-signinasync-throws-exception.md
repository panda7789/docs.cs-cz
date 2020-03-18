---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394352"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a>Identita: SignInAsync vyvolá výjimku pro neověřenou identitu

Ve výchozím `SignInAsync` nastavení vyvolá výjimku pro objekty `IsAuthenticated` `false`zabezpečení / identity, ve kterém je .

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

`SignInAsync`přijímá všechny objekty / identity, včetně `IsAuthenticated` `false`identit, ve kterých je .

#### <a name="new-behavior"></a>Nové chování

Ve výchozím `SignInAsync` nastavení vyvolá výjimku pro objekty `IsAuthenticated` `false`zabezpečení / identity, ve kterém je . Je nový příznak potlačit toto chování, ale výchozí chování se změnilo.

#### <a name="reason-for-change"></a>Důvod změny

Staré chování bylo problematické, protože ve výchozím nastavení `[Authorize]`  /  `RequireAuthenticatedUser()`byly tyto objekty odmítnuty .

#### <a name="recommended-action"></a>Doporučená akce

V ASP.NET Core 3.0 Preview 6 `RequireAuthenticatedSignIn` je `AuthenticationOptions` ve `true` výchozím nastavení příznak. Nastavte tento `false` příznak obnovit staré chování.

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádný

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
