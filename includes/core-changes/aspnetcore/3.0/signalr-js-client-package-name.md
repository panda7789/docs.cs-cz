---
ms.openlocfilehash: f202b39f1a45f740625827be25e72df0e403d605
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75902060"
---
### <a name="signalr-javascript-client-package-name-changed"></a>Signal: změnil se název balíčku klienta JavaScript

V ASP.NET Core 3,0 Preview 7 se název klientského balíčku JavaScriptu pro signály změnil z `@aspnet/signalr` na `@microsoft/signalr`. Tato změna názvu odráží skutečnost, že signál je užitečný ve více než jenom ASP.NET Corech aplikacích díky službě Azure Signaler.

Chcete-li na tuto změnu reagovat, změňte odkazy v souborech *Package. JSON* , `require` příkazy a ECMAScript `import` příkazy. V rámci tohoto přejmenování se žádné rozhraní API nemění.

Diskuzi najdete v tématu [dotnet/aspnetcore # 11637](https://github.com/dotnet/aspnetcore/issues/11637).

#### <a name="version-introduced"></a>Představená verze

3,0

#### <a name="old-behavior"></a>Staré chování

Balíček klienta byl pojmenován `@aspnet/signalr`.

#### <a name="new-behavior"></a>Nové chování

Balíček klienta má název `@microsoft/signalr`.

#### <a name="reason-for-change"></a>Důvod změny

Změna názvu upřesňuje, že je signál, který je užitečný pro ASP.NET Core aplikace, díky službě Azure Signal Service.

#### <a name="recommended-action"></a>Doporučená akce

Přepněte na `@microsoft/signalr`nového balíčku.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
