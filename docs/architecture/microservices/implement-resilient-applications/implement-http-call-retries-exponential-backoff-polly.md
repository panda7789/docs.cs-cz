---
title: Implementace opakovaných volání HTTP s exponenciálním zpomalováním s knihovnou Polly
description: Zjistěte, jak zpracovat chyby PROTOKOLU HTTP pomocí Polly a IHttpClientFactory.
ms.date: 03/03/2020
ms.openlocfilehash: 49396dd545a05699278254474c77acf1483e0e0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846793"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-ihttpclientfactory-and-polly-policies"></a>Implementace opakovaných pokusů o volání HTTP s exponenciálním vypnutím pomocí zásad IHttpClientFactory a Polly

Doporučeným přístupem pro opakované pokusy s exponenciálním podvržením je využít pokročilejší knihovny .NET, jako je open source [knihovna Polly](https://github.com/App-vNext/Polly).

Polly je knihovna .NET, která poskytuje odolnost a funkce zpracování přechodných chyb. Tyto možnosti můžete implementovat použitím polly zásad, jako je opakování, jistič, izolace přepážky, časový čas a záložní. Polly cíle .NET Framework 4.x a .NET Standard 1.0, 1.1 a 2.0 (který podporuje .NET Core).

Následující kroky ukazují, jak můžete použít http opakování `IHttpClientFactory`s Polly integrované do , což je vysvětleno v předchozí části.

**Odkaz na ASP.NET balíčky Core 3.1**

`IHttpClientFactory`je k dispozici od .NET Core 2.1 však doporučujeme použít nejnovější ASP.NET balíčky Core 3.1 z NuGet ve vašem projektu. Obvykle je také nutné odkazovat `Microsoft.Extensions.Http.Polly`na balíček rozšíření .

**Konfigurace klienta pomocí pollyiny zásady opakování při spuštění**

Jak je znázorněno v předchozích částech, je třeba definovat konfiguraci httpklienta s názvem nebo typem klienta ve standardní metodě Startup.ConfigureServices(...), ale nyní přidáte přírůstkový kód určující zásadu pro opakování protokolu Http s exponenciálním vypnutím jako Níže:

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

**Metoda AddPolicyHandler()** je to, `HttpClient` co přidává zásady k objektům, které budete používat. V tomto případě je přidání Polly zásady pro http opakování s exponenciální backoff.

Chcete-li mít více modulární přístup, http opakování zásady lze `Startup.cs` definovat v samostatné metodě v rámci souboru, jak je znázorněno v následujícím kódu:

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

S Polly, můžete definovat zásady Opakování s počtem opakování, exponenciální backoff konfigurace a akce, které mají být přijata, když je výjimka HTTP, jako je například protokolování chyby. V tomto případě je zásada nakonfigurována tak, aby se pokusila šestkrát s exponenciálním opakováním, počínaje dvěma sekundami.

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a>Přidání strategie nervozity do zásady opakování

Pravidelné zásady opakování může ovlivnit váš systém v případech vysoké souběžnosti a škálovatelnosti a pod vysokou kolizí. Chcete-li překonat špičky podobných opakování pocházejících z mnoha klientů v případě částečných výpadků, dobrým řešením je přidat strategii chvění do algoritmu nebo zásady opakování. To může zlepšit celkový výkon systému end-to-end přidáním náhodnost exponenciální backoff. To se šíří hroty, když vzniknou problémy. Princip je ilustrován následujícím příkladem:

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

Polly poskytuje algoritmy nervozity připravené pro výrobu prostřednictvím webových stránek projektu.

## <a name="additional-resources"></a>Další zdroje

- **Vzorek opakování**  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- **Polly a IHttpClientFactory**  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- **Polly (knihovna odolnosti a zpracování přechodných chyb)**  
  <https://github.com/App-vNext/Polly>

- **Polly: Opakování s chvěním**  
  <https://github.com/App-vNext/Polly/wiki/Retry-with-jitter>

- **Marca Brookera. Nervozita: Dělat věci lépe s náhodností**  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
>[Předchozí](use-httpclientfactory-to-implement-resilient-http-requests.md)
>[další](implement-circuit-breaker-pattern.md)
