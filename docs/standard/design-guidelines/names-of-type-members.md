---
title: "Názvy členy typu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1a3460b734d5bab6f5362fa9d3631e06821f6d49
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="names-of-type-members"></a><span data-ttu-id="427c7-102">Názvy členy typu</span><span class="sxs-lookup"><span data-stu-id="427c7-102">Names of Type Members</span></span>
<span data-ttu-id="427c7-103">Typy jsou vytvářeny členů: metody, vlastnosti, události, konstruktory a pole.</span><span class="sxs-lookup"><span data-stu-id="427c7-103">Types are made of members: methods, properties, events, constructors, and fields.</span></span> <span data-ttu-id="427c7-104">Následující části popisují pokyny pro pojmenování členy typu.</span><span class="sxs-lookup"><span data-stu-id="427c7-104">The following sections describe guidelines for naming type members.</span></span>  
  
## <a name="names-of-methods"></a><span data-ttu-id="427c7-105">Názvy metod</span><span class="sxs-lookup"><span data-stu-id="427c7-105">Names of Methods</span></span>  
 <span data-ttu-id="427c7-106">Vzhledem k tomu, že jsou metody způsob akce, pokynů pro návrh vyžadují, aby metoda názvy příkazy nebo akce frází.</span><span class="sxs-lookup"><span data-stu-id="427c7-106">Because methods are the means of taking action, the design guidelines require that method names be verbs or verb phrases.</span></span> <span data-ttu-id="427c7-107">Toto platí také následující slouží k rozlišení názvů metoda z vlastnost a zadejte názvy, které jsou podstatné jméno a přídavných jmen frází.</span><span class="sxs-lookup"><span data-stu-id="427c7-107">Following this guideline also serves to distinguish method names from property and type names, which are noun or adjective phrases.</span></span>  
  
 <span data-ttu-id="427c7-108">**PROVEĎTE ✓** zadejte název metody, které jsou, nebo příkaz frází.</span><span class="sxs-lookup"><span data-stu-id="427c7-108">**✓ DO** give methods names that are verbs or verb phrases.</span></span>  
  
```  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
```  
  
## <a name="names-of-properties"></a><span data-ttu-id="427c7-109">Názvy vlastností</span><span class="sxs-lookup"><span data-stu-id="427c7-109">Names of Properties</span></span>  
 <span data-ttu-id="427c7-110">Na rozdíl od jiných členů by měly mít vlastnosti frázi podstatné jméno nebo tvary přídavných jmen názvy.</span><span class="sxs-lookup"><span data-stu-id="427c7-110">Unlike other members, properties should be given noun phrase or adjective names.</span></span> <span data-ttu-id="427c7-111">Je to způsobeno odkazuje vlastnost k datům a název vlastnosti, která odráží.</span><span class="sxs-lookup"><span data-stu-id="427c7-111">That is because a property refers to data, and the name of the property reflects that.</span></span> <span data-ttu-id="427c7-112">PascalCasing se vždy používá pro názvy vlastností.</span><span class="sxs-lookup"><span data-stu-id="427c7-112">PascalCasing is always used for property names.</span></span>  
  
 <span data-ttu-id="427c7-113">**PROVEĎTE ✓** název vlastnosti pomocí podstatné jméno, heslo podstatné jméno nebo přídavných jmen.</span><span class="sxs-lookup"><span data-stu-id="427c7-113">**✓ DO** name properties using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="427c7-114">**X nesmí** mít vlastnosti, které odpovídají názvu metody "Get" jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="427c7-114">**X DO NOT** have properties that match the name of "Get" methods as in the following example:</span></span>  
  
 `public string TextWriter { get {...} set {...} }`  
 `public string GetTextWriter(int value) { ... }`  
  
 <span data-ttu-id="427c7-115">Tento vzor obvykle označuje vlastnost by měla být skutečně metodu.</span><span class="sxs-lookup"><span data-stu-id="427c7-115">This pattern typically indicates that the property should really be a method.</span></span>  
  
 <span data-ttu-id="427c7-116">**PROVEĎTE ✓** název vlastnosti v kolekci s množném čísle frázi popisující položky v kolekci místo použití singulární frázi následuje "seznam" nebo "Kolekce."</span><span class="sxs-lookup"><span data-stu-id="427c7-116">**✓ DO** name collection properties with a plural phrase describing the items in the collection instead of using a singular phrase followed by "List" or "Collection."</span></span>  
  
 <span data-ttu-id="427c7-117">**PROVEĎTE ✓** název logické vlastnosti s kladných frázi (`CanSeek` místo `CantSeek`).</span><span class="sxs-lookup"><span data-stu-id="427c7-117">**✓ DO** name Boolean properties with an affirmative phrase (`CanSeek` instead of `CantSeek`).</span></span> <span data-ttu-id="427c7-118">Volitelně můžete také předpony logická hodnota vlastnosti s "Je", "můžete" nebo "Má" ale pouze tam, kde se přidá hodnotu.</span><span class="sxs-lookup"><span data-stu-id="427c7-118">Optionally, you can also prefix Boolean properties with "Is," "Can," or "Has," but only where it adds value.</span></span>  
  
 <span data-ttu-id="427c7-119">**✓ ZVAŽTE** poskytnutí stejný název jako typ vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="427c7-119">**✓ CONSIDER** giving a property the same name as its type.</span></span>  
  
 <span data-ttu-id="427c7-120">Například následující vlastnost správně získá a nastaví hodnotu výčtu s názvem `Color`, takže je název vlastnosti `Color`:</span><span class="sxs-lookup"><span data-stu-id="427c7-120">For example, the following property correctly gets and sets an enum value named `Color`, so the property is named `Color`:</span></span>  
  
```  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## <a name="names-of-events"></a><span data-ttu-id="427c7-121">Názvy událostí</span><span class="sxs-lookup"><span data-stu-id="427c7-121">Names of Events</span></span>  
 <span data-ttu-id="427c7-122">Události se vždy odkazují na některé akce, a to buď jednu, která je situaci nebo ten, který došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="427c7-122">Events always refer to some action, either one that is happening or one that has occurred.</span></span> <span data-ttu-id="427c7-123">Stejně jako u metody, proto události jsou pojmenované s příkazy a slovesného příkaz času slouží k označení doby, kdy je vyvolána událost.</span><span class="sxs-lookup"><span data-stu-id="427c7-123">Therefore, as with methods, events are named with verbs, and verb tense is used to indicate the time when the event is raised.</span></span>  
  
 <span data-ttu-id="427c7-124">**PROVEĎTE ✓** název události s operaci nebo frázi operaci.</span><span class="sxs-lookup"><span data-stu-id="427c7-124">**✓ DO** name events with a verb or a verb phrase.</span></span>  
  
 <span data-ttu-id="427c7-125">Mezi příklady patří `Clicked`, `Painting`, `DroppedDown`a tak dále.</span><span class="sxs-lookup"><span data-stu-id="427c7-125">Examples include `Clicked`, `Painting`, `DroppedDown`, and so on.</span></span>  
  
 <span data-ttu-id="427c7-126">**PROVEĎTE ✓** zadejte název události s koncept před a po, pomocí přítomen a časů v minulosti.</span><span class="sxs-lookup"><span data-stu-id="427c7-126">**✓ DO** give events names with a concept of before and after, using the present and past tenses.</span></span>  
  
 <span data-ttu-id="427c7-127">Například by názvem zavřít událost, která je vyvolána před zavřením okna `Closing`, a ten, který je vyvolána po zavření okna by se volat `Closed`.</span><span class="sxs-lookup"><span data-stu-id="427c7-127">For example, a close event that is raised before a window is closed would be called `Closing`, and one that is raised after the window is closed would be called `Closed`.</span></span>  
  
 <span data-ttu-id="427c7-128">**X nesmí** použijte "Před" nebo "Po" předpony nebo postfixes k označení před a po události.</span><span class="sxs-lookup"><span data-stu-id="427c7-128">**X DO NOT** use "Before" or "After" prefixes or postfixes to indicate pre- and post-events.</span></span> <span data-ttu-id="427c7-129">Použití přítomen a časy minulosti jako právě popsané.</span><span class="sxs-lookup"><span data-stu-id="427c7-129">Use present and past tenses as just described.</span></span>  
  
 <span data-ttu-id="427c7-130">**PROVEĎTE ✓** název obslužné rutiny událostí (delegáti používat jako typy událostí) s příponou "Obslužná rutina události", jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="427c7-130">**✓ DO** name event handlers (delegates used as types of events) with the "EventHandler" suffix, as shown in the following example:</span></span>  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 <span data-ttu-id="427c7-131">**PROVEĎTE ✓** použít dva parametry s názvem `sender` a `e` v obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="427c7-131">**✓ DO** use two parameters named `sender` and `e` in event handlers.</span></span>  
  
 <span data-ttu-id="427c7-132">Parametr odesílatele představuje objekt, který vyvolá událost.</span><span class="sxs-lookup"><span data-stu-id="427c7-132">The sender parameter represents the object that raised the event.</span></span> <span data-ttu-id="427c7-133">Parametr odesílatele je obvykle typu `object`i v případě, že je možné využívat více konkrétního typu.</span><span class="sxs-lookup"><span data-stu-id="427c7-133">The sender parameter is typically of type `object`, even if it is possible to employ a more specific type.</span></span>  
  
 <span data-ttu-id="427c7-134">**PROVEĎTE ✓** název události třídy argument s příponou "EventArgs".</span><span class="sxs-lookup"><span data-stu-id="427c7-134">**✓ DO** name event argument classes with the "EventArgs" suffix.</span></span>  
  
## <a name="names-of-fields"></a><span data-ttu-id="427c7-135">Názvy polí</span><span class="sxs-lookup"><span data-stu-id="427c7-135">Names of Fields</span></span>  
 <span data-ttu-id="427c7-136">Pole názvy pokyny se vztahují k statických polí veřejné a chráněné.</span><span class="sxs-lookup"><span data-stu-id="427c7-136">The field-naming guidelines apply to static public and protected fields.</span></span> <span data-ttu-id="427c7-137">Interní a privátní pole nejsou předmětem pokyny a veřejné nebo chráněné instance pole nejsou povoleny [pokynů pro návrh člen](../../../docs/standard/design-guidelines/member.md).</span><span class="sxs-lookup"><span data-stu-id="427c7-137">Internal and private fields are not covered by guidelines, and public or protected instance fields are not allowed by the [member design guidelines](../../../docs/standard/design-guidelines/member.md).</span></span>  
  
 <span data-ttu-id="427c7-138">**PROVEĎTE ✓** použít PascalCasing v názvech polí.</span><span class="sxs-lookup"><span data-stu-id="427c7-138">**✓ DO** use PascalCasing in field names.</span></span>  
  
 <span data-ttu-id="427c7-139">**PROVEĎTE ✓** název pole pomocí podstatné jméno, heslo podstatné jméno nebo přídavných jmen.</span><span class="sxs-lookup"><span data-stu-id="427c7-139">**✓ DO** name fields using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="427c7-140">**X nesmí** použijte předponu pro názvy polí.</span><span class="sxs-lookup"><span data-stu-id="427c7-140">**X DO NOT** use a prefix for field names.</span></span>  
  
 <span data-ttu-id="427c7-141">Nepoužívejte například "g_" nebo "s_" k označení statických polí.</span><span class="sxs-lookup"><span data-stu-id="427c7-141">For example, do not use "g_" or "s_" to indicate static fields.</span></span>  
  
 <span data-ttu-id="427c7-142">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="427c7-142">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="427c7-143">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="427c7-143">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="427c7-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="427c7-144">See Also</span></span>  
 [<span data-ttu-id="427c7-145">Pokyny pro návrh Framework</span><span class="sxs-lookup"><span data-stu-id="427c7-145">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="427c7-146">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="427c7-146">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
