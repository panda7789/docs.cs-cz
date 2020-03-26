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
# <a name="migrate-from-aspnet-web-forms-to-blazor"></a>Migrace z webových formulářů ASP.NET do Blazoru

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Migrace základu kódu z ASP.NET webových formulářů do Blazoru je časově náročná úloha, která vyžaduje plánování. Tato kapitola popisuje proces. Něco, co může usnadnit přechod je zajistit, že aplikace dodržuje architekturu *N-vrstvé,* kde model aplikace (v tomto případě webové formuláře) je oddělen od obchodní logiky. Toto logické oddělení vrstev jasně ukazuje, co je potřeba přesunout do .NET Core a Blazor.

V tomto příkladu se používá aplikace eShop dostupná na [GitHubu.](https://github.com/dotnet-architecture/eShopOnBlazor) eShop je katalogová služba, která poskytuje možnosti CRUD prostřednictvím zadávání formulářů a validace.

Proč by měla být pracovní aplikace migrována do Blazoru? Mnohokrát, není třeba. ASP.NET webových formulářů bude podporována po mnoho let. Mnoho funkcí, které Blazor poskytuje, je však podporováno pouze v migrované aplikaci. Mezi tyto funkce patří:

- Zlepšení výkonnosti v rámci, jako je`Span<T>`
- Možnost spuštění jako webová sestava
- Podpora napříč platformami pro Linux a macOS
- Nasazení v místním prostředí aplikace nebo nasazení sdíleného frameworku bez dopadu na jiné aplikace

Pokud jsou tyto nebo jiné nové funkce dostatečně přesvědčivé, může být migrace aplikace hodnotou. Migrace může mít různé tvary; může to být celá aplikace nebo pouze určité koncové body, které vyžadují změny. Rozhodnutí o migraci je v konečném důsledku založeno na obchodních problémech, které má vývojář vyřešit.

## <a name="server-side-versus-client-side-hosting"></a>Hosting na straně serveru versus na straně klienta

Jak je popsáno v kapitole [hostování modelů,](hosting-models.md) aplikace Blazor může být hostována dvěma různými způsoby: na straně serveru a na straně klienta. Model na straně serveru používá připojení ASP.NET Core SignalR ke správě aktualizací modelu DOM při spuštění libovolného skutečného kódu na serveru. Model na straně klienta běží jako WebAssembly v prohlížeči a nevyžaduje žádná připojení k serveru. Existuje řada rozdílů, které mohou ovlivnit, což je nejlepší pro konkrétní aplikaci:

- Spuštění jako WebAssembly je stále ve vývoji a nemusí podporovat všechny funkce (například zřetězení) v aktuálním čase
- Upovídaná komunikace mezi klientem a serverem může způsobit problémy s latencí v režimu na straně serveru
- Přístup k databázím a interním nebo chráněným službám vyžaduje samostatnou službu s hostováním na straně klienta

V době psaní modelu na straně serveru více podobá webové formuláře. Většina této kapitoly se zaměřuje na model hostování na straně serveru, protože je připraven na produkční prostředí.

## <a name="create-a-new-project"></a>Vytvoření nového projektu

Tento počáteční krok migrace je vytvořit nový projekt. Tento typ projektu je založen na projektech stylu Sady SDK .NET Core a zjednodušuje velkou část často používaný text, který byl použit v předchozích formátech projektu. Podrobnější informace naleznete v kapitole [O struktuře projektu](project-structure.md).

Po vytvoření projektu nainstalujte knihovny, které byly použity v předchozím projektu. Ve starších projektech webových formulářů jste pravděpodobně použili soubor *packages.config* k zobrazení seznamu požadovaných balíčků NuGet. V novém projektu ve stylu sady SDK byl soubor `<PackageReference>` *packages.config* nahrazen prvky v souboru projektu. Výhodou tohoto přístupu je, že všechny závislosti jsou nainstalovány přechodně. Uvádíte pouze závislosti nejvyšší úrovně, na kterých vám záleží.

Mnoho závislostí, které používáte, je k dispozici pro rozhraní .NET Core, včetně entity Framework 6 a log4net. Pokud není k dispozici žádná verze .NET Core nebo .NET Standard, lze často použít verzi rozhraní .NET Framework. Počet ujetých kilometrů se může lišit. Jakékoli rozhraní API, které není k dispozici v rozhraní .NET Core, způsobí chybu za běhu. Visual Studio vás upozorní na tyto balíčky. V uzlu **Reference** v projektu se v **Průzkumníku řešení**zobrazí žlutá ikona.

V projektu eShopu založeném na Blazoru můžete vidět nainstalované balíčky. Dříve soubor *packages.config* vyjmenoval všechny balíčky použité v projektu, což vedlo k tomu, že soubor byl dlouhý téměř 50 řádků. Výstřižek *packages.config* je:

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

Prvek `<packages>` obsahuje všechny nezbytné závislosti. Je obtížné určit, které z těchto balíčků jsou zahrnuty, protože je požadujete. Některé `<package>` prvky jsou uvedeny jednoduše pro uspokojení potřeb závislostí, které potřebujete.

Projekt Blazor uvádí závislosti, které `<ItemGroup>` požadujete v rámci prvku v souboru projektu:

```xml
<ItemGroup>
    <PackageReference Include="Autofac" Version="4.9.3" />
    <PackageReference Include="EntityFramework" Version="6.3.0-preview9-19423-04" />
    <PackageReference Include="log4net" Version="2.0.8" />
</ItemGroup>
```

Jeden balíček NuGet, který zjednodušuje životnost vývojářů webových formulářů, je [sada Windows Compatibility Pack](../../core/porting/windows-compat-pack.md). Ačkoli .NET Core je multiplatformní, některé funkce jsou k dispozici pouze v systému Windows. Funkce specifické pro systém Windows jsou k dispozici instalací sady Compatibility Pack. Příklady těchto funkcí zahrnují registr, službu WMI a adresářové služby. Balíček přidá přibližně 20 000 api a aktivuje mnoho služeb, se kterými už možná znáte. Projekt eShopu nevyžaduje balíček kompatibility; ale pokud vaše projekty používají funkce specifické pro systém Windows, balíček usnadňuje úsilí o migraci.

## <a name="enable-startup-process"></a>Povolit proces spuštění

Proces spuštění pro Blazor se změnil z webových formulářů a následuje podobné nastavení pro jiné služby ASP.NET Core. Když hostované straně serveru, Blazor komponenty jsou spuštěny jako součást normální ASP.NET aplikace Core. Při hostování v prohlížeči s WebAssembly, Komponenty Blazor používají podobný model hostování. Rozdíl je, že součásti jsou spuštěny jako samostatná služba od některého z back-endových procesů. Ať tak či onak, spuštění je podobné.

Soubor *Global.asax.cs* je výchozí spouštěcí stránka pro projekty webových formulářů. V projektu eShopu tento soubor konfiguruje kontejner Inversion of Control (IoC) a zpracovává různé události životního cyklu aplikace nebo požadavku. Některé z těchto událostí jsou zpracovány `Application_BeginRequest`pomocí middleware (například ). Jiné události vyžadují přepsání konkrétních služeb prostřednictvím vkládání závislostí (DI).

Například *Global.asax.cs* soubor pro eShop obsahuje následující kód:

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

Předchozí soubor se `Startup` stane třídou v Blazoru na straně serveru:

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

Jednou z významných změn, které si můžete všimnout z webových formulářů, je význam DI. DI je hlavní zásadou v návrhu ASP.NET Core. Podporuje přizpůsobení téměř všech aspektů ASP.NET core frameworku. Existuje dokonce i vestavěný poskytovatel služeb, který lze použít pro mnoho scénářů. Pokud je vyžadováno více přizpůsobení, může být podporováno mnoha komunitními projekty. Můžete například převést investice do knihovny DI třetích stran.

V původní aplikaci eShop je určitá konfigurace pro správu relací. Vzhledem k tomu, že Blazor na straně serveru používá ASP.NET Core SignalR pro komunikaci, stav relace není podporován, protože připojení může dojít nezávisle na kontextu HTTP. Aplikace, která používá stav relace, vyžaduje před spuštěním jako aplikace Blazor rearchitecting.

Další informace o spuštění aplikace naleznete v [tématu App startup](app-startup.md).

## <a name="migrate-http-modules-and-handlers-to-middleware"></a>Migrace modulů HTTP a obslužných rutin do middlewaru

Moduly HTTP a obslužné rutiny jsou běžné vzory ve webových formulářích pro řízení kanálu požadavků HTTP. Třídy, `IHttpModule` `IHttpHandler` které implementují nebo by mohly být registrovány a zpracovávat příchozí požadavky. Webové formuláře konfigurují moduly a obslužné rutiny v souboru *web.config.* Webové formuláře jsou také silně založeny na zpracování událostí životního cyklu aplikace. ASP.NET Core místo toho používá middleware. Middleware je registrován `Configure` v `Startup` metodě třídy. Pořadí provádění middlewaru je určeno registračním příkazem.

V části [Povolit proces spuštění](#enable-startup-process) byla jako metoda vyvolána událost životního cyklu webovými formuláři. `Application_BeginRequest` Tato událost není k dispozici v ASP.NET Core. Jedním ze způsobů, jak dosáhnout tohoto chování je implementovat middleware, jak je vidět v příkladu souboru *Startup.cs.* Tento middleware provádí stejnou logiku a poté přenese řízení na další obslužnou rutinu v kanálu middlewaru.

Další informace o migraci modulů a obslužných rutin naleznete [v tématu Migrace obslužných rutin protokolu HTTP a modulů do ASP.NET middlewaru core](/aspnet/core/migration/http-modules).

## <a name="migrate-static-files"></a>Migrace statických souborů

Chcete-li zobrazovat statické soubory (například HTML, CSS, obrázky a JavaScript), musí být soubory vystaveny middlewarem. Volání `UseStaticFiles` metody umožňuje obsluhu statických souborů z kořenové cesty webu. Výchozí kořenový adresář webu je *wwwroot*, ale lze jej přizpůsobit. Jak je `Configure` zahrnuto v metodě `Startup` třídy eShopu:

```csharp
public void Configure(IApplicationBuilder app)
{
    ...

    app.UseStaticFiles();

    ...
}
```

Projekt eShopu umožňuje základní přístup ke statickým souborům. Pro statický přístup k souborům je k dispozici mnoho vlastních nastavení. Informace o povolení výchozích souborů nebo prohlížeče souborů naleznete [v tématu Statické soubory v ASP.NET jádra](/aspnet/core/fundamentals/static-files).

## <a name="migrate-runtime-bundling-and-minification-setup"></a>Migrace nastavení sdružování za běhu a minifikace

Sdružování a minifikace jsou techniky optimalizace výkonu pro snížení počtu a velikosti požadavků serveru k načtení určitých typů souborů. JavaScript a CSS často podstupují nějakou formu sdružování nebo minifikace před odesláním klientovi. Ve ASP.NET webových formulářů jsou tyto optimalizace zpracovány za běhu. Konvence optimalizace jsou definovány jako soubor *App_Start/BundleConfig.cs.* V ASP.NET Core je přijat více deklarativní přístup. Soubor obsahuje seznam souborů, které mají být minififikovány, spolu s konkrétní nastavení minifikace.

Další informace o sdružování a minifikaci viz [Sada a minify statických aktiv v ASP.NET Core](/aspnet/core/client-side/bundling-and-minification).

## <a name="migrate-aspx-pages"></a>Migrace stránek ASPX

Stránka v aplikaci Webové formuláře je soubor s příponou *ASPX.* Stránku webových formulářů lze často mapovat na komponentu v Blazoru. Komponenta Blazor je napsána v souboru s *příponou .razor.* Pro projekt eShopu je pět stránek převedeno na stránku Razor.

Zobrazení podrobností se například skládá ze tří souborů v projektu webových formulářů: *Details.aspx*, *Details.aspx.cs*a *Details.aspx.designer.cs*. Při převodu na Blazor, kód-za a značky jsou kombinovány do *Details.razor*. Kompilace Razor (ekvivalentní tomu, co je v *souborech .designer.cs)* je uložena v adresáři *obj* a ve výchozím nastavení není k dispozici v **Průzkumníku řešení**. Stránka Webové formuláře se skládá z následujících značek:

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

Kód předchozí značky obsahuje následující kód:

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

Při převodu na Blazor se stránka Webových formulářů překládá na následující kód:

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

Všimněte si, že kód a značky jsou ve stejném souboru. Všechny požadované služby jsou `@inject` přístupné pomocí atributu. Podle `@page` směrnice je tato stránka přístupná `Catalog/Details/{id}` na trase. Hodnota `{id}` zástupného symbolu trasy byla omezena na celé číslo. Jak je popsáno v části [směrování,](pages-routing-layouts.md) na rozdíl od webových formulářů komponenta Razor výslovně uvádí jeho trasu a všechny parametry, které jsou zahrnuty. Mnoho ovládacích prvků webových formulářů nemusí mít přesné protějšky v Blazoru. Často existuje ekvivalentní fragment HTML, který bude sloužit stejnému účelu. `<asp:Label />` Ovládací prvek lze například nahradit elementem HTML. `<label>`

### <a name="model-validation-in-blazor"></a>Ověření modelu v Blazoru

Pokud kód webových formulářů zahrnuje ověření, můžete přenést velkou část toho, co máte, s malými změnami. Výhodou pro spuštění v Blazoru je, že stejnou ověřovací logiku lze spustit bez nutnosti vlastního JavaScriptu. Datové poznámky umožňují snadné ověření modelu.

Například stránka *Create.aspx* obsahuje formulář pro zadávání dat s ověřením. Ukázkový úryvek bude vypadat takto:

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

V Blazor, ekvivalentní značky je k dispozici v souboru *Create.razor:*

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

Kontext `EditForm` zahrnuje podporu ověření a lze je omotat kolem vstupu. Poznámky k datům jsou běžným způsobem přidání ověření. Tato podpora ověření lze `DataAnnotationsValidator` přidat prostřednictvím komponenty. Další informace o tomto mechanismu naleznete [v ASP.NET formuláře Core Blazor a ověření](/aspnet/core/blazor/forms-validation).

## <a name="migrate-built-in-web-forms-controls"></a>Migrace integrovaných ovládacích prvků webových formulářů

*Tento obsah je již brzy.*

## <a name="migrate-configuration"></a>Migrace konfigurace

V projektu webových formulářů jsou konfigurační data nejčastěji uložena v souboru *web.config.* K konfiguračním `ConfigurationManager`datům se přistupuje pomocí aplikace . Služby byly často nutné k analýzě objektů. S rozhraním .NET Framework 4.7.2 byla do `ConfigurationBuilders`konfigurace přidána shodnost prostřednictvím rozhraní . Tyto tvůrce povoleno vývojáři přidat různé zdroje pro konfiguraci, která byla pak skládá za běhu načíst potřebné hodnoty.

ASP.NET Core zavedla flexibilní konfigurační systém, který umožňuje definovat zdroj konfigurace nebo zdroje používané vaší aplikací a nasazením. Infrastruktura, `ConfigurationBuilder` kterou můžete používat v aplikaci Webové formuláře, byla modelována podle konceptů používaných v konfiguračním systému ASP.NET Core.

Následující úryvek ukazuje, jak projekt eShopu Web Forms používá *web.config* k ukládání hodnot konfigurace:

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

Je běžné, že tajné klíče, jako jsou připojovací řetězce databáze, mají být uloženy v souboru *web.config*. Tajné klíče jsou nevyhnutelně trvalé v nezabezpečených místech, jako je například řízení zdrojového kódu. S Blazor na ASP.NET Core, předchozí konfigurace založené na XML je nahrazen a následující JSON:

```json
{
  "ConnectionStrings": {
    "CatalogDBContext": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;"
  },
  "UseMockData": true,
  "UseCustomizationData": false
}
```

JSON je výchozí konfigurační formát. ASP.NET však Core podporuje mnoho dalších formátů, včetně XML. Existuje také několik formátů podporovaných komunitou.

Konstruktor ve `Startup` třídě projektu Blazor přijímá `IConfiguration` instanci prostřednictvím techniky DI známé jako vstřikování konstruktoru:

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

Ve výchozím nastavení proměnné prostředí, soubory JSON (*appsettings.json* a *appsettings.{ Environment}.json*) a možnosti příkazového řádku jsou registrovány jako platné zdroje konfigurace v objektu konfigurace. Ke zdrojům konfigurace lze `Configuration[key]`přistupovat prostřednictvím aplikace . Pokročilejší technika je svázat konfigurační data s objekty pomocí vzoru voleb. Další informace o konfiguraci a vzoru voleb naleznete [v tématu Konfigurace v ASP.NET jádra](/aspnet/core/fundamentals/configuration/) a [vzory Možnosti v ASP.NET jádrem](/aspnet/core/fundamentals/configuration/options).

## <a name="migrate-data-access"></a>Migrace přístupu k datům

Přístup k datům je důležitým aspektem každé aplikace. Projekt eShopu ukládá informace o katalogu do databáze a načítá data pomocí entity Framework (EF) 6. Vzhledem k tomu, že EF 6 je podporován v rozhraní .NET Core 3.0, projekt může nadále používat.

Pro eShop byly nutné následující změny týkající se EF:

- V rozhraní .NET `DbContext` Framework objekt přijme řetězec *názvu formuláře=ConnectionString* a `ConfigurationManager.AppSettings[ConnectionString]` použije připojovací řetězec z pro připojení. V rozhraní .NET Core to není podporováno. Připojovací řetězec musí být zadán.
- K databázi bylo přistupováno synchronně. I když to funguje, škálovatelnost může trpět. Tato logika by měla být přesunuta do asynchronní vzor.

I když neexistuje stejná nativní podpora pro vazbu datové sady, Blazor poskytuje flexibilitu a napájení s podporou Jazyka C# na stránce Razor. Můžete například provádět výpočty a zobrazit výsledek. Další informace o vzorcích dat v Blazoru najdete v kapitole [Přístup k datům.](data.md)

## <a name="architectural-changes"></a>Architektonické změny

A konečně, tam jsou některé důležité architektonické rozdíly, aby zvážila při migraci do Blazor. Mnohé z těchto změn se vztahují na cokoli na základě .NET Core nebo ASP.NET Core.

Protože Blazor je postaven na .NET Core, existují důležité informace o zajištění podpory na .NET Core. Některé z hlavních změn patří odstranění následujících funkcí:

- Více domén aplikací
- Remoting
- Zabezpečení přístupu kódu (CAS)
- Transparentnost zabezpečení

Další informace o technikách k identifikaci nezbytných změn pro podporu spuštěného v jádru .NET naleznete [v tématu Port kódu z rozhraní .NET Framework do .NET Core](/dotnet/core/porting).

ASP.NET Core je přepracovaná verze ASP.NET a má některé změny, které se nemusí zpočátku zdát zřejmé. Hlavní změny jsou:

- Žádný kontext synchronizace, což znamená, že neexistuje žádný `HttpContext.Current`, `Thread.CurrentPrincipal`, nebo jiné statické přístupové moduly
- Žádné stínové kopírování
- Žádná fronta požadavků

Mnoho operací v ASP.NET Core jsou asynchronní, což umožňuje snadnější off-loading úlohy vázané na vstupně-výstupní operace. Je důležité nikdy blokovat pomocí `Task.Wait()` `Task.GetResult()`nebo , které mohou rychle vyčerpat prostředky fondu vláken.

## <a name="migration-conclusion"></a>Závěr o migraci

V tomto okamžiku jste viděli mnoho příkladů toho, co je zapotřebí k přesunutí projektu webových formulářů do Blazoru. Úplný příklad najdete v projektu [eShopOnBlazor.](https://github.com/dotnet-architecture/eShopOnBlazor)

>[!div class="step-by-step"]
>[Předchozí](security-authentication-authorization.md)
