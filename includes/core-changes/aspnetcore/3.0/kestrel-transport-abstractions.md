---
ms.openlocfilehash: fb23418816abcae125106c93b339a546aa9bc2ee
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721182"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a>Kestrel: abstrakce přenosu se odebrala a provedla jako veřejná.

V rámci přesunu z rozhraní API přenosové vrstvy pubternal se rozhraní API transportní vrstvy Kestrel zveřejňují jako veřejné rozhraní v `Microsoft.AspNetCore.Connections.Abstractions` knihovně.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="old-behavior"></a>Staré chování

- V knihovně jsou k dispozici abstrakce související s přenosem `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` .
- `ListenOptions.NoDelay`Vlastnost byla k dispozici.

#### <a name="new-behavior"></a>Nové chování

- `IConnectionListener`Rozhraní bylo představeno v `Microsoft.AspNetCore.Connections.Abstractions` knihovně, aby bylo možné vystavit z knihovny nejčastěji používané funkce `...Transport.Abstractions` .
- `NoDelay`Je nyní k dispozici v možnostech přenosu ( `LibuvTransportOptions` a `SocketTransportOptions` ).
- `SchedulingMode`již není k dispozici.

#### <a name="reason-for-change"></a>Důvod změny

ASP.NET Core 3,0 se přesunuly z rozhraní API "pubternal".

#### <a name="recommended-action"></a>Doporučená akce

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
