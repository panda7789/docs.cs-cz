---
title: 'Návod: Vytvoření tlačítka použitím XAML'
description: V tomto návodu se dozvíte, jak vytvořit animované tlačítko pro použití v Windows Presentation Foundation aplikace pomocí jazyka XAML.
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
ms.openlocfilehash: 136d1ad5d6fefd70f0d977e5287ae75f06c52d36
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164847"
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a><span data-ttu-id="b07fd-103">Návod: Vytvoření tlačítka použitím XAML</span><span class="sxs-lookup"><span data-stu-id="b07fd-103">Walkthrough: Create a Button by Using XAML</span></span>

<span data-ttu-id="b07fd-104">Cílem tohoto návodu je zjistit, jak vytvořit animované tlačítko pro použití v aplikaci Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="b07fd-104">The objective of this walkthrough is to learn how to create an animated button for use in a Windows Presentation Foundation (WPF) application.</span></span> <span data-ttu-id="b07fd-105">Tento návod používá styly a šablonu k vytvoření vlastního prostředku tlačítka, který umožňuje opakované použití kódu a oddělení logiky tlačítek z deklarace tlačítka.</span><span class="sxs-lookup"><span data-stu-id="b07fd-105">This walkthrough uses styles and a template to create a customized button resource that allows reuse of code and separation of button logic from the button declaration.</span></span> <span data-ttu-id="b07fd-106">Tento návod se zapisuje výhradně v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b07fd-106">This walkthrough is written entirely in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b07fd-107">Tento návod vás provede kroky pro vytvoření aplikace zadáním nebo zkopírováním a vložením [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b07fd-107">This walkthrough guides you through the steps for creating the application by typing or copying and pasting [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] into Visual Studio.</span></span> <span data-ttu-id="b07fd-108">Pokud se chcete dozvědět, jak pomocí návrháře vytvořit stejnou aplikaci, přečtěte si téma [Vytvoření tlačítka pomocí nástroje Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).</span><span class="sxs-lookup"><span data-stu-id="b07fd-108">If you would prefer to learn how to use a designer to create the same application, see [Create a Button by Using Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).</span></span>

<span data-ttu-id="b07fd-109">Následující obrázek ukazuje tlačítka dokončená.</span><span class="sxs-lookup"><span data-stu-id="b07fd-109">The following figure shows the finished buttons.</span></span>

<span data-ttu-id="b07fd-110">![Vlastní tlačítka, která byla vytvořena pomocí jazyka XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="b07fd-110">![Custom buttons that were created by using XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>

## <a name="create-basic-buttons"></a><span data-ttu-id="b07fd-111">Vytvoření základních tlačítek</span><span class="sxs-lookup"><span data-stu-id="b07fd-111">Create Basic Buttons</span></span>

<span data-ttu-id="b07fd-112">Pojďme začít vytvořením nového projektu a přidáním několika tlačítek do okna.</span><span class="sxs-lookup"><span data-stu-id="b07fd-112">Let's start by creating a new project and adding a few buttons to the window.</span></span>

### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a><span data-ttu-id="b07fd-113">Vytvoření nového projektu WPF a přidání tlačítek do okna</span><span class="sxs-lookup"><span data-stu-id="b07fd-113">To create a new WPF project and add buttons to the window</span></span>

1. <span data-ttu-id="b07fd-114">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b07fd-114">Start Visual Studio.</span></span>

2. <span data-ttu-id="b07fd-115">**Vytvořit nový projekt WPF:** V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**.</span><span class="sxs-lookup"><span data-stu-id="b07fd-115">**Create a new WPF project:** On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="b07fd-116">Vyhledejte šablonu **aplikace systému Windows (WPF)** a pojmenujte projekt "AnimatedButton".</span><span class="sxs-lookup"><span data-stu-id="b07fd-116">Find the **Windows Application (WPF)** template and name the project "AnimatedButton".</span></span> <span data-ttu-id="b07fd-117">Tím se vytvoří kostra aplikace.</span><span class="sxs-lookup"><span data-stu-id="b07fd-117">This will create the skeleton for the application.</span></span>

3. <span data-ttu-id="b07fd-118">**Přidat základní výchozí tlačítka:** Všechny soubory, které potřebujete pro tento návod, poskytuje šablona.</span><span class="sxs-lookup"><span data-stu-id="b07fd-118">**Add basic default buttons:** All the files you need for this walkthrough are provided by the template.</span></span> <span data-ttu-id="b07fd-119">Otevřete soubor Window1. XAML dvojitým kliknutím na něj v Průzkumník řešení.</span><span class="sxs-lookup"><span data-stu-id="b07fd-119">Open the Window1.xaml file by double clicking it in Solution Explorer.</span></span> <span data-ttu-id="b07fd-120">Ve výchozím nastavení je v souboru <xref:System.Windows.Controls.Grid> Window1. XAML prvek.</span><span class="sxs-lookup"><span data-stu-id="b07fd-120">By default, there is a <xref:System.Windows.Controls.Grid> element in Window1.xaml.</span></span> <span data-ttu-id="b07fd-121">Odeberte <xref:System.Windows.Controls.Grid> prvek a přidejte na stránku několik tlačítek, a to tak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , že do souboru Window1. XAML zadáte nebo zkopírujete a vložíte následující zvýrazněný kód:</span><span class="sxs-lookup"><span data-stu-id="b07fd-121">Remove the <xref:System.Windows.Controls.Grid> element and add a few buttons to the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page by typing or copy and pasting the following highlighted code to Window1.xaml:</span></span>

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

     <span data-ttu-id="b07fd-122">Stisknutím klávesy F5 spusťte aplikaci. měla by se zobrazit sada tlačítek, která vypadají jako na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="b07fd-122">Press F5 to run the application; you should see a set of buttons that looks like the following figure.</span></span>

     <span data-ttu-id="b07fd-123">![Tři základní tlačítka](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span><span class="sxs-lookup"><span data-stu-id="b07fd-123">![Three basic buttons](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")</span></span>

     <span data-ttu-id="b07fd-124">Nyní, když jste vytvořili základní tlačítka, jste dokončili práci v souboru Window1. XAML.</span><span class="sxs-lookup"><span data-stu-id="b07fd-124">Now that you have created the basic buttons, you are finished working in the Window1.xaml file.</span></span> <span data-ttu-id="b07fd-125">Zbytek návodu se zaměřuje na soubor App. XAML, který definuje styly a šablonu pro tlačítka.</span><span class="sxs-lookup"><span data-stu-id="b07fd-125">The rest of the walkthrough focuses on the app.xaml file, defining styles and a template for the buttons.</span></span>

## <a name="set-basic-properties"></a><span data-ttu-id="b07fd-126">Nastavit základní vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b07fd-126">Set Basic Properties</span></span>

<span data-ttu-id="b07fd-127">Nyní na těchto tlačítkách nastavíme některé vlastnosti, které řídí vzhled a rozložení tlačítka.</span><span class="sxs-lookup"><span data-stu-id="b07fd-127">Next, let's set some properties on these buttons to control the button appearance and layout.</span></span> <span data-ttu-id="b07fd-128">Místo toho, abyste nastavovat vlastnosti u tlačítek samostatně, budete používat prostředky k definování vlastností tlačítek pro celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b07fd-128">Rather than setting properties on the buttons individually, you will use resources to define button properties for the entire application.</span></span> <span data-ttu-id="b07fd-129">Prostředky aplikace jsou koncepčně podobné externím šablony stylů CSS (CSS) pro webové stránky; prostředky jsou ale mnohem výkonnější než šablony stylů CSS (CSS), jak vidíte na konci tohoto návodu.</span><span class="sxs-lookup"><span data-stu-id="b07fd-129">Application resources are conceptually similar to external Cascading Style Sheets (CSS) for Web pages; however, resources are much more powerful than Cascading Style Sheets (CSS), as you will see by the end of this walkthrough.</span></span> <span data-ttu-id="b07fd-130">Další informace o prostředcích najdete v tématu [prostředky XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span><span class="sxs-lookup"><span data-stu-id="b07fd-130">To learn more about resources, see [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>

### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a><span data-ttu-id="b07fd-131">Použití stylů k nastavení základních vlastností tlačítek</span><span class="sxs-lookup"><span data-stu-id="b07fd-131">To use styles to set basic properties on the buttons</span></span>

1. <span data-ttu-id="b07fd-132">**Definujte blok Application. Resources:** Otevřete App. XAML a přidejte následující zvýrazněný kód, pokud tam ještě není:</span><span class="sxs-lookup"><span data-stu-id="b07fd-132">**Define an Application.Resources block:** Open app.xaml and add the following highlighted markup if it is not already there:</span></span>

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

     <span data-ttu-id="b07fd-133">Rozsah prostředku určuje, kde můžete prostředek definovat.</span><span class="sxs-lookup"><span data-stu-id="b07fd-133">Resource scope is determined by where you define the resource.</span></span> <span data-ttu-id="b07fd-134">Definování prostředků v `Application.Resources` souboru App. XAML umožňuje použít prostředek z libovolného místa v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b07fd-134">Defining resources in `Application.Resources` in the app.xaml file enables the resource to be used from anywhere in the application.</span></span> <span data-ttu-id="b07fd-135">Další informace o definování rozsahu vašich prostředků najdete v tématu věnovaném [prostředkům XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span><span class="sxs-lookup"><span data-stu-id="b07fd-135">To learn more about defining the scope of your resources, see [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>

2. <span data-ttu-id="b07fd-136">**Vytvořte styl a definujte pro něj základní hodnoty vlastností:** Do bloku přidejte následující kód `Application.Resources` .</span><span class="sxs-lookup"><span data-stu-id="b07fd-136">**Create a style and define basic property values with it:** Add the following markup to the `Application.Resources` block.</span></span> <span data-ttu-id="b07fd-137">Tento kód vytvoří <xref:System.Windows.Style> , který se vztahuje na všechna tlačítka v aplikaci, nastavení <xref:System.Windows.FrameworkElement.Width%2A> tlačítek na 90 a na <xref:System.Windows.FrameworkElement.Margin%2A> 10:</span><span class="sxs-lookup"><span data-stu-id="b07fd-137">This markup creates a <xref:System.Windows.Style> that applies to all buttons in the application, setting the <xref:System.Windows.FrameworkElement.Width%2A> of the buttons to 90 and the <xref:System.Windows.FrameworkElement.Margin%2A> to 10:</span></span>

    ```xaml
    <Application.Resources>
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>
    </Application.Resources>
    ```

     <span data-ttu-id="b07fd-138"><xref:System.Windows.Style.TargetType%2A>Vlastnost určuje, že styl platí pro všechny objekty typu <xref:System.Windows.Controls.Button> .</span><span class="sxs-lookup"><span data-stu-id="b07fd-138">The <xref:System.Windows.Style.TargetType%2A> property specifies that the style applies to all objects of type <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="b07fd-139">Každý <xref:System.Windows.Setter> Nastaví jinou hodnotu vlastnosti pro <xref:System.Windows.Style> .</span><span class="sxs-lookup"><span data-stu-id="b07fd-139">Each <xref:System.Windows.Setter> sets a different property value for the <xref:System.Windows.Style>.</span></span> <span data-ttu-id="b07fd-140">Proto v tomto okamžiku každé tlačítko v aplikaci má šířku 90 a okraj 10.</span><span class="sxs-lookup"><span data-stu-id="b07fd-140">Therefore, at this point every button in the application has a width of 90 and a margin of 10.</span></span>  <span data-ttu-id="b07fd-141">Pokud stisknete klávesu F5 ke spuštění aplikace, zobrazí se následující okno.</span><span class="sxs-lookup"><span data-stu-id="b07fd-141">If you press F5 to run the application, you see the following window.</span></span>

     <span data-ttu-id="b07fd-142">![Tlačítka s šířkou 90 a okrajem 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span><span class="sxs-lookup"><span data-stu-id="b07fd-142">![Buttons with a width of 90 and a margin of 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")</span></span>

     <span data-ttu-id="b07fd-143">K dispozici je mnohem více, co můžete dělat se styly, včetně nejrůznějších způsobů, jak vyladit objekty, které jsou cílené, určením složitých hodnot vlastností a dokonce i pomocí stylů jako vstup pro jiné styly.</span><span class="sxs-lookup"><span data-stu-id="b07fd-143">There is much more you can do with styles, including a variety of ways to fine-tune what objects are targeted, specifying complex property values, and even using styles as input for other styles.</span></span> <span data-ttu-id="b07fd-144">Další informace najdete v tématu [stylování a šablonování](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b07fd-144">For more information, see [Styling and Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

3. <span data-ttu-id="b07fd-145">**Nastavte hodnotu vlastnosti Style na prostředek:** Prostředky umožňují jednoduchý způsob opakovaného použití běžně definovaných objektů a hodnot.</span><span class="sxs-lookup"><span data-stu-id="b07fd-145">**Set a style property value to a resource:** Resources enable a simple way to reuse commonly defined objects and values.</span></span> <span data-ttu-id="b07fd-146">To je užitečné hlavně při definování složitých hodnot pomocí prostředků, aby se váš kód podrobněji vytvářely.</span><span class="sxs-lookup"><span data-stu-id="b07fd-146">It is especially useful to define complex values using resources to make your code more modular.</span></span> <span data-ttu-id="b07fd-147">Přidejte do souboru App. XAML následující zvýrazněný kód.</span><span class="sxs-lookup"><span data-stu-id="b07fd-147">Add the following highlighted markup to app.xaml.</span></span>

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

     <span data-ttu-id="b07fd-148">Přímo pod `Application.Resources` blokem jste vytvořili prostředek s názvem "GrayBlueGradientBrush".</span><span class="sxs-lookup"><span data-stu-id="b07fd-148">Directly under the `Application.Resources` block, you created a resource called "GrayBlueGradientBrush".</span></span> <span data-ttu-id="b07fd-149">Tento prostředek definuje Vodorovný přechod.</span><span class="sxs-lookup"><span data-stu-id="b07fd-149">This resource defines a horizontal gradient.</span></span> <span data-ttu-id="b07fd-150">Tento prostředek lze použít jako hodnotu vlastnosti z libovolného místa v aplikaci, včetně nastavení stylu tlačítka pro <xref:System.Windows.Controls.Control.Background%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b07fd-150">This resource can be used as a property value from anywhere in the application, including inside the button style setter for the <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="b07fd-151">Nyní všechna tlačítka mají <xref:System.Windows.Controls.Control.Background%2A> hodnotu vlastnosti tohoto přechodu.</span><span class="sxs-lookup"><span data-stu-id="b07fd-151">Now, all the buttons have a <xref:System.Windows.Controls.Control.Background%2A> property value of this gradient.</span></span>

     <span data-ttu-id="b07fd-152">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b07fd-152">Press F5 to run the application.</span></span> <span data-ttu-id="b07fd-153">Měl by vypadat nějak takto.</span><span class="sxs-lookup"><span data-stu-id="b07fd-153">It should look like the following.</span></span>

     <span data-ttu-id="b07fd-154">![Tlačítka s pozadím přechodu](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span><span class="sxs-lookup"><span data-stu-id="b07fd-154">![Buttons with a gradient background](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")</span></span>

## <a name="create-a-template-that-defines-the-look-of-the-button"></a><span data-ttu-id="b07fd-155">Vytvoření šablony definující vzhled tlačítka</span><span class="sxs-lookup"><span data-stu-id="b07fd-155">Create a Template That Defines the Look of the Button</span></span>

<span data-ttu-id="b07fd-156">V této části vytvoříte šablonu, která přizpůsobí vzhled tlačítka (prezentace).</span><span class="sxs-lookup"><span data-stu-id="b07fd-156">In this section, you create a template that customizes the appearance (presentation) of the button.</span></span> <span data-ttu-id="b07fd-157">Prezentace tlačítek se skládá z několika objektů, včetně obdélníků a dalších komponent, které tlačítku podávají jedinečný vzhled.</span><span class="sxs-lookup"><span data-stu-id="b07fd-157">The button presentation is made up of several objects including rectangles and other components to give the button a unique look.</span></span>

<span data-ttu-id="b07fd-158">V tuto dobu byl ovládací prvek toho, jak se tlačítka vypadají v aplikaci, omezen na změnu vlastností tlačítka.</span><span class="sxs-lookup"><span data-stu-id="b07fd-158">So far, the control of how buttons look in the application has been confined to changing properties of the button.</span></span> <span data-ttu-id="b07fd-159">Co dělat v případě, že chcete další odmocniny změn v zobrazení tlačítka?</span><span class="sxs-lookup"><span data-stu-id="b07fd-159">What if you want to make more radical changes to the button's appearance?</span></span> <span data-ttu-id="b07fd-160">Šablony umožňují výkonnou kontrolu nad prezentací objektu.</span><span class="sxs-lookup"><span data-stu-id="b07fd-160">Templates enable powerful control over the presentation of an object.</span></span> <span data-ttu-id="b07fd-161">Vzhledem k tomu, že šablony lze použít v rámci stylů, můžete použít šablonu na všechny objekty, na které se vztahuje styl (v tomto návodu tlačítko).</span><span class="sxs-lookup"><span data-stu-id="b07fd-161">Because templates can be used within styles, you can apply a template to all objects that the style applies to (in this walkthrough, the button).</span></span>

### <a name="to-use-the-template-to-define-the-look-of-the-button"></a><span data-ttu-id="b07fd-162">Chcete-li použít šablonu k definování vzhledu tlačítka</span><span class="sxs-lookup"><span data-stu-id="b07fd-162">To use the template to define the look of the button</span></span>

1. <span data-ttu-id="b07fd-163">**Nastavte šablonu:** Vzhledem k tomu, že ovládací prvky jako <xref:System.Windows.Controls.Button> mají <xref:System.Windows.Controls.Control.Template%2A> vlastnost, lze definovat hodnotu vlastnosti šablony stejným způsobem jako ostatní hodnoty vlastností, které jsme nastavili v s <xref:System.Windows.Style> použitím <xref:System.Windows.Setter> .</span><span class="sxs-lookup"><span data-stu-id="b07fd-163">**Set up the template:** Because controls like <xref:System.Windows.Controls.Button> have a <xref:System.Windows.Controls.Control.Template%2A> property, you can define the template property value just like the other property values we have set in a <xref:System.Windows.Style> using a <xref:System.Windows.Setter>.</span></span> <span data-ttu-id="b07fd-164">Přidejte následující zvýrazněný kód na styl tlačítka.</span><span class="sxs-lookup"><span data-stu-id="b07fd-164">Add the following highlighted markup to your button style.</span></span>

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

2. <span data-ttu-id="b07fd-165">**Upravit úpravu tlačítek:** V tomto okamžiku je nutné šablonu definovat.</span><span class="sxs-lookup"><span data-stu-id="b07fd-165">**Alter button presentation:** At this point, you need to define the template.</span></span> <span data-ttu-id="b07fd-166">Přidejte následující zvýrazněný kód.</span><span class="sxs-lookup"><span data-stu-id="b07fd-166">Add the following highlighted markup.</span></span> <span data-ttu-id="b07fd-167">Tento kód určuje dva <xref:System.Windows.Shapes.Rectangle> prvky s zaoblenými hranami následovaný <xref:System.Windows.Controls.DockPanel> .</span><span class="sxs-lookup"><span data-stu-id="b07fd-167">This markup specifies two <xref:System.Windows.Shapes.Rectangle> elements with rounded edges, followed by a <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="b07fd-168"><xref:System.Windows.Controls.DockPanel>Slouží k hostování <xref:System.Windows.Controls.ContentPresenter> tlačítka.</span><span class="sxs-lookup"><span data-stu-id="b07fd-168">The <xref:System.Windows.Controls.DockPanel> is used to host the <xref:System.Windows.Controls.ContentPresenter> of the button.</span></span> <span data-ttu-id="b07fd-169"><xref:System.Windows.Controls.ContentPresenter>Zobrazí obsah tlačítka.</span><span class="sxs-lookup"><span data-stu-id="b07fd-169">A <xref:System.Windows.Controls.ContentPresenter> displays the content of the button.</span></span> <span data-ttu-id="b07fd-170">V tomto návodu je obsahem text ("tlačítko 1", "tlačítko 2", "tlačítko 3").</span><span class="sxs-lookup"><span data-stu-id="b07fd-170">In this walkthrough, the content is text ("Button 1", "Button 2", "Button 3").</span></span> <span data-ttu-id="b07fd-171">Všechny součásti šablony (obdélníky a <xref:System.Windows.Controls.DockPanel> ) jsou rozloženy v rámci <xref:System.Windows.Controls.Grid> .</span><span class="sxs-lookup"><span data-stu-id="b07fd-171">All of the template components (the rectangles and the <xref:System.Windows.Controls.DockPanel>) are laid out inside of a <xref:System.Windows.Controls.Grid>.</span></span>

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

     <span data-ttu-id="b07fd-172">Stisknutím klávesy F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b07fd-172">Press F5 to run the application.</span></span> <span data-ttu-id="b07fd-173">Měl by vypadat nějak takto.</span><span class="sxs-lookup"><span data-stu-id="b07fd-173">It should look like the following.</span></span>

     ![Okno se třemi tlačítky](./media/custom-button-animatedbutton-4.gif)

3. <span data-ttu-id="b07fd-175">**Přidat glasseffect do šablony:** V dalším kroku přidáte skleněnou.</span><span class="sxs-lookup"><span data-stu-id="b07fd-175">**Add a glasseffect to the template:** Next you will add the glass.</span></span> <span data-ttu-id="b07fd-176">Nejprve vytvoříte některé prostředky, které vytvoří efekt skleněného přechodu.</span><span class="sxs-lookup"><span data-stu-id="b07fd-176">First you create some resources that create a glass gradient effect.</span></span> <span data-ttu-id="b07fd-177">Přidejte tyto prostředky přechodu kamkoli v rámci `Application.Resources` bloku:</span><span class="sxs-lookup"><span data-stu-id="b07fd-177">Add these gradient resources anywhere within the `Application.Resources` block:</span></span>

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

     <span data-ttu-id="b07fd-178">Tyto prostředky se používají jako <xref:System.Windows.Shapes.Shape.Fill%2A> pro obdélník, který vložíte do <xref:System.Windows.Controls.Grid> šablony tlačítka.</span><span class="sxs-lookup"><span data-stu-id="b07fd-178">These resources are used as the <xref:System.Windows.Shapes.Shape.Fill%2A> for a rectangle that we insert into the <xref:System.Windows.Controls.Grid> of the button template.</span></span> <span data-ttu-id="b07fd-179">Přidejte následující zvýrazněný kód do šablony.</span><span class="sxs-lookup"><span data-stu-id="b07fd-179">Add the following highlighted markup to the template.</span></span>

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

     <span data-ttu-id="b07fd-180">Všimněte si, že <xref:System.Windows.UIElement.Opacity%2A> obdélník s `x:Name` vlastností "glassCube" je 0, takže při spuštění ukázky se nezobrazuje skleněný obdélník překrytý nahoře.</span><span class="sxs-lookup"><span data-stu-id="b07fd-180">Notice that the <xref:System.Windows.UIElement.Opacity%2A> of the rectangle with the `x:Name` property of "glassCube" is 0, so when you run the sample, you do not see the glass rectangle overlaid on top.</span></span> <span data-ttu-id="b07fd-181">Důvodem je, že později přidáte triggery do šablony, když uživatel komunikuje s tlačítkem.</span><span class="sxs-lookup"><span data-stu-id="b07fd-181">This is because we will later add triggers to the template for when the user interacts with the button.</span></span> <span data-ttu-id="b07fd-182">Můžete si ale prohlédnout, co tlačítko vypadá nyní, změnou <xref:System.Windows.UIElement.Opacity%2A> hodnoty na 1 a spuštěním aplikace.</span><span class="sxs-lookup"><span data-stu-id="b07fd-182">However, you can see what the button looks like now by changing the <xref:System.Windows.UIElement.Opacity%2A> value to 1 and running the application.</span></span> <span data-ttu-id="b07fd-183">Prohlédněte si následující obrázek.</span><span class="sxs-lookup"><span data-stu-id="b07fd-183">See the following figure.</span></span> <span data-ttu-id="b07fd-184">Než budete pokračovat k dalšímu kroku, změňte <xref:System.Windows.UIElement.Opacity%2A> zpět na 0.</span><span class="sxs-lookup"><span data-stu-id="b07fd-184">Before proceeding to the next step, change the <xref:System.Windows.UIElement.Opacity%2A> back to 0.</span></span>

     <span data-ttu-id="b07fd-185">![Vlastní tlačítka, která byla vytvořena pomocí jazyka XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span><span class="sxs-lookup"><span data-stu-id="b07fd-185">![Custom buttons that were created by using XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")</span></span>

## <a name="create-button-interactivity"></a><span data-ttu-id="b07fd-186">Vytvořit interaktivitu tlačítka</span><span class="sxs-lookup"><span data-stu-id="b07fd-186">Create Button Interactivity</span></span>

<span data-ttu-id="b07fd-187">V této části vytvoříte triggery vlastností a aktivační události pro změnu hodnot vlastností a spustíte animace v reakci na akce uživatele, jako je například přesunutí ukazatele myši na tlačítko a kliknutí.</span><span class="sxs-lookup"><span data-stu-id="b07fd-187">In this section, you will create property triggers and event triggers to change property values and run animations in response to user actions such as moving the mouse pointer over the button and clicking.</span></span>

<span data-ttu-id="b07fd-188">Snadný způsob, jak přidat interaktivitu (přetažení myší, ponechání myší, kliknutí atd.), je definovat triggery v rámci šablony nebo stylu.</span><span class="sxs-lookup"><span data-stu-id="b07fd-188">An easy way to add interactivity (mouse-over, mouse-leave, click, and so on) is to define triggers within your template or style.</span></span> <span data-ttu-id="b07fd-189">Chcete-li vytvořit <xref:System.Windows.Trigger> , definujte vlastnost "podmínka", například: <xref:System.Windows.UIElement.IsMouseOver%2A> hodnota vlastnosti Button je rovna `true` .</span><span class="sxs-lookup"><span data-stu-id="b07fd-189">To create a <xref:System.Windows.Trigger>, you define a property "condition" such as: The button <xref:System.Windows.UIElement.IsMouseOver%2A> property value is equal to `true`.</span></span> <span data-ttu-id="b07fd-190">Pak definujete metody setter (akce), které se provedou, když je podmínka triggeru pravdivá.</span><span class="sxs-lookup"><span data-stu-id="b07fd-190">You then define setters (actions) that take place when the trigger condition is true.</span></span>

### <a name="to-create-button-interactivity"></a><span data-ttu-id="b07fd-191">Vytvoření interaktivity tlačítek</span><span class="sxs-lookup"><span data-stu-id="b07fd-191">To create button interactivity</span></span>

1. <span data-ttu-id="b07fd-192">**Přidat aktivační události šablony:** Přidejte zvýrazněný kód do šablony.</span><span class="sxs-lookup"><span data-stu-id="b07fd-192">**Add template triggers:** Add the highlighted markup to your template.</span></span>

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

2. <span data-ttu-id="b07fd-193">**Přidat triggery vlastností:** Přidejte zvýrazněný kód do `ControlTemplate.Triggers` bloku:</span><span class="sxs-lookup"><span data-stu-id="b07fd-193">**Add property triggers:** Add the highlighted markup to the `ControlTemplate.Triggers` block:</span></span>

    ```xaml
    <ControlTemplate.Triggers>

      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>

    <ControlTemplate.Triggers/>
    ```

     <span data-ttu-id="b07fd-194">Stiskněte klávesu F5 ke spuštění aplikace a zobrazení efektu při spuštění ukazatele myši nad tlačítky.</span><span class="sxs-lookup"><span data-stu-id="b07fd-194">Press F5 to run the application and see the effect as you run the mouse pointer over the buttons.</span></span>

3. <span data-ttu-id="b07fd-195">**Přidat aktivační událost fokusu:** Dále přidáte několik podobných setter pro zpracování případu, když má tlačítko fokus (například poté, co na něj uživatel klikne).</span><span class="sxs-lookup"><span data-stu-id="b07fd-195">**Add a focus trigger:** Next, we'll add some similar setters to handle the case when the button has focus (for example, after the user clicks it).</span></span>

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

     <span data-ttu-id="b07fd-196">Stisknutím klávesy F5 spusťte aplikaci a klikněte na jedno z tlačítek.</span><span class="sxs-lookup"><span data-stu-id="b07fd-196">Press F5 to run the application and click on one of the buttons.</span></span> <span data-ttu-id="b07fd-197">Všimněte si, že tlačítko zůstane zvýrazněné, i když na něj kliknete, protože pořád má fokus.</span><span class="sxs-lookup"><span data-stu-id="b07fd-197">Notice that the button stays highlighted after you click it because it still has focus.</span></span> <span data-ttu-id="b07fd-198">Pokud kliknete na jiné tlačítko, nové tlačítko získá fokus, zatímco poslední ho ztratí.</span><span class="sxs-lookup"><span data-stu-id="b07fd-198">If you click another button, the new button gains focus while the last one loses it.</span></span>

4. <span data-ttu-id="b07fd-199">**Přidat animace pro** <xref:System.Windows.UIElement.MouseEnter> **a** <xref:System.Windows.UIElement.MouseLeave> **:** V dalším kroku přidáme k aktivačním událostem nějaké animace.  </span><span class="sxs-lookup"><span data-stu-id="b07fd-199">**Add animations for**  <xref:System.Windows.UIElement.MouseEnter> **and** <xref:System.Windows.UIElement.MouseLeave> **:** Next we add some animations to the triggers.</span></span> <span data-ttu-id="b07fd-200">Přidejte následující kód kdekoli uvnitř `ControlTemplate.Triggers` bloku.</span><span class="sxs-lookup"><span data-stu-id="b07fd-200">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block.</span></span>

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

     <span data-ttu-id="b07fd-201">Skleněný obdélník se zmenší, když se ukazatel myši přesune nad tlačítko a vrátí se zpět na normální velikost, když ukazatel opustí.</span><span class="sxs-lookup"><span data-stu-id="b07fd-201">The glass rectangle shrinks when the mouse pointer moves over the button and returns back to normal size when the pointer leaves.</span></span>

     <span data-ttu-id="b07fd-202">Pokud se ukazatel myši nachází nad tlačítkem ( <xref:System.Windows.UIElement.MouseEnter> událost je aktivována), existují dva animace, které jsou aktivovány.</span><span class="sxs-lookup"><span data-stu-id="b07fd-202">There are two animations that are triggered when the pointer goes over the button (<xref:System.Windows.UIElement.MouseEnter> event is raised).</span></span> <span data-ttu-id="b07fd-203">Tyto animace zmenší skleněný obdélník podél osy X a Y.</span><span class="sxs-lookup"><span data-stu-id="b07fd-203">These animations shrink the glass rectangle along the X and Y axis.</span></span> <span data-ttu-id="b07fd-204">Všimněte si vlastností <xref:System.Windows.Media.Animation.DoubleAnimation> prvků, <xref:System.Windows.Media.Animation.Timeline.Duration%2A> a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> .</span><span class="sxs-lookup"><span data-stu-id="b07fd-204">Notice the properties on the <xref:System.Windows.Media.Animation.DoubleAnimation> elements — <xref:System.Windows.Media.Animation.Timeline.Duration%2A> and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.</span></span> <span data-ttu-id="b07fd-205"><xref:System.Windows.Media.Animation.Timeline.Duration%2A>Určuje, že animace probíhá přes polovinu sekundy, a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> Určuje, že se skleněná zmenší o 10%.</span><span class="sxs-lookup"><span data-stu-id="b07fd-205">The <xref:System.Windows.Media.Animation.Timeline.Duration%2A> specifies that the animation occurs over half a second, and <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> specifies that the glass shrinks by 10%.</span></span>

     <span data-ttu-id="b07fd-206">Druhá aktivační procedura události ( <xref:System.Windows.UIElement.MouseLeave> ) jednoduše zastaví první z nich.</span><span class="sxs-lookup"><span data-stu-id="b07fd-206">The second event trigger (<xref:System.Windows.UIElement.MouseLeave>) simply stops the first one.</span></span> <span data-ttu-id="b07fd-207">Po zastavení <xref:System.Windows.Media.Animation.Storyboard> se všechny animované vlastnosti vrátí do jejich výchozích hodnot.</span><span class="sxs-lookup"><span data-stu-id="b07fd-207">When you stop a <xref:System.Windows.Media.Animation.Storyboard>, all the animated properties return to their default values.</span></span> <span data-ttu-id="b07fd-208">Proto když uživatel přesune ukazatel myši na tlačítko, tlačítko se vrátí k tomu, jak bylo předtím, než se ukazatel myši přesunul nad tlačítko.</span><span class="sxs-lookup"><span data-stu-id="b07fd-208">Therefore, when the user moves the pointer off the button, the button goes back to the way it was before the mouse pointer moved over the button.</span></span> <span data-ttu-id="b07fd-209">Další informace o animacích najdete v tématu [Přehled animací](../graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b07fd-209">For more information about animations, see [Animation Overview](../graphics-multimedia/animation-overview.md).</span></span>

5. <span data-ttu-id="b07fd-210">**Přidat animaci pro, když se klikne na tlačítko:** Posledním krokem je přidání triggeru pro, když uživatel klikne na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="b07fd-210">**Add an animation for when the button is clicked:** The final step is to add a trigger for when the user clicks the button.</span></span> <span data-ttu-id="b07fd-211">Přidejte následující kód kdekoli uvnitř `ControlTemplate.Triggers` bloku:</span><span class="sxs-lookup"><span data-stu-id="b07fd-211">Add the following markup anywhere inside of the `ControlTemplate.Triggers` block:</span></span>

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

     <span data-ttu-id="b07fd-212">Stisknutím klávesy F5 spusťte aplikaci a klikněte na jedno z tlačítek.</span><span class="sxs-lookup"><span data-stu-id="b07fd-212">Press F5 to run the application, and click one of the buttons.</span></span> <span data-ttu-id="b07fd-213">Po kliknutí na tlačítko se otáčí obdélník kolem.</span><span class="sxs-lookup"><span data-stu-id="b07fd-213">When you click a button, the glass rectangle spins around.</span></span>

## <a name="summary"></a><span data-ttu-id="b07fd-214">Souhrn</span><span class="sxs-lookup"><span data-stu-id="b07fd-214">Summary</span></span>
 <span data-ttu-id="b07fd-215">V tomto návodu jste provedli následující cvičení:</span><span class="sxs-lookup"><span data-stu-id="b07fd-215">In this walkthrough, you performed the following exercises:</span></span>

- <span data-ttu-id="b07fd-216">Cílem a <xref:System.Windows.Style> na typ objektu ( <xref:System.Windows.Controls.Button> ).</span><span class="sxs-lookup"><span data-stu-id="b07fd-216">Targeted a <xref:System.Windows.Style> to an object type (<xref:System.Windows.Controls.Button>).</span></span>

- <span data-ttu-id="b07fd-217">Řízená základní vlastnosti tlačítek v celé aplikaci pomocí <xref:System.Windows.Style> .</span><span class="sxs-lookup"><span data-stu-id="b07fd-217">Controlled basic properties of the buttons in the entire application using the <xref:System.Windows.Style>.</span></span>

- <span data-ttu-id="b07fd-218">Vytvořené prostředky, jako jsou přechody, které se použijí pro hodnoty vlastností <xref:System.Windows.Style> setter.</span><span class="sxs-lookup"><span data-stu-id="b07fd-218">Created resources like gradients to use for property values of the <xref:System.Windows.Style> setters.</span></span>

- <span data-ttu-id="b07fd-219">Přizpůsobený vzhled tlačítek v celé aplikaci aplikováním šablony na tlačítka.</span><span class="sxs-lookup"><span data-stu-id="b07fd-219">Customized the look of buttons in the entire application by applying a template to the buttons.</span></span>

- <span data-ttu-id="b07fd-220">Přizpůsobení chování pro tlačítka v reakci na akce uživatele (například <xref:System.Windows.UIElement.MouseEnter> , <xref:System.Windows.UIElement.MouseLeave> , a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> ), které obsahují animační efekty.</span><span class="sxs-lookup"><span data-stu-id="b07fd-220">Customized behavior for the buttons in response to user actions (such as <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>, and <xref:System.Windows.Controls.Primitives.ButtonBase.Click>) that included animation effects.</span></span>

## <a name="see-also"></a><span data-ttu-id="b07fd-221">Viz také</span><span class="sxs-lookup"><span data-stu-id="b07fd-221">See also</span></span>

- [<span data-ttu-id="b07fd-222">Vytvoření tlačítka pomocí nástroje Microsoft Expression Blend</span><span class="sxs-lookup"><span data-stu-id="b07fd-222">Create a Button by Using Microsoft Expression Blend</span></span>](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)
- [<span data-ttu-id="b07fd-223">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="b07fd-223">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="b07fd-224">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="b07fd-224">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="b07fd-225">Přehled malování plnými barvami a přechody</span><span class="sxs-lookup"><span data-stu-id="b07fd-225">Painting with Solid Colors and Gradients Overview</span></span>](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="b07fd-226">Přehled efektů bitmap</span><span class="sxs-lookup"><span data-stu-id="b07fd-226">Bitmap Effects Overview</span></span>](../graphics-multimedia/bitmap-effects-overview.md)
