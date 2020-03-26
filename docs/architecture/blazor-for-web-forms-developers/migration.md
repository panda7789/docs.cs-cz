---
title: Migrace z webových formulářů ASP.NET do Blazoru
description: Přečtěte si, jak přistupovat k migraci existující aplikace ASP.NET Web Forms do Blazoru.
author: twsouthwick
ms.author: tasou
ms.date: 09/19/2019
ms.openlocfilehash: 0a10a9a3d5ab32e16cb59a68da57116e20c53e49
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134094"
---
# <a name="migrate-from-aspnet-web-forms-to-blazor"></a><span data-ttu-id="9bd4b-103">Migrace z webových formulářů ASP.NET do Blazoru</span><span class="sxs-lookup"><span data-stu-id="9bd4b-103">Migrate from ASP.NET Web Forms to Blazor</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="9bd4b-104">Migrace základu kódu z ASP.NET webových formulářů do Blazoru je časově náročná úloha, která vyžaduje plánování.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-104">Migrating a code base from ASP.NET Web Forms to Blazor is a time-consuming task that requires planning.</span></span> <span data-ttu-id="9bd4b-105">Tato kapitola popisuje proces.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-105">This chapter outlines the process.</span></span> <span data-ttu-id="9bd4b-106">Něco, co může usnadnit přechod je zajistit, že aplikace dodržuje architekturu *N-vrstvé,* kde model aplikace (v tomto případě webové formuláře) je oddělen od obchodní logiky.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-106">Something that can ease the transition is to ensure the app adheres to an *N-tier* architecture, wherein the app model (in this case, Web Forms) is separate from the business logic.</span></span> <span data-ttu-id="9bd4b-107">Toto logické oddělení vrstev jasně ukazuje, co je potřeba přesunout do .NET Core a Blazor.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-107">This logical separation of layers makes it clear what needs to move to .NET Core and Blazor.</span></span>

<span data-ttu-id="9bd4b-108">V tomto příkladu se používá aplikace eShop dostupná na [GitHubu.](https://github.com/dotnet-architecture/eShopOnBlazor)</span><span class="sxs-lookup"><span data-stu-id="9bd4b-108">For this example, the eShop app available on [GitHub](https://github.com/dotnet-architecture/eShopOnBlazor) is used.</span></span> <span data-ttu-id="9bd4b-109">eShop je katalogová služba, která poskytuje možnosti CRUD prostřednictvím zadávání formulářů a validace.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-109">eShop is a catalog service that provides CRUD capabilities via form entry and validation.</span></span>

<span data-ttu-id="9bd4b-110">Proč by měla být pracovní aplikace migrována do Blazoru?</span><span class="sxs-lookup"><span data-stu-id="9bd4b-110">Why should a working app be migrated to Blazor?</span></span> <span data-ttu-id="9bd4b-111">Mnohokrát, není třeba.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-111">Many times, there's no need.</span></span> <span data-ttu-id="9bd4b-112">ASP.NET webových formulářů bude podporována po mnoho let.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-112">ASP.NET Web Forms will continue to be supported for many years.</span></span> <span data-ttu-id="9bd4b-113">Mnoho funkcí, které Blazor poskytuje, je však podporováno pouze v migrované aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-113">However, many of the features that Blazor provides are only supported on a migrated app.</span></span> <span data-ttu-id="9bd4b-114">Mezi tyto funkce patří:</span><span class="sxs-lookup"><span data-stu-id="9bd4b-114">Such features include:</span></span>

- <span data-ttu-id="9bd4b-115">Zlepšení výkonnosti v rámci, jako je`Span<T>`</span><span class="sxs-lookup"><span data-stu-id="9bd4b-115">Performance improvements in the framework such as `Span<T>`</span></span>
- <span data-ttu-id="9bd4b-116">Možnost spuštění jako webová sestava</span><span class="sxs-lookup"><span data-stu-id="9bd4b-116">Ability to run as WebAssembly</span></span>
- <span data-ttu-id="9bd4b-117">Podpora napříč platformami pro Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="9bd4b-117">Cross-platform support for Linux and macOS</span></span>
- <span data-ttu-id="9bd4b-118">Nasazení v místním prostředí aplikace nebo nasazení sdíleného frameworku bez dopadu na jiné aplikace</span><span class="sxs-lookup"><span data-stu-id="9bd4b-118">App-local deployment or shared framework deployment without impacting other apps</span></span>

<span data-ttu-id="9bd4b-119">Pokud jsou tyto nebo jiné nové funkce dostatečně přesvědčivé, může být migrace aplikace hodnotou.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-119">If these or other new features are compelling enough, there may be value in migrating the app.</span></span> <span data-ttu-id="9bd4b-120">Migrace může mít různé tvary; může to být celá aplikace nebo pouze určité koncové body, které vyžadují změny.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-120">The migration can take different shapes; it can be the entire app, or only certain endpoints that require the changes.</span></span> <span data-ttu-id="9bd4b-121">Rozhodnutí o migraci je v konečném důsledku založeno na obchodních problémech, které má vývojář vyřešit.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-121">The decision to migrate is ultimately based on the business problems to be solved by the developer.</span></span>

## <a name="server-side-versus-client-side-hosting"></a><span data-ttu-id="9bd4b-122">Hosting na straně serveru versus na straně klienta</span><span class="sxs-lookup"><span data-stu-id="9bd4b-122">Server-side versus client-side hosting</span></span>

<span data-ttu-id="9bd4b-123">Jak je popsáno v kapitole [hostování modelů,](hosting-models.md) aplikace Blazor může být hostována dvěma různými způsoby: na straně serveru a na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-123">As described in the [hosting models](hosting-models.md) chapter, a Blazor app can be hosted in two different ways: server-side and client-side.</span></span> <span data-ttu-id="9bd4b-124">Model na straně serveru používá připojení ASP.NET Core SignalR ke správě aktualizací modelu DOM při spuštění libovolného skutečného kódu na serveru.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-124">The server-side model uses ASP.NET Core SignalR connections to manage the DOM updates while running any actual code on the server.</span></span> <span data-ttu-id="9bd4b-125">Model na straně klienta běží jako WebAssembly v prohlížeči a nevyžaduje žádná připojení k serveru.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-125">The client-side model runs as WebAssembly within a browser and requires no server connections.</span></span> <span data-ttu-id="9bd4b-126">Existuje řada rozdílů, které mohou ovlivnit, což je nejlepší pro konkrétní aplikaci:</span><span class="sxs-lookup"><span data-stu-id="9bd4b-126">There are a number of differences that may affect which is best for a specific app:</span></span>

- <span data-ttu-id="9bd4b-127">Spuštění jako WebAssembly je stále ve vývoji a nemusí podporovat všechny funkce (například zřetězení) v aktuálním čase</span><span class="sxs-lookup"><span data-stu-id="9bd4b-127">Running as WebAssembly is still in development and may not support all features (such as threading) at the current time</span></span>
- <span data-ttu-id="9bd4b-128">Upovídaná komunikace mezi klientem a serverem může způsobit problémy s latencí v režimu na straně serveru</span><span class="sxs-lookup"><span data-stu-id="9bd4b-128">Chatty communication between the client and server may cause latency issues in server-side mode</span></span>
- <span data-ttu-id="9bd4b-129">Přístup k databázím a interním nebo chráněným službám vyžaduje samostatnou službu s hostováním na straně klienta</span><span class="sxs-lookup"><span data-stu-id="9bd4b-129">Access to databases and internal or protected services require a separate service with client-side hosting</span></span>

<span data-ttu-id="9bd4b-130">V době psaní modelu na straně serveru více podobá webové formuláře.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-130">At the time of writing, the server-side model more closely resembles Web Forms.</span></span> <span data-ttu-id="9bd4b-131">Většina této kapitoly se zaměřuje na model hostování na straně serveru, protože je připraven na produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-131">Most of this chapter focuses on the server-side hosting model, as it's production-ready.</span></span>

## <a name="create-a-new-project"></a><span data-ttu-id="9bd4b-132">Vytvoření nového projektu</span><span class="sxs-lookup"><span data-stu-id="9bd4b-132">Create a new project</span></span>

<span data-ttu-id="9bd4b-133">Tento počáteční krok migrace je vytvořit nový projekt.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-133">This initial migration step is to create a new project.</span></span> <span data-ttu-id="9bd4b-134">Tento typ projektu je založen na projektech stylu Sady SDK .NET Core a zjednodušuje velkou část často používaný text, který byl použit v předchozích formátech projektu.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-134">This project type is based on the SDK style projects of .NET Core and simplifies much of the boilerplate that was used in previous project formats.</span></span> <span data-ttu-id="9bd4b-135">Podrobnější informace naleznete v kapitole [O struktuře projektu](project-structure.md).</span><span class="sxs-lookup"><span data-stu-id="9bd4b-135">For more detail, please see the chapter on [Project Structure](project-structure.md).</span></span>

<span data-ttu-id="9bd4b-136">Po vytvoření projektu nainstalujte knihovny, které byly použity v předchozím projektu.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-136">Once the project has been created, install the libraries that were used in the previous project.</span></span> <span data-ttu-id="9bd4b-137">Ve starších projektech webových formulářů jste pravděpodobně použili soubor *packages.config* k zobrazení seznamu požadovaných balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-137">In older Web Forms projects, you may have used the *packages.config* file to list the required NuGet packages.</span></span> <span data-ttu-id="9bd4b-138">V novém projektu ve stylu sady SDK byl soubor `<PackageReference>` *packages.config* nahrazen prvky v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-138">In the new SDK-style project, *packages.config* has been replaced with `<PackageReference>` elements in the project file.</span></span> <span data-ttu-id="9bd4b-139">Výhodou tohoto přístupu je, že všechny závislosti jsou nainstalovány přechodně.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-139">A benefit to this approach is that all dependencies are installed transitively.</span></span> <span data-ttu-id="9bd4b-140">Uvádíte pouze závislosti nejvyšší úrovně, na kterých vám záleží.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-140">You only list the top-level dependencies you care about.</span></span>

<span data-ttu-id="9bd4b-141">Mnoho závislostí, které používáte, je k dispozici pro rozhraní .NET Core, včetně entity Framework 6 a log4net.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-141">Many of the dependencies you're using are available for .NET Core, including Entity Framework 6 and log4net.</span></span> <span data-ttu-id="9bd4b-142">Pokud není k dispozici žádná verze .NET Core nebo .NET Standard, lze často použít verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-142">If there's no .NET Core or .NET Standard version available, the .NET Framework version can often be used.</span></span> <span data-ttu-id="9bd4b-143">Počet ujetých kilometrů se může lišit.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-143">Your mileage may vary.</span></span> <span data-ttu-id="9bd4b-144">Jakékoli rozhraní API, které není k dispozici v rozhraní .NET Core, způsobí chybu za běhu.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-144">Any API used that isn't available in .NET Core causes a runtime error.</span></span> <span data-ttu-id="9bd4b-145">Visual Studio vás upozorní na tyto balíčky.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-145">Visual Studio notifies you of such packages.</span></span> <span data-ttu-id="9bd4b-146">V uzlu **Reference** v projektu se v **Průzkumníku řešení**zobrazí žlutá ikona.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-146">A yellow icon appears on the project's **References** node in **Solution Explorer**.</span></span>

<span data-ttu-id="9bd4b-147">V projektu eShopu založeném na Blazoru můžete vidět nainstalované balíčky.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-147">In the Blazor-based eShop project, you can see the packages that are installed.</span></span> <span data-ttu-id="9bd4b-148">Dříve soubor *packages.config* vyjmenoval všechny balíčky použité v projektu, což vedlo k tomu, že soubor byl dlouhý téměř 50 řádků.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-148">Previously, the *packages.config* file listed every package used in the project, resulting in a file almost 50 lines long.</span></span> <span data-ttu-id="9bd4b-149">Výstřižek *packages.config* je:</span><span class="sxs-lookup"><span data-stu-id="9bd4b-149">A snippet of *packages.config* is:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  ...
  <package id="Microsoft.ApplicationInsights.Agent.Intercept" version="2.4.0" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.DependencyCollector" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.PerfCounterCollector" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.Web" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.WindowsServer" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.WindowsServer.TelemetryChannel" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.AspNet.FriendlyUrls" version="1.0.2" targetFramework="net472" />
  <package id="Microsoft.AspNet.FriendlyUrls.Core" version="1.0.2" targetFramework="net472" />
  <package id="Microsoft.AspNet.ScriptManager.MSAjax" version="5.0.0" targetFramework="net472" />
  <package id="Microsoft.AspNet.ScriptManager.WebForms" version="5.0.0" targetFramework="net472" />
  ...
  <package id="System.Memory" version="4.5.1" targetFramework="net472" />
  <package id="System.Numerics.Vectors" version="4.4.0" targetFramework="net472" />
  <package id="System.Runtime.CompilerServices.Unsafe" version="4.5.0" targetFramework="net472" />
  <package id="System.Threading.Channels" version="4.5.0" targetFramework="net472" />
  <package id="System.Threading.Tasks.Extensions" version="4.5.1" targetFramework="net472" />
  <package id="WebGrease" version="1.6.0" targetFramework="net472" />
</packages>
```

<span data-ttu-id="9bd4b-150">Prvek `<packages>` obsahuje všechny nezbytné závislosti.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-150">The `<packages>` element includes all necessary dependencies.</span></span> <span data-ttu-id="9bd4b-151">Je obtížné určit, které z těchto balíčků jsou zahrnuty, protože je požadujete.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-151">It's difficult to identify which of these packages are included because you require them.</span></span> <span data-ttu-id="9bd4b-152">Některé `<package>` prvky jsou uvedeny jednoduše pro uspokojení potřeb závislostí, které potřebujete.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-152">Some `<package>` elements are listed simply to satisfy the needs of dependencies you require.</span></span>

<span data-ttu-id="9bd4b-153">Projekt Blazor uvádí závislosti, které `<ItemGroup>` požadujete v rámci prvku v souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="9bd4b-153">The Blazor project lists the dependencies you require within an `<ItemGroup>` element in the project file:</span></span>

```xml
<ItemGroup>
    <PackageReference Include="Autofac" Version="4.9.3" />
    <PackageReference Include="EntityFramework" Version="6.3.0-preview9-19423-04" />
    <PackageReference Include="log4net" Version="2.0.8" />
</ItemGroup>
```

<span data-ttu-id="9bd4b-154">Jeden balíček NuGet, který zjednodušuje životnost vývojářů webových formulářů, je [sada Windows Compatibility Pack](../../core/porting/windows-compat-pack.md).</span><span class="sxs-lookup"><span data-stu-id="9bd4b-154">One NuGet package that simplifies the life of Web Forms developers is the [Windows Compatibility Pack](../../core/porting/windows-compat-pack.md).</span></span> <span data-ttu-id="9bd4b-155">Ačkoli .NET Core je multiplatformní, některé funkce jsou k dispozici pouze v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-155">Although .NET Core is cross-platform, some features are only available on Windows.</span></span> <span data-ttu-id="9bd4b-156">Funkce specifické pro systém Windows jsou k dispozici instalací sady Compatibility Pack.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-156">Windows-specific features are made available by installing the compatibility pack.</span></span> <span data-ttu-id="9bd4b-157">Příklady těchto funkcí zahrnují registr, službu WMI a adresářové služby.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-157">Examples of such features include the Registry, WMI, and Directory Services.</span></span> <span data-ttu-id="9bd4b-158">Balíček přidá přibližně 20 000 api a aktivuje mnoho služeb, se kterými už možná znáte.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-158">The package adds around 20,000 APIs and activates many services with which you may already be familiar.</span></span> <span data-ttu-id="9bd4b-159">Projekt eShopu nevyžaduje balíček kompatibility; ale pokud vaše projekty používají funkce specifické pro systém Windows, balíček usnadňuje úsilí o migraci.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-159">The eShop project doesn't require the compatibility pack; but if your projects use Windows-specific features, the package eases the migration efforts.</span></span>

## <a name="enable-startup-process"></a><span data-ttu-id="9bd4b-160">Povolit proces spuštění</span><span class="sxs-lookup"><span data-stu-id="9bd4b-160">Enable startup process</span></span>

<span data-ttu-id="9bd4b-161">Proces spuštění pro Blazor se změnil z webových formulářů a následuje podobné nastavení pro jiné služby ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-161">The startup process for Blazor has changed from Web Forms and follows a similar setup for other ASP.NET Core services.</span></span> <span data-ttu-id="9bd4b-162">Když hostované straně serveru, Blazor komponenty jsou spuštěny jako součást normální ASP.NET aplikace Core.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-162">When hosted server-side, Blazor components are run as part of a normal ASP.NET Core app.</span></span> <span data-ttu-id="9bd4b-163">Při hostování v prohlížeči s WebAssembly, Komponenty Blazor používají podobný model hostování.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-163">When hosted in the browser with WebAssembly, Blazor components use a similar hosting model.</span></span> <span data-ttu-id="9bd4b-164">Rozdíl je, že součásti jsou spuštěny jako samostatná služba od některého z back-endových procesů.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-164">The difference is the components are run as a separate service from any of the backend processes.</span></span> <span data-ttu-id="9bd4b-165">Ať tak či onak, spuštění je podobné.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-165">Either way, the startup is similar.</span></span>

<span data-ttu-id="9bd4b-166">Soubor *Global.asax.cs* je výchozí spouštěcí stránka pro projekty webových formulářů.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-166">The *Global.asax.cs* file is the default startup page for Web Forms projects.</span></span> <span data-ttu-id="9bd4b-167">V projektu eShopu tento soubor konfiguruje kontejner Inversion of Control (IoC) a zpracovává různé události životního cyklu aplikace nebo požadavku.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-167">In the eShop project, this file configures the Inversion of Control (IoC) container and handles the various lifecycle events of the app or request.</span></span> <span data-ttu-id="9bd4b-168">Některé z těchto událostí jsou zpracovány `Application_BeginRequest`pomocí middleware (například ).</span><span class="sxs-lookup"><span data-stu-id="9bd4b-168">Some of these events are handled with middleware (such as `Application_BeginRequest`).</span></span> <span data-ttu-id="9bd4b-169">Jiné události vyžadují přepsání konkrétních služeb prostřednictvím vkládání závislostí (DI).</span><span class="sxs-lookup"><span data-stu-id="9bd4b-169">Other events require the overriding of specific services via dependency injection (DI).</span></span>

<span data-ttu-id="9bd4b-170">Například *Global.asax.cs* soubor pro eShop obsahuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="9bd4b-170">By way of example, the *Global.asax.cs* file for eShop, contains the following code:</span></span>

```csharp
public class Global : HttpApplication, IContainerProviderAccessor
{
    private static readonly ILog _log = LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);

    static IContainerProvider _containerProvider;
    IContainer container;

    public IContainerProvider ContainerProvider
    {
        get { return _containerProvider; }
    }

    protected void Application_Start(object sender, EventArgs e)
    {
        // Code that runs on app startup
        RouteConfig.RegisterRoutes(RouteTable.Routes);
        BundleConfig.RegisterBundles(BundleTable.Bundles);
        ConfigureContainer();
        ConfigDataBase();
    }

    /// <summary>
    /// Track the machine name and the start time for the session inside the current session
    /// </summary>
    protected void Session_Start(Object sender, EventArgs e)
    {
        HttpContext.Current.Session["MachineName"] = Environment.MachineName;
        HttpContext.Current.Session["SessionStartTime"] = DateTime.Now;
    }

    /// <summary>
    /// http://docs.autofac.org/en/latest/integration/webforms.html
    /// </summary>
    private void ConfigureContainer()
    {
        var builder = new ContainerBuilder();
        var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);
        builder.RegisterModule(new ApplicationModule(mockData));
        container = builder.Build();
        _containerProvider = new ContainerProvider(container);
    }

    private void ConfigDataBase()
    {
        var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);

        if (!mockData)
        {
            Database.SetInitializer<CatalogDBContext>(container.Resolve<CatalogDBInitializer>());
        }
    }

    protected void Application_BeginRequest(object sender, EventArgs e)
    {
        //set the property to our new object
        LogicalThreadContext.Properties["activityid"] = new ActivityIdHelper();

        LogicalThreadContext.Properties["requestinfo"] = new WebRequestInfo();

        _log.Debug("Application_BeginRequest");
    }
}
```

<span data-ttu-id="9bd4b-171">Předchozí soubor se `Startup` stane třídou v Blazoru na straně serveru:</span><span class="sxs-lookup"><span data-stu-id="9bd4b-171">The preceding file becomes the `Startup` class in server-side Blazor:</span></span>

```csharp
public class Startup
{
    public Startup(IConfiguration configuration, IWebHostEnvironment env)
    {
        Configuration = configuration;
        Env = env;
    }

    public IConfiguration Configuration { get; }

    public IWebHostEnvironment Env { get; }

    // This method gets called by the runtime. Use this method to add services to the container.
    // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddRazorPages();
        services.AddServerSideBlazor();

        if (Configuration.GetValue<bool>("UseMockData"))
        {
            services.AddSingleton<ICatalogService, CatalogServiceMock>();
        }
        else
        {
            services.AddScoped<ICatalogService, CatalogService>();
            services.AddScoped<IDatabaseInitializer<CatalogDBContext>, CatalogDBInitializer>();
            services.AddSingleton<CatalogItemHiLoGenerator>();
            services.AddScoped(_ => new CatalogDBContext(Configuration.GetConnectionString("CatalogDBContext")));
        }
    }

    // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
    public void Configure(IApplicationBuilder app, ILoggerFactory loggerFactory)
    {
        loggerFactory.AddLog4Net("log4Net.xml");

        if (Env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
        else
        {
            app.UseExceptionHandler("/Home/Error");
        }

        // Middleware for Application_BeginRequest
        app.Use((ctx, next) =>
        {
            LogicalThreadContext.Properties["activityid"] = new ActivityIdHelper(ctx);
            LogicalThreadContext.Properties["requestinfo"] = new WebRequestInfo(ctx);
            return next();
        });

        app.UseStaticFiles();

        app.UseRouting();

        app.UseEndpoints(endpoints =>
        {
            endpoints.MapBlazorHub();
            endpoints.MapFallbackToPage("/_Host");
        });

        ConfigDataBase(app);
    }

    private void ConfigDataBase(IApplicationBuilder app)
    {
        using (var scope = app.ApplicationServices.CreateScope())
        {
            var initializer = scope.ServiceProvider.GetService<IDatabaseInitializer<CatalogDBContext>>();

            if (initializer != null)
            {
                Database.SetInitializer(initializer);
            }
        }
    }
}
```

<span data-ttu-id="9bd4b-172">Jednou z významných změn, které si můžete všimnout z webových formulářů, je význam DI.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-172">One significant change you may notice from Web Forms is the prominence of DI.</span></span> <span data-ttu-id="9bd4b-173">DI je hlavní zásadou v návrhu ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-173">DI has been a guiding principle in the ASP.NET Core design.</span></span> <span data-ttu-id="9bd4b-174">Podporuje přizpůsobení téměř všech aspektů ASP.NET core frameworku.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-174">It supports customization of almost all aspects of the ASP.NET Core framework.</span></span> <span data-ttu-id="9bd4b-175">Existuje dokonce i vestavěný poskytovatel služeb, který lze použít pro mnoho scénářů.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-175">There's even a built-in service provider that can be used for many scenarios.</span></span> <span data-ttu-id="9bd4b-176">Pokud je vyžadováno více přizpůsobení, může být podporováno mnoha komunitními projekty.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-176">If more customization is required, it can be supported by the many community projects.</span></span> <span data-ttu-id="9bd4b-177">Můžete například převést investice do knihovny DI třetích stran.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-177">For example, you can carry forward your third-party DI library investment.</span></span>

<span data-ttu-id="9bd4b-178">V původní aplikaci eShop je určitá konfigurace pro správu relací.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-178">In the original eShop app, there's some configuration for session management.</span></span> <span data-ttu-id="9bd4b-179">Vzhledem k tomu, že Blazor na straně serveru používá ASP.NET Core SignalR pro komunikaci, stav relace není podporován, protože připojení může dojít nezávisle na kontextu HTTP.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-179">Since server-side Blazor uses ASP.NET Core SignalR for communication, session state isn't supported as the connections may occur independent of an HTTP context.</span></span> <span data-ttu-id="9bd4b-180">Aplikace, která používá stav relace, vyžaduje před spuštěním jako aplikace Blazor rearchitecting.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-180">An app that uses session state requires rearchitecting before running as a Blazor app.</span></span>

<span data-ttu-id="9bd4b-181">Další informace o spuštění aplikace naleznete v [tématu App startup](app-startup.md).</span><span class="sxs-lookup"><span data-stu-id="9bd4b-181">For more information about app startup, see [App startup](app-startup.md).</span></span>

## <a name="migrate-http-modules-and-handlers-to-middleware"></a><span data-ttu-id="9bd4b-182">Migrace modulů HTTP a obslužných rutin do middlewaru</span><span class="sxs-lookup"><span data-stu-id="9bd4b-182">Migrate HTTP modules and handlers to middleware</span></span>

<span data-ttu-id="9bd4b-183">Moduly HTTP a obslužné rutiny jsou běžné vzory ve webových formulářích pro řízení kanálu požadavků HTTP.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-183">HTTP modules and handlers are common patterns in Web Forms to control the HTTP request pipeline.</span></span> <span data-ttu-id="9bd4b-184">Třídy, `IHttpModule` `IHttpHandler` které implementují nebo by mohly být registrovány a zpracovávat příchozí požadavky.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-184">Classes that implement `IHttpModule` or `IHttpHandler` could be registered and process incoming requests.</span></span> <span data-ttu-id="9bd4b-185">Webové formuláře konfigurují moduly a obslužné rutiny v souboru *web.config.*</span><span class="sxs-lookup"><span data-stu-id="9bd4b-185">Web Forms configures modules and handlers in the *web.config* file.</span></span> <span data-ttu-id="9bd4b-186">Webové formuláře jsou také silně založeny na zpracování událostí životního cyklu aplikace.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-186">Web Forms is also heavily based on app lifecycle event handling.</span></span> <span data-ttu-id="9bd4b-187">ASP.NET Core místo toho používá middleware.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-187">ASP.NET Core uses middleware instead.</span></span> <span data-ttu-id="9bd4b-188">Middleware je registrován `Configure` v `Startup` metodě třídy.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-188">Middleware is registered in the `Configure` method of the `Startup` class.</span></span> <span data-ttu-id="9bd4b-189">Pořadí provádění middlewaru je určeno registračním příkazem.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-189">Middleware execution order is determined by the registration order.</span></span>

<span data-ttu-id="9bd4b-190">V části [Povolit proces spuštění](#enable-startup-process) byla jako metoda vyvolána událost životního cyklu webovými formuláři. `Application_BeginRequest`</span><span class="sxs-lookup"><span data-stu-id="9bd4b-190">In the [Enable startup process](#enable-startup-process) section, a lifecycle event was raised by Web Forms as the `Application_BeginRequest` method.</span></span> <span data-ttu-id="9bd4b-191">Tato událost není k dispozici v ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-191">This event isn't available in ASP.NET Core.</span></span> <span data-ttu-id="9bd4b-192">Jedním ze způsobů, jak dosáhnout tohoto chování je implementovat middleware, jak je vidět v příkladu souboru *Startup.cs.*</span><span class="sxs-lookup"><span data-stu-id="9bd4b-192">One way to achieve this behavior is to implement middleware as seen in the *Startup.cs* file example.</span></span> <span data-ttu-id="9bd4b-193">Tento middleware provádí stejnou logiku a poté přenese řízení na další obslužnou rutinu v kanálu middlewaru.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-193">This middleware does the same logic and then transfers control to the next handler in the middleware pipeline.</span></span>

<span data-ttu-id="9bd4b-194">Další informace o migraci modulů a obslužných rutin naleznete [v tématu Migrace obslužných rutin protokolu HTTP a modulů do ASP.NET middlewaru core](/aspnet/core/migration/http-modules).</span><span class="sxs-lookup"><span data-stu-id="9bd4b-194">For more information on migrating modules and handlers, see [Migrate HTTP handlers and modules to ASP.NET Core middleware](/aspnet/core/migration/http-modules).</span></span>

## <a name="migrate-static-files"></a><span data-ttu-id="9bd4b-195">Migrace statických souborů</span><span class="sxs-lookup"><span data-stu-id="9bd4b-195">Migrate static files</span></span>

<span data-ttu-id="9bd4b-196">Chcete-li zobrazovat statické soubory (například HTML, CSS, obrázky a JavaScript), musí být soubory vystaveny middlewarem.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-196">To serve static files (for example, HTML, CSS, images, and JavaScript), the files must be exposed by middleware.</span></span> <span data-ttu-id="9bd4b-197">Volání `UseStaticFiles` metody umožňuje obsluhu statických souborů z kořenové cesty webu.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-197">Calling the `UseStaticFiles` method enables the serving of static files from the web root path.</span></span> <span data-ttu-id="9bd4b-198">Výchozí kořenový adresář webu je *wwwroot*, ale lze jej přizpůsobit.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-198">The default web root directory is *wwwroot*, but it can be customized.</span></span> <span data-ttu-id="9bd4b-199">Jak je `Configure` zahrnuto v metodě `Startup` třídy eShopu:</span><span class="sxs-lookup"><span data-stu-id="9bd4b-199">As included in the `Configure` method of eShop's `Startup` class:</span></span>

```csharp
public void Configure(IApplicationBuilder app)
{
    ...

    app.UseStaticFiles();

    ...
}
```

<span data-ttu-id="9bd4b-200">Projekt eShopu umožňuje základní přístup ke statickým souborům.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-200">The eShop project enables basic static file access.</span></span> <span data-ttu-id="9bd4b-201">Pro statický přístup k souborům je k dispozici mnoho vlastních nastavení.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-201">There are many customizations available for static file access.</span></span> <span data-ttu-id="9bd4b-202">Informace o povolení výchozích souborů nebo prohlížeče souborů naleznete [v tématu Statické soubory v ASP.NET jádra](/aspnet/core/fundamentals/static-files).</span><span class="sxs-lookup"><span data-stu-id="9bd4b-202">For information on enabling default files or a file browser, see [Static files in ASP.NET Core](/aspnet/core/fundamentals/static-files).</span></span>

## <a name="migrate-runtime-bundling-and-minification-setup"></a><span data-ttu-id="9bd4b-203">Migrace nastavení sdružování za běhu a minifikace</span><span class="sxs-lookup"><span data-stu-id="9bd4b-203">Migrate runtime bundling and minification setup</span></span>

<span data-ttu-id="9bd4b-204">Sdružování a minifikace jsou techniky optimalizace výkonu pro snížení počtu a velikosti požadavků serveru k načtení určitých typů souborů.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-204">Bundling and minification are performance optimization techniques for reducing the number and size of server requests to retrieve certain file types.</span></span> <span data-ttu-id="9bd4b-205">JavaScript a CSS často podstupují nějakou formu sdružování nebo minifikace před odesláním klientovi.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-205">JavaScript and CSS often undergo some form of bundling or minification before being sent to the client.</span></span> <span data-ttu-id="9bd4b-206">Ve ASP.NET webových formulářů jsou tyto optimalizace zpracovány za běhu.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-206">In ASP.NET Web Forms, these optimizations are handled at runtime.</span></span> <span data-ttu-id="9bd4b-207">Konvence optimalizace jsou definovány jako soubor *App_Start/BundleConfig.cs.*</span><span class="sxs-lookup"><span data-stu-id="9bd4b-207">The optimization conventions are defined an *App_Start/BundleConfig.cs* file.</span></span> <span data-ttu-id="9bd4b-208">V ASP.NET Core je přijat více deklarativní přístup.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-208">In ASP.NET Core, a more declarative approach is adopted.</span></span> <span data-ttu-id="9bd4b-209">Soubor obsahuje seznam souborů, které mají být minififikovány, spolu s konkrétní nastavení minifikace.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-209">A file lists the files to be minified, along with specific minification settings.</span></span>

<span data-ttu-id="9bd4b-210">Další informace o sdružování a minifikaci viz [Sada a minify statických aktiv v ASP.NET Core](/aspnet/core/client-side/bundling-and-minification).</span><span class="sxs-lookup"><span data-stu-id="9bd4b-210">For more information on bundling and minification, see [Bundle and minify static assets in ASP.NET Core](/aspnet/core/client-side/bundling-and-minification).</span></span>

## <a name="migrate-aspx-pages"></a><span data-ttu-id="9bd4b-211">Migrace stránek ASPX</span><span class="sxs-lookup"><span data-stu-id="9bd4b-211">Migrate ASPX pages</span></span>

<span data-ttu-id="9bd4b-212">Stránka v aplikaci Webové formuláře je soubor s příponou *ASPX.*</span><span class="sxs-lookup"><span data-stu-id="9bd4b-212">A page in a Web Forms app is a file with the *.aspx* extension.</span></span> <span data-ttu-id="9bd4b-213">Stránku webových formulářů lze často mapovat na komponentu v Blazoru.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-213">A Web Forms page can often be mapped to a component in Blazor.</span></span> <span data-ttu-id="9bd4b-214">Komponenta Blazor je napsána v souboru s *příponou .razor.*</span><span class="sxs-lookup"><span data-stu-id="9bd4b-214">A Blazor component is authored in a file with the *.razor* extension.</span></span> <span data-ttu-id="9bd4b-215">Pro projekt eShopu je pět stránek převedeno na stránku Razor.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-215">For the eShop project, five pages are converted to a Razor page.</span></span>

<span data-ttu-id="9bd4b-216">Zobrazení podrobností se například skládá ze tří souborů v projektu webových formulářů: *Details.aspx*, *Details.aspx.cs*a *Details.aspx.designer.cs*.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-216">For example, the details view is comprised of three files in the Web Forms project: *Details.aspx*, *Details.aspx.cs*, and *Details.aspx.designer.cs*.</span></span> <span data-ttu-id="9bd4b-217">Při převodu na Blazor, kód-za a značky jsou kombinovány do *Details.razor*.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-217">When converting to Blazor, the code-behind and markup are combined into *Details.razor*.</span></span> <span data-ttu-id="9bd4b-218">Kompilace Razor (ekvivalentní tomu, co je v *souborech .designer.cs)* je uložena v adresáři *obj* a ve výchozím nastavení není k dispozici v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-218">Razor compilation (equivalent to what's in *.designer.cs* files) is stored in the *obj* directory and aren't, by default, viewable in **Solution Explorer**.</span></span> <span data-ttu-id="9bd4b-219">Stránka Webové formuláře se skládá z následujících značek:</span><span class="sxs-lookup"><span data-stu-id="9bd4b-219">The Web Forms page consists of the following markup:</span></span>

```aspx-csharp
<%@ Page Title="Details" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Details.aspx.cs" Inherits="eShopLegacyWebForms.Catalog.Details" %>

<asp:Content ID="Details" ContentPlaceHolderID="MainContent" runat="server">
    <h2 class="esh-body-title">Details</h2>

    <div class="container">
        <div class="row">
            <asp:Image runat="server" CssClass="col-md-6 esh-picture" ImageUrl='<%#"/Pics/" + product.PictureFileName%>' />
            <dl class="col-md-6 dl-horizontal">
                <dt>Name
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.Name%>' />
                </dd>

                <dt>Description
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.Description%>' />
                </dd>

                <dt>Brand
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.CatalogBrand.Brand%>' />
                </dd>

                <dt>Type
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.CatalogType.Type%>' />
                </dd>
                <dt>Price
                </dt>

                <dd>
                    <asp:Label CssClass="esh-price" runat="server" Text='<%#product.Price%>' />
                </dd>

                <dt>Picture name
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.PictureFileName%>' />
                </dd>

                <dt>Stock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.AvailableStock%>' />
                </dd>

                <dt>Restock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.RestockThreshold%>' />
                </dd>

                <dt>Max stock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.MaxStockThreshold%>' />
                </dd>

            </dl>
        </div>

        <div class="form-actions no-color esh-link-list">
            <a runat="server" href='<%# GetRouteUrl("EditProductRoute", new {id =product.Id}) %>' class="esh-link-item">Edit
            </a>
            |
            <a runat="server" href="~" class="esh-link-item">Back to list
            </a>
        </div>

    </div>
</asp:Content>
```

<span data-ttu-id="9bd4b-220">Kód předchozí značky obsahuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="9bd4b-220">The preceding markup's code-behind includes the following code:</span></span>

```csharp
using eShopLegacyWebForms.Models;
using eShopLegacyWebForms.Services;
using log4net;
using System;
using System.Web.UI;

namespace eShopLegacyWebForms.Catalog
{
    public partial class Details : System.Web.UI.Page
    {
        private static readonly ILog _log = LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);

        protected CatalogItem product;

        public ICatalogService CatalogService { get; set; }

        protected void Page_Load(object sender, EventArgs e)
        {
            var productId = Convert.ToInt32(Page.RouteData.Values["id"]);
            _log.Info($"Now loading... /Catalog/Details.aspx?id={productId}");
            product = CatalogService.FindCatalogItem(productId);

            this.DataBind();
        }
    }
}
```

<span data-ttu-id="9bd4b-221">Při převodu na Blazor se stránka Webových formulářů překládá na následující kód:</span><span class="sxs-lookup"><span data-stu-id="9bd4b-221">When converted to Blazor, the Web Forms page translates to the following code:</span></span>

```razor
@page "/Catalog/Details/{id:int}"
@inject ICatalogService CatalogService
@inject ILogger<Details> Logger

<h2 class="esh-body-title">Details</h2>

<div class="container">
    <div class="row">
        <img class="col-md-6 esh-picture" src="@($"/Pics/{_item.PictureFileName}")">

        <dl class="col-md-6 dl-horizontal">
            <dt>
                Name
            </dt>

            <dd>
                @_item.Name
            </dd>

            <dt>
                Description
            </dt>

            <dd>
                @_item.Description
            </dd>

            <dt>
                Brand
            </dt>

            <dd>
                @_item.CatalogBrand.Brand
            </dd>

            <dt>
                Type
            </dt>

            <dd>
                @_item.CatalogType.Type
            </dd>
            <dt>
                Price
            </dt>

            <dd>
                @_item.Price
            </dd>

            <dt>
                Picture name
            </dt>

            <dd>
                @_item.PictureFileName
            </dd>

            <dt>
                Stock
            </dt>

            <dd>
                @_item.AvailableStock
            </dd>

            <dt>
                Restock
            </dt>

            <dd>
                @_item.RestockThreshold
            </dd>

            <dt>
                Max stock
            </dt>

            <dd>
                @_item.MaxStockThreshold
            </dd>

        </dl>
    </div>

    <div class="form-actions no-color esh-link-list">
        <a href="@($"/Catalog/Edit/{_item.Id}")" class="esh-link-item">
            Edit
        </a>
        |
        <a href="/" class="esh-link-item">
            Back to list
        </a>
    </div>

</div>

@code {
    private CatalogItem _item;

    [Parameter]
    public int Id { get; set; }

    protected override void OnInitialized()
    {
        Logger.LogInformation("Now loading... /Catalog/Details/{Id}", Id);

        _item = CatalogService.FindCatalogItem(Id);
    }
}
```

<span data-ttu-id="9bd4b-222">Všimněte si, že kód a značky jsou ve stejném souboru.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-222">Notice that the code and markup are in the same file.</span></span> <span data-ttu-id="9bd4b-223">Všechny požadované služby jsou `@inject` přístupné pomocí atributu.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-223">Any required services are made accessible with the `@inject` attribute.</span></span> <span data-ttu-id="9bd4b-224">Podle `@page` směrnice je tato stránka přístupná `Catalog/Details/{id}` na trase.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-224">Per the `@page` directive, this page can be accessed at the `Catalog/Details/{id}` route.</span></span> <span data-ttu-id="9bd4b-225">Hodnota `{id}` zástupného symbolu trasy byla omezena na celé číslo.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-225">The value of the route's `{id}` placeholder has been constrained to an integer.</span></span> <span data-ttu-id="9bd4b-226">Jak je popsáno v části [směrování,](pages-routing-layouts.md) na rozdíl od webových formulářů komponenta Razor výslovně uvádí jeho trasu a všechny parametry, které jsou zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-226">As described in the [routing](pages-routing-layouts.md) section, unlike Web Forms, a Razor component explicitly states its route and any parameters that are included.</span></span> <span data-ttu-id="9bd4b-227">Mnoho ovládacích prvků webových formulářů nemusí mít přesné protějšky v Blazoru.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-227">Many Web Forms controls may not have exact counterparts in Blazor.</span></span> <span data-ttu-id="9bd4b-228">Často existuje ekvivalentní fragment HTML, který bude sloužit stejnému účelu.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-228">There's often an equivalent HTML snippet that will serve the same purpose.</span></span> <span data-ttu-id="9bd4b-229">`<asp:Label />` Ovládací prvek lze například nahradit elementem HTML. `<label>`</span><span class="sxs-lookup"><span data-stu-id="9bd4b-229">For example, the `<asp:Label />` control can be replaced with an HTML `<label>` element.</span></span>

### <a name="model-validation-in-blazor"></a><span data-ttu-id="9bd4b-230">Ověření modelu v Blazoru</span><span class="sxs-lookup"><span data-stu-id="9bd4b-230">Model validation in Blazor</span></span>

<span data-ttu-id="9bd4b-231">Pokud kód webových formulářů zahrnuje ověření, můžete přenést velkou část toho, co máte, s malými změnami.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-231">If your Web Forms code includes validation, you can transfer much of what you have with little-to-no changes.</span></span> <span data-ttu-id="9bd4b-232">Výhodou pro spuštění v Blazoru je, že stejnou ověřovací logiku lze spustit bez nutnosti vlastního JavaScriptu.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-232">A benefit to running in Blazor is that the same validation logic can be run without needing custom JavaScript.</span></span> <span data-ttu-id="9bd4b-233">Datové poznámky umožňují snadné ověření modelu.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-233">Data annotations enable easy model validation.</span></span>

<span data-ttu-id="9bd4b-234">Například stránka *Create.aspx* obsahuje formulář pro zadávání dat s ověřením.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-234">For example, the *Create.aspx* page has a data entry form with validation.</span></span> <span data-ttu-id="9bd4b-235">Ukázkový úryvek bude vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="9bd4b-235">An example snippet would look like this:</span></span>

```aspx
<div class="form-group">
    <label class="control-label col-md-2">Name</label>
    <div class="col-md-3">
        <asp:TextBox ID="Name" runat="server" CssClass="form-control"></asp:TextBox>
        <asp:RequiredFieldValidator runat="server" ControlToValidate="Name" Display="Dynamic"
            CssClass="field-validation-valid text-danger" ErrorMessage="The Name field is required." />
    </div>
</div>
```

<span data-ttu-id="9bd4b-236">V Blazor, ekvivalentní značky je k dispozici v souboru *Create.razor:*</span><span class="sxs-lookup"><span data-stu-id="9bd4b-236">In Blazor, the equivalent markup is provided in a *Create.razor* file:</span></span>

```razor
<EditForm Model="_item" OnValidSubmit="@...">
    <DataAnnotationsValidator />

    <div class="form-group">
        <label class="control-label col-md-2">Name</label>
        <div class="col-md-3">
            <InputText class="form-control" @bind-Value="_item.Name" />
            <ValidationMessage For="(() => _item.Name)" />
        </div>
    </div>

    ...
</EditForm>
```

<span data-ttu-id="9bd4b-237">Kontext `EditForm` zahrnuje podporu ověření a lze je omotat kolem vstupu.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-237">The `EditForm` context includes validation support and can be wrapped around input.</span></span> <span data-ttu-id="9bd4b-238">Poznámky k datům jsou běžným způsobem přidání ověření.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-238">Data annotations are a common way to add validation.</span></span> <span data-ttu-id="9bd4b-239">Tato podpora ověření lze `DataAnnotationsValidator` přidat prostřednictvím komponenty.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-239">Such validation support can be added via the `DataAnnotationsValidator` component.</span></span> <span data-ttu-id="9bd4b-240">Další informace o tomto mechanismu naleznete [v ASP.NET formuláře Core Blazor a ověření](/aspnet/core/blazor/forms-validation).</span><span class="sxs-lookup"><span data-stu-id="9bd4b-240">For more information on this mechanism, see [ASP.NET Core Blazor forms and validation](/aspnet/core/blazor/forms-validation).</span></span>

## <a name="migrate-built-in-web-forms-controls"></a><span data-ttu-id="9bd4b-241">Migrace integrovaných ovládacích prvků webových formulářů</span><span class="sxs-lookup"><span data-stu-id="9bd4b-241">Migrate built-in Web Forms controls</span></span>

<span data-ttu-id="9bd4b-242">*Tento obsah je již brzy.*</span><span class="sxs-lookup"><span data-stu-id="9bd4b-242">*This content is coming soon.*</span></span>

## <a name="migrate-configuration"></a><span data-ttu-id="9bd4b-243">Migrace konfigurace</span><span class="sxs-lookup"><span data-stu-id="9bd4b-243">Migrate configuration</span></span>

<span data-ttu-id="9bd4b-244">V projektu webových formulářů jsou konfigurační data nejčastěji uložena v souboru *web.config.*</span><span class="sxs-lookup"><span data-stu-id="9bd4b-244">In a Web Forms project, configuration data is most commonly stored in the *web.config* file.</span></span> <span data-ttu-id="9bd4b-245">K konfiguračním `ConfigurationManager`datům se přistupuje pomocí aplikace .</span><span class="sxs-lookup"><span data-stu-id="9bd4b-245">The configuration data is accessed with `ConfigurationManager`.</span></span> <span data-ttu-id="9bd4b-246">Služby byly často nutné k analýzě objektů.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-246">Services were often required to parse objects.</span></span> <span data-ttu-id="9bd4b-247">S rozhraním .NET Framework 4.7.2 byla do `ConfigurationBuilders`konfigurace přidána shodnost prostřednictvím rozhraní .</span><span class="sxs-lookup"><span data-stu-id="9bd4b-247">With .NET Framework 4.7.2, composability was added to configuration via `ConfigurationBuilders`.</span></span> <span data-ttu-id="9bd4b-248">Tyto tvůrce povoleno vývojáři přidat různé zdroje pro konfiguraci, která byla pak skládá za běhu načíst potřebné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-248">These builders allowed developers to add various sources for configuration that was then composed at runtime to retrieve the necessary values.</span></span>

<span data-ttu-id="9bd4b-249">ASP.NET Core zavedla flexibilní konfigurační systém, který umožňuje definovat zdroj konfigurace nebo zdroje používané vaší aplikací a nasazením.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-249">ASP.NET Core introduced a flexible configuration system that allows you to define the configuration source or sources used by your app and deployment.</span></span> <span data-ttu-id="9bd4b-250">Infrastruktura, `ConfigurationBuilder` kterou můžete používat v aplikaci Webové formuláře, byla modelována podle konceptů používaných v konfiguračním systému ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-250">The `ConfigurationBuilder` infrastructure that you may be using in your Web Forms app was modeled after the concepts used in the ASP.NET Core configuration system.</span></span>

<span data-ttu-id="9bd4b-251">Následující úryvek ukazuje, jak projekt eShopu Web Forms používá *web.config* k ukládání hodnot konfigurace:</span><span class="sxs-lookup"><span data-stu-id="9bd4b-251">The following snippet demonstrates how the Web Forms eShop project uses *web.config* to store configuration values:</span></span>

```xml
<configuration>
  <configSections>
    <section name="entityFramework" type="System.Data.Entity.Internal.ConfigFile.EntityFrameworkSection, EntityFramework, Version=6.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" requirePermission="false" />
  </configSections>
  <connectionStrings>
    <add name="CatalogDBContext" connectionString="Data Source=(localdb)\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;" providerName="System.Data.SqlClient" />
  </connectionStrings>
  <appSettings>
    <add key="UseMockData" value="true" />
    <add key="UseCustomizationData" value="false" />
  </appSettings>
</configuration>
```

<span data-ttu-id="9bd4b-252">Je běžné, že tajné klíče, jako jsou připojovací řetězce databáze, mají být uloženy v souboru *web.config*. Tajné klíče jsou nevyhnutelně trvalé v nezabezpečených místech, jako je například řízení zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-252">It's common for secrets, such as database connection strings, to be stored within the *web.config*. The secrets are inevitably persisted in unsecure locations, such as source control.</span></span> <span data-ttu-id="9bd4b-253">S Blazor na ASP.NET Core, předchozí konfigurace založené na XML je nahrazen a následující JSON:</span><span class="sxs-lookup"><span data-stu-id="9bd4b-253">With Blazor on ASP.NET Core, the preceding XML-based configuration is replaced with the following JSON:</span></span>

```json
{
  "ConnectionStrings": {
    "CatalogDBContext": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;"
  },
  "UseMockData": true,
  "UseCustomizationData": false
}
```

<span data-ttu-id="9bd4b-254">JSON je výchozí konfigurační formát. ASP.NET však Core podporuje mnoho dalších formátů, včetně XML.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-254">JSON is the default configuration format; however, ASP.NET Core supports many other formats, including XML.</span></span> <span data-ttu-id="9bd4b-255">Existuje také několik formátů podporovaných komunitou.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-255">There are also several community-supported formats.</span></span>

<span data-ttu-id="9bd4b-256">Konstruktor ve `Startup` třídě projektu Blazor přijímá `IConfiguration` instanci prostřednictvím techniky DI známé jako vstřikování konstruktoru:</span><span class="sxs-lookup"><span data-stu-id="9bd4b-256">The constructor in the Blazor project's `Startup` class accepts an `IConfiguration` instance through a DI technique known as constructor injection:</span></span>

```csharp
public class Startup
{
    public Startup(IConfiguration configuration, IWebHostEnvironment env)
    {
        Configuration = configuration;
        Env = env;
    }

    ...
}
```

<span data-ttu-id="9bd4b-257">Ve výchozím nastavení proměnné prostředí, soubory JSON (*appsettings.json* a *appsettings.{ Environment}.json*) a možnosti příkazového řádku jsou registrovány jako platné zdroje konfigurace v objektu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-257">By default, environment variables, JSON files (*appsettings.json* and *appsettings.{Environment}.json*), and command-line options are registered as valid configuration sources in the configuration object.</span></span> <span data-ttu-id="9bd4b-258">Ke zdrojům konfigurace lze `Configuration[key]`přistupovat prostřednictvím aplikace .</span><span class="sxs-lookup"><span data-stu-id="9bd4b-258">The configuration sources can be accessed via `Configuration[key]`.</span></span> <span data-ttu-id="9bd4b-259">Pokročilejší technika je svázat konfigurační data s objekty pomocí vzoru voleb.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-259">A more advanced technique is to bind the configuration data to objects using the options pattern.</span></span> <span data-ttu-id="9bd4b-260">Další informace o konfiguraci a vzoru voleb naleznete [v tématu Konfigurace v ASP.NET jádra](/aspnet/core/fundamentals/configuration/) a [vzory Možnosti v ASP.NET jádrem](/aspnet/core/fundamentals/configuration/options).</span><span class="sxs-lookup"><span data-stu-id="9bd4b-260">For more information on configuration and the options pattern, see [Configuration in ASP.NET Core](/aspnet/core/fundamentals/configuration/) and [Options pattern in ASP.NET Core](/aspnet/core/fundamentals/configuration/options), respectively.</span></span>

## <a name="migrate-data-access"></a><span data-ttu-id="9bd4b-261">Migrace přístupu k datům</span><span class="sxs-lookup"><span data-stu-id="9bd4b-261">Migrate data access</span></span>

<span data-ttu-id="9bd4b-262">Přístup k datům je důležitým aspektem každé aplikace.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-262">Data access is an important aspect of any app.</span></span> <span data-ttu-id="9bd4b-263">Projekt eShopu ukládá informace o katalogu do databáze a načítá data pomocí entity Framework (EF) 6.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-263">The eShop project stores catalog information in a database and retrieves the data with Entity Framework (EF) 6.</span></span> <span data-ttu-id="9bd4b-264">Vzhledem k tomu, že EF 6 je podporován v rozhraní .NET Core 3.0, projekt může nadále používat.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-264">Since EF 6 is supported in .NET Core 3.0, the project can continue to use it.</span></span>

<span data-ttu-id="9bd4b-265">Pro eShop byly nutné následující změny týkající se EF:</span><span class="sxs-lookup"><span data-stu-id="9bd4b-265">The following EF-related changes were necessary to eShop:</span></span>

- <span data-ttu-id="9bd4b-266">V rozhraní .NET `DbContext` Framework objekt přijme řetězec *názvu formuláře=ConnectionString* a `ConfigurationManager.AppSettings[ConnectionString]` použije připojovací řetězec z pro připojení.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-266">In .NET Framework, the `DbContext` object accepts a string of the form *name=ConnectionString* and uses the connection string from `ConfigurationManager.AppSettings[ConnectionString]` to connect.</span></span> <span data-ttu-id="9bd4b-267">V rozhraní .NET Core to není podporováno.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-267">In .NET Core, this isn't supported.</span></span> <span data-ttu-id="9bd4b-268">Připojovací řetězec musí být zadán.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-268">The connection string must be supplied.</span></span>
- <span data-ttu-id="9bd4b-269">K databázi bylo přistupováno synchronně.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-269">The database was accessed in a synchronous way.</span></span> <span data-ttu-id="9bd4b-270">I když to funguje, škálovatelnost může trpět.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-270">Though this works, scalability may suffer.</span></span> <span data-ttu-id="9bd4b-271">Tato logika by měla být přesunuta do asynchronní vzor.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-271">This logic should be moved to an asynchronous pattern.</span></span>

<span data-ttu-id="9bd4b-272">I když neexistuje stejná nativní podpora pro vazbu datové sady, Blazor poskytuje flexibilitu a napájení s podporou Jazyka C# na stránce Razor.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-272">Although there isn't the same native support for dataset binding, Blazor provides flexibility and power with its C# support in a Razor page.</span></span> <span data-ttu-id="9bd4b-273">Můžete například provádět výpočty a zobrazit výsledek.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-273">For example, you can perform calculations and display the result.</span></span> <span data-ttu-id="9bd4b-274">Další informace o vzorcích dat v Blazoru najdete v kapitole [Přístup k datům.](data.md)</span><span class="sxs-lookup"><span data-stu-id="9bd4b-274">For more information on data patterns in Blazor, see the [Data access](data.md) chapter.</span></span>

## <a name="architectural-changes"></a><span data-ttu-id="9bd4b-275">Architektonické změny</span><span class="sxs-lookup"><span data-stu-id="9bd4b-275">Architectural changes</span></span>

<span data-ttu-id="9bd4b-276">A konečně, tam jsou některé důležité architektonické rozdíly, aby zvážila při migraci do Blazor.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-276">Finally, there are some important architectural differences to consider when migrating to Blazor.</span></span> <span data-ttu-id="9bd4b-277">Mnohé z těchto změn se vztahují na cokoli na základě .NET Core nebo ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-277">Many of these changes are applicable to anything based on .NET Core or ASP.NET Core.</span></span>

<span data-ttu-id="9bd4b-278">Protože Blazor je postaven na .NET Core, existují důležité informace o zajištění podpory na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-278">Because Blazor is built on .NET Core, there are considerations in ensuring support on .NET Core.</span></span> <span data-ttu-id="9bd4b-279">Některé z hlavních změn patří odstranění následujících funkcí:</span><span class="sxs-lookup"><span data-stu-id="9bd4b-279">Some of the major changes include the removal of the following features:</span></span>

- <span data-ttu-id="9bd4b-280">Více domén aplikací</span><span class="sxs-lookup"><span data-stu-id="9bd4b-280">Multiple AppDomains</span></span>
- <span data-ttu-id="9bd4b-281">Remoting</span><span class="sxs-lookup"><span data-stu-id="9bd4b-281">Remoting</span></span>
- <span data-ttu-id="9bd4b-282">Zabezpečení přístupu kódu (CAS)</span><span class="sxs-lookup"><span data-stu-id="9bd4b-282">Code Access Security (CAS)</span></span>
- <span data-ttu-id="9bd4b-283">Transparentnost zabezpečení</span><span class="sxs-lookup"><span data-stu-id="9bd4b-283">Security Transparency</span></span>

<span data-ttu-id="9bd4b-284">Další informace o technikách k identifikaci nezbytných změn pro podporu spuštěného v jádru .NET naleznete [v tématu Port kódu z rozhraní .NET Framework do .NET Core](/dotnet/core/porting).</span><span class="sxs-lookup"><span data-stu-id="9bd4b-284">For more information on techniques to identify necessary changes to support running on .NET Core, see [Port your code from .NET Framework to .NET Core](/dotnet/core/porting).</span></span>

<span data-ttu-id="9bd4b-285">ASP.NET Core je přepracovaná verze ASP.NET a má některé změny, které se nemusí zpočátku zdát zřejmé.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-285">ASP.NET Core is a reimagined version of ASP.NET and has some changes that may not initially seem obvious.</span></span> <span data-ttu-id="9bd4b-286">Hlavní změny jsou:</span><span class="sxs-lookup"><span data-stu-id="9bd4b-286">The main changes are:</span></span>

- <span data-ttu-id="9bd4b-287">Žádný kontext synchronizace, což znamená, že neexistuje žádný `HttpContext.Current`, `Thread.CurrentPrincipal`, nebo jiné statické přístupové moduly</span><span class="sxs-lookup"><span data-stu-id="9bd4b-287">No synchronization context, which means there's no `HttpContext.Current`, `Thread.CurrentPrincipal`, or other static accessors</span></span>
- <span data-ttu-id="9bd4b-288">Žádné stínové kopírování</span><span class="sxs-lookup"><span data-stu-id="9bd4b-288">No shadow copying</span></span>
- <span data-ttu-id="9bd4b-289">Žádná fronta požadavků</span><span class="sxs-lookup"><span data-stu-id="9bd4b-289">No request queue</span></span>

<span data-ttu-id="9bd4b-290">Mnoho operací v ASP.NET Core jsou asynchronní, což umožňuje snadnější off-loading úlohy vázané na vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-290">Many operations in ASP.NET Core are asynchronous, which allows easier off-loading of I/O-bound tasks.</span></span> <span data-ttu-id="9bd4b-291">Je důležité nikdy blokovat pomocí `Task.Wait()` `Task.GetResult()`nebo , které mohou rychle vyčerpat prostředky fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-291">It's important to never block by using `Task.Wait()` or `Task.GetResult()`, which can quickly exhaust thread pool resources.</span></span>

## <a name="migration-conclusion"></a><span data-ttu-id="9bd4b-292">Závěr o migraci</span><span class="sxs-lookup"><span data-stu-id="9bd4b-292">Migration conclusion</span></span>

<span data-ttu-id="9bd4b-293">V tomto okamžiku jste viděli mnoho příkladů toho, co je zapotřebí k přesunutí projektu webových formulářů do Blazoru.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-293">At this point, you've seen many examples of what it takes to move a Web Forms project to Blazor.</span></span> <span data-ttu-id="9bd4b-294">Úplný příklad najdete v projektu [eShopOnBlazor.](https://github.com/dotnet-architecture/eShopOnBlazor)</span><span class="sxs-lookup"><span data-stu-id="9bd4b-294">For a full example, see the [eShopOnBlazor](https://github.com/dotnet-architecture/eShopOnBlazor) project.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="9bd4b-295">Předchozí</span><span class="sxs-lookup"><span data-stu-id="9bd4b-295">Previous</span></span>](security-authentication-authorization.md)
