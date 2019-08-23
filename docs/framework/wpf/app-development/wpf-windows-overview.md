---
title: Přehled WPF Windows
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
ms.openlocfilehash: 16f4155cefea20868185febb3d2a566dc1524cc4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956275"
---
# <a name="wpf-windows-overview"></a><span data-ttu-id="9c71c-102">Přehled WPF Windows</span><span class="sxs-lookup"><span data-stu-id="9c71c-102">WPF Windows Overview</span></span>
<span data-ttu-id="9c71c-103">Uživatelé pracují se samostatnými aplikacemi Windows Presentation Foundation (WPF) prostřednictvím systému Windows.</span><span class="sxs-lookup"><span data-stu-id="9c71c-103">Users interact with Windows Presentation Foundation (WPF) standalone applications through windows.</span></span> <span data-ttu-id="9c71c-104">Hlavním účelem okna je hostování obsahu, který vizualizuje data a umožňuje uživatelům pracovat s daty.</span><span class="sxs-lookup"><span data-stu-id="9c71c-104">The primary purpose of a window is to host content that visualizes data and enables users to interact with data.</span></span> <span data-ttu-id="9c71c-105">Samostatné [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace poskytují vlastní okna <xref:System.Windows.Window> pomocí třídy.</span><span class="sxs-lookup"><span data-stu-id="9c71c-105">Standalone [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications provide their own windows by using the <xref:System.Windows.Window> class.</span></span> <span data-ttu-id="9c71c-106">V tomto tématu <xref:System.Windows.Window> se seznámíte se základy vytváření a správy oken v samostatných aplikacích.</span><span class="sxs-lookup"><span data-stu-id="9c71c-106">This topic introduces <xref:System.Windows.Window> before covering the fundamentals of creating and managing windows in standalone applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9c71c-107">Aplikace hostované [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] v prohlížeči, včetně [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] a volné [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] stránky, neposkytují vlastní okna.</span><span class="sxs-lookup"><span data-stu-id="9c71c-107">Browser-hosted [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications, including [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] and loose [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pages, don't provide their own windows.</span></span> <span data-ttu-id="9c71c-108">Místo toho jsou hostovány ve Windows, poskytovaném aplikací Windows Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="9c71c-108">Instead, they are hosted in windows provided by Windows Internet Explorer.</span></span> <span data-ttu-id="9c71c-109">Viz téma [Přehled aplikací prohlížeče WPF XAML](wpf-xaml-browser-applications-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9c71c-109">See [WPF XAML Browser Applications Overview](wpf-xaml-browser-applications-overview.md).</span></span>  

<a name="TheWindowClass"></a>   
## <a name="the-window-class"></a><span data-ttu-id="9c71c-110">Třída okna</span><span class="sxs-lookup"><span data-stu-id="9c71c-110">The Window Class</span></span>  
 <span data-ttu-id="9c71c-111">Následující obrázek znázorňuje prvky části okna:</span><span class="sxs-lookup"><span data-stu-id="9c71c-111">The following figure illustrates the constituent parts of a window:</span></span>  
  
 ![Snímek obrazovky zobrazující prvky okna](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 <span data-ttu-id="9c71c-113">Okno je rozděleno do dvou oblastí: mimo klientské a klientské oblasti.</span><span class="sxs-lookup"><span data-stu-id="9c71c-113">A window is divided into two areas: the non-client area and client area.</span></span>  
  
 <span data-ttu-id="9c71c-114">Neklientská *oblast* okna je implementována nástrojem [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] a zahrnuje části okna, která jsou společná pro většinu oken, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="9c71c-114">The *non-client area* of a window is implemented by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] and includes the parts of a window that are common to most windows, including the following:</span></span>  
  
- <span data-ttu-id="9c71c-115">Ohraničení.</span><span class="sxs-lookup"><span data-stu-id="9c71c-115">A border.</span></span>  
  
- <span data-ttu-id="9c71c-116">Záhlaví.</span><span class="sxs-lookup"><span data-stu-id="9c71c-116">A title bar.</span></span>  
  
- <span data-ttu-id="9c71c-117">Ikona.</span><span class="sxs-lookup"><span data-stu-id="9c71c-117">An icon.</span></span>  
  
- <span data-ttu-id="9c71c-118">Tlačítka minimalizovat, maximalizovat a obnovit.</span><span class="sxs-lookup"><span data-stu-id="9c71c-118">Minimize, Maximize, and Restore buttons.</span></span>  
  
- <span data-ttu-id="9c71c-119">Tlačítko Zavřít</span><span class="sxs-lookup"><span data-stu-id="9c71c-119">A Close button.</span></span>  
  
- <span data-ttu-id="9c71c-120">Systémová nabídka s položkami nabídky, které uživatelům umožňují minimalizovat, maximalizovat, obnovit, přesunout, změnit velikost a zavřít okno.</span><span class="sxs-lookup"><span data-stu-id="9c71c-120">A System menu with menu items that allow users to minimize, maximize, restore, move, resize, and close a window.</span></span>  
  
 <span data-ttu-id="9c71c-121">*Klientská oblast* okna je oblast v neklientské oblasti okna, kterou vývojáři používají k přidání obsahu specifického pro aplikaci, jako jsou například panely nabídek, panely nástrojů a ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="9c71c-121">The *client area* of a window is the area within a window's non-client area and is used by developers to add application-specific content, such as menu bars, tool bars, and controls.</span></span>  
  
 <span data-ttu-id="9c71c-122">V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]systému je okno zapouzdřené <xref:System.Windows.Window> třídou, kterou použijete k provedení následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="9c71c-122">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], a window is encapsulated by the <xref:System.Windows.Window> class that you use to do the following:</span></span>  
  
- <span data-ttu-id="9c71c-123">Zobrazí okno.</span><span class="sxs-lookup"><span data-stu-id="9c71c-123">Display a window.</span></span>  
  
- <span data-ttu-id="9c71c-124">Nakonfigurujte velikost, umístění a vzhled okna.</span><span class="sxs-lookup"><span data-stu-id="9c71c-124">Configure the size, position, and appearance of a window.</span></span>  
  
- <span data-ttu-id="9c71c-125">Hostování obsahu specifického pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9c71c-125">Host application-specific content.</span></span>  
  
- <span data-ttu-id="9c71c-126">Umožňuje spravovat dobu života okna.</span><span class="sxs-lookup"><span data-stu-id="9c71c-126">Manage the lifetime of a window.</span></span>  
  
<a name="DefiningAWindow"></a>   
## <a name="implementing-a-window"></a><span data-ttu-id="9c71c-127">Implementace okna</span><span class="sxs-lookup"><span data-stu-id="9c71c-127">Implementing a Window</span></span>  
 <span data-ttu-id="9c71c-128">Implementace typického okna zahrnuje vzhled i chování, kde *vzhled* definuje, jak okno vypadá uživatelům a *chování* definuje způsob, jakým okno funguje, jak se s ním uživatelé budou pracovat.</span><span class="sxs-lookup"><span data-stu-id="9c71c-128">The implementation of a typical window comprises both appearance and behavior, where *appearance* defines how a window looks to users and *behavior* defines the way a window functions as users interact with it.</span></span> <span data-ttu-id="9c71c-129">V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]aplikaci můžete implementovat vzhled a chování okna pomocí kódu nebo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značky.</span><span class="sxs-lookup"><span data-stu-id="9c71c-129">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], you can implement the appearance and behavior of a window using either code or [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 <span data-ttu-id="9c71c-130">Obecně se však vzhled okna implementuje pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek a jeho chování je implementováno pomocí kódu na pozadí, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9c71c-130">In general, however, the appearance of a window is implemented using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and its behavior is implemented using code-behind, as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 <span data-ttu-id="9c71c-131">Chcete-li [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] povolit spolupráci souboru značek a souboru s kódem na pozadí, jsou vyžadovány následující:</span><span class="sxs-lookup"><span data-stu-id="9c71c-131">To enable a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup file and code-behind file to work together, the following are required:</span></span>  
  
- <span data-ttu-id="9c71c-132">V kódu `Window` musí element `x:Class` obsahovat atribut.</span><span class="sxs-lookup"><span data-stu-id="9c71c-132">In markup, the `Window` element must include the `x:Class` attribute.</span></span> <span data-ttu-id="9c71c-133">Když je `x:Class` aplikace sestavena, existence v souboru označení způsobí, že nástroj Microsoft Build Engine (MSBuild) `partial` vytvoří třídu, která je odvozena z <xref:System.Windows.Window> a `x:Class` má název, který je určen atributem.</span><span class="sxs-lookup"><span data-stu-id="9c71c-133">When the application is built, the existence of `x:Class` in the markup file causes Microsoft build engine (MSBuild) to create a `partial` class that derives from <xref:System.Windows.Window> and has the name that is specified by the `x:Class` attribute.</span></span> <span data-ttu-id="9c71c-134">To vyžaduje přidání [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] deklarace oboru názvů [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pro schéma ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).</span><span class="sxs-lookup"><span data-stu-id="9c71c-134">This requires the addition of an [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace declaration for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schema ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).</span></span> <span data-ttu-id="9c71c-135">Vygenerovaná `partial` třída `InitializeComponent` implementuje metodu, která je volána k registraci událostí a nastavení vlastností, které jsou implementovány v označení.</span><span class="sxs-lookup"><span data-stu-id="9c71c-135">The generated `partial` class implements the `InitializeComponent` method, which is called to register the events and set the properties that are implemented in markup.</span></span>  
  
- <span data-ttu-id="9c71c-136">V kódu na pozadí třída musí být `partial` třída se stejným názvem, který je určen `x:Class` atributem v označení a musí odvozovat z <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="9c71c-136">In code-behind, the class must be a `partial` class with the same name that is specified by the `x:Class` attribute in markup, and it must derive from <xref:System.Windows.Window>.</span></span> <span data-ttu-id="9c71c-137">To umožňuje, aby soubor s kódem na pozadí byl přidružen `partial` ke třídě, která je generována pro soubor označení při sestavení aplikace (viz [Vytvoření aplikace WPF](building-a-wpf-application-wpf.md)).</span><span class="sxs-lookup"><span data-stu-id="9c71c-137">This allows the code-behind file to be associated with the `partial` class that is generated for the markup file when the application is built (see [Building a WPF Application](building-a-wpf-application-wpf.md)).</span></span>  
  
- <span data-ttu-id="9c71c-138">V kódu na pozadí <xref:System.Windows.Window> třída musí implementovat konstruktor, který `InitializeComponent` volá metodu.</span><span class="sxs-lookup"><span data-stu-id="9c71c-138">In code-behind, the <xref:System.Windows.Window> class must implement a constructor that calls the `InitializeComponent` method.</span></span> <span data-ttu-id="9c71c-139">`InitializeComponent`je implementována třídou vygenerovanou `partial` souborem označení pro registraci událostí a nastavení vlastností, které jsou definovány v označení.</span><span class="sxs-lookup"><span data-stu-id="9c71c-139">`InitializeComponent` is implemented by the markup file's generated `partial` class to register events and set properties that are defined in markup.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9c71c-140">Když do projektu přidáte nový <xref:System.Windows.Window> pomocí [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], <xref:System.Windows.Window> je implementováno pomocí kódu a kódu na pozadí a zahrnuje nezbytnou konfiguraci pro vytvoření přidružení mezi značkami a soubory kódu na pozadí jako popsané tady.</span><span class="sxs-lookup"><span data-stu-id="9c71c-140">When you add a new <xref:System.Windows.Window> to your project by using [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], the <xref:System.Windows.Window> is implemented using both markup and code-behind, and includes the necessary configuration to create the association between the markup and code-behind files as described here.</span></span>  
  
 <span data-ttu-id="9c71c-141">S touto konfigurací se můžete soustředit na definování vzhledu okna v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kódu a implementaci jeho chování v kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="9c71c-141">With this configuration in place, you can focus on defining the appearance of the window in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and implementing its behavior in code-behind.</span></span> <span data-ttu-id="9c71c-142">Následující příklad ukazuje okno s tlačítkem, implementované v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kódu a obslužná rutina události pro <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost tlačítka, implementovaná v kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="9c71c-142">The following example shows a window with a button, implemented in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and an event handler for the button's <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, implemented in code-behind.</span></span>  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>   
## <a name="configuring-a-window-definition-for-msbuild"></a><span data-ttu-id="9c71c-143">Konfigurace definice okna pro MSBuild</span><span class="sxs-lookup"><span data-stu-id="9c71c-143">Configuring a Window Definition for MSBuild</span></span>  
 <span data-ttu-id="9c71c-144">Způsob implementace vašeho okna určuje, jak je nakonfigurován pro nástroj MSBuild.</span><span class="sxs-lookup"><span data-stu-id="9c71c-144">How you implement your window determines how it is configured for MSBuild.</span></span> <span data-ttu-id="9c71c-145">Pro okno, které je definováno pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek a kódu na pozadí:</span><span class="sxs-lookup"><span data-stu-id="9c71c-145">For a window that is defined using both [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind:</span></span>  
  
- <span data-ttu-id="9c71c-146">Soubory značek XAML jsou konfigurovány jako `Page` položky MSBuild.</span><span class="sxs-lookup"><span data-stu-id="9c71c-146">XAML markup files are configured as MSBuild `Page` items.</span></span>  
  
- <span data-ttu-id="9c71c-147">Soubory kódu na pozadí jsou konfigurovány jako `Compile` položky nástroje MSBuild.</span><span class="sxs-lookup"><span data-stu-id="9c71c-147">Code-behind files are configured as MSBuild `Compile` items.</span></span>  
  
 <span data-ttu-id="9c71c-148">Tento soubor je zobrazen v následujícím souboru projektu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="9c71c-148">This is shown in the following MSBuild project file.</span></span>  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 <span data-ttu-id="9c71c-149">Informace o vytváření [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikací naleznete v tématu sestavování [aplikace WPF](building-a-wpf-application-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="9c71c-149">For information about building [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications, see [Building a WPF Application](building-a-wpf-application-wpf.md).</span></span>  
  
<a name="WindowLifetime"></a>   
## <a name="window-lifetime"></a><span data-ttu-id="9c71c-150">Doba života okna</span><span class="sxs-lookup"><span data-stu-id="9c71c-150">Window Lifetime</span></span>  
 <span data-ttu-id="9c71c-151">Stejně jako u libovolné třídy má okno životnost, která začíná při prvním vytvoření instance, po jejím otevření, aktivaci a deaktivaci a nakonec uzavření.</span><span class="sxs-lookup"><span data-stu-id="9c71c-151">As with any class, a window has a lifetime that begins when it is first instantiated, after which it is opened, activated and deactivated, and eventually closed.</span></span>  

<a name="Opening_a_Window"></a>   
### <a name="opening-a-window"></a><span data-ttu-id="9c71c-152">Otevření okna</span><span class="sxs-lookup"><span data-stu-id="9c71c-152">Opening a Window</span></span>  
 <span data-ttu-id="9c71c-153">Chcete-li otevřít okno, nejprve vytvořte jeho instanci, která je znázorněna v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9c71c-153">To open a window, you first create an instance of it, which is demonstrated in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 <span data-ttu-id="9c71c-154">V tomto příkladu `MarkupAndCodeBehindWindow` je vytvořena instance při spuštění aplikace, což nastane <xref:System.Windows.Application.Startup> při vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="9c71c-154">In this example, the `MarkupAndCodeBehindWindow` is instantiated when the application starts, which occurs when the <xref:System.Windows.Application.Startup> event is raised.</span></span>  
  
 <span data-ttu-id="9c71c-155">Při vytvoření instance okna je odkaz na něj automaticky přidán do seznamu oken, který je spravován <xref:System.Windows.Application> objektem (viz <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="9c71c-155">When a window is instantiated, a reference to it is automatically added to a list of windows that is managed by the <xref:System.Windows.Application> object (see <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>).</span></span> <span data-ttu-id="9c71c-156">Kromě toho první okno, které má být vytvořena instance, je ve výchozím nastavení nastaveno <xref:System.Windows.Application> jako hlavní okno aplikace (viz <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="9c71c-156">Additionally, the first window to be instantiated is, by default, set by <xref:System.Windows.Application> as the main application window (see <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="9c71c-157">Okno je nakonec otevřeno voláním <xref:System.Windows.Window.Show%2A> metody. výsledek je znázorněn na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="9c71c-157">The window is finally opened by calling the <xref:System.Windows.Window.Show%2A> method; the result is shown in the following figure.</span></span>  
  
 ![Okno otevřené voláním okna. show](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 <span data-ttu-id="9c71c-159">Okno otevřené voláním <xref:System.Windows.Window.Show%2A> je nemodální okno, což znamená, že aplikace funguje v režimu, který umožňuje uživatelům aktivovat další okna ve stejné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9c71c-159">A window that is opened by calling <xref:System.Windows.Window.Show%2A> is a modeless window, which means that the application operates in a mode that allows users to activate other windows in the same application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9c71c-160"><xref:System.Windows.Window.ShowDialog%2A>je volána pro otevření oken, například dialogová okna v modálním formátu.</span><span class="sxs-lookup"><span data-stu-id="9c71c-160"><xref:System.Windows.Window.ShowDialog%2A> is called to open windows such as dialog boxes modally.</span></span> <span data-ttu-id="9c71c-161">Další informace najdete v tématu Přehled dialogových [oken](dialog-boxes-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="9c71c-161">See [Dialog Boxes Overview](dialog-boxes-overview.md) for more information.</span></span>  
  
 <span data-ttu-id="9c71c-162">Když <xref:System.Windows.Window.Show%2A> je volána, okno provede inicializační práci předtím, než se zobrazí, aby se navázala infrastruktura, která umožňuje přijímat uživatelský vstup.</span><span class="sxs-lookup"><span data-stu-id="9c71c-162">When <xref:System.Windows.Window.Show%2A> is called, a window performs initialization work before it is shown to establish infrastructure that allows it to receive user input.</span></span> <span data-ttu-id="9c71c-163">Po inicializaci <xref:System.Windows.Window.SourceInitialized> okna se událost vyvolá a zobrazí se okno.</span><span class="sxs-lookup"><span data-stu-id="9c71c-163">When the window is initialized, the <xref:System.Windows.Window.SourceInitialized> event is raised and the window is shown.</span></span>  
  
 <span data-ttu-id="9c71c-164">Jako zástupce <xref:System.Windows.Application.StartupUri%2A> lze nastavit, aby určovalo první okno, které se automaticky otevře při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="9c71c-164">As a shortcut, <xref:System.Windows.Application.StartupUri%2A> can be set to specify the first window that is opened automatically when an application starts.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 <span data-ttu-id="9c71c-165">Po spuštění aplikace je okno určené hodnotou <xref:System.Windows.Application.StartupUri%2A> otevřeno nemodální. interně je okno otevřeno voláním jeho <xref:System.Windows.Window.Show%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9c71c-165">When the application starts, the window specified by the value of <xref:System.Windows.Application.StartupUri%2A> is opened modelessly; internally, the window is opened by calling its <xref:System.Windows.Window.Show%2A> method.</span></span>  
  
<a name="Ownership"></a>   
#### <a name="window-ownership"></a><span data-ttu-id="9c71c-166">Vlastnictví okna</span><span class="sxs-lookup"><span data-stu-id="9c71c-166">Window Ownership</span></span>  
 <span data-ttu-id="9c71c-167">Okno, které je otevřeno pomocí <xref:System.Windows.Window.Show%2A> metody, nemá implicitní relaci s oknem, který ho vytvořil. uživatelé mohou pracovat s některým z oken nezávisle na sobě, což znamená, že jedno okno může provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="9c71c-167">A window that is opened by using the <xref:System.Windows.Window.Show%2A> method does not have an implicit relationship with the window that created it; users can interact with either window independently of the other, which means that either window can do the following:</span></span>  
  
- <span data-ttu-id="9c71c-168">Zakrytí druhé (Pokud má <xref:System.Windows.Window.Topmost%2A> jedna z oken `true`nastavenou vlastnost).</span><span class="sxs-lookup"><span data-stu-id="9c71c-168">Cover the other (unless one of the windows has its <xref:System.Windows.Window.Topmost%2A> property set to `true`).</span></span>  
  
- <span data-ttu-id="9c71c-169">Minimalizujte, maximalizujete a obnovíte, aniž by to ovlivnilo druhý.</span><span class="sxs-lookup"><span data-stu-id="9c71c-169">Be minimized, maximized, and restored without affecting the other.</span></span>  
  
 <span data-ttu-id="9c71c-170">Některá okna vyžadují relaci s oknem, který je otevírá.</span><span class="sxs-lookup"><span data-stu-id="9c71c-170">Some windows require a relationship with the window that opens them.</span></span> <span data-ttu-id="9c71c-171">Například aplikace integrovaného vývojového prostředí (IDE) může otevřít okna vlastností a nástrojů, jejichž typické chování je pokrýt okno, které je vytvoří.</span><span class="sxs-lookup"><span data-stu-id="9c71c-171">For example, an Integrated Development Environment (IDE) application may open property windows and tool windows whose typical behavior is to cover the window that creates them.</span></span> <span data-ttu-id="9c71c-172">Kromě toho by tato okna měla vždycky zavřít, minimalizovat, maximalizovat a obnovit ve vzájemné součinnosti s oknem, který je vytvořil.</span><span class="sxs-lookup"><span data-stu-id="9c71c-172">Furthermore, such windows should always close, minimize, maximize, and restore in concert with the window that created them.</span></span> <span data-ttu-id="9c71c-173">Takový vztah může být vytvořen tak, že jedno okno naplňuje jako jiné a je dosaženo nastavením <xref:System.Windows.Window.Owner%2A> vlastnosti vlastnictví *okna* s odkazem na *okno vlastníka*.</span><span class="sxs-lookup"><span data-stu-id="9c71c-173">Such a relationship can be established by making one window *own* another, and is achieved by setting the <xref:System.Windows.Window.Owner%2A> property of the *owned window* with a reference to the *owner window*.</span></span> <span data-ttu-id="9c71c-174">To je ukázáno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9c71c-174">This is shown in the following example.</span></span>  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 <span data-ttu-id="9c71c-175">Po navázání vlastnictví:</span><span class="sxs-lookup"><span data-stu-id="9c71c-175">After ownership is established:</span></span>  
  
- <span data-ttu-id="9c71c-176">Vlastněné okno může odkazovat na své nadřazené okno kontrolou hodnoty jeho <xref:System.Windows.Window.Owner%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9c71c-176">The owned window can reference its owner window by inspecting the value of its <xref:System.Windows.Window.Owner%2A> property.</span></span>  
  
- <span data-ttu-id="9c71c-177">Okno vlastník může zjistit, že je v něm vlastní systém Windows, a to tak, <xref:System.Windows.Window.OwnedWindows%2A> že zkontroluje hodnotu jeho vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9c71c-177">The owner window can discover all the windows it owns by inspecting the value of its <xref:System.Windows.Window.OwnedWindows%2A> property.</span></span>  
  
<a name="Preventing"></a>   
#### <a name="preventing-window-activation"></a><span data-ttu-id="9c71c-178">Prevence aktivace okna</span><span class="sxs-lookup"><span data-stu-id="9c71c-178">Preventing Window Activation</span></span>  
 <span data-ttu-id="9c71c-179">Existují situace, kdy by systém Windows neměl být aktivovaný, pokud je zobrazený, například okna konverzace aplikace ve stylu kurýrní služby nebo okna oznámení e-mailové aplikace.</span><span class="sxs-lookup"><span data-stu-id="9c71c-179">There are scenarios where windows should not be activated when shown, such as conversation windows of an Internet messenger-style application or notification windows of an email application.</span></span>  
  
 <span data-ttu-id="9c71c-180">Pokud má aplikace okno, které by se nemělo aktivovat, pokud je zobrazeno, můžete nastavit <xref:System.Windows.Window.ShowActivated%2A> jeho vlastnost `false` na hodnotu před <xref:System.Windows.Window.Show%2A> prvním voláním metody.</span><span class="sxs-lookup"><span data-stu-id="9c71c-180">If your application has a window that shouldn't be activated when shown, you can set its <xref:System.Windows.Window.ShowActivated%2A> property to `false` before calling the <xref:System.Windows.Window.Show%2A> method for the first time.</span></span> <span data-ttu-id="9c71c-181">Jako důsledek:</span><span class="sxs-lookup"><span data-stu-id="9c71c-181">As a consequence:</span></span>  
  
- <span data-ttu-id="9c71c-182">Okno není aktivováno.</span><span class="sxs-lookup"><span data-stu-id="9c71c-182">The window is not activated.</span></span>  
  
- <span data-ttu-id="9c71c-183"><xref:System.Windows.Window.Activated> Událost okna není vyvolána.</span><span class="sxs-lookup"><span data-stu-id="9c71c-183">The window's <xref:System.Windows.Window.Activated> event is not raised.</span></span>  
  
- <span data-ttu-id="9c71c-184">Aktuálně aktivované okno zůstane aktivované.</span><span class="sxs-lookup"><span data-stu-id="9c71c-184">The currently activated window remains activated.</span></span>  
  
 <span data-ttu-id="9c71c-185">Okno se aktivuje, ale jakmile ho uživatel aktivuje, klikněte buď na klienta, nebo na oblast mimo klienta.</span><span class="sxs-lookup"><span data-stu-id="9c71c-185">The window will become activated, however, as soon as the user activates it by clicking either the client or non-client area.</span></span> <span data-ttu-id="9c71c-186">V tomto případě:</span><span class="sxs-lookup"><span data-stu-id="9c71c-186">In this case:</span></span>  
  
- <span data-ttu-id="9c71c-187">Okno je aktivováno.</span><span class="sxs-lookup"><span data-stu-id="9c71c-187">The window is activated.</span></span>  
  
- <span data-ttu-id="9c71c-188">Vyvolá se <xref:System.Windows.Window.Activated> událost okna.</span><span class="sxs-lookup"><span data-stu-id="9c71c-188">The window's <xref:System.Windows.Window.Activated> event is raised.</span></span>  
  
- <span data-ttu-id="9c71c-189">Dříve aktivované okno je deaktivováno.</span><span class="sxs-lookup"><span data-stu-id="9c71c-189">The previously activated window is deactivated.</span></span>  
  
- <span data-ttu-id="9c71c-190">V reakci na <xref:System.Windows.Window.Deactivated> akce <xref:System.Windows.Window.Activated> uživatele jsou následně vyvolány okno a události.</span><span class="sxs-lookup"><span data-stu-id="9c71c-190">The window's <xref:System.Windows.Window.Deactivated> and <xref:System.Windows.Window.Activated> events are subsequently raised as expected in response to user actions.</span></span>  
  
<a name="Window_Activation"></a>   
### <a name="window-activation"></a><span data-ttu-id="9c71c-191">Aktivace okna</span><span class="sxs-lookup"><span data-stu-id="9c71c-191">Window Activation</span></span>  
 <span data-ttu-id="9c71c-192">Při prvním otevření okna se zobrazí okno aktivní (Pokud se nezobrazí s <xref:System.Windows.Window.ShowActivated%2A> nastavením na `false`).</span><span class="sxs-lookup"><span data-stu-id="9c71c-192">When a window is first opened, it becomes the active window (unless it is shown with <xref:System.Windows.Window.ShowActivated%2A> set to `false`).</span></span> <span data-ttu-id="9c71c-193">*Aktivní okno* je okno, které aktuálně zachytí vstup uživatele, například tahy kláves a kliknutí myší.</span><span class="sxs-lookup"><span data-stu-id="9c71c-193">The *active window* is the window that is currently capturing user input, such as key strokes and mouse clicks.</span></span> <span data-ttu-id="9c71c-194">Když dojde k aktivaci okna, vyvolá <xref:System.Windows.Window.Activated> událost.</span><span class="sxs-lookup"><span data-stu-id="9c71c-194">When a window becomes active, it raises the <xref:System.Windows.Window.Activated> event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9c71c-195">Při prvním otevření <xref:System.Windows.FrameworkElement.Loaded> okna se události a <xref:System.Windows.Window.ContentRendered> vyvolá až po <xref:System.Windows.Window.Activated> vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="9c71c-195">When a window is first opened, the <xref:System.Windows.FrameworkElement.Loaded> and <xref:System.Windows.Window.ContentRendered> events are raised only after the <xref:System.Windows.Window.Activated> event is raised.</span></span> <span data-ttu-id="9c71c-196">V takovém případě může být okno efektivně považováno za otevřené při <xref:System.Windows.Window.ContentRendered> vyvolání.</span><span class="sxs-lookup"><span data-stu-id="9c71c-196">With this in mind, a window can effectively be considered opened when <xref:System.Windows.Window.ContentRendered> is raised.</span></span>  
  
 <span data-ttu-id="9c71c-197">Po aktivaci okna může uživatel aktivovat jiné okno ve stejné aplikaci nebo aktivovat jinou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9c71c-197">After a window becomes active, a user can activate another window in the same application, or activate another application.</span></span> <span data-ttu-id="9c71c-198">Pokud k tomu dojde, stane se aktuálně aktivní okno deaktivováno a vyvolá <xref:System.Windows.Window.Deactivated> událost.</span><span class="sxs-lookup"><span data-stu-id="9c71c-198">When that happens, the currently active window becomes deactivated and raises the <xref:System.Windows.Window.Deactivated> event.</span></span> <span data-ttu-id="9c71c-199">Podobně když uživatel vybere aktuálně deaktivované okno, okno se znovu aktivuje a <xref:System.Windows.Window.Activated> vyvolá se.</span><span class="sxs-lookup"><span data-stu-id="9c71c-199">Likewise, when the user selects a currently deactivated window, the window becomes active again and <xref:System.Windows.Window.Activated> is raised.</span></span>  
  
 <span data-ttu-id="9c71c-200">Jedním z běžných důvodů, <xref:System.Windows.Window.Activated> jak <xref:System.Windows.Window.Deactivated> zpracovat a zakázat funkce, které lze spustit pouze v případě, že je okno aktivní.</span><span class="sxs-lookup"><span data-stu-id="9c71c-200">One common reason to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> is to enable and disable functionality that can only run when a window is active.</span></span> <span data-ttu-id="9c71c-201">Například některá okna zobrazují interaktivní obsah, který vyžaduje stálý vstup uživatele nebo pozornost, včetně her a přehrávačů videí.</span><span class="sxs-lookup"><span data-stu-id="9c71c-201">For example, some windows display interactive content that requires constant user input or attention, including games and video players.</span></span> <span data-ttu-id="9c71c-202">Následující příklad je zjednodušený přehrávač videa, který ukazuje, jak zpracovat <xref:System.Windows.Window.Activated> a <xref:System.Windows.Window.Deactivated> implementovat toto chování.</span><span class="sxs-lookup"><span data-stu-id="9c71c-202">The following example is a simplified video player that demonstrates how to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> to implement this behavior.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 <span data-ttu-id="9c71c-203">Jiné typy aplikací mohou stále spouštět kód na pozadí, když dojde k deaktivaci okna.</span><span class="sxs-lookup"><span data-stu-id="9c71c-203">Other types of applications may still run code in the background when a window is deactivated.</span></span> <span data-ttu-id="9c71c-204">Například poštovní klient může pokračovat v dotazování poštovního serveru, zatímco uživatel používá jiné aplikace.</span><span class="sxs-lookup"><span data-stu-id="9c71c-204">For example, a mail client may continue polling the mail server while the user is using other applications.</span></span> <span data-ttu-id="9c71c-205">Tyto aplikace často poskytují jiné nebo dodatečné chování při deaktivaci hlavního okna.</span><span class="sxs-lookup"><span data-stu-id="9c71c-205">Applications like these often provide different or additional behavior while the main window is deactivated.</span></span> <span data-ttu-id="9c71c-206">V souvislosti s e-mailovým programem může to znamenat, že by se nová položka pošty přidala do doručené pošty a přidala se ikona oznámení do systémového zásobníku.</span><span class="sxs-lookup"><span data-stu-id="9c71c-206">With respect to the mail program, this may mean both adding the new mail item to the inbox and adding a notification icon to the system tray.</span></span> <span data-ttu-id="9c71c-207">Ikona oznámení musí být zobrazena pouze v případě, že okno pošty není aktivní, což lze určit <xref:System.Windows.Window.IsActive%2A> kontrolou vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9c71c-207">A notification icon need only be displayed when the mail window isn't active, which can be determined by inspecting the <xref:System.Windows.Window.IsActive%2A> property.</span></span>  
  
 <span data-ttu-id="9c71c-208">Pokud je úloha na pozadí dokončena, okno může chtít uživateli upozorňovat na naléhavější voláním <xref:System.Windows.Window.Activate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9c71c-208">If a background task completes, a window may want to notify the user more urgently by calling <xref:System.Windows.Window.Activate%2A> method.</span></span> <span data-ttu-id="9c71c-209">Pokud uživatel pracuje s jinou aplikací aktivovanou, když <xref:System.Windows.Window.Activate%2A> je volána, tlačítko na hlavním panelu bude blikat.</span><span class="sxs-lookup"><span data-stu-id="9c71c-209">If the user is interacting with another application activated when <xref:System.Windows.Window.Activate%2A> is called, the window's taskbar button flashes.</span></span> <span data-ttu-id="9c71c-210">Pokud uživatel spolupracuje s aktuální aplikací, volání <xref:System.Windows.Window.Activate%2A> přepne okno do popředí.</span><span class="sxs-lookup"><span data-stu-id="9c71c-210">If a user is interacting with the current application, calling <xref:System.Windows.Window.Activate%2A> will bring the window to the foreground.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9c71c-211">Můžete zpracovávat aktivaci rozsahu aplikace pomocí <xref:System.Windows.Application.Activated?displayProperty=nameWithType> událostí a. <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9c71c-211">You can handle application-scope activation using the <xref:System.Windows.Application.Activated?displayProperty=nameWithType> and <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> events.</span></span>  
  
<a name="Closing_a_Window"></a>   
### <a name="closing-a-window"></a><span data-ttu-id="9c71c-212">Zavření okna</span><span class="sxs-lookup"><span data-stu-id="9c71c-212">Closing a Window</span></span>  
 <span data-ttu-id="9c71c-213">Životnost okna začíná až do konce, když ho uživatel zavře.</span><span class="sxs-lookup"><span data-stu-id="9c71c-213">The life of a window starts coming to an end when a user closes it.</span></span> <span data-ttu-id="9c71c-214">Okno lze uzavřít pomocí prvků v neklientské oblasti, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="9c71c-214">A window can be closed by using elements in the non-client area, including the following:</span></span>  
  
- <span data-ttu-id="9c71c-215">Položka **Zavřít** v **systémové** nabídce</span><span class="sxs-lookup"><span data-stu-id="9c71c-215">The **Close** item of the **System** menu.</span></span>  
  
- <span data-ttu-id="9c71c-216">Stiskněte kombinaci kláves ALT + F4.</span><span class="sxs-lookup"><span data-stu-id="9c71c-216">Pressing ALT+F4.</span></span>  
  
- <span data-ttu-id="9c71c-217">Stisknutí tlačítka **Zavřít** .</span><span class="sxs-lookup"><span data-stu-id="9c71c-217">Pressing the **Close** button.</span></span>  
  
 <span data-ttu-id="9c71c-218">Do klientské oblasti můžete poskytnout další mechanismy pro zavření okna, běžnější z nich, které zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="9c71c-218">You can provide additional mechanisms to the client area to close a window, the more common of which include the following:</span></span>  
  
- <span data-ttu-id="9c71c-219">Položka **Exit** v nabídce **soubor** , obvykle pro okna hlavní aplikace.</span><span class="sxs-lookup"><span data-stu-id="9c71c-219">An **Exit** item in the **File** menu, typically for main application windows.</span></span>  
  
- <span data-ttu-id="9c71c-220">Položka **Zavřít** v nabídce **soubor** , která se obvykle nachází v sekundárním okně aplikace.</span><span class="sxs-lookup"><span data-stu-id="9c71c-220">A **Close** item in the **File** menu, typically on a secondary application window.</span></span>  
  
- <span data-ttu-id="9c71c-221">Tlačítko **Zrušit** , obvykle v modálním dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="9c71c-221">A **Cancel** button, typically on a modal dialog box.</span></span>  
  
- <span data-ttu-id="9c71c-222">Tlačítko **Zavřít** , obvykle v nemodálním dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="9c71c-222">A **Close** button, typically on a modeless dialog box.</span></span>  
  
 <span data-ttu-id="9c71c-223">Chcete-li zavřít okno v reakci na některý z těchto vlastních mechanismů, je třeba zavolat <xref:System.Windows.Window.Close%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="9c71c-223">To close a window in response to one of these custom mechanisms, you need to call the <xref:System.Windows.Window.Close%2A> method.</span></span> <span data-ttu-id="9c71c-224">Následující příklad implementuje možnost Zavřít okno výběrem možnosti **konec** v nabídce **soubor** .</span><span class="sxs-lookup"><span data-stu-id="9c71c-224">The following example implements the ability to close a window by choosing the **Exit** on the **File** menu.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 <span data-ttu-id="9c71c-225">Po zavření okna vyvolá dvě události: <xref:System.Windows.Window.Closing> a. <xref:System.Windows.Window.Closed></span><span class="sxs-lookup"><span data-stu-id="9c71c-225">When a window closes, it raises two events: <xref:System.Windows.Window.Closing> and <xref:System.Windows.Window.Closed>.</span></span>  
  
 <span data-ttu-id="9c71c-226"><xref:System.Windows.Window.Closing>je aktivována před zavřením okna a poskytuje mechanismus, pomocí kterého lze zabránit zavření okna.</span><span class="sxs-lookup"><span data-stu-id="9c71c-226"><xref:System.Windows.Window.Closing> is raised before the window closes, and it provides a mechanism by which window closure can be prevented.</span></span> <span data-ttu-id="9c71c-227">Jedním z běžných důvodů, jak zabránit zavření okna, je, pokud obsah okna obsahuje upravená data.</span><span class="sxs-lookup"><span data-stu-id="9c71c-227">One common reason to prevent window closure is if window content contains modified data.</span></span> <span data-ttu-id="9c71c-228">V takovém <xref:System.Windows.Window.Closing> případě může být událost zpracována za účelem zjištění, zda jsou data nečistá, a pokud ano, požádejte uživatele, aby buď pokračoval v zavírání okna bez uložení dat, nebo zrušení zavření okna.</span><span class="sxs-lookup"><span data-stu-id="9c71c-228">In this situation, the <xref:System.Windows.Window.Closing> event can be handled to determine whether data is dirty and, if so, to ask the user whether to either continue closing the window without saving the data or to cancel window closure.</span></span> <span data-ttu-id="9c71c-229">Následující příklad ukazuje klíčové aspekty manipulace <xref:System.Windows.Window.Closing>.</span><span class="sxs-lookup"><span data-stu-id="9c71c-229">The following example shows the key aspects of handling <xref:System.Windows.Window.Closing>.</span></span>  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 <span data-ttu-id="9c71c-230"><xref:System.ComponentModel.CancelEventArgs.Cancel%2A> <xref:System.ComponentModel.CancelEventArgs> `Boolean` Obslužná rutina `true` události je předána a, která implementuje vlastnost, která je nastavena na, aby zabránila zavření okna. <xref:System.Windows.Window.Closing></span><span class="sxs-lookup"><span data-stu-id="9c71c-230">The <xref:System.Windows.Window.Closing> event handler is passed a <xref:System.ComponentModel.CancelEventArgs>, which implements the `Boolean`<xref:System.ComponentModel.CancelEventArgs.Cancel%2A> property that you set to `true` to prevent a window from closing.</span></span>  
  
 <span data-ttu-id="9c71c-231">Pokud <xref:System.Windows.Window.Closing> není zpracována nebo je zpracována, ale není zrušeno, okno se zavře.</span><span class="sxs-lookup"><span data-stu-id="9c71c-231">If <xref:System.Windows.Window.Closing> is not handled, or it is handled but not canceled, the window will close.</span></span> <span data-ttu-id="9c71c-232">Těsně před tím, než se okno <xref:System.Windows.Window.Closed> skutečně zavře, se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="9c71c-232">Just before a window actually closes, <xref:System.Windows.Window.Closed> is raised.</span></span> <span data-ttu-id="9c71c-233">V tuto chvíli není možné zabránit zavření okna.</span><span class="sxs-lookup"><span data-stu-id="9c71c-233">At this point, a window cannot be prevented from closing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9c71c-234">Aplikaci lze nakonfigurovat tak, aby se automaticky vypnula při zavření okna hlavní aplikace (viz <xref:System.Windows.Application.MainWindow%2A>) nebo po zavření posledního okna.</span><span class="sxs-lookup"><span data-stu-id="9c71c-234">An application can be configured to shut down automatically when either the main application window closes (see <xref:System.Windows.Application.MainWindow%2A>) or the last window closes.</span></span> <span data-ttu-id="9c71c-235">Podrobnosti najdete v tématu <xref:System.Windows.Application.ShutdownMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="9c71c-235">For details, see <xref:System.Windows.Application.ShutdownMode%2A>.</span></span>  
  
 <span data-ttu-id="9c71c-236">I když může být okno explicitně uzavřeno prostřednictvím mechanismů, které jsou k dispozici v klientských a klientských oblastech, může být okno také implicitně uzavřeno v důsledku chování v jiných částech aplikace nebo Windows, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="9c71c-236">While a window can be explicitly closed through mechanisms provided in the non-client and client areas, a window can also be implicitly closed as a result of behavior in other parts of the application or Windows, including the following:</span></span>  
  
- <span data-ttu-id="9c71c-237">Uživatel se odhlásí nebo vypne v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="9c71c-237">A user logs off or shuts down Windows.</span></span>  
  
- <span data-ttu-id="9c71c-238">Vlastník okna se zavře (viz <xref:System.Windows.Window.Owner%2A>).</span><span class="sxs-lookup"><span data-stu-id="9c71c-238">A window's owner closes (see <xref:System.Windows.Window.Owner%2A>).</span></span>  
  
- <span data-ttu-id="9c71c-239">Hlavní okno aplikace je zavřené a <xref:System.Windows.Application.ShutdownMode%2A> je <xref:System.Windows.ShutdownMode.OnMainWindowClose>.</span><span class="sxs-lookup"><span data-stu-id="9c71c-239">The main application window is closed and <xref:System.Windows.Application.ShutdownMode%2A> is <xref:System.Windows.ShutdownMode.OnMainWindowClose>.</span></span>  
  
- <span data-ttu-id="9c71c-240"><xref:System.Windows.Application.Shutdown%2A>je volána.</span><span class="sxs-lookup"><span data-stu-id="9c71c-240"><xref:System.Windows.Application.Shutdown%2A> is called.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9c71c-241">Po zavření okna nelze znovu otevřít.</span><span class="sxs-lookup"><span data-stu-id="9c71c-241">A window cannot be reopened after it is closed.</span></span>  
  
<a name="Window_Lifetime_Events"></a>   
### <a name="window-lifetime-events"></a><span data-ttu-id="9c71c-242">Události životního cyklu okna</span><span class="sxs-lookup"><span data-stu-id="9c71c-242">Window Lifetime Events</span></span>  
 <span data-ttu-id="9c71c-243">Následující ilustrace znázorňuje sekvenci hlavních událostí v době života okna:</span><span class="sxs-lookup"><span data-stu-id="9c71c-243">The following illustration shows the sequence of the principal events in the lifetime of a window:</span></span>  
  
 ![Diagram, který zobrazuje události v době života okna.](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 <span data-ttu-id="9c71c-245">Následující ilustrace znázorňuje sekvenci hlavních událostí v době životnosti okna, které je zobrazeno bez aktivace (<xref:System.Windows.Window.ShowActivated%2A> je nastaveno na `false` hodnotu před zobrazením okna):</span><span class="sxs-lookup"><span data-stu-id="9c71c-245">The following illustration shows the sequence of the principal events in the lifetime of a window that is shown without activation (<xref:System.Windows.Window.ShowActivated%2A> is set to `false` before the window is shown):</span></span>  
  
 ![Diagram, který zobrazuje události v době života okna bez aktivace.](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>   
## <a name="window-location"></a><span data-ttu-id="9c71c-247">Umístění okna</span><span class="sxs-lookup"><span data-stu-id="9c71c-247">Window Location</span></span>  
 <span data-ttu-id="9c71c-248">Když je okno otevřené, má umístění v rozměrech x a y relativně k ploše.</span><span class="sxs-lookup"><span data-stu-id="9c71c-248">While a window is open, it has a location in the x and y dimensions relative to the desktop.</span></span> <span data-ttu-id="9c71c-249">Toto umístění lze určit <xref:System.Windows.Window.Left%2A> kontrolou vlastností a <xref:System.Windows.Window.Top%2A> v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="9c71c-249">This location can be determined by inspecting the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties, respectively.</span></span> <span data-ttu-id="9c71c-250">Nastavením těchto vlastností lze změnit umístění okna.</span><span class="sxs-lookup"><span data-stu-id="9c71c-250">You can set these properties to change the location of the window.</span></span>  
  
 <span data-ttu-id="9c71c-251">Můžete také zadat počáteční umístění <xref:System.Windows.Window> při prvním zobrazení <xref:System.Windows.Window.WindowStartupLocation%2A> nastavením vlastnosti pomocí jedné z následujících <xref:System.Windows.WindowStartupLocation> hodnot výčtu:</span><span class="sxs-lookup"><span data-stu-id="9c71c-251">You can also specify the initial location of a <xref:System.Windows.Window> when it first appears by setting the <xref:System.Windows.Window.WindowStartupLocation%2A> property with one of the following <xref:System.Windows.WindowStartupLocation> enumeration values:</span></span>  
  
- <span data-ttu-id="9c71c-252"><xref:System.Windows.WindowStartupLocation.CenterOwner>výchozí</span><span class="sxs-lookup"><span data-stu-id="9c71c-252"><xref:System.Windows.WindowStartupLocation.CenterOwner> (default)</span></span>  
  
- <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
- <xref:System.Windows.WindowStartupLocation.Manual>  
  
 <span data-ttu-id="9c71c-253">Pokud je <xref:System.Windows.WindowStartupLocation.Manual>počáteční umístění zadané jako <xref:System.Windows.Window.Left%2A> a vlastnosti a <xref:System.Windows.Window.Top%2A> nejsou nastavené, požádá Windows o <xref:System.Windows.Window> umístění, ve kterém se bude zobrazovat.</span><span class="sxs-lookup"><span data-stu-id="9c71c-253">If the startup location is specified as <xref:System.Windows.WindowStartupLocation.Manual>, and the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties have not been set, <xref:System.Windows.Window> will ask Windows for a location to appear in.</span></span>  
  
<a name="Topmost_Windows_and_Z_Order"></a>   
### <a name="topmost-windows-and-z-order"></a><span data-ttu-id="9c71c-254">V horních oknech a pořadí Z</span><span class="sxs-lookup"><span data-stu-id="9c71c-254">Topmost Windows and Z-Order</span></span>  
 <span data-ttu-id="9c71c-255">Kromě umístění x a y má okno také místo v dimenzi z, které určuje jeho svislou polohu vzhledem k ostatním systémům Windows.</span><span class="sxs-lookup"><span data-stu-id="9c71c-255">Besides having an x and y location, a window also has a location in the z dimension, which determines its vertical position with respect to other windows.</span></span> <span data-ttu-id="9c71c-256">Toto se říká pořadí vykreslování v okně a existují dva typy: normální pořadí vykreslování a nejvyšší pořadí vykreslování.</span><span class="sxs-lookup"><span data-stu-id="9c71c-256">This is known as the window's z-order, and there are two types: normal z-order and topmost z-order.</span></span> <span data-ttu-id="9c71c-257">Umístění okna v *normálním pořadí z* je určeno, zda je aktuálně aktivní nebo ne.</span><span class="sxs-lookup"><span data-stu-id="9c71c-257">The location of a window in the *normal z-order* is determined by whether it is currently active or not.</span></span> <span data-ttu-id="9c71c-258">Ve výchozím nastavení je okno umístěno v normálním pořadí z.</span><span class="sxs-lookup"><span data-stu-id="9c71c-258">By default, a window is located in the normal z-order.</span></span> <span data-ttu-id="9c71c-259">Umístění okna v *horním pořadí z* je také určeno, zda je aktuálně aktivní nebo ne.</span><span class="sxs-lookup"><span data-stu-id="9c71c-259">The location of a window in the *topmost z-order* is also determined by whether it is currently active or not.</span></span> <span data-ttu-id="9c71c-260">Kromě toho Windows v horním pořadí z je vždycky umístěný nad Windows v normálním pořadí z.</span><span class="sxs-lookup"><span data-stu-id="9c71c-260">Furthermore, windows in the topmost z-order are always located above windows in the normal z-order.</span></span> <span data-ttu-id="9c71c-261">Okno je umístěno v horní části pořadí z – nastavením jeho <xref:System.Windows.Window.Topmost%2A> vlastnosti na. `true`</span><span class="sxs-lookup"><span data-stu-id="9c71c-261">A window is located in the topmost z-order by setting its <xref:System.Windows.Window.Topmost%2A> property to `true`.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 <span data-ttu-id="9c71c-262">V rámci každého pořadí z je zobrazeno aktuálně aktivní okno nad všemi ostatními okny ve stejném pořadí z.</span><span class="sxs-lookup"><span data-stu-id="9c71c-262">Within each z-order, the currently active window appears above all other windows in the same z-order.</span></span>  
  
<a name="WindowSize"></a>   
## <a name="window-size"></a><span data-ttu-id="9c71c-263">Velikost okna</span><span class="sxs-lookup"><span data-stu-id="9c71c-263">Window Size</span></span>  
 <span data-ttu-id="9c71c-264">Kromě umístění na ploše má okno velikost, která je určena několika vlastnostmi, včetně různých vlastností šířky a výšky a <xref:System.Windows.Window.SizeToContent%2A>.</span><span class="sxs-lookup"><span data-stu-id="9c71c-264">Besides having a desktop location, a window has a size that is determined by several properties, including the various width and height properties and <xref:System.Windows.Window.SizeToContent%2A>.</span></span>  
  
 <span data-ttu-id="9c71c-265"><xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, a <xref:System.Windows.FrameworkElement.MaxWidth%2A> slouží ke správě rozsahu šířek, které může okno mít během své životnosti a jsou konfigurovány tak, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9c71c-265"><xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.MaxWidth%2A> are used to manage the range of widths that a window can have during its lifetime, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 <span data-ttu-id="9c71c-266">Výška okna je spravována <xref:System.Windows.FrameworkElement.MinHeight%2A>pomocí <xref:System.Windows.FrameworkElement.Height%2A>,, <xref:System.Windows.FrameworkElement.MaxHeight%2A>a, a je konfigurována tak, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9c71c-266">Window height is managed by <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, and <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 <span data-ttu-id="9c71c-267">Vzhledem k tomu, že různé hodnoty šířky a hodnoty výšky určují rozsah, je možné, že šířka a Výška okna s možností změny velikosti budou kdekoli v zadaném rozsahu pro příslušnou dimenzi.</span><span class="sxs-lookup"><span data-stu-id="9c71c-267">Because the various width values and height values each specify a range, it is possible for the width and height of a resizable window to be anywhere within the specified range for the respective dimension.</span></span> <span data-ttu-id="9c71c-268">Chcete-li zjistit aktuální šířku a výšku, <xref:System.Windows.FrameworkElement.ActualWidth%2A> zkontrolujte <xref:System.Windows.FrameworkElement.ActualHeight%2A>a v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="9c71c-268">To detect its current width and height, inspect <xref:System.Windows.FrameworkElement.ActualWidth%2A> and <xref:System.Windows.FrameworkElement.ActualHeight%2A>, respectively.</span></span>  
  
 <span data-ttu-id="9c71c-269">Pokud chcete, aby Šířka a Výška okna měla velikost, která se vejde na velikost obsahu okna, můžete použít <xref:System.Windows.Window.SizeToContent%2A> vlastnost, která má následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="9c71c-269">If you'd like the width and height of your window to have a size that fits to the size of the window's content, you can use the <xref:System.Windows.Window.SizeToContent%2A> property, which has the following values:</span></span>  
  
- <span data-ttu-id="9c71c-270"><xref:System.Windows.SizeToContent.Manual>.</span><span class="sxs-lookup"><span data-stu-id="9c71c-270"><xref:System.Windows.SizeToContent.Manual>.</span></span> <span data-ttu-id="9c71c-271">Žádný efekt (výchozí).</span><span class="sxs-lookup"><span data-stu-id="9c71c-271">No effect (default).</span></span>  
  
- <span data-ttu-id="9c71c-272"><xref:System.Windows.SizeToContent.Width>.</span><span class="sxs-lookup"><span data-stu-id="9c71c-272"><xref:System.Windows.SizeToContent.Width>.</span></span> <span data-ttu-id="9c71c-273">Přizpůsobit šířce obsahu, která má stejný efekt jako nastavení <xref:System.Windows.FrameworkElement.MinWidth%2A> a <xref:System.Windows.FrameworkElement.MaxWidth%2A> na šířku obsahu.</span><span class="sxs-lookup"><span data-stu-id="9c71c-273">Fit to content width, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
- <span data-ttu-id="9c71c-274"><xref:System.Windows.SizeToContent.Height>.</span><span class="sxs-lookup"><span data-stu-id="9c71c-274"><xref:System.Windows.SizeToContent.Height>.</span></span> <span data-ttu-id="9c71c-275">Přizpůsobit výšce obsahu, která má stejný efekt jako nastavení obou <xref:System.Windows.FrameworkElement.MinHeight%2A> i <xref:System.Windows.FrameworkElement.MaxHeight%2A> na výšku obsahu.</span><span class="sxs-lookup"><span data-stu-id="9c71c-275">Fit to content height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content.</span></span>  
  
- <span data-ttu-id="9c71c-276"><xref:System.Windows.SizeToContent.WidthAndHeight>.</span><span class="sxs-lookup"><span data-stu-id="9c71c-276"><xref:System.Windows.SizeToContent.WidthAndHeight>.</span></span> <span data-ttu-id="9c71c-277">Přizpůsobit šířce a výšce obsahu, která má stejný <xref:System.Windows.FrameworkElement.MinHeight%2A> efekt jako nastavení obou <xref:System.Windows.FrameworkElement.MaxHeight%2A> i na výšku <xref:System.Windows.FrameworkElement.MinWidth%2A> obsahu a nastavení <xref:System.Windows.FrameworkElement.MaxWidth%2A> i na šířku obsahu.</span><span class="sxs-lookup"><span data-stu-id="9c71c-277">Fit to content width and height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content, and setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
 <span data-ttu-id="9c71c-278">Následující příklad ukazuje okno, které automaticky přizpůsobí svůj obsah, jak je to možné, vertikálně i vodorovně, pokud je zobrazeno první.</span><span class="sxs-lookup"><span data-stu-id="9c71c-278">The following example shows a window that automatically sizes to fit its content, both vertically and horizontally, when first shown.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 <span data-ttu-id="9c71c-279">Následující příklad ukazuje, jak nastavit <xref:System.Windows.Window.SizeToContent%2A> vlastnost v kódu pro určení, jak se změní velikost okna tak, aby odpovídala jeho obsahu.</span><span class="sxs-lookup"><span data-stu-id="9c71c-279">The following example shows how to set the <xref:System.Windows.Window.SizeToContent%2A> property in code to specify how a window resizes to fit its content    .</span></span>
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>   
## <a name="order-of-precedence-for-sizing-properties"></a><span data-ttu-id="9c71c-280">Pořadí priorit pro vlastnosti velikosti</span><span class="sxs-lookup"><span data-stu-id="9c71c-280">Order of Precedence for Sizing Properties</span></span>  
 <span data-ttu-id="9c71c-281">V podstatě jsou různé vlastnosti velikosti okna kombinovány, aby bylo možné definovat rozsah šířky a výšky okna s možností změny velikosti.</span><span class="sxs-lookup"><span data-stu-id="9c71c-281">Essentially, the various sizes properties of a window combine to define the range of width and height for a resizable window.</span></span> <span data-ttu-id="9c71c-282">Chcete-li zajistit zachování platného rozsahu, <xref:System.Windows.Window> vyhodnotí hodnoty vlastností velikosti pomocí následujících pořadí priorit.</span><span class="sxs-lookup"><span data-stu-id="9c71c-282">To ensure a valid range is maintained, <xref:System.Windows.Window> evaluates the values of the size properties using the following orders of precedence.</span></span>  
  
 <span data-ttu-id="9c71c-283">**Pro vlastnosti výšky:**</span><span class="sxs-lookup"><span data-stu-id="9c71c-283">**For Height Properties:**</span></span>  
  
1. <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="9c71c-284">**Pro vlastnosti šířky:**</span><span class="sxs-lookup"><span data-stu-id="9c71c-284">**For Width Properties:**</span></span>  
  
1. <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="9c71c-285">Pořadí priorit může také určit velikost okna v případě maximalizace, které je spravováno pomocí <xref:System.Windows.Window.WindowState%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9c71c-285">The order of precedence can also determine the size of a window when it is maximized, which is managed with the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="WindowState"></a>   
## <a name="window-state"></a><span data-ttu-id="9c71c-286">Stav okna</span><span class="sxs-lookup"><span data-stu-id="9c71c-286">Window State</span></span>  
 <span data-ttu-id="9c71c-287">Během životnosti okna s možností změny velikosti může mít tři stavy: normální, minimalizované a maximalizované.</span><span class="sxs-lookup"><span data-stu-id="9c71c-287">During the lifetime of a resizable window, it can have three states: normal, minimized, and maximized.</span></span> <span data-ttu-id="9c71c-288">Okno s normálním stavem je výchozí stav okna.</span><span class="sxs-lookup"><span data-stu-id="9c71c-288">A window with a *normal* state is the default state of a window.</span></span> <span data-ttu-id="9c71c-289">Okno s tímto stavem umožňuje uživateli, aby ho přesunul a změnil jeho velikost pomocí úchytu změny velikosti nebo ohraničení, pokud jde o změnu velikosti.</span><span class="sxs-lookup"><span data-stu-id="9c71c-289">A window with this state allows a user to move and resize it by using a resize grip or the border, if it is resizable.</span></span>  
  
 <span data-ttu-id="9c71c-290">Okno s minimalizovaným stavem se sbalí na jeho tlačítko na panelu úkolů <xref:System.Windows.Window.ShowInTaskbar%2A> , pokud je `true`nastaveno na hodnotu; v opačném případě se sbalí na nejmenší možnou velikost, která může být a přemístění do levého dolního rohu plochy.</span><span class="sxs-lookup"><span data-stu-id="9c71c-290">A window with a *minimized* state collapses to its task bar button if <xref:System.Windows.Window.ShowInTaskbar%2A> is set to `true`; otherwise, it collapses to the smallest possible size it can be and relocates itself to the bottom-left corner of the desktop.</span></span> <span data-ttu-id="9c71c-291">Velikost minimalizovaného okna nelze měnit pomocí ohraničení nebo změny velikosti, i když minimalizované okno, které není zobrazeno na panelu úloh, lze přetáhnout na plochu.</span><span class="sxs-lookup"><span data-stu-id="9c71c-291">Neither type of minimized window can be resized using a border or resize grip, although a minimized window that isn't shown in the task bar can be dragged around the desktop.</span></span>  
  
 <span data-ttu-id="9c71c-292">Okno s maximalizovaném stavem se zvětšuje na maximální velikost, která může být, což bude mít až velkou <xref:System.Windows.FrameworkElement.MaxWidth%2A> <xref:System.Windows.FrameworkElement.MaxHeight%2A>hodnotu, a <xref:System.Windows.Window.SizeToContent%2A> vlastnosti se určí.</span><span class="sxs-lookup"><span data-stu-id="9c71c-292">A window with a *maximized* state expands to the maximum size it can be, which will only be as large as its <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and <xref:System.Windows.Window.SizeToContent%2A> properties dictate.</span></span> <span data-ttu-id="9c71c-293">Podobně jako minimalizované okno nelze upravit velikost maximalizovaného okna pomocí úchytu pro změnu velikosti nebo přetažením ohraničení.</span><span class="sxs-lookup"><span data-stu-id="9c71c-293">Like a minimized window, a maximized window cannot be resized by using a resize grip or by dragging the border.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9c71c-294"><xref:System.Windows.Window.Top%2A> <xref:System.Windows.Window.Left%2A>Hodnoty vlastností<xref:System.Windows.FrameworkElement.Height%2A> , ,<xref:System.Windows.FrameworkElement.Width%2A>a v okně vždy reprezentují hodnoty pro normální stav, a to i v případě, že je okno momentálně maximalizováno nebo minimalizováno.</span><span class="sxs-lookup"><span data-stu-id="9c71c-294">The values of the <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.Height%2A> properties of a window always represent the values for the normal state, even when the window is currently maximized or minimized.</span></span>  
  
 <span data-ttu-id="9c71c-295">Stav okna lze nakonfigurovat nastavením jeho <xref:System.Windows.Window.WindowState%2A> vlastnosti, která může mít jednu z následujících <xref:System.Windows.WindowState> hodnot výčtu:</span><span class="sxs-lookup"><span data-stu-id="9c71c-295">The state of a window can be configured by setting its <xref:System.Windows.Window.WindowState%2A> property, which can have one of the following <xref:System.Windows.WindowState> enumeration values:</span></span>  
  
- <span data-ttu-id="9c71c-296"><xref:System.Windows.WindowState.Normal>výchozí</span><span class="sxs-lookup"><span data-stu-id="9c71c-296"><xref:System.Windows.WindowState.Normal> (default)</span></span>  
  
- <xref:System.Windows.WindowState.Maximized>  
  
- <xref:System.Windows.WindowState.Minimized>  
  
 <span data-ttu-id="9c71c-297">Následující příklad ukazuje, jak vytvořit okno, které se zobrazí při otevření v maximalizovaném okně.</span><span class="sxs-lookup"><span data-stu-id="9c71c-297">The following example shows how to create a window that is shown as maximized when it opens.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 <span data-ttu-id="9c71c-298">Obecně byste měli nastavit <xref:System.Windows.Window.WindowState%2A> , aby se nakonfiguroval počáteční stav okna.</span><span class="sxs-lookup"><span data-stu-id="9c71c-298">In general, you should set <xref:System.Windows.Window.WindowState%2A> to configure the initial state of a window.</span></span> <span data-ttu-id="9c71c-299">Jakmile se zobrazí okno pro změnu velikosti, uživatelé mohou změnit stav okna stisknutím tlačítek minimalizovat, maximalizovat a obnovit v záhlaví okna.</span><span class="sxs-lookup"><span data-stu-id="9c71c-299">Once a resizable window is shown, users can press the minimize, maximize, and restore buttons on the window's title bar to change the window state.</span></span>  
  
<a name="WindowAppearance"></a>   
## <a name="window-appearance"></a><span data-ttu-id="9c71c-300">Vzhled okna</span><span class="sxs-lookup"><span data-stu-id="9c71c-300">Window Appearance</span></span>  
 <span data-ttu-id="9c71c-301">Můžete změnit vzhled oblasti klienta okna přidáním obsahu pro jednotlivé okno, jako jsou tlačítka, popisky a textová pole.</span><span class="sxs-lookup"><span data-stu-id="9c71c-301">You change the appearance of the client area of a window by adding window-specific content to it, such as buttons, labels, and text boxes.</span></span> <span data-ttu-id="9c71c-302">Chcete-li nakonfigurovat neklientskou oblast <xref:System.Windows.Window> , poskytuje několik vlastností, které <xref:System.Windows.Window.Icon%2A> zahrnují nastavení ikony okna a <xref:System.Windows.Window.Title%2A> nastavení jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="9c71c-302">To configure the non-client area, <xref:System.Windows.Window> provides several properties, which include <xref:System.Windows.Window.Icon%2A> to set a window's icon and <xref:System.Windows.Window.Title%2A> to set its title.</span></span>  
  
 <span data-ttu-id="9c71c-303">Můžete také změnit vzhled a chování ohraničení neklientské oblasti tím, že nakonfigurujete režim změny velikosti okna, styl okna a zda se zobrazí jako tlačítko na panelu úloh plochy.</span><span class="sxs-lookup"><span data-stu-id="9c71c-303">You can also change the appearance and behavior of non-client area border by configuring a window's resize mode, window style, and whether it appears as a button in the desktop task bar.</span></span>  

<a name="Resize_Mode"></a>   
### <a name="resize-mode"></a><span data-ttu-id="9c71c-304">Změnit velikost režimu</span><span class="sxs-lookup"><span data-stu-id="9c71c-304">Resize Mode</span></span>  
 <span data-ttu-id="9c71c-305">V závislosti na <xref:System.Windows.Window.WindowStyle%2A> vlastnosti můžete určit, jak (a kdy) uživatelé mohou měnit velikost okna.</span><span class="sxs-lookup"><span data-stu-id="9c71c-305">Depending on the <xref:System.Windows.Window.WindowStyle%2A> property, you can control how (and if) users can resize the window.</span></span> <span data-ttu-id="9c71c-306">Volba stylu okna ovlivňuje, zda může uživatel změnit velikost okna přetažením jeho ohraničení myší, zda se tlačítka **minimalizovat**, **maximalizovat**a **změnit velikost** zobrazují v neklientské oblasti a v případě, že se zobrazí. umožněn.</span><span class="sxs-lookup"><span data-stu-id="9c71c-306">The choice of window style affects whether a user can resize the window by dragging its border with the mouse, whether the **Minimize**, **Maximize**, and **Resize** buttons appear on the non-client area, and, if they do appear, whether they are enabled.</span></span>  
  
 <span data-ttu-id="9c71c-307">Můžete nakonfigurovat, jak se změní velikost okna nastavením jeho <xref:System.Windows.Window.ResizeMode%2A> vlastnosti, což může být jedna z následujících <xref:System.Windows.ResizeMode> hodnot výčtu:</span><span class="sxs-lookup"><span data-stu-id="9c71c-307">You can configure how a window resizes by setting its <xref:System.Windows.Window.ResizeMode%2A> property, which can be one of the following <xref:System.Windows.ResizeMode> enumeration values:</span></span>  
  
- <xref:System.Windows.ResizeMode.NoResize>  
  
- <xref:System.Windows.ResizeMode.CanMinimize>  
  
- <span data-ttu-id="9c71c-308"><xref:System.Windows.ResizeMode.CanResize>výchozí</span><span class="sxs-lookup"><span data-stu-id="9c71c-308"><xref:System.Windows.ResizeMode.CanResize> (default)</span></span>  
  
- <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 <span data-ttu-id="9c71c-309">Stejně jako <xref:System.Windows.Window.WindowStyle%2A>v se režim změny velikosti okna pravděpodobně během své životnosti nezmění, což znamená, že je pravděpodobně možné ho nastavit ze [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek.</span><span class="sxs-lookup"><span data-stu-id="9c71c-309">As with <xref:System.Windows.Window.WindowStyle%2A>, the resize mode of a window is unlikely to change during its lifetime, which means that you'll most likely set it from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 <span data-ttu-id="9c71c-310">Všimněte si, že kontrolu <xref:System.Windows.Window.WindowState%2A> vlastností můžete zjistit, zda je okno maximalizováno, minimalizováno nebo obnoveno.</span><span class="sxs-lookup"><span data-stu-id="9c71c-310">Note that you can detect whether a window is maximized, minimized, or restored by inspecting the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="Window_Style"></a>   
### <a name="window-style"></a><span data-ttu-id="9c71c-311">Styl okna</span><span class="sxs-lookup"><span data-stu-id="9c71c-311">Window Style</span></span>  
 <span data-ttu-id="9c71c-312">Ohraničení, které je vystaveno mimo klientskou oblast okna, je vhodné pro většinu aplikací.</span><span class="sxs-lookup"><span data-stu-id="9c71c-312">The border that is exposed from the non-client area of a window is suitable for most applications.</span></span> <span data-ttu-id="9c71c-313">Existují však situace, kdy je třeba zadat různé typy ohraničení, nebo není nutné žádné ohraničení v závislosti na typu okna.</span><span class="sxs-lookup"><span data-stu-id="9c71c-313">However, there are circumstances where different types of borders are needed, or no borders are needed at all, depending on the type of window.</span></span>  
  
 <span data-ttu-id="9c71c-314">Chcete-li určit, jaký typ ohraničení okno získá, nastavte jeho <xref:System.Windows.Window.WindowStyle%2A> vlastnost pomocí jedné z následujících hodnot <xref:System.Windows.WindowStyle> výčtu:</span><span class="sxs-lookup"><span data-stu-id="9c71c-314">To control what type of border a window gets, you set its <xref:System.Windows.Window.WindowStyle%2A> property with one of the following values of the <xref:System.Windows.WindowStyle> enumeration:</span></span>  
  
- <xref:System.Windows.WindowStyle.None>  
  
- <span data-ttu-id="9c71c-315"><xref:System.Windows.WindowStyle.SingleBorderWindow>výchozí</span><span class="sxs-lookup"><span data-stu-id="9c71c-315"><xref:System.Windows.WindowStyle.SingleBorderWindow> (default)</span></span>  
  
- <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
- <xref:System.Windows.WindowStyle.ToolWindow>  
  
 <span data-ttu-id="9c71c-316">Efekt těchto stylů oken je znázorněn na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="9c71c-316">The effect of these window styles are illustrated in the following figure:</span></span>  
  
 ![Ilustrace stylů ohraničení okna](./media/wpf-windows-overview/window-border-styles.png)  
  
 <span data-ttu-id="9c71c-318">Můžete nastavit <xref:System.Windows.Window.WindowStyle%2A> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pomocí značky nebo kódu; vzhledem k tomu, že se po celou dobu životnosti okna pravděpodobně nemění, je pravděpodobné, že ho budete konfigurovat pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek.</span><span class="sxs-lookup"><span data-stu-id="9c71c-318">You can set <xref:System.Windows.Window.WindowStyle%2A> using either [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup or code; because it is unlikely to change during the lifetime of a window, you will most likely configure it using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a><span data-ttu-id="9c71c-319">Styl neobdélníkového okna</span><span class="sxs-lookup"><span data-stu-id="9c71c-319">Non-Rectangular Window Style</span></span>  
 <span data-ttu-id="9c71c-320">Existují také situace, kdy styly ohraničení, které <xref:System.Windows.Window.WindowStyle%2A> umožňují, nejsou dostačující.</span><span class="sxs-lookup"><span data-stu-id="9c71c-320">There are also situations where the border styles that <xref:System.Windows.Window.WindowStyle%2A> allows you to have are not sufficient.</span></span> <span data-ttu-id="9c71c-321">Například můžete chtít vytvořit aplikaci s neobdélníkovým ohraničením, jako [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] je například použití.</span><span class="sxs-lookup"><span data-stu-id="9c71c-321">For example, you may want to create an application with a non-rectangular border, like [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] uses.</span></span>  
  
 <span data-ttu-id="9c71c-322">Představte si například okno bublinového slova, které vidíte na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="9c71c-322">For example, consider the speech bubble window shown in the following figure:</span></span>  
  
 ![Okno bublinového slova, které říká, že se má přetáhnout](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 <span data-ttu-id="9c71c-324">Tento typ okna lze vytvořit nastavením <xref:System.Windows.Window.WindowStyle%2A> vlastnosti na <xref:System.Windows.WindowStyle.None>a pomocí speciální podpory, která <xref:System.Windows.Window> má transparentnost.</span><span class="sxs-lookup"><span data-stu-id="9c71c-324">This type of window can be created by setting the <xref:System.Windows.Window.WindowStyle%2A> property to <xref:System.Windows.WindowStyle.None>, and by using special support that <xref:System.Windows.Window> has for transparency.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 <span data-ttu-id="9c71c-325">Tato kombinace hodnot instruuje okno tak, aby bylo zcela transparentní.</span><span class="sxs-lookup"><span data-stu-id="9c71c-325">This combination of values instructs the window to render completely transparent.</span></span> <span data-ttu-id="9c71c-326">V tomto stavu nelze použít doplňky neklientských oblastí okna (tlačítka Zavřít nabídky, minimalizovat, maximalizovat a obnovit atd.).</span><span class="sxs-lookup"><span data-stu-id="9c71c-326">In this state, the window's non-client area adornments (the Close menu, Minimize, Maximize, and Restore buttons, and so on) cannot be used.</span></span> <span data-ttu-id="9c71c-327">V důsledku toho je třeba zadat vlastní.</span><span class="sxs-lookup"><span data-stu-id="9c71c-327">Consequently, you need to provide your own.</span></span>  
  
<a name="Task_Bar_Presence"></a>   
### <a name="task-bar-presence"></a><span data-ttu-id="9c71c-328">Přítomnost panelu úloh</span><span class="sxs-lookup"><span data-stu-id="9c71c-328">Task Bar Presence</span></span>  

<span data-ttu-id="9c71c-329">Výchozí vzhled okna obsahuje tlačítko na hlavním panelu, podobně jako na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="9c71c-329">The default appearance of a window includes a taskbar button, like the one shown in the following figure:</span></span>

 ![Snímek obrazovky, který zobrazuje okno s tlačítkem hlavního panelu.](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 <span data-ttu-id="9c71c-331">Některé typy oken nemají tlačítko na hlavním panelu, například pole se zprávami a dialogová okna (viz dialogová [okna Přehled](dialog-boxes-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="9c71c-331">Some types of windows don't have a task bar button, such as message boxes and dialog boxes (see [Dialog Boxes Overview](dialog-boxes-overview.md)).</span></span> <span data-ttu-id="9c71c-332">Nastavením <xref:System.Windows.Window.ShowInTaskbar%2A> vlastnosti (`true` ve výchozím nastavení) můžete určit, zda je zobrazeno tlačítko na panelu úloh okna.</span><span class="sxs-lookup"><span data-stu-id="9c71c-332">You can control whether the task bar button for a window is shown by setting the <xref:System.Windows.Window.ShowInTaskbar%2A> property (`true` by default).</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations"></a><span data-ttu-id="9c71c-333">Důležité informace o zabezpečení</span><span class="sxs-lookup"><span data-stu-id="9c71c-333">Security Considerations</span></span>  
 <span data-ttu-id="9c71c-334"><xref:System.Windows.Window>vyžaduje `UnmanagedCode` , aby se vytvořila instance oprávnění zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="9c71c-334"><xref:System.Windows.Window> requires `UnmanagedCode` security permission to be instantiated.</span></span> <span data-ttu-id="9c71c-335">Pro aplikace nainstalované a spouštěné z místního počítače spadá do sady oprávnění udělených aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9c71c-335">For applications installed on and launched from the local machine, this falls within the set of permissions that are granted to the application.</span></span>  
  
 <span data-ttu-id="9c71c-336">To však spadá mimo sadu oprávnění udělených aplikacím, které jsou spouštěny z Internetu nebo místního intranetu pomocí technologie ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="9c71c-336">However, this falls outside the set of permissions granted to applications that are launched from the Internet or Local intranet zone using ClickOnce.</span></span> <span data-ttu-id="9c71c-337">V důsledku toho se uživatelům zobrazí upozornění zabezpečení ClickOnce a bude muset zvýšit úroveň oprávnění pro aplikaci na úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="9c71c-337">Consequently, users will receive a ClickOnce security warning and will need to elevate the permission set for the application to full trust.</span></span>  
  
 <span data-ttu-id="9c71c-338">Kromě toho [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] nelze ve výchozím nastavení zobrazovat okna nebo dialogová okna.</span><span class="sxs-lookup"><span data-stu-id="9c71c-338">Additionally, [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] cannot show windows or dialog boxes by default.</span></span> <span data-ttu-id="9c71c-339">Diskuzi o zabezpečení samostatných aplikací najdete v tématu [strategie zabezpečení WPF – zabezpečení platformy](../wpf-security-strategy-platform-security.md).</span><span class="sxs-lookup"><span data-stu-id="9c71c-339">For a discussion on standalone application security considerations, see [WPF Security Strategy - Platform Security](../wpf-security-strategy-platform-security.md).</span></span>  
  
<a name="Other_Types_of_Windows"></a>   
## <a name="other-types-of-windows"></a><span data-ttu-id="9c71c-340">Jiné typy Windows</span><span class="sxs-lookup"><span data-stu-id="9c71c-340">Other Types of Windows</span></span>  
 <span data-ttu-id="9c71c-341"><xref:System.Windows.Navigation.NavigationWindow>je okno, které je navrženo pro hostování obsahu naviguje.</span><span class="sxs-lookup"><span data-stu-id="9c71c-341"><xref:System.Windows.Navigation.NavigationWindow> is a window that is designed to host navigable content.</span></span> <span data-ttu-id="9c71c-342">Další informace najdete v tématu [Přehled navigace](navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9c71c-342">For more information, see [Navigation Overview](navigation-overview.md)).</span></span>  
  
 <span data-ttu-id="9c71c-343">Dialogová okna jsou okna, která se často používají k získání informací z uživatele k dokončení funkce.</span><span class="sxs-lookup"><span data-stu-id="9c71c-343">Dialog boxes are windows that are often used to gather information from a user to complete a function.</span></span> <span data-ttu-id="9c71c-344">Například když chce uživatel otevřít soubor, dialogové okno **otevřít soubor** se obvykle zobrazí v aplikaci k získání názvu souboru od uživatele.</span><span class="sxs-lookup"><span data-stu-id="9c71c-344">For example, when a user wants to open a file, the **Open File** dialog box is usually displayed by an application to get the file name from the user.</span></span> <span data-ttu-id="9c71c-345">Další informace najdete v tématu [Přehled dialogových oken](dialog-boxes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9c71c-345">For more information, see [Dialog Boxes Overview](dialog-boxes-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c71c-346">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9c71c-346">See also</span></span>

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [<span data-ttu-id="9c71c-347">Přehled dialogových oken</span><span class="sxs-lookup"><span data-stu-id="9c71c-347">Dialog Boxes Overview</span></span>](dialog-boxes-overview.md)
- [<span data-ttu-id="9c71c-348">Sestavení aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="9c71c-348">Building a WPF Application</span></span>](building-a-wpf-application-wpf.md)
