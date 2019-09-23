---
title: Vývoj aplikací ASP.NET Core MVC
description: Architekt moderních webových aplikací pomocí ASP.NET Core a Azure | vývoj aplikací ASP.NET Core MVC
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 19d1d5f81b5be9b843698b6e61d8571d4edfa66f
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181949"
---
# <a name="develop-aspnet-core-mvc-apps"></a>Vývoj aplikací ASP.NET Core MVC

> "Není důležité si ho poprvé napravit. Je důležité, abyste si ho v poslední době získali hned. "  
> _– Andrew loven a David Tomáš_

ASP.NET Core je open source platforma pro různé platformy pro vytváření moderních cloudových webových aplikací. Aplikace ASP.NET Core jsou odlehčené a modulární s integrovanou podporou pro vkládání závislostí a umožňují větší možnosti testování a udržovatelnosti. V kombinaci se službou MVC, která kromě aplikací založených na zobrazení podporuje vytváření moderních webových rozhraní API, ASP.NET Core představuje výkonnou architekturu pro vytváření podnikových webových aplikací.

## <a name="mvc-and-razor-pages"></a>MVC a Razor Pages

ASP.NET Core MVC nabízí mnoho funkcí, které jsou užitečné při vytváření webových rozhraní API a aplikací. Termín MVC představuje "Model-View-Controller", vzorek uživatelského rozhraní, který rozdělí zodpovědnosti na požadavky uživatelů na několik částí. Kromě tohoto vzoru můžete ve svých aplikacích pro ASP.NET Core taky implementovat funkce jako Razor Pages. Razor Pages jsou integrované do ASP.NET Core MVC a používají stejné funkce pro směrování, vázání modelů atd. Místo toho, aby byly samostatné složky a soubory pro řadiče, zobrazení atd. a používaly směrování založené na atributech, Razor Pages jsou umístěny do jediné složky ("/Pages"), směrovat na základě jejich relativního umístění v této složce a zpracovávat požadavky pomocí obslužných rutin. namísto akcí kontroleru.

Když vytváříte novou aplikaci ASP.NET Core, měli byste mít na paměti, že máte na mysli druh aplikace, kterou chcete sestavit. V aplikaci Visual Studio si zvolíte z několika šablon. Tři nejběžnější šablony projektu jsou webové rozhraní API, Webová aplikace a webová aplikace (Model-View-Controller). I když můžete toto rozhodnutí udělat pouze při prvním vytvoření projektu, není to neodvolatelné rozhodnutí. Projekt webového rozhraní API používá standardní řadiče pro zobrazení modelu, ale ve výchozím nastavení jen postrádá zobrazení. Stejně tak výchozí šablona webové aplikace používá Razor Pages, a tak také nemá složku zobrazení. Do těchto projektů můžete přidat složku zobrazení později, aby se podporovalo chování na základě zobrazení. Projekty webového rozhraní API a Model-View-Controller ve výchozím nastavení neobsahují složku Pages, ale můžete ji přidat později, aby se podporovalo chování založené na Razor Pages. Tyto tři šablony si můžete představit jako podpora tří různých druhů výchozích zásahů uživatele: data (webové rozhraní API), na stránce a na základě zobrazení. V případě potřeby však můžete v rámci jednoho projektu kombinovat a porovnat libovolné nebo všechny z nich.

### <a name="why-razor-pages"></a>Proč Razor Pages?

Razor Pages je výchozím přístupem pro nové webové aplikace v aplikaci Visual Studio. Razor Pages nabízí jednodušší způsob, jak sestavovat funkce aplikace založené na stránkách, jako jsou například formuláře bez hesla. Pomocí řadičů a zobrazení je běžné, že aplikace mají velmi velké řadiče, které pracovaly s mnoha různými závislostmi a zobrazují modely a vracejí mnoho různých zobrazení. To vedlo hodně složitosti a často to vedlo k tomu, že řadiče, které nesledovaly princip jedné zodpovědnosti nebo jsou efektivně otevřené/uzavřené zásady. Tento problém Razor Pages řeší zapouzdřením logiky na straně serveru pro danou logickou "stránku" v rámci webové aplikace pomocí značek Razor. Stránka Razor, která nemá žádnou logiku na straně serveru, může jednoduše sestávat ze souboru Razor (např. index. cshtml). Avšak většina netriviálních Razor Pages bude mít přidruženou třídu modelu stránky, která je podle konvence pojmenována stejně jako soubor Razor s příponou ". cs" (například "Index.cshtml.cs").

Model stránky stránky Razor kombinuje zodpovědnosti kontroleru MVC a ViewModel. Místo zpracování žádostí s metodami akce kontroleru se spustí obslužné rutiny modelu stránky, jako je například "OnGet ()", vykreslení jejich přidružené stránky ve výchozím nastavení. Razor Pages zjednodušuje proces sestavování jednotlivých stránek v aplikaci ASP.NET Core a zároveň stále poskytuje všechny funkce architektury služby ASP.NET Core MVC. Jsou to dobrá výchozí volba pro nové funkce založené na stránkách.

### <a name="when-to-use-mvc"></a>Kdy použít MVC

Pokud vytváříte webová rozhraní API, vzor MVC je větší, než se snažíte použít Razor Pages. Pokud váš projekt zveřejňuje koncové body webového rozhraní API, měli byste v ideálním případě začít od šablony projektu webového rozhraní API, ale v opačném případě je snadné přidat řadiče a přidružené koncové body rozhraní API do libovolné ASP.NET Core aplikace. Přístup na základě zobrazení MVC byste měli použít také v případě, že migrujete existující aplikaci z ASP.NET MVC 5 nebo starší na ASP.NET Core MVC a chcete tak učinit s minimálním úsilím. Po provedení prvotní migrace můžete vyhodnotit, jestli má smysl přijmout Razor Pages pro nové funkce nebo dokonce i jako migraci ve velkoobchodu.

Bez ohledu na to, jestli se rozhodnete vytvořit webovou aplikaci pomocí Razor Pages nebo zobrazení MVC, bude mít aplikace podobný výkon a bude zahrnovat podporu pro vkládání závislostí, filtry, vazbu a ověřování v modelu atd.

## <a name="mapping-requests-to-responses"></a>Mapování požadavků na odpovědi

Ve své srdci ASP.NET Core aplikace mapují příchozí požadavky na odchozí odpovědi. Na nízké úrovni se to dělá s middlewarem a jednoduché ASP.NET Core aplikace a mikroslužby můžou být tvořeny výhradně vlastním middlewarem. Při použití ASP.NET Core MVC můžete pracovat na trochu vyšší úrovni, což je v souladu s _trasami_, _řadiči_a _akcemi_. Každý příchozí požadavek je porovnán s tabulkou směrování aplikace a pokud je nalezena odpovídající trasa, je pro zpracování žádosti volána přidružená metoda akce (patří k řadiči). Pokud není nalezena žádná vyhovující trasa, je volána obslužná rutina chyby (v tomto případě vrátí výsledek NotFound).

Aplikace ASP.NET Core MVC můžou používat konvenční trasy, trasy atributů nebo obojí. Konvenční trasy jsou definovány v kódu a určují _konvence_ směrování pomocí syntaxe jako v následujícím příkladu:

```csharp
app.UseMvc(routes =>
{
    routes.MapRoute("default","{controller=Home}/{action=Index}/{id?}");
});
```

V tomto příkladu byla do směrovací tabulky přidána trasa s názvem "default". Definuje šablonu směrování se zástupnými symboly pro _kontroler_, _Akce_a _ID_. Zástupné symboly kontroleru a akce mají nastavené výchozí hodnoty ("Home" a "index") a zástupný symbol ID je nepovinný (na základě použití "?"). Zde definovaná konvence uvádí, že první část požadavku by měla odpovídat názvu kontroleru, druhé části akce a v případě, že je potřeba třetí část, bude představovat parametr ID. Konvenční trasy jsou obvykle definovány na jednom místě pro aplikaci, například v metodě Configure ve třídě Startup.

Trasy atributů jsou aplikovány přímo na řadiče a akce namísto zadání globálně. To má výhodu, že je mnohem více zjistitelná, když se díváte na konkrétní metodu, ale znamená, že informace o směrování nejsou uchovávány na jednom místě v aplikaci. Pomocí tras atributů můžete snadno zadat více tras pro danou akci a kombinovat trasy mezi řadiči a akcemi. Příklad:

```csharp
[Route("Home")]
public class HomeController : Controller
{
    [Route("")] // Combines to define the route template "Home"
    [Route("Index")] // Combines to define route template "Home/Index"
    [Route("/")] // Does not combine, defines the route template ""
    public IActionResult Index() {}
}
```

Trasy lze zadat na [HttpGet] a podobných atributech a vyhnout se nutnosti přidávat samostatné atributy [Route]. Trasy atributů můžou také používat tokeny k omezení nutnosti opakovat názvy kontroléru nebo akce, jak je znázorněno níže:

```csharp
[Route("[controller]")]
public class ProductsController : Controller
{
    [Route("")] // Matches 'Products'
    [Route("Index")] // Matches 'Products/Index'
    public IActionResult Index() {}
}
```

Razor Pages nepoužívá směrování atributů. V rámci své `@page` směrnice můžete zadat další informace o šabloně směrování pro stránku Razor:

```csharp
@page "{id:int}"
```

V předchozím příkladu by se stránka měla shodovat s parametrem typu Integer `id` . Například stránka *Products. cshtml* , která se nachází v kořenovém adresáři `/Pages` , by měla tuto trasu:

```csharp
"/Products/123"
```

Po porovnání dané žádosti s trasou, ale před zavoláním metody Action, ASP.NET Core MVC provede [vazbu modelu](/aspnet/core/mvc/models/model-binding) a [ověření modelu](/aspnet/core/mvc/models/validation) na žádosti. Vazba modelu zodpovídá za převod příchozích dat HTTP do typů .NET určených jako parametrů metody akce, která má být volána. Například pokud metoda Action očekává parametr ID int, vazba modelu se pokusí tento parametr poskytnout z hodnoty zadané v rámci žádosti. V takovém případě vazba modelu vyhledá hodnoty v zaúčtovaném formuláři, hodnotách v samotné trase a hodnotách řetězce dotazu. Za předpokladu, že je hodnota ID nalezena, bude převedena na celé číslo před předáním do metody Action.

Po vytvoření vazby modelu, ale před voláním metody Action, dojde k ověření modelu. Ověřování modelu používá volitelné atributy pro typ modelu a může zajistit, aby zadaný objekt modelu splňoval určité požadavky na data. Některé hodnoty mohou být zadány jako povinné nebo omezené na určitou délku nebo číselný rozsah atd. Pokud jsou zadány atributy ověřování, ale model nevyhovuje jejich požadavkům, vlastnost ModelState. IsValid bude false a sada neúspěšných ověřovacích pravidel bude k dispozici pro odeslání klientovi, který vytváří požadavek.

Pokud používáte ověřování modelu, měli byste před provedením jakýchkoli příkazů pro změnu stavu zkontrolovat, jestli je model platný, abyste zajistili, že vaše aplikace nebude poškozená pomocí neplatných dat. [Filtr](/aspnet/core/mvc/controllers/filters) můžete použít k tomu, abyste se vyhnuli nutnosti přidat kód pro toto v každé akci. ASP.NET Core filtry MVC nabízí způsob, jak zachytit skupiny požadavků, aby bylo možné použít společné zásady a vzájemné navýšení obav na základě cíle. Filtry lze použít pro jednotlivé akce, pro všechny řadiče nebo pro globálně pro aplikaci.

Pro webová rozhraní API ASP.NET Core MVC podporuje [_vyjednávání obsahu_](/aspnet/core/mvc/models/formatting)a umožňuje žádostem určit, jak mají být odpovědi naformátovány. V závislosti na hlavičkách poskytnutých v žádosti naformátují akce vracející data odpověď ve formátu XML, JSON nebo v jiném podporovaném formátu. Tato funkce umožňuje používat stejné rozhraní API pro více klientů s různými požadavky na formát dat.

Projekty webového rozhraní API by měly uvažovat `[ApiController]` o použití atributu, který lze použít na jednotlivé řadiče, na základní třídu kontroleru nebo na celé sestavení. Tento atribut přidá automatickou kontrolu ověřování modelu a všechny akce s neplatným modelem vrátí důvodu chybného požadavku s podrobnostmi o chybách ověřování. Atribut také vyžaduje, aby všechny akce měly trasu atributu, nikoli použití konvenční trasy, a v reakci na chyby vrátí podrobnější informace ProblemDetails.

> ### <a name="references--mapping-requests-to-responses"></a>Odkazy – mapování požadavků na odpovědi
>
> - **Směrování na akce kontroleru**
 > <https://docs.microsoft.com/aspnet/core/mvc/controllers/routing>
> - **Vazba modelu**
 > <https://docs.microsoft.com/aspnet/core/mvc/models/model-binding>
> - **Ověření modelu**
 > <https://docs.microsoft.com/aspnet/core/mvc/models/validation>
> - **Outlook**
 > <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - **ApiController – atribut**
 > <https://docs.microsoft.com/aspnet/core/web-api/>

## <a name="working-with-dependencies"></a>Práce se závislostmi

ASP.NET Core má integrovanou podporu pro a interně využívá techniku známou jako [vkládání závislostí](/aspnet/core/fundamentals/dependency-injection). Injektáže závislostí je technika, která umožňuje volné spojení mezi různými částmi aplikace. Volné spojení je žádoucí, protože usnadňuje izolaci částí aplikace a umožňuje jejich testování nebo nahrazení. Tím je také méně pravděpodobný, že změna v jedné části aplikace bude mít neočekávaný dopad někde jinde v aplikaci. Vstřik závislosti je založen na principu inverze závislosti a často se jedná o klíč k dosažení principu otevření/uzavření. Při vyhodnocování, jak vaše aplikace pracuje s jejími závislostmi, si popamatujete pach kódu [statického cling](https://deviq.com/static-cling/) a zapamatujte si, že aphorism "[nové je připevnit](https://ardalis.com/new-is-glue)".

Ke statickému cling dochází, když vaše třídy volají volání statických metod, nebo mají přístup ke statickým vlastnostem, které mají vedlejší účinky nebo závislosti na infrastruktuře. Například pokud máte metodu, která volá statickou metodu, která zase zapisuje do databáze, vaše metoda je pevně spojena s databází. Cokoli, co toto volání databáze přeruší, bude vaše metoda rušit. Testování takových metod je obvykle odlaďuje obtížné, protože tyto testy buď vyžadují komerční napodobné knihovny pro napodobení statických volání, nebo je lze testovat pouze pomocí testovací databáze na místě. Statická volání, která nemají žádnou závislost na infrastruktuře, zejména ta, která jsou zcela Bezstavová, jsou schopná volat a nemají žádný vliv na spojku ani možnosti testování (mimo spojovací kód pro samotný statický hovor).

Mnoho vývojářů rozumí rizikům statických cling a globálních stavů, ale stále úzce přiděluje svůj kód na konkrétní implementace prostřednictvím přímé instance. "Nové je připevnit", aby bylo připomenutí tohoto spoje, a ne obecné condemnation použití `new` klíčového slova. Stejně jako u volání statických metod nové instance typů, které nemají žádné externí závislosti, obvykle nezpůsobí pevnění kódu k implementačním podrobnostem nebo provádění testování obtížnější. Ale pokaždé, když je vytvořena instance třídy, posuzuje, zda má smysl na pevný kód konkrétní instance v daném umístění, nebo v případě, že by byl lepším návrhem pro vyžádání této instance jako závislosti.

### <a name="declare-your-dependencies"></a>Deklarovat závislosti

ASP.NET Core je sestaven s ohledem na to, že metody a třídy deklaruje jejich závislosti, a požaduje je jako argumenty. Aplikace ASP.NET jsou obvykle nastavené ve spouštěcí třídě, která je nakonfigurovaná tak, aby podporovala vkládání závislostí na několika místech. Pokud má vaše spouštěcí třída konstruktor, může vyžádat závislosti prostřednictvím konstruktoru, například takto:

```csharp
public class Startup
{
    public Startup(IHostingEnvironment env)
    {
        var builder = new ConfigurationBuilder()
        .SetBasePath(env.ContentRootPath)
        .AddJsonFile("appsettings.json", optional: false, reloadOnChange: true)
        .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true);
    }
}
```

Spouštěcí třída je zajímavá v tom, že pro ni nejsou k dispozici žádné explicitní požadavky typu. Nedědí ze speciální spouštěcí základní třídy ani neimplementuje žádné konkrétní rozhraní. Můžete mu udělit konstruktor nebo ne a můžete zadat tolik parametrů v konstruktoru, jak chcete. Po spuštění webového hostitele, který jste nakonfigurovali pro vaši aplikaci, bude volat spouštěcí třídu, kterou jste si dozvěděli, že se má použít, a pomocí injektáže závislosti vyplníte všechny závislosti, které spouštěcí třída vyžaduje. Samozřejmě, pokud požadujete parametry, které nejsou nakonfigurované v kontejneru Services používaném ASP.NET Core, získáte výjimku, ale pokud budete chtít, aby se na závislosti kontejneru ví, můžete si vyžádat cokoli, co potřebujete.

Vkládání závislostí je v aplikacích ASP.NET Core přímo od spuštění, když vytváříte instanci spouštění. Neukončí třídu pro spuštění. V metodě konfigurace můžete také vyžádat závislosti:

```csharp
public void Configure(IApplicationBuilder app,
    IHostingEnvironment env,
    ILoggerFactory loggerFactory)
{

}
```

Metoda ConfigureServices je výjimkou tohoto chování; musí mít pouze jeden parametr typu IServiceCollection. Ve skutečnosti nemusí podporovat vkládání závislostí, protože na jedné straně zodpovídá za přidání objektů do kontejneru služeb a na druhé má přístup ke všem aktuálně nakonfigurovaným službám prostřednictvím parametru IServiceCollection. Proto můžete pracovat se závislostmi definovanými v kolekci ASP.NET Core Services v každé části třídy po spuštění, a to tak, že požadujete potřebnou službu jako parametr nebo při práci s IServiceCollection v ConfigureServices.

> [!NOTE]
> Pokud potřebujete zajistit, aby byly určité služby k dispozici pro třídu spuštění, můžete je nakonfigurovat pomocí WebHostBuilder a její metody ConfigureServices.

Spouštěcí třída je modelem, jak byste měli strukturovat ostatní části aplikace ASP.NET Core, od řadičů po middlewaru až po filtrování na vaše vlastní služby. V každém případě byste měli postupovat podle [principu explicitních závislostí](https://deviq.com/explicit-dependencies-principle/), vyžádat si své závislosti namísto jejich přímého vytváření a využití injektáže závislostí v celé aplikaci. Buďte opatrní, kde a jak přímo vytvářet instance implementací, zejména služeb a objektů, které pracují s infrastrukturou nebo mají vedlejší účinky. Preferovat práci s abstrakcemi definovanými v jádru vaší aplikace a předanými jako argumenty pro zakódujeme odkazů na konkrétní typy implementace.

## <a name="structuring-the-application"></a>Strukturování aplikace

Monolitické aplikace mají typicky jeden vstupní bod. V případě ASP.NET Core webové aplikace bude vstupním bodem ASP.NET Core webový projekt. To však neznamená, že by se mělo řešení sestávat pouze z jednoho projektu. Je vhodné rozdělit aplikaci do různých vrstev, aby bylo možné postupovat podle oddělení obav. Po rozčlenění do vrstev je vhodné přecházet mimo složky pro samostatné projekty, což může pomoct dosáhnout lepšího zapouzdření. Nejlepším způsobem, jak dosáhnout těchto cílů pomocí ASP.NET Core aplikace, je variace čisté architektury popsané v kapitole 5. Po tomto přístupu se řešení aplikace skládá z samostatných knihoven pro uživatelské rozhraní, infrastrukturu a ApplicationCore.

Kromě těchto projektů jsou zahrnuty také samostatné testovací projekty (testování je popsáno v kapitole 9).

Objektový model a rozhraní aplikace by měly být umístěny do projektu ApplicationCore. Tento projekt bude mít co nejmenší závislosti a ostatní projekty v řešení na něj budou odkazovat. Obchodní entity, které je nutné zachovat, jsou definovány v projektu ApplicationCore, stejně jako služby, které nejsou přímo závislé na infrastruktuře.

Podrobnosti implementace, například jak probíhá trvalá trvalost nebo jak mohou být oznámení odeslána uživateli, jsou uchovávány v projektu infrastruktury. Tento projekt bude odkazovat na balíčky specifické pro implementaci, jako je například Entity Framework Core, ale neměly by zveřejňovat podrobnosti o těchto implementacích mimo projekt. Služby infrastruktury a úložiště by měly implementovat rozhraní, která jsou definovaná v projektu ApplicationCore, a jeho implementace trvalosti zodpovídá za načítání a ukládání entit definovaných v ApplicationCore.

Projekt ASP.NET Core uživatelského rozhraní zodpovídá za všechny aspekty na úrovni uživatelského rozhraní, ale nemělo by obsahovat podrobnosti obchodní logiky nebo infrastruktury. V ideálním případě by neměl být v ideálním případě závislý na projektu infrastruktury, což vám pomůže zajistit, že nedojde k náhodnému zavedení žádné závislosti mezi těmito dvěma projekty. Toho lze dosáhnout pomocí kontejneru DI třetí strany, jako je Autofac, což umožňuje definovat pravidla DI v třídách modulů v každém projektu.

Dalším způsobem, jak odložení aplikace z podrobností implementace, je mít aplikace volající mikroslužby, případně nasazené v jednotlivých kontejnerech Docker. To poskytuje ještě větší oddělení obav a odpojuje se od využití DI mezi dvěma projekty, ale má další složitost.

### <a name="feature-organization"></a>Organizace funkcí

Ve výchozím nastavení ASP.NET Core aplikace uspořádat svoji strukturu složek tak, aby zahrnovala řadiče a zobrazení a často ViewModels. Kód na straně klienta pro podporu těchto struktur na straně serveru je obvykle uložen samostatně ve složce Wwwroot. Velké aplikace ale můžou narazit na problémy s touto organizací, protože práce na určité funkci často vyžaduje přechod mezi těmito složkami. To znamená více a obtížnější, protože počet souborů a podsložek v každé složce roste a výsledkem je skvělé rolování prostřednictvím Průzkumník řešení. Jedním z řešení tohoto problému je organizovat kód aplikace podle _funkcí_ , nikoli podle typu souboru. Tento styl organizace se obvykle označuje jako složky funkcí nebo [řezy funkcí](https://msdn.microsoft.com/magazine/mt763233.aspx) (viz také: [Svislé řezy](https://deviq.com/vertical-slices/)).

ASP.NET Core MVC podporuje oblasti pro tento účel. Pomocí oblastí můžete vytvořit samostatné sady řadičů a složek zobrazení (stejně jako všechny přidružené modely) v každé složce oblasti. Obrázek 7-1 ukazuje příklad struktury složek s použitím oblastí.

![Ukázková organizace oblastí](./media/image7-1.png)

**Obrázek 7-1**. Ukázková organizace oblastí

Při použití oblastí je nutné použít atributy k seupravování řadičů s názvem oblasti, do které patří:

```csharp
[Area("Catalog")]
public class HomeController
{}
```

Také je potřeba přidat do svých tras podporu oblastí:

```csharp
app.UseMvc(routes =>
{
    // Areas support
    routes.MapRoute(
    name: "areaRoute",
    template: "{area:exists}/{controller=Home}/{action=Index}/{id?}");
    routes.MapRoute(
    name: "default",
    template: "{controller=Home}/{action=Index}/{id?}");
});
```

Kromě integrované podpory pro oblasti můžete také použít vlastní strukturu složek a konvence namísto atributů a vlastních tras. To vám umožní mít složky funkcí, které neobsahovaly samostatné složky pro zobrazení, řadiče atd., udržovat hierarchii plošší a zjednodušit zobrazení všech souvisejících souborů na jednom místě pro jednotlivé funkce.

ASP.NET Core používá k řízení jeho chování předdefinované typy konvencí. Tyto konvence můžete upravit nebo nahradit. Můžete například vytvořit konvenci, která automaticky získá název funkce pro daný řadič na základě jeho oboru názvů (který obvykle koreluje se složkou, ve které je kontroler umístěný):

```csharp
public class FeatureConvention : IControllerModelConvention
{
    public void Apply(ControllerModel controller)
    {
        controller.Properties.Add("feature",
        GetFeatureName(controller.ControllerType));
    }

    private string GetFeatureName(TypeInfo controllerType)
    {
        string[] tokens = controllerType.FullName.Split('.');
        if (!tokens.Any(t => t == "Features")) return "";
        string featureName = tokens
        .SkipWhile(t => !t.Equals("features",
        StringComparison.CurrentCultureIgnoreCase))
        .Skip(1)
        .Take(1)
        .FirstOrDefault();
        return featureName;
    }
}
```

Tuto konvenci pak zadáte jako možnost při přidávání podpory pro MVC do aplikace v ConfigureServices:

```csharp
services.AddMvc(o => o.Conventions.Add(new FeatureConvention()));
```

ASP.NET Core MVC také používá konvenci k vyhledání zobrazení. Můžete ho přepsat vlastní konvencí, aby se zobrazily ve složkách funkcí (pomocí názvu funkce poskytnutého FeatureConvention, výše). Další informace o tomto přístupu a stažení Pracovní ukázky najdete v článku na webu MSDN, [řezy funkcí pro ASP.NET Core MVC](https://msdn.microsoft.com/magazine/mt763233.aspx).

### <a name="cross-cutting-concerns"></a>Otázky pro průřezy

Jak aplikace roste, je stále důležitější, aby bylo možné vyloučit duplicity a zachovat konzistenci. Mezi důležité aspekty průřezů v ASP.NET Core aplikacemi patří ověřování, pravidla ověřování modelů, ukládání výstupu do mezipaměti a zpracování chyb, i když existuje mnoho dalších. ASP.NET Core [filtry](/aspnet/core/mvc/controllers/filters) MVC umožňují spustit kód před nebo za některými kroky v kanálu zpracování požadavků. Filtr může například běžet před a po vazbě modelu, před a po akci, nebo před a po výsledku akce. Pomocí autorizačního filtru můžete také řídit přístup ke zbytku kanálu. Obrázky 7-2 ukazují, jak provádění požadavků prostřednictvím filtrů, pokud je nakonfigurováno.

![Požadavek se zpracovává pomocí autorizačních filtrů, filtrů prostředků, vazeb modelů, filtrů akcí, provádění akcí a konverze výsledků akcí, filtrů výjimek, výsledných filtrů a provádění výsledků. Na cestě je požadavek zpracován pouze pomocí filtrů výsledků a filtrů prostředků před tím, než se stane odpověď odeslanou klientovi.](./media/image7-2.png)

**Obrázek 7-2**. Vyžádá provádění prostřednictvím filtrů a kanálu požadavků.

Filtry se obvykle implementují jako atributy, takže je můžete aplikovat na řadiče nebo akce (nebo i globálně). Při přidání tímto způsobem filtry zadané na úrovni akce přepisují nebo sestavují na filtrech zadaných na úrovni řadiče, které samy o nich přepíšou globální filtry. Například \[atribut Route\] lze použít k sestavení tras mezi řadiči a akcemi. Podobně je možné konfigurovat autorizaci na úrovni řadiče a pak je přepsat jednotlivými akcemi, jak ukazuje následující příklad:

```csharp
[Authorize]
public class AccountController : Controller

{
    [AllowAnonymous] // overrides the Authorize attribute
    public async Task<IActionResult> Login() {}
    public async Task<IActionResult> ForgotPassword() {}
}
```

První metoda přihlašování používá filtr AllowAnonymous (atribut) k přepsání autorizačního filtru nastaveného na úrovni řadiče. Akce ForgotPassword (a jakákoli jiná akce ve třídě, která nemá atribut AllowAnonymous), bude vyžadovat ověřený požadavek.

Filtry se dají použít k odstranění duplicit ve formě běžných zásad zpracování chyb pro rozhraní API. Například Typická zásada rozhraní API je vrátit odpověď NotFound na požadavky odkazující na klíče, které neexistují, a odpověď důvodu chybného požadavku, pokud se ověřování modelu nepovede. Následující příklad znázorňuje tyto dvě zásady v akci:

```csharp
[HttpPut("{id}")]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    if ((await _authorRepository.ListAsync()).All(a => a.Id != id))
    {
        return NotFound(id);
    }
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }
    author.Id = id;
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

Nepovolujte, aby vaše metody akcí byly nepotřebné s podmíněným kódem. Místo toho tyto zásady vyžádejte do filtrů, které se dají použít podle potřeby. V tomto příkladu se kontrola ověření modelu, ke kterému by mělo dojít při každém odeslání příkazu do rozhraní API, může nahradit následující atribut:

```csharp
public class ValidateModelAttribute : ActionFilterAttribute
{
    public override void OnActionExecuting(ActionExecutingContext context)
    {
        if (!context.ModelState.IsValid)
        {
            context.Result = new BadRequestObjectResult(context.ModelState);
        }
    }
}
```

`ValidateModelAttribute` Do projektu můžete přidat jako závislost NuGet zahrnutím balíčku [Ardalis. ValidateModel](https://www.nuget.org/packages/Ardalis.ValidateModel) . Pro rozhraní API můžete použít `ApiController` atribut k vykonání tohoto chování bez nutnosti samostatného `ValidateModel` filtru.

Podobně lze použít filtr ke kontrole, zda záznam existuje a vrátí 404 před provedením akce, a eliminuje nutnost provádět tyto kontroly v akci. Po vyzkoušení běžných konvencí a jejich uspořádání do samostatného kódu infrastruktury a obchodní logiky z uživatelského rozhraní by vaše metody akce MVC měly být extrémně tenké:

```csharp
[HttpPut("{id}")]
[ValidateAuthorExists]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

Můžete si přečíst další informace o implementaci filtrů a stažení Pracovní ukázky z článku na webu MSDN [– reálné ASP.NET Core filtry MVC](https://msdn.microsoft.com/magazine/mt767699.aspx).

> ### <a name="references--structuring-applications"></a>Odkazy – strukturování aplikací
>
> - **Oblasti**  
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/areas>
> - **MSDN Magazine – řezy funkcí pro ASP.NET Core MVC**  
>   <https://msdn.microsoft.com/magazine/mt763233.aspx>
> - **Filtry**  
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - **MSDN – Real World ASP.NET Core filtry MVC**  
>   <https://msdn.microsoft.com/magazine/mt767699.aspx>

## <a name="security"></a>Zabezpečení

Zabezpečení webových aplikací je velké téma s mnoha důležitými informacemi. Ve své základní úrovni zabezpečení zahrnuje jistotu, že víte, komu daný požadavek pochází, a potom zajistěte, aby žádost měla přístup jenom k prostředkům, které by měl mít. Ověřování je proces porovnávání přihlašovacích údajů dodaných s žádostí v důvěryhodném úložišti dat, aby bylo možné zjistit, jestli by se žádost měla považovat za přicházející ze známé entity. Autorizace je proces omezení přístupu k určitým prostředkům na základě identity uživatele. Třetí problém se zabezpečením chrání žádosti před odposloucháváním třetími stranami, pro které byste měli aspoň [zajistit, aby vaše aplikace používala SSL](/aspnet/core/security/enforcing-ssl).

### <a name="authentication"></a>Ověřování

ASP.NET Core identitou je systém členství, který můžete použít k podpoře funkcí přihlášení k vaší aplikaci. Nabízí podporu místních uživatelských účtů a také podporu externího poskytovatele přihlášení od poskytovatelů, jako je například účet Microsoft, Twitter, Facebook, Google a další. Kromě ASP.NET Core identity může vaše aplikace používat ověřování systému Windows nebo poskytovatele identity jiného výrobce jako [Server identit](https://github.com/IdentityServer/IdentityServer4).

Pokud je vybrána možnost jednotlivé uživatelské účty, je ASP.NET Core identita obsažena v nových šablonách projektů. Tato šablona zahrnuje podporu pro registraci, přihlášení, externí přihlášení, zapomenutá hesla a další funkce.

![Vyberte jednotlivé uživatelské účty, pro které má být předem nakonfigurovaná identita.](./media/image7-3.png)

**Obrázek 7-3**. Vyberte jednotlivé uživatelské účty, pro které má být předem nakonfigurovaná identita.

Podpora identit je nakonfigurována při spuštění, v ConfigureServices i v konfiguraci:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // Add framework services.
    services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
    .AddEntityFrameworkStores<ApplicationDbContext>()
    .AddDefaultTokenProviders();
    services.AddMvc();
}

public void Configure(IApplicationBuilder app)
{
    app.UseStaticFiles();
    app.UseIdentity();
    app.UseMvc(routes =>
    {
        routes.MapRoute(
        name: "default",
        template: "{controller=Home}/{action=Index}/{id?}");
    });
}
```

Je důležité, aby se UseIdentity zobrazoval před UseMvc v metodě configure. Při konfiguraci identity v ConfigureServices si všimněte volání AddDefaultTokenProviders. To nemá nic dělat s tokeny, které se dají použít k zabezpečení webové komunikace, ale odkazuje na poskytovatele, kteří vytvoří výzvy, které se dají uživatelům poslat přes SMS, nebo e-mailem, aby mohli potvrdit jejich identitu.

Můžete si přečíst další informace o [konfiguraci dvojúrovňové ověřování](/aspnet/core/security/authentication/2fa) a [Povolení externích poskytovatelů přihlášení](/aspnet/core/security/authentication/social/) z oficiálních ASP.NET Core dokumentů.

### <a name="authorization"></a>Autorizace

Nejjednodušší způsob autorizace zahrnuje omezení přístupu anonymním uživatelům. Toho lze dosáhnout pouhým použitím \[\] atributu autorizovat na určité řadiče nebo akce. Pokud se používají role, je možné atribut dál rozšířit, aby se omezil přístup k určitým rolím, jak je znázorněno na následujícím obrázku:

```csharp
[Authorize(Roles = "HRManager,Finance")]
public class SalaryController : Controller
{

}
```

V takovém případě budou mít uživatelé patřící do rolí HRManager nebo finance (nebo obojí) přístup k SalaryController. Chcete-li vyžadovat, aby uživatel patřil k více rolím (ne jen jednomu z několika), můžete použít atribut vícekrát a zadat požadovanou roli pokaždé.

Zadání určitých sad rolí jako řetězců v mnoha různých řadičích a akcí může vést k nežádoucímu opakování. Můžete nakonfigurovat autorizační zásady, které zapouzdřují autorizační pravidla, a pak při použití \[\] autorizačního atributu zadat zásady místo jednotlivých rolí:

```csharp
[Authorize(Policy = "CanViewPrivateReport")]
public IActionResult ExecutiveSalaryReport()
{
    return View();
}
```

Pomocí zásad tímto způsobem můžete oddělit druhy akcí, které jsou omezené z konkrétních rolí nebo pravidel, která se na ně vztahují. Pokud později vytvoříte novou roli, která potřebuje mít přístup k určitým prostředkům, můžete místo aktualizace všech seznamů rolí u každého \[\] autorizačního atributu jednoduše aktualizovat zásadu.

#### <a name="claims"></a>podpory

Deklarace identity jsou páry název-hodnota, které představují vlastnosti ověřeného uživatele. Můžete například ukládat číslo zaměstnance pro uživatele jako deklaraci identity. Deklarace identity se pak dají použít jako součást zásad autorizace. Můžete vytvořit zásadu nazvanou "EmployeeOnly", která vyžaduje existenci deklarace identity s názvem "EmployeeNumber", jak je znázorněno v tomto příkladu:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc();
    services.AddAuthorization(options =>
    {
        options.AddPolicy("EmployeeOnly", policy => policy.RequireClaim("EmployeeNumber"));
    });
}
```

Tato zásada se pak dá použít s \[\] atributem autorizovat k ochraně libovolného kontroleru nebo akce, jak je popsáno výše.

#### <a name="securing-web-apis"></a>Zabezpečení webových rozhraní API

Většina webových rozhraní API by měla implementovat ověřovací systém založený na tokenech. Ověřování tokenu je bezstavové a navržené tak, aby bylo škálovatelné. V ověřovacím systému založeném na tokenech musí klient nejdřív ověřit u poskytovatele ověřování. V případě úspěchu se klientovi vydá token, který je jednoduše kryptograficky smysluplný řetězec znaků. Když klient pak potřebuje vydat požadavek na rozhraní API, přidá tento token jako hlavičku na žádost. Server pak před dokončením žádosti ověří token, který byl nalezen v hlavičce požadavku. Obrázek 7-4 ukazuje tento proces.

![TokenAuth](./media/image7-4.png)

**Obrázek 7-4.** Ověřování na základě tokenu pro webová rozhraní API.

Můžete vytvořit vlastní ověřovací službu, integrovat ji s Azure AD a OAuth nebo implementovat službu pomocí Open Source nástroje, jako je [IdentityServer](https://github.com/IdentityServer).

#### <a name="custom-security"></a>Vlastní zabezpečení

Buďte obzvláště opatrní při zavádění vlastní implementace kryptografie, členství v uživatelích nebo systému generování tokenů. K dispozici je spousta komerčních a open source alternativ, což téměř jistě bude lepší zabezpečení než vlastní implementace.

> ### <a name="references--security"></a>Odkazy – zabezpečení
>
> - **Přehled dokumentů zabezpečení**  
>   https://docs.microsoft.com/aspnet/core/security/
> - **Vynucování SSL v aplikaci ASP.NET Core**  
>   <https://docs.microsoft.com/aspnet/core/security/enforcing-ssl>
> - **Úvod do systému Identity**  
>   <https://docs.microsoft.com/aspnet/core/security/authentication/identity>
> - **Úvod k autorizaci**  
>   <https://docs.microsoft.com/aspnet/core/security/authorization/introduction>
> - **Ověřování a autorizace pro API Apps v Azure App Service**  
>   <https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication>
> - **Server identit**  
>   <https://github.com/IdentityServer>

## <a name="client-communication"></a>Komunikace klienta

Kromě obsluhy stránek a reagování na požadavky na data prostřednictvím webových rozhraní API můžou ASP.NET Core aplikace komunikovat přímo s připojenými klienty. Tato odchozí komunikace může využívat celou řadu přenosových technologií, nejběžnějších WebSockets. ASP.NET Core Signal je knihovna, která usnadňuje přidání funkce komunikace mezi klientem a serverem v reálném čase do vašich aplikací. Signal podporuje nejrůznější technologie přenosu, včetně WebSockets, a abstrakce mnoho podrobností implementace od vývojářů.

Pro ASP.NET Core od verze 2,1 byl k dispozici ASP.NET Core signál.

Komunikace klienta v reálném čase, ať už používá objekty WebSockets přímo nebo jiné techniky, je užitečná v nejrůznějších scénářích aplikací. Možné příklady:

- Živé aplikace chatovací místnosti

- Monitorování aplikací

- Aktualizace průběhu úlohy

- Oznámení

- Interaktivní aplikace formulářů

Při sestavování klientské komunikace do aplikací jsou obvykle k dispozici dvě komponenty:

- Správce připojení na straně serveru (centrum signálů, WebSocketManager WebSocketHandler)

- Knihovna na straně klienta

Klienti nejsou omezeni na prohlížeče – mobilní aplikace, konzolové aplikace a další nativní aplikace mohou komunikovat také pomocí nástroje Signal/WebSockets. Následující jednoduchý program vrátí veškerý obsah odeslaný do konzoly aplikace chat jako součást ukázkové aplikace WebSocketManager:

```csharp
public class Program
{
    private static Connection _connection;
    public static void Main(string[] args)
    {
        StartConnectionAsync();
        _connection.On("receiveMessage", (arguments) =>
        {
            Console.WriteLine($"{arguments[0]} said: {arguments[1]}");
        });
        Console.ReadLine();
        StopConnectionAsync();
    }

    public static async Task StartConnectionAsync()
    {
        _connection = new Connection();
        await _connection.StartConnectionAsync("ws://localhost:65110/chat");
    }

    public static async Task StopConnectionAsync()
    {
        await _connection.StopConnectionAsync();
    }
}
```

Zvažte způsob, jakým vaše aplikace komunikují přímo s klientskými aplikacemi, a zvažte, jestli komunikace v reálném čase vylepší uživatelské prostředí vaší aplikace.

> ### <a name="references--client-communication"></a>Odkazy – komunikace klienta
>
> - **ASP.NET Core signál**  
>   <https://github.com/aspnet/SignalR>
> - **Správce WebSocket**  
>   https://github.com/radu-matei/websocket-manager

## <a name="domain-driven-design--should-you-apply-it"></a>Návrh založený na doméně – byste ho měli použít?

Návrh založený na doméně (DDD) je agilní přístup k vytváření softwaru, který zvýrazňuje zaměření na _obchodní doménu_. Představuje velký důraz na komunikaci a interakci s odborníky na podnikovou doménu, kteří se můžou spojit s vývojáři, jak funguje reálné systém. Pokud například vytváříte systém, který zpracovává skladové obchody, může být odborníkem na vaši doménu zkušeným zprostředkovatelem. DDD je navržený tak, aby vyřešil velké, složité obchodní problémy a často není vhodný pro menší a jednodušší aplikace, protože investice do porozumění a modelování domény nestojí za to.

Při sestavování softwaru po přístupu DDD by váš tým (včetně neodborných smluvních stran a přispěvatelů) měl vyvinout _všudypřítomný jazyk_ pro místo problému. To znamená, že by se stejná terminologie měla použít pro pojem model reálného světa, ekvivalent softwaru a všechny struktury, které mohou existovat pro zachování konceptu (například databázové tabulky). Proto by pojmy popsané v jazyce všudypřítomný měly tvořit základ pro váš _doménový model_.

Model domény se skládá z objektů, které vzájemně spolupracují, aby představovaly chování systému. Tyto objekty mohou patřit do následujících kategorií:

- [Entity](https://deviq.com/entity/), které reprezentují objekty s vláknem identity. Entity jsou obvykle uloženy v persistenci s klíčem, pomocí kterého je možné je později načíst.

- [Agregace](https://deviq.com/aggregate-pattern/), které reprezentují skupiny objektů, které by měly být trvale uložené jako jednotka.

- [Hodnotové objekty](https://deviq.com/value-object/), které reprezentují koncepty, které lze porovnat na základě součtu hodnot jejich vlastností. Například DateRange skládající se z počátečního a koncového data.

- [Události domény](https://martinfowler.com/eaaDev/DomainEvent.html), které představují věci v rámci systému, které jsou důležité pro ostatní části systému.

Počítejte s tím, že doménový model s DDD by měl zapouzdřit složité chování v rámci modelu. Entity, zejména, by neměly být pouze kolekce vlastností. Pokud model domény postrádá chování a pouze představuje stav systému, je tento [model anemic](https://deviq.com/anemic-model/), což je nežádoucí v DDD.

Kromě těchto typů modelů se na DDD obvykle používá celá řada vzorů:

- [Úložiště](https://deviq.com/repository-pattern/)pro abstrakci podrobností o trvalosti.

- [Factory](https://en.wikipedia.org/wiki/Factory_method_pattern)pro zapouzdření komplexního vytváření objektů.

- Události domény pro odspojování závislého chování od chování aktivace.

- [Služby](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/)pro zapouzdření komplexního chování a/nebo podrobností implementace infrastruktury.

- [Příkaz](https://en.wikipedia.org/wiki/Command_pattern)pro oddělení vydávání příkazů a provedení příkazu samotného.

- [Specifikace](https://deviq.com/specification-pattern/)pro zapouzdření podrobností dotazu.

DDD také doporučuje použití čisté architektury popsané dříve, což umožňuje volné spojování, zapouzdření a kód, který lze snadno ověřit pomocí jednotkových testů.

### <a name="when-should-you-apply-ddd"></a>Kdy byste měli použít DDD

DDD je vhodný pro velké aplikace s významnou firmou (ne jenom technickou) složitostí. Aplikace by měla vyžadovat znalosti expertů domény. V samotném modelu domény by mělo být významné chování, které představuje obchodní pravidla a interakce, a to nad rámec pouhého ukládání a načítání aktuálního stavu různých záznamů z úložišť dat.

### <a name="when-shouldnt-you-apply-ddd"></a>Pokud byste neměli použít DDD

DDD zahrnuje investice do modelování, architektury a komunikace, které nemusí být oprávněné pro menší aplikace nebo aplikace, které jsou v podstatě pouze CRUD (vytváření, čtení, aktualizace a odstranění). Pokud se rozhodnete získat přístup k aplikaci po DDD, ale zjistíte, že vaše doména má model anemic bez chování, možná budete muset vzít v úvahu svůj přístup. Buď vaše aplikace nemusí potřebovat DDD, nebo můžete potřebovat pomoc při refaktoringu vaší aplikace k zapouzdření obchodní logiky v doménovém modelu, nikoli v databázi nebo uživatelském rozhraní.

Hybridní přístup by byl pro transakční nebo složitější oblasti aplikace použit pouze DDD, ale ne pro jednodušší části CRUD nebo jen pro čtení. Nemusí podepisovat například omezení agregace, pokud se dotazuje na data pro zobrazení sestavy nebo vizualizaci dat pro řídicí panel. Je naprosto přijatelné, abyste měli samostatný, jednodušší model pro čtení těchto požadavků.

> ### <a name="references--domain-driven-design"></a>Odkazy – návrh založený na doméně
>
> - **DDD v jednoduché angličtině (odpověď StackOverflow)**  
>   <https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488>

## <a name="deployment"></a>Nasazení

Proces nasazení ASP.NET Core aplikace se účastní několika kroků bez ohledu na to, kde se bude hostovat. Prvním krokem je publikování aplikace, která se dá provést pomocí příkazu dotnet publish CLI. Tím dojde k zkompilování aplikace a k umístění všech souborů potřebných ke spuštění aplikace do určené složky. Při nasazení ze sady Visual Studio se tento krok provádí automaticky. Složka Publish obsahuje soubory. exe a. dll pro aplikaci a její závislosti. Samostatně obsažená aplikace bude obsahovat také verzi modulu runtime .NET. ASP.NET Core aplikace budou zahrnovat také konfigurační soubory, statické prostředky klienta a zobrazení MVC.

ASP.NET Core aplikace jsou konzolové aplikace, které musí být spuštěny, když se Server spustí a restartuje, pokud dojde k chybě aplikace (nebo serveru). K automatizaci tohoto procesu lze použít správce procesů. Nejběžnějšími správci procesů pro ASP.NET Core jsou Nginx a Apache v systémech Linux a IIS nebo ve službě Windows ve Windows.

Kromě správce procesů musí ASP.NET Core aplikace hostované na webovém serveru Kestrel použít reverzní proxy server. Zpětný proxy server přijímá požadavky HTTP z Internetu a předá je Kestrel po předběžném zpracování. Reverzní proxy servery poskytují vrstvu zabezpečení pro aplikaci a vyžadují se pro nasazení Edge (vystavené provozu z Internetu). Kestrel je relativně nové a ještě nenabízí ochranu proti určitým útokům. Kestrel také nepodporuje hostování více aplikací na stejném portu, takže techniky, jako jsou hlavičky hostitelů, nelze s ní používat, aby bylo možné hostovat více aplikací na stejném portu a IP adrese.

![Kestrel na Internet](./media/image7-5.png)

**Obrázek 7-5**. ASP.NET hostované v Kestrel za reverzním proxy server

Dalším scénářem, ve kterém může mít reverzní proxy být užitečný, je zabezpečení více aplikací pomocí protokolu SSL/HTTPS. V takovém případě musí mít nakonfigurován protokol SSL pouze reverzní proxy server. Komunikace mezi zpětným proxy server a Kestrel může probíhat přes protokol HTTP, jak je znázorněno na obrázku 7-6.

![ASP.NET hostované za reverzním proxy server zabezpečeným protokolem HTTPS](./media/image7-6.png)

**Obrázek 7-6**. ASP.NET hostované za reverzním proxy server zabezpečeným protokolem HTTPS

Stále oblíbeným přístupem je hostování aplikace ASP.NET Core v kontejneru Docker, který pak můžete hostovat místně nebo nasadit do Azure pro cloudové hostování. Kontejner Docker může obsahovat kód vaší aplikace spuštěný v Kestrel a bude nasazen za reverzním proxy server, jak je uvedeno výše.

Pokud jste hostitelem aplikace v Azure, můžete použít Microsoft Azure Application Gateway jako vyhrazené virtuální zařízení k poskytnutí několika služeb. Kromě toho, že funguje jako reverzní proxy server pro jednotlivé aplikace, Application Gateway může také nabízet tyto funkce:

- Vyrovnávání zatížení HTTP

- Přesměrování zpracování SSL (jenom SSL pro Internet)

- Koncové šifrování protokolu SSL

- Směrování na více webů (konsolidovat až 20 lokalit na jednom Application Gateway)

- Firewall webových aplikací

- Podpora protokolu WebSocket

- Pokročilá diagnostika

_Další informace o možnostech nasazení Azure najdete v [kapitole 10](development-process-for-azure.md)._

> ### <a name="references--deployment"></a>Odkazy – nasazení
>
> - **Přehled hostování a nasazení**  
>   <https://docs.microsoft.com/aspnet/core/publishing/>
> - **Kdy použít Kestrel s reverzním proxy serverem**  
>   <https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy>
> - **Hostování ASP.NET Core aplikací v Docker**  
>   <https://docs.microsoft.com/aspnet/core/publishing/docker>
> - **Představujeme Azure Application Gateway**  
>   <https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction>

>[!div class="step-by-step"]
>[Předchozí](common-client-side-web-technologies.md)
>[Další](work-with-data-in-asp-net-core-apps.md)
