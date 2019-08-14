---
title: 'Návod: Určení stylu obsahu WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
ms.openlocfilehash: 32ca9658ddf4ab6e8690f29797b7ac7b09df2ca7
ms.sourcegitcommit: d98fdb087d9c8aba7d2cb93fe4b4ee35a2308cee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2019
ms.locfileid: "69012948"
---
# <a name="walkthrough-style-wpf-content"></a><span data-ttu-id="55098-102">Návod: Styl obsahu WPF</span><span class="sxs-lookup"><span data-stu-id="55098-102">Walkthrough: Style WPF content</span></span>

<span data-ttu-id="55098-103">V tomto návodu se dozvíte, jak použít styly pro ovládací prvek Windows Presentation Foundation (WPF) hostovaný ve formuláři Windows.</span><span class="sxs-lookup"><span data-stu-id="55098-103">This walkthrough show you how to apply styling to a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>

 <span data-ttu-id="55098-104">V tomto návodu provedete následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="55098-104">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="55098-105">Vytvořte projekt.</span><span class="sxs-lookup"><span data-stu-id="55098-105">Create the project.</span></span>

- <span data-ttu-id="55098-106">Vytvořte typ ovládacího prvku WPF.</span><span class="sxs-lookup"><span data-stu-id="55098-106">Create the WPF control type.</span></span>

- <span data-ttu-id="55098-107">Použijte styl pro ovládací prvek WPF.</span><span class="sxs-lookup"><span data-stu-id="55098-107">Apply a style to the WPF control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="55098-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="55098-108">Prerequisites</span></span>

<span data-ttu-id="55098-109">K dokončení tohoto Názorného postupu potřebujete Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="55098-109">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="55098-110">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="55098-110">Create the project</span></span>

<span data-ttu-id="55098-111">Otevřete Visual Studio a vytvořte nový projekt aplikace model Windows Forms v Visual Basic nebo vizuálu C# s názvem `StylingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="55098-111">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `StylingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="55098-112">Při hostování obsahu WPF jsou podporovány C# pouze projekty a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="55098-112">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="55098-113">Vytvoření typů ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="55098-113">Create the WPF control types</span></span>

<span data-ttu-id="55098-114">Po přidání typu ovládacího prvku WPF do projektu jej můžete hostovat v <xref:System.Windows.Forms.Integration.ElementHost> ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="55098-114">After you add a WPF control type to the project, you can host it in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

1. <span data-ttu-id="55098-115">Přidejte do řešení nový <xref:System.Windows.Controls.UserControl> projekt WPF.</span><span class="sxs-lookup"><span data-stu-id="55098-115">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="55098-116">Použijte výchozí název pro typ ovládacího prvku, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="55098-116">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="55098-117">Další informace najdete v tématu [Návod: Vytváření nového obsahu WPF v model Windows Forms v době](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)návrhu.</span><span class="sxs-lookup"><span data-stu-id="55098-117">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="55098-118">V zobrazení Návrh se ujistěte, že `UserControl1` je vybraná možnost.</span><span class="sxs-lookup"><span data-stu-id="55098-118">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="55098-119">Další informace najdete v tématu [jak: Vyberte a přesuňte prvky na Návrhová plocha](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="55098-119">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>

3. <span data-ttu-id="55098-120">V okně **vlastnosti** nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> vlastností a <xref:System.Windows.FrameworkElement.Height%2A> na `200`.</span><span class="sxs-lookup"><span data-stu-id="55098-120">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>

4. <span data-ttu-id="55098-121">Přidejte ovládací prvek <xref:System.Windows.Controls.UserControl> do a <xref:System.Windows.Controls.ContentControl.Content%2A> nastavte hodnotu vlastnosti na **zrušit.** <xref:System.Windows.Controls.Button?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="55098-121">Add a <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **Cancel**.</span></span>

5. <span data-ttu-id="55098-122">Přidejte druhý <xref:System.Windows.Controls.Button?displayProperty=nameWithType> ovládací prvek <xref:System.Windows.Controls.UserControl> do a <xref:System.Windows.Controls.ContentControl.Content%2A> nastavte hodnotu vlastnosti na **OK**.</span><span class="sxs-lookup"><span data-stu-id="55098-122">Add a second <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **OK**.</span></span>

6. <span data-ttu-id="55098-123">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="55098-123">Build the project.</span></span>

## <a name="apply-a-style-to-a-wpf-control"></a><span data-ttu-id="55098-124">Použití stylu pro ovládací prvek WPF</span><span class="sxs-lookup"><span data-stu-id="55098-124">Apply a Style to a WPF Control</span></span>

<span data-ttu-id="55098-125">Můžete použít různé styly pro ovládací prvek WPF a změnit jeho vzhled a chování.</span><span class="sxs-lookup"><span data-stu-id="55098-125">You can apply different styling to a WPF control to change its appearance and behavior.</span></span>

1. <span data-ttu-id="55098-126">Otevřete `Form1` v Návrhář formulářů.</span><span class="sxs-lookup"><span data-stu-id="55098-126">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="55098-127">Na **panelu nástrojů**poklikejte na `UserControl1` `UserControl1` vytvoření instance ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="55098-127">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

     <span data-ttu-id="55098-128">Instance `UserControl1` je hostována v novém <xref:System.Windows.Forms.Integration.ElementHost> ovládacím prvku s názvem `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="55098-128">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

1. <span data-ttu-id="55098-129">Na panelu inteligentních značek pro `elementHost1`klikněte v rozevíracím seznamu na **Upravit hostovaný obsah** .</span><span class="sxs-lookup"><span data-stu-id="55098-129">In the smart tag panel for `elementHost1`, click **Edit Hosted Content** from the drop-down list.</span></span>

     <span data-ttu-id="55098-130">`UserControl1`Otevře se [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]v.</span><span class="sxs-lookup"><span data-stu-id="55098-130">`UserControl1` opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>

1. <span data-ttu-id="55098-131">V zobrazení XAML vložte následující kód XAML za `<UserControl>` úvodní značku.</span><span class="sxs-lookup"><span data-stu-id="55098-131">In XAML view, insert the following XAML after the `<UserControl>` opening tag.</span></span>

     <span data-ttu-id="55098-132">Tento kód XAML vytvoří přechod s kontrastem ohraničení přechodu.</span><span class="sxs-lookup"><span data-stu-id="55098-132">This XAML creates a gradient with a contrasting gradient border.</span></span> <span data-ttu-id="55098-133">Při kliknutí na ovládací prvek se přechody změní tak, aby se vygenerovalo tlačítko při stisknutí tlačítka.</span><span class="sxs-lookup"><span data-stu-id="55098-133">When the control is clicked, the gradients are changed to generate a pressed button look.</span></span> <span data-ttu-id="55098-134">Další informace najdete v tématu [stylování a šablonování](../../wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="55098-134">For more information, see [Styling and Templating](../../wpf/controls/styling-and-templating.md).</span></span>

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

1. <span data-ttu-id="55098-135">Použijte styl definovaný v předchozím kroku na tlačítko Storno vložením následujícího kódu XAML `<Button>` do značky tlačítka Storno. `SimpleButton`</span><span class="sxs-lookup"><span data-stu-id="55098-135">Apply the `SimpleButton` style defined in the previous step to the Cancel button by inserting the following XAML in the `<Button>` tag of the Cancel button.</span></span>

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   <span data-ttu-id="55098-136">Vaše deklarace tlačítka bude vypadat podobně jako v následujícím kódu XAML:</span><span class="sxs-lookup"><span data-stu-id="55098-136">Your button declaration will resemble the following XAML:</span></span>

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

1. <span data-ttu-id="55098-137">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="55098-137">Build the project.</span></span>

1. <span data-ttu-id="55098-138">Otevřete `Form1` v Návrhář formulářů.</span><span class="sxs-lookup"><span data-stu-id="55098-138">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="55098-139">Nový styl se aplikuje na ovládací prvek tlačítko.</span><span class="sxs-lookup"><span data-stu-id="55098-139">The new style is applied to the button control.</span></span>

1. <span data-ttu-id="55098-140">V nabídce **ladění** vyberte **Spustit ladění** , aby se aplikace spustila.</span><span class="sxs-lookup"><span data-stu-id="55098-140">From the **Debug** menu, select **Start Debugging** to run the application.</span></span>

1. <span data-ttu-id="55098-141">Klikněte na tlačítko OK a tlačítka Storno a zobrazte rozdíly.</span><span class="sxs-lookup"><span data-stu-id="55098-141">Click the OK and Cancel buttons and view the differences.</span></span>

## <a name="see-also"></a><span data-ttu-id="55098-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55098-142">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="55098-143">Migrace a interoperabilita</span><span class="sxs-lookup"><span data-stu-id="55098-143">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="55098-144">Používání ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="55098-144">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="55098-145">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="55098-145">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="55098-146">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="55098-146">XAML Overview (WPF)</span></span>](../../wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="55098-147">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="55098-147">Styling and Templating</span></span>](../../wpf/controls/styling-and-templating.md)
