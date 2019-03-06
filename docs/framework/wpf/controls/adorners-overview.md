---
title: Přehled doplňků
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: 9c9d77c9771fd8759530267bd38cb7c0bb59598c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357939"
---
# <a name="adorners-overview"></a><span data-ttu-id="7a852-102">Přehled doplňků</span><span class="sxs-lookup"><span data-stu-id="7a852-102">Adorners Overview</span></span>
<span data-ttu-id="7a852-103">Doplňky pro úpravy jsou zvláštní druh <xref:System.Windows.FrameworkElement>, která slouží k poskytování vizuální upozornění na uživatele.</span><span class="sxs-lookup"><span data-stu-id="7a852-103">Adorners are a special type of <xref:System.Windows.FrameworkElement>, used to provide visual cues to a user.</span></span> <span data-ttu-id="7a852-104">Mimo jiné účely je možné přidat funkční zpracovává na prvky nebo poskytují informace o ovládací prvek stavu doplňků pro úpravy.</span><span class="sxs-lookup"><span data-stu-id="7a852-104">Among other uses, Adorners can be used to add functional handles to elements or provide state information about a control.</span></span>  
  
  
  
<a name="about_Adorners"></a>   
## <a name="about-adorners"></a><span data-ttu-id="7a852-105">O doplňcích</span><span class="sxs-lookup"><span data-stu-id="7a852-105">About Adorners</span></span>  
 <span data-ttu-id="7a852-106"><xref:System.Windows.Documents.Adorner> Je vlastní <xref:System.Windows.FrameworkElement> , který je vázán <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="7a852-106">An <xref:System.Windows.Documents.Adorner> is a custom <xref:System.Windows.FrameworkElement> that is bound to a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="7a852-107">Doplňky pro úpravy se zobrazují v <xref:System.Windows.Documents.AdornerLayer>, což je vykreslovací plochu, který je pořád nad s element nebo kolekci elementů s.</span><span class="sxs-lookup"><span data-stu-id="7a852-107">Adorners are rendered in an <xref:System.Windows.Documents.AdornerLayer>, which is a rendering surface that is always on top of the adorned element or a collection of adorned elements.</span></span> <span data-ttu-id="7a852-108">Vykreslování doplňku je nezávislý na vykreslování <xref:System.Windows.UIElement> svázané doplněk pro úpravy.</span><span class="sxs-lookup"><span data-stu-id="7a852-108">Rendering of an adorner is independent from rendering of the <xref:System.Windows.UIElement> that the adorner is bound to.</span></span> <span data-ttu-id="7a852-109">Pro úpravy je obvykle umístěn vzhledem k elementu, ke kterému je vázán, pomocí standardní počátek souřadnic 2D nachází v levém horním rohu elementu s.</span><span class="sxs-lookup"><span data-stu-id="7a852-109">An adorner is typically positioned relative to the element to which it is bound, using the standard 2-D coordinate origin located at the upper-left of the adorned element.</span></span>  
  
 <span data-ttu-id="7a852-110">Běžné aplikace pro doplňky pro úpravy patří:</span><span class="sxs-lookup"><span data-stu-id="7a852-110">Common applications for adorners include:</span></span>  
  
-   <span data-ttu-id="7a852-111">Přidání funkčnosti popisovače <xref:System.Windows.UIElement> , který umožní uživateli manipulovat s elementu nějakým způsobem (Změna velikosti, otáčení, změna umístění atd.).</span><span class="sxs-lookup"><span data-stu-id="7a852-111">Adding functional handles to a <xref:System.Windows.UIElement> that enable a user to manipulate the element in some way (resize, rotate, reposition, etc.).</span></span>  
  
-   <span data-ttu-id="7a852-112">Vizuální zpětnou vazbu k označení různých státech nebo v reakci na různé události.</span><span class="sxs-lookup"><span data-stu-id="7a852-112">Provide visual feedback to indicate various states, or in response to various events.</span></span>  
  
-   <span data-ttu-id="7a852-113">Překryv visual dekorace na <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="7a852-113">Overlay visual decorations on a <xref:System.Windows.UIElement>.</span></span>  
  
-   <span data-ttu-id="7a852-114">Vizuálně maskování nebo přepsat některá nebo všechna <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="7a852-114">Visually mask or override part or all of a <xref:System.Windows.UIElement>.</span></span>  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="7a852-115">poskytuje základní rozhraní pro adorning vizuální prvky.</span><span class="sxs-lookup"><span data-stu-id="7a852-115">provides a basic framework for adorning visual elements.</span></span> <span data-ttu-id="7a852-116">Následující tabulka uvádí hlavní typy používané při adorning objekty a jejich účel.</span><span class="sxs-lookup"><span data-stu-id="7a852-116">The following table lists the primary types used when adorning objects, and their purpose.</span></span> <span data-ttu-id="7a852-117">Postupujte podle několik příkladů použití.</span><span class="sxs-lookup"><span data-stu-id="7a852-117">Several usage examples follow.</span></span>  
  
|||  
|-|-|  
|<xref:System.Windows.Documents.Adorner>|<span data-ttu-id="7a852-118">Abstraktní základní třída, ze kterého dědí všechny implementace konkrétní doplněk pro úpravy.</span><span class="sxs-lookup"><span data-stu-id="7a852-118">An abstract base class from which all concrete adorner implementations inherit.</span></span>|  
|<xref:System.Windows.Documents.AdornerLayer>|<span data-ttu-id="7a852-119">Třída představující vrstvu vykreslování pro adorner(s) jeden nebo více elementů s.</span><span class="sxs-lookup"><span data-stu-id="7a852-119">A class representing a rendering layer for the adorner(s) of one or more adorned elements.</span></span>|  
|<xref:System.Windows.Documents.AdornerDecorator>|<span data-ttu-id="7a852-120">Třída, která umožňuje vrstvu doplněk pro úpravy, který se má přidružit kolekci elementů.</span><span class="sxs-lookup"><span data-stu-id="7a852-120">A class that enables an adorner layer to be associated with a collection of elements.</span></span>|  
  
<a name="implement_custom_Adorner"></a>   
## <a name="implementing-a-custom-adorner"></a><span data-ttu-id="7a852-121">Implementace vlastního doplněk pro úpravy</span><span class="sxs-lookup"><span data-stu-id="7a852-121">Implementing a Custom Adorner</span></span>  
 <span data-ttu-id="7a852-122">Doplňky pro úpravy framework poskytované [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] je určený primárně pro vytváření vlastní doplňky pro úpravy.</span><span class="sxs-lookup"><span data-stu-id="7a852-122">The adorners framework provided by [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is intended primarily to support the creation of custom adorners.</span></span> <span data-ttu-id="7a852-123">Vlastní doplněk pro úpravy je vytvořen pomocí implementace, která dědí z abstraktní třídy <xref:System.Windows.Documents.Adorner> třídy.</span><span class="sxs-lookup"><span data-stu-id="7a852-123">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a852-124">Nadřazený prvek <xref:System.Windows.Documents.Adorner> je <xref:System.Windows.Documents.AdornerLayer> , který vykreslí <xref:System.Windows.Documents.Adorner>, není element se opatřený.</span><span class="sxs-lookup"><span data-stu-id="7a852-124">The parent of an <xref:System.Windows.Documents.Adorner> is the <xref:System.Windows.Documents.AdornerLayer> that renders the <xref:System.Windows.Documents.Adorner>, not the element being adorned.</span></span>  
  
 <span data-ttu-id="7a852-125">Následující příklad ukazuje třídu, která implementuje jednoduchou doplněk pro úpravy.</span><span class="sxs-lookup"><span data-stu-id="7a852-125">The following example shows a class that implements a simple adorner.</span></span> <span data-ttu-id="7a852-126">Doplněk pro úpravy příklad jednoduše adorns rohů <xref:System.Windows.UIElement> s kruzích.</span><span class="sxs-lookup"><span data-stu-id="7a852-126">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
 <span data-ttu-id="7a852-127">Následující obrázek ukazuje SimpleCircleAdorner u <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="7a852-127">The following image shows the SimpleCircleAdorner applied to a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 <span data-ttu-id="7a852-128">![Příklad doplňků pro úpravy: S textového pole](./media/adornedtextbox.png "AdornedTextBox")</span><span class="sxs-lookup"><span data-stu-id="7a852-128">![Adorners Example: An adorned TextBox](./media/adornedtextbox.png "AdornedTextBox")</span></span>  
  
<a name="rendering_behavior_for_Adorners"></a>   
## <a name="rendering-behavior-for-adorners"></a><span data-ttu-id="7a852-129">Chování vykreslování pro doplňky pro úpravy</span><span class="sxs-lookup"><span data-stu-id="7a852-129">Rendering Behavior for Adorners</span></span>  
 <span data-ttu-id="7a852-130">Je důležité si uvědomit, že doplňky pro úpravy neobsahují žádné vlastní vykreslování chování; zajištění, že pro úpravy vykreslí zodpovídá za implementátora doplněk pro úpravy.</span><span class="sxs-lookup"><span data-stu-id="7a852-130">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span>   <span data-ttu-id="7a852-131">Běžný způsob implementace chování vykreslování je k přepsání <xref:System.Windows.UIElement.OnRender%2A> metoda a používat jednu nebo více <xref:System.Windows.Media.DrawingContext> objekty k vykreslení doplněk pro úpravy vizuály podle potřeby (jak je znázorněno v příkladu výše).</span><span class="sxs-lookup"><span data-stu-id="7a852-131">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in the example above).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a852-132">Cokoli, co je umístěn ve vrstvě doplněk pro úpravy je vykreslen na zbytek všechny styly, které jste nastavili.</span><span class="sxs-lookup"><span data-stu-id="7a852-132">Anything placed in the adorner layer is rendered on top of the rest of any styles you have set.</span></span> <span data-ttu-id="7a852-133">Jinými slovy doplňky pro úpravy jsou vždy vizuálně nahoře a nedají se přepsat použití pořadí vykreslování.</span><span class="sxs-lookup"><span data-stu-id="7a852-133">In other words, adorners are always visually on top and cannot be overridden using z-order.</span></span>  
  
<a name="adorner_events_hittest"></a>   
## <a name="events-and-hit-testing"></a><span data-ttu-id="7a852-134">Události a volání testování</span><span class="sxs-lookup"><span data-stu-id="7a852-134">Events and Hit Testing</span></span>  
 <span data-ttu-id="7a852-135">Doplňky pro úpravy přijímat události vstupu stejně jako jakýkoli jiný <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="7a852-135">Adorners receive input events just like any other <xref:System.Windows.FrameworkElement>.</span></span>  <span data-ttu-id="7a852-136">Protože doplňku má vždy vyšší pořadí vykreslování než element ho adorns, doplněk pro úpravy přijímá vstupní události (například <xref:System.Windows.UIElement.Drop> nebo <xref:System.Windows.UIElement.MouseMove>), který může být určené pro základní opatřený element.</span><span class="sxs-lookup"><span data-stu-id="7a852-136">Because an adorner always has a higher z-order than the element it adorns, the adorner receives input events (such as <xref:System.Windows.UIElement.Drop> or <xref:System.Windows.UIElement.MouseMove>) that may be intended for the underlying adorned element.</span></span>  <span data-ttu-id="7a852-137">Pro úpravy můžete očekávat určité vstupní události a předat tyto k elementu s základní opětovné vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="7a852-137">An adorner can listen for certain input events and pass these on to the underlying adorned element by re-raising the event.</span></span>  
  
 <span data-ttu-id="7a852-138">Pokud chcete povolit předávací přístupů testování prvků pro úpravy, nastavte průchodů testů <xref:System.Windows.UIElement.IsHitTestVisible%2A> vlastnost **false** na doplněk pro úpravy.</span><span class="sxs-lookup"><span data-stu-id="7a852-138">To enable pass-through hit testing of elements under an adorner, set the hit test <xref:System.Windows.UIElement.IsHitTestVisible%2A> property to **false** on the adorner.</span></span>  <span data-ttu-id="7a852-139">Další informace o přístupů testování najdete v tématu</span><span class="sxs-lookup"><span data-stu-id="7a852-139">For more information about hit testing, see</span></span>  
  
 <span data-ttu-id="7a852-140">[Ověřování pozice ve vizuální vrstvě](../graphics-multimedia/hit-testing-in-the-visual-layer.md).</span><span class="sxs-lookup"><span data-stu-id="7a852-140">[Hit Testing in the Visual Layer](../graphics-multimedia/hit-testing-in-the-visual-layer.md).</span></span>  
  
<a name="adorn_single_element"></a>   
## <a name="adorning-a-single-uielement"></a><span data-ttu-id="7a852-141">Adorning jednoho elementu UIElement</span><span class="sxs-lookup"><span data-stu-id="7a852-141">Adorning a Single UIElement</span></span>  
 <span data-ttu-id="7a852-142">K připojení doplňku k konkrétní <xref:System.Windows.UIElement>, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="7a852-142">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>  
  
1.  <span data-ttu-id="7a852-143">Zavolejte statickou metodu <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> zobrazíte <xref:System.Windows.Documents.AdornerLayer> objekt pro <xref:System.Windows.UIElement> chcete být opatřený.</span><span class="sxs-lookup"><span data-stu-id="7a852-143">Call the static method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="7a852-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> provede se vizuální strom začínající v zadaném <xref:System.Windows.UIElement>a vrátí první vrstvu doplněk pro úpravy, které nalezne.</span><span class="sxs-lookup"><span data-stu-id="7a852-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified <xref:System.Windows.UIElement>, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="7a852-145">(Pokud se nenajdou žádné vrstvy doplněk pro úpravy, metoda vrátí hodnotu null.)</span><span class="sxs-lookup"><span data-stu-id="7a852-145">(If no adorner layers are found, the method returns null.)</span></span>  
  
2.  <span data-ttu-id="7a852-146">Volání <xref:System.Windows.Documents.AdornerLayer.Add%2A> metodu pro vytvoření vazby doplněk pro úpravy k cíli <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="7a852-146">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target <xref:System.Windows.UIElement>.</span></span>  
  
 <span data-ttu-id="7a852-147">Následující příklad vytvoří vazbu SimpleCircleAdorner (popsaný výš) k <xref:System.Windows.Controls.TextBox> s názvem *hodnotu myTextBox*.</span><span class="sxs-lookup"><span data-stu-id="7a852-147">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  <span data-ttu-id="7a852-148">Pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pro vazbu na jiný prvek pro úpravy v tuto chvíli nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="7a852-148">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
<a name="adorn_children_panel"></a>   
## <a name="adorning-the-children-of-a-panel"></a><span data-ttu-id="7a852-149">Adorning podřízených položek panelu</span><span class="sxs-lookup"><span data-stu-id="7a852-149">Adorning the Children of a Panel</span></span>  
 <span data-ttu-id="7a852-150">K připojení doplňku k podřízených položek <xref:System.Windows.Controls.Panel>, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="7a852-150">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>  
  
1.  <span data-ttu-id="7a852-151">Volání `static` metoda <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> najít vrstvu doplněk pro úpravy pro element, jehož potomci mají být opatřený.</span><span class="sxs-lookup"><span data-stu-id="7a852-151">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to find an adorner layer for the element whose children are to be adorned.</span></span>  
  
2.  <span data-ttu-id="7a852-152">Zobrazit výčet prostřednictvím podřízené objekty nadřazeného elementu a volání <xref:System.Windows.Documents.AdornerLayer.Add%2A> metodu připojení doplňku k každý podřízený prvek.</span><span class="sxs-lookup"><span data-stu-id="7a852-152">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>  
  
 <span data-ttu-id="7a852-153">Následující příklad vytvoří vazbu SimpleCircleAdorner (popsaný výš) do podřízených položek <xref:System.Windows.Controls.StackPanel> s názvem *myStackPanel*.</span><span class="sxs-lookup"><span data-stu-id="7a852-153">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
## <a name="see-also"></a><span data-ttu-id="7a852-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7a852-154">See also</span></span>
- <xref:System.Windows.Media.AdornerHitTestResult>
- [<span data-ttu-id="7a852-155">Přehled objektů Shape a základního kreslení ve WPF</span><span class="sxs-lookup"><span data-stu-id="7a852-155">Shapes and Basic Drawing in WPF Overview</span></span>](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="7a852-156">Malování pomocí obrázků, kreseb a vizuálních objektů</span><span class="sxs-lookup"><span data-stu-id="7a852-156">Painting with Images, Drawings, and Visuals</span></span>](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="7a852-157">Přehled nakreslených objektů</span><span class="sxs-lookup"><span data-stu-id="7a852-157">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="7a852-158">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="7a852-158">How-to Topics</span></span>](adorners-how-to-topics.md)
