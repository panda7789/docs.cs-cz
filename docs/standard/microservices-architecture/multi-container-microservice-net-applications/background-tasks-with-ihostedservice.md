---
title: Implementace úlohy na pozadí v mikroslužeb s IHostedService a BackgroundService – třída
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace úlohy na pozadí v mikroslužeb s IHostedService a BackgroundService – třída
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: eb6d412ee91ab8d2c97a4917f23ee914e3fb9068
ms.sourcegitcommit: fc70fcb9c789b6a4aefcdace46f3643fd076450f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2018
ms.locfileid: "34805565"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a>Implementace úlohy na pozadí v mikroslužeb s IHostedService a BackgroundService – třída

Úlohy na pozadí a naplánované úlohy jsou něco, co může být nutné implementovat, nakonec v aplikaci mikroslužbu na základě nebo v jakékoliv aplikaci. Při použití architektury mikroslužeb rozdílem je, že můžete implementovat jednu mikroslužbu proces nebo kontejner pro hostování tyto úlohy na pozadí, můžete ho dolů/nahoru škálovat, jako je třeba nebo můžete i zajistit, aby byl spouštěn jednu instanci mikroslužbu procesu nebo kontejneru.

Z obecné hlediska v .NET Core volali jsme tyto typ úlohy hostované služby, protože jsou služby nebo logiky, která hostitele v rámci vaší hostitele/aplikace/mikroslužby. Všimněte si, že v tomto případě hostovanou službu jednoduše znamená třídu s logikou úloh na pozadí.

Od verze rozhraní .NET 2.0 jádra, rozhraní, poskytuje nové rozhraní s názvem <xref:Microsoft.Extensions.Hosting.IHostedService> pomáhá můžete snadno implementace hostované služby. Základní myšlenkou je, že zaregistrujete několik úlohy na pozadí (hostované služby), které běží na pozadí při webového hostitele nebo hostiteli běží, jak je znázorněno na obrázku níže.

![](./media/image26.png)

**Obrázek 8-25.** Použití IHostedService v webového hostitele a hostitele

Všimněte si rozdílu mezi `WebHost` a `Host`. A `WebHost` (základní třída implementace `IWebHost`) v technologii ASP.NET 2.0 základní je artefaktů infrastruktury k poskytování HTTP server funkce procesu, jako třeba když používáte implementujete webové aplikace MVC nebo webového rozhraní API služby. Poskytuje všechny nové přesnosti infrastruktury v ASP.NET Core, umožňuje pomocí vkládání závislostí, vložte middlewares kanál protokolu HTTP, atd. a přesněji použít `IHostedServices` pro úlohy na pozadí.

A `Host` (základní třída implementace `IHost`), ale je něco v rozhraní .NET Core 2.1 nového. V podstatě `Host` umožňuje mít podobné infrastrukturu než máte s `WebHost` (vkládání závislostí, hostovaných služeb atd.), ale v takovém případě stačí chcete mít jednoduché a světlejší proces jako hostitel, s nic související s MVC , Webové rozhraní API nebo HTTP funkce serveru.

Proto můžete vybrat a buď vytvořit specializované hostitelský proces s IHost pro zpracování hostované služby a nic jiného, takové mikroslužbu, jenom pro hostování `IHostedServices`, nebo můžete případně rozšířit existující ASP.NET Core `WebHost` , jako je například stávající aplikace webového rozhraní API ASP.NET Core nebo MVC. 

Každý přístup má výhody a nevýhody podle potřeby firmy a škálovatelnost. Dolní řádek je v podstatě, pokud vaše úlohy na pozadí nemají co dělat s byste měli používat protokol HTTP (IWebHost) a IHost, pokud je k dispozici v rozhraní .NET Core 2.1.

## <a name="registering-hosted-services-in-your-webhost-or-host"></a>Registrace hostovaných služeb v webového hostitele nebo hostitele

Umožňuje přejít k podrobnostem dolů na další `IHostedService` rozhraní vzhledem k tomu, že je poměrně podobně jako v jeho využití `WebHost` nebo v `Host`. 

SignalR je příkladem artefakt pomocí hostované služby, ale můžete ji použít i pro mnohem jednodušší věcmi, jako jsou:

-   Úlohy na pozadí, dotazování databáze hledá změny.
-   Naplánované úlohy pravidelně aktualizuje některé mezipaměti.
-   Implementace QueueBackgroundWorkItem, která umožňuje úlohy ke spuštění na vlákna na pozadí.
-   Zpracování zpráv z fronty zpráv na pozadí webové aplikace při sdílení společných služeb, jako `ILogger`.
-   Spuštění úlohy na pozadí s `Task.Run()`.

V podstatě můžete přesměrovat některou z těchto akcí pro úlohy na pozadí podle IHostedService.

Způsob, jak můžete přidat jeden nebo více `IHostedServices` do vaší `WebHost` nebo `Host` je tak, že je zaregistrujete až prostřednictvím standardní DI (dependency injection) v ASP.NET Core `WebHost` (nebo v `Host` v rozhraní .NET Core 2.1). V podstatě, je nutné provést registraci hostovaných služeb v rámci známé `ConfigureServices()` metodu `Startup` třídy, jako v následujícím kódu z typických webového hostitele technologie ASP.NET. 

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{            
    //Other DI registrations;

    // Register Hosted Services
    services.AddSingleton<IHostedService, GracePeriodManagerService>();
    services.AddSingleton<IHostedService, MyHostedServiceB>();
    services.AddSingleton<IHostedService, MyHostedServiceC>();
    //...
}
```

V kódu `GracePeriodManagerService` hostovaná služba je skutečné kód z mikroslužbu obchodní řazení v eShopOnContainers, při dalších dva jsou právě dva další ukázky.

`IHostedService` Provádění úkolů pozadí bude řízeno životního cyklu aplikace (hostitele nebo mikroslužbu k tomuto účelu). Při spuštění aplikace a máte možnost provést některé řádně akce nebo čištění když se aplikace vypíná, zaregistrovat úlohy.

Bez použití `IHostedService`, můžete začít vždy vlákna na pozadí spustit všechny úlohy. Rozdílem je, přesněji v době vypnutí aplikace při daném vláknu by být ukončeny jednoduše bez nutnosti příležitostí ke spouštění řádně akcí čištění.


## <a name="the-ihostedservice-interface"></a>Rozhraní IHostedService

Když se zaregistrujete `IHostedService`, .NET Core zavolá `StartAsync()` a `StopAsync()` metody vaší `IHostedService` zadejte při spuštění aplikace a zastavit v uvedeném pořadí. Konkrétně je počáteční volána po spuštění serveru a `IApplicationLifetime.ApplicationStarted` se aktivuje.

`IHostedService` Definuje .NET Core, vypadá podobně jako následující.

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
Jak si lze představit, můžete vytvořit více implementace IHostedService a zaregistrujte je v `ConfigureService()` metoda do kontejneru DI, jak je uvedený výše. Všechny tyto hostované služby se spuštění a zastavení spolu s aplikací nebo mikroslužby.

Jako vývojář je zodpovědná za zpracování akce zastavení nebo vašim službám při `StopAsync()` metoda se aktivuje hostitele.

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a>Implementace IHostedService s třídou vlastní hostovanou službu odvozování ze základní třídy BackgroundService

Můžete ihned začít a vytvořit vlastní hostovanou službu třída od začátku a implementovat `IHostedService`, jako je třeba provést při použití rozhraní .NET 2.0 jádra. 

Ale vzhledem k tomu, že většina úlohy na pozadí bude mít podobné potřeby správy zrušení tokenů a dalších typických operací, .NET Core 2.1 bude poskytovat velmi praktické abstraktní základní třída, kterou můžete odvozena od, s názvem BackgroundService.

Třídy poskytuje hlavní práce potřebné k nastavení úlohy na pozadí. Všimněte si, že tato třída, vrátí se v knihovně .NET Core 2.1, nemusíte ho zapsat.

Však od době psaní tohoto textu .NET Core 2.1 ještě neuvolnil. Proto v eShopOnContainers, který je aktuálně používá rozhraní .NET 2.0 jádra, jsme se právě dočasně zařadit třídy z úložiště .NET Core 2.1 open-source (není třeba žádné vlastní licence než licence open-source) vzhledem k tomu, že je kompatibilní s aktuální IHostedService rozhraní v rozhraní .NET 2.0 jádra. Po vydání .NET Core 2.1, budete potřebovat pouze tak, aby odkazovaly na správné balíček NuGet.

Další kód je abstraktní základní třída BackgroundService, jak jsou implementované v rozhraní .NET Core 2.1.

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

Při jeho odvozování z předchozí abstraktní základní třída, díky této zděděné implementace, stačí k implementaci `ExecuteAsync()` metoda ve vlastní vlastní hostované třídy služeb, jako v následujícím příkladu zjednodušené kód z eShopOnContainers, který se dotazuje databáze a publikování události integrace do sběrnici událost v případě potřeby.

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
                // and publishing events into the Event Bus (RabbitMS / ServiceBus)
                CheckConfirmedGracePeriodOrders();

                await Task.Delay(_settings.CheckUpdateTime, stoppingToken);
            }
            
            _logger.LogDebug($"GracePeriod background task is stopping.");

        }

        protected override async Task StopAsync (CancellationToken stoppingToken)
        {
               // Run your graceful clean-up actions
        }
}
```

V tomto konkrétním případě pro eShopOnContainers je prováděna metodu aplikace, který se dotazuje tabulku databáze, hledá příkazy se určitý stav a při použití změn, publikování události integrace přes sběrnici událostí (dole, může to být pomocí RabbitMQ nebo Azure Service Bus). 

Samozřejmě může spustit jakékoli jiné obchodní úlohy na pozadí, místo toho.

Ve výchozím nastavení, token zrušení nastavena 5 druhý vypršel časový limit, i když tuto hodnotu můžete změnit při vytváření vašeho `WebHost` pomocí `UseShutdownTimeout` rozšíření `IWebHostBuilder`. To znamená, že naše služby je očekávaná zrušit po dobu pěti sekund jinak bude mít více náhle ukončeny.

Následující kód by změna této doby na 10 sekund.

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a>Třída shrnutí diagram

Následující obrázek 8-26 zobrazuje souhrn třídy vizuál a propojen související se situací, při implementaci IHostedServices.
 
![](./media/image27.png)

**Obrázek 8-26.** Třída diagram znázorňující násobek třídy a rozhraní související s IHostedService

### <a name="deployment-considerations-and-takeaways"></a>Důležité informace o nasazení a takeaways

Je důležité si uvědomit, že způsob nasazení ASP.NET Core `WebHost` nebo .NET Core `Host` může mít vliv na konečné řešení. Například pokud nasadíte vaší `WebHost` služby IIS nebo regulární Azure App Service, může být váš hostitel vypnut z důvodu recykluje fond aplikací. Ale pokud nasazujete váš hostitel jako kontejner do produktu orchestrator jako Kubernetes nebo Service Fabric, můžete řídit pojištěných počet instancí za provozu vaše hostitele. Kromě toho zvažte další postupy v cloudu, zejména provedené pro tyto scénáře, jako je Azure Functions. 

Ale i pro `WebHost` nasadí do fondu aplikací, existují scénáře, jako je opětovného vyplnění nebo abyste vyprázdnili mezipaměť v paměti aplikace, která by byla stále platná.

`IHostedService` Rozhraní představuje pohodlný způsob pro spuštění úlohy na pozadí v ASP.NET Core webovou aplikaci (v rozhraní .NET 2.0 jádra) nebo v jakékoli proces hostitele (počínaje .NET Core 2.1 s `IHost`). Jeho hlavní výhodou je příležitost, kterou dostanete s řádně zrušení čištění kódu úlohy na pozadí, když se vypíná hostitele sám sebe.


#### <a name="additional-resources"></a>Další zdroje

-   **Vytváření naplánované úlohy v technologii ASP.NET 2.0 základní nebo standardní** 

    [*https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html*](https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html)

-   **Implementace IHostedService v základní technologie ASP.NET 2.0** 

    [*https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice*](https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice)

-   **Ukázky hostování 2.1 jádro ASP.NET** 

    [*https://github.com/aspnet/Hosting/tree/dev/samples/GenericHostSample*](https://github.com/aspnet/Hosting/tree/dev/samples/GenericHostSample)



>[!div class="step-by-step"]
[Předchozí] (test-aspnet-core-services-web-apps.md) [Další] (.. /microservice-ddd-cqrs-Patterns/index.MD)
