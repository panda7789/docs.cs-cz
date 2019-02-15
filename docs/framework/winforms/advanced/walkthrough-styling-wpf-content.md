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
# <a name="walkthrough-styling-wpf-content"></a>Průvodce: Určení stylu obsahu WPF
Tento názorný postup ukazují, jak použít používání stylů pro ovládací prvek Windows Presentation Foundation (WPF) hostovaného ve formuláři Windows.

 V tomto podrobném návodu můžete provádět následující úlohy:

-   Vytvoření projektu.

-   Vytvořte typ ovládacího prvku WPF.

-   Použití stylu pro ovládací prvek WPF.

> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   Visual Studio 2012.  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu Windows Forms.  
  
> [!NOTE]
>  Při hostování obsahu WPF, jsou podporovány pouze projekty C# a Visual Basic.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
-   Vytvořte nový projekt Formulářové aplikace Windows v jazyce Visual Basic nebo Visual C# s názvem `StylingWpfContent`.  
  
## <a name="creating-the-wpf-control-types"></a>Vytváření typů ovládacích prvků WPF  
 Poté, co do projektu přidáte typ ovládacího prvku WPF, které můžete hostovat jej do <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku.  
  
#### <a name="to-create-wpf-control-types"></a>Chcete-li vytvořit typy ovládacích prvků WPF  
  
1.  Přidat nový WPF <xref:System.Windows.Controls.UserControl> projektu do řešení. Použití výchozího názvu pro typ ovládacího prvku `UserControl1.xaml`. Další informace najdete v tématu [názorný postup: Vytvoření nového obsahu WPF ve Windows Forms v době návrhu](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  V návrhovém zobrazení, ujistěte se, že `UserControl1` zaškrtnuto. Další informace najdete v tématu [jak: Vyberte a přesuňte prvků na návrhové ploše](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).  
  
3.  V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastností `200`.  
  
4.  Přidat <xref:System.Windows.Controls.Button?displayProperty=nameWithType> ovládací prvek <xref:System.Windows.Controls.UserControl> a nastavte hodnotu <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost **zrušit**.  
  
5.  Přidejte druhý <xref:System.Windows.Controls.Button?displayProperty=nameWithType> ovládací prvek <xref:System.Windows.Controls.UserControl> a nastavte hodnotu <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost **OK**.  
  
6.  Sestavte projekt.  
  
## <a name="applying-a-style-to-a-wpf-control"></a>Použití stylu ovládacího prvku WPF  
 Můžete použít různé pro používání stylů pro ovládací prvek WPF, chcete-li změnit její vzhled a chování.  
  
#### <a name="to-apply-a-style-to-a-wpf-control"></a>Pokud chcete použít styl ovládacího prvku WPF  
  
1.  Otevřít `Form1` v Návrháři formulářů Windows.  
  
2.  V **nástrojů**, dvakrát klikněte na panel `UserControl1` k vytvoření instance `UserControl1` ve formuláři.  
  
     Instance `UserControl1` hostována v novém <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost1`.  
  
3.  Na panelu inteligentních značek `elementHost1`, klikněte na tlačítko **upravit hostovaný obsah** z rozevíracího seznamu.  
  
     `UserControl1` Otevře [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
4.  V XAML zobrazení, vložte následující XAML po `<UserControl>` počáteční značku.  
  
     Tento XAML vytvoří přechod kontrastní přechodu ohraničení. Po kliknutí na ovládací prvek přechody jsou změněny na generování vzhled při stisknutí tlačítka. Další informace najdete v tématu [styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
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
  
1.  Použít `SimpleButton` styl definovaný v předchozím kroku, a na tlačítko Storno vložením následujícího XAML v `<Button>` značky na tlačítko Storno.  
  
    ```  
    Style="{StaticResource SimpleButton}  
    ```  
  
     Vaše prohlášení tlačítko bude vypadat podobně jako následující XAML.  
  
```xaml  
<Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"  
                Style="{StaticResource SimpleButton}">Cancel</Button>  
```  
  
1.  Sestavte projekt.  
  
2.  Otevřít `Form1` v Návrháři formulářů Windows.  
  
3.  Nový styl platí pro ovládací prvek tlačítko.  
  
4.  Z **ladění** nabídce vyberte možnost **spustit ladění** ke spuštění aplikace.  
  
5.  Klikněte na tlačítko OK a zrušit a zobrazit rozdíly.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migrace a interoperabilita](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)
- [Používání ovládacích prvků WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)
