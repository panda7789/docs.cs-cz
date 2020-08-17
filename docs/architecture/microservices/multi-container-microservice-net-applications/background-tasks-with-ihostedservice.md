---
title: Implementace úloh na pozadí v mikroslužbách pomocí IHostedService a třídy BackgroundService
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Seznamte se s novými možnostmi použití IHostedService a BackgroundService k implementaci úloh na pozadí v mikroslužbách .NET Core.
ms.date: 08/14/2020
ms.openlocfilehash: 4ab215f2196cd2e66b116465c3a582a9846c8066
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267994"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a>Implementace úloh na pozadí v mikroslužbách pomocí IHostedService a třídy BackgroundService

Úlohy na pozadí a naplánované úlohy můžou být potřebné k použití v libovolné aplikaci, bez ohledu na to, jestli se řídí vzorem architektury mikroslužeb. Rozdíl při použití architektury mikroslužeb je, že můžete implementovat úlohu na pozadí v samostatném procesu nebo kontejneru pro hostování, abyste je mohli škálovat podle potřeby.

Z obecného bodu zobrazení se v .NET Core říkáme tento typ úkolů *hostovaných službami*, protože se jedná o služby/logiku, které hostuje v rámci hostitele/aplikace nebo mikroslužby. Všimněte si, že v tomto případě hostovaná služba jednoduše znamená třídu s logikou úlohy na pozadí.

Vzhledem k tomu, že rozhraní .NET Core 2,0, rozhraní poskytuje nové rozhraní s názvem, <xref:Microsoft.Extensions.Hosting.IHostedService> které vám pomůže snadno implementovat hostované služby. Základní nápad je, že můžete registrovat více úloh na pozadí (hostované služby), které běží na pozadí, když je spuštěný webový hostitel nebo hostitel, jak je znázorněno na obrázku 6-26.

![Diagram porovnávání ASP.NET Core IWebHost a .NET Core IHost.](./media/background-tasks-with-ihostedservice/ihosted-service-webhost-vs-host.png)

**Obrázek 6-26**. Použití IHostedService na Webhostu vs. hostiteli

ASP.NET Core 1. x a 2. x podpora `IWebHost` procesů na pozadí ve webových aplikacích. .NET Core 2,1 a novější verze podporují `IHost` procesy na pozadí pomocí jednoduchých konzolových aplikací. Všimněte si rozdílů mezi `WebHost` a `Host` .

A `WebHost` (implementace základní třídy `IWebHost` ) v ASP.NET Core 2,0 je artefakt infrastruktury, který používáte k poskytování funkcí serveru http vašemu procesu, například při implementaci webové aplikace MVC nebo služby webového rozhraní API. Poskytuje veškerou novou užitečnost infrastruktury v ASP.NET Core, což vám umožní používat vkládání závislostí, vkládat middleware do kanálu požadavků a podobně. Tato pole `WebHost` používá velmi stejné `IHostedServices` pro úlohy na pozadí.

A `Host` (implementace základní třídy `IHost` ) byla představena v rozhraní .net Core 2,1. `Host`V podstatě vám umožní mít podobnou infrastrukturu, než jakou máte s `WebHost` (vkládáním závislostí, hostovanými službami atd.), ale v takovém případě budete chtít mít jenom jednoduchý a světlejší proces jako hostitel, a to bez ohledu na funkce MVC, webové rozhraní API nebo server http.

Proto si můžete vybrat a buď vytvořit specializovaný hostitelský proces s `IHost` cílem zpracovat hostované služby a nic jiného, což je mikroslužba vytvořená jenom pro hostování `IHostedServices` , nebo můžete alternativně roztáhnout existující ASP.NET Core, jako je `WebHost` třeba existující ASP.NET Core webového rozhraní API nebo aplikace MVC.

Každý přístup má v závislosti na potřebách vaší firmy a škálovatelnosti své specialisty a nevýhody. Dolní řádek je v podstatě, aby v případě, že vaše úlohy na pozadí neobsahují žádnou akci s protokolem HTTP ( `IWebHost` ), byste měli použít `IHost` .

## <a name="registering-hosted-services-in-your-webhost-or-host"></a>Registrace hostovaných služeb ve vašem Webhostu nebo hostiteli

Pojďme přejít podrobněji na `IHostedService` rozhraní, protože jeho použití je poměrně podobné v `WebHost` nebo v `Host` .

Návěstí je jedním z příkladů artefaktu, který používá hostované služby, ale můžete ho použít i mnohem jednodušším způsobem:

- Úloha na pozadí s dotazem, který hledá změny v databázi
- Naplánovaná aktualizace některých mezipamětí v pravidelných intervalech.
- Implementace QueueBackgroundWorkItem, která umožňuje spuštění úlohy ve vlákně na pozadí.
- Zpracování zpráv z fronty zpráv na pozadí webové aplikace při sdílení běžných služeb, jako je `ILogger` .
- Úloha na pozadí začala s `Task.Run()` .

V podstatě můžete všechny tyto akce přesměrovat na úlohu na pozadí, která implementuje `IHostedService` .

Způsob, jakým můžete přidat jeden nebo více `IHostedServices` do svých nebo více aplikací, můžete `WebHost` `Host` zaregistrovat pomocí <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A>   metody rozšíření v ASP.NET Core `WebHost` (nebo v `Host` rozhraní .NET Core 2,1 a vyšší). V podstatě je nutné zaregistrovat hostované služby v rámci známé `ConfigureServices()` metody `Startup` třídy, jako v následujícím kódu z typického webhostu ASP.NET.

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    //Other DI registrations;

    // Register Hosted Services
    services.AddHostedService<GracePeriodManagerService>();
    services.AddHostedService<MyHostedServiceB>();
    services.AddHostedService<MyHostedServiceC>();
    //...
}
```

V tomto kódu `GracePeriodManagerService` je hostovaná služba skutečný kód z objednávání firemní mikroslužeb v eShopOnContainers, zatímco ostatní dva jsou jenom dvě další ukázky.

`IHostedService`Provádění úlohy na pozadí je koordinováno s životností aplikace (hostitel nebo mikroslužba pro tuto skutečnost). Při spuštění aplikace zaregistrujete úlohy a máte příležitost provést některé řádné akce nebo vyčistit při vypínání aplikace.

Bez použití `IHostedService` můžete vlákno na pozadí vždy spustit, aby se spouštěla libovolná úloha. Rozdíl je přesně v době vypnutí aplikace, kdy by bylo vlákno jednoduše ukončeno, aniž by bylo možné spustit bezproblémové čisticí akce.

## <a name="the-ihostedservice-interface"></a>Rozhraní IHostedService

Při registraci `IHostedService` rozhraní .NET Core zavolá `StartAsync()` `StopAsync()` metody a vašeho `IHostedService` typu během spuštění a zastavení aplikace. Další podrobnosti najdete v tématu [rozhraní IHostedService](https://docs.microsoft.com/aspnet/core/fundamentals/host/hosted-services?view=aspnetcore-3.1&tabs=visual-studio#ihostedservice-interface) .

Jak můžete předplatit, můžete vytvořit více implementací IHostedService a zaregistrovat je v `ConfigureService()` metodě do kontejneru di, jak je uvedeno výše. Všechny tyto hostované služby se spustí a zastaví společně s aplikací nebo mikroslužbou.

Jako vývojář zodpovídáte za zpracování akce zastavení vašich služeb, když `StopAsync()` hostitel spustí metodu.

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a>Implementace IHostedService s vlastní třídou hostované služby odvozenou od základní třídy BackgroundService

Můžete pokračovat a vytvořit vlastní třídu hostované služby od začátku a implementovat `IHostedService` , jak potřebujete při použití .NET Core 2,0.

Vzhledem k tomu, že většina úloh na pozadí bude mít podobné požadavky v souvislosti se správou tokenů zrušení a dalšími typickými operacemi, existuje praktická abstraktní základní třída, kterou můžete odvodit z, s názvem `BackgroundService` (k dispozici od rozhraní .NET Core 2,1).

Tato třída poskytuje hlavní práci potřebnou k nastavení úlohy na pozadí.

Dalším kódem je abstraktní základní třída BackgroundService, jak je implementováno v .NET Core.

```csharp
// Copyright (c) .NET Foundation. Licensed under the Apache License, Version 2.0.
/// <summary>
/// Base class for implementing a long running <see cref="IHostedService"/>.
/// </summary>
public abstract class BackgroundService : IHostedService, IDisposable
{
    private Task _executingTask;
    private readonly CancellationTokenSource _stoppingCts =
                                                   new CancellationTokenSource();

    protected abstract Task ExecuteAsync(CancellationToken stoppingToken);

    public virtual Task StartAsync(CancellationToken cancellationToken)
    {
        // Store the task we're executing
        _executingTask = ExecuteAsync(_stoppingCts.Token);

        // If the task is completed then return it,
        // this will bubble cancellation and failure to the caller
        if (_executingTask.IsCompleted)
        {
            return _executingTask;
        }

        // Otherwise it's running
        return Task.CompletedTask;
    }

    public virtual async Task StopAsync(CancellationToken cancellationToken)
    {
        // Stop called without start
        if (_executingTask == null)
        {
            return;
        }

        try
        {
            // Signal cancellation to the executing method
            _stoppingCts.Cancel();
        }
        finally
        {
            // Wait until the task completes or the stop token triggers
            await Task.WhenAny(_executingTask, Task.Delay(Timeout.Infinite,
                                                          cancellationToken));
        }

    }

    public virtual void Dispose()
    {
        _stoppingCts.Cancel();
    }
}
```

Při odvozování od předchozí abstraktní základní třídy díky této zděděné implementaci stačí implementovat `ExecuteAsync()` metodu ve vlastní třídě hostované služby, jako v následujícím zjednodušeném kódu z eShopOnContainers, který v případě potřeby dotazuje databázi a publikuje události integrace do sběrnice událostí.

```csharp
public class GracePeriodManagerService : BackgroundService
{
    private readonly ILogger<GracePeriodManagerService> _logger;
    private readonly OrderingBackgroundSettings _settings;

    private readonly IEventBus _eventBus;

    public GracePeriodManagerService(IOptions<OrderingBackgroundSettings> settings,
                                     IEventBus eventBus,
                                     ILogger<GracePeriodManagerService> logger)
    {
        // Constructor's parameters validations...
    }

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        _logger.LogDebug($"GracePeriodManagerService is starting.");

        stoppingToken.Register(() =>
            _logger.LogDebug($" GracePeriod background task is stopping."));

        while (!stoppingToken.IsCancellationRequested)
        {
            _logger.LogDebug($"GracePeriod task doing background work.");

            // This eShopOnContainers method is querying a database table
            // and publishing events into the Event Bus (RabbitMQ / ServiceBus)
            CheckConfirmedGracePeriodOrders();

            await Task.Delay(_settings.CheckUpdateTime, stoppingToken);
        }

        _logger.LogDebug($"GracePeriod background task is stopping.");
    }

    .../...
}
```

V tomto konkrétním případě pro eShopOnContainers je spuštěná metoda aplikace, která se dotazuje na databázovou tabulku a hledá objednávky s určitým stavem a při použití změn publikování událostí integrace prostřednictvím sběrnice událostí (pod ní může použít RabbitMQ nebo Azure Service Bus).

Samozřejmě můžete místo toho spustit jakoukoli jinou úlohu na pozadí firmy.

Ve výchozím nastavení je token zrušení nastaven s časovým limitem 5 sekund, i když můžete tuto hodnotu změnit při sestavování `WebHost` pomocí `UseShutdownTimeout` rozšíření `IWebHostBuilder` . To znamená, že se očekává, že se naše služba zruší do 5 sekund, jinak se ukončí.

Následující kód se změní na tento čas na 10 sekund.

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a>Diagram třídy souhrnu

Následující obrázek ukazuje vizuální souhrn tříd a rozhraní zapojených při implementaci IHostedServices.

![Diagram znázorňující, že IWebHost a IHost můžou hostovat spoustu služeb.](./media/background-tasks-with-ihostedservice/class-diagram-custom-ihostedservice.png)

**Obrázek 6-27**. Diagram tříd znázorňující více tříd a rozhraní souvisejících s IHostedService

Diagram tříd: IWebHost a IHost mohou hostovat mnoho služeb, které dědí z BackgroundService, které implementuje IHostedService.

### <a name="deployment-considerations-and-takeaways"></a>Požadavky na nasazení a poznatky

Je důležité si uvědomit, že způsob nasazení ASP.NET Core `WebHost` nebo .NET Core `Host` může mít dopad na konečné řešení. Pokud například nasadíte `WebHost` službu do služby IIS nebo běžný Azure App Service, může být hostitel vypnutý kvůli recyklaci fondu aplikací. Pokud ale hostitele nasazujete jako kontejner do nástroje Orchestrator jako Kubernetes, můžete řídit zaručený počet živých instancí hostitele. Kromě toho můžete zvážit další přístupy v cloudu, zejména pro tyto scénáře, například Azure Functions. Nakonec, pokud potřebujete, aby služba běžela po celou dobu a nasadila na Windows Server, můžete použít službu systému Windows.

Ale dokonce i pro `WebHost` nasazení do fondu aplikací existují scénáře, jako je přeplnění nebo vyprázdnění mezipaměti v paměti aplikace, kterou by bylo možné dál použít.

`IHostedService`Rozhraní poskytuje pohodlný způsob, jak spustit úlohy na pozadí ve webové aplikaci ASP.NET Core (v .NET core 2,0 a novějších verzích) nebo v jakémkoli procesu nebo hostiteli (počínaje rozhraním .NET core 2,1 s `IHost` ). Hlavní výhodou je příležitost, kterou obdržíte s řádným zrušením pro vyčištění kódu úloh na pozadí při vypínání hostitele samotného.

## <a name="additional-resources"></a>Další zdroje

- **Sestavení naplánované úlohy v ASP.NET Core/Standard 2,0** \
  <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html>

- **Implementace IHostedService v ASP.NET Core 2,0** \
  <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice>

- **Ukázka GenericHost s využitím ASP.NET Core 2,1** \
  <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample>

> [!div class="step-by-step"]
> [Předchozí](test-aspnet-core-services-web-apps.md) 
>  [Další](implement-api-gateways-with-ocelot.md)
