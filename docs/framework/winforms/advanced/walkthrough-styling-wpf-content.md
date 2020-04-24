---
title: 'Návod: Styl WPF obsahu'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 07241d41e3fbf270a76bd241765bfa369ee265d5
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646334"
---
# <a name="walkthrough-style-wpf-content"></a><span data-ttu-id="0dcaf-102">Návod: Styl WPF obsahu</span><span class="sxs-lookup"><span data-stu-id="0dcaf-102">Walkthrough: Style WPF content</span></span>

<span data-ttu-id="0dcaf-103">Tento článek ukazuje, jak použít styl pro ovládací prvek WPF (Windows Presentation Foundation) hostovaný ve formuláři systému Windows.</span><span class="sxs-lookup"><span data-stu-id="0dcaf-103">This article show you how to apply styling to a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0dcaf-104">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0dcaf-104">Prerequisites</span></span>

<span data-ttu-id="0dcaf-105">K dokončení tohoto návodu potřebujete Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0dcaf-105">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="0dcaf-106">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="0dcaf-106">Create the project</span></span>

<span data-ttu-id="0dcaf-107">Otevřete Visual Studio a vytvořte nový projekt aplikace Windows `StylingWpfContent`Forms v jazyce Visual Basic nebo Visual C# s názvem .</span><span class="sxs-lookup"><span data-stu-id="0dcaf-107">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `StylingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="0dcaf-108">Při hostování obsahu WPF jsou podporovány pouze projekty jazyka C# a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0dcaf-108">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="0dcaf-109">Vytvoření typů ovládacích prvku WPF</span><span class="sxs-lookup"><span data-stu-id="0dcaf-109">Create the WPF control types</span></span>

<span data-ttu-id="0dcaf-110">Po přidání typu ovládacího prvku WPF do projektu <xref:System.Windows.Forms.Integration.ElementHost> jej můžete hostovat v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="0dcaf-110">After you add a WPF control type to the project, you can host it in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

1. <span data-ttu-id="0dcaf-111">Přidejte do <xref:System.Windows.Controls.UserControl> řešení nový projekt WPF.</span><span class="sxs-lookup"><span data-stu-id="0dcaf-111">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="0dcaf-112">Použijte výchozí název pro typ `UserControl1.xaml`ovládacího prvku .</span><span class="sxs-lookup"><span data-stu-id="0dcaf-112">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="0dcaf-113">Další informace naleznete [v tématu Návod: Vytvoření nového obsahu WPF ve formulářích Windows v době návrhu](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="0dcaf-113">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="0dcaf-114">V návrhovém zobrazení `UserControl1` zkontrolujte, zda je tato možnost vybraná.</span><span class="sxs-lookup"><span data-stu-id="0dcaf-114">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="0dcaf-115">V okně **Vlastnosti** nastavte hodnotu <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti a na <xref:System.Windows.FrameworkElement.Width%2A> **hodnotu 200**.</span><span class="sxs-lookup"><span data-stu-id="0dcaf-115">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="0dcaf-116">Přidejte <xref:System.Windows.Controls.Button?displayProperty=nameWithType> ovládací <xref:System.Windows.Controls.UserControl> prvek a nastavte <xref:System.Windows.Controls.ContentControl.Content%2A> hodnotu vlastnosti **na Cancel**.</span><span class="sxs-lookup"><span data-stu-id="0dcaf-116">Add a <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **Cancel**.</span></span>

5. <span data-ttu-id="0dcaf-117">Přidejte <xref:System.Windows.Controls.Button?displayProperty=nameWithType> druhý ovládací <xref:System.Windows.Controls.UserControl> prvek a nastavte <xref:System.Windows.Controls.ContentControl.Content%2A> hodnotu vlastnosti na **OK**.</span><span class="sxs-lookup"><span data-stu-id="0dcaf-117">Add a second <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **OK**.</span></span>

6. <span data-ttu-id="0dcaf-118">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="0dcaf-118">Build the project.</span></span>

## <a name="apply-a-style-to-a-wpf-control"></a><span data-ttu-id="0dcaf-119">Použití stylu u ovládacího prvku WPF</span><span class="sxs-lookup"><span data-stu-id="0dcaf-119">Apply a Style to a WPF Control</span></span>

<span data-ttu-id="0dcaf-120">Můžete použít jiný styl ovládacího prvku WPF změnit jeho vzhled a chování.</span><span class="sxs-lookup"><span data-stu-id="0dcaf-120">You can apply different styling to a WPF control to change its appearance and behavior.</span></span>

1. <span data-ttu-id="0dcaf-121">Otevřete `Form1` v Návrháři formulářů systému Windows.</span><span class="sxs-lookup"><span data-stu-id="0dcaf-121">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="0dcaf-122">V **panelu nástrojů**poklepejte `UserControl1` `UserControl1` na vytvoření instance ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="0dcaf-122">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

   <span data-ttu-id="0dcaf-123">Instance `UserControl1` je hostována v <xref:System.Windows.Forms.Integration.ElementHost> novém `elementHost1`ovládacím prvku s názvem .</span><span class="sxs-lookup"><span data-stu-id="0dcaf-123">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

1. <span data-ttu-id="0dcaf-124">V panelu inteligentních značek klikněte v `elementHost1`rozevíracím seznamu na Upravit **hostovaný obsah.**</span><span class="sxs-lookup"><span data-stu-id="0dcaf-124">In the smart tag panel for `elementHost1`, click **Edit Hosted Content** from the drop-down list.</span></span>

   <span data-ttu-id="0dcaf-125">`UserControl1`otevře v Návrháři WPF.</span><span class="sxs-lookup"><span data-stu-id="0dcaf-125">`UserControl1` opens in the WPF Designer.</span></span>

1. <span data-ttu-id="0dcaf-126">V zobrazení XAML vložte za `<UserControl>` otevírací značku následující XAML.</span><span class="sxs-lookup"><span data-stu-id="0dcaf-126">In XAML view, insert the following XAML after the `<UserControl>` opening tag.</span></span> <span data-ttu-id="0dcaf-127">Tento XAML vytvoří přechod s kontrastním ohraničením přechodu.</span><span class="sxs-lookup"><span data-stu-id="0dcaf-127">This XAML creates a gradient with a contrasting gradient border.</span></span> <span data-ttu-id="0dcaf-128">Po klepnutí na ovládací prvek se přechody změní tak, aby generovaly vzhled stisknutého tlačítka.</span><span class="sxs-lookup"><span data-stu-id="0dcaf-128">When the control is clicked, the gradients are changed to generate a pressed button look.</span></span> <span data-ttu-id="0dcaf-129">Další informace naleznete [v tématu Styling a Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0dcaf-129">For more information, see [Styling and Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

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

1. <span data-ttu-id="0dcaf-130">Použijte `SimpleButton` styl definovaný v předchozím kroku na tlačítko Storno vložením `<Button>` následujícího xaml do značky tlačítka **Storno.**</span><span class="sxs-lookup"><span data-stu-id="0dcaf-130">Apply the `SimpleButton` style defined in the previous step to the Cancel button by inserting the following XAML in the `<Button>` tag of the **Cancel** button.</span></span>

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   <span data-ttu-id="0dcaf-131">Deklarace tlačítka se bude podobat následujícímu xaml:</span><span class="sxs-lookup"><span data-stu-id="0dcaf-131">Your button declaration will resemble the following XAML:</span></span>

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

1. <span data-ttu-id="0dcaf-132">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="0dcaf-132">Build the project.</span></span>

1. <span data-ttu-id="0dcaf-133">Otevřete `Form1` v Návrháři formulářů systému Windows.</span><span class="sxs-lookup"><span data-stu-id="0dcaf-133">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="0dcaf-134">Nový styl se aplikuje na ovládací prvek tlačítka.</span><span class="sxs-lookup"><span data-stu-id="0dcaf-134">The new style is applied to the button control.</span></span>

1. <span data-ttu-id="0dcaf-135">V nabídce **Ladění** vyberte **Spustit ladění,** chcete-li aplikaci spustit.</span><span class="sxs-lookup"><span data-stu-id="0dcaf-135">From the **Debug** menu, select **Start Debugging** to run the application.</span></span>

1. <span data-ttu-id="0dcaf-136">Klikněte na tlačítka **OK** a **Storno** a zobrazte rozdíly.</span><span class="sxs-lookup"><span data-stu-id="0dcaf-136">Click the **OK** and **Cancel** buttons and view the differences.</span></span>

## <a name="see-also"></a><span data-ttu-id="0dcaf-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="0dcaf-137">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="0dcaf-138">Migrace a interoperabilita</span><span class="sxs-lookup"><span data-stu-id="0dcaf-138">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="0dcaf-139">Používání ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="0dcaf-139">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="0dcaf-140">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0dcaf-140">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="0dcaf-141">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="0dcaf-141">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="0dcaf-142">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="0dcaf-142">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
