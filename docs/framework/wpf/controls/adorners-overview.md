---
title: Přehled doplňků
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: b41c1f10f7e1b7c1799fd27270a3eeb9899ceeb6
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111176"
---
# <a name="adorners-overview"></a><span data-ttu-id="66ffb-102">Přehled doplňků</span><span class="sxs-lookup"><span data-stu-id="66ffb-102">Adorners Overview</span></span>

<span data-ttu-id="66ffb-103">Adorners jsou speciální <xref:System.Windows.FrameworkElement>typ , který slouží k poskytování vizuální podněty pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="66ffb-103">Adorners are a special type of <xref:System.Windows.FrameworkElement>, used to provide visual cues to a user.</span></span> <span data-ttu-id="66ffb-104">Mezi další použití Adorners lze přidat funkční popisovače prvků nebo poskytnout informace o stavu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="66ffb-104">Among other uses, Adorners can be used to add functional handles to elements or provide state information about a control.</span></span>

## <a name="about-adorners"></a><span data-ttu-id="66ffb-105">O adorners</span><span class="sxs-lookup"><span data-stu-id="66ffb-105">About Adorners</span></span>

<span data-ttu-id="66ffb-106">A <xref:System.Windows.Documents.Adorner> je <xref:System.Windows.FrameworkElement> vlastní, který <xref:System.Windows.UIElement>je vázán na .</span><span class="sxs-lookup"><span data-stu-id="66ffb-106">An <xref:System.Windows.Documents.Adorner> is a custom <xref:System.Windows.FrameworkElement> that is bound to a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="66ffb-107">Adorners jsou vykresleny <xref:System.Windows.Documents.AdornerLayer>v , což je vykreslovací povrch, který je vždy nad objektem adorned element nebo kolekce adorned prvky.</span><span class="sxs-lookup"><span data-stu-id="66ffb-107">Adorners are rendered in an <xref:System.Windows.Documents.AdornerLayer>, which is a rendering surface that is always on top of the adorned element or a collection of adorned elements.</span></span> <span data-ttu-id="66ffb-108">Vykreslování adorner <xref:System.Windows.UIElement> je nezávislý na vykreslování adorner je vázán.</span><span class="sxs-lookup"><span data-stu-id="66ffb-108">Rendering of an adorner is independent from rendering of the <xref:System.Windows.UIElement> that the adorner is bound to.</span></span> <span data-ttu-id="66ffb-109">Adorner je obvykle umístěn vzhledem k prvku, ke kterému je vázán, pomocí standardní 2D souřadnice původu umístěného v levém horním rohu adorned elementu.</span><span class="sxs-lookup"><span data-stu-id="66ffb-109">An adorner is typically positioned relative to the element to which it is bound, using the standard 2D coordinate origin located at the upper-left of the adorned element.</span></span>

<span data-ttu-id="66ffb-110">Běžné aplikace pro adorners patří:</span><span class="sxs-lookup"><span data-stu-id="66ffb-110">Common applications for adorners include:</span></span>

- <span data-ttu-id="66ffb-111">Přidání funkčních <xref:System.Windows.UIElement> úchytů, které umožňují uživateli nějakým způsobem manipulovat s prvkem (změna velikosti, otočení, změna umístění atd.).</span><span class="sxs-lookup"><span data-stu-id="66ffb-111">Adding functional handles to a <xref:System.Windows.UIElement> that enable a user to manipulate the element in some way (resize, rotate, reposition, etc.).</span></span>
- <span data-ttu-id="66ffb-112">Poskytněte vizuální zpětnou vazbu k označení různých stavů nebo v reakci na různé události.</span><span class="sxs-lookup"><span data-stu-id="66ffb-112">Provide visual feedback to indicate various states, or in response to various events.</span></span>
- <span data-ttu-id="66ffb-113">Překryvné vizuální <xref:System.Windows.UIElement>dekorace na .</span><span class="sxs-lookup"><span data-stu-id="66ffb-113">Overlay visual decorations on a <xref:System.Windows.UIElement>.</span></span>
- <span data-ttu-id="66ffb-114">Vizuálně maskovat nebo přepsat část <xref:System.Windows.UIElement>nebo celý .</span><span class="sxs-lookup"><span data-stu-id="66ffb-114">Visually mask or override part or all of a <xref:System.Windows.UIElement>.</span></span>

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="66ffb-115">poskytuje základní rámec pro zdobení vizuálních prvků.</span><span class="sxs-lookup"><span data-stu-id="66ffb-115">provides a basic framework for adorning visual elements.</span></span> <span data-ttu-id="66ffb-116">V následující tabulce jsou uvedeny primární typy používané při ozdobení objektů a jejich účel.</span><span class="sxs-lookup"><span data-stu-id="66ffb-116">The following table lists the primary types used when adorning objects, and their purpose.</span></span> <span data-ttu-id="66ffb-117">Následuje několik příkladů použití:</span><span class="sxs-lookup"><span data-stu-id="66ffb-117">Several usage examples follow:</span></span>

|||
|-|-|
|<xref:System.Windows.Documents.Adorner>|<span data-ttu-id="66ffb-118">Abstraktní základní třídy, ze kterého zdědí všechny konkrétní adorner implementace.</span><span class="sxs-lookup"><span data-stu-id="66ffb-118">An abstract base class from which all concrete adorner implementations inherit.</span></span>|
|<xref:System.Windows.Documents.AdornerLayer>|<span data-ttu-id="66ffb-119">Třída představující vykreslovací vrstvu pro adorner (y) jednoho nebo více ozdobných prvků.</span><span class="sxs-lookup"><span data-stu-id="66ffb-119">A class representing a rendering layer for the adorner(s) of one or more adorned elements.</span></span>|
|<xref:System.Windows.Documents.AdornerDecorator>|<span data-ttu-id="66ffb-120">Třída, která umožňuje adorner vrstvy, které mají být spojeny s kolekcí prvků.</span><span class="sxs-lookup"><span data-stu-id="66ffb-120">A class that enables an adorner layer to be associated with a collection of elements.</span></span>|

## <a name="implementing-a-custom-adorner"></a><span data-ttu-id="66ffb-121">Implementace vlastní adorner</span><span class="sxs-lookup"><span data-stu-id="66ffb-121">Implementing a Custom Adorner</span></span>

<span data-ttu-id="66ffb-122">Adorners rámec poskytuje [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] je určena především pro podporu vytváření vlastní adorners.</span><span class="sxs-lookup"><span data-stu-id="66ffb-122">The adorners framework provided by [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is intended primarily to support the creation of custom adorners.</span></span> <span data-ttu-id="66ffb-123">Vlastní adorner je vytvořen implementací třídy, <xref:System.Windows.Documents.Adorner> která dědí z abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="66ffb-123">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>

> [!NOTE]
> <span data-ttu-id="66ffb-124">Nadřazený <xref:System.Windows.Documents.Adorner> <xref:System.Windows.Documents.AdornerLayer> je, který <xref:System.Windows.Documents.Adorner>vykreslí , není prvek zdobí.</span><span class="sxs-lookup"><span data-stu-id="66ffb-124">The parent of an <xref:System.Windows.Documents.Adorner> is the <xref:System.Windows.Documents.AdornerLayer> that renders the <xref:System.Windows.Documents.Adorner>, not the element being adorned.</span></span>

<span data-ttu-id="66ffb-125">Následující příklad ukazuje třídu, která implementuje jednoduchý adorner.</span><span class="sxs-lookup"><span data-stu-id="66ffb-125">The following example shows a class that implements a simple adorner.</span></span> <span data-ttu-id="66ffb-126">Příklad adorner jednoduše zdobí rohy <xref:System.Windows.UIElement> s kruhy.</span><span class="sxs-lookup"><span data-stu-id="66ffb-126">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles.</span></span>

[!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
[!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]
  
<span data-ttu-id="66ffb-127">Následující obrázek znázorňuje SimpleCircleAdorner aplikovaný na <xref:System.Windows.Controls.TextBox>:</span><span class="sxs-lookup"><span data-stu-id="66ffb-127">The following image shows the SimpleCircleAdorner applied to a <xref:System.Windows.Controls.TextBox>:</span></span>

![Snímek obrazovky s ozdobným textovým polem](./media/adorners-overview/simplecircleadorner-textbox.png)

## <a name="rendering-behavior-for-adorners"></a><span data-ttu-id="66ffb-129">Chování vykreslování pro adornery</span><span class="sxs-lookup"><span data-stu-id="66ffb-129">Rendering Behavior for Adorners</span></span>

<span data-ttu-id="66ffb-130">Je důležité si uvědomit, že adorners neobsahují žádné vlastní vykreslování chování; zajištění, že adorner vykreslí je odpovědnost adorner implementer.</span><span class="sxs-lookup"><span data-stu-id="66ffb-130">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span> <span data-ttu-id="66ffb-131">Běžným způsobem implementace chování vykreslování je přepsat metodu <xref:System.Windows.UIElement.OnRender%2A> a použít jeden nebo více <xref:System.Windows.Media.DrawingContext> objektů k vykreslení vizuálů adorner podle potřeby (jak je znázorněno v příkladu výše).</span><span class="sxs-lookup"><span data-stu-id="66ffb-131">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in the example above).</span></span>

> [!NOTE]
> <span data-ttu-id="66ffb-132">Vše, co je umístěno ve vrstvě adorner, je vykresleno nad ostatními styly, které jste nastavili.</span><span class="sxs-lookup"><span data-stu-id="66ffb-132">Anything placed in the adorner layer is rendered on top of the rest of any styles you have set.</span></span> <span data-ttu-id="66ffb-133">Jinými slovy adorners jsou vždy vizuálně na vrcholu a nelze přepsat pomocí pořadí vykreslovat.</span><span class="sxs-lookup"><span data-stu-id="66ffb-133">In other words, adorners are always visually on top and cannot be overridden using z-order.</span></span>

## <a name="events-and-hit-testing"></a><span data-ttu-id="66ffb-134">Události a testování přístupů</span><span class="sxs-lookup"><span data-stu-id="66ffb-134">Events and Hit Testing</span></span>

<span data-ttu-id="66ffb-135">Adorners přijímat vstupní události, <xref:System.Windows.FrameworkElement>stejně jako všechny ostatní .</span><span class="sxs-lookup"><span data-stu-id="66ffb-135">Adorners receive input events just like any other <xref:System.Windows.FrameworkElement>.</span></span>  <span data-ttu-id="66ffb-136">Vzhledem k tomu, že adorner má vždy vyšší pořadí vykreslování <xref:System.Windows.UIElement.Drop> <xref:System.Windows.UIElement.MouseMove>než prvek, který zdobí, adorner obdrží vstupní události (například nebo ) které mohou být určeny pro základní adorned element.</span><span class="sxs-lookup"><span data-stu-id="66ffb-136">Because an adorner always has a higher z-order than the element it adorns, the adorner receives input events (such as <xref:System.Windows.UIElement.Drop> or <xref:System.Windows.UIElement.MouseMove>) that may be intended for the underlying adorned element.</span></span>  <span data-ttu-id="66ffb-137">Adorner můžete naslouchat pro určité vstupní události a předat je na základní adorned prvek re-raising události.</span><span class="sxs-lookup"><span data-stu-id="66ffb-137">An adorner can listen for certain input events and pass these on to the underlying adorned element by re-raising the event.</span></span>

<span data-ttu-id="66ffb-138">Chcete-li povolit předávací přístupů testování <xref:System.Windows.UIElement.IsHitTestVisible%2A> prvků pod adorner, nastavte vlastnost test přístupů na **false** na adorner.</span><span class="sxs-lookup"><span data-stu-id="66ffb-138">To enable pass-through hit testing of elements under an adorner, set the hit test <xref:System.Windows.UIElement.IsHitTestVisible%2A> property to **false** on the adorner.</span></span>  <span data-ttu-id="66ffb-139">Další informace o testování přístupů naleznete [v tématu Testování přístupů ve vizuální vrstvě](../graphics-multimedia/hit-testing-in-the-visual-layer.md).</span><span class="sxs-lookup"><span data-stu-id="66ffb-139">For more information about hit testing, see [Hit Testing in the Visual Layer](../graphics-multimedia/hit-testing-in-the-visual-layer.md).</span></span>

## <a name="adorning-a-single-uielement"></a><span data-ttu-id="66ffb-140">Ozdobit jeden prvek uielement</span><span class="sxs-lookup"><span data-stu-id="66ffb-140">Adorning a Single UIElement</span></span>

<span data-ttu-id="66ffb-141">Chcete-li svázat adorner na konkrétní <xref:System.Windows.UIElement>, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="66ffb-141">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>

1. <span data-ttu-id="66ffb-142">Volání statické <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> metody získat <xref:System.Windows.Documents.AdornerLayer> objekt <xref:System.Windows.UIElement> pro být adorned.</span><span class="sxs-lookup"><span data-stu-id="66ffb-142">Call the static method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="66ffb-143"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>prochází vizuální strom, počínaje zadanou <xref:System.Windows.UIElement>a vrátí první adorner vrstvu, kterou najde.</span><span class="sxs-lookup"><span data-stu-id="66ffb-143"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified <xref:System.Windows.UIElement>, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="66ffb-144">(Pokud jsou nalezeny žádné adorner vrstvy, metoda vrátí null.)</span><span class="sxs-lookup"><span data-stu-id="66ffb-144">(If no adorner layers are found, the method returns null.)</span></span>

2. <span data-ttu-id="66ffb-145">Volání <xref:System.Windows.Documents.AdornerLayer.Add%2A> metody svázat adorner k <xref:System.Windows.UIElement>cíli .</span><span class="sxs-lookup"><span data-stu-id="66ffb-145">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target <xref:System.Windows.UIElement>.</span></span>

 <span data-ttu-id="66ffb-146">Následující příklad váže SimpleCircleAdorner (viz výše) <xref:System.Windows.Controls.TextBox> s názvem *myTextBox*:</span><span class="sxs-lookup"><span data-stu-id="66ffb-146">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*:</span></span>

 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]

> [!NOTE]
> <span data-ttu-id="66ffb-147">Použití [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] svázat adorner na jiný prvek není aktuálně podporována.</span><span class="sxs-lookup"><span data-stu-id="66ffb-147">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>

## <a name="adorning-the-children-of-a-panel"></a><span data-ttu-id="66ffb-148">Ozdobit děti panelu</span><span class="sxs-lookup"><span data-stu-id="66ffb-148">Adorning the Children of a Panel</span></span>

<span data-ttu-id="66ffb-149">Chcete-li svázat adorner <xref:System.Windows.Controls.Panel>s podřízenými objekty , postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="66ffb-149">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>

1. <span data-ttu-id="66ffb-150">Volání `static` metody <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> najít adorner vrstvu pro prvek, jehož podřízené objekty mají být adorned.</span><span class="sxs-lookup"><span data-stu-id="66ffb-150">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to find an adorner layer for the element whose children are to be adorned.</span></span>

2. <span data-ttu-id="66ffb-151">Výčet prostřednictvím podřízených nadřazený prvek a volání <xref:System.Windows.Documents.AdornerLayer.Add%2A> metody svázat adorner na každý podřízený prvek.</span><span class="sxs-lookup"><span data-stu-id="66ffb-151">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>

<span data-ttu-id="66ffb-152">Následující příklad váže SimpleCircleAdorner (viz výše) na <xref:System.Windows.Controls.StackPanel> podřízené s názvem *myStackPanel*:</span><span class="sxs-lookup"><span data-stu-id="66ffb-152">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*:</span></span>

[!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
[!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]

## <a name="see-also"></a><span data-ttu-id="66ffb-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="66ffb-153">See also</span></span>

- <xref:System.Windows.Media.AdornerHitTestResult>
- [<span data-ttu-id="66ffb-154">Přehled objektů Shape a základního kreslení ve WPF</span><span class="sxs-lookup"><span data-stu-id="66ffb-154">Shapes and Basic Drawing in WPF Overview</span></span>](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="66ffb-155">Malování pomocí obrázků, kreseb a vizuálních objektů</span><span class="sxs-lookup"><span data-stu-id="66ffb-155">Painting with Images, Drawings, and Visuals</span></span>](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="66ffb-156">Přehled vykreslovaných objektů</span><span class="sxs-lookup"><span data-stu-id="66ffb-156">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="66ffb-157">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="66ffb-157">How-to Topics</span></span>](adorners-how-to-topics.md)
