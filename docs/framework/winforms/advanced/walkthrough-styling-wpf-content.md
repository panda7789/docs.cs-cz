---
title: 'Návod: Určení stylu obsahu WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 581fcbfdfd7806b8f0f70347ac96f1bf09fa9098
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460948"
---
# <a name="walkthrough-style-wpf-content"></a><span data-ttu-id="386d8-102">Návod: styl obsahu WPF</span><span class="sxs-lookup"><span data-stu-id="386d8-102">Walkthrough: Style WPF content</span></span>

<span data-ttu-id="386d8-103">V tomto článku se dozvíte, jak použít styly pro řízení Windows Presentation Foundation (WPF) hostovaného ve formuláři Windows.</span><span class="sxs-lookup"><span data-stu-id="386d8-103">This article show you how to apply styling to a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="386d8-104">Požadavky</span><span class="sxs-lookup"><span data-stu-id="386d8-104">Prerequisites</span></span>

<span data-ttu-id="386d8-105">K dokončení tohoto Názorného postupu potřebujete Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="386d8-105">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="386d8-106">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="386d8-106">Create the project</span></span>

<span data-ttu-id="386d8-107">Otevřete Visual Studio a vytvořte nový projekt aplikace model Windows Forms v Visual Basic nebo vizuálu C# s názvem `StylingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="386d8-107">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `StylingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="386d8-108">Při hostování obsahu WPF jsou podporovány C# pouze projekty a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="386d8-108">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="386d8-109">Vytvoření typů ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="386d8-109">Create the WPF control types</span></span>

<span data-ttu-id="386d8-110">Po přidání typu ovládacího prvku WPF do projektu jej můžete hostovat v ovládacím prvku <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="386d8-110">After you add a WPF control type to the project, you can host it in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

1. <span data-ttu-id="386d8-111">Přidejte do řešení nový projekt WPF <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="386d8-111">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="386d8-112">Použijte výchozí název pro typ ovládacího prvku `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="386d8-112">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="386d8-113">Další informace najdete v tématu [Návod: vytvoření nového obsahu WPF na model Windows Forms v době návrhu](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="386d8-113">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="386d8-114">V zobrazení Návrh se ujistěte, že je vybrána možnost `UserControl1`.</span><span class="sxs-lookup"><span data-stu-id="386d8-114">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="386d8-115">V okně **vlastnosti** nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a vlastnosti <xref:System.Windows.FrameworkElement.Height%2A> na **200**.</span><span class="sxs-lookup"><span data-stu-id="386d8-115">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="386d8-116">Do <xref:System.Windows.Controls.UserControl> přidejte ovládací prvek <xref:System.Windows.Controls.Button?displayProperty=nameWithType> a nastavte hodnotu vlastnosti <xref:System.Windows.Controls.ContentControl.Content%2A> na **Zrušit**.</span><span class="sxs-lookup"><span data-stu-id="386d8-116">Add a <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **Cancel**.</span></span>

5. <span data-ttu-id="386d8-117">Přidejte do <xref:System.Windows.Controls.UserControl> druhý ovládací prvek <xref:System.Windows.Controls.Button?displayProperty=nameWithType> a nastavte hodnotu vlastnosti <xref:System.Windows.Controls.ContentControl.Content%2A> na **OK**.</span><span class="sxs-lookup"><span data-stu-id="386d8-117">Add a second <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **OK**.</span></span>

6. <span data-ttu-id="386d8-118">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="386d8-118">Build the project.</span></span>

## <a name="apply-a-style-to-a-wpf-control"></a><span data-ttu-id="386d8-119">Použití stylu pro ovládací prvek WPF</span><span class="sxs-lookup"><span data-stu-id="386d8-119">Apply a Style to a WPF Control</span></span>

<span data-ttu-id="386d8-120">Můžete použít různé styly pro ovládací prvek WPF a změnit jeho vzhled a chování.</span><span class="sxs-lookup"><span data-stu-id="386d8-120">You can apply different styling to a WPF control to change its appearance and behavior.</span></span>

1. <span data-ttu-id="386d8-121">Otevřete `Form1` v Návrhář formulářů.</span><span class="sxs-lookup"><span data-stu-id="386d8-121">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="386d8-122">Na **panelu nástrojů**dvakrát klikněte na `UserControl1`. tím se vytvoří instance `UserControl1` ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="386d8-122">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

   <span data-ttu-id="386d8-123">Instance `UserControl1` je hostována v novém ovládacím prvku <xref:System.Windows.Forms.Integration.ElementHost> s názvem `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="386d8-123">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

1. <span data-ttu-id="386d8-124">Na panelu inteligentních značek pro `elementHost1`v rozevíracím seznamu klikněte na **Upravit hostovaný obsah** .</span><span class="sxs-lookup"><span data-stu-id="386d8-124">In the smart tag panel for `elementHost1`, click **Edit Hosted Content** from the drop-down list.</span></span>

   <span data-ttu-id="386d8-125">`UserControl1` se otevře v Návrháři WPF.</span><span class="sxs-lookup"><span data-stu-id="386d8-125">`UserControl1` opens in the WPF Designer.</span></span>

1. <span data-ttu-id="386d8-126">V zobrazení XAML vložte následující kód XAML po `<UserControl>` počáteční značku.</span><span class="sxs-lookup"><span data-stu-id="386d8-126">In XAML view, insert the following XAML after the `<UserControl>` opening tag.</span></span> <span data-ttu-id="386d8-127">Tento kód XAML vytvoří přechod s kontrastem ohraničení přechodu.</span><span class="sxs-lookup"><span data-stu-id="386d8-127">This XAML creates a gradient with a contrasting gradient border.</span></span> <span data-ttu-id="386d8-128">Při kliknutí na ovládací prvek se přechody změní tak, aby se vygenerovalo tlačítko při stisknutí tlačítka.</span><span class="sxs-lookup"><span data-stu-id="386d8-128">When the control is clicked, the gradients are changed to generate a pressed button look.</span></span> <span data-ttu-id="386d8-129">Další informace najdete v tématu [stylování a šablonování](../../wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="386d8-129">For more information, see [Styling and Templating](../../wpf/controls/styling-and-templating.md).</span></span>

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

1. <span data-ttu-id="386d8-130">Použijte styl `SimpleButton` definovaný v předchozím kroku na tlačítko Storno vložením následujícího kódu XAML do značky `<Button>` tlačítka **Zrušit** .</span><span class="sxs-lookup"><span data-stu-id="386d8-130">Apply the `SimpleButton` style defined in the previous step to the Cancel button by inserting the following XAML in the `<Button>` tag of the **Cancel** button.</span></span>

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   <span data-ttu-id="386d8-131">Vaše deklarace tlačítka bude vypadat podobně jako v následujícím kódu XAML:</span><span class="sxs-lookup"><span data-stu-id="386d8-131">Your button declaration will resemble the following XAML:</span></span>

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

1. <span data-ttu-id="386d8-132">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="386d8-132">Build the project.</span></span>

1. <span data-ttu-id="386d8-133">Otevřete `Form1` v Návrhář formulářů.</span><span class="sxs-lookup"><span data-stu-id="386d8-133">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="386d8-134">Nový styl se aplikuje na ovládací prvek tlačítko.</span><span class="sxs-lookup"><span data-stu-id="386d8-134">The new style is applied to the button control.</span></span>

1. <span data-ttu-id="386d8-135">V nabídce **ladění** vyberte **Spustit ladění** , aby se aplikace spustila.</span><span class="sxs-lookup"><span data-stu-id="386d8-135">From the **Debug** menu, select **Start Debugging** to run the application.</span></span>

1. <span data-ttu-id="386d8-136">Klikněte na tlačítko **OK** a tlačítka **Storno** a zobrazte rozdíly.</span><span class="sxs-lookup"><span data-stu-id="386d8-136">Click the **OK** and **Cancel** buttons and view the differences.</span></span>

## <a name="see-also"></a><span data-ttu-id="386d8-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="386d8-137">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="386d8-138">Migrace a interoperabilita</span><span class="sxs-lookup"><span data-stu-id="386d8-138">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="386d8-139">Používání ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="386d8-139">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="386d8-140">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="386d8-140">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="386d8-141">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="386d8-141">XAML Overview (WPF)</span></span>](../../wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="386d8-142">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="386d8-142">Styling and Templating</span></span>](../../wpf/controls/styling-and-templating.md)
