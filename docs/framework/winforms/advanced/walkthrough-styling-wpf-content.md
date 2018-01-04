---
title: "Návod: Určení stylu obsahu WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0fa4772ebb321f927087fe13d0d50a6ae8145e55
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-styling-wpf-content"></a>Návod: Určení stylu obsahu WPF
Tento názorný postup ukazují, jak použít stylů do ovládacího prvku Windows Presentation Foundation (WPF) hostované ve formuláři Windows.  
  
 V tomto návodu můžete provádět následující úlohy:  
  
-   Vytvoření projektu.  
  
-   Vytvořte typ ovládacího prvku WPF.  
  
-   Použijte styl pro ovládací prvek WPF.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu modelu Windows Forms.  
  
> [!NOTE]
>  Pokud hostování obsahu subsystému WPF, jsou podporovány pouze projekty C# a Visual Basic.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
-   Vytvořte nový projekt aplikace Windows Forms v jazyce Visual Basic a Visual C# s názvem `StylingWpfContent`.  
  
## <a name="creating-the-wpf-control-types"></a>Vytváření typy ovládacích prvků grafického subsystému WPF  
 Po přidání typu ovládacího prvku WPF do projektu, je možné hostovat v <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku.  
  
#### <a name="to-create-wpf-control-types"></a>Chcete-li vytvořit typy ovládacích prvků grafického subsystému WPF  
  
1.  Přidat nové WPF <xref:System.Windows.Controls.UserControl> projektu k řešení. Použití výchozího názvu pro typ ovládacího prvku `UserControl1.xaml`. Další informace najdete v tématu [návod: vytvoření nové WPF obsahu v aplikaci Windows Forms v době návrhu](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  V návrhovém zobrazení, ujistěte se, že `UserControl1` je vybrána. Další informace najdete v tématu [postup: vyberte a přesunout elementů na návrhovou plochu](http://msdn.microsoft.com/en-us/54cb70b6-b35b-46e4-a0cc-65189399c474).  
  
3.  V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti, které chcete `200`.  
  
4.  Přidat <xref:System.Windows.Controls.Button?displayProperty=nameWithType> řídit k <xref:System.Windows.Controls.UserControl> a nastavte hodnotu <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost **zrušit**.  
  
5.  Přidejte druhý <xref:System.Windows.Controls.Button?displayProperty=nameWithType> řídit k <xref:System.Windows.Controls.UserControl> a nastavte hodnotu <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost **OK**.  
  
6.  Sestavte projekt.  
  
## <a name="applying-a-style-to-a-wpf-control"></a>Použití styl pro ovládací prvek WPF  
 Můžete použít různé styly pro ovládací prvek WPF změnit vzhled a chování.  
  
#### <a name="to-apply-a-style-to-a-wpf-control"></a>Pokud chcete použít styl pro ovládací prvek WPF  
  
1.  Otevřete `Form1` v Návrháři formulářů.  
  
2.  V **sada nástrojů**, dvakrát klikněte na `UserControl1` k vytvoření instance `UserControl1` na formuláři.  
  
     Instance `UserControl1` je hostován v nové <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost1`.  
  
3.  V panelu inteligentních značek pro `elementHost1`, klikněte na tlačítko **upravit hostované obsah** z rozevíracího seznamu.  
  
     `UserControl1`Otevře se v [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
4.  V zobrazení jazyka XAML, vložte následující XAML po `<UserControl>` počáteční značce.  
  
     Tato XAML vytvoří přechod s kontrastní přechodu ohraničení. Při kliknutí na ovládací prvek přechody se mění ke generování stisknutého tlačítka podívejte. Další informace najdete v tématu [stylů a ukázka](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
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
  
1.  Použít `SimpleButton` styl definované v předchozím kroku na tlačítko Storno vložením následující XAML v `<Button>` značky na tlačítko Storno.  
  
    ```  
    Style="{StaticResource SimpleButton}  
    ```  
  
     Vaše tlačítko deklarace bude připomínat následující XAML.  
  
```xaml  
<Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"  
                Style="{StaticResource SimpleButton}">Cancel</Button>  
```  
  
1.  Sestavte projekt.  
  
2.  Otevřete `Form1` v Návrháři formulářů.  
  
3.  Nový styl je použit do ovládacího prvku tlačítko.  
  
4.  Z **ladění** nabídce vyberte možnost **spustit ladění** ke spuštění aplikace.  
  
5.  Klepnutím na tlačítko OK a zrušit a zobrazit rozdíly.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Migrace a interoperabilita](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [Používání ovládacích prvků WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [Návrhář WPF](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)
