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
# <a name="walkthrough-style-wpf-content"></a>Návod: Styl WPF obsahu

Tento článek ukazuje, jak použít styl pro ovládací prvek WPF (Windows Presentation Foundation) hostovaný ve formuláři systému Windows.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu potřebujete Visual Studio.

## <a name="create-the-project"></a>Vytvoření projektu

Otevřete Visual Studio a vytvořte nový projekt aplikace Windows `StylingWpfContent`Forms v jazyce Visual Basic nebo Visual C# s názvem .

> [!NOTE]
> Při hostování obsahu WPF jsou podporovány pouze projekty jazyka C# a Visual Basic.

## <a name="create-the-wpf-control-types"></a>Vytvoření typů ovládacích prvku WPF

Po přidání typu ovládacího prvku WPF do projektu <xref:System.Windows.Forms.Integration.ElementHost> jej můžete hostovat v ovládacím prvku.

1. Přidejte do <xref:System.Windows.Controls.UserControl> řešení nový projekt WPF. Použijte výchozí název pro typ `UserControl1.xaml`ovládacího prvku . Další informace naleznete [v tématu Návod: Vytvoření nového obsahu WPF ve formulářích Windows v době návrhu](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).

2. V návrhovém zobrazení `UserControl1` zkontrolujte, zda je tato možnost vybraná.

3. V okně **Vlastnosti** nastavte hodnotu <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti a na <xref:System.Windows.FrameworkElement.Width%2A> **hodnotu 200**.

4. Přidejte <xref:System.Windows.Controls.Button?displayProperty=nameWithType> ovládací <xref:System.Windows.Controls.UserControl> prvek a nastavte <xref:System.Windows.Controls.ContentControl.Content%2A> hodnotu vlastnosti **na Cancel**.

5. Přidejte <xref:System.Windows.Controls.Button?displayProperty=nameWithType> druhý ovládací <xref:System.Windows.Controls.UserControl> prvek a nastavte <xref:System.Windows.Controls.ContentControl.Content%2A> hodnotu vlastnosti na **OK**.

6. Sestavte projekt.

## <a name="apply-a-style-to-a-wpf-control"></a>Použití stylu u ovládacího prvku WPF

Můžete použít jiný styl ovládacího prvku WPF změnit jeho vzhled a chování.

1. Otevřete `Form1` v Návrháři formulářů systému Windows.

1. V **panelu nástrojů**poklepejte `UserControl1` `UserControl1` na vytvoření instance ve formuláři.

   Instance `UserControl1` je hostována v <xref:System.Windows.Forms.Integration.ElementHost> novém `elementHost1`ovládacím prvku s názvem .

1. V panelu inteligentních značek klikněte v `elementHost1`rozevíracím seznamu na Upravit **hostovaný obsah.**

   `UserControl1`otevře v Návrháři WPF.

1. V zobrazení XAML vložte za `<UserControl>` otevírací značku následující XAML. Tento XAML vytvoří přechod s kontrastním ohraničením přechodu. Po klepnutí na ovládací prvek se přechody změní tak, aby generovaly vzhled stisknutého tlačítka. Další informace naleznete [v tématu Styling a Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).

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

1. Použijte `SimpleButton` styl definovaný v předchozím kroku na tlačítko Storno vložením `<Button>` následujícího xaml do značky tlačítka **Storno.**

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   Deklarace tlačítka se bude podobat následujícímu xaml:

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

1. Sestavte projekt.

1. Otevřete `Form1` v Návrháři formulářů systému Windows.

1. Nový styl se aplikuje na ovládací prvek tlačítka.

1. V nabídce **Ladění** vyberte **Spustit ladění,** chcete-li aplikaci spustit.

1. Klikněte na tlačítka **OK** a **Storno** a zobrazte rozdíly.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migrace a interoperabilita](../../wpf/advanced/migration-and-interoperability.md)
- [Používání ovládacích prvků WPF](using-wpf-controls.md)
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
