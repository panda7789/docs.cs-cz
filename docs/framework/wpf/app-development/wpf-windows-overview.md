---
title: "Přehled WPF Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XAML [WPF], displaying content via
- XAML pages [WPF], displaying
- content [WPF], displaying via XAML
- window objects [WPF]
- hosting [WPF], applications
- managing windows [WPF]
- dialog boxes [WPF]
- Page object [WPF]
- NavigationWindow objects [WPF]
- applications [WPF], hosting
- content [WPF], displaying
- events [WPF]
- content [WPF], displaying via procedural code
- modal windows [WPF]
- procedural code [WPF], displaying content via
- displaying content via procedural code [WPF]
- window management [WPF]
- displaying content [WPF]
- window events [WPF]
- windows [WPF]
- modal dialog boxes [WPF]
- displaying XAML pages [WPF]
ms.assetid: 737d04ec-8861-46c3-8d44-fa11d3528d23
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 594bb21983f51f3c0698c43d0f6ea39594b72705
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="wpf-windows-overview"></a><span data-ttu-id="0aff9-102">Přehled WPF Windows</span><span class="sxs-lookup"><span data-stu-id="0aff9-102">WPF Windows Overview</span></span>
<span data-ttu-id="0aff9-103">Uživatelé komunikovat s [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] samostatné aplikace prostřednictvím služby windows.</span><span class="sxs-lookup"><span data-stu-id="0aff9-103">Users interact with [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] standalone applications through windows.</span></span> <span data-ttu-id="0aff9-104">Primárním účelem okno je jako hostitele obsahu, který vizualizuje data a umožňuje uživatelům interakci s daty.</span><span class="sxs-lookup"><span data-stu-id="0aff9-104">The primary purpose of a window is to host content that visualizes data and enables users to interact with data.</span></span> <span data-ttu-id="0aff9-105">Samostatné [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace zadat své vlastní windows pomocí <xref:System.Windows.Window> třídy.</span><span class="sxs-lookup"><span data-stu-id="0aff9-105">Standalone [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications provide their own windows by using the <xref:System.Windows.Window> class.</span></span> <span data-ttu-id="0aff9-106">Toto téma představuje <xref:System.Windows.Window> před pokrývajících základní informace o vytváření a správa systému windows v samostatné aplikace.</span><span class="sxs-lookup"><span data-stu-id="0aff9-106">This topic introduces <xref:System.Windows.Window> before covering the fundamentals of creating and managing windows in standalone applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0aff9-107">Hostované prohlížečem [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace, včetně [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] a ztratit [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] stránky, neposkytují vlastní windows.</span><span class="sxs-lookup"><span data-stu-id="0aff9-107">Browser-hosted [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications, including [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] and loose [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pages, don't provide their own windows.</span></span> <span data-ttu-id="0aff9-108">Místo toho jsou hostované v systému windows poskytuje [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0aff9-108">Instead, they are hosted in windows provided by [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)].</span></span> <span data-ttu-id="0aff9-109">V tématu [přehled aplikace prohlížeče WPF XAML](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0aff9-109">See [WPF XAML Browser Applications Overview](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md).</span></span>  
  
  
<a name="TheWindowClass"></a>   
## <a name="the-window-class"></a><span data-ttu-id="0aff9-110">Třídy oken</span><span class="sxs-lookup"><span data-stu-id="0aff9-110">The Window Class</span></span>  
 <span data-ttu-id="0aff9-111">Následující obrázek ukazuje základní části okna.</span><span class="sxs-lookup"><span data-stu-id="0aff9-111">The following figure illustrates the constituent parts of a window.</span></span>  
  
 <span data-ttu-id="0aff9-112">![Okno elementy](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure1.PNG "WindowOverviewFigure1")</span><span class="sxs-lookup"><span data-stu-id="0aff9-112">![Window elements](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure1.PNG "WindowOverviewFigure1")</span></span>  
  
 <span data-ttu-id="0aff9-113">Okno je rozdělené do dvou oblastech: neklientská oblast a klientské oblasti.</span><span class="sxs-lookup"><span data-stu-id="0aff9-113">A window is divided into two areas: the non-client area and client area.</span></span>  
  
 <span data-ttu-id="0aff9-114">*Neklientská oblast* časového období je implementováno modulem [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] a zahrnuje části okna, které jsou společné pro většinu windows, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="0aff9-114">The *non-client area* of a window is implemented by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] and includes the parts of a window that are common to most windows, including the following:</span></span>  
  
-   <span data-ttu-id="0aff9-115">Ohraničení.</span><span class="sxs-lookup"><span data-stu-id="0aff9-115">A border.</span></span>  
  
-   <span data-ttu-id="0aff9-116">Záhlaví.</span><span class="sxs-lookup"><span data-stu-id="0aff9-116">A title bar.</span></span>  
  
-   <span data-ttu-id="0aff9-117">Ikona.</span><span class="sxs-lookup"><span data-stu-id="0aff9-117">An icon.</span></span>  
  
-   <span data-ttu-id="0aff9-118">Minimalizovat, maximalizovat a obnovte tlačítka.</span><span class="sxs-lookup"><span data-stu-id="0aff9-118">Minimize, Maximize, and Restore buttons.</span></span>  
  
-   <span data-ttu-id="0aff9-119">Tlačítko Zavřít.</span><span class="sxs-lookup"><span data-stu-id="0aff9-119">A Close button.</span></span>  
  
-   <span data-ttu-id="0aff9-120">Nabídky systému s položky nabídky, které umožňují uživatelům minimalizovat, maximalizovat, obnovení, přesunout, přizpůsobit a zavřete okno.</span><span class="sxs-lookup"><span data-stu-id="0aff9-120">A System menu with menu items that allow users to minimize, maximize, restore, move, resize, and close a window.</span></span>  
  
 <span data-ttu-id="0aff9-121">*Klientské oblasti* časového období je oblast v rámci časového období neklientská oblast a používají vývojáři přidání obsahu specifické pro aplikace, jako je například nabídek, panely nástrojů a ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="0aff9-121">The *client area* of a window is the area within a window's non-client area and is used by developers to add application-specific content, such as menu bars, tool bars, and controls.</span></span>  
  
 <span data-ttu-id="0aff9-122">V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], okno se zapouzdřené pomocí <xref:System.Windows.Window> třídu, která používáte k postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="0aff9-122">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], a window is encapsulated by the <xref:System.Windows.Window> class that you use to do the following:</span></span>  
  
-   <span data-ttu-id="0aff9-123">Zobrazí okno.</span><span class="sxs-lookup"><span data-stu-id="0aff9-123">Display a window.</span></span>  
  
-   <span data-ttu-id="0aff9-124">Nakonfigurujte velikost, pozice a vzhled časového období.</span><span class="sxs-lookup"><span data-stu-id="0aff9-124">Configure the size, position, and appearance of a window.</span></span>  
  
-   <span data-ttu-id="0aff9-125">Hostování obsahu specifické pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0aff9-125">Host application-specific content.</span></span>  
  
-   <span data-ttu-id="0aff9-126">Správa životního cyklu časového období.</span><span class="sxs-lookup"><span data-stu-id="0aff9-126">Manage the lifetime of a window.</span></span>  
  
<a name="DefiningAWindow"></a>   
## <a name="implementing-a-window"></a><span data-ttu-id="0aff9-127">Implementace okno</span><span class="sxs-lookup"><span data-stu-id="0aff9-127">Implementing a Window</span></span>  
 <span data-ttu-id="0aff9-128">Vzhled a chování, se skládá z implementace typické okno kde *vzhled* definuje, jak vypadá okno uživatelům a *chování* definuje způsob, jakým okno funguje jak uživatelé pracují s ním.</span><span class="sxs-lookup"><span data-stu-id="0aff9-128">The implementation of a typical window comprises both appearance and behavior, where *appearance* defines how a window looks to users and *behavior* defines the way a window functions as users interact with it.</span></span> <span data-ttu-id="0aff9-129">V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], můžete implementovat vzhled a chování okno pomocí buď kódu nebo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek.</span><span class="sxs-lookup"><span data-stu-id="0aff9-129">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], you can implement the appearance and behavior of a window using either code or [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 <span data-ttu-id="0aff9-130">Obecně platí, ale vzhled okno je implementovaná pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek a její chování je implementovaná pomocí kódu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0aff9-130">In general, however, the appearance of a window is implemented using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and its behavior is implemented using code-behind, as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 <span data-ttu-id="0aff9-131">Chcete-li povolit [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor značek a kódu soubor používat společně, vyžadují se následující věci:</span><span class="sxs-lookup"><span data-stu-id="0aff9-131">To enable a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup file and code-behind file to work together, the following are required:</span></span>  
  
-   <span data-ttu-id="0aff9-132">V kódu `Window` musí obsahovat element `x:Class` atribut.</span><span class="sxs-lookup"><span data-stu-id="0aff9-132">In markup, the `Window` element must include the `x:Class` attribute.</span></span> <span data-ttu-id="0aff9-133">Když je aplikace vytvářena, existenci `x:Class` ve značkách souboru způsobí, že [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] k vytvoření `partial` třídu odvozenou od <xref:System.Windows.Window> a má název, který je zadán `x:Class` atribut.</span><span class="sxs-lookup"><span data-stu-id="0aff9-133">When the application is built, the existence of `x:Class` in the markup file causes [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] to create a `partial` class that derives from <xref:System.Windows.Window> and has the name that is specified by the `x:Class` attribute.</span></span> <span data-ttu-id="0aff9-134">To vyžaduje přidání [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] deklaraci oboru názvů pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schématu ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).</span><span class="sxs-lookup"><span data-stu-id="0aff9-134">This requires the addition of an [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace declaration for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schema ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).</span></span> <span data-ttu-id="0aff9-135">Generovaný objekt `partial` třída implementuje `InitializeComponent` metoda, která se nazývá registrace události a nastavte vlastnosti, které jsou implementované v kódu.</span><span class="sxs-lookup"><span data-stu-id="0aff9-135">The generated `partial` class implements the `InitializeComponent` method, which is called to register the events and set the properties that are implemented in markup.</span></span>  
  
-   <span data-ttu-id="0aff9-136">V kódu, musí být třída `partial` třídy se stejným názvem, která je zadána `x:Class` atribut ve značce a musí být odvozeny od <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="0aff9-136">In code-behind, the class must be a `partial` class with the same name that is specified by the `x:Class` attribute in markup, and it must derive from <xref:System.Windows.Window>.</span></span> <span data-ttu-id="0aff9-137">To umožňuje souboru kódu, který má být spojen s `partial` třídu, která se vygeneruje pro soubor značek, když je aplikace vytvářena (najdete v části [vytváření aplikace WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)).</span><span class="sxs-lookup"><span data-stu-id="0aff9-137">This allows the code-behind file to be associated with the `partial` class that is generated for the markup file when the application is built (see [Building a WPF Application](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)).</span></span>  
  
-   <span data-ttu-id="0aff9-138">V modelu code-behind <xref:System.Windows.Window> třída musí implementovat konstruktor, který volá `InitializeComponent` metoda.</span><span class="sxs-lookup"><span data-stu-id="0aff9-138">In code-behind, the <xref:System.Windows.Window> class must implement a constructor that calls the `InitializeComponent` method.</span></span> <span data-ttu-id="0aff9-139">`InitializeComponent`je implementována ve kód je generována souboru `partial` třída registrace události a nastavte vlastnosti, které jsou definovány v kódu.</span><span class="sxs-lookup"><span data-stu-id="0aff9-139">`InitializeComponent` is implemented by the markup file's generated `partial` class to register events and set properties that are defined in markup.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0aff9-140">Když přidáte novou <xref:System.Windows.Window> do projektu s použitím [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], <xref:System.Windows.Window> je implementovaná pomocí značek a kódu a zahrnuje konfiguraci potřebné k vytvoření přidružení mezi soubory značek a kódu jako popsané v tomto poli.</span><span class="sxs-lookup"><span data-stu-id="0aff9-140">When you add a new <xref:System.Windows.Window> to your project by using [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], the <xref:System.Windows.Window> is implemented using both markup and code-behind, and includes the necessary configuration to create the association between the markup and code-behind files as described here.</span></span>  
  
 <span data-ttu-id="0aff9-141">V této konfiguraci na místě, můžete se zaměřit na definování vzhled okna v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek a implementace své chování v kódu.</span><span class="sxs-lookup"><span data-stu-id="0aff9-141">With this configuration in place, you can focus on defining the appearance of the window in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and implementing its behavior in code-behind.</span></span> <span data-ttu-id="0aff9-142">Následující příklad ukazuje okno s tlačítkem na implementované v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek a obslužné rutiny události pro tlačítka <xref:System.Windows.Controls.Primitives.ButtonBase.Click> události, které jsou implementované v kódu.</span><span class="sxs-lookup"><span data-stu-id="0aff9-142">The following example shows a window with a button, implemented in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and an event handler for the button's <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, implemented in code-behind.</span></span>  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>   
## <a name="configuring-a-window-definition-for-msbuild"></a><span data-ttu-id="0aff9-143">Konfigurace definici okna pro nástroje MSBuild</span><span class="sxs-lookup"><span data-stu-id="0aff9-143">Configuring a Window Definition for MSBuild</span></span>  
 <span data-ttu-id="0aff9-144">Jak implementovat okně aplikace určuje, jak je nakonfigurována pro [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0aff9-144">How you implement your window determines how it is configured for [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)].</span></span> <span data-ttu-id="0aff9-145">Časový interval, který je definován pomocí obou pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek a kódu:</span><span class="sxs-lookup"><span data-stu-id="0aff9-145">For a window that is defined using both [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind:</span></span>  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <span data-ttu-id="0aff9-146">soubory značek jsou nakonfigurované jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` položky.</span><span class="sxs-lookup"><span data-stu-id="0aff9-146">markup files are configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items.</span></span>  
  
-   <span data-ttu-id="0aff9-147">Soubory kódu jsou nakonfigurované jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Compile` položky.</span><span class="sxs-lookup"><span data-stu-id="0aff9-147">Code-behind files are configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Compile` items.</span></span>  
  
 <span data-ttu-id="0aff9-148">To je znázorněno v následujícím [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="0aff9-148">This is shown in the following [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] project file.</span></span>  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 <span data-ttu-id="0aff9-149">Informace o vytváření [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace, najdete v části [vytváření aplikace WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="0aff9-149">For information about building [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications, see [Building a WPF Application](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md).</span></span>  
  
<a name="WindowLifetime"></a>   
## <a name="window-lifetime"></a><span data-ttu-id="0aff9-150">Doba života okna</span><span class="sxs-lookup"><span data-stu-id="0aff9-150">Window Lifetime</span></span>  
 <span data-ttu-id="0aff9-151">Okno s jakákoli třída má životnost, který začíná, když je vytvořena první instance, po jejímž uplynutí ho je otevřít, aktivovat a deaktivovat a nakonec zavřít.</span><span class="sxs-lookup"><span data-stu-id="0aff9-151">As with any class, a window has a lifetime that begins when it is first instantiated, after which it is opened, activated and deactivated, and eventually closed.</span></span>  
  
  
<a name="Opening_a_Window"></a>   
### <a name="opening-a-window"></a><span data-ttu-id="0aff9-152">Otevřete okno</span><span class="sxs-lookup"><span data-stu-id="0aff9-152">Opening a Window</span></span>  
 <span data-ttu-id="0aff9-153">Chcete-li otevřít okno, nejdřív vytvořit instance, který je znázorněn v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0aff9-153">To open a window, you first create an instance of it, which is demonstrated in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 <span data-ttu-id="0aff9-154">V tomto příkladu `MarkupAndCodeBehindWindow` je vytvořena instance při spuštění aplikace, která nastane při <xref:System.Windows.Application.Startup> událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="0aff9-154">In this example, the `MarkupAndCodeBehindWindow` is instantiated when the application starts, which occurs when the <xref:System.Windows.Application.Startup> event is raised.</span></span>  
  
 <span data-ttu-id="0aff9-155">Při vytváření instance časového období, odkaz na jeho se automaticky přidá do seznamu systému windows, který spravuje <xref:System.Windows.Application> objektu (viz <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="0aff9-155">When a window is instantiated, a reference to it is automatically added to a list of windows that is managed by the <xref:System.Windows.Application> object (see <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>).</span></span> <span data-ttu-id="0aff9-156">Kromě toho první okno chcete vytvořit instanci se ve výchozím nastavení <xref:System.Windows.Application> jako hlavní okno aplikace (viz <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="0aff9-156">Additionally, the first window to be instantiated is, by default, set by <xref:System.Windows.Application> as the main application window (see <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="0aff9-157">Nakonec otevření okna voláním <xref:System.Windows.Window.Show%2A> metoda; výsledek je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="0aff9-157">The window is finally opened by calling the <xref:System.Windows.Window.Show%2A> method; the result is shown in the following figure.</span></span>  
  
 <span data-ttu-id="0aff9-158">![Otevřít okno otevřené voláním metody window.show](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure8.png "WindowOverviewFigure8")</span><span class="sxs-lookup"><span data-stu-id="0aff9-158">![A Window Opened by Calling Window.Show](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure8.png "WindowOverviewFigure8")</span></span>  
  
 <span data-ttu-id="0aff9-159">Okno, ve kterém je otevřen voláním <xref:System.Windows.Window.Show%2A> je nemodálním okně, což znamená, že aplikace funguje v režimu, který umožňuje uživatelům aktivovat jiné systém windows ve stejné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0aff9-159">A window that is opened by calling <xref:System.Windows.Window.Show%2A> is a modeless window, which means that the application operates in a mode that allows users to activate other windows in the same application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0aff9-160"><xref:System.Windows.Window.ShowDialog%2A>je volána modálně otevřete windows, jako je například dialogová okna.</span><span class="sxs-lookup"><span data-stu-id="0aff9-160"><xref:System.Windows.Window.ShowDialog%2A> is called to open windows such as dialog boxes modally.</span></span> <span data-ttu-id="0aff9-161">V tématu [dialogové okno Přehled polí](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="0aff9-161">See [Dialog Boxes Overview](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md) for more information.</span></span>  
  
 <span data-ttu-id="0aff9-162">Když <xref:System.Windows.Window.Show%2A> je volána, okno provede práci inicializace dříve, než je zobrazen k vytvoření infrastruktury, který umožní přijímat vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="0aff9-162">When <xref:System.Windows.Window.Show%2A> is called, a window performs initialization work before it is shown to establish infrastructure that allows it to receive user input.</span></span> <span data-ttu-id="0aff9-163">Při inicializaci okna <xref:System.Windows.Window.SourceInitialized> událost se vyvolá, a zobrazí se okno.</span><span class="sxs-lookup"><span data-stu-id="0aff9-163">When the window is initialized, the <xref:System.Windows.Window.SourceInitialized> event is raised and the window is shown.</span></span>  
  
 <span data-ttu-id="0aff9-164">Jako zástupce <xref:System.Windows.Application.StartupUri%2A> může být nastaven na zadejte první okno, která se automaticky otevře při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="0aff9-164">As a shortcut, <xref:System.Windows.Application.StartupUri%2A> can be set to specify the first window that is opened automatically when an application starts.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 <span data-ttu-id="0aff9-165">Při spuštění aplikace, okno zadaný hodnotou <xref:System.Windows.Application.StartupUri%2A> je otevřen modelessly; interně otevření okna voláním jeho <xref:System.Windows.Window.Show%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="0aff9-165">When the application starts, the window specified by the value of <xref:System.Windows.Application.StartupUri%2A> is opened modelessly; internally, the window is opened by calling its <xref:System.Windows.Window.Show%2A> method.</span></span>  
  
<a name="Ownership"></a>   
#### <a name="window-ownership"></a><span data-ttu-id="0aff9-166">Okno vlastnictví</span><span class="sxs-lookup"><span data-stu-id="0aff9-166">Window Ownership</span></span>  
 <span data-ttu-id="0aff9-167">Okno, ve kterém je otevřen pomocí <xref:System.Windows.Window.Show%2A> metoda nemá relaci implicitní s okna, která ho vytvořila; mohou uživatelé komunikovat s buď okno nezávisle na druhém, což znamená, že buď okno můžete provádět následující:</span><span class="sxs-lookup"><span data-stu-id="0aff9-167">A window that is opened by using the <xref:System.Windows.Window.Show%2A> method does not have an implicit relationship with the window that created it; users can interact with either window independently of the other, which means that either window can do the following:</span></span>  
  
-   <span data-ttu-id="0aff9-168">Zahrnují dalších (Pokud některý ze systému windows má jeho <xref:System.Windows.Window.Topmost%2A> vlastnost nastavena na hodnotu `true`).</span><span class="sxs-lookup"><span data-stu-id="0aff9-168">Cover the other (unless one of the windows has its <xref:System.Windows.Window.Topmost%2A> property set to `true`).</span></span>  
  
-   <span data-ttu-id="0aff9-169">Minimalizovat, maximalizovaném okně a obnovený bez ovlivnění dalších.</span><span class="sxs-lookup"><span data-stu-id="0aff9-169">Be minimized, maximized, and restored without affecting the other.</span></span>  
  
 <span data-ttu-id="0aff9-170">Některé windows vyžadují vztah s okně, které je otevře.</span><span class="sxs-lookup"><span data-stu-id="0aff9-170">Some windows require a relationship with the window that opens them.</span></span> <span data-ttu-id="0aff9-171">Například [!INCLUDE[TLA#tla_ide](../../../../includes/tlasharptla-ide-md.md)] aplikace může zobrazit vlastnost windows a nástroj windows, jejichž typické chování je tak, aby pokrývalo okna, která je vytvořila.</span><span class="sxs-lookup"><span data-stu-id="0aff9-171">For example, an [!INCLUDE[TLA#tla_ide](../../../../includes/tlasharptla-ide-md.md)] application may open property windows and tool windows whose typical behavior is to cover the window that creates them.</span></span> <span data-ttu-id="0aff9-172">Kromě toho takové windows by měla vždycky zavřete, minimalizovat, maximalizovat a obnovení v souladu s okno, které byly vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="0aff9-172">Furthermore, such windows should always close, minimize, maximize, and restore in concert with the window that created them.</span></span> <span data-ttu-id="0aff9-173">Takové relace by bylo možné navázat tím, že jeden interval *vlastní* jiný a je dosaženo nastavením <xref:System.Windows.Window.Owner%2A> vlastnost *ve vlastnictví okno* s odkazem na *vlastníka okno*.</span><span class="sxs-lookup"><span data-stu-id="0aff9-173">Such a relationship can be established by making one window *own* another, and is achieved by setting the <xref:System.Windows.Window.Owner%2A> property of the *owned window* with a reference to the *owner window*.</span></span> <span data-ttu-id="0aff9-174">To je ukázáno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0aff9-174">This is shown in the following example.</span></span>  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 <span data-ttu-id="0aff9-175">Po navázání vlastnictví:</span><span class="sxs-lookup"><span data-stu-id="0aff9-175">After ownership is established:</span></span>  
  
-   <span data-ttu-id="0aff9-176">Okno Vlastní odkazovat jeho vlastníka okno zkontrolováním hodnotu jeho <xref:System.Windows.Window.Owner%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0aff9-176">The owned window can reference its owner window by inspecting the value of its <xref:System.Windows.Window.Owner%2A> property.</span></span>  
  
-   <span data-ttu-id="0aff9-177">Okno vlastníka můžete zjistit všechny systémy windows vlastní zkontrolováním hodnotu jeho <xref:System.Windows.Window.OwnedWindows%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0aff9-177">The owner window can discover all the windows it owns by inspecting the value of its <xref:System.Windows.Window.OwnedWindows%2A> property.</span></span>  
  
<a name="Preventing"></a>   
#### <a name="preventing-window-activation"></a><span data-ttu-id="0aff9-178">Brání aktivaci okna</span><span class="sxs-lookup"><span data-stu-id="0aff9-178">Preventing Window Activation</span></span>  
 <span data-ttu-id="0aff9-179">Existují scénáře, kde by neměl být windows aktivovat, pokud ukazuje, jako je například konverzace windows messenger-style aplikace Internet nebo windows oznámení e-mailové aplikace.</span><span class="sxs-lookup"><span data-stu-id="0aff9-179">There are scenarios where windows should not be activated when shown, such as conversation windows of an Internet messenger-style application or notification windows of an email application.</span></span>  
  
 <span data-ttu-id="0aff9-180">Pokud aplikace obsahuje okno, které by neměly být aktivní, pokud vidět, můžete nastavit jeho <xref:System.Windows.Window.ShowActivated%2A> vlastnost `false` před voláním <xref:System.Windows.Window.Show%2A> metoda poprvé.</span><span class="sxs-lookup"><span data-stu-id="0aff9-180">If your application has a window that shouldn't be activated when shown, you can set its <xref:System.Windows.Window.ShowActivated%2A> property to `false` before calling the <xref:System.Windows.Window.Show%2A> method for the first time.</span></span> <span data-ttu-id="0aff9-181">V důsledku:</span><span class="sxs-lookup"><span data-stu-id="0aff9-181">As a consequence:</span></span>  
  
-   <span data-ttu-id="0aff9-182">Okno není aktivována.</span><span class="sxs-lookup"><span data-stu-id="0aff9-182">The window is not activated.</span></span>  
  
-   <span data-ttu-id="0aff9-183">Okně <xref:System.Windows.Window.Activated> událost není aktivována.</span><span class="sxs-lookup"><span data-stu-id="0aff9-183">The window's <xref:System.Windows.Window.Activated> event is not raised.</span></span>  
  
-   <span data-ttu-id="0aff9-184">Okno aktuálně aktivovaný zůstane aktivovaný.</span><span class="sxs-lookup"><span data-stu-id="0aff9-184">The currently activated window remains activated.</span></span>  
  
 <span data-ttu-id="0aff9-185">Okno se aktivuje, ale jakmile uživatel aktivuje kliknutím na klienta nebo neklientská oblast.</span><span class="sxs-lookup"><span data-stu-id="0aff9-185">The window will become activated, however, as soon as the user activates it by clicking either the client or non-client area.</span></span> <span data-ttu-id="0aff9-186">V tomto případě:</span><span class="sxs-lookup"><span data-stu-id="0aff9-186">In this case:</span></span>  
  
-   <span data-ttu-id="0aff9-187">Okno se aktivuje.</span><span class="sxs-lookup"><span data-stu-id="0aff9-187">The window is activated.</span></span>  
  
-   <span data-ttu-id="0aff9-188">Okně <xref:System.Windows.Window.Activated> událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="0aff9-188">The window's <xref:System.Windows.Window.Activated> event is raised.</span></span>  
  
-   <span data-ttu-id="0aff9-189">Okno dříve aktivovaná je deaktivována.</span><span class="sxs-lookup"><span data-stu-id="0aff9-189">The previously activated window is deactivated.</span></span>  
  
-   <span data-ttu-id="0aff9-190">Okně <xref:System.Windows.Window.Deactivated> a <xref:System.Windows.Window.Activated> události jsou vyvolány následně podle očekávání v odpovědi na akce uživatele.</span><span class="sxs-lookup"><span data-stu-id="0aff9-190">The window's <xref:System.Windows.Window.Deactivated> and <xref:System.Windows.Window.Activated> events are subsequently raised as expected in response to user actions.</span></span>  
  
<a name="Window_Activation"></a>   
### <a name="window-activation"></a><span data-ttu-id="0aff9-191">Okno Aktivace</span><span class="sxs-lookup"><span data-stu-id="0aff9-191">Window Activation</span></span>  
 <span data-ttu-id="0aff9-192">Při prvním otevření okna bude aktivní okno (Pokud se zobrazí s <xref:System.Windows.Window.ShowActivated%2A> nastavena na `false`).</span><span class="sxs-lookup"><span data-stu-id="0aff9-192">When a window is first opened, it becomes the active window (unless it is shown with <xref:System.Windows.Window.ShowActivated%2A> set to `false`).</span></span> <span data-ttu-id="0aff9-193">*Aktivní okno* je okno, které je aktuálně zachytávání vstupu uživatele, jako je například stisknutí kláves a kliknutí myší.</span><span class="sxs-lookup"><span data-stu-id="0aff9-193">The *active window* is the window that is currently capturing user input, such as key strokes and mouse clicks.</span></span> <span data-ttu-id="0aff9-194">Okno stane aktivní, vyvolá <xref:System.Windows.Window.Activated> událostí.</span><span class="sxs-lookup"><span data-stu-id="0aff9-194">When a window becomes active, it raises the <xref:System.Windows.Window.Activated> event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0aff9-195">Při prvním otevření okna <xref:System.Windows.FrameworkElement.Loaded> a <xref:System.Windows.Window.ContentRendered> události jsou vyvolány až poté, co <xref:System.Windows.Window.Activated> událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="0aff9-195">When a window is first opened, the <xref:System.Windows.FrameworkElement.Loaded> and <xref:System.Windows.Window.ContentRendered> events are raised only after the <xref:System.Windows.Window.Activated> event is raised.</span></span> <span data-ttu-id="0aff9-196">Myslete na to, okno lze účinně považovat za otevřít, když <xref:System.Windows.Window.ContentRendered> je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="0aff9-196">With this in mind, a window can effectively be considered opened when <xref:System.Windows.Window.ContentRendered> is raised.</span></span>  
  
 <span data-ttu-id="0aff9-197">Po okno stane aktivní, uživatel může aktivovat další okno ve stejné aplikaci, nebo jiná aplikace.</span><span class="sxs-lookup"><span data-stu-id="0aff9-197">After a window becomes active, a user can activate another window in the same application, or activate another application.</span></span> <span data-ttu-id="0aff9-198">Pokud k tomu dojde, aktuálně aktivní okno bude deaktivováno a vyvolá <xref:System.Windows.Window.Deactivated> událostí.</span><span class="sxs-lookup"><span data-stu-id="0aff9-198">When that happens, the currently active window becomes deactivated and raises the <xref:System.Windows.Window.Deactivated> event.</span></span> <span data-ttu-id="0aff9-199">Podobně platí, když uživatel vybere okno aktuálně deaktivované, okno zase aktivní a <xref:System.Windows.Window.Activated> je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="0aff9-199">Likewise, when the user selects a currently deactivated window, the window becomes active again and <xref:System.Windows.Window.Activated> is raised.</span></span>  
  
 <span data-ttu-id="0aff9-200">Jeden běžným důvodem pro zpracování <xref:System.Windows.Window.Activated> a <xref:System.Windows.Window.Deactivated> se povolení a zakázání funkce, které lze spustit pouze když je aktivní okno.</span><span class="sxs-lookup"><span data-stu-id="0aff9-200">One common reason to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> is to enable and disable functionality that can only run when a window is active.</span></span> <span data-ttu-id="0aff9-201">Například některé windows zobrazit interaktivní obsah, který vyžaduje konstantní uživatelský vstup nebo pozornost, včetně hry a přehrávačů videa.</span><span class="sxs-lookup"><span data-stu-id="0aff9-201">For example, some windows display interactive content that requires constant user input or attention, including games and video players.</span></span> <span data-ttu-id="0aff9-202">Následující příklad je zjednodušený přehrávání videa, které ukazuje, jak bude zpracováván <xref:System.Windows.Window.Activated> a <xref:System.Windows.Window.Deactivated> implementovat toto chování.</span><span class="sxs-lookup"><span data-stu-id="0aff9-202">The following example is a simplified video player that demonstrates how to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> to implement this behavior.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 <span data-ttu-id="0aff9-203">Jiné typy aplikací mohou stále spustit kód na pozadí při deaktivaci časového období.</span><span class="sxs-lookup"><span data-stu-id="0aff9-203">Other types of applications may still run code in the background when a window is deactivated.</span></span> <span data-ttu-id="0aff9-204">E-mailového klienta může například pokračovat v dotazování poštovní server, když uživatel používá jiné aplikace.</span><span class="sxs-lookup"><span data-stu-id="0aff9-204">For example, a mail client may continue polling the mail server while the user is using other applications.</span></span> <span data-ttu-id="0aff9-205">Aplikace, jako je to často poskytují různé nebo další chování, zatímco je deaktivována hlavní okno.</span><span class="sxs-lookup"><span data-stu-id="0aff9-205">Applications like these often provide different or additional behavior while the main window is deactivated.</span></span> <span data-ttu-id="0aff9-206">S ohledem na e-mailu program to znamená přidání nové položky e-mailu do složky Doručená pošta i přidání ikony v oznamovací do na hlavním panelu.</span><span class="sxs-lookup"><span data-stu-id="0aff9-206">With respect to the mail program, this may mean both adding the new mail item to the inbox and adding a notification icon to the system tray.</span></span> <span data-ttu-id="0aff9-207">Ikony v oznamovací potřebovat zobrazí jenom v případě okna e-mailu není aktivní, což může být určen na základě <xref:System.Windows.Window.IsActive%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0aff9-207">A notification icon need only be displayed when the mail window isn't active, which can be determined by inspecting the <xref:System.Windows.Window.IsActive%2A> property.</span></span>  
  
 <span data-ttu-id="0aff9-208">Dokončení úlohy na pozadí, okno chtít upozornit uživatele, více naléhavě voláním <xref:System.Windows.Window.Activate%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="0aff9-208">If a background task completes, a window may want to notify the user more urgently by calling <xref:System.Windows.Window.Activate%2A> method.</span></span> <span data-ttu-id="0aff9-209">Pokud uživatel komunikuje s aktivaci jiné aplikace při <xref:System.Windows.Window.Activate%2A> nazývá bliká tlačítko okno na hlavním panelu.</span><span class="sxs-lookup"><span data-stu-id="0aff9-209">If the user is interacting with another application activated when <xref:System.Windows.Window.Activate%2A> is called, the window's taskbar button flashes.</span></span> <span data-ttu-id="0aff9-210">Pokud uživatel komunikuje s aktuální aplikace, volání <xref:System.Windows.Window.Activate%2A> se otevře okno na popředí.</span><span class="sxs-lookup"><span data-stu-id="0aff9-210">If a user is interacting with the current application, calling <xref:System.Windows.Window.Activate%2A> will bring the window to the foreground.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0aff9-211">Dokáže zpracovat aktivace oboru aplikace pomocí <xref:System.Windows.Application.Activated?displayProperty=nameWithType> a <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> události.</span><span class="sxs-lookup"><span data-stu-id="0aff9-211">You can handle application-scope activation using the <xref:System.Windows.Application.Activated?displayProperty=nameWithType> and <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> events.</span></span>  
  
<a name="Closing_a_Window"></a>   
### <a name="closing-a-window"></a><span data-ttu-id="0aff9-212">Zavřením okna</span><span class="sxs-lookup"><span data-stu-id="0aff9-212">Closing a Window</span></span>  
 <span data-ttu-id="0aff9-213">Dobu životnosti okno spustí, přejdete-li na element end při zavření ho.</span><span class="sxs-lookup"><span data-stu-id="0aff9-213">The life of a window starts coming to an end when a user closes it.</span></span> <span data-ttu-id="0aff9-214">Okno můžete ukončit pomocí prvků v neklientská oblast, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="0aff9-214">A window can be closed by using elements in the non-client area, including the following:</span></span>  
  
-   <span data-ttu-id="0aff9-215">**Zavřít** položku **systému** nabídky.</span><span class="sxs-lookup"><span data-stu-id="0aff9-215">The **Close** item of the **System** menu.</span></span>  
  
-   <span data-ttu-id="0aff9-216">Stisknutím ALT + F4.</span><span class="sxs-lookup"><span data-stu-id="0aff9-216">Pressing ALT+F4.</span></span>  
  
-   <span data-ttu-id="0aff9-217">Kliknutím **Zavřít** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="0aff9-217">Pressing the **Close** button.</span></span>  
  
 <span data-ttu-id="0aff9-218">Můžete zadat další mechanismy pro klientské oblasti zavřete okno, další běžné, které zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="0aff9-218">You can provide additional mechanisms to the client area to close a window, the more common of which include the following:</span></span>  
  
-   <span data-ttu-id="0aff9-219">**Ukončení** položky v **souboru** nabídky, obvykle hlavní aplikaci pro windows.</span><span class="sxs-lookup"><span data-stu-id="0aff9-219">An **Exit** item in the **File** menu, typically for main application windows.</span></span>  
  
-   <span data-ttu-id="0aff9-220">A **Zavřít** položky v **souboru** nabídky, obvykle na okno sekundární aplikace.</span><span class="sxs-lookup"><span data-stu-id="0aff9-220">A **Close** item in the **File** menu, typically on a secondary application window.</span></span>  
  
-   <span data-ttu-id="0aff9-221">A **zrušit** tlačítko, obvykle na modální dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="0aff9-221">A **Cancel** button, typically on a modal dialog box.</span></span>  
  
-   <span data-ttu-id="0aff9-222">A **Zavřít** tlačítko, obvykle v nemodálním dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="0aff9-222">A **Close** button, typically on a modeless dialog box.</span></span>  
  
 <span data-ttu-id="0aff9-223">Zavřete okno v reakci na jednu z těchto mechanismů vlastní, je třeba volat <xref:System.Windows.Window.Close%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="0aff9-223">To close a window in response to one of these custom mechanisms, you need to call the <xref:System.Windows.Window.Close%2A> method.</span></span> <span data-ttu-id="0aff9-224">Následující příklad implementuje zavřete okno a vybrat možnost **ukončení** na **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="0aff9-224">The following example implements the ability to close a window by choosing the **Exit** on the **File** menu.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 <span data-ttu-id="0aff9-225">Zavře okno, vyvolá dvě události: <xref:System.Windows.Window.Closing> a <xref:System.Windows.Window.Closed>.</span><span class="sxs-lookup"><span data-stu-id="0aff9-225">When a window closes, it raises two events: <xref:System.Windows.Window.Closing> and <xref:System.Windows.Window.Closed>.</span></span>  
  
 <span data-ttu-id="0aff9-226"><xref:System.Windows.Window.Closing>je vyvolána před okno se zavře a poskytuje mechanismus, pomocí které okna je možné zabránit uzavření.</span><span class="sxs-lookup"><span data-stu-id="0aff9-226"><xref:System.Windows.Window.Closing> is raised before the window closes, and it provides a mechanism by which window closure can be prevented.</span></span> <span data-ttu-id="0aff9-227">Jeden běžným důvodem, aby se zabránilo okno uzavření je, pokud obsah okno obsahuje upravených dat.</span><span class="sxs-lookup"><span data-stu-id="0aff9-227">One common reason to prevent window closure is if window content contains modified data.</span></span> <span data-ttu-id="0aff9-228">V takovém případě <xref:System.Windows.Window.Closing> události může být zpracována pro určení, zda je nekonzistentní data a pokud ano, chcete-li požádat uživatele, jestli se mají buď pokračovat zavřít okno bez uložení dat nebo zrušit okno uzavření.</span><span class="sxs-lookup"><span data-stu-id="0aff9-228">In this situation, the <xref:System.Windows.Window.Closing> event can be handled to determine whether data is dirty and, if so, to ask the user whether to either continue closing the window without saving the data or to cancel window closure.</span></span> <span data-ttu-id="0aff9-229">Následující příklad ukazuje klíčových aspektů zpracování <xref:System.Windows.Window.Closing>.</span><span class="sxs-lookup"><span data-stu-id="0aff9-229">The following example shows the key aspects of handling <xref:System.Windows.Window.Closing>.</span></span>  
  
 [!code-csharp[WindowClosingSnippets](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  
 
  
 <span data-ttu-id="0aff9-230"><xref:System.Windows.Window.Closing> Obslužné rutiny události je předána <xref:System.ComponentModel.CancelEventArgs>, který implementuje `Boolean` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> vlastnost, která můžete nastavit na hodnotu `true` zabránit zavření okna.</span><span class="sxs-lookup"><span data-stu-id="0aff9-230">The <xref:System.Windows.Window.Closing> event handler is passed a <xref:System.ComponentModel.CancelEventArgs>, which implements the `Boolean`<xref:System.ComponentModel.CancelEventArgs.Cancel%2A> property that you set to `true` to prevent a window from closing.</span></span>  
  
 <span data-ttu-id="0aff9-231">Pokud <xref:System.Windows.Window.Closing> nejsou zpracovávány, nebo je zpracovává, ale nebyl zrušen, okno se zavře.</span><span class="sxs-lookup"><span data-stu-id="0aff9-231">If <xref:System.Windows.Window.Closing> is not handled, or it is handled but not canceled, the window will close.</span></span> <span data-ttu-id="0aff9-232">Těsně před okno ve skutečnosti zavře, <xref:System.Windows.Window.Closed> je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="0aff9-232">Just before a window actually closes, <xref:System.Windows.Window.Closed> is raised.</span></span> <span data-ttu-id="0aff9-233">V tomto okamžiku nelze okno zabránila uzavírací.</span><span class="sxs-lookup"><span data-stu-id="0aff9-233">At this point, a window cannot be prevented from closing.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0aff9-234">Aplikace může být nakonfigurována pro vypnutí automaticky, při zavření okna hlavní aplikace (viz <xref:System.Windows.Application.MainWindow%2A>) nebo poslední okno se zavře.</span><span class="sxs-lookup"><span data-stu-id="0aff9-234">An application can be configured to shut down automatically when either the main application window closes (see <xref:System.Windows.Application.MainWindow%2A>) or the last window closes.</span></span> <span data-ttu-id="0aff9-235">Podrobnosti najdete v tématu <xref:System.Windows.Application.ShutdownMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="0aff9-235">For details, see <xref:System.Windows.Application.ShutdownMode%2A>.</span></span>  
  
 <span data-ttu-id="0aff9-236">Během časového období je možné explicitně uzavřít prostřednictvím mechanismy, které poskytuje v oblastech jiného počítače než klientského a klienta, okno lze také implicitně uzavřít v důsledku chování v dalších částí aplikace nebo [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="0aff9-236">While a window can be explicitly closed through mechanisms provided in the non-client and client areas, a window can also be implicitly closed as a result of behavior in other parts of the application or [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], including the following:</span></span>  
  
-   <span data-ttu-id="0aff9-237">Uživatel odhlásí nebo ukončí [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0aff9-237">A user logs off or shuts down [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)].</span></span>  
  
-   <span data-ttu-id="0aff9-238">Zavře vlastníka časového období (viz <xref:System.Windows.Window.Owner%2A>).</span><span class="sxs-lookup"><span data-stu-id="0aff9-238">A window's owner closes (see <xref:System.Windows.Window.Owner%2A>).</span></span>  
  
-   <span data-ttu-id="0aff9-239">Zavření okna hlavní aplikaci a <xref:System.Windows.Application.ShutdownMode%2A> je <xref:System.Windows.ShutdownMode.OnMainWindowClose>.</span><span class="sxs-lookup"><span data-stu-id="0aff9-239">The main application window is closed and <xref:System.Windows.Application.ShutdownMode%2A> is <xref:System.Windows.ShutdownMode.OnMainWindowClose>.</span></span>  
  
-   <span data-ttu-id="0aff9-240"><xref:System.Windows.Application.Shutdown%2A>je volána.</span><span class="sxs-lookup"><span data-stu-id="0aff9-240"><xref:System.Windows.Application.Shutdown%2A> is called.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0aff9-241">Nelze znovu otevřít okno, jakmile je uzavřený.</span><span class="sxs-lookup"><span data-stu-id="0aff9-241">A window cannot be reopened after it is closed.</span></span>  
  
<a name="Window_Lifetime_Events"></a>   
### <a name="window-lifetime-events"></a><span data-ttu-id="0aff9-242">Interval životního cyklu události</span><span class="sxs-lookup"><span data-stu-id="0aff9-242">Window Lifetime Events</span></span>  
 <span data-ttu-id="0aff9-243">Následující obrázek zobrazuje posloupnost hlavní událostí v průběhu životnosti časového období.</span><span class="sxs-lookup"><span data-stu-id="0aff9-243">The following illustration shows the sequence of the principal events in the lifetime of a window.</span></span>  
  
 <span data-ttu-id="0aff9-244">![Doba života okna](../../../../docs/framework/wpf/app-development/media/windowlifetimeevents.png "WindowLifetimeEvents")</span><span class="sxs-lookup"><span data-stu-id="0aff9-244">![Window Lifetime](../../../../docs/framework/wpf/app-development/media/windowlifetimeevents.png "WindowLifetimeEvents")</span></span>  
  
 <span data-ttu-id="0aff9-245">Následující obrázek zobrazuje posloupnost hlavní událostí ve životnost okno, které se zobrazí bez aktivace (<xref:System.Windows.Window.ShowActivated%2A> je nastaven na `false` předtím, než se zobrazí okno).</span><span class="sxs-lookup"><span data-stu-id="0aff9-245">The following illustration shows the sequence of the principal events in the lifetime of a window that is shown without activation (<xref:System.Windows.Window.ShowActivated%2A> is set to `false` before the window is shown).</span></span>  
  
 <span data-ttu-id="0aff9-246">![Doba života okna &#40; Window.ShowActivated & č. 61; False &#41; ] (../../../../docs/framework/wpf/app-development/media/windowlifetimenoact.png "WindowLifetimeNoAct")</span><span class="sxs-lookup"><span data-stu-id="0aff9-246">![Window Lifetime &#40;Window.ShowActivated &#61; False&#41;](../../../../docs/framework/wpf/app-development/media/windowlifetimenoact.png "WindowLifetimeNoAct")</span></span>  
  
<a name="WindowLocation"></a>   
## <a name="window-location"></a><span data-ttu-id="0aff9-247">Umístění okna</span><span class="sxs-lookup"><span data-stu-id="0aff9-247">Window Location</span></span>  
 <span data-ttu-id="0aff9-248">Při otevřené okno obsahuje umístění, do x a y dimenze relativně k ploše.</span><span class="sxs-lookup"><span data-stu-id="0aff9-248">While a window is open, it has a location in the x and y dimensions relative to the desktop.</span></span> <span data-ttu-id="0aff9-249">Toto umístění může být určen na základě <xref:System.Windows.Window.Left%2A> a <xref:System.Windows.Window.Top%2A> vlastnosti, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="0aff9-249">This location can be determined by inspecting the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties, respectively.</span></span> <span data-ttu-id="0aff9-250">Můžete nastavit tyto vlastnosti chcete změnit umístění okna.</span><span class="sxs-lookup"><span data-stu-id="0aff9-250">You can set these properties to change the location of the window.</span></span>  
  
 <span data-ttu-id="0aff9-251">Můžete také zadat počáteční umístění <xref:System.Windows.Window> při prvním zobrazení nastavením <xref:System.Windows.Window.WindowStartupLocation%2A> vlastnost s jedním z následujících <xref:System.Windows.WindowStartupLocation> hodnot výčtu:</span><span class="sxs-lookup"><span data-stu-id="0aff9-251">You can also specify the initial location of a <xref:System.Windows.Window> when it first appears by setting the <xref:System.Windows.Window.WindowStartupLocation%2A> property with one of the following <xref:System.Windows.WindowStartupLocation> enumeration values:</span></span>  
  
-   <span data-ttu-id="0aff9-252"><xref:System.Windows.WindowStartupLocation.CenterOwner>(výchozí)</span><span class="sxs-lookup"><span data-stu-id="0aff9-252"><xref:System.Windows.WindowStartupLocation.CenterOwner> (default)</span></span>  
  
-   <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
-   <xref:System.Windows.WindowStartupLocation.Manual>  
  
 <span data-ttu-id="0aff9-253">Pokud při spuštění je zadán jako <xref:System.Windows.WindowStartupLocation.Manual>a <xref:System.Windows.Window.Left%2A> a <xref:System.Windows.Window.Top%2A> nebyly nastaveny vlastnosti, <xref:System.Windows.Window> požádá [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] pro umístění, do kterého se zobrazí v.</span><span class="sxs-lookup"><span data-stu-id="0aff9-253">If the startup location is specified as <xref:System.Windows.WindowStartupLocation.Manual>, and the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties have not been set, <xref:System.Windows.Window> will ask [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] for a location to appear in.</span></span>  
  
<a name="Topmost_Windows_and_Z_Order"></a>   
### <a name="topmost-windows-and-z-order"></a><span data-ttu-id="0aff9-254">Nejhornější Windows a pořadí Z-Order</span><span class="sxs-lookup"><span data-stu-id="0aff9-254">Topmost Windows and Z-Order</span></span>  
 <span data-ttu-id="0aff9-255">Kromě toho také s x a y umístění, okno má umístění v z dimenzi, která určuje svislé polohy s ohledem na ostatní windows.</span><span class="sxs-lookup"><span data-stu-id="0aff9-255">Besides having an x and y location, a window also has a location in the z dimension, which determines its vertical position with respect to other windows.</span></span> <span data-ttu-id="0aff9-256">To se označuje jako okna pořadí z-order a existují dva typy: Normální pořadí vykreslování a nejhornější pořadí vykreslování.</span><span class="sxs-lookup"><span data-stu-id="0aff9-256">This is known as the window's z-order, and there are two types: normal z-order and topmost z-order.</span></span> <span data-ttu-id="0aff9-257">Umístění okna v *normální pořadí vykreslování* je dáno bez ohledu na jeho, jestli je aktuálně aktivní.</span><span class="sxs-lookup"><span data-stu-id="0aff9-257">The location of a window in the *normal z-order* is determined by whether it is currently active or not.</span></span> <span data-ttu-id="0aff9-258">Ve výchozím nastavení okno se nachází v normálním pořadí z-order.</span><span class="sxs-lookup"><span data-stu-id="0aff9-258">By default, a window is located in the normal z-order.</span></span> <span data-ttu-id="0aff9-259">Umístění okna v *nejhornější pořadí vykreslování* je také určeno bez ohledu na jeho, jestli je aktuálně aktivní.</span><span class="sxs-lookup"><span data-stu-id="0aff9-259">The location of a window in the *topmost z-order* is also determined by whether it is currently active or not.</span></span> <span data-ttu-id="0aff9-260">Kromě toho windows v nejhornější pořadí z-order nacházejí vždy výše windows v normálním pořadí z-order.</span><span class="sxs-lookup"><span data-stu-id="0aff9-260">Furthermore, windows in the topmost z-order are always located above windows in the normal z-order.</span></span> <span data-ttu-id="0aff9-261">Okno se nachází v nejhornější pořadí z-order nastavením jeho <xref:System.Windows.Window.Topmost%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="0aff9-261">A window is located in the topmost z-order by setting its <xref:System.Windows.Window.Topmost%2A> property to `true`.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup2)]  
  
 <span data-ttu-id="0aff9-262">V rámci každé pořadí vykreslování aktuálně aktivní okno se zobrazí nad všemi jiných windows ve stejném pořadí.</span><span class="sxs-lookup"><span data-stu-id="0aff9-262">Within each z-order, the currently active window appears above all other windows in the same z-order.</span></span>  
  
<a name="WindowSize"></a>   
## <a name="window-size"></a><span data-ttu-id="0aff9-263">Velikost okna</span><span class="sxs-lookup"><span data-stu-id="0aff9-263">Window Size</span></span>  
 <span data-ttu-id="0aff9-264">Kromě nutnosti plochy umístění, okno má velikost, které je určeno několik vlastností, včetně různé vlastnosti šířky a výšky a <xref:System.Windows.Window.SizeToContent%2A>.</span><span class="sxs-lookup"><span data-stu-id="0aff9-264">Besides having a desktop location, a window has a size that is determined by several properties, including the various width and height properties and <xref:System.Windows.Window.SizeToContent%2A>.</span></span>  
  
 <span data-ttu-id="0aff9-265"><xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, a <xref:System.Windows.FrameworkElement.MaxWidth%2A> se používají ke správě celou škálu šířek, které může mít během celé jeho životnosti okno a jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0aff9-265"><xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.MaxWidth%2A> are used to manage the range of widths that a window can have during its lifetime, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup2)]  
  
 <span data-ttu-id="0aff9-266">Spravuje výšku okna <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, a <xref:System.Windows.FrameworkElement.MaxHeight%2A>a jsou nakonfigurovány, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0aff9-266">Window height is managed by <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, and <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup2)]  
  
 <span data-ttu-id="0aff9-267">Protože různých hodnot šířka a výška hodnoty zadejte rozsah, je možné pro šířku a výšku s možností změny velikosti okna musí být kdekoli v zadaný rozsah pro příslušné dimenze.</span><span class="sxs-lookup"><span data-stu-id="0aff9-267">Because the various width values and height values each specify a range, it is possible for the width and height of a resizable window to be anywhere within the specified range for the respective dimension.</span></span> <span data-ttu-id="0aff9-268">Ke zjištění jeho aktuální šířka a výška, zkontrolujte <xref:System.Windows.FrameworkElement.ActualWidth%2A> a <xref:System.Windows.FrameworkElement.ActualHeight%2A>, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="0aff9-268">To detect its current width and height, inspect <xref:System.Windows.FrameworkElement.ActualWidth%2A> and <xref:System.Windows.FrameworkElement.ActualHeight%2A>, respectively.</span></span>  
  
 <span data-ttu-id="0aff9-269">Pokud chcete šířku a výšku okna tak, aby měl velikost, která odpovídá velikosti okna je obsahu, můžete použít <xref:System.Windows.Window.SizeToContent%2A> vlastnosti, která má následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="0aff9-269">If you'd like the width and height of your window to have a size that fits to the size of the window's content, you can use the <xref:System.Windows.Window.SizeToContent%2A> property, which has the following values:</span></span>  
  
-   <span data-ttu-id="0aff9-270"><xref:System.Windows.SizeToContent.Manual>.</span><span class="sxs-lookup"><span data-stu-id="0aff9-270"><xref:System.Windows.SizeToContent.Manual>.</span></span> <span data-ttu-id="0aff9-271">Žádný vliv (výchozí).</span><span class="sxs-lookup"><span data-stu-id="0aff9-271">No effect (default).</span></span>  
  
-   <span data-ttu-id="0aff9-272"><xref:System.Windows.SizeToContent.Width>.</span><span class="sxs-lookup"><span data-stu-id="0aff9-272"><xref:System.Windows.SizeToContent.Width>.</span></span> <span data-ttu-id="0aff9-273">Na celou šířku obsahu, který má stejný účinek jako nastavení obě <xref:System.Windows.FrameworkElement.MinWidth%2A> a <xref:System.Windows.FrameworkElement.MaxWidth%2A> na šířku obsahu.</span><span class="sxs-lookup"><span data-stu-id="0aff9-273">Fit to content width, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
-   <span data-ttu-id="0aff9-274"><xref:System.Windows.SizeToContent.Height>.</span><span class="sxs-lookup"><span data-stu-id="0aff9-274"><xref:System.Windows.SizeToContent.Height>.</span></span> <span data-ttu-id="0aff9-275">Přizpůsobit na výšku obsahu, který má stejný účinek jako nastavení obě <xref:System.Windows.FrameworkElement.MinHeight%2A> a <xref:System.Windows.FrameworkElement.MaxHeight%2A> na výšku obsahu.</span><span class="sxs-lookup"><span data-stu-id="0aff9-275">Fit to content height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content.</span></span>  
  
-   <span data-ttu-id="0aff9-276"><xref:System.Windows.SizeToContent.WidthAndHeight>.</span><span class="sxs-lookup"><span data-stu-id="0aff9-276"><xref:System.Windows.SizeToContent.WidthAndHeight>.</span></span> <span data-ttu-id="0aff9-277">Přizpůsobit na obsahu šířka a výška, který má stejný účinek jako nastavení obě <xref:System.Windows.FrameworkElement.MinHeight%2A> a <xref:System.Windows.FrameworkElement.MaxHeight%2A> na výšku obsahu i nastavení <xref:System.Windows.FrameworkElement.MinWidth%2A> a <xref:System.Windows.FrameworkElement.MaxWidth%2A> na šířku obsahu.</span><span class="sxs-lookup"><span data-stu-id="0aff9-277">Fit to content width and height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content, and setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
 <span data-ttu-id="0aff9-278">Následující příklad ukazuje okno která automaticky velikosti podle jeho obsahu svisle i vodorovně, pokud zobrazen jako první.</span><span class="sxs-lookup"><span data-stu-id="0aff9-278">The following example shows a window that automatically sizes to fit its content, both vertically and horizontally, when first shown.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup2)]  
  
 <span data-ttu-id="0aff9-279">Následující příklad ukazuje, jak nastavit <xref:System.Windows.Window.SizeToContent%2A> vlastností v kódu k určení, jak se okno změní podle jeho obsahu.</span><span class="sxs-lookup"><span data-stu-id="0aff9-279">The following example shows how to set the <xref:System.Windows.Window.SizeToContent%2A> property in code to specify how a window resizes to fit its content    .</span></span>
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>   
## <a name="order-of-precedence-for-sizing-properties"></a><span data-ttu-id="0aff9-280">Pořadí priorit o velikosti vlastnosti</span><span class="sxs-lookup"><span data-stu-id="0aff9-280">Order of Precedence for Sizing Properties</span></span>  
 <span data-ttu-id="0aff9-281">V podstatě různé vlastnosti velikosti okna se kombinují a definují rozsah šířky a výšky pro okno umožňující změnu velikosti.</span><span class="sxs-lookup"><span data-stu-id="0aff9-281">Essentially, the various sizes properties of a window combine to define the range of width and height for a resizable window.</span></span> <span data-ttu-id="0aff9-282">K zajištění platný rozsah se zachová, <xref:System.Windows.Window> vyhodnotí hodnoty vlastností velikost pomocí následující objednávky priorit.</span><span class="sxs-lookup"><span data-stu-id="0aff9-282">To ensure a valid range is maintained, <xref:System.Windows.Window> evaluates the values of the size properties using the following orders of precedence.</span></span>  
  
 <span data-ttu-id="0aff9-283">**Výška vlastnosti:**</span><span class="sxs-lookup"><span data-stu-id="0aff9-283">**For Height Properties:**</span></span>  
  
1.  <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType> >  
  
2.  <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType> >  
  
3.  <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType> >  
  
4.  <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="0aff9-284">**Šířka vlastnosti:**</span><span class="sxs-lookup"><span data-stu-id="0aff9-284">**For Width Properties:**</span></span>  
  
1.  <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType> >  
  
2.  <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType> >  
  
3.  <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType> >  
  
4.  <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="0aff9-285">Pořadí priorit můžete také určit velikost okna, když ho je maximalizované, který je spravován pomocí <xref:System.Windows.Window.WindowState%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0aff9-285">The order of precedence can also determine the size of a window when it is maximized, which is managed with the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="WindowState"></a>   
## <a name="window-state"></a><span data-ttu-id="0aff9-286">Stav okna</span><span class="sxs-lookup"><span data-stu-id="0aff9-286">Window State</span></span>  
 <span data-ttu-id="0aff9-287">Po dobu životnosti okno s možností změny velikosti, může mít tři stavy: Normální, minimalizovat a v maximalizovaném okně.</span><span class="sxs-lookup"><span data-stu-id="0aff9-287">During the lifetime of a resizable window, it can have three states: normal, minimized, and maximized.</span></span> <span data-ttu-id="0aff9-288">Okno s *normální* stav je výchozí stav časového období.</span><span class="sxs-lookup"><span data-stu-id="0aff9-288">A window with a *normal* state is the default state of a window.</span></span> <span data-ttu-id="0aff9-289">Okno s Tento stav umožňuje uživateli přesunout a jeho velikost na základě velikosti úchytu nebo ohraničení, pokud je s možností změny velikosti.</span><span class="sxs-lookup"><span data-stu-id="0aff9-289">A window with this state allows a user to move and resize it by using a resize grip or the border, if it is resizable.</span></span>  
  
 <span data-ttu-id="0aff9-290">Okno s *minimalizovaná* stavu Hroutí k jeho tlačítko panelu úloh, pokud <xref:System.Windows.Window.ShowInTaskbar%2A> je nastaven na `true`, jinak se sbalí nejmenší možná velikost může být a přemístí samotné okraje v levém dolním rohu plochy.</span><span class="sxs-lookup"><span data-stu-id="0aff9-290">A window with a *minimized* state collapses to its task bar button if <xref:System.Windows.Window.ShowInTaskbar%2A> is set to `true`; otherwise, it collapses to the smallest possible size it can be and relocates itself to the bottom-left corner of the desktop.</span></span> <span data-ttu-id="0aff9-291">Ani typu minimalizovaném okně velikost lze změnit pomocí ohraničení nebo změnit velikost úchytu, i když minimalizovaném okně, které se zobrazí na hlavním panelu můžete přetáhnout kolem plochy.</span><span class="sxs-lookup"><span data-stu-id="0aff9-291">Neither type of minimized window can be resized using a border or resize grip, although a minimized window that isn't shown in the task bar can be dragged around the desktop.</span></span>  
  
 <span data-ttu-id="0aff9-292">Okno s *maximalizovaný* stavu zasahuje do maximální velikost může být, která bude pouze tak velké, jaká jeho <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, a <xref:System.Windows.Window.SizeToContent%2A> tu určují vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="0aff9-292">A window with a *maximized* state expands to the maximum size it can be, which will only be as large as its <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and <xref:System.Windows.Window.SizeToContent%2A> properties dictate.</span></span> <span data-ttu-id="0aff9-293">Maximalizovaném okně jako minimalizovaném okně, nebude možné změnit pomocí změny velikosti úchytu nebo přetažením ohraničení.</span><span class="sxs-lookup"><span data-stu-id="0aff9-293">Like a minimized window, a maximized window cannot be resized by using a resize grip or by dragging the border.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0aff9-294">Hodnoty <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti časového období vždy představují hodnoty pro stav Normální, i když aktuálně maximalizovaný nebo minimalizovaná okna.</span><span class="sxs-lookup"><span data-stu-id="0aff9-294">The values of the <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.Height%2A> properties of a window always represent the values for the normal state, even when the window is currently maximized or minimized.</span></span>  
  
 <span data-ttu-id="0aff9-295">Stav okno se dá nakonfigurovat nastavení jeho <xref:System.Windows.Window.WindowState%2A> vlastnosti, která může mít jednu z následujících <xref:System.Windows.WindowState> hodnot výčtu:</span><span class="sxs-lookup"><span data-stu-id="0aff9-295">The state of a window can be configured by setting its <xref:System.Windows.Window.WindowState%2A> property, which can have one of the following <xref:System.Windows.WindowState> enumeration values:</span></span>  
  
-   <span data-ttu-id="0aff9-296"><xref:System.Windows.WindowState.Normal>(výchozí)</span><span class="sxs-lookup"><span data-stu-id="0aff9-296"><xref:System.Windows.WindowState.Normal> (default)</span></span>  
  
-   <xref:System.Windows.WindowState.Maximized>  
  
-   <xref:System.Windows.WindowState.Minimized>  
  
 <span data-ttu-id="0aff9-297">Následující příklad ukazuje, jak vytvořit okno, které se zobrazí jako maximalizovaný po jejím otevření.</span><span class="sxs-lookup"><span data-stu-id="0aff9-297">The following example shows how to create a window that is shown as maximized when it opens.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup2)]  
  
 <span data-ttu-id="0aff9-298">Obecně byste měli nastavit <xref:System.Windows.Window.WindowState%2A> můžete nakonfigurovat počáteční stav časového období.</span><span class="sxs-lookup"><span data-stu-id="0aff9-298">In general, you should set <xref:System.Windows.Window.WindowState%2A> to configure the initial state of a window.</span></span> <span data-ttu-id="0aff9-299">Jakmile se zobrazí okno s možností změny velikosti, uživatelé stiskněte minimalizovat, maximalizovat a obnovit tlačítka v záhlaví okna na změnu stavu okna.</span><span class="sxs-lookup"><span data-stu-id="0aff9-299">Once a resizable window is shown, users can press the minimize, maximize, and restore buttons on the window's title bar to change the window state.</span></span>  
  
<a name="WindowAppearance"></a>   
## <a name="window-appearance"></a><span data-ttu-id="0aff9-300">Okno vzhledu</span><span class="sxs-lookup"><span data-stu-id="0aff9-300">Window Appearance</span></span>  
 <span data-ttu-id="0aff9-301">Změna vzhledu klientské oblasti okno přidáním okno obsahu, jako je například textová pole, tlačítka a popisky.</span><span class="sxs-lookup"><span data-stu-id="0aff9-301">You change the appearance of the client area of a window by adding window-specific content to it, such as buttons, labels, and text boxes.</span></span> <span data-ttu-id="0aff9-302">Ke konfiguraci neklientská oblast <xref:System.Windows.Window> nabízí několik vlastností, které zahrnují <xref:System.Windows.Window.Icon%2A> nastavit ikonu časového období a <xref:System.Windows.Window.Title%2A> nastavit její název.</span><span class="sxs-lookup"><span data-stu-id="0aff9-302">To configure the non-client area, <xref:System.Windows.Window> provides several properties, which include <xref:System.Windows.Window.Icon%2A> to set a window's icon and <xref:System.Windows.Window.Title%2A> to set its title.</span></span>  
  
 <span data-ttu-id="0aff9-303">Také můžete změnit vzhled a chování ohraničení neklientská oblast konfigurace režim změny velikosti časového období, styl oken, a určuje, zda se zobrazí jako tlačítka na panelu úloh klientů.</span><span class="sxs-lookup"><span data-stu-id="0aff9-303">You can also change the appearance and behavior of non-client area border by configuring a window's resize mode, window style, and whether it appears as a button in the desktop task bar.</span></span>  
  
  
<a name="Resize_Mode"></a>   
### <a name="resize-mode"></a><span data-ttu-id="0aff9-304">Změnit velikost režimu</span><span class="sxs-lookup"><span data-stu-id="0aff9-304">Resize Mode</span></span>  
 <span data-ttu-id="0aff9-305">V závislosti na <xref:System.Windows.Window.WindowStyle%2A> vlastnost, můžete řídit způsob (a pokud) uživatelé mohou změnit velikost okna.</span><span class="sxs-lookup"><span data-stu-id="0aff9-305">Depending on the <xref:System.Windows.Window.WindowStyle%2A> property, you can control how (and if) users can resize the window.</span></span> <span data-ttu-id="0aff9-306">Volba Styl okna ovlivňuje, jestli uživatel může změnit velikost okna tak, že přetáhnete jeho ohraničení pomocí myši, jestli **minimalizaci**, **Maximalizovat**, a **změnit velikost** tlačítka zobrazí na neklientská oblast, a pokud se zdá, jestli jsou povolené.</span><span class="sxs-lookup"><span data-stu-id="0aff9-306">The choice of window style affects whether a user can resize the window by dragging its border with the mouse, whether the **Minimize**, **Maximize**, and **Resize** buttons appear on the non-client area, and, if they do appear, whether they are enabled.</span></span>  
  
 <span data-ttu-id="0aff9-307">Můžete nakonfigurovat, jak se okno změní nastavením jeho <xref:System.Windows.Window.ResizeMode%2A> vlastnosti, která může být jedna z následujících <xref:System.Windows.ResizeMode> hodnot výčtu:</span><span class="sxs-lookup"><span data-stu-id="0aff9-307">You can configure how a window resizes by setting its <xref:System.Windows.Window.ResizeMode%2A> property, which can be one of the following <xref:System.Windows.ResizeMode> enumeration values:</span></span>  
  
-   <xref:System.Windows.ResizeMode.NoResize>  
  
-   <xref:System.Windows.ResizeMode.CanMinimize>  
  
-   <span data-ttu-id="0aff9-308"><xref:System.Windows.ResizeMode.CanResize>(výchozí)</span><span class="sxs-lookup"><span data-stu-id="0aff9-308"><xref:System.Windows.ResizeMode.CanResize> (default)</span></span>  
  
-   <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 <span data-ttu-id="0aff9-309">Stejně jako u <xref:System.Windows.Window.WindowStyle%2A>, režim změny velikosti okna nepravděpodobné, chcete-li změnit během celé jeho životnosti, což znamená, že budete pravděpodobně nastavíte z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek.</span><span class="sxs-lookup"><span data-stu-id="0aff9-309">As with <xref:System.Windows.Window.WindowStyle%2A>, the resize mode of a window is unlikely to change during its lifetime, which means that you'll most likely set it from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup2)]  
  
 <span data-ttu-id="0aff9-310">Všimněte si, že můžete zjistit, jestli je okno maximalizované, rychle minimalizovat nebo obnovit zkontrolováním <xref:System.Windows.Window.WindowState%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0aff9-310">Note that you can detect whether a window is maximized, minimized, or restored by inspecting the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="Window_Style"></a>   
### <a name="window-style"></a><span data-ttu-id="0aff9-311">Styl okna</span><span class="sxs-lookup"><span data-stu-id="0aff9-311">Window Style</span></span>  
 <span data-ttu-id="0aff9-312">Ohraničení, který je zveřejněný z jiného počítače než klientského oblasti časového období je vhodná pro většinu aplikací.</span><span class="sxs-lookup"><span data-stu-id="0aff9-312">The border that is exposed from the non-client area of a window is suitable for most applications.</span></span> <span data-ttu-id="0aff9-313">Existují však okolnosti, kdy je potřeba různé typy ohraničení nebo žádné ohraničení, je potřeba vůbec, v závislosti na typu časového období.</span><span class="sxs-lookup"><span data-stu-id="0aff9-313">However, there are circumstances where different types of borders are needed, or no borders are needed at all, depending on the type of window.</span></span>  
  
 <span data-ttu-id="0aff9-314">K řízení, jaké typy ohraničení okno získá, nastavíte jeho <xref:System.Windows.Window.WindowStyle%2A> vlastnost s jedním z následujících hodnot <xref:System.Windows.WindowStyle> výčtu:</span><span class="sxs-lookup"><span data-stu-id="0aff9-314">To control what type of border a window gets, you set its <xref:System.Windows.Window.WindowStyle%2A> property with one of the following values of the <xref:System.Windows.WindowStyle> enumeration:</span></span>  
  
-   <xref:System.Windows.WindowStyle.None>  
  
-   <span data-ttu-id="0aff9-315"><xref:System.Windows.WindowStyle.SingleBorderWindow>(výchozí)</span><span class="sxs-lookup"><span data-stu-id="0aff9-315"><xref:System.Windows.WindowStyle.SingleBorderWindow> (default)</span></span>  
  
-   <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
-   <xref:System.Windows.WindowStyle.ToolWindow>  
  
 <span data-ttu-id="0aff9-316">Účinek tyto styly oken jsou zobrazené na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="0aff9-316">The effect of these window styles are illustrated in the following figure.</span></span>  
  
 <span data-ttu-id="0aff9-317">![Styly oken](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure6.PNG "WindowOverviewFigure6")</span><span class="sxs-lookup"><span data-stu-id="0aff9-317">![Window styles](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure6.PNG "WindowOverviewFigure6")</span></span>  
  
 <span data-ttu-id="0aff9-318">Můžete nastavit <xref:System.Windows.Window.WindowStyle%2A> buď pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kód; protože nepravděpodobné, chcete-li změnit během časového období platnosti, budou s největší pravděpodobností nakonfigurujete pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek.</span><span class="sxs-lookup"><span data-stu-id="0aff9-318">You can set <xref:System.Windows.Window.WindowStyle%2A> using either [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup or code; because it is unlikely to change during the lifetime of a window, you will most likely configure it using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup2)]  
  
#### <a name="non-rectangular-window-style"></a><span data-ttu-id="0aff9-319">Styl obdélníkový oken</span><span class="sxs-lookup"><span data-stu-id="0aff9-319">Non-Rectangular Window Style</span></span>  
 <span data-ttu-id="0aff9-320">Existují také situace, kdy které styly ohraničení <xref:System.Windows.Window.WindowStyle%2A> umožňuje vám tak, aby měl nestačí.</span><span class="sxs-lookup"><span data-stu-id="0aff9-320">There are also situations where the border styles that <xref:System.Windows.Window.WindowStyle%2A> allows you to have are not sufficient.</span></span> <span data-ttu-id="0aff9-321">Například můžete chtít vytvořit aplikaci s obdélníkový ohraničení, jako je [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] používá.</span><span class="sxs-lookup"><span data-stu-id="0aff9-321">For example, you may want to create an application with a non-rectangular border, like [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] uses.</span></span>  
  
 <span data-ttu-id="0aff9-322">Představte si třeba okna bublin řeči vidět na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="0aff9-322">For example, consider the speech bubble window shown in the following figure.</span></span>  
  
 <span data-ttu-id="0aff9-323">![Nepravoúhlý okno](../../../../docs/framework/wpf/app-development/media/nonrectangularwindowfigure.PNG "NonRectangularWindowFigure")</span><span class="sxs-lookup"><span data-stu-id="0aff9-323">![Nonrectangular window](../../../../docs/framework/wpf/app-development/media/nonrectangularwindowfigure.PNG "NonRectangularWindowFigure")</span></span>  
  
 <span data-ttu-id="0aff9-324">Tento typ okna lze vytvořit pomocí nastavení <xref:System.Windows.Window.WindowStyle%2A> vlastnost <xref:System.Windows.WindowStyle.None>a pomocí speciální podpory, který <xref:System.Windows.Window> má transparentnosti.</span><span class="sxs-lookup"><span data-stu-id="0aff9-324">This type of window can be created by setting the <xref:System.Windows.Window.WindowStyle%2A> property to <xref:System.Windows.WindowStyle.None>, and by using special support that <xref:System.Windows.Window> has for transparency.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup2)]  
  
 <span data-ttu-id="0aff9-325">Tato kombinace hodnot dá pokyn okno k vykreslení zcela transparentní.</span><span class="sxs-lookup"><span data-stu-id="0aff9-325">This combination of values instructs the window to render completely transparent.</span></span> <span data-ttu-id="0aff9-326">V tomto stavu nelze použít okně neklientská oblast vylepšení (Zavřít nabídky, tlačítka Minimalizovat, maximalizovat a obnovení a tak dále).</span><span class="sxs-lookup"><span data-stu-id="0aff9-326">In this state, the window's non-client area adornments (the Close menu, Minimize, Maximize, and Restore buttons, and so on) cannot be used.</span></span> <span data-ttu-id="0aff9-327">V důsledku toho je třeba zadat vlastní.</span><span class="sxs-lookup"><span data-stu-id="0aff9-327">Consequently, you need to provide your own.</span></span>  
  
<a name="Task_Bar_Presence"></a>   
### <a name="task-bar-presence"></a><span data-ttu-id="0aff9-328">Přítomnosti na hlavním panelu</span><span class="sxs-lookup"><span data-stu-id="0aff9-328">Task Bar Presence</span></span>  
 <span data-ttu-id="0aff9-329">Výchozí vzhled okno obsahuje tlačítko panelu úloh, stejný, jako je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="0aff9-329">The default appearance of a window includes a task bar button, like the one shown in the following figure.</span></span>  
  
 <span data-ttu-id="0aff9-330">![Okno s tlačítkem na hlavním panelu](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure7.PNG "WindowOverviewFigure7")</span><span class="sxs-lookup"><span data-stu-id="0aff9-330">![Window with a task bar button](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure7.PNG "WindowOverviewFigure7")</span></span>  
  
 <span data-ttu-id="0aff9-331">Některé typy windows nemáte tlačítko panelu úloh, jako je například okna zpráv a dialogových oken (viz [dialogové okno Přehled polí](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="0aff9-331">Some types of windows don't have a task bar button, such as message boxes and dialog boxes (see [Dialog Boxes Overview](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md)).</span></span> <span data-ttu-id="0aff9-332">Můžete řídit, jestli se zobrazí tlačítko panelu úloh v časovém období nastavením <xref:System.Windows.Window.ShowInTaskbar%2A> vlastnost (`true` ve výchozím nastavení).</span><span class="sxs-lookup"><span data-stu-id="0aff9-332">You can control whether the task bar button for a window is shown by setting the <xref:System.Windows.Window.ShowInTaskbar%2A> property (`true` by default).</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup2)]  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations"></a><span data-ttu-id="0aff9-333">Důležité informace o zabezpečení</span><span class="sxs-lookup"><span data-stu-id="0aff9-333">Security Considerations</span></span>  
 <span data-ttu-id="0aff9-334"><xref:System.Windows.Window>vyžaduje `UnmanagedCode` oprávnění zabezpečení k vytvořit instanci.</span><span class="sxs-lookup"><span data-stu-id="0aff9-334"><xref:System.Windows.Window> requires `UnmanagedCode` security permission to be instantiated.</span></span> <span data-ttu-id="0aff9-335">Pro aplikace v nainstalován a spuštěn z místního počítače to spadá do sadu oprávnění, kterým je uděleno oprávnění k aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0aff9-335">For applications installed on and launched from the local machine, this falls within the set of permissions that are granted to the application.</span></span>  
  
 <span data-ttu-id="0aff9-336">To však spadá mimo sadu oprávnění udělená aplikace, které jsou spouštěny z Internetu nebo místní intranetové zóny pomocí [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0aff9-336">However, this falls outside the set of permissions granted to applications that are launched from the Internet or Local intranet zone using [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)].</span></span> <span data-ttu-id="0aff9-337">V důsledku toho se uživatelé dostanou [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] upozornění zabezpečení a bude nutné zvýšení oprávnění, nastavení pro aplikaci na úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="0aff9-337">Consequently, users will receive a [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] security warning and will need to elevate the permission set for the application to full trust.</span></span>  
  
 <span data-ttu-id="0aff9-338">Kromě toho [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] nelze zobrazit systému windows nebo dialogová okna ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="0aff9-338">Additionally, [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] cannot show windows or dialog boxes by default.</span></span> <span data-ttu-id="0aff9-339">Podrobné informace o aspekty zabezpečení samostatné aplikace, najdete v části [strategie zabezpečení WPF - platformy zabezpečení](../../../../docs/framework/wpf/wpf-security-strategy-platform-security.md).</span><span class="sxs-lookup"><span data-stu-id="0aff9-339">For a discussion on standalone application security considerations, see [WPF Security Strategy - Platform Security](../../../../docs/framework/wpf/wpf-security-strategy-platform-security.md).</span></span>  
  
<a name="Other_Types_of_Windows"></a>   
## <a name="other-types-of-windows"></a><span data-ttu-id="0aff9-340">Jiné typy systému Windows</span><span class="sxs-lookup"><span data-stu-id="0aff9-340">Other Types of Windows</span></span>  
 <span data-ttu-id="0aff9-341"><xref:System.Windows.Navigation.NavigationWindow>je okno, které slouží jako hostitele obsahu navigaci.</span><span class="sxs-lookup"><span data-stu-id="0aff9-341"><xref:System.Windows.Navigation.NavigationWindow> is a window that is designed to host navigable content.</span></span> <span data-ttu-id="0aff9-342">Další informace najdete v tématu [navigační přehled](../../../../docs/framework/wpf/app-development/navigation-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="0aff9-342">For more information, see [Navigation Overview](../../../../docs/framework/wpf/app-development/navigation-overview.md)).</span></span>  
  
 <span data-ttu-id="0aff9-343">Dialogová okna jsou windows, které se často používá ke shromažďování informací od uživatele k dokončení funkce.</span><span class="sxs-lookup"><span data-stu-id="0aff9-343">Dialog boxes are windows that are often used to gather information from a user to complete a function.</span></span> <span data-ttu-id="0aff9-344">Například pokud uživatel chce k otevření souboru, **otevřít soubor** obvykle zobrazí dialogové okno pomocí aplikace pro získání názvu souboru od uživatele.</span><span class="sxs-lookup"><span data-stu-id="0aff9-344">For example, when a user wants to open a file, the **Open File** dialog box is usually displayed by an application to get the file name from the user.</span></span> <span data-ttu-id="0aff9-345">Další informace najdete v tématu [dialogové okno Přehled polí](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0aff9-345">For more information, see [Dialog Boxes Overview](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aff9-346">Viz také</span><span class="sxs-lookup"><span data-stu-id="0aff9-346">See Also</span></span>  
 <xref:System.Windows.Window>  
 <xref:System.Windows.MessageBox>  
 <xref:System.Windows.Navigation.NavigationWindow>  
 <xref:System.Windows.Application>  
 [<span data-ttu-id="0aff9-347">Přehled dialogových oken</span><span class="sxs-lookup"><span data-stu-id="0aff9-347">Dialog Boxes Overview</span></span>](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md)  
 [<span data-ttu-id="0aff9-348">Sestavení aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="0aff9-348">Building a WPF Application</span></span>](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)
