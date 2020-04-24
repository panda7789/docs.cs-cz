---
title: 'Návod: Vytvoření tlačítka použitím XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
ms.openlocfilehash: a8cc227703e81e5de9dea7e44e10dfecca2cd05c
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646466"
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a>Návod: Vytvoření tlačítka použitím XAML

Cílem tohoto návodu je zjistit, jak vytvořit animované tlačítko pro použití v aplikaci WPF (Windows Presentation Foundation). Tento návod používá styly a šablonu k vytvoření přizpůsobeného prostředku tlačítka, který umožňuje opakované použití kódu a oddělení logiky tlačítka z deklarace tlačítka. Tento návod je napsán [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]zcela v .

> [!IMPORTANT]
> Tento návod vás provede kroky pro vytvoření aplikace zadáním nebo [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] zkopírováním a vložením do sady Visual Studio. Pokud chcete se dozvědět, jak pomocí návrháře vytvořit stejnou aplikaci, naleznete v [tématu Vytvoření tlačítka pomocí prolnutí výrazů společnosti Microsoft](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).

Následující obrázek znázorňuje dokončená tlačítka.

![Vlastní tlačítka, která byla vytvořena pomocí xaml](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")

## <a name="create-basic-buttons"></a>Vytvořit základní tlačítka

Začněme vytvořením nového projektu a přidáním několika tlačítek do okna.

### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a>Vytvoření nového projektu WPF a přidání tlačítek do okna

1. Spusťte Visual Studio.

2. **Vytvořte nový projekt WPF:** V nabídce **Soubor** přejděte na **Nový**a potom klepněte na **položku Project**. Najděte šablonu **aplikace systému Windows (WPF)** a pojmenujte projekt "AnimatedButton". Tím se vytvoří kostra pro aplikaci.

3. **Přidejte základní výchozí tlačítka:** Všechny soubory, které potřebujete pro tento návod jsou poskytovány šablonou. Otevřete soubor Window1.xaml poklepáním v Průzkumníku řešení. Ve výchozím nastavení <xref:System.Windows.Controls.Grid> je prvek v Window1.xaml. Odeberte <xref:System.Windows.Controls.Grid> prvek a přidejte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] na stránku několik tlačítek zadáním nebo zkopírováním a vložením následujícího zvýrazněného kódu do okna 1.xaml:

    ```xaml
    <Window x:Class="AnimatedButton.Window1"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      Title="AnimatedButton" Height="300" Width="300"
      Background="Black">
      <!-- Buttons arranged vertically inside a StackPanel. -->
      <StackPanel HorizontalAlignment="Left">
          <Button>Button 1</Button>
          <Button>Button 2</Button>
          <Button>Button 3</Button>
      </StackPanel>
    </Window>
    ```

     Stisknutím klávesy F5 spusťte aplikaci. měli byste vidět sadu tlačítek, která vypadá jako na následujícím obrázku.

     ![Tři základní tlačítka](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")

     Nyní, když jste vytvořili základní tlačítka, jste dokončili práci v souboru Window1.xaml. Zbytek návodu se zaměřuje na soubor app.xaml, definování stylů a šablonu pro tlačítka.

## <a name="set-basic-properties"></a>Nastavení základních vlastností

Dále nastavíme některé vlastnosti těchto tlačítek, abybylo řízení vzhledu a rozložení tlačítka. Místo nastavování vlastností na tlačítkách jednotlivě použijete prostředky k definování vlastností tlačítek pro celou aplikaci. Aplikační prostředky jsou koncepčně podobné externím kaskádovým šablonám stylů CSS (CSS) pro webové stránky; prostředky jsou však mnohem výkonnější než kaskádové šablony stylů (CSS), jak uvidíte na konci tohoto návodu. Další informace o prostředcích naleznete v tématu [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).

### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a>Použití stylů k nastavení základních vlastností tlačítek

1. **Definujte blok Application.Resources:** Otevřete soubor app.xaml a přidejte následující zvýrazněné značky, pokud k ní ještě není:

    ```xaml
    <Application x:Class="AnimatedButton.App"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      StartupUri="Window1.xaml"
      >
      <Application.Resources>
        <!-- Resources for the entire application can be defined here. -->
      </Application.Resources>
    </Application>
    ```

     Obor prostředků je určen tím, kde definujete prostředek. Definování prostředků `Application.Resources` v souboru app.xaml umožňuje prostředek použít z libovolného místa v aplikaci. Další informace o definování rozsahu prostředků naleznete v tématu [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).

2. **Vytvořte styl a definujte s ním základní hodnoty vlastností:** Přidejte do bloku `Application.Resources` následující značky. Tato značka vytvoří, <xref:System.Windows.Style> která platí pro všechna tlačítka <xref:System.Windows.FrameworkElement.Width%2A> v aplikaci, nastavení <xref:System.Windows.FrameworkElement.Margin%2A> tlačítek na 90 a na 10:

    ```xaml
    <Application.Resources>
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>
    </Application.Resources>
    ```

     Vlastnost <xref:System.Windows.Style.TargetType%2A> určuje, že styl platí pro všechny <xref:System.Windows.Controls.Button>objekty typu . Každý <xref:System.Windows.Setter> nastaví jinou <xref:System.Windows.Style>hodnotu vlastnosti pro . Proto v tomto okamžiku každé tlačítko v aplikaci má šířku 90 a rozpětí 10.  Pokud stisknete klávesu F5 a spustíte aplikaci, zobrazí se následující okno.

     ![Tlačítka o šířce 90 a okraji 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")

     Existuje mnohem více, co můžete udělat se styly, včetně různých způsobů, jak doladit, jaké objekty jsou cílené, určení komplexních hodnot vlastností a dokonce i použití stylů jako vstupu pro jiné styly. Další informace naleznete [v tématu Styling a Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).

3. **Nastavte hodnotu vlastnosti stylu na prostředek:** Prostředky umožňují jednoduchý způsob opakovaného použití běžně definovaných objektů a hodnot. Je zvláště užitečné definovat složité hodnoty pomocí prostředků, aby váš kód více modulární. Do souboru app.xaml přidejte následující zvýrazněné značky.

    ```xaml
    <Application.Resources>
      <LinearGradientBrush x:Key="GrayBlueGradientBrush" StartPoint="0,0" EndPoint="1,1">
        <GradientStop Color="DarkGray" Offset="0" />
        <GradientStop Color="#CCCCFF" Offset="0.5" />
        <GradientStop Color="DarkGray" Offset="1" />
      </LinearGradientBrush>
      <Style TargetType="{x:Type Button}">
        <Setter Property="Background" Value="{StaticResource GrayBlueGradientBrush}" />
        <Setter Property="Width" Value="80" />
        <Setter Property="Margin" Value="10" />
      </Style>
    </Application.Resources>
    ```

     Přímo pod `Application.Resources` blokem jste vytvořili prostředek s názvem "GrayBlueGradientBrush". Tento prostředek definuje vodorovný přechod. Tento prostředek lze použít jako hodnotu vlastnosti z libovolného místa v <xref:System.Windows.Controls.Control.Background%2A> aplikaci, včetně uvnitř setter stylu tlačítka pro vlastnost. Nyní všechna tlačítka mají <xref:System.Windows.Controls.Control.Background%2A> hodnotu vlastnosti tohoto přechodu.

     Stisknutím klávesy F5 spusťte aplikaci. Mělo by to vypadat takto.

     ![Tlačítka s pozadím přechodu](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")

## <a name="create-a-template-that-defines-the-look-of-the-button"></a>Vytvoření šablony, která definuje vzhled tlačítka

V této části vytvoříte šablonu, která přizpůsobí vzhled (prezentaci) tlačítka. Prezentace tlačítka se skládá z několika objektů, včetně obdélníků a dalších komponent, aby tlačítko jedinečný vzhled.

Zatím ovládací prvek, jak tlačítka vypadají v aplikaci byla omezena na změnu vlastností tlačítka. Co když chcete provést radikálnější změny vzhledu tlačítka? Šablony umožňují výkonnou kontrolu nad prezentací objektu. Vzhledem k tomu, že šablony lze použít v rámci stylů, můžete použít šablonu pro všechny objekty, které styl platí pro (v tomto návodu, tlačítko).

### <a name="to-use-the-template-to-define-the-look-of-the-button"></a>Použití šablony k definování vzhledu tlačítka

1. **Nastavte šablonu:** Vzhledem <xref:System.Windows.Controls.Button> k <xref:System.Windows.Controls.Control.Template%2A> tomu, že ovládací prvky jako mají vlastnost, můžete definovat <xref:System.Windows.Style> hodnotu vlastnosti šablony stejně jako ostatní hodnoty vlastností, které jsme nastavili v použití <xref:System.Windows.Setter>. Přidejte následující zvýrazněné značky do stylu tlačítka.

    ```xaml
    <Application.Resources>
      <LinearGradientBrush x:Key="GrayBlueGradientBrush"
        StartPoint="0,0" EndPoint="1,1">
        <GradientStop Color="DarkGray" Offset="0" />
        <GradientStop Color="#CCCCFF" Offset="0.5" />
        <GradientStop Color="DarkGray" Offset="1" />
      </LinearGradientBrush>
      <Style TargetType="{x:Type Button}">
        <Setter Property="Background" Value="{StaticResource GrayBlueGradientBrush}" />
        <Setter Property="Width" Value="80" />
        <Setter Property="Margin" Value="10" />
        <Setter Property="Template">
          <Setter.Value>
            <!-- The button template is defined here. -->
          </Setter.Value>
        </Setter>
      </Style>
    </Application.Resources>
    ```

2. **Změnit prezentaci tlačítka:** V tomto okamžiku je třeba definovat šablonu. Přidejte následující zvýrazněné značky. Tato značka určuje <xref:System.Windows.Shapes.Rectangle> dva prvky se zaoblenými hranami, následované <xref:System.Windows.Controls.DockPanel>. Slouží <xref:System.Windows.Controls.DockPanel> k hostování <xref:System.Windows.Controls.ContentPresenter> tlačítka. A <xref:System.Windows.Controls.ContentPresenter> zobrazí obsah tlačítka. V tomto návodu je obsahem text ("Tlačítko 1", "Tlačítko 2", "Tlačítko 3"). Všechny součásti šablony (obdélníky a <xref:System.Windows.Controls.DockPanel>) jsou umístěny <xref:System.Windows.Controls.Grid>uvnitř .

    ```xaml
    <Setter.Value>
      <ControlTemplate TargetType="Button">
        <Grid Width="{TemplateBinding Width}" Height="{TemplateBinding Height}" ClipToBounds="True">
          <!-- Outer Rectangle with rounded corners. -->
          <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}" RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />
          <!-- Inner Rectangle with rounded corners. -->
          <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Stroke="Transparent" StrokeThickness="20" Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20" />
          <!-- Present Content (text) of the button. -->
          <DockPanel Name="myContentPresenterDockPanel">
            <ContentPresenter x:Name="myContentPresenter" Margin="20" Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />
          </DockPanel>
        </Grid>
      </ControlTemplate>
    </Setter.Value>
    ```

     Stisknutím klávesy F5 spusťte aplikaci. Mělo by to vypadat takto.

     ![Okno se 3 tlačítky](./media/custom-button-animatedbutton-4.gif)

3. **Přidejte glasseffect do šablony:** Dále přidáte sklenici. Nejprve vytvoříte některé prostředky, které vytvoří efekt sklonu skla. Přidejte tyto prostředky `Application.Resources` přechodu kdekoli v bloku:

    ```xaml
    <Application.Resources>
      <GradientStopCollection x:Key="MyGlassGradientStopsResource">
        <GradientStop Color="WhiteSmoke" Offset="0.2" />
        <GradientStop Color="Transparent" Offset="0.4" />
        <GradientStop Color="WhiteSmoke" Offset="0.5" />
        <GradientStop Color="Transparent" Offset="0.75" />
        <GradientStop Color="WhiteSmoke" Offset="0.9" />
        <GradientStop Color="Transparent" Offset="1" />
      </GradientStopCollection>
      <LinearGradientBrush x:Key="MyGlassBrushResource"
        StartPoint="0,0" EndPoint="1,1" Opacity="0.75"
        GradientStops="{StaticResource MyGlassGradientStopsResource}" />
    <!-- Styles and other resources below here. -->
    ```

     Tyto prostředky se <xref:System.Windows.Shapes.Shape.Fill%2A> používají jako pro obdélník, <xref:System.Windows.Controls.Grid> který vložíme do šablony tlačítka. Přidejte do šablony následující zvýrazněné značky.

    ```xaml
    <Setter.Value>
      <ControlTemplate TargetType="{x:Type Button}">
        <Grid Width="{TemplateBinding Width}" Height="{TemplateBinding Height}"
          ClipToBounds="True">

        <!-- Outer Rectangle with rounded corners. -->
        <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}"
          RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />

        <!-- Inner Rectangle with rounded corners. -->
        <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch" Stroke="Transparent" StrokeThickness="20"
          Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20" />

        <!-- Glass Rectangle -->
        <Rectangle x:Name="glassCube" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch"
          StrokeThickness="2" RadiusX="10" RadiusY="10" Opacity="0"
          Fill="{StaticResource MyGlassBrushResource}"
          RenderTransformOrigin="0.5,0.5">
          <Rectangle.Stroke>
            <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">
              <LinearGradientBrush.GradientStops>
                <GradientStop Offset="0.0" Color="LightBlue" />
                <GradientStop Offset="1.0" Color="Gray" />
              </LinearGradientBrush.GradientStops>
            </LinearGradientBrush>
          </Rectangle.Stroke>
          <!-- These transforms have no effect as they are declared here.
          The reason the transforms are included is to be targets
          for animation (see later). -->
          <Rectangle.RenderTransform>
            <TransformGroup>
              <ScaleTransform />
              <RotateTransform />
            </TransformGroup>
          </Rectangle.RenderTransform>
          <!-- A BevelBitmapEffect is applied to give the button a "Beveled" look. -->
          <Rectangle.BitmapEffect>
            <BevelBitmapEffect />
          </Rectangle.BitmapEffect>
        </Rectangle>

        <!-- Present Text of the button. -->
        <DockPanel Name="myContentPresenterDockPanel">
          <ContentPresenter x:Name="myContentPresenter" Margin="20"
            Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />
        </DockPanel>
      </Grid>
    </ControlTemplate>
    </Setter.Value>
    ```

     Všimněte <xref:System.Windows.UIElement.Opacity%2A> si, že `x:Name` obdélník s vlastností "glassCube" je 0, takže při spuštění vzorku, nevidíte skleněný obdélník překrytý nahoře. Je to proto, že později přidáme aktivační události do šablony, když uživatel interaguje s tlačítkem. Můžete však vidět, jak tlačítko vypadá <xref:System.Windows.UIElement.Opacity%2A> nyní změnou hodnoty na 1 a spuštěním aplikace. Prohlédněte si následující obrázek. Než přesete další krok, změňte zadní na <xref:System.Windows.UIElement.Opacity%2A> 0.

     ![Vlastní tlačítka, která byla vytvořena pomocí xaml](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")

## <a name="create-button-interactivity"></a>Vytvořit interaktivitu tlačítka

V této části vytvoříte aktivační události vlastností a aktivační události pro změnu hodnot vlastností a spuštění animací v reakci na akce uživatele, jako je přesunutí ukazatele myši nad tlačítko a kliknutí.

Snadný způsob, jak přidat interaktivitu (přejet myší, přejet myší, kliknout a tak dále) je definovat aktivační události v šabloně nebo stylu. Chcete-li <xref:System.Windows.Trigger>vytvořit , definujete vlastnost "podmínka", například: Hodnota vlastnosti button <xref:System.Windows.UIElement.IsMouseOver%2A> je rovna `true`. Potom definujete nastavení (akce), které se uskuteční, když je podmínka aktivační události true.

### <a name="to-create-button-interactivity"></a>Vytvoření interaktivity tlačítek

1. **Přidat aktivační události šablony:** Přidejte zvýrazněné značky do šablony.

    ```xaml
    <Setter.Value>
      <ControlTemplate TargetType="{x:Type Button}">
        <Grid Width="{TemplateBinding Width}"
          Height="{TemplateBinding Height}" ClipToBounds="True">

          <!-- Outer Rectangle with rounded corners. -->
          <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch"
          VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}"
          RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />

          <!-- Inner Rectangle with rounded corners. -->
          <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch"
            VerticalAlignment="Stretch" Stroke="Transparent"
            StrokeThickness="20"
            Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20"
          />

          <!-- Glass Rectangle -->
          <Rectangle x:Name="glassCube" HorizontalAlignment="Stretch"
            VerticalAlignment="Stretch"
            StrokeThickness="2" RadiusX="10" RadiusY="10" Opacity="0"
            Fill="{StaticResource MyGlassBrushResource}"
            RenderTransformOrigin="0.5,0.5">
            <Rectangle.Stroke>
              <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">
                <LinearGradientBrush.GradientStops>
                  <GradientStop Offset="0.0" Color="LightBlue" />
                  <GradientStop Offset="1.0" Color="Gray" />
                </LinearGradientBrush.GradientStops>
              </LinearGradientBrush>
            </Rectangle.Stroke>

            <!-- These transforms have no effect as they
                 are declared here.
                 The reason the transforms are included is to be targets
                 for animation (see later). -->
            <Rectangle.RenderTransform>
              <TransformGroup>
                <ScaleTransform />
                <RotateTransform />
              </TransformGroup>
            </Rectangle.RenderTransform>

              <!-- A BevelBitmapEffect is applied to give the button a
                   "Beveled" look. -->
            <Rectangle.BitmapEffect>
              <BevelBitmapEffect />
            </Rectangle.BitmapEffect>
          </Rectangle>

          <!-- Present Text of the button. -->
          <DockPanel Name="myContentPresenterDockPanel">
            <ContentPresenter x:Name="myContentPresenter" Margin="20"
              Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />
          </DockPanel>
        </Grid>

        <ControlTemplate.Triggers>       <!-- Set action triggers for the buttons and define            what the button does in response to those triggers. -->     </ControlTemplate.Triggers>
      </ControlTemplate>
    </Setter.Value>
    ```

2. **Přidat aktivační události vlastností:** Přidejte zvýrazněné značky `ControlTemplate.Triggers` do bloku:

    ```xaml
    <ControlTemplate.Triggers>

      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>

    <ControlTemplate.Triggers/>
    ```

     Stisknutím klávesy F5 spusťte aplikaci a uvidíte efekt při spuštění ukazatele myši nad tlačítky.

3. **Přidejte aktivační událost fokusu:** Dále přidáme některé podobné nastavení pro zpracování případu, když má tlačítko fokus (například poté, co na něj uživatel klikne).

    ```xaml
    <ControlTemplate.Triggers>

      <!-- Set properties when mouse pointer is over the button. -->
      <Trigger Property="IsMouseOver" Value="True">

        <!-- Below are three property settings that occur when the
             condition is met (user mouses over button).  -->
        <!-- Change the color of the outer rectangle when user          mouses over it. -->
        <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"
          Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />

        <!-- Sets the glass opacity to 1, therefore, the          glass "appears" when user mouses over it. -->
        <Setter Property="Rectangle.Opacity" Value="1"       TargetName="glassCube" />

        <!-- Makes the text slightly blurry as though you were          looking at it through blurry glass. -->
        <Setter Property="ContentPresenter.BitmapEffect"       TargetName="myContentPresenter">
          <Setter.Value>
            <BlurBitmapEffect Radius="1" />
          </Setter.Value>
        </Setter>
      </Trigger>
      <!-- Set properties when button has focus. -->   <Trigger Property="IsFocused" Value="true">     <Setter Property="Rectangle.Opacity" Value="1"       TargetName="glassCube" />     <Setter Property="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />   </Trigger>

    </ControlTemplate.Triggers>
    ```

     Stisknutím klávesy F5 spusťte aplikaci a klikněte na jedno z tlačítek. Všimněte si, že tlačítko zůstane zvýrazněné po klepnutí na něj, protože má stále fokus. Pokud kliknete na jiné tlačítko, nové tlačítko získá fokus, zatímco poslední ztratí.

4. **Přidat animace pro** <xref:System.Windows.UIElement.MouseEnter> **a** <xref:System.Windows.UIElement.MouseLeave> **:** Dále přidáme některé animace na aktivační události.   Přidejte následující značky kdekoli `ControlTemplate.Triggers` uvnitř bloku.

    ```xaml
    <!-- Animations that start when mouse enters and leaves button. -->
    <EventTrigger RoutedEvent="Mouse.MouseEnter">
      <EventTrigger.Actions>
        <BeginStoryboard Name="mouseEnterBeginStoryboard">
          <Storyboard>
          <!-- This animation makes the glass rectangle shrink in the X direction. -->
            <DoubleAnimation Storyboard.TargetName="glassCube"
              Storyboard.TargetProperty=
              "(Rectangle.RenderTransform).(TransformGroup.Children)[0].(ScaleTransform.ScaleX)"
              By="-0.1" Duration="0:0:0.5" />
            <!-- This animation makes the glass rectangle shrink in the Y direction. -->
            <DoubleAnimation
            Storyboard.TargetName="glassCube"
              Storyboard.TargetProperty=
              "(Rectangle.RenderTransform).(TransformGroup.Children)[0].(ScaleTransform.ScaleY)"
              By="-0.1" Duration="0:0:0.5" />
          </Storyboard>
        </BeginStoryboard>
      </EventTrigger.Actions>
    </EventTrigger>
    <EventTrigger RoutedEvent="Mouse.MouseLeave">
      <EventTrigger.Actions>
        <!-- Stopping the storyboard sets all animated properties back to default. -->
        <StopStoryboard BeginStoryboardName="mouseEnterBeginStoryboard" />
      </EventTrigger.Actions>
    </EventTrigger>
    ```

     Skleněný obdélník se zmenší, když se ukazatel myši přesune nad tlačítko a vrátí se zpět na normální velikost, když ukazatel opustí.

     Existují dvě animace, které se aktivují,<xref:System.Windows.UIElement.MouseEnter> když ukazatel přejde přes tlačítko (událost je aktivována). Tyto animace zmenšit skleněný obdélník podél osy X a Y. Všimněte si <xref:System.Windows.Media.Animation.DoubleAnimation> vlastností <xref:System.Windows.Media.Animation.Timeline.Duration%2A> <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>prvků – a . Určuje, <xref:System.Windows.Media.Animation.Timeline.Duration%2A> že animace dochází více než půl <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> sekundy a určuje, že sklo zmenší o 10 %.

     Druhá aktivační událost<xref:System.Windows.UIElement.MouseLeave>( ) jednoduše zastaví první. Když zastavíte <xref:System.Windows.Media.Animation.Storyboard>, všechny animované vlastnosti se vrátí na své výchozí hodnoty. Proto když uživatel přesune ukazatel mimo tlačítko, tlačítko přejde zpět tak, jak to bylo před ukazatelem myši přesunuta přes tlačítko. Další informace o animacích naleznete v [tématu Přehled animací](../graphics-multimedia/animation-overview.md).

5. **Přidejte animaci po kliknutí na tlačítko:** Posledním krokem je přidání aktivační události pro po klepnutí na tlačítko uživatelem. Přidejte následující značky kdekoli `ControlTemplate.Triggers` uvnitř bloku:

    ```xaml
    <!-- Animation fires when button is clicked, causing glass to spin.  -->
    <EventTrigger RoutedEvent="Button.Click">
      <EventTrigger.Actions>
        <BeginStoryboard>
          <Storyboard>
            <DoubleAnimation Storyboard.TargetName="glassCube"
              Storyboard.TargetProperty=
              "(Rectangle.RenderTransform).(TransformGroup.Children)[1].(RotateTransform.Angle)"
              By="360" Duration="0:0:0.5" />
          </Storyboard>
        </BeginStoryboard>
      </EventTrigger.Actions>
    </EventTrigger>
    ```

     Stisknutím klávesy F5 spusťte aplikaci a klepněte na jedno z tlačítek. Když kliknete na tlačítko, skleněný obdélník se otáčí.

## <a name="summary"></a>Souhrn
 V tomto návodu jste provedli následující cvičení:

- Zacílený a <xref:System.Windows.Style> na<xref:System.Windows.Controls.Button>typ objektu ( ).

- Řízené základní vlastnosti tlačítek v celé <xref:System.Windows.Style>aplikaci pomocí .

- Byly vytvořeny prostředky, jako jsou přechody, které se mají použít pro hodnoty vlastností <xref:System.Windows.Style> nastavení.

- Přizpůsobenvzhled tlačítek v celé aplikaci použitím šablony na tlačítka.

- Přizpůsobené chování tlačítek v reakci na akce <xref:System.Windows.UIElement.MouseEnter> <xref:System.Windows.UIElement.MouseLeave>uživatele <xref:System.Windows.Controls.Primitives.ButtonBase.Click>(například , a ), které zahrnovaly animační efekty.

## <a name="see-also"></a>Viz také

- [Vytvoření tlačítka pomocí nástroje Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Přehled animace](../graphics-multimedia/animation-overview.md)
- [Přehled malování plnými barvami a přechody](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [Přehled efektů bitmap](../graphics-multimedia/bitmap-effects-overview.md)
