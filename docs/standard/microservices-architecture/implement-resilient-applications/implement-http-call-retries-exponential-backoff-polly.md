---
title: Implementace opakování volání HTTP pomocí exponenciálního omezení rychlosti pomocí knihovny Polly
description: Zjistěte, jak pomocí knihovny Polly a HttpClientFactory zpracování chyb HTTP
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/10/2018
ms.openlocfilehash: 78de1440721e83459e455f5c31d10e52a1d3b1b6
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143984"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-httpclientfactory-and-polly-policies"></a>Implementace opakování volání HTTP pomocí exponenciálního omezení rychlosti zásadám HttpClientFactory a Polly

Opakování pomocí exponenciálního omezení rychlosti doporučuje využívat rozšířené knihovny .NET, jako je open source [knihovnu Polly](https://github.com/App-vNext/Polly).

Polly je knihovna .NET, která poskytuje odolnost a možnosti zpracování přechodná selhání. Tyto možnosti můžete implementovat pomocí knihovny Polly zásad například opakování, jističe, přepážka izolace, vypršení časového limitu a použití náhradní lokality. Polly cílí na .NET 4.x a .NET Standard knihovny 1.0 (který podporuje .NET Core).

Pomocí knihovny Polly společnosti s vlastním kódem s HttpClient však může být výrazně složité. V původní verzi aplikaci eShopOnContainers došlo [stavební blok ResilientHttpClient](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/Resilience/Resilience.Http/ResilientHttpClient.cs) podle Polly. Ale verzi HttpClientFactory odolné komunikaci pomocí protokolu Http stal mnohem jednodušší implementace, tak, aby stavebním blokem se přestala nabízet v aplikaci eShopOnContainers. 

Následující kroky ukazují, jak můžete pomocí protokolu Http opakování pomocí knihovny Polly integrovaná HttpClientFactory, což je vysvětleno v předchozí části.

**Referenční dokumentace technologie ASP.NET Core 2.1 balíčky**

Váš projekt musí být pomocí ASP.NET Core 2.1 balíčků z NuGet. Je obvykle třeba `AspNetCore` Microsoft.aspnetcore.all a balíček rozšíření `Microsoft.Extensions.Http.Polly`.

**Konfigurace klienta díky zásadám opakování pro Polly, při spuštění**

Jak je znázorněno v předchozích částech, budete muset definovat pojmenované nebo typu klienta Konfigurace HttpClient ve své metodě standardní Startup.ConfigureServices(...), ale teď přidejte určení zásad pro opakované pokusy Http pomocí exponenciálního omezení rychlosti, jako přírůstkové kódu níže:

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

**AddPolicyHandler()** metoda je co přidá zásady, které `HttpClient` objekty, které použijete. V tomto případě to je přidání zásad Polly pro opakování Http pomocí exponenciálního omezení rychlosti.

Abyste měli přístup založený na modulárnější, lze v samostatné metodě v rámci metody ConfigureServices() jako následující kód definovat zásady opakování Http.

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2,
                                                                    retryAttempt)));
}
```

Pomocí knihovny Polly můžete definovat zásady opakování s počtem opakovaných pokusů, konfigurace exponenciálního omezení rychlosti a akce, jež mají provést, když dojde k výjimce protokolu HTTP, jako je například protokolování chyba. V tomto případě zásad je nakonfigurovaná vyzkoušet šestkrát s exponenciální opakování, které začínají na 2 sekundy. 

proto pokusí šestkrát a počet sekund mezi opakováními bude exponenciální, od dvou sekund.

### <a name="adding-a-jitter-strategy-to-the-retry-policy"></a>Přidání zpoždění strategie zásad opakování

Pravidelné zásady opakování můžou mít vliv na váš systém v případech, vysoká souběžnosti a škálovatelnosti a v části vysokou kolize. K překonání špičky podobné opakované pokusy pocházejí z mnoha klientů v případě částečné výpadky, dobrým řešením je přidat strategii kolísání algoritmus/zásad opakování. Přidání náhodnost exponenciálního omezení rychlosti tím lze vylepšit celkový výkon systému začátku do konce. To šíří provozní špičky případných problémech. Při použití standardní zásady Polly kód pro implementaci zpoždění může vypadat jako v následujícím příkladu:

```csharp
Random jitterer = new Random(); 
Policy
  .Handle<HttpResponseException>() // etc
  .WaitAndRetry(5,    // exponential back-off plus some jitter
      retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))  
                    + TimeSpan.FromMilliseconds(jitterer.Next(0, 100)) 
  );
```

## <a name="additional-resources"></a>Další zdroje

-   **Model opakování**
    [*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)

-   **Polly a HttpClientFactory**
    [*https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory*](https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory)

-   **Polly (.NET odolnosti a zpracování chyb přechodná knihovny)**

    [*https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)

-   **Marc Brooker. Zpoždění: Provedení akce lépe s náhodnost**

    [*https://brooker.co.za/blog/2015/03/21/backoff.html*](https://brooker.co.za/blog/2015/03/21/backoff.html)

>[!div class="step-by-step"]
>[Předchozí](explore-custom-http-call-retries-exponential-backoff.md)
>[další](implement-circuit-breaker-pattern.md)