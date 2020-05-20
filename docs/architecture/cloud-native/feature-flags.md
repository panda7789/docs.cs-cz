---
title: Příznaky funkcí
description: Implementace příznaků funkcí v cloudových nativních aplikacích s využitím konfigurace aplikací Azure
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 607bd14a415a25b382f550e697542cf749a21772
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614068"
---
# <a name="feature-flags"></a><span data-ttu-id="106a7-103">Příznaky funkcí</span><span class="sxs-lookup"><span data-stu-id="106a7-103">Feature flags</span></span>

<span data-ttu-id="106a7-104">V kapitole 1 jsme tvrdili, že nativní Cloud je mnohem o rychlosti a flexibilitě.</span><span class="sxs-lookup"><span data-stu-id="106a7-104">In chapter 1, we affirmed that cloud native is much about speed and agility.</span></span> <span data-ttu-id="106a7-105">Uživatelé očekávají rychlou odezvu, inovativní funkce a nulové výpadky.</span><span class="sxs-lookup"><span data-stu-id="106a7-105">Users expect rapid responsiveness, innovative features, and zero downtime.</span></span> <span data-ttu-id="106a7-106">`Feature flags`jsou moderní techniky nasazení, které pomáhají zvýšit flexibilitu pro aplikace nativní pro Cloud.</span><span class="sxs-lookup"><span data-stu-id="106a7-106">`Feature flags` are a modern deployment technique that helps increase agility for cloud-native applications.</span></span> <span data-ttu-id="106a7-107">Umožňují nasazovat nové funkce do produkčního prostředí, ale omezují jejich dostupnost.</span><span class="sxs-lookup"><span data-stu-id="106a7-107">They enable you to deploy new features into a production environment, but restrict their availability.</span></span> <span data-ttu-id="106a7-108">Pomocí rychlého pohybu přepínače můžete aktivovat novou funkci pro konkrétní uživatele bez restartování aplikace nebo nasazení nového kódu.</span><span class="sxs-lookup"><span data-stu-id="106a7-108">With the flick of a switch, you can activate a new feature for specific users without restarting the app or deploying new code.</span></span> <span data-ttu-id="106a7-109">Oddělují vydání nových funkcí od jejich nasazení kódu.</span><span class="sxs-lookup"><span data-stu-id="106a7-109">They separate the release of new features from their code deployment.</span></span>

<span data-ttu-id="106a7-110">Příznaky funkcí jsou postavené na podmíněné logice, které ovládají viditelnost funkcí pro uživatele za běhu.</span><span class="sxs-lookup"><span data-stu-id="106a7-110">Feature flags are built upon conditional logic that control visibility of functionality for users at runtime.</span></span> <span data-ttu-id="106a7-111">V moderních cloudových nativních systémech je běžné nasadit nové funkce do produkčního prostředí, ale testovat je s omezeným cílovou skupinou.</span><span class="sxs-lookup"><span data-stu-id="106a7-111">In modern cloud-native systems, it's common to deploy new features into production early, but test them with a limited audience.</span></span> <span data-ttu-id="106a7-112">Jak se zvyšuje spolehlivost, funkce se dá přírůstkově vymezit širším cílovým skupinám.</span><span class="sxs-lookup"><span data-stu-id="106a7-112">As confidence increases, the feature can be incrementally rolled out to wider audiences.</span></span>

<span data-ttu-id="106a7-113">K dalším případům použití pro příznaky funkcí patří:</span><span class="sxs-lookup"><span data-stu-id="106a7-113">Other use cases for feature flags include:</span></span>

- <span data-ttu-id="106a7-114">Omezte prémiové funkce na konkrétní skupiny zákazníků ochotné uhradit vyšší poplatky za předplatné.</span><span class="sxs-lookup"><span data-stu-id="106a7-114">Restrict premium functionality to specific customer groups willing to pay higher subscription fees.</span></span>
- <span data-ttu-id="106a7-115">Umožňuje stabilizovat systém tím, že se rychle deaktivuje funkce problému, což vyloučí rizika vrácení zpět nebo okamžité opravy hotfix.</span><span class="sxs-lookup"><span data-stu-id="106a7-115">Stabilize a system by quickly deactivating a problem feature, avoiding the risks of a rollback or immediate hotfix.</span></span>
- <span data-ttu-id="106a7-116">Zakážete volitelnou funkci s vysokou spotřebou prostředků během období špičky využití.</span><span class="sxs-lookup"><span data-stu-id="106a7-116">Disable an optional feature with high resource consumption during peak usage periods.</span></span>
- <span data-ttu-id="106a7-117">Pro účely `experimental feature releases` ověření možnosti proveditelnost a oblíbenosti můžete provádět malé uživatelské segmenty.</span><span class="sxs-lookup"><span data-stu-id="106a7-117">Conduct `experimental feature releases` to small user segments to validate feasibility and popularity.</span></span>

<span data-ttu-id="106a7-118">Příznaky funkcí také povýší `trunk-based` vývoj.</span><span class="sxs-lookup"><span data-stu-id="106a7-118">Feature flags also promote `trunk-based` development.</span></span> <span data-ttu-id="106a7-119">Jedná se o model větvení správy zdrojového kódu, ve kterém vývojáři spolupracují na funkcích v jedné větvi.</span><span class="sxs-lookup"><span data-stu-id="106a7-119">It's a source-control branching model where developers collaborate on features in a single branch.</span></span> <span data-ttu-id="106a7-120">Tento přístup minimalizuje riziko a složitost slučování velkého počtu dlouhotrvajících větví funkcí.</span><span class="sxs-lookup"><span data-stu-id="106a7-120">The approach minimizes the risk and complexity of merging large numbers of long-running feature branches.</span></span> <span data-ttu-id="106a7-121">Funkce nejsou k dispozici, dokud nejsou aktivovány.</span><span class="sxs-lookup"><span data-stu-id="106a7-121">Features are unavailable until activated.</span></span>

## <a name="implementing-feature-flags"></a><span data-ttu-id="106a7-122">Implementace příznaků funkcí</span><span class="sxs-lookup"><span data-stu-id="106a7-122">Implementing feature flags</span></span>

<span data-ttu-id="106a7-123">Ve svém jádru je příznak funkce odkazem na jednoduchý `decision object` .</span><span class="sxs-lookup"><span data-stu-id="106a7-123">At its core, a feature flag is a reference to a simple `decision object`.</span></span> <span data-ttu-id="106a7-124">Vrátí logický stav `on` nebo `off` .</span><span class="sxs-lookup"><span data-stu-id="106a7-124">It returns a Boolean state of `on` or `off`.</span></span> <span data-ttu-id="106a7-125">Příznak obvykle zabalí blok kódu, který zapouzdřuje schopnost funkce.</span><span class="sxs-lookup"><span data-stu-id="106a7-125">The flag typically wraps a block of code that encapsulates a feature capability.</span></span> <span data-ttu-id="106a7-126">Stav příznaku určuje, zda se pro daného uživatele spustí blok kódu.</span><span class="sxs-lookup"><span data-stu-id="106a7-126">The state of the flag determines whether that code block executes for a given user.</span></span> <span data-ttu-id="106a7-127">Obrázek 10-11 ukazuje implementaci.</span><span class="sxs-lookup"><span data-stu-id="106a7-127">Figure 10-11 shows the implementation.</span></span>

```c#
if (featureFlag) {
    // Run this code block if the featureFlag value is true
} else {
    // Run this code block if the featureFlag value is false
}
```

<span data-ttu-id="106a7-128">**Obrázek 10-11** – implementace příznaku jednoduché funkce</span><span class="sxs-lookup"><span data-stu-id="106a7-128">**Figure 10-11** - Simple feature flag implementation.</span></span>

<span data-ttu-id="106a7-129">Všimněte si, jak tento přístup odděluje rozhodovací logiku od kódu funkce.</span><span class="sxs-lookup"><span data-stu-id="106a7-129">Note how this approach separates the decision logic from the feature code.</span></span>

<span data-ttu-id="106a7-130">V kapitole 1 jsme probrali `Twelve-Factor App` .</span><span class="sxs-lookup"><span data-stu-id="106a7-130">In chapter 1, we discussed the `Twelve-Factor App`.</span></span> <span data-ttu-id="106a7-131">Návod doporučuje zachovat nastavení konfigurace externě ze spustitelného kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="106a7-131">The guidance recommended keeping configuration settings external from application executable code.</span></span> <span data-ttu-id="106a7-132">V případě potřeby je možné číst nastavení z externího zdroje.</span><span class="sxs-lookup"><span data-stu-id="106a7-132">When needed, settings can be read in from the external source.</span></span> <span data-ttu-id="106a7-133">Hodnoty konfigurace příznaku funkce by měly být také nezávislé na základu kódu.</span><span class="sxs-lookup"><span data-stu-id="106a7-133">Feature flag configuration values should also be independent from their codebase.</span></span> <span data-ttu-id="106a7-134">Konfigurací příznaku přenesení v samostatném úložišti můžete změnit stav příznaku bez změny a nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="106a7-134">By externalizing flag configuration in a separate repository, you can change flag state without modifying and redeploying the application.</span></span>

<span data-ttu-id="106a7-135">[Azure App Configuration](https://docs.microsoft.com/azure/azure-app-configuration/overview) poskytuje centralizované úložiště pro příznaky funkcí.</span><span class="sxs-lookup"><span data-stu-id="106a7-135">[Azure App Configuration](https://docs.microsoft.com/azure/azure-app-configuration/overview) provides a centralized repository for feature flags.</span></span> <span data-ttu-id="106a7-136">Pomocí této funkce můžete definovat různé druhy příznaků funkcí a rychle a bez obav manipulovat se svými stavy.</span><span class="sxs-lookup"><span data-stu-id="106a7-136">With it, you define different kinds of feature flags and manipulate their states quickly and confidently.</span></span> <span data-ttu-id="106a7-137">Přidáním klientských knihoven konfigurace aplikace do aplikace povolíte funkci příznaku funkcí.</span><span class="sxs-lookup"><span data-stu-id="106a7-137">You add the App Configuration client libraries to your application to enable feature flag functionality.</span></span> <span data-ttu-id="106a7-138">Podporovány jsou různé programovací jazykové prostředí.</span><span class="sxs-lookup"><span data-stu-id="106a7-138">Various programming language frameworks are supported.</span></span>

<span data-ttu-id="106a7-139">Příznaky funkcí lze snadno implementovat ve [službě ASP.NET Core](https://docs.microsoft.com/azure/azure-app-configuration/use-feature-flags-dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="106a7-139">Feature flags can be easily implemented in an [ASP.NET Core service](https://docs.microsoft.com/azure/azure-app-configuration/use-feature-flags-dotnet-core).</span></span> <span data-ttu-id="106a7-140">Když nainstalujete knihovny pro správu funkcí .NET a poskytovatele konfigurace aplikace, umožníte deklarativní Přidání příznaků funkcí do kódu.</span><span class="sxs-lookup"><span data-stu-id="106a7-140">Installing the .NET Feature Management libraries and App Configuration provider enable you to declaratively add feature flags to your code.</span></span> <span data-ttu-id="106a7-141">Povolují `FeatureGate` atributy, takže nemusíte vytvářet příkazy if v rámci vašeho základu kódu ručně.</span><span class="sxs-lookup"><span data-stu-id="106a7-141">They enable `FeatureGate` attributes so that you don't have to manually write if statements across your codebase.</span></span>

<span data-ttu-id="106a7-142">Po nakonfigurování ve vaší spouštěcí třídě můžete přidat funkce příznaků funkcí na úrovni kontroleru, akce nebo middleware.</span><span class="sxs-lookup"><span data-stu-id="106a7-142">Once configured in your Startup class, you can add feature flag functionality at the controller, action, or middleware level.</span></span> <span data-ttu-id="106a7-143">Obrázek 10-12 představuje implementaci kontroléru a akce:</span><span class="sxs-lookup"><span data-stu-id="106a7-143">Figure 10-12 presents controller and action implementation:</span></span>

```c#
[FeatureGate(MyFeatureFlags.FeatureA)]
public class ProductController : Controller
{
    ...
}
```

```c#
[FeatureGate(MyFeatureFlags.FeatureA)]
public IActionResult UpdateProductStatus()
{
    return ObjectResult(ProductDto);
}
```

<span data-ttu-id="106a7-144">**Obrázek 10-12** – implementace příznaků funkcí v kontroleru a akci.</span><span class="sxs-lookup"><span data-stu-id="106a7-144">**Figure 10-12** - Feature flag implementation in a controller and action.</span></span>

<span data-ttu-id="106a7-145">Pokud je příznak funkce zakázán, bude uživatel dostávat stavový kód 404 (Nenalezeno) bez těla odpovědi.</span><span class="sxs-lookup"><span data-stu-id="106a7-145">If a feature flag is disabled, the user will receive a 404 (Not Found) status code with no response body.</span></span>

<span data-ttu-id="106a7-146">Příznaky funkcí lze také vložit přímo do tříd jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="106a7-146">Feature flags can also be injected directly into C# classes.</span></span> <span data-ttu-id="106a7-147">Obrázek 10-13 ukazuje vkládání příznaků funkcí:</span><span class="sxs-lookup"><span data-stu-id="106a7-147">Figure 10-13 shows feature flag injection:</span></span>

```c#
public class ProductController : Controller
{
    private readonly IFeatureManager _featureManager;

    public ProductController(IFeatureManager featureManager)
    {
        _featureManager = featureManager;
    }
}
```

<span data-ttu-id="106a7-148">**Obrázek 10-13** – příznak funkce pro vkládání do třídy.</span><span class="sxs-lookup"><span data-stu-id="106a7-148">**Figure 10-13** - Feature flag injection into a class.</span></span>

<span data-ttu-id="106a7-149">Knihovny správy funkcí spravují životní cyklus příznaků funkcí na pozadí.</span><span class="sxs-lookup"><span data-stu-id="106a7-149">The Feature Management libraries manage the feature flag lifecycle behind the scenes.</span></span> <span data-ttu-id="106a7-150">Například pro minimalizaci vysokého počtu volání do úložiště konfigurace jsou po určitou dobu v mezipaměti knihoven označeny stavy.</span><span class="sxs-lookup"><span data-stu-id="106a7-150">For example, to minimize high numbers of calls to the configuration store, the libraries cache flag states for a specified duration.</span></span> <span data-ttu-id="106a7-151">Můžou zaručit neměnnosti stavů příznaků během volání žádosti.</span><span class="sxs-lookup"><span data-stu-id="106a7-151">They can guarantee the immutability of flag states during a request call.</span></span> <span data-ttu-id="106a7-152">Nabízejí také `Point-in-time snapshot` .</span><span class="sxs-lookup"><span data-stu-id="106a7-152">They also offer a `Point-in-time snapshot`.</span></span> <span data-ttu-id="106a7-153">Historii jakékoli hodnoty klíč-hodnota můžete kdykoli znovu sestavit a zadat její dřívější hodnotu během posledních sedmi dnů.</span><span class="sxs-lookup"><span data-stu-id="106a7-153">You can reconstruct the history of any key-value and provide its past value at any moment within the previous seven days.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="106a7-154">[Předchozí](devops.md) 
> [Další](infrastructure-as-code.md)</span><span class="sxs-lookup"><span data-stu-id="106a7-154">[Previous](devops.md)
[Next](infrastructure-as-code.md)</span></span>
