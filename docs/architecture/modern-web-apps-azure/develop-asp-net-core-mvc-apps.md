---
title: Vývoj aplikací ASP.NET Core MVC
description: Architekt moderní webové aplikace s ASP.NET core a Azure | vývoj ASP.NET core MVC Apps
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: 3de70af23206b0ae0525541b3d2cb480dc5bb882
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987904"
---
# <a name="develop-aspnet-core-mvc-apps"></a>Vývoj aplikací ASP.NET Core MVC

> "Není důležité, aby to bylo napoprvé správně. Je životně důležité, aby to bylo správné minule."  
> _- Andrew Hunt a David Thomas_

ASP.NET Core je multiplatformní open source framework pro vytváření moderních webových aplikací optimalizovaných pro cloud. aplikace ASP.NET Core jsou lehké a modulární, s integrovanou podporou vkládání závislostí, což umožňuje větší testovatelnost a udržovatelnost. V kombinaci s MVC, který podporuje vytváření moderních webových rozhraní API kromě aplikací založených na zobrazení, ASP.NET Core je výkonný rámec pro vytváření podnikových webových aplikací.

## <a name="mvc-and-razor-pages"></a>MVC a Břitva stránky

ASP.NET Core MVC nabízí mnoho funkcí, které jsou užitečné pro vytváření webových api a aplikací. Termín MVC je zkratka pro "Model-View-Controller", vzor uživatelského rozhraní, které rozděluje odpovědnost i odpovědi na požadavky uživatelů do několika částí. Kromě sledování tohoto vzoru můžete také implementovat funkce ve svých aplikacích ASP.NET Core jako Razor Pages. Razor Pages jsou integrovány do ASP.NET Core MVC a používají stejné funkce pro směrování, vázání modelu atd. Místo toho, aby samostatné složky a soubory pro řadiče, zobrazení, atd.

Když vytvoříte novou ASP.NET základní aplikaci, měli byste mít na mysli plán pro druh aplikace, kterou chcete vytvořit. V sadě Visual Studio si vyberete z několika šablon. Tři nejběžnější šablony projektu jsou webové rozhraní API, webová aplikace a webová aplikace (Model-View-Controller). I když toto rozhodnutí můžete učinit pouze při prvním vytvoření projektu, není to neodvolatelné rozhodnutí. Projekt webového rozhraní API používá standardní řadiče model-view-controller – ve výchozím nastavení prostě postrádá zobrazení. Stejně tak výchozí šablona webové aplikace používá Razor Pages, a proto také postrádá složku Zobrazení. Později můžete do těchto projektů přidat složku Zobrazení, která podporuje chování založené na zobrazení. Webové rozhraní API a projekty Model-View-Controller ve výchozím nastavení neobsahují složku Stránky, ale můžete ji přidat později pro podporu chování založeného na Razor Pages. Tyto tři šablony si můžete myslet jako podporu tří různých druhů výchozí interakce s uživatelem: data (webové rozhraní API), založené na stránce a založené na zobrazení. Pokud však chcete, můžete některé nebo všechny tyto kombinace kombinovat v rámci jednoho projektu.

### <a name="why-razor-pages"></a>Proč Razor Stránky?

Razor Pages je výchozí přístup pro nové webové aplikace v sadě Visual Studio. Razor Pages nabízí jednodušší způsob vytváření funkcí aplikací založených na stránce, jako jsou formuláře bez SPA. Pomocí řadičů a zobrazení bylo běžné, že aplikace mají velmi velké řadiče, které pracovaly s mnoha různými závislostmi a zobrazovaly modely a vracely mnoho různých zobrazení. To mělo za následek větší složitost a často vedlo k tomu, že řadiče, které účinně nedodržovaly zásady jednotné odpovědnosti nebo zásady otevřených/uzavřených zásad. Razor Pages řeší tento problém zapouzdřením logiky na straně serveru pro danou logickou "stránku" ve webové aplikaci se značkami Razor. Razor Page, který nemá logiku na straně serveru může jednoduše sestávat ze souboru Razor (například "Index.cshtml"). Většina netriviálních stránek Razor však bude mít přidruženou třídu modelu stránky, která je podle konvence pojmenována stejně jako soubor Razor s příponou ".cs" (například "Index.cshtml.cs").

Model stránky Razor Page kombinuje odpovědnosti řadiče MVC a modelu zobrazení. Namísto zpracování požadavků s metodami akce řadiče, obslužné rutiny modelu stránky jako "OnGet()" jsou provedeny, vykreslování jejich přidružené stránky ve výchozím nastavení. Razor Pages zjednodušuje proces vytváření jednotlivých stránek v aplikaci ASP.NET Core a zároveň poskytuje všechny architektonické funkce ASP.NET Core MVC. Jsou dobrou výchozí volbou pro nové funkce založené na stránce.

### <a name="when-to-use-mvc"></a>Kdy použít MVC

Pokud vytváříte webová api, vzor MVC dává větší smysl než pokus o použití stránek Razor Pages. Pokud váš projekt bude pouze vystavit koncové body webového rozhraní API, měli byste v ideálním případě začít ze šablony projektu webového rozhraní API. V opačném případě je snadné přidat řadiče a přidružené koncové body rozhraní API do libovolné aplikace ASP.NET Core. Přístup MVC založený na zobrazení použijte, pokud migrujete existující aplikaci z ASP.NET MVC 5 nebo starší, abyste ASP.NET Core MVC a chcete tak učinit s nejmenším úsilím. Jakmile provedete počáteční migraci, můžete vyhodnotit, zda má smysl přijmout Razor Pages pro nové funkce nebo dokonce jako velkoobchodní migraci.

Ať už se rozhodnete vytvořit webovou aplikaci pomocí Razor Pages nebo MVC zobrazení, vaše aplikace bude mít podobný výkon a bude zahrnovat podporu pro vkládání závislostí, filtry, vazby modelu, ověřování a tak dále.

## <a name="mapping-requests-to-responses"></a>Mapování požadavků na odpovědi

V srdci aplikace ASP.NET Core mapují příchozí požadavky na odchozí odpovědi. Na nízké úrovni se to provádí pomocí middlewaru a jednoduché ASP.NET základní aplikace a mikroslužby mohou být tvořeny výhradně vlastním middlewarem. Při použití ASP.NET Core MVC, můžete pracovat na poněkud vyšší úrovni, myšlení, pokud jde o _trasy_, _regulátory_, a _akce_. Každý příchozí požadavek je porovnán s směrovací tabulkou aplikace a pokud je nalezena odpovídající trasa, je volána přidružená metoda akce (patřící k řadiči) pro zpracování požadavku. Pokud není nalezena žádná odpovídající trasa, je volána obslužná rutina chyby (v tomto případě vrácení výsledku NotFound).

ASP.NET aplikace Core MVC můžou používat konvenční trasy, trasy atributů nebo obojí. Konvenční trasy jsou definovány v kódu a určují _konvence_ směrování pomocí syntaxe, jako v příkladu níže:

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapControllerRoute(name: "default", pattern: "{controller=Home}/{action=Index}/{id?}");
});
```

V tomto příkladu byla do směrovací tabulky přidána trasa s názvem "výchozí". Definuje šablonu trasy se zástupnými symboly pro _kontroler_, _akci_a _id_. Řadič a zástupné symboly akce mají výchozí zadané ("Home" a "Index", v uvedeném pořadí) a zástupný symbol id je volitelný (na základě "?" na něj aplikovaný). Konvence definované zde uvádí, že první část požadavku by měla odpovídat názvu řadiče, druhá část akce a pak v případě potřeby třetí část bude představovat id parametr. Konvenční trasy jsou obvykle definovány na jednom místě pro aplikaci, například v Configure metoda ve třídě Startup.

Atribut trasy jsou použity pro řadiče a akce přímo, nikoli určené globálně. To má tu výhodu, že je mnohem více zjistitelné, když se díváte na určitou metodu, ale znamená to, že informace o směrování nejsou uchovávány na jednom místě v aplikaci. Pomocí tras atributů můžete snadno zadat více tras pro danou akci a také kombinovat trasy mezi řadiči a akcemi. Příklad:

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

Trasy lze zadat na [HttpGet] a podobné atributy, vyhnout se nutnosti přidat samostatné [Route] atributy. Trasy atributů mohou také použít tokeny ke snížení potřeby opakovat názvy řadičů nebo akcí, jak je znázorněno níže:

```csharp
[Route("[controller]")]
public class ProductsController : Controller
{
    [Route("")] // Matches 'Products'
    [Route("Index")] // Matches 'Products/Index'
    public IActionResult Index() {}
}
```

Razor Pages nepoužívá směrování atributů. Jako součást směrnice `@page` můžete zadat další informace o šabloně trasy pro stránku Razor:

```csharp
@page "{id:int}"
```

V předchozím příkladu by dotyčná stránka odpovídala trase s parametrem celé číslo. `id` Například stránka *Products.cshtml* umístěná v `/Pages` kořenovém adresáři bude mít tuto trasu:

```csharp
"/Products/123"
```

Jakmile daný požadavek byl spárován s trasou, ale před voláním metody akce, ASP.NET Core MVC provede [vazbu modelu](/aspnet/core/mvc/models/model-binding) a [ověření modelu](/aspnet/core/mvc/models/validation) na požadavek. Vazba modelu je zodpovědná za převod příchozích dat HTTP na typy .NET zadané jako parametry metody akce, která má být volána. Například pokud metoda akce očekává parametr int id, vazba modelu se pokusí poskytnout tento parametr z hodnoty poskytnuté jako součást požadavku. Chcete-li tak učinit, vazba modelu hledá hodnoty v zaúčtovaném formuláři, hodnoty v samotném postupu a hodnoty řetězce dotazu. Za předpokladu, že je nalezena hodnota id, bude před předáním do metody akce převedena na celé číslo.

Po vazbě modelu, ale před voláním metody akce dojde k ověření modelu. Ověření modelu používá volitelné atributy pro typ modelu a může pomoci zajistit, aby zadaný objekt modelu splňoval určité požadavky na data. Některé hodnoty mohou být specifikovány podle potřeby nebo omezeny na určitou délku nebo číselný rozsah atd. Pokud jsou zadány atributy ověření, ale model nesplňuje jejich požadavky, vlastnost ModelState.IsValid bude false a sada selhání ověřovací pravidla budou k dispozici k odeslání klientovi, který žádost.

Pokud používáte ověření modelu, měli byste vždy zkontrolovat, zda je model platný před provedením jakýchkoli příkazů pro změnu stavu, abyste zajistili, že vaše aplikace není poškozena neplatnými daty. Můžete použít [filtr,](/aspnet/core/mvc/controllers/filters) aby se zabránilo nutnosti přidat kód pro tuto akci. ASP.NET core MVC filtry nabízejí způsob, jak zachytit skupiny žádostí, takže společné politiky a průřezové obavy mohou být použity na cílené bázi. Filtry lze použít pro jednotlivé akce, celé řadiče nebo globálně pro aplikaci.

Pro webová api ASP.NET Core MVC podporuje [_vyjednávání obsahu_](/aspnet/core/mvc/models/formatting), což umožňuje požadavkům určit, jak mají být odpovědi formátovány. Na základě záhlaví uvedených v požadavku budou akce vracející data formátovat odpověď ve formátu XML, JSON nebo jiném podporovaném formátu. Tato funkce umožňuje stejné rozhraní API používat více klientů s různými požadavky na formát dat.

Projekty webového rozhraní `[ApiController]` API by měly zvážit použití atributu, který lze použít pro jednotlivé řadiče, pro třídu základního řadiče nebo pro celé sestavení. Tento atribut přidá automatickou kontrolu ověření modelu a všechny akce s neplatným modelem vrátí BadRequest s podrobnostmi o chybách ověření. Atribut také vyžaduje, aby všechny akce mají trasu atributu, nikoli pomocí konvenční trasy a vrátí podrobnější ProblemDetails informace v reakci na chyby.

> ### <a name="references--mapping-requests-to-responses"></a>Odkazy – mapování požadavků na odpovědi
>
> - **Směrování k akcím řadiče**
 > <https://docs.microsoft.com/aspnet/core/mvc/controllers/routing>
> - **Vazba modelu**
 > <https://docs.microsoft.com/aspnet/core/mvc/models/model-binding>
> - **Ověření modelu**
 > <https://docs.microsoft.com/aspnet/core/mvc/models/validation>
> - **Filtry**
 > <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - **Atribut ApiController**
 > <https://docs.microsoft.com/aspnet/core/web-api/>

## <a name="working-with-dependencies"></a>Práce se závislostmi

ASP.NET Core má vestavěnou podporu a interně využívá techniku známou jako [vkládání závislostí](/aspnet/core/fundamentals/dependency-injection). Vkládání závislostí je technika, která umožňuje volné párování mezi různými částmi aplikace. Volnější spojka je žádoucí, protože usnadňuje izolátní částí aplikace, což umožňuje testování nebo výměnu. To také dělá méně pravděpodobné, že změna v jedné části aplikace bude mít neočekávaný dopad někde jinde v aplikaci. Vkládání závislostí je založeno na principu inverze závislosti a je často klíčem k dosažení principu otevření/uzavření. Při vyhodnocování, jak vaše aplikace pracuje s jeho závislosti, dejte si pozor na [statické přilnavý](https://deviq.com/static-cling/) kód vůně, a pamatujte aforismus["nové je lepidlo](https://ardalis.com/new-is-glue)" .

Statické přilnutí dochází při vaše třídy volat statické metody nebo přístup ke statickým vlastnostem, které mají vedlejší účinky nebo závislosti na infrastruktuře. Například pokud máte metodu, která volá statickou metodu, která zase zapíše do databáze, vaše metoda je pevně spojena s databází. Cokoli, co přeruší volání databáze, přeruší vaši metodu. Testování těchto metod je notoricky obtížné, protože tyto testy buď vyžadují komerční zesměšňovat knihovny zesměšňovat statické volání, nebo mohou být testovány pouze s testovací databáze na místě. Statická volání, která nemají žádnou závislost na infrastruktuře, zejména ty, které jsou zcela bezstátní, jsou v pořádku volat a nemají žádný vliv na párování nebo testovatelnost (mimo kód párování na statické volání samotné).

Mnoho vývojářů pochopit rizika statické lpět a globální stav, ale bude stále pevně spárovat svůj kód na konkrétní implementace prostřednictvím přímé instance. "New is glue" má být připomínkou této spojky, a nikoli `new` obecným odsouzením použití klíčového slova. Stejně jako u volání statické metody, nové instance typů, které nemají žádné externí závislosti obvykle nejsou pevně pár kód implementace podrobnosti nebo ztížit testování. Ale pokaždé, když je vytvořena instance třídy, trvat jen krátkou chvíli, aby zvážila, zda má smysl, aby pevný kód, že konkrétní instance v tomto konkrétním umístění, nebo pokud by bylo lepší návrh požadovat, aby instance jako závislost.

### <a name="declare-your-dependencies"></a>Deklarovat své závislosti

ASP.NET Core je postaven na tom, že metody a třídy deklarují své závislosti a požadují je jako argumenty. ASP.NET aplikace jsou obvykle nastaveny ve třídě Startup, která je sama nakonfigurována tak, aby podporovala vkládání závislostí na několika místech. Pokud vaše startupová třída má konstruktor, může prostřednictvím konstruktoru požadovat závislosti, například takto:

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

Startup třída je zajímavé v tom, že neexistují žádné požadavky explicitní typ pro něj. Nedědí ze speciální základní třídy při spuštění, ani neimplementuje žádné konkrétní rozhraní. Můžete mu dát konstruktor, nebo ne, a můžete zadat tolik parametrů na konstruktoru, jak chcete. Po spuštění webového hostitele, který jste nakonfigurovali pro vaši aplikaci, bude volat třídu Startup, kterou jste mu řekli, aby používala, a použije vkládání závislostí k naplnění všech závislostí, které třída Po spuštění vyžaduje. Samozřejmě pokud požadujete parametry, které nejsou nakonfigurovány v kontejneru služeb používaném ASP.NET Core, dostanete výjimku, ale pokud se budete držet závislostí, o kterých kontejner ví, můžete požádat o cokoliv chcete.

Vkládání závislostí je integrovándo ASP.NET základní aplikace hned od začátku, když vytvoříte instanci po spuštění. To nekončí, že pro spuštění třídy. Můžete také požádat o závislosti v configure metoda:

```csharp
public void Configure(IApplicationBuilder app,
    IHostingEnvironment env,
    ILoggerFactory loggerFactory)
{

}
```

ConfigureServices Metoda je výjimka z tohoto chování; musí trvat pouze jeden parametr typu IServiceCollection. Není opravdu nutné podporovat vkládání závislostí, protože na jedné straně je zodpovědný za přidání objektů do kontejneru služeb a na druhé straně má přístup ke všem aktuálně nakonfigurovaných služeb prostřednictvím iServiceCollection parametr. Proto můžete pracovat se závislostmi definovanými v kolekci služeb ASP.NET Core v každé části třídy Startup, a to buď vyžádáním potřebné služby jako parametru, nebo prací s IServiceCollection v ConfigureServices.

> [!NOTE]
> Pokud potřebujete zajistit, aby určité služby byly k dispozici pro vaši třídu Startup, můžete je nakonfigurovat pomocí IWebHostBuilder a jeho metody ConfigureServices uvnitř volání CreateDefaultBuilder.

Třída Startup je model pro strukturu jiných částí aplikace ASP.NET Core, od řadičů přes Middleware až po filtry až po vlastní služby. V každém případě byste měli dodržovat [explicitdependencies principle](https://deviq.com/explicit-dependencies-principle/), požadující vaše závislosti spíše než jejich přímé vytváření a využití vkládání závislostí v celé aplikaci. Dávejte pozor na to, kde a jak přímo konkretizovat implementace, zejména služby a objekty, které pracují s infrastrukturou nebo mají vedlejší účinky. Preferujte práci s abstrakcemi definovanými v jádru aplikace a předávanými jako argumenty pro odkazy na hardcoding na konkrétní typy implementace.

## <a name="structuring-the-application"></a>Strukturování aplikace

Monolitické aplikace mají obvykle jeden vstupní bod. V případě webové aplikace ASP.NET Core bude vstupním bodem webový projekt ASP.NET Core. To však neznamená, že řešení by se mělo skládat pouze z jednoho projektu. Je užitečné rozdělit aplikaci do různých vrstev, aby bylo možné sledovat oddělení obav. Po rozdělení do vrstev je užitečné jít nad rámec složek do samostatných projektů, což může pomoci dosáhnout lepšího zapouzdření. Nejlepší přístup k dosažení těchto cílů s aplikací ASP.NET Core je varianta čisté architektury popsané v kapitole 5. Podle tohoto přístupu bude řešení aplikace se skládá ze samostatných knihoven pro uživatelské ui, infrastruktury a ApplicationCore.

Kromě těchto projektů jsou zahrnuty také samostatné testovací projekty (testování je popsáno v kapitole 9).

Objektový model aplikace a rozhraní by měly být umístěny v projektu ApplicationCore. Tento projekt bude mít co nejméně závislostí a ostatní projekty v řešení na něj budou odkazovat. Obchodní entity, které je třeba zachovat, jsou definovány v projektu ApplicationCore, stejně jako služby, které nejsou přímo závislé na infrastruktuře.

Podrobnosti implementace, například jak se provádí trvalost nebo jak mohou být oznámení odesílána uživateli, jsou uchovávány v projektu Infrastruktura. Tento projekt bude odkazovat na balíčky specifické pro implementaci, jako je například core entity framework, ale neměl by vystavit podrobnosti o těchto implementacích mimo projekt. Infrastrukturní služby a úložiště by měly implementovat rozhraní, která jsou definována v projektu ApplicationCore, a jeho implementace trvalosti jsou zodpovědné za načítání a ukládání entit definovaných v ApplicationCore.

Projekt ASP.NET základního ui je zodpovědný za všechny obavy o úroveň ui, ale neměl by obsahovat obchodní logiku nebo podrobnosti o infrastruktuře. Ve skutečnosti v ideálním případě by neměl mít ani závislost na projektu Infrastruktura, což pomůže zajistit, že žádná závislost mezi těmito dvěma projekty není náhodně zavedena. Toho lze dosáhnout pomocí kontejneru DI jiného výrobce, jako je Autofac, který umožňuje definovat pravidla DI ve třídách modulu v každém projektu.

Dalším přístupem k oddělení aplikace od podrobností implementace je mít mikroslužby volání aplikace, možná nasazené v jednotlivých kontejnerech Dockeru. To poskytuje ještě větší oddělení obav a oddělení než využití DI mezi dvěma projekty, ale má další složitost.

### <a name="feature-organization"></a>Organizace funkcí

Ve výchozím nastavení ASP.NET základní aplikace uspořádat jejich strukturu složek tak, aby zahrnovala řadiče a zobrazení a často ViewModels. Kód na straně klienta pro podporu těchto struktur na straně serveru je obvykle uložen samostatně ve složce wwwroot. Velké aplikace však mohou narazit na problémy s touto organizací, protože práce na dané funkci často vyžaduje přechod mezi těmito složkami. To je stále obtížnější, protože počet souborů a podsložek v každé složce roste, což má za následek velké procházení Průzkumníka řešení. Jedním z řešení tohoto problému je uspořádání kódu aplikace podle _funkce_ namísto podle typu souboru. Tento organizační styl se obvykle označuje jako složky prvků nebo [řezy prvků](https://docs.microsoft.com/archive/msdn-magazine/2016/september/asp-net-core-feature-slices-for-asp-net-core-mvc) (viz také: [Svislé řezy](https://deviq.com/vertical-slices/)).

ASP.NET Core MVC podporuje oblasti pro tento účel. Pomocí oblastí můžete v každé složce Oblast vytvořit samostatné sady složek Řadiče a zobrazení (stejně jako všechny přidružené modely). Obrázek 7-1 znázorňuje ukázkovou strukturu složek pomocí funkce Oblasti.

![Vzorová oblast organizace](./media/image7-1.png)

**Obrázek 7-1**. Vzorová oblast organizace

Při použití oblastí, musíte použít atributy k dekoraci řadiče s názvem oblasti, do které patří:

```csharp
[Area("Catalog")]
public class HomeController
{}
```

K cestám je také třeba přidat podporu oblasti:

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapControllerRoute(name: "areaRoute", pattern: "{area:exists}/{controller=Home}/{action=Index}/{id?}");
    endpoints.MapControllerRoute(name: "default", pattern: "{controller=Home}/{action=Index}/{id?}");
});
```

Kromě integrované podpory pro oblasti můžete také použít vlastní strukturu složek a konvence namísto atributů a vlastních tras. To by vám umožnilo mít složky funkcí, které neobsahovaly samostatné složky pro zobrazení, řadiče atd., aby hierarchie byla plošší a usnadnila zobrazení všech souvisejících souborů na jednom místě pro každou funkci.

ASP.NET Core používá integrované typy konvencí k řízení jeho chování. Tyto konvence můžete upravit nebo nahradit. Můžete například vytvořit konvenci, která automaticky získá název funkce pro daný řadič na základě jeho oboru názvů (který obvykle koreluje se složkou, ve které je řadič umístěn):

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

Tuto konvenci pak zadáte jako možnost, když přidáte podporu pro MVC do vaší aplikace v ConfigureServices:

```csharp
services.AddMvc(o => o.Conventions.Add(new FeatureConvention()));
```

ASP.NET Core MVC také používá konvence k vyhledání zobrazení. Můžete přepsat pomocí vlastní konvence tak, aby zobrazení budou umístěny ve složkách funkcí (pomocí názvu funkce poskytované FeatureConvention, výše). Můžete se dozvědět více o tomto přístupu a stáhnout pracovní ukázku z článku Časopisu MSDN, [Funkce řezy pro ASP.NET Core MVC](https://docs.microsoft.com/archive/msdn-magazine/2016/september/asp-net-core-feature-slices-for-asp-net-core-mvc).

### <a name="cross-cutting-concerns"></a>Související aspekty

S růstem aplikací je stále důležitější zohlednit průřezové obavy, aby se odstranila duplicita a zachovala konzistence. Některé příklady průřezových problémů v ASP.NET základních aplikacích jsou ověřování, pravidla ověřování modelu, ukládání do mezipaměti výstupu a zpracování chyb, i když existuje mnoho dalších. ASP.NET core MVC [filtry](/aspnet/core/mvc/controllers/filters) umožňují spustit kód před nebo po určité kroky v kanálu zpracování požadavků. Například filtr lze spustit před a po vazby modelu, před a po akci nebo před a po výsledku akce. K řízení přístupu ke zbytku kanálu můžete také použít filtr autorizace. Obrázek 7-2 ukazuje, jak spuštění požadavku toky filtry, pokud jsou nakonfigurovány.

![Požadavek je zpracován prostřednictvím filtrů autorizace, filtrů prostředků, vazby modelu, filtrů akcí, provádění akcí a převodu výsledků akce, filtrů výjimek, filtrů výsledků a spuštění výsledků. Na cestě ven je požadavek zpracován pouze filtry výsledků a filtry prostředků před tím, než se stane odpovědí odeslanou klientovi.](./media/image7-2.png)

**Obrázek 7-2**. Požádejte o spuštění prostřednictvím filtrů a kanálu požadavků.

Filtry jsou obvykle implementovány jako atributy, takže je můžete použít na řadiče nebo akce (nebo dokonce globálně). Při přidání tímto způsobem filtry zadané na úrovni akce přepsat nebo stavět na filtry určené na úrovni řadiče, které samy přepsat globální filtry. Atribut \[Route\] lze například použít k vytvoření tras mezi řadiči a akcemi. Podobně autorizace může být nakonfigurována na úrovni řadiče a poté přepsána jednotlivými akcemi, jak ukazuje následující ukázka:

```csharp
[Authorize]
public class AccountController : Controller

{
    [AllowAnonymous] // overrides the Authorize attribute
    public async Task<IActionResult> Login() {}
    public async Task<IActionResult> ForgotPassword() {}
}
```

První metoda, Login, používá AllowAnonymous filtr (atribut) přepsat autorizovat filtr nastavit na úrovni řadiče. Akce ForgotPassword (a jakákoli jiná akce ve třídě, která nemá atribut AllowAnonymous) bude vyžadovat ověřený požadavek.

Filtry lze použít k odstranění duplicit ve formě běžných zásad zpracování chyb pro rozhraní API. Například typické zásady rozhraní API je vrátit NotFound odpověď na požadavky odkazující na klíče, které neexistují, a Odpověď BadRequest, pokud se nezdaří ověření modelu. Následující příklad ukazuje tyto dvě zásady v akci:

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

Nedovolte, aby vaše metody akce, aby se stal přeplněný s podmíněným kódem, jako je tento. Místo toho přetáhněte zásady do filtrů, které lze použít podle potřeby. V tomto příkladu může být kontrola ověření modelu, ke které by mělo dojít při každém odeslání příkazu do rozhraní API, nahrazena následujícím atributem:

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

Můžete přidat `ValidateModelAttribute` do projektu jako závislost NuGet zahrnutím balíčku [Ardalis.ValidateModel.](https://www.nuget.org/packages/Ardalis.ValidateModel) Pro api můžete použít `ApiController` atribut k vynucení tohoto chování `ValidateModel` bez nutnosti samostatného filtru.

Podobně filtr lze použít ke kontrole, zda existuje záznam a vrátit 404 před provedením akce, což eliminuje potřebu provádět tyto kontroly v akci. Jakmile vytáhnete běžné konvence a uspořádáte řešení tak, aby oddělovali kód infrastruktury a obchodní logiku od vašeho ui, měly by být vaše metody akce MVC extrémně tenké:

```csharp
[HttpPut("{id}")]
[ValidateAuthorExists]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

Můžete si přečíst více o implementaci filtrů a stáhnout pracovní ukázku z článku Časopisu MSDN, [Real-World ASP.NET Core MVC filtry](https://docs.microsoft.com/archive/msdn-magazine/2016/august/asp-net-core-real-world-asp-net-core-mvc-filters).

> ### <a name="references--structuring-applications"></a>Reference – Strukturování aplikací
>
> - **Oblasti**  
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/areas>
> - **MSDN Magazine - Funkce plátky pro ASP.NET Jádra MVC**  
>   <https://docs.microsoft.com/archive/msdn-magazine/2016/september/asp-net-core-feature-slices-for-asp-net-core-mvc>
> - **Filtry**  
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - **MSDN Magazine - Real World ASP.NET Core MVC filtry**  
>   <https://docs.microsoft.com/archive/msdn-magazine/2016/august/asp-net-core-real-world-asp-net-core-mvc-filters>

## <a name="security"></a>Zabezpečení

Zabezpečení webových aplikací je velké téma, s mnoha úvahami. Na nejzákladnější úrovni zabezpečení zahrnuje zajištění, že víte, od koho daný požadavek pochází, a pak zajištění, že žádost má pouze přístup k prostředkům, které by měla. Ověřování je proces porovnání pověření dodaný s požadavkem na ty v důvěryhodném úložišti dat, chcete-li zjistit, zda požadavek by měl být považován za pocházející ze známé entity. Autorizace je proces omezení přístupu k určitým prostředkům na základě identity uživatele. Třetím bezpečnostním problémem je ochrana žádostí před odposlechem třetími stranami, pro které byste měli alespoň [zajistit, aby vaše aplikace používala ssl](/aspnet/core/security/enforcing-ssl).

### <a name="authentication"></a>Authentication

ASP.NET Core Identity je systém členství, který můžete použít k podpoře funkce přihlášení pro vaši aplikaci. Má podporu pro místní uživatelské účty, stejně jako externí podporu poskytovatele přihlášení od poskytovatelů, jako je účet Microsoft, Twitter, Facebook, Google a další. Kromě ASP.NET základní identity může vaše aplikace používat ověřování systému Windows nebo poskytovatele identity jiného výrobce, jako [je Identity Server](https://github.com/IdentityServer/IdentityServer4).

ASP.NET Základní identita je zahrnuta v nových šablonách projektu, pokud je vybrána možnost Individuální uživatelské účty. Tato šablona obsahuje podporu pro registraci, přihlášení, externí přihlášení, zapomenutá hesla a další funkce.

![Vyberte jednotlivé uživatelské účty, chcete-li mít předkonfigurovanou identitu.](./media/image7-3.png)

**Obrázek 7-3**. Vyberte jednotlivé uživatelské účty, chcete-li mít identitu předem nakonfigurovanou.

Podpora identit je nakonfigurována při spuštění, a to jak v ConfigureServices, tak v configureservices a configure:

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
    app.UseEndpoints(endpoints =>
    {
        endpoints.MapControllerRoute(name: "default", pattern: "{controller=Home}/{action=Index}/{id?}");
    });
}
```

Je důležité, aby UseIdentity se zobrazí před UseMvc v Configure metoda. Při konfiguraci identity v ConfigureServices, všimnete si volání AddDefaultTokenProviders. To nemá nic společného s tokeny, které mohou být použity k zabezpečení webové komunikace, ale místo toho odkazuje na poskytovatele, kteří vytvářejí výzvy, které mohou být odeslány uživatelům prostřednictvím SMS nebo e-mailu, aby mohli potvrdit svou identitu.

Další informace o [konfiguraci dvoufaktorového ověřování](/aspnet/core/security/authentication/2fa) a [povolení externích poskytovatelů přihlášení](/aspnet/core/security/authentication/social/) z oficiálních ASP.NET základní dokumenty.

### <a name="authorization"></a>Autorizace

Nejjednodušší forma autorizace zahrnuje omezení přístupu k anonymním uživatelům. Toho lze dosáhnout jednoduše \[použitím\] atributu Authorize na určité řadiče nebo akce. Pokud jsou role používány, atribut lze dále rozšířit omezit přístup k uživatelům, kteří patří do určité role, jak je znázorněno:

```csharp
[Authorize(Roles = "HRManager,Finance")]
public class SalaryController : Controller
{

}
```

V tomto případě by uživatelé, kteří patří do role HRManager nebo Finance (nebo obojí), měli přístup k SalaryController. Chcete-li vyžadovat, aby uživatel patřil do více rolí (nikoli pouze do jedné z několika), můžete atribut použít vícekrát a pokaždé zadat požadovanou roli.

Určení určitých sad rolí jako řetězců v mnoha různých řadičích a akcích může vést k nežádoucímu opakování. Můžete nakonfigurovat zásady autorizace, které zapouzdřují autorizační pravidla, a při použití atributu \[Authorize\] určit zásady namísto jednotlivých rolí:

```csharp
[Authorize(Policy = "CanViewPrivateReport")]
public IActionResult ExecutiveSalaryReport()
{
    return View();
}
```

Pomocí zásad tímto způsobem můžete oddělit druhy akcí, které jsou omezeny, od konkrétních rolí nebo pravidel, která se na ně vztahují. Později pokud vytvoříte novou roli, která potřebuje mít přístup k určitým prostředkům, můžete pouze \[aktualizovat\] zásady, spíše než aktualizovat každý seznam rolí na každém atributu Authorize.

#### <a name="claims"></a>Deklarace identity

Deklarace jsou dvojice hodnot názvů, které představují vlastnosti ověřeného uživatele. Můžete například uložit číslo zaměstnance uživatele jako deklaraci. Deklarace identity pak lze použít jako součást zásad autorizace. Můžete vytvořit zásadu s názvem "EmployeeOnly", která vyžaduje existenci deklarace s názvem "EmployeeNumber", jak je znázorněno v tomto příkladu:

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

Tato zásada by pak \[\] mohla být použita s atributem Authorize k ochraně libovolného řadiče nebo akce, jak je popsáno výše.

#### <a name="securing-web-apis"></a>Zabezpečení webových api

Většina webových api by měla implementovat ověřovací systém založený na tokenech. Ověřování tokenů je bezstavové a je navrženo tak, aby bylo škálovatelné. V ověřovacím systému založeném na tokenech musí klient nejprve ověřit u zprostředkovatele ověřování. Pokud je úspěšný, je klientovi vydán token, který je jednoduše kryptograficky smysluplný řetězec znaků. Když klient pak potřebuje vydat požadavek na rozhraní API, přidá tento token jako záhlaví na požadavek. Server pak ověří token nalezený v hlavičce požadavku před dokončením požadavku. Obrázek 7-4 ukazuje tento proces.

![TokenAuth](./media/image7-4.png)

**Obrázek 7-4.** Ověřování na základě tokenu pro webová řešení API.

Můžete vytvořit vlastní ověřovací službu, integrovat s Azure AD a OAuth nebo implementovat službu pomocí open source nástroje, jako [je IdentityServer](https://github.com/IdentityServer).

#### <a name="custom-security"></a>Vlastní zabezpečení

Buďte obzvláště opatrní při "válcování vlastní" implementace kryptografie, členství uživatele nebo token generování systému. Existuje mnoho komerčních a open-source alternativy k dispozici, které budou téměř jistě mít lepší zabezpečení než vlastní implementace.

> ### <a name="references--security"></a>Reference – zabezpečení
>
> - **Přehled dokumentů zabezpečení**  
>   https://docs.microsoft.com/aspnet/core/security/
> - **Vynucení ssl v ASP.NET základní aplikaci**  
>   <https://docs.microsoft.com/aspnet/core/security/enforcing-ssl>
> - **Úvod do systému Identity**  
>   <https://docs.microsoft.com/aspnet/core/security/authentication/identity>
> - **Úvod do autorizace**  
>   <https://docs.microsoft.com/aspnet/core/security/authorization/introduction>
> - **Ověřování a autorizace API Apps ve službě Azure App Service**  
>   <https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication>
> - **Server identit**  
>   <https://github.com/IdentityServer>

## <a name="client-communication"></a>Komunikace s klientem

Kromě zobrazování stránek a odpovídání na požadavky na data prostřednictvím webových api mohou aplikace ASP.NET Core komunikovat přímo s připojenými klienty. Tato odchozí komunikace může používat celou řadu dopravních technologií, nejběžnější je WebSockets. ASP.NET Core SignalR je knihovna, která usnadňuje přidávání funkcí komunikace mezi servery v reálném čase do aplikací. SignalR podporuje celou řadu technologií přenosu, včetně WebSockets a abstrahuje mnoho podrobností implementace od vývojáře.

Komunikace klienta v reálném čase, ať už pomocí WebSockets přímo nebo jiné techniky, jsou užitečné v různých scénářích aplikace. Možné příklady:

- Aplikace živé chatovací místnosti

- Monitorování aplikací

- Aktualizace průběhu projektu

- Oznámení

- Aplikace interaktivních formulářů

Při vytváření komunikace klienta do aplikací, obvykle existují dvě součásti:

- Správce připojení na straně serveru (hub SignalR, WebSocketManager WebSocketHandler)

- Knihovna na straně klienta

Klienti nejsou omezeny na prohlížeče – mobilní aplikace, konzolové aplikace a další nativní aplikace mohou také komunikovat pomocí SignalR/WebSockets. Následující jednoduchý program odráží veškerý obsah odeslaný do chatovací aplikace do konzoly jako součást ukázkové aplikace WebSocketManager:

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

Zvažte způsoby, jakými vaše aplikace komunikují přímo s klientskými aplikacemi, a zvažte, zda by komunikace v reálném čase zlepšila uživatelské prostředí vaší aplikace.

> ### <a name="references--client-communication"></a>Reference – komunikace s klientem
>
> - **ASP.NET Core SignalR**  
>   <https://github.com/dotnet/aspnetcore/tree/master/src/SignalR>
> - **Správce websocketů**  
>   https://github.com/radu-matei/websocket-manager

## <a name="domain-driven-design--should-you-apply-it"></a>Návrh řízený doménou – Měli byste jej použít?

Domain-Driven Design (DDD) je agilní přístup k vytváření softwaru, který klade důraz na zaměření na _obchodní doménu_. Klade velký důraz na komunikaci a interakci s odborníky na obchodní doménu, kteří se mohou vztahovat k vývojářům, jak funguje reálný systém. Pokud například vytváříte systém, který zpracovává obchody s akciemi, může být váš odborník na doménu zkušeným burzovním makléřem. DDD je navržen tak, aby řešit velké, složité obchodní problémy, a často není vhodný pro menší, jednodušší aplikace, jako investice do pochopení a modelování domény nestojí za to.

Při vytváření softwaru podle přístupu DDD by váš tým (včetně netechnických zúčastněných stran a přispěvatelů) měl vyvinout _všudypřítomný jazyk_ pro problémový prostor. To znamená, že stejná terminologie by měla být použita pro koncept reálného světa, který je modelován, ekvivalent softwaru a všechny struktury, které mohou existovat k zachování konceptu (například databázové tabulky). Proto pojmy popsané v všudypřítomném jazyce by měly tvořit základ pro _model domény_.

Model domény se skládá z objektů, které vzájemně spolupracují a představují chování systému. Tyto objekty mohou spadat do následujících kategorií:

- [Entity](https://deviq.com/entity/), které představují objekty s podprocesem identity. Entity jsou obvykle uloženy v trvalost s klíčem, kterým mohou být později načteny.

- [Agregace](https://deviq.com/aggregate-pattern/), které představují skupiny objektů, které by měly být trvalé jako celek.

- [Hodnota objekty](https://deviq.com/value-object/), které představují koncepty, které lze porovnat na základě součtu jejich hodnoty vlastností. Například DateRange skládající se z počátečního a koncového data.

- [Události domény](https://martinfowler.com/eaaDev/DomainEvent.html), které představují věci, které se dějí v rámci systému a které jsou zajímavé pro jiné části systému.

Model domény DDD by měl zapouzdřit složité chování v rámci modelu. Entity by zejména neměly být pouze sbírkami vlastností. Pokud model domény postrádá chování a pouze představuje stav systému, říká se, že je [chudokrevný model](https://deviq.com/anemic-model/), což je nežádoucí v DDD.

Kromě těchto typů modelů DDD obvykle používá různé vzory:

- [Úložiště](https://deviq.com/repository-pattern/), pro abstrakce podrobnosti trvalosti.

- [Factory](https://en.wikipedia.org/wiki/Factory_method_pattern), pro zapouzdření vytvoření složitých objektů.

- Události domény pro oddělení závislé chování od spouštění chování.

- [služby](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/), pro zapouzdření podrobností o komplexním chování nebo implementaci infrastruktury.

- [příkazu](https://en.wikipedia.org/wiki/Command_pattern)pro oddělení vydávání příkazů a provádění samotného příkazu.

- [Specifikace](https://deviq.com/specification-pattern/), pro zapouzdření podrobností o dotazu.

DDD také doporučuje použití architektury čištění popsané dříve, umožňující volné párování, zapouzdření a kód, který lze snadno ověřit pomocí testování částí.

### <a name="when-should-you-apply-ddd"></a>Kdy byste měli použít DDD

DDD je vhodný pro velké aplikace s významnou obchodní (nejen technickou) složitostí. Aplikace by měla vyžadovat znalosti odborníků na doménu. V samotném modelu domény by mělo být významné chování představující obchodní pravidla a interakce nad rámec pouhého ukládání a načítání aktuálního stavu různých záznamů z úložišť dat.

### <a name="when-shouldnt-you-apply-ddd"></a>Kdy byste neměli použít DDD

DDD zahrnuje investice do modelování, architektury a komunikace, které nemusí být oprávněné pro menší aplikace nebo aplikace, které jsou v podstatě jen CRUD (vytvořit / číst / aktualizovat / odstranit). Pokud se rozhodnete přistupovat k aplikaci po DDD, ale zjistíte, že vaše doména má chudokrevný model bez chování, možná budete muset přehodnotit svůj přístup. Buď vaše aplikace nemusí potřebovat DDD, nebo budete potřebovat pomoc refaktoring aplikace zapouzdřit obchodní logiku v modelu domény, nikoli v databázi nebo uživatelskérozhraní.

Hybridní přístup by bylo použít pouze DDD pro transakční nebo složitější oblasti aplikace, ale ne pro jednodušší CRUD nebo jen pro čtení části aplikace. Například nemusíte mít omezení Agregace, pokud dotazujete data k zobrazení sestavy nebo k vizualizaci dat pro řídicí panel. Je naprosto přijatelné mít samostatný, jednodušší model čtení pro takové požadavky.

> ### <a name="references--domain-driven-design"></a>Odkazy – návrh řízený doménou
>
> - **DDD v jednoduché angličtině (StackOverflow Odpověď)**  
>   <https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488>

## <a name="deployment"></a>Nasazení

Existuje několik kroků zapojených do procesu nasazení ASP.NET základní aplikace, bez ohledu na to, kde bude hostována. Prvním krokem je publikovat aplikaci, kterou lze `dotnet publish` provést pomocí příkazu CLI. Tím se zkompiluje aplikace a umístí všechny soubory potřebné ke spuštění aplikace do určené složky. Při nasazení z visual studia se tento krok provede automaticky. Složka publikování obsahuje soubory EXE a DLL pro aplikaci a její závislosti. Samostatná aplikace bude také obsahovat verzi běhu .NET. ASP.NET základní aplikace budou také obsahovat konfigurační soubory, statické prostředky klienta a zobrazení MVC.

ASP.NET Základní aplikace jsou konzolové aplikace, které musí být spuštěny při spuštění a restartování serveru, pokud dojde k chybě aplikace (nebo serveru). K automatizaci tohoto procesu lze použít správce procesů. Nejběžnější procesní manažeři pro ASP.NET Core jsou Nginx a Apache na Linuxu a IIS nebo Windows Service v systému Windows.

Kromě správce procesů mohou aplikace ASP.NET Core používat reverzní proxy server. Reverzní proxy server přijímá požadavky HTTP z Internetu a předává je Kestrel po nějaké předběžné zpracování. Reverzní proxy servery poskytují vrstvu zabezpečení pro aplikaci. Kestrel také nepodporuje hostování více aplikací na stejném portu, takže techniky, jako jsou hlavičky hostitele, s ním nelze použít k povolení hostování více aplikací na stejném portu a IP adrese.

![Poštolka k internetu](./media/image7-5.png)

**Obrázek 7-5**. ASP.NET hostované v Kestrelu za reverzním proxy serverem

Dalším scénářem, ve kterém může být užitečný reverzní proxy server, je zabezpečení více aplikací pomocí protokolu SSL/HTTPS. V takovém případě by pouze reverzní proxy server musel mít nakonfigurovaný SSL. Komunikace mezi reverzní proxy server a Kestrel by mohla probíhat přes HTTP, jak je znázorněno na obrázku 7-6.

![ASP.NET hostované za serverem reverzního proxy serveru zabezpečeného protokolem HTTPS](./media/image7-6.png)

**Obrázek 7-6**. ASP.NET hostované za serverem reverzního proxy serveru zabezpečeného protokolem HTTPS

Stále populárnější přístup je hostování aplikace ASP.NET Core v kontejneru Dockeru, který pak může být hostovaný místně nebo nasazený do Azure pro cloudový hosting. Kontejner Dockeru může obsahovat kód aplikace, spuštěný na Kestrelu a bude nasazen za reverzní proxy server, jak je znázorněno výše.

Pokud hostujete svou aplikaci v Azure, můžete použít Microsoft Azure Application Gateway jako vyhrazené virtuální zařízení k poskytování několika služeb. Kromě toho, že funguje jako reverzní proxy pro jednotlivé aplikace, aplikace gateway může také nabídnout následující funkce:

- Http vyrovnávání zatížení

- SSL redikace (SSL pouze k Internetu)

- Ssl od konce ke konci

- Směrování na více sítích (konsolidace až 20 sítí na jedné aplikační bráně)

- Brána firewall webových aplikací

- Podpora pro Websocket

- Pokročilá diagnostika

_Další informace o možnostech nasazení Azure najdete v [kapitole 10](development-process-for-azure.md)._

> ### <a name="references--deployment"></a>Reference – nasazení
>
> - **Přehled hostování a nasazení**  
>   <https://docs.microsoft.com/aspnet/core/publishing/>
> - **Kdy použít Kestrel s reverzním proxy serverem**  
>   <https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy>
> - **Hostování aplikací ASP.NET jádra v Dockeru**  
>   <https://docs.microsoft.com/aspnet/core/publishing/docker>
> - **Představujeme aplikační bránu Azure**  
>   <https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction>

>[!div class="step-by-step"]
>[Předchozí](common-client-side-web-technologies.md)
>[další](work-with-data-in-asp-net-core-apps.md)
