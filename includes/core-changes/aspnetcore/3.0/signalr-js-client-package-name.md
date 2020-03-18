---
ms.openlocfilehash: f202b39f1a45f740625827be25e72df0e403d605
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902060"
---
### <a name="signalr-javascript-client-package-name-changed"></a>SignalR: Název klientského balíčku JavaScriptu byl změněn.

V ASP.NET Core 3.0 Preview 7 se název klientského `@microsoft/signalr`balíčku SignalR JavaScript změnil z na `@aspnet/signalr` . Změna názvu odráží skutečnost, že SignalR je užitečný ve více než jen ASP.NET aplikace core, díky službě Azure SignalR.

Chcete-li reagovat na tuto změnu, změňte `require` odkazy v souborech `import` *package.json,* příkazech a příkazech ECMAScript. Žádné rozhraní API se změní jako součást tohoto přejmenování.

Diskuse naleznete [v tématu dotnet/aspnetcore#11637](https://github.com/dotnet/aspnetcore/issues/11637).

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Klientský balíček `@aspnet/signalr`byl pojmenován .

#### <a name="new-behavior"></a>Nové chování

Klientský balíček `@microsoft/signalr`je pojmenován .

#### <a name="reason-for-change"></a>Důvod změny

Změna názvu objasňuje, že SignalR je užitečný mimo ASP.NET aplikace core, díky službě Azure SignalR.

#### <a name="recommended-action"></a>Doporučená akce

Přepněte na `@microsoft/signalr`nový balíček .

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádný

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
