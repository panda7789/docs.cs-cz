---
ms.openlocfilehash: a16d443a37fb0bb5f6bdc4a39e7dcb4f91c54ead
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393980"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a>Autorizace: implementace IAuthorizationPolicyProvider vyžadují novou metodu.

V ASP.NET Core 3,0 byla do `IAuthorizationPolicyProvider` přidána nová metoda `GetFallbackPolicyAsync`. Tuto záložní zásadu používá middleware autorizace, pokud není zadána žádná zásada.

Další informace najdete v tématu [ASPNET/AspNetCore # 9759](https://github.com/aspnet/AspNetCore/pull/9759). 

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Implementace `IAuthorizationPolicyProvider` nevyžadovaly metodu `GetFallbackPolicyAsync`.

#### <a name="new-behavior"></a>Nové chování

Implementace `IAuthorizationPolicyProvider` vyžadují metodu `GetFallbackPolicyAsync`.

#### <a name="reason-for-change"></a>Důvod změny

Nová metoda byla nutná pro nové `AuthorizationMiddleware` pro použití, pokud nejsou zadány žádné zásady.

#### <a name="recommended-action"></a>Doporučená akce

Přidejte metodu `GetFallbackPolicyAsync` do implementací `IAuthorizationPolicyProvider`.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
