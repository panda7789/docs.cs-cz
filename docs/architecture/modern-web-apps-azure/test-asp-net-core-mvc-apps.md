---
title: Test ASP.NET Core aplikací MVC
description: Architekt moderních webových aplikací pomocí ASP.NET Core a Azure | Test ASP.NET Core aplikací MVC
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 4e4ab71cc542767460e92be1510ccc5c5e0e7ce0
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374074"
---
# <a name="test-aspnet-core-mvc-apps"></a>Test ASP.NET Core aplikací MVC

> *"Pokud si nejste spokojeni s testováním částí vašeho produktu, pravděpodobně ho vaši zákazníci nechtějí testovat, buď."*
 > \_Anonymous

Software jakékoli složitosti může při reakci na změny selhat neočekávaným způsobem. Proto se testování po provedení změn vyžaduje pro všechny, ale nejvíce triviální (nebo nejméně kritické) aplikace. Manuální testování je nejpomalejší, nejméně spolehlivý a nejnákladný způsob testování softwaru. Pokud aplikace není navržena tak, aby se testovatelné, může to být pouze to, co je k dispozici. Aplikace napsané podle principů architektury, které jsou uvedeny v [kapitole 4](architectural-principles.md) , by měly být jednotky testovatelné a aplikace ASP.NET Core podporují také automatickou integraci a funkční testování.

## <a name="kinds-of-automated-tests"></a>Druhy automatizovaných testů

Existuje mnoho druhů automatizovaných testů pro softwarové aplikace. Nejjednodušším, nejnižším testem úrovně je test jednotky. Na poněkud vyšší úrovni existují integrační testy a funkční testy. Jiné druhy testů, jako jsou testy uživatelského rozhraní, zátěžové testy, zátěžové testy a testy kouře, jsou nad rámec tohoto dokumentu.

### <a name="unit-tests"></a>Testování částí

Test jednotek testuje jednu část logiky vaší aplikace. Jednu z nich může popsána uvedením některých věcí, které nejsou. Test jednotek netestuje, jak váš kód funguje se závislostmi nebo infrastrukturou – to je to, pro které jsou k disviset testy. Test jednotek netestuje rozhraní, ve kterém je váš kód napsán – měli byste předpokládat, že funguje, nebo pokud ho nenajdete, poznamenejte si chybu a kód a požádejte ho. Test jednotek běží zcela v paměti a zpracovává se. Nekomunikuje se systémem souborů, sítí nebo databází. Testy jednotek by měly testovat pouze váš kód.

Testování částí, na základě skutečnosti, že testuje pouze jednu jednotku vašeho kódu bez externích závislostí, by mělo být prováděno velmi rychle. Proto byste měli být schopni spustit testovací sady stovek jednotek testů za několik sekund. Spouštějte je často, ideálně před každým vložením do sdíleného úložiště správy zdrojového kódu a jistě u každého automatizovaného sestavení na serveru sestavení.

### <a name="integration-tests"></a>Integrační testy

I když je vhodné zapouzdřit kód, který komunikuje s infrastrukturou, jako jsou databáze a systémy souborů, budete mít i nějaký kód a budete ho pravděpodobně chtít otestovat. Kromě toho byste měli ověřit, že vrstvy kódu pracují podle očekávání, když jsou závislosti vaší aplikace zcela vyřešeny. Jedná se o zodpovědnost za integrační testy. Testy integrace mají za následek pomalejší a obtížnější nastavení než testování částí, protože jsou často závislé na externích závislostech a infrastruktuře. Proto byste se měli vyhnout testování věcí, které by mohly být testovány pomocí testů jednotek v rámci integračních testů. Pokud otestujete daný scénář s testováním částí, měli byste ho otestovat pomocí testu jednotek. Pokud nemůžete, zvažte použití integračního testu.

Integrační testy často mají složitější nastavení a rozboru postupy než testy jednotek. Například test integrace, který se dostane ke skutečné databázi, bude potřebovat způsob, jak vrátit databázi do známého stavu před každým spuštěním testu. Při přidání nových testů a vývoje produkčního schématu databáze budou tyto testovací skripty v úmyslu růst velikosti a složitosti. V mnoha velkých systémech je nepraktické spouštět úplné sady integračních testů na pracovních stanicích pro vývojáře před vrácením změn do správy sdíleného zdrojového kódu. V těchto případech mohou být integrační testy spuštěny na serveru sestavení.

### <a name="functional-tests"></a>Funkční testy

Integrační testy se napíší z perspektivy vývojářů, aby bylo možné ověřit, že některé součásti systému fungují správně společně. Funkční testy se zapisují z perspektivy uživatele a ověřují správnost systému na základě jeho požadavků. Následující úryvek nabízí užitečný analogový způsob, jak si představit o funkčních testech v porovnání s testováním částí:

> "" Hodně vývoje systému likened do budování domu. I když tato analogová možnost není poměrně správná, můžeme ji pro účely porozumění rozdílu mezi jednotkou a funkčními testy roztáhnout. Testování částí je obdobné jako inspektor stavby, který se navštíví na staveništi. Zaměřuje se na různé interní systémy domu, základů, rámců, elektroinstalace, instalací a tak dále. Zajišťuje (testuje), že části domu budou fungovat správně a bezpečně, to znamená, že budou splňovat stavební kód. Funkční testy v tomto scénáři jsou obdobou domácnosti návštěvě tohoto téhož staveništového webu. Předpokládá, že se interní systémy budou chovat patřičně, takže inspektor budovy provádí jeho úlohu. Domácnosti se zaměřuje na to, co bude v této domácnosti v provozu. Záleží na tom, jak se na pracovišti nachází, na různých místnostech a na tom, kde se v rodině hodí, jsou Windows na dobrém místě pro zachycení ráno. Domácnosti provádí funkční testy na domu. Má perspektivu uživatele. Inspektor budovy provádí testování částí na pracovišti. Má perspektivu tvůrce. "

Zdrojová [Testování částí versus funkční testy](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)

Fond jsem se říkám vývojářům, že nedošlo k chybě dvěma způsoby: nepovedlo se nám sestavit chybu, nebo jsme vytvořili špatné věci. " Testování částí vám zajistí, že vytváříte přímo věc. funkční testy zajistí, že vytváříte správnou věc.

Vzhledem k tomu, že funkční testy fungují na úrovni systému, mohou vyžadovat určitý stupeň automatizace uživatelského rozhraní. Stejně jako integrační testy obvykle pracují s určitým druhem testovací infrastruktury. Díky tomu jsou pomalejší a větší poměrně křehký než testy jednotek a integrace. Měli byste mít jenom tolik funkčních testů, protože potřebujete mít jistotu, že se systém chová, jako uživatelé očekávají.

### <a name="testing-pyramid"></a>Testovací jehlan

Martin Fowlera zapsaný k testovacímu pyramidu, který je příkladem zobrazeného na obrázku 9-1.

![Testovací jehlan](./media/image9-1.png)

**Obrázek 9-1**. Testovací jehlan

Různé vrstvy pyramidy a jejich relativní velikosti, reprezentují různé druhy testů a počet, kolik byste měli pro svou aplikaci psát. Jak vidíte, doporučuje se mít velký základ testování částí, který je podporován menší vrstvou integračních testů, s ještě menší vrstvou funkčních testů. Každá vrstva by v ideálním případě měla mít pouze testy, které nemohou být provedeny přiměřeně na nižší vrstvě. Mějte na paměti, že při pokusu o určení toho, jaký typ testu potřebujete pro konkrétní scénář, mějte na paměti jehlany s testováním.

### <a name="what-to-test"></a>Co testovat

Běžný problém pro vývojáře, kteří mají zkušenosti s psaním automatizovaných testů, se blíží k testování. Dobrým výchozím bodem je testování podmíněné logiky. Kdekoli máte metodu s chováním, které se mění v závislosti na podmíněném příkazu (if-else, Switch atd.), měli byste být schopni vytvořit alespoň několik testů, které pro určité podmínky potvrzují správné chování. Pokud má váš kód chybové podmínky, je vhodné napsat alespoň jeden test pro "příjemné" cestu prostřednictvím kódu (bez chyb) a alespoň jeden test pro "cestu JSD" (s chybami nebo netypickými výsledky) k potvrzení, že se aplikace chová jako očekávaná na výskytu chyb. Nakonec se snažte soustředit na testování věcí, které mohou selhat, a nemusíte se zaměřit na metriky, jako je pokrytí kódu. Větší pokrytí kódu je lepší než méně, obecně. Nicméně zápis několika dalších testů pro velmi složitou a nepostradatelnou metodu je obvykle vhodnější než při psaní testů pro automatické vlastnosti, a to jenom pro zlepšení metriky pokrytí testovacího kódu.

## <a name="organizing-test-projects"></a>Uspořádání projektů testů

Projekty testů mohou být uspořádány, ale budou pro vás nejlépe fungovat. Je vhodné oddělit testy podle typu (testování částí, test integrace) a podle toho, co jsou testovány (podle projektu, podle oboru názvů). Bez ohledu na to, zda se toto oddělení skládá ze složek v rámci jednoho testovacího projektu nebo více testovacích projektů, je rozhodnutí o návrhu. Jeden projekt je nejjednodušší, ale pro velké projekty s mnoha testy nebo pro snazší spouštění různých sad testů může být vhodné mít několik různých testovacích projektů. Mnoho týmů organizuje projekty testů na základě projektu, který testuje, což pro aplikace s více než několika projekty může vést k velkému počtu testovacích projektů, zejména v případě, že je stále rozdělíte podle toho, jaké typy testů jsou v jednotlivých projektech. Přístup k ohrožení je mít jeden projekt na typ testu, na aplikaci a složky uvnitř testovacích projektů k označení projektu (a třídy), který je testován.

Běžným přístupem je uspořádání projektů aplikace do složky src a testovacích projektů aplikace v rámci paralelní "testy". Můžete vytvořit vyhovující složky řešení v aplikaci Visual Studio, pokud najdete tuto organizaci jako užitečnou.

![Testování organizace ve vašem řešení](./media/image9-2.png)

**Obrázek 9-2**. Testování organizace ve vašem řešení

Můžete použít jakékoli testovací rozhraní, které dáváte přednost. XUnit Framework dobře funguje a je to, co všechny ASP.NET Core a EF Core testy jsou napsány v. Projekt testů xUnit můžete do sady Visual Studio přidat pomocí šablony zobrazené na obrázku 9-3 nebo z rozhraní příkazového řádku pomocí příkazu dotnet New xUnit.

![Přidání projektu testů xUnit do sady Visual Studio](./media/image9-3.png)

**Obrázek 9-3**. Přidání projektu testů xUnit do sady Visual Studio

### <a name="test-naming"></a>Pojmenování testů

Testy byste měli pojmenovat konzistentním způsobem s názvy, které určují, co každý test dělá. Jedním z přístupů, které mám skvělou úspěšnost, je pojmenovat třídy testu podle třídy a metody, které testuje. Výsledkem je mnoho malých testovacích tříd, ale je velmi jasné, co každý test zodpovídá za. S názvem třídy testu nastaveným k identifikaci třídy a metody, která má být testována, lze název testovací metody použít k určení testovaného chování. To by mělo zahrnovat očekávané chování a všechny vstupy nebo předpoklady, které by měly toto chování vracet. Příklady názvů testů:

- `CatalogControllerGetImage.CallsImageServiceWithId`

- `CatalogControllerGetImage.LogsWarningGivenImageMissingException`

- `CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess`

- `CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException`

Variace tohoto přístupu končí každý název třídy testu pomocí "by" měl "a vhodné mírně mění:

- `CatalogControllerGetImage`**By mělo**`.`**zavolat**`ImageServiceWithId`

- `CatalogControllerGetImage`**Měl by**`.`se**Protokolovat**`WarningGivenImageMissingException`

Někteří týmy hledají druhý jasný přístup k pojmenování, i když mírně podrobnější. V každém případě se pokuste použít konvenci pojmenování, která poskytuje přehled o chování testu, aby při selhání jednoho nebo více testů bylo zřejmé, že se nezdařily jejich názvy. Vyhněte se pojmenovávání testů Vaguely, jako je ControllerTests. test1, protože při jejich zobrazení ve výsledcích testů nejsou k dispozici žádná hodnota.

Pokud budete postupovat podle konvence pojmenování, jako je ta výše, která vytváří mnoho malých testovacích tříd, je vhodné lépe uspořádat testy pomocí složek a oborů názvů. Obrázek 9-4 ukazuje jeden z přístupů k organizování testů podle složky v rámci několika testovacích projektů.

![Uspořádání tříd testu podle složky na základě testované třídy](./media/image9-4.png)

**Obrázek 9-4.** Uspořádání tříd testu podle složky na základě testované třídy.

Samozřejmě platí, že pokud konkrétní třída aplikace má testovat mnoho metod (a tedy mnoho testovacích tříd), může být vhodné umístit je do složky, která odpovídá třídě aplikace. Tato organizace se neliší od způsobu, jakým můžete soubory uspořádat do složek jinde. Pokud máte ve složce obsahující mnoho dalších souborů více než tři nebo čtyři související soubory, je často vhodné je přesunout do své vlastní podsložky.

## <a name="unit-testing-aspnet-core-apps"></a>Testování částí ASP.NET Core aplikací

V dobře navržené aplikaci ASP.NET Core bude většina složitosti a obchodní logiky zapouzdřená v obchodních entitách a v různých službách. Aplikace ASP.NET Core MVC samotná, s jejími kontroléry, filtry, ViewModels a zobrazeními, by měla vyžadovat hodně testů jednotek. Většina funkcí dané akce leží mimo metodu Action sám. Testování, zda směrování funguje správně, nebo globální zpracování chyb, nelze provést efektivně pomocí testu jednotek. Podobně platí, že jakékoli filtry, včetně ověřování modelu a ověřování a ověřovacích filtrů, nemůžou být testovány jednotkou. Bez těchto zdrojů chování by většina metod akcí měla být triviální, a to bez ohledu na to, jestli je jejich práce na služby, která se dá testovat nezávisle na řadiči, který je používá.

Někdy budete muset kód Refaktorovat za účelem testování částí. To často zahrnuje identifikaci abstrakcí a použití injektáže závislosti pro přístup k abstrakci v kódu, který chcete testovat, spíše než kódování přímo proti infrastruktuře. Zvažte například tuto jednoduchou metodu akce pro zobrazení obrázků:

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

Testování částí: Tato metoda je obtížná při přímé závislosti na `System.IO.File`, kterou používá ke čtení ze systému souborů. Toto chování můžete otestovat, abyste zajistili, že funguje podle očekávání, ale v reálném souboru je test integrace. Vybereme na vědomí, že nemůžete testovat tuto trasu této metody – v krátké době se vám ukáže, jak to udělat s funkčním testem.

Pokud nemůžete testovat chování systému souborů přímo a nemůžete testovat trasu, co je pro test k dispozici? I po refaktorování, aby bylo možné testování jednotek, můžete zjistit některé testovací případy a chybějící chování, například zpracování chyb. Co metoda dělá, když se soubor nenajde? Co by mělo dělat? V tomto příkladu vypadá refaktoring Method takto:

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

Protokolovací nástroje a \_imageService jsou vloženy jako závislosti. \_ Nyní můžete testovat, že stejné ID, které je předáno metodě Action, je předáno do \_imageService a že výsledné bajty jsou vráceny jako součást výsledku. Můžete také otestovat, že protokolování chyb probíhá podle očekávání, a že se vrátí výsledek NotFound v případě, že chybí obrázek. za předpokladu, že se jedná o důležité chování aplikace (ne pouze dočasný kód, který vývojář přidal k diagnostice problému). Skutečná logika souboru se přesunula do samostatné implementační služby a rozšířila se, aby vracela výjimku specifickou pro danou aplikaci pro případ chybějícího souboru. Tuto implementaci můžete testovat nezávisle pomocí testu integrace.

Ve většině případů budete chtít použít globální obslužné rutiny výjimek v řadičích, takže v nich by měla být velikost logiky minimální a pravděpodobně nebude znamenat testování částí. Většinu testování akcí kontroleru byste měli provést pomocí funkčních testů a `TestServer` třídy popsané níže.

## <a name="integration-testing-aspnet-core-apps"></a>Testování integrace ASP.NET Core aplikací

Většina testů integrace v aplikacích ASP.NET Core by měla být testovací služby a další typy implementace definované v projektu infrastruktury. Můžete například [otestovat, že EF Core úspěšně aktualizoval a načítá data, která očekáváte](https://docs.microsoft.com/ef/core/miscellaneous/testing/) z tříd přístupu k datům umístěných v projektu infrastruktury. Nejlepším způsobem, jak otestovat, že se váš ASP.NET Core projekt MVC chová správně, je funkční testy, které běží na vaší aplikaci běžící na testovacím hostiteli.

## <a name="functional-testing-aspnet-core-apps"></a>Funkční testování ASP.NET Core aplikací

U ASP.NET Corech aplikací `TestServer` třída provádí funkční testy poměrně snadného zápisu. Můžete nakonfigurovat `TestServer` `WebHostBuilder` přímým použitím (jako obvykle pro aplikaci `WebApplicationFactory` ) nebo s typem (k dispozici od verze 2,1). Měli byste se pokusit přesně vyhledat svého testovacího hostitele na produkčního hostitele, aby testy mohly postupovat podobně jako v případě, že aplikace provede v produkčním prostředí. Tato `WebApplicationFactory` třída je užitečná pro konfiguraci ContentRootu TestServer, která je používána ASP.NET Core k nalezení statických prostředků, jako jsou zobrazení.

Jednoduché funkční testy můžete vytvořit vytvořením třídy testu, která implementuje IClassFixture\<WebApplicationFactory\<TEntry > >, kde TEntry je vaše spouštěcí třída vaší webové aplikace. Na tomto místě testovací přípravek může vytvořit klienta pomocí metody CreateClient objektu pro vytváření:

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

Často budete chtít před jednotlivými testovacími běhy provést nějakou další konfiguraci vašeho webu, jako je například konfigurace aplikace tak, aby používala úložiště dat v paměti a pak dosazení aplikace s testovacími daty. K tomu byste měli vytvořit vlastní podtřídu WebApplicationFactory\<TEntry > a přepsat jeho ConfigureWebHost metodu. Níže uvedený příklad je z projektu eShopOnWeb FunctionalTests a slouží jako součást testů v hlavní webové aplikaci.

```cs
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Mvc.Testing;
using Microsoft.EntityFrameworkCore;
using Microsoft.eShopWeb.Infrastructure.Data;
using Microsoft.eShopWeb.Infrastructure.Identity;
using Microsoft.eShopWeb.Web;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Logging;
using System;

namespace Microsoft.eShopWeb.FunctionalTests.Web.Controllers
{
    public class CustomWebApplicationFactory<TStartup>
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
                        .GetRequiredService<ILogger<CustomWebApplicationFactory<TStartup>>>();

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

Testy mohou pomocí tohoto vlastního WebApplicationFactory vytvořit klienta a následně provádět požadavky na aplikaci pomocí této klientské instance. Aplikace bude mít osazená data, která lze použít jako součást kontrolních výrazů testu. Následující test ověří, zda se Domovská stránka aplikace eShopOnWeb správně načítá a obsahuje seznam produktů přidaných do aplikace v rámci počátečních dat.

```cs
using Microsoft.eShopWeb.FunctionalTests.Web.Controllers;
using Microsoft.eShopWeb.Web;
using System.Net.Http;
using System.Threading.Tasks;
using Xunit;

namespace Microsoft.eShopWeb.FunctionalTests.WebRazorPages
{
    public class HomePageOnGet : IClassFixture<CustomWebApplicationFactory<Startup>>
    {
        public HomePageOnGet(CustomWebApplicationFactory<Startup> factory)
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

Tento funkční test vykonává úplný ASP.NET Core zásobník aplikací MVC/Razor Pages, včetně všech middlewarů, filtrů, pořadačů atd., které mohou být na místě. Ověřuje, že daná trasa ("/") vrací stavový kód očekávané úspěšnosti a výstup ve formátu HTML. Je to bez nastavování reálného webového serveru, takže předejdete většině brittleness, které používají skutečný webový server pro testování, může nastat (například problémy s nastavením brány firewall). Funkční testy, které jsou spouštěny proti TestServer, jsou obvykle pomalejší než při integraci a testování částí, ale jsou mnohem rychlejší než testy, které by mohly být spuštěny přes síť s testovacím webovým serverem. Použijte funkční testy, abyste zajistili, že zásobník front-endu vaší aplikace funguje podle očekávání. Tyto testy jsou zvláště užitečné při hledání duplicity na vašich řadičích nebo na stránkách a při odstraňování duplicit pomocí přidávání filtrů. V ideálním případě tento refaktoring nezmění chování aplikace a sada funkčních testů ověří, zda se jedná o tento případ.

> ### <a name="references--test-aspnet-core-mvc-apps"></a>Odkazy – test ASP.NET Core aplikace MVC
>
> - **Testování v ASP.NET Core**  
>   <https://docs.microsoft.com/aspnet/core/testing/>
> - **Konvence pojmenování testů jednotek**  
>   <https://ardalis.com/unit-test-naming-convention>
> - **EF Core testování**  
>   <https://docs.microsoft.com/ef/core/miscellaneous/testing/>

>[!div class="step-by-step"]
>[Předchozí](work-with-data-in-asp-net-core-apps.md)Další
>[](development-process-for-azure.md)
