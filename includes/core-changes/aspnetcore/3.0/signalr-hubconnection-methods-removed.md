---
ms.openlocfilehash: de06825f1031d05bc83183a83bae165e2f9512ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901919"
---
### <a name="signalr-hubconnection-resetsendping-and-resettimeout-methods-removed"></a>SignalR: Metody ResetSendPing a ResetTimeout připojení hubu byly odebrány

Metody `ResetSendPing` `ResetTimeout` a byly odebrány `HubConnection` z rozhraní API signalr. Tyto metody byly původně určeny pouze pro vnitřní použití, ale byly zveřejněny v ASP.NET core 2.2. Tyto metody nebudou k dispozici počínaje ASP.NET verze Core 3.0 Preview 4. Diskuse naleznete [v tématu dotnet/aspnetcore#8543](https://github.com/dotnet/aspnetcore/issues/8543).

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

K dispozici byla rozhraní API.

#### <a name="new-behavior"></a>Nové chování

Api jsou odebrány.

#### <a name="reason-for-change"></a>Důvod změny

Tyto metody byly původně určeny pouze pro vnitřní použití, ale byly zveřejněny v ASP.NET core 2.2.

#### <a name="recommended-action"></a>Doporučená akce

Nepoužívejte tyto metody.

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing`
- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout`

-->
