---
title: Návrh události
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
ms.openlocfilehash: b44ee5933f8629b4dddbf3be1b79b2e77b0254f7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741684"
---
# <a name="event-design"></a><span data-ttu-id="4589b-102">Návrh události</span><span class="sxs-lookup"><span data-stu-id="4589b-102">Event Design</span></span>
<span data-ttu-id="4589b-103">Události jsou nejčastěji používané formy zpětných volání (konstrukce, které umožňují rozhraní volat do uživatelského kódu).</span><span class="sxs-lookup"><span data-stu-id="4589b-103">Events are the most commonly used form of callbacks (constructs that allow the framework to call into user code).</span></span> <span data-ttu-id="4589b-104">Mezi další mechanismy zpětného volání patří členové, kteří přijímají delegáty, virtuální členy a moduly plug-in založené na rozhraní. data z studií použitelnosti označují, že většina vývojářů je pohodlnější díky událostem, než používá jiné mechanismy zpětného volání. .</span><span class="sxs-lookup"><span data-stu-id="4589b-104">Other callback mechanisms include members taking delegates, virtual members, and interface-based plug-ins. Data from usability studies indicate that the majority of developers are more comfortable using events than they are using the other callback mechanisms.</span></span> <span data-ttu-id="4589b-105">Události jsou v ucelené integraci se sadou Visual Studio a mnoha jazyky.</span><span class="sxs-lookup"><span data-stu-id="4589b-105">Events are nicely integrated with Visual Studio and many languages.</span></span>

 <span data-ttu-id="4589b-106">Je důležité si uvědomit, že existují dvě skupiny událostí: události vyvolané před stavem změny systému, nazývané před událostmi a události vyvolané po změně stavu, označované po událostech.</span><span class="sxs-lookup"><span data-stu-id="4589b-106">It is important to note that there are two groups of events: events raised before a state of the system changes, called pre-events, and events raised after a state changes, called post-events.</span></span> <span data-ttu-id="4589b-107">Příkladem předběžné události by byla `Form.Closing`, která je aktivována před zavřením formuláře.</span><span class="sxs-lookup"><span data-stu-id="4589b-107">An example of a pre-event would be `Form.Closing`, which is raised before a form is closed.</span></span> <span data-ttu-id="4589b-108">Příkladem následné události by byl `Form.Closed`, který je vyvolán po zavření formuláře.</span><span class="sxs-lookup"><span data-stu-id="4589b-108">An example of a post-event would be `Form.Closed`, which is raised after a form is closed.</span></span>

 <span data-ttu-id="4589b-109">✔️ použít termín "vyvolat" pro události, nikoli "oheň" nebo "Trigger".</span><span class="sxs-lookup"><span data-stu-id="4589b-109">✔️ DO use the term "raise" for events rather than "fire" or "trigger."</span></span>

 <span data-ttu-id="4589b-110">✔️ použít <xref:System.EventHandler%601?displayProperty=nameWithType> namísto ručního vytváření nových delegátů pro použití jako obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="4589b-110">✔️ DO use <xref:System.EventHandler%601?displayProperty=nameWithType> instead of manually creating new delegates to be used as event handlers.</span></span>

 <span data-ttu-id="4589b-111">✔️ Zvažte použití podtřídy <xref:System.EventArgs> jako argumentu události, pokud nejste naprosto jistotu, že událost nebude nikdy potřebovat převést žádná data do metody zpracování událostí. v takovém případě lze typ `EventArgs` použít přímo.</span><span class="sxs-lookup"><span data-stu-id="4589b-111">✔️ CONSIDER using a subclass of <xref:System.EventArgs> as the event argument, unless you are absolutely sure the event will never need to carry any data to the event handling method, in which case you can use the `EventArgs` type directly.</span></span>

 <span data-ttu-id="4589b-112">Pokud rozhraní API dodáváte přímo pomocí `EventArgs`, nebudete nikdy moci přidat žádná data, která by se měla přenést s událostí bez narušení kompatibility.</span><span class="sxs-lookup"><span data-stu-id="4589b-112">If you ship an API using `EventArgs` directly, you will never be able to add any data to be carried with the event without breaking compatibility.</span></span> <span data-ttu-id="4589b-113">Použijete-li podtřídu i v případě, že je zpočátku zcela prázdná, budete moci v případě potřeby přidat vlastnosti do podtřídy.</span><span class="sxs-lookup"><span data-stu-id="4589b-113">If you use a subclass, even if initially completely empty, you will be able to add properties to the subclass when needed.</span></span>

 <span data-ttu-id="4589b-114">k vyvolání každé události ✔️ použít chráněnou virtuální metodu.</span><span class="sxs-lookup"><span data-stu-id="4589b-114">✔️ DO use a protected virtual method to raise each event.</span></span> <span data-ttu-id="4589b-115">To platí pouze pro nestatické události pro nezapečetěné třídy, nikoli pro struktury, zapečetěné třídy nebo statické události.</span><span class="sxs-lookup"><span data-stu-id="4589b-115">This is only applicable to nonstatic events on unsealed classes, not to structs, sealed classes, or static events.</span></span>

 <span data-ttu-id="4589b-116">Účelem metody je poskytnout pro odvozenou třídu způsob, jakým má být událost zpracována pomocí přepsání.</span><span class="sxs-lookup"><span data-stu-id="4589b-116">The purpose of the method is to provide a way for a derived class to handle the event using an override.</span></span> <span data-ttu-id="4589b-117">Přepisování je flexibilnější, rychlejší a přirozený způsob zpracování událostí základní třídy v odvozených třídách.</span><span class="sxs-lookup"><span data-stu-id="4589b-117">Overriding is a more flexible, faster, and more natural way to handle base class events in derived classes.</span></span> <span data-ttu-id="4589b-118">Podle konvence má název metody začínat na "on" a musí následovat za názvem události.</span><span class="sxs-lookup"><span data-stu-id="4589b-118">By convention, the name of the method should start with "On" and be followed with the name of the event.</span></span>

 <span data-ttu-id="4589b-119">Odvozená třída může zvolit, že se má volat základní implementace metody v jejím přepsání.</span><span class="sxs-lookup"><span data-stu-id="4589b-119">The derived class can choose not to call the base implementation of the method in its override.</span></span> <span data-ttu-id="4589b-120">Připravte se na to bez jakéhokoli zpracování v metodě, která je nutná pro správné fungování základní třídy.</span><span class="sxs-lookup"><span data-stu-id="4589b-120">Be prepared for this by not including any processing in the method that is required for the base class to work correctly.</span></span>

 <span data-ttu-id="4589b-121">✔️ přijímá jeden parametr pro chráněnou metodu, která vyvolá událost.</span><span class="sxs-lookup"><span data-stu-id="4589b-121">✔️ DO take one parameter to the protected method that raises an event.</span></span>

 <span data-ttu-id="4589b-122">Parametr by měl mít název `e` a měl by být zadán jako třída argumentu události.</span><span class="sxs-lookup"><span data-stu-id="4589b-122">The parameter should be named `e` and should be typed as the event argument class.</span></span>

 <span data-ttu-id="4589b-123">Při vyvolání nestatické události ❌ Nepředávat jako odesilateli hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="4589b-123">❌ DO NOT pass null as the sender when raising a nonstatic event.</span></span>

 <span data-ttu-id="4589b-124">Při vyvolání statické události ✔️ předat jako odesilateli hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="4589b-124">✔️ DO pass null as the sender when raising a static event.</span></span>

 <span data-ttu-id="4589b-125">Při vyvolání události ❌ Nepředávat jako datový parametr události hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="4589b-125">❌ DO NOT pass null as the event data parameter when raising an event.</span></span>

 <span data-ttu-id="4589b-126">Pokud nechcete předat žádná data do metody zpracování událostí, je vhodné předat `EventArgs.Empty`.</span><span class="sxs-lookup"><span data-stu-id="4589b-126">You should pass `EventArgs.Empty` if you don’t want to pass any data to the event handling method.</span></span> <span data-ttu-id="4589b-127">Vývojáři očekávají, že tento parametr nemá hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="4589b-127">Developers expect this parameter not to be null.</span></span>

 <span data-ttu-id="4589b-128">✔️ Zvažte vyvolání událostí, které může koncový uživatel zrušit.</span><span class="sxs-lookup"><span data-stu-id="4589b-128">✔️ CONSIDER raising events that the end user can cancel.</span></span> <span data-ttu-id="4589b-129">To platí jenom pro předběžné události.</span><span class="sxs-lookup"><span data-stu-id="4589b-129">This only applies to pre-events.</span></span>

 <span data-ttu-id="4589b-130">Pokud chcete koncovému uživateli dovolit události zrušit, použijte <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> nebo jeho podtřídu jako argument události.</span><span class="sxs-lookup"><span data-stu-id="4589b-130">Use <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> or its subclass as the event argument to allow the end user to cancel events.</span></span>

### <a name="custom-event-handler-design"></a><span data-ttu-id="4589b-131">Vlastní návrh obslužné rutiny událostí</span><span class="sxs-lookup"><span data-stu-id="4589b-131">Custom Event Handler Design</span></span>
 <span data-ttu-id="4589b-132">Existují případy, kdy `EventHandler<T>` nelze použít, například když rozhraní potřebuje pracovat se staršími verzemi modulu CLR, které nepodporovaly obecné typy.</span><span class="sxs-lookup"><span data-stu-id="4589b-132">There are cases in which `EventHandler<T>` cannot be used, such as when the framework needs to work with earlier versions of the CLR, which did not support Generics.</span></span> <span data-ttu-id="4589b-133">V takových případech může být nutné navrhnout a vyvinout delegáta vlastní obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="4589b-133">In such cases, you might need to design and develop a custom event handler delegate.</span></span>

 <span data-ttu-id="4589b-134">✔️ použít návratový typ void pro obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="4589b-134">✔️ DO use a return type of void for event handlers.</span></span>

 <span data-ttu-id="4589b-135">Obslužná rutina události může vyvolat více metod zpracování událostí, případně u více objektů.</span><span class="sxs-lookup"><span data-stu-id="4589b-135">An event handler can invoke multiple event handling methods, possibly on multiple objects.</span></span> <span data-ttu-id="4589b-136">Pokud metody zpracování událostí povolily vrácení hodnoty, bude pro každé vyvolání události k dispozici více vrácených hodnot.</span><span class="sxs-lookup"><span data-stu-id="4589b-136">If event handling methods were allowed to return a value, there would be multiple return values for each event invocation.</span></span>

 <span data-ttu-id="4589b-137">✔️ Použijte `object` jako typ prvního parametru obslužné rutiny události a zavolejte ho `sender`.</span><span class="sxs-lookup"><span data-stu-id="4589b-137">✔️ DO use `object` as the type of the first parameter of the event handler, and call it `sender`.</span></span>

 <span data-ttu-id="4589b-138">✔️ Použijte <xref:System.EventArgs?displayProperty=nameWithType> nebo jeho podtřídu jako typ druhého parametru obslužné rutiny události a zavolejte ji `e`.</span><span class="sxs-lookup"><span data-stu-id="4589b-138">✔️ DO use <xref:System.EventArgs?displayProperty=nameWithType> or its subclass as the type of the second parameter of the event handler, and call it `e`.</span></span>

 <span data-ttu-id="4589b-139">❌ pro obslužné rutiny událostí neobsahují více než dva parametry.</span><span class="sxs-lookup"><span data-stu-id="4589b-139">❌ DO NOT have more than two parameters on event handlers.</span></span>

 <span data-ttu-id="4589b-140">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="4589b-140">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="4589b-141">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="4589b-141">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="4589b-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4589b-142">See also</span></span>

- [<span data-ttu-id="4589b-143">Pokyny k návrhu člena</span><span class="sxs-lookup"><span data-stu-id="4589b-143">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="4589b-144">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="4589b-144">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
