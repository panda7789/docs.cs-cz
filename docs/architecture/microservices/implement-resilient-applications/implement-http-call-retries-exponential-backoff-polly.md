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
# <a name="implement-http-call-retries-with-exponential-backoff-with-httpclientfactory-and-polly-policies"></a><span data-ttu-id="b20f8-103">Implementace opakovaných pokusů volání HTTP pomocí exponenciálního omezení rychlostiu se zásadami HttpClientFactory a Polly</span><span class="sxs-lookup"><span data-stu-id="b20f8-103">Implement HTTP call retries with exponential backoff with HttpClientFactory and Polly policies</span></span>

<span data-ttu-id="b20f8-104">Doporučený postup pro opakování s exponenciálním omezení rychlosti je využít výhod pokročilejších knihoven .NET, jako je open source [Knihovna Polly](https://github.com/App-vNext/Polly).</span><span class="sxs-lookup"><span data-stu-id="b20f8-104">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open-source [Polly library](https://github.com/App-vNext/Polly).</span></span>

<span data-ttu-id="b20f8-105">Polly je knihovna .NET, která poskytuje funkce odolnosti a přechodných chyb.</span><span class="sxs-lookup"><span data-stu-id="b20f8-105">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="b20f8-106">Tyto možnosti můžete implementovat pomocí zásad Polly, jako je opakování, přerušení okruhů, izolace přepážky, časový limit a Fallback.</span><span class="sxs-lookup"><span data-stu-id="b20f8-106">You can implement those capabilities by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="b20f8-107">Polly cílí na rozhraní .NET 4. x a knihovnu .NET Standard 1,0 (která podporuje .NET Core).</span><span class="sxs-lookup"><span data-stu-id="b20f8-107">Polly targets .NET 4.x and the .NET Standard Library 1.0 (which supports .NET Core).</span></span>

<span data-ttu-id="b20f8-108">Nicméně použití knihovny Polly s vlastním kódem s HttpClient může být výrazně složité.</span><span class="sxs-lookup"><span data-stu-id="b20f8-108">However, using Polly’s library with your own custom code with HttpClient can be significantly complex.</span></span> <span data-ttu-id="b20f8-109">V původní verzi eShopOnContainers byly [ResilientHttpClient stavební bloky](https://github.com/dotnet-architecture/eShopOnContainers/commit/0c317d56f3c8937f6823cf1b45f5683397274815#diff-e6532e623eb606a0f8568663403e3a10) založené na Polly.</span><span class="sxs-lookup"><span data-stu-id="b20f8-109">In the original version of eShopOnContainers, there was a [ResilientHttpClient building-block](https://github.com/dotnet-architecture/eShopOnContainers/commit/0c317d56f3c8937f6823cf1b45f5683397274815#diff-e6532e623eb606a0f8568663403e3a10) based on Polly.</span></span> <span data-ttu-id="b20f8-110">Ale s vydáním [HttpClientFactory](use-httpclientfactory-to-implement-resilient-http-requests.md)se odolnost proti chybám protokolu HTTP mnohem zjednodušila, takže sestavení-Block bylo z eShopOnContainers zastaralé.</span><span class="sxs-lookup"><span data-stu-id="b20f8-110">But with the release of [HttpClientFactory](use-httpclientfactory-to-implement-resilient-http-requests.md), resilient HTTP communication has become much simpler to implement, so that building-block was deprecated from eShopOnContainers.</span></span> 

<span data-ttu-id="b20f8-111">Následující kroky ukazují, jak můžete použít opakování protokolu HTTP s integrovaným Polly do HttpClientFactory, který je vysvětlen v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="b20f8-111">The following steps show how you can use Http retries with Polly integrated into HttpClientFactory, which is explained in the previous section.</span></span>

<span data-ttu-id="b20f8-112">**Odkazování na balíčky ASP.NET Core 2,2**</span><span class="sxs-lookup"><span data-stu-id="b20f8-112">**Reference the ASP.NET Core 2.2 packages**</span></span>

<span data-ttu-id="b20f8-113">`HttpClientFactory`je k dispozici od .NET Core 2,1, ale doporučujeme použít nejnovější balíčky ASP.NET Core 2,2 ze sady NuGet ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="b20f8-113">`HttpClientFactory` is available since .NET Core 2.1 however we recommend you to use the latest ASP.NET Core 2.2 packages from NuGet in your project.</span></span> <span data-ttu-id="b20f8-114">Obvykle potřebujete `AspNetCore` Metapackage a balíček `Microsoft.Extensions.Http.Polly`rozšíření.</span><span class="sxs-lookup"><span data-stu-id="b20f8-114">You typically need the `AspNetCore` metapackage, and the extension package `Microsoft.Extensions.Http.Polly`.</span></span>

<span data-ttu-id="b20f8-115">**Konfigurace klienta pomocí zásad opakování Polly při spuštění**</span><span class="sxs-lookup"><span data-stu-id="b20f8-115">**Configure a client with Polly’s Retry policy, in Startup**</span></span>

<span data-ttu-id="b20f8-116">Jak je znázorněno v předchozích částech, je třeba v rámci standardní metody Startup. ConfigureServices (...) definovat pojmenovanou konfiguraci HttpClient nebo napsaného klienta, ale nyní přidáte přírůstkový kód, který určuje zásadu pro opakované pokusy protokolu HTTP s exponenciálním omezení rychlosti, jako psán</span><span class="sxs-lookup"><span data-stu-id="b20f8-116">As shown in previous sections, you need to define a named or typed client HttpClient configuration in your standard Startup.ConfigureServices(...) method, but now, you add incremental code specifying the policy for the Http retries with exponential backoff, as below:</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

<span data-ttu-id="b20f8-117">Metoda **AddPolicyHandler ()** je to, co přidává zásady pro `HttpClient` objekty, které budete používat.</span><span class="sxs-lookup"><span data-stu-id="b20f8-117">The **AddPolicyHandler()** method is what adds policies to the `HttpClient` objects you'll use.</span></span> <span data-ttu-id="b20f8-118">V takovém případě přidáváme zásady Polly pro opakování HTTP pomocí exponenciálního omezení rychlosti.</span><span class="sxs-lookup"><span data-stu-id="b20f8-118">In this case, it's adding a Polly’s policy for Http Retries with exponential backoff.</span></span>

<span data-ttu-id="b20f8-119">Chcete-li mít více modulární přístup, je možné v rámci `Startup.cs` souboru definovat zásady opakování protokolu HTTP v samostatné metodě, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="b20f8-119">To have a more modular approach, the Http Retry Policy can be defined in a separate method within the `Startup.cs` file, as shown in the following code:</span></span>

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

<span data-ttu-id="b20f8-120">Pomocí Polly můžete definovat zásady opakování s počtem opakování, exponenciální konfigurací omezení rychlosti a akcemi, které se mají provést, pokud dojde k výjimce HTTP, jako je například protokolování chyby.</span><span class="sxs-lookup"><span data-stu-id="b20f8-120">With Polly, you can define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there's an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="b20f8-121">V takovém případě je zásada nakonfigurovaná tak, aby vyzkoušela šest časů s exponenciálním opakováním, od dvou sekund.</span><span class="sxs-lookup"><span data-stu-id="b20f8-121">In this case, the policy is configured to try six times with an exponential retry, starting at two seconds.</span></span> 

<span data-ttu-id="b20f8-122">Proto bude zkoušet šest časů a sekundy mezi jednotlivými opakováními budou exponenciální, počínaje dvou sekundami.</span><span class="sxs-lookup"><span data-stu-id="b20f8-122">so it will try six times and the seconds between each retry will be exponential, starting on two seconds.</span></span>

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a><span data-ttu-id="b20f8-123">Přidání strategie kolísání do zásady opakování</span><span class="sxs-lookup"><span data-stu-id="b20f8-123">Add a jitter strategy to the retry policy</span></span>

<span data-ttu-id="b20f8-124">Pravidelná zásada opakování může mít vliv na váš systém v případech vysoké souběžnosti a škálovatelnosti a vysokého sporu.</span><span class="sxs-lookup"><span data-stu-id="b20f8-124">A regular Retry policy can impact your system in cases of high concurrency and scalability and under high contention.</span></span> <span data-ttu-id="b20f8-125">Chcete-li překonat špičky podobných pokusů přicházejících z mnoha klientů v případě částečných výpadků, dobrým řešením je přidat strategii kolísání do algoritmu opakování nebo zásady.</span><span class="sxs-lookup"><span data-stu-id="b20f8-125">To overcome peaks of similar retries coming from many clients in case of partial outages, a good workaround is to add a jitter strategy to the retry algorithm/policy.</span></span> <span data-ttu-id="b20f8-126">To může zvýšit celkový výkon kompletního systému přidáním náhodnosti do exponenciálního omezení rychlostiu.</span><span class="sxs-lookup"><span data-stu-id="b20f8-126">This can improve the overall performance of the end-to-end system by adding randomness to the exponential backoff.</span></span> <span data-ttu-id="b20f8-127">Tím se rozšíří špičky, když dojde k problémům.</span><span class="sxs-lookup"><span data-stu-id="b20f8-127">This spreads out the spikes when issues arise.</span></span> <span data-ttu-id="b20f8-128">Při použití jednoduchých zásad Polly by kód pro implementaci kolísání mohl vypadat jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="b20f8-128">When you use a plain Polly policy, code to implement jitter could look like the following example:</span></span>

```csharp
Random jitterer = new Random(); 
Policy
  .Handle<HttpResponseException>() // etc
  .WaitAndRetry(5,    // exponential back-off plus some jitter
      retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))  
                    + TimeSpan.FromMilliseconds(jitterer.Next(0, 100)) 
  );
```

## <a name="additional-resources"></a><span data-ttu-id="b20f8-129">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="b20f8-129">Additional resources</span></span>

- <span data-ttu-id="b20f8-130">**Vzor opakování**</span><span class="sxs-lookup"><span data-stu-id="b20f8-130">**Retry pattern**</span></span>  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- <span data-ttu-id="b20f8-131">**Polly a HttpClientFactory**</span><span class="sxs-lookup"><span data-stu-id="b20f8-131">**Polly and HttpClientFactory**</span></span>  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- <span data-ttu-id="b20f8-132">**Polly (odolnost proti chybám .NET a knihovna pro zpracování s přechodnými chybami)**</span><span class="sxs-lookup"><span data-stu-id="b20f8-132">**Polly (.NET resilience and transient-fault-handling library)**</span></span>  
  <https://github.com/App-vNext/Polly>

- <span data-ttu-id="b20f8-133">**Brooker ohraničení Zpoždění Lepší zvýšení náhodnosti**</span><span class="sxs-lookup"><span data-stu-id="b20f8-133">**Marc Brooker. Jitter: Making Things Better With Randomness**</span></span>  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
><span data-ttu-id="b20f8-134">[Předchozí](explore-custom-http-call-retries-exponential-backoff.md)Další
>[](implement-circuit-breaker-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="b20f8-134">[Previous](explore-custom-http-call-retries-exponential-backoff.md)
[Next](implement-circuit-breaker-pattern.md)</span></span>
