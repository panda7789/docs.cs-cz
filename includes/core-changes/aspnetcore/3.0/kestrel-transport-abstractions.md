---
ms.openlocfilehash: f95c3916f4da8164cf927344f60f2845f04ddc5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394196"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a>Poštolka: Transport abstrakce odstraněny a zveřejněny

Jako součást odklonu od "pubternal" rozhraní API kestrel transportní vrstvy rozhraní `Microsoft.AspNetCore.Connections.Abstractions` jsou vystaveny jako veřejné rozhraní v knihovně.

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

- Abstrakce související s dopravou `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` byly k dispozici v knihovně.
- Nemovitost `ListenOptions.NoDelay` byla k dispozici.

#### <a name="new-behavior"></a>Nové chování

- Rozhraní `IConnectionListener` bylo zavedeno `Microsoft.AspNetCore.Connections.Abstractions` v knihovně vystavit nejpoužívanější `...Transport.Abstractions` funkce z knihovny.
- The `NoDelay` je nyní k`LibuvTransportOptions` dispozici `SocketTransportOptions`v možnostech dopravy ( a ).
- `SchedulingMode`již není k dispozici.

#### <a name="reason-for-change"></a>Důvod změny

ASP.NET Core 3.0 se odklonil od "pubternal" API.

#### <a name="recommended-action"></a>Doporučená akce

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádný

<!-- 

### Affected APIs

Not detectable via API analysis

-->
