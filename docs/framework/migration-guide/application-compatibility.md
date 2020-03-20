---
title: Runtime a retargeting změny - .NET Framework
ms.date: 10/29/2019
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
ms.openlocfilehash: c46f781d495b87a4f24e77935df7c4814c8567ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73196694"
---
# <a name="application-compatibility-in-the-net-framework"></a><span data-ttu-id="d6c2e-102">Kompatibilita aplikací v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d6c2e-102">Application compatibility in the .NET Framework</span></span>

<span data-ttu-id="d6c2e-103">Kompatibilita je důležitým cílem každé verze .NET.</span><span class="sxs-lookup"><span data-stu-id="d6c2e-103">Compatibility is an important goal of each .NET release.</span></span> <span data-ttu-id="d6c2e-104">Kompatibilita zajišťuje, že každá verze je aditivní, takže předchozí verze budou i nadále fungovat.</span><span class="sxs-lookup"><span data-stu-id="d6c2e-104">Compatibility ensures that each version is additive, so previous versions will continue to work.</span></span> <span data-ttu-id="d6c2e-105">Na druhou stranu změny předchozích funkcí (například ke zlepšení výkonu, řešení problémů se zabezpečením nebo opravě chyb) mohou způsobit problémy s kompatibilitou v existujícím kódu nebo existujících aplikacích, které běží v novější verzi.</span><span class="sxs-lookup"><span data-stu-id="d6c2e-105">On the other hand, changes to previous functionality (for example, to improve performance, address security issues, or fix bugs) can cause compatibility problems in existing code or existing applications that run under a later version.</span></span>

<span data-ttu-id="d6c2e-106">Každá aplikace cílí na konkrétní verzi rozhraní .NET Framework podle následujících cílů:</span><span class="sxs-lookup"><span data-stu-id="d6c2e-106">Each app targets a specific version of the .NET Framework by:</span></span>

- <span data-ttu-id="d6c2e-107">Definování cílového rozhraní v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d6c2e-107">Defining a target framework in Visual Studio.</span></span>
- <span data-ttu-id="d6c2e-108">Určení cílového rozhraní v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="d6c2e-108">Specifying the target framework in a project file.</span></span>
- <span data-ttu-id="d6c2e-109">Použití <xref:System.Runtime.Versioning.TargetFrameworkAttribute> a na zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="d6c2e-109">Applying a <xref:System.Runtime.Versioning.TargetFrameworkAttribute> to the source code.</span></span>

<span data-ttu-id="d6c2e-110">Při migraci z jedné verze rozhraní .NET Framework do jiné ho lze zvážit dvěma typy změn:</span><span class="sxs-lookup"><span data-stu-id="d6c2e-110">When migrating from one version of the .NET Framework to another, there are two types of changes to consider:</span></span>

- [<span data-ttu-id="d6c2e-111">Změny za běhu</span><span class="sxs-lookup"><span data-stu-id="d6c2e-111">Runtime changes</span></span>](#runtime-changes)
- [<span data-ttu-id="d6c2e-112">Změny opětovného cílení</span><span class="sxs-lookup"><span data-stu-id="d6c2e-112">Retargeting changes</span></span>](#retargeting-changes)

## <a name="runtime-changes"></a><span data-ttu-id="d6c2e-113">Změny v modulu runtime</span><span class="sxs-lookup"><span data-stu-id="d6c2e-113">Runtime changes</span></span>

<span data-ttu-id="d6c2e-114">Problémy s runtime jsou ty, které vznikají při umístění nového runtime do počítače a změny chování aplikace.</span><span class="sxs-lookup"><span data-stu-id="d6c2e-114">Runtime issues are those that arise when a new runtime is placed on a machine and an app's behavior changes.</span></span> <span data-ttu-id="d6c2e-115">Při spuštění na novější verzi, než co bylo cílené, rozhraní .NET Framework používá *vtípek* chování napodobovat starší cílenou verzi.</span><span class="sxs-lookup"><span data-stu-id="d6c2e-115">When running on a newer version than what was targeted, the .NET Framework uses *quirked* behavior to mimic the older targeted version.</span></span> <span data-ttu-id="d6c2e-116">Aplikace běží na novější verzi, ale funguje, jako by byla spuštěna na starší verzi.</span><span class="sxs-lookup"><span data-stu-id="d6c2e-116">The app runs on the newer version but acts as if it's running on the older version.</span></span> <span data-ttu-id="d6c2e-117">Mnoho problémů s kompatibilitou mezi verzemi rozhraní .NET Framework je zmírněno prostřednictvím tohoto modelu quirking.</span><span class="sxs-lookup"><span data-stu-id="d6c2e-117">Many of the compatibility issues between versions of the .NET Framework are mitigated through this quirking model.</span></span> <span data-ttu-id="d6c2e-118">Pokud byl například binární soubor zkompilován pro rozhraní .NET Framework 4.0, ale běží v počítači s rozhraním .NET Framework 4.5 nebo novějším, běží v režimu kompatibility rozhraní .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="d6c2e-118">For example, if a binary was compiled for .NET Framework 4.0 but runs on a machine with .NET Framework 4.5 or later, it runs in .NET Framework 4.0 compatibility mode.</span></span> <span data-ttu-id="d6c2e-119">To znamená, že mnoho změn v novější verzi nemá vliv na binární.</span><span class="sxs-lookup"><span data-stu-id="d6c2e-119">This means that many of the changes in the later version don't affect the binary.</span></span>

<span data-ttu-id="d6c2e-120">Verze rozhraní .NET Framework, na kterou se aplikace zaměřuje, je určena cílovou verzí vstupního sestavení pro doménu aplikace, ve které je kód spuštěn.</span><span class="sxs-lookup"><span data-stu-id="d6c2e-120">The version of the .NET Framework that an application targets is determined by the target version of the entry assembly for the application domain that the code runs in.</span></span> <span data-ttu-id="d6c2e-121">Všechna další sestavení načtená v této doméně aplikace cílí na tuto verzi.</span><span class="sxs-lookup"><span data-stu-id="d6c2e-121">All additional assemblies loaded in that application domain target that version.</span></span> <span data-ttu-id="d6c2e-122">Například v případě spustitelného souboru verze, která je spustitelný mýše cíle režim kompatibility všechna sestavení v této doméně aplikace spustit pod.</span><span class="sxs-lookup"><span data-stu-id="d6c2e-122">For example, in the case of an executable, the version that the executable targets is the compatibility mode all assemblies in that application domain run under.</span></span>

<span data-ttu-id="d6c2e-123">Chcete-li zobrazit seznam změn za běhu, které se vztahují na vaše prostředí, vyberte verzi rozhraní .NET Framework, na kterou aktuálně cílíte, a verzi, na kterou chcete migrovat:</span><span class="sxs-lookup"><span data-stu-id="d6c2e-123">To see a list of runtime changes that apply to your environment, select the .NET Framework version you're currently targeting and then the version you wish to migrate to:</span></span>

[!INCLUDE[versionselector](../../../includes/migration-guide/runtime/versionselector.md)]

## <a name="retargeting-changes"></a><span data-ttu-id="d6c2e-124">Změny cílení</span><span class="sxs-lookup"><span data-stu-id="d6c2e-124">Retargeting changes</span></span>

<span data-ttu-id="d6c2e-125">Retargeting změny jsou ty, které vznikají při sestavení je znovu zkompilován cílit novější verzi.</span><span class="sxs-lookup"><span data-stu-id="d6c2e-125">Retargeting changes are those that arise when an assembly is recompiled to target a newer version.</span></span> <span data-ttu-id="d6c2e-126">Cílení na novější verzi znamená, že sestavení se rozhodne pro nové funkce, stejně jako potenciální problémy s kompatibilitou starých funkcí.</span><span class="sxs-lookup"><span data-stu-id="d6c2e-126">Targeting a newer version means the assembly opts into the new features as well as potential compatibility issues for old features.</span></span>

<span data-ttu-id="d6c2e-127">Chcete-li zobrazit seznam změn opětovného cílení, které se vztahují na vaše prostředí, vyberte verzi rozhraní .NET Framework, na kterou aktuálně cílíte, a verzi, na kterou chcete migrovat:</span><span class="sxs-lookup"><span data-stu-id="d6c2e-127">To see a list of retargeting changes that apply to your environment, select the .NET Framework version you're currently targeting and then the version you wish to migrate to:</span></span>

[!INCLUDE[versionselector](../../../includes/migration-guide/retargeting/versionselector.md)]

## <a name="impact-classification"></a><span data-ttu-id="d6c2e-128">Klasifikace dopadů</span><span class="sxs-lookup"><span data-stu-id="d6c2e-128">Impact classification</span></span>

<span data-ttu-id="d6c2e-129">V tématech, která popisují změny za běhu a retargeting, například [Změny retargetingu pro migraci z 4.7.2 na 4.8](retargeting/4.7.2-4.8.md), jsou jednotlivé položky klasifikovány podle očekávaného dopadu takto:</span><span class="sxs-lookup"><span data-stu-id="d6c2e-129">In the topics that describe runtime and retargeting changes, for example, [Retargeting changes for migrating from 4.7.2 to 4.8](retargeting/4.7.2-4.8.md), individual items are classified by their expected impact as follows:</span></span>

<span data-ttu-id="d6c2e-130">**Hlavní**</span><span class="sxs-lookup"><span data-stu-id="d6c2e-130">**Major**</span></span>\
<span data-ttu-id="d6c2e-131">Významná změna, která ovlivňuje velký počet aplikací nebo která vyžaduje podstatnou změnu kódu.</span><span class="sxs-lookup"><span data-stu-id="d6c2e-131">A significant change that affects a large number of apps or that requires substantial modification of code.</span></span>

<span data-ttu-id="d6c2e-132">**Menší**</span><span class="sxs-lookup"><span data-stu-id="d6c2e-132">**Minor**</span></span>\
<span data-ttu-id="d6c2e-133">Změna, která má vliv na malý počet aplikací nebo která vyžaduje menší úpravy kódu.</span><span class="sxs-lookup"><span data-stu-id="d6c2e-133">A change that affects a small number of apps or that requires minor modification of code.</span></span>

<span data-ttu-id="d6c2e-134">**Pouzdro edge**</span><span class="sxs-lookup"><span data-stu-id="d6c2e-134">**Edge case**</span></span>\
<span data-ttu-id="d6c2e-135">Změna, která ovlivňuje aplikace ve velmi specifických scénářích, které nejsou běžné.</span><span class="sxs-lookup"><span data-stu-id="d6c2e-135">A change that affects apps under very specific scenarios that are not common.</span></span>

<span data-ttu-id="d6c2e-136">**Průhledné**</span><span class="sxs-lookup"><span data-stu-id="d6c2e-136">**Transparent**</span></span>\
<span data-ttu-id="d6c2e-137">Změna, která nemá žádný znatelný vliv na vývojáře nebo uživatele aplikace.</span><span class="sxs-lookup"><span data-stu-id="d6c2e-137">A change that has no noticeable effect on the app's developer or user.</span></span> <span data-ttu-id="d6c2e-138">Z důvodu této změny by aplikace neměla vyžadovat úpravy.</span><span class="sxs-lookup"><span data-stu-id="d6c2e-138">The app should not require modification because of this change.</span></span>

## <a name="see-also"></a><span data-ttu-id="d6c2e-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6c2e-139">See also</span></span>

- [<span data-ttu-id="d6c2e-140">Verze a závislosti</span><span class="sxs-lookup"><span data-stu-id="d6c2e-140">Versions and dependencies</span></span>](versions-and-dependencies.md)
- [<span data-ttu-id="d6c2e-141">Co je nového</span><span class="sxs-lookup"><span data-stu-id="d6c2e-141">What's new</span></span>](../whats-new/index.md)
- [<span data-ttu-id="d6c2e-142">Co je zastaralé</span><span class="sxs-lookup"><span data-stu-id="d6c2e-142">What's obsolete</span></span>](../whats-new/whats-obsolete.md)
