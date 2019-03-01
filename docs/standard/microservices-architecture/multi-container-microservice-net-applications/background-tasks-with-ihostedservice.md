---
title: Implementace úloh na pozadí v mikroslužbách s IHostedService a BackgroundService třídy
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Zjistěte, nové možnosti použití IHostedService a BackgroundService implementace úloh na pozadí v mikroslužby .NET Core.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: 638c9b9bae97b90b94c0ca9b421bc20cd3eb41ee
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967188"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a><span data-ttu-id="ae269-103">Implementace úloh na pozadí v mikroslužbách s IHostedService a BackgroundService třídy</span><span class="sxs-lookup"><span data-stu-id="ae269-103">Implement background tasks in microservices with IHostedService and the BackgroundService class</span></span>

<span data-ttu-id="ae269-104">Naplánované úlohy a úlohy na pozadí jsou něco, co možná budete muset implementovat, případně v aplikaci na základě mikroslužeb nebo v jakékoliv aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ae269-104">Background tasks and scheduled jobs are something you might need to implement, eventually, in a microservice based application or in any kind of application.</span></span> <span data-ttu-id="ae269-105">Rozdíl při použití architektury mikroslužeb je, že můžete implementovat jednu mikroslužbu procesu/kontejner pro hostování tyto úlohy na pozadí, takže je možné ji dolů/nahoru škálovat podle musíte nebo dokonce zajistit, že běží jedna instance, která mikroslužby procesu nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="ae269-105">The difference when using a microservices architecture is that you can implement a single microservice process/container for hosting these background tasks so you can scale it down/up as you need or you can even make sure that it runs a single instance of that microservice process/container.</span></span>

<span data-ttu-id="ae269-106">Z obecného pohledu, v .NET Core zavolali jsme na těchto typů úkolů *služeb hostovaných v*, protože jsou služby a logiku, která hostujete v rámci vašeho hostitele/aplikace/mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="ae269-106">From a generic point of view, in .NET Core we called these type of tasks *Hosted Services*, because they are services/logic that you host within your host/application/microservice.</span></span> <span data-ttu-id="ae269-107">Všimněte si, že v tomto případě hostovanou službu jednoduše znamená, že třída s atributem logiky úloh na pozadí.</span><span class="sxs-lookup"><span data-stu-id="ae269-107">Note that in this case, the hosted service simply means a class with the background task logic.</span></span>

<span data-ttu-id="ae269-108">Od verze rozhraní .NET Core 2.0, rozhraní poskytuje nové rozhraní s názvem <xref:Microsoft.Extensions.Hosting.IHostedService> vám pomáhá snadno implementovat hostované služby.</span><span class="sxs-lookup"><span data-stu-id="ae269-108">Since .NET Core 2.0, the framework provides a new interface named <xref:Microsoft.Extensions.Hosting.IHostedService> helping you to easily implement hosted services.</span></span> <span data-ttu-id="ae269-109">Základní myšlenka je, že můžete registrovat několika úloh na pozadí (hostované služby), které běží na pozadí při webového hostitele nebo hostiteli běží, jak je znázorněno na obrázku 6-26.</span><span class="sxs-lookup"><span data-stu-id="ae269-109">The basic idea is that you can register multiple background tasks (hosted services), that run in the background while your web host or host is running, as shown in the image 6-26.</span></span>

![ASP.NET Core 1.x a 2.x podpora IWebHost pozadí zpracovává ve službě web apps, .NET Core, 2,1 podporuje IHost pro procesy na pozadí s jednoduché konzolové aplikace.](./media/image26.png)

<span data-ttu-id="ae269-111">**Obrázek 6-26**.</span><span class="sxs-lookup"><span data-stu-id="ae269-111">**Figure 6-26**.</span></span> <span data-ttu-id="ae269-112">Použití IHostedService v webového hostitele a hostitele</span><span class="sxs-lookup"><span data-stu-id="ae269-112">Using IHostedService in a WebHost vs. a Host</span></span>

<span data-ttu-id="ae269-113">Všimněte si rozdílu mezi `WebHost` a `Host`.</span><span class="sxs-lookup"><span data-stu-id="ae269-113">Note the difference made between `WebHost` and `Host`.</span></span> 

<span data-ttu-id="ae269-114">A `WebHost` (základní třídy implementující `IWebHost`) v ASP.NET Core 2.0 je artefaktů infrastruktury vám poskytují HTTP server s funkcí pro váš proces, třeba když implementujete MVC webové aplikace nebo služba webového rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="ae269-114">A `WebHost` (base class implementing `IWebHost`) in ASP.NET Core 2.0 is the infrastructure artifact you use to provide HTTP server features to your process, such as if you are implementing an MVC web app or Web API service.</span></span> <span data-ttu-id="ae269-115">Poskytuje všechny nové infrastruktury přesnosti v ASP.NET Core, která vám umožní pomocí vkládání závislostí, vložit middlewares v požadavku kanálu atd a pomocí nich přesně `IHostedServices` pro úlohy na pozadí.</span><span class="sxs-lookup"><span data-stu-id="ae269-115">It provides all the new infrastructure goodness in ASP.NET Core, enabling you to use dependency injection, insert middlewares in the request pipeline, etc. and precisely use these `IHostedServices` for background tasks.</span></span>

<span data-ttu-id="ae269-116">A `Host` (základní třídy implementující `IHost`) byla zavedena v rozhraní .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="ae269-116">A `Host` (base class implementing `IHost`) was introduced in .NET Core 2.1.</span></span> <span data-ttu-id="ae269-117">V podstatě `Host` umožňuje mít podobné infrastruktury, než máte s `WebHost` (injektáž závislostí, hostovaných služeb atd.), ale v tomto případě chcete mít jednoduchou a lehčí proces jako hostitele, není nic související s MVC , Webové rozhraní API nebo HTTP funkce serveru.</span><span class="sxs-lookup"><span data-stu-id="ae269-117">Basically, a `Host` allows you to have a similar infrastructure than what you have with `WebHost` (dependency injection, hosted services, etc.), but in this case, you just want to have a simple and lighter process as the host, with nothing related to MVC, Web API or HTTP server features.</span></span>

<span data-ttu-id="ae269-118">Proto můžete použít a buď vytvořte specializované hostitelský proces s IHost hostovaným službám a nic jiného, mikroslužby, vytvořená speciálně pro hostování `IHostedServices`, nebo můžete případně rozšířit stávající ASP.NET Core `WebHost` , jako je například existující aplikaci webového rozhraní API ASP.NET Core nebo MVC.</span><span class="sxs-lookup"><span data-stu-id="ae269-118">Therefore, you can choose and either create a specialized host-process with IHost to handle the hosted services and nothing else, such a microservice made just for hosting the `IHostedServices`, or you can alternatively extend an existing ASP.NET Core `WebHost`, such as an existing ASP.NET Core Web API or MVC app.</span></span> 

<span data-ttu-id="ae269-119">Každý přístup má výhody a nevýhody v závislosti na potřebách vaší firmy a škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="ae269-119">Each approach has pros and cons depending on your business and scalability needs.</span></span> <span data-ttu-id="ae269-120">Dolní řádek je v podstatě, že pokud vaše úlohy na pozadí nemají co dělat s protokolem HTTP (IWebHost) byste měli použít IHost.</span><span class="sxs-lookup"><span data-stu-id="ae269-120">The bottom line is basically that if your background tasks have nothing to do with HTTP (IWebHost) you should use IHost.</span></span>

## <a name="registering-hosted-services-in-your-webhost-or-host"></a><span data-ttu-id="ae269-121">Registrace hostovaných služeb v webového hostitele nebo hostitele</span><span class="sxs-lookup"><span data-stu-id="ae269-121">Registering hosted services in your WebHost or Host</span></span>

<span data-ttu-id="ae269-122">Můžeme přejít na další nižší `IHostedService` rozhraní, protože jeho používání je hodně podobné jako u `WebHost` nebo v `Host`.</span><span class="sxs-lookup"><span data-stu-id="ae269-122">Let’s drill down further on the `IHostedService` interface since its usage is pretty similar in a `WebHost` or in a `Host`.</span></span> 

<span data-ttu-id="ae269-123">SignalR je jeden příklad artefakt pomocí hostovaných služeb, ale můžete ho můžete použít pro jednodušší věci, jako je:</span><span class="sxs-lookup"><span data-stu-id="ae269-123">SignalR is one example of an artifact using hosted services, but you can also use it for much simpler things like:</span></span>

-   <span data-ttu-id="ae269-124">Dotazování databáze hledá změny úlohy na pozadí.</span><span class="sxs-lookup"><span data-stu-id="ae269-124">A background task polling a database looking for changes.</span></span>
-   <span data-ttu-id="ae269-125">Naplánované úlohy pravidelně aktualizuje některé mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="ae269-125">A scheduled task updating some cache periodically.</span></span>
-   <span data-ttu-id="ae269-126">Implementace QueueBackgroundWorkItem umožňující úkol má být proveden na vlákně na pozadí.</span><span class="sxs-lookup"><span data-stu-id="ae269-126">An implementation of QueueBackgroundWorkItem that allows a task to be executed on a background thread.</span></span>
-   <span data-ttu-id="ae269-127">Zpracování zpráv z fronty zpráv z webové aplikace na pozadí při sdílení běžné služby jako například `ILogger`.</span><span class="sxs-lookup"><span data-stu-id="ae269-127">Processing messages from a message queue in the background of a web app while sharing common services such as `ILogger`.</span></span>
-   <span data-ttu-id="ae269-128">Spustit úlohu na pozadí s `Task.Run()`.</span><span class="sxs-lookup"><span data-stu-id="ae269-128">A background task started with `Task.Run()`.</span></span>

<span data-ttu-id="ae269-129">V podstatě můžete přesměrovat některou z těchto akcí pro úlohu na pozadí podle IHostedService.</span><span class="sxs-lookup"><span data-stu-id="ae269-129">You can basically offload any of those actions to a background task based on IHostedService.</span></span>

<span data-ttu-id="ae269-130">Způsob, jak přidat jeden nebo více `IHostedServices` do vaší `WebHost` nebo `Host` je tak, že je zaregistrujete si prostřednictvím standardních DI (injektáž závislostí) v ASP.NET Core `WebHost` (nebo `Host` v .NET Core 2.1 a vyšší).</span><span class="sxs-lookup"><span data-stu-id="ae269-130">The way you add one or multiple `IHostedServices` into your `WebHost` or `Host` is by registering them up through the standard DI (dependency injection) in an ASP.NET Core `WebHost` (or in a `Host` in .NET Core 2.1 and above).</span></span> <span data-ttu-id="ae269-131">V podstatě, je nutné provést registraci hostovaných služeb v rámci známé `ConfigureServices()` metodu `Startup` třídy, jako v následujícím kódu z typických tomuto webovému hostiteli technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ae269-131">Basically, you have to register the hosted services within the familiar `ConfigureServices()` method of the `Startup` class, as in the following code from a typical ASP.NET WebHost.</span></span> 

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

<span data-ttu-id="ae269-132">V tomto kódu `GracePeriodManagerService` hostovanou službu je z mikroslužeb obchodní řazení v aplikaci eShopOnContainers skutečného kódu, ale jiné dva jsou jenom dvě další ukázky.</span><span class="sxs-lookup"><span data-stu-id="ae269-132">In that code, the `GracePeriodManagerService` hosted service is real code from the Ordering business microservice in eShopOnContainers, while the other two are just two additional samples.</span></span>

<span data-ttu-id="ae269-133">`IHostedService` Provedení úlohy na pozadí se koordinují s životního cyklu aplikací (hostitele nebo mikroslužeb, k tomuto účelu).</span><span class="sxs-lookup"><span data-stu-id="ae269-133">The `IHostedService` background task execution is coordinated with the lifetime of the application (host or microservice, for that matter).</span></span> <span data-ttu-id="ae269-134">Zaregistrujete úlohy při spuštění aplikace a budete mít příležitost provést určitou akci řádné nebo čištění po aplikaci se vypíná.</span><span class="sxs-lookup"><span data-stu-id="ae269-134">You register tasks when the application starts and you have the opportunity to do some graceful action or clean-up when the application is shutting down.</span></span>

<span data-ttu-id="ae269-135">Bez použití `IHostedService`, může vždy spustit vlákno na pozadí ke spuštění každého úkolu.</span><span class="sxs-lookup"><span data-stu-id="ae269-135">Without using `IHostedService`, you could always start a background thread to run any task.</span></span> <span data-ttu-id="ae269-136">Rozdíl je přesně v době vypnutí aplikace, kdy bylo vlákno by jednoduše ukončeny bez nutnosti příležitosti ke spouštění řádné akcí čištění.</span><span class="sxs-lookup"><span data-stu-id="ae269-136">The difference is precisely at the app’s shutdown time when that thread would simply be killed without having the opportunity to run graceful clean-up actions.</span></span>

## <a name="the-ihostedservice-interface"></a><span data-ttu-id="ae269-137">Rozhraní IHostedService</span><span class="sxs-lookup"><span data-stu-id="ae269-137">The IHostedService interface</span></span>

<span data-ttu-id="ae269-138">Když se zaregistrujete `IHostedService`, zavolá .NET Core `StartAsync()` a `StopAsync()` metody vaše `IHostedService` zadejte při spuštění aplikace a zastavit v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ae269-138">When you register an `IHostedService`, .NET Core will call the `StartAsync()` and `StopAsync()` methods of your `IHostedService` type during application start and stop respectively.</span></span> <span data-ttu-id="ae269-139">Konkrétně start se volá, když server spuštěn a `IApplicationLifetime.ApplicationStarted` se aktivuje.</span><span class="sxs-lookup"><span data-stu-id="ae269-139">Specifically, start is called after the server has started and `IApplicationLifetime.ApplicationStarted` is triggered.</span></span>

<span data-ttu-id="ae269-140">`IHostedService` Jak jsou definovány v .NET Core, vypadá podobně jako následující.</span><span class="sxs-lookup"><span data-stu-id="ae269-140">The `IHostedService` as defined in .NET Core, looks like the following.</span></span>

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
<span data-ttu-id="ae269-141">Jak si dokážete představit, můžete vytvořit více implementací IHostedService a zaregistrujte je v `ConfigureService()` metoda do kontejnerů DI, jak bylo uvedeno výše.</span><span class="sxs-lookup"><span data-stu-id="ae269-141">As you can imagine, you can create multiple implementations of IHostedService and register them at the `ConfigureService()` method into the DI container, as shown previously.</span></span> <span data-ttu-id="ae269-142">Všechny tyto hostované služby se a zastavování spolu s aplikací/mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="ae269-142">All those hosted services will be started and stopped along with the application/microservice.</span></span>

<span data-ttu-id="ae269-143">Jako vývojář je zodpovědná za zpracování akce zastavení nebo služby při `StopAsync()` metoda aktivuje hostitele.</span><span class="sxs-lookup"><span data-stu-id="ae269-143">As a developer, you are responsible for handling the stopping action or your services when `StopAsync()` method is triggered by the host.</span></span>

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a><span data-ttu-id="ae269-144">Implementace IHostedService pomocí vlastní hostované služby třídu odvozenou z BackgroundService základní třídy</span><span class="sxs-lookup"><span data-stu-id="ae269-144">Implementing IHostedService with a custom hosted service class deriving from the BackgroundService base class</span></span>

<span data-ttu-id="ae269-145">Můžete pokračovat a vytvoření zcela nové třídě vlastní hostovanou službu a implementovat `IHostedService`, jako je třeba provést při použití .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="ae269-145">You could go ahead and create your custom hosted service class from scratch and implement the `IHostedService`, as you need to do when using .NET Core 2.0.</span></span> 

<span data-ttu-id="ae269-146">Protože většina úloh na pozadí mají podobné potřeby správy tokeny zrušení a další běžné operace, neexistuje však vhodné abstraktní základní třídu lze odvodit z, s názvem `BackgroundService` (dostupné od verze rozhraní .NET Core 2.1).</span><span class="sxs-lookup"><span data-stu-id="ae269-146">However, since most background tasks will have similar needs in regard to the cancellation tokens management and other typical operations, there is a convenient abstract base class you can derive from, named `BackgroundService` (available since .NET Core 2.1).</span></span>

<span data-ttu-id="ae269-147">Tuto třídu poskytuje hlavní práce potřebné k nastavení úlohy na pozadí.</span><span class="sxs-lookup"><span data-stu-id="ae269-147">That class provides the main work needed to set up the background task.</span></span>

<span data-ttu-id="ae269-148">Následující kód je abstraktní základní třída BackgroundService, jak je implementován v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ae269-148">The next code is the abstract BackgroundService base class as implemented in .NET Core.</span></span>

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

<span data-ttu-id="ae269-149">Při odvozování z předchozí abstraktní základní třída, díky zděděná implementace, stačí k implementaci `ExecuteAsync()` metoda ve vlastní hostované třídy služby, viz následující příklad zjednodušená kódu v aplikaci eShopOnContainers, což je interval dotazování databáze a publikování události integrace do sběrnice událostí v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="ae269-149">When deriving from the previous abstract base class, thanks to that inherited implementation, you just need to implement the `ExecuteAsync()` method in your own custom hosted service class, as in the following simplified code from eShopOnContainers which is polling a database and publishing integration events into the Event Bus when needed.</span></span>

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

    .../...
}
```

<span data-ttu-id="ae269-150">V tomto konkrétním případě pro aplikaci eShopOnContainers je prováděna metodu aplikace, který se dotazuje tabulku databáze hledá objednávky se specifickým stavem, a při použití změn, je publikování události integrace přes Service bus událostí (pod tím může být s použitím RabbitMQ nebo Azure Service Bus).</span><span class="sxs-lookup"><span data-stu-id="ae269-150">In this specific case for eShopOnContainers, it's executing an application method that's querying a database table looking for orders with a specific state and when applying changes, it is publishing integration events through the event bus (underneath it can be using RabbitMQ or Azure Service Bus).</span></span>

<span data-ttu-id="ae269-151">Samozřejmě můžete spustit žádné jiné obchodní úlohy na pozadí, místo toho.</span><span class="sxs-lookup"><span data-stu-id="ae269-151">Of course, you could run any other business background task, instead.</span></span>

<span data-ttu-id="ae269-152">Ve výchozím nastavení, token rušení, který je nastavena s 5 druhý časový limit, i když tuto hodnotu můžete změnit při sestavování vašich `WebHost` pomocí `UseShutdownTimeout` rozšíření `IWebHostBuilder`.</span><span class="sxs-lookup"><span data-stu-id="ae269-152">By default, the cancellation token is set with a 5 second timeout, although you can change that value when building your `WebHost` using the `UseShutdownTimeout` extension of the `IWebHostBuilder`.</span></span> <span data-ttu-id="ae269-153">To znamená, že naše služby má zrušit v rámci jinak 5 sekund více náhlé ukončení dojde.</span><span class="sxs-lookup"><span data-stu-id="ae269-153">This means that our service is expected to cancel within 5 seconds otherwise it will be more abruptly killed.</span></span>

<span data-ttu-id="ae269-154">Následující kód by změna této doby na 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="ae269-154">The following code would be changing that time to 10 seconds.</span></span>

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a><span data-ttu-id="ae269-155">Třída shrnutí diagramu</span><span class="sxs-lookup"><span data-stu-id="ae269-155">Summary class diagram</span></span>

<span data-ttu-id="ae269-156">Následující obrázek ukazuje vizuál přehled tříd a připojený používané při implementaci IHostedServices.</span><span class="sxs-lookup"><span data-stu-id="ae269-156">The following image shows a visual summary of the classes and interfaced involved when implementing IHostedServices.</span></span>
 
![Diagram tříd: Mnoho služeb, které dědí nastavení z BackgroundService, která implementuje IHostedService můžete hostovat IWebHost a IHost.](./media/image27.png)

<span data-ttu-id="ae269-158">**Obrázek 6 – 27**.</span><span class="sxs-lookup"><span data-stu-id="ae269-158">**Figure 6-27**.</span></span> <span data-ttu-id="ae269-159">Diagram tříd zobrazující více tříd a rozhraní související s IHostedService</span><span class="sxs-lookup"><span data-stu-id="ae269-159">Class diagram showing the multiple classes and interfaces related to IHostedService</span></span>

### <a name="deployment-considerations-and-takeaways"></a><span data-ttu-id="ae269-160">Důležité informace o nasazení a takeaways</span><span class="sxs-lookup"><span data-stu-id="ae269-160">Deployment considerations and takeaways</span></span>

<span data-ttu-id="ae269-161">Je důležité si uvědomit, že způsob nasazení ASP.NET Core `WebHost` nebo .NET Core `Host` může mít vliv na konečné řešení.</span><span class="sxs-lookup"><span data-stu-id="ae269-161">It is important to note that the way you deploy your ASP.NET Core `WebHost` or .NET Core `Host` might impact the final solution.</span></span> <span data-ttu-id="ae269-162">Například při nasazení vaší `WebHost` na serveru IIS nebo pravidelné službě Azure App Service, může být vypnut hostitele kvůli recyklace fondu aplikací.</span><span class="sxs-lookup"><span data-stu-id="ae269-162">For instance, if you deploy your `WebHost` on IIS or a regular Azure App Service, your host can be shut down because of app pool recycles.</span></span> <span data-ttu-id="ae269-163">Ale pokud nasazujete hostitele jako kontejner do orchestrátoru, jako je Kubernetes nebo Service Fabric, můžete řídit pojištěných počet instancí za provozu z hostitele.</span><span class="sxs-lookup"><span data-stu-id="ae269-163">But if you are deploying your host as a container into an orchestrator like Kubernetes or Service Fabric, you can control the assured number of live instances of your host.</span></span> <span data-ttu-id="ae269-164">Kromě toho zvažte další přístupy v cloudu, zejména provedené pro tyto scénáře, jako je Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="ae269-164">In addition, you could consider other approaches in the cloud especially made for these scenarios, like Azure Functions.</span></span> <span data-ttu-id="ae269-165">Nakonec pokud potřebujete služby běžet neustále a provádíte nasazení na Windows serveru můžete použít službu Windows.</span><span class="sxs-lookup"><span data-stu-id="ae269-165">Finally, if you need the service to be running all the time and are deploying on a Windows Server you could use a Windows Service.</span></span>

<span data-ttu-id="ae269-166">Ale i pro `WebHost` nasazené do fondu aplikací, jsou scénáře, jako jsou opětovného vyplnění nebo vyprazdňování mezipaměti v paměti aplikace, která bude i nadále použitelná.</span><span class="sxs-lookup"><span data-stu-id="ae269-166">But even for a `WebHost` deployed into an app pool, there are scenarios like repopulating or flushing application’s in-memory cache, that would be still applicable.</span></span>

<span data-ttu-id="ae269-167">`IHostedService` Rozhraní poskytuje pohodlný způsob, jak spustit úlohy na pozadí v ASP.NET Core webovou aplikaci (v .NET Core 2.0) nebo v procesu/hostitele (počínaje verzí .NET Core 2.1 s `IHost`).</span><span class="sxs-lookup"><span data-stu-id="ae269-167">The `IHostedService` interface provides a convenient way to start background tasks in an ASP.NET Core web application (in .NET Core 2.0) or in any process/host (starting in .NET Core 2.1 with `IHost`).</span></span> <span data-ttu-id="ae269-168">Jeho hlavní výhodou je příležitost, kterou dostanete s řádné zrušení na kód pro vyčištění vaše úlohy na pozadí, když se vypíná samotného hostitele.</span><span class="sxs-lookup"><span data-stu-id="ae269-168">Its main benefit is the opportunity you get with the graceful cancellation to clean-up code of your background tasks when the host itself is shutting down.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="ae269-169">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="ae269-169">Additional resources</span></span>

-   <span data-ttu-id="ae269-170">**Vytvoření naplánované úlohy v technologii ASP.NET Core/Standard 2.0**</span><span class="sxs-lookup"><span data-stu-id="ae269-170">**Building a scheduled task in ASP.NET Core/Standard 2.0**</span></span> <br/>
    [*https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html*](https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html)

-   <span data-ttu-id="ae269-171">**Implementace IHostedService v ASP.NET Core 2.0**</span><span class="sxs-lookup"><span data-stu-id="ae269-171">**Implementing IHostedService in ASP.NET Core 2.0**</span></span> <br/>
    [*https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice*](https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice)

-   <span data-ttu-id="ae269-172">**Ukázka GenericHost pomocí ASP.NET Core 2.1**</span><span class="sxs-lookup"><span data-stu-id="ae269-172">**GenericHost Sample using ASP.NET Core 2.1**</span></span> <br/>
    [*https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample*](https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample)

>[!div class="step-by-step"]
><span data-ttu-id="ae269-173">[Předchozí](test-aspnet-core-services-web-apps.md)
>[další](implement-api-gateways-with-ocelot.md)</span><span class="sxs-lookup"><span data-stu-id="ae269-173">[Previous](test-aspnet-core-services-web-apps.md)
[Next](implement-api-gateways-with-ocelot.md)</span></span>
