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
# <a name="explore-custom-http-call-retries-with-exponential-backoff"></a>Prozkoumejte opakované pokusy o vlastní volání HTTP pomocí exponenciálního omezení rychlostiu

Chcete-li vytvořit odolné mikroslužby, je třeba zvládnout možné scénáře selhání protokolu HTTP. Jedním ze způsobů, jak tyto chyby zpracovat, ale nedoporučujeme, je vytvořit vlastní implementaci opakovaných pokusů pomocí exponenciálního omezení rychlostiu.

**Důležitá Poznámka:** V této části se dozvíte, jak můžete vytvořit vlastní kód pro implementaci opakovaných pokusů o volání HTTP. Nedoporučuje se ale dělat sami sebe, ale k použití výkonnějších a spolehlivých a současně jednoduššího používání mechanismů, `HttpClientFactory` jako je Polly, k dispozici od .NET Core 2,1. Tyto doporučené přístupy jsou vysvětleny v dalších částech.

Jako úvodní průzkum můžete implementovat vlastní kód s třídou nástrojů pro exponenciální omezení rychlosti jako v [RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260), plus jako v následujícím kódu.

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

Použití tohoto kódu v klientské aplikaci jazyka\# C (další klientská mikroslužba webového rozhraní API, aplikace ASP.NET MVC nebo dokonce aplikace C\# Xamarin) je jednoduchá. Následující příklad ukazuje, jak pomocí třídy HttpClient.

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

Mějte na paměti, že tento kód je vhodný jenom jako zkušební koncept. V dalších částech se dozvíte, jak používat složitější přístupy, a to pomocí HttpClientFactory. HttpClientFactory je k dispozici od .NET Core 2,1 s osvědčenými knihovnami odolnými proti chybám, jako je Polly.

>[!div class="step-by-step"]
>[Předchozí](implement-resilient-entity-framework-core-sql-connections.md)Další
>[](use-httpclientfactory-to-implement-resilient-http-requests.md)
