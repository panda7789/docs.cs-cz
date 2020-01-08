---
title: Vývoj aplikací
ms.date: 01/26/2018
helpviewer_keywords:
- WPF [WPF], about application development
- application development [WPF], about
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
ms.openlocfilehash: b0bdf49e0bb3d9bfa3fc4e7fd94aa68ee4ea0bb3
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636390"
---
# <a name="application-development"></a><span data-ttu-id="14737-102">Vývoj aplikací</span><span class="sxs-lookup"><span data-stu-id="14737-102">Application Development</span></span>
<a name="introduction"></a><span data-ttu-id="14737-103">Windows Presentation Foundation (WPF) je prezentační rozhraní, které lze použít k vývoji následujících typů aplikací:</span><span class="sxs-lookup"><span data-stu-id="14737-103">Windows Presentation Foundation (WPF) is a presentation framework that can be used to develop the following types of applications:</span></span>  
  
- <span data-ttu-id="14737-104">Samostatné aplikace (tradiční styly aplikací pro Windows postavené jako spustitelná sestavení, která jsou nainstalovaná a spouštěná z klientského počítače).</span><span class="sxs-lookup"><span data-stu-id="14737-104">Standalone Applications (traditional style Windows applications built as executable assemblies that are installed to and run from the client computer).</span></span>  
  
- <span data-ttu-id="14737-105">Aplikace prohlížeče XAML (XBAP) (aplikace tvořené navigačními stránkami, které jsou sestaveny jako spustitelná sestavení a hostovány webovými prohlížeči, jako je například Microsoft Internet Explorer nebo Mozilla Firefox).</span><span class="sxs-lookup"><span data-stu-id="14737-105">XAML browser applications (XBAPs) (applications composed of navigation pages that are built as executable assemblies and hosted by Web browsers such as Microsoft Internet Explorer or Mozilla Firefox).</span></span>  
  
- <span data-ttu-id="14737-106">Vlastní knihovny ovládacích prvků (nespustitelná sestavení obsahující opakovaně použitelné ovládací prvky).</span><span class="sxs-lookup"><span data-stu-id="14737-106">Custom Control Libraries (non-executable assemblies containing reusable controls).</span></span>  
  
- <span data-ttu-id="14737-107">Knihovny tříd (nespustitelná sestavení, která obsahují opakovaně použitelné třídy).</span><span class="sxs-lookup"><span data-stu-id="14737-107">Class Libraries (non-executable assemblies that contain reusable classes).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="14737-108">Použití typů WPF ve službě systému Windows se důrazně nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="14737-108">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="14737-109">Pokud se pokusíte tyto funkce použít ve službě systému Windows, nemusí fungovat podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="14737-109">If you attempt to use these features in a Windows service, they may not work as expected.</span></span>  
  
 <span data-ttu-id="14737-110">Pro sestavení této sady aplikací WPF implementuje hostitele služeb.</span><span class="sxs-lookup"><span data-stu-id="14737-110">To build this set of applications, WPF implements a host of services.</span></span> <span data-ttu-id="14737-111">V tomto tématu najdete přehled těchto služeb a kde najdete další informace.</span><span class="sxs-lookup"><span data-stu-id="14737-111">This topic provides an overview of these services and where to find more information.</span></span>  

<a name="Application_Management"></a>   
## <a name="application-management"></a><span data-ttu-id="14737-112">Správa aplikací</span><span class="sxs-lookup"><span data-stu-id="14737-112">Application Management</span></span>  
 <span data-ttu-id="14737-113">Spustitelné aplikace WPF běžně vyžadují základní sadu funkcí, které zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="14737-113">Executable WPF applications commonly require a core set of functionality that includes the following:</span></span>  
  
- <span data-ttu-id="14737-114">Vytvoření a Správa běžné aplikační infrastruktury (včetně vytvoření metody vstupního bodu a smyčky zpráv systému Windows pro příjem systémových a vstupních zpráv).</span><span class="sxs-lookup"><span data-stu-id="14737-114">Creating and managing common application infrastructure (including creating an entry point method and a Windows message loop to receive system and input messages).</span></span>  
  
- <span data-ttu-id="14737-115">Sledování a interakce s životností aplikace.</span><span class="sxs-lookup"><span data-stu-id="14737-115">Tracking and interacting with the lifetime of an application.</span></span>  
  
- <span data-ttu-id="14737-116">Načítání a zpracování parametrů příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="14737-116">Retrieving and processing command-line parameters.</span></span>  
  
- <span data-ttu-id="14737-117">Sdílení vlastností oboru aplikace a prostředků [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="14737-117">Sharing application-scope properties and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] resources.</span></span>  
  
- <span data-ttu-id="14737-118">Zjišťování a zpracování neošetřených výjimek.</span><span class="sxs-lookup"><span data-stu-id="14737-118">Detecting and processing unhandled exceptions.</span></span>  
  
- <span data-ttu-id="14737-119">Vracení ukončovacích kódů</span><span class="sxs-lookup"><span data-stu-id="14737-119">Returning exit codes.</span></span>  
  
- <span data-ttu-id="14737-120">Správa systému Windows v samostatných aplikacích.</span><span class="sxs-lookup"><span data-stu-id="14737-120">Managing windows in standalone applications.</span></span>  
  
- <span data-ttu-id="14737-121">Sledování navigace v aplikacích prohlížeče XAML (XBAP) a samostatné aplikace s navigačními okny a snímky.</span><span class="sxs-lookup"><span data-stu-id="14737-121">Tracking navigation in XAML browser applications (XBAPs), and standalone applications with navigation windows and frames.</span></span>  
  
 <span data-ttu-id="14737-122">Tyto možnosti jsou implementovány třídou <xref:System.Windows.Application>, kterou přidáte do aplikací pomocí *definice aplikace*.</span><span class="sxs-lookup"><span data-stu-id="14737-122">These capabilities are implemented by the <xref:System.Windows.Application> class, which you add to your applications using an *application definition*.</span></span>  
  
 <span data-ttu-id="14737-123">Další informace najdete v tématu [Přehled správy aplikací](application-management-overview.md).</span><span class="sxs-lookup"><span data-stu-id="14737-123">For more information, see [Application Management Overview](application-management-overview.md).</span></span>  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>   
## <a name="wpf-application-resource-content-and-data-files"></a><span data-ttu-id="14737-124">Zdroj, obsah a datové soubory zdroje aplikací WPF</span><span class="sxs-lookup"><span data-stu-id="14737-124">WPF Application Resource, Content, and Data Files</span></span>  
 <span data-ttu-id="14737-125">WPF rozšiřuje základní podporu v Microsoft .NET Framework pro vložené prostředky a podporuje tři druhy nespustitelných datových souborů: zdroj, obsah a data.</span><span class="sxs-lookup"><span data-stu-id="14737-125">WPF extends the core support in the Microsoft .NET Framework for embedded resources with support for three kinds of non-executable data files: resource, content, and data.</span></span> <span data-ttu-id="14737-126">Další informace naleznete v tématu [prostředky aplikace WPF, obsah a datové soubory](wpf-application-resource-content-and-data-files.md).</span><span class="sxs-lookup"><span data-stu-id="14737-126">For more information, see [WPF Application Resource, Content, and Data Files](wpf-application-resource-content-and-data-files.md).</span></span>  
  
 <span data-ttu-id="14737-127">Klíčovou součástí podpory pro nespustitelné datové soubory WPF je schopnost identifikovat a načíst je pomocí jedinečného identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="14737-127">A key component of the support for WPF non-executable data files is the ability to identify and load them using a unique URI.</span></span> <span data-ttu-id="14737-128">Další informace najdete v tématu [identifikátory URI Pack v](pack-uris-in-wpf.md)subsystému WPF.</span><span class="sxs-lookup"><span data-stu-id="14737-128">For more information, see [Pack URIs in WPF](pack-uris-in-wpf.md).</span></span>  
  
<a name="Windows_and_Dialog_Boxes"></a>   
## <a name="windows-and-dialog-boxes"></a><span data-ttu-id="14737-129">Okna a dialogová okna</span><span class="sxs-lookup"><span data-stu-id="14737-129">Windows and Dialog Boxes</span></span>  
 <span data-ttu-id="14737-130">Uživatelé pracují se samostatnými aplikacemi WPF prostřednictvím systému Windows.</span><span class="sxs-lookup"><span data-stu-id="14737-130">Users interact with WPF standalone applications through windows.</span></span> <span data-ttu-id="14737-131">Účelem okna je hostování obsahu aplikace a vystavení funkcí aplikace, které obvykle uživatelům umožňují pracovat s obsahem.</span><span class="sxs-lookup"><span data-stu-id="14737-131">The purpose of a window is to host application content and expose application functionality that usually allows users to interact with the content.</span></span> <span data-ttu-id="14737-132">V WPF je Windows zapouzdřený pomocí <xref:System.Windows.Window> třídy, která podporuje:</span><span class="sxs-lookup"><span data-stu-id="14737-132">In WPF, windows are encapsulated by the <xref:System.Windows.Window> class, which supports:</span></span>  
  
- <span data-ttu-id="14737-133">Vytváření a zobrazování oken.</span><span class="sxs-lookup"><span data-stu-id="14737-133">Creating and showing windows.</span></span>  
  
- <span data-ttu-id="14737-134">Vytváření vztahů mezi vlastníkem a vlastníkem okna.</span><span class="sxs-lookup"><span data-stu-id="14737-134">Establishing owner/owned window relationships.</span></span>  
  
- <span data-ttu-id="14737-135">Konfigurace vzhledu okna (například velikost, umístění, ikony, text záhlaví, ohraničení).</span><span class="sxs-lookup"><span data-stu-id="14737-135">Configuring window appearance (for example, size, location, icons, title bar text, border).</span></span>  
  
- <span data-ttu-id="14737-136">Sledování a interakce s dobou života okna.</span><span class="sxs-lookup"><span data-stu-id="14737-136">Tracking and interacting with the lifetime of a window.</span></span>  
  
 <span data-ttu-id="14737-137">Další informace najdete v tématu [Přehled Windows WPF](wpf-windows-overview.md).</span><span class="sxs-lookup"><span data-stu-id="14737-137">For more information, see [WPF Windows Overview](wpf-windows-overview.md).</span></span>  
  
 <span data-ttu-id="14737-138"><xref:System.Windows.Window> podporuje možnost vytvoření speciálního typu okna označovaného jako dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="14737-138"><xref:System.Windows.Window> supports the ability to create a special type of window known as a dialog box.</span></span> <span data-ttu-id="14737-139">Lze vytvořit modální i nemodální typy dialogových oken.</span><span class="sxs-lookup"><span data-stu-id="14737-139">Both modal and modeless types of dialog boxes can be created.</span></span>  
  
 <span data-ttu-id="14737-140">Pro usnadnění a výhody opětovné použitelnosti a konzistentní uživatelské prostředí napříč aplikacemi poskytuje WPF tři z dialogových oken běžné Windows: <xref:Microsoft.Win32.OpenFileDialog>, <xref:Microsoft.Win32.SaveFileDialog>a <xref:System.Windows.Controls.PrintDialog>.</span><span class="sxs-lookup"><span data-stu-id="14737-140">For convenience, and the benefits of reusability and a consistent user experience across applications, WPF exposes three of the common Windows dialog boxes: <xref:Microsoft.Win32.OpenFileDialog>, <xref:Microsoft.Win32.SaveFileDialog>, and <xref:System.Windows.Controls.PrintDialog>.</span></span>  
  
 <span data-ttu-id="14737-141">Okno se zprávou je speciální typ dialogového okna pro zobrazení důležitých textových informací uživatelům a pro dotazování jednoduchých dotazů Ano/Ne/OK/zrušit.</span><span class="sxs-lookup"><span data-stu-id="14737-141">A message box is a special type of dialog box for showing important textual information to users, and for asking simple Yes/No/OK/Cancel questions.</span></span> <span data-ttu-id="14737-142">Pro vytváření a zobrazování oken se zprávami se používá třída <xref:System.Windows.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="14737-142">You use the <xref:System.Windows.MessageBox> class to create and show message boxes.</span></span>  
  
 <span data-ttu-id="14737-143">Další informace najdete v tématu [Přehled dialogových oken](dialog-boxes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="14737-143">For more information, see [Dialog Boxes Overview](dialog-boxes-overview.md).</span></span>  
  
<a name="Navigation"></a>   
## <a name="navigation"></a><span data-ttu-id="14737-144">Navigace</span><span class="sxs-lookup"><span data-stu-id="14737-144">Navigation</span></span>  
 <span data-ttu-id="14737-145">WPF podporuje navigaci na webovém stylu pomocí stránek (<xref:System.Windows.Controls.Page>) a hypertextových odkazů (<xref:System.Windows.Documents.Hyperlink>).</span><span class="sxs-lookup"><span data-stu-id="14737-145">WPF supports Web-style navigation using pages (<xref:System.Windows.Controls.Page>) and hyperlinks (<xref:System.Windows.Documents.Hyperlink>).</span></span> <span data-ttu-id="14737-146">Navigace může být implementována různými způsoby, které zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="14737-146">Navigation can be implemented in a variety of ways that include the following:</span></span>  
  
- <span data-ttu-id="14737-147">Samostatné stránky, které jsou hostovány ve webovém prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="14737-147">Standalone pages that are hosted in a Web browser.</span></span>  
  
- <span data-ttu-id="14737-148">Stránky zkompilované do XBAP, která je hostována ve webovém prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="14737-148">Pages compiled into an XBAP that is hosted in a Web browser.</span></span>  
  
- <span data-ttu-id="14737-149">Stránky zkompilované do samostatné aplikace a hostované v navigačním okně (<xref:System.Windows.Navigation.NavigationWindow>).</span><span class="sxs-lookup"><span data-stu-id="14737-149">Pages compiled into a standalone application and hosted by a navigation window (<xref:System.Windows.Navigation.NavigationWindow>).</span></span>  
  
- <span data-ttu-id="14737-150">Stránky hostované snímkem (<xref:System.Windows.Controls.Frame>), které mohou být hostovány na samostatné stránce nebo na stránce zkompilované do aplikace XBAP nebo samostatné aplikace.</span><span class="sxs-lookup"><span data-stu-id="14737-150">Pages that are hosted by a frame (<xref:System.Windows.Controls.Frame>), which may be hosted in a standalone page, or a page compiled into either an XBAP or a standalone application.</span></span>  
  
 <span data-ttu-id="14737-151">Pro usnadnění navigace WPF implementuje následující:</span><span class="sxs-lookup"><span data-stu-id="14737-151">To facilitate navigation, WPF implements the following:</span></span>  
  
- <span data-ttu-id="14737-152"><xref:System.Windows.Navigation.NavigationService>sdílený navigační modul pro zpracování žádostí o navigaci, které jsou používány <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>a XBAP k podpoře navigace uvnitř aplikace.</span><span class="sxs-lookup"><span data-stu-id="14737-152"><xref:System.Windows.Navigation.NavigationService>, the shared navigation engine for processing navigation requests that is used by <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>, and XBAPs to support intra-application navigation.</span></span>  
  
- <span data-ttu-id="14737-153">Navigační metody pro zahájení navigace</span><span class="sxs-lookup"><span data-stu-id="14737-153">Navigation methods to initiate navigation.</span></span>  
  
- <span data-ttu-id="14737-154">Navigační události pro sledování a interakci s dobou života navigace</span><span class="sxs-lookup"><span data-stu-id="14737-154">Navigation events to track and interact with navigation lifetime.</span></span>  
  
- <span data-ttu-id="14737-155">Zapamatování navigace zpět a přeposlání pomocí deníku, který lze také kontrolovat a manipulovat.</span><span class="sxs-lookup"><span data-stu-id="14737-155">Remembering back and forward navigation using a journal, which can also be inspected and manipulated.</span></span>  
  
 <span data-ttu-id="14737-156">Informace najdete v tématu [Přehled navigace](navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="14737-156">For information, see [Navigation Overview](navigation-overview.md).</span></span>  
  
 <span data-ttu-id="14737-157">WPF také podporuje speciální typ navigace známý jako strukturovaná navigace.</span><span class="sxs-lookup"><span data-stu-id="14737-157">WPF also supports a special type of navigation known as structured navigation.</span></span> <span data-ttu-id="14737-158">Strukturované navigace lze použít k volání jedné nebo více stránek, které vracejí data strukturovaným a předvídatelným způsobem, který je konzistentní s voláním funkce.</span><span class="sxs-lookup"><span data-stu-id="14737-158">Structured navigation can be used to call one or more pages that return data in a structured and predictable way that is consistent with calling functions.</span></span> <span data-ttu-id="14737-159">Tato funkce závisí na třídě <xref:System.Windows.Navigation.PageFunction%601>, která je podrobněji popsána v [přehledu strukturované navigace](structured-navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="14737-159">This capability depends on the <xref:System.Windows.Navigation.PageFunction%601> class, which is described further in [Structured Navigation Overview](structured-navigation-overview.md).</span></span> <span data-ttu-id="14737-160"><xref:System.Windows.Navigation.PageFunction%601> také slouží ke zjednodušení vytváření komplexních navigačních topologií, které jsou popsány v tématu [Přehled topologií navigace](navigation-topologies-overview.md).</span><span class="sxs-lookup"><span data-stu-id="14737-160"><xref:System.Windows.Navigation.PageFunction%601> also serves to simplify the creation of complex navigation topologies, which are described in [Navigation Topologies Overview](navigation-topologies-overview.md).</span></span>  
  
<a name="Hosting"></a>   
## <a name="hosting"></a><span data-ttu-id="14737-161">Hosting</span><span class="sxs-lookup"><span data-stu-id="14737-161">Hosting</span></span>  
 <span data-ttu-id="14737-162">Aplikace XBAP je možné hostovat v aplikacích Microsoft Internet Explorer a Firefox.</span><span class="sxs-lookup"><span data-stu-id="14737-162">XBAPs can be hosted in Microsoft Internet Explorer or Firefox.</span></span> <span data-ttu-id="14737-163">Každý model hostování má vlastní sadu důležitých informací a omezení, které jsou pokryty v [hostování](hosting-wpf-applications.md).</span><span class="sxs-lookup"><span data-stu-id="14737-163">Each hosting model has its own set of considerations and constraints that are covered in [Hosting](hosting-wpf-applications.md).</span></span>  
  
<a name="Build_and_Deploy"></a>   
## <a name="build-and-deploy"></a><span data-ttu-id="14737-164">Sestavení a nasazení</span><span class="sxs-lookup"><span data-stu-id="14737-164">Build and Deploy</span></span>  
 <span data-ttu-id="14737-165">I když jednoduché aplikace WPF mohou být sestaveny z příkazového řádku pomocí kompilátorů příkazového řádku, WPF se integruje se sadou Visual Studio a poskytuje další podporu, která zjednodušuje proces vývoje a sestavování.</span><span class="sxs-lookup"><span data-stu-id="14737-165">Although simple WPF applications can be built from a command prompt using command-line compilers, WPF integrates with Visual Studio to provide additional support that simplified the development and build process.</span></span> <span data-ttu-id="14737-166">Další informace naleznete v tématu [sestavování aplikace WPF](building-a-wpf-application-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="14737-166">For more information, see [Building a WPF Application](building-a-wpf-application-wpf.md).</span></span>  
  
 <span data-ttu-id="14737-167">V závislosti na typu aplikace, kterou sestavíte, existuje jedna nebo více možností nasazení, ze kterých si můžete vybrat.</span><span class="sxs-lookup"><span data-stu-id="14737-167">Depending on the type of application you build, there are one or more deployment options to choose from.</span></span> <span data-ttu-id="14737-168">Další informace naleznete v tématu [nasazení aplikace WPF](deploying-a-wpf-application-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="14737-168">For more information, see [Deploying a WPF Application](deploying-a-wpf-application-wpf.md).</span></span>  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="14737-169">Související témata</span><span class="sxs-lookup"><span data-stu-id="14737-169">Related Topics</span></span>  
  
|<span data-ttu-id="14737-170">Název</span><span class="sxs-lookup"><span data-stu-id="14737-170">Title</span></span>|<span data-ttu-id="14737-171">Popis</span><span class="sxs-lookup"><span data-stu-id="14737-171">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="14737-172">Přehled správy aplikací</span><span class="sxs-lookup"><span data-stu-id="14737-172">Application Management Overview</span></span>](application-management-overview.md)|<span data-ttu-id="14737-173">Poskytuje přehled <xref:System.Windows.Application> třídy, včetně správy životního cyklu aplikací, Windows, prostředků aplikací a navigace.</span><span class="sxs-lookup"><span data-stu-id="14737-173">Provides an overview of the <xref:System.Windows.Application> class including managing application lifetime, windows, application resources, and navigation.</span></span>|  
|[<span data-ttu-id="14737-174">Windows ve WPF</span><span class="sxs-lookup"><span data-stu-id="14737-174">Windows in WPF</span></span>](windows-in-wpf-applications.md)|<span data-ttu-id="14737-175">Obsahuje podrobnosti o správě oken ve vaší aplikaci, včetně způsobu použití <xref:System.Windows.Window> třídy a dialogových oken.</span><span class="sxs-lookup"><span data-stu-id="14737-175">Provides details of managing windows in your application including how to use the <xref:System.Windows.Window> class and dialog boxes.</span></span>|  
|[<span data-ttu-id="14737-176">Přehled navigace</span><span class="sxs-lookup"><span data-stu-id="14737-176">Navigation Overview</span></span>](navigation-overview.md)|<span data-ttu-id="14737-177">Poskytuje přehled o správě navigace mezi stránkami aplikace.</span><span class="sxs-lookup"><span data-stu-id="14737-177">Provides an overview of managing navigation between pages of your application.</span></span>|  
|[<span data-ttu-id="14737-178">Hostování</span><span class="sxs-lookup"><span data-stu-id="14737-178">Hosting</span></span>](hosting-wpf-applications.md)|<span data-ttu-id="14737-179">Poskytuje přehled aplikací prohlížeče XAML (XBAP).</span><span class="sxs-lookup"><span data-stu-id="14737-179">Provides an overview of XAML browser applications (XBAPs).</span></span>|  
|[<span data-ttu-id="14737-180">Sestavení a nasazení</span><span class="sxs-lookup"><span data-stu-id="14737-180">Build and Deploy</span></span>](building-and-deploying-wpf-applications.md)|<span data-ttu-id="14737-181">Popisuje, jak sestavit a nasadit vaši aplikaci WPF.</span><span class="sxs-lookup"><span data-stu-id="14737-181">Describes how to build and deploy your WPF application.</span></span>|  
|[<span data-ttu-id="14737-182">Úvod k použití WPF v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="14737-182">Introduction to WPF in Visual Studio</span></span>](../getting-started/introduction-to-wpf-in-vs.md)|<span data-ttu-id="14737-183">Popisuje hlavní funkce WPF.</span><span class="sxs-lookup"><span data-stu-id="14737-183">Describes the main features of WPF.</span></span>|  
|[<span data-ttu-id="14737-184">Návod: Moje první desktopová aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="14737-184">Walkthrough: My first WPF desktop application</span></span>](../getting-started/walkthrough-my-first-wpf-desktop-application.md)|<span data-ttu-id="14737-185">Návod, který ukazuje, jak vytvořit aplikaci WPF pomocí navigace na stránce, rozložení, ovládacích prvků, obrázků, stylů a vazeb.</span><span class="sxs-lookup"><span data-stu-id="14737-185">A walkthrough that shows how to create a WPF application using page navigation, layout, controls, images, styles, and binding.</span></span>|
