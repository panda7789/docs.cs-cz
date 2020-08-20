---
ms.openlocfilehash: 44d33fb28e66e590e4604c6dd2c73616e4c5e943
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728272"
---
### <a name="http-httpclient-instances-created-by-ihttpclientfactory-log-integer-status-codes"></a><span data-ttu-id="0b439-101">HTTP: HttpClient instance vytvořené pomocí kódů IHttpClientFactory pro celočíselné hodnoty log status</span><span class="sxs-lookup"><span data-stu-id="0b439-101">HTTP: HttpClient instances created by IHttpClientFactory log integer status codes</span></span>

<span data-ttu-id="0b439-102"><xref:System.Net.Http.HttpClient> instance vytvořené <xref:System.Net.Http.IHttpClientFactory> protokolem stavových kódů HTTP jako celé číslo namísto názvů stavových kódů.</span><span class="sxs-lookup"><span data-stu-id="0b439-102"><xref:System.Net.Http.HttpClient> instances created by <xref:System.Net.Http.IHttpClientFactory> log HTTP status codes as integers instead of with status code names.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0b439-103">Představená verze</span><span class="sxs-lookup"><span data-stu-id="0b439-103">Version introduced</span></span>

<span data-ttu-id="0b439-104">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="0b439-104">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0b439-105">Staré chování</span><span class="sxs-lookup"><span data-stu-id="0b439-105">Old behavior</span></span>

<span data-ttu-id="0b439-106">Protokolování používá textové popisy stavových kódů HTTP.</span><span class="sxs-lookup"><span data-stu-id="0b439-106">Logging uses the textual descriptions of HTTP status codes.</span></span> <span data-ttu-id="0b439-107">Vezměte v úvahu následující zprávy protokolu:</span><span class="sxs-lookup"><span data-stu-id="0b439-107">Consider the following log messages:</span></span>

```
Received HTTP response after 56.0044ms - OK
End processing HTTP request after 70.0862ms - OK
```

#### <a name="new-behavior"></a><span data-ttu-id="0b439-108">Nové chování</span><span class="sxs-lookup"><span data-stu-id="0b439-108">New behavior</span></span>

<span data-ttu-id="0b439-109">Protokolování používá celočíselné hodnoty stavových kódů HTTP.</span><span class="sxs-lookup"><span data-stu-id="0b439-109">Logging uses the integer values of HTTP status codes.</span></span> <span data-ttu-id="0b439-110">Vezměte v úvahu následující zprávy protokolu:</span><span class="sxs-lookup"><span data-stu-id="0b439-110">Consider the following log messages:</span></span>

```
Received HTTP response after 56.0044ms - 200
End processing HTTP request after 70.0862ms - 200
```

#### <a name="reason-for-change"></a><span data-ttu-id="0b439-111">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="0b439-111">Reason for change</span></span>

<span data-ttu-id="0b439-112">Původní chování tohoto protokolování je nekonzistentní s jinými částmi ASP.NET Core, které vždycky používaly celočíselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0b439-112">The original behavior of this logging is inconsistent with other parts of ASP.NET Core that have always used integer values.</span></span> <span data-ttu-id="0b439-113">Nekonzistence usnadňuje dotazování protokolů prostřednictvím strukturovaných protokolovacích systémů, jako je [Elasticsearch](https://www.elastic.co/elasticsearch/).</span><span class="sxs-lookup"><span data-stu-id="0b439-113">The inconsistency makes logs difficult to query via structured logging systems such as [Elasticsearch](https://www.elastic.co/elasticsearch/).</span></span> <span data-ttu-id="0b439-114">Další kontext naleznete v tématu [dotnet/Extensions # 1549](https://github.com/dotnet/extensions/issues/1549).</span><span class="sxs-lookup"><span data-stu-id="0b439-114">For more context, see [dotnet/extensions#1549](https://github.com/dotnet/extensions/issues/1549).</span></span>

<span data-ttu-id="0b439-115">Použití celočíselných hodnot je flexibilnější než text, protože umožňuje dotazy na rozsahy hodnot.</span><span class="sxs-lookup"><span data-stu-id="0b439-115">Using integer values is more flexible than text because it allows queries on ranges of values.</span></span>

<span data-ttu-id="0b439-116">Přidání další hodnoty protokolu k zachycení stavového kódu pro celý kód byl zvážen.</span><span class="sxs-lookup"><span data-stu-id="0b439-116">Adding another log value to capture the integer status code was considered.</span></span> <span data-ttu-id="0b439-117">To bohužel by zavedlo další nekonzistenci se zbytkem ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0b439-117">Unfortunately, doing so would introduce another inconsistency with the rest of ASP.NET Core.</span></span> <span data-ttu-id="0b439-118">Protokolování HttpClient a Server HTTP/protokolování hostování používají stejný `StatusCode` název klíče již.</span><span class="sxs-lookup"><span data-stu-id="0b439-118">HttpClient logging and HTTP server/hosting logging use the same `StatusCode` key name already.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0b439-119">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="0b439-119">Recommended action</span></span>

<span data-ttu-id="0b439-120">Nejlepší možností je aktualizovat dotazy protokolování tak, aby používaly celočíselné hodnoty stavových kódů.</span><span class="sxs-lookup"><span data-stu-id="0b439-120">The best option is to update logging queries to use the integer values of status codes.</span></span> <span data-ttu-id="0b439-121">Tato možnost může způsobit potíže s psaním dotazů napříč více verzemi ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0b439-121">This option may cause some difficulty writing queries across multiple ASP.NET Core versions.</span></span> <span data-ttu-id="0b439-122">Použití celých čísel pro tento účel je však mnohem flexibilnější pro dotazování protokolů.</span><span class="sxs-lookup"><span data-stu-id="0b439-122">However, using integers for this purpose is much more flexible for querying logs.</span></span>

<span data-ttu-id="0b439-123">Pokud potřebujete vynutit kompatibilitu se starým chováním a používat textové stavové kódy, nahraďte `IHttpClientFactory` protokolování vlastními:</span><span class="sxs-lookup"><span data-stu-id="0b439-123">If you need to force compatibility with the old behavior and use textual status codes, replace the `IHttpClientFactory` logging with your own:</span></span>

1. <span data-ttu-id="0b439-124">Do projektu zkopírujte verze .NET Core 3,1 následujících tříd:</span><span class="sxs-lookup"><span data-stu-id="0b439-124">Copy the .NET Core 3.1 versions of the following classes into your project:</span></span>

    * [<span data-ttu-id="0b439-125">LoggingHttpMessageHandlerBuilderFilter</span><span class="sxs-lookup"><span data-stu-id="0b439-125">LoggingHttpMessageHandlerBuilderFilter</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingHttpMessageHandlerBuilderFilter.cs)
    * [<span data-ttu-id="0b439-126">LoggingHttpMessageHandler</span><span class="sxs-lookup"><span data-stu-id="0b439-126">LoggingHttpMessageHandler</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingHttpMessageHandler.cs)
    * [<span data-ttu-id="0b439-127">LoggingScopeHttpMessageHandler</span><span class="sxs-lookup"><span data-stu-id="0b439-127">LoggingScopeHttpMessageHandler</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingScopeHttpMessageHandler.cs)
    * [<span data-ttu-id="0b439-128">HttpHeadersLogValue</span><span class="sxs-lookup"><span data-stu-id="0b439-128">HttpHeadersLogValue</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/HttpHeadersLogValue.cs)

1. <span data-ttu-id="0b439-129">Přejmenujte třídy, aby nedocházelo ke konfliktům s veřejnými typy v balíčku NuGet [Microsoft. Extensions. http](https://www.nuget.org/packages/Microsoft.Extensions.Http) .</span><span class="sxs-lookup"><span data-stu-id="0b439-129">Rename the classes to avoid conflicts with public types in the [Microsoft.Extensions.Http](https://www.nuget.org/packages/Microsoft.Extensions.Http) NuGet package.</span></span>

1. <span data-ttu-id="0b439-130">Nahraďte vestavěnou implementaci `LoggingHttpMessageHandlerBuilderFilter` vlastním v `Startup.ConfigureServices` metodě projektu.</span><span class="sxs-lookup"><span data-stu-id="0b439-130">Replace the built-in implementation of `LoggingHttpMessageHandlerBuilderFilter` with your own in the project's `Startup.ConfigureServices` method.</span></span> <span data-ttu-id="0b439-131">Příklad:</span><span class="sxs-lookup"><span data-stu-id="0b439-131">For example:</span></span>

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

#### <a name="category"></a><span data-ttu-id="0b439-132">Kategorie</span><span class="sxs-lookup"><span data-stu-id="0b439-132">Category</span></span>

<span data-ttu-id="0b439-133">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0b439-133">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0b439-134">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="0b439-134">Affected APIs</span></span>

<xref:System.Net.Http.HttpClient?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:System.Net.Http.HttpClient`

-->
