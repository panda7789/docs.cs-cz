---
title: Prozkoumejte vlastních opakování volání HTTP pomocí exponenciálního omezení rychlosti
description: Zjistěte, jak je možné implementovat, od začátku, opakování volání HTTP pomocí exponenciálního omezení rychlosti zpracování možných scénářů chyby protokolu HTTP.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: b7aaad9199bb275f45fd088a6207d707e8e5751c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145095"
---
# <a name="explore-custom-http-call-retries-with-exponential-backoff"></a><span data-ttu-id="52ef2-103">Prozkoumejte vlastních opakování volání HTTP pomocí exponenciálního omezení rychlosti</span><span class="sxs-lookup"><span data-stu-id="52ef2-103">Explore custom HTTP call retries with exponential backoff</span></span>

<span data-ttu-id="52ef2-104">K vytvoření odolné mikroslužeb, potřebujete zpracovávat možných scénářů chyby protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="52ef2-104">To create resilient microservices, you need to handle possible HTTP failure scenarios.</span></span> <span data-ttu-id="52ef2-105">Jedním ze způsobů zpracování těchto chyb, však není doporučena, je vytvořit vlastní implementace opakování pomocí exponenciálního omezení rychlosti.</span><span class="sxs-lookup"><span data-stu-id="52ef2-105">One way of handling those failures, although not recommended, is to create your own implementation of retries with exponential backoff.</span></span>

<span data-ttu-id="52ef2-106">**Důležitá poznámka:** Tato část popisuje, jak můžete vytvořit vlastní kód pro implementaci opakování volání HTTP.</span><span class="sxs-lookup"><span data-stu-id="52ef2-106">**Important note:** This section shows you how you could create your own custom code to implement HTTP call retries.</span></span> <span data-ttu-id="52ef2-107">Ale nedoporučujeme to udělat příkazem vlastní, ale výkonné a spolehlivé, zatímco je jednodušší použít mechanismy, jako například `HttpClientFactory` pomocí knihovny Polly dostupné od verze rozhraní .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="52ef2-107">However, it is not recommended to do it by your own but to use more powerful and reliable while simpler to use mechanisms, such as `HttpClientFactory` with Polly, available since .NET Core 2.1.</span></span> <span data-ttu-id="52ef2-108">Tyto doporučené postupy jsou vysvětlené v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="52ef2-108">Those recommended approaches are explained in the next sections.</span></span> 

<span data-ttu-id="52ef2-109">Jako počáteční zkoumání, je možné implementovat vlastního kódu s využitím třídy nástrojů pro exponenciálního omezení rychlosti jako v [RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260), plus kód podobný tomuto (což je také k dispozici na tomto [Githubu úložiště](https://gist.github.com/CESARDELATORRE/d80c6423a1aebaffaf387469f5194f5b)).</span><span class="sxs-lookup"><span data-stu-id="52ef2-109">As an initial exploration, you could implement your own code with a utility class for exponential backoff as in [RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260), plus code like the following (which is also available at this [GitHub repo](https://gist.github.com/CESARDELATORRE/d80c6423a1aebaffaf387469f5194f5b)).</span></span>

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

<span data-ttu-id="52ef2-110">Pomocí tohoto kódu v klientovi C\# aplikace (jiného webového rozhraní API klienta mikroslužeb, aplikaci ASP.NET MVC nebo dokonce C\# aplikace Xamarin) je jednoduché.</span><span class="sxs-lookup"><span data-stu-id="52ef2-110">Using this code in a client C\# application (another Web API client microservice, an ASP.NET MVC application, or even a C\# Xamarin application) is straightforward.</span></span> <span data-ttu-id="52ef2-111">Následující příklad ukazuje, jak pomocí třídy HttpClient.</span><span class="sxs-lookup"><span data-stu-id="52ef2-111">The following example shows how, using the HttpClient class.</span></span>

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

<span data-ttu-id="52ef2-112">Mějte na paměti, že tento kód je vhodný pouze jako testování konceptu.</span><span class="sxs-lookup"><span data-stu-id="52ef2-112">Remember that this code is suitable only as a proof of concept.</span></span> <span data-ttu-id="52ef2-113">Další části popisují, jak používat složitější přístupy, zatímco je jednodušší, pomocí HttpClientFactory.</span><span class="sxs-lookup"><span data-stu-id="52ef2-113">The next sections explain how to use more sophisticated approaches while simpler, by using HttpClientFactory.</span></span>
<span data-ttu-id="52ef2-114">HttpClientFactory je k dispozici od verze rozhraní .NET Core 2.1 s knihovnami osvědčené odolnost proti chybám, jako je Polly.</span><span class="sxs-lookup"><span data-stu-id="52ef2-114">HttpClientFactory is available since .NET Core 2.1, with proven resiliency libraries like Polly.</span></span> 

>[!div class="step-by-step"]
><span data-ttu-id="52ef2-115">[Předchozí](implement-resilient-entity-framework-core-sql-connections.md)
>[další](use-httpclientfactory-to-implement-resilient-http-requests.md)</span><span class="sxs-lookup"><span data-stu-id="52ef2-115">[Previous](implement-resilient-entity-framework-core-sql-connections.md)
[Next](use-httpclientfactory-to-implement-resilient-http-requests.md)</span></span>