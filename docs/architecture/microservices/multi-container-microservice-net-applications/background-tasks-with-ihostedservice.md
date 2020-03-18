---
title: Implementace úloh na pozadí v mikroslužbách pomocí služby IHostedService a třídy BackgroundService
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Seznamte se s novými možnostmi použití služeb IHostedService a BackgroundService k implementaci úloh na pozadí v mikroslužbách .NET Core.
ms.date: 01/30/2020
ms.openlocfilehash: fab67c816e90c69a4d593422b4974cb9b8819807
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77502316"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a>Implementace úloh na pozadí v mikroslužbách pomocí služby IHostedService a třídy BackgroundService

Úlohy na pozadí a naplánované úlohy jsou něco, co budete muset implementovat, nakonec v aplikaci založené na mikroslužbách nebo v jakémkoli druhu aplikace. Rozdíl při použití architektury mikroslužeb je, že můžete implementovat jeden proces mikroslužeb nebo kontejner pro hostování těchto úloh na pozadí, takže můžete škálovat dolů nebo nahoru podle potřeby, nebo můžete dokonce ujistěte se, že spustí jednu instanci tohoto procesu mikroslužeb/kontejneru.

Z obecného hlediska v .NET Core jsme nazvali tyto typy úkolů *hostované služby*, protože se jedná o služby nebo logiku, kterou hostujete v rámci hostitele/aplikace/mikroslužby. Všimněte si, že v tomto případě hostované služby jednoduše znamená třídu s logikou úlohy na pozadí.

Vzhledem k tomu, že rozhraní .NET <xref:Microsoft.Extensions.Hosting.IHostedService> Core 2.0, rozhraní poskytuje nové rozhraní s názvem pomáhá snadno implementovat hostované služby. Základní myšlenkou je, že můžete zaregistrovat více úloh na pozadí (hostované služby), které běží na pozadí, zatímco váš webový hostitel nebo hostitel běží, jak je znázorněno na obrázku 6-26.

![Diagram porovnávající ASP.NET Core IWebHost a .NET Core IHost.](./media/background-tasks-with-ihostedservice/ihosted-service-webhost-vs-host.png)

**Obrázek 6-26**. Použití služby IHostedService ve službě WebHost vs. hostitel

ASP.NET podpora core 1.x `IWebHost` a 2.x pro procesy na pozadí ve webových aplikacích. .NET Core 2.1 a `IHost` novější verze podporují procesy na pozadí s jednoduchými konzolovými aplikacemi. Všimněte si `WebHost` rozdílu mezi a `Host`.

A `WebHost` (implementace základní `IWebHost`třídy ) v ASP.NET Core 2.0 je artefakt infrastruktury, který slouží k poskytování funkcí serveru HTTP pro váš proces, například při implementaci webové aplikace MVC nebo služby webového rozhraní API. Poskytuje všechny nové infrastruktury dobra v ASP.NET Core, což vám umožní používat vkládání závislostí, vložit middlewares v kanálu požadavku a podobně. Používá `WebHost` tyto velmi `IHostedServices` stejné pro úlohy na pozadí.

A `Host` (implementace základní `IHost`třídy) byla zavedena v rozhraní .NET Core 2.1. V podstatě, `Host` a umožňuje mít podobnou infrastrukturu, než to, co máte s `WebHost` (vkládání závislostí, hostované služby, atd.), ale v tomto případě, stačí mít jednoduchý a lehčí proces jako hostitel, s ničím souvisejícím s MVC, Web API nebo HTTP server funkce.

Proto můžete zvolit a buď vytvořit specializovaný hostitelský proces s `IHost` pro zpracování hostované služby a nic `IHostedServices`jiného, jako mikroslužby `WebHost`vyrobené pouze pro hostování , nebo můžete alternativně rozšířit existující ASP.NET Core , jako je například existující ASP.NET Core Web API nebo MVC aplikace.

Každý přístup má klady a zápory v závislosti na vaší firmě a potřebách škálovatelnosti. Pointa je v podstatě, že pokud vaše pozadí`IWebHost`úkoly `IHost`nemají nic společného s HTTP ( ) měli byste použít .

## <a name="registering-hosted-services-in-your-webhost-or-host"></a>Registrace hostovaných služeb ve vašem WebHost nebo Host

Pojďme přejít dále `IHostedService` na rozhraní, protože jeho `WebHost` použití je `Host`docela podobné v nebo v .

SignalR je jedním z příkladů artefaktu pomocí hostovaných služeb, ale můžete jej také použít pro mnohem jednodušší věci, jako jsou:

- Úloha na pozadí dotazování databáze hledá změny.
- Naplánovaná úloha pravidelně aktualizuje některé mezipaměti.
- Implementace QueueBackgroundWorkItem, která umožňuje úlohu, která má být provedena na podprocesu na pozadí.
- Zpracování zpráv z fronty zpráv na pozadí webové aplikace při `ILogger`sdílení běžných služeb, jako je například .
- Úloha na `Task.Run()`pozadí byla zahájena pomocí souboru .

V podstatě můžete převést některé z těchto akcí `IHostedService`na úlohu na pozadí, která implementuje .

Způsob, jakým přidáte `IHostedServices` jeden `WebHost` nebo `Host` více do vašeho nebo <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A>  je jejich registrací prostřednictvím metody rozšíření v ASP.NET Core `WebHost` (nebo `Host` v rozhraní .NET Core 2.1 a vyšší). V podstatě musíte zaregistrovat hostované služby v rámci známé `ConfigureServices()` metody `Startup` třídy, jako v následujícím kódu z typického ASP.NET WebHost.

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

V tomto kódu `GracePeriodManagerService` hostované služby je skutečný kód z objednávání obchodní mikroslužby v eShopOnContainers, zatímco další dva jsou jen dva další ukázky.

Spuštění `IHostedService` úlohy na pozadí je koordinováno s životností aplikace (hostitele nebo mikroslužby, když na to přijde). Zaregistrujete úkoly při spuštění aplikace a máte možnost provést některé řádné akce nebo vyčištění při ukončení aplikace.

Bez `IHostedService`použití můžete vždy spustit vlákno na pozadí pro spuštění libovolné úlohy. Rozdíl je právě v době vypnutí aplikace, kdy by toto vlákno bylo jednoduše ukončeno, aniž by mělo možnost spustit řádné akce čištění.

## <a name="the-ihostedservice-interface"></a>Rozhraní IHostedService

Při registraci `IHostedService`, .NET Core `StartAsync()` `StopAsync()` bude volat `IHostedService` a metody vašeho typu během spuštění a zastavení aplikace v uvedeném pořadí. Konkrétně start je volána po `IApplicationLifetime.ApplicationStarted` spuštění serveru a je spuštěn.

Jak `IHostedService` je definováno v .NET Core, vypadá takto.

```csharp
namespace Microsoft.Extensions.Hosting
{
    //
    // Summary:
    //     Defines methods for objects that are managed by the host.
    public interface IHostedService
    {
        //
        // Summary:
        // Triggered when the application host is ready to start the service.
        Task StartAsync(CancellationToken cancellationToken);
        //
        // Summary:
        // Triggered when the application host is performing a graceful shutdown.
        Task StopAsync(CancellationToken cancellationToken);
    }
}
```

Jak si dokážete představit, můžete vytvořit více implementací IHostedService a zaregistrovat je metodou `ConfigureService()` do kontejneru DI, jak je znázorněno dříve. Všechny tyto hostované služby budou spuštěny a zastaveny spolu s aplikací nebo mikroslužbou.

Jako vývojář jste zodpovědní za zpracování akce zastavení `StopAsync()` vašich služeb při spuštění metody hostitelem.

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a>Implementace služby IHostedService s vlastní třídou hostované služby odvozenou ze základní třídy BackgroundService

Můžete pokračovat a vytvořit vlastní třídu hostované služby od začátku a implementovat `IHostedService`, jak je potřeba udělat při použití rozhraní .NET Core 2.0.

Však vzhledem k tomu, že většina úloh na pozadí bude mít podobné potřeby s ohledem na `BackgroundService` správu tokenů zrušení a další typické operace, je pohodlné abstraktní základní třídy můžete odvodit z, pojmenovaný (k dispozici od .NET Core 2.1).

Tato třída poskytuje hlavní práci potřebnou k nastavení úlohy na pozadí.

Další kód je abstraktní Základní třída BackgroundService, jak je implementována v .NET Core.

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

Při odvození z předchozí abstraktní základní třídy, díky této zděděné `ExecuteAsync()` implementaci, stačí implementovat metodu ve vlastní třídě hostované služby, jako v následujícím zjednodušeném kódu z eShopOnContainers, který je dotazování databáze a publikování integračních událostí do sběrnice událostí v případě potřeby.

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
        //Constructor’s parameters validations...
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

V tomto konkrétním případě pro eShopOnContainers, je to provádění aplikační metody, která je dotazování databázové tabulky hledá objednávky s určitým stavem a při použití změn, je publikování integračních událostí prostřednictvím sběrnice událostí (pod ním může být pomocí RabbitMQ nebo Azure Service Bus).

Samozřejmě, můžete spustit jakýkoli jiný obchodní pozadí úkol, místo toho.

Ve výchozím nastavení je token zrušení nastaven s časovým limitem 5 `WebHost` sekund, `UseShutdownTimeout` i `IWebHostBuilder`když tuto hodnotu můžete změnit při vytváření rozšíření . To znamená, že naše služba by měla být zrušena do 5 sekund, jinak bude náhle zabita.

Následující kód by se mění, že čas na 10 sekund.

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a>Souhrnný diagram třídy

Následující obrázek znázorňuje vizuální souhrn tříd a rozhraní zapojených při implementaci IHostedServices.

![Diagram znázorňující, že IWebHost a IHost mohou hostit mnoho služeb.](./media/background-tasks-with-ihostedservice/class-diagram-custom-ihostedservice.png)

**Obrázek 6-27**. Diagram tříd znázorňující více tříd a rozhraní souvisejících se službou IHostedService

Diagram tříd: IWebHost a IHost mohou hostovat mnoho služeb, které dědí z BackgroundService, která implementuje IHostedService.

### <a name="deployment-considerations-and-takeaways"></a>Důležité informace o nasazení a s sebou

Je důležité si uvědomit, že způsob `WebHost` nasazení ASP.NET `Host` core nebo .NET Core může mít vliv na konečné řešení. Pokud například nasadíte službu `WebHost` IIS nebo běžnou službu Azure App Service, můžete hostitele vypnout z důvodu recyklace fondu aplikací. Ale pokud nasazujete hostitele jako kontejner do orchestrátoru, jako je Kubernetes, můžete řídit jistý počet živých instancí hostitele. Kromě toho můžete zvážit další přístupy v cloudu speciálně pro tyto scénáře, jako jsou funkce Azure. A konečně, pokud potřebujete službu, která má být spuštěna po celou dobu a nasazuje te na systém Windows Server, můžete použít službu Systému Windows.

Ale i `WebHost` pro nasazené do fondu aplikací existují scénáře, jako je repopulating nebo vyprázdnění mezipaměti aplikace v paměti, které by byly stále použitelné.

Rozhraní `IHostedService` poskytuje pohodlný způsob, jak spustit úlohy na pozadí ve webové aplikaci ASP.NET Core (v rozhraní .NET Core 2.0 `IHost`a novějších verzích) nebo v libovolném procesu/hostiteli (počínaje rozhraním .NET Core 2.1 s). Jeho hlavní výhodou je příležitost, kterou získáte s elegantním zrušením k vyčištění kódu vašich úloh na pozadí, když se hostitel sám vypíná.

## <a name="additional-resources"></a>Další zdroje

- **Vytvoření naplánované úlohy v ASP.NET Jádrem/Standardem 2.0** \
  <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html>

- **Implementace služby IHostedService v ASP.NET Jádra 2.0** \
  <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice>

- **Ukázka generického hostitele pomocí ASP.NET Core 2.1** \
  <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample>

>[!div class="step-by-step"]
>[Předchozí](test-aspnet-core-services-web-apps.md)
>[další](implement-api-gateways-with-ocelot.md)
