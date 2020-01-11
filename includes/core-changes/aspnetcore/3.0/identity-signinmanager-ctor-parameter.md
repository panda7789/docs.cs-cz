---
ms.openlocfilehash: 6f8e6d2786d20e055c9bef63891db4d6f88bc64b
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75902036"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a>Identita: konstruktor SignInManager akceptuje nový parametr.

Počínaje ASP.NET Core 3,0 byl do konstruktoru `SignInManager` přidán nový parametr `IUserConfirmation<TUser>`. Další informace naleznete v tématu [dotnet/aspnetcore # 8356](https://github.com/dotnet/aspnetcore/issues/8356).

#### <a name="version-introduced"></a>Představená verze

3,0

#### <a name="reason-for-change"></a>Důvod změny

Motivací pro změnu byla přidání podpory pro nové toky e-mailu a potvrzení identity.

#### <a name="recommended-action"></a>Doporučená akce

Pokud je ručně vytvořen `SignInManager`, Poskytněte implementaci `IUserConfirmation` nebo předejte od injektáže závislosti k poskytnutí.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
