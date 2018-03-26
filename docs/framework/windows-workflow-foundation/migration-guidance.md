---
title: Pokyny pro migraci
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e04c63754960dca44558d888b8ce357220562ea7
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2018
---
# <a name="migration-guidance"></a><span data-ttu-id="a0806-102">Pokyny pro migraci</span><span class="sxs-lookup"><span data-stu-id="a0806-102">Migration Guidance</span></span>
<span data-ttu-id="a0806-103">V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], společnost Microsoft vydává druhý hlavní verzi [!INCLUDE[wf](../../../includes/wf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a0806-103">In the [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], Microsoft is releasing the second major version of [!INCLUDE[wf](../../../includes/wf-md.md)].</span></span> [!INCLUDE[wf1](../../../includes/wf1-md.md)]<span data-ttu-id="a0806-104"> byla vydána v [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] (to zahrnuté typy v oborech názvů System.Workflow.\* barvy; nyní označuje jako WF3) a rozšířené v [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a0806-104"> was released in [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] (this included the types in the System.Workflow.\* namespaces; now referred to as WF3) and enhanced in [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span></span> <span data-ttu-id="a0806-105">WF3 je také součástí [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], ale existuje existuje souběžně s novou technologií pracovního postupu (typy v systém.\* obory názvů; označuje jako WF4).</span><span class="sxs-lookup"><span data-stu-id="a0806-105">WF3 is also part of the [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], but it exists there alongside new workflow technology (the types in the System.Activities.\* namespaces; referred to as WF4).</span></span> <span data-ttu-id="a0806-106">Při určování, kdy se mají přijmout WF4, je potřeba nejdřív rozpoznat řídit načasování.</span><span class="sxs-lookup"><span data-stu-id="a0806-106">When considering when to adopt WF4, it is important to first recognize that you control the timing.</span></span>  
  
-   <span data-ttu-id="a0806-107">WF3 je plně podporovaný součástí [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a0806-107">WF3 is a fully supported part of the [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span></span>  
  
-   <span data-ttu-id="a0806-108">WF3 aplikace spustit na [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] bez úprav a dále plně podporována.</span><span class="sxs-lookup"><span data-stu-id="a0806-108">WF3 applications run on the [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] without modification and continue to be fully supported.</span></span>  
  
-   <span data-ttu-id="a0806-109">Můžete vytvořit nové aplikace WF3 a existující aplikace lze upravit v [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] a jsou plně podporovány.</span><span class="sxs-lookup"><span data-stu-id="a0806-109">New WF3 applications can be created and your existing applications can be edited in [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] and are fully supported.</span></span>  
  
 <span data-ttu-id="a0806-110">Proto je rozhodnutí o přijetí rozhraní .NET Framework 4 odpojené od vaše rozhodnutí pro přesun do WF4 (System.Activities.*) z WF3 (System.Workflow.\*).</span><span class="sxs-lookup"><span data-stu-id="a0806-110">Thus, the decision to adopt the .NET Framework 4 is decoupled from your decision to move to WF4 (System.Activities.*) from WF3 (System.Workflow.\*).</span></span> <span data-ttu-id="a0806-111">Toto téma obsahuje odkazy na pokyny k migraci WF, které obsahuje informace o práci s WF3 a WF4.</span><span class="sxs-lookup"><span data-stu-id="a0806-111">This topic provides links to WF migration guidance that provides information about working with WF3 and WF4.</span></span>  
  
## <a name="wf-migration-whitepapers-and-cookbooks"></a><span data-ttu-id="a0806-112">Dokumenty White paper Migrace WF a Cookbooks</span><span class="sxs-lookup"><span data-stu-id="a0806-112">WF Migration Whitepapers and Cookbooks</span></span>  
 <span data-ttu-id="a0806-113">[Přehled migrace WF](http://go.microsoft.com/fwlink/?LinkId=153873) tématu poskytuje komplexní přehled o vztah mezi WF3 a WF4 a migrace strategie.</span><span class="sxs-lookup"><span data-stu-id="a0806-113">The [WF Migration Overview](http://go.microsoft.com/fwlink/?LinkId=153873) topic provides a broad overview of the relationship between WF3 and WF4 and migration strategies.</span></span> <span data-ttu-id="a0806-114">Témata Průvodce vyhledáváním, přejdete na konkrétní témata.</span><span class="sxs-lookup"><span data-stu-id="a0806-114">Companion topics drill into specific topics.</span></span>  
  
 [<span data-ttu-id="a0806-115">Přehled migrace WF</span><span class="sxs-lookup"><span data-stu-id="a0806-115">WF Migration Overview</span></span>](http://go.microsoft.com/fwlink/?LinkId=153873)  
 <span data-ttu-id="a0806-116">Popisuje vztah mezi WF3 a WF4 a volby, měli byste jako uživatel nebo potenciální uživatel technologie pracovního postupu v rozhraní .NET 4.</span><span class="sxs-lookup"><span data-stu-id="a0806-116">Describes the relationship between WF3 and WF4, and the choices you have as a user or a potential user of workflow technology in .NET 4.</span></span>  
  
 [<span data-ttu-id="a0806-117">WF migrace: Osvědčené postupy pro vývoj WF3</span><span class="sxs-lookup"><span data-stu-id="a0806-117">WF Migration: Best Practices for WF3 Development</span></span>](http://go.microsoft.com/fwlink/?LinkId=153852)  
 <span data-ttu-id="a0806-118">Popisuje, jak navrhnout WF3 artefakty, mohou být snadněji migrovány do WF4.</span><span class="sxs-lookup"><span data-stu-id="a0806-118">Discusses how to design WF3 artifacts so they can be more easily migrated to WF4.</span></span>  
  
 [<span data-ttu-id="a0806-119">WF pokyny: pravidla</span><span class="sxs-lookup"><span data-stu-id="a0806-119">WF Guidance: Rules</span></span>](http://go.microsoft.com/fwlink/?LinkId=153854)  
 <span data-ttu-id="a0806-120">Popisuje, jak převést související pravidla investice předat do [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] řešení.</span><span class="sxs-lookup"><span data-stu-id="a0806-120">Discusses how to bring rules-related investments forward into [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] solutions.</span></span>  
  
 [<span data-ttu-id="a0806-121">WF pokyny: Stav počítače</span><span class="sxs-lookup"><span data-stu-id="a0806-121">WF Guidance: State Machine</span></span>](http://go.microsoft.com/fwlink/?LinkId=153855)  
 <span data-ttu-id="a0806-122">Popisuje tok řízení WF4 modelování chybí aktivitu stav počítače.</span><span class="sxs-lookup"><span data-stu-id="a0806-122">Discusses WF4 control flow modeling in the absence of a State-Machine activity.</span></span>  
  
 <span data-ttu-id="a0806-123">Všimněte si, že v tomto návodu se aplikuje jenom na projekty workflow, které cílí na rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a0806-123">Note that this guidance only applies to workflow projects that target .NET Framework 4.</span></span> <span data-ttu-id="a0806-124">Pracovní postupy stavu počítače byly přidány v rozhraní .NET 4.0.1 s vydáním Platform Update 1 a byly součástí rozhraní .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="a0806-124">State Machine workflows were added in .NET 4.0.1 with the release of Platform Update 1, and were included as part of .NET Framework 4.5.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="a0806-125"> stav počítače pracovních postupů v rozhraní .NET 4.0.1 - 4.0.3 a rozhraní .NET Framework 4.5, najdete v části [aktualizace 4.0.1 pro rozhraní Microsoft .NET Framework 4 funkce](http://msdn.microsoft.com/library/de3297bd-c3e1-4126-95be-2ed7fe2a98fc) a [stavu počítače pracovních](../../../docs/framework/windows-workflow-foundation/state-machine-workflows.md).</span><span class="sxs-lookup"><span data-stu-id="a0806-125"> state machine workflows in .NET 4.0.1 - 4.0.3 and .NET Framework 4.5, see [Update 4.0.1 for Microsoft .NET Framework 4 Features](http://msdn.microsoft.com/library/de3297bd-c3e1-4126-95be-2ed7fe2a98fc) and [State Machine Workflows](../../../docs/framework/windows-workflow-foundation/state-machine-workflows.md).</span></span>  
  
 [<span data-ttu-id="a0806-126">WF kuchařka migrace: Vlastní aktivity</span><span class="sxs-lookup"><span data-stu-id="a0806-126">WF Migration Cookbook: Custom Activities</span></span>](http://go.microsoft.com/fwlink/?LinkId=153856)  
 <span data-ttu-id="a0806-127">Poskytuje pokyny pro přepracování WF3 vlastní aktivity na WF4 a příklady.</span><span class="sxs-lookup"><span data-stu-id="a0806-127">Provides examples and instructions for redesigning WF3 custom activities on WF4.</span></span>  
  
 [<span data-ttu-id="a0806-128">WF kuchařka migrace: Pokročilé vlastní aktivity</span><span class="sxs-lookup"><span data-stu-id="a0806-128">WF Migration Cookbook: Advanced Custom Activities</span></span>](http://go.microsoft.com/fwlink/?LinkId=275560)  
 <span data-ttu-id="a0806-129">Obsahuje pokyny pro přepracování pokročilé vlastní aktivity WF3, které používají fronty WF3 a plán podřízené aktivity jako WF4 vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="a0806-129">Provides guidance for redesigning advanced WF3 custom activities that use WF3 queues and schedule child activities as WF4 custom activities.</span></span>  
  
 [<span data-ttu-id="a0806-130">WF migrace kuchařka: pracovní postupy</span><span class="sxs-lookup"><span data-stu-id="a0806-130">WF Migration Cookbook: Workflows</span></span>](http://go.microsoft.com/fwlink/?LinkId=153858)  
 <span data-ttu-id="a0806-131">Poskytuje pokyny pro přepracování WF3 pracovních postupů na WF4 a příklady.</span><span class="sxs-lookup"><span data-stu-id="a0806-131">Provides examples and instructions for redesigning WF3 workflows on WF4.</span></span>  
  
 [<span data-ttu-id="a0806-132">WF kuchařka migrace: Hostování pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="a0806-132">WF Migration Cookbook: Workflow Hosting</span></span>](http://go.microsoft.com/fwlink/?LinkId=275561)  
 <span data-ttu-id="a0806-133">Obsahuje pokyny pro přepracování WF3 hostování kód jako WF4 hostování kódu.</span><span class="sxs-lookup"><span data-stu-id="a0806-133">Provides guidance for redesigning WF3 hosting code as WF4 hosting code.</span></span> <span data-ttu-id="a0806-134">Cílem je tak, aby pokrývalo hlavní rozdíly ve hostování mezi WF3 a WF4 pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a0806-134">The goal is to cover the key differences in workflow hosting between WF3 and WF4.</span></span>  
  
 [<span data-ttu-id="a0806-135">WF kuchařka migrace: Sledování pracovní postup</span><span class="sxs-lookup"><span data-stu-id="a0806-135">WF Migration Cookbook: Workflow Tracking</span></span>](http://go.microsoft.com/fwlink/?LinkId=275562)  
 <span data-ttu-id="a0806-136">Obsahuje pokyny pro přepracování WF3 sledování kódu a konfigurace pomocí ekvivalentní WF4 sledování kódu a konfigurace.</span><span class="sxs-lookup"><span data-stu-id="a0806-136">Provides guidance for redesigning WF3 tracking code and configuration using equivalent WF4 tracking code and configuration.</span></span>  
  
 [<span data-ttu-id="a0806-137">WF pokyny: Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="a0806-137">WF Guidance: Workflow Services</span></span>](http://go.microsoft.com/fwlink/?LinkId=275564)  
 <span data-ttu-id="a0806-138">Poskytuje příklad orientované podrobné pokyny pro pracovní postupy, které implementují Windows Communication Foundation (WCF) webové služby (obvykle označuje jako služeb pracovních postupů) vytvořené v WF3 použití WF4, pro běžné scénáře pro out-of-box přepracování aktivity.</span><span class="sxs-lookup"><span data-stu-id="a0806-138">Provides example-oriented step-by-step instructions for redesigning workflows that implement Windows Communication Foundation (WCF) web services (commonly referred to as workflow services) created in WF3 to use WF4, for common scenarios for out-of-box activities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0806-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0806-139">See Also</span></span>  
 <xref:System.Activities.Statements.Interop>
