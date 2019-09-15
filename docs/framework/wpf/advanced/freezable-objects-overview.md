---
title: Přehled zablokovatelných objektů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], description
- unfreezing Freezable objects [WPF]
- classes [WPF], Freezable
ms.assetid: 89c71692-4f43-4057-b611-67c6a8a863a2
ms.openlocfilehash: 05cd3c27430146f575c23011f53995aa07aaf99e
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991486"
---
# <a name="freezable-objects-overview"></a><span data-ttu-id="d195a-102">Přehled zablokovatelných objektů</span><span class="sxs-lookup"><span data-stu-id="d195a-102">Freezable Objects Overview</span></span>

<span data-ttu-id="d195a-103">V tomto tématu se dozvíte, jak efektivně <xref:System.Windows.Freezable> používat a vytvářet objekty, které poskytují speciální funkce, které mohou pomoci zlepšit výkon aplikace.</span><span class="sxs-lookup"><span data-stu-id="d195a-103">This topic describes how to effectively use and create <xref:System.Windows.Freezable> objects, which provide special features that can help improve application performance.</span></span> <span data-ttu-id="d195a-104">Příklady objektů Freezable zahrnují štětce, pera, transformace, geometrií a animace.</span><span class="sxs-lookup"><span data-stu-id="d195a-104">Examples of freezable objects include brushes, pens, transformations, geometries, and animations.</span></span>

<a name="whatisafreezable"></a>

## <a name="what-is-a-freezable"></a><span data-ttu-id="d195a-105">Co je Freezable?</span><span class="sxs-lookup"><span data-stu-id="d195a-105">What Is a Freezable?</span></span>

<span data-ttu-id="d195a-106">A <xref:System.Windows.Freezable> je speciální typ objektu, který má dva stavy: nezmrazené a zmrazené.</span><span class="sxs-lookup"><span data-stu-id="d195a-106">A <xref:System.Windows.Freezable> is a special type of object that has two states: unfrozen and frozen.</span></span> <span data-ttu-id="d195a-107">Při nezmrazení se <xref:System.Windows.Freezable> zdá, že se chová jako jakýkoliv jiný objekt.</span><span class="sxs-lookup"><span data-stu-id="d195a-107">When unfrozen, a <xref:System.Windows.Freezable> appears to behave like any other object.</span></span> <span data-ttu-id="d195a-108">Po zmrazení <xref:System.Windows.Freezable> již nelze upravovat.</span><span class="sxs-lookup"><span data-stu-id="d195a-108">When frozen, a <xref:System.Windows.Freezable> can no longer be modified.</span></span>

<span data-ttu-id="d195a-109"><xref:System.Windows.Freezable> Poskytujeudálostupozorňujícípozorovatele<xref:System.Windows.Freezable.Changed> na jakékoli úpravy objektu.</span><span class="sxs-lookup"><span data-stu-id="d195a-109">A <xref:System.Windows.Freezable> provides a <xref:System.Windows.Freezable.Changed> event to notify observers of any modifications to the object.</span></span> <span data-ttu-id="d195a-110">Zmrazení <xref:System.Windows.Freezable> může zlepšit jeho výkon, protože už nepotřebuje věnovat prostředky v oznámeních o změnách.</span><span class="sxs-lookup"><span data-stu-id="d195a-110">Freezing a <xref:System.Windows.Freezable> can improve its performance, because it no longer needs to spend resources on change notifications.</span></span> <span data-ttu-id="d195a-111">Zmrazení <xref:System.Windows.Freezable> lze také sdílet mezi vlákny, zatímco nezmrazení <xref:System.Windows.Freezable> nemůže.</span><span class="sxs-lookup"><span data-stu-id="d195a-111">A frozen <xref:System.Windows.Freezable> can also be shared across threads, while an unfrozen <xref:System.Windows.Freezable> cannot.</span></span>

<span data-ttu-id="d195a-112">I když <xref:System.Windows.Freezable> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] třída obsahuje mnoho aplikací, většina objektů v je v relaci s podsystémem grafiky. <xref:System.Windows.Freezable></span><span class="sxs-lookup"><span data-stu-id="d195a-112">Although the <xref:System.Windows.Freezable> class has many applications, most <xref:System.Windows.Freezable> objects in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] are related to the graphics sub-system.</span></span>

<span data-ttu-id="d195a-113"><xref:System.Windows.Freezable> Třída usnadňuje používání určitých grafických systémových objektů a může zvýšit výkon aplikace.</span><span class="sxs-lookup"><span data-stu-id="d195a-113">The <xref:System.Windows.Freezable> class makes it easier to use certain graphics system objects and can help improve application performance.</span></span> <span data-ttu-id="d195a-114">Příklady typů, které dědí z <xref:System.Windows.Freezable> <xref:System.Windows.Media.Brush>zahrnuje třídy, <xref:System.Windows.Media.Transform>a <xref:System.Windows.Media.Geometry> .</span><span class="sxs-lookup"><span data-stu-id="d195a-114">Examples of types that inherit from <xref:System.Windows.Freezable> include the <xref:System.Windows.Media.Brush>, <xref:System.Windows.Media.Transform>, and <xref:System.Windows.Media.Geometry> classes.</span></span> <span data-ttu-id="d195a-115">Vzhledem k tomu, že obsahují nespravované prostředky, systém musí tyto objekty monitorovat pro úpravy a následně aktualizovat odpovídající nespravované prostředky, pokud dojde ke změně původního objektu.</span><span class="sxs-lookup"><span data-stu-id="d195a-115">Because they contain unmanaged resources, the system must monitor these objects for modifications, and then update their corresponding unmanaged resources when there is a change to the original object.</span></span> <span data-ttu-id="d195a-116">I v případě, že ve skutečnosti neupravíte objekt systému grafiky, systém musí stále strávit některé prostředky, které sledují objekt, v případě, že ho změníte.</span><span class="sxs-lookup"><span data-stu-id="d195a-116">Even if you don't actually modify a graphics system object, the system must still spend some of its resources monitoring the object, in case you do change it.</span></span>

<span data-ttu-id="d195a-117">Předpokládejme například, že vytvoříte <xref:System.Windows.Media.SolidColorBrush> štětec a použijete ho k vykreslování pozadí tlačítka.</span><span class="sxs-lookup"><span data-stu-id="d195a-117">For example, suppose you create a <xref:System.Windows.Media.SolidColorBrush> brush and use it to paint the background of a button.</span></span>

[!code-csharp[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart1)]
[!code-vb[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart1)]

<span data-ttu-id="d195a-118">Když je toto tlačítko vykresleno, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá dílčí systém grafiky informace, které jste zadali k vykreslení skupiny pixelů, aby bylo možné vytvořit vzhled tlačítka.</span><span class="sxs-lookup"><span data-stu-id="d195a-118">When the button is rendered, the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] graphics sub-system uses the information you provided to paint a group of pixels to create the appearance of a button.</span></span> <span data-ttu-id="d195a-119">I když jste použili barevný štětec, který popisuje, jak se má tlačítko vykreslit, váš barevný štětec ve skutečnosti neprovede malování.</span><span class="sxs-lookup"><span data-stu-id="d195a-119">Although you used a solid color brush to describe how the button should be painted, your solid color brush doesn't actually do the painting.</span></span> <span data-ttu-id="d195a-120">Grafický systém generuje rychlé objekty nízké úrovně pro tlačítko a štětec a jedná se o objekty, které se ve skutečnosti zobrazují na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="d195a-120">The graphics system generates fast, low-level objects for the button and the brush, and it is those objects that actually appear on the screen.</span></span>

<span data-ttu-id="d195a-121">Pokud jste změnili štětec, bude nutné tyto objekty nízké úrovně znovu vygenerovat.</span><span class="sxs-lookup"><span data-stu-id="d195a-121">If you were to modify the brush, those low-level objects would have to be regenerated.</span></span> <span data-ttu-id="d195a-122">Třída Freezable je to, co umožňuje štětci najít odpovídající vygenerované objekty nízké úrovně a aktualizovat je při změně.</span><span class="sxs-lookup"><span data-stu-id="d195a-122">The freezable class is what gives a brush the ability to find its corresponding generated, low-level objects and to update them when it changes.</span></span> <span data-ttu-id="d195a-123">Když je tato možnost povolená, bude se štětec považovat za nezmrazený.</span><span class="sxs-lookup"><span data-stu-id="d195a-123">When this ability is enabled, the brush is said to be "unfrozen."</span></span>

<span data-ttu-id="d195a-124"><xref:System.Windows.Freezable.Freeze%2A> Metoda Freezable umožňuje zakázat tuto schopnost automatických aktualizací.</span><span class="sxs-lookup"><span data-stu-id="d195a-124">A freezable's <xref:System.Windows.Freezable.Freeze%2A> method enables you to disable this self-updating ability.</span></span> <span data-ttu-id="d195a-125">Tuto metodu lze použít k tomu, aby se štětec stala "zmrazená", nebo neupravitelný.</span><span class="sxs-lookup"><span data-stu-id="d195a-125">You can use this method to make the brush become "frozen," or unmodifiable.</span></span>

> [!NOTE]
> <span data-ttu-id="d195a-126">Ne každý objekt Freezable může být zmrazen.</span><span class="sxs-lookup"><span data-stu-id="d195a-126">Not every Freezable object can be frozen.</span></span> <span data-ttu-id="d195a-127">Chcete-li se <xref:System.InvalidOperationException>vyhnout vyvolání, zkontrolujte hodnotu <xref:System.Windows.Freezable.CanFreeze%2A> vlastnosti objektu Freezable a určete, zda může být zmrazena před pokusem o její zablokování.</span><span class="sxs-lookup"><span data-stu-id="d195a-127">To avoid throwing an <xref:System.InvalidOperationException>, check the value of the Freezable object's <xref:System.Windows.Freezable.CanFreeze%2A> property to determine whether it can be frozen before attempting to freeze it.</span></span>

[!code-csharp[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart2)]
[!code-vb[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart2)]

<span data-ttu-id="d195a-128">Když už nepotřebujete měnit Freezable, zamrznutí poskytuje výhody pro výkon.</span><span class="sxs-lookup"><span data-stu-id="d195a-128">When you no longer need to modify a freezable, freezing it provides performance benefits.</span></span> <span data-ttu-id="d195a-129">Pokud jste v tomto příkladu zablokování štětce, grafický systém už ho nebude potřebovat ke sledování změn.</span><span class="sxs-lookup"><span data-stu-id="d195a-129">If you were to freeze the brush in this example, the graphics system would no longer need to monitor it for changes.</span></span> <span data-ttu-id="d195a-130">Systém grafiky může také provádět další optimalizace, protože ví, že se štětec nemění.</span><span class="sxs-lookup"><span data-stu-id="d195a-130">The graphics system can also make other optimizations, because it knows the brush won't change.</span></span>

> [!NOTE]
> <span data-ttu-id="d195a-131">Pro usnadnění práce objekty Freezable zůstanou nezmrazené, pokud je explicitně neuvolníte.</span><span class="sxs-lookup"><span data-stu-id="d195a-131">For convenience, freezable objects remain unfrozen unless you explicitly freeze them.</span></span>

<a name="frozenfreezables"></a>

## <a name="using-freezables"></a><span data-ttu-id="d195a-132">Použití Zablokovatelné</span><span class="sxs-lookup"><span data-stu-id="d195a-132">Using Freezables</span></span>

<span data-ttu-id="d195a-133">Použití nezmrazeného Freezable se podobá použití jiného typu objektu.</span><span class="sxs-lookup"><span data-stu-id="d195a-133">Using an unfrozen freezable is like using any other type of object.</span></span> <span data-ttu-id="d195a-134">V následujícím příkladu se barva a <xref:System.Windows.Media.SolidColorBrush> změní ze žluté na červenou po použití k vykreslení pozadí tlačítka.</span><span class="sxs-lookup"><span data-stu-id="d195a-134">In the following example, the color of a <xref:System.Windows.Media.SolidColorBrush> is changed from yellow to red after it's used to paint the background of a button.</span></span> <span data-ttu-id="d195a-135">Grafický systém funguje na pozadí, aby při příštím obnovení obrazovky automaticky změnil tlačítko od žluté na červenou.</span><span class="sxs-lookup"><span data-stu-id="d195a-135">The graphics system works behind the scenes to automatically change the button from yellow to red the next time the screen is refreshed.</span></span>

[!code-csharp[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#unfrozenexampleshort)]
[!code-vb[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#unfrozenexampleshort)]

### <a name="freezing-a-freezable"></a><span data-ttu-id="d195a-136">Zmrazení Freezable</span><span class="sxs-lookup"><span data-stu-id="d195a-136">Freezing a Freezable</span></span>

<span data-ttu-id="d195a-137">Chcete-li <xref:System.Windows.Freezable> provést neupravitelný způsob volání, <xref:System.Windows.Freezable.Freeze%2A> zavolejte jeho metodu.</span><span class="sxs-lookup"><span data-stu-id="d195a-137">To make a <xref:System.Windows.Freezable> unmodifiable, you call its <xref:System.Windows.Freezable.Freeze%2A> method.</span></span> <span data-ttu-id="d195a-138">Při zablokování objektu, který obsahuje objekty Freezable, jsou tyto objekty také zmrazeny.</span><span class="sxs-lookup"><span data-stu-id="d195a-138">When you freeze an object that contains freezable objects, those objects are frozen as well.</span></span> <span data-ttu-id="d195a-139">Pokud například zadáte <xref:System.Windows.Media.PathGeometry>, hodnoty a segmenty, které obsahuje, by byly zmrazeny.</span><span class="sxs-lookup"><span data-stu-id="d195a-139">For example, if you freeze a <xref:System.Windows.Media.PathGeometry>, the figures and segments it contains would be frozen too.</span></span>

<span data-ttu-id="d195a-140">Freezable **nelze** zmrazit, pokud platí některá z následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="d195a-140">A Freezable **can't** be frozen if any of the following are true:</span></span>

- <span data-ttu-id="d195a-141">Obsahuje animované nebo vlastnosti vázaného na data.</span><span class="sxs-lookup"><span data-stu-id="d195a-141">It has animated or data bound properties.</span></span>

- <span data-ttu-id="d195a-142">Má vlastnosti nastavené dynamickým prostředkem.</span><span class="sxs-lookup"><span data-stu-id="d195a-142">It has properties set by a dynamic resource.</span></span> <span data-ttu-id="d195a-143">(Další informace o dynamických prostředcích najdete v tématu [zdroje XAML](xaml-resources.md) .)</span><span class="sxs-lookup"><span data-stu-id="d195a-143">(See the [XAML Resources](xaml-resources.md) for more information about dynamic resources.)</span></span>

- <span data-ttu-id="d195a-144">Obsahuje <xref:System.Windows.Freezable> dílčí objekty, které nelze ukotvit.</span><span class="sxs-lookup"><span data-stu-id="d195a-144">It contains <xref:System.Windows.Freezable> sub-objects that can't be frozen.</span></span>

<span data-ttu-id="d195a-145">Pokud jsou tyto podmínky nepravdivé a nehodláte je upravovat <xref:System.Windows.Freezable>, měli byste je zmrazit, abyste získali výše popsané výhody výkonu.</span><span class="sxs-lookup"><span data-stu-id="d195a-145">If these conditions are false, and you don't intend to modify the <xref:System.Windows.Freezable>, then you should freeze it to gain the performance benefits described earlier.</span></span>

<span data-ttu-id="d195a-146">Po volání <xref:System.Windows.Freezable.Freeze%2A> metody Freezable již nelze upravovat.</span><span class="sxs-lookup"><span data-stu-id="d195a-146">Once you call a freezable's <xref:System.Windows.Freezable.Freeze%2A> method, it can no longer be modified.</span></span> <span data-ttu-id="d195a-147">Pokus o úpravu zmrazeného objektu způsobí, že <xref:System.InvalidOperationException> bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="d195a-147">Attempting to modify a frozen object causes an <xref:System.InvalidOperationException> to be thrown.</span></span> <span data-ttu-id="d195a-148">Následující kód vyvolá výjimku, protože se pokusíme štětec změnit po jeho zmrazení.</span><span class="sxs-lookup"><span data-stu-id="d195a-148">The following code throws an exception, because we attempt to modify the brush after it's been frozen.</span></span>

[!code-csharp[freezablesample_procedural#ExceptionExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#exceptionexample)]
[!code-vb[freezablesample_procedural#ExceptionExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#exceptionexample)]

<span data-ttu-id="d195a-149">Chcete-li zabránit vyvolání této výjimky, můžete použít <xref:System.Windows.Freezable.IsFrozen%2A> metodu k určení, zda <xref:System.Windows.Freezable> je objekt zmrazen.</span><span class="sxs-lookup"><span data-stu-id="d195a-149">To avoid throwing this exception, you can use the <xref:System.Windows.Freezable.IsFrozen%2A> method to determine whether a <xref:System.Windows.Freezable> is frozen.</span></span>

[!code-csharp[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
[!code-vb[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]

<span data-ttu-id="d195a-150">V předchozím příkladu kódu byla Upravitelná kopie vytvořena zmrazeným objektem pomocí <xref:System.Windows.Freezable.Clone%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d195a-150">In the preceding code example, a modifiable copy was made of a frozen object using the <xref:System.Windows.Freezable.Clone%2A> method.</span></span> <span data-ttu-id="d195a-151">Další část popisuje klonování podrobněji.</span><span class="sxs-lookup"><span data-stu-id="d195a-151">The next section discusses cloning in more detail.</span></span>

> [!NOTE]
> <span data-ttu-id="d195a-152">Vzhledem k tomu, že zmrazené Freezable nemohou být animovány, systém animace automaticky vytvoří upravitelné klony zmrazených <xref:System.Windows.Freezable> objektů při pokusu o jejich animaci <xref:System.Windows.Media.Animation.Storyboard>pomocí.</span><span class="sxs-lookup"><span data-stu-id="d195a-152">Because a frozen freezable cannot be animated, the animation system will automatically create modifiable clones of frozen <xref:System.Windows.Freezable> objects when you try to animate them with a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="d195a-153">Chcete-li odstranit režii výkonu způsobenou klonování, ponechte objekt nezmrazený, pokud je v úmyslu ho animovat.</span><span class="sxs-lookup"><span data-stu-id="d195a-153">To eliminate the performance overhead caused by cloning, leave an object unfrozen if you intend to animate it.</span></span> <span data-ttu-id="d195a-154">Další informace o animování ve scénářích najdete v [přehledu scénářů](../graphics-multimedia/storyboards-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d195a-154">For more information about animating with storyboards, see the [Storyboards Overview](../graphics-multimedia/storyboards-overview.md).</span></span>

### <a name="freezing-from-markup"></a><span data-ttu-id="d195a-155">Zamrznutí ze značek</span><span class="sxs-lookup"><span data-stu-id="d195a-155">Freezing from Markup</span></span>

<span data-ttu-id="d195a-156">Chcete-li <xref:System.Windows.Freezable> zablokovat objekt deklarovaný v kódu, `PresentationOptions:Freeze` použijte atribut.</span><span class="sxs-lookup"><span data-stu-id="d195a-156">To freeze a <xref:System.Windows.Freezable> object declared in markup, you use the `PresentationOptions:Freeze` attribute.</span></span> <span data-ttu-id="d195a-157">V následujícím příkladu <xref:System.Windows.Media.SolidColorBrush> je deklarován jako prostředek stránky a zmrazen.</span><span class="sxs-lookup"><span data-stu-id="d195a-157">In the following example, a <xref:System.Windows.Media.SolidColorBrush> is declared as a page resource and frozen.</span></span> <span data-ttu-id="d195a-158">Pak se použije k nastavení pozadí tlačítka.</span><span class="sxs-lookup"><span data-stu-id="d195a-158">It is then used to set the background of a button.</span></span>

[!code-xaml[FreezableSample#FreezeFromMarkupWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FreezableSample/CS/FreezeFromMarkupExample.xaml#freezefrommarkupwholepage)]

<span data-ttu-id="d195a-159">Chcete-li `Freeze` použít atribut, je nutné namapovat na obor názvů možností `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`prezentace:.</span><span class="sxs-lookup"><span data-stu-id="d195a-159">To use the `Freeze` attribute, you must map to the presentation options namespace: `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`.</span></span> <span data-ttu-id="d195a-160">`PresentationOptions`je doporučená předpona pro mapování tohoto oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="d195a-160">`PresentationOptions` is the recommended prefix for mapping this namespace:</span></span>

```xaml
xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"
```

<span data-ttu-id="d195a-161">Vzhledem k tomu, že ne všechny čtečky XAML rozpoznávají tento atribut, je doporučeno použít [atribut MC: reignorovat](mc-ignorable-attribute.md) k označení `Presentation:Freeze` atributu jako ignorovatelné:</span><span class="sxs-lookup"><span data-stu-id="d195a-161">Because not all XAML readers recognize this attribute, it's recommended that you use the [mc:Ignorable Attribute](mc-ignorable-attribute.md) to mark the `Presentation:Freeze` attribute as ignorable:</span></span>

```xaml
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="PresentationOptions"
```

<span data-ttu-id="d195a-162">Další informace najdete na stránce [atributu MC: Reignorovatelné](mc-ignorable-attribute.md) .</span><span class="sxs-lookup"><span data-stu-id="d195a-162">For more information, see the [mc:Ignorable Attribute](mc-ignorable-attribute.md) page.</span></span>

### <a name="unfreezing-a-freezable"></a><span data-ttu-id="d195a-163">"Unmrznutí" a Freezable</span><span class="sxs-lookup"><span data-stu-id="d195a-163">"Unfreezing" a Freezable</span></span>

<span data-ttu-id="d195a-164">Po zmrazení <xref:System.Windows.Freezable> nemůže být nikdy upravován ani nezmrazený. můžete však vytvořit nezmrazený klon <xref:System.Windows.Freezable.Clone%2A> pomocí metody nebo <xref:System.Windows.Freezable.CloneCurrentValue%2A> .</span><span class="sxs-lookup"><span data-stu-id="d195a-164">Once frozen, a <xref:System.Windows.Freezable> can never be modified or unfrozen; however, you can create an unfrozen clone using the <xref:System.Windows.Freezable.Clone%2A> or <xref:System.Windows.Freezable.CloneCurrentValue%2A> method.</span></span>

<span data-ttu-id="d195a-165">V následujícím příkladu je pozadí na tlačítku nastaveno pomocí štětce a následně zmrazení štětce.</span><span class="sxs-lookup"><span data-stu-id="d195a-165">In the following example, the button's background is set with a brush and that brush is then frozen.</span></span> <span data-ttu-id="d195a-166">Nezmrazená kopie se skládá z štětce pomocí <xref:System.Windows.Freezable.Clone%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d195a-166">An unfrozen copy is made of the brush using the <xref:System.Windows.Freezable.Clone%2A> method.</span></span> <span data-ttu-id="d195a-167">Klon se upraví a použije se ke změně pozadí tlačítka ze žluté na červenou.</span><span class="sxs-lookup"><span data-stu-id="d195a-167">The clone is modified and used to change the button's background from yellow to red.</span></span>

[!code-csharp[freezablesample_procedural#CloneExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
[!code-vb[freezablesample_procedural#CloneExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]

> [!NOTE]
> <span data-ttu-id="d195a-168">Bez ohledu na to, kterou metodu klonování použijete, se animace nikdy nezkopírují do nového <xref:System.Windows.Freezable>.</span><span class="sxs-lookup"><span data-stu-id="d195a-168">Regardless of which clone method you use, animations are never copied to the new <xref:System.Windows.Freezable>.</span></span>

<span data-ttu-id="d195a-169">Metody <xref:System.Windows.Freezable.Clone%2A> a<xref:System.Windows.Freezable.CloneCurrentValue%2A> vytváří hluboké kopie Freezable.</span><span class="sxs-lookup"><span data-stu-id="d195a-169">The <xref:System.Windows.Freezable.Clone%2A> and <xref:System.Windows.Freezable.CloneCurrentValue%2A> methods produce deep copies of the freezable.</span></span> <span data-ttu-id="d195a-170">Pokud Freezable obsahuje jiné zmrazené objekty Freezable, naklonují se a dají se upravovat.</span><span class="sxs-lookup"><span data-stu-id="d195a-170">If the freezable contains other frozen freezable objects, they are also cloned and made modifiable.</span></span> <span data-ttu-id="d195a-171">Například pokud naklonujte zmrazení <xref:System.Windows.Media.PathGeometry> tak, aby bylo možné ho upravovat, hodnoty a segmenty, které obsahuje, jsou také zkopírovány a provedeny jako upravitelné.</span><span class="sxs-lookup"><span data-stu-id="d195a-171">For example, if you clone a frozen <xref:System.Windows.Media.PathGeometry> to make it modifiable, the figures and segments it contains are also copied and made modifiable.</span></span>

<a name="createyourownfreezableclass"></a>

## <a name="creating-your-own-freezable-class"></a><span data-ttu-id="d195a-172">Vytvoření vlastní třídy Freezable</span><span class="sxs-lookup"><span data-stu-id="d195a-172">Creating Your Own Freezable Class</span></span>

<span data-ttu-id="d195a-173">Třída, která je odvozena <xref:System.Windows.Freezable> z, získává následující funkce.</span><span class="sxs-lookup"><span data-stu-id="d195a-173">A class that derives from <xref:System.Windows.Freezable> gains the following features.</span></span>

- <span data-ttu-id="d195a-174">Speciální stavy: jen pro čtení (zmrazeno) a stav zápisu.</span><span class="sxs-lookup"><span data-stu-id="d195a-174">Special states: a read-only (frozen) and a writable state.</span></span>

- <span data-ttu-id="d195a-175">Bezpečnost vlákna: zmrazení <xref:System.Windows.Freezable> lze sdílet napříč vlákny.</span><span class="sxs-lookup"><span data-stu-id="d195a-175">Thread safety: a frozen <xref:System.Windows.Freezable> can be shared across threads.</span></span>

- <span data-ttu-id="d195a-176">Podrobné oznámení o změně: Na rozdíl od <xref:System.Windows.DependencyObject>jiných s Freezable objekty poskytují oznámení o změně, když se změní hodnoty dílčích vlastností.</span><span class="sxs-lookup"><span data-stu-id="d195a-176">Detailed change notification: Unlike other <xref:System.Windows.DependencyObject>s, Freezable objects provide change notifications when sub-property values change.</span></span>

- <span data-ttu-id="d195a-177">Snadné klonování: třída Freezable už implementovala několik metod, které vytváří hloubkové klony.</span><span class="sxs-lookup"><span data-stu-id="d195a-177">Easy cloning: the Freezable class has already implemented several methods that produce deep clones.</span></span>

<span data-ttu-id="d195a-178">A <xref:System.Windows.Freezable> je <xref:System.Windows.DependencyObject>typu, a proto používá systém vlastností závislosti.</span><span class="sxs-lookup"><span data-stu-id="d195a-178">A <xref:System.Windows.Freezable> is a type of <xref:System.Windows.DependencyObject>, and therefore uses the dependency property system.</span></span> <span data-ttu-id="d195a-179">Vlastnosti vaší třídy nemusí být vlastnosti závislosti, ale pomocí vlastností závislosti se zmenší množství kódu, který musíte napsat, protože <xref:System.Windows.Freezable> třída byla navržena s vlastnostmi závislosti.</span><span class="sxs-lookup"><span data-stu-id="d195a-179">Your class properties don't have to be dependency properties, but using dependency properties will reduce the amount of code you have to write, because the <xref:System.Windows.Freezable> class was designed with dependency properties in mind.</span></span> <span data-ttu-id="d195a-180">Další informace o systému vlastností závislosti naleznete v tématu [Přehled vlastností závislosti](dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d195a-180">For more information about the dependency property system, see the [Dependency Properties Overview](dependency-properties-overview.md).</span></span>

<span data-ttu-id="d195a-181">Každá <xref:System.Windows.Freezable> podtřída musí <xref:System.Windows.Freezable.CreateInstanceCore%2A> přepsat metodu.</span><span class="sxs-lookup"><span data-stu-id="d195a-181">Every <xref:System.Windows.Freezable> subclass must override the <xref:System.Windows.Freezable.CreateInstanceCore%2A> method.</span></span> <span data-ttu-id="d195a-182">Pokud vaše třída používá vlastnosti závislosti pro všechna svoje data, budete hotovi.</span><span class="sxs-lookup"><span data-stu-id="d195a-182">If your class uses dependency properties for all its data, you're finished.</span></span>

<span data-ttu-id="d195a-183">Pokud vaše třída obsahuje datové členy vlastnosti bez závislosti, je nutné také přepsat následující metody:</span><span class="sxs-lookup"><span data-stu-id="d195a-183">If your class contains non-dependency property data members, you must also override the following methods:</span></span>

- <xref:System.Windows.Freezable.CloneCore%2A>

- <xref:System.Windows.Freezable.CloneCurrentValueCore%2A>

- <xref:System.Windows.Freezable.GetAsFrozenCore%2A>

- <xref:System.Windows.Freezable.GetCurrentValueAsFrozenCore%2A>

- <xref:System.Windows.Freezable.FreezeCore%2A>

<span data-ttu-id="d195a-184">Také je nutné sledovat následující pravidla pro přístup a zápis do datových členů, kteří nejsou vlastnostmi závislosti:</span><span class="sxs-lookup"><span data-stu-id="d195a-184">You must also observe the following rules for accessing and writing to data members that are not dependency properties:</span></span>

- <span data-ttu-id="d195a-185">Na začátku libovolného rozhraní API, které čte datové členy vlastnosti bez závislosti, zavolejte <xref:System.Windows.Freezable.ReadPreamble%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="d195a-185">At the beginning of any API that reads non-dependency property data members, call the <xref:System.Windows.Freezable.ReadPreamble%2A> method.</span></span>

- <span data-ttu-id="d195a-186">Na začátku jakéhokoli rozhraní API, které zapisuje datové členy vlastnosti bez závislosti, zavolejte <xref:System.Windows.Freezable.WritePreamble%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="d195a-186">At the beginning of any API that writes non-dependency property data members, call the <xref:System.Windows.Freezable.WritePreamble%2A> method.</span></span> <span data-ttu-id="d195a-187">(Po volání <xref:System.Windows.Freezable.WritePreamble%2A> v rozhraní API není nutné provádět další <xref:System.Windows.Freezable.ReadPreamble%2A> volání, pokud také přečtete datové členy vlastnosti, které nejsou závislé na závislostech.)</span><span class="sxs-lookup"><span data-stu-id="d195a-187">(Once you've called <xref:System.Windows.Freezable.WritePreamble%2A> in an API, you don't need to make an additional call to <xref:System.Windows.Freezable.ReadPreamble%2A> if you also read non-dependency property data members.)</span></span>

- <span data-ttu-id="d195a-188">Před ukončením metod, které jsou zapsány do datových členů vlastnosti bez závislosti, volejte metodu.<xref:System.Windows.Freezable.WritePostscript%2A></span><span class="sxs-lookup"><span data-stu-id="d195a-188">Call the <xref:System.Windows.Freezable.WritePostscript%2A> method before exiting methods that write to non-dependency property data members.</span></span>

<span data-ttu-id="d195a-189">Pokud vaše třída obsahuje datové členy, které nejsou <xref:System.Windows.DependencyObject> závislé na vlastnostech, je nutné <xref:System.Windows.Freezable.OnFreezablePropertyChanged%2A> volat metodu také pokaždé, když změníte jednu z jejich hodnot, a to i v případě, že nastavujete `null`člena.</span><span class="sxs-lookup"><span data-stu-id="d195a-189">If your class contains non-dependency-property data members that are <xref:System.Windows.DependencyObject> objects, you must also call the <xref:System.Windows.Freezable.OnFreezablePropertyChanged%2A> method each time you change one of their values, even if you're setting the member to `null`.</span></span>

> [!NOTE]
> <span data-ttu-id="d195a-190">Je velmi důležité, abyste začali každou <xref:System.Windows.Freezable> metodu, kterou jste přepsali, voláním základní implementace.</span><span class="sxs-lookup"><span data-stu-id="d195a-190">It's very important that you begin each <xref:System.Windows.Freezable> method you override with a call to the base implementation.</span></span>

<span data-ttu-id="d195a-191">Příklad vlastní <xref:System.Windows.Freezable> třídy naleznete v [ukázce vlastní animace](https://go.microsoft.com/fwlink/?LinkID=159981).</span><span class="sxs-lookup"><span data-stu-id="d195a-191">For an example of a custom <xref:System.Windows.Freezable> class, see the [Custom Animation Sample](https://go.microsoft.com/fwlink/?LinkID=159981).</span></span>

## <a name="see-also"></a><span data-ttu-id="d195a-192">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d195a-192">See also</span></span>

- <xref:System.Windows.Freezable>
- [<span data-ttu-id="d195a-193">Ukázka vlastní animace</span><span class="sxs-lookup"><span data-stu-id="d195a-193">Custom Animation Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159981)
- [<span data-ttu-id="d195a-194">Přehled vlastností závislosti</span><span class="sxs-lookup"><span data-stu-id="d195a-194">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="d195a-195">Vlastní vlastnosti závislosti</span><span class="sxs-lookup"><span data-stu-id="d195a-195">Custom Dependency Properties</span></span>](custom-dependency-properties.md)
