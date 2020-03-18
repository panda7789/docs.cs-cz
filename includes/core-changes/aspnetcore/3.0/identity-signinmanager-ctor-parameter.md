---
ms.openlocfilehash: 6f8e6d2786d20e055c9bef63891db4d6f88bc64b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902036"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a>Identita: Konstruktor SignInManager přijímá nový parametr.

Počínaje ASP.NET Jádrem 3.0 `IUserConfirmation<TUser>` byl do `SignInManager` konstruktoru přidán nový parametr. Další informace naleznete [v tématu dotnet/aspnetcore#8356](https://github.com/dotnet/aspnetcore/issues/8356).

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="reason-for-change"></a>Důvod změny

Motivací pro změnu bylo přidat podporu pro nové e-mailové / potvrzovací toky v Identity.

#### <a name="recommended-action"></a>Doporučená akce

Pokud ručně vytváření `SignInManager`, poskytují implementaci `IUserConfirmation` nebo uchopit jeden z vkládání závislostí poskytnout.

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
