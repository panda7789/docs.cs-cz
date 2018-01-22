---
title: "Návod: Vytvoření první aplikace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating a touch-sensitive application [WPF]
- touchscreen applications [WPF], creating
- touch-sensitive applications [WPF], creating
- creating a touchscreen application [WPF]
ms.assetid: d69e602e-9a25-4e24-950b-e89eaa2a906b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 08f4004329d15b527a889cd7b437a7f18278fc79
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-creating-your-first-touch-application"></a><span data-ttu-id="0a1d4-102">Návod: Vytvoření první aplikace</span><span class="sxs-lookup"><span data-stu-id="0a1d4-102">Walkthrough: Creating Your First Touch Application</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="0a1d4-103">umožňuje aplikacím reagovat na touch.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-103"> enables applications to respond to touch.</span></span> <span data-ttu-id="0a1d4-104">Například můžete pracovat s aplikací pomocí jedné nebo více prsty, které na zařízení touch-velká a malá písmena, například dotykovou obrazovku tento návod vytvoří aplikaci, která umožňuje uživatelům přesunout, změnit velikost nebo otočení jednoho objektu pomocí touch.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-104">For example, you can interact with an application by using one or more fingers on a touch-sensitive device, such as a touchscreen This walkthrough creates an application that enables the user to move, resize, or rotate a single object by using touch.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0a1d4-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0a1d4-105">Prerequisites</span></span>  
 <span data-ttu-id="0a1d4-106">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="0a1d4-106">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_ext](../../../../includes/vs-dev10-ext-md.md)]<span data-ttu-id="0a1d4-107">.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-107">.</span></span>  
  
-   <span data-ttu-id="0a1d4-108">Windows 7.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-108">Windows 7.</span></span>  
  
-   <span data-ttu-id="0a1d4-109">Zařízení, které přijímá touch vstupu, například dotykovou obrazovku, který podporuje Windows Touch.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-109">A device that accepts touch input, such as a touchscreen, that supports Windows Touch.</span></span>  
  
 <span data-ttu-id="0a1d4-110">Kromě toho musí mít základní znalosti o tom, jak vytvořit aplikaci v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zejména jak se přihlásit k odběru a zpracování události.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-110">Additionally, you should have a basic understanding of how to create an application in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], especially how to subscribe to and handle an event.</span></span> <span data-ttu-id="0a1d4-111">Další informace najdete v tématu [návod: Můj první desktopová aplikace WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="0a1d4-111">For more information, see [Walkthrough: My first WPF desktop application](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>  
  
## <a name="creating-the-application"></a><span data-ttu-id="0a1d4-112">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="0a1d4-112">Creating the Application</span></span>  
  
#### <a name="to-create-the-application"></a><span data-ttu-id="0a1d4-113">K vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="0a1d4-113">To create the application</span></span>  
  
1.  <span data-ttu-id="0a1d4-114">Vytvořte nový projekt aplikace WPF v jazyce Visual Basic a Visual C# s názvem `BasicManipulation`.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-114">Create a new WPF Application project in Visual Basic or Visual C# named `BasicManipulation`.</span></span> <span data-ttu-id="0a1d4-115">Další informace najdete v tématu [postupy: vytvoření nového projektu aplikace WPF](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span><span class="sxs-lookup"><span data-stu-id="0a1d4-115">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>  
  
2.  <span data-ttu-id="0a1d4-116">Nahraďte obsah MainWindow.xaml následující XAML.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-116">Replace the contents of MainWindow.xaml with the following XAML.</span></span>  
  
     <span data-ttu-id="0a1d4-117">Tento kód vytvoří jednoduchou aplikaci, která obsahuje zobrazí červený <xref:System.Windows.Shapes.Rectangle> na <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-117">This markup creates a simple application that contains a red <xref:System.Windows.Shapes.Rectangle> on a <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="0a1d4-118"><xref:System.Windows.UIElement.IsManipulationEnabled%2A> Vlastnost <xref:System.Windows.Shapes.Rectangle> je nastaven na hodnotu true, aby ho přijme zpracování události.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-118">The <xref:System.Windows.UIElement.IsManipulationEnabled%2A> property of the <xref:System.Windows.Shapes.Rectangle> is set to true so that it will receive manipulation events.</span></span> <span data-ttu-id="0a1d4-119">Aplikace se přihlásí k odběru <xref:System.Windows.UIElement.ManipulationStarting>, <xref:System.Windows.UIElement.ManipulationDelta>, a <xref:System.Windows.UIElement.ManipulationInertiaStarting> události.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-119">The application subscribes to the <xref:System.Windows.UIElement.ManipulationStarting>, <xref:System.Windows.UIElement.ManipulationDelta>, and <xref:System.Windows.UIElement.ManipulationInertiaStarting> events.</span></span> <span data-ttu-id="0a1d4-120">Tyto události obsahují logiku pro přesun <xref:System.Windows.Shapes.Rectangle> když uživatel manipuluje ho.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-120">These events contain the logic to move the <xref:System.Windows.Shapes.Rectangle> when the user manipulates it.</span></span>  
  
     [!code-xaml[BasicManipulation#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml#ui)]  
  
3.  <span data-ttu-id="0a1d4-121">Pokud používáte Visual Basic, v prvním řádku MainWindow.xaml, nahraďte `x:Class="BasicManipulation.MainWindow"` s `x:Class="MainWindow"`.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-121">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="BasicManipulation.MainWindow"` with `x:Class="MainWindow"`.</span></span>  
  
4.  <span data-ttu-id="0a1d4-122">V `MainWindow` třídy, přidejte následující <xref:System.Windows.UIElement.ManipulationStarting> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-122">In the `MainWindow` class, add the following <xref:System.Windows.UIElement.ManipulationStarting> event handler.</span></span>  
  
     <span data-ttu-id="0a1d4-123"><xref:System.Windows.UIElement.ManipulationStarting> Dojde k události při [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zjistí, že touch vstup začne pracovat s objekt.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-123">The <xref:System.Windows.UIElement.ManipulationStarting> event occurs when [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] detects that touch input begins to manipulate an object.</span></span> <span data-ttu-id="0a1d4-124">Kód určuje, že pozice manipulaci by měl být vzhledem k <xref:System.Windows.Window> nastavením <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-124">The code specifies that the position of the manipulation should be relative to the <xref:System.Windows.Window> by setting the <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> property.</span></span>  
  
     [!code-csharp[BasicManipulation#ManipulationStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationstarting)]
     [!code-vb[BasicManipulation#ManipulationStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationstarting)]  
  
5.  <span data-ttu-id="0a1d4-125">V `MainWindow` třídy, přidejte následující <xref:System.Windows.Input.ManipulationDelta> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-125">In the `MainWindow` class, add the following <xref:System.Windows.Input.ManipulationDelta> event handler.</span></span>  
  
     <span data-ttu-id="0a1d4-126"><xref:System.Windows.Input.ManipulationDelta> Události dojde, když stiskem vstupní pozice změny a dochází při manipulaci s více než jednou.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-126">The <xref:System.Windows.Input.ManipulationDelta> event occurs when the touch input changes position and can occur multiple times during a manipulation.</span></span> <span data-ttu-id="0a1d4-127">Události může dojít také po se vyvolá prstu.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-127">The event can also occur after a finger is raised.</span></span> <span data-ttu-id="0a1d4-128">Pokud uživatel nastavuje tažením prstem napříč na obrazovce, například <xref:System.Windows.Input.ManipulationDelta> vícekrát jako přesune prstem dojde k události.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-128">For example, if the user drags a finger across a screen, the <xref:System.Windows.Input.ManipulationDelta> event occurs multiple times as the finger moves.</span></span> <span data-ttu-id="0a1d4-129">Když uživatel vyvolá prstem na obrazovce, <xref:System.Windows.Input.ManipulationDelta> vyskytuje opakovaně událostí k simulaci nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-129">When the user raises a finger from the screen, the <xref:System.Windows.Input.ManipulationDelta> event keeps occurring to simulate inertia.</span></span>  
  
     <span data-ttu-id="0a1d4-130">Kód se vztahuje <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> k <xref:System.Windows.UIElement.RenderTransform%2A> z <xref:System.Windows.Shapes.Rectangle> ho přesunout, protože uživatel přesune touch vstup.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-130">The code applies the <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> to the <xref:System.Windows.UIElement.RenderTransform%2A> of the <xref:System.Windows.Shapes.Rectangle> to move it as the user moves the touch input.</span></span> <span data-ttu-id="0a1d4-131">Je také zkontroluje, zda <xref:System.Windows.Shapes.Rectangle> je mimo hranice <xref:System.Windows.Window> když dojde k události při nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-131">It also checks whether the <xref:System.Windows.Shapes.Rectangle> is outside the bounds of the <xref:System.Windows.Window> when the event occurs during inertia.</span></span> <span data-ttu-id="0a1d4-132">Pokud ano, aplikace volá <xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=nameWithType> metoda na konec manipulaci.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-132">If so, the application calls the <xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=nameWithType> method to end the manipulation.</span></span>  
  
     [!code-csharp[BasicManipulation#ManipulationDelta](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationdelta)]
     [!code-vb[BasicManipulation#ManipulationDelta](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationdelta)]  
  
6.  <span data-ttu-id="0a1d4-133">V `MainWindow` třídy, přidejte následující <xref:System.Windows.UIElement.ManipulationInertiaStarting> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-133">In the `MainWindow` class, add the following <xref:System.Windows.UIElement.ManipulationInertiaStarting> event handler.</span></span>  
  
     <span data-ttu-id="0a1d4-134"><xref:System.Windows.UIElement.ManipulationInertiaStarting> Události dojde, když uživatel vyvolá všech prstů na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-134">The <xref:System.Windows.UIElement.ManipulationInertiaStarting> event occurs when the user raises all fingers from the screen.</span></span> <span data-ttu-id="0a1d4-135">Kód nastaví počáteční rychlost a zpomalení přesun, rozšíření a oběh rámeček.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-135">The code sets the initial velocity and deceleration for the movement, expansion, and rotation of the rectangle.</span></span>  
  
     [!code-csharp[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationinertiastarting)]
     [!code-vb[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationinertiastarting)]  
  
7.  <span data-ttu-id="0a1d4-136">Sestavte a spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-136">Build and run the project.</span></span>  
  
     <span data-ttu-id="0a1d4-137">Měli byste vidět červený čtvereček se zobrazí v okně.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-137">You should see a red square appear in the window.</span></span>  
  
## <a name="testing-the-application"></a><span data-ttu-id="0a1d4-138">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="0a1d4-138">Testing the Application</span></span>  
 <span data-ttu-id="0a1d4-139">K testování aplikace, zkuste následující manipulace.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-139">To test the application, try the following manipulations.</span></span> <span data-ttu-id="0a1d4-140">Všimněte si, že můžete provést více než jednu z těchto ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-140">Note that you can do more than one of the following at the same time.</span></span>  
  
-   <span data-ttu-id="0a1d4-141">Přesunout <xref:System.Windows.Shapes.Rectangle>, umístí prstem <xref:System.Windows.Shapes.Rectangle> a přesuňte prstu po obrazovce.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-141">To move the <xref:System.Windows.Shapes.Rectangle>, put a finger on the <xref:System.Windows.Shapes.Rectangle> and move the finger across the screen.</span></span>  
  
-   <span data-ttu-id="0a1d4-142">Ke změně velikosti <xref:System.Windows.Shapes.Rectangle>, umístí dvěma prsty <xref:System.Windows.Shapes.Rectangle> a přesunout prsty blíže společně nebo dále vedle sebe navzájem.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-142">To resize the <xref:System.Windows.Shapes.Rectangle>, put two fingers on the <xref:System.Windows.Shapes.Rectangle> and move the fingers closer together or farther apart from each other.</span></span>  
  
-   <span data-ttu-id="0a1d4-143">Obměna <xref:System.Windows.Shapes.Rectangle>, umístí dvěma prsty <xref:System.Windows.Shapes.Rectangle> a otočit prsty kolem navzájem.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-143">To rotate the <xref:System.Windows.Shapes.Rectangle>, put two fingers on the <xref:System.Windows.Shapes.Rectangle> and rotate the fingers around each other.</span></span>  
  
 <span data-ttu-id="0a1d4-144">Chcete-li způsobit nečinnosti, rychle zvýšit prsty z obrazovky provádět předchozí manipulace.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-144">To cause inertia, quickly raise your fingers from the screen as you perform the previous manipulations.</span></span> <span data-ttu-id="0a1d4-145"><xref:System.Windows.Shapes.Rectangle> Budou nadále přesunout, změnit velikost nebo otočit na několik sekund, než se zastavuje.</span><span class="sxs-lookup"><span data-stu-id="0a1d4-145">The <xref:System.Windows.Shapes.Rectangle> will continue to move, resize, or rotate for a few seconds before it stops.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a1d4-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="0a1d4-146">See Also</span></span>  
 <xref:System.Windows.UIElement.ManipulationStarting?displayProperty=nameWithType>  
 <xref:System.Windows.UIElement.ManipulationDelta?displayProperty=nameWithType>  
 <xref:System.Windows.UIElement.ManipulationInertiaStarting?displayProperty=nameWithType>
