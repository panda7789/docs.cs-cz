---
title: 'Průvodce: Vytvoření nového obsahu WPF ve Windows Forms v době návrhu'
ms.date: 08/18/2018
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
ms.openlocfilehash: 9414eb8edc839b109aafa0c98fa3ed74a34a7d62
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54500496"
---
# <a name="walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="660cf-102">Průvodce: Vytvoření nového obsahu WPF ve Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="660cf-102">Walkthrough: Creating New WPF Content on Windows Forms at Design Time</span></span>

<span data-ttu-id="660cf-103">Toto téma ukazuje, jak vytvořit ovládací prvek Windows Presentation Foundation (WPF) pro použití ve svých aplikacích pomocí formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="660cf-103">This topic shows you how to create a Windows Presentation Foundation (WPF) control for use in your Windows Forms-based applications.</span></span>

<span data-ttu-id="660cf-104">V tomto podrobném návodu můžete provádět následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="660cf-104">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="660cf-105">Vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="660cf-105">Create the project.</span></span>

- <span data-ttu-id="660cf-106">Vytvořte nový ovládací prvek WPF.</span><span class="sxs-lookup"><span data-stu-id="660cf-106">Create a new WPF control.</span></span>

- <span data-ttu-id="660cf-107">Přidání nového ovládacího prvku WPF do formuláře Windows.</span><span class="sxs-lookup"><span data-stu-id="660cf-107">Add the new WPF control to a Windows Form.</span></span> <span data-ttu-id="660cf-108">Ovládací prvek WPF je hostován v <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="660cf-108">The WPF control is hosted in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="660cf-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="660cf-109">Prerequisites</span></span>

<span data-ttu-id="660cf-110">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="660cf-110">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="660cf-111">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="660cf-111">Visual Studio 2017</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="660cf-112">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="660cf-112">Creating the Project</span></span>

<span data-ttu-id="660cf-113">Prvním krokem je vytvoření projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="660cf-113">The first step is to create the Windows Forms project.</span></span> <span data-ttu-id="660cf-114">Otevřít Visual Studio a vytvořte nový **aplikace Windows Forms (.NET Framework)** projektu v jazyce Visual Basic nebo Visual C# s názvem `HostingWpf`.</span><span class="sxs-lookup"><span data-stu-id="660cf-114">Open Visual Studio and create a new **Windows Forms App (.NET Framework)** project in Visual Basic or Visual C# named `HostingWpf`.</span></span>

> [!NOTE]
> <span data-ttu-id="660cf-115">Při hostování obsahu WPF, jsou podporovány pouze projekty C# a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="660cf-115">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="creating-a-new-wpf-control"></a><span data-ttu-id="660cf-116">Vytvoření nového ovládacího prvku WPF</span><span class="sxs-lookup"><span data-stu-id="660cf-116">Creating a New WPF Control</span></span>

<span data-ttu-id="660cf-117">Vytvoření nového ovládacího prvku WPF a jeho přidání do projektu je stejně jednoduché jako přidání jakoukoli jinou položku do projektu.</span><span class="sxs-lookup"><span data-stu-id="660cf-117">Creating a new WPF control and adding it to your project is as easy as adding any other item to your project.</span></span> <span data-ttu-id="660cf-118">Návrhář formulářů Windows funguje s konkrétní druh ovládacího prvku s názvem *složeného ovládacího prvku*, nebo *uživatelský ovládací prvek*.</span><span class="sxs-lookup"><span data-stu-id="660cf-118">The Windows Forms Designer works with a particular kind of control named *composite control*, or *user control*.</span></span> <span data-ttu-id="660cf-119">Další informace o uživatelských ovládacích prvcích WPF naleznete v tématu <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="660cf-119">For more information about WPF user controls, see <xref:System.Windows.Controls.UserControl>.</span></span>

> [!NOTE]
> <span data-ttu-id="660cf-120"><xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> Zadejte pro WPF se liší od typ ovládacího prvku uživatel k dispozici ve Windows Forms, který se také nazývá <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="660cf-120">The <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> type for WPF is distinct from the user control type provided by Windows Forms, which is also named <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span></span>

### <a name="to-create-a-new-wpf-control"></a><span data-ttu-id="660cf-121">Chcete-li vytvořit nový ovládací prvek WPF</span><span class="sxs-lookup"><span data-stu-id="660cf-121">To create a new WPF control</span></span>

1. <span data-ttu-id="660cf-122">V **Průzkumníka řešení**, přidejte novou **Knihovna uživatelských ovládacích prvků WPF (.NET Framework)** projektu do řešení.</span><span class="sxs-lookup"><span data-stu-id="660cf-122">In **Solution Explorer**, add a new **WPF User Control Library (.NET Framework)** project to the solution.</span></span> <span data-ttu-id="660cf-123">Použít výchozí název knihovny ovládacích prvků `WpfControlLibrary1`.</span><span class="sxs-lookup"><span data-stu-id="660cf-123">Use the default name for the control library, `WpfControlLibrary1`.</span></span> <span data-ttu-id="660cf-124">Výchozí název ovládacího prvku je `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="660cf-124">The default control name is `UserControl1.xaml`.</span></span>

     <span data-ttu-id="660cf-125">Přidání nového ovládacího prvku má následující důsledky:</span><span class="sxs-lookup"><span data-stu-id="660cf-125">Adding the new control has the following effects:</span></span>

    - <span data-ttu-id="660cf-126">Přidání souboru UserControl1.xaml.</span><span class="sxs-lookup"><span data-stu-id="660cf-126">File UserControl1.xaml is added.</span></span>

    - <span data-ttu-id="660cf-127">Přidání souboru UserControl1.xaml.cs nebo UserControl1.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="660cf-127">Either file UserControl1.xaml.cs or UserControl1.xaml.vb is added.</span></span> <span data-ttu-id="660cf-128">Tento soubor obsahuje kód na pozadí pro obslužné rutiny událostí a jiné implementace.</span><span class="sxs-lookup"><span data-stu-id="660cf-128">This file contains the code-behind for event handlers and other implementation.</span></span>

    - <span data-ttu-id="660cf-129">Jsou přidány odkazy na sestavení WPF.</span><span class="sxs-lookup"><span data-stu-id="660cf-129">References to WPF assemblies are added.</span></span>

    - <span data-ttu-id="660cf-130">Soubor UserControl1.xaml otevře [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="660cf-130">File UserControl1.xaml opens in the [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].</span></span>

2. <span data-ttu-id="660cf-131">V návrhovém zobrazení, ujistěte se, že `UserControl1` zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="660cf-131">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="660cf-132">Další informace najdete v tématu [jak: Vyberte a přesuňte prvků na návrhové ploše](https://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span><span class="sxs-lookup"><span data-stu-id="660cf-132">For more information, see [How to: Select and Move Elements on the Design Surface](https://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>

3. <span data-ttu-id="660cf-133">V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastností **200**.</span><span class="sxs-lookup"><span data-stu-id="660cf-133">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="660cf-134">Z **nástrojů**, přetáhněte <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> ovládací prvek na návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="660cf-134">From the **Toolbox**, drag a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control onto the design surface.</span></span>

5. <span data-ttu-id="660cf-135">V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost **hostované obsahu**.</span><span class="sxs-lookup"><span data-stu-id="660cf-135">In the **Properties** window, set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="660cf-136">Obecně byste neměli hostit složitější obsahu WPF.</span><span class="sxs-lookup"><span data-stu-id="660cf-136">In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="660cf-137"><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Ovládací prvek se tady používá pouze pro ilustraci.</span><span class="sxs-lookup"><span data-stu-id="660cf-137">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>

6. <span data-ttu-id="660cf-138">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="660cf-138">Build the project.</span></span>

## <a name="adding-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="660cf-139">Přidání ovládacího prvku WPF na formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="660cf-139">Adding a WPF Control to a Windows Form</span></span>

<span data-ttu-id="660cf-140">Nový ovládací prvek WPF je připravená k použití ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="660cf-140">Your new WPF control is ready for use on the form.</span></span> <span data-ttu-id="660cf-141">Windows Forms používá <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku na hostování obsahu WPF.</span><span class="sxs-lookup"><span data-stu-id="660cf-141">Windows Forms uses the <xref:System.Windows.Forms.Integration.ElementHost> control to host WPF content.</span></span>

### <a name="to-add-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="660cf-142">Přidání ovládacího prvku WPF do formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="660cf-142">To add a WPF control to a Windows Form</span></span>

1. <span data-ttu-id="660cf-143">Otevřít `Form1` v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="660cf-143">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="660cf-144">V **nástrojů**, najít na kartě s popiskem **uživatelské ovládací prvky WPF WPFUserControlLibrary**.</span><span class="sxs-lookup"><span data-stu-id="660cf-144">In the **Toolbox**, find the tab labeled **WPFUserControlLibrary WPF User Controls**.</span></span>

3. <span data-ttu-id="660cf-145">Přetáhněte instance `UserControl1` do formuláře.</span><span class="sxs-lookup"><span data-stu-id="660cf-145">Drag an instance of `UserControl1` onto the form.</span></span>

    - <span data-ttu-id="660cf-146"><xref:System.Windows.Forms.Integration.ElementHost> Ovládací prvek je automaticky vytvořen ve formuláři pro hostování ovládacího prvku WPF.</span><span class="sxs-lookup"><span data-stu-id="660cf-146">An <xref:System.Windows.Forms.Integration.ElementHost> control is created automatically on the form to host the WPF control.</span></span>

    - <span data-ttu-id="660cf-147"><xref:System.Windows.Forms.Integration.ElementHost> Ovládací prvek má název `elementHost1` a **vlastnosti** okně můžete zobrazit jeho <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> je nastavena na **UserControl1**.</span><span class="sxs-lookup"><span data-stu-id="660cf-147">The <xref:System.Windows.Forms.Integration.ElementHost> control is named `elementHost1` and in the **Properties** window, you can see its <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl1**.</span></span>

    - <span data-ttu-id="660cf-148">Do projektu přidají odkazy na sestavení WPF.</span><span class="sxs-lookup"><span data-stu-id="660cf-148">References to WPF assemblies are added to the project.</span></span>

    - <span data-ttu-id="660cf-149">`elementHost1` Má ovládací prvek panelu inteligentních značek, které jsou uvedené dostupné možnosti hostování.</span><span class="sxs-lookup"><span data-stu-id="660cf-149">The `elementHost1` control has a smart tag panel that shows the available hosting options.</span></span>

4. <span data-ttu-id="660cf-150">V **ElementHost úlohy** panelu inteligentních značek, vyberte **ukotvit v nadřazeném kontejneru**.</span><span class="sxs-lookup"><span data-stu-id="660cf-150">In the **ElementHost Tasks** smart tag panel, select **Dock in parent container**.</span></span>

5. <span data-ttu-id="660cf-151">Stisknutím klávesy **F5** sestavíte a spustíte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="660cf-151">Press **F5** to build and run the application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="660cf-152">Další kroky</span><span class="sxs-lookup"><span data-stu-id="660cf-152">Next Steps</span></span>

<span data-ttu-id="660cf-153">Windows Forms a WPF jsou různé technologie, ale jsou určené ke úzce spolupracovat.</span><span class="sxs-lookup"><span data-stu-id="660cf-153">Windows Forms and WPF are different technologies, but they are designed to interoperate closely.</span></span> <span data-ttu-id="660cf-154">K poskytování bohatších vzhled a chování ve svých aplikacích, zkuste následující:</span><span class="sxs-lookup"><span data-stu-id="660cf-154">To provide richer appearance and behavior in your applications, try the following:</span></span>

- <span data-ttu-id="660cf-155">Hostování ovládacího prvku Windows Forms na stránce WPF.</span><span class="sxs-lookup"><span data-stu-id="660cf-155">Host a Windows Forms control in a WPF page.</span></span> <span data-ttu-id="660cf-156">Další informace najdete v tématu [názorný postup: Ovládací prvek hostování Windows Forms v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="660cf-156">For more information, see [Walkthrough: Hosting a Windows Forms Control in WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>

- <span data-ttu-id="660cf-157">Použití vizuálních stylů Windows Forms k vašemu obsahu WPF.</span><span class="sxs-lookup"><span data-stu-id="660cf-157">Apply Windows Forms visual styles to your WPF content.</span></span> <span data-ttu-id="660cf-158">Další informace najdete v tématu [jak: Povolení vizuálních stylů v hybridní aplikaci](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span><span class="sxs-lookup"><span data-stu-id="660cf-158">For more information, see [How to: Enable Visual Styles in a Hybrid Application](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span></span>

- <span data-ttu-id="660cf-159">Změna stylu obsahu WPF.</span><span class="sxs-lookup"><span data-stu-id="660cf-159">Change the style of your WPF content.</span></span> <span data-ttu-id="660cf-160">Další informace najdete v tématu [názorný postup: Určení stylu obsahu WPF](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md).</span><span class="sxs-lookup"><span data-stu-id="660cf-160">For more information, see [Walkthrough: Styling WPF Content](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="660cf-161">Viz také:</span><span class="sxs-lookup"><span data-stu-id="660cf-161">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="660cf-162">Migrace a interoperabilita</span><span class="sxs-lookup"><span data-stu-id="660cf-162">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="660cf-163">Používání ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="660cf-163">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)
- [<span data-ttu-id="660cf-164">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="660cf-164">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
