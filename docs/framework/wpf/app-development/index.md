---
title: Vývoj aplikací
description: Naučte se vytvářet různé aplikace pomocí architektury Windows Presentation Foundation (WPF).
ms.date: 01/26/2018
helpviewer_keywords:
- WPF [WPF], about application development
- application development [WPF], about
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
ms.openlocfilehash: ac4227785f2fc398217b3aa8984176844264bbaa
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85613732"
---
# <a name="application-development"></a><span data-ttu-id="198be-103">Vývoj aplikací</span><span class="sxs-lookup"><span data-stu-id="198be-103">Application Development</span></span>
<a name="introduction"></a><span data-ttu-id="198be-104">Windows Presentation Foundation (WPF) je prezentační rozhraní, které lze použít k vývoji následujících typů aplikací:</span><span class="sxs-lookup"><span data-stu-id="198be-104">Windows Presentation Foundation (WPF) is a presentation framework that can be used to develop the following types of applications:</span></span>  
  
- <span data-ttu-id="198be-105">Samostatné aplikace (tradiční styly aplikací pro Windows postavené jako spustitelná sestavení, která jsou nainstalovaná a spouštěná z klientského počítače).</span><span class="sxs-lookup"><span data-stu-id="198be-105">Standalone Applications (traditional style Windows applications built as executable assemblies that are installed to and run from the client computer).</span></span>  
  
- <span data-ttu-id="198be-106">Aplikace prohlížeče XAML (XBAP) (aplikace tvořené navigačními stránkami, které jsou sestaveny jako spustitelná sestavení a hostovány webovými prohlížeči, jako je například Microsoft Internet Explorer nebo Mozilla Firefox).</span><span class="sxs-lookup"><span data-stu-id="198be-106">XAML browser applications (XBAPs) (applications composed of navigation pages that are built as executable assemblies and hosted by Web browsers such as Microsoft Internet Explorer or Mozilla Firefox).</span></span>  
  
- <span data-ttu-id="198be-107">Vlastní knihovny ovládacích prvků (nespustitelná sestavení obsahující opakovaně použitelné ovládací prvky).</span><span class="sxs-lookup"><span data-stu-id="198be-107">Custom Control Libraries (non-executable assemblies containing reusable controls).</span></span>  
  
- <span data-ttu-id="198be-108">Knihovny tříd (nespustitelná sestavení, která obsahují opakovaně použitelné třídy).</span><span class="sxs-lookup"><span data-stu-id="198be-108">Class Libraries (non-executable assemblies that contain reusable classes).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="198be-109">Použití typů WPF ve službě systému Windows se důrazně nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="198be-109">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="198be-110">Pokud se pokusíte tyto funkce použít ve službě systému Windows, nemusí fungovat podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="198be-110">If you attempt to use these features in a Windows service, they may not work as expected.</span></span>  
  
 <span data-ttu-id="198be-111">Pro sestavení této sady aplikací WPF implementuje hostitele služeb.</span><span class="sxs-lookup"><span data-stu-id="198be-111">To build this set of applications, WPF implements a host of services.</span></span> <span data-ttu-id="198be-112">V tomto tématu najdete přehled těchto služeb a kde najdete další informace.</span><span class="sxs-lookup"><span data-stu-id="198be-112">This topic provides an overview of these services and where to find more information.</span></span>  

<a name="Application_Management"></a>
## <a name="application-management"></a><span data-ttu-id="198be-113">Správa aplikací</span><span class="sxs-lookup"><span data-stu-id="198be-113">Application Management</span></span>  
 <span data-ttu-id="198be-114">Spustitelné aplikace WPF běžně vyžadují základní sadu funkcí, které zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="198be-114">Executable WPF applications commonly require a core set of functionality that includes the following:</span></span>  
  
- <span data-ttu-id="198be-115">Vytvoření a Správa běžné aplikační infrastruktury (včetně vytvoření metody vstupního bodu a smyčky zpráv systému Windows pro příjem systémových a vstupních zpráv).</span><span class="sxs-lookup"><span data-stu-id="198be-115">Creating and managing common application infrastructure (including creating an entry point method and a Windows message loop to receive system and input messages).</span></span>  
  
- <span data-ttu-id="198be-116">Sledování a interakce s životností aplikace.</span><span class="sxs-lookup"><span data-stu-id="198be-116">Tracking and interacting with the lifetime of an application.</span></span>  
  
- <span data-ttu-id="198be-117">Načítání a zpracování parametrů příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="198be-117">Retrieving and processing command-line parameters.</span></span>  
  
- <span data-ttu-id="198be-118">Sdílení vlastností a prostředků oboru aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]</span><span class="sxs-lookup"><span data-stu-id="198be-118">Sharing application-scope properties and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] resources.</span></span>  
  
- <span data-ttu-id="198be-119">Zjišťování a zpracování neošetřených výjimek.</span><span class="sxs-lookup"><span data-stu-id="198be-119">Detecting and processing unhandled exceptions.</span></span>  
  
- <span data-ttu-id="198be-120">Vracení ukončovacích kódů</span><span class="sxs-lookup"><span data-stu-id="198be-120">Returning exit codes.</span></span>  
  
- <span data-ttu-id="198be-121">Správa systému Windows v samostatných aplikacích.</span><span class="sxs-lookup"><span data-stu-id="198be-121">Managing windows in standalone applications.</span></span>  
  
- <span data-ttu-id="198be-122">Sledování navigace v aplikacích prohlížeče XAML (XBAP) a samostatné aplikace s navigačními okny a snímky.</span><span class="sxs-lookup"><span data-stu-id="198be-122">Tracking navigation in XAML browser applications (XBAPs), and standalone applications with navigation windows and frames.</span></span>  
  
 <span data-ttu-id="198be-123">Tyto možnosti jsou implementovány <xref:System.Windows.Application> třídou, kterou přidáte do aplikací pomocí *definice aplikace*.</span><span class="sxs-lookup"><span data-stu-id="198be-123">These capabilities are implemented by the <xref:System.Windows.Application> class, which you add to your applications using an *application definition*.</span></span>  
  
 <span data-ttu-id="198be-124">Další informace najdete v tématu [Přehled správy aplikací](application-management-overview.md).</span><span class="sxs-lookup"><span data-stu-id="198be-124">For more information, see [Application Management Overview](application-management-overview.md).</span></span>  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>
## <a name="wpf-application-resource-content-and-data-files"></a><span data-ttu-id="198be-125">Zdroj, obsah a datové soubory zdroje aplikací WPF</span><span class="sxs-lookup"><span data-stu-id="198be-125">WPF Application Resource, Content, and Data Files</span></span>  
 <span data-ttu-id="198be-126">WPF rozšiřuje základní podporu v Microsoft .NET Framework pro vložené prostředky a podporuje tři druhy nespustitelných datových souborů: zdroj, obsah a data.</span><span class="sxs-lookup"><span data-stu-id="198be-126">WPF extends the core support in the Microsoft .NET Framework for embedded resources with support for three kinds of non-executable data files: resource, content, and data.</span></span> <span data-ttu-id="198be-127">Další informace naleznete v tématu [prostředky aplikace WPF, obsah a datové soubory](wpf-application-resource-content-and-data-files.md).</span><span class="sxs-lookup"><span data-stu-id="198be-127">For more information, see [WPF Application Resource, Content, and Data Files](wpf-application-resource-content-and-data-files.md).</span></span>  
  
 <span data-ttu-id="198be-128">Klíčovou součástí podpory pro nespustitelné datové soubory WPF je schopnost identifikovat a načíst je pomocí jedinečného identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="198be-128">A key component of the support for WPF non-executable data files is the ability to identify and load them using a unique URI.</span></span> <span data-ttu-id="198be-129">Další informace najdete v tématu [identifikátory URI Pack v](pack-uris-in-wpf.md)subsystému WPF.</span><span class="sxs-lookup"><span data-stu-id="198be-129">For more information, see [Pack URIs in WPF](pack-uris-in-wpf.md).</span></span>  
  
<a name="Windows_and_Dialog_Boxes"></a>
## <a name="windows-and-dialog-boxes"></a><span data-ttu-id="198be-130">Okna a dialogová okna</span><span class="sxs-lookup"><span data-stu-id="198be-130">Windows and Dialog Boxes</span></span>  
 <span data-ttu-id="198be-131">Uživatelé pracují se samostatnými aplikacemi WPF prostřednictvím systému Windows.</span><span class="sxs-lookup"><span data-stu-id="198be-131">Users interact with WPF standalone applications through windows.</span></span> <span data-ttu-id="198be-132">Účelem okna je hostování obsahu aplikace a vystavení funkcí aplikace, které obvykle uživatelům umožňují pracovat s obsahem.</span><span class="sxs-lookup"><span data-stu-id="198be-132">The purpose of a window is to host application content and expose application functionality that usually allows users to interact with the content.</span></span> <span data-ttu-id="198be-133">V technologii WPF jsou okna zapouzdřena <xref:System.Windows.Window> třídou, která podporuje:</span><span class="sxs-lookup"><span data-stu-id="198be-133">In WPF, windows are encapsulated by the <xref:System.Windows.Window> class, which supports:</span></span>  
  
- <span data-ttu-id="198be-134">Vytváření a zobrazování oken.</span><span class="sxs-lookup"><span data-stu-id="198be-134">Creating and showing windows.</span></span>  
  
- <span data-ttu-id="198be-135">Vytváření vztahů mezi vlastníkem a vlastníkem okna.</span><span class="sxs-lookup"><span data-stu-id="198be-135">Establishing owner/owned window relationships.</span></span>  
  
- <span data-ttu-id="198be-136">Konfigurace vzhledu okna (například velikost, umístění, ikony, text záhlaví, ohraničení).</span><span class="sxs-lookup"><span data-stu-id="198be-136">Configuring window appearance (for example, size, location, icons, title bar text, border).</span></span>  
  
- <span data-ttu-id="198be-137">Sledování a interakce s dobou života okna.</span><span class="sxs-lookup"><span data-stu-id="198be-137">Tracking and interacting with the lifetime of a window.</span></span>  
  
 <span data-ttu-id="198be-138">Další informace najdete v tématu [Přehled Windows WPF](wpf-windows-overview.md).</span><span class="sxs-lookup"><span data-stu-id="198be-138">For more information, see [WPF Windows Overview](wpf-windows-overview.md).</span></span>  
  
 <span data-ttu-id="198be-139"><xref:System.Windows.Window>podporuje možnost vytvoření speciálního typu okna označovaného jako dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="198be-139"><xref:System.Windows.Window> supports the ability to create a special type of window known as a dialog box.</span></span> <span data-ttu-id="198be-140">Lze vytvořit modální i nemodální typy dialogových oken.</span><span class="sxs-lookup"><span data-stu-id="198be-140">Both modal and modeless types of dialog boxes can be created.</span></span>  
  
 <span data-ttu-id="198be-141">Pro usnadnění a výhody opětovné použitelnosti a konzistentní uživatelské prostředí napříč aplikacemi poskytuje WPF tři z dialogových oken běžné Windows: <xref:Microsoft.Win32.OpenFileDialog> , a <xref:Microsoft.Win32.SaveFileDialog> <xref:System.Windows.Controls.PrintDialog> .</span><span class="sxs-lookup"><span data-stu-id="198be-141">For convenience, and the benefits of reusability and a consistent user experience across applications, WPF exposes three of the common Windows dialog boxes: <xref:Microsoft.Win32.OpenFileDialog>, <xref:Microsoft.Win32.SaveFileDialog>, and <xref:System.Windows.Controls.PrintDialog>.</span></span>  
  
 <span data-ttu-id="198be-142">Okno se zprávou je speciální typ dialogového okna pro zobrazení důležitých textových informací uživatelům a pro dotazování jednoduchých dotazů Ano/Ne/OK/zrušit.</span><span class="sxs-lookup"><span data-stu-id="198be-142">A message box is a special type of dialog box for showing important textual information to users, and for asking simple Yes/No/OK/Cancel questions.</span></span> <span data-ttu-id="198be-143">Třídu můžete použít <xref:System.Windows.MessageBox> k vytvoření a zobrazení oken se zprávami.</span><span class="sxs-lookup"><span data-stu-id="198be-143">You use the <xref:System.Windows.MessageBox> class to create and show message boxes.</span></span>  
  
 <span data-ttu-id="198be-144">Další informace najdete v tématu [Přehled dialogových oken](dialog-boxes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="198be-144">For more information, see [Dialog Boxes Overview](dialog-boxes-overview.md).</span></span>  
  
<a name="Navigation"></a>
## <a name="navigation"></a><span data-ttu-id="198be-145">Navigace</span><span class="sxs-lookup"><span data-stu-id="198be-145">Navigation</span></span>  
 <span data-ttu-id="198be-146">WPF podporuje navigaci na webovém stylu pomocí stránek ( <xref:System.Windows.Controls.Page> ) a hypertextových odkazů ( <xref:System.Windows.Documents.Hyperlink> ).</span><span class="sxs-lookup"><span data-stu-id="198be-146">WPF supports Web-style navigation using pages (<xref:System.Windows.Controls.Page>) and hyperlinks (<xref:System.Windows.Documents.Hyperlink>).</span></span> <span data-ttu-id="198be-147">Navigace může být implementována různými způsoby, které zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="198be-147">Navigation can be implemented in a variety of ways that include the following:</span></span>  
  
- <span data-ttu-id="198be-148">Samostatné stránky, které jsou hostovány ve webovém prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="198be-148">Standalone pages that are hosted in a Web browser.</span></span>  
  
- <span data-ttu-id="198be-149">Stránky zkompilované do XBAP, která je hostována ve webovém prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="198be-149">Pages compiled into an XBAP that is hosted in a Web browser.</span></span>  
  
- <span data-ttu-id="198be-150">Stránky zkompilované do samostatné aplikace a hostované v navigačním okně ( <xref:System.Windows.Navigation.NavigationWindow> ).</span><span class="sxs-lookup"><span data-stu-id="198be-150">Pages compiled into a standalone application and hosted by a navigation window (<xref:System.Windows.Navigation.NavigationWindow>).</span></span>  
  
- <span data-ttu-id="198be-151">Stránky, které jsou hostovány rámcem ( <xref:System.Windows.Controls.Frame> ), které mohou být hostovány na samostatné stránce nebo na stránce zkompilované do aplikace XBAP nebo samostatné aplikace.</span><span class="sxs-lookup"><span data-stu-id="198be-151">Pages that are hosted by a frame (<xref:System.Windows.Controls.Frame>), which may be hosted in a standalone page, or a page compiled into either an XBAP or a standalone application.</span></span>  
  
 <span data-ttu-id="198be-152">Pro usnadnění navigace WPF implementuje následující:</span><span class="sxs-lookup"><span data-stu-id="198be-152">To facilitate navigation, WPF implements the following:</span></span>  
  
- <span data-ttu-id="198be-153"><xref:System.Windows.Navigation.NavigationService>sdílený navigační modul pro zpracování žádostí o navigaci používaných aplikacemi <xref:System.Windows.Controls.Frame> , <xref:System.Windows.Navigation.NavigationWindow> a XBAP pro podporu navigace uvnitř aplikace.</span><span class="sxs-lookup"><span data-stu-id="198be-153"><xref:System.Windows.Navigation.NavigationService>, the shared navigation engine for processing navigation requests that is used by <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>, and XBAPs to support intra-application navigation.</span></span>  
  
- <span data-ttu-id="198be-154">Navigační metody pro zahájení navigace</span><span class="sxs-lookup"><span data-stu-id="198be-154">Navigation methods to initiate navigation.</span></span>  
  
- <span data-ttu-id="198be-155">Navigační události pro sledování a interakci s dobou života navigace</span><span class="sxs-lookup"><span data-stu-id="198be-155">Navigation events to track and interact with navigation lifetime.</span></span>  
  
- <span data-ttu-id="198be-156">Zapamatování navigace zpět a přeposlání pomocí deníku, který lze také kontrolovat a manipulovat.</span><span class="sxs-lookup"><span data-stu-id="198be-156">Remembering back and forward navigation using a journal, which can also be inspected and manipulated.</span></span>  
  
 <span data-ttu-id="198be-157">Informace najdete v tématu [Přehled navigace](navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="198be-157">For information, see [Navigation Overview](navigation-overview.md).</span></span>  
  
 <span data-ttu-id="198be-158">WPF také podporuje speciální typ navigace známý jako strukturovaná navigace.</span><span class="sxs-lookup"><span data-stu-id="198be-158">WPF also supports a special type of navigation known as structured navigation.</span></span> <span data-ttu-id="198be-159">Strukturované navigace lze použít k volání jedné nebo více stránek, které vracejí data strukturovaným a předvídatelným způsobem, který je konzistentní s voláním funkce.</span><span class="sxs-lookup"><span data-stu-id="198be-159">Structured navigation can be used to call one or more pages that return data in a structured and predictable way that is consistent with calling functions.</span></span> <span data-ttu-id="198be-160">Tato schopnost závisí na <xref:System.Windows.Navigation.PageFunction%601> třídě, která je podrobněji popsána v [přehledu strukturované navigace](structured-navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="198be-160">This capability depends on the <xref:System.Windows.Navigation.PageFunction%601> class, which is described further in [Structured Navigation Overview](structured-navigation-overview.md).</span></span> <span data-ttu-id="198be-161"><xref:System.Windows.Navigation.PageFunction%601>slouží také ke zjednodušení vytváření komplexních navigačních topologií, které jsou popsány v tématu [Přehled topologií navigace](navigation-topologies-overview.md).</span><span class="sxs-lookup"><span data-stu-id="198be-161"><xref:System.Windows.Navigation.PageFunction%601> also serves to simplify the creation of complex navigation topologies, which are described in [Navigation Topologies Overview](navigation-topologies-overview.md).</span></span>  
  
<a name="Hosting"></a>
## <a name="hosting"></a><span data-ttu-id="198be-162">Hosting</span><span class="sxs-lookup"><span data-stu-id="198be-162">Hosting</span></span>  
 <span data-ttu-id="198be-163">Aplikace XBAP je možné hostovat v aplikacích Microsoft Internet Explorer a Firefox.</span><span class="sxs-lookup"><span data-stu-id="198be-163">XBAPs can be hosted in Microsoft Internet Explorer or Firefox.</span></span> <span data-ttu-id="198be-164">Každý model hostování má vlastní sadu důležitých informací a omezení, které jsou pokryty v [hostování](hosting-wpf-applications.md).</span><span class="sxs-lookup"><span data-stu-id="198be-164">Each hosting model has its own set of considerations and constraints that are covered in [Hosting](hosting-wpf-applications.md).</span></span>  
  
<a name="Build_and_Deploy"></a>
## <a name="build-and-deploy"></a><span data-ttu-id="198be-165">Sestavení a nasazení</span><span class="sxs-lookup"><span data-stu-id="198be-165">Build and Deploy</span></span>  
 <span data-ttu-id="198be-166">I když jednoduché aplikace WPF mohou být sestaveny z příkazového řádku pomocí kompilátorů příkazového řádku, WPF se integruje se sadou Visual Studio a poskytuje další podporu, která zjednodušuje proces vývoje a sestavování.</span><span class="sxs-lookup"><span data-stu-id="198be-166">Although simple WPF applications can be built from a command prompt using command-line compilers, WPF integrates with Visual Studio to provide additional support that simplified the development and build process.</span></span> <span data-ttu-id="198be-167">Další informace naleznete v tématu [sestavování aplikace WPF](building-a-wpf-application-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="198be-167">For more information, see [Building a WPF Application](building-a-wpf-application-wpf.md).</span></span>  
  
 <span data-ttu-id="198be-168">V závislosti na typu aplikace, kterou sestavíte, existuje jedna nebo více možností nasazení, ze kterých si můžete vybrat.</span><span class="sxs-lookup"><span data-stu-id="198be-168">Depending on the type of application you build, there are one or more deployment options to choose from.</span></span> <span data-ttu-id="198be-169">Další informace naleznete v tématu [nasazení aplikace WPF](deploying-a-wpf-application-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="198be-169">For more information, see [Deploying a WPF Application](deploying-a-wpf-application-wpf.md).</span></span>  
  
<a name="related_topics"></a>
## <a name="related-topics"></a><span data-ttu-id="198be-170">Související témata</span><span class="sxs-lookup"><span data-stu-id="198be-170">Related Topics</span></span>  
  
|<span data-ttu-id="198be-171">Nadpis</span><span class="sxs-lookup"><span data-stu-id="198be-171">Title</span></span>|<span data-ttu-id="198be-172">Popis</span><span class="sxs-lookup"><span data-stu-id="198be-172">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="198be-173">Přehled správy aplikací</span><span class="sxs-lookup"><span data-stu-id="198be-173">Application Management Overview</span></span>](application-management-overview.md)|<span data-ttu-id="198be-174">Poskytuje přehled <xref:System.Windows.Application> třídy, včetně správy životního cyklu aplikací, Windows, prostředků aplikací a navigace.</span><span class="sxs-lookup"><span data-stu-id="198be-174">Provides an overview of the <xref:System.Windows.Application> class including managing application lifetime, windows, application resources, and navigation.</span></span>|  
|[<span data-ttu-id="198be-175">Okna ve WPF</span><span class="sxs-lookup"><span data-stu-id="198be-175">Windows in WPF</span></span>](windows-in-wpf-applications.md)|<span data-ttu-id="198be-176">Obsahuje podrobnosti o správě oken v aplikaci, včetně způsobu použití <xref:System.Windows.Window> polí a dialogových oken.</span><span class="sxs-lookup"><span data-stu-id="198be-176">Provides details of managing windows in your application including how to use the <xref:System.Windows.Window> class and dialog boxes.</span></span>|  
|[<span data-ttu-id="198be-177">Přehled navigace</span><span class="sxs-lookup"><span data-stu-id="198be-177">Navigation Overview</span></span>](navigation-overview.md)|<span data-ttu-id="198be-178">Poskytuje přehled o správě navigace mezi stránkami aplikace.</span><span class="sxs-lookup"><span data-stu-id="198be-178">Provides an overview of managing navigation between pages of your application.</span></span>|  
|[<span data-ttu-id="198be-179">Hosting</span><span class="sxs-lookup"><span data-stu-id="198be-179">Hosting</span></span>](hosting-wpf-applications.md)|<span data-ttu-id="198be-180">Poskytuje přehled aplikací prohlížeče XAML (XBAP).</span><span class="sxs-lookup"><span data-stu-id="198be-180">Provides an overview of XAML browser applications (XBAPs).</span></span>|  
|[<span data-ttu-id="198be-181">Sestavení a nasazení</span><span class="sxs-lookup"><span data-stu-id="198be-181">Build and Deploy</span></span>](building-and-deploying-wpf-applications.md)|<span data-ttu-id="198be-182">Popisuje, jak sestavit a nasadit vaši aplikaci WPF.</span><span class="sxs-lookup"><span data-stu-id="198be-182">Describes how to build and deploy your WPF application.</span></span>|  
|[<span data-ttu-id="198be-183">Úvod k použití WPF v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="198be-183">Introduction to WPF in Visual Studio</span></span>](../getting-started/introduction-to-wpf-in-vs.md)|<span data-ttu-id="198be-184">Popisuje hlavní funkce WPF.</span><span class="sxs-lookup"><span data-stu-id="198be-184">Describes the main features of WPF.</span></span>|  
|[<span data-ttu-id="198be-185">Návod: Moje první desktopová aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="198be-185">Walkthrough: My first WPF desktop application</span></span>](../getting-started/walkthrough-my-first-wpf-desktop-application.md)|<span data-ttu-id="198be-186">Návod, který ukazuje, jak vytvořit aplikaci WPF pomocí navigace na stránce, rozložení, ovládacích prvků, obrázků, stylů a vazeb.</span><span class="sxs-lookup"><span data-stu-id="198be-186">A walkthrough that shows how to create a WPF application using page navigation, layout, controls, images, styles, and binding.</span></span>|
