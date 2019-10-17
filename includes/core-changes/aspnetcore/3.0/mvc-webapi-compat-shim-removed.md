---
ms.openlocfilehash: 75945e7ff26c1c6db891d12cef4c16ed210da6af
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393941"
---
### <a name="mvc-web-api-compatibility-shim-removed"></a>MVC: překrytí kompatibility webového rozhraní API se odebralo.

Počínaje verzí ASP.NET Core 3,0 není balíček `Microsoft.AspNetCore.Mvc.WebApiCompatShim` k dispozici.

#### <a name="change-description"></a>Změnit popis

Balíček `Microsoft.AspNetCore.Mvc.WebApiCompatShim` (WebApiCompatShim) poskytuje částečnou kompatibilitu v ASP.NET Core s webovým rozhraním API 2 ASP.NET 4. x pro zjednodušení migrace stávajících implementací webového rozhraní API na ASP.NET Core. Aplikace, které používají WebApiCompatShim, ale netěží z funkcí souvisejících s rozhraním API, které se dodávají v posledních ASP.NET Core verzích. Mezi tyto funkce patří vylepšené generování specifikace Open API, standardizované zpracování chyb a generování kódu klienta. Aby se zajistilo lepší zaměření na úsilí rozhraní API v 3,0, odebral se WebApiCompatShim. Stávající aplikace, které používají WebApiCompatShim, by se měly migrovat na novější model `[ApiController]`.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="reason-for-change"></a>Důvod změny

Překrytí kompatibility webového rozhraní API je nástroj pro migraci. Omezuje přístup uživatelů k novým funkcím přidaným v ASP.NET Core.

#### <a name="recommended-action"></a>Doporučená akce

Odeberte použití tohoto překrytí a přímo se migrujte na podobné funkce v ASP.NET Core samotné.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.Mvc.WebApiCompatShim?displayProperty=fullName>

<!--

#### Affected APIs

N:Microsoft.AspNetCore.Mvc.WebApiCompatShim

-->
