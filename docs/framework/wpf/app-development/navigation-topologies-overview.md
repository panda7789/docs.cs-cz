---
title: "Přehled topologií navigace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- linear topology [WPF]
- fixed hierarchical topology [WPF]
- fixed linear topology [WPF]
- topologies [WPF]
- navigation topologies [WPF]
- dynamically-generated topology
ms.assetid: 5d5ee837-629a-4933-869a-186dc22ac43d
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d33eb42aded2ad9d6cd32ae5790470fa1b2dc935
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="navigation-topologies-overview"></a><span data-ttu-id="a7b35-102">Přehled topologií navigace</span><span class="sxs-lookup"><span data-stu-id="a7b35-102">Navigation Topologies Overview</span></span>
<span data-ttu-id="a7b35-103"><a name="introduction"></a>Tento přehled obsahuje úvod do topologie navigace v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a7b35-103"><a name="introduction"></a> This overview provides an introduction to navigation topologies in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span> <span data-ttu-id="a7b35-104">Tři běžné topologie navigační s ukázky, jsou následně popsané.</span><span class="sxs-lookup"><span data-stu-id="a7b35-104">Three common navigation topologies, with samples, are subsequently discussed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7b35-105">Než si přečtete v tomto tématu, měli byste se seznámit s ohledem na strukturovaných navigace v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pomocí stránky funkce.</span><span class="sxs-lookup"><span data-stu-id="a7b35-105">Before reading this topic, you should be familiar with the concept of structured navigation in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] using page functions.</span></span> <span data-ttu-id="a7b35-106">Další informace o obou těchto tématech najdete v tématu [strukturovaných navigační přehled](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a7b35-106">For more information on both of these topics, see [Structured Navigation Overview](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md).</span></span>  
  
 <span data-ttu-id="a7b35-107">Toto téma obsahuje následující oddíly:</span><span class="sxs-lookup"><span data-stu-id="a7b35-107">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="a7b35-108">Navigace topologie</span><span class="sxs-lookup"><span data-stu-id="a7b35-108">Navigation Topologies</span></span>](#Navigation_Topologies)  
  
-   [<span data-ttu-id="a7b35-109">Strukturované navigační topologie</span><span class="sxs-lookup"><span data-stu-id="a7b35-109">Structured Navigation Topologies</span></span>](#Structured_Navigation_Topologies)  
  
-   [<span data-ttu-id="a7b35-110">Navigace přes pevné lineární topologie</span><span class="sxs-lookup"><span data-stu-id="a7b35-110">Navigation over a Fixed Linear Topology</span></span>](#Navigation_over_a_Fixed_Linear_Topology)  
  
-   [<span data-ttu-id="a7b35-111">Dynamické navigační přes pevné hierarchické topologie</span><span class="sxs-lookup"><span data-stu-id="a7b35-111">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
-   [<span data-ttu-id="a7b35-112">Navigace v dynamicky generovaném topologie</span><span class="sxs-lookup"><span data-stu-id="a7b35-112">Navigation over a Dynamically Generated Topology</span></span>](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>   
## <a name="navigation-topologies"></a><span data-ttu-id="a7b35-113">Navigace topologie</span><span class="sxs-lookup"><span data-stu-id="a7b35-113">Navigation Topologies</span></span>  
 <span data-ttu-id="a7b35-114">V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], navigace se obvykle skládá z stránky (<xref:System.Windows.Controls.Page>) s hypertextové odkazy (<xref:System.Windows.Documents.Hyperlink>), přejděte k ostatním stránkám při kliknutí na.</span><span class="sxs-lookup"><span data-stu-id="a7b35-114">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], navigation typically consists of pages (<xref:System.Windows.Controls.Page>) with hyperlinks (<xref:System.Windows.Documents.Hyperlink>) that navigate to other pages when clicked.</span></span> <span data-ttu-id="a7b35-115">Jsou určeny stránek, které jsou přešli [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] (viz [Pack identifikátory URI v grafickém subsystému WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)).</span><span class="sxs-lookup"><span data-stu-id="a7b35-115">Pages that are navigated to are identified by [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] (see [Pack URIs in WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)).</span></span> <span data-ttu-id="a7b35-116">Vezměte v úvahu následující jednoduchý příklad, který ukazuje stránky, hypertextové odkazy, a [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="a7b35-116">Consider the following simple example that shows pages, hyperlinks, and [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]:</span></span>  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 <span data-ttu-id="a7b35-117">Tyto stránky jsou uspořádány do *navigační topologie* jejichž struktura je dáno jak přecházet mezi stránkami.</span><span class="sxs-lookup"><span data-stu-id="a7b35-117">These pages are arranged in a *navigation topology* whose structure is determined by how you can navigate between the pages.</span></span> <span data-ttu-id="a7b35-118">Tato topologie konkrétní navigace je vhodná v jednoduchého scénáře, i když navigační může vyžadovat komplexnější topologie, některé z nich může být definovaný jenom když aplikace běží.</span><span class="sxs-lookup"><span data-stu-id="a7b35-118">This particular navigation topology is suitable in simple scenarios, although navigation can require more complex topologies, some of which can only be defined when an application is running.</span></span>  
  
 <span data-ttu-id="a7b35-119">Toto téma popisuje tři běžné topologie navigace: *pevné lineární*, *pevné hierarchické*, a *dynamicky generovaném*.</span><span class="sxs-lookup"><span data-stu-id="a7b35-119">This topic covers three common navigation topologies: *fixed linear*, *fixed hierarchical*, and *dynamically generated*.</span></span> <span data-ttu-id="a7b35-120">Každé navigační topologii se demonstruje vzorku, který má [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] jako ten, který je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="a7b35-120">Each navigation topology is demonstrated with a sample that has a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] like the one that is shown in the following figure:</span></span>  
  
 <span data-ttu-id="a7b35-121">![Úloha stránky s datovými položkami](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure6.png "NavigationTopologyFigure6")</span><span class="sxs-lookup"><span data-stu-id="a7b35-121">![Task pages with data items](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure6.png "NavigationTopologyFigure6")</span></span>  
  
<a name="Structured_Navigation_Topologies"></a>   
## <a name="structured-navigation-topologies"></a><span data-ttu-id="a7b35-122">Strukturované navigační topologie</span><span class="sxs-lookup"><span data-stu-id="a7b35-122">Structured Navigation Topologies</span></span>  
 <span data-ttu-id="a7b35-123">Existují dva široké typy navigační topologie:</span><span class="sxs-lookup"><span data-stu-id="a7b35-123">There are two broad types of navigation topologies:</span></span>  
  
-   <span data-ttu-id="a7b35-124">**Pevné topologie**: definované při kompilaci a v době běhu se nemění.</span><span class="sxs-lookup"><span data-stu-id="a7b35-124">**Fixed Topology**: defined at compile time and does not change at run time.</span></span> <span data-ttu-id="a7b35-125">Opravené topologie jsou užitečné pro navigaci prostřednictvím pevné pořadí stránek v lineární nebo hierarchické pořadí.</span><span class="sxs-lookup"><span data-stu-id="a7b35-125">Fixed topologies are useful for navigation through a fixed sequence of pages in either a linear or hierarchical order.</span></span>  
  
-   <span data-ttu-id="a7b35-126">**Dynamické topologie**: definované v době běhu na základě informací, které jsou shromážděny od uživatele, aplikace nebo systému.</span><span class="sxs-lookup"><span data-stu-id="a7b35-126">**Dynamic Topology**: defined at run time based on input that is collected from the user, the application, or the system.</span></span> <span data-ttu-id="a7b35-127">Dynamické topologie je užitečný v případě stránky lze procházet v různých pořadí.</span><span class="sxs-lookup"><span data-stu-id="a7b35-127">Dynamic topologies are useful when pages can be navigated in different sequences.</span></span>  
  
 <span data-ttu-id="a7b35-128">Přestože je možné vytvořit navigační topologie pomocí stránek, ukázky použít stránku funkce, protože poskytují další podporu, který zjednodušuje podporu pro předávání a vrací data prostřednictvím stránky topologie.</span><span class="sxs-lookup"><span data-stu-id="a7b35-128">Although it is possible to create navigation topologies using pages, the samples use page functions because they provide additional support that simplifies support for passing and returning data through the pages of a topology.</span></span>  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>   
## <a name="navigation-over-a-fixed-linear-topology"></a><span data-ttu-id="a7b35-129">Navigace přes pevné lineární topologie</span><span class="sxs-lookup"><span data-stu-id="a7b35-129">Navigation over a Fixed Linear Topology</span></span>  
 <span data-ttu-id="a7b35-130">Pevné lineární topologie je podobná struktuře průvodce, který má jeden nebo více stránek průvodce, které jsou navigaci v pevné pořadí.</span><span class="sxs-lookup"><span data-stu-id="a7b35-130">A fixed linear topology is analogous to the structure of a wizard that has one or more wizard pages that are navigated in a fixed sequence.</span></span> <span data-ttu-id="a7b35-131">Následující obrázek ukazuje základní strukturu a toku průvodce s pevnou lineární topologií.</span><span class="sxs-lookup"><span data-stu-id="a7b35-131">The following figure shows the high-level structure and flow of a wizard with a fixed linear topology.</span></span>  
  
 <span data-ttu-id="a7b35-132">![Diagram topologie pro navigační](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure1.png "NavigationTopologyFigure1")</span><span class="sxs-lookup"><span data-stu-id="a7b35-132">![Navigation topology diagram](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure1.png "NavigationTopologyFigure1")</span></span>  
  
 <span data-ttu-id="a7b35-133">Typické chování pro navigaci přes pevné lineární topologie zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="a7b35-133">The typical behaviors for navigating over a fixed linear topology include the following:</span></span>  
  
-   <span data-ttu-id="a7b35-134">Navigace na stránce volání Spouštěče stránku, která inicializuje průvodce a přejde na první stránce průvodce.</span><span class="sxs-lookup"><span data-stu-id="a7b35-134">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="a7b35-135">Na stránce Spouštěče ( [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-menší <xref:System.Windows.Navigation.PageFunction%601>) není vyžadována, protože volání stránky můžete volat přímo na první stránku průvodce.</span><span class="sxs-lookup"><span data-stu-id="a7b35-135">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="a7b35-136">Pomocí stránky Spouštěče, však může zjednodušit inicializace průvodce, zvlášť pokud je komplexní inicializace.</span><span class="sxs-lookup"><span data-stu-id="a7b35-136">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
-   <span data-ttu-id="a7b35-137">Uživatelé mohou přecházet mezi stránkami pomocí zpět a předat dál tlačítka (nebo hypertextové odkazy).</span><span class="sxs-lookup"><span data-stu-id="a7b35-137">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
-   <span data-ttu-id="a7b35-138">Uživatelé mohou přecházet mezi stránkami pomocí deníku.</span><span class="sxs-lookup"><span data-stu-id="a7b35-138">Users can navigate between pages using the journal.</span></span>  
  
-   <span data-ttu-id="a7b35-139">Uživatele můžete ukončit průvodce z kterékoli stránce průvodce klepnutím na tlačítko Storno.</span><span class="sxs-lookup"><span data-stu-id="a7b35-139">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
-   <span data-ttu-id="a7b35-140">Uživatelé můžou přijmout Průvodce na poslední stránce průvodce klepnutím na tlačítko Dokončit.</span><span class="sxs-lookup"><span data-stu-id="a7b35-140">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
-   <span data-ttu-id="a7b35-141">Pokud zrušení průvodce Průvodce vrátí odpovídající výsledek a nevrátí žádná data.</span><span class="sxs-lookup"><span data-stu-id="a7b35-141">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
-   <span data-ttu-id="a7b35-142">Když uživatel přijme podmínky průvodce, Průvodce vrátí odpovídající výsledek a vrátí data, která se shromažďují.</span><span class="sxs-lookup"><span data-stu-id="a7b35-142">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
-   <span data-ttu-id="a7b35-143">Až průvodce dokončí (přijímat nebo došlo ke zrušení), stránek, které tvoří průvodce se odeberou z deníku.</span><span class="sxs-lookup"><span data-stu-id="a7b35-143">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="a7b35-144">Díky tomu každou instanci Průvodce izolovaných, aby se předešlo potenciální data nebo anomálií stavu.</span><span class="sxs-lookup"><span data-stu-id="a7b35-144">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>   
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a><span data-ttu-id="a7b35-145">Dynamické navigační přes pevné hierarchické topologie</span><span class="sxs-lookup"><span data-stu-id="a7b35-145">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>  
 <span data-ttu-id="a7b35-146">V některých aplikacích stránky procházení do dvou nebo více dalších stránek, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="a7b35-146">In some applications, pages allow navigation to two or more other pages, as shown in the following figure.</span></span>  
  
 <span data-ttu-id="a7b35-147">![Na stránce, který můžete přejít na více stránkách](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure2.png "NavigationTopologyFigure2")</span><span class="sxs-lookup"><span data-stu-id="a7b35-147">![A page that can navigate to multiple pages](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure2.png "NavigationTopologyFigure2")</span></span>  
  
 <span data-ttu-id="a7b35-148">Tato struktura je známý jako pevné hierarchické topologie a pořadí, ve kterém je provázán hierarchii je často dáno v době běhu aplikace nebo uživatele.</span><span class="sxs-lookup"><span data-stu-id="a7b35-148">This structure is known as a fixed hierarchical topology, and the sequence in which the hierarchy is traversed is often determined at run time by either the application or the user.</span></span> <span data-ttu-id="a7b35-149">Každé stránce v hierarchii, která umožňuje navigace na dvě nebo více stránek za běhu, shromažďuje data potřebná k určení stránku, která má přejděte do.</span><span class="sxs-lookup"><span data-stu-id="a7b35-149">At run time, each page in the hierarchy that allows navigation to two or more other pages gathers the data required to determine which page to navigate to.</span></span> <span data-ttu-id="a7b35-150">Následující obrázek ukazuje jeden z několika možných navigační pořadí podle na předchozím obrázku.</span><span class="sxs-lookup"><span data-stu-id="a7b35-150">The following figure illustrates one of several possible navigation sequences based on the previous figure.</span></span>  
  
 <span data-ttu-id="a7b35-151">![Diagram topologie pro navigační](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure3.png "NavigationTopologyFigure3")</span><span class="sxs-lookup"><span data-stu-id="a7b35-151">![Navigation topology diagram](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure3.png "NavigationTopologyFigure3")</span></span>  
  
 <span data-ttu-id="a7b35-152">Přestože v době běhu je určit pořadí, ve kterém jsou stránky v pevné hierarchická struktura navigaci, činnost koncového uživatele je stejný jako činnost koncového uživatele pro pevnou lineární topologie:</span><span class="sxs-lookup"><span data-stu-id="a7b35-152">Even though the sequence in which pages in a fixed hierarchical structure are navigated is determined at run time, the user experience is the same as the user experience for a fixed linear topology:</span></span>  
  
-   <span data-ttu-id="a7b35-153">Navigace na stránce volání Spouštěče stránku, která inicializuje průvodce a přejde na první stránce průvodce.</span><span class="sxs-lookup"><span data-stu-id="a7b35-153">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="a7b35-154">Na stránce Spouštěče ( [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-menší <xref:System.Windows.Navigation.PageFunction%601>) není vyžadována, protože volání stránky můžete volat přímo na první stránku průvodce.</span><span class="sxs-lookup"><span data-stu-id="a7b35-154">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="a7b35-155">Pomocí stránky Spouštěče, však může zjednodušit inicializace průvodce, zvlášť pokud je komplexní inicializace.</span><span class="sxs-lookup"><span data-stu-id="a7b35-155">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
-   <span data-ttu-id="a7b35-156">Uživatelé mohou přecházet mezi stránkami pomocí zpět a předat dál tlačítka (nebo hypertextové odkazy).</span><span class="sxs-lookup"><span data-stu-id="a7b35-156">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
-   <span data-ttu-id="a7b35-157">Uživatelé mohou přecházet mezi stránkami pomocí deníku.</span><span class="sxs-lookup"><span data-stu-id="a7b35-157">Users can navigate between pages using the journal.</span></span>  
  
-   <span data-ttu-id="a7b35-158">Uživatelé mohou změnit pořadí navigace, pokud jejich přejděte zpět prostřednictvím deníku.</span><span class="sxs-lookup"><span data-stu-id="a7b35-158">Users can change the navigation sequence if they navigate back through the journal.</span></span>  
  
-   <span data-ttu-id="a7b35-159">Uživatele můžete ukončit průvodce z kterékoli stránce průvodce klepnutím na tlačítko Storno.</span><span class="sxs-lookup"><span data-stu-id="a7b35-159">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
-   <span data-ttu-id="a7b35-160">Uživatelé můžou přijmout Průvodce na poslední stránce průvodce klepnutím na tlačítko Dokončit.</span><span class="sxs-lookup"><span data-stu-id="a7b35-160">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
-   <span data-ttu-id="a7b35-161">Pokud zrušení průvodce Průvodce vrátí odpovídající výsledek a nevrátí žádná data.</span><span class="sxs-lookup"><span data-stu-id="a7b35-161">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
-   <span data-ttu-id="a7b35-162">Když uživatel přijme podmínky průvodce, Průvodce vrátí odpovídající výsledek a vrátí data, která se shromažďují.</span><span class="sxs-lookup"><span data-stu-id="a7b35-162">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
-   <span data-ttu-id="a7b35-163">Až průvodce dokončí (přijímat nebo došlo ke zrušení), stránek, které tvoří průvodce se odeberou z deníku.</span><span class="sxs-lookup"><span data-stu-id="a7b35-163">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="a7b35-164">Díky tomu každou instanci Průvodce izolovaných, aby se předešlo potenciální data nebo anomálií stavu.</span><span class="sxs-lookup"><span data-stu-id="a7b35-164">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>   
## <a name="navigation-over-a-dynamically-generated-topology"></a><span data-ttu-id="a7b35-165">Navigace v dynamicky generovaném topologie</span><span class="sxs-lookup"><span data-stu-id="a7b35-165">Navigation over a Dynamically Generated Topology</span></span>  
 <span data-ttu-id="a7b35-166">V některých aplikacích pořadí, ve kterém jsou dvě nebo více stránek navigaci dá pouze určit v době běhu pomocí uživatele, aplikace nebo externí data.</span><span class="sxs-lookup"><span data-stu-id="a7b35-166">In some applications, the sequence in which two or more pages are navigated can only be determined at run time, whether by the user, the application, or external data.</span></span> <span data-ttu-id="a7b35-167">Následující obrázek ukazuje sadu stránek se v neurčeném navigační sekvenci.</span><span class="sxs-lookup"><span data-stu-id="a7b35-167">The following figure illustrates a set of pages with an undetermined navigation sequence.</span></span>  
  
 <span data-ttu-id="a7b35-168">![Diagram topologie pro navigační](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure4.png "NavigationTopologyFigure4")</span><span class="sxs-lookup"><span data-stu-id="a7b35-168">![Navigation topology diagram](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure4.png "NavigationTopologyFigure4")</span></span>  
  
 <span data-ttu-id="a7b35-169">Následující obrázek znázorňuje navigační pořadí, které jste vybrali uživatelem v době běhu.</span><span class="sxs-lookup"><span data-stu-id="a7b35-169">The next figure illustrates a navigation sequence that was chosen by the user at run time.</span></span>  
  
 <span data-ttu-id="a7b35-170">![Navigace – diagram](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure5.png "NavigationTopologyFigure5")</span><span class="sxs-lookup"><span data-stu-id="a7b35-170">![Navigation diagram](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure5.png "NavigationTopologyFigure5")</span></span>  
  
 <span data-ttu-id="a7b35-171">Navigace pořadí se označuje jako dynamicky generovaném topologie.</span><span class="sxs-lookup"><span data-stu-id="a7b35-171">The navigation sequence is known as a dynamically generated topology.</span></span> <span data-ttu-id="a7b35-172">Pro uživatele jako s jiných topologiích navigační činnost koncového uživatele je stejný, jako je pro předchozí topologie:</span><span class="sxs-lookup"><span data-stu-id="a7b35-172">For the user, as with the other navigation topologies, the user experience is the same as it is for the previous topologies:</span></span>  
  
-   <span data-ttu-id="a7b35-173">Navigace na stránce volání Spouštěče stránku, která inicializuje průvodce a přejde na první stránce průvodce.</span><span class="sxs-lookup"><span data-stu-id="a7b35-173">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="a7b35-174">Na stránce Spouštěče ( [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-menší <xref:System.Windows.Navigation.PageFunction%601>) není vyžadována, protože volání stránky můžete volat přímo na první stránku průvodce.</span><span class="sxs-lookup"><span data-stu-id="a7b35-174">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="a7b35-175">Pomocí stránky Spouštěče, však může zjednodušit inicializace průvodce, zvlášť pokud je komplexní inicializace.</span><span class="sxs-lookup"><span data-stu-id="a7b35-175">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
-   <span data-ttu-id="a7b35-176">Uživatelé mohou přecházet mezi stránkami pomocí zpět a předat dál tlačítka (nebo hypertextové odkazy).</span><span class="sxs-lookup"><span data-stu-id="a7b35-176">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
-   <span data-ttu-id="a7b35-177">Uživatelé mohou přecházet mezi stránkami pomocí deníku.</span><span class="sxs-lookup"><span data-stu-id="a7b35-177">Users can navigate between pages using the journal.</span></span>  
  
-   <span data-ttu-id="a7b35-178">Uživatele můžete ukončit průvodce z kterékoli stránce průvodce klepnutím na tlačítko Storno.</span><span class="sxs-lookup"><span data-stu-id="a7b35-178">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
-   <span data-ttu-id="a7b35-179">Uživatelé můžou přijmout Průvodce na poslední stránce průvodce klepnutím na tlačítko Dokončit.</span><span class="sxs-lookup"><span data-stu-id="a7b35-179">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
-   <span data-ttu-id="a7b35-180">Pokud zrušení průvodce Průvodce vrátí odpovídající výsledek a nevrátí žádná data.</span><span class="sxs-lookup"><span data-stu-id="a7b35-180">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
-   <span data-ttu-id="a7b35-181">Když uživatel přijme podmínky průvodce, Průvodce vrátí odpovídající výsledek a vrátí data, která se shromažďují.</span><span class="sxs-lookup"><span data-stu-id="a7b35-181">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
-   <span data-ttu-id="a7b35-182">Až průvodce dokončí (přijímat nebo došlo ke zrušení), stránek, které tvoří průvodce se odeberou z deníku.</span><span class="sxs-lookup"><span data-stu-id="a7b35-182">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="a7b35-183">Díky tomu každou instanci Průvodce izolovaných, aby se předešlo potenciální data nebo anomálií stavu.</span><span class="sxs-lookup"><span data-stu-id="a7b35-183">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7b35-184">Viz také</span><span class="sxs-lookup"><span data-stu-id="a7b35-184">See Also</span></span>  
 <xref:System.Windows.Controls.Page>  
 <xref:System.Windows.Navigation.PageFunction%601>  
 <xref:System.Windows.Navigation.NavigationService>  
 [<span data-ttu-id="a7b35-185">Strukturované navigační – přehled</span><span class="sxs-lookup"><span data-stu-id="a7b35-185">Structured Navigation Overview</span></span>](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md)
