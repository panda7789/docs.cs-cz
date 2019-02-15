---
title: 'Průvodce: Určení stylu obsahu WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
ms.openlocfilehash: ef81d9272acdddfc7d547de6f44725481e55dc3e
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2019
ms.locfileid: "56303722"
---
# <a name="walkthrough-styling-wpf-content"></a><span data-ttu-id="c9974-102">Průvodce: Určení stylu obsahu WPF</span><span class="sxs-lookup"><span data-stu-id="c9974-102">Walkthrough: Styling WPF Content</span></span>
<span data-ttu-id="c9974-103">Tento názorný postup ukazují, jak použít používání stylů pro ovládací prvek Windows Presentation Foundation (WPF) hostovaného ve formuláři Windows.</span><span class="sxs-lookup"><span data-stu-id="c9974-103">This walkthrough show you how to apply styling to a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>

 <span data-ttu-id="c9974-104">V tomto podrobném návodu můžete provádět následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="c9974-104">In this walkthrough, you perform the following tasks:</span></span>

-   <span data-ttu-id="c9974-105">Vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="c9974-105">Create the project.</span></span>

-   <span data-ttu-id="c9974-106">Vytvořte typ ovládacího prvku WPF.</span><span class="sxs-lookup"><span data-stu-id="c9974-106">Create the WPF control type.</span></span>

-   <span data-ttu-id="c9974-107">Použití stylu pro ovládací prvek WPF.</span><span class="sxs-lookup"><span data-stu-id="c9974-107">Apply a style to the WPF control.</span></span>

> [!NOTE]
>  <span data-ttu-id="c9974-108">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="c9974-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c9974-109">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="c9974-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="c9974-110">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="c9974-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c9974-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c9974-111">Prerequisites</span></span>  
 <span data-ttu-id="c9974-112">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="c9974-112">You need the following components to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="c9974-113">Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="c9974-113">Visual Studio 2012.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="c9974-114">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="c9974-114">Creating the Project</span></span>  
 <span data-ttu-id="c9974-115">Prvním krokem je vytvoření projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c9974-115">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c9974-116">Při hostování obsahu WPF, jsou podporovány pouze projekty C# a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c9974-116">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="c9974-117">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="c9974-117">To create the project</span></span>  
  
-   <span data-ttu-id="c9974-118">Vytvořte nový projekt Formulářové aplikace Windows v jazyce Visual Basic nebo Visual C# s názvem `StylingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="c9974-118">Create a new Windows Forms Application project in Visual Basic or Visual C# named `StylingWpfContent`.</span></span>  
  
## <a name="creating-the-wpf-control-types"></a><span data-ttu-id="c9974-119">Vytváření typů ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="c9974-119">Creating the WPF Control Types</span></span>  
 <span data-ttu-id="c9974-120">Poté, co do projektu přidáte typ ovládacího prvku WPF, které můžete hostovat jej do <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c9974-120">After you add a WPF control type to the project, you can host it in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>  
  
#### <a name="to-create-wpf-control-types"></a><span data-ttu-id="c9974-121">Chcete-li vytvořit typy ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="c9974-121">To create WPF control types</span></span>  
  
1.  <span data-ttu-id="c9974-122">Přidat nový WPF <xref:System.Windows.Controls.UserControl> projektu do řešení.</span><span class="sxs-lookup"><span data-stu-id="c9974-122">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="c9974-123">Použití výchozího názvu pro typ ovládacího prvku `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="c9974-123">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="c9974-124">Další informace najdete v tématu [názorný postup: Vytvoření nového obsahu WPF ve Windows Forms v době návrhu](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="c9974-124">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="c9974-125">V návrhovém zobrazení, ujistěte se, že `UserControl1` zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="c9974-125">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="c9974-126">Další informace najdete v tématu [jak: Vyberte a přesuňte prvků na návrhové ploše](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c9974-126">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>  
  
3.  <span data-ttu-id="c9974-127">V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastností `200`.</span><span class="sxs-lookup"><span data-stu-id="c9974-127">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="c9974-128">Přidat <xref:System.Windows.Controls.Button?displayProperty=nameWithType> ovládací prvek <xref:System.Windows.Controls.UserControl> a nastavte hodnotu <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost **zrušit**.</span><span class="sxs-lookup"><span data-stu-id="c9974-128">Add a <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **Cancel**.</span></span>  
  
5.  <span data-ttu-id="c9974-129">Přidejte druhý <xref:System.Windows.Controls.Button?displayProperty=nameWithType> ovládací prvek <xref:System.Windows.Controls.UserControl> a nastavte hodnotu <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost **OK**.</span><span class="sxs-lookup"><span data-stu-id="c9974-129">Add a second <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **OK**.</span></span>  
  
6.  <span data-ttu-id="c9974-130">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="c9974-130">Build the project.</span></span>  
  
## <a name="applying-a-style-to-a-wpf-control"></a><span data-ttu-id="c9974-131">Použití stylu ovládacího prvku WPF</span><span class="sxs-lookup"><span data-stu-id="c9974-131">Applying a Style to a WPF Control</span></span>  
 <span data-ttu-id="c9974-132">Můžete použít různé pro používání stylů pro ovládací prvek WPF, chcete-li změnit její vzhled a chování.</span><span class="sxs-lookup"><span data-stu-id="c9974-132">You can apply different styling to a WPF control to change its appearance and behavior.</span></span>  
  
#### <a name="to-apply-a-style-to-a-wpf-control"></a><span data-ttu-id="c9974-133">Pokud chcete použít styl ovládacího prvku WPF</span><span class="sxs-lookup"><span data-stu-id="c9974-133">To apply a style to a WPF control</span></span>  
  
1.  <span data-ttu-id="c9974-134">Otevřít `Form1` v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="c9974-134">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="c9974-135">V **nástrojů**, dvakrát klikněte na panel `UserControl1` k vytvoření instance `UserControl1` ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="c9974-135">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>  
  
     <span data-ttu-id="c9974-136">Instance `UserControl1` hostována v novém <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="c9974-136">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
3.  <span data-ttu-id="c9974-137">Na panelu inteligentních značek `elementHost1`, klikněte na tlačítko **upravit hostovaný obsah** z rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="c9974-137">In the smart tag panel for `elementHost1`, click **Edit Hosted Content** from the drop-down list.</span></span>  
  
     <span data-ttu-id="c9974-138">`UserControl1` Otevře [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c9974-138">`UserControl1` opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="c9974-139">V XAML zobrazení, vložte následující XAML po `<UserControl>` počáteční značku.</span><span class="sxs-lookup"><span data-stu-id="c9974-139">In XAML view, insert the following XAML after the `<UserControl>` opening tag.</span></span>  
  
     <span data-ttu-id="c9974-140">Tento XAML vytvoří přechod kontrastní přechodu ohraničení.</span><span class="sxs-lookup"><span data-stu-id="c9974-140">This XAML creates a gradient with a contrasting gradient border.</span></span> <span data-ttu-id="c9974-141">Po kliknutí na ovládací prvek přechody jsou změněny na generování vzhled při stisknutí tlačítka.</span><span class="sxs-lookup"><span data-stu-id="c9974-141">When the control is clicked, the gradients are changed to generate a pressed button look.</span></span> <span data-ttu-id="c9974-142">Další informace najdete v tématu [styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="c9974-142">For more information, see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>  
  
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
  
1.  <span data-ttu-id="c9974-143">Použít `SimpleButton` styl definovaný v předchozím kroku, a na tlačítko Storno vložením následujícího XAML v `<Button>` značky na tlačítko Storno.</span><span class="sxs-lookup"><span data-stu-id="c9974-143">Apply the `SimpleButton` style defined in the previous step to the Cancel button by inserting the following XAML in the `<Button>` tag of the Cancel button.</span></span>  
  
    ```  
    Style="{StaticResource SimpleButton}  
    ```  
  
     <span data-ttu-id="c9974-144">Vaše prohlášení tlačítko bude vypadat podobně jako následující XAML.</span><span class="sxs-lookup"><span data-stu-id="c9974-144">Your button declaration will resemble the following XAML.</span></span>  
  
```xaml  
<Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"  
                Style="{StaticResource SimpleButton}">Cancel</Button>  
```  
  
1.  <span data-ttu-id="c9974-145">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="c9974-145">Build the project.</span></span>  
  
2.  <span data-ttu-id="c9974-146">Otevřít `Form1` v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="c9974-146">Open `Form1` in the Windows Forms Designer.</span></span>  
  
3.  <span data-ttu-id="c9974-147">Nový styl platí pro ovládací prvek tlačítko.</span><span class="sxs-lookup"><span data-stu-id="c9974-147">The new style is applied to the button control.</span></span>  
  
4.  <span data-ttu-id="c9974-148">Z **ladění** nabídce vyberte možnost **spustit ladění** ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="c9974-148">From the **Debug** menu, select **Start Debugging** to run the application.</span></span>  
  
5.  <span data-ttu-id="c9974-149">Klikněte na tlačítko OK a zrušit a zobrazit rozdíly.</span><span class="sxs-lookup"><span data-stu-id="c9974-149">Click the OK and Cancel buttons and view the differences.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9974-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c9974-150">See also</span></span>
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="c9974-151">Migrace a interoperabilita</span><span class="sxs-lookup"><span data-stu-id="c9974-151">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="c9974-152">Používání ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="c9974-152">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)
- [<span data-ttu-id="c9974-153">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c9974-153">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="c9974-154">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="c9974-154">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="c9974-155">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="c9974-155">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
