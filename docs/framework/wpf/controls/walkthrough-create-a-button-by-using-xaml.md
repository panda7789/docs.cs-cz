---
title: "Návod: Vytvoření tlačítka použitím XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5c5efa9f8787e65d59e1b544632e806bf3fbbc81
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a><span data-ttu-id="34554-102">Návod: Vytvoření tlačítka použitím XAML</span><span class="sxs-lookup"><span data-stu-id="34554-102">Walkthrough: Create a Button by Using XAML</span></span>
<span data-ttu-id="34554-103">Cílem tohoto návodu je informace o vytváření animované tlačítko pro použití v [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="34554-103">The objective of this walkthrough is to learn how to create an animated button for use in a [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] application.</span></span> <span data-ttu-id="34554-104">Tento návod používá styly a šablonu pro vytvoření přizpůsobené tlačítko prostředek, který umožňuje opětovné použití kódu a oddělení tlačítko logiku z deklarace tlačítko.</span><span class="sxs-lookup"><span data-stu-id="34554-104">This walkthrough uses styles and a template to create a customized button resource that allows reuse of code and separation of button logic from the button declaration.</span></span> <span data-ttu-id="34554-105">Tento názorný postup je zapsán výhradně v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="34554-105">This walkthrough is written entirely in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="34554-106">Tento postup vás provede kroky pro vytvoření aplikace zadáním nebo kopírování a vkládání [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do Microsoft [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="34554-106">This walkthrough guides you through the steps for creating the application by typing or copying and pasting [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] into Microsoft [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span> <span data-ttu-id="34554-107">Pokud si přejete se dozvíte, jak použít nástroj návrhu (Microsoft Expression Blend) vytvořit stejnou aplikaci, najdete v článku [vytvoření tlačítka společností pomocí Microsoft Expression Blend](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md).</span><span class="sxs-lookup"><span data-stu-id="34554-107">If you would prefer to learn how to use a design tool (Microsoft Expression Blend) to create the same application, see [Create a Button by Using Microsoft Expression Blend](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md).</span></span>  
  
 <span data-ttu-id="34554-108">Následující obrázek znázorňuje tlačítka bylo dokončeno.</span><span class="sxs-lookup"><span data-stu-id="34554-108">The following figure shows the finished buttons.</span></span>  
  
 <span data-ttu-id="34554-109">![Vlastní tlačítka, které se vytvořily s použitím jazyka XAML](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="34554-109">![Custom buttons that were created by using XAML](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>  
  
## <a name="create-basic-buttons"></a><span data-ttu-id="34554-110">Vytvořte základní tlačítka</span><span class="sxs-lookup"><span data-stu-id="34554-110">Create Basic Buttons</span></span>  
 <span data-ttu-id="34554-111">Začněme vytvořením nového projektu a přidáním několik tlačítka v okně.</span><span class="sxs-lookup"><span data-stu-id="34554-111">Let's start by creating a new project and adding a few buttons to the window.</span></span>  
  
#### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a><span data-ttu-id="34554-112">Vytvořte nový projekt WPF a přidání tlačítek do okna</span><span class="sxs-lookup"><span data-stu-id="34554-112">To create a new WPF project and add buttons to the window</span></span>  
  
1.  <span data-ttu-id="34554-113">Spustit[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="34554-113">Start[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span>  
  
2.  <span data-ttu-id="34554-114">**Vytvořte nový projekt WPF:** na **soubor** nabídky, přejděte na příkaz **nový**a potom klikněte na **projektu**.</span><span class="sxs-lookup"><span data-stu-id="34554-114">**Create a new WPF project:** On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="34554-115">Najít **aplikace WPF (Windows)** šablony a názvu projektu "AnimatedButton".</span><span class="sxs-lookup"><span data-stu-id="34554-115">Find the **Windows Application (WPF)** template and name the project "AnimatedButton".</span></span> <span data-ttu-id="34554-116">Tím se vytvoří kostru aplikace.</span><span class="sxs-lookup"><span data-stu-id="34554-116">This will create the skeleton for the application.</span></span>  
  
3.  <span data-ttu-id="34554-117">**Přidat základní výchozích tlačítek:** všechny soubory potřebné pro tento návod jsou poskytovány šablony.</span><span class="sxs-lookup"><span data-stu-id="34554-117">**Add basic default buttons:** All the files you need for this walkthrough are provided by the template.</span></span> <span data-ttu-id="34554-118">Dvojím kliknutím na tlačítko v Průzkumníku řešení otevřete soubor Window1.xaml.</span><span class="sxs-lookup"><span data-stu-id="34554-118">Open the Window1.xaml file by double clicking it in Solution Explorer.</span></span> <span data-ttu-id="34554-119">Ve výchozím nastavení, je <xref:System.Windows.Controls.Grid> element v Window1.xaml.</span><span class="sxs-lookup"><span data-stu-id="34554-119">By default, there is a <xref:System.Windows.Controls.Grid> element in Window1.xaml.</span></span> <span data-ttu-id="34554-120">Odeberte <xref:System.Windows.Controls.Grid> elementu a přidejte několik tlačítek [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] stránky zadáním nebo kopírování a vkládání následující zvýrazněný kód do Window1.xaml:</span><span class="sxs-lookup"><span data-stu-id="34554-120">Remove the <xref:System.Windows.Controls.Grid> element and add a few buttons to the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page by typing or copy and pasting the following highlighted code to Window1.xaml:</span></span>  
  
    ```xaml  
    <Window x:Class="AnimatedButton.Window1"  
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
      Title="AnimatedButton" Height="300" Width="300"   
      Background="Black">   <!-- Buttons arranged vertically inside a StackPanel. -->   <StackPanel HorizontalAlignment="Left">     <Button>Button 1</Button>     <Button>Button 2</Button>     <Button>Button 3</Button>   </StackPanel>  
  
    </Window>  
    ```  
  
     <span data-ttu-id="34554-121">Stisknutím klávesy F5 spusťte aplikaci; měli byste vidět sadu tlačítek, který vypadá jako na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="34554-121">Press F5 to run the application; you should see a set of buttons that looks like the following figure.</span></span>  
  
     <span data-ttu-id="34554-122">![Tři základní tlačítka](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span><span class="sxs-lookup"><span data-stu-id="34554-122">![Three basic buttons](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span></span>  
  
     <span data-ttu-id="34554-123">Teď, když jste vytvořili základní tlačítek, budete mít v souboru Window1.xaml funguje.</span><span class="sxs-lookup"><span data-stu-id="34554-123">Now that you have created the basic buttons, you are finished working in the Window1.xaml file.</span></span> <span data-ttu-id="34554-124">Zbývající návodu se zaměřuje na soubor app.xaml definování styly a šablonu pro tlačítka.</span><span class="sxs-lookup"><span data-stu-id="34554-124">The rest of the walkthrough focuses on the app.xaml file, defining styles and a template for the buttons.</span></span>  
  
## <a name="set-basic-properties"></a><span data-ttu-id="34554-125">Nastavit základní vlastnosti</span><span class="sxs-lookup"><span data-stu-id="34554-125">Set Basic Properties</span></span>  
 <span data-ttu-id="34554-126">Dále umožňuje nastavit některé vlastnosti na tato tlačítka řídit vzhled tlačítka a rozložení.</span><span class="sxs-lookup"><span data-stu-id="34554-126">Next, let's set some properties on these buttons to control the button appearance and layout.</span></span> <span data-ttu-id="34554-127">Místo jednotlivě nastavit vlastnosti tlačítka, bude používat prostředky k definování vlastnosti tlačítka pro celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="34554-127">Rather than setting properties on the buttons individually, you will use resources to define button properties for the entire application.</span></span> <span data-ttu-id="34554-128">Prostředky aplikace se koncepčně podobá externí [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)] pro webové stránky; ale prostředky jsou mnohem silnější než [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)], jak se zobrazí na konci tohoto průvodce.</span><span class="sxs-lookup"><span data-stu-id="34554-128">Application resources are conceptually similar to external [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)] for Web pages; however, resources are much more powerful than [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)], as you will see by the end of this walkthrough.</span></span> <span data-ttu-id="34554-129">Další informace o prostředcích, najdete v části [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="34554-129">To learn more about resources, see [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
#### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a><span data-ttu-id="34554-130">Nastavení základní vlastnosti tlačítek pomocí styly</span><span class="sxs-lookup"><span data-stu-id="34554-130">To use styles to set basic properties on the buttons</span></span>  
  
1.  <span data-ttu-id="34554-131">**Definování bloku Application.Resources:** otevřete app.xaml a přidejte následující zvýrazněný kód, pokud ještě není:</span><span class="sxs-lookup"><span data-stu-id="34554-131">**Define an Application.Resources block:** Open app.xaml and add the following highlighted markup if it is not already there:</span></span>  
  
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
  
     <span data-ttu-id="34554-132">Obor prostředků je určen podle kde definici zdroje.</span><span class="sxs-lookup"><span data-stu-id="34554-132">Resource scope is determined by where you define the resource.</span></span> <span data-ttu-id="34554-133">Definování prostředky v `Application.Resources` v app.xaml umožňuje soubor prostředků pro použití v libovolné místo v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="34554-133">Defining resources in `Application.Resources` in the app.xaml file enables the resource to be used from anywhere in the application.</span></span> <span data-ttu-id="34554-134">Další informace o definování oboru vašich prostředků najdete v tématu [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="34554-134">To learn more about defining the scope of your resources, see [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
2.  <span data-ttu-id="34554-135">**Vytvořit styl a definovat hodnoty vlastnosti základní s ním:** přidejte následující kód do `Application.Resources` bloku.</span><span class="sxs-lookup"><span data-stu-id="34554-135">**Create a style and define basic property values with it:** Add the following markup to the `Application.Resources` block.</span></span> <span data-ttu-id="34554-136">Tento kód vytvoří <xref:System.Windows.Style> , platí pro všechny tlačítka v nastavení aplikace <xref:System.Windows.FrameworkElement.Width%2A> tlačítek a 90 a <xref:System.Windows.FrameworkElement.Margin%2A> 10:</span><span class="sxs-lookup"><span data-stu-id="34554-136">This markup creates a <xref:System.Windows.Style> that applies to all buttons in the application, setting the <xref:System.Windows.FrameworkElement.Width%2A> of the buttons to 90 and the <xref:System.Windows.FrameworkElement.Margin%2A> to 10:</span></span>  
  
    ```xaml  
    <Application.Resources>  
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>  
    </Application.Resources>  
    ```  
  
     <span data-ttu-id="34554-137"><xref:System.Windows.Style.TargetType%2A> Vlastnost určuje, že styl platí pro všechny objekty typu <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="34554-137">The <xref:System.Windows.Style.TargetType%2A> property specifies that the style applies to all objects of type <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="34554-138">Každý <xref:System.Windows.Setter> hodnotu jinou vlastnost nastaví <xref:System.Windows.Style>.</span><span class="sxs-lookup"><span data-stu-id="34554-138">Each <xref:System.Windows.Setter> sets a different property value for the <xref:System.Windows.Style>.</span></span> <span data-ttu-id="34554-139">Proto v tomto okamžiku každé tlačítko v aplikaci má šířku 90 a okraji 10.</span><span class="sxs-lookup"><span data-stu-id="34554-139">Therefore, at this point every button in the application has a width of 90 and a margin of 10.</span></span>  <span data-ttu-id="34554-140">Pokud stisknete klávesu F5 a spusťte aplikaci, najdete v následujícím okně.</span><span class="sxs-lookup"><span data-stu-id="34554-140">If you press F5 to run the application, you see the following window.</span></span>  
  
     <span data-ttu-id="34554-141">![Tlačítka s šířkou 90 a okraji 10](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span><span class="sxs-lookup"><span data-stu-id="34554-141">![Buttons with a width of 90 and a margin of 10](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span></span>  
  
     <span data-ttu-id="34554-142">Je mnohem víc, že můžete provést se styly, včetně různými způsoby a systém doladit, jaké objekty jsou cíleny zadání hodnoty komplexní vlastností a i pomocí styly jako vstup pro jiné styly.</span><span class="sxs-lookup"><span data-stu-id="34554-142">There is much more you can do with styles, including a variety of ways to fine-tune what objects are targeted, specifying complex property values, and even using styles as input for other styles.</span></span> <span data-ttu-id="34554-143">Další informace najdete v tématu [stylů a ukázka](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="34554-143">For more information, see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>  
  
3.  <span data-ttu-id="34554-144">**Nastavení hodnoty vlastnosti stylu na prostředek:** prostředky povolit jednoduchý způsob, jak znovu použít běžně definované objekty a hodnoty.</span><span class="sxs-lookup"><span data-stu-id="34554-144">**Set a style property value to a resource:** Resources enable a simple way to reuse commonly defined objects and values.</span></span> <span data-ttu-id="34554-145">Je obzvláště užitečná k definování komplexní hodnoty používání prostředků, aby váš kód více modulární.</span><span class="sxs-lookup"><span data-stu-id="34554-145">It is especially useful to define complex values using resources to make your code more modular.</span></span> <span data-ttu-id="34554-146">Přidejte následující zvýrazněný kód do app.xaml.</span><span class="sxs-lookup"><span data-stu-id="34554-146">Add the following highlighted markup to app.xaml.</span></span>  
  
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
  
     <span data-ttu-id="34554-147">Přímo pod `Application.Resources` bloku vytvoříte prostředek s názvem "GrayBlueGradientBrush".</span><span class="sxs-lookup"><span data-stu-id="34554-147">Directly under the `Application.Resources` block, you created a resource called "GrayBlueGradientBrush".</span></span> <span data-ttu-id="34554-148">Tento prostředek definuje vodorovný přechod.</span><span class="sxs-lookup"><span data-stu-id="34554-148">This resource defines a horizontal gradient.</span></span> <span data-ttu-id="34554-149">Tento prostředek lze použít jako hodnotu vlastnosti z libovolného místa v aplikaci, včetně uvnitř nastavovací metoda styl tlačítko <xref:System.Windows.Controls.Control.Background%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="34554-149">This resource can be used as a property value from anywhere in the application, including inside the button style setter for the <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="34554-150">Nyní máte všechny tlačítka <xref:System.Windows.Controls.Control.Background%2A> hodnota vlastnosti této přechodu.</span><span class="sxs-lookup"><span data-stu-id="34554-150">Now, all the buttons have a <xref:System.Windows.Controls.Control.Background%2A> property value of this gradient.</span></span>  
  
     <span data-ttu-id="34554-151">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="34554-151">Press F5 to run the application.</span></span> <span data-ttu-id="34554-152">By měl vypadat jako následující.</span><span class="sxs-lookup"><span data-stu-id="34554-152">It should look like the following.</span></span>  
  
     <span data-ttu-id="34554-153">![Tlačítka s barevného přechodu pozadí](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span><span class="sxs-lookup"><span data-stu-id="34554-153">![Buttons with a gradient background](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span></span>  
  
## <a name="create-a-template-that-defines-the-look-of-the-button"></a><span data-ttu-id="34554-154">Vytvořit šablonu, která definuje vzhled tlačítka</span><span class="sxs-lookup"><span data-stu-id="34554-154">Create a Template That Defines the Look of the Button</span></span>  
 <span data-ttu-id="34554-155">V této části vytvoříte šablonu, která se přizpůsobí vzhled tlačítka (prezentace).</span><span class="sxs-lookup"><span data-stu-id="34554-155">In this section, you create a template that customizes the appearance (presentation) of the button.</span></span> <span data-ttu-id="34554-156">Tlačítko prezentace se skládá z několika objektů včetně obdélníků a další součásti chcete jedinečný vzhled tlačítka.</span><span class="sxs-lookup"><span data-stu-id="34554-156">The button presentation is made up of several objects including rectangles and other components to give the button a unique look.</span></span>  
  
 <span data-ttu-id="34554-157">Zatím řízení vzhled tlačítka v aplikaci má byla omezena změna vlastností tlačítka.</span><span class="sxs-lookup"><span data-stu-id="34554-157">So far, the control of how buttons look in the application has been confined to changing properties of the button.</span></span> <span data-ttu-id="34554-158">Co dělat, pokud chcete více znak změnit vzhled tlačítka?</span><span class="sxs-lookup"><span data-stu-id="34554-158">What if you want to make more radical changes to the button's appearance?</span></span> <span data-ttu-id="34554-159">Šablony umožňují efektivní kontrolu nad prezentace objektu.</span><span class="sxs-lookup"><span data-stu-id="34554-159">Templates enable powerful control over the presentation of an object.</span></span> <span data-ttu-id="34554-160">Protože šablony lze používat v rámci styly, můžete použít šablonu pro všechny objekty, které se vztahuje styl (v tomto návodu tlačítko).</span><span class="sxs-lookup"><span data-stu-id="34554-160">Because templates can be used within styles, you can apply a template to all objects that the style applies to (in this walkthrough, the button).</span></span>  
  
#### <a name="to-use-the-template-to-define-the-look-of-the-button"></a><span data-ttu-id="34554-161">Abyste mohli použít šablonu definovat vzhled tlačítka</span><span class="sxs-lookup"><span data-stu-id="34554-161">To use the template to define the look of the button</span></span>  
  
1.  <span data-ttu-id="34554-162">**Nastavení šablony:** protože ovládací prvky, jako <xref:System.Windows.Controls.Button> mít <xref:System.Windows.Controls.Control.Template%2A> vlastnost, můžete definovat hodnoty vlastnosti šablony stejně jako hodnoty vlastností jsme ve nastavili <xref:System.Windows.Style> pomocí <xref:System.Windows.Setter>.</span><span class="sxs-lookup"><span data-stu-id="34554-162">**Set up the template:** Because controls like <xref:System.Windows.Controls.Button> have a <xref:System.Windows.Controls.Control.Template%2A> property, you can define the template property value just like the other property values we have set in a <xref:System.Windows.Style> using a <xref:System.Windows.Setter>.</span></span> <span data-ttu-id="34554-163">Přidejte následující zvýrazněný kód do vaší stylů tlačítek.</span><span class="sxs-lookup"><span data-stu-id="34554-163">Add the following highlighted markup to your button style.</span></span>  
  
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
  
2.  <span data-ttu-id="34554-164">**Příkaz ALTER tlačítko prezentace:** v tomto okamžiku je nutné definovat šablony.</span><span class="sxs-lookup"><span data-stu-id="34554-164">**Alter button presentation:** At this point, you need to define the template.</span></span> <span data-ttu-id="34554-165">Přidejte následující zvýrazněný kód.</span><span class="sxs-lookup"><span data-stu-id="34554-165">Add the following highlighted markup.</span></span> <span data-ttu-id="34554-166">Tento kód určuje dva <xref:System.Windows.Shapes.Rectangle> prvky s zaoblenými hranami, za nímž následuje <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="34554-166">This markup specifies two <xref:System.Windows.Shapes.Rectangle> elements with rounded edges, followed by a <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="34554-167"><xref:System.Windows.Controls.DockPanel> Se používá k hostiteli <xref:System.Windows.Controls.ContentPresenter> tlačítka.</span><span class="sxs-lookup"><span data-stu-id="34554-167">The <xref:System.Windows.Controls.DockPanel> is used to host the <xref:System.Windows.Controls.ContentPresenter> of the button.</span></span> <span data-ttu-id="34554-168">A <xref:System.Windows.Controls.ContentPresenter> zobrazuje obsah tlačítka.</span><span class="sxs-lookup"><span data-stu-id="34554-168">A <xref:System.Windows.Controls.ContentPresenter> displays the content of the button.</span></span> <span data-ttu-id="34554-169">V tomto návodu je obsah text ("Tlačítko 1", "Tlačítko 2", "Tlačítko 3").</span><span class="sxs-lookup"><span data-stu-id="34554-169">In this walkthrough, the content is text ("Button 1", "Button 2", "Button 3").</span></span> <span data-ttu-id="34554-170">Všechny součásti šablony (obdélníků a <xref:System.Windows.Controls.DockPanel>) jsou nastíněny uvnitř <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="34554-170">All of the template components (the rectangles and the <xref:System.Windows.Controls.DockPanel>) are laid out inside of a <xref:System.Windows.Controls.Grid>.</span></span>  
  
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
  
     <span data-ttu-id="34554-171">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="34554-171">Press F5 to run the application.</span></span> <span data-ttu-id="34554-172">By měl vypadat jako následující.</span><span class="sxs-lookup"><span data-stu-id="34554-172">It should look like the following.</span></span>  
  
     <span data-ttu-id="34554-173">![](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-4.gif "custom_button_AnimatedButton_4")</span><span class="sxs-lookup"><span data-stu-id="34554-173">![](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-4.gif "custom_button_AnimatedButton_4")</span></span>  
  
3.  <span data-ttu-id="34554-174">**Přidání do šablony glasseffect:** dále přidáte skla.</span><span class="sxs-lookup"><span data-stu-id="34554-174">**Add a glasseffect to the template:** Next you will add the glass.</span></span> <span data-ttu-id="34554-175">Nejdřív vytvoříte některé prostředky, které vytvářejí skleněný efekt barevného přechodu.</span><span class="sxs-lookup"><span data-stu-id="34554-175">First you create some resources that create a glass gradient effect.</span></span> <span data-ttu-id="34554-176">Přidat tyto přechodu prostředky kdekoli v rámci `Application.Resources` bloku:</span><span class="sxs-lookup"><span data-stu-id="34554-176">Add these gradient resources anywhere within the `Application.Resources` block:</span></span>  
  
    ```xaml  
    <Application.Resources>  
      <GradientStopCollection x:Key="MyGlassGradientStopsResource">     <GradientStop Color="WhiteSmoke" Offset="0.2" />     <GradientStop Color="Transparent" Offset="0.4" />     <GradientStop Color="WhiteSmoke" Offset="0.5" />     <GradientStop Color="Transparent" Offset="0.75" />     <GradientStop Color="WhiteSmoke" Offset="0.9" />     <GradientStop Color="Transparent" Offset="1" />   </GradientStopCollection>   <LinearGradientBrush x:Key="MyGlassBrushResource"     StartPoint="0,0" EndPoint="1,1" Opacity="0.75"     GradientStops="{StaticResource MyGlassGradientStopsResource}" />  
    <!-- Styles and other resources below here. -->  
    ```  
  
     <span data-ttu-id="34554-177">Tyto prostředky jsou použity jako <xref:System.Windows.Shapes.Shape.Fill%2A> pro obdélníku, který jsme vložit do <xref:System.Windows.Controls.Grid> tlačítko šablony.</span><span class="sxs-lookup"><span data-stu-id="34554-177">These resources are used as the <xref:System.Windows.Shapes.Shape.Fill%2A> for a rectangle that we insert into the <xref:System.Windows.Controls.Grid> of the button template.</span></span> <span data-ttu-id="34554-178">Přidejte následující zvýrazněný kód do šablony.</span><span class="sxs-lookup"><span data-stu-id="34554-178">Add the following highlighted markup to the template.</span></span>  
  
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
  
     <span data-ttu-id="34554-179">Všimněte si, že <xref:System.Windows.UIElement.Opacity%2A> obdélníku s `x:Name` vlastnost "glassCube" je 0, tak při spuštění vzorového nevidíte pohotovostní rámeček jako překryvný obrázek nahoře.</span><span class="sxs-lookup"><span data-stu-id="34554-179">Notice that the <xref:System.Windows.UIElement.Opacity%2A> of the rectangle with the `x:Name` property of "glassCube" is 0, so when you run the sample, you do not see the glass rectangle overlaid on top.</span></span> <span data-ttu-id="34554-180">Je to proto, že později přidáme aktivační události do šablony pro tehdy, když uživatel pracuje s tlačítko.</span><span class="sxs-lookup"><span data-stu-id="34554-180">This is because we will later add triggers to the template for when the user interacts with the button.</span></span> <span data-ttu-id="34554-181">Ale uvidíte, jak tlačítko vypadá teď změnou <xref:System.Windows.UIElement.Opacity%2A> hodnotu na 1 a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="34554-181">However, you can see what the button looks like now by changing the <xref:System.Windows.UIElement.Opacity%2A> value to 1 and running the application.</span></span> <span data-ttu-id="34554-182">Prohlédněte si následující obrázek.</span><span class="sxs-lookup"><span data-stu-id="34554-182">See the following figure.</span></span> <span data-ttu-id="34554-183">Než budete pokračovat k dalšímu kroku, změnit <xref:System.Windows.UIElement.Opacity%2A> zpět na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="34554-183">Before proceeding to the next step, change the <xref:System.Windows.UIElement.Opacity%2A> back to 0.</span></span>  
  
     <span data-ttu-id="34554-184">![Vlastní tlačítka, které se vytvořily s použitím jazyka XAML](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="34554-184">![Custom buttons that were created by using XAML](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>  
  
## <a name="create-button-interactivity"></a><span data-ttu-id="34554-185">Vytvoření interaktivity tlačítko</span><span class="sxs-lookup"><span data-stu-id="34554-185">Create Button Interactivity</span></span>  
 <span data-ttu-id="34554-186">V této části vytvoříte vlastnost triggerů a aktivačních událostí změně hodnot vlastností a spuštění animace v odpovědi na akce uživatele, například ukazatele myši nad tlačítko a kliknutím na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="34554-186">In this section, you will create property triggers and event triggers to change property values and run animations in response to user actions such as moving the mouse pointer over the button and clicking.</span></span>  
  
 <span data-ttu-id="34554-187">Zadejte aktivační události v rámci šablony nebo styl je snadný způsob, jak přidat interaktivity (myší nad, ponechejte myši, klikněte na tlačítko a tak dále).</span><span class="sxs-lookup"><span data-stu-id="34554-187">An easy way to add interactivity (mouse-over, mouse-leave, click, and so on) is to define triggers within your template or style.</span></span> <span data-ttu-id="34554-188">K vytvoření <xref:System.Windows.Trigger>, například definovat vlastnost "podmínky": tlačítko <xref:System.Windows.UIElement.IsMouseOver%2A> vlastnost hodnota se rovná `true`.</span><span class="sxs-lookup"><span data-stu-id="34554-188">To create a <xref:System.Windows.Trigger>, you define a property "condition" such as: The button <xref:System.Windows.UIElement.IsMouseOver%2A> property value is equal to `true`.</span></span> <span data-ttu-id="34554-189">Potom můžete definovat setter (akce), kterým dochází, když je splněna podmínka aktivace.</span><span class="sxs-lookup"><span data-stu-id="34554-189">You then define setters (actions) that take place when the trigger condition is true.</span></span>  
  
#### <a name="to-create-button-interactivity"></a><span data-ttu-id="34554-190">Chcete-li vytvořit interaktivity tlačítko</span><span class="sxs-lookup"><span data-stu-id="34554-190">To create button interactivity</span></span>  
  
1.  <span data-ttu-id="34554-191">**Přidat šablonu aktivační události:** do šablony přidat zvýrazněný kód.</span><span class="sxs-lookup"><span data-stu-id="34554-191">**Add template triggers:** Add the highlighted markup to your template.</span></span>  
  
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
  
2.  <span data-ttu-id="34554-192">**Přidat vlastnost aktivační události:** přidat zvýrazněná značky k `ControlTemplate.Triggers` bloku:</span><span class="sxs-lookup"><span data-stu-id="34554-192">**Add property triggers:** Add the highlighted markup to the `ControlTemplate.Triggers` block:</span></span>  
  
    ```  
    <ControlTemplate.Triggers>  
  
      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>  
  
    <ControlTemplate.Triggers/>  
    ```  
  
     <span data-ttu-id="34554-193">Stisknutím klávesy F5 spusťte aplikaci a projevily po spuštění ukazatel myši nad tlačítka.</span><span class="sxs-lookup"><span data-stu-id="34554-193">Press F5 to run the application and see the effect as you run the mouse pointer over the buttons.</span></span>  
  
3.  <span data-ttu-id="34554-194">**Přidat aktivační událost fokus:** potom přidáme některé podobné setter zpracování případě, pokud má právě fokus (například po klepnutí se), na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="34554-194">**Add a focus trigger:** Next, we'll add some similar setters to handle the case when the button has focus (for example, after the user clicks it).</span></span>  
  
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
  
     <span data-ttu-id="34554-195">Stisknutím klávesy F5 spusťte aplikaci a klikněte na jednu z tlačítka.</span><span class="sxs-lookup"><span data-stu-id="34554-195">Press F5 to run the application and click on one of the buttons.</span></span> <span data-ttu-id="34554-196">Všimněte si, že zůstane tlačítko zvýrazněná po kliknutí na tlačítko ji vzhledem k tomu, že je stále fokus.</span><span class="sxs-lookup"><span data-stu-id="34554-196">Notice that the button stays highlighted after you click it because it still has focus.</span></span> <span data-ttu-id="34554-197">Pokud klepnete na tlačítko Další, nové tlačítko získá fokus při poslední ztratí ho.</span><span class="sxs-lookup"><span data-stu-id="34554-197">If you click another button, the new button gains focus while the last one loses it.</span></span>  
  
4.  <span data-ttu-id="34554-198">**Přidání animace pro** <xref:System.Windows.UIElement.MouseEnter> **a** <xref:System.Windows.UIElement.MouseLeave> **:** další přidáme některé animací aktivačních událostí.</span><span class="sxs-lookup"><span data-stu-id="34554-198">**Add animations for**  <xref:System.Windows.UIElement.MouseEnter> **and** <xref:System.Windows.UIElement.MouseLeave> **:** Next we add some animations to the triggers.</span></span> <span data-ttu-id="34554-199">Přidejte následující kód kdekoli v z `ControlTemplate.Triggers` bloku.</span><span class="sxs-lookup"><span data-stu-id="34554-199">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block.</span></span>  
  
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
  
     <span data-ttu-id="34554-200">Rámeček pohotovostní zmenší při ukazatel myši přesune na tlačítko a vrátí zpět na normální velikost, když ukazatel opustí.</span><span class="sxs-lookup"><span data-stu-id="34554-200">The glass rectangle shrinks when the mouse pointer moves over the button and returns back to normal size when the pointer leaves.</span></span>  
  
     <span data-ttu-id="34554-201">Existují dvě animace, které jsou aktivované, když ukazatel prochází přes tlačítko (<xref:System.Windows.UIElement.MouseEnter> událost se vyvolá,).</span><span class="sxs-lookup"><span data-stu-id="34554-201">There are two animations that are triggered when the pointer goes over the button (<xref:System.Windows.UIElement.MouseEnter> event is raised).</span></span> <span data-ttu-id="34554-202">Tyto animací zmenšit rámeček pohotovostní podél osy X a Y.</span><span class="sxs-lookup"><span data-stu-id="34554-202">These animations shrink the glass rectangle along the X and Y axis.</span></span> <span data-ttu-id="34554-203">Všimněte si vlastnosti na <xref:System.Windows.Media.Animation.DoubleAnimation> elementy – <xref:System.Windows.Media.Animation.Timeline.Duration%2A> a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.</span><span class="sxs-lookup"><span data-stu-id="34554-203">Notice the properties on the <xref:System.Windows.Media.Animation.DoubleAnimation> elements — <xref:System.Windows.Media.Animation.Timeline.Duration%2A> and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.</span></span> <span data-ttu-id="34554-204"><xref:System.Windows.Media.Animation.Timeline.Duration%2A> Určuje, že animace dochází k více než půl sekundy, a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> Určuje, že skla zmenšuje 10 %.</span><span class="sxs-lookup"><span data-stu-id="34554-204">The <xref:System.Windows.Media.Animation.Timeline.Duration%2A> specifies that the animation occurs over half a second, and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> specifies that the glass shrinks by 10%.</span></span>  
  
     <span data-ttu-id="34554-205">Druhý aktivační události (<xref:System.Windows.UIElement.MouseLeave>) jednoduše zastaví první z nich.</span><span class="sxs-lookup"><span data-stu-id="34554-205">The second event trigger (<xref:System.Windows.UIElement.MouseLeave>) simply stops the first one.</span></span> <span data-ttu-id="34554-206">Při zastavení <xref:System.Windows.Media.Animation.Storyboard>, všechny animovaný vlastnosti vrátit na výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="34554-206">When you stop a <xref:System.Windows.Media.Animation.Storyboard>, all the animated properties return to their default values.</span></span> <span data-ttu-id="34554-207">Proto pokud se uživatel přesune ukazatel mimo tlačítko, tlačítko přejde zpět způsob, jakým byl před přesunutí ukazatele myši nad tlačítko.</span><span class="sxs-lookup"><span data-stu-id="34554-207">Therefore, when the user moves the pointer off the button, the button goes back to the way it was before the mouse pointer moved over the button.</span></span> <span data-ttu-id="34554-208">Další informace o animací najdete v tématu [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="34554-208">For more information about animations, see [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span>  
  
5.  <span data-ttu-id="34554-209">**Přidání animace pro při kliknutí na tlačítko:** posledním krokem je aktivační událost pro když uživatel klikne na tlačítko Přidat.</span><span class="sxs-lookup"><span data-stu-id="34554-209">**Add an animation for when the button is clicked:** The final step is to add a trigger for when the user clicks the button.</span></span> <span data-ttu-id="34554-210">Přidejte následující kód kdekoli v z `ControlTemplate.Triggers` bloku:</span><span class="sxs-lookup"><span data-stu-id="34554-210">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block:</span></span>  
  
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
  
     <span data-ttu-id="34554-211">Stisknutím klávesy F5 spusťte aplikaci a klikněte na jednu z tlačítka.</span><span class="sxs-lookup"><span data-stu-id="34554-211">Press F5 to run the application, and click one of the buttons.</span></span> <span data-ttu-id="34554-212">Po kliknutí tlačítko, rámeček pohotovostní otáčí kolem.</span><span class="sxs-lookup"><span data-stu-id="34554-212">When you click a button, the glass rectangle spins around.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="34554-213">Souhrn</span><span class="sxs-lookup"><span data-stu-id="34554-213">Summary</span></span>  
 <span data-ttu-id="34554-214">V tomto návodu jste provedli následující cvičení:</span><span class="sxs-lookup"><span data-stu-id="34554-214">In this walkthrough, you performed the following exercises:</span></span>  
  
-   <span data-ttu-id="34554-215">Cílem <xref:System.Windows.Style> na typ objektu (<xref:System.Windows.Controls.Button>).</span><span class="sxs-lookup"><span data-stu-id="34554-215">Targeted a <xref:System.Windows.Style> to an object type (<xref:System.Windows.Controls.Button>).</span></span>  
  
-   <span data-ttu-id="34554-216">Řídí základní vlastnosti tlačítek v celé aplikace pomocí <xref:System.Windows.Style>.</span><span class="sxs-lookup"><span data-stu-id="34554-216">Controlled basic properties of the buttons in the entire application using the <xref:System.Windows.Style>.</span></span>  
  
-   <span data-ttu-id="34554-217">Vytvořit prostředky jako přechody pro hodnot vlastností <xref:System.Windows.Style> setter.</span><span class="sxs-lookup"><span data-stu-id="34554-217">Created resources like gradients to use for property values of the <xref:System.Windows.Style> setters.</span></span>  
  
-   <span data-ttu-id="34554-218">Použití šablony na tlačítka přizpůsobit vzhled tlačítek v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="34554-218">Customized the look of buttons in the entire application by applying a template to the buttons.</span></span>  
  
-   <span data-ttu-id="34554-219">Přizpůsobit chování pro tlačítka v odpovědi na akce uživatele (například <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>, a <xref:System.Windows.Controls.Primitives.ButtonBase.Click>), které zahrnuty efekty animace.</span><span class="sxs-lookup"><span data-stu-id="34554-219">Customized behavior for the buttons in response to user actions (such as <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>, and <xref:System.Windows.Controls.Primitives.ButtonBase.Click>) that included animation effects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34554-220">Viz také</span><span class="sxs-lookup"><span data-stu-id="34554-220">See Also</span></span>  
 [<span data-ttu-id="34554-221">Vytvoření tlačítka pomocí nástroje Microsoft Expression Blend</span><span class="sxs-lookup"><span data-stu-id="34554-221">Create a Button by Using Microsoft Expression Blend</span></span>](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md)  
 [<span data-ttu-id="34554-222">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="34554-222">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="34554-223">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="34554-223">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="34554-224">Přehled malování plnými barvami a přechody</span><span class="sxs-lookup"><span data-stu-id="34554-224">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [<span data-ttu-id="34554-225">Přehled efektů bitmap</span><span class="sxs-lookup"><span data-stu-id="34554-225">Bitmap Effects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/bitmap-effects-overview.md)
