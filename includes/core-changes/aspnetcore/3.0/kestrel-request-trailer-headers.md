---
ms.openlocfilehash: b0e1d6d720a1c9b827fb4585606e64b545d395d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394126"
---
### <a name="kestrel-request-trailer-headers-moved-to-new-collection"></a>Poštolka: Žádost trailer záhlaví přesunuta do nové kolekce

V předchozích verzích Kestrel přidal hlavičky přívěsu HTTP/1.1 chunked do kolekce hlavičky požadavku, když bylo tělo požadavku přečteno až do konce. Toto chování způsobilo obavy z nejednoznačnosti mezi záhlavími a přívěsy. Bylo rozhodnuto přesunout přívěsy do nové kolekce.

HTTP/2 požadavek přívěsy nebyly k dispozici v ASP.NET Core 2.2, ale jsou nyní k dispozici také v této nové kolekci v ASP.NET Core 3.0.

Pro přístup k těmto přípojkovým vozidlům byly přidány nové metody rozšíření požadavků.

Přívěsy HTTP/1.1 jsou k dispozici po přečtení celého těla požadavku.

Upoutávky HTTP/2 jsou k dispozici po přijetí od klienta. Klient nebude posílat přívěsy, dokud celý tělo požadavku byl alespoň do vyrovnávací paměti serverem. Možná budete muset přečíst tělo požadavku uvolnit vyrovnávací paměti. Přívěsy jsou vždy k dispozici, pokud čtete tělo požadavku až do konce. Přívěsy označují konec karoserie.

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Žádost trailer záhlaví by být `HttpRequest.Headers` přidány do kolekce.

#### <a name="new-behavior"></a>Nové chování

V `HttpRequest.Headers` ynopačních hlavičkách request **trailer nejsou k dispozici.** Pro přístup `HttpRequest` k nim použijte následující metody rozšíření:

- `GetDeclaredTrailers()`- Dostane žádost "Trailer" záhlaví, které uvádí, které přívěsy očekávat po těle.
- `SupportsTrailers()`- Označuje, zda požadavek podporuje příjem záhlaví přívěsu.
- `CheckTrailersAvailable()`- Určuje, zda žádost podporuje přívěsy a zda jsou k dispozici pro čtení.
- `GetTrailer(string trailerName)`- Získá požadované koncové hlavičky z odpovědi.

#### <a name="reason-for-change"></a>Důvod změny

Upoutávky jsou klíčovou funkcí ve scénářích, jako je gRPC. Sloučení přívěsů do požádat záhlaví bylo matoucí pro uživatele.

#### <a name="recommended-action"></a>Doporučená akce

Pro přístup k přípojovým vozidlům použijte metody rozšíření týkající se přívěsu. `HttpRequest`

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.Http.HttpRequest.Headers?displayProperty=nameWithType>

<!--

#### Affected APIs

`P:Microsoft.AspNetCore.Http.HttpRequest.Headers`

-->
