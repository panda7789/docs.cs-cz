---
title: Názvy tříd, struktur a rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- type names, guidelines
- classes [.NET Framework], names
- enumerations [.NET Framework], names
- names [.NET Framework], interfaces
- common type names
- names [.NET Framework], type names
- names [.NET Framework], classes
- interfaces [.NET Framework], names
- generic type parameters
ms.assetid: 87a4b0da-ed64-43b1-ac43-968576c444ce
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f60a2283c01d0dc2665dafaa99ea52000aa3bc47
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42931204"
---
# <a name="names-of-classes-structs-and-interfaces"></a><span data-ttu-id="c7f06-102">Názvy tříd, struktur a rozhraní</span><span class="sxs-lookup"><span data-stu-id="c7f06-102">Names of Classes, Structs, and Interfaces</span></span>
<span data-ttu-id="c7f06-103">Pokyny pro pojmenování, které následují platí pro pojmenování obecného typu.</span><span class="sxs-lookup"><span data-stu-id="c7f06-103">The naming guidelines that follow apply to general type naming.</span></span>  
  
 <span data-ttu-id="c7f06-104">**✓ DO** název třídy a struktury s podstatná jména či fráze podstatné jméno, pomocí PascalCasing.</span><span class="sxs-lookup"><span data-stu-id="c7f06-104">**✓ DO** name classes and structs with nouns or noun phrases, using PascalCasing.</span></span>  
  
 <span data-ttu-id="c7f06-105">Názvy typů to odlišuje od metody, které jsou pojmenovány příkaz Možnosti.</span><span class="sxs-lookup"><span data-stu-id="c7f06-105">This distinguishes type names from methods, which are named with verb phrases.</span></span>  
  
 <span data-ttu-id="c7f06-106">**✓ DO** název rozhraní tvary přídavných jmen fráze nebo příležitostně s podstatná jména či fráze podstatné jméno.</span><span class="sxs-lookup"><span data-stu-id="c7f06-106">**✓ DO** name interfaces with adjective phrases, or occasionally with nouns or noun phrases.</span></span>  
  
 <span data-ttu-id="c7f06-107">Podstatná jména a frází podstatné jméno by měl používat jen zřídka a může znamenat, že typ musí být abstraktní třída a není rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c7f06-107">Nouns and noun phrases should be used rarely and they might indicate that the type should be an abstract class, and not an interface.</span></span>  
  
 <span data-ttu-id="c7f06-108">**X DO NOT** poskytnout názvy tříd předpona (například "C").</span><span class="sxs-lookup"><span data-stu-id="c7f06-108">**X DO NOT** give class names a prefix (e.g., "C").</span></span>  
  
 <span data-ttu-id="c7f06-109">**✓ CONSIDER** ukončení název odvozené třídy s názvem základní třídy.</span><span class="sxs-lookup"><span data-stu-id="c7f06-109">**✓ CONSIDER** ending the name of derived classes with the name of the base class.</span></span>  
  
 <span data-ttu-id="c7f06-110">To je velmi čitelný a jasně vysvětluje relace.</span><span class="sxs-lookup"><span data-stu-id="c7f06-110">This is very readable and explains the relationship clearly.</span></span> <span data-ttu-id="c7f06-111">Tady je několik příkladů tohoto kódu: `ArgumentOutOfRangeException`, což je typ z `Exception`, a `SerializableAttribute`, což je typ z `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="c7f06-111">Some examples of this in code are: `ArgumentOutOfRangeException`, which is a kind of `Exception`, and `SerializableAttribute`, which is a kind of `Attribute`.</span></span> <span data-ttu-id="c7f06-112">Je však potřeba použít přiměřené rozhodnutí při uplatňování toto pravidlo; například `Button` třída je typ z `Control` události, i když `Control` nezobrazí ve svém názvu.</span><span class="sxs-lookup"><span data-stu-id="c7f06-112">However, it is important to use reasonable judgment in applying this guideline; for example, the `Button` class is a kind of `Control` event, although `Control` doesn’t appear in its name.</span></span>  
  
 <span data-ttu-id="c7f06-113">**✓ DO** předponu rozhraní názvy písmenem I, že je typ rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c7f06-113">**✓ DO** prefix interface names with the letter I, to indicate that the type is an interface.</span></span>  
  
 <span data-ttu-id="c7f06-114">Například `IComponent` (popisná podstatná) `ICustomAttributeProvider` (podstatné jméno fráze), a `IPersistable` (přídavného jména) jsou názvy odpovídající rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c7f06-114">For example, `IComponent` (descriptive noun), `ICustomAttributeProvider` (noun phrase), and `IPersistable` (adjective) are appropriate interface names.</span></span> <span data-ttu-id="c7f06-115">Stejně jako jiné názvy typů se vyhněte zkratky.</span><span class="sxs-lookup"><span data-stu-id="c7f06-115">As with other type names, avoid abbreviations.</span></span>  
  
 <span data-ttu-id="c7f06-116">**✓ DO** Ujistěte se, že názvy liší pouze pomocí "I" předpony na název rozhraní při definování pár třída – rozhraní, kde třída je standardní implementace rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c7f06-116">**✓ DO** ensure that the names differ only by the "I" prefix on the interface name when you are defining a class–interface pair where the class is a standard implementation of the interface.</span></span>  
  
## <a name="names-of-generic-type-parameters"></a><span data-ttu-id="c7f06-117">Názvy parametrů obecného typu</span><span class="sxs-lookup"><span data-stu-id="c7f06-117">Names of Generic Type Parameters</span></span>  
 <span data-ttu-id="c7f06-118">Obecné typy byly přidány do rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="c7f06-118">Generics were added to .NET Framework 2.0.</span></span> <span data-ttu-id="c7f06-119">Funkce zavedená nová druh identifikátor s názvem *parametr typu*.</span><span class="sxs-lookup"><span data-stu-id="c7f06-119">The feature introduced a new kind of identifier called *type parameter*.</span></span>  
  
 <span data-ttu-id="c7f06-120">**✓ DO** název parametry obecného typu pomocí popisných názvů, pokud je název jednoho písmeno úplně není potřeba vysvětlovat a popisný název nebude přidejte hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c7f06-120">**✓ DO** name generic type parameters with descriptive names unless a single-letter name is completely self-explanatory and a descriptive name would not add value.</span></span>  
  
 <span data-ttu-id="c7f06-121">**✓ CONSIDER** pomocí `T` jako název typu parametru pro typy s jeden parametr typu jedním písmenem.</span><span class="sxs-lookup"><span data-stu-id="c7f06-121">**✓ CONSIDER** using `T` as the type parameter name for types with one single-letter type parameter.</span></span>  
  
```  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 <span data-ttu-id="c7f06-122">**✓ DO** předpony typ popisné názvy parametrů s `T`.</span><span class="sxs-lookup"><span data-stu-id="c7f06-122">**✓ DO** prefix descriptive type parameter names with `T`.</span></span>  
  
```  
public interface ISessionChannel<TSession> where TSession : ISession {  
    TSession Session { get; }  
}  
```  
  
 <span data-ttu-id="c7f06-123">**✓ CONSIDER** označující omezení vztahujících se na parametr typu názvu parametru.</span><span class="sxs-lookup"><span data-stu-id="c7f06-123">**✓ CONSIDER** indicating constraints placed on a type parameter in the name of the parameter.</span></span>  
  
 <span data-ttu-id="c7f06-124">Například s omezením parametru `ISession` může být volána `TSession`.</span><span class="sxs-lookup"><span data-stu-id="c7f06-124">For example, a parameter constrained to `ISession` might be called `TSession`.</span></span>  
  
## <a name="names-of-common-types"></a><span data-ttu-id="c7f06-125">Názvy běžných typů</span><span class="sxs-lookup"><span data-stu-id="c7f06-125">Names of Common Types</span></span>  
 <span data-ttu-id="c7f06-126">**✓ DO** postupujte podle pokynů popsaných v následující tabulce, při pojmenování typy odvozené od nebo implementaci určitých typů rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c7f06-126">**✓ DO** follow the guidelines described in the following table when naming types derived from or implementing certain .NET Framework types.</span></span>  
  
|<span data-ttu-id="c7f06-127">Základní typ</span><span class="sxs-lookup"><span data-stu-id="c7f06-127">Base Type</span></span>|<span data-ttu-id="c7f06-128">Pravidlo typu odvozené/implementace</span><span class="sxs-lookup"><span data-stu-id="c7f06-128">Derived/Implementing Type Guideline</span></span>|  
|---------------|------------------------------------------|  
|`System.Attribute`|<span data-ttu-id="c7f06-129">**✓ DO** přidat příponu "Atribut" názvy vlastních atributů tříd.</span><span class="sxs-lookup"><span data-stu-id="c7f06-129">**✓ DO** add the suffix "Attribute" to names of custom attribute classes.</span></span>|  
|`System.Delegate`|<span data-ttu-id="c7f06-130">**✓ DO** přidat příponu "Obslužná rutina události" na názvy delegáti, které se používají v události.</span><span class="sxs-lookup"><span data-stu-id="c7f06-130">**✓ DO** add the suffix "EventHandler" to names of delegates that are used in events.</span></span><br /><br /> <span data-ttu-id="c7f06-131">**✓ DO** přidat příponu "Zpětné volání" pro názvy delegátů kromě těch, které používá jako obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="c7f06-131">**✓ DO** add the suffix "Callback" to names of delegates other than those used as event handlers.</span></span><br /><br /> <span data-ttu-id="c7f06-132">**X DO NOT** přidat příponu "Delegáta" s delegátem.</span><span class="sxs-lookup"><span data-stu-id="c7f06-132">**X DO NOT** add the suffix "Delegate" to a delegate.</span></span>|  
|`System.EventArgs`|<span data-ttu-id="c7f06-133">**✓ DO** přidat příponu "EventArgs."</span><span class="sxs-lookup"><span data-stu-id="c7f06-133">**✓ DO** add the suffix "EventArgs."</span></span>|  
|`System.Enum`|<span data-ttu-id="c7f06-134">**X DO NOT** odvozovat z této třídy; použijte – klíčové slovo jazyka nepodporuje místo toho, například v jazyce C#, použít `enum` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="c7f06-134">**X DO NOT** derive from this class; use the keyword supported by your language instead; for example, in C#, use the `enum` keyword.</span></span><br /><br /> <span data-ttu-id="c7f06-135">**X DO NOT** přidat příponu "Výčtu" nebo "Příznak."</span><span class="sxs-lookup"><span data-stu-id="c7f06-135">**X DO NOT** add the suffix "Enum" or "Flag."</span></span>|  
|`System.Exception`|<span data-ttu-id="c7f06-136">**✓ DO** přidat příponu "Výjimky."</span><span class="sxs-lookup"><span data-stu-id="c7f06-136">**✓ DO** add the suffix "Exception."</span></span>|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|<span data-ttu-id="c7f06-137">**✓ DO** přidat příponu "Slovník."</span><span class="sxs-lookup"><span data-stu-id="c7f06-137">**✓ DO** add the suffix "Dictionary."</span></span> <span data-ttu-id="c7f06-138">Všimněte si, že `IDictionary` je určitý typ kolekce, ale toto pravidlo má přednost před více obecných pokynů kolekce, který následuje.</span><span class="sxs-lookup"><span data-stu-id="c7f06-138">Note that `IDictionary` is a specific type of collection, but this guideline takes precedence over the more general collections guideline that follows.</span></span>|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|<span data-ttu-id="c7f06-139">**✓ DO** přidat příponu "Kolekce."</span><span class="sxs-lookup"><span data-stu-id="c7f06-139">**✓ DO** add the suffix "Collection."</span></span>|  
|`System.IO.Stream`|<span data-ttu-id="c7f06-140">**✓ DO** přidat příponu "Stream."</span><span class="sxs-lookup"><span data-stu-id="c7f06-140">**✓ DO** add the suffix "Stream."</span></span>|  
|`CodeAccessPermission IPermission`|<span data-ttu-id="c7f06-141">**✓ DO** přidat příponu "Oprávnění."</span><span class="sxs-lookup"><span data-stu-id="c7f06-141">**✓ DO** add the suffix "Permission."</span></span>|  
  
## <a name="naming-enumerations"></a><span data-ttu-id="c7f06-142">Názvy výčtů</span><span class="sxs-lookup"><span data-stu-id="c7f06-142">Naming Enumerations</span></span>  
 <span data-ttu-id="c7f06-143">Názvy typů výčtu (také nazývané výčtů) obecně by měla dodržovat standardní pojmenování typ pravidla (PascalCasing atd.).</span><span class="sxs-lookup"><span data-stu-id="c7f06-143">Names of enumeration types (also called enums) in general should follow the standard type-naming rules (PascalCasing, etc.).</span></span> <span data-ttu-id="c7f06-144">Existují však další pokyny, které platí konkrétně pro výčty.</span><span class="sxs-lookup"><span data-stu-id="c7f06-144">However, there are additional guidelines that apply specifically to enums.</span></span>  
  
 <span data-ttu-id="c7f06-145">**✓ DO** použijte název singulární typ výčtu pouze v případě jeho hodnoty jsou bitová pole.</span><span class="sxs-lookup"><span data-stu-id="c7f06-145">**✓ DO** use a singular type name for an enumeration unless its values are bit fields.</span></span>  
  
 <span data-ttu-id="c7f06-146">**✓ DO** použijte název množném čísle typ výčtu s bitových polí jako hodnoty, označované taky jako příznaky výčtu.</span><span class="sxs-lookup"><span data-stu-id="c7f06-146">**✓ DO** use a plural type name for an enumeration with bit fields as values, also called flags enum.</span></span>  
  
 <span data-ttu-id="c7f06-147">**X DO NOT** používají příponu "Výčtu" v názvech typ výčtu.</span><span class="sxs-lookup"><span data-stu-id="c7f06-147">**X DO NOT** use an "Enum" suffix in enum type names.</span></span>  
  
 <span data-ttu-id="c7f06-148">**X DO NOT** použijte "Příznak" nebo "Příznaky" přípony ve výčtu zadejte názvy.</span><span class="sxs-lookup"><span data-stu-id="c7f06-148">**X DO NOT** use "Flag" or "Flags" suffixes in enum type names.</span></span>  
  
 <span data-ttu-id="c7f06-149">**X DO NOT** použijte předponu na názvy hodnot výčtu (například "ad" pro výčty ADO.), "rtf" pro výčty RTF atd.</span><span class="sxs-lookup"><span data-stu-id="c7f06-149">**X DO NOT** use a prefix on enumeration value names (e.g., "ad" for ADO enums, "rtf" for rich text enums, etc.).</span></span>  
  
 <span data-ttu-id="c7f06-150">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="c7f06-150">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="c7f06-151">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="c7f06-151">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7f06-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7f06-152">See Also</span></span>  
 [<span data-ttu-id="c7f06-153">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="c7f06-153">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="c7f06-154">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="c7f06-154">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
