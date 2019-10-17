---
ms.openlocfilehash: 04e5ca41374fc333a31f0422bc2e89f54b3cb049
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394298"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a>Hostování: AspNetCoreModule v1 odebrané ze sady hostování Windows

Počínaje ASP.NET Core 3,0 sada hostitelů Windows nebude obsahovat AspNetCoreModule (ANCM) v1.

ANCM v2 je zpětně kompatibilní s ANCM OutOfProcess a doporučuje se pro použití s aplikacemi ASP.NET Core 3,0.

Diskuzi najdete v tématu [ASPNET/AspNetCore # 7095](https://github.com/aspnet/AspNetCore/issues/7095).

#### <a name="version-introduced"></a>Představená verze

3.0

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
