---
title: 'Návod: Určení stylu obsahu WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
ms.openlocfilehash: b689bb7299d541708db7ae786bff62a1007608e5
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557893"
---
# <a name="walkthrough-style-wpf-content"></a><span data-ttu-id="9bb84-102">Návod: Stylu obsahu WPF</span><span class="sxs-lookup"><span data-stu-id="9bb84-102">Walkthrough: Style WPF content</span></span>

<span data-ttu-id="9bb84-103">Tento názorný postup ukazují, jak použít používání stylů pro ovládací prvek Windows Presentation Foundation (WPF) hostovaného ve formuláři Windows.</span><span class="sxs-lookup"><span data-stu-id="9bb84-103">This walkthrough show you how to apply styling to a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>

 <span data-ttu-id="9bb84-104">V tomto podrobném návodu můžete provádět následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="9bb84-104">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="9bb84-105">Vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="9bb84-105">Create the project.</span></span>

- <span data-ttu-id="9bb84-106">Vytvořte typ ovládacího prvku WPF.</span><span class="sxs-lookup"><span data-stu-id="9bb84-106">Create the WPF control type.</span></span>

- <span data-ttu-id="9bb84-107">Použít styl WPF control.a</span><span class="sxs-lookup"><span data-stu-id="9bb84-107">Apply a style to the WPF control.a</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9bb84-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9bb84-108">Prerequisites</span></span>

<span data-ttu-id="9bb84-109">Visual Studio k dokončení tohoto návodu potřebujete.</span><span class="sxs-lookup"><span data-stu-id="9bb84-109">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="9bb84-110">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="9bb84-110">Create the project</span></span>

<span data-ttu-id="9bb84-111">Otevřít Visual Studio a vytvořte nový projekt Formulářové aplikace Windows v jazyce Visual Basic nebo Visual C# s názvem `StylingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="9bb84-111">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `StylingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="9bb84-112">Při hostování obsahu WPF, jsou podporovány pouze projekty C# a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9bb84-112">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="9bb84-113">Vytvořit typy ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="9bb84-113">Create the WPF control types</span></span>

<span data-ttu-id="9bb84-114">Poté, co do projektu přidáte typ ovládacího prvku WPF, které můžete hostovat jej do <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9bb84-114">After you add a WPF control type to the project, you can host it in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

1. <span data-ttu-id="9bb84-115">Přidat nový WPF <xref:System.Windows.Controls.UserControl> projektu do řešení.</span><span class="sxs-lookup"><span data-stu-id="9bb84-115">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="9bb84-116">Použití výchozího názvu pro typ ovládacího prvku `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="9bb84-116">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="9bb84-117">Další informace najdete v tématu [názorný postup: Vytvoření nového obsahu WPF ve Windows Forms v době návrhu](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="9bb84-117">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="9bb84-118">V návrhovém zobrazení, ujistěte se, že `UserControl1` zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="9bb84-118">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="9bb84-119">Další informace najdete v tématu [jak: Vyberte a přesuňte prvků na návrhové ploše](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="9bb84-119">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>

3. <span data-ttu-id="9bb84-120">V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastností `200`.</span><span class="sxs-lookup"><span data-stu-id="9bb84-120">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>

4. <span data-ttu-id="9bb84-121">Přidat <xref:System.Windows.Controls.Button?displayProperty=nameWithType> ovládací prvek <xref:System.Windows.Controls.UserControl> a nastavte hodnotu <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost **zrušit**.</span><span class="sxs-lookup"><span data-stu-id="9bb84-121">Add a <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **Cancel**.</span></span>

5. <span data-ttu-id="9bb84-122">Přidejte druhý <xref:System.Windows.Controls.Button?displayProperty=nameWithType> ovládací prvek <xref:System.Windows.Controls.UserControl> a nastavte hodnotu <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost **OK**.</span><span class="sxs-lookup"><span data-stu-id="9bb84-122">Add a second <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **OK**.</span></span>

6. <span data-ttu-id="9bb84-123">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="9bb84-123">Build the project.</span></span>

## <a name="apply-a-style-to-a-wpf-control"></a><span data-ttu-id="9bb84-124">Použití stylu ovládacího prvku WPF</span><span class="sxs-lookup"><span data-stu-id="9bb84-124">Apply a Style to a WPF Control</span></span>

<span data-ttu-id="9bb84-125">Můžete použít různé pro používání stylů pro ovládací prvek WPF, chcete-li změnit její vzhled a chování.</span><span class="sxs-lookup"><span data-stu-id="9bb84-125">You can apply different styling to a WPF control to change its appearance and behavior.</span></span>

1. <span data-ttu-id="9bb84-126">Otevřít `Form1` v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="9bb84-126">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="9bb84-127">V **nástrojů**, dvakrát klikněte na panel `UserControl1` k vytvoření instance `UserControl1` ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="9bb84-127">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

     <span data-ttu-id="9bb84-128">Instance `UserControl1` hostována v novém <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="9bb84-128">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

1. <span data-ttu-id="9bb84-129">Na panelu inteligentních značek `elementHost1`, klikněte na tlačítko **upravit hostovaný obsah** z rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="9bb84-129">In the smart tag panel for `elementHost1`, click **Edit Hosted Content** from the drop-down list.</span></span>

     <span data-ttu-id="9bb84-130">`UserControl1` Otevře [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9bb84-130">`UserControl1` opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>

1. <span data-ttu-id="9bb84-131">V XAML zobrazení, vložte následující XAML po `<UserControl>` počáteční značku.</span><span class="sxs-lookup"><span data-stu-id="9bb84-131">In XAML view, insert the following XAML after the `<UserControl>` opening tag.</span></span>

     <span data-ttu-id="9bb84-132">Tento XAML vytvoří přechod kontrastní přechodu ohraničení.</span><span class="sxs-lookup"><span data-stu-id="9bb84-132">This XAML creates a gradient with a contrasting gradient border.</span></span> <span data-ttu-id="9bb84-133">Po kliknutí na ovládací prvek přechody jsou změněny na generování vzhled při stisknutí tlačítka.</span><span class="sxs-lookup"><span data-stu-id="9bb84-133">When the control is clicked, the gradients are changed to generate a pressed button look.</span></span> <span data-ttu-id="9bb84-134">Další informace najdete v tématu [styly a šablony](../../wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="9bb84-134">For more information, see [Styling and Templating](../../wpf/controls/styling-and-templating.md).</span></span>

   ```xaml
   <UserControl.Resources>
    <LinearGradientBrush x:Key="NormalBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#FFF" Offset="0.0"/>
        <GradientStop Color="#CCC" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="PressedBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#BBB" Offset="0.0"/>
        <GradientStop Color="#EEE" Offset="0.1"/>
        <GradientStop Color="#EEE" Offset="0.9"/>
        <GradientStop Color="#FFF" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="NormalBorderBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#CCC" Offset="0.0"/>
        <GradientStop Color="#444" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="BorderBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#CCC" Offset="0.0"/>
        <GradientStop Color="#444" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="PressedBorderBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#444" Offset="0.0"/>
        <GradientStop Color="#888" Offset="1.0"/>
    </LinearGradientBrush>

    <Style x:Key="SimpleButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="Background" Value="{StaticResource NormalBrush}"/>
        <Setter Property="BorderBrush" Value="{StaticResource NormalBorderBrush}"/>
        <Setter Property="Template">
            <Setter.Value>
                <ControlTemplate TargetType="{x:Type Button}">
                    <Grid x:Name="Grid">
                        <Border x:Name="Border" Background="{TemplateBinding Background}" BorderBrush="{TemplateBinding BorderBrush}" BorderThickness="{TemplateBinding BorderThickness}" Padding="{TemplateBinding Padding}"/>
                        <ContentPresenter HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Margin="{TemplateBinding Padding}" VerticalAlignment="{TemplateBinding VerticalContentAlignment}" RecognizesAccessKey="True"/>
                    </Grid>
                    <ControlTemplate.Triggers>
                        <Trigger Property="IsPressed" Value="true">
                            <Setter Property="Background" Value="{StaticResource PressedBrush}" TargetName="Border"/>
                            <Setter Property="BorderBrush" Value="{StaticResource PressedBorderBrush}" TargetName="Border"/>
                        </Trigger>
                    </ControlTemplate.Triggers>
                </ControlTemplate>
            </Setter.Value>
        </Setter>
    </Style>
   </UserControl.Resources>
   ```

1. <span data-ttu-id="9bb84-135">Použít `SimpleButton` styl definovaný v předchozím kroku, a na tlačítko Storno vložením následujícího XAML v `<Button>` značky na tlačítko Storno.</span><span class="sxs-lookup"><span data-stu-id="9bb84-135">Apply the `SimpleButton` style defined in the previous step to the Cancel button by inserting the following XAML in the `<Button>` tag of the Cancel button.</span></span>

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   <span data-ttu-id="9bb84-136">Vaše prohlášení tlačítko bude vypadat podobně jako následující XAML:</span><span class="sxs-lookup"><span data-stu-id="9bb84-136">Your button declaration will resemble the following XAML:</span></span>

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

1. <span data-ttu-id="9bb84-137">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="9bb84-137">Build the project.</span></span>

1. <span data-ttu-id="9bb84-138">Otevřít `Form1` v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="9bb84-138">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="9bb84-139">Nový styl platí pro ovládací prvek tlačítko.</span><span class="sxs-lookup"><span data-stu-id="9bb84-139">The new style is applied to the button control.</span></span>

1. <span data-ttu-id="9bb84-140">Z **ladění** nabídce vyberte možnost **spustit ladění** ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="9bb84-140">From the **Debug** menu, select **Start Debugging** to run the application.</span></span>

1. <span data-ttu-id="9bb84-141">Klikněte na tlačítko OK a zrušit a zobrazit rozdíly.</span><span class="sxs-lookup"><span data-stu-id="9bb84-141">Click the OK and Cancel buttons and view the differences.</span></span>

## <a name="see-also"></a><span data-ttu-id="9bb84-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9bb84-142">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="9bb84-143">Migrace a interoperabilita</span><span class="sxs-lookup"><span data-stu-id="9bb84-143">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="9bb84-144">Používání ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="9bb84-144">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="9bb84-145">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9bb84-145">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="9bb84-146">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="9bb84-146">XAML Overview (WPF)</span></span>](../../wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="9bb84-147">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="9bb84-147">Styling and Templating</span></span>](../../wpf/controls/styling-and-templating.md)
