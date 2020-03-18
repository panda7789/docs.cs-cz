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
# <a name="implement-http-call-retries-with-exponential-backoff-with-ihttpclientfactory-and-polly-policies"></a><span data-ttu-id="ca1bf-103">Implementace opakovaných pokusů o volání HTTP s exponenciálním vypnutím pomocí zásad IHttpClientFactory a Polly</span><span class="sxs-lookup"><span data-stu-id="ca1bf-103">Implement HTTP call retries with exponential backoff with IHttpClientFactory and Polly policies</span></span>

<span data-ttu-id="ca1bf-104">Doporučeným přístupem pro opakované pokusy s exponenciálním podvržením je využít pokročilejší knihovny .NET, jako je open source [knihovna Polly](https://github.com/App-vNext/Polly).</span><span class="sxs-lookup"><span data-stu-id="ca1bf-104">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open-source [Polly library](https://github.com/App-vNext/Polly).</span></span>

<span data-ttu-id="ca1bf-105">Polly je knihovna .NET, která poskytuje odolnost a funkce zpracování přechodných chyb.</span><span class="sxs-lookup"><span data-stu-id="ca1bf-105">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="ca1bf-106">Tyto možnosti můžete implementovat použitím polly zásad, jako je opakování, jistič, izolace přepážky, časový čas a záložní.</span><span class="sxs-lookup"><span data-stu-id="ca1bf-106">You can implement those capabilities by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="ca1bf-107">Polly cíle .NET Framework 4.x a .NET Standard 1.0, 1.1 a 2.0 (který podporuje .NET Core).</span><span class="sxs-lookup"><span data-stu-id="ca1bf-107">Polly targets .NET Framework 4.x and .NET Standard 1.0, 1.1, and 2.0 (which supports .NET Core).</span></span>

<span data-ttu-id="ca1bf-108">Následující kroky ukazují, jak můžete použít http opakování `IHttpClientFactory`s Polly integrované do , což je vysvětleno v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="ca1bf-108">The following steps show how you can use Http retries with Polly integrated into `IHttpClientFactory`, which is explained in the previous section.</span></span>

<span data-ttu-id="ca1bf-109">**Odkaz na ASP.NET balíčky Core 3.1**</span><span class="sxs-lookup"><span data-stu-id="ca1bf-109">**Reference the ASP.NET Core 3.1 packages**</span></span>

<span data-ttu-id="ca1bf-110">`IHttpClientFactory`je k dispozici od .NET Core 2.1 však doporučujeme použít nejnovější ASP.NET balíčky Core 3.1 z NuGet ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="ca1bf-110">`IHttpClientFactory` is available since .NET Core 2.1 however we recommend you to use the latest ASP.NET Core 3.1 packages from NuGet in your project.</span></span> <span data-ttu-id="ca1bf-111">Obvykle je také nutné odkazovat `Microsoft.Extensions.Http.Polly`na balíček rozšíření .</span><span class="sxs-lookup"><span data-stu-id="ca1bf-111">You typically also need to reference the extension package `Microsoft.Extensions.Http.Polly`.</span></span>

<span data-ttu-id="ca1bf-112">**Konfigurace klienta pomocí pollyiny zásady opakování při spuštění**</span><span class="sxs-lookup"><span data-stu-id="ca1bf-112">**Configure a client with Polly's Retry policy, in Startup**</span></span>

<span data-ttu-id="ca1bf-113">Jak je znázorněno v předchozích částech, je třeba definovat konfiguraci httpklienta s názvem nebo typem klienta ve standardní metodě Startup.ConfigureServices(...), ale nyní přidáte přírůstkový kód určující zásadu pro opakování protokolu Http s exponenciálním vypnutím jako Níže:</span><span class="sxs-lookup"><span data-stu-id="ca1bf-113">As shown in previous sections, you need to define a named or typed client HttpClient configuration in your standard Startup.ConfigureServices(...) method, but now, you add incremental code specifying the policy for the Http retries with exponential backoff, as below:</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

<span data-ttu-id="ca1bf-114">**Metoda AddPolicyHandler()** je to, `HttpClient` co přidává zásady k objektům, které budete používat.</span><span class="sxs-lookup"><span data-stu-id="ca1bf-114">The **AddPolicyHandler()** method is what adds policies to the `HttpClient` objects you'll use.</span></span> <span data-ttu-id="ca1bf-115">V tomto případě je přidání Polly zásady pro http opakování s exponenciální backoff.</span><span class="sxs-lookup"><span data-stu-id="ca1bf-115">In this case, it's adding a Polly's policy for Http Retries with exponential backoff.</span></span>

<span data-ttu-id="ca1bf-116">Chcete-li mít více modulární přístup, http opakování zásady lze `Startup.cs` definovat v samostatné metodě v rámci souboru, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="ca1bf-116">To have a more modular approach, the Http Retry Policy can be defined in a separate method within the `Startup.cs` file, as shown in the following code:</span></span>

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

<span data-ttu-id="ca1bf-117">S Polly, můžete definovat zásady Opakování s počtem opakování, exponenciální backoff konfigurace a akce, které mají být přijata, když je výjimka HTTP, jako je například protokolování chyby.</span><span class="sxs-lookup"><span data-stu-id="ca1bf-117">With Polly, you can define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there's an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="ca1bf-118">V tomto případě je zásada nakonfigurována tak, aby se pokusila šestkrát s exponenciálním opakováním, počínaje dvěma sekundami.</span><span class="sxs-lookup"><span data-stu-id="ca1bf-118">In this case, the policy is configured to try six times with an exponential retry, starting at two seconds.</span></span>

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a><span data-ttu-id="ca1bf-119">Přidání strategie nervozity do zásady opakování</span><span class="sxs-lookup"><span data-stu-id="ca1bf-119">Add a jitter strategy to the retry policy</span></span>

<span data-ttu-id="ca1bf-120">Pravidelné zásady opakování může ovlivnit váš systém v případech vysoké souběžnosti a škálovatelnosti a pod vysokou kolizí.</span><span class="sxs-lookup"><span data-stu-id="ca1bf-120">A regular Retry policy can impact your system in cases of high concurrency and scalability and under high contention.</span></span> <span data-ttu-id="ca1bf-121">Chcete-li překonat špičky podobných opakování pocházejících z mnoha klientů v případě částečných výpadků, dobrým řešením je přidat strategii chvění do algoritmu nebo zásady opakování.</span><span class="sxs-lookup"><span data-stu-id="ca1bf-121">To overcome peaks of similar retries coming from many clients in case of partial outages, a good workaround is to add a jitter strategy to the retry algorithm/policy.</span></span> <span data-ttu-id="ca1bf-122">To může zlepšit celkový výkon systému end-to-end přidáním náhodnost exponenciální backoff.</span><span class="sxs-lookup"><span data-stu-id="ca1bf-122">This can improve the overall performance of the end-to-end system by adding randomness to the exponential backoff.</span></span> <span data-ttu-id="ca1bf-123">To se šíří hroty, když vzniknou problémy.</span><span class="sxs-lookup"><span data-stu-id="ca1bf-123">This spreads out the spikes when issues arise.</span></span> <span data-ttu-id="ca1bf-124">Princip je ilustrován následujícím příkladem:</span><span class="sxs-lookup"><span data-stu-id="ca1bf-124">The principle is illustrated by the following example:</span></span>

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

<span data-ttu-id="ca1bf-125">Polly poskytuje algoritmy nervozity připravené pro výrobu prostřednictvím webových stránek projektu.</span><span class="sxs-lookup"><span data-stu-id="ca1bf-125">Polly provides production-ready jitter algorithms via the project website.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="ca1bf-126">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="ca1bf-126">Additional resources</span></span>

- <span data-ttu-id="ca1bf-127">**Vzorek opakování**</span><span class="sxs-lookup"><span data-stu-id="ca1bf-127">**Retry pattern**</span></span>  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- <span data-ttu-id="ca1bf-128">**Polly a IHttpClientFactory**</span><span class="sxs-lookup"><span data-stu-id="ca1bf-128">**Polly and IHttpClientFactory**</span></span>  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- <span data-ttu-id="ca1bf-129">**Polly (knihovna odolnosti a zpracování přechodných chyb)**</span><span class="sxs-lookup"><span data-stu-id="ca1bf-129">**Polly (.NET resilience and transient-fault-handling library)**</span></span>  
  <https://github.com/App-vNext/Polly>

- <span data-ttu-id="ca1bf-130">**Polly: Opakování s chvěním**</span><span class="sxs-lookup"><span data-stu-id="ca1bf-130">**Polly: Retry with Jitter**</span></span>  
  <https://github.com/App-vNext/Polly/wiki/Retry-with-jitter>

- <span data-ttu-id="ca1bf-131">**Marca Brookera. Nervozita: Dělat věci lépe s náhodností**</span><span class="sxs-lookup"><span data-stu-id="ca1bf-131">**Marc Brooker. Jitter: Making Things Better With Randomness**</span></span>  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
><span data-ttu-id="ca1bf-132">[Předchozí](use-httpclientfactory-to-implement-resilient-http-requests.md)
>[další](implement-circuit-breaker-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="ca1bf-132">[Previous](use-httpclientfactory-to-implement-resilient-http-requests.md)
[Next](implement-circuit-breaker-pattern.md)</span></span>
