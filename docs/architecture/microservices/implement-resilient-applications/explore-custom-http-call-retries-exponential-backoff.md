---
title: Prozkoumejte opakované pokusy o vlastní volání HTTP pomocí exponenciálního omezení rychlostiu
description: Přečtěte si, jak můžete implementovat opakované pokusy o volání HTTP pomocí exponenciálního omezení rychlostiu, od nuly až po zpracování možných scénářů selhání protokolu HTTP.
ms.date: 10/16/2018
ms.openlocfilehash: 2b40b73a014faa87d4eb42192c72b5a9b6c8d4fa
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296121"
---
# <a name="explore-custom-http-call-retries-with-exponential-backoff"></a><span data-ttu-id="58d6b-103">Prozkoumejte opakované pokusy o vlastní volání HTTP pomocí exponenciálního omezení rychlostiu</span><span class="sxs-lookup"><span data-stu-id="58d6b-103">Explore custom HTTP call retries with exponential backoff</span></span>

<span data-ttu-id="58d6b-104">Chcete-li vytvořit odolné mikroslužby, je třeba zvládnout možné scénáře selhání protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="58d6b-104">To create resilient microservices, you need to handle possible HTTP failure scenarios.</span></span> <span data-ttu-id="58d6b-105">Jedním ze způsobů, jak tyto chyby zpracovat, ale nedoporučujeme, je vytvořit vlastní implementaci opakovaných pokusů pomocí exponenciálního omezení rychlostiu.</span><span class="sxs-lookup"><span data-stu-id="58d6b-105">One way of handling those failures, although not recommended, is to create your own implementation of retries with exponential backoff.</span></span>

<span data-ttu-id="58d6b-106">**Důležitá Poznámka:** V této části se dozvíte, jak můžete vytvořit vlastní kód pro implementaci opakovaných pokusů o volání HTTP.</span><span class="sxs-lookup"><span data-stu-id="58d6b-106">**Important note:** This section shows you how you could create your own custom code to implement HTTP call retries.</span></span> <span data-ttu-id="58d6b-107">Nedoporučuje se ale dělat sami sebe, ale k použití výkonnějších a spolehlivých a současně jednoduššího používání mechanismů, jako jsou `HttpClientFactory` s Polly, k dispozici od .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="58d6b-107">However, it isn't recommended to do it on your own but to use more powerful and reliable while simpler to use mechanisms, such as `HttpClientFactory` with Polly, available since .NET Core 2.1.</span></span> <span data-ttu-id="58d6b-108">Tyto doporučené přístupy jsou vysvětleny v dalších částech.</span><span class="sxs-lookup"><span data-stu-id="58d6b-108">Those recommended approaches are explained in the next sections.</span></span>

<span data-ttu-id="58d6b-109">Jako úvodní průzkum můžete implementovat vlastní kód s třídou nástrojů pro exponenciální omezení rychlosti jako v [RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260), plus jako v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="58d6b-109">As an initial exploration, you could implement your own code with a utility class for exponential backoff as in [RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260), plus code like the following.</span></span>

```csharp
public sealed class RetryWithExponentialBackoff
{
    private readonly int maxRetries, delayMilliseconds, maxDelayMilliseconds;

    public RetryWithExponentialBackoff(int maxRetries = 50,
        int delayMilliseconds = 200,
        int maxDelayMilliseconds = 2000)
    {
        this.maxRetries = maxRetries;
        this.delayMilliseconds = delayMilliseconds;
        this.maxDelayMilliseconds = maxDelayMilliseconds;
    }

    public async Task RunAsync(Func<Task> func)
    {
        ExponentialBackoff backoff = new ExponentialBackoff(this.maxRetries,
            this.delayMilliseconds,
            this.maxDelayMilliseconds);
        retry:
        try
        {
            await func();
        }
        catch (Exception ex) when (ex is TimeoutException ||
            ex is System.Net.Http.HttpRequestException)
        {
            Debug.WriteLine("Exception raised is: " +
                ex.GetType().ToString() +
                " –Message: " + ex.Message +
                " -- Inner Message: " +
                ex.InnerException.Message);
            await backoff.Delay();
            goto retry;
        }
    }
}

public struct ExponentialBackoff
{
    private readonly int m_maxRetries, m_delayMilliseconds, m_maxDelayMilliseconds;
    private int m_retries, m_pow;

    public ExponentialBackoff(int maxRetries, int delayMilliseconds,
        int maxDelayMilliseconds)
    {
        m_maxRetries = maxRetries;
        m_delayMilliseconds = delayMilliseconds;
        m_maxDelayMilliseconds = maxDelayMilliseconds;
        m_retries = 0;
        m_pow = 1;
    }

    public Task Delay()
    {
        if (m_retries == m_maxRetries)
        {
            throw new TimeoutException("Max retry attempts exceeded.");
        }
        ++m_retries;
        if (m_retries < 31)
        {
            m_pow = m_pow << 1; // m_pow = Pow(2, m_retries - 1)
        }
        int delay = Math.Min(m_delayMilliseconds * (m_pow - 1) / 2,
            m_maxDelayMilliseconds);
        return Task.Delay(delay);
    }
}
```

<span data-ttu-id="58d6b-110">Použití tohoto kódu v klientské aplikaci v jazyce C\# (další klientská mikroslužba webového rozhraní API, aplikace ASP.NET MVC nebo dokonce aplikace v jazyce C\# Xamarin) je jednoduchá.</span><span class="sxs-lookup"><span data-stu-id="58d6b-110">Using this code in a client C\# application (another Web API client microservice, an ASP.NET MVC application, or even a C\# Xamarin application) is straightforward.</span></span> <span data-ttu-id="58d6b-111">Následující příklad ukazuje, jak pomocí třídy HttpClient.</span><span class="sxs-lookup"><span data-stu-id="58d6b-111">The following example shows how, using the HttpClient class.</span></span>

```csharp
public async Task<Catalog> GetCatalogItems(int page,int take, int? brand, int? type)
{
    _apiClient = new HttpClient();
    var itemsQs = $"items?pageIndex={page}&pageSize={take}";
    var filterQs = "";
    var catalogUrl = $"{_remoteServiceBaseUrl}items{filterQs}?pageIndex={page}&pageSize={take}";
    var dataString = "";
    //
    // Using HttpClient with Retry and Exponential Backoff
    //
    var retry = new RetryWithExponentialBackoff();
    await retry.RunAsync(async () =>
    {
        // work with HttpClient call
        dataString = await _apiClient.GetStringAsync(catalogUrl);
    });
    return JsonConvert.DeserializeObject<Catalog>(dataString);
}
```

<span data-ttu-id="58d6b-112">Mějte na paměti, že tento kód je vhodný jenom jako zkušební koncept.</span><span class="sxs-lookup"><span data-stu-id="58d6b-112">Remember that this code is suitable only as a proof of concept.</span></span> <span data-ttu-id="58d6b-113">V dalších částech se dozvíte, jak používat složitější přístupy, a to pomocí HttpClientFactory.</span><span class="sxs-lookup"><span data-stu-id="58d6b-113">The next sections explain how to use more sophisticated approaches while simpler, by using HttpClientFactory.</span></span> <span data-ttu-id="58d6b-114">HttpClientFactory je k dispozici od .NET Core 2,1 s osvědčenými knihovnami odolnými proti chybám, jako je Polly.</span><span class="sxs-lookup"><span data-stu-id="58d6b-114">HttpClientFactory is available since .NET Core 2.1, with proven resiliency libraries like Polly.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="58d6b-115">[Předchozí](implement-resilient-entity-framework-core-sql-connections.md)
>[Další](use-httpclientfactory-to-implement-resilient-http-requests.md)</span><span class="sxs-lookup"><span data-stu-id="58d6b-115">[Previous](implement-resilient-entity-framework-core-sql-connections.md)
[Next](use-httpclientfactory-to-implement-resilient-http-requests.md)</span></span>
