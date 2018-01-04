---
title: "Kompatibilita aplikací v rozhraní .NET Framework"
ms.custom: 
ms.date: 05/19/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
- app-compat
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
caps.latest.revision: "19"
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0144d75d7b158efb5ab205dfdd96884fb630eabc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="application-compatibility-in-the-net-framework"></a><span data-ttu-id="97abc-102">Kompatibilita aplikací v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="97abc-102">Application Compatibility in the .NET Framework</span></span>

## <a name="introduction"></a><span data-ttu-id="97abc-103">Úvod</span><span class="sxs-lookup"><span data-stu-id="97abc-103">Introduction</span></span>
<span data-ttu-id="97abc-104">Kompatibilita je velmi důležité cílem každou verzi rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="97abc-104">Compatibility is a very important goal of each .NET release.</span></span> <span data-ttu-id="97abc-105">Kompatibilita zajišťuje, že každou verzi sčítání, takže předchozí verze budou i nadále fungovat.</span><span class="sxs-lookup"><span data-stu-id="97abc-105">Compatibility ensures that each version is additive, so previous versions will still work.</span></span> <span data-ttu-id="97abc-106">Na druhé straně změny předchozí funkce (zvýšit výkon, řeší problémy zabezpečení, nebo opravit chyby) může způsobit problémy s kompatibilitou existující kód nebo existující aplikace, které běží v novější verzi.</span><span class="sxs-lookup"><span data-stu-id="97abc-106">On the other hand, changes to previous functionality (to improve performance, address security issues, or fix bugs) can cause compatibility problems in existing code or existing applications that run under a later version.</span></span> <span data-ttu-id="97abc-107">Rozhraní .NET Framework rozpozná Změna orientace změny a změny v modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="97abc-107">The .NET Framework recognizes retargeting changes and runtime changes.</span></span> <span data-ttu-id="97abc-108">Změna orientace změny ovlivní aplikace, které cílí na konkrétní verzi rozhraní .NET Framework, ale běží na novější verzi.</span><span class="sxs-lookup"><span data-stu-id="97abc-108">Retargeting changes affect applications that target a specific version of the .NET Framework but are running on a later version.</span></span> <span data-ttu-id="97abc-109">Změny v modulu runtime vliv na všechny aplikace spuštěné na konkrétní verzi.</span><span class="sxs-lookup"><span data-stu-id="97abc-109">Runtime changes affect all applications running on a particular version.</span></span>

<span data-ttu-id="97abc-110">Každá aplikace cílí na konkrétní verzi rozhraní .NET Framework, který může být určena:</span><span class="sxs-lookup"><span data-stu-id="97abc-110">Each app targets a specific version of the .NET Framework, which can be specified by:</span></span>

* <span data-ttu-id="97abc-111">Definování cílové rozhraní v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="97abc-111">Defining a target framework in Visual Studio.</span></span>
* <span data-ttu-id="97abc-112">Určení cílové rozhraní v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="97abc-112">Specifying the target framework in a project file.</span></span>
* <span data-ttu-id="97abc-113">Použití <xref:System.Runtime.Versioning.TargetFrameworkAttribute> ke zdrojovému kódu.</span><span class="sxs-lookup"><span data-stu-id="97abc-113">Applying a <xref:System.Runtime.Versioning.TargetFrameworkAttribute> to the source code.</span></span>

<span data-ttu-id="97abc-114">Když se používá novější verze, než jaké byla cílem, rozhraní .NET Framework použije quirked chování tak, aby napodoboval starší cílovou verzi.</span><span class="sxs-lookup"><span data-stu-id="97abc-114">When running on a newer version than what was targeted, the .NET Framework will use quirked behavior to mimic the older targeted version.</span></span> <span data-ttu-id="97abc-115">Jinými slovy aplikace bude spouštět na novější verzi rozhraní Framework, ale fungovat jako, pokud je spuštěn na starší verzi.</span><span class="sxs-lookup"><span data-stu-id="97abc-115">In other words, the app will run on the newer version of the Framework, but act as if it's running on the older version.</span></span> <span data-ttu-id="97abc-116">Prostřednictvím tohoto modelu quirking jsou omezeny řadu problémy s kompatibilitou mezi verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="97abc-116">Many of the compatibility issues between versions of the .NET Framework are mitigated through this quirking model.</span></span>

## <a name="runtime-changes"></a><span data-ttu-id="97abc-117">Změny v modulu runtime</span><span class="sxs-lookup"><span data-stu-id="97abc-117">Runtime changes</span></span>

<span data-ttu-id="97abc-118">Modul runtime problémy jsou ty, které se vynoří během nový modul runtime je umístěn na počítači a spouštějí stejnou binární soubory, ale je vidět různé chování.</span><span class="sxs-lookup"><span data-stu-id="97abc-118">Runtime issues are those that arise when a new runtime is placed on a machine and the same binaries are run, but different behavior is seen.</span></span> <span data-ttu-id="97abc-119">Pokud byl binární zkompilovaném pro rozhraní .NET Framework 4.0 se spustí v režimu kompatibility rozhraní .NET Framework 4.0 na verze 4.5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="97abc-119">If a binary was compiled for .NET Framework 4.0 it will run in .NET Framework 4.0 compatibility mode on 4.5 or later versions.</span></span> <span data-ttu-id="97abc-120">Mnoho změn, které mají vliv 4.5 nebude mít vliv na binární zkompilovaném pro 4.0.</span><span class="sxs-lookup"><span data-stu-id="97abc-120">Many of the changes that affect 4.5 will not affect a binary compiled for 4.0.</span></span> <span data-ttu-id="97abc-121">Toto je specifické pro domény aplikace a závisí na nastavení sestavení položky.</span><span class="sxs-lookup"><span data-stu-id="97abc-121">This is specific to the AppDomain and depends on the settings of the entry assembly.</span></span>

## <a name="retargeting-changes"></a><span data-ttu-id="97abc-122">Změny cíle</span><span class="sxs-lookup"><span data-stu-id="97abc-122">Retargeting changes</span></span>

<span data-ttu-id="97abc-123">Změna orientace problémy jsou ty, které se vynoří během sestavení, které se cílení na 4.0 je teď nastavená na cíl 4.5.</span><span class="sxs-lookup"><span data-stu-id="97abc-123">Retargeting issues are those that arise when an assembly that was targeting 4.0 is now set to target 4.5.</span></span> <span data-ttu-id="97abc-124">Nyní požádá sestavení do nové funkce, jakož i potenciální problémy s kompatibilitou na starých funkcí.</span><span class="sxs-lookup"><span data-stu-id="97abc-124">Now the assembly opts into the new features as well as potential compatibility issues to old features.</span></span> <span data-ttu-id="97abc-125">Znovu, to je závisí na položku sestavení, takže konzolovou aplikaci, která používá sestavení nebo web, který odkazuje na sestavení.</span><span class="sxs-lookup"><span data-stu-id="97abc-125">Again, this is dictated by the entry assembly, so the console app that uses the assembly, or the website that references the assembly.</span></span>

## <a name="net-compatibility-diagnostics"></a><span data-ttu-id="97abc-126">Diagnostika kompatibility rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="97abc-126">.NET Compatibility Diagnostics</span></span>

<span data-ttu-id="97abc-127">Diagnostika kompatibility .NET jsou zapnuté Roslyn analyzátorů, které pomáhají identifikovat problémy s kompatibilitou aplikací mezi verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="97abc-127">The .NET Compatibility Diagnostics are Roslyn-powered analyzers that help identify application compatibility issues between versions of the .NET Framework.</span></span> <span data-ttu-id="97abc-128">Tento seznam obsahuje všechny analyzátory k dispozici, i když pouze podmnožinu budou platit pro všechny konkrétní migrace.</span><span class="sxs-lookup"><span data-stu-id="97abc-128">This list contains all of the analyzers available, although only a subset will apply to any specific migration.</span></span> <span data-ttu-id="97abc-129">Analyzátory určí problémy, které platí pro plánované migrace a bude pouze surface ty.</span><span class="sxs-lookup"><span data-stu-id="97abc-129">The analyzers will determine which issues are applicable for the planned migration and will only surface those.</span></span>

<span data-ttu-id="97abc-130">Každý problém obsahuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="97abc-130">Each issue includes the following information:</span></span>

-   <span data-ttu-id="97abc-131">Popis co se změnilo z předchozí verze.</span><span class="sxs-lookup"><span data-stu-id="97abc-131">The description of what has changed from a previous version.</span></span>

-   <span data-ttu-id="97abc-132">Jak tato změna ovlivňuje zákazníky a jestli jsou dostupné pro zachování kompatibility mezi verzemi žádné alternativní řešení.</span><span class="sxs-lookup"><span data-stu-id="97abc-132">How the change affects customers and whether any workarounds are available to preserve compatibility across versions.</span></span>

-   <span data-ttu-id="97abc-133">Posouzení jak důležité je změnu.</span><span class="sxs-lookup"><span data-stu-id="97abc-133">An assessment of how important the change is.</span></span> <span data-ttu-id="97abc-134">Potíže s kompatibilitou aplikací jsou rozdělené takto:</span><span class="sxs-lookup"><span data-stu-id="97abc-134">Application compatibility issue are categorized as follows:</span></span>

    |   |   |
    |---|---|
    |<span data-ttu-id="97abc-135">Hlavní</span><span class="sxs-lookup"><span data-stu-id="97abc-135">Major</span></span>|<span data-ttu-id="97abc-136">Významné změny, která ovlivňuje velký počet aplikací, nebo vyžaduje významné úpravu kódu.</span><span class="sxs-lookup"><span data-stu-id="97abc-136">A significant change that affects a large number of apps or requires substantial modification of code.</span></span>|
    |<span data-ttu-id="97abc-137">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="97abc-137">Minor</span></span>|<span data-ttu-id="97abc-138">Změna, která ovlivňuje malý počet aplikací nebo který vyžaduje menší úpravu kódu.</span><span class="sxs-lookup"><span data-stu-id="97abc-138">A change that affects a small number of apps or that requires minor modification of code.</span></span>|
    |<span data-ttu-id="97abc-139">Okrajový případ</span><span class="sxs-lookup"><span data-stu-id="97abc-139">Edge case</span></span>|<span data-ttu-id="97abc-140">Změnu, která ovlivňuje aplikací v rámci velmi konkrétní, neobvyklé scénáře.</span><span class="sxs-lookup"><span data-stu-id="97abc-140">A change that affects apps under very specific, uncommon scenarios.</span></span>|
    |<span data-ttu-id="97abc-141">Transparentní</span><span class="sxs-lookup"><span data-stu-id="97abc-141">Transparent</span></span>|<span data-ttu-id="97abc-142">Změna bez znatelného vlivu na vývojáře aplikace nebo uživatele.</span><span class="sxs-lookup"><span data-stu-id="97abc-142">A change with no noticeable effect on the application's developer or user.</span></span>|

-   <span data-ttu-id="97abc-143">Verze označuje, když tato změna se nejprve zobrazí v rozhraní framework.</span><span class="sxs-lookup"><span data-stu-id="97abc-143">Version indicates when the change first appears in the framework.</span></span> <span data-ttu-id="97abc-144">Některé změny jsou umístěna v konkrétní verzi a vrátit v novější verzi; který také uvedené.</span><span class="sxs-lookup"><span data-stu-id="97abc-144">Some of the changes are introduced in a particular version and reverted in a later version; that is indicated as well.</span></span>

-   <span data-ttu-id="97abc-145">Typ změny:</span><span class="sxs-lookup"><span data-stu-id="97abc-145">The type of change:</span></span>

    |   |   |
    |---|---|
    |<span data-ttu-id="97abc-146">Změna orientace</span><span class="sxs-lookup"><span data-stu-id="97abc-146">Retargeting</span></span>|<span data-ttu-id="97abc-147">Změna ovlivní aplikace, které jsou překompilovat, jehož cílem je nová verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="97abc-147">The change affects apps that are recompiled to target a new version of the .NET Framework.</span></span>|
    |<span data-ttu-id="97abc-148">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="97abc-148">Runtime</span></span>|<span data-ttu-id="97abc-149">Změna ovlivní existující aplikaci, která cílí na předchozí verzi rozhraní .NET Framework, ale běží na novější verzi.</span><span class="sxs-lookup"><span data-stu-id="97abc-149">The change affects an existing app that targets a previous version of the .NET Framework but runs on a later version.</span></span>|

-   <span data-ttu-id="97abc-150">Ovlivněné rozhraní API, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="97abc-150">The affected APIS, if any.</span></span>

-   <span data-ttu-id="97abc-151">ID dostupné diagnostiky</span><span class="sxs-lookup"><span data-stu-id="97abc-151">The IDs of the available diagnostics</span></span>

## <a name="usage"></a><span data-ttu-id="97abc-152">Použití</span><span class="sxs-lookup"><span data-stu-id="97abc-152">Usage</span></span>
<span data-ttu-id="97abc-153">Pokud chcete začít, vyberte typ kompatibility změny níže:</span><span class="sxs-lookup"><span data-stu-id="97abc-153">To begin, select the type of compatibility change below:</span></span>

* [<span data-ttu-id="97abc-154">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="97abc-154">Retargeting Changes</span></span>](./retargeting/index.md)
* [<span data-ttu-id="97abc-155">Změny v modulu runtime</span><span class="sxs-lookup"><span data-stu-id="97abc-155">Runtime Changes</span></span>](./runtime/index.md)


## <a name="see-also"></a><span data-ttu-id="97abc-156">Viz také</span><span class="sxs-lookup"><span data-stu-id="97abc-156">See Also</span></span>

* [<span data-ttu-id="97abc-157">Verze a závislosti</span><span class="sxs-lookup"><span data-stu-id="97abc-157">Versions and Dependencies</span></span>](../../../docs/framework/migration-guide/versions-and-dependencies.md)
* [<span data-ttu-id="97abc-158">Co je nového</span><span class="sxs-lookup"><span data-stu-id="97abc-158">What's New</span></span>](../../../docs/framework/whats-new/index.md)
* [<span data-ttu-id="97abc-159">Zastaralé položky v knihovně tříd</span><span class="sxs-lookup"><span data-stu-id="97abc-159">What's Obsolete in the Class Library</span></span>](../../../docs/framework/whats-new/whats-obsolete.md)
