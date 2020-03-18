---
title: Názvy tříd, struktur a rozhraní
ms.date: 10/22/2008
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
ms.openlocfilehash: 2c528348c0e84037a80df9797c56f03b51c73adc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400594"
---
# <a name="names-of-classes-structs-and-interfaces"></a><span data-ttu-id="8c87d-102">Názvy tříd, struktur a rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c87d-102">Names of Classes, Structs, and Interfaces</span></span>
<span data-ttu-id="8c87d-103">Následující pokyny pro pojmenování platí pro obecné pojmenování typu.</span><span class="sxs-lookup"><span data-stu-id="8c87d-103">The naming guidelines that follow apply to general type naming.</span></span>

 <span data-ttu-id="8c87d-104">✔️ do name třídy a struktury s návěsy nebo fráze užitkových jmen, pomocí PascalCasing.</span><span class="sxs-lookup"><span data-stu-id="8c87d-104">✔️ DO name classes and structs with nouns or noun phrases, using PascalCasing.</span></span>

 <span data-ttu-id="8c87d-105">Tím se odlišují názvy typů od metod, které jsou pojmenovány s lovesnými frázemi.</span><span class="sxs-lookup"><span data-stu-id="8c87d-105">This distinguishes type names from methods, which are named with verb phrases.</span></span>

 <span data-ttu-id="8c87d-106">✔️ do název rozhraní s přídavnými jmény, nebo občas s přídavnými jmény nebo fráze z rozmene.</span><span class="sxs-lookup"><span data-stu-id="8c87d-106">✔️ DO name interfaces with adjective phrases, or occasionally with nouns or noun phrases.</span></span>

 <span data-ttu-id="8c87d-107">Fráze se zápojem a beznosná označení by měla být používána zřídka a mohou označovat, že typ by měl být abstraktní třídou, nikoli rozhraním.</span><span class="sxs-lookup"><span data-stu-id="8c87d-107">Nouns and noun phrases should be used rarely and they might indicate that the type should be an abstract class, and not an interface.</span></span>

 <span data-ttu-id="8c87d-108">❌Nedávejte názvy tříd předponu (např.</span><span class="sxs-lookup"><span data-stu-id="8c87d-108">❌ DO NOT give class names a prefix (e.g., "C").</span></span>

 <span data-ttu-id="8c87d-109">✔️ ZVAŽTe ukončení názvu odvozených tříd názvem základní třídy.</span><span class="sxs-lookup"><span data-stu-id="8c87d-109">✔️ CONSIDER ending the name of derived classes with the name of the base class.</span></span>

 <span data-ttu-id="8c87d-110">To je velmi čitelné a vysvětluje vztah jasně.</span><span class="sxs-lookup"><span data-stu-id="8c87d-110">This is very readable and explains the relationship clearly.</span></span> <span data-ttu-id="8c87d-111">Některé příklady tohoto v `ArgumentOutOfRangeException`kódu jsou: , `Exception`což `SerializableAttribute`je druh , `Attribute`a , což je druh .</span><span class="sxs-lookup"><span data-stu-id="8c87d-111">Some examples of this in code are: `ArgumentOutOfRangeException`, which is a kind of `Exception`, and `SerializableAttribute`, which is a kind of `Attribute`.</span></span> <span data-ttu-id="8c87d-112">Při uplatňování těchto pokynů je však důležité použít přiměřený úsudek; například `Button` třída je druh `Control` události, `Control` i když se nezobrazí v jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="8c87d-112">However, it is important to use reasonable judgment in applying this guideline; for example, the `Button` class is a kind of `Control` event, although `Control` doesn’t appear in its name.</span></span>

 <span data-ttu-id="8c87d-113">✔️ názvy předpony rozhraní DO s písmenem I, což znamená, že typ je rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8c87d-113">✔️ DO prefix interface names with the letter I, to indicate that the type is an interface.</span></span>

 <span data-ttu-id="8c87d-114">Například `IComponent` (popisné jméno), `ICustomAttributeProvider` (fráze nosného `IPersistable` jména) a (přídavné jméno) jsou vhodné názvy rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8c87d-114">For example, `IComponent` (descriptive noun), `ICustomAttributeProvider` (noun phrase), and `IPersistable` (adjective) are appropriate interface names.</span></span> <span data-ttu-id="8c87d-115">Stejně jako u jiných názvů typů se vyhněte zkratkám.</span><span class="sxs-lookup"><span data-stu-id="8c87d-115">As with other type names, avoid abbreviations.</span></span>

 <span data-ttu-id="8c87d-116">✔️ do ujistěte se, že názvy se liší pouze předponou "I" na název rozhraní při definování dvojice třídy rozhraní, kde třída je standardní implementace rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8c87d-116">✔️ DO ensure that the names differ only by the "I" prefix on the interface name when you are defining a class–interface pair where the class is a standard implementation of the interface.</span></span>

## <a name="names-of-generic-type-parameters"></a><span data-ttu-id="8c87d-117">Názvy parametrů obecného typu</span><span class="sxs-lookup"><span data-stu-id="8c87d-117">Names of Generic Type Parameters</span></span>
 <span data-ttu-id="8c87d-118">Obecné typy byly přidány do rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="8c87d-118">Generics were added to .NET Framework 2.0.</span></span> <span data-ttu-id="8c87d-119">Tato funkce zavedla nový druh identifikátoru nazývaný *parametr typu*.</span><span class="sxs-lookup"><span data-stu-id="8c87d-119">The feature introduced a new kind of identifier called *type parameter*.</span></span>

 <span data-ttu-id="8c87d-120">✔️ do název obecný typ parametry s popisnými názvy, pokud jednopísmenný název je zcela samovysvětlující a popisný název by nepřidanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8c87d-120">✔️ DO name generic type parameters with descriptive names unless a single-letter name is completely self-explanatory and a descriptive name would not add value.</span></span>

 <span data-ttu-id="8c87d-121">✔️ ZVAŽTe použití `T` jako název parametru typu pro typy s jedním parametrem typu s jedním písmenem.</span><span class="sxs-lookup"><span data-stu-id="8c87d-121">✔️ CONSIDER using `T` as the type parameter name for types with one single-letter type parameter.</span></span>

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

 <span data-ttu-id="8c87d-122">✔️ názvy parametrů popisného typu `T`předpony DO s programem .</span><span class="sxs-lookup"><span data-stu-id="8c87d-122">✔️ DO prefix descriptive type parameter names with `T`.</span></span>

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
    TSession Session { get; }
}
```

 <span data-ttu-id="8c87d-123">✔️ ZVAŽTe označení omezení umístěných na parametr typu v názvu parametru.</span><span class="sxs-lookup"><span data-stu-id="8c87d-123">✔️ CONSIDER indicating constraints placed on a type parameter in the name of the parameter.</span></span>

 <span data-ttu-id="8c87d-124">Například parametr omezen na `ISession` může být `TSession`volána .</span><span class="sxs-lookup"><span data-stu-id="8c87d-124">For example, a parameter constrained to `ISession` might be called `TSession`.</span></span>

## <a name="names-of-common-types"></a><span data-ttu-id="8c87d-125">Názvy běžných typů</span><span class="sxs-lookup"><span data-stu-id="8c87d-125">Names of Common Types</span></span>
 <span data-ttu-id="8c87d-126">✔️ do postupujte podle pokynů popsaných v následující tabulce při pojmenování typů odvozených z nebo provádění některých typů rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8c87d-126">✔️ DO follow the guidelines described in the following table when naming types derived from or implementing certain .NET Framework types.</span></span>

|<span data-ttu-id="8c87d-127">Základní typ</span><span class="sxs-lookup"><span data-stu-id="8c87d-127">Base Type</span></span>|<span data-ttu-id="8c87d-128">Pokyny pro odvozené/implementující typ</span><span class="sxs-lookup"><span data-stu-id="8c87d-128">Derived/Implementing Type Guideline</span></span>|
|---------------|------------------------------------------|
|`System.Attribute`|<span data-ttu-id="8c87d-129">✔️ DO přidat příponu "Atribut" do názvů vlastních tříd atributů.</span><span class="sxs-lookup"><span data-stu-id="8c87d-129">✔️ DO add the suffix "Attribute" to names of custom attribute classes.</span></span>|
|`System.Delegate`|<span data-ttu-id="8c87d-130">✔️ DO přidat příponu "EventHandler" do názvů delegátů, které se používají v událostech.</span><span class="sxs-lookup"><span data-stu-id="8c87d-130">✔️ DO add the suffix "EventHandler" to names of delegates that are used in events.</span></span><br /><br /> <span data-ttu-id="8c87d-131">✔️ DO přidat příponu "Zpětné volání" na názvy delegátů než ty, které se používají jako obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="8c87d-131">✔️ DO add the suffix "Callback" to names of delegates other than those used as event handlers.</span></span><br /><br /> <span data-ttu-id="8c87d-132">❌NEPŘIdávejte příponu "Delegát" delegátovi.</span><span class="sxs-lookup"><span data-stu-id="8c87d-132">❌ DO NOT add the suffix "Delegate" to a delegate.</span></span>|
|`System.EventArgs`|<span data-ttu-id="8c87d-133">✔️ DO přidat příponu "EventArgs."</span><span class="sxs-lookup"><span data-stu-id="8c87d-133">✔️ DO add the suffix "EventArgs."</span></span>|
|`System.Enum`|<span data-ttu-id="8c87d-134">❌NEODvozujte z této třídy; místo toho použijte klíčové slovo podporované vaším jazykem; například v c#, `enum` použijte klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="8c87d-134">❌ DO NOT derive from this class; use the keyword supported by your language instead; for example, in C#, use the `enum` keyword.</span></span><br /><br /> <span data-ttu-id="8c87d-135">❌Nepřidávejte příponu "Enum" nebo "Flag".</span><span class="sxs-lookup"><span data-stu-id="8c87d-135">❌ DO NOT add the suffix "Enum" or "Flag."</span></span>|
|`System.Exception`|<span data-ttu-id="8c87d-136">✔️ DO přidat příponu "Výjimka".</span><span class="sxs-lookup"><span data-stu-id="8c87d-136">✔️ DO add the suffix "Exception."</span></span>|
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|<span data-ttu-id="8c87d-137">✔️ do přidat příponu "Slovník."</span><span class="sxs-lookup"><span data-stu-id="8c87d-137">✔️ DO add the suffix "Dictionary."</span></span> <span data-ttu-id="8c87d-138">Všimněte `IDictionary` si, že je konkrétní typ kolekce, ale tento pokyn má přednost před obecnější kolekce pokyny, které následuje.</span><span class="sxs-lookup"><span data-stu-id="8c87d-138">Note that `IDictionary` is a specific type of collection, but this guideline takes precedence over the more general collections guideline that follows.</span></span>|
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|<span data-ttu-id="8c87d-139">✔️ do přidat příponu "Kolekce".</span><span class="sxs-lookup"><span data-stu-id="8c87d-139">✔️ DO add the suffix "Collection."</span></span>|
|`System.IO.Stream`|<span data-ttu-id="8c87d-140">✔️ do přidat příponu "Stream.".</span><span class="sxs-lookup"><span data-stu-id="8c87d-140">✔️ DO add the suffix "Stream."</span></span>|
|`CodeAccessPermission IPermission`|<span data-ttu-id="8c87d-141">✔️ do přidat příponu "Oprávnění".</span><span class="sxs-lookup"><span data-stu-id="8c87d-141">✔️ DO add the suffix "Permission."</span></span>|

## <a name="naming-enumerations"></a><span data-ttu-id="8c87d-142">Pojmenování výčtů</span><span class="sxs-lookup"><span data-stu-id="8c87d-142">Naming Enumerations</span></span>
 <span data-ttu-id="8c87d-143">Názvy typů výčtu (také nazývané výčty) obecně by se měly řídit standardními pravidly pojmenování typu (PascalCasing atd.).</span><span class="sxs-lookup"><span data-stu-id="8c87d-143">Names of enumeration types (also called enums) in general should follow the standard type-naming rules (PascalCasing, etc.).</span></span> <span data-ttu-id="8c87d-144">Existují však další pokyny, které platí konkrétně pro výčty.</span><span class="sxs-lookup"><span data-stu-id="8c87d-144">However, there are additional guidelines that apply specifically to enums.</span></span>

 <span data-ttu-id="8c87d-145">✔️ DO použít název jednotného čísla typu pro výčet, pokud jeho hodnoty jsou bitová pole.</span><span class="sxs-lookup"><span data-stu-id="8c87d-145">✔️ DO use a singular type name for an enumeration unless its values are bit fields.</span></span>

 <span data-ttu-id="8c87d-146">✔️ DO použít název typu množného čísla pro výčet s bitovými poli jako hodnoty, nazývané také výčty příznaků.</span><span class="sxs-lookup"><span data-stu-id="8c87d-146">✔️ DO use a plural type name for an enumeration with bit fields as values, also called flags enum.</span></span>

 <span data-ttu-id="8c87d-147">❌Nepoužívejte příponu "Enum" v názvech typů výčtu.</span><span class="sxs-lookup"><span data-stu-id="8c87d-147">❌ DO NOT use an "Enum" suffix in enum type names.</span></span>

 <span data-ttu-id="8c87d-148">❌Nepoužívejte přípony "Příznak" nebo "Příznaky" v názvech typu enum.</span><span class="sxs-lookup"><span data-stu-id="8c87d-148">❌ DO NOT use "Flag" or "Flags" suffixes in enum type names.</span></span>

 <span data-ttu-id="8c87d-149">❌Nepoužívejte předponu na názvy hodnot výčtu (např. "ad" pro výčty ADO, "rtf" pro výčty rtf atd.).</span><span class="sxs-lookup"><span data-stu-id="8c87d-149">❌ DO NOT use a prefix on enumeration value names (e.g., "ad" for ADO enums, "rtf" for rich text enums, etc.).</span></span>

 <span data-ttu-id="8c87d-150">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="8c87d-150">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="8c87d-151">*Přetištěno se svolením Pearson Education, Inc. z [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="8c87d-151">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="8c87d-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="8c87d-152">See also</span></span>

- [<span data-ttu-id="8c87d-153">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="8c87d-153">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="8c87d-154">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="8c87d-154">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
