---
title: Algoritmus načítání satelitního sestavení - .NET Core
description: Popis podrobností algoritmu satelitního nakládacího systému v rozhraní .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: bfdc1d8179d46a13b3d137a87397fa3e573da33c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70105313"
---
# <a name="satellite-assembly-loading-algorithm"></a><span data-ttu-id="b4a30-103">Algoritmus satelitního nakládacího systému</span><span class="sxs-lookup"><span data-stu-id="b4a30-103">Satellite assembly loading algorithm</span></span>

<span data-ttu-id="b4a30-104">Satelitní sestavení se používají k ukládání lokalizovaných prostředků přizpůsobených pro jazyk a jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="b4a30-104">Satellite assemblies are used to store localized resources customized for language and culture.</span></span>

<span data-ttu-id="b4a30-105">Satelitní sestavení používají jiný algoritmus načítání než obecně spravovaná sestavení.</span><span class="sxs-lookup"><span data-stu-id="b4a30-105">Satellite assemblies use a different loading algorithm than general managed assemblies.</span></span>

## <a name="when-are-satellite-assemblies-loaded"></a><span data-ttu-id="b4a30-106">Kdy jsou satelitní sestavení načtena?</span><span class="sxs-lookup"><span data-stu-id="b4a30-106">When are satellite assemblies loaded?</span></span>

<span data-ttu-id="b4a30-107">Satelitní sestavení jsou načteny při načítání lokalizovaného prostředku.</span><span class="sxs-lookup"><span data-stu-id="b4a30-107">Satellite assemblies are loaded when loading a localized resource.</span></span>

<span data-ttu-id="b4a30-108">Základní rozhraní API pro načtení <xref:System.Resources.ResourceManager?displayProperty=fullName> lokalizovaných prostředků je třída.</span><span class="sxs-lookup"><span data-stu-id="b4a30-108">The basic API to load localized resources is the <xref:System.Resources.ResourceManager?displayProperty=fullName> class.</span></span> <span data-ttu-id="b4a30-109">Nakonec <xref:System.Resources.ResourceManager> třída bude volat <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> metodu <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>pro každý .</span><span class="sxs-lookup"><span data-stu-id="b4a30-109">Ultimately the <xref:System.Resources.ResourceManager> class will call the <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> method for each <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="b4a30-110">Rozhraní API vyšší úrovně může abstrahujte rozhraní API nižší úrovně.</span><span class="sxs-lookup"><span data-stu-id="b4a30-110">Higher-level APIs may abstract the low-level API.</span></span>

## <a name="algorithm"></a><span data-ttu-id="b4a30-111">Algoritmus</span><span class="sxs-lookup"><span data-stu-id="b4a30-111">Algorithm</span></span>

<span data-ttu-id="b4a30-112">Záložní proces prostředku .NET Core zahrnuje následující kroky:</span><span class="sxs-lookup"><span data-stu-id="b4a30-112">The .NET Core resource fallback process involves the following steps:</span></span>

1. <span data-ttu-id="b4a30-113">Určete `active` <xref:System.Runtime.Loader.AssemblyLoadContext> instanci.</span><span class="sxs-lookup"><span data-stu-id="b4a30-113">Determine the `active` <xref:System.Runtime.Loader.AssemblyLoadContext> instance.</span></span> <span data-ttu-id="b4a30-114">Ve všech případech `active` instance je vykonávající <xref:System.Runtime.Loader.AssemblyLoadContext>sestavení .</span><span class="sxs-lookup"><span data-stu-id="b4a30-114">In all cases, the `active` instance is the executing assembly's <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span>

2. <span data-ttu-id="b4a30-115">Instance `active` se pokusí načíst satelitní sestavení pro požadovanou jazykovou verzi v pořadí podle priority:</span><span class="sxs-lookup"><span data-stu-id="b4a30-115">The `active` instance attempts to load a satellite assembly for the requested culture in priority order by:</span></span>
    - <span data-ttu-id="b4a30-116">Kontroluji jeho mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="b4a30-116">Checking its cache.</span></span>
    - <span data-ttu-id="b4a30-117">Kontrola adresáře aktuálně spuštěného sestavení pro podadresář, který <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> odpovídá `es-MX`požadovanému (například).</span><span class="sxs-lookup"><span data-stu-id="b4a30-117">Checking the directory of the currently executing assembly for a subdirectory that matches the requested <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> (for example `es-MX`).</span></span>

        > [!NOTE]
        > <span data-ttu-id="b4a30-118">Tato funkce nebyla implementována v rozhraní .NET Core před 3.0.</span><span class="sxs-lookup"><span data-stu-id="b4a30-118">This feature was not implemented in .NET Core before 3.0.</span></span>
        >
        > [!NOTE]
        > <span data-ttu-id="b4a30-119">V Linuxu a macOS je podadresář rozlišován podle velkých a malých písmen a musí:</span><span class="sxs-lookup"><span data-stu-id="b4a30-119">On Linux and macOS, the subdirectory is case-sensitive and must either:</span></span>
        > - <span data-ttu-id="b4a30-120">Přesně tak, aby se shodoval.</span><span class="sxs-lookup"><span data-stu-id="b4a30-120">Exactly match case.</span></span>
        > - <span data-ttu-id="b4a30-121">Buďte v malé písmeno.</span><span class="sxs-lookup"><span data-stu-id="b4a30-121">Be in lower case.</span></span>

    - <span data-ttu-id="b4a30-122">Pokud `active` je <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> instance, spuštěním [výchozí satelitní (prostředek) sondování](default-probing.md#satellite-resource-assembly-probing) logiky.</span><span class="sxs-lookup"><span data-stu-id="b4a30-122">If `active` is the <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> instance, by running the [default satellite (resource) assembly probing](default-probing.md#satellite-resource-assembly-probing) logic.</span></span>

    - <span data-ttu-id="b4a30-123">Volání <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> funkce.</span><span class="sxs-lookup"><span data-stu-id="b4a30-123">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> function.</span></span>

    - <span data-ttu-id="b4a30-124">Vyvolání <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> akce.</span><span class="sxs-lookup"><span data-stu-id="b4a30-124">Raising the <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> event.</span></span>

    - <span data-ttu-id="b4a30-125">Vyvolání <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> akce.</span><span class="sxs-lookup"><span data-stu-id="b4a30-125">Raising the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>

3. <span data-ttu-id="b4a30-126">Pokud je načteno satelitní sestavení:</span><span class="sxs-lookup"><span data-stu-id="b4a30-126">If a satellite assembly is loaded:</span></span>
   - <span data-ttu-id="b4a30-127">Událost <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="b4a30-127">The <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> event is raised.</span></span>
   - <span data-ttu-id="b4a30-128">Sestavení je prohledáno pro požadovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="b4a30-128">The assembly is searched it for the requested resource.</span></span> <span data-ttu-id="b4a30-129">Pokud za běhu najde prostředek v sestavení, použije jej.</span><span class="sxs-lookup"><span data-stu-id="b4a30-129">If the runtime finds the resource in the assembly, it uses it.</span></span> <span data-ttu-id="b4a30-130">Pokud zdroj nenajde, bude pokračovat v hledání.</span><span class="sxs-lookup"><span data-stu-id="b4a30-130">If it doesn't find the resource, it continues the search.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b4a30-131">Chcete-li najít prostředek v satelitním sestavení, hledá za běhu <xref:System.Resources.ResourceManager> soubor <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>prostředků požadovaný pro aktuální .</span><span class="sxs-lookup"><span data-stu-id="b4a30-131">To find a resource within the satellite assembly, the runtime searches for the resource file requested by the <xref:System.Resources.ResourceManager> for the current <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b4a30-132">V souboru prostředků vyhledá požadovaný název prostředku.</span><span class="sxs-lookup"><span data-stu-id="b4a30-132">Within the resource file, it searches for the requested resource name.</span></span> <span data-ttu-id="b4a30-133">Pokud buď nebyl nalezen, prostředek je považován za nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="b4a30-133">If either is not found, the resource is treated as not found.</span></span>

4. <span data-ttu-id="b4a30-134">Další runtime prohledává nadřazená sestavení jazykové verze prostřednictvím mnoha potenciálních úrovní, pokaždé, když opakuje kroky 2 & 3.</span><span class="sxs-lookup"><span data-stu-id="b4a30-134">The runtime next searches the parent culture assemblies through many potential levels, each time repeating steps 2 & 3.</span></span>

    <span data-ttu-id="b4a30-135">Každá jazyková verze má pouze jeden <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> nadřazený, který je definován vlastností.</span><span class="sxs-lookup"><span data-stu-id="b4a30-135">Each culture has only one parent, which is defined by the <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> property.</span></span>

    <span data-ttu-id="b4a30-136">Hledání nadřazené jazykové verze <xref:System.Globalization.CultureInfo.Parent%2A> se <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>zastaví, když je vlastnost jazykové verze .</span><span class="sxs-lookup"><span data-stu-id="b4a30-136">The search for parent cultures stops when a culture's <xref:System.Globalization.CultureInfo.Parent%2A> property is <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>.</span></span>

    <span data-ttu-id="b4a30-137">Pro <xref:System.Globalization.CultureInfo.InvariantCulture>, nevracíme se k krokům 2 & 3, ale spíše pokračovat krokem 5.</span><span class="sxs-lookup"><span data-stu-id="b4a30-137">For the <xref:System.Globalization.CultureInfo.InvariantCulture>, we don't return to steps 2 & 3, but rather continue with step 5.</span></span>

5. <span data-ttu-id="b4a30-138">Pokud prostředek stále nebyl nalezen, použije se prostředek pro výchozí (záložní) jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="b4a30-138">If the resource is still not found, the resource for the default (fallback) culture is used.</span></span>

   <span data-ttu-id="b4a30-139">Prostředky pro výchozí jazykovou verzi jsou obvykle zahrnuty v sestavení hlavní aplikace.</span><span class="sxs-lookup"><span data-stu-id="b4a30-139">Typically, the resources for the default culture are included in the main application assembly.</span></span> <span data-ttu-id="b4a30-140">Můžete však <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> zadat <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b4a30-140">However, you can specify <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> for the <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="b4a30-141">Tato hodnota označuje, že konečné záložní umístění pro prostředky je satelitní sestavení spíše než hlavní sestavení.</span><span class="sxs-lookup"><span data-stu-id="b4a30-141">This value indicates that the ultimate fallback location for resources is a satellite assembly rather than the main assembly.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b4a30-142">Výchozí jazyková verze je konečný záložní.</span><span class="sxs-lookup"><span data-stu-id="b4a30-142">The default culture is the ultimate fallback.</span></span> <span data-ttu-id="b4a30-143">Proto doporučujeme vždy zahrnout vyčerpávající sadu prostředků ve výchozím souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="b4a30-143">Therefore, we recommend that you always include an exhaustive set of resources in the default resource file.</span></span> <span data-ttu-id="b4a30-144">To pomáhá zabránit vyvolání výjimek.</span><span class="sxs-lookup"><span data-stu-id="b4a30-144">This helps prevent exceptions from being thrown.</span></span> <span data-ttu-id="b4a30-145">Tím, že vyčerpávající sadu, poskytujete záložní pro všechny prostředky a ujistěte se, že alespoň jeden prostředek je vždy k dispozici pro uživatele, i když není kulturně specifické.</span><span class="sxs-lookup"><span data-stu-id="b4a30-145">By having an exhaustive set, you provide a fallback for all resources and ensure that at least one resource is always present for the user, even if it is not culturally specific.</span></span>

6. <span data-ttu-id="b4a30-146">Konečně</span><span class="sxs-lookup"><span data-stu-id="b4a30-146">Finally,</span></span>
   - <span data-ttu-id="b4a30-147">Pokud runtime nenajde soubor prostředků pro výchozí (záložní) jazykovou <xref:System.Resources.MissingManifestResourceException> <xref:System.Resources.MissingSatelliteAssemblyException> verzi, je vyvolána výjimka nebo výjimka.</span><span class="sxs-lookup"><span data-stu-id="b4a30-147">If the runtime doesn't find a resource file for a default (fallback) culture, a <xref:System.Resources.MissingManifestResourceException> or <xref:System.Resources.MissingSatelliteAssemblyException> exception is thrown.</span></span>
   - <span data-ttu-id="b4a30-148">Pokud je soubor prostředků nalezen, ale požadovaný prostředek není `null`k dispozici, požadavek vrátí .</span><span class="sxs-lookup"><span data-stu-id="b4a30-148">If the resource file is found but the requested resource isn't present, the request returns `null`.</span></span>
