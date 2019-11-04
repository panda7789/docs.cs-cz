---
title: 'Návod: Vytvoření nového obsahu WPF ve Windows Forms během návrhu'
ms.date: 08/18/2018
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 395543a3141af66038cabef9a3c9fed40a36b47e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460650"
---
# <a name="walkthrough-create-new-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="e1e1e-102">Návod: vytvoření nového obsahu WPF v model Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="e1e1e-102">Walkthrough: Create new WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="e1e1e-103">V tomto článku se dozvíte, jak vytvořit ovládací prvek Windows Presentation Foundation (WPF) pro použití v aplikacích založených na model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-103">This article shows you how to create a Windows Presentation Foundation (WPF) control for use in your Windows Forms-based applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e1e1e-104">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e1e1e-104">Prerequisites</span></span>

<span data-ttu-id="e1e1e-105">K dokončení tohoto Názorného postupu potřebujete Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-105">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="e1e1e-106">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="e1e1e-106">Create the project</span></span>

<span data-ttu-id="e1e1e-107">Otevřete Visual Studio a vytvořte nový projekt **aplikace model Windows Forms (.NET Framework)** v Visual Basic nebo vizuálu C# s názvem `HostingWpf`.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-107">Open Visual Studio and create a new **Windows Forms App (.NET Framework)** project in Visual Basic or Visual C# named `HostingWpf`.</span></span>

> [!NOTE]
> <span data-ttu-id="e1e1e-108">Při hostování obsahu WPF jsou podporovány C# pouze projekty a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-108">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-a-new-wpf-control"></a><span data-ttu-id="e1e1e-109">Vytvořit nový ovládací prvek WPF</span><span class="sxs-lookup"><span data-stu-id="e1e1e-109">Create a new WPF control</span></span>

<span data-ttu-id="e1e1e-110">Vytvoření nového ovládacího prvku WPF a jeho přidání do projektu je stejně snadné jako přidání jakékoli jiné položky do projektu.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-110">Creating a new WPF control and adding it to your project is as easy as adding any other item to your project.</span></span> <span data-ttu-id="e1e1e-111">Návrhář formulářů pracuje s konkrétním druhem ovládacího prvku s názvem *složený ovládací*prvek nebo *uživatelským ovládacím prvkem*.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-111">The Windows Forms Designer works with a particular kind of control named *composite control*, or *user control*.</span></span> <span data-ttu-id="e1e1e-112">Další informace o uživatelských ovládacích prvcích WPF naleznete v tématu <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-112">For more information about WPF user controls, see <xref:System.Windows.Controls.UserControl>.</span></span>

> [!NOTE]
> <span data-ttu-id="e1e1e-113">Typ <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> pro WPF je odlišný od typu uživatelského ovládacího prvku, který poskytuje model Windows Forms, který je také pojmenován <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-113">The <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> type for WPF is distinct from the user control type provided by Windows Forms, which is also named <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="e1e1e-114">Vytvoření nového ovládacího prvku WPF:</span><span class="sxs-lookup"><span data-stu-id="e1e1e-114">To create a new WPF control:</span></span>

1. <span data-ttu-id="e1e1e-115">V **Průzkumník řešení**přidejte do řešení nový projekt **knihovny uživatelských ovládacích prvků WPF (.NET Framework)** .</span><span class="sxs-lookup"><span data-stu-id="e1e1e-115">In **Solution Explorer**, add a new **WPF User Control Library (.NET Framework)** project to the solution.</span></span> <span data-ttu-id="e1e1e-116">Použijte výchozí název knihovny ovládacích prvků `WpfControlLibrary1`.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-116">Use the default name for the control library, `WpfControlLibrary1`.</span></span> <span data-ttu-id="e1e1e-117">Výchozí název ovládacího prvku je `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-117">The default control name is `UserControl1.xaml`.</span></span>

   <span data-ttu-id="e1e1e-118">Přidání nového ovládacího prvku má následující důsledky:</span><span class="sxs-lookup"><span data-stu-id="e1e1e-118">Adding the new control has the following effects:</span></span>

   - <span data-ttu-id="e1e1e-119">Byl přidán soubor UserControl1. XAML.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-119">File UserControl1.xaml is added.</span></span>

   - <span data-ttu-id="e1e1e-120">Přidal se soubor UserControl1.xaml.cs (nebo UserControl1. XAML. vb).</span><span class="sxs-lookup"><span data-stu-id="e1e1e-120">File UserControl1.xaml.cs (or UserControl1.xaml.vb) is added.</span></span> <span data-ttu-id="e1e1e-121">Tento soubor obsahuje kód na pozadí pro obslužné rutiny událostí a další implementace.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-121">This file contains the code-behind for event handlers and other implementation.</span></span>

   - <span data-ttu-id="e1e1e-122">Přidaly se odkazy na sestavení WPF.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-122">References to WPF assemblies are added.</span></span>

   - <span data-ttu-id="e1e1e-123">Soubor UserControl1. XAML se otevře v Návrháři WPF pro Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-123">File UserControl1.xaml opens in the WPF Designer for Visual Studio.</span></span>

2. <span data-ttu-id="e1e1e-124">V zobrazení Návrh se ujistěte, že je vybrána možnost `UserControl1`.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-124">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="e1e1e-125">V okně **vlastnosti** nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a vlastnosti <xref:System.Windows.FrameworkElement.Height%2A> na **200**.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-125">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="e1e1e-126">Z **panelu nástrojů**přetáhněte ovládací prvek <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> na návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-126">From the **Toolbox**, drag a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control onto the design surface.</span></span>

5. <span data-ttu-id="e1e1e-127">V okně **vlastnosti** nastavte hodnotu vlastnosti <xref:System.Windows.Controls.TextBox.Text%2A> na **hostovaný obsah**.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-127">In the **Properties** window, set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="e1e1e-128">Obecně byste měli hostovat propracovanější obsah WPF.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-128">In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="e1e1e-129"><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> ovládací prvek slouží pouze pro ilustrativní účely.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-129">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>

6. <span data-ttu-id="e1e1e-130">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-130">Build the project.</span></span>

## <a name="add-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="e1e1e-131">Přidání ovládacího prvku WPF do formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="e1e1e-131">Add a WPF control to a Windows Form</span></span>

<span data-ttu-id="e1e1e-132">Nový ovládací prvek WPF je připravený k použití ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-132">Your new WPF control is ready for use on the form.</span></span> <span data-ttu-id="e1e1e-133">Model Windows Forms používá ovládací prvek <xref:System.Windows.Forms.Integration.ElementHost> k hostování obsahu WPF.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-133">Windows Forms uses the <xref:System.Windows.Forms.Integration.ElementHost> control to host WPF content.</span></span>

<span data-ttu-id="e1e1e-134">Přidání ovládacího prvku WPF do formuláře Windows:</span><span class="sxs-lookup"><span data-stu-id="e1e1e-134">To add a WPF control to a Windows Form:</span></span>

1. <span data-ttu-id="e1e1e-135">Otevřete `Form1` v Návrhář formulářů.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-135">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="e1e1e-136">V **sadě nástrojů**Najděte kartu s názvem **WPFUserControlLibrary uživatelské ovládací prvky WPF**.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-136">In the **Toolbox**, find the tab labeled **WPFUserControlLibrary WPF User Controls**.</span></span>

3. <span data-ttu-id="e1e1e-137">Přetáhněte instanci `UserControl1` do formuláře.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-137">Drag an instance of `UserControl1` onto the form.</span></span>

    - <span data-ttu-id="e1e1e-138"><xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek je automaticky vytvořen na formuláři pro hostování ovládacího prvku WPF.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-138">An <xref:System.Windows.Forms.Integration.ElementHost> control is created automatically on the form to host the WPF control.</span></span>

    - <span data-ttu-id="e1e1e-139">Ovládací prvek <xref:System.Windows.Forms.Integration.ElementHost> je pojmenován `elementHost1` a v okně **vlastnosti** lze zobrazit jeho vlastnost <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> je nastavena na hodnotu **UserControl1**.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-139">The <xref:System.Windows.Forms.Integration.ElementHost> control is named `elementHost1` and in the **Properties** window, you can see its <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl1**.</span></span>

    - <span data-ttu-id="e1e1e-140">Odkazy na sestavení WPF jsou přidány do projektu.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-140">References to WPF assemblies are added to the project.</span></span>

    - <span data-ttu-id="e1e1e-141">Ovládací prvek `elementHost1` má panel inteligentních značek, který zobrazuje dostupné možnosti hostování.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-141">The `elementHost1` control has a smart tag panel that shows the available hosting options.</span></span>

4. <span data-ttu-id="e1e1e-142">Na panelu inteligentních značek **úlohy ElementHost** vyberte **Dock v nadřazeném kontejneru**.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-142">In the **ElementHost Tasks** smart tag panel, select **Dock in parent container**.</span></span>

5. <span data-ttu-id="e1e1e-143">Stisknutím klávesy **F5** Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-143">Press **F5** to build and run the application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e1e1e-144">Další kroky</span><span class="sxs-lookup"><span data-stu-id="e1e1e-144">Next steps</span></span>

<span data-ttu-id="e1e1e-145">Model Windows Forms a WPF jsou různé technologie, ale jsou navržené tak, aby úzce fungovaly.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-145">Windows Forms and WPF are different technologies, but they are designed to interoperate closely.</span></span> <span data-ttu-id="e1e1e-146">Pokud chcete ve svých aplikacích zajistit rozsáhlejší vzhled a chování, vyzkoušejte následující:</span><span class="sxs-lookup"><span data-stu-id="e1e1e-146">To provide richer appearance and behavior in your applications, try the following:</span></span>

- <span data-ttu-id="e1e1e-147">Hostování ovládacího prvku model Windows Forms na stránce WPF.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-147">Host a Windows Forms control in a WPF page.</span></span> <span data-ttu-id="e1e1e-148">Další informace naleznete v tématu [Návod: hostování ovládacího prvku model Windows Forms v](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)subsystému WPF.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-148">For more information, see [Walkthrough: Hosting a Windows Forms Control in WPF](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>

- <span data-ttu-id="e1e1e-149">Použijte model Windows Forms vizuální styly pro obsah WPF.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-149">Apply Windows Forms visual styles to your WPF content.</span></span> <span data-ttu-id="e1e1e-150">Další informace najdete v tématu [Postup: Povolení vizuálních stylů v hybridní aplikaci](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span><span class="sxs-lookup"><span data-stu-id="e1e1e-150">For more information, see [How to: Enable Visual Styles in a Hybrid Application](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span></span>

- <span data-ttu-id="e1e1e-151">Změňte styl obsahu WPF.</span><span class="sxs-lookup"><span data-stu-id="e1e1e-151">Change the style of your WPF content.</span></span> <span data-ttu-id="e1e1e-152">Další informace najdete v tématu [Návod: určení stylu obsahu WPF](walkthrough-styling-wpf-content.md).</span><span class="sxs-lookup"><span data-stu-id="e1e1e-152">For more information, see [Walkthrough: Styling WPF Content](walkthrough-styling-wpf-content.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e1e1e-153">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e1e1e-153">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="e1e1e-154">Migrace a interoperabilita</span><span class="sxs-lookup"><span data-stu-id="e1e1e-154">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="e1e1e-155">Používání ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="e1e1e-155">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="e1e1e-156">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e1e1e-156">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
