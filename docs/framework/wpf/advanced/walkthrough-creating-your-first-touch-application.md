---
title: 'Návod: Vytvoření první dotykové aplikace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating a touch-sensitive application [WPF]
- touchscreen applications [WPF], creating
- touch-sensitive applications [WPF], creating
- creating a touchscreen application [WPF]
ms.assetid: d69e602e-9a25-4e24-950b-e89eaa2a906b
ms.openlocfilehash: 53ae737394d76d9f293f6e03fbf04cbb46d2adbb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778817"
---
# <a name="walkthrough-creating-your-first-touch-application"></a><span data-ttu-id="c5080-102">Návod: Vytvoření první dotykové aplikace</span><span class="sxs-lookup"><span data-stu-id="c5080-102">Walkthrough: Creating Your First Touch Application</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="c5080-103">umožňuje aplikacím na dotykového ovládání.</span><span class="sxs-lookup"><span data-stu-id="c5080-103">enables applications to respond to touch.</span></span> <span data-ttu-id="c5080-104">Například můžete pracovat s aplikací pomocí jedné nebo více prsty na dotyk zařízení, např. k tomu dotykovou obrazovku tento návod vytvoří aplikaci, která umožňuje uživateli přesunutí, změna velikosti nebo otočení jednoho objektu pomocí touch.</span><span class="sxs-lookup"><span data-stu-id="c5080-104">For example, you can interact with an application by using one or more fingers on a touch-sensitive device, such as a touchscreen This walkthrough creates an application that enables the user to move, resize, or rotate a single object by using touch.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c5080-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c5080-105">Prerequisites</span></span>  
 <span data-ttu-id="c5080-106">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="c5080-106">You need the following components to complete this walkthrough:</span></span>  
  
- <span data-ttu-id="c5080-107">Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c5080-107">Visual Studio.</span></span>  
  
- <span data-ttu-id="c5080-108">Zařízení, která přijímá dotykové ovládání, jako je například k tomu dotykovou obrazovku, který podporuje Windows Touch.</span><span class="sxs-lookup"><span data-stu-id="c5080-108">A device that accepts touch input, such as a touchscreen, that supports Windows Touch.</span></span>  
  
 <span data-ttu-id="c5080-109">Kromě toho byste měli mít základní znalosti o tom, jak vytvořit aplikaci v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zejména jak přihlásit k odběru a zpracovat události.</span><span class="sxs-lookup"><span data-stu-id="c5080-109">Additionally, you should have a basic understanding of how to create an application in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], especially how to subscribe to and handle an event.</span></span> <span data-ttu-id="c5080-110">Další informace najdete v tématu [názorný postup: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="c5080-110">For more information, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>  
  
## <a name="creating-the-application"></a><span data-ttu-id="c5080-111">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="c5080-111">Creating the Application</span></span>  
  
#### <a name="to-create-the-application"></a><span data-ttu-id="c5080-112">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="c5080-112">To create the application</span></span>  
  
1. <span data-ttu-id="c5080-113">Vytvoření nového projektu aplikace WPF v jazyce Visual Basic nebo Visual C# s názvem `BasicManipulation`.</span><span class="sxs-lookup"><span data-stu-id="c5080-113">Create a new WPF Application project in Visual Basic or Visual C# named `BasicManipulation`.</span></span> <span data-ttu-id="c5080-114">Další informace najdete v tématu [názorný postup: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="c5080-114">For more information, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>  
  
2. <span data-ttu-id="c5080-115">Obsah souboru MainWindow.xaml nahraďte následující XAML.</span><span class="sxs-lookup"><span data-stu-id="c5080-115">Replace the contents of MainWindow.xaml with the following XAML.</span></span>  
  
     <span data-ttu-id="c5080-116">Tento kód vytvoří jednoduchou aplikaci, která obsahuje červený <xref:System.Windows.Shapes.Rectangle> na <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="c5080-116">This markup creates a simple application that contains a red <xref:System.Windows.Shapes.Rectangle> on a <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="c5080-117"><xref:System.Windows.UIElement.IsManipulationEnabled%2A> Vlastnost <xref:System.Windows.Shapes.Rectangle> je nastavena na hodnotu true, tak, aby obdrží manipulace s událostmi.</span><span class="sxs-lookup"><span data-stu-id="c5080-117">The <xref:System.Windows.UIElement.IsManipulationEnabled%2A> property of the <xref:System.Windows.Shapes.Rectangle> is set to true so that it will receive manipulation events.</span></span> <span data-ttu-id="c5080-118">Aplikace se přihlásí k odběru <xref:System.Windows.UIElement.ManipulationStarting>, <xref:System.Windows.UIElement.ManipulationDelta>, a <xref:System.Windows.UIElement.ManipulationInertiaStarting> události.</span><span class="sxs-lookup"><span data-stu-id="c5080-118">The application subscribes to the <xref:System.Windows.UIElement.ManipulationStarting>, <xref:System.Windows.UIElement.ManipulationDelta>, and <xref:System.Windows.UIElement.ManipulationInertiaStarting> events.</span></span> <span data-ttu-id="c5080-119">Tyto události obsahují logiku pro přesun <xref:System.Windows.Shapes.Rectangle> když uživatel manipuluje s ním.</span><span class="sxs-lookup"><span data-stu-id="c5080-119">These events contain the logic to move the <xref:System.Windows.Shapes.Rectangle> when the user manipulates it.</span></span>  
  
     [!code-xaml[BasicManipulation#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml#ui)]  
  
3. <span data-ttu-id="c5080-120">Pokud používáte Visual Basic v prvním řádku souboru mainwindow.XAML, nahraďte `x:Class="BasicManipulation.MainWindow"` s `x:Class="MainWindow"`.</span><span class="sxs-lookup"><span data-stu-id="c5080-120">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="BasicManipulation.MainWindow"` with `x:Class="MainWindow"`.</span></span>  
  
4. <span data-ttu-id="c5080-121">V `MainWindow` třídy, přidejte následující <xref:System.Windows.UIElement.ManipulationStarting> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="c5080-121">In the `MainWindow` class, add the following <xref:System.Windows.UIElement.ManipulationStarting> event handler.</span></span>  
  
     <span data-ttu-id="c5080-122"><xref:System.Windows.UIElement.ManipulationStarting> Dojde k události při [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zjistí, že touch vstup začne pracovat s objektu.</span><span class="sxs-lookup"><span data-stu-id="c5080-122">The <xref:System.Windows.UIElement.ManipulationStarting> event occurs when [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] detects that touch input begins to manipulate an object.</span></span> <span data-ttu-id="c5080-123">Kód určuje, že pozice manipulace by měl být vzhledem k <xref:System.Windows.Window> nastavením <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c5080-123">The code specifies that the position of the manipulation should be relative to the <xref:System.Windows.Window> by setting the <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> property.</span></span>  
  
     [!code-csharp[BasicManipulation#ManipulationStarting](~/samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationstarting)]
     [!code-vb[BasicManipulation#ManipulationStarting](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationstarting)]

5. <span data-ttu-id="c5080-124">V `MainWindow` třídy, přidejte následující <xref:System.Windows.Input.ManipulationDelta> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="c5080-124">In the `MainWindow` class, add the following <xref:System.Windows.Input.ManipulationDelta> event handler.</span></span>

     <span data-ttu-id="c5080-125"><xref:System.Windows.Input.ManipulationDelta> Události dojde, když dotykem vstup změny pozice a může dojít k více než jednou při manipulaci s.</span><span class="sxs-lookup"><span data-stu-id="c5080-125">The <xref:System.Windows.Input.ManipulationDelta> event occurs when the touch input changes position and can occur multiple times during a manipulation.</span></span> <span data-ttu-id="c5080-126">Události může také dojít v případě prstem je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="c5080-126">The event can also occur after a finger is raised.</span></span> <span data-ttu-id="c5080-127">Například, pokud uživatel přetáhne prstem obrazovce <xref:System.Windows.Input.ManipulationDelta> více než jednou jako přesune prstem dojde k události.</span><span class="sxs-lookup"><span data-stu-id="c5080-127">For example, if the user drags a finger across a screen, the <xref:System.Windows.Input.ManipulationDelta> event occurs multiple times as the finger moves.</span></span> <span data-ttu-id="c5080-128">Pokud uživatel prstem na obrazovce, <xref:System.Windows.Input.ManipulationDelta> udržuje pro simulaci nečinnost výskytu události.</span><span class="sxs-lookup"><span data-stu-id="c5080-128">When the user raises a finger from the screen, the <xref:System.Windows.Input.ManipulationDelta> event keeps occurring to simulate inertia.</span></span>

     <span data-ttu-id="c5080-129">Kód se vztahuje <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> k <xref:System.Windows.UIElement.RenderTransform%2A> z <xref:System.Windows.Shapes.Rectangle> ji přesunout, jak uživatel přesouvá dotykem vstup.</span><span class="sxs-lookup"><span data-stu-id="c5080-129">The code applies the <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> to the <xref:System.Windows.UIElement.RenderTransform%2A> of the <xref:System.Windows.Shapes.Rectangle> to move it as the user moves the touch input.</span></span> <span data-ttu-id="c5080-130">Také zkontroluje, zda <xref:System.Windows.Shapes.Rectangle> je mimo hranice <xref:System.Windows.Window> při výskytu události při nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="c5080-130">It also checks whether the <xref:System.Windows.Shapes.Rectangle> is outside the bounds of the <xref:System.Windows.Window> when the event occurs during inertia.</span></span> <span data-ttu-id="c5080-131">Pokud ano, aplikace volá <xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=nameWithType> metoda end manipulaci.</span><span class="sxs-lookup"><span data-stu-id="c5080-131">If so, the application calls the <xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=nameWithType> method to end the manipulation.</span></span>

     [!code-csharp[BasicManipulation#ManipulationDelta](~/samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationdelta)]
     [!code-vb[BasicManipulation#ManipulationDelta](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationdelta)]

6. <span data-ttu-id="c5080-132">V `MainWindow` třídy, přidejte následující <xref:System.Windows.UIElement.ManipulationInertiaStarting> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="c5080-132">In the `MainWindow` class, add the following <xref:System.Windows.UIElement.ManipulationInertiaStarting> event handler.</span></span>

     <span data-ttu-id="c5080-133"><xref:System.Windows.UIElement.ManipulationInertiaStarting> Události dojde, když uživatel vyvolá všechny prsty na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="c5080-133">The <xref:System.Windows.UIElement.ManipulationInertiaStarting> event occurs when the user raises all fingers from the screen.</span></span> <span data-ttu-id="c5080-134">Kód nastaví počáteční a zpomalení přesunu, rozšíření a otočení obdélníku.</span><span class="sxs-lookup"><span data-stu-id="c5080-134">The code sets the initial velocity and deceleration for the movement, expansion, and rotation of the rectangle.</span></span>

     [!code-csharp[BasicManipulation#ManipulationInertiaStarting](~/samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationinertiastarting)]
     [!code-vb[BasicManipulation#ManipulationInertiaStarting](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationinertiastarting)]

7. <span data-ttu-id="c5080-135">Sestavte a spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="c5080-135">Build and run the project.</span></span>

     <span data-ttu-id="c5080-136">Měli byste vidět v okně se zobrazí červený čtvereček.</span><span class="sxs-lookup"><span data-stu-id="c5080-136">You should see a red square appear in the window.</span></span>

## <a name="testing-the-application"></a><span data-ttu-id="c5080-137">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="c5080-137">Testing the Application</span></span>
 <span data-ttu-id="c5080-138">K otestování aplikace, zkuste následující manipulací.</span><span class="sxs-lookup"><span data-stu-id="c5080-138">To test the application, try the following manipulations.</span></span> <span data-ttu-id="c5080-139">Všimněte si, že můžete provést více než jednu z následujících akcí ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="c5080-139">Note that you can do more than one of the following at the same time.</span></span>

- <span data-ttu-id="c5080-140">Přesunout <xref:System.Windows.Shapes.Rectangle>, umístí prstem <xref:System.Windows.Shapes.Rectangle> a napříč obrazovkou se pohybují prstu.</span><span class="sxs-lookup"><span data-stu-id="c5080-140">To move the <xref:System.Windows.Shapes.Rectangle>, put a finger on the <xref:System.Windows.Shapes.Rectangle> and move the finger across the screen.</span></span>

- <span data-ttu-id="c5080-141">Pro změnu velikosti <xref:System.Windows.Shapes.Rectangle>, umístí dvěma prsty <xref:System.Windows.Shapes.Rectangle> a přesunout prsty blíže společně nebo jsou od sebe navzájem.</span><span class="sxs-lookup"><span data-stu-id="c5080-141">To resize the <xref:System.Windows.Shapes.Rectangle>, put two fingers on the <xref:System.Windows.Shapes.Rectangle> and move the fingers closer together or farther apart from each other.</span></span>

- <span data-ttu-id="c5080-142">Obměna <xref:System.Windows.Shapes.Rectangle>, umístí dvěma prsty <xref:System.Windows.Shapes.Rectangle> a otočení prsty kolem sebe navzájem.</span><span class="sxs-lookup"><span data-stu-id="c5080-142">To rotate the <xref:System.Windows.Shapes.Rectangle>, put two fingers on the <xref:System.Windows.Shapes.Rectangle> and rotate the fingers around each other.</span></span>

 <span data-ttu-id="c5080-143">Způsobit nečinnost, rychle zvýšit prsty na obrazovce při provádění předchozího manipulací.</span><span class="sxs-lookup"><span data-stu-id="c5080-143">To cause inertia, quickly raise your fingers from the screen as you perform the previous manipulations.</span></span> <span data-ttu-id="c5080-144"><xref:System.Windows.Shapes.Rectangle> Budou i nadále přesunutí, změna velikosti nebo otočení na několik sekund, než přestane.</span><span class="sxs-lookup"><span data-stu-id="c5080-144">The <xref:System.Windows.Shapes.Rectangle> will continue to move, resize, or rotate for a few seconds before it stops.</span></span>

## <a name="see-also"></a><span data-ttu-id="c5080-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c5080-145">See also</span></span>

- <xref:System.Windows.UIElement.ManipulationStarting?displayProperty=nameWithType>
- <xref:System.Windows.UIElement.ManipulationDelta?displayProperty=nameWithType>
- <xref:System.Windows.UIElement.ManipulationInertiaStarting?displayProperty=nameWithType>