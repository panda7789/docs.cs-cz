---
ms.openlocfilehash: 53d2c989120c92f4e2d18f50ce4b364bd4c9b604
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901798"
---
### <a name="http-synchronous-io-disabled-in-all-servers"></a>HTTP: synchronní v/v – zakázáno na všech serverech

Počínaje ASP.NET Core 3,0 jsou synchronní operace serveru ve výchozím nastavení zakázané.

#### <a name="change-description"></a>Popis změny

`AllowSynchronousIO` je možnost na každém serveru, který povoluje nebo zakazuje synchronní rozhraní API pro vstupně-výstupní operace jako `HttpRequest.Body.Read`, `HttpResponse.Body.Write`a `Stream.Flush`. Tato rozhraní API jsou dlouhodobě zdrojem vláken vyčerpání a aplikace přestane reagovat. Počínaje verzí ASP.NET Core 3,0 Preview 3 jsou tyto synchronní operace ve výchozím nastavení zakázány.

Ovlivněné servery:

- Kestrel
- HttpSys
- Vnitroprocesové v rámci služby IIS
- TestServer

Očekávat chyby podobné:

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

Každý server má možnost `AllowSynchronousIO`, která řídí toto chování a výchozí hodnota pro všechny jsou nyní `false`.

Chování je také možné přepsat na základě jednotlivých požadavků jako dočasné zmírnění. Příklad:

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

Pokud máte potíže s `TextWriter` nebo jiným datovým proudem, který volá synchronní rozhraní API v `Dispose`, zavolejte místo toho nové rozhraní API `DisposeAsync`.

Diskuzi najdete v tématu [dotnet/aspnetcore # 7644](https://github.com/dotnet/aspnetcore/issues/7644).

#### <a name="version-introduced"></a>Představená verze

3,0

#### <a name="old-behavior"></a>Staré chování

ve výchozím nastavení jsou povolené `HttpRequest.Body.Read`, `HttpResponse.Body.Write`a `Stream.Flush`.

#### <a name="new-behavior"></a>Nové chování

Ve výchozím nastavení nejsou povolena tato synchronní rozhraní API:

Očekávat chyby podobné:

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

#### <a name="reason-for-change"></a>Důvod změny

Tato synchronní rozhraní API byla dlouhodobě zdrojem vláken vyčerpání a aplikace přestane reagovat. Počínaje verzí ASP.NET Core 3,0 Preview 3 jsou synchronní operace ve výchozím nastavení zakázané.

#### <a name="recommended-action"></a>Doporučená akce

Použijte asynchronní verze metod. Chování je také možné přepsat na základě jednotlivých požadavků jako dočasné zmírnění.

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

#### <a name="category"></a>Kategorie

ASP.NET Core

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
