---
ms.openlocfilehash: 75945e7ff26c1c6db891d12cef4c16ed210da6af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393941"
---
### <a name="mvc-web-api-compatibility-shim-removed"></a>MVC: Překrytí kompatibility webového rozhraní byla odstraněna.

Počínaje ASP.NET Core 3.0, balíček `Microsoft.AspNetCore.Mvc.WebApiCompatShim` již není k dispozici.

#### <a name="change-description"></a>Popis změny

Balíček `Microsoft.AspNetCore.Mvc.WebApiCompatShim` (WebApiCompatShim) poskytuje částečnou kompatibilitu v ASP.NET Core s ASP.NET 4.x Web API 2 pro zjednodušení migrace existujících implementací webového rozhraní API pro ASP.NET Core. Aplikace používající WebApiCompatShim však nemají prospěch z funkcí souvisejících s rozhraním API, které jsou dodávány v posledních ASP.NET vydánícore. Mezi tyto funkce patří vylepšené generování specifikace Open API, standardizované zpracování chyb a generování kódu klienta. Chcete-li lépe zaměřit úsilí rozhraní API v 3.0, WebApiCompatShim byl odebrán. Existující aplikace používající WebApiCompatShim by `[ApiController]` měly migrovat na novější model.

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="reason-for-change"></a>Důvod změny

Překrytí kompatibility webového rozhraní API byl nástroj pro migraci. Omezuje přístup uživatelů k novým funkcím přidaným v ASP.NET Core.

#### <a name="recommended-action"></a>Doporučená akce

Odeberte použití této překrytí a migrujte přímo na podobné funkce v ASP.NET samotnéjádro.

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.Mvc.WebApiCompatShim?displayProperty=fullName>

<!--

#### Affected APIs

N:Microsoft.AspNetCore.Mvc.WebApiCompatShim

-->
