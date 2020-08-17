---
title: Spuštění aplikace
description: Naučte se definovat logiku spouštění vaší aplikace.
author: csharpfritz
ms.author: jefritz
ms.date: 02/25/2020
ms.openlocfilehash: ea2ea458011d8351a834aa12db02e5d2bac2dc65
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267695"
---
# <a name="app-startup"></a><span data-ttu-id="31a29-103">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="31a29-103">App startup</span></span>

<span data-ttu-id="31a29-104">Aplikace napsané pro ASP.NET mají typicky `global.asax.cs` soubor, který definuje `Application_Start` událost, která řídí, které služby jsou nakonfigurovány a zpřístupněny pro vykreslování HTML i pro zpracování .NET.</span><span class="sxs-lookup"><span data-stu-id="31a29-104">Applications that are written for ASP.NET typically have a `global.asax.cs` file that defines the `Application_Start` event that controls which services are configured and made available for both HTML rendering and .NET processing.</span></span> <span data-ttu-id="31a29-105">V této kapitole najdete informace o tom, jak se trochu liší od ASP.NET Core a Blazor serveru.</span><span class="sxs-lookup"><span data-stu-id="31a29-105">This chapter looks at how things are slightly different with ASP.NET Core and Blazor Server.</span></span>

## <a name="application_start-and-web-forms"></a><span data-ttu-id="31a29-106">Application_Start a webové formuláře</span><span class="sxs-lookup"><span data-stu-id="31a29-106">Application_Start and Web Forms</span></span>

<span data-ttu-id="31a29-107">Výchozí metoda webových formulářů `Application_Start` vzrostla za několik let a zpracovává mnoho úloh konfigurace.</span><span class="sxs-lookup"><span data-stu-id="31a29-107">The default web forms `Application_Start` method has grown in purpose over years to handle many configuration tasks.</span></span>  <span data-ttu-id="31a29-108">Nový projekt webových formulářů s výchozí šablonou v aplikaci Visual Studio 2019 teď obsahuje následující logiku konfigurace:</span><span class="sxs-lookup"><span data-stu-id="31a29-108">A fresh web forms project with the default template in Visual Studio 2019 now contains the following configuration logic:</span></span>

- <span data-ttu-id="31a29-109">`RouteConfig` – Směrování adres URL aplikace</span><span class="sxs-lookup"><span data-stu-id="31a29-109">`RouteConfig` - Application URL routing</span></span>
- <span data-ttu-id="31a29-110">`BundleConfig` – Sdružování CSS a JavaScriptu a minifikace</span><span class="sxs-lookup"><span data-stu-id="31a29-110">`BundleConfig` - CSS and JavaScript bundling and minification</span></span>

<span data-ttu-id="31a29-111">Každý z těchto jednotlivých souborů se nachází ve `App_Start` složce a spouští se pouze jednou na začátku naší aplikace.</span><span class="sxs-lookup"><span data-stu-id="31a29-111">Each of these individual files reside in the `App_Start` folder and run only once at the start of our application.</span></span>  <span data-ttu-id="31a29-112">`RouteConfig` ve výchozí šabloně projektu přidá `FriendlyUrlSettings` webové formuláře, které umožní adresám URL aplikace vynechat `.ASPX` příponu souboru.</span><span class="sxs-lookup"><span data-stu-id="31a29-112">`RouteConfig` in the default project template adds the `FriendlyUrlSettings` for web forms to allow application URLs to omit the `.ASPX` file extension.</span></span>  <span data-ttu-id="31a29-113">Výchozí šablona obsahuje také direktivu, která poskytuje trvalé stavové kódy přesměrování HTTP (HTTP 301) pro `.ASPX` stránky popisné adresy URL s názvem souboru, který toto rozšíření vynechává.</span><span class="sxs-lookup"><span data-stu-id="31a29-113">The default template also contains a directive that provides permanent HTTP redirect status codes (HTTP 301) for the `.ASPX` pages to the friendly URL with the file name that omits the extension.</span></span>

<span data-ttu-id="31a29-114">Pomocí ASP.NET Core a Blazor jsou tyto metody buď zjednodušené, konsoliduje do `Startup` třídy, nebo jsou z hlediska běžných webových technologií eliminovány.</span><span class="sxs-lookup"><span data-stu-id="31a29-114">With ASP.NET Core and Blazor, these methods are either simplified and consolidated into the `Startup` class or they are eliminated in favor of common web technologies.</span></span>

## <a name="blazor-server-startup-structure"></a><span data-ttu-id="31a29-115">Spouštěcí struktura serveru Blazor</span><span class="sxs-lookup"><span data-stu-id="31a29-115">Blazor Server Startup Structure</span></span>

<span data-ttu-id="31a29-116">Blazor serverové aplikace jsou umístěné na ASP.NET Core 3,0 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="31a29-116">Blazor Server applications reside on top of an ASP.NET Core 3.0 or later application.</span></span>  <span data-ttu-id="31a29-117">ASP.NET Core webové aplikace jsou konfigurovány prostřednictvím páru metod ve třídě v `Startup.cs` kořenové složce aplikace.</span><span class="sxs-lookup"><span data-stu-id="31a29-117">ASP.NET Core web applications are configured through a pair of methods in the `Startup.cs` class on the root folder of the application.</span></span>  <span data-ttu-id="31a29-118">Výchozí obsah spouštěcí třídy je uveden níže.</span><span class="sxs-lookup"><span data-stu-id="31a29-118">The Startup class's default content is listed below</span></span>

```csharp
public class Startup
{
  public Startup(IConfiguration configuration)
  {
    Configuration = configuration;
  }

  public IConfiguration Configuration { get; }

  // This method gets called by the runtime. Use this method to add services to the container.
  // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
  public void ConfigureServices(IServiceCollection services)
  {
    services.AddRazorPages();
    services.AddServerSideBlazor();
    services.AddSingleton<WeatherForecastService>();
  }

  // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
  public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
  {
    if (env.IsDevelopment())
    {
      app.UseDeveloperExceptionPage();
    }
    else
    {
      app.UseExceptionHandler("/Error");
      // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
      app.UseHsts();
    }

    app.UseHttpsRedirection();
    app.UseStaticFiles();

    app.UseRouting();

    app.UseEndpoints(endpoints =>
    {
      endpoints.MapBlazorHub();
      endpoints.MapFallbackToPage("/_Host");
   });
  }
 }
```

<span data-ttu-id="31a29-119">Podobně jako u ostatních ASP.NET Core je třída po spuštění vytvořena se zásadami injektáže závislostí.</span><span class="sxs-lookup"><span data-stu-id="31a29-119">Like the rest of ASP.NET Core, the Startup class is created with dependency injection principles.</span></span>  <span data-ttu-id="31a29-120">`IConfiguration`Je k dispozici pro konstruktor a v případě pozdějšího přístupu během konfigurace může být dočasně vydaný ve vlastnosti Public.</span><span class="sxs-lookup"><span data-stu-id="31a29-120">The `IConfiguration` is provided to the constructor and stashed in a public property for later access during configuration.</span></span>

<span data-ttu-id="31a29-121">`ConfigureServices`Metoda zavedená v ASP.NET Core umožňuje nakonfigurovat různé služby ASP.NET Core Framework pro integrovaný kontejner injektáže závislosti rozhraní.</span><span class="sxs-lookup"><span data-stu-id="31a29-121">The `ConfigureServices` method introduced in ASP.NET Core allows for the various ASP.NET Core framework services to be configured for the framework's built-in dependency injection container.</span></span>  <span data-ttu-id="31a29-122">Mezi různé `services.Add*` metody patří služby, které umožňují používat funkce, jako je ověřování, stránky Razor, směrování kontroléru MVC, signál a interakce Blazor serveru mezi mnoha ostatními.</span><span class="sxs-lookup"><span data-stu-id="31a29-122">The various `services.Add*` methods add services that enable features such as authentication, razor pages, MVC controller routing, SignalR, and Blazor Server interactions among many others.</span></span>  <span data-ttu-id="31a29-123">Tato metoda není ve webových formulářích nutná, protože analýza a zpracování souborů ASPX, ASCX, ASHX a ASMX byly definovány odkazem na ASP.NET v konfiguračním souboru web.config.</span><span class="sxs-lookup"><span data-stu-id="31a29-123">This method was not needed in web forms, as the parsing and handling of the ASPX, ASCX, ASHX, and ASMX files was defined by referencing ASP.NET in the web.config configuration file.</span></span>  <span data-ttu-id="31a29-124">Další informace o vkládání závislostí v ASP.NET Core najdete v [online dokumentaci](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection).</span><span class="sxs-lookup"><span data-stu-id="31a29-124">More information about dependency injection in ASP.NET Core is available in the [online documentation](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection).</span></span>

<span data-ttu-id="31a29-125">`Configure`Metoda zavádí koncept kanálu HTTP na ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="31a29-125">The `Configure` method introduces the concept of the HTTP pipeline to ASP.NET Core.</span></span>  <span data-ttu-id="31a29-126">V této metodě deklarujeme shora dolů [middleware](middleware.md) , který zpracuje všechny požadavky odeslané do naší aplikace.</span><span class="sxs-lookup"><span data-stu-id="31a29-126">In this method, we declare from top to bottom the [Middleware](middleware.md) that will handle every request sent to our application.</span></span> <span data-ttu-id="31a29-127">Většina těchto funkcí ve výchozí konfiguraci byla rozptýlená napříč konfiguračními soubory webových formulářů a teď je na jednom místě pro snadné použití reference.</span><span class="sxs-lookup"><span data-stu-id="31a29-127">Most of these features in the default configuration were scattered across the web forms configuration files and are now in one place for ease of reference.</span></span>

<span data-ttu-id="31a29-128">Již není konfigurací vlastní chybové stránky umístěné v `web.config` souboru, ale nyní je nakonfigurována tak, aby se vždy zobrazila, pokud není v prostředí aplikace označeno `Development` .</span><span class="sxs-lookup"><span data-stu-id="31a29-128">No longer is the configuration of the custom error page placed in a `web.config` file, but now is configured to always be shown if the application environment is not labeled `Development`.</span></span>  <span data-ttu-id="31a29-129">Kromě toho ASP.NET Core aplikace teď nakonfigurované tak, aby ve výchozím nastavení sloužily zabezpečené stránky s protokolem TLS, a to prostřednictvím `UseHttpsRedirection` volání metody.</span><span class="sxs-lookup"><span data-stu-id="31a29-129">Additionally, ASP.NET Core applications are now configured to serve secure pages with TLS by default with the `UseHttpsRedirection` method call.</span></span>

<span data-ttu-id="31a29-130">V dalším kroku je neočekávaná metoda konfigurace uvedená jako `UseStaticFiles` .</span><span class="sxs-lookup"><span data-stu-id="31a29-130">Next, an unexpected configuration method is listed to `UseStaticFiles`.</span></span>  <span data-ttu-id="31a29-131">V ASP.NET Core musí být podpora žádostí o statické soubory (například JavaScript, CSS a obrázkové soubory) explicitně povolená a ve výchozím nastavení budou mít veřejné i jenom soubory ve složce *wwwroot* této aplikace.</span><span class="sxs-lookup"><span data-stu-id="31a29-131">In ASP.NET Core, support for requests for static files (like JavaScript, CSS, and image files) must be explicitly enabled, and only files in the app's *wwwroot* folder are publicly addressable by default.</span></span>

<span data-ttu-id="31a29-132">Další řádek je první, který replikuje jednu z možností konfigurace z webových formulářů: `UseRouting` .</span><span class="sxs-lookup"><span data-stu-id="31a29-132">The next line is the first that replicates one of the configuration options from web forms: `UseRouting`.</span></span>  <span data-ttu-id="31a29-133">Tato metoda přidá směrovač ASP.NET Core do kanálu a může být buď nakonfigurován zde, nebo v jednotlivých souborech, na které může zvážit směrování.</span><span class="sxs-lookup"><span data-stu-id="31a29-133">This method adds the ASP.NET Core router to the pipeline and it can be either configured here or in the individual files that it can consider routing to.</span></span>  <span data-ttu-id="31a29-134">Další informace o konfiguraci směrování najdete v [části směrování](pages-routing-layouts.md).</span><span class="sxs-lookup"><span data-stu-id="31a29-134">More information about routing configuration can be found in the [Routing section](pages-routing-layouts.md).</span></span>

<span data-ttu-id="31a29-135">Poslední příkaz v této metodě definuje koncové body, na kterých ASP.NET Core naslouchá.</span><span class="sxs-lookup"><span data-stu-id="31a29-135">The final statement in this method defines the endpoints that ASP.NET Core is listening on.</span></span>  <span data-ttu-id="31a29-136">Jedná se o dostupná umístění webu, ke kterým můžete přistupovat na webovém serveru a získat nějaký obsah zpracovaný rozhraním .NET a vrátit se na vás.</span><span class="sxs-lookup"><span data-stu-id="31a29-136">These are the web accessible locations that you can access on the web server and receive some content handled by .NET and returned to you.</span></span>  <span data-ttu-id="31a29-137">První položka `MapBlazorHub` nakonfiguruje centrum signalizace pro použití v reálném čase a trvalé připojení k serveru, kde je zpracováván stav a vykreslování komponent Blazor.</span><span class="sxs-lookup"><span data-stu-id="31a29-137">The first entry, `MapBlazorHub` configures a SignalR hub for use in providing the real-time and persistent connection to the server where the state and rendering of Blazor components is handled.</span></span>  <span data-ttu-id="31a29-138">`MapFallbackToPage`Volání metody indikuje umístění stránky přístupné pro web, které spouští aplikaci Blazor, a také nakonfiguruje aplikaci tak, aby zpracovávala požadavky na důkladné propojení od klienta.</span><span class="sxs-lookup"><span data-stu-id="31a29-138">The `MapFallbackToPage` method call indicates the web-accessible location of the page that starts the Blazor application and also configures the application to handle deep-linking requests from the client-side.</span></span>  <span data-ttu-id="31a29-139">Tato funkce se zobrazí v práci, pokud otevřete prohlížeč a přejdete přímo na Blazor zpracovávaný postup ve vaší aplikaci, například `/counter` ve výchozí šabloně projektu.</span><span class="sxs-lookup"><span data-stu-id="31a29-139">You will see this feature at work if you open a browser and navigate directly to Blazor handled route in your application, such as `/counter` in the default project template.</span></span> <span data-ttu-id="31a29-140">Požadavek se zpracuje pomocí stránky *_Host. cshtml* Fallback, která pak spustí směrovač Blazor a vykreslí stránku čítače.</span><span class="sxs-lookup"><span data-stu-id="31a29-140">The request gets handled by the *_Host.cshtml* fallback page, which then runs the Blazor router and renders the counter page.</span></span>

## <a name="upgrading-the-bundleconfig-process"></a><span data-ttu-id="31a29-141">Upgrade procesu BundleConfig</span><span class="sxs-lookup"><span data-stu-id="31a29-141">Upgrading the BundleConfig Process</span></span>

<span data-ttu-id="31a29-142">Technologie pro sdružování prostředků, jako jsou šablony stylů CSS a soubory JavaScriptu, se významně vyvinuly s dalšími technologiemi, které poskytují rychlé vývoj nástrojů a technik pro správu těchto prostředků.</span><span class="sxs-lookup"><span data-stu-id="31a29-142">Technologies for bundling assets like CSS stylesheets and JavaScript files have evolved significantly, with other technologies providing quickly evolving tools and techniques for managing these resources.</span></span>  <span data-ttu-id="31a29-143">K tomuto účelu doporučujeme použít pro zabalení statických prostředků nástroj příkazového řádku Node, jako je Grunt/Gulp/Webpack.</span><span class="sxs-lookup"><span data-stu-id="31a29-143">To this end, we recommend using a Node command-line tool such as Grunt / Gulp / WebPack to package your static assets.</span></span>

<span data-ttu-id="31a29-144">Nástroje příkazového řádku grunt, Gulp a Webpack a jejich přidružené konfigurace je možné do vaší aplikace přidat a ASP.NET Core je během procesu sestavení aplikace tyto soubory v tichém režimu ignorovat.</span><span class="sxs-lookup"><span data-stu-id="31a29-144">The Grunt, Gulp, and WebPack command-line tools and their associated configurations can be added to your application and ASP.NET Core will quietly ignore those files during the application build process.</span></span>  <span data-ttu-id="31a29-145">Můžete přidat volání ke spouštění svých úkolů přidáním `Target` v rámci souboru projektu s syntaxí podobnou následující, která by aktivovala skript Gulp a `min` cíl uvnitř tohoto skriptu.</span><span class="sxs-lookup"><span data-stu-id="31a29-145">You can add a call to run their tasks by adding a `Target` inside your project file with syntax similar to the following that would trigger a gulp script and the `min` target inside that script</span></span>

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="gulp min" />
</Target>
```

<span data-ttu-id="31a29-146">Další podrobnosti o obou strategiích pro správu souborů CSS a JavaScript jsou k dispozici v sadě [prostředků a statické prostředky minimalizuje v dokumentaci ASP.NET Core](https://docs.microsoft.com/aspnet/core/client-side/bundling-and-minification) .</span><span class="sxs-lookup"><span data-stu-id="31a29-146">More details about both strategies to manage your CSS and JavaScript files are available in the [Bundle and minify static assets in ASP.NET Core](https://docs.microsoft.com/aspnet/core/client-side/bundling-and-minification) documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="31a29-147">[Předchozí](project-structure.md) 
> [Další](components.md)</span><span class="sxs-lookup"><span data-stu-id="31a29-147">[Previous](project-structure.md)
[Next](components.md)</span></span>
