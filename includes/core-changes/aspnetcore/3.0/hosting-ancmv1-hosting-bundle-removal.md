---
ms.openlocfilehash: 82103d82a6f68c62f3532608718bc71b0ba126bf
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901958"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a>Hostování: AspNetCoreModule v1 odebrané ze sady hostování Windows

Počínaje ASP.NET Core 3,0 sada hostitelů Windows nebude obsahovat AspNetCoreModule (ANCM) v1.

ANCM v2 je zpětně kompatibilní s ANCM OutOfProcess a doporučuje se pro použití s aplikacemi ASP.NET Core 3,0.

Diskuzi najdete v tématu [dotnet/aspnetcore # 7095](https://github.com/dotnet/aspnetcore/issues/7095).

#### <a name="version-introduced"></a>Představená verze

3,0

#### <a name="old-behavior"></a>Staré chování

ANCM v1 je součástí sady hostování systému Windows.

#### <a name="new-behavior"></a>Nové chování

ANCM v1 není součástí hostitelské sady Windows.

#### <a name="reason-for-change"></a>Důvod změny

ANCM v2 je zpětně kompatibilní s ANCM OutOfProcess a doporučuje se pro použití s aplikacemi ASP.NET Core 3,0.

#### <a name="recommended-action"></a>Doporučená akce

Použijte ANCM v2 s aplikacemi ASP.NET Core 3,0.

Pokud je požadováno ANCM V1, může být nainstalováno pomocí hostitelské sady Windows ASP.NET Core 2,1 nebo 2,2.

Tato změna způsobí přerušení aplikací ASP.NET Core 3,0, které:

- Výslovný souhlas s používáním ANCM V1 s `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`.
- Mít vlastní soubor *Web. config* s `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
