---
ms.openlocfilehash: 492d3e61acff31d3d6858a1c27cf353b04a05e36
ms.sourcegitcommit: d4f7ba08f2a45a9dbef53be597eed6d4a9410f29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2020
ms.locfileid: "86401975"
---
### <a name="security-cookie-name-encoding-removed"></a>Zabezpečení: odebrání kódování názvu souboru cookie

[Standard souborů cookie protokolu HTTP](https://tools.ietf.org/html/rfc6265#section-4.1.1) umožňuje pouze konkrétní znaky v názvech souborů cookie a hodnotách. Pro podporu nepovolených znaků ASP.NET Core:

* Při vytváření souboru cookie odpovědi se zakóduje.
* Dekóduje při čtení souboru cookie žádosti.

V ASP.NET Core 5,0 se toto chování kódování změnilo v reakci na zabezpečení.

Diskuzi najdete v tématu problém GitHubu [dotnet/aspnetcore # 23578](https://github.com/dotnet/aspnetcore/issues/23578).

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 8

#### <a name="old-behavior"></a>Staré chování

Názvy souborů cookie odpovědí jsou zakódovány. Název souboru cookie žádosti je dekódovat.

#### <a name="new-behavior"></a>Nové chování

Bylo odebráno kódování a dekódování názvů souborů cookie. Pro předchozí [podporované verze](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ASP.NET Core tým plánuje zmírnit problémy s dekódováním na místě. Kromě toho volání <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append%2A?displayProperty=nameWithType> s neplatným názvem souboru cookie vyvolá výjimku typu <xref:System.ArgumentException> . Kódování a dekódování hodnot souborů cookie zůstane beze změny.

#### <a name="reason-for-change"></a>Důvod změny

Byl zjištěn problém ve [více webových rozhraních](https://github.com/advisories/GHSA-j6w9-fv6q-3q52). Kódování a dekódování může útočníkovi umožnit obejít funkci zabezpečení nazvanou [předpony souborů cookie](https://tools.ietf.org/html/draft-ietf-httpbis-cookie-prefixes-00) pomocí zfalšovaných rezervovaných předpon, jako jsou `__Host-` například zakódované hodnoty `__%48ost-` . Útok vyžaduje sekundární zneužití pro vložení zfalšovaných souborů cookie, jako je například zranitelnost mezi lokalitami (XSS), na webu. Tyto předpony se ve výchozím nastavení nepoužívají v ASP.NET Core `Microsoft.Owin` knihoven nebo šablonách.

#### <a name="recommended-action"></a>Doporučená akce

Pokud přesouváte projekty na ASP.NET Core 5,0 nebo novější, ujistěte se, že názvy jejich souborů cookie odpovídají [požadavkům specifikace tokenů](https://tools.ietf.org/html/rfc2616#section-2.2): znaky ASCII bez ovládacích prvků a oddělovačů `"(" | ")" | "<" | ">" | "@" | "," | ";" | ":" | "\" | <"> | "/" | "[" | "]" | "?" | "=" | "{" | "}" | SP | HT` . Použití jiných znaků než ASCII v názvech souborů cookie nebo jiných hlaviček protokolu HTTP může způsobit výjimku ze serveru nebo nesprávně Trip klientovi.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.AspNetCore.Http.HttpRequest.Cookies%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.HttpResponse.Cookies%2A?displayProperty=nameWithType>
- <xref:Microsoft.Owin.IOwinRequest.Cookies?displayProperty=nameWithType>
- <xref:Microsoft.Owin.IOwinResponse.Cookies?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Http.HttpRequest.Cookies`
- `Overload:Microsoft.AspNetCore.Http.HttpResponse.Cookies`
- `P:Microsoft.Owin.IOwinRequest.Cookies`
- `P:Microsoft.Owin.IOwinResponse.Cookies`

-->
