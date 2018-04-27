---
title: Testování jádro ASP.NET MVC aplikace
description: Architektury moderních webových aplikací pomocí ASP.NET Core a Azure | Testování jádro ASP.NET MVC aplikace
author: ardalis
ms.author: wiwagn
ms.date: 10/08/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c9e71e7aeffbdb0721dae8487fe027b937b5b28a
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="test-aspnet-core-mvc-apps"></a>Testování jádro ASP.NET MVC aplikace

> _"Pokud chcete svůj produkt testování částí, s největší pravděpodobností vašim zákazníkům nebude rádi otestovat ji, buď."_
> _ – Anonymní -

## <a name="summary"></a>Souhrn

Software jakékoli složitosti může selhat v reakci na změny neočekávaným způsobem. Proto testování po provedení změn je vyžadována pro všechny, ale většina trivial (nebo nejméně důležité) aplikace. Manuální testování je nejpomalejší, nejméně spolehlivé a nejnákladnější způsob, jak otestovat softwaru. Bohužel Pokud nejsou určeny jako možností intenzivního testování, může být jediným způsobem, který je k dispozici. Aplikace napsané následující architektury Principy nastíněny v kapitole X musí být jednotka možností intenzivního testování a ASP.NET Core aplikace podporují automatické integraci a také funkční testování.

## <a name="kinds-of-automated-tests"></a>Druhy automatizované testy

Existují různé druhy automatizovaných testů pro softwarové aplikace. Nejjednodušším, nejnižší úrovni testu je testování částí. Mírně vyšší úrovně jsou integrace testy a funkčních testů. Ostatní typy testů, jako například testy uživatelského rozhraní, zátěžových testů, zátěžových testů a kouře testy, jsou nad rámec tohoto dokumentu.

### <a name="unit-tests"></a>Testy jednotek

Testování částí testů jedné součásti vaší aplikace logiky. Jeden ho další popisují tak, že uvedete několik kroků, které není. Testování částí není testovat, jak se váš kód funguje s závislosti nebo infrastruktury – co integrace testy pro. Testování částí nepodporuje testování rozhraní framework kódu se zapisují na – byste měli počítat ho pracuje nebo, pokud pro vás není, založení záznamu o chybě a code alternativní řešení. Testování částí spouští zcela v paměti a v procesu. Nepodporuje se komunikace se serverem systému souborů, v síti nebo v databázi. Testování částí by měla pouze Otestujte svůj kód.

Testy jednotek, na základě skutečnosti, že testují pouze jedné jednotky kódu, nemá žádné externí závislosti, musí provést velmi rychle. Proto byste měli mít testovacích sad stovky testování částí spustit za několik sekund. Je často spouštíte, ideálně před každou nabízené do ovládacího prvku úložiště sdíleného zdroje a jistě s každou automatizované sestavení na vašem serveru sestavení.

### <a name="integration-tests"></a>Integrace testů

Přestože je vhodné pro zapouzdření váš kód, který komunikuje s infrastrukturou, jako jsou databáze a systémy souborů, budete mít stále některé tento kód a budete pravděpodobně chtít otestovat. Kromě toho je třeba ověřit, že váš kód vrstvy pracovat jako můžete očekávat, když aplikace závislosti jsou plně vyřešený. To má na starosti integrace testy. Integrace testů jsou často pomalejší a obtížnější nastavení než testy jednotek, protože často závisí na externí závislosti a infrastrukturu. Proto byste neměli testování věcí, které by mohly být testů pomocí jednotkových testů v testech integrace. Pokud v daném scénáři můžete otestovat s testů jednotek, byste měli otestovat s testování částí. Pokud není, pak zvažte použití test integrace.

Integrace testy bude mít často složitější nastavení a postupy rušením než testování částí. Například test integrace, který prochází skutečné databázi potřebovat způsob, jak databázi do známého stavu před každým testem spustit. Se přidávají nové testy a schématu databáze produkční zpracovaní tyto testovací skripty se zpravidla Čím velikost a složitost. V mnoha velkých systémů je nepraktické spustit úplné sady testů integrace na pracovních stanicích vývojáře před vrácením se změnami změny sdíleného zdrojového kódu. V těchto případech může být spuštěno integrace testy na serveru sestavení.

Třída implementace LocalFileImageService implementuje logiku pro načítání a vrátí počet bajtů souboru bitové kopie z určité složce zadané id:

```cs
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
```

### <a name="functional-tests"></a>Funkčních testů

Integrace testy se zapisují z pohledu vývojáře, chcete-li ověřit správné fungování společně některé součásti systému. Funkční testy se zapisují z pohledu uživatele a ověřte správnost systému na požadavky na jeho základě. Následující výňatek nabízí užitečné analogie postup myslíte o funkčních testů, ve srovnání s testování částí:

> "K vytvoření úklidové je připodobnit mnohokrát vývoj systému. Když tato analogie není poměrně správný, jsme ji rozšířit pro účely vysvětlení rozdílu mezi jednotky a funkčních testů. Testování částí je podobná vytváření inspector, zobrazení úklidové vytváření webu. Zadá se zaměřuje na různých interní systémy úklidové, foundation, vypracování elektrický, domovních instalací a tak dále. Mu zajišťuje (testy), bude fungovat správně a bezpečně, který je splňovat kód vytváření části budovy. Funkčních testů v tomto scénáři jsou obdobou majitele domu návštěvě tohoto webu byly stejné konstrukce. Zadá se předpokládá, že interní systémy budou chovat správně, že vytváření inspector provádí jeho úloh. Majitele domu se zaměřuje na co bude třeba za provozu v této úklidové. Jak vypadá úklidové problémem, jsou různé místnostmi možnost velikost, nemá úklidové podle potřeb dané rodině, jsou windows ve funkčním místo k zachycení sun ráno. Majitele domu provádí funkčních testů na budovy. Má pohledu uživatele. Vytváření inspector provádí testování částí v domácnosti. Má Tvůrce perspektivy."

Zdroj: [testování a funkčních testů jednotek](http://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)

Jsem rádi o tom, že "jako vývojáři, nám nepovedlo dvěma způsoby: využijeme věc nesprávný, nebo využijeme špatného." Testování částí Ujistěte se, že vytváříte právo věc; funkčních testů Ujistěte se, že vytváříte správné věci.

Vzhledem k tomu, že funkčních testů fungovat na úrovni systému, mohou požadovat určitý stupeň automatizace uživatelského rozhraní. Jako integrace testy obvykle pracují s nějaký druh infrastruktury testovací také. Díky tomu je pomalejší a více křehká než testy částí a integrace. Měli byste mít jenom tolik funkčních testů, jak je budete muset být jistý, systém se chovají jako uživatelé očekávají, že.

### <a name="testing-pyramid"></a>Testování pyramidy

Martin Fowler napsali o testování pyramidy, je příkladem se zobrazí v obrázek 9-1.

![](./media/image9-1.png)

Obrázek 9-1 testování pyramidy

Různých úrovní pyramidy a jejich relativní velikosti, představují různé druhy testy a kolik byste měli zapsat pro vaši aplikaci. Jak vidíte, doporučuje se mít velký základ testování částí nepodporuje menší vrstvu integrace testy, i menší vrstva funkční testů. Jednotlivé úrovně by v ideálním případě mít pouze testy v něm, který nelze nyní provést, adekvátní nižší vrstvě. Testování pyramidy mít na paměti, když se pokoušíte rozhodnout, jaký druh test, je nutné pro konkrétní scénář.

### <a name="what-to-test"></a>Co do testu

Častých problémů pro vývojáře, kteří jsou používáním s vytváření automatizovaných testů na blížící se s co chcete otestovat. Je to dobrý výchozí bod k testování podmíněnou logiku. Kdekoli máte metodu s chování, které změny podle podmíněného příkazu (if-else, přepínače, apod), byste měli mít spolu alespoň několik testů, které potvrďte správné chování pro určité podmínky. Pokud má váš kód chybové stavy a je vhodný k zápisu alespoň jeden test pro "radostí cestu" prostřednictvím kód (s žádné chyby) a alespoň jeden test pro "sad cesta" (s chybami nebo netypických výsledky) a ověřte, zda že chování vaší aplikace podle očekávání při krátkodobém chyby. Nakonec pokuste se zaměřit na testování věcí, které může selhat, nikoli zaměřené na metriky jako pokrytí kódu. Obecně je lepší, než je menší, další pokrytí kódu. Zápis několik testů další metody velmi složité a důležitých je však obvykle lepší využití doby, než zápis testů vlastností automaticky právě ke zlepšení testovací metriky pokrytí kódu.

## <a name="organizing-test-projects"></a>Uspořádání projektů testů

Projektů testů můžete uspořádat, ale funguje osvědčené za vás. Je vhodné oddělení testy podle typu (testování částí, integrace testovací) a co se testování (podle projektu podle oboru názvů). Jestli toto rozdělení se skládá ze složek v rámci jednoho testovacího projektu nebo více projektů testování, je rozhodnutí o návrhu. Nejjednodušší je jeden projektu, ale pro rozsáhlých projektů s mnoha testy nebo aby bylo možné snadněji spustit různé sady testů, můžete chtít mít několik různých testovací projekty. Mnoha týmy uspořádat projektů testů založené na projekt, který testování, což pro aplikace s víc než několik projekty může vést k velký počet projektů testování, zejména v případě, že jste stále rozdělení tyto podle druh testů jsou v každém projektu. Přístup ohrožení je tak, aby měl jeden projekt na typ testu na aplikaci, se složkami uvnitř projektů testování označíte projektu (a třída) během testování.

Běžně je k uspořádání projekty aplikací ve složce 'src' a projektů testování aplikace paralelní 'testy' složce. Porovnávání složek řešení můžete vytvořit v sadě Visual Studio, pokud vás užitečné této organizace.

![](./media/image9-2.png)

Obrázek 9-2 testovací organizaci ve vašem řešení

Můžete použít vámi preferované rozhraní test. Rozhraní framework xUnit funguje dobře a co se všemi testy ASP.NET Core a základní EF jsou zapsány v. Můžete přidat xUnit testovacího projektu v sadě Visual Studio pomocí šablony zobrazí obrázek 9-3, nebo z příkazového řádku pomocí nové xunit dotnet.

![](./media/image9-3.png)

Obrázek 9-3 přidat xUnit testovacího projektu v sadě Visual Studio

### <a name="test-naming"></a>Test pojmenování

Testy konzistentní způsobem, by měl název s názvy, které označují, jaké jsou všechny testy. Jeden z přístupů, které došlo skvělé úspěšné dokončení je název třídy testovací podle třídy a metody, kterou budou testování. Výsledkem je mnoho tříd malý test, ale umožňuje velmi vymazat, co je zodpovědná za každý test. Pomocí názvu třídy testovací nastavit tak, aby určovat třídu a metoda má být testována název metody testovací slouží k určení chování testuje. To by mělo zahrnovat očekávané chování a všechny vstupy nebo předpoklady, které by měl yield toto chování. Některé názvy testovací příklad:

-   CatalogControllerGetImage.CallsImageServiceWithId

-   CatalogControllerGetImage.LogsWarningGivenImageMissingException

-   CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess

-   CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException

Varianta tohoto přístupu končí každý název třídy test s "By" a mírně změní slovesného času:

-   CatalogControllerGetImage**by**. **Volání**ImageServiceWithId

-   CatalogControllerGetImage**by**. **Protokol**WarningGivenImageMissingException

Některé týmy najít druhý pojmenování přístup jasnější, ale něco víc verbose. V každém případě zkuste použít zásady vytváření názvů, který poskytuje vhled do testovací chování, takže pokud jeden nebo více testů nezdaří, je zřejmé z jejich názvy, jaké případech se nezdařilo. Nepojmenovávejte můžete testy představu o možných, jako je například ControllerTests.Test1, jak tyto nabízet žádnou hodnotu, při jejich zobrazí ve výsledcích testu.

Pokud budete postupovat podle zásady vytváření názvů jako jeden vyšší vytvoří mnoho tříd malý test, je vhodné dalšího uspořádání testů pomocí složky a oborů názvů. Obrázek 9 – 4 ukazuje jeden ze způsobů, uspořádání testů ve složce v rámci několika projektů testů.

![](./media/image9-4.png)

**Obrázek 9 – 4.** Uspořádání testovací třídy ve složce založeno na třídě testuje.

Samozřejmě pokud třída určitá aplikace má mnoho způsobů testuje (a tedy mnoho testování třídy), může mít smysl umístit tyto ve složce odpovídající třídy aplikace. Tato organizace je nejsou jiné než jak může soubory uspořádat do složek jinde. Pokud máte více než tři nebo čtyři související soubory ve složce obsahující mnoho souborů, je často užitečné přesuňte je do svých vlastních podsložky.

## <a name="unit-testing-aspnet-core-apps"></a>Aplikace ASP.NET Core testování částí

V dobře navrženou aplikaci ASP.NET Core bude se zapouzdřené většina složitost a obchodní logiku v obchodní entity a různých služeb. Aplikace ASP.NET MVC jádra, s řadiči, filtry, viewmodels a zobrazení, měli vyžadovat jen několik testů jednotek. Mnoho funkcí danou akci leží mimo samotné metody akce. Zjišťuje, zda je směrování funguje správně, nebo globální při zpracování chyb nelze provést efektivně pomocí testování částí. Podobně všechny filtry, včetně ověření modelu a ověřování a autorizace filtry, nelze testování jednotky. Bez těchto zdrojů chování musí být trivially malé, delegování hromadným práci na služby, které může být testována nezávislé na řadič, který používá, je většina metody akce.

V některých případech budete muset refactor kódu v pořadí pro testování částí. Často to zahrnuje identifikace abstrakce a využitím vkládání závislostí pro přístup k odběru v kód, který chcete otestovat, nikoli kódování přímo na infrastrukturu. Představte si třeba tato metoda jednoduché akce pro zobrazení obrázků:

```cs
[HttpGet("[controller]/pic/{id}")]
public IActionResult GetImage(int id)
{
    var contentRoot = _env.ContentRootPath + "//Pics";
    var path = Path.Combine(contentRoot, id + ".png");
    Byte[] b = System.IO.File.ReadAllBytes(path);
    return File(b, "image/png");
}
```

Tato metoda testování částí je provedené obtížné je přímé závislá na System.IO.File, který se používá ke čtení systému souborů. Toto chování zajistit funguje podle očekávání, ale to se skutečné soubory se test integrace můžete otestovat. Je vhodné poznamenat trasy tato metoda nemůže otestovat – uvidíte, jak to provést pomocí testu funkční za chvíli.

Pokud nemůžete přímo testování částí chování systému souborů, a nemůže otestovat trasy, co je došlo k testování? Po refaktoring k umožnění testování částí, je dobře, může zjistit některé testovací případy a chybějící chování, jako je například zpracování chyb. Jakým způsobem metodu? Pokud soubor nebyl nalezen. Co je dělat? V tomto příkladu metoda refactored vypadat třeba takto:

```cs
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

\_Protokolovacího nástroje a \_imageService jsou obě vložit jako závislosti. Nyní můžete otestovat předaný stejným id, který je předán do metody akce \_imageService, a že výsledné bajtů jsou vraceny jako součást FileResult. Můžete také otestovat že protokolování chyb probíhá podle očekávání a že NotFound výsledek je vrácena v případě, že chybí bitovou kopii, za předpokladu, že to je důležité aplikace chování (to znamená, právě dočasné kód vývojáře přidat do diagnostikovat problém). Logika skutečný soubor přesunul do samostatné implementace služby a rozšíření, vrátí výjimku specifické pro aplikaci pro případ souboru chybí. Tato implementace můžete otestovat nezávisle, pomocí test integrace.

## <a name="integration-testing-aspnet-core-apps"></a>Integrace aplikace ASP.NET Core testování

```cs
    }
        catch (FileNotFoundException ex)
        {
            throw new CatalogImageMissingException(ex);
        }
    }
}
```

Tato služba používá IHostingEnvironment, stejně jako CatalogController kódu se předtím, než je teď vyčleněný do samostatné služby. Protože se jedná pouze kód v kontroleru, který používá IHostingEnvironment, že závislostí je odebraný z na CatalogController konstruktor.

Pokud chcete otestovat, že tato služba funguje správně, musíte vytvořit soubor image známé test a ověřte, zda služba vrací je zadána specifický vstup. Měli postará nepoužívat mock objektů na chování, které chcete ve skutečnosti testovat (v tomto případě čtení ze systému souborů). Však mock objektů může být stále užitečná k nastavení integrace testy. V takovém případě můžete model IHostingEnvironment, tak, aby jeho ContentRootPath ukazuje na složku, kterou se chystáte použít pro vaše testovací bitovou kopii. Dokončení třídy testovací integrace pracovní je znázorněno zde:

```cs
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
> že sama je velmi jednoduchý – hromadné kódu je nutné konfigurovat systém a vytvářet testování infrastrukturu (v tomto případě skutečný soubor čtení z disku). Toto je typické pro integraci testy, které často vyžadují složitější nastavení než testování částí.

## <a name="functional-testing-aspnet-core-apps"></a>Funkční testování aplikací ASP.NET Core

Pro aplikace ASP.NET Core třídě TestServer usnadňuje funkčních testů poměrně k zápisu. Nakonfigurujete TestServer, použití WebHostBuilder stejným způsobem jako za normálních okolností pro vaši aplikaci. Tato WebHostBuilder by měl být nakonfigurovaný stejně jako skutečné hostitele vaší aplikace, ale můžete upravit všechny jeho aspektů, které testování usnadnit. Ve většině případů, stejný objekt TestServer pro mnoho testovacích případů budete opakovaně, tak ho může zapouzdřit v opakovaně použitelné metodu (možná v základní třídě):

```cs
public abstract class BaseWebTest
{
    protected readonly HttpClient _client;
    protected string _contentRoot;

    public BaseWebTest()
    {
        _client = GetClient();
    }
    
    protected HttpClient GetClient()
    {
        var startupAssembly = typeof(Startup).GetTypeInfo().Assembly;
        _contentRoot = GetProjectPath("src", startupAssembly);
        var builder = new WebHostBuilder()
        .UseContentRoot(_contentRoot)
        .UseStartup&lt;Startup&gt;();
        var server = new TestServer(builder);
        var client = server.CreateClient();
        return client;
    }
}
```

GetProjectPath – metoda jednoduše vrátí fyzickou cestu k webovému projektu (stažení ukázkové řešení). WebHostBuilder v tomto případě jednoduše Určuje, kde je kořenu obsahu pro webovou aplikaci a odkazuje na stejný třída při spuštění, které skutečné webová aplikace používá. Pro práci s TestServer, používat standardní typ System.Net.HttpClient provádět požadavky na ni. Objekt TestServer zpřístupní užitečné CreateClient metodu, která obsahuje předem nakonfigurovaná klienta, který je připraven k provedení požadavků v aplikaci objekt TestServer a systémem. Pomocí tohoto klienta (nastavit do chráněného \_člen klienta na základní test výše) při zápisu funkčních testů pro aplikace ASP.NET Core:

```cs
public class CatalogControllerGetImage : BaseWebTest
{
    [Fact]
    public async Task ReturnsFileContentResultGivenValidId()
    {
        var testFilePath = Path.Combine(_contentRoot, "pics//1.png");
        var expectedFileBytes = File.ReadAllBytes(testFilePath);
        var response = await _client.GetAsync("/catalog/pic/1");
        response.EnsureSuccessStatusCode();
        var streamResponse = await response.Content.ReadAsStreamAsync();
        byte[] byteResult;
        using (var ms = new MemoryStream())
        {
            streamResponse.CopyTo(ms);
            byteResult = ms.ToArray();
        }
        Assert.Equal(expectedFileBytes, byteResult);
    }
}
```

Tento test funkční vykonává úplné zásobník aplikací ASP.NET MVC jádra, včetně všech middleware, filtry, vazače, atd., které může být na místě. Ověřuje, že danou trasu ("/ katalogu/pic/1) vrátí očekávané bajtové pole pro soubor do vhodného umístění. Nebude tak bez nastavování skutečné webový server a proto zabraňuje většinu brittleness, který používá skutečné webového serveru pro testování můžete zaznamenat (například problémy s nastavením brány firewall). Funkčních testů, které spouštění TestServer jsou obvykle nižší než integrace a testování částí, ale je mnohem rychlejší než testy, které by spustit v síti k serveru webového testu.

>[!div class="step-by-step"]
[Předchozí] (work-with-data-in-asp-net-core-apps.md) [Další] (development-process-for-azure.md)
