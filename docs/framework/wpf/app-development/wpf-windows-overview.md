---
title: Windows – přehled
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
ms.openlocfilehash: b06afb56f43a874815cf9f679f1f7fefbdfd4565
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145537"
---
# <a name="wpf-windows-overview"></a><span data-ttu-id="1e9f2-102">Přehled WPF Windows</span><span class="sxs-lookup"><span data-stu-id="1e9f2-102">WPF Windows Overview</span></span>
<span data-ttu-id="1e9f2-103">Uživatelé interagují se samostatnými aplikacemi Windows Presentation Foundation (WPF) prostřednictvím oken.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-103">Users interact with Windows Presentation Foundation (WPF) standalone applications through windows.</span></span> <span data-ttu-id="1e9f2-104">Primárním účelem okna je hostování obsahu, který vizualizuje data a umožňuje uživatelům pracovat s daty.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-104">The primary purpose of a window is to host content that visualizes data and enables users to interact with data.</span></span> <span data-ttu-id="1e9f2-105">Samostatné wpf aplikace poskytují vlastní okna <xref:System.Windows.Window> pomocí třídy.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-105">Standalone WPF applications provide their own windows by using the <xref:System.Windows.Window> class.</span></span> <span data-ttu-id="1e9f2-106">Toto téma <xref:System.Windows.Window> představuje před pokrývající základy vytváření a správy oken v samostatných aplikacích.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-106">This topic introduces <xref:System.Windows.Window> before covering the fundamentals of creating and managing windows in standalone applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1e9f2-107">WPF aplikace hostované v prohlížeči, včetně aplikací prohlížeče XAML (XBAPs) a volných [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] stránek, neposkytují vlastní okna.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-107">Browser-hosted WPF applications, including XAML browser applications (XBAPs) and loose [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pages, don't provide their own windows.</span></span> <span data-ttu-id="1e9f2-108">Místo toho jsou hostovány v oknech poskytovaných aplikací Windows Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-108">Instead, they are hosted in windows provided by Windows Internet Explorer.</span></span> <span data-ttu-id="1e9f2-109">Viz [Přehled aplikací prohlížeče WPF XAML](wpf-xaml-browser-applications-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1e9f2-109">See [WPF XAML Browser Applications Overview](wpf-xaml-browser-applications-overview.md).</span></span>  

<a name="TheWindowClass"></a>
## <a name="the-window-class"></a><span data-ttu-id="1e9f2-110">Třída okna</span><span class="sxs-lookup"><span data-stu-id="1e9f2-110">The Window Class</span></span>  
 <span data-ttu-id="1e9f2-111">Následující obrázek znázorňuje jednotlivé části okna:</span><span class="sxs-lookup"><span data-stu-id="1e9f2-111">The following figure illustrates the constituent parts of a window:</span></span>  
  
 ![Snímek obrazovky, který zobrazuje prvky okna.](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 <span data-ttu-id="1e9f2-113">Okno je rozděleno do dvou oblastí: neklientská oblast a klientská oblast.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-113">A window is divided into two areas: the non-client area and client area.</span></span>  
  
 <span data-ttu-id="1e9f2-114">Oblast, která *není klientem* okna, je implementována wpf a zahrnuje části okna, které jsou společné pro většinu oken, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="1e9f2-114">The *non-client area* of a window is implemented by WPF and includes the parts of a window that are common to most windows, including the following:</span></span>  
  
- <span data-ttu-id="1e9f2-115">Hranice.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-115">A border.</span></span>  
  
- <span data-ttu-id="1e9f2-116">Záhlaví.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-116">A title bar.</span></span>  
  
- <span data-ttu-id="1e9f2-117">Ikona.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-117">An icon.</span></span>  
  
- <span data-ttu-id="1e9f2-118">Minimalizovat, maximalizovat a obnovit tlačítka.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-118">Minimize, Maximize, and Restore buttons.</span></span>  
  
- <span data-ttu-id="1e9f2-119">Tlačítko Zavřít.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-119">A Close button.</span></span>  
  
- <span data-ttu-id="1e9f2-120">Nabídka Systém s položkami nabídky, které uživatelům umožňují minimalizovat, maximalizovat, obnovit, přesunout, změnit velikost a zavřít okno.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-120">A System menu with menu items that allow users to minimize, maximize, restore, move, resize, and close a window.</span></span>  
  
 <span data-ttu-id="1e9f2-121">Klientská *oblast* okna je oblast v oblasti mimo klienta a vývojáři ji používají k přidání obsahu specifického pro aplikaci, jako jsou panely nabídek, panely nástrojů a ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-121">The *client area* of a window is the area within a window's non-client area and is used by developers to add application-specific content, such as menu bars, tool bars, and controls.</span></span>  
  
 <span data-ttu-id="1e9f2-122">V WPF okno je zapouzdřen třídy, <xref:System.Windows.Window> které používáte k provedení následujícího:</span><span class="sxs-lookup"><span data-stu-id="1e9f2-122">In WPF, a window is encapsulated by the <xref:System.Windows.Window> class that you use to do the following:</span></span>  
  
- <span data-ttu-id="1e9f2-123">Zobrazení okna.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-123">Display a window.</span></span>  
  
- <span data-ttu-id="1e9f2-124">Nakonfigurujte velikost, umístění a vzhled okna.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-124">Configure the size, position, and appearance of a window.</span></span>  
  
- <span data-ttu-id="1e9f2-125">Hostitelský obsah specifický pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-125">Host application-specific content.</span></span>  
  
- <span data-ttu-id="1e9f2-126">Spravujte životnost okna.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-126">Manage the lifetime of a window.</span></span>  
  
<a name="DefiningAWindow"></a>
## <a name="implementing-a-window"></a><span data-ttu-id="1e9f2-127">Implementace okna</span><span class="sxs-lookup"><span data-stu-id="1e9f2-127">Implementing a Window</span></span>  
 <span data-ttu-id="1e9f2-128">Implementace typického okna se skládá z vzhledu i chování, kde *vzhled* definuje vzhled okna pro uživatele a *chování* definuje způsob, jakým okno funguje při interakci uživatelů s ním.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-128">The implementation of a typical window comprises both appearance and behavior, where *appearance* defines how a window looks to users and *behavior* defines the way a window functions as users interact with it.</span></span> <span data-ttu-id="1e9f2-129">V WPF můžete implementovat vzhled a chování okna [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pomocí kódu nebo značky.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-129">In WPF, you can implement the appearance and behavior of a window using either code or [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 <span data-ttu-id="1e9f2-130">Obecně je však vzhled okna implementován pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek a jeho chování je implementováno pomocí kódu na pozadí, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-130">In general, however, the appearance of a window is implemented using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and its behavior is implemented using code-behind, as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 <span data-ttu-id="1e9f2-131">Chcete-li [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] povolit, aby soubor se značkami a soubor s kódem na pozadí spolupracovaly, jsou vyžadovány následující:</span><span class="sxs-lookup"><span data-stu-id="1e9f2-131">To enable a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup file and code-behind file to work together, the following are required:</span></span>  
  
- <span data-ttu-id="1e9f2-132">Ve značkách `Window` musí prvek `x:Class` obsahovat atribut.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-132">In markup, the `Window` element must include the `x:Class` attribute.</span></span> <span data-ttu-id="1e9f2-133">Když je aplikace vytvořena, `x:Class` existence v souboru značek způsobí, že modul sestavení `partial` společnosti Microsoft <xref:System.Windows.Window> (MSBuild) vytvoří třídu, která je odvozena od atributu a má název, který je určen `x:Class` atributem.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-133">When the application is built, the existence of `x:Class` in the markup file causes Microsoft build engine (MSBuild) to create a `partial` class that derives from <xref:System.Windows.Window> and has the name that is specified by the `x:Class` attribute.</span></span> <span data-ttu-id="1e9f2-134">To vyžaduje přidání deklarace oboru názvů [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] XML pro `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` schéma ( ).</span><span class="sxs-lookup"><span data-stu-id="1e9f2-134">This requires the addition of an XML namespace declaration for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schema ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).</span></span> <span data-ttu-id="1e9f2-135">Vygenerovaná `partial` třída `InitializeComponent` implementuje metodu, která je volána k registraci událostí a nastavení vlastností, které jsou implementovány v přirážce.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-135">The generated `partial` class implements the `InitializeComponent` method, which is called to register the events and set the properties that are implemented in markup.</span></span>  
  
- <span data-ttu-id="1e9f2-136">V kódu na pozadí musí `partial` být třída se stejným názvem, `x:Class` který je určen atributem <xref:System.Windows.Window>v přirážce a musí být odvozen z .</span><span class="sxs-lookup"><span data-stu-id="1e9f2-136">In code-behind, the class must be a `partial` class with the same name that is specified by the `x:Class` attribute in markup, and it must derive from <xref:System.Windows.Window>.</span></span> <span data-ttu-id="1e9f2-137">To umožňuje soubor s kódem na `partial` pozadí, který má být přidružen ke třídě, která je generována pro soubor značek při sestavení aplikace (viz [Vytváření aplikace WPF).](building-a-wpf-application-wpf.md)</span><span class="sxs-lookup"><span data-stu-id="1e9f2-137">This allows the code-behind file to be associated with the `partial` class that is generated for the markup file when the application is built (see [Building a WPF Application](building-a-wpf-application-wpf.md)).</span></span>  
  
- <span data-ttu-id="1e9f2-138">V kódu na <xref:System.Windows.Window> pozadí, třída musí implementovat `InitializeComponent` konstruktor, který volá metodu.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-138">In code-behind, the <xref:System.Windows.Window> class must implement a constructor that calls the `InitializeComponent` method.</span></span> <span data-ttu-id="1e9f2-139">`InitializeComponent`je implementována vygenerovanou `partial` třídou souboru značek pro registraci událostí a nastavení vlastností, které jsou definovány ve značkách.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-139">`InitializeComponent` is implemented by the markup file's generated `partial` class to register events and set properties that are defined in markup.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1e9f2-140">Přidáte-li nový <xref:System.Windows.Window> do projektu pomocí sady <xref:System.Windows.Window> Visual Studio, je implementována pomocí značek a kód na pozadí a zahrnuje potřebnou konfiguraci k vytvoření přidružení mezi soubory značky a kód na pozadí, jak je popsáno zde.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-140">When you add a new <xref:System.Windows.Window> to your project by using Visual Studio, the <xref:System.Windows.Window> is implemented using both markup and code-behind, and includes the necessary configuration to create the association between the markup and code-behind files as described here.</span></span>  
  
 <span data-ttu-id="1e9f2-141">S touto konfigurací na místě, můžete se zaměřit [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] na definování vzhledu okna v značky a provádění jeho chování v kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-141">With this configuration in place, you can focus on defining the appearance of the window in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and implementing its behavior in code-behind.</span></span> <span data-ttu-id="1e9f2-142">Následující příklad ukazuje okno s tlačítkem [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementovaným ve značkách a obslužnou rutinou události pro <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost tlačítka implementovanou v kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-142">The following example shows a window with a button, implemented in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and an event handler for the button's <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, implemented in code-behind.</span></span>  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>
## <a name="configuring-a-window-definition-for-msbuild"></a><span data-ttu-id="1e9f2-143">Konfigurace definice okna pro msbuild</span><span class="sxs-lookup"><span data-stu-id="1e9f2-143">Configuring a Window Definition for MSBuild</span></span>  
 <span data-ttu-id="1e9f2-144">Způsob implementace okna určuje, jak je nakonfigurován pro MSBuild.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-144">How you implement your window determines how it is configured for MSBuild.</span></span> <span data-ttu-id="1e9f2-145">Pro okno, které je [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] definováno pomocí značek a kódu na pozadí:</span><span class="sxs-lookup"><span data-stu-id="1e9f2-145">For a window that is defined using both [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind:</span></span>  
  
- <span data-ttu-id="1e9f2-146">Soubory značek XAML jsou konfigurovány `Page` jako položky MSBuild.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-146">XAML markup files are configured as MSBuild `Page` items.</span></span>  
  
- <span data-ttu-id="1e9f2-147">Soubory s kódem na pozadí `Compile` jsou konfigurovány jako položky MSBuild.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-147">Code-behind files are configured as MSBuild `Compile` items.</span></span>  
  
 <span data-ttu-id="1e9f2-148">To je znázorněno v následujícím souboru projektu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-148">This is shown in the following MSBuild project file.</span></span>  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 <span data-ttu-id="1e9f2-149">Informace o vytváření aplikací WPF naleznete [v tématu Vytváření aplikace WPF](building-a-wpf-application-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="1e9f2-149">For information about building WPF applications, see [Building a WPF Application](building-a-wpf-application-wpf.md).</span></span>  
  
<a name="WindowLifetime"></a>
## <a name="window-lifetime"></a><span data-ttu-id="1e9f2-150">Životnost okna</span><span class="sxs-lookup"><span data-stu-id="1e9f2-150">Window Lifetime</span></span>  
 <span data-ttu-id="1e9f2-151">Stejně jako u všech tříd má okno životnost, která začíná při prvním vytvoření instance, po které je otevřena, aktivována a deaktivována a nakonec uzavřena.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-151">As with any class, a window has a lifetime that begins when it is first instantiated, after which it is opened, activated and deactivated, and eventually closed.</span></span>  

<a name="Opening_a_Window"></a>
### <a name="opening-a-window"></a><span data-ttu-id="1e9f2-152">Otevření okna</span><span class="sxs-lookup"><span data-stu-id="1e9f2-152">Opening a Window</span></span>  
 <span data-ttu-id="1e9f2-153">Chcete-li otevřít okno, nejprve vytvořte jeho instanci, která je znázorněna v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-153">To open a window, you first create an instance of it, which is demonstrated in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 <span data-ttu-id="1e9f2-154">V tomto příkladu `MarkupAndCodeBehindWindow` je vytvořena instance při spuštění aplikace, <xref:System.Windows.Application.Startup> ke kterému dochází při vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-154">In this example, the `MarkupAndCodeBehindWindow` is instantiated when the application starts, which occurs when the <xref:System.Windows.Application.Startup> event is raised.</span></span>  
  
 <span data-ttu-id="1e9f2-155">Při vytvoření instance okna je odkaz na něj automaticky přidán do seznamu oken, <xref:System.Windows.Application> který <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>je spravován objektem (viz ).</span><span class="sxs-lookup"><span data-stu-id="1e9f2-155">When a window is instantiated, a reference to it is automatically added to a list of windows that is managed by the <xref:System.Windows.Application> object (see <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>).</span></span> <span data-ttu-id="1e9f2-156">Kromě toho první okno, které má být vytvořena instance <xref:System.Windows.Application> je ve výchozím nastavení <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>nastavena jako hlavní okno aplikace (viz).</span><span class="sxs-lookup"><span data-stu-id="1e9f2-156">Additionally, the first window to be instantiated is, by default, set by <xref:System.Windows.Application> as the main application window (see <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="1e9f2-157">Okno je nakonec otevřen <xref:System.Windows.Window.Show%2A> voláním metody; výsledek je zobrazen na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-157">The window is finally opened by calling the <xref:System.Windows.Window.Show%2A> method; the result is shown in the following figure.</span></span>  
  
 ![Okno otevřené voláním Window.Show](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 <span data-ttu-id="1e9f2-159">Okno, které je <xref:System.Windows.Window.Show%2A> otevřeno voláním je nemodlavé okno, což znamená, že aplikace pracuje v režimu, který umožňuje uživatelům aktivovat jiná okna ve stejné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-159">A window that is opened by calling <xref:System.Windows.Window.Show%2A> is a modeless window, which means that the application operates in a mode that allows users to activate other windows in the same application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1e9f2-160"><xref:System.Windows.Window.ShowDialog%2A>je volána k otevření oken, jako jsou dialogová okna modálně.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-160"><xref:System.Windows.Window.ShowDialog%2A> is called to open windows such as dialog boxes modally.</span></span> <span data-ttu-id="1e9f2-161">Další informace najdete v [tématu Přehled dialogových oken.](dialog-boxes-overview.md)</span><span class="sxs-lookup"><span data-stu-id="1e9f2-161">See [Dialog Boxes Overview](dialog-boxes-overview.md) for more information.</span></span>  
  
 <span data-ttu-id="1e9f2-162">Při <xref:System.Windows.Window.Show%2A> volání, okno provádí inicializační práce před je zobrazen a vytvořit infrastrukturu, která umožňuje přijímat vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-162">When <xref:System.Windows.Window.Show%2A> is called, a window performs initialization work before it is shown to establish infrastructure that allows it to receive user input.</span></span> <span data-ttu-id="1e9f2-163">Když je okno inicializováno, je vyvolána <xref:System.Windows.Window.SourceInitialized> událost a okno se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-163">When the window is initialized, the <xref:System.Windows.Window.SourceInitialized> event is raised and the window is shown.</span></span>  
  
 <span data-ttu-id="1e9f2-164">Jako zástupce <xref:System.Windows.Application.StartupUri%2A> lze nastavit, aby bylo možné určit první okno, které se otevře automaticky při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-164">As a shortcut, <xref:System.Windows.Application.StartupUri%2A> can be set to specify the first window that is opened automatically when an application starts.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 <span data-ttu-id="1e9f2-165">Při spuštění aplikace je okno určené <xref:System.Windows.Application.StartupUri%2A> hodnotou otevřeno nemodálně; interně okno se otevře voláním jeho <xref:System.Windows.Window.Show%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-165">When the application starts, the window specified by the value of <xref:System.Windows.Application.StartupUri%2A> is opened modelessly; internally, the window is opened by calling its <xref:System.Windows.Window.Show%2A> method.</span></span>  
  
<a name="Ownership"></a>
#### <a name="window-ownership"></a><span data-ttu-id="1e9f2-166">Vlastnictví okna</span><span class="sxs-lookup"><span data-stu-id="1e9f2-166">Window Ownership</span></span>  
 <span data-ttu-id="1e9f2-167">Okno, které je otevřeno <xref:System.Windows.Window.Show%2A> pomocí metody nemá implicitní vztah s oknem, který jej vytvořil; Uživatelé mohou pracovat s oběma okny nezávisle na druhém, což znamená, že jedno okno může provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="1e9f2-167">A window that is opened by using the <xref:System.Windows.Window.Show%2A> method does not have an implicit relationship with the window that created it; users can interact with either window independently of the other, which means that either window can do the following:</span></span>  
  
- <span data-ttu-id="1e9f2-168">Zakryjte druhé (pokud jedno z <xref:System.Windows.Window.Topmost%2A> oken `true`nemá svou vlastnost nastavenou na).</span><span class="sxs-lookup"><span data-stu-id="1e9f2-168">Cover the other (unless one of the windows has its <xref:System.Windows.Window.Topmost%2A> property set to `true`).</span></span>  
  
- <span data-ttu-id="1e9f2-169">Být minimalizovány, maximalizovány a obnoveny bez ovlivnění ostatních.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-169">Be minimized, maximized, and restored without affecting the other.</span></span>  
  
 <span data-ttu-id="1e9f2-170">Některá okna vyžadují vztah s oknem, které je otevře.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-170">Some windows require a relationship with the window that opens them.</span></span> <span data-ttu-id="1e9f2-171">Například aplikace integrovaného vývojového prostředí (IDE) může otevřít okna vlastností a okna nástrojů, jejichž typické chování je pokrýt okno, které je vytváří.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-171">For example, an Integrated Development Environment (IDE) application may open property windows and tool windows whose typical behavior is to cover the window that creates them.</span></span> <span data-ttu-id="1e9f2-172">Kromě toho by tato okna měla vždy zavřít, minimalizovat, maximalizovat a obnovit ve shodě s oknem, které je vytvořilo.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-172">Furthermore, such windows should always close, minimize, maximize, and restore in concert with the window that created them.</span></span> <span data-ttu-id="1e9f2-173">Takový vztah lze vytvořit tím, že jedno okno *vlastní* <xref:System.Windows.Window.Owner%2A> jiné a je dosaženo nastavením *vlastnosti vlastněného okna* s odkazem na *okno vlastníka*.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-173">Such a relationship can be established by making one window *own* another, and is achieved by setting the <xref:System.Windows.Window.Owner%2A> property of the *owned window* with a reference to the *owner window*.</span></span> <span data-ttu-id="1e9f2-174">To je ukázáno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-174">This is shown in the following example.</span></span>  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 <span data-ttu-id="1e9f2-175">Po navázání vlastnictví:</span><span class="sxs-lookup"><span data-stu-id="1e9f2-175">After ownership is established:</span></span>  
  
- <span data-ttu-id="1e9f2-176">Vlastněné okno může odkazovat na okno vlastníka kontrolou hodnoty jeho <xref:System.Windows.Window.Owner%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-176">The owned window can reference its owner window by inspecting the value of its <xref:System.Windows.Window.Owner%2A> property.</span></span>  
  
- <span data-ttu-id="1e9f2-177">Okno vlastníka můžete zjistit všechna okna, která vlastní <xref:System.Windows.Window.OwnedWindows%2A> kontrolou hodnoty jeho vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-177">The owner window can discover all the windows it owns by inspecting the value of its <xref:System.Windows.Window.OwnedWindows%2A> property.</span></span>  
  
<a name="Preventing"></a>
#### <a name="preventing-window-activation"></a><span data-ttu-id="1e9f2-178">Zabránění aktivaci okna</span><span class="sxs-lookup"><span data-stu-id="1e9f2-178">Preventing Window Activation</span></span>  
 <span data-ttu-id="1e9f2-179">Existují scénáře, kde by okna by neměla být aktivována při zobrazení, jako jsou například okna konverzace aplikace ve stylu messenger Internetu nebo okna oznámení e-mailové aplikace.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-179">There are scenarios where windows should not be activated when shown, such as conversation windows of an Internet messenger-style application or notification windows of an email application.</span></span>  
  
 <span data-ttu-id="1e9f2-180">Pokud vaše aplikace má okno, které by neměly být <xref:System.Windows.Window.ShowActivated%2A> aktivovány při zobrazení, můžete nastavit jeho vlastnost `false` před voláním <xref:System.Windows.Window.Show%2A> metody poprvé.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-180">If your application has a window that shouldn't be activated when shown, you can set its <xref:System.Windows.Window.ShowActivated%2A> property to `false` before calling the <xref:System.Windows.Window.Show%2A> method for the first time.</span></span> <span data-ttu-id="1e9f2-181">V důsledku toho:</span><span class="sxs-lookup"><span data-stu-id="1e9f2-181">As a consequence:</span></span>  
  
- <span data-ttu-id="1e9f2-182">Okno není aktivováno.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-182">The window is not activated.</span></span>  
  
- <span data-ttu-id="1e9f2-183">Událost okna <xref:System.Windows.Window.Activated> není aktivována.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-183">The window's <xref:System.Windows.Window.Activated> event is not raised.</span></span>  
  
- <span data-ttu-id="1e9f2-184">Aktuálně aktivované okno zůstane aktivováno.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-184">The currently activated window remains activated.</span></span>  
  
 <span data-ttu-id="1e9f2-185">Okno se však aktivuje, jakmile jej uživatel aktivuje kliknutím na klientskou nebo neklientskou oblast.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-185">The window will become activated, however, as soon as the user activates it by clicking either the client or non-client area.</span></span> <span data-ttu-id="1e9f2-186">V tomto případě:</span><span class="sxs-lookup"><span data-stu-id="1e9f2-186">In this case:</span></span>  
  
- <span data-ttu-id="1e9f2-187">Okno je aktivováno.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-187">The window is activated.</span></span>  
  
- <span data-ttu-id="1e9f2-188">Událost okna <xref:System.Windows.Window.Activated> je aktivována.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-188">The window's <xref:System.Windows.Window.Activated> event is raised.</span></span>  
  
- <span data-ttu-id="1e9f2-189">Dříve aktivované okno je deaktivováno.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-189">The previously activated window is deactivated.</span></span>  
  
- <span data-ttu-id="1e9f2-190">Okno a <xref:System.Windows.Window.Activated> <xref:System.Windows.Window.Deactivated> události jsou následně aktivována podle očekávání v reakci na akce uživatele.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-190">The window's <xref:System.Windows.Window.Deactivated> and <xref:System.Windows.Window.Activated> events are subsequently raised as expected in response to user actions.</span></span>  
  
<a name="Window_Activation"></a>
### <a name="window-activation"></a><span data-ttu-id="1e9f2-191">Aktivace okna</span><span class="sxs-lookup"><span data-stu-id="1e9f2-191">Window Activation</span></span>  
 <span data-ttu-id="1e9f2-192">Při prvním otevření se okno stane aktivním oknem <xref:System.Windows.Window.ShowActivated%2A> (pokud `false`není zobrazeno s nastavenou na ).</span><span class="sxs-lookup"><span data-stu-id="1e9f2-192">When a window is first opened, it becomes the active window (unless it is shown with <xref:System.Windows.Window.ShowActivated%2A> set to `false`).</span></span> <span data-ttu-id="1e9f2-193">*Aktivní okno* je okno, které právě zachytává vstup uživatele, například stisknutí kláves a kliknutí myší.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-193">The *active window* is the window that is currently capturing user input, such as key strokes and mouse clicks.</span></span> <span data-ttu-id="1e9f2-194">Když se okno aktivuje, <xref:System.Windows.Window.Activated> vyvolá událost.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-194">When a window becomes active, it raises the <xref:System.Windows.Window.Activated> event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1e9f2-195">Při prvním otevření okna <xref:System.Windows.FrameworkElement.Loaded> a <xref:System.Windows.Window.ContentRendered> události jsou vyvolány pouze po vyvolání <xref:System.Windows.Window.Activated> události.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-195">When a window is first opened, the <xref:System.Windows.FrameworkElement.Loaded> and <xref:System.Windows.Window.ContentRendered> events are raised only after the <xref:System.Windows.Window.Activated> event is raised.</span></span> <span data-ttu-id="1e9f2-196">S ohledem na tuto skutečnost může být <xref:System.Windows.Window.ContentRendered> okno skutečně považováno za otevřené, když je zvednuto.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-196">With this in mind, a window can effectively be considered opened when <xref:System.Windows.Window.ContentRendered> is raised.</span></span>  
  
 <span data-ttu-id="1e9f2-197">Jakmile se okno aktivuje, může uživatel aktivovat jiné okno ve stejné aplikaci nebo aktivovat jinou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-197">After a window becomes active, a user can activate another window in the same application, or activate another application.</span></span> <span data-ttu-id="1e9f2-198">V takovém případě se aktuálně aktivní okno deaktivuje a vyvolá <xref:System.Windows.Window.Deactivated> událost.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-198">When that happens, the currently active window becomes deactivated and raises the <xref:System.Windows.Window.Deactivated> event.</span></span> <span data-ttu-id="1e9f2-199">Podobně když uživatel vybere aktuálně deaktivované okno, okno se <xref:System.Windows.Window.Activated> znovu aktivuje a je aktivováno.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-199">Likewise, when the user selects a currently deactivated window, the window becomes active again and <xref:System.Windows.Window.Activated> is raised.</span></span>  
  
 <span data-ttu-id="1e9f2-200">Jedním z běžných důvodů pro zpracování <xref:System.Windows.Window.Activated> a <xref:System.Windows.Window.Deactivated> je povolit a zakázat funkce, které lze spustit pouze v případě, že je aktivní okno.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-200">One common reason to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> is to enable and disable functionality that can only run when a window is active.</span></span> <span data-ttu-id="1e9f2-201">Některá okna například zobrazují interaktivní obsah, který vyžaduje neustálý vstup uživatele nebo pozornost, včetně her a přehrávačů videa.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-201">For example, some windows display interactive content that requires constant user input or attention, including games and video players.</span></span> <span data-ttu-id="1e9f2-202">Následující příklad je zjednodušený přehrávač videa, <xref:System.Windows.Window.Activated> <xref:System.Windows.Window.Deactivated> který ukazuje, jak zpracovat a implementovat toto chování.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-202">The following example is a simplified video player that demonstrates how to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> to implement this behavior.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 <span data-ttu-id="1e9f2-203">Jiné typy aplikací může stále spustit kód na pozadí při deaktivaci okna.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-203">Other types of applications may still run code in the background when a window is deactivated.</span></span> <span data-ttu-id="1e9f2-204">Poštovní klient může například pokračovat v dotazování poštovního serveru, zatímco uživatel používá jiné aplikace.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-204">For example, a mail client may continue polling the mail server while the user is using other applications.</span></span> <span data-ttu-id="1e9f2-205">Aplikace, jako jsou tyto často poskytují různé nebo další chování, zatímco hlavní okno je deaktivován.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-205">Applications like these often provide different or additional behavior while the main window is deactivated.</span></span> <span data-ttu-id="1e9f2-206">Pokud jde o poštovní program, může to znamenat jak přidání nové položky pošty do složky Doručená pošta, tak přidání ikony oznámení do systémové lišty.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-206">With respect to the mail program, this may mean both adding the new mail item to the inbox and adding a notification icon to the system tray.</span></span> <span data-ttu-id="1e9f2-207">Ikonu oznámení je třeba zobrazit pouze v případě, že okno pošty není <xref:System.Windows.Window.IsActive%2A> aktivní, což lze určit kontrolou vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-207">A notification icon need only be displayed when the mail window isn't active, which can be determined by inspecting the <xref:System.Windows.Window.IsActive%2A> property.</span></span>  
  
 <span data-ttu-id="1e9f2-208">Pokud úloha na pozadí dokončí, okno může chtít upozornit <xref:System.Windows.Window.Activate%2A> uživatele naléhavěji voláním metody.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-208">If a background task completes, a window may want to notify the user more urgently by calling <xref:System.Windows.Window.Activate%2A> method.</span></span> <span data-ttu-id="1e9f2-209">Pokud uživatel pracuje s jinou <xref:System.Windows.Window.Activate%2A> aplikací aktivovanou při volání, tlačítko hlavního panelu okna bliká.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-209">If the user is interacting with another application activated when <xref:System.Windows.Window.Activate%2A> is called, the window's taskbar button flashes.</span></span> <span data-ttu-id="1e9f2-210">Pokud uživatel pracuje s aktuální aplikací, <xref:System.Windows.Window.Activate%2A> volání přenese okno do popředí.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-210">If a user is interacting with the current application, calling <xref:System.Windows.Window.Activate%2A> will bring the window to the foreground.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1e9f2-211">Můžete zpracovat aktivaci oboru <xref:System.Windows.Application.Activated?displayProperty=nameWithType> <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> aplikace pomocí události a.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-211">You can handle application-scope activation using the <xref:System.Windows.Application.Activated?displayProperty=nameWithType> and <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> events.</span></span>  
  
<a name="Closing_a_Window"></a>
### <a name="closing-a-window"></a><span data-ttu-id="1e9f2-212">Zavření okna</span><span class="sxs-lookup"><span data-stu-id="1e9f2-212">Closing a Window</span></span>  
 <span data-ttu-id="1e9f2-213">Životnost okna začne končit, když jej uživatel zavře.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-213">The life of a window starts coming to an end when a user closes it.</span></span> <span data-ttu-id="1e9f2-214">Okno lze zavřít pomocí prvků v oblasti mimo klienta, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="1e9f2-214">A window can be closed by using elements in the non-client area, including the following:</span></span>  
  
- <span data-ttu-id="1e9f2-215">Položka **Zavřít** v nabídce **Systém.**</span><span class="sxs-lookup"><span data-stu-id="1e9f2-215">The **Close** item of the **System** menu.</span></span>  
  
- <span data-ttu-id="1e9f2-216">Stisknutím kláves ALT+F4.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-216">Pressing ALT+F4.</span></span>  
  
- <span data-ttu-id="1e9f2-217">Stisknutím tlačítka **Zavřít.**</span><span class="sxs-lookup"><span data-stu-id="1e9f2-217">Pressing the **Close** button.</span></span>  
  
 <span data-ttu-id="1e9f2-218">Můžete poskytnout další mechanismy do oblasti klienta zavřít okno, častější, které zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="1e9f2-218">You can provide additional mechanisms to the client area to close a window, the more common of which include the following:</span></span>  
  
- <span data-ttu-id="1e9f2-219">**Ukončit** položku v nabídce **Soubor,** obvykle pro hlavní okna aplikace.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-219">An **Exit** item in the **File** menu, typically for main application windows.</span></span>  
  
- <span data-ttu-id="1e9f2-220">A **Zavřít** položku v nabídce **Soubor,** obvykle v sekundárním okně aplikace.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-220">A **Close** item in the **File** menu, typically on a secondary application window.</span></span>  
  
- <span data-ttu-id="1e9f2-221">Tlačítko **Storno,** obvykle v modálním dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-221">A **Cancel** button, typically on a modal dialog box.</span></span>  
  
- <span data-ttu-id="1e9f2-222">Tlačítko **Zavřít,** obvykle v nemodálním dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-222">A **Close** button, typically on a modeless dialog box.</span></span>  
  
 <span data-ttu-id="1e9f2-223">Chcete-li zavřít okno v reakci na jeden z těchto <xref:System.Windows.Window.Close%2A> vlastních mechanismů, je třeba volat metodu.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-223">To close a window in response to one of these custom mechanisms, you need to call the <xref:System.Windows.Window.Close%2A> method.</span></span> <span data-ttu-id="1e9f2-224">Následující příklad implementuje možnost zavřít okno výběrem **exit** v nabídce **Soubor.**</span><span class="sxs-lookup"><span data-stu-id="1e9f2-224">The following example implements the ability to close a window by choosing the **Exit** on the **File** menu.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 <span data-ttu-id="1e9f2-225">Když se okno zavře, vyvolá <xref:System.Windows.Window.Closing> dvě <xref:System.Windows.Window.Closed>události: a .</span><span class="sxs-lookup"><span data-stu-id="1e9f2-225">When a window closes, it raises two events: <xref:System.Windows.Window.Closing> and <xref:System.Windows.Window.Closed>.</span></span>  
  
 <span data-ttu-id="1e9f2-226"><xref:System.Windows.Window.Closing>je aktivována před zavřením okna a poskytuje mechanismus, kterým lze zabránit uzavření okna.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-226"><xref:System.Windows.Window.Closing> is raised before the window closes, and it provides a mechanism by which window closure can be prevented.</span></span> <span data-ttu-id="1e9f2-227">Jedním z běžných důvodů, proč zabránit uzavření okna, je, pokud obsah okna obsahuje upravená data.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-227">One common reason to prevent window closure is if window content contains modified data.</span></span> <span data-ttu-id="1e9f2-228">V takovém případě <xref:System.Windows.Window.Closing> událost může být zpracována k určení, zda jsou data znečištěná, a pokud ano, požádat uživatele, zda pokračovat v zavírání okna bez uložení dat nebo zrušit zavření okna.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-228">In this situation, the <xref:System.Windows.Window.Closing> event can be handled to determine whether data is dirty and, if so, to ask the user whether to either continue closing the window without saving the data or to cancel window closure.</span></span> <span data-ttu-id="1e9f2-229">Následující příklad ukazuje klíčové aspekty <xref:System.Windows.Window.Closing>zpracování .</span><span class="sxs-lookup"><span data-stu-id="1e9f2-229">The following example shows the key aspects of handling <xref:System.Windows.Window.Closing>.</span></span>  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 <span data-ttu-id="1e9f2-230"><xref:System.Windows.Window.Closing> Obslužná <xref:System.ComponentModel.CancelEventArgs>rutina události `Boolean` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> je předána `true` , která implementuje vlastnost, kterou jste nastavili, abyste zabránili zavření okna.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-230">The <xref:System.Windows.Window.Closing> event handler is passed a <xref:System.ComponentModel.CancelEventArgs>, which implements the `Boolean`<xref:System.ComponentModel.CancelEventArgs.Cancel%2A> property that you set to `true` to prevent a window from closing.</span></span>  
  
 <span data-ttu-id="1e9f2-231">Pokud <xref:System.Windows.Window.Closing> není zpracována, nebo je zpracována, ale není zrušena, okno se zavře.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-231">If <xref:System.Windows.Window.Closing> is not handled, or it is handled but not canceled, the window will close.</span></span> <span data-ttu-id="1e9f2-232">Těsně předtím, než se <xref:System.Windows.Window.Closed> okno skutečně zavře, je zvednut.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-232">Just before a window actually closes, <xref:System.Windows.Window.Closed> is raised.</span></span> <span data-ttu-id="1e9f2-233">V tomto okamžiku nelze zabránit zavření okna.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-233">At this point, a window cannot be prevented from closing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1e9f2-234">Aplikaci lze nakonfigurovat tak, aby se automaticky vypnula, když se zavře (viz) <xref:System.Windows.Application.MainWindow%2A>nebo poslední okno.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-234">An application can be configured to shut down automatically when either the main application window closes (see <xref:System.Windows.Application.MainWindow%2A>) or the last window closes.</span></span> <span data-ttu-id="1e9f2-235">Podrobnosti najdete v tématu <xref:System.Windows.Application.ShutdownMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-235">For details, see <xref:System.Windows.Application.ShutdownMode%2A>.</span></span>  
  
 <span data-ttu-id="1e9f2-236">Zatímco okno může být explicitně uzavřeno prostřednictvím mechanismů poskytovaných v oblastech bez klienta a klienta, okno může být také implicitně uzavřeno v důsledku chování v jiných částech aplikace nebo systému Windows, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="1e9f2-236">While a window can be explicitly closed through mechanisms provided in the non-client and client areas, a window can also be implicitly closed as a result of behavior in other parts of the application or Windows, including the following:</span></span>  
  
- <span data-ttu-id="1e9f2-237">Uživatel se odhlásí nebo vypne systém Windows.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-237">A user logs off or shuts down Windows.</span></span>  
  
- <span data-ttu-id="1e9f2-238">Majitel okna se zavře (viz). <xref:System.Windows.Window.Owner%2A></span><span class="sxs-lookup"><span data-stu-id="1e9f2-238">A window's owner closes (see <xref:System.Windows.Window.Owner%2A>).</span></span>  
  
- <span data-ttu-id="1e9f2-239">Hlavní okno aplikace je <xref:System.Windows.Application.ShutdownMode%2A> <xref:System.Windows.ShutdownMode.OnMainWindowClose>uzavřeno a je .</span><span class="sxs-lookup"><span data-stu-id="1e9f2-239">The main application window is closed and <xref:System.Windows.Application.ShutdownMode%2A> is <xref:System.Windows.ShutdownMode.OnMainWindowClose>.</span></span>  
  
- <span data-ttu-id="1e9f2-240"><xref:System.Windows.Application.Shutdown%2A>se nazývá.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-240"><xref:System.Windows.Application.Shutdown%2A> is called.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1e9f2-241">Po zavření nelze okno znovu otevřít.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-241">A window cannot be reopened after it is closed.</span></span>  
  
<a name="Window_Lifetime_Events"></a>
### <a name="window-lifetime-events"></a><span data-ttu-id="1e9f2-242">Události životnosti okna</span><span class="sxs-lookup"><span data-stu-id="1e9f2-242">Window Lifetime Events</span></span>  
 <span data-ttu-id="1e9f2-243">Následující obrázek znázorňuje posloupnost hlavních událostí v životnosti okna:</span><span class="sxs-lookup"><span data-stu-id="1e9f2-243">The following illustration shows the sequence of the principal events in the lifetime of a window:</span></span>  
  
 ![Diagram, který zobrazuje události v okně životnost.](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 <span data-ttu-id="1e9f2-245">Následující obrázek znázorňuje posloupnost hlavních událostí v pocelou<xref:System.Windows.Window.ShowActivated%2A> dobu životnosti okna, které je zobrazeno bez aktivace ( je nastaveno na `false` před zobrazením okna):</span><span class="sxs-lookup"><span data-stu-id="1e9f2-245">The following illustration shows the sequence of the principal events in the lifetime of a window that is shown without activation (<xref:System.Windows.Window.ShowActivated%2A> is set to `false` before the window is shown):</span></span>  
  
 ![Diagram, který zobrazuje události v okně životnost bez aktivace.](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>
## <a name="window-location"></a><span data-ttu-id="1e9f2-247">Umístění okna</span><span class="sxs-lookup"><span data-stu-id="1e9f2-247">Window Location</span></span>  
 <span data-ttu-id="1e9f2-248">Když je okno otevřené, má umístění v rozměrech x a y vzhledem k ploše.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-248">While a window is open, it has a location in the x and y dimensions relative to the desktop.</span></span> <span data-ttu-id="1e9f2-249">Toto umístění lze určit <xref:System.Windows.Window.Left%2A> kontrolou <xref:System.Windows.Window.Top%2A> vlastnosti a, resp.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-249">This location can be determined by inspecting the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties, respectively.</span></span> <span data-ttu-id="1e9f2-250">Tyto vlastnosti můžete nastavit tak, aby se změnilo umístění okna.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-250">You can set these properties to change the location of the window.</span></span>  
  
 <span data-ttu-id="1e9f2-251">Můžete také určit počáteční umístění <xref:System.Windows.Window> při prvním zjevu <xref:System.Windows.Window.WindowStartupLocation%2A> nastavením <xref:System.Windows.WindowStartupLocation> vlastnosti s jednou z následujících hodnot výčtu:</span><span class="sxs-lookup"><span data-stu-id="1e9f2-251">You can also specify the initial location of a <xref:System.Windows.Window> when it first appears by setting the <xref:System.Windows.Window.WindowStartupLocation%2A> property with one of the following <xref:System.Windows.WindowStartupLocation> enumeration values:</span></span>  
  
- <span data-ttu-id="1e9f2-252"><xref:System.Windows.WindowStartupLocation.CenterOwner>(výchozí)</span><span class="sxs-lookup"><span data-stu-id="1e9f2-252"><xref:System.Windows.WindowStartupLocation.CenterOwner> (default)</span></span>  
  
- <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
- <xref:System.Windows.WindowStartupLocation.Manual>  
  
 <span data-ttu-id="1e9f2-253">Pokud je umístění při <xref:System.Windows.WindowStartupLocation.Manual>spuštění <xref:System.Windows.Window.Left%2A> zadáno jako a vlastnosti a <xref:System.Windows.Window.Top%2A> nebyly nastaveny, požádá systém Windows o umístění, <xref:System.Windows.Window> ve které se má zobrazit.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-253">If the startup location is specified as <xref:System.Windows.WindowStartupLocation.Manual>, and the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties have not been set, <xref:System.Windows.Window> will ask Windows for a location to appear in.</span></span>  
  
<a name="Topmost_Windows_and_Z_Order"></a>
### <a name="topmost-windows-and-z-order"></a><span data-ttu-id="1e9f2-254">Nejvyšší okna a pořadí vykreslované</span><span class="sxs-lookup"><span data-stu-id="1e9f2-254">Topmost Windows and Z-Order</span></span>  
 <span data-ttu-id="1e9f2-255">Kromě umístění x a y má okno také umístění v dimenzi z, které určuje jeho svislou polohu vzhledem k ostatním oknům.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-255">Besides having an x and y location, a window also has a location in the z dimension, which determines its vertical position with respect to other windows.</span></span> <span data-ttu-id="1e9f2-256">To se označuje jako pořadí vykreslační pořadí okna a existují dva typy: normální pořadí vykreslační a nejvyšší pořadí vykresl.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-256">This is known as the window's z-order, and there are two types: normal z-order and topmost z-order.</span></span> <span data-ttu-id="1e9f2-257">Umístění okna v *normálním pořadí vykreslování* je určeno tím, zda je aktuálně aktivní či nikoli.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-257">The location of a window in the *normal z-order* is determined by whether it is currently active or not.</span></span> <span data-ttu-id="1e9f2-258">Ve výchozím nastavení je okno umístěno v normálním pořadí vykresláčů.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-258">By default, a window is located in the normal z-order.</span></span> <span data-ttu-id="1e9f2-259">Umístění okna v *nejvyšším pořadí vykreslování* je také určeno tím, zda je aktuálně aktivní nebo ne.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-259">The location of a window in the *topmost z-order* is also determined by whether it is currently active or not.</span></span> <span data-ttu-id="1e9f2-260">Kromě toho jsou okna v nejvyšším pořadí vykreslovaného stavu vždy umístěna nad okny v normálním pořadí vykreslovaného.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-260">Furthermore, windows in the topmost z-order are always located above windows in the normal z-order.</span></span> <span data-ttu-id="1e9f2-261">Okno je umístěno v nejvyšším pořadí vykreslování nastavením jeho <xref:System.Windows.Window.Topmost%2A> vlastnosti na `true`.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-261">A window is located in the topmost z-order by setting its <xref:System.Windows.Window.Topmost%2A> property to `true`.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 <span data-ttu-id="1e9f2-262">V každém pořadí vykreslovaného se aktuálně aktivní okno zobrazí nad všemi ostatními okny ve stejném pořadí vykresládek.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-262">Within each z-order, the currently active window appears above all other windows in the same z-order.</span></span>  
  
<a name="WindowSize"></a>
## <a name="window-size"></a><span data-ttu-id="1e9f2-263">Velikost okna</span><span class="sxs-lookup"><span data-stu-id="1e9f2-263">Window Size</span></span>  
 <span data-ttu-id="1e9f2-264">Kromě umístění na ploše má okno velikost, která je určena několika vlastnostmi, <xref:System.Windows.Window.SizeToContent%2A>včetně různých vlastností šířky a výšky a .</span><span class="sxs-lookup"><span data-stu-id="1e9f2-264">Besides having a desktop location, a window has a size that is determined by several properties, including the various width and height properties and <xref:System.Windows.Window.SizeToContent%2A>.</span></span>  
  
 <span data-ttu-id="1e9f2-265"><xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>a <xref:System.Windows.FrameworkElement.MaxWidth%2A> slouží ke správě rozsahu šířek, které může mít okno během své životnosti, a jsou konfigurovány tak, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-265"><xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.MaxWidth%2A> are used to manage the range of widths that a window can have during its lifetime, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 <span data-ttu-id="1e9f2-266">Výška okna <xref:System.Windows.FrameworkElement.MinHeight%2A>je <xref:System.Windows.FrameworkElement.Height%2A>spravována aplikacemi , a <xref:System.Windows.FrameworkElement.MaxHeight%2A>, a je konfigurována tak, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-266">Window height is managed by <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, and <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 <span data-ttu-id="1e9f2-267">Vzhledem k tomu, že různé hodnoty šířky a hodnoty výšky každý určit rozsah, je možné, že šířka a výška okna s nastavitelnou velikostí být kdekoli v rámci zadaného rozsahu pro příslušnou dimenzi.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-267">Because the various width values and height values each specify a range, it is possible for the width and height of a resizable window to be anywhere within the specified range for the respective dimension.</span></span> <span data-ttu-id="1e9f2-268">Chcete-li zjistit jeho aktuální <xref:System.Windows.FrameworkElement.ActualWidth%2A> <xref:System.Windows.FrameworkElement.ActualHeight%2A>šířku a výšku, zkontrolujte a , resp.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-268">To detect its current width and height, inspect <xref:System.Windows.FrameworkElement.ActualWidth%2A> and <xref:System.Windows.FrameworkElement.ActualHeight%2A>, respectively.</span></span>  
  
 <span data-ttu-id="1e9f2-269">Pokud chcete, aby šířka a výška okna měla velikost, která odpovídá velikosti obsahu okna, můžete použít <xref:System.Windows.Window.SizeToContent%2A> vlastnost, která má následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="1e9f2-269">If you'd like the width and height of your window to have a size that fits to the size of the window's content, you can use the <xref:System.Windows.Window.SizeToContent%2A> property, which has the following values:</span></span>  
  
- <span data-ttu-id="1e9f2-270"><xref:System.Windows.SizeToContent.Manual>.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-270"><xref:System.Windows.SizeToContent.Manual>.</span></span> <span data-ttu-id="1e9f2-271">Žádný efekt (výchozí).</span><span class="sxs-lookup"><span data-stu-id="1e9f2-271">No effect (default).</span></span>  
  
- <span data-ttu-id="1e9f2-272"><xref:System.Windows.SizeToContent.Width>.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-272"><xref:System.Windows.SizeToContent.Width>.</span></span> <span data-ttu-id="1e9f2-273">Přizpůsobit šířce obsahu, což má stejný <xref:System.Windows.FrameworkElement.MinWidth%2A> <xref:System.Windows.FrameworkElement.MaxWidth%2A> účinek jako nastavení obsahu i šířky obsahu.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-273">Fit to content width, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
- <span data-ttu-id="1e9f2-274"><xref:System.Windows.SizeToContent.Height>.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-274"><xref:System.Windows.SizeToContent.Height>.</span></span> <span data-ttu-id="1e9f2-275">Přizpůsobit výšce obsahu, která má stejný <xref:System.Windows.FrameworkElement.MinHeight%2A> účinek jako nastavení obsahu i <xref:System.Windows.FrameworkElement.MaxHeight%2A> výšky obsahu.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-275">Fit to content height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content.</span></span>  
  
- <span data-ttu-id="1e9f2-276"><xref:System.Windows.SizeToContent.WidthAndHeight>.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-276"><xref:System.Windows.SizeToContent.WidthAndHeight>.</span></span> <span data-ttu-id="1e9f2-277">Přizpůsobit šířce a výšce obsahu, což má <xref:System.Windows.FrameworkElement.MinHeight%2A> <xref:System.Windows.FrameworkElement.MaxHeight%2A> stejný účinek jako nastavení obsahu <xref:System.Windows.FrameworkElement.MinWidth%2A> <xref:System.Windows.FrameworkElement.MaxWidth%2A> i výšky obsahu a nastavení obsahu i šířky obsahu.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-277">Fit to content width and height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content, and setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
 <span data-ttu-id="1e9f2-278">Následující příklad ukazuje okno, které automaticky velikosti, aby se vešly jeho obsah, svisle i vodorovně, při prvním zobrazení.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-278">The following example shows a window that automatically sizes to fit its content, both vertically and horizontally, when first shown.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 <span data-ttu-id="1e9f2-279">Následující příklad ukazuje, jak <xref:System.Windows.Window.SizeToContent%2A> nastavit vlastnost v kódu určit, jak se změní velikost okna, aby se vešly jeho obsah .</span><span class="sxs-lookup"><span data-stu-id="1e9f2-279">The following example shows how to set the <xref:System.Windows.Window.SizeToContent%2A> property in code to specify how a window resizes to fit its content    .</span></span>
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>
## <a name="order-of-precedence-for-sizing-properties"></a><span data-ttu-id="1e9f2-280">Pořadí priorit pro vlastnosti velikosti</span><span class="sxs-lookup"><span data-stu-id="1e9f2-280">Order of Precedence for Sizing Properties</span></span>  
 <span data-ttu-id="1e9f2-281">V podstatě různé velikosti vlastnosti okna kombinovat definovat rozsah šířky a výšky pro okno s nastavitelnou velikostí.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-281">Essentially, the various sizes properties of a window combine to define the range of width and height for a resizable window.</span></span> <span data-ttu-id="1e9f2-282">Chcete-li zajistit zachování <xref:System.Windows.Window> platného rozsahu, vyhodnocuje hodnoty vlastností velikosti pomocí následujících pořadí priorit.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-282">To ensure a valid range is maintained, <xref:System.Windows.Window> evaluates the values of the size properties using the following orders of precedence.</span></span>  
  
 <span data-ttu-id="1e9f2-283">**Pro výškové vlastnosti:**</span><span class="sxs-lookup"><span data-stu-id="1e9f2-283">**For Height Properties:**</span></span>  
  
1. <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="1e9f2-284">**Pro vlastnosti šířky:**</span><span class="sxs-lookup"><span data-stu-id="1e9f2-284">**For Width Properties:**</span></span>  
  
1. <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="1e9f2-285">Pořadí priority můžete také určit velikost okna při maximalizaci, která je <xref:System.Windows.Window.WindowState%2A> spravována s vlastností.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-285">The order of precedence can also determine the size of a window when it is maximized, which is managed with the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="WindowState"></a>
## <a name="window-state"></a><span data-ttu-id="1e9f2-286">Stav okna</span><span class="sxs-lookup"><span data-stu-id="1e9f2-286">Window State</span></span>  
 <span data-ttu-id="1e9f2-287">Během životnosti okna s nastavitelnou platností může mít tři stavy: normální, minimalizované a maximalizované.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-287">During the lifetime of a resizable window, it can have three states: normal, minimized, and maximized.</span></span> <span data-ttu-id="1e9f2-288">Okno s *normálním* stavem je výchozí stav okna.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-288">A window with a *normal* state is the default state of a window.</span></span> <span data-ttu-id="1e9f2-289">Okno s tímto stavem umožňuje uživateli přesunout a změnit jeho velikost pomocí uzlu pro změny velikosti nebo ohraničení, pokud je možné změnit jeho velikost.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-289">A window with this state allows a user to move and resize it by using a resize grip or the border, if it is resizable.</span></span>  
  
 <span data-ttu-id="1e9f2-290">Okno s *minimalizovaným* stavem se sbalí <xref:System.Windows.Window.ShowInTaskbar%2A> na `true`tlačítko hlavního panelu, pokud je nastaveno na ; v opačném případě se zhroutí na nejmenší možnou velikost, kterou může být, a přemístí se do levého dolního rohu plochy.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-290">A window with a *minimized* state collapses to its task bar button if <xref:System.Windows.Window.ShowInTaskbar%2A> is set to `true`; otherwise, it collapses to the smallest possible size it can be and relocates itself to the bottom-left corner of the desktop.</span></span> <span data-ttu-id="1e9f2-291">Velikost žádného typu minimalizovaného okna nelze změnit pomocí ohraničení nebo uzlu pro změna velikosti, i když minimalizované okno, které není zobrazeno na hlavním panelu, lze přetáhnout po ploše.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-291">Neither type of minimized window can be resized using a border or resize grip, although a minimized window that isn't shown in the task bar can be dragged around the desktop.</span></span>  
  
 <span data-ttu-id="1e9f2-292">Okno s *maximalizovaným* stavem se rozbalí na maximální velikost, která může <xref:System.Windows.FrameworkElement.MaxWidth%2A> <xref:System.Windows.FrameworkElement.MaxHeight%2A>být, <xref:System.Windows.Window.SizeToContent%2A> což bude pouze tak velké, jako je jeho , a vlastnosti diktovat.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-292">A window with a *maximized* state expands to the maximum size it can be, which will only be as large as its <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and <xref:System.Windows.Window.SizeToContent%2A> properties dictate.</span></span> <span data-ttu-id="1e9f2-293">Podobně jako minimalizované okno nelze změnit velikost maximalizovaného okna pomocí uzlu pro změna velikosti nebo přetažením ohraničení.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-293">Like a minimized window, a maximized window cannot be resized by using a resize grip or by dragging the border.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1e9f2-294">Hodnoty <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti okna vždy představují hodnoty pro normální stav, i když je okno aktuálně maximalizováno nebo minimalizováno.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-294">The values of the <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.Height%2A> properties of a window always represent the values for the normal state, even when the window is currently maximized or minimized.</span></span>  
  
 <span data-ttu-id="1e9f2-295">Stav okna lze nakonfigurovat nastavením <xref:System.Windows.Window.WindowState%2A> jeho vlastnosti, která <xref:System.Windows.WindowState> může mít jednu z následujících hodnot výčtu:</span><span class="sxs-lookup"><span data-stu-id="1e9f2-295">The state of a window can be configured by setting its <xref:System.Windows.Window.WindowState%2A> property, which can have one of the following <xref:System.Windows.WindowState> enumeration values:</span></span>  
  
- <span data-ttu-id="1e9f2-296"><xref:System.Windows.WindowState.Normal>(výchozí)</span><span class="sxs-lookup"><span data-stu-id="1e9f2-296"><xref:System.Windows.WindowState.Normal> (default)</span></span>  
  
- <xref:System.Windows.WindowState.Maximized>  
  
- <xref:System.Windows.WindowState.Minimized>  
  
 <span data-ttu-id="1e9f2-297">Následující příklad ukazuje, jak vytvořit okno, které se při otevření zobrazí jako maximalizované.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-297">The following example shows how to create a window that is shown as maximized when it opens.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 <span data-ttu-id="1e9f2-298">Obecně byste měli <xref:System.Windows.Window.WindowState%2A> nastavit konfiguraci počátečního stavu okna.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-298">In general, you should set <xref:System.Windows.Window.WindowState%2A> to configure the initial state of a window.</span></span> <span data-ttu-id="1e9f2-299">Po zobrazení okna s nastavitelnou změnou velikosti mohou uživatelé stisknutím tlačítek minimalizovat, maximalizovat a obnovit v záhlaví okna a změnit stav okna.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-299">Once a resizable window is shown, users can press the minimize, maximize, and restore buttons on the window's title bar to change the window state.</span></span>  
  
<a name="WindowAppearance"></a>
## <a name="window-appearance"></a><span data-ttu-id="1e9f2-300">Vzhled okna</span><span class="sxs-lookup"><span data-stu-id="1e9f2-300">Window Appearance</span></span>  
 <span data-ttu-id="1e9f2-301">Vzhled klientské oblasti okna změníte přidáním obsahu specifického pro okno, například tlačítek, popisků a textových polí.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-301">You change the appearance of the client area of a window by adding window-specific content to it, such as buttons, labels, and text boxes.</span></span> <span data-ttu-id="1e9f2-302">Chcete-li nakonfigurovat oblast <xref:System.Windows.Window> mimo klienta, <xref:System.Windows.Window.Icon%2A> poskytuje několik vlastností, <xref:System.Windows.Window.Title%2A> které zahrnují nastavení ikony okna a nastavení jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-302">To configure the non-client area, <xref:System.Windows.Window> provides several properties, which include <xref:System.Windows.Window.Icon%2A> to set a window's icon and <xref:System.Windows.Window.Title%2A> to set its title.</span></span>  
  
 <span data-ttu-id="1e9f2-303">Vzhled a chování ohraničení neklientské oblasti můžete také změnit konfigurací režimu změny velikosti okna, stylu okna a jeho zobrazení jako tlačítka na hlavním panelu plochy.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-303">You can also change the appearance and behavior of non-client area border by configuring a window's resize mode, window style, and whether it appears as a button in the desktop task bar.</span></span>  

<a name="Resize_Mode"></a>
### <a name="resize-mode"></a><span data-ttu-id="1e9f2-304">Změna velikosti režimu</span><span class="sxs-lookup"><span data-stu-id="1e9f2-304">Resize Mode</span></span>  
 <span data-ttu-id="1e9f2-305">V závislosti <xref:System.Windows.Window.WindowStyle%2A> na vlastnosti můžete určit, jak (a pokud) mohou uživatelé změnit velikost okna.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-305">Depending on the <xref:System.Windows.Window.WindowStyle%2A> property, you can control how (and if) users can resize the window.</span></span> <span data-ttu-id="1e9f2-306">Volba stylu okna ovlivňuje, zda uživatel může změnit velikost okna přetažením jeho ohraničení myší, zda se v oblasti mimo klienta zobrazí tlačítka **Minimalizovat**, **Maximalizovat**a **Změnit velikost,** a pokud se zobrazí, zda jsou povolena.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-306">The choice of window style affects whether a user can resize the window by dragging its border with the mouse, whether the **Minimize**, **Maximize**, and **Resize** buttons appear on the non-client area, and, if they do appear, whether they are enabled.</span></span>  
  
 <span data-ttu-id="1e9f2-307">Můžete nakonfigurovat, jak se změní <xref:System.Windows.Window.ResizeMode%2A> velikost okna nastavením jeho <xref:System.Windows.ResizeMode> vlastnosti, což může být jedna z následujících hodnot výčtu:</span><span class="sxs-lookup"><span data-stu-id="1e9f2-307">You can configure how a window resizes by setting its <xref:System.Windows.Window.ResizeMode%2A> property, which can be one of the following <xref:System.Windows.ResizeMode> enumeration values:</span></span>  
  
- <xref:System.Windows.ResizeMode.NoResize>  
  
- <xref:System.Windows.ResizeMode.CanMinimize>  
  
- <span data-ttu-id="1e9f2-308"><xref:System.Windows.ResizeMode.CanResize>(výchozí)</span><span class="sxs-lookup"><span data-stu-id="1e9f2-308"><xref:System.Windows.ResizeMode.CanResize> (default)</span></span>  
  
- <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 <span data-ttu-id="1e9f2-309">Stejně <xref:System.Windows.Window.WindowStyle%2A>jako u , je nepravděpodobné, že by se režim změny velikosti okna [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] během jeho životnosti změnil, což znamená, že jej s největší pravděpodobností nastavíte ze značek.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-309">As with <xref:System.Windows.Window.WindowStyle%2A>, the resize mode of a window is unlikely to change during its lifetime, which means that you'll most likely set it from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 <span data-ttu-id="1e9f2-310">Všimněte si, že můžete zjistit, zda je okno maximalizované, <xref:System.Windows.Window.WindowState%2A> minimalizované nebo obnovené kontrolou vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-310">Note that you can detect whether a window is maximized, minimized, or restored by inspecting the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="Window_Style"></a>
### <a name="window-style"></a><span data-ttu-id="1e9f2-311">Styl okna</span><span class="sxs-lookup"><span data-stu-id="1e9f2-311">Window Style</span></span>  
 <span data-ttu-id="1e9f2-312">Ohraničení, které je vystaveno z neklientské oblasti okna, je vhodné pro většinu aplikací.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-312">The border that is exposed from the non-client area of a window is suitable for most applications.</span></span> <span data-ttu-id="1e9f2-313">Existují však okolnosti, kdy jsou zapotřebí různé typy ohraničení nebo v závislosti na typu okna nejsou zapotřebí žádné hranice.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-313">However, there are circumstances where different types of borders are needed, or no borders are needed at all, depending on the type of window.</span></span>  
  
 <span data-ttu-id="1e9f2-314">Chcete-li určit, jaký typ ohraničení <xref:System.Windows.Window.WindowStyle%2A> okno získá, nastavte jeho <xref:System.Windows.WindowStyle> vlastnost s jedním z následujících hodnot výčtu:</span><span class="sxs-lookup"><span data-stu-id="1e9f2-314">To control what type of border a window gets, you set its <xref:System.Windows.Window.WindowStyle%2A> property with one of the following values of the <xref:System.Windows.WindowStyle> enumeration:</span></span>  
  
- <xref:System.Windows.WindowStyle.None>  
  
- <span data-ttu-id="1e9f2-315"><xref:System.Windows.WindowStyle.SingleBorderWindow>(výchozí)</span><span class="sxs-lookup"><span data-stu-id="1e9f2-315"><xref:System.Windows.WindowStyle.SingleBorderWindow> (default)</span></span>  
  
- <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
- <xref:System.Windows.WindowStyle.ToolWindow>  
  
 <span data-ttu-id="1e9f2-316">Efekt těchto stylů oken je znázorněn na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="1e9f2-316">The effect of these window styles are illustrated in the following figure:</span></span>  
  
 ![Obrázek stylů ohraničení okna.](./media/wpf-windows-overview/window-border-styles.png)  
  
 <span data-ttu-id="1e9f2-318">Můžete nastavit <xref:System.Windows.Window.WindowStyle%2A> pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek nebo kódu; protože je nepravděpodobné, že se během životnosti okna změní, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] s největší pravděpodobností ji nakonfigurujete pomocí značek.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-318">You can set <xref:System.Windows.Window.WindowStyle%2A> using either [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup or code; because it is unlikely to change during the lifetime of a window, you will most likely configure it using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a><span data-ttu-id="1e9f2-319">Neobdélníkový styl okna</span><span class="sxs-lookup"><span data-stu-id="1e9f2-319">Non-Rectangular Window Style</span></span>  
 <span data-ttu-id="1e9f2-320">Existují také situace, kdy <xref:System.Windows.Window.WindowStyle%2A> styly ohraničení, které vám umožní mít, nejsou dostatečné.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-320">There are also situations where the border styles that <xref:System.Windows.Window.WindowStyle%2A> allows you to have are not sufficient.</span></span> <span data-ttu-id="1e9f2-321">Můžete například vytvořit aplikaci s neobdélníkovým ohraničením, jako je používá program Microsoft Windows Media Player.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-321">For example, you may want to create an application with a non-rectangular border, like Microsoft Windows Media Player uses.</span></span>  
  
 <span data-ttu-id="1e9f2-322">Zvažte například okno bubliny řeči zobrazené na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="1e9f2-322">For example, consider the speech bubble window shown in the following figure:</span></span>  
  
 ![Okno bubliny řeči s nápisem Drag Me.](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 <span data-ttu-id="1e9f2-324">Tento typ okna lze vytvořit <xref:System.Windows.Window.WindowStyle%2A> nastavením <xref:System.Windows.WindowStyle.None>vlastnosti na , <xref:System.Windows.Window> a pomocí speciální podpory, která má pro průhlednost.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-324">This type of window can be created by setting the <xref:System.Windows.Window.WindowStyle%2A> property to <xref:System.Windows.WindowStyle.None>, and by using special support that <xref:System.Windows.Window> has for transparency.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 <span data-ttu-id="1e9f2-325">Tato kombinace hodnot instruuje okno k vykreslení zcela transparentní.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-325">This combination of values instructs the window to render completely transparent.</span></span> <span data-ttu-id="1e9f2-326">V tomto stavu nelze použít vylepšení oblasti bez klienta (nabídka Zavřít, Minimalizovat, Maximalizovat a Obnovit a tak dále).</span><span class="sxs-lookup"><span data-stu-id="1e9f2-326">In this state, the window's non-client area adornments (the Close menu, Minimize, Maximize, and Restore buttons, and so on) cannot be used.</span></span> <span data-ttu-id="1e9f2-327">V důsledku toho musíte poskytnout své vlastní.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-327">Consequently, you need to provide your own.</span></span>  
  
<a name="Task_Bar_Presence"></a>
### <a name="task-bar-presence"></a><span data-ttu-id="1e9f2-328">Přítomnost na hlavním panelu</span><span class="sxs-lookup"><span data-stu-id="1e9f2-328">Task Bar Presence</span></span>  

<span data-ttu-id="1e9f2-329">Výchozí vzhled okna obsahuje tlačítko na hlavním panelu, například tlačítko znázorněné na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="1e9f2-329">The default appearance of a window includes a taskbar button, like the one shown in the following figure:</span></span>

 ![Snímek obrazovky s oknem s tlačítkem na hlavním panelu](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 <span data-ttu-id="1e9f2-331">Některé typy oken nemají tlačítko na hlavním panelu, například okna se zprávami a dialogová okna (viz [Přehled dialogových oken).](dialog-boxes-overview.md)</span><span class="sxs-lookup"><span data-stu-id="1e9f2-331">Some types of windows don't have a task bar button, such as message boxes and dialog boxes (see [Dialog Boxes Overview](dialog-boxes-overview.md)).</span></span> <span data-ttu-id="1e9f2-332">Nastavením vlastnosti (ve <xref:System.Windows.Window.ShowInTaskbar%2A> `true` výchozím nastavení) můžete určit, zda se zobrazí tlačítko hlavního panelu okna.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-332">You can control whether the task bar button for a window is shown by setting the <xref:System.Windows.Window.ShowInTaskbar%2A> property (`true` by default).</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>
## <a name="security-considerations"></a><span data-ttu-id="1e9f2-333">Aspekty zabezpečení</span><span class="sxs-lookup"><span data-stu-id="1e9f2-333">Security Considerations</span></span>  
 <span data-ttu-id="1e9f2-334"><xref:System.Windows.Window>vyžaduje `UnmanagedCode` oprávnění zabezpečení, které má být vytvořena instance.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-334"><xref:System.Windows.Window> requires `UnmanagedCode` security permission to be instantiated.</span></span> <span data-ttu-id="1e9f2-335">Pro aplikace nainstalované a spuštěné z místního počítače to spadá do sady oprávnění, která jsou aplikaci udělena.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-335">For applications installed on and launched from the local machine, this falls within the set of permissions that are granted to the application.</span></span>  
  
 <span data-ttu-id="1e9f2-336">To však spadá mimo sadu oprávnění udělených aplikacím, které jsou spouštěny z oblasti Internetu nebo místní intranetu pomocí ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-336">However, this falls outside the set of permissions granted to applications that are launched from the Internet or Local intranet zone using ClickOnce.</span></span> <span data-ttu-id="1e9f2-337">V důsledku toho uživatelé obdrží clickonce upozornění zabezpečení a bude muset zvýšit oprávnění nastavena pro aplikaci na úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-337">Consequently, users will receive a ClickOnce security warning and will need to elevate the permission set for the application to full trust.</span></span>  
  
 <span data-ttu-id="1e9f2-338">XBAPs navíc nemůže zobrazit okna nebo dialogová okna ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-338">Additionally, XBAPs cannot show windows or dialog boxes by default.</span></span> <span data-ttu-id="1e9f2-339">Diskuse o aspektech zabezpečení samostatných aplikací naleznete v [tématu WPF Security Strategy - Platform Security](../wpf-security-strategy-platform-security.md).</span><span class="sxs-lookup"><span data-stu-id="1e9f2-339">For a discussion on standalone application security considerations, see [WPF Security Strategy - Platform Security](../wpf-security-strategy-platform-security.md).</span></span>  
  
<a name="Other_Types_of_Windows"></a>
## <a name="other-types-of-windows"></a><span data-ttu-id="1e9f2-340">Jiné typy windows</span><span class="sxs-lookup"><span data-stu-id="1e9f2-340">Other Types of Windows</span></span>  
 <span data-ttu-id="1e9f2-341"><xref:System.Windows.Navigation.NavigationWindow>je okno, které je určeno k hostování splavného obsahu.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-341"><xref:System.Windows.Navigation.NavigationWindow> is a window that is designed to host navigable content.</span></span> <span data-ttu-id="1e9f2-342">Další informace naleznete v tématu [Navigační přehled](navigation-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="1e9f2-342">For more information, see [Navigation Overview](navigation-overview.md)).</span></span>  
  
 <span data-ttu-id="1e9f2-343">Dialogová okna jsou okna, která se často používají ke shromažďování informací od uživatele k dokončení funkce.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-343">Dialog boxes are windows that are often used to gather information from a user to complete a function.</span></span> <span data-ttu-id="1e9f2-344">Pokud například chce uživatel otevřít soubor, zobrazí se aplikace obvykle dialogové okno **Otevřít soubor,** aby uživatel získal název souboru.</span><span class="sxs-lookup"><span data-stu-id="1e9f2-344">For example, when a user wants to open a file, the **Open File** dialog box is usually displayed by an application to get the file name from the user.</span></span> <span data-ttu-id="1e9f2-345">Další informace naleznete v [tématu Přehled dialogových oken](dialog-boxes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1e9f2-345">For more information, see [Dialog Boxes Overview](dialog-boxes-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e9f2-346">Viz také</span><span class="sxs-lookup"><span data-stu-id="1e9f2-346">See also</span></span>

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [<span data-ttu-id="1e9f2-347">Přehled dialogových oken</span><span class="sxs-lookup"><span data-stu-id="1e9f2-347">Dialog Boxes Overview</span></span>](dialog-boxes-overview.md)
- [<span data-ttu-id="1e9f2-348">Sestavení aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="1e9f2-348">Building a WPF Application</span></span>](building-a-wpf-application-wpf.md)
