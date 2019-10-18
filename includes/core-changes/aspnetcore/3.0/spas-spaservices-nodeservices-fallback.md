---
ms.openlocfilehash: e5355387d5cb6d9e6de89f5b85e64bc100b32ae1
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522695"
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
