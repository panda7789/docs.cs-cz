---
title: "Slabý vzor událostí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3f024ae77740c596d8646b10a036428e2342d084
ms.sourcegitcommit: 8ed4ebc15b5ef89d06a7507dc9d5e306e30accf7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/14/2017
---
# <a name="weak-event-patterns"></a><span data-ttu-id="4c4a5-102">Slabý vzor událostí</span><span class="sxs-lookup"><span data-stu-id="4c4a5-102">Weak Event Patterns</span></span>
<span data-ttu-id="4c4a5-103">V aplikacích je možné, že obslužné rutiny, které jsou připojené k zdroje událostí nebude v koordinaci s objektem naslouchací proces, který obslužná rutina připojen ke zdroji.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-103">In applications, it is possible that handlers that are attached to event sources will not be destroyed in coordination with the listener object that attached the handler to the source.</span></span> <span data-ttu-id="4c4a5-104">Tato situace může vést k nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-104">This situation can lead to memory leaks.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="4c4a5-105">představuje návrhový vzor, který lze tento problém vyřešit pomocí vyhrazené manager třídu pro konkrétní události a implementace rozhraní na naslouchací procesy pro tuto událost.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-105"> introduces a design pattern that can be used to address this issue, by providing a dedicated manager class for particular events and implementing an interface on listeners for that event.</span></span> <span data-ttu-id="4c4a5-106">Tento vzor návrhu se označuje jako *slabé událostí vzor*.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-106">This design pattern is known as the *weak event pattern*.</span></span>  
  
## <a name="why-implement-the-weak-event-pattern"></a><span data-ttu-id="4c4a5-107">Proč implementovat vzor slabé událostí?</span><span class="sxs-lookup"><span data-stu-id="4c4a5-107">Why Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="4c4a5-108">Naslouchání událostem může vést k nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-108">Listening for events can lead to memory leaks.</span></span> <span data-ttu-id="4c4a5-109">Typické technika pro naslouchání na událost, je použití syntaxe pro specifický jazyk, který připojí obslužnou rutinu pro událost ve zdroji.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-109">The typical technique for listening to an event is to use the language-specific syntax that attaches a handler to an event on a source.</span></span> <span data-ttu-id="4c4a5-110">Například v [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)], že syntaxe je: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-110">For example, in [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)], that syntax is: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span></span>  
  
 <span data-ttu-id="4c4a5-111">Tento postup vytvoří silné odkaz ze zdroje událostí pro událost naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-111">This technique creates a strong reference from the event source to the event listener.</span></span> <span data-ttu-id="4c4a5-112">Obvykle je připojení obslužné rutiny události pro naslouchací proces způsobí, že naslouchací proces má doba života objektu, který je ovlivněno doba života objektu zdroje (Pokud je výslovně odebrali obslužné rutiny události).</span><span class="sxs-lookup"><span data-stu-id="4c4a5-112">Ordinarily, attaching an event handler for a listener causes the listener to have an object lifetime that is influenced by the object lifetime of the source (unless the event handler is explicitly removed).</span></span> <span data-ttu-id="4c4a5-113">Ale v některých případech můžete doba života objektu z naslouchacího procesu kontrolován dalších faktorech, například zda aktuálně patří vizuálním stromu aplikace a ne serverem životnost zdroje.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-113">But in certain circumstances, you might want the object lifetime of the listener to be controlled by other factors, such as whether it currently belongs to the visual tree of the application, and not by the lifetime of the source.</span></span> <span data-ttu-id="4c4a5-114">Vždy, když doba života objektu zdroj přesahuje doba života objektu naslouchacího procesu, vzoru normálního událostí vede k nevrácenou pamětí: naslouchací proces je udržováno zachování delší než určená.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-114">Whenever the source object lifetime extends beyond the object lifetime of the listener, the normal event pattern leads to a memory leak: the listener is kept alive longer than intended.</span></span>  
  
 <span data-ttu-id="4c4a5-115">Vzor slabé událostí slouží k vyřešení tohoto problému nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-115">The weak event pattern is designed to solve this memory leak problem.</span></span> <span data-ttu-id="4c4a5-116">Vzor slabé události lze vždy, když potřebuje naslouchací proces registrace pro událost, avšak naslouchací proces nebude vědět explicitně při zrušení registrace.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-116">The weak event pattern can be used whenever a listener needs to register for an event, but the listener does not explicitly know when to unregister.</span></span> <span data-ttu-id="4c4a5-117">Vzor slabé události mohou sloužit také vždy, když doba života objektu zdroje překračuje doba života užitečné objektu naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-117">The weak event pattern can also be used whenever the object lifetime of the source exceeds the useful object lifetime of the listener.</span></span> <span data-ttu-id="4c4a5-118">(V tomto případě *užitečné* je dáno jste.) Vzor slabé událostí umožňuje naslouchací proces se registrovat a přijímat události bez ovlivnění charakteristiky doba života objektu naslouchací proces žádným způsobem.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-118">(In this case, *useful* is determined by you.) The weak event pattern allows the listener to register for and receive the event without affecting the object lifetime characteristics of the listener in any way.</span></span> <span data-ttu-id="4c4a5-119">Ve skutečnosti implicitní odkaz ze zdroje není určit, zda naslouchací proces je vhodné pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-119">In effect, the implied reference from the source does not determine whether the listener is eligible for garbage collection.</span></span> <span data-ttu-id="4c4a5-120">Odkaz je slabé odkaz, proto pojmenování vzoru slabé události a související [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4c4a5-120">The reference is a weak reference, thus the naming of the weak event pattern and the related [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)].</span></span> <span data-ttu-id="4c4a5-121">Naslouchací proces může být paměti shromážděných nebo jinak zničeno a zdroj můžete pokračovat bez zachování noncollectible obslužná rutina odkazy na objekt nyní zničení.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-121">The listener can be garbage collected or otherwise destroyed, and the source can continue without retaining noncollectible handler references to a now destroyed object.</span></span>  
  
## <a name="who-should-implement-the-weak-event-pattern"></a><span data-ttu-id="4c4a5-122">Kdo by měla implementovat vzor slabé událostí?</span><span class="sxs-lookup"><span data-stu-id="4c4a5-122">Who Should Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="4c4a5-123">Implementace vzoru slabé událostí je zajímavé hlavně pro autory ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-123">Implementing the weak event pattern is interesting primarily for control authors.</span></span> <span data-ttu-id="4c4a5-124">Jako autor ovládací prvek je z velké části zodpovědná chování a členství ve skupině ovládacího prvku a dopad, který má v aplikacích, ve kterých je vložen.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-124">As a control author, you are largely responsible for the behavior and containment of your control and the impact it has on applications in which it is inserted.</span></span> <span data-ttu-id="4c4a5-125">To zahrnuje řídit chování doba života objektu, zejména zpracování problému úniku popsané paměti.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-125">This includes the control object lifetime behavior, in particular the handling of the described memory leak problem.</span></span>  
  
 <span data-ttu-id="4c4a5-126">Některé scénáře ze své podstaty samo o vzoru slabé událostí aplikace.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-126">Certain scenarios inherently lend themselves to the application of the weak event pattern.</span></span> <span data-ttu-id="4c4a5-127">Jeden takový scénář se datová vazba.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-127">One such scenario is data binding.</span></span> <span data-ttu-id="4c4a5-128">V datové vazby, je běžné zdroje objekt, který má být zcela nezávislé na objekt naslouchací proces, který je cílem vazbu.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-128">In data binding, it is common for the source object to be completely independent of the listener object, which is a target of a binding.</span></span> <span data-ttu-id="4c4a5-129">Mnoho aspektů [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] datové vazby již mít vzoru slabé událostí použité v tom, jak jsou implementované události.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-129">Many aspects of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] data binding already have the weak event pattern applied in how the events are implemented.</span></span>  
  
## <a name="how-to-implement-the-weak-event-pattern"></a><span data-ttu-id="4c4a5-130">Implementace vzoru slabé událostí</span><span class="sxs-lookup"><span data-stu-id="4c4a5-130">How to Implement the Weak Event Pattern</span></span>  
 <span data-ttu-id="4c4a5-131">Existují tři způsoby, jak implementovat vzor slabé událostí.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-131">There are three ways to implement weak event pattern.</span></span> <span data-ttu-id="4c4a5-132">Následující tabulka uvádí se třemi způsoby a nabízí některé pokyny, když každý měli použít.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-132">The following table lists the three approaches and provides some guidance for when you should use each.</span></span>  
  
|<span data-ttu-id="4c4a5-133">Přístup</span><span class="sxs-lookup"><span data-stu-id="4c4a5-133">Approach</span></span>|<span data-ttu-id="4c4a5-134">Kdy implementovat</span><span class="sxs-lookup"><span data-stu-id="4c4a5-134">When to Implement</span></span>|  
|--------------|-----------------------|  
|<span data-ttu-id="4c4a5-135">Použít existující třídu manager slabé události</span><span class="sxs-lookup"><span data-stu-id="4c4a5-135">Use an existing weak event manager class</span></span>|<span data-ttu-id="4c4a5-136">Pokud se chcete přihlásit k odběru události má odpovídající <xref:System.Windows.WeakEventManager>, použijte existující správce slabé událostí.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-136">If the event you want to subscribe to has a corresponding <xref:System.Windows.WeakEventManager>, use the existing weak event manager.</span></span> <span data-ttu-id="4c4a5-137">Seznam manažerů slabé událostí, které jsou součástí WPF najdete v tématu v hierarchii dědičnosti <xref:System.Windows.WeakEventManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-137">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span> <span data-ttu-id="4c4a5-138">Upozorňujeme však, že jsou poměrně málo správci slabé událostí, které jsou součástí WPF, takže budete pravděpodobně muset vyberte jednu z dalších přístupy.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-138">Note, however, that there are relatively few weak event managers that are included with WPF, so you will probably need to choose one of the other approaches.</span></span>|  
|<span data-ttu-id="4c4a5-139">Použití třídy manager obecné slabé událostí</span><span class="sxs-lookup"><span data-stu-id="4c4a5-139">Use a generic weak event manager class</span></span>|<span data-ttu-id="4c4a5-140">Použít obecný <xref:System.Windows.WeakEventManager%602> pokud stávající <xref:System.Windows.WeakEventManager> má není k dispozici, má snadný způsob, jak implementovat a nemáte zájem o efektivitu.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-140">Use a generic <xref:System.Windows.WeakEventManager%602> when an existing <xref:System.Windows.WeakEventManager> is not available, you want an easy way to implement, and you are not concerned about efficiency.</span></span> <span data-ttu-id="4c4a5-141">Obecná <xref:System.Windows.WeakEventManager%602> sice méně efektivní než existující nebo vlastní správce slabé událostí.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-141">The generic <xref:System.Windows.WeakEventManager%602> is less efficient than an existing or custom weak event manager.</span></span> <span data-ttu-id="4c4a5-142">Například obecná třída nepodporuje více reflexe ke zjištění události název události.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-142">For example, the generic class does more reflection to discover the event given the event's name.</span></span> <span data-ttu-id="4c4a5-143">Navíc kód k registraci události pomocí Obecné <xref:System.Windows.WeakEventManager%602> více podrobné než při použití existující nebo vlastní <xref:System.Windows.WeakEventManager>.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-143">Also, the code to register the event by using the generic <xref:System.Windows.WeakEventManager%602> is more verbose than using an existing or custom <xref:System.Windows.WeakEventManager>.</span></span>|  
|<span data-ttu-id="4c4a5-144">Vytvoření třídy manager vlastní slabé událostí</span><span class="sxs-lookup"><span data-stu-id="4c4a5-144">Create a custom weak event manager class</span></span>|<span data-ttu-id="4c4a5-145">Vytvoření vlastní <xref:System.Windows.WeakEventManager> pokud stávající <xref:System.Windows.WeakEventManager> není k dispozici, a chcete nejlepšího výkonu.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-145">Create a custom <xref:System.Windows.WeakEventManager> when an existing <xref:System.Windows.WeakEventManager> is not available and you want the best efficiency.</span></span> <span data-ttu-id="4c4a5-146">Použití vlastní <xref:System.Windows.WeakEventManager> přihlásit k odběru události bude efektivnější, ale způsobit náklady na zápis další kód na začátku.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-146">Using a custom <xref:System.Windows.WeakEventManager> to subscribe to an event will be more efficient, but you do incur the cost of writing more code at the beginning.</span></span>|  
  
 <span data-ttu-id="4c4a5-147">Následující části popisují, jak implementovat vzor slabé událostí.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-147">The following sections describe how to implement the weak event pattern.</span></span>  <span data-ttu-id="4c4a5-148">Pro účely Tato diskuse se přihlásit k odběru události má následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-148">For purposes of this discussion, the event to subscribe to has the following characteristics.</span></span>  
  
-   <span data-ttu-id="4c4a5-149">Název události je `SomeEvent`.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-149">The event name is `SomeEvent`.</span></span>  
  
-   <span data-ttu-id="4c4a5-150">Událost se vyvolá, pomocí `EventSource` třídy.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-150">The event is raised by the `EventSource` class.</span></span>  
  
-   <span data-ttu-id="4c4a5-151">Obslužné rutiny události má typ: `SomeEventEventHandler` (nebo `EventHandler<SomeEventEventArgs>`).</span><span class="sxs-lookup"><span data-stu-id="4c4a5-151">The event handler has type: `SomeEventEventHandler` (or `EventHandler<SomeEventEventArgs>`).</span></span>  
  
-   <span data-ttu-id="4c4a5-152">Událost předá parametr typu `SomeEventEventArgs` do obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-152">The event passes a parameter of type `SomeEventEventArgs` to the event handlers.</span></span>  
  
### <a name="using-an-existing-weak-event-manager-class"></a><span data-ttu-id="4c4a5-153">Použití existující třídy slabé správce událostí</span><span class="sxs-lookup"><span data-stu-id="4c4a5-153">Using an Existing Weak Event Manager Class</span></span>  
  
1.  <span data-ttu-id="4c4a5-154">Najdete existující slabé událost správce.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-154">Find an existing weak event manager.</span></span>  
  
     <span data-ttu-id="4c4a5-155">Seznam manažerů slabé událostí, které jsou součástí WPF najdete v tématu v hierarchii dědičnosti <xref:System.Windows.WeakEventManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-155">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
2.  <span data-ttu-id="4c4a5-156">Pomocí nového správce slabé událostí místo normální událostí spojení.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-156">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="4c4a5-157">Pokud například váš kód používá následující vzorec k odběru události:</span><span class="sxs-lookup"><span data-stu-id="4c4a5-157">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="4c4a5-158">Změňte jej na vzoru následující:</span><span class="sxs-lookup"><span data-stu-id="4c4a5-158">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="4c4a5-159">Podobně pokud kód používá následující vzor k odhlášení odběru na událost:</span><span class="sxs-lookup"><span data-stu-id="4c4a5-159">Similarly, if your code uses the following pattern to unsubscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     <span data-ttu-id="4c4a5-160">Změňte jej na vzoru následující:</span><span class="sxs-lookup"><span data-stu-id="4c4a5-160">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a><span data-ttu-id="4c4a5-161">Použití obecné třídy slabé správce událostí</span><span class="sxs-lookup"><span data-stu-id="4c4a5-161">Using the Generic Weak Event Manager Class</span></span>  
  
1.  <span data-ttu-id="4c4a5-162">Používat obecná <xref:System.Windows.WeakEventManager%602> třída místo normální událostí spojení.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-162">Use the generic <xref:System.Windows.WeakEventManager%602> class instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="4c4a5-163">Při použití <xref:System.Windows.WeakEventManager%602> Chcete-li zaregistrovat naslouchacích procesů událostí, je zadat zdroj události a <xref:System.EventArgs> typů jako parametrů typů třídy a volání <xref:System.Windows.WeakEventManager%602.AddHandler%2A> jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="4c4a5-163">When you use <xref:System.Windows.WeakEventManager%602> to register event listeners, you supply the event source and <xref:System.EventArgs> type as the type parameters to the class and call <xref:System.Windows.WeakEventManager%602.AddHandler%2A> as shown in the following code:</span></span>  
  
    ```  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a><span data-ttu-id="4c4a5-164">Vytvoření vlastní třídy slabé správce událostí</span><span class="sxs-lookup"><span data-stu-id="4c4a5-164">Creating a Custom Weak Event Manager Class</span></span>  
  
1.  <span data-ttu-id="4c4a5-165">Zkopírujte následující šablony třídu do projektu.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-165">Copy the following class template to your project.</span></span>  
  
     <span data-ttu-id="4c4a5-166">Tato třída dědí z <xref:System.Windows.WeakEventManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-166">This class inherits from the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2.  <span data-ttu-id="4c4a5-167">Nahraďte `SomeEventWeakEventManager` název s svůj vlastní název.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-167">Replace the `SomeEventWeakEventManager` name with your own name.</span></span>  
  
3.  <span data-ttu-id="4c4a5-168">Nahraďte tři názvy popsané s odpovídající názvy pro událost.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-168">Replace the three names described previously with the corresponding names for your event.</span></span> <span data-ttu-id="4c4a5-169">(`SomeEvent`, `EventSource`, a `SomeEventEventArgs`)</span><span class="sxs-lookup"><span data-stu-id="4c4a5-169">(`SomeEvent`, `EventSource`, and `SomeEventEventArgs`)</span></span>  
  
4.  <span data-ttu-id="4c4a5-170">Nastavte viditelnost (veřejné / interní / privátní) slabé event – třída manager na stejném viditelnost jako událost, které spravuje.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-170">Set the visibility (public / internal / private) of the weak event manager class to the same visibility as event it manages.</span></span>  
  
5.  <span data-ttu-id="4c4a5-171">Pomocí nového správce slabé událostí místo normální událostí spojení.</span><span class="sxs-lookup"><span data-stu-id="4c4a5-171">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="4c4a5-172">Pokud například váš kód používá následující vzorec k odběru události:</span><span class="sxs-lookup"><span data-stu-id="4c4a5-172">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="4c4a5-173">Změňte jej na vzoru následující:</span><span class="sxs-lookup"><span data-stu-id="4c4a5-173">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="4c4a5-174">Podobně pokud kód používá následující vzor k odhlášení odběru na událost:</span><span class="sxs-lookup"><span data-stu-id="4c4a5-174">Similarly, if your code uses the following pattern to unsubscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     <span data-ttu-id="4c4a5-175">Změňte jej na vzoru následující:</span><span class="sxs-lookup"><span data-stu-id="4c4a5-175">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4c4a5-176">Viz také</span><span class="sxs-lookup"><span data-stu-id="4c4a5-176">See Also</span></span>  
 <xref:System.Windows.WeakEventManager>  
 <xref:System.Windows.IWeakEventListener>  
 [<span data-ttu-id="4c4a5-177">Přehled směrovaných událostí</span><span class="sxs-lookup"><span data-stu-id="4c4a5-177">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="4c4a5-178">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="4c4a5-178">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
