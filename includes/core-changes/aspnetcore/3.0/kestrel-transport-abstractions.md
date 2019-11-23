---
ms.openlocfilehash: f95c3916f4da8164cf927344f60f2845f04ddc5c
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394196"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a>Kestrel: abstrakce přenosu se odebrala a provedla jako veřejná.

V rámci přesunu z rozhraní API pro pubternal jsou v knihovně `Microsoft.AspNetCore.Connections.Abstractions` zpřístupněny rozhraní API přenosové vrstvy Kestrel jako veřejné rozhraní.

#### <a name="version-introduced"></a>Představená verze

3,0

#### <a name="old-behavior"></a>Staré chování

- V knihovně `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` byly k dispozici abstrakce související s přenosem.
- Vlastnost `ListenOptions.NoDelay` byla k dispozici.

#### <a name="new-behavior"></a>Nové chování

- Rozhraní `IConnectionListener` bylo představeno v knihovně `Microsoft.AspNetCore.Connections.Abstractions`, aby vystavilo nejvíce používané funkce z knihovny `...Transport.Abstractions`.
- `NoDelay` je teď k dispozici v možnostech přenosu (`LibuvTransportOptions` a `SocketTransportOptions`).
- `SchedulingMode` již není k dispozici.

#### <a name="reason-for-change"></a>Důvod změny

ASP.NET Core 3,0 se přesunuly z rozhraní API "pubternal".

#### <a name="recommended-action"></a>Doporučená akce

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné

<!-- 

### Affected APIs

Not detectable via API analysis

-->
