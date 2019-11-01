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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fc6f988d6ffd270eba4abe277ca34fa2eeec56fd
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197421"
---
# <a name="walkthrough-create-new-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="dde44-102">Návod: vytvoření nového obsahu WPF v model Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="dde44-102">Walkthrough: Create new WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="dde44-103">V tomto článku se dozvíte, jak vytvořit ovládací prvek Windows Presentation Foundation (WPF) pro použití v aplikacích založených na model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="dde44-103">This article shows you how to create a Windows Presentation Foundation (WPF) control for use in your Windows Forms-based applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dde44-104">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dde44-104">Prerequisites</span></span>

<span data-ttu-id="dde44-105">K dokončení tohoto Názorného postupu potřebujete Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dde44-105">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="dde44-106">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="dde44-106">Create the project</span></span>

<span data-ttu-id="dde44-107">Otevřete Visual Studio a vytvořte nový projekt **aplikace model Windows Forms (.NET Framework)** v Visual Basic nebo vizuálu C# s názvem `HostingWpf`.</span><span class="sxs-lookup"><span data-stu-id="dde44-107">Open Visual Studio and create a new **Windows Forms App (.NET Framework)** project in Visual Basic or Visual C# named `HostingWpf`.</span></span>

> [!NOTE]
> <span data-ttu-id="dde44-108">Při hostování obsahu WPF jsou podporovány C# pouze projekty a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="dde44-108">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-a-new-wpf-control"></a><span data-ttu-id="dde44-109">Vytvořit nový ovládací prvek WPF</span><span class="sxs-lookup"><span data-stu-id="dde44-109">Create a new WPF control</span></span>

<span data-ttu-id="dde44-110">Vytvoření nového ovládacího prvku WPF a jeho přidání do projektu je stejně snadné jako přidání jakékoli jiné položky do projektu.</span><span class="sxs-lookup"><span data-stu-id="dde44-110">Creating a new WPF control and adding it to your project is as easy as adding any other item to your project.</span></span> <span data-ttu-id="dde44-111">Návrhář formulářů pracuje s konkrétním druhem ovládacího prvku s názvem *složený ovládací*prvek nebo *uživatelským ovládacím prvkem*.</span><span class="sxs-lookup"><span data-stu-id="dde44-111">The Windows Forms Designer works with a particular kind of control named *composite control*, or *user control*.</span></span> <span data-ttu-id="dde44-112">Další informace o uživatelských ovládacích prvcích WPF naleznete v tématu <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="dde44-112">For more information about WPF user controls, see <xref:System.Windows.Controls.UserControl>.</span></span>

> [!NOTE]
> <span data-ttu-id="dde44-113">Typ <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> pro WPF je odlišný od typu uživatelského ovládacího prvku, který poskytuje model Windows Forms, který je také pojmenován <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dde44-113">The <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> type for WPF is distinct from the user control type provided by Windows Forms, which is also named <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="dde44-114">Vytvoření nového ovládacího prvku WPF:</span><span class="sxs-lookup"><span data-stu-id="dde44-114">To create a new WPF control:</span></span>

1. <span data-ttu-id="dde44-115">V **Průzkumník řešení**přidejte do řešení nový projekt **knihovny uživatelských ovládacích prvků WPF (.NET Framework)** .</span><span class="sxs-lookup"><span data-stu-id="dde44-115">In **Solution Explorer**, add a new **WPF User Control Library (.NET Framework)** project to the solution.</span></span> <span data-ttu-id="dde44-116">Použijte výchozí název knihovny ovládacích prvků `WpfControlLibrary1`.</span><span class="sxs-lookup"><span data-stu-id="dde44-116">Use the default name for the control library, `WpfControlLibrary1`.</span></span> <span data-ttu-id="dde44-117">Výchozí název ovládacího prvku je `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="dde44-117">The default control name is `UserControl1.xaml`.</span></span>

   <span data-ttu-id="dde44-118">Přidání nového ovládacího prvku má následující důsledky:</span><span class="sxs-lookup"><span data-stu-id="dde44-118">Adding the new control has the following effects:</span></span>

   - <span data-ttu-id="dde44-119">Byl přidán soubor UserControl1. XAML.</span><span class="sxs-lookup"><span data-stu-id="dde44-119">File UserControl1.xaml is added.</span></span>

   - <span data-ttu-id="dde44-120">Přidal se soubor UserControl1.xaml.cs (nebo UserControl1. XAML. vb).</span><span class="sxs-lookup"><span data-stu-id="dde44-120">File UserControl1.xaml.cs (or UserControl1.xaml.vb) is added.</span></span> <span data-ttu-id="dde44-121">Tento soubor obsahuje kód na pozadí pro obslužné rutiny událostí a další implementace.</span><span class="sxs-lookup"><span data-stu-id="dde44-121">This file contains the code-behind for event handlers and other implementation.</span></span>

   - <span data-ttu-id="dde44-122">Přidaly se odkazy na sestavení WPF.</span><span class="sxs-lookup"><span data-stu-id="dde44-122">References to WPF assemblies are added.</span></span>

   - <span data-ttu-id="dde44-123">Soubor UserControl1. XAML se otevře v Návrháři WPF pro Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dde44-123">File UserControl1.xaml opens in the WPF Designer for Visual Studio.</span></span>

2. <span data-ttu-id="dde44-124">V zobrazení Návrh se ujistěte, že je vybrána možnost `UserControl1`.</span><span class="sxs-lookup"><span data-stu-id="dde44-124">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="dde44-125">V okně **vlastnosti** nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a vlastnosti <xref:System.Windows.FrameworkElement.Height%2A> na **200**.</span><span class="sxs-lookup"><span data-stu-id="dde44-125">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="dde44-126">Z **panelu nástrojů**přetáhněte ovládací prvek <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> na návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="dde44-126">From the **Toolbox**, drag a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control onto the design surface.</span></span>

5. <span data-ttu-id="dde44-127">V okně **vlastnosti** nastavte hodnotu vlastnosti <xref:System.Windows.Controls.TextBox.Text%2A> na **hostovaný obsah**.</span><span class="sxs-lookup"><span data-stu-id="dde44-127">In the **Properties** window, set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="dde44-128">Obecně byste měli hostovat propracovanější obsah WPF.</span><span class="sxs-lookup"><span data-stu-id="dde44-128">In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="dde44-129"><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> ovládací prvek slouží pouze pro ilustrativní účely.</span><span class="sxs-lookup"><span data-stu-id="dde44-129">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>

6. <span data-ttu-id="dde44-130">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="dde44-130">Build the project.</span></span>

## <a name="add-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="dde44-131">Přidání ovládacího prvku WPF do formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="dde44-131">Add a WPF control to a Windows Form</span></span>

<span data-ttu-id="dde44-132">Nový ovládací prvek WPF je připravený k použití ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="dde44-132">Your new WPF control is ready for use on the form.</span></span> <span data-ttu-id="dde44-133">Model Windows Forms používá ovládací prvek <xref:System.Windows.Forms.Integration.ElementHost> k hostování obsahu WPF.</span><span class="sxs-lookup"><span data-stu-id="dde44-133">Windows Forms uses the <xref:System.Windows.Forms.Integration.ElementHost> control to host WPF content.</span></span>

<span data-ttu-id="dde44-134">Přidání ovládacího prvku WPF do formuláře Windows:</span><span class="sxs-lookup"><span data-stu-id="dde44-134">To add a WPF control to a Windows Form:</span></span>

1. <span data-ttu-id="dde44-135">Otevřete `Form1` v Návrhář formulářů.</span><span class="sxs-lookup"><span data-stu-id="dde44-135">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="dde44-136">V **sadě nástrojů**Najděte kartu s názvem **WPFUserControlLibrary uživatelské ovládací prvky WPF**.</span><span class="sxs-lookup"><span data-stu-id="dde44-136">In the **Toolbox**, find the tab labeled **WPFUserControlLibrary WPF User Controls**.</span></span>

3. <span data-ttu-id="dde44-137">Přetáhněte instanci `UserControl1` do formuláře.</span><span class="sxs-lookup"><span data-stu-id="dde44-137">Drag an instance of `UserControl1` onto the form.</span></span>

    - <span data-ttu-id="dde44-138"><xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek je automaticky vytvořen na formuláři pro hostování ovládacího prvku WPF.</span><span class="sxs-lookup"><span data-stu-id="dde44-138">An <xref:System.Windows.Forms.Integration.ElementHost> control is created automatically on the form to host the WPF control.</span></span>

    - <span data-ttu-id="dde44-139">Ovládací prvek <xref:System.Windows.Forms.Integration.ElementHost> je pojmenován `elementHost1` a v okně **vlastnosti** lze zobrazit jeho vlastnost <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> je nastavena na hodnotu **UserControl1**.</span><span class="sxs-lookup"><span data-stu-id="dde44-139">The <xref:System.Windows.Forms.Integration.ElementHost> control is named `elementHost1` and in the **Properties** window, you can see its <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl1**.</span></span>

    - <span data-ttu-id="dde44-140">Odkazy na sestavení WPF jsou přidány do projektu.</span><span class="sxs-lookup"><span data-stu-id="dde44-140">References to WPF assemblies are added to the project.</span></span>

    - <span data-ttu-id="dde44-141">Ovládací prvek `elementHost1` má panel inteligentních značek, který zobrazuje dostupné možnosti hostování.</span><span class="sxs-lookup"><span data-stu-id="dde44-141">The `elementHost1` control has a smart tag panel that shows the available hosting options.</span></span>

4. <span data-ttu-id="dde44-142">Na panelu inteligentních značek **úlohy ElementHost** vyberte **Dock v nadřazeném kontejneru**.</span><span class="sxs-lookup"><span data-stu-id="dde44-142">In the **ElementHost Tasks** smart tag panel, select **Dock in parent container**.</span></span>

5. <span data-ttu-id="dde44-143">Stisknutím klávesy **F5** Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="dde44-143">Press **F5** to build and run the application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="dde44-144">Další kroky</span><span class="sxs-lookup"><span data-stu-id="dde44-144">Next steps</span></span>

<span data-ttu-id="dde44-145">Model Windows Forms a WPF jsou různé technologie, ale jsou navržené tak, aby úzce fungovaly.</span><span class="sxs-lookup"><span data-stu-id="dde44-145">Windows Forms and WPF are different technologies, but they are designed to interoperate closely.</span></span> <span data-ttu-id="dde44-146">Pokud chcete ve svých aplikacích zajistit rozsáhlejší vzhled a chování, vyzkoušejte následující:</span><span class="sxs-lookup"><span data-stu-id="dde44-146">To provide richer appearance and behavior in your applications, try the following:</span></span>

- <span data-ttu-id="dde44-147">Hostování ovládacího prvku model Windows Forms na stránce WPF.</span><span class="sxs-lookup"><span data-stu-id="dde44-147">Host a Windows Forms control in a WPF page.</span></span> <span data-ttu-id="dde44-148">Další informace naleznete v tématu [Návod: hostování ovládacího prvku model Windows Forms v](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)subsystému WPF.</span><span class="sxs-lookup"><span data-stu-id="dde44-148">For more information, see [Walkthrough: Hosting a Windows Forms Control in WPF](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>

- <span data-ttu-id="dde44-149">Použijte model Windows Forms vizuální styly pro obsah WPF.</span><span class="sxs-lookup"><span data-stu-id="dde44-149">Apply Windows Forms visual styles to your WPF content.</span></span> <span data-ttu-id="dde44-150">Další informace najdete v tématu [Postup: Povolení vizuálních stylů v hybridní aplikaci](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span><span class="sxs-lookup"><span data-stu-id="dde44-150">For more information, see [How to: Enable Visual Styles in a Hybrid Application](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span></span>

- <span data-ttu-id="dde44-151">Změňte styl obsahu WPF.</span><span class="sxs-lookup"><span data-stu-id="dde44-151">Change the style of your WPF content.</span></span> <span data-ttu-id="dde44-152">Další informace najdete v tématu [Návod: určení stylu obsahu WPF](walkthrough-styling-wpf-content.md).</span><span class="sxs-lookup"><span data-stu-id="dde44-152">For more information, see [Walkthrough: Styling WPF Content](walkthrough-styling-wpf-content.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dde44-153">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dde44-153">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="dde44-154">Migrace a interoperabilita</span><span class="sxs-lookup"><span data-stu-id="dde44-154">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="dde44-155">Používání ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="dde44-155">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="dde44-156">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dde44-156">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
