---
title: ASP.NET Core MVC testování aplikace
description: Navrhování moderních webových aplikací pomocí ASP.NET Core a Azure | Test ASP.NET Core MVC aplikace
author: ardalis
ms.author: wiwagn
ms.date: 06/28/2018
ms.openlocfilehash: b6c881a445f5848829ab5ccc6ce8547a390d89f3
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404616"
---
# <a name="test-aspnet-core-mvc-apps"></a>ASP.NET Core MVC testování aplikace

> *"Pokud se vám testování produktu, pravděpodobně vaši zákazníci nebudou, jako je a otestovat ho, buď."*
 > \_-Anonymní-

Software jakékoli složitosti, může selhat neočekávaným způsobem v reakci na změny. Proto testování po provedení změn je potřeba u všech aplikací nejvíce triviální (nebo nejméně důležité). Manuální testování je nejpomalejší, nejméně spolehlivé a nejdražší způsob testování softwaru. Bohužel Pokud aplikace nejsou navržena jako možností intenzivního testování, může být k dispozici pouze prostředky. Aplikace napsané v kapitole X následující architektonických principů rozloženy by měl být možností intenzivního testování jednotek a aplikace ASP.NET Core podporují automatizované integraci a také funkční testování.

## <a name="kinds-of-automated-tests"></a>Druhy automatizované testy

Existují různé druhy automatizovaných testů pro softwarové aplikace. Nejjednodušší, nejnižší úrovni test je testování částí. Mírně vyšší úrovně jsou integrační testy a funkčních testů. Jiné druhy testů, jako jsou testy uživatelského rozhraní, zátěžové testy, zátěžové testy a orientačních testů jsou nad rámec tohoto dokumentu.

### <a name="unit-tests"></a>Testování částí

Test jednotky testů jedné části vaší aplikace logiky. Jeden je podrobnější popis uvedením některé z akcí, které není. Testování částí nepodporuje testování, jak váš kód funguje bez závislostí nebo infrastruktury –, který je co integrační testy jsou určené pro. Jednotkový test není testovací rozhraní, které váš kód psaní vycházelo – by měl předpokládat ho funguje nebo, pokud pro vás není oznámit chybu a kód alternativní řešení. Testování částí spouští kompletně v paměti a v procesu. Nelze komunikovat pomocí systému souborů, sítě nebo v databázi. Testy jednotek by měl pouze testování kódu.

Testy jednotek, tím, že fakt, že se test pouze jednu jednotku kódu, nemá žádné externí závislosti, by se měl spustit velmi rychle. Proto byste měli spustit testovací sady stovky testů jednotek za pár sekund. Spuštění je často, v ideálním případě před každou push do úložiště správy sdílené zdroje a jistě s každou automatické sestavení na vašem serveru sestavení.

### <a name="integration-tests"></a>Integrační testy

I když je vhodné k zapouzdření kódu, který komunikuje s infrastruktury, jako jsou databáze nebo souborové systémy, budete mít stále některé tento kód a budete pravděpodobně chtít otestovat. Kromě toho byste měli ověřit, že váš kód vrstvy pracovat jako očekáváte, že když jsou zcela přeložit závislostí aplikace. To odpovídá testů integrace. Integrační testy mají být pomalejší a obtížnější než testování částí, nastavit, protože jsou často závislé na vnější závislosti a infrastrukturou. Proto byste se měli vyhnout testování věcí, které by mohly být testy s testy jednotek v testech integrace. Pokud daný scénář můžete otestovat pomocí testování částí, měli byste otestovat pomocí testování částí. Pokud není možné, zvažte použití o test integrace.

Integrační testy se mají často mnohem složitější nastavení a jejich vyřazování z provozu postupy než testování částí. Například o test integrace, který odkazuje na databázi aplikace skutečný potřebovat způsob, jak vrátit databázi do známého stavu před jednotlivých testovacích běhů. Jak se přidávají nové testy a schéma databáze produkční vyvíjí, tyto testovací skripty bodech zvětšit velikost a složitost. V mnoha velkých systémů je nepraktické spustit úplné sady testů integrace na vývojářské pracovní stanice před vrácením se změnami do správy sdílených zdrojů. V těchto případech se může spustit testy integrace na serveru sestavení.

Implementace třídy LocalFileImageService implementuje logiku pro načítání a vrátí počet bajtů soubor obrázku z konkrétní složky zadané id:

```csharp
public class LocalFileImageService : IImageService
{
    private readonly IHostingEnvironment _env;
    public LocalFileImageService(IHostingEnvironment env)
    {
        _env = env;
    }
    public byte[] GetImageBytesById(int id)
    {
        try
        {
            var contentRoot = _env.ContentRootPath + "//Pics";
            var path = Path.Combine(contentRoot, id + ".png");
            return File.ReadAllBytes(path);
        }
        catch (FileNotFoundException ex)
        {
            throw new CatalogImageMissingException(ex);
        }
    }
}
```

### <a name="functional-tests"></a>Funkční testy

Integrační testy se zapisují z pohledu vývojáře, chcete-li ověřit, že některé součásti systému správně fungovat společně. Funkční testy se zapisují z pohledu uživatele a ověřte správnost podle svých požadavků na systém. Následující úryvek nabízí užitečné přirovnání jak uvažovat o funkčních testů v porovnání s testy jednotek:

> "V mnoha případech vývoj systému je připodobnit sestavování z domu. Zatímco tato analogie není úplně správná, teď ho můžeme rozšířit pro účely vysvětlení rozdílu mezi částí a funkčních testů. Testování jednotek je obdobou vytváření inspektoru konstrukce společnosti organizace. Má se zaměřuje na různých interních systémů house základ vypracování, elektrický, domovních instalací a tak dále. Má zajišťuje (testů), součástí dům bude fungovat správně a bezpečně, to znamená, že splňují sestavování kódu. Funkční testy v tomto scénáři jsou podobná na základě návštěvě tohoto webu stejné konstrukce. Má se předpokládá, že se bude odpovídajícím způsobem chovat interních systémů, inspektor vytváření fungování jeho úlohy. Základě se zaměřuje na co je třeba to je toto porušuje. Problémem vzhledu dům, jsou různé místnosti pohodlné velikost, nemá dům podle potřeb vaší rodiny, jsou windows nevhodná situace pro zachycení sun ráno. Na dům provádí základě funkčních testů. Má pohledu uživatele. Inspektor sestavení na dům provádí testy jednotek. Má Tvůrce perspektivy."

Zdroj: [testování a funkční testy jednotek](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)

Jsem rádi o tom, že "jako vývojáři služeb při selhání dvěma způsoby: jsme integrovali věc nesprávné nebo integrujeme špatného." Testování částí zajišťuje, že vytváříte věc, kterou vpravo; funkční testy – Ujistěte se, že vytváříte správné věci.

Vzhledem k tomu, že funkční testy pracovat na úrovni systému, můžou vyžadovat jistou automatizace uživatelského rozhraní. Stejně jako integrační testy obvykle fungují s nějaký druh také infrastrukturu pro testování. Díky tomu je pomalejší a křehký více než testy jednotky a integrace. Měli byste mít jenom tolik funkčních testů, jak potřebujete být jistí, systému se nechová podle očekávání uživatelů.

### <a name="testing-pyramid"></a>Testování pyramidového diagramu

Martina Fowlera napsal o testování pyramidového diagramu, které příklad v obrázek 9-1.

![](./media/image9-1.png)

Obrázek 9-1 testování pyramidového diagramu

Různé vrstvy pyramidy a jejich relativní velikosti představují různé druhy testů a kolik měli byste psát pro vaši aplikaci. Jak je vidět, doporučujeme mít velký základ testování částí nepodporuje menší vrstvy testů integrace, dokonce i menší vrstvou funkčních testů. Každá vrstva by měl v ideálním případě obsahovat pouze testy, které se nedá adekvátně v nižší vrstvě. Testování pyramidového diagramu mít na paměti, když se pokoušíte rozhodnout, jaký druh testu, je nutné pro konkrétní scénář.

### <a name="what-to-test"></a>Co se má testovat

Běžný problém pro vývojáře, kteří jsou Nezkušený s vytváření automatizovaných testů se chystá s co se má otestovat. Dobrým výchozím bodem je otestovat podmíněnou logiku. Kdekoli měl odpovídající metodu s chování, které mění podle údajů zadaných v podmíněném příkazu (if-else, přepnout, atd.), byste měli aktivován alespoň několik testy, které potvrdí správný chování za určitých podmínek. Pokud má váš kód chybové stavy, je vhodné k zápisu u minimálně jednoho testu pro "všechno nejlepší cestu" skrze kód (s žádné chyby) a alespoň jeden test pro "sad cesty" (s chybami nebo atypické výsledky) pro potvrzení, že vaše aplikace chová podle očekávání i v případě chyby. A konečně pokuste se zaměřit na testování věcí, které může selhat, místo zaměření na metriky, jako je pokrytí kódu. Další pokrytí kódu je obecně lepší než méně. Zápis několik více testů velmi náročné a komplexní obchodní – metoda je však obvykle lepší využití času než psaní testů pro automatické vlastnosti pouze ke zlepšení metriky pro pokrytí kódu testu.

## <a name="organizing-test-projects"></a>Uspořádání projektů testování

Projekty testů lze uspořádat, ale funguje nejlépe za vás. Je vhodné oddělit testy podle typu (testování částí, test integrace) a co testují (podle projektu, oboru názvů). Ať už toto oddělení se skládá ze složky v rámci jednoho testovacího projektu, nebo více zkušebních projektů, je rozhodnutí o návrhu. Nejjednodušší je jeden projekt, ale pro velké projekty s mnoho testů, nebo chcete-li snadněji spustit různé sady testů, můžete chtít mít několik různých testovacích projektů. Mnoho týmů uspořádat projekty testů podle projektu, které testují, který pro aplikace s více než několik projektů může mít za následek velký počet projekty testů, zejména v případě, že se můžete stále rozdělit tyto podle druh testy jsou v každém projektu. Přístup založený na ohrožení zabezpečení je, aby jeden projekt za druh testu na aplikaci, se složkami v testovacích projektů po označení projektu (a třída) testován.

Běžným přístupem je uspořádat projekty aplikací v rámci složky "src" a projekty testů aplikace v rámci složky paralelní "testů". Pokud najdete užitečné této organizace, můžete vytvořit odpovídající složky řešení v sadě Visual Studio.

![](./media/image9-2.png)

Obrázek 9-2 Test organizace ve vašem řešení

Můžete použít testovací vámi preferované rozhraní. Rozhraní xUnit dobře funguje a co se všechny testy v ASP.NET Core a EF Core jsou napsané v. V sadě Visual Studio pomocí šablony je znázorněno v obrázek 9-3, nebo z rozhraní příkazového řádku pomocí nové xunit dotnet můžete přidat projekt testů xUnit.

![](./media/image9-3.png)

Obrázek 9-3 v sadě Visual Studio přidejte projekt testů xUnit

### <a name="test-naming"></a>Názvy testů

Byste měli pojmenovat testů v konzistentní podobě s názvy, které označují, co dělá každého testu. Jedním z přístupů, které měl skvělý o úspěšných nasazeních je název testovací třídy podle třídy a metody, které testují. Výsledkem je mnoho tříd malý test, ale umožní bylo velmi jasné, co je zodpovědný za každý test. Pomocí názvu třídy testů nastavení k identifikaci třídy a metody, které má být testována název testovací metody slouží k určení chování testován. Ty by měly zahrnovat očekávané chování a žádné vstupy nebo předpokladů, které by měl vést k tomuto chování. Některé příklady názvů testů:

- `CatalogControllerGetImage.CallsImageServiceWithId`

- `CatalogControllerGetImage.LogsWarningGivenImageMissingException`

- `CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess`

- `CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException`

Variace tohoto přístupu končí názvem testovací třídy "By" a mírně změní čas:

- `CatalogControllerGetImage`**By měl**`.`**volání**`ImageServiceWithId`

- `CatalogControllerGetImage`**By měl**`.`**protokolu**`WarningGivenImageMissingException`

Některé týmy najít druhý způsob pojmenování jasnější, ale o něco víc verbose. V každém případě zkuste použít zásady vytváření názvů, který poskytuje podrobné informace o chování testu tak, aby když dojde k selhání jednoho nebo více testů, je zřejmý z jejich názvy, jaké případy, které selhaly. Vyhněte se pojmenování můžete testy představu o možných, jako je například ControllerTests.Test1, jako ty nabízejí žádnou hodnotu, když se zobrazí ve výsledcích testu.

Pokud budete postupovat podle zásady vytváření názvů jako ten výše, který vytvoří mnoho tříd malý test, je vhodné uspořádat ještě více testů pomocí složky a obory názvů. Jedním z přístupů k uspořádání testů podle složky, které obsahuje několik testovacích projektů je vidět na obrázku 9-4.

![](./media/image9-4.png)

**Obrázek 9-4.** Uspořádání testovacích tříd ve složce založené na třídě testován.

Samozřejmě pokud třída konkrétní aplikace má mnoho metod testování (a tedy mnoho testovací třídy), může mít smysl ve složce odpovídající – třída aplikace umístit. Toto uspořádání se nijak neliší od jak můžete organizovat soubory do složek, které jinde. Pokud máte více než tři nebo čtyři související soubory ve složce obsahující mnoho souborů, je často užitečné k přesunutí do své vlastní podsložce.

## <a name="unit-testing-aspnet-core-apps"></a>Aplikace ASP.NET Core pro testování částí

V dobře navržené aplikace ASP.NET Core bude se většina složitost a obchodní logiky zapouzdřeny v obchodní entity a širokou škálu služeb. Aplikace ASP.NET Core MVC, s řadiči, filtry, modely viewmodels a zobrazení, by měla vyžadovat velmi málo testování částí. Většina funkcí danou akci leží mimo samotný metody akce. Testování, zda směrování funguje správně, nebo zpracování globální chyb, není možné efektivně pomocí testování částí. Podobně všechny filtry, včetně ověření modelu a ověřování a autorizace filtry, nemůže být testován částí. Bez těchto zdrojů chování by měl být triviálně malé, delegování hromadné svou práci do služby, které můžete testovat nezávisle na kontroler, který používá většina metod akce.

V některých případech budete muset Refaktorovat kód v pořadí pro testování částí. Často to zahrnuje identifikaci abstrakce a využitím vkládání závislostí pro přístup k odběru v kódu, který chcete otestovat, spíše než kódovat infrastruktury. Zvažte například tuto metodu jednoduché akce pro zobrazení obrázků:

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

Testování tato metoda provádí složité s přímým přístupem je závislá na System.IO.File, kterou používá ke čtení ze systému souborů. Toto chování zajistit funguje podle očekávání, ale to skutečné souborech se o test integrace můžete otestovat. Je vhodné poznamenat nelze otestovat tuto metodu směrování – uvidíte, jak na to používat funkční testy za chvíli.

Pokud nelze přímo Jednotkový test chování systému souborů a nelze otestovat trasu, co má k testování? Po refaktoring provádět testování částí je to možné, může také zjistit některé testovací případy a chybějící chování, jako je zpracování chyb. Co metodu dělat, když nebyl nalezen soubor? Co to dělat? V tomto příkladu refaktorovaný metoda vypadá například takto:

```csharp
[HttpGet("[controller]/pic/{id}")\]
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

\_Protokolovací nástroj a \_obě imageService jsou vloženy jako závislosti. Nyní můžete otestovat, že je předán stejné id, který je předán metodě akce \_imageService, a že výsledný počet bajtů se vrátí jako součást FileResult. Můžete také otestovat, protokolování chyb dochází podle očekávání, a, pokud chybí bitovou kopii, vrátí se výsledek NotFound za předpokladu, že toto je chování důležité aplikace (to znamená, jenom dočasné kód pro vývojáře, přidá k diagnostice problému). Logika skutečný soubor přesunul do samostatné implementace služby a je rozšířený vrátit výjimku specifické pro aplikaci pro případ chybí soubor. Tato implementace můžete otestovat nezávisle na sobě pomocí o test integrace.

## <a name="integration-testing-aspnet-core-apps"></a>Aplikace ASP.NET Core pro testování integrace

Pokud chcete otestovat, LocalFileImageService funguje správně pomocí testu integraiton, budete muset vytvořit známý testovací soubor image a ověřte, že tato služba vrátí ho zadaný specifický vstup. Které byste měli věnovat pozornost nepoužívat mock objektů na chování, které chcete skutečně testovat (v tomto případě čtení ze systému souborů). Však mock objektů může být stále užitečné nastavit testy integrace. V takovém případě můžete napodobení IHostingEnvironment, tak, aby jeho ContentRootPath odkazuje na složku, kterou se chystáte použít pro testovací obrázek. Dokončení testovací třídě integrace pracovních je znázorněna zde:

```csharp
public class LocalFileImageServiceGetImageBytesById
{
    private byte[] _testBytes = new byte[] { 0x01, 0x02, 0x03 };
    private readonly Mock<IHostingEnvironment> _mockEnvironment = new Mock<IHostingEnvironment>();
    private int _testImageId = 123;
    private string _testFileName = "123.png";

    public LocalFileImageServiceGetImageBytesById()
    {
        // create folder if necessary
        Directory.CreateDirectory(Path.Combine(GetFileDirectory(), "Pics"));
        string filePath = GetFilePath(_testFileName);
        System.IO.File.WriteAllBytes(filePath, _testBytes);
        _mockEnvironment.SetupGet<string>(m => m.ContentRootPath).Returns(GetFileDirectory());
    }

    private string GetFilePath(string fileName)
    {
        return Path.Combine(GetFileDirectory(), "Pics", fileName);
        }
            private string GetFileDirectory()
        {
        var location = System.Reflection.Assembly.GetEntryAssembly().Location;
        return Path.GetDirectoryName(location);
    }

    [Fact]
    public void ReturnsFileContentResultGivenValidId()
    {
        var fileService = new LocalFileImageService(_mockEnvironment.Object);
        var result = fileService.GetImageBytesById(_testImageId);
        Assert.Equal(_testBytes, result);
    }
}
```

> [!NOTE]
> Samotný test je velmi jednoduché – větší část kódu je potřebné ke konfiguraci systému a vytvořit testovací infrastruktury (v tomto případě skutečný soubor ke čtení z disku). Toto je typický pro integrační testy, které často vyžadují složitější nastavení práce než testování částí.

## <a name="functional-testing-aspnet-core-apps"></a>Funkční testování aplikací ASP.NET Core

Pro aplikace ASP.NET Core třída TestServer usnadňuje funkční testy poměrně pro zápis. Konfigurace TestServer přímo pomocí WebHostBuilder (pouze pro vaši aplikaci obvyklým způsobem), nebo s typem WebApplicationFactory (k dispozici v 2.1). Měli byste vyzkoušet, co nejpřesněji souhlasit s hostitelem vašeho testu na produkční hostitele tak, že testy budou vykonávat chování podobné co aplikace provádět v produkčním prostředí. Třída WebApplicationFactory je užitečné pro konfiguraci objekt TestServer ContentRoot, který používá ASP.NET Core najít jako zobrazení statických prostředků.

Vytvoříte jednoduchou funkční testy tak, že vytvoříte testovací třídě, která implementuje IClassFixture < WebApplicationFactory<TEntry>> kde je TEntry třídu pro spuštění vaší webové aplikace. S tímto na místě můžete vytvořit testovací přípravek klienta pomocí metody CreateClient factory pro:

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

Často, bude potřeba provést další konfiguraci vašeho webu, před spuštěním každého testu, jako je například konfigurace aplikace pro použití v paměti úložiště dat a pak synchronizace replik indexů aplikace s daty testu. Proto byste měli vytvořit vlastní podtřídy WebApplicationFactory<TEntry> a přepsat její ConfigureWebHost metodu. Následující příklad je z projektu FunctionalTests eShopOnWeb a slouží jako součást testy na hlavní webové aplikace.

```cs
using Infrastructure.Data;
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Mvc.Testing;
using Microsoft.eShopWeb;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Logging;
using System;
using Microsoft.EntityFrameworkCore;
using Infrastructure.Identity;

namespace FunctionalTests.WebRazorPages
{
    public class CustomWebRazorPagesApplicationFactory<TStartup>
    : WebApplicationFactory<Startup>
    {
        protected override void ConfigureWebHost(IWebHostBuilder builder)
        {
            builder.ConfigureServices(services =>
            {
                // Create a new service provider.
                var serviceProvider = new ServiceCollection()
                    .AddEntityFrameworkInMemoryDatabase()
                    .BuildServiceProvider();

                // Add a database context (ApplicationDbContext) using an in-memory
                // database for testing.
                services.AddDbContext<CatalogContext>(options =>
                {
                    options.UseInMemoryDatabase("InMemoryDbForTesting");
                    options.UseInternalServiceProvider(serviceProvider);
                });

                services.AddDbContext<AppIdentityDbContext>(options =>
                {
                    options.UseInMemoryDatabase("Identity");
                    options.UseInternalServiceProvider(serviceProvider);
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
                        .GetRequiredService<ILogger<CustomWebRazorPagesApplicationFactory<TStartup>>>();

                    // Ensure the database is created.
                    db.Database.EnsureCreated();

                    try
                    {
                        // Seed the database with test data.
                        CatalogContextSeed.SeedAsync(db, loggerFactory).Wait();
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

Testy můžete využít tuto vlastní WebApplicationFactory tak, že použijete k vytvoření klienta a pak zasílání požadavků na aplikaci pomocí instance tohoto klienta. Aplikace bude mít nasazený data, která slouží jako část testu kontrolní výrazy. Tento test ověřuje, že na domovskou stránku eShopOnWeb aplikace Razor Pages načte správně a obsahuje seznam produktů, která byla přidána k aplikaci jako součást počáteční hodnoty data.

```cs
using Microsoft.eShopWeb.RazorPages;
using System.Net.Http;
using System.Threading.Tasks;
using Xunit;

namespace FunctionalTests.WebRazorPages
{
    public class HomePageOnGet : IClassFixture<CustomWebRazorPagesApplicationFactory<Startup>>
    {
        public HomePageOnGet(CustomWebRazorPagesApplicationFactory<Startup> factory)
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
            Assert.Contains(".NET Bot Black Sweatshirt", stringResponse); // from seed data
        }
    }
}
```

Tato funkční testování vykonává úplné ASP.NET Core MVC / zásobníku aplikace Razor Pages, včetně middleware, filtry, vazače, atd., které mohou být na místě. Ověřuje, že danou trasou ("/") vrátí stavový kód úspěchu očekávané a výstupu protokolu HTML. Provádí se bez nastavování skutečné webový server a proto zabraňuje velkou část brittleness, který používá skutečné webového serveru pro účely testování můžete vyzkoušet (například problémy s nastavením brány firewall). Funkční testy, které spustily TestServer jsou obvykle nižší než integraci a testy jednotek, ale jsou mnohem rychleji než testy, které se spustí v síti k serveru webového testu. Abyste používali funkční testy k zajištění, že zásobník front-endu vaší aplikace funguje podle očekávání. Tyto testy jsou zvláště užitečné při najít duplicity ve vašich kontrolerech nebo stránky a adresy duplicity přidáním filtrů. V ideálním případě by tento refaktoring nedojde ke změně chování aplikace a sadu funkční testy se ověří, že jde o tento případ.

>[!div class="step-by-step"]
[Předchozí](work-with-data-in-asp-net-core-apps.md)
[další](development-process-for-azure.md)
