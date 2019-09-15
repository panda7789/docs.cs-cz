---
title: Slabý vzor událostí
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: f4cbb22a3cdd7b966c36f6c8246b13b5c58e056d
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991792"
---
# <a name="weak-event-patterns"></a><span data-ttu-id="b0d74-102">Slabý vzor událostí</span><span class="sxs-lookup"><span data-stu-id="b0d74-102">Weak Event Patterns</span></span>
<span data-ttu-id="b0d74-103">V aplikacích je možné, že obslužné rutiny, které jsou připojeny ke zdrojům událostí, nebudou zničeny v koordinaci s objektem naslouchacího procesu, který připojil obslužnou rutinu ke zdroji.</span><span class="sxs-lookup"><span data-stu-id="b0d74-103">In applications, it is possible that handlers that are attached to event sources will not be destroyed in coordination with the listener object that attached the handler to the source.</span></span> <span data-ttu-id="b0d74-104">Tato situace může vést k nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="b0d74-104">This situation can lead to memory leaks.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="b0d74-105">zavádí vzor návrhu, který lze použít k vyřešení tohoto problému, poskytnutím vyhrazené třídy správce pro konkrétní události a implementací rozhraní na naslouchací proces pro danou událost.</span><span class="sxs-lookup"><span data-stu-id="b0d74-105">introduces a design pattern that can be used to address this issue, by providing a dedicated manager class for particular events and implementing an interface on listeners for that event.</span></span> <span data-ttu-id="b0d74-106">Tento vzor návrhu je známý jako *slabý vzorek události*.</span><span class="sxs-lookup"><span data-stu-id="b0d74-106">This design pattern is known as the *weak event pattern*.</span></span>  
  
## <a name="why-implement-the-weak-event-pattern"></a><span data-ttu-id="b0d74-107">Proč implementovat slabý vzorek události?</span><span class="sxs-lookup"><span data-stu-id="b0d74-107">Why Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="b0d74-108">Poslouchání událostí může vést k nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="b0d74-108">Listening for events can lead to memory leaks.</span></span> <span data-ttu-id="b0d74-109">Typická technika pro naslouchání události je použít syntaxi specifickou pro jazyk, která připojí obslužnou rutinu k události ve zdroji.</span><span class="sxs-lookup"><span data-stu-id="b0d74-109">The typical technique for listening to an event is to use the language-specific syntax that attaches a handler to an event on a source.</span></span> <span data-ttu-id="b0d74-110">Například v C#, tato syntaxe je: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span><span class="sxs-lookup"><span data-stu-id="b0d74-110">For example, in C#, that syntax is: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span></span>  
  
 <span data-ttu-id="b0d74-111">Tato technika vytvoří silný odkaz ze zdroje události na naslouchací proces událostí.</span><span class="sxs-lookup"><span data-stu-id="b0d74-111">This technique creates a strong reference from the event source to the event listener.</span></span> <span data-ttu-id="b0d74-112">Obvykle připojení obslužné rutiny události pro naslouchací proces způsobí, že naslouchací proces bude mít životnost objektu, která je ovlivněna životností objektu zdroje (Pokud není obslužná rutina události explicitně odebrána).</span><span class="sxs-lookup"><span data-stu-id="b0d74-112">Ordinarily, attaching an event handler for a listener causes the listener to have an object lifetime that is influenced by the object lifetime of the source (unless the event handler is explicitly removed).</span></span> <span data-ttu-id="b0d74-113">V některých případech však můžete chtít, aby životnost objektu naslouchacího procesu byla kontrolována jinými faktory, například zda aktuálně patří do vizuálního stromu aplikace, a nikoli po dobu života zdroje.</span><span class="sxs-lookup"><span data-stu-id="b0d74-113">But in certain circumstances, you might want the object lifetime of the listener to be controlled by other factors, such as whether it currently belongs to the visual tree of the application, and not by the lifetime of the source.</span></span> <span data-ttu-id="b0d74-114">Pokaždé, když životnost zdrojového objektu přesáhne dobu životnosti objektu naslouchacího procesu, vzorek normální události vede k nevrácení paměti: naslouchací proces je udržován v provozu déle, než je určeno.</span><span class="sxs-lookup"><span data-stu-id="b0d74-114">Whenever the source object lifetime extends beyond the object lifetime of the listener, the normal event pattern leads to a memory leak: the listener is kept alive longer than intended.</span></span>  
  
 <span data-ttu-id="b0d74-115">Slabý vzorek události je navržen pro vyřešení problému při nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="b0d74-115">The weak event pattern is designed to solve this memory leak problem.</span></span> <span data-ttu-id="b0d74-116">Slabý vzorek události lze použít vždy, když se naslouchací proces potřebuje zaregistrovat pro událost, ale naslouchací proces výslovně neví, kdy zrušit registraci.</span><span class="sxs-lookup"><span data-stu-id="b0d74-116">The weak event pattern can be used whenever a listener needs to register for an event, but the listener does not explicitly know when to unregister.</span></span> <span data-ttu-id="b0d74-117">Slabý vzorek události lze také použít vždy, když životnost objektu zdroje překračuje užitečnou životnost objektu naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="b0d74-117">The weak event pattern can also be used whenever the object lifetime of the source exceeds the useful object lifetime of the listener.</span></span> <span data-ttu-id="b0d74-118">(V takovém případě je to *užitečné* , je určeno vámi.) Slabý vzorek události umožňuje naslouchací proces registrovat a přijímat události, aniž by to ovlivnilo vlastnosti životnosti objektu naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="b0d74-118">(In this case, *useful* is determined by you.) The weak event pattern allows the listener to register for and receive the event without affecting the object lifetime characteristics of the listener in any way.</span></span> <span data-ttu-id="b0d74-119">V podstatě implicitní odkaz ze zdroje neurčuje, zda má naslouchací proces nárok na uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b0d74-119">In effect, the implied reference from the source does not determine whether the listener is eligible for garbage collection.</span></span> <span data-ttu-id="b0d74-120">Odkaz je slabý odkaz, takže pojmenováváme slabý vzorek události a související rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="b0d74-120">The reference is a weak reference, thus the naming of the weak event pattern and the related APIs.</span></span> <span data-ttu-id="b0d74-121">Naslouchací proces může být shromážděn z paměti nebo jinak zničen a zdroj může pokračovat bez uchování odkazů obslužných rutin utvořit na objekt, který je nyní zničen.</span><span class="sxs-lookup"><span data-stu-id="b0d74-121">The listener can be garbage collected or otherwise destroyed, and the source can continue without retaining noncollectible handler references to a now destroyed object.</span></span>  
  
## <a name="who-should-implement-the-weak-event-pattern"></a><span data-ttu-id="b0d74-122">Kdo má implementovat slabý vzorek události?</span><span class="sxs-lookup"><span data-stu-id="b0d74-122">Who Should Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="b0d74-123">Implementace slabého vzoru události je zajímavá hlavně pro autory ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="b0d74-123">Implementing the weak event pattern is interesting primarily for control authors.</span></span> <span data-ttu-id="b0d74-124">Jako autor ovládacího prvku je převážně zodpovědný za chování a omezení vašeho řízení a vliv na aplikace, do kterých je vložen.</span><span class="sxs-lookup"><span data-stu-id="b0d74-124">As a control author, you are largely responsible for the behavior and containment of your control and the impact it has on applications in which it is inserted.</span></span> <span data-ttu-id="b0d74-125">To zahrnuje chování při životnosti řídicích objektů, zejména zpracování popsaného problému při nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="b0d74-125">This includes the control object lifetime behavior, in particular the handling of the described memory leak problem.</span></span>  
  
 <span data-ttu-id="b0d74-126">Některé scénáře jsou z vlastního podstaty zapůjčení do aplikace slabého vzoru události.</span><span class="sxs-lookup"><span data-stu-id="b0d74-126">Certain scenarios inherently lend themselves to the application of the weak event pattern.</span></span> <span data-ttu-id="b0d74-127">Jedním z takových scénářů je vázání dat.</span><span class="sxs-lookup"><span data-stu-id="b0d74-127">One such scenario is data binding.</span></span> <span data-ttu-id="b0d74-128">V datové vazbě je běžné, že zdrojový objekt je zcela nezávislý na objektu naslouchacího procesu, který je cílem vazby.</span><span class="sxs-lookup"><span data-stu-id="b0d74-128">In data binding, it is common for the source object to be completely independent of the listener object, which is a target of a binding.</span></span> <span data-ttu-id="b0d74-129">Mnoho aspektů [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] datové vazby už má slabý vzor událostí, který se používá při implementaci událostí.</span><span class="sxs-lookup"><span data-stu-id="b0d74-129">Many aspects of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] data binding already have the weak event pattern applied in how the events are implemented.</span></span>  
  
## <a name="how-to-implement-the-weak-event-pattern"></a><span data-ttu-id="b0d74-130">Jak implementovat slabý vzorek události</span><span class="sxs-lookup"><span data-stu-id="b0d74-130">How to Implement the Weak Event Pattern</span></span>  
 <span data-ttu-id="b0d74-131">Existují tři způsoby, jak implementovat slabý vzorek události.</span><span class="sxs-lookup"><span data-stu-id="b0d74-131">There are three ways to implement weak event pattern.</span></span> <span data-ttu-id="b0d74-132">Následující tabulka uvádí tři přístupy a poskytuje pokyny pro použití každého z nich.</span><span class="sxs-lookup"><span data-stu-id="b0d74-132">The following table lists the three approaches and provides some guidance for when you should use each.</span></span>  
  
|<span data-ttu-id="b0d74-133">Přístup</span><span class="sxs-lookup"><span data-stu-id="b0d74-133">Approach</span></span>|<span data-ttu-id="b0d74-134">Kdy implementovat</span><span class="sxs-lookup"><span data-stu-id="b0d74-134">When to Implement</span></span>|  
|--------------|-----------------------|  
|<span data-ttu-id="b0d74-135">Použít stávající slabší třídu správce událostí</span><span class="sxs-lookup"><span data-stu-id="b0d74-135">Use an existing weak event manager class</span></span>|<span data-ttu-id="b0d74-136">Pokud má událost, které se má přihlásit k odběru, <xref:System.Windows.WeakEventManager>odpovídající, použijte stávající správce slabé události.</span><span class="sxs-lookup"><span data-stu-id="b0d74-136">If the event you want to subscribe to has a corresponding <xref:System.Windows.WeakEventManager>, use the existing weak event manager.</span></span> <span data-ttu-id="b0d74-137">Seznam slabých správců událostí, které jsou součástí WPF, najdete v tématu Hierarchie dědičnosti ve <xref:System.Windows.WeakEventManager> třídě.</span><span class="sxs-lookup"><span data-stu-id="b0d74-137">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span> <span data-ttu-id="b0d74-138">Vzhledem k tomu, že jsou zahrnuté slabé správce událostí omezené, budete pravděpodobně muset zvolit jeden z dalších přístupů.</span><span class="sxs-lookup"><span data-stu-id="b0d74-138">Because the included weak event managers are limited, you will probably need to choose one of the other approaches.</span></span>|  
|<span data-ttu-id="b0d74-139">Použití obecné třídy slabého správce událostí</span><span class="sxs-lookup"><span data-stu-id="b0d74-139">Use a generic weak event manager class</span></span>|<span data-ttu-id="b0d74-140">Použijte obecné <xref:System.Windows.WeakEventManager%602> , pokud není k <xref:System.Windows.WeakEventManager> dispozici existující, chcete snadno implementovat a nebudete mít obavy o efektivitu.</span><span class="sxs-lookup"><span data-stu-id="b0d74-140">Use a generic <xref:System.Windows.WeakEventManager%602> when an existing <xref:System.Windows.WeakEventManager> is not available, you want an easy way to implement, and you are not concerned about efficiency.</span></span> <span data-ttu-id="b0d74-141">Obecný <xref:System.Windows.WeakEventManager%602> je méně efektivní než stávající nebo vlastní slabý správce událostí.</span><span class="sxs-lookup"><span data-stu-id="b0d74-141">The generic <xref:System.Windows.WeakEventManager%602> is less efficient than an existing or custom weak event manager.</span></span> <span data-ttu-id="b0d74-142">Například obecná třída má větší odraz pro zjištění události s ohledem na název události.</span><span class="sxs-lookup"><span data-stu-id="b0d74-142">For example, the generic class does more reflection to discover the event given the event's name.</span></span> <span data-ttu-id="b0d74-143">Také kód pro registraci události pomocí obecného <xref:System.Windows.WeakEventManager%602> je podrobnější než použití existující nebo vlastní. <xref:System.Windows.WeakEventManager></span><span class="sxs-lookup"><span data-stu-id="b0d74-143">Also, the code to register the event by using the generic <xref:System.Windows.WeakEventManager%602> is more verbose than using an existing or custom <xref:System.Windows.WeakEventManager>.</span></span>|  
|<span data-ttu-id="b0d74-144">Vytvoření vlastní slabé třídy správce událostí</span><span class="sxs-lookup"><span data-stu-id="b0d74-144">Create a custom weak event manager class</span></span>|<span data-ttu-id="b0d74-145">Pokud není k <xref:System.Windows.WeakEventManager> dispozici existující <xref:System.Windows.WeakEventManager> a chcete nejlepší efektivitu, vytvořte vlastní.</span><span class="sxs-lookup"><span data-stu-id="b0d74-145">Create a custom <xref:System.Windows.WeakEventManager> when an existing <xref:System.Windows.WeakEventManager> is not available and you want the best efficiency.</span></span> <span data-ttu-id="b0d74-146">Použití vlastního <xref:System.Windows.WeakEventManager> přihlášení k odběru události bude efektivnější, ale náklady na zápis dalších kódů na začátku se účtují.</span><span class="sxs-lookup"><span data-stu-id="b0d74-146">Using a custom <xref:System.Windows.WeakEventManager> to subscribe to an event will be more efficient, but you do incur the cost of writing more code at the beginning.</span></span>|  
|<span data-ttu-id="b0d74-147">Použití slabého správce událostí třetí strany</span><span class="sxs-lookup"><span data-stu-id="b0d74-147">Use a third-party weak event manager</span></span>|<span data-ttu-id="b0d74-148">NuGet má [několik slabých správců událostí](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) a řada platforem WPF také podporuje vzor (například [dokumentaci Prism o volně vázaných odběrech událostí](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events)).</span><span class="sxs-lookup"><span data-stu-id="b0d74-148">NuGet has [several weak event managers](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) and many WPF frameworks also support the pattern (for instance, see [Prism's documentation on loosely coupled event subscription](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events)).</span></span>|

 <span data-ttu-id="b0d74-149">Následující části popisují, jak implementovat slabý vzorek události.</span><span class="sxs-lookup"><span data-stu-id="b0d74-149">The following sections describe how to implement the weak event pattern.</span></span>  <span data-ttu-id="b0d74-150">Pro účely této diskuze má událost pro přihlášení k odběru následující charakteristiky.</span><span class="sxs-lookup"><span data-stu-id="b0d74-150">For purposes of this discussion, the event to subscribe to has the following characteristics.</span></span>  
  
- <span data-ttu-id="b0d74-151">Název události je `SomeEvent`.</span><span class="sxs-lookup"><span data-stu-id="b0d74-151">The event name is `SomeEvent`.</span></span>  
  
- <span data-ttu-id="b0d74-152">Událost je vyvolána `EventSource` třídou.</span><span class="sxs-lookup"><span data-stu-id="b0d74-152">The event is raised by the `EventSource` class.</span></span>  
  
- <span data-ttu-id="b0d74-153">Obslužná rutina události je typu `SomeEventEventHandler` : ( `EventHandler<SomeEventEventArgs>`nebo).</span><span class="sxs-lookup"><span data-stu-id="b0d74-153">The event handler has type: `SomeEventEventHandler` (or `EventHandler<SomeEventEventArgs>`).</span></span>  
  
- <span data-ttu-id="b0d74-154">Událost předá parametr typu `SomeEventEventArgs` obslužným rutinám události.</span><span class="sxs-lookup"><span data-stu-id="b0d74-154">The event passes a parameter of type `SomeEventEventArgs` to the event handlers.</span></span>  
  
### <a name="using-an-existing-weak-event-manager-class"></a><span data-ttu-id="b0d74-155">Použití stávající slabé třídy správce událostí</span><span class="sxs-lookup"><span data-stu-id="b0d74-155">Using an Existing Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="b0d74-156">Najděte stávajícího slabého správce událostí.</span><span class="sxs-lookup"><span data-stu-id="b0d74-156">Find an existing weak event manager.</span></span>  
  
     <span data-ttu-id="b0d74-157">Seznam slabých správců událostí, které jsou součástí WPF, najdete v tématu Hierarchie dědičnosti ve <xref:System.Windows.WeakEventManager> třídě.</span><span class="sxs-lookup"><span data-stu-id="b0d74-157">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
2. <span data-ttu-id="b0d74-158">Místo běžné události propojení použijte nový slabý správce událostí.</span><span class="sxs-lookup"><span data-stu-id="b0d74-158">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="b0d74-159">Například pokud váš kód používá následující vzor pro přihlášení k odběru události:</span><span class="sxs-lookup"><span data-stu-id="b0d74-159">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="b0d74-160">Změňte ji na následující vzor:</span><span class="sxs-lookup"><span data-stu-id="b0d74-160">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="b0d74-161">Podobně, pokud váš kód používá následující vzor k odhlášení odběru události:</span><span class="sxs-lookup"><span data-stu-id="b0d74-161">Similarly, if your code uses the following pattern to unsubscribe from an event:</span></span>  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="b0d74-162">Změňte ji na následující vzor:</span><span class="sxs-lookup"><span data-stu-id="b0d74-162">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a><span data-ttu-id="b0d74-163">Použití obecné třídy slabého správce událostí</span><span class="sxs-lookup"><span data-stu-id="b0d74-163">Using the Generic Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="b0d74-164">Místo běžné události <xref:System.Windows.WeakEventManager%602> propojení použijte obecnou třídu.</span><span class="sxs-lookup"><span data-stu-id="b0d74-164">Use the generic <xref:System.Windows.WeakEventManager%602> class instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="b0d74-165">Použijete <xref:System.Windows.WeakEventManager%602> -li k registraci posluchačů událostí, zadáváte zdroj <xref:System.EventArgs> události a typ jako parametry typu do třídy a volání <xref:System.Windows.WeakEventManager%602.AddHandler%2A> , jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="b0d74-165">When you use <xref:System.Windows.WeakEventManager%602> to register event listeners, you supply the event source and <xref:System.EventArgs> type as the type parameters to the class and call <xref:System.Windows.WeakEventManager%602.AddHandler%2A> as shown in the following code:</span></span>  
  
    ```csharp  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a><span data-ttu-id="b0d74-166">Vytvoření vlastní slabé třídy správce událostí</span><span class="sxs-lookup"><span data-stu-id="b0d74-166">Creating a Custom Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="b0d74-167">Zkopírujte následující šablonu třídy do projektu.</span><span class="sxs-lookup"><span data-stu-id="b0d74-167">Copy the following class template to your project.</span></span>  
  
     <span data-ttu-id="b0d74-168">Tato třída dědí z <xref:System.Windows.WeakEventManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="b0d74-168">This class inherits from the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2. <span data-ttu-id="b0d74-169">`SomeEventWeakEventManager` Název nahraďte vlastním názvem.</span><span class="sxs-lookup"><span data-stu-id="b0d74-169">Replace the `SomeEventWeakEventManager` name with your own name.</span></span>  
  
3. <span data-ttu-id="b0d74-170">Nahraďte tři výše popsané názvy odpovídajícími názvy pro vaši událost.</span><span class="sxs-lookup"><span data-stu-id="b0d74-170">Replace the three names described previously with the corresponding names for your event.</span></span> <span data-ttu-id="b0d74-171">(`SomeEvent`, `EventSource`, a `SomeEventEventArgs`)</span><span class="sxs-lookup"><span data-stu-id="b0d74-171">(`SomeEvent`, `EventSource`, and `SomeEventEventArgs`)</span></span>  
  
4. <span data-ttu-id="b0d74-172">Nastavte viditelnost (veřejná/interní/privátní) třídy slabého správce událostí na stejnou viditelnost jako událost, kterou spravuje.</span><span class="sxs-lookup"><span data-stu-id="b0d74-172">Set the visibility (public / internal / private) of the weak event manager class to the same visibility as event it manages.</span></span>  
  
5. <span data-ttu-id="b0d74-173">Místo běžné události propojení použijte nový slabý správce událostí.</span><span class="sxs-lookup"><span data-stu-id="b0d74-173">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="b0d74-174">Například pokud váš kód používá následující vzor pro přihlášení k odběru události:</span><span class="sxs-lookup"><span data-stu-id="b0d74-174">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="b0d74-175">Změňte ji na následující vzor:</span><span class="sxs-lookup"><span data-stu-id="b0d74-175">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="b0d74-176">Podobně, pokud váš kód používá následující vzor k odhlášení odběru události:</span><span class="sxs-lookup"><span data-stu-id="b0d74-176">Similarly, if your code uses the following pattern to unsubscribe to an event:</span></span>  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     <span data-ttu-id="b0d74-177">Změňte ji na následující vzor:</span><span class="sxs-lookup"><span data-stu-id="b0d74-177">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b0d74-178">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0d74-178">See also</span></span>

- <xref:System.Windows.WeakEventManager>
- <xref:System.Windows.IWeakEventListener>
- [<span data-ttu-id="b0d74-179">Přehled směrovaných událostí</span><span class="sxs-lookup"><span data-stu-id="b0d74-179">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="b0d74-180">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="b0d74-180">Data Binding Overview</span></span>](../data/data-binding-overview.md)
