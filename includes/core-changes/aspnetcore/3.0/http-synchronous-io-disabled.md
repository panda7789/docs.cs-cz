---
ms.openlocfilehash: 53d2c989120c92f4e2d18f50ce4b364bd4c9b604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901798"
---
### <a name="http-synchronous-io-disabled-in-all-servers"></a>HTTP: Synchronní vi zakázáno na všech serverech

Počínaje ASP.NET jádrem 3.0 jsou synchronní operace serveru ve výchozím nastavení zakázány.

#### <a name="change-description"></a>Popis změny

`AllowSynchronousIO`je možnost na každém serveru, která povoluje nebo `HttpRequest.Body.Read` `HttpResponse.Body.Write`zakazuje `Stream.Flush`synchronní vypovězení vi, jako je , a . Tato rozhraní API jsou již dlouho zdrojem hladovění podprocesu a přestane reagovat aplikace. Počínaje ASP.NET Core 3.0 Preview 3, tyto synchronní operace jsou ve výchozím nastavení zakázány.

Ohrožené servery:

- Kestrel
- HttpSys
- IIS v průběhu
- Testovací server

Očekávejte chyby podobné:

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

Každý server `AllowSynchronousIO` má možnost, která řídí toto chování `false`a výchozí pro všechny z nich je nyní .

Chování může být také přepsána na základě požadavku jako dočasné zmírnění. Například:

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

Pokud máte potíže `TextWriter` s nebo jiný datový proud `Dispose`volání synchronní `DisposeAsync` rozhraní API v , volání nové rozhraní API místo.

Diskuse naleznete [v tématu dotnet/aspnetcore#7644](https://github.com/dotnet/aspnetcore/issues/7644).

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

`HttpRequest.Body.Read`, `HttpResponse.Body.Write`a `Stream.Flush` byly ve výchozím nastavení povoleny.

#### <a name="new-behavior"></a>Nové chování

Tato synchronní prostředí API jsou ve výchozím nastavení zakázána:

Očekávejte chyby podobné:

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

#### <a name="reason-for-change"></a>Důvod změny

Tato synchronní rozhraní API jsou již dlouho zdrojem hladovění podprocesu a přestane reagovat. Počínaje ASP.NET Core 3.0 Preview 3 jsou synchronní operace ve výchozím nastavení zakázány.

#### <a name="recommended-action"></a>Doporučená akce

Použijte asynchronní verze metod. Chování může být také přepsána na základě požadavku jako dočasné zmírnění.

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.IO.Stream.Flush%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.IO.Stream.Flush`
- `Overload:System.IO.Stream.Read`
- `Overload:System.IO.Stream.Write`

-->
