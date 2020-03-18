---
ms.openlocfilehash: e5355387d5cb6d9e6de89f5b85e64bc100b32ae1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522695"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a>SPA: SpaServices a NodeServices již nespadají zpět do konzoly logger

<xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType>a <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> nebude zobrazovat protokoly konzoly, pokud není nakonfigurováno protokolování.

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

`Microsoft.AspNetCore.SpaServices`a `Microsoft.AspNetCore.NodeServices` slouží k automatickému vytvoření protokolování konzoly, když protokolování není nakonfigurováno.

#### <a name="new-behavior"></a>Nové chování

`Microsoft.AspNetCore.SpaServices`a `Microsoft.AspNetCore.NodeServices` nebude zobrazovat protokoly konzoly, pokud není nakonfigurováno protokolování.

#### <a name="reason-for-change"></a>Důvod změny

Je třeba zarovnat s tím, jak ostatní balíčky ASP.NET Core implementují protokolování.

#### <a name="recommended-action"></a>Doporučená akce

Pokud je vyžadováno staré chování, chcete-li nakonfigurovat protokolování konzoly, přidejte `services.AddLogging(builder => builder.AddConsole())` `Setup.ConfigureServices` metodu.

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádný

<!--

#### Affected APIs

Not detectable via API analysis

-->
