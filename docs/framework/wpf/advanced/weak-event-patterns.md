---
title: Slabý vzor událostí
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: 61e7f6d29cf9275004238ca776d5af9bf027004f
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859913"
---
# <a name="weak-event-patterns"></a><span data-ttu-id="7e891-102">Slabý vzor událostí</span><span class="sxs-lookup"><span data-stu-id="7e891-102">Weak Event Patterns</span></span>
<span data-ttu-id="7e891-103">V aplikacích je možné, že obslužné rutiny, které jsou připojeny ke zdrojům událostí nebude ve spolupráci s objektem naslouchací proces, který připojuje ke zdroji obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="7e891-103">In applications, it is possible that handlers that are attached to event sources will not be destroyed in coordination with the listener object that attached the handler to the source.</span></span> <span data-ttu-id="7e891-104">Tato situace může vést k nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="7e891-104">This situation can lead to memory leaks.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="7e891-105">zavádí návrhový vzor, který je možné tento problém vyřešit tak, že třída vyhrazený správce poskytuje pro určité události a implementace rozhraní pro naslouchací procesy pro tuto událost.</span><span class="sxs-lookup"><span data-stu-id="7e891-105">introduces a design pattern that can be used to address this issue, by providing a dedicated manager class for particular events and implementing an interface on listeners for that event.</span></span> <span data-ttu-id="7e891-106">Tento vzor návrhu se označuje jako *slabý vzor událostí*.</span><span class="sxs-lookup"><span data-stu-id="7e891-106">This design pattern is known as the *weak event pattern*.</span></span>  
  
## <a name="why-implement-the-weak-event-pattern"></a><span data-ttu-id="7e891-107">Proč implementovat vzor slabých událostí?</span><span class="sxs-lookup"><span data-stu-id="7e891-107">Why Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="7e891-108">Naslouchání událostem může vést k nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="7e891-108">Listening for events can lead to memory leaks.</span></span> <span data-ttu-id="7e891-109">Typickou techniku pro naslouchání události je syntaxí specifické pro jazyk, který připojí obslužnou rutinu události ve zdroji.</span><span class="sxs-lookup"><span data-stu-id="7e891-109">The typical technique for listening to an event is to use the language-specific syntax that attaches a handler to an event on a source.</span></span> <span data-ttu-id="7e891-110">Například v C#, že syntaxe je: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span><span class="sxs-lookup"><span data-stu-id="7e891-110">For example, in C#, that syntax is: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span></span>  
  
 <span data-ttu-id="7e891-111">Tento postup vytvoří silného odkazu ze zdroje události do event listener.</span><span class="sxs-lookup"><span data-stu-id="7e891-111">This technique creates a strong reference from the event source to the event listener.</span></span> <span data-ttu-id="7e891-112">Obvykle připojení obslužnou rutinu události pro naslouchací proces způsobí, že naslouchací proces má dobu života objektu, který ovlivňuje dobu života objektu zdroje (Pokud obslužná rutina události je výslovně odebrali).</span><span class="sxs-lookup"><span data-stu-id="7e891-112">Ordinarily, attaching an event handler for a listener causes the listener to have an object lifetime that is influenced by the object lifetime of the source (unless the event handler is explicitly removed).</span></span> <span data-ttu-id="7e891-113">Ale v některých případech může být vhodné doba života objektu naslouchacího procesu pro řídit pomocí dalších faktorů, jako například, jestli aktuálně patří do vizuálního stromu, aplikace a ne životnost zdroje.</span><span class="sxs-lookup"><span data-stu-id="7e891-113">But in certain circumstances, you might want the object lifetime of the listener to be controlled by other factors, such as whether it currently belongs to the visual tree of the application, and not by the lifetime of the source.</span></span> <span data-ttu-id="7e891-114">Pokaždé, když se doba života objektu zdroje se rozpíná za dobu života objektu naslouchacího procesu, vzor normální událost povede k nevrácení paměti: naslouchací proces je udržována nehledě déle, než bylo zamýšleno.</span><span class="sxs-lookup"><span data-stu-id="7e891-114">Whenever the source object lifetime extends beyond the object lifetime of the listener, the normal event pattern leads to a memory leak: the listener is kept alive longer than intended.</span></span>  
  
 <span data-ttu-id="7e891-115">Slabý vzor událostí je navržená pro vyřešení tohoto problému nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="7e891-115">The weak event pattern is designed to solve this memory leak problem.</span></span> <span data-ttu-id="7e891-116">Pokaždé, když se naslouchací proces potřebuje k registraci na událost, ale naslouchací proces nezná explicitně při zrušení registrace je možné slabý vzor událostí.</span><span class="sxs-lookup"><span data-stu-id="7e891-116">The weak event pattern can be used whenever a listener needs to register for an event, but the listener does not explicitly know when to unregister.</span></span> <span data-ttu-id="7e891-117">Slabý vzor událostí je také možné pokaždé, když se doba života objektu zdroje překračuje dobu života objektu užitečné naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="7e891-117">The weak event pattern can also be used whenever the object lifetime of the source exceeds the useful object lifetime of the listener.</span></span> <span data-ttu-id="7e891-118">(V tomto případě *užitečné* se určuje podle vás.) Slabý vzor událostí umožňuje naslouchací proces, zaregistrujte se a přijímat události bez ovlivnění vlastnosti doby života objektu naslouchacího procesu žádným způsobem.</span><span class="sxs-lookup"><span data-stu-id="7e891-118">(In this case, *useful* is determined by you.) The weak event pattern allows the listener to register for and receive the event without affecting the object lifetime characteristics of the listener in any way.</span></span> <span data-ttu-id="7e891-119">V důsledku toho implicitní odkaz ze zdroje nezjišťuje, zda naslouchací proces má nárok na uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7e891-119">In effect, the implied reference from the source does not determine whether the listener is eligible for garbage collection.</span></span> <span data-ttu-id="7e891-120">Odkaz je slabý odkaz, tedy pojmenování slabý vzor událostí a souvisejících rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="7e891-120">The reference is a weak reference, thus the naming of the weak event pattern and the related APIs.</span></span> <span data-ttu-id="7e891-121">Naslouchací proces může být uvolňování paměti shromažďovaným nebo jinak zničeny a zdroji můžete pokračovat bez zachování utvořit obslužná rutina odkazy na nyní zničení objektu.</span><span class="sxs-lookup"><span data-stu-id="7e891-121">The listener can be garbage collected or otherwise destroyed, and the source can continue without retaining noncollectible handler references to a now destroyed object.</span></span>  
  
## <a name="who-should-implement-the-weak-event-pattern"></a><span data-ttu-id="7e891-122">Kdo by měly implementovat vzor slabých událostí?</span><span class="sxs-lookup"><span data-stu-id="7e891-122">Who Should Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="7e891-123">Implementace vzoru slabých událostí je zajímavé hlavně pro autory ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7e891-123">Implementing the weak event pattern is interesting primarily for control authors.</span></span> <span data-ttu-id="7e891-124">Jako autor ovládací prvek jsou do značné míry zodpovědná za chování a členství ve skupině ovládacího prvku a dopad, který má u aplikací, ve kterých je vložen.</span><span class="sxs-lookup"><span data-stu-id="7e891-124">As a control author, you are largely responsible for the behavior and containment of your control and the impact it has on applications in which it is inserted.</span></span> <span data-ttu-id="7e891-125">To zahrnuje řízení chování doba života objektu, zejména zpracování problém nevracení paměti popsané.</span><span class="sxs-lookup"><span data-stu-id="7e891-125">This includes the control object lifetime behavior, in particular the handling of the described memory leak problem.</span></span>  
  
 <span data-ttu-id="7e891-126">Některé scénáře ze své podstaty přizpůsobují aplikace slabý vzor událostí.</span><span class="sxs-lookup"><span data-stu-id="7e891-126">Certain scenarios inherently lend themselves to the application of the weak event pattern.</span></span> <span data-ttu-id="7e891-127">Jeden takový scénář je datové vazby.</span><span class="sxs-lookup"><span data-stu-id="7e891-127">One such scenario is data binding.</span></span> <span data-ttu-id="7e891-128">V datové vazbě je běžné, že zdrojový objekt nezávislou naslouchací proces objektu, který je cílem vazby.</span><span class="sxs-lookup"><span data-stu-id="7e891-128">In data binding, it is common for the source object to be completely independent of the listener object, which is a target of a binding.</span></span> <span data-ttu-id="7e891-129">Mnoho aspektů [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] datové vazby již mít slabý vzor událostí v tom, jak jsou implementované událostí.</span><span class="sxs-lookup"><span data-stu-id="7e891-129">Many aspects of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] data binding already have the weak event pattern applied in how the events are implemented.</span></span>  
  
## <a name="how-to-implement-the-weak-event-pattern"></a><span data-ttu-id="7e891-130">Jak implementovat slabý vzor událostí</span><span class="sxs-lookup"><span data-stu-id="7e891-130">How to Implement the Weak Event Pattern</span></span>  
 <span data-ttu-id="7e891-131">Existují tři způsoby, jak implementovat slabý vzor událostí.</span><span class="sxs-lookup"><span data-stu-id="7e891-131">There are three ways to implement weak event pattern.</span></span> <span data-ttu-id="7e891-132">Následující tabulka uvádí se třemi způsoby a poskytuje pokyny, kdy by každý používá.</span><span class="sxs-lookup"><span data-stu-id="7e891-132">The following table lists the three approaches and provides some guidance for when you should use each.</span></span>  
  
|<span data-ttu-id="7e891-133">Přístup</span><span class="sxs-lookup"><span data-stu-id="7e891-133">Approach</span></span>|<span data-ttu-id="7e891-134">Kdy k implementaci</span><span class="sxs-lookup"><span data-stu-id="7e891-134">When to Implement</span></span>|  
|--------------|-----------------------|  
|<span data-ttu-id="7e891-135">Použít existující třídu správce slabých událostí</span><span class="sxs-lookup"><span data-stu-id="7e891-135">Use an existing weak event manager class</span></span>|<span data-ttu-id="7e891-136">Pokud se chcete přihlásit k odběru události nemá odpovídající <xref:System.Windows.WeakEventManager>, použijte existujícího správce slabých událostí.</span><span class="sxs-lookup"><span data-stu-id="7e891-136">If the event you want to subscribe to has a corresponding <xref:System.Windows.WeakEventManager>, use the existing weak event manager.</span></span> <span data-ttu-id="7e891-137">Seznam správců slabých událostí, které jsou součástí WPF najdete v tématu v hierarchii dědičnosti <xref:System.Windows.WeakEventManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="7e891-137">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span> <span data-ttu-id="7e891-138">Vzhledem k tomu, že správce součástí slabých událostí jsou omezeny, bude pravděpodobně muset zvolte jednu z dalších přístupů.</span><span class="sxs-lookup"><span data-stu-id="7e891-138">Because the included weak event managers are limited, you will probably need to choose one of the other approaches.</span></span>|  
|<span data-ttu-id="7e891-139">Použití třídy obecného slabých událostí správce</span><span class="sxs-lookup"><span data-stu-id="7e891-139">Use a generic weak event manager class</span></span>|<span data-ttu-id="7e891-140">Použití obecného <xref:System.Windows.WeakEventManager%602> pokud stávající <xref:System.Windows.WeakEventManager> má není k dispozici, má snadný způsob, jak implementovat a nemáte zájem o efektivitu.</span><span class="sxs-lookup"><span data-stu-id="7e891-140">Use a generic <xref:System.Windows.WeakEventManager%602> when an existing <xref:System.Windows.WeakEventManager> is not available, you want an easy way to implement, and you are not concerned about efficiency.</span></span> <span data-ttu-id="7e891-141">Obecné <xref:System.Windows.WeakEventManager%602> je méně efektivní než existující nebo vlastní správce slabých událostí.</span><span class="sxs-lookup"><span data-stu-id="7e891-141">The generic <xref:System.Windows.WeakEventManager%602> is less efficient than an existing or custom weak event manager.</span></span> <span data-ttu-id="7e891-142">Například obecná třída nemá další reflexi ke zjišťování událostí, název události.</span><span class="sxs-lookup"><span data-stu-id="7e891-142">For example, the generic class does more reflection to discover the event given the event's name.</span></span> <span data-ttu-id="7e891-143">Navíc kód pro registraci na událost pomocí obecného <xref:System.Windows.WeakEventManager%602> podrobné než při použití existující nebo vlastní <xref:System.Windows.WeakEventManager>.</span><span class="sxs-lookup"><span data-stu-id="7e891-143">Also, the code to register the event by using the generic <xref:System.Windows.WeakEventManager%602> is more verbose than using an existing or custom <xref:System.Windows.WeakEventManager>.</span></span>|  
|<span data-ttu-id="7e891-144">Vytvořte třídu správce vlastní slabých událostí</span><span class="sxs-lookup"><span data-stu-id="7e891-144">Create a custom weak event manager class</span></span>|<span data-ttu-id="7e891-145">Vytvoření vlastní <xref:System.Windows.WeakEventManager> pokud stávající <xref:System.Windows.WeakEventManager> není k dispozici a chcete, aby nejlepšího výkonu.</span><span class="sxs-lookup"><span data-stu-id="7e891-145">Create a custom <xref:System.Windows.WeakEventManager> when an existing <xref:System.Windows.WeakEventManager> is not available and you want the best efficiency.</span></span> <span data-ttu-id="7e891-146">Použití vlastní <xref:System.Windows.WeakEventManager> přihlásit k odběru události bude mnohem efektivnější, ale účtovat náklady na vytváření další kódu na začátku.</span><span class="sxs-lookup"><span data-stu-id="7e891-146">Using a custom <xref:System.Windows.WeakEventManager> to subscribe to an event will be more efficient, but you do incur the cost of writing more code at the beginning.</span></span>|  
|<span data-ttu-id="7e891-147">Pomocí Správce slabých událostí třetích stran</span><span class="sxs-lookup"><span data-stu-id="7e891-147">Use a third-party weak event manager</span></span>|<span data-ttu-id="7e891-148">NuGet má [několik správci slabých událostí](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) a také podpora vzor mnoha architektur WPF (například naleznete v tématu [modulu Prism dokumentaci k odběru událostí volně](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events)).</span><span class="sxs-lookup"><span data-stu-id="7e891-148">NuGet has [several weak event managers](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) and many WPF frameworks also support the pattern (for instance, see [Prism's documentation on loosely coupled event subscription](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events)).</span></span>|

 <span data-ttu-id="7e891-149">Následující části popisují, jak implementovat vzor slabých událostí.</span><span class="sxs-lookup"><span data-stu-id="7e891-149">The following sections describe how to implement the weak event pattern.</span></span>  <span data-ttu-id="7e891-150">Pro účely této diskuse Přihlaste se k odběru události má následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7e891-150">For purposes of this discussion, the event to subscribe to has the following characteristics.</span></span>  
  
- <span data-ttu-id="7e891-151">Je název události `SomeEvent`.</span><span class="sxs-lookup"><span data-stu-id="7e891-151">The event name is `SomeEvent`.</span></span>  
  
- <span data-ttu-id="7e891-152">Událost je vyvolána `EventSource` třídy.</span><span class="sxs-lookup"><span data-stu-id="7e891-152">The event is raised by the `EventSource` class.</span></span>  
  
- <span data-ttu-id="7e891-153">Obslužná rutina události má typ: `SomeEventEventHandler` (nebo `EventHandler<SomeEventEventArgs>`).</span><span class="sxs-lookup"><span data-stu-id="7e891-153">The event handler has type: `SomeEventEventHandler` (or `EventHandler<SomeEventEventArgs>`).</span></span>  
  
- <span data-ttu-id="7e891-154">Událost předává parametr typu `SomeEventEventArgs` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="7e891-154">The event passes a parameter of type `SomeEventEventArgs` to the event handlers.</span></span>  
  
### <a name="using-an-existing-weak-event-manager-class"></a><span data-ttu-id="7e891-155">Použití existující třídy slabé správce událostí</span><span class="sxs-lookup"><span data-stu-id="7e891-155">Using an Existing Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="7e891-156">Najděte si událost ve stávající slabé správce.</span><span class="sxs-lookup"><span data-stu-id="7e891-156">Find an existing weak event manager.</span></span>  
  
     <span data-ttu-id="7e891-157">Seznam správců slabých událostí, které jsou součástí WPF najdete v tématu v hierarchii dědičnosti <xref:System.Windows.WeakEventManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="7e891-157">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
2. <span data-ttu-id="7e891-158">Pomocí nového správce slabých událostí místo normální událost propojení.</span><span class="sxs-lookup"><span data-stu-id="7e891-158">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="7e891-159">Pokud například váš kód používá následující vzor k odběru události:</span><span class="sxs-lookup"><span data-stu-id="7e891-159">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="7e891-160">Změňte ho na následujícímu vzoru:</span><span class="sxs-lookup"><span data-stu-id="7e891-160">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="7e891-161">Podobně pokud váš kód používá následující vzor na zrušit odběr události:</span><span class="sxs-lookup"><span data-stu-id="7e891-161">Similarly, if your code uses the following pattern to unsubscribe from an event:</span></span>  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="7e891-162">Změňte ho na následujícímu vzoru:</span><span class="sxs-lookup"><span data-stu-id="7e891-162">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a><span data-ttu-id="7e891-163">Použití obecné třídy slabé správce událostí</span><span class="sxs-lookup"><span data-stu-id="7e891-163">Using the Generic Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="7e891-164">Použití obecného <xref:System.Windows.WeakEventManager%602> třídy místo normální událost propojení.</span><span class="sxs-lookup"><span data-stu-id="7e891-164">Use the generic <xref:System.Windows.WeakEventManager%602> class instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="7e891-165">Při použití <xref:System.Windows.WeakEventManager%602> zaregistrovat naslouchacích procesů událostí, zadáte zdroj události a <xref:System.EventArgs> typ jako parametry typu třídy a volání <xref:System.Windows.WeakEventManager%602.AddHandler%2A> jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="7e891-165">When you use <xref:System.Windows.WeakEventManager%602> to register event listeners, you supply the event source and <xref:System.EventArgs> type as the type parameters to the class and call <xref:System.Windows.WeakEventManager%602.AddHandler%2A> as shown in the following code:</span></span>  
  
    ```  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a><span data-ttu-id="7e891-166">Vytvoření vlastní třídy slabé správce událostí</span><span class="sxs-lookup"><span data-stu-id="7e891-166">Creating a Custom Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="7e891-167">Zkopírujte následující šablony třídy do projektu.</span><span class="sxs-lookup"><span data-stu-id="7e891-167">Copy the following class template to your project.</span></span>  
  
     <span data-ttu-id="7e891-168">Tato třída dědí z <xref:System.Windows.WeakEventManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="7e891-168">This class inherits from the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2. <span data-ttu-id="7e891-169">Nahradit `SomeEventWeakEventManager` název nahraďte vlastním názvem.</span><span class="sxs-lookup"><span data-stu-id="7e891-169">Replace the `SomeEventWeakEventManager` name with your own name.</span></span>  
  
3. <span data-ttu-id="7e891-170">Nahraďte tři popsané dříve se odpovídající názvy pro událost.</span><span class="sxs-lookup"><span data-stu-id="7e891-170">Replace the three names described previously with the corresponding names for your event.</span></span> <span data-ttu-id="7e891-171">(`SomeEvent`, `EventSource`, a `SomeEventEventArgs`)</span><span class="sxs-lookup"><span data-stu-id="7e891-171">(`SomeEvent`, `EventSource`, and `SomeEventEventArgs`)</span></span>  
  
4. <span data-ttu-id="7e891-172">Nastavte viditelnost (veřejné / interní nebo privátní) třídy správce slabých událostí pro stejnou viditelnost jako událost, kterou spravuje.</span><span class="sxs-lookup"><span data-stu-id="7e891-172">Set the visibility (public / internal / private) of the weak event manager class to the same visibility as event it manages.</span></span>  
  
5. <span data-ttu-id="7e891-173">Pomocí nového správce slabých událostí místo normální událost propojení.</span><span class="sxs-lookup"><span data-stu-id="7e891-173">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="7e891-174">Pokud například váš kód používá následující vzor k odběru události:</span><span class="sxs-lookup"><span data-stu-id="7e891-174">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="7e891-175">Změňte ho na následujícímu vzoru:</span><span class="sxs-lookup"><span data-stu-id="7e891-175">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="7e891-176">Podobně pokud váš kód k odhlášení odběru událostí používá následující vzorec:</span><span class="sxs-lookup"><span data-stu-id="7e891-176">Similarly, if your code uses the following pattern to unsubscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     <span data-ttu-id="7e891-177">Změňte ho na následujícímu vzoru:</span><span class="sxs-lookup"><span data-stu-id="7e891-177">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7e891-178">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7e891-178">See also</span></span>

- <xref:System.Windows.WeakEventManager>
- <xref:System.Windows.IWeakEventListener>
- [<span data-ttu-id="7e891-179">Přehled směrovaných událostí</span><span class="sxs-lookup"><span data-stu-id="7e891-179">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="7e891-180">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="7e891-180">Data Binding Overview</span></span>](../data/data-binding-overview.md)
