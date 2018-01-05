---
title: "Postupy: Nastavení vlastnosti po animaci pomocí scénáře"
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
helpviewer_keywords: animation [WPF], changing property values after
ms.assetid: 79466556-4dbf-40bd-9c1e-a77613b07077
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3ffc534549f5b114a07f09326be72c1968d178a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-a-property-after-animating-it-with-a-storyboard"></a><span data-ttu-id="37ff3-102">Postupy: Nastavení vlastnosti po animaci pomocí scénáře</span><span class="sxs-lookup"><span data-stu-id="37ff3-102">How to: Set a Property After Animating It with a Storyboard</span></span>
<span data-ttu-id="37ff3-103">V některých případech může vypadat, že po byla animovaný nelze změnit hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="37ff3-103">In some cases, it might appear that you can't change the value of a property after it has been animated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37ff3-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="37ff3-104">Example</span></span>  
 <span data-ttu-id="37ff3-105">V následujícím příkladu <xref:System.Windows.Media.Animation.Storyboard> se používá k animace barva <xref:System.Windows.Media.SolidColorBrush>.</span><span class="sxs-lookup"><span data-stu-id="37ff3-105">In the following example, a <xref:System.Windows.Media.Animation.Storyboard> is used to animate the color of a <xref:System.Windows.Media.SolidColorBrush>.</span></span> <span data-ttu-id="37ff3-106">Při kliknutí na tlačítko, aktivuje se scénáři.</span><span class="sxs-lookup"><span data-stu-id="37ff3-106">The storyboard is triggered when the button is clicked.</span></span> <span data-ttu-id="37ff3-107"><xref:System.Windows.Media.Animation.Timeline.Completed> Událost je zpracovávána tak, aby program obdrží oznámení při <xref:System.Windows.Media.Animation.ColorAnimation> dokončení.</span><span class="sxs-lookup"><span data-stu-id="37ff3-107">The <xref:System.Windows.Media.Animation.Timeline.Completed> event is handled so that the program is notified when the <xref:System.Windows.Media.Animation.ColorAnimation> completes.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton1Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton1declaration)]  
  
## <a name="example"></a><span data-ttu-id="37ff3-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="37ff3-108">Example</span></span>  
 <span data-ttu-id="37ff3-109">Po <xref:System.Windows.Media.Animation.ColorAnimation> dokončí, program se pokusí změnit barvu stopy na modrou.</span><span class="sxs-lookup"><span data-stu-id="37ff3-109">After the <xref:System.Windows.Media.Animation.ColorAnimation> completes, the program attempts to change the brush's color to blue.</span></span>  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton1Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton1handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton1Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton1handler)]  
  
 <span data-ttu-id="37ff3-110">Předchozí kód nezobrazí žádnou: poskytl žlutý, štětce zůstanou, které je hodnota <xref:System.Windows.Media.Animation.ColorAnimation> který animovaný stopy.</span><span class="sxs-lookup"><span data-stu-id="37ff3-110">The previous code doesn't appear to do anything: the brush remains yellow, which is the value supplied by the <xref:System.Windows.Media.Animation.ColorAnimation> that animated the brush.</span></span> <span data-ttu-id="37ff3-111">Základní hodnota vlastnosti (základní hodnota) je ve skutečnosti změnit na modrou.</span><span class="sxs-lookup"><span data-stu-id="37ff3-111">The underlying property value (the base value) is actually changed to blue.</span></span> <span data-ttu-id="37ff3-112">Ale zůstává žlutý hodnota efektivní nebo aktuální, protože <xref:System.Windows.Media.Animation.ColorAnimation> stále přepisují základní hodnota.</span><span class="sxs-lookup"><span data-stu-id="37ff3-112">However, the effective, or current, value remains yellow because the <xref:System.Windows.Media.Animation.ColorAnimation> is still overriding the base value.</span></span> <span data-ttu-id="37ff3-113">Pokud chcete hodnotu opět efektivní hodnota, je nutné zastavit animace z ovlivňující vlastnost.</span><span class="sxs-lookup"><span data-stu-id="37ff3-113">If you want the base value to become the effective value again, you must stop the animation from influencing the property.</span></span> <span data-ttu-id="37ff3-114">Existují tři způsoby, jak to provést pomocí animací scénáře:</span><span class="sxs-lookup"><span data-stu-id="37ff3-114">There are three ways to do this with storyboard animations:</span></span>  
  
-   <span data-ttu-id="37ff3-115">Nastavení animace <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> vlastnosti<xref:System.Windows.Media.Animation.FillBehavior.Stop></span><span class="sxs-lookup"><span data-stu-id="37ff3-115">Set the animation's <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property to <xref:System.Windows.Media.Animation.FillBehavior.Stop></span></span>  
  
-   <span data-ttu-id="37ff3-116">Odeberte celý scénáře.</span><span class="sxs-lookup"><span data-stu-id="37ff3-116">Remove the entire Storyboard.</span></span>  
  
-   <span data-ttu-id="37ff3-117">Odeberte animace z dané vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="37ff3-117">Remove the animation from the individual property.</span></span>  
  
## <a name="set-the-animations-fillbehavior-property-to-stop"></a><span data-ttu-id="37ff3-118">Nastavte vlastnost FillBehavior má animace na zastavení</span><span class="sxs-lookup"><span data-stu-id="37ff3-118">Set the animation's FillBehavior property to Stop</span></span>  
 <span data-ttu-id="37ff3-119">Nastavením <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> k <xref:System.Windows.Media.Animation.FillBehavior.Stop>, řekněte animace zastavit, které mají vliv na jeho vlastnost target po ukončení jeho aktivní období.</span><span class="sxs-lookup"><span data-stu-id="37ff3-119">By setting <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> to <xref:System.Windows.Media.Animation.FillBehavior.Stop>, you tell the animation to stop affecting its target property after it reaches the end of its active period.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton2Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton2declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton2Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton2handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton2Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton2handler)]  
  
## <a name="remove-the-entire-storyboard"></a><span data-ttu-id="37ff3-120">Odeberte celý scénáře</span><span class="sxs-lookup"><span data-stu-id="37ff3-120">Remove the entire storyboard</span></span>  
 <span data-ttu-id="37ff3-121">Pomocí <xref:System.Windows.Media.Animation.RemoveStoryboard> aktivační události nebo <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType> metoda, řekněte animací storyboard zastavit, které mají vliv na jejich vlastnosti cíle.</span><span class="sxs-lookup"><span data-stu-id="37ff3-121">By using a <xref:System.Windows.Media.Animation.RemoveStoryboard> trigger or the <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType> method, you tell the storyboard animations to stop affecting their target properties.</span></span> <span data-ttu-id="37ff3-122">Rozdíl mezi tento přístup a nastavení <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> vlastnost je, že můžete odebrat scénáři v kdykoli, při <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> vlastnost má vliv pouze v případě animace dosáhne konce své aktivní období.</span><span class="sxs-lookup"><span data-stu-id="37ff3-122">The difference between this approach and setting the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property is that you can remove the storyboard at anytime, while the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property only has an effect when the animation reaches the end of its active period.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton3Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton3declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton3Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton3handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton3Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton3handler)]  
  
## <a name="remove-an-animation-from-an-individual-property"></a><span data-ttu-id="37ff3-123">Odebrání animace jednotlivé vlastnosti</span><span class="sxs-lookup"><span data-stu-id="37ff3-123">Remove an animation from an individual property</span></span>  
 <span data-ttu-id="37ff3-124">Jiné technik zastavit animace neovlivňovaly vlastnost je použít <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> metodu objektu se animace.</span><span class="sxs-lookup"><span data-stu-id="37ff3-124">Another technique to stop an animation from affecting a property is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> method of the object being animated.</span></span> <span data-ttu-id="37ff3-125">Určete vlastnost probíhá animovaný jako první parametr a `null` jako druhý.</span><span class="sxs-lookup"><span data-stu-id="37ff3-125">Specify the property being animated as the first parameter and `null` as the second.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton4Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton4declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton4Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton4handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton4Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton4handler)]  
  
 <span data-ttu-id="37ff3-126">Tento postup funguje i pro jiné scénáře animace.</span><span class="sxs-lookup"><span data-stu-id="37ff3-126">This technique also works for non-storyboard animations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37ff3-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="37ff3-127">See Also</span></span>  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>  
 <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Media.Animation.RemoveStoryboard>  
 [<span data-ttu-id="37ff3-128">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="37ff3-128">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="37ff3-129">Přehled způsobů animace vlastností</span><span class="sxs-lookup"><span data-stu-id="37ff3-129">Property Animation Techniques Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
