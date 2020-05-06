---
title: Algoritmus načítání satelitních sestavení – .NET Core
description: Popis podrobností algoritmu satelitního načítání sestavení v .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 17f29a9aca79019daa91736e586bf1b6b753a9ec
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859527"
---
# <a name="satellite-assembly-loading-algorithm"></a><span data-ttu-id="6019c-103">Algoritmus načítání satelitních sestavení</span><span class="sxs-lookup"><span data-stu-id="6019c-103">Satellite assembly loading algorithm</span></span>

<span data-ttu-id="6019c-104">Satelitní sestavení se používají k ukládání lokalizovaných prostředků přizpůsobených pro jazyk a jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="6019c-104">Satellite assemblies are used to store localized resources customized for language and culture.</span></span>

<span data-ttu-id="6019c-105">Satelitní sestavení používají jiný algoritmus načítání než obecná spravovaná sestavení.</span><span class="sxs-lookup"><span data-stu-id="6019c-105">Satellite assemblies use a different loading algorithm than general managed assemblies.</span></span>

## <a name="when-are-satellite-assemblies-loaded"></a><span data-ttu-id="6019c-106">Kdy jsou satelitní sestavení načtena?</span><span class="sxs-lookup"><span data-stu-id="6019c-106">When are satellite assemblies loaded?</span></span>

<span data-ttu-id="6019c-107">Satelitní sestavení jsou načtena při načítání lokalizovaného prostředku.</span><span class="sxs-lookup"><span data-stu-id="6019c-107">Satellite assemblies are loaded when loading a localized resource.</span></span>

<span data-ttu-id="6019c-108">Základní rozhraní API pro načtení lokalizovaných prostředků je <xref:System.Resources.ResourceManager?displayProperty=fullName> třída.</span><span class="sxs-lookup"><span data-stu-id="6019c-108">The basic API to load localized resources is the <xref:System.Resources.ResourceManager?displayProperty=fullName> class.</span></span> <span data-ttu-id="6019c-109">Nakonec <xref:System.Resources.ResourceManager> třída zavolá <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> metodu pro každý z nich <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6019c-109">Ultimately the <xref:System.Resources.ResourceManager> class will call the <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> method for each <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="6019c-110">Rozhraní API vyšší úrovně můžou mít abstraktní rozhraní API nízké úrovně.</span><span class="sxs-lookup"><span data-stu-id="6019c-110">Higher-level APIs may abstract the low-level API.</span></span>

## <a name="algorithm"></a><span data-ttu-id="6019c-111">Algoritmus</span><span class="sxs-lookup"><span data-stu-id="6019c-111">Algorithm</span></span>

<span data-ttu-id="6019c-112">Záložní proces prostředku .NET Core zahrnuje následující kroky:</span><span class="sxs-lookup"><span data-stu-id="6019c-112">The .NET Core resource fallback process involves the following steps:</span></span>

1. <span data-ttu-id="6019c-113">`active` <xref:System.Runtime.Loader.AssemblyLoadContext> Určete instanci.</span><span class="sxs-lookup"><span data-stu-id="6019c-113">Determine the `active` <xref:System.Runtime.Loader.AssemblyLoadContext> instance.</span></span> <span data-ttu-id="6019c-114">Ve všech případech je `active` instancí spouštěným sestavením. <xref:System.Runtime.Loader.AssemblyLoadContext></span><span class="sxs-lookup"><span data-stu-id="6019c-114">In all cases, the `active` instance is the executing assembly's <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span>

2. <span data-ttu-id="6019c-115">`active` Instance se pokusí načíst satelitní sestavení pro požadovanou jazykovou verzi v pořadí podle priority podle:</span><span class="sxs-lookup"><span data-stu-id="6019c-115">The `active` instance attempts to load a satellite assembly for the requested culture in priority order by:</span></span>
    - <span data-ttu-id="6019c-116">Kontroluje se její mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="6019c-116">Checking its cache.</span></span>
    - <span data-ttu-id="6019c-117">Kontrola adresáře aktuálně spuštěného sestavení pro podadresář, který odpovídá požadovanému <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> (například `es-MX`).</span><span class="sxs-lookup"><span data-stu-id="6019c-117">Checking the directory of the currently executing assembly for a subdirectory that matches the requested <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> (for example `es-MX`).</span></span>

        > [!NOTE]
        > <span data-ttu-id="6019c-118">Tato funkce nebyla implementována v .NET Core před 3,0.</span><span class="sxs-lookup"><span data-stu-id="6019c-118">This feature was not implemented in .NET Core before 3.0.</span></span>
        >
        > [!NOTE]
        > <span data-ttu-id="6019c-119">V případě systému Linux a macOS se v podadresářích rozlišují malá a velká písmena a musí být buď:</span><span class="sxs-lookup"><span data-stu-id="6019c-119">On Linux and macOS, the subdirectory is case-sensitive and must either:</span></span>
        >
        > - <span data-ttu-id="6019c-120">Přesně rozlišovat velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="6019c-120">Exactly match case.</span></span>
        > - <span data-ttu-id="6019c-121">V malých malých písmenech.</span><span class="sxs-lookup"><span data-stu-id="6019c-121">Be in lower case.</span></span>

    - <span data-ttu-id="6019c-122">Pokud `active` je <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> instance, spusťte výchozí logiku pro [zjišťování sestavení (prostředků)](default-probing.md#satellite-resource-assembly-probing) .</span><span class="sxs-lookup"><span data-stu-id="6019c-122">If `active` is the <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> instance, by running the [default satellite (resource) assembly probing](default-probing.md#satellite-resource-assembly-probing) logic.</span></span>

    - <span data-ttu-id="6019c-123">Volání <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> funkce.</span><span class="sxs-lookup"><span data-stu-id="6019c-123">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> function.</span></span>

    - <span data-ttu-id="6019c-124">Vyvolává se <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> událost.</span><span class="sxs-lookup"><span data-stu-id="6019c-124">Raising the <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> event.</span></span>

    - <span data-ttu-id="6019c-125">Vyvolává se <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událost.</span><span class="sxs-lookup"><span data-stu-id="6019c-125">Raising the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>

3. <span data-ttu-id="6019c-126">Pokud je načteno satelitní sestavení:</span><span class="sxs-lookup"><span data-stu-id="6019c-126">If a satellite assembly is loaded:</span></span>
   - <span data-ttu-id="6019c-127"><xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> Událost je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="6019c-127">The <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> event is raised.</span></span>
   - <span data-ttu-id="6019c-128">Sestavení je vyhledalo pro požadovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="6019c-128">The assembly is searched it for the requested resource.</span></span> <span data-ttu-id="6019c-129">Pokud modul runtime nalezne prostředek v sestavení, použije ho.</span><span class="sxs-lookup"><span data-stu-id="6019c-129">If the runtime finds the resource in the assembly, it uses it.</span></span> <span data-ttu-id="6019c-130">Pokud prostředek nenajde, pokračuje v hledání.</span><span class="sxs-lookup"><span data-stu-id="6019c-130">If it doesn't find the resource, it continues the search.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6019c-131">Chcete-li najít prostředek v rámci satelitního sestavení, modul runtime vyhledá soubor prostředků požadovaný <xref:System.Resources.ResourceManager> pro aktuální. <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="6019c-131">To find a resource within the satellite assembly, the runtime searches for the resource file requested by the <xref:System.Resources.ResourceManager> for the current <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6019c-132">V rámci souboru prostředků vyhledá požadovaný název prostředku.</span><span class="sxs-lookup"><span data-stu-id="6019c-132">Within the resource file, it searches for the requested resource name.</span></span> <span data-ttu-id="6019c-133">Pokud buď není nalezen, bude prostředek považován za nenalezený.</span><span class="sxs-lookup"><span data-stu-id="6019c-133">If either is not found, the resource is treated as not found.</span></span>

4. <span data-ttu-id="6019c-134">Modul runtime Next prohledává sestavení nadřazené jazykové verze prostřednictvím mnoha potenciálních úrovní, pokaždé při opakování kroků 2 & 3.</span><span class="sxs-lookup"><span data-stu-id="6019c-134">The runtime next searches the parent culture assemblies through many potential levels, each time repeating steps 2 & 3.</span></span>

    <span data-ttu-id="6019c-135">Každá jazyková verze má pouze jeden nadřazený prvek, který je definován <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> vlastností.</span><span class="sxs-lookup"><span data-stu-id="6019c-135">Each culture has only one parent, which is defined by the <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> property.</span></span>

    <span data-ttu-id="6019c-136">Hledání nadřazených jazykových verzí se zastaví, pokud je <xref:System.Globalization.CultureInfo.Parent%2A> <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>vlastnost jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="6019c-136">The search for parent cultures stops when a culture's <xref:System.Globalization.CultureInfo.Parent%2A> property is <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>.</span></span>

    <span data-ttu-id="6019c-137">V <xref:System.Globalization.CultureInfo.InvariantCulture>případě se nevrátíme k krokům 2 & 3, ale místo toho pokračujte krokem 5.</span><span class="sxs-lookup"><span data-stu-id="6019c-137">For the <xref:System.Globalization.CultureInfo.InvariantCulture>, we don't return to steps 2 & 3, but rather continue with step 5.</span></span>

5. <span data-ttu-id="6019c-138">Pokud se prostředek ještě nenalezne, použije se prostředek pro výchozí (záložní) jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="6019c-138">If the resource is still not found, the resource for the default (fallback) culture is used.</span></span>

   <span data-ttu-id="6019c-139">Prostředky pro výchozí jazykovou verzi jsou obvykle zahrnuty v sestavení Main aplikace.</span><span class="sxs-lookup"><span data-stu-id="6019c-139">Typically, the resources for the default culture are included in the main application assembly.</span></span> <span data-ttu-id="6019c-140">Pro <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> vlastnost však lze zadat <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6019c-140">However, you can specify <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> for the <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="6019c-141">Tato hodnota označuje, že konečné záložní umístění pro prostředky je satelitní sestavení, nikoli hlavní sestavení.</span><span class="sxs-lookup"><span data-stu-id="6019c-141">This value indicates that the ultimate fallback location for resources is a satellite assembly rather than the main assembly.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6019c-142">Výchozí jazyková verze je Ultimate Fallback.</span><span class="sxs-lookup"><span data-stu-id="6019c-142">The default culture is the ultimate fallback.</span></span> <span data-ttu-id="6019c-143">Proto doporučujeme vždy zahrnout vyčerpávající sadu prostředků do výchozího souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="6019c-143">Therefore, we recommend that you always include an exhaustive set of resources in the default resource file.</span></span> <span data-ttu-id="6019c-144">To pomáhá zabránit vyvolání výjimek.</span><span class="sxs-lookup"><span data-stu-id="6019c-144">This helps prevent exceptions from being thrown.</span></span> <span data-ttu-id="6019c-145">Díky úplnému nastavení zadáte zálohu pro všechny prostředky a zajistěte, aby měl uživatel vždy k dispozici alespoň jeden prostředek, a to i v případě, že není kulturně specifické.</span><span class="sxs-lookup"><span data-stu-id="6019c-145">By having an exhaustive set, you provide a fallback for all resources and ensure that at least one resource is always present for the user, even if it is not culturally specific.</span></span>

6. <span data-ttu-id="6019c-146">Uznan</span><span class="sxs-lookup"><span data-stu-id="6019c-146">Finally,</span></span>
   - <span data-ttu-id="6019c-147">Pokud modul runtime nenajde soubor prostředků pro výchozí (záložní) jazykovou verzi, je vyvolána <xref:System.Resources.MissingManifestResourceException> výjimka <xref:System.Resources.MissingSatelliteAssemblyException> nebo.</span><span class="sxs-lookup"><span data-stu-id="6019c-147">If the runtime doesn't find a resource file for a default (fallback) culture, a <xref:System.Resources.MissingManifestResourceException> or <xref:System.Resources.MissingSatelliteAssemblyException> exception is thrown.</span></span>
   - <span data-ttu-id="6019c-148">Pokud je nalezen soubor prostředků, ale požadovaný prostředek není k dispozici, požadavek se `null`vrátí.</span><span class="sxs-lookup"><span data-stu-id="6019c-148">If the resource file is found but the requested resource isn't present, the request returns `null`.</span></span>
