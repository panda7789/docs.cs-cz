---
title: "Vývoj aplikací MVC ASP.NET Core"
description: "Architektury moderních webových aplikací pomocí ASP.NET Core a Azure | vývoj aplikací MVC ASP.NET Core"
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c10bf66dd37f0d99c038db7f95999d84986152fa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="develop-aspnet-core-mvc-apps"></a><span data-ttu-id="aad62-103">Vývoj aplikací MVC ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="aad62-103">Develop ASP.NET Core MVC Apps</span></span>

> <span data-ttu-id="aad62-104">"Není potřeba získat správné, poprvé.</span><span class="sxs-lookup"><span data-stu-id="aad62-104">"It's not important to get it right the first time.</span></span> <span data-ttu-id="aad62-105">Je životně důležité získat správné, čas posledního."</span><span class="sxs-lookup"><span data-stu-id="aad62-105">It's vitally important to get it right the last time."</span></span>  
> <span data-ttu-id="aad62-106">_-Andrew Hunt a David Thomas_</span><span class="sxs-lookup"><span data-stu-id="aad62-106">_- Andrew Hunt and David Thomas_</span></span>

## <a name="summary"></a><span data-ttu-id="aad62-107">Souhrn</span><span class="sxs-lookup"><span data-stu-id="aad62-107">Summary</span></span>

<span data-ttu-id="aad62-108">ASP.NET Core je napříč platformami, open-source architektura pro vytváření moderní optimalizovaných cloudů webových aplikací.</span><span class="sxs-lookup"><span data-stu-id="aad62-108">ASP.NET Core is a cross-platform, open-source framework for building modern cloud-optimized web applications.</span></span> <span data-ttu-id="aad62-109">Aplikace ASP.NET Core jsou jednoduchý a modulární s integrovanou podporu pro vkládání závislostí, povolení v větší možnosti testování a jeho udržovatelnost.</span><span class="sxs-lookup"><span data-stu-id="aad62-109">ASP.NET Core apps are lightweight and modular, with built-in support for dependency injection, enabling in greater testability and maintainability.</span></span> <span data-ttu-id="aad62-110">V kombinaci s MVC, která podporuje vytváření moderní webové rozhraní API kromě aplikace založené na zobrazení, ASP.NET Core je výkonné rozhraní pro sestavení podnikové webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="aad62-110">Combined with MVC, which supports building modern web APIs in addition to view-based apps, ASP.NET Core is a powerful framework with which to build enterprise web applications.</span></span>

## <a name="mapping-requests-to-responses"></a><span data-ttu-id="aad62-111">Mapování žádosti o odpovědi</span><span class="sxs-lookup"><span data-stu-id="aad62-111">Mapping Requests to Responses</span></span>

<span data-ttu-id="aad62-112">Aplikace ASP.NET Core svou podstatou mapování příchozích požadavků na odchozí odpovědi.</span><span class="sxs-lookup"><span data-stu-id="aad62-112">At its heart, ASP.NET Core apps map incoming requests to outgoing responses.</span></span> <span data-ttu-id="aad62-113">Na nízké úrovni to je prováděno pomocí middlewaru a jednoduché aplikace ASP.NET Core a mikroslužeb může tvořit pouze z vlastní middleware.</span><span class="sxs-lookup"><span data-stu-id="aad62-113">At a low level, this is done with middleware, and simple ASP.NET Core apps and microservices may be comprised solely of custom middleware.</span></span> <span data-ttu-id="aad62-114">Pokud používáte rozhraní ASP.NET MVC jádra, můžete pracovat na něco vyšší úrovni, myslím z hlediska *trasy*, *řadiče*, a *akce*.</span><span class="sxs-lookup"><span data-stu-id="aad62-114">When using ASP.NET Core MVC, you can work at a somewhat higher level, thinking in terms of *routes*, *controllers*, and *actions*.</span></span> <span data-ttu-id="aad62-115">Každého příchozího požadavku se porovná se aplikace směrovací tabulky, a pokud je nalezen odpovídající trasy, je přidružená metoda akce (patřící do řadiče) se nazývá pro zpracování požadavku.</span><span class="sxs-lookup"><span data-stu-id="aad62-115">Each incoming request is compared with the application's routing table, and if a matching route is found, the associated action method (belonging to a controller) is called to handle the request.</span></span> <span data-ttu-id="aad62-116">Pokud se nenajde žádný odpovídající trasy, je volána obslužná rutina (v tomto případě vrácením výsledku NotFound).</span><span class="sxs-lookup"><span data-stu-id="aad62-116">If no matching route is found, an error handler (in this case, returning a NotFound result) is called.</span></span>

<span data-ttu-id="aad62-117">Jádro ASP.NET MVC aplikace můžete použít konvenční trasy a trasy atributů.</span><span class="sxs-lookup"><span data-stu-id="aad62-117">ASP.NET Core MVC apps can use conventional routes, attribute routes, or both.</span></span> <span data-ttu-id="aad62-118">Konvenční trasy jsou definovány v kódu zadání směrování *konvence* pomocí syntaxe jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="aad62-118">Conventional routes are defined in code, specifying routing *conventions* using syntax like in the example below:</span></span>

```csharp
app.UseMvc(routes =>;
{
    routes.MapRoute("default","{controller=Home}/{action=Index}/{id?}");
});
```

<span data-ttu-id="aad62-119">V tomto příkladu se přidal s názvem "Výchozí" trasy do směrovací tabulky.</span><span class="sxs-lookup"><span data-stu-id="aad62-119">In this example, a route named "default" has been added to the routing table.</span></span> <span data-ttu-id="aad62-120">Definuje šablonu trasy se zástupnými symboly pro *řadič*, *akce*, a *id*. Zástupné symboly kontroleru a akce mají výchozí zadaný ("Domů" a "Index", v uvedeném pořadí), a zástupný symbol id je volitelný (základě "?" na něho použít).</span><span class="sxs-lookup"><span data-stu-id="aad62-120">It defines a route template with placeholders for *controller*, *action*, and *id*. The controller and action placeholders have default specified ("Home" and "Index", respectively), and the id placeholder is optional (by virtue of a "?" applied to it).</span></span> <span data-ttu-id="aad62-121">Konvence definované tady stavy, které by měla odpovídat první část požadavku k názvu řadiče a druhou částí pro akce, a pak v případě potřeby třetí část bude reprezentovat id parametru.</span><span class="sxs-lookup"><span data-stu-id="aad62-121">The convention defined here states that the first part of a request should correspond to the name of the controller, the second part to the action, and then if necessary a third part will represent an id parameter.</span></span> <span data-ttu-id="aad62-122">Konvenční trasy jsou obvykle definovány na jednom místě aplikace, například v metodě konfigurace v třída při spuštění.</span><span class="sxs-lookup"><span data-stu-id="aad62-122">Conventional routes are typically defined in one place for the application, such as in the Configure method in the Startup class.</span></span>

<span data-ttu-id="aad62-123">Trasy atributů jsou přímo použít na kontrolerů a akcí, nikoli zadat globálně.</span><span class="sxs-lookup"><span data-stu-id="aad62-123">Attribute routes are applied to controllers and actions directly, rather than specified globally.</span></span> <span data-ttu-id="aad62-124">To nabízí výhodu v podobě přitom mnohem víc zjistitelný při díváte na konkrétní metodu, ale znamená, že informace o směrování není nacházet v jednom místě v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="aad62-124">This has the advantage of making them much more discoverable when you're looking at a particular method, but does mean that routing information is not kept in one place in the application.</span></span> <span data-ttu-id="aad62-125">Pomocí atributů tras můžete můžete snadno určit víc tras pro danou akci, jakož i kombinovat trasy mezi službami kontrolery a akce.</span><span class="sxs-lookup"><span data-stu-id="aad62-125">With attribute routes, you can easily specify multiple routes for a given action, as well as combine routes between controllers and actions.</span></span> <span data-ttu-id="aad62-126">Příklad:</span><span class="sxs-lookup"><span data-stu-id="aad62-126">For example:</span></span>

```csharp
[Route("Home")]
public class HomeController : Controller
{
    [Route("")] // Combines to define the route template "Home"
    [Route("Index")] // Combines to define route template "Home/Index"
    [Route("/")] // Does not combine, defines the route template ""
    public IActionResult Index() {}
```

<span data-ttu-id="aad62-127">Třídy [MetadataExchangeClientMode] jde zadat trasy a podobné atributy, takže není nutné přidat oddělte [trasy\] atributy.</span><span class="sxs-lookup"><span data-stu-id="aad62-127">Routes can be specified on [HttpGet] and similar attributes, avoiding the need to add separate [Route\] attributes.</span></span> <span data-ttu-id="aad62-128">Atribut trasy, můžete použít také tokeny snížit nutnost opakování názvy kontroler nebo akce, jak je uvedeno níže:</span><span class="sxs-lookup"><span data-stu-id="aad62-128">Attribute routes can also use tokens to reduce the need to repeat controller or action names, as shown below:</span></span>

```csharp
[Route("[controller\]")]
public class ProductsController : Controller
{
    [Route("")] // Matches 'Products'
    [Route("Index")] // Matches 'Products/Index'
    public IActionResult Index()
}
```

<span data-ttu-id="aad62-129">Jakmile byl daný požadavek odpovídá trasu, ale před akce metoda je volána, ASP.NET MVC jádra provede [model vazby](https://docs.microsoft.com/aspnet/core/mvc/models/model-binding) a [modelu ověření](https://docs.microsoft.com/aspnet/core/mvc/models/validation) v žádosti.</span><span class="sxs-lookup"><span data-stu-id="aad62-129">Once a given request has been matched to a route, but before the action method is called, ASP.NET Core MVC will perform [model binding](https://docs.microsoft.com/aspnet/core/mvc/models/model-binding) and [model validation](https://docs.microsoft.com/aspnet/core/mvc/models/validation) on the request.</span></span> <span data-ttu-id="aad62-130">Vazby modelu je zodpovědná za převádění příchozích dat protokolu HTTP na typy .NET zadané jako parametry metody akce, která se má volat.</span><span class="sxs-lookup"><span data-stu-id="aad62-130">Model binding is responsible for converting incoming HTTP data into the .NET types specified as parameters of the action method to be called.</span></span> <span data-ttu-id="aad62-131">Například pokud metoda akce očekává parametr id typu int, vazby modelu se pokusí zajistit tento parametr z hodnoty zadané v rámci žádosti.</span><span class="sxs-lookup"><span data-stu-id="aad62-131">For example, if the action method expects an int id parameter, model binding will attempt to provide this parameter from a value provided as part of the request.</span></span> <span data-ttu-id="aad62-132">Uděláte to tak, vazby modelu hledá hodnoty v odeslaného formuláře, hodnoty v samotného postupu a hodnoty řetězců dotazu.</span><span class="sxs-lookup"><span data-stu-id="aad62-132">To do so, model binding looks for values in a posted form, values in the route itself, and query string values.</span></span> <span data-ttu-id="aad62-133">Za předpokladu, že hodnotu id nenajde, jej bude možné převést na celé číslo před předáním do metody akce.</span><span class="sxs-lookup"><span data-stu-id="aad62-133">Assuming an id value is found, it will be converted to an integer before being passed into the action method.</span></span>

<span data-ttu-id="aad62-134">Po vytvoření vazby modelu, ale před voláním metody akce dojde k ověření modelu.</span><span class="sxs-lookup"><span data-stu-id="aad62-134">After binding the model but before calling the action method, model validation occurs.</span></span> <span data-ttu-id="aad62-135">Ověření modelu používá volitelných atributů v typu modelu a může pomoct zajistit, že objekt zadaného modelu, splňuje určité požadavky na data.</span><span class="sxs-lookup"><span data-stu-id="aad62-135">Model validation uses optional attributes on the model type, and can help ensure that the provided model object conforms to certain data requirements.</span></span> <span data-ttu-id="aad62-136">Některé hodnoty je možné zadat jako vyžaduje, nebo jsou omezena na délku nebo číselný rozsah, atd. Pokud jsou zadané atributy ověření, ale model není v souladu s požadavky na jejich, vlastnost ModelState.IsValid bude mít hodnotu false a sadu selhání pravidla ověřování bude k dispozici k odeslání do klienta vytvoření požadavku.</span><span class="sxs-lookup"><span data-stu-id="aad62-136">Certain values may be specified as required, or limited to a certain length or numeric range, etc. If validation attributes are specified but the model does not conform to their requirements, the property ModelState.IsValid will be false, and the set of failing validation rules will be available to send to the client making the request.</span></span>

<span data-ttu-id="aad62-137">Pokud používáte ověření modelu, byste měli vždy zkontrolujte, zda je model platný před provedením jakékoli změny stavu příkazů, ujistěte se, že vaše aplikace není poškozen neplatnými daty.</span><span class="sxs-lookup"><span data-stu-id="aad62-137">If you are using model validation, you should be sure to always check that the model is valid before performing any state-altering commands, to ensure your app is not corrupted by invalid data.</span></span> <span data-ttu-id="aad62-138">Můžete použít [filtru](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters) abyste ho nemuseli přidat kód pro tuto v každou akci.</span><span class="sxs-lookup"><span data-stu-id="aad62-138">You can use a [filter](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters) to avoid the need to add code for this in every action.</span></span> <span data-ttu-id="aad62-139">Jádro ASP.NET MVC filtry nabízejí způsob brání skupiny požadavků, tak, aby běžné zásady a aspekty mezi vyjímání mohou být použity na základě cílové.</span><span class="sxs-lookup"><span data-stu-id="aad62-139">ASP.NET Core MVC filters offer a way of intercepting groups of requests, so that common policies and cross-cutting concerns can be applied on a targeted basis.</span></span> <span data-ttu-id="aad62-140">Filtry lze použít k jednotlivým akcím, celou řadiče nebo globálně pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="aad62-140">Filters can be applied to individual actions, whole controllers, or globally for an application.</span></span>

<span data-ttu-id="aad62-141">Pro webové rozhraní API, rozhraní ASP.NET MVC základní podporuje [ *vyjednávání obsahu*](https://docs.microsoft.com/aspnet/core/mvc/models/formatting), povolení požadavků zadat způsob formátování odpovědi.</span><span class="sxs-lookup"><span data-stu-id="aad62-141">For web APIs, ASP.NET Core MVC supports [*content negotiation*](https://docs.microsoft.com/aspnet/core/mvc/models/formatting), allowing requests to specify how responses should be formatted.</span></span> <span data-ttu-id="aad62-142">Podle hlavičky v požadavku, bude akce vracející data formátu odpovědi v XML, JSON nebo jiné podporovaného formátu.</span><span class="sxs-lookup"><span data-stu-id="aad62-142">Based on headers provided in the request, actions returning data will format the response in XML, JSON, or another supported format.</span></span> <span data-ttu-id="aad62-143">Tato funkce umožňuje rozhraní API stejné má být používána více klientů s požadavky na jiný datový formát.</span><span class="sxs-lookup"><span data-stu-id="aad62-143">This feature enables the same API to be used by multiple clients with different data format requirements.</span></span>

> ### <a name="references--mapping-requests-to-responses"></a><span data-ttu-id="aad62-144">Odkazy – mapování požadavky na odpovědi</span><span class="sxs-lookup"><span data-stu-id="aad62-144">References – Mapping Requests to Responses</span></span>
> - <span data-ttu-id="aad62-145">**Směrování do akce Kontroleru**
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/routing></span><span class="sxs-lookup"><span data-stu-id="aad62-145">**Routing to Controller Actions**
<https://docs.microsoft.com/aspnet/core/mvc/controllers/routing></span></span>
> - <span data-ttu-id="aad62-146">**Model Binding** https://docs.microsoft.com/aspnet/core/mvc/models/model-binding</span><span class="sxs-lookup"><span data-stu-id="aad62-146">**Model Binding** https://docs.microsoft.com/aspnet/core/mvc/models/model-binding</span></span>
> - <span data-ttu-id="aad62-147">**Model Validation**
> <https://docs.microsoft.com/aspnet/core/mvc/models/validation></span><span class="sxs-lookup"><span data-stu-id="aad62-147">**Model Validation**
<https://docs.microsoft.com/aspnet/core/mvc/models/validation></span></span>
> - <span data-ttu-id="aad62-148">**Filters** https://docs.microsoft.com/aspnet/core/mvc/controllers/filters</span><span class="sxs-lookup"><span data-stu-id="aad62-148">**Filters** https://docs.microsoft.com/aspnet/core/mvc/controllers/filters</span></span>

## <a name="working-with-dependencies"></a><span data-ttu-id="aad62-149">Práce s závislosti</span><span class="sxs-lookup"><span data-stu-id="aad62-149">Working with Dependencies</span></span>

<span data-ttu-id="aad62-150">Má integrovanou podporu pro ASP.NET Core a interně využívá techniku známou jako [vkládání závislostí](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection).</span><span class="sxs-lookup"><span data-stu-id="aad62-150">ASP.NET Core has built-in support for and internally makes use of a technique known as [dependency injection](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection).</span></span> <span data-ttu-id="aad62-151">Vkládání závislostí je technika, který povolený volné párování mezi různé části aplikace.</span><span class="sxs-lookup"><span data-stu-id="aad62-151">Dependency injection is a technique that enabled loose coupling between different parts of an application.</span></span> <span data-ttu-id="aad62-152">Čím větší párování je žádoucí, protože umožňuje jednodušší izolace částí aplikace a umožňuje pro testování nebo pro nahrazení.</span><span class="sxs-lookup"><span data-stu-id="aad62-152">Looser coupling is desirable because it makes it easier to isolate parts of the application, allowing for testing or replacement.</span></span> <span data-ttu-id="aad62-153">Je také je méně pravděpodobné, že ke změně v jedné části aplikace bude mít neočekávané dopad někde jinde v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="aad62-153">It also makes it less likely that a change in one part of the application will have an unexpected impact somewhere else in the application.</span></span> <span data-ttu-id="aad62-154">Vkládání závislostí je založena na principu inverzi závislostí a často je klíčem k dosažení Princip otevřený nebo zavřený.</span><span class="sxs-lookup"><span data-stu-id="aad62-154">Dependency injection is based on the dependency inversion principle, and is often key to achieving the open/closed principle.</span></span> <span data-ttu-id="aad62-155">Při vyhodnocování, jak vaše aplikace funguje s jeho závislé součásti, pozor [statické plevami](http://deviq.com/static-cling/) kód pach a pamatovat aphorism "[nové je spojovací](http://ardalis.com/new-is-glue)."</span><span class="sxs-lookup"><span data-stu-id="aad62-155">When evaluating how your application works with its dependencies, beware of the [static cling](http://deviq.com/static-cling/) code smell, and remember the aphorism "[new is glue](http://ardalis.com/new-is-glue)."</span></span>

<span data-ttu-id="aad62-156">Statické plevami nastane, když volat statických metod třídy nebo přístup statické vlastnosti, které mají vedlejší účinky nebo v závislosti na infrastruktuře.</span><span class="sxs-lookup"><span data-stu-id="aad62-156">Static cling occurs when your classes make calls to static methods, or access static properties, which have side effects or dependencies on infrastructure.</span></span> <span data-ttu-id="aad62-157">Například pokud máte metodu, která volá statickou metodu, která zase zapisuje do databáze, způsob je úzce párované do databáze.</span><span class="sxs-lookup"><span data-stu-id="aad62-157">For example, if you have a method that calls a static method, which in turn writes to a database, your method is tightly coupled to the database.</span></span> <span data-ttu-id="aad62-158">Všechno, co dělí tohoto volání databáze dojde k přerušení metodu.</span><span class="sxs-lookup"><span data-stu-id="aad62-158">Anything that breaks that database call will break your method.</span></span> <span data-ttu-id="aad62-159">Testování tyto metody je často složité, protože tyto testy vyžadovala komerční mocking knihovny model statické volání, nebo může být testována pouze pomocí testovací databáze na místě.</span><span class="sxs-lookup"><span data-stu-id="aad62-159">Testing such methods is notoriously difficult, since such tests either require commercial mocking libraries to mock the static calls, or can only be tested with a test database in place.</span></span> <span data-ttu-id="aad62-160">Statické volání, které nemají žádné závislost na infrastrukturu, především těch, které jsou zcela bezstavové jsou volání a nemají žádný vliv na párování nebo testovatelnosti (kromě spojovacích kódu statických volání sám sebe).</span><span class="sxs-lookup"><span data-stu-id="aad62-160">Static calls that don't have any dependence on infrastructure, especially those that are completely stateless, are fine to call and have no impact on coupling or testability (beyond coupling code to the static call itself).</span></span>

<span data-ttu-id="aad62-161">Celá řada vývojářů pochopit rizika statické plevami a globální stav, ale bude stále úzce spojte svůj kód do konkrétní implementace prostřednictvím přímé vytváření instancí.</span><span class="sxs-lookup"><span data-stu-id="aad62-161">Many developers understand the risks of static cling and global state, but will still tightly couple their code to specific implementations through direct instantiation.</span></span> <span data-ttu-id="aad62-162">"Nové je spojovací" měl by být připomenutí tento párování a není obecné odsouzení použití new – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="aad62-162">"New is glue" is meant to be a reminder of this coupling, and not a general condemnation of the use of the new keyword.</span></span> <span data-ttu-id="aad62-163">Stejně jako s statickou metodu volání nové instance třídy typy, které nemají žádné externí závislosti obvykle není úzce spojte kód do implementace podrobnosti nebo se přesvědčte testování obtížnější.</span><span class="sxs-lookup"><span data-stu-id="aad62-163">Just as with static method calls, new instances of types that have no external dependencies typically do not tightly couple code to implementation details or make testing more difficult.</span></span> <span data-ttu-id="aad62-164">Ale pokaždé, když je vytvořena instance třídy, pozorně právě stručný zvažte, zda má smysl zakódovat tuto konkrétní instanci v tomto konkrétní umístění, nebo pokud je návrh s lepší požádat o dané instance jako závislost.</span><span class="sxs-lookup"><span data-stu-id="aad62-164">But each time a class is instantiated, take just a brief moment to consider whether it makes sense to hard-code that specific instance in that particular location, or if it would be a better design to request that instance as a dependency.</span></span>

### <a name="declare-your-dependencies"></a><span data-ttu-id="aad62-165">Deklarovat závislostmi</span><span class="sxs-lookup"><span data-stu-id="aad62-165">Declare Your Dependencies</span></span>

<span data-ttu-id="aad62-166">ASP.NET Core se vytváří přibližně s metody a třídy deklarovat jejich závislosti, je požádá jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="aad62-166">ASP.NET Core is built around having methods and classes declare their dependencies, requesting them as arguments.</span></span> <span data-ttu-id="aad62-167">Aplikace ASP.NET se obvykle nastavují ve spuštění třídy, které je nakonfigurován pro podporu vkládání závislostí na několika místech.</span><span class="sxs-lookup"><span data-stu-id="aad62-167">ASP.NET applications are typically set up in a Startup class, which itself is configured to support dependency injection at several points.</span></span> <span data-ttu-id="aad62-168">Pokud vaše třída při spuštění má konstruktor, může požádat o závislosti pomocí konstruktoru, například takto:</span><span class="sxs-lookup"><span data-stu-id="aad62-168">If your Startup class has a constructor, it can request dependencies through the constructor, like so:</span></span>

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

<span data-ttu-id="aad62-169">Třída při spuštění se zajímavé, že neexistují žádné požadavky explicitního typu pro ni.</span><span class="sxs-lookup"><span data-stu-id="aad62-169">The Startup class is interesting in that there are no explicit type requirements for it.</span></span> <span data-ttu-id="aad62-170">Není dědí speciální spuštění základní třídu, ani nebude implementovat žádné konkrétní rozhraní.</span><span class="sxs-lookup"><span data-stu-id="aad62-170">It doesn't inherit from a special Startup base class, nor does it implement any particular interface.</span></span> <span data-ttu-id="aad62-171">Můžete jí konstruktoru, nebo Ne, a můžete určit jako v mnoha parametry v konstruktoru tak, jak chcete.</span><span class="sxs-lookup"><span data-stu-id="aad62-171">You can give it a constructor, or not, and you can specify as many parameters on the constructor as you want.</span></span> <span data-ttu-id="aad62-172">Při spuštění webového hostitele, kterou jste nakonfigurovali pro vaše aplikace bude volat třída při spuštění, které jste ho na použití sdělili a použije k naplnění všechny závislosti, které vyžaduje třída při spuštění vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="aad62-172">When the web host you've configured for your application starts, it will call the Startup class you've told it to use, and will use dependency injection to populate any dependencies the Startup class requires.</span></span> <span data-ttu-id="aad62-173">Samozřejmě Pokud požádáte o parametry, které nejsou nakonfigurované v kontejneru služby používá ASP.NET Core, získáte výjimku, ale také přilepit k závislosti kontejneru zná, můžete požádat nic, co chcete.</span><span class="sxs-lookup"><span data-stu-id="aad62-173">Of course, if you request parameters that aren't configured in the services container used by ASP.NET Core, you'll get an exception, but as long as you stick to dependencies the container knows about, you can request anything you want.</span></span>

<span data-ttu-id="aad62-174">Vkládání závislostí je integrovaná do aplikace ASP.NET Core vpravo od začátku, při vytváření instance spuštění.</span><span class="sxs-lookup"><span data-stu-id="aad62-174">Dependency injection is built into your ASP.NET Core apps right from the start, when you create the Startup instance.</span></span> <span data-ttu-id="aad62-175">Zastavit není existuje pro třída při spuštění.</span><span class="sxs-lookup"><span data-stu-id="aad62-175">It doesn't stop there for the Startup class.</span></span> <span data-ttu-id="aad62-176">Můžete také vyžadovat závislosti v metodě konfigurace:</span><span class="sxs-lookup"><span data-stu-id="aad62-176">You can also request dependencies in the Configure method:</span></span>

```csharp
public void Configure(IApplicationBuilder app,
    IHostingEnvironment env,
    ILoggerFactory loggerFactory)
{

}
```

<span data-ttu-id="aad62-177">Metoda ConfigureServices je výjimka, která má toto chování; je nutné provést pouze jeden parametr typu IServiceCollection.</span><span class="sxs-lookup"><span data-stu-id="aad62-177">The ConfigureServices method is the exception to this behavior; it must take just one parameter of type IServiceCollection.</span></span> <span data-ttu-id="aad62-178">Není třeba skutečně podpoře vkládání závislostí, protože na jedné straně je zodpovědný za přidání objektů do kontejneru služby, a na dalších má přístup ke všem službám aktuálně nakonfigurovaný pomocí parametru IServiceCollection.</span><span class="sxs-lookup"><span data-stu-id="aad62-178">It doesn't really need to support dependency injection, since on the one hand it is responsible for adding objects to the services container, and on the other it has access to all currently configured services via the IServiceCollection parameter.</span></span> <span data-ttu-id="aad62-179">Proto můžete pracovat s závislosti, které jsou definované v kolekci služeb ASP.NET Core v každé části třída při spuštění, vyžaduje jako parametr potřebné služby, nebo ve spolupráci s IServiceCollection v ConfigureServices.</span><span class="sxs-lookup"><span data-stu-id="aad62-179">Thus, you can work with dependencies defined in the ASP.NET Core services collection in every part of the Startup class, either by requesting the needed service as a parameter or by working with the IServiceCollection in ConfigureServices.</span></span>

> [!NOTE]
> <span data-ttu-id="aad62-180">Pokud je potřeba zajistit, jsou k dispozici ke třídě spuštění určité služby, můžete je nakonfigurovat pomocí WebHostBuilder a jeho ConfigureServices metoda.</span><span class="sxs-lookup"><span data-stu-id="aad62-180">If you need to ensure certain services are available to your Startup class, you can configure them using WebHostBuilder and its ConfigureServices method.</span></span>

<span data-ttu-id="aad62-181">Třída při spuštění je model při volbě struktury dalších částí vaší aplikace ASP.NET Core, z řadičů pro Middleware filtrů vlastní Services.</span><span class="sxs-lookup"><span data-stu-id="aad62-181">The Startup class is a model for how you should structure other parts of your ASP.NET Core application, from Controllers to Middleware to Filters to your own Services.</span></span> <span data-ttu-id="aad62-182">V každém případě byste měli postupovat [explicitní závislosti Princip](http://deviq.com/explicit-dependencies-principle/), požaduje závislostmi místo přímo jejich vytváření a využitím vkládání závislostí v celé vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="aad62-182">In each case, you should follow the [Explicit Dependencies Principle](http://deviq.com/explicit-dependencies-principle/), requesting your dependencies rather than directly creating them, and leveraging dependency injection throughout your application.</span></span> <span data-ttu-id="aad62-183">Dávejte pozor, kde a jak přímo doložit implementace, zejména služeb a objekty, které práce s infrastrukturou, nebo vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="aad62-183">Be careful of where and how you directly instantiate implementations, especially services and objects that work with infrastructure or have side effects.</span></span> <span data-ttu-id="aad62-184">Dáváte přednost práci s abstrakce definované v vaše základní aplikace a jako argumenty předané do hardcoding odkazy na konkrétní implementace typy.</span><span class="sxs-lookup"><span data-stu-id="aad62-184">Prefer working with abstractions defined in your application core and passed in as arguments to hardcoding references to specific implementation types.</span></span>

## <a name="structuring-the-application"></a><span data-ttu-id="aad62-185">Strukturování aplikace</span><span class="sxs-lookup"><span data-stu-id="aad62-185">Structuring the Application</span></span>

<span data-ttu-id="aad62-186">Monolitický aplikace obvykle mají jeden vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="aad62-186">Monolithic applications typically have a single entry point.</span></span> <span data-ttu-id="aad62-187">V případě webová aplikace ASP.NET Core vstupní bod budou webového projektu ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="aad62-187">In the case of an ASP.NET Core web application, the entry point will be the ASP.NET Core web project.</span></span> <span data-ttu-id="aad62-188">Však neznamená, že řešení by měla obsahovat právě jeden projekt.</span><span class="sxs-lookup"><span data-stu-id="aad62-188">However, that doesn't mean the solution should consist of just a single project.</span></span> <span data-ttu-id="aad62-189">Je užitečné rozdělit aplikaci do různých vrstev, abyste podle oddělené oblasti zájmu.</span><span class="sxs-lookup"><span data-stu-id="aad62-189">It's useful to break up the application into different layers in order to follow separation of concerns.</span></span> <span data-ttu-id="aad62-190">Jakmile rozdělit do vrstvy, je vhodné nad rámec složky jednotlivé projekty, které může pomoci dosáhnout lepší zapouzdření.</span><span class="sxs-lookup"><span data-stu-id="aad62-190">Once broken up into layers, it's helpful to go beyond folders to separate projects, which can help achieve better encapsulation.</span></span> <span data-ttu-id="aad62-191">Nejlepší metodou k dosažení těchto cílů s aplikací ASP.NET Core se odlišuje od architektuře čistého popsané v kapitole 5.</span><span class="sxs-lookup"><span data-stu-id="aad62-191">The best approach to achieve these goals with an ASP.NET Core application is a variation of the Clean Architecture discussed in chapter 5.</span></span> <span data-ttu-id="aad62-192">Následující tento přístup řešení aplikace budou tvořit samostatné knihovny uživatelského rozhraní, infrastruktury a ApplicationCore.</span><span class="sxs-lookup"><span data-stu-id="aad62-192">Following this approach, the application's solution will be comprised of separate libraries for the UI, Infrastructure, and ApplicationCore.</span></span>

<span data-ttu-id="aad62-193">Kromě těchto projekty samostatné testovací projekty jsou zahrnuty také (testování je popsané v kapitole 9).</span><span class="sxs-lookup"><span data-stu-id="aad62-193">In addition to these projects, separate test projects are included as well (Testing is discussed in Chapter 9).</span></span>

<span data-ttu-id="aad62-194">Objektový model aplikace a rozhraní musí být umístěny v ApplicationCore projektu.</span><span class="sxs-lookup"><span data-stu-id="aad62-194">The application's object model and interfaces should be placed in the ApplicationCore project.</span></span> <span data-ttu-id="aad62-195">Tento projekt budou mít co nejméně závislosti nejdříve a další projekty v řešení bude odkazovat ho.</span><span class="sxs-lookup"><span data-stu-id="aad62-195">This project will have as few dependencies as possible, and the other projects in the solution will reference it.</span></span> <span data-ttu-id="aad62-196">Obchodní entity, které je třeba nastavit jako trvalý, jsou definovány v projektu ApplicationCore, jako jsou služby, které přímo nezávisí na infrastruktuře.</span><span class="sxs-lookup"><span data-stu-id="aad62-196">Business entities that need to be persisted are defined in the ApplicationCore project, as are services that do not directly depend on infrastructure.</span></span>

<span data-ttu-id="aad62-197">Podrobnosti implementace, například jak se provádí trvalost nebo jak může být odeslána oznámení pro uživatele, jsou uchovány v projektu infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="aad62-197">Implementation details, such as how persistence is performed or how notifications might be sent to a user, are kept in the Infrastructure project.</span></span> <span data-ttu-id="aad62-198">Tento projekt bude odkazovat na konkrétní implementace balíčků, jako jsou Entity Framework Core, ale by neměli zveřejňovat podrobnosti o těchto implementace mimo projekt.</span><span class="sxs-lookup"><span data-stu-id="aad62-198">This project will reference implementation-specific packages such as Entity Framework Core, but should not expose details about these implementations outside of the project.</span></span> <span data-ttu-id="aad62-199">Infrastruktura služby a úložiště musí implementovat rozhraní, které jsou definovány v projektu ApplicationCore a jeho implementace trvalost jsou zodpovědní za načítání a ukládání entit definované v ApplicationCore.</span><span class="sxs-lookup"><span data-stu-id="aad62-199">Infrastructure services and repositories should implement interfaces that are defined in the ApplicationCore project, and its persistence implementations are responsible for retrieving and storing entities defined in ApplicationCore.</span></span>

<span data-ttu-id="aad62-200">Samotného projektu ASP.NET Core je zodpovědná za nejasností kontaktovali úrovně uživatelského rozhraní, ale nesmí obsahovat obchodní logiku nebo infrastrukturu podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="aad62-200">The ASP.NET Core project itself is responsible for any UI level concerns, but should not include business logic or infrastructure details.</span></span> <span data-ttu-id="aad62-201">Ve skutečnosti v ideálním případě by neměl i mít závislost na projekt infrastruktury, který vám pomůže zajistit, že žádná závislost mezi dva projekty uvádíme omylem.</span><span class="sxs-lookup"><span data-stu-id="aad62-201">In fact, ideally it shouldn't even have a dependency on the Infrastructure project, which will help ensure no dependency between the two projects is introduced accidentally.</span></span> <span data-ttu-id="aad62-202">Toho lze dosáhnout pomocí kontejner DI jiných výrobců jako StructureMap, který umožňuje definovat pravidla DI v registru třídy v každém projektu.</span><span class="sxs-lookup"><span data-stu-id="aad62-202">This can be achieved using a third-party DI container like StructureMap, which allows you to define DI rules in Registry classes in each project.</span></span>

<span data-ttu-id="aad62-203">Další postup pro aplikace z podrobnosti implementace oddělení je mikroslužeb volání aplikace, pravděpodobně nasazený v jednotlivých kontejnerech Docker.</span><span class="sxs-lookup"><span data-stu-id="aad62-203">Another approach to decoupling the application from implementation details is to have the application call microservices, perhaps deployed in individual Docker containers.</span></span> <span data-ttu-id="aad62-204">To poskytuje ještě větší oddělení otázky a oddělení než využití DI mezi dva projekty, ale má zvýšenou složitostí.</span><span class="sxs-lookup"><span data-stu-id="aad62-204">This provides even greater separation of concerns and decoupling than leveraging DI between two projects, but has additional complexity.</span></span>

### <a name="feature-organization"></a><span data-ttu-id="aad62-205">Funkce organizace</span><span class="sxs-lookup"><span data-stu-id="aad62-205">Feature Organization</span></span>

<span data-ttu-id="aad62-206">Ve výchozím nastavení aplikace ASP.NET Core uspořádat jejich struktura složek, například řadiče a zobrazení a často ViewModels.</span><span class="sxs-lookup"><span data-stu-id="aad62-206">By default, ASP.NET Core applications organize their folder structure to include Controllers and Views, and frequently ViewModels.</span></span> <span data-ttu-id="aad62-207">Kódu na straně klienta pro podporu těchto struktur serverové je obvykle uložen samostatně ve složce wwwroot.</span><span class="sxs-lookup"><span data-stu-id="aad62-207">Client-side code to support these server-side structures is typically stored separately in the wwwroot folder.</span></span> <span data-ttu-id="aad62-208">Však velké aplikace setkat s problémy u této organizace, protože funguje na jakékoli dané funkce často vyžaduje přechod mezi tyto složky.</span><span class="sxs-lookup"><span data-stu-id="aad62-208">However, large applications may encounter problems with this organization, since working on any given feature often requires jumping between these folders.</span></span> <span data-ttu-id="aad62-209">To získá mnohem obtížnější počet soubory a podsložky ve složce každého roste, což vede k značnou část posouvání pomocí Průzkumníka řešení.</span><span class="sxs-lookup"><span data-stu-id="aad62-209">This gets more and more difficult as the number of files and subfolders in each folder grows, resulting in a great deal of scrolling through Solution Explorer.</span></span> <span data-ttu-id="aad62-210">Jedno řešení tohoto problému, je uspořádat kódu aplikace pomocí *funkce* místo pomocí typ souboru.</span><span class="sxs-lookup"><span data-stu-id="aad62-210">One solution to this problem is to organize application code by *feature* instead of by file type.</span></span> <span data-ttu-id="aad62-211">Tato organizace styl se obvykle označuje jako funkce složek nebo funkce řezy (viz také: [svislé řezy](http://deviq.com/vertical-slices/)).</span><span class="sxs-lookup"><span data-stu-id="aad62-211">This organizational style is typically referred to as feature folders or feature slices (see also: [Vertical Slices](http://deviq.com/vertical-slices/)).</span></span>

<span data-ttu-id="aad62-212">Jádro ASP.NET MVC podporuje oblasti pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="aad62-212">ASP.NET Core MVC supports Areas for this purpose.</span></span> <span data-ttu-id="aad62-213">Použití oblastí, můžete vytvořit samostatné sady řadiče a zobrazení složky (stejně jako žádné přidružené modely) v každé oblasti složky.</span><span class="sxs-lookup"><span data-stu-id="aad62-213">Using areas, you can create separate sets of Controllers and Views folders (as well as any associated models) in each Area folder.</span></span> <span data-ttu-id="aad62-214">Obrázek 7-1 zobrazuje strukturu složky příklad pomocí oblastí.</span><span class="sxs-lookup"><span data-stu-id="aad62-214">Figure 7-1 shows an example folder structure, using Areas.</span></span>

![](./media/image7-1.png)

<span data-ttu-id="aad62-215">Obrázek 7-1 ukázka oblasti organizace</span><span class="sxs-lookup"><span data-stu-id="aad62-215">Figure 7-1 Sample Area Organization</span></span>

<span data-ttu-id="aad62-216">Při použití oblastí, je nutné použít atributy pro uspořádání řadičů s název oblasti, do které patří:</span><span class="sxs-lookup"><span data-stu-id="aad62-216">When using Areas, you must use attributes to decorate your controllers with the name of the area to which they belong:</span></span>

```csharp
[Area("Catalog")]
public class HomeController
{}
```

<span data-ttu-id="aad62-217">Musíte taky přidat podporu oblasti trasy:</span><span class="sxs-lookup"><span data-stu-id="aad62-217">You also need to add area support to your routes:</span></span>

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

<span data-ttu-id="aad62-218">Kromě integrovanou podporu pro oblasti můžete také použít vlastní struktury složek a pravidla týkající se místo atributy a vlastní trasy.</span><span class="sxs-lookup"><span data-stu-id="aad62-218">In addition to the built-in support for Areas, you can also use your own folder structure, and conventions in place of attributes and custom routes.</span></span> <span data-ttu-id="aad62-219">To by umožnilo mít složky funkce, které nezahrnuli samostatné složky pro zobrazení, řadičů, atd., udržování plošší hierarchii a usnadnit zobrazte že všechny související soubory na jednom místě, pro každou funkci.</span><span class="sxs-lookup"><span data-stu-id="aad62-219">This would allow you to have feature folders that didn't include separate folders for Views, Controllers, etc., keeping the hierarchy flatter and making it easier to see all related files in a single place for each feature.</span></span>

<span data-ttu-id="aad62-220">ASP.NET Core používá integrované konvence typy mohla kontrolovat své chování.</span><span class="sxs-lookup"><span data-stu-id="aad62-220">ASP.NET Core uses built-in convention types to control its behavior.</span></span> <span data-ttu-id="aad62-221">Můžete upravit nebo nahradit tyto konvence.</span><span class="sxs-lookup"><span data-stu-id="aad62-221">You can modify or replace these conventions.</span></span> <span data-ttu-id="aad62-222">Můžete například vytvořit názvů, který automaticky získá název funkce pro daný kontroler založený na jeho oboru názvů (což obvykle korelaci do složky, ve kterém se nachází řadičem):</span><span class="sxs-lookup"><span data-stu-id="aad62-222">For example, you can create a convention that will automatically get the feature name for a given controller based on its namespace (which typically correlates to the folder in which the controller is located):</span></span>

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

<span data-ttu-id="aad62-223">Potom zadejte touto konvencí jako možnost při přidání podpory pro rozhraní MVC do vaší aplikace v ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="aad62-223">You then specify this convention as an option when you add support for MVC to your application in ConfigureServices:</span></span>

```csharp
services.AddMvc(o => o.Conventions.Add(new FeatureConvention()));
```

<span data-ttu-id="aad62-224">Jádro ASP.NET MVC také používá konvenci k vyhledání zobrazení.</span><span class="sxs-lookup"><span data-stu-id="aad62-224">ASP.NET Core MVC also uses a convention to locate views.</span></span> <span data-ttu-id="aad62-225">Lze jej přepsat pomocí vlastních názvů tak, aby zobrazení budou umístěny ve vašich složkách funkce (s použitím názvu funkce poskytované FeatureConvention, výše).</span><span class="sxs-lookup"><span data-stu-id="aad62-225">You can override it with a custom convention so that views will be located in your feature folders (using the feature name provided by the FeatureConvention, above).</span></span> <span data-ttu-id="aad62-226">Můžete získat další informace o tento přístup a stáhnout ukázku práce z článku na webu MSDN [řezy funkce pro ASP.NET MVC základní](https://msdn.microsoft.com/magazine/mt763233.aspx).</span><span class="sxs-lookup"><span data-stu-id="aad62-226">You can learn more about this approach and download a working sample from the MSDN article, [Feature Slices for ASP.NET Core MVC](https://msdn.microsoft.com/magazine/mt763233.aspx).</span></span>

### <a name="cross-cutting-concerns"></a><span data-ttu-id="aad62-227">Mezi vyjímání otázky</span><span class="sxs-lookup"><span data-stu-id="aad62-227">Cross-Cutting Concerns</span></span>

<span data-ttu-id="aad62-228">Jelikož aplikace, bude stále důležité zohlednit se mezi vyjímání otázky k odstranění duplicity a zajistit konzistenci.</span><span class="sxs-lookup"><span data-stu-id="aad62-228">As applications grow, it becomes increasingly important to factor out cross-cutting concerns to eliminate duplication and maintain consistency.</span></span> <span data-ttu-id="aad62-229">Některé příklady mezi vyjímání obavy v aplikacích ASP.NET Core jsou ověřování, pravidla ověřování modelu, ukládání výstupu do mezipaměti a zpracování chyb, i když existuje mnoho dalších.</span><span class="sxs-lookup"><span data-stu-id="aad62-229">Some examples of cross-cutting concerns in ASP.NET Core applications are authentication, model validation rules, output caching, and error handling, though there are many others.</span></span> <span data-ttu-id="aad62-230">Jádro ASP.NET MVC [filtry](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters) vám umožní spustit kód před nebo po určité kroky v kanálu zpracování požadavků.</span><span class="sxs-lookup"><span data-stu-id="aad62-230">ASP.NET Core MVC [filters](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters) allow you to run code before or after certain steps in the request processing pipeline.</span></span> <span data-ttu-id="aad62-231">Například filtr můžete spustit před a po vazby modelu, před a po akci, nebo před a po výsledek akce.</span><span class="sxs-lookup"><span data-stu-id="aad62-231">For instance, a filter can run before and after model binding, before and after an action, or before and after an action's result.</span></span> <span data-ttu-id="aad62-232">Filtr autorizace můžete také použít k řízení přístupu k zbytek kanálu.</span><span class="sxs-lookup"><span data-stu-id="aad62-232">You can also use an authorization filter to control access to the rest of the pipeline.</span></span> <span data-ttu-id="aad62-233">Obrázky 7-2 ukazuje jak požadavek provádění toky filtry, pokud nakonfigurovaný.</span><span class="sxs-lookup"><span data-stu-id="aad62-233">Figures 7-2 shows how request execution flows through filters, if configured.</span></span>

![Filtry autorizace, filtry prostředků, vazby modelu, filtry akce, provádění akce a akce výsledek převodu, filtry výjimek, filtry výsledků a výsledek spuštění zpracování žádosti.](./media/image7-2.png)

<span data-ttu-id="aad62-236">Obrázek 7-2 žádost o spuštění přes filtry a požadavku kanálu.</span><span class="sxs-lookup"><span data-stu-id="aad62-236">Figure 7-2 Request execution through filters and request pipeline.</span></span>

<span data-ttu-id="aad62-237">Filtry jsou obvykle implementovány jako atributy, abyste je mohli použít, řadiče nebo akce.</span><span class="sxs-lookup"><span data-stu-id="aad62-237">Filters are usually implemented as attributes, so you can apply them controllers or actions.</span></span> <span data-ttu-id="aad62-238">Při přidání tímto způsobem, filtry zadaná na úrovni přepsání akce nebo sestavení při filtry zadané na úrovni kontroleru, který sami přepsat globální filtry.</span><span class="sxs-lookup"><span data-stu-id="aad62-238">When added in this fashion, filters specified at the action level override or build upon filters specified at the controller level, which themselves override global filters.</span></span> <span data-ttu-id="aad62-239">Například \[trasy\] atributu lze vytvořit trasy mezi službami kontrolery a akce.</span><span class="sxs-lookup"><span data-stu-id="aad62-239">For example, the \[Route\] attribute can be used to build up routes between controllers and actions.</span></span> <span data-ttu-id="aad62-240">Podobně autorizace můžete nakonfigurovat na úrovni kontroleru a pak přepsat jednotlivé akce, jako ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="aad62-240">Likewise, authorization can be configured at the controller level, and then overridden by individual actions, as the following sample demonstrates:</span></span>

```csharp
[Authorize]
public class AccountController : Controller

{
    [AllowAnonymous]
    public async Task<IActionResult> Login() {}
    public async Task<IActionResult> ForgotPassword() {}
}
```

<span data-ttu-id="aad62-241">První metoda přihlášení, využívá filtr AllowAnonymous (atribut) pro přepsání filtru autorizovat nastavit na úrovni kontroleru.</span><span class="sxs-lookup"><span data-stu-id="aad62-241">The first method, Login, uses the AllowAnonymous filter (attribute) to override the Authorize filter set at the controller level.</span></span> <span data-ttu-id="aad62-242">Požadavek na ověřeného bude vyžadovat akce ForgotPassword (a provedení dalších akcí ve třídě, která nemá atribut AllowAnonymous).</span><span class="sxs-lookup"><span data-stu-id="aad62-242">The ForgotPassword action (and any other action in the class that doesn't have an AllowAnonymous attribute) will require an authenticated request.</span></span>

<span data-ttu-id="aad62-243">K vyloučení duplikace ve formě běžné Chyba při zpracování zásady pro rozhraní API můžete použít filtry.</span><span class="sxs-lookup"><span data-stu-id="aad62-243">Filters can be used to eliminate duplication in the form of common error handling policies for APIs.</span></span> <span data-ttu-id="aad62-244">Typické zásada rozhraní API je například vrátí serveru odpovědí na požadavky odkazující na klíče, které nejsou k dispozici a struktura BadRequest odpověď, pokud selže ověření modelu.</span><span class="sxs-lookup"><span data-stu-id="aad62-244">For example, a typical API policy is to return a NotFound response to requests referencing keys that do not exist, and a BadRequest response if model validation fails.</span></span> <span data-ttu-id="aad62-245">Následující příklad ukazuje tyto dvě zásady v akci:</span><span class="sxs-lookup"><span data-stu-id="aad62-245">The following example demonstrates these two policies in action:</span></span>

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

<span data-ttu-id="aad62-246">Nepovolit vaší metody akce k zaplní podmíněného kód takto.</span><span class="sxs-lookup"><span data-stu-id="aad62-246">Don't allow your action methods to become cluttered with conditional code like this.</span></span> <span data-ttu-id="aad62-247">Místo toho načítat zásady do filtry, které mohou být použity na podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="aad62-247">Instead, pull the policies into filters that can be applied on an as-needed basis.</span></span> <span data-ttu-id="aad62-248">Kontrola ověření modelu, která by měl nastat, když je odeslán příkaz do rozhraní API, můžete v tomto příkladu nahrazuje následující atribut:</span><span class="sxs-lookup"><span data-stu-id="aad62-248">In this example, the model validation check, which should occur any time a command is sent to the API, can be replaced by the following attribute:</span></span>

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

<span data-ttu-id="aad62-249">Podobně filtr slouží ke kontrole Pokud záznam existuje a vrátí 404, před provedením akce, takže není nutné provádět tyto kontroly v akci.</span><span class="sxs-lookup"><span data-stu-id="aad62-249">Likewise, a filter can be used to check if a record exists and return a 404 before the action is executed, eliminating the need to perform these checks in the action.</span></span> <span data-ttu-id="aad62-250">Jakmile jste výseče běžné konvence a uspořádány řešení infrastruktury kódu a obchodní logiku nezávislá na vaše uživatelské prostředí, by měla být velmi dynamické vaší metody akce MVC:</span><span class="sxs-lookup"><span data-stu-id="aad62-250">Once you've pulled out common conventions and organized your solution to separate infrastructure code and business logic from your UI, your MVC action methods should be extremely thin:</span></span>

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

<span data-ttu-id="aad62-251">Další informace o implementaci filtry a stáhnout ukázku práce z článku na webu MSDN [skutečné World ASP.NET Core MVC filtry](https://msdn.microsoft.com/magazine/mt767699.aspx).</span><span class="sxs-lookup"><span data-stu-id="aad62-251">You can read more about implementing filters and download a working sample from the MSDN article, [Real World ASP.NET Core MVC Filters](https://msdn.microsoft.com/magazine/mt767699.aspx).</span></span>

> ### <a name="references--structuring-applications"></a><span data-ttu-id="aad62-252">Odkazy – strukturování aplikace</span><span class="sxs-lookup"><span data-stu-id="aad62-252">References – Structuring Applications</span></span>
> - <span data-ttu-id="aad62-253">**Oblasti**</span><span class="sxs-lookup"><span data-stu-id="aad62-253">**Areas**</span></span>  
> <span data-ttu-id="aad62-254"><https://docs.microsoft.com/aspnet/core/mvc/controllers/areas></span><span class="sxs-lookup"><span data-stu-id="aad62-254"><https://docs.microsoft.com/aspnet/core/mvc/controllers/areas></span></span>
> - <span data-ttu-id="aad62-255">**MSDN – funkce řezy pro jádro ASP.NET MVC**
>  <https://msdn.microsoft.com/magazine/mt763233.aspx></span><span class="sxs-lookup"><span data-stu-id="aad62-255">**MSDN – Feature Slices for ASP.NET Core MVC**
<https://msdn.microsoft.com/magazine/mt763233.aspx></span></span>
> - <span data-ttu-id="aad62-256">**Filtry**</span><span class="sxs-lookup"><span data-stu-id="aad62-256">**Filters**</span></span>  
> <span data-ttu-id="aad62-257"><https://docs.microsoft.com/aspnet/core/mvc/controllers/filters></span><span class="sxs-lookup"><span data-stu-id="aad62-257"><https://docs.microsoft.com/aspnet/core/mvc/controllers/filters></span></span>
> - <span data-ttu-id="aad62-258">**MSDN – skutečných jádro ASP.NET MVC filtry**</span><span class="sxs-lookup"><span data-stu-id="aad62-258">**MSDN – Real World ASP.NET Core MVC Filters**</span></span>  
> <span data-ttu-id="aad62-259"><https://msdn.microsoft.com/magazine/mt767699.aspx></span><span class="sxs-lookup"><span data-stu-id="aad62-259"><https://msdn.microsoft.com/magazine/mt767699.aspx></span></span>

## <a name="security"></a><span data-ttu-id="aad62-260">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="aad62-260">Security</span></span>

<span data-ttu-id="aad62-261">Zabezpečení webových aplikací je velké téma, mnoho aspektů.</span><span class="sxs-lookup"><span data-stu-id="aad62-261">Securing web applications is a large topic, with many considerations.</span></span> <span data-ttu-id="aad62-262">Na nejzákladnější úrovni zahrnuje zabezpečení zajistíte, že budete vědět, kdo je pocházejících z daného požadavku a zajistit, že tento požadavek má jenom přístup k prostředkům, které by měl.</span><span class="sxs-lookup"><span data-stu-id="aad62-262">At its most basic level, security involves ensuring you know who a given request is coming from, and then ensuring that that request only has access to resources it should.</span></span> <span data-ttu-id="aad62-263">Ověřování je proces porovnávání přihlašovací údaje se žádostí o definicím v úložišti důvěryhodných dat, pokud chcete zobrazit, pokud by se jako pocházející ze známé entity zpracovávat žádosti.</span><span class="sxs-lookup"><span data-stu-id="aad62-263">Authentication is the process of comparing credentials provided with a request to those in a trusted data store, to see if the request should be treated as coming from a known entity.</span></span> <span data-ttu-id="aad62-264">Autorizace je proces omezení přístupu k určitým prostředkům na základě identity uživatele.</span><span class="sxs-lookup"><span data-stu-id="aad62-264">Authorization is the process of restricting access to certain resources based on user identity.</span></span> <span data-ttu-id="aad62-265">Třetí potíže se zabezpečením chrání požadavky založenými na odposlechu třetích stran, pro které byste měli aspoň [Ujistěte se, že vaše aplikace používá protokol SSL](https://docs.microsoft.com/aspnet/core/security/enforcing-ssl).</span><span class="sxs-lookup"><span data-stu-id="aad62-265">A third security concern is protecting requests from eavesdropping by third parties, for which you should at least [ensure that SSL is used by your application](https://docs.microsoft.com/aspnet/core/security/enforcing-ssl).</span></span>

### <a name="authentication"></a><span data-ttu-id="aad62-266">Ověřování</span><span class="sxs-lookup"><span data-stu-id="aad62-266">Authentication</span></span>

<span data-ttu-id="aad62-267">Identita ASP.NET Core je systém členství, které můžete použít k podpoře funkce přihlašování pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="aad62-267">ASP.NET Core Identity is a membership system you can use to support login functionality for your application.</span></span> <span data-ttu-id="aad62-268">Obsahuje podporu pro místní uživatelské účty a také podpora zprostředkovatele externí přihlášení od poskytovatelů, jako je Microsoft Account, Twitter, Facebook, Google a další.</span><span class="sxs-lookup"><span data-stu-id="aad62-268">It has support for local user accounts as well as external login provider support from providers like Microsoft Account, Twitter, Facebook, Google, and more.</span></span> <span data-ttu-id="aad62-269">Kromě ASP.NET Core Identity, vaše aplikace může použít ověřování systému windows nebo jako poskytovatel identity jiného výrobce [serveru identit](https://github.com/IdentityServer/IdentityServer4).</span><span class="sxs-lookup"><span data-stu-id="aad62-269">In addition to ASP.NET Core Identity, your application can use windows authentication, or a third-party identity provider like [Identity Server](https://github.com/IdentityServer/IdentityServer4).</span></span>

<span data-ttu-id="aad62-270">Jádro ASP.NET Identity je součástí nové šablony projektu, pokud je vybrána možnost jednotlivé uživatelské účty.</span><span class="sxs-lookup"><span data-stu-id="aad62-270">ASP.NET Core Identity is included in new project templates if the Individual User Accounts option is selected.</span></span> <span data-ttu-id="aad62-271">Tato šablona zahrnuje podporu registrace, přihlášení, externí přihlášení, zapomenutým heslům a další funkce.</span><span class="sxs-lookup"><span data-stu-id="aad62-271">This template includes support for registration, login, external logins, forgotten passwords, and additional functionality.</span></span>

![](./media/image7-3.png)

<span data-ttu-id="aad62-272">Obrázek 7-3 vyberte jednotlivé uživatelské účty tak, aby měl předkonfigurované Identity.</span><span class="sxs-lookup"><span data-stu-id="aad62-272">Figure 7-3 Select Individual User Accounts to have Identity preconfigured.</span></span>

<span data-ttu-id="aad62-273">Podpora identit je nakonfigurované ve spuštění v ConfigureServices i konfigurace:</span><span class="sxs-lookup"><span data-stu-id="aad62-273">Identity support is configured in Startup, both in ConfigureServices and Configure:</span></span>

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

<span data-ttu-id="aad62-274">Je důležité, aby UseIdentity zobrazí před UseMvc v metodě konfigurace.</span><span class="sxs-lookup"><span data-stu-id="aad62-274">It's important that UseIdentity appear before UseMvc in the Configure method.</span></span> <span data-ttu-id="aad62-275">Při konfiguraci Identity v ConfigureServices, můžete si všimnout volání AddDefaultTokenProviders.</span><span class="sxs-lookup"><span data-stu-id="aad62-275">When configuring Identity in ConfigureServices, you'll notice a call to AddDefaultTokenProviders.</span></span> <span data-ttu-id="aad62-276">Tato akce nemá co dělat s tokeny, které slouží k zabezpečení komunikace webových, ale místo toho odkazuje na zprostředkovatele, které vytvářejí výzvy, které může být uživatelům odešle přes SMS nebo e-mailu v pořadí pro ně potvrdit svou identitu.</span><span class="sxs-lookup"><span data-stu-id="aad62-276">This has nothing to do with tokens that may be used to secure web communications, but instead refers to providers that create prompts that can be sent to users via SMS or email in order for them to confirm their identity.</span></span>

<span data-ttu-id="aad62-277">Další informace o [konfigurace dvoufaktorové ověřování](https://docs.microsoft.com/aspnet/core/security/authentication/2fa) a [povolení zprostředkovatele externí přihlášení](https://docs.microsoft.com/aspnet/core/security/authentication/social/) z oficiální dokumentaci ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="aad62-277">You can learn more about [configuring two-factor authentication](https://docs.microsoft.com/aspnet/core/security/authentication/2fa) and [enabling external login providers](https://docs.microsoft.com/aspnet/core/security/authentication/social/) from the official ASP.NET Core docs.</span></span>

### <a name="authorization"></a><span data-ttu-id="aad62-278">Autorizace</span><span class="sxs-lookup"><span data-stu-id="aad62-278">Authorization</span></span>

<span data-ttu-id="aad62-279">Nejjednodušší forma autorizace zahrnuje omezení přístupu pro anonymní uživatele.</span><span class="sxs-lookup"><span data-stu-id="aad62-279">The simplest form of authorization involves restricting access to anonymous users.</span></span> <span data-ttu-id="aad62-280">Toho lze dosáhnout jednoduše použitím \[Autorizovat\] atribut určité řadiče nebo akce.</span><span class="sxs-lookup"><span data-stu-id="aad62-280">This can be achieved by simply applying the \[Authorize\] attribute to certain controllers or actions.</span></span> <span data-ttu-id="aad62-281">Pokud role se používají, atribut můžete omezit přístup pro uživatele, kteří patří do určité role, jak je vidět další rozšířené:</span><span class="sxs-lookup"><span data-stu-id="aad62-281">If roles are being used, the attribute can be further extended to restrict access to users who belong to certain roles, as shown:</span></span>

```csharp
[Authorize(Roles = "HRManager,Finance")]
public class SalaryController : Controller
{

}
```

<span data-ttu-id="aad62-282">V takovém případě by uživatelé, kteří patří buď HRManager nebo finanční rolí (nebo obě) mít přístup k SalaryController.</span><span class="sxs-lookup"><span data-stu-id="aad62-282">In this case, users belonging to either the HRManager or Finance roles (or both) would have access to the SalaryController.</span></span> <span data-ttu-id="aad62-283">Pokud chcete vyžadovat, aby uživatel patří do více rolí, (nikoli pouze jeden z několika), můžete použít atribut vícekrát, zadáte požadované role pokaždé, když.</span><span class="sxs-lookup"><span data-stu-id="aad62-283">To require that a user belong to multiple roles (not just one of several), you can apply the attribute multiple times, specifying a required role each time.</span></span>

<span data-ttu-id="aad62-284">Zadání určité sady role jako řetězce v mnoha různých kontrolery a akce může vést k nežádoucího opakování.</span><span class="sxs-lookup"><span data-stu-id="aad62-284">Specifying certain sets of roles as strings in many different controllers and actions can lead to undesirable repetition.</span></span> <span data-ttu-id="aad62-285">Můžete nakonfigurovat zásady autorizace, které zapouzdření autorizační pravidla, a poté zadejte zásady místo jednotlivých rolí při použití \[Autorizovat\] atribut:</span><span class="sxs-lookup"><span data-stu-id="aad62-285">You can configure authorization policies, which encapsulate authorization rules, and then specify the policy instead of individual roles when applying the \[Authorize\] attribute:</span></span>

```csharp
[Authorize(Policy = "CanViewPrivateReport")]
public IActionResult ExecutiveSalaryReport()
{
    return View();
}
```

<span data-ttu-id="aad62-286">Pomocí zásad tímto způsobem, můžete oddělit druhy akce je omezená z konkrétní role nebo pravidla, která se použije na ni.</span><span class="sxs-lookup"><span data-stu-id="aad62-286">Using policies in this way, you can separate the kinds of actions being restricted from the specific roles or rules that apply to it.</span></span> <span data-ttu-id="aad62-287">Později, pokud vytvoříte novou roli, která potřebuje přístup k určitým prostředkům, můžete pouze aktualizovat zásady, nikoli aktualizace každých seznam rolí na každý \[Autorizovat\] atribut.</span><span class="sxs-lookup"><span data-stu-id="aad62-287">Later, if you create a new role that needs to have access to certain resources, you can just update a policy, rather than updating every list of roles on every \[Authorize\] attribute.</span></span>

#### <a name="claims"></a><span data-ttu-id="aad62-288">Deklarace identity</span><span class="sxs-lookup"><span data-stu-id="aad62-288">Claims</span></span>

<span data-ttu-id="aad62-289">Deklarace identity jsou páry název hodnota, které představují vlastnosti ověřeného uživatele.</span><span class="sxs-lookup"><span data-stu-id="aad62-289">Claims are name value pairs that represent properties of an authenticated user.</span></span> <span data-ttu-id="aad62-290">Číslo zaměstnance uživatelů může například uložit jako deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="aad62-290">For example, you might store users' employee number as a claim.</span></span> <span data-ttu-id="aad62-291">Deklarace identity pak lze v rámci zásad autorizace.</span><span class="sxs-lookup"><span data-stu-id="aad62-291">Claims can then be used as part of authorization policies.</span></span> <span data-ttu-id="aad62-292">Můžete vytvořit zásadu s názvem "EmployeeOnly", musí existovat deklarace názvem "Číslo_zaměstnance", jak je uvedeno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="aad62-292">You could create a policy called "EmployeeOnly" that requires the existence of a claim called "EmployeeNumber", as shown in this example:</span></span>

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

<span data-ttu-id="aad62-293">Tato zásada se pak může pomocí \[Autorizovat\] atribut k ochraně všech kontroleru a akce, jak je popsáno výše.</span><span class="sxs-lookup"><span data-stu-id="aad62-293">This policy could then be used with the \[Authorize\] attribute to protect any controller and/or action, as described above.</span></span>

#### <a name="securing-web-apis"></a><span data-ttu-id="aad62-294">Zabezpečení rozhraní Web API</span><span class="sxs-lookup"><span data-stu-id="aad62-294">Securing Web APIs</span></span>

<span data-ttu-id="aad62-295">Většina webových rozhraní API by měla implementovat ověřování na základě tokenu systému.</span><span class="sxs-lookup"><span data-stu-id="aad62-295">Most web APIs should implement a token-based authentication system.</span></span> <span data-ttu-id="aad62-296">Ověření pomocí tokenu je bezstavové a navrženy tak, aby byla škálovatelná.</span><span class="sxs-lookup"><span data-stu-id="aad62-296">Token authentication is stateless and designed to be scalable.</span></span> <span data-ttu-id="aad62-297">V systému na základě tokenu ověřování musí klient nejprve ověřit pomocí zprostředkovatele ověřování.</span><span class="sxs-lookup"><span data-stu-id="aad62-297">In a token-based authentication system, the client must first authenticate with the authentication provider.</span></span> <span data-ttu-id="aad62-298">V případě úspěšného klienta vydán token, který je jednoduše kryptograficky smysluplný řetězec znaků.</span><span class="sxs-lookup"><span data-stu-id="aad62-298">If successful, the client is issued a token, which is simply a cryptographically meaningful string of characters.</span></span> <span data-ttu-id="aad62-299">Pokud klient potřebuje potom vydat žádost na rozhraní API, přidá tento token jako záhlaví v žádosti.</span><span class="sxs-lookup"><span data-stu-id="aad62-299">When the client then needs to issue a request to an API, it adds this token as a header on the request.</span></span> <span data-ttu-id="aad62-300">Server pak ověří token nalezen v hlavičce požadavku před dokončením požadavku.</span><span class="sxs-lookup"><span data-stu-id="aad62-300">The server then validates the token found in the request header before completing the request.</span></span> <span data-ttu-id="aad62-301">Obrázek 7-4 ukazuje tento proces.</span><span class="sxs-lookup"><span data-stu-id="aad62-301">Figure 7-4 demonstrates this process.</span></span>

![TokenAuth](./media/image7-4.png)

<span data-ttu-id="aad62-303">**Obrázek 7 – 4.**</span><span class="sxs-lookup"><span data-stu-id="aad62-303">**Figure 7-4.**</span></span> <span data-ttu-id="aad62-304">Ověřování na základě tokenu pro rozhraní Web API.</span><span class="sxs-lookup"><span data-stu-id="aad62-304">Token-based authentication for Web APIs.</span></span>

> ### <a name="references--security"></a><span data-ttu-id="aad62-305">Odkazy – zabezpečení</span><span class="sxs-lookup"><span data-stu-id="aad62-305">References – Security</span></span>
> - <span data-ttu-id="aad62-306">**Přehled dokumentace zabezpečení**</span><span class="sxs-lookup"><span data-stu-id="aad62-306">**Security Docs Overview**</span></span>  
> <span data-ttu-id="aad62-307">https://docs.microsoft.com/aspnet/core/security/</span><span class="sxs-lookup"><span data-stu-id="aad62-307">https://docs.microsoft.com/aspnet/core/security/</span></span>
> - <span data-ttu-id="aad62-308">**Vynucování SSL v aplikaci ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="aad62-308">**Enforcing SSL in an ASP.NET Core App**</span></span>  
> <span data-ttu-id="aad62-309"><https://docs.microsoft.com/aspnet/core/security/enforcing-ssl></span><span class="sxs-lookup"><span data-stu-id="aad62-309"><https://docs.microsoft.com/aspnet/core/security/enforcing-ssl></span></span>
> - <span data-ttu-id="aad62-310">**Úvod do systému Identity**</span><span class="sxs-lookup"><span data-stu-id="aad62-310">**Introduction to Identity**</span></span>  
> <span data-ttu-id="aad62-311"><https://docs.microsoft.com/aspnet/core/security/authentication/identity></span><span class="sxs-lookup"><span data-stu-id="aad62-311"><https://docs.microsoft.com/aspnet/core/security/authentication/identity></span></span>
> - <span data-ttu-id="aad62-312">**Úvod do autorizace**</span><span class="sxs-lookup"><span data-stu-id="aad62-312">**Introduction to Authorization**</span></span>  
> <span data-ttu-id="aad62-313"><https://docs.microsoft.com/aspnet/core/security/authorization/introduction></span><span class="sxs-lookup"><span data-stu-id="aad62-313"><https://docs.microsoft.com/aspnet/core/security/authorization/introduction></span></span>
> - <span data-ttu-id="aad62-314">**Ověřování a autorizace API Apps v Azure App Service**</span><span class="sxs-lookup"><span data-stu-id="aad62-314">**Authentication and Authorization for API Apps in Azure App Service**</span></span>  
> <span data-ttu-id="aad62-315"><https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication></span><span class="sxs-lookup"><span data-stu-id="aad62-315"><https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication></span></span>

## <a name="client-communication"></a><span data-ttu-id="aad62-316">Komunikace klienta</span><span class="sxs-lookup"><span data-stu-id="aad62-316">Client Communication</span></span>

<span data-ttu-id="aad62-317">Kromě obsluhující stránky a reagovat na požadavky na data prostřednictvím webových rozhraní API, může aplikace ASP.NET Core komunikovat přímo s připojenými klienty.</span><span class="sxs-lookup"><span data-stu-id="aad62-317">In addition to serving pages and responding to requests for data via web APIs, ASP.NET Core apps can communicate directly with connected clients.</span></span> <span data-ttu-id="aad62-318">Odchozí komunikaci, můžete použít různé přenosu technologií, nejběžnější vrácení objekty WebSockets.</span><span class="sxs-lookup"><span data-stu-id="aad62-318">This outbound communication can use a variety of transport technologies, the most common being WebSockets.</span></span> <span data-ttu-id="aad62-319">Jádro ASP.NET SignalR je do knihovny, která zjednodušuje druh funkce v reálném čase komunikace klienta a serveru pro vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="aad62-319">ASP.NET Core SignalR is a library that makes it simple to kind of real-time server-to-client communication functionality to your applications.</span></span> <span data-ttu-id="aad62-320">SignalR podporuje celou řadu technologií přenosu, včetně Websocket a abstrahuje tokeny n Podrobnosti implementace od vývojáře.</span><span class="sxs-lookup"><span data-stu-id="aad62-320">SignalR supports a variety of transport technologies, including WebSockets, and abstracts away many of the implementation details from the developer.</span></span>

<span data-ttu-id="aad62-321">Jádro ASP.NET SignalR je aktuálně ve vývoji a bude k dispozici v další verzi ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="aad62-321">ASP.NET Core SignalR is currently under development, and will be available in the next release of ASP.NET Core.</span></span> <span data-ttu-id="aad62-322">Ale jiné [otevřete zdroj Websocket knihovny](https://github.com/radu-matei/websocket-manager) jsou nyní k dispozici.</span><span class="sxs-lookup"><span data-stu-id="aad62-322">However, other [open source WebSockets libraries](https://github.com/radu-matei/websocket-manager) are currently available.</span></span>

<span data-ttu-id="aad62-323">Komunikace klienta v reálném čase, zda pomocí technologie WebSockets přímo nebo jinými technikami, jsou užitečné v různých scénářů aplikace.</span><span class="sxs-lookup"><span data-stu-id="aad62-323">Real-time client communication, whether using WebSockets directly or other techniques, are useful in a variety of application scenarios.</span></span> <span data-ttu-id="aad62-324">Mezi příklady patří:</span><span class="sxs-lookup"><span data-stu-id="aad62-324">Some examples include:</span></span>

-   <span data-ttu-id="aad62-325">Za provozu konverzační skupinu aplikací</span><span class="sxs-lookup"><span data-stu-id="aad62-325">Live chat room applications</span></span>

-   <span data-ttu-id="aad62-326">Monitorování aplikací</span><span class="sxs-lookup"><span data-stu-id="aad62-326">Monitoring applications</span></span>

-   <span data-ttu-id="aad62-327">Probíhá aktualizace úlohy</span><span class="sxs-lookup"><span data-stu-id="aad62-327">Job progress updates</span></span>

-   <span data-ttu-id="aad62-328">Oznámení</span><span class="sxs-lookup"><span data-stu-id="aad62-328">Notifications</span></span>

-   <span data-ttu-id="aad62-329">Interaktivní formulářových aplikací</span><span class="sxs-lookup"><span data-stu-id="aad62-329">Interactive forms applications</span></span>

<span data-ttu-id="aad62-330">Při sestavování komunikace klienta do svých aplikací, jsou obvykle dvě součásti:</span><span class="sxs-lookup"><span data-stu-id="aad62-330">When building client communication into your applications, there are typically two components:</span></span>

-   <span data-ttu-id="aad62-331">Správce připojení na straně serveru (rozbočovače SignalR, WebSocketManager WebSocketHandler)</span><span class="sxs-lookup"><span data-stu-id="aad62-331">Server-side connection manager (SignalR Hub, WebSocketManager WebSocketHandler)</span></span>

-   <span data-ttu-id="aad62-332">Knihovna klienta</span><span class="sxs-lookup"><span data-stu-id="aad62-332">Client-side library</span></span>

<span data-ttu-id="aad62-333">Klienti nejsou nijak omezené do prohlížečů – mobilních aplikací, aplikace konzoly a dalších nativní aplikace může také komunikovat pomocí SignalR/Websocket.</span><span class="sxs-lookup"><span data-stu-id="aad62-333">Clients are not limited to browsers – mobile apps, console apps, and other native apps can also communicate using SignalR/WebSockets.</span></span> <span data-ttu-id="aad62-334">Následující jednoduchý program vrátí veškerý obsah odeslat do aplikace chat konzole, jako součást WebSocketManager ukázkovou aplikaci:</span><span class="sxs-lookup"><span data-stu-id="aad62-334">The following simple program echoes all content sent to a chat application to the console, as part of a WebSocketManager sample application:</span></span>

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

<span data-ttu-id="aad62-335">Zvažte zvýšení způsoby, ve kterých vaše aplikace komunikovat přímo s klientským aplikacím a zvažte, zda v reálném čase komunikace by zlepšit uživatele vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="aad62-335">Consider ways in which your applications communicate directly with client applications, and consider whether real-time communication would improve your app's user experience.</span></span>

> ### <a name="references--client-communication"></a><span data-ttu-id="aad62-336">Odkazy – komunikaci klientů</span><span class="sxs-lookup"><span data-stu-id="aad62-336">References – Client Communication</span></span>
> - <span data-ttu-id="aad62-337">**Jádro ASP.NET SignalR**</span><span class="sxs-lookup"><span data-stu-id="aad62-337">**ASP.NET Core SignalR**</span></span>  
> <span data-ttu-id="aad62-338"><https://github.com/aspnet/SignalR></span><span class="sxs-lookup"><span data-stu-id="aad62-338"><https://github.com/aspnet/SignalR></span></span>
> - <span data-ttu-id="aad62-339">**Správce protokolu WebSocket**</span><span class="sxs-lookup"><span data-stu-id="aad62-339">**WebSocket Manager**</span></span>  
> <span data-ttu-id="aad62-340">https://github.com/radu-matei/websocket-manager</span><span class="sxs-lookup"><span data-stu-id="aad62-340">https://github.com/radu-matei/websocket-manager</span></span>

## <a name="domain-driven-design--should-you-apply-it"></a><span data-ttu-id="aad62-341">Návrh – řízené domény by měl použijete ho?</span><span class="sxs-lookup"><span data-stu-id="aad62-341">Domain-Driven Design – Should You Apply It?</span></span>

<span data-ttu-id="aad62-342">Řízené domény návrhu (DDD) je agilní přístup k vytváření software, který klade důraz zaměřené na *obchodní domény*.</span><span class="sxs-lookup"><span data-stu-id="aad62-342">Domain-Driven Design (DDD) is an agile approach to building software that emphasizes focusing on the *business domain*.</span></span> <span data-ttu-id="aad62-343">Umístí velkou důraz na komunikaci a interakci s expert(s) obchodní domény, který může být v relaci pro vývojáře fungování reálného systému.</span><span class="sxs-lookup"><span data-stu-id="aad62-343">It places a heavy emphasis on communication and interaction with business domain expert(s) who can relate to the developers how the real-world system works.</span></span> <span data-ttu-id="aad62-344">Například pokud vytváříte systém, který zpracovává burzovní obchody, expert vaší domény může být zkušeného uložených zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="aad62-344">For example, if you're building a system that handles stock trades, your domain expert might be an experienced stock broker.</span></span> <span data-ttu-id="aad62-345">DDD slouží k řešení problémů složitých obchodní a není často vhodná pro menší, jednodušší aplikací, protože investice vysvětlující Princip fungování a modelování domény není vhodné ho.</span><span class="sxs-lookup"><span data-stu-id="aad62-345">DDD is designed to address large, complex business problems, and is often not appropriate for smaller, simpler applications, as the investment in understanding and modeling the domain is not worth it.</span></span>

<span data-ttu-id="aad62-346">Při sestavování softwaru následující DDD přístup, musí váš tým (včetně netechnické zúčastněným stranám a přispěvatelé) vyvíjet *všudypřítomný jazyk* místo problém.</span><span class="sxs-lookup"><span data-stu-id="aad62-346">When building software following a DDD approach, your team (including non-technical stakeholders and contributors) should develop a *ubiquitous language* for the problem space.</span></span> <span data-ttu-id="aad62-347">To znamená stejné terminologie slouží koncept reálného modelovaných, ekvivalent softwaru a všechny struktury, které mohou existovat udržení koncept (například tabulek databáze).</span><span class="sxs-lookup"><span data-stu-id="aad62-347">That is, the same terminology should be used for the real-world concept being modeled, the software equivalent, and any structures that might exist to persist the concept (for example, database tables).</span></span> <span data-ttu-id="aad62-348">Proto by měl konceptů popsaných v jazyce všudypřítomný tvoří základ pro vaše *modelu domény*.</span><span class="sxs-lookup"><span data-stu-id="aad62-348">Thus, the concepts described in the ubiquitous language should form the basis for your *domain model*.</span></span>

<span data-ttu-id="aad62-349">Váš model domény se skládá z objektů, které vzájemně představují chování systému.</span><span class="sxs-lookup"><span data-stu-id="aad62-349">Your domain model is comprised of objects that interact with one another to represent the behavior of the system.</span></span> <span data-ttu-id="aad62-350">Tyto objekty může spadají do následujících kategorií:</span><span class="sxs-lookup"><span data-stu-id="aad62-350">These objects may fall into the following categories:</span></span>

-   <span data-ttu-id="aad62-351">[Entity](http://deviq.com/entity/), které představují objekty s vláknem identity.</span><span class="sxs-lookup"><span data-stu-id="aad62-351">[Entities](http://deviq.com/entity/), which represent objects with a thread of identity.</span></span> <span data-ttu-id="aad62-352">Entity jsou obvykle uložena v trvalost s klíčem, podle kterého se dá později načíst.</span><span class="sxs-lookup"><span data-stu-id="aad62-352">Entities are typically stored in persistence with a key by which they can later be retrieved.</span></span>

-   <span data-ttu-id="aad62-353">[Agregace](http://deviq.com/aggregate-pattern/), který představuje skupiny objektů, které by měl být trvalé jako jednotku.</span><span class="sxs-lookup"><span data-stu-id="aad62-353">[Aggregates](http://deviq.com/aggregate-pattern/), which represent groups of objects that should be persisted as a unit.</span></span>

-   <span data-ttu-id="aad62-354">[Hodnota objekty](http://deviq.com/value-object/), které představují koncepty, které lze porovnat s hodnotou na základě součtu hodnot jejich vlastností.</span><span class="sxs-lookup"><span data-stu-id="aad62-354">[Value objects](http://deviq.com/value-object/), which represent concepts that can be compared on the basis of the sum of their property values.</span></span> <span data-ttu-id="aad62-355">Například DateRange skládající se z počáteční a koncové datum.</span><span class="sxs-lookup"><span data-stu-id="aad62-355">For example, DateRange consisting of a start and end date.</span></span>

-   <span data-ttu-id="aad62-356">[Události domény](https://martinfowler.com/eaaDev/DomainEvent.html), které představují věcí děje v rámci systému, které jsou důležité pro ostatní části systému.</span><span class="sxs-lookup"><span data-stu-id="aad62-356">[Domain events](https://martinfowler.com/eaaDev/DomainEvent.html), which represent things happening within the system that are of interest to other parts of the system.</span></span>

<span data-ttu-id="aad62-357">Všimněte si, že by měl modelu domény DDD zapouzdření komplexní chování v rámci modelu.</span><span class="sxs-lookup"><span data-stu-id="aad62-357">Note that a DDD domain model should encapsulate complex behavior within the model.</span></span> <span data-ttu-id="aad62-358">Entity, by neměl být zejména jenom kolekcí vlastností.</span><span class="sxs-lookup"><span data-stu-id="aad62-358">Entities, in particular, should not merely be collections of properties.</span></span> <span data-ttu-id="aad62-359">Pokud model domény chybí chování a představuje pouze stav systému, je označováno jako [anemic modelu](http://deviq.com/anemic-model/), což je žádoucí v DDD.</span><span class="sxs-lookup"><span data-stu-id="aad62-359">When the domain model lacks behavior and merely represents the state of the system, it is said to be an [anemic model](http://deviq.com/anemic-model/), which is undesirable in DDD.</span></span>

<span data-ttu-id="aad62-360">Kromě těchto typů modelu DDD obvykle využívá různé vzorce:</span><span class="sxs-lookup"><span data-stu-id="aad62-360">In addition to these model types, DDD typically employs a variety of patterns:</span></span>

-   <span data-ttu-id="aad62-361">[Úložiště](http://deviq.com/repository-pattern/), pro poskytuje abstrakci podrobnosti trvalost.</span><span class="sxs-lookup"><span data-stu-id="aad62-361">[Repository](http://deviq.com/repository-pattern/), for abstracting persistence details.</span></span>

-   <span data-ttu-id="aad62-362">[Objekt pro vytváření](https://en.wikipedia.org/wiki/Factory_method_pattern), pro zapouzdření vytváření komplexních objektů.</span><span class="sxs-lookup"><span data-stu-id="aad62-362">[Factory](https://en.wikipedia.org/wiki/Factory_method_pattern), for encapsulating complex object creation.</span></span>

-   <span data-ttu-id="aad62-363">Události domény pro oddělení závislé chování z aktivován chování.</span><span class="sxs-lookup"><span data-stu-id="aad62-363">Domain events, for decoupling dependent behavior from triggering behavior.</span></span>

-   <span data-ttu-id="aad62-364">[Služby](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/)pro zapouzdřením komplexní chování a podrobnosti implementace infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="aad62-364">[Services](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/), for encapsulating complex behavior and/or infrastructure implementation details.</span></span>

-   <span data-ttu-id="aad62-365">[Příkaz](https://en.wikipedia.org/wiki/Command_pattern), pro oddělení vydávání příkazů a provádění příkazu sám sebe.</span><span class="sxs-lookup"><span data-stu-id="aad62-365">[Command](https://en.wikipedia.org/wiki/Command_pattern), for decoupling issuing commands and executing the command itself.</span></span>

-   <span data-ttu-id="aad62-366">[Specifikace](http://deviq.com/specification-pattern/), pro zapouzdření podrobnosti dotazu.</span><span class="sxs-lookup"><span data-stu-id="aad62-366">[Specification](http://deviq.com/specification-pattern/), for encapsulating query details.</span></span>

<span data-ttu-id="aad62-367">DDD také doporučuje použití architektuře čistého, jak jsme vysvětlili výše, aby vám umožnil volné párování, zapouzdření a kód, který lze snadno ověřit pomocí testování částí.</span><span class="sxs-lookup"><span data-stu-id="aad62-367">DDD also recommends the use of the Clean Architecture discussed previously, allowing for loose coupling, encapsulation, and code that can easily be verified using unit tests.</span></span>

### <a name="when-should-you-apply-ddd"></a><span data-ttu-id="aad62-368">Pokud by se měly používat DDD</span><span class="sxs-lookup"><span data-stu-id="aad62-368">When Should You Apply DDD</span></span>

<span data-ttu-id="aad62-369">DDD je vhodné řešení pro velké aplikace s složitost významné firmy (ne technického právě).</span><span class="sxs-lookup"><span data-stu-id="aad62-369">DDD is well-suited to large applications with significant business (not just technical) complexity.</span></span> <span data-ttu-id="aad62-370">Aplikace by měla vyžadují znalosti systému domény odborníky.</span><span class="sxs-lookup"><span data-stu-id="aad62-370">The application should require the knowledge of domain experts.</span></span> <span data-ttu-id="aad62-371">Domény přímo pro model, představující obchodní pravidla a interakce nad rámec jednoduše ukládání a načítání aktuální stav různých záznamů z úložiště dat by měly mít významné chování.</span><span class="sxs-lookup"><span data-stu-id="aad62-371">There should be significant behavior in the domain model itself, representing business rules and interactions beyond simply storing and retrieving the current state of various records from data stores.</span></span>

### <a name="when-shouldnt-you-apply-ddd"></a><span data-ttu-id="aad62-372">Pokud by se neměla vztahovat DDD</span><span class="sxs-lookup"><span data-stu-id="aad62-372">When Shouldn't You Apply DDD</span></span>

<span data-ttu-id="aad62-373">DDD zahrnuje investice do modelování, architekturu a komunikaci, která nemusí být jader pro menší aplikací nebo aplikace, které jsou v podstatě právě CRUD (vytváření, čtení, aktualizaci nebo odstranění).</span><span class="sxs-lookup"><span data-stu-id="aad62-373">DDD involves investments in modeling, architecture, and communication that may not be warranted for smaller applications or applications that are essentially just CRUD (create/read/update/delete).</span></span> <span data-ttu-id="aad62-374">Pokud zvolíte možnost přístupu aplikace následující DDD, ale najít, že má vaše doména model anemic s žádné chování, musíte přehodnotit váš přístup.</span><span class="sxs-lookup"><span data-stu-id="aad62-374">If you choose to approach your application following DDD, but find that your domain has an anemic model with no behavior, you may need to rethink your approach.</span></span> <span data-ttu-id="aad62-375">Buď vaše aplikace nemusí potřebovat DDD, nebo potřebujete pomoc refaktoring aplikace má být zapouzdřena obchodní logiku v modelu domény, nikoli vaše databáze nebo uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="aad62-375">Either your application may not need DDD, or you may need assistance refactoring your application to encapsulate business logic in the domain model, rather than in your database or user interface.</span></span>

<span data-ttu-id="aad62-376">Hybridní přístup by mohla být DDD použít pouze pro transakční či složitější oblasti aplikace, ale ne pro jednodušší CRUD nebo jen pro čtení částí aplikace.</span><span class="sxs-lookup"><span data-stu-id="aad62-376">A hybrid approach would be to only use DDD for the transactional or more complex areas of the application, but not for simpler CRUD or read-only portions of the application.</span></span> <span data-ttu-id="aad62-377">Pokud se dotazuje data k zobrazení sestavy nebo k vizualizaci dat pro řídicí panel, například nemusí mít omezení agregace.</span><span class="sxs-lookup"><span data-stu-id="aad62-377">For instance, you needn't have the constraints of an Aggregate if you're querying data to display a report or to visualize data for a dashboard.</span></span> <span data-ttu-id="aad62-378">Je zcela přijatelné mít samostatné, jednodušší čtení model pro tyto požadavky.</span><span class="sxs-lookup"><span data-stu-id="aad62-378">It's perfectly acceptable to have a separate, simpler read model for such requirements.</span></span>

> ### <a name="references--domain-driven-design"></a><span data-ttu-id="aad62-379">Odkazy – funguje na základě domény</span><span class="sxs-lookup"><span data-stu-id="aad62-379">References – Domain-Driven Design</span></span>
> - <span data-ttu-id="aad62-380">**DDD zjednodušeně (StackOverflow odpovědí)**</span><span class="sxs-lookup"><span data-stu-id="aad62-380">**DDD in Plain English (StackOverflow Answer)**</span></span>  
> <span data-ttu-id="aad62-381"><https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488></span><span class="sxs-lookup"><span data-stu-id="aad62-381"><https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488></span></span>

## <a name="deployment"></a><span data-ttu-id="aad62-382">Nasazení</span><span class="sxs-lookup"><span data-stu-id="aad62-382">Deployment</span></span>

<span data-ttu-id="aad62-383">Související se situací procesu nasazení vaší aplikace ASP.NET Core, bez ohledu na to, který bude hostitelem je několik kroků.</span><span class="sxs-lookup"><span data-stu-id="aad62-383">There are a few steps involved in the process of deploying your ASP.NET Core application, regardless of where it will be hosted.</span></span> <span data-ttu-id="aad62-384">Prvním krokem je můžete publikovat aplikaci, což lze provést pomocí dotnet publikování rozhraní příkazového řádku příkaz.</span><span class="sxs-lookup"><span data-stu-id="aad62-384">The first step is to publish the application, which can be done using the dotnet publish CLI command.</span></span> <span data-ttu-id="aad62-385">Tato akce kompilace aplikace a umístit všechny soubory potřebné ke spuštění aplikace do určené složky.</span><span class="sxs-lookup"><span data-stu-id="aad62-385">This will compile the application and place all of the files needed to run the application into a designated folder.</span></span> <span data-ttu-id="aad62-386">Při nasazení ze sady Visual Studio, je pro vás tento krok provést automaticky.</span><span class="sxs-lookup"><span data-stu-id="aad62-386">When you deploy from Visual Studio, this step is performed for you automatically.</span></span> <span data-ttu-id="aad62-387">Publikování složka obsahuje soubory .exe a .dll pro aplikace a její závislosti.</span><span class="sxs-lookup"><span data-stu-id="aad62-387">The publish folder contains .exe and .dll files for the application and its dependencies.</span></span> <span data-ttu-id="aad62-388">Samostatný aplikace bude také obsahovat verzi modulu runtime rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="aad62-388">A self-contained application will also include a version of the .NET runtime.</span></span> <span data-ttu-id="aad62-389">Aplikace ASP.NET Core bude také obsahovat konfigurační soubory, prostředky statického klienta a zobrazení MVC.</span><span class="sxs-lookup"><span data-stu-id="aad62-389">ASP.NET Core applications will also include configuration files, static client assets, and MVC views.</span></span>

<span data-ttu-id="aad62-390">Aplikace ASP.NET Core jsou konzolové aplikace, které musí být spuštěna, když na server se spustí a restartovat, pokud dojde k chybě aplikace (nebo serveru).</span><span class="sxs-lookup"><span data-stu-id="aad62-390">ASP.NET Core applications are console applications that must be started when the server boots and restarted if the application (or server) crashes.</span></span> <span data-ttu-id="aad62-391">Proces manager můžete použít k automatizaci tohoto procesu.</span><span class="sxs-lookup"><span data-stu-id="aad62-391">A process manager can be used to automate this process.</span></span> <span data-ttu-id="aad62-392">Nejběžnější správci proces pro ASP.NET Core jsou Nginx a Apache na Linuxu a služby IIS nebo služba systému Windows v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="aad62-392">The most common process managers for ASP.NET Core are Nginx and Apache on Linux and IIS or Windows Service on Windows.</span></span>

<span data-ttu-id="aad62-393">Kromě Správce úloh musí aplikace ASP.NET Core hostované na webovém serveru Kestrel použít reverzní proxy server.</span><span class="sxs-lookup"><span data-stu-id="aad62-393">In addition to a process manager, ASP.NET Core applications hosted in the Kestrel web server must use a reverse proxy server.</span></span> <span data-ttu-id="aad62-394">Reverzní proxy server přijímá požadavky HTTP z Internetu a předává je Kestrel po některé předběžné zpracování.</span><span class="sxs-lookup"><span data-stu-id="aad62-394">A reverse proxy server receives HTTP requests from the internet and forwards them to Kestrel after some preliminary handling.</span></span> <span data-ttu-id="aad62-395">Reverzní proxy servery poskytují úroveň zabezpečení pro aplikace a jsou vyžadována pro nasazení okraj (vystavený pro přenosy z Internetu).</span><span class="sxs-lookup"><span data-stu-id="aad62-395">Reverse proxy servers provide a layer of security for the application, and are required for edge deployments (exposed to traffic from the Internet).</span></span> <span data-ttu-id="aad62-396">Kestrel je relativně nové a dosud neposkytuje obranu proti napadením.</span><span class="sxs-lookup"><span data-stu-id="aad62-396">Kestrel is relatively new and does not yet offer defenses against certain attacks.</span></span> <span data-ttu-id="aad62-397">Kestrel nepodporuje hostování více aplikací na stejném portu, takže techniky jako hlavičky hostitele nelze použít s ním povolit hostování více aplikací na stejný port a IP adresu.</span><span class="sxs-lookup"><span data-stu-id="aad62-397">Kestrel also doesn't support hosting multiple applications on the same port, so techniques like host headers cannot be used with it to enable hosting multiple applications on the same port and IP address.</span></span>

![Kestrel k Internetu](./media/image7-5.png)

<span data-ttu-id="aad62-399">Obrázek 7-5 ASP.NET, které jsou hostovány v Kestrel za reverzní proxy server</span><span class="sxs-lookup"><span data-stu-id="aad62-399">Figure 7-5 ASP.NET hosted in Kestrel behind a reverse proxy server</span></span>

<span data-ttu-id="aad62-400">Další scénáře, ve kterém může být užitečné reverzní proxy server je zabezpečit více aplikací pomocí SSL nebo HTTPS.</span><span class="sxs-lookup"><span data-stu-id="aad62-400">Another scenario in which a reverse proxy can be helpful is to secure multiple applications using SSL/HTTPS.</span></span> <span data-ttu-id="aad62-401">Pouze reverzní proxy server v takovém případě bude muset mít nakonfigurovaný protokol SSL.</span><span class="sxs-lookup"><span data-stu-id="aad62-401">In this case, only the reverse proxy would need to have SSL configured.</span></span> <span data-ttu-id="aad62-402">Komunikace mezi reverzní proxy server a Kestrel mohla provést prostřednictvím protokolu HTTP, jak je znázorněno na obrázku 7 až 6.</span><span class="sxs-lookup"><span data-stu-id="aad62-402">Communication between the reverse proxy server and Kestrel could take place over HTTP, as shown in Figure 7-6.</span></span>

![](./media/image7-6.png)

<span data-ttu-id="aad62-403">Obrázek 7-6 ASP.NET hostované za serveru HTTPS zabezpečené reverzní proxy server</span><span class="sxs-lookup"><span data-stu-id="aad62-403">Figure 7-6 ASP.NET hosted behind an HTTPS-secured reverse proxy server</span></span>

<span data-ttu-id="aad62-404">Kvůli hostování vaší aplikace ASP.NET Core v kontejner Docker, který pak lze hostována místně nebo nasadit do Azure pro hostování cloudových je stále oblíbených přístup.</span><span class="sxs-lookup"><span data-stu-id="aad62-404">An increasingly popular approach is to host your ASP.NET Core application in a Docker container, which then can be hosted locally or deployed to Azure for cloud-based hosting.</span></span> <span data-ttu-id="aad62-405">Kontejner Docker může obsahovat kód aplikace, systémem Kestrel a se nasazuje za reverzní proxy server, jak je uvedeno výše.</span><span class="sxs-lookup"><span data-stu-id="aad62-405">The Docker container could contain your application code, running on Kestrel, and would be deployed behind a reverse proxy server, as shown above.</span></span>

<span data-ttu-id="aad62-406">Pokud máte aplikace na platformě Azure, slouží k poskytování několika služeb Microsoft Azure Application Gateway jako vyhrazené virtuální zařízení.</span><span class="sxs-lookup"><span data-stu-id="aad62-406">If you're hosting your application on Azure, you can use Microsoft Azure Application Gateway as a dedicated virtual appliance to provide several services.</span></span> <span data-ttu-id="aad62-407">Kromě funguje jako reverzní proxy server pro jednotlivé aplikace, aplikační brány také nabízí následující funkce:</span><span class="sxs-lookup"><span data-stu-id="aad62-407">In addition to acting as a reverse proxy for individual applications, Application Gateway can also offer the following features:</span></span>

-   <span data-ttu-id="aad62-408">Vyrovnávání zatížení HTTP</span><span class="sxs-lookup"><span data-stu-id="aad62-408">HTTP load balancing</span></span>

-   <span data-ttu-id="aad62-409">Přesměrování zpracování SSL (SSL pouze k Internetu)</span><span class="sxs-lookup"><span data-stu-id="aad62-409">SSL offload (SSL only to Internet)</span></span>

-   <span data-ttu-id="aad62-410">Koncová SSL</span><span class="sxs-lookup"><span data-stu-id="aad62-410">End to End SSL</span></span>

-   <span data-ttu-id="aad62-411">Více lokalit směrování (konsolidovat až 20 webů na jednom Aplikační brána)</span><span class="sxs-lookup"><span data-stu-id="aad62-411">Multi-site routing (consolidate up to 20 sites on a single Application Gateway)</span></span>

-   <span data-ttu-id="aad62-412">Brány firewall webových aplikací</span><span class="sxs-lookup"><span data-stu-id="aad62-412">Web application firewall</span></span>

-   <span data-ttu-id="aad62-413">Podpora protokolu Websocket</span><span class="sxs-lookup"><span data-stu-id="aad62-413">Websocket support</span></span>

-   <span data-ttu-id="aad62-414">Pokročilé diagnostiky</span><span class="sxs-lookup"><span data-stu-id="aad62-414">Advanced diagnostics</span></span>

<span data-ttu-id="aad62-415">*Další informace o možnostech nasazení Azure v kapitole 10.*</span><span class="sxs-lookup"><span data-stu-id="aad62-415">*Learn more about Azure deployment options in Chapter 10.*</span></span>

> ### <a name="references--deployment"></a><span data-ttu-id="aad62-416">Odkazy – nasazení</span><span class="sxs-lookup"><span data-stu-id="aad62-416">References – Deployment</span></span>
> - <span data-ttu-id="aad62-417">**Přehled nasazení a hostování**</span><span class="sxs-lookup"><span data-stu-id="aad62-417">**Hosting and Deployment Overview**</span></span>  
> <span data-ttu-id="aad62-418"><https://docs.microsoft.com/aspnet/core/publishing/></span><span class="sxs-lookup"><span data-stu-id="aad62-418"><https://docs.microsoft.com/aspnet/core/publishing/></span></span>
> - <span data-ttu-id="aad62-419">**Kdy použít Kestrel s reverzní proxy server**</span><span class="sxs-lookup"><span data-stu-id="aad62-419">**When to use Kestrel with a reverse proxy**</span></span>  
> <span data-ttu-id="aad62-420"><https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy></span><span class="sxs-lookup"><span data-stu-id="aad62-420"><https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy></span></span>
> - <span data-ttu-id="aad62-421">**Aplikace ASP.NET Core hostitele v Docker**</span><span class="sxs-lookup"><span data-stu-id="aad62-421">**Host ASP.NET Core apps in Docker**</span></span>  
> <span data-ttu-id="aad62-422"><https://docs.microsoft.com/aspnet/core/publishing/docker></span><span class="sxs-lookup"><span data-stu-id="aad62-422"><https://docs.microsoft.com/aspnet/core/publishing/docker></span></span>
> - <span data-ttu-id="aad62-423">**Představení Azure Application Gateway**</span><span class="sxs-lookup"><span data-stu-id="aad62-423">**Introducing Azure Application Gateway**</span></span>  
> <span data-ttu-id="aad62-424"><https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction></span><span class="sxs-lookup"><span data-stu-id="aad62-424"><https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction></span></span>

>[!div class="step-by-step"]
<span data-ttu-id="aad62-425">[Předchozí] (common-client-side-web-technologies.md) [Další] (work-with-data-in-asp-net-core-apps.md)</span><span class="sxs-lookup"><span data-stu-id="aad62-425">[Previous] (common-client-side-web-technologies.md) [Next] (work-with-data-in-asp-net-core-apps.md)</span></span>
