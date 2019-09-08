---
title: Kompatibilita aplikací v rozhraní .NET Framework
ms.date: 05/19/2017
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f547180995ec155f9121eeace109e7dfb07c7827
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790123"
---
# <a name="application-compatibility-in-the-net-framework"></a><span data-ttu-id="e7507-102">Kompatibilita aplikací v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e7507-102">Application Compatibility in the .NET Framework</span></span>

## <a name="introduction"></a><span data-ttu-id="e7507-103">Úvod</span><span class="sxs-lookup"><span data-stu-id="e7507-103">Introduction</span></span>
<span data-ttu-id="e7507-104">Kompatibilita je velice důležitým cílem každé verze rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="e7507-104">Compatibility is a very important goal of each .NET release.</span></span> <span data-ttu-id="e7507-105">Kompatibilita zajišťuje, že každá verze je doplňková, takže předchozí verze budou fungovat i nadále.</span><span class="sxs-lookup"><span data-stu-id="e7507-105">Compatibility ensures that each version is additive, so previous versions will still work.</span></span> <span data-ttu-id="e7507-106">Na druhé straně změny předchozí funkce (za účelem vylepšení výkonu, řešení potíží se zabezpečením nebo opravy chyb) můžou způsobit problémy s kompatibilitou v existujícím kódu nebo v existujících aplikacích, které běží v novější verzi.</span><span class="sxs-lookup"><span data-stu-id="e7507-106">On the other hand, changes to previous functionality (to improve performance, address security issues, or fix bugs) can cause compatibility problems in existing code or existing applications that run under a later version.</span></span> <span data-ttu-id="e7507-107">.NET Framework rozpoznává změny cíle a změny v běhu.</span><span class="sxs-lookup"><span data-stu-id="e7507-107">The .NET Framework recognizes retargeting changes and runtime changes.</span></span> <span data-ttu-id="e7507-108">Změny cíle ovlivňují aplikace, které cílí na konkrétní verzi .NET Framework, ale běží v novější verzi.</span><span class="sxs-lookup"><span data-stu-id="e7507-108">Retargeting changes affect applications that target a specific version of the .NET Framework but are running on a later version.</span></span> <span data-ttu-id="e7507-109">Změny v modulu runtime ovlivňují všechny aplikace spuštěné v konkrétní verzi.</span><span class="sxs-lookup"><span data-stu-id="e7507-109">Runtime changes affect all applications running on a particular version.</span></span>

<span data-ttu-id="e7507-110">Každá aplikace cílí na konkrétní verzi .NET Framework, kterou lze určit pomocí:</span><span class="sxs-lookup"><span data-stu-id="e7507-110">Each app targets a specific version of the .NET Framework, which can be specified by:</span></span>

- <span data-ttu-id="e7507-111">Definování cílové architektury v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e7507-111">Defining a target framework in Visual Studio.</span></span>
- <span data-ttu-id="e7507-112">Určení cílové architektury v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="e7507-112">Specifying the target framework in a project file.</span></span>
- <span data-ttu-id="e7507-113">Aplikuje <xref:System.Runtime.Versioning.TargetFrameworkAttribute> se na zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="e7507-113">Applying a <xref:System.Runtime.Versioning.TargetFrameworkAttribute> to the source code.</span></span>

<span data-ttu-id="e7507-114">Při spuštění v novější verzi, než je cílová, .NET Framework použije chování quirked k napodobování starší cílové verze.</span><span class="sxs-lookup"><span data-stu-id="e7507-114">When running on a newer version than what was targeted, the .NET Framework will use quirked behavior to mimic the older targeted version.</span></span> <span data-ttu-id="e7507-115">Jinými slovy, aplikace bude spuštěna v novější verzi rozhraní, ale funguje jako v případě, že běží na starší verzi.</span><span class="sxs-lookup"><span data-stu-id="e7507-115">In other words, the app will run on the newer version of the Framework, but act as if it's running on the older version.</span></span> <span data-ttu-id="e7507-116">Mnohé z problémů s kompatibilitou mezi verzemi .NET Framework jsou zmírnit prostřednictvím tohoto modelu quirking.</span><span class="sxs-lookup"><span data-stu-id="e7507-116">Many of the compatibility issues between versions of the .NET Framework are mitigated through this quirking model.</span></span> <span data-ttu-id="e7507-117">Verze .NET Framework, na kterou aplikace cílí, je určena cílovou verzí záznamu pro doménu aplikace, ve které kód běží.</span><span class="sxs-lookup"><span data-stu-id="e7507-117">The version of the .NET Framework that an application targets is determined by the target version of the entry assembly for the application domain that the code is running in.</span></span> <span data-ttu-id="e7507-118">Všechna další sestavení načtená v této cílové doméně aplikace, která .NET Framework verzi.</span><span class="sxs-lookup"><span data-stu-id="e7507-118">All additional assemblies loaded in that application domain target that .NET Framework version.</span></span> <span data-ttu-id="e7507-119">Například v případě spustitelného souboru je rozhraní, které cílí na spustitelný soubor, v režimu kompatibility všechna sestavení v dané doméně AppDomain budou spouštěna v.</span><span class="sxs-lookup"><span data-stu-id="e7507-119">For example, in the case of an executable, the framework the executable targets is the compatibility mode all assemblies in that AppDomain will run under.</span></span>

## <a name="runtime-changes"></a><span data-ttu-id="e7507-120">Změny v modulu runtime</span><span class="sxs-lookup"><span data-stu-id="e7507-120">Runtime changes</span></span>

<span data-ttu-id="e7507-121">Problémy za běhu jsou ty, které vznikají při umístění nového modulu runtime do počítače a spuštění stejných binárních souborů, ale je vidět jiné chování.</span><span class="sxs-lookup"><span data-stu-id="e7507-121">Runtime issues are those that arise when a new runtime is placed on a machine and the same binaries are run, but different behavior is seen.</span></span> <span data-ttu-id="e7507-122">Pokud byl binární soubor kompilován pro .NET Framework 4,0, bude spuštěn v režimu kompatibility .NET Framework 4,0 na 4,5 nebo novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="e7507-122">If a binary was compiled for .NET Framework 4.0 it will run in .NET Framework 4.0 compatibility mode on 4.5 or later versions.</span></span> <span data-ttu-id="e7507-123">Mnohé změny, které ovlivňují 4,5, nebudou mít vliv na binární kompilováno pro 4,0.</span><span class="sxs-lookup"><span data-stu-id="e7507-123">Many of the changes that affect 4.5 will not affect a binary compiled for 4.0.</span></span> <span data-ttu-id="e7507-124">To je specifické pro doménu AppDomain a závisí na nastavení položky sestavení.</span><span class="sxs-lookup"><span data-stu-id="e7507-124">This is specific to the AppDomain and depends on the settings of the entry assembly.</span></span>

## <a name="retargeting-changes"></a><span data-ttu-id="e7507-125">Změny cíle</span><span class="sxs-lookup"><span data-stu-id="e7507-125">Retargeting changes</span></span>

<span data-ttu-id="e7507-126">Změny cíle se projevují v případě, že sestavení, které cílí na 4,0, je teď nastavené na target 4,5.</span><span class="sxs-lookup"><span data-stu-id="e7507-126">Retargeting issues are those that arise when an assembly that was targeting 4.0 is now set to target 4.5.</span></span> <span data-ttu-id="e7507-127">Nyní se sestavení výslovný do nových funkcí a také potenciální problémy s kompatibilitou se starými funkcemi.</span><span class="sxs-lookup"><span data-stu-id="e7507-127">Now the assembly opts into the new features as well as potential compatibility issues to old features.</span></span> <span data-ttu-id="e7507-128">Znovu, toto je určeno sestavením záznamu, aby Konzolová aplikace používala sestavení, nebo web, který odkazuje na sestavení.</span><span class="sxs-lookup"><span data-stu-id="e7507-128">Again, this is dictated by the entry assembly, so the console app that uses the assembly, or the website that references the assembly.</span></span>

## <a name="net-compatibility-diagnostics"></a><span data-ttu-id="e7507-129">Diagnostika kompatibility rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="e7507-129">.NET Compatibility Diagnostics</span></span>

<span data-ttu-id="e7507-130">Diagnostika kompatibility rozhraní .NET jsou Roslyn analyzátory založené na technologii, které vám pomůžou identifikovat problémy s kompatibilitou aplikací mezi verzemi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e7507-130">The .NET Compatibility Diagnostics are Roslyn-powered analyzers that help identify application compatibility issues between versions of the .NET Framework.</span></span> <span data-ttu-id="e7507-131">Tento seznam obsahuje všechny dostupné analyzátory, i když se u jakékoli konkrétní migrace uplatní jenom podmnožina.</span><span class="sxs-lookup"><span data-stu-id="e7507-131">This list contains all of the analyzers available, although only a subset will apply to any specific migration.</span></span> <span data-ttu-id="e7507-132">Analyzátory určí, které problémy se vztahují k plánované migraci, a budou je jenom naploché.</span><span class="sxs-lookup"><span data-stu-id="e7507-132">The analyzers will determine which issues are applicable for the planned migration and will only surface those.</span></span>

<span data-ttu-id="e7507-133">Každý problém zahrnuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="e7507-133">Each issue includes the following information:</span></span>

- <span data-ttu-id="e7507-134">Popis toho, co se změnilo v předchozí verzi.</span><span class="sxs-lookup"><span data-stu-id="e7507-134">The description of what has changed from a previous version.</span></span>

- <span data-ttu-id="e7507-135">Jaký vliv má změna na zákazníky a zda jsou k dispozici jakákoli alternativní řešení pro zachování kompatibility napříč verzemi.</span><span class="sxs-lookup"><span data-stu-id="e7507-135">How the change affects customers and whether any workarounds are available to preserve compatibility across versions.</span></span>

- <span data-ttu-id="e7507-136">Posouzení důležitosti změny.</span><span class="sxs-lookup"><span data-stu-id="e7507-136">An assessment of how important the change is.</span></span> <span data-ttu-id="e7507-137">Problémy s kompatibilitou aplikací jsou zařazené do kategorií následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e7507-137">Application compatibility issue are categorized as follows:</span></span>

    |   |   |
    |---|---|
    |<span data-ttu-id="e7507-138">Hlavní</span><span class="sxs-lookup"><span data-stu-id="e7507-138">Major</span></span>|<span data-ttu-id="e7507-139">Významná změna ovlivňující velký počet aplikací nebo vyžaduje značnou úpravu kódu.</span><span class="sxs-lookup"><span data-stu-id="e7507-139">A significant change that affects a large number of apps or requires substantial modification of code.</span></span>|
    |<span data-ttu-id="e7507-140">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="e7507-140">Minor</span></span>|<span data-ttu-id="e7507-141">Změna, která má vliv na malý počet aplikací nebo které vyžadují menší úpravu kódu.</span><span class="sxs-lookup"><span data-stu-id="e7507-141">A change that affects a small number of apps or that requires minor modification of code.</span></span>|
    |<span data-ttu-id="e7507-142">Okrajový případ</span><span class="sxs-lookup"><span data-stu-id="e7507-142">Edge case</span></span>|<span data-ttu-id="e7507-143">Změna ovlivňující aplikace v rámci velmi konkrétních neobvyklých scénářů.</span><span class="sxs-lookup"><span data-stu-id="e7507-143">A change that affects apps under very specific, uncommon scenarios.</span></span>|
    |<span data-ttu-id="e7507-144">Transparentní</span><span class="sxs-lookup"><span data-stu-id="e7507-144">Transparent</span></span>|<span data-ttu-id="e7507-145">Změna bez znatelného efektu pro vývojáře nebo uživatele aplikace.</span><span class="sxs-lookup"><span data-stu-id="e7507-145">A change with no noticeable effect on the application's developer or user.</span></span>|

- <span data-ttu-id="e7507-146">Verze označuje, kdy se změna v rozhraní zobrazí jako první.</span><span class="sxs-lookup"><span data-stu-id="e7507-146">Version indicates when the change first appears in the framework.</span></span> <span data-ttu-id="e7507-147">Některé změny jsou představeny v konkrétní verzi a vráceny v pozdější verzi. To je také uvedeno.</span><span class="sxs-lookup"><span data-stu-id="e7507-147">Some of the changes are introduced in a particular version and reverted in a later version; that is indicated as well.</span></span>

- <span data-ttu-id="e7507-148">Typ změny:</span><span class="sxs-lookup"><span data-stu-id="e7507-148">The type of change:</span></span>

    |   |   |
    |---|---|
    |<span data-ttu-id="e7507-149">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="e7507-149">Retargeting</span></span>|<span data-ttu-id="e7507-150">Tato změna ovlivní aplikace, které jsou znovu zkompilovány, aby byly cíleny na novou verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e7507-150">The change affects apps that are recompiled to target a new version of the .NET Framework.</span></span>|
    |<span data-ttu-id="e7507-151">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="e7507-151">Runtime</span></span>|<span data-ttu-id="e7507-152">Tato změna má vliv na existující aplikaci, která cílí na předchozí verzi .NET Framework, ale běží v novější verzi.</span><span class="sxs-lookup"><span data-stu-id="e7507-152">The change affects an existing app that targets a previous version of the .NET Framework but runs on a later version.</span></span>|

- <span data-ttu-id="e7507-153">Ovlivněná rozhraní API, pokud existují.</span><span class="sxs-lookup"><span data-stu-id="e7507-153">The affected APIS, if any.</span></span>

- <span data-ttu-id="e7507-154">ID dostupné diagnostiky</span><span class="sxs-lookup"><span data-stu-id="e7507-154">The IDs of the available diagnostics</span></span>

## <a name="usage"></a><span data-ttu-id="e7507-155">Použití</span><span class="sxs-lookup"><span data-stu-id="e7507-155">Usage</span></span>
<span data-ttu-id="e7507-156">Začněte tím, že vyberete typ změny kompatibility níže:</span><span class="sxs-lookup"><span data-stu-id="e7507-156">To begin, select the type of compatibility change below:</span></span>

- [<span data-ttu-id="e7507-157">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="e7507-157">Retargeting Changes</span></span>](./retargeting/index.md)
- [<span data-ttu-id="e7507-158">Změny v modulu runtime</span><span class="sxs-lookup"><span data-stu-id="e7507-158">Runtime Changes</span></span>](./runtime/index.md)

## <a name="see-also"></a><span data-ttu-id="e7507-159">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7507-159">See also</span></span>

- [<span data-ttu-id="e7507-160">Verze a závislosti</span><span class="sxs-lookup"><span data-stu-id="e7507-160">Versions and Dependencies</span></span>](versions-and-dependencies.md)
- [<span data-ttu-id="e7507-161">Co je nového</span><span class="sxs-lookup"><span data-stu-id="e7507-161">What's New</span></span>](../whats-new/index.md)
- [<span data-ttu-id="e7507-162">Zastaralé položky v knihovně tříd</span><span class="sxs-lookup"><span data-stu-id="e7507-162">What's Obsolete in the Class Library</span></span>](../whats-new/whats-obsolete.md)
