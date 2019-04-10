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
# <a name="walkthrough-create-a-button-by-using-xaml"></a><span data-ttu-id="c5f40-102">Návod: Vytvoření tlačítka pomocí XAML</span><span class="sxs-lookup"><span data-stu-id="c5f40-102">Walkthrough: Create a Button by Using XAML</span></span>
<span data-ttu-id="c5f40-103">Cílem tohoto návodu je zjistěte, jak vytvořit animovaná tlačítka pro použití v aplikaci Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="c5f40-103">The objective of this walkthrough is to learn how to create an animated button for use in a Windows Presentation Foundation (WPF) application.</span></span> <span data-ttu-id="c5f40-104">Tento návod používá – styly a šablony vytvořit tlačítko vlastní prostředek, umožňující opětovné použití kódu a oddělení logiky tlačítko od deklarace tlačítko.</span><span class="sxs-lookup"><span data-stu-id="c5f40-104">This walkthrough uses styles and a template to create a customized button resource that allows reuse of code and separation of button logic from the button declaration.</span></span> <span data-ttu-id="c5f40-105">Tento návod byl napsán výhradně v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c5f40-105">This walkthrough is written entirely in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c5f40-106">Tento názorný postup vás provede kroky pro vytváření aplikace psát nebo zkopírováním a vložením [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do sady Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c5f40-106">This walkthrough guides you through the steps for creating the application by typing or copying and pasting [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] into Microsoft Visual Studio.</span></span> <span data-ttu-id="c5f40-107">Pokud chcete další informace o použití návrhářský nástroj (Microsoft Expression Blend) Chcete-li vytvořit stejnou aplikaci, najdete v článku [vytvoření tlačítka pomocí pomocí Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).</span><span class="sxs-lookup"><span data-stu-id="c5f40-107">If you would prefer to learn how to use a design tool (Microsoft Expression Blend) to create the same application, see [Create a Button by Using Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).</span></span>  
  
 <span data-ttu-id="c5f40-108">Následující obrázek ukazuje dokončení tlačítka.</span><span class="sxs-lookup"><span data-stu-id="c5f40-108">The following figure shows the finished buttons.</span></span>  
  
 <span data-ttu-id="c5f40-109">![Vlastní tlačítka, které se vytvořily pomocí XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="c5f40-109">![Custom buttons that were created by using XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>  
  
## <a name="create-basic-buttons"></a><span data-ttu-id="c5f40-110">Vytvoření základní tlačítka</span><span class="sxs-lookup"><span data-stu-id="c5f40-110">Create Basic Buttons</span></span>  
 <span data-ttu-id="c5f40-111">Začněme vytvořením nového projektu a přidává několik tlačítek do okna.</span><span class="sxs-lookup"><span data-stu-id="c5f40-111">Let's start by creating a new project and adding a few buttons to the window.</span></span>  
  
#### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a><span data-ttu-id="c5f40-112">Přidání tlačítek do okna a vytvořte nový projekt WPF</span><span class="sxs-lookup"><span data-stu-id="c5f40-112">To create a new WPF project and add buttons to the window</span></span>  
  
1. <span data-ttu-id="c5f40-113">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c5f40-113">Start Visual Studio.</span></span>  
  
2. <span data-ttu-id="c5f40-114">**Vytvořte nový projekt WPF:** Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.</span><span class="sxs-lookup"><span data-stu-id="c5f40-114">**Create a new WPF project:** On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="c5f40-115">Najít **aplikace Windows (WPF)** šablony a názvu projektu "AnimatedButton".</span><span class="sxs-lookup"><span data-stu-id="c5f40-115">Find the **Windows Application (WPF)** template and name the project "AnimatedButton".</span></span> <span data-ttu-id="c5f40-116">Tím se vytvoří kostru pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c5f40-116">This will create the skeleton for the application.</span></span>  
  
3. <span data-ttu-id="c5f40-117">**Přidáte výchozí základní tlačítka:** Všechny soubory, které potřebujete pro Tento názorný postup jsou k dispozici šablonou.</span><span class="sxs-lookup"><span data-stu-id="c5f40-117">**Add basic default buttons:** All the files you need for this walkthrough are provided by the template.</span></span> <span data-ttu-id="c5f40-118">Otevřete soubor Window1.xaml dvojitým kliknutím v Průzkumníku řešení.</span><span class="sxs-lookup"><span data-stu-id="c5f40-118">Open the Window1.xaml file by double clicking it in Solution Explorer.</span></span> <span data-ttu-id="c5f40-119">Ve výchozím nastavení, je <xref:System.Windows.Controls.Grid> prvek Window1.xaml.</span><span class="sxs-lookup"><span data-stu-id="c5f40-119">By default, there is a <xref:System.Windows.Controls.Grid> element in Window1.xaml.</span></span> <span data-ttu-id="c5f40-120">Odeberte <xref:System.Windows.Controls.Grid> elementu a přidejte několik tlačítek na hodnotu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] stránky zadáním nebo kopírování a vkládání následující zvýrazněný kód do Window1.xaml:</span><span class="sxs-lookup"><span data-stu-id="c5f40-120">Remove the <xref:System.Windows.Controls.Grid> element and add a few buttons to the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page by typing or copy and pasting the following highlighted code to Window1.xaml:</span></span>  
  
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
  
     <span data-ttu-id="c5f40-121">Stisknutím klávesy F5 spusťte aplikaci. měli byste vidět sadu tlačítek, která vypadá jako na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="c5f40-121">Press F5 to run the application; you should see a set of buttons that looks like the following figure.</span></span>  
  
     <span data-ttu-id="c5f40-122">![Tři základní tlačítka](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span><span class="sxs-lookup"><span data-stu-id="c5f40-122">![Three basic buttons](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span></span>  
  
     <span data-ttu-id="c5f40-123">Teď, když jste vytvořili základní tlačítka, jste dokončili práci v souboru Window1.xaml.</span><span class="sxs-lookup"><span data-stu-id="c5f40-123">Now that you have created the basic buttons, you are finished working in the Window1.xaml file.</span></span> <span data-ttu-id="c5f40-124">Zbytek tohoto průvodce se zaměřuje na soubor app.xaml definování – styly a šablony tlačítek.</span><span class="sxs-lookup"><span data-stu-id="c5f40-124">The rest of the walkthrough focuses on the app.xaml file, defining styles and a template for the buttons.</span></span>  
  
## <a name="set-basic-properties"></a><span data-ttu-id="c5f40-125">Nastavte základní vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c5f40-125">Set Basic Properties</span></span>  
 <span data-ttu-id="c5f40-126">V dalším kroku nastavíme některé vlastnosti na tato tlačítka řídit vzhled tlačítka a rozložení.</span><span class="sxs-lookup"><span data-stu-id="c5f40-126">Next, let's set some properties on these buttons to control the button appearance and layout.</span></span> <span data-ttu-id="c5f40-127">Namísto nastavení vlastností tlačítka jednotlivě, budete používat prostředky k definování vlastností tlačítka pro celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c5f40-127">Rather than setting properties on the buttons individually, you will use resources to define button properties for the entire application.</span></span> <span data-ttu-id="c5f40-128">Prostředky aplikace jsou koncepčně podobné pro externí [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)] pro webové stránky; prostředky jsou však mnohem výkonnější než [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)], jak se zobrazí na konci tohoto návodu.</span><span class="sxs-lookup"><span data-stu-id="c5f40-128">Application resources are conceptually similar to external [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)] for Web pages; however, resources are much more powerful than [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)], as you will see by the end of this walkthrough.</span></span> <span data-ttu-id="c5f40-129">Další informace o prostředcích najdete v tématu [prostředky XAML](../advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="c5f40-129">To learn more about resources, see [XAML Resources](../advanced/xaml-resources.md).</span></span>  
  
#### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a><span data-ttu-id="c5f40-130">Použití stylů můžete nastavit základní vlastnosti tlačítka</span><span class="sxs-lookup"><span data-stu-id="c5f40-130">To use styles to set basic properties on the buttons</span></span>  
  
1. <span data-ttu-id="c5f40-131">**Definování blok Application.Resources:** Otevření souboru app.xaml a pokud už tam není, přidejte následující zvýrazněný kód:</span><span class="sxs-lookup"><span data-stu-id="c5f40-131">**Define an Application.Resources block:** Open app.xaml and add the following highlighted markup if it is not already there:</span></span>  
  
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
  
     <span data-ttu-id="c5f40-132">Tady můžete definovat prostředek Určuje prostředek oboru.</span><span class="sxs-lookup"><span data-stu-id="c5f40-132">Resource scope is determined by where you define the resource.</span></span> <span data-ttu-id="c5f40-133">Definování prostředků v `Application.Resources` v souboru app.xaml umožňuje soubor prostředků pro použití v kdekoli v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c5f40-133">Defining resources in `Application.Resources` in the app.xaml file enables the resource to be used from anywhere in the application.</span></span> <span data-ttu-id="c5f40-134">Další informace o definování oboru prostředků najdete v tématu [prostředky XAML](../advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="c5f40-134">To learn more about defining the scope of your resources, see [XAML Resources](../advanced/xaml-resources.md).</span></span>  
  
2. <span data-ttu-id="c5f40-135">**Vytvoření stylu a definovat hodnoty základní vlastnosti s ní:** Přidejte následující kód k `Application.Resources` bloku.</span><span class="sxs-lookup"><span data-stu-id="c5f40-135">**Create a style and define basic property values with it:** Add the following markup to the `Application.Resources` block.</span></span> <span data-ttu-id="c5f40-136">Tento kód vytvoří <xref:System.Windows.Style> , která se vztahuje na všechna tlačítka v nastavení aplikace <xref:System.Windows.FrameworkElement.Width%2A> tlačítek na hodnotu 90 a <xref:System.Windows.FrameworkElement.Margin%2A> 10:</span><span class="sxs-lookup"><span data-stu-id="c5f40-136">This markup creates a <xref:System.Windows.Style> that applies to all buttons in the application, setting the <xref:System.Windows.FrameworkElement.Width%2A> of the buttons to 90 and the <xref:System.Windows.FrameworkElement.Margin%2A> to 10:</span></span>  
  
    ```xaml  
    <Application.Resources>  
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>  
    </Application.Resources>  
    ```  
  
     <span data-ttu-id="c5f40-137"><xref:System.Windows.Style.TargetType%2A> Vlastnost určuje, že styl platí pro všechny objekty typu <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="c5f40-137">The <xref:System.Windows.Style.TargetType%2A> property specifies that the style applies to all objects of type <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="c5f40-138">Každý <xref:System.Windows.Setter> nastaví hodnotu jinou vlastnost <xref:System.Windows.Style>.</span><span class="sxs-lookup"><span data-stu-id="c5f40-138">Each <xref:System.Windows.Setter> sets a different property value for the <xref:System.Windows.Style>.</span></span> <span data-ttu-id="c5f40-139">Proto v tuto chvíli každé tlačítko v aplikaci má šířku 90 a okraj 10.</span><span class="sxs-lookup"><span data-stu-id="c5f40-139">Therefore, at this point every button in the application has a width of 90 and a margin of 10.</span></span>  <span data-ttu-id="c5f40-140">Pokud stisknete klávesu F5 ke spuštění aplikace, zobrazí následující okno.</span><span class="sxs-lookup"><span data-stu-id="c5f40-140">If you press F5 to run the application, you see the following window.</span></span>  
  
     <span data-ttu-id="c5f40-141">![Tlačítka s šířkou 90 a okraj 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span><span class="sxs-lookup"><span data-stu-id="c5f40-141">![Buttons with a width of 90 and a margin of 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span></span>  
  
     <span data-ttu-id="c5f40-142">Je mnohem více že můžete provést se styly, včetně celou řadu způsobů, jak doladit, jaké objekty jsou cíleny, zadáte hodnoty komplexní vlastnost a dokonce i pomocí stylů jako vstup pro jiné styly.</span><span class="sxs-lookup"><span data-stu-id="c5f40-142">There is much more you can do with styles, including a variety of ways to fine-tune what objects are targeted, specifying complex property values, and even using styles as input for other styles.</span></span> <span data-ttu-id="c5f40-143">Další informace najdete v tématu [styly a šablony](styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="c5f40-143">For more information, see [Styling and Templating](styling-and-templating.md).</span></span>  
  
3. <span data-ttu-id="c5f40-144">**Nastavte hodnotu vlastnosti stylu na prostředek:** Prostředky povolit jednoduchý způsob, jak opětovné použití obecně definovaných objektů a hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c5f40-144">**Set a style property value to a resource:** Resources enable a simple way to reuse commonly defined objects and values.</span></span> <span data-ttu-id="c5f40-145">To je užitečné zejména pro definování komplexních hodnot. aby byl kód modulárnější použití prostředků.</span><span class="sxs-lookup"><span data-stu-id="c5f40-145">It is especially useful to define complex values using resources to make your code more modular.</span></span> <span data-ttu-id="c5f40-146">Přidejte následující zvýrazněný kód do souboru app.xaml.</span><span class="sxs-lookup"><span data-stu-id="c5f40-146">Add the following highlighted markup to app.xaml.</span></span>  
  
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
  
     <span data-ttu-id="c5f40-147">Přímo pod `Application.Resources` bloku, vytvoříte prostředek s názvem "GrayBlueGradientBrush".</span><span class="sxs-lookup"><span data-stu-id="c5f40-147">Directly under the `Application.Resources` block, you created a resource called "GrayBlueGradientBrush".</span></span> <span data-ttu-id="c5f40-148">Tento prostředek definuje vodorovný přechod.</span><span class="sxs-lookup"><span data-stu-id="c5f40-148">This resource defines a horizontal gradient.</span></span> <span data-ttu-id="c5f40-149">Tento prostředek může sloužit jako hodnotu vlastnosti z libovolného místa v aplikaci, včetně v style setter tlačítko pro <xref:System.Windows.Controls.Control.Background%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c5f40-149">This resource can be used as a property value from anywhere in the application, including inside the button style setter for the <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="c5f40-150">Teď k dispozici všechna tlačítka <xref:System.Windows.Controls.Control.Background%2A> hodnota vlastnosti tohoto přechodu.</span><span class="sxs-lookup"><span data-stu-id="c5f40-150">Now, all the buttons have a <xref:System.Windows.Controls.Control.Background%2A> property value of this gradient.</span></span>  
  
     <span data-ttu-id="c5f40-151">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c5f40-151">Press F5 to run the application.</span></span> <span data-ttu-id="c5f40-152">By měl vypadat nějak takto.</span><span class="sxs-lookup"><span data-stu-id="c5f40-152">It should look like the following.</span></span>  
  
     <span data-ttu-id="c5f40-153">![Tlačítka s barevného přechodu pozadí](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span><span class="sxs-lookup"><span data-stu-id="c5f40-153">![Buttons with a gradient background](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span></span>  
  
## <a name="create-a-template-that-defines-the-look-of-the-button"></a><span data-ttu-id="c5f40-154">Vytvořit šablonu, která definuje vzhled tlačítka</span><span class="sxs-lookup"><span data-stu-id="c5f40-154">Create a Template That Defines the Look of the Button</span></span>  
 <span data-ttu-id="c5f40-155">V této části vytvoříte šablonu, která se přizpůsobí vzhled tlačítka (prezentace).</span><span class="sxs-lookup"><span data-stu-id="c5f40-155">In this section, you create a template that customizes the appearance (presentation) of the button.</span></span> <span data-ttu-id="c5f40-156">Prezentace tlačítko se skládá z několika objektů včetně obdélníků a další součásti jedinečný vzhled na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="c5f40-156">The button presentation is made up of several objects including rectangles and other components to give the button a unique look.</span></span>  
  
 <span data-ttu-id="c5f40-157">Zatím kontrolou vzhled tlačítek v aplikaci má byla omezena změna vlastností tlačítka.</span><span class="sxs-lookup"><span data-stu-id="c5f40-157">So far, the control of how buttons look in the application has been confined to changing properties of the button.</span></span> <span data-ttu-id="c5f40-158">Co když chcete provést radikálnější změně vzhled tlačítka?</span><span class="sxs-lookup"><span data-stu-id="c5f40-158">What if you want to make more radical changes to the button's appearance?</span></span> <span data-ttu-id="c5f40-159">Šablony povolit výkonná kontrolu nad prezentaci objektu.</span><span class="sxs-lookup"><span data-stu-id="c5f40-159">Templates enable powerful control over the presentation of an object.</span></span> <span data-ttu-id="c5f40-160">Vzhledem k tomu, že šablony lze používat v rámci stylů, můžete použít šablonu pro všechny objekty, které styl platí (v tomto návodu tlačítka).</span><span class="sxs-lookup"><span data-stu-id="c5f40-160">Because templates can be used within styles, you can apply a template to all objects that the style applies to (in this walkthrough, the button).</span></span>  
  
#### <a name="to-use-the-template-to-define-the-look-of-the-button"></a><span data-ttu-id="c5f40-161">Použití šablony k definování vzhledu tlačítka</span><span class="sxs-lookup"><span data-stu-id="c5f40-161">To use the template to define the look of the button</span></span>  
  
1. <span data-ttu-id="c5f40-162">**Nastavení šablony:** Vzhledem k tomu, že ovládací prvky jako <xref:System.Windows.Controls.Button> mít <xref:System.Windows.Controls.Control.Template%2A> vlastností, můžete definovat hodnotu vlastnosti šablony, stejně jako jiné hodnoty vlastností jsme nastavili v <xref:System.Windows.Style> pomocí <xref:System.Windows.Setter>.</span><span class="sxs-lookup"><span data-stu-id="c5f40-162">**Set up the template:** Because controls like <xref:System.Windows.Controls.Button> have a <xref:System.Windows.Controls.Control.Template%2A> property, you can define the template property value just like the other property values we have set in a <xref:System.Windows.Style> using a <xref:System.Windows.Setter>.</span></span> <span data-ttu-id="c5f40-163">Přidejte následující zvýrazněný kód do vašeho styl tlačítka.</span><span class="sxs-lookup"><span data-stu-id="c5f40-163">Add the following highlighted markup to your button style.</span></span>  
  
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
  
2. <span data-ttu-id="c5f40-164">**Příkaz ALTER prezentace tlačítka:** V tomto okamžiku budete muset definovat šablony.</span><span class="sxs-lookup"><span data-stu-id="c5f40-164">**Alter button presentation:** At this point, you need to define the template.</span></span> <span data-ttu-id="c5f40-165">Přidejte následující zvýrazněný kód.</span><span class="sxs-lookup"><span data-stu-id="c5f40-165">Add the following highlighted markup.</span></span> <span data-ttu-id="c5f40-166">Tento kód určuje dvě <xref:System.Windows.Shapes.Rectangle> prvky s zaoblenými hranami, za nímž následuje <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="c5f40-166">This markup specifies two <xref:System.Windows.Shapes.Rectangle> elements with rounded edges, followed by a <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="c5f40-167"><xref:System.Windows.Controls.DockPanel> Slouží k hostiteli <xref:System.Windows.Controls.ContentPresenter> tlačítka.</span><span class="sxs-lookup"><span data-stu-id="c5f40-167">The <xref:System.Windows.Controls.DockPanel> is used to host the <xref:System.Windows.Controls.ContentPresenter> of the button.</span></span> <span data-ttu-id="c5f40-168">A <xref:System.Windows.Controls.ContentPresenter> zobrazí obsah tlačítka.</span><span class="sxs-lookup"><span data-stu-id="c5f40-168">A <xref:System.Windows.Controls.ContentPresenter> displays the content of the button.</span></span> <span data-ttu-id="c5f40-169">V tomto názorném postupu obsahu je text ("Tlačítko 1", "Tlačítko 2", "Tlačítko 3").</span><span class="sxs-lookup"><span data-stu-id="c5f40-169">In this walkthrough, the content is text ("Button 1", "Button 2", "Button 3").</span></span> <span data-ttu-id="c5f40-170">Všechny součásti šablony (obdélníků a <xref:System.Windows.Controls.DockPanel>) jsou rozloženy uvnitř <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="c5f40-170">All of the template components (the rectangles and the <xref:System.Windows.Controls.DockPanel>) are laid out inside of a <xref:System.Windows.Controls.Grid>.</span></span>  
  
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
  
     <span data-ttu-id="c5f40-171">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c5f40-171">Press F5 to run the application.</span></span> <span data-ttu-id="c5f40-172">By měl vypadat nějak takto.</span><span class="sxs-lookup"><span data-stu-id="c5f40-172">It should look like the following.</span></span>  
  
     <span data-ttu-id="c5f40-173">![](./media/custom-button-animatedbutton-4.gif "custom_button_AnimatedButton_4")</span><span class="sxs-lookup"><span data-stu-id="c5f40-173">![](./media/custom-button-animatedbutton-4.gif "custom_button_AnimatedButton_4")</span></span>  
  
3. <span data-ttu-id="c5f40-174">**Přidejte glasseffect do šablony:** Dále přidáte skla.</span><span class="sxs-lookup"><span data-stu-id="c5f40-174">**Add a glasseffect to the template:** Next you will add the glass.</span></span> <span data-ttu-id="c5f40-175">Nejprve vytvoříte některé prostředky, které vytvoření efektu přechodu skla.</span><span class="sxs-lookup"><span data-stu-id="c5f40-175">First you create some resources that create a glass gradient effect.</span></span> <span data-ttu-id="c5f40-176">Přidat tyto přechodu prostředky kdekoli v rámci `Application.Resources` blok:</span><span class="sxs-lookup"><span data-stu-id="c5f40-176">Add these gradient resources anywhere within the `Application.Resources` block:</span></span>  
  
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
  
     <span data-ttu-id="c5f40-177">Tyto prostředky se používají jako <xref:System.Windows.Shapes.Shape.Fill%2A> obdélníku, který jsme použít příkaz insert <xref:System.Windows.Controls.Grid> šablony tlačítka.</span><span class="sxs-lookup"><span data-stu-id="c5f40-177">These resources are used as the <xref:System.Windows.Shapes.Shape.Fill%2A> for a rectangle that we insert into the <xref:System.Windows.Controls.Grid> of the button template.</span></span> <span data-ttu-id="c5f40-178">Přidejte následující zvýrazněný kód do šablony.</span><span class="sxs-lookup"><span data-stu-id="c5f40-178">Add the following highlighted markup to the template.</span></span>  
  
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
  
     <span data-ttu-id="c5f40-179">Všimněte si, že <xref:System.Windows.UIElement.Opacity%2A> obdélníku s `x:Name` vlastnost "glassCube" je 0, takže při spuštění ukázky, se nezobrazí jako překryvný obrázek na horní části obdélníku lupy.</span><span class="sxs-lookup"><span data-stu-id="c5f40-179">Notice that the <xref:System.Windows.UIElement.Opacity%2A> of the rectangle with the `x:Name` property of "glassCube" is 0, so when you run the sample, you do not see the glass rectangle overlaid on top.</span></span> <span data-ttu-id="c5f40-180">Je to proto, že později přidáme aktivační procedury do šablon pro při interakci uživatele pomocí tlačítka.</span><span class="sxs-lookup"><span data-stu-id="c5f40-180">This is because we will later add triggers to the template for when the user interacts with the button.</span></span> <span data-ttu-id="c5f40-181">Však můžete zobrazit tlačítko vypadá nyní tak, že změníte <xref:System.Windows.UIElement.Opacity%2A> hodnotu 1 a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="c5f40-181">However, you can see what the button looks like now by changing the <xref:System.Windows.UIElement.Opacity%2A> value to 1 and running the application.</span></span> <span data-ttu-id="c5f40-182">Prohlédněte si následující obrázek.</span><span class="sxs-lookup"><span data-stu-id="c5f40-182">See the following figure.</span></span> <span data-ttu-id="c5f40-183">Než budete pokračovat k dalšímu kroku, změnit <xref:System.Windows.UIElement.Opacity%2A> zpět na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="c5f40-183">Before proceeding to the next step, change the <xref:System.Windows.UIElement.Opacity%2A> back to 0.</span></span>  
  
     <span data-ttu-id="c5f40-184">![Vlastní tlačítka, které se vytvořily pomocí XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="c5f40-184">![Custom buttons that were created by using XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>  
  
## <a name="create-button-interactivity"></a><span data-ttu-id="c5f40-185">Vytvářet tlačítka interakce</span><span class="sxs-lookup"><span data-stu-id="c5f40-185">Create Button Interactivity</span></span>  
 <span data-ttu-id="c5f40-186">V této části vytvoříte aktivační procedury vlastností a aktivační události změnit hodnoty vlastností a spuštění animace v reakci na akce uživatelů, například ukazatele myši nad tlačítkem a kliknutím na.</span><span class="sxs-lookup"><span data-stu-id="c5f40-186">In this section, you will create property triggers and event triggers to change property values and run animations in response to user actions such as moving the mouse pointer over the button and clicking.</span></span>  
  
 <span data-ttu-id="c5f40-187">Snadný způsob, jak přidat interaktivitu (myší nad, myši ponechat, klikněte na tlačítko a tak dále) je k definování triggerů v šabloně nebo stylu.</span><span class="sxs-lookup"><span data-stu-id="c5f40-187">An easy way to add interactivity (mouse-over, mouse-leave, click, and so on) is to define triggers within your template or style.</span></span> <span data-ttu-id="c5f40-188">Chcete-li vytvořit <xref:System.Windows.Trigger>, jako například definovat vlastnost "podmínku": Tlačítko <xref:System.Windows.UIElement.IsMouseOver%2A> hodnota vlastnosti je rovna `true`.</span><span class="sxs-lookup"><span data-stu-id="c5f40-188">To create a <xref:System.Windows.Trigger>, you define a property "condition" such as: The button <xref:System.Windows.UIElement.IsMouseOver%2A> property value is equal to `true`.</span></span> <span data-ttu-id="c5f40-189">Potom definujte metody setter (akce), které se použijí při aktivační podmínka pravdivá.</span><span class="sxs-lookup"><span data-stu-id="c5f40-189">You then define setters (actions) that take place when the trigger condition is true.</span></span>  
  
#### <a name="to-create-button-interactivity"></a><span data-ttu-id="c5f40-190">Chcete-li vytvořit tlačítko interaktivitu</span><span class="sxs-lookup"><span data-stu-id="c5f40-190">To create button interactivity</span></span>  
  
1. <span data-ttu-id="c5f40-191">**Přidání aktivačních událostí šablony:** Zvýrazněná značka se přidáte do šablony.</span><span class="sxs-lookup"><span data-stu-id="c5f40-191">**Add template triggers:** Add the highlighted markup to your template.</span></span>  
  
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
  
2. <span data-ttu-id="c5f40-192">**Přidáte aktivační procedury vlastností:** Přidat zvýrazněné značky `ControlTemplate.Triggers` blok:</span><span class="sxs-lookup"><span data-stu-id="c5f40-192">**Add property triggers:** Add the highlighted markup to the `ControlTemplate.Triggers` block:</span></span>  
  
    ```xaml
    <ControlTemplate.Triggers>  
  
      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>  
  
    <ControlTemplate.Triggers/>  
    ```  
  
     <span data-ttu-id="c5f40-193">Stisknutím klávesy F5 spusťte aplikaci a vidět její účinek spuštění ukazatele myši nad tlačítka.</span><span class="sxs-lookup"><span data-stu-id="c5f40-193">Press F5 to run the application and see the effect as you run the mouse pointer over the buttons.</span></span>  
  
3. <span data-ttu-id="c5f40-194">**Přidání triggeru fokus:** V dalším kroku přidáme několik podobné metody setter pro zpracování případu, když je fokus na tlačítko (například po na něj uživatel klikne).</span><span class="sxs-lookup"><span data-stu-id="c5f40-194">**Add a focus trigger:** Next, we'll add some similar setters to handle the case when the button has focus (for example, after the user clicks it).</span></span>  
  
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
  
     <span data-ttu-id="c5f40-195">Stisknutím klávesy F5 spusťte aplikaci a klikněte na jedno z tlačítek.</span><span class="sxs-lookup"><span data-stu-id="c5f40-195">Press F5 to run the application and click on one of the buttons.</span></span> <span data-ttu-id="c5f40-196">Všimněte si, že zůstane po kliknutí na jeho protože stále má fokus zvýrazněné tlačítko.</span><span class="sxs-lookup"><span data-stu-id="c5f40-196">Notice that the button stays highlighted after you click it because it still has focus.</span></span> <span data-ttu-id="c5f40-197">Pokud klepnete na tlačítko Další, nové tlačítko získá fokus, zatímco poslední z nich se ztratí.</span><span class="sxs-lookup"><span data-stu-id="c5f40-197">If you click another button, the new button gains focus while the last one loses it.</span></span>  
  
4. <span data-ttu-id="c5f40-198">**Přidání animace k** <xref:System.Windows.UIElement.MouseEnter> **a** <xref:System.Windows.UIElement.MouseLeave> **:** Vedle přidáme některé animace aktivačních událostí.</span><span class="sxs-lookup"><span data-stu-id="c5f40-198">**Add animations for**  <xref:System.Windows.UIElement.MouseEnter> **and** <xref:System.Windows.UIElement.MouseLeave> **:** Next we add some animations to the triggers.</span></span> <span data-ttu-id="c5f40-199">Přidejte následující kód, kdekoli uvnitř sady `ControlTemplate.Triggers` bloku.</span><span class="sxs-lookup"><span data-stu-id="c5f40-199">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block.</span></span>  
  
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
  
     <span data-ttu-id="c5f40-200">Obdélník lupy se zmenší, pokud ukazatel myši přesune na tlačítko a vrátí zpět na normální velikosti, když ukazatel opustí.</span><span class="sxs-lookup"><span data-stu-id="c5f40-200">The glass rectangle shrinks when the mouse pointer moves over the button and returns back to normal size when the pointer leaves.</span></span>  
  
     <span data-ttu-id="c5f40-201">Existují dva animace, které se zobrazí, když ukazatel myši překročí tlačítka (<xref:System.Windows.UIElement.MouseEnter> událost je aktivována).</span><span class="sxs-lookup"><span data-stu-id="c5f40-201">There are two animations that are triggered when the pointer goes over the button (<xref:System.Windows.UIElement.MouseEnter> event is raised).</span></span> <span data-ttu-id="c5f40-202">Tyto animace budete zmenšit skla obdélník na ose X a Y.</span><span class="sxs-lookup"><span data-stu-id="c5f40-202">These animations shrink the glass rectangle along the X and Y axis.</span></span> <span data-ttu-id="c5f40-203">Všimněte si, že vlastnosti na <xref:System.Windows.Media.Animation.DoubleAnimation> prvky – <xref:System.Windows.Media.Animation.Timeline.Duration%2A> a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.</span><span class="sxs-lookup"><span data-stu-id="c5f40-203">Notice the properties on the <xref:System.Windows.Media.Animation.DoubleAnimation> elements — <xref:System.Windows.Media.Animation.Timeline.Duration%2A> and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.</span></span> <span data-ttu-id="c5f40-204"><xref:System.Windows.Media.Animation.Timeline.Duration%2A> Určuje, zda animace vyskytuje více než půl sekundy, a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> Určuje, že zmenšuje skla 10 %.</span><span class="sxs-lookup"><span data-stu-id="c5f40-204">The <xref:System.Windows.Media.Animation.Timeline.Duration%2A> specifies that the animation occurs over half a second, and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> specifies that the glass shrinks by 10%.</span></span>  
  
     <span data-ttu-id="c5f40-205">Druhý aktivační procedura událostí (<xref:System.Windows.UIElement.MouseLeave>) jednoduše zastaví první z nich.</span><span class="sxs-lookup"><span data-stu-id="c5f40-205">The second event trigger (<xref:System.Windows.UIElement.MouseLeave>) simply stops the first one.</span></span> <span data-ttu-id="c5f40-206">Při zastavení <xref:System.Windows.Media.Animation.Storyboard>, animované vlastnosti vrátit na výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c5f40-206">When you stop a <xref:System.Windows.Media.Animation.Storyboard>, all the animated properties return to their default values.</span></span> <span data-ttu-id="c5f40-207">Proto když uživatel přesune ukazatel mimo tlačítko, na tlačítko se vrátí způsobu, jakým byl před přesunutím ukazatele myši nad tlačítkem.</span><span class="sxs-lookup"><span data-stu-id="c5f40-207">Therefore, when the user moves the pointer off the button, the button goes back to the way it was before the mouse pointer moved over the button.</span></span> <span data-ttu-id="c5f40-208">Další informace o animacích naleznete v tématu [přehled animace](../graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c5f40-208">For more information about animations, see [Animation Overview](../graphics-multimedia/animation-overview.md).</span></span>  
  
5. <span data-ttu-id="c5f40-209">**Přidání animace k po kliknutí na tlačítko:** Posledním krokem je přidání triggeru pro, když uživatel klikne na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="c5f40-209">**Add an animation for when the button is clicked:** The final step is to add a trigger for when the user clicks the button.</span></span> <span data-ttu-id="c5f40-210">Přidejte následující kód, kdekoli uvnitř sady `ControlTemplate.Triggers` blok:</span><span class="sxs-lookup"><span data-stu-id="c5f40-210">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block:</span></span>  
  
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
  
     <span data-ttu-id="c5f40-211">Stisknutím klávesy F5 spusťte aplikaci a klikněte na jedno z tlačítek.</span><span class="sxs-lookup"><span data-stu-id="c5f40-211">Press F5 to run the application, and click one of the buttons.</span></span> <span data-ttu-id="c5f40-212">Po kliknutí na tlačítko lupy obdélník přede kolem.</span><span class="sxs-lookup"><span data-stu-id="c5f40-212">When you click a button, the glass rectangle spins around.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="c5f40-213">Souhrn</span><span class="sxs-lookup"><span data-stu-id="c5f40-213">Summary</span></span>  
 <span data-ttu-id="c5f40-214">V tomto návodu jste provedli následující praktická cvičení:</span><span class="sxs-lookup"><span data-stu-id="c5f40-214">In this walkthrough, you performed the following exercises:</span></span>  
  
-   <span data-ttu-id="c5f40-215">Cílené <xref:System.Windows.Style> s typem objektu (<xref:System.Windows.Controls.Button>).</span><span class="sxs-lookup"><span data-stu-id="c5f40-215">Targeted a <xref:System.Windows.Style> to an object type (<xref:System.Windows.Controls.Button>).</span></span>  
  
-   <span data-ttu-id="c5f40-216">Řídí základní vlastnosti v celé aplikaci pomocí tlačítek <xref:System.Windows.Style>.</span><span class="sxs-lookup"><span data-stu-id="c5f40-216">Controlled basic properties of the buttons in the entire application using the <xref:System.Windows.Style>.</span></span>  
  
-   <span data-ttu-id="c5f40-217">Vytvoření zdroje, jako jsou přechody pro hodnoty vlastností <xref:System.Windows.Style> funkce setter.</span><span class="sxs-lookup"><span data-stu-id="c5f40-217">Created resources like gradients to use for property values of the <xref:System.Windows.Style> setters.</span></span>  
  
-   <span data-ttu-id="c5f40-218">Použití šablony tlačítka Upravit vzhled tlačítka v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c5f40-218">Customized the look of buttons in the entire application by applying a template to the buttons.</span></span>  
  
-   <span data-ttu-id="c5f40-219">Přizpůsobit chování pro tlačítka v reakci na akce uživatele (například <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>, a <xref:System.Windows.Controls.Primitives.ButtonBase.Click>), které obsahovat efekty animace.</span><span class="sxs-lookup"><span data-stu-id="c5f40-219">Customized behavior for the buttons in response to user actions (such as <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>, and <xref:System.Windows.Controls.Primitives.ButtonBase.Click>) that included animation effects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5f40-220">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c5f40-220">See also</span></span>

- [<span data-ttu-id="c5f40-221">Vytvoření tlačítka pomocí nástroje Microsoft Expression Blend</span><span class="sxs-lookup"><span data-stu-id="c5f40-221">Create a Button by Using Microsoft Expression Blend</span></span>](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)
- [<span data-ttu-id="c5f40-222">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="c5f40-222">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="c5f40-223">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="c5f40-223">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="c5f40-224">Přehled malování plnými barvami a přechody</span><span class="sxs-lookup"><span data-stu-id="c5f40-224">Painting with Solid Colors and Gradients Overview</span></span>](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="c5f40-225">Přehled efektů bitmap</span><span class="sxs-lookup"><span data-stu-id="c5f40-225">Bitmap Effects Overview</span></span>](../graphics-multimedia/bitmap-effects-overview.md)
