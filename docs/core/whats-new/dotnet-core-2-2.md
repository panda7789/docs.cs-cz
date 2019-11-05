---
title: Co je nového v .NET Core 2.2
description: Přečtěte si o nových funkcích, které najdete v .NET Core 2,2.
dev_langs:
- csharp
- vb
ms.date: 12/04/2018
ms.openlocfilehash: 917b51e0cf36cca45135fda4a084eb2bca62e835
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73100696"
---
# <a name="whats-new-in-net-core-22"></a><span data-ttu-id="b239b-103">Co je nového v .NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="b239b-103">What's new in .NET Core 2.2</span></span>

<span data-ttu-id="b239b-104">.NET Core 2,2 obsahuje vylepšení při nasazení aplikace, zpracování událostí pro služby runtime, ověřování pro Azure SQL Database, výkon kompilátoru JIT a vkládání kódu před provedením metody `Main`.</span><span class="sxs-lookup"><span data-stu-id="b239b-104">.NET Core 2.2 includes enhancements in application deployment, event handling for runtime services, authentication to Azure SQL databases, JIT compiler performance, and code injection prior to the execution of the `Main` method.</span></span>

## <a name="new-deployment-mode"></a><span data-ttu-id="b239b-105">Nový režim nasazení</span><span class="sxs-lookup"><span data-stu-id="b239b-105">New deployment mode</span></span>

<span data-ttu-id="b239b-106">Počínaje rozhraním .NET Core 2,2 můžete nasadit [spustitelné soubory závislé na rozhraních](../deploying/index.md#framework-dependent-executables-fde), které jsou soubory **. exe** namísto souborů **. dll** .</span><span class="sxs-lookup"><span data-stu-id="b239b-106">Starting with .NET Core 2.2, you can deploy [framework-dependent executables](../deploying/index.md#framework-dependent-executables-fde), which are **.exe** files instead of **.dll** files.</span></span> <span data-ttu-id="b239b-107">Funguje podobně jako u nasazení závislých na rozhraních, v závislosti na architektuře (FDE) se pořád spoléhá na přítomnost sdílené systémové verze .NET Core, která se má spustit.</span><span class="sxs-lookup"><span data-stu-id="b239b-107">Functionally similar to framework-dependent deployments, framework-dependent executables (FDE) still rely on the presence of a shared system-wide version of .NET Core to run.</span></span> <span data-ttu-id="b239b-108">Vaše aplikace obsahuje jenom váš kód a všechny závislosti třetích stran.</span><span class="sxs-lookup"><span data-stu-id="b239b-108">Your app contains only your code and any third-party dependencies.</span></span> <span data-ttu-id="b239b-109">Na rozdíl od nasazení závislých na rozhraních FDEs jsou specifické pro platformu.</span><span class="sxs-lookup"><span data-stu-id="b239b-109">Unlike framework-dependent deployments, FDEs are platform-specific.</span></span>

<span data-ttu-id="b239b-110">Tento nový režim nasazení má odlišnou výhodu při vytváření spustitelného souboru místo knihovny, což znamená, že můžete svou aplikaci spustit přímo, aniž byste vyvolali `dotnet` jako první.</span><span class="sxs-lookup"><span data-stu-id="b239b-110">This new deployment mode has the distinct advantage of building an executable instead of a library, which means you can run your app directly without invoking `dotnet` first.</span></span>

## <a name="core"></a><span data-ttu-id="b239b-111">Jádro</span><span class="sxs-lookup"><span data-stu-id="b239b-111">Core</span></span>

<span data-ttu-id="b239b-112">**Zpracování událostí ve službách za běhu**</span><span class="sxs-lookup"><span data-stu-id="b239b-112">**Handling events in runtime services**</span></span>

<span data-ttu-id="b239b-113">Chcete-li pochopit, jak ovlivňují vaši aplikaci, může být často vhodné monitorovat použití služeb runtime, jako je například GC, JIT, a nevlákenná vlákna.</span><span class="sxs-lookup"><span data-stu-id="b239b-113">You may often want to monitor your application's use of runtime services, such as the GC, JIT, and ThreadPool, to understand how they impact your application.</span></span><span data-ttu-id="b239b-114"> V systémech Windows to se obvykle provádí monitorováním událostí ETW aktuálního procesu.</span><span class="sxs-lookup"><span data-stu-id="b239b-114"> On Windows systems, this is commonly done by monitoring the ETW events of the current process.</span></span><span data-ttu-id="b239b-115"> I když to bude i nadále fungovat dobře, není vždy možné používat trasování událostí pro Windows, pokud pracujete v prostředí s nízkým oprávněním nebo v systému Linux nebo macOS.</span><span class="sxs-lookup"><span data-stu-id="b239b-115"> While this continues to work well, it's not always possible to use ETW if you're running in a low-privilege environment or on Linux or macOS.</span></span> 

<span data-ttu-id="b239b-116">Počínaje .NET Core 2,2 události CoreCLR se teď dají spotřebovat pomocí třídy <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b239b-116">Starting with .NET Core 2.2, CoreCLR events can now be consumed using the <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="b239b-117">Tyto události popisují chování takových služeb za běhu jako GC, JIT, fondu a spolupráci.</span><span class="sxs-lookup"><span data-stu-id="b239b-117">These events describe the behavior of such runtime services as GC, JIT, ThreadPool, and interop.</span></span> <span data-ttu-id="b239b-118">Jedná se o stejné události, které jsou přístupné jako součást zprostředkovatele ETW CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="b239b-118">These are the same events that are exposed as part of the CoreCLR ETW provider.</span></span><span data-ttu-id="b239b-119">  Díky tomu můžou aplikace tyto události spotřebovat nebo použít transportní mechanismus k jejich posílání do agregační služby telemetrie.</span><span class="sxs-lookup"><span data-stu-id="b239b-119">  This allows for applications to consume these events or use a transport mechanism to send them to a telemetry aggregation service.</span></span> <span data-ttu-id="b239b-120">Můžete se podívat, jak se přihlásit k odběru událostí v následující ukázce kódu:</span><span class="sxs-lookup"><span data-stu-id="b239b-120">You can see how to subscribe to events in the following code sample:</span></span>

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

<span data-ttu-id="b239b-121">Kromě toho .NET Core 2,2 přidá následující dvě vlastnosti do třídy <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> k poskytnutí dalších informací o událostech ETW:</span><span class="sxs-lookup"><span data-stu-id="b239b-121">In addition, .NET Core 2.2 adds the following two properties to the <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> class to provide additional information about ETW events:</span></span>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.OSThreadId?displayProperty=nameWithType>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.TimeStamp?displayProperty=nameWithType>

## <a name="data"></a><span data-ttu-id="b239b-122">Data</span><span class="sxs-lookup"><span data-stu-id="b239b-122">Data</span></span>

<span data-ttu-id="b239b-123">**Ověřování AAD pro databáze SQL Azure s vlastností SqlConnection. AccessToken**</span><span class="sxs-lookup"><span data-stu-id="b239b-123">**AAD authentication to Azure SQL databases with the SqlConnection.AccessToken property**</span></span>

<span data-ttu-id="b239b-124">Počínaje rozhraním .NET Core 2,2 je možné k ověřování ve službě Azure SQL Database použít přístupový token vydaný Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="b239b-124">Starting with .NET Core 2.2, an access token issued by Azure Active Directory can be used to authenticate to an Azure SQL database.</span></span> <span data-ttu-id="b239b-125">Pro podporu přístupových tokenů byla vlastnost <xref:System.Data.SqlClient.SqlConnection.AccessToken> přidána do třídy <xref:System.Data.SqlClient.SqlConnection>.</span><span class="sxs-lookup"><span data-stu-id="b239b-125">To support access tokens, the <xref:System.Data.SqlClient.SqlConnection.AccessToken> property has been added to the <xref:System.Data.SqlClient.SqlConnection> class.</span></span> <span data-ttu-id="b239b-126">Pokud chcete využít výhod ověřování AAD, Stáhněte si balíček NuGet System. data. SqlClient verze 4,6.</span><span class="sxs-lookup"><span data-stu-id="b239b-126">To take advantage of AAD authentication, download version 4.6 of the System.Data.SqlClient NuGet package.</span></span> <span data-ttu-id="b239b-127">Aby bylo možné funkci používat, můžete získat hodnotu přístupového tokenu pomocí [Active Directory Authentication Library pro .NET](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) , které jsou obsaženy v balíčku NuGet [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) .</span><span class="sxs-lookup"><span data-stu-id="b239b-127">In order to use the feature, you can obtain the access token value using the [Active Directory Authentication Library for .NET](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) contained in the [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet package.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="b239b-128">Vylepšení kompilátoru JIT</span><span class="sxs-lookup"><span data-stu-id="b239b-128">JIT compiler improvements</span></span>

<span data-ttu-id="b239b-129">**Vrstvená kompilace zůstává funkcí výslovných přihlášení.**</span><span class="sxs-lookup"><span data-stu-id="b239b-129">**Tiered compilation remains an opt-in feature**</span></span>

<span data-ttu-id="b239b-130">V .NET Core 2,1 kompilátor JIT implementoval novou technologii kompilátoru, *vrstvenou kompilaci*, jako funkci opt-in.</span><span class="sxs-lookup"><span data-stu-id="b239b-130">In .NET Core 2.1, the JIT compiler implemented a new compiler technology, *tiered compilation*, as an opt-in feature.</span></span> <span data-ttu-id="b239b-131">Cílem vrstvené kompilace je zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="b239b-131">The goal of tiered compilation is improved performance.</span></span> <span data-ttu-id="b239b-132">Jedním z důležitých úloh prováděných kompilátorem JIT je optimalizace provádění kódu.</span><span class="sxs-lookup"><span data-stu-id="b239b-132">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="b239b-133">Pro málo používané cesty kódu však může kompilátor strávit více času optimalizací kódu, než modul runtime zpracovává neoptimalizovaný kód.</span><span class="sxs-lookup"><span data-stu-id="b239b-133">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends executing unoptimized code.</span></span> <span data-ttu-id="b239b-134">Vrstvená kompilace přináší dvě fáze kompilace JIT:</span><span class="sxs-lookup"><span data-stu-id="b239b-134">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="b239b-135">**První vrstva**, která generuje kód co nejrychleji.</span><span class="sxs-lookup"><span data-stu-id="b239b-135">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="b239b-136">**Druhá vrstva**, která generuje optimalizovaný kód pro tyto metody, které jsou spouštěny často.</span><span class="sxs-lookup"><span data-stu-id="b239b-136">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="b239b-137">Druhá vrstva kompilace se paralelně provádí za účelem zvýšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="b239b-137">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="b239b-138">Informace o vylepšení výkonu, které může být výsledkem vrstvené kompilace, najdete v tématu [oznamujeme rozhraní .NET Core 2,2 Preview 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).</span><span class="sxs-lookup"><span data-stu-id="b239b-138">For information on the performance improvement that can result from tiered compilation, see [Announcing .NET Core 2.2 Preview 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).</span></span>

<span data-ttu-id="b239b-139">Ve výchozím nastavení je v .NET Core 2,2 Preview 2 zapnutá vrstvená kompilace.</span><span class="sxs-lookup"><span data-stu-id="b239b-139">In .NET Core 2.2 Preview 2, tiered compilation was enabled by default.</span></span> <span data-ttu-id="b239b-140">Rozhodli jsme se však, že ve výchozím nastavení není stále připraveno povolit vrstvenou kompilaci.</span><span class="sxs-lookup"><span data-stu-id="b239b-140">However, we've decided that we are still not ready to enable tiered compilation by default.</span></span> <span data-ttu-id="b239b-141">Takže v .NET Core 2,2 se vrstvená kompilace bude i nadále jednat o funkci výslovného souhlasu.</span><span class="sxs-lookup"><span data-stu-id="b239b-141">So in .NET Core 2.2, tiered compilation continues to be an opt-in feature.</span></span> <span data-ttu-id="b239b-142">Informace o tom, jak se na vrstvenou kompilaci rozvrstvit, najdete v tématu [vylepšení kompilátoru JIT](dotnet-core-2-1.md#jit-compiler-improvements) v tématu [co je nového v .NET Core 2,1](dotnet-core-2-1.md).</span><span class="sxs-lookup"><span data-stu-id="b239b-142">For information on opting in to tiered compilation, see [Jit compiler improvements](dotnet-core-2-1.md#jit-compiler-improvements) in [What's new in .NET Core 2.1](dotnet-core-2-1.md).</span></span>

## <a name="runtime"></a><span data-ttu-id="b239b-143">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="b239b-143">Runtime</span></span>

<span data-ttu-id="b239b-144">**Vložení kódu před provedením metody Main**</span><span class="sxs-lookup"><span data-stu-id="b239b-144">**Injecting code prior to executing the Main method**</span></span>

<span data-ttu-id="b239b-145">Počínaje .NET Core 2,2 můžete použít spouštěcí zavěšení pro vložení kódu před spuštěním metody Main aplikace.</span><span class="sxs-lookup"><span data-stu-id="b239b-145">Starting with .NET Core 2.2, you can use a startup hook to inject code prior to running an application's Main method.</span></span> <span data-ttu-id="b239b-146">Spouštěcí háky umožňují hostiteli přizpůsobit chování aplikací poté, co byly nasazeny, aniž by museli aplikaci znovu kompilovat nebo měnit.</span><span class="sxs-lookup"><span data-stu-id="b239b-146">Startup hooks make it possible for a host to customize the behavior of applications after they have been deployed without needing to recompile or change the application.</span></span>

<span data-ttu-id="b239b-147">Očekáváme, že poskytovatelé hostingu definují vlastní konfiguraci a zásady, včetně nastavení, která mohou mít vliv na chování při načítání hlavního vstupního bodu, například <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> chování.</span><span class="sxs-lookup"><span data-stu-id="b239b-147">We expect hosting providers to define custom configuration and policy, including settings that potentially influence the load behavior of the main entry point, such as the <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> behavior.</span></span> <span data-ttu-id="b239b-148">Zavěšení lze použít k nastavení trasování nebo injektáže telemetrie, k nastavení zpětných volání pro zpracování nebo k definování jiného chování závislého na prostředí.</span><span class="sxs-lookup"><span data-stu-id="b239b-148">The hook can be used to set up tracing or telemetry injection, to set up callbacks for handling, or to define other environment-dependent behavior.</span></span> <span data-ttu-id="b239b-149">Zavěšení je oddělené od vstupního bodu, aby se kód uživatele nemuselo upravovat.</span><span class="sxs-lookup"><span data-stu-id="b239b-149">The hook is separate from the entry point, so that user code doesn't need to be modified.</span></span>

<span data-ttu-id="b239b-150">Další informace najdete v tématu [spouštěcí zavěšení hostitele](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) .</span><span class="sxs-lookup"><span data-stu-id="b239b-150">See [Host startup hook](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="b239b-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b239b-151">See also</span></span>

- [<span data-ttu-id="b239b-152">Co je nového v .NET Core</span><span class="sxs-lookup"><span data-stu-id="b239b-152">What's new in .NET Core</span></span>](index.md)
- [<span data-ttu-id="b239b-153">Co je nového v ASP.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="b239b-153">What's new in ASP.NET Core 2.2</span></span>](/aspnet/core/release-notes/aspnetcore-2.2)
- [<span data-ttu-id="b239b-154">Nové funkce v EF Core 2,2</span><span class="sxs-lookup"><span data-stu-id="b239b-154">New features in EF Core 2.2</span></span>](/ef/core/what-is-new/ef-core-2.2)
