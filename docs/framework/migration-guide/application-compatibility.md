---
title: Spuštění a změna cílení na změny – .NET Framework
ms.date: 10/29/2019
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
ms.openlocfilehash: c46f781d495b87a4f24e77935df7c4814c8567ae
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73196694"
---
# <a name="application-compatibility-in-the-net-framework"></a><span data-ttu-id="f5e68-102">Kompatibilita aplikací v .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f5e68-102">Application compatibility in the .NET Framework</span></span>

<span data-ttu-id="f5e68-103">Kompatibilita je důležitým cílem každé verze rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="f5e68-103">Compatibility is an important goal of each .NET release.</span></span> <span data-ttu-id="f5e68-104">Kompatibilita zajišťuje, že každá verze je doplňková, takže předchozí verze budou fungovat i nadále.</span><span class="sxs-lookup"><span data-stu-id="f5e68-104">Compatibility ensures that each version is additive, so previous versions will continue to work.</span></span> <span data-ttu-id="f5e68-105">Na druhé straně změny předchozí funkce (například pro zlepšení výkonu, řešení potíží se zabezpečením nebo opravy chyb) mohou způsobit problémy s kompatibilitou v existujícím kódu nebo v existujících aplikacích, které jsou spuštěny v novější verzi.</span><span class="sxs-lookup"><span data-stu-id="f5e68-105">On the other hand, changes to previous functionality (for example, to improve performance, address security issues, or fix bugs) can cause compatibility problems in existing code or existing applications that run under a later version.</span></span>

<span data-ttu-id="f5e68-106">Každá aplikace cílí na konkrétní verzi .NET Framework podle:</span><span class="sxs-lookup"><span data-stu-id="f5e68-106">Each app targets a specific version of the .NET Framework by:</span></span>

- <span data-ttu-id="f5e68-107">Definování cílové architektury v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f5e68-107">Defining a target framework in Visual Studio.</span></span>
- <span data-ttu-id="f5e68-108">Určení cílové architektury v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="f5e68-108">Specifying the target framework in a project file.</span></span>
- <span data-ttu-id="f5e68-109">Použití <xref:System.Runtime.Versioning.TargetFrameworkAttribute> ke zdrojovému kódu.</span><span class="sxs-lookup"><span data-stu-id="f5e68-109">Applying a <xref:System.Runtime.Versioning.TargetFrameworkAttribute> to the source code.</span></span>

<span data-ttu-id="f5e68-110">Při migraci z jedné verze .NET Framework na jinou existují dva typy změn, které je třeba vzít v úvahu:</span><span class="sxs-lookup"><span data-stu-id="f5e68-110">When migrating from one version of the .NET Framework to another, there are two types of changes to consider:</span></span>

- [<span data-ttu-id="f5e68-111">Změny modulu runtime</span><span class="sxs-lookup"><span data-stu-id="f5e68-111">Runtime changes</span></span>](#runtime-changes)
- [<span data-ttu-id="f5e68-112">Změny cíle</span><span class="sxs-lookup"><span data-stu-id="f5e68-112">Retargeting changes</span></span>](#retargeting-changes)

## <a name="runtime-changes"></a><span data-ttu-id="f5e68-113">Změny modulu runtime</span><span class="sxs-lookup"><span data-stu-id="f5e68-113">Runtime changes</span></span>

<span data-ttu-id="f5e68-114">Problémy za běhu jsou ty, které vznikají při umístění nového modulu runtime do počítače a změny chování aplikace.</span><span class="sxs-lookup"><span data-stu-id="f5e68-114">Runtime issues are those that arise when a new runtime is placed on a machine and an app's behavior changes.</span></span> <span data-ttu-id="f5e68-115">Při spuštění v novější verzi, než je cílová, .NET Framework používá chování *quirked* k napodobování starší cílové verze.</span><span class="sxs-lookup"><span data-stu-id="f5e68-115">When running on a newer version than what was targeted, the .NET Framework uses *quirked* behavior to mimic the older targeted version.</span></span> <span data-ttu-id="f5e68-116">Aplikace běží na novější verzi, ale funguje jako v případě, že běží na starší verzi.</span><span class="sxs-lookup"><span data-stu-id="f5e68-116">The app runs on the newer version but acts as if it's running on the older version.</span></span> <span data-ttu-id="f5e68-117">Mnohé z problémů s kompatibilitou mezi verzemi .NET Framework jsou zmírnit prostřednictvím tohoto modelu quirking.</span><span class="sxs-lookup"><span data-stu-id="f5e68-117">Many of the compatibility issues between versions of the .NET Framework are mitigated through this quirking model.</span></span> <span data-ttu-id="f5e68-118">Například pokud byl binární soubor kompilován pro .NET Framework 4,0, ale běží na počítači s .NET Framework 4,5 nebo novějším, běží v .NET Framework 4,0 režim kompatibility.</span><span class="sxs-lookup"><span data-stu-id="f5e68-118">For example, if a binary was compiled for .NET Framework 4.0 but runs on a machine with .NET Framework 4.5 or later, it runs in .NET Framework 4.0 compatibility mode.</span></span> <span data-ttu-id="f5e68-119">To znamená, že mnoho změn v novější verzi nemá vliv na binární soubor.</span><span class="sxs-lookup"><span data-stu-id="f5e68-119">This means that many of the changes in the later version don't affect the binary.</span></span>

<span data-ttu-id="f5e68-120">Verze .NET Framework, na kterou aplikace cílí, je určena cílovou verzí záznamu pro doménu aplikace, ve které kód běží.</span><span class="sxs-lookup"><span data-stu-id="f5e68-120">The version of the .NET Framework that an application targets is determined by the target version of the entry assembly for the application domain that the code runs in.</span></span> <span data-ttu-id="f5e68-121">Všechna další sestavení načtená v této aplikační doméně cílí na verzi.</span><span class="sxs-lookup"><span data-stu-id="f5e68-121">All additional assemblies loaded in that application domain target that version.</span></span> <span data-ttu-id="f5e68-122">Například v případě spustitelného souboru je verze, kterou spustitelný soubor cílí, režim kompatibility všechna sestavení v dané doméně aplikace běží pod.</span><span class="sxs-lookup"><span data-stu-id="f5e68-122">For example, in the case of an executable, the version that the executable targets is the compatibility mode all assemblies in that application domain run under.</span></span>

<span data-ttu-id="f5e68-123">Pokud chcete zobrazit seznam změn za běhu, které se vztahují k vašemu prostředí, vyberte verzi .NET Framework, na kterou aktuálně cílíte, a pak verzi, na kterou chcete migrovat:</span><span class="sxs-lookup"><span data-stu-id="f5e68-123">To see a list of runtime changes that apply to your environment, select the .NET Framework version you're currently targeting and then the version you wish to migrate to:</span></span>

[!INCLUDE[versionselector](../../../includes/migration-guide/runtime/versionselector.md)]

## <a name="retargeting-changes"></a><span data-ttu-id="f5e68-124">Změny cíle</span><span class="sxs-lookup"><span data-stu-id="f5e68-124">Retargeting changes</span></span>

<span data-ttu-id="f5e68-125">Změny cíle se projeví, když se sestavení znovu zkompiluje do cíle novější verze.</span><span class="sxs-lookup"><span data-stu-id="f5e68-125">Retargeting changes are those that arise when an assembly is recompiled to target a newer version.</span></span> <span data-ttu-id="f5e68-126">Cílení na novější verzi znamená, že se sestavení výslovný do nových funkcí a také potenciální problémy s kompatibilitou pro staré funkce.</span><span class="sxs-lookup"><span data-stu-id="f5e68-126">Targeting a newer version means the assembly opts into the new features as well as potential compatibility issues for old features.</span></span>

<span data-ttu-id="f5e68-127">Pokud chcete zobrazit seznam změn cíle, které se vztahují k vašemu prostředí, vyberte verzi .NET Framework, na kterou aktuálně cílíte, a pak verzi, na kterou chcete migrovat:</span><span class="sxs-lookup"><span data-stu-id="f5e68-127">To see a list of retargeting changes that apply to your environment, select the .NET Framework version you're currently targeting and then the version you wish to migrate to:</span></span>

[!INCLUDE[versionselector](../../../includes/migration-guide/retargeting/versionselector.md)]

## <a name="impact-classification"></a><span data-ttu-id="f5e68-128">Klasifikace dopadu</span><span class="sxs-lookup"><span data-stu-id="f5e68-128">Impact classification</span></span>

<span data-ttu-id="f5e68-129">V tématech popisujících modul runtime a změny cíle, například změny [cíle pro migraci z 4.7.2 na 4,8](retargeting/4.7.2-4.8.md), jednotlivé položky jsou klasifikovány podle očekávaného dopadu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f5e68-129">In the topics that describe runtime and retargeting changes, for example, [Retargeting changes for migrating from 4.7.2 to 4.8](retargeting/4.7.2-4.8.md), individual items are classified by their expected impact as follows:</span></span>

<span data-ttu-id="f5e68-130">**Hlavní** </span><span class="sxs-lookup"><span data-stu-id="f5e68-130">**Major**</span></span>\
<span data-ttu-id="f5e68-131">Významná změna, která má vliv na velký počet aplikací nebo která vyžaduje podstatnou úpravu kódu.</span><span class="sxs-lookup"><span data-stu-id="f5e68-131">A significant change that affects a large number of apps or that requires substantial modification of code.</span></span>

<span data-ttu-id="f5e68-132">**Vedlejší**</span><span class="sxs-lookup"><span data-stu-id="f5e68-132">**Minor**</span></span>\
<span data-ttu-id="f5e68-133">Změna, která má vliv na malý počet aplikací nebo které vyžadují menší úpravu kódu.</span><span class="sxs-lookup"><span data-stu-id="f5e68-133">A change that affects a small number of apps or that requires minor modification of code.</span></span>

<span data-ttu-id="f5e68-134">\ **okrajového případu**</span><span class="sxs-lookup"><span data-stu-id="f5e68-134">**Edge case**\</span></span>
<span data-ttu-id="f5e68-135">Změna ovlivňující aplikace v rámci velmi specifických scénářů, které nejsou běžné.</span><span class="sxs-lookup"><span data-stu-id="f5e68-135">A change that affects apps under very specific scenarios that are not common.</span></span>

<span data-ttu-id="f5e68-136">**Transparentní**</span><span class="sxs-lookup"><span data-stu-id="f5e68-136">**Transparent**</span></span>\
<span data-ttu-id="f5e68-137">Změna, která nemá znatelný vliv na vývojáře nebo uživatele aplikace.</span><span class="sxs-lookup"><span data-stu-id="f5e68-137">A change that has no noticeable effect on the app's developer or user.</span></span> <span data-ttu-id="f5e68-138">Z důvodu této změny by aplikace neměla vyžadovat úpravy.</span><span class="sxs-lookup"><span data-stu-id="f5e68-138">The app should not require modification because of this change.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5e68-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f5e68-139">See also</span></span>

- [<span data-ttu-id="f5e68-140">Verze a závislosti</span><span class="sxs-lookup"><span data-stu-id="f5e68-140">Versions and dependencies</span></span>](versions-and-dependencies.md)
- [<span data-ttu-id="f5e68-141">Co je nového</span><span class="sxs-lookup"><span data-stu-id="f5e68-141">What's new</span></span>](../whats-new/index.md)
- [<span data-ttu-id="f5e68-142">Zastaralé položky</span><span class="sxs-lookup"><span data-stu-id="f5e68-142">What's obsolete</span></span>](../whats-new/whats-obsolete.md)
