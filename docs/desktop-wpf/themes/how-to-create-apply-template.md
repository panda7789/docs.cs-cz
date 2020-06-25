---
title: Vytvoření šablony v prostředí WPF – .NET Desktop
description: Naučte se vytvořit a odkazovat na šablonu ovládacího prvku v Windows Presentation Foundation a .NET Core.
author: adegeo
ms.author: adegeo
ms.date: 11/15/2019
no-loc:
- <Window>
- <ControlTemplate>
- <Ellipse>
- <ContentPresenter>
- <Trigger>
- <Setter>
- <PropertyTrigger>
- <Grid>
- <VisualStateManager.VisualStateGroups>
- <VisualStateGroup>
- <VisualState>
- <Storyboard>
- SizeToContent
- MinWidth
- TargetType
- Title
helpviewer_keywords:
- control contract [WPF]
- controls [WPF], visual structure changes
- ControlTemplate [WPF], customizing for existing controls
- skinning controls [WPF]
- controls [WPF], appearance specified by state
- templates [WPF], custom for existing controls
ms.openlocfilehash: c372659676b450cde789c96e45c7ec5de2aea194
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325726"
---
# <a name="create-a-template-for-a-control"></a><span data-ttu-id="e7330-103">Vytvoření šablony pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="e7330-103">Create a template for a control</span></span>

<span data-ttu-id="e7330-104">Pomocí Windows Presentation Foundation (WPF) můžete přizpůsobit vizuální strukturu a chování existující ovládacímu prvku pomocí vlastní opakovaně použitelné šablony.</span><span class="sxs-lookup"><span data-stu-id="e7330-104">With Windows Presentation Foundation (WPF), you can customize an existing control's visual structure and behavior with your own reusable template.</span></span> <span data-ttu-id="e7330-105">Šablony lze globálně použít pro vaši aplikaci, okna a stránky nebo přímo k ovládacím prvkům.</span><span class="sxs-lookup"><span data-stu-id="e7330-105">Templates can be applied globally to your application, windows and pages, or directly to controls.</span></span> <span data-ttu-id="e7330-106">Pro většinu scénářů, které vyžadují vytvoření nového ovládacího prvku, se místo toho dá vytvořit nová šablona pro existující ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="e7330-106">Most scenarios that require you to create a new control can be covered by instead creating a new template for an existing control.</span></span>

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

<span data-ttu-id="e7330-107">V tomto článku budete zkoumat vytvoření nového <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e7330-107">In this article, you'll explore creating a new <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>

## <a name="when-to-create-a-controltemplate"></a><span data-ttu-id="e7330-108">Kdy vytvořit ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="e7330-108">When to create a ControlTemplate</span></span>

<span data-ttu-id="e7330-109">Ovládací prvky mají mnoho vlastností, jako jsou <xref:System.Windows.Controls.Border.Background%2A> , <xref:System.Windows.Controls.Control.Foreground%2A> a <xref:System.Windows.Controls.Control.FontFamily%2A> .</span><span class="sxs-lookup"><span data-stu-id="e7330-109">Controls have many properties, such as <xref:System.Windows.Controls.Border.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, and <xref:System.Windows.Controls.Control.FontFamily%2A>.</span></span> <span data-ttu-id="e7330-110">Tyto vlastnosti řídí různé aspekty vzhledu ovládacího prvku, ale změny, které můžete provést nastavením těchto vlastností, jsou omezené.</span><span class="sxs-lookup"><span data-stu-id="e7330-110">These properties control different aspects of the control's appearance, but the changes that you can make by setting these properties are limited.</span></span> <span data-ttu-id="e7330-111">Můžete například nastavit <xref:System.Windows.Controls.Control.Foreground%2A> vlastnost na modrou a <xref:System.Windows.Controls.Control.FontStyle%2A> na kurzívu na <xref:System.Windows.Controls.CheckBox> .</span><span class="sxs-lookup"><span data-stu-id="e7330-111">For example, you can set the <xref:System.Windows.Controls.Control.Foreground%2A> property to blue and <xref:System.Windows.Controls.Control.FontStyle%2A> to italic on a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="e7330-112">Pokud chcete přizpůsobit vzhled ovládacího prvku nad rámec toho, co nastavení dalších vlastností ovládacího prvku může udělat, vytvoříte <xref:System.Windows.Controls.ControlTemplate> .</span><span class="sxs-lookup"><span data-stu-id="e7330-112">When you want to customize the control's appearance beyond what setting the other properties on the control can do, you create a <xref:System.Windows.Controls.ControlTemplate>.</span></span>

<span data-ttu-id="e7330-113">Ve většině uživatelských rozhraní má tlačítko stejný obecný vzhled: obdélník s nějakým textem.</span><span class="sxs-lookup"><span data-stu-id="e7330-113">In most user interfaces, a button has the same general appearance: a rectangle with some text.</span></span> <span data-ttu-id="e7330-114">Pokud jste chtěli vytvořit zaoblené tlačítko, mohli byste vytvořit nový ovládací prvek, který dědí z tlačítka, nebo znovu vytvořit funkci tlačítka.</span><span class="sxs-lookup"><span data-stu-id="e7330-114">If you wanted to create a rounded button, you could create a new control that inherits from the button or recreates the functionality of the button.</span></span> <span data-ttu-id="e7330-115">Kromě toho nový uživatelský ovládací prvek poskytne kruhový vizuál.</span><span class="sxs-lookup"><span data-stu-id="e7330-115">In addition, the new user control would provide the circular visual.</span></span>

<span data-ttu-id="e7330-116">Vytváření nových ovládacích prvků můžete vyhnout přizpůsobením vizuálního rozložení existujícího ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e7330-116">You can avoid creating new controls by customizing the visual layout of an existing control.</span></span> <span data-ttu-id="e7330-117">Pomocí zaobleného tlačítka vytvoříte <xref:System.Windows.Controls.ControlTemplate> s požadovaným rozložením vizuálu.</span><span class="sxs-lookup"><span data-stu-id="e7330-117">With a rounded button, you create a <xref:System.Windows.Controls.ControlTemplate> with the desired visual layout.</span></span>

<span data-ttu-id="e7330-118">Na druhé straně, pokud potřebujete ovládací prvek s novými funkcemi, různými vlastnostmi a novými nastaveními, měli byste vytvořit nový <xref:System.Windows.Controls.UserControl> .</span><span class="sxs-lookup"><span data-stu-id="e7330-118">On the other hand, if you need a control with new functionality, different properties, and new settings, you would create a new <xref:System.Windows.Controls.UserControl>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e7330-119">Požadované součásti</span><span class="sxs-lookup"><span data-stu-id="e7330-119">Prerequisites</span></span>

<span data-ttu-id="e7330-120">Vytvořte novou aplikaci WPF a v *MainWindow. XAML* (nebo jiném okně podle vašeho výběru) nastavte následující vlastnosti **\<Window>** elementu:</span><span class="sxs-lookup"><span data-stu-id="e7330-120">Create a new WPF application and in *MainWindow.xaml* (or another window of your choice) set the following properties on the **\<Window>** element:</span></span>

|     |     |
| --- | --- |
| **Title**         | `Template Intro Sample` |
| **SizeToContent** | `WidthAndHeight` |
| **MinWidth**      | `250` |

<span data-ttu-id="e7330-121">Nastavte obsah **\<Window>** elementu na následující XAML:</span><span class="sxs-lookup"><span data-stu-id="e7330-121">Set the content of the **\<Window>** element to the following XAML:</span></span>

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

<span data-ttu-id="e7330-122">V elementu end by soubor *MainWindow. XAML* měl vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="e7330-122">In the end, the *MainWindow.xaml* file should look similar to the following:</span></span>

[!code-xaml[InitialWhole](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#InitialWhole)]

<span data-ttu-id="e7330-123">Pokud aplikaci spouštíte, vypadá to jako na následujícím:</span><span class="sxs-lookup"><span data-stu-id="e7330-123">If you run the application, it looks like the following:</span></span>

![Okno WPF se dvěma nestyle tlačítky](media/create-apply-template/unstyled-button.png)

## <a name="create-a-controltemplate"></a><span data-ttu-id="e7330-125">Vytvoření ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="e7330-125">Create a ControlTemplate</span></span>

<span data-ttu-id="e7330-126">Nejběžnější způsob, jak deklarovat, <xref:System.Windows.Controls.ControlTemplate> je jako prostředek v `Resources` oddílu v souboru XAML.</span><span class="sxs-lookup"><span data-stu-id="e7330-126">The most common way to declare a <xref:System.Windows.Controls.ControlTemplate> is as a resource in the `Resources` section in a XAML file.</span></span> <span data-ttu-id="e7330-127">Vzhledem k tomu, že šablony jsou prostředky, řídí se stejnými pravidly oboru, která se vztahují na všechny prostředky.</span><span class="sxs-lookup"><span data-stu-id="e7330-127">Because templates are resources, they obey the same scoping rules that apply to all resources.</span></span> <span data-ttu-id="e7330-128">Jednoduše řečeno, kde deklarujete šablonu, má vliv na to, kde lze šablonu použít.</span><span class="sxs-lookup"><span data-stu-id="e7330-128">Put simply, where you declare a template affects where the template can be applied.</span></span> <span data-ttu-id="e7330-129">Například pokud deklarujete šablonu v kořenovém elementu souboru XAML definice aplikace, šablonu lze použít kdekoli v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e7330-129">For example, if you declare the template in the root element of your application definition XAML file, the template can be used anywhere in your application.</span></span> <span data-ttu-id="e7330-130">Definujete-li šablonu v okně, mohou šablonu používat pouze ovládací prvky v tomto okně.</span><span class="sxs-lookup"><span data-stu-id="e7330-130">If you define the template in a window, only the controls in that window can use the template.</span></span>

<span data-ttu-id="e7330-131">Chcete-li začít s, přidejte `Window.Resources` element do souboru *MainWindow. XAML* :</span><span class="sxs-lookup"><span data-stu-id="e7330-131">To start with, add a `Window.Resources` element to your *MainWindow.xaml* file:</span></span>

[!code-xaml[WindowResStart](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window2.xaml#WindowResStart)]

<span data-ttu-id="e7330-132">Vytvořte nový **\<ControlTemplate>** s následujícími vlastnostmi:</span><span class="sxs-lookup"><span data-stu-id="e7330-132">Create a new **\<ControlTemplate>** with the following properties set:</span></span>

|     |     |
| --- | --- |
| <span data-ttu-id="e7330-133">**X:Key –**</span><span class="sxs-lookup"><span data-stu-id="e7330-133">**x:Key**</span></span>         | `roundbutton` |
| **TargetType**    | `Button` |

<span data-ttu-id="e7330-134">Tato šablona ovládacího prvku bude jednoduchá:</span><span class="sxs-lookup"><span data-stu-id="e7330-134">This control template will be simple:</span></span>

- <span data-ttu-id="e7330-135">kořenový element ovládacího prvku,<xref:System.Windows.Controls.Grid></span><span class="sxs-lookup"><span data-stu-id="e7330-135">a root element for the control, a <xref:System.Windows.Controls.Grid></span></span>
- <span data-ttu-id="e7330-136"><xref:System.Windows.Shapes.Ellipse>vykreslení zaobleného vzhledu tlačítka</span><span class="sxs-lookup"><span data-stu-id="e7330-136">an <xref:System.Windows.Shapes.Ellipse> to draw the rounded appearance of the button</span></span>
- <span data-ttu-id="e7330-137"><xref:System.Windows.Controls.ContentPresenter>pro zobrazení obsahu tlačítka zadaného uživatelem</span><span class="sxs-lookup"><span data-stu-id="e7330-137">a <xref:System.Windows.Controls.ContentPresenter> to display the user-specified button content</span></span>

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#ControlTemplate)]

### <a name="templatebinding"></a><span data-ttu-id="e7330-138">TemplateBinding</span><span class="sxs-lookup"><span data-stu-id="e7330-138">TemplateBinding</span></span>

<span data-ttu-id="e7330-139">Když vytvoříte nový <xref:System.Windows.Controls.ControlTemplate> , můžete přesto chtít použít veřejné vlastnosti ke změně vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e7330-139">When you create a new <xref:System.Windows.Controls.ControlTemplate>, you still might want to use the public properties to change the control's appearance.</span></span> <span data-ttu-id="e7330-140">Rozšíření značek [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) váže vlastnost prvku, který je v <xref:System.Windows.Controls.ControlTemplate> vlastnosti Public, která je definována ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="e7330-140">The [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) markup extension binds a property of an element that is in the <xref:System.Windows.Controls.ControlTemplate> to a public property that is defined by the control.</span></span> <span data-ttu-id="e7330-141">Když použijete [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md), povolíte vlastnosti ovládacího prvku tak, aby sloužily jako parametry šablony.</span><span class="sxs-lookup"><span data-stu-id="e7330-141">When you use a [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md), you enable properties on the control to act as parameters to the template.</span></span> <span data-ttu-id="e7330-142">To znamená, že když je nastavena vlastnost ovládacího prvku, je tato hodnota předána prvku, který má [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) .</span><span class="sxs-lookup"><span data-stu-id="e7330-142">That is, when a property on a control is set, that value is passed on to the element that has the [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) on it.</span></span>

### <a name="ellipse"></a><span data-ttu-id="e7330-143">Elipsa</span><span class="sxs-lookup"><span data-stu-id="e7330-143">Ellipse</span></span>

<span data-ttu-id="e7330-144">Všimněte si, **:::no-loc text="Fill":::** že **:::no-loc text="Stroke":::** vlastnosti a **\<Ellipse>** prvku jsou vázány k ovládacím prvkům <xref:System.Windows.Controls.Control.Foreground> a <xref:System.Windows.Controls.Control.Background> vlastnostem.</span><span class="sxs-lookup"><span data-stu-id="e7330-144">Notice that the **:::no-loc text="Fill":::** and **:::no-loc text="Stroke":::** properties of the **\<Ellipse>** element are bound to the control's <xref:System.Windows.Controls.Control.Foreground> and <xref:System.Windows.Controls.Control.Background> properties.</span></span>

### <a name="contentpresenter"></a><span data-ttu-id="e7330-145">ContentPresenter</span><span class="sxs-lookup"><span data-stu-id="e7330-145">ContentPresenter</span></span>

<span data-ttu-id="e7330-146">[\<ContentPresenter>](xref:System.Windows.Controls.ContentPresenter)Do šablony se přidá také element.</span><span class="sxs-lookup"><span data-stu-id="e7330-146">A [\<ContentPresenter>](xref:System.Windows.Controls.ContentPresenter) element is also added to the template.</span></span> <span data-ttu-id="e7330-147">Vzhledem k tomu, že je tato šablona navržena pro tlačítko, vezměte v úvahu, že tlačítko dědí z <xref:System.Windows.Controls.ContentControl> .</span><span class="sxs-lookup"><span data-stu-id="e7330-147">Because this template is designed for a button, take into consideration that the button inherits from <xref:System.Windows.Controls.ContentControl>.</span></span> <span data-ttu-id="e7330-148">Tlačítko zobrazí obsah elementu.</span><span class="sxs-lookup"><span data-stu-id="e7330-148">The button presents the content of the element.</span></span> <span data-ttu-id="e7330-149">Můžete nastavit cokoli uvnitř tlačítka, jako je prostý text nebo i jiný ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="e7330-149">You can set anything inside of the button, such as plain text or even another control.</span></span> <span data-ttu-id="e7330-150">Níže jsou uvedené platná tlačítka:</span><span class="sxs-lookup"><span data-stu-id="e7330-150">Both of the following are valid buttons:</span></span>

```xaml
<Button>My Text</Button>

<!-- and -->

<Button>
    <CheckBox>Checkbox in a button</CheckBox>
</Button>
```

<span data-ttu-id="e7330-151">V obou předchozích příkladech se text a zaškrtávací políčko nastaví jako vlastnost [Button. Content](xref:System.Windows.Controls.ContentControl.Content) .</span><span class="sxs-lookup"><span data-stu-id="e7330-151">In both of the previous examples, the text and the checkbox are set as the [Button.Content](xref:System.Windows.Controls.ContentControl.Content) property.</span></span> <span data-ttu-id="e7330-152">Bez ohledu na to, jak je možné obsah prezentovat prostřednictvím **\<ContentPresenter>** , což je to, co dělá šablona.</span><span class="sxs-lookup"><span data-stu-id="e7330-152">Whatever is set as the content can be presented through a **\<ContentPresenter>**, which is what the template does.</span></span>

<span data-ttu-id="e7330-153">Pokud <xref:System.Windows.Controls.ControlTemplate> je použit na <xref:System.Windows.Controls.ContentControl> typ, například `Button` ,, <xref:System.Windows.Controls.ContentPresenter> je prohledán ve stromu elementu.</span><span class="sxs-lookup"><span data-stu-id="e7330-153">If the <xref:System.Windows.Controls.ControlTemplate> is applied to a <xref:System.Windows.Controls.ContentControl> type, such as a `Button`, a <xref:System.Windows.Controls.ContentPresenter> is searched for in the element tree.</span></span> <span data-ttu-id="e7330-154">Pokud `ContentPresenter` je nalezen, šablona automaticky váže vlastnost ovládacího prvku <xref:System.Windows.Controls.ContentControl.Content> na `ContentPresenter` .</span><span class="sxs-lookup"><span data-stu-id="e7330-154">If the `ContentPresenter` is found, the template automatically binds the control's <xref:System.Windows.Controls.ContentControl.Content> property to the `ContentPresenter`.</span></span>

## <a name="use-the-template"></a><span data-ttu-id="e7330-155">Použití šablony</span><span class="sxs-lookup"><span data-stu-id="e7330-155">Use the template</span></span>

<span data-ttu-id="e7330-156">Najděte tlačítka, která byla deklarována na začátku tohoto článku.</span><span class="sxs-lookup"><span data-stu-id="e7330-156">Find the buttons that were declared at the start of this article.</span></span>

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

<span data-ttu-id="e7330-157">Nastavte vlastnost druhého tlačítka <xref:System.Windows.Controls.Control.Template> na `roundbutton` prostředek:</span><span class="sxs-lookup"><span data-stu-id="e7330-157">Set the second button's <xref:System.Windows.Controls.Control.Template> property to the `roundbutton` resource:</span></span>

[!code-xaml[StyledButton](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButton)]

<span data-ttu-id="e7330-158">Pokud projekt spustíte a podíváte se na výsledek, uvidíte, že tlačítko má zaoblené pozadí.</span><span class="sxs-lookup"><span data-stu-id="e7330-158">If you run the project and look at the result, you'll see that the button has a rounded background.</span></span>

![Okno WPF s jedním tlačítkem šablony – tlačítko elipsa](media/create-apply-template/styled-button.png)

<span data-ttu-id="e7330-160">Možná jste si všimli, že tlačítko není kruh, ale je zkosený.</span><span class="sxs-lookup"><span data-stu-id="e7330-160">You may have noticed that the button isn't a circle but is skewed.</span></span> <span data-ttu-id="e7330-161">Vzhledem k tomu, jak **\<Ellipse>** element funguje, se vždy rozšíří, aby vyplnilo dostupný prostor.</span><span class="sxs-lookup"><span data-stu-id="e7330-161">Because of the way the **\<Ellipse>** element works, it always expands to fill the available space.</span></span> <span data-ttu-id="e7330-162">Označit kroužek jako Uniform změnou vlastností Button a na **:::no-loc text="width":::** **:::no-loc text="height":::** stejnou hodnotu:</span><span class="sxs-lookup"><span data-stu-id="e7330-162">Make the circle uniform by changing the button's  **:::no-loc text="width":::** and **:::no-loc text="height":::** properties to the same value:</span></span>

[!code-xaml[StyledButtonSize](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButtonSize)]

![Okno WPF s jedním kulatým tlačítkem šablony](media/create-apply-template/styled-uniform-button.png)

## <a name="add-a-trigger"></a><span data-ttu-id="e7330-164">Přidání triggeru</span><span class="sxs-lookup"><span data-stu-id="e7330-164">Add a Trigger</span></span>

<span data-ttu-id="e7330-165">I když tlačítko s použitou šablonou vypadá jinak, chová se stejně jako jakékoli jiné tlačítko.</span><span class="sxs-lookup"><span data-stu-id="e7330-165">Even though a button with a template applied looks different, it behaves the same as any other button.</span></span> <span data-ttu-id="e7330-166">Po stisknutí tlačítka se <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost aktivuje.</span><span class="sxs-lookup"><span data-stu-id="e7330-166">If you press the button, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event fires.</span></span> <span data-ttu-id="e7330-167">Ale možná jste si všimli, že když přesunete ukazatel myši na tlačítko, vizuály tlačítka se nezmění.</span><span class="sxs-lookup"><span data-stu-id="e7330-167">However, you may have noticed that when you move your mouse over the button, the button's visuals don't change.</span></span> <span data-ttu-id="e7330-168">Tyto interakce vizuálů jsou všechny definované šablonou.</span><span class="sxs-lookup"><span data-stu-id="e7330-168">These visual interactions are all defined by the template.</span></span>

<span data-ttu-id="e7330-169">Díky dynamickým systémům událostí a vlastností, které poskytuje WPF, můžete sledovat konkrétní vlastnost pro určitou hodnotu a pak šablonu v případě potřeby přeformátovat.</span><span class="sxs-lookup"><span data-stu-id="e7330-169">With the dynamic event and property systems that WPF provides, you can watch a specific property for a value and then restyle the template when appropriate.</span></span> <span data-ttu-id="e7330-170">V tomto příkladu budete sledovat <xref:System.Windows.UIElement.IsMouseOver> vlastnost tlačítka.</span><span class="sxs-lookup"><span data-stu-id="e7330-170">In this example, you'll watch the button's <xref:System.Windows.UIElement.IsMouseOver> property.</span></span> <span data-ttu-id="e7330-171">Když je ukazatel myši nad ovládacím prvkem, styl **\<Ellipse>** s novou barvou.</span><span class="sxs-lookup"><span data-stu-id="e7330-171">When the mouse is over the control, style the **\<Ellipse>** with a new color.</span></span> <span data-ttu-id="e7330-172">Tento typ triggeru se označuje jako *PropertyTrigger*.</span><span class="sxs-lookup"><span data-stu-id="e7330-172">This type of trigger is known as a *PropertyTrigger*.</span></span>

<span data-ttu-id="e7330-173">Aby to fungovalo, budete muset přidat název do **\<Ellipse>** , na který můžete odkazovat.</span><span class="sxs-lookup"><span data-stu-id="e7330-173">For this to work, you'll need to add a name to the **\<Ellipse>** that you can reference.</span></span> <span data-ttu-id="e7330-174">Dejte mu název **backgroundElement**.</span><span class="sxs-lookup"><span data-stu-id="e7330-174">Give it the name of **backgroundElement**.</span></span>

[!code-xaml[EllipseName](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml#EllipseName)]

<span data-ttu-id="e7330-175">Dále přidejte nový <xref:System.Windows.Trigger> do kolekce [ControlTemplate. Triggers](xref:System.Windows.Controls.ControlTemplate.Triggers) .</span><span class="sxs-lookup"><span data-stu-id="e7330-175">Next, add a new <xref:System.Windows.Trigger> to the [ControlTemplate.Triggers](xref:System.Windows.Controls.ControlTemplate.Triggers) collection.</span></span> <span data-ttu-id="e7330-176">Aktivační událost bude sledovat `IsMouseOver` událost pro danou hodnotu `true` .</span><span class="sxs-lookup"><span data-stu-id="e7330-176">The trigger will watch the `IsMouseOver` event for the value `true`.</span></span>

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml?name=ControlTemplate&highlight=6-10)]

<span data-ttu-id="e7330-177">Dále přidejte do, **\<Setter>** **\<Trigger>** který změní vlastnost **Fill** na **\<Ellipse>** novou barvu.</span><span class="sxs-lookup"><span data-stu-id="e7330-177">Next, add a **\<Setter>** to the **\<Trigger>** that changes the **Fill** property of the **\<Ellipse>** to a new color.</span></span>

[!code-xaml[MouseOver](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#MouseOver)]

<span data-ttu-id="e7330-178">Spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="e7330-178">Run the project.</span></span> <span data-ttu-id="e7330-179">Všimněte si, že když přesunete ukazatel myši na tlačítko, barva **\<Ellipse>** změn.</span><span class="sxs-lookup"><span data-stu-id="e7330-179">Notice that when you move the mouse over the button, the color of the **\<Ellipse>** changes.</span></span>

![Změna barvy výplně tlačítkem myši se pohybuje přes tlačítko WPF](media/create-apply-template/mouse-move-over-button.gif)

## <a name="use-a-visualstate"></a><span data-ttu-id="e7330-181">Použití VisualState</span><span class="sxs-lookup"><span data-stu-id="e7330-181">Use a VisualState</span></span>

<span data-ttu-id="e7330-182">Vizuální stavy jsou definovány a aktivovány ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="e7330-182">Visual states are defined and triggered by a control.</span></span> <span data-ttu-id="e7330-183">Například když se ukazatel myši přesune nad ovládací prvek, `CommonStates.MouseOver` stav se aktivuje.</span><span class="sxs-lookup"><span data-stu-id="e7330-183">For example, when the mouse is moved on top of the control, the `CommonStates.MouseOver` state is triggered.</span></span> <span data-ttu-id="e7330-184">Můžete animovat změny vlastností na základě aktuálního stavu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e7330-184">You can animate property changes based on the current state of the control.</span></span> <span data-ttu-id="e7330-185">V předchozí části **\<PropertyTrigger>** byl použit příkaz pro změnu popředí tlačítka na hodnotu, `AliceBlue` Pokud `IsMouseOver` byla vlastnost `true` .</span><span class="sxs-lookup"><span data-stu-id="e7330-185">In the previous section, a **\<PropertyTrigger>** was used to change the foreground of the button to `AliceBlue` when the `IsMouseOver` property was `true`.</span></span> <span data-ttu-id="e7330-186">Místo toho vytvořte vizuální stav, který animuje změnu této barvy, čímž zajistíte hladký přechod.</span><span class="sxs-lookup"><span data-stu-id="e7330-186">Instead, create a visual state that animates the change of this color, providing a smooth transition.</span></span> <span data-ttu-id="e7330-187">Další informace o *VisualStates*naleznete v tématu [styly a šablony v WPF](../fundamentals/styles-templates-overview.md#visual-states).</span><span class="sxs-lookup"><span data-stu-id="e7330-187">For more information about *VisualStates*, see [Styles and templates in WPF](../fundamentals/styles-templates-overview.md#visual-states).</span></span>

<span data-ttu-id="e7330-188">Chcete-li převést na **\<PropertyTrigger>** animovaný vizuální stav, nejprve odeberte **\<ControlTemplate.Triggers>** prvek ze šablony.</span><span class="sxs-lookup"><span data-stu-id="e7330-188">To convert the **\<PropertyTrigger>** to an animated visual state, First, remove the **\<ControlTemplate.Triggers>** element from your template.</span></span>

[!code-xaml[CleanTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#CleanTemplate)]

<span data-ttu-id="e7330-189">Dále v **\<Grid>** kořenovém adresáři šablony ovládacího prvku přidejte **\<VisualStateManager.VisualStateGroups>** element **\<VisualStateGroup>** pro `CommonStates` .</span><span class="sxs-lookup"><span data-stu-id="e7330-189">Next, in the **\<Grid>** root of the control template, add the **\<VisualStateManager.VisualStateGroups>** element with a **\<VisualStateGroup>** for `CommonStates`.</span></span> <span data-ttu-id="e7330-190">Definujte dva stavy `Normal` a `MouseOver` .</span><span class="sxs-lookup"><span data-stu-id="e7330-190">Define two states, `Normal` and `MouseOver`.</span></span>

[!code-xaml[VisualState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#VisualState)]

<span data-ttu-id="e7330-191">V **\<VisualState>** případě, že je tento stav aktivován, jsou aplikovány jakékoli animace definované v.</span><span class="sxs-lookup"><span data-stu-id="e7330-191">Any animations defined in a **\<VisualState>** are applied when that state is triggered.</span></span> <span data-ttu-id="e7330-192">Vytváření animací pro každý stav</span><span class="sxs-lookup"><span data-stu-id="e7330-192">Create animations for each state.</span></span> <span data-ttu-id="e7330-193">Animace jsou umístěny uvnitř **\<Storyboard>** elementu.</span><span class="sxs-lookup"><span data-stu-id="e7330-193">Animations are put inside of a **\<Storyboard>** element.</span></span> <span data-ttu-id="e7330-194">Další informace o scénářích najdete v tématu [Přehled scénářů](../../framework/wpf/graphics-multimedia/storyboards-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e7330-194">For more information about storyboards, see [Storyboards Overview](../../framework/wpf/graphics-multimedia/storyboards-overview.md).</span></span>

- <span data-ttu-id="e7330-195">Normální</span><span class="sxs-lookup"><span data-stu-id="e7330-195">Normal</span></span>

  <span data-ttu-id="e7330-196">Tento stav animuje výplň elipsy a obnoví ji do barvy ovládacího prvku `Background` .</span><span class="sxs-lookup"><span data-stu-id="e7330-196">This state animates the ellipse fill, restoring it to the control's `Background` color.</span></span>

  [!code-xaml[NormalState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#NormalState)]

- <span data-ttu-id="e7330-197">MouseOver</span><span class="sxs-lookup"><span data-stu-id="e7330-197">MouseOver</span></span>

  <span data-ttu-id="e7330-198">Tento stav animuje barvu elipsy `Background` na novou barvu: `Yellow` .</span><span class="sxs-lookup"><span data-stu-id="e7330-198">This state animates the ellipse `Background` color to a new color: `Yellow`.</span></span>

  [!code-xaml[MouseOverState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#MouseOverState)]

<span data-ttu-id="e7330-199">**\<ControlTemplate>** By měl nyní vypadat takto.</span><span class="sxs-lookup"><span data-stu-id="e7330-199">The **\<ControlTemplate>** should now look like the following.</span></span>

[!code-xaml[FinalTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window7.xaml#FinalTemplate)]

<span data-ttu-id="e7330-200">Spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="e7330-200">Run the project.</span></span> <span data-ttu-id="e7330-201">Všimněte si, že když přesunete ukazatel myši na tlačítko, barva **\<Ellipse>** animace.</span><span class="sxs-lookup"><span data-stu-id="e7330-201">Notice that when you move the mouse over the button, the color of the **\<Ellipse>** animates.</span></span>

![Změna barvy výplně tlačítkem myši se pohybuje přes tlačítko WPF](media/create-apply-template/mouse-move-over-button-visualstate.gif)

## <a name="next-steps"></a><span data-ttu-id="e7330-203">Další kroky</span><span class="sxs-lookup"><span data-stu-id="e7330-203">Next steps</span></span>

- [<span data-ttu-id="e7330-204">Vytvoření stylu pro ovládací prvek v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="e7330-204">Create a style for a control in WPF</span></span>](../fundamentals/styles-templates-create-apply-style.md)
- [<span data-ttu-id="e7330-205">Styly a šablony v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="e7330-205">Styles and templates in WPF</span></span>](../fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="e7330-206">Přehled prostředků XAML</span><span class="sxs-lookup"><span data-stu-id="e7330-206">Overview of XAML Resources</span></span>](../fundamentals/xaml-resources-define.md)
