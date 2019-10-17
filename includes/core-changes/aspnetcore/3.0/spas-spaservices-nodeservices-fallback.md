---
ms.openlocfilehash: 1017801346e65940e4dc075ef72f7a00d7e6bcd9
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393959"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a>Jednostránkové: SpaServices a NodeServices se už nevrátí do protokolovacího nástroje konzoly.

<xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType> a <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> nezobrazí protokoly konzoly, pokud není nakonfigurováno protokolování.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="old-behavior"></a>Staré chování

`Microsoft.AspNetCore.SpaServices` a `Microsoft.AspNetCore.NodeServices` slouží k automatickému vytvoření protokolovacího nástroje konzoly, pokud není nakonfigurováno protokolování. 

#### <a name="new-behavior"></a>Nové chování

`Microsoft.AspNetCore.SpaServices` a `Microsoft.AspNetCore.NodeServices` nezobrazí protokoly konzoly, pokud není nakonfigurováno protokolování.

#### <a name="reason-for-change"></a>Důvod změny

Je potřeba se zarovnávat s tím, jak jiné balíčky ASP.NET Core implementují protokolování.

#### <a name="recommended-action"></a>Doporučená akce

Pokud je nutné staré chování, nakonfigurujte protokolování konzoly přidáním `services.AddLogging(builder => builder.AddConsole())` do metody `Setup.ConfigureServices`.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
