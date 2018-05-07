---
title: 'Návod: Vytvoření tlačítka použitím XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
ms.openlocfilehash: 6d41d0894aa85f342deafb77434771b2c89e4150
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a>Návod: Vytvoření tlačítka použitím XAML
Cílem tohoto návodu je informace o vytváření animované tlačítko pro použití v aplikaci Windows Presentation Foundation (WPF). Tento návod používá styly a šablonu pro vytvoření přizpůsobené tlačítko prostředek, který umožňuje opětovné použití kódu a oddělení tlačítko logiku z deklarace tlačítko. Tento názorný postup je zapsán výhradně v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
> [!IMPORTANT]
>  Tento postup vás provede kroky pro vytvoření aplikace zadáním nebo kopírování a vkládání [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do sady Microsoft Visual Studio. Pokud si přejete se dozvíte, jak použít nástroj návrhu (Microsoft Expression Blend) vytvořit stejnou aplikaci, najdete v článku [vytvoření tlačítka společností pomocí Microsoft Expression Blend](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md).  
  
 Následující obrázek znázorňuje tlačítka bylo dokončeno.  
  
 ![Vlastní tlačítka, které se vytvořily s použitím jazyka XAML](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")  
  
## <a name="create-basic-buttons"></a>Vytvořte základní tlačítka  
 Začněme vytvořením nového projektu a přidáním několik tlačítka v okně.  
  
#### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a>Vytvořte nový projekt WPF a přidání tlačítek do okna  
  
1.  Spuštění sady Visual Studio.  
  
2.  **Vytvořte nový projekt WPF:** na **soubor** nabídky, přejděte na příkaz **nový**a potom klikněte na **projektu**. Najít **aplikace WPF (Windows)** šablony a názvu projektu "AnimatedButton". Tím se vytvoří kostru aplikace.  
  
3.  **Přidat základní výchozích tlačítek:** všechny soubory potřebné pro tento návod jsou poskytovány šablony. Dvojím kliknutím na tlačítko v Průzkumníku řešení otevřete soubor Window1.xaml. Ve výchozím nastavení, je <xref:System.Windows.Controls.Grid> element v Window1.xaml. Odeberte <xref:System.Windows.Controls.Grid> elementu a přidejte několik tlačítek [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] stránky zadáním nebo kopírování a vkládání následující zvýrazněný kód do Window1.xaml:  
  
    ```xaml  
    <Window x:Class="AnimatedButton.Window1"  
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
      Title="AnimatedButton" Height="300" Width="300"   
      Background="Black">   <!-- Buttons arranged vertically inside a StackPanel. -->   <StackPanel HorizontalAlignment="Left">     <Button>Button 1</Button>     <Button>Button 2</Button>     <Button>Button 3</Button>   </StackPanel>  
  
    </Window>  
    ```  
  
     Stisknutím klávesy F5 spusťte aplikaci; měli byste vidět sadu tlačítek, který vypadá jako na následujícím obrázku.  
  
     ![Tři základní tlačítka](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")  
  
     Teď, když jste vytvořili základní tlačítek, budete mít v souboru Window1.xaml funguje. Zbývající návodu se zaměřuje na soubor app.xaml definování styly a šablonu pro tlačítka.  
  
## <a name="set-basic-properties"></a>Nastavit základní vlastnosti  
 Dále umožňuje nastavit některé vlastnosti na tato tlačítka řídit vzhled tlačítka a rozložení. Místo jednotlivě nastavit vlastnosti tlačítka, bude používat prostředky k definování vlastnosti tlačítka pro celou aplikaci. Prostředky aplikace se koncepčně podobá externí [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)] pro webové stránky; ale prostředky jsou mnohem silnější než [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)], jak se zobrazí na konci tohoto průvodce. Další informace o prostředcích, najdete v části [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
#### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a>Nastavení základní vlastnosti tlačítek pomocí styly  
  
1.  **Definování bloku Application.Resources:** otevřete app.xaml a přidejte následující zvýrazněný kód, pokud ještě není:  
  
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
  
     Obor prostředků je určen podle kde definici zdroje. Definování prostředky v `Application.Resources` v app.xaml umožňuje soubor prostředků pro použití v libovolné místo v aplikaci. Další informace o definování oboru vašich prostředků najdete v tématu [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
2.  **Vytvořit styl a definovat hodnoty vlastnosti základní s ním:** přidejte následující kód do `Application.Resources` bloku. Tento kód vytvoří <xref:System.Windows.Style> , platí pro všechny tlačítka v nastavení aplikace <xref:System.Windows.FrameworkElement.Width%2A> tlačítek a 90 a <xref:System.Windows.FrameworkElement.Margin%2A> 10:  
  
    ```xaml  
    <Application.Resources>  
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>  
    </Application.Resources>  
    ```  
  
     <xref:System.Windows.Style.TargetType%2A> Vlastnost určuje, že styl platí pro všechny objekty typu <xref:System.Windows.Controls.Button>. Každý <xref:System.Windows.Setter> hodnotu jinou vlastnost nastaví <xref:System.Windows.Style>. Proto v tomto okamžiku každé tlačítko v aplikaci má šířku 90 a okraji 10.  Pokud stisknete klávesu F5 a spusťte aplikaci, najdete v následujícím okně.  
  
     ![Tlačítka s šířkou 90 a okraji 10](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")  
  
     Je mnohem víc, že můžete provést se styly, včetně různými způsoby a systém doladit, jaké objekty jsou cíleny zadání hodnoty komplexní vlastností a i pomocí styly jako vstup pro jiné styly. Další informace najdete v tématu [stylů a ukázka](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
3.  **Nastavení hodnoty vlastnosti stylu na prostředek:** prostředky povolit jednoduchý způsob, jak znovu použít běžně definované objekty a hodnoty. Je obzvláště užitečná k definování komplexní hodnoty používání prostředků, aby váš kód více modulární. Přidejte následující zvýrazněný kód do app.xaml.  
  
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
  
     Přímo pod `Application.Resources` bloku vytvoříte prostředek s názvem "GrayBlueGradientBrush". Tento prostředek definuje vodorovný přechod. Tento prostředek lze použít jako hodnotu vlastnosti z libovolného místa v aplikaci, včetně uvnitř nastavovací metoda styl tlačítko <xref:System.Windows.Controls.Control.Background%2A> vlastnost. Nyní máte všechny tlačítka <xref:System.Windows.Controls.Control.Background%2A> hodnota vlastnosti této přechodu.  
  
     Stisknutím klávesy F5 spusťte aplikaci. By měl vypadat jako následující.  
  
     ![Tlačítka s barevného přechodu pozadí](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")  
  
## <a name="create-a-template-that-defines-the-look-of-the-button"></a>Vytvořit šablonu, která definuje vzhled tlačítka  
 V této části vytvoříte šablonu, která se přizpůsobí vzhled tlačítka (prezentace). Tlačítko prezentace se skládá z několika objektů včetně obdélníků a další součásti chcete jedinečný vzhled tlačítka.  
  
 Zatím řízení vzhled tlačítka v aplikaci má byla omezena změna vlastností tlačítka. Co dělat, pokud chcete více znak změnit vzhled tlačítka? Šablony umožňují efektivní kontrolu nad prezentace objektu. Protože šablony lze používat v rámci styly, můžete použít šablonu pro všechny objekty, které se vztahuje styl (v tomto návodu tlačítko).  
  
#### <a name="to-use-the-template-to-define-the-look-of-the-button"></a>Abyste mohli použít šablonu definovat vzhled tlačítka  
  
1.  **Nastavení šablony:** protože ovládací prvky, jako <xref:System.Windows.Controls.Button> mít <xref:System.Windows.Controls.Control.Template%2A> vlastnost, můžete definovat hodnoty vlastnosti šablony stejně jako hodnoty vlastností jsme ve nastavili <xref:System.Windows.Style> pomocí <xref:System.Windows.Setter>. Přidejte následující zvýrazněný kód do vaší stylů tlačítek.  
  
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
  
2.  **Příkaz ALTER tlačítko prezentace:** v tomto okamžiku je nutné definovat šablony. Přidejte následující zvýrazněný kód. Tento kód určuje dva <xref:System.Windows.Shapes.Rectangle> prvky s zaoblenými hranami, za nímž následuje <xref:System.Windows.Controls.DockPanel>. <xref:System.Windows.Controls.DockPanel> Se používá k hostiteli <xref:System.Windows.Controls.ContentPresenter> tlačítka. A <xref:System.Windows.Controls.ContentPresenter> zobrazuje obsah tlačítka. V tomto návodu je obsah text ("Tlačítko 1", "Tlačítko 2", "Tlačítko 3"). Všechny součásti šablony (obdélníků a <xref:System.Windows.Controls.DockPanel>) jsou nastíněny uvnitř <xref:System.Windows.Controls.Grid>.  
  
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
  
     Stisknutím klávesy F5 spusťte aplikaci. By měl vypadat jako následující.  
  
     ![](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-4.gif "custom_button_AnimatedButton_4")  
  
3.  **Přidání do šablony glasseffect:** dále přidáte skla. Nejdřív vytvoříte některé prostředky, které vytvářejí skleněný efekt barevného přechodu. Přidat tyto přechodu prostředky kdekoli v rámci `Application.Resources` bloku:  
  
    ```xaml  
    <Application.Resources>  
      <GradientStopCollection x:Key="MyGlassGradientStopsResource">     <GradientStop Color="WhiteSmoke" Offset="0.2" />     <GradientStop Color="Transparent" Offset="0.4" />     <GradientStop Color="WhiteSmoke" Offset="0.5" />     <GradientStop Color="Transparent" Offset="0.75" />     <GradientStop Color="WhiteSmoke" Offset="0.9" />     <GradientStop Color="Transparent" Offset="1" />   </GradientStopCollection>   <LinearGradientBrush x:Key="MyGlassBrushResource"     StartPoint="0,0" EndPoint="1,1" Opacity="0.75"     GradientStops="{StaticResource MyGlassGradientStopsResource}" />  
    <!-- Styles and other resources below here. -->  
    ```  
  
     Tyto prostředky jsou použity jako <xref:System.Windows.Shapes.Shape.Fill%2A> pro obdélníku, který jsme vložit do <xref:System.Windows.Controls.Grid> tlačítko šablony. Přidejte následující zvýrazněný kód do šablony.  
  
    ```  
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
  
        <!-- Glass Rectangle -->     <Rectangle x:Name="glassCube" HorizontalAlignment="Stretch"       VerticalAlignment="Stretch"       StrokeThickness="2" RadiusX="10" RadiusY="10" Opacity="0"       Fill="{StaticResource MyGlassBrushResource}"       RenderTransformOrigin="0.5,0.5">       <Rectangle.Stroke>         <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">           <LinearGradientBrush.GradientStops>             <GradientStop Offset="0.0" Color="LightBlue" />             <GradientStop Offset="1.0" Color="Gray" />           </LinearGradientBrush.GradientStops>         </LinearGradientBrush>       </Rectangle.Stroke>       <!-- These transforms have no effect as they are declared here.             The reason the transforms are included is to be targets             for animation (see later). -->       <Rectangle.RenderTransform>         <TransformGroup>           <ScaleTransform />           <RotateTransform />         </TransformGroup>       </Rectangle.RenderTransform>       <!-- A BevelBitmapEffect is applied to give the button a             "Beveled" look. -->       <Rectangle.BitmapEffect>         <BevelBitmapEffect />       </Rectangle.BitmapEffect>     </Rectangle>  
  
        <!-- Present Text of the button. -->  
        <DockPanel Name="myContentPresenterDockPanel">  
          <ContentPresenter x:Name="myContentPresenter" Margin="20"   
            Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />  
        </DockPanel>  
      </Grid>  
    </ControlTemplate>  
    </Setter.Value>  
    ```  
  
     Všimněte si, že <xref:System.Windows.UIElement.Opacity%2A> obdélníku s `x:Name` vlastnost "glassCube" je 0, tak při spuštění vzorového nevidíte pohotovostní rámeček jako překryvný obrázek nahoře. Je to proto, že později přidáme aktivační události do šablony pro tehdy, když uživatel pracuje s tlačítko. Ale uvidíte, jak tlačítko vypadá teď změnou <xref:System.Windows.UIElement.Opacity%2A> hodnotu na 1 a spuštění aplikace. Prohlédněte si následující obrázek. Než budete pokračovat k dalšímu kroku, změnit <xref:System.Windows.UIElement.Opacity%2A> zpět na hodnotu 0.  
  
     ![Vlastní tlačítka, které se vytvořily s použitím jazyka XAML](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")  
  
## <a name="create-button-interactivity"></a>Vytvoření interaktivity tlačítko  
 V této části vytvoříte vlastnost triggerů a aktivačních událostí změně hodnot vlastností a spuštění animace v odpovědi na akce uživatele, například ukazatele myši nad tlačítko a kliknutím na tlačítko.  
  
 Zadejte aktivační události v rámci šablony nebo styl je snadný způsob, jak přidat interaktivity (myší nad, ponechejte myši, klikněte na tlačítko a tak dále). K vytvoření <xref:System.Windows.Trigger>, například definovat vlastnost "podmínky": tlačítko <xref:System.Windows.UIElement.IsMouseOver%2A> vlastnost hodnota se rovná `true`. Potom můžete definovat setter (akce), kterým dochází, když je splněna podmínka aktivace.  
  
#### <a name="to-create-button-interactivity"></a>Chcete-li vytvořit interaktivity tlačítko  
  
1.  **Přidat šablonu aktivační události:** do šablony přidat zvýrazněný kód.  
  
    ```  
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
  
2.  **Přidat vlastnost aktivační události:** přidat zvýrazněná značky k `ControlTemplate.Triggers` bloku:  
  
    ```  
    <ControlTemplate.Triggers>  
  
      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>  
  
    <ControlTemplate.Triggers/>  
    ```  
  
     Stisknutím klávesy F5 spusťte aplikaci a projevily po spuštění ukazatel myši nad tlačítka.  
  
3.  **Přidat aktivační událost fokus:** potom přidáme některé podobné setter zpracování případě, pokud má právě fokus (například po klepnutí se), na tlačítko.  
  
    ```  
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
  
     Stisknutím klávesy F5 spusťte aplikaci a klikněte na jednu z tlačítka. Všimněte si, že zůstane tlačítko zvýrazněná po kliknutí na tlačítko ji vzhledem k tomu, že je stále fokus. Pokud klepnete na tlačítko Další, nové tlačítko získá fokus při poslední ztratí ho.  
  
4.  **Přidání animace pro** <xref:System.Windows.UIElement.MouseEnter> **a** <xref:System.Windows.UIElement.MouseLeave> **:** další přidáme některé animací aktivačních událostí. Přidejte následující kód kdekoli v z `ControlTemplate.Triggers` bloku.  
  
    ```  
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
  
     Rámeček pohotovostní zmenší při ukazatel myši přesune na tlačítko a vrátí zpět na normální velikost, když ukazatel opustí.  
  
     Existují dvě animace, které jsou aktivované, když ukazatel prochází přes tlačítko (<xref:System.Windows.UIElement.MouseEnter> událost se vyvolá,). Tyto animací zmenšit rámeček pohotovostní podél osy X a Y. Všimněte si vlastnosti na <xref:System.Windows.Media.Animation.DoubleAnimation> elementy – <xref:System.Windows.Media.Animation.Timeline.Duration%2A> a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>. <xref:System.Windows.Media.Animation.Timeline.Duration%2A> Určuje, že animace dochází k více než půl sekundy, a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> Určuje, že skla zmenšuje 10 %.  
  
     Druhý aktivační události (<xref:System.Windows.UIElement.MouseLeave>) jednoduše zastaví první z nich. Při zastavení <xref:System.Windows.Media.Animation.Storyboard>, všechny animovaný vlastnosti vrátit na výchozí hodnoty. Proto pokud se uživatel přesune ukazatel mimo tlačítko, tlačítko přejde zpět způsob, jakým byl před přesunutí ukazatele myši nad tlačítko. Další informace o animací najdete v tématu [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
5.  **Přidání animace pro při kliknutí na tlačítko:** posledním krokem je aktivační událost pro když uživatel klikne na tlačítko Přidat. Přidejte následující kód kdekoli v z `ControlTemplate.Triggers` bloku:  
  
    ```  
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
  
     Stisknutím klávesy F5 spusťte aplikaci a klikněte na jednu z tlačítka. Po kliknutí tlačítko, rámeček pohotovostní otáčí kolem.  
  
## <a name="summary"></a>Souhrn  
 V tomto návodu jste provedli následující cvičení:  
  
-   Cílem <xref:System.Windows.Style> na typ objektu (<xref:System.Windows.Controls.Button>).  
  
-   Řídí základní vlastnosti tlačítek v celé aplikace pomocí <xref:System.Windows.Style>.  
  
-   Vytvořit prostředky jako přechody pro hodnot vlastností <xref:System.Windows.Style> setter.  
  
-   Použití šablony na tlačítka přizpůsobit vzhled tlačítek v celé aplikaci.  
  
-   Přizpůsobit chování pro tlačítka v odpovědi na akce uživatele (například <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>, a <xref:System.Windows.Controls.Primitives.ButtonBase.Click>), které zahrnuty efekty animace.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření tlačítka pomocí nástroje Microsoft Expression Blend](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md)  
 [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Přehled malování plnými barvami a přechody](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Přehled efektů bitmap](../../../../docs/framework/wpf/graphics-multimedia/bitmap-effects-overview.md)
