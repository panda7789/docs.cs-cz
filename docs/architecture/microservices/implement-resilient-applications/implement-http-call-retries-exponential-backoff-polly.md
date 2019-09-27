---
title: Implementace opakovaných volání HTTP s exponenciálním zpomalováním s knihovnou Polly
description: Naučte se zpracovávat chyby HTTP pomocí Polly a HttpClientFactory.
ms.date: 01/07/2019
ms.openlocfilehash: de1dad44b1ddc7b04438fb380f240d3be33bbb83
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71331982"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-httpclientfactory-and-polly-policies"></a>Implementace opakovaných pokusů volání HTTP pomocí exponenciálního omezení rychlostiu se zásadami HttpClientFactory a Polly

Doporučený postup pro opakování s exponenciálním omezení rychlosti je využít výhod pokročilejších knihoven .NET, jako je open source [Knihovna Polly](https://github.com/App-vNext/Polly).

Polly je knihovna .NET, která poskytuje funkce odolnosti a přechodných chyb. Tyto možnosti můžete implementovat pomocí zásad Polly, jako je opakování, přerušení okruhů, izolace přepážky, časový limit a Fallback. Polly cílí na rozhraní .NET 4. x a knihovnu .NET Standard 1,0 (která podporuje .NET Core).

Nicméně použití knihovny Polly s vlastním kódem s HttpClient může být výrazně složité. V původní verzi eShopOnContainers byly [ResilientHttpClient stavební bloky](https://github.com/dotnet-architecture/eShopOnContainers/commit/0c317d56f3c8937f6823cf1b45f5683397274815#diff-e6532e623eb606a0f8568663403e3a10) založené na Polly. Ale s vydáním [HttpClientFactory](use-httpclientfactory-to-implement-resilient-http-requests.md)se odolnost proti chybám protokolu HTTP mnohem zjednodušila, takže sestavení-Block bylo z eShopOnContainers zastaralé. 

Následující kroky ukazují, jak můžete použít opakování protokolu HTTP s integrovaným Polly do HttpClientFactory, který je vysvětlen v předchozí části.

**Odkazování na balíčky ASP.NET Core 2,2**

`HttpClientFactory` je k dispozici od rozhraní .NET Core 2,1. Doporučujeme však, abyste použili nejnovější balíčky ASP.NET Core 2,2 z NuGet ve vašem projektu. Obvykle potřebujete `AspNetCore` Metapackage a balíček rozšíření `Microsoft.Extensions.Http.Polly`.

**Konfigurace klienta pomocí zásad opakování Polly při spuštění**

Jak je znázorněno v předchozích částech, je třeba v rámci standardní metody Startup. ConfigureServices (...) definovat pojmenovanou konfiguraci HttpClient nebo napsaného klienta, ale nyní přidáte přírůstkový kód, který určuje zásadu pro opakované pokusy protokolu HTTP s exponenciálním omezení rychlosti, jako psán

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

Metoda **AddPolicyHandler ()** je to, co přidává zásady do objektů `HttpClient`, které budete používat. V takovém případě přidáváme zásady Polly pro opakování HTTP pomocí exponenciálního omezení rychlosti.

Chcete-li mít obecnější přístup, zásady opakování http lze definovat v samostatné metodě v souboru `Startup.cs`, jak je znázorněno v následujícím kódu:

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

- @no__t – 0Marc Brooker. Zpoždění Lepší zvýšení náhodnosti @ no__t-0  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
>[Předchozí](explore-custom-http-call-retries-exponential-backoff.md)
>[Další](implement-circuit-breaker-pattern.md)
