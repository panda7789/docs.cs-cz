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
# <a name="walkthrough-create-a-button-by-using-xaml"></a><span data-ttu-id="07dd1-102">Návod: Vytvoření tlačítka použitím XAML</span><span class="sxs-lookup"><span data-stu-id="07dd1-102">Walkthrough: Create a Button by Using XAML</span></span>

<span data-ttu-id="07dd1-103">Cílem tohoto návodu je zjistit, jak vytvořit animované tlačítko pro použití v aplikaci WPF (Windows Presentation Foundation).</span><span class="sxs-lookup"><span data-stu-id="07dd1-103">The objective of this walkthrough is to learn how to create an animated button for use in a Windows Presentation Foundation (WPF) application.</span></span> <span data-ttu-id="07dd1-104">Tento návod používá styly a šablonu k vytvoření přizpůsobeného prostředku tlačítka, který umožňuje opakované použití kódu a oddělení logiky tlačítka z deklarace tlačítka.</span><span class="sxs-lookup"><span data-stu-id="07dd1-104">This walkthrough uses styles and a template to create a customized button resource that allows reuse of code and separation of button logic from the button declaration.</span></span> <span data-ttu-id="07dd1-105">Tento návod je napsán [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]zcela v .</span><span class="sxs-lookup"><span data-stu-id="07dd1-105">This walkthrough is written entirely in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>

> [!IMPORTANT]
> <span data-ttu-id="07dd1-106">Tento návod vás provede kroky pro vytvoření aplikace zadáním nebo [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] zkopírováním a vložením do sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="07dd1-106">This walkthrough guides you through the steps for creating the application by typing or copying and pasting [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] into Visual Studio.</span></span> <span data-ttu-id="07dd1-107">Pokud chcete se dozvědět, jak pomocí návrháře vytvořit stejnou aplikaci, naleznete v [tématu Vytvoření tlačítka pomocí prolnutí výrazů společnosti Microsoft](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).</span><span class="sxs-lookup"><span data-stu-id="07dd1-107">If you would prefer to learn how to use a designer to create the same application, see [Create a Button by Using Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).</span></span>

<span data-ttu-id="07dd1-108">Následující obrázek znázorňuje dokončená tlačítka.</span><span class="sxs-lookup"><span data-stu-id="07dd1-108">The following figure shows the finished buttons.</span></span>

<span data-ttu-id="07dd1-109">![Vlastní tlačítka, která byla vytvořena pomocí xaml](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="07dd1-109">![Custom buttons that were created by using XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>

## <a name="create-basic-buttons"></a><span data-ttu-id="07dd1-110">Vytvořit základní tlačítka</span><span class="sxs-lookup"><span data-stu-id="07dd1-110">Create Basic Buttons</span></span>

<span data-ttu-id="07dd1-111">Začněme vytvořením nového projektu a přidáním několika tlačítek do okna.</span><span class="sxs-lookup"><span data-stu-id="07dd1-111">Let's start by creating a new project and adding a few buttons to the window.</span></span>

### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a><span data-ttu-id="07dd1-112">Vytvoření nového projektu WPF a přidání tlačítek do okna</span><span class="sxs-lookup"><span data-stu-id="07dd1-112">To create a new WPF project and add buttons to the window</span></span>

1. <span data-ttu-id="07dd1-113">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="07dd1-113">Start Visual Studio.</span></span>

2. <span data-ttu-id="07dd1-114">**Vytvořte nový projekt WPF:** V nabídce **Soubor** přejděte na **Nový**a potom klepněte na **položku Project**.</span><span class="sxs-lookup"><span data-stu-id="07dd1-114">**Create a new WPF project:** On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="07dd1-115">Najděte šablonu **aplikace systému Windows (WPF)** a pojmenujte projekt "AnimatedButton".</span><span class="sxs-lookup"><span data-stu-id="07dd1-115">Find the **Windows Application (WPF)** template and name the project "AnimatedButton".</span></span> <span data-ttu-id="07dd1-116">Tím se vytvoří kostra pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="07dd1-116">This will create the skeleton for the application.</span></span>

3. <span data-ttu-id="07dd1-117">**Přidejte základní výchozí tlačítka:** Všechny soubory, které potřebujete pro tento návod jsou poskytovány šablonou.</span><span class="sxs-lookup"><span data-stu-id="07dd1-117">**Add basic default buttons:** All the files you need for this walkthrough are provided by the template.</span></span> <span data-ttu-id="07dd1-118">Otevřete soubor Window1.xaml poklepáním v Průzkumníku řešení.</span><span class="sxs-lookup"><span data-stu-id="07dd1-118">Open the Window1.xaml file by double clicking it in Solution Explorer.</span></span> <span data-ttu-id="07dd1-119">Ve výchozím nastavení <xref:System.Windows.Controls.Grid> je prvek v Window1.xaml.</span><span class="sxs-lookup"><span data-stu-id="07dd1-119">By default, there is a <xref:System.Windows.Controls.Grid> element in Window1.xaml.</span></span> <span data-ttu-id="07dd1-120">Odeberte <xref:System.Windows.Controls.Grid> prvek a přidejte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] na stránku několik tlačítek zadáním nebo zkopírováním a vložením následujícího zvýrazněného kódu do okna 1.xaml:</span><span class="sxs-lookup"><span data-stu-id="07dd1-120">Remove the <xref:System.Windows.Controls.Grid> element and add a few buttons to the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page by typing or copy and pasting the following highlighted code to Window1.xaml:</span></span>

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

     <span data-ttu-id="07dd1-121">Stisknutím klávesy F5 spusťte aplikaci. měli byste vidět sadu tlačítek, která vypadá jako na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="07dd1-121">Press F5 to run the application; you should see a set of buttons that looks like the following figure.</span></span>

     <span data-ttu-id="07dd1-122">![Tři základní tlačítka](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span><span class="sxs-lookup"><span data-stu-id="07dd1-122">![Three basic buttons](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span></span>

     <span data-ttu-id="07dd1-123">Nyní, když jste vytvořili základní tlačítka, jste dokončili práci v souboru Window1.xaml.</span><span class="sxs-lookup"><span data-stu-id="07dd1-123">Now that you have created the basic buttons, you are finished working in the Window1.xaml file.</span></span> <span data-ttu-id="07dd1-124">Zbytek návodu se zaměřuje na soubor app.xaml, definování stylů a šablonu pro tlačítka.</span><span class="sxs-lookup"><span data-stu-id="07dd1-124">The rest of the walkthrough focuses on the app.xaml file, defining styles and a template for the buttons.</span></span>

## <a name="set-basic-properties"></a><span data-ttu-id="07dd1-125">Nastavení základních vlastností</span><span class="sxs-lookup"><span data-stu-id="07dd1-125">Set Basic Properties</span></span>

<span data-ttu-id="07dd1-126">Dále nastavíme některé vlastnosti těchto tlačítek, abybylo řízení vzhledu a rozložení tlačítka.</span><span class="sxs-lookup"><span data-stu-id="07dd1-126">Next, let's set some properties on these buttons to control the button appearance and layout.</span></span> <span data-ttu-id="07dd1-127">Místo nastavování vlastností na tlačítkách jednotlivě použijete prostředky k definování vlastností tlačítek pro celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="07dd1-127">Rather than setting properties on the buttons individually, you will use resources to define button properties for the entire application.</span></span> <span data-ttu-id="07dd1-128">Aplikační prostředky jsou koncepčně podobné externím kaskádovým šablonám stylů CSS (CSS) pro webové stránky; prostředky jsou však mnohem výkonnější než kaskádové šablony stylů (CSS), jak uvidíte na konci tohoto návodu.</span><span class="sxs-lookup"><span data-stu-id="07dd1-128">Application resources are conceptually similar to external Cascading Style Sheets (CSS) for Web pages; however, resources are much more powerful than Cascading Style Sheets (CSS), as you will see by the end of this walkthrough.</span></span> <span data-ttu-id="07dd1-129">Další informace o prostředcích naleznete v tématu [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span><span class="sxs-lookup"><span data-stu-id="07dd1-129">To learn more about resources, see [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>

### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a><span data-ttu-id="07dd1-130">Použití stylů k nastavení základních vlastností tlačítek</span><span class="sxs-lookup"><span data-stu-id="07dd1-130">To use styles to set basic properties on the buttons</span></span>

1. <span data-ttu-id="07dd1-131">**Definujte blok Application.Resources:** Otevřete soubor app.xaml a přidejte následující zvýrazněné značky, pokud k ní ještě není:</span><span class="sxs-lookup"><span data-stu-id="07dd1-131">**Define an Application.Resources block:** Open app.xaml and add the following highlighted markup if it is not already there:</span></span>

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

     <span data-ttu-id="07dd1-132">Obor prostředků je určen tím, kde definujete prostředek.</span><span class="sxs-lookup"><span data-stu-id="07dd1-132">Resource scope is determined by where you define the resource.</span></span> <span data-ttu-id="07dd1-133">Definování prostředků `Application.Resources` v souboru app.xaml umožňuje prostředek použít z libovolného místa v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="07dd1-133">Defining resources in `Application.Resources` in the app.xaml file enables the resource to be used from anywhere in the application.</span></span> <span data-ttu-id="07dd1-134">Další informace o definování rozsahu prostředků naleznete v tématu [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span><span class="sxs-lookup"><span data-stu-id="07dd1-134">To learn more about defining the scope of your resources, see [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>

2. <span data-ttu-id="07dd1-135">**Vytvořte styl a definujte s ním základní hodnoty vlastností:** Přidejte do bloku `Application.Resources` následující značky.</span><span class="sxs-lookup"><span data-stu-id="07dd1-135">**Create a style and define basic property values with it:** Add the following markup to the `Application.Resources` block.</span></span> <span data-ttu-id="07dd1-136">Tato značka vytvoří, <xref:System.Windows.Style> která platí pro všechna tlačítka <xref:System.Windows.FrameworkElement.Width%2A> v aplikaci, nastavení <xref:System.Windows.FrameworkElement.Margin%2A> tlačítek na 90 a na 10:</span><span class="sxs-lookup"><span data-stu-id="07dd1-136">This markup creates a <xref:System.Windows.Style> that applies to all buttons in the application, setting the <xref:System.Windows.FrameworkElement.Width%2A> of the buttons to 90 and the <xref:System.Windows.FrameworkElement.Margin%2A> to 10:</span></span>

    ```xaml
    <Application.Resources>
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>
    </Application.Resources>
    ```

     <span data-ttu-id="07dd1-137">Vlastnost <xref:System.Windows.Style.TargetType%2A> určuje, že styl platí pro všechny <xref:System.Windows.Controls.Button>objekty typu .</span><span class="sxs-lookup"><span data-stu-id="07dd1-137">The <xref:System.Windows.Style.TargetType%2A> property specifies that the style applies to all objects of type <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="07dd1-138">Každý <xref:System.Windows.Setter> nastaví jinou <xref:System.Windows.Style>hodnotu vlastnosti pro .</span><span class="sxs-lookup"><span data-stu-id="07dd1-138">Each <xref:System.Windows.Setter> sets a different property value for the <xref:System.Windows.Style>.</span></span> <span data-ttu-id="07dd1-139">Proto v tomto okamžiku každé tlačítko v aplikaci má šířku 90 a rozpětí 10.</span><span class="sxs-lookup"><span data-stu-id="07dd1-139">Therefore, at this point every button in the application has a width of 90 and a margin of 10.</span></span>  <span data-ttu-id="07dd1-140">Pokud stisknete klávesu F5 a spustíte aplikaci, zobrazí se následující okno.</span><span class="sxs-lookup"><span data-stu-id="07dd1-140">If you press F5 to run the application, you see the following window.</span></span>

     <span data-ttu-id="07dd1-141">![Tlačítka o šířce 90 a okraji 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span><span class="sxs-lookup"><span data-stu-id="07dd1-141">![Buttons with a width of 90 and a margin of 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span></span>

     <span data-ttu-id="07dd1-142">Existuje mnohem více, co můžete udělat se styly, včetně různých způsobů, jak doladit, jaké objekty jsou cílené, určení komplexních hodnot vlastností a dokonce i použití stylů jako vstupu pro jiné styly.</span><span class="sxs-lookup"><span data-stu-id="07dd1-142">There is much more you can do with styles, including a variety of ways to fine-tune what objects are targeted, specifying complex property values, and even using styles as input for other styles.</span></span> <span data-ttu-id="07dd1-143">Další informace naleznete [v tématu Styling a Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="07dd1-143">For more information, see [Styling and Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

3. <span data-ttu-id="07dd1-144">**Nastavte hodnotu vlastnosti stylu na prostředek:** Prostředky umožňují jednoduchý způsob opakovaného použití běžně definovaných objektů a hodnot.</span><span class="sxs-lookup"><span data-stu-id="07dd1-144">**Set a style property value to a resource:** Resources enable a simple way to reuse commonly defined objects and values.</span></span> <span data-ttu-id="07dd1-145">Je zvláště užitečné definovat složité hodnoty pomocí prostředků, aby váš kód více modulární.</span><span class="sxs-lookup"><span data-stu-id="07dd1-145">It is especially useful to define complex values using resources to make your code more modular.</span></span> <span data-ttu-id="07dd1-146">Do souboru app.xaml přidejte následující zvýrazněné značky.</span><span class="sxs-lookup"><span data-stu-id="07dd1-146">Add the following highlighted markup to app.xaml.</span></span>

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

     <span data-ttu-id="07dd1-147">Přímo pod `Application.Resources` blokem jste vytvořili prostředek s názvem "GrayBlueGradientBrush".</span><span class="sxs-lookup"><span data-stu-id="07dd1-147">Directly under the `Application.Resources` block, you created a resource called "GrayBlueGradientBrush".</span></span> <span data-ttu-id="07dd1-148">Tento prostředek definuje vodorovný přechod.</span><span class="sxs-lookup"><span data-stu-id="07dd1-148">This resource defines a horizontal gradient.</span></span> <span data-ttu-id="07dd1-149">Tento prostředek lze použít jako hodnotu vlastnosti z libovolného místa v <xref:System.Windows.Controls.Control.Background%2A> aplikaci, včetně uvnitř setter stylu tlačítka pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="07dd1-149">This resource can be used as a property value from anywhere in the application, including inside the button style setter for the <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="07dd1-150">Nyní všechna tlačítka mají <xref:System.Windows.Controls.Control.Background%2A> hodnotu vlastnosti tohoto přechodu.</span><span class="sxs-lookup"><span data-stu-id="07dd1-150">Now, all the buttons have a <xref:System.Windows.Controls.Control.Background%2A> property value of this gradient.</span></span>

     <span data-ttu-id="07dd1-151">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="07dd1-151">Press F5 to run the application.</span></span> <span data-ttu-id="07dd1-152">Mělo by to vypadat takto.</span><span class="sxs-lookup"><span data-stu-id="07dd1-152">It should look like the following.</span></span>

     <span data-ttu-id="07dd1-153">![Tlačítka s pozadím přechodu](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span><span class="sxs-lookup"><span data-stu-id="07dd1-153">![Buttons with a gradient background](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span></span>

## <a name="create-a-template-that-defines-the-look-of-the-button"></a><span data-ttu-id="07dd1-154">Vytvoření šablony, která definuje vzhled tlačítka</span><span class="sxs-lookup"><span data-stu-id="07dd1-154">Create a Template That Defines the Look of the Button</span></span>

<span data-ttu-id="07dd1-155">V této části vytvoříte šablonu, která přizpůsobí vzhled (prezentaci) tlačítka.</span><span class="sxs-lookup"><span data-stu-id="07dd1-155">In this section, you create a template that customizes the appearance (presentation) of the button.</span></span> <span data-ttu-id="07dd1-156">Prezentace tlačítka se skládá z několika objektů, včetně obdélníků a dalších komponent, aby tlačítko jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="07dd1-156">The button presentation is made up of several objects including rectangles and other components to give the button a unique look.</span></span>

<span data-ttu-id="07dd1-157">Zatím ovládací prvek, jak tlačítka vypadají v aplikaci byla omezena na změnu vlastností tlačítka.</span><span class="sxs-lookup"><span data-stu-id="07dd1-157">So far, the control of how buttons look in the application has been confined to changing properties of the button.</span></span> <span data-ttu-id="07dd1-158">Co když chcete provést radikálnější změny vzhledu tlačítka?</span><span class="sxs-lookup"><span data-stu-id="07dd1-158">What if you want to make more radical changes to the button's appearance?</span></span> <span data-ttu-id="07dd1-159">Šablony umožňují výkonnou kontrolu nad prezentací objektu.</span><span class="sxs-lookup"><span data-stu-id="07dd1-159">Templates enable powerful control over the presentation of an object.</span></span> <span data-ttu-id="07dd1-160">Vzhledem k tomu, že šablony lze použít v rámci stylů, můžete použít šablonu pro všechny objekty, které styl platí pro (v tomto návodu, tlačítko).</span><span class="sxs-lookup"><span data-stu-id="07dd1-160">Because templates can be used within styles, you can apply a template to all objects that the style applies to (in this walkthrough, the button).</span></span>

### <a name="to-use-the-template-to-define-the-look-of-the-button"></a><span data-ttu-id="07dd1-161">Použití šablony k definování vzhledu tlačítka</span><span class="sxs-lookup"><span data-stu-id="07dd1-161">To use the template to define the look of the button</span></span>

1. <span data-ttu-id="07dd1-162">**Nastavte šablonu:** Vzhledem <xref:System.Windows.Controls.Button> k <xref:System.Windows.Controls.Control.Template%2A> tomu, že ovládací prvky jako mají vlastnost, můžete definovat <xref:System.Windows.Style> hodnotu vlastnosti šablony stejně jako ostatní hodnoty vlastností, které jsme nastavili v použití <xref:System.Windows.Setter>.</span><span class="sxs-lookup"><span data-stu-id="07dd1-162">**Set up the template:** Because controls like <xref:System.Windows.Controls.Button> have a <xref:System.Windows.Controls.Control.Template%2A> property, you can define the template property value just like the other property values we have set in a <xref:System.Windows.Style> using a <xref:System.Windows.Setter>.</span></span> <span data-ttu-id="07dd1-163">Přidejte následující zvýrazněné značky do stylu tlačítka.</span><span class="sxs-lookup"><span data-stu-id="07dd1-163">Add the following highlighted markup to your button style.</span></span>

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

2. <span data-ttu-id="07dd1-164">**Změnit prezentaci tlačítka:** V tomto okamžiku je třeba definovat šablonu.</span><span class="sxs-lookup"><span data-stu-id="07dd1-164">**Alter button presentation:** At this point, you need to define the template.</span></span> <span data-ttu-id="07dd1-165">Přidejte následující zvýrazněné značky.</span><span class="sxs-lookup"><span data-stu-id="07dd1-165">Add the following highlighted markup.</span></span> <span data-ttu-id="07dd1-166">Tato značka určuje <xref:System.Windows.Shapes.Rectangle> dva prvky se zaoblenými hranami, následované <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="07dd1-166">This markup specifies two <xref:System.Windows.Shapes.Rectangle> elements with rounded edges, followed by a <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="07dd1-167">Slouží <xref:System.Windows.Controls.DockPanel> k hostování <xref:System.Windows.Controls.ContentPresenter> tlačítka.</span><span class="sxs-lookup"><span data-stu-id="07dd1-167">The <xref:System.Windows.Controls.DockPanel> is used to host the <xref:System.Windows.Controls.ContentPresenter> of the button.</span></span> <span data-ttu-id="07dd1-168">A <xref:System.Windows.Controls.ContentPresenter> zobrazí obsah tlačítka.</span><span class="sxs-lookup"><span data-stu-id="07dd1-168">A <xref:System.Windows.Controls.ContentPresenter> displays the content of the button.</span></span> <span data-ttu-id="07dd1-169">V tomto návodu je obsahem text ("Tlačítko 1", "Tlačítko 2", "Tlačítko 3").</span><span class="sxs-lookup"><span data-stu-id="07dd1-169">In this walkthrough, the content is text ("Button 1", "Button 2", "Button 3").</span></span> <span data-ttu-id="07dd1-170">Všechny součásti šablony (obdélníky a <xref:System.Windows.Controls.DockPanel>) jsou umístěny <xref:System.Windows.Controls.Grid>uvnitř .</span><span class="sxs-lookup"><span data-stu-id="07dd1-170">All of the template components (the rectangles and the <xref:System.Windows.Controls.DockPanel>) are laid out inside of a <xref:System.Windows.Controls.Grid>.</span></span>

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

     <span data-ttu-id="07dd1-171">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="07dd1-171">Press F5 to run the application.</span></span> <span data-ttu-id="07dd1-172">Mělo by to vypadat takto.</span><span class="sxs-lookup"><span data-stu-id="07dd1-172">It should look like the following.</span></span>

     ![Okno se 3 tlačítky](./media/custom-button-animatedbutton-4.gif)

3. <span data-ttu-id="07dd1-174">**Přidejte glasseffect do šablony:** Dále přidáte sklenici.</span><span class="sxs-lookup"><span data-stu-id="07dd1-174">**Add a glasseffect to the template:** Next you will add the glass.</span></span> <span data-ttu-id="07dd1-175">Nejprve vytvoříte některé prostředky, které vytvoří efekt sklonu skla.</span><span class="sxs-lookup"><span data-stu-id="07dd1-175">First you create some resources that create a glass gradient effect.</span></span> <span data-ttu-id="07dd1-176">Přidejte tyto prostředky `Application.Resources` přechodu kdekoli v bloku:</span><span class="sxs-lookup"><span data-stu-id="07dd1-176">Add these gradient resources anywhere within the `Application.Resources` block:</span></span>

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

     <span data-ttu-id="07dd1-177">Tyto prostředky se <xref:System.Windows.Shapes.Shape.Fill%2A> používají jako pro obdélník, <xref:System.Windows.Controls.Grid> který vložíme do šablony tlačítka.</span><span class="sxs-lookup"><span data-stu-id="07dd1-177">These resources are used as the <xref:System.Windows.Shapes.Shape.Fill%2A> for a rectangle that we insert into the <xref:System.Windows.Controls.Grid> of the button template.</span></span> <span data-ttu-id="07dd1-178">Přidejte do šablony následující zvýrazněné značky.</span><span class="sxs-lookup"><span data-stu-id="07dd1-178">Add the following highlighted markup to the template.</span></span>

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

     <span data-ttu-id="07dd1-179">Všimněte <xref:System.Windows.UIElement.Opacity%2A> si, že `x:Name` obdélník s vlastností "glassCube" je 0, takže při spuštění vzorku, nevidíte skleněný obdélník překrytý nahoře.</span><span class="sxs-lookup"><span data-stu-id="07dd1-179">Notice that the <xref:System.Windows.UIElement.Opacity%2A> of the rectangle with the `x:Name` property of "glassCube" is 0, so when you run the sample, you do not see the glass rectangle overlaid on top.</span></span> <span data-ttu-id="07dd1-180">Je to proto, že později přidáme aktivační události do šablony, když uživatel interaguje s tlačítkem.</span><span class="sxs-lookup"><span data-stu-id="07dd1-180">This is because we will later add triggers to the template for when the user interacts with the button.</span></span> <span data-ttu-id="07dd1-181">Můžete však vidět, jak tlačítko vypadá <xref:System.Windows.UIElement.Opacity%2A> nyní změnou hodnoty na 1 a spuštěním aplikace.</span><span class="sxs-lookup"><span data-stu-id="07dd1-181">However, you can see what the button looks like now by changing the <xref:System.Windows.UIElement.Opacity%2A> value to 1 and running the application.</span></span> <span data-ttu-id="07dd1-182">Prohlédněte si následující obrázek.</span><span class="sxs-lookup"><span data-stu-id="07dd1-182">See the following figure.</span></span> <span data-ttu-id="07dd1-183">Než přesete další krok, změňte zadní na <xref:System.Windows.UIElement.Opacity%2A> 0.</span><span class="sxs-lookup"><span data-stu-id="07dd1-183">Before proceeding to the next step, change the <xref:System.Windows.UIElement.Opacity%2A> back to 0.</span></span>

     <span data-ttu-id="07dd1-184">![Vlastní tlačítka, která byla vytvořena pomocí xaml](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="07dd1-184">![Custom buttons that were created by using XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>

## <a name="create-button-interactivity"></a><span data-ttu-id="07dd1-185">Vytvořit interaktivitu tlačítka</span><span class="sxs-lookup"><span data-stu-id="07dd1-185">Create Button Interactivity</span></span>

<span data-ttu-id="07dd1-186">V této části vytvoříte aktivační události vlastností a aktivační události pro změnu hodnot vlastností a spuštění animací v reakci na akce uživatele, jako je přesunutí ukazatele myši nad tlačítko a kliknutí.</span><span class="sxs-lookup"><span data-stu-id="07dd1-186">In this section, you will create property triggers and event triggers to change property values and run animations in response to user actions such as moving the mouse pointer over the button and clicking.</span></span>

<span data-ttu-id="07dd1-187">Snadný způsob, jak přidat interaktivitu (přejet myší, přejet myší, kliknout a tak dále) je definovat aktivační události v šabloně nebo stylu.</span><span class="sxs-lookup"><span data-stu-id="07dd1-187">An easy way to add interactivity (mouse-over, mouse-leave, click, and so on) is to define triggers within your template or style.</span></span> <span data-ttu-id="07dd1-188">Chcete-li <xref:System.Windows.Trigger>vytvořit , definujete vlastnost "podmínka", například: Hodnota vlastnosti button <xref:System.Windows.UIElement.IsMouseOver%2A> je rovna `true`.</span><span class="sxs-lookup"><span data-stu-id="07dd1-188">To create a <xref:System.Windows.Trigger>, you define a property "condition" such as: The button <xref:System.Windows.UIElement.IsMouseOver%2A> property value is equal to `true`.</span></span> <span data-ttu-id="07dd1-189">Potom definujete nastavení (akce), které se uskuteční, když je podmínka aktivační události true.</span><span class="sxs-lookup"><span data-stu-id="07dd1-189">You then define setters (actions) that take place when the trigger condition is true.</span></span>

### <a name="to-create-button-interactivity"></a><span data-ttu-id="07dd1-190">Vytvoření interaktivity tlačítek</span><span class="sxs-lookup"><span data-stu-id="07dd1-190">To create button interactivity</span></span>

1. <span data-ttu-id="07dd1-191">**Přidat aktivační události šablony:** Přidejte zvýrazněné značky do šablony.</span><span class="sxs-lookup"><span data-stu-id="07dd1-191">**Add template triggers:** Add the highlighted markup to your template.</span></span>

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

2. <span data-ttu-id="07dd1-192">**Přidat aktivační události vlastností:** Přidejte zvýrazněné značky `ControlTemplate.Triggers` do bloku:</span><span class="sxs-lookup"><span data-stu-id="07dd1-192">**Add property triggers:** Add the highlighted markup to the `ControlTemplate.Triggers` block:</span></span>

    ```xaml
    <ControlTemplate.Triggers>

      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>

    <ControlTemplate.Triggers/>
    ```

     <span data-ttu-id="07dd1-193">Stisknutím klávesy F5 spusťte aplikaci a uvidíte efekt při spuštění ukazatele myši nad tlačítky.</span><span class="sxs-lookup"><span data-stu-id="07dd1-193">Press F5 to run the application and see the effect as you run the mouse pointer over the buttons.</span></span>

3. <span data-ttu-id="07dd1-194">**Přidejte aktivační událost fokusu:** Dále přidáme některé podobné nastavení pro zpracování případu, když má tlačítko fokus (například poté, co na něj uživatel klikne).</span><span class="sxs-lookup"><span data-stu-id="07dd1-194">**Add a focus trigger:** Next, we'll add some similar setters to handle the case when the button has focus (for example, after the user clicks it).</span></span>

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

     <span data-ttu-id="07dd1-195">Stisknutím klávesy F5 spusťte aplikaci a klikněte na jedno z tlačítek.</span><span class="sxs-lookup"><span data-stu-id="07dd1-195">Press F5 to run the application and click on one of the buttons.</span></span> <span data-ttu-id="07dd1-196">Všimněte si, že tlačítko zůstane zvýrazněné po klepnutí na něj, protože má stále fokus.</span><span class="sxs-lookup"><span data-stu-id="07dd1-196">Notice that the button stays highlighted after you click it because it still has focus.</span></span> <span data-ttu-id="07dd1-197">Pokud kliknete na jiné tlačítko, nové tlačítko získá fokus, zatímco poslední ztratí.</span><span class="sxs-lookup"><span data-stu-id="07dd1-197">If you click another button, the new button gains focus while the last one loses it.</span></span>

4. <span data-ttu-id="07dd1-198">**Přidat animace pro** <xref:System.Windows.UIElement.MouseEnter> **a** <xref:System.Windows.UIElement.MouseLeave> **:** Dále přidáme některé animace na aktivační události.  </span><span class="sxs-lookup"><span data-stu-id="07dd1-198">**Add animations for**  <xref:System.Windows.UIElement.MouseEnter> **and** <xref:System.Windows.UIElement.MouseLeave> **:** Next we add some animations to the triggers.</span></span> <span data-ttu-id="07dd1-199">Přidejte následující značky kdekoli `ControlTemplate.Triggers` uvnitř bloku.</span><span class="sxs-lookup"><span data-stu-id="07dd1-199">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block.</span></span>

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

     <span data-ttu-id="07dd1-200">Skleněný obdélník se zmenší, když se ukazatel myši přesune nad tlačítko a vrátí se zpět na normální velikost, když ukazatel opustí.</span><span class="sxs-lookup"><span data-stu-id="07dd1-200">The glass rectangle shrinks when the mouse pointer moves over the button and returns back to normal size when the pointer leaves.</span></span>

     <span data-ttu-id="07dd1-201">Existují dvě animace, které se aktivují,<xref:System.Windows.UIElement.MouseEnter> když ukazatel přejde přes tlačítko (událost je aktivována).</span><span class="sxs-lookup"><span data-stu-id="07dd1-201">There are two animations that are triggered when the pointer goes over the button (<xref:System.Windows.UIElement.MouseEnter> event is raised).</span></span> <span data-ttu-id="07dd1-202">Tyto animace zmenšit skleněný obdélník podél osy X a Y.</span><span class="sxs-lookup"><span data-stu-id="07dd1-202">These animations shrink the glass rectangle along the X and Y axis.</span></span> <span data-ttu-id="07dd1-203">Všimněte si <xref:System.Windows.Media.Animation.DoubleAnimation> vlastností <xref:System.Windows.Media.Animation.Timeline.Duration%2A> <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>prvků – a .</span><span class="sxs-lookup"><span data-stu-id="07dd1-203">Notice the properties on the <xref:System.Windows.Media.Animation.DoubleAnimation> elements — <xref:System.Windows.Media.Animation.Timeline.Duration%2A> and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.</span></span> <span data-ttu-id="07dd1-204">Určuje, <xref:System.Windows.Media.Animation.Timeline.Duration%2A> že animace dochází více než půl <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> sekundy a určuje, že sklo zmenší o 10 %.</span><span class="sxs-lookup"><span data-stu-id="07dd1-204">The <xref:System.Windows.Media.Animation.Timeline.Duration%2A> specifies that the animation occurs over half a second, and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> specifies that the glass shrinks by 10%.</span></span>

     <span data-ttu-id="07dd1-205">Druhá aktivační událost<xref:System.Windows.UIElement.MouseLeave>( ) jednoduše zastaví první.</span><span class="sxs-lookup"><span data-stu-id="07dd1-205">The second event trigger (<xref:System.Windows.UIElement.MouseLeave>) simply stops the first one.</span></span> <span data-ttu-id="07dd1-206">Když zastavíte <xref:System.Windows.Media.Animation.Storyboard>, všechny animované vlastnosti se vrátí na své výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="07dd1-206">When you stop a <xref:System.Windows.Media.Animation.Storyboard>, all the animated properties return to their default values.</span></span> <span data-ttu-id="07dd1-207">Proto když uživatel přesune ukazatel mimo tlačítko, tlačítko přejde zpět tak, jak to bylo před ukazatelem myši přesunuta přes tlačítko.</span><span class="sxs-lookup"><span data-stu-id="07dd1-207">Therefore, when the user moves the pointer off the button, the button goes back to the way it was before the mouse pointer moved over the button.</span></span> <span data-ttu-id="07dd1-208">Další informace o animacích naleznete v [tématu Přehled animací](../graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="07dd1-208">For more information about animations, see [Animation Overview](../graphics-multimedia/animation-overview.md).</span></span>

5. <span data-ttu-id="07dd1-209">**Přidejte animaci po kliknutí na tlačítko:** Posledním krokem je přidání aktivační události pro po klepnutí na tlačítko uživatelem.</span><span class="sxs-lookup"><span data-stu-id="07dd1-209">**Add an animation for when the button is clicked:** The final step is to add a trigger for when the user clicks the button.</span></span> <span data-ttu-id="07dd1-210">Přidejte následující značky kdekoli `ControlTemplate.Triggers` uvnitř bloku:</span><span class="sxs-lookup"><span data-stu-id="07dd1-210">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block:</span></span>

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

     <span data-ttu-id="07dd1-211">Stisknutím klávesy F5 spusťte aplikaci a klepněte na jedno z tlačítek.</span><span class="sxs-lookup"><span data-stu-id="07dd1-211">Press F5 to run the application, and click one of the buttons.</span></span> <span data-ttu-id="07dd1-212">Když kliknete na tlačítko, skleněný obdélník se otáčí.</span><span class="sxs-lookup"><span data-stu-id="07dd1-212">When you click a button, the glass rectangle spins around.</span></span>

## <a name="summary"></a><span data-ttu-id="07dd1-213">Souhrn</span><span class="sxs-lookup"><span data-stu-id="07dd1-213">Summary</span></span>
 <span data-ttu-id="07dd1-214">V tomto návodu jste provedli následující cvičení:</span><span class="sxs-lookup"><span data-stu-id="07dd1-214">In this walkthrough, you performed the following exercises:</span></span>

- <span data-ttu-id="07dd1-215">Zacílený a <xref:System.Windows.Style> na<xref:System.Windows.Controls.Button>typ objektu ( ).</span><span class="sxs-lookup"><span data-stu-id="07dd1-215">Targeted a <xref:System.Windows.Style> to an object type (<xref:System.Windows.Controls.Button>).</span></span>

- <span data-ttu-id="07dd1-216">Řízené základní vlastnosti tlačítek v celé <xref:System.Windows.Style>aplikaci pomocí .</span><span class="sxs-lookup"><span data-stu-id="07dd1-216">Controlled basic properties of the buttons in the entire application using the <xref:System.Windows.Style>.</span></span>

- <span data-ttu-id="07dd1-217">Byly vytvořeny prostředky, jako jsou přechody, které se mají použít pro hodnoty vlastností <xref:System.Windows.Style> nastavení.</span><span class="sxs-lookup"><span data-stu-id="07dd1-217">Created resources like gradients to use for property values of the <xref:System.Windows.Style> setters.</span></span>

- <span data-ttu-id="07dd1-218">Přizpůsobenvzhled tlačítek v celé aplikaci použitím šablony na tlačítka.</span><span class="sxs-lookup"><span data-stu-id="07dd1-218">Customized the look of buttons in the entire application by applying a template to the buttons.</span></span>

- <span data-ttu-id="07dd1-219">Přizpůsobené chování tlačítek v reakci na akce <xref:System.Windows.UIElement.MouseEnter> <xref:System.Windows.UIElement.MouseLeave>uživatele <xref:System.Windows.Controls.Primitives.ButtonBase.Click>(například , a ), které zahrnovaly animační efekty.</span><span class="sxs-lookup"><span data-stu-id="07dd1-219">Customized behavior for the buttons in response to user actions (such as <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>, and <xref:System.Windows.Controls.Primitives.ButtonBase.Click>) that included animation effects.</span></span>

## <a name="see-also"></a><span data-ttu-id="07dd1-220">Viz také</span><span class="sxs-lookup"><span data-stu-id="07dd1-220">See also</span></span>

- [<span data-ttu-id="07dd1-221">Vytvoření tlačítka pomocí nástroje Microsoft Expression Blend</span><span class="sxs-lookup"><span data-stu-id="07dd1-221">Create a Button by Using Microsoft Expression Blend</span></span>](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)
- [<span data-ttu-id="07dd1-222">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="07dd1-222">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="07dd1-223">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="07dd1-223">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="07dd1-224">Přehled malování plnými barvami a přechody</span><span class="sxs-lookup"><span data-stu-id="07dd1-224">Painting with Solid Colors and Gradients Overview</span></span>](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="07dd1-225">Přehled efektů bitmap</span><span class="sxs-lookup"><span data-stu-id="07dd1-225">Bitmap Effects Overview</span></span>](../graphics-multimedia/bitmap-effects-overview.md)
