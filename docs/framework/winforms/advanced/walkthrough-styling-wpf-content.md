---
title: 'Návod: Určení stylu obsahu WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
ms.openlocfilehash: d02e48daad705b29cb7e179417f665c34857896e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529195"
---
# <a name="walkthrough-styling-wpf-content"></a><span data-ttu-id="f7a99-102">Návod: Určení stylu obsahu WPF</span><span class="sxs-lookup"><span data-stu-id="f7a99-102">Walkthrough: Styling WPF Content</span></span>
<span data-ttu-id="f7a99-103">Tento názorný postup ukazují, jak použít stylů do ovládacího prvku Windows Presentation Foundation (WPF) hostované ve formuláři Windows.</span><span class="sxs-lookup"><span data-stu-id="f7a99-103">This walkthrough show you how to apply styling to a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>  
  
 <span data-ttu-id="f7a99-104">V tomto návodu můžete provádět následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="f7a99-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="f7a99-105">Vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="f7a99-105">Create the project.</span></span>  
  
-   <span data-ttu-id="f7a99-106">Vytvořte typ ovládacího prvku WPF.</span><span class="sxs-lookup"><span data-stu-id="f7a99-106">Create the WPF control type.</span></span>  
  
-   <span data-ttu-id="f7a99-107">Použijte styl pro ovládací prvek WPF.</span><span class="sxs-lookup"><span data-stu-id="f7a99-107">Apply a style to the WPF control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7a99-108">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="f7a99-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f7a99-109">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="f7a99-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f7a99-110">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="f7a99-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f7a99-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f7a99-111">Prerequisites</span></span>  
 <span data-ttu-id="f7a99-112">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="f7a99-112">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="f7a99-113">.</span><span class="sxs-lookup"><span data-stu-id="f7a99-113">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="f7a99-114">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="f7a99-114">Creating the Project</span></span>  
 <span data-ttu-id="f7a99-115">Prvním krokem je vytvoření projektu modelu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f7a99-115">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7a99-116">Pokud hostování obsahu subsystému WPF, jsou podporovány pouze projekty C# a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f7a99-116">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="f7a99-117">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="f7a99-117">To create the project</span></span>  
  
-   <span data-ttu-id="f7a99-118">Vytvořte nový projekt aplikace Windows Forms v jazyce Visual Basic a Visual C# s názvem `StylingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="f7a99-118">Create a new Windows Forms Application project in Visual Basic or Visual C# named `StylingWpfContent`.</span></span>  
  
## <a name="creating-the-wpf-control-types"></a><span data-ttu-id="f7a99-119">Vytváření typy ovládacích prvků grafického subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="f7a99-119">Creating the WPF Control Types</span></span>  
 <span data-ttu-id="f7a99-120">Po přidání typu ovládacího prvku WPF do projektu, je možné hostovat v <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f7a99-120">After you add a WPF control type to the project, you can host it in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>  
  
#### <a name="to-create-wpf-control-types"></a><span data-ttu-id="f7a99-121">Chcete-li vytvořit typy ovládacích prvků grafického subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="f7a99-121">To create WPF control types</span></span>  
  
1.  <span data-ttu-id="f7a99-122">Přidat nové WPF <xref:System.Windows.Controls.UserControl> projektu k řešení.</span><span class="sxs-lookup"><span data-stu-id="f7a99-122">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="f7a99-123">Použití výchozího názvu pro typ ovládacího prvku `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="f7a99-123">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="f7a99-124">Další informace najdete v tématu [návod: vytvoření nové WPF obsahu v aplikaci Windows Forms v době návrhu](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="f7a99-124">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="f7a99-125">V návrhovém zobrazení, ujistěte se, že `UserControl1` je vybrána.</span><span class="sxs-lookup"><span data-stu-id="f7a99-125">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="f7a99-126">Další informace najdete v tématu [postup: vyberte a přesunout elementů na návrhovou plochu](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span><span class="sxs-lookup"><span data-stu-id="f7a99-126">For more information, see [How to: Select and Move Elements on the Design Surface](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>  
  
3.  <span data-ttu-id="f7a99-127">V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti, které chcete `200`.</span><span class="sxs-lookup"><span data-stu-id="f7a99-127">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="f7a99-128">Přidat <xref:System.Windows.Controls.Button?displayProperty=nameWithType> řídit k <xref:System.Windows.Controls.UserControl> a nastavte hodnotu <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost **zrušit**.</span><span class="sxs-lookup"><span data-stu-id="f7a99-128">Add a <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **Cancel**.</span></span>  
  
5.  <span data-ttu-id="f7a99-129">Přidejte druhý <xref:System.Windows.Controls.Button?displayProperty=nameWithType> řídit k <xref:System.Windows.Controls.UserControl> a nastavte hodnotu <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost **OK**.</span><span class="sxs-lookup"><span data-stu-id="f7a99-129">Add a second <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **OK**.</span></span>  
  
6.  <span data-ttu-id="f7a99-130">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="f7a99-130">Build the project.</span></span>  
  
## <a name="applying-a-style-to-a-wpf-control"></a><span data-ttu-id="f7a99-131">Použití styl pro ovládací prvek WPF</span><span class="sxs-lookup"><span data-stu-id="f7a99-131">Applying a Style to a WPF Control</span></span>  
 <span data-ttu-id="f7a99-132">Můžete použít různé styly pro ovládací prvek WPF změnit vzhled a chování.</span><span class="sxs-lookup"><span data-stu-id="f7a99-132">You can apply different styling to a WPF control to change its appearance and behavior.</span></span>  
  
#### <a name="to-apply-a-style-to-a-wpf-control"></a><span data-ttu-id="f7a99-133">Pokud chcete použít styl pro ovládací prvek WPF</span><span class="sxs-lookup"><span data-stu-id="f7a99-133">To apply a style to a WPF control</span></span>  
  
1.  <span data-ttu-id="f7a99-134">Otevřete `Form1` v Návrháři formulářů.</span><span class="sxs-lookup"><span data-stu-id="f7a99-134">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="f7a99-135">V **sada nástrojů**, dvakrát klikněte na `UserControl1` k vytvoření instance `UserControl1` na formuláři.</span><span class="sxs-lookup"><span data-stu-id="f7a99-135">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>  
  
     <span data-ttu-id="f7a99-136">Instance `UserControl1` je hostován v nové <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="f7a99-136">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
3.  <span data-ttu-id="f7a99-137">V panelu inteligentních značek pro `elementHost1`, klikněte na tlačítko **upravit hostované obsah** z rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="f7a99-137">In the smart tag panel for `elementHost1`, click **Edit Hosted Content** from the drop-down list.</span></span>  
  
     <span data-ttu-id="f7a99-138">`UserControl1` Otevře se v [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f7a99-138">`UserControl1` opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="f7a99-139">V zobrazení jazyka XAML, vložte následující XAML po `<UserControl>` počáteční značce.</span><span class="sxs-lookup"><span data-stu-id="f7a99-139">In XAML view, insert the following XAML after the `<UserControl>` opening tag.</span></span>  
  
     <span data-ttu-id="f7a99-140">Tato XAML vytvoří přechod s kontrastní přechodu ohraničení.</span><span class="sxs-lookup"><span data-stu-id="f7a99-140">This XAML creates a gradient with a contrasting gradient border.</span></span> <span data-ttu-id="f7a99-141">Při kliknutí na ovládací prvek přechody se mění ke generování stisknutého tlačítka podívejte.</span><span class="sxs-lookup"><span data-stu-id="f7a99-141">When the control is clicked, the gradients are changed to generate a pressed button look.</span></span> <span data-ttu-id="f7a99-142">Další informace najdete v tématu [stylů a ukázka](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="f7a99-142">For more information, see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>  
  
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
  
1.  <span data-ttu-id="f7a99-143">Použít `SimpleButton` styl definované v předchozím kroku na tlačítko Storno vložením následující XAML v `<Button>` značky na tlačítko Storno.</span><span class="sxs-lookup"><span data-stu-id="f7a99-143">Apply the `SimpleButton` style defined in the previous step to the Cancel button by inserting the following XAML in the `<Button>` tag of the Cancel button.</span></span>  
  
    ```  
    Style="{StaticResource SimpleButton}  
    ```  
  
     <span data-ttu-id="f7a99-144">Vaše tlačítko deklarace bude připomínat následující XAML.</span><span class="sxs-lookup"><span data-stu-id="f7a99-144">Your button declaration will resemble the following XAML.</span></span>  
  
```xaml  
<Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"  
                Style="{StaticResource SimpleButton}">Cancel</Button>  
```  
  
1.  <span data-ttu-id="f7a99-145">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="f7a99-145">Build the project.</span></span>  
  
2.  <span data-ttu-id="f7a99-146">Otevřete `Form1` v Návrháři formulářů.</span><span class="sxs-lookup"><span data-stu-id="f7a99-146">Open `Form1` in the Windows Forms Designer.</span></span>  
  
3.  <span data-ttu-id="f7a99-147">Nový styl je použit do ovládacího prvku tlačítko.</span><span class="sxs-lookup"><span data-stu-id="f7a99-147">The new style is applied to the button control.</span></span>  
  
4.  <span data-ttu-id="f7a99-148">Z **ladění** nabídce vyberte možnost **spustit ladění** ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="f7a99-148">From the **Debug** menu, select **Start Debugging** to run the application.</span></span>  
  
5.  <span data-ttu-id="f7a99-149">Klepnutím na tlačítko OK a zrušit a zobrazit rozdíly.</span><span class="sxs-lookup"><span data-stu-id="f7a99-149">Click the OK and Cancel buttons and view the differences.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7a99-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="f7a99-150">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="f7a99-151">Migrace a interoperabilita</span><span class="sxs-lookup"><span data-stu-id="f7a99-151">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="f7a99-152">Používání ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="f7a99-152">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="f7a99-153">Návrhář WPF</span><span class="sxs-lookup"><span data-stu-id="f7a99-153">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="f7a99-154">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="f7a99-154">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="f7a99-155">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="f7a99-155">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
