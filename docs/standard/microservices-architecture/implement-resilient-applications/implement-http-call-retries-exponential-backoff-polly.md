---
title: "Implementace opakování volání protokolu HTTP s exponenciálního omezení rychlosti s Polly"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace opakování volání protokolu HTTP s exponenciálního omezení rychlosti s Polly"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 122f617874188d3bffe689d6b3cf7d7249c59c3b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-http-call-retries-with-exponential-backoff-with-polly"></a><span data-ttu-id="1f4cf-104">Implementace opakování volání protokolu HTTP s exponenciálního omezení rychlosti s Polly</span><span class="sxs-lookup"><span data-stu-id="1f4cf-104">Implementing HTTP call retries with exponential backoff with Polly</span></span>

<span data-ttu-id="1f4cf-105">Doporučený postup pro opakování s exponenciálního omezení rychlosti je využívat výhod pokročilejší knihovny .NET jako open source [Polly](https://github.com/App-vNext/Polly) knihovny.</span><span class="sxs-lookup"><span data-stu-id="1f4cf-105">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open source [Polly](https://github.com/App-vNext/Polly) library.</span></span>

<span data-ttu-id="1f4cf-106">Polly je knihovny .NET, která poskytuje odolnost a možnosti přechodná selhání zpracování.</span><span class="sxs-lookup"><span data-stu-id="1f4cf-106">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="1f4cf-107">Tyto možnosti můžete snadno implementovat použitím Polly zásad, například opakování, jistič, přepážkovou izolace, vypršení časového limitu a záložní.</span><span class="sxs-lookup"><span data-stu-id="1f4cf-107">You can implement those capabilities easily by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="1f4cf-108">Polly cílem .NET 4.x a .NET Standard verze 1.0 (podporujícího .NET Core).</span><span class="sxs-lookup"><span data-stu-id="1f4cf-108">Polly targets .NET 4.x and the .NET Standard version 1.0 (which supports .NET Core).</span></span>

<span data-ttu-id="1f4cf-109">Zásady opakování v Polly je metoda používaná v eShopOnContainers při implementaci opakování HTTP.</span><span class="sxs-lookup"><span data-stu-id="1f4cf-109">The Retry policy in Polly is the approach used in eShopOnContainers when implementing HTTP retries.</span></span> <span data-ttu-id="1f4cf-110">Rozhraní můžete implementovat, takže můžete vložit standardní funkce HttpClient nebo odolné verzi HttpClient pomocí Polly, v závislosti na Konfigurace zásady opakovaných pokusů, které chcete použít.</span><span class="sxs-lookup"><span data-stu-id="1f4cf-110">You can implement an interface so you can inject either standard HttpClient functionality or a resilient version of HttpClient using Polly, depending on what retry policy configuration you want to use.</span></span>

<span data-ttu-id="1f4cf-111">Následující příklad ukazuje rozhraní implementované v eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="1f4cf-111">The following example shows the interface implemented in eShopOnContainers.</span></span>

```csharp
public interface IHttpClient
{
    Task<string> GetStringAsync(string uri, string authorizationToken = null,
        string authorizationMethod = "Bearer");
        Task<HttpResponseMessage> PostAsync<T>(string uri, T item,
        string authorizationToken = null, string requestId = null,
        string authorizationMethod = "Bearer");

    Task<HttpResponseMessage> DeleteAsync(string uri,
        string authorizationToken = null, string requestId = null,
        string authorizationMethod = "Bearer");

    // Other methods ...
}
```

<span data-ttu-id="1f4cf-112">Standardní implementace můžete použít, pokud nechcete použít odolné mechanismus, jako při vývoji a testování jednodušší přístupy.</span><span class="sxs-lookup"><span data-stu-id="1f4cf-112">You can use the standard implementation if you do not want to use a resilient mechanism, as when you are developing or testing simpler approaches.</span></span> <span data-ttu-id="1f4cf-113">Následující kód ukazuje standardní HttpClient implementace povolení žádosti s tokeny ověřování jako volitelné případu.</span><span class="sxs-lookup"><span data-stu-id="1f4cf-113">The following code shows the standard HttpClient implementation allowing requests with authentication tokens as an optional case.</span></span>

```csharp
public class StandardHttpClient : IHttpClient
{
    private HttpClient _client;
    private ILogger<StandardHttpClient> _logger;

    public StandardHttpClient(ILogger<StandardHttpClient> logger)
    {
        _client = new HttpClient();
        _logger = logger;
    }

    public async Task<string> GetStringAsync(string uri,
        string authorizationToken = null,
        string authorizationMethod = "Bearer")
    {
        var requestMessage = new HttpRequestMessage(HttpMethod.Get, uri);
        if (authorizationToken != null)
        {
            requestMessage.Headers.Authorization =
                new AuthenticationHeaderValue(authorizationMethod, authorizationToken);
        }
        var response = await _client.SendAsync(requestMessage);
        return await response.Content.ReadAsStringAsync();
    }

    public async Task<HttpResponseMessage> PostAsync<T>(string uri, T item,
        string authorizationToken = null, string requestId = null,
        string authorizationMethod = "Bearer")
    {
        // Rest of the code and other Http methods ...
```

<span data-ttu-id="1f4cf-114">Zajímavé implementace je kód jiný, podobně jako třída, ale používá Polly implementovat odolné mechanismy, které chcete použít – v následujícím příkladu, opakování s exponenciálního omezení rychlosti.</span><span class="sxs-lookup"><span data-stu-id="1f4cf-114">The interesting implementation is to code another, similar class, but using Polly to implement the resilient mechanisms you want to use—in the following example, retries with exponential backoff.</span></span>

```csharp
public class ResilientHttpClient : IHttpClient
{
    private HttpClient _client;
    private PolicyWrap _policyWrapper;
    private ILogger<ResilientHttpClient> _logger;

    public ResilientHttpClient(Policy[] policies,
        ILogger<ResilientHttpClient> logger)
    {
        _client = new HttpClient();
        _logger = logger;
        // Add Policies to be applied
        _policyWrapper = Policy.WrapAsync(policies);
    }

    private Task<T> HttpInvoker<T>(Func<Task<T>> action)
    {
        // Executes the action applying all
        // the policies defined in the wrapper
        return _policyWrapper.ExecuteAsync(() => action());
    }

    public Task<string> GetStringAsync(string uri,
        string authorizationToken = null,
        string authorizationMethod = "Bearer")
    {
        return HttpInvoker(async () =>
        {
            var requestMessage = new HttpRequestMessage(HttpMethod.Get, uri);
            // The Token's related code eliminated for clarity in code snippet
            var response = await _client.SendAsync(requestMessage);
            return await response.Content.ReadAsStringAsync();
        });
    }
    // Other Http methods executed through HttpInvoker so it applies Polly policies
    // ...
}
```

<span data-ttu-id="1f4cf-115">Pomocí Polly definovat zásady opakování s počtem opakování exponenciálního omezení rychlosti konfigurace a akce, jež mají provést, když dojde k výjimce HTTP, jako je například protokolování chyba.</span><span class="sxs-lookup"><span data-stu-id="1f4cf-115">With Polly, you define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there is an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="1f4cf-116">V takovém případě zásad je nakonfigurovaná tak pokusí kolikrát zadané při registraci v kontejneru IoC typy.</span><span class="sxs-lookup"><span data-stu-id="1f4cf-116">In this case, the policy is configured so it will try the number of times specified when registering the types in the IoC container.</span></span> <span data-ttu-id="1f4cf-117">Z důvodu konfigurace exponenciálního omezení rychlosti vždy, když kód zjistí výjimku požadavku HTTP se pokusí požadavek Http po určenou dobu, která zvyšuje exponenciálnímu v závislosti na tom, jak bylo nakonfigurované zásady čekání.</span><span class="sxs-lookup"><span data-stu-id="1f4cf-117">Because of the exponential backoff configuration, whenever the code detects an HttpRequest exception, it retries the Http request after waiting an amount of time that increases exponentially depending on how the policy was configured.</span></span>

<span data-ttu-id="1f4cf-118">Metodu důležité je HttpInvoker, což je díky požadavků HTTP v rámci této třídy nástroj.</span><span class="sxs-lookup"><span data-stu-id="1f4cf-118">The important method is HttpInvoker, which is what makes HTTP requests throughout this utility class.</span></span> <span data-ttu-id="1f4cf-119">Metoda interně provede požadavek HTTP s \_policyWrapper.ExecuteAsync, který bere v úvahu zásady opakování.</span><span class="sxs-lookup"><span data-stu-id="1f4cf-119">That method internally executes the HTTP request with \_policyWrapper.ExecuteAsync, which takes into account the retry policy.</span></span>

<span data-ttu-id="1f4cf-120">V eShopOnContainers zadáte Polly zásady při registraci typy na kontejner IoC, jako v následujícím kódu z [webové aplikace MVC v souboru startup.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs) třídy.</span><span class="sxs-lookup"><span data-stu-id="1f4cf-120">In eShopOnContainers you specify Polly policies when registering the types at the IoC container, as in the following code from the [MVC web app at the startup.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs) class.</span></span>

```csharp
// Startup.cs class
if (Configuration.GetValue<string>("UseResilientHttp") == bool.TrueString)
{
    services.AddTransient<IResilientHttpClientFactory,
        ResilientHttpClientFactory>();
    services.AddSingleton<IHttpClient,
        ResilientHttpClient>(sp =>
            sp.GetService<IResilientHttpClientFactory>().
            CreateResilientHttpClient());
}
else
{
    services.AddSingleton<IHttpClient, StandardHttpClient>();
}
```

<span data-ttu-id="1f4cf-121">Všimněte si, že IHttpClient objekty jsou vytvářeny instance jako singleton místo jako přechodný tak, aby připojení TCP se používají efektivně službou a [problém s sockets](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) nedojde.</span><span class="sxs-lookup"><span data-stu-id="1f4cf-121">Note that the IHttpClient objects are instantiated as singleton instead of as transient so that TCP connections are used efficiently by the service and [an issue with sockets](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) will not occur.</span></span>

<span data-ttu-id="1f4cf-122">Ale důležité o odolnosti je použít Polly WaitAndRetryAsync zásadu v rámci ResilientHttpClientFactory v metodě CreateResilientHttpClient, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="1f4cf-122">But the important point about resiliency is that you apply the Polly WaitAndRetryAsync policy within ResilientHttpClientFactory in the CreateResilientHttpClient method, as shown in the following code:</span></span>

```csharp
public ResilientHttpClient CreateResilientHttpClient()
    => new ResilientHttpClient(CreatePolicies(), _logger);

// Other code
private Policy[] CreatePolicies()
    => new Policy[]
    {
        Policy.Handle<HttpRequestException>()
            .WaitAndRetryAsync(
        // number of retries
        6,
        // exponential backoff
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)),
        // on retry
        (exception, timeSpan, retryCount, context) =>
        {
            var msg = $"Retry {retryCount} implemented with Pollys RetryPolicy " +
            $"of {context.PolicyKey} " +
            $"at {context.ExecutionKey}, " +
            $"due to: {exception}.";
            _logger.LogWarning(msg);
            _logger.LogDebug(msg);
        }),
    }
```


>[!div class="step-by-step"]
<span data-ttu-id="1f4cf-123">[Předchozí] (implement-custom-http-call-retries-exponential-backoff.md) [Další] (implementace okruh dělení pattern.md)</span><span class="sxs-lookup"><span data-stu-id="1f4cf-123">[Previous] (implement-custom-http-call-retries-exponential-backoff.md) [Next] (implement-circuit-breaker-pattern.md)</span></span>
