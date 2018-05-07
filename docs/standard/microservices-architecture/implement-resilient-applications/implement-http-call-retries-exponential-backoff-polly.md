---
title: Implementace opakování volání protokolu HTTP s exponenciálního omezení rychlosti s Polly
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace opakování volání protokolu HTTP s exponenciálního omezení rychlosti s Polly
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 66ac57fc824e01f96d6584ab86bb95ba1b0174a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-http-call-retries-with-exponential-backoff-with-polly"></a>Implementace opakování volání protokolu HTTP s exponenciálního omezení rychlosti s Polly

Doporučený postup pro opakování s exponenciálního omezení rychlosti je využívat výhod pokročilejší knihovny .NET jako open source [Polly](https://github.com/App-vNext/Polly) knihovny.

Polly je knihovny .NET, která poskytuje odolnost a možnosti přechodná selhání zpracování. Tyto možnosti můžete snadno implementovat použitím Polly zásad, například opakování, jistič, přepážkovou izolace, vypršení časového limitu a záložní. Polly cílem .NET 4.x a .NET Standard verze 1.0 (podporujícího .NET Core).

Zásady opakování v Polly je metoda používaná v eShopOnContainers při implementaci opakování HTTP. Rozhraní můžete implementovat, takže můžete vložit standardní funkce HttpClient nebo odolné verzi HttpClient pomocí Polly, v závislosti na Konfigurace zásady opakovaných pokusů, které chcete použít.

Následující příklad ukazuje rozhraní implementované v eShopOnContainers.

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

Standardní implementace můžete použít, pokud nechcete použít odolné mechanismus, jako při vývoji a testování jednodušší přístupy. Následující kód ukazuje standardní HttpClient implementace povolení žádosti s tokeny ověřování jako volitelné případu.

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

Zajímavé implementace je kód jiný, podobně jako třída, ale používá Polly implementovat odolné mechanismy, které chcete použít – v následujícím příkladu, opakování s exponenciálního omezení rychlosti.

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

Pomocí Polly definovat zásady opakování s počtem opakování exponenciálního omezení rychlosti konfigurace a akce, jež mají provést, když dojde k výjimce HTTP, jako je například protokolování chyba. V takovém případě zásad je nakonfigurovaná tak pokusí kolikrát zadané při registraci v kontejneru IoC typy. Z důvodu konfigurace exponenciálního omezení rychlosti vždy, když kód zjistí výjimku požadavku HTTP se pokusí požadavek Http po určenou dobu, která zvyšuje exponenciálnímu v závislosti na tom, jak bylo nakonfigurované zásady čekání.

Metodu důležité je HttpInvoker, což je díky požadavků HTTP v rámci této třídy nástroj. Metoda interně provede požadavek HTTP s \_policyWrapper.ExecuteAsync, který bere v úvahu zásady opakování.

V eShopOnContainers zadáte Polly zásady při registraci typy na kontejner IoC, jako v následujícím kódu z [webové aplikace MVC v souboru startup.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs) třídy.

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

Všimněte si, že IHttpClient objekty jsou vytvářeny instance jako singleton místo jako přechodný tak, aby připojení TCP se používají efektivně službou a [problém s sockets](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) nedojde.

Ale důležité o odolnosti je použít Polly WaitAndRetryAsync zásadu v rámci ResilientHttpClientFactory v metodě CreateResilientHttpClient, jak je znázorněno v následujícím kódu:

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
[Předchozí] (implement-custom-http-call-retries-exponential-backoff.md) [Další] (implementace okruh dělení pattern.md)
