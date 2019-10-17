---
ms.openlocfilehash: 56b394c4698f60baeb70d3c17d1abee5d867deb7
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394365"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a>Identita: konstruktor SignInManager akceptuje nový parametr.

Počínaje ASP.NET Core 3,0 byl do konstruktoru `SignInManager` přidán nový parametr `IUserConfirmation<TUser>`. Další informace najdete v tématu [ASPNET/AspNetCore # 8356](https://github.com/aspnet/AspNetCore/issues/8356).

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="reason-for-change"></a>Důvod změny

Motivací pro změnu byla přidání podpory pro nové toky e-mailu a potvrzení identity.

#### <a name="recommended-action"></a>Doporučená akce

Pokud je ručně vytvořen `SignInManager`, Poskytněte implementaci `IUserConfirmation` nebo jeden ze vkládání závislostí k poskytnutí.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
