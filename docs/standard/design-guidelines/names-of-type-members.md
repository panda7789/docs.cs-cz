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
author: KrzysztofCwalina
ms.openlocfilehash: b4da14575d29582814d32a3050087b7acc0da802
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353699"
---
# <a name="names-of-type-members"></a><span data-ttu-id="99cd7-102">Názvy členů typu</span><span class="sxs-lookup"><span data-stu-id="99cd7-102">Names of Type Members</span></span>
<span data-ttu-id="99cd7-103">Typy jsou tvořeny členy: metody, vlastnosti, události, konstruktory a pole.</span><span class="sxs-lookup"><span data-stu-id="99cd7-103">Types are made of members: methods, properties, events, constructors, and fields.</span></span> <span data-ttu-id="99cd7-104">Následující části popisují pokyny pro pojmenování členů typu.</span><span class="sxs-lookup"><span data-stu-id="99cd7-104">The following sections describe guidelines for naming type members.</span></span>  
  
## <a name="names-of-methods"></a><span data-ttu-id="99cd7-105">Názvy metod</span><span class="sxs-lookup"><span data-stu-id="99cd7-105">Names of Methods</span></span>  
 <span data-ttu-id="99cd7-106">Vzhledem k tomu, že metody jsou způsoby provádění akce, pokyny pro návrh vyžadují, aby názvy metod byly příkazy nebo příkazy.</span><span class="sxs-lookup"><span data-stu-id="99cd7-106">Because methods are the means of taking action, the design guidelines require that method names be verbs or verb phrases.</span></span> <span data-ttu-id="99cd7-107">Podle těchto pokynů také slouží k odlišení názvů metod od názvů vlastností a typů, což jsou podstatná jména nebo fráze.</span><span class="sxs-lookup"><span data-stu-id="99cd7-107">Following this guideline also serves to distinguish method names from property and type names, which are noun or adjective phrases.</span></span>  
  
 <span data-ttu-id="99cd7-108">**✓ DO** poskytují názvy metod, které jsou, nebo příkaz frází.</span><span class="sxs-lookup"><span data-stu-id="99cd7-108">**✓ DO** give methods names that are verbs or verb phrases.</span></span>  
  
```csharp  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
```  
  
## <a name="names-of-properties"></a><span data-ttu-id="99cd7-109">Názvy vlastností</span><span class="sxs-lookup"><span data-stu-id="99cd7-109">Names of Properties</span></span>  
 <span data-ttu-id="99cd7-110">Na rozdíl od jiných členů je třeba předávat vlastnosti na jméno nebo název přídavného jména.</span><span class="sxs-lookup"><span data-stu-id="99cd7-110">Unlike other members, properties should be given noun phrase or adjective names.</span></span> <span data-ttu-id="99cd7-111">Důvodem je, že vlastnost odkazuje na data a název vlastnosti odráží.</span><span class="sxs-lookup"><span data-stu-id="99cd7-111">That is because a property refers to data, and the name of the property reflects that.</span></span> <span data-ttu-id="99cd7-112">PascalCasing se vždycky používá pro názvy vlastností.</span><span class="sxs-lookup"><span data-stu-id="99cd7-112">PascalCasing is always used for property names.</span></span>  
  
 <span data-ttu-id="99cd7-113">**✓ DO** název vlastnosti pomocí podstatné jméno, podstatné jméno fráze nebo přídavného jména.</span><span class="sxs-lookup"><span data-stu-id="99cd7-113">**✓ DO** name properties using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="99cd7-114">**X DO NOT** mít vlastnosti, které odpovídají názvu metody "Get" jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="99cd7-114">**X DO NOT** have properties that match the name of "Get" methods as in the following example:</span></span>  
  
 `public string TextWriter { get {...} set {...} }`  
 `public string GetTextWriter(int value) { ... }`  
  
 <span data-ttu-id="99cd7-115">Tento model obvykle označuje, že by vlastnost měla být ve skutečnosti metodou.</span><span class="sxs-lookup"><span data-stu-id="99cd7-115">This pattern typically indicates that the property should really be a method.</span></span>  
  
 <span data-ttu-id="99cd7-116">**✓ DO** název vlastnosti kolekce s množném čísle věta popisující položek v kolekci namísto použití singulární frázi "Seznam" nebo "Kolekce."</span><span class="sxs-lookup"><span data-stu-id="99cd7-116">**✓ DO** name collection properties with a plural phrase describing the items in the collection instead of using a singular phrase followed by "List" or "Collection."</span></span>  
  
 <span data-ttu-id="99cd7-117">**✓ DO** název logické vlastnosti s nevyjádřil fráze (`CanSeek` místo `CantSeek`).</span><span class="sxs-lookup"><span data-stu-id="99cd7-117">**✓ DO** name Boolean properties with an affirmative phrase (`CanSeek` instead of `CantSeek`).</span></span> <span data-ttu-id="99cd7-118">Volitelně můžete také zadat předponu logických vlastností pomocí "is", "může" nebo "má", ale pouze tam, kde přidá hodnotu.</span><span class="sxs-lookup"><span data-stu-id="99cd7-118">Optionally, you can also prefix Boolean properties with "Is," "Can," or "Has," but only where it adds value.</span></span>  
  
 <span data-ttu-id="99cd7-119">**✓ CONSIDER** poskytuje vlastnost se stejným názvem jako jeho typu.</span><span class="sxs-lookup"><span data-stu-id="99cd7-119">**✓ CONSIDER** giving a property the same name as its type.</span></span>  
  
 <span data-ttu-id="99cd7-120">Například následující vlastnost správně získá a nastaví hodnotu výčtu s názvem `Color`, takže vlastnost má název `Color`:</span><span class="sxs-lookup"><span data-stu-id="99cd7-120">For example, the following property correctly gets and sets an enum value named `Color`, so the property is named `Color`:</span></span>  
  
```csharp  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## <a name="names-of-events"></a><span data-ttu-id="99cd7-121">Názvy událostí</span><span class="sxs-lookup"><span data-stu-id="99cd7-121">Names of Events</span></span>  
 <span data-ttu-id="99cd7-122">Události vždy odkazují na určitou akci, která se děje, nebo na jednu z nich.</span><span class="sxs-lookup"><span data-stu-id="99cd7-122">Events always refer to some action, either one that is happening or one that has occurred.</span></span> <span data-ttu-id="99cd7-123">Proto jako u metod jsou události pojmenovány s příkazy a k označení času vyvolání události se používá příkaz vhodné.</span><span class="sxs-lookup"><span data-stu-id="99cd7-123">Therefore, as with methods, events are named with verbs, and verb tense is used to indicate the time when the event is raised.</span></span>  
  
 <span data-ttu-id="99cd7-124">**✓ DO** název události operaci nebo operace frází.</span><span class="sxs-lookup"><span data-stu-id="99cd7-124">**✓ DO** name events with a verb or a verb phrase.</span></span>  
  
 <span data-ttu-id="99cd7-125">Příklady zahrnují `Clicked`, `Painting`, `DroppedDown`a tak dále.</span><span class="sxs-lookup"><span data-stu-id="99cd7-125">Examples include `Clicked`, `Painting`, `DroppedDown`, and so on.</span></span>  
  
 <span data-ttu-id="99cd7-126">**✓ DO** pojmenovat události s koncept před a po ní, pomocí k dispozici a rodu minulosti.</span><span class="sxs-lookup"><span data-stu-id="99cd7-126">**✓ DO** give events names with a concept of before and after, using the present and past tenses.</span></span>  
  
 <span data-ttu-id="99cd7-127">Například událost zavření, která je aktivována před zavřením okna, by byla volána `Closing`a ta, která je aktivována po zavření okna, by byla volána `Closed`.</span><span class="sxs-lookup"><span data-stu-id="99cd7-127">For example, a close event that is raised before a window is closed would be called `Closing`, and one that is raised after the window is closed would be called `Closed`.</span></span>  
  
 <span data-ttu-id="99cd7-128">**X DO NOT** použijte "Before" nebo "After" předpony nebo postfixes udávajících před a po událostech.</span><span class="sxs-lookup"><span data-stu-id="99cd7-128">**X DO NOT** use "Before" or "After" prefixes or postfixes to indicate pre- and post-events.</span></span> <span data-ttu-id="99cd7-129">Použijte přítomné a dřívější časů, jak je popsáno výše.</span><span class="sxs-lookup"><span data-stu-id="99cd7-129">Use present and past tenses as just described.</span></span>  
  
 <span data-ttu-id="99cd7-130">**✓ DO** název s příponou "EventHandler" obslužné rutiny události (delegáty používané jako typy událostí), jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="99cd7-130">**✓ DO** name event handlers (delegates used as types of events) with the "EventHandler" suffix, as shown in the following example:</span></span>  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 <span data-ttu-id="99cd7-131">**✓ DO** použití dvou parametrů s názvem `sender` a `e` v obslužných rutinách událostí.</span><span class="sxs-lookup"><span data-stu-id="99cd7-131">**✓ DO** use two parameters named `sender` and `e` in event handlers.</span></span>  
  
 <span data-ttu-id="99cd7-132">Parametr Sender reprezentuje objekt, který vyvolal událost.</span><span class="sxs-lookup"><span data-stu-id="99cd7-132">The sender parameter represents the object that raised the event.</span></span> <span data-ttu-id="99cd7-133">Parametr sender je obvykle typu `object`, a to i v případě, že je možné využít konkrétnější typ.</span><span class="sxs-lookup"><span data-stu-id="99cd7-133">The sender parameter is typically of type `object`, even if it is possible to employ a more specific type.</span></span>  
  
 <span data-ttu-id="99cd7-134">**✓ DO** pojmenujte událost třídy argument s příponou "EventArgs".</span><span class="sxs-lookup"><span data-stu-id="99cd7-134">**✓ DO** name event argument classes with the "EventArgs" suffix.</span></span>  
  
## <a name="names-of-fields"></a><span data-ttu-id="99cd7-135">Názvy polí</span><span class="sxs-lookup"><span data-stu-id="99cd7-135">Names of Fields</span></span>  
 <span data-ttu-id="99cd7-136">Pokyny pro pojmenovávání polí se vztahují na statická veřejná a chráněná pole.</span><span class="sxs-lookup"><span data-stu-id="99cd7-136">The field-naming guidelines apply to static public and protected fields.</span></span> <span data-ttu-id="99cd7-137">Do interních a privátních polí se nevztahují pokyny a v [pokynech návrhu členů](../../../docs/standard/design-guidelines/member.md)nejsou povolena pole veřejné nebo chráněné instance.</span><span class="sxs-lookup"><span data-stu-id="99cd7-137">Internal and private fields are not covered by guidelines, and public or protected instance fields are not allowed by the [member design guidelines](../../../docs/standard/design-guidelines/member.md).</span></span>  
  
 <span data-ttu-id="99cd7-138">**✓ DO** použít PascalCasing v názvech polí.</span><span class="sxs-lookup"><span data-stu-id="99cd7-138">**✓ DO** use PascalCasing in field names.</span></span>  
  
 <span data-ttu-id="99cd7-139">**✓ DO** pojmenovat pole pomocí podstatné jméno, podstatné jméno fráze nebo přídavného jména.</span><span class="sxs-lookup"><span data-stu-id="99cd7-139">**✓ DO** name fields using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="99cd7-140">**X DO NOT** použijte předponu pro názvy polí.</span><span class="sxs-lookup"><span data-stu-id="99cd7-140">**X DO NOT** use a prefix for field names.</span></span>  
  
 <span data-ttu-id="99cd7-141">Například nepoužívejte "g_" nebo "s_" k označení statických polí.</span><span class="sxs-lookup"><span data-stu-id="99cd7-141">For example, do not use "g_" or "s_" to indicate static fields.</span></span>  
  
 <span data-ttu-id="99cd7-142">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="99cd7-142">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="99cd7-143">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="99cd7-143">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99cd7-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="99cd7-144">See also</span></span>

- [<span data-ttu-id="99cd7-145">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="99cd7-145">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="99cd7-146">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="99cd7-146">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
