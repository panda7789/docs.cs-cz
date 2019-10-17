---
ms.openlocfilehash: a56c5fc32b5fd274d5da0d9b295918f5ea3b345e
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394467"
---
### <a name="signalr-hubconnection-resetsendping-and-resettimeout-methods-removed"></a>Signál: odebraly se HubConnection ResetSendPing a metody ResetTimeout.

Metody `ResetSendPing` a `ResetTimeout` byly odebrány z rozhraní API pro signalizaci `HubConnection`. Tyto metody byly původně určeny pouze pro interní použití, ale byly zveřejněny v ASP.NET Core 2,2. Tyto metody nebudou dostupné od verze ASP.NET Core 3,0 Preview 4. Diskuzi najdete v tématu [ASPNET/AspNetCore # 8543](https://github.com/aspnet/AspNetCore/issues/8543).

#### <a name="version-introduced"></a>Představená verze

3.0

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
