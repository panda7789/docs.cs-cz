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
ms.openlocfilehash: 5679bac06b87b3c4e50cbc4a238d7daf3e33a564
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636273"
---
# <a name="navigation-topologies-overview"></a><span data-ttu-id="50c39-102">Přehled topologií navigace</span><span class="sxs-lookup"><span data-stu-id="50c39-102">Navigation Topologies Overview</span></span>
<a name="introduction"></a><span data-ttu-id="50c39-103">Tento přehled poskytuje Úvod do topologií navigace v WPF.</span><span class="sxs-lookup"><span data-stu-id="50c39-103">This overview provides an introduction to navigation topologies in WPF.</span></span> <span data-ttu-id="50c39-104">Následně jsou popsány tři běžné topologie navigace s ukázkami.</span><span class="sxs-lookup"><span data-stu-id="50c39-104">Three common navigation topologies, with samples, are subsequently discussed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="50c39-105">Před čtením tohoto tématu byste měli být obeznámeni s konceptem strukturované navigace ve WPF pomocí funkcí stránky.</span><span class="sxs-lookup"><span data-stu-id="50c39-105">Before reading this topic, you should be familiar with the concept of structured navigation in WPF using page functions.</span></span> <span data-ttu-id="50c39-106">Další informace o obou těchto tématech najdete v tématu [Přehled strukturované navigace](structured-navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="50c39-106">For more information on both of these topics, see [Structured Navigation Overview](structured-navigation-overview.md).</span></span>  
  
 <span data-ttu-id="50c39-107">Toto téma obsahuje následující oddíly:</span><span class="sxs-lookup"><span data-stu-id="50c39-107">This topic contains the following sections:</span></span>  
  
- [<span data-ttu-id="50c39-108">Topologie navigace</span><span class="sxs-lookup"><span data-stu-id="50c39-108">Navigation Topologies</span></span>](#Navigation_Topologies)  
  
- [<span data-ttu-id="50c39-109">Strukturované navigační topologie</span><span class="sxs-lookup"><span data-stu-id="50c39-109">Structured Navigation Topologies</span></span>](#Structured_Navigation_Topologies)  
  
- [<span data-ttu-id="50c39-110">Navigace přes pevnou lineární topologii</span><span class="sxs-lookup"><span data-stu-id="50c39-110">Navigation over a Fixed Linear Topology</span></span>](#Navigation_over_a_Fixed_Linear_Topology)  
  
- [<span data-ttu-id="50c39-111">Dynamická navigace nad pevnou hierarchickou topologií</span><span class="sxs-lookup"><span data-stu-id="50c39-111">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
- [<span data-ttu-id="50c39-112">Navigace prostřednictvím dynamicky generované topologie</span><span class="sxs-lookup"><span data-stu-id="50c39-112">Navigation over a Dynamically Generated Topology</span></span>](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>   
## <a name="navigation-topologies"></a><span data-ttu-id="50c39-113">Topologie navigace</span><span class="sxs-lookup"><span data-stu-id="50c39-113">Navigation Topologies</span></span>  
 <span data-ttu-id="50c39-114">V WPF se navigace obvykle skládá ze stránek (<xref:System.Windows.Controls.Page>) s hypertextovými odkazy (<xref:System.Windows.Documents.Hyperlink>), které po kliknutí přejdou na jiné stránky.</span><span class="sxs-lookup"><span data-stu-id="50c39-114">In WPF, navigation typically consists of pages (<xref:System.Windows.Controls.Page>) with hyperlinks (<xref:System.Windows.Documents.Hyperlink>) that navigate to other pages when clicked.</span></span> <span data-ttu-id="50c39-115">Stránky, na které se navigují, se identifikují pomocí identifikátorů URI (Uniform Resource Identifier) (viz [identifikátory URI balíčku v WPF](pack-uris-in-wpf.md)).</span><span class="sxs-lookup"><span data-stu-id="50c39-115">Pages that are navigated to are identified by uniform resource identifiers (URIs) (see [Pack URIs in WPF](pack-uris-in-wpf.md)).</span></span> <span data-ttu-id="50c39-116">Vezměte v úvahu následující jednoduchý příklad, který ukazuje stránky, hypertextové odkazy a identifikátory URI (Uniform Resource Identifier):</span><span class="sxs-lookup"><span data-stu-id="50c39-116">Consider the following simple example that shows pages, hyperlinks, and uniform resource identifiers (URIs):</span></span>  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 <span data-ttu-id="50c39-117">Tyto stránky jsou uspořádány do *navigační topologie* , jejíž struktura je určena podle toho, jak můžete mezi stránkami přecházet.</span><span class="sxs-lookup"><span data-stu-id="50c39-117">These pages are arranged in a *navigation topology* whose structure is determined by how you can navigate between the pages.</span></span> <span data-ttu-id="50c39-118">Tato konkrétní navigační topologie je vhodná v jednoduchých scénářích, i když navigace může vyžadovat složitější topologie, některé z nich lze definovat pouze v případě, že je aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="50c39-118">This particular navigation topology is suitable in simple scenarios, although navigation can require more complex topologies, some of which can only be defined when an application is running.</span></span>  
  
 <span data-ttu-id="50c39-119">V tomto tématu se dozvíte o třech běžných topologiích navigace: *pevné lineární*, *pevné hierarchické*a *dynamicky generované*.</span><span class="sxs-lookup"><span data-stu-id="50c39-119">This topic covers three common navigation topologies: *fixed linear*, *fixed hierarchical*, and *dynamically generated*.</span></span> <span data-ttu-id="50c39-120">Každá navigační topologie je znázorněna s ukázkou, která má [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] jako na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="50c39-120">Each navigation topology is demonstrated with a sample that has a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] like the one that is shown in the following figure:</span></span>  
  
 ![Stránky úloh s datovými položkami a navigačními tlačítky.](./media/navigation-topologies-overview/navigation-topology-data-items.png)  
  
<a name="Structured_Navigation_Topologies"></a>   
## <a name="structured-navigation-topologies"></a><span data-ttu-id="50c39-122">Strukturované navigační topologie</span><span class="sxs-lookup"><span data-stu-id="50c39-122">Structured Navigation Topologies</span></span>  
 <span data-ttu-id="50c39-123">Existují dva široké typy topologií navigace:</span><span class="sxs-lookup"><span data-stu-id="50c39-123">There are two broad types of navigation topologies:</span></span>  
  
- <span data-ttu-id="50c39-124">**Pevná topologie**: definována v době kompilace a v době běhu se nemění.</span><span class="sxs-lookup"><span data-stu-id="50c39-124">**Fixed Topology**: defined at compile time and does not change at run time.</span></span> <span data-ttu-id="50c39-125">Pevné topologie jsou užitečné pro navigaci prostřednictvím pevné sekvence stránek lineárním nebo hierarchickém řazením.</span><span class="sxs-lookup"><span data-stu-id="50c39-125">Fixed topologies are useful for navigation through a fixed sequence of pages in either a linear or hierarchical order.</span></span>  
  
- <span data-ttu-id="50c39-126">**Dynamická topologie**: definuje se v době běhu na základě vstupu, který se shromažďuje od uživatele, aplikace nebo systému.</span><span class="sxs-lookup"><span data-stu-id="50c39-126">**Dynamic Topology**: defined at run time based on input that is collected from the user, the application, or the system.</span></span> <span data-ttu-id="50c39-127">Dynamické topologie jsou užitečné, když lze stránky procházet v různých sekvencích.</span><span class="sxs-lookup"><span data-stu-id="50c39-127">Dynamic topologies are useful when pages can be navigated in different sequences.</span></span>  
  
 <span data-ttu-id="50c39-128">I když je možné vytvořit navigační topologie pomocí stránek, ukázky používají funkce stránky, protože poskytují další podporu, která zjednodušuje podporu pro předávání a vracení dat prostřednictvím stránek topologie.</span><span class="sxs-lookup"><span data-stu-id="50c39-128">Although it is possible to create navigation topologies using pages, the samples use page functions because they provide additional support that simplifies support for passing and returning data through the pages of a topology.</span></span>  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>   
## <a name="navigation-over-a-fixed-linear-topology"></a><span data-ttu-id="50c39-129">Navigace přes pevnou lineární topologii</span><span class="sxs-lookup"><span data-stu-id="50c39-129">Navigation over a Fixed Linear Topology</span></span>  
 <span data-ttu-id="50c39-130">Pevná lineární topologie je podobná struktuře průvodce, který obsahuje jednu nebo více stránek průvodce, které jsou v pevné sekvenci.</span><span class="sxs-lookup"><span data-stu-id="50c39-130">A fixed linear topology is analogous to the structure of a wizard that has one or more wizard pages that are navigated in a fixed sequence.</span></span> <span data-ttu-id="50c39-131">Následující obrázek ukazuje strukturu vysoké úrovně a tok průvodce s pevnou lineární topologií:</span><span class="sxs-lookup"><span data-stu-id="50c39-131">The following figure shows the high-level structure and flow of a wizard with a fixed linear topology:</span></span>  
  
 ![Diagram, který zobrazuje pevnou lineární topologii.](./media/navigation-topologies-overview/navigation-topology-fixed-linear.png)  
  
 <span data-ttu-id="50c39-133">Typické chování pro navigaci přes pevnou lineární topologii zahrnuje následující:</span><span class="sxs-lookup"><span data-stu-id="50c39-133">The typical behaviors for navigating over a fixed linear topology include the following:</span></span>  
  
- <span data-ttu-id="50c39-134">Přechod z volající stránky na stránku spouštěče, která inicializuje průvodce a přejde na první stránku průvodce.</span><span class="sxs-lookup"><span data-stu-id="50c39-134">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="50c39-135">Stránka spouštěče ([!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]bez <xref:System.Windows.Navigation.PageFunction%601>) není vyžadována, protože volající stránka může zavolat první stránku průvodce přímo.</span><span class="sxs-lookup"><span data-stu-id="50c39-135">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="50c39-136">Použití stránky spouštěče může ale zjednodušit inicializaci průvodce, zejména v případě, že je inicializace složitá.</span><span class="sxs-lookup"><span data-stu-id="50c39-136">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
- <span data-ttu-id="50c39-137">Uživatelé mohou procházet mezi stránkami pomocí tlačítek zpět a vpřed (nebo hypertextových odkazů).</span><span class="sxs-lookup"><span data-stu-id="50c39-137">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
- <span data-ttu-id="50c39-138">Uživatelé mohou procházet mezi stránkami pomocí deníku.</span><span class="sxs-lookup"><span data-stu-id="50c39-138">Users can navigate between pages using the journal.</span></span>  
  
- <span data-ttu-id="50c39-139">Uživatelé mohou zrušit průvodce z libovolné stránky průvodce stisknutím tlačítka zrušit.</span><span class="sxs-lookup"><span data-stu-id="50c39-139">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
- <span data-ttu-id="50c39-140">Kliknutím na tlačítko Dokončit můžete uživatelům přijmout Průvodce na poslední stránce průvodce.</span><span class="sxs-lookup"><span data-stu-id="50c39-140">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
- <span data-ttu-id="50c39-141">Pokud se Průvodce zruší, průvodce vrátí příslušný výsledek a nevrátí žádná data.</span><span class="sxs-lookup"><span data-stu-id="50c39-141">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
- <span data-ttu-id="50c39-142">Pokud uživatel Průvodce přijme, průvodce vrátí příslušný výsledek a vrátí shromážděná data.</span><span class="sxs-lookup"><span data-stu-id="50c39-142">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
- <span data-ttu-id="50c39-143">Po dokončení průvodce (přijatý nebo zrušený) se z deníku odeberou stránky, které průvodce obsahuje.</span><span class="sxs-lookup"><span data-stu-id="50c39-143">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="50c39-144">Tím se udržuje všechny instance průvodce izolované, takže se vyhnete potenciálním anomáliím dat nebo stavu.</span><span class="sxs-lookup"><span data-stu-id="50c39-144">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>   
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a><span data-ttu-id="50c39-145">Dynamická navigace nad pevnou hierarchickou topologií</span><span class="sxs-lookup"><span data-stu-id="50c39-145">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>  
 <span data-ttu-id="50c39-146">V některých aplikacích stránky umožňují navigaci na dvě nebo více dalších stránek, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="50c39-146">In some applications, pages allow navigation to two or more other pages, as shown in the following figure:</span></span> 
  
 ![Diagram, který zobrazuje stránku, která může přejít na více stránek.](./media/navigation-topologies-overview/navigation-topology-multiple-pages.png)  
  
 <span data-ttu-id="50c39-148">Tato struktura je známá jako pevná hierarchická topologie a pořadí, ve kterém je hierarchie procházena, je často určeno v době spuštění aplikací nebo uživatelem.</span><span class="sxs-lookup"><span data-stu-id="50c39-148">This structure is known as a fixed hierarchical topology, and the sequence in which the hierarchy is traversed is often determined at run time by either the application or the user.</span></span> <span data-ttu-id="50c39-149">V době spuštění každá stránka v hierarchii, která umožňuje navigaci na dvě nebo více dalších stránek, shromažďuje data potřebná k určení stránky, na kterou se má přejít.</span><span class="sxs-lookup"><span data-stu-id="50c39-149">At run time, each page in the hierarchy that allows navigation to two or more other pages gathers the data required to determine which page to navigate to.</span></span> <span data-ttu-id="50c39-150">Následující obrázek znázorňuje jednu z několika možných navigačních sekvencí v závislosti na předchozím obrázku:</span><span class="sxs-lookup"><span data-stu-id="50c39-150">The following figure illustrates one of several possible navigation sequences based on the previous figure:</span></span>  
  
 ![Diagram, který zobrazuje možnou navigační sekvenci.](./media/navigation-topologies-overview/navigation-topology-fixed-hierarchical.png)  
  
 <span data-ttu-id="50c39-152">I když je pořadí, ve kterém se stránky v pevné hierarchické struktuře procházejí, určuje za běhu, činnost koncového uživatele je stejná jako činnost koncového uživatele pro pevnou lineární topologii:</span><span class="sxs-lookup"><span data-stu-id="50c39-152">Even though the sequence in which pages in a fixed hierarchical structure are navigated is determined at run time, the user experience is the same as the user experience for a fixed linear topology:</span></span>  
  
- <span data-ttu-id="50c39-153">Přechod z volající stránky na stránku spouštěče, která inicializuje průvodce a přejde na první stránku průvodce.</span><span class="sxs-lookup"><span data-stu-id="50c39-153">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="50c39-154">Stránka spouštěče ([!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]bez <xref:System.Windows.Navigation.PageFunction%601>) není vyžadována, protože volající stránka může zavolat první stránku průvodce přímo.</span><span class="sxs-lookup"><span data-stu-id="50c39-154">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="50c39-155">Použití stránky spouštěče může ale zjednodušit inicializaci průvodce, zejména v případě, že je inicializace složitá.</span><span class="sxs-lookup"><span data-stu-id="50c39-155">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
- <span data-ttu-id="50c39-156">Uživatelé mohou procházet mezi stránkami pomocí tlačítek zpět a vpřed (nebo hypertextových odkazů).</span><span class="sxs-lookup"><span data-stu-id="50c39-156">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
- <span data-ttu-id="50c39-157">Uživatelé mohou procházet mezi stránkami pomocí deníku.</span><span class="sxs-lookup"><span data-stu-id="50c39-157">Users can navigate between pages using the journal.</span></span>  
  
- <span data-ttu-id="50c39-158">Uživatelé mohou navigační sekvenci změnit, pokud procházejí zpět prostřednictvím deníku.</span><span class="sxs-lookup"><span data-stu-id="50c39-158">Users can change the navigation sequence if they navigate back through the journal.</span></span>  
  
- <span data-ttu-id="50c39-159">Uživatelé mohou zrušit průvodce z libovolné stránky průvodce stisknutím tlačítka zrušit.</span><span class="sxs-lookup"><span data-stu-id="50c39-159">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
- <span data-ttu-id="50c39-160">Kliknutím na tlačítko Dokončit můžete uživatelům přijmout Průvodce na poslední stránce průvodce.</span><span class="sxs-lookup"><span data-stu-id="50c39-160">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
- <span data-ttu-id="50c39-161">Pokud se Průvodce zruší, průvodce vrátí příslušný výsledek a nevrátí žádná data.</span><span class="sxs-lookup"><span data-stu-id="50c39-161">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
- <span data-ttu-id="50c39-162">Pokud uživatel Průvodce přijme, průvodce vrátí příslušný výsledek a vrátí shromážděná data.</span><span class="sxs-lookup"><span data-stu-id="50c39-162">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
- <span data-ttu-id="50c39-163">Po dokončení průvodce (přijatý nebo zrušený) se z deníku odeberou stránky, které průvodce obsahuje.</span><span class="sxs-lookup"><span data-stu-id="50c39-163">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="50c39-164">Tím se udržuje všechny instance průvodce izolované, takže se vyhnete potenciálním anomáliím dat nebo stavu.</span><span class="sxs-lookup"><span data-stu-id="50c39-164">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>   
## <a name="navigation-over-a-dynamically-generated-topology"></a><span data-ttu-id="50c39-165">Navigace prostřednictvím dynamicky generované topologie</span><span class="sxs-lookup"><span data-stu-id="50c39-165">Navigation over a Dynamically Generated Topology</span></span>  
 <span data-ttu-id="50c39-166">V některých aplikacích je pořadí, ve kterém se dvě nebo více stránek prochází, dá určit jenom za běhu, ať už podle uživatele, aplikace nebo externích dat.</span><span class="sxs-lookup"><span data-stu-id="50c39-166">In some applications, the sequence in which two or more pages are navigated can only be determined at run time, whether by the user, the application, or external data.</span></span> <span data-ttu-id="50c39-167">Následující obrázek znázorňuje sadu stránek s neurčenou navigační sekvencí:</span><span class="sxs-lookup"><span data-stu-id="50c39-167">The following figure illustrates a set of pages with an undetermined navigation sequence:</span></span>  
  
 ![Sada stránek s neurčenou navigační sekvencí.](./media/navigation-topologies-overview/navigation-topology-dynamically-generated.png)  
  
 <span data-ttu-id="50c39-169">Následující obrázek znázorňuje navigační sekvenci, kterou uživatel zvolil v době běhu:</span><span class="sxs-lookup"><span data-stu-id="50c39-169">The next figure illustrates a navigation sequence that was chosen by the user at run time:</span></span>  
  
 ![Diagram, který zobrazuje navigační sekvenci zvolenou v době běhu.](./media/navigation-topologies-overview/navigation-topology-sequence-chosen-run-time.png)  
  
 <span data-ttu-id="50c39-171">Navigační sekvence je označována jako dynamicky generovaná topologie.</span><span class="sxs-lookup"><span data-stu-id="50c39-171">The navigation sequence is known as a dynamically generated topology.</span></span> <span data-ttu-id="50c39-172">Pro uživatele stejně jako u ostatních topologií navigace je prostředí uživatele stejné jako u předchozích topologií:</span><span class="sxs-lookup"><span data-stu-id="50c39-172">For the user, as with the other navigation topologies, the user experience is the same as it is for the previous topologies:</span></span>  
  
- <span data-ttu-id="50c39-173">Přechod z volající stránky na stránku spouštěče, která inicializuje průvodce a přejde na první stránku průvodce.</span><span class="sxs-lookup"><span data-stu-id="50c39-173">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="50c39-174">Stránka spouštěče ([!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]bez <xref:System.Windows.Navigation.PageFunction%601>) není vyžadována, protože volající stránka může zavolat první stránku průvodce přímo.</span><span class="sxs-lookup"><span data-stu-id="50c39-174">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="50c39-175">Použití stránky spouštěče může ale zjednodušit inicializaci průvodce, zejména v případě, že je inicializace složitá.</span><span class="sxs-lookup"><span data-stu-id="50c39-175">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
- <span data-ttu-id="50c39-176">Uživatelé mohou procházet mezi stránkami pomocí tlačítek zpět a vpřed (nebo hypertextových odkazů).</span><span class="sxs-lookup"><span data-stu-id="50c39-176">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
- <span data-ttu-id="50c39-177">Uživatelé mohou procházet mezi stránkami pomocí deníku.</span><span class="sxs-lookup"><span data-stu-id="50c39-177">Users can navigate between pages using the journal.</span></span>  
  
- <span data-ttu-id="50c39-178">Uživatelé mohou zrušit průvodce z libovolné stránky průvodce stisknutím tlačítka zrušit.</span><span class="sxs-lookup"><span data-stu-id="50c39-178">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
- <span data-ttu-id="50c39-179">Kliknutím na tlačítko Dokončit můžete uživatelům přijmout Průvodce na poslední stránce průvodce.</span><span class="sxs-lookup"><span data-stu-id="50c39-179">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
- <span data-ttu-id="50c39-180">Pokud se Průvodce zruší, průvodce vrátí příslušný výsledek a nevrátí žádná data.</span><span class="sxs-lookup"><span data-stu-id="50c39-180">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
- <span data-ttu-id="50c39-181">Pokud uživatel Průvodce přijme, průvodce vrátí příslušný výsledek a vrátí shromážděná data.</span><span class="sxs-lookup"><span data-stu-id="50c39-181">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
- <span data-ttu-id="50c39-182">Po dokončení průvodce (přijatý nebo zrušený) se z deníku odeberou stránky, které průvodce obsahuje.</span><span class="sxs-lookup"><span data-stu-id="50c39-182">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="50c39-183">Tím se udržuje všechny instance průvodce izolované, takže se vyhnete potenciálním anomáliím dat nebo stavu.</span><span class="sxs-lookup"><span data-stu-id="50c39-183">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50c39-184">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50c39-184">See also</span></span>

- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [<span data-ttu-id="50c39-185">Přehled strukturované navigace</span><span class="sxs-lookup"><span data-stu-id="50c39-185">Structured Navigation Overview</span></span>](structured-navigation-overview.md)
