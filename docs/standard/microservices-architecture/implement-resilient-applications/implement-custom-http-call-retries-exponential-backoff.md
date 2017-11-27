---
title: "Implementace vlastních opakování volání protokolu HTTP s exponenciálního omezení rychlosti"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace vlastních opakování volání protokolu HTTP s exponenciálního omezení rychlosti"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 4449e5d7e0ca3c81aead26fac653de3ba2187a92
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-custom-http-call-retries-with-exponential-backoff"></a>Implementace vlastních opakování volání protokolu HTTP s exponenciálního omezení rychlosti

Chcete-li vytvořit odolné mikroslužeb, budete muset zpracování možných scénářích selhání HTTP. K tomuto účelu můžete vytvářet vlastní implementaci opakování s exponenciálního omezení rychlosti.

Kromě zpracování prostředků dočasné nedostupnosti, exponenciálního omezení rychlosti také je potřeba vzít v úvahu, že poskytovatel cloudové může omezit dostupnost prostředků, aby se zabránilo přetížení využití. Například velmi rychle vytváření příliš mnoho žádostí o připojení může zobrazit jako Denial of Service ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) útoku poskytovatelem cloudu. V důsledku toho budete muset poskytují mechanismus back připojení požadavky škálovat tak, když byla zjištěna prahové hodnoty kapacity.

Jako počáteční zkoumání, může implementovat vlastní kód s třídou nástroj pro exponenciálního omezení rychlosti jako v [RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260), plus kód takto (což je také k dispozici na [úložiště GitHub ](https://gist.github.com/CESARDELATORRE/d80c6423a1aebaffaf387469f5194f5b)).

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

Pomocí tohoto kódu v klientovi C\# aplikace (jiné mikroslužbu webového rozhraní API klienta, aplikace ASP.NET MVC nebo i C\# aplikace Xamarin) je jednoduché. Následující příklad ukazuje, jak pomocí třídy HttpClient.

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

Tento kód je však vhodné pouze jako testování konceptu. Další téma vysvětluje, jak používat sofistikované a osvědčené knihovny.


>[!div class="step-by-step"]
[Předchozí] (implement-resilient-entity-framework-core-sql-connections.md) [Další] (implement-http-call-retries-exponential-backoff-polly.md)
