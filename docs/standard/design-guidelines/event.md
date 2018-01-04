---
title: "Návrh událostí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a07392ba805b5f2a3913b01a15dd0e1668f0ccf7
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="event-design"></a><span data-ttu-id="bd828-102">Návrh událostí</span><span class="sxs-lookup"><span data-stu-id="bd828-102">Event Design</span></span>
<span data-ttu-id="bd828-103">Události jsou nejčastěji používané formu zpětných volání (konstrukce, které umožňují rozhraní k volání do kódu uživatele).</span><span class="sxs-lookup"><span data-stu-id="bd828-103">Events are the most commonly used form of callbacks (constructs that allow the framework to call into user code).</span></span> <span data-ttu-id="bd828-104">Další mechanismy zpětné volání zahrnout členy trvá delegáti, virtuální členové a na základě rozhraní moduly plug-in. Data z použitelnost studie označit, že většina vývojářů pohodlnější použití událostí, než používají jiné mechanismy zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="bd828-104">Other callback mechanisms include members taking delegates, virtual members, and interface-based plug-ins. Data from usability studies indicate that the majority of developers are more comfortable using events than they are using the other callback mechanisms.</span></span> <span data-ttu-id="bd828-105">Události jsou výborně integrované s Visual Studio a mnoha jazycích.</span><span class="sxs-lookup"><span data-stu-id="bd828-105">Events are nicely integrated with Visual Studio and many languages.</span></span>  
  
 <span data-ttu-id="bd828-106">Je důležité si uvědomit, že existují dvě skupiny události: událostí vyvolaných před stavu změny systému, volá se před události a události aktivované po změn stavu, volá se po události.</span><span class="sxs-lookup"><span data-stu-id="bd828-106">It is important to note that there are two groups of events: events raised before a state of the system changes, called pre-events, and events raised after a state changes, called post-events.</span></span> <span data-ttu-id="bd828-107">Příkladem předběžné události může být `Form.Closing`, která je vyvolána před zavřením formuláře.</span><span class="sxs-lookup"><span data-stu-id="bd828-107">An example of a pre-event would be `Form.Closing`, which is raised before a form is closed.</span></span> <span data-ttu-id="bd828-108">Jedná se například po události `Form.Closed`, která se vyvolá po zavření formuláře.</span><span class="sxs-lookup"><span data-stu-id="bd828-108">An example of a post-event would be `Form.Closed`, which is raised after a form is closed.</span></span>  
  
 <span data-ttu-id="bd828-109">**PROVEĎTE ✓** použít termín "vyvolat" pro události místo "fire" nebo "spustit".</span><span class="sxs-lookup"><span data-stu-id="bd828-109">**✓ DO** use the term "raise" for events rather than "fire" or "trigger."</span></span>  
  
 <span data-ttu-id="bd828-110">**PROVEĎTE ✓** použít <xref:System.EventHandler%601?displayProperty=nameWithType> místo ruční vytvoření nového delegáti má být použit jako obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="bd828-110">**✓ DO** use <xref:System.EventHandler%601?displayProperty=nameWithType> instead of manually creating new delegates to be used as event handlers.</span></span>  
  
 <span data-ttu-id="bd828-111">**✓ ZVAŽTE** pomocí podtřídou třídy <xref:System.EventArgs> jako argument událost, pokud si nejste zcela jisti událost nikdy nebudete potřebovat k provedení žádná data pro zpracování metody událostí v takovém případě můžete použít `EventArgs` typ přímo.</span><span class="sxs-lookup"><span data-stu-id="bd828-111">**✓ CONSIDER** using a subclass of <xref:System.EventArgs> as the event argument, unless you are absolutely sure the event will never need to carry any data to the event handling method, in which case you can use the `EventArgs` type directly.</span></span>  
  
 <span data-ttu-id="bd828-112">Pokud dodávat rozhraní API pomocí `EventArgs` přímo, nikdy nebudete moct přidat žádná data k realizaci k události, aniž by vás kompatibility.</span><span class="sxs-lookup"><span data-stu-id="bd828-112">If you ship an API using `EventArgs` directly, you will never be able to add any data to be carried with the event without breaking compatibility.</span></span> <span data-ttu-id="bd828-113">Pokud používáte podtřídy, i pokud původně úplně prázdná, nebudete moct přidávat vlastnosti pro podtřídu v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="bd828-113">If you use a subclass, even if initially completely empty, you will be able to add properties to the subclass when needed.</span></span>  
  
 <span data-ttu-id="bd828-114">**PROVEĎTE ✓** použít chráněné virtuální metodu pro vyvolání každé události.</span><span class="sxs-lookup"><span data-stu-id="bd828-114">**✓ DO** use a protected virtual method to raise each event.</span></span> <span data-ttu-id="bd828-115">Tento krok platí jenom pro nestatické událostí v nezapečetěných třídy, struktury, zapečetěné třídy ani statické události.</span><span class="sxs-lookup"><span data-stu-id="bd828-115">This is only applicable to nonstatic events on unsealed classes, not to structs, sealed classes, or static events.</span></span>  
  
 <span data-ttu-id="bd828-116">Cílem této metody je poskytnout způsob, jak odvozené třídy za účelem zpracování události pomocí přepsání.</span><span class="sxs-lookup"><span data-stu-id="bd828-116">The purpose of the method is to provide a way for a derived class to handle the event using an override.</span></span> <span data-ttu-id="bd828-117">Přepsání je flexibilnější, rychlejší a přirozenější způsob zpracování událostí třídy base v odvozených třídách.</span><span class="sxs-lookup"><span data-stu-id="bd828-117">Overriding is a more flexible, faster, and more natural way to handle base class events in derived classes.</span></span> <span data-ttu-id="bd828-118">Podle konvence název metody by měla začínat znakem "Na" a provést s názvem události.</span><span class="sxs-lookup"><span data-stu-id="bd828-118">By convention, the name of the method should start with "On" and be followed with the name of the event.</span></span>  
  
 <span data-ttu-id="bd828-119">Odvozené třídy mohou rozhodnout volat základní implementaci metody v jeho přepsání.</span><span class="sxs-lookup"><span data-stu-id="bd828-119">The derived class can choose not to call the base implementation of the method in its override.</span></span> <span data-ttu-id="bd828-120">Připravit pro tento není zahrnutím jakékoli zpracovávání v metodě, které jsou potřeba pro základní třídu fungovala správně.</span><span class="sxs-lookup"><span data-stu-id="bd828-120">Be prepared for this by not including any processing in the method that is required for the base class to work correctly.</span></span>  
  
 <span data-ttu-id="bd828-121">**PROVEĎTE ✓** trvat jeden parametr chráněná metoda, která vyvolává událost.</span><span class="sxs-lookup"><span data-stu-id="bd828-121">**✓ DO** take one parameter to the protected method that raises an event.</span></span>  
  
 <span data-ttu-id="bd828-122">Parametr musí mít název `e` a by měla být zadána jako třída argumentů události.</span><span class="sxs-lookup"><span data-stu-id="bd828-122">The parameter should be named `e` and should be typed as the event argument class.</span></span>  
  
 <span data-ttu-id="bd828-123">**X nesmí** předejte hodnotu null pro odesílatele při vyvolání nestatické události.</span><span class="sxs-lookup"><span data-stu-id="bd828-123">**X DO NOT** pass null as the sender when raising a nonstatic event.</span></span>  
  
 <span data-ttu-id="bd828-124">**PROVEĎTE ✓** předejte hodnotu null pro odesílatele při vyvolání statické události.</span><span class="sxs-lookup"><span data-stu-id="bd828-124">**✓ DO** pass null as the sender when raising a static event.</span></span>  
  
 <span data-ttu-id="bd828-125">**X nesmí** předejte jako parametr data událostí hodnotu null při vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="bd828-125">**X DO NOT** pass null as the event data parameter when raising an event.</span></span>  
  
 <span data-ttu-id="bd828-126">By měla předávat `EventArgs.Empty` Pokud nechcete, aby všechny data předat metodu zpracování událostí.</span><span class="sxs-lookup"><span data-stu-id="bd828-126">You should pass `EventArgs.Empty` if you don’t want to pass any data to the event handling method.</span></span> <span data-ttu-id="bd828-127">Vývojáři očekávají, že tento parametr nechcete mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="bd828-127">Developers expect this parameter not to be null.</span></span>  
  
 <span data-ttu-id="bd828-128">**✓ ZVAŽTE** vyvolávání událostí, které můžete zrušit koncového uživatele.</span><span class="sxs-lookup"><span data-stu-id="bd828-128">**✓ CONSIDER** raising events that the end user can cancel.</span></span> <span data-ttu-id="bd828-129">To platí jenom pro předběžné události.</span><span class="sxs-lookup"><span data-stu-id="bd828-129">This only applies to pre-events.</span></span>  
  
 <span data-ttu-id="bd828-130">Použití <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> nebo jeho podtřídou jako argument události koncovému uživateli se zrušit události.</span><span class="sxs-lookup"><span data-stu-id="bd828-130">Use <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> or its subclass as the event argument to allow the end user to cancel events.</span></span>  
  
### <a name="custom-event-handler-design"></a><span data-ttu-id="bd828-131">Obslužná rutina návrhu vlastní události</span><span class="sxs-lookup"><span data-stu-id="bd828-131">Custom Event Handler Design</span></span>  
 <span data-ttu-id="bd828-132">Existují případy, ve kterém `EventHandler<T>` nelze použít, například když rozhraní potřebuje pro starší verze modulu CLR, který nepodporuje obecné typy.</span><span class="sxs-lookup"><span data-stu-id="bd828-132">There are cases in which `EventHandler<T>` cannot be used, such as when the framework needs to work with earlier versions of the CLR, which did not support Generics.</span></span> <span data-ttu-id="bd828-133">V takových případech může být nutné pro návrh a vývoj vlastní události delegáta obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="bd828-133">In such cases, you might need to design and develop a custom event handler delegate.</span></span>  
  
 <span data-ttu-id="bd828-134">**PROVEĎTE ✓** použít návratový typ void pro obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="bd828-134">**✓ DO** use a return type of void for event handlers.</span></span>  
  
 <span data-ttu-id="bd828-135">Obslužné rutiny události můžete vyvolat metody, které by mohly mít na více objektů zpracování více událostí.</span><span class="sxs-lookup"><span data-stu-id="bd828-135">An event handler can invoke multiple event handling methods, possibly on multiple objects.</span></span> <span data-ttu-id="bd828-136">Pokud bude vrácena hodnota byly povoleny metody zpracování událostí, by bylo více vrácených hodnot pro každé vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="bd828-136">If event handling methods were allowed to return a value, there would be multiple return values for each event invocation.</span></span>  
  
 <span data-ttu-id="bd828-137">**PROVEĎTE ✓** použít `object` jako typ prvního parametru obslužné rutiny události a pojmenujte ji `sender`.</span><span class="sxs-lookup"><span data-stu-id="bd828-137">**✓ DO** use `object` as the type of the first parameter of the event handler, and call it `sender`.</span></span>  
  
 <span data-ttu-id="bd828-138">**PROVEĎTE ✓** použít <xref:System.EventArgs?displayProperty=nameWithType> nebo jeho podtřídou jako typ druhého parametru obslužné rutiny události a pojmenujte ji `e`.</span><span class="sxs-lookup"><span data-stu-id="bd828-138">**✓ DO** use <xref:System.EventArgs?displayProperty=nameWithType> or its subclass as the type of the second parameter of the event handler, and call it `e`.</span></span>  
  
 <span data-ttu-id="bd828-139">**X nesmí** mít více než dva parametry obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="bd828-139">**X DO NOT** have more than two parameters on event handlers.</span></span>  
  
 <span data-ttu-id="bd828-140">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="bd828-140">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="bd828-141">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="bd828-141">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd828-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="bd828-142">See Also</span></span>  
 [<span data-ttu-id="bd828-143">Pokyny k návrhu člena</span><span class="sxs-lookup"><span data-stu-id="bd828-143">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="bd828-144">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="bd828-144">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
