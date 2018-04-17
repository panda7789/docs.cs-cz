---
title: Vývoj aplikací MVC ASP.NET Core
description: Architektury moderních webových aplikací pomocí ASP.NET Core a Azure | vývoj aplikací MVC ASP.NET Core
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 230deb3869887fbcdd07e748d30601f19ec2be2a
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="develop-aspnet-core-mvc-apps"></a>Vývoj aplikací MVC ASP.NET Core

> "Není potřeba získat správné, poprvé. Je životně důležité získat správné, čas posledního."  
> _-Andrew Hunt a David Thomas_

## <a name="summary"></a>Souhrn

ASP.NET Core je napříč platformami, open-source architektura pro vytváření moderní optimalizovaných cloudů webových aplikací. Aplikace ASP.NET Core jsou jednoduchý a modulární s integrovanou podporu pro vkládání závislostí, povolení v větší možnosti testování a jeho udržovatelnost. V kombinaci s MVC, která podporuje vytváření moderní webové rozhraní API kromě aplikace založené na zobrazení, ASP.NET Core je výkonné rozhraní pro sestavení podnikové webové aplikace.

## <a name="mapping-requests-to-responses"></a>Mapování žádosti o odpovědi

Aplikace ASP.NET Core svou podstatou mapování příchozích požadavků na odchozí odpovědi. Na nízké úrovni to je prováděno pomocí middlewaru a jednoduché aplikace ASP.NET Core a mikroslužeb může tvořit pouze z vlastní middleware. Pokud používáte rozhraní ASP.NET MVC jádra, můžete pracovat na něco vyšší úrovni, myslím z hlediska *trasy*, *řadiče*, a *akce*. Každého příchozího požadavku se porovná se aplikace směrovací tabulky, a pokud je nalezen odpovídající trasy, je přidružená metoda akce (patřící do řadiče) se nazývá pro zpracování požadavku. Pokud se nenajde žádný odpovídající trasy, je volána obslužná rutina (v tomto případě vrácením výsledku NotFound).

Jádro ASP.NET MVC aplikace můžete použít konvenční trasy a trasy atributů. Konvenční trasy jsou definovány v kódu zadání směrování *konvence* pomocí syntaxe jako v následujícím příkladu:

```csharp
app.UseMvc(routes =>;
{
    routes.MapRoute("default","{controller=Home}/{action=Index}/{id?}");
});
```

V tomto příkladu se přidal s názvem "Výchozí" trasy do směrovací tabulky. Definuje šablonu trasy se zástupnými symboly pro *řadič*, *akce*, a *id*. Zástupné symboly kontroleru a akce mají výchozí zadaný ("Domů" a "Index", v uvedeném pořadí), a zástupný symbol id je volitelný (základě "?" na něho použít). Konvence definované tady stavy, které by měla odpovídat první část požadavku k názvu řadiče a druhou částí pro akce, a pak v případě potřeby třetí část bude reprezentovat id parametru. Konvenční trasy jsou obvykle definovány na jednom místě aplikace, například v metodě konfigurace v třída při spuštění.

Trasy atributů jsou přímo použít na kontrolerů a akcí, nikoli zadat globálně. To nabízí výhodu v podobě přitom mnohem víc zjistitelný při díváte na konkrétní metodu, ale znamená, že informace o směrování není nacházet v jednom místě v aplikaci. Pomocí atributů tras můžete můžete snadno určit víc tras pro danou akci, jakož i kombinovat trasy mezi službami kontrolery a akce. Příklad:

```csharp
[Route("Home")]
public class HomeController : Controller
{
    [Route("")] // Combines to define the route template "Home"
    [Route("Index")] // Combines to define route template "Home/Index"
    [Route("/")] // Does not combine, defines the route template ""
    public IActionResult Index() {}
```

Třídy [MetadataExchangeClientMode] jde zadat trasy a podobné atributy, takže není nutné přidat oddělte [trasy\] atributy. Atribut trasy, můžete použít také tokeny snížit nutnost opakování názvy kontroler nebo akce, jak je uvedeno níže:

```csharp
[Route("[controller\]")]
public class ProductsController : Controller
{
    [Route("")] // Matches 'Products'
    [Route("Index")] // Matches 'Products/Index'
    public IActionResult Index()
}
```

Jakmile byl daný požadavek odpovídá trasu, ale před akce metoda je volána, ASP.NET MVC jádra provede [model vazby](https://docs.microsoft.com/aspnet/core/mvc/models/model-binding) a [modelu ověření](https://docs.microsoft.com/aspnet/core/mvc/models/validation) v žádosti. Vazby modelu je zodpovědná za převádění příchozích dat protokolu HTTP na typy .NET zadané jako parametry metody akce, která se má volat. Například pokud metoda akce očekává parametr id typu int, vazby modelu se pokusí zajistit tento parametr z hodnoty zadané v rámci žádosti. Uděláte to tak, vazby modelu hledá hodnoty v odeslaného formuláře, hodnoty v samotného postupu a hodnoty řetězců dotazu. Za předpokladu, že hodnotu id nenajde, jej bude možné převést na celé číslo před předáním do metody akce.

Po vytvoření vazby modelu, ale před voláním metody akce dojde k ověření modelu. Ověření modelu používá volitelných atributů v typu modelu a může pomoct zajistit, že objekt zadaného modelu, splňuje určité požadavky na data. Některé hodnoty je možné zadat jako vyžaduje, nebo jsou omezena na délku nebo číselný rozsah, atd. Pokud jsou zadané atributy ověření, ale model není v souladu s požadavky na jejich, vlastnost ModelState.IsValid bude mít hodnotu false a sadu selhání pravidla ověřování bude k dispozici k odeslání do klienta vytvoření požadavku.

Pokud používáte ověření modelu, byste měli vždy zkontrolujte, zda je model platný před provedením jakékoli změny stavu příkazů, ujistěte se, že vaše aplikace není poškozen neplatnými daty. Můžete použít [filtru](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters) abyste ho nemuseli přidat kód pro tuto v každou akci. Jádro ASP.NET MVC filtry nabízejí způsob brání skupiny požadavků, tak, aby běžné zásady a aspekty mezi vyjímání mohou být použity na základě cílové. Filtry lze použít k jednotlivým akcím, celou řadiče nebo globálně pro aplikaci.

Pro webové rozhraní API, rozhraní ASP.NET MVC základní podporuje [ *vyjednávání obsahu*](https://docs.microsoft.com/aspnet/core/mvc/models/formatting), povolení požadavků zadat způsob formátování odpovědi. Podle hlavičky v požadavku, bude akce vracející data formátu odpovědi v XML, JSON nebo jiné podporovaného formátu. Tato funkce umožňuje rozhraní API stejné má být používána více klientů s požadavky na jiný datový formát.

> ### <a name="references--mapping-requests-to-responses"></a>Odkazy – mapování požadavky na odpovědi
> - **Směrování do akce Kontroleru**
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/routing>
> - **Vazby modelu** https://docs.microsoft.com/aspnet/core/mvc/models/model-binding
> - **Ověření modelu**
> <https://docs.microsoft.com/aspnet/core/mvc/models/validation>
> - **filtry** https://docs.microsoft.com/aspnet/core/mvc/controllers/filters

## <a name="working-with-dependencies"></a>Práce s závislosti

Má integrovanou podporu pro ASP.NET Core a interně využívá techniku známou jako [vkládání závislostí](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection). Vkládání závislostí je technika, který povolený volné párování mezi různé části aplikace. Čím větší párování je žádoucí, protože umožňuje jednodušší izolace částí aplikace a umožňuje pro testování nebo pro nahrazení. Je také je méně pravděpodobné, že ke změně v jedné části aplikace bude mít neočekávané dopad někde jinde v aplikaci. Vkládání závislostí je založena na principu inverzi závislostí a často je klíčem k dosažení Princip otevřený nebo zavřený. Při vyhodnocování, jak vaše aplikace funguje s jeho závislé součásti, pozor [statické plevami](http://deviq.com/static-cling/) kód pach a pamatovat aphorism "[nové je spojovací](http://ardalis.com/new-is-glue)."

Statické plevami nastane, když volat statických metod třídy nebo přístup statické vlastnosti, které mají vedlejší účinky nebo v závislosti na infrastruktuře. Například pokud máte metodu, která volá statickou metodu, která zase zapisuje do databáze, způsob je úzce párované do databáze. Všechno, co dělí tohoto volání databáze dojde k přerušení metodu. Testování tyto metody je často složité, protože tyto testy vyžadovala komerční mocking knihovny model statické volání, nebo může být testována pouze pomocí testovací databáze na místě. Statické volání, které nemají žádné závislost na infrastrukturu, především těch, které jsou zcela bezstavové jsou volání a nemají žádný vliv na párování nebo testovatelnosti (kromě spojovacích kódu statických volání sám sebe).

Celá řada vývojářů pochopit rizika statické plevami a globální stav, ale bude stále úzce spojte svůj kód do konkrétní implementace prostřednictvím přímé vytváření instancí. "Nové je spojovací" měl by být připomenutí tento párování a není obecné odsouzení použití new – klíčové slovo. Stejně jako s statickou metodu volání nové instance třídy typy, které nemají žádné externí závislosti obvykle není úzce spojte kód do implementace podrobnosti nebo se přesvědčte testování obtížnější. Ale pokaždé, když je vytvořena instance třídy, pozorně právě stručný zvažte, zda má smysl zakódovat tuto konkrétní instanci v tomto konkrétní umístění, nebo pokud je návrh s lepší požádat o dané instance jako závislost.

### <a name="declare-your-dependencies"></a>Deklarovat závislostmi

ASP.NET Core se vytváří přibližně s metody a třídy deklarovat jejich závislosti, je požádá jako argumenty. Aplikace ASP.NET se obvykle nastavují ve spuštění třídy, které je nakonfigurován pro podporu vkládání závislostí na několika místech. Pokud vaše třída při spuštění má konstruktor, může požádat o závislosti pomocí konstruktoru, například takto:

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

Třída při spuštění se zajímavé, že neexistují žádné požadavky explicitního typu pro ni. Není dědí speciální spuštění základní třídu, ani nebude implementovat žádné konkrétní rozhraní. Můžete jí konstruktoru, nebo Ne, a můžete určit jako v mnoha parametry v konstruktoru tak, jak chcete. Při spuštění webového hostitele, kterou jste nakonfigurovali pro vaše aplikace bude volat třída při spuštění, které jste ho na použití sdělili a použije k naplnění všechny závislosti, které vyžaduje třída při spuštění vkládání závislostí. Samozřejmě Pokud požádáte o parametry, které nejsou nakonfigurované v kontejneru služby používá ASP.NET Core, získáte výjimku, ale také přilepit k závislosti kontejneru zná, můžete požádat nic, co chcete.

Vkládání závislostí je integrovaná do aplikace ASP.NET Core vpravo od začátku, při vytváření instance spuštění. Zastavit není existuje pro třída při spuštění. Můžete také vyžadovat závislosti v metodě konfigurace:

```csharp
public void Configure(IApplicationBuilder app,
    IHostingEnvironment env,
    ILoggerFactory loggerFactory)
{

}
```

Metoda ConfigureServices je výjimka, která má toto chování; je nutné provést pouze jeden parametr typu IServiceCollection. Není třeba skutečně podpoře vkládání závislostí, protože na jedné straně je zodpovědný za přidání objektů do kontejneru služby, a na dalších má přístup ke všem službám aktuálně nakonfigurovaný pomocí parametru IServiceCollection. Proto můžete pracovat s závislosti, které jsou definované v kolekci služeb ASP.NET Core v každé části třída při spuštění, vyžaduje jako parametr potřebné služby, nebo ve spolupráci s IServiceCollection v ConfigureServices.

> [!NOTE]
> Pokud je potřeba zajistit, jsou k dispozici ke třídě spuštění určité služby, můžete je nakonfigurovat pomocí WebHostBuilder a jeho ConfigureServices metoda.

Třída při spuštění je model při volbě struktury dalších částí vaší aplikace ASP.NET Core, z řadičů pro Middleware filtrů vlastní Services. V každém případě byste měli postupovat [explicitní závislosti Princip](http://deviq.com/explicit-dependencies-principle/), požaduje závislostmi místo přímo jejich vytváření a využitím vkládání závislostí v celé vaší aplikaci. Dávejte pozor, kde a jak přímo doložit implementace, zejména služeb a objekty, které práce s infrastrukturou, nebo vedlejší účinky. Dáváte přednost práci s abstrakce definované v vaše základní aplikace a jako argumenty předané do hardcoding odkazy na konkrétní implementace typy.

## <a name="structuring-the-application"></a>Strukturování aplikace

Monolitický aplikace obvykle mají jeden vstupní bod. V případě webová aplikace ASP.NET Core vstupní bod budou webového projektu ASP.NET Core. Však neznamená, že řešení by měla obsahovat právě jeden projekt. Je užitečné rozdělit aplikaci do různých vrstev, abyste podle oddělené oblasti zájmu. Jakmile rozdělit do vrstvy, je vhodné nad rámec složky jednotlivé projekty, které může pomoci dosáhnout lepší zapouzdření. Nejlepší metodou k dosažení těchto cílů s aplikací ASP.NET Core se odlišuje od architektuře čistého popsané v kapitole 5. Následující tento přístup řešení aplikace budou tvořit samostatné knihovny uživatelského rozhraní, infrastruktury a ApplicationCore.

Kromě těchto projekty samostatné testovací projekty jsou zahrnuty také (testování je popsané v kapitole 9).

Objektový model aplikace a rozhraní musí být umístěny v ApplicationCore projektu. Tento projekt budou mít co nejméně závislosti nejdříve a další projekty v řešení bude odkazovat ho. Obchodní entity, které je třeba nastavit jako trvalý, jsou definovány v projektu ApplicationCore, jako jsou služby, které přímo nezávisí na infrastruktuře.

Podrobnosti implementace, například jak se provádí trvalost nebo jak může být odeslána oznámení pro uživatele, jsou uchovány v projektu infrastruktury. Tento projekt bude odkazovat na konkrétní implementace balíčků, jako jsou Entity Framework Core, ale by neměli zveřejňovat podrobnosti o těchto implementace mimo projekt. Infrastruktura služby a úložiště musí implementovat rozhraní, které jsou definovány v projektu ApplicationCore a jeho implementace trvalost jsou zodpovědní za načítání a ukládání entit definované v ApplicationCore.

Samotného projektu ASP.NET Core je zodpovědná za nejasností kontaktovali úrovně uživatelského rozhraní, ale nesmí obsahovat obchodní logiku nebo infrastrukturu podrobnosti. Ve skutečnosti v ideálním případě by neměl i mít závislost na projekt infrastruktury, který vám pomůže zajistit, že žádná závislost mezi dva projekty uvádíme omylem. Toho lze dosáhnout pomocí kontejner DI jiných výrobců jako StructureMap, který umožňuje definovat pravidla DI v registru třídy v každém projektu.

Další postup pro aplikace z podrobnosti implementace oddělení je mikroslužeb volání aplikace, pravděpodobně nasazený v jednotlivých kontejnerech Docker. To poskytuje ještě větší oddělení otázky a oddělení než využití DI mezi dva projekty, ale má zvýšenou složitostí.

### <a name="feature-organization"></a>Funkce organizace

Ve výchozím nastavení aplikace ASP.NET Core uspořádat jejich struktura složek, například řadiče a zobrazení a často ViewModels. Kódu na straně klienta pro podporu těchto struktur serverové je obvykle uložen samostatně ve složce wwwroot. Však velké aplikace setkat s problémy u této organizace, protože funguje na jakékoli dané funkce často vyžaduje přechod mezi tyto složky. To získá mnohem obtížnější počet soubory a podsložky ve složce každého roste, což vede k značnou část posouvání pomocí Průzkumníka řešení. Jedno řešení tohoto problému, je uspořádat kódu aplikace pomocí *funkce* místo pomocí typ souboru. Tato organizace styl se obvykle označuje jako funkce složek nebo funkce řezy (viz také: [svislé řezy](http://deviq.com/vertical-slices/)).

Jádro ASP.NET MVC podporuje oblasti pro tento účel. Použití oblastí, můžete vytvořit samostatné sady řadiče a zobrazení složky (stejně jako žádné přidružené modely) v každé oblasti složky. Obrázek 7-1 zobrazuje strukturu složky příklad pomocí oblastí.

![](./media/image7-1.png)

Obrázek 7-1 ukázka oblasti organizace

Při použití oblastí, je nutné použít atributy pro uspořádání řadičů s název oblasti, do které patří:

```csharp
[Area("Catalog")]
public class HomeController
{}
```

Musíte taky přidat podporu oblasti trasy:

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

Kromě integrovanou podporu pro oblasti můžete také použít vlastní struktury složek a pravidla týkající se místo atributy a vlastní trasy. To by umožnilo mít složky funkce, které nezahrnuli samostatné složky pro zobrazení, řadičů, atd., udržování plošší hierarchii a usnadnit zobrazte že všechny související soubory na jednom místě, pro každou funkci.

ASP.NET Core používá integrované konvence typy mohla kontrolovat své chování. Můžete upravit nebo nahradit tyto konvence. Můžete například vytvořit názvů, který automaticky získá název funkce pro daný kontroler založený na jeho oboru názvů (což obvykle korelaci do složky, ve kterém se nachází řadičem):

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

Potom zadejte touto konvencí jako možnost při přidání podpory pro rozhraní MVC do vaší aplikace v ConfigureServices:

```csharp
services.AddMvc(o => o.Conventions.Add(new FeatureConvention()));
```

Jádro ASP.NET MVC také používá konvenci k vyhledání zobrazení. Lze jej přepsat pomocí vlastních názvů tak, aby zobrazení budou umístěny ve vašich složkách funkce (s použitím názvu funkce poskytované FeatureConvention, výše). Můžete získat další informace o tento přístup a stáhnout ukázku práce z článku na webu MSDN [řezy funkce pro ASP.NET MVC základní](https://msdn.microsoft.com/magazine/mt763233.aspx).

### <a name="cross-cutting-concerns"></a>Mezi vyjímání otázky

Jelikož aplikace, bude stále důležité zohlednit se mezi vyjímání otázky k odstranění duplicity a zajistit konzistenci. Některé příklady mezi vyjímání obavy v aplikacích ASP.NET Core jsou ověřování, pravidla ověřování modelu, ukládání výstupu do mezipaměti a zpracování chyb, i když existuje mnoho dalších. Jádro ASP.NET MVC [filtry](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters) vám umožní spustit kód před nebo po určité kroky v kanálu zpracování požadavků. Například filtr můžete spustit před a po vazby modelu, před a po akci, nebo před a po výsledek akce. Filtr autorizace můžete také použít k řízení přístupu k zbytek kanálu. Obrázky 7-2 ukazuje jak požadavek provádění toky filtry, pokud nakonfigurovaný.

![Filtry autorizace, filtry prostředků, vazby modelu, filtry akce, provádění akce a akce výsledek převodu, filtry výjimek, filtry výsledků a výsledek spuštění zpracování žádosti. Na cestě se žádost pouze zpracovává filtry výsledků a filtry prostředků než se stane odpověď může odeslat klientovi.](./media/image7-2.png)

Obrázek 7-2 žádost o spuštění přes filtry a požadavku kanálu.

Filtry jsou obvykle implementovány jako atributy, abyste je mohli použít, řadiče nebo akce. Při přidání tímto způsobem, filtry zadaná na úrovni přepsání akce nebo sestavení při filtry zadané na úrovni kontroleru, který sami přepsat globální filtry. Například \[trasy\] atributu lze vytvořit trasy mezi službami kontrolery a akce. Podobně autorizace můžete nakonfigurovat na úrovni kontroleru a pak přepsat jednotlivé akce, jako ukazuje následující příklad:

```csharp
[Authorize]
public class AccountController : Controller

{
    [AllowAnonymous]
    public async Task<IActionResult> Login() {}
    public async Task<IActionResult> ForgotPassword() {}
}
```

První metoda přihlášení, využívá filtr AllowAnonymous (atribut) pro přepsání filtru autorizovat nastavit na úrovni kontroleru. Požadavek na ověřeného bude vyžadovat akce ForgotPassword (a provedení dalších akcí ve třídě, která nemá atribut AllowAnonymous).

K vyloučení duplikace ve formě běžné Chyba při zpracování zásady pro rozhraní API můžete použít filtry. Typické zásada rozhraní API je například vrátí serveru odpovědí na požadavky odkazující na klíče, které nejsou k dispozici a struktura BadRequest odpověď, pokud selže ověření modelu. Následující příklad ukazuje tyto dvě zásady v akci:

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

Nepovolit vaší metody akce k zaplní podmíněného kód takto. Místo toho načítat zásady do filtry, které mohou být použity na podle potřeby. Kontrola ověření modelu, která by měl nastat, když je odeslán příkaz do rozhraní API, můžete v tomto příkladu nahrazuje následující atribut:

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

Podobně filtr slouží ke kontrole Pokud záznam existuje a vrátí 404, před provedením akce, takže není nutné provádět tyto kontroly v akci. Jakmile jste výseče běžné konvence a uspořádány řešení infrastruktury kódu a obchodní logiku nezávislá na vaše uživatelské prostředí, by měla být velmi dynamické vaší metody akce MVC:

```csharp
// PUT api/authors/2/5
[HttpPut("{id}")]
[ValidateAuthorExists]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

Další informace o implementaci filtry a stáhnout ukázku práce z článku na webu MSDN [skutečné World ASP.NET Core MVC filtry](https://msdn.microsoft.com/magazine/mt767699.aspx).

> ### <a name="references--structuring-applications"></a>Odkazy – strukturování aplikace
> - **Oblasti**  
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/areas>
> - **MSDN – funkce řezy pro jádro ASP.NET MVC**
>  <https://msdn.microsoft.com/magazine/mt763233.aspx>
> - **Filtry**  
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - **MSDN – skutečných jádro ASP.NET MVC filtry**  
> <https://msdn.microsoft.com/magazine/mt767699.aspx>

## <a name="security"></a>Zabezpečení

Zabezpečení webových aplikací je velké téma, mnoho aspektů. Na nejzákladnější úrovni zahrnuje zabezpečení zajistíte, že budete vědět, kdo je pocházejících z daného požadavku a zajistit, že tento požadavek má jenom přístup k prostředkům, které by měl. Ověřování je proces porovnávání přihlašovací údaje se žádostí o definicím v úložišti důvěryhodných dat, pokud chcete zobrazit, pokud by se jako pocházející ze známé entity zpracovávat žádosti. Autorizace je proces omezení přístupu k určitým prostředkům na základě identity uživatele. Třetí potíže se zabezpečením chrání požadavky založenými na odposlechu třetích stran, pro které byste měli aspoň [Ujistěte se, že vaše aplikace používá protokol SSL](https://docs.microsoft.com/aspnet/core/security/enforcing-ssl).

### <a name="authentication"></a>Ověřování

Identita ASP.NET Core je systém členství, které můžete použít k podpoře funkce přihlašování pro vaši aplikaci. Obsahuje podporu pro místní uživatelské účty a také podpora zprostředkovatele externí přihlášení od poskytovatelů, jako je Microsoft Account, Twitter, Facebook, Google a další. Kromě ASP.NET Core Identity, vaše aplikace může použít ověřování systému windows nebo jako poskytovatel identity jiného výrobce [serveru identit](https://github.com/IdentityServer/IdentityServer4).

Jádro ASP.NET Identity je součástí nové šablony projektu, pokud je vybrána možnost jednotlivé uživatelské účty. Tato šablona zahrnuje podporu registrace, přihlášení, externí přihlášení, zapomenutým heslům a další funkce.

![](./media/image7-3.png)

Obrázek 7-3 vyberte jednotlivé uživatelské účty tak, aby měl předkonfigurované Identity.

Podpora identit je nakonfigurované ve spuštění v ConfigureServices i konfigurace:

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

Je důležité, aby UseIdentity zobrazí před UseMvc v metodě konfigurace. Při konfiguraci Identity v ConfigureServices, můžete si všimnout volání AddDefaultTokenProviders. Tato akce nemá co dělat s tokeny, které slouží k zabezpečení komunikace webových, ale místo toho odkazuje na zprostředkovatele, které vytvářejí výzvy, které může být uživatelům odešle přes SMS nebo e-mailu v pořadí pro ně potvrdit svou identitu.

Další informace o [konfigurace dvoufaktorové ověřování](https://docs.microsoft.com/aspnet/core/security/authentication/2fa) a [povolení zprostředkovatele externí přihlášení](https://docs.microsoft.com/aspnet/core/security/authentication/social/) z oficiální dokumentaci ASP.NET Core.

### <a name="authorization"></a>Autorizace

Nejjednodušší forma autorizace zahrnuje omezení přístupu pro anonymní uživatele. Toho lze dosáhnout jednoduše použitím \[Autorizovat\] atribut určité řadiče nebo akce. Pokud role se používají, atribut můžete omezit přístup pro uživatele, kteří patří do určité role, jak je vidět další rozšířené:

```csharp
[Authorize(Roles = "HRManager,Finance")]
public class SalaryController : Controller
{

}
```

V takovém případě by uživatelé, kteří patří buď HRManager nebo finanční rolí (nebo obě) mít přístup k SalaryController. Pokud chcete vyžadovat, aby uživatel patří do více rolí, (nikoli pouze jeden z několika), můžete použít atribut vícekrát, zadáte požadované role pokaždé, když.

Zadání určité sady role jako řetězce v mnoha různých kontrolery a akce může vést k nežádoucího opakování. Můžete nakonfigurovat zásady autorizace, které zapouzdření autorizační pravidla, a poté zadejte zásady místo jednotlivých rolí při použití \[Autorizovat\] atribut:

```csharp
[Authorize(Policy = "CanViewPrivateReport")]
public IActionResult ExecutiveSalaryReport()
{
    return View();
}
```

Pomocí zásad tímto způsobem, můžete oddělit druhy akce je omezená z konkrétní role nebo pravidla, která se použije na ni. Později, pokud vytvoříte novou roli, která potřebuje přístup k určitým prostředkům, můžete pouze aktualizovat zásady, nikoli aktualizace každých seznam rolí na každý \[Autorizovat\] atribut.

#### <a name="claims"></a>Deklarace identity

Deklarace identity jsou páry název hodnota, které představují vlastnosti ověřeného uživatele. Číslo zaměstnance uživatelů může například uložit jako deklarace identity. Deklarace identity pak lze v rámci zásad autorizace. Můžete vytvořit zásadu s názvem "EmployeeOnly", musí existovat deklarace názvem "Číslo_zaměstnance", jak je uvedeno v následujícím příkladu:

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

Tato zásada se pak může pomocí \[Autorizovat\] atribut k ochraně všech kontroleru a akce, jak je popsáno výše.

#### <a name="securing-web-apis"></a>Zabezpečení rozhraní Web API

Většina webových rozhraní API by měla implementovat ověřování na základě tokenu systému. Ověření pomocí tokenu je bezstavové a navrženy tak, aby byla škálovatelná. V systému na základě tokenu ověřování musí klient nejprve ověřit pomocí zprostředkovatele ověřování. V případě úspěšného klienta vydán token, který je jednoduše kryptograficky smysluplný řetězec znaků. Pokud klient potřebuje potom vydat žádost na rozhraní API, přidá tento token jako záhlaví v žádosti. Server pak ověří token nalezen v hlavičce požadavku před dokončením požadavku. Obrázek 7-4 ukazuje tento proces.

![TokenAuth](./media/image7-4.png)

**Obrázek 7 – 4.** Ověřování na základě tokenu pro rozhraní Web API.

> ### <a name="references--security"></a>Odkazy – zabezpečení
> - **Přehled dokumentace zabezpečení**  
> https://docs.microsoft.com/aspnet/core/security/
> - **Vynucování SSL v aplikaci ASP.NET Core**  
> <https://docs.microsoft.com/aspnet/core/security/enforcing-ssl>
> - **Úvod do systému Identity**  
> <https://docs.microsoft.com/aspnet/core/security/authentication/identity>
> - **Úvod do autorizace**  
> <https://docs.microsoft.com/aspnet/core/security/authorization/introduction>
> - **Ověřování a autorizace API Apps v Azure App Service**  
> <https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication>

## <a name="client-communication"></a>Komunikace klienta

Kromě obsluhující stránky a reagovat na požadavky na data prostřednictvím webových rozhraní API, může aplikace ASP.NET Core komunikovat přímo s připojenými klienty. Odchozí komunikaci, můžete použít různé přenosu technologií, nejběžnější vrácení objekty WebSockets. Jádro ASP.NET SignalR je do knihovny, která usnadňuje přidat funkce v reálném čase komunikace klienta a serveru pro vaše aplikace. SignalR podporuje celou řadu technologií přenosu, včetně Websocket a abstrahuje tokeny n Podrobnosti implementace od vývojáře.

Jádro ASP.NET SignalR je aktuálně ve vývoji a bude k dispozici v další verzi ASP.NET Core. Ale jiné [otevřete zdroj Websocket knihovny](https://github.com/radu-matei/websocket-manager) jsou nyní k dispozici.

Komunikace klienta v reálném čase, zda pomocí technologie WebSockets přímo nebo jinými technikami, jsou užitečné v různých scénářů aplikace. Mezi příklady patří:

-   Za provozu konverzační skupinu aplikací

-   Monitorování aplikací

-   Probíhá aktualizace úlohy

-   Oznámení

-   Interaktivní formulářových aplikací

Při sestavování komunikace klienta do svých aplikací, jsou obvykle dvě součásti:

-   Správce připojení na straně serveru (rozbočovače SignalR, WebSocketManager WebSocketHandler)

-   Knihovna klienta

Klienti nejsou nijak omezené do prohlížečů – mobilních aplikací, aplikace konzoly a dalších nativní aplikace může také komunikovat pomocí SignalR/Websocket. Následující jednoduchý program vrátí veškerý obsah odeslat do aplikace chat konzole, jako součást WebSocketManager ukázkovou aplikaci:

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
```

Zvažte zvýšení způsoby, ve kterých vaše aplikace komunikovat přímo s klientským aplikacím a zvažte, zda v reálném čase komunikace by zlepšit uživatele vaší aplikace.

> ### <a name="references--client-communication"></a>Odkazy – komunikaci klientů
> - **Jádro ASP.NET SignalR**  
> <https://github.com/aspnet/SignalR>
> - **Správce protokolu WebSocket**  
> https://github.com/radu-matei/websocket-manager

## <a name="domain-driven-design--should-you-apply-it"></a>Návrh – řízené domény by měl použijete ho?

Řízené domény návrhu (DDD) je agilní přístup k vytváření software, který klade důraz zaměřené na *obchodní domény*. Umístí velkou důraz na komunikaci a interakci s expert(s) obchodní domény, který může být v relaci pro vývojáře fungování reálného systému. Například pokud vytváříte systém, který zpracovává burzovní obchody, expert vaší domény může být zkušeného uložených zprostředkovatele. DDD slouží k řešení problémů složitých obchodní a není často vhodná pro menší, jednodušší aplikací, protože investice vysvětlující Princip fungování a modelování domény není vhodné ho.

Při sestavování softwaru následující DDD přístup, musí váš tým (včetně netechnické zúčastněným stranám a přispěvatelé) vyvíjet *všudypřítomný jazyk* místo problém. To znamená stejné terminologie slouží koncept reálného modelovaných, ekvivalent softwaru a všechny struktury, které mohou existovat udržení koncept (například tabulek databáze). Proto by měl konceptů popsaných v jazyce všudypřítomný tvoří základ pro vaše *modelu domény*.

Váš model domény se skládá z objektů, které vzájemně představují chování systému. Tyto objekty může spadají do následujících kategorií:

-   [Entity](http://deviq.com/entity/), které představují objekty s vláknem identity. Entity jsou obvykle uložena v trvalost s klíčem, podle kterého se dá později načíst.

-   [Agregace](http://deviq.com/aggregate-pattern/), který představuje skupiny objektů, které by měl být trvalé jako jednotku.

-   [Hodnota objekty](http://deviq.com/value-object/), které představují koncepty, které lze porovnat s hodnotou na základě součtu hodnot jejich vlastností. Například DateRange skládající se z počáteční a koncové datum.

-   [Události domény](https://martinfowler.com/eaaDev/DomainEvent.html), které představují věcí děje v rámci systému, které jsou důležité pro ostatní části systému.

Všimněte si, že by měl modelu domény DDD zapouzdření komplexní chování v rámci modelu. Entity, by neměl být zejména jenom kolekcí vlastností. Pokud model domény chybí chování a představuje pouze stav systému, je označováno jako [anemic modelu](http://deviq.com/anemic-model/), což je žádoucí v DDD.

Kromě těchto typů modelu DDD obvykle využívá různé vzorce:

-   [Úložiště](http://deviq.com/repository-pattern/), pro poskytuje abstrakci podrobnosti trvalost.

-   [Objekt pro vytváření](https://en.wikipedia.org/wiki/Factory_method_pattern), pro zapouzdření vytváření komplexních objektů.

-   Události domény pro oddělení závislé chování z aktivován chování.

-   [Služby](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/)pro zapouzdřením komplexní chování a podrobnosti implementace infrastruktury.

-   [Příkaz](https://en.wikipedia.org/wiki/Command_pattern), pro oddělení vydávání příkazů a provádění příkazu sám sebe.

-   [Specifikace](http://deviq.com/specification-pattern/), pro zapouzdření podrobnosti dotazu.

DDD také doporučuje použití architektuře čistého, jak jsme vysvětlili výše, aby vám umožnil volné párování, zapouzdření a kód, který lze snadno ověřit pomocí testování částí.

### <a name="when-should-you-apply-ddd"></a>Pokud by se měly používat DDD

DDD je vhodné řešení pro velké aplikace s složitost významné firmy (ne technického právě). Aplikace by měla vyžadují znalosti systému domény odborníky. Domény přímo pro model, představující obchodní pravidla a interakce nad rámec jednoduše ukládání a načítání aktuální stav různých záznamů z úložiště dat by měly mít významné chování.

### <a name="when-shouldnt-you-apply-ddd"></a>Pokud by se neměla vztahovat DDD

DDD zahrnuje investice do modelování, architekturu a komunikaci, která nemusí být jader pro menší aplikací nebo aplikace, které jsou v podstatě právě CRUD (vytváření, čtení, aktualizaci nebo odstranění). Pokud zvolíte možnost přístupu aplikace následující DDD, ale najít, že má vaše doména model anemic s žádné chování, musíte přehodnotit váš přístup. Buď vaše aplikace nemusí potřebovat DDD, nebo potřebujete pomoc refaktoring aplikace má být zapouzdřena obchodní logiku v modelu domény, nikoli vaše databáze nebo uživatelské rozhraní.

Hybridní přístup by mohla být DDD použít pouze pro transakční či složitější oblasti aplikace, ale ne pro jednodušší CRUD nebo jen pro čtení částí aplikace. Pokud se dotazuje data k zobrazení sestavy nebo k vizualizaci dat pro řídicí panel, například nemusí mít omezení agregace. Je zcela přijatelné mít samostatné, jednodušší čtení model pro tyto požadavky.

> ### <a name="references--domain-driven-design"></a>Odkazy – funguje na základě domény
> - **DDD zjednodušeně (StackOverflow odpovědí)**  
> <https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488>

## <a name="deployment"></a>Nasazení

Související se situací procesu nasazení vaší aplikace ASP.NET Core, bez ohledu na to, který bude hostitelem je několik kroků. Prvním krokem je můžete publikovat aplikaci, což lze provést pomocí dotnet publikování rozhraní příkazového řádku příkaz. Tato akce kompilace aplikace a umístit všechny soubory potřebné ke spuštění aplikace do určené složky. Při nasazení ze sady Visual Studio, je pro vás tento krok provést automaticky. Publikování složka obsahuje soubory .exe a .dll pro aplikace a její závislosti. Samostatný aplikace bude také obsahovat verzi modulu runtime rozhraní .NET. Aplikace ASP.NET Core bude také obsahovat konfigurační soubory, prostředky statického klienta a zobrazení MVC.

Aplikace ASP.NET Core jsou konzolové aplikace, které musí být spuštěna, když na server se spustí a restartovat, pokud dojde k chybě aplikace (nebo serveru). Proces manager můžete použít k automatizaci tohoto procesu. Nejběžnější správci proces pro ASP.NET Core jsou Nginx a Apache na Linuxu a služby IIS nebo služba systému Windows v systému Windows.

Kromě Správce úloh musí aplikace ASP.NET Core hostované na webovém serveru Kestrel použít reverzní proxy server. Reverzní proxy server přijímá požadavky HTTP z Internetu a předává je Kestrel po některé předběžné zpracování. Reverzní proxy servery poskytují úroveň zabezpečení pro aplikace a jsou vyžadována pro nasazení okraj (vystavený pro přenosy z Internetu). Kestrel je relativně nové a dosud neposkytuje obranu proti napadením. Kestrel nepodporuje hostování více aplikací na stejném portu, takže techniky jako hlavičky hostitele nelze použít s ním povolit hostování více aplikací na stejný port a IP adresu.

![Kestrel k Internetu](./media/image7-5.png)

Obrázek 7-5 ASP.NET, které jsou hostovány v Kestrel za reverzní proxy server

Další scénáře, ve kterém může být užitečné reverzní proxy server je zabezpečit více aplikací pomocí SSL nebo HTTPS. Pouze reverzní proxy server v takovém případě bude muset mít nakonfigurovaný protokol SSL. Komunikace mezi reverzní proxy server a Kestrel mohla provést prostřednictvím protokolu HTTP, jak je znázorněno na obrázku 7 až 6.

![](./media/image7-6.png)

Obrázek 7-6 ASP.NET hostované za serveru HTTPS zabezpečené reverzní proxy server

Kvůli hostování vaší aplikace ASP.NET Core v kontejner Docker, který pak lze hostována místně nebo nasadit do Azure pro hostování cloudových je stále oblíbených přístup. Kontejner Docker může obsahovat kód aplikace, systémem Kestrel a se nasazuje za reverzní proxy server, jak je uvedeno výše.

Pokud máte aplikace na platformě Azure, slouží k poskytování několika služeb Microsoft Azure Application Gateway jako vyhrazené virtuální zařízení. Kromě funguje jako reverzní proxy server pro jednotlivé aplikace, aplikační brány také nabízí následující funkce:

-   Vyrovnávání zatížení HTTP

-   Přesměrování zpracování SSL (SSL pouze k Internetu)

-   Koncová SSL

-   Více lokalit směrování (konsolidovat až 20 webů na jednom Aplikační brána)

-   Brány firewall webových aplikací

-   Podpora protokolu Websocket

-   Pokročilé diagnostiky

*Další informace o možnostech nasazení Azure v kapitole 10.*

> ### <a name="references--deployment"></a>Odkazy – nasazení
> - **Přehled nasazení a hostování**  
> <https://docs.microsoft.com/aspnet/core/publishing/>
> - **Kdy použít Kestrel s reverzní proxy server**  
> <https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy>
> - **Aplikace ASP.NET Core hostitele v Docker**  
> <https://docs.microsoft.com/aspnet/core/publishing/docker>
> - **Představení Azure Application Gateway**  
> <https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction>

>[!div class="step-by-step"]
[Předchozí] (common-client-side-web-technologies.md) [Další] (work-with-data-in-asp-net-core-apps.md)
