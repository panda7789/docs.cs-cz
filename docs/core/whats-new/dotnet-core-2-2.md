---
title: Co je nového v .NET Core 2.2
description: Další informace o nových funkcích v rozhraní .NET Core 2.2.
dev_langs:
- csharp
- vb
ms.date: 12/04/2018
ms.openlocfilehash: e045c39240c99777d05ca86ee0a8cd1fa4309c4f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156579"
---
# <a name="whats-new-in-net-core-22"></a><span data-ttu-id="72a6b-103">Co je nového v .NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="72a6b-103">What's new in .NET Core 2.2</span></span>

<span data-ttu-id="72a6b-104">.NET Core 2.2 zahrnuje vylepšení v nasazení aplikací, zpracování událostí pro runtime služby, ověřování do databází Azure SQL, výkon kompilátoru JIT a vkládání kódu před spuštěním `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="72a6b-104">.NET Core 2.2 includes enhancements in application deployment, event handling for runtime services, authentication to Azure SQL databases, JIT compiler performance, and code injection prior to the execution of the `Main` method.</span></span>

## <a name="new-deployment-mode"></a><span data-ttu-id="72a6b-105">Nový režim nasazení</span><span class="sxs-lookup"><span data-stu-id="72a6b-105">New deployment mode</span></span>

<span data-ttu-id="72a6b-106">Počínaje rozhraním .NET Core 2.2 můžete nasadit [spustitelné soubory závislé na rozhraní](../deploying/index.md#publish-runtime-dependent), což jsou soubory **EXE** namísto souborů **DLL.**</span><span class="sxs-lookup"><span data-stu-id="72a6b-106">Starting with .NET Core 2.2, you can deploy [framework-dependent executables](../deploying/index.md#publish-runtime-dependent), which are **.exe** files instead of **.dll** files.</span></span> <span data-ttu-id="72a6b-107">Funkčně podobné nasazení závislé na rozhraní, spustitelné soubory závislé na rámci (FDE) stále spoléhají na přítomnost sdílené verze rozhraní .NET Core pro celý systém ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="72a6b-107">Functionally similar to framework-dependent deployments, framework-dependent executables (FDE) still rely on the presence of a shared system-wide version of .NET Core to run.</span></span> <span data-ttu-id="72a6b-108">Vaše aplikace obsahuje pouze váš kód a všechny závislosti třetích stran.</span><span class="sxs-lookup"><span data-stu-id="72a6b-108">Your app contains only your code and any third-party dependencies.</span></span> <span data-ttu-id="72a6b-109">Na rozdíl od nasazení závislých na rámci jsou FTE specifické pro platformu.</span><span class="sxs-lookup"><span data-stu-id="72a6b-109">Unlike framework-dependent deployments, FDEs are platform-specific.</span></span>

<span data-ttu-id="72a6b-110">Tento nový režim nasazení má výraznou výhodu v budování spustitelného souboru namísto knihovny, což znamená, že aplikaci můžete spustit přímo bez vyvolání. `dotnet`</span><span class="sxs-lookup"><span data-stu-id="72a6b-110">This new deployment mode has the distinct advantage of building an executable instead of a library, which means you can run your app directly without invoking `dotnet` first.</span></span>

## <a name="core"></a><span data-ttu-id="72a6b-111">Jádro</span><span class="sxs-lookup"><span data-stu-id="72a6b-111">Core</span></span>

<span data-ttu-id="72a6b-112">**Zpracování událostí ve službách runtime**</span><span class="sxs-lookup"><span data-stu-id="72a6b-112">**Handling events in runtime services**</span></span>

<span data-ttu-id="72a6b-113">Často můžete chtít sledovat použití služeb runtime vaší aplikace, jako je například GC, JIT a ThreadPool, abyste pochopili, jak ovlivňují vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="72a6b-113">You may often want to monitor your application's use of runtime services, such as the GC, JIT, and ThreadPool, to understand how they impact your application.</span></span><span data-ttu-id="72a6b-114">V systémech Windows se to obvykle provádí sledováním událostí ETW aktuálního procesu.</span><span class="sxs-lookup"><span data-stu-id="72a6b-114"> On Windows systems, this is commonly done by monitoring the ETW events of the current process.</span></span><span data-ttu-id="72a6b-115">I když to i nadále funguje dobře, není vždy možné používat ETW, pokud používáte v prostředí s nízkými oprávněními nebo na Linuxu nebo macOS.</span><span class="sxs-lookup"><span data-stu-id="72a6b-115"> While this continues to work well, it's not always possible to use ETW if you're running in a low-privilege environment or on Linux or macOS.</span></span>

<span data-ttu-id="72a6b-116">Počínaje .NET Core 2.2, CoreCLR události lze <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType> nyní spotřebovávat pomocí třídy.</span><span class="sxs-lookup"><span data-stu-id="72a6b-116">Starting with .NET Core 2.2, CoreCLR events can now be consumed using the <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="72a6b-117">Tyto události popisují chování těchto runtime služeb jako GC, JIT, ThreadPool a interop.</span><span class="sxs-lookup"><span data-stu-id="72a6b-117">These events describe the behavior of such runtime services as GC, JIT, ThreadPool, and interop.</span></span> <span data-ttu-id="72a6b-118">Jedná se o stejné události, které jsou vystaveny jako součást poskytovatele CoreCLR ETW.</span><span class="sxs-lookup"><span data-stu-id="72a6b-118">These are the same events that are exposed as part of the CoreCLR ETW provider.</span></span><span data-ttu-id="72a6b-119">To umožňuje aplikacím využívat tyto události nebo použít mechanismus přenosu k jejich odeslání do služby agregace telemetrie.</span><span class="sxs-lookup"><span data-stu-id="72a6b-119">  This allows for applications to consume these events or use a transport mechanism to send them to a telemetry aggregation service.</span></span> <span data-ttu-id="72a6b-120">Můžete vidět, jak se přihlásit k odběru událostí v následující ukázce kódu:</span><span class="sxs-lookup"><span data-stu-id="72a6b-120">You can see how to subscribe to events in the following code sample:</span></span>

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

<span data-ttu-id="72a6b-121">Kromě toho .NET Core 2.2 přidá následující <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> dvě vlastnosti třídy poskytnout další informace o událostech ETW:</span><span class="sxs-lookup"><span data-stu-id="72a6b-121">In addition, .NET Core 2.2 adds the following two properties to the <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> class to provide additional information about ETW events:</span></span>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.OSThreadId?displayProperty=nameWithType>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.TimeStamp?displayProperty=nameWithType>

## <a name="data"></a><span data-ttu-id="72a6b-122">Data</span><span class="sxs-lookup"><span data-stu-id="72a6b-122">Data</span></span>

<span data-ttu-id="72a6b-123">**Ověřování AAD do databází Azure SQL s vlastností SqlConnection.AccessToken**</span><span class="sxs-lookup"><span data-stu-id="72a6b-123">**AAD authentication to Azure SQL databases with the SqlConnection.AccessToken property**</span></span>

<span data-ttu-id="72a6b-124">Počínaje rozhraním .NET Core 2.2 lze přístupový token vydaný službou Azure Active Directory použít k ověření do databáze Azure SQL.</span><span class="sxs-lookup"><span data-stu-id="72a6b-124">Starting with .NET Core 2.2, an access token issued by Azure Active Directory can be used to authenticate to an Azure SQL database.</span></span> <span data-ttu-id="72a6b-125">Pro podporu přístupových <xref:System.Data.SqlClient.SqlConnection.AccessToken> tokenů byla vlastnost <xref:System.Data.SqlClient.SqlConnection> přidána do třídy.</span><span class="sxs-lookup"><span data-stu-id="72a6b-125">To support access tokens, the <xref:System.Data.SqlClient.SqlConnection.AccessToken> property has been added to the <xref:System.Data.SqlClient.SqlConnection> class.</span></span> <span data-ttu-id="72a6b-126">Chcete-li využít výhod ověřování AAD, stáhněte si verzi 4.6 balíčku System.Data.SqlClient NuGet.</span><span class="sxs-lookup"><span data-stu-id="72a6b-126">To take advantage of AAD authentication, download version 4.6 of the System.Data.SqlClient NuGet package.</span></span> <span data-ttu-id="72a6b-127">Chcete-li tuto funkci použít, můžete získat hodnotu přístupového tokenu pomocí [knihovny ověřování služby Active Directory pro rozhraní .NET](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) obsažené v balíčku [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet.</span><span class="sxs-lookup"><span data-stu-id="72a6b-127">In order to use the feature, you can obtain the access token value using the [Active Directory Authentication Library for .NET](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) contained in the [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet package.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="72a6b-128">Vylepšení kompilátoru JIT</span><span class="sxs-lookup"><span data-stu-id="72a6b-128">JIT compiler improvements</span></span>

<span data-ttu-id="72a6b-129">**Vrstvená kompilace zůstává funkcí opt-in**</span><span class="sxs-lookup"><span data-stu-id="72a6b-129">**Tiered compilation remains an opt-in feature**</span></span>

<span data-ttu-id="72a6b-130">V rozhraní .NET Core 2.1 implementoval kompilátor JIT novou technologii kompilátoru, *vrstvenou kompilaci*jako funkci opt-in.</span><span class="sxs-lookup"><span data-stu-id="72a6b-130">In .NET Core 2.1, the JIT compiler implemented a new compiler technology, *tiered compilation*, as an opt-in feature.</span></span> <span data-ttu-id="72a6b-131">Cílem vrstvené kompilace je lepší výkon.</span><span class="sxs-lookup"><span data-stu-id="72a6b-131">The goal of tiered compilation is improved performance.</span></span> <span data-ttu-id="72a6b-132">Jedním z důležitých úkolů prováděných kompilátorem JIT je optimalizace spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="72a6b-132">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="72a6b-133">Pro málo používané cesty kódu však kompilátor může strávit více času optimalizací kódu než modul runtime, který stráví prováděním neoptimalizovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="72a6b-133">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends executing unoptimized code.</span></span> <span data-ttu-id="72a6b-134">Vrstvená kompilace zavádí dvě fáze kompilace JIT:</span><span class="sxs-lookup"><span data-stu-id="72a6b-134">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="72a6b-135">**První vrstva**, která generuje kód co nejrychleji.</span><span class="sxs-lookup"><span data-stu-id="72a6b-135">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="72a6b-136">**Druhá vrstva**, která generuje optimalizovaný kód pro ty metody, které jsou často spouštěny.</span><span class="sxs-lookup"><span data-stu-id="72a6b-136">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="72a6b-137">Druhá vrstva kompilace se provádí paralelně pro zvýšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="72a6b-137">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="72a6b-138">Informace o zlepšení výkonu, které může být výsledkem vrstvené kompilace, naleznete [v tématu Oznámení .NET Core 2.2 Náhled 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).</span><span class="sxs-lookup"><span data-stu-id="72a6b-138">For information on the performance improvement that can result from tiered compilation, see [Announcing .NET Core 2.2 Preview 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).</span></span>

<span data-ttu-id="72a6b-139">V rozhraní .NET Core 2.2 Preview 2 byla ve výchozím nastavení povolena vrstvená kompilace.</span><span class="sxs-lookup"><span data-stu-id="72a6b-139">In .NET Core 2.2 Preview 2, tiered compilation was enabled by default.</span></span> <span data-ttu-id="72a6b-140">Rozhodli jsme se však, že stále nejsme připraveni povolit vrstvené kompilace ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="72a6b-140">However, we've decided that we are still not ready to enable tiered compilation by default.</span></span> <span data-ttu-id="72a6b-141">Takže v rozhraní .NET Core 2.2 je vrstvená kompilace i nadále funkcí opt-in.</span><span class="sxs-lookup"><span data-stu-id="72a6b-141">So in .NET Core 2.2, tiered compilation continues to be an opt-in feature.</span></span> <span data-ttu-id="72a6b-142">Informace o přihlášení k vrstvené kompilaci najdete v tématu [Vylepšení kompilátoru Jit](dotnet-core-2-1.md#jit-compiler-improvements) v [tématu Co je nového v rozhraní .NET Core 2.1](dotnet-core-2-1.md).</span><span class="sxs-lookup"><span data-stu-id="72a6b-142">For information on opting in to tiered compilation, see [Jit compiler improvements](dotnet-core-2-1.md#jit-compiler-improvements) in [What's new in .NET Core 2.1](dotnet-core-2-1.md).</span></span>

## <a name="runtime"></a><span data-ttu-id="72a6b-143">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="72a6b-143">Runtime</span></span>

<span data-ttu-id="72a6b-144">**Vkládání kódu před spuštěním Hlavní metody**</span><span class="sxs-lookup"><span data-stu-id="72a6b-144">**Injecting code prior to executing the Main method**</span></span>

<span data-ttu-id="72a6b-145">Počínaje rozhraním .NET Core 2.2 můžete použít spouštěcí hák k vložení kódu před spuštěním metody Main aplikace.</span><span class="sxs-lookup"><span data-stu-id="72a6b-145">Starting with .NET Core 2.2, you can use a startup hook to inject code prior to running an application's Main method.</span></span> <span data-ttu-id="72a6b-146">Spouštěcí háčky umožňují hostiteli přizpůsobit chování aplikací po jejich nasazení bez nutnosti překompilovat nebo změnit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="72a6b-146">Startup hooks make it possible for a host to customize the behavior of applications after they have been deployed without needing to recompile or change the application.</span></span>

<span data-ttu-id="72a6b-147">Očekáváme, že poskytovatelé hostingu definovat vlastní konfiguraci a zásady, včetně nastavení, <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> které potenciálně ovlivňují chování zatížení hlavnívstupní bod, jako je například chování.</span><span class="sxs-lookup"><span data-stu-id="72a6b-147">We expect hosting providers to define custom configuration and policy, including settings that potentially influence the load behavior of the main entry point, such as the <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> behavior.</span></span> <span data-ttu-id="72a6b-148">Háček lze nastavit trasování nebo vkládání telemetrie, nastavit zpětná volání pro zpracování nebo definovat jiné chování závislé na prostředí.</span><span class="sxs-lookup"><span data-stu-id="72a6b-148">The hook can be used to set up tracing or telemetry injection, to set up callbacks for handling, or to define other environment-dependent behavior.</span></span> <span data-ttu-id="72a6b-149">Háček je oddělen od vstupního bodu, takže uživatelský kód není nutné měnit.</span><span class="sxs-lookup"><span data-stu-id="72a6b-149">The hook is separate from the entry point, so that user code doesn't need to be modified.</span></span>

<span data-ttu-id="72a6b-150">Další informace naleznete [v tématu Háček pro spuštění hostitele.](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md)</span><span class="sxs-lookup"><span data-stu-id="72a6b-150">See [Host startup hook](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="72a6b-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="72a6b-151">See also</span></span>

- [<span data-ttu-id="72a6b-152">Co je nového v .NET Core</span><span class="sxs-lookup"><span data-stu-id="72a6b-152">What's new in .NET Core</span></span>](index.md)
- [<span data-ttu-id="72a6b-153">Co je nového v ASP.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="72a6b-153">What's new in ASP.NET Core 2.2</span></span>](/aspnet/core/release-notes/aspnetcore-2.2)
- [<span data-ttu-id="72a6b-154">Nové funkce v EF Core 2.2</span><span class="sxs-lookup"><span data-stu-id="72a6b-154">New features in EF Core 2.2</span></span>](/ef/core/what-is-new/ef-core-2.2)
