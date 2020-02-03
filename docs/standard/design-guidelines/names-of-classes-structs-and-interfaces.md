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
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727782"
---
# <a name="names-of-classes-structs-and-interfaces"></a><span data-ttu-id="bb802-102">Názvy tříd, struktur a rozhraní</span><span class="sxs-lookup"><span data-stu-id="bb802-102">Names of Classes, Structs, and Interfaces</span></span>
<span data-ttu-id="bb802-103">Pokyny pro pojmenování, které následují, se týkají obecného typu pojmenování.</span><span class="sxs-lookup"><span data-stu-id="bb802-103">The naming guidelines that follow apply to general type naming.</span></span>

 <span data-ttu-id="bb802-104">pomocí PascalCasing ✔️ DO tříd názvů a struktur s podstatnými jmény nebo frázemi podstatných jmen.</span><span class="sxs-lookup"><span data-stu-id="bb802-104">✔️ DO name classes and structs with nouns or noun phrases, using PascalCasing.</span></span>

 <span data-ttu-id="bb802-105">To odlišuje názvy typů od metod, které jsou pojmenovány pomocí příkazového fráze.</span><span class="sxs-lookup"><span data-stu-id="bb802-105">This distinguishes type names from methods, which are named with verb phrases.</span></span>

 <span data-ttu-id="bb802-106">✔️ DO názvových rozhraní přidávejte fráze adjektiva nebo občas s podstatnými jmény nebo frázemi podstatných jmen.</span><span class="sxs-lookup"><span data-stu-id="bb802-106">✔️ DO name interfaces with adjective phrases, or occasionally with nouns or noun phrases.</span></span>

 <span data-ttu-id="bb802-107">Podstatná jména a fráze substantivum by se měly používat zřídka a můžou indikovat, že typ by měl být abstraktní třída, a ne rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bb802-107">Nouns and noun phrases should be used rarely and they might indicate that the type should be an abstract class, and not an interface.</span></span>

 <span data-ttu-id="bb802-108">❌ nedávají název třídy předponu (např. "C").</span><span class="sxs-lookup"><span data-stu-id="bb802-108">❌ DO NOT give class names a prefix (e.g., "C").</span></span>

 <span data-ttu-id="bb802-109">✔️ Zvažte ukončení názvu odvozených tříd s názvem základní třídy.</span><span class="sxs-lookup"><span data-stu-id="bb802-109">✔️ CONSIDER ending the name of derived classes with the name of the base class.</span></span>

 <span data-ttu-id="bb802-110">To je velmi čitelné a jasně vysvětluje vztah.</span><span class="sxs-lookup"><span data-stu-id="bb802-110">This is very readable and explains the relationship clearly.</span></span> <span data-ttu-id="bb802-111">Některé příklady tohoto kódu jsou: `ArgumentOutOfRangeException`, což je druh `Exception`a `SerializableAttribute`, což je typ `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="bb802-111">Some examples of this in code are: `ArgumentOutOfRangeException`, which is a kind of `Exception`, and `SerializableAttribute`, which is a kind of `Attribute`.</span></span> <span data-ttu-id="bb802-112">Je ale důležité použít rozumné rozhodnutí při použití této směrnice. Například třída `Button` je druh události `Control`, i když `Control` se nezobrazuje v názvu.</span><span class="sxs-lookup"><span data-stu-id="bb802-112">However, it is important to use reasonable judgment in applying this guideline; for example, the `Button` class is a kind of `Control` event, although `Control` doesn’t appear in its name.</span></span>

 <span data-ttu-id="bb802-113">✔️ PROVEDE předpony názvů rozhraní s písmenem I, aby označoval, že typ je rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bb802-113">✔️ DO prefix interface names with the letter I, to indicate that the type is an interface.</span></span>

 <span data-ttu-id="bb802-114">Například `IComponent` (popisný substantivum), `ICustomAttributeProvider` (fráze substantivum) a `IPersistable` (adjektivum) jsou vhodné názvy rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bb802-114">For example, `IComponent` (descriptive noun), `ICustomAttributeProvider` (noun phrase), and `IPersistable` (adjective) are appropriate interface names.</span></span> <span data-ttu-id="bb802-115">Stejně jako u jiných typů názvů Vyhněte zkratce.</span><span class="sxs-lookup"><span data-stu-id="bb802-115">As with other type names, avoid abbreviations.</span></span>

 <span data-ttu-id="bb802-116">✔️ Zajistěte, aby se názvy lišily pouze předponou "I" v názvu rozhraní při definování dvojice třídy – rozhraní, kde je třída standardní implementací rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bb802-116">✔️ DO ensure that the names differ only by the "I" prefix on the interface name when you are defining a class–interface pair where the class is a standard implementation of the interface.</span></span>

## <a name="names-of-generic-type-parameters"></a><span data-ttu-id="bb802-117">Názvy parametrů obecného typu</span><span class="sxs-lookup"><span data-stu-id="bb802-117">Names of Generic Type Parameters</span></span>
 <span data-ttu-id="bb802-118">K .NET Framework 2,0 byly přidány obecné typy.</span><span class="sxs-lookup"><span data-stu-id="bb802-118">Generics were added to .NET Framework 2.0.</span></span> <span data-ttu-id="bb802-119">Funkce představila nový typ identifikátoru nazvaný *parametr typu*.</span><span class="sxs-lookup"><span data-stu-id="bb802-119">The feature introduced a new kind of identifier called *type parameter*.</span></span>

 <span data-ttu-id="bb802-120">✔️ pojmenovat parametry obecného typu s popisnými názvy, pokud není název s jedním písmenem zcela zřejmý a popisný název by nepřidal hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bb802-120">✔️ DO name generic type parameters with descriptive names unless a single-letter name is completely self-explanatory and a descriptive name would not add value.</span></span>

 <span data-ttu-id="bb802-121">✔️ Zvažte použití `T` jako názvu parametru typu pro typy s jedním parametrem typu s jedním písmenem.</span><span class="sxs-lookup"><span data-stu-id="bb802-121">✔️ CONSIDER using `T` as the type parameter name for types with one single-letter type parameter.</span></span>

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

 <span data-ttu-id="bb802-122">✔️ DĚLAT předpony názvů parametrů popisného typu s `T`.</span><span class="sxs-lookup"><span data-stu-id="bb802-122">✔️ DO prefix descriptive type parameter names with `T`.</span></span>

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
    TSession Session { get; }
}
```

 <span data-ttu-id="bb802-123">✔️ Zvažte označení omezení, která jsou uvedena v parametru typu v názvu parametru.</span><span class="sxs-lookup"><span data-stu-id="bb802-123">✔️ CONSIDER indicating constraints placed on a type parameter in the name of the parameter.</span></span>

 <span data-ttu-id="bb802-124">Například parametr omezený na `ISession` může být volán `TSession`.</span><span class="sxs-lookup"><span data-stu-id="bb802-124">For example, a parameter constrained to `ISession` might be called `TSession`.</span></span>

## <a name="names-of-common-types"></a><span data-ttu-id="bb802-125">Názvy běžných typů</span><span class="sxs-lookup"><span data-stu-id="bb802-125">Names of Common Types</span></span>
 <span data-ttu-id="bb802-126">✔️ postupujte podle pokynů popsaných v následující tabulce, když pojmenováváte typy odvozené z nebo implementují určité .NET Framework typy.</span><span class="sxs-lookup"><span data-stu-id="bb802-126">✔️ DO follow the guidelines described in the following table when naming types derived from or implementing certain .NET Framework types.</span></span>

|<span data-ttu-id="bb802-127">Základní typ</span><span class="sxs-lookup"><span data-stu-id="bb802-127">Base Type</span></span>|<span data-ttu-id="bb802-128">Základní pravidlo pro odvození/implementaci typu</span><span class="sxs-lookup"><span data-stu-id="bb802-128">Derived/Implementing Type Guideline</span></span>|
|---------------|------------------------------------------|
|`System.Attribute`|<span data-ttu-id="bb802-129">✔️ Přidejte příponu "Attribute" do názvů vlastních tříd atributů.</span><span class="sxs-lookup"><span data-stu-id="bb802-129">✔️ DO add the suffix "Attribute" to names of custom attribute classes.</span></span>|
|`System.Delegate`|<span data-ttu-id="bb802-130">✔️ přidat příponu EventHandler do názvů delegátů, kteří se používají v událostech.</span><span class="sxs-lookup"><span data-stu-id="bb802-130">✔️ DO add the suffix "EventHandler" to names of delegates that are used in events.</span></span><br /><br /> <span data-ttu-id="bb802-131">✔️ přidat příponu "zpětného volání" do názvů jiných delegátů, než které byly použity jako obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="bb802-131">✔️ DO add the suffix "Callback" to names of delegates other than those used as event handlers.</span></span><br /><br /> <span data-ttu-id="bb802-132">❌ Nepřidávat příponu Delegate do delegáta.</span><span class="sxs-lookup"><span data-stu-id="bb802-132">❌ DO NOT add the suffix "Delegate" to a delegate.</span></span>|
|`System.EventArgs`|<span data-ttu-id="bb802-133">✔️ přidat příponu EventArgs.</span><span class="sxs-lookup"><span data-stu-id="bb802-133">✔️ DO add the suffix "EventArgs."</span></span>|
|`System.Enum`|<span data-ttu-id="bb802-134">❌ neodvozovat z této třídy; místo toho použijte klíčové slovo podporované vaším jazykem. například v C#použijte klíčové slovo `enum`.</span><span class="sxs-lookup"><span data-stu-id="bb802-134">❌ DO NOT derive from this class; use the keyword supported by your language instead; for example, in C#, use the `enum` keyword.</span></span><br /><br /> <span data-ttu-id="bb802-135">❌ Nepřidávat příponu "enum" nebo "Flag".</span><span class="sxs-lookup"><span data-stu-id="bb802-135">❌ DO NOT add the suffix "Enum" or "Flag."</span></span>|
|`System.Exception`|<span data-ttu-id="bb802-136">✔️ přidat příponu "Exception".</span><span class="sxs-lookup"><span data-stu-id="bb802-136">✔️ DO add the suffix "Exception."</span></span>|
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|<span data-ttu-id="bb802-137">✔️ přidat příponu "Dictionary".</span><span class="sxs-lookup"><span data-stu-id="bb802-137">✔️ DO add the suffix "Dictionary."</span></span> <span data-ttu-id="bb802-138">Všimněte si, že `IDictionary` je konkrétní typ kolekce, ale tyto zásady mají přednost před obecnější pokyny ke kolekcím.</span><span class="sxs-lookup"><span data-stu-id="bb802-138">Note that `IDictionary` is a specific type of collection, but this guideline takes precedence over the more general collections guideline that follows.</span></span>|
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|<span data-ttu-id="bb802-139">✔️ přidat příponu "Collection".</span><span class="sxs-lookup"><span data-stu-id="bb802-139">✔️ DO add the suffix "Collection."</span></span>|
|`System.IO.Stream`|<span data-ttu-id="bb802-140">✔️ přidat příponu "Stream".</span><span class="sxs-lookup"><span data-stu-id="bb802-140">✔️ DO add the suffix "Stream."</span></span>|
|`CodeAccessPermission IPermission`|<span data-ttu-id="bb802-141">✔️ přidat příponu "oprávnění".</span><span class="sxs-lookup"><span data-stu-id="bb802-141">✔️ DO add the suffix "Permission."</span></span>|

## <a name="naming-enumerations"></a><span data-ttu-id="bb802-142">Vytváření názvů výčtů</span><span class="sxs-lookup"><span data-stu-id="bb802-142">Naming Enumerations</span></span>
 <span data-ttu-id="bb802-143">Názvy výčtových typů (označovaných také jako výčty) by obecně měly splňovat standardní pravidla pro pojmenovávání typů (PascalCasing atd.).</span><span class="sxs-lookup"><span data-stu-id="bb802-143">Names of enumeration types (also called enums) in general should follow the standard type-naming rules (PascalCasing, etc.).</span></span> <span data-ttu-id="bb802-144">Existují však další pokyny, které platí konkrétně pro výčty.</span><span class="sxs-lookup"><span data-stu-id="bb802-144">However, there are additional guidelines that apply specifically to enums.</span></span>

 <span data-ttu-id="bb802-145">✔️ použít název typu jednotného čísla pro výčet, pokud jeho hodnoty nejsou bitové pole.</span><span class="sxs-lookup"><span data-stu-id="bb802-145">✔️ DO use a singular type name for an enumeration unless its values are bit fields.</span></span>

 <span data-ttu-id="bb802-146">✔️ použít název typu plural pro výčet s bitovými poli jako hodnoty, označované také jako příznaky Enum.</span><span class="sxs-lookup"><span data-stu-id="bb802-146">✔️ DO use a plural type name for an enumeration with bit fields as values, also called flags enum.</span></span>

 <span data-ttu-id="bb802-147">❌ nepoužívejte příponu "enum" v názvech typu výčtu.</span><span class="sxs-lookup"><span data-stu-id="bb802-147">❌ DO NOT use an "Enum" suffix in enum type names.</span></span>

 <span data-ttu-id="bb802-148">❌ v názvech typů výčtu nepoužívejte přípony příznak ani Flags.</span><span class="sxs-lookup"><span data-stu-id="bb802-148">❌ DO NOT use "Flag" or "Flags" suffixes in enum type names.</span></span>

 <span data-ttu-id="bb802-149">❌ nepoužívejte předponu u názvů hodnot výčtu (např. "AD" pro výčty objektů ADO, "RTF" pro výčty formátovaného textu atd.).</span><span class="sxs-lookup"><span data-stu-id="bb802-149">❌ DO NOT use a prefix on enumeration value names (e.g., "ad" for ADO enums, "rtf" for rich text enums, etc.).</span></span>

 <span data-ttu-id="bb802-150">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="bb802-150">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="bb802-151">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="bb802-151">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="bb802-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb802-152">See also</span></span>

- [<span data-ttu-id="bb802-153">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="bb802-153">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="bb802-154">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="bb802-154">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
