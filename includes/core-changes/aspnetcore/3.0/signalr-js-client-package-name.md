---
ms.openlocfilehash: acef6d7177ee5ad7e18dc8ba1e383d6f76263623
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393955"
---
### <a name="signalr-javascript-client-package-name-changed"></a>Signal: změnil se název balíčku klienta JavaScript

V ASP.NET Core 3,0 Preview 7 se název klientského balíčku JavaScriptu pro signály změnil z `@aspnet/signalr` na `@microsoft/signalr`. Tato změna názvu odráží skutečnost, že signál je užitečný ve více než jenom ASP.NET Corech aplikacích díky službě Azure Signaler.

Pro reakci na tuto změnu, změňte odkazy v souborech *Package. JSON* , příkazech `require` a příkazech jazyka ECMAScript `import`. V rámci tohoto přejmenování se žádné rozhraní API nemění.

Diskuzi najdete v tématu [ASPNET/AspNetCore # 11637](https://github.com/aspnet/AspNetCore/issues/11637).

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Balíček klienta byl pojmenován `@aspnet/signalr`.

#### <a name="new-behavior"></a>Nové chování

Balíček klienta má název `@microsoft/signalr`.

#### <a name="reason-for-change"></a>Důvod změny

Změna názvu upřesňuje, že je signál, který je užitečný pro ASP.NET Core aplikace, díky službě Azure Signal Service.

#### <a name="recommended-action"></a>Doporučená akce

Přepněte do nového balíčku `@microsoft/signalr`.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
