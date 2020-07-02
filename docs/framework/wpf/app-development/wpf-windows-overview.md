---
title: Přehled systému Windows
description: Seznamte se se základy vytváření a správy Windows pro samostatné aplikace v Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
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
ms.openlocfilehash: e1ad3c118fbaea8f1e23d012721f0cf3c2c50015
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622884"
---
# <a name="wpf-windows-overview"></a><span data-ttu-id="8b800-103">Přehled WPF Windows</span><span class="sxs-lookup"><span data-stu-id="8b800-103">WPF Windows Overview</span></span>
<span data-ttu-id="8b800-104">Uživatelé pracují se samostatnými aplikacemi Windows Presentation Foundation (WPF) prostřednictvím systému Windows.</span><span class="sxs-lookup"><span data-stu-id="8b800-104">Users interact with Windows Presentation Foundation (WPF) standalone applications through windows.</span></span> <span data-ttu-id="8b800-105">Hlavním účelem okna je hostování obsahu, který vizualizuje data a umožňuje uživatelům pracovat s daty.</span><span class="sxs-lookup"><span data-stu-id="8b800-105">The primary purpose of a window is to host content that visualizes data and enables users to interact with data.</span></span> <span data-ttu-id="8b800-106">Samostatné aplikace WPF poskytují vlastní okna pomocí <xref:System.Windows.Window> třídy.</span><span class="sxs-lookup"><span data-stu-id="8b800-106">Standalone WPF applications provide their own windows by using the <xref:System.Windows.Window> class.</span></span> <span data-ttu-id="8b800-107">V tomto tématu <xref:System.Windows.Window> se seznámíte se základy vytváření a správy oken v samostatných aplikacích.</span><span class="sxs-lookup"><span data-stu-id="8b800-107">This topic introduces <xref:System.Windows.Window> before covering the fundamentals of creating and managing windows in standalone applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b800-108">Aplikace WPF hostované v prohlížeči, včetně aplikací prohlížeče XAML (XBAP) a volných [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] stránek, neposkytují vlastní okna.</span><span class="sxs-lookup"><span data-stu-id="8b800-108">Browser-hosted WPF applications, including XAML browser applications (XBAPs) and loose [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pages, don't provide their own windows.</span></span> <span data-ttu-id="8b800-109">Místo toho jsou hostovány ve Windows, poskytovaném aplikací Windows Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="8b800-109">Instead, they are hosted in windows provided by Windows Internet Explorer.</span></span> <span data-ttu-id="8b800-110">Viz téma [Přehled aplikací prohlížeče WPF XAML](wpf-xaml-browser-applications-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8b800-110">See [WPF XAML Browser Applications Overview](wpf-xaml-browser-applications-overview.md).</span></span>  

<a name="TheWindowClass"></a>
## <a name="the-window-class"></a><span data-ttu-id="8b800-111">Třída okna</span><span class="sxs-lookup"><span data-stu-id="8b800-111">The Window Class</span></span>  
 <span data-ttu-id="8b800-112">Následující obrázek znázorňuje prvky části okna:</span><span class="sxs-lookup"><span data-stu-id="8b800-112">The following figure illustrates the constituent parts of a window:</span></span>  
  
 ![Snímek obrazovky zobrazující prvky okna](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 <span data-ttu-id="8b800-114">Okno je rozděleno do dvou oblastí: mimo klientské a klientské oblasti.</span><span class="sxs-lookup"><span data-stu-id="8b800-114">A window is divided into two areas: the non-client area and client area.</span></span>  
  
 <span data-ttu-id="8b800-115">*Neklientská oblast* okna je implementována pomocí WPF a zahrnuje části okna, která jsou společná pro většinu oken, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="8b800-115">The *non-client area* of a window is implemented by WPF and includes the parts of a window that are common to most windows, including the following:</span></span>  
  
- <span data-ttu-id="8b800-116">Ohraničení.</span><span class="sxs-lookup"><span data-stu-id="8b800-116">A border.</span></span>  
  
- <span data-ttu-id="8b800-117">Záhlaví.</span><span class="sxs-lookup"><span data-stu-id="8b800-117">A title bar.</span></span>  
  
- <span data-ttu-id="8b800-118">Ikona.</span><span class="sxs-lookup"><span data-stu-id="8b800-118">An icon.</span></span>  
  
- <span data-ttu-id="8b800-119">Tlačítka minimalizovat, maximalizovat a obnovit.</span><span class="sxs-lookup"><span data-stu-id="8b800-119">Minimize, Maximize, and Restore buttons.</span></span>  
  
- <span data-ttu-id="8b800-120">Tlačítko Zavřít</span><span class="sxs-lookup"><span data-stu-id="8b800-120">A Close button.</span></span>  
  
- <span data-ttu-id="8b800-121">Systémová nabídka s položkami nabídky, které uživatelům umožňují minimalizovat, maximalizovat, obnovit, přesunout, změnit velikost a zavřít okno.</span><span class="sxs-lookup"><span data-stu-id="8b800-121">A System menu with menu items that allow users to minimize, maximize, restore, move, resize, and close a window.</span></span>  
  
 <span data-ttu-id="8b800-122">*Klientská oblast* okna je oblast v neklientské oblasti okna, kterou vývojáři používají k přidání obsahu specifického pro aplikaci, jako jsou například panely nabídek, panely nástrojů a ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="8b800-122">The *client area* of a window is the area within a window's non-client area and is used by developers to add application-specific content, such as menu bars, tool bars, and controls.</span></span>  
  
 <span data-ttu-id="8b800-123">V WPF je okno zapouzdřené <xref:System.Windows.Window> třídou, kterou použijete k provedení následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="8b800-123">In WPF, a window is encapsulated by the <xref:System.Windows.Window> class that you use to do the following:</span></span>  
  
- <span data-ttu-id="8b800-124">Zobrazí okno.</span><span class="sxs-lookup"><span data-stu-id="8b800-124">Display a window.</span></span>  
  
- <span data-ttu-id="8b800-125">Nakonfigurujte velikost, umístění a vzhled okna.</span><span class="sxs-lookup"><span data-stu-id="8b800-125">Configure the size, position, and appearance of a window.</span></span>  
  
- <span data-ttu-id="8b800-126">Hostování obsahu specifického pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8b800-126">Host application-specific content.</span></span>  
  
- <span data-ttu-id="8b800-127">Umožňuje spravovat dobu života okna.</span><span class="sxs-lookup"><span data-stu-id="8b800-127">Manage the lifetime of a window.</span></span>  
  
<a name="DefiningAWindow"></a>
## <a name="implementing-a-window"></a><span data-ttu-id="8b800-128">Implementace okna</span><span class="sxs-lookup"><span data-stu-id="8b800-128">Implementing a Window</span></span>  
 <span data-ttu-id="8b800-129">Implementace typického okna zahrnuje vzhled i chování, kde *vzhled* definuje, jak okno vypadá uživatelům a *chování* definuje způsob, jakým okno funguje, jak se s ním uživatelé budou pracovat.</span><span class="sxs-lookup"><span data-stu-id="8b800-129">The implementation of a typical window comprises both appearance and behavior, where *appearance* defines how a window looks to users and *behavior* defines the way a window functions as users interact with it.</span></span> <span data-ttu-id="8b800-130">V jazyce WPF můžete implementovat vzhled a chování okna pomocí kódu nebo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značky.</span><span class="sxs-lookup"><span data-stu-id="8b800-130">In WPF, you can implement the appearance and behavior of a window using either code or [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 <span data-ttu-id="8b800-131">Obecně se však vzhled okna implementuje pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek a jeho chování je implementováno pomocí kódu na pozadí, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8b800-131">In general, however, the appearance of a window is implemented using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and its behavior is implemented using code-behind, as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 <span data-ttu-id="8b800-132">Chcete-li povolit spolupráci [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru značek a souboru s kódem na pozadí, jsou vyžadovány následující:</span><span class="sxs-lookup"><span data-stu-id="8b800-132">To enable a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup file and code-behind file to work together, the following are required:</span></span>  
  
- <span data-ttu-id="8b800-133">V kódu `Window` musí element obsahovat `x:Class` atribut.</span><span class="sxs-lookup"><span data-stu-id="8b800-133">In markup, the `Window` element must include the `x:Class` attribute.</span></span> <span data-ttu-id="8b800-134">Když je aplikace sestavena, existence `x:Class` v souboru označení způsobí, že nástroj Microsoft Build Engine (MSBuild) vytvoří `partial` třídu, která je odvozena z <xref:System.Windows.Window> a má název, který je určen `x:Class` atributem.</span><span class="sxs-lookup"><span data-stu-id="8b800-134">When the application is built, the existence of `x:Class` in the markup file causes Microsoft build engine (MSBuild) to create a `partial` class that derives from <xref:System.Windows.Window> and has the name that is specified by the `x:Class` attribute.</span></span> <span data-ttu-id="8b800-135">To vyžaduje přidání deklarace oboru názvů XML pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schéma ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).</span><span class="sxs-lookup"><span data-stu-id="8b800-135">This requires the addition of an XML namespace declaration for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schema ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).</span></span> <span data-ttu-id="8b800-136">Vygenerovaná `partial` Třída implementuje `InitializeComponent` metodu, která je volána k registraci událostí a nastavení vlastností, které jsou implementovány v označení.</span><span class="sxs-lookup"><span data-stu-id="8b800-136">The generated `partial` class implements the `InitializeComponent` method, which is called to register the events and set the properties that are implemented in markup.</span></span>  
  
- <span data-ttu-id="8b800-137">V kódu na pozadí třída musí být `partial` Třída se stejným názvem, který je určen `x:Class` atributem v označení a musí odvozovat z <xref:System.Windows.Window> .</span><span class="sxs-lookup"><span data-stu-id="8b800-137">In code-behind, the class must be a `partial` class with the same name that is specified by the `x:Class` attribute in markup, and it must derive from <xref:System.Windows.Window>.</span></span> <span data-ttu-id="8b800-138">To umožňuje, aby soubor s kódem na pozadí byl přidružen ke `partial` třídě, která je generována pro soubor označení při sestavení aplikace (viz [Vytvoření aplikace WPF](building-a-wpf-application-wpf.md)).</span><span class="sxs-lookup"><span data-stu-id="8b800-138">This allows the code-behind file to be associated with the `partial` class that is generated for the markup file when the application is built (see [Building a WPF Application](building-a-wpf-application-wpf.md)).</span></span>  
  
- <span data-ttu-id="8b800-139">V kódu na pozadí <xref:System.Windows.Window> Třída musí implementovat konstruktor, který volá `InitializeComponent` metodu.</span><span class="sxs-lookup"><span data-stu-id="8b800-139">In code-behind, the <xref:System.Windows.Window> class must implement a constructor that calls the `InitializeComponent` method.</span></span> <span data-ttu-id="8b800-140">`InitializeComponent`je implementována třídou vygenerovanou souborem označení `partial` pro registraci událostí a nastavení vlastností, které jsou definovány v označení.</span><span class="sxs-lookup"><span data-stu-id="8b800-140">`InitializeComponent` is implemented by the markup file's generated `partial` class to register events and set properties that are defined in markup.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b800-141">Přidáte-li <xref:System.Windows.Window> do projektu nový pomocí sady Visual Studio, <xref:System.Windows.Window> je implementováno pomocí kódu a kódu na pozadí a obsahuje nezbytnou konfiguraci pro vytvoření přidružení mezi značkami a soubory kódu na pozadí, jak je popsáno zde.</span><span class="sxs-lookup"><span data-stu-id="8b800-141">When you add a new <xref:System.Windows.Window> to your project by using Visual Studio, the <xref:System.Windows.Window> is implemented using both markup and code-behind, and includes the necessary configuration to create the association between the markup and code-behind files as described here.</span></span>  
  
 <span data-ttu-id="8b800-142">S touto konfigurací se můžete soustředit na definování vzhledu okna v kódu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a implementaci jeho chování v kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="8b800-142">With this configuration in place, you can focus on defining the appearance of the window in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and implementing its behavior in code-behind.</span></span> <span data-ttu-id="8b800-143">Následující příklad ukazuje okno s tlačítkem, implementované v kódu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a obslužná rutina události pro <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Událost tlačítka, implementovaná v kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="8b800-143">The following example shows a window with a button, implemented in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and an event handler for the button's <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, implemented in code-behind.</span></span>  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>
## <a name="configuring-a-window-definition-for-msbuild"></a><span data-ttu-id="8b800-144">Konfigurace definice okna pro MSBuild</span><span class="sxs-lookup"><span data-stu-id="8b800-144">Configuring a Window Definition for MSBuild</span></span>  
 <span data-ttu-id="8b800-145">Způsob implementace vašeho okna určuje, jak je nakonfigurován pro nástroj MSBuild.</span><span class="sxs-lookup"><span data-stu-id="8b800-145">How you implement your window determines how it is configured for MSBuild.</span></span> <span data-ttu-id="8b800-146">Pro okno, které je definováno pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek a kódu na pozadí:</span><span class="sxs-lookup"><span data-stu-id="8b800-146">For a window that is defined using both [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind:</span></span>  
  
- <span data-ttu-id="8b800-147">Soubory značek XAML jsou konfigurovány jako `Page` položky MSBuild.</span><span class="sxs-lookup"><span data-stu-id="8b800-147">XAML markup files are configured as MSBuild `Page` items.</span></span>  
  
- <span data-ttu-id="8b800-148">Soubory kódu na pozadí jsou konfigurovány jako `Compile` položky nástroje MSBuild.</span><span class="sxs-lookup"><span data-stu-id="8b800-148">Code-behind files are configured as MSBuild `Compile` items.</span></span>  
  
 <span data-ttu-id="8b800-149">Tento soubor je zobrazen v následujícím souboru projektu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="8b800-149">This is shown in the following MSBuild project file.</span></span>  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 <span data-ttu-id="8b800-150">Informace o vytváření aplikací WPF naleznete v tématu [sestavování aplikace WPF](building-a-wpf-application-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="8b800-150">For information about building WPF applications, see [Building a WPF Application](building-a-wpf-application-wpf.md).</span></span>  
  
<a name="WindowLifetime"></a>
## <a name="window-lifetime"></a><span data-ttu-id="8b800-151">Doba života okna</span><span class="sxs-lookup"><span data-stu-id="8b800-151">Window Lifetime</span></span>  
 <span data-ttu-id="8b800-152">Stejně jako u libovolné třídy má okno životnost, která začíná při prvním vytvoření instance, po jejím otevření, aktivaci a deaktivaci a nakonec uzavření.</span><span class="sxs-lookup"><span data-stu-id="8b800-152">As with any class, a window has a lifetime that begins when it is first instantiated, after which it is opened, activated and deactivated, and eventually closed.</span></span>  

<a name="Opening_a_Window"></a>
### <a name="opening-a-window"></a><span data-ttu-id="8b800-153">Otevření okna</span><span class="sxs-lookup"><span data-stu-id="8b800-153">Opening a Window</span></span>  
 <span data-ttu-id="8b800-154">Chcete-li otevřít okno, nejprve vytvořte jeho instanci, která je znázorněna v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8b800-154">To open a window, you first create an instance of it, which is demonstrated in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 <span data-ttu-id="8b800-155">V tomto příkladu `MarkupAndCodeBehindWindow` je vytvořena instance při spuštění aplikace, což nastane při <xref:System.Windows.Application.Startup> vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="8b800-155">In this example, the `MarkupAndCodeBehindWindow` is instantiated when the application starts, which occurs when the <xref:System.Windows.Application.Startup> event is raised.</span></span>  
  
 <span data-ttu-id="8b800-156">Při vytvoření instance okna je odkaz na něj automaticky přidán do seznamu oken, který je spravován <xref:System.Windows.Application> objektem (viz <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType> ).</span><span class="sxs-lookup"><span data-stu-id="8b800-156">When a window is instantiated, a reference to it is automatically added to a list of windows that is managed by the <xref:System.Windows.Application> object (see <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>).</span></span> <span data-ttu-id="8b800-157">Kromě toho první okno, které má být vytvořena instance, je ve výchozím nastavení nastaveno <xref:System.Windows.Application> jako hlavní okno aplikace (viz <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType> ).</span><span class="sxs-lookup"><span data-stu-id="8b800-157">Additionally, the first window to be instantiated is, by default, set by <xref:System.Windows.Application> as the main application window (see <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="8b800-158">Okno je nakonec otevřeno voláním metody. <xref:System.Windows.Window.Show%2A> výsledek je znázorněn na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="8b800-158">The window is finally opened by calling the <xref:System.Windows.Window.Show%2A> method; the result is shown in the following figure.</span></span>  
  
 ![Okno otevřené voláním okna. show](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 <span data-ttu-id="8b800-160">Okno otevřené voláním <xref:System.Windows.Window.Show%2A> je nemodální okno, což znamená, že aplikace funguje v režimu, který umožňuje uživatelům aktivovat další okna ve stejné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8b800-160">A window that is opened by calling <xref:System.Windows.Window.Show%2A> is a modeless window, which means that the application operates in a mode that allows users to activate other windows in the same application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b800-161"><xref:System.Windows.Window.ShowDialog%2A>je volána pro otevření oken, například dialogová okna v modálním formátu.</span><span class="sxs-lookup"><span data-stu-id="8b800-161"><xref:System.Windows.Window.ShowDialog%2A> is called to open windows such as dialog boxes modally.</span></span> <span data-ttu-id="8b800-162">Další informace najdete v tématu Přehled dialogových [oken](dialog-boxes-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="8b800-162">See [Dialog Boxes Overview](dialog-boxes-overview.md) for more information.</span></span>  
  
 <span data-ttu-id="8b800-163">Když <xref:System.Windows.Window.Show%2A> je volána, okno provede inicializační práci předtím, než se zobrazí, aby se navázala infrastruktura, která umožňuje přijímat uživatelský vstup.</span><span class="sxs-lookup"><span data-stu-id="8b800-163">When <xref:System.Windows.Window.Show%2A> is called, a window performs initialization work before it is shown to establish infrastructure that allows it to receive user input.</span></span> <span data-ttu-id="8b800-164">Po inicializaci okna se <xref:System.Windows.Window.SourceInitialized> událost vyvolá a zobrazí se okno.</span><span class="sxs-lookup"><span data-stu-id="8b800-164">When the window is initialized, the <xref:System.Windows.Window.SourceInitialized> event is raised and the window is shown.</span></span>  
  
 <span data-ttu-id="8b800-165">Jako zástupce <xref:System.Windows.Application.StartupUri%2A> lze nastavit, aby určovalo první okno, které se automaticky otevře při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="8b800-165">As a shortcut, <xref:System.Windows.Application.StartupUri%2A> can be set to specify the first window that is opened automatically when an application starts.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 <span data-ttu-id="8b800-166">Po spuštění aplikace je okno určené hodnotou <xref:System.Windows.Application.StartupUri%2A> otevřeno nemodální. interně je okno otevřeno voláním jeho <xref:System.Windows.Window.Show%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8b800-166">When the application starts, the window specified by the value of <xref:System.Windows.Application.StartupUri%2A> is opened modelessly; internally, the window is opened by calling its <xref:System.Windows.Window.Show%2A> method.</span></span>  
  
<a name="Ownership"></a>
#### <a name="window-ownership"></a><span data-ttu-id="8b800-167">Vlastnictví okna</span><span class="sxs-lookup"><span data-stu-id="8b800-167">Window Ownership</span></span>  
 <span data-ttu-id="8b800-168">Okno, které je otevřeno pomocí metody, nemá <xref:System.Windows.Window.Show%2A> implicitní relaci s oknem, který ho vytvořil. uživatelé mohou pracovat s některým z oken nezávisle na sobě, což znamená, že jedno okno může provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="8b800-168">A window that is opened by using the <xref:System.Windows.Window.Show%2A> method does not have an implicit relationship with the window that created it; users can interact with either window independently of the other, which means that either window can do the following:</span></span>  
  
- <span data-ttu-id="8b800-169">Zakrytí druhé (Pokud má jedna z oken <xref:System.Windows.Window.Topmost%2A> nastavenou vlastnost `true` ).</span><span class="sxs-lookup"><span data-stu-id="8b800-169">Cover the other (unless one of the windows has its <xref:System.Windows.Window.Topmost%2A> property set to `true`).</span></span>  
  
- <span data-ttu-id="8b800-170">Minimalizujte, maximalizujete a obnovíte, aniž by to ovlivnilo druhý.</span><span class="sxs-lookup"><span data-stu-id="8b800-170">Be minimized, maximized, and restored without affecting the other.</span></span>  
  
 <span data-ttu-id="8b800-171">Některá okna vyžadují relaci s oknem, který je otevírá.</span><span class="sxs-lookup"><span data-stu-id="8b800-171">Some windows require a relationship with the window that opens them.</span></span> <span data-ttu-id="8b800-172">Například aplikace integrovaného vývojového prostředí (IDE) může otevřít okna vlastností a nástrojů, jejichž typické chování je pokrýt okno, které je vytvoří.</span><span class="sxs-lookup"><span data-stu-id="8b800-172">For example, an Integrated Development Environment (IDE) application may open property windows and tool windows whose typical behavior is to cover the window that creates them.</span></span> <span data-ttu-id="8b800-173">Kromě toho by tato okna měla vždycky zavřít, minimalizovat, maximalizovat a obnovit ve vzájemné součinnosti s oknem, který je vytvořil.</span><span class="sxs-lookup"><span data-stu-id="8b800-173">Furthermore, such windows should always close, minimize, maximize, and restore in concert with the window that created them.</span></span> <span data-ttu-id="8b800-174">Takový vztah může být vytvořen tak, že *jedno okno* naplňuje jako jiné a je dosaženo nastavením <xref:System.Windows.Window.Owner%2A> vlastnosti vlastnictví *okna* s odkazem na *okno vlastníka*.</span><span class="sxs-lookup"><span data-stu-id="8b800-174">Such a relationship can be established by making one window *own* another, and is achieved by setting the <xref:System.Windows.Window.Owner%2A> property of the *owned window* with a reference to the *owner window*.</span></span> <span data-ttu-id="8b800-175">To je ukázáno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8b800-175">This is shown in the following example.</span></span>  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 <span data-ttu-id="8b800-176">Po navázání vlastnictví:</span><span class="sxs-lookup"><span data-stu-id="8b800-176">After ownership is established:</span></span>  
  
- <span data-ttu-id="8b800-177">Vlastněné okno může odkazovat na své nadřazené okno kontrolou hodnoty jeho <xref:System.Windows.Window.Owner%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8b800-177">The owned window can reference its owner window by inspecting the value of its <xref:System.Windows.Window.Owner%2A> property.</span></span>  
  
- <span data-ttu-id="8b800-178">Okno vlastník může zjistit, že je v něm vlastní systém Windows, a to tak, že zkontroluje hodnotu jeho <xref:System.Windows.Window.OwnedWindows%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8b800-178">The owner window can discover all the windows it owns by inspecting the value of its <xref:System.Windows.Window.OwnedWindows%2A> property.</span></span>  
  
<a name="Preventing"></a>
#### <a name="preventing-window-activation"></a><span data-ttu-id="8b800-179">Prevence aktivace okna</span><span class="sxs-lookup"><span data-stu-id="8b800-179">Preventing Window Activation</span></span>  
 <span data-ttu-id="8b800-180">Existují situace, kdy by systém Windows neměl být aktivovaný, pokud je zobrazený, například okna konverzace aplikace ve stylu kurýrní služby nebo okna oznámení e-mailové aplikace.</span><span class="sxs-lookup"><span data-stu-id="8b800-180">There are scenarios where windows should not be activated when shown, such as conversation windows of an Internet messenger-style application or notification windows of an email application.</span></span>  
  
 <span data-ttu-id="8b800-181">Pokud má aplikace okno, které by se nemělo aktivovat, pokud je zobrazeno, můžete nastavit jeho <xref:System.Windows.Window.ShowActivated%2A> vlastnost na hodnotu `false` před <xref:System.Windows.Window.Show%2A> prvním voláním metody.</span><span class="sxs-lookup"><span data-stu-id="8b800-181">If your application has a window that shouldn't be activated when shown, you can set its <xref:System.Windows.Window.ShowActivated%2A> property to `false` before calling the <xref:System.Windows.Window.Show%2A> method for the first time.</span></span> <span data-ttu-id="8b800-182">Jako důsledek:</span><span class="sxs-lookup"><span data-stu-id="8b800-182">As a consequence:</span></span>  
  
- <span data-ttu-id="8b800-183">Okno není aktivováno.</span><span class="sxs-lookup"><span data-stu-id="8b800-183">The window is not activated.</span></span>  
  
- <span data-ttu-id="8b800-184">Událost okna není <xref:System.Windows.Window.Activated> vyvolána.</span><span class="sxs-lookup"><span data-stu-id="8b800-184">The window's <xref:System.Windows.Window.Activated> event is not raised.</span></span>  
  
- <span data-ttu-id="8b800-185">Aktuálně aktivované okno zůstane aktivované.</span><span class="sxs-lookup"><span data-stu-id="8b800-185">The currently activated window remains activated.</span></span>  
  
 <span data-ttu-id="8b800-186">Okno se aktivuje, ale jakmile ho uživatel aktivuje, klikněte buď na klienta, nebo na oblast mimo klienta.</span><span class="sxs-lookup"><span data-stu-id="8b800-186">The window will become activated, however, as soon as the user activates it by clicking either the client or non-client area.</span></span> <span data-ttu-id="8b800-187">V tomto případě:</span><span class="sxs-lookup"><span data-stu-id="8b800-187">In this case:</span></span>  
  
- <span data-ttu-id="8b800-188">Okno je aktivováno.</span><span class="sxs-lookup"><span data-stu-id="8b800-188">The window is activated.</span></span>  
  
- <span data-ttu-id="8b800-189"><xref:System.Windows.Window.Activated>Vyvolá se událost okna.</span><span class="sxs-lookup"><span data-stu-id="8b800-189">The window's <xref:System.Windows.Window.Activated> event is raised.</span></span>  
  
- <span data-ttu-id="8b800-190">Dříve aktivované okno je deaktivováno.</span><span class="sxs-lookup"><span data-stu-id="8b800-190">The previously activated window is deactivated.</span></span>  
  
- <span data-ttu-id="8b800-191"><xref:System.Windows.Window.Deactivated> <xref:System.Windows.Window.Activated> V reakci na akce uživatele jsou následně vyvolány okno a události.</span><span class="sxs-lookup"><span data-stu-id="8b800-191">The window's <xref:System.Windows.Window.Deactivated> and <xref:System.Windows.Window.Activated> events are subsequently raised as expected in response to user actions.</span></span>  
  
<a name="Window_Activation"></a>
### <a name="window-activation"></a><span data-ttu-id="8b800-192">Aktivace okna</span><span class="sxs-lookup"><span data-stu-id="8b800-192">Window Activation</span></span>  
 <span data-ttu-id="8b800-193">Při prvním otevření okna se zobrazí okno aktivní (Pokud se nezobrazí s <xref:System.Windows.Window.ShowActivated%2A> nastavením na `false` ).</span><span class="sxs-lookup"><span data-stu-id="8b800-193">When a window is first opened, it becomes the active window (unless it is shown with <xref:System.Windows.Window.ShowActivated%2A> set to `false`).</span></span> <span data-ttu-id="8b800-194">*Aktivní okno* je okno, které aktuálně zachytí vstup uživatele, například tahy kláves a kliknutí myší.</span><span class="sxs-lookup"><span data-stu-id="8b800-194">The *active window* is the window that is currently capturing user input, such as key strokes and mouse clicks.</span></span> <span data-ttu-id="8b800-195">Když dojde k aktivaci okna, vyvolá <xref:System.Windows.Window.Activated> událost.</span><span class="sxs-lookup"><span data-stu-id="8b800-195">When a window becomes active, it raises the <xref:System.Windows.Window.Activated> event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b800-196">Při prvním otevření okna se <xref:System.Windows.FrameworkElement.Loaded> události a vyvolá až <xref:System.Windows.Window.ContentRendered> po <xref:System.Windows.Window.Activated> vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="8b800-196">When a window is first opened, the <xref:System.Windows.FrameworkElement.Loaded> and <xref:System.Windows.Window.ContentRendered> events are raised only after the <xref:System.Windows.Window.Activated> event is raised.</span></span> <span data-ttu-id="8b800-197">V takovém případě může být okno efektivně považováno za otevřené při <xref:System.Windows.Window.ContentRendered> vyvolání.</span><span class="sxs-lookup"><span data-stu-id="8b800-197">With this in mind, a window can effectively be considered opened when <xref:System.Windows.Window.ContentRendered> is raised.</span></span>  
  
 <span data-ttu-id="8b800-198">Po aktivaci okna může uživatel aktivovat jiné okno ve stejné aplikaci nebo aktivovat jinou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8b800-198">After a window becomes active, a user can activate another window in the same application, or activate another application.</span></span> <span data-ttu-id="8b800-199">Pokud k tomu dojde, stane se aktuálně aktivní okno deaktivováno a vyvolá <xref:System.Windows.Window.Deactivated> událost.</span><span class="sxs-lookup"><span data-stu-id="8b800-199">When that happens, the currently active window becomes deactivated and raises the <xref:System.Windows.Window.Deactivated> event.</span></span> <span data-ttu-id="8b800-200">Podobně když uživatel vybere aktuálně deaktivované okno, okno se znovu aktivuje a <xref:System.Windows.Window.Activated> vyvolá se.</span><span class="sxs-lookup"><span data-stu-id="8b800-200">Likewise, when the user selects a currently deactivated window, the window becomes active again and <xref:System.Windows.Window.Activated> is raised.</span></span>  
  
 <span data-ttu-id="8b800-201">Jedním z běžných důvodů, jak zpracovat a <xref:System.Windows.Window.Activated> <xref:System.Windows.Window.Deactivated> Zakázat funkce, které lze spustit pouze v případě, že je okno aktivní.</span><span class="sxs-lookup"><span data-stu-id="8b800-201">One common reason to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> is to enable and disable functionality that can only run when a window is active.</span></span> <span data-ttu-id="8b800-202">Například některá okna zobrazují interaktivní obsah, který vyžaduje stálý vstup uživatele nebo pozornost, včetně her a přehrávačů videí.</span><span class="sxs-lookup"><span data-stu-id="8b800-202">For example, some windows display interactive content that requires constant user input or attention, including games and video players.</span></span> <span data-ttu-id="8b800-203">Následující příklad je zjednodušený přehrávač videa, který ukazuje, jak zpracovat <xref:System.Windows.Window.Activated> a <xref:System.Windows.Window.Deactivated> implementovat toto chování.</span><span class="sxs-lookup"><span data-stu-id="8b800-203">The following example is a simplified video player that demonstrates how to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> to implement this behavior.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 <span data-ttu-id="8b800-204">Jiné typy aplikací mohou stále spouštět kód na pozadí, když dojde k deaktivaci okna.</span><span class="sxs-lookup"><span data-stu-id="8b800-204">Other types of applications may still run code in the background when a window is deactivated.</span></span> <span data-ttu-id="8b800-205">Například poštovní klient může pokračovat v dotazování poštovního serveru, zatímco uživatel používá jiné aplikace.</span><span class="sxs-lookup"><span data-stu-id="8b800-205">For example, a mail client may continue polling the mail server while the user is using other applications.</span></span> <span data-ttu-id="8b800-206">Tyto aplikace často poskytují jiné nebo dodatečné chování při deaktivaci hlavního okna.</span><span class="sxs-lookup"><span data-stu-id="8b800-206">Applications like these often provide different or additional behavior while the main window is deactivated.</span></span> <span data-ttu-id="8b800-207">V souvislosti s e-mailovým programem může to znamenat, že by se nová položka pošty přidala do doručené pošty a přidala se ikona oznámení do systémového zásobníku.</span><span class="sxs-lookup"><span data-stu-id="8b800-207">With respect to the mail program, this may mean both adding the new mail item to the inbox and adding a notification icon to the system tray.</span></span> <span data-ttu-id="8b800-208">Ikona oznámení musí být zobrazena pouze v případě, že okno pošty není aktivní, což lze určit kontrolou <xref:System.Windows.Window.IsActive%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8b800-208">A notification icon need only be displayed when the mail window isn't active, which can be determined by inspecting the <xref:System.Windows.Window.IsActive%2A> property.</span></span>  
  
 <span data-ttu-id="8b800-209">Pokud je úloha na pozadí dokončena, okno může chtít uživateli upozorňovat na naléhavější voláním <xref:System.Windows.Window.Activate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8b800-209">If a background task completes, a window may want to notify the user more urgently by calling <xref:System.Windows.Window.Activate%2A> method.</span></span> <span data-ttu-id="8b800-210">Pokud uživatel pracuje s jinou aplikací aktivovanou <xref:System.Windows.Window.Activate%2A> , když je volána, tlačítko na hlavním panelu bude blikat.</span><span class="sxs-lookup"><span data-stu-id="8b800-210">If the user is interacting with another application activated when <xref:System.Windows.Window.Activate%2A> is called, the window's taskbar button flashes.</span></span> <span data-ttu-id="8b800-211">Pokud uživatel spolupracuje s aktuální aplikací, volání přepne <xref:System.Windows.Window.Activate%2A> okno do popředí.</span><span class="sxs-lookup"><span data-stu-id="8b800-211">If a user is interacting with the current application, calling <xref:System.Windows.Window.Activate%2A> will bring the window to the foreground.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b800-212">Můžete zpracovávat aktivaci rozsahu aplikace pomocí <xref:System.Windows.Application.Activated?displayProperty=nameWithType> <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> událostí a.</span><span class="sxs-lookup"><span data-stu-id="8b800-212">You can handle application-scope activation using the <xref:System.Windows.Application.Activated?displayProperty=nameWithType> and <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> events.</span></span>  
  
<a name="Closing_a_Window"></a>
### <a name="closing-a-window"></a><span data-ttu-id="8b800-213">Zavření okna</span><span class="sxs-lookup"><span data-stu-id="8b800-213">Closing a Window</span></span>  
 <span data-ttu-id="8b800-214">Životnost okna začíná až do konce, když ho uživatel zavře.</span><span class="sxs-lookup"><span data-stu-id="8b800-214">The life of a window starts coming to an end when a user closes it.</span></span> <span data-ttu-id="8b800-215">Okno lze uzavřít pomocí prvků v neklientské oblasti, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="8b800-215">A window can be closed by using elements in the non-client area, including the following:</span></span>  
  
- <span data-ttu-id="8b800-216">Položka **Zavřít** v **systémové** nabídce</span><span class="sxs-lookup"><span data-stu-id="8b800-216">The **Close** item of the **System** menu.</span></span>  
  
- <span data-ttu-id="8b800-217">Stiskněte kombinaci kláves ALT + F4.</span><span class="sxs-lookup"><span data-stu-id="8b800-217">Pressing ALT+F4.</span></span>  
  
- <span data-ttu-id="8b800-218">Stisknutí tlačítka **Zavřít** .</span><span class="sxs-lookup"><span data-stu-id="8b800-218">Pressing the **Close** button.</span></span>  
  
 <span data-ttu-id="8b800-219">Do klientské oblasti můžete poskytnout další mechanismy pro zavření okna, běžnější z nich, které zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="8b800-219">You can provide additional mechanisms to the client area to close a window, the more common of which include the following:</span></span>  
  
- <span data-ttu-id="8b800-220">Položka **Exit** v nabídce **soubor** , obvykle pro okna hlavní aplikace.</span><span class="sxs-lookup"><span data-stu-id="8b800-220">An **Exit** item in the **File** menu, typically for main application windows.</span></span>  
  
- <span data-ttu-id="8b800-221">Položka **Zavřít** v nabídce **soubor** , která se obvykle nachází v sekundárním okně aplikace.</span><span class="sxs-lookup"><span data-stu-id="8b800-221">A **Close** item in the **File** menu, typically on a secondary application window.</span></span>  
  
- <span data-ttu-id="8b800-222">Tlačítko **Zrušit** , obvykle v modálním dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="8b800-222">A **Cancel** button, typically on a modal dialog box.</span></span>  
  
- <span data-ttu-id="8b800-223">Tlačítko **Zavřít** , obvykle v nemodálním dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="8b800-223">A **Close** button, typically on a modeless dialog box.</span></span>  
  
 <span data-ttu-id="8b800-224">Chcete-li zavřít okno v reakci na některý z těchto vlastních mechanismů, je třeba zavolat <xref:System.Windows.Window.Close%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="8b800-224">To close a window in response to one of these custom mechanisms, you need to call the <xref:System.Windows.Window.Close%2A> method.</span></span> <span data-ttu-id="8b800-225">Následující příklad implementuje možnost Zavřít okno výběrem možnosti **konec** v nabídce **soubor** .</span><span class="sxs-lookup"><span data-stu-id="8b800-225">The following example implements the ability to close a window by choosing the **Exit** on the **File** menu.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 <span data-ttu-id="8b800-226">Po zavření okna vyvolá dvě události: <xref:System.Windows.Window.Closing> a <xref:System.Windows.Window.Closed> .</span><span class="sxs-lookup"><span data-stu-id="8b800-226">When a window closes, it raises two events: <xref:System.Windows.Window.Closing> and <xref:System.Windows.Window.Closed>.</span></span>  
  
 <span data-ttu-id="8b800-227"><xref:System.Windows.Window.Closing>je aktivována před zavřením okna a poskytuje mechanismus, pomocí kterého lze zabránit zavření okna.</span><span class="sxs-lookup"><span data-stu-id="8b800-227"><xref:System.Windows.Window.Closing> is raised before the window closes, and it provides a mechanism by which window closure can be prevented.</span></span> <span data-ttu-id="8b800-228">Jedním z běžných důvodů, jak zabránit zavření okna, je, pokud obsah okna obsahuje upravená data.</span><span class="sxs-lookup"><span data-stu-id="8b800-228">One common reason to prevent window closure is if window content contains modified data.</span></span> <span data-ttu-id="8b800-229">V takovém <xref:System.Windows.Window.Closing> případě může být událost zpracována za účelem zjištění, zda jsou data nečistá, a pokud ano, požádejte uživatele, aby buď pokračoval v zavírání okna bez uložení dat, nebo zrušení zavření okna.</span><span class="sxs-lookup"><span data-stu-id="8b800-229">In this situation, the <xref:System.Windows.Window.Closing> event can be handled to determine whether data is dirty and, if so, to ask the user whether to either continue closing the window without saving the data or to cancel window closure.</span></span> <span data-ttu-id="8b800-230">Následující příklad ukazuje klíčové aspekty manipulace <xref:System.Windows.Window.Closing> .</span><span class="sxs-lookup"><span data-stu-id="8b800-230">The following example shows the key aspects of handling <xref:System.Windows.Window.Closing>.</span></span>  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 <span data-ttu-id="8b800-231"><xref:System.Windows.Window.Closing>Obslužná rutina události je předána a <xref:System.ComponentModel.CancelEventArgs> , která implementuje `Boolean` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> vlastnost, která je nastavena na, `true` aby zabránila zavření okna.</span><span class="sxs-lookup"><span data-stu-id="8b800-231">The <xref:System.Windows.Window.Closing> event handler is passed a <xref:System.ComponentModel.CancelEventArgs>, which implements the `Boolean`<xref:System.ComponentModel.CancelEventArgs.Cancel%2A> property that you set to `true` to prevent a window from closing.</span></span>  
  
 <span data-ttu-id="8b800-232">Pokud není <xref:System.Windows.Window.Closing> zpracována nebo je zpracována, ale není zrušeno, okno se zavře.</span><span class="sxs-lookup"><span data-stu-id="8b800-232">If <xref:System.Windows.Window.Closing> is not handled, or it is handled but not canceled, the window will close.</span></span> <span data-ttu-id="8b800-233">Těsně před tím, než se okno skutečně zavře, <xref:System.Windows.Window.Closed> se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="8b800-233">Just before a window actually closes, <xref:System.Windows.Window.Closed> is raised.</span></span> <span data-ttu-id="8b800-234">V tuto chvíli není možné zabránit zavření okna.</span><span class="sxs-lookup"><span data-stu-id="8b800-234">At this point, a window cannot be prevented from closing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b800-235">Aplikaci lze nakonfigurovat tak, aby se automaticky vypnula při zavření okna hlavní aplikace (viz <xref:System.Windows.Application.MainWindow%2A> ) nebo po zavření posledního okna.</span><span class="sxs-lookup"><span data-stu-id="8b800-235">An application can be configured to shut down automatically when either the main application window closes (see <xref:System.Windows.Application.MainWindow%2A>) or the last window closes.</span></span> <span data-ttu-id="8b800-236">Podrobnosti najdete v tématu <xref:System.Windows.Application.ShutdownMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="8b800-236">For details, see <xref:System.Windows.Application.ShutdownMode%2A>.</span></span>  
  
 <span data-ttu-id="8b800-237">I když může být okno explicitně uzavřeno prostřednictvím mechanismů, které jsou k dispozici v klientských a klientských oblastech, může být okno také implicitně uzavřeno v důsledku chování v jiných částech aplikace nebo Windows, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="8b800-237">While a window can be explicitly closed through mechanisms provided in the non-client and client areas, a window can also be implicitly closed as a result of behavior in other parts of the application or Windows, including the following:</span></span>  
  
- <span data-ttu-id="8b800-238">Uživatel se odhlásí nebo vypne v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="8b800-238">A user logs off or shuts down Windows.</span></span>  
  
- <span data-ttu-id="8b800-239">Vlastník okna se zavře (viz <xref:System.Windows.Window.Owner%2A> ).</span><span class="sxs-lookup"><span data-stu-id="8b800-239">A window's owner closes (see <xref:System.Windows.Window.Owner%2A>).</span></span>  
  
- <span data-ttu-id="8b800-240">Hlavní okno aplikace je zavřené a <xref:System.Windows.Application.ShutdownMode%2A> je <xref:System.Windows.ShutdownMode.OnMainWindowClose> .</span><span class="sxs-lookup"><span data-stu-id="8b800-240">The main application window is closed and <xref:System.Windows.Application.ShutdownMode%2A> is <xref:System.Windows.ShutdownMode.OnMainWindowClose>.</span></span>  
  
- <span data-ttu-id="8b800-241"><xref:System.Windows.Application.Shutdown%2A>je volána.</span><span class="sxs-lookup"><span data-stu-id="8b800-241"><xref:System.Windows.Application.Shutdown%2A> is called.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b800-242">Po zavření okna nelze znovu otevřít.</span><span class="sxs-lookup"><span data-stu-id="8b800-242">A window cannot be reopened after it is closed.</span></span>  
  
<a name="Window_Lifetime_Events"></a>
### <a name="window-lifetime-events"></a><span data-ttu-id="8b800-243">Události životního cyklu okna</span><span class="sxs-lookup"><span data-stu-id="8b800-243">Window Lifetime Events</span></span>  
 <span data-ttu-id="8b800-244">Následující ilustrace znázorňuje sekvenci hlavních událostí v době života okna:</span><span class="sxs-lookup"><span data-stu-id="8b800-244">The following illustration shows the sequence of the principal events in the lifetime of a window:</span></span>  
  
 ![Diagram, který zobrazuje události v době života okna.](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 <span data-ttu-id="8b800-246">Následující ilustrace znázorňuje sekvenci hlavních událostí v době životnosti okna, které je zobrazeno bez aktivace ( <xref:System.Windows.Window.ShowActivated%2A> je nastaveno na hodnotu `false` před zobrazením okna):</span><span class="sxs-lookup"><span data-stu-id="8b800-246">The following illustration shows the sequence of the principal events in the lifetime of a window that is shown without activation (<xref:System.Windows.Window.ShowActivated%2A> is set to `false` before the window is shown):</span></span>  
  
 ![Diagram, který zobrazuje události v době života okna bez aktivace.](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>
## <a name="window-location"></a><span data-ttu-id="8b800-248">Umístění okna</span><span class="sxs-lookup"><span data-stu-id="8b800-248">Window Location</span></span>  
 <span data-ttu-id="8b800-249">Když je okno otevřené, má umístění v rozměrech x a y relativně k ploše.</span><span class="sxs-lookup"><span data-stu-id="8b800-249">While a window is open, it has a location in the x and y dimensions relative to the desktop.</span></span> <span data-ttu-id="8b800-250">Toto umístění lze určit kontrolou <xref:System.Windows.Window.Left%2A> vlastností a v <xref:System.Windows.Window.Top%2A> uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="8b800-250">This location can be determined by inspecting the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties, respectively.</span></span> <span data-ttu-id="8b800-251">Nastavením těchto vlastností lze změnit umístění okna.</span><span class="sxs-lookup"><span data-stu-id="8b800-251">You can set these properties to change the location of the window.</span></span>  
  
 <span data-ttu-id="8b800-252">Můžete také zadat počáteční umístění <xref:System.Windows.Window> při prvním zobrazení nastavením <xref:System.Windows.Window.WindowStartupLocation%2A> vlastnosti pomocí jedné z následujících <xref:System.Windows.WindowStartupLocation> hodnot výčtu:</span><span class="sxs-lookup"><span data-stu-id="8b800-252">You can also specify the initial location of a <xref:System.Windows.Window> when it first appears by setting the <xref:System.Windows.Window.WindowStartupLocation%2A> property with one of the following <xref:System.Windows.WindowStartupLocation> enumeration values:</span></span>  
  
- <span data-ttu-id="8b800-253"><xref:System.Windows.WindowStartupLocation.CenterOwner>výchozí</span><span class="sxs-lookup"><span data-stu-id="8b800-253"><xref:System.Windows.WindowStartupLocation.CenterOwner> (default)</span></span>  
  
- <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
- <xref:System.Windows.WindowStartupLocation.Manual>  
  
 <span data-ttu-id="8b800-254">Pokud je počáteční umístění zadané jako <xref:System.Windows.WindowStartupLocation.Manual> a <xref:System.Windows.Window.Left%2A> <xref:System.Windows.Window.Top%2A> vlastnosti a nejsou nastavené, <xref:System.Windows.Window> požádá Windows o umístění, ve kterém se bude zobrazovat.</span><span class="sxs-lookup"><span data-stu-id="8b800-254">If the startup location is specified as <xref:System.Windows.WindowStartupLocation.Manual>, and the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties have not been set, <xref:System.Windows.Window> will ask Windows for a location to appear in.</span></span>  
  
<a name="Topmost_Windows_and_Z_Order"></a>
### <a name="topmost-windows-and-z-order"></a><span data-ttu-id="8b800-255">V horních oknech a pořadí Z</span><span class="sxs-lookup"><span data-stu-id="8b800-255">Topmost Windows and Z-Order</span></span>  
 <span data-ttu-id="8b800-256">Kromě umístění x a y má okno také místo v dimenzi z, které určuje jeho svislou polohu vzhledem k ostatním systémům Windows.</span><span class="sxs-lookup"><span data-stu-id="8b800-256">Besides having an x and y location, a window also has a location in the z dimension, which determines its vertical position with respect to other windows.</span></span> <span data-ttu-id="8b800-257">Toto se říká pořadí vykreslování v okně a existují dva typy: normální pořadí vykreslování a nejvyšší pořadí vykreslování.</span><span class="sxs-lookup"><span data-stu-id="8b800-257">This is known as the window's z-order, and there are two types: normal z-order and topmost z-order.</span></span> <span data-ttu-id="8b800-258">Umístění okna v *normálním pořadí z* je určeno, zda je aktuálně aktivní nebo ne.</span><span class="sxs-lookup"><span data-stu-id="8b800-258">The location of a window in the *normal z-order* is determined by whether it is currently active or not.</span></span> <span data-ttu-id="8b800-259">Ve výchozím nastavení je okno umístěno v normálním pořadí z.</span><span class="sxs-lookup"><span data-stu-id="8b800-259">By default, a window is located in the normal z-order.</span></span> <span data-ttu-id="8b800-260">Umístění okna v *horním pořadí z* je také určeno, zda je aktuálně aktivní nebo ne.</span><span class="sxs-lookup"><span data-stu-id="8b800-260">The location of a window in the *topmost z-order* is also determined by whether it is currently active or not.</span></span> <span data-ttu-id="8b800-261">Kromě toho Windows v horním pořadí z je vždycky umístěný nad Windows v normálním pořadí z.</span><span class="sxs-lookup"><span data-stu-id="8b800-261">Furthermore, windows in the topmost z-order are always located above windows in the normal z-order.</span></span> <span data-ttu-id="8b800-262">Okno je umístěno v horní části pořadí z – nastavením jeho <xref:System.Windows.Window.Topmost%2A> vlastnosti na `true` .</span><span class="sxs-lookup"><span data-stu-id="8b800-262">A window is located in the topmost z-order by setting its <xref:System.Windows.Window.Topmost%2A> property to `true`.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 <span data-ttu-id="8b800-263">V rámci každého pořadí z je zobrazeno aktuálně aktivní okno nad všemi ostatními okny ve stejném pořadí z.</span><span class="sxs-lookup"><span data-stu-id="8b800-263">Within each z-order, the currently active window appears above all other windows in the same z-order.</span></span>  
  
<a name="WindowSize"></a>
## <a name="window-size"></a><span data-ttu-id="8b800-264">Velikost okna</span><span class="sxs-lookup"><span data-stu-id="8b800-264">Window Size</span></span>  
 <span data-ttu-id="8b800-265">Kromě umístění na ploše má okno velikost, která je určena několika vlastnostmi, včetně různých vlastností šířky a výšky a <xref:System.Windows.Window.SizeToContent%2A> .</span><span class="sxs-lookup"><span data-stu-id="8b800-265">Besides having a desktop location, a window has a size that is determined by several properties, including the various width and height properties and <xref:System.Windows.Window.SizeToContent%2A>.</span></span>  
  
 <span data-ttu-id="8b800-266"><xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A> , a <xref:System.Windows.FrameworkElement.MaxWidth%2A> slouží ke správě rozsahu šířek, které může okno mít během své životnosti a jsou konfigurovány tak, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8b800-266"><xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.MaxWidth%2A> are used to manage the range of widths that a window can have during its lifetime, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 <span data-ttu-id="8b800-267">Výška okna je spravována pomocí <xref:System.Windows.FrameworkElement.MinHeight%2A> , <xref:System.Windows.FrameworkElement.Height%2A> , a <xref:System.Windows.FrameworkElement.MaxHeight%2A> , a je konfigurována tak, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8b800-267">Window height is managed by <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, and <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 <span data-ttu-id="8b800-268">Vzhledem k tomu, že různé hodnoty šířky a hodnoty výšky určují rozsah, je možné, že šířka a Výška okna s možností změny velikosti budou kdekoli v zadaném rozsahu pro příslušnou dimenzi.</span><span class="sxs-lookup"><span data-stu-id="8b800-268">Because the various width values and height values each specify a range, it is possible for the width and height of a resizable window to be anywhere within the specified range for the respective dimension.</span></span> <span data-ttu-id="8b800-269">Chcete-li zjistit aktuální šířku a výšku, zkontrolujte <xref:System.Windows.FrameworkElement.ActualWidth%2A> a <xref:System.Windows.FrameworkElement.ActualHeight%2A> v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="8b800-269">To detect its current width and height, inspect <xref:System.Windows.FrameworkElement.ActualWidth%2A> and <xref:System.Windows.FrameworkElement.ActualHeight%2A>, respectively.</span></span>  
  
 <span data-ttu-id="8b800-270">Pokud chcete, aby Šířka a Výška okna měla velikost, která se vejde na velikost obsahu okna, můžete použít <xref:System.Windows.Window.SizeToContent%2A> vlastnost, která má následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="8b800-270">If you'd like the width and height of your window to have a size that fits to the size of the window's content, you can use the <xref:System.Windows.Window.SizeToContent%2A> property, which has the following values:</span></span>  
  
- <span data-ttu-id="8b800-271"><xref:System.Windows.SizeToContent.Manual>.</span><span class="sxs-lookup"><span data-stu-id="8b800-271"><xref:System.Windows.SizeToContent.Manual>.</span></span> <span data-ttu-id="8b800-272">Žádný efekt (výchozí).</span><span class="sxs-lookup"><span data-stu-id="8b800-272">No effect (default).</span></span>  
  
- <span data-ttu-id="8b800-273"><xref:System.Windows.SizeToContent.Width>.</span><span class="sxs-lookup"><span data-stu-id="8b800-273"><xref:System.Windows.SizeToContent.Width>.</span></span> <span data-ttu-id="8b800-274">Přizpůsobit šířce obsahu, která má stejný efekt jako nastavení <xref:System.Windows.FrameworkElement.MinWidth%2A> a <xref:System.Windows.FrameworkElement.MaxWidth%2A> na šířku obsahu.</span><span class="sxs-lookup"><span data-stu-id="8b800-274">Fit to content width, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
- <span data-ttu-id="8b800-275"><xref:System.Windows.SizeToContent.Height>.</span><span class="sxs-lookup"><span data-stu-id="8b800-275"><xref:System.Windows.SizeToContent.Height>.</span></span> <span data-ttu-id="8b800-276">Přizpůsobit výšce obsahu, která má stejný efekt jako nastavení obou <xref:System.Windows.FrameworkElement.MinHeight%2A> i <xref:System.Windows.FrameworkElement.MaxHeight%2A> na výšku obsahu.</span><span class="sxs-lookup"><span data-stu-id="8b800-276">Fit to content height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content.</span></span>  
  
- <span data-ttu-id="8b800-277"><xref:System.Windows.SizeToContent.WidthAndHeight>.</span><span class="sxs-lookup"><span data-stu-id="8b800-277"><xref:System.Windows.SizeToContent.WidthAndHeight>.</span></span> <span data-ttu-id="8b800-278">Přizpůsobit šířce a výšce obsahu, která má stejný efekt jako nastavení obou i <xref:System.Windows.FrameworkElement.MinHeight%2A> <xref:System.Windows.FrameworkElement.MaxHeight%2A> na výšku obsahu a nastavení i <xref:System.Windows.FrameworkElement.MinWidth%2A> <xref:System.Windows.FrameworkElement.MaxWidth%2A> na šířku obsahu.</span><span class="sxs-lookup"><span data-stu-id="8b800-278">Fit to content width and height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content, and setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
 <span data-ttu-id="8b800-279">Následující příklad ukazuje okno, které automaticky přizpůsobí svůj obsah, jak je to možné, vertikálně i vodorovně, pokud je zobrazeno první.</span><span class="sxs-lookup"><span data-stu-id="8b800-279">The following example shows a window that automatically sizes to fit its content, both vertically and horizontally, when first shown.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 <span data-ttu-id="8b800-280">Následující příklad ukazuje, jak nastavit <xref:System.Windows.Window.SizeToContent%2A> vlastnost v kódu pro určení, jak se změní velikost okna tak, aby odpovídala jeho obsahu.</span><span class="sxs-lookup"><span data-stu-id="8b800-280">The following example shows how to set the <xref:System.Windows.Window.SizeToContent%2A> property in code to specify how a window resizes to fit its content    .</span></span>
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>
## <a name="order-of-precedence-for-sizing-properties"></a><span data-ttu-id="8b800-281">Pořadí priorit pro vlastnosti velikosti</span><span class="sxs-lookup"><span data-stu-id="8b800-281">Order of Precedence for Sizing Properties</span></span>  
 <span data-ttu-id="8b800-282">V podstatě jsou různé vlastnosti velikosti okna kombinovány, aby bylo možné definovat rozsah šířky a výšky okna s možností změny velikosti.</span><span class="sxs-lookup"><span data-stu-id="8b800-282">Essentially, the various sizes properties of a window combine to define the range of width and height for a resizable window.</span></span> <span data-ttu-id="8b800-283">Chcete-li zajistit zachování platného rozsahu, <xref:System.Windows.Window> vyhodnotí hodnoty vlastností velikosti pomocí následujících pořadí priorit.</span><span class="sxs-lookup"><span data-stu-id="8b800-283">To ensure a valid range is maintained, <xref:System.Windows.Window> evaluates the values of the size properties using the following orders of precedence.</span></span>  
  
 <span data-ttu-id="8b800-284">**Pro vlastnosti výšky:**</span><span class="sxs-lookup"><span data-stu-id="8b800-284">**For Height Properties:**</span></span>  
  
1. <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="8b800-285">**Pro vlastnosti šířky:**</span><span class="sxs-lookup"><span data-stu-id="8b800-285">**For Width Properties:**</span></span>  
  
1. <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="8b800-286">Pořadí priorit může také určit velikost okna v případě maximalizace, které je spravováno pomocí <xref:System.Windows.Window.WindowState%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8b800-286">The order of precedence can also determine the size of a window when it is maximized, which is managed with the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="WindowState"></a>
## <a name="window-state"></a><span data-ttu-id="8b800-287">Stav okna</span><span class="sxs-lookup"><span data-stu-id="8b800-287">Window State</span></span>  
 <span data-ttu-id="8b800-288">Během životnosti okna s možností změny velikosti může mít tři stavy: normální, minimalizované a maximalizované.</span><span class="sxs-lookup"><span data-stu-id="8b800-288">During the lifetime of a resizable window, it can have three states: normal, minimized, and maximized.</span></span> <span data-ttu-id="8b800-289">Okno s *normálním* stavem je výchozí stav okna.</span><span class="sxs-lookup"><span data-stu-id="8b800-289">A window with a *normal* state is the default state of a window.</span></span> <span data-ttu-id="8b800-290">Okno s tímto stavem umožňuje uživateli, aby ho přesunul a změnil jeho velikost pomocí úchytu změny velikosti nebo ohraničení, pokud jde o změnu velikosti.</span><span class="sxs-lookup"><span data-stu-id="8b800-290">A window with this state allows a user to move and resize it by using a resize grip or the border, if it is resizable.</span></span>  
  
 <span data-ttu-id="8b800-291">Okno s *minimalizovaným* stavem se sbalí na jeho tlačítko na panelu úkolů <xref:System.Windows.Window.ShowInTaskbar%2A> , pokud je nastaveno na hodnotu `true` ; v opačném případě se sbalí na nejmenší možnou velikost, která může být a přemístění do levého dolního rohu plochy.</span><span class="sxs-lookup"><span data-stu-id="8b800-291">A window with a *minimized* state collapses to its task bar button if <xref:System.Windows.Window.ShowInTaskbar%2A> is set to `true`; otherwise, it collapses to the smallest possible size it can be and relocates itself to the bottom-left corner of the desktop.</span></span> <span data-ttu-id="8b800-292">Velikost minimalizovaného okna nelze měnit pomocí ohraničení nebo změny velikosti, i když minimalizované okno, které není zobrazeno na panelu úloh, lze přetáhnout na plochu.</span><span class="sxs-lookup"><span data-stu-id="8b800-292">Neither type of minimized window can be resized using a border or resize grip, although a minimized window that isn't shown in the task bar can be dragged around the desktop.</span></span>  
  
 <span data-ttu-id="8b800-293">Okno s *maximalizovaném* stavem se zvětšuje na maximální velikost, která může být, což bude mít až velkou hodnotu, <xref:System.Windows.FrameworkElement.MaxWidth%2A> <xref:System.Windows.FrameworkElement.MaxHeight%2A> a <xref:System.Windows.Window.SizeToContent%2A> vlastnosti se určí.</span><span class="sxs-lookup"><span data-stu-id="8b800-293">A window with a *maximized* state expands to the maximum size it can be, which will only be as large as its <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and <xref:System.Windows.Window.SizeToContent%2A> properties dictate.</span></span> <span data-ttu-id="8b800-294">Podobně jako minimalizované okno nelze upravit velikost maximalizovaného okna pomocí úchytu pro změnu velikosti nebo přetažením ohraničení.</span><span class="sxs-lookup"><span data-stu-id="8b800-294">Like a minimized window, a maximized window cannot be resized by using a resize grip or by dragging the border.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b800-295">Hodnoty <xref:System.Windows.Window.Top%2A> vlastností,, a <xref:System.Windows.Window.Left%2A> v <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> okně vždy reprezentují hodnoty pro normální stav, a to i v případě, že je okno momentálně maximalizováno nebo minimalizováno.</span><span class="sxs-lookup"><span data-stu-id="8b800-295">The values of the <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.Height%2A> properties of a window always represent the values for the normal state, even when the window is currently maximized or minimized.</span></span>  
  
 <span data-ttu-id="8b800-296">Stav okna lze nakonfigurovat nastavením jeho <xref:System.Windows.Window.WindowState%2A> vlastnosti, která může mít jednu z následujících <xref:System.Windows.WindowState> hodnot výčtu:</span><span class="sxs-lookup"><span data-stu-id="8b800-296">The state of a window can be configured by setting its <xref:System.Windows.Window.WindowState%2A> property, which can have one of the following <xref:System.Windows.WindowState> enumeration values:</span></span>  
  
- <span data-ttu-id="8b800-297"><xref:System.Windows.WindowState.Normal>výchozí</span><span class="sxs-lookup"><span data-stu-id="8b800-297"><xref:System.Windows.WindowState.Normal> (default)</span></span>  
  
- <xref:System.Windows.WindowState.Maximized>  
  
- <xref:System.Windows.WindowState.Minimized>  
  
 <span data-ttu-id="8b800-298">Následující příklad ukazuje, jak vytvořit okno, které se zobrazí při otevření v maximalizovaném okně.</span><span class="sxs-lookup"><span data-stu-id="8b800-298">The following example shows how to create a window that is shown as maximized when it opens.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 <span data-ttu-id="8b800-299">Obecně byste měli nastavit, <xref:System.Windows.Window.WindowState%2A> aby se nakonfiguroval počáteční stav okna.</span><span class="sxs-lookup"><span data-stu-id="8b800-299">In general, you should set <xref:System.Windows.Window.WindowState%2A> to configure the initial state of a window.</span></span> <span data-ttu-id="8b800-300">Jakmile se zobrazí okno pro změnu velikosti, uživatelé mohou změnit stav okna stisknutím tlačítek minimalizovat, maximalizovat a obnovit v záhlaví okna.</span><span class="sxs-lookup"><span data-stu-id="8b800-300">Once a resizable window is shown, users can press the minimize, maximize, and restore buttons on the window's title bar to change the window state.</span></span>  
  
<a name="WindowAppearance"></a>
## <a name="window-appearance"></a><span data-ttu-id="8b800-301">Vzhled okna</span><span class="sxs-lookup"><span data-stu-id="8b800-301">Window Appearance</span></span>  
 <span data-ttu-id="8b800-302">Můžete změnit vzhled oblasti klienta okna přidáním obsahu pro jednotlivé okno, jako jsou tlačítka, popisky a textová pole.</span><span class="sxs-lookup"><span data-stu-id="8b800-302">You change the appearance of the client area of a window by adding window-specific content to it, such as buttons, labels, and text boxes.</span></span> <span data-ttu-id="8b800-303">Chcete-li nakonfigurovat neklientskou oblast, <xref:System.Windows.Window> poskytuje několik vlastností, které zahrnují <xref:System.Windows.Window.Icon%2A> Nastavení ikony okna a <xref:System.Windows.Window.Title%2A> nastavení jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="8b800-303">To configure the non-client area, <xref:System.Windows.Window> provides several properties, which include <xref:System.Windows.Window.Icon%2A> to set a window's icon and <xref:System.Windows.Window.Title%2A> to set its title.</span></span>  
  
 <span data-ttu-id="8b800-304">Můžete také změnit vzhled a chování ohraničení neklientské oblasti tím, že nakonfigurujete režim změny velikosti okna, styl okna a zda se zobrazí jako tlačítko na panelu úloh plochy.</span><span class="sxs-lookup"><span data-stu-id="8b800-304">You can also change the appearance and behavior of non-client area border by configuring a window's resize mode, window style, and whether it appears as a button in the desktop task bar.</span></span>  

<a name="Resize_Mode"></a>
### <a name="resize-mode"></a><span data-ttu-id="8b800-305">Změnit velikost režimu</span><span class="sxs-lookup"><span data-stu-id="8b800-305">Resize Mode</span></span>  
 <span data-ttu-id="8b800-306">V závislosti na <xref:System.Windows.Window.WindowStyle%2A> vlastnosti můžete určit, jak (a kdy) uživatelé mohou měnit velikost okna.</span><span class="sxs-lookup"><span data-stu-id="8b800-306">Depending on the <xref:System.Windows.Window.WindowStyle%2A> property, you can control how (and if) users can resize the window.</span></span> <span data-ttu-id="8b800-307">Volba stylu okna ovlivňuje, zda může uživatel změnit velikost okna přetažením jeho ohraničení pomocí myši, zda jsou tlačítka **minimalizovat**, **maximalizovat**a **změnit velikost** zobrazena v neklientské oblasti a v případě, že se zobrazí, zda jsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="8b800-307">The choice of window style affects whether a user can resize the window by dragging its border with the mouse, whether the **Minimize**, **Maximize**, and **Resize** buttons appear on the non-client area, and, if they do appear, whether they are enabled.</span></span>  
  
 <span data-ttu-id="8b800-308">Můžete nakonfigurovat, jak se změní velikost okna nastavením jeho <xref:System.Windows.Window.ResizeMode%2A> vlastnosti, což může být jedna z následujících <xref:System.Windows.ResizeMode> hodnot výčtu:</span><span class="sxs-lookup"><span data-stu-id="8b800-308">You can configure how a window resizes by setting its <xref:System.Windows.Window.ResizeMode%2A> property, which can be one of the following <xref:System.Windows.ResizeMode> enumeration values:</span></span>  
  
- <xref:System.Windows.ResizeMode.NoResize>  
  
- <xref:System.Windows.ResizeMode.CanMinimize>  
  
- <span data-ttu-id="8b800-309"><xref:System.Windows.ResizeMode.CanResize>výchozí</span><span class="sxs-lookup"><span data-stu-id="8b800-309"><xref:System.Windows.ResizeMode.CanResize> (default)</span></span>  
  
- <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 <span data-ttu-id="8b800-310">Stejně jako v se <xref:System.Windows.Window.WindowStyle%2A> režim změny velikosti okna pravděpodobně během své životnosti nezmění, což znamená, že je pravděpodobně možné ho nastavit ze [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek.</span><span class="sxs-lookup"><span data-stu-id="8b800-310">As with <xref:System.Windows.Window.WindowStyle%2A>, the resize mode of a window is unlikely to change during its lifetime, which means that you'll most likely set it from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 <span data-ttu-id="8b800-311">Všimněte si, že kontrolu vlastností můžete zjistit, zda je okno maximalizováno, minimalizováno nebo obnoveno <xref:System.Windows.Window.WindowState%2A> .</span><span class="sxs-lookup"><span data-stu-id="8b800-311">Note that you can detect whether a window is maximized, minimized, or restored by inspecting the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="Window_Style"></a>
### <a name="window-style"></a><span data-ttu-id="8b800-312">Styl okna</span><span class="sxs-lookup"><span data-stu-id="8b800-312">Window Style</span></span>  
 <span data-ttu-id="8b800-313">Ohraničení, které je vystaveno mimo klientskou oblast okna, je vhodné pro většinu aplikací.</span><span class="sxs-lookup"><span data-stu-id="8b800-313">The border that is exposed from the non-client area of a window is suitable for most applications.</span></span> <span data-ttu-id="8b800-314">Existují však situace, kdy je třeba zadat různé typy ohraničení, nebo není nutné žádné ohraničení v závislosti na typu okna.</span><span class="sxs-lookup"><span data-stu-id="8b800-314">However, there are circumstances where different types of borders are needed, or no borders are needed at all, depending on the type of window.</span></span>  
  
 <span data-ttu-id="8b800-315">Chcete-li určit, jaký typ ohraničení okno získá, nastavte jeho <xref:System.Windows.Window.WindowStyle%2A> vlastnost pomocí jedné z následujících hodnot <xref:System.Windows.WindowStyle> výčtu:</span><span class="sxs-lookup"><span data-stu-id="8b800-315">To control what type of border a window gets, you set its <xref:System.Windows.Window.WindowStyle%2A> property with one of the following values of the <xref:System.Windows.WindowStyle> enumeration:</span></span>  
  
- <xref:System.Windows.WindowStyle.None>  
  
- <span data-ttu-id="8b800-316"><xref:System.Windows.WindowStyle.SingleBorderWindow>výchozí</span><span class="sxs-lookup"><span data-stu-id="8b800-316"><xref:System.Windows.WindowStyle.SingleBorderWindow> (default)</span></span>  
  
- <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
- <xref:System.Windows.WindowStyle.ToolWindow>  
  
 <span data-ttu-id="8b800-317">Efekt těchto stylů oken je znázorněn na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="8b800-317">The effect of these window styles are illustrated in the following figure:</span></span>  
  
 ![Ilustrace stylů ohraničení okna](./media/wpf-windows-overview/window-border-styles.png)  
  
 <span data-ttu-id="8b800-319">Můžete nastavit <xref:System.Windows.Window.WindowStyle%2A> pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značky nebo kódu; vzhledem k tomu, že se po celou dobu životnosti okna pravděpodobně nemění, je pravděpodobné, že ho budete konfigurovat pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek.</span><span class="sxs-lookup"><span data-stu-id="8b800-319">You can set <xref:System.Windows.Window.WindowStyle%2A> using either [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup or code; because it is unlikely to change during the lifetime of a window, you will most likely configure it using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a><span data-ttu-id="8b800-320">Styl neobdélníkového okna</span><span class="sxs-lookup"><span data-stu-id="8b800-320">Non-Rectangular Window Style</span></span>  
 <span data-ttu-id="8b800-321">Existují také situace, kdy styly ohraničení, které umožňují, nejsou <xref:System.Windows.Window.WindowStyle%2A> dostačující.</span><span class="sxs-lookup"><span data-stu-id="8b800-321">There are also situations where the border styles that <xref:System.Windows.Window.WindowStyle%2A> allows you to have are not sufficient.</span></span> <span data-ttu-id="8b800-322">Například můžete chtít vytvořit aplikaci s neobdélníkovým ohraničením, například Microsoft Windows Media Player používá.</span><span class="sxs-lookup"><span data-stu-id="8b800-322">For example, you may want to create an application with a non-rectangular border, like Microsoft Windows Media Player uses.</span></span>  
  
 <span data-ttu-id="8b800-323">Představte si například okno bublinového slova, které vidíte na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="8b800-323">For example, consider the speech bubble window shown in the following figure:</span></span>  
  
 ![Okno bublinového slova, které říká, že se má přetáhnout](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 <span data-ttu-id="8b800-325">Tento typ okna lze vytvořit nastavením <xref:System.Windows.Window.WindowStyle%2A> vlastnosti na <xref:System.Windows.WindowStyle.None> a pomocí speciální podpory, která <xref:System.Windows.Window> má transparentnost.</span><span class="sxs-lookup"><span data-stu-id="8b800-325">This type of window can be created by setting the <xref:System.Windows.Window.WindowStyle%2A> property to <xref:System.Windows.WindowStyle.None>, and by using special support that <xref:System.Windows.Window> has for transparency.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 <span data-ttu-id="8b800-326">Tato kombinace hodnot instruuje okno tak, aby bylo zcela transparentní.</span><span class="sxs-lookup"><span data-stu-id="8b800-326">This combination of values instructs the window to render completely transparent.</span></span> <span data-ttu-id="8b800-327">V tomto stavu nelze použít doplňky neklientských oblastí okna (tlačítka Zavřít nabídky, minimalizovat, maximalizovat a obnovit atd.).</span><span class="sxs-lookup"><span data-stu-id="8b800-327">In this state, the window's non-client area adornments (the Close menu, Minimize, Maximize, and Restore buttons, and so on) cannot be used.</span></span> <span data-ttu-id="8b800-328">V důsledku toho je třeba zadat vlastní.</span><span class="sxs-lookup"><span data-stu-id="8b800-328">Consequently, you need to provide your own.</span></span>  
  
<a name="Task_Bar_Presence"></a>
### <a name="task-bar-presence"></a><span data-ttu-id="8b800-329">Přítomnost panelu úloh</span><span class="sxs-lookup"><span data-stu-id="8b800-329">Task Bar Presence</span></span>  

<span data-ttu-id="8b800-330">Výchozí vzhled okna obsahuje tlačítko na hlavním panelu, podobně jako na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="8b800-330">The default appearance of a window includes a taskbar button, like the one shown in the following figure:</span></span>

 ![Snímek obrazovky, který zobrazuje okno s tlačítkem hlavního panelu.](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 <span data-ttu-id="8b800-332">Některé typy oken nemají tlačítko na hlavním panelu, například pole se zprávami a dialogová okna (viz dialogová [okna Přehled](dialog-boxes-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="8b800-332">Some types of windows don't have a task bar button, such as message boxes and dialog boxes (see [Dialog Boxes Overview](dialog-boxes-overview.md)).</span></span> <span data-ttu-id="8b800-333">Nastavením <xref:System.Windows.Window.ShowInTaskbar%2A> vlastnosti ( `true` ve výchozím nastavení) můžete určit, zda je zobrazeno tlačítko na panelu úloh okna.</span><span class="sxs-lookup"><span data-stu-id="8b800-333">You can control whether the task bar button for a window is shown by setting the <xref:System.Windows.Window.ShowInTaskbar%2A> property (`true` by default).</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>
## <a name="security-considerations"></a><span data-ttu-id="8b800-334">Aspekty zabezpečení</span><span class="sxs-lookup"><span data-stu-id="8b800-334">Security Considerations</span></span>  
 <span data-ttu-id="8b800-335"><xref:System.Windows.Window>vyžaduje, `UnmanagedCode` aby se vytvořila instance oprávnění zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8b800-335"><xref:System.Windows.Window> requires `UnmanagedCode` security permission to be instantiated.</span></span> <span data-ttu-id="8b800-336">Pro aplikace nainstalované a spouštěné z místního počítače spadá do sady oprávnění udělených aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8b800-336">For applications installed on and launched from the local machine, this falls within the set of permissions that are granted to the application.</span></span>  
  
 <span data-ttu-id="8b800-337">To však spadá mimo sadu oprávnění udělených aplikacím, které jsou spouštěny z Internetu nebo místního intranetu pomocí technologie ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="8b800-337">However, this falls outside the set of permissions granted to applications that are launched from the Internet or Local intranet zone using ClickOnce.</span></span> <span data-ttu-id="8b800-338">V důsledku toho se uživatelům zobrazí upozornění zabezpečení ClickOnce a bude muset zvýšit úroveň oprávnění pro aplikaci na úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="8b800-338">Consequently, users will receive a ClickOnce security warning and will need to elevate the permission set for the application to full trust.</span></span>  
  
 <span data-ttu-id="8b800-339">Aplikace XBAP navíc nemůžou ve výchozím nastavení zobrazovat okna nebo dialogová okna.</span><span class="sxs-lookup"><span data-stu-id="8b800-339">Additionally, XBAPs cannot show windows or dialog boxes by default.</span></span> <span data-ttu-id="8b800-340">Diskuzi o zabezpečení samostatných aplikací najdete v tématu [strategie zabezpečení WPF – zabezpečení platformy](../wpf-security-strategy-platform-security.md).</span><span class="sxs-lookup"><span data-stu-id="8b800-340">For a discussion on standalone application security considerations, see [WPF Security Strategy - Platform Security](../wpf-security-strategy-platform-security.md).</span></span>  
  
<a name="Other_Types_of_Windows"></a>
## <a name="other-types-of-windows"></a><span data-ttu-id="8b800-341">Jiné typy Windows</span><span class="sxs-lookup"><span data-stu-id="8b800-341">Other Types of Windows</span></span>  
 <span data-ttu-id="8b800-342"><xref:System.Windows.Navigation.NavigationWindow>je okno, které je navrženo pro hostování obsahu naviguje.</span><span class="sxs-lookup"><span data-stu-id="8b800-342"><xref:System.Windows.Navigation.NavigationWindow> is a window that is designed to host navigable content.</span></span> <span data-ttu-id="8b800-343">Další informace najdete v tématu [Přehled navigace](navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8b800-343">For more information, see [Navigation Overview](navigation-overview.md)).</span></span>  
  
 <span data-ttu-id="8b800-344">Dialogová okna jsou okna, která se často používají k získání informací z uživatele k dokončení funkce.</span><span class="sxs-lookup"><span data-stu-id="8b800-344">Dialog boxes are windows that are often used to gather information from a user to complete a function.</span></span> <span data-ttu-id="8b800-345">Například když chce uživatel otevřít soubor, dialogové okno **otevřít soubor** se obvykle zobrazí v aplikaci k získání názvu souboru od uživatele.</span><span class="sxs-lookup"><span data-stu-id="8b800-345">For example, when a user wants to open a file, the **Open File** dialog box is usually displayed by an application to get the file name from the user.</span></span> <span data-ttu-id="8b800-346">Další informace najdete v tématu [Přehled dialogových oken](dialog-boxes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8b800-346">For more information, see [Dialog Boxes Overview](dialog-boxes-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b800-347">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b800-347">See also</span></span>

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [<span data-ttu-id="8b800-348">Přehled dialogových oken</span><span class="sxs-lookup"><span data-stu-id="8b800-348">Dialog Boxes Overview</span></span>](dialog-boxes-overview.md)
- [<span data-ttu-id="8b800-349">Sestavení aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="8b800-349">Building a WPF Application</span></span>](building-a-wpf-application-wpf.md)
