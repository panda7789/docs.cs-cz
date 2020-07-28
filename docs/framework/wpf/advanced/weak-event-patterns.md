---
title: Slabý vzor událostí
description: Přečtěte si o vzorech slabé události Windows Presentation Foundation, který řeší problémy s obslužnými rutinami, které nejsou zničeny, a vyloučí nevracení paměti.
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: 75c6888c8ac20c41d13e3787005377c75248c5d9
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168261"
---
# <a name="weak-event-patterns"></a><span data-ttu-id="9870e-103">Slabý vzor událostí</span><span class="sxs-lookup"><span data-stu-id="9870e-103">Weak Event Patterns</span></span>
<span data-ttu-id="9870e-104">V aplikacích je možné, že obslužné rutiny, které jsou připojeny ke zdrojům událostí, nebudou zničeny v koordinaci s objektem naslouchacího procesu, který připojil obslužnou rutinu ke zdroji.</span><span class="sxs-lookup"><span data-stu-id="9870e-104">In applications, it is possible that handlers that are attached to event sources will not be destroyed in coordination with the listener object that attached the handler to the source.</span></span> <span data-ttu-id="9870e-105">Tato situace může vést k nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="9870e-105">This situation can lead to memory leaks.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="9870e-106">zavádí vzor návrhu, který lze použít k vyřešení tohoto problému, poskytnutím vyhrazené třídy správce pro konkrétní události a implementací rozhraní na naslouchací proces pro danou událost.</span><span class="sxs-lookup"><span data-stu-id="9870e-106">introduces a design pattern that can be used to address this issue, by providing a dedicated manager class for particular events and implementing an interface on listeners for that event.</span></span> <span data-ttu-id="9870e-107">Tento vzor návrhu je známý jako *slabý vzorek události*.</span><span class="sxs-lookup"><span data-stu-id="9870e-107">This design pattern is known as the *weak event pattern*.</span></span>  
  
## <a name="why-implement-the-weak-event-pattern"></a><span data-ttu-id="9870e-108">Proč implementovat slabý vzorek události?</span><span class="sxs-lookup"><span data-stu-id="9870e-108">Why Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="9870e-109">Poslouchání událostí může vést k nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="9870e-109">Listening for events can lead to memory leaks.</span></span> <span data-ttu-id="9870e-110">Typická technika pro naslouchání události je použít syntaxi specifickou pro jazyk, která připojí obslužnou rutinu k události ve zdroji.</span><span class="sxs-lookup"><span data-stu-id="9870e-110">The typical technique for listening to an event is to use the language-specific syntax that attaches a handler to an event on a source.</span></span> <span data-ttu-id="9870e-111">Například v jazyce C# je tato syntaxe: `source.SomeEvent += new SomeEventHandler(MyEventHandler)` .</span><span class="sxs-lookup"><span data-stu-id="9870e-111">For example, in C#, that syntax is: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span></span>  
  
 <span data-ttu-id="9870e-112">Tato technika vytvoří silný odkaz ze zdroje události na naslouchací proces událostí.</span><span class="sxs-lookup"><span data-stu-id="9870e-112">This technique creates a strong reference from the event source to the event listener.</span></span> <span data-ttu-id="9870e-113">Obvykle připojení obslužné rutiny události pro naslouchací proces způsobí, že naslouchací proces bude mít životnost objektu, která je ovlivněna životností objektu zdroje (Pokud není obslužná rutina události explicitně odebrána).</span><span class="sxs-lookup"><span data-stu-id="9870e-113">Ordinarily, attaching an event handler for a listener causes the listener to have an object lifetime that is influenced by the object lifetime of the source (unless the event handler is explicitly removed).</span></span> <span data-ttu-id="9870e-114">V některých případech však můžete chtít, aby životnost objektu naslouchacího procesu byla kontrolována jinými faktory, například zda aktuálně patří do vizuálního stromu aplikace, a nikoli po dobu života zdroje.</span><span class="sxs-lookup"><span data-stu-id="9870e-114">But in certain circumstances, you might want the object lifetime of the listener to be controlled by other factors, such as whether it currently belongs to the visual tree of the application, and not by the lifetime of the source.</span></span> <span data-ttu-id="9870e-115">Pokaždé, když životnost zdrojového objektu přesáhne dobu životnosti objektu naslouchacího procesu, vzorek normální události vede k nevrácení paměti: naslouchací proces je udržován v provozu déle, než je určeno.</span><span class="sxs-lookup"><span data-stu-id="9870e-115">Whenever the source object lifetime extends beyond the object lifetime of the listener, the normal event pattern leads to a memory leak: the listener is kept alive longer than intended.</span></span>  
  
 <span data-ttu-id="9870e-116">Slabý vzorek události je navržen pro vyřešení problému při nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="9870e-116">The weak event pattern is designed to solve this memory leak problem.</span></span> <span data-ttu-id="9870e-117">Slabý vzorek události lze použít vždy, když se naslouchací proces potřebuje zaregistrovat pro událost, ale naslouchací proces výslovně neví, kdy zrušit registraci.</span><span class="sxs-lookup"><span data-stu-id="9870e-117">The weak event pattern can be used whenever a listener needs to register for an event, but the listener does not explicitly know when to unregister.</span></span> <span data-ttu-id="9870e-118">Slabý vzorek události lze také použít vždy, když životnost objektu zdroje překračuje užitečnou životnost objektu naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="9870e-118">The weak event pattern can also be used whenever the object lifetime of the source exceeds the useful object lifetime of the listener.</span></span> <span data-ttu-id="9870e-119">(V takovém případě je to *užitečné* , je určeno vámi.) Slabý vzorek události umožňuje naslouchací proces registrovat a přijímat události, aniž by to ovlivnilo vlastnosti životnosti objektu naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="9870e-119">(In this case, *useful* is determined by you.) The weak event pattern allows the listener to register for and receive the event without affecting the object lifetime characteristics of the listener in any way.</span></span> <span data-ttu-id="9870e-120">V podstatě implicitní odkaz ze zdroje neurčuje, zda má naslouchací proces nárok na uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9870e-120">In effect, the implied reference from the source does not determine whether the listener is eligible for garbage collection.</span></span> <span data-ttu-id="9870e-121">Odkaz je slabý odkaz, takže pojmenováváme slabý vzorek události a související rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="9870e-121">The reference is a weak reference, thus the naming of the weak event pattern and the related APIs.</span></span> <span data-ttu-id="9870e-122">Naslouchací proces může být shromážděn z paměti nebo jinak zničen a zdroj může pokračovat bez uchování odkazů obslužných rutin utvořit na objekt, který je nyní zničen.</span><span class="sxs-lookup"><span data-stu-id="9870e-122">The listener can be garbage collected or otherwise destroyed, and the source can continue without retaining noncollectible handler references to a now destroyed object.</span></span>  
  
## <a name="who-should-implement-the-weak-event-pattern"></a><span data-ttu-id="9870e-123">Kdo má implementovat slabý vzorek události?</span><span class="sxs-lookup"><span data-stu-id="9870e-123">Who Should Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="9870e-124">Implementace slabého vzoru události je zajímavá hlavně pro autory ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="9870e-124">Implementing the weak event pattern is interesting primarily for control authors.</span></span> <span data-ttu-id="9870e-125">Jako autor ovládacího prvku je převážně zodpovědný za chování a omezení vašeho řízení a vliv na aplikace, do kterých je vložen.</span><span class="sxs-lookup"><span data-stu-id="9870e-125">As a control author, you are largely responsible for the behavior and containment of your control and the impact it has on applications in which it is inserted.</span></span> <span data-ttu-id="9870e-126">To zahrnuje chování při životnosti řídicích objektů, zejména zpracování popsaného problému při nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="9870e-126">This includes the control object lifetime behavior, in particular the handling of the described memory leak problem.</span></span>  
  
 <span data-ttu-id="9870e-127">Některé scénáře jsou z vlastního podstaty zapůjčení do aplikace slabého vzoru události.</span><span class="sxs-lookup"><span data-stu-id="9870e-127">Certain scenarios inherently lend themselves to the application of the weak event pattern.</span></span> <span data-ttu-id="9870e-128">Jedním z takových scénářů je vázání dat.</span><span class="sxs-lookup"><span data-stu-id="9870e-128">One such scenario is data binding.</span></span> <span data-ttu-id="9870e-129">V datové vazbě je běžné, že zdrojový objekt je zcela nezávislý na objektu naslouchacího procesu, který je cílem vazby.</span><span class="sxs-lookup"><span data-stu-id="9870e-129">In data binding, it is common for the source object to be completely independent of the listener object, which is a target of a binding.</span></span> <span data-ttu-id="9870e-130">Mnoho aspektů [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] datové vazby už má slabý vzor událostí, který se používá při implementaci událostí.</span><span class="sxs-lookup"><span data-stu-id="9870e-130">Many aspects of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] data binding already have the weak event pattern applied in how the events are implemented.</span></span>  
  
## <a name="how-to-implement-the-weak-event-pattern"></a><span data-ttu-id="9870e-131">Jak implementovat slabý vzorek události</span><span class="sxs-lookup"><span data-stu-id="9870e-131">How to Implement the Weak Event Pattern</span></span>  
 <span data-ttu-id="9870e-132">Existují tři způsoby, jak implementovat slabý vzorek události.</span><span class="sxs-lookup"><span data-stu-id="9870e-132">There are three ways to implement weak event pattern.</span></span> <span data-ttu-id="9870e-133">Následující tabulka uvádí tři přístupy a poskytuje pokyny pro použití každého z nich.</span><span class="sxs-lookup"><span data-stu-id="9870e-133">The following table lists the three approaches and provides some guidance for when you should use each.</span></span>  
  
|<span data-ttu-id="9870e-134">Přístup</span><span class="sxs-lookup"><span data-stu-id="9870e-134">Approach</span></span>|<span data-ttu-id="9870e-135">Kdy implementovat</span><span class="sxs-lookup"><span data-stu-id="9870e-135">When to Implement</span></span>|  
|--------------|-----------------------|  
|<span data-ttu-id="9870e-136">Použít stávající slabší třídu správce událostí</span><span class="sxs-lookup"><span data-stu-id="9870e-136">Use an existing weak event manager class</span></span>|<span data-ttu-id="9870e-137">Pokud má událost, které se má přihlásit k odběru <xref:System.Windows.WeakEventManager> , odpovídající, použijte stávající správce slabé události.</span><span class="sxs-lookup"><span data-stu-id="9870e-137">If the event you want to subscribe to has a corresponding <xref:System.Windows.WeakEventManager>, use the existing weak event manager.</span></span> <span data-ttu-id="9870e-138">Seznam slabých správců událostí, které jsou součástí WPF, najdete v tématu Hierarchie dědičnosti ve <xref:System.Windows.WeakEventManager> třídě.</span><span class="sxs-lookup"><span data-stu-id="9870e-138">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span> <span data-ttu-id="9870e-139">Vzhledem k tomu, že jsou zahrnuté slabé správce událostí omezené, budete pravděpodobně muset zvolit jeden z dalších přístupů.</span><span class="sxs-lookup"><span data-stu-id="9870e-139">Because the included weak event managers are limited, you will probably need to choose one of the other approaches.</span></span>|  
|<span data-ttu-id="9870e-140">Použití obecné třídy slabého správce událostí</span><span class="sxs-lookup"><span data-stu-id="9870e-140">Use a generic weak event manager class</span></span>|<span data-ttu-id="9870e-141">Použijte obecné <xref:System.Windows.WeakEventManager%602> , pokud není <xref:System.Windows.WeakEventManager> k dispozici existující, chcete snadno implementovat a nebudete mít obavy o efektivitu.</span><span class="sxs-lookup"><span data-stu-id="9870e-141">Use a generic <xref:System.Windows.WeakEventManager%602> when an existing <xref:System.Windows.WeakEventManager> is not available, you want an easy way to implement, and you are not concerned about efficiency.</span></span> <span data-ttu-id="9870e-142">Obecný <xref:System.Windows.WeakEventManager%602> je méně efektivní než stávající nebo vlastní slabý správce událostí.</span><span class="sxs-lookup"><span data-stu-id="9870e-142">The generic <xref:System.Windows.WeakEventManager%602> is less efficient than an existing or custom weak event manager.</span></span> <span data-ttu-id="9870e-143">Například obecná třída má větší odraz pro zjištění události s ohledem na název události.</span><span class="sxs-lookup"><span data-stu-id="9870e-143">For example, the generic class does more reflection to discover the event given the event's name.</span></span> <span data-ttu-id="9870e-144">Také kód pro registraci události pomocí obecného <xref:System.Windows.WeakEventManager%602> je podrobnější než použití existující nebo vlastní <xref:System.Windows.WeakEventManager> .</span><span class="sxs-lookup"><span data-stu-id="9870e-144">Also, the code to register the event by using the generic <xref:System.Windows.WeakEventManager%602> is more verbose than using an existing or custom <xref:System.Windows.WeakEventManager>.</span></span>|  
|<span data-ttu-id="9870e-145">Vytvoření vlastní slabé třídy správce událostí</span><span class="sxs-lookup"><span data-stu-id="9870e-145">Create a custom weak event manager class</span></span>|<span data-ttu-id="9870e-146"><xref:System.Windows.WeakEventManager>Pokud není <xref:System.Windows.WeakEventManager> k dispozici existující a chcete nejlepší efektivitu, vytvořte vlastní.</span><span class="sxs-lookup"><span data-stu-id="9870e-146">Create a custom <xref:System.Windows.WeakEventManager> when an existing <xref:System.Windows.WeakEventManager> is not available and you want the best efficiency.</span></span> <span data-ttu-id="9870e-147">Použití vlastního <xref:System.Windows.WeakEventManager> přihlášení k odběru události bude efektivnější, ale náklady na zápis dalších kódů na začátku se účtují.</span><span class="sxs-lookup"><span data-stu-id="9870e-147">Using a custom <xref:System.Windows.WeakEventManager> to subscribe to an event will be more efficient, but you do incur the cost of writing more code at the beginning.</span></span>|  
|<span data-ttu-id="9870e-148">Použití slabého správce událostí třetí strany</span><span class="sxs-lookup"><span data-stu-id="9870e-148">Use a third-party weak event manager</span></span>|<span data-ttu-id="9870e-149">NuGet má [několik slabých správců událostí](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) a řada platforem WPF také podporuje vzor (například [dokumentaci Prism o volně vázaných odběrech událostí](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/legacy/Communication.md#subscribing-to-events)).</span><span class="sxs-lookup"><span data-stu-id="9870e-149">NuGet has [several weak event managers](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) and many WPF frameworks also support the pattern (for instance, see [Prism's documentation on loosely coupled event subscription](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/legacy/Communication.md#subscribing-to-events)).</span></span>|

 <span data-ttu-id="9870e-150">Následující části popisují, jak implementovat slabý vzorek události.</span><span class="sxs-lookup"><span data-stu-id="9870e-150">The following sections describe how to implement the weak event pattern.</span></span>  <span data-ttu-id="9870e-151">Pro účely této diskuze má událost pro přihlášení k odběru následující charakteristiky.</span><span class="sxs-lookup"><span data-stu-id="9870e-151">For purposes of this discussion, the event to subscribe to has the following characteristics.</span></span>  
  
- <span data-ttu-id="9870e-152">Název události je `SomeEvent` .</span><span class="sxs-lookup"><span data-stu-id="9870e-152">The event name is `SomeEvent`.</span></span>  
  
- <span data-ttu-id="9870e-153">Událost je vyvolána `EventSource` třídou.</span><span class="sxs-lookup"><span data-stu-id="9870e-153">The event is raised by the `EventSource` class.</span></span>  
  
- <span data-ttu-id="9870e-154">Obslužná rutina události je typu: `SomeEventEventHandler` (nebo `EventHandler<SomeEventEventArgs>` ).</span><span class="sxs-lookup"><span data-stu-id="9870e-154">The event handler has type: `SomeEventEventHandler` (or `EventHandler<SomeEventEventArgs>`).</span></span>  
  
- <span data-ttu-id="9870e-155">Událost předá parametr typu `SomeEventEventArgs` obslužným rutinám události.</span><span class="sxs-lookup"><span data-stu-id="9870e-155">The event passes a parameter of type `SomeEventEventArgs` to the event handlers.</span></span>  
  
### <a name="using-an-existing-weak-event-manager-class"></a><span data-ttu-id="9870e-156">Použití stávající slabé třídy správce událostí</span><span class="sxs-lookup"><span data-stu-id="9870e-156">Using an Existing Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="9870e-157">Najděte stávajícího slabého správce událostí.</span><span class="sxs-lookup"><span data-stu-id="9870e-157">Find an existing weak event manager.</span></span>  
  
     <span data-ttu-id="9870e-158">Seznam slabých správců událostí, které jsou součástí WPF, najdete v tématu Hierarchie dědičnosti ve <xref:System.Windows.WeakEventManager> třídě.</span><span class="sxs-lookup"><span data-stu-id="9870e-158">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
2. <span data-ttu-id="9870e-159">Místo běžné události propojení použijte nový slabý správce událostí.</span><span class="sxs-lookup"><span data-stu-id="9870e-159">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="9870e-160">Například pokud váš kód používá následující vzor pro přihlášení k odběru události:</span><span class="sxs-lookup"><span data-stu-id="9870e-160">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="9870e-161">Změňte ji na následující vzor:</span><span class="sxs-lookup"><span data-stu-id="9870e-161">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="9870e-162">Podobně, pokud váš kód používá následující vzor k odhlášení odběru události:</span><span class="sxs-lookup"><span data-stu-id="9870e-162">Similarly, if your code uses the following pattern to unsubscribe from an event:</span></span>  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="9870e-163">Změňte ji na následující vzor:</span><span class="sxs-lookup"><span data-stu-id="9870e-163">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a><span data-ttu-id="9870e-164">Použití obecné třídy slabého správce událostí</span><span class="sxs-lookup"><span data-stu-id="9870e-164">Using the Generic Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="9870e-165"><xref:System.Windows.WeakEventManager%602>Místo běžné události propojení použijte obecnou třídu.</span><span class="sxs-lookup"><span data-stu-id="9870e-165">Use the generic <xref:System.Windows.WeakEventManager%602> class instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="9870e-166">Použijete <xref:System.Windows.WeakEventManager%602> -li k registraci posluchačů událostí, zadáváte zdroj události a <xref:System.EventArgs> typ jako parametry typu do třídy a volání <xref:System.Windows.WeakEventManager%602.AddHandler%2A> , jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="9870e-166">When you use <xref:System.Windows.WeakEventManager%602> to register event listeners, you supply the event source and <xref:System.EventArgs> type as the type parameters to the class and call <xref:System.Windows.WeakEventManager%602.AddHandler%2A> as shown in the following code:</span></span>  
  
    ```csharp  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a><span data-ttu-id="9870e-167">Vytvoření vlastní slabé třídy správce událostí</span><span class="sxs-lookup"><span data-stu-id="9870e-167">Creating a Custom Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="9870e-168">Zkopírujte následující šablonu třídy do projektu.</span><span class="sxs-lookup"><span data-stu-id="9870e-168">Copy the following class template to your project.</span></span>  
  
     <span data-ttu-id="9870e-169">Tato třída dědí z <xref:System.Windows.WeakEventManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="9870e-169">This class inherits from the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2. <span data-ttu-id="9870e-170">Název nahraďte `SomeEventWeakEventManager` vlastním názvem.</span><span class="sxs-lookup"><span data-stu-id="9870e-170">Replace the `SomeEventWeakEventManager` name with your own name.</span></span>  
  
3. <span data-ttu-id="9870e-171">Nahraďte tři výše popsané názvy odpovídajícími názvy pro vaši událost.</span><span class="sxs-lookup"><span data-stu-id="9870e-171">Replace the three names described previously with the corresponding names for your event.</span></span> <span data-ttu-id="9870e-172">( `SomeEvent` , `EventSource` , a `SomeEventEventArgs` )</span><span class="sxs-lookup"><span data-stu-id="9870e-172">(`SomeEvent`, `EventSource`, and `SomeEventEventArgs`)</span></span>  
  
4. <span data-ttu-id="9870e-173">Nastavte viditelnost (veřejná/interní/privátní) třídy slabého správce událostí na stejnou viditelnost jako událost, kterou spravuje.</span><span class="sxs-lookup"><span data-stu-id="9870e-173">Set the visibility (public / internal / private) of the weak event manager class to the same visibility as event it manages.</span></span>  
  
5. <span data-ttu-id="9870e-174">Místo běžné události propojení použijte nový slabý správce událostí.</span><span class="sxs-lookup"><span data-stu-id="9870e-174">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="9870e-175">Například pokud váš kód používá následující vzor pro přihlášení k odběru události:</span><span class="sxs-lookup"><span data-stu-id="9870e-175">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="9870e-176">Změňte ji na následující vzor:</span><span class="sxs-lookup"><span data-stu-id="9870e-176">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="9870e-177">Podobně, pokud váš kód používá následující vzor k odhlášení odběru události:</span><span class="sxs-lookup"><span data-stu-id="9870e-177">Similarly, if your code uses the following pattern to unsubscribe to an event:</span></span>  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     <span data-ttu-id="9870e-178">Změňte ji na následující vzor:</span><span class="sxs-lookup"><span data-stu-id="9870e-178">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9870e-179">Viz také</span><span class="sxs-lookup"><span data-stu-id="9870e-179">See also</span></span>

- <xref:System.Windows.WeakEventManager>
- <xref:System.Windows.IWeakEventListener>
- [<span data-ttu-id="9870e-180">Přehled směrovaných událostí</span><span class="sxs-lookup"><span data-stu-id="9870e-180">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="9870e-181">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="9870e-181">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
