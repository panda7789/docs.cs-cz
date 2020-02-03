---
title: 'Návod: styl obsahu WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e52297f51c74fc3dba93c987fd5b9bd5b6801777
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732540"
---
# <a name="walkthrough-style-wpf-content"></a>Návod: styl obsahu WPF

V tomto článku se dozvíte, jak použít styly pro řízení Windows Presentation Foundation (WPF) hostovaného ve formuláři Windows.

## <a name="prerequisites"></a>Předpoklady

K dokončení tohoto Názorného postupu potřebujete Visual Studio.

## <a name="create-the-project"></a>Vytvoření projektu

Otevřete Visual Studio a vytvořte nový projekt aplikace model Windows Forms v Visual Basic nebo vizuálu C# s názvem `StylingWpfContent`.

> [!NOTE]
> Při hostování obsahu WPF jsou podporovány C# pouze projekty a Visual Basic.

## <a name="create-the-wpf-control-types"></a>Vytvoření typů ovládacích prvků WPF

Po přidání typu ovládacího prvku WPF do projektu jej můžete hostovat v ovládacím prvku <xref:System.Windows.Forms.Integration.ElementHost>.

1. Přidejte do řešení nový projekt WPF <xref:System.Windows.Controls.UserControl>. Použijte výchozí název pro typ ovládacího prvku `UserControl1.xaml`. Další informace najdete v tématu [Návod: vytvoření nového obsahu WPF na model Windows Forms v době návrhu](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).

2. V zobrazení Návrh se ujistěte, že je vybrána možnost `UserControl1`.

3. V okně **vlastnosti** nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a vlastnosti <xref:System.Windows.FrameworkElement.Height%2A> na **200**.

4. Do <xref:System.Windows.Controls.UserControl> přidejte ovládací prvek <xref:System.Windows.Controls.Button?displayProperty=nameWithType> a nastavte hodnotu vlastnosti <xref:System.Windows.Controls.ContentControl.Content%2A> na **Zrušit**.

5. Přidejte do <xref:System.Windows.Controls.UserControl> druhý ovládací prvek <xref:System.Windows.Controls.Button?displayProperty=nameWithType> a nastavte hodnotu vlastnosti <xref:System.Windows.Controls.ContentControl.Content%2A> na **OK**.

6. Sestavte projekt.

## <a name="apply-a-style-to-a-wpf-control"></a>Použití stylu pro ovládací prvek WPF

Můžete použít různé styly pro ovládací prvek WPF a změnit jeho vzhled a chování.

1. Otevřete `Form1` v Návrhář formulářů.

1. Na **panelu nástrojů**dvakrát klikněte na `UserControl1`. tím se vytvoří instance `UserControl1` ve formuláři.

   Instance `UserControl1` je hostována v novém ovládacím prvku <xref:System.Windows.Forms.Integration.ElementHost> s názvem `elementHost1`.

1. Na panelu inteligentních značek pro `elementHost1`v rozevíracím seznamu klikněte na **Upravit hostovaný obsah** .

   `UserControl1` se otevře v Návrháři WPF.

1. V zobrazení XAML vložte následující kód XAML po `<UserControl>` počáteční značku. Tento kód XAML vytvoří přechod s kontrastem ohraničení přechodu. Při kliknutí na ovládací prvek se přechody změní tak, aby se vygenerovalo tlačítko při stisknutí tlačítka. Další informace najdete v tématu [stylování a šablonování](../../../desktop-wpf/fundamentals/styles-templates-overview.md).

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

1. Použijte styl `SimpleButton` definovaný v předchozím kroku na tlačítko Storno vložením následujícího kódu XAML do značky `<Button>` tlačítka **Zrušit** .

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

1. Klikněte na tlačítko **OK** a tlačítka **Storno** a zobrazte rozdíly.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migrace a interoperabilita](../../wpf/advanced/migration-and-interoperability.md)
- [Používání ovládacích prvků WPF](using-wpf-controls.md)
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Přehled XAML (WPF)](../../wpf/advanced/xaml-overview-wpf.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
