---
title: 'Návod: Vytvoření tlačítka pomocí XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
ms.openlocfilehash: 2dfa70515fb257740015e4d6d75ef9d8a6007006
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512816"
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a>Návod: Vytvoření tlačítka pomocí XAML
Cílem tohoto návodu je zjistit, jak vytvořit animované tlačítko pro použití v aplikaci Windows Presentation Foundation (WPF). Tento návod používá styly a šablonu k vytvoření vlastního prostředku tlačítka, který umožňuje opakované použití kódu a oddělení logiky tlačítek z deklarace tlačítka. Tento návod se zapisuje výhradně [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]v.  
  
> [!IMPORTANT]
>  Tento návod vás provede kroky pro vytvoření aplikace zadáním nebo zkopírováním a vložením [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do Microsoft Visual Studio. Pokud se chcete dozvědět, jak pomocí nástroje pro návrh (Microsoft Expression Blend) vytvořit stejnou aplikaci, přečtěte si téma [Vytvoření tlačítka pomocí sady Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).  
  
 Následující obrázek ukazuje tlačítka dokončená.  
  
 ![Vlastní tlačítka, která byla vytvořena pomocí jazyka XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")  
  
## <a name="create-basic-buttons"></a>Vytvoření základních tlačítek  
 Pojďme začít vytvořením nového projektu a přidáním několika tlačítek do okna.  
  
#### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a>Vytvoření nového projektu WPF a přidání tlačítek do okna  
  
1. Spusťte Visual Studio.  
  
2. **Vytvořit nový projekt WPF:** V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**. Vyhledejte šablonu **aplikace systému Windows (WPF)** a pojmenujte projekt "AnimatedButton". Tím se vytvoří kostra aplikace.  
  
3. **Přidat základní výchozí tlačítka:** Všechny soubory, které potřebujete pro tento návod, poskytuje šablona. Otevřete soubor Window1. XAML dvojitým kliknutím na něj v Průzkumník řešení. Ve výchozím nastavení je <xref:System.Windows.Controls.Grid> v souboru Window1. XAML prvek. Odeberte prvek a přidejte na [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] stránku několik tlačítek, a to tak, že do souboru Window1. XAML zadáte nebo zkopírujete a vložíte následující zvýrazněný kód: <xref:System.Windows.Controls.Grid>  
  
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
  
     Stisknutím klávesy F5 spusťte aplikaci. měla by se zobrazit sada tlačítek, která vypadají jako na následujícím obrázku.  
  
     ![Tři základní tlačítka](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")  
  
     Nyní, když jste vytvořili základní tlačítka, jste dokončili práci v souboru Window1. XAML. Zbytek návodu se zaměřuje na soubor App. XAML, který definuje styly a šablonu pro tlačítka.  
  
## <a name="set-basic-properties"></a>Nastavit základní vlastnosti  
 Nyní na těchto tlačítkách nastavíme některé vlastnosti, které řídí vzhled a rozložení tlačítka. Místo toho, abyste nastavovat vlastnosti u tlačítek samostatně, budete používat prostředky k definování vlastností tlačítek pro celou aplikaci. Prostředky aplikace jsou koncepčně podobné externím šablony stylů CSS (CSS) pro webové stránky; prostředky jsou ale mnohem výkonnější než šablony stylů CSS (CSS), jak vidíte na konci tohoto návodu. Další informace o prostředcích najdete v tématu [prostředky XAML](../advanced/xaml-resources.md).  
  
#### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a>Použití stylů k nastavení základních vlastností tlačítek  
  
1. **Definujte blok Application. Resources:** Otevřete App. XAML a přidejte následující zvýrazněný kód, pokud tam ještě není:  
  
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
  
     Rozsah prostředku určuje, kde můžete prostředek definovat. Definování prostředků v `Application.Resources` souboru App. XAML umožňuje použít prostředek z libovolného místa v aplikaci. Další informace o definování rozsahu vašich prostředků najdete v tématu věnovaném [prostředkům XAML](../advanced/xaml-resources.md).  
  
2. **Vytvořte styl a definujte pro něj základní hodnoty vlastností:** Do `Application.Resources` bloku přidejte následující kód. Tento kód vytvoří <xref:System.Windows.Style> , který se vztahuje na všechna tlačítka v aplikaci, <xref:System.Windows.FrameworkElement.Width%2A> nastavení <xref:System.Windows.FrameworkElement.Margin%2A> tlačítek na 90 a na 10:  
  
    ```xaml  
    <Application.Resources>  
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>  
    </Application.Resources>  
    ```  
  
     Vlastnost určuje, že styl platí pro všechny objekty typu <xref:System.Windows.Controls.Button>. <xref:System.Windows.Style.TargetType%2A> Každý <xref:System.Windows.Setter> nastaví jinou hodnotu vlastnosti <xref:System.Windows.Style>pro. Proto v tomto okamžiku každé tlačítko v aplikaci má šířku 90 a okraj 10.  Pokud stisknete klávesu F5 ke spuštění aplikace, zobrazí se následující okno.  
  
     ![Tlačítka s šířkou 90 a okrajem 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")  
  
     K dispozici je mnohem více, co můžete dělat se styly, včetně nejrůznějších způsobů, jak vyladit objekty, které jsou cílené, určením složitých hodnot vlastností a dokonce i pomocí stylů jako vstup pro jiné styly. Další informace najdete v tématu [stylování a šablonování](styling-and-templating.md).  
  
3. **Nastavte hodnotu vlastnosti Style na prostředek:** Prostředky umožňují jednoduchý způsob opakovaného použití běžně definovaných objektů a hodnot. To je užitečné hlavně při definování složitých hodnot pomocí prostředků, aby se váš kód podrobněji vytvářely. Přidejte do souboru App. XAML následující zvýrazněný kód.  
  
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
  
     Přímo pod `Application.Resources` blokem jste vytvořili prostředek s názvem "GrayBlueGradientBrush". Tento prostředek definuje Vodorovný přechod. Tento prostředek lze použít jako hodnotu vlastnosti z libovolného místa v aplikaci, včetně nastavení stylu tlačítka pro <xref:System.Windows.Controls.Control.Background%2A> vlastnost. Nyní všechna tlačítka mají <xref:System.Windows.Controls.Control.Background%2A> hodnotu vlastnosti tohoto přechodu.  
  
     Stisknutím klávesy F5 spusťte aplikaci. Měl by vypadat nějak takto.  
  
     ![Tlačítka s pozadím přechodu](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")  
  
## <a name="create-a-template-that-defines-the-look-of-the-button"></a>Vytvoření šablony definující vzhled tlačítka  
 V této části vytvoříte šablonu, která přizpůsobí vzhled tlačítka (prezentace). Prezentace tlačítek se skládá z několika objektů, včetně obdélníků a dalších komponent, které tlačítku podávají jedinečný vzhled.  
  
 V tuto dobu byl ovládací prvek toho, jak se tlačítka vypadají v aplikaci, omezen na změnu vlastností tlačítka. Co dělat v případě, že chcete další odmocniny změn v zobrazení tlačítka? Šablony umožňují výkonnou kontrolu nad prezentací objektu. Vzhledem k tomu, že šablony lze použít v rámci stylů, můžete použít šablonu na všechny objekty, na které se vztahuje styl (v tomto návodu tlačítko).  
  
#### <a name="to-use-the-template-to-define-the-look-of-the-button"></a>Chcete-li použít šablonu k definování vzhledu tlačítka  
  
1. **Nastavte šablonu:** Vzhledem k tomu <xref:System.Windows.Controls.Button> , že <xref:System.Windows.Controls.Control.Template%2A> ovládací prvky jako mají vlastnost, lze definovat hodnotu vlastnosti šablony stejným způsobem jako ostatní hodnoty vlastností, které jsme <xref:System.Windows.Style> <xref:System.Windows.Setter>nastavili v s použitím. Přidejte následující zvýrazněný kód na styl tlačítka.  
  
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
  
2. **Upravit úpravu tlačítek:** V tomto okamžiku je nutné šablonu definovat. Přidejte následující zvýrazněný kód. Tento kód určuje dva <xref:System.Windows.Shapes.Rectangle> prvky s zaoblenými hranami následovaný. <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.DockPanel> Slouží k<xref:System.Windows.Controls.ContentPresenter> hostování tlačítka. <xref:System.Windows.Controls.ContentPresenter> Zobrazí obsah tlačítka. V tomto návodu je obsahem text ("tlačítko 1", "tlačítko 2", "tlačítko 3"). Všechny součásti šablony (obdélníky a <xref:System.Windows.Controls.DockPanel>) jsou rozloženy v <xref:System.Windows.Controls.Grid>rámci.  
  
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
  
     Stisknutím klávesy F5 spusťte aplikaci. Měl by vypadat nějak takto.  
  
     ![](./media/custom-button-animatedbutton-4.gif "custom_button_AnimatedButton_4")  
  
3. **Přidat glasseffect do šablony:** V dalším kroku přidáte skleněnou. Nejprve vytvoříte některé prostředky, které vytvoří efekt skleněného přechodu. Přidejte tyto prostředky přechodu kamkoli v rámci `Application.Resources` bloku:  
  
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
  
     Tyto prostředky se používají jako <xref:System.Windows.Shapes.Shape.Fill%2A> pro obdélník, který vložíte <xref:System.Windows.Controls.Grid> do šablony tlačítka. Přidejte následující zvýrazněný kód do šablony.  
  
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
  
     Všimněte si, <xref:System.Windows.UIElement.Opacity%2A> že obdélník `x:Name` s vlastností "glassCube" je 0, takže při spuštění ukázky se nezobrazuje skleněný obdélník překrytý nahoře. Důvodem je, že později přidáte triggery do šablony, když uživatel komunikuje s tlačítkem. Můžete si ale prohlédnout, co tlačítko vypadá nyní, změnou <xref:System.Windows.UIElement.Opacity%2A> hodnoty na 1 a spuštěním aplikace. Prohlédněte si následující obrázek. Než budete pokračovat k dalšímu kroku, změňte <xref:System.Windows.UIElement.Opacity%2A> zpět na 0.  
  
     ![Vlastní tlačítka, která byla vytvořena pomocí jazyka XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")  
  
## <a name="create-button-interactivity"></a>Vytvořit interaktivitu tlačítka  
 V této části vytvoříte triggery vlastností a aktivační události pro změnu hodnot vlastností a spustíte animace v reakci na akce uživatele, jako je například přesunutí ukazatele myši na tlačítko a kliknutí.  
  
 Snadný způsob, jak přidat interaktivitu (přetažení myší, ponechání myší, kliknutí atd.), je definovat triggery v rámci šablony nebo stylu. Chcete-li <xref:System.Windows.Trigger>vytvořit, definujte vlastnost "podmínka", například: Hodnota vlastnosti <xref:System.Windows.UIElement.IsMouseOver%2A> tlačítka je `true`rovna. Pak definujete metody setter (akce), které se provedou, když je podmínka triggeru pravdivá.  
  
#### <a name="to-create-button-interactivity"></a>Vytvoření interaktivity tlačítek  
  
1. **Přidat aktivační události šablony:** Přidejte zvýrazněný kód do šablony.  
  
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
  
2. **Přidat triggery vlastností:** Přidejte zvýrazněný kód do `ControlTemplate.Triggers` bloku:  
  
    ```xaml
    <ControlTemplate.Triggers>  
  
      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>  
  
    <ControlTemplate.Triggers/>  
    ```  
  
     Stiskněte klávesu F5 ke spuštění aplikace a zobrazení efektu při spuštění ukazatele myši nad tlačítky.  
  
3. **Přidat aktivační událost fokusu:** Dále přidáte několik podobných setter pro zpracování případu, když má tlačítko fokus (například poté, co na něj uživatel klikne).  
  
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
  
     Stisknutím klávesy F5 spusťte aplikaci a klikněte na jedno z tlačítek. Všimněte si, že tlačítko zůstane zvýrazněné, i když na něj kliknete, protože pořád má fokus. Pokud kliknete na jiné tlačítko, nové tlačítko získá fokus, zatímco poslední ho ztratí.  
  
4. **Přidejte animace pro** <xref:System.Windows.UIElement.MouseEnter> a **:**  <xref:System.Windows.UIElement.MouseLeave>   V dalším kroku přidáme k aktivačním událostem nějaké animace. Přidejte následující kód kdekoli uvnitř `ControlTemplate.Triggers` bloku.  
  
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
  
     Pokud se ukazatel myši nachází nad tlačítkem (<xref:System.Windows.UIElement.MouseEnter> událost je aktivována), existují dva animace, které jsou aktivovány. Tyto animace zmenší skleněný obdélník podél osy X a Y. Všimněte si vlastností <xref:System.Windows.Media.Animation.DoubleAnimation> prvků, <xref:System.Windows.Media.Animation.Timeline.Duration%2A> a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>. Určuje, že animace probíhá přes polovinu sekundy, a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> určuje, že se skleněná zmenší o 10%. <xref:System.Windows.Media.Animation.Timeline.Duration%2A>  
  
     Druhá aktivační procedura události (<xref:System.Windows.UIElement.MouseLeave>) jednoduše zastaví první z nich. Po zastavení <xref:System.Windows.Media.Animation.Storyboard>se všechny animované vlastnosti vrátí do jejich výchozích hodnot. Proto když uživatel přesune ukazatel myši na tlačítko, tlačítko se vrátí k tomu, jak bylo předtím, než se ukazatel myši přesunul nad tlačítko. Další informace o animacích najdete v tématu [Přehled animací](../graphics-multimedia/animation-overview.md).  
  
5. **Přidat animaci pro, když se klikne na tlačítko:** Posledním krokem je přidání triggeru pro, když uživatel klikne na tlačítko. Přidejte následující kód kdekoli uvnitř `ControlTemplate.Triggers` bloku:  
  
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
  
     Stisknutím klávesy F5 spusťte aplikaci a klikněte na jedno z tlačítek. Po kliknutí na tlačítko se otáčí obdélník kolem.  
  
## <a name="summary"></a>Souhrn  
 V tomto návodu jste provedli následující cvičení:  
  
- Cílem a <xref:System.Windows.Style> na typ objektu (<xref:System.Windows.Controls.Button>).  
  
- Řízená základní vlastnosti tlačítek v celé aplikaci pomocí <xref:System.Windows.Style>.  
  
- Vytvořené prostředky, jako jsou <xref:System.Windows.Style> přechody, které se použijí pro hodnoty vlastností setter.  
  
- Přizpůsobený vzhled tlačítek v celé aplikaci aplikováním šablony na tlačítka.  
  
- Přizpůsobení chování pro tlačítka v reakci na akce uživatele (například <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>, a <xref:System.Windows.Controls.Primitives.ButtonBase.Click>), které obsahují animační efekty.  
  
## <a name="see-also"></a>Viz také:

- [Vytvoření tlačítka pomocí nástroje Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)
- [Styly a šablony](styling-and-templating.md)
- [Přehled animace](../graphics-multimedia/animation-overview.md)
- [Přehled malování plnými barvami a přechody](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [Přehled efektů bitmap](../graphics-multimedia/bitmap-effects-overview.md)
