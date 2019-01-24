---
title: Co je nového v .NET Core 2.2
description: Informace o nových funkcích v rozhraní .NET Core 2.2.
dev_langs:
- csharp
- vb
author: rpetrusha
ms.author: ronpet
ms.date: 12/04/2018
ms.openlocfilehash: 058e7ee1dc834ff23a9a4aa191f7eaeb1016375c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679774"
---
# <a name="whats-new-in-net-core-22"></a><span data-ttu-id="37164-103">Co je nového v .NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="37164-103">What's new in .NET Core 2.2</span></span>

<span data-ttu-id="37164-104">.NET core 2.2 zahrnuje vylepšení v nasazení aplikací, zpracování událostí pro služby modulu runtime, ověřování pro Azure SQL Database, výkon kompilátoru JIT a injektáž kódu před spuštěním `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="37164-104">.NET Core 2.2 includes enhancements in application deployment, event handling for runtime services, authentication to Azure SQL databases, JIT compiler performance, and code injection prior to the execution of the `Main` method.</span></span>

## <a name="new-deployment-mode"></a><span data-ttu-id="37164-105">Nový režim nasazení</span><span class="sxs-lookup"><span data-stu-id="37164-105">New deployment mode</span></span>

<span data-ttu-id="37164-106">Spouští se s nástroji .NET Core 2.2, můžete nasadit [závisí na architektuře spustitelných souborů](../deploying/index.md#framework-dependent-executables-fde), které jsou **.exe** soubory místo **.dll** soubory.</span><span class="sxs-lookup"><span data-stu-id="37164-106">Starting with .NET Core 2.2, you can deploy [framework-dependent executables](../deploying/index.md#framework-dependent-executables-fde), which are **.exe** files instead of **.dll** files.</span></span> <span data-ttu-id="37164-107">Funkčně podobný nasazení závisí na architektuře, závisí na architektuře spustitelných souborů (FDE) stále spoléhat na přítomnost sdílené systémová verzi .NET Core pro spuštění.</span><span class="sxs-lookup"><span data-stu-id="37164-107">Functionally similar to framework-dependent deployments, framework-dependent executables (FDE) still rely on the presence of a shared system-wide version of .NET Core to run.</span></span> <span data-ttu-id="37164-108">Vaše aplikace obsahuje pouze váš kód a případných závislostí třetích stran.</span><span class="sxs-lookup"><span data-stu-id="37164-108">Your app contains only your code and any third-party dependencies.</span></span> <span data-ttu-id="37164-109">Na rozdíl od nasazení závisí na architektuře FDEs jsou specifické pro platformu.</span><span class="sxs-lookup"><span data-stu-id="37164-109">Unlike framework-dependent deployments, FDEs are platform-specific.</span></span>

<span data-ttu-id="37164-110">Tento nový režim nasazení má odlišné výhod sestavení spustitelného souboru namísto knihovny, což znamená, že spustíte svou aplikaci přímo bez vyvolání `dotnet` první.</span><span class="sxs-lookup"><span data-stu-id="37164-110">This new deployment mode has the distinct advantage of building an executable instead of a library, which means you can run your app directly without invoking `dotnet` first.</span></span>

## <a name="core"></a><span data-ttu-id="37164-111">Jádro</span><span class="sxs-lookup"><span data-stu-id="37164-111">Core</span></span>

<span data-ttu-id="37164-112">**Zpracování událostí v modulu runtime služeb**</span><span class="sxs-lookup"><span data-stu-id="37164-112">**Handling events in runtime services**</span></span>

<span data-ttu-id="37164-113">Často můžete chtít sledovat vaše aplikace při používání služby modulu runtime, jako je například uvolňování paměti, JIT a fondu vláken, abyste pochopili, jak by mohly mít dopad vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="37164-113">You may often want to monitor your application's use of runtime services, such as the GC, JIT, and ThreadPool, to understand how they impact your application.</span></span><span data-ttu-id="37164-114"> V systémech Windows obvykle stačí monitorování událostí trasování událostí pro Windows aktuálního procesu.</span><span class="sxs-lookup"><span data-stu-id="37164-114"> On Windows systems, this is commonly done by monitoring the ETW events of the current process.</span></span><span data-ttu-id="37164-115"> I když toto zůstává fungovat dobře, není vždy možné použít trasování událostí pro Windows, pokud používáte v prostředí s nízkou úrovní oprávnění, nebo v Linuxu nebo macOS.</span><span class="sxs-lookup"><span data-stu-id="37164-115"> While this continues to work well, it's not always possible to use ETW if you're running in a low-privilege environment or on Linux or macOS.</span></span>  

<span data-ttu-id="37164-116">Spouští se s nástroji .NET Core 2.2, události CoreCLR se teď dají zpracovat pomocí <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithtype> třídy.</span><span class="sxs-lookup"><span data-stu-id="37164-116">Starting with .NET Core 2.2, CoreCLR events can now be consumed using the <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithtype> class.</span></span> <span data-ttu-id="37164-117">Tyto události popisují chování takové služby modulu runtime jako uvolňování paměti, JIT, fondu vláken a zprostředkovatele komunikace s objekty.</span><span class="sxs-lookup"><span data-stu-id="37164-117">These events describe the behavior of such runtime services as GC, JIT, ThreadPool, and interop.</span></span> <span data-ttu-id="37164-118">Toto jsou stejné události, které části zprostředkovatelů trasování událostí pro Windows CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="37164-118">These are the same events that parts of the CoreCLR ETW provider.</span></span><span data-ttu-id="37164-119">  To umožňuje aplikacím používat tyto události nebo použít mechanismus přenosu k odesílání telemetrických dat služby agregace.</span><span class="sxs-lookup"><span data-stu-id="37164-119">  This allows for applications to consume these events or use a transport mechanism to send them to a telemetry aggregation service.</span></span> <span data-ttu-id="37164-120">Uvidíte jak přihlášení k odběru událostí v následujícím příkladu kódu:</span><span class="sxs-lookup"><span data-stu-id="37164-120">You can see how to subscribe to events in the following code sample:</span></span>

```csharp
internal sealed class SimpleEventListener : EventListener
{
    // Called whenever an EventSource is created.
    protected override void OnEventSourceCreated(EventSource eventSource)
    {
        // Watch for the .NET runtime EventSource and enable all of its events.
        if (eventSource.Name.Equals("Microsoft-Windows-DotNETRuntime"))
        {
            EnableEvents(eventSource, EventLevel.Verbose, (EventKeywords)(-1));
        }
    }

    // Called whenever an event is written.
    protected override void OnEventWritten(EventWrittenEventArgs eventData)
    {
        // Write the contents of the event to the console.
        Console.WriteLine($"ThreadID = {eventData.OSThreadId} ID = {eventData.EventId} Name = {eventData.EventName}");
        for (int i = 0; i < eventData.Payload.Count; i++)
        {
            string payloadString = eventData.Payload[i]?.ToString() ?? string.Empty;
            Console.WriteLine($"\tName = \"{eventData.PayloadNames[i]}\" Value = \"{payloadString}\"");
        }
        Console.WriteLine("\n");
    }
}
```

<span data-ttu-id="37164-121">Kromě toho přidá následující dvě vlastnosti do .NET Core 2.2 <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> třídy lze zadat další informace o trasování událostí pro Windows:</span><span class="sxs-lookup"><span data-stu-id="37164-121">In addition, .NET Core 2.2 adds the following two properties to the <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> class to provide additional information about ETW events:</span></span>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.OSThreadId?displayProperty=nameWithType>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.TimeStamp?displayProperty=nameWithType>

## <a name="data"></a><span data-ttu-id="37164-122">Data</span><span class="sxs-lookup"><span data-stu-id="37164-122">Data</span></span>

<span data-ttu-id="37164-123">**Ověřování AAD k databázím Azure SQL s vlastností SqlConnection.AccessToken**</span><span class="sxs-lookup"><span data-stu-id="37164-123">**AAD authentication to Azure SQL databases with the SqlConnection.AccessToken property**</span></span>

<span data-ttu-id="37164-124">Spouští se s nástroji .NET Core 2.2, přístupový token vydala Azure Active Directory je možné k ověření ke službě Azure SQL database.</span><span class="sxs-lookup"><span data-stu-id="37164-124">Starting with .NET Core 2.2, an access token issued by Azure Active Directory can be used to authenticate to an Azure SQL database.</span></span> <span data-ttu-id="37164-125">Pro podporu přístupových tokenů <xref:System.Data.SqlClient.SqlConnection.AccessToken> byla přidána vlastnost <xref:System.Data.SqlClient.SqlConnection> třídy.</span><span class="sxs-lookup"><span data-stu-id="37164-125">To support access tokens, the <xref:System.Data.SqlClient.SqlConnection.AccessToken> property has been added to the <xref:System.Data.SqlClient.SqlConnection> class.</span></span> <span data-ttu-id="37164-126">Abyste mohli využívat ověřování AAD, stáhněte si verzi 4.6 balíček System.Data.SqlClient NuGet.</span><span class="sxs-lookup"><span data-stu-id="37164-126">To take advantage of AAD authentication, download version 4.6 of the System.Data.SqlClient NuGet package.</span></span> <span data-ttu-id="37164-127">Chcete-li použít funkci, můžete získat přístup pomocí tokenu hodnotu [Active Directory Authentication Library pro .NET](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) součástí [ `Microsoft.IdentityModel.Clients.ActiveDirectory` ](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="37164-127">In order to use the feature, you can obtain the access token value using the [Active Directory Authentication Library for .NET](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) contained in the [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet package.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="37164-128">Vylepšení kompilátoru JIT</span><span class="sxs-lookup"><span data-stu-id="37164-128">JIT compiler improvements</span></span>

<span data-ttu-id="37164-129">**Vrstvené kompilace zůstává funkce opt-in**</span><span class="sxs-lookup"><span data-stu-id="37164-129">**Tiered compilation remains an opt-in feature**</span></span>

<span data-ttu-id="37164-130">V rozhraní .NET Core 2.1, kompilátor JIT implementovat novou technologii kompilátoru *vrstvené kompilace*, jako funkce opt-in.</span><span class="sxs-lookup"><span data-stu-id="37164-130">In .NET Core 2.1, the JIT compiler implemented a new compiler technology, *tiered compilation*, as an opt-in feature.</span></span> <span data-ttu-id="37164-131">Cílem vrstvené kompilace je vylepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="37164-131">The goal of tiered compilation is improved performance.</span></span> <span data-ttu-id="37164-132">Mezi důležité úlohy prováděné kompilátorem JIT je optimalizace spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="37164-132">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="37164-133">Cesty málo používané kódu ale může kompilátor věnovat víc času než modul runtime stráví spuštěním kódu neoptimalizované optimalizace kódu.</span><span class="sxs-lookup"><span data-stu-id="37164-133">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends executing unoptimized code.</span></span> <span data-ttu-id="37164-134">Vrstvené kompilace zavádí dvě fáze kompilace JIT:</span><span class="sxs-lookup"><span data-stu-id="37164-134">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="37164-135">A **první úroveň**, který generuje kód co nejrychleji.</span><span class="sxs-lookup"><span data-stu-id="37164-135">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="37164-136">A **druhé vrstvy**, který generuje optimalizovaný kód pro tyto metody, které jsou spouštěny často.</span><span class="sxs-lookup"><span data-stu-id="37164-136">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="37164-137">Druhá vrstva kompilace provádí paralelní pro lepší výkon.</span><span class="sxs-lookup"><span data-stu-id="37164-137">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="37164-138">Informace o vylepšení výkonu, které můžou být výsledkem kompilace vrstvený, naleznete v tématu [Ohlašujeme .NET Core 2.2 ve verzi Preview 2](https://blogs.msdn.microsoft.com/dotnet/2018/09/12/announcing-net-core-2-2-preview-2/).</span><span class="sxs-lookup"><span data-stu-id="37164-138">For information on the performance improvement that can result from tiered compilation, see [Announcing .NET Core 2.2 Preview 2](https://blogs.msdn.microsoft.com/dotnet/2018/09/12/announcing-net-core-2-2-preview-2/).</span></span> 

<span data-ttu-id="37164-139">V rozhraní .NET Core 2.2 ve verzi Preview 2 vrstvené kompilace byla povolena ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="37164-139">In .NET Core 2.2 Preview 2, tiered compilation was enabled by default.</span></span> <span data-ttu-id="37164-140">Ale jsme jste se rozhodli, že budeme připravení stále není ve výchozím nastavení povolena vrstvené kompilace.</span><span class="sxs-lookup"><span data-stu-id="37164-140">However, we've decided that we are still not ready to enable tiered compilation by default.</span></span> <span data-ttu-id="37164-141">Takže v .NET Core 2.2 vrstvené kompilace nadále funkce opt-in.</span><span class="sxs-lookup"><span data-stu-id="37164-141">So in .NET Core 2.2, tiered compilation continues to be an opt-in feature.</span></span> <span data-ttu-id="37164-142">Informace o vyjádření výslovného souhlasu s vrstvené kompilace, naleznete v tématu [vylepšení kompilátoru Jit](dotnet-core-2-1.md#jit-compiler-improvements) v [co je nového v .NET Core 2.1](dotnet-core-2-1.md).</span><span class="sxs-lookup"><span data-stu-id="37164-142">For information on opting in to tiered compilation, see [Jit compiler improvements](dotnet-core-2-1.md#jit-compiler-improvements) in [What's new in .NET Core 2.1](dotnet-core-2-1.md).</span></span>

## <a name="runtime"></a><span data-ttu-id="37164-143">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="37164-143">Runtime</span></span>

<span data-ttu-id="37164-144">**Vkládání kódu před spuštěním metody Main**</span><span class="sxs-lookup"><span data-stu-id="37164-144">**Injecting code prior to executing the Main method**</span></span>

<span data-ttu-id="37164-145">Spouští se s nástroji .NET Core 2.2, vám pomůže spuštění hook vložení kódu před spuštěním aplikace metodu Main.</span><span class="sxs-lookup"><span data-stu-id="37164-145">Starting with .NET Core 2.2, you can use a startup hook to inject code prior to running an application's Main method.</span></span> <span data-ttu-id="37164-146">Spouštění zachytávání umožňují hostitele po jejich nasazení bez nutnosti znovu kompilovat nebo změnit aplikaci přizpůsobit chování aplikace.</span><span class="sxs-lookup"><span data-stu-id="37164-146">Startup hooks make it possible for a host to customize the behavior of applications after they have been deployed without needing to recompile or change the application.</span></span>

<span data-ttu-id="37164-147">Očekáváme, že poskytovatelům hostingu definovat vlastní konfigurace a zásad, včetně nastavení, které potenciálně ovlivňují chování zatížení hlavní vstupní bod, jako <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> chování.</span><span class="sxs-lookup"><span data-stu-id="37164-147">We expect hosting providers to define custom configuration and policy, including settings that potentially influence the load behavior of the main entry point, such as the <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> behavior.</span></span> <span data-ttu-id="37164-148">Volání je možné nastavit trasování nebo shromažďování telemetrických vkládání, nastavit zpětná volání pro zpracování nebo definovat další chování závislé na prostředí.</span><span class="sxs-lookup"><span data-stu-id="37164-148">The hook can be used to set up tracing or telemetry injection, to set up callbacks for handling, or to define other environment-dependent behavior.</span></span> <span data-ttu-id="37164-149">Volání je oddělené od vstupní bod tak, aby kód uživatele není potřeba upravit.</span><span class="sxs-lookup"><span data-stu-id="37164-149">The hook is separate from the entry point, so that user code doesn't need to be modified.</span></span>

<span data-ttu-id="37164-150">Zobrazit [hook spuštění hostitele](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="37164-150">See [Host startup hook](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="37164-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="37164-151">See also</span></span>

- [<span data-ttu-id="37164-152">Co je nového v .NET Core</span><span class="sxs-lookup"><span data-stu-id="37164-152">What's new in .NET Core</span></span>](index.md)
- [<span data-ttu-id="37164-153">Co je nového v ASP.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="37164-153">What's new in ASP.NET Core 2.2</span></span>](/aspnet/core/release-notes/aspnetcore-2.2)
- [<span data-ttu-id="37164-154">Novinky v EF Core 2.2</span><span class="sxs-lookup"><span data-stu-id="37164-154">New features in EF Core 2.2</span></span>](/ef/core/what-is-new/ef-core-2.2)
