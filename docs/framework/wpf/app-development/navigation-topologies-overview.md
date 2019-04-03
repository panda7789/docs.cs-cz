---
title: Přehled topologií navigace
ms.date: 03/30/2017
helpviewer_keywords:
- linear topology [WPF]
- fixed hierarchical topology [WPF]
- fixed linear topology [WPF]
- topologies [WPF]
- navigation topologies [WPF]
- dynamically-generated topology
ms.assetid: 5d5ee837-629a-4933-869a-186dc22ac43d
ms.openlocfilehash: 3e5cca90861ccdeaff904a34c6f484cfdd32c975
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819590"
---
# <a name="navigation-topologies-overview"></a><span data-ttu-id="eb079-102">Přehled topologií navigace</span><span class="sxs-lookup"><span data-stu-id="eb079-102">Navigation Topologies Overview</span></span>
<a name="introduction"></a> <span data-ttu-id="eb079-103">Tento přehled poskytuje úvod do topologie navigace v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb079-103">This overview provides an introduction to navigation topologies in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span> <span data-ttu-id="eb079-104">Tři běžné topologie navigace s ukázkami, následně jsou popsány.</span><span class="sxs-lookup"><span data-stu-id="eb079-104">Three common navigation topologies, with samples, are subsequently discussed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eb079-105">Před čtením tohoto tématu, měli byste se seznámit s konceptem strukturované navigace v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pomocí stránky funkce.</span><span class="sxs-lookup"><span data-stu-id="eb079-105">Before reading this topic, you should be familiar with the concept of structured navigation in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] using page functions.</span></span> <span data-ttu-id="eb079-106">Další informace o obou těchto tématech najdete v tématu [přehled strukturované navigace](structured-navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="eb079-106">For more information on both of these topics, see [Structured Navigation Overview](structured-navigation-overview.md).</span></span>  
  
 <span data-ttu-id="eb079-107">Toto téma obsahuje následující oddíly:</span><span class="sxs-lookup"><span data-stu-id="eb079-107">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="eb079-108">Topologie navigace</span><span class="sxs-lookup"><span data-stu-id="eb079-108">Navigation Topologies</span></span>](#Navigation_Topologies)  
  
-   [<span data-ttu-id="eb079-109">Topologie strukturované navigace</span><span class="sxs-lookup"><span data-stu-id="eb079-109">Structured Navigation Topologies</span></span>](#Structured_Navigation_Topologies)  
  
-   [<span data-ttu-id="eb079-110">Navigace prostřednictvím pevná lineární topologie</span><span class="sxs-lookup"><span data-stu-id="eb079-110">Navigation over a Fixed Linear Topology</span></span>](#Navigation_over_a_Fixed_Linear_Topology)  
  
-   [<span data-ttu-id="eb079-111">Dynamické navigace přes pevná hierarchická topologie</span><span class="sxs-lookup"><span data-stu-id="eb079-111">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
-   [<span data-ttu-id="eb079-112">Navigace v dynamicky generovaném topologie</span><span class="sxs-lookup"><span data-stu-id="eb079-112">Navigation over a Dynamically Generated Topology</span></span>](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>   
## <a name="navigation-topologies"></a><span data-ttu-id="eb079-113">Topologie navigace</span><span class="sxs-lookup"><span data-stu-id="eb079-113">Navigation Topologies</span></span>  
 <span data-ttu-id="eb079-114">V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], navigace se obvykle skládá z stránky (<xref:System.Windows.Controls.Page>) s hypertextovými odkazy (<xref:System.Windows.Documents.Hyperlink>), přejděte na jinou stránku po kliknutí.</span><span class="sxs-lookup"><span data-stu-id="eb079-114">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], navigation typically consists of pages (<xref:System.Windows.Controls.Page>) with hyperlinks (<xref:System.Windows.Documents.Hyperlink>) that navigate to other pages when clicked.</span></span> <span data-ttu-id="eb079-115">Stránky, které se přejde poté, jsou identifikované [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] (viz [identifikátory Pack URI v subsystému WPF](pack-uris-in-wpf.md)).</span><span class="sxs-lookup"><span data-stu-id="eb079-115">Pages that are navigated to are identified by [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] (see [Pack URIs in WPF](pack-uris-in-wpf.md)).</span></span> <span data-ttu-id="eb079-116">Vezměte v úvahu následující jednoduchý příklad, který zobrazí stránky, hypertextové odkazy, a [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="eb079-116">Consider the following simple example that shows pages, hyperlinks, and [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]:</span></span>  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 <span data-ttu-id="eb079-117">Tyto stránky jsou uspořádány *topologie navigace* jehož struktura je určen jak přecházet mezi stránkami.</span><span class="sxs-lookup"><span data-stu-id="eb079-117">These pages are arranged in a *navigation topology* whose structure is determined by how you can navigate between the pages.</span></span> <span data-ttu-id="eb079-118">Tato topologie konkrétní navigace je vhodný v jednoduché scénáře, i když navigace mohou vyžadovat složitější topologie, některé z nich je možné definovat jenom při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="eb079-118">This particular navigation topology is suitable in simple scenarios, although navigation can require more complex topologies, some of which can only be defined when an application is running.</span></span>  
  
 <span data-ttu-id="eb079-119">Toto téma popisuje tři běžné topologie navigace: *pevná lineární*, *pevná hierarchická*, a *dynamicky generované*.</span><span class="sxs-lookup"><span data-stu-id="eb079-119">This topic covers three common navigation topologies: *fixed linear*, *fixed hierarchical*, and *dynamically generated*.</span></span> <span data-ttu-id="eb079-120">Každá topologie navigace je znázorněn s pomocí ukázky, která má [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , jako je ten, který je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="eb079-120">Each navigation topology is demonstrated with a sample that has a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] like the one that is shown in the following figure:</span></span>  
  
 ![Stránky úloh s datovými položkami a navigačních tlačítek.](./media/navigation-topologies-overview/navigation-topology-data-items.png)  
  
<a name="Structured_Navigation_Topologies"></a>   
## <a name="structured-navigation-topologies"></a><span data-ttu-id="eb079-122">Topologie strukturované navigace</span><span class="sxs-lookup"><span data-stu-id="eb079-122">Structured Navigation Topologies</span></span>  
 <span data-ttu-id="eb079-123">Existují dva široké typy topologie navigace:</span><span class="sxs-lookup"><span data-stu-id="eb079-123">There are two broad types of navigation topologies:</span></span>  
  
-   <span data-ttu-id="eb079-124">**Opraveno Topology**: definovaná v době kompilace a za běhu se nemění.</span><span class="sxs-lookup"><span data-stu-id="eb079-124">**Fixed Topology**: defined at compile time and does not change at run time.</span></span> <span data-ttu-id="eb079-125">Oprava topologie jsou užitečné pro navigaci pevné pořadí stránek v lineární nebo hierarchickém pořadí.</span><span class="sxs-lookup"><span data-stu-id="eb079-125">Fixed topologies are useful for navigation through a fixed sequence of pages in either a linear or hierarchical order.</span></span>  
  
-   <span data-ttu-id="eb079-126">**Dynamické topologie**: definovaný v době běhu na základě vstupu, shromážděných od uživatele, aplikace nebo systému.</span><span class="sxs-lookup"><span data-stu-id="eb079-126">**Dynamic Topology**: defined at run time based on input that is collected from the user, the application, or the system.</span></span> <span data-ttu-id="eb079-127">Dynamické topologie jsou užitečné, pokud stránky se dá Navigovat v různých řad.</span><span class="sxs-lookup"><span data-stu-id="eb079-127">Dynamic topologies are useful when pages can be navigated in different sequences.</span></span>  
  
 <span data-ttu-id="eb079-128">I když je možné vytvářet topologie navigace pomocí stránek, ukázky funkcí stránky použít, protože poskytují další podporu, která zjednodušuje podporu pro předávání a vrací data na stránkách topologie.</span><span class="sxs-lookup"><span data-stu-id="eb079-128">Although it is possible to create navigation topologies using pages, the samples use page functions because they provide additional support that simplifies support for passing and returning data through the pages of a topology.</span></span>  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>   
## <a name="navigation-over-a-fixed-linear-topology"></a><span data-ttu-id="eb079-129">Navigace prostřednictvím pevná lineární topologie</span><span class="sxs-lookup"><span data-stu-id="eb079-129">Navigation over a Fixed Linear Topology</span></span>  
 <span data-ttu-id="eb079-130">Pevná lineární topologie se podobá struktuře průvodce, který má jeden nebo více stránkách průvodce, které se přejde poté, v pevné posloupnosti.</span><span class="sxs-lookup"><span data-stu-id="eb079-130">A fixed linear topology is analogous to the structure of a wizard that has one or more wizard pages that are navigated in a fixed sequence.</span></span> <span data-ttu-id="eb079-131">Následující obrázek znázorňuje základní strukturu a tok průvodce s pevná lineární topologie:</span><span class="sxs-lookup"><span data-stu-id="eb079-131">The following figure shows the high-level structure and flow of a wizard with a fixed linear topology:</span></span>  
  
 ![Diagram zobrazující průběh pevná lineární topologie.](./media/navigation-topologies-overview/navigation-topology-fixed-linear.png)  
  
 <span data-ttu-id="eb079-133">Chování typické pro navigaci přes pevná lineární topologie patří:</span><span class="sxs-lookup"><span data-stu-id="eb079-133">The typical behaviors for navigating over a fixed linear topology include the following:</span></span>  
  
-   <span data-ttu-id="eb079-134">Navigace na stránce volání Spouštěč stránku, která inicializuje průvodce a přejde na první stránce průvodce.</span><span class="sxs-lookup"><span data-stu-id="eb079-134">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="eb079-135">Spouštěč stránky ( [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]– méně <xref:System.Windows.Navigation.PageFunction%601>) není vyžadováno, protože volání stránky můžete volat přímo na první stránku průvodce.</span><span class="sxs-lookup"><span data-stu-id="eb079-135">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="eb079-136">Pomocí stránky Spouštěče, ale může zjednodušit inicializace průvodce, zejména v případě, že inicializace je složitá.</span><span class="sxs-lookup"><span data-stu-id="eb079-136">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
-   <span data-ttu-id="eb079-137">Uživatelé můžou přecházet mezi stránkami pomocí zpět a vpřed tlačítka (nebo hypertextové odkazy).</span><span class="sxs-lookup"><span data-stu-id="eb079-137">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
-   <span data-ttu-id="eb079-138">Uživatelé můžou přecházet mezi stránky s využitím deníku.</span><span class="sxs-lookup"><span data-stu-id="eb079-138">Users can navigate between pages using the journal.</span></span>  
  
-   <span data-ttu-id="eb079-139">Uživatele můžete zrušit Průvodce na kterékoli stránce průvodce stisknutím tlačítka Storno.</span><span class="sxs-lookup"><span data-stu-id="eb079-139">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
-   <span data-ttu-id="eb079-140">Uživatelé můžou přijmout Průvodce na poslední stránce průvodce klepnutím na tlačítko Dokončit.</span><span class="sxs-lookup"><span data-stu-id="eb079-140">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
-   <span data-ttu-id="eb079-141">Pokud dojde ke zrušení průvodce, Průvodce vrátí odpovídající výsledek a nevrátí žádná data.</span><span class="sxs-lookup"><span data-stu-id="eb079-141">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
-   <span data-ttu-id="eb079-142">Když uživatel přijme podmínky průvodce, Průvodce vrátí odpovídající výsledek a vrátí data, která se shromažďují.</span><span class="sxs-lookup"><span data-stu-id="eb079-142">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
-   <span data-ttu-id="eb079-143">Dokončení průvodce (přijata nebo bylo zrušeno), stránek, které se skládá z Průvodce se odeberou z deníku.</span><span class="sxs-lookup"><span data-stu-id="eb079-143">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="eb079-144">Každá instance průvodce izolované, aby se předešlo potenciální dat nebo stavu anomálie se takto zachová.</span><span class="sxs-lookup"><span data-stu-id="eb079-144">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>   
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a><span data-ttu-id="eb079-145">Dynamické navigace přes pevná hierarchická topologie</span><span class="sxs-lookup"><span data-stu-id="eb079-145">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>  
 <span data-ttu-id="eb079-146">V některých aplikacích stránky povolit navigaci na dvě nebo více stránek, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="eb079-146">In some applications, pages allow navigation to two or more other pages, as shown in the following figure:</span></span> 
  
 ![Diagram zobrazující stránku můžete přejít na více stránkách.](./media/navigation-topologies-overview/navigation-topology-multiple-pages.png)  
  
 <span data-ttu-id="eb079-148">Tato struktura se označuje jako pevná hierarchická topologie a pořadí, ve kterém je procházet hierarchii často stanovena v době běhu aplikace nebo uživatele.</span><span class="sxs-lookup"><span data-stu-id="eb079-148">This structure is known as a fixed hierarchical topology, and the sequence in which the hierarchy is traversed is often determined at run time by either the application or the user.</span></span> <span data-ttu-id="eb079-149">V době běhu každá stránka v hierarchii, která umožňuje navigaci na dvě nebo více stránek shromažďuje data potřebná k určení stránku, která má přejít na.</span><span class="sxs-lookup"><span data-stu-id="eb079-149">At run time, each page in the hierarchy that allows navigation to two or more other pages gathers the data required to determine which page to navigate to.</span></span> <span data-ttu-id="eb079-150">Následující obrázek znázorňuje jeden z několika možných navigace pořadí založen na předchozím obrázku:</span><span class="sxs-lookup"><span data-stu-id="eb079-150">The following figure illustrates one of several possible navigation sequences based on the previous figure:</span></span>  
  
 ![Diagram zobrazující průběh pořadí navigace je to možné.](./media/navigation-topologies-overview/navigation-topology-fixed-hierarchical.png)  
  
 <span data-ttu-id="eb079-152">Přestože pořadí, ve kterém jsou stránky ve struktuře pevná hierarchická přejde je stanovena v době běhu, činnost koncového uživatele je stejné jako uživatelské prostředí u pevná lineární topologie:</span><span class="sxs-lookup"><span data-stu-id="eb079-152">Even though the sequence in which pages in a fixed hierarchical structure are navigated is determined at run time, the user experience is the same as the user experience for a fixed linear topology:</span></span>  
  
-   <span data-ttu-id="eb079-153">Navigace na stránce volání Spouštěč stránku, která inicializuje průvodce a přejde na první stránce průvodce.</span><span class="sxs-lookup"><span data-stu-id="eb079-153">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="eb079-154">Spouštěč stránky ( [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]– méně <xref:System.Windows.Navigation.PageFunction%601>) není vyžadováno, protože volání stránky můžete volat přímo na první stránku průvodce.</span><span class="sxs-lookup"><span data-stu-id="eb079-154">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="eb079-155">Pomocí stránky Spouštěče, ale může zjednodušit inicializace průvodce, zejména v případě, že inicializace je složitá.</span><span class="sxs-lookup"><span data-stu-id="eb079-155">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
-   <span data-ttu-id="eb079-156">Uživatelé můžou přecházet mezi stránkami pomocí zpět a vpřed tlačítka (nebo hypertextové odkazy).</span><span class="sxs-lookup"><span data-stu-id="eb079-156">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
-   <span data-ttu-id="eb079-157">Uživatelé můžou přecházet mezi stránky s využitím deníku.</span><span class="sxs-lookup"><span data-stu-id="eb079-157">Users can navigate between pages using the journal.</span></span>  
  
-   <span data-ttu-id="eb079-158">Uživatelé mohou změnit pořadí navigace, pokud uživatel přejde zpět prostřednictvím deníku.</span><span class="sxs-lookup"><span data-stu-id="eb079-158">Users can change the navigation sequence if they navigate back through the journal.</span></span>  
  
-   <span data-ttu-id="eb079-159">Uživatele můžete zrušit Průvodce na kterékoli stránce průvodce stisknutím tlačítka Storno.</span><span class="sxs-lookup"><span data-stu-id="eb079-159">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
-   <span data-ttu-id="eb079-160">Uživatelé můžou přijmout Průvodce na poslední stránce průvodce klepnutím na tlačítko Dokončit.</span><span class="sxs-lookup"><span data-stu-id="eb079-160">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
-   <span data-ttu-id="eb079-161">Pokud dojde ke zrušení průvodce, Průvodce vrátí odpovídající výsledek a nevrátí žádná data.</span><span class="sxs-lookup"><span data-stu-id="eb079-161">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
-   <span data-ttu-id="eb079-162">Když uživatel přijme podmínky průvodce, Průvodce vrátí odpovídající výsledek a vrátí data, která se shromažďují.</span><span class="sxs-lookup"><span data-stu-id="eb079-162">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
-   <span data-ttu-id="eb079-163">Dokončení průvodce (přijata nebo bylo zrušeno), stránek, které se skládá z Průvodce se odeberou z deníku.</span><span class="sxs-lookup"><span data-stu-id="eb079-163">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="eb079-164">Každá instance průvodce izolované, aby se předešlo potenciální dat nebo stavu anomálie se takto zachová.</span><span class="sxs-lookup"><span data-stu-id="eb079-164">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>   
## <a name="navigation-over-a-dynamically-generated-topology"></a><span data-ttu-id="eb079-165">Navigace v dynamicky generovaném topologie</span><span class="sxs-lookup"><span data-stu-id="eb079-165">Navigation over a Dynamically Generated Topology</span></span>  
 <span data-ttu-id="eb079-166">V některých aplikacích pořadí, ve kterém se přejde poté, dvě nebo více stránek lze pouze určit v době běhu podle uživatele, aplikace nebo externí data.</span><span class="sxs-lookup"><span data-stu-id="eb079-166">In some applications, the sequence in which two or more pages are navigated can only be determined at run time, whether by the user, the application, or external data.</span></span> <span data-ttu-id="eb079-167">Následující obrázek znázorňuje sadu stránek s neurčenou navigační sekvenci:</span><span class="sxs-lookup"><span data-stu-id="eb079-167">The following figure illustrates a set of pages with an undetermined navigation sequence:</span></span>  
  
 ![Sady stránek s neurčenou navigační sekvenci.](./media/navigation-topologies-overview/navigation-topology-dynamically-generated.png)  
  
 <span data-ttu-id="eb079-169">Následující obrázek znázorňuje navigační sekvenci, který byl vybrán uživatelem v době běhu:</span><span class="sxs-lookup"><span data-stu-id="eb079-169">The next figure illustrates a navigation sequence that was chosen by the user at run time:</span></span>  
  
 ![Diagram zobrazující průběh pořadí navigace zvolená v době běhu.](./media/navigation-topologies-overview/navigation-topology-sequence-chosen-run-time.png)  
  
 <span data-ttu-id="eb079-171">Navigační sekvenci se označuje jako dynamicky generovaných topologií.</span><span class="sxs-lookup"><span data-stu-id="eb079-171">The navigation sequence is known as a dynamically generated topology.</span></span> <span data-ttu-id="eb079-172">Pro uživatele, stejně jako u jiných topologie navigace, činnost koncového uživatele je stejné je pro předchozí topologie:</span><span class="sxs-lookup"><span data-stu-id="eb079-172">For the user, as with the other navigation topologies, the user experience is the same as it is for the previous topologies:</span></span>  
  
-   <span data-ttu-id="eb079-173">Navigace na stránce volání Spouštěč stránku, která inicializuje průvodce a přejde na první stránce průvodce.</span><span class="sxs-lookup"><span data-stu-id="eb079-173">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="eb079-174">Spouštěč stránky ( [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]– méně <xref:System.Windows.Navigation.PageFunction%601>) není vyžadováno, protože volání stránky můžete volat přímo na první stránku průvodce.</span><span class="sxs-lookup"><span data-stu-id="eb079-174">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="eb079-175">Pomocí stránky Spouštěče, ale může zjednodušit inicializace průvodce, zejména v případě, že inicializace je složitá.</span><span class="sxs-lookup"><span data-stu-id="eb079-175">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
-   <span data-ttu-id="eb079-176">Uživatelé můžou přecházet mezi stránkami pomocí zpět a vpřed tlačítka (nebo hypertextové odkazy).</span><span class="sxs-lookup"><span data-stu-id="eb079-176">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
-   <span data-ttu-id="eb079-177">Uživatelé můžou přecházet mezi stránky s využitím deníku.</span><span class="sxs-lookup"><span data-stu-id="eb079-177">Users can navigate between pages using the journal.</span></span>  
  
-   <span data-ttu-id="eb079-178">Uživatele můžete zrušit Průvodce na kterékoli stránce průvodce stisknutím tlačítka Storno.</span><span class="sxs-lookup"><span data-stu-id="eb079-178">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
-   <span data-ttu-id="eb079-179">Uživatelé můžou přijmout Průvodce na poslední stránce průvodce klepnutím na tlačítko Dokončit.</span><span class="sxs-lookup"><span data-stu-id="eb079-179">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
-   <span data-ttu-id="eb079-180">Pokud dojde ke zrušení průvodce, Průvodce vrátí odpovídající výsledek a nevrátí žádná data.</span><span class="sxs-lookup"><span data-stu-id="eb079-180">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
-   <span data-ttu-id="eb079-181">Když uživatel přijme podmínky průvodce, Průvodce vrátí odpovídající výsledek a vrátí data, která se shromažďují.</span><span class="sxs-lookup"><span data-stu-id="eb079-181">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
-   <span data-ttu-id="eb079-182">Dokončení průvodce (přijata nebo bylo zrušeno), stránek, které se skládá z Průvodce se odeberou z deníku.</span><span class="sxs-lookup"><span data-stu-id="eb079-182">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="eb079-183">Každá instance průvodce izolované, aby se předešlo potenciální dat nebo stavu anomálie se takto zachová.</span><span class="sxs-lookup"><span data-stu-id="eb079-183">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb079-184">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eb079-184">See also</span></span>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [<span data-ttu-id="eb079-185">Přehled strukturované navigace</span><span class="sxs-lookup"><span data-stu-id="eb079-185">Structured Navigation Overview</span></span>](structured-navigation-overview.md)
