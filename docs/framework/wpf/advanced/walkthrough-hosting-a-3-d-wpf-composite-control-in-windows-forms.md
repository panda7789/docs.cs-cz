---
title: 'Návod: Hostování kompozitního ovládacího prvku 3D WPF v rozhraní Windows Forms'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
ms.openlocfilehash: f33adf6bac5efab87fecd9e95437ac8cff6d1f16
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976560"
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a><span data-ttu-id="6e507-102">Návod: Hostování kompozitního ovládacího prvku 3D WPF v rozhraní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6e507-102">Walkthrough: Hosting a 3-D WPF Composite Control in Windows Forms</span></span>

<span data-ttu-id="6e507-103">Tento návod ukazuje, jak lze vytvořit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] složený ovládací prvek a hostovat ho v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacích prvcích a formulářích pomocí ovládacího prvku <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="6e507-103">This walkthrough demonstrates how you can create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] composite control and host it in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls and forms by using the <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

<span data-ttu-id="6e507-104">V tomto návodu implementujete [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>, které obsahují dva podřízené ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="6e507-104">In this walkthrough, you will implement a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> that contains two child controls.</span></span> <span data-ttu-id="6e507-105"><xref:System.Windows.Controls.UserControl> zobrazí trojrozměrné (3D) kužel.</span><span class="sxs-lookup"><span data-stu-id="6e507-105">The <xref:System.Windows.Controls.UserControl> displays a three-dimensional (3-D) cone.</span></span> <span data-ttu-id="6e507-106">Vykreslování 3D objektů je mnohem snazší s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] než s [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6e507-106">Rendering 3-D objects is much easier with the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] than with [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="6e507-107">Proto má smysl hostovat třídu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> a vytvořit v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]3D grafiku.</span><span class="sxs-lookup"><span data-stu-id="6e507-107">Therefore, it makes sense to host a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> class to create 3-D graphics in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>

<span data-ttu-id="6e507-108">Úlohy, které jsou znázorněné v tomto návodu, zahrnují:</span><span class="sxs-lookup"><span data-stu-id="6e507-108">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="6e507-109">Vytváření <xref:System.Windows.Controls.UserControl>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6e507-109">Creating the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>

- <span data-ttu-id="6e507-110">Vytváří se projekt hostitele model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6e507-110">Creating the Windows Forms host project.</span></span>

- <span data-ttu-id="6e507-111">Hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="6e507-111">Hosting the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6e507-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6e507-112">Prerequisites</span></span>

<span data-ttu-id="6e507-113">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="6e507-113">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="6e507-114">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="6e507-114">Visual Studio 2017</span></span>

<a name="To_Create_the_UserControl"></a>
## <a name="create-the-usercontrol"></a><span data-ttu-id="6e507-115">Vytvoření prvku UserControl</span><span class="sxs-lookup"><span data-stu-id="6e507-115">Create the UserControl</span></span>

1. <span data-ttu-id="6e507-116">Vytvořte projekt **knihovny uživatelských ovládacích prvků WPF** s názvem `HostingWpfUserControlInWf`.</span><span class="sxs-lookup"><span data-stu-id="6e507-116">Create a **WPF User Control Library** project named `HostingWpfUserControlInWf`.</span></span>

2. <span data-ttu-id="6e507-117">Otevřete UserControl1. XAML v Návrháři WPF.</span><span class="sxs-lookup"><span data-stu-id="6e507-117">Open UserControl1.xaml in the WPF Designer.</span></span>

3. <span data-ttu-id="6e507-118">Vygenerovaný kód nahraďte následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="6e507-118">Replace the generated code with the following code:</span></span>

     [!code-xaml[HostingWpfUserControlInWf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]

     <span data-ttu-id="6e507-119">Tento kód definuje <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>, která obsahuje dva podřízené ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="6e507-119">This code defines a <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> that contains two child controls.</span></span> <span data-ttu-id="6e507-120">Prvním podřízeným ovládacím prvkem je ovládací prvek <xref:System.Windows.Controls.Label?displayProperty=nameWithType>; druhým je <xref:System.Windows.Controls.Viewport3D> ovládací prvek, který zobrazuje prostorový kuželový.</span><span class="sxs-lookup"><span data-stu-id="6e507-120">The first child control is a <xref:System.Windows.Controls.Label?displayProperty=nameWithType> control; the second is a <xref:System.Windows.Controls.Viewport3D> control that displays a 3-D cone.</span></span>

<a name="To_Create_the_Windows_Forms_Host_Project"></a>
## <a name="create-the-host-project"></a><span data-ttu-id="6e507-121">Vytvořit hostitelský projekt</span><span class="sxs-lookup"><span data-stu-id="6e507-121">Create the host project</span></span>

1. <span data-ttu-id="6e507-122">Přidejte do řešení projekt **aplikace model Windows Forms (.NET Framework)** s názvem `WpfUserControlHost`.</span><span class="sxs-lookup"><span data-stu-id="6e507-122">Add a **Windows Forms App (.NET Framework)** project named `WpfUserControlHost` to the solution.</span></span>

2. <span data-ttu-id="6e507-123">V **Průzkumník řešení**přidejte odkaz na sestavení WindowsFormsIntegration, které má název WindowsFormsIntegration. dll.</span><span class="sxs-lookup"><span data-stu-id="6e507-123">In **Solution Explorer**, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3. <span data-ttu-id="6e507-124">Přidejte odkazy na následující [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sestavení:</span><span class="sxs-lookup"><span data-stu-id="6e507-124">Add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies:</span></span>

    - <span data-ttu-id="6e507-125">PresentationCore</span><span class="sxs-lookup"><span data-stu-id="6e507-125">PresentationCore</span></span>

    - <span data-ttu-id="6e507-126">PresentationFramework</span><span class="sxs-lookup"><span data-stu-id="6e507-126">PresentationFramework</span></span>

    - <span data-ttu-id="6e507-127">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="6e507-127">WindowsBase</span></span>

4. <span data-ttu-id="6e507-128">Přidejte odkaz na `HostingWpfUserControlInWf` projekt.</span><span class="sxs-lookup"><span data-stu-id="6e507-128">Add a reference to the `HostingWpfUserControlInWf` project.</span></span>

5. <span data-ttu-id="6e507-129">V Průzkumník řešení nastavte projekt `WpfUserControlHost` na spouštěný projekt.</span><span class="sxs-lookup"><span data-stu-id="6e507-129">In Solution Explorer, set the `WpfUserControlHost` project to be the startup project.</span></span>

<a name="To_Host_the_Windows_Presentation_Foundation"></a>
## <a name="host-the-usercontrol"></a><span data-ttu-id="6e507-130">Hostování prvku UserControl</span><span class="sxs-lookup"><span data-stu-id="6e507-130">Host the UserControl</span></span>

1. <span data-ttu-id="6e507-131">V Návrhář formulářů otevřete Form1.</span><span class="sxs-lookup"><span data-stu-id="6e507-131">In the Windows Forms Designer, open Form1.</span></span>

2. <span data-ttu-id="6e507-132">V okno Vlastnosti klikněte na položku **události**a potom poklikejte na událost <xref:System.Windows.Forms.Form.Load> a vytvořte obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="6e507-132">In the Properties window, click **Events**, and then double-click the <xref:System.Windows.Forms.Form.Load> event to create an event handler.</span></span>

     <span data-ttu-id="6e507-133">Editor kódu se otevře v nově vygenerované obslužné rutině `Form1_Load` události.</span><span class="sxs-lookup"><span data-stu-id="6e507-133">The Code Editor opens to the newly generated `Form1_Load` event handler.</span></span>

3. <span data-ttu-id="6e507-134">Nahraďte kód v Form1.cs následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="6e507-134">Replace the code in Form1.cs with the following code.</span></span>

     <span data-ttu-id="6e507-135">Obslužná rutina události `Form1_Load` vytvoří instanci `UserControl1` a přidá tovární kolekci podřízených ovládacích prvků <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="6e507-135">The `Form1_Load` event handler creates an instance of `UserControl1` and adds itto the <xref:System.Windows.Forms.Integration.ElementHost> control's collection of child controls.</span></span> <span data-ttu-id="6e507-136"><xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek je přidán do kolekce podřízených ovládacích prvků formuláře.</span><span class="sxs-lookup"><span data-stu-id="6e507-136">The <xref:System.Windows.Forms.Integration.ElementHost> control is added to the form's collection of child controls.</span></span>

     [!code-csharp[HostingWpfUserControlInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]

4. <span data-ttu-id="6e507-137">Stisknutím klávesy **F5** Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6e507-137">Press **F5** to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="6e507-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e507-138">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="6e507-139">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6e507-139">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="6e507-140">Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6e507-140">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="6e507-141">Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="6e507-141">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="6e507-142">Hostování složeného ovládacího prvku WPF v model Windows Forms Sample</span><span class="sxs-lookup"><span data-stu-id="6e507-142">Hosting a WPF Composite Control in Windows Forms Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160001)
