---
title: Testování aplikací ASP.NET Core MVC
description: Architekt moderní webové aplikace s ASP.NET core a Azure | Testování ASP.NET základních aplikací MVC
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: 2b347442c4a9b7b6cf912ec461248f901dc45417
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147488"
---
# <a name="test-aspnet-core-mvc-apps"></a>Testování aplikací ASP.NET Core MVC

> *"Pokud se vám nelíbí testování částí produktu, s největší pravděpodobností vaši zákazníci nebudou chtít testovat, a to buď."*
 > \_- Anonymní-

Software jakékoliv složitosti může selhat neočekávaným způsobem v reakci na změny. Testování po provedení změn je tedy vyžadováno pro všechny aplikace kromě nejbanálnějších (nebo nejméně kritických). Ruční testování je nejpomalejší, nejméně spolehlivý a nejdražší způsob testování softwaru. Bohužel, pokud aplikace nejsou navrženy tak, aby byly testovatelné, může to být jediný dostupný prostředek. Aplikace napsané tak, aby se řídily architektonickými zásadami stanovenými v [kapitole 4,](architectural-principles.md) by měly být testovatelné částí. ASP.NET základní aplikace podporují automatizovanou integraci a funkční testování.

## <a name="kinds-of-automated-tests"></a>Druhy automatizovaných testů

Existuje mnoho druhů automatizovaných testů softwarových aplikací. Nejjednodušší, nejnižší úroveň testu je test jednotky. Na mírně vyšší úrovni existují integrační testy a funkční testy. Jiné druhy testů, jako jsou například testy ui, zátěžové testy, zátěžové testy a kouřové testy, jsou nad rámec tohoto dokumentu.

### <a name="unit-tests"></a>Testování částí

Testování částí testuje jednu část logiky vaší aplikace. Jeden může dále popsat tím, že uvádí některé z věcí, které to není. Testování částí netestuje, jak váš kód funguje se závislostmi nebo infrastrukturou – to je to, co jsou testy integrace. Testování částí netestuje rozhraní, na které je váš kód napsán – měli byste předpokládat, že funguje, nebo pokud zjistíte, že ne, zadejte chybu a kód řešení. Test jednotky běží zcela v paměti a probíhá. Nekomunikuje se systémem souborů, sítí ani s databází. Testy částí by měly pouze testovat váš kód.

Testování částí, na základě skutečnosti, že testují pouze jednu jednotku vašeho kódu, bez externích závislostí, by měly být provedeny velmi rychle. Proto byste měli být schopni spustit testovací sady stovky testů částí během několika sekund. Spouštějte je často, ideálně před každým nabízením do sdíleného úložiště správy zdrojového kódu, a určitě s každým automatizovaným sestavením na serveru sestavení.

### <a name="integration-tests"></a>Integrační testy

I když je vhodné zapouzdřit kód, který interaguje s infrastrukturou, jako jsou databáze a systémy souborů, budete mít stále některé z tohoto kódu a pravděpodobně budete chtít otestovat. Kromě toho byste měli ověřit, že vrstvy kódu interagují podle očekávání, když jsou plně vyřešeny závislosti vaší aplikace. To je odpovědností integračních testů. Integrační testy mají tendenci být pomalejší a obtížnější než testování částí, protože často závisí na externízávislosti a infrastruktury. Proto byste se měli vyhnout testování věcí, které by mohly být testovány s testy částí v integračních testech. Pokud můžete otestovat daný scénář s testování částí, měli byste jej otestovat s testování částí. Pokud nemůžete, zvažte použití testu integrace.

Integrační testy budou mít často složitější postupy nastavení a stržení než testy částí. Například test integrace, který je v rozporu se skutečnou databází, bude potřebovat způsob, jak vrátit databázi do známého stavu před každým spuštěním testu. Při přidávání nových testů a vývoji schématu produkční databáze budou mít tyto testovací skripty tendenci zvětšovat se co do velikosti a složitosti. V mnoha velkých systémech je nepraktické spouštět úplné sady integračních testů na vývojářských pracovních stanicích před vrácením změn sdílenésprávy zdrojového kódu. V těchto případech mohou být na serveru sestavení spuštěny integrační testy.

### <a name="functional-tests"></a>Funkční testy

Integrační testy jsou zapsány z pohledu vývojáře, aby se ověřilo, že některé součásti systému pracují správně společně. Funkční testy jsou psány z pohledu uživatele a ověřují správnost systému na základě jeho požadavků. Následující výňatek nabízí užitečnou analogii, jak přemýšlet o funkčních testech ve srovnání s testy částí:

> "Mnohokrát je vývoj systému přirovnáván k výstavbě domu. I když tato analogie není zcela správná, můžeme ji rozšířit pro účely pochopení rozdílu mezi jednotkovými a funkčními testy. Testování částí je obdobou stavebního inspektora, který navštíví staveniště domu. Zaměřuje se na různé vnitřní systémy domu, základy, rámování, elektroinstalace, instalatérské a tak dále. Zajišťuje (testy), že části domu budou fungovat správně a bezpečně, to znamená, že splňují stavební předpisy. Funkční testy v tomto scénáři jsou obdobou majitele domu, který navštíví stejné staveniště. Předpokládá, že vnitřní systémy se budou chovat vhodně, že stavební inspektor plní svůj úkol. Majitel domu se zaměřuje na to, jaké to bude žít v tomto domě. On se zabývá tím, jak dům vypadá, jsou různé pokoje pohodlné velikosti, se dům hodí rodiny potřeby, jsou okna v dobrém místě chytit ranní slunce. Majitel domu provádí funkční testy na domě. Má pohled uživatele. Stavební inspektor provádí jednotkové testy domu. Má pohled na stavitele."

Zdroj: [Testování částí versus funkční testy](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)

Jsem rád říká: "Jako vývojáři, se nám nepodaří dvěma způsoby: stavíme věc špatně, nebo jsme stavět špatnou věc." Jednotkové testy zajistí, že vytváříte věc správně; funkční testy zajistí, že budujete správnou věc.

Vzhledem k tomu, že funkční testy pracují na úrovni systému, mohou vyžadovat určitý stupeň automatizace uživatelského rozhraní. Stejně jako integrační testy, obvykle pracují s nějakou testovací infrastrukturou. Díky tomu jsou pomalejší a křehčí než testy jednotek a integrace. Měli byste mít pouze tolik funkčních testů, kolik potřebujete, abyste si byli jisti, že se systém chová tak, jak uživatelé očekávají.

### <a name="testing-pyramid"></a>Testovací pyramida

Martin Fowler psal o testovací pyramidě, jejíž příklad je znázorněn na obrázku 9-1.

![Testovací pyramida](./media/image9-1.png)

**Obrázek 9-1**. Testovací pyramida

Různé vrstvy pyramidy a jejich relativní velikosti představují různé druhy testů a kolik byste měli napsat pro vaši aplikaci. Jak můžete vidět, doporučení je mít velkou základnu testů částí, podporované menší vrstvou integračních testů, s ještě menší vrstvou funkčních testů. Každá vrstva by v ideálním případě měla mít pouze testy, které nelze provést adekvátně v nižší vrstvě. Mějte na paměti testovací pyramidu, když se snažíte rozhodnout, jaký druh testu potřebujete pro konkrétní scénář.

### <a name="what-to-test"></a>Co testovat

Běžným problémem pro vývojáře, kteří mají zkušenosti s psaním automatizovaných testů, je přijít s tím, co testovat. Dobrým výchozím bodem je testování podmíněné logiky. Kdekoli máte metodu s chováním, které se mění na základě podmíněného příkazu (if-else, switch a tak dále), měli byste být schopni přijít s alespoň několika testy, které potvrzují správné chování za určitých podmínek. Pokud váš kód obsahuje chybové stavy, je vhodné napsat alespoň jeden test pro "happy path" prostřednictvím kódu (bez chyb) a alespoň jeden test pro "smutnou cestu" (s chybami nebo atypickými výsledky) k potvrzení, že se aplikace chová podle očekávání tváří v tvář chybám. Nakonec se pokuste zaměřit na testování věcí, které mohou selhat, spíše než se zaměřit na metriky, jako je pokrytí kódu. Více pokrytí kódu je lepší než méně, obecně. Psaní několika dalších testů složité a důležité metody pro podnikání je však obvykle lepší využití času než psaní testů pro automatické vlastnosti, jen aby se zlepšily metriky pokrytí testovacího kódu.

## <a name="organizing-test-projects"></a>Uspořádání testovacích projektů

Testovací projekty mohou být organizovány, ale funguje nejlépe pro vás. Je vhodné oddělit testy podle typu (testování částí, test integrace) a podle toho, co testují (podle projektu, podle oboru názvů). Zda toto oddělení se skládá ze složek v rámci jednoho testovacího projektu nebo více testovacích projektů, je rozhodnutí o návrhu. Jeden projekt je nejjednodušší, ale pro velké projekty s mnoha testy nebo za účelem snadněji spustit různé sady testů, můžete chtít mít několik různých testovacích projektů. Mnoho týmů organizuje testovací projekty na základě projektu, který testují, což pro aplikace s více než několika projekty může mít za následek velký počet testovacích projektů, zejména pokud je stále rozkládáte podle toho, jaký druh testů je v každém projektu. Kompromisní přístup je mít jeden projekt na druh testu, na aplikaci, se složkami uvnitř testovacích projektů k označení projektu (a třídy) testovány.

Běžným přístupem je uspořádání projektů aplikace ve složce "src" a testovacích projektů aplikace pod paralelní složky "testy". Pokud se vám tato organizace bude hodit, můžete v sadě Visual Studio vytvořit složky odpovídajících řešení.

![Testovací organizace ve vašem řešení](./media/image9-2.png)

**Obrázek 9-2**. Testovací organizace ve vašem řešení

Můžete použít podle toho, co test rozhraní, které dáváte přednost. XUnit framework funguje dobře a je to, co všechny ASP.NET core a EF core testy jsou zapsány v. Testovací projekt xUnit můžete přidat v sadě Visual Studio pomocí šablony znázorněné na `dotnet new xunit`obrázku 9-3 nebo z cli pomocí .

![Přidání testovacího projektu xUnit v sadě Visual Studio](./media/image9-3.png)

**Obrázek 9-3**. Přidání testovacího projektu xUnit v sadě Visual Studio

### <a name="test-naming"></a>Testovat pojmenování

Pojmenujte testy konzistentním způsobem s názvy, které označují, co každý test dělá. Jeden přístup jsem měl velký úspěch s je název testovacítřídy podle třídy a metody, které jsou testování. To má za následek mnoho malých testovacích tříd, ale je velmi jasné, co každý test je zodpovědný za. S názvem testovací třídy nastavena k identifikaci třídy a metody, které mají být testovány, název zkušební metody lze použít k určení chování, které jsou testovány. To by mělo zahrnovat očekávané chování a všechny vstupy nebo předpoklady, které by měly výnos toto chování. Některé příklady testovacích názvů:

- `CatalogControllerGetImage.CallsImageServiceWithId`

- `CatalogControllerGetImage.LogsWarningGivenImageMissingException`

- `CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess`

- `CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException`

Změna tohoto přístupu ukončí každý název zkušební třídy s "Should" a mírně upraví čas:

- `CatalogControllerGetImage`**By měl**`.`**volat**`ImageServiceWithId`

- `CatalogControllerGetImage`**By se**`.`**přihlásit**`WarningGivenImageMissingException`

Některé týmy považují druhý přístup pojmenování za jasnější, i když o něco podrobnější. V každém případě zkuste použít konvenci pojmenování, která poskytuje přehled o chování testu, takže když jeden nebo více testů nezdaří, je zřejmé z jejich názvů, jaké případy selhaly. Vyhněte se pojmenování testů vágně, jako je například ControllerTests.Test1, protože tyto nabízejí žádnou hodnotu, když je vidíte ve výsledcích testu.

Pokud se řídíte konvence pojmenování, jako je výše, která vytváří mnoho malých testovacích tříd, je vhodné dále organizovat testy pomocí složek a oborů názvů. Obrázek 9-4 ukazuje jeden přístup k uspořádání testů podle složky v rámci několika testovacích projektů.

![Uspořádání testovacích tříd podle složky na základě testované třídy](./media/image9-4.png)

**Obrázek 9-4.** Uspořádání testovacích tříd podle složky na základě testované třídy.

Pokud má určitá třída aplikace mnoho testovaných metod (a tedy mnoho testovacích tříd), může mít smysl je umístit do složky odpovídající třídě aplikace. Tato organizace se nijak neliší od uspořádání souborů do složek jinde. Pokud máte ve složce více než tři nebo čtyři související soubory obsahující mnoho dalších souborů, je často užitečné je přesunout do vlastní podsložky.

## <a name="unit-testing-aspnet-core-apps"></a>Testování částí ASP.NET základní aplikace

V dobře navržené aplikaci ASP.NET Core bude většina složitosti a obchodní logiky zapouzdřena v obchodních entitách a různých službách. Samotná aplikace ASP.NET Core MVC se svými řadiči, filtry, zobrazeními a zobrazeními by měla vyžadovat velmi málo testů částí. Velká část funkce dané akce leží mimo samotnou metodu akce. Testování, zda směrování funguje správně, nebo globální zpracování chyb, nelze provést efektivně s testování částí. Stejně tak žádné filtry, včetně ověřování modelu a ověřování a autorizace filtry, nelze testovat jednotku s testem cílení na metodu akce řadiče. Bez těchto zdrojů chování by většina metod akce měla být triviálně malá a delegovat většinu své práce na služby, které lze testovat nezávisle na řadiči, který je používá.

Někdy budete muset refaktorovat kód, aby bylo možné jej otestovat. Často to zahrnuje identifikaci abstrakce a použití vkládání závislostí pro přístup k abstrakci v kódu, který chcete testovat, spíše než kódování přímo proti infrastruktuře. Zvažte například tuto jednoduchou metodu akce pro zobrazení obrázků:

```csharp
[HttpGet("[controller]/pic/{id}")]
public IActionResult GetImage(int id)
{
    var contentRoot = _env.ContentRootPath + "//Pics";
    var path = Path.Combine(contentRoot, id + ".png");
    Byte[] b = System.IO.File.ReadAllBytes(path);
    return File(b, "image/png");
}
```

Testování částí této metody je obtížné jeho `System.IO.File`přímou závislostí na , kterou používá ke čtení ze systému souborů. Toto chování můžete otestovat, abyste zajistili, že funguje podle očekávání, ale pokud tak učiníte se skutečnými soubory, je test integrace. Stojí za zmínku, že nemůžete jednotkový test této metody trasy - uvidíte, jak to udělat s funkčnítest krátce.

Pokud nemůžete otestovat chování systému souborů přímo a nemůžete otestovat trasu, co je k testování? No, po refaktoringu, aby bylo možné testování částí, můžete zjistit některé testovací případy a chybějící chování, jako je například zpracování chyb. K čemu tato metoda dochází, když soubor není nalezen? Co by to mělo dělat? V tomto příkladu refaktorovaná metoda vypadá takto:

```csharp
[HttpGet("[controller]/pic/{id}")]
public IActionResult GetImage(int id)
{
    byte[] imageBytes;
    try
    {
        imageBytes = _imageService.GetImageBytesById(id);
    }
    catch (CatalogImageMissingException ex)
    {
        _logger.LogWarning($"No image found for id: {id}");
        return NotFound();
    }
    return File(imageBytes, "image/png");
}
```

`_logger`a `_imageService` jsou oba injekčně jako závislosti. Nyní můžete otestovat, že stejné ID, které je `_imageService`předáno metodě akce, je předáno a že výsledné bajty jsou vráceny jako součást FileResult. Můžete také otestovat, že protokolování chyb `NotFound` se děje podle očekávání a že výsledek je vrácena, pokud chybí obrázek, za předpokladu, že je důležité chování aplikace (to znamená, že nejen dočasný kód vývojář přidal k diagnostice problému). Skutečná logika souboru byla přesunuta do samostatné implementační služby a byla rozšířena tak, aby vrátila výjimku specifickou pro aplikaci pro případ chybějícího souboru. Tuto implementaci můžete otestovat nezávisle pomocí integračního testu.

Ve většině případů budete chtít použít globální obslužné rutiny výjimek ve vašich řadičích, takže množství logiky v nich by mělo být minimální a pravděpodobně nestojí za testování částí. Většinu testování akcí řadiče byste měli provést `TestServer` pomocí funkčních testů a třídy popsané níže.

## <a name="integration-testing-aspnet-core-apps"></a>Testování integrace ASP.NET základní aplikace

Většina testů integrace ve vašich ASP.NET základních aplikacích by měla být testování služeb a dalších typů implementací definovaných v projektu Infrastruktura. Můžete například [otestovat, že EF Core úspěšně aktualizoval a načítal data, která očekáváte](https://docs.microsoft.com/ef/core/miscellaneous/testing/) od tříd přístupu k datům v projektu Infrastruktura. Nejlepší způsob, jak otestovat, že váš ASP.NET core MVC projekt se chová správně, je s funkční testy, které běží proti vaší aplikaci spuštěné v testovacím hostiteli.

## <a name="functional-testing-aspnet-core-apps"></a>Funkční testování ASP.NET základní aplikace

Pro ASP.NET základní `TestServer` aplikace, třída umožňuje funkční testy poměrně snadno psát. `TestServer` Nakonfigurujete `WebHostBuilder` pomocí (nebo `HostBuilder`) přímo (jako obvykle `WebApplicationFactory` pro vaši aplikaci) nebo s typem (k dispozici od verze 2.1). Měli byste se pokusit co nejvíce spárovat testovacího hostitele s hostitelem produkčního prostředí, takže vaše testy budou postupovat podobně jako aplikace v produkčním prostředí. Třída `WebApplicationFactory` je užitečná pro konfiguraci Kořenové kořenové stránky Obsahu serveru TestServer, který používá ASP.NET Core k vyhledání statického prostředku, jako je zobrazení.

Jednoduché funkční testy můžete vytvořit vytvořením testovací třídy, která implementuje IClassFixture\<WebApplicationFactory\<TEntry>> kde TEntry je třída startupvaší webové aplikace. S tímto na místě, testovací svítidlo můžete vytvořit klienta pomocí metody CreateClient výroby:

```cs
public class BasicWebTests : IClassFixture<WebApplicationFactory<Startup>>
{
    protected readonly HttpClient _client;

    public BaseWebTest(WebApplicationFactory<Startup> factory)
    {
        _client = factory.CreateClient();
    }

    // write tests that use _client
}
```

Často budete chtít provést některé další konfigurace webu před každým spuštěním testu, jako je například konfigurace aplikace pro použití úložiště dat v paměti a potom osetí aplikace s testovacími daty. Chcete-li to provést, měli byste vytvořit\<vlastní podtřídu WebApplicationFactory TEntry> a přepsat jeho ConfigureWebHost metoda. Níže uvedený příklad je z projektu eShopOnWeb FunctionalTests a používá se jako součást testů na hlavní webové aplikaci.

```cs
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Identity;
using Microsoft.AspNetCore.Mvc.Testing;
using Microsoft.EntityFrameworkCore;
using Microsoft.eShopWeb.Infrastructure.Data;
using Microsoft.eShopWeb.Infrastructure.Identity;
using Microsoft.eShopWeb.Web;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Logging;
using System;

namespace Microsoft.eShopWeb.FunctionalTests.Web
{
    public class WebTestFixture : WebApplicationFactory<Startup>
    {
        protected override void ConfigureWebHost(IWebHostBuilder builder)
        {
            builder.UseEnvironment("Testing");

            builder.ConfigureServices(services =>
            {
                 services.AddEntityFrameworkInMemoryDatabase();

                // Create a new service provider.
                var provider = services
                    .AddEntityFrameworkInMemoryDatabase()
                    .BuildServiceProvider();

                // Add a database context (ApplicationDbContext) using an in-memory
                // database for testing.
                services.AddDbContext<CatalogContext>(options =>
                {
                    options.UseInMemoryDatabase("InMemoryDbForTesting");
                    options.UseInternalServiceProvider(provider);
                });

                services.AddDbContext<AppIdentityDbContext>(options =>
                {
                    options.UseInMemoryDatabase("Identity");
                    options.UseInternalServiceProvider(provider);
                });

                // Build the service provider.
                var sp = services.BuildServiceProvider();

                // Create a scope to obtain a reference to the database
                // context (ApplicationDbContext).
                using (var scope = sp.CreateScope())
                {
                    var scopedServices = scope.ServiceProvider;
                    var db = scopedServices.GetRequiredService<CatalogContext>();
                    var loggerFactory = scopedServices.GetRequiredService<ILoggerFactory>();

                    var logger = scopedServices
                        .GetRequiredService<ILogger<WebTestFixture>>();

                    // Ensure the database is created.
                    db.Database.EnsureCreated();

                    try
                    {
                        // Seed the database with test data.
                        CatalogContextSeed.SeedAsync(db, loggerFactory).Wait();

                        // seed sample user data
                        var userManager = scopedServices.GetRequiredService<UserManager<ApplicationUser>>();
                        var roleManager = scopedServices.GetRequiredService<RoleManager<IdentityRole>>();
                        AppIdentityDbContextSeed.SeedAsync(userManager, roleManager).Wait();
                    }
                    catch (Exception ex)
                    {
                        logger.LogError(ex, $"An error occurred seeding the " +
                            "database with test messages. Error: {ex.Message}");
                    }
                }
            });
        }
    }
}
```

Testy můžete využít této vlastní WebApplicationFactory pomocí k vytvoření klienta a potom vytváření požadavků na aplikaci pomocí této instance klienta. Aplikace bude mít data osévání, které lze použít jako součást kontrolní výrazy testu. Následující test ověří, zda se domovská stránka aplikace eShopOnWeb načte správně a obsahuje výpis produktu, který byl do aplikace přidán jako součást údajů o osivu.

```cs
using Microsoft.eShopWeb.FunctionalTests.Web;
using System.Net.Http;
using System.Threading.Tasks;
using Xunit;

namespace Microsoft.eShopWeb.FunctionalTests.WebRazorPages
{
    [Collection("Sequential")]
    public class HomePageOnGet : IClassFixture<WebTestFixture>
    {
        public HomePageOnGet(WebTestFixture factory)
        {
            Client = factory.CreateClient();
        }

        public HttpClient Client { get; }

        [Fact]
        public async Task ReturnsHomePageWithProductListing()
        {
            // Arrange & Act
            var response = await Client.GetAsync("/");
            response.EnsureSuccessStatusCode();
            var stringResponse = await response.Content.ReadAsStringAsync();

            // Assert
            Assert.Contains(".NET Bot Black Sweatshirt", stringResponse);
        }
    }
}
```

Tento funkční test vykonává plnou ASP.NET Core MVC / Razor Pages aplikační zásobník, včetně všech middleware, filtry, pojiva, atd., které mohou být na místě. Ověří, že daná trasa ("/" vrátí kód stavu očekávaného úspěchu a výstup HTML. Činí tak bez nastavení skutečného webového serveru, a tak se vyhýbá velké části křehkosti, kterou může zažít použití skutečného webového serveru pro testování (například problémy s nastavením brány firewall). Funkční testy, které běží proti TestServer jsou obvykle pomalejší než integrace a testování částí, ale jsou mnohem rychlejší než testy, které by běžely přes síť na testovací webový server. Měli byste použít funkční testy k zajištění front-end zásobníku aplikace funguje podle očekávání. Tyto testy jsou užitečné zejména při zjištění duplicity v řadičích nebo stránkách a řešíte duplikaci přidáním filtrů. V ideálním případě toto refaktoring nezmění chování aplikace a sada funkčních testů ověří tento případ.

> ### <a name="references--test-aspnet-core-mvc-apps"></a>Reference – Testování ASP.NET aplikace Core MVC
>
> - **Testování v ASP.NET jádru** \
>   <https://docs.microsoft.com/aspnet/core/testing/>
> - **Konvence pojmenování testu částí** \
>   <https://ardalis.com/unit-test-naming-convention>
> - **Testování EF core** \
>   <https://docs.microsoft.com/ef/core/miscellaneous/testing/>
> - **Integrační testy v ASP.NET Core** \
>   <https://docs.microsoft.com/aspnet/core/test/integration-tests>

>[!div class="step-by-step"]
>[Předchozí](work-with-data-in-asp-net-core-apps.md)
>[další](development-process-for-azure.md)
