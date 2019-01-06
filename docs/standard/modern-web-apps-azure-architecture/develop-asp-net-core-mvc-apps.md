---
title: Vývoj aplikace ASP.NET Core MVC aplikace
description: Navrhování moderních webových aplikací pomocí ASP.NET Core a Azure | vývoj aplikací ASP.NET Core MVC
author: ardalis
ms.author: wiwagn
ms.date: 06/28/2018
ms.openlocfilehash: aed0ba4621eab91dd47df9ef760fdf8c39ff1103
ms.sourcegitcommit: deb9225a55485a5a6e6c7914deb30ccfceb69d3f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2019
ms.locfileid: "54058500"
---
# <a name="develop-aspnet-core-mvc-apps"></a><span data-ttu-id="403e4-103">Vývoj aplikace ASP.NET Core MVC aplikace</span><span class="sxs-lookup"><span data-stu-id="403e4-103">Develop ASP.NET Core MVC apps</span></span>

> <span data-ttu-id="403e4-104">"Není důležité, chcete-li získat správný, poprvé.</span><span class="sxs-lookup"><span data-stu-id="403e4-104">"It's not important to get it right the first time.</span></span> <span data-ttu-id="403e4-105">Je životně důležitá, chcete-li získat správný, čas posledního."</span><span class="sxs-lookup"><span data-stu-id="403e4-105">It's vitally important to get it right the last time."</span></span>  
> <span data-ttu-id="403e4-106">_– Andrew Hunt a David Thomas_</span><span class="sxs-lookup"><span data-stu-id="403e4-106">_- Andrew Hunt and David Thomas_</span></span>

<span data-ttu-id="403e4-107">ASP.NET Core je různé platformy, open source architektura pro vytváření moderních optimalizovaných cloudů webových aplikací.</span><span class="sxs-lookup"><span data-stu-id="403e4-107">ASP.NET Core is a cross-platform, open-source framework for building modern cloud-optimized web applications.</span></span> <span data-ttu-id="403e4-108">Aplikace ASP.NET Core je Odlehčená a modulární a s integrovanou podporou pro vkládání závislostí, umožní větší testovatelnost a udržovatelnost.</span><span class="sxs-lookup"><span data-stu-id="403e4-108">ASP.NET Core apps are lightweight and modular, with built-in support for dependency injection, enabling greater testability and maintainability.</span></span> <span data-ttu-id="403e4-109">V kombinaci s MVC, která podporuje vytváření moderních webových rozhraní API kromě aplikace založené na zobrazení, ASP.NET Core je výkonnou architekturu, pomocí kterého se má tvorbu podnikových webových aplikací.</span><span class="sxs-lookup"><span data-stu-id="403e4-109">Combined with MVC, which supports building modern web APIs in addition to view-based apps, ASP.NET Core is a powerful framework with which to build enterprise web applications.</span></span>

## <a name="mapping-requests-to-responses"></a><span data-ttu-id="403e4-110">Mapování požadavků na reakce</span><span class="sxs-lookup"><span data-stu-id="403e4-110">Mapping requests to responses</span></span>

<span data-ttu-id="403e4-111">Aplikace ASP.NET Core svou podstatou mapování příchozích požadavků na odchozí odpovědi.</span><span class="sxs-lookup"><span data-stu-id="403e4-111">At its heart, ASP.NET Core apps map incoming requests to outgoing responses.</span></span> <span data-ttu-id="403e4-112">Na nízké úrovni používá se k tomu middleware a jednoduché aplikace ASP.NET Core a mikroslužeb může být složená výhradně z vlastního middlewaru.</span><span class="sxs-lookup"><span data-stu-id="403e4-112">At a low level, this is done with middleware, and simple ASP.NET Core apps and microservices may be comprised solely of custom middleware.</span></span> <span data-ttu-id="403e4-113">Při použití technologie ASP.NET Core MVC, můžete pracovat se o něco vyšší úrovně, uvažujete z hlediska _trasy_, _řadiče_, a _akce_.</span><span class="sxs-lookup"><span data-stu-id="403e4-113">When using ASP.NET Core MVC, you can work at a somewhat higher level, thinking in terms of _routes_, _controllers_, and _actions_.</span></span> <span data-ttu-id="403e4-114">Jednotlivých příchozích požadavků je ve srovnání s směrovací tabulky aplikace, a pokud je nalezen odpovídající trasy, přidružená metoda akce (patří do kontroleru) se nazývá žádost zpracovat.</span><span class="sxs-lookup"><span data-stu-id="403e4-114">Each incoming request is compared with the application's routing table, and if a matching route is found, the associated action method (belonging to a controller) is called to handle the request.</span></span> <span data-ttu-id="403e4-115">Pokud není nalezen žádný odpovídající trasy, je volána obslužná rutina chyby (v tomto případě vrácením výsledku NotFound).</span><span class="sxs-lookup"><span data-stu-id="403e4-115">If no matching route is found, an error handler (in this case, returning a NotFound result) is called.</span></span>

<span data-ttu-id="403e4-116">ASP.NET Core MVC aplikace můžou používat konvenční trasy a trasy atributů.</span><span class="sxs-lookup"><span data-stu-id="403e4-116">ASP.NET Core MVC apps can use conventional routes, attribute routes, or both.</span></span> <span data-ttu-id="403e4-117">Konvenční trasy, které jsou definovány v kódu, určení směrování _konvence_ pomocí syntaxe jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="403e4-117">Conventional routes are defined in code, specifying routing _conventions_ using syntax like in the example below:</span></span>

```csharp
app.UseMvc(routes =>;
{
    routes.MapRoute("default","{controller=Home}/{action=Index}/{id?}");
});
```

<span data-ttu-id="403e4-118">V tomto příkladu se přidala do směrovací tabulky trasa s názvem "Výchozí".</span><span class="sxs-lookup"><span data-stu-id="403e4-118">In this example, a route named "default" has been added to the routing table.</span></span> <span data-ttu-id="403e4-119">Definuje šablonu trasy se zástupnými symboly pro _řadič_, _akce_, a _id_. Zástupné symboly kontroleru a akce mají výchozí zadaná ("Home" a "Index", v uvedeném pořadí), a zástupný symbol id je volitelný (základě "?" použit).</span><span class="sxs-lookup"><span data-stu-id="403e4-119">It defines a route template with placeholders for _controller_, _action_, and _id_. The controller and action placeholders have default specified ("Home" and "Index", respectively), and the id placeholder is optional (by virtue of a "?" applied to it).</span></span> <span data-ttu-id="403e4-120">Tato konvence jsou zde definovány stavy, které by měl odpovídat první část žádost o název kontroleru, druhá část na akci, a pak v případě potřeby třetí části bude reprezentovat pomocí parametru id.</span><span class="sxs-lookup"><span data-stu-id="403e4-120">The convention defined here states that the first part of a request should correspond to the name of the controller, the second part to the action, and then if necessary a third part will represent an id parameter.</span></span> <span data-ttu-id="403e4-121">Konvenční trasy jsou obvykle definovány na jednom místě aplikace, jako v metodě konfigurace v třída při spuštění.</span><span class="sxs-lookup"><span data-stu-id="403e4-121">Conventional routes are typically defined in one place for the application, such as in the Configure method in the Startup class.</span></span>

<span data-ttu-id="403e4-122">Trasy atributů jsou přímo použít pro kontrolery a akce, spíše než zadané globálně.</span><span class="sxs-lookup"><span data-stu-id="403e4-122">Attribute routes are applied to controllers and actions directly, rather than specified globally.</span></span> <span data-ttu-id="403e4-123">Tato akce nemá výhodou, že je mnohem snadnější když se podíváte na konkrétní metody, ale znamená, že informace o směrování se uchovávat na jednom místě v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="403e4-123">This has the advantage of making them much more discoverable when you're looking at a particular method, but does mean that routing information is not kept in one place in the application.</span></span> <span data-ttu-id="403e4-124">Atribut trasy je můžete snadno zadat několik tras pro danou akci, jakož i kombinovat trasy mezi kontrolery a akce.</span><span class="sxs-lookup"><span data-stu-id="403e4-124">With attribute routes, you can easily specify multiple routes for a given action, as well as combine routes between controllers and actions.</span></span> <span data-ttu-id="403e4-125">Příklad:</span><span class="sxs-lookup"><span data-stu-id="403e4-125">For example:</span></span>

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

<span data-ttu-id="403e4-126">Trasy se dá nastavit na [HttpGet] a podobně jako atributy, takže není nutné přidat samostatné atributy [trasy].</span><span class="sxs-lookup"><span data-stu-id="403e4-126">Routes can be specified on [HttpGet] and similar attributes, avoiding the need to add separate [Route] attributes.</span></span> <span data-ttu-id="403e4-127">Atribut trasy můžete také použít tokeny omezit opakovat názvy kontroler nebo akce, jak je znázorněno níže:</span><span class="sxs-lookup"><span data-stu-id="403e4-127">Attribute routes can also use tokens to reduce the need to repeat controller or action names, as shown below:</span></span>

```csharp
[Route("[controller\]")]
public class ProductsController : Controller
{
    [Route("")] // Matches 'Products'
    [Route("Index")] // Matches 'Products/Index'
    public IActionResult Index() {}
}
```

<span data-ttu-id="403e4-128">Jakmile danou žádost pravá složená závorka k trase, ale před akci, metoda je volána, ASP.NET Core MVC provede [vazby modelu](/aspnet/core/mvc/models/model-binding) a [ověření modelu](/aspnet/core/mvc/models/validation) v požadavku.</span><span class="sxs-lookup"><span data-stu-id="403e4-128">Once a given request has been matched to a route, but before the action method is called, ASP.NET Core MVC will perform [model binding](/aspnet/core/mvc/models/model-binding) and [model validation](/aspnet/core/mvc/models/validation) on the request.</span></span> <span data-ttu-id="403e4-129">Vazby modelu je zodpovědný za převod příchozích dat protokolu HTTP na typy .NET zadány jako parametry metody akce má být volána.</span><span class="sxs-lookup"><span data-stu-id="403e4-129">Model binding is responsible for converting incoming HTTP data into the .NET types specified as parameters of the action method to be called.</span></span> <span data-ttu-id="403e4-130">Například pokud metoda akce očekává parametr id int, vazby modelu se pokusí zadejte tento parametr z hodnoty zadané jako součást požadavku.</span><span class="sxs-lookup"><span data-stu-id="403e4-130">For example, if the action method expects an int id parameter, model binding will attempt to provide this parameter from a value provided as part of the request.</span></span> <span data-ttu-id="403e4-131">Uděláte to tak, vazby modelu hledá hodnoty v odeslaného formuláře, hodnoty v trase, samotného a hodnoty řetězce dotazu.</span><span class="sxs-lookup"><span data-stu-id="403e4-131">To do so, model binding looks for values in a posted form, values in the route itself, and query string values.</span></span> <span data-ttu-id="403e4-132">Za předpokladu, že je hodnota id nenajde, převede se na celé před předáním do metody akce.</span><span class="sxs-lookup"><span data-stu-id="403e4-132">Assuming an id value is found, it will be converted to an integer before being passed into the action method.</span></span>

<span data-ttu-id="403e4-133">Po vytvoření vazby modelu, ale před voláním metody akce dojde k ověření modelu.</span><span class="sxs-lookup"><span data-stu-id="403e4-133">After binding the model but before calling the action method, model validation occurs.</span></span> <span data-ttu-id="403e4-134">Ověření modelu používá volitelné atributy typu modelu a pomáhají zajistit, že objekt zadaného modelu vyhovuje určitým požadavkům data.</span><span class="sxs-lookup"><span data-stu-id="403e4-134">Model validation uses optional attributes on the model type, and can help ensure that the provided model object conforms to certain data requirements.</span></span> <span data-ttu-id="403e4-135">Některé hodnoty lze zadat jako povinné, nebo jsou omezena na konkrétní délku nebo číselného rozsahu, atd. Pokud jsou zadané atributy ověřování, ale model není v souladu s jejich požadavky, vlastnost ModelState.IsValid bude mít hodnotu false a sadu ověřovacích pravidel selhání bude možné odeslat klientovi provádějícímu žádost.</span><span class="sxs-lookup"><span data-stu-id="403e4-135">Certain values may be specified as required, or limited to a certain length or numeric range, etc. If validation attributes are specified but the model does not conform to their requirements, the property ModelState.IsValid will be false, and the set of failing validation rules will be available to send to the client making the request.</span></span>

<span data-ttu-id="403e4-136">Pokud používáte ověření modelu, byste měli vždy zkontrolujte, zda je model platný před provedením jakékoli změny stavu příkazů, ujistěte se, že vaše aplikace není poškozený neplatnými daty.</span><span class="sxs-lookup"><span data-stu-id="403e4-136">If you're using model validation, you should be sure to always check that the model is valid before performing any state-altering commands, to ensure your app is not corrupted by invalid data.</span></span> <span data-ttu-id="403e4-137">Můžete použít [filtr](/aspnet/core/mvc/controllers/filters) aby se zabránilo nutnosti přidat kód pro tuto v každé akce.</span><span class="sxs-lookup"><span data-stu-id="403e4-137">You can use a [filter](/aspnet/core/mvc/controllers/filters) to avoid the need to add code for this in every action.</span></span> <span data-ttu-id="403e4-138">Filtry ASP.NET Core MVC nabízí způsob, jak zachycování skupiny požadavků, tak, aby se běžných zásad a převeďte společné aspekty lze použít na základě cílové.</span><span class="sxs-lookup"><span data-stu-id="403e4-138">ASP.NET Core MVC filters offer a way of intercepting groups of requests, so that common policies and cross-cutting concerns can be applied on a targeted basis.</span></span> <span data-ttu-id="403e4-139">Filtry lze použít k jednotlivým akcím, celý řadiče, nebo globálně pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="403e4-139">Filters can be applied to individual actions, whole controllers, or globally for an application.</span></span>

<span data-ttu-id="403e4-140">Pro webová rozhraní API ASP.NET Core MVC podporuje [ _vyjednávání obsahu_](/aspnet/core/mvc/models/formatting), povolíte požadavky k určení, jak by měly být formátovány odpovědi.</span><span class="sxs-lookup"><span data-stu-id="403e4-140">For web APIs, ASP.NET Core MVC supports [_content negotiation_](/aspnet/core/mvc/models/formatting), allowing requests to specify how responses should be formatted.</span></span> <span data-ttu-id="403e4-141">Založen na záhlavích zadaný v požadavku, bude akce vrácení dat formátu odpovědi v XML, JSON nebo jiný podporovaný formát.</span><span class="sxs-lookup"><span data-stu-id="403e4-141">Based on headers provided in the request, actions returning data will format the response in XML, JSON, or another supported format.</span></span> <span data-ttu-id="403e4-142">Tato funkce umožňuje využívat víc klientů s požadavky na jiný datový formát stejného rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="403e4-142">This feature enables the same API to be used by multiple clients with different data format requirements.</span></span>

> ### <a name="references--mapping-requests-to-responses"></a><span data-ttu-id="403e4-143">Odkazy – mapování vyžádá, aby odpovědi</span><span class="sxs-lookup"><span data-stu-id="403e4-143">References – Mapping Requests to Responses</span></span>
>
> - <span data-ttu-id="403e4-144">**Směrování na akce Kontroleru**
 > <https://docs.microsoft.com/aspnet/core/mvc/controllers/routing></span><span class="sxs-lookup"><span data-stu-id="403e4-144">**Routing to Controller Actions**
<https://docs.microsoft.com/aspnet/core/mvc/controllers/routing></span></span>
> - <span data-ttu-id="403e4-145">**Vazby modelu**
 > <https://docs.microsoft.com/aspnet/core/mvc/models/model-binding></span><span class="sxs-lookup"><span data-stu-id="403e4-145">**Model Binding**
<https://docs.microsoft.com/aspnet/core/mvc/models/model-binding></span></span>
> - <span data-ttu-id="403e4-146">**Ověření modelu**
 > <https://docs.microsoft.com/aspnet/core/mvc/models/validation></span><span class="sxs-lookup"><span data-stu-id="403e4-146">**Model Validation**
<https://docs.microsoft.com/aspnet/core/mvc/models/validation></span></span>
> - <span data-ttu-id="403e4-147">**Filtry**
 > <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters></span><span class="sxs-lookup"><span data-stu-id="403e4-147">**Filters**
<https://docs.microsoft.com/aspnet/core/mvc/controllers/filters></span></span>

## <a name="working-with-dependencies"></a><span data-ttu-id="403e4-148">Práce se závislostmi</span><span class="sxs-lookup"><span data-stu-id="403e4-148">Working with dependencies</span></span>

<span data-ttu-id="403e4-149">Má integrovanou podporu pro ASP.NET Core a interně využívá techniky označované jako [injektáž závislostí](/aspnet/core/fundamentals/dependency-injection).</span><span class="sxs-lookup"><span data-stu-id="403e4-149">ASP.NET Core has built-in support for and internally makes use of a technique known as [dependency injection](/aspnet/core/fundamentals/dependency-injection).</span></span> <span data-ttu-id="403e4-150">Injektáž závislostí je technika, která umožňuje volné párování mezi různé části aplikace.</span><span class="sxs-lookup"><span data-stu-id="403e4-150">Dependency injection is a technique that enables loose coupling between different parts of an application.</span></span> <span data-ttu-id="403e4-151">Volnější párování je žádoucí, protože to usnadňuje izolace částí aplikace umožňující testování nebo nahrazení.</span><span class="sxs-lookup"><span data-stu-id="403e4-151">Looser coupling is desirable because it makes it easier to isolate parts of the application, allowing for testing or replacement.</span></span> <span data-ttu-id="403e4-152">Je také podstatně tím snížíte pravděpodobnost, že změna v jedné části aplikace bude mít neočekávané dopad někde jinde v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="403e4-152">It also makes it less likely that a change in one part of the application will have an unexpected impact somewhere else in the application.</span></span> <span data-ttu-id="403e4-153">Injektáž závislostí je založený na principu inverzi závislostí a často je klíčem k dosažení Princip otevřený/uzavřený.</span><span class="sxs-lookup"><span data-stu-id="403e4-153">Dependency injection is based on the dependency inversion principle, and is often key to achieving the open/closed principle.</span></span> <span data-ttu-id="403e4-154">Při vyhodnocování, jak vaše aplikace funguje s jeho závislostí, dávejte ale pozor [statické plevami](https://deviq.com/static-cling/) kódu pach a nezapomeňte, aphorism "[nové je spojovací](https://ardalis.com/new-is-glue)."</span><span class="sxs-lookup"><span data-stu-id="403e4-154">When evaluating how your application works with its dependencies, beware of the [static cling](https://deviq.com/static-cling/) code smell, and remember the aphorism "[new is glue](https://ardalis.com/new-is-glue)."</span></span>

<span data-ttu-id="403e4-155">Plevami statický nastane, pokud volání statické metody třídy nebo přistupovat ke statické vlastnosti, které mají vedlejší účinky nebo závislosti na infrastruktuře.</span><span class="sxs-lookup"><span data-stu-id="403e4-155">Static cling occurs when your classes make calls to static methods, or access static properties, which have side effects or dependencies on infrastructure.</span></span> <span data-ttu-id="403e4-156">Například pokud máte metodu, která volá statická metoda, která pak zapisuje do databáze, vaše metoda je těsně spjat s databáze.</span><span class="sxs-lookup"><span data-stu-id="403e4-156">For example, if you have a method that calls a static method, which in turn writes to a database, your method is tightly coupled to the database.</span></span> <span data-ttu-id="403e4-157">Cokoli, co toto volání databáze přestane fungovat přeruší metodu.</span><span class="sxs-lookup"><span data-stu-id="403e4-157">Anything that breaks that database call will break your method.</span></span> <span data-ttu-id="403e4-158">Testování těchto metod je známo, že obtížné, protože tyto testy vyžadují komerční napodobování knihovny k napodobení volání statické, nebo pouze jde testovat pomocí testovací databázi na místě.</span><span class="sxs-lookup"><span data-stu-id="403e4-158">Testing such methods is notoriously difficult, since such tests either require commercial mocking libraries to mock the static calls, or can only be tested with a test database in place.</span></span> <span data-ttu-id="403e4-159">Statické volání, které nemají žádné závislosti na infrastruktuře, zejména těch, které jsou zcela bezstavové, se dají volat a mít žádný vliv na párování nebo testovatelnosti (nad rámec spojovacího kódu na statické volání sebe sama).</span><span class="sxs-lookup"><span data-stu-id="403e4-159">Static calls that don't have any dependence on infrastructure, especially those that are completely stateless, are fine to call and have no impact on coupling or testability (beyond coupling code to the static call itself).</span></span>

<span data-ttu-id="403e4-160">Mnoho vývojářů pochopení rizik statické plevami a globální stav, ale bude stále úzce spojit svůj kód pro konkrétní implementace prostřednictvím přímé vytváření instancí.</span><span class="sxs-lookup"><span data-stu-id="403e4-160">Many developers understand the risks of static cling and global state, but will still tightly couple their code to specific implementations through direct instantiation.</span></span> <span data-ttu-id="403e4-161">"Nové je připevnit" má být připomenutí toto párování a obecné odsouzení využívání `new` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="403e4-161">"New is glue" is meant to be a reminder of this coupling, and not a general condemnation of the use of the `new` keyword.</span></span> <span data-ttu-id="403e4-162">Stejně jako s volání statické metody, nové instance typů, které nemají žádné externí závislosti obvykle není úzce spárovat kód podrobnosti implementace nebo ztížit testování.</span><span class="sxs-lookup"><span data-stu-id="403e4-162">Just as with static method calls, new instances of types that have no external dependencies typically do not tightly couple code to implementation details or make testing more difficult.</span></span> <span data-ttu-id="403e4-163">Ale pokaždé, když je vytvořena instance třídy, pouze krátkou chvíli trvat zvažte, jestli má smysl pevně kódovat této konkrétní instance v této konkrétní umístění, nebo pokud by bylo lepší návrh požádat o tuto instanci jako závislost.</span><span class="sxs-lookup"><span data-stu-id="403e4-163">But each time a class is instantiated, take just a brief moment to consider whether it makes sense to hard-code that specific instance in that particular location, or if it would be a better design to request that instance as a dependency.</span></span>

### <a name="declare-your-dependencies"></a><span data-ttu-id="403e4-164">Deklarace závislostí</span><span class="sxs-lookup"><span data-stu-id="403e4-164">Declare your dependencies</span></span>

<span data-ttu-id="403e4-165">ASP.NET Core je postavené na s metody a třídy deklarují jejich závislosti, požadování jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="403e4-165">ASP.NET Core is built around having methods and classes declare their dependencies, requesting them as arguments.</span></span> <span data-ttu-id="403e4-166">Aplikace ASP.NET jsou obvykle nastavené ve třídě spuštění, které je nakonfigurována pro podporu injektáž závislostí v několika fázích.</span><span class="sxs-lookup"><span data-stu-id="403e4-166">ASP.NET applications are typically set up in a Startup class, which itself is configured to support dependency injection at several points.</span></span> <span data-ttu-id="403e4-167">Pokud počáteční třída nemá konstruktor, můžete požádat o závislosti pomocí konstruktoru, například takto:</span><span class="sxs-lookup"><span data-stu-id="403e4-167">If your Startup class has a constructor, it can request dependencies through the constructor, like so:</span></span>

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

<span data-ttu-id="403e4-168">Třída při spuštění je zajímavé, v tom, že neexistují žádné požadavky na explicitní typ pro něj.</span><span class="sxs-lookup"><span data-stu-id="403e4-168">The Startup class is interesting in that there are no explicit type requirements for it.</span></span> <span data-ttu-id="403e4-169">Nedědí ze základní třídy speciální spuštění, ani je implementuje žádné konkrétní rozhraní.</span><span class="sxs-lookup"><span data-stu-id="403e4-169">It doesn't inherit from a special Startup base class, nor does it implement any particular interface.</span></span> <span data-ttu-id="403e4-170">Můžete jí konstruktor, nebo Ne, a můžete zadat libovolný počet parametrů v konstruktoru chcete.</span><span class="sxs-lookup"><span data-stu-id="403e4-170">You can give it a constructor, or not, and you can specify as many parameters on the constructor as you want.</span></span> <span data-ttu-id="403e4-171">Při spuštění webového hostitele, které jste nakonfigurovali pro vaše aplikace bude volat třída při spuštění, které má použít a pomocí vkládání závislostí naplnit všechny závislosti, které vyžaduje třídu pro spuštění.</span><span class="sxs-lookup"><span data-stu-id="403e4-171">When the web host you've configured for your application starts, it will call the Startup class you've told it to use, and will use dependency injection to populate any dependencies the Startup class requires.</span></span> <span data-ttu-id="403e4-172">Samozřejmě pokud jste požádali o parametry, které nejsou nakonfigurované v kontejneru služby používat ASP.NET Core, zobrazí se výjimka, ale tak dlouho, dokud zůstanou závislosti kontejneru ví o, můžete požádat o všechno, co chcete.</span><span class="sxs-lookup"><span data-stu-id="403e4-172">Of course, if you request parameters that aren't configured in the services container used by ASP.NET Core, you'll get an exception, but as long as you stick to dependencies the container knows about, you can request anything you want.</span></span>

<span data-ttu-id="403e4-173">Injektáž závislostí je integrovaná do aplikace ASP.NET Core přímo od začátku, při vytváření instancí při spuštění.</span><span class="sxs-lookup"><span data-stu-id="403e4-173">Dependency injection is built into your ASP.NET Core apps right from the start, when you create the Startup instance.</span></span> <span data-ttu-id="403e4-174">Nelze zastavit existuje pro třídu pro spuštění.</span><span class="sxs-lookup"><span data-stu-id="403e4-174">It doesn't stop there for the Startup class.</span></span> <span data-ttu-id="403e4-175">Můžete také požádat o závislosti v metodě konfigurace:</span><span class="sxs-lookup"><span data-stu-id="403e4-175">You can also request dependencies in the Configure method:</span></span>

```csharp
public void Configure(IApplicationBuilder app,
    IHostingEnvironment env,
    ILoggerFactory loggerFactory)
{

}
```

<span data-ttu-id="403e4-176">Výjimka, která má toto chování je ConfigureServices – metoda je nutné provést pouze jeden parametr typu IServiceCollection.</span><span class="sxs-lookup"><span data-stu-id="403e4-176">The ConfigureServices method is the exception to this behavior; it must take just one parameter of type IServiceCollection.</span></span> <span data-ttu-id="403e4-177">Není nutné ve skutečnosti k podpoře vkládání závislostí, protože na jedné straně je zodpovědný za přidání objektů do kontejneru služby a na druhé má přístup ke všem službám aktuálně nakonfigurovaná prostřednictvím IServiceCollection parametru.</span><span class="sxs-lookup"><span data-stu-id="403e4-177">It doesn't really need to support dependency injection, since on the one hand it is responsible for adding objects to the services container, and on the other it has access to all currently configured services via the IServiceCollection parameter.</span></span> <span data-ttu-id="403e4-178">Proto můžete pracovat se závislosti definované v kolekci služby ASP.NET Core v každé části třídu pro spuštění, můžete si vyžádat potřebný služby jako parametr nebo práce s IServiceCollection v ConfigureServices.</span><span class="sxs-lookup"><span data-stu-id="403e4-178">Thus, you can work with dependencies defined in the ASP.NET Core services collection in every part of the Startup class, either by requesting the needed service as a parameter or by working with the IServiceCollection in ConfigureServices.</span></span>

> [!NOTE]
> <span data-ttu-id="403e4-179">Pokud je potřeba zajistit určité služby jsou k dispozici pro vaši třídu pro spuštění, můžete je nakonfigurovat pomocí WebHostBuilder a jeho ConfigureServices metodu.</span><span class="sxs-lookup"><span data-stu-id="403e4-179">If you need to ensure certain services are available to your Startup class, you can configure them using WebHostBuilder and its ConfigureServices method.</span></span>

<span data-ttu-id="403e4-180">Třída při spuštění je model jak strukturovat ostatních částech aplikace ASP.NET Core z řadiče s Middlewarem pro filtry, které vlastní služby.</span><span class="sxs-lookup"><span data-stu-id="403e4-180">The Startup class is a model for how you should structure other parts of your ASP.NET Core application, from Controllers to Middleware to Filters to your own Services.</span></span> <span data-ttu-id="403e4-181">V každém případě byste měli postupovat [explicitní závislosti Princip](https://deviq.com/explicit-dependencies-principle/), požadování závislostí místo přímo jejich vytváření a využitím vkládání závislostí v rámci aplikace.</span><span class="sxs-lookup"><span data-stu-id="403e4-181">In each case, you should follow the [Explicit Dependencies Principle](https://deviq.com/explicit-dependencies-principle/), requesting your dependencies rather than directly creating them, and leveraging dependency injection throughout your application.</span></span> <span data-ttu-id="403e4-182">Dejte pozor, kde a jak můžete přímo vytvořit instanci implementace, zejména služeb a objektů, které pracují s infrastrukturou nebo mají vedlejší účinky.</span><span class="sxs-lookup"><span data-stu-id="403e4-182">Be careful of where and how you directly instantiate implementations, especially services and objects that work with infrastructure or have side effects.</span></span> <span data-ttu-id="403e4-183">Dáváte přednost práci s odběry definovaný v základní vaší aplikace a předané jako argumenty hardcoding odkazy na konkrétní implementaci typů.</span><span class="sxs-lookup"><span data-stu-id="403e4-183">Prefer working with abstractions defined in your application core and passed in as arguments to hardcoding references to specific implementation types.</span></span>

## <a name="structuring-the-application"></a><span data-ttu-id="403e4-184">Strukturování aplikace</span><span class="sxs-lookup"><span data-stu-id="403e4-184">Structuring the application</span></span>

<span data-ttu-id="403e4-185">Monolitické aplikace obvykle mají jeden vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="403e4-185">Monolithic applications typically have a single entry point.</span></span> <span data-ttu-id="403e4-186">V případě webové aplikace ASP.NET Core vstupní bod budou webový projekt ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="403e4-186">In the case of an ASP.NET Core web application, the entry point will be the ASP.NET Core web project.</span></span> <span data-ttu-id="403e4-187">Nicméně to neznamená, že řešení by měla obsahovat právě jeden projekt.</span><span class="sxs-lookup"><span data-stu-id="403e4-187">However, that doesn't mean the solution should consist of just a single project.</span></span> <span data-ttu-id="403e4-188">Je užitečné k rozdělení aplikaci do různých vrstev před dalším postupem podle oddělení oblastí zájmu.</span><span class="sxs-lookup"><span data-stu-id="403e4-188">It's useful to break up the application into different layers in order to follow separation of concerns.</span></span> <span data-ttu-id="403e4-189">Jakmile rozdělené do vrstev, je užitečné se dostat nad rámec složky pro oddělení projekty, které může zajistit lepší zapouzdření.</span><span class="sxs-lookup"><span data-stu-id="403e4-189">Once broken up into layers, it's helpful to go beyond folders to separate projects, which can help achieve better encapsulation.</span></span> <span data-ttu-id="403e4-190">Nejlepší metodou k dosažení těchto cílů s aplikací ASP.NET Core je varianta čisté architektuře popsané v kapitole 5.</span><span class="sxs-lookup"><span data-stu-id="403e4-190">The best approach to achieve these goals with an ASP.NET Core application is a variation of the Clean Architecture discussed in chapter 5.</span></span> <span data-ttu-id="403e4-191">Následující tento přístup aplikace řešení bude tvořit samostatné knihovny uživatelského rozhraní, infrastruktury a ApplicationCore.</span><span class="sxs-lookup"><span data-stu-id="403e4-191">Following this approach, the application's solution will be comprised of separate libraries for the UI, Infrastructure, and ApplicationCore.</span></span>

<span data-ttu-id="403e4-192">Kromě těchto projektů samostatný testovací projekty jsou zahrnuté také (testování je popsáno v kapitole 9).</span><span class="sxs-lookup"><span data-stu-id="403e4-192">In addition to these projects, separate test projects are included as well (Testing is discussed in Chapter 9).</span></span>

<span data-ttu-id="403e4-193">Objektový model aplikace a rozhraní musí být umístěné ve ApplicationCore projektu.</span><span class="sxs-lookup"><span data-stu-id="403e4-193">The application's object model and interfaces should be placed in the ApplicationCore project.</span></span> <span data-ttu-id="403e4-194">Tento projekt bude mít například několik závislostí nejvíce a ho bude odkazovat jiné projekty v řešení.</span><span class="sxs-lookup"><span data-stu-id="403e4-194">This project will have as few dependencies as possible, and the other projects in the solution will reference it.</span></span> <span data-ttu-id="403e4-195">Obchodní entity, které je potřeba nastavit jako trvalý, jsou definovány v ApplicationCore projektu, jako jsou služby, které přímo nezávisí na infrastrukturu.</span><span class="sxs-lookup"><span data-stu-id="403e4-195">Business entities that need to be persisted are defined in the ApplicationCore project, as are services that do not directly depend on infrastructure.</span></span>

<span data-ttu-id="403e4-196">Podrobnosti implementace, například jak se provádí trvalého nebo jak může být odeslána oznámení pro uživatele, jsou uloženy v projektu infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="403e4-196">Implementation details, such as how persistence is performed or how notifications might be sent to a user, are kept in the Infrastructure project.</span></span> <span data-ttu-id="403e4-197">Tento projekt bude odkazovat na specifický pro implementaci balíčků, jako jsou Entity Framework Core, ale by neměly zveřejňovat informace o těchto implementacích mimo projekt.</span><span class="sxs-lookup"><span data-stu-id="403e4-197">This project will reference implementation-specific packages such as Entity Framework Core, but should not expose details about these implementations outside of the project.</span></span> <span data-ttu-id="403e4-198">Služby infrastruktury a úložiště by měly implementovat rozhraní, které jsou definovány v projektu ApplicationCore a jeho implementace trvalost zodpovídají za načítání a ukládání entit, které jsou definovány v ApplicationCore.</span><span class="sxs-lookup"><span data-stu-id="403e4-198">Infrastructure services and repositories should implement interfaces that are defined in the ApplicationCore project, and its persistence implementations are responsible for retrieving and storing entities defined in ApplicationCore.</span></span>

<span data-ttu-id="403e4-199">Projekt uživatelského rozhraní ASP.NET Core je zodpovědný za jakékoli obavy úrovni uživatelského rozhraní, ale by neměly obsahovat podrobnosti o obchodní logiku nebo infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="403e4-199">The ASP.NET Core UI project is responsible for any UI level concerns, but should not include business logic or infrastructure details.</span></span> <span data-ttu-id="403e4-200">Ve skutečnosti v ideálním případě nemůže i mít závislost na projektu infrastrukturu, která vám pomůže zajistit, že se omylem zavedeny žádné závislosti mezi dva projekty.</span><span class="sxs-lookup"><span data-stu-id="403e4-200">In fact, ideally it shouldn't even have a dependency on the Infrastructure project, which will help ensure no dependency between the two projects is introduced accidentally.</span></span> <span data-ttu-id="403e4-201">Toho lze dosáhnout pomocí kontejneru DI třetích stran stejně jako StructureMap, který umožňuje definovat DI pravidla v registru třídy v každém projektu.</span><span class="sxs-lookup"><span data-stu-id="403e4-201">This can be achieved using a third-party DI container like StructureMap, which allows you to define DI rules in Registry classes in each project.</span></span>

<span data-ttu-id="403e4-202">Dalším přístupem k oddělení aplikace od podrobností implementace je mikroslužby volání aplikace, možná nasazený v jednotlivých kontejnerech Dockeru.</span><span class="sxs-lookup"><span data-stu-id="403e4-202">Another approach to decoupling the application from implementation details is to have the application call microservices, perhaps deployed in individual Docker containers.</span></span> <span data-ttu-id="403e4-203">To poskytuje ještě větší oddělení otázky a oddělení než využitím DI mezi dva projekty, ale má další složitosti.</span><span class="sxs-lookup"><span data-stu-id="403e4-203">This provides even greater separation of concerns and decoupling than leveraging DI between two projects, but has additional complexity.</span></span>

### <a name="feature-organization"></a><span data-ttu-id="403e4-204">Funkce organizace</span><span class="sxs-lookup"><span data-stu-id="403e4-204">Feature organization</span></span>

<span data-ttu-id="403e4-205">Aplikace ASP.NET Core ve výchozím nastavení, uspořádejte jejich strukturu složek Kontrolerů a zobrazení a často modely ViewModel.</span><span class="sxs-lookup"><span data-stu-id="403e4-205">By default, ASP.NET Core applications organize their folder structure to include Controllers and Views, and frequently ViewModels.</span></span> <span data-ttu-id="403e4-206">Kód na straně klienta pro podporu těchto struktur na straně serveru jsou obvykle uložená samostatně ve složce wwwroot.</span><span class="sxs-lookup"><span data-stu-id="403e4-206">Client-side code to support these server-side structures is typically stored separately in the wwwroot folder.</span></span> <span data-ttu-id="403e4-207">Však velké aplikace setkat s problémy u této organizace, protože pracující na jakékoli dané funkce často vyžaduje přechod mezi tyto složky.</span><span class="sxs-lookup"><span data-stu-id="403e4-207">However, large applications may encounter problems with this organization, since working on any given feature often requires jumping between these folders.</span></span> <span data-ttu-id="403e4-208">Načte mnohem obtížnější, roste počet souborů a podsložek v každé složky, což vede k spoustu posouvání se v Průzkumníku řešení.</span><span class="sxs-lookup"><span data-stu-id="403e4-208">This gets more and more difficult as the number of files and subfolders in each folder grows, resulting in a great deal of scrolling through Solution Explorer.</span></span> <span data-ttu-id="403e4-209">Jedním řešením tohoto problému, je uspořádat kód aplikace podle _funkce_ místo podle typu souboru.</span><span class="sxs-lookup"><span data-stu-id="403e4-209">One solution to this problem is to organize application code by _feature_ instead of by file type.</span></span> <span data-ttu-id="403e4-210">Tento styl organizace se obvykle označuje jako složky funkce nebo funkce řezů (viz také: [Svislé řezy](https://deviq.com/vertical-slices/)).</span><span class="sxs-lookup"><span data-stu-id="403e4-210">This organizational style is typically referred to as feature folders or feature slices (see also: [Vertical Slices](https://deviq.com/vertical-slices/)).</span></span>

<span data-ttu-id="403e4-211">ASP.NET Core MVC podporuje oblasti pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="403e4-211">ASP.NET Core MVC supports Areas for this purpose.</span></span> <span data-ttu-id="403e4-212">Pomocí oblastí, můžete vytvořit samostatné sady Kontrolerů a zobrazení složek (stejně jako jakékoli přidružených modelech) v každé oblasti složky.</span><span class="sxs-lookup"><span data-stu-id="403e4-212">Using areas, you can create separate sets of Controllers and Views folders (as well as any associated models) in each Area folder.</span></span> <span data-ttu-id="403e4-213">Obrázek 7-1 znázorňuje strukturu složky příklad používat.</span><span class="sxs-lookup"><span data-stu-id="403e4-213">Figure 7-1 shows an example folder structure, using Areas.</span></span>

![](./media/image7-1.png)

<span data-ttu-id="403e4-214">Obrázek 7-1 ukázka oblasti organizace</span><span class="sxs-lookup"><span data-stu-id="403e4-214">Figure 7-1 Sample Area Organization</span></span>

<span data-ttu-id="403e4-215">Při použití oblasti, je nutné použít atributy k vyplnění řadičích s názvem oblast, do které patří:</span><span class="sxs-lookup"><span data-stu-id="403e4-215">When using Areas, you must use attributes to decorate your controllers with the name of the area to which they belong:</span></span>

```csharp
[Area("Catalog")]
public class HomeController
{}
```

<span data-ttu-id="403e4-216">Potřebujete také přidává oblast na trasy:</span><span class="sxs-lookup"><span data-stu-id="403e4-216">You also need to add area support to your routes:</span></span>

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

<span data-ttu-id="403e4-217">Kromě integrované podpory pro oblasti můžete také použít vlastní strukturu složek a konvence místo atributy a vlastní trasy.</span><span class="sxs-lookup"><span data-stu-id="403e4-217">In addition to the built-in support for Areas, you can also use your own folder structure, and conventions in place of attributes and custom routes.</span></span> <span data-ttu-id="403e4-218">To by umožnilo mít funkce složky, které nezahrnuli samostatné složky pro zobrazení, Kontrolery, atd., udržování hierarchii plošší a usnadnit tak vidět, že všechny související soubory na jednom místě pro jednotlivé funkce.</span><span class="sxs-lookup"><span data-stu-id="403e4-218">This would allow you to have feature folders that didn't include separate folders for Views, Controllers, etc., keeping the hierarchy flatter and making it easier to see all related files in a single place for each feature.</span></span>

<span data-ttu-id="403e4-219">ASP.NET Core používá konvence integrované typy mohla kontrolovat své chování.</span><span class="sxs-lookup"><span data-stu-id="403e4-219">ASP.NET Core uses built-in convention types to control its behavior.</span></span> <span data-ttu-id="403e4-220">Můžete změnit nebo nahraďte tyto konvence.</span><span class="sxs-lookup"><span data-stu-id="403e4-220">You can modify or replace these conventions.</span></span> <span data-ttu-id="403e4-221">Můžete například vytvořit konvence, automaticky získá název funkce pro daný kontroler podle jeho obor názvů (což obvykle souvisí s složku, ve kterém se nachází kontroler):</span><span class="sxs-lookup"><span data-stu-id="403e4-221">For example, you can create a convention that will automatically get the feature name for a given controller based on its namespace (which typically correlates to the folder in which the controller is located):</span></span>

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

<span data-ttu-id="403e4-222">Potom zadejte tyto vytváření názvů jako možnost při přidání podpory pro rozhraní MVC do vaší aplikace v ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="403e4-222">You then specify this convention as an option when you add support for MVC to your application in ConfigureServices:</span></span>

```csharp
services.AddMvc(o => o.Conventions.Add(new FeatureConvention()));
```

<span data-ttu-id="403e4-223">ASP.NET Core MVC také používá konvence pro vyhledání zobrazení.</span><span class="sxs-lookup"><span data-stu-id="403e4-223">ASP.NET Core MVC also uses a convention to locate views.</span></span> <span data-ttu-id="403e4-224">Lze jej přepsat pomocí vlastních konvence tak, aby zobrazení budou umístěny ve složkách funkci (pomocí názvu funkce poskytované FeatureConvention, výše).</span><span class="sxs-lookup"><span data-stu-id="403e4-224">You can override it with a custom convention so that views will be located in your feature folders (using the feature name provided by the FeatureConvention, above).</span></span> <span data-ttu-id="403e4-225">Další informace o tento přístup a stáhnout ukázku práce z článku na webu MSDN můžete [řezy funkce pro ASP.NET Core MVC](https://msdn.microsoft.com/magazine/mt763233.aspx).</span><span class="sxs-lookup"><span data-stu-id="403e4-225">You can learn more about this approach and download a working sample from the MSDN article, [Feature Slices for ASP.NET Core MVC](https://msdn.microsoft.com/magazine/mt763233.aspx).</span></span>

### <a name="cross-cutting-concerns"></a><span data-ttu-id="403e4-226">Související aspekty</span><span class="sxs-lookup"><span data-stu-id="403e4-226">Cross-cutting concerns</span></span>

<span data-ttu-id="403e4-227">S růstem aplikace stává čím dál důležitějším zohlednit si vyskytující aspekty k vyloučení duplicity a zajistit konzistenci.</span><span class="sxs-lookup"><span data-stu-id="403e4-227">As applications grow, it becomes increasingly important to factor out cross-cutting concerns to eliminate duplication and maintain consistency.</span></span> <span data-ttu-id="403e4-228">Některé příklady vyskytující aspekty aplikace ASP.NET Core se ověřování modelu ověřovacích pravidel, ukládání výstupu do mezipaměti a zpracování chyb, když existuje řada dalších.</span><span class="sxs-lookup"><span data-stu-id="403e4-228">Some examples of cross-cutting concerns in ASP.NET Core applications are authentication, model validation rules, output caching, and error handling, though there are many others.</span></span> <span data-ttu-id="403e4-229">ASP.NET Core MVC [filtry](/aspnet/core/mvc/controllers/filters) umožňuje spuštění kódu před nebo po určité kroky v kanálu zpracování požadavků.</span><span class="sxs-lookup"><span data-stu-id="403e4-229">ASP.NET Core MVC [filters](/aspnet/core/mvc/controllers/filters) allow you to run code before or after certain steps in the request processing pipeline.</span></span> <span data-ttu-id="403e4-230">Například filtr můžete spustit před a po vytvoření vazby modelu před a po akci, nebo před a po výsledku akce.</span><span class="sxs-lookup"><span data-stu-id="403e4-230">For instance, a filter can run before and after model binding, before and after an action, or before and after an action's result.</span></span> <span data-ttu-id="403e4-231">Můžete také použít filtr autorizace pro řízení přístupu k rest z kanálu.</span><span class="sxs-lookup"><span data-stu-id="403e4-231">You can also use an authorization filter to control access to the rest of the pipeline.</span></span> <span data-ttu-id="403e4-232">Obrázky 7-2 ukazuje jak požadavek spuštění toků filtry, pokud nakonfigurované.</span><span class="sxs-lookup"><span data-stu-id="403e4-232">Figures 7-2 shows how request execution flows through filters, if configured.</span></span>

![Žádost se zpracovává prostřednictvím filtry autorizace, prostředků filtry, vazby modelu, filtry akce, provedení akce a převod výsledek akce, filtry výjimek, filtry výsledků a výsledek spuštění.](./media/image7-2.png)

<span data-ttu-id="403e4-235">Obrázek 7-2 provádění požadavku prostřednictvím kanálu požadavku a filtry.</span><span class="sxs-lookup"><span data-stu-id="403e4-235">Figure 7-2 Request execution through filters and request pipeline.</span></span>

<span data-ttu-id="403e4-236">Filtry jsou obvykle implementovány jako atributy, takže je lze následně použít na řadiče nebo akce (nebo dokonce globálně).</span><span class="sxs-lookup"><span data-stu-id="403e4-236">Filters are usually implemented as attributes, so you can apply them to controllers or actions (or even globally).</span></span> <span data-ttu-id="403e4-237">Když se přidá tímto způsobem, filtry na úrovni akce přepsání nebo jsou postavené na úrovni kontroleru, filtrů které samy přepsat globální filtry.</span><span class="sxs-lookup"><span data-stu-id="403e4-237">When added in this fashion, filters specified at the action level override or build upon filters specified at the controller level, which themselves override global filters.</span></span> <span data-ttu-id="403e4-238">Například \[trasy\] atribut lze použít k vytvoření trasy mezi kontrolery a akce.</span><span class="sxs-lookup"><span data-stu-id="403e4-238">For example, the \[Route\] attribute can be used to build up routes between controllers and actions.</span></span> <span data-ttu-id="403e4-239">Obdobně autorizace můžete nakonfigurovat na úrovni kontroleru a poté přepsána jednotlivé akce, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="403e4-239">Likewise, authorization can be configured at the controller level, and then overridden by individual actions, as the following sample demonstrates:</span></span>

```csharp
[Authorize]
public class AccountController : Controller

{
    [AllowAnonymous]
    public async Task<IActionResult> Login() {}
    public async Task<IActionResult> ForgotPassword() {}
}
```

<span data-ttu-id="403e4-240">První metoda přihlášení, využívá filtr AllowAnonymous (atribut) k přepsání filtru Authorize nastavená na úrovni kontroleru.</span><span class="sxs-lookup"><span data-stu-id="403e4-240">The first method, Login, uses the AllowAnonymous filter (attribute) to override the Authorize filter set at the controller level.</span></span> <span data-ttu-id="403e4-241">Akce ForgotPassword (a další akce v třídě, která nemá atribut AllowAnonymous) bude vyžadovat ověřeného požadavku.</span><span class="sxs-lookup"><span data-stu-id="403e4-241">The ForgotPassword action (and any other action in the class that doesn't have an AllowAnonymous attribute) will require an authenticated request.</span></span>

<span data-ttu-id="403e4-242">Filtry lze použít k vyloučení duplicity v podobě běžnou chybou zpracování zásady pro rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="403e4-242">Filters can be used to eliminate duplication in the form of common error handling policies for APIs.</span></span> <span data-ttu-id="403e4-243">Typické zásad rozhraní API je například vrátit NotFound reakci na požadavky odkazující na klíče, které neexistují a odpověď chybného požadavku, pokud selže ověření modelu.</span><span class="sxs-lookup"><span data-stu-id="403e4-243">For example, a typical API policy is to return a NotFound response to requests referencing keys that do not exist, and a BadRequest response if model validation fails.</span></span> <span data-ttu-id="403e4-244">Následující příklad znázorňuje tyto dvě zásady v akci:</span><span class="sxs-lookup"><span data-stu-id="403e4-244">The following example demonstrates these two policies in action:</span></span>

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

<span data-ttu-id="403e4-245">Nepovolit metody akce pro zaplní podmíněný kód tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="403e4-245">Don't allow your action methods to become cluttered with conditional code like this.</span></span> <span data-ttu-id="403e4-246">Místo toho o přijetí změn zásad do filtry, které mohou být použity na základě podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="403e4-246">Instead, pull the policies into filters that can be applied on an as-needed basis.</span></span> <span data-ttu-id="403e4-247">Kontrola ověření modelu, které se budou objevovat pokaždé, když je odeslán příkaz k rozhraní API, můžete v tomto příkladu nahrazuje následující atribut:</span><span class="sxs-lookup"><span data-stu-id="403e4-247">In this example, the model validation check, which should occur any time a command is sent to the API, can be replaced by the following attribute:</span></span>

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

<span data-ttu-id="403e4-248">Filtr lze, zkontrolujte, zda existuje záznam a vrátit kód 404, před provedením akce, takže odpadá potřeba k provedení těchto kontrol v akci.</span><span class="sxs-lookup"><span data-stu-id="403e4-248">Likewise, a filter can be used to check if a record exists and return a 404 before the action is executed, eliminating the need to perform these checks in the action.</span></span> <span data-ttu-id="403e4-249">Po výseče běžné konvence a uspořádané řešení k oddělení infrastruktury kódu a obchodní logiku z vašeho uživatelského rozhraní, by měla být velmi dynamicky vaše metody akce MVC:</span><span class="sxs-lookup"><span data-stu-id="403e4-249">Once you've pulled out common conventions and organized your solution to separate infrastructure code and business logic from your UI, your MVC action methods should be extremely thin:</span></span>

```csharp
[HttpPut("{id}")]
[ValidateAuthorExists]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

<span data-ttu-id="403e4-250">Další informace o implementaci filtry a stáhněte si ukázky práce z článku na webu MSDN [reálného světa ASP.NET Core MVC filtry](https://msdn.microsoft.com/magazine/mt767699.aspx).</span><span class="sxs-lookup"><span data-stu-id="403e4-250">You can read more about implementing filters and download a working sample from the MSDN article, [Real World ASP.NET Core MVC Filters](https://msdn.microsoft.com/magazine/mt767699.aspx).</span></span>

> ### <a name="references--structuring-applications"></a><span data-ttu-id="403e4-251">Odkazy – strukturování aplikací</span><span class="sxs-lookup"><span data-stu-id="403e4-251">References – Structuring applications</span></span>
>
> - <span data-ttu-id="403e4-252">**Oblasti**</span><span class="sxs-lookup"><span data-stu-id="403e4-252">**Areas**</span></span>  
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/areas>
> - <span data-ttu-id="403e4-253">**Zpravodaj MSDN Magazine – funkce řezy pro ASP.NET Core MVC**</span><span class="sxs-lookup"><span data-stu-id="403e4-253">**MSDN Magazine – Feature Slices for ASP.NET Core MVC**</span></span>  
>   <https://msdn.microsoft.com/magazine/mt763233.aspx>
> - <span data-ttu-id="403e4-254">**Filtry**</span><span class="sxs-lookup"><span data-stu-id="403e4-254">**Filters**</span></span>  
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - <span data-ttu-id="403e4-255">**MSDN – filtry reálného světa ASP.NET Core MVC**</span><span class="sxs-lookup"><span data-stu-id="403e4-255">**MSDN – Real World ASP.NET Core MVC Filters**</span></span>  
>   <https://msdn.microsoft.com/magazine/mt767699.aspx>

## <a name="security"></a><span data-ttu-id="403e4-256">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="403e4-256">Security</span></span>

<span data-ttu-id="403e4-257">Zabezpečení webových aplikací je velké tématu, s mnoha aspekty.</span><span class="sxs-lookup"><span data-stu-id="403e4-257">Securing web applications is a large topic, with many considerations.</span></span> <span data-ttu-id="403e4-258">Na nejzákladnější úrovni zabezpečení je nutné si ověřit, budete vědět, kdo je pocházející z daného požadavku a pak zajistit, že žádost má jenom přístup k prostředkům, které by měl.</span><span class="sxs-lookup"><span data-stu-id="403e4-258">At its most basic level, security involves ensuring you know who a given request is coming from, and then ensuring that the request only has access to resources it should.</span></span> <span data-ttu-id="403e4-259">Ověřování provádí porovnání se žádostí o těch v úložišti důvěryhodných dat, pokud chcete zobrazit, pokud požadavek má být považována za pocházející ze známého entity zadané přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="403e4-259">Authentication is the process of comparing credentials provided with a request to those in a trusted data store, to see if the request should be treated as coming from a known entity.</span></span> <span data-ttu-id="403e4-260">Autorizace je proces omezení přístupu k určitým prostředkům na základě identity uživatele.</span><span class="sxs-lookup"><span data-stu-id="403e4-260">Authorization is the process of restricting access to certain resources based on user identity.</span></span> <span data-ttu-id="403e4-261">Třetí potíže se zabezpečením chrání požadavky z odposlouchávání třetími stranami, u kterých byste měli aspoň [Ujistěte se, že se vaše aplikace používá protokol SSL](/aspnet/core/security/enforcing-ssl).</span><span class="sxs-lookup"><span data-stu-id="403e4-261">A third security concern is protecting requests from eavesdropping by third parties, for which you should at least [ensure that SSL is used by your application](/aspnet/core/security/enforcing-ssl).</span></span>

### <a name="authentication"></a><span data-ttu-id="403e4-262">Ověřování</span><span class="sxs-lookup"><span data-stu-id="403e4-262">Authentication</span></span>

<span data-ttu-id="403e4-263">ASP.NET Core Identity je systém členství, které lze použít k podpoře funkce přihlášení pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="403e4-263">ASP.NET Core Identity is a membership system you can use to support login functionality for your application.</span></span> <span data-ttu-id="403e4-264">Obsahuje podporu pro místní uživatelské účty a externí přihlášení zprostředkovatele podpory od poskytovatelů, jako je Microsoft Account, Twitter, Facebook, Google a další.</span><span class="sxs-lookup"><span data-stu-id="403e4-264">It has support for local user accounts as well as external login provider support from providers like Microsoft Account, Twitter, Facebook, Google, and more.</span></span> <span data-ttu-id="403e4-265">Kromě ASP.NET Core Identity vaší aplikace můžete použít ověřování systému windows nebo zprostředkovatele identit třetích stran, jako jsou [serveru identit](https://github.com/IdentityServer/IdentityServer4).</span><span class="sxs-lookup"><span data-stu-id="403e4-265">In addition to ASP.NET Core Identity, your application can use windows authentication, or a third-party identity provider like [Identity Server](https://github.com/IdentityServer/IdentityServer4).</span></span>

<span data-ttu-id="403e4-266">ASP.NET Core Identity je součástí nové šablony projektu, pokud je vybraná možnost jednotlivé uživatelské účty.</span><span class="sxs-lookup"><span data-stu-id="403e4-266">ASP.NET Core Identity is included in new project templates if the Individual User Accounts option is selected.</span></span> <span data-ttu-id="403e4-267">Tato šablona obsahuje podporu pro registrace, přihlášení, externí přihlášení, zapomenutí hesel a další funkce.</span><span class="sxs-lookup"><span data-stu-id="403e4-267">This template includes support for registration, login, external logins, forgotten passwords, and additional functionality.</span></span>

![](./media/image7-3.png)

<span data-ttu-id="403e4-268">Obrázek 7 – 3 vyberte jednotlivé uživatelské účty do mít identitu předkonfigurované.</span><span class="sxs-lookup"><span data-stu-id="403e4-268">Figure 7-3 Select Individual User Accounts to have Identity preconfigured.</span></span>

<span data-ttu-id="403e4-269">Podpora identit je nakonfigurovaný v po spuštění, v ConfigureServices i konfigurace:</span><span class="sxs-lookup"><span data-stu-id="403e4-269">Identity support is configured in Startup, both in ConfigureServices and Configure:</span></span>

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

<span data-ttu-id="403e4-270">Je důležité, že UseIdentity předcházet UseMvc v metodě konfigurace.</span><span class="sxs-lookup"><span data-stu-id="403e4-270">It's important that UseIdentity appear before UseMvc in the Configure method.</span></span> <span data-ttu-id="403e4-271">Při konfiguraci Identity v ConfigureServices, Všimněte si volání AddDefaultTokenProviders.</span><span class="sxs-lookup"><span data-stu-id="403e4-271">When configuring Identity in ConfigureServices, you'll notice a call to AddDefaultTokenProviders.</span></span> <span data-ttu-id="403e4-272">Tato akce nemá nic společného s tokeny, které slouží k zabezpečení komunikace webových, ale místo toho odkazuje na zprostředkovatele, které vytvářejí výzvy, které je možné odeslat uživatelům přes zprávu SMS nebo e-mailu je potvrdit svou identitu.</span><span class="sxs-lookup"><span data-stu-id="403e4-272">This has nothing to do with tokens that may be used to secure web communications, but instead refers to providers that create prompts that can be sent to users via SMS or email in order for them to confirm their identity.</span></span>

<span data-ttu-id="403e4-273">Další informace o [konfiguraci dvojúrovňového ověřování](/aspnet/core/security/authentication/2fa) a [povolení zprostředkovatele externí přihlášení](/aspnet/core/security/authentication/social/) z oficiální dokumentace ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="403e4-273">You can learn more about [configuring two-factor authentication](/aspnet/core/security/authentication/2fa) and [enabling external login providers](/aspnet/core/security/authentication/social/) from the official ASP.NET Core docs.</span></span>

### <a name="authorization"></a><span data-ttu-id="403e4-274">Autorizace</span><span class="sxs-lookup"><span data-stu-id="403e4-274">Authorization</span></span>

<span data-ttu-id="403e4-275">Nejjednodušší forma autorizace zahrnuje omezení přístupu pro anonymní uživatele.</span><span class="sxs-lookup"><span data-stu-id="403e4-275">The simplest form of authorization involves restricting access to anonymous users.</span></span> <span data-ttu-id="403e4-276">Toho lze dosáhnout jednoduše použitím \[Authorize\] atribut na některých řadičích nebo akce.</span><span class="sxs-lookup"><span data-stu-id="403e4-276">This can be achieved by simply applying the \[Authorize\] attribute to certain controllers or actions.</span></span> <span data-ttu-id="403e4-277">Pokud role se používají, je atribut dále rozšířit k omezení přístupu k uživatelům patřícím do určité role, jak je znázorněno:</span><span class="sxs-lookup"><span data-stu-id="403e4-277">If roles are being used, the attribute can be further extended to restrict access to users who belong to certain roles, as shown:</span></span>

```csharp
[Authorize(Roles = "HRManager,Finance")]
public class SalaryController : Controller
{

}
```

<span data-ttu-id="403e4-278">V takovém případě uživatelé, kteří patří do role HRManager nebo Finance (nebo obojí) by měli SalaryController.</span><span class="sxs-lookup"><span data-stu-id="403e4-278">In this case, users belonging to either the HRManager or Finance roles (or both) would have access to the SalaryController.</span></span> <span data-ttu-id="403e4-279">Vyžadovat, aby uživatel patřit do více rolí (nikoli pouze jeden z několika), můžete použít atribut několikrát, pokaždé, když zadáte požadované role.</span><span class="sxs-lookup"><span data-stu-id="403e4-279">To require that a user belong to multiple roles (not just one of several), you can apply the attribute multiple times, specifying a required role each time.</span></span>

<span data-ttu-id="403e4-280">Určení určité sady rolí jako řetězce v mnoha různých kontrolery a akce může mít za následek nežádoucí opakování.</span><span class="sxs-lookup"><span data-stu-id="403e4-280">Specifying certain sets of roles as strings in many different controllers and actions can lead to undesirable repetition.</span></span> <span data-ttu-id="403e4-281">Můžete nakonfigurovat zásady autorizace, které zapouzdřují autorizační pravidla, a pak zadejte zásady namísto jednotlivých rolí při použití \[Authorize\] atribut:</span><span class="sxs-lookup"><span data-stu-id="403e4-281">You can configure authorization policies, which encapsulate authorization rules, and then specify the policy instead of individual roles when applying the \[Authorize\] attribute:</span></span>

```csharp
[Authorize(Policy = "CanViewPrivateReport")]
public IActionResult ExecutiveSalaryReport()
{
    return View();
}
```

<span data-ttu-id="403e4-282">Tímto způsobem pomocí zásad, můžete oddělit typy akcí se s omezením pomocí specifikátoru z konkrétní role nebo pravidla, která se použije na ni.</span><span class="sxs-lookup"><span data-stu-id="403e4-282">Using policies in this way, you can separate the kinds of actions being restricted from the specific roles or rules that apply to it.</span></span> <span data-ttu-id="403e4-283">Později, pokud vytvoříte novou roli, kterou je potřeba mít přístup k určitým prostředkům, můžete jen aktualizovat zásady, nikoli aktualizovat každý seznam rolí na každý \[Authorize\] atribut.</span><span class="sxs-lookup"><span data-stu-id="403e4-283">Later, if you create a new role that needs to have access to certain resources, you can just update a policy, rather than updating every list of roles on every \[Authorize\] attribute.</span></span>

#### <a name="claims"></a><span data-ttu-id="403e4-284">deklarace identity</span><span class="sxs-lookup"><span data-stu-id="403e4-284">Claims</span></span>

<span data-ttu-id="403e4-285">Deklarace identity jsou páry název-hodnota, které představují vlastnosti ověřeného uživatele.</span><span class="sxs-lookup"><span data-stu-id="403e4-285">Claims are name value pairs that represent properties of an authenticated user.</span></span> <span data-ttu-id="403e4-286">Například může ukládat číslo zaměstnance uživatelů jako deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="403e4-286">For example, you might store users' employee number as a claim.</span></span> <span data-ttu-id="403e4-287">Deklarace identity je pak možné jako součást zásad autorizace.</span><span class="sxs-lookup"><span data-stu-id="403e4-287">Claims can then be used as part of authorization policies.</span></span> <span data-ttu-id="403e4-288">Můžete vytvořit zásadu s názvem "EmployeeOnly", který vyžaduje existenci deklaraci identity nazývá "Rovnítkem", jak je znázorněno v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="403e4-288">You could create a policy called "EmployeeOnly" that requires the existence of a claim called "EmployeeNumber", as shown in this example:</span></span>

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

<span data-ttu-id="403e4-289">Tato zásada může pak lze použít \[Authorize\] atribut k ochraně všech kontroleru a akce, jak je popsáno výše.</span><span class="sxs-lookup"><span data-stu-id="403e4-289">This policy could then be used with the \[Authorize\] attribute to protect any controller and/or action, as described above.</span></span>

#### <a name="securing-web-apis"></a><span data-ttu-id="403e4-290">Zabezpečení webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="403e4-290">Securing web APIs</span></span>

<span data-ttu-id="403e4-291">Většina webových rozhraní API by měla implementovat systém ověřování založené na tokenech.</span><span class="sxs-lookup"><span data-stu-id="403e4-291">Most web APIs should implement a token-based authentication system.</span></span> <span data-ttu-id="403e4-292">Ověřování pomocí tokenu je bezstavové a navržená tak, aby byla škálovatelná.</span><span class="sxs-lookup"><span data-stu-id="403e4-292">Token authentication is stateless and designed to be scalable.</span></span> <span data-ttu-id="403e4-293">V systému, ověřování založené na tokenech musí klient nejdřív ověřit zprostředkovatele ověřování.</span><span class="sxs-lookup"><span data-stu-id="403e4-293">In a token-based authentication system, the client must first authenticate with the authentication provider.</span></span> <span data-ttu-id="403e4-294">V případě úspěšného ověření klienta vystaví token, který je jednoduše kryptograficky smysluplné řetězce znaků.</span><span class="sxs-lookup"><span data-stu-id="403e4-294">If successful, the client is issued a token, which is simply a cryptographically meaningful string of characters.</span></span> <span data-ttu-id="403e4-295">Když klient potřebuje potom vydat požadavek na rozhraní API, přidá tento token jako záhlaví v žádosti.</span><span class="sxs-lookup"><span data-stu-id="403e4-295">When the client then needs to issue a request to an API, it adds this token as a header on the request.</span></span> <span data-ttu-id="403e4-296">Server pak ověří daný token nalezen v hlavičce požadavku před dokončením žádosti.</span><span class="sxs-lookup"><span data-stu-id="403e4-296">The server then validates the token found in the request header before completing the request.</span></span> <span data-ttu-id="403e4-297">Obrázek 7 – 4 ukazuje tento proces.</span><span class="sxs-lookup"><span data-stu-id="403e4-297">Figure 7-4 demonstrates this process.</span></span>

![TokenAuth](./media/image7-4.png)

<span data-ttu-id="403e4-299">**Obrázek 7 – 4.**</span><span class="sxs-lookup"><span data-stu-id="403e4-299">**Figure 7-4.**</span></span> <span data-ttu-id="403e4-300">Ověřování založené na tokenech pro webová rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="403e4-300">Token-based authentication for Web APIs.</span></span>

> ### <a name="references--security"></a><span data-ttu-id="403e4-301">Odkazy – zabezpečení</span><span class="sxs-lookup"><span data-stu-id="403e4-301">References – Security</span></span>
>
> - <span data-ttu-id="403e4-302">**Přehled dokumentace zabezpečení**</span><span class="sxs-lookup"><span data-stu-id="403e4-302">**Security Docs Overview**</span></span>  
>   https://docs.microsoft.com/aspnet/core/security/
> - <span data-ttu-id="403e4-303">**Vynucování SSL v aplikaci ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="403e4-303">**Enforcing SSL in an ASP.NET Core App**</span></span>  
>   <https://docs.microsoft.com/aspnet/core/security/enforcing-ssl>
> - <span data-ttu-id="403e4-304">**Úvod do systému Identity**</span><span class="sxs-lookup"><span data-stu-id="403e4-304">**Introduction to Identity**</span></span>  
>   <https://docs.microsoft.com/aspnet/core/security/authentication/identity>
> - <span data-ttu-id="403e4-305">**Úvod k ověřování**</span><span class="sxs-lookup"><span data-stu-id="403e4-305">**Introduction to Authorization**</span></span>  
>   <https://docs.microsoft.com/aspnet/core/security/authorization/introduction>
> - <span data-ttu-id="403e4-306">**Ověřování a autorizace API Apps ve službě Azure App Service**</span><span class="sxs-lookup"><span data-stu-id="403e4-306">**Authentication and Authorization for API Apps in Azure App Service**</span></span>  
>   <https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication>

## <a name="client-communication"></a><span data-ttu-id="403e4-307">Komunikace klienta</span><span class="sxs-lookup"><span data-stu-id="403e4-307">Client communication</span></span>

<span data-ttu-id="403e4-308">Kromě poskytování stránky a reagování na žádosti o data prostřednictvím webových rozhraní API, aplikace ASP.NET Core může komunikovat přímo s připojenými klienty.</span><span class="sxs-lookup"><span data-stu-id="403e4-308">In addition to serving pages and responding to requests for data via web APIs, ASP.NET Core apps can communicate directly with connected clients.</span></span> <span data-ttu-id="403e4-309">Tato odchozí komunikaci, můžete použít širokou škálu technologií přenosu nejčastěji používané jsou objekty Websocket.</span><span class="sxs-lookup"><span data-stu-id="403e4-309">This outbound communication can use a variety of transport technologies, the most common being WebSockets.</span></span> <span data-ttu-id="403e4-310">Funkce SignalR technologie ASP.NET Core je knihovna, která umožňuje snadno přidat funkce komunikaci v reálném čase klient a server pro vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="403e4-310">ASP.NET Core SignalR is a library that makes it simple to add real-time server-to-client communication functionality to your applications.</span></span> <span data-ttu-id="403e4-311">Funkce SignalR, podporuje různé přenosové technologií, včetně protokoly Websocket a abstrahuje tokeny n Podrobnosti implementace od vývojáře.</span><span class="sxs-lookup"><span data-stu-id="403e4-311">SignalR supports a variety of transport technologies, including WebSockets, and abstracts away many of the implementation details from the developer.</span></span>

<span data-ttu-id="403e4-312">Funkce SignalR technologie ASP.NET Core je k dispozici s ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="403e4-312">ASP.NET Core SignalR is available with ASP.NET Core 2.1.</span></span>

<span data-ttu-id="403e4-313">Komunikace v reálném čase klienta, jestli přes WebSockets přímo nebo jinými technikami, jsou užitečné v různých scénářích aplikací.</span><span class="sxs-lookup"><span data-stu-id="403e4-313">Real-time client communication, whether using WebSockets directly or other techniques, are useful in a variety of application scenarios.</span></span> <span data-ttu-id="403e4-314">Možné příklady:</span><span class="sxs-lookup"><span data-stu-id="403e4-314">Some examples include:</span></span>

- <span data-ttu-id="403e4-315">Konverzační živých aplikací</span><span class="sxs-lookup"><span data-stu-id="403e4-315">Live chat room applications</span></span>

- <span data-ttu-id="403e4-316">Monitorování aplikací</span><span class="sxs-lookup"><span data-stu-id="403e4-316">Monitoring applications</span></span>

- <span data-ttu-id="403e4-317">Aktualizace průběhu úlohy</span><span class="sxs-lookup"><span data-stu-id="403e4-317">Job progress updates</span></span>

- <span data-ttu-id="403e4-318">Oznámení</span><span class="sxs-lookup"><span data-stu-id="403e4-318">Notifications</span></span>

- <span data-ttu-id="403e4-319">Interaktivní formulářových aplikací</span><span class="sxs-lookup"><span data-stu-id="403e4-319">Interactive forms applications</span></span>

<span data-ttu-id="403e4-320">Při sestavování komunikaci s klienty do svých aplikací, jsou obvykle dvě součásti:</span><span class="sxs-lookup"><span data-stu-id="403e4-320">When building client communication into your applications, there are typically two components:</span></span>

- <span data-ttu-id="403e4-321">Správce připojení na straně serveru (rozbočovače SignalR, WebSocketManager WebSocketHandler)</span><span class="sxs-lookup"><span data-stu-id="403e4-321">Server-side connection manager (SignalR Hub, WebSocketManager WebSocketHandler)</span></span>

- <span data-ttu-id="403e4-322">Klientské knihovny</span><span class="sxs-lookup"><span data-stu-id="403e4-322">Client-side library</span></span>

<span data-ttu-id="403e4-323">Klienti nejsou omezené na prohlížeče – mobilních aplikací, aplikací konzoly a další nativní aplikace můžou taky komunikovat pomocí SignalR/Websocket.</span><span class="sxs-lookup"><span data-stu-id="403e4-323">Clients aren't limited to browsers – mobile apps, console apps, and other native apps can also communicate using SignalR/WebSockets.</span></span> <span data-ttu-id="403e4-324">Následující jednoduchý program vypisuje všechny obsah odeslaný do chatovací aplikaci do konzoly, jako součást WebSocketManager ukázkovou aplikaci:</span><span class="sxs-lookup"><span data-stu-id="403e4-324">The following simple program echoes all content sent to a chat application to the console, as part of a WebSocketManager sample application:</span></span>

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

<span data-ttu-id="403e4-325">Vezměte v úvahu, že prostředí způsoby, ve kterých vaše aplikace komunikovat přímo pomocí klientských aplikací a zvažte, jestli komunikaci v reálném čase by mohly zlepšit uživatele vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="403e4-325">Consider ways in which your applications communicate directly with client applications, and consider whether real-time communication would improve your app's user experience.</span></span>

> ### <a name="references--client-communication"></a><span data-ttu-id="403e4-326">Odkazy – komunikace klienta</span><span class="sxs-lookup"><span data-stu-id="403e4-326">References – Client Communication</span></span>
>
> - <span data-ttu-id="403e4-327">**Funkce SignalR technologie ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="403e4-327">**ASP.NET Core SignalR**</span></span>  
>   <https://github.com/aspnet/SignalR>
> - <span data-ttu-id="403e4-328">**Správce protokolu WebSocket**</span><span class="sxs-lookup"><span data-stu-id="403e4-328">**WebSocket Manager**</span></span>  
>   https://github.com/radu-matei/websocket-manager

## <a name="domain-driven-design--should-you-apply-it"></a><span data-ttu-id="403e4-329">Návrhy řízené doménou – by je použijete?</span><span class="sxs-lookup"><span data-stu-id="403e4-329">Domain-driven design – Should you apply it?</span></span>

<span data-ttu-id="403e4-330">Řízené doménou návrhu (DDD) je agilní přístup k vytváření softwaru, který zvýrazňuje zaměření na _obchodní domény_.</span><span class="sxs-lookup"><span data-stu-id="403e4-330">Domain-Driven Design (DDD) is an agile approach to building software that emphasizes focusing on the _business domain_.</span></span> <span data-ttu-id="403e4-331">Umístí velkým důrazem na komunikaci a interakci s expert(s) obchodní domény, který souviset s vývojáři fungování systému reálného světa.</span><span class="sxs-lookup"><span data-stu-id="403e4-331">It places a heavy emphasis on communication and interaction with business domain expert(s) who can relate to the developers how the real-world system works.</span></span> <span data-ttu-id="403e4-332">Například pokud sestavujete systému, který zpracovává burzovních, odborníky vaší domény může být zkušení uložených zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="403e4-332">For example, if you're building a system that handles stock trades, your domain expert might be an experienced stock broker.</span></span> <span data-ttu-id="403e4-333">DDD je navržená k řešení složitých obchodních problémů a není často vhodná pro menší, jednodušší aplikací, jako investice vysvětlující Princip fungování a modelování domény není vhodné ho.</span><span class="sxs-lookup"><span data-stu-id="403e4-333">DDD is designed to address large, complex business problems, and is often not appropriate for smaller, simpler applications, as the investment in understanding and modeling the domain is not worth it.</span></span>

<span data-ttu-id="403e4-334">Při sestavování softwaru přístupu DDD, by měl vývoj vašeho týmu (včetně netechnické zúčastněných stran a přispěvatelé) _všudypřítomná jazyk_ prostoru problém.</span><span class="sxs-lookup"><span data-stu-id="403e4-334">When building software following a DDD approach, your team (including non-technical stakeholders and contributors) should develop a _ubiquitous language_ for the problem space.</span></span> <span data-ttu-id="403e4-335">To znamená stejné terminologie by měla sloužit pro každodenní praxe koncept modelovaných, ekvivalent softwaru a všech struktur, které mohou existovat k uchování koncept (například tabulek databáze).</span><span class="sxs-lookup"><span data-stu-id="403e4-335">That is, the same terminology should be used for the real-world concept being modeled, the software equivalent, and any structures that might exist to persist the concept (for example, database tables).</span></span> <span data-ttu-id="403e4-336">Proto by měl koncepty popsané v jazyce všudypřítomná tvoří základ pro váš _doménový model_.</span><span class="sxs-lookup"><span data-stu-id="403e4-336">Thus, the concepts described in the ubiquitous language should form the basis for your _domain model_.</span></span>

<span data-ttu-id="403e4-337">Doménový model se skládá z objektů, které vzájemně spolupracují představující chování systému.</span><span class="sxs-lookup"><span data-stu-id="403e4-337">Your domain model is comprised of objects that interact with one another to represent the behavior of the system.</span></span> <span data-ttu-id="403e4-338">Tyto objekty mohou spadají do následujících kategorií:</span><span class="sxs-lookup"><span data-stu-id="403e4-338">These objects may fall into the following categories:</span></span>

- <span data-ttu-id="403e4-339">[Entity](https://deviq.com/entity/), které představují objekty s vláknem identity.</span><span class="sxs-lookup"><span data-stu-id="403e4-339">[Entities](https://deviq.com/entity/), which represent objects with a thread of identity.</span></span> <span data-ttu-id="403e4-340">Entity jsou obvykle uloženy v trvalost s klíčem, pomocí kterého může později načíst.</span><span class="sxs-lookup"><span data-stu-id="403e4-340">Entities are typically stored in persistence with a key by which they can later be retrieved.</span></span>

- <span data-ttu-id="403e4-341">[Agregace](https://deviq.com/aggregate-pattern/), které představují skupiny objektů, které by měl být trvalé jako celek.</span><span class="sxs-lookup"><span data-stu-id="403e4-341">[Aggregates](https://deviq.com/aggregate-pattern/), which represent groups of objects that should be persisted as a unit.</span></span>

- <span data-ttu-id="403e4-342">[Hodnota objekty](https://deviq.com/value-object/), které představují koncepty, které lze porovnávat na základě součtu hodnot vlastností.</span><span class="sxs-lookup"><span data-stu-id="403e4-342">[Value objects](https://deviq.com/value-object/), which represent concepts that can be compared on the basis of the sum of their property values.</span></span> <span data-ttu-id="403e4-343">Například DateRange skládající se z počáteční a koncové datum.</span><span class="sxs-lookup"><span data-stu-id="403e4-343">For example, DateRange consisting of a start and end date.</span></span>

- <span data-ttu-id="403e4-344">[Události domény](https://martinfowler.com/eaaDev/DomainEvent.html), které představují věcí děje v rámci systému, které jsou zajímavé pro ostatní části systému.</span><span class="sxs-lookup"><span data-stu-id="403e4-344">[Domain events](https://martinfowler.com/eaaDev/DomainEvent.html), which represent things happening within the system that are of interest to other parts of the system.</span></span>

<span data-ttu-id="403e4-345">Všimněte si, že by měl doménový model DDD zapouzdření složité chování v rámci modelu.</span><span class="sxs-lookup"><span data-stu-id="403e4-345">Note that a DDD domain model should encapsulate complex behavior within the model.</span></span> <span data-ttu-id="403e4-346">Entity, by neměly být zejména pouze kolekce vlastností.</span><span class="sxs-lookup"><span data-stu-id="403e4-346">Entities, in particular, should not merely be collections of properties.</span></span> <span data-ttu-id="403e4-347">Když doménový model nemá chování a představuje pouze stav systému, je označen jako [anemic modelu](https://deviq.com/anemic-model/), což je v DDD nežádoucí.</span><span class="sxs-lookup"><span data-stu-id="403e4-347">When the domain model lacks behavior and merely represents the state of the system, it is said to be an [anemic model](https://deviq.com/anemic-model/), which is undesirable in DDD.</span></span>

<span data-ttu-id="403e4-348">Kromě těchto typů modelu DDD obvykle využívá širokou škálu vzorce:</span><span class="sxs-lookup"><span data-stu-id="403e4-348">In addition to these model types, DDD typically employs a variety of patterns:</span></span>

- <span data-ttu-id="403e4-349">[Úložiště](https://deviq.com/repository-pattern/), pro abstrahovat podrobnosti trvalosti.</span><span class="sxs-lookup"><span data-stu-id="403e4-349">[Repository](https://deviq.com/repository-pattern/), for abstracting persistence details.</span></span>

- <span data-ttu-id="403e4-350">[Objekt pro vytváření](https://en.wikipedia.org/wiki/Factory_method_pattern), pro zapouzdření vytváření komplexních objektů.</span><span class="sxs-lookup"><span data-stu-id="403e4-350">[Factory](https://en.wikipedia.org/wiki/Factory_method_pattern), for encapsulating complex object creation.</span></span>

- <span data-ttu-id="403e4-351">Události domény pro oddělení závislé chování spouštět chování.</span><span class="sxs-lookup"><span data-stu-id="403e4-351">Domain events, for decoupling dependent behavior from triggering behavior.</span></span>

- <span data-ttu-id="403e4-352">[Služby](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/), pro zapouzdřující složité chování a/nebo podrobnosti implementace infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="403e4-352">[Services](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/), for encapsulating complex behavior and/or infrastructure implementation details.</span></span>

- <span data-ttu-id="403e4-353">[Příkaz](https://en.wikipedia.org/wiki/Command_pattern), pro oddělení vydávání příkazů a provádění příkazu samého.</span><span class="sxs-lookup"><span data-stu-id="403e4-353">[Command](https://en.wikipedia.org/wiki/Command_pattern), for decoupling issuing commands and executing the command itself.</span></span>

- <span data-ttu-id="403e4-354">[Specifikace](https://deviq.com/specification-pattern/), pro zapouzdření podrobností dotazu.</span><span class="sxs-lookup"><span data-stu-id="403e4-354">[Specification](https://deviq.com/specification-pattern/), for encapsulating query details.</span></span>

<span data-ttu-id="403e4-355">DDD také doporučuje používat čisté architektury, jak jsme vysvětlili výše, umožňuje volné párování zapouzdření a kód, který lze snadno ověřit pomocí testů jednotek.</span><span class="sxs-lookup"><span data-stu-id="403e4-355">DDD also recommends the use of the Clean Architecture discussed previously, allowing for loose coupling, encapsulation, and code that can easily be verified using unit tests.</span></span>

### <a name="when-should-you-apply-ddd"></a><span data-ttu-id="403e4-356">Po instalaci aktualizace DDD</span><span class="sxs-lookup"><span data-stu-id="403e4-356">When should you apply DDD</span></span>

<span data-ttu-id="403e4-357">DDD je velmi vhodná pro velké aplikace ve službě (ne technickou právě) důležité firemní složitosti.</span><span class="sxs-lookup"><span data-stu-id="403e4-357">DDD is well-suited to large applications with significant business (not just technical) complexity.</span></span> <span data-ttu-id="403e4-358">Aplikace by měla vyžadují znalost odborníky na domény.</span><span class="sxs-lookup"><span data-stu-id="403e4-358">The application should require the knowledge of domain experts.</span></span> <span data-ttu-id="403e4-359">V doménovém modelu, samostatně, představující obchodní pravidla a interakce nad rámec jednoduše ukládání a načítání aktuální stav různých záznamy z úložiště dat by měl být významné chování.</span><span class="sxs-lookup"><span data-stu-id="403e4-359">There should be significant behavior in the domain model itself, representing business rules and interactions beyond simply storing and retrieving the current state of various records from data stores.</span></span>

### <a name="when-shouldnt-you-apply-ddd"></a><span data-ttu-id="403e4-360">Pokud by neměla použijete DDD</span><span class="sxs-lookup"><span data-stu-id="403e4-360">When shouldn't you apply DDD</span></span>

<span data-ttu-id="403e4-361">DDD vyžaduje investice do modelování, architektury a komunikaci, která nemusí být jader pro menší aplikace nebo aplikace, které jsou v podstatě stačí CRUD (vytváření, čtení, aktualizace nebo odstranění).</span><span class="sxs-lookup"><span data-stu-id="403e4-361">DDD involves investments in modeling, architecture, and communication that may not be warranted for smaller applications or applications that are essentially just CRUD (create/read/update/delete).</span></span> <span data-ttu-id="403e4-362">Pokud budete chtít přístup aplikace po DDD, ale najít, že má vaše doména anemic model s žádné chování, budete muset znovu zamysleli nad váš přístup.</span><span class="sxs-lookup"><span data-stu-id="403e4-362">If you choose to approach your application following DDD, but find that your domain has an anemic model with no behavior, you may need to rethink your approach.</span></span> <span data-ttu-id="403e4-363">Vaše aplikace nemusí potřebovat DDD, nebo potřebujete pomoc, refaktoring pro zapouzdření obchodní logiku v modelu domény, nikoli databázi nebo uživatelské rozhraní aplikace.</span><span class="sxs-lookup"><span data-stu-id="403e4-363">Either your application may not need DDD, or you may need assistance refactoring your application to encapsulate business logic in the domain model, rather than in your database or user interface.</span></span>

<span data-ttu-id="403e4-364">Hybridní přístup může být pouze použití DDD v oblastech transakční či složitější aplikace, ale ne pro jednodušší CRUD nebo jen pro čtení částí aplikace.</span><span class="sxs-lookup"><span data-stu-id="403e4-364">A hybrid approach would be to only use DDD for the transactional or more complex areas of the application, but not for simpler CRUD or read-only portions of the application.</span></span> <span data-ttu-id="403e4-365">Pokud se dotazujete dat. Chcete-li zobrazit sestavu nebo vizualizaci dat pro řídicí panel, například nemusí mít omezení agregace.</span><span class="sxs-lookup"><span data-stu-id="403e4-365">For instance, you needn't have the constraints of an Aggregate if you're querying data to display a report or to visualize data for a dashboard.</span></span> <span data-ttu-id="403e4-366">Je naprosto přijatelné mít samostatné, jednodušší model čtení pro tyto požadavky.</span><span class="sxs-lookup"><span data-stu-id="403e4-366">It's perfectly acceptable to have a separate, simpler read model for such requirements.</span></span>

> ### <a name="references--domain-driven-design"></a><span data-ttu-id="403e4-367">Odkazy – návrhem řízeným doménou</span><span class="sxs-lookup"><span data-stu-id="403e4-367">References – Domain-Driven Design</span></span>
>
> - <span data-ttu-id="403e4-368">**DDD v běžném jazyce (StackOverflow odpovědí)**</span><span class="sxs-lookup"><span data-stu-id="403e4-368">**DDD in Plain English (StackOverflow Answer)**</span></span>  
>   <https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488>

## <a name="deployment"></a><span data-ttu-id="403e4-369">Nasazení</span><span class="sxs-lookup"><span data-stu-id="403e4-369">Deployment</span></span>

<span data-ttu-id="403e4-370">Se využívá řada probíhá nasazení aplikace ASP.NET Core, bez ohledu na to, kde bude hostovat několik kroků.</span><span class="sxs-lookup"><span data-stu-id="403e4-370">There are a few steps involved in the process of deploying your ASP.NET Core application, regardless of where it will be hosted.</span></span> <span data-ttu-id="403e4-371">Prvním krokem je publikovat aplikaci, která se dá dělat pomocí dotnet příkazu rozhraní příkazového řádku pro publikování.</span><span class="sxs-lookup"><span data-stu-id="403e4-371">The first step is to publish the application, which can be done using the dotnet publish CLI command.</span></span> <span data-ttu-id="403e4-372">To bude který aplikaci zkompiluje a umístěte všechny soubory potřebné ke spuštění aplikace do určené složky.</span><span class="sxs-lookup"><span data-stu-id="403e4-372">This will compile the application and place all of the files needed to run the application into a designated folder.</span></span> <span data-ttu-id="403e4-373">Při nasazení ze sady Visual Studio tento krok děláte proto pro vás automaticky.</span><span class="sxs-lookup"><span data-stu-id="403e4-373">When you deploy from Visual Studio, this step is performed for you automatically.</span></span> <span data-ttu-id="403e4-374">Publikovat složka obsahuje soubory .exe a .dll pro aplikace a jeho závislosti.</span><span class="sxs-lookup"><span data-stu-id="403e4-374">The publish folder contains .exe and .dll files for the application and its dependencies.</span></span> <span data-ttu-id="403e4-375">Samostatné aplikace bude také obsahovat verzi modulu .NET runtime.</span><span class="sxs-lookup"><span data-stu-id="403e4-375">A self-contained application will also include a version of the .NET runtime.</span></span> <span data-ttu-id="403e4-376">Aplikace ASP.NET Core bude také obsahovat konfigurační soubory, prostředky statického klienta a zobrazení MVC.</span><span class="sxs-lookup"><span data-stu-id="403e4-376">ASP.NET Core applications will also include configuration files, static client assets, and MVC views.</span></span>

<span data-ttu-id="403e4-377">Aplikace ASP.NET Core jsou konzolové aplikace, které musí být spuštěna, když na server se spustí a restartovaný, pokud dojde k chybě aplikace (nebo serveru).</span><span class="sxs-lookup"><span data-stu-id="403e4-377">ASP.NET Core applications are console applications that must be started when the server boots and restarted if the application (or server) crashes.</span></span> <span data-ttu-id="403e4-378">Správce procesu můžete použít k automatizaci tohoto procesu.</span><span class="sxs-lookup"><span data-stu-id="403e4-378">A process manager can be used to automate this process.</span></span> <span data-ttu-id="403e4-379">Nejběžnější vedoucí proces pro ASP.NET Core se server Nginx a Apache v Linuxu a služby IIS nebo službu Windows na Windows.</span><span class="sxs-lookup"><span data-stu-id="403e4-379">The most common process managers for ASP.NET Core are Nginx and Apache on Linux and IIS or Windows Service on Windows.</span></span>

<span data-ttu-id="403e4-380">Kromě správce procesu musí aplikace ASP.NET Core hostované na webovém serveru Kestrel použít reverzní proxy server.</span><span class="sxs-lookup"><span data-stu-id="403e4-380">In addition to a process manager, ASP.NET Core applications hosted in the Kestrel web server must use a reverse proxy server.</span></span> <span data-ttu-id="403e4-381">Reverzní proxy server přijímá požadavky HTTP z Internetu a předává je na Kestrel po některé předběžného zpracování.</span><span class="sxs-lookup"><span data-stu-id="403e4-381">A reverse proxy server receives HTTP requests from the internet and forwards them to Kestrel after some preliminary handling.</span></span> <span data-ttu-id="403e4-382">Reverzní proxy servery aplikace poskytuje vrstvu zabezpečení a jsou požadovány pro nasazení hraniční (vystavené pro provoz z Internetu).</span><span class="sxs-lookup"><span data-stu-id="403e4-382">Reverse proxy servers provide a layer of security for the application, and are required for edge deployments (exposed to traffic from the Internet).</span></span> <span data-ttu-id="403e4-383">Kestrel je relativně nové a dosud neposkytuje ochranu proti některým útokům.</span><span class="sxs-lookup"><span data-stu-id="403e4-383">Kestrel is relatively new and does not yet offer defenses against certain attacks.</span></span> <span data-ttu-id="403e4-384">Kestrel také nepodporuje hostování více aplikací na stejném portu, takže postupů, jako jsou hlavičky hostitele nelze použít s ním k povolení hostování více aplikací na stejném portu a IP adresu.</span><span class="sxs-lookup"><span data-stu-id="403e4-384">Kestrel also doesn't support hosting multiple applications on the same port, so techniques like host headers cannot be used with it to enable hosting multiple applications on the same port and IP address.</span></span>

![Kestrel k Internetu](./media/image7-5.png)

<span data-ttu-id="403e4-386">Obrázek 7 – 5 hostované v Kestrel za reverzní proxy server ASP.NET</span><span class="sxs-lookup"><span data-stu-id="403e4-386">Figure 7-5 ASP.NET hosted in Kestrel behind a reverse proxy server</span></span>

<span data-ttu-id="403e4-387">Jiný scénář, ve kterém může být užitečné reverzního proxy serveru je zajistit více aplikací pomocí protokolu SSL/HTTPS.</span><span class="sxs-lookup"><span data-stu-id="403e4-387">Another scenario in which a reverse proxy can be helpful is to secure multiple applications using SSL/HTTPS.</span></span> <span data-ttu-id="403e4-388">V takovém případě by pouze reverzní proxy server musí být nakonfigurovaný protokol SSL.</span><span class="sxs-lookup"><span data-stu-id="403e4-388">In this case, only the reverse proxy would need to have SSL configured.</span></span> <span data-ttu-id="403e4-389">Komunikace mezi serverem pro reverzní proxy server a Kestrel se mohla provést přes protokol HTTP, jak je znázorněno v obrázek 7 až 6.</span><span class="sxs-lookup"><span data-stu-id="403e4-389">Communication between the reverse proxy server and Kestrel could take place over HTTP, as shown in Figure 7-6.</span></span>

![](./media/image7-6.png)

<span data-ttu-id="403e4-390">Obrázek 7 – 6 ASP.NET hostovaných za službou serveru protokol HTTPS zabezpečená reverzního proxy serveru</span><span class="sxs-lookup"><span data-stu-id="403e4-390">Figure 7-6 ASP.NET hosted behind an HTTPS-secured reverse proxy server</span></span>

<span data-ttu-id="403e4-391">Stále oblíbených přístupem je hostovat aplikace ASP.NET Core v kontejneru Dockeru, které pak můžete hostované místně nebo nasadit do Azure pro hostování založené na cloudu.</span><span class="sxs-lookup"><span data-stu-id="403e4-391">An increasingly popular approach is to host your ASP.NET Core application in a Docker container, which then can be hosted locally or deployed to Azure for cloud-based hosting.</span></span> <span data-ttu-id="403e4-392">Kontejner Dockeru můžou obsahovat kód vaší aplikace běžící na Kestrel a nasadí se za reverzní proxy server, jak je znázorněno výše.</span><span class="sxs-lookup"><span data-stu-id="403e4-392">The Docker container could contain your application code, running on Kestrel, and would be deployed behind a reverse proxy server, as shown above.</span></span>

<span data-ttu-id="403e4-393">Pokud máte aplikace na Azure, slouží k poskytování několik služeb Microsoft Azure Application Gateway jako vyhrazené virtuální zařízení.</span><span class="sxs-lookup"><span data-stu-id="403e4-393">If you're hosting your application on Azure, you can use Microsoft Azure Application Gateway as a dedicated virtual appliance to provide several services.</span></span> <span data-ttu-id="403e4-394">Kromě funguje jako reverzní proxy server pro jednotlivé aplikace, služba Application Gateway nabízí také následující funkce:</span><span class="sxs-lookup"><span data-stu-id="403e4-394">In addition to acting as a reverse proxy for individual applications, Application Gateway can also offer the following features:</span></span>

- <span data-ttu-id="403e4-395">Vyrovnávání zatížení HTTP</span><span class="sxs-lookup"><span data-stu-id="403e4-395">HTTP load balancing</span></span>

- <span data-ttu-id="403e4-396">Přesměrování zpracování SSL (protokol SSL jenom pro Internet)</span><span class="sxs-lookup"><span data-stu-id="403e4-396">SSL offload (SSL only to Internet)</span></span>

- <span data-ttu-id="403e4-397">Kompletního protokolu SSL</span><span class="sxs-lookup"><span data-stu-id="403e4-397">End to End SSL</span></span>

- <span data-ttu-id="403e4-398">Směrování více webů (konsolidovat až 20 webů na jedinou službou Application Gateway)</span><span class="sxs-lookup"><span data-stu-id="403e4-398">Multi-site routing (consolidate up to 20 sites on a single Application Gateway)</span></span>

- <span data-ttu-id="403e4-399">Firewall webových aplikací</span><span class="sxs-lookup"><span data-stu-id="403e4-399">Web application firewall</span></span>

- <span data-ttu-id="403e4-400">Podpora protokolu Websocket</span><span class="sxs-lookup"><span data-stu-id="403e4-400">Websocket support</span></span>

- <span data-ttu-id="403e4-401">Pokročilou diagnostiku</span><span class="sxs-lookup"><span data-stu-id="403e4-401">Advanced diagnostics</span></span>

<span data-ttu-id="403e4-402">_Další informace o možnostech nasazení Azure v [kapitoly 10](development-process-for-azure.md)._</span><span class="sxs-lookup"><span data-stu-id="403e4-402">_Learn more about Azure deployment options in [Chapter 10](development-process-for-azure.md)._</span></span>

> ### <a name="references--deployment"></a><span data-ttu-id="403e4-403">Odkazy – nasazení</span><span class="sxs-lookup"><span data-stu-id="403e4-403">References – Deployment</span></span>
>
> - <span data-ttu-id="403e4-404">**Přehled nasazení a hostování**</span><span class="sxs-lookup"><span data-stu-id="403e4-404">**Hosting and Deployment Overview**</span></span>  
>   <https://docs.microsoft.com/aspnet/core/publishing/>
> - <span data-ttu-id="403e4-405">**Kdy použít Kestrel pomocí reverzního proxy serveru**</span><span class="sxs-lookup"><span data-stu-id="403e4-405">**When to use Kestrel with a reverse proxy**</span></span>  
>   <https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy>
> - <span data-ttu-id="403e4-406">**Hostování aplikací ASP.NET Core v Dockeru**</span><span class="sxs-lookup"><span data-stu-id="403e4-406">**Host ASP.NET Core apps in Docker**</span></span>  
>   <https://docs.microsoft.com/aspnet/core/publishing/docker>
> - <span data-ttu-id="403e4-407">**Představujeme Azure Application Gateway**</span><span class="sxs-lookup"><span data-stu-id="403e4-407">**Introducing Azure Application Gateway**</span></span>  
>   <https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction>

>[!div class="step-by-step"]
><span data-ttu-id="403e4-408">[Předchozí](common-client-side-web-technologies.md)
>[další](work-with-data-in-asp-net-core-apps.md)</span><span class="sxs-lookup"><span data-stu-id="403e4-408">[Previous](common-client-side-web-technologies.md)
[Next](work-with-data-in-asp-net-core-apps.md)</span></span>