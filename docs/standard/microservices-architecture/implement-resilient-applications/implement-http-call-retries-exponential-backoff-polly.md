---
title: Implementace opakování volání HTTP pomocí exponenciálního omezení rychlosti pomocí knihovny Polly
description: Zjistěte, jak pro zpracování chyb HTTP pomocí knihovny Polly a HttpClientFactory.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: 25b816cb56c30545b8d67986817f51e17b2ff770
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362753"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-httpclientfactory-and-polly-policies"></a><span data-ttu-id="dd0b0-103">Implementace opakování volání HTTP pomocí exponenciálního omezení rychlosti zásadám HttpClientFactory a Polly</span><span class="sxs-lookup"><span data-stu-id="dd0b0-103">Implement HTTP call retries with exponential backoff with HttpClientFactory and Polly policies</span></span>

<span data-ttu-id="dd0b0-104">Opakování pomocí exponenciálního omezení rychlosti doporučuje využívat rozšířené knihovny .NET, jako je open source [knihovnu Polly](https://github.com/App-vNext/Polly).</span><span class="sxs-lookup"><span data-stu-id="dd0b0-104">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open-source [Polly library](https://github.com/App-vNext/Polly).</span></span>

<span data-ttu-id="dd0b0-105">Polly je knihovna .NET, která poskytuje odolnost a možnosti zpracování přechodná selhání.</span><span class="sxs-lookup"><span data-stu-id="dd0b0-105">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="dd0b0-106">Tyto možnosti můžete implementovat pomocí knihovny Polly zásad například opakování, jističe, přepážka izolace, vypršení časového limitu a použití náhradní lokality.</span><span class="sxs-lookup"><span data-stu-id="dd0b0-106">You can implement those capabilities by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="dd0b0-107">Polly cílí na .NET 4.x a .NET Standard knihovny 1.0 (který podporuje .NET Core).</span><span class="sxs-lookup"><span data-stu-id="dd0b0-107">Polly targets .NET 4.x and the .NET Standard Library 1.0 (which supports .NET Core).</span></span>

<span data-ttu-id="dd0b0-108">Pomocí knihovny Polly společnosti s vlastním kódem s HttpClient však může být výrazně složité.</span><span class="sxs-lookup"><span data-stu-id="dd0b0-108">However, using Polly’s library with your own custom code with HttpClient can be significantly complex.</span></span> <span data-ttu-id="dd0b0-109">V původní verzi aplikaci eShopOnContainers došlo [stavební blok ResilientHttpClient](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/Resilience/Resilience.Http/ResilientHttpClient.cs) podle Polly.</span><span class="sxs-lookup"><span data-stu-id="dd0b0-109">In the original version of eShopOnContainers, there was a [ResilientHttpClient building-block](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/Resilience/Resilience.Http/ResilientHttpClient.cs) based on Polly.</span></span> <span data-ttu-id="dd0b0-110">Ale verzi HttpClientFactory odolné komunikaci pomocí protokolu Http stal mnohem jednodušší implementace, tak, aby stavebním blokem se přestala nabízet v aplikaci eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="dd0b0-110">But with the release of HttpClientFactory, resilient Http communication has become much simpler to implement, so that building-block was deprecated from eShopOnContainers.</span></span> 

<span data-ttu-id="dd0b0-111">Následující kroky ukazují, jak můžete pomocí protokolu Http opakování pomocí knihovny Polly integrovaná HttpClientFactory, což je vysvětleno v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="dd0b0-111">The following steps show how you can use Http retries with Polly integrated into HttpClientFactory, which is explained in the previous section.</span></span>

<span data-ttu-id="dd0b0-112">**Referenční dokumentace technologie ASP.NET Core 2.1 balíčky**</span><span class="sxs-lookup"><span data-stu-id="dd0b0-112">**Reference the ASP.NET Core 2.1 packages**</span></span>

<span data-ttu-id="dd0b0-113">Váš projekt musí být pomocí ASP.NET Core 2.1 balíčků z NuGet.</span><span class="sxs-lookup"><span data-stu-id="dd0b0-113">Your project has to be using the ASP.NET Core 2.1 packages from NuGet.</span></span> <span data-ttu-id="dd0b0-114">Je obvykle třeba `AspNetCore` Microsoft.aspnetcore.all a balíček rozšíření `Microsoft.Extensions.Http.Polly`.</span><span class="sxs-lookup"><span data-stu-id="dd0b0-114">You typically need the `AspNetCore` metapackage, and the extension package `Microsoft.Extensions.Http.Polly`.</span></span>

<span data-ttu-id="dd0b0-115">**Konfigurace klienta díky zásadám opakování pro Polly, při spuštění**</span><span class="sxs-lookup"><span data-stu-id="dd0b0-115">**Configure a client with Polly’s Retry policy, in Startup**</span></span>

<span data-ttu-id="dd0b0-116">Jak je znázorněno v předchozích částech, budete muset definovat pojmenované nebo typu klienta Konfigurace HttpClient ve své metodě standardní Startup.ConfigureServices(...), ale teď přidejte určení zásad pro opakované pokusy Http pomocí exponenciálního omezení rychlosti, jako přírůstkové kódu níže:</span><span class="sxs-lookup"><span data-stu-id="dd0b0-116">As shown in previous sections, you need to define a named or typed client HttpClient configuration in your standard Startup.ConfigureServices(...) method, but now, you add incremental code specifying the policy for the Http retries with exponential backoff, as below:</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

<span data-ttu-id="dd0b0-117">**AddPolicyHandler()** metoda je co přidá zásady, které `HttpClient` objekty, které použijete.</span><span class="sxs-lookup"><span data-stu-id="dd0b0-117">The **AddPolicyHandler()** method is what adds policies to the `HttpClient` objects you'll use.</span></span> <span data-ttu-id="dd0b0-118">V tomto případě to je přidání zásad Polly pro opakování Http pomocí exponenciálního omezení rychlosti.</span><span class="sxs-lookup"><span data-stu-id="dd0b0-118">In this case, it's adding a Polly’s policy for Http Retries with exponential backoff.</span></span>

<span data-ttu-id="dd0b0-119">Pokud chcete, aby modulárnější přístup, lze definovat zásady opakování Http v samostatné metodě v rámci `Startup.cs` souboru, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="dd0b0-119">To have a more modular approach, the Http Retry Policy can be defined in a separate method within the `Startup.cs` file, as shown in the following code:</span></span>

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

<span data-ttu-id="dd0b0-120">Pomocí knihovny Polly můžete definovat zásady opakování s počtem opakovaných pokusů, konfigurace exponenciálního omezení rychlosti a akce, jež mají provést, když dojde k výjimce protokolu HTTP, jako je například protokolování chyba.</span><span class="sxs-lookup"><span data-stu-id="dd0b0-120">With Polly, you can define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there's an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="dd0b0-121">V tomto případě zásad je nakonfigurovaná vyzkoušet šestkrát s exponenciální opakování, které začínají na 2 sekundy.</span><span class="sxs-lookup"><span data-stu-id="dd0b0-121">In this case, the policy is configured to try six times with an exponential retry, starting at two seconds.</span></span> 

<span data-ttu-id="dd0b0-122">proto pokusí šestkrát a počet sekund mezi opakováními bude exponenciální, od dvou sekund.</span><span class="sxs-lookup"><span data-stu-id="dd0b0-122">so it will try six times and the seconds between each retry will be exponential, starting on two seconds.</span></span>

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a><span data-ttu-id="dd0b0-123">Přidání zpoždění strategie zásad opakování</span><span class="sxs-lookup"><span data-stu-id="dd0b0-123">Add a jitter strategy to the retry policy</span></span>

<span data-ttu-id="dd0b0-124">Pravidelné zásady opakování můžou mít vliv na váš systém v případech, vysoká souběžnosti a škálovatelnosti a v části vysokou kolize.</span><span class="sxs-lookup"><span data-stu-id="dd0b0-124">A regular Retry policy can impact your system in cases of high concurrency and scalability and under high contention.</span></span> <span data-ttu-id="dd0b0-125">K překonání špičky podobné opakované pokusy pocházejí z mnoha klientů v případě částečné výpadky, dobrým řešením je přidat strategii kolísání algoritmus/zásad opakování.</span><span class="sxs-lookup"><span data-stu-id="dd0b0-125">To overcome peaks of similar retries coming from many clients in case of partial outages, a good workaround is to add a jitter strategy to the retry algorithm/policy.</span></span> <span data-ttu-id="dd0b0-126">Přidání náhodnost exponenciálního omezení rychlosti tím lze vylepšit celkový výkon systému začátku do konce.</span><span class="sxs-lookup"><span data-stu-id="dd0b0-126">This can improve the overall performance of the end-to-end system by adding randomness to the exponential backoff.</span></span> <span data-ttu-id="dd0b0-127">To šíří provozní špičky případných problémech.</span><span class="sxs-lookup"><span data-stu-id="dd0b0-127">This spreads out the spikes when issues arise.</span></span> <span data-ttu-id="dd0b0-128">Při použití standardní zásady Polly kód pro implementaci zpoždění může vypadat jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="dd0b0-128">When you use a plain Polly policy, code to implement jitter could look like the following example:</span></span>

```csharp
Random jitterer = new Random(); 
Policy
  .Handle<HttpResponseException>() // etc
  .WaitAndRetry(5,    // exponential back-off plus some jitter
      retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))  
                    + TimeSpan.FromMilliseconds(jitterer.Next(0, 100)) 
  );
```

## <a name="additional-resources"></a><span data-ttu-id="dd0b0-129">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="dd0b0-129">Additional resources</span></span>

- <span data-ttu-id="dd0b0-130">**Model opakování**\\</span><span class="sxs-lookup"><span data-stu-id="dd0b0-130">**Retry pattern**\\</span></span>
  [*https://docs.microsoft.com/azure/architecture/patterns/retry*](/azure/architecture/patterns/retry)

- <span data-ttu-id="dd0b0-131">**Polly a HttpClientFactory**\\</span><span class="sxs-lookup"><span data-stu-id="dd0b0-131">**Polly and HttpClientFactory**\\</span></span>
  [*https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory*](https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory)

- <span data-ttu-id="dd0b0-132">**Polly (.NET odolnosti a zpracování chyb přechodná knihovny)**\\</span><span class="sxs-lookup"><span data-stu-id="dd0b0-132">**Polly (.NET resilience and transient-fault-handling library)**\\</span></span>
  [*https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)

- <span data-ttu-id="dd0b0-133">**Marc Brooker. Zpoždění: Provedení akce lépe s náhodnost**\\</span><span class="sxs-lookup"><span data-stu-id="dd0b0-133">**Marc Brooker. Jitter: Making Things Better With Randomness**\\</span></span>
  [*https://brooker.co.za/blog/2015/03/21/backoff.html*](https://brooker.co.za/blog/2015/03/21/backoff.html)

>[!div class="step-by-step"]
><span data-ttu-id="dd0b0-134">[Předchozí](explore-custom-http-call-retries-exponential-backoff.md)
>[další](implement-circuit-breaker-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="dd0b0-134">[Previous](explore-custom-http-call-retries-exponential-backoff.md)
[Next](implement-circuit-breaker-pattern.md)</span></span>