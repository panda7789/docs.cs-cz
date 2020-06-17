---
ms.openlocfilehash: d00b8ecaa61b358e062d85a2b68ca8a95cada442
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803232"
---
### <a name="kestrel-configuration-changes-at-run-time-detected-by-default"></a><span data-ttu-id="6cd3e-101">Kestrel: ve výchozím nastavení se zjistily změny v konfiguraci v době běhu.</span><span class="sxs-lookup"><span data-stu-id="6cd3e-101">Kestrel: Configuration changes at run time detected by default</span></span>

<span data-ttu-id="6cd3e-102">Kestrel nyní reaguje na změny v `Kestrel` části `IConfiguration` instance projektu (například *appsettings.json*) v době běhu.</span><span class="sxs-lookup"><span data-stu-id="6cd3e-102">Kestrel now reacts to changes made to the `Kestrel` section of the project's `IConfiguration` instance (for example, *appsettings.json*) at run time.</span></span> <span data-ttu-id="6cd3e-103">Další informace o tom, jak nakonfigurovat Kestrel pomocí *appsettings.jsna*, najdete v *appsettings.js* v tématu [Konfigurace koncového bodu](/aspnet/core/fundamentals/servers/kestrel#endpoint-configuration).</span><span class="sxs-lookup"><span data-stu-id="6cd3e-103">To learn more about how to configure Kestrel using *appsettings.json*, see the *appsettings.json* example in [Endpoint configuration](/aspnet/core/fundamentals/servers/kestrel#endpoint-configuration).</span></span>

<span data-ttu-id="6cd3e-104">Kestrel bude při reakci na tyto změny konfigurace navazovat, odpojit a znovu vytvořit vazbu koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="6cd3e-104">Kestrel will bind, unbind, and rebind endpoints as necessary to react to these configuration changes.</span></span>

<span data-ttu-id="6cd3e-105">Diskuzi najdete v tématu problém [dotnet/aspnetcore # 22807](https://github.com/dotnet/aspnetcore/issues/22807).</span><span class="sxs-lookup"><span data-stu-id="6cd3e-105">For discussion, see issue [dotnet/aspnetcore#22807](https://github.com/dotnet/aspnetcore/issues/22807).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6cd3e-106">Představená verze</span><span class="sxs-lookup"><span data-stu-id="6cd3e-106">Version introduced</span></span>

<span data-ttu-id="6cd3e-107">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="6cd3e-107">5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="6cd3e-108">Staré chování</span><span class="sxs-lookup"><span data-stu-id="6cd3e-108">Old behavior</span></span>

<span data-ttu-id="6cd3e-109">Před ASP.NET Core 5,0 Preview 6 nepodporuje Kestrel změnu konfigurace v době běhu.</span><span class="sxs-lookup"><span data-stu-id="6cd3e-109">Before ASP.NET Core 5.0 Preview 6, Kestrel didn't support changing configuration at run time.</span></span>

<span data-ttu-id="6cd3e-110">V ASP.NET Core 5,0 Preview 6 se můžete vyjádřit jako výchozí chování při provádění změn konfigurace v době běhu.</span><span class="sxs-lookup"><span data-stu-id="6cd3e-110">In ASP.NET Core 5.0 Preview 6, you could opt into the now-default behavior of reacting to configuration changes at run time.</span></span> <span data-ttu-id="6cd3e-111">Ruční konfigurace Kestrel vazeb v konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="6cd3e-111">Opting in required binding Kestrel's configuration manually:</span></span>

```csharp
using Microsoft.AspNetCore.Hosting;
using Microsoft.Extensions.Hosting;

public class Program
{
    public static void Main(string[] args) =>
        CreateHostBuilder(args).Build().Run();

    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureWebHostDefaults(webBuilder =>
            {
                webBuilder.UseKestrel((builderContext, kestrelOptions) =>
                {
                    kestrelOptions.Configure(
                        builderContext.Configuration.GetSection("Kestrel"), reloadOnChange: true);
                });

                webBuilder.UseStartup<Startup>();
            });
}
```

#### <a name="new-behavior"></a><span data-ttu-id="6cd3e-112">Nové chování</span><span class="sxs-lookup"><span data-stu-id="6cd3e-112">New behavior</span></span>

<span data-ttu-id="6cd3e-113">Kestrel ve výchozím nastavení reaguje na změny konfigurace v době běhu.</span><span class="sxs-lookup"><span data-stu-id="6cd3e-113">Kestrel reacts to configuration changes at run time by default.</span></span> <span data-ttu-id="6cd3e-114">Pro podporu této změny <xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A> volání `KestrelServerOptions.Configure(IConfiguration, bool)` `reloadOnChange: true` ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="6cd3e-114">To support that change, <xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A> calls `KestrelServerOptions.Configure(IConfiguration, bool)` with `reloadOnChange: true` by default.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6cd3e-115">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="6cd3e-115">Reason for change</span></span>

<span data-ttu-id="6cd3e-116">Změna byla provedena za účelem podpory opětovné konfigurace koncového bodu v době běhu bez úplného restartování serveru.</span><span class="sxs-lookup"><span data-stu-id="6cd3e-116">The change was made to support endpoint reconfiguration at run time without completely restarting the server.</span></span> <span data-ttu-id="6cd3e-117">Na rozdíl od úplného restartování serveru nejsou nezměněné koncové body bez dočasné vazby.</span><span class="sxs-lookup"><span data-stu-id="6cd3e-117">Unlike with a full server restart, unchanged endpoints aren't unbound even temporarily.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6cd3e-118">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="6cd3e-118">Recommended action</span></span>

* <span data-ttu-id="6cd3e-119">Ve většině scénářů, ve kterých výchozí konfigurační oddíl Kestrel se nezmění v době běhu, tato změna nemá žádný vliv a není nutné provádět žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="6cd3e-119">For most scenarios in which Kestrel's default configuration section doesn't change at run time, this change has no impact and no action is needed.</span></span>
* <span data-ttu-id="6cd3e-120">Ve scénářích, ve kterých se výchozí konfigurační oddíl Kestrel mění v době běhu a Kestrel by na ni měl reagovat, je teď to výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="6cd3e-120">For scenarios in which Kestrel's default configuration section does change at run time and Kestrel should react to it, this is now the default behavior.</span></span>
* <span data-ttu-id="6cd3e-121">U scénářů, ve kterých se výchozí konfigurační oddíl Kestrel mění v době běhu a Kestrel by na něj neměli reagovat, můžete odhlásit následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="6cd3e-121">For scenarios in which Kestrel's default configuration section changes at run time and Kestrel shouldn't react to it, you can opt out as follows:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Extensions.Hosting;

    public class Program
    {
        public static void Main(string[] args) =>
            CreateHostBuilder(args).Build().Run();

        public static IHostBuilder CreateHostBuilder(string[] args) =>
            Host.CreateDefaultBuilder(args)
                .ConfigureWebHostDefaults(webBuilder =>
                {
                    webBuilder.UseKestrel((builderContext, kestrelOptions) =>
                    {
                        kestrelOptions.Configure(
                            builderContext.Configuration.GetSection("Kestrel"), reloadOnChange: false);
                    });

                    webBuilder.UseStartup<Startup>();
                });
    }
    ```

<span data-ttu-id="6cd3e-122">**Poznámky:**</span><span class="sxs-lookup"><span data-stu-id="6cd3e-122">**Notes:**</span></span>

<span data-ttu-id="6cd3e-123">Tato změna nemění chování `KestrelServerOptions.Configure(IConfiguration)` přetížení, které je stále výchozím `reloadOnChange: false` chováním.</span><span class="sxs-lookup"><span data-stu-id="6cd3e-123">This change doesn't modify the behavior of the `KestrelServerOptions.Configure(IConfiguration)` overload, which still defaults to the `reloadOnChange: false` behavior.</span></span>

<span data-ttu-id="6cd3e-124">Je také důležité se ujistit, že zdroj konfigurace podporuje opětovné načtení.</span><span class="sxs-lookup"><span data-stu-id="6cd3e-124">It's also important to make sure the configuration source supports reloading.</span></span> <span data-ttu-id="6cd3e-125">U zdrojů JSON je opakované načítání konfigurováno voláním `AddJsonFile(path, reloadOnChange: true)` .</span><span class="sxs-lookup"><span data-stu-id="6cd3e-125">For JSON sources, reloading is configured by calling `AddJsonFile(path, reloadOnChange: true)`.</span></span> <span data-ttu-id="6cd3e-126">Opětovné načítání je již ve výchozím nastavení nakonfigurováno pro *appsettings.jsv* a *appSettings. { Environment}. JSON*.</span><span class="sxs-lookup"><span data-stu-id="6cd3e-126">Reloading is already configured by default for *appsettings.json* and *appsettings.{Environment}.json*.</span></span>

#### <a name="category"></a><span data-ttu-id="6cd3e-127">Kategorie</span><span class="sxs-lookup"><span data-stu-id="6cd3e-127">Category</span></span>

<span data-ttu-id="6cd3e-128">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6cd3e-128">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6cd3e-129">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="6cd3e-129">Affected APIs</span></span>

<xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`Overload:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults`

-->
