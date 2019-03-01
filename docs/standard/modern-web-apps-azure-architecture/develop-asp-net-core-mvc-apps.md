---
title: Vývoj aplikace ASP.NET Core MVC aplikace
description: Navrhování moderních webových aplikací pomocí ASP.NET Core a Azure | vývoj aplikací ASP.NET Core MVC
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 3ab7de919ed98df1d3fcda02772ba66f9d6294ae
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978329"
---
# <a name="develop-aspnet-core-mvc-apps"></a>Vývoj aplikace ASP.NET Core MVC aplikace

> "Není důležité, chcete-li získat správný, poprvé. Je životně důležitá, chcete-li získat správný, čas posledního."  
> _– Andrew Hunt a David Thomas_

ASP.NET Core je různé platformy, open source architektura pro vytváření moderních optimalizovaných cloudů webových aplikací. Aplikace ASP.NET Core je Odlehčená a modulární a s integrovanou podporou pro vkládání závislostí, umožní větší testovatelnost a udržovatelnost. V kombinaci s MVC, která podporuje vytváření moderních webových rozhraní API kromě aplikace založené na zobrazení, ASP.NET Core je výkonnou architekturu, pomocí kterého se má tvorbu podnikových webových aplikací.

## <a name="mvc-and-razor-pages"></a>MVC a stránky Razor

ASP.NET Core MVC nabízí mnoho funkcí, které jsou užitečné pro vytváření webových rozhraní API a aplikace. Výraz MVC zastupuje "Model-View-Controller", vzoru uživatelského rozhraní, které rozdělí odpovědnosti reagování na žádosti uživatele do několika částí. Kromě dodržení tohoto modelu, můžete taky implementovat funkce v aplikacích ASP.NET Core jako stránky Razor. Stránky Razor jsou integrované do ASP.NET Core MVC a použít stejné funkce pro směrování, vazby modelu atd. Namísto nutnosti samostatné složky a soubory pro Kontrolery, zobrazení a podobně a používající směrování na základě atributů, ale pro stránky Razor jsou umístěny v jedné složce ("/ stránky"), směrování na základě jejich relativní umístění v této složce a popisovač požadavků s obslužnými rutinami místo akce kontroleru.

Při vytváření nové aplikace ASP.NET Core, měli byste mít plán v úvahu pro typ aplikace, kterou chcete sestavit. V sadě Visual Studio budete vybírat několik šablon. Tři nejběžnější šablony projektu jsou webové rozhraní API, webové aplikace a webové aplikace (Model-View-Controller). I když toto rozhodnutí lze vytvořit pouze při prvním vytvoření projektu, není nezvratná rozhodnutí. Projekt webového rozhraní API používá standardní Model-View-Controller řadiče – stačí chybí zobrazení ve výchozím nastavení. Výchozí šablony webové aplikace podobně, používá Razor Pages a proto také nemá zobrazení složky. Zobrazení složky můžete přidat později k podpoře chování na základě zobrazení těchto projektů. Projekty webového rozhraní API a Model-View-Controller nezahrnují složce stránky ve výchozím nastavení, ale můžete přidat později k podpoře chování na základě stránky Razor. Si můžete představit jako podporuje tři různé druhy interakci s uživatelem výchozí tyto tři šablony: data (webového rozhraní API), na stránce a na základě zobrazení. Můžete však kombinovat a párovat některé nebo všechny z nich v rámci jednoho projektu, pokud chcete.

### <a name="why-razor-pages"></a>Proč pro stránky Razor?

Stránky Razor je výchozí metoda pro nové webové aplikace v sadě Visual Studio. Stránky Razor nabízí jednodušší způsob, jak vytvářet aplikace založené na stránce funkce, jako jsou formuláře – jednostránková aplikace. Použití kontrolerů a zobrazení, je běžné, že aplikace má velmi velké řadiče ve spolupráci s mnoha různých závislostí a Zobrazit modely a vrátí mnoho různých zobrazení. To vedlo spoustu složitost a často za následek řadiče, které nebyly postupujte podle jednoho zásady odpovědnosti nebo zásady Open/uzavřeno efektivně. Stránky Razor řeší tento problém zapouzdřením logiku na straně serveru pro danou logickou "stránku" ve webové aplikaci s jeho kód Razor. Stránka Razor, která nemá žádné logiku na straně serveru se může skládat jednoduše Razor souboru (například "Index.cshtml"). Většina netriviální Razor Pages však bude mít třídu modelu stránku, který bude pojmenován stejně jako Razor soubor s příponou "cs" (například "Index.cshtml.cs").

Stránka Razor model stránky kombinuje odpovědnosti kontroler MVC a viewmodel. Namísto zpracování požadavků pomocí metody akce kontroleru, jsou spouštěny obslužných rutin modelu stránky jako "OnGet()" vykreslování jejich přidružené stránky ve výchozím nastavení. Stránky Razor zjednodušuje proces vytváření jednotlivé stránky v aplikaci ASP.NET Core, současně stále zajišťuje všechny funkce architektury ASP.NET Core MVC. Jsou to dobrá výchozí volba pro nové funkce založené na stránce.

### <a name="when-to-use-mvc"></a>Kdy použít MVC

Pokud vytváříte webové rozhraní API, vzor MVC vhodnější než pokusu o použití stránek Razor. Pokud váš projekt bude vystavovat jenom koncové body webové rozhraní API, měli byste v ideálním případě začít ze šablony projektu webového rozhraní API, ale jinak je jednoduše přidávat řadiče a přidružené koncové body rozhraní API pro jakoukoli aplikaci ASP.NET Core. Také byste měli použít přístup založený na zobrazení MVC, pokud migrujete existující aplikace v ASP.NET MVC 5 nebo dříve k ASP.NET Core MVC a chcete provést s minimální množství úsilí. Po počáteční migraci, můžete si vyzkoušet, zda je vhodné přijmout stránky Razor pro nové funkce nebo dokonce i jako velkoobchodního migrace.

Jestli si sestavení webové aplikace pomocí nástroje Razor Pages a zobrazení MVC, vaše aplikace bude mít podobným výkonem a bude zahrnovat podporu pro vkládání závislostí, filtry, vazby modelu a ověření atd.

## <a name="mapping-requests-to-responses"></a>Mapování požadavků na reakce

Aplikace ASP.NET Core svou podstatou mapování příchozích požadavků na odchozí odpovědi. Na nízké úrovni používá se k tomu middleware a jednoduché aplikace ASP.NET Core a mikroslužeb může být složená výhradně z vlastního middlewaru. Při použití technologie ASP.NET Core MVC, můžete pracovat se o něco vyšší úrovně, uvažujete z hlediska _trasy_, _řadiče_, a _akce_. Jednotlivých příchozích požadavků je ve srovnání s směrovací tabulky aplikace, a pokud je nalezen odpovídající trasy, přidružená metoda akce (patří do kontroleru) se nazývá žádost zpracovat. Pokud není nalezen žádný odpovídající trasy, je volána obslužná rutina chyby (v tomto případě vrácením výsledku NotFound).

ASP.NET Core MVC aplikace můžou používat konvenční trasy a trasy atributů. Konvenční trasy, které jsou definovány v kódu, určení směrování _konvence_ pomocí syntaxe jako v následujícím příkladu:

```csharp
app.UseMvc(routes =>;
{
    routes.MapRoute("default","{controller=Home}/{action=Index}/{id?}");
});
```

V tomto příkladu se přidala do směrovací tabulky trasa s názvem "Výchozí". Definuje šablonu trasy se zástupnými symboly pro _řadič_, _akce_, a _id_. Zástupné symboly kontroleru a akce mají výchozí zadaná ("Home" a "Index", v uvedeném pořadí), a zástupný symbol id je volitelný (základě "?" použit). Tato konvence jsou zde definovány stavy, které by měl odpovídat první část žádost o název kontroleru, druhá část na akci, a pak v případě potřeby třetí části bude reprezentovat pomocí parametru id. Konvenční trasy jsou obvykle definovány na jednom místě aplikace, jako v metodě konfigurace v třída při spuštění.

Trasy atributů jsou přímo použít pro kontrolery a akce, spíše než zadané globálně. Tato akce nemá výhodou, že je mnohem snadnější když se podíváte na konkrétní metody, ale znamená, že informace o směrování se uchovávat na jednom místě v aplikaci. Atribut trasy je můžete snadno zadat několik tras pro danou akci, jakož i kombinovat trasy mezi kontrolery a akce. Příklad:

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

Trasy se dá nastavit na [HttpGet] a podobně jako atributy, takže není nutné přidat samostatné atributy [trasy]. Atribut trasy můžete také použít tokeny omezit opakovat názvy kontroler nebo akce, jak je znázorněno níže:

```csharp
[Route("[controller\]")]
public class ProductsController : Controller
{
    [Route("")] // Matches 'Products'
    [Route("Index")] // Matches 'Products/Index'
    public IActionResult Index() {}
}
```

Stránky Razor nepoužívá směrováním atributů. Informace o šabloně další trasy pro stránky Razor můžete zadat jako součást jeho `@page` – direktiva:

```csharp
@page "{id:int}"
```

V předchozím příkladu by odpovídala příslušná stránka trasu s celým číslem `id` parametru. Například *Products.cshtml* stránky umístěný v kořenovém adresáři `/Pages` bude mít tato trasa:

```csharp
"/Products/123"
```

Jakmile danou žádost pravá složená závorka k trase, ale před akci, metoda je volána, ASP.NET Core MVC provede [vazby modelu](/aspnet/core/mvc/models/model-binding) a [ověření modelu](/aspnet/core/mvc/models/validation) v požadavku. Vazby modelu je zodpovědný za převod příchozích dat protokolu HTTP na typy .NET zadány jako parametry metody akce má být volána. Například pokud metoda akce očekává parametr id int, vazby modelu se pokusí zadejte tento parametr z hodnoty zadané jako součást požadavku. Uděláte to tak, vazby modelu hledá hodnoty v odeslaného formuláře, hodnoty v trase, samotného a hodnoty řetězce dotazu. Za předpokladu, že je hodnota id nenajde, převede se na celé před předáním do metody akce.

Po vytvoření vazby modelu, ale před voláním metody akce dojde k ověření modelu. Ověření modelu používá volitelné atributy typu modelu a pomáhají zajistit, že objekt zadaného modelu vyhovuje určitým požadavkům data. Některé hodnoty lze zadat jako povinné, nebo jsou omezena na konkrétní délku nebo číselného rozsahu, atd. Pokud jsou zadané atributy ověřování, ale model není v souladu s jejich požadavky, vlastnost ModelState.IsValid bude mít hodnotu false a sadu ověřovacích pravidel selhání bude možné odeslat klientovi provádějícímu žádost.

Pokud používáte ověření modelu, byste měli vždy zkontrolujte, zda je model platný před provedením jakékoli změny stavu příkazů, ujistěte se, že vaše aplikace není poškozený neplatnými daty. Můžete použít [filtr](/aspnet/core/mvc/controllers/filters) aby se zabránilo nutnosti přidat kód pro tuto v každé akce. Filtry ASP.NET Core MVC nabízí způsob, jak zachycování skupiny požadavků, tak, aby se běžných zásad a převeďte společné aspekty lze použít na základě cílové. Filtry lze použít k jednotlivým akcím, celý řadiče, nebo globálně pro aplikaci.

Pro webová rozhraní API ASP.NET Core MVC podporuje [ _vyjednávání obsahu_](/aspnet/core/mvc/models/formatting), povolíte požadavky k určení, jak by měly být formátovány odpovědi. Založen na záhlavích zadaný v požadavku, bude akce vrácení dat formátu odpovědi v XML, JSON nebo jiný podporovaný formát. Tato funkce umožňuje využívat víc klientů s požadavky na jiný datový formát stejného rozhraní API.

Projekty webového rozhraní API byste zvážit použití `[ApiController]` atribut, který je možné použít k jednotlivým řadičům, třída base kontroleru nebo celé sestavení. Tento atribut přidá ověřování automatické model a všechny akce s neplatný model vrátí chybného požadavku s podrobnostmi chyb ověřování. Atribut vyžaduje taky mít atribut trasy, spíše než použití konvenční trasy všechny akce a vrátí podrobné informace ProblemDetails v reakci na chyby.

> ### <a name="references--mapping-requests-to-responses"></a>Odkazy – mapování vyžádá, aby odpovědi
>
> - **Směrování na akce Kontroleru**
 > <https://docs.microsoft.com/aspnet/core/mvc/controllers/routing>
> - **Vazby modelu**
 > <https://docs.microsoft.com/aspnet/core/mvc/models/model-binding>
> - **Ověření modelu**
 > <https://docs.microsoft.com/aspnet/core/mvc/models/validation>
> - **Filtry**
 > <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - **Atribut objektu ApiController**
 > <https://docs.microsoft.com/aspnet/core/web-api/?view=aspnetcore-2.2>

## <a name="working-with-dependencies"></a>Práce se závislostmi

Má integrovanou podporu pro ASP.NET Core a interně využívá techniky označované jako [injektáž závislostí](/aspnet/core/fundamentals/dependency-injection). Injektáž závislostí je technika, která umožňuje volné párování mezi různé části aplikace. Volnější párování je žádoucí, protože to usnadňuje izolace částí aplikace umožňující testování nebo nahrazení. Je také podstatně tím snížíte pravděpodobnost, že změna v jedné části aplikace bude mít neočekávané dopad někde jinde v aplikaci. Injektáž závislostí je založený na principu inverzi závislostí a často je klíčem k dosažení Princip otevřený/uzavřený. Při vyhodnocování, jak vaše aplikace funguje s jeho závislostí, dávejte ale pozor [statické plevami](https://deviq.com/static-cling/) kódu pach a nezapomeňte, aphorism "[nové je spojovací](https://ardalis.com/new-is-glue)."

Plevami statický nastane, pokud volání statické metody třídy nebo přistupovat ke statické vlastnosti, které mají vedlejší účinky nebo závislosti na infrastruktuře. Například pokud máte metodu, která volá statická metoda, která pak zapisuje do databáze, vaše metoda je těsně spjat s databáze. Cokoli, co toto volání databáze přestane fungovat přeruší metodu. Testování těchto metod je známo, že obtížné, protože tyto testy vyžadují komerční napodobování knihovny k napodobení volání statické, nebo pouze jde testovat pomocí testovací databázi na místě. Statické volání, které nemají žádné závislosti na infrastruktuře, zejména těch, které jsou zcela bezstavové, se dají volat a mít žádný vliv na párování nebo testovatelnosti (nad rámec spojovacího kódu na statické volání sebe sama).

Mnoho vývojářů pochopení rizik statické plevami a globální stav, ale bude stále úzce spojit svůj kód pro konkrétní implementace prostřednictvím přímé vytváření instancí. "Nové je připevnit" má být připomenutí toto párování a obecné odsouzení využívání `new` – klíčové slovo. Stejně jako s volání statické metody, nové instance typů, které nemají žádné externí závislosti obvykle není úzce spárovat kód podrobnosti implementace nebo ztížit testování. Ale pokaždé, když je vytvořena instance třídy, pouze krátkou chvíli trvat zvažte, jestli má smysl pevně kódovat této konkrétní instance v této konkrétní umístění, nebo pokud by bylo lepší návrh požádat o tuto instanci jako závislost.

### <a name="declare-your-dependencies"></a>Deklarace závislostí

ASP.NET Core je postavené na s metody a třídy deklarují jejich závislosti, požadování jako argumenty. Aplikace ASP.NET jsou obvykle nastavené ve třídě spuštění, které je nakonfigurována pro podporu injektáž závislostí v několika fázích. Pokud počáteční třída nemá konstruktor, můžete požádat o závislosti pomocí konstruktoru, například takto:

```csharp
public class Startup
{
    public Startup(IHostingEnvironment env)
    {
        var builder = new ConfigurationBuilder()
        .SetBasePath(env.ContentRootPath)
        .AddJsonFile("appsettings.json", optional: false, reloadOnChange: true)
        .AddJsonFile(\$"appsettings.{env.EnvironmentName}.json", optional: true);
    }
}
```

Třída při spuštění je zajímavé, v tom, že neexistují žádné požadavky na explicitní typ pro něj. Nedědí ze základní třídy speciální spuštění, ani je implementuje žádné konkrétní rozhraní. Můžete jí konstruktor, nebo Ne, a můžete zadat libovolný počet parametrů v konstruktoru chcete. Při spuštění webového hostitele, které jste nakonfigurovali pro vaše aplikace bude volat třída při spuštění, které má použít a pomocí vkládání závislostí naplnit všechny závislosti, které vyžaduje třídu pro spuštění. Samozřejmě pokud jste požádali o parametry, které nejsou nakonfigurované v kontejneru služby používat ASP.NET Core, zobrazí se výjimka, ale tak dlouho, dokud zůstanou závislosti kontejneru ví o, můžete požádat o všechno, co chcete.

Injektáž závislostí je integrovaná do aplikace ASP.NET Core přímo od začátku, při vytváření instancí při spuštění. Nelze zastavit existuje pro třídu pro spuštění. Můžete také požádat o závislosti v metodě konfigurace:

```csharp
public void Configure(IApplicationBuilder app,
    IHostingEnvironment env,
    ILoggerFactory loggerFactory)
{

}
```

Výjimka, která má toto chování je ConfigureServices – metoda je nutné provést pouze jeden parametr typu IServiceCollection. Není nutné ve skutečnosti k podpoře vkládání závislostí, protože na jedné straně je zodpovědný za přidání objektů do kontejneru služby a na druhé má přístup ke všem službám aktuálně nakonfigurovaná prostřednictvím IServiceCollection parametru. Proto můžete pracovat se závislosti definované v kolekci služby ASP.NET Core v každé části třídu pro spuštění, můžete si vyžádat potřebný služby jako parametr nebo práce s IServiceCollection v ConfigureServices.

> [!NOTE]
> Pokud je potřeba zajistit určité služby jsou k dispozici pro vaši třídu pro spuštění, můžete je nakonfigurovat pomocí WebHostBuilder a jeho ConfigureServices metodu.

Třída při spuštění je model jak strukturovat ostatních částech aplikace ASP.NET Core z řadiče s Middlewarem pro filtry, které vlastní služby. V každém případě byste měli postupovat [explicitní závislosti Princip](https://deviq.com/explicit-dependencies-principle/), požadování závislostí místo přímo jejich vytváření a využitím vkládání závislostí v rámci aplikace. Dejte pozor, kde a jak můžete přímo vytvořit instanci implementace, zejména služeb a objektů, které pracují s infrastrukturou nebo mají vedlejší účinky. Dáváte přednost práci s odběry definovaný v základní vaší aplikace a předané jako argumenty hardcoding odkazy na konkrétní implementaci typů.

## <a name="structuring-the-application"></a>Strukturování aplikace

Monolitické aplikace obvykle mají jeden vstupní bod. V případě webové aplikace ASP.NET Core vstupní bod budou webový projekt ASP.NET Core. Nicméně to neznamená, že řešení by měla obsahovat právě jeden projekt. Je užitečné k rozdělení aplikaci do různých vrstev před dalším postupem podle oddělení oblastí zájmu. Jakmile rozdělené do vrstev, je užitečné se dostat nad rámec složky pro oddělení projekty, které může zajistit lepší zapouzdření. Nejlepší metodou k dosažení těchto cílů s aplikací ASP.NET Core je varianta čisté architektuře popsané v kapitole 5. Následující tento přístup aplikace řešení bude tvořit samostatné knihovny uživatelského rozhraní, infrastruktury a ApplicationCore.

Kromě těchto projektů samostatný testovací projekty jsou zahrnuté také (testování je popsáno v kapitole 9).

Objektový model aplikace a rozhraní musí být umístěné ve ApplicationCore projektu. Tento projekt bude mít například několik závislostí nejvíce a ho bude odkazovat jiné projekty v řešení. Obchodní entity, které je potřeba nastavit jako trvalý, jsou definovány v ApplicationCore projektu, jako jsou služby, které přímo nezávisí na infrastrukturu.

Podrobnosti implementace, například jak se provádí trvalého nebo jak může být odeslána oznámení pro uživatele, jsou uloženy v projektu infrastruktury. Tento projekt bude odkazovat na specifický pro implementaci balíčků, jako jsou Entity Framework Core, ale by neměly zveřejňovat informace o těchto implementacích mimo projekt. Služby infrastruktury a úložiště by měly implementovat rozhraní, které jsou definovány v projektu ApplicationCore a jeho implementace trvalost zodpovídají za načítání a ukládání entit, které jsou definovány v ApplicationCore.

Projekt uživatelského rozhraní ASP.NET Core je zodpovědný za jakékoli obavy úrovni uživatelského rozhraní, ale by neměly obsahovat podrobnosti o obchodní logiku nebo infrastruktury. Ve skutečnosti v ideálním případě nemůže i mít závislost na projektu infrastrukturu, která vám pomůže zajistit, že se omylem zavedeny žádné závislosti mezi dva projekty. Toho lze dosáhnout pomocí kontejneru DI třetích stran stejně jako Autofac, který umožňuje definovat DI pravidla v modulu třídy v každém projektu.

Dalším přístupem k oddělení aplikace od podrobností implementace je mikroslužby volání aplikace, možná nasazený v jednotlivých kontejnerech Dockeru. To poskytuje ještě větší oddělení otázky a oddělení než využitím DI mezi dva projekty, ale má další složitosti.

### <a name="feature-organization"></a>Funkce organizace

Aplikace ASP.NET Core ve výchozím nastavení, uspořádejte jejich strukturu složek Kontrolerů a zobrazení a často modely ViewModel. Kód na straně klienta pro podporu těchto struktur na straně serveru jsou obvykle uložená samostatně ve složce wwwroot. Však velké aplikace setkat s problémy u této organizace, protože pracující na jakékoli dané funkce často vyžaduje přechod mezi tyto složky. Načte mnohem obtížnější, roste počet souborů a podsložek v každé složky, což vede k spoustu posouvání se v Průzkumníku řešení. Jedním řešením tohoto problému, je uspořádat kód aplikace podle _funkce_ místo podle typu souboru. Tento styl organizace se obvykle označuje jako funkce složky nebo [funkce řezy](https://msdn.microsoft.com/magazine/mt763233.aspx) (viz také: [Svislé řezy](https://deviq.com/vertical-slices/)).

ASP.NET Core MVC podporuje oblasti pro tento účel. Pomocí oblastí, můžete vytvořit samostatné sady Kontrolerů a zobrazení složek (stejně jako jakékoli přidružených modelech) v každé oblasti složky. Obrázek 7-1 znázorňuje strukturu složky příklad používat.

![](./media/image7-1.png)

Obrázek 7-1 ukázka oblasti organizace

Při použití oblasti, je nutné použít atributy k vyplnění řadičích s názvem oblast, do které patří:

```csharp
[Area("Catalog")]
public class HomeController
{}
```

Potřebujete také přidává oblast na trasy:

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

Kromě integrované podpory pro oblasti můžete také použít vlastní strukturu složek a konvence místo atributy a vlastní trasy. To by umožnilo mít funkce složky, které nezahrnuli samostatné složky pro zobrazení, Kontrolery, atd., udržování hierarchii plošší a usnadnit tak vidět, že všechny související soubory na jednom místě pro jednotlivé funkce.

ASP.NET Core používá konvence integrované typy mohla kontrolovat své chování. Můžete změnit nebo nahraďte tyto konvence. Můžete například vytvořit konvence, automaticky získá název funkce pro daný kontroler podle jeho obor názvů (což obvykle souvisí s složku, ve kterém se nachází kontroler):

```csharp
FeatureConvention : IControllerModelConvention
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

Potom zadejte tyto vytváření názvů jako možnost při přidání podpory pro rozhraní MVC do vaší aplikace v ConfigureServices:

```csharp
services.AddMvc(o => o.Conventions.Add(new FeatureConvention()));
```

ASP.NET Core MVC také používá konvence pro vyhledání zobrazení. Lze jej přepsat pomocí vlastních konvence tak, aby zobrazení budou umístěny ve složkách funkci (pomocí názvu funkce poskytované FeatureConvention, výše). Další informace o tento přístup a stáhnout ukázku práce z článku na webu MSDN můžete [řezy funkce pro ASP.NET Core MVC](https://msdn.microsoft.com/magazine/mt763233.aspx).

### <a name="cross-cutting-concerns"></a>Související aspekty

S růstem aplikace stává čím dál důležitějším zohlednit si vyskytující aspekty k vyloučení duplicity a zajistit konzistenci. Některé příklady vyskytující aspekty aplikace ASP.NET Core se ověřování modelu ověřovacích pravidel, ukládání výstupu do mezipaměti a zpracování chyb, když existuje řada dalších. ASP.NET Core MVC [filtry](/aspnet/core/mvc/controllers/filters) umožňuje spuštění kódu před nebo po určité kroky v kanálu zpracování požadavků. Například filtr můžete spustit před a po vytvoření vazby modelu před a po akci, nebo před a po výsledku akce. Můžete také použít filtr autorizace pro řízení přístupu k rest z kanálu. Obrázky 7-2 ukazuje jak požadavek spuštění toků filtry, pokud nakonfigurované.

![Žádost se zpracovává prostřednictvím filtry autorizace, prostředků filtry, vazby modelu, filtry akce, provedení akce a převod výsledek akce, filtry výjimek, filtry výsledků a výsledek spuštění. Na cestě navýšení kapacity pouze zpracuje požadavek výsledek filtry a filtry prostředků než se náplní odpověď zaslána klientovi.](./media/image7-2.png)

Obrázek 7-2 provádění požadavku prostřednictvím kanálu požadavku a filtry.

Filtry jsou obvykle implementovány jako atributy, takže je lze následně použít na řadiče nebo akce (nebo dokonce globálně). Když se přidá tímto způsobem, filtry na úrovni akce přepsání nebo jsou postavené na úrovni kontroleru, filtrů které samy přepsat globální filtry. Například \[trasy\] atribut lze použít k vytvoření trasy mezi kontrolery a akce. Obdobně autorizace můžete nakonfigurovat na úrovni kontroleru a poté přepsána jednotlivé akce, jak ukazuje následující příklad:

```csharp
[Authorize]
public class AccountController : Controller

{
    [AllowAnonymous] // overrides the Authorize attribute
    public async Task<IActionResult> Login() {}
    public async Task<IActionResult> ForgotPassword() {}
}
```

První metoda přihlášení, využívá filtr AllowAnonymous (atribut) k přepsání filtru Authorize nastavená na úrovni kontroleru. Akce ForgotPassword (a další akce v třídě, která nemá atribut AllowAnonymous) bude vyžadovat ověřeného požadavku.

Filtry lze použít k vyloučení duplicity v podobě běžnou chybou zpracování zásady pro rozhraní API. Typické zásad rozhraní API je například vrátit NotFound reakci na požadavky odkazující na klíče, které neexistují a odpověď chybného požadavku, pokud selže ověření modelu. Následující příklad znázorňuje tyto dvě zásady v akci:

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

Nepovolit metody akce pro zaplní podmíněný kód tímto způsobem. Místo toho o přijetí změn zásad do filtry, které mohou být použity na základě podle potřeby. Kontrola ověření modelu, které se budou objevovat pokaždé, když je odeslán příkaz k rozhraní API, můžete v tomto příkladu nahrazuje následující atribut:

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

Můžete přidat `ValidateModelAttribute` do projektu jako závislost NuGet zahrnutím [Ardalis.ValidateModel](https://www.nuget.org/packages/Ardalis.ValidateModel) balíčku. Pro rozhraní API, můžete použít `ApiController` atribut k vynucení tohoto chování bez nutnosti samostatné `ValidateModel` filtru.

Filtr lze, zkontrolujte, zda existuje záznam a vrátit kód 404, před provedením akce, takže odpadá potřeba k provedení těchto kontrol v akci. Po výseče běžné konvence a uspořádané řešení k oddělení infrastruktury kódu a obchodní logiku z vašeho uživatelského rozhraní, by měla být velmi dynamicky vaše metody akce MVC:

```csharp
[HttpPut("{id}")]
[ValidateAuthorExists]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

Další informace o implementaci filtry a stáhněte si ukázky práce z článku na webu MSDN [skutečných ASP.NET Core MVC filtry](https://msdn.microsoft.com/magazine/mt767699.aspx).

> ### <a name="references--structuring-applications"></a>Odkazy – strukturování aplikací
>
> - **Oblasti**  
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/areas>
> - **Zpravodaj MSDN Magazine – funkce řezy pro ASP.NET Core MVC**  
>   <https://msdn.microsoft.com/magazine/mt763233.aspx>
> - **Filtry**  
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - **MSDN – filtry reálného světa ASP.NET Core MVC**  
>   <https://msdn.microsoft.com/magazine/mt767699.aspx>

## <a name="security"></a>Zabezpečení

Zabezpečení webových aplikací je velké tématu, s mnoha aspekty. Na nejzákladnější úrovni zabezpečení je nutné si ověřit, budete vědět, kdo je pocházející z daného požadavku a pak zajistit, že žádost má jenom přístup k prostředkům, které by měl. Ověřování provádí porovnání se žádostí o těch v úložišti důvěryhodných dat, pokud chcete zobrazit, pokud požadavek má být považována za pocházející ze známého entity zadané přihlašovací údaje. Autorizace je proces omezení přístupu k určitým prostředkům na základě identity uživatele. Třetí potíže se zabezpečením chrání požadavky z odposlouchávání třetími stranami, u kterých byste měli aspoň [Ujistěte se, že se vaše aplikace používá protokol SSL](/aspnet/core/security/enforcing-ssl).

### <a name="authentication"></a>Ověřování

ASP.NET Core Identity je systém členství, které lze použít k podpoře funkce přihlášení pro aplikaci. Obsahuje podporu pro místní uživatelské účty a externí přihlášení zprostředkovatele podpory od poskytovatelů, jako je Microsoft Account, Twitter, Facebook, Google a další. Kromě ASP.NET Core Identity vaší aplikace můžete použít ověřování systému windows nebo zprostředkovatele identit třetích stran, jako jsou [serveru identit](https://github.com/IdentityServer/IdentityServer4).

ASP.NET Core Identity je součástí nové šablony projektu, pokud je vybraná možnost jednotlivé uživatelské účty. Tato šablona obsahuje podporu pro registrace, přihlášení, externí přihlášení, zapomenutí hesel a další funkce.

![](./media/image7-3.png)

Obrázek 7 – 3 vyberte jednotlivé uživatelské účty do mít identitu předkonfigurované.

Podpora identit je nakonfigurovaný v po spuštění, v ConfigureServices i konfigurace:

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

Je důležité, že UseIdentity předcházet UseMvc v metodě konfigurace. Při konfiguraci Identity v ConfigureServices, Všimněte si volání AddDefaultTokenProviders. Tato akce nemá nic společného s tokeny, které slouží k zabezpečení komunikace webových, ale místo toho odkazuje na zprostředkovatele, které vytvářejí výzvy, které je možné odeslat uživatelům přes zprávu SMS nebo e-mailu je potvrdit svou identitu.

Další informace o [konfiguraci dvojúrovňového ověřování](/aspnet/core/security/authentication/2fa) a [povolení zprostředkovatele externí přihlášení](/aspnet/core/security/authentication/social/) z oficiální dokumentace ASP.NET Core.

### <a name="authorization"></a>Autorizace

Nejjednodušší forma autorizace zahrnuje omezení přístupu pro anonymní uživatele. Toho lze dosáhnout jednoduše použitím \[Authorize\] atribut na některých řadičích nebo akce. Pokud role se používají, je atribut dále rozšířit k omezení přístupu k uživatelům patřícím do určité role, jak je znázorněno:

```csharp
[Authorize(Roles = "HRManager,Finance")]
public class SalaryController : Controller
{

}
```

V takovém případě uživatelé, kteří patří do role HRManager nebo Finance (nebo obojí) by měli SalaryController. Vyžadovat, aby uživatel patřit do více rolí (nikoli pouze jeden z několika), můžete použít atribut několikrát, pokaždé, když zadáte požadované role.

Určení určité sady rolí jako řetězce v mnoha různých kontrolery a akce může mít za následek nežádoucí opakování. Můžete nakonfigurovat zásady autorizace, které zapouzdřují autorizační pravidla, a pak zadejte zásady namísto jednotlivých rolí při použití \[Authorize\] atribut:

```csharp
[Authorize(Policy = "CanViewPrivateReport")]
public IActionResult ExecutiveSalaryReport()
{
    return View();
}
```

Tímto způsobem pomocí zásad, můžete oddělit typy akcí se s omezením pomocí specifikátoru z konkrétní role nebo pravidla, která se použije na ni. Později, pokud vytvoříte novou roli, kterou je potřeba mít přístup k určitým prostředkům, můžete jen aktualizovat zásady, nikoli aktualizovat každý seznam rolí na každý \[Authorize\] atribut.

#### <a name="claims"></a>deklarace identity

Deklarace identity jsou páry název-hodnota, které představují vlastnosti ověřeného uživatele. Například může ukládat číslo zaměstnance uživatelů jako deklarace identity. Deklarace identity je pak možné jako součást zásad autorizace. Můžete vytvořit zásadu s názvem "EmployeeOnly", který vyžaduje existenci deklaraci identity nazývá "Rovnítkem", jak je znázorněno v tomto příkladu:

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

Tato zásada může pak lze použít \[Authorize\] atribut k ochraně všech kontroleru a akce, jak je popsáno výše.

#### <a name="securing-web-apis"></a>Zabezpečení webového rozhraní API

Většina webových rozhraní API by měla implementovat systém ověřování založené na tokenech. Ověřování pomocí tokenu je bezstavové a navržená tak, aby byla škálovatelná. V systému, ověřování založené na tokenech musí klient nejdřív ověřit zprostředkovatele ověřování. V případě úspěšného ověření klienta vystaví token, který je jednoduše kryptograficky smysluplné řetězce znaků. Když klient potřebuje potom vydat požadavek na rozhraní API, přidá tento token jako záhlaví v žádosti. Server pak ověří daný token nalezen v hlavičce požadavku před dokončením žádosti. Obrázek 7 – 4 ukazuje tento proces.

![TokenAuth](./media/image7-4.png)

**Obrázek 7 – 4.** Ověřování založené na tokenech pro webová rozhraní API.

Můžete vytvořit vlastní ověřovací službu, integrace s Azure AD a OAuth, nebo implementace služby pomocí open source nástroj jako [IdentityServer](https://github.com/IdentityServer).

#### <a name="custom-security"></a>Vlastní zabezpečení

Buďte opatrní hlavně o implementaci šifrování, členství uživatele nebo systému generování tokenů "se zajištěním provozu vlastní". Existuje mnoho obchodní a open source alternativy k dispozici, které se mají téměř jistě lepší zabezpečení než vlastní implementaci.


> ### <a name="references--security"></a>Odkazy – zabezpečení
>
> - **Přehled dokumentace zabezpečení**  
>   https://docs.microsoft.com/aspnet/core/security/
> - **Vynucování SSL v aplikaci ASP.NET Core**  
>   <https://docs.microsoft.com/aspnet/core/security/enforcing-ssl>
> - **Úvod do systému Identity**  
>   <https://docs.microsoft.com/aspnet/core/security/authentication/identity>
> - **Úvod k ověřování**  
>   <https://docs.microsoft.com/aspnet/core/security/authorization/introduction>
> - **Ověřování a autorizace API Apps ve službě Azure App Service**  
>   <https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication>
> - **Serveru identit**  
>   <https://github.com/IdentityServer>

## <a name="client-communication"></a>Komunikace klienta

Kromě poskytování stránky a reagování na žádosti o data prostřednictvím webových rozhraní API, aplikace ASP.NET Core může komunikovat přímo s připojenými klienty. Tato odchozí komunikaci, můžete použít širokou škálu technologií přenosu nejčastěji používané jsou objekty Websocket. Funkce SignalR technologie ASP.NET Core je knihovna, která umožňuje snadno přidat funkce komunikaci v reálném čase klient a server pro vaše aplikace. Funkce SignalR, podporuje různé přenosové technologií, včetně protokoly Websocket a abstrahuje tokeny n Podrobnosti implementace od vývojáře.

Funkce SignalR technologie ASP.NET Core je k dispozici s ASP.NET Core od verze 2.1.

Komunikace v reálném čase klienta, jestli přes WebSockets přímo nebo jinými technikami, jsou užitečné v různých scénářích aplikací. Možné příklady:

- Konverzační živých aplikací

- Monitorování aplikací

- Aktualizace průběhu úlohy

- Oznámení

- Interaktivní formulářových aplikací

Při sestavování komunikaci s klienty do svých aplikací, jsou obvykle dvě součásti:

- Správce připojení na straně serveru (rozbočovače SignalR, WebSocketManager WebSocketHandler)

- Klientské knihovny

Klienti nejsou omezené na prohlížeče – mobilních aplikací, aplikací konzoly a další nativní aplikace můžou taky komunikovat pomocí SignalR/Websocket. Následující jednoduchý program vypisuje všechny obsah odeslaný do chatovací aplikaci do konzoly, jako součást WebSocketManager ukázkovou aplikaci:

```csharp
public class Program
{
    private static Connection _connection;
    public static void Main(string[] args)
    {
        StartConnectionAsync();
        _connection.On("receiveMessage", (arguments) =>;
        {
            Console.WriteLine(\$"{arguments\[0\]} said: {arguments\[1\]}");
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

Vezměte v úvahu, že prostředí způsoby, ve kterých vaše aplikace komunikovat přímo pomocí klientských aplikací a zvažte, jestli komunikaci v reálném čase by mohly zlepšit uživatele vaší aplikace.

> ### <a name="references--client-communication"></a>Odkazy – komunikace klienta
>
> - **ASP.NET Core SignalR**  
>   <https://github.com/aspnet/SignalR>
> - **WebSocket Manager**  
>   https://github.com/radu-matei/websocket-manager

## <a name="domain-driven-design--should-you-apply-it"></a>Návrhy řízené doménou – by je použijete?

Řízené doménou návrhu (DDD) je agilní přístup k vytváření softwaru, který zvýrazňuje zaměření na _obchodní domény_. Umístí velkým důrazem na komunikaci a interakci s expert(s) obchodní domény, který souviset s vývojáři fungování systému reálného světa. Například pokud sestavujete systému, který zpracovává burzovních, odborníky vaší domény může být zkušení uložených zprostředkovatele. DDD je navržená k řešení složitých obchodních problémů a není často vhodná pro menší, jednodušší aplikací, jako investice vysvětlující Princip fungování a modelování domény není vhodné ho.

Při sestavování softwaru přístupu DDD, by měl vývoj vašeho týmu (včetně netechnické zúčastněných stran a přispěvatelé) _všudypřítomná jazyk_ prostoru problém. To znamená stejné terminologie by měla sloužit pro každodenní praxe koncept modelovaných, ekvivalent softwaru a všech struktur, které mohou existovat k uchování koncept (například tabulek databáze). Proto by měl koncepty popsané v jazyce všudypřítomná tvoří základ pro váš _doménový model_.

Doménový model se skládá z objektů, které vzájemně spolupracují představující chování systému. Tyto objekty mohou spadají do následujících kategorií:

- [Entity](https://deviq.com/entity/), které představují objekty s vláknem identity. Entity jsou obvykle uloženy v trvalost s klíčem, pomocí kterého může později načíst.

- [Agregace](https://deviq.com/aggregate-pattern/), které představují skupiny objektů, které by měl být trvalé jako celek.

- [Hodnota objekty](https://deviq.com/value-object/), které představují koncepty, které lze porovnávat na základě součtu hodnot vlastností. Například DateRange skládající se z počáteční a koncové datum.

- [Události domény](https://martinfowler.com/eaaDev/DomainEvent.html), které představují věcí děje v rámci systému, které jsou zajímavé pro ostatní části systému.

Všimněte si, že by měl doménový model DDD zapouzdření složité chování v rámci modelu. Entity, by neměly být zejména pouze kolekce vlastností. Když doménový model nemá chování a představuje pouze stav systému, je označen jako [anemic modelu](https://deviq.com/anemic-model/), což je v DDD nežádoucí.

Kromě těchto typů modelu DDD obvykle využívá širokou škálu vzorce:

- [Úložiště](https://deviq.com/repository-pattern/), pro abstrahovat podrobnosti trvalosti.

- [Objekt pro vytváření](https://en.wikipedia.org/wiki/Factory_method_pattern), pro zapouzdření vytváření komplexních objektů.

- Události domény pro oddělení závislé chování spouštět chování.

- [Služby](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/), pro zapouzdřující složité chování a/nebo podrobnosti implementace infrastruktury.

- [Příkaz](https://en.wikipedia.org/wiki/Command_pattern), pro oddělení vydávání příkazů a provádění příkazu samého.

- [Specifikace](https://deviq.com/specification-pattern/), pro zapouzdření podrobností dotazu.

DDD také doporučuje používat čisté architektury, jak jsme vysvětlili výše, umožňuje volné párování zapouzdření a kód, který lze snadno ověřit pomocí testů jednotek.

### <a name="when-should-you-apply-ddd"></a>Po instalaci aktualizace DDD

DDD je velmi vhodná pro velké aplikace ve službě (ne technickou právě) důležité firemní složitosti. Aplikace by měla vyžadují znalost odborníky na domény. V doménovém modelu, samostatně, představující obchodní pravidla a interakce nad rámec jednoduše ukládání a načítání aktuální stav různých záznamy z úložiště dat by měl být významné chování.

### <a name="when-shouldnt-you-apply-ddd"></a>Pokud by neměla použijete DDD

DDD vyžaduje investice do modelování, architektury a komunikaci, která nemusí být jader pro menší aplikace nebo aplikace, které jsou v podstatě stačí CRUD (vytváření, čtení, aktualizace nebo odstranění). Pokud budete chtít přístup aplikace po DDD, ale najít, že má vaše doména anemic model s žádné chování, budete muset znovu zamysleli nad váš přístup. Vaše aplikace nemusí potřebovat DDD, nebo potřebujete pomoc, refaktoring pro zapouzdření obchodní logiku v modelu domény, nikoli databázi nebo uživatelské rozhraní aplikace.

Hybridní přístup může být pouze použití DDD v oblastech transakční či složitější aplikace, ale ne pro jednodušší CRUD nebo jen pro čtení částí aplikace. Pokud se dotazujete dat. Chcete-li zobrazit sestavu nebo vizualizaci dat pro řídicí panel, například nemusí mít omezení agregace. Je naprosto přijatelné mít samostatné, jednodušší model čtení pro tyto požadavky.

> ### <a name="references--domain-driven-design"></a>Odkazy – návrhem řízeným doménou
>
> - **DDD v běžném jazyce (StackOverflow odpovědí)**  
>   <https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488>

## <a name="deployment"></a>Nasazení

Se využívá řada probíhá nasazení aplikace ASP.NET Core, bez ohledu na to, kde bude hostovat několik kroků. Prvním krokem je publikovat aplikaci, která se dá dělat pomocí dotnet příkazu rozhraní příkazového řádku pro publikování. To bude který aplikaci zkompiluje a umístěte všechny soubory potřebné ke spuštění aplikace do určené složky. Při nasazení ze sady Visual Studio tento krok děláte proto pro vás automaticky. Publikovat složka obsahuje soubory .exe a .dll pro aplikace a jeho závislosti. Samostatné aplikace bude také obsahovat verzi modulu .NET runtime. Aplikace ASP.NET Core bude také obsahovat konfigurační soubory, prostředky statického klienta a zobrazení MVC.

Aplikace ASP.NET Core jsou konzolové aplikace, které musí být spuštěna, když na server se spustí a restartovaný, pokud dojde k chybě aplikace (nebo serveru). Správce procesu můžete použít k automatizaci tohoto procesu. Nejběžnější vedoucí proces pro ASP.NET Core se server Nginx a Apache v Linuxu a služby IIS nebo službu Windows na Windows.

Kromě správce procesu musí aplikace ASP.NET Core hostované na webovém serveru Kestrel použít reverzní proxy server. Reverzní proxy server přijímá požadavky HTTP z Internetu a předává je na Kestrel po některé předběžného zpracování. Reverzní proxy servery aplikace poskytuje vrstvu zabezpečení a jsou požadovány pro nasazení hraniční (vystavené pro provoz z Internetu). Kestrel je relativně nové a dosud neposkytuje ochranu proti některým útokům. Kestrel také nepodporuje hostování více aplikací na stejném portu, takže postupů, jako jsou hlavičky hostitele nelze použít s ním k povolení hostování více aplikací na stejném portu a IP adresu.

![Kestrel k Internetu](./media/image7-5.png)

Obrázek 7 – 5 hostované v Kestrel za reverzní proxy server ASP.NET

Jiný scénář, ve kterém může být užitečné reverzního proxy serveru je zajistit více aplikací pomocí protokolu SSL/HTTPS. V takovém případě by pouze reverzní proxy server musí být nakonfigurovaný protokol SSL. Komunikace mezi serverem pro reverzní proxy server a Kestrel se mohla provést přes protokol HTTP, jak je znázorněno v obrázek 7 až 6.

![](./media/image7-6.png)

Obrázek 7 – 6 ASP.NET hostovaných za službou serveru protokol HTTPS zabezpečená reverzního proxy serveru

Stále oblíbených přístupem je hostovat aplikace ASP.NET Core v kontejneru Dockeru, které pak můžete hostované místně nebo nasadit do Azure pro hostování založené na cloudu. Kontejner Dockeru můžou obsahovat kód vaší aplikace běžící na Kestrel a nasadí se za reverzní proxy server, jak je znázorněno výše.

Pokud máte aplikace na Azure, slouží k poskytování několik služeb Microsoft Azure Application Gateway jako vyhrazené virtuální zařízení. Kromě funguje jako reverzní proxy server pro jednotlivé aplikace, služba Application Gateway nabízí také následující funkce:

- Vyrovnávání zatížení HTTP

- Přesměrování zpracování SSL (protokol SSL jenom pro Internet)

- Kompletního protokolu SSL

- Směrování více webů (konsolidovat až 20 webů na jedinou službou Application Gateway)

- Firewall webových aplikací

- Podpora protokolu Websocket

- Pokročilou diagnostiku

_Další informace o možnostech nasazení Azure v [kapitoly 10](development-process-for-azure.md)._

> ### <a name="references--deployment"></a>Odkazy – nasazení
>
> - **Přehled nasazení a hostování**  
>   <https://docs.microsoft.com/aspnet/core/publishing/>
> - **Kdy použít Kestrel pomocí reverzního proxy serveru**  
>   <https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy>
> - **Hostování aplikací ASP.NET Core v Dockeru**  
>   <https://docs.microsoft.com/aspnet/core/publishing/docker>
> - **Představujeme Azure Application Gateway**  
>   <https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction>

>[!div class="step-by-step"]
>[Předchozí](common-client-side-web-technologies.md)
>[další](work-with-data-in-asp-net-core-apps.md)
