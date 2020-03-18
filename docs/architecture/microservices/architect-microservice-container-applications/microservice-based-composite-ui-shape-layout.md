---
title: Vytváření složeného ui na základě mikroslužeb
description: Architektura mikroslužeb není pouze pro back-end. Získejte náhled na jeho použití v přední části.
ms.date: 09/20/2018
ms.openlocfilehash: 1861d3bb6e5d4a0226aa8f3f72a2e0d3e83be56f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72275738"
---
# <a name="creating-composite-ui-based-on-microservices"></a><span data-ttu-id="acbdd-104">Vytváření složeného ui na základě mikroslužeb</span><span class="sxs-lookup"><span data-stu-id="acbdd-104">Creating composite UI based on microservices</span></span>

<span data-ttu-id="acbdd-105">Architektura mikroslužeb často začíná zpracování dat na straně serveru a logiky, ale v mnoha případech ui je stále zpracována jako monolit.</span><span class="sxs-lookup"><span data-stu-id="acbdd-105">Microservices architecture often starts with the server-side handling data and logic, but, in many cases, the UI is still handled as a monolith.</span></span> <span data-ttu-id="acbdd-106">Pokročilejší přístup, nazývaný mikro [front-endy](https://martinfowler.com/articles/micro-frontends.html), je však navrhnout vaše aplikace ui na základě mikroslužeb také.</span><span class="sxs-lookup"><span data-stu-id="acbdd-106">However, a more advanced approach, called [micro frontends](https://martinfowler.com/articles/micro-frontends.html), is to design your application UI based on microservices as well.</span></span> <span data-ttu-id="acbdd-107">To znamená, že s složené ui vyrobené mikroslužeb, namísto mikroslužeb na serveru a pouze monolitické klientské aplikace náročné mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="acbdd-107">That means having a composite UI produced by the microservices, instead of having microservices on the server and just a monolithic client app consuming the microservices.</span></span> <span data-ttu-id="acbdd-108">S tímto přístupem mikroslužeb, které vytvoříte může být kompletní s logikou a vizuální reprezentace.</span><span class="sxs-lookup"><span data-stu-id="acbdd-108">With this approach, the microservices you build can be complete with both logic and visual representation.</span></span>

<span data-ttu-id="acbdd-109">Obrázek 4-20 ukazuje jednodušší přístup právě náročné mikroslužeb z monolitické klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="acbdd-109">Figure 4-20 shows the simpler approach of just consuming microservices from a monolithic client application.</span></span> <span data-ttu-id="acbdd-110">Samozřejmě, můžete mít ASP.NET Služby MVC mezi výrobou HTML a JavaScript.</span><span class="sxs-lookup"><span data-stu-id="acbdd-110">Of course, you could have an ASP.NET MVC service in between producing the HTML and JavaScript.</span></span> <span data-ttu-id="acbdd-111">Obrázek je zjednodušení, které zdůrazňuje, že máte jeden (monolitické) klientské ui náročné mikroslužeb, které se zaměřují pouze na logiku a data, a nikoli na obrazec ui (HTML a JavaScript).</span><span class="sxs-lookup"><span data-stu-id="acbdd-111">The figure is a simplification that highlights that you have a single (monolithic) client UI consuming the microservices, which just focus on logic and data and not on the UI shape (HTML and JavaScript).</span></span>

![Diagram monolitické aplikace ui připojení k mikroslužbám.](./media/microservice-based-composite-ui-shape-layout/monolith-ui-consume-microservices.png)

<span data-ttu-id="acbdd-113">**Obrázek 4-20**.</span><span class="sxs-lookup"><span data-stu-id="acbdd-113">**Figure 4-20**.</span></span> <span data-ttu-id="acbdd-114">Monolitické aplikace ui náročné back-endové mikroslužby</span><span class="sxs-lookup"><span data-stu-id="acbdd-114">A monolithic UI application consuming back-end microservices</span></span>

<span data-ttu-id="acbdd-115">Naproti tomu složené uzpložené umělá vi je přesně generována a skládá mikroslužeb sami.</span><span class="sxs-lookup"><span data-stu-id="acbdd-115">In contrast, a composite UI is precisely generated and composed by the microservices themselves.</span></span> <span data-ttu-id="acbdd-116">Některé mikroslužeb řídit vizuální tvar konkrétní oblasti ui.</span><span class="sxs-lookup"><span data-stu-id="acbdd-116">Some of the microservices drive the visual shape of specific areas of the UI.</span></span> <span data-ttu-id="acbdd-117">Klíčovým rozdílem je, že máte komponenty uživatelského prostředí klienta (například třídy TypeScript) založené na šablonách a model zobrazení ui pro tyto šablony pro tyto šablony pochází z každé mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="acbdd-117">The key difference is that you have client UI components (TypeScript classes, for example) based on templates, and the data-shaping-UI ViewModel for those templates comes from each microservice.</span></span>

<span data-ttu-id="acbdd-118">Při spuštění klientské aplikace se každá komponenta klientského ui (například třídy jazyka TypeScript) zaregistruje pomocí mikroslužby infrastruktury, která je schopna poskytnout ViewModels pro daný scénář.</span><span class="sxs-lookup"><span data-stu-id="acbdd-118">At client application start-up time, each of the client UI components (TypeScript classes, for example) registers itself with an infrastructure microservice capable of providing ViewModels for a given scenario.</span></span> <span data-ttu-id="acbdd-119">Pokud mikroslužba změní tvar, změní se také ui.</span><span class="sxs-lookup"><span data-stu-id="acbdd-119">If the microservice changes the shape, the UI changes also.</span></span>

<span data-ttu-id="acbdd-120">Obrázek 4-21 ukazuje verzi tohoto přístupu složené houževnatého.</span><span class="sxs-lookup"><span data-stu-id="acbdd-120">Figure 4-21 shows a version of this composite UI approach.</span></span> <span data-ttu-id="acbdd-121">To je zjednodušeno, protože může mít jiné mikroslužby, které agregují granulované části, které jsou založeny na různých technikách.</span><span class="sxs-lookup"><span data-stu-id="acbdd-121">This is simplified because you might have other microservices that are aggregating granular parts that are based on different techniques.</span></span> <span data-ttu-id="acbdd-122">Záleží na tom, zda vytváříte tradiční webový přístup (ASP.NET MVC) nebo SPA (jednostránková aplikace).</span><span class="sxs-lookup"><span data-stu-id="acbdd-122">It depends on whether you're building a traditional web approach (ASP.NET MVC) or an SPA (Single Page Application).</span></span>

![Diagram složeného ui tvořeného mnoha modely zobrazení.](./media/microservice-based-composite-ui-shape-layout/microservice-generate-composite-ui.png)

<span data-ttu-id="acbdd-124">**Obrázek 4-21**.</span><span class="sxs-lookup"><span data-stu-id="acbdd-124">**Figure 4-21**.</span></span> <span data-ttu-id="acbdd-125">Příklad složené aplikace unesprávné back-endovými mikroslužbami</span><span class="sxs-lookup"><span data-stu-id="acbdd-125">Example of a composite UI application shaped by back-end microservices</span></span>

<span data-ttu-id="acbdd-126">Každá z těchto mikroslužeb složení ui by být podobné malé brány rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="acbdd-126">Each of those UI composition microservices would be similar to a small API Gateway.</span></span> <span data-ttu-id="acbdd-127">Ale v tomto případě je každý z nich zodpovědný za malou oblast ui.</span><span class="sxs-lookup"><span data-stu-id="acbdd-127">But in this case, each one is responsible for a small UI area.</span></span>

<span data-ttu-id="acbdd-128">Přístup kombinovaného ui, který je řízen mikroslužeb může být náročnější nebo méně, v závislosti na tom, jaké technologie ui, které používáte.</span><span class="sxs-lookup"><span data-stu-id="acbdd-128">A composite UI approach that's driven by microservices can be more challenging or less so, depending on what UI technologies you're using.</span></span> <span data-ttu-id="acbdd-129">Například nebudete používat stejné techniky pro vytváření tradiční webové aplikace, které používáte pro vytváření SPA nebo pro nativní mobilní aplikace (jako při vývoji aplikací Xamarin, což může být pro tento přístup náročnější).</span><span class="sxs-lookup"><span data-stu-id="acbdd-129">For instance, you won't use the same techniques for building a traditional web application that you use for building an SPA or for native mobile app (as when developing Xamarin apps, which can be more challenging for this approach).</span></span>

<span data-ttu-id="acbdd-130">Ukázková aplikace [eShopOnContainers](https://aka.ms/MicroservicesArchitecture) používá monolitický přístup ui z několika důvodů.</span><span class="sxs-lookup"><span data-stu-id="acbdd-130">The [eShopOnContainers](https://aka.ms/MicroservicesArchitecture) sample application uses the monolithic UI approach for multiple reasons.</span></span> <span data-ttu-id="acbdd-131">Nejprve je úvod do mikroslužeb a kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="acbdd-131">First, it's an introduction to microservices and containers.</span></span> <span data-ttu-id="acbdd-132">Složené ui je pokročilejší, ale také vyžaduje další složitost při navrhování a vývoji uj.</span><span class="sxs-lookup"><span data-stu-id="acbdd-132">A composite UI is more advanced but also requires further complexity when designing and developing the UI.</span></span> <span data-ttu-id="acbdd-133">Za druhé, eShopOnContainers také poskytuje nativní mobilní aplikace založená na Xamarin, což by bylo složitější na straně klienta C.\#</span><span class="sxs-lookup"><span data-stu-id="acbdd-133">Second, eShopOnContainers also provides a native mobile app based on Xamarin, which would make it more complex on the client C\# side.</span></span>

<span data-ttu-id="acbdd-134">Doporučujeme však použít následující odkazy, abyste se dozvěděli další informace o složeném uzpořeného ui na základě mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="acbdd-134">However, we encourage you to use the following references to learn more about composite UI based on microservices.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="acbdd-135">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="acbdd-135">Additional resources</span></span>

- <span data-ttu-id="acbdd-136">**Micro Frontends (Martin Fowler blog)**</span><span class="sxs-lookup"><span data-stu-id="acbdd-136">**Micro Frontends (Martin Fowler's blog)**</span></span>  
  <https://martinfowler.com/articles/micro-frontends.html>
  
- <span data-ttu-id="acbdd-137">**Micro Frontends (Michael Geers stránky)**</span><span class="sxs-lookup"><span data-stu-id="acbdd-137">**Micro Frontends (Michael Geers site)**</span></span>  
  <https://micro-frontends.org/>
  
- <span data-ttu-id="acbdd-138">**Kompozitní ui pomocí ASP.NET (Particular's Workshop)**</span><span class="sxs-lookup"><span data-stu-id="acbdd-138">**Composite UI using ASP.NET (Particular's Workshop)**</span></span>  
  <https://github.com/Particular/Workshop/tree/master/demos/asp-net-core>

- <span data-ttu-id="acbdd-139">**Ruben Oostinga. Monolitický frontend v architektuře mikroslužeb**</span><span class="sxs-lookup"><span data-stu-id="acbdd-139">**Ruben Oostinga. The Monolithic Frontend in the Microservices Architecture**</span></span>  
  <https://xebia.com/blog/the-monolithic-frontend-in-the-microservices-architecture/>

- <span data-ttu-id="acbdd-140">**Mauro Servienti. Tajemství lepší složení ui**</span><span class="sxs-lookup"><span data-stu-id="acbdd-140">**Mauro Servienti. The secret of better UI composition**</span></span>  
  <https://particular.net/blog/secret-of-better-ui-composition>

- <span data-ttu-id="acbdd-141">**Viktor Farcic. Zahrnutí webových komponent front-endu do mikroslužeb**</span><span class="sxs-lookup"><span data-stu-id="acbdd-141">**Viktor Farcic. Including Front-End Web Components Into Microservices**</span></span>  
  <https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/>

- <span data-ttu-id="acbdd-142">**Správa front-endu v architektuře mikroslužeb**</span><span class="sxs-lookup"><span data-stu-id="acbdd-142">**Managing Frontend in the Microservices Architecture**</span></span>  
  <https://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html>

>[!div class="step-by-step"]
><span data-ttu-id="acbdd-143">[Předchozí](microservices-addressability-service-registry.md)
>[další](resilient-high-availability-microservices.md)</span><span class="sxs-lookup"><span data-stu-id="acbdd-143">[Previous](microservices-addressability-service-registry.md)
[Next](resilient-high-availability-microservices.md)</span></span>
