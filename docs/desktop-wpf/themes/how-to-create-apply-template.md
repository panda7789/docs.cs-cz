---
title: Vytvoření šablony v aplikaci WPF - .NET Desktop
description: Zjistěte, jak vytvořit a odkazovat na šablonu ovládacího prvku v systému Windows Presentation Foundation a .NET Core.
author: thraka
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
ms.openlocfilehash: c901864d387b8de976bbfa9a9b3c14a7d5a0b4d8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "82071246"
---
# <a name="create-a-template-for-a-control"></a><span data-ttu-id="f02f3-103">Vytvoření šablony pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="f02f3-103">Create a template for a control</span></span>

<span data-ttu-id="f02f3-104">Pomocí windows presentation foundation (WPF) můžete přizpůsobit vizuální strukturu a chování existujícího ovládacího prvku pomocí vlastní opakovaně použitelné šablony.</span><span class="sxs-lookup"><span data-stu-id="f02f3-104">With Windows Presentation Foundation (WPF), you can customize an existing control's visual structure and behavior with your own reusable template.</span></span> <span data-ttu-id="f02f3-105">Šablony lze použít globálně na vaši aplikaci, okna a stránky nebo přímo na ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="f02f3-105">Templates can be applied globally to your application, windows and pages, or directly to controls.</span></span> <span data-ttu-id="f02f3-106">Většina scénářů, které vyžadují vytvoření nového ovládacího prvku, může být pokryta místo toho vytvoření množení nové šablony pro existující ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="f02f3-106">Most scenarios that require you to create a new control can be covered by instead creating a new template for an existing control.</span></span>

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

<span data-ttu-id="f02f3-107">V tomto článku se budete zabývat vytvořením nového <xref:System.Windows.Controls.ControlTemplate> ovládacího <xref:System.Windows.Controls.Button> prvku.</span><span class="sxs-lookup"><span data-stu-id="f02f3-107">In this article, you'll explore creating a new <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>

## <a name="when-to-create-a-controltemplate"></a><span data-ttu-id="f02f3-108">Kdy vytvořit šablonu ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="f02f3-108">When to create a ControlTemplate</span></span>

<span data-ttu-id="f02f3-109">Ovládací prvky mají <xref:System.Windows.Controls.Border.Background%2A>mnoho <xref:System.Windows.Controls.Control.Foreground%2A>vlastností, například , a <xref:System.Windows.Controls.Control.FontFamily%2A>.</span><span class="sxs-lookup"><span data-stu-id="f02f3-109">Controls have many properties, such as <xref:System.Windows.Controls.Border.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, and <xref:System.Windows.Controls.Control.FontFamily%2A>.</span></span> <span data-ttu-id="f02f3-110">Tyto vlastnosti řídí různé aspekty vzhledu ovládacího prvku, ale změny, které můžete provést nastavením těchto vlastností, jsou omezené.</span><span class="sxs-lookup"><span data-stu-id="f02f3-110">These properties control different aspects of the control's appearance, but the changes that you can make by setting these properties are limited.</span></span> <span data-ttu-id="f02f3-111">Můžete například nastavit <xref:System.Windows.Controls.Control.Foreground%2A> vlastnost na <xref:System.Windows.Controls.Control.FontStyle%2A> modrou a kurzívu <xref:System.Windows.Controls.CheckBox>na .</span><span class="sxs-lookup"><span data-stu-id="f02f3-111">For example, you can set the <xref:System.Windows.Controls.Control.Foreground%2A> property to blue and <xref:System.Windows.Controls.Control.FontStyle%2A> to italic on a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="f02f3-112">Pokud chcete přizpůsobit vzhled ovládacího prvku nad rámec toho, co může nastavení <xref:System.Windows.Controls.ControlTemplate>ostatních vlastností v ovládacím prvku provést, vytvořte .</span><span class="sxs-lookup"><span data-stu-id="f02f3-112">When you want to customize the control's appearance beyond what setting the other properties on the control can do, you create a <xref:System.Windows.Controls.ControlTemplate>.</span></span>

<span data-ttu-id="f02f3-113">Ve většině uživatelských rozhraní má tlačítko stejný celkový vzhled: obdélník s určitým textem.</span><span class="sxs-lookup"><span data-stu-id="f02f3-113">In most user interfaces, a button has the same general appearance: a rectangle with some text.</span></span> <span data-ttu-id="f02f3-114">Pokud chcete vytvořit zaoblené tlačítko, můžete vytvořit nový ovládací prvek, který dědí z tlačítka nebo znovu vytvoří funkce tlačítka.</span><span class="sxs-lookup"><span data-stu-id="f02f3-114">If you wanted to create a rounded button, you could create a new control that inherits from the button or recreates the functionality of the button.</span></span> <span data-ttu-id="f02f3-115">Kromě toho nový uživatelský ovládací prvek by poskytnout kruhový vizuál.</span><span class="sxs-lookup"><span data-stu-id="f02f3-115">In addition, the new user control would provide the circular visual.</span></span>

<span data-ttu-id="f02f3-116">Můžete se vyhnout vytváření nových ovládacích prvků přizpůsobením vizuální rozložení existujícího ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f02f3-116">You can avoid creating new controls by customizing the visual layout of an existing control.</span></span> <span data-ttu-id="f02f3-117">Se zaobleným tlačítkem vytvoříte a <xref:System.Windows.Controls.ControlTemplate> s požadovaným vizuálním rozložením.</span><span class="sxs-lookup"><span data-stu-id="f02f3-117">With a rounded button, you create a <xref:System.Windows.Controls.ControlTemplate> with the desired visual layout.</span></span>

<span data-ttu-id="f02f3-118">Na druhou stranu, pokud potřebujete ovládací prvek s novými funkcemi, různými vlastnostmi a novýmnastavením, vytvoříte nový <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="f02f3-118">On the other hand, if you need a control with new functionality, different properties, and new settings, you would create a new <xref:System.Windows.Controls.UserControl>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f02f3-119">Požadované součásti</span><span class="sxs-lookup"><span data-stu-id="f02f3-119">Prerequisites</span></span>

<span data-ttu-id="f02f3-120">Vytvořte novou aplikaci WPF a v *mainwindow.xaml* (nebo jiné okno podle vašeho výběru) nastavit následující vlastnosti na \*\* \<Element Okna>:\*\*</span><span class="sxs-lookup"><span data-stu-id="f02f3-120">Create a new WPF application and in *MainWindow.xaml* (or another window of your choice) set the following properties on the **\<Window>** element:</span></span>

|     |     |
| --- | --- |
| **[!OP.NO-LOC(Title)]**         | `Template Intro Sample` |
| **[!OP.NO-LOC(SizeToContent)]** | `WidthAndHeight` |
| **[!OP.NO-LOC(MinWidth)]**      | `250` |

<span data-ttu-id="f02f3-121">Nastavte obsah elementu \*\* \<Window>\*\* na následující XAML:</span><span class="sxs-lookup"><span data-stu-id="f02f3-121">Set the content of the **\<Window>** element to the following XAML:</span></span>

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

<span data-ttu-id="f02f3-122">Nakonec *mainwindow.xaml* soubor by měl vypadat podobně jako následující:</span><span class="sxs-lookup"><span data-stu-id="f02f3-122">In the end, the *MainWindow.xaml* file should look similar to the following:</span></span>

[!code-xaml[InitialWhole](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#InitialWhole)]

<span data-ttu-id="f02f3-123">Pokud spustíte aplikaci, vypadá to takto:</span><span class="sxs-lookup"><span data-stu-id="f02f3-123">If you run the application, it looks like the following:</span></span>

![Okno WPF se dvěma nestylovými tlačítky](media/create-apply-template/unstyled-button.png)

## <a name="create-a-controltemplate"></a><span data-ttu-id="f02f3-125">Vytvoření šablony ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="f02f3-125">Create a ControlTemplate</span></span>

<span data-ttu-id="f02f3-126">Nejběžnější způsob deklarování <xref:System.Windows.Controls.ControlTemplate> a je `Resources` jako prostředek v části v souboru XAML.</span><span class="sxs-lookup"><span data-stu-id="f02f3-126">The most common way to declare a <xref:System.Windows.Controls.ControlTemplate> is as a resource in the `Resources` section in a XAML file.</span></span> <span data-ttu-id="f02f3-127">Vzhledem k tomu, že šablony jsou prostředky, řídí se stejnými pravidly oboru, která platí pro všechny prostředky.</span><span class="sxs-lookup"><span data-stu-id="f02f3-127">Because templates are resources, they obey the same scoping rules that apply to all resources.</span></span> <span data-ttu-id="f02f3-128">Jednoduše řečeno, kde deklarujete, že šablona ovlivňuje, kde lze šablonu použít.</span><span class="sxs-lookup"><span data-stu-id="f02f3-128">Put simply, where you declare a template affects where the template can be applied.</span></span> <span data-ttu-id="f02f3-129">Pokud například deklarujete šablonu v kořenovém prvku souboru XAML definice aplikace, šablonu lze použít kdekoli v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f02f3-129">For example, if you declare the template in the root element of your application definition XAML file, the template can be used anywhere in your application.</span></span> <span data-ttu-id="f02f3-130">Pokud definujete šablonu v okně, mohou šablonu používat pouze ovládací prvky v tomto okně.</span><span class="sxs-lookup"><span data-stu-id="f02f3-130">If you define the template in a window, only the controls in that window can use the template.</span></span>

<span data-ttu-id="f02f3-131">Chcete-li začít, `Window.Resources` přidejte prvek do souboru *MainWindow.xaml:*</span><span class="sxs-lookup"><span data-stu-id="f02f3-131">To start with, add a `Window.Resources` element to your *MainWindow.xaml* file:</span></span>

[!code-xaml[WindowResStart](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window2.xaml#WindowResStart)]

<span data-ttu-id="f02f3-132">Vytvořte novou \*\* \<>ControlTemplate\*\* s následující sadou vlastností:</span><span class="sxs-lookup"><span data-stu-id="f02f3-132">Create a new **\<ControlTemplate>** with the following properties set:</span></span>

|     |     |
| --- | --- |
| <span data-ttu-id="f02f3-133">**x:Klíč**</span><span class="sxs-lookup"><span data-stu-id="f02f3-133">**x:Key**</span></span>         | `roundbutton` |
| **TargetType**    | `Button` |

<span data-ttu-id="f02f3-134">Tato šablona ovládacího prvku bude jednoduchá:</span><span class="sxs-lookup"><span data-stu-id="f02f3-134">This control template will be simple:</span></span>

- <span data-ttu-id="f02f3-135">kořenový prvek ovládacího prvku,<xref:System.Windows.Controls.Grid></span><span class="sxs-lookup"><span data-stu-id="f02f3-135">a root element for the control, a <xref:System.Windows.Controls.Grid></span></span>
- <span data-ttu-id="f02f3-136">a <xref:System.Windows.Shapes.Ellipse> nakreslit zaoblený vzhled tlačítka</span><span class="sxs-lookup"><span data-stu-id="f02f3-136">an <xref:System.Windows.Shapes.Ellipse> to draw the rounded appearance of the button</span></span>
- <span data-ttu-id="f02f3-137">a <xref:System.Windows.Controls.ContentPresenter> zobrazí obsah tlačítka určeného uživatelem</span><span class="sxs-lookup"><span data-stu-id="f02f3-137">a <xref:System.Windows.Controls.ContentPresenter> to display the user-specified button content</span></span>

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#ControlTemplate)]

### <a name="templatebinding"></a><span data-ttu-id="f02f3-138">Šablona vazba</span><span class="sxs-lookup"><span data-stu-id="f02f3-138">TemplateBinding</span></span>

<span data-ttu-id="f02f3-139">Při vytváření nového <xref:System.Windows.Controls.ControlTemplate>ovládacího prvku můžete stále chtít použít veřejné vlastnosti ke změně vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f02f3-139">When you create a new <xref:System.Windows.Controls.ControlTemplate>, you still might want to use the public properties to change the control's appearance.</span></span> <span data-ttu-id="f02f3-140">Rozšíření značky [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) váže vlastnost prvku, který <xref:System.Windows.Controls.ControlTemplate> je ve veřejné vlastnosti, která je definována ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="f02f3-140">The [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) markup extension binds a property of an element that is in the <xref:System.Windows.Controls.ControlTemplate> to a public property that is defined by the control.</span></span> <span data-ttu-id="f02f3-141">Při použití [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md), povolíte vlastnosti ovládacího prvku působit jako parametry šablony.</span><span class="sxs-lookup"><span data-stu-id="f02f3-141">When you use a [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md), you enable properties on the control to act as parameters to the template.</span></span> <span data-ttu-id="f02f3-142">To znamená, že když je nastavena vlastnost na ovládací prvek, tato hodnota je předána na prvek, který má [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) na něm.</span><span class="sxs-lookup"><span data-stu-id="f02f3-142">That is, when a property on a control is set, that value is passed on to the element that has the [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) on it.</span></span>

### <a name="ellipse"></a><span data-ttu-id="f02f3-143">Elipsa</span><span class="sxs-lookup"><span data-stu-id="f02f3-143">Ellipse</span></span>

<span data-ttu-id="f02f3-144">Všimněte **:::no-loc text="Fill":::** si, že a **:::no-loc text="Stroke":::** vlastnosti \*\* \<elementu elipsy\*\* <xref:System.Windows.Controls.Control.Background>>jsou vázány na vlastnosti ovládacího <xref:System.Windows.Controls.Control.Foreground> prvku a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f02f3-144">Notice that the **:::no-loc text="Fill":::** and **:::no-loc text="Stroke":::** properties of the **\<Ellipse>** element are bound to the control's <xref:System.Windows.Controls.Control.Foreground> and <xref:System.Windows.Controls.Control.Background> properties.</span></span>

### <a name="contentpresenter"></a><span data-ttu-id="f02f3-145">Contentpresenter</span><span class="sxs-lookup"><span data-stu-id="f02f3-145">ContentPresenter</span></span>

<span data-ttu-id="f02f3-146">Do šablony je také přidán prvek [ \<ContentPresenter>.](xref:System.Windows.Controls.ContentPresenter)</span><span class="sxs-lookup"><span data-stu-id="f02f3-146">A [\<ContentPresenter>](xref:System.Windows.Controls.ContentPresenter) element is also added to the template.</span></span> <span data-ttu-id="f02f3-147">Vzhledem k tomu, že tato šablona je určena <xref:System.Windows.Controls.ContentControl>pro tlačítko, vezměte v úvahu, že tlačítko dědí z .</span><span class="sxs-lookup"><span data-stu-id="f02f3-147">Because this template is designed for a button, take into consideration that the button inherits from <xref:System.Windows.Controls.ContentControl>.</span></span> <span data-ttu-id="f02f3-148">Tlačítko představuje obsah prvku.</span><span class="sxs-lookup"><span data-stu-id="f02f3-148">The button presents the content of the element.</span></span> <span data-ttu-id="f02f3-149">Uvnitř tlačítka můžete nastavit cokoli, například prostý text nebo dokonce jiný ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="f02f3-149">You can set anything inside of the button, such as plain text or even another control.</span></span> <span data-ttu-id="f02f3-150">Obě následující tlačítka jsou platná:</span><span class="sxs-lookup"><span data-stu-id="f02f3-150">Both of the following are valid buttons:</span></span>

```xaml
<Button>My Text</Button>

<!-- and -->

<Button>
    <CheckBox>Checkbox in a button</CheckBox>
</Button>
```

<span data-ttu-id="f02f3-151">V obou předchozích příkladech jsou text a zaškrtávací políčko nastaveny jako vlastnost [Button.Content.](xref:System.Windows.Controls.ContentControl.Content)</span><span class="sxs-lookup"><span data-stu-id="f02f3-151">In both of the previous examples, the text and the checkbox are set as the [Button.Content](xref:System.Windows.Controls.ContentControl.Content) property.</span></span> <span data-ttu-id="f02f3-152">Cokoliv je nastaveno jako obsah, může být prezentováno prostřednictvím \*\* \<>ContentPresenter \*\*, což je to, co šablona dělá.</span><span class="sxs-lookup"><span data-stu-id="f02f3-152">Whatever is set as the content can be presented through a **\<ContentPresenter>**, which is what the template does.</span></span>

<span data-ttu-id="f02f3-153">Pokud <xref:System.Windows.Controls.ControlTemplate> je použita <xref:System.Windows.Controls.ContentControl> pro typ, `Button`například , a <xref:System.Windows.Controls.ContentPresenter> je hledána ve stromu prvků.</span><span class="sxs-lookup"><span data-stu-id="f02f3-153">If the <xref:System.Windows.Controls.ControlTemplate> is applied to a <xref:System.Windows.Controls.ContentControl> type, such as a `Button`, a <xref:System.Windows.Controls.ContentPresenter> is searched for in the element tree.</span></span> <span data-ttu-id="f02f3-154">Pokud `ContentPresenter` je nalezen, šablona automaticky sváže <xref:System.Windows.Controls.ContentControl.Content> vlastnost `ContentPresenter`ovládacího prvku na .</span><span class="sxs-lookup"><span data-stu-id="f02f3-154">If the `ContentPresenter` is found, the template automatically binds the control's <xref:System.Windows.Controls.ContentControl.Content> property to the `ContentPresenter`.</span></span>

## <a name="use-the-template"></a><span data-ttu-id="f02f3-155">Použití šablony</span><span class="sxs-lookup"><span data-stu-id="f02f3-155">Use the template</span></span>

<span data-ttu-id="f02f3-156">Najít tlačítka, které byly deklarovány na začátku tohoto článku.</span><span class="sxs-lookup"><span data-stu-id="f02f3-156">Find the buttons that were declared at the start of this article.</span></span>

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

<span data-ttu-id="f02f3-157">Nastavte <xref:System.Windows.Controls.Control.Template> vlastnost druhého tlačítka na `roundbutton` prostředek:</span><span class="sxs-lookup"><span data-stu-id="f02f3-157">Set the second button's <xref:System.Windows.Controls.Control.Template> property to the `roundbutton` resource:</span></span>

[!code-xaml[StyledButton](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButton)]

<span data-ttu-id="f02f3-158">Pokud spustíte projekt a podíváte se na výsledek, uvidíte, že tlačítko má zaoblené pozadí.</span><span class="sxs-lookup"><span data-stu-id="f02f3-158">If you run the project and look at the result, you'll see that the button has a rounded background.</span></span>

![Okno WPF s jedním tlačítkem oválné šablony](media/create-apply-template/styled-button.png)

<span data-ttu-id="f02f3-160">Možná jste si všimli, že tlačítko není kruh, ale je zkosené.</span><span class="sxs-lookup"><span data-stu-id="f02f3-160">You may have noticed that the button isn't a circle but is skewed.</span></span> <span data-ttu-id="f02f3-161">Vzhledem ke způsobu, \*\* \<>\*\* jakým prvek funguje, se vždy zvětšuje tak, aby vyplnil dostupné místo.</span><span class="sxs-lookup"><span data-stu-id="f02f3-161">Because of the way the **\<Ellipse>** element works, it always expands to fill the available space.</span></span> <span data-ttu-id="f02f3-162">Změníte tak, že **:::no-loc text="width":::** **:::no-loc text="height":::** kruh bude jednotný na stejnou hodnotu:</span><span class="sxs-lookup"><span data-stu-id="f02f3-162">Make the circle uniform by changing the button's  **:::no-loc text="width":::** and **:::no-loc text="height":::** properties to the same value:</span></span>

[!code-xaml[StyledButtonSize](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButtonSize)]

![Okno WPF s jedním cyklovým tlačítkem šablony](media/create-apply-template/styled-uniform-button.png)

## <a name="add-a-trigger"></a><span data-ttu-id="f02f3-164">Přidání aktivační události</span><span class="sxs-lookup"><span data-stu-id="f02f3-164">Add a Trigger</span></span>

<span data-ttu-id="f02f3-165">I když tlačítko s použitou šablonou vypadá jinak, chová se stejně jako jakékoli jiné tlačítko.</span><span class="sxs-lookup"><span data-stu-id="f02f3-165">Even though a button with a template applied looks different, it behaves the same as any other button.</span></span> <span data-ttu-id="f02f3-166">Pokud stisknete <xref:System.Windows.Controls.Primitives.ButtonBase.Click> tlačítko, událost se spustí.</span><span class="sxs-lookup"><span data-stu-id="f02f3-166">If you press the button, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event fires.</span></span> <span data-ttu-id="f02f3-167">Možná jste si však všimli, že když přesunete ukazatel myši nad tlačítko, vizuály tlačítka se nezmění.</span><span class="sxs-lookup"><span data-stu-id="f02f3-167">However, you may have noticed that when you move your mouse over the button, the button's visuals don't change.</span></span> <span data-ttu-id="f02f3-168">Všechny tyto vizuální interakce jsou definovány šablonou.</span><span class="sxs-lookup"><span data-stu-id="f02f3-168">These visual interactions are all defined by the template.</span></span>

<span data-ttu-id="f02f3-169">S dynamické události a vlastnosti systémy, které poskytuje WPF, můžete sledovat konkrétní vlastnost pro hodnotu a potom změnit styl šablony v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="f02f3-169">With the dynamic event and property systems that WPF provides, you can watch a specific property for a value and then restyle the template when appropriate.</span></span> <span data-ttu-id="f02f3-170">V tomto příkladu budete sledovat <xref:System.Windows.UIElement.IsMouseOver> vlastnost tlačítka.</span><span class="sxs-lookup"><span data-stu-id="f02f3-170">In this example, you'll watch the button's <xref:System.Windows.UIElement.IsMouseOver> property.</span></span> <span data-ttu-id="f02f3-171">Když je myš nad ovládacím prvkem, styl \*\* \<Elipsa>\*\* s novou barvou.</span><span class="sxs-lookup"><span data-stu-id="f02f3-171">When the mouse is over the control, style the **\<Ellipse>** with a new color.</span></span> <span data-ttu-id="f02f3-172">Tento typ aktivační události se označuje jako *PropertyTrigger*.</span><span class="sxs-lookup"><span data-stu-id="f02f3-172">This type of trigger is known as a *PropertyTrigger*.</span></span>

<span data-ttu-id="f02f3-173">Aby to fungovalo, budete muset přidat název \*\* \<elipsy>,\*\* na které můžete odkazovat.</span><span class="sxs-lookup"><span data-stu-id="f02f3-173">For this to work, you'll need to add a name to the **\<Ellipse>** that you can reference.</span></span> <span data-ttu-id="f02f3-174">Dejte mu název **backgroundElement**.</span><span class="sxs-lookup"><span data-stu-id="f02f3-174">Give it the name of **backgroundElement**.</span></span>

[!code-xaml[EllipseName](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml#EllipseName)]

<span data-ttu-id="f02f3-175">Dále přidejte <xref:System.Windows.Trigger> nové [controlTemplate.Triggers](xref:System.Windows.Controls.ControlTemplate.Triggers) kolekce.</span><span class="sxs-lookup"><span data-stu-id="f02f3-175">Next, add a new <xref:System.Windows.Trigger> to the [ControlTemplate.Triggers](xref:System.Windows.Controls.ControlTemplate.Triggers) collection.</span></span> <span data-ttu-id="f02f3-176">Aktivační událost bude `IsMouseOver` sledovat událost `true`pro hodnotu .</span><span class="sxs-lookup"><span data-stu-id="f02f3-176">The trigger will watch the `IsMouseOver` event for the value `true`.</span></span>

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml?name=ControlTemplate&highlight=6-10)]

<span data-ttu-id="f02f3-177">Dále přidejte \*\* \<setter>\*\* do \*\* \<>aktivační události,\*\* která změní **Fill** vlastnost \*\* \<>elipsy\*\* na novou barvu.</span><span class="sxs-lookup"><span data-stu-id="f02f3-177">Next, add a **\<Setter>** to the **\<Trigger>** that changes the **Fill** property of the **\<Ellipse>** to a new color.</span></span>

[!code-xaml[MouseOver](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#MouseOver)]

<span data-ttu-id="f02f3-178">Spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="f02f3-178">Run the project.</span></span> <span data-ttu-id="f02f3-179">Všimněte si, že při přesunutí myši nad tlačítko se změní barva \*\* \<elipsy>.\*\*</span><span class="sxs-lookup"><span data-stu-id="f02f3-179">Notice that when you move the mouse over the button, the color of the **\<Ellipse>** changes.</span></span>

![přejecími myšpřes tlačítko WPF změnit barvu výplně](media/create-apply-template/mouse-move-over-button.gif)

## <a name="use-a-visualstate"></a><span data-ttu-id="f02f3-181">Použití visualstate</span><span class="sxs-lookup"><span data-stu-id="f02f3-181">Use a VisualState</span></span>

<span data-ttu-id="f02f3-182">Vizuální stavy jsou definovány a spuštěny ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="f02f3-182">Visual states are defined and triggered by a control.</span></span> <span data-ttu-id="f02f3-183">Například při přesunutí myši nad ovládací prvek, `CommonStates.MouseOver` stav se aktivuje.</span><span class="sxs-lookup"><span data-stu-id="f02f3-183">For example, when the mouse is moved on top of the control, the `CommonStates.MouseOver` state is triggered.</span></span> <span data-ttu-id="f02f3-184">Můžete animovat změny vlastností na základě aktuálního stavu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f02f3-184">You can animate property changes based on the current state of the control.</span></span> <span data-ttu-id="f02f3-185">V předchozí části \*\* \<PropertyTrigger>\*\* byl použit ke změně popředí `AliceBlue` tlačítka, `IsMouseOver` když `true`byla vlastnost .</span><span class="sxs-lookup"><span data-stu-id="f02f3-185">In the previous section, a **\<PropertyTrigger>** was used to change the foreground of the button to `AliceBlue` when the `IsMouseOver` property was `true`.</span></span> <span data-ttu-id="f02f3-186">Místo toho vytvořte vizuální stav, který animuje změnu této barvy a poskytuje hladký přechod.</span><span class="sxs-lookup"><span data-stu-id="f02f3-186">Instead, create a visual state that animates the change of this color, providing a smooth transition.</span></span> <span data-ttu-id="f02f3-187">Další informace o *VisualStates*naleznete [v tématu styly a šablony v WPF](../fundamentals/styles-templates-overview.md#visual-states).</span><span class="sxs-lookup"><span data-stu-id="f02f3-187">For more information about *VisualStates*, see [Styles and templates in WPF](../fundamentals/styles-templates-overview.md#visual-states).</span></span>

<span data-ttu-id="f02f3-188">Chcete-li převést \*\* \<>Vlastnost triggeru\*\* do animovaného vizuálního stavu, nejprve odeberte prvek \*\* \<ControlTemplate.Triggers>\*\* ze šablony.</span><span class="sxs-lookup"><span data-stu-id="f02f3-188">To convert the **\<PropertyTrigger>** to an animated visual state, First, remove the **\<ControlTemplate.Triggers>** element from your template.</span></span>

[!code-xaml[CleanTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#CleanTemplate)]

<span data-ttu-id="f02f3-189">Dále `CommonStates`v kořenovém \*\* \<\*\* adresáři grid>šablony ovládacího prvku přidejte prvek \*\* \<VisualStateManager.VisualStateGroups>\*\* s>\*\* \<VisualStateGroup\*\* pro .</span><span class="sxs-lookup"><span data-stu-id="f02f3-189">Next, in the **\<Grid>** root of the control template, add the **\<VisualStateManager.VisualStateGroups>** element with a **\<VisualStateGroup>** for `CommonStates`.</span></span> <span data-ttu-id="f02f3-190">Definujte dva `Normal` `MouseOver`stavy a .</span><span class="sxs-lookup"><span data-stu-id="f02f3-190">Define two states, `Normal` and `MouseOver`.</span></span>

[!code-xaml[VisualState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#VisualState)]

<span data-ttu-id="f02f3-191">Všechny animace definované v \*\* \<visualstate>\*\* jsou použity při aktivaci tohoto stavu.</span><span class="sxs-lookup"><span data-stu-id="f02f3-191">Any animations defined in a **\<VisualState>** are applied when that state is triggered.</span></span> <span data-ttu-id="f02f3-192">Vytvořte animace pro každý stav.</span><span class="sxs-lookup"><span data-stu-id="f02f3-192">Create animations for each state.</span></span> <span data-ttu-id="f02f3-193">Animace jsou umístěny uvnitř \*\* \<Storyboard>\*\* element.</span><span class="sxs-lookup"><span data-stu-id="f02f3-193">Animations are put inside of a **\<Storyboard>** element.</span></span> <span data-ttu-id="f02f3-194">Další informace o scénářích najdete v [tématu Přehled scénářů](../../framework/wpf/graphics-multimedia/storyboards-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f02f3-194">For more information about storyboards, see [Storyboards Overview](../../framework/wpf/graphics-multimedia/storyboards-overview.md).</span></span>

- <span data-ttu-id="f02f3-195">Normální</span><span class="sxs-lookup"><span data-stu-id="f02f3-195">Normal</span></span>

  <span data-ttu-id="f02f3-196">Tento stav animuje výplň elipsy a `Background` obnovuje ji na barvu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f02f3-196">This state animates the ellipse fill, restoring it to the control's `Background` color.</span></span>

  [!code-xaml[NormalState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#NormalState)]

- <span data-ttu-id="f02f3-197">Mouseover</span><span class="sxs-lookup"><span data-stu-id="f02f3-197">MouseOver</span></span>

  <span data-ttu-id="f02f3-198">Tento stav animuje `Background` barvu elipsy `Yellow`na novou barvu: .</span><span class="sxs-lookup"><span data-stu-id="f02f3-198">This state animates the ellipse `Background` color to a new color: `Yellow`.</span></span>

  [!code-xaml[MouseOverState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#MouseOverState)]

<span data-ttu-id="f02f3-199">\*\* \<ControlTemplate>\*\* by nyní měl vypadat takto.</span><span class="sxs-lookup"><span data-stu-id="f02f3-199">The **\<ControlTemplate>** should now look like the following.</span></span>

[!code-xaml[FinalTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window7.xaml#FinalTemplate)]

<span data-ttu-id="f02f3-200">Spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="f02f3-200">Run the project.</span></span> <span data-ttu-id="f02f3-201">Všimněte si, že při pohybu myší nad tlačítkem>barva \*\* \<elipsy\*\* animovat.</span><span class="sxs-lookup"><span data-stu-id="f02f3-201">Notice that when you move the mouse over the button, the color of the **\<Ellipse>** animates.</span></span>

![přejecími myšpřes tlačítko WPF změnit barvu výplně](media/create-apply-template/mouse-move-over-button-visualstate.gif)

## <a name="next-steps"></a><span data-ttu-id="f02f3-203">Další kroky</span><span class="sxs-lookup"><span data-stu-id="f02f3-203">Next steps</span></span>

- [<span data-ttu-id="f02f3-204">Vytvoření stylu ovládacího prvku ve WPF</span><span class="sxs-lookup"><span data-stu-id="f02f3-204">Create a style for a control in WPF</span></span>](../fundamentals/styles-templates-create-apply-style.md)
- [<span data-ttu-id="f02f3-205">Styly a šablony ve WPF</span><span class="sxs-lookup"><span data-stu-id="f02f3-205">Styles and templates in WPF</span></span>](../fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="f02f3-206">Přehled zdrojů XAML</span><span class="sxs-lookup"><span data-stu-id="f02f3-206">Overview of XAML Resources</span></span>](../fundamentals/xaml-resources-define.md)
