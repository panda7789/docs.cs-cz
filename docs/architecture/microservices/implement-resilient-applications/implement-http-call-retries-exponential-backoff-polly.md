---
title: Implementace opakovaných volání HTTP s exponenciálním zpomalováním s knihovnou Polly
description: Naučte se zpracovávat chyby HTTP pomocí Polly a HttpClientFactory.
ms.date: 01/07/2019
ms.openlocfilehash: aa500b5525eff9f0bbf91bf98de8945f7c84704f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296072"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-httpclientfactory-and-polly-policies"></a>Implementace opakovaných pokusů volání HTTP pomocí exponenciálního omezení rychlostiu se zásadami HttpClientFactory a Polly

Doporučený postup pro opakování s exponenciálním omezení rychlosti je využít výhod pokročilejších knihoven .NET, jako je open source [Knihovna Polly](https://github.com/App-vNext/Polly).

Polly je knihovna .NET, která poskytuje funkce odolnosti a přechodných chyb. Tyto možnosti můžete implementovat pomocí zásad Polly, jako je opakování, přerušení okruhů, izolace přepážky, časový limit a Fallback. Polly cílí na rozhraní .NET 4. x a knihovnu .NET Standard 1,0 (která podporuje .NET Core).

Nicméně použití knihovny Polly s vlastním kódem s HttpClient může být výrazně složité. V původní verzi eShopOnContainers byly [ResilientHttpClient stavební bloky](https://github.com/dotnet-architecture/eShopOnContainers/commit/0c317d56f3c8937f6823cf1b45f5683397274815#diff-e6532e623eb606a0f8568663403e3a10) založené na Polly. Ale s vydáním [HttpClientFactory](use-httpclientfactory-to-implement-resilient-http-requests.md)se odolnost proti chybám protokolu HTTP mnohem zjednodušila, takže sestavení-Block bylo z eShopOnContainers zastaralé. 

Následující kroky ukazují, jak můžete použít opakování protokolu HTTP s integrovaným Polly do HttpClientFactory, který je vysvětlen v předchozí části.

**Odkazování na balíčky ASP.NET Core 2,2**

`HttpClientFactory`je k dispozici od .NET Core 2,1, ale doporučujeme použít nejnovější balíčky ASP.NET Core 2,2 ze sady NuGet ve vašem projektu. Obvykle potřebujete `AspNetCore` Metapackage a balíček `Microsoft.Extensions.Http.Polly`rozšíření.

**Konfigurace klienta pomocí zásad opakování Polly při spuštění**

Jak je znázorněno v předchozích částech, je třeba v rámci standardní metody Startup. ConfigureServices (...) definovat pojmenovanou konfiguraci HttpClient nebo napsaného klienta, ale nyní přidáte přírůstkový kód, který určuje zásadu pro opakované pokusy protokolu HTTP s exponenciálním omezení rychlosti, jako psán

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

Metoda **AddPolicyHandler ()** je to, co přidává zásady pro `HttpClient` objekty, které budete používat. V takovém případě přidáváme zásady Polly pro opakování HTTP pomocí exponenciálního omezení rychlosti.

Chcete-li mít více modulární přístup, je možné v rámci `Startup.cs` souboru definovat zásady opakování protokolu HTTP v samostatné metodě, jak je znázorněno v následujícím kódu:

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

Proto bude zkoušet šest časů a sekundy mezi jednotlivými opakováními budou exponenciální, počínaje dvou sekundami.

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a>Přidání strategie kolísání do zásady opakování

Pravidelná zásada opakování může mít vliv na váš systém v případech vysoké souběžnosti a škálovatelnosti a vysokého sporu. Chcete-li překonat špičky podobných pokusů přicházejících z mnoha klientů v případě částečných výpadků, dobrým řešením je přidat strategii kolísání do algoritmu opakování nebo zásady. To může zvýšit celkový výkon kompletního systému přidáním náhodnosti do exponenciálního omezení rychlostiu. Tím se rozšíří špičky, když dojde k problémům. Při použití jednoduchých zásad Polly by kód pro implementaci kolísání mohl vypadat jako v následujícím příkladu:

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

- **Vzor opakování**  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- **Polly a HttpClientFactory**  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- **Polly (odolnost proti chybám .NET a knihovna pro zpracování s přechodnými chybami)**  
  <https://github.com/App-vNext/Polly>

- **Brooker ohraničení Zpoždění Lepší zvýšení náhodnosti**  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
>[Předchozí](explore-custom-http-call-retries-exponential-backoff.md)Další
>[](implement-circuit-breaker-pattern.md)
