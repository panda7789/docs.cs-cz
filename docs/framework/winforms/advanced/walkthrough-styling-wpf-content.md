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
# <a name="walkthrough-style-wpf-content"></a>Návod: Styl obsahu WPF

V tomto návodu se dozvíte, jak použít styly pro ovládací prvek Windows Presentation Foundation (WPF) hostovaný ve formuláři Windows.

 V tomto návodu provedete následující úlohy:

- Vytvořte projekt.

- Vytvořte typ ovládacího prvku WPF.

- Použijte styl pro ovládací prvek WPF.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto Názorného postupu potřebujete Visual Studio.

## <a name="create-the-project"></a>Vytvoření projektu

Otevřete Visual Studio a vytvořte nový projekt aplikace model Windows Forms v Visual Basic nebo vizuálu C# s názvem `StylingWpfContent`.

> [!NOTE]
> Při hostování obsahu WPF jsou podporovány C# pouze projekty a Visual Basic.

## <a name="create-the-wpf-control-types"></a>Vytvoření typů ovládacích prvků WPF

Po přidání typu ovládacího prvku WPF do projektu jej můžete hostovat v <xref:System.Windows.Forms.Integration.ElementHost> ovládacím prvku.

1. Přidejte do řešení nový <xref:System.Windows.Controls.UserControl> projekt WPF. Použijte výchozí název pro typ ovládacího prvku, `UserControl1.xaml`. Další informace najdete v tématu [Návod: Vytváření nového obsahu WPF v model Windows Forms v době](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)návrhu.

2. V zobrazení Návrh se ujistěte, že `UserControl1` je vybraná možnost. Další informace najdete v tématu [jak: Vyberte a přesuňte prvky na Návrhová plocha](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).

3. V okně **vlastnosti** nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> vlastností a <xref:System.Windows.FrameworkElement.Height%2A> na `200`.

4. Přidejte ovládací prvek <xref:System.Windows.Controls.UserControl> do a <xref:System.Windows.Controls.ContentControl.Content%2A> nastavte hodnotu vlastnosti na **zrušit.** <xref:System.Windows.Controls.Button?displayProperty=nameWithType>

5. Přidejte druhý <xref:System.Windows.Controls.Button?displayProperty=nameWithType> ovládací prvek <xref:System.Windows.Controls.UserControl> do a <xref:System.Windows.Controls.ContentControl.Content%2A> nastavte hodnotu vlastnosti na **OK**.

6. Sestavte projekt.

## <a name="apply-a-style-to-a-wpf-control"></a>Použití stylu pro ovládací prvek WPF

Můžete použít různé styly pro ovládací prvek WPF a změnit jeho vzhled a chování.

1. Otevřete `Form1` v Návrhář formulářů.

1. Na **panelu nástrojů**poklikejte na `UserControl1` `UserControl1` vytvoření instance ve formuláři.

     Instance `UserControl1` je hostována v novém <xref:System.Windows.Forms.Integration.ElementHost> ovládacím prvku s názvem `elementHost1`.

1. Na panelu inteligentních značek pro `elementHost1`klikněte v rozevíracím seznamu na **Upravit hostovaný obsah** .

     `UserControl1`Otevře se [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]v.

1. V zobrazení XAML vložte následující kód XAML za `<UserControl>` úvodní značku.

     Tento kód XAML vytvoří přechod s kontrastem ohraničení přechodu. Při kliknutí na ovládací prvek se přechody změní tak, aby se vygenerovalo tlačítko při stisknutí tlačítka. Další informace najdete v tématu [stylování a šablonování](../../wpf/controls/styling-and-templating.md).

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

1. Použijte styl definovaný v předchozím kroku na tlačítko Storno vložením následujícího kódu XAML `<Button>` do značky tlačítka Storno. `SimpleButton`

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   Vaše deklarace tlačítka bude vypadat podobně jako v následujícím kódu XAML:

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

1. Sestavte projekt.

1. Otevřete `Form1` v Návrhář formulářů.

1. Nový styl se aplikuje na ovládací prvek tlačítko.

1. V nabídce **ladění** vyberte **Spustit ladění** , aby se aplikace spustila.

1. Klikněte na tlačítko OK a tlačítka Storno a zobrazte rozdíly.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migrace a interoperabilita](../../wpf/advanced/migration-and-interoperability.md)
- [Používání ovládacích prvků WPF](using-wpf-controls.md)
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Přehled XAML (WPF)](../../wpf/advanced/xaml-overview-wpf.md)
- [Styly a šablony](../../wpf/controls/styling-and-templating.md)
