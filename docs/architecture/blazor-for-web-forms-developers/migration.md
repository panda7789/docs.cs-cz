---
title: Migrace z webových formulářů ASP.NET na Blazor
description: Naučte se, jak získat přístup k migraci existující aplikace webových formulářů ASP.NET do Blazor .
author: twsouthwick
ms.author: tasou
no-loc:
- Blazor
- WebAssembly
ms.date: 09/19/2019
ms.openlocfilehash: ca3d8747b02602c89aec187ea0826e658fb0cbc4
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267799"
---
# <a name="migrate-from-aspnet-web-forms-to-no-locblazor"></a>Migrace z webových formulářů ASP.NET na Blazor

Migrace základu kódu z webových formulářů ASP.NET na Blazor je časově náročná úloha, která vyžaduje plánování. Tato kapitola popisuje proces. Něco, co usnadňuje přechod, je zajistit, že aplikace dodržuje *N-vrstvou* architekturu a v takovém případě je model aplikace (v tomto případě webový formulář) oddělený od obchodní logiky. Tato logická oddělení vrstev umožňuje vymazat to, co je potřeba přesunout do .NET Core a Blazor .

V tomto příkladu se používá aplikace eShop, která je dostupná na [GitHubu](https://github.com/dotnet-architecture/eShopOnBlazor) . eShop je služba katalogu, která poskytuje možnosti CRUD prostřednictvím vstupu a ověření formuláře.

Proč by se měla migrovat pracovní aplikace na Blazor ? Mnohokrát není potřeba. Webové formuláře ASP.NET budou v mnoha letech i nadále podporovány. Mnohé z funkcí, které nabízí, ale Blazor podporují jenom migrované aplikace. Mezi tyto funkce patří:

- Vylepšení výkonu v rozhraní, jako je například `Span<T>`
- Možnost spuštění jako WebAssembly
- Podpora více platforem pro Linux a macOS
- Nasazení místního nasazení aplikace nebo sdíleného rozhraní, aniž by to ovlivnilo jiné aplikace

Pokud jsou tyto nebo jiné nové funkce přesvědčivější, může se v migraci aplikace nacházet hodnota. Migrace může mít různé tvary. může to být celá aplikace nebo jenom některé koncové body, které vyžadují změny. Rozhodnutí o migraci je v konečném důsledku na základě obchodních problémů, které vývojář vyřeší.

## <a name="server-side-versus-client-side-hosting"></a>Hostování na straně serveru a na straně klienta

Jak je popsáno v kapitole [hostující modely](hosting-models.md) , Blazor aplikace může být hostována dvěma různými způsoby: na straně serveru a na straně klienta. Model na straně serveru používá ASP.NET Core připojení k signalizaci ke správě aktualizací modelu DOM při spuštění libovolného skutečného kódu na serveru. Model na straně klienta se spouští jako WebAssembly v prohlížeči a nevyžaduje žádná připojení k serveru. K dispozici je několik rozdílů, které by mohly ovlivnit, což je nejlepší pro konkrétní aplikaci:

- Běží tak, jak WebAssembly je stále ve vývoji, a nemusí podporovat všechny funkce (například vlákna) v aktuálním čase.
- Komunikace mezi konverzacemi mezi klientem a serverem může způsobit problémy s latencí v režimu na straně serveru.
- Přístup k databázím a interním nebo chráněným službám vyžaduje samostatnou službu s hostováním na straně klienta.

V době psaní je model na straně serveru podrobněji podobný webovým formulářům. Většina této kapitoly se zaměřuje na model hostování na straně serveru, protože je připravený pro produkční prostředí.

## <a name="create-a-new-project"></a>Vytvoření nového projektu

Tento krok prvotní migrace je vytvoření nového projektu. Tento typ projektu je založen na projektech stylu sady SDK rozhraní .NET Core a zjednodušuje většinu často používaných vzorů, které byly použity v předchozích formátech projektu. Další podrobnosti naleznete v kapitole o [struktuře projektu](project-structure.md).

Po vytvoření projektu nainstalujte knihovny, které byly použity v předchozím projektu. V dřívějších projektech webových formulářů jste pravděpodobně použili soubor *packages.config* k vypsání požadovaných balíčků NuGet. V novém projektu ve stylu sady SDK byla *packages.config* nahrazena `<PackageReference>` prvky v souboru projektu. Výhodou tohoto přístupu je, že všechny závislosti se nainstalují po cestách. Vypíšete pouze závislosti nejvyšší úrovně, které vás zajímají.

Mnohé ze závislostí, které používáte, jsou k dispozici pro .NET Core, včetně Entity Framework 6 a log4net. Pokud není k dispozici žádná verze .NET Core nebo .NET Standard, je často možné použít .NET Framework verzi. Vaše ujetých km se může lišit. Jakékoli použité rozhraní API, které není dostupné v .NET Core, způsobí chybu za běhu. Visual Studio vás upozorní na tyto balíčky. Žlutá ikona se zobrazí v uzlu **odkazy** projektu v **Průzkumník řešení**.

V Blazor projektu eshop založeném na službě můžete vidět balíčky, které jsou nainstalovány. Dříve soubor *packages.config* uvedený v každém balíčku, který je v projektu použit, což má za následek to, že soubor bude téměř 50 řádků dlouhý. Fragment *packages.config* je:

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

`<packages>`Element zahrnuje všechny nezbytné závislosti. Je obtížné zjistit, které z těchto balíčků jsou zahrnuty, protože je budete potřebovat. Některé `<package>` prvky jsou uvedeny jednoduše, aby splňovaly požadavky na závislosti, které požadujete.

BlazorProjekt uvádí závislosti, které požadujete v rámci `<ItemGroup>` elementu v souboru projektu:

```xml
<ItemGroup>
    <PackageReference Include="Autofac" Version="4.9.3" />
    <PackageReference Include="EntityFramework" Version="6.3.0-preview9-19423-04" />
    <PackageReference Include="log4net" Version="2.0.8" />
</ItemGroup>
```

Jeden balíček NuGet, který zjednodušuje životnost vývojářů webových formulářů, je [Sada Windows Compatibility Pack](../../core/porting/windows-compat-pack.md). I když je .NET Core pro různé platformy, některé funkce jsou dostupné jenom ve Windows. Funkce specifické pro systém Windows jsou k dispozici po instalaci sady Compatibility Pack. Příklady takových funkcí zahrnují Registry, rozhraní WMI a adresářové služby. Balíček přidává rozhraní API pro 20 000 a aktivuje spoustu služeb, se kterými už možná máte zkušenosti. Projekt eShop nevyžaduje sadu Compatibility Pack. Pokud však vaše projekty používají funkce specifické pro systém Windows, balíček usnadňuje migraci.

## <a name="enable-startup-process"></a>Povolit proces po spuštění

Proces spuštění pro Blazor byl změněn z webových formulářů a následuje podobné nastavení pro jiné ASP.NET Core služby. Když jsou hostované serverové Blazor komponenty spouštěné jako součást normální ASP.NET Core aplikace. Při hostování v prohlížeči pomocí nástroje WebAssembly Blazor komponenty používají podobný model hostování. Rozdílem je, že komponenty jsou spouštěny jako samostatná služba ze všech back-end procesů. V obou případech je spuštění podobné.

Soubor *Global.asax.cs* je výchozí spouštěcí stránka pro projekty webových formulářů. V projektu eShop tento soubor konfiguruje kontejner inverze ovládacího prvku (IoC) a zpracovává různé události životního cyklu aplikace nebo žádosti. Některé z těchto událostí jsou zpracovávány pomocí middlewaru (například `Application_BeginRequest` ). Jiné události vyžadují přepsání konkrétních služeb prostřednictvím injektáže závislostí (DI).

Například soubor *Global.asax.cs* pro eshop obsahuje následující kód:

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

Předchozí soubor se na `Startup` straně serveru stal třídou Blazor :

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

Jednu významnou změnu, kterou si můžete všimnout z webových formulářů, je význačnost DI. DI byl princip identifikátoru GUID v návrhu ASP.NET Core. Podporuje přizpůsobení téměř všech aspektů ASP.NET Core Frameworku. Existuje i integrovaný poskytovatel služeb, který je možné použít pro mnoho scénářů. Pokud je vyžadováno více přizpůsobení, může být podporováno mnoha projekty komunity. Můžete třeba přenášet svoji investici do knihovny DI Library od třetích stran.

V původní aplikaci eShop existuje určitá konfigurace pro správu relací. Vzhledem k tomu, že na straně serveru Blazor používá nástroj ASP.NET Core signalizace pro komunikaci, není stav relace podporován, protože připojení mohou vzniknout nezávisle na kontextu http. Aplikace, která používá stav relace, vyžaduje přearchitekturu před spuštěním jako Blazor aplikaci.

Další informace o spuštění aplikace najdete v tématu [spuštění aplikace](app-startup.md).

## <a name="migrate-http-modules-and-handlers-to-middleware"></a>Migrace modulů a obslužných rutin HTTP do middlewaru

Moduly a obslužné rutiny HTTP jsou běžné vzory ve webových formulářích pro řízení kanálu požadavků protokolu HTTP. Třídy, které implementují `IHttpModule` nebo `IHttpHandler` můžou být zaregistrované a zpracovávají příchozí požadavky. Webové formuláře nakonfigurují moduly a obslužné rutiny v souboru *web.config* . Webové formuláře jsou také silně založené na zpracování událostí životního cyklu aplikace. ASP.NET Core místo toho používá middleware. Middleware je zaregistrován v `Configure` metodě `Startup` třídy. Pořadí spouštění middlewaru je určeno pořadím registrace.

V části [Povolit proces po spuštění](#enable-startup-process) byla událost životního cyklu vyvolána webovými formuláři jako `Application_BeginRequest` metoda. Tato událost není k dispozici v ASP.NET Core. Jedním ze způsobů, jak toto chování dosáhnout, je implementovat middleware, jak je vidět v příkladu souboru *Startup.cs* . Tento middleware provádí stejnou logiku a následně přenáší řízení na další obslužnou rutinu v kanálu middlewaru.

Další informace o migraci modulů a obslužných rutin najdete v tématu [migrace obslužných rutin a modulů HTTP na ASP.NET Core middlewaru](/aspnet/core/migration/http-modules).

## <a name="migrate-static-files"></a>Migrace statických souborů

Pro poskytování statických souborů (například HTML, CSS, obrázky a JavaScriptu) musí být soubory vystaveny middlewarem. Volání `UseStaticFiles` metody umožňuje obsluhu statických souborů z webové kořenové cesty. Výchozí kořenový adresář webu je *wwwroot*, ale dá se upravit. Jak je zahrnuto v `Configure` metodě třídy eshop `Startup` :

```csharp
public void Configure(IApplicationBuilder app)
{
    ...

    app.UseStaticFiles();

    ...
}
```

Projekt eShop umožňuje základní statický přístup k souborům. K dispozici je mnoho vlastních nastavení pro statický přístup k souborům. Informace o povolení výchozích souborů nebo prohlížeče souborů najdete v tématu [statické soubory v ASP.NET Core](/aspnet/core/fundamentals/static-files).

## <a name="migrate-runtime-bundling-and-minification-setup"></a>Migrace modulů runtime a nastavení minifikace

Sdružování a minifikace jsou techniky optimalizace výkonu pro omezení počtu a velikosti požadavků serveru na načtení určitých typů souborů. JavaScript a CSS často přecházejí z nějaké formy sdružování nebo minifikace před odesláním klientovi. Ve webových formulářích ASP.NET jsou tyto optimalizace zpracovávány za běhu. Optimalizační konvence jsou definovány *app_start soubor/bundleconfig.cs* . V ASP.NET Core je přijímánější deklarativní přístup. Soubor obsahuje seznam souborů, které se mají minifikovaného, spolu s konkrétními nastaveními minifikace.

Další informace o sdružování a minifikace najdete v tématu [statické prostředky sady prostředků a minimalizuje v ASP.NET Core](/aspnet/core/client-side/bundling-and-minification).

## <a name="migrate-aspx-pages"></a>Migrovat stránky ASPX

Stránka v aplikaci webových formulářů je soubor s příponou *. aspx* . Stránka webových formulářů je často mapována na komponentu v nástroji Blazor . BlazorKomponenta je vytvořená v souboru s příponou *. Razor* . Pro projekt eShop se pět stránek převede na stránku Razor.

Například zobrazení podrobností obsahuje tři soubory v projektu webových formulářů: *Details. aspx*, *Details.aspx.cs*a *Details.aspx.Designer.cs*. Při převodu na Blazor je kód na pozadí a označení zkombinován do *Details. Razor*. Kompilace Razor (ekvivalentní k těm, co je v souborech *. Designer.cs* ), je uložena v adresáři *obj* a ve výchozím nastavení není viditelná v **Průzkumník řešení**. Stránka webových formulářů se skládá z následujících značek:

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

Předchozí kód kódu na pozadí obsahuje následující kód:

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

Při převodu na Blazor se stránka webových formulářů převede na následující kód:

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

Všimněte si, že kód a značky jsou ve stejném souboru. Všechny požadované služby jsou zpřístupněny s `@inject` atributem. Na základě `@page` této direktivy lze na této stránce přejít v `Catalog/Details/{id}` trase. Hodnota `{id}` zástupného symbolu trasy byla omezena na celé číslo. Jak je popsáno v části [Směrování](pages-routing-layouts.md) na rozdíl od webových formulářů, komponenta Razor explicitně uvádí svou trasu a všechny zahrnuté parametry. Mnoho ovládacích prvků webových formulářů nemůže mít přesnou protějšek v Blazor . Často se jedná o ekvivalentní fragment kódu HTML, který bude sloužit ke stejnému účelu. Například `<asp:Label />` ovládací prvek lze nahradit `<label>` elementem jazyka HTML.

### <a name="model-validation-in-no-locblazor"></a>Ověřování modelu v Blazor

Pokud váš kód webového formuláře zahrnuje ověřování, můžete přenést většinu z toho, co máte, s méně než nedostatečnými změnami. Výhodou pro spuštění v Blazor je, že stejnou logiku ověřování můžete spustit bez nutnosti vlastního JavaScriptu. Datové poznámky umožňují snadné ověřování modelu.

Například stránka *vytvořit. aspx* obsahuje formulář pro zadávání dat s ověřením. Ukázkový fragment kódu by vypadal takto:

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

V je Blazor ekvivalentní označení k dispozici v souboru *Create. Razor* :

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

`EditForm`Kontext zahrnuje podporu ověřování a může být zabalen kolem vstupu. Poznámky k datům představují běžný způsob, jak přidat ověřování. Taková podpora ověřování se dá přidat prostřednictvím `DataAnnotationsValidator` součásti. Další informace o tomto mechanismu najdete v tématu [ASP.NET Core Blazor Forms a ověřování](/aspnet/core/blazor/forms-validation).

## <a name="migrate-built-in-web-forms-controls"></a>Migrace vestavěných ovládacích prvků webových formulářů

*Tento obsah už brzy bude.*

## <a name="migrate-configuration"></a>Migrace konfigurace

V projektu webových formulářů se konfigurační data nejčastěji ukládají do souboru *web.config* . Konfigurační data jsou k dispozici v nástroji `ConfigurationManager` . Služby se často vyžadovaly k analýze objektů. S .NET Framework 4.7.2 bylo možné do konfigurace přidat prostřednictvím `ConfigurationBuilders` . Tito tvůrci povolili vývojářům přidat různé zdroje pro konfiguraci, která se pak sestavila za běhu a načetla potřebné hodnoty.

ASP.NET Core představil flexibilní konfigurační systém, který umožňuje definovat zdroj konfigurace nebo zdroje používané vaší aplikací a nasazením. `ConfigurationBuilder`Infrastruktura, kterou můžete používat v aplikaci webových formulářů, byla modelována za použití konceptů v systému ASP.NET Core Configuration.

Následující fragment kódu ukazuje, jak projekt eShop webových formulářů používá *web.config* k ukládání hodnot konfigurace:

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

Je běžné, že tajné klíče, například databázové připojovací řetězce, budou uloženy v rámci *web.config*. Tajné kódy jsou nevyhnutelně trvale uložené v nezabezpečených umístěních, jako je například Správa zdrojového kódu. V Blazor případě ASP.NET Core je předchozí konfigurace založená na XML nahrazena následujícím kódem JSON:

```json
{
  "ConnectionStrings": {
    "CatalogDBContext": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;"
  },
  "UseMockData": true,
  "UseCustomizationData": false
}
```

JSON je výchozí formát konfigurace; ASP.NET Core však podporuje mnoho dalších formátů, včetně XML. K dispozici jsou také různé formáty podporované komunitou.

Konstruktor Blazor `Startup` třídy projektu přijímá `IConfiguration` instanci prostřednictvím metody di známé jako injektáže konstruktoru:

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

Ve výchozím nastavení proměnné prostředí, soubory JSON (*appsettings.jsna* a *appSettings. { Prostředí}. JSON*) a možnosti příkazového řádku jsou registrovány jako platné zdroje konfigurace v objektu konfigurace. Ke zdrojům konfigurace je možné přistup prostřednictvím `Configuration[key]` . Pokročilejší technikou je svázání konfiguračních dat s objekty pomocí vzoru možností. Další informace o konfiguraci a vzoru možností najdete v tématu [konfigurace v ASP.NET Core](/aspnet/core/fundamentals/configuration/) a [vzory možností v ASP.NET Core v](/aspnet/core/fundamentals/configuration/options)uvedeném pořadí.

## <a name="migrate-data-access"></a>Migrace přístupu k datům

Přístup k datům je důležitým aspektem jakékoli aplikace. Projekt eShop ukládá informace o katalogu do databáze a načítá data pomocí Entity Framework (EF) 6. Vzhledem k tomu, že se v .NET Core 3,0 podporuje EF 6, projekt ho může i nadále používat.

Následující změny související s EF byly nutné pro eShop:

- V .NET Framework `DbContext` objekt přijímá řetězec ve tvaru *název = ConnectionString* a používá připojovací řetězec z `ConfigurationManager.AppSettings[ConnectionString]` k připojení. V rozhraní .NET Core to není podporováno. Připojovací řetězec musí být dodán.
- K databázi došlo synchronním způsobem. I když to funguje, může dojít ke zhoršení škálovatelnosti. Tato logika by se měla přesunout do asynchronního vzoru.

I když se nejedná o stejnou nativní podporu vazby datové sady, Blazor poskytuje flexibilitu a výkon díky podpoře C# na stránce Razor. Můžete například provádět výpočty a zobrazovat výsledek. Další informace o vzorech dat v nástroji Blazor naleznete v kapitole [přístup k datům](data.md) .

## <a name="architectural-changes"></a>Změny architektury

Nakonec existují některé důležité rozdíly architektury, které je potřeba vzít v úvahu při migraci na Blazor . Mnohé z těchto změn platí pro cokoli na základě .NET Core nebo ASP.NET Core.

Vzhledem k tomu Blazor , že je rozhraní .NET Core postaveno, existují i pokyny k zajištění podpory .NET Core. Některé z hlavních změn zahrnují odebrání následujících funkcí:

- Více objektů třídy AppDomains
- Vzdálenou
- Zabezpečení přístupu kódu (CAS)
- Transparentnost zabezpečení

Další informace o technikách, které identifikují nezbytné změny v podpoře používání .NET Core, najdete v tématu [portování kódu z .NET Framework do .NET Core](/dotnet/core/porting).

ASP.NET Core je přepracované verze ASP.NET a obsahuje některé změny, které nemusí zpočátku vypadat zjevně. Hlavní změny:

- Žádný kontext synchronizace, což znamená, že nejsou k dispozici žádné `HttpContext.Current` , `Thread.CurrentPrincipal` nebo jiné statické přistupující objekty
- Bez stínového kopírování
- Žádná fronta žádostí

Mnoho operací v ASP.NET Core je asynchronní, což umožňuje snazší načítat vstupně-výstupní úlohy vázané na vstupně-výstupní operace. Je důležité nikdy neblokovat pomocí `Task.Wait()` nebo `Task.GetResult()` , což může rychle vyčerpat prostředky fondu vláken.

## <a name="migration-conclusion"></a>Závěr migrace

V tomto okamžiku jste viděli spoustu příkladů toho, co je potřeba k přesunutí projektu webových formulářů do Blazor . Úplný příklad naleznete v projektu [eShopOn Blazor ](https://github.com/dotnet-architecture/eShopOnBlazor) .

>[!div class="step-by-step"]
>[Předchozí](security-authentication-authorization.md)
