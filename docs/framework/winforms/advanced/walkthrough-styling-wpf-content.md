---
title: 'Návod: Určení stylu obsahu WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
ms.openlocfilehash: f33ce76e8c14fc84f6429bc48d34437b4f0d97d0
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2018
ms.locfileid: "43257406"
---
# <a name="walkthrough-styling-wpf-content"></a><span data-ttu-id="82ff6-102">Návod: Určení stylu obsahu WPF</span><span class="sxs-lookup"><span data-stu-id="82ff6-102">Walkthrough: Styling WPF Content</span></span>
<span data-ttu-id="82ff6-103">Tento názorný postup ukazují, jak použít používání stylů pro ovládací prvek Windows Presentation Foundation (WPF) hostovaného ve formuláři Windows.</span><span class="sxs-lookup"><span data-stu-id="82ff6-103">This walkthrough show you how to apply styling to a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>  
  
 <span data-ttu-id="82ff6-104">V tomto podrobném návodu můžete provádět následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="82ff6-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="82ff6-105">Vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="82ff6-105">Create the project.</span></span>  
  
-   <span data-ttu-id="82ff6-106">Vytvořte typ ovládacího prvku WPF.</span><span class="sxs-lookup"><span data-stu-id="82ff6-106">Create the WPF control type.</span></span>  
  
-   <span data-ttu-id="82ff6-107">Použití stylu pro ovládací prvek WPF.</span><span class="sxs-lookup"><span data-stu-id="82ff6-107">Apply a style to the WPF control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82ff6-108">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="82ff6-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="82ff6-109">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="82ff6-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="82ff6-110">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="82ff6-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="82ff6-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="82ff6-111">Prerequisites</span></span>  
 <span data-ttu-id="82ff6-112">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="82ff6-112">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="82ff6-113">.</span><span class="sxs-lookup"><span data-stu-id="82ff6-113">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="82ff6-114">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="82ff6-114">Creating the Project</span></span>  
 <span data-ttu-id="82ff6-115">Prvním krokem je vytvoření projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="82ff6-115">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82ff6-116">Při hostování obsahu WPF, jsou podporovány pouze projekty C# a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="82ff6-116">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="82ff6-117">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="82ff6-117">To create the project</span></span>  
  
-   <span data-ttu-id="82ff6-118">Vytvořte nový projekt Formulářové aplikace Windows v jazyce Visual Basic nebo Visual C# s názvem `StylingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="82ff6-118">Create a new Windows Forms Application project in Visual Basic or Visual C# named `StylingWpfContent`.</span></span>  
  
## <a name="creating-the-wpf-control-types"></a><span data-ttu-id="82ff6-119">Vytváření typů ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="82ff6-119">Creating the WPF Control Types</span></span>  
 <span data-ttu-id="82ff6-120">Poté, co do projektu přidáte typ ovládacího prvku WPF, které můžete hostovat jej do <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="82ff6-120">After you add a WPF control type to the project, you can host it in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>  
  
#### <a name="to-create-wpf-control-types"></a><span data-ttu-id="82ff6-121">Chcete-li vytvořit typy ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="82ff6-121">To create WPF control types</span></span>  
  
1.  <span data-ttu-id="82ff6-122">Přidat nový WPF <xref:System.Windows.Controls.UserControl> projektu do řešení.</span><span class="sxs-lookup"><span data-stu-id="82ff6-122">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="82ff6-123">Použití výchozího názvu pro typ ovládacího prvku `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="82ff6-123">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="82ff6-124">Další informace najdete v tématu [návod: vytváření nových WPF obsahu ve Windows Forms v době návrhu](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="82ff6-124">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="82ff6-125">V návrhovém zobrazení, ujistěte se, že `UserControl1` zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="82ff6-125">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="82ff6-126">Další informace najdete v tématu [postupy: výběr a přesunutí prvků na návrhové ploše](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span><span class="sxs-lookup"><span data-stu-id="82ff6-126">For more information, see [How to: Select and Move Elements on the Design Surface](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>  
  
3.  <span data-ttu-id="82ff6-127">V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastností `200`.</span><span class="sxs-lookup"><span data-stu-id="82ff6-127">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="82ff6-128">Přidat <xref:System.Windows.Controls.Button?displayProperty=nameWithType> ovládací prvek <xref:System.Windows.Controls.UserControl> a nastavte hodnotu <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost **zrušit**.</span><span class="sxs-lookup"><span data-stu-id="82ff6-128">Add a <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **Cancel**.</span></span>  
  
5.  <span data-ttu-id="82ff6-129">Přidejte druhý <xref:System.Windows.Controls.Button?displayProperty=nameWithType> ovládací prvek <xref:System.Windows.Controls.UserControl> a nastavte hodnotu <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost **OK**.</span><span class="sxs-lookup"><span data-stu-id="82ff6-129">Add a second <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **OK**.</span></span>  
  
6.  <span data-ttu-id="82ff6-130">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="82ff6-130">Build the project.</span></span>  
  
## <a name="applying-a-style-to-a-wpf-control"></a><span data-ttu-id="82ff6-131">Použití stylu ovládacího prvku WPF</span><span class="sxs-lookup"><span data-stu-id="82ff6-131">Applying a Style to a WPF Control</span></span>  
 <span data-ttu-id="82ff6-132">Můžete použít různé pro používání stylů pro ovládací prvek WPF, chcete-li změnit její vzhled a chování.</span><span class="sxs-lookup"><span data-stu-id="82ff6-132">You can apply different styling to a WPF control to change its appearance and behavior.</span></span>  
  
#### <a name="to-apply-a-style-to-a-wpf-control"></a><span data-ttu-id="82ff6-133">Pokud chcete použít styl ovládacího prvku WPF</span><span class="sxs-lookup"><span data-stu-id="82ff6-133">To apply a style to a WPF control</span></span>  
  
1.  <span data-ttu-id="82ff6-134">Otevřít `Form1` v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="82ff6-134">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="82ff6-135">V **nástrojů**, dvakrát klikněte na panel `UserControl1` k vytvoření instance `UserControl1` ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="82ff6-135">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>  
  
     <span data-ttu-id="82ff6-136">Instance `UserControl1` hostována v novém <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="82ff6-136">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
3.  <span data-ttu-id="82ff6-137">Na panelu inteligentních značek `elementHost1`, klikněte na tlačítko **upravit hostovaný obsah** z rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="82ff6-137">In the smart tag panel for `elementHost1`, click **Edit Hosted Content** from the drop-down list.</span></span>  
  
     <span data-ttu-id="82ff6-138">`UserControl1` Otevře [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="82ff6-138">`UserControl1` opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="82ff6-139">V XAML zobrazení, vložte následující XAML po `<UserControl>` počáteční značku.</span><span class="sxs-lookup"><span data-stu-id="82ff6-139">In XAML view, insert the following XAML after the `<UserControl>` opening tag.</span></span>  
  
     <span data-ttu-id="82ff6-140">Tento XAML vytvoří přechod kontrastní přechodu ohraničení.</span><span class="sxs-lookup"><span data-stu-id="82ff6-140">This XAML creates a gradient with a contrasting gradient border.</span></span> <span data-ttu-id="82ff6-141">Po kliknutí na ovládací prvek přechody jsou změněny na generování vzhled při stisknutí tlačítka.</span><span class="sxs-lookup"><span data-stu-id="82ff6-141">When the control is clicked, the gradients are changed to generate a pressed button look.</span></span> <span data-ttu-id="82ff6-142">Další informace najdete v tématu [styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="82ff6-142">For more information, see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>  
  
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
  
1.  <span data-ttu-id="82ff6-143">Použít `SimpleButton` styl definovaný v předchozím kroku, a na tlačítko Storno vložením následujícího XAML v `<Button>` značky na tlačítko Storno.</span><span class="sxs-lookup"><span data-stu-id="82ff6-143">Apply the `SimpleButton` style defined in the previous step to the Cancel button by inserting the following XAML in the `<Button>` tag of the Cancel button.</span></span>  
  
    ```  
    Style="{StaticResource SimpleButton}  
    ```  
  
     <span data-ttu-id="82ff6-144">Vaše prohlášení tlačítko bude vypadat podobně jako následující XAML.</span><span class="sxs-lookup"><span data-stu-id="82ff6-144">Your button declaration will resemble the following XAML.</span></span>  
  
```xaml  
<Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"  
                Style="{StaticResource SimpleButton}">Cancel</Button>  
```  
  
1.  <span data-ttu-id="82ff6-145">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="82ff6-145">Build the project.</span></span>  
  
2.  <span data-ttu-id="82ff6-146">Otevřít `Form1` v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="82ff6-146">Open `Form1` in the Windows Forms Designer.</span></span>  
  
3.  <span data-ttu-id="82ff6-147">Nový styl platí pro ovládací prvek tlačítko.</span><span class="sxs-lookup"><span data-stu-id="82ff6-147">The new style is applied to the button control.</span></span>  
  
4.  <span data-ttu-id="82ff6-148">Z **ladění** nabídce vyberte možnost **spustit ladění** ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="82ff6-148">From the **Debug** menu, select **Start Debugging** to run the application.</span></span>  
  
5.  <span data-ttu-id="82ff6-149">Klikněte na tlačítko OK a zrušit a zobrazit rozdíly.</span><span class="sxs-lookup"><span data-stu-id="82ff6-149">Click the OK and Cancel buttons and view the differences.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82ff6-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="82ff6-150">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="82ff6-151">Migrace a interoperabilita</span><span class="sxs-lookup"><span data-stu-id="82ff6-151">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="82ff6-152">Používání ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="82ff6-152">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="82ff6-153">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="82ff6-153">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)  
 [<span data-ttu-id="82ff6-154">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="82ff6-154">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="82ff6-155">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="82ff6-155">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
