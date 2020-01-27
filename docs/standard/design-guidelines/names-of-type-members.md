---
title: Názvy členů typu
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], names
- methods [.NET Framework], names
- type members
- properties [.NET Framework], names
- fields, names
- field names
- names [.NET Framework], type members
- members [.NET Framework], type
ms.assetid: af5a0903-36af-4c2a-b848-cf959affeaa5
ms.openlocfilehash: 81c837bd045992043208a59f6ee16803c1d6eb3c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744179"
---
# <a name="names-of-type-members"></a><span data-ttu-id="3b4ee-102">Názvy členů typu</span><span class="sxs-lookup"><span data-stu-id="3b4ee-102">Names of Type Members</span></span>
<span data-ttu-id="3b4ee-103">Typy jsou tvořeny členy: metody, vlastnosti, události, konstruktory a pole.</span><span class="sxs-lookup"><span data-stu-id="3b4ee-103">Types are made of members: methods, properties, events, constructors, and fields.</span></span> <span data-ttu-id="3b4ee-104">Následující části popisují pokyny pro pojmenování členů typu.</span><span class="sxs-lookup"><span data-stu-id="3b4ee-104">The following sections describe guidelines for naming type members.</span></span>

## <a name="names-of-methods"></a><span data-ttu-id="3b4ee-105">Názvy metod</span><span class="sxs-lookup"><span data-stu-id="3b4ee-105">Names of Methods</span></span>
 <span data-ttu-id="3b4ee-106">Vzhledem k tomu, že metody jsou způsoby provádění akce, pokyny pro návrh vyžadují, aby názvy metod byly příkazy nebo příkazy.</span><span class="sxs-lookup"><span data-stu-id="3b4ee-106">Because methods are the means of taking action, the design guidelines require that method names be verbs or verb phrases.</span></span> <span data-ttu-id="3b4ee-107">Podle těchto pokynů také slouží k odlišení názvů metod od názvů vlastností a typů, což jsou podstatná jména nebo fráze.</span><span class="sxs-lookup"><span data-stu-id="3b4ee-107">Following this guideline also serves to distinguish method names from property and type names, which are noun or adjective phrases.</span></span>

 <span data-ttu-id="3b4ee-108">✔️ Zadejte názvy metod, které jsou slovesy nebo fráze příkazů.</span><span class="sxs-lookup"><span data-stu-id="3b4ee-108">✔️ DO give methods names that are verbs or verb phrases.</span></span>

```csharp
public class String {
    public int CompareTo(...);
    public string[] Split(...);
    public string Trim();
}
```

## <a name="names-of-properties"></a><span data-ttu-id="3b4ee-109">Názvy vlastností</span><span class="sxs-lookup"><span data-stu-id="3b4ee-109">Names of Properties</span></span>
 <span data-ttu-id="3b4ee-110">Na rozdíl od jiných členů je třeba předávat vlastnosti na jméno nebo název přídavného jména.</span><span class="sxs-lookup"><span data-stu-id="3b4ee-110">Unlike other members, properties should be given noun phrase or adjective names.</span></span> <span data-ttu-id="3b4ee-111">Důvodem je, že vlastnost odkazuje na data a název vlastnosti odráží.</span><span class="sxs-lookup"><span data-stu-id="3b4ee-111">That is because a property refers to data, and the name of the property reflects that.</span></span> <span data-ttu-id="3b4ee-112">PascalCasing se vždycky používá pro názvy vlastností.</span><span class="sxs-lookup"><span data-stu-id="3b4ee-112">PascalCasing is always used for property names.</span></span>

 <span data-ttu-id="3b4ee-113">✔️ pojmenovat vlastnosti s použitím podstatného jména, fráze podstatného jména nebo přídavného jména.</span><span class="sxs-lookup"><span data-stu-id="3b4ee-113">✔️ DO name properties using a noun, noun phrase, or adjective.</span></span>

 <span data-ttu-id="3b4ee-114">❌ nemají vlastnosti, které se shodují s názvem metody Get, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="3b4ee-114">❌ DO NOT have properties that match the name of "Get" methods as in the following example:</span></span>

 <span data-ttu-id="3b4ee-115">`public string TextWriter { get {...} set {...} }` `public string GetTextWriter(int value) { ... }`</span><span class="sxs-lookup"><span data-stu-id="3b4ee-115">`public string TextWriter { get {...} set {...} }` `public string GetTextWriter(int value) { ... }`</span></span>

 <span data-ttu-id="3b4ee-116">Tento model obvykle označuje, že by vlastnost měla být ve skutečnosti metodou.</span><span class="sxs-lookup"><span data-stu-id="3b4ee-116">This pattern typically indicates that the property should really be a method.</span></span>

 <span data-ttu-id="3b4ee-117">✔️ DO vlastností kolekce name pomocí množném fráze popisující položky v kolekci namísto použití fráze v jednotném čísle, za kterou následuje seznam nebo kolekce.</span><span class="sxs-lookup"><span data-stu-id="3b4ee-117">✔️ DO name collection properties with a plural phrase describing the items in the collection instead of using a singular phrase followed by "List" or "Collection".</span></span>

 <span data-ttu-id="3b4ee-118">✔️ Pojmenujte logické vlastnosti s použitím kladné fráze (`CanSeek` namísto `CantSeek`).</span><span class="sxs-lookup"><span data-stu-id="3b4ee-118">✔️ DO name Boolean properties with an affirmative phrase (`CanSeek` instead of `CantSeek`).</span></span> <span data-ttu-id="3b4ee-119">Volitelně můžete také zadat předponu logických vlastností pomocí "is", "Can" nebo "má", ale pouze tam, kde přidá hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3b4ee-119">Optionally, you can also prefix Boolean properties with "Is", "Can", or "Has", but only where it adds value.</span></span>

 <span data-ttu-id="3b4ee-120">✔️ Zvažte vlastnost, která má stejný název jako jeho typ.</span><span class="sxs-lookup"><span data-stu-id="3b4ee-120">✔️ CONSIDER giving a property the same name as its type.</span></span>

 <span data-ttu-id="3b4ee-121">Například následující vlastnost správně získá a nastaví hodnotu výčtu s názvem `Color`, takže vlastnost má název `Color`:</span><span class="sxs-lookup"><span data-stu-id="3b4ee-121">For example, the following property correctly gets and sets an enum value named `Color`, so the property is named `Color`:</span></span>

```csharp
public enum Color {...}
public class Control {
    public Color Color { get {...} set {...} }
}
```

## <a name="names-of-events"></a><span data-ttu-id="3b4ee-122">Názvy událostí</span><span class="sxs-lookup"><span data-stu-id="3b4ee-122">Names of Events</span></span>
 <span data-ttu-id="3b4ee-123">Události vždy odkazují na určitou akci, která se děje, nebo na jednu z nich.</span><span class="sxs-lookup"><span data-stu-id="3b4ee-123">Events always refer to some action, either one that is happening or one that has occurred.</span></span> <span data-ttu-id="3b4ee-124">Proto jako u metod jsou události pojmenovány s příkazy a k označení času vyvolání události se používá příkaz vhodné.</span><span class="sxs-lookup"><span data-stu-id="3b4ee-124">Therefore, as with methods, events are named with verbs, and verb tense is used to indicate the time when the event is raised.</span></span>

 <span data-ttu-id="3b4ee-125">✔️ události s názvem pomocí příkazu nebo fráze.</span><span class="sxs-lookup"><span data-stu-id="3b4ee-125">✔️ DO name events with a verb or a verb phrase.</span></span>

 <span data-ttu-id="3b4ee-126">Příklady zahrnují `Clicked`, `Painting`, `DroppedDown`a tak dále.</span><span class="sxs-lookup"><span data-stu-id="3b4ee-126">Examples include `Clicked`, `Painting`, `DroppedDown`, and so on.</span></span>

 <span data-ttu-id="3b4ee-127">✔️ Přidávejte názvy událostí s konceptem před a po, a to pomocí současného a minulého časů.</span><span class="sxs-lookup"><span data-stu-id="3b4ee-127">✔️ DO give events names with a concept of before and after, using the present and past tenses.</span></span>

 <span data-ttu-id="3b4ee-128">Například událost zavření, která je aktivována před zavřením okna, by byla volána `Closing`a ta, která je aktivována po zavření okna, by byla volána `Closed`.</span><span class="sxs-lookup"><span data-stu-id="3b4ee-128">For example, a close event that is raised before a window is closed would be called `Closing`, and one that is raised after the window is closed would be called `Closed`.</span></span>

 <span data-ttu-id="3b4ee-129">❌ nepoužívat předpony a přípony "Before" nebo "After" k označení před a po událostech.</span><span class="sxs-lookup"><span data-stu-id="3b4ee-129">❌ DO NOT use "Before" or "After" prefixes or postfixes to indicate pre- and post-events.</span></span> <span data-ttu-id="3b4ee-130">Použijte přítomné a dřívější časů, jak je popsáno výše.</span><span class="sxs-lookup"><span data-stu-id="3b4ee-130">Use present and past tenses as just described.</span></span>

 <span data-ttu-id="3b4ee-131">✔️ obslužné rutiny událostí názvů (Delegáti používané jako typy událostí) s příponou EventHandler, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="3b4ee-131">✔️ DO name event handlers (delegates used as types of events) with the "EventHandler" suffix, as shown in the following example:</span></span>

 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`

 <span data-ttu-id="3b4ee-132">✔️ použít dva parametry s názvem `sender` a `e` v obslužných rutinách událostí.</span><span class="sxs-lookup"><span data-stu-id="3b4ee-132">✔️ DO use two parameters named `sender` and `e` in event handlers.</span></span>

 <span data-ttu-id="3b4ee-133">Parametr Sender reprezentuje objekt, který vyvolal událost.</span><span class="sxs-lookup"><span data-stu-id="3b4ee-133">The sender parameter represents the object that raised the event.</span></span> <span data-ttu-id="3b4ee-134">Parametr sender je obvykle typu `object`, a to i v případě, že je možné využít konkrétnější typ.</span><span class="sxs-lookup"><span data-stu-id="3b4ee-134">The sender parameter is typically of type `object`, even if it is possible to employ a more specific type.</span></span>

 <span data-ttu-id="3b4ee-135">✔️ třídy argumentu události názvu s příponou EventArgs.</span><span class="sxs-lookup"><span data-stu-id="3b4ee-135">✔️ DO name event argument classes with the "EventArgs" suffix.</span></span>

## <a name="names-of-fields"></a><span data-ttu-id="3b4ee-136">Názvy polí</span><span class="sxs-lookup"><span data-stu-id="3b4ee-136">Names of Fields</span></span>
 <span data-ttu-id="3b4ee-137">Pokyny pro pojmenovávání polí se vztahují na statická veřejná a chráněná pole.</span><span class="sxs-lookup"><span data-stu-id="3b4ee-137">The field-naming guidelines apply to static public and protected fields.</span></span> <span data-ttu-id="3b4ee-138">Do interních a privátních polí se nevztahují pokyny a v [pokynech návrhu členů](../../../docs/standard/design-guidelines/member.md)nejsou povolena pole veřejné nebo chráněné instance.</span><span class="sxs-lookup"><span data-stu-id="3b4ee-138">Internal and private fields are not covered by guidelines, and public or protected instance fields are not allowed by the [member design guidelines](../../../docs/standard/design-guidelines/member.md).</span></span>

 <span data-ttu-id="3b4ee-139">✔️ používat PascalCasing v názvech polí.</span><span class="sxs-lookup"><span data-stu-id="3b4ee-139">✔️ DO use PascalCasing in field names.</span></span>

 <span data-ttu-id="3b4ee-140">✔️ pole DO pole název s použitím podstatného jména, věty nebo jména.</span><span class="sxs-lookup"><span data-stu-id="3b4ee-140">✔️ DO name fields using a noun, noun phrase, or adjective.</span></span>

 <span data-ttu-id="3b4ee-141">❌ nepoužívejte předponu pro názvy polí.</span><span class="sxs-lookup"><span data-stu-id="3b4ee-141">❌ DO NOT use a prefix for field names.</span></span>

 <span data-ttu-id="3b4ee-142">Například nepoužívejte "g_" nebo "s_" k označení statických polí.</span><span class="sxs-lookup"><span data-stu-id="3b4ee-142">For example, do not use "g_" or "s_" to indicate static fields.</span></span>

 <span data-ttu-id="3b4ee-143">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="3b4ee-143">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="3b4ee-144">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="3b4ee-144">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="3b4ee-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3b4ee-145">See also</span></span>

- [<span data-ttu-id="3b4ee-146">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="3b4ee-146">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="3b4ee-147">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="3b4ee-147">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
