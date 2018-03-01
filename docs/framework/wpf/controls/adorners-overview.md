---
title: "Přehled doplňků"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 47b43b1b9848f91e77448d41609d8be5d60ecda5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="adorners-overview"></a><span data-ttu-id="6f2c1-102">Přehled doplňků</span><span class="sxs-lookup"><span data-stu-id="6f2c1-102">Adorners Overview</span></span>
<span data-ttu-id="6f2c1-103">Ozdobného prvku se o zvláštní typ <xref:System.Windows.FrameworkElement>používané k poskytování vizuální upozornění uživatele.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-103">Adorners are a special type of <xref:System.Windows.FrameworkElement>, used to provide visual cues to a user.</span></span> <span data-ttu-id="6f2c1-104">Mezi další používá ozdobného prvku slouží k přidejte funkční obslužné rutiny na elementy nebo zadejte informace o prvku stavu.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-104">Among other uses, Adorners can be used to add functional handles to elements or provide state information about a control.</span></span>  
  
  
  
<a name="about_Adorners"></a>   
## <a name="about-adorners"></a><span data-ttu-id="6f2c1-105">O ozdobného prvku</span><span class="sxs-lookup"><span data-stu-id="6f2c1-105">About Adorners</span></span>  
 <span data-ttu-id="6f2c1-106"><xref:System.Windows.Documents.Adorner> Je vlastní <xref:System.Windows.FrameworkElement> která je vázaná <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-106">An <xref:System.Windows.Documents.Adorner> is a custom <xref:System.Windows.FrameworkElement> that is bound to a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="6f2c1-107">Ozdobného prvku se zobrazují v <xref:System.Windows.Documents.AdornerLayer>, což je vykreslování prostor, který je pořád nad ozdobné element nebo kolekci elementů ozdobné.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-107">Adorners are rendered in an <xref:System.Windows.Documents.AdornerLayer>, which is a rendering surface that is always on top of the adorned element or a collection of adorned elements.</span></span> <span data-ttu-id="6f2c1-108">Vykreslování adorner je nezávislé na vykreslování <xref:System.Windows.UIElement> s vazbou adorner na.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-108">Rendering of an adorner is independent from rendering of the <xref:System.Windows.UIElement> that the adorner is bound to.</span></span> <span data-ttu-id="6f2c1-109">Adorner je obvykle umístěné vzhledem k elementu, ke kterému je vázán, pomocí standardní počátek souřadnic 2-D umístěný v levé horní ozdobné elementu.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-109">An adorner is typically positioned relative to the element to which it is bound, using the standard 2-D coordinate origin located at the upper-left of the adorned element.</span></span>  
  
 <span data-ttu-id="6f2c1-110">Běžné aplikace pro ozdobného prvku patří:</span><span class="sxs-lookup"><span data-stu-id="6f2c1-110">Common applications for adorners include:</span></span>  
  
-   <span data-ttu-id="6f2c1-111">Přidání funkční obslužné rutiny na <xref:System.Windows.UIElement> které umožňují uživatelům pracovat s element nějakým způsobem (Změna velikosti, otáčení, změna umístění atd.).</span><span class="sxs-lookup"><span data-stu-id="6f2c1-111">Adding functional handles to a <xref:System.Windows.UIElement> that enable a user to manipulate the element in some way (resize, rotate, reposition, etc.).</span></span>  
  
-   <span data-ttu-id="6f2c1-112">Vizuální zpětnou vazbu k označení různé stavy, nebo v reakci na různé události.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-112">Provide visual feedback to indicate various states, or in response to various events.</span></span>  
  
-   <span data-ttu-id="6f2c1-113">Překrytí visual dekorace na <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-113">Overlay visual decorations on a <xref:System.Windows.UIElement>.</span></span>  
  
-   <span data-ttu-id="6f2c1-114">Vizuální maskování nebo přepsání část nebo všechny <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-114">Visually mask or override part or all of a <xref:System.Windows.UIElement>.</span></span>  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="6f2c1-115">poskytuje základní architekturu pro adorning vizuální prvky.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-115"> provides a basic framework for adorning visual elements.</span></span> <span data-ttu-id="6f2c1-116">Následující tabulka uvádí primární typy používané při adorning objekty a jejich účel.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-116">The following table lists the primary types used when adorning objects, and their purpose.</span></span> <span data-ttu-id="6f2c1-117">Postupujte podle několik příkladů použití.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-117">Several usage examples follow.</span></span>  
  
|||  
|-|-|  
|<xref:System.Windows.Documents.Adorner>|<span data-ttu-id="6f2c1-118">Abstraktní základní třída, ze které dědí všechny adorner konkrétní implementace.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-118">An abstract base class from which all concrete adorner implementations inherit.</span></span>|  
|<xref:System.Windows.Documents.AdornerLayer>|<span data-ttu-id="6f2c1-119">Třída představující vrstvu vykreslování pro adorner(s) jeden nebo více ozdobné elementů.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-119">A class representing a rendering layer for the adorner(s) of one or more adorned elements.</span></span>|  
|<xref:System.Windows.Documents.AdornerDecorator>|<span data-ttu-id="6f2c1-120">Třída, která umožňuje vrstvu adorner přidruženou kolekci elementů.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-120">A class that enables an adorner layer to be associated with a collection of elements.</span></span>|  
  
<a name="implement_custom_Adorner"></a>   
## <a name="implementing-a-custom-adorner"></a><span data-ttu-id="6f2c1-121">Implementace vlastních Adorner</span><span class="sxs-lookup"><span data-stu-id="6f2c1-121">Implementing a Custom Adorner</span></span>  
 <span data-ttu-id="6f2c1-122">Rozhraní framework ozdobného prvku poskytované [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] je určená hlavně pro podporu vytváření vlastní ozdobného prvku.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-122">The adorners framework provided by [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is intended primarily to support the creation of custom adorners.</span></span> <span data-ttu-id="6f2c1-123">Vlastní adorner je vytvořen pomocí implementace třídy, která dědí z abstraktní <xref:System.Windows.Documents.Adorner> třídy.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-123">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f2c1-124">Nadřazeného <xref:System.Windows.Documents.Adorner> je <xref:System.Windows.Documents.AdornerLayer> , vykreslí <xref:System.Windows.Documents.Adorner>, není právě ozdobené elementu.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-124">The parent of an <xref:System.Windows.Documents.Adorner> is the <xref:System.Windows.Documents.AdornerLayer> that renders the <xref:System.Windows.Documents.Adorner>, not the element being adorned.</span></span>  
  
 <span data-ttu-id="6f2c1-125">Následující příklad ukazuje třídu, která implementuje jednoduché adorner.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-125">The following example shows a class that implements a simple adorner.</span></span> <span data-ttu-id="6f2c1-126">Příklad adorner jednoduše adorns rozích <xref:System.Windows.UIElement> s kroužky.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-126">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
 <span data-ttu-id="6f2c1-127">Následující obrázek ukazuje SimpleCircleAdorner u <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-127">The following image shows the SimpleCircleAdorner applied to a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 <span data-ttu-id="6f2c1-128">![Příklad ozdobného prvku: Ozdobné textové pole](../../../../docs/framework/wpf/controls/media/adornedtextbox.png "AdornedTextBox")</span><span class="sxs-lookup"><span data-stu-id="6f2c1-128">![Adorners Example: An adorned TextBox](../../../../docs/framework/wpf/controls/media/adornedtextbox.png "AdornedTextBox")</span></span>  
  
<a name="rendering_behavior_for_Adorners"></a>   
## <a name="rendering-behavior-for-adorners"></a><span data-ttu-id="6f2c1-129">Vykreslování chování ozdobného prvku</span><span class="sxs-lookup"><span data-stu-id="6f2c1-129">Rendering Behavior for Adorners</span></span>  
 <span data-ttu-id="6f2c1-130">Je důležité si uvědomit, že ozdobného prvku neobsahují žádné vyplývajících vykreslování chování; zajištění, že adorner vykreslí má na starosti implementátor adorner.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-130">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span>   <span data-ttu-id="6f2c1-131">Běžný způsob implementace vykreslování chování je přepsat <xref:System.Windows.UIElement.OnRender%2A> metoda a používat jednu nebo více <xref:System.Windows.Media.DrawingContext> pro vykreslení adorner vizuály podle potřeby (jak je uvedeno v předchozím příkladu).</span><span class="sxs-lookup"><span data-stu-id="6f2c1-131">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in the example above).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f2c1-132">Nic umístěny ve vrstvě adorner vykreslením nad zbytek všech stylů, které jste nastavili.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-132">Anything placed in the adorner layer is rendered on top of the rest of any styles you have set.</span></span> <span data-ttu-id="6f2c1-133">Jinými slovy ozdobného prvku jsou vždy vizuálně nahoře a nelze ji přepsat pomocí pořadí z-order.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-133">In other words, adorners are always visually on top and cannot be overridden using z-order.</span></span>  
  
<a name="adorner_events_hittest"></a>   
## <a name="events-and-hit-testing"></a><span data-ttu-id="6f2c1-134">Události a přístupů testování</span><span class="sxs-lookup"><span data-stu-id="6f2c1-134">Events and Hit Testing</span></span>  
 <span data-ttu-id="6f2c1-135">Ozdobného prvku přijímat vstupní události stejně jako libovolný jiný <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-135">Adorners receive input events just like any other <xref:System.Windows.FrameworkElement>.</span></span>  <span data-ttu-id="6f2c1-136">Protože adorner vždy má vyšší pořadí vykreslování než element ho adorns, adorner obdrží vstupních událostech (například <xref:System.Windows.UIElement.Drop> nebo <xref:System.Windows.UIElement.MouseMove>), může být žádoucí pro základní ozdobené elementu.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-136">Because an adorner always has a higher z-order than the element it adorns, the adorner receives input events (such as <xref:System.Windows.UIElement.Drop> or <xref:System.Windows.UIElement.MouseMove>) that may be intended for the underlying adorned element.</span></span>  <span data-ttu-id="6f2c1-137">Adorner může sledovat určité vstupní události a odesílat základní ozdobné element podle znovu vyvolá událost.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-137">An adorner can listen for certain input events and pass these on to the underlying adorned element by re-raising the event.</span></span>  
  
 <span data-ttu-id="6f2c1-138">Pokud chcete povolit průchozí přístupů testování elementů v rámci adorner, nastavte přístupů test <xref:System.Windows.UIElement.IsHitTestVisible%2A> vlastnost **false** na adorner.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-138">To enable pass-through hit testing of elements under an adorner, set the hit test <xref:System.Windows.UIElement.IsHitTestVisible%2A> property to **false** on the adorner.</span></span>  <span data-ttu-id="6f2c1-139">Další informace o počtu testování najdete v tématu</span><span class="sxs-lookup"><span data-stu-id="6f2c1-139">For more information about hit testing, see</span></span>  
  
 <span data-ttu-id="6f2c1-140">[Testování v Visual vrstvě průchodu](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md).</span><span class="sxs-lookup"><span data-stu-id="6f2c1-140">[Hit Testing in the Visual Layer](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md).</span></span>  
  
<a name="adorn_single_element"></a>   
## <a name="adorning-a-single-uielement"></a><span data-ttu-id="6f2c1-141">Adorning jeden prvků uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="6f2c1-141">Adorning a Single UIElement</span></span>  
 <span data-ttu-id="6f2c1-142">K vytvoření vazby adorner konkrétní <xref:System.Windows.UIElement>, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="6f2c1-142">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>  
  
1.  <span data-ttu-id="6f2c1-143">Zavolejte statickou metodu <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> získat <xref:System.Windows.Documents.AdornerLayer> objekt pro <xref:System.Windows.UIElement> k být ozdobené.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-143">Call the static method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="6f2c1-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>provede až vizuálním stromu, začínající v zadaném <xref:System.Windows.UIElement>a vrátí první vrstvu adorner najde.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified <xref:System.Windows.UIElement>, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="6f2c1-145">(Pokud se nenajdou žádné adorner vrstvy, metoda vrátí hodnotu null.)</span><span class="sxs-lookup"><span data-stu-id="6f2c1-145">(If no adorner layers are found, the method returns null.)</span></span>  
  
2.  <span data-ttu-id="6f2c1-146">Volání <xref:System.Windows.Documents.AdornerLayer.Add%2A> metoda pro vazbu adorner k cíli <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-146">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target <xref:System.Windows.UIElement>.</span></span>  
  
 <span data-ttu-id="6f2c1-147">Následující příklad vytvoří vazbu SimpleCircleAdorner (viz výše) k <xref:System.Windows.Controls.TextBox> s názvem *hodnotu myTextBox*.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-147">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  <span data-ttu-id="6f2c1-148">Pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] vytvořit vazbu adorner jiný element se aktuálně nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-148">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
<a name="adorn_children_panel"></a>   
## <a name="adorning-the-children-of-a-panel"></a><span data-ttu-id="6f2c1-149">Adorning podřízených prvků panely</span><span class="sxs-lookup"><span data-stu-id="6f2c1-149">Adorning the Children of a Panel</span></span>  
 <span data-ttu-id="6f2c1-150">Při vytváření vazby adorner podřízených objektů daného <xref:System.Windows.Controls.Panel>, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="6f2c1-150">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>  
  
1.  <span data-ttu-id="6f2c1-151">Volání `static` metoda <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> najít vrstvu adorner pro element, jehož podřízené objekty mají být ozdobené.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-151">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to find an adorner layer for the element whose children are to be adorned.</span></span>  
  
2.  <span data-ttu-id="6f2c1-152">Zobrazení výčtu prostřednictvím podřízené objekty daného nadřazeného elementu a volání <xref:System.Windows.Documents.AdornerLayer.Add%2A> metoda pro vazbu adorner každý podřízený element.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-152">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>  
  
 <span data-ttu-id="6f2c1-153">Následující příklad vytvoří vazbu SimpleCircleAdorner (viz výše) u podřízených objektů daného <xref:System.Windows.Controls.StackPanel> s názvem *myStackPanel*.</span><span class="sxs-lookup"><span data-stu-id="6f2c1-153">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
## <a name="see-also"></a><span data-ttu-id="6f2c1-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f2c1-154">See Also</span></span>  
 <xref:System.Windows.Media.AdornerHitTestResult>  
 [<span data-ttu-id="6f2c1-155">Přehled objektů Shape a základního kreslení ve WPF</span><span class="sxs-lookup"><span data-stu-id="6f2c1-155">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [<span data-ttu-id="6f2c1-156">Malování pomocí obrázků, kreseb a vizuálních objektů</span><span class="sxs-lookup"><span data-stu-id="6f2c1-156">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [<span data-ttu-id="6f2c1-157">Přehled nakreslených objektů</span><span class="sxs-lookup"><span data-stu-id="6f2c1-157">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="6f2c1-158">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="6f2c1-158">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/adorners-how-to-topics.md)
