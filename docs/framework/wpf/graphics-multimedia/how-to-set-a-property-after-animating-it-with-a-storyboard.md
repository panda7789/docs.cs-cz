---
title: 'Postupy: Nastavení vlastnosti po animaci pomocí scénáře'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], changing property values after
ms.assetid: 79466556-4dbf-40bd-9c1e-a77613b07077
ms.openlocfilehash: 1f66c79f18fd02327c0c1f4f20787e566437f20f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359425"
---
# <a name="how-to-set-a-property-after-animating-it-with-a-storyboard"></a><span data-ttu-id="799ea-102">Postupy: Nastavení vlastnosti po animaci pomocí scénáře</span><span class="sxs-lookup"><span data-stu-id="799ea-102">How to: Set a Property After Animating It with a Storyboard</span></span>
<span data-ttu-id="799ea-103">V některých případech se může zobrazit, že po jeho animovat nelze změnit hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="799ea-103">In some cases, it might appear that you can't change the value of a property after it has been animated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="799ea-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="799ea-104">Example</span></span>  
 <span data-ttu-id="799ea-105">V následujícím příkladu <xref:System.Windows.Media.Animation.Storyboard> slouží k animace barvy <xref:System.Windows.Media.SolidColorBrush>.</span><span class="sxs-lookup"><span data-stu-id="799ea-105">In the following example, a <xref:System.Windows.Media.Animation.Storyboard> is used to animate the color of a <xref:System.Windows.Media.SolidColorBrush>.</span></span> <span data-ttu-id="799ea-106">Scénář se aktivuje, když dojde ke kliknutí na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="799ea-106">The storyboard is triggered when the button is clicked.</span></span> <span data-ttu-id="799ea-107"><xref:System.Windows.Media.Animation.Timeline.Completed> Událost je zpracovávána tak, aby program obdrží oznámení při <xref:System.Windows.Media.Animation.ColorAnimation> dokončí.</span><span class="sxs-lookup"><span data-stu-id="799ea-107">The <xref:System.Windows.Media.Animation.Timeline.Completed> event is handled so that the program is notified when the <xref:System.Windows.Media.Animation.ColorAnimation> completes.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton1Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton1declaration)]  
  
## <a name="example"></a><span data-ttu-id="799ea-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="799ea-108">Example</span></span>  
 <span data-ttu-id="799ea-109">Po <xref:System.Windows.Media.Animation.ColorAnimation> dokončí, program se pokusí změnit přebarvení na modrou.</span><span class="sxs-lookup"><span data-stu-id="799ea-109">After the <xref:System.Windows.Media.Animation.ColorAnimation> completes, the program attempts to change the brush's color to blue.</span></span>  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton1Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton1handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton1Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton1handler)]  
  
 <span data-ttu-id="799ea-110">Předchozí kód nezobrazí žádné akce: poskytnutých žlutý, štětce zůstane, což je hodnota <xref:System.Windows.Media.Animation.ColorAnimation> , který animovat štětec.</span><span class="sxs-lookup"><span data-stu-id="799ea-110">The previous code doesn't appear to do anything: the brush remains yellow, which is the value supplied by the <xref:System.Windows.Media.Animation.ColorAnimation> that animated the brush.</span></span> <span data-ttu-id="799ea-111">Základní hodnota vlastnosti (základní hodnoty) se ve skutečnosti změní na modrou.</span><span class="sxs-lookup"><span data-stu-id="799ea-111">The underlying property value (the base value) is actually changed to blue.</span></span> <span data-ttu-id="799ea-112">Ale zůstává žlutý hodnota efektivní nebo aktuální, protože <xref:System.Windows.Media.Animation.ColorAnimation> stále přepisuje základní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="799ea-112">However, the effective, or current, value remains yellow because the <xref:System.Windows.Media.Animation.ColorAnimation> is still overriding the base value.</span></span> <span data-ttu-id="799ea-113">Pokud chcete základní hodnota opět platnou hodnotu, je nutné zastavit animace z vliv na vlastnost.</span><span class="sxs-lookup"><span data-stu-id="799ea-113">If you want the base value to become the effective value again, you must stop the animation from influencing the property.</span></span> <span data-ttu-id="799ea-114">Existují tři způsoby, jak to provést s animacemi scénáře:</span><span class="sxs-lookup"><span data-stu-id="799ea-114">There are three ways to do this with storyboard animations:</span></span>  
  
-   <span data-ttu-id="799ea-115">Nastavení se animace <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> vlastnost <xref:System.Windows.Media.Animation.FillBehavior.Stop></span><span class="sxs-lookup"><span data-stu-id="799ea-115">Set the animation's <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property to <xref:System.Windows.Media.Animation.FillBehavior.Stop></span></span>  
  
-   <span data-ttu-id="799ea-116">Odeberte celý scénář.</span><span class="sxs-lookup"><span data-stu-id="799ea-116">Remove the entire Storyboard.</span></span>  
  
-   <span data-ttu-id="799ea-117">Odstranit animaci jednotlivých vlastností.</span><span class="sxs-lookup"><span data-stu-id="799ea-117">Remove the animation from the individual property.</span></span>  
  
## <a name="set-the-animations-fillbehavior-property-to-stop"></a><span data-ttu-id="799ea-118">Nastavte vlastnost FillBehavior animace Stop</span><span class="sxs-lookup"><span data-stu-id="799ea-118">Set the animation's FillBehavior property to Stop</span></span>  
 <span data-ttu-id="799ea-119">Nastavením <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> k <xref:System.Windows.Media.Animation.FillBehavior.Stop>, dáte animace zastavit po dosažení konce jeho aktivního období by to ovlivnilo její vlastnost target.</span><span class="sxs-lookup"><span data-stu-id="799ea-119">By setting <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> to <xref:System.Windows.Media.Animation.FillBehavior.Stop>, you tell the animation to stop affecting its target property after it reaches the end of its active period.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton2Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton2declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton2Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton2handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton2Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton2handler)]  
  
## <a name="remove-the-entire-storyboard"></a><span data-ttu-id="799ea-120">Odeberte celý scénář</span><span class="sxs-lookup"><span data-stu-id="799ea-120">Remove the entire storyboard</span></span>  
 <span data-ttu-id="799ea-121">Pomocí <xref:System.Windows.Media.Animation.RemoveStoryboard> aktivační události nebo <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType> metoda, dáte animacemi scénáře zastavit by to mělo dopad jejich vlastnosti cíle.</span><span class="sxs-lookup"><span data-stu-id="799ea-121">By using a <xref:System.Windows.Media.Animation.RemoveStoryboard> trigger or the <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType> method, you tell the storyboard animations to stop affecting their target properties.</span></span> <span data-ttu-id="799ea-122">Rozdíl mezi tento přístup a nastavení <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> vlastnost je, že můžete odebrat scénáře v kdykoli, zatímco <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> vlastnost má vliv pouze v případě animace dosáhne konce jeho aktivní období.</span><span class="sxs-lookup"><span data-stu-id="799ea-122">The difference between this approach and setting the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property is that you can remove the storyboard at anytime, while the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property only has an effect when the animation reaches the end of its active period.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton3Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton3declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton3Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton3handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton3Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton3handler)]  
  
## <a name="remove-an-animation-from-an-individual-property"></a><span data-ttu-id="799ea-123">Odebrat z jednotlivých vlastností animace</span><span class="sxs-lookup"><span data-stu-id="799ea-123">Remove an animation from an individual property</span></span>  
 <span data-ttu-id="799ea-124">Další technikou zastavit animaci vlastnosti výstrahy neovlivňovaly je použít <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> metodu objektu animované.</span><span class="sxs-lookup"><span data-stu-id="799ea-124">Another technique to stop an animation from affecting a property is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> method of the object being animated.</span></span> <span data-ttu-id="799ea-125">Zadejte vlastnost animované jako první parametr a `null` jako druhý.</span><span class="sxs-lookup"><span data-stu-id="799ea-125">Specify the property being animated as the first parameter and `null` as the second.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton4Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton4declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton4Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton4handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton4Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton4handler)]  
  
 <span data-ttu-id="799ea-126">Tento postup funguje i pro animace mimo scénář.</span><span class="sxs-lookup"><span data-stu-id="799ea-126">This technique also works for non-storyboard animations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="799ea-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="799ea-127">See also</span></span>
- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.Animation.RemoveStoryboard>
- [<span data-ttu-id="799ea-128">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="799ea-128">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="799ea-129">Přehled způsobů animace vlastností</span><span class="sxs-lookup"><span data-stu-id="799ea-129">Property Animation Techniques Overview</span></span>](property-animation-techniques-overview.md)
