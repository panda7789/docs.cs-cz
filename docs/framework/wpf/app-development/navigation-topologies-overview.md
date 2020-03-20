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
ms.openlocfilehash: 08f6342095706e5ffe9479f5236457d21474152a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174196"
---
# <a name="navigation-topologies-overview"></a><span data-ttu-id="d251d-102">Přehled topologií navigace</span><span class="sxs-lookup"><span data-stu-id="d251d-102">Navigation Topologies Overview</span></span>
<a name="introduction"></a><span data-ttu-id="d251d-103">Tento přehled poskytuje úvod do topologie navigace v WPF.</span><span class="sxs-lookup"><span data-stu-id="d251d-103">This overview provides an introduction to navigation topologies in WPF.</span></span> <span data-ttu-id="d251d-104">Následně jsou diskutovány tři běžné navigační topologie se vzorky.</span><span class="sxs-lookup"><span data-stu-id="d251d-104">Three common navigation topologies, with samples, are subsequently discussed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d251d-105">Před přečtením tohoto tématu byste měli být obeznámeni s konceptem strukturované navigace v WPF pomocí funkcí stránky.</span><span class="sxs-lookup"><span data-stu-id="d251d-105">Before reading this topic, you should be familiar with the concept of structured navigation in WPF using page functions.</span></span> <span data-ttu-id="d251d-106">Další informace o obou těchto tématech naleznete v tématu [Přehled strukturované navigace](structured-navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d251d-106">For more information on both of these topics, see [Structured Navigation Overview](structured-navigation-overview.md).</span></span>  
  
 <span data-ttu-id="d251d-107">Toto téma obsahuje následující oddíly:</span><span class="sxs-lookup"><span data-stu-id="d251d-107">This topic contains the following sections:</span></span>  
  
- [<span data-ttu-id="d251d-108">Navigační topologie</span><span class="sxs-lookup"><span data-stu-id="d251d-108">Navigation Topologies</span></span>](#Navigation_Topologies)  
  
- [<span data-ttu-id="d251d-109">Strukturované navigační topologie</span><span class="sxs-lookup"><span data-stu-id="d251d-109">Structured Navigation Topologies</span></span>](#Structured_Navigation_Topologies)  
  
- [<span data-ttu-id="d251d-110">Navigace přes pevnou lineární topologii</span><span class="sxs-lookup"><span data-stu-id="d251d-110">Navigation over a Fixed Linear Topology</span></span>](#Navigation_over_a_Fixed_Linear_Topology)  
  
- [<span data-ttu-id="d251d-111">Dynamická navigace přes pevnou hierarchickou topologii</span><span class="sxs-lookup"><span data-stu-id="d251d-111">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
- [<span data-ttu-id="d251d-112">Navigace přes dynamicky generovanou topologii</span><span class="sxs-lookup"><span data-stu-id="d251d-112">Navigation over a Dynamically Generated Topology</span></span>](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>
## <a name="navigation-topologies"></a><span data-ttu-id="d251d-113">Navigační topologie</span><span class="sxs-lookup"><span data-stu-id="d251d-113">Navigation Topologies</span></span>  
 <span data-ttu-id="d251d-114">Ve WPF se navigace obvykle skládá<xref:System.Windows.Controls.Page>ze stránek<xref:System.Windows.Documents.Hyperlink>( ) s hypertextovými odkazy ( ), které po klepnutí přecházejí na jiné stránky.</span><span class="sxs-lookup"><span data-stu-id="d251d-114">In WPF, navigation typically consists of pages (<xref:System.Windows.Controls.Page>) with hyperlinks (<xref:System.Windows.Documents.Hyperlink>) that navigate to other pages when clicked.</span></span> <span data-ttu-id="d251d-115">Stránky, na které se naviguje, jsou označeny identifikátory prostředků (URI) (viz [Balení identifikátorů URI v wpf).](pack-uris-in-wpf.md)</span><span class="sxs-lookup"><span data-stu-id="d251d-115">Pages that are navigated to are identified by uniform resource identifiers (URIs) (see [Pack URIs in WPF](pack-uris-in-wpf.md)).</span></span> <span data-ttu-id="d251d-116">Vezměte v úvahu následující jednoduchý příklad, který zobrazuje stránky, hypertextové odkazy a jednotné identifikátory prostředků (URI):</span><span class="sxs-lookup"><span data-stu-id="d251d-116">Consider the following simple example that shows pages, hyperlinks, and uniform resource identifiers (URIs):</span></span>  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 <span data-ttu-id="d251d-117">Tyto stránky jsou uspořádány v *navigační topologii,* jejíž struktura je určena tím, jak můžete procházet mezi stránkami.</span><span class="sxs-lookup"><span data-stu-id="d251d-117">These pages are arranged in a *navigation topology* whose structure is determined by how you can navigate between the pages.</span></span> <span data-ttu-id="d251d-118">Tato konkrétní navigační topologie je vhodná v jednoduchých scénářích, i když navigace může vyžadovat složitější topologie, z nichž některé lze definovat pouze v případě, že je spuštěna aplikace.</span><span class="sxs-lookup"><span data-stu-id="d251d-118">This particular navigation topology is suitable in simple scenarios, although navigation can require more complex topologies, some of which can only be defined when an application is running.</span></span>  
  
 <span data-ttu-id="d251d-119">Toto téma popisuje tři běžné navigační topologie: *pevné lineární*, *pevné hierarchické*a *dynamicky generované*.</span><span class="sxs-lookup"><span data-stu-id="d251d-119">This topic covers three common navigation topologies: *fixed linear*, *fixed hierarchical*, and *dynamically generated*.</span></span> <span data-ttu-id="d251d-120">Každá navigační topologie je demonstrována [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] se vzorkem, který má podobný ten, který je znázorněn na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="d251d-120">Each navigation topology is demonstrated with a sample that has a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] like the one that is shown in the following figure:</span></span>  
  
 ![Stránky úkolů s datovými položkami a navigačními tlačítky.](./media/navigation-topologies-overview/navigation-topology-data-items.png)  
  
<a name="Structured_Navigation_Topologies"></a>
## <a name="structured-navigation-topologies"></a><span data-ttu-id="d251d-122">Strukturované navigační topologie</span><span class="sxs-lookup"><span data-stu-id="d251d-122">Structured Navigation Topologies</span></span>  
 <span data-ttu-id="d251d-123">Existují dva široké typy navigačních topologie:</span><span class="sxs-lookup"><span data-stu-id="d251d-123">There are two broad types of navigation topologies:</span></span>  
  
- <span data-ttu-id="d251d-124">**Pevná topologie**: definována v době kompilace a nemění se za běhu.</span><span class="sxs-lookup"><span data-stu-id="d251d-124">**Fixed Topology**: defined at compile time and does not change at run time.</span></span> <span data-ttu-id="d251d-125">Pevné topologie jsou užitečné pro navigaci přes pevnou sekvenci stránek v lineárním nebo hierarchickém pořadí.</span><span class="sxs-lookup"><span data-stu-id="d251d-125">Fixed topologies are useful for navigation through a fixed sequence of pages in either a linear or hierarchical order.</span></span>  
  
- <span data-ttu-id="d251d-126">**Dynamická topologie**: definována za běhu na základě vstupu, který je shromážděn od uživatele, aplikace nebo systému.</span><span class="sxs-lookup"><span data-stu-id="d251d-126">**Dynamic Topology**: defined at run time based on input that is collected from the user, the application, or the system.</span></span> <span data-ttu-id="d251d-127">Dynamické topologie jsou užitečné, když stránky lze procházet v různých sekvencích.</span><span class="sxs-lookup"><span data-stu-id="d251d-127">Dynamic topologies are useful when pages can be navigated in different sequences.</span></span>  
  
 <span data-ttu-id="d251d-128">I když je možné vytvořit navigační topologie pomocí stránek, ukázky používají funkce stránky, protože poskytují další podporu, která zjednodušuje podporu pro předávání a vracení dat prostřednictvím stránek topologie.</span><span class="sxs-lookup"><span data-stu-id="d251d-128">Although it is possible to create navigation topologies using pages, the samples use page functions because they provide additional support that simplifies support for passing and returning data through the pages of a topology.</span></span>  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>
## <a name="navigation-over-a-fixed-linear-topology"></a><span data-ttu-id="d251d-129">Navigace přes pevnou lineární topologii</span><span class="sxs-lookup"><span data-stu-id="d251d-129">Navigation over a Fixed Linear Topology</span></span>  
 <span data-ttu-id="d251d-130">Pevná lineární topologie je obdobou struktury průvodce, který má jednu nebo více stránek průvodce, které jsou navigovány v pevném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d251d-130">A fixed linear topology is analogous to the structure of a wizard that has one or more wizard pages that are navigated in a fixed sequence.</span></span> <span data-ttu-id="d251d-131">Následující obrázek znázorňuje strukturu vysoké úrovně a tok průvodce s pevnou lineární topologii:</span><span class="sxs-lookup"><span data-stu-id="d251d-131">The following figure shows the high-level structure and flow of a wizard with a fixed linear topology:</span></span>  
  
 ![Diagram, který zobrazuje pevnou lineární topologii.](./media/navigation-topologies-overview/navigation-topology-fixed-linear.png)  
  
 <span data-ttu-id="d251d-133">Typické chování pro navigaci přes pevnou lineární topologii patří následující:</span><span class="sxs-lookup"><span data-stu-id="d251d-133">The typical behaviors for navigating over a fixed linear topology include the following:</span></span>  
  
- <span data-ttu-id="d251d-134">Přechod ze stránky volajícího na stránku spouštěče, která inicializuje průvodce a přejde na první stránku průvodce.</span><span class="sxs-lookup"><span data-stu-id="d251d-134">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="d251d-135">Stránka spouštěče [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)](a <xref:System.Windows.Navigation.PageFunction%601>-less) není vyžadována, protože volající stránka může volat přímo první stránku průvodce.</span><span class="sxs-lookup"><span data-stu-id="d251d-135">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="d251d-136">Použití stránky spouštěče však může zjednodušit inicializaci průvodce, zejména pokud je inicializace složitá.</span><span class="sxs-lookup"><span data-stu-id="d251d-136">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
- <span data-ttu-id="d251d-137">Uživatelé mohou přecházet mezi stránkami pomocí tlačítek Zpět a Vpřed (nebo hypertextových odkazů).</span><span class="sxs-lookup"><span data-stu-id="d251d-137">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
- <span data-ttu-id="d251d-138">Uživatelé mohou procházet mezi stránkami pomocí deníku.</span><span class="sxs-lookup"><span data-stu-id="d251d-138">Users can navigate between pages using the journal.</span></span>  
  
- <span data-ttu-id="d251d-139">Uživatelé mohou zrušit průvodce z libovolné stránky průvodce stisknutím tlačítka Storno.</span><span class="sxs-lookup"><span data-stu-id="d251d-139">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
- <span data-ttu-id="d251d-140">Uživatelé mohou průvodce přijmout na poslední stránce průvodce stisknutím tlačítka Dokončit.</span><span class="sxs-lookup"><span data-stu-id="d251d-140">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
- <span data-ttu-id="d251d-141">Pokud je průvodce zrušen, vrátí odpovídající výsledek a nevrátí žádná data.</span><span class="sxs-lookup"><span data-stu-id="d251d-141">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
- <span data-ttu-id="d251d-142">Pokud uživatel přijme průvodce, vrátí odpovídající výsledek a vrátí shromážděná data.</span><span class="sxs-lookup"><span data-stu-id="d251d-142">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
- <span data-ttu-id="d251d-143">Po dokončení průvodce (přijato nebo zrušeno) budou stránky, které průvodce obsahuje, odebrány z deníku.</span><span class="sxs-lookup"><span data-stu-id="d251d-143">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="d251d-144">To udržuje každou instanci průvodce izolované, čímž se zabrání potenciální data nebo státní anomálie.</span><span class="sxs-lookup"><span data-stu-id="d251d-144">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a><span data-ttu-id="d251d-145">Dynamická navigace přes pevnou hierarchickou topologii</span><span class="sxs-lookup"><span data-stu-id="d251d-145">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>  
 <span data-ttu-id="d251d-146">V některých aplikacích stránky umožňují navigaci na dvě nebo více dalších stránek, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="d251d-146">In some applications, pages allow navigation to two or more other pages, as shown in the following figure:</span></span>
  
 ![Diagram, který zobrazuje stránku, která může přejít na více stránek.](./media/navigation-topologies-overview/navigation-topology-multiple-pages.png)  
  
 <span data-ttu-id="d251d-148">Tato struktura se označuje jako pevná hierarchická topologie a pořadí, ve kterém je hierarchie provázána, je často určeno za běhu aplikací nebo uživatelem.</span><span class="sxs-lookup"><span data-stu-id="d251d-148">This structure is known as a fixed hierarchical topology, and the sequence in which the hierarchy is traversed is often determined at run time by either the application or the user.</span></span> <span data-ttu-id="d251d-149">Za běhu každá stránka v hierarchii, která umožňuje navigaci na dvě nebo více dalších stránek, shromažďuje data potřebná k určení stránky, na kterou chcete přejít.</span><span class="sxs-lookup"><span data-stu-id="d251d-149">At run time, each page in the hierarchy that allows navigation to two or more other pages gathers the data required to determine which page to navigate to.</span></span> <span data-ttu-id="d251d-150">Následující obrázek znázorňuje jednu z několika možných navigačních sekvencí na základě předchozího obrázku:</span><span class="sxs-lookup"><span data-stu-id="d251d-150">The following figure illustrates one of several possible navigation sequences based on the previous figure:</span></span>  
  
 ![Diagram, který ukazuje možnou navigační sekvenci.](./media/navigation-topologies-overview/navigation-topology-fixed-hierarchical.png)  
  
 <span data-ttu-id="d251d-152">I když pořadí, ve kterém jsou stránky v pevné hierarchické struktuře navigovány, je určeno za běhu, uživatelské prostředí je stejné jako uživatelské prostředí pro pevnou lineární topologii:</span><span class="sxs-lookup"><span data-stu-id="d251d-152">Even though the sequence in which pages in a fixed hierarchical structure are navigated is determined at run time, the user experience is the same as the user experience for a fixed linear topology:</span></span>  
  
- <span data-ttu-id="d251d-153">Přechod ze stránky volajícího na stránku spouštěče, která inicializuje průvodce a přejde na první stránku průvodce.</span><span class="sxs-lookup"><span data-stu-id="d251d-153">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="d251d-154">Stránka spouštěče [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)](a <xref:System.Windows.Navigation.PageFunction%601>-less) není vyžadována, protože volající stránka může volat přímo první stránku průvodce.</span><span class="sxs-lookup"><span data-stu-id="d251d-154">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="d251d-155">Použití stránky spouštěče však může zjednodušit inicializaci průvodce, zejména pokud je inicializace složitá.</span><span class="sxs-lookup"><span data-stu-id="d251d-155">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
- <span data-ttu-id="d251d-156">Uživatelé mohou přecházet mezi stránkami pomocí tlačítek Zpět a Vpřed (nebo hypertextových odkazů).</span><span class="sxs-lookup"><span data-stu-id="d251d-156">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
- <span data-ttu-id="d251d-157">Uživatelé mohou procházet mezi stránkami pomocí deníku.</span><span class="sxs-lookup"><span data-stu-id="d251d-157">Users can navigate between pages using the journal.</span></span>  
  
- <span data-ttu-id="d251d-158">Uživatelé mohou změnit navigační pořadí, pokud projdou zpět deníkem.</span><span class="sxs-lookup"><span data-stu-id="d251d-158">Users can change the navigation sequence if they navigate back through the journal.</span></span>  
  
- <span data-ttu-id="d251d-159">Uživatelé mohou zrušit průvodce z libovolné stránky průvodce stisknutím tlačítka Storno.</span><span class="sxs-lookup"><span data-stu-id="d251d-159">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
- <span data-ttu-id="d251d-160">Uživatelé mohou průvodce přijmout na poslední stránce průvodce stisknutím tlačítka Dokončit.</span><span class="sxs-lookup"><span data-stu-id="d251d-160">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
- <span data-ttu-id="d251d-161">Pokud je průvodce zrušen, vrátí odpovídající výsledek a nevrátí žádná data.</span><span class="sxs-lookup"><span data-stu-id="d251d-161">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
- <span data-ttu-id="d251d-162">Pokud uživatel přijme průvodce, vrátí odpovídající výsledek a vrátí shromážděná data.</span><span class="sxs-lookup"><span data-stu-id="d251d-162">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
- <span data-ttu-id="d251d-163">Po dokončení průvodce (přijato nebo zrušeno) budou stránky, které průvodce obsahuje, odebrány z deníku.</span><span class="sxs-lookup"><span data-stu-id="d251d-163">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="d251d-164">To udržuje každou instanci průvodce izolované, čímž se zabrání potenciální data nebo státní anomálie.</span><span class="sxs-lookup"><span data-stu-id="d251d-164">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>
## <a name="navigation-over-a-dynamically-generated-topology"></a><span data-ttu-id="d251d-165">Navigace přes dynamicky generovanou topologii</span><span class="sxs-lookup"><span data-stu-id="d251d-165">Navigation over a Dynamically Generated Topology</span></span>  
 <span data-ttu-id="d251d-166">V některých aplikacích pořadí, ve kterém jsou procházeny dvě nebo více stránek lze určit pouze za běhu, ať už uživatelem, aplikace nebo externí data.</span><span class="sxs-lookup"><span data-stu-id="d251d-166">In some applications, the sequence in which two or more pages are navigated can only be determined at run time, whether by the user, the application, or external data.</span></span> <span data-ttu-id="d251d-167">Následující obrázek znázorňuje sadu stránek s neurčenou navigační sekvencí:</span><span class="sxs-lookup"><span data-stu-id="d251d-167">The following figure illustrates a set of pages with an undetermined navigation sequence:</span></span>  
  
 ![Sada stránek s neurčenou navigační sekvencí.](./media/navigation-topologies-overview/navigation-topology-dynamically-generated.png)  
  
 <span data-ttu-id="d251d-169">Následující obrázek znázorňuje navigační sekvenci, která byla vybrána uživatelem za běhu:</span><span class="sxs-lookup"><span data-stu-id="d251d-169">The next figure illustrates a navigation sequence that was chosen by the user at run time:</span></span>  
  
 ![Diagram, který zobrazuje navigační sekvenci zvolenou za běhu.](./media/navigation-topologies-overview/navigation-topology-sequence-chosen-run-time.png)  
  
 <span data-ttu-id="d251d-171">Navigační sekvence se označuje jako dynamicky generovaná topologie.</span><span class="sxs-lookup"><span data-stu-id="d251d-171">The navigation sequence is known as a dynamically generated topology.</span></span> <span data-ttu-id="d251d-172">Pro uživatele, stejně jako u ostatních topologie navigace, uživatelské prostředí je stejné jako pro předchozí topologie:</span><span class="sxs-lookup"><span data-stu-id="d251d-172">For the user, as with the other navigation topologies, the user experience is the same as it is for the previous topologies:</span></span>  
  
- <span data-ttu-id="d251d-173">Přechod ze stránky volajícího na stránku spouštěče, která inicializuje průvodce a přejde na první stránku průvodce.</span><span class="sxs-lookup"><span data-stu-id="d251d-173">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="d251d-174">Stránka spouštěče [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)](a <xref:System.Windows.Navigation.PageFunction%601>-less) není vyžadována, protože volající stránka může volat přímo první stránku průvodce.</span><span class="sxs-lookup"><span data-stu-id="d251d-174">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="d251d-175">Použití stránky spouštěče však může zjednodušit inicializaci průvodce, zejména pokud je inicializace složitá.</span><span class="sxs-lookup"><span data-stu-id="d251d-175">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
- <span data-ttu-id="d251d-176">Uživatelé mohou přecházet mezi stránkami pomocí tlačítek Zpět a Vpřed (nebo hypertextových odkazů).</span><span class="sxs-lookup"><span data-stu-id="d251d-176">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
- <span data-ttu-id="d251d-177">Uživatelé mohou procházet mezi stránkami pomocí deníku.</span><span class="sxs-lookup"><span data-stu-id="d251d-177">Users can navigate between pages using the journal.</span></span>  
  
- <span data-ttu-id="d251d-178">Uživatelé mohou zrušit průvodce z libovolné stránky průvodce stisknutím tlačítka Storno.</span><span class="sxs-lookup"><span data-stu-id="d251d-178">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
- <span data-ttu-id="d251d-179">Uživatelé mohou průvodce přijmout na poslední stránce průvodce stisknutím tlačítka Dokončit.</span><span class="sxs-lookup"><span data-stu-id="d251d-179">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
- <span data-ttu-id="d251d-180">Pokud je průvodce zrušen, vrátí odpovídající výsledek a nevrátí žádná data.</span><span class="sxs-lookup"><span data-stu-id="d251d-180">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
- <span data-ttu-id="d251d-181">Pokud uživatel přijme průvodce, vrátí odpovídající výsledek a vrátí shromážděná data.</span><span class="sxs-lookup"><span data-stu-id="d251d-181">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
- <span data-ttu-id="d251d-182">Po dokončení průvodce (přijato nebo zrušeno) budou stránky, které průvodce obsahuje, odebrány z deníku.</span><span class="sxs-lookup"><span data-stu-id="d251d-182">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="d251d-183">To udržuje každou instanci průvodce izolované, čímž se zabrání potenciální data nebo státní anomálie.</span><span class="sxs-lookup"><span data-stu-id="d251d-183">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d251d-184">Viz také</span><span class="sxs-lookup"><span data-stu-id="d251d-184">See also</span></span>

- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [<span data-ttu-id="d251d-185">Přehled strukturované navigace</span><span class="sxs-lookup"><span data-stu-id="d251d-185">Structured Navigation Overview</span></span>](structured-navigation-overview.md)
