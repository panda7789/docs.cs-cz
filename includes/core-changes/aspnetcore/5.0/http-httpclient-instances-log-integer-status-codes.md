---
ms.openlocfilehash: 44d33fb28e66e590e4604c6dd2c73616e4c5e943
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728272"
---
### <a name="http-httpclient-instances-created-by-ihttpclientfactory-log-integer-status-codes"></a>HTTP: HttpClient instance vytvořené pomocí kódů IHttpClientFactory pro celočíselné hodnoty log status

<xref:System.Net.Http.HttpClient> instance vytvořené <xref:System.Net.Http.IHttpClientFactory> protokolem stavových kódů HTTP jako celé číslo namísto názvů stavových kódů.

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 1

#### <a name="old-behavior"></a>Staré chování

Protokolování používá textové popisy stavových kódů HTTP. Vezměte v úvahu následující zprávy protokolu:

```
Received HTTP response after 56.0044ms - OK
End processing HTTP request after 70.0862ms - OK
```

#### <a name="new-behavior"></a>Nové chování

Protokolování používá celočíselné hodnoty stavových kódů HTTP. Vezměte v úvahu následující zprávy protokolu:

```
Received HTTP response after 56.0044ms - 200
End processing HTTP request after 70.0862ms - 200
```

#### <a name="reason-for-change"></a>Důvod změny

Původní chování tohoto protokolování je nekonzistentní s jinými částmi ASP.NET Core, které vždycky používaly celočíselné hodnoty. Nekonzistence usnadňuje dotazování protokolů prostřednictvím strukturovaných protokolovacích systémů, jako je [Elasticsearch](https://www.elastic.co/elasticsearch/). Další kontext naleznete v tématu [dotnet/Extensions # 1549](https://github.com/dotnet/extensions/issues/1549).

Použití celočíselných hodnot je flexibilnější než text, protože umožňuje dotazy na rozsahy hodnot.

Přidání další hodnoty protokolu k zachycení stavového kódu pro celý kód byl zvážen. To bohužel by zavedlo další nekonzistenci se zbytkem ASP.NET Core. Protokolování HttpClient a Server HTTP/protokolování hostování používají stejný `StatusCode` název klíče již.

#### <a name="recommended-action"></a>Doporučená akce

Nejlepší možností je aktualizovat dotazy protokolování tak, aby používaly celočíselné hodnoty stavových kódů. Tato možnost může způsobit potíže s psaním dotazů napříč více verzemi ASP.NET Core. Použití celých čísel pro tento účel je však mnohem flexibilnější pro dotazování protokolů.

Pokud potřebujete vynutit kompatibilitu se starým chováním a používat textové stavové kódy, nahraďte `IHttpClientFactory` protokolování vlastními:

1. Do projektu zkopírujte verze .NET Core 3,1 následujících tříd:

    * [LoggingHttpMessageHandlerBuilderFilter](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingHttpMessageHandlerBuilderFilter.cs)
    * [LoggingHttpMessageHandler](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingHttpMessageHandler.cs)
    * [LoggingScopeHttpMessageHandler](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingScopeHttpMessageHandler.cs)
    * [HttpHeadersLogValue](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/HttpHeadersLogValue.cs)

1. Přejmenujte třídy, aby nedocházelo ke konfliktům s veřejnými typy v balíčku NuGet [Microsoft. Extensions. http](https://www.nuget.org/packages/Microsoft.Extensions.Http) .

1. Nahraďte vestavěnou implementaci `LoggingHttpMessageHandlerBuilderFilter` vlastním v `Startup.ConfigureServices` metodě projektu. Příklad:

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        // Other service registrations go first. Code omitted for brevity.

        // Place the following after all AddHttpClient registrations.
        var descriptors = services.Where(
            s => s.ServiceType == typeof(IHttpMessageHandlerBuilderFilter));
        foreach (var descriptor in descriptors)
        {
            services.Remove(descriptor);
        }

        services.AddSingleton<IHttpMessageHandlerBuilderFilter,
                              MyLoggingHttpMessageHandlerBuilderFilter>();
    }
    ```

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:System.Net.Http.HttpClient?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:System.Net.Http.HttpClient`

-->
