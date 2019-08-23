---
title: Přehled doplňků
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: d8e6e53edc92a2847c001377706d313cf97cced5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956099"
---
# <a name="adorners-overview"></a><span data-ttu-id="320f0-102">Přehled doplňků</span><span class="sxs-lookup"><span data-stu-id="320f0-102">Adorners Overview</span></span>
<span data-ttu-id="320f0-103">Doplňky jsou speciálním typem <xref:System.Windows.FrameworkElement>, který slouží k poskytování vizuálních pomůcek uživateli.</span><span class="sxs-lookup"><span data-stu-id="320f0-103">Adorners are a special type of <xref:System.Windows.FrameworkElement>, used to provide visual cues to a user.</span></span> <span data-ttu-id="320f0-104">Mimo jiné použití Doplňky lze použít k přidání funkčních obslužných rutin do prvků nebo k poskytnutí informací o stavu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="320f0-104">Among other uses, Adorners can be used to add functional handles to elements or provide state information about a control.</span></span>  

<a name="about_Adorners"></a>   
## <a name="about-adorners"></a><span data-ttu-id="320f0-105">O doplňkových Doplňkůch</span><span class="sxs-lookup"><span data-stu-id="320f0-105">About Adorners</span></span>  
 <span data-ttu-id="320f0-106"><xref:System.Windows.Documents.Adorner> Je vlastní <xref:System.Windows.FrameworkElement>,který je svázán s. <xref:System.Windows.UIElement></span><span class="sxs-lookup"><span data-stu-id="320f0-106">An <xref:System.Windows.Documents.Adorner> is a custom <xref:System.Windows.FrameworkElement> that is bound to a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="320f0-107">Doplňky jsou vykresleny v <xref:System.Windows.Documents.AdornerLayer>, což je plocha vykreslování, která je vždy nad přívrchním prvkem nebo kolekcí doplňkových prvků.</span><span class="sxs-lookup"><span data-stu-id="320f0-107">Adorners are rendered in an <xref:System.Windows.Documents.AdornerLayer>, which is a rendering surface that is always on top of the adorned element or a collection of adorned elements.</span></span> <span data-ttu-id="320f0-108">Vykreslování doplňku je nezávislé na vykreslování <xref:System.Windows.UIElement> , ke kterému je doplněk vázán.</span><span class="sxs-lookup"><span data-stu-id="320f0-108">Rendering of an adorner is independent from rendering of the <xref:System.Windows.UIElement> that the adorner is bound to.</span></span> <span data-ttu-id="320f0-109">Doplněk je obvykle umístěn vzhledem k elementu, ke kterému je svázán, pomocí standardního zdroje souřadnic 2D v levém horním rohu nataženého prvku.</span><span class="sxs-lookup"><span data-stu-id="320f0-109">An adorner is typically positioned relative to the element to which it is bound, using the standard 2-D coordinate origin located at the upper-left of the adorned element.</span></span>  
  
 <span data-ttu-id="320f0-110">Mezi běžné aplikace pro doplňky patří:</span><span class="sxs-lookup"><span data-stu-id="320f0-110">Common applications for adorners include:</span></span>  
  
- <span data-ttu-id="320f0-111">Přidání funkčních popisovačů <xref:System.Windows.UIElement> , které uživateli umožňují manipulovat s prvkem nějakým způsobem (Změna velikosti, otočení, přemístění atd.).</span><span class="sxs-lookup"><span data-stu-id="320f0-111">Adding functional handles to a <xref:System.Windows.UIElement> that enable a user to manipulate the element in some way (resize, rotate, reposition, etc.).</span></span>  
  
- <span data-ttu-id="320f0-112">Poskytněte vizuální zpětnou vazbu pro indikaci různých stavů nebo v reakci na různé události.</span><span class="sxs-lookup"><span data-stu-id="320f0-112">Provide visual feedback to indicate various states, or in response to various events.</span></span>  
  
- <span data-ttu-id="320f0-113">Překrytí vizuálních <xref:System.Windows.UIElement>dekorace na.</span><span class="sxs-lookup"><span data-stu-id="320f0-113">Overlay visual decorations on a <xref:System.Windows.UIElement>.</span></span>  
  
- <span data-ttu-id="320f0-114">Vizuálně maskovat nebo potlačit část nebo vše <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="320f0-114">Visually mask or override part or all of a <xref:System.Windows.UIElement>.</span></span>  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="320f0-115">poskytuje základní rámec pro doplňky vizuálních prvků.</span><span class="sxs-lookup"><span data-stu-id="320f0-115">provides a basic framework for adorning visual elements.</span></span> <span data-ttu-id="320f0-116">V následující tabulce jsou uvedeny primární typy používané při příchodu objektů a jejich účel.</span><span class="sxs-lookup"><span data-stu-id="320f0-116">The following table lists the primary types used when adorning objects, and their purpose.</span></span> <span data-ttu-id="320f0-117">Následuje několik příkladů použití.</span><span class="sxs-lookup"><span data-stu-id="320f0-117">Several usage examples follow.</span></span>  
  
|||  
|-|-|  
|<xref:System.Windows.Documents.Adorner>|<span data-ttu-id="320f0-118">Abstraktní základní třída, ze které všechny konkrétní implementace doplňků dědí.</span><span class="sxs-lookup"><span data-stu-id="320f0-118">An abstract base class from which all concrete adorner implementations inherit.</span></span>|  
|<xref:System.Windows.Documents.AdornerLayer>|<span data-ttu-id="320f0-119">Třída, která představuje vrstvu vykreslování pro doplňky jednoho nebo více prvků s přístupnými doplňky.</span><span class="sxs-lookup"><span data-stu-id="320f0-119">A class representing a rendering layer for the adorner(s) of one or more adorned elements.</span></span>|  
|<xref:System.Windows.Documents.AdornerDecorator>|<span data-ttu-id="320f0-120">Třída, která umožňuje přidružit vrstvu doplňků ke kolekci elementů.</span><span class="sxs-lookup"><span data-stu-id="320f0-120">A class that enables an adorner layer to be associated with a collection of elements.</span></span>|  
  
<a name="implement_custom_Adorner"></a>   
## <a name="implementing-a-custom-adorner"></a><span data-ttu-id="320f0-121">Implementace vlastního doplňku</span><span class="sxs-lookup"><span data-stu-id="320f0-121">Implementing a Custom Adorner</span></span>  
 <span data-ttu-id="320f0-122">Doplňky, které poskytuje [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] , jsou určené hlavně pro podporu vytváření vlastních doplňků.</span><span class="sxs-lookup"><span data-stu-id="320f0-122">The adorners framework provided by [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is intended primarily to support the creation of custom adorners.</span></span> <span data-ttu-id="320f0-123">Vlastní doplňky je vytvořeno implementací třídy, která dědí z abstraktní <xref:System.Windows.Documents.Adorner> třídy.</span><span class="sxs-lookup"><span data-stu-id="320f0-123">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="320f0-124">Nadřazený <xref:System.Windows.Documents.Adorner> objekt <xref:System.Windows.Documents.Adorner>je, který vykresluje, nikoli element, který je v něm navýšený. <xref:System.Windows.Documents.AdornerLayer></span><span class="sxs-lookup"><span data-stu-id="320f0-124">The parent of an <xref:System.Windows.Documents.Adorner> is the <xref:System.Windows.Documents.AdornerLayer> that renders the <xref:System.Windows.Documents.Adorner>, not the element being adorned.</span></span>  
  
 <span data-ttu-id="320f0-125">Následující příklad ukazuje třídu, která implementuje jednoduché doplňky.</span><span class="sxs-lookup"><span data-stu-id="320f0-125">The following example shows a class that implements a simple adorner.</span></span> <span data-ttu-id="320f0-126">Příkladem může být <xref:System.Windows.UIElement> pouze sevýšení rohů s kroužky.</span><span class="sxs-lookup"><span data-stu-id="320f0-126">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
 <span data-ttu-id="320f0-127">Na následujícím obrázku vidíte SimpleCircleAdorner použité pro <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="320f0-127">The following image shows the SimpleCircleAdorner applied to a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 ![Snímek obrazovky se zobrazeným textovým polem](./media/adorners-overview/simplecircleadorner-textbox.png)  
  
<a name="rendering_behavior_for_Adorners"></a>   
## <a name="rendering-behavior-for-adorners"></a><span data-ttu-id="320f0-129">Chování vykreslování pro Doplňky</span><span class="sxs-lookup"><span data-stu-id="320f0-129">Rendering Behavior for Adorners</span></span>  
 <span data-ttu-id="320f0-130">Je důležité si uvědomit, že doplňky neobsahují žádné podstatné chování při vykreslování; zajištění, že se nakreslí doplňková událost, je odpovědností dodatečně implementátor.</span><span class="sxs-lookup"><span data-stu-id="320f0-130">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span>   <span data-ttu-id="320f0-131">Běžným způsobem, jak implementovat chování vykreslování, je přepsat <xref:System.Windows.UIElement.OnRender%2A> metodu a použít jeden nebo více <xref:System.Windows.Media.DrawingContext> objektů pro vykreslení vizuálů doplňku podle potřeby (jak je znázorněno v příkladu výše).</span><span class="sxs-lookup"><span data-stu-id="320f0-131">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in the example above).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="320f0-132">Cokoli, co umístíte do doplňku, se vykreslí nad zbývajícími styly, které jste nastavili.</span><span class="sxs-lookup"><span data-stu-id="320f0-132">Anything placed in the adorner layer is rendered on top of the rest of any styles you have set.</span></span> <span data-ttu-id="320f0-133">Jinými slovy, doplňky jsou vždy vizuálně nahoře a nelze je přepsat pomocí pořadí vykreslování.</span><span class="sxs-lookup"><span data-stu-id="320f0-133">In other words, adorners are always visually on top and cannot be overridden using z-order.</span></span>  
  
<a name="adorner_events_hittest"></a>   
## <a name="events-and-hit-testing"></a><span data-ttu-id="320f0-134">Události a testování přístupů</span><span class="sxs-lookup"><span data-stu-id="320f0-134">Events and Hit Testing</span></span>  
 <span data-ttu-id="320f0-135">Doplňky dostávají vstupní události stejně jako jiné <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="320f0-135">Adorners receive input events just like any other <xref:System.Windows.FrameworkElement>.</span></span>  <span data-ttu-id="320f0-136">Vzhledem k tomu, že má doplňková událost vždy vyšší pořadí z, než je prvek, který je prvkem, může doplněk přijímat vstupní události <xref:System.Windows.UIElement.Drop> ( <xref:System.Windows.UIElement.MouseMove>například nebo), které mohou být určeny pro základní prvek s právy.</span><span class="sxs-lookup"><span data-stu-id="320f0-136">Because an adorner always has a higher z-order than the element it adorns, the adorner receives input events (such as <xref:System.Windows.UIElement.Drop> or <xref:System.Windows.UIElement.MouseMove>) that may be intended for the underlying adorned element.</span></span>  <span data-ttu-id="320f0-137">Doplňková událost může naslouchat určitým vstupním událostem a předávat je základnímu prvku, který ho znovu vyvolal.</span><span class="sxs-lookup"><span data-stu-id="320f0-137">An adorner can listen for certain input events and pass these on to the underlying adorned element by re-raising the event.</span></span>  
  
 <span data-ttu-id="320f0-138">Chcete-li povolit testování průchozího průchodu prvků v doplňku, nastavte vlastnost test <xref:System.Windows.UIElement.IsHitTestVisible%2A> přístupů na **hodnotu false** u doplňku.</span><span class="sxs-lookup"><span data-stu-id="320f0-138">To enable pass-through hit testing of elements under an adorner, set the hit test <xref:System.Windows.UIElement.IsHitTestVisible%2A> property to **false** on the adorner.</span></span>  <span data-ttu-id="320f0-139">Další informace o testování přístupů najdete v tématu.</span><span class="sxs-lookup"><span data-stu-id="320f0-139">For more information about hit testing, see</span></span>  
  
 <span data-ttu-id="320f0-140">[Testování přístupů ve vizuální vrstvě](../graphics-multimedia/hit-testing-in-the-visual-layer.md).</span><span class="sxs-lookup"><span data-stu-id="320f0-140">[Hit Testing in the Visual Layer](../graphics-multimedia/hit-testing-in-the-visual-layer.md).</span></span>  
  
<a name="adorn_single_element"></a>   
## <a name="adorning-a-single-uielement"></a><span data-ttu-id="320f0-141">Navýšení jednoho prvku UIElement</span><span class="sxs-lookup"><span data-stu-id="320f0-141">Adorning a Single UIElement</span></span>  
 <span data-ttu-id="320f0-142">Chcete-li navazovat Doplňky na konkrétní <xref:System.Windows.UIElement>, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="320f0-142">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>  
  
1. <span data-ttu-id="320f0-143">Zavolejte statickou metodu <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> pro <xref:System.Windows.Documents.AdornerLayer> získání objektu, <xref:System.Windows.UIElement> který má být podrobnější.</span><span class="sxs-lookup"><span data-stu-id="320f0-143">Call the static method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="320f0-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>provede sestavování vizuálního stromu, počínaje zadaným <xref:System.Windows.UIElement>a vrátí první nalezenou vrstvu doplňku.</span><span class="sxs-lookup"><span data-stu-id="320f0-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified <xref:System.Windows.UIElement>, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="320f0-145">(Pokud se nenaleznou žádné vrstvy doplňků, vrátí metoda hodnotu null.)</span><span class="sxs-lookup"><span data-stu-id="320f0-145">(If no adorner layers are found, the method returns null.)</span></span>  
  
2. <span data-ttu-id="320f0-146">Voláním <xref:System.Windows.UIElement>metody navázání doplňku k cíli. <xref:System.Windows.Documents.AdornerLayer.Add%2A></span><span class="sxs-lookup"><span data-stu-id="320f0-146">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target <xref:System.Windows.UIElement>.</span></span>  
  
 <span data-ttu-id="320f0-147">Následující příklad váže SimpleCircleAdorner (zobrazený výše) k <xref:System.Windows.Controls.TextBox> pojmenovanému *MyTextBox*.</span><span class="sxs-lookup"><span data-stu-id="320f0-147">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
> <span data-ttu-id="320f0-148">Použití [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pro svázání doplňku s jiným prvkem není aktuálně podporováno.</span><span class="sxs-lookup"><span data-stu-id="320f0-148">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
<a name="adorn_children_panel"></a>   
## <a name="adorning-the-children-of-a-panel"></a><span data-ttu-id="320f0-149">Vylepšení podřízených objektů panelu</span><span class="sxs-lookup"><span data-stu-id="320f0-149">Adorning the Children of a Panel</span></span>  
 <span data-ttu-id="320f0-150">Chcete-li vytvořit navázání doplňku k <xref:System.Windows.Controls.Panel>podřízeným položkám, postupujte následovně:</span><span class="sxs-lookup"><span data-stu-id="320f0-150">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>  
  
1. <span data-ttu-id="320f0-151">`static` Zavolejte metodu <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> pro nalezení doplňkové vrstvy pro element, jehož podřízené prvky mají být navrstveny.</span><span class="sxs-lookup"><span data-stu-id="320f0-151">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to find an adorner layer for the element whose children are to be adorned.</span></span>  
  
2. <span data-ttu-id="320f0-152">Zobrazte výčet prostřednictvím podřízených objektů nadřazeného prvku a zavolejte <xref:System.Windows.Documents.AdornerLayer.Add%2A> metodu pro svázání doplňku s každým podřízeným elementem.</span><span class="sxs-lookup"><span data-stu-id="320f0-152">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>  
  
 <span data-ttu-id="320f0-153">Následující příklad váže SimpleCircleAdorner (zobrazený výše) na podřízené objekty <xref:System.Windows.Controls.StackPanel> pojmenovaného *myStackPanel*.</span><span class="sxs-lookup"><span data-stu-id="320f0-153">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
## <a name="see-also"></a><span data-ttu-id="320f0-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="320f0-154">See also</span></span>

- <xref:System.Windows.Media.AdornerHitTestResult>
- [<span data-ttu-id="320f0-155">Přehled objektů Shape a základního kreslení ve WPF</span><span class="sxs-lookup"><span data-stu-id="320f0-155">Shapes and Basic Drawing in WPF Overview</span></span>](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="320f0-156">Malování pomocí obrázků, kreseb a vizuálních objektů</span><span class="sxs-lookup"><span data-stu-id="320f0-156">Painting with Images, Drawings, and Visuals</span></span>](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="320f0-157">Přehled nakreslených objektů</span><span class="sxs-lookup"><span data-stu-id="320f0-157">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="320f0-158">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="320f0-158">How-to Topics</span></span>](adorners-how-to-topics.md)
