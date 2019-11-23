---
title: Implementace opakovaných volání HTTP s exponenciálním zpomalováním s knihovnou Polly
description: Naučte se zpracovávat chyby HTTP pomocí Polly a HttpClientFactory.
ms.date: 01/07/2019
ms.openlocfilehash: 551cd1230c565b30c81090c984747e726680b9ed
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73089960"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-httpclientfactory-and-polly-policies"></a>Implementace opakovaných pokusů volání HTTP pomocí exponenciálního omezení rychlostiu se zásadami HttpClientFactory a Polly

Doporučený postup pro opakování s exponenciálním omezení rychlosti je využít výhod pokročilejších knihoven .NET, jako je open source [Knihovna Polly](https://github.com/App-vNext/Polly).

Polly je knihovna .NET, která poskytuje funkce odolnosti a přechodných chyb. Tyto možnosti můžete implementovat pomocí zásad Polly, jako je opakování, přerušení okruhů, izolace přepážky, časový limit a Fallback. Polly cíle .NET Framework 4. x a .NET Standard 1,0, 1,1 a 2,0 (což podporuje .NET Core).

Nicméně psaní vlastního kódu pro použití knihovny Polly s HttpClient může být výrazně složité. V původní verzi eShopOnContainers byly [ResilientHttpClient stavební bloky](https://github.com/dotnet-architecture/eShopOnContainers/commit/0c317d56f3c8937f6823cf1b45f5683397274815#diff-e6532e623eb606a0f8568663403e3a10) založené na Polly. Ale u vydání [HttpClientFactory](use-httpclientfactory-to-implement-resilient-http-requests.md)se implementace odolné komunikace http s Polly stala mnohem jednodušší, takže sestavení-Block bylo od eShopOnContainersu zastaralá.

Následující kroky ukazují, jak můžete použít opakování protokolu HTTP s integrovaným Polly do HttpClientFactory, který je vysvětlen v předchozí části.

**Odkazování na balíčky ASP.NET Core 2,2**

`HttpClientFactory` je k dispozici od .NET Core 2,1. Doporučujeme však použít nejnovější balíčky ASP.NET Core 2,2 z NuGet v projektu. Obvykle potřebujete `AspNetCore` Metapackage a balíček rozšíření `Microsoft.Extensions.Http.Polly`.

**Konfigurace klienta pomocí zásad opakování Polly při spuštění**

Jak je znázorněno v předchozích částech, je třeba v rámci standardní metody Startup. ConfigureServices (...) definovat pojmenovanou konfiguraci HttpClient nebo napsaného klienta, ale nyní přidáte přírůstkový kód, který určuje zásadu pro opakované pokusy protokolu HTTP s exponenciálním omezení rychlosti, jako psán

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

Metoda **AddPolicyHandler ()** slouží k přidání zásad do objektů `HttpClient`, které budete používat. V takovém případě přidáváme zásady Polly pro opakování HTTP pomocí exponenciálního omezení rychlosti.

Chcete-li mít obecnější přístup, zásady opakování protokolu HTTP lze definovat v samostatné metodě v souboru `Startup.cs`, jak je znázorněno v následujícím kódu:

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

Pomocí Polly můžete definovat zásady opakování s počtem opakování, exponenciální konfigurací omezení rychlosti a akcemi, které se mají provést, pokud dojde k výjimce HTTP, jako je například protokolování chyby. V takovém případě je zásada nakonfigurovaná tak, aby vyzkoušela šest časů s exponenciálním opakováním, od dvou sekund.

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a>Přidání strategie kolísání do zásady opakování

Pravidelná zásada opakování může mít vliv na váš systém v případech vysoké souběžnosti a škálovatelnosti a vysokého sporu. Chcete-li překonat špičky podobných pokusů přicházejících z mnoha klientů v případě částečných výpadků, dobrým řešením je přidat strategii kolísání do algoritmu opakování nebo zásady. To může zvýšit celkový výkon kompletního systému přidáním náhodnosti do exponenciálního omezení rychlostiu. Tím se rozšíří špičky, když dojde k problémům. Princip je znázorněn v následujícím příkladu:

```csharp
Random jitterer = new Random();
var retryWithJitterPolicy = HttpPolicyExtensions
    .HandleTransientHttpError()
    .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
    .WaitAndRetryAsync(6,    // exponential back-off plus some jitter
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))  
                      + TimeSpan.FromMilliseconds(jitterer.Next(0, 100))
    );
```

Polly poskytuje algoritmy chvění připravené k výrobě prostřednictvím webu projektu.

## <a name="additional-resources"></a>Další materiály a zdroje informací

- **Vzor opakování**  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- **Polly a HttpClientFactory**  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- **Polly (odolnost proti chybám .NET a knihovna pro zpracování s přechodnými chybami)**  
  <https://github.com/App-vNext/Polly>

- **Polly: opakovat se kolísáním**  
  <https://github.com/App-vNext/Polly/wiki/Retry-with-jitter>

- **Brooker ohraničení Kolísání: lepší práce díky náhodnosti**  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
>[Předchozí](explore-custom-http-call-retries-exponential-backoff.md)
>[Další](implement-circuit-breaker-pattern.md)
