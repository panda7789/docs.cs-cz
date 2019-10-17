---
ms.openlocfilehash: b0e1d6d720a1c9b827fb4585606e64b545d395d7
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394126"
---
### <a name="kestrel-request-trailer-headers-moved-to-new-collection"></a>Kestrel: hlavičky přípojných vozidel žádosti přesunuté do nové kolekce

V předchozích verzích Kestrel přidal do kolekce hlaviček požadavků hlavičky přípojného bodu HTTP/1.1, když byl text požadavku přečtený na konci. Toto chování způsobilo obavy z nejednoznačnosti mezi hlavičkami a přípojnými vozidly. Rozhodnutí o přesunutí přípojných vozidel do nové kolekce bylo provedeno.

V ASP.NET Core 2,2 nejsou dostupné přípojné ovladače HTTP/2, ale teď jsou v této nové kolekci dostupné taky v ASP.NET Core 3,0.

Pro přístup k těmto přípojným vozidlům byly přidány nové metody rozšíření žádosti.

Po načtení celého textu žádosti jsou k dispozici Přípojná místa HTTP/1.1.

Po přijetí od klienta jsou k dispozici Přípojná místa HTTP/2. Klient nepošle přípojná vozidla, dokud celý text žádosti nebude alespoň ukládán do vyrovnávací paměti serverem. Možná budete muset přečíst text žádosti, abyste uvolnili místo ve vyrovnávací paměti. Pokud přečtete text žádosti na konec, jsou k dispozici vždy. Přípojná vozidla označují konec těla.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Do kolekce `HttpRequest.Headers` by se přidaly hlavičky žádosti o přípojné vozidlo.

#### <a name="new-behavior"></a>Nové chování

V kolekci `HttpRequest.Headers` **nejsou k dispozici** záhlaví přípojných vozidel. Pro přístup k nim použijte následující metody rozšíření `HttpRequest`:

- `GetDeclaredTrailers()` – načte hlavičku Request "přívěs", která obsahuje seznam přípojných vozidel, která se mají po tělo očekávat.
- `SupportsTrailers()` – určuje, zda požadavek podporuje příjem hlaviček přípojných vozidel.
- `CheckTrailersAvailable()` – určuje, zda požadavek podporuje Přípojná místa, a pokud jsou k dispozici pro čtení.
- `GetTrailer(string trailerName)` – Získá požadovanou ukončovací hlavičku z odpovědi.

#### <a name="reason-for-change"></a>Důvod změny

Přípojná vozidla jsou klíčovou funkcí ve scénářích, jako je gRPC. Sloučení přípojných vozidel v nástroji do hlaviček požadavků bylo matoucí pro uživatele.

#### <a name="recommended-action"></a>Doporučená akce

Pro přístup k přípojným vozidlům použijte metody rozšíření související s přívěsem na `HttpRequest`.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.Http.HttpRequest.Headers?displayProperty=nameWithType>

<!--

#### Affected APIs

`P:Microsoft.AspNetCore.Http.HttpRequest.Headers`

-->
