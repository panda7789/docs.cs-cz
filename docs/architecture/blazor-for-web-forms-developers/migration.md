---
title: Migrace z webových formulářů ASP.NET na Blazor
description: Naučte se, jak získat přístup k migraci existující aplikace webových formulářů ASP.NET do Blazor.
author: twsouthwick
ms.author: tasou
ms.date: 09/19/2019
ms.openlocfilehash: b614572bd04d9ec694b0feb95173373591d5e117
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144406"
---
# <a name="migrate-from-aspnet-web-forms-to-blazor"></a><span data-ttu-id="8e482-103">Migrace z webových formulářů ASP.NET na Blazor</span><span class="sxs-lookup"><span data-stu-id="8e482-103">Migrate from ASP.NET Web Forms to Blazor</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="8e482-104">Migrace základu kódu z webových formulářů ASP.NET na Blazor je časově náročná úloha, která vyžaduje plánování.</span><span class="sxs-lookup"><span data-stu-id="8e482-104">Migrating a code base from ASP.NET Web Forms to Blazor is a time-consuming task that requires planning.</span></span> <span data-ttu-id="8e482-105">Tato kapitola popisuje proces.</span><span class="sxs-lookup"><span data-stu-id="8e482-105">This chapter outlines the process.</span></span> <span data-ttu-id="8e482-106">Něco, co usnadňuje přechod, je zajistit, že aplikace dodržuje *N-vrstvou* architekturu a v takovém případě je model aplikace (v tomto případě webový formulář) oddělený od obchodní logiky.</span><span class="sxs-lookup"><span data-stu-id="8e482-106">Something that can ease the transition is to ensure the app adheres to an *N-tier* architecture, wherein the app model (in this case, Web Forms) is separate from the business logic.</span></span> <span data-ttu-id="8e482-107">Tato logická oddělení vrstev umožňuje vymazat to, co je potřeba přesunout do .NET Core a Blazor.</span><span class="sxs-lookup"><span data-stu-id="8e482-107">This logical separation of layers makes it clear what needs to move to .NET Core and Blazor.</span></span>

<span data-ttu-id="8e482-108">V tomto příkladu se používá aplikace eShop, která je dostupná na [GitHubu](https://github.com/dotnet-architecture/eShopOnBlazor) .</span><span class="sxs-lookup"><span data-stu-id="8e482-108">For this example, the eShop app available on [GitHub](https://github.com/dotnet-architecture/eShopOnBlazor) is used.</span></span> <span data-ttu-id="8e482-109">eShop je služba katalogu, která poskytuje možnosti CRUD prostřednictvím vstupu a ověření formuláře.</span><span class="sxs-lookup"><span data-stu-id="8e482-109">eShop is a catalog service that provides CRUD capabilities via form entry and validation.</span></span>

<span data-ttu-id="8e482-110">Proč by se měla pracovní aplikace migrovat na Blazor?</span><span class="sxs-lookup"><span data-stu-id="8e482-110">Why should a working app be migrated to Blazor?</span></span> <span data-ttu-id="8e482-111">Mnohokrát není potřeba.</span><span class="sxs-lookup"><span data-stu-id="8e482-111">Many times, there's no need.</span></span> <span data-ttu-id="8e482-112">Webové formuláře ASP.NET budou v mnoha letech i nadále podporovány.</span><span class="sxs-lookup"><span data-stu-id="8e482-112">ASP.NET Web Forms will continue to be supported for many years.</span></span> <span data-ttu-id="8e482-113">Mnohé z funkcí, které Blazor poskytuje, se ale podporují jenom u migrované aplikace.</span><span class="sxs-lookup"><span data-stu-id="8e482-113">However, many of the features that Blazor provides are only supported on a migrated app.</span></span> <span data-ttu-id="8e482-114">Mezi tyto funkce patří:</span><span class="sxs-lookup"><span data-stu-id="8e482-114">Such features include:</span></span>

- <span data-ttu-id="8e482-115">Vylepšení výkonu v rozhraní, jako je například`Span<T>`</span><span class="sxs-lookup"><span data-stu-id="8e482-115">Performance improvements in the framework such as `Span<T>`</span></span>
- <span data-ttu-id="8e482-116">Schopnost spustit jako WebAssembly</span><span class="sxs-lookup"><span data-stu-id="8e482-116">Ability to run as WebAssembly</span></span>
- <span data-ttu-id="8e482-117">Podpora více platforem pro Linux a macOS</span><span class="sxs-lookup"><span data-stu-id="8e482-117">Cross-platform support for Linux and macOS</span></span>
- <span data-ttu-id="8e482-118">Nasazení místního nasazení aplikace nebo sdíleného rozhraní, aniž by to ovlivnilo jiné aplikace</span><span class="sxs-lookup"><span data-stu-id="8e482-118">App-local deployment or shared framework deployment without impacting other apps</span></span>

<span data-ttu-id="8e482-119">Pokud jsou tyto nebo jiné nové funkce přesvědčivější, může se v migraci aplikace nacházet hodnota.</span><span class="sxs-lookup"><span data-stu-id="8e482-119">If these or other new features are compelling enough, there may be value in migrating the app.</span></span> <span data-ttu-id="8e482-120">Migrace může mít různé tvary. může to být celá aplikace nebo jenom některé koncové body, které vyžadují změny.</span><span class="sxs-lookup"><span data-stu-id="8e482-120">The migration can take different shapes; it can be the entire app, or only certain endpoints that require the changes.</span></span> <span data-ttu-id="8e482-121">Rozhodnutí o migraci je v konečném důsledku na základě obchodních problémů, které vývojář vyřeší.</span><span class="sxs-lookup"><span data-stu-id="8e482-121">The decision to migrate is ultimately based on the business problems to be solved by the developer.</span></span>

## <a name="server-side-versus-client-side-hosting"></a><span data-ttu-id="8e482-122">Hostování na straně serveru a na straně klienta</span><span class="sxs-lookup"><span data-stu-id="8e482-122">Server-side versus client-side hosting</span></span>

<span data-ttu-id="8e482-123">Jak je popsáno v kapitole [hostující modely](hosting-models.md) , může být aplikace Blazor hostována dvěma různými způsoby: na straně serveru a na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="8e482-123">As described in the [hosting models](hosting-models.md) chapter, a Blazor app can be hosted in two different ways: server-side and client-side.</span></span> <span data-ttu-id="8e482-124">Model na straně serveru používá ASP.NET Core připojení k signalizaci ke správě aktualizací modelu DOM při spuštění libovolného skutečného kódu na serveru.</span><span class="sxs-lookup"><span data-stu-id="8e482-124">The server-side model uses ASP.NET Core SignalR connections to manage the DOM updates while running any actual code on the server.</span></span> <span data-ttu-id="8e482-125">Model na straně klienta běží v prohlížeči jako WebAssembly a nevyžaduje žádná připojení k serveru.</span><span class="sxs-lookup"><span data-stu-id="8e482-125">The client-side model runs as WebAssembly within a browser and requires no server connections.</span></span> <span data-ttu-id="8e482-126">K dispozici je několik rozdílů, které by mohly ovlivnit, což je nejlepší pro konkrétní aplikaci:</span><span class="sxs-lookup"><span data-stu-id="8e482-126">There are a number of differences that may affect which is best for a specific app:</span></span>

- <span data-ttu-id="8e482-127">Spuštění jako WebAssembly je stále ve vývoji a nemusí podporovat všechny funkce (například vlákna) v aktuálním čase.</span><span class="sxs-lookup"><span data-stu-id="8e482-127">Running as WebAssembly is still in development and may not support all features (such as threading) at the current time</span></span>
- <span data-ttu-id="8e482-128">Komunikace mezi konverzacemi mezi klientem a serverem může způsobit problémy s latencí v režimu na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="8e482-128">Chatty communication between the client and server may cause latency issues in server-side mode</span></span>
- <span data-ttu-id="8e482-129">Přístup k databázím a interním nebo chráněným službám vyžaduje samostatnou službu s hostováním na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="8e482-129">Access to databases and internal or protected services require a separate service with client-side hosting</span></span>

<span data-ttu-id="8e482-130">V době psaní je model na straně serveru podrobněji podobný webovým formulářům.</span><span class="sxs-lookup"><span data-stu-id="8e482-130">At the time of writing, the server-side model more closely resembles Web Forms.</span></span> <span data-ttu-id="8e482-131">Většina této kapitoly se zaměřuje na model hostování na straně serveru, protože je připravený pro produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="8e482-131">Most of this chapter focuses on the server-side hosting model, as it's production-ready.</span></span>

## <a name="create-a-new-project"></a><span data-ttu-id="8e482-132">Vytvoření nového projektu</span><span class="sxs-lookup"><span data-stu-id="8e482-132">Create a new project</span></span>

<span data-ttu-id="8e482-133">Tento krok prvotní migrace je vytvoření nového projektu.</span><span class="sxs-lookup"><span data-stu-id="8e482-133">This initial migration step is to create a new project.</span></span> <span data-ttu-id="8e482-134">Tento typ projektu je založen na projektech stylu sady SDK rozhraní .NET Core a zjednodušuje většinu často používaných vzorů, které byly použity v předchozích formátech projektu.</span><span class="sxs-lookup"><span data-stu-id="8e482-134">This project type is based on the SDK style projects of .NET Core and simplifies much of the boilerplate that was used in previous project formats.</span></span> <span data-ttu-id="8e482-135">Další podrobnosti naleznete v kapitole o [struktuře projektu](project-structure.md).</span><span class="sxs-lookup"><span data-stu-id="8e482-135">For more detail, please see the chapter on [Project Structure](project-structure.md).</span></span>

<span data-ttu-id="8e482-136">Po vytvoření projektu nainstalujte knihovny, které byly použity v předchozím projektu.</span><span class="sxs-lookup"><span data-stu-id="8e482-136">Once the project has been created, install the libraries that were used in the previous project.</span></span> <span data-ttu-id="8e482-137">Ve starších projektech webových formulářů jste pravděpodobně použili soubor *Packages. config* pro výpis požadovaných balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="8e482-137">In older Web Forms projects, you may have used the *packages.config* file to list the required NuGet packages.</span></span> <span data-ttu-id="8e482-138">V novém projektu ve stylu sady SDK byl soubor *Packages. config* nahrazen `<PackageReference>` prvky v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="8e482-138">In the new SDK-style project, *packages.config* has been replaced with `<PackageReference>` elements in the project file.</span></span> <span data-ttu-id="8e482-139">Výhodou tohoto přístupu je, že všechny závislosti se nainstalují po cestách.</span><span class="sxs-lookup"><span data-stu-id="8e482-139">A benefit to this approach is that all dependencies are installed transitively.</span></span> <span data-ttu-id="8e482-140">Vypíšete pouze závislosti nejvyšší úrovně, které vás zajímají.</span><span class="sxs-lookup"><span data-stu-id="8e482-140">You only list the top-level dependencies you care about.</span></span>

<span data-ttu-id="8e482-141">Mnohé ze závislostí, které používáte, jsou k dispozici pro .NET Core, včetně Entity Framework 6 a log4net.</span><span class="sxs-lookup"><span data-stu-id="8e482-141">Many of the dependencies you're using are available for .NET Core, including Entity Framework 6 and log4net.</span></span> <span data-ttu-id="8e482-142">Pokud není k dispozici žádná verze .NET Core nebo .NET Standard, je často možné použít .NET Framework verzi.</span><span class="sxs-lookup"><span data-stu-id="8e482-142">If there's no .NET Core or .NET Standard version available, the .NET Framework version can often be used.</span></span> <span data-ttu-id="8e482-143">Vaše ujetých km se může lišit.</span><span class="sxs-lookup"><span data-stu-id="8e482-143">Your mileage may vary.</span></span> <span data-ttu-id="8e482-144">Jakékoli použité rozhraní API, které není dostupné v .NET Core, způsobí chybu za běhu.</span><span class="sxs-lookup"><span data-stu-id="8e482-144">Any API used that isn't available in .NET Core causes a runtime error.</span></span> <span data-ttu-id="8e482-145">Visual Studio vás upozorní na tyto balíčky.</span><span class="sxs-lookup"><span data-stu-id="8e482-145">Visual Studio notifies you of such packages.</span></span> <span data-ttu-id="8e482-146">Žlutá ikona se zobrazí v uzlu **odkazy** projektu v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="8e482-146">A yellow icon appears on the project's **References** node in **Solution Explorer**.</span></span>

<span data-ttu-id="8e482-147">V projektu eShop založeném na Blazor můžete zobrazit balíčky, které jsou nainstalovány.</span><span class="sxs-lookup"><span data-stu-id="8e482-147">In the Blazor-based eShop project, you can see the packages that are installed.</span></span> <span data-ttu-id="8e482-148">Soubor *Packages. config* byl dřív uveden v každém balíčku, který se používá v projektu, což má za následek to, že soubor bude téměř 50 řádků dlouhý.</span><span class="sxs-lookup"><span data-stu-id="8e482-148">Previously, the *packages.config* file listed every package used in the project, resulting in a file almost 50 lines long.</span></span> <span data-ttu-id="8e482-149">Fragment souboru *Packages. config* je:</span><span class="sxs-lookup"><span data-stu-id="8e482-149">A snippet of *packages.config* is:</span></span>

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

<span data-ttu-id="8e482-150">`<packages>`Element zahrnuje všechny nezbytné závislosti.</span><span class="sxs-lookup"><span data-stu-id="8e482-150">The `<packages>` element includes all necessary dependencies.</span></span> <span data-ttu-id="8e482-151">Je obtížné zjistit, které z těchto balíčků jsou zahrnuty, protože je budete potřebovat.</span><span class="sxs-lookup"><span data-stu-id="8e482-151">It's difficult to identify which of these packages are included because you require them.</span></span> <span data-ttu-id="8e482-152">Některé `<package>` prvky jsou uvedeny jednoduše, aby splňovaly požadavky na závislosti, které požadujete.</span><span class="sxs-lookup"><span data-stu-id="8e482-152">Some `<package>` elements are listed simply to satisfy the needs of dependencies you require.</span></span>

<span data-ttu-id="8e482-153">Projekt Blazor uvádí závislosti, které požadujete v rámci `<ItemGroup>` elementu v souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="8e482-153">The Blazor project lists the dependencies you require within an `<ItemGroup>` element in the project file:</span></span>

```xml
<ItemGroup>
    <PackageReference Include="Autofac" Version="4.9.3" />
    <PackageReference Include="EntityFramework" Version="6.3.0-preview9-19423-04" />
    <PackageReference Include="log4net" Version="2.0.8" />
</ItemGroup>
```

<span data-ttu-id="8e482-154">Jeden balíček NuGet, který zjednodušuje životnost vývojářů webových formulářů, je [Sada Windows Compatibility Pack](../../core/porting/windows-compat-pack.md).</span><span class="sxs-lookup"><span data-stu-id="8e482-154">One NuGet package that simplifies the life of Web Forms developers is the [Windows Compatibility Pack](../../core/porting/windows-compat-pack.md).</span></span> <span data-ttu-id="8e482-155">I když je .NET Core pro různé platformy, některé funkce jsou dostupné jenom ve Windows.</span><span class="sxs-lookup"><span data-stu-id="8e482-155">Although .NET Core is cross-platform, some features are only available on Windows.</span></span> <span data-ttu-id="8e482-156">Funkce specifické pro systém Windows jsou k dispozici po instalaci sady Compatibility Pack.</span><span class="sxs-lookup"><span data-stu-id="8e482-156">Windows-specific features are made available by installing the compatibility pack.</span></span> <span data-ttu-id="8e482-157">Příklady takových funkcí zahrnují Registry, rozhraní WMI a adresářové služby.</span><span class="sxs-lookup"><span data-stu-id="8e482-157">Examples of such features include the Registry, WMI, and Directory Services.</span></span> <span data-ttu-id="8e482-158">Balíček přidává rozhraní API pro 20 000 a aktivuje spoustu služeb, se kterými už možná máte zkušenosti.</span><span class="sxs-lookup"><span data-stu-id="8e482-158">The package adds around 20,000 APIs and activates many services with which you may already be familiar.</span></span> <span data-ttu-id="8e482-159">Projekt eShop nevyžaduje sadu Compatibility Pack. Pokud však vaše projekty používají funkce specifické pro systém Windows, balíček usnadňuje migraci.</span><span class="sxs-lookup"><span data-stu-id="8e482-159">The eShop project doesn't require the compatibility pack; but if your projects use Windows-specific features, the package eases the migration efforts.</span></span>

## <a name="enable-startup-process"></a><span data-ttu-id="8e482-160">Povolit proces po spuštění</span><span class="sxs-lookup"><span data-stu-id="8e482-160">Enable startup process</span></span>

<span data-ttu-id="8e482-161">Proces spuštění pro Blazor se změnil z webových formulářů a následuje podobné nastavení pro další ASP.NET Core služby.</span><span class="sxs-lookup"><span data-stu-id="8e482-161">The startup process for Blazor has changed from Web Forms and follows a similar setup for other ASP.NET Core services.</span></span> <span data-ttu-id="8e482-162">Když jsou hostované komponenty na straně serveru Blazor, spustí se jako součást normální aplikace ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="8e482-162">When hosted server-side, Blazor components are run as part of a normal ASP.NET Core app.</span></span> <span data-ttu-id="8e482-163">Při hostování v prohlížeči pomocí webového sestavení používají komponenty Blazor podobný model hostování.</span><span class="sxs-lookup"><span data-stu-id="8e482-163">When hosted in the browser with WebAssembly, Blazor components use a similar hosting model.</span></span> <span data-ttu-id="8e482-164">Rozdílem je, že komponenty jsou spouštěny jako samostatná služba ze všech back-end procesů.</span><span class="sxs-lookup"><span data-stu-id="8e482-164">The difference is the components are run as a separate service from any of the backend processes.</span></span> <span data-ttu-id="8e482-165">V obou případech je spuštění podobné.</span><span class="sxs-lookup"><span data-stu-id="8e482-165">Either way, the startup is similar.</span></span>

<span data-ttu-id="8e482-166">Soubor *Global.asax.cs* je výchozí spouštěcí stránka pro projekty webových formulářů.</span><span class="sxs-lookup"><span data-stu-id="8e482-166">The *Global.asax.cs* file is the default startup page for Web Forms projects.</span></span> <span data-ttu-id="8e482-167">V projektu eShop tento soubor konfiguruje kontejner inverze ovládacího prvku (IoC) a zpracovává různé události životního cyklu aplikace nebo žádosti.</span><span class="sxs-lookup"><span data-stu-id="8e482-167">In the eShop project, this file configures the Inversion of Control (IoC) container and handles the various lifecycle events of the app or request.</span></span> <span data-ttu-id="8e482-168">Některé z těchto událostí jsou zpracovávány pomocí middlewaru (například `Application_BeginRequest` ).</span><span class="sxs-lookup"><span data-stu-id="8e482-168">Some of these events are handled with middleware (such as `Application_BeginRequest`).</span></span> <span data-ttu-id="8e482-169">Jiné události vyžadují přepsání konkrétních služeb prostřednictvím injektáže závislostí (DI).</span><span class="sxs-lookup"><span data-stu-id="8e482-169">Other events require the overriding of specific services via dependency injection (DI).</span></span>

<span data-ttu-id="8e482-170">Například soubor *Global.asax.cs* pro eshop obsahuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="8e482-170">By way of example, the *Global.asax.cs* file for eShop, contains the following code:</span></span>

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
    /// https://autofaccn.readthedocs.io/en/latest/integration/webforms.html
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

<span data-ttu-id="8e482-171">Předchozí soubor se na `Startup` straně serveru Blazor jako třída:</span><span class="sxs-lookup"><span data-stu-id="8e482-171">The preceding file becomes the `Startup` class in server-side Blazor:</span></span>

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

<span data-ttu-id="8e482-172">Jednu významnou změnu, kterou si můžete všimnout z webových formulářů, je význačnost DI.</span><span class="sxs-lookup"><span data-stu-id="8e482-172">One significant change you may notice from Web Forms is the prominence of DI.</span></span> <span data-ttu-id="8e482-173">DI byl princip identifikátoru GUID v návrhu ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="8e482-173">DI has been a guiding principle in the ASP.NET Core design.</span></span> <span data-ttu-id="8e482-174">Podporuje přizpůsobení téměř všech aspektů ASP.NET Core Frameworku.</span><span class="sxs-lookup"><span data-stu-id="8e482-174">It supports customization of almost all aspects of the ASP.NET Core framework.</span></span> <span data-ttu-id="8e482-175">Existuje i integrovaný poskytovatel služeb, který je možné použít pro mnoho scénářů.</span><span class="sxs-lookup"><span data-stu-id="8e482-175">There's even a built-in service provider that can be used for many scenarios.</span></span> <span data-ttu-id="8e482-176">Pokud je vyžadováno více přizpůsobení, může být podporováno mnoha projekty komunity.</span><span class="sxs-lookup"><span data-stu-id="8e482-176">If more customization is required, it can be supported by the many community projects.</span></span> <span data-ttu-id="8e482-177">Můžete třeba přenášet svoji investici do knihovny DI Library od třetích stran.</span><span class="sxs-lookup"><span data-stu-id="8e482-177">For example, you can carry forward your third-party DI library investment.</span></span>

<span data-ttu-id="8e482-178">V původní aplikaci eShop existuje určitá konfigurace pro správu relací.</span><span class="sxs-lookup"><span data-stu-id="8e482-178">In the original eShop app, there's some configuration for session management.</span></span> <span data-ttu-id="8e482-179">Vzhledem k tomu, že Blazor na straně serveru používá pro komunikaci signál ASP.NET Core, stav relace není podporován, protože připojení mohou vzniknout nezávisle na kontextu HTTP.</span><span class="sxs-lookup"><span data-stu-id="8e482-179">Since server-side Blazor uses ASP.NET Core SignalR for communication, session state isn't supported as the connections may occur independent of an HTTP context.</span></span> <span data-ttu-id="8e482-180">Aplikace, která používá stav relace, vyžaduje před spuštěním jako aplikaci Blazor přearchitekturu.</span><span class="sxs-lookup"><span data-stu-id="8e482-180">An app that uses session state requires rearchitecting before running as a Blazor app.</span></span>

<span data-ttu-id="8e482-181">Další informace o spuštění aplikace najdete v tématu [spuštění aplikace](app-startup.md).</span><span class="sxs-lookup"><span data-stu-id="8e482-181">For more information about app startup, see [App startup](app-startup.md).</span></span>

## <a name="migrate-http-modules-and-handlers-to-middleware"></a><span data-ttu-id="8e482-182">Migrace modulů a obslužných rutin HTTP do middlewaru</span><span class="sxs-lookup"><span data-stu-id="8e482-182">Migrate HTTP modules and handlers to middleware</span></span>

<span data-ttu-id="8e482-183">Moduly a obslužné rutiny HTTP jsou běžné vzory ve webových formulářích pro řízení kanálu požadavků protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="8e482-183">HTTP modules and handlers are common patterns in Web Forms to control the HTTP request pipeline.</span></span> <span data-ttu-id="8e482-184">Třídy, které implementují `IHttpModule` nebo `IHttpHandler` můžou být zaregistrované a zpracovávají příchozí požadavky.</span><span class="sxs-lookup"><span data-stu-id="8e482-184">Classes that implement `IHttpModule` or `IHttpHandler` could be registered and process incoming requests.</span></span> <span data-ttu-id="8e482-185">Webové formuláře nakonfigurují moduly a obslužné rutiny v souboru *Web. config* .</span><span class="sxs-lookup"><span data-stu-id="8e482-185">Web Forms configures modules and handlers in the *web.config* file.</span></span> <span data-ttu-id="8e482-186">Webové formuláře jsou také silně založené na zpracování událostí životního cyklu aplikace.</span><span class="sxs-lookup"><span data-stu-id="8e482-186">Web Forms is also heavily based on app lifecycle event handling.</span></span> <span data-ttu-id="8e482-187">ASP.NET Core místo toho používá middleware.</span><span class="sxs-lookup"><span data-stu-id="8e482-187">ASP.NET Core uses middleware instead.</span></span> <span data-ttu-id="8e482-188">Middleware je zaregistrován v `Configure` metodě `Startup` třídy.</span><span class="sxs-lookup"><span data-stu-id="8e482-188">Middleware is registered in the `Configure` method of the `Startup` class.</span></span> <span data-ttu-id="8e482-189">Pořadí spouštění middlewaru je určeno pořadím registrace.</span><span class="sxs-lookup"><span data-stu-id="8e482-189">Middleware execution order is determined by the registration order.</span></span>

<span data-ttu-id="8e482-190">V části [Povolit proces po spuštění](#enable-startup-process) byla událost životního cyklu vyvolána webovými formuláři jako `Application_BeginRequest` metoda.</span><span class="sxs-lookup"><span data-stu-id="8e482-190">In the [Enable startup process](#enable-startup-process) section, a lifecycle event was raised by Web Forms as the `Application_BeginRequest` method.</span></span> <span data-ttu-id="8e482-191">Tato událost není k dispozici v ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="8e482-191">This event isn't available in ASP.NET Core.</span></span> <span data-ttu-id="8e482-192">Jedním ze způsobů, jak toto chování dosáhnout, je implementovat middleware, jak je vidět v příkladu souboru *Startup.cs* .</span><span class="sxs-lookup"><span data-stu-id="8e482-192">One way to achieve this behavior is to implement middleware as seen in the *Startup.cs* file example.</span></span> <span data-ttu-id="8e482-193">Tento middleware provádí stejnou logiku a následně přenáší řízení na další obslužnou rutinu v kanálu middlewaru.</span><span class="sxs-lookup"><span data-stu-id="8e482-193">This middleware does the same logic and then transfers control to the next handler in the middleware pipeline.</span></span>

<span data-ttu-id="8e482-194">Další informace o migraci modulů a obslužných rutin najdete v tématu [migrace obslužných rutin a modulů HTTP na ASP.NET Core middlewaru](/aspnet/core/migration/http-modules).</span><span class="sxs-lookup"><span data-stu-id="8e482-194">For more information on migrating modules and handlers, see [Migrate HTTP handlers and modules to ASP.NET Core middleware](/aspnet/core/migration/http-modules).</span></span>

## <a name="migrate-static-files"></a><span data-ttu-id="8e482-195">Migrace statických souborů</span><span class="sxs-lookup"><span data-stu-id="8e482-195">Migrate static files</span></span>

<span data-ttu-id="8e482-196">Pro poskytování statických souborů (například HTML, CSS, obrázky a JavaScriptu) musí být soubory vystaveny middlewarem.</span><span class="sxs-lookup"><span data-stu-id="8e482-196">To serve static files (for example, HTML, CSS, images, and JavaScript), the files must be exposed by middleware.</span></span> <span data-ttu-id="8e482-197">Volání `UseStaticFiles` metody umožňuje obsluhu statických souborů z webové kořenové cesty.</span><span class="sxs-lookup"><span data-stu-id="8e482-197">Calling the `UseStaticFiles` method enables the serving of static files from the web root path.</span></span> <span data-ttu-id="8e482-198">Výchozí kořenový adresář webu je *wwwroot*, ale dá se upravit.</span><span class="sxs-lookup"><span data-stu-id="8e482-198">The default web root directory is *wwwroot*, but it can be customized.</span></span> <span data-ttu-id="8e482-199">Jak je zahrnuto v `Configure` metodě třídy eshop `Startup` :</span><span class="sxs-lookup"><span data-stu-id="8e482-199">As included in the `Configure` method of eShop's `Startup` class:</span></span>

```csharp
public void Configure(IApplicationBuilder app)
{
    ...

    app.UseStaticFiles();

    ...
}
```

<span data-ttu-id="8e482-200">Projekt eShop umožňuje základní statický přístup k souborům.</span><span class="sxs-lookup"><span data-stu-id="8e482-200">The eShop project enables basic static file access.</span></span> <span data-ttu-id="8e482-201">K dispozici je mnoho vlastních nastavení pro statický přístup k souborům.</span><span class="sxs-lookup"><span data-stu-id="8e482-201">There are many customizations available for static file access.</span></span> <span data-ttu-id="8e482-202">Informace o povolení výchozích souborů nebo prohlížeče souborů najdete v tématu [statické soubory v ASP.NET Core](/aspnet/core/fundamentals/static-files).</span><span class="sxs-lookup"><span data-stu-id="8e482-202">For information on enabling default files or a file browser, see [Static files in ASP.NET Core](/aspnet/core/fundamentals/static-files).</span></span>

## <a name="migrate-runtime-bundling-and-minification-setup"></a><span data-ttu-id="8e482-203">Migrace modulů runtime a nastavení minifikace</span><span class="sxs-lookup"><span data-stu-id="8e482-203">Migrate runtime bundling and minification setup</span></span>

<span data-ttu-id="8e482-204">Sdružování a minifikace jsou techniky optimalizace výkonu pro omezení počtu a velikosti požadavků serveru na načtení určitých typů souborů.</span><span class="sxs-lookup"><span data-stu-id="8e482-204">Bundling and minification are performance optimization techniques for reducing the number and size of server requests to retrieve certain file types.</span></span> <span data-ttu-id="8e482-205">JavaScript a CSS často přecházejí z nějaké formy sdružování nebo minifikace před odesláním klientovi.</span><span class="sxs-lookup"><span data-stu-id="8e482-205">JavaScript and CSS often undergo some form of bundling or minification before being sent to the client.</span></span> <span data-ttu-id="8e482-206">Ve webových formulářích ASP.NET jsou tyto optimalizace zpracovávány za běhu.</span><span class="sxs-lookup"><span data-stu-id="8e482-206">In ASP.NET Web Forms, these optimizations are handled at runtime.</span></span> <span data-ttu-id="8e482-207">Optimalizační konvence jsou definovány *app_start soubor/bundleconfig.cs* .</span><span class="sxs-lookup"><span data-stu-id="8e482-207">The optimization conventions are defined an *App_Start/BundleConfig.cs* file.</span></span> <span data-ttu-id="8e482-208">V ASP.NET Core je přijímánější deklarativní přístup.</span><span class="sxs-lookup"><span data-stu-id="8e482-208">In ASP.NET Core, a more declarative approach is adopted.</span></span> <span data-ttu-id="8e482-209">Soubor obsahuje seznam souborů, které se mají minifikovaného, spolu s konkrétními nastaveními minifikace.</span><span class="sxs-lookup"><span data-stu-id="8e482-209">A file lists the files to be minified, along with specific minification settings.</span></span>

<span data-ttu-id="8e482-210">Další informace o sdružování a minifikace najdete v tématu [statické prostředky sady prostředků a minimalizuje v ASP.NET Core](/aspnet/core/client-side/bundling-and-minification).</span><span class="sxs-lookup"><span data-stu-id="8e482-210">For more information on bundling and minification, see [Bundle and minify static assets in ASP.NET Core](/aspnet/core/client-side/bundling-and-minification).</span></span>

## <a name="migrate-aspx-pages"></a><span data-ttu-id="8e482-211">Migrovat stránky ASPX</span><span class="sxs-lookup"><span data-stu-id="8e482-211">Migrate ASPX pages</span></span>

<span data-ttu-id="8e482-212">Stránka v aplikaci webových formulářů je soubor s příponou *. aspx* .</span><span class="sxs-lookup"><span data-stu-id="8e482-212">A page in a Web Forms app is a file with the *.aspx* extension.</span></span> <span data-ttu-id="8e482-213">Stránku webových formulářů je často možné namapovat na komponentu v Blazor.</span><span class="sxs-lookup"><span data-stu-id="8e482-213">A Web Forms page can often be mapped to a component in Blazor.</span></span> <span data-ttu-id="8e482-214">Komponenta Blazor je vytvořená v souboru s příponou *. Razor* .</span><span class="sxs-lookup"><span data-stu-id="8e482-214">A Blazor component is authored in a file with the *.razor* extension.</span></span> <span data-ttu-id="8e482-215">Pro projekt eShop se pět stránek převede na stránku Razor.</span><span class="sxs-lookup"><span data-stu-id="8e482-215">For the eShop project, five pages are converted to a Razor page.</span></span>

<span data-ttu-id="8e482-216">Například zobrazení podrobností se skládá ze tří souborů v projektu webových formulářů: *Details. aspx*, *Details.aspx.cs*a *Details.aspx.Designer.cs*.</span><span class="sxs-lookup"><span data-stu-id="8e482-216">For example, the details view is comprised of three files in the Web Forms project: *Details.aspx*, *Details.aspx.cs*, and *Details.aspx.designer.cs*.</span></span> <span data-ttu-id="8e482-217">Při převodu na Blazor jsou kód na pozadí a značky zkombinovány do *Details. Razor*.</span><span class="sxs-lookup"><span data-stu-id="8e482-217">When converting to Blazor, the code-behind and markup are combined into *Details.razor*.</span></span> <span data-ttu-id="8e482-218">Kompilace Razor (ekvivalentní k těm, co je v souborech *. Designer.cs* ), je uložena v adresáři *obj* a ve výchozím nastavení není viditelná v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="8e482-218">Razor compilation (equivalent to what's in *.designer.cs* files) is stored in the *obj* directory and aren't, by default, viewable in **Solution Explorer**.</span></span> <span data-ttu-id="8e482-219">Stránka webových formulářů se skládá z následujících značek:</span><span class="sxs-lookup"><span data-stu-id="8e482-219">The Web Forms page consists of the following markup:</span></span>

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

<span data-ttu-id="8e482-220">Předchozí kód kódu na pozadí obsahuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="8e482-220">The preceding markup's code-behind includes the following code:</span></span>

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

<span data-ttu-id="8e482-221">Při převodu na Blazor se stránka webových formulářů převede na následující kód:</span><span class="sxs-lookup"><span data-stu-id="8e482-221">When converted to Blazor, the Web Forms page translates to the following code:</span></span>

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

<span data-ttu-id="8e482-222">Všimněte si, že kód a značky jsou ve stejném souboru.</span><span class="sxs-lookup"><span data-stu-id="8e482-222">Notice that the code and markup are in the same file.</span></span> <span data-ttu-id="8e482-223">Všechny požadované služby jsou zpřístupněny s `@inject` atributem.</span><span class="sxs-lookup"><span data-stu-id="8e482-223">Any required services are made accessible with the `@inject` attribute.</span></span> <span data-ttu-id="8e482-224">Na základě `@page` této direktivy lze na této stránce přejít v `Catalog/Details/{id}` trase.</span><span class="sxs-lookup"><span data-stu-id="8e482-224">Per the `@page` directive, this page can be accessed at the `Catalog/Details/{id}` route.</span></span> <span data-ttu-id="8e482-225">Hodnota `{id}` zástupného symbolu trasy byla omezena na celé číslo.</span><span class="sxs-lookup"><span data-stu-id="8e482-225">The value of the route's `{id}` placeholder has been constrained to an integer.</span></span> <span data-ttu-id="8e482-226">Jak je popsáno v části [Směrování](pages-routing-layouts.md) na rozdíl od webových formulářů, komponenta Razor explicitně uvádí svou trasu a všechny zahrnuté parametry.</span><span class="sxs-lookup"><span data-stu-id="8e482-226">As described in the [routing](pages-routing-layouts.md) section, unlike Web Forms, a Razor component explicitly states its route and any parameters that are included.</span></span> <span data-ttu-id="8e482-227">Mnoho ovládacích prvků webových formulářů nemůže mít v Blazor stejné protějšky.</span><span class="sxs-lookup"><span data-stu-id="8e482-227">Many Web Forms controls may not have exact counterparts in Blazor.</span></span> <span data-ttu-id="8e482-228">Často se jedná o ekvivalentní fragment kódu HTML, který bude sloužit ke stejnému účelu.</span><span class="sxs-lookup"><span data-stu-id="8e482-228">There's often an equivalent HTML snippet that will serve the same purpose.</span></span> <span data-ttu-id="8e482-229">Například `<asp:Label />` ovládací prvek lze nahradit `<label>` elementem jazyka HTML.</span><span class="sxs-lookup"><span data-stu-id="8e482-229">For example, the `<asp:Label />` control can be replaced with an HTML `<label>` element.</span></span>

### <a name="model-validation-in-blazor"></a><span data-ttu-id="8e482-230">Ověřování modelu v Blazor</span><span class="sxs-lookup"><span data-stu-id="8e482-230">Model validation in Blazor</span></span>

<span data-ttu-id="8e482-231">Pokud váš kód webového formuláře zahrnuje ověřování, můžete přenést většinu z toho, co máte, s méně než nedostatečnými změnami.</span><span class="sxs-lookup"><span data-stu-id="8e482-231">If your Web Forms code includes validation, you can transfer much of what you have with little-to-no changes.</span></span> <span data-ttu-id="8e482-232">Výhodou spuštění v Blazor je, že stejnou logiku ověřování můžete spustit bez nutnosti vlastního JavaScriptu.</span><span class="sxs-lookup"><span data-stu-id="8e482-232">A benefit to running in Blazor is that the same validation logic can be run without needing custom JavaScript.</span></span> <span data-ttu-id="8e482-233">Datové poznámky umožňují snadné ověřování modelu.</span><span class="sxs-lookup"><span data-stu-id="8e482-233">Data annotations enable easy model validation.</span></span>

<span data-ttu-id="8e482-234">Například stránka *vytvořit. aspx* obsahuje formulář pro zadávání dat s ověřením.</span><span class="sxs-lookup"><span data-stu-id="8e482-234">For example, the *Create.aspx* page has a data entry form with validation.</span></span> <span data-ttu-id="8e482-235">Ukázkový fragment kódu by vypadal takto:</span><span class="sxs-lookup"><span data-stu-id="8e482-235">An example snippet would look like this:</span></span>

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

<span data-ttu-id="8e482-236">V Blazor je k dispozici ekvivalentní označení v souboru *Create. Razor* :</span><span class="sxs-lookup"><span data-stu-id="8e482-236">In Blazor, the equivalent markup is provided in a *Create.razor* file:</span></span>

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

<span data-ttu-id="8e482-237">`EditForm`Kontext zahrnuje podporu ověřování a může být zabalen kolem vstupu.</span><span class="sxs-lookup"><span data-stu-id="8e482-237">The `EditForm` context includes validation support and can be wrapped around input.</span></span> <span data-ttu-id="8e482-238">Poznámky k datům představují běžný způsob, jak přidat ověřování.</span><span class="sxs-lookup"><span data-stu-id="8e482-238">Data annotations are a common way to add validation.</span></span> <span data-ttu-id="8e482-239">Taková podpora ověřování se dá přidat prostřednictvím `DataAnnotationsValidator` součásti.</span><span class="sxs-lookup"><span data-stu-id="8e482-239">Such validation support can be added via the `DataAnnotationsValidator` component.</span></span> <span data-ttu-id="8e482-240">Další informace o tomto mechanismu najdete v tématu [ASP.NET Core Blazor Forms and Validation](/aspnet/core/blazor/forms-validation).</span><span class="sxs-lookup"><span data-stu-id="8e482-240">For more information on this mechanism, see [ASP.NET Core Blazor forms and validation](/aspnet/core/blazor/forms-validation).</span></span>

## <a name="migrate-built-in-web-forms-controls"></a><span data-ttu-id="8e482-241">Migrace vestavěných ovládacích prvků webových formulářů</span><span class="sxs-lookup"><span data-stu-id="8e482-241">Migrate built-in Web Forms controls</span></span>

<span data-ttu-id="8e482-242">*Tento obsah už brzy bude.*</span><span class="sxs-lookup"><span data-stu-id="8e482-242">*This content is coming soon.*</span></span>

## <a name="migrate-configuration"></a><span data-ttu-id="8e482-243">Migrace konfigurace</span><span class="sxs-lookup"><span data-stu-id="8e482-243">Migrate configuration</span></span>

<span data-ttu-id="8e482-244">V projektu webových formulářů se konfigurační data nejčastěji ukládají v souboru *Web. config* .</span><span class="sxs-lookup"><span data-stu-id="8e482-244">In a Web Forms project, configuration data is most commonly stored in the *web.config* file.</span></span> <span data-ttu-id="8e482-245">Konfigurační data jsou k dispozici v nástroji `ConfigurationManager` .</span><span class="sxs-lookup"><span data-stu-id="8e482-245">The configuration data is accessed with `ConfigurationManager`.</span></span> <span data-ttu-id="8e482-246">Služby se často vyžadovaly k analýze objektů.</span><span class="sxs-lookup"><span data-stu-id="8e482-246">Services were often required to parse objects.</span></span> <span data-ttu-id="8e482-247">S .NET Framework 4.7.2 bylo možné do konfigurace přidat prostřednictvím `ConfigurationBuilders` .</span><span class="sxs-lookup"><span data-stu-id="8e482-247">With .NET Framework 4.7.2, composability was added to configuration via `ConfigurationBuilders`.</span></span> <span data-ttu-id="8e482-248">Tito tvůrci povolili vývojářům přidat různé zdroje pro konfiguraci, která se pak sestavila za běhu a načetla potřebné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8e482-248">These builders allowed developers to add various sources for configuration that was then composed at runtime to retrieve the necessary values.</span></span>

<span data-ttu-id="8e482-249">ASP.NET Core představil flexibilní konfigurační systém, který umožňuje definovat zdroj konfigurace nebo zdroje používané vaší aplikací a nasazením.</span><span class="sxs-lookup"><span data-stu-id="8e482-249">ASP.NET Core introduced a flexible configuration system that allows you to define the configuration source or sources used by your app and deployment.</span></span> <span data-ttu-id="8e482-250">`ConfigurationBuilder`Infrastruktura, kterou můžete používat v aplikaci webových formulářů, byla modelována za použití konceptů v systému ASP.NET Core Configuration.</span><span class="sxs-lookup"><span data-stu-id="8e482-250">The `ConfigurationBuilder` infrastructure that you may be using in your Web Forms app was modeled after the concepts used in the ASP.NET Core configuration system.</span></span>

<span data-ttu-id="8e482-251">Následující fragment kódu ukazuje, jak projekt eShop webových formulářů používá *Web. config* k ukládání hodnot konfigurace:</span><span class="sxs-lookup"><span data-stu-id="8e482-251">The following snippet demonstrates how the Web Forms eShop project uses *web.config* to store configuration values:</span></span>

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

<span data-ttu-id="8e482-252">Je běžné, že tajné klíče, jako jsou databázové připojovací řetězce, jsou uložené v *souboru Web. config*. Tajné kódy jsou nevyhnutelně trvale uložené v nezabezpečených umístěních, jako je například Správa zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="8e482-252">It's common for secrets, such as database connection strings, to be stored within the *web.config*. The secrets are inevitably persisted in unsecure locations, such as source control.</span></span> <span data-ttu-id="8e482-253">V Blazor v ASP.NET Core je předchozí konfigurace založená na XML nahrazena následujícím kódem JSON:</span><span class="sxs-lookup"><span data-stu-id="8e482-253">With Blazor on ASP.NET Core, the preceding XML-based configuration is replaced with the following JSON:</span></span>

```json
{
  "ConnectionStrings": {
    "CatalogDBContext": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;"
  },
  "UseMockData": true,
  "UseCustomizationData": false
}
```

<span data-ttu-id="8e482-254">JSON je výchozí formát konfigurace; ASP.NET Core však podporuje mnoho dalších formátů, včetně XML.</span><span class="sxs-lookup"><span data-stu-id="8e482-254">JSON is the default configuration format; however, ASP.NET Core supports many other formats, including XML.</span></span> <span data-ttu-id="8e482-255">K dispozici jsou také různé formáty podporované komunitou.</span><span class="sxs-lookup"><span data-stu-id="8e482-255">There are also several community-supported formats.</span></span>

<span data-ttu-id="8e482-256">Konstruktor třídy projektu Blazor `Startup` přijímá `IConfiguration` instanci prostřednictvím metody di známé jako injektáže konstruktoru:</span><span class="sxs-lookup"><span data-stu-id="8e482-256">The constructor in the Blazor project's `Startup` class accepts an `IConfiguration` instance through a DI technique known as constructor injection:</span></span>

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

<span data-ttu-id="8e482-257">Ve výchozím nastavení proměnné prostředí, soubory JSON (*appSettings. JSON* a *appSettings. { Prostředí}. JSON*) a možnosti příkazového řádku jsou registrovány jako platné zdroje konfigurace v objektu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="8e482-257">By default, environment variables, JSON files (*appsettings.json* and *appsettings.{Environment}.json*), and command-line options are registered as valid configuration sources in the configuration object.</span></span> <span data-ttu-id="8e482-258">Ke zdrojům konfigurace je možné přistup prostřednictvím `Configuration[key]` .</span><span class="sxs-lookup"><span data-stu-id="8e482-258">The configuration sources can be accessed via `Configuration[key]`.</span></span> <span data-ttu-id="8e482-259">Pokročilejší technikou je svázání konfiguračních dat s objekty pomocí vzoru možností.</span><span class="sxs-lookup"><span data-stu-id="8e482-259">A more advanced technique is to bind the configuration data to objects using the options pattern.</span></span> <span data-ttu-id="8e482-260">Další informace o konfiguraci a vzoru možností najdete v tématu [konfigurace v ASP.NET Core](/aspnet/core/fundamentals/configuration/) a [vzory možností v ASP.NET Core v](/aspnet/core/fundamentals/configuration/options)uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="8e482-260">For more information on configuration and the options pattern, see [Configuration in ASP.NET Core](/aspnet/core/fundamentals/configuration/) and [Options pattern in ASP.NET Core](/aspnet/core/fundamentals/configuration/options), respectively.</span></span>

## <a name="migrate-data-access"></a><span data-ttu-id="8e482-261">Migrace přístupu k datům</span><span class="sxs-lookup"><span data-stu-id="8e482-261">Migrate data access</span></span>

<span data-ttu-id="8e482-262">Přístup k datům je důležitým aspektem jakékoli aplikace.</span><span class="sxs-lookup"><span data-stu-id="8e482-262">Data access is an important aspect of any app.</span></span> <span data-ttu-id="8e482-263">Projekt eShop ukládá informace o katalogu do databáze a načítá data pomocí Entity Framework (EF) 6.</span><span class="sxs-lookup"><span data-stu-id="8e482-263">The eShop project stores catalog information in a database and retrieves the data with Entity Framework (EF) 6.</span></span> <span data-ttu-id="8e482-264">Vzhledem k tomu, že se v .NET Core 3,0 podporuje EF 6, projekt ho může i nadále používat.</span><span class="sxs-lookup"><span data-stu-id="8e482-264">Since EF 6 is supported in .NET Core 3.0, the project can continue to use it.</span></span>

<span data-ttu-id="8e482-265">Následující změny související s EF byly nutné pro eShop:</span><span class="sxs-lookup"><span data-stu-id="8e482-265">The following EF-related changes were necessary to eShop:</span></span>

- <span data-ttu-id="8e482-266">V .NET Framework `DbContext` objekt přijímá řetězec ve tvaru *název = ConnectionString* a používá připojovací řetězec z `ConfigurationManager.AppSettings[ConnectionString]` k připojení.</span><span class="sxs-lookup"><span data-stu-id="8e482-266">In .NET Framework, the `DbContext` object accepts a string of the form *name=ConnectionString* and uses the connection string from `ConfigurationManager.AppSettings[ConnectionString]` to connect.</span></span> <span data-ttu-id="8e482-267">V rozhraní .NET Core to není podporováno.</span><span class="sxs-lookup"><span data-stu-id="8e482-267">In .NET Core, this isn't supported.</span></span> <span data-ttu-id="8e482-268">Připojovací řetězec musí být dodán.</span><span class="sxs-lookup"><span data-stu-id="8e482-268">The connection string must be supplied.</span></span>
- <span data-ttu-id="8e482-269">K databázi došlo synchronním způsobem.</span><span class="sxs-lookup"><span data-stu-id="8e482-269">The database was accessed in a synchronous way.</span></span> <span data-ttu-id="8e482-270">I když to funguje, může dojít ke zhoršení škálovatelnosti.</span><span class="sxs-lookup"><span data-stu-id="8e482-270">Though this works, scalability may suffer.</span></span> <span data-ttu-id="8e482-271">Tato logika by se měla přesunout do asynchronního vzoru.</span><span class="sxs-lookup"><span data-stu-id="8e482-271">This logic should be moved to an asynchronous pattern.</span></span>

<span data-ttu-id="8e482-272">I když se nejedná o stejnou nativní podporu vazby datové sady, Blazor poskytuje flexibilitu a výkon díky podpoře C# na stránce Razor.</span><span class="sxs-lookup"><span data-stu-id="8e482-272">Although there isn't the same native support for dataset binding, Blazor provides flexibility and power with its C# support in a Razor page.</span></span> <span data-ttu-id="8e482-273">Můžete například provádět výpočty a zobrazovat výsledek.</span><span class="sxs-lookup"><span data-stu-id="8e482-273">For example, you can perform calculations and display the result.</span></span> <span data-ttu-id="8e482-274">Další informace o vzorech dat v Blazor naleznete v kapitole [přístup k datům](data.md) .</span><span class="sxs-lookup"><span data-stu-id="8e482-274">For more information on data patterns in Blazor, see the [Data access](data.md) chapter.</span></span>

## <a name="architectural-changes"></a><span data-ttu-id="8e482-275">Změny architektury</span><span class="sxs-lookup"><span data-stu-id="8e482-275">Architectural changes</span></span>

<span data-ttu-id="8e482-276">Nakonec existují některé důležité rozdíly v architektuře, které je potřeba vzít v úvahu při migraci na Blazor.</span><span class="sxs-lookup"><span data-stu-id="8e482-276">Finally, there are some important architectural differences to consider when migrating to Blazor.</span></span> <span data-ttu-id="8e482-277">Mnohé z těchto změn platí pro cokoli na základě .NET Core nebo ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="8e482-277">Many of these changes are applicable to anything based on .NET Core or ASP.NET Core.</span></span>

<span data-ttu-id="8e482-278">Vzhledem k tomu, že Blazor je postaven na rozhraní .NET Core, existují důvody pro zajištění podpory .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8e482-278">Because Blazor is built on .NET Core, there are considerations in ensuring support on .NET Core.</span></span> <span data-ttu-id="8e482-279">Některé z hlavních změn zahrnují odebrání následujících funkcí:</span><span class="sxs-lookup"><span data-stu-id="8e482-279">Some of the major changes include the removal of the following features:</span></span>

- <span data-ttu-id="8e482-280">Více objektů třídy AppDomains</span><span class="sxs-lookup"><span data-stu-id="8e482-280">Multiple AppDomains</span></span>
- <span data-ttu-id="8e482-281">Vzdálenou</span><span class="sxs-lookup"><span data-stu-id="8e482-281">Remoting</span></span>
- <span data-ttu-id="8e482-282">Zabezpečení přístupu kódu (CAS)</span><span class="sxs-lookup"><span data-stu-id="8e482-282">Code Access Security (CAS)</span></span>
- <span data-ttu-id="8e482-283">Transparentnost zabezpečení</span><span class="sxs-lookup"><span data-stu-id="8e482-283">Security Transparency</span></span>

<span data-ttu-id="8e482-284">Další informace o technikách, které identifikují nezbytné změny v podpoře používání .NET Core, najdete v tématu [portování kódu z .NET Framework do .NET Core](/dotnet/core/porting).</span><span class="sxs-lookup"><span data-stu-id="8e482-284">For more information on techniques to identify necessary changes to support running on .NET Core, see [Port your code from .NET Framework to .NET Core](/dotnet/core/porting).</span></span>

<span data-ttu-id="8e482-285">ASP.NET Core je přepracované verze ASP.NET a obsahuje některé změny, které nemusí zpočátku vypadat zjevně.</span><span class="sxs-lookup"><span data-stu-id="8e482-285">ASP.NET Core is a reimagined version of ASP.NET and has some changes that may not initially seem obvious.</span></span> <span data-ttu-id="8e482-286">Hlavní změny:</span><span class="sxs-lookup"><span data-stu-id="8e482-286">The main changes are:</span></span>

- <span data-ttu-id="8e482-287">Žádný kontext synchronizace, což znamená, že nejsou k dispozici žádné `HttpContext.Current` , `Thread.CurrentPrincipal` nebo jiné statické přistupující objekty</span><span class="sxs-lookup"><span data-stu-id="8e482-287">No synchronization context, which means there's no `HttpContext.Current`, `Thread.CurrentPrincipal`, or other static accessors</span></span>
- <span data-ttu-id="8e482-288">Bez stínového kopírování</span><span class="sxs-lookup"><span data-stu-id="8e482-288">No shadow copying</span></span>
- <span data-ttu-id="8e482-289">Žádná fronta žádostí</span><span class="sxs-lookup"><span data-stu-id="8e482-289">No request queue</span></span>

<span data-ttu-id="8e482-290">Mnoho operací v ASP.NET Core je asynchronní, což umožňuje snazší načítat vstupně-výstupní úlohy vázané na vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="8e482-290">Many operations in ASP.NET Core are asynchronous, which allows easier off-loading of I/O-bound tasks.</span></span> <span data-ttu-id="8e482-291">Je důležité nikdy neblokovat pomocí `Task.Wait()` nebo `Task.GetResult()` , což může rychle vyčerpat prostředky fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="8e482-291">It's important to never block by using `Task.Wait()` or `Task.GetResult()`, which can quickly exhaust thread pool resources.</span></span>

## <a name="migration-conclusion"></a><span data-ttu-id="8e482-292">Závěr migrace</span><span class="sxs-lookup"><span data-stu-id="8e482-292">Migration conclusion</span></span>

<span data-ttu-id="8e482-293">V tomto okamžiku jste viděli spoustu příkladů toho, co je potřeba k přesunutí projektu webových formulářů do Blazor.</span><span class="sxs-lookup"><span data-stu-id="8e482-293">At this point, you've seen many examples of what it takes to move a Web Forms project to Blazor.</span></span> <span data-ttu-id="8e482-294">Úplný příklad naleznete v projektu [eShopOnBlazor](https://github.com/dotnet-architecture/eShopOnBlazor) .</span><span class="sxs-lookup"><span data-stu-id="8e482-294">For a full example, see the [eShopOnBlazor](https://github.com/dotnet-architecture/eShopOnBlazor) project.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="8e482-295">Předchozí</span><span class="sxs-lookup"><span data-stu-id="8e482-295">Previous</span></span>](security-authentication-authorization.md)
