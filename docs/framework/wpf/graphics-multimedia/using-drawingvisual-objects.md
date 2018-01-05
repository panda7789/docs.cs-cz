---
title: "Použití objektů DrawingVisual"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- visual layer [WPF], DrawingVisual objects
- DrawingVisual objects in visual layer [WPF]
ms.assetid: 0b4e711d-e640-40cb-81c3-8f5c59909b7d
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a33e56b69a357694a1d1a23d5cd3c887c88cea37
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-drawingvisual-objects"></a><span data-ttu-id="c7890-102">Použití objektů DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="c7890-102">Using DrawingVisual Objects</span></span>
<span data-ttu-id="c7890-103">Toto téma obsahuje přehled o tom, jak používat <xref:System.Windows.Media.DrawingVisual> objekty v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] visual vrstvy.</span><span class="sxs-lookup"><span data-stu-id="c7890-103">This topic provides an overview of how to use <xref:System.Windows.Media.DrawingVisual> objects in the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] visual layer.</span></span>  
  
<a name="drawingvisual_object"></a>   
## <a name="drawingvisual-object"></a><span data-ttu-id="c7890-104">Objekt DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="c7890-104">DrawingVisual Object</span></span>  
 <span data-ttu-id="c7890-105"><xref:System.Windows.Media.DrawingVisual> Představuje nenáročné, kreslení třídu, která se použije k vykreslení tvarů, Image nebo text.</span><span class="sxs-lookup"><span data-stu-id="c7890-105">The <xref:System.Windows.Media.DrawingVisual> is a lightweight drawing class that is used to render shapes, images, or text.</span></span> <span data-ttu-id="c7890-106">Tato třída se považuje za lightweight, protože neposkytuje rozložení nebo událostí zpracování, což zvyšuje jeho výkon.</span><span class="sxs-lookup"><span data-stu-id="c7890-106">This class is considered lightweight because it does not provide layout or event handling, which improves its performance.</span></span> <span data-ttu-id="c7890-107">Z toho důvodu jsou ideální pro pozadí a vytvoříte čára.</span><span class="sxs-lookup"><span data-stu-id="c7890-107">For this reason, drawings are ideal for backgrounds and clip art.</span></span>  
  
<a name="drawingvisual_host_container"></a>   
## <a name="drawingvisual-host-container"></a><span data-ttu-id="c7890-108">Kontejner DrawingVisual hostitele</span><span class="sxs-lookup"><span data-stu-id="c7890-108">DrawingVisual Host Container</span></span>  
 <span data-ttu-id="c7890-109">Chcete-li použít <xref:System.Windows.Media.DrawingVisual> objekty, je nutné vytvořit kontejner hostitele pro objekty.</span><span class="sxs-lookup"><span data-stu-id="c7890-109">In order to use <xref:System.Windows.Media.DrawingVisual> objects, you need to create a host container for the objects.</span></span> <span data-ttu-id="c7890-110">Objekt kontejneru hostitele musí být odvozeny od <xref:System.Windows.FrameworkElement> třídy, která poskytuje, který podporuje rozložení a zpracování událostí <xref:System.Windows.Media.DrawingVisual> třídy chybí.</span><span class="sxs-lookup"><span data-stu-id="c7890-110">The host container object must derive from the <xref:System.Windows.FrameworkElement> class, which provides the layout and event handling support that the <xref:System.Windows.Media.DrawingVisual> class lacks.</span></span> <span data-ttu-id="c7890-111">Objekt kontejneru hostitele nezobrazuje žádné viditelné vlastnosti vzhledem k tomu, že jeho hlavním účelem je tak, aby obsahovala podřízené objekty.</span><span class="sxs-lookup"><span data-stu-id="c7890-111">The host container object does not display any visible properties, since its main purpose is to contain child objects.</span></span> <span data-ttu-id="c7890-112">Ale <xref:System.Windows.UIElement.Visibility%2A> kontejneru hostitele musí být nastavena na <xref:System.Windows.Visibility.Visible>, jinak hodnota žádný z jejích podřízených elementů se nebude zobrazovat.</span><span class="sxs-lookup"><span data-stu-id="c7890-112">However, the <xref:System.Windows.UIElement.Visibility%2A> property of the host container must be set to <xref:System.Windows.Visibility.Visible>; otherwise, none of its child elements will be visible.</span></span>  
  
 <span data-ttu-id="c7890-113">Když vytvoříte objekt kontejneru hostitele pro vizuální objekty, je třeba uložit vizuální objekt odkazy v <xref:System.Windows.Media.VisualCollection>.</span><span class="sxs-lookup"><span data-stu-id="c7890-113">When you create a host container object for visual objects, you need to store the visual object references in a <xref:System.Windows.Media.VisualCollection>.</span></span> <span data-ttu-id="c7890-114">Použití <xref:System.Windows.Media.VisualCollection.Add%2A> metody přidat objekt visual ke kontejneru hostitele.</span><span class="sxs-lookup"><span data-stu-id="c7890-114">Use the <xref:System.Windows.Media.VisualCollection.Add%2A> method to add a visual object to the host container.</span></span> <span data-ttu-id="c7890-115">V následujícím příkladu je vytvořen objekt kontejneru hostitele a tři vizuální objekty jsou přidány do jeho <xref:System.Windows.Media.VisualCollection>.</span><span class="sxs-lookup"><span data-stu-id="c7890-115">In the following example, a host container object is created, and three visual objects are added to its <xref:System.Windows.Media.VisualCollection>.</span></span>  
  
 [!code-csharp[DrawingVisualSample#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
>  <span data-ttu-id="c7890-116">Ukázka dokončení kódu, ze kterého jste extrahovali v předchozím příkladu kódu, najdete v části [ukázka průchodu testu DrawingVisuals](http://go.microsoft.com/fwlink/?LinkID=159994).</span><span class="sxs-lookup"><span data-stu-id="c7890-116">For the complete code sample from which the preceding code example was extracted, see [Hit Test Using DrawingVisuals Sample](http://go.microsoft.com/fwlink/?LinkID=159994).</span></span>  
  
<a name="creating_drawingvisual_objects"></a>   
## <a name="creating-drawingvisual-objects"></a><span data-ttu-id="c7890-117">Vytváření objektů DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="c7890-117">Creating DrawingVisual Objects</span></span>  
 <span data-ttu-id="c7890-118">Při vytváření <xref:System.Windows.Media.DrawingVisual> objektu má žádné kreslení obsah.</span><span class="sxs-lookup"><span data-stu-id="c7890-118">When you create a <xref:System.Windows.Media.DrawingVisual> object, it has no drawing content.</span></span> <span data-ttu-id="c7890-119">Text, grafiky nebo obsahu bitové kopie můžete přidat načtením objektu <xref:System.Windows.Media.DrawingContext> a kreslení do ní.</span><span class="sxs-lookup"><span data-stu-id="c7890-119">You can add text, graphics, or image content by retrieving the object's <xref:System.Windows.Media.DrawingContext> and drawing into it.</span></span> <span data-ttu-id="c7890-120">A <xref:System.Windows.Media.DrawingContext> vrátí volání <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> metodu <xref:System.Windows.Media.DrawingVisual> objektu.</span><span class="sxs-lookup"><span data-stu-id="c7890-120">A <xref:System.Windows.Media.DrawingContext> is returned by calling the <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> method of a <xref:System.Windows.Media.DrawingVisual> object.</span></span>  
  
 <span data-ttu-id="c7890-121">Vytvořte obdélník do <xref:System.Windows.Media.DrawingContext>, použijte <xref:System.Windows.Media.DrawingContext.DrawRectangle%2A> metodu <xref:System.Windows.Media.DrawingContext> objektu.</span><span class="sxs-lookup"><span data-stu-id="c7890-121">To draw a rectangle into the <xref:System.Windows.Media.DrawingContext>, use the <xref:System.Windows.Media.DrawingContext.DrawRectangle%2A> method of the <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="c7890-122">Existují podobné metody pro kreslení jiné typy obsahu.</span><span class="sxs-lookup"><span data-stu-id="c7890-122">Similar methods exist for drawing other types of content.</span></span> <span data-ttu-id="c7890-123">Po dokončení kreslení obsah do <xref:System.Windows.Media.DrawingContext>, volání <xref:System.Windows.Media.DrawingContext.Close%2A> metoda zavřete <xref:System.Windows.Media.DrawingContext> a zachovat obsah.</span><span class="sxs-lookup"><span data-stu-id="c7890-123">When you are finished drawing content into the <xref:System.Windows.Media.DrawingContext>, call the <xref:System.Windows.Media.DrawingContext.Close%2A> method to close the <xref:System.Windows.Media.DrawingContext> and persist the content.</span></span>  
  
 <span data-ttu-id="c7890-124">V následujícím příkladu <xref:System.Windows.Media.DrawingVisual> objekt se vytvoří a obdélníku vykreslením do jeho <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="c7890-124">In the following example, a <xref:System.Windows.Media.DrawingVisual> object is created, and a rectangle is drawn into its <xref:System.Windows.Media.DrawingContext>.</span></span>  
  
 [!code-csharp[DrawingVisualSample#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>   
## <a name="creating-overrides-for-frameworkelement-members"></a><span data-ttu-id="c7890-125">Vytváření přepsání pro FrameworkElement členy</span><span class="sxs-lookup"><span data-stu-id="c7890-125">Creating Overrides for FrameworkElement Members</span></span>  
 <span data-ttu-id="c7890-126">Objekt kontejneru hostitele je zodpovědný za správu jeho kolekce vizuální objekty.</span><span class="sxs-lookup"><span data-stu-id="c7890-126">The host container object is responsible for managing its collection of visual objects.</span></span> <span data-ttu-id="c7890-127">To vyžaduje, aby kontejneru hostitele implementovat člen přepsání odvozené <xref:System.Windows.FrameworkElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="c7890-127">This requires that the host container implement member overrides for the derived <xref:System.Windows.FrameworkElement> class.</span></span>  
  
 <span data-ttu-id="c7890-128">Následující seznam popisuje dva členy, které je nutné přepsat:</span><span class="sxs-lookup"><span data-stu-id="c7890-128">The following list describes the two members you must override:</span></span>  
  
-   <span data-ttu-id="c7890-129"><xref:System.Windows.FrameworkElement.GetVisualChild%2A>: Vrátí podřízené v zadaném indexu kolekce podřízených elementů.</span><span class="sxs-lookup"><span data-stu-id="c7890-129"><xref:System.Windows.FrameworkElement.GetVisualChild%2A>: Returns a child at the specified index from the collection of child elements.</span></span>  
  
-   <span data-ttu-id="c7890-130"><xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>: Získá číslo visual podřízených elementů v rámci tohoto elementu.</span><span class="sxs-lookup"><span data-stu-id="c7890-130"><xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>: Gets the number of visual child elements within this element.</span></span>  
  
 <span data-ttu-id="c7890-131">V následujícím příkladu jsou přepsání pro dva <xref:System.Windows.FrameworkElement> jsou implementované členy.</span><span class="sxs-lookup"><span data-stu-id="c7890-131">In the following example, overrides for the two <xref:System.Windows.FrameworkElement> members are implemented.</span></span>  
  
 [!code-csharp[DrawingVisualSample#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>   
## <a name="providing-hit-testing-support"></a><span data-ttu-id="c7890-132">Zajištění podpory přístupů testování</span><span class="sxs-lookup"><span data-stu-id="c7890-132">Providing Hit Testing Support</span></span>  
 <span data-ttu-id="c7890-133">Objekt kontejneru hostitele můžete zadat, událostí zpracování i v případě, že se nezobrazí žádné viditelné vlastnosti – však jeho <xref:System.Windows.UIElement.Visibility%2A> musí být nastavena na <xref:System.Windows.Visibility.Visible>.</span><span class="sxs-lookup"><span data-stu-id="c7890-133">The host container object can provide event handling even if it does not display any visible properties—however, its <xref:System.Windows.UIElement.Visibility%2A> property must be set to <xref:System.Windows.Visibility.Visible>.</span></span> <span data-ttu-id="c7890-134">Můžete vytvořit událost zpracování rutiny pro hostitele kontejner, který můžete depeše události myši, jako je například verzi levé tlačítko.</span><span class="sxs-lookup"><span data-stu-id="c7890-134">This allows you to create an event handling routine for the host container that can trap mouse events, such as the release of the left mouse button.</span></span> <span data-ttu-id="c7890-135">Rutiny zpracování událostí poté můžete implementovat, počtu testování vyvoláním <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="c7890-135">The event handling routine can then implement hit testing by invoking the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method.</span></span> <span data-ttu-id="c7890-136">Metody <xref:System.Windows.Media.HitTestResultCallback> parametr odkazuje na procedury definovaný uživatelem, která můžete použít k určení výsledné akce testu přístupů.</span><span class="sxs-lookup"><span data-stu-id="c7890-136">The method's <xref:System.Windows.Media.HitTestResultCallback> parameter refers to a user-defined procedure that you can use to determine the resulting action of a hit test.</span></span>  
  
 <span data-ttu-id="c7890-137">V následujícím příkladu se implementuje podle testování podporu pro objekt kontejneru hostitele a její podřízené položky.</span><span class="sxs-lookup"><span data-stu-id="c7890-137">In the following example, hit testing support is implemented for the host container object and its children.</span></span>  
  
 [!code-csharp[DrawingVisualSample#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="c7890-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7890-138">See Also</span></span>  
 <xref:System.Windows.Media.DrawingVisual>  
 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>  
 [<span data-ttu-id="c7890-139">Přehled vykreslování grafiky WPF</span><span class="sxs-lookup"><span data-stu-id="c7890-139">WPF Graphics Rendering Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [<span data-ttu-id="c7890-140">Ověřování pozice ve vizuální vrstvě</span><span class="sxs-lookup"><span data-stu-id="c7890-140">Hit Testing in the Visual Layer</span></span>](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)
