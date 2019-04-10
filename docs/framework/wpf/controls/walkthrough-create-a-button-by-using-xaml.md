---
title: 'Návod: Vytvoření tlačítka pomocí XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
ms.openlocfilehash: 908a38485c879e3f28399bb7dbc8303afd4505da
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59309495"
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a>Návod: Vytvoření tlačítka pomocí XAML
Cílem tohoto návodu je zjistěte, jak vytvořit animovaná tlačítka pro použití v aplikaci Windows Presentation Foundation (WPF). Tento návod používá – styly a šablony vytvořit tlačítko vlastní prostředek, umožňující opětovné použití kódu a oddělení logiky tlačítko od deklarace tlačítko. Tento návod byl napsán výhradně v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
> [!IMPORTANT]
>  Tento názorný postup vás provede kroky pro vytváření aplikace psát nebo zkopírováním a vložením [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do sady Microsoft Visual Studio. Pokud chcete další informace o použití návrhářský nástroj (Microsoft Expression Blend) Chcete-li vytvořit stejnou aplikaci, najdete v článku [vytvoření tlačítka pomocí pomocí Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).  
  
 Následující obrázek ukazuje dokončení tlačítka.  
  
 ![Vlastní tlačítka, které se vytvořily pomocí XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")  
  
## <a name="create-basic-buttons"></a>Vytvoření základní tlačítka  
 Začněme vytvořením nového projektu a přidává několik tlačítek do okna.  
  
#### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a>Přidání tlačítek do okna a vytvořte nový projekt WPF  
  
1. Spusťte Visual Studio.  
  
2. **Vytvořte nový projekt WPF:** Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**. Najít **aplikace Windows (WPF)** šablony a názvu projektu "AnimatedButton". Tím se vytvoří kostru pro aplikaci.  
  
3. **Přidáte výchozí základní tlačítka:** Všechny soubory, které potřebujete pro Tento názorný postup jsou k dispozici šablonou. Otevřete soubor Window1.xaml dvojitým kliknutím v Průzkumníku řešení. Ve výchozím nastavení, je <xref:System.Windows.Controls.Grid> prvek Window1.xaml. Odeberte <xref:System.Windows.Controls.Grid> elementu a přidejte několik tlačítek na hodnotu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] stránky zadáním nebo kopírování a vkládání následující zvýrazněný kód do Window1.xaml:  
  
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
  
     Teď, když jste vytvořili základní tlačítka, jste dokončili práci v souboru Window1.xaml. Zbytek tohoto průvodce se zaměřuje na soubor app.xaml definování – styly a šablony tlačítek.  
  
## <a name="set-basic-properties"></a>Nastavte základní vlastnosti  
 V dalším kroku nastavíme některé vlastnosti na tato tlačítka řídit vzhled tlačítka a rozložení. Namísto nastavení vlastností tlačítka jednotlivě, budete používat prostředky k definování vlastností tlačítka pro celou aplikaci. Prostředky aplikace jsou koncepčně podobné pro externí [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)] pro webové stránky; prostředky jsou však mnohem výkonnější než [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)], jak se zobrazí na konci tohoto návodu. Další informace o prostředcích najdete v tématu [prostředky XAML](../advanced/xaml-resources.md).  
  
#### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a>Použití stylů můžete nastavit základní vlastnosti tlačítka  
  
1. **Definování blok Application.Resources:** Otevření souboru app.xaml a pokud už tam není, přidejte následující zvýrazněný kód:  
  
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
  
     Tady můžete definovat prostředek Určuje prostředek oboru. Definování prostředků v `Application.Resources` v souboru app.xaml umožňuje soubor prostředků pro použití v kdekoli v aplikaci. Další informace o definování oboru prostředků najdete v tématu [prostředky XAML](../advanced/xaml-resources.md).  
  
2. **Vytvoření stylu a definovat hodnoty základní vlastnosti s ní:** Přidejte následující kód k `Application.Resources` bloku. Tento kód vytvoří <xref:System.Windows.Style> , která se vztahuje na všechna tlačítka v nastavení aplikace <xref:System.Windows.FrameworkElement.Width%2A> tlačítek na hodnotu 90 a <xref:System.Windows.FrameworkElement.Margin%2A> 10:  
  
    ```xaml  
    <Application.Resources>  
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>  
    </Application.Resources>  
    ```  
  
     <xref:System.Windows.Style.TargetType%2A> Vlastnost určuje, že styl platí pro všechny objekty typu <xref:System.Windows.Controls.Button>. Každý <xref:System.Windows.Setter> nastaví hodnotu jinou vlastnost <xref:System.Windows.Style>. Proto v tuto chvíli každé tlačítko v aplikaci má šířku 90 a okraj 10.  Pokud stisknete klávesu F5 ke spuštění aplikace, zobrazí následující okno.  
  
     ![Tlačítka s šířkou 90 a okraj 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")  
  
     Je mnohem více že můžete provést se styly, včetně celou řadu způsobů, jak doladit, jaké objekty jsou cíleny, zadáte hodnoty komplexní vlastnost a dokonce i pomocí stylů jako vstup pro jiné styly. Další informace najdete v tématu [styly a šablony](styling-and-templating.md).  
  
3. **Nastavte hodnotu vlastnosti stylu na prostředek:** Prostředky povolit jednoduchý způsob, jak opětovné použití obecně definovaných objektů a hodnoty. To je užitečné zejména pro definování komplexních hodnot. aby byl kód modulárnější použití prostředků. Přidejte následující zvýrazněný kód do souboru app.xaml.  
  
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
  
     Přímo pod `Application.Resources` bloku, vytvoříte prostředek s názvem "GrayBlueGradientBrush". Tento prostředek definuje vodorovný přechod. Tento prostředek může sloužit jako hodnotu vlastnosti z libovolného místa v aplikaci, včetně v style setter tlačítko pro <xref:System.Windows.Controls.Control.Background%2A> vlastnost. Teď k dispozici všechna tlačítka <xref:System.Windows.Controls.Control.Background%2A> hodnota vlastnosti tohoto přechodu.  
  
     Stisknutím klávesy F5 spusťte aplikaci. By měl vypadat nějak takto.  
  
     ![Tlačítka s barevného přechodu pozadí](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")  
  
## <a name="create-a-template-that-defines-the-look-of-the-button"></a>Vytvořit šablonu, která definuje vzhled tlačítka  
 V této části vytvoříte šablonu, která se přizpůsobí vzhled tlačítka (prezentace). Prezentace tlačítko se skládá z několika objektů včetně obdélníků a další součásti jedinečný vzhled na tlačítko.  
  
 Zatím kontrolou vzhled tlačítek v aplikaci má byla omezena změna vlastností tlačítka. Co když chcete provést radikálnější změně vzhled tlačítka? Šablony povolit výkonná kontrolu nad prezentaci objektu. Vzhledem k tomu, že šablony lze používat v rámci stylů, můžete použít šablonu pro všechny objekty, které styl platí (v tomto návodu tlačítka).  
  
#### <a name="to-use-the-template-to-define-the-look-of-the-button"></a>Použití šablony k definování vzhledu tlačítka  
  
1. **Nastavení šablony:** Vzhledem k tomu, že ovládací prvky jako <xref:System.Windows.Controls.Button> mít <xref:System.Windows.Controls.Control.Template%2A> vlastností, můžete definovat hodnotu vlastnosti šablony, stejně jako jiné hodnoty vlastností jsme nastavili v <xref:System.Windows.Style> pomocí <xref:System.Windows.Setter>. Přidejte následující zvýrazněný kód do vašeho styl tlačítka.  
  
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
  
2. **Příkaz ALTER prezentace tlačítka:** V tomto okamžiku budete muset definovat šablony. Přidejte následující zvýrazněný kód. Tento kód určuje dvě <xref:System.Windows.Shapes.Rectangle> prvky s zaoblenými hranami, za nímž následuje <xref:System.Windows.Controls.DockPanel>. <xref:System.Windows.Controls.DockPanel> Slouží k hostiteli <xref:System.Windows.Controls.ContentPresenter> tlačítka. A <xref:System.Windows.Controls.ContentPresenter> zobrazí obsah tlačítka. V tomto názorném postupu obsahu je text ("Tlačítko 1", "Tlačítko 2", "Tlačítko 3"). Všechny součásti šablony (obdélníků a <xref:System.Windows.Controls.DockPanel>) jsou rozloženy uvnitř <xref:System.Windows.Controls.Grid>.  
  
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
  
     Stisknutím klávesy F5 spusťte aplikaci. By měl vypadat nějak takto.  
  
     ![](./media/custom-button-animatedbutton-4.gif "custom_button_AnimatedButton_4")  
  
3. **Přidejte glasseffect do šablony:** Dále přidáte skla. Nejprve vytvoříte některé prostředky, které vytvoření efektu přechodu skla. Přidat tyto přechodu prostředky kdekoli v rámci `Application.Resources` blok:  
  
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
  
     Tyto prostředky se používají jako <xref:System.Windows.Shapes.Shape.Fill%2A> obdélníku, který jsme použít příkaz insert <xref:System.Windows.Controls.Grid> šablony tlačítka. Přidejte následující zvýrazněný kód do šablony.  
  
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
  
     Všimněte si, že <xref:System.Windows.UIElement.Opacity%2A> obdélníku s `x:Name` vlastnost "glassCube" je 0, takže při spuštění ukázky, se nezobrazí jako překryvný obrázek na horní části obdélníku lupy. Je to proto, že později přidáme aktivační procedury do šablon pro při interakci uživatele pomocí tlačítka. Však můžete zobrazit tlačítko vypadá nyní tak, že změníte <xref:System.Windows.UIElement.Opacity%2A> hodnotu 1 a spuštění aplikace. Prohlédněte si následující obrázek. Než budete pokračovat k dalšímu kroku, změnit <xref:System.Windows.UIElement.Opacity%2A> zpět na hodnotu 0.  
  
     ![Vlastní tlačítka, které se vytvořily pomocí XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")  
  
## <a name="create-button-interactivity"></a>Vytvářet tlačítka interakce  
 V této části vytvoříte aktivační procedury vlastností a aktivační události změnit hodnoty vlastností a spuštění animace v reakci na akce uživatelů, například ukazatele myši nad tlačítkem a kliknutím na.  
  
 Snadný způsob, jak přidat interaktivitu (myší nad, myši ponechat, klikněte na tlačítko a tak dále) je k definování triggerů v šabloně nebo stylu. Chcete-li vytvořit <xref:System.Windows.Trigger>, jako například definovat vlastnost "podmínku": Tlačítko <xref:System.Windows.UIElement.IsMouseOver%2A> hodnota vlastnosti je rovna `true`. Potom definujte metody setter (akce), které se použijí při aktivační podmínka pravdivá.  
  
#### <a name="to-create-button-interactivity"></a>Chcete-li vytvořit tlačítko interaktivitu  
  
1. **Přidání aktivačních událostí šablony:** Zvýrazněná značka se přidáte do šablony.  
  
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
  
2. **Přidáte aktivační procedury vlastností:** Přidat zvýrazněné značky `ControlTemplate.Triggers` blok:  
  
    ```xaml
    <ControlTemplate.Triggers>  
  
      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>  
  
    <ControlTemplate.Triggers/>  
    ```  
  
     Stisknutím klávesy F5 spusťte aplikaci a vidět její účinek spuštění ukazatele myši nad tlačítka.  
  
3. **Přidání triggeru fokus:** V dalším kroku přidáme několik podobné metody setter pro zpracování případu, když je fokus na tlačítko (například po na něj uživatel klikne).  
  
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
  
     Stisknutím klávesy F5 spusťte aplikaci a klikněte na jedno z tlačítek. Všimněte si, že zůstane po kliknutí na jeho protože stále má fokus zvýrazněné tlačítko. Pokud klepnete na tlačítko Další, nové tlačítko získá fokus, zatímco poslední z nich se ztratí.  
  
4. **Přidání animace k** <xref:System.Windows.UIElement.MouseEnter> **a** <xref:System.Windows.UIElement.MouseLeave> **:** Vedle přidáme některé animace aktivačních událostí. Přidejte následující kód, kdekoli uvnitř sady `ControlTemplate.Triggers` bloku.  
  
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
  
     Obdélník lupy se zmenší, pokud ukazatel myši přesune na tlačítko a vrátí zpět na normální velikosti, když ukazatel opustí.  
  
     Existují dva animace, které se zobrazí, když ukazatel myši překročí tlačítka (<xref:System.Windows.UIElement.MouseEnter> událost je aktivována). Tyto animace budete zmenšit skla obdélník na ose X a Y. Všimněte si, že vlastnosti na <xref:System.Windows.Media.Animation.DoubleAnimation> prvky – <xref:System.Windows.Media.Animation.Timeline.Duration%2A> a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>. <xref:System.Windows.Media.Animation.Timeline.Duration%2A> Určuje, zda animace vyskytuje více než půl sekundy, a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> Určuje, že zmenšuje skla 10 %.  
  
     Druhý aktivační procedura událostí (<xref:System.Windows.UIElement.MouseLeave>) jednoduše zastaví první z nich. Při zastavení <xref:System.Windows.Media.Animation.Storyboard>, animované vlastnosti vrátit na výchozí hodnoty. Proto když uživatel přesune ukazatel mimo tlačítko, na tlačítko se vrátí způsobu, jakým byl před přesunutím ukazatele myši nad tlačítkem. Další informace o animacích naleznete v tématu [přehled animace](../graphics-multimedia/animation-overview.md).  
  
5. **Přidání animace k po kliknutí na tlačítko:** Posledním krokem je přidání triggeru pro, když uživatel klikne na tlačítko. Přidejte následující kód, kdekoli uvnitř sady `ControlTemplate.Triggers` blok:  
  
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
  
     Stisknutím klávesy F5 spusťte aplikaci a klikněte na jedno z tlačítek. Po kliknutí na tlačítko lupy obdélník přede kolem.  
  
## <a name="summary"></a>Souhrn  
 V tomto návodu jste provedli následující praktická cvičení:  
  
-   Cílené <xref:System.Windows.Style> s typem objektu (<xref:System.Windows.Controls.Button>).  
  
-   Řídí základní vlastnosti v celé aplikaci pomocí tlačítek <xref:System.Windows.Style>.  
  
-   Vytvoření zdroje, jako jsou přechody pro hodnoty vlastností <xref:System.Windows.Style> funkce setter.  
  
-   Použití šablony tlačítka Upravit vzhled tlačítka v celé aplikaci.  
  
-   Přizpůsobit chování pro tlačítka v reakci na akce uživatele (například <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>, a <xref:System.Windows.Controls.Primitives.ButtonBase.Click>), které obsahovat efekty animace.  
  
## <a name="see-also"></a>Viz také:

- [Vytvoření tlačítka pomocí nástroje Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)
- [Styly a šablony](styling-and-templating.md)
- [Přehled animace](../graphics-multimedia/animation-overview.md)
- [Přehled malování plnými barvami a přechody](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [Přehled efektů bitmap](../graphics-multimedia/bitmap-effects-overview.md)
