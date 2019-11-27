---
title: Pokyny pro migraci
ms.date: 03/30/2017
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
ms.openlocfilehash: 8abc241331b3d322763ffd67b41ff676ebc680fb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283198"
---
# <a name="migration-guidance"></a><span data-ttu-id="f5849-102">Pokyny pro migraci</span><span class="sxs-lookup"><span data-stu-id="f5849-102">Migration Guidance</span></span>

<span data-ttu-id="f5849-103">V .NET Framework 4 Společnost Microsoft uvolňuje druhou hlavní verzi programovací model Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="f5849-103">In the .NET Framework 4, Microsoft is releasing the second major version of Windows Workflow Foundation (WF).</span></span> [!INCLUDE[wf1](../../../includes/wf1-md.md)] <span data-ttu-id="f5849-104">byla vydána v WinFX (to zahrnuje typy v oborech názvů System. Workflow.\*, nyní označované jako WF3) a vylepšené v .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="f5849-104">was released in WinFX (this included the types in the System.Workflow.\* namespaces; now referred to as WF3) and enhanced in .NET Framework 3.5.</span></span> <span data-ttu-id="f5849-105">WF3 je také součástí .NET Framework 4, ale existuje společně s novou technologií pracovního postupu (typy v oborech názvů System. Activities.\*, označované jako WF4).</span><span class="sxs-lookup"><span data-stu-id="f5849-105">WF3 is also part of the .NET Framework 4, but it exists there alongside new workflow technology (the types in the System.Activities.\* namespaces; referred to as WF4).</span></span> <span data-ttu-id="f5849-106">Při zvažování, kdy přijmout WF4, je důležité nejprve rozpoznat, že budete řídit časování.</span><span class="sxs-lookup"><span data-stu-id="f5849-106">When considering when to adopt WF4, it is important to first recognize that you control the timing.</span></span>  
  
- <span data-ttu-id="f5849-107">WF3 je plně podporovaná součást .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f5849-107">WF3 is a fully supported part of the .NET Framework 4.</span></span>  
  
- <span data-ttu-id="f5849-108">Aplikace WF3 běží na .NET Framework 4 bez úprav a nadále jsou plně podporované.</span><span class="sxs-lookup"><span data-stu-id="f5849-108">WF3 applications run on the .NET Framework 4 without modification and continue to be fully supported.</span></span>  
  
- <span data-ttu-id="f5849-109">Je možné vytvořit nové aplikace WF3 a stávající aplikace lze upravovat v aplikaci Visual Studio 2012 a jsou plně podporovány.</span><span class="sxs-lookup"><span data-stu-id="f5849-109">New WF3 applications can be created and your existing applications can be edited in Visual Studio 2012 and are fully supported.</span></span>  
  
 <span data-ttu-id="f5849-110">Proto se rozhodnutí o přijetí .NET Framework 4 oddělí od vašeho rozhodnutí o přesun do WF4 (System. Activities.\*) z WF3 (System. Workflow.\*).</span><span class="sxs-lookup"><span data-stu-id="f5849-110">Thus, the decision to adopt the .NET Framework 4 is decoupled from your decision to move to WF4 (System.Activities.\*) from WF3 (System.Workflow.\*).</span></span> <span data-ttu-id="f5849-111">Toto téma obsahuje odkazy na pokyny k migraci WF, které poskytují informace o práci s WF3 a WF4.</span><span class="sxs-lookup"><span data-stu-id="f5849-111">This topic provides links to WF migration guidance that provides information about working with WF3 and WF4.</span></span>  
  
## <a name="wf-migration-whitepapers-and-cookbooks"></a><span data-ttu-id="f5849-112">Dokumenty White paper k migraci WF a návody</span><span class="sxs-lookup"><span data-stu-id="f5849-112">WF Migration Whitepapers and Cookbooks</span></span>  
 <span data-ttu-id="f5849-113">Téma [Přehled migrace WF](https://go.microsoft.com/fwlink/?LinkId=153873) poskytuje širokou škálu vztahů mezi WF3 a WF4 a strategiemi migrace.</span><span class="sxs-lookup"><span data-stu-id="f5849-113">The [WF Migration Overview](https://go.microsoft.com/fwlink/?LinkId=153873) topic provides a broad overview of the relationship between WF3 and WF4 and migration strategies.</span></span> <span data-ttu-id="f5849-114">Doprovodná témata se podrobněji přecházení na konkrétní témata.</span><span class="sxs-lookup"><span data-stu-id="f5849-114">Companion topics drill into specific topics.</span></span>  
  
 [<span data-ttu-id="f5849-115">Přehled migrace WF</span><span class="sxs-lookup"><span data-stu-id="f5849-115">WF Migration Overview</span></span>](https://go.microsoft.com/fwlink/?LinkId=153873)  
 <span data-ttu-id="f5849-116">Popisuje vztah mezi WF3 a WF4 a možnostmi, které máte jako uživatel nebo potenciální uživatel technologie pracovního postupu v rozhraní .NET 4.</span><span class="sxs-lookup"><span data-stu-id="f5849-116">Describes the relationship between WF3 and WF4, and the choices you have as a user or a potential user of workflow technology in .NET 4.</span></span>  
  
 [<span data-ttu-id="f5849-117">Migrace WF: osvědčené postupy pro vývoj WF3</span><span class="sxs-lookup"><span data-stu-id="f5849-117">WF Migration: Best Practices for WF3 Development</span></span>](https://go.microsoft.com/fwlink/?LinkId=153852)  
 <span data-ttu-id="f5849-118">Popisuje, jak navrhovat artefakty WF3, aby je bylo možné snadněji migrovat na WF4.</span><span class="sxs-lookup"><span data-stu-id="f5849-118">Discusses how to design WF3 artifacts so they can be more easily migrated to WF4.</span></span>  
  
 [<span data-ttu-id="f5849-119">Pokyny k WF: pravidla</span><span class="sxs-lookup"><span data-stu-id="f5849-119">WF Guidance: Rules</span></span>](https://go.microsoft.com/fwlink/?LinkId=153854)  
 <span data-ttu-id="f5849-120">Popisuje, jak přenést investice související s pravidly do řešení .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f5849-120">Discusses how to bring rules-related investments forward into .NET Framework 4 solutions.</span></span>  
  
 [<span data-ttu-id="f5849-121">Návod k WF: Stavový počítač</span><span class="sxs-lookup"><span data-stu-id="f5849-121">WF Guidance: State Machine</span></span>](https://go.microsoft.com/fwlink/?LinkId=153855)  
 <span data-ttu-id="f5849-122">Popisuje modelování toku řízení WF4 při absenci aktivity stavového počítače.</span><span class="sxs-lookup"><span data-stu-id="f5849-122">Discusses WF4 control flow modeling in the absence of a State-Machine activity.</span></span>  
  
 <span data-ttu-id="f5849-123">Upozorňujeme, že tyto pokyny platí jenom pro projekty pracovního postupu, které cílí na .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f5849-123">Note that this guidance only applies to workflow projects that target .NET Framework 4.</span></span> <span data-ttu-id="f5849-124">Pracovní postupy stavového počítače byly přidány do .NET 4.0.1 s vydáním aktualizace platformy 1 a byly zahrnuty jako součást .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="f5849-124">State Machine workflows were added in .NET 4.0.1 with the release of Platform Update 1, and were included as part of .NET Framework 4.5.</span></span> <span data-ttu-id="f5849-125">Další informace o pracovních postupech stavových počítačů v .NET 4.0.1-4.0.3 a .NET Framework 4,5 najdete v tématu [aktualizace 4.0.1 pro součásti Microsoft .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hh290669(v=vs.100)) a [pracovní postupy stavového počítače](state-machine-workflows.md).</span><span class="sxs-lookup"><span data-stu-id="f5849-125">For more information about state machine workflows in .NET 4.0.1 - 4.0.3 and .NET Framework 4.5, see [Update 4.0.1 for Microsoft .NET Framework 4 Features](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hh290669(v=vs.100)) and [State Machine Workflows](state-machine-workflows.md).</span></span>  
  
 [<span data-ttu-id="f5849-126">Migrace WF kuchařka: vlastní aktivity</span><span class="sxs-lookup"><span data-stu-id="f5849-126">WF Migration Cookbook: Custom Activities</span></span>](https://go.microsoft.com/fwlink/?LinkId=153856)  
 <span data-ttu-id="f5849-127">Poskytuje příklady a pokyny pro změnu návrhu WF3 vlastních aktivit na WF4.</span><span class="sxs-lookup"><span data-stu-id="f5849-127">Provides examples and instructions for redesigning WF3 custom activities on WF4.</span></span>  
  
 [<span data-ttu-id="f5849-128">Migrace WF kuchařka: pokročilé vlastní aktivity</span><span class="sxs-lookup"><span data-stu-id="f5849-128">WF Migration Cookbook: Advanced Custom Activities</span></span>](https://go.microsoft.com/fwlink/?LinkId=275560)  
 <span data-ttu-id="f5849-129">Poskytuje pokyny pro přenávrh pokročilých WF3 vlastních aktivit, které používají fronty WF3 a naplánování podřízených aktivit jako WF4 vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="f5849-129">Provides guidance for redesigning advanced WF3 custom activities that use WF3 queues and schedule child activities as WF4 custom activities.</span></span>  
  
 [<span data-ttu-id="f5849-130">Migrace WF kuchařka: pracovní postupy</span><span class="sxs-lookup"><span data-stu-id="f5849-130">WF Migration Cookbook: Workflows</span></span>](https://go.microsoft.com/fwlink/?LinkId=153858)  
 <span data-ttu-id="f5849-131">Poskytuje příklady a pokyny pro přepracování pracovních postupů WF3 v WF4.</span><span class="sxs-lookup"><span data-stu-id="f5849-131">Provides examples and instructions for redesigning WF3 workflows on WF4.</span></span>  
  
 [<span data-ttu-id="f5849-132">Migrace WF kuchařka: Hostování pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="f5849-132">WF Migration Cookbook: Workflow Hosting</span></span>](https://go.microsoft.com/fwlink/?LinkId=275561)  
 <span data-ttu-id="f5849-133">Poskytuje pokyny pro přepracování kódu hostování WF3 jako kódu hostování WF4.</span><span class="sxs-lookup"><span data-stu-id="f5849-133">Provides guidance for redesigning WF3 hosting code as WF4 hosting code.</span></span> <span data-ttu-id="f5849-134">Cílem je pokrýt klíčové rozdíly v pracovních postupech hostujících mezi WF3 a WF4.</span><span class="sxs-lookup"><span data-stu-id="f5849-134">The goal is to cover the key differences in workflow hosting between WF3 and WF4.</span></span>  
  
 [<span data-ttu-id="f5849-135">Migrace WF kuchařka: sledování pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="f5849-135">WF Migration Cookbook: Workflow Tracking</span></span>](https://go.microsoft.com/fwlink/?LinkId=275562)  
 <span data-ttu-id="f5849-136">Poskytuje pokyny pro změnu návrhu kódu sledování WF3 a konfigurace pomocí ekvivalentního kódu a konfigurace sledování WF4.</span><span class="sxs-lookup"><span data-stu-id="f5849-136">Provides guidance for redesigning WF3 tracking code and configuration using equivalent WF4 tracking code and configuration.</span></span>  
  
 [<span data-ttu-id="f5849-137">Pokyny k WF: služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="f5849-137">WF Guidance: Workflow Services</span></span>](https://go.microsoft.com/fwlink/?LinkId=275564)  
 <span data-ttu-id="f5849-138">Poskytuje příklad podrobných pokynů pro přepracování pracovních postupů, které implementují webové služby Windows Communication Foundation (WCF), které jsou vytvořené v WF3 k použití WF4, pro běžné scénáře pro předem připravené služby. soutěž.</span><span class="sxs-lookup"><span data-stu-id="f5849-138">Provides example-oriented step-by-step instructions for redesigning workflows that implement Windows Communication Foundation (WCF) web services (commonly referred to as workflow services) created in WF3 to use WF4, for common scenarios for out-of-box activities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5849-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f5849-139">See also</span></span>

- <xref:System.Activities.Statements.Interop>
