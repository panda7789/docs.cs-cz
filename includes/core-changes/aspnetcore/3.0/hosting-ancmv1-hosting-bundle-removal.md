---
ms.openlocfilehash: 82103d82a6f68c62f3532608718bc71b0ba126bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901958"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a>Hosting: AspNetCoreModule V1 odstraněn z Windows Hosting Bundle

Počínaje ASP.NET Core 3.0, Windows Hosting Bundle nebude obsahovat AspNetCoreModule (ANCM) V1.

ANCM V2 je zpětně kompatibilní s ANCM OutOfProcess a je doporučeno pro použití s aplikacemi ASP.NET Core 3.0.

Diskuse naleznete [v tématu dotnet/aspnetcore#7095](https://github.com/dotnet/aspnetcore/issues/7095).

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

ANCM V1 je součástí balíčku Windows Hosting.

#### <a name="new-behavior"></a>Nové chování

ANCM V1 není součástí balíčku Windows Hosting.

#### <a name="reason-for-change"></a>Důvod změny

ANCM V2 je zpětně kompatibilní s ANCM OutOfProcess a je doporučeno pro použití s aplikacemi ASP.NET Core 3.0.

#### <a name="recommended-action"></a>Doporučená akce

S aplikacemi core 3.0 ASP.NET Core 3.0 používejte ANCM V2.

Pokud je vyžadovánan cm V1, lze jej nainstalovat pomocí ASP.NET Core 2.1 nebo 2.2 Windows Hosting Bundle.

Tato změna přeruší ASP.NET aplikací core 3.0, které:

- Explicitně se rozhodl pro `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`použití ANCM V1 s .
- Mít vlastní *web.config* `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`soubor s .

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádný

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
