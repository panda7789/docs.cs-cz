---
ms.openlocfilehash: de06825f1031d05bc83183a83bae165e2f9512ff
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901919"
---
### <a name="signalr-hubconnection-resetsendping-and-resettimeout-methods-removed"></a>Signál: odebraly se HubConnection ResetSendPing a metody ResetTimeout.

Metody `ResetSendPing` a `ResetTimeout` se odebraly z rozhraní API pro signalizaci `HubConnection`. Tyto metody byly původně určeny pouze pro interní použití, ale byly zveřejněny v ASP.NET Core 2,2. Tyto metody nebudou dostupné od verze ASP.NET Core 3,0 Preview 4. Diskuzi najdete v tématu [dotnet/aspnetcore # 8543](https://github.com/dotnet/aspnetcore/issues/8543).

#### <a name="version-introduced"></a>Představená verze

3,0

#### <a name="old-behavior"></a>Staré chování

Rozhraní API jsou k dispozici.

#### <a name="new-behavior"></a>Nové chování

Rozhraní API se odeberou.

#### <a name="reason-for-change"></a>Důvod změny

Tyto metody byly původně určeny pouze pro interní použití, ale byly zveřejněny v ASP.NET Core 2,2.

#### <a name="recommended-action"></a>Doporučená akce

Tyto metody nepoužívejte.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing`
- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout`

-->
