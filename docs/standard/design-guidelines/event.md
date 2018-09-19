---
title: Návrh události
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b257da73d33fae54ef464e9dd69906316b87fd88
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46288274"
---
# <a name="event-design"></a><span data-ttu-id="05fff-102">Návrh události</span><span class="sxs-lookup"><span data-stu-id="05fff-102">Event Design</span></span>
<span data-ttu-id="05fff-103">Události jsou nejčastěji používané formuláři zpětná volání (konstrukce, které umožňují rozhraní pro volání do uživatelského kódu).</span><span class="sxs-lookup"><span data-stu-id="05fff-103">Events are the most commonly used form of callbacks (constructs that allow the framework to call into user code).</span></span> <span data-ttu-id="05fff-104">Jiné mechanismy zpětné volání zahrnout členy, přičemž delegáty, virtuální členy a založeny na rozhraní modulů plug-in. Data z použitelnost studie označuje, že většina vývojářů je pohodlnější použití událostí, než které využívají jiné mechanismy zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="05fff-104">Other callback mechanisms include members taking delegates, virtual members, and interface-based plug-ins. Data from usability studies indicate that the majority of developers are more comfortable using events than they are using the other callback mechanisms.</span></span> <span data-ttu-id="05fff-105">Události jsou krásně součástí sady Visual Studio a mnoha jazyků.</span><span class="sxs-lookup"><span data-stu-id="05fff-105">Events are nicely integrated with Visual Studio and many languages.</span></span>  
  
 <span data-ttu-id="05fff-106">Je důležité si uvědomit, že existují dvě skupiny událostí: události vyvolané před stavu změny systému, volá se před událostmi a události vyvolané po změně stavu, volá se po události.</span><span class="sxs-lookup"><span data-stu-id="05fff-106">It is important to note that there are two groups of events: events raised before a state of the system changes, called pre-events, and events raised after a state changes, called post-events.</span></span> <span data-ttu-id="05fff-107">Příkladem předběžné události může být `Form.Closing`, která je vyvolána před zavřením formuláře.</span><span class="sxs-lookup"><span data-stu-id="05fff-107">An example of a pre-event would be `Form.Closing`, which is raised before a form is closed.</span></span> <span data-ttu-id="05fff-108">Příkladem po události může být `Form.Closed`, která je vyvolána po zavření formuláře.</span><span class="sxs-lookup"><span data-stu-id="05fff-108">An example of a post-event would be `Form.Closed`, which is raised after a form is closed.</span></span>  
  
 <span data-ttu-id="05fff-109">**✓ DO** použít termín "vyvolat" pro události místo "fire" nebo "spustit".</span><span class="sxs-lookup"><span data-stu-id="05fff-109">**✓ DO** use the term "raise" for events rather than "fire" or "trigger."</span></span>  
  
 <span data-ttu-id="05fff-110">**✓ DO** použít <xref:System.EventHandler%601?displayProperty=nameWithType> místo ruční vytvoření nového delegáti má být použit jako obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="05fff-110">**✓ DO** use <xref:System.EventHandler%601?displayProperty=nameWithType> instead of manually creating new delegates to be used as event handlers.</span></span>  
  
 <span data-ttu-id="05fff-111">**✓ CONSIDER** pomocí podtřídou třídy <xref:System.EventArgs> jako argument událost, pokud si nejste zcela jisti událost nikdy nebudete potřebovat k provedení žádná data pro zpracování metody událostí v takovém případě můžete použít `EventArgs` typ přímo.</span><span class="sxs-lookup"><span data-stu-id="05fff-111">**✓ CONSIDER** using a subclass of <xref:System.EventArgs> as the event argument, unless you are absolutely sure the event will never need to carry any data to the event handling method, in which case you can use the `EventArgs` type directly.</span></span>  
  
 <span data-ttu-id="05fff-112">Pokud neodešlete rozhraní API pomocí `EventArgs` přímo, nikdy budete moct přidat žádná data k realizaci s událostí bez porušení kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="05fff-112">If you ship an API using `EventArgs` directly, you will never be able to add any data to be carried with the event without breaking compatibility.</span></span> <span data-ttu-id="05fff-113">Pokud používáte podtřídu, i pokud původně úplně prázdná, bude možné přidávat vlastnosti pro podtřídu v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="05fff-113">If you use a subclass, even if initially completely empty, you will be able to add properties to the subclass when needed.</span></span>  
  
 <span data-ttu-id="05fff-114">**✓ DO** použít chráněné virtuální metodu pro vyvolání každé události.</span><span class="sxs-lookup"><span data-stu-id="05fff-114">**✓ DO** use a protected virtual method to raise each event.</span></span> <span data-ttu-id="05fff-115">To platí pouze pro nestatické události v nezapečetěné třídy, struktury, zapečetěné třídy ani statické události.</span><span class="sxs-lookup"><span data-stu-id="05fff-115">This is only applicable to nonstatic events on unsealed classes, not to structs, sealed classes, or static events.</span></span>  
  
 <span data-ttu-id="05fff-116">Cílem této metody je poskytnout způsob, jakým odvozené třídy za účelem zpracování události pomocí přepsání.</span><span class="sxs-lookup"><span data-stu-id="05fff-116">The purpose of the method is to provide a way for a derived class to handle the event using an override.</span></span> <span data-ttu-id="05fff-117">Přepsání je flexibilnější, rychlejší a přirozenější způsob, jak zpracovat událostí třídy base v odvozených třídách.</span><span class="sxs-lookup"><span data-stu-id="05fff-117">Overriding is a more flexible, faster, and more natural way to handle base class events in derived classes.</span></span> <span data-ttu-id="05fff-118">Název metody podle konvence by měla začínat řetězcem "On" a následovat název události.</span><span class="sxs-lookup"><span data-stu-id="05fff-118">By convention, the name of the method should start with "On" and be followed with the name of the event.</span></span>  
  
 <span data-ttu-id="05fff-119">Odvozené třídy můžete volat základní implementaci metody v jeho přepsání.</span><span class="sxs-lookup"><span data-stu-id="05fff-119">The derived class can choose not to call the base implementation of the method in its override.</span></span> <span data-ttu-id="05fff-120">Připravit pro tento bez zahrnutí zpracování v metodě, která je požadována pro základní třídu fungovat správně.</span><span class="sxs-lookup"><span data-stu-id="05fff-120">Be prepared for this by not including any processing in the method that is required for the base class to work correctly.</span></span>  
  
 <span data-ttu-id="05fff-121">**✓ DO** trvat jeden parametr chráněná metoda, která vyvolává událost.</span><span class="sxs-lookup"><span data-stu-id="05fff-121">**✓ DO** take one parameter to the protected method that raises an event.</span></span>  
  
 <span data-ttu-id="05fff-122">Parametr by měl být pojmenován `e` a by měl být typu Třída argumentů události.</span><span class="sxs-lookup"><span data-stu-id="05fff-122">The parameter should be named `e` and should be typed as the event argument class.</span></span>  
  
 <span data-ttu-id="05fff-123">**X DO NOT** předejte hodnotu null pro odesílatele při vyvolání nestatické události.</span><span class="sxs-lookup"><span data-stu-id="05fff-123">**X DO NOT** pass null as the sender when raising a nonstatic event.</span></span>  
  
 <span data-ttu-id="05fff-124">**✓ DO** předejte hodnotu null pro odesílatele při vyvolání statické události.</span><span class="sxs-lookup"><span data-stu-id="05fff-124">**✓ DO** pass null as the sender when raising a static event.</span></span>  
  
 <span data-ttu-id="05fff-125">**X DO NOT** předejte jako parametr data událostí hodnotu null při vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="05fff-125">**X DO NOT** pass null as the event data parameter when raising an event.</span></span>  
  
 <span data-ttu-id="05fff-126">Je třeba předat `EventArgs.Empty` Pokud nechcete předávat žádná data pro metodu zpracování událostí.</span><span class="sxs-lookup"><span data-stu-id="05fff-126">You should pass `EventArgs.Empty` if you don’t want to pass any data to the event handling method.</span></span> <span data-ttu-id="05fff-127">Vývojáři očekávat, že tento parametr nechcete mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="05fff-127">Developers expect this parameter not to be null.</span></span>  
  
 <span data-ttu-id="05fff-128">**✓ CONSIDER** vyvolávání událostí, které můžete zrušit koncového uživatele.</span><span class="sxs-lookup"><span data-stu-id="05fff-128">**✓ CONSIDER** raising events that the end user can cancel.</span></span> <span data-ttu-id="05fff-129">To platí pouze pro před událostmi.</span><span class="sxs-lookup"><span data-stu-id="05fff-129">This only applies to pre-events.</span></span>  
  
 <span data-ttu-id="05fff-130">Použití <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> nebo jeho podtřídy jako argument události koncovému uživateli pro zrušení události.</span><span class="sxs-lookup"><span data-stu-id="05fff-130">Use <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> or its subclass as the event argument to allow the end user to cancel events.</span></span>  
  
### <a name="custom-event-handler-design"></a><span data-ttu-id="05fff-131">Obslužná rutina návrhu vlastní událost</span><span class="sxs-lookup"><span data-stu-id="05fff-131">Custom Event Handler Design</span></span>  
 <span data-ttu-id="05fff-132">Existují případy, ve kterém `EventHandler<T>` nelze použít, třeba když rozhraní musí fungovat s předchozími verzemi modulu CLR, který nepodporuje obecné typy.</span><span class="sxs-lookup"><span data-stu-id="05fff-132">There are cases in which `EventHandler<T>` cannot be used, such as when the framework needs to work with earlier versions of the CLR, which did not support Generics.</span></span> <span data-ttu-id="05fff-133">V takových případech může být potřeba navrhovat a vyvíjet vlastní událost obslužné rutiny delegáta.</span><span class="sxs-lookup"><span data-stu-id="05fff-133">In such cases, you might need to design and develop a custom event handler delegate.</span></span>  
  
 <span data-ttu-id="05fff-134">**✓ DO** použít návratový typ void pro obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="05fff-134">**✓ DO** use a return type of void for event handlers.</span></span>  
  
 <span data-ttu-id="05fff-135">Obslužné rutiny události můžete volat metody, případně pro více objektů zpracování více událostí.</span><span class="sxs-lookup"><span data-stu-id="05fff-135">An event handler can invoke multiple event handling methods, possibly on multiple objects.</span></span> <span data-ttu-id="05fff-136">Pokud pro navrácení hodnoty byly povoleny metody zpracování událostí, by bylo více vrácených hodnot pro každé vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="05fff-136">If event handling methods were allowed to return a value, there would be multiple return values for each event invocation.</span></span>  
  
 <span data-ttu-id="05fff-137">**✓ DO** použít `object` jako typ prvního parametru obslužné rutiny události a pojmenujte ji `sender`.</span><span class="sxs-lookup"><span data-stu-id="05fff-137">**✓ DO** use `object` as the type of the first parameter of the event handler, and call it `sender`.</span></span>  
  
 <span data-ttu-id="05fff-138">**✓ DO** použít <xref:System.EventArgs?displayProperty=nameWithType> nebo jeho podtřídou jako typ druhého parametru obslužné rutiny události a pojmenujte ji `e`.</span><span class="sxs-lookup"><span data-stu-id="05fff-138">**✓ DO** use <xref:System.EventArgs?displayProperty=nameWithType> or its subclass as the type of the second parameter of the event handler, and call it `e`.</span></span>  
  
 <span data-ttu-id="05fff-139">**X DO NOT** mít více než dva parametry obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="05fff-139">**X DO NOT** have more than two parameters on event handlers.</span></span>  
  
 <span data-ttu-id="05fff-140">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="05fff-140">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="05fff-141">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="05fff-141">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05fff-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05fff-142">See also</span></span>

- [<span data-ttu-id="05fff-143">Pokyny k návrhu člena</span><span class="sxs-lookup"><span data-stu-id="05fff-143">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
- [<span data-ttu-id="05fff-144">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="05fff-144">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
