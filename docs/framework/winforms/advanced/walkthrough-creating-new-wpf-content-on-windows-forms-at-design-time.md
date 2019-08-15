---
title: 'Návod: Vytvoření nového obsahu WPF v modelu Windows Forms během návrhu'
ms.date: 08/18/2018
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
ms.openlocfilehash: 889e81053d4e2264755468446a4e1681216ae22e
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040367"
---
# <a name="walkthrough-create-new-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="ef767-102">Návod: Vytvoření nového obsahu WPF v model Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="ef767-102">Walkthrough: Create new WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="ef767-103">V tomto článku se dozvíte, jak vytvořit ovládací prvek Windows Presentation Foundation (WPF) pro použití v aplikacích založených na model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ef767-103">This article shows you how to create a Windows Presentation Foundation (WPF) control for use in your Windows Forms-based applications.</span></span>

<span data-ttu-id="ef767-104">V tomto návodu provedete následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="ef767-104">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="ef767-105">Vytvořte projekt.</span><span class="sxs-lookup"><span data-stu-id="ef767-105">Create the project.</span></span>

- <span data-ttu-id="ef767-106">Vytvořit nový ovládací prvek WPF.</span><span class="sxs-lookup"><span data-stu-id="ef767-106">Create a new WPF control.</span></span>

- <span data-ttu-id="ef767-107">Přidejte nový ovládací prvek WPF do formuláře Windows.</span><span class="sxs-lookup"><span data-stu-id="ef767-107">Add the new WPF control to a Windows Form.</span></span> <span data-ttu-id="ef767-108">Ovládací prvek WPF je hostován v <xref:System.Windows.Forms.Integration.ElementHost> ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="ef767-108">The WPF control is hosted in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ef767-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ef767-109">Prerequisites</span></span>

<span data-ttu-id="ef767-110">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="ef767-110">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="ef767-111">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ef767-111">Visual Studio</span></span>

## <a name="create-the-project"></a><span data-ttu-id="ef767-112">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="ef767-112">Create the project</span></span>

<span data-ttu-id="ef767-113">Prvním krokem je vytvoření projektu model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ef767-113">The first step is to create the Windows Forms project.</span></span> <span data-ttu-id="ef767-114">Otevřete Visual Studio a vytvořte nový projekt **aplikace model Windows Forms (.NET Framework)** v Visual Basic nebo vizuálu C# s názvem `HostingWpf`.</span><span class="sxs-lookup"><span data-stu-id="ef767-114">Open Visual Studio and create a new **Windows Forms App (.NET Framework)** project in Visual Basic or Visual C# named `HostingWpf`.</span></span>

> [!NOTE]
> <span data-ttu-id="ef767-115">Při hostování obsahu WPF jsou podporovány C# pouze projekty a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ef767-115">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-a-new-wpf-control"></a><span data-ttu-id="ef767-116">Vytvořit nový ovládací prvek WPF</span><span class="sxs-lookup"><span data-stu-id="ef767-116">Create a new WPF control</span></span>

<span data-ttu-id="ef767-117">Vytvoření nového ovládacího prvku WPF a jeho přidání do projektu je stejně snadné jako přidání jakékoli jiné položky do projektu.</span><span class="sxs-lookup"><span data-stu-id="ef767-117">Creating a new WPF control and adding it to your project is as easy as adding any other item to your project.</span></span> <span data-ttu-id="ef767-118">Návrhář formulářů pracuje s konkrétním druhem ovládacího prvku s názvem *složený ovládací*prvek nebo *uživatelským ovládacím prvkem*.</span><span class="sxs-lookup"><span data-stu-id="ef767-118">The Windows Forms Designer works with a particular kind of control named *composite control*, or *user control*.</span></span> <span data-ttu-id="ef767-119">Další informace o uživatelských ovládacích prvcích WPF naleznete v <xref:System.Windows.Controls.UserControl>tématu.</span><span class="sxs-lookup"><span data-stu-id="ef767-119">For more information about WPF user controls, see <xref:System.Windows.Controls.UserControl>.</span></span>

> [!NOTE]
> <span data-ttu-id="ef767-120">Typ pro WPF je odlišný od typu uživatelského ovládacího prvku, který poskytuje model Windows Forms, který je také pojmenován <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>. <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ef767-120">The <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> type for WPF is distinct from the user control type provided by Windows Forms, which is also named <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="ef767-121">Vytvoření nového ovládacího prvku WPF:</span><span class="sxs-lookup"><span data-stu-id="ef767-121">To create a new WPF control:</span></span>

1. <span data-ttu-id="ef767-122">V **Průzkumník řešení**přidejte do řešení nový projekt **knihovny uživatelských ovládacích prvků WPF (.NET Framework)** .</span><span class="sxs-lookup"><span data-stu-id="ef767-122">In **Solution Explorer**, add a new **WPF User Control Library (.NET Framework)** project to the solution.</span></span> <span data-ttu-id="ef767-123">Pro knihovnu `WpfControlLibrary1`ovládacích prvků použijte výchozí název.</span><span class="sxs-lookup"><span data-stu-id="ef767-123">Use the default name for the control library, `WpfControlLibrary1`.</span></span> <span data-ttu-id="ef767-124">Výchozí název ovládacího prvku je `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="ef767-124">The default control name is `UserControl1.xaml`.</span></span>

     <span data-ttu-id="ef767-125">Přidání nového ovládacího prvku má následující důsledky:</span><span class="sxs-lookup"><span data-stu-id="ef767-125">Adding the new control has the following effects:</span></span>

    - <span data-ttu-id="ef767-126">Byl přidán soubor UserControl1. XAML.</span><span class="sxs-lookup"><span data-stu-id="ef767-126">File UserControl1.xaml is added.</span></span>

    - <span data-ttu-id="ef767-127">Přidal se soubor UserControl1.xaml.cs nebo UserControl1. XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="ef767-127">Either file UserControl1.xaml.cs or UserControl1.xaml.vb is added.</span></span> <span data-ttu-id="ef767-128">Tento soubor obsahuje kód na pozadí pro obslužné rutiny událostí a další implementace.</span><span class="sxs-lookup"><span data-stu-id="ef767-128">This file contains the code-behind for event handlers and other implementation.</span></span>

    - <span data-ttu-id="ef767-129">Přidaly se odkazy na sestavení WPF.</span><span class="sxs-lookup"><span data-stu-id="ef767-129">References to WPF assemblies are added.</span></span>

    - <span data-ttu-id="ef767-130">Soubor UserControl1. XAML se otevře v [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ef767-130">File UserControl1.xaml opens in the [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].</span></span>

2. <span data-ttu-id="ef767-131">V zobrazení Návrh se ujistěte, že `UserControl1` je vybraná možnost.</span><span class="sxs-lookup"><span data-stu-id="ef767-131">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="ef767-132">Další informace najdete v tématu [jak: Vyberte a přesuňte prvky na Návrhová plocha](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ef767-132">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>

3. <span data-ttu-id="ef767-133">V okně **vlastnosti** nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> vlastností a <xref:System.Windows.FrameworkElement.Height%2A> na **200**.</span><span class="sxs-lookup"><span data-stu-id="ef767-133">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="ef767-134">Z **panelu nástrojů**přetáhněte <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> ovládací prvek na návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="ef767-134">From the **Toolbox**, drag a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control onto the design surface.</span></span>

5. <span data-ttu-id="ef767-135">V okně **vlastnosti** nastavte hodnotu <xref:System.Windows.Controls.TextBox.Text%2A> vlastnosti na **hostovaný obsah**.</span><span class="sxs-lookup"><span data-stu-id="ef767-135">In the **Properties** window, set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ef767-136">Obecně byste měli hostovat propracovanější obsah WPF.</span><span class="sxs-lookup"><span data-stu-id="ef767-136">In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="ef767-137"><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Ovládací prvek slouží pouze pro ilustrativní účely.</span><span class="sxs-lookup"><span data-stu-id="ef767-137">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>

6. <span data-ttu-id="ef767-138">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="ef767-138">Build the project.</span></span>

## <a name="add-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="ef767-139">Přidání ovládacího prvku WPF do formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="ef767-139">Add a WPF control to a Windows Form</span></span>

<span data-ttu-id="ef767-140">Nový ovládací prvek WPF je připravený k použití ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="ef767-140">Your new WPF control is ready for use on the form.</span></span> <span data-ttu-id="ef767-141">Model Windows Forms používá <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek k hostování obsahu WPF.</span><span class="sxs-lookup"><span data-stu-id="ef767-141">Windows Forms uses the <xref:System.Windows.Forms.Integration.ElementHost> control to host WPF content.</span></span>

<span data-ttu-id="ef767-142">Přidání ovládacího prvku WPF do formuláře Windows:</span><span class="sxs-lookup"><span data-stu-id="ef767-142">To add a WPF control to a Windows Form:</span></span>

1. <span data-ttu-id="ef767-143">Otevřete `Form1` v Návrhář formulářů.</span><span class="sxs-lookup"><span data-stu-id="ef767-143">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="ef767-144">V **sadě nástrojů**Najděte kartu s názvem **WPFUserControlLibrary uživatelské ovládací prvky WPF**.</span><span class="sxs-lookup"><span data-stu-id="ef767-144">In the **Toolbox**, find the tab labeled **WPFUserControlLibrary WPF User Controls**.</span></span>

3. <span data-ttu-id="ef767-145">Přetáhněte instanci `UserControl1` do formuláře.</span><span class="sxs-lookup"><span data-stu-id="ef767-145">Drag an instance of `UserControl1` onto the form.</span></span>

    - <span data-ttu-id="ef767-146"><xref:System.Windows.Forms.Integration.ElementHost> Ovládací prvek je vytvořen automaticky na formuláři pro hostování ovládacího prvku WPF.</span><span class="sxs-lookup"><span data-stu-id="ef767-146">An <xref:System.Windows.Forms.Integration.ElementHost> control is created automatically on the form to host the WPF control.</span></span>

    - <span data-ttu-id="ef767-147">`elementHost1` <xref:System.Windows.Forms.Integration.ElementHost.Child%2A>Ovládací prvek je pojmenován a v okně Vlastnosti lze zobrazit jeho vlastnost nastavenou na UserControl1. <xref:System.Windows.Forms.Integration.ElementHost></span><span class="sxs-lookup"><span data-stu-id="ef767-147">The <xref:System.Windows.Forms.Integration.ElementHost> control is named `elementHost1` and in the **Properties** window, you can see its <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl1**.</span></span>

    - <span data-ttu-id="ef767-148">Odkazy na sestavení WPF jsou přidány do projektu.</span><span class="sxs-lookup"><span data-stu-id="ef767-148">References to WPF assemblies are added to the project.</span></span>

    - <span data-ttu-id="ef767-149">`elementHost1` Ovládací prvek má panel inteligentních značek, který zobrazuje dostupné možnosti hostování.</span><span class="sxs-lookup"><span data-stu-id="ef767-149">The `elementHost1` control has a smart tag panel that shows the available hosting options.</span></span>

4. <span data-ttu-id="ef767-150">Na panelu inteligentních značek **úlohy ElementHost** vyberte **Dock v nadřazeném kontejneru**.</span><span class="sxs-lookup"><span data-stu-id="ef767-150">In the **ElementHost Tasks** smart tag panel, select **Dock in parent container**.</span></span>

5. <span data-ttu-id="ef767-151">Stisknutím klávesy **F5** Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ef767-151">Press **F5** to build and run the application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ef767-152">Další postup</span><span class="sxs-lookup"><span data-stu-id="ef767-152">Next steps</span></span>

<span data-ttu-id="ef767-153">Model Windows Forms a WPF jsou různé technologie, ale jsou navržené tak, aby úzce fungovaly.</span><span class="sxs-lookup"><span data-stu-id="ef767-153">Windows Forms and WPF are different technologies, but they are designed to interoperate closely.</span></span> <span data-ttu-id="ef767-154">Pokud chcete ve svých aplikacích zajistit rozsáhlejší vzhled a chování, vyzkoušejte následující:</span><span class="sxs-lookup"><span data-stu-id="ef767-154">To provide richer appearance and behavior in your applications, try the following:</span></span>

- <span data-ttu-id="ef767-155">Hostování ovládacího prvku model Windows Forms na stránce WPF.</span><span class="sxs-lookup"><span data-stu-id="ef767-155">Host a Windows Forms control in a WPF page.</span></span> <span data-ttu-id="ef767-156">Další informace najdete v tématu [Návod: Hostování ovládacího prvku model Windows Forms v subsystému WPF](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="ef767-156">For more information, see [Walkthrough: Hosting a Windows Forms Control in WPF](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>

- <span data-ttu-id="ef767-157">Použijte model Windows Forms vizuální styly pro obsah WPF.</span><span class="sxs-lookup"><span data-stu-id="ef767-157">Apply Windows Forms visual styles to your WPF content.</span></span> <span data-ttu-id="ef767-158">Další informace najdete v tématu [jak: Povolit vizuální styly v hybridní aplikaci](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)</span><span class="sxs-lookup"><span data-stu-id="ef767-158">For more information, see [How to: Enable Visual Styles in a Hybrid Application](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span></span>

- <span data-ttu-id="ef767-159">Změňte styl obsahu WPF.</span><span class="sxs-lookup"><span data-stu-id="ef767-159">Change the style of your WPF content.</span></span> <span data-ttu-id="ef767-160">Další informace najdete v tématu [Návod: Stylování obsahu](walkthrough-styling-wpf-content.md)WPF.</span><span class="sxs-lookup"><span data-stu-id="ef767-160">For more information, see [Walkthrough: Styling WPF Content](walkthrough-styling-wpf-content.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ef767-161">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ef767-161">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="ef767-162">Migrace a interoperabilita</span><span class="sxs-lookup"><span data-stu-id="ef767-162">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="ef767-163">Používání ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="ef767-163">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="ef767-164">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ef767-164">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
