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
ms.openlocfilehash: 60ed101df691db9f1afa8e47702f131bee384495
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625314"
---
# <a name="wpf-windows-overview"></a><span data-ttu-id="662dd-102">Přehled WPF Windows</span><span class="sxs-lookup"><span data-stu-id="662dd-102">WPF Windows Overview</span></span>
<span data-ttu-id="662dd-103">Uživatelé komunikují s samostatné aplikace Windows Presentation Foundation (WPF) prostřednictvím systému windows.</span><span class="sxs-lookup"><span data-stu-id="662dd-103">Users interact with Windows Presentation Foundation (WPF) standalone applications through windows.</span></span> <span data-ttu-id="662dd-104">Primárním účelem okna je jako hostitele obsahu, která data vizualizuje a umožňuje uživatelům interakci s daty.</span><span class="sxs-lookup"><span data-stu-id="662dd-104">The primary purpose of a window is to host content that visualizes data and enables users to interact with data.</span></span> <span data-ttu-id="662dd-105">Samostatné [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace poskytují jejich vlastní okna s použitím <xref:System.Windows.Window> třídy.</span><span class="sxs-lookup"><span data-stu-id="662dd-105">Standalone [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications provide their own windows by using the <xref:System.Windows.Window> class.</span></span> <span data-ttu-id="662dd-106">Toto téma představuje <xref:System.Windows.Window> před pokrývají základní informace o vytváření a správa systému windows v samostatné aplikace.</span><span class="sxs-lookup"><span data-stu-id="662dd-106">This topic introduces <xref:System.Windows.Window> before covering the fundamentals of creating and managing windows in standalone applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="662dd-107">Hostované v prohlížeči [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikací, včetně [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] a dojde ke ztrátě [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] neposkytují stránek, vlastní systému windows.</span><span class="sxs-lookup"><span data-stu-id="662dd-107">Browser-hosted [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications, including [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] and loose [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pages, don't provide their own windows.</span></span> <span data-ttu-id="662dd-108">Místo toho jsou hostované v systému windows poskytuje [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)].</span><span class="sxs-lookup"><span data-stu-id="662dd-108">Instead, they are hosted in windows provided by [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)].</span></span> <span data-ttu-id="662dd-109">Zobrazit [přehled aplikací prohlížeče WPF XAML](wpf-xaml-browser-applications-overview.md).</span><span class="sxs-lookup"><span data-stu-id="662dd-109">See [WPF XAML Browser Applications Overview](wpf-xaml-browser-applications-overview.md).</span></span>  

<a name="TheWindowClass"></a>   
## <a name="the-window-class"></a><span data-ttu-id="662dd-110">Třídy oken</span><span class="sxs-lookup"><span data-stu-id="662dd-110">The Window Class</span></span>  
 <span data-ttu-id="662dd-111">Následující obrázek znázorňuje základní části okna:</span><span class="sxs-lookup"><span data-stu-id="662dd-111">The following figure illustrates the constituent parts of a window:</span></span>  
  
 ![Snímek obrazovky zobrazující prvků okna.](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 <span data-ttu-id="662dd-113">Okno je rozdělen do dvou oblastí: neklientská oblast a klientské oblasti.</span><span class="sxs-lookup"><span data-stu-id="662dd-113">A window is divided into two areas: the non-client area and client area.</span></span>  
  
 <span data-ttu-id="662dd-114">*Neklientská oblast* okna je implementováno [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] a obsahuje části okna, které jsou společné pro většinu windows, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="662dd-114">The *non-client area* of a window is implemented by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] and includes the parts of a window that are common to most windows, including the following:</span></span>  
  
- <span data-ttu-id="662dd-115">Ohraničení.</span><span class="sxs-lookup"><span data-stu-id="662dd-115">A border.</span></span>  
  
- <span data-ttu-id="662dd-116">Záhlaví okna.</span><span class="sxs-lookup"><span data-stu-id="662dd-116">A title bar.</span></span>  
  
- <span data-ttu-id="662dd-117">Ikona.</span><span class="sxs-lookup"><span data-stu-id="662dd-117">An icon.</span></span>  
  
- <span data-ttu-id="662dd-118">Minimalizovat, maximalizovat a obnovit tlačítka.</span><span class="sxs-lookup"><span data-stu-id="662dd-118">Minimize, Maximize, and Restore buttons.</span></span>  
  
- <span data-ttu-id="662dd-119">Tlačítko pro uzavření.</span><span class="sxs-lookup"><span data-stu-id="662dd-119">A Close button.</span></span>  
  
- <span data-ttu-id="662dd-120">Systémové nabídky pomocí položky nabídky, které umožňují uživatelům minimalizovat, maximalizovat, obnovení, přesunutí, změna velikosti a zavření okna.</span><span class="sxs-lookup"><span data-stu-id="662dd-120">A System menu with menu items that allow users to minimize, maximize, restore, move, resize, and close a window.</span></span>  
  
 <span data-ttu-id="662dd-121">*Klientské oblasti* okna je oblast v neklientské oblasti okna a vývojáři slouží k přidání obsahu specifické pro aplikace, jako je například panel nabídek, panelů nástrojů a ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="662dd-121">The *client area* of a window is the area within a window's non-client area and is used by developers to add application-specific content, such as menu bars, tool bars, and controls.</span></span>  
  
 <span data-ttu-id="662dd-122">V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], okna jsou zapouzdřena objektem <xref:System.Windows.Window> třídu, která vám postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="662dd-122">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], a window is encapsulated by the <xref:System.Windows.Window> class that you use to do the following:</span></span>  
  
- <span data-ttu-id="662dd-123">Zobrazte okno.</span><span class="sxs-lookup"><span data-stu-id="662dd-123">Display a window.</span></span>  
  
- <span data-ttu-id="662dd-124">Nakonfigurujte velikost, umístění a vzhled okna.</span><span class="sxs-lookup"><span data-stu-id="662dd-124">Configure the size, position, and appearance of a window.</span></span>  
  
- <span data-ttu-id="662dd-125">Hostování obsahu specifické pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="662dd-125">Host application-specific content.</span></span>  
  
- <span data-ttu-id="662dd-126">Správa životního cyklu okna.</span><span class="sxs-lookup"><span data-stu-id="662dd-126">Manage the lifetime of a window.</span></span>  
  
<a name="DefiningAWindow"></a>   
## <a name="implementing-a-window"></a><span data-ttu-id="662dd-127">Implementace okna</span><span class="sxs-lookup"><span data-stu-id="662dd-127">Implementing a Window</span></span>  
 <span data-ttu-id="662dd-128">Vzhled a chování, se skládá z implementace typické okno kde *vzhled* definuje, jak vypadá okno pro uživatele a *chování* definuje způsob, jakým okno funguje, jak uživatelé pracují s ním.</span><span class="sxs-lookup"><span data-stu-id="662dd-128">The implementation of a typical window comprises both appearance and behavior, where *appearance* defines how a window looks to users and *behavior* defines the way a window functions as users interact with it.</span></span> <span data-ttu-id="662dd-129">V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], můžete implementovat vzhled a chování oken pomocí buď kódu nebo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek.</span><span class="sxs-lookup"><span data-stu-id="662dd-129">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], you can implement the appearance and behavior of a window using either code or [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 <span data-ttu-id="662dd-130">Obecně platí, ale vzhled okna je implementováno pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značky a její chování je implementováno pomocí použití modelu code-behind, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="662dd-130">In general, however, the appearance of a window is implemented using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and its behavior is implemented using code-behind, as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 <span data-ttu-id="662dd-131">Chcete-li povolit [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru označení a použití modelu code-behind soubor spolupráce, vyžadují se následující věci:</span><span class="sxs-lookup"><span data-stu-id="662dd-131">To enable a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup file and code-behind file to work together, the following are required:</span></span>  
  
- <span data-ttu-id="662dd-132">V kódu `Window` musí obsahovat element `x:Class` atribut.</span><span class="sxs-lookup"><span data-stu-id="662dd-132">In markup, the `Window` element must include the `x:Class` attribute.</span></span> <span data-ttu-id="662dd-133">Když je aplikace sestavená, existenci `x:Class` ve značkách soubor způsobí, že [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] k vytvoření `partial` třídu odvozenou od <xref:System.Windows.Window> a má název, který je určen `x:Class` atribut.</span><span class="sxs-lookup"><span data-stu-id="662dd-133">When the application is built, the existence of `x:Class` in the markup file causes [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] to create a `partial` class that derives from <xref:System.Windows.Window> and has the name that is specified by the `x:Class` attribute.</span></span> <span data-ttu-id="662dd-134">To vyžaduje přidání [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] deklarace oboru názvů pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schématu ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).</span><span class="sxs-lookup"><span data-stu-id="662dd-134">This requires the addition of an [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace declaration for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schema ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).</span></span> <span data-ttu-id="662dd-135">Vygenerovaný `partial` implementuje třída `InitializeComponent` metodu, která je volána k registraci události a nastavit vlastnosti, které jsou implementovány v kódu.</span><span class="sxs-lookup"><span data-stu-id="662dd-135">The generated `partial` class implements the `InitializeComponent` method, which is called to register the events and set the properties that are implemented in markup.</span></span>  
  
- <span data-ttu-id="662dd-136">V modelu code-behind, musí být třída `partial` třídy se stejným názvem, která je zadána `x:Class` atribut v kódu který musí být odvozen od <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="662dd-136">In code-behind, the class must be a `partial` class with the same name that is specified by the `x:Class` attribute in markup, and it must derive from <xref:System.Windows.Window>.</span></span> <span data-ttu-id="662dd-137">To umožňuje použití modelu code-behind souboru má být spojen s `partial` třídu, která se vygeneruje pro označovacího souboru, když je aplikace sestavená (viz [sestavení aplikace WPF](building-a-wpf-application-wpf.md)).</span><span class="sxs-lookup"><span data-stu-id="662dd-137">This allows the code-behind file to be associated with the `partial` class that is generated for the markup file when the application is built (see [Building a WPF Application](building-a-wpf-application-wpf.md)).</span></span>  
  
- <span data-ttu-id="662dd-138">V modelu code-behind <xref:System.Windows.Window> třída musí implementovat konstruktor, který volá `InitializeComponent` metody.</span><span class="sxs-lookup"><span data-stu-id="662dd-138">In code-behind, the <xref:System.Windows.Window> class must implement a constructor that calls the `InitializeComponent` method.</span></span> <span data-ttu-id="662dd-139">`InitializeComponent` je implementován ve značce vygenerovaný soubor `partial` třídy k registraci události a nastavte vlastnosti, které jsou definovány v kódu.</span><span class="sxs-lookup"><span data-stu-id="662dd-139">`InitializeComponent` is implemented by the markup file's generated `partial` class to register events and set properties that are defined in markup.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="662dd-140">Když přidáte nový <xref:System.Windows.Window> do svého projektu pomocí [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], <xref:System.Windows.Window> je implementováno pomocí značek a kódu a obsahuje nezbytnou konfiguraci pro vytvoření přidružení mezi značky a modelu code-behind soubory jako najdete tady.</span><span class="sxs-lookup"><span data-stu-id="662dd-140">When you add a new <xref:System.Windows.Window> to your project by using [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], the <xref:System.Windows.Window> is implemented using both markup and code-behind, and includes the necessary configuration to create the association between the markup and code-behind files as described here.</span></span>  
  
 <span data-ttu-id="662dd-141">S touto konfigurací na místě, můžete se soustředit na definování vzhledu okna [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek a provádění své chování v kódu.</span><span class="sxs-lookup"><span data-stu-id="662dd-141">With this configuration in place, you can focus on defining the appearance of the window in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and implementing its behavior in code-behind.</span></span> <span data-ttu-id="662dd-142">Následující příklad ukazuje okno s tlačítkem, implementované v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značky a obslužnou rutinu události pro tlačítka <xref:System.Windows.Controls.Primitives.ButtonBase.Click> události, implementovat v kódu.</span><span class="sxs-lookup"><span data-stu-id="662dd-142">The following example shows a window with a button, implemented in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and an event handler for the button's <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, implemented in code-behind.</span></span>  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>   
## <a name="configuring-a-window-definition-for-msbuild"></a><span data-ttu-id="662dd-143">Konfigurace definice okna pro MSBuild</span><span class="sxs-lookup"><span data-stu-id="662dd-143">Configuring a Window Definition for MSBuild</span></span>  
 <span data-ttu-id="662dd-144">Jak implementovat okno určuje, jak je nakonfigurována pro [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)].</span><span class="sxs-lookup"><span data-stu-id="662dd-144">How you implement your window determines how it is configured for [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)].</span></span> <span data-ttu-id="662dd-145">Pro okno, které je definováno pomocí obou [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek a kódu:</span><span class="sxs-lookup"><span data-stu-id="662dd-145">For a window that is defined using both [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind:</span></span>  
  
- [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <span data-ttu-id="662dd-146">soubory kódu nejsou nakonfigurované jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` položky.</span><span class="sxs-lookup"><span data-stu-id="662dd-146">markup files are configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items.</span></span>  
  
- <span data-ttu-id="662dd-147">Soubory kódu na pozadí jsou nakonfigurované jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Compile` položky.</span><span class="sxs-lookup"><span data-stu-id="662dd-147">Code-behind files are configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Compile` items.</span></span>  
  
 <span data-ttu-id="662dd-148">To je ukázáno v následujícím [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="662dd-148">This is shown in the following [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] project file.</span></span>  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 <span data-ttu-id="662dd-149">Informace o vytváření [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] naleznete v tématu [sestavení aplikace WPF](building-a-wpf-application-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="662dd-149">For information about building [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications, see [Building a WPF Application](building-a-wpf-application-wpf.md).</span></span>  
  
<a name="WindowLifetime"></a>   
## <a name="window-lifetime"></a><span data-ttu-id="662dd-150">Doba života okna</span><span class="sxs-lookup"><span data-stu-id="662dd-150">Window Lifetime</span></span>  
 <span data-ttu-id="662dd-151">S všechny třídy, má okno s dobou života, která začíná, když je vytvořena první instance, po jejímž uplynutí ho je otevřen, aktivovat a deaktivovat a nakonec zavřít.</span><span class="sxs-lookup"><span data-stu-id="662dd-151">As with any class, a window has a lifetime that begins when it is first instantiated, after which it is opened, activated and deactivated, and eventually closed.</span></span>  

<a name="Opening_a_Window"></a>   
### <a name="opening-a-window"></a><span data-ttu-id="662dd-152">Otevřete okno</span><span class="sxs-lookup"><span data-stu-id="662dd-152">Opening a Window</span></span>  
 <span data-ttu-id="662dd-153">Otevřete okno, nejprve vytvořte její instanci, která je znázorněn v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="662dd-153">To open a window, you first create an instance of it, which is demonstrated in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 <span data-ttu-id="662dd-154">V tomto příkladu `MarkupAndCodeBehindWindow` je vytvořena instance při spuštění aplikace, které dojde při <xref:System.Windows.Application.Startup> událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="662dd-154">In this example, the `MarkupAndCodeBehindWindow` is instantiated when the application starts, which occurs when the <xref:System.Windows.Application.Startup> event is raised.</span></span>  
  
 <span data-ttu-id="662dd-155">Při vytváření instance časového období se na ni odkaz automaticky přidá do seznamu systému windows, která jsou spravována <xref:System.Windows.Application> objektu (viz <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="662dd-155">When a window is instantiated, a reference to it is automatically added to a list of windows that is managed by the <xref:System.Windows.Application> object (see <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>).</span></span> <span data-ttu-id="662dd-156">Kromě toho první okno má být vytvořena se ve výchozím nastavení <xref:System.Windows.Application> jako hlavní okno aplikace (viz <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="662dd-156">Additionally, the first window to be instantiated is, by default, set by <xref:System.Windows.Application> as the main application window (see <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="662dd-157">Otevření okna je nakonec voláním <xref:System.Windows.Window.Show%2A> metoda; výsledek je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="662dd-157">The window is finally opened by calling the <xref:System.Windows.Window.Show%2A> method; the result is shown in the following figure.</span></span>  
  
 ![Otevření okna voláním Window.Show](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 <span data-ttu-id="662dd-159">Okno, které se otevře voláním <xref:System.Windows.Window.Show%2A> je nemodálním okně, což znamená, že aplikace funguje v režimu, který umožňuje uživatelům aktivovat ostatní okna ve stejné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="662dd-159">A window that is opened by calling <xref:System.Windows.Window.Show%2A> is a modeless window, which means that the application operates in a mode that allows users to activate other windows in the same application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="662dd-160"><xref:System.Windows.Window.ShowDialog%2A> je volána k modálně otevřít windows, jako například dialogová okna.</span><span class="sxs-lookup"><span data-stu-id="662dd-160"><xref:System.Windows.Window.ShowDialog%2A> is called to open windows such as dialog boxes modally.</span></span> <span data-ttu-id="662dd-161">Zobrazit [přehled dialogových oken](dialog-boxes-overview.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="662dd-161">See [Dialog Boxes Overview](dialog-boxes-overview.md) for more information.</span></span>  
  
 <span data-ttu-id="662dd-162">Když <xref:System.Windows.Window.Show%2A> je volána, okno provádí inicializace předtím, než se zobrazí k vytvoření infrastruktury, které umožňuje přijímat uživatelský vstup.</span><span class="sxs-lookup"><span data-stu-id="662dd-162">When <xref:System.Windows.Window.Show%2A> is called, a window performs initialization work before it is shown to establish infrastructure that allows it to receive user input.</span></span> <span data-ttu-id="662dd-163">Při inicializaci okna <xref:System.Windows.Window.SourceInitialized> událost se vyvolá, a zobrazí se okno.</span><span class="sxs-lookup"><span data-stu-id="662dd-163">When the window is initialized, the <xref:System.Windows.Window.SourceInitialized> event is raised and the window is shown.</span></span>  
  
 <span data-ttu-id="662dd-164">Jako zástupce <xref:System.Windows.Application.StartupUri%2A> lze nastavit k určení první okno, které se automaticky otevře při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="662dd-164">As a shortcut, <xref:System.Windows.Application.StartupUri%2A> can be set to specify the first window that is opened automatically when an application starts.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 <span data-ttu-id="662dd-165">Při spuštění aplikace, okna zadanou hodnotou <xref:System.Windows.Application.StartupUri%2A> otevření modelessly; interně, voláním otevření okna jeho <xref:System.Windows.Window.Show%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="662dd-165">When the application starts, the window specified by the value of <xref:System.Windows.Application.StartupUri%2A> is opened modelessly; internally, the window is opened by calling its <xref:System.Windows.Window.Show%2A> method.</span></span>  
  
<a name="Ownership"></a>   
#### <a name="window-ownership"></a><span data-ttu-id="662dd-166">Okno vlastnictví</span><span class="sxs-lookup"><span data-stu-id="662dd-166">Window Ownership</span></span>  
 <span data-ttu-id="662dd-167">Okno, které se otevře pomocí <xref:System.Windows.Window.Show%2A> metoda nemá implicitní vztah s oknem, který byl vytvořen, mohou uživatelé komunikovat s kterékoli z těchto oken nezávisle na druhé, což znamená, že některé okno můžete dělat tyto věci:</span><span class="sxs-lookup"><span data-stu-id="662dd-167">A window that is opened by using the <xref:System.Windows.Window.Show%2A> method does not have an implicit relationship with the window that created it; users can interact with either window independently of the other, which means that either window can do the following:</span></span>  
  
- <span data-ttu-id="662dd-168">Na druhou (Pokud některý ze systému windows má jeho <xref:System.Windows.Window.Topmost%2A> nastavenou na `true`).</span><span class="sxs-lookup"><span data-stu-id="662dd-168">Cover the other (unless one of the windows has its <xref:System.Windows.Window.Topmost%2A> property set to `true`).</span></span>  
  
- <span data-ttu-id="662dd-169">Minimalizovat, zachovat maximalizované a obnovit, aniž by to ovlivnilo druhé.</span><span class="sxs-lookup"><span data-stu-id="662dd-169">Be minimized, maximized, and restored without affecting the other.</span></span>  
  
 <span data-ttu-id="662dd-170">Některé windows vyžadují vztah s oknem je otevře.</span><span class="sxs-lookup"><span data-stu-id="662dd-170">Some windows require a relationship with the window that opens them.</span></span> <span data-ttu-id="662dd-171">Například [!INCLUDE[TLA#tla_ide](../../../../includes/tlasharptla-ide-md.md)] aplikace může zobrazit vlastnosti windows a okna nástrojů, jehož chování typické je zahrnují okna, která je vytvořila.</span><span class="sxs-lookup"><span data-stu-id="662dd-171">For example, an [!INCLUDE[TLA#tla_ide](../../../../includes/tlasharptla-ide-md.md)] application may open property windows and tool windows whose typical behavior is to cover the window that creates them.</span></span> <span data-ttu-id="662dd-172">Kromě toho taková okna by měl vždy zavřít, minimalizovat, maximalizovat a obnovit společně s oknem, které byly vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="662dd-172">Furthermore, such windows should always close, minimize, maximize, and restore in concert with the window that created them.</span></span> <span data-ttu-id="662dd-173">Takové vztah lze navázat tak, že jedno okno *vlastní* jiného a dosáhnout tak, že nastavíte <xref:System.Windows.Window.Owner%2A> vlastnost *vlastní okno* s odkazem na *vlastníka okno*.</span><span class="sxs-lookup"><span data-stu-id="662dd-173">Such a relationship can be established by making one window *own* another, and is achieved by setting the <xref:System.Windows.Window.Owner%2A> property of the *owned window* with a reference to the *owner window*.</span></span> <span data-ttu-id="662dd-174">To je ukázáno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="662dd-174">This is shown in the following example.</span></span>  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 <span data-ttu-id="662dd-175">Po navázání vlastnictví:</span><span class="sxs-lookup"><span data-stu-id="662dd-175">After ownership is established:</span></span>  
  
- <span data-ttu-id="662dd-176">Vlastní okno může odkazovat jeho nadřazenému oknu zkontrolováním hodnota jeho <xref:System.Windows.Window.Owner%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="662dd-176">The owned window can reference its owner window by inspecting the value of its <xref:System.Windows.Window.Owner%2A> property.</span></span>  
  
- <span data-ttu-id="662dd-177">Okno vlastníka může zjišťovat všechna okna vlastní hodnotu zkontrolováním jeho <xref:System.Windows.Window.OwnedWindows%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="662dd-177">The owner window can discover all the windows it owns by inspecting the value of its <xref:System.Windows.Window.OwnedWindows%2A> property.</span></span>  
  
<a name="Preventing"></a>   
#### <a name="preventing-window-activation"></a><span data-ttu-id="662dd-178">Brání aktivaci okno</span><span class="sxs-lookup"><span data-stu-id="662dd-178">Preventing Window Activation</span></span>  
 <span data-ttu-id="662dd-179">Existují scénáře, kde by neměl systém windows aktivovat, když je vidět, jako je například konverzace windows messenger – vizuální styl internetovou aplikaci nebo windows oznámení e-mailové aplikace.</span><span class="sxs-lookup"><span data-stu-id="662dd-179">There are scenarios where windows should not be activated when shown, such as conversation windows of an Internet messenger-style application or notification windows of an email application.</span></span>  
  
 <span data-ttu-id="662dd-180">Pokud vaše aplikace má okno, které by neměly aktivovat, když je znázorněno, můžete nastavit jeho <xref:System.Windows.Window.ShowActivated%2A> vlastnost `false` před voláním <xref:System.Windows.Window.Show%2A> metoda poprvé.</span><span class="sxs-lookup"><span data-stu-id="662dd-180">If your application has a window that shouldn't be activated when shown, you can set its <xref:System.Windows.Window.ShowActivated%2A> property to `false` before calling the <xref:System.Windows.Window.Show%2A> method for the first time.</span></span> <span data-ttu-id="662dd-181">V důsledku:</span><span class="sxs-lookup"><span data-stu-id="662dd-181">As a consequence:</span></span>  
  
- <span data-ttu-id="662dd-182">V okně se neaktivuje.</span><span class="sxs-lookup"><span data-stu-id="662dd-182">The window is not activated.</span></span>  
  
- <span data-ttu-id="662dd-183">V okně <xref:System.Windows.Window.Activated> není vyvolána událost.</span><span class="sxs-lookup"><span data-stu-id="662dd-183">The window's <xref:System.Windows.Window.Activated> event is not raised.</span></span>  
  
- <span data-ttu-id="662dd-184">Aktuálně aktivovaná okno zůstane aktivovaná.</span><span class="sxs-lookup"><span data-stu-id="662dd-184">The currently activated window remains activated.</span></span>  
  
 <span data-ttu-id="662dd-185">V okně se aktivuje, ale ihned poté, co uživatel aktivuje klepnutím na klienta nebo neklientská oblast.</span><span class="sxs-lookup"><span data-stu-id="662dd-185">The window will become activated, however, as soon as the user activates it by clicking either the client or non-client area.</span></span> <span data-ttu-id="662dd-186">V tomto případě:</span><span class="sxs-lookup"><span data-stu-id="662dd-186">In this case:</span></span>  
  
- <span data-ttu-id="662dd-187">Okno se aktivuje.</span><span class="sxs-lookup"><span data-stu-id="662dd-187">The window is activated.</span></span>  
  
- <span data-ttu-id="662dd-188">V okně <xref:System.Windows.Window.Activated> událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="662dd-188">The window's <xref:System.Windows.Window.Activated> event is raised.</span></span>  
  
- <span data-ttu-id="662dd-189">Dříve aktivovaná je deaktivováno.</span><span class="sxs-lookup"><span data-stu-id="662dd-189">The previously activated window is deactivated.</span></span>  
  
- <span data-ttu-id="662dd-190">V okně <xref:System.Windows.Window.Deactivated> a <xref:System.Windows.Window.Activated> následně vyvolány události podle očekávání v reakci na akce uživatele.</span><span class="sxs-lookup"><span data-stu-id="662dd-190">The window's <xref:System.Windows.Window.Deactivated> and <xref:System.Windows.Window.Activated> events are subsequently raised as expected in response to user actions.</span></span>  
  
<a name="Window_Activation"></a>   
### <a name="window-activation"></a><span data-ttu-id="662dd-191">Okno Aktivace</span><span class="sxs-lookup"><span data-stu-id="662dd-191">Window Activation</span></span>  
 <span data-ttu-id="662dd-192">Při prvním otevření okna stane aktivní okno (Pokud se zobrazí s <xref:System.Windows.Window.ShowActivated%2A> nastavena na `false`).</span><span class="sxs-lookup"><span data-stu-id="662dd-192">When a window is first opened, it becomes the active window (unless it is shown with <xref:System.Windows.Window.ShowActivated%2A> set to `false`).</span></span> <span data-ttu-id="662dd-193">*Aktivní okno* je okno, které je aktuálně zachytávání vstupu uživatele, jako je například klávesnicí a myší.</span><span class="sxs-lookup"><span data-stu-id="662dd-193">The *active window* is the window that is currently capturing user input, such as key strokes and mouse clicks.</span></span> <span data-ttu-id="662dd-194">Pokud se okno stane aktivní, vyvolá <xref:System.Windows.Window.Activated> událostí.</span><span class="sxs-lookup"><span data-stu-id="662dd-194">When a window becomes active, it raises the <xref:System.Windows.Window.Activated> event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="662dd-195">Při prvním otevření okna <xref:System.Windows.FrameworkElement.Loaded> a <xref:System.Windows.Window.ContentRendered> až poté, co jsou vyvolány události <xref:System.Windows.Window.Activated> událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="662dd-195">When a window is first opened, the <xref:System.Windows.FrameworkElement.Loaded> and <xref:System.Windows.Window.ContentRendered> events are raised only after the <xref:System.Windows.Window.Activated> event is raised.</span></span> <span data-ttu-id="662dd-196">S myslete na to, okno lze účinně považovat za při otevření <xref:System.Windows.Window.ContentRendered> je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="662dd-196">With this in mind, a window can effectively be considered opened when <xref:System.Windows.Window.ContentRendered> is raised.</span></span>  
  
 <span data-ttu-id="662dd-197">Poté, co se okno stane aktivní, uživatel může aktivovat další okno ve stejné aplikaci, nebo jiná aplikace.</span><span class="sxs-lookup"><span data-stu-id="662dd-197">After a window becomes active, a user can activate another window in the same application, or activate another application.</span></span> <span data-ttu-id="662dd-198">Pokud k tomu dojde, aktuálně aktivní okno stane deaktivováno a vyvolá <xref:System.Windows.Window.Deactivated> událostí.</span><span class="sxs-lookup"><span data-stu-id="662dd-198">When that happens, the currently active window becomes deactivated and raises the <xref:System.Windows.Window.Deactivated> event.</span></span> <span data-ttu-id="662dd-199">Podobně, když uživatel vybere aktuálně deaktivované okno, v okně opět aktivní a <xref:System.Windows.Window.Activated> je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="662dd-199">Likewise, when the user selects a currently deactivated window, the window becomes active again and <xref:System.Windows.Window.Activated> is raised.</span></span>  
  
 <span data-ttu-id="662dd-200">Jedním z běžných důvodů pro zpracování <xref:System.Windows.Window.Activated> a <xref:System.Windows.Window.Deactivated> je můžete povolit nebo zakázat funkce, které lze spustit pouze když je aktivní okno.</span><span class="sxs-lookup"><span data-stu-id="662dd-200">One common reason to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> is to enable and disable functionality that can only run when a window is active.</span></span> <span data-ttu-id="662dd-201">Například některé windows zobrazit interaktivní obsah, který vyžaduje vstup uživatele konstantní nebo pozornost, včetně hry a přehrávačů videa.</span><span class="sxs-lookup"><span data-stu-id="662dd-201">For example, some windows display interactive content that requires constant user input or attention, including games and video players.</span></span> <span data-ttu-id="662dd-202">Následující příklad je zjednodušený video přehrávač, který ukazuje, jak zpracovat <xref:System.Windows.Window.Activated> a <xref:System.Windows.Window.Deactivated> k implementaci tohoto chování.</span><span class="sxs-lookup"><span data-stu-id="662dd-202">The following example is a simplified video player that demonstrates how to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> to implement this behavior.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 <span data-ttu-id="662dd-203">Další typy aplikací může stále spuštění kódu na pozadí při deaktivaci časového období.</span><span class="sxs-lookup"><span data-stu-id="662dd-203">Other types of applications may still run code in the background when a window is deactivated.</span></span> <span data-ttu-id="662dd-204">Například poštovní klient může pokračovat v dotazování poštovní server, když uživatel používá jiné aplikace.</span><span class="sxs-lookup"><span data-stu-id="662dd-204">For example, a mail client may continue polling the mail server while the user is using other applications.</span></span> <span data-ttu-id="662dd-205">Aplikace, jako jsou tyto často poskytují odlišných nebo dodatečných chování, zatímco je deaktivováno hlavního okna.</span><span class="sxs-lookup"><span data-stu-id="662dd-205">Applications like these often provide different or additional behavior while the main window is deactivated.</span></span> <span data-ttu-id="662dd-206">S ohledem na program e-mailu to může znamenat přidání nové položky pošty do schránky doručených zpráv i přidání oznámení ikony na hlavním panelu systému.</span><span class="sxs-lookup"><span data-stu-id="662dd-206">With respect to the mail program, this may mean both adding the new mail item to the inbox and adding a notification icon to the system tray.</span></span> <span data-ttu-id="662dd-207">Ikona oznámení potřebovat zobrazí jenom při e-mailu okno není aktivní, které se dají určit pomocí kontroly <xref:System.Windows.Window.IsActive%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="662dd-207">A notification icon need only be displayed when the mail window isn't active, which can be determined by inspecting the <xref:System.Windows.Window.IsActive%2A> property.</span></span>  
  
 <span data-ttu-id="662dd-208">Pokud se dokončí úlohu na pozadí, okno chtít upozornit uživatele, více urgentně voláním <xref:System.Windows.Window.Activate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="662dd-208">If a background task completes, a window may want to notify the user more urgently by calling <xref:System.Windows.Window.Activate%2A> method.</span></span> <span data-ttu-id="662dd-209">Pokud uživatel pracuje s jinou aplikací aktivuje se, když <xref:System.Windows.Window.Activate%2A> nazývá bliká tlačítko na hlavním panelu okna.</span><span class="sxs-lookup"><span data-stu-id="662dd-209">If the user is interacting with another application activated when <xref:System.Windows.Window.Activate%2A> is called, the window's taskbar button flashes.</span></span> <span data-ttu-id="662dd-210">Pokud uživatel pracuje s aktuální aplikace, volání <xref:System.Windows.Window.Activate%2A> přinese okno na popředí.</span><span class="sxs-lookup"><span data-stu-id="662dd-210">If a user is interacting with the current application, calling <xref:System.Windows.Window.Activate%2A> will bring the window to the foreground.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="662dd-211">Můžete zpracovat pomocí aktivace oboru aplikace <xref:System.Windows.Application.Activated?displayProperty=nameWithType> a <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> události.</span><span class="sxs-lookup"><span data-stu-id="662dd-211">You can handle application-scope activation using the <xref:System.Windows.Application.Activated?displayProperty=nameWithType> and <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> events.</span></span>  
  
<a name="Closing_a_Window"></a>   
### <a name="closing-a-window"></a><span data-ttu-id="662dd-212">Zavřením okna</span><span class="sxs-lookup"><span data-stu-id="662dd-212">Closing a Window</span></span>  
 <span data-ttu-id="662dd-213">Životnost časového období začíná už skončí, když uživatel zavře.</span><span class="sxs-lookup"><span data-stu-id="662dd-213">The life of a window starts coming to an end when a user closes it.</span></span> <span data-ttu-id="662dd-214">Zavřením okna za použití prvků v neklientské oblasti, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="662dd-214">A window can be closed by using elements in the non-client area, including the following:</span></span>  
  
- <span data-ttu-id="662dd-215">**Zavřít** položku **systému** nabídky.</span><span class="sxs-lookup"><span data-stu-id="662dd-215">The **Close** item of the **System** menu.</span></span>  
  
- <span data-ttu-id="662dd-216">Stisknutím klávesy ALT + F4.</span><span class="sxs-lookup"><span data-stu-id="662dd-216">Pressing ALT+F4.</span></span>  
  
- <span data-ttu-id="662dd-217">Stisknutím klávesy **Zavřít** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="662dd-217">Pressing the **Close** button.</span></span>  
  
 <span data-ttu-id="662dd-218">Můžete zadat další mechanismy pro klientskou oblast okna, zavřete další běžné nástroje, které zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="662dd-218">You can provide additional mechanisms to the client area to close a window, the more common of which include the following:</span></span>  
  
- <span data-ttu-id="662dd-219">**Ukončovací** položky v **souboru** nabídky, obvykle hlavní aplikaci pro windows.</span><span class="sxs-lookup"><span data-stu-id="662dd-219">An **Exit** item in the **File** menu, typically for main application windows.</span></span>  
  
- <span data-ttu-id="662dd-220">A **Zavřít** položky v **souboru** nabídky, obvykle na sekundární oknu.</span><span class="sxs-lookup"><span data-stu-id="662dd-220">A **Close** item in the **File** menu, typically on a secondary application window.</span></span>  
  
- <span data-ttu-id="662dd-221">A **zrušit** tlačítko, obvykle na modální dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="662dd-221">A **Cancel** button, typically on a modal dialog box.</span></span>  
  
- <span data-ttu-id="662dd-222">A **Zavřít** tlačítko, obvykle na nemodální dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="662dd-222">A **Close** button, typically on a modeless dialog box.</span></span>  
  
 <span data-ttu-id="662dd-223">Zavřete okno v reakci na jednu z těchto mechanismů vlastní, musíte zavolat <xref:System.Windows.Window.Close%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="662dd-223">To close a window in response to one of these custom mechanisms, you need to call the <xref:System.Windows.Window.Close%2A> method.</span></span> <span data-ttu-id="662dd-224">Následující příklad implementuje možnost Zavřít okno výběrem **ukončovací** na **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="662dd-224">The following example implements the ability to close a window by choosing the **Exit** on the **File** menu.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 <span data-ttu-id="662dd-225">Po zavření okna vyvolává dvě události: <xref:System.Windows.Window.Closing> a <xref:System.Windows.Window.Closed>.</span><span class="sxs-lookup"><span data-stu-id="662dd-225">When a window closes, it raises two events: <xref:System.Windows.Window.Closing> and <xref:System.Windows.Window.Closed>.</span></span>  
  
 <span data-ttu-id="662dd-226"><xref:System.Windows.Window.Closing> je aktivována před okno se zavře a poskytuje mechanismus, podle které okno jde zakázat uzavření.</span><span class="sxs-lookup"><span data-stu-id="662dd-226"><xref:System.Windows.Window.Closing> is raised before the window closes, and it provides a mechanism by which window closure can be prevented.</span></span> <span data-ttu-id="662dd-227">Jedním z běžných důvodů zabránit zavření okna je, pokud obsahu okna obsahuje upravený data.</span><span class="sxs-lookup"><span data-stu-id="662dd-227">One common reason to prevent window closure is if window content contains modified data.</span></span> <span data-ttu-id="662dd-228">V takovém případě <xref:System.Windows.Window.Closing> události může být zpracována pro určení, zda je nekonzistentní data a pokud ano, chcete-li požádat uživatele, zda chcete pokračovat bez uložení dat zavření okna nebo zrušení zavření okna.</span><span class="sxs-lookup"><span data-stu-id="662dd-228">In this situation, the <xref:System.Windows.Window.Closing> event can be handled to determine whether data is dirty and, if so, to ask the user whether to either continue closing the window without saving the data or to cancel window closure.</span></span> <span data-ttu-id="662dd-229">Následující příklad ukazuje klíčové aspekty zpracování <xref:System.Windows.Window.Closing>.</span><span class="sxs-lookup"><span data-stu-id="662dd-229">The following example shows the key aspects of handling <xref:System.Windows.Window.Closing>.</span></span>  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 <span data-ttu-id="662dd-230"><xref:System.Windows.Window.Closing> Je předána obslužné rutiny události <xref:System.ComponentModel.CancelEventArgs>, která implementuje `Boolean` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> vlastnost, která nastavíte na `true` zabránit okno zavřít.</span><span class="sxs-lookup"><span data-stu-id="662dd-230">The <xref:System.Windows.Window.Closing> event handler is passed a <xref:System.ComponentModel.CancelEventArgs>, which implements the `Boolean`<xref:System.ComponentModel.CancelEventArgs.Cancel%2A> property that you set to `true` to prevent a window from closing.</span></span>  
  
 <span data-ttu-id="662dd-231">Pokud <xref:System.Windows.Window.Closing> není zpracována, nebo je zpracována, ale není zrušena, okno se zavře.</span><span class="sxs-lookup"><span data-stu-id="662dd-231">If <xref:System.Windows.Window.Closing> is not handled, or it is handled but not canceled, the window will close.</span></span> <span data-ttu-id="662dd-232">Těsně před plánovaným začátkem skutečně okno zavře, <xref:System.Windows.Window.Closed> je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="662dd-232">Just before a window actually closes, <xref:System.Windows.Window.Closed> is raised.</span></span> <span data-ttu-id="662dd-233">V tuto chvíli nelze zabránit okno zabrání v uzavření.</span><span class="sxs-lookup"><span data-stu-id="662dd-233">At this point, a window cannot be prevented from closing.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="662dd-234">Aplikace může být nakonfigurována pro vypnutí automaticky když buď hlavního okna aplikace se zavře (viz <xref:System.Windows.Application.MainWindow%2A>) nebo poslední okno se zavře.</span><span class="sxs-lookup"><span data-stu-id="662dd-234">An application can be configured to shut down automatically when either the main application window closes (see <xref:System.Windows.Application.MainWindow%2A>) or the last window closes.</span></span> <span data-ttu-id="662dd-235">Podrobnosti najdete v tématu <xref:System.Windows.Application.ShutdownMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="662dd-235">For details, see <xref:System.Windows.Application.ShutdownMode%2A>.</span></span>  
  
 <span data-ttu-id="662dd-236">Během časového období můžete explicitně ukončeno prostřednictvím mechanismů poskytnutých v oblasti neklientských a klienta, okna můžete také být implicitně uzavřen, v důsledku chování v ostatních částech aplikace nebo [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="662dd-236">While a window can be explicitly closed through mechanisms provided in the non-client and client areas, a window can also be implicitly closed as a result of behavior in other parts of the application or [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], including the following:</span></span>  
  
- <span data-ttu-id="662dd-237">Uživatel odhlásí nebo ukončí Windows.</span><span class="sxs-lookup"><span data-stu-id="662dd-237">A user logs off or shuts down Windows.</span></span>  
  
- <span data-ttu-id="662dd-238">Zavření okna vlastníka (viz <xref:System.Windows.Window.Owner%2A>).</span><span class="sxs-lookup"><span data-stu-id="662dd-238">A window's owner closes (see <xref:System.Windows.Window.Owner%2A>).</span></span>  
  
- <span data-ttu-id="662dd-239">Zavření hlavního okna aplikace a <xref:System.Windows.Application.ShutdownMode%2A> je <xref:System.Windows.ShutdownMode.OnMainWindowClose>.</span><span class="sxs-lookup"><span data-stu-id="662dd-239">The main application window is closed and <xref:System.Windows.Application.ShutdownMode%2A> is <xref:System.Windows.ShutdownMode.OnMainWindowClose>.</span></span>  
  
- <span data-ttu-id="662dd-240"><xref:System.Windows.Application.Shutdown%2A> je volána.</span><span class="sxs-lookup"><span data-stu-id="662dd-240"><xref:System.Windows.Application.Shutdown%2A> is called.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="662dd-241">Nelze znovu otevřít časové období, po jeho zavření.</span><span class="sxs-lookup"><span data-stu-id="662dd-241">A window cannot be reopened after it is closed.</span></span>  
  
<a name="Window_Lifetime_Events"></a>   
### <a name="window-lifetime-events"></a><span data-ttu-id="662dd-242">Události doby života okno</span><span class="sxs-lookup"><span data-stu-id="662dd-242">Window Lifetime Events</span></span>  
 <span data-ttu-id="662dd-243">Následující obrázek znázorňuje posloupnost událostí instančního objektu v životnost časového období:</span><span class="sxs-lookup"><span data-stu-id="662dd-243">The following illustration shows the sequence of the principal events in the lifetime of a window:</span></span>  
  
 ![Diagram, který zobrazuje události do okna životnost.](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 <span data-ttu-id="662dd-245">Následující obrázek znázorňuje posloupnost událostí instančního objektu v době životnosti okno, které se zobrazí bez aktivace (<xref:System.Windows.Window.ShowActivated%2A> je nastavena na `false` předtím, než se zobrazí v okně):</span><span class="sxs-lookup"><span data-stu-id="662dd-245">The following illustration shows the sequence of the principal events in the lifetime of a window that is shown without activation (<xref:System.Windows.Window.ShowActivated%2A> is set to `false` before the window is shown):</span></span>  
  
 ![Diagram, který zobrazuje události do okna životnost bez aktivace.](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>   
## <a name="window-location"></a><span data-ttu-id="662dd-247">Umístění okna</span><span class="sxs-lookup"><span data-stu-id="662dd-247">Window Location</span></span>  
 <span data-ttu-id="662dd-248">Při otevření okna má umístění v x a y dimenze vzhledem k pracovní ploše.</span><span class="sxs-lookup"><span data-stu-id="662dd-248">While a window is open, it has a location in the x and y dimensions relative to the desktop.</span></span> <span data-ttu-id="662dd-249">Toto umístění se dají určit pomocí kontroly <xref:System.Windows.Window.Left%2A> a <xref:System.Windows.Window.Top%2A> vlastnosti, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="662dd-249">This location can be determined by inspecting the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties, respectively.</span></span> <span data-ttu-id="662dd-250">Můžete nastavit tyto vlastnosti chcete změnit umístění okna.</span><span class="sxs-lookup"><span data-stu-id="662dd-250">You can set these properties to change the location of the window.</span></span>  
  
 <span data-ttu-id="662dd-251">Můžete také zadat počáteční umístění <xref:System.Windows.Window> při prvním zobrazení tak, že nastavíte <xref:System.Windows.Window.WindowStartupLocation%2A> vlastnosti s jednou z následujících <xref:System.Windows.WindowStartupLocation> hodnot výčtu:</span><span class="sxs-lookup"><span data-stu-id="662dd-251">You can also specify the initial location of a <xref:System.Windows.Window> when it first appears by setting the <xref:System.Windows.Window.WindowStartupLocation%2A> property with one of the following <xref:System.Windows.WindowStartupLocation> enumeration values:</span></span>  
  
- <span data-ttu-id="662dd-252"><xref:System.Windows.WindowStartupLocation.CenterOwner> (výchozí)</span><span class="sxs-lookup"><span data-stu-id="662dd-252"><xref:System.Windows.WindowStartupLocation.CenterOwner> (default)</span></span>  
  
- <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
- <xref:System.Windows.WindowStartupLocation.Manual>  
  
 <span data-ttu-id="662dd-253">Pokud umístění při spuštění je zadán jako <xref:System.Windows.WindowStartupLocation.Manual>a <xref:System.Windows.Window.Left%2A> a <xref:System.Windows.Window.Top%2A> nebyly nastaveny vlastnosti, <xref:System.Windows.Window> požádá Windows se zobrazí v pro umístění.</span><span class="sxs-lookup"><span data-stu-id="662dd-253">If the startup location is specified as <xref:System.Windows.WindowStartupLocation.Manual>, and the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties have not been set, <xref:System.Windows.Window> will ask Windows for a location to appear in.</span></span>  
  
<a name="Topmost_Windows_and_Z_Order"></a>   
### <a name="topmost-windows-and-z-order"></a><span data-ttu-id="662dd-254">Nejvyšší Windows a pořadí Z-Order</span><span class="sxs-lookup"><span data-stu-id="662dd-254">Topmost Windows and Z-Order</span></span>  
 <span data-ttu-id="662dd-255">Kromě nutnosti x a y umístění, okno má také umístění z dimenze, která určuje svislé polohy s ohledem na ostatní okna.</span><span class="sxs-lookup"><span data-stu-id="662dd-255">Besides having an x and y location, a window also has a location in the z dimension, which determines its vertical position with respect to other windows.</span></span> <span data-ttu-id="662dd-256">To se označuje jako pořadí vykreslování v okně a existují dva typy: Normální pořadí vykreslování a nejvyšší pořadí vykreslování.</span><span class="sxs-lookup"><span data-stu-id="662dd-256">This is known as the window's z-order, and there are two types: normal z-order and topmost z-order.</span></span> <span data-ttu-id="662dd-257">Umístění okna *normální pořadí vykreslování* je určeno bez ohledu na to, zda je aktuálně aktivní.</span><span class="sxs-lookup"><span data-stu-id="662dd-257">The location of a window in the *normal z-order* is determined by whether it is currently active or not.</span></span> <span data-ttu-id="662dd-258">Ve výchozím nastavení okno se nachází v normální pořadí vykreslování.</span><span class="sxs-lookup"><span data-stu-id="662dd-258">By default, a window is located in the normal z-order.</span></span> <span data-ttu-id="662dd-259">Umístění okna *nejvyšší pořadí vykreslování* je také určeno bez ohledu na to, zda je aktuálně aktivní.</span><span class="sxs-lookup"><span data-stu-id="662dd-259">The location of a window in the *topmost z-order* is also determined by whether it is currently active or not.</span></span> <span data-ttu-id="662dd-260">Kromě toho windows v nejvyšší pořadí vykreslování jsou vždy umístěné nad windows v normálním pořadí vykreslování.</span><span class="sxs-lookup"><span data-stu-id="662dd-260">Furthermore, windows in the topmost z-order are always located above windows in the normal z-order.</span></span> <span data-ttu-id="662dd-261">Okno se nachází v nejvyšší pořadí vykreslování nastavením jeho <xref:System.Windows.Window.Topmost%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="662dd-261">A window is located in the topmost z-order by setting its <xref:System.Windows.Window.Topmost%2A> property to `true`.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 <span data-ttu-id="662dd-262">V rámci každého pořadí vykreslování aktuálně aktivní okno zobrazuje nad všemi ostatními okny ve stejném pořadí vykreslování.</span><span class="sxs-lookup"><span data-stu-id="662dd-262">Within each z-order, the currently active window appears above all other windows in the same z-order.</span></span>  
  
<a name="WindowSize"></a>   
## <a name="window-size"></a><span data-ttu-id="662dd-263">Velikost okna</span><span class="sxs-lookup"><span data-stu-id="662dd-263">Window Size</span></span>  
 <span data-ttu-id="662dd-264">Kromě nutnosti klasické pracovní plochy umístění, okno má velikost, která je určena podle několika vlastností, včetně různé vlastnosti šířku a výšku a <xref:System.Windows.Window.SizeToContent%2A>.</span><span class="sxs-lookup"><span data-stu-id="662dd-264">Besides having a desktop location, a window has a size that is determined by several properties, including the various width and height properties and <xref:System.Windows.Window.SizeToContent%2A>.</span></span>  
  
 <span data-ttu-id="662dd-265"><xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, a <xref:System.Windows.FrameworkElement.MaxWidth%2A> se používají ke správě škálu šířek, které může mít během celé jeho životnosti okna a konfiguraci, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="662dd-265"><xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.MaxWidth%2A> are used to manage the range of widths that a window can have during its lifetime, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 <span data-ttu-id="662dd-266">Spravuje výšku okna <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, a <xref:System.Windows.FrameworkElement.MaxHeight%2A>a konfiguraci, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="662dd-266">Window height is managed by <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, and <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 <span data-ttu-id="662dd-267">Protože různé hodnoty šířku a výšku hodnoty určit rozsah, je možné pro šířku a výšku umožňující změnu velikosti okna musí být kdekoli v zadaném rozsahu pro odpovídající dimenzi.</span><span class="sxs-lookup"><span data-stu-id="662dd-267">Because the various width values and height values each specify a range, it is possible for the width and height of a resizable window to be anywhere within the specified range for the respective dimension.</span></span> <span data-ttu-id="662dd-268">Ke zjištění svou aktuální šířku a výšku, zkontrolujte <xref:System.Windows.FrameworkElement.ActualWidth%2A> a <xref:System.Windows.FrameworkElement.ActualHeight%2A>v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="662dd-268">To detect its current width and height, inspect <xref:System.Windows.FrameworkElement.ActualWidth%2A> and <xref:System.Windows.FrameworkElement.ActualHeight%2A>, respectively.</span></span>  
  
 <span data-ttu-id="662dd-269">Pokud chcete šířku a výšku okna mít vhodnou velikost okna velikost obsahu, můžete použít <xref:System.Windows.Window.SizeToContent%2A> vlastnost, která má následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="662dd-269">If you'd like the width and height of your window to have a size that fits to the size of the window's content, you can use the <xref:System.Windows.Window.SizeToContent%2A> property, which has the following values:</span></span>  
  
- <span data-ttu-id="662dd-270"><xref:System.Windows.SizeToContent.Manual>.</span><span class="sxs-lookup"><span data-stu-id="662dd-270"><xref:System.Windows.SizeToContent.Manual>.</span></span> <span data-ttu-id="662dd-271">Žádný vliv (výchozí).</span><span class="sxs-lookup"><span data-stu-id="662dd-271">No effect (default).</span></span>  
  
- <span data-ttu-id="662dd-272"><xref:System.Windows.SizeToContent.Width>.</span><span class="sxs-lookup"><span data-stu-id="662dd-272"><xref:System.Windows.SizeToContent.Width>.</span></span> <span data-ttu-id="662dd-273">Přizpůsobit šířce obsahu, který má stejný účinek jako nastavení obě <xref:System.Windows.FrameworkElement.MinWidth%2A> a <xref:System.Windows.FrameworkElement.MaxWidth%2A> šířku obsahu.</span><span class="sxs-lookup"><span data-stu-id="662dd-273">Fit to content width, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
- <span data-ttu-id="662dd-274"><xref:System.Windows.SizeToContent.Height>.</span><span class="sxs-lookup"><span data-stu-id="662dd-274"><xref:System.Windows.SizeToContent.Height>.</span></span> <span data-ttu-id="662dd-275">Přizpůsobit na výšku obsahu, který má stejný účinek jako nastavení obě <xref:System.Windows.FrameworkElement.MinHeight%2A> a <xref:System.Windows.FrameworkElement.MaxHeight%2A> výškou obsahu.</span><span class="sxs-lookup"><span data-stu-id="662dd-275">Fit to content height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content.</span></span>  
  
- <span data-ttu-id="662dd-276"><xref:System.Windows.SizeToContent.WidthAndHeight>.</span><span class="sxs-lookup"><span data-stu-id="662dd-276"><xref:System.Windows.SizeToContent.WidthAndHeight>.</span></span> <span data-ttu-id="662dd-277">Přizpůsobit obsahu šířku a výšku, který má stejný účinek jako nastavení obě <xref:System.Windows.FrameworkElement.MinHeight%2A> a <xref:System.Windows.FrameworkElement.MaxHeight%2A> výškou obsahu a nastavení obě <xref:System.Windows.FrameworkElement.MinWidth%2A> a <xref:System.Windows.FrameworkElement.MaxWidth%2A> šířku obsahu.</span><span class="sxs-lookup"><span data-stu-id="662dd-277">Fit to content width and height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content, and setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
 <span data-ttu-id="662dd-278">Následující příklad ukazuje okno, která automaticky velikosti podle jeho obsah svisle nebo vodorovně, při prvním zobrazení.</span><span class="sxs-lookup"><span data-stu-id="662dd-278">The following example shows a window that automatically sizes to fit its content, both vertically and horizontally, when first shown.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 <span data-ttu-id="662dd-279">Následující příklad ukazuje, jak nastavit <xref:System.Windows.Window.SizeToContent%2A> vlastností v kódu k určení, jak změní velikost okna podle jeho obsahu.</span><span class="sxs-lookup"><span data-stu-id="662dd-279">The following example shows how to set the <xref:System.Windows.Window.SizeToContent%2A> property in code to specify how a window resizes to fit its content    .</span></span>
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>   
## <a name="order-of-precedence-for-sizing-properties"></a><span data-ttu-id="662dd-280">Pořadí priorit pro vlastností změny velikosti</span><span class="sxs-lookup"><span data-stu-id="662dd-280">Order of Precedence for Sizing Properties</span></span>  
 <span data-ttu-id="662dd-281">V podstatě kombinovat různé vlastnosti velikosti okna pro účely definování rozsahu šířky a výšky umožňující změnu velikosti okna.</span><span class="sxs-lookup"><span data-stu-id="662dd-281">Essentially, the various sizes properties of a window combine to define the range of width and height for a resizable window.</span></span> <span data-ttu-id="662dd-282">Aby byla zachována platný rozsah <xref:System.Windows.Window> vyhodnotí jako hodnoty vlastností velikost pomocí následujících pořadí priorit.</span><span class="sxs-lookup"><span data-stu-id="662dd-282">To ensure a valid range is maintained, <xref:System.Windows.Window> evaluates the values of the size properties using the following orders of precedence.</span></span>  
  
 <span data-ttu-id="662dd-283">**Pro vlastnosti Height:**</span><span class="sxs-lookup"><span data-stu-id="662dd-283">**For Height Properties:**</span></span>  
  
1. <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="662dd-284">**Pro vlastnosti Šířka:**</span><span class="sxs-lookup"><span data-stu-id="662dd-284">**For Width Properties:**</span></span>  
  
1. <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="662dd-285">Pořadí priorit můžete také určit velikost okna, když se maximalizuje, který se spravuje pomocí <xref:System.Windows.Window.WindowState%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="662dd-285">The order of precedence can also determine the size of a window when it is maximized, which is managed with the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="WindowState"></a>   
## <a name="window-state"></a><span data-ttu-id="662dd-286">Stav okna</span><span class="sxs-lookup"><span data-stu-id="662dd-286">Window State</span></span>  
 <span data-ttu-id="662dd-287">Po celou dobu životnosti umožňující změnu velikosti okna, může mít tři stavy: normální minimalizovány a maximalizovat.</span><span class="sxs-lookup"><span data-stu-id="662dd-287">During the lifetime of a resizable window, it can have three states: normal, minimized, and maximized.</span></span> <span data-ttu-id="662dd-288">Okno s *normální* stav je výchozí stav okna.</span><span class="sxs-lookup"><span data-stu-id="662dd-288">A window with a *normal* state is the default state of a window.</span></span> <span data-ttu-id="662dd-289">Okno s tímto stavem umožňuje uživateli umístění a velikost úchyt pro změnu nebo ohraničení, pokud je umožňující změnu velikosti.</span><span class="sxs-lookup"><span data-stu-id="662dd-289">A window with this state allows a user to move and resize it by using a resize grip or the border, if it is resizable.</span></span>  
  
 <span data-ttu-id="662dd-290">Okno s *minimalizovány* sbalí stavu na jeho tlačítko na hlavním panelu, pokud <xref:System.Windows.Window.ShowInTaskbar%2A> je nastavena na `true`; v opačném případě Hroutí k nejmenší velikost je to možné, může být a samotné přemístí do levého dolního rohu plochy.</span><span class="sxs-lookup"><span data-stu-id="662dd-290">A window with a *minimized* state collapses to its task bar button if <xref:System.Windows.Window.ShowInTaskbar%2A> is set to `true`; otherwise, it collapses to the smallest possible size it can be and relocates itself to the bottom-left corner of the desktop.</span></span> <span data-ttu-id="662dd-291">Ani typu minimalizované okno velikost lze změnit pomocí ohraničení nebo úchyt, i když můžete kolem ploše přetáhnout minimalizované okno, které se nezobrazuje na hlavním panelu.</span><span class="sxs-lookup"><span data-stu-id="662dd-291">Neither type of minimized window can be resized using a border or resize grip, although a minimized window that isn't shown in the task bar can be dragged around the desktop.</span></span>  
  
 <span data-ttu-id="662dd-292">Okno s *maximalizované* stavu rozšíří na maximální velikost může být, který může mít pouze stejně velké jako jeho <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, a <xref:System.Windows.Window.SizeToContent%2A> vlastnosti diktování.</span><span class="sxs-lookup"><span data-stu-id="662dd-292">A window with a *maximized* state expands to the maximum size it can be, which will only be as large as its <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and <xref:System.Windows.Window.SizeToContent%2A> properties dictate.</span></span> <span data-ttu-id="662dd-293">Například minimalizované okno maximalizované okno nelze změnit velikost úchyt pro změnu nebo přetažením ohraničení.</span><span class="sxs-lookup"><span data-stu-id="662dd-293">Like a minimized window, a maximized window cannot be resized by using a resize grip or by dragging the border.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="662dd-294">Hodnoty <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, a <xref:System.Windows.FrameworkElement.Height%2A> i v případě, že momentálně maximalizované nebo minimalizovat okno Vlastnosti okna vždy představují hodnoty pro normální stav.</span><span class="sxs-lookup"><span data-stu-id="662dd-294">The values of the <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.Height%2A> properties of a window always represent the values for the normal state, even when the window is currently maximized or minimized.</span></span>  
  
 <span data-ttu-id="662dd-295">Stav okna se dá nakonfigurovat pomocí nastavení jeho <xref:System.Windows.Window.WindowState%2A> vlastnost, která může mít jednu z následujících <xref:System.Windows.WindowState> hodnot výčtu:</span><span class="sxs-lookup"><span data-stu-id="662dd-295">The state of a window can be configured by setting its <xref:System.Windows.Window.WindowState%2A> property, which can have one of the following <xref:System.Windows.WindowState> enumeration values:</span></span>  
  
- <span data-ttu-id="662dd-296"><xref:System.Windows.WindowState.Normal> (výchozí)</span><span class="sxs-lookup"><span data-stu-id="662dd-296"><xref:System.Windows.WindowState.Normal> (default)</span></span>  
  
- <xref:System.Windows.WindowState.Maximized>  
  
- <xref:System.Windows.WindowState.Minimized>  
  
 <span data-ttu-id="662dd-297">Následující příklad ukazuje, jak vytvořit okno, které se zobrazí jako maximalizované, když se otevře.</span><span class="sxs-lookup"><span data-stu-id="662dd-297">The following example shows how to create a window that is shown as maximized when it opens.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 <span data-ttu-id="662dd-298">Obecně byste měli nastavit <xref:System.Windows.Window.WindowState%2A> nakonfigurovat počáteční stav okna.</span><span class="sxs-lookup"><span data-stu-id="662dd-298">In general, you should set <xref:System.Windows.Window.WindowState%2A> to configure the initial state of a window.</span></span> <span data-ttu-id="662dd-299">Jakmile se zobrazí okno s možností změny velikosti, uživatele stiskněte minimalizovat, maximalizovat a obnovit tlačítka na záhlaví okna. Chcete-li změnit stav okna.</span><span class="sxs-lookup"><span data-stu-id="662dd-299">Once a resizable window is shown, users can press the minimize, maximize, and restore buttons on the window's title bar to change the window state.</span></span>  
  
<a name="WindowAppearance"></a>   
## <a name="window-appearance"></a><span data-ttu-id="662dd-300">Okno Vzhled</span><span class="sxs-lookup"><span data-stu-id="662dd-300">Window Appearance</span></span>  
 <span data-ttu-id="662dd-301">Změna vzhledu klientské oblasti okna tak, že přidáte specifické pro okno obsah, jako jsou tlačítka a popisky, textová pole.</span><span class="sxs-lookup"><span data-stu-id="662dd-301">You change the appearance of the client area of a window by adding window-specific content to it, such as buttons, labels, and text boxes.</span></span> <span data-ttu-id="662dd-302">Ke konfiguraci neklientská oblast <xref:System.Windows.Window> poskytuje několik vlastností, které zahrnují <xref:System.Windows.Window.Icon%2A> nastavit ikonu okna a <xref:System.Windows.Window.Title%2A> nastavit její název.</span><span class="sxs-lookup"><span data-stu-id="662dd-302">To configure the non-client area, <xref:System.Windows.Window> provides several properties, which include <xref:System.Windows.Window.Icon%2A> to set a window's icon and <xref:System.Windows.Window.Title%2A> to set its title.</span></span>  
  
 <span data-ttu-id="662dd-303">Můžete také změnit vzhled a chování ohraničení neklientská oblast nakonfigurováním režim změny velikosti okna, styl okna, a určuje, zda je zobrazen jako tlačítko na panelu úkolů klasické pracovní plochy.</span><span class="sxs-lookup"><span data-stu-id="662dd-303">You can also change the appearance and behavior of non-client area border by configuring a window's resize mode, window style, and whether it appears as a button in the desktop task bar.</span></span>  

<a name="Resize_Mode"></a>   
### <a name="resize-mode"></a><span data-ttu-id="662dd-304">Změna velikosti režimu</span><span class="sxs-lookup"><span data-stu-id="662dd-304">Resize Mode</span></span>  
 <span data-ttu-id="662dd-305">V závislosti na tom <xref:System.Windows.Window.WindowStyle%2A> vlastností, můžete řídit jak (a zda) uživatelé mohou změnit výšku okna.</span><span class="sxs-lookup"><span data-stu-id="662dd-305">Depending on the <xref:System.Windows.Window.WindowStyle%2A> property, you can control how (and if) users can resize the window.</span></span> <span data-ttu-id="662dd-306">Volba Styl okna ovlivňuje, jestli uživatel může změnit velikost okna přetažením ohraničení pomocí myši, zda **minimalizovat**, **Maximalizovat**, a **změnit velikost** tlačítka zobrazí v neklientské oblasti, a pokud se zobrazí, zda jsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="662dd-306">The choice of window style affects whether a user can resize the window by dragging its border with the mouse, whether the **Minimize**, **Maximize**, and **Resize** buttons appear on the non-client area, and, if they do appear, whether they are enabled.</span></span>  
  
 <span data-ttu-id="662dd-307">Můžete nakonfigurovat, jak změní velikost okna tak, že nastavíte její <xref:System.Windows.Window.ResizeMode%2A> vlastnost, která může být jedna z následujících <xref:System.Windows.ResizeMode> hodnot výčtu:</span><span class="sxs-lookup"><span data-stu-id="662dd-307">You can configure how a window resizes by setting its <xref:System.Windows.Window.ResizeMode%2A> property, which can be one of the following <xref:System.Windows.ResizeMode> enumeration values:</span></span>  
  
- <xref:System.Windows.ResizeMode.NoResize>  
  
- <xref:System.Windows.ResizeMode.CanMinimize>  
  
- <span data-ttu-id="662dd-308"><xref:System.Windows.ResizeMode.CanResize> (výchozí)</span><span class="sxs-lookup"><span data-stu-id="662dd-308"><xref:System.Windows.ResizeMode.CanResize> (default)</span></span>  
  
- <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 <span data-ttu-id="662dd-309">Stejně jako u <xref:System.Windows.Window.WindowStyle%2A>, režim změny velikosti okna je pravděpodobně nebudou měnit během celé jeho životnosti, což znamená, že budete pravděpodobně ji nastavíte z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek.</span><span class="sxs-lookup"><span data-stu-id="662dd-309">As with <xref:System.Windows.Window.WindowStyle%2A>, the resize mode of a window is unlikely to change during its lifetime, which means that you'll most likely set it from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 <span data-ttu-id="662dd-310">Všimněte si, že můžete zjistit, zda je okno maximalizované, rychle minimalizovat nebo obnovit, že se podíváte <xref:System.Windows.Window.WindowState%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="662dd-310">Note that you can detect whether a window is maximized, minimized, or restored by inspecting the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="Window_Style"></a>   
### <a name="window-style"></a><span data-ttu-id="662dd-311">Styl okna</span><span class="sxs-lookup"><span data-stu-id="662dd-311">Window Style</span></span>  
 <span data-ttu-id="662dd-312">Ohraničení, která je vystavena v neklientské oblasti okna je vhodný pro většinu aplikací.</span><span class="sxs-lookup"><span data-stu-id="662dd-312">The border that is exposed from the non-client area of a window is suitable for most applications.</span></span> <span data-ttu-id="662dd-313">Existují však okolností, kde jsou potřebné různé druhy ohraničení nebo bez ohraničení nejsou vůbec potřeba v závislosti na typu okna.</span><span class="sxs-lookup"><span data-stu-id="662dd-313">However, there are circumstances where different types of borders are needed, or no borders are needed at all, depending on the type of window.</span></span>  
  
 <span data-ttu-id="662dd-314">Řídit, jaký typ ohraničení okna získá, nastavíte její <xref:System.Windows.Window.WindowStyle%2A> vlastnosti s jednou z následujících hodnot <xref:System.Windows.WindowStyle> výčtu:</span><span class="sxs-lookup"><span data-stu-id="662dd-314">To control what type of border a window gets, you set its <xref:System.Windows.Window.WindowStyle%2A> property with one of the following values of the <xref:System.Windows.WindowStyle> enumeration:</span></span>  
  
- <xref:System.Windows.WindowStyle.None>  
  
- <span data-ttu-id="662dd-315"><xref:System.Windows.WindowStyle.SingleBorderWindow> (výchozí)</span><span class="sxs-lookup"><span data-stu-id="662dd-315"><xref:System.Windows.WindowStyle.SingleBorderWindow> (default)</span></span>  
  
- <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
- <xref:System.Windows.WindowStyle.ToolWindow>  
  
 <span data-ttu-id="662dd-316">Vliv tyto styly oken jsou znázorněné na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="662dd-316">The effect of these window styles are illustrated in the following figure:</span></span>  
  
 ![Obrázek styly ohraničení okna.](./media/wpf-windows-overview/window-border-styles.png)  
  
 <span data-ttu-id="662dd-318">Můžete nastavit <xref:System.Windows.Window.WindowStyle%2A> buď pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek nebo kódu, protože nepravděpodobné, chcete-li změnit během životního cyklu okna, bude pravděpodobně nakonfigurujete pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek.</span><span class="sxs-lookup"><span data-stu-id="662dd-318">You can set <xref:System.Windows.Window.WindowStyle%2A> using either [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup or code; because it is unlikely to change during the lifetime of a window, you will most likely configure it using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a><span data-ttu-id="662dd-319">Styl neobdélníkových oken</span><span class="sxs-lookup"><span data-stu-id="662dd-319">Non-Rectangular Window Style</span></span>  
 <span data-ttu-id="662dd-320">Také existují situace, kdy styly ohraničení, které <xref:System.Windows.Window.WindowStyle%2A> umožňuje mít nestačí.</span><span class="sxs-lookup"><span data-stu-id="662dd-320">There are also situations where the border styles that <xref:System.Windows.Window.WindowStyle%2A> allows you to have are not sufficient.</span></span> <span data-ttu-id="662dd-321">Můžete například vytvořit aplikaci s neobdélníkových ohraničení, jako je [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] používá.</span><span class="sxs-lookup"><span data-stu-id="662dd-321">For example, you may want to create an application with a non-rectangular border, like [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] uses.</span></span>  
  
 <span data-ttu-id="662dd-322">Představte si třeba okně bublin řeči je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="662dd-322">For example, consider the speech bubble window shown in the following figure:</span></span>  
  
 ![Okno bublin řeči, s upozorněním přetáhněte Me.](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 <span data-ttu-id="662dd-324">Tento typ okna je vytvořit tak, že nastavíte <xref:System.Windows.Window.WindowStyle%2A> vlastnost <xref:System.Windows.WindowStyle.None>a pomocí speciální podporu, která <xref:System.Windows.Window> má transparentnosti.</span><span class="sxs-lookup"><span data-stu-id="662dd-324">This type of window can be created by setting the <xref:System.Windows.Window.WindowStyle%2A> property to <xref:System.Windows.WindowStyle.None>, and by using special support that <xref:System.Windows.Window> has for transparency.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 <span data-ttu-id="662dd-325">Tato kombinace hodnot instruuje okno k vykreslení zcela transparentní.</span><span class="sxs-lookup"><span data-stu-id="662dd-325">This combination of values instructs the window to render completely transparent.</span></span> <span data-ttu-id="662dd-326">V tomto stavu nelze použít v okně neklientská oblast vylepšení (Zavřít nabídku, tlačítka Minimalizovat, maximalizovat a obnovit a tak dále).</span><span class="sxs-lookup"><span data-stu-id="662dd-326">In this state, the window's non-client area adornments (the Close menu, Minimize, Maximize, and Restore buttons, and so on) cannot be used.</span></span> <span data-ttu-id="662dd-327">V důsledku toho budete muset zadat vlastní.</span><span class="sxs-lookup"><span data-stu-id="662dd-327">Consequently, you need to provide your own.</span></span>  
  
<a name="Task_Bar_Presence"></a>   
### <a name="task-bar-presence"></a><span data-ttu-id="662dd-328">Přítomnost hlavního panelu</span><span class="sxs-lookup"><span data-stu-id="662dd-328">Task Bar Presence</span></span>  

<span data-ttu-id="662dd-329">Výchozí vzhled okna obsahuje tlačítko na hlavním panelu, podobný jako na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="662dd-329">The default appearance of a window includes a taskbar button, like the one shown in the following figure:</span></span>

 ![Snímek obrazovky zobrazující okno s tlačítkem na hlavním panelu.](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 <span data-ttu-id="662dd-331">Některé typy windows nemají tlačítko na hlavním panelu, jako jsou okna se zprávou a dialogová okna (viz [přehled dialogových oken](dialog-boxes-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="662dd-331">Some types of windows don't have a task bar button, such as message boxes and dialog boxes (see [Dialog Boxes Overview](dialog-boxes-overview.md)).</span></span> <span data-ttu-id="662dd-332">Můžete řídit, zda je zobrazen tlačítko na hlavním panelu okna tak, že nastavíte <xref:System.Windows.Window.ShowInTaskbar%2A> vlastnosti (`true` ve výchozím nastavení).</span><span class="sxs-lookup"><span data-stu-id="662dd-332">You can control whether the task bar button for a window is shown by setting the <xref:System.Windows.Window.ShowInTaskbar%2A> property (`true` by default).</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations"></a><span data-ttu-id="662dd-333">Důležité informace o zabezpečení</span><span class="sxs-lookup"><span data-stu-id="662dd-333">Security Considerations</span></span>  
 <span data-ttu-id="662dd-334"><xref:System.Windows.Window> vyžaduje `UnmanagedCode` oprávnění zabezpečení, které má být vytvořena.</span><span class="sxs-lookup"><span data-stu-id="662dd-334"><xref:System.Windows.Window> requires `UnmanagedCode` security permission to be instantiated.</span></span> <span data-ttu-id="662dd-335">Pro aplikace nainstalované na a spustili z místního počítače to spadá do sady oprávnění, která jsou k aplikaci.</span><span class="sxs-lookup"><span data-stu-id="662dd-335">For applications installed on and launched from the local machine, this falls within the set of permissions that are granted to the application.</span></span>  
  
 <span data-ttu-id="662dd-336">Ale to spadá mimo sadu oprávnění udělená aplikace, které jsou spouštěny z Internetu nebo místní intranet zóny pomocí [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)].</span><span class="sxs-lookup"><span data-stu-id="662dd-336">However, this falls outside the set of permissions granted to applications that are launched from the Internet or Local intranet zone using [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)].</span></span> <span data-ttu-id="662dd-337">V důsledku toho uživatelé dostanou [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] upozornění zabezpečení a se potřebují k rozvoji sady oprávnění pro aplikace pro úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="662dd-337">Consequently, users will receive a [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] security warning and will need to elevate the permission set for the application to full trust.</span></span>  
  
 <span data-ttu-id="662dd-338">Kromě toho [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] nelze zobrazit systému windows nebo dialogová okna ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="662dd-338">Additionally, [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] cannot show windows or dialog boxes by default.</span></span> <span data-ttu-id="662dd-339">Informace o informace o zabezpečení pro samostatné aplikace, najdete v článku [strategie zabezpečení WPF – zabezpečení platformy](../wpf-security-strategy-platform-security.md).</span><span class="sxs-lookup"><span data-stu-id="662dd-339">For a discussion on standalone application security considerations, see [WPF Security Strategy - Platform Security](../wpf-security-strategy-platform-security.md).</span></span>  
  
<a name="Other_Types_of_Windows"></a>   
## <a name="other-types-of-windows"></a><span data-ttu-id="662dd-340">Jiné typy Windows</span><span class="sxs-lookup"><span data-stu-id="662dd-340">Other Types of Windows</span></span>  
 <span data-ttu-id="662dd-341"><xref:System.Windows.Navigation.NavigationWindow> je okno, které slouží k hostování navigaci obsahu.</span><span class="sxs-lookup"><span data-stu-id="662dd-341"><xref:System.Windows.Navigation.NavigationWindow> is a window that is designed to host navigable content.</span></span> <span data-ttu-id="662dd-342">Další informace najdete v tématu [Přehled navigace](navigation-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="662dd-342">For more information, see [Navigation Overview](navigation-overview.md)).</span></span>  
  
 <span data-ttu-id="662dd-343">Dialogová okna jsou windows, které se často používají k získání informací od uživatele k dokončení funkce.</span><span class="sxs-lookup"><span data-stu-id="662dd-343">Dialog boxes are windows that are often used to gather information from a user to complete a function.</span></span> <span data-ttu-id="662dd-344">Například, pokud uživatel požaduje pro otevření souboru, **otevřít soubor** aplikací a získání názvu souboru od uživatele je obvykle zobrazí dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="662dd-344">For example, when a user wants to open a file, the **Open File** dialog box is usually displayed by an application to get the file name from the user.</span></span> <span data-ttu-id="662dd-345">Další informace najdete v tématu [přehled dialogových oken](dialog-boxes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="662dd-345">For more information, see [Dialog Boxes Overview](dialog-boxes-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="662dd-346">Viz také:</span><span class="sxs-lookup"><span data-stu-id="662dd-346">See also</span></span>

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [<span data-ttu-id="662dd-347">Přehled dialogových oken</span><span class="sxs-lookup"><span data-stu-id="662dd-347">Dialog Boxes Overview</span></span>](dialog-boxes-overview.md)
- [<span data-ttu-id="662dd-348">Sestavení aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="662dd-348">Building a WPF Application</span></span>](building-a-wpf-application-wpf.md)
