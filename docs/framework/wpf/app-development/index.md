---
title: Vývoj aplikací
ms.date: 01/26/2018
helpviewer_keywords:
- WPF [WPF], about application development
- application development [WPF], about
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
ms.openlocfilehash: 5ff9f58b72982f79e70b80f60c10828c3b54e5bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186006"
---
# <a name="application-development"></a><span data-ttu-id="a82d1-102">Vývoj aplikací</span><span class="sxs-lookup"><span data-stu-id="a82d1-102">Application Development</span></span>
<a name="introduction"></a><span data-ttu-id="a82d1-103">Windows Presentation Foundation (WPF) je prezentační architektura, kterou lze použít k vývoji následujících typů aplikací:</span><span class="sxs-lookup"><span data-stu-id="a82d1-103">Windows Presentation Foundation (WPF) is a presentation framework that can be used to develop the following types of applications:</span></span>  
  
- <span data-ttu-id="a82d1-104">Samostatné aplikace (tradiční styl aplikace systému Windows vytvořené jako spustitelná sestavení, která jsou nainstalována do klientského počítače a spouštěna z ní).</span><span class="sxs-lookup"><span data-stu-id="a82d1-104">Standalone Applications (traditional style Windows applications built as executable assemblies that are installed to and run from the client computer).</span></span>  
  
- <span data-ttu-id="a82d1-105">Aplikace prohlížeče XAML (XBAPs) (aplikace složené z navigačních stránek, které jsou vytvořeny jako spustitelná sestavení a hostované webovými prohlížeči, jako je Microsoft Internet Explorer nebo Mozilla Firefox).</span><span class="sxs-lookup"><span data-stu-id="a82d1-105">XAML browser applications (XBAPs) (applications composed of navigation pages that are built as executable assemblies and hosted by Web browsers such as Microsoft Internet Explorer or Mozilla Firefox).</span></span>  
  
- <span data-ttu-id="a82d1-106">Vlastní knihovny ovládacích prvků (nespustitelná sestavení obsahující opakovaně použitelné ovládací prvky).</span><span class="sxs-lookup"><span data-stu-id="a82d1-106">Custom Control Libraries (non-executable assemblies containing reusable controls).</span></span>  
  
- <span data-ttu-id="a82d1-107">Knihovny tříd (nespustitelná sestavení, která obsahují opakovaně použitelné třídy).</span><span class="sxs-lookup"><span data-stu-id="a82d1-107">Class Libraries (non-executable assemblies that contain reusable classes).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a82d1-108">Použití wpf typů ve službě systému Windows se důrazně nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="a82d1-108">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="a82d1-109">Pokud se pokusíte použít tyto funkce ve službě systému Windows, nemusí fungovat podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="a82d1-109">If you attempt to use these features in a Windows service, they may not work as expected.</span></span>  
  
 <span data-ttu-id="a82d1-110">Chcete-li vytvořit tuto sadu aplikací, WPF implementuje celou řadu služeb.</span><span class="sxs-lookup"><span data-stu-id="a82d1-110">To build this set of applications, WPF implements a host of services.</span></span> <span data-ttu-id="a82d1-111">Toto téma obsahuje přehled těchto služeb a kde najít další informace.</span><span class="sxs-lookup"><span data-stu-id="a82d1-111">This topic provides an overview of these services and where to find more information.</span></span>  

<a name="Application_Management"></a>
## <a name="application-management"></a><span data-ttu-id="a82d1-112">Správa aplikací</span><span class="sxs-lookup"><span data-stu-id="a82d1-112">Application Management</span></span>  
 <span data-ttu-id="a82d1-113">Spustitelné aplikace WPF obvykle vyžadují základní sadu funkcí, která zahrnuje následující:</span><span class="sxs-lookup"><span data-stu-id="a82d1-113">Executable WPF applications commonly require a core set of functionality that includes the following:</span></span>  
  
- <span data-ttu-id="a82d1-114">Vytváření a správa společné aplikační infrastruktury (včetně vytvoření metody vstupního bodu a smyčky zpráv systému Windows pro příjem systémových a vstupních zpráv).</span><span class="sxs-lookup"><span data-stu-id="a82d1-114">Creating and managing common application infrastructure (including creating an entry point method and a Windows message loop to receive system and input messages).</span></span>  
  
- <span data-ttu-id="a82d1-115">Sledování a interakce s životností aplikace.</span><span class="sxs-lookup"><span data-stu-id="a82d1-115">Tracking and interacting with the lifetime of an application.</span></span>  
  
- <span data-ttu-id="a82d1-116">Načítání a zpracování parametrů příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="a82d1-116">Retrieving and processing command-line parameters.</span></span>  
  
- <span data-ttu-id="a82d1-117">Sdílení vlastností a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prostředků oboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="a82d1-117">Sharing application-scope properties and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] resources.</span></span>  
  
- <span data-ttu-id="a82d1-118">Zjišťování a zpracování neošetřených výjimek.</span><span class="sxs-lookup"><span data-stu-id="a82d1-118">Detecting and processing unhandled exceptions.</span></span>  
  
- <span data-ttu-id="a82d1-119">Vracím únikové kódy.</span><span class="sxs-lookup"><span data-stu-id="a82d1-119">Returning exit codes.</span></span>  
  
- <span data-ttu-id="a82d1-120">Správa oken v samostatných aplikacích.</span><span class="sxs-lookup"><span data-stu-id="a82d1-120">Managing windows in standalone applications.</span></span>  
  
- <span data-ttu-id="a82d1-121">Sledování navigace v aplikacích prohlížeče XAML (XBAPs) a samostatných aplikacích s navigačními okny a rámečky.</span><span class="sxs-lookup"><span data-stu-id="a82d1-121">Tracking navigation in XAML browser applications (XBAPs), and standalone applications with navigation windows and frames.</span></span>  
  
 <span data-ttu-id="a82d1-122">Tyto funkce jsou <xref:System.Windows.Application> implementovány třídou, kterou přidáte do aplikací pomocí *definice aplikace*.</span><span class="sxs-lookup"><span data-stu-id="a82d1-122">These capabilities are implemented by the <xref:System.Windows.Application> class, which you add to your applications using an *application definition*.</span></span>  
  
 <span data-ttu-id="a82d1-123">Další informace naleznete v [tématu Application Management Overview](application-management-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a82d1-123">For more information, see [Application Management Overview](application-management-overview.md).</span></span>  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>
## <a name="wpf-application-resource-content-and-data-files"></a><span data-ttu-id="a82d1-124">Zdroj, obsah a datové soubory zdroje aplikací WPF</span><span class="sxs-lookup"><span data-stu-id="a82d1-124">WPF Application Resource, Content, and Data Files</span></span>  
 <span data-ttu-id="a82d1-125">WPF rozšiřuje základní podporu v rozhraní Microsoft .NET Framework pro vložené prostředky s podporou pro tři druhy nespustitelných datových souborů: prostředek, obsah a data.</span><span class="sxs-lookup"><span data-stu-id="a82d1-125">WPF extends the core support in the Microsoft .NET Framework for embedded resources with support for three kinds of non-executable data files: resource, content, and data.</span></span> <span data-ttu-id="a82d1-126">Další informace naleznete v [tématu WPF Aplikační zdroj, obsah a datové soubory](wpf-application-resource-content-and-data-files.md).</span><span class="sxs-lookup"><span data-stu-id="a82d1-126">For more information, see [WPF Application Resource, Content, and Data Files](wpf-application-resource-content-and-data-files.md).</span></span>  
  
 <span data-ttu-id="a82d1-127">Klíčovou součástí podpory nespustitelných datových souborů WPF je schopnost identifikovat a načíst je pomocí jedinečného identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="a82d1-127">A key component of the support for WPF non-executable data files is the ability to identify and load them using a unique URI.</span></span> <span data-ttu-id="a82d1-128">Další informace naleznete [v tématu Pack URI v WPF](pack-uris-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="a82d1-128">For more information, see [Pack URIs in WPF](pack-uris-in-wpf.md).</span></span>  
  
<a name="Windows_and_Dialog_Boxes"></a>
## <a name="windows-and-dialog-boxes"></a><span data-ttu-id="a82d1-129">Okna a dialogová okna</span><span class="sxs-lookup"><span data-stu-id="a82d1-129">Windows and Dialog Boxes</span></span>  
 <span data-ttu-id="a82d1-130">Uživatelé interagují se samostatnými aplikacemi WPF prostřednictvím oken.</span><span class="sxs-lookup"><span data-stu-id="a82d1-130">Users interact with WPF standalone applications through windows.</span></span> <span data-ttu-id="a82d1-131">Účelem okna je hostovat obsah aplikace a zpřístupnit funkce aplikace, které obvykle umožňují uživatelům pracovat s obsahem.</span><span class="sxs-lookup"><span data-stu-id="a82d1-131">The purpose of a window is to host application content and expose application functionality that usually allows users to interact with the content.</span></span> <span data-ttu-id="a82d1-132">V WPF jsou okna zapouzdřena třídou, <xref:System.Windows.Window> která podporuje:</span><span class="sxs-lookup"><span data-stu-id="a82d1-132">In WPF, windows are encapsulated by the <xref:System.Windows.Window> class, which supports:</span></span>  
  
- <span data-ttu-id="a82d1-133">Vytváření a zobrazování oken.</span><span class="sxs-lookup"><span data-stu-id="a82d1-133">Creating and showing windows.</span></span>  
  
- <span data-ttu-id="a82d1-134">Vytvoření vztahů mezi vlastníkem/vlastněným oknem.</span><span class="sxs-lookup"><span data-stu-id="a82d1-134">Establishing owner/owned window relationships.</span></span>  
  
- <span data-ttu-id="a82d1-135">Konfigurace vzhledu okna (například velikost, umístění, ikony, text záhlaví, ohraničení).</span><span class="sxs-lookup"><span data-stu-id="a82d1-135">Configuring window appearance (for example, size, location, icons, title bar text, border).</span></span>  
  
- <span data-ttu-id="a82d1-136">Sledování a interakce s životností okna.</span><span class="sxs-lookup"><span data-stu-id="a82d1-136">Tracking and interacting with the lifetime of a window.</span></span>  
  
 <span data-ttu-id="a82d1-137">Další informace naleznete v tématu [WPF Windows Overview](wpf-windows-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a82d1-137">For more information, see [WPF Windows Overview](wpf-windows-overview.md).</span></span>  
  
 <span data-ttu-id="a82d1-138"><xref:System.Windows.Window>podporuje možnost vytvořit speciální typ okna známého jako dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="a82d1-138"><xref:System.Windows.Window> supports the ability to create a special type of window known as a dialog box.</span></span> <span data-ttu-id="a82d1-139">Lze vytvořit modální i nemodální typy dialogových oken.</span><span class="sxs-lookup"><span data-stu-id="a82d1-139">Both modal and modeless types of dialog boxes can be created.</span></span>  
  
 <span data-ttu-id="a82d1-140">Pro větší pohodlí a výhody opětovného použití a konzistentní uživatelské prostředí napříč aplikacemi wpf <xref:Microsoft.Win32.SaveFileDialog>zveřejňuje <xref:System.Windows.Controls.PrintDialog>tři běžná dialogová okna systému Windows: <xref:Microsoft.Win32.OpenFileDialog>, , a .</span><span class="sxs-lookup"><span data-stu-id="a82d1-140">For convenience, and the benefits of reusability and a consistent user experience across applications, WPF exposes three of the common Windows dialog boxes: <xref:Microsoft.Win32.OpenFileDialog>, <xref:Microsoft.Win32.SaveFileDialog>, and <xref:System.Windows.Controls.PrintDialog>.</span></span>  
  
 <span data-ttu-id="a82d1-141">Okno se zprávou je speciální typ dialogového okna pro zobrazení důležitých textových informací uživatelům a pro kladení jednoduchých otázek Ano/Ne/OK/Zrušení.</span><span class="sxs-lookup"><span data-stu-id="a82d1-141">A message box is a special type of dialog box for showing important textual information to users, and for asking simple Yes/No/OK/Cancel questions.</span></span> <span data-ttu-id="a82d1-142">Třídu <xref:System.Windows.MessageBox> slouží k vytvoření a zobrazení oken zpráv.</span><span class="sxs-lookup"><span data-stu-id="a82d1-142">You use the <xref:System.Windows.MessageBox> class to create and show message boxes.</span></span>  
  
 <span data-ttu-id="a82d1-143">Další informace naleznete v [tématu Přehled dialogových oken](dialog-boxes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a82d1-143">For more information, see [Dialog Boxes Overview](dialog-boxes-overview.md).</span></span>  
  
<a name="Navigation"></a>
## <a name="navigation"></a><span data-ttu-id="a82d1-144">Navigace</span><span class="sxs-lookup"><span data-stu-id="a82d1-144">Navigation</span></span>  
 <span data-ttu-id="a82d1-145">WPF podporuje webovou navigaci<xref:System.Windows.Controls.Page>pomocí stránek (<xref:System.Windows.Documents.Hyperlink>) a hypertextových odkazů ( ).</span><span class="sxs-lookup"><span data-stu-id="a82d1-145">WPF supports Web-style navigation using pages (<xref:System.Windows.Controls.Page>) and hyperlinks (<xref:System.Windows.Documents.Hyperlink>).</span></span> <span data-ttu-id="a82d1-146">Navigace může být implementována různými způsoby, které zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="a82d1-146">Navigation can be implemented in a variety of ways that include the following:</span></span>  
  
- <span data-ttu-id="a82d1-147">Samostatné stránky, které jsou hostovány ve webovém prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="a82d1-147">Standalone pages that are hosted in a Web browser.</span></span>  
  
- <span data-ttu-id="a82d1-148">Stránky zkompilované do XBAP, který je hostován ve webovém prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="a82d1-148">Pages compiled into an XBAP that is hosted in a Web browser.</span></span>  
  
- <span data-ttu-id="a82d1-149">Stránky zkompilované do samostatné aplikace a hostované navigačním oknem (<xref:System.Windows.Navigation.NavigationWindow>).</span><span class="sxs-lookup"><span data-stu-id="a82d1-149">Pages compiled into a standalone application and hosted by a navigation window (<xref:System.Windows.Navigation.NavigationWindow>).</span></span>  
  
- <span data-ttu-id="a82d1-150">Stránky, které jsou hostovány<xref:System.Windows.Controls.Frame>rámcem ( ), které mohou být hostovány na samostatné stránce, nebo stránky zkompilované do XBAP nebo samostatné aplikace.</span><span class="sxs-lookup"><span data-stu-id="a82d1-150">Pages that are hosted by a frame (<xref:System.Windows.Controls.Frame>), which may be hosted in a standalone page, or a page compiled into either an XBAP or a standalone application.</span></span>  
  
 <span data-ttu-id="a82d1-151">Pro usnadnění navigace wpf implementuje následující:</span><span class="sxs-lookup"><span data-stu-id="a82d1-151">To facilitate navigation, WPF implements the following:</span></span>  
  
- <span data-ttu-id="a82d1-152"><xref:System.Windows.Navigation.NavigationService>, sdílený navigační modul pro zpracování navigačních <xref:System.Windows.Controls.Frame> <xref:System.Windows.Navigation.NavigationWindow>požadavků používaných aplikacemi , a XBAPs pro podporu navigace v rámci aplikace.</span><span class="sxs-lookup"><span data-stu-id="a82d1-152"><xref:System.Windows.Navigation.NavigationService>, the shared navigation engine for processing navigation requests that is used by <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>, and XBAPs to support intra-application navigation.</span></span>  
  
- <span data-ttu-id="a82d1-153">Navigační metody pro zahájení navigace.</span><span class="sxs-lookup"><span data-stu-id="a82d1-153">Navigation methods to initiate navigation.</span></span>  
  
- <span data-ttu-id="a82d1-154">Navigační události pro sledování a interakci s životností navigace.</span><span class="sxs-lookup"><span data-stu-id="a82d1-154">Navigation events to track and interact with navigation lifetime.</span></span>  
  
- <span data-ttu-id="a82d1-155">Zapamatování zpět a vpřed navigace pomocí deníku, který může být také kontrolována a manipulovat.</span><span class="sxs-lookup"><span data-stu-id="a82d1-155">Remembering back and forward navigation using a journal, which can also be inspected and manipulated.</span></span>  
  
 <span data-ttu-id="a82d1-156">Další informace naleznete v [tématu Navigační přehled](navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a82d1-156">For information, see [Navigation Overview](navigation-overview.md).</span></span>  
  
 <span data-ttu-id="a82d1-157">WPF také podporuje speciální typ navigace známý jako strukturované navigace.</span><span class="sxs-lookup"><span data-stu-id="a82d1-157">WPF also supports a special type of navigation known as structured navigation.</span></span> <span data-ttu-id="a82d1-158">Strukturované navigace lze volat jednu nebo více stránek, které vracejí data strukturovaným a předvídatelným způsobem, který je konzistentní s volající funkce.</span><span class="sxs-lookup"><span data-stu-id="a82d1-158">Structured navigation can be used to call one or more pages that return data in a structured and predictable way that is consistent with calling functions.</span></span> <span data-ttu-id="a82d1-159">Tato funkce závisí <xref:System.Windows.Navigation.PageFunction%601> na třídě, která je popsána dále ve [strukturované navigační přehled](structured-navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a82d1-159">This capability depends on the <xref:System.Windows.Navigation.PageFunction%601> class, which is described further in [Structured Navigation Overview](structured-navigation-overview.md).</span></span> <span data-ttu-id="a82d1-160"><xref:System.Windows.Navigation.PageFunction%601>slouží také ke zjednodušení vytváření složitých navigačních topologie, které jsou popsány v [přehledu navigačních topologií](navigation-topologies-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a82d1-160"><xref:System.Windows.Navigation.PageFunction%601> also serves to simplify the creation of complex navigation topologies, which are described in [Navigation Topologies Overview](navigation-topologies-overview.md).</span></span>  
  
<a name="Hosting"></a>
## <a name="hosting"></a><span data-ttu-id="a82d1-161">Hostování</span><span class="sxs-lookup"><span data-stu-id="a82d1-161">Hosting</span></span>  
 <span data-ttu-id="a82d1-162">XBAPs mohou být hostovány v aplikaci Microsoft Internet Explorer nebo Firefox.</span><span class="sxs-lookup"><span data-stu-id="a82d1-162">XBAPs can be hosted in Microsoft Internet Explorer or Firefox.</span></span> <span data-ttu-id="a82d1-163">Každý hostingový model má svou vlastní sadu úvah a omezení, které jsou zahrnuty v [Hostingu](hosting-wpf-applications.md).</span><span class="sxs-lookup"><span data-stu-id="a82d1-163">Each hosting model has its own set of considerations and constraints that are covered in [Hosting](hosting-wpf-applications.md).</span></span>  
  
<a name="Build_and_Deploy"></a>
## <a name="build-and-deploy"></a><span data-ttu-id="a82d1-164">Sestavení a nasazení</span><span class="sxs-lookup"><span data-stu-id="a82d1-164">Build and Deploy</span></span>  
 <span data-ttu-id="a82d1-165">Přestože jednoduché wpf aplikace lze sestavit z příkazového řádku pomocí kompilátorů příkazového řádku, WPF integruje s Visual Studio poskytovat další podporu, která zjednodušuje vývoj a proces sestavení.</span><span class="sxs-lookup"><span data-stu-id="a82d1-165">Although simple WPF applications can be built from a command prompt using command-line compilers, WPF integrates with Visual Studio to provide additional support that simplified the development and build process.</span></span> <span data-ttu-id="a82d1-166">Další informace naleznete [v tématu Vytváření aplikace WPF](building-a-wpf-application-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="a82d1-166">For more information, see [Building a WPF Application](building-a-wpf-application-wpf.md).</span></span>  
  
 <span data-ttu-id="a82d1-167">V závislosti na typu aplikace, kterou vytvoříte, existuje jedna nebo více možností nasazení, ze kterých si můžete vybrat.</span><span class="sxs-lookup"><span data-stu-id="a82d1-167">Depending on the type of application you build, there are one or more deployment options to choose from.</span></span> <span data-ttu-id="a82d1-168">Další informace naleznete [v tématu Nasazení aplikace WPF](deploying-a-wpf-application-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="a82d1-168">For more information, see [Deploying a WPF Application](deploying-a-wpf-application-wpf.md).</span></span>  
  
<a name="related_topics"></a>
## <a name="related-topics"></a><span data-ttu-id="a82d1-169">Související témata</span><span class="sxs-lookup"><span data-stu-id="a82d1-169">Related Topics</span></span>  
  
|<span data-ttu-id="a82d1-170">Nadpis</span><span class="sxs-lookup"><span data-stu-id="a82d1-170">Title</span></span>|<span data-ttu-id="a82d1-171">Popis</span><span class="sxs-lookup"><span data-stu-id="a82d1-171">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="a82d1-172">Přehled správy aplikací</span><span class="sxs-lookup"><span data-stu-id="a82d1-172">Application Management Overview</span></span>](application-management-overview.md)|<span data-ttu-id="a82d1-173">Obsahuje přehled třídy včetně správy životnosti <xref:System.Windows.Application> aplikace, oken, prostředků aplikace a navigace.</span><span class="sxs-lookup"><span data-stu-id="a82d1-173">Provides an overview of the <xref:System.Windows.Application> class including managing application lifetime, windows, application resources, and navigation.</span></span>|  
|[<span data-ttu-id="a82d1-174">Okna ve WPF</span><span class="sxs-lookup"><span data-stu-id="a82d1-174">Windows in WPF</span></span>](windows-in-wpf-applications.md)|<span data-ttu-id="a82d1-175">Obsahuje podrobnosti o správě oken v <xref:System.Windows.Window> aplikaci, včetně použití třídy a dialogových oken.</span><span class="sxs-lookup"><span data-stu-id="a82d1-175">Provides details of managing windows in your application including how to use the <xref:System.Windows.Window> class and dialog boxes.</span></span>|  
|[<span data-ttu-id="a82d1-176">Přehled navigace</span><span class="sxs-lookup"><span data-stu-id="a82d1-176">Navigation Overview</span></span>](navigation-overview.md)|<span data-ttu-id="a82d1-177">Obsahuje přehled správy navigace mezi stránkami aplikace.</span><span class="sxs-lookup"><span data-stu-id="a82d1-177">Provides an overview of managing navigation between pages of your application.</span></span>|  
|[<span data-ttu-id="a82d1-178">Hostování</span><span class="sxs-lookup"><span data-stu-id="a82d1-178">Hosting</span></span>](hosting-wpf-applications.md)|<span data-ttu-id="a82d1-179">Obsahuje přehled aplikací prohlížeče XAML (XBAPs).</span><span class="sxs-lookup"><span data-stu-id="a82d1-179">Provides an overview of XAML browser applications (XBAPs).</span></span>|  
|[<span data-ttu-id="a82d1-180">Sestavení a nasazení</span><span class="sxs-lookup"><span data-stu-id="a82d1-180">Build and Deploy</span></span>](building-and-deploying-wpf-applications.md)|<span data-ttu-id="a82d1-181">Popisuje, jak vytvořit a nasadit aplikaci WPF.</span><span class="sxs-lookup"><span data-stu-id="a82d1-181">Describes how to build and deploy your WPF application.</span></span>|  
|[<span data-ttu-id="a82d1-182">Úvod k použití WPF v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a82d1-182">Introduction to WPF in Visual Studio</span></span>](../getting-started/introduction-to-wpf-in-vs.md)|<span data-ttu-id="a82d1-183">Popisuje hlavní rysy WPF.</span><span class="sxs-lookup"><span data-stu-id="a82d1-183">Describes the main features of WPF.</span></span>|  
|[<span data-ttu-id="a82d1-184">Návod: Moje první desktopová aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="a82d1-184">Walkthrough: My first WPF desktop application</span></span>](../getting-started/walkthrough-my-first-wpf-desktop-application.md)|<span data-ttu-id="a82d1-185">Návod, který ukazuje, jak vytvořit aplikaci WPF pomocí navigace na stránce, rozložení, ovládací prvky, obrázky, styly a vazby.</span><span class="sxs-lookup"><span data-stu-id="a82d1-185">A walkthrough that shows how to create a WPF application using page navigation, layout, controls, images, styles, and binding.</span></span>|
