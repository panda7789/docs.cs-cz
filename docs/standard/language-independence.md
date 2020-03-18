---
title: Jazyková nezávislost a jazykově nezávislé komponenty
description: Zjistěte, jak můžete vyvíjet v jednom z mnoha podporovaných jazyků v rozhraní .NET, jako je například C#, C++/CLI, F#, IronPython, VB, Visual COBOL a PowerShell.
ms.date: 07/22/2016
dev_langs:
- csharp
- vb
ms.technology: dotnet-standard
ms.assetid: 2dbed1bc-86f5-43cd-9a57-adbb1c5efba4
ms.openlocfilehash: e1f419dd57c1e90d7ebb57ef572f338a34d1c509
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73423640"
---
# <a name="language-independence-and-language-independent-components"></a><span data-ttu-id="384c1-103">Jazyková nezávislost a jazykově nezávislé komponenty</span><span class="sxs-lookup"><span data-stu-id="384c1-103">Language independence and language-independent components</span></span>

<span data-ttu-id="384c1-104">.NET je jazykově nezávislý.</span><span class="sxs-lookup"><span data-stu-id="384c1-104">.NET is language independent.</span></span> <span data-ttu-id="384c1-105">To znamená, že jako vývojář můžete vyvíjet v jednom z mnoha jazyků, které cílí na implementace rozhraní .NET, například C#, F# a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="384c1-105">This means that, as a developer, you can develop in one of the many languages that target .NET implementations, such as C#, F#, and Visual Basic.</span></span> <span data-ttu-id="384c1-106">Můžete přistupovat k typům a členům knihoven tříd vyvinutých pro implementace rozhraní .NET, aniž byste museli znát jazyk, ve kterém byly původně napsány, a aniž byste museli dodržovat některé z konvencí původního jazyka.</span><span class="sxs-lookup"><span data-stu-id="384c1-106">You can access the types and members of class libraries developed for .NET implementations without having to know the language in which they were originally written and without having to follow any of the original language's conventions.</span></span> <span data-ttu-id="384c1-107">Pokud jste vývojář komponent, vaše komponenta může přistupovat libovolnou aplikací .NET bez ohledu na její jazyk.</span><span class="sxs-lookup"><span data-stu-id="384c1-107">If you are a component developer, your component can be accessed by any .NET app regardless of its language.</span></span>

> [!NOTE]
> <span data-ttu-id="384c1-108">Tato první část tohoto článku popisuje vytváření součásti nezávislé na jazyce - to znamená, že součásti, které mohou být spotřebovány aplikace, které jsou napsány v libovolném jazyce.</span><span class="sxs-lookup"><span data-stu-id="384c1-108">This first part of this article discusses creating language-independent components - that is, components that can be consumed by apps that are written in any language.</span></span> <span data-ttu-id="384c1-109">Můžete také vytvořit jednu komponentu nebo aplikaci ze zdrojového kódu napsaného ve více jazycích. viz [Interoperabilita mezi jazyky](#cross-language-interoperability) v druhé části tohoto článku.</span><span class="sxs-lookup"><span data-stu-id="384c1-109">You can also create a single component or app from source code written in multiple languages; see [Cross-Language Interoperability](#cross-language-interoperability) in the second part of this article.</span></span>

<span data-ttu-id="384c1-110">Chcete-li plně pracovat s jinými objekty napsanými v libovolném jazyce, musí objekty vystavit volajícím pouze ty funkce, které jsou společné pro všechny jazyky.</span><span class="sxs-lookup"><span data-stu-id="384c1-110">To fully interact with other objects written in any language, objects must expose to callers only those features that are common to all languages.</span></span> <span data-ttu-id="384c1-111">Tato společná sada funkcí je definována specifikací CLS (Common Language Specification), což je sada pravidel, která platí pro vygenerovaná sestavení.</span><span class="sxs-lookup"><span data-stu-id="384c1-111">This common set of features is defined by the Common Language Specification (CLS), which is a set of rules that apply to generated assemblies.</span></span> <span data-ttu-id="384c1-112">Specifikace společného jazyka je definována v oddílu I, větách 7 až 11 [normy ECMA-335: Společná jazyková infrastruktura](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="384c1-112">The Common Language Specification is defined in Partition I, Clauses 7 through 11 of the [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>

<span data-ttu-id="384c1-113">Pokud vaše součást odpovídá specifikaci společného jazyka, je zaručeno, že je kompatibilní se specifikací CLS a je přístupná z kódu v sestaveních napsaných v libovolném programovacím jazyce, který podporuje cls.</span><span class="sxs-lookup"><span data-stu-id="384c1-113">If your component conforms to the Common Language Specification, it is guaranteed to be CLS-compliant and can be accessed from code in assemblies written in any programming language that supports the CLS.</span></span> <span data-ttu-id="384c1-114">Můžete určit, zda vaše součást odpovídá specifikaci společného jazyka v době kompilace použitím atributu [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) na zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="384c1-114">You can determine whether your component conforms to the Common Language Specification at compile time by applying the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute to your source code.</span></span> <span data-ttu-id="384c1-115">Další informace naleznete v [tématu Atribut CLSCompliantAttribute](#the-clscompliantattribute-attribute).</span><span class="sxs-lookup"><span data-stu-id="384c1-115">For more information, see The [CLSCompliantAttribute attribute](#the-clscompliantattribute-attribute).</span></span>

<span data-ttu-id="384c1-116">V tomto článku:</span><span class="sxs-lookup"><span data-stu-id="384c1-116">In this article:</span></span>

* [<span data-ttu-id="384c1-117">Pravidla dodržování předpisů CLS</span><span class="sxs-lookup"><span data-stu-id="384c1-117">CLS compliance rules</span></span>](#cls-compliance-rules)

  * [<span data-ttu-id="384c1-118">Typy a podpisy členů typu</span><span class="sxs-lookup"><span data-stu-id="384c1-118">Types and type member signatures</span></span>](#types-and-type-member-signatures)

  * [<span data-ttu-id="384c1-119">Zásady vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="384c1-119">Naming conventions</span></span>](#naming-conventions)

  * [<span data-ttu-id="384c1-120">Převod typů</span><span class="sxs-lookup"><span data-stu-id="384c1-120">Type conversion</span></span>](#type-conversion)

  * [<span data-ttu-id="384c1-121">Pole</span><span class="sxs-lookup"><span data-stu-id="384c1-121">Arrays</span></span>](#arrays)

  * [<span data-ttu-id="384c1-122">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="384c1-122">Interfaces</span></span>](#interfaces)

  * [<span data-ttu-id="384c1-123">Výčty</span><span class="sxs-lookup"><span data-stu-id="384c1-123">Enumerations</span></span>](#enumerations)

  * [<span data-ttu-id="384c1-124">Typ členů obecně</span><span class="sxs-lookup"><span data-stu-id="384c1-124">Type members in general</span></span>](#type-members-in-general)

  * [<span data-ttu-id="384c1-125">Přístupnost členů</span><span class="sxs-lookup"><span data-stu-id="384c1-125">Member accessibility</span></span>](#member-accessibility)

  * [<span data-ttu-id="384c1-126">Obecné typy a členy</span><span class="sxs-lookup"><span data-stu-id="384c1-126">Generic types and members</span></span>](#generic-types-and-members)

  * [<span data-ttu-id="384c1-127">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="384c1-127">Constructors</span></span>](#constructors)

  * [<span data-ttu-id="384c1-128">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="384c1-128">Properties</span></span>](#properties)

  * [<span data-ttu-id="384c1-129">Akce</span><span class="sxs-lookup"><span data-stu-id="384c1-129">Events</span></span>](#events)

  * [<span data-ttu-id="384c1-130">Přetížení</span><span class="sxs-lookup"><span data-stu-id="384c1-130">Overloads</span></span>](#overloads)

  * [<span data-ttu-id="384c1-131">Výjimky</span><span class="sxs-lookup"><span data-stu-id="384c1-131">Exceptions</span></span>](#exceptions)

  * [<span data-ttu-id="384c1-132">Atributy</span><span class="sxs-lookup"><span data-stu-id="384c1-132">Attributes</span></span>](#attributes)

* [<span data-ttu-id="384c1-133">Atribut CLSCompliantAttribute</span><span class="sxs-lookup"><span data-stu-id="384c1-133">CLSCompliantAttribute attribute</span></span>](#the-clscompliantattribute-attribute)

* [<span data-ttu-id="384c1-134">Vzájemná funkční spolupráce mezi jazyky</span><span class="sxs-lookup"><span data-stu-id="384c1-134">Cross-Language Interoperability</span></span>](#cross-language-interoperability)

## <a name="cls-compliance-rules"></a><span data-ttu-id="384c1-135">Pravidla dodržování předpisů CLS</span><span class="sxs-lookup"><span data-stu-id="384c1-135">CLS compliance rules</span></span>

<span data-ttu-id="384c1-136">Tato část popisuje pravidla pro vytvoření součásti kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-136">This section discusses the rules for creating a CLS-compliant component.</span></span> <span data-ttu-id="384c1-137">Úplný seznam pravidel naleznete v oddílu I, článku 11 [normy ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="384c1-137">For a complete list of rules, see Partition I, Clause 11 of the [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>

> [!NOTE]
> <span data-ttu-id="384c1-138">Specifikace společného jazyka popisuje každé pravidlo pro dodržování specifikace CLS, protože se vztahuje na spotřebitele (vývojáři, kteří programově přistupují k součásti, která je kompatibilní se specifikací CLS), architektury (vývojáři, kteří používají kompilátor jazyka k vytvoření Knihovny kompatibilní se standardem CLS) a rozšiřující zařízení (vývojáři, kteří vytvářejí nástroj, jako je například kompilátor jazyka nebo analyzátor kódu, který vytváří součásti kompatibilní se standardem CLS).</span><span class="sxs-lookup"><span data-stu-id="384c1-138">The Common Language Specification discusses each rule for CLS compliance as it applies to consumers (developers who are programmatically accessing a component that is CLS-compliant), frameworks (developers who are using a language compiler to create CLS-compliant libraries), and extenders (developers who are creating a tool such as a language compiler or a code parser that creates CLS-compliant components).</span></span> <span data-ttu-id="384c1-139">Tento článek se zaměřuje na pravidla, která se vztahují na rámce.</span><span class="sxs-lookup"><span data-stu-id="384c1-139">This article focuses on the rules as they apply to frameworks.</span></span> <span data-ttu-id="384c1-140">Všimněte si však, že některá pravidla, která platí pro rozšiřující zařízení, se mohou vztahovat také na sestavení, která jsou vytvořena pomocí [funkce Reflection.Emit](xref:System.Reflection.Emit).</span><span class="sxs-lookup"><span data-stu-id="384c1-140">Note, though, that some of the rules that apply to extenders may also apply to assemblies that are created using [Reflection.Emit](xref:System.Reflection.Emit).</span></span>

<span data-ttu-id="384c1-141">Chcete-li navrhnout komponentu, která je jazykově nezávislá, stačí použít pravidla pro dodržování předpisů CLS na veřejné rozhraní komponenty.</span><span class="sxs-lookup"><span data-stu-id="384c1-141">To design a component that is language independent, you only need to apply the rules for CLS compliance to your component's public interface.</span></span> <span data-ttu-id="384c1-142">Vaše soukromá implementace nemusí odpovídat specifikaci.</span><span class="sxs-lookup"><span data-stu-id="384c1-142">Your private implementation does not have to conform to the specification.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="384c1-143">Pravidla pro dodržování předpisů cls se vztahují pouze na veřejné rozhraní komponenty, nikoli na její privátní implementaci.</span><span class="sxs-lookup"><span data-stu-id="384c1-143">The rules for CLS compliance apply only to a component's public interface, not to its private implementation.</span></span>

<span data-ttu-id="384c1-144">Například nepodepsaná celá čísla než [Byte](xref:System.Byte) nejsou kompatibilní se smlouvou CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-144">For example, unsigned integers other than [Byte](xref:System.Byte) are not CLS-compliant.</span></span> <span data-ttu-id="384c1-145">Vzhledem `Person` k tomu, že `Age` třída v následujícím příkladu zpřístupňuje vlastnost typu [UInt16](xref:System.UInt16), zobrazí se v následujícím kódu upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="384c1-145">Because the `Person` class in the following example exposes an `Age` property of type [UInt16](xref:System.UInt16), the following code displays a compiler warning.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person
{
   private UInt16 personAge = 0;

   public UInt16 Age
   { get { return personAge; } }
}
// The attempt to compile the example displays the following compiler warning:
//    Public1.cs(10,18): warning CS3003: Type of 'Person.Age' is not CLS-compliant
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Person
   Private personAge As UInt16

   Public ReadOnly Property Age As UInt16
      Get
         Return personAge
      End Get
   End Property
End Class
' The attempt to compile the example displays the following compiler warning:
'    Public1.vb(9) : warning BC40027: Return type of function 'Age' is not CLS-compliant.
'
'       Public ReadOnly Property Age As UInt16
'                                ~~~
```

<span data-ttu-id="384c1-146">Třídu Person CLS můžete provést změnou `Age` typu `UInt16` vlastnosti z [Int16](xref:System.Int16), což je 16bitové podepsané číslo cls.</span><span class="sxs-lookup"><span data-stu-id="384c1-146">You can make the Person class CLS-compliant by changing the type of `Age` property from `UInt16` to [Int16](xref:System.Int16), which is a CLS-compliant, 16-bit signed integer.</span></span> <span data-ttu-id="384c1-147">Není třeba měnit typ soukromého `personAge` pole.</span><span class="sxs-lookup"><span data-stu-id="384c1-147">You do not have to change the type of the private `personAge` field.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person
{
   private Int16 personAge = 0;

   public Int16 Age
   { get { return personAge; } }
}
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Person
   Private personAge As UInt16

   Public ReadOnly Property Age As Int16
      Get
         Return CType(personAge, Int16)
      End Get
   End Property
End Class
```

<span data-ttu-id="384c1-148">Veřejné rozhraní knihovny se skládá z následujících:</span><span class="sxs-lookup"><span data-stu-id="384c1-148">A library's public interface consists of the following:</span></span>

* <span data-ttu-id="384c1-149">Definice veřejných tříd.</span><span class="sxs-lookup"><span data-stu-id="384c1-149">Definitions of public classes.</span></span>

* <span data-ttu-id="384c1-150">Definice veřejné členy veřejné třídy a definice členů přístupných odvozené třídy (to znamená, chráněné členy).</span><span class="sxs-lookup"><span data-stu-id="384c1-150">Definitions of the public members of public classes, and definitions of members accessible to derived classes (that is, protected members).</span></span>

* <span data-ttu-id="384c1-151">Parametry a návratové typy veřejných metod veřejných tříd a parametry a návratové typy metod přístupných odvozeným třídám.</span><span class="sxs-lookup"><span data-stu-id="384c1-151">Parameters and return types of public methods of public classes, and parameters and return types of methods accessible to derived classes.</span></span>

<span data-ttu-id="384c1-152">Pravidla pro dodržování předpisů cls jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="384c1-152">The rules for CLS compliance are listed in the following table.</span></span> <span data-ttu-id="384c1-153">Znění pravidel je převzato doslovně z [normy ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm), což je autorská práva 2012 od ecma International.</span><span class="sxs-lookup"><span data-stu-id="384c1-153">The text of the rules is taken verbatim from the [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm), which is Copyright 2012 by Ecma International.</span></span> <span data-ttu-id="384c1-154">Podrobnější informace o těchto pravidlech naleznete v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="384c1-154">More detailed information about these rules is found in the following sections.</span></span>

<span data-ttu-id="384c1-155">Kategorie</span><span class="sxs-lookup"><span data-stu-id="384c1-155">Category</span></span> | <span data-ttu-id="384c1-156">Seznamte se s </span><span class="sxs-lookup"><span data-stu-id="384c1-156">See</span></span> | <span data-ttu-id="384c1-157">Pravidlo</span><span class="sxs-lookup"><span data-stu-id="384c1-157">Rule</span></span> | <span data-ttu-id="384c1-158">Číslo pravidla</span><span class="sxs-lookup"><span data-stu-id="384c1-158">Rule Number</span></span>
-------- | --- | ---- | -----------
<span data-ttu-id="384c1-159">Přístupnost</span><span class="sxs-lookup"><span data-stu-id="384c1-159">Accessibility</span></span> | [<span data-ttu-id="384c1-160">Přístupnost členů</span><span class="sxs-lookup"><span data-stu-id="384c1-160">Member accessibility</span></span>](#member-accessibility) | <span data-ttu-id="384c1-161">Usnadnění přístupu se nesmí změnit při přepsání zděděných metod, s `family-or-assembly`výjimkou přepsání metody zděděné z jiného sestavení s usnadněním přístupu .</span><span class="sxs-lookup"><span data-stu-id="384c1-161">Accessibility shall not be changed when overriding inherited methods, except when overriding a method inherited from a different assembly with accessibility `family-or-assembly`.</span></span> <span data-ttu-id="384c1-162">V tomto případě musí mít `family`přepsání přístupnost .</span><span class="sxs-lookup"><span data-stu-id="384c1-162">In this case, the override shall have accessibility `family`.</span></span> | <span data-ttu-id="384c1-163">10</span><span class="sxs-lookup"><span data-stu-id="384c1-163">10</span></span>
<span data-ttu-id="384c1-164">Přístupnost</span><span class="sxs-lookup"><span data-stu-id="384c1-164">Accessibility</span></span> | [<span data-ttu-id="384c1-165">Přístupnost členů</span><span class="sxs-lookup"><span data-stu-id="384c1-165">Member accessibility</span></span>](#member-accessibility) | <span data-ttu-id="384c1-166">Viditelnost a přístupnost typů a členů musí být takové, aby typy v podpisu kteréhokoli člena byly viditelné a přístupné vždy, když je člen sám viditelný a přístupný.</span><span class="sxs-lookup"><span data-stu-id="384c1-166">The visibility and accessibility of types and members shall be such that types in the signature of any member shall be visible and accessible whenever the member itself is visible and accessible.</span></span> <span data-ttu-id="384c1-167">Například veřejná metoda, která je viditelná mimo jeho sestavení, nesmí mít argument, jehož typ je viditelný pouze v rámci sestavení.</span><span class="sxs-lookup"><span data-stu-id="384c1-167">For example, a public method that is visible outside its assembly shall not have an argument whose type is visible only within the assembly.</span></span> <span data-ttu-id="384c1-168">Viditelnost a přístupnost typů tvořících instanci obecný typ použitý v podpisu každého člena musí být viditelná a přístupná vždy, když je člen sám viditelný a přístupný.</span><span class="sxs-lookup"><span data-stu-id="384c1-168">The visibility and accessibility of types composing an instantiated generic type used in the signature of any member shall be visible and accessible whenever the member itself is visible and accessible.</span></span> <span data-ttu-id="384c1-169">Například instance obecný typ přítomný v podpisu člena, který je viditelný mimo jeho sestavení nesmí mít obecný argument, jehož typ je viditelný pouze v rámci sestavení.</span><span class="sxs-lookup"><span data-stu-id="384c1-169">For example, an instantiated generic type present in the signature of a member that is visible outside its assembly shall not have a generic argument whose type is visible only within the assembly.</span></span> | <span data-ttu-id="384c1-170">12</span><span class="sxs-lookup"><span data-stu-id="384c1-170">12</span></span>
<span data-ttu-id="384c1-171">Pole</span><span class="sxs-lookup"><span data-stu-id="384c1-171">Arrays</span></span> | [<span data-ttu-id="384c1-172">Pole</span><span class="sxs-lookup"><span data-stu-id="384c1-172">Arrays</span></span>](#arrays) | <span data-ttu-id="384c1-173">Pole musí mít prvky s typem kompatibilním se standardem CLS a všechny rozměry pole musí mít dolní hranice nula.</span><span class="sxs-lookup"><span data-stu-id="384c1-173">Arrays shall have elements with a CLS-compliant type, and all dimensions of the array shall have lower bounds of zero.</span></span> <span data-ttu-id="384c1-174">Pouze skutečnost, že položka je pole a typ prvku pole musí být nutné rozlišovat mezi přetížení.</span><span class="sxs-lookup"><span data-stu-id="384c1-174">Only the fact that an item is an array and the element type of the array shall be required to distinguish between overloads.</span></span> <span data-ttu-id="384c1-175">Při přetížení je založena na dvou nebo více typů pole typy prvků musí být pojmenovány typy.</span><span class="sxs-lookup"><span data-stu-id="384c1-175">When overloading is based on two or more array types the element types shall be named types.</span></span> | <span data-ttu-id="384c1-176">16</span><span class="sxs-lookup"><span data-stu-id="384c1-176">16</span></span>
<span data-ttu-id="384c1-177">Atributy</span><span class="sxs-lookup"><span data-stu-id="384c1-177">Attributes</span></span> | [<span data-ttu-id="384c1-178">Atributy</span><span class="sxs-lookup"><span data-stu-id="384c1-178">Attributes</span></span>](#attributes) | <span data-ttu-id="384c1-179">Atributy musí být typu [System.Attribute](xref:System.Attribute)nebo typu dědícího z něj.</span><span class="sxs-lookup"><span data-stu-id="384c1-179">Attributes shall be of type [System.Attribute](xref:System.Attribute), or a type inheriting from it.</span></span> | <span data-ttu-id="384c1-180">41</span><span class="sxs-lookup"><span data-stu-id="384c1-180">41</span></span>
<span data-ttu-id="384c1-181">Atributy</span><span class="sxs-lookup"><span data-stu-id="384c1-181">Attributes</span></span> | [<span data-ttu-id="384c1-182">Atributy</span><span class="sxs-lookup"><span data-stu-id="384c1-182">Attributes</span></span>](#attributes) | <span data-ttu-id="384c1-183">Cls umožňuje pouze podmnožinu kódování vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="384c1-183">The CLS only allows a subset of the encodings of custom attributes.</span></span> <span data-ttu-id="384c1-184">V těchto kódováních se zobrazí pouze typy (viz oddíl IV): [System.Type](xref:System.Type), [System.String](xref:System.String), [System.Char](xref:System.Char), [System.Boolean](xref:System.Boolean), [System.Byte](xref:System.Byte), [System.Int16](xref:System.Int16), [System.Int32](xref:System.Int32), [System.Int64](xref:System.Int64), [System.Single](xref:System.Single), [System.Double](xref:System.Double)a jakýkoli typ výčtu založený na typu základního celého čísla kompatibilního se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-184">The only types that shall appear in these encodings are (see Partition IV): [System.Type](xref:System.Type), [System.String](xref:System.String), [System.Char](xref:System.Char), [System.Boolean](xref:System.Boolean), [System.Byte](xref:System.Byte), [System.Int16](xref:System.Int16), [System.Int32](xref:System.Int32), [System.Int64](xref:System.Int64), [System.Single](xref:System.Single), [System.Double](xref:System.Double), and any enumeration type based on a CLS-compliant base integer type.</span></span> | <span data-ttu-id="384c1-185">34</span><span class="sxs-lookup"><span data-stu-id="384c1-185">34</span></span>
<span data-ttu-id="384c1-186">Atributy</span><span class="sxs-lookup"><span data-stu-id="384c1-186">Attributes</span></span> | [<span data-ttu-id="384c1-187">Atributy</span><span class="sxs-lookup"><span data-stu-id="384c1-187">Attributes</span></span>](#attributes) | <span data-ttu-id="384c1-188">Cls neumožňuje veřejně viditelné požadované modifikátory (`modreq`, viz Oddíl II),`modopt`ale umožňuje volitelné modifikátory ( , viz Oddíl II), kterému nerozumí.</span><span class="sxs-lookup"><span data-stu-id="384c1-188">The CLS does not allow publicly visible required modifiers (`modreq`, see Partition II), but does allow optional modifiers (`modopt`, see Partition II) it does not understand.</span></span> | <span data-ttu-id="384c1-189">35</span><span class="sxs-lookup"><span data-stu-id="384c1-189">35</span></span>
<span data-ttu-id="384c1-190">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="384c1-190">Constructors</span></span> | [<span data-ttu-id="384c1-191">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="384c1-191">Constructors</span></span>](#constructors) | <span data-ttu-id="384c1-192">Konstruktor objektu musí volat některé instance konstruktor jeho základní třídy před dojde k přístupu k datzitý instance.</span><span class="sxs-lookup"><span data-stu-id="384c1-192">An object constructor shall call some instance constructor of its base class before any access occurs to inherited instance data.</span></span> <span data-ttu-id="384c1-193">(To se nevztahuje na typy hodnot, které nemusí mít konstruktory.)</span><span class="sxs-lookup"><span data-stu-id="384c1-193">(This does not apply to value types, which need not have constructors.)</span></span>  | <span data-ttu-id="384c1-194">21</span><span class="sxs-lookup"><span data-stu-id="384c1-194">21</span></span>
<span data-ttu-id="384c1-195">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="384c1-195">Constructors</span></span> | [<span data-ttu-id="384c1-196">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="384c1-196">Constructors</span></span>](#constructors) | <span data-ttu-id="384c1-197">Konstruktor objektu nesmí být volán s výjimkou součásti vytvoření objektu a objekt nesmí být inicializován dvakrát.</span><span class="sxs-lookup"><span data-stu-id="384c1-197">An object constructor shall not be called except as part of the creation of an object, and an object shall not be initialized twice.</span></span> | <span data-ttu-id="384c1-198">22</span><span class="sxs-lookup"><span data-stu-id="384c1-198">22</span></span>
<span data-ttu-id="384c1-199">Výčty</span><span class="sxs-lookup"><span data-stu-id="384c1-199">Enumerations</span></span> | [<span data-ttu-id="384c1-200">Výčty</span><span class="sxs-lookup"><span data-stu-id="384c1-200">Enumerations</span></span>](#enumerations) | <span data-ttu-id="384c1-201">Základní typ výčtu musí být vestavěný typ celého čísla CLS, název pole bude "value__" a `RTSpecialName`toto pole bude označeno .</span><span class="sxs-lookup"><span data-stu-id="384c1-201">The underlying type of an enum shall be a built-in CLS integer type, the name of the field shall be "value__", and that field shall be marked `RTSpecialName`.</span></span> |  <span data-ttu-id="384c1-202">7</span><span class="sxs-lookup"><span data-stu-id="384c1-202">7</span></span>
<span data-ttu-id="384c1-203">Výčty</span><span class="sxs-lookup"><span data-stu-id="384c1-203">Enumerations</span></span> | [<span data-ttu-id="384c1-204">Výčty</span><span class="sxs-lookup"><span data-stu-id="384c1-204">Enumerations</span></span>](#enumerations) | <span data-ttu-id="384c1-205">Existují dva odlišné druhy výčtů, označené přítomností nebo nepřítomností vlastního atributu [System.FlagsAttribute](xref:System.FlagsAttribute) (viz Knihovna oddílu IV).</span><span class="sxs-lookup"><span data-stu-id="384c1-205">There are two distinct kinds of enums, indicated by the presence or absence of the [System.FlagsAttribute](xref:System.FlagsAttribute) (see Partition IV Library) custom attribute.</span></span> <span data-ttu-id="384c1-206">Jeden představuje pojmenované celé číslo hodnoty; ostatní představuje pojmenované bitové příznaky, které lze kombinovat pro generování nepojmenované hodnoty.</span><span class="sxs-lookup"><span data-stu-id="384c1-206">One represents named integer values; the other represents named bit flags that can be combined to generate an unnamed value.</span></span> <span data-ttu-id="384c1-207">Hodnota an `enum` není omezena na zadané hodnoty.</span><span class="sxs-lookup"><span data-stu-id="384c1-207">The value of an `enum` is not limited to the specified values.</span></span> |  <span data-ttu-id="384c1-208">8</span><span class="sxs-lookup"><span data-stu-id="384c1-208">8</span></span>
<span data-ttu-id="384c1-209">Výčty</span><span class="sxs-lookup"><span data-stu-id="384c1-209">Enumerations</span></span> | [<span data-ttu-id="384c1-210">Výčty</span><span class="sxs-lookup"><span data-stu-id="384c1-210">Enumerations</span></span>](#enumerations) | <span data-ttu-id="384c1-211">Literálová statická pole výčtu musí mít typ výčtu samotného.</span><span class="sxs-lookup"><span data-stu-id="384c1-211">Literal static fields of an enum shall have the type of the enum itself.</span></span> |  <span data-ttu-id="384c1-212">9</span><span class="sxs-lookup"><span data-stu-id="384c1-212">9</span></span>
<span data-ttu-id="384c1-213">Akce</span><span class="sxs-lookup"><span data-stu-id="384c1-213">Events</span></span> | [<span data-ttu-id="384c1-214">Akce</span><span class="sxs-lookup"><span data-stu-id="384c1-214">Events</span></span>](#events) | <span data-ttu-id="384c1-215">Metody, které implementují `SpecialName` událost, musí být označeny v metadatech.</span><span class="sxs-lookup"><span data-stu-id="384c1-215">The methods that implement an event shall be marked `SpecialName` in the metadata.</span></span> |<span data-ttu-id="384c1-216">29</span><span class="sxs-lookup"><span data-stu-id="384c1-216">29</span></span>
<span data-ttu-id="384c1-217">Akce</span><span class="sxs-lookup"><span data-stu-id="384c1-217">Events</span></span> | [<span data-ttu-id="384c1-218">Akce</span><span class="sxs-lookup"><span data-stu-id="384c1-218">Events</span></span>](#events) | <span data-ttu-id="384c1-219">Přístupnost události a jejích přistupujících objektů musí být totožná.</span><span class="sxs-lookup"><span data-stu-id="384c1-219">The accessibility of an event and of its accessors shall be identical.</span></span> |<span data-ttu-id="384c1-220">30</span><span class="sxs-lookup"><span data-stu-id="384c1-220">30</span></span>
<span data-ttu-id="384c1-221">Akce</span><span class="sxs-lookup"><span data-stu-id="384c1-221">Events</span></span> | [<span data-ttu-id="384c1-222">Akce</span><span class="sxs-lookup"><span data-stu-id="384c1-222">Events</span></span>](#events) | <span data-ttu-id="384c1-223">Metody `add` `remove` a metody události musí být buď přítomny, nebo chybí.</span><span class="sxs-lookup"><span data-stu-id="384c1-223">The `add` and `remove` methods for an event shall both either be present or absent.</span></span> |<span data-ttu-id="384c1-224">31</span><span class="sxs-lookup"><span data-stu-id="384c1-224">31</span></span>
<span data-ttu-id="384c1-225">Akce</span><span class="sxs-lookup"><span data-stu-id="384c1-225">Events</span></span> | [<span data-ttu-id="384c1-226">Akce</span><span class="sxs-lookup"><span data-stu-id="384c1-226">Events</span></span>](#events) | <span data-ttu-id="384c1-227">Metody `add` `remove` a pro událost musí mít jeden parametr, jehož typ definuje typ události a který musí být odvozen od [System.Delegate](xref:System.Delegate).</span><span class="sxs-lookup"><span data-stu-id="384c1-227">The `add` and `remove` methods for an event shall each take one parameter whose type defines the type of the event and that shall be derived from [System.Delegate](xref:System.Delegate).</span></span> |<span data-ttu-id="384c1-228">32</span><span class="sxs-lookup"><span data-stu-id="384c1-228">32</span></span>
<span data-ttu-id="384c1-229">Akce</span><span class="sxs-lookup"><span data-stu-id="384c1-229">Events</span></span> | [<span data-ttu-id="384c1-230">Akce</span><span class="sxs-lookup"><span data-stu-id="384c1-230">Events</span></span>](#events) | <span data-ttu-id="384c1-231">Události musí dodržovat konkrétní vzor pojmenování.</span><span class="sxs-lookup"><span data-stu-id="384c1-231">Events shall adhere to a specific naming pattern.</span></span> <span data-ttu-id="384c1-232">Atribut SpecialName uvedený v pravidle CLS 29 bude při porovnávání příslušných názvů ignorován a musí dodržovat pravidla identifikátorů.</span><span class="sxs-lookup"><span data-stu-id="384c1-232">The SpecialName attribute referred to in CLS rule 29 shall be ignored in appropriate name comparisons and shall adhere to identifier rules.</span></span>  |<span data-ttu-id="384c1-233">33</span><span class="sxs-lookup"><span data-stu-id="384c1-233">33</span></span>
<span data-ttu-id="384c1-234">Výjimky</span><span class="sxs-lookup"><span data-stu-id="384c1-234">Exceptions</span></span> | [<span data-ttu-id="384c1-235">Výjimky</span><span class="sxs-lookup"><span data-stu-id="384c1-235">Exceptions</span></span>](#exceptions) | <span data-ttu-id="384c1-236">Objekty, které jsou vyvolány musí být typu [System.Exception](xref:System.Exception) nebo typu dědit z něj.</span><span class="sxs-lookup"><span data-stu-id="384c1-236">Objects that are thrown shall be of type [System.Exception](xref:System.Exception) or a type inheriting from it.</span></span> <span data-ttu-id="384c1-237">Metody kompatibilní se standardem CLS však nejsou nutné k blokování šíření jiných typů výjimek.</span><span class="sxs-lookup"><span data-stu-id="384c1-237">Nonetheless, CLS-compliant methods are not required to block the propagation of other types of exceptions.</span></span> | <span data-ttu-id="384c1-238">40</span><span class="sxs-lookup"><span data-stu-id="384c1-238">40</span></span>
<span data-ttu-id="384c1-239">Obecné</span><span class="sxs-lookup"><span data-stu-id="384c1-239">General</span></span> | [<span data-ttu-id="384c1-240">Pravidla dodržování předpisů CLS</span><span class="sxs-lookup"><span data-stu-id="384c1-240">CLS compliance rules</span></span>](#cls-compliance-rules) | <span data-ttu-id="384c1-241">Pravidla CLS platí pouze pro ty části typu, které jsou přístupné nebo viditelné mimo definující sestavu.</span><span class="sxs-lookup"><span data-stu-id="384c1-241">CLS rules apply only to those parts of a type that are accessible or visible outside of the defining assembly.</span></span> | <span data-ttu-id="384c1-242">1</span><span class="sxs-lookup"><span data-stu-id="384c1-242">1</span></span>
<span data-ttu-id="384c1-243">Obecné</span><span class="sxs-lookup"><span data-stu-id="384c1-243">General</span></span> | [<span data-ttu-id="384c1-244">Pravidla dodržování předpisů CLS</span><span class="sxs-lookup"><span data-stu-id="384c1-244">CLS compliance rules</span></span>](#cls-compliance-rules) | <span data-ttu-id="384c1-245">Členové typů, které nejsou kompatibilní se standardem CLS, nesmějí být označeni jako kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-245">Members of non-CLS compliant types shall not be marked CLS-compliant.</span></span> | <span data-ttu-id="384c1-246">2</span><span class="sxs-lookup"><span data-stu-id="384c1-246">2</span></span>
<span data-ttu-id="384c1-247">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="384c1-247">Generics</span></span> | [<span data-ttu-id="384c1-248">Obecné typy a členy</span><span class="sxs-lookup"><span data-stu-id="384c1-248">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="384c1-249">Vnořené typy musí mít alespoň tolik obecných parametrů jako ohraničující typ.</span><span class="sxs-lookup"><span data-stu-id="384c1-249">Nested types shall have at least as many generic parameters as the enclosing type.</span></span> <span data-ttu-id="384c1-250">Obecné parametry v nosného typu odpovídají podle pozice obecným parametrům v jeho ohraničujícím typu.</span><span class="sxs-lookup"><span data-stu-id="384c1-250">Generic parameters in a nested type correspond by position to the generic parameters in its enclosing type.</span></span>  | <span data-ttu-id="384c1-251">42</span><span class="sxs-lookup"><span data-stu-id="384c1-251">42</span></span>
<span data-ttu-id="384c1-252">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="384c1-252">Generics</span></span> | [<span data-ttu-id="384c1-253">Obecné typy a členy</span><span class="sxs-lookup"><span data-stu-id="384c1-253">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="384c1-254">Název obecného typu musí kódovat počet parametrů typu deklarovaných na nevnořeném typu nebo nově zaváděných do typu, pokud je vnořen, podle výše definovaných pravidel.</span><span class="sxs-lookup"><span data-stu-id="384c1-254">The name of a generic type shall encode the number of type parameters declared on the non-nested type, or newly introduced to the type if nested, according to the rules defined above.</span></span> | <span data-ttu-id="384c1-255">43</span><span class="sxs-lookup"><span data-stu-id="384c1-255">43</span></span>
<span data-ttu-id="384c1-256">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="384c1-256">Generics</span></span> | [<span data-ttu-id="384c1-257">Obecné typy a členy</span><span class="sxs-lookup"><span data-stu-id="384c1-257">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="384c1-258">Obecný typ musí znovu deklarovat dostatečná omezení, aby bylo zaručeno, že všechna omezení základního typu nebo rozhraní budou splněna omezeními obecného typu.</span><span class="sxs-lookup"><span data-stu-id="384c1-258">A generic type shall redeclare sufficient constraints to guarantee that any constraints on the base type, or interfaces would be satisfied by the generic type constraints.</span></span> | <span data-ttu-id="384c1-259">44</span><span class="sxs-lookup"><span data-stu-id="384c1-259">44</span></span>
<span data-ttu-id="384c1-260">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="384c1-260">Generics</span></span> | [<span data-ttu-id="384c1-261">Obecné typy a členy</span><span class="sxs-lookup"><span data-stu-id="384c1-261">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="384c1-262">Typy používané jako omezení obecných parametrů musí být samy o sobě kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-262">Types used as constraints on generic parameters shall themselves be CLS-compliant.</span></span> | <span data-ttu-id="384c1-263">45</span><span class="sxs-lookup"><span data-stu-id="384c1-263">45</span></span>
<span data-ttu-id="384c1-264">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="384c1-264">Generics</span></span> | [<span data-ttu-id="384c1-265">Obecné typy a členy</span><span class="sxs-lookup"><span data-stu-id="384c1-265">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="384c1-266">Viditelnost a přístupnost členů (včetně vnořených typů) v instanovaném obecném typu se považuje spíše za vymezenou podle konkrétní instance než za obecné prohlášení typu jako celek.</span><span class="sxs-lookup"><span data-stu-id="384c1-266">The visibility and accessibility of members (including nested types) in an instantiated generic type shall be considered to be scoped to the specific instantiation rather than the generic type declaration as a whole.</span></span> <span data-ttu-id="384c1-267">Za tímto podmínek stále platí pravidla viditelnosti a usnadnění pravidla CLS 12.</span><span class="sxs-lookup"><span data-stu-id="384c1-267">Assuming this, the visibility and accessibility rules of CLS rule 12 still apply.</span></span> | <span data-ttu-id="384c1-268">46</span><span class="sxs-lookup"><span data-stu-id="384c1-268">46</span></span>
<span data-ttu-id="384c1-269">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="384c1-269">Generics</span></span> | [<span data-ttu-id="384c1-270">Obecné typy a členy</span><span class="sxs-lookup"><span data-stu-id="384c1-270">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="384c1-271">Pro každou abstraktní nebo virtuální obecnou metodu musí být k dispozici výchozí konkrétní (neabstraktní) implementace</span><span class="sxs-lookup"><span data-stu-id="384c1-271">For each abstract or virtual generic method, there shall be a default concrete (nonabstract) implementation</span></span> | <span data-ttu-id="384c1-272">47</span><span class="sxs-lookup"><span data-stu-id="384c1-272">47</span></span>
<span data-ttu-id="384c1-273">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="384c1-273">Interfaces</span></span> | [<span data-ttu-id="384c1-274">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="384c1-274">Interfaces</span></span>](#interfaces) | <span data-ttu-id="384c1-275">Rozhraní kompatibilní s cls nesmějí k jejich provádění vyžadovat definici metod, které nejsou kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-275">CLS-compliant interfaces shall not require the definition of non-CLS compliant methods in order to implement them.</span></span> | <span data-ttu-id="384c1-276">18</span><span class="sxs-lookup"><span data-stu-id="384c1-276">18</span></span>
<span data-ttu-id="384c1-277">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="384c1-277">Interfaces</span></span> | [<span data-ttu-id="384c1-278">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="384c1-278">Interfaces</span></span>](#interfaces) | <span data-ttu-id="384c1-279">Rozhraní kompatibilní s CLS nesmějí definovat statické metody ani pole.</span><span class="sxs-lookup"><span data-stu-id="384c1-279">CLS-compliant interfaces shall not define static methods, nor shall they define fields.</span></span> | <span data-ttu-id="384c1-280">19</span><span class="sxs-lookup"><span data-stu-id="384c1-280">19</span></span>
<span data-ttu-id="384c1-281">Členové</span><span class="sxs-lookup"><span data-stu-id="384c1-281">Members</span></span> | [<span data-ttu-id="384c1-282">Typ členů obecně</span><span class="sxs-lookup"><span data-stu-id="384c1-282">Type members in general</span></span>](#type-members-in-general) | <span data-ttu-id="384c1-283">Globální statická pole a metody nejsou kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-283">Global static fields and methods are not CLS-compliant.</span></span> | <span data-ttu-id="384c1-284">36</span><span class="sxs-lookup"><span data-stu-id="384c1-284">36</span></span>
<span data-ttu-id="384c1-285">Členové</span><span class="sxs-lookup"><span data-stu-id="384c1-285">Members</span></span> | -- | <span data-ttu-id="384c1-286">Hodnota literálu statické je určena pomocí metadat inicializace pole.</span><span class="sxs-lookup"><span data-stu-id="384c1-286">The value of a literal static is specified through the use of field initialization metadata.</span></span> <span data-ttu-id="384c1-287">Literál kompatibilní se standardem CLS musí mít hodnotu zadanou v metadatech inicializace pole, která je přesně `enum`stejného typu jako literál (nebo základního typu, pokud je tento literál ).</span><span class="sxs-lookup"><span data-stu-id="384c1-287">A CLS-compliant literal must have a value specified in field initialization metadata that is of exactly the same type as the literal (or of the underlying type, if that literal is an `enum`).</span></span> | <span data-ttu-id="384c1-288">13</span><span class="sxs-lookup"><span data-stu-id="384c1-288">13</span></span>
<span data-ttu-id="384c1-289">Členové</span><span class="sxs-lookup"><span data-stu-id="384c1-289">Members</span></span> | [<span data-ttu-id="384c1-290">Typ členů obecně</span><span class="sxs-lookup"><span data-stu-id="384c1-290">Type members in general</span></span>](#type-members-in-general) | <span data-ttu-id="384c1-291">Omezení vararg není součástí cls a pouze konvence volání podporované CLS je standardní spravované volání konvence.</span><span class="sxs-lookup"><span data-stu-id="384c1-291">The vararg constraint is not part of the CLS, and the only calling convention supported by the CLS is the standard managed calling convention.</span></span> | <span data-ttu-id="384c1-292">15</span><span class="sxs-lookup"><span data-stu-id="384c1-292">15</span></span>
<span data-ttu-id="384c1-293">Zásady vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="384c1-293">Naming conventions</span></span> | [<span data-ttu-id="384c1-294">Zásady vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="384c1-294">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="384c1-295">Sestavy se řídí přílohou 7 technické zprávy 15 standardu Unicode Standard3.0, kterými se řídí soubor znaků povolených pro spuštění a zahrnutí do identifikátorů, které jsou k dispozici online na [formulářích normalizace Unicode](https://www.unicode.org/unicode/reports/tr15/tr15-18.html).</span><span class="sxs-lookup"><span data-stu-id="384c1-295">Assemblies shall follow Annex 7 of Technical Report 15 of the Unicode Standard3.0 governing the set of characters permitted to start and be included in identifiers, available online at [Unicode Normalization Forms](https://www.unicode.org/unicode/reports/tr15/tr15-18.html).</span></span> <span data-ttu-id="384c1-296">Identifikátory musí být v kanonickém formátu definovaném normalizačním formulářem C kódování Unicode. Pro účely cls dva identifikátory jsou stejné, pokud jejich mapování malých písmen (jak je určeno unicode národní ho necitlivý, 1-1 malá písmena mapování) jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="384c1-296">Identifiers shall be in the canonical format defined by Unicode Normalization Form C. For CLS purposes, two identifiers are the same if their lowercase mappings (as specified by the Unicode locale-insensitive, one-to-one lowercase mappings) are the same.</span></span> <span data-ttu-id="384c1-297">To znamená, že pro dva identifikátory, které mají být považovány za odlišné podle CLS, které se liší ve více než jen jejich případě.</span><span class="sxs-lookup"><span data-stu-id="384c1-297">That is, for two identifiers to be considered different under the CLS they shall differ in more than simply their case.</span></span> <span data-ttu-id="384c1-298">Však za účelem přepsání zděděné definice CLI vyžaduje přesné kódování původní deklarace použít.</span><span class="sxs-lookup"><span data-stu-id="384c1-298">However, in order to override an inherited definition the CLI requires the precise encoding of the original declaration be used.</span></span> | <span data-ttu-id="384c1-299">4</span><span class="sxs-lookup"><span data-stu-id="384c1-299">4</span></span>
<span data-ttu-id="384c1-300">Přetížení</span><span class="sxs-lookup"><span data-stu-id="384c1-300">Overloading</span></span> | [<span data-ttu-id="384c1-301">Zásady vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="384c1-301">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="384c1-302">Všechny názvy zavedené v oblasti souladu se standardem CLS musí být odlišné nezávislé svého druhu, s výjimkou případů, kdy jsou názvy totožné a jsou vyřešeny přetížením.</span><span class="sxs-lookup"><span data-stu-id="384c1-302">All names introduced in a CLS-compliant scope shall be distinct independent of kind, except where the names are identical and resolved via overloading.</span></span> <span data-ttu-id="384c1-303">To znamená, že zatímco CTS umožňuje jeden typ použít stejný název pro metodu a pole, CLS není.</span><span class="sxs-lookup"><span data-stu-id="384c1-303">That is, while the CTS allows a single type to use the same name for a method and a field, the CLS does not.</span></span> | <span data-ttu-id="384c1-304">5</span><span class="sxs-lookup"><span data-stu-id="384c1-304">5</span></span>
<span data-ttu-id="384c1-305">Přetížení</span><span class="sxs-lookup"><span data-stu-id="384c1-305">Overloading</span></span> | [<span data-ttu-id="384c1-306">Zásady vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="384c1-306">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="384c1-307">Pole a vnořené typy se odlišují pouze porovnáním identifikátorů, i když CTS umožňuje rozlišit odlišné podpisy.</span><span class="sxs-lookup"><span data-stu-id="384c1-307">Fields and nested types shall be distinct by identifier comparison alone, even though the CTS allows distinct signatures to be distinguished.</span></span> <span data-ttu-id="384c1-308">Metody, vlastnosti a události, které mají stejný název (podle porovnání identifikátorů), se musí lišit o více než jen návratový typ, s výjimkou případů uvedených v pravidle CLS 39</span><span class="sxs-lookup"><span data-stu-id="384c1-308">Methods, properties, and events that have the same name (by identifier comparison) shall differ by more than just the return type,except as specified in CLS Rule 39</span></span> | <span data-ttu-id="384c1-309">6</span><span class="sxs-lookup"><span data-stu-id="384c1-309">6</span></span>
<span data-ttu-id="384c1-310">Přetížení</span><span class="sxs-lookup"><span data-stu-id="384c1-310">Overloading</span></span> | [<span data-ttu-id="384c1-311">Přetížení</span><span class="sxs-lookup"><span data-stu-id="384c1-311">Overloads</span></span>](#overloads) | <span data-ttu-id="384c1-312">Pouze vlastnosti a metody mohou být přetíženy.</span><span class="sxs-lookup"><span data-stu-id="384c1-312">Only properties and methods can be overloaded.</span></span> | <span data-ttu-id="384c1-313">37</span><span class="sxs-lookup"><span data-stu-id="384c1-313">37</span></span>
<span data-ttu-id="384c1-314">Přetížení</span><span class="sxs-lookup"><span data-stu-id="384c1-314">Overloading</span></span> | [<span data-ttu-id="384c1-315">Přetížení</span><span class="sxs-lookup"><span data-stu-id="384c1-315">Overloads</span></span>](#overloads) |<span data-ttu-id="384c1-316">Vlastnosti a metody mohou být přetíženy pouze na základě počtu a `op_Implicit` typů `op_Explicit`jejich parametrů, s výjimkou operátorů převodu s názvem a , které mohou být také přetíženy na základě jejich návratového typu.</span><span class="sxs-lookup"><span data-stu-id="384c1-316">Properties and methods can be overloaded based only on the number and types of their parameters, except the conversion operators named `op_Implicit` and `op_Explicit`, which can also be overloaded based on their return type.</span></span> | <span data-ttu-id="384c1-317">38</span><span class="sxs-lookup"><span data-stu-id="384c1-317">38</span></span>
<span data-ttu-id="384c1-318">Přetížení</span><span class="sxs-lookup"><span data-stu-id="384c1-318">Overloading</span></span> | -- | <span data-ttu-id="384c1-319">Mají-li dvě nebo více metod kompatibilních se standardem CLS deklarované v typu stejný název a pro určitou sadu instancí typu mají stejný parametr a návratové typy, musí být všechny tyto metody sémanticky rovnocenné při těchto instancích typu.</span><span class="sxs-lookup"><span data-stu-id="384c1-319">If two or more CLS-compliant methods declared in a type have the same name and, for a specific set of type instantiations, they have the same parameter and return types, then all these methods shall be semantically equivalent at those type instantiations.</span></span> | <span data-ttu-id="384c1-320">48</span><span class="sxs-lookup"><span data-stu-id="384c1-320">48</span></span>
<span data-ttu-id="384c1-321">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="384c1-321">Properties</span></span> | [<span data-ttu-id="384c1-322">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="384c1-322">Properties</span></span>](#properties) | <span data-ttu-id="384c1-323">Metody, které implementují metody getter a setter vlastnosti, musí být označeny `SpecialName` v metadatech.</span><span class="sxs-lookup"><span data-stu-id="384c1-323">The methods that implement the getter and setter methods of a property shall be marked `SpecialName` in the metadata.</span></span> | <span data-ttu-id="384c1-324">24</span><span class="sxs-lookup"><span data-stu-id="384c1-324">24</span></span>
<span data-ttu-id="384c1-325">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="384c1-325">Properties</span></span> | [<span data-ttu-id="384c1-326">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="384c1-326">Properties</span></span>](#properties) | <span data-ttu-id="384c1-327">Všechny přistupující objekty vlastnosti musí být statické, všechny virtuální nebo všechny instance.</span><span class="sxs-lookup"><span data-stu-id="384c1-327">A property’s accessors shall all be static, all be virtual, or all be instance.</span></span> | <span data-ttu-id="384c1-328">26</span><span class="sxs-lookup"><span data-stu-id="384c1-328">26</span></span>
<span data-ttu-id="384c1-329">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="384c1-329">Properties</span></span> | [<span data-ttu-id="384c1-330">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="384c1-330">Properties</span></span>](#properties) | <span data-ttu-id="384c1-331">Typ vlastnosti musí být návratový typ getter a typ posledního argumentu setter.</span><span class="sxs-lookup"><span data-stu-id="384c1-331">The type of a property shall be the return type of the getter and the type of the last argument of the setter.</span></span> <span data-ttu-id="384c1-332">Typy parametrů vlastnosti musí být typy parametrů pro getter a typy všech, kromě konečného parametru setteru.</span><span class="sxs-lookup"><span data-stu-id="384c1-332">The types of the parameters of the property shall be the types of the parameters to the getter and the types of all but the final parameter of the setter.</span></span> <span data-ttu-id="384c1-333">Všechny tyto typy musí být kompatibilní se standardem CLS a nesmí být spravovány ukazatele (to znamená, nesmí být předány odkazem).</span><span class="sxs-lookup"><span data-stu-id="384c1-333">All of these types shall be CLS-compliant, and shall not be managed pointers (that is, shall not be passed by reference).</span></span> | <span data-ttu-id="384c1-334">27</span><span class="sxs-lookup"><span data-stu-id="384c1-334">27</span></span>
<span data-ttu-id="384c1-335">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="384c1-335">Properties</span></span> | [<span data-ttu-id="384c1-336">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="384c1-336">Properties</span></span>](#properties) | <span data-ttu-id="384c1-337">Vlastnosti musí splňovat konkrétní vzor pojmenování.</span><span class="sxs-lookup"><span data-stu-id="384c1-337">Properties shall adhere to a specific naming pattern.</span></span> <span data-ttu-id="384c1-338">Atribut `SpecialName` uvedený v pravidle CLS 24 se při porovnávání názvů ignoruje a musí dodržovat pravidla identifikátorů.</span><span class="sxs-lookup"><span data-stu-id="384c1-338">The `SpecialName` attribute referred to in CLS rule 24 shall be ignored in appropriate name comparisons and shall adhere to identifier rules.</span></span> <span data-ttu-id="384c1-339">Vlastnost musí mít getter metoda, setter metoda nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="384c1-339">A property shall have a getter method, a setter method, or both.</span></span> | <span data-ttu-id="384c1-340">28</span><span class="sxs-lookup"><span data-stu-id="384c1-340">28</span></span>
<span data-ttu-id="384c1-341">Převod typů</span><span class="sxs-lookup"><span data-stu-id="384c1-341">Type conversion</span></span> | [<span data-ttu-id="384c1-342">Převod typů</span><span class="sxs-lookup"><span data-stu-id="384c1-342">Type conversion</span></span>](#type-conversion) | <span data-ttu-id="384c1-343">Je-li k dispozici op_Implicit nebo op_Explicit, musí být poskytnuty alternativní prostředky pro zajištění nátlaku.</span><span class="sxs-lookup"><span data-stu-id="384c1-343">If either op_Implicit or op_Explicit is provided, an alternate means of providing the coercion shall be provided.</span></span> | <span data-ttu-id="384c1-344">39</span><span class="sxs-lookup"><span data-stu-id="384c1-344">39</span></span>
<span data-ttu-id="384c1-345">Typy</span><span class="sxs-lookup"><span data-stu-id="384c1-345">Types</span></span> | [<span data-ttu-id="384c1-346">Typy a podpisy členů typu</span><span class="sxs-lookup"><span data-stu-id="384c1-346">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="384c1-347">Typy hodnot v rámečku nejsou kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-347">Boxed value types are not CLS-compliant.</span></span> | <span data-ttu-id="384c1-348">3</span><span class="sxs-lookup"><span data-stu-id="384c1-348">3</span></span>
<span data-ttu-id="384c1-349">Typy</span><span class="sxs-lookup"><span data-stu-id="384c1-349">Types</span></span> | [<span data-ttu-id="384c1-350">Typy a podpisy členů typu</span><span class="sxs-lookup"><span data-stu-id="384c1-350">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="384c1-351">Všechny typy uvedené v podpisu musí být kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-351">All types appearing in a signature shall be CLS-compliant.</span></span> <span data-ttu-id="384c1-352">Všechny typy, které tvoří typ typu instanovaného obecného typu, musí být kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-352">All types composing an instantiated generic type shall be CLS-compliant.</span></span> | <span data-ttu-id="384c1-353">11</span><span class="sxs-lookup"><span data-stu-id="384c1-353">11</span></span>
<span data-ttu-id="384c1-354">Typy</span><span class="sxs-lookup"><span data-stu-id="384c1-354">Types</span></span> | [<span data-ttu-id="384c1-355">Typy a podpisy členů typu</span><span class="sxs-lookup"><span data-stu-id="384c1-355">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="384c1-356">Zadané odkazy nejsou kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-356">Typed references are not CLS-compliant.</span></span> | <span data-ttu-id="384c1-357">14</span><span class="sxs-lookup"><span data-stu-id="384c1-357">14</span></span>
<span data-ttu-id="384c1-358">Typy</span><span class="sxs-lookup"><span data-stu-id="384c1-358">Types</span></span> | [<span data-ttu-id="384c1-359">Typy a podpisy členů typu</span><span class="sxs-lookup"><span data-stu-id="384c1-359">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="384c1-360">Nespravované typy ukazatelů nejsou kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-360">Unmanaged pointer types are not CLS-compliant.</span></span> | <span data-ttu-id="384c1-361">17</span><span class="sxs-lookup"><span data-stu-id="384c1-361">17</span></span>
<span data-ttu-id="384c1-362">Typy</span><span class="sxs-lookup"><span data-stu-id="384c1-362">Types</span></span> | [<span data-ttu-id="384c1-363">Typy a podpisy členů typu</span><span class="sxs-lookup"><span data-stu-id="384c1-363">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="384c1-364">Třídy, typy hodnot a rozhraní kompatibilní se standardem CLS nevyžadují implementaci členů, kteří nejsou kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-364">CLS-compliant classes, value types, and interfaces shall not require the implementation of non-CLS-compliant members</span></span> | <span data-ttu-id="384c1-365">20</span><span class="sxs-lookup"><span data-stu-id="384c1-365">20</span></span>
<span data-ttu-id="384c1-366">Typy</span><span class="sxs-lookup"><span data-stu-id="384c1-366">Types</span></span> | [<span data-ttu-id="384c1-367">Typy a podpisy členů typu</span><span class="sxs-lookup"><span data-stu-id="384c1-367">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="384c1-368">[System.Object](xref:System.Object) je kompatibilní se systémem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-368">[System.Object](xref:System.Object) is CLS-compliant.</span></span> <span data-ttu-id="384c1-369">Všechny ostatní třídy kompatibilní se standardem CLS dědí z třídy kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-369">Any other CLS-compliant class shall inherit from a CLS-compliant class.</span></span> | <span data-ttu-id="384c1-370">23</span><span class="sxs-lookup"><span data-stu-id="384c1-370">23</span></span>

### <a name="types-and-type-member-signatures"></a><span data-ttu-id="384c1-371">Typy a podpisy členů typu</span><span class="sxs-lookup"><span data-stu-id="384c1-371">Types and type member signatures</span></span>

<span data-ttu-id="384c1-372">Typ [System.Object](xref:System.Object) je kompatibilní se systémem CLS a je základním typem všech typů objektů v systému typu rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="384c1-372">The [System.Object](xref:System.Object) type is CLS-compliant and is the base type of all object types in the .NET Framework type system.</span></span> <span data-ttu-id="384c1-373">Dědičnost v rozhraní .NET Framework je [String](xref:System.String) implicitní (například třída `Object` String implicitně dědí z třídy) nebo explicitní (například třída [CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) explicitně dědí z třídy [ArgumentException,](xref:System.ArgumentException) která explicitně dědí z třídy [Exception.](xref:System.Exception)</span><span class="sxs-lookup"><span data-stu-id="384c1-373">Inheritance in the .NET Framework is either implicit (for example, the [String](xref:System.String) class implicitly inherits from the `Object` class) or explicit (for example, the [CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) class explicitly inherits from the [ArgumentException](xref:System.ArgumentException) class, which explicitly inherits from the [Exception](xref:System.Exception) class.</span></span> <span data-ttu-id="384c1-374">Aby byl odvozený typ kompatibilní se standardem CLS, musí být jeho základní typ také kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-374">For a derived type to be CLS compliant, its base type must also be CLS-compliant.</span></span>

<span data-ttu-id="384c1-375">Následující příklad ukazuje odvozený typ, jehož základní typ není kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-375">The following example shows a derived type whose base type is not CLS-compliant.</span></span> <span data-ttu-id="384c1-376">Definuje základní `Counter` třídu, která používá nepodepsané 32bitové celé číslo jako čítač.</span><span class="sxs-lookup"><span data-stu-id="384c1-376">It defines a base `Counter` class that uses an unsigned 32-bit integer as a counter.</span></span> <span data-ttu-id="384c1-377">Vzhledem k tomu, že třída poskytuje funkci čítače zabalením nepodepsaného celého čísla, je třída označena jako nekompatibilní se souborem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-377">Because the class provides counter functionality by wrapping an unsigned integer, the class is marked as non-CLS-compliant.</span></span> <span data-ttu-id="384c1-378">V důsledku toho odvozené `NonZeroCounter`třídy , také není kompatibilní se seznamem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-378">As a result, a derived class, `NonZeroCounter`, is also not CLS-compliant.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

[CLSCompliant(false)]
public class Counter
{
   UInt32 ctr;

   public Counter()
   {
      ctr = 0;
   }

   protected Counter(UInt32 ctr)
   {
      this.ctr = ctr;
   }

   public override string ToString()
   {
      return $"{ctr}). ";
   }

   public UInt32 Value
   {
      get { return ctr; }
   }

   public void Increment()
   {
      ctr += (uint) 1;
   }
}

public class NonZeroCounter : Counter
{
   public NonZeroCounter(int startIndex) : this((uint) startIndex)
   {
   }

   private NonZeroCounter(UInt32 startIndex) : base(startIndex)
   {
   }
}
// Compilation produces a compiler warning like the following:
//    Type3.cs(37,14): warning CS3009: 'NonZeroCounter': base type 'Counter' is not
//            CLS-compliant
//    Type3.cs(7,14): (Location of symbol related to previous warning)
```

```vb
<Assembly: CLSCompliant(True)>

<CLSCompliant(False)> _
Public Class Counter
   Dim ctr As UInt32

   Public Sub New
      ctr = 0
   End Sub

   Protected Sub New(ctr As UInt32)
      ctr = ctr
   End Sub

   Public Overrides Function ToString() As String
      Return $"{ctr}). "
   End Function

   Public ReadOnly Property Value As UInt32
      Get
         Return ctr
      End Get
   End Property

   Public Sub Increment()
      ctr += CType(1, UInt32)
   End Sub
End Class

Public Class NonZeroCounter : Inherits Counter
   Public Sub New(startIndex As Integer)
      MyClass.New(CType(startIndex, UInt32))
   End Sub

   Private Sub New(startIndex As UInt32)
      MyBase.New(CType(startIndex, UInt32))
   End Sub
End Class
' Compilation produces a compiler warning like the following:
'    Type3.vb(34) : warning BC40026: 'NonZeroCounter' is not CLS-compliant
'    because it derives from 'Counter', which is not CLS-compliant.
'
'    Public Class NonZeroCounter : Inherits Counter
'                 ~~~~~~~~~~~~~~
```

<span data-ttu-id="384c1-379">Všechny typy, které se zobrazují v podpisech členů, včetně návratového typu metody nebo typu vlastnosti, musí být kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-379">All types that appear in member signatures, including a method's return type or a property type, must be CLS-compliant.</span></span> <span data-ttu-id="384c1-380">Kromě toho pro obecné typy:</span><span class="sxs-lookup"><span data-stu-id="384c1-380">In addition, for generic types:</span></span>

* <span data-ttu-id="384c1-381">Všechny typy, které tvoří instanci obecný typ musí být kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-381">All types that compose an instantiated generic type must be CLS-compliant.</span></span>

* <span data-ttu-id="384c1-382">Všechny typy používané jako omezení obecných parametrů musí být kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-382">All types used as constraints on generic parameters must be CLS-compliant.</span></span>

<span data-ttu-id="384c1-383">[Systém běžného typu](common-type-system.md) .NET obsahuje řadu předdefinovaných typů, které jsou podporovány přímo modulem COMMON Language runtime a jsou speciálně kódovány v metadatech sestavení.</span><span class="sxs-lookup"><span data-stu-id="384c1-383">The .NET [common type system](common-type-system.md) includes a number of built-in types that are supported directly by the common language runtime and are specially encoded in an assembly's metadata.</span></span> <span data-ttu-id="384c1-384">Z těchto vnitřních typů jsou typy uvedené v následující tabulce kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-384">Of these intrinsic types, the types listed in the following table are CLS-compliant.</span></span>

<span data-ttu-id="384c1-385">Typ kompatibilní se standardem CLS</span><span class="sxs-lookup"><span data-stu-id="384c1-385">CLS-compliant type</span></span> | <span data-ttu-id="384c1-386">Popis</span><span class="sxs-lookup"><span data-stu-id="384c1-386">Description</span></span>
------------------ | -----------
[<span data-ttu-id="384c1-387">Byte</span><span class="sxs-lookup"><span data-stu-id="384c1-387">Byte</span></span>](xref:System.Byte) | <span data-ttu-id="384c1-388">Osmibitové celé číslo bez znaménka</span><span class="sxs-lookup"><span data-stu-id="384c1-388">8-bit unsigned integer</span></span>
[<span data-ttu-id="384c1-389">Int16</span><span class="sxs-lookup"><span data-stu-id="384c1-389">Int16</span></span>](xref:System.Int16) | <span data-ttu-id="384c1-390">16bitové podepsané celé číslo</span><span class="sxs-lookup"><span data-stu-id="384c1-390">16-bit signed integer</span></span>
[<span data-ttu-id="384c1-391">Int32</span><span class="sxs-lookup"><span data-stu-id="384c1-391">Int32</span></span>](xref:System.Int32) | <span data-ttu-id="384c1-392">32bitové podepsané celé číslo</span><span class="sxs-lookup"><span data-stu-id="384c1-392">32-bit signed integer</span></span>
[<span data-ttu-id="384c1-393">Int64</span><span class="sxs-lookup"><span data-stu-id="384c1-393">Int64</span></span>](xref:System.Int64) | <span data-ttu-id="384c1-394">64bitové podepsané celé číslo</span><span class="sxs-lookup"><span data-stu-id="384c1-394">64-bit signed integer</span></span>
[<span data-ttu-id="384c1-395">Single</span><span class="sxs-lookup"><span data-stu-id="384c1-395">Single</span></span>](xref:System.Single) | <span data-ttu-id="384c1-396">Hodnota s plovoucí desetinnou desetinnou s jednou přesností</span><span class="sxs-lookup"><span data-stu-id="384c1-396">Single-precision floating-point value</span></span>
[<span data-ttu-id="384c1-397">Dvojité</span><span class="sxs-lookup"><span data-stu-id="384c1-397">Double</span></span>](xref:System.Double) | <span data-ttu-id="384c1-398">Hodnota s dvojitou přesností s plovoucí desetinnou desetinnou desetinnou hodnotou</span><span class="sxs-lookup"><span data-stu-id="384c1-398">Double-precision floating-point value</span></span>
[<span data-ttu-id="384c1-399">Logická hodnota</span><span class="sxs-lookup"><span data-stu-id="384c1-399">Boolean</span></span>](xref:System.Boolean) | <span data-ttu-id="384c1-400">typ hodnoty true nebo false</span><span class="sxs-lookup"><span data-stu-id="384c1-400">true or false value type</span></span>
[<span data-ttu-id="384c1-401">Char</span><span class="sxs-lookup"><span data-stu-id="384c1-401">Char</span></span>](xref:System.Char) | <span data-ttu-id="384c1-402">Jednotka kódovaného kódu UTF-16</span><span class="sxs-lookup"><span data-stu-id="384c1-402">UTF-16 encoded code unit</span></span>
[<span data-ttu-id="384c1-403">Desetinných</span><span class="sxs-lookup"><span data-stu-id="384c1-403">Decimal</span></span>](xref:System.Decimal) | <span data-ttu-id="384c1-404">Desítkové číslo bez plovoucí desetinné čárky</span><span class="sxs-lookup"><span data-stu-id="384c1-404">Non-floating-point decimal number</span></span>
[<span data-ttu-id="384c1-405">Intptr</span><span class="sxs-lookup"><span data-stu-id="384c1-405">IntPtr</span></span>](xref:System.IntPtr) | <span data-ttu-id="384c1-406">Ukazatel nebo úchyt definované platformou</span><span class="sxs-lookup"><span data-stu-id="384c1-406">Pointer or handle of a platform-defined size</span></span>
[<span data-ttu-id="384c1-407">Řetězec</span><span class="sxs-lookup"><span data-stu-id="384c1-407">String</span></span>](xref:System.String) | <span data-ttu-id="384c1-408">Kolekce objektů s nulou, jedním nebo více char</span><span class="sxs-lookup"><span data-stu-id="384c1-408">Collection of zero, one, or more Char objects</span></span>

<span data-ttu-id="384c1-409">Vnitřní typy uvedené v následující tabulce nejsou kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-409">The intrinsic types listed in the following table are not CLS-Compliant.</span></span>

<span data-ttu-id="384c1-410">Nevyhovující typ</span><span class="sxs-lookup"><span data-stu-id="384c1-410">Non-compliant type</span></span> | <span data-ttu-id="384c1-411">Popis</span><span class="sxs-lookup"><span data-stu-id="384c1-411">Description</span></span> | <span data-ttu-id="384c1-412">Alternativa odpovídající specifikaci CLS</span><span class="sxs-lookup"><span data-stu-id="384c1-412">CLS-compliant alternative</span></span>
------------------ | ----------- | -------------------------
[<span data-ttu-id="384c1-413">Sbyte</span><span class="sxs-lookup"><span data-stu-id="384c1-413">SByte</span></span>](xref:System.SByte) | <span data-ttu-id="384c1-414">Osmibitový podepsaný celočíselný datový typ</span><span class="sxs-lookup"><span data-stu-id="384c1-414">8-bit signed integer data type</span></span> | [<span data-ttu-id="384c1-415">Int16</span><span class="sxs-lookup"><span data-stu-id="384c1-415">Int16</span></span>](xref:System.Int16)
[<span data-ttu-id="384c1-416">UInt16</span><span class="sxs-lookup"><span data-stu-id="384c1-416">UInt16</span></span>](xref:System.UInt16) | <span data-ttu-id="384c1-417">16bitové celé celé číslo bez znaménka</span><span class="sxs-lookup"><span data-stu-id="384c1-417">16-bit unsigned integer</span></span> | [<span data-ttu-id="384c1-418">Int32</span><span class="sxs-lookup"><span data-stu-id="384c1-418">Int32</span></span>](xref:System.Int32)
[<span data-ttu-id="384c1-419">UInt32</span><span class="sxs-lookup"><span data-stu-id="384c1-419">UInt32</span></span>](xref:System.UInt32) | <span data-ttu-id="384c1-420">32bitové celé celé číslo bez znaménka</span><span class="sxs-lookup"><span data-stu-id="384c1-420">32-bit unsigned integer</span></span> | [<span data-ttu-id="384c1-421">Int64</span><span class="sxs-lookup"><span data-stu-id="384c1-421">Int64</span></span>](xref:System.Int64)
[<span data-ttu-id="384c1-422">UInt64</span><span class="sxs-lookup"><span data-stu-id="384c1-422">UInt64</span></span>](xref:System.UInt64) | <span data-ttu-id="384c1-423">64bitové celé celé číslo bez znaménka</span><span class="sxs-lookup"><span data-stu-id="384c1-423">64-bit unsigned integer</span></span> | <span data-ttu-id="384c1-424">[Int64](xref:System.Int64) (může přetečení), [BigInteger](xref:System.Numerics.BigInteger), nebo [Double](xref:System.Double)</span><span class="sxs-lookup"><span data-stu-id="384c1-424">[Int64](xref:System.Int64) (may overflow), [BigInteger](xref:System.Numerics.BigInteger), or [Double](xref:System.Double)</span></span>
[<span data-ttu-id="384c1-425">UIntPtr</span><span class="sxs-lookup"><span data-stu-id="384c1-425">UIntPtr</span></span>](xref:System.UIntPtr) | <span data-ttu-id="384c1-426">Nepodepsaný ukazatel nebo popisovač</span><span class="sxs-lookup"><span data-stu-id="384c1-426">Unsigned pointer or handle</span></span> | [<span data-ttu-id="384c1-427">Intptr</span><span class="sxs-lookup"><span data-stu-id="384c1-427">IntPtr</span></span>](xref:System.IntPtr)

<span data-ttu-id="384c1-428">Knihovna tříd rozhraní .NET Framework nebo jakákoli jiná knihovna tříd může obsahovat jiné typy, které nejsou kompatibilní se standardem CLS. například:</span><span class="sxs-lookup"><span data-stu-id="384c1-428">The .NET Framework Class Library or any other class library may include other types that aren't CLS-compliant; for example:</span></span>

* <span data-ttu-id="384c1-429">Typy hodnot v rámečku.</span><span class="sxs-lookup"><span data-stu-id="384c1-429">Boxed value types.</span></span> <span data-ttu-id="384c1-430">Následující příklad jazyka C# vytvoří třídu, `int`která `Value`má veřejnou vlastnost typu \* s názvem .</span><span class="sxs-lookup"><span data-stu-id="384c1-430">The following C# example creates a class that has a public property of type `int`\* named `Value`.</span></span> <span data-ttu-id="384c1-431">Vzhledem `int`k tomu, že \* je zabalený typ hodnoty, kompilátor jej označí jako nekompatibilní se souborem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-431">Because an `int`\* is a boxed value type, the compiler flags it as non-CLS-compliant.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public unsafe class TestClass
{
   private int* val;

   public TestClass(int number)
   {
      val = (int*) number;
   }

   public int* Value {
      get { return val; }
   }
}
// The compiler generates the following output when compiling this example:
//        warning CS3003: Type of 'TestClass.Value' is not CLS-compliant
```

* <span data-ttu-id="384c1-432">Zadané odkazy, které jsou speciální konstrukce, které obsahují odkaz na objekt a odkaz na typ.</span><span class="sxs-lookup"><span data-stu-id="384c1-432">Typed references, which are special constructs that contain a reference to an object and a reference to a type.</span></span>

<span data-ttu-id="384c1-433">Pokud typ není kompatibilní se souborem CLS, měli byste použít atribut [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) s parametrem *isCompliant* s jeho hodnotou. `false`</span><span class="sxs-lookup"><span data-stu-id="384c1-433">If a type is not CLS-compliant, you should apply the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute with an *isCompliant* parameter with a value of `false` to it.</span></span> <span data-ttu-id="384c1-434">Další informace naleznete v části [atributu CLSCompliantAttribute.](#the-clscompliantattribute-attribute)</span><span class="sxs-lookup"><span data-stu-id="384c1-434">For more information, see the [CLSCompliantAttribute attribute](#the-clscompliantattribute-attribute) section.</span></span>

<span data-ttu-id="384c1-435">Následující příklad ilustruje problém dodržování cls v podpisu metody a v obecném typu instanování.</span><span class="sxs-lookup"><span data-stu-id="384c1-435">The following example illustrates the problem of CLS compliance in a method signature and in generic type instantiation.</span></span> <span data-ttu-id="384c1-436">Definuje třídu `InvoiceItem` s vlastností typu [UInt32](xref:System.UInt32), vlastnost typu [Nullable(Of UInt32)](xref:System.Nullable%601)a konstruktor `UInt32` `Nullable(Of UInt32)`s parametry typu a .</span><span class="sxs-lookup"><span data-stu-id="384c1-436">It defines an `InvoiceItem` class with a property of type [UInt32](xref:System.UInt32), a property of type [Nullable(Of UInt32)](xref:System.Nullable%601), and a constructor with parameters of type `UInt32` and `Nullable(Of UInt32)`.</span></span> <span data-ttu-id="384c1-437">Při pokusu o kompilaci v tomto příkladu se zobrazí čtyři upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="384c1-437">You get four compiler warnings when you try to compile this example.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class InvoiceItem
{
   private uint invId = 0;
   private uint itemId = 0;
   private Nullable<uint> qty;

   public InvoiceItem(uint sku, Nullable<uint> quantity)
   {
      itemId = sku;
      qty = quantity;
   }

   public Nullable<uint> Quantity
   {
      get { return qty; }
      set { qty = value; }
   }

   public uint InvoiceId
   {
      get { return invId; }
      set { invId = value; }
   }
}
// The attempt to compile the example displays the following output:
//    Type1.cs(13,23): warning CS3001: Argument type 'uint' is not CLS-compliant
//    Type1.cs(13,33): warning CS3001: Argument type 'uint?' is not CLS-compliant
//    Type1.cs(19,26): warning CS3003: Type of 'InvoiceItem.Quantity' is not CLS-compliant
//    Type1.cs(25,16): warning CS3003: Type of 'InvoiceItem.InvoiceId' is not CLS-compliant
```

```vb
<Assembly: CLSCompliant(True)>

Public Class InvoiceItem

   Private invId As UInteger = 0
   Private itemId As UInteger = 0
   Private qty AS Nullable(Of UInteger)

   Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
      itemId = sku
      qty = quantity
   End Sub

   Public Property Quantity As Nullable(Of UInteger)
      Get
         Return qty
      End Get
      Set
         qty = value
      End Set
   End Property

   Public Property InvoiceId As UInteger
      Get
         Return invId
      End Get
      Set
         invId = value
      End Set
   End Property
End Class
' The attempt to compile the example displays output similar to the following:
'    Type1.vb(13) : warning BC40028: Type of parameter 'sku' is not CLS-compliant.
'
'       Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
'                      ~~~
'    Type1.vb(13) : warning BC40041: Type 'UInteger' is not CLS-compliant.
'
'       Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
'                                                               ~~~~~~~~
'    Type1.vb(18) : warning BC40041: Type 'UInteger' is not CLS-compliant.
'
'       Public Property Quantity As Nullable(Of UInteger)
'                                               ~~~~~~~~
'    Type1.vb(27) : warning BC40027: Return type of function 'InvoiceId' is not CLS-compliant.
'
'       Public Property InvoiceId As UInteger
```

<span data-ttu-id="384c1-438">Chcete-li odstranit upozornění kompilátoru, nahraďte `InvoiceItem` typy, které nejsou kompatibilní se standardem CLS ve veřejném rozhraní, kompatibilními typy:</span><span class="sxs-lookup"><span data-stu-id="384c1-438">To eliminate the compiler warnings, replace the non-CLS-compliant types in the `InvoiceItem` public interface with compliant types:</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class InvoiceItem
{
   private uint invId = 0;
   private uint itemId = 0;
   private Nullable<int> qty;

   public InvoiceItem(int sku, Nullable<int> quantity)
   {
      if (sku <= 0)
         throw new ArgumentOutOfRangeException("The item number is zero or negative.");
      itemId = (uint) sku;

      qty = quantity;
   }

   public Nullable<int> Quantity
   {
      get { return qty; }
      set { qty = value; }
   }

   public int InvoiceId
   {
      get { return (int) invId; }
      set {
         if (value <= 0)
            throw new ArgumentOutOfRangeException("The invoice number is zero or negative.");
         invId = (uint) value; }
   }
}
```

```vb
Assembly: CLSCompliant(True)>

Public Class InvoiceItem

   Private invId As UInteger = 0
   Private itemId As UInteger = 0
   Private qty AS Nullable(Of Integer)

   Public Sub New(sku As Integer, quantity As Nullable(Of Integer))
      If sku <= 0 Then
         Throw New ArgumentOutOfRangeException("The item number is zero or negative.")
      End If
      itemId = CUInt(sku)
      qty = quantity
   End Sub

   Public Property Quantity As Nullable(Of Integer)
      Get
         Return qty
      End Get
      Set
         qty = value
      End Set
   End Property

   Public Property InvoiceId As Integer
      Get
         Return CInt(invId)
      End Get
      Set
         invId = CUInt(value)
      End Set
   End Property
End Class
```

<span data-ttu-id="384c1-439">Kromě konkrétních uvedených typů nejsou některé kategorie typů kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-439">In addition to the specific types listed, some categories of types are not CLS compliant.</span></span> <span data-ttu-id="384c1-440">Patří mezi ně nespravované typy ukazatelů a typy ukazatelů funkce.</span><span class="sxs-lookup"><span data-stu-id="384c1-440">These include unmanaged pointer types and function pointer types.</span></span> <span data-ttu-id="384c1-441">Následující příklad generuje upozornění kompilátoru, protože používá ukazatel na celé číslo k vytvoření pole celá čísla.</span><span class="sxs-lookup"><span data-stu-id="384c1-441">The following example generates a compiler warning because it uses a pointer to an integer to create an array of integers.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ArrayHelper
{
   unsafe public static Array CreateInstance(Type type, int* ptr, int items)
   {
      Array arr = Array.CreateInstance(type, items);
      int* addr = ptr;
      for (int ctr = 0; ctr < items; ctr++) {
          int value = *addr;
          arr.SetValue(value, ctr);
          addr++;
      }
      return arr;
   }
}
// The attempt to compile this example displays the following output:
//    UnmanagedPtr1.cs(8,57): warning CS3001: Argument type 'int*' is not CLS-compliant
```

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ArrayHelper
{
   unsafe public static Array CreateInstance(Type type, int* ptr, int items)
   {
      Array arr = Array.CreateInstance(type, items);
      int* addr = ptr;
      for (int ctr = 0; ctr < items; ctr++) {
          int value = *addr;
          arr.SetValue(value, ctr);
          addr++;
      }
      return arr;
   }
}
// The attempt to compile this example displays the following output:
//    UnmanagedPtr1.cs(8,57): warning CS3001: Argument type 'int*' is not CLS-compliant
```

<span data-ttu-id="384c1-442">Pro abstraktní třídy kompatibilní se seznamem `abstract` CLS (to znamená třídy označené jako v c#) musí být všichni členové třídy také kompatibilní se seznamem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-442">For CLS-compliant abstract classes (that is, classes marked as `abstract` in C#), all members of the class must also be CLS-compliant.</span></span>

### <a name="naming-conventions"></a><span data-ttu-id="384c1-443">Zásady vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="384c1-443">Naming conventions</span></span>

<span data-ttu-id="384c1-444">Vzhledem k tomu, že některé programovací jazyky nerozlišují malá a velká písmena, identifikátory (například názvy oborů názvů, typů a členů) se musí lišit o více než malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="384c1-444">Because some programming languages are case-insensitive, identifiers (such as the names of namespaces, types, and members) must differ by more than case.</span></span> <span data-ttu-id="384c1-445">Dva identifikátory jsou považovány za rovnocenné, pokud jejich mapování s nižšími písmeny jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="384c1-445">Two identifiers are considered equivalent if their lowercase mappings are the same.</span></span> <span data-ttu-id="384c1-446">Následující příklad jazyka C# definuje `Person` dvě `person`veřejné třídy a .</span><span class="sxs-lookup"><span data-stu-id="384c1-446">The following C# example defines two public classes, `Person` and `person`.</span></span> <span data-ttu-id="384c1-447">Vzhledem k tomu, že se liší pouze podle případu, kompilátor Jazyka C# je označí jako nekompatibilní se seznamem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-447">Because they differ only by case, the C# compiler flags them as not CLS-compliant.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person : person
{

}

public class person
{

}
// Compilation produces a compiler warning like the following:
//    Naming1.cs(11,14): warning CS3005: Identifier 'person' differing
//                       only in case is not CLS-compliant
//    Naming1.cs(6,14): (Location of symbol related to previous warning)
```

<span data-ttu-id="384c1-448">Identifikátory programovacích jazyků, jako jsou názvy jmenných prostorů, typů a členů, musí odpovídat [normě Unicode 3.0, Technické zprávě 15, příloha 7](https://www.unicode.org/reports/tr15/tr15-18.html).</span><span class="sxs-lookup"><span data-stu-id="384c1-448">Programming language identifiers, such as the names of namespaces, types, and members, must conform to the [Unicode Standard 3.0, Technical Report 15, Annex 7](https://www.unicode.org/reports/tr15/tr15-18.html).</span></span> <span data-ttu-id="384c1-449">To znamená, že:</span><span class="sxs-lookup"><span data-stu-id="384c1-449">This means that:</span></span>

* <span data-ttu-id="384c1-450">Prvním znakem identifikátoru může být libovolné velké písmeno Unicode, malé písmeno, písmeno nadpisu, modifikační písmeno, jiné písmeno nebo písmeno.</span><span class="sxs-lookup"><span data-stu-id="384c1-450">The first character of an identifier can be any Unicode uppercase letter, lowercase letter, title case letter, modifier letter, other letter, or letter number.</span></span> <span data-ttu-id="384c1-451">Informace o kategoriích znaků Unicode naleznete ve výčtu [System.Globalization.UnicodeCategory.](xref:System.Globalization.UnicodeCategory)</span><span class="sxs-lookup"><span data-stu-id="384c1-451">For information on Unicode character categories, see the [System.Globalization.UnicodeCategory](xref:System.Globalization.UnicodeCategory) enumeration.</span></span>

* <span data-ttu-id="384c1-452">Následující znaky mohou být z libovolné z kategorií jako první znak a mohou také obsahovat značky bez mezer, mezery kombinující značky, desetinná čísla, interpunkce spojnice a formátovací kódy.</span><span class="sxs-lookup"><span data-stu-id="384c1-452">Subsequent characters can be from any of the categories as the first character, and can also include non-spacing marks, spacing combining marks, decimal numbers, connector punctuations, and formatting codes.</span></span>

<span data-ttu-id="384c1-453">Před porovnáním identifikátorů byste měli odfiltrovat formátovací kódy a převést identifikátory na formulář C normalizace kódování Unicode, protože jeden znak může být reprezentován více jednotkami kódu kódovaných UTF-16.</span><span class="sxs-lookup"><span data-stu-id="384c1-453">Before you compare identifiers, you should filter out formatting codes and convert the identifiers to Unicode Normalization Form C, because a single character can be represented by multiple UTF-16-encoded code units.</span></span> <span data-ttu-id="384c1-454">Posloupnosti znaků, které vytvářejí stejné jednotky kódu ve formuláři C normalizace kódování Unicode, nejsou kompatibilní se seznamem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-454">Character sequences that produce the same code units in Unicode Normalization Form C are not CLS-compliant.</span></span> <span data-ttu-id="384c1-455">Následující příklad definuje vlastnost `Å`s názvem , která se skládá z znaku ANGSTROM sign (U + 212B) a druhá vlastnost s názvem, `Å` která se skládá ze znaku latinka velké písmeno a s kroužkem nad (U + 00C5).</span><span class="sxs-lookup"><span data-stu-id="384c1-455">The following example defines a property named `Å`, which consists of the character ANGSTROM SIGN (U+212B), and a second property named `Å` which consists of the character LATIN CAPITAL LETTER A WITH RING ABOVE (U+00C5).</span></span> <span data-ttu-id="384c1-456">Kompilátor Jazyka C# označí zdrojový kód jako nekompatibilní se souborem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-456">The C# compiler flags the source code as non-CLS-compliant.</span></span>

```csharp
public class Size
{
   private double a1;
   private double a2;

   public double Å
   {
       get { return a1; }
       set { a1 = value; }
   }

   public double Å
   {
       get { return a2; }
       set { a2 = value; }
   }
}
// Compilation produces a compiler warning like the following:
//    Naming2a.cs(16,18): warning CS3005: Identifier 'Size.Å' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(10,18): (Location of symbol related to previous warning)
//    Naming2a.cs(18,8): warning CS3005: Identifier 'Size.Å.get' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(12,8): (Location of symbol related to previous warning)
//    Naming2a.cs(19,8): warning CS3005: Identifier 'Size.Å.set' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(13,8): (Location of symbol related to previous warning)
```

```vb
<Assembly: CLSCompliant(True)>
Public Class Size
   Private a1 As Double
   Private a2 As Double

   Public Property Å As Double
       Get
          Return a1
       End Get
       Set
          a1 = value
       End Set
   End Property

   Public Property Å As Double
       Get
          Return a2
       End Get
       Set
          a2 = value
       End Set
   End Property
End Class
' Compilation produces a compiler warning like the following:
'    Naming1.vb(9) : error BC30269: 'Public Property Å As Double' has multiple definitions
'     with identical signatures.
'
'       Public Property Å As Double
'                       ~
```

<span data-ttu-id="384c1-457">Názvy členů v rámci určitého oboru (například obory názvů v rámci sestavení, typy v oboru názvů nebo členy v rámci typu) musí být jedinečné s výjimkou názvů, které jsou vyřešeny přetížením.</span><span class="sxs-lookup"><span data-stu-id="384c1-457">Member names within a particular scope (such as the namespaces within an assembly, the types within a namespace, or the members within a type) must be unique except for names that are resolved through overloading.</span></span> <span data-ttu-id="384c1-458">Tento požadavek je přísnější než u běžného systému typů, který umožňuje více členů v rámci oboru mít stejné názvy, pokud se jedná o různé druhy členů (například jeden je metoda a jeden je pole).</span><span class="sxs-lookup"><span data-stu-id="384c1-458">This requirement is more stringent than that of the common type system, which allows multiple members within a scope to have identical names as long as they are different kinds of members (for example, one is a method and one is a field).</span></span> <span data-ttu-id="384c1-459">Zejména pro členy typu:</span><span class="sxs-lookup"><span data-stu-id="384c1-459">In particular, for type members:</span></span>

* <span data-ttu-id="384c1-460">Pole a vnořené typy se rozlišují podle názvu samotného.</span><span class="sxs-lookup"><span data-stu-id="384c1-460">Fields and nested types are distinguished by name alone.</span></span>

* <span data-ttu-id="384c1-461">Metody, vlastnosti a události, které mají stejný název, se musí lišit více než pouze návratový typ.</span><span class="sxs-lookup"><span data-stu-id="384c1-461">Methods, properties, and events that have the same name must differ by more than just return type.</span></span>

<span data-ttu-id="384c1-462">Následující příklad ilustruje požadavek, že názvy členů musí být jedinečné v rámci jejich oboru.</span><span class="sxs-lookup"><span data-stu-id="384c1-462">The following example illustrates the requirement that member names must be unique within their scope.</span></span> <span data-ttu-id="384c1-463">Definuje třídu s `Converter` názvem, která `Conversion`zahrnuje čtyři členy s názvem .</span><span class="sxs-lookup"><span data-stu-id="384c1-463">It defines a class named `Converter` that includes four members named `Conversion`.</span></span> <span data-ttu-id="384c1-464">Tři jsou metody a jedna je vlastnost.</span><span class="sxs-lookup"><span data-stu-id="384c1-464">Three are methods, and one is a property.</span></span> <span data-ttu-id="384c1-465">Metoda, která `Int64` obsahuje parametr, je jednoznačně pojmenována, `Int32` ale dvě metody s parametrem nejsou, protože vrácená hodnota není považována za součást podpisu člena.</span><span class="sxs-lookup"><span data-stu-id="384c1-465">The method that includes an `Int64` parameter is uniquely named, but the two methods with an `Int32` parameter are not, because return value is not considered a part of a member's signature.</span></span> <span data-ttu-id="384c1-466">Vlastnost `Conversion` také porušuje tento požadavek, protože vlastnosti nemohou mít stejný název jako přetížené metody.</span><span class="sxs-lookup"><span data-stu-id="384c1-466">The `Conversion` property also violates this requirement, because properties cannot have the same name as overloaded methods.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Converter
{
   public double Conversion(int number)
   {
      return (double) number;
   }

   public float Conversion(int number)
   {
      return (float) number;
   }

   public double Conversion(long number)
   {
      return (double) number;
   }

   public bool Conversion
   {
      get { return true; }
   }
}
// Compilation produces a compiler error like the following:
//    Naming3.cs(13,17): error CS0111: Type 'Converter' already defines a member called
//            'Conversion' with the same parameter types
//    Naming3.cs(8,18): (Location of symbol related to previous error)
//    Naming3.cs(23,16): error CS0102: The type 'Converter' already contains a definition for
//            'Conversion'
//    Naming3.cs(8,18): (Location of symbol related to previous error)
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Converter
   Public Function Conversion(number As Integer) As Double
      Return CDbl(number)
   End Function

   Public Function Conversion(number As Integer) As Single
      Return CSng(number)
   End Function

   Public Function Conversion(number As Long) As Double
      Return CDbl(number)
   End Function

   Public ReadOnly Property Conversion As Boolean
      Get
         Return True
      End Get
   End Property
End Class
' Compilation produces a compiler error like the following:
'    Naming3.vb(8) : error BC30301: 'Public Function Conversion(number As Integer) As Double'
'                    and 'Public Function Conversion(number As Integer) As Single' cannot
'                    overload each other because they differ only by return types.
'
'       Public Function Conversion(number As Integer) As Double
'                       ~~~~~~~~~~
'    Naming3.vb(20) : error BC30260: 'Conversion' is already declared as 'Public Function
'                     Conversion(number As Integer) As Single' in this class.
'
'       Public ReadOnly Property Conversion As Boolean
'                                ~~~~~~~~~~
```

<span data-ttu-id="384c1-467">Jednotlivé jazyky obsahují jedinečná klíčová slova, takže jazyky, které cílí na běžný jazyk runtime, musí také poskytovat určitý mechanismus pro odkazování na identifikátory (například názvy typů), které se shodují s klíčovými slovy.</span><span class="sxs-lookup"><span data-stu-id="384c1-467">Individual languages include unique keywords, so languages that target the common language runtime must also provide some mechanism for referencing identifiers (such as type names) that coincide with keywords.</span></span> <span data-ttu-id="384c1-468">Například `case` je klíčové slovo v jazyce C# a jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="384c1-468">For example, `case` is a keyword in both C# and Visual Basic.</span></span> <span data-ttu-id="384c1-469">Následující příklad jazyka však je schopen rozptýlit třídu `case` pojmenovanou z klíčového `case` slova pomocí počáteční a uzavírací závorky.</span><span class="sxs-lookup"><span data-stu-id="384c1-469">However, the following Visual Basic example is able to disambiguate a class named `case` from the `case` keyword by using opening and closing braces.</span></span> <span data-ttu-id="384c1-470">V opačném případě by v příkladu vytvořit chybovou zprávu , "Klíčové slovo není platný jako identifikátor" a nepodaří zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="384c1-470">Otherwise, the example would produce the error message, "Keyword is not valid as an identifier," and fail to compile.</span></span>

```vb
Public Class [case]
   Private _id As Guid
   Private name As String

   Public Sub New(name As String)
      _id = Guid.NewGuid()
      Me.name = name
   End Sub

   Public ReadOnly Property ClientName As String
      Get
         Return name
      End Get
   End Property
End Class
```

<span data-ttu-id="384c1-471">Následující příklad jazyka C# je schopen `case` vytvořit instanci třídy pomocí symbolu @ k rozdvojení identifikátoru z klíčového slova jazyka.</span><span class="sxs-lookup"><span data-stu-id="384c1-471">The following C# example is able to instantiate the `case` class by using the @ symbol to disambiguate the identifier from the language keyword.</span></span> <span data-ttu-id="384c1-472">Bez něj by kompilátor Jazyka C# zobrazil dvě chybové zprávy"Type expected" a "Invalid expression term 'case'."</span><span class="sxs-lookup"><span data-stu-id="384c1-472">Without it, the C# compiler would display two error messages, "Type expected" and "Invalid expression term 'case'."</span></span>

```csharp
using System;

public class Example
{
   public static void Main()
   {
      @case c = new @case("John");
      Console.WriteLine(c.ClientName);
   }
}
```

### <a name="type-conversion"></a><span data-ttu-id="384c1-473">Převod typů</span><span class="sxs-lookup"><span data-stu-id="384c1-473">Type conversion</span></span>

<span data-ttu-id="384c1-474">Specifikace společného jazyka definuje dva operátory převodu:</span><span class="sxs-lookup"><span data-stu-id="384c1-474">The Common Language Specification defines two conversion operators:</span></span>

* <span data-ttu-id="384c1-475">`op_Implicit`, který se používá pro rozšíření převody, které nevedou ke ztrátě dat nebo přesnosti.</span><span class="sxs-lookup"><span data-stu-id="384c1-475">`op_Implicit`, which is used for widening conversions that do not result in loss of data or precision.</span></span> <span data-ttu-id="384c1-476">Například [desítkové](xref:System.Decimal) struktury obsahuje přetížené `op_Implicit` operátor převést hodnoty integrální typy a [Char](xref:System.Char) hodnoty. `Decimal`</span><span class="sxs-lookup"><span data-stu-id="384c1-476">For example, the [Decimal](xref:System.Decimal) structure includes an overloaded `op_Implicit` operator to convert values of integral types and [Char](xref:System.Char) values to `Decimal` values.</span></span>

* <span data-ttu-id="384c1-477">`op_Explicit`, který se používá pro zúžení převody, které mohou mít za následek ztrátu velikosti (hodnota je převedena na hodnotu, která má menší rozsah) nebo přesnost.</span><span class="sxs-lookup"><span data-stu-id="384c1-477">`op_Explicit`, which is used for narrowing conversions that can result in loss of magnitude (a value is converted to a value that has a smaller range) or precision.</span></span> <span data-ttu-id="384c1-478">`Decimal` Struktura například obsahuje přetížený `op_Explicit` operátor převést [Double](xref:System.Double) `Decimal` a Single `Decimal` hodnoty a `Double`převést hodnoty na integrální hodnoty , `Single`, a `Char`. [Single](xref:System.Single)</span><span class="sxs-lookup"><span data-stu-id="384c1-478">For example, the `Decimal` structure includes an overloaded `op_Explicit` operator to convert [Double](xref:System.Double) and [Single](xref:System.Single) values to `Decimal` and to convert `Decimal` values to integral values, `Double`, `Single`, and `Char`.</span></span>

<span data-ttu-id="384c1-479">Však ne všechny jazyky podporují přetížení operátoru nebo definice vlastní operátory.</span><span class="sxs-lookup"><span data-stu-id="384c1-479">However, not all languages support operator overloading or the definition of custom operators.</span></span> <span data-ttu-id="384c1-480">Pokud se rozhodnete implementovat tyto operátory převodu, měli byste také poskytnout alternativní způsob provedení převodu.</span><span class="sxs-lookup"><span data-stu-id="384c1-480">If you choose to implement these conversion operators, you should also provide an alternate way to perform the conversion.</span></span> <span data-ttu-id="384c1-481">Doporučujeme zadat `From`xxx `To`a xxx metody.</span><span class="sxs-lookup"><span data-stu-id="384c1-481">We recommend that you provide `From`Xxx and `To`Xxx methods.</span></span>

<span data-ttu-id="384c1-482">Následující příklad definuje implicitní a explicitní převody kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-482">The following example defines CLS-compliant implicit and explicit conversions.</span></span> <span data-ttu-id="384c1-483">Vytvoří třídu, `UDouble` která představuje podepsané číslo s dvojitou přesností s plovoucí desetinnou desetinnou hlavou.</span><span class="sxs-lookup"><span data-stu-id="384c1-483">It creates a `UDouble` class that represents an signed double-precision, floating-point number.</span></span> <span data-ttu-id="384c1-484">Poskytuje implicitní převody `UDouble` `Double` z a pro `UDouble` explicitní `Single` `Double` převody `Single` z `UDouble`, do `UDouble`, a na .</span><span class="sxs-lookup"><span data-stu-id="384c1-484">It provides for implicit conversions from `UDouble` to `Double` and for explicit conversions from `UDouble` to `Single`, `Double` to `UDouble`, and `Single` to `UDouble`.</span></span> <span data-ttu-id="384c1-485">Definuje také `ToDouble` metodu jako alternativu k implicitnímu operátoru převodu a metodě `ToSingle`, `FromDouble`a `FromSingle` metody jako alternativy k operátorům explicitního převodu.</span><span class="sxs-lookup"><span data-stu-id="384c1-485">It also defines a `ToDouble` method as an alternative to the implicit conversion operator and the `ToSingle`, `FromDouble`, and `FromSingle` methods as alternatives to the explicit conversion operators.</span></span>

```csharp
using System;

public struct UDouble
{
   private double number;

   public UDouble(double value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      number = value;
   }

   public UDouble(float value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      number = value;
   }

   public static readonly UDouble MinValue = (UDouble) 0.0;
   public static readonly UDouble MaxValue = (UDouble) Double.MaxValue;

   public static explicit operator Double(UDouble value)
   {
      return value.number;
   }

   public static implicit operator Single(UDouble value)
   {
      if (value.number > (double) Single.MaxValue)
         throw new InvalidCastException("A UDouble value is out of range of the Single type.");

      return (float) value.number;
   }

   public static explicit operator UDouble(double value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      return new UDouble(value);
   }

   public static implicit operator UDouble(float value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      return new UDouble(value);
   }

   public static Double ToDouble(UDouble value)
   {
      return (Double) value;
   }

   public static float ToSingle(UDouble value)
   {
      return (float) value;
   }

   public static UDouble FromDouble(double value)
   {
      return new UDouble(value);
   }

   public static UDouble FromSingle(float value)
   {
      return new UDouble(value);
   }
}
```

```vb
Public Structure UDouble
   Private number As Double

   Public Sub New(value As Double)
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      number = value
   End Sub

   Public Sub New(value As Single)
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      number = value
   End Sub

   Public Shared ReadOnly MinValue As UDouble = CType(0.0, UDouble)
   Public Shared ReadOnly MaxValue As UDouble = Double.MaxValue

   Public Shared Widening Operator CType(value As UDouble) As Double
      Return value.number
   End Operator

   Public Shared Narrowing Operator CType(value As UDouble) As Single
      If value.number > CDbl(Single.MaxValue) Then
         Throw New InvalidCastException("A UDouble value is out of range of the Single type.")
      End If
      Return CSng(value.number)
   End Operator

   Public Shared Narrowing Operator CType(value As Double) As UDouble
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      Return New UDouble(value)
   End Operator

   Public Shared Narrowing Operator CType(value As Single) As UDouble
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      Return New UDouble(value)
   End Operator

   Public Shared Function ToDouble(value As UDouble) As Double
      Return CType(value, Double)
   End Function

   Public Shared Function ToSingle(value As UDouble) As Single
      Return CType(value, Single)
   End Function

   Public Shared Function FromDouble(value As Double) As UDouble
      Return New UDouble(value)
   End Function

   Public Shared Function FromSingle(value As Single) As UDouble
      Return New UDouble(value)
   End Function
End Structure
```

### <a name="arrays"></a><span data-ttu-id="384c1-486">Pole</span><span class="sxs-lookup"><span data-stu-id="384c1-486">Arrays</span></span>

<span data-ttu-id="384c1-487">Pole kompatibilní se standardem CLS splňují následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="384c1-487">CLS-compliant arrays conform to the following rules:</span></span>

* <span data-ttu-id="384c1-488">Všechny dimenze pole musí mít dolní mez nula.</span><span class="sxs-lookup"><span data-stu-id="384c1-488">All dimensions of an array must have a lower bound of zero.</span></span> <span data-ttu-id="384c1-489">Následující příklad vytvoří pole, které není kompatibilní se standardem CLS, s dolní mez jednoho.</span><span class="sxs-lookup"><span data-stu-id="384c1-489">The following example creates a non-CLS-compliant array with a lower bound of one.</span></span> <span data-ttu-id="384c1-490">Všimněte si, že i přes přítomnost [clscompliantattribute](xref:System.CLSCompliantAttribute) atribut kompilátor nezjistí, že pole vrácené `Numbers.GetTenPrimes` metodou není kompatibilní se seznamem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-490">Note that, despite the presence of the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute, the compiler does not detect that the array returned by the `Numbers.GetTenPrimes` method is not CLS-compliant.</span></span>

  ```csharp
  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static Array GetTenPrimes()
    {
        Array arr = Array.CreateInstance(typeof(Int32), new int[] {10}, new int[] {1});
        arr.SetValue(1, 1);
        arr.SetValue(2, 2);
        arr.SetValue(3, 3);
        arr.SetValue(5, 4);
        arr.SetValue(7, 5);
        arr.SetValue(11, 6);
        arr.SetValue(13, 7);
        arr.SetValue(17, 8);
        arr.SetValue(19, 9);
        arr.SetValue(23, 10);

        return arr;
    }
  }
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Class Numbers
     Public Shared Function GetTenPrimes() As Array
        Dim arr As Array = Array.CreateInstance(GetType(Int32), {10}, {1})
        arr.SetValue(1, 1)
        arr.SetValue(2, 2)
        arr.SetValue(3, 3)
        arr.SetValue(5, 4)
        arr.SetValue(7, 5)
        arr.SetValue(11, 6)
        arr.SetValue(13, 7)
        arr.SetValue(17, 8)
        arr.SetValue(19, 9)
        arr.SetValue(23, 10)
        Return arr
     End Function
  End Class
  ```

* <span data-ttu-id="384c1-491">Všechny prvky pole se musí skládat z typů kompatibilních se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-491">All array elements must consist of CLS-compliant types.</span></span> <span data-ttu-id="384c1-492">Následující příklad definuje dvě metody, které vracejí pole, která nejsou kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-492">The following example defines two methods that return non-CLS-compliant arrays.</span></span> <span data-ttu-id="384c1-493">První vrátí pole [hodnot UInt32.](xref:System.UInt32)</span><span class="sxs-lookup"><span data-stu-id="384c1-493">The first returns an array of [UInt32](xref:System.UInt32) values.</span></span> <span data-ttu-id="384c1-494">Druhý vrátí [object](xref:System.Object) pole, které obsahuje `UInt32` [Int32](xref:System.Int32) a hodnoty.</span><span class="sxs-lookup"><span data-stu-id="384c1-494">The second returns an [Object](xref:System.Object) array that includes [Int32](xref:System.Int32) and `UInt32` values.</span></span> <span data-ttu-id="384c1-495">Přestože kompilátor identifikuje první pole jako nekompatibilní z důvodu jeho `UInt32` typu, nedokáže rozpoznat, že druhé pole obsahuje prvky, které nejsou kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-495">Although the compiler identifies the first array as non-compliant because of its `UInt32` type, it fails to recognize that the second array includes non-CLS-compliant elements.</span></span>

  ```csharp
  using System;

  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static UInt32[] GetTenPrimes()
    {
        uint[] arr = { 1u, 2u, 3u, 5u, 7u, 11u, 13u, 17u, 19u };
        return arr;
    }

    public static Object[] GetFivePrimes()
    {
        Object[] arr = { 1, 2, 3, 5u, 7u };
        return arr;
    }
  }
  // Compilation produces a compiler warning like the following:
  //    Array2.cs(8,27): warning CS3002: Return type of 'Numbers.GetTenPrimes()' is not
  //            CLS-compliant
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Class Numbers
     Public Shared Function GetTenPrimes() As UInt32()
        Return { 1ui, 2ui, 3ui, 5ui, 7ui, 11ui, 13ui, 17ui, 19ui }
     End Function
     Public Shared Function GetFivePrimes() As Object()
        Dim arr() As Object = { 1, 2, 3, 5ui, 7ui }
        Return arr
     End Function
  End Class
  ' Compilation produces a compiler warning like the following:
  '    warning BC40027: Return type of function 'GetTenPrimes' is not CLS-compliant.
  ```

* <span data-ttu-id="384c1-496">Řešení přetížení pro metody, které mají parametry pole je založena na skutečnosti, že jsou pole a na jejich typu prvku.</span><span class="sxs-lookup"><span data-stu-id="384c1-496">Overload resolution for methods that have array parameters is based on the fact that they are arrays and on their element type.</span></span> <span data-ttu-id="384c1-497">Z tohoto důvodu je následující definice `GetSquares` přetížené metody kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-497">For this reason, the following definition of an overloaded `GetSquares` method is CLS-compliant.</span></span>

  ```csharp
  using System;
  using System.Numerics;

  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static byte[] GetSquares(byte[] numbers)
    {
        byte[] numbersOut = new byte[numbers.Length];
        for (int ctr = 0; ctr < numbers.Length; ctr++) {
            int square = ((int) numbers[ctr]) * ((int) numbers[ctr]);
            if (square <= Byte.MaxValue)
                numbersOut[ctr] = (byte) square;
            // If there's an overflow, assign MaxValue to the corresponding
            // element.
            else
                numbersOut[ctr] = Byte.MaxValue;

        }
        return numbersOut;
    }

    public static BigInteger[] GetSquares(BigInteger[] numbers)
  {
        BigInteger[] numbersOut = new BigInteger[numbers.Length];
        for (int ctr = 0; ctr < numbers.Length; ctr++)
            numbersOut[ctr] = numbers[ctr] * numbers[ctr];

       return numbersOut;
    }
  }
  ```

  ```vb
  Imports System.Numerics

  <Assembly: CLSCompliant(True)>

  Public Module Numbers
     Public Function GetSquares(numbers As Byte()) As Byte()
        Dim numbersOut(numbers.Length - 1) As Byte
        For ctr As Integer = 0 To numbers.Length - 1
           Dim square As Integer = (CInt(numbers(ctr)) * CInt(numbers(ctr)))
           If square <= Byte.MaxValue Then
              numbersOut(ctr) = CByte(square)
           ' If there's an overflow, assign MaxValue to the corresponding
           ' element.
           Else
              numbersOut(ctr) = Byte.MaxValue
           End If
        Next
        Return numbersOut
     End Function

     Public Function GetSquares(numbers As BigInteger()) As BigInteger()
         Dim numbersOut(numbers.Length - 1) As BigInteger
         For ctr As Integer = 0 To numbers.Length - 1
            numbersOut(ctr) = numbers(ctr) * numbers(ctr)
         Next
         Return numbersOut
     End Function
  End Module
  ```

### <a name="interfaces"></a><span data-ttu-id="384c1-498">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="384c1-498">Interfaces</span></span>

<span data-ttu-id="384c1-499">Rozhraní kompatibilní se standardem CLS mohou definovat vlastnosti, události a virtuální metody (metody bez implementace).</span><span class="sxs-lookup"><span data-stu-id="384c1-499">CLS-compliant interfaces can define properties, events, and virtual methods (methods with no implementation).</span></span> <span data-ttu-id="384c1-500">Rozhraní kompatibilní se standardem CLS nemůže obsahovat některou z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="384c1-500">A CLS-compliant interface cannot have any of the following:</span></span>

* <span data-ttu-id="384c1-501">Statické metody nebo statická pole.</span><span class="sxs-lookup"><span data-stu-id="384c1-501">Static methods or static fields.</span></span> <span data-ttu-id="384c1-502">Kompilátor Jazyka C# generuje chyby kompilátoru, pokud definujete statický člen v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="384c1-502">The C# compiler generates compiler errors if you define a static member in an interface.</span></span>

* <span data-ttu-id="384c1-503">Pole.</span><span class="sxs-lookup"><span data-stu-id="384c1-503">Fields.</span></span> <span data-ttu-id="384c1-504">C# kompilátor generuje chyby kompilátoru, pokud definujete pole v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="384c1-504">The C# a compiler generates compiler errors if you define a field in an interface.</span></span>

* <span data-ttu-id="384c1-505">Metody, které nejsou kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-505">Methods that are not CLS-compliant.</span></span> <span data-ttu-id="384c1-506">Například následující definice rozhraní obsahuje `INumber.GetUnsigned`metodu , která je označena jako nekompatibilní se souborem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-506">For example, the following interface definition includes a method, `INumber.GetUnsigned`, that is marked as non-CLS-compliant.</span></span> <span data-ttu-id="384c1-507">Tento příklad generuje upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="384c1-507">This example generates a compiler warning.</span></span>

  ```csharp
  using System;

  [assembly:CLSCompliant(true)]

  public interface INumber
  {
      int Length();
      [CLSCompliant(false)] ulong GetUnsigned();
  }
  // Attempting to compile the example displays output like the following:
  //    Interface2.cs(8,32): warning CS3010: 'INumber.GetUnsigned()': CLS-compliant interfaces
  //            must have only CLS-compliant members
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Interface INumber
    Function Length As Integer
      <CLSCompliant(False)> Function GetUnsigned As ULong
    End Interface
    ' Attempting to compile the example displays output like the following:
    '    Interface2.vb(9) : warning BC40033: Non CLS-compliant 'function' is not allowed in a
    '    CLS-compliant interface.
    '
    '       <CLSCompliant(False)> Function GetUnsigned As ULong
    '                                      ~~~~~~~~~~~
  ```

  <span data-ttu-id="384c1-508">Z důvodu tohoto pravidla nejsou typy kompatibilní se standardem CLS nutné implementovat členy, které nejsou kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-508">Because of this rule, CLS-compliant types are not required to implement non-CLS-compliant members.</span></span> <span data-ttu-id="384c1-509">Pokud rozhraní kompatibilní se standardem CLS zveřejňuje třídu, která implementuje rozhraní kompatibilní se standardem CLS, měla by také poskytovat konkrétní implementace všech členů, které nejsou kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-509">If a CLS-compliant framework does expose a class that implements a non-CLS compliant interface, it should also provide concrete implementations of all non-CLS-compliant members.</span></span>

<span data-ttu-id="384c1-510">Kompilátory jazyka kompatibilní se seznamem CLS musí také umožnit třídě poskytovat samostatné implementace členů, které mají stejný název a podpis ve více rozhraních.</span><span class="sxs-lookup"><span data-stu-id="384c1-510">CLS-compliant language compilers must also allow a class to provide separate implementations of members that have the same name and signature in multiple interfaces.</span></span> <span data-ttu-id="384c1-511">C# podporuje explicitní implementace rozhraní poskytovat různé implementace identicky pojmenované metody.</span><span class="sxs-lookup"><span data-stu-id="384c1-511">C# supports explicit interface implementations to provide different implementations of identically named methods.</span></span> <span data-ttu-id="384c1-512">Následující příklad ilustruje tento scénář definováním `Temperature` třídy, `ICelsius` `IFahrenheit` která implementuje rozhraní a jako explicitní implementace rozhraní.</span><span class="sxs-lookup"><span data-stu-id="384c1-512">The following example illustrates this scenario by defining a `Temperature` class that implements the `ICelsius` and `IFahrenheit` interfaces as explicit interface implementations.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public interface IFahrenheit
{
   decimal GetTemperature();
}

public interface ICelsius
{
   decimal GetTemperature();
}

public class Temperature : ICelsius, IFahrenheit
{
   private decimal _value;

   public Temperature(decimal value)
   {
      // We assume that this is the Celsius value.
      _value = value;
   }

   decimal IFahrenheit.GetTemperature()
   {
      return _value * 9 / 5 + 32;
   }

   decimal ICelsius.GetTemperature()
   {
      return _value;
   }
}
public class Example
{
   public static void Main()
   {
      Temperature temp = new Temperature(100.0m);
      ICelsius cTemp = temp;
      IFahrenheit fTemp = temp;
      Console.WriteLine("Temperature in Celsius: {0} degrees",
                        cTemp.GetTemperature());
      Console.WriteLine("Temperature in Fahrenheit: {0} degrees",
                        fTemp.GetTemperature());
   }
}
// The example displays the following output:
//       Temperature in Celsius: 100.0 degrees
//       Temperature in Fahrenheit: 212.0 degrees
```

```vb
Assembly: CLSCompliant(True)>

Public Interface IFahrenheit
   Function GetTemperature() As Decimal
End Interface

Public Interface ICelsius
   Function GetTemperature() As Decimal
End Interface

Public Class Temperature : Implements ICelsius, IFahrenheit
   Private _value As Decimal

   Public Sub New(value As Decimal)
      ' We assume that this is the Celsius value.
      _value = value
   End Sub

   Public Function GetFahrenheit() As Decimal _
          Implements IFahrenheit.GetTemperature
      Return _value * 9 / 5 + 32
   End Function

   Public Function GetCelsius() As Decimal _
          Implements ICelsius.GetTemperature
      Return _value
   End Function
End Class

Module Example
   Public Sub Main()
      Dim temp As New Temperature(100.0d)
      Console.WriteLine("Temperature in Celsius: {0} degrees",
                        temp.GetCelsius())
      Console.WriteLine("Temperature in Fahrenheit: {0} degrees",
                        temp.GetFahrenheit())
   End Sub
End Module
' The example displays the following output:
'       Temperature in Celsius: 100.0 degrees
'       Temperature in Fahrenheit: 212.0 degrees
```

### <a name="enumerations"></a><span data-ttu-id="384c1-513">Výčty</span><span class="sxs-lookup"><span data-stu-id="384c1-513">Enumerations</span></span>

<span data-ttu-id="384c1-514">Výčty kompatibilní se standardem CLS se musí řídit těmito pravidly:</span><span class="sxs-lookup"><span data-stu-id="384c1-514">CLS-compliant enumerations must follow these rules:</span></span>

* <span data-ttu-id="384c1-515">Základní typ výčtu musí být vnitřní cls kompatibilní celé číslo ([Byte](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32)nebo [Int64](xref:System.Int64)).</span><span class="sxs-lookup"><span data-stu-id="384c1-515">The underlying type of the enumeration must be an intrinsic CLS-compliant integer ([Byte](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32), or [Int64](xref:System.Int64)).</span></span> <span data-ttu-id="384c1-516">Například následující kód se pokusí definovat výčtu, jehož základní typ je [UInt32](xref:System.UInt32) a generuje upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="384c1-516">For example, the following code tries to define an enumeration whose underlying type is [UInt32](xref:System.UInt32) and generates a compiler warning.</span></span>

    ```csharp
    using System;

    [assembly: CLSCompliant(true)]

    public enum Size : uint {
        Unspecified = 0,
        XSmall = 1,
        Small = 2,
        Medium = 3,
        Large = 4,
        XLarge = 5
    };

    public class Clothing
    {
        public string Name;
        public string Type;
        public string Size;
    }
    // The attempt to compile the example displays a compiler warning like the following:
    //    Enum3.cs(6,13): warning CS3009: 'Size': base type 'uint' is not CLS-compliant
    ```

    ```vb
    <Assembly: CLSCompliant(True)>

    Public Enum Size As UInt32
       Unspecified = 0
       XSmall = 1
       Small = 2
       Medium = 3
       Large = 4
       XLarge = 5
    End Enum

    Public Class Clothing
       Public Name As String
       Public Type As String
       Public Size As Size
    End Class
    ' The attempt to compile the example displays a compiler warning like the following:
    '    Enum3.vb(6) : warning BC40032: Underlying type 'UInt32' of Enum is not CLS-compliant.
    '
    '    Public Enum Size As UInt32
    '                ~~~~
    ```

* <span data-ttu-id="384c1-517">Typ výčtu musí mít jedno `Value__` pole instance s `FieldAttributes.RTSpecialName` názvem atributem.</span><span class="sxs-lookup"><span data-stu-id="384c1-517">An enumeration type must have a single instance field named `Value__` that is marked with the `FieldAttributes.RTSpecialName` attribute.</span></span> <span data-ttu-id="384c1-518">To umožňuje implicitně odkazovat na hodnotu pole.</span><span class="sxs-lookup"><span data-stu-id="384c1-518">This enables you to reference the field value implicitly.</span></span>

* <span data-ttu-id="384c1-519">Výčet zahrnuje literálová statická pole, jejichž typy odpovídají typu samotného výčtu.</span><span class="sxs-lookup"><span data-stu-id="384c1-519">An enumeration includes literal static fields whose types match the type of the enumeration itself.</span></span> <span data-ttu-id="384c1-520">Například pokud definujete `State` výčet s `State.On` hodnotami `State.On` `State.Off` a `State.Off`, a jsou oba `State`literál statická pole, jejichž typ je .</span><span class="sxs-lookup"><span data-stu-id="384c1-520">For example, if you define a `State` enumeration with values of `State.On` and `State.Off`, `State.On` and `State.Off` are both literal static fields whose type is `State`.</span></span>

* <span data-ttu-id="384c1-521">Existují dva druhy výčtů:</span><span class="sxs-lookup"><span data-stu-id="384c1-521">There are two kinds of enumerations:</span></span>

  * <span data-ttu-id="384c1-522">Výčet, který představuje sadu vzájemně se vylučujících, pojmenovaných celé hodnoty.</span><span class="sxs-lookup"><span data-stu-id="384c1-522">An enumeration that represents a set of mutually exclusive, named integer values.</span></span> <span data-ttu-id="384c1-523">Tento typ výčtu je označen absencí vlastního atributu [System.FlagsAttribute.](xref:System.FlagsAttribute)</span><span class="sxs-lookup"><span data-stu-id="384c1-523">This type of enumeration is indicated by the absence of the [System.FlagsAttribute](xref:System.FlagsAttribute) custom attribute.</span></span>

  * <span data-ttu-id="384c1-524">Výčet, který představuje sadu bitových příznaků, které lze kombinovat generovat nepojmenovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="384c1-524">An enumeration that represents a set of bit flags that can combine to generate an unnamed value.</span></span> <span data-ttu-id="384c1-525">Tento typ výčtu je označen přítomností vlastního atributu [System.FlagsAttribute.](xref:System.FlagsAttribute)</span><span class="sxs-lookup"><span data-stu-id="384c1-525">This type of enumeration is indicated by the presence of the [System.FlagsAttribute](xref:System.FlagsAttribute) custom attribute.</span></span>

<span data-ttu-id="384c1-526">Další informace naleznete v dokumentaci ke struktuře [výčtu.](xref:System.Enum)</span><span class="sxs-lookup"><span data-stu-id="384c1-526">For more information, see the documentation for the [Enum](xref:System.Enum) structure.</span></span>

* <span data-ttu-id="384c1-527">Hodnota výčtu není omezena na rozsah jeho zadané hodnoty.</span><span class="sxs-lookup"><span data-stu-id="384c1-527">The value of an enumeration is not limited to the range of its specified values.</span></span> <span data-ttu-id="384c1-528">Jinými slovy rozsah hodnot ve výčtu je rozsah jeho základní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="384c1-528">In other words, the range of values in an enumeration is the range of its underlying value.</span></span> <span data-ttu-id="384c1-529">Metodu `Enum.IsDefined` můžete použít k určení, zda je zadaná hodnota členem výčtu.</span><span class="sxs-lookup"><span data-stu-id="384c1-529">You can use the `Enum.IsDefined` method to determine whether a specified value is a member of an enumeration.</span></span>

### <a name="type-members-in-general"></a><span data-ttu-id="384c1-530">Typ členů obecně</span><span class="sxs-lookup"><span data-stu-id="384c1-530">Type members in general</span></span>

<span data-ttu-id="384c1-531">Specifikace společného jazyka vyžaduje, aby všechna pole a metody byly přístupné jako členové určité třídy.</span><span class="sxs-lookup"><span data-stu-id="384c1-531">The Common Language Specification requires all fields and methods to be accessed as members of a particular class.</span></span> <span data-ttu-id="384c1-532">Globální statická pole a metody (tj. statická pole nebo metody, které jsou definovány na rozdíl od typu) proto nejsou kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-532">Therefore, global static fields and methods (that is, static fields or methods that are defined apart from a type) are not CLS-compliant.</span></span> <span data-ttu-id="384c1-533">Pokud se pokusíte zahrnout globální pole nebo metodu do zdrojového kódu, kompilátor Jazyka C# vygeneruje chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="384c1-533">If you try to include a global field or method in your source code, the C# compiler generates a compiler error.</span></span>

<span data-ttu-id="384c1-534">Specifikace společného jazyka podporuje pouze standardní konvence spravovaných volání.</span><span class="sxs-lookup"><span data-stu-id="384c1-534">The Common Language Specification supports only the standard managed calling convention.</span></span> <span data-ttu-id="384c1-535">Nepodporuje nespravované konvence volání a metody s proměnnými `varargs` argumenty označenými klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="384c1-535">It doesn't support unmanaged calling conventions and methods with variable argument lists marked with the `varargs` keyword.</span></span> <span data-ttu-id="384c1-536">Pro seznamy proměnných argumentů, které jsou kompatibilní se standardní konvencí spravovaných `params` volání, použijte atribut `ParamArray` [ParamArrayAttribute](xref:System.ParamArrayAttribute) nebo implementaci jednotlivého jazyka, například klíčové slovo v jazyce C# a klíčové slovo v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="384c1-536">For variable argument lists that are compatible with the standard managed calling convention, use the [ParamArrayAttribute](xref:System.ParamArrayAttribute) attribute or the individual language's implementation, such as the `params` keyword in C# and the `ParamArray` keyword in Visual Basic.</span></span>

### <a name="member-accessibility"></a><span data-ttu-id="384c1-537">Přístupnost členů</span><span class="sxs-lookup"><span data-stu-id="384c1-537">Member accessibility</span></span>

<span data-ttu-id="384c1-538">Přepsání zděděného člena nemůže změnit přístupnost tohoto člena.</span><span class="sxs-lookup"><span data-stu-id="384c1-538">Overriding an inherited member cannot change the accessibility of that member.</span></span> <span data-ttu-id="384c1-539">Například veřejná metoda v základní třídě nemůže být přepsána soukromou metodou v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="384c1-539">For example, a public method in a base class cannot be overridden by a private method in a derived class.</span></span> <span data-ttu-id="384c1-540">Existuje jedna výjimka: a `protected internal` (v `Protected Friend` jazyce C#) nebo (v jazyce Visual Basic) člen v jednom sestavení, který je přepsán typem v jiném sestavení.</span><span class="sxs-lookup"><span data-stu-id="384c1-540">There is one exception: a `protected internal` (in C#) or `Protected Friend` (in Visual Basic) member in one assembly that is overridden by a type in a different assembly.</span></span>  <span data-ttu-id="384c1-541">V takovém případě je `Protected`přístupnost přepsání .</span><span class="sxs-lookup"><span data-stu-id="384c1-541">In that case, the accessibility of the override is `Protected`.</span></span>

<span data-ttu-id="384c1-542">Následující příklad ilustruje chybu, která je generována při [clsCompliantAttribute](xref:System.CLSCompliantAttribute) atribut je nastaven `true`na , a `Person`, což je třída odvozená z `Animal`, pokusí se změnit usnadnění `Species` přístupu vlastnosti z veřejné na soukromé.</span><span class="sxs-lookup"><span data-stu-id="384c1-542">The following example illustrates the error that is generated when the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute is set to `true`, and `Person`, which is a class derived from `Animal`, tries to change the accessibility of the `Species` property from public to private.</span></span> <span data-ttu-id="384c1-543">Příklad se úspěšně zkompiluje, pokud je jeho usnadnění přístupu změněno na veřejné.</span><span class="sxs-lookup"><span data-stu-id="384c1-543">The example compiles successfully if its accessibility is changed to public.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Animal
{
   private string _species;

   public Animal(string species)
   {
      _species = species;
   }

   public virtual string Species
   {
      get { return _species; }
   }

   public override string ToString()
   {
      return _species;
   }
}

public class Human : Animal
{
   private string _name;

   public Human(string name) : base("Homo Sapiens")
   {
      _name = name;
   }

   public string Name
   {
      get { return _name; }
   }

   private override string Species
   {
      get { return base.Species; }
   }

   public override string ToString()
   {
      return _name;
   }
}

public class Example
{
   public static void Main()
   {
      Human p = new Human("John");
      Console.WriteLine(p.Species);
      Console.WriteLine(p.ToString());
   }
}
// The example displays the following output:
//    error CS0621: 'Human.Species': virtual or abstract members cannot be private
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Animal
   Private _species As String

   Public Sub New(species As String)
      _species = species
   End Sub

   Public Overridable ReadOnly Property Species As String
      Get
         Return _species
      End Get
   End Property

   Public Overrides Function ToString() As String
      Return _species
   End Function
End Class

Public Class Human : Inherits Animal
   Private _name As String

   Public Sub New(name As String)
      MyBase.New("Homo Sapiens")
      _name = name
   End Sub

   Public ReadOnly Property Name As String
      Get
         Return _name
      End Get
   End Property

   Private Overrides ReadOnly Property Species As String
      Get
         Return MyBase.Species
      End Get
   End Property

   Public Overrides Function ToString() As String
      Return _name
   End Function
End Class

Public Module Example
   Public Sub Main()
      Dim p As New Human("John")
      Console.WriteLine(p.Species)
      Console.WriteLine(p.ToString())
   End Sub
End Module
' The example displays the following output:
'     'Private Overrides ReadOnly Property Species As String' cannot override
'     'Public Overridable ReadOnly Property Species As String' because
'      they have different access levels.
'
'         Private Overrides ReadOnly Property Species As String
```

<span data-ttu-id="384c1-544">Typy v podpisu člena musí být přístupné vždy, když je tento člen přístupný.</span><span class="sxs-lookup"><span data-stu-id="384c1-544">Types in the signature of a member must be accessible whenever that member is accessible.</span></span> <span data-ttu-id="384c1-545">Například to znamená, že veřejný člen nemůže obsahovat parametr, jehož typ je soukromý, chráněný nebo interní.</span><span class="sxs-lookup"><span data-stu-id="384c1-545">For example, this means that a public member cannot include a parameter whose type is private, protected, or internal.</span></span> <span data-ttu-id="384c1-546">Následující příklad ilustruje chybu kompilátoru, `StringWrapper` která je výsledkem, když konstruktor třídy zpřístupní hodnotu vnitřního `StringOperationType` výčtu, která určuje, jak by měla být zabalena hodnota řetězce.</span><span class="sxs-lookup"><span data-stu-id="384c1-546">The following example illustrates the compiler error that results when a `StringWrapper` class constructor exposes an internal `StringOperationType` enumeration value that determines how a string value should be wrapped.</span></span>

```csharp
using System;
using System.Text;

public class StringWrapper
{
   string internalString;
   StringBuilder internalSB = null;
   bool useSB = false;

   public StringWrapper(StringOperationType type)
   {
      if (type == StringOperationType.Normal) {
         useSB = false;
      }
      else {
         useSB = true;
         internalSB = new StringBuilder();
      }
   }

   // The remaining source code...
}

internal enum StringOperationType { Normal, Dynamic }
// The attempt to compile the example displays the following output:
//    error CS0051: Inconsistent accessibility: parameter type
//            'StringOperationType' is less accessible than method
//            'StringWrapper.StringWrapper(StringOperationType)'
```

```vb
Imports System.Text

<Assembly:CLSCompliant(True)>

Public Class StringWrapper

   Dim internalString As String
   Dim internalSB As StringBuilder = Nothing
   Dim useSB As Boolean = False

   Public Sub New(type As StringOperationType)
      If type = StringOperationType.Normal Then
         useSB = False
      Else
         internalSB = New StringBuilder()
         useSB = True
      End If
   End Sub

   ' The remaining source code...
End Class

Friend Enum StringOperationType As Integer
   Normal = 0
   Dynamic = 1
End Enum
' The attempt to compile the example displays the following output:
'    error BC30909: 'type' cannot expose type 'StringOperationType'
'     outside the project through class 'StringWrapper'.
'
'       Public Sub New(type As StringOperationType)
'                              ~~~~~~~~~~~~~~~~~~~
```

### <a name="generic-types-and-members"></a><span data-ttu-id="384c1-547">Obecné typy a členy</span><span class="sxs-lookup"><span data-stu-id="384c1-547">Generic types and members</span></span>

<span data-ttu-id="384c1-548">Vnořené typy mají vždy alespoň tolik obecných parametrů jako jejich ohraničující typ.</span><span class="sxs-lookup"><span data-stu-id="384c1-548">Nested types always have at least as many generic parameters as their enclosing type.</span></span> <span data-ttu-id="384c1-549">Ty odpovídají podle pozice obecných parametrů v ohraničujícím typu.</span><span class="sxs-lookup"><span data-stu-id="384c1-549">These correspond by position to the generic parameters in the enclosing type.</span></span> <span data-ttu-id="384c1-550">Obecný typ může také obsahovat nové obecné parametry.</span><span class="sxs-lookup"><span data-stu-id="384c1-550">The generic type can also include new generic parameters.</span></span>

<span data-ttu-id="384c1-551">Vztah mezi parametry obecného typu obsahujícího typu a jeho vnořených typů může být skryt syntaxí jednotlivých jazyků.</span><span class="sxs-lookup"><span data-stu-id="384c1-551">The relationship between the generic type parameters of a containing type and its nested types may be hidden by the syntax of individual languages.</span></span> <span data-ttu-id="384c1-552">V následujícím příkladu obecný `Outer<T>` typ obsahuje dvě `Inner1A` `Inner1B<U>`vnořené třídy a .</span><span class="sxs-lookup"><span data-stu-id="384c1-552">In the following example, a generic type `Outer<T>` contains two nested classes, `Inner1A` and `Inner1B<U>`.</span></span> <span data-ttu-id="384c1-553">Volání `ToString` metody, ze které každá třída `Object.ToString`dědí , ukazují, že každá vnořená třída obsahuje parametry typu její obsahující třídy.</span><span class="sxs-lookup"><span data-stu-id="384c1-553">The calls to the `ToString` method, which each class inherits from `Object.ToString`, show that each nested class includes the type parameters of its containing class.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Outer<T>
{
   T value;

   public Outer(T value)
   {
      this.value = value;
   }

   public class Inner1A : Outer<T>
   {
      public Inner1A(T value) : base(value)
      {  }
   }

   public class Inner1B<U> : Outer<T>
   {
      U value2;

      public Inner1B(T value1, U value2) : base(value1)
      {
         this.value2 = value2;
      }
   }
}

public class Example
{
   public static void Main()
   {
      var inst1 = new Outer<String>("This");
      Console.WriteLine(inst1);

      var inst2 = new Outer<String>.Inner1A("Another");
      Console.WriteLine(inst2);

      var inst3 = new Outer<String>.Inner1B<int>("That", 2);
      Console.WriteLine(inst3);
   }
}
// The example displays the following output:
//       Outer`1[System.String]
//       Outer`1+Inner1A[System.String]
//       Outer`1+Inner1B`1[System.String,System.Int32]
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Outer(Of T)
   Dim value As T

   Public Sub New(value As T)
      Me.value = value
   End Sub

   Public Class Inner1A : Inherits Outer(Of T)
      Public Sub New(value As T)
         MyBase.New(value)
      End Sub
   End Class

   Public Class Inner1B(Of U) : Inherits Outer(Of T)
      Dim value2 As U

      Public Sub New(value1 As T, value2 As U)
         MyBase.New(value1)
         Me.value2 = value2
      End Sub
   End Class
End Class

Public Module Example
   Public Sub Main()
      Dim inst1 As New Outer(Of String)("This")
      Console.WriteLine(inst1)

      Dim inst2 As New Outer(Of String).Inner1A("Another")
      Console.WriteLine(inst2)

      Dim inst3 As New Outer(Of String).Inner1B(Of Integer)("That", 2)
      Console.WriteLine(inst3)
   End Sub
End Module
' The example displays the following output:
'       Outer`1[System.String]
'       Outer`1+Inner1A[System.String]
'       Outer`1+Inner1B`1[System.String,System.Int32]
```

<span data-ttu-id="384c1-554">Obecné názvy typů jsou kódovány v *názvu*formuláře*n*, *\`* kde *název* je název typu, je literál znaku a *n* je počet parametrů deklarovaných na typu nebo, pro vnořené obecné typy, počet nově zavedených parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="384c1-554">Generic type names are encoded in the form *name*'*n*, where *name* is the type name, *\`* is a character literal, and *n* is the number of parameters declared on the type, or, for nested generic types, the number of newly introduced type parameters.</span></span> <span data-ttu-id="384c1-555">Toto kódování obecných názvů typů je primárně zajímavé pro vývojáře, kteří používají reflexe pro přístup k obecným typům stížností CLS v knihovně.</span><span class="sxs-lookup"><span data-stu-id="384c1-555">This encoding of generic type names is primarily of interest to developers who use reflection to access CLS-complaint generic types in a library.</span></span>

<span data-ttu-id="384c1-556">Pokud jsou použita omezení pro obecný typ, všechny typy používané jako omezení musí být také kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-556">If constraints are applied to a generic type, any types used as constraints must also be CLS-compliant.</span></span> <span data-ttu-id="384c1-557">Následující příklad definuje třídu `BaseClass` s názvem, která není kompatibilní `BaseCollection` se standardem CLS, a obecnou třídu s názvem, jejíž parametr typu musí být odvozen z `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="384c1-557">The following example defines a class named `BaseClass` that is not CLS-compliant and a generic class named `BaseCollection` whose type parameter must derive from `BaseClass`.</span></span> <span data-ttu-id="384c1-558">Ale `BaseClass` protože není kompatibilní se standardem CLS, kompilátor vydává upozornění.</span><span class="sxs-lookup"><span data-stu-id="384c1-558">But because `BaseClass` is not CLS-compliant, the compiler emits a warning.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

[CLSCompliant(false)] public class BaseClass
{}

public class BaseCollection<T> where T : BaseClass
{}
// Attempting to compile the example displays the following output:
//    warning CS3024: Constraint type 'BaseClass' is not CLS-compliant
```

```vb
Assembly: CLSCompliant(True)>

<CLSCompliant(False)> Public Class BaseClass
End Class

Public Class BaseCollection(Of T As BaseClass)
End Class
' Attempting to compile the example displays the following output:
'    warning BC40040: Generic parameter constraint type 'BaseClass' is not
'    CLS-compliant.
'
'    Public Class BaseCollection(Of T As BaseClass)
'                                        ~~~~~~~~~
```

<span data-ttu-id="384c1-559">Pokud obecný typ je odvozen od obecného základního typu, musí znovu deklarovat všechna omezení tak, aby může zaručit, že omezení na základní typ jsou také splněny.</span><span class="sxs-lookup"><span data-stu-id="384c1-559">If a generic type is derived from a generic base type, it must redeclare any constraints so that it can guarantee that constraints on the base type are also satisfied.</span></span> <span data-ttu-id="384c1-560">Následující příklad definuje, `Number<T>` který může představovat libovolný číselný typ.</span><span class="sxs-lookup"><span data-stu-id="384c1-560">The following example defines a `Number<T>` that can represent any numeric type.</span></span> <span data-ttu-id="384c1-561">Také definuje třídu, `FloatingPoint<T>` která představuje hodnotu s plovoucí desetinnou tácek.</span><span class="sxs-lookup"><span data-stu-id="384c1-561">It also defines a `FloatingPoint<T>` class that represents a floating point value.</span></span> <span data-ttu-id="384c1-562">Zdrojový kód se však nepodaří zkompilovat, `Number<T>` protože nepoužije omezení (že `FloatingPoint<T>`T musí být typ hodnoty) na .</span><span class="sxs-lookup"><span data-stu-id="384c1-562">However, the source code fails to compile, because it does not apply the constraint on `Number<T>` (that T must be a value type) to `FloatingPoint<T>`.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Number<T> where T : struct
{
   // use Double as the underlying type, since its range is a superset of
   // the ranges of all numeric types except BigInteger.
   protected double number;

   public Number(T value)
   {
      try {
         this.number = Convert.ToDouble(value);
      }
      catch (OverflowException e) {
         throw new ArgumentException("value is too large.", e);
      }
      catch (InvalidCastException e) {
         throw new ArgumentException("The value parameter is not numeric.", e);
      }
   }

   public T Add(T value)
   {
      return (T) Convert.ChangeType(number + Convert.ToDouble(value), typeof(T));
   }

   public T Subtract(T value)
   {
      return (T) Convert.ChangeType(number - Convert.ToDouble(value), typeof(T));
   }
}

public class FloatingPoint<T> : Number<T>
{
   public FloatingPoint(T number) : base(number)
   {
      if (typeof(float) == number.GetType() ||
          typeof(double) == number.GetType() ||
          typeof(decimal) == number.GetType())
         this.number = Convert.ToDouble(number);
      else
         throw new ArgumentException("The number parameter is not a floating-point number.");
   }
}
// The attempt to compile the example displays the following output:
//       error CS0453: The type 'T' must be a non-nullable value type in
//               order to use it as parameter 'T' in the generic type or method 'Number<T>'
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Number(Of T As Structure)
   ' Use Double as the underlying type, since its range is a superset of
   ' the ranges of all numeric types except BigInteger.
   Protected number As Double

   Public Sub New(value As T)
      Try
         Me.number = Convert.ToDouble(value)
      Catch e As OverflowException
         Throw New ArgumentException("value is too large.", e)
      Catch e As InvalidCastException
         Throw New ArgumentException("The value parameter is not numeric.", e)
      End Try
   End Sub

   Public Function Add(value As T) As T
      Return CType(Convert.ChangeType(number + Convert.ToDouble(value), GetType(T)), T)
   End Function

   Public Function Subtract(value As T) As T
      Return CType(Convert.ChangeType(number - Convert.ToDouble(value), GetType(T)), T)
   End Function
End Class

Public Class FloatingPoint(Of T) : Inherits Number(Of T)
   Public Sub New(number As T)
      MyBase.New(number)
      If TypeOf number Is Single Or
               TypeOf number Is Double Or
               TypeOf number Is Decimal Then
         Me.number = Convert.ToDouble(number)
      Else
         throw new ArgumentException("The number parameter is not a floating-point number.")
      End If
   End Sub
End Class
' The attempt to compile the example displays the following output:
'    error BC32105: Type argument 'T' does not satisfy the 'Structure'
'    constraint for type parameter 'T'.
'
'    Public Class FloatingPoint(Of T) : Inherits Number(Of T)
'                                                          ~
```

<span data-ttu-id="384c1-563">Příklad se úspěšně zkompiluje, `FloatingPoint<T>` pokud je omezení přidáno do třídy.</span><span class="sxs-lookup"><span data-stu-id="384c1-563">The example compiles successfully if the constraint is added to the `FloatingPoint<T>` class.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Number<T> where T : struct
{
   // use Double as the underlying type, since its range is a superset of
   // the ranges of all numeric types except BigInteger.
   protected double number;

   public Number(T value)
   {
      try {
         this.number = Convert.ToDouble(value);
      }
      catch (OverflowException e) {
         throw new ArgumentException("value is too large.", e);
      }
      catch (InvalidCastException e) {
         throw new ArgumentException("The value parameter is not numeric.", e);
      }
   }

   public T Add(T value)
   {
      return (T) Convert.ChangeType(number + Convert.ToDouble(value), typeof(T));
   }

   public T Subtract(T value)
   {
      return (T) Convert.ChangeType(number - Convert.ToDouble(value), typeof(T));
   }
}

public class FloatingPoint<T> : Number<T> where T : struct
{
   public FloatingPoint(T number) : base(number)
   {
      if (typeof(float) == number.GetType() ||
          typeof(double) == number.GetType() ||
          typeof(decimal) == number.GetType())
         this.number = Convert.ToDouble(number);
      else
         throw new ArgumentException("The number parameter is not a floating-point number.");
   }
}
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Number(Of T As Structure)
   ' Use Double as the underlying type, since its range is a superset of
   ' the ranges of all numeric types except BigInteger.
   Protected number As Double

   Public Sub New(value As T)
      Try
         Me.number = Convert.ToDouble(value)
      Catch e As OverflowException
         Throw New ArgumentException("value is too large.", e)
      Catch e As InvalidCastException
         Throw New ArgumentException("The value parameter is not numeric.", e)
      End Try
   End Sub

   Public Function Add(value As T) As T
      Return CType(Convert.ChangeType(number + Convert.ToDouble(value), GetType(T)), T)
   End Function

   Public Function Subtract(value As T) As T
      Return CType(Convert.ChangeType(number - Convert.ToDouble(value), GetType(T)), T)
   End Function
End Class

Public Class FloatingPoint(Of T As Structure) : Inherits Number(Of T)
   Public Sub New(number As T)
      MyBase.New(number)
      If TypeOf number Is Single Or
               TypeOf number Is Double Or
               TypeOf number Is Decimal Then
         Me.number = Convert.ToDouble(number)
      Else
         throw new ArgumentException("The number parameter is not a floating-point number.")
      End If
   End Sub
End Class
```

<span data-ttu-id="384c1-564">Specifikace společného jazyka ukládá konzervativní model instance pro vnořené typy a chráněné členy.</span><span class="sxs-lookup"><span data-stu-id="384c1-564">The Common Language Specification imposes a conservative per-instantiation model for nested types and protected members.</span></span> <span data-ttu-id="384c1-565">Otevřené obecné typy nemohou vystavit pole nebo členy s podpisy, které obsahují konkrétní instanci vnořeného chráněného obecného typu.</span><span class="sxs-lookup"><span data-stu-id="384c1-565">Open generic types cannot expose fields or members with signatures that contain a specific instantiation of a nested, protected generic type.</span></span> <span data-ttu-id="384c1-566">Neobecné typy, které rozšiřují konkrétní konkretizovat obecnou základní třídu nebo rozhraní, nemohou vystavit pole nebo členy s podpisy, které obsahují jinou instanci vnořeného chráněného obecného typu.</span><span class="sxs-lookup"><span data-stu-id="384c1-566">Non-generic types that extend a specific instantiation of a generic base class or interface cannot expose fields or members with signatures that contain a different instantiation of a nested, protected generic type.</span></span>

<span data-ttu-id="384c1-567">Následující příklad definuje obecný typ `C1<T>`a chráněnou `C1<T>.N`třídu .</span><span class="sxs-lookup"><span data-stu-id="384c1-567">The following example defines a generic type, `C1<T>`, and a protected class, `C1<T>.N`.</span></span> <span data-ttu-id="384c1-568">`C1<T>`má dvě `M1` metody `M2`a .</span><span class="sxs-lookup"><span data-stu-id="384c1-568">`C1<T>` has two methods, `M1` and `M2`.</span></span> <span data-ttu-id="384c1-569">Však `M1` není kompatibilní se standardem CLS, protože se pokusí vrátit `C1<int>.N` objekt z `C1<T>`.</span><span class="sxs-lookup"><span data-stu-id="384c1-569">However, `M1` is not CLS-compliant because it tries to return a `C1<int>.N` object from `C1<T>`.</span></span> <span data-ttu-id="384c1-570">Druhá třída `C2`, je odvozena od `C1<long>`.</span><span class="sxs-lookup"><span data-stu-id="384c1-570">A second class, `C2`, is derived from `C1<long>`.</span></span> <span data-ttu-id="384c1-571">Má dvě metody `M3` `M4`a .</span><span class="sxs-lookup"><span data-stu-id="384c1-571">It has two methods, `M3` and `M4`.</span></span> <span data-ttu-id="384c1-572">`M3`není kompatibilní se sítí CLS, `C1<int>.N` protože se pokusí `C1<long>`vrátit objekt z podtřídy rozhraní .</span><span class="sxs-lookup"><span data-stu-id="384c1-572">`M3` is not CLS-compliant because it tries to return a `C1<int>.N` object from a subclass of `C1<long>`.</span></span> <span data-ttu-id="384c1-573">Všimněte si, že kompilátory jazyka může být ještě více omezující.</span><span class="sxs-lookup"><span data-stu-id="384c1-573">Note that language compilers can be even more restrictive.</span></span> <span data-ttu-id="384c1-574">V tomto příkladu visual basic zobrazí chybu `M4`při pokusu o kompilaci .</span><span class="sxs-lookup"><span data-stu-id="384c1-574">In this example, Visual Basic displays an error when it tries to compile `M4`.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public class C1<T>
{
   protected class N { }

   protected void M1(C1<int>.N n) { } // Not CLS-compliant - C1<int>.N not
                                      // accessible from within C1<T> in all
                                      // languages
   protected void M2(C1<T>.N n) { }   // CLS-compliant – C1<T>.N accessible
                                      // inside C1<T>
}

public class C2 : C1<long>
{
   protected void M3(C1<int>.N n) { }  // Not CLS-compliant – C1<int>.N is not
                                       // accessible in C2 (extends C1<long>)

   protected void M4(C1<long>.N n) { } // CLS-compliant, C1<long>.N is
                                       // accessible in C2 (extends C1<long>)
}
// Attempting to compile the example displays output like the following:
//       Generics4.cs(9,22): warning CS3001: Argument type 'C1<int>.N' is not CLS-compliant
//       Generics4.cs(18,22): warning CS3001: Argument type 'C1<int>.N' is not CLS-compliant
```

```vb
<Assembly:CLSCompliant(True)>

Public Class C1(Of T)
   Protected Class N
   End Class

   Protected Sub M1(n As C1(Of Integer).N)   ' Not CLS-compliant - C1<int>.N not
                                             ' accessible from within C1(Of T) in all
   End Sub                                   ' languages

   Protected Sub M2(n As C1(Of T).N)     ' CLS-compliant – C1(Of T).N accessible
   End Sub                               ' inside C1(Of T)
End Class

Public Class C2 : Inherits C1(Of Long)
   Protected Sub M3(n As C1(Of Integer).N)   ' Not CLS-compliant – C1(Of Integer).N is not
   End Sub                                   ' accessible in C2 (extends C1(Of Long))

   Protected Sub M4(n As C1(Of Long).N)
   End Sub
End Class
' Attempting to compile the example displays output like the following:
'    error BC30508: 'n' cannot expose type 'C1(Of Integer).N' in namespace
'    '<Default>' through class 'C1'.
'
'       Protected Sub M1(n As C1(Of Integer).N)   ' Not CLS-compliant - C1<int>.N not
'                             ~~~~~~~~~~~~~~~~
'    error BC30389: 'C1(Of T).N' is not accessible in this context because
'    it is 'Protected'.
'
'       Protected Sub M3(n As C1(Of Integer).N)   ' Not CLS-compliant - C1(Of Integer).N is not
'
'                             ~~~~~~~~~~~~~~~~
'
'    error BC30389: 'C1(Of T).N' is not accessible in this context because it is 'Protected'.
'
'       Protected Sub M4(n As C1(Of Long).N)
'                             ~~~~~~~~~~~~~
```

### <a name="constructors"></a><span data-ttu-id="384c1-575">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="384c1-575">Constructors</span></span>

<span data-ttu-id="384c1-576">Konstruktory ve třídách a strukturách kompatibilních se standardem CLS se musí řídit těmito pravidly:</span><span class="sxs-lookup"><span data-stu-id="384c1-576">Constructors in CLS-compliant classes and structures must follow these rules:</span></span>

* <span data-ttu-id="384c1-577">Konstruktor odvozené třídy musí volat konstruktor instance své základní třídy předtím, než přistupuje k datům zděděné instance.</span><span class="sxs-lookup"><span data-stu-id="384c1-577">A constructor of a derived class must call the instance constructor of its base class before it accesses inherited instance data.</span></span> <span data-ttu-id="384c1-578">Tento požadavek je způsoben skutečností, že konstruktory základní třídy nejsou zděděny jejich odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="384c1-578">This requirement is due to the fact that base class constructors are not inherited by their derived classes.</span></span> <span data-ttu-id="384c1-579">Toto pravidlo se nevztahuje na struktury, které nepodporují přímou dědičnost.</span><span class="sxs-lookup"><span data-stu-id="384c1-579">This rule does not apply to structures, which do not support direct inheritance.</span></span>

  <span data-ttu-id="384c1-580">Kompilátory obvykle vynucují toto pravidlo nezávisle na dodržování předpisů cls, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="384c1-580">Typically, compilers enforce this rule independently of CLS compliance, as the following example shows.</span></span> <span data-ttu-id="384c1-581">Vytvoří `Doctor` třídu, která je `Person` odvozena z `Doctor` třídy, `Person` ale třída se nezdaří volat konstruktor třídy inicializovat zděděná pole instance.</span><span class="sxs-lookup"><span data-stu-id="384c1-581">It creates a `Doctor` class that is derived from a `Person` class, but the `Doctor` class fails to call the `Person` class constructor to initialize inherited instance fields.</span></span>

    ```csharp
    using System;

    [assembly: CLSCompliant(true)]

    public class Person
    {
    private string fName, lName, _id;

    public Person(string firstName, string lastName, string id)
    {
        if (String.IsNullOrEmpty(firstName + lastName))
            throw new ArgumentNullException("Either a first name or a last name must be provided.");

        fName = firstName;
        lName = lastName;
        _id = id;
    }

    public string FirstName
    {
        get { return fName; }
    }

    public string LastName
    {
        get { return lName; }
    }

    public string Id
    {
        get { return _id; }
    }

    public override string ToString()
    {
        return String.Format("{0}{1}{2}", fName,
                            String.IsNullOrEmpty(fName) ?  "" : " ",
                            lName);
    }
    }

    public class Doctor : Person
    {
    public Doctor(string firstName, string lastName, string id)
    {
    }

    public override string ToString()
    {
        return "Dr. " + base.ToString();
    }
    }
    // Attempting to compile the example displays output like the following:
    //    ctor1.cs(45,11): error CS1729: 'Person' does not contain a constructor that takes 0
    //            arguments
    //    ctor1.cs(10,11): (Location of symbol related to previous error)
    ```

    ```vb
    <Assembly: CLSCompliant(True)>

    Public Class Person
       Private fName, lName, _id As String

       Public Sub New(firstName As String, lastName As String, id As String)
          If String.IsNullOrEmpty(firstName + lastName) Then
             Throw New ArgumentNullException("Either a first name or a last name must be provided.")
          End If

          fName = firstName
          lName = lastName
          _id = id
       End Sub

       Public ReadOnly Property FirstName As String
          Get
             Return fName
          End Get
       End Property

       Public ReadOnly Property LastName As String
          Get
             Return lName
          End Get
       End Property

       Public ReadOnly Property Id As String
          Get
             Return _id
          End Get
       End Property

       Public Overrides Function ToString() As String
          Return String.Format("{0}{1}{2}", fName,
                               If(String.IsNullOrEmpty(fName), "", " "),
                               lName)
       End Function
    End Class

    Public Class Doctor : Inherits Person
       Public Sub New(firstName As String, lastName As String, id As String)
       End Sub

       Public Overrides Function ToString() As String
          Return "Dr. " + MyBase.ToString()
       End Function
    End Class
    ' Attempting to compile the example displays output like the following:
    '    Ctor1.vb(46) : error BC30148: First statement of this 'Sub New' must be a call
    '    to 'MyBase.New' or 'MyClass.New' because base class 'Person' of 'Doctor' does
    '    not have an accessible 'Sub New' that can be called with no arguments.
    '
    '       Public Sub New()
    '                  ~~~
    ````

* <span data-ttu-id="384c1-582">Konstruktor objektu nelze volat s výjimkou vytvoření objektu.</span><span class="sxs-lookup"><span data-stu-id="384c1-582">An object constructor cannot be called except to create an object.</span></span> <span data-ttu-id="384c1-583">Kromě toho objekt nelze inicializovat dvakrát.</span><span class="sxs-lookup"><span data-stu-id="384c1-583">In addition, an object cannot be initialized twice.</span></span> <span data-ttu-id="384c1-584">Například to znamená, že `Object.MemberwiseClone` nesmí volat konstruktory.</span><span class="sxs-lookup"><span data-stu-id="384c1-584">For example, this means that `Object.MemberwiseClone` must not call constructors.</span></span>

### <a name="properties"></a><span data-ttu-id="384c1-585">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="384c1-585">Properties</span></span>

<span data-ttu-id="384c1-586">Vlastnosti v typech kompatibilních se standardem CLS se musí řídit těmito pravidly:</span><span class="sxs-lookup"><span data-stu-id="384c1-586">Properties in CLS-compliant types must follow these rules:</span></span>

* <span data-ttu-id="384c1-587">Vlastnost musí mít setter, getter nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="384c1-587">A property must have a setter, a getter, or both.</span></span> <span data-ttu-id="384c1-588">V sestavení jsou implementovány jako speciální metody, což znamená, že se zobrazí `get` \_jako samostatné metody (getter se `SpecialName` nazývá *propertyname* a setter je `set` \_ *propertyname*) označené jako v metadatech sestavení.</span><span class="sxs-lookup"><span data-stu-id="384c1-588">In an assembly, these are implemented as special methods, which means that they will appear as separate methods (the getter is named `get`\_*propertyname* and the setter is `set`\_*propertyname*) marked as `SpecialName` in the assembly's metadata.</span></span> <span data-ttu-id="384c1-589">Kompilátor Jazyka C# vynucuje toto pravidlo automaticky bez nutnosti <xref:System.CLSCompliantAttribute> použít atribut.</span><span class="sxs-lookup"><span data-stu-id="384c1-589">The C# compiler enforces this rule automatically without the need to apply the <xref:System.CLSCompliantAttribute> attribute.</span></span>

* <span data-ttu-id="384c1-590">Typ vlastnosti je návratový typ vlastnosti getter a poslední argument setter.</span><span class="sxs-lookup"><span data-stu-id="384c1-590">A property's type is the return type of the property getter and the last argument of the setter.</span></span> <span data-ttu-id="384c1-591">Tyto typy musí být kompatibilní se standardem CLS a argumenty nelze přiřadit k vlastnosti odkazem (to znamená, že nemohou být spravovány ukazatele).</span><span class="sxs-lookup"><span data-stu-id="384c1-591">These types must be CLS compliant, and arguments cannot be assigned to the property by reference (that is, they cannot be managed pointers).</span></span>

* <span data-ttu-id="384c1-592">Pokud vlastnost má getter a setter, musí být oba virtuální, statické nebo obě instance.</span><span class="sxs-lookup"><span data-stu-id="384c1-592">If a property has both a getter and a setter, they must both be virtual, both static, or both instance.</span></span> <span data-ttu-id="384c1-593">Kompilátor Jazyka C# automaticky vynucuje toto pravidlo prostřednictvím syntaxe definice vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="384c1-593">The C# compiler automatically enforces this rule through property definition syntax.</span></span>

### <a name="events"></a><span data-ttu-id="384c1-594">Akce</span><span class="sxs-lookup"><span data-stu-id="384c1-594">Events</span></span>

<span data-ttu-id="384c1-595">Událost je definována svým názvem a typem.</span><span class="sxs-lookup"><span data-stu-id="384c1-595">An event is defined by its name and its type.</span></span> <span data-ttu-id="384c1-596">Typ události je delegát, který se používá k označení události.</span><span class="sxs-lookup"><span data-stu-id="384c1-596">The event type is a delegate that is used to indicate the event.</span></span> <span data-ttu-id="384c1-597">Například `DbConnection.StateChange` událost je typu `StateChangeEventHandler`.</span><span class="sxs-lookup"><span data-stu-id="384c1-597">For example, the `DbConnection.StateChange` event is of type `StateChangeEventHandler`.</span></span> <span data-ttu-id="384c1-598">Kromě samotné události poskytují implementaci události tři metody s názvy založenými na `SpecialName` názvu události a jsou označeny jako v metadatech sestavení:</span><span class="sxs-lookup"><span data-stu-id="384c1-598">In addition to the event itself, three methods with names based on the event name provide the event's implementation and are marked as `SpecialName` in the assembly's metadata:</span></span>

* <span data-ttu-id="384c1-599">Metoda pro přidání obslužné rutiny události s názvem `add`_*EventName*.</span><span class="sxs-lookup"><span data-stu-id="384c1-599">A method for adding an event handler, named `add`_*EventName*.</span></span> <span data-ttu-id="384c1-600">Například metoda odběru události `DbConnection.StateChange` pro událost `add_StateChange`je pojmenována .</span><span class="sxs-lookup"><span data-stu-id="384c1-600">For example, the event subscription method for the `DbConnection.StateChange` event is named `add_StateChange`.</span></span>

* <span data-ttu-id="384c1-601">Metoda odebrání obslužné `remove`rutiny události s názvem _*EventName*.</span><span class="sxs-lookup"><span data-stu-id="384c1-601">A method for removing an event handler, named `remove`_*EventName*.</span></span> <span data-ttu-id="384c1-602">Například metoda odebrání pro `DbConnection.StateChange` událost `remove_StateChange`je pojmenována .</span><span class="sxs-lookup"><span data-stu-id="384c1-602">For example, the removal method for the `DbConnection.StateChange` event is named `remove_StateChange`.</span></span>

* <span data-ttu-id="384c1-603">Metoda označující, že došlo k `raise` \_události s názvem *EventName*.</span><span class="sxs-lookup"><span data-stu-id="384c1-603">A method for indicating that the event has occurred, named `raise`\_*EventName*.</span></span>

> [!NOTE]
> <span data-ttu-id="384c1-604">Většina pravidel společné jazykové specifikace týkající se událostí je implementována kompilátory jazyka a je transparentní pro vývojáře komponent.</span><span class="sxs-lookup"><span data-stu-id="384c1-604">Most of the Common Language Specification's rules regarding events are implemented by language compilers and are transparent to component developers.</span></span>

<span data-ttu-id="384c1-605">Metody pro přidání, odebrání a vyvolání události musí mít stejnou přístupnost.</span><span class="sxs-lookup"><span data-stu-id="384c1-605">The methods for adding, removing, and raising the event must have the same accessibility.</span></span> <span data-ttu-id="384c1-606">Musí být také všechny statické, instance nebo virtuální.</span><span class="sxs-lookup"><span data-stu-id="384c1-606">They must also all be static, instance, or virtual.</span></span> <span data-ttu-id="384c1-607">Metody pro přidání a odebrání události mají jeden parametr, jehož typ je typ delegáta události.</span><span class="sxs-lookup"><span data-stu-id="384c1-607">The methods for adding and removing an event have one parameter whose type is the event delegate type.</span></span> <span data-ttu-id="384c1-608">Metody add a remove musí být přítomny nebo obě chybí.</span><span class="sxs-lookup"><span data-stu-id="384c1-608">The add and remove methods must both be present or both be absent.</span></span>

<span data-ttu-id="384c1-609">Následující příklad definuje třídu kompatibilní se `Temperature` seznamem `TemperatureChanged` CLS s názvem, která vyvolá událost, pokud se změna teploty mezi dvěma hodnotami rovná nebo překročí prahovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="384c1-609">The following example defines a CLS-compliant class named `Temperature` that raises a `TemperatureChanged` event if the change in temperature between two readings equals or exceeds a threshold value.</span></span> <span data-ttu-id="384c1-610">Třída `Temperature` explicitně definuje `raise_TemperatureChanged` metodu tak, aby mohla selektivně spouštět obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="384c1-610">The `Temperature` class explicitly defines a `raise_TemperatureChanged` method so that it can selectively execute event handlers.</span></span>

```csharp
using System;
using System.Collections;
using System.Collections.Generic;

[assembly: CLSCompliant(true)]

public class TemperatureChangedEventArgs : EventArgs
{
   private Decimal originalTemp;
   private Decimal newTemp;
   private DateTimeOffset when;

   public TemperatureChangedEventArgs(Decimal original, Decimal @new, DateTimeOffset time)
   {
      originalTemp = original;
      newTemp = @new;
      when = time;
   }

   public Decimal OldTemperature
   {
      get { return originalTemp; }
   }

   public Decimal CurrentTemperature
   {
      get { return newTemp; }
   }

   public DateTimeOffset Time
   {
      get { return when; }
   }
}

public delegate void TemperatureChanged(Object sender, TemperatureChangedEventArgs e);

public class Temperature
{
   private struct TemperatureInfo
   {
      public Decimal Temperature;
      public DateTimeOffset Recorded;
   }

   public event TemperatureChanged TemperatureChanged;

   private Decimal previous;
   private Decimal current;
   private Decimal tolerance;
   private List<TemperatureInfo> tis = new List<TemperatureInfo>();

   public Temperature(Decimal temperature, Decimal tolerance)
   {
      current = temperature;
      TemperatureInfo ti = new TemperatureInfo();
      ti.Temperature = temperature;
      tis.Add(ti);
      ti.Recorded = DateTimeOffset.UtcNow;
      this.tolerance = tolerance;
   }

   public Decimal CurrentTemperature
   {
      get { return current; }
      set {
         TemperatureInfo ti = new TemperatureInfo();
         ti.Temperature = value;
         ti.Recorded = DateTimeOffset.UtcNow;
         previous = current;
         current = value;
         if (Math.Abs(current - previous) >= tolerance)
            raise_TemperatureChanged(new TemperatureChangedEventArgs(previous, current, ti.Recorded));
      }
   }

   public void raise_TemperatureChanged(TemperatureChangedEventArgs eventArgs)
   {
      if (TemperatureChanged == null)
         return;

      foreach (TemperatureChanged d in TemperatureChanged.GetInvocationList()) {
         if (d.Method.Name.Contains("Duplicate"))
            Console.WriteLine("Duplicate event handler; event handler not executed.");
         else
            d.Invoke(this, eventArgs);
      }
   }
}

public class Example
{
   public Temperature temp;

   public static void Main()
   {
      Example ex = new Example();
   }

   public Example()
   {
      temp = new Temperature(65, 3);
      temp.TemperatureChanged += this.TemperatureNotification;
      RecordTemperatures();
      Example ex = new Example(temp);
      ex.RecordTemperatures();
   }

   public Example(Temperature t)
   {
      temp = t;
      RecordTemperatures();
   }

   public void RecordTemperatures()
   {
      temp.TemperatureChanged += this.DuplicateTemperatureNotification;
      temp.CurrentTemperature = 66;
      temp.CurrentTemperature = 63;
   }

   internal void TemperatureNotification(Object sender, TemperatureChangedEventArgs e)
   {
      Console.WriteLine("Notification 1: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature);
   }

   public void DuplicateTemperatureNotification(Object sender, TemperatureChangedEventArgs e)
   {
      Console.WriteLine("Notification 2: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature);
   }
}
```

```vb
Imports System.Collections
Imports System.Collections.Generic

<Assembly: CLSCompliant(True)>

Public Class TemperatureChangedEventArgs   : Inherits EventArgs
   Private originalTemp As Decimal
   Private newTemp As Decimal
   Private [when] As DateTimeOffset

   Public Sub New(original As Decimal, [new] As Decimal, [time] As DateTimeOffset)
      originalTemp = original
      newTemp = [new]
      [when] = [time]
   End Sub

   Public ReadOnly Property OldTemperature As Decimal
      Get
         Return originalTemp
      End Get
   End Property

   Public ReadOnly Property CurrentTemperature As Decimal
      Get
         Return newTemp
      End Get
   End Property

   Public ReadOnly Property [Time] As DateTimeOffset
      Get
         Return [when]
      End Get
   End Property
End Class

Public Delegate Sub TemperatureChanged(sender As Object, e As TemperatureChangedEventArgs)

Public Class Temperature
   Private Structure TemperatureInfo
      Dim Temperature As Decimal
      Dim Recorded As DateTimeOffset
   End Structure

   Public Event TemperatureChanged As TemperatureChanged

   Private previous As Decimal
   Private current As Decimal
   Private tolerance As Decimal
   Private tis As New List(Of TemperatureInfo)

   Public Sub New(temperature As Decimal, tolerance As Decimal)
      current = temperature
      Dim ti As New TemperatureInfo()
      ti.Temperature = temperature
      ti.Recorded = DateTimeOffset.UtcNow
      tis.Add(ti)
      Me.tolerance = tolerance
   End Sub

   Public Property CurrentTemperature As Decimal
      Get
         Return current
      End Get
      Set
         Dim ti As New TemperatureInfo
         ti.Temperature = value
         ti.Recorded = DateTimeOffset.UtcNow
         previous = current
         current = value
         If Math.Abs(current - previous) >= tolerance Then
            raise_TemperatureChanged(New TemperatureChangedEventArgs(previous, current, ti.Recorded))
         End If
      End Set
   End Property

   Public Sub raise_TemperatureChanged(eventArgs As TemperatureChangedEventArgs)
      If TemperatureChangedEvent Is Nothing Then Exit Sub

      Dim ListenerList() As System.Delegate = TemperatureChangedEvent.GetInvocationList()
      For Each d As TemperatureChanged In TemperatureChangedEvent.GetInvocationList()
         If d.Method.Name.Contains("Duplicate") Then
            Console.WriteLine("Duplicate event handler; event handler not executed.")
         Else
            d.Invoke(Me, eventArgs)
         End If
      Next
   End Sub
End Class

Public Class Example
   Public WithEvents temp As Temperature

   Public Shared Sub Main()
      Dim ex As New Example()
   End Sub

   Public Sub New()
      temp = New Temperature(65, 3)
      RecordTemperatures()
      Dim ex As New Example(temp)
      ex.RecordTemperatures()
   End Sub

   Public Sub New(t As Temperature)
      temp = t
      RecordTemperatures()
   End Sub

   Public Sub RecordTemperatures()
      temp.CurrentTemperature = 66
      temp.CurrentTemperature = 63

   End Sub

   Friend Shared Sub TemperatureNotification(sender As Object, e As TemperatureChangedEventArgs) _
          Handles temp.TemperatureChanged
      Console.WriteLine("Notification 1: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature)
   End Sub

   Friend Shared Sub DuplicateTemperatureNotification(sender As Object, e As TemperatureChangedEventArgs) _
          Handles temp.TemperatureChanged
      Console.WriteLine("Notification 2: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature)
   End Sub
End Class
```

### <a name="overloads"></a><span data-ttu-id="384c1-611">Přetížení</span><span class="sxs-lookup"><span data-stu-id="384c1-611">Overloads</span></span>

<span data-ttu-id="384c1-612">Specifikace společného jazyka ukládá přetíženým členům následující požadavky:</span><span class="sxs-lookup"><span data-stu-id="384c1-612">The Common Language Specification imposes the following requirements on overloaded members:</span></span>

* <span data-ttu-id="384c1-613">Členy mohou být přetíženy na základě počtu parametrů a typu libovolného parametru.</span><span class="sxs-lookup"><span data-stu-id="384c1-613">Members can be overloaded based on the number of parameters and the type of any parameter.</span></span> <span data-ttu-id="384c1-614">Volání konvence, návratový typ, vlastní modifikátory použité na metodu nebo její parametr a zda parametry jsou předány hodnotou nebo odkazem nejsou považovány při rozlišování mezi přetížení.</span><span class="sxs-lookup"><span data-stu-id="384c1-614">Calling convention, return type, custom modifiers applied to the method or its parameter, and whether parameters are passed by value or by reference are not considered when differentiating between overloads.</span></span> <span data-ttu-id="384c1-615">Příklad naleznete v kódu požadavku, že názvy musí být jedinečné v rámci oboru v části [Konvence pojmenování.](#naming-conventions)</span><span class="sxs-lookup"><span data-stu-id="384c1-615">For an example, see the code for the requirement that names must be unique within a scope in the [Naming conventions](#naming-conventions) section.</span></span>

* <span data-ttu-id="384c1-616">Pouze vlastnosti a metody mohou být přetíženy.</span><span class="sxs-lookup"><span data-stu-id="384c1-616">Only properties and methods can be overloaded.</span></span> <span data-ttu-id="384c1-617">Pole a události nemohou být přetíženy.</span><span class="sxs-lookup"><span data-stu-id="384c1-617">Fields and events cannot be overloaded.</span></span>

* <span data-ttu-id="384c1-618">Obecné metody mohou být přetíženy na základě počtu jejich obecných parametrů.</span><span class="sxs-lookup"><span data-stu-id="384c1-618">Generic methods can be overloaded based on the number of their generic parameters.</span></span>

> [!NOTE]
> <span data-ttu-id="384c1-619">A `op_Explicit` `op_Implicit` operátory jsou výjimky z pravidla, že vrácená hodnota není považována za součást podpisu metody pro řešení přetížení.</span><span class="sxs-lookup"><span data-stu-id="384c1-619">The `op_Explicit` and `op_Implicit` operators are exceptions to the rule that return value is not considered part of a method signature for overload resolution.</span></span> <span data-ttu-id="384c1-620">Tyto dva operátory mohou být přetíženy na základě jejich parametry a jejich vrácená hodnota.</span><span class="sxs-lookup"><span data-stu-id="384c1-620">These two operators can be overloaded based on both their parameters and their return value.</span></span>

### <a name="exceptions"></a><span data-ttu-id="384c1-621">Výjimky</span><span class="sxs-lookup"><span data-stu-id="384c1-621">Exceptions</span></span>

<span data-ttu-id="384c1-622">Objekty výjimek musí být odvozeny z `System.Exception` [system.exception](xref:System.Exception) nebo z jiného typu odvozeného z .</span><span class="sxs-lookup"><span data-stu-id="384c1-622">Exception objects must derive from [System.Exception](xref:System.Exception) or from another type derived from `System.Exception`.</span></span> <span data-ttu-id="384c1-623">Následující příklad ilustruje chybu kompilátoru, která `ErrorClass` se vynaložit při vlastní třídy s názvem se používá pro zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="384c1-623">The following example illustrates the compiler error that results when a custom class named `ErrorClass` is used for exception handling.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ErrorClass
{
   string msg;

   public ErrorClass(string errorMessage)
   {
      msg = errorMessage;
   }

   public string Message
   {
      get { return msg; }
   }
}

public static class StringUtilities
{
   public static string[] SplitString(this string value, int index)
   {
      if (index < 0 | index > value.Length) {
         ErrorClass badIndex = new ErrorClass("The index is not within the string.");
         throw badIndex;
      }
      string[] retVal = { value.Substring(0, index - 1),
                          value.Substring(index) };
      return retVal;
   }
}
// Compilation produces a compiler error like the following:
//    Exceptions1.cs(26,16): error CS0155: The type caught or thrown must be derived from
//            System.Exception
```

```vb
Imports System.Runtime.CompilerServices

<Assembly: CLSCompliant(True)>

Public Class ErrorClass
   Dim msg As String

   Public Sub New(errorMessage As String)
      msg = errorMessage
   End Sub

   Public ReadOnly Property Message As String
      Get
         Return msg
      End Get
   End Property
End Class

Public Module StringUtilities
   <Extension()> Public Function SplitString(value As String, index As Integer) As String()
      If index < 0 Or index > value.Length Then
         Dim BadIndex As New ErrorClass("The index is not within the string.")
         Throw BadIndex
      End If
      Dim retVal() As String = { value.Substring(0, index - 1),
                                 value.Substring(index) }
      Return retVal
   End Function
End Module
' Compilation produces a compiler error like the following:
'    Exceptions1.vb(27) : error BC30665: 'Throw' operand must derive from 'System.Exception'.
'
'             Throw BadIndex
'             ~~~~~~~~~~~~~~
```

<span data-ttu-id="384c1-624">Chcete-li opravit `ErrorClass` tuto chybu, `System.Exception`třída musí dědit z .</span><span class="sxs-lookup"><span data-stu-id="384c1-624">To correct this error, the `ErrorClass` class must inherit from `System.Exception`.</span></span> <span data-ttu-id="384c1-625">Kromě toho Message vlastnost musí být přepsána.</span><span class="sxs-lookup"><span data-stu-id="384c1-625">In addition, the Message property must be overridden.</span></span> <span data-ttu-id="384c1-626">Následující příklad opravuje tyto chyby definovat třídu, `ErrorClass` která je kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-626">The following example corrects these errors to define an `ErrorClass` class that is CLS-compliant.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ErrorClass : Exception
{
   string msg;

   public ErrorClass(string errorMessage)
   {
      msg = errorMessage;
   }

   public override string Message
   {
      get { return msg; }
   }
}

public static class StringUtilities
{
   public static string[] SplitString(this string value, int index)
   {
      if (index < 0 | index > value.Length) {
         ErrorClass badIndex = new ErrorClass("The index is not within the string.");
         throw badIndex;
      }
      string[] retVal = { value.Substring(0, index - 1),
                          value.Substring(index) };
      return retVal;
   }
}
```

```vb
Imports System.Runtime.CompilerServices

<Assembly: CLSCompliant(True)>

Public Class ErrorClass : Inherits Exception
   Dim msg As String

   Public Sub New(errorMessage As String)
      msg = errorMessage
   End Sub

   Public Overrides ReadOnly Property Message As String
      Get
         Return msg
      End Get
   End Property
End Class

Public Module StringUtilities
   <Extension()> Public Function SplitString(value As String, index As Integer) As String()
      If index < 0 Or index > value.Length Then
         Dim BadIndex As New ErrorClass("The index is not within the string.")
         Throw BadIndex
      End If
      Dim retVal() As String = { value.Substring(0, index - 1),
                                 value.Substring(index) }
      Return retVal
   End Function
End Module
```

### <a name="attributes"></a><span data-ttu-id="384c1-627">Atributy</span><span class="sxs-lookup"><span data-stu-id="384c1-627">Attributes</span></span>

<span data-ttu-id="384c1-628">In.NET framework sestavení, vlastní atributy poskytují rozšiřitelný mechanismus pro ukládání vlastních atributů a načítání metadat o programovacích objektech, jako jsou sestavení, typy, členy a parametry metody.</span><span class="sxs-lookup"><span data-stu-id="384c1-628">In.NET Framework assemblies, custom attributes provide an extensible mechanism for storing custom attributes and retrieving metadata about programming objects, such as assemblies, types, members, and method parameters.</span></span> <span data-ttu-id="384c1-629">Vlastní atributy musí být odvozeny z [System.Attribute](xref:System.Attribute) nebo z typu odvozeného z . `System.Attribute`</span><span class="sxs-lookup"><span data-stu-id="384c1-629">Custom attributes must derive from [System.Attribute](xref:System.Attribute) or from a type derived from `System.Attribute`.</span></span>

<span data-ttu-id="384c1-630">Následující příklad porušuje toto pravidlo.</span><span class="sxs-lookup"><span data-stu-id="384c1-630">The following example violates this rule.</span></span> <span data-ttu-id="384c1-631">Definuje třídu, `NumericAttribute` která není `System.Attribute`odvozena z .</span><span class="sxs-lookup"><span data-stu-id="384c1-631">It defines a `NumericAttribute` class that does not derive from `System.Attribute`.</span></span> <span data-ttu-id="384c1-632">Všimněte si, že chyba kompilátoru výsledky pouze v případě, že je použit atribut nekompatibilní se standardem CLS, nikoli při definování třídy.</span><span class="sxs-lookup"><span data-stu-id="384c1-632">Note that a compiler error results only when the non-CLS-compliant attribute is applied, not when the class is defined.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

[AttributeUsageAttribute(AttributeTargets.Class | AttributeTargets.Struct)]
public class NumericAttribute
{
   private bool _isNumeric;

   public NumericAttribute(bool isNumeric)
   {
      _isNumeric = isNumeric;
   }

   public bool IsNumeric
   {
      get { return _isNumeric; }
   }
}

[Numeric(true)] public struct UDouble
{
   double Value;
}
// Compilation produces a compiler error like the following:
//    Attribute1.cs(22,2): error CS0616: 'NumericAttribute' is not an attribute class
//    Attribute1.cs(7,14): (Location of symbol related to previous error)
```

```vb
<Assembly: CLSCompliant(True)>

<AttributeUsageAttribute(AttributeTargets.Class Or AttributeTargets.Struct)> _
Public Class NumericAttribute
   Private _isNumeric As Boolean

   Public Sub New(isNumeric As Boolean)
      _isNumeric = isNumeric
   End Sub

   Public ReadOnly Property IsNumeric As Boolean
      Get
         Return _isNumeric
      End Get
   End Property
End Class

<Numeric(True)> Public Structure UDouble
   Dim Value As Double
End Structure
' Compilation produces a compiler error like the following:
'    error BC31504: 'NumericAttribute' cannot be used as an attribute because it
'    does not inherit from 'System.Attribute'.
'
'    <Numeric(True)> Public Structure UDouble
'     ~~~~~~~~~~~~~
```

<span data-ttu-id="384c1-633">Konstruktor nebo vlastnosti atributu kompatibilního se standardem CLS mohou vystavit pouze následující typy:</span><span class="sxs-lookup"><span data-stu-id="384c1-633">The constructor or the properties of a CLS-compliant attribute can expose only the following types:</span></span>

* [<span data-ttu-id="384c1-634">Logická hodnota</span><span class="sxs-lookup"><span data-stu-id="384c1-634">Boolean</span></span>](xref:System.Boolean)

* [<span data-ttu-id="384c1-635">Byte</span><span class="sxs-lookup"><span data-stu-id="384c1-635">Byte</span></span>](xref:System.Byte)

* [<span data-ttu-id="384c1-636">Char</span><span class="sxs-lookup"><span data-stu-id="384c1-636">Char</span></span>](xref:System.Char)

* [<span data-ttu-id="384c1-637">Dvojité</span><span class="sxs-lookup"><span data-stu-id="384c1-637">Double</span></span>](xref:System.Double)

* [<span data-ttu-id="384c1-638">Int16</span><span class="sxs-lookup"><span data-stu-id="384c1-638">Int16</span></span>](xref:System.Int16)

* [<span data-ttu-id="384c1-639">Int32</span><span class="sxs-lookup"><span data-stu-id="384c1-639">Int32</span></span>](xref:System.Int32)

* [<span data-ttu-id="384c1-640">Int64</span><span class="sxs-lookup"><span data-stu-id="384c1-640">Int64</span></span>](xref:System.Int64)

* [<span data-ttu-id="384c1-641">Single</span><span class="sxs-lookup"><span data-stu-id="384c1-641">Single</span></span>](xref:System.Single)

* [<span data-ttu-id="384c1-642">Řetězec</span><span class="sxs-lookup"><span data-stu-id="384c1-642">String</span></span>](xref:System.String)

* [<span data-ttu-id="384c1-643">Typ</span><span class="sxs-lookup"><span data-stu-id="384c1-643">Type</span></span>](xref:System.Type)

* <span data-ttu-id="384c1-644">Libovolný typ výčtu, `Byte`jehož `Int32`základní `Int64`typ je , `Int16`, , nebo .</span><span class="sxs-lookup"><span data-stu-id="384c1-644">Any enumeration type whose underlying type is `Byte`, `Int16`, `Int32`, or `Int64`.</span></span>

<span data-ttu-id="384c1-645">Následující příklad definuje `DescriptionAttribute` třídu, která je odvozena z [Atribut](xref:System.Attribute).</span><span class="sxs-lookup"><span data-stu-id="384c1-645">The following example defines a `DescriptionAttribute` class that derives from [Attribute](xref:System.Attribute).</span></span> <span data-ttu-id="384c1-646">Konstruktor třídy má parametr `Descriptor`typu , takže třída není kompatibilní se seznamem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-646">The class constructor has a parameter of type `Descriptor`, so the class is not CLS-compliant.</span></span> <span data-ttu-id="384c1-647">Všimněte si, že kompilátor Jazyka C# vydává upozornění, ale úspěšně se zkompiluje.</span><span class="sxs-lookup"><span data-stu-id="384c1-647">Note that the C# compiler emits a warning but compiles successfully.</span></span>

```csharp
using System;

[assembly:CLSCompliantAttribute(true)]

public enum DescriptorType { type, member };

public class Descriptor
{
   public DescriptorType Type;
   public String Description;
}

[AttributeUsage(AttributeTargets.All)]
public class DescriptionAttribute : Attribute
{
   private Descriptor desc;

   public DescriptionAttribute(Descriptor d)
   {
      desc = d;
   }

   public Descriptor Descriptor
   { get { return desc; } }
}
// Attempting to compile the example displays output like the following:
//       warning CS3015: 'DescriptionAttribute' has no accessible
//               constructors which use only CLS-compliant types
```

```vb
<Assembly:CLSCompliantAttribute(True)>

Public Enum DescriptorType As Integer
   Type = 0
   Member = 1
End Enum

Public Class Descriptor
   Public Type As DescriptorType
   Public Description As String
End Class

<AttributeUsage(AttributeTargets.All)> _
Public Class DescriptionAttribute : Inherits Attribute
   Private desc As Descriptor

   Public Sub New(d As Descriptor)
      desc = d
   End Sub

   Public ReadOnly Property Descriptor As Descriptor
      Get
         Return desc
      End Get
   End Property
End Class
```

## <a name="the-clscompliantattribute-attribute"></a><span data-ttu-id="384c1-648">Atribut CLSCompliantAttribute</span><span class="sxs-lookup"><span data-stu-id="384c1-648">The CLSCompliantAttribute attribute</span></span>

<span data-ttu-id="384c1-649">Atribut [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) se používá k označení, zda prvek programu splňuje specifikaci společného jazyka.</span><span class="sxs-lookup"><span data-stu-id="384c1-649">The [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute is used to indicate whether a program element complies with the Common Language Specification.</span></span> <span data-ttu-id="384c1-650">Konstruktor `CLSCompliantAttribute.CLSCompliantAttribute(Boolean)` obsahuje jeden povinný parametr *isCompliant*, který označuje, zda je prvek programu kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-650">The `CLSCompliantAttribute.CLSCompliantAttribute(Boolean)` constructor includes a single required parameter, *isCompliant*, that indicates whether the program element is CLS-compliant.</span></span>

<span data-ttu-id="384c1-651">V době kompilace kompilátor zjistí nekompatibilní prvky, které jsou považovány za kompatibilní se standardem CLS a vydává upozornění.</span><span class="sxs-lookup"><span data-stu-id="384c1-651">At compile time, the compiler detects non-compliant elements that are presumed to be CLS-compliant and emits a warning.</span></span> <span data-ttu-id="384c1-652">Kompilátor nevydává upozornění pro typy nebo členy, které jsou explicitně deklarovány jako nekompatibilní.</span><span class="sxs-lookup"><span data-stu-id="384c1-652">The compiler does not emit warnings for types or members that are explicitly declared to be non-compliant.</span></span>

<span data-ttu-id="384c1-653">Vývojáři komponent `CLSCompliantAttribute` mohou atribut použít dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="384c1-653">Component developers can use the `CLSCompliantAttribute` attribute in two ways:</span></span>

* <span data-ttu-id="384c1-654">Chcete-li definovat části veřejného rozhraní vystavené komponenty, které jsou kompatibilní se seznamem CLS a součásti, které nejsou kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-654">To define the parts of the public interface exposed by a component that are CLS-compliant and the parts that are not CLS-compliant.</span></span> <span data-ttu-id="384c1-655">Pokud se atribut používá k označení určitých prvků programu jako kompatibilní se standardem CLS, jeho použití zaručuje, že tyto prvky jsou přístupné ze všech jazyků a nástrojů, které cílí na rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="384c1-655">When the attribute is used to mark particular program elements as CLS-compliant, its use guarantees that those elements are accessible from all languages and tools that target the .NET Framework.</span></span>

* <span data-ttu-id="384c1-656">Chcete-li zajistit, že veřejné rozhraní knihovny komponent zpřístupňuje pouze prvky programu, které jsou kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-656">To ensure that the component library's public interface exposes only program elements that are CLS-compliant.</span></span> <span data-ttu-id="384c1-657">Pokud prvky nejsou kompatibilní se seznamem CLS, kompilátory obecně vydá upozornění.</span><span class="sxs-lookup"><span data-stu-id="384c1-657">If elements are not CLS-compliant, compilers will generally issue a warning.</span></span>

> [!WARNING]
> <span data-ttu-id="384c1-658">V některých případech kompilátory jazyka vynucovat cls kompatibilní pravidla bez ohledu na to, zda se používá `CLSCompliantAttribute` atribut.</span><span class="sxs-lookup"><span data-stu-id="384c1-658">In some cases, language compilers enforce CLS-compliant rules regardless of whether the `CLSCompliantAttribute` attribute is used.</span></span> <span data-ttu-id="384c1-659">Například definování `*static` člena v rozhraní porušuje pravidlo CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-659">For example, defining a `*static` member in an interface violates a CLS rule.</span></span> <span data-ttu-id="384c1-660">Pokud však definujete `*static` člena v rozhraní, kompilátor Jazyka C# zobrazí chybovou zprávu a nepodaří se zkompilovat aplikaci.</span><span class="sxs-lookup"><span data-stu-id="384c1-660">However, if you define a `*static` member in an interface, the C# compiler displays an error message and fails to compile the app.</span></span>

<span data-ttu-id="384c1-661">Atribut `CLSCompliantAttribute` je označen atributem [AttributeUsageAttribute,](xref:System.AttributeUsageAttribute) který `AttributeTargets.All`má hodnotu .</span><span class="sxs-lookup"><span data-stu-id="384c1-661">The `CLSCompliantAttribute` attribute is marked with an [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) attribute that has a value of `AttributeTargets.All`.</span></span> <span data-ttu-id="384c1-662">Tato hodnota umožňuje použít `CLSCompliantAttribute` atribut pro libovolný prvek programu, včetně sestavení, modulů, typů (třídy, struktury, výčty, rozhraní a delegáty), členů typu (konstruktory, metody, vlastnosti, pole a události), parametry, obecné parametry a vrácené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="384c1-662">This value allows you to apply the `CLSCompliantAttribute` attribute to any program element, including assemblies, modules, types (classes, structures, enumerations, interfaces, and delegates), type members (constructors, methods, properties, fields, and events), parameters, generic parameters, and return values.</span></span> <span data-ttu-id="384c1-663">V praxi byste však měli atribut použít pouze pro sestavení, typy a členy typu.</span><span class="sxs-lookup"><span data-stu-id="384c1-663">However, in practice, you should apply the attribute only to assemblies, types, and type members.</span></span> <span data-ttu-id="384c1-664">V opačném případě kompilátory ignorovat atribut a nadále generovat upozornění kompilátoru vždy, když narazí na nekompatibilní parametr, obecný parametr nebo vrácenou hodnotu ve veřejné rozhraní knihovny.</span><span class="sxs-lookup"><span data-stu-id="384c1-664">Otherwise, compilers ignore the attribute and continue to generate compiler warnings whenever they encounter a non-compliant parameter, generic parameter, or return value in your library's public interface.</span></span>

<span data-ttu-id="384c1-665">Hodnota atributu `CLSCompliantAttribute` je zděděna obsaženými prvky programu.</span><span class="sxs-lookup"><span data-stu-id="384c1-665">The value of the `CLSCompliantAttribute` attribute is inherited by contained program elements.</span></span> <span data-ttu-id="384c1-666">Například pokud je sestavení označeno jako kompatibilní se standardem CLS, jeho typy jsou také kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-666">For example, if an assembly is marked as CLS-compliant, its types are also CLS-compliant.</span></span> <span data-ttu-id="384c1-667">Pokud je typ označen jako kompatibilní se seznamem CLS, jeho vnořené typy a členy jsou také kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-667">If a type is marked as CLS-compliant, its nested types and members are also CLS-compliant.</span></span>

<span data-ttu-id="384c1-668">Zděděnou dodržování předpisů můžete explicitně přepsat použitím atributu `CLSCompliantAttribute` na prvek obsaženého programu.</span><span class="sxs-lookup"><span data-stu-id="384c1-668">You can explicitly override the inherited compliance by applying the `CLSCompliantAttribute` attribute to a contained program element.</span></span> <span data-ttu-id="384c1-669">Můžete například použít `CLSCompliantAttribute` atribut s hodnotou `false` *isCompliant* k definování nekompatibilního typu v kompatibilním sestavení a můžete `true` použít atribut s hodnotou *isCompliant* k definování kompatibilního typu v nekompatibilním sestavení.</span><span class="sxs-lookup"><span data-stu-id="384c1-669">For example, you can use the `CLSCompliantAttribute` attribute with an *isCompliant* value of `false` to define a non-compliant type in a compliant assembly, and you can use the attribute with an *isCompliant* value of `true` to define a compliant type in a non-compliant assembly.</span></span> <span data-ttu-id="384c1-670">Můžete také definovat nekompatibilní členy v kompatibilním typu.</span><span class="sxs-lookup"><span data-stu-id="384c1-670">You can also define non-compliant members in a compliant type.</span></span> <span data-ttu-id="384c1-671">Nekompatibilní typ však nemůže mít kompatibilní členy, takže nelze použít atribut `true` s hodnotou *isCompliant* k přepsání dědičnosti z nekompatibilního typu.</span><span class="sxs-lookup"><span data-stu-id="384c1-671">However, a non-compliant type cannot have compliant members, so you cannot use the attribute with an *isCompliant* value of `true` to override inheritance from a non-compliant type.</span></span>

<span data-ttu-id="384c1-672">Při vývoji součástí byste měli vždy `CLSCompliantAttribute` použít atribut k označení, zda vaše sestavení, jeho typy a jeho členy jsou kompatibilní se seznamem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-672">When you are developing components, you should always use the `CLSCompliantAttribute` attribute to indicate whether your assembly, its types, and its members are CLS-compliant.</span></span>

<span data-ttu-id="384c1-673">Vytvoření součástí kompatibilních se standardem CLS:</span><span class="sxs-lookup"><span data-stu-id="384c1-673">To create CLS-compliant components:</span></span>

1. <span data-ttu-id="384c1-674">Použijte `CLSCompliantAttribute` k označení sestavení jako kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-674">Use the `CLSCompliantAttribute` to mark you assembly as CLS-compliant.</span></span>

2. <span data-ttu-id="384c1-675">Označte všechny veřejně exponované typy v sestavení, které nejsou kompatibilní se standardem CLS jako nekompatibilní.</span><span class="sxs-lookup"><span data-stu-id="384c1-675">Mark any publicly exposed types in the assembly that are not CLS-compliant as non-compliant.</span></span>

3. <span data-ttu-id="384c1-676">Označte všechny veřejně exponované členy v typech kompatibilních se standardem CLS jako nekompatibilní.</span><span class="sxs-lookup"><span data-stu-id="384c1-676">Mark any publicly exposed members in CLS-compliant types as non-compliant.</span></span>

4. <span data-ttu-id="384c1-677">Poskytněte alternativu kompatibilní se standardem CLS pro členy, kteří nejsou kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-677">Provide a CLS-compliant alternative for non-CLS-compliant members.</span></span>

<span data-ttu-id="384c1-678">Pokud jste úspěšně označili všechny nekompatibilní typy a členy, kompilátor by neměl vyzařovat žádná upozornění na nedodržování předpisů.</span><span class="sxs-lookup"><span data-stu-id="384c1-678">If you've successfully marked all your non-compliant types and members, your compiler should not emit any non-compliance warnings.</span></span> <span data-ttu-id="384c1-679">Měli byste však určit, které členy nejsou kompatibilní se standardem CLS, a v dokumentaci k produktu uvést jejich alternativy kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-679">However, you should indicate which members are not CLS-compliant and list their CLS-compliant alternatives in your product documentation.</span></span>

<span data-ttu-id="384c1-680">Následující příklad používá `CLSCompliantAttribute` atribut k definování sestavení kompatibilního se `CharacterUtilities`seznamem CLS a typu , který má dva členy, které nesplňují požadavky cls.</span><span class="sxs-lookup"><span data-stu-id="384c1-680">The following example uses the `CLSCompliantAttribute` attribute to define a CLS-compliant assembly and a type, `CharacterUtilities`, that has two non-CLS-compliant members.</span></span> <span data-ttu-id="384c1-681">Vzhledem k tomu, `CLSCompliant(false)` že oba členy jsou označeny atributem, kompilátor nevytváří žádná upozornění.</span><span class="sxs-lookup"><span data-stu-id="384c1-681">Because both members are tagged with the `CLSCompliant(false)` attribute, the compiler produces no warnings.</span></span> <span data-ttu-id="384c1-682">Třída také poskytuje alternativu kompatibilní se standardem CLS pro obě metody.</span><span class="sxs-lookup"><span data-stu-id="384c1-682">The class also provides a CLS-compliant alternative for both methods.</span></span> <span data-ttu-id="384c1-683">Obvykle bychom jen přidat dvě přetížení `ToUTF16` metody poskytnout alternativy kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-683">Ordinarily, we would just add two overloads to the `ToUTF16` method to provide CLS-compliant alternatives.</span></span> <span data-ttu-id="384c1-684">Protože však metody nemohou být přetíženy na základě vrácené hodnoty, názvy metod kompatibilních se standardem CLS se liší od názvů nekompatibilních metod.</span><span class="sxs-lookup"><span data-stu-id="384c1-684">However, because methods cannot be overloaded based on return value, the names of the CLS-compliant methods are different from the names of the non-compliant methods.</span></span>

```csharp
using System;
using System.Text;

[assembly:CLSCompliant(true)]

public class CharacterUtilities
{
   [CLSCompliant(false)] public static ushort ToUTF16(String s)
   {
      s = s.Normalize(NormalizationForm.FormC);
      return Convert.ToUInt16(s[0]);
   }

   [CLSCompliant(false)] public static ushort ToUTF16(Char ch)
   {
      return Convert.ToUInt16(ch);
   }

   // CLS-compliant alternative for ToUTF16(String).
   public static int ToUTF16CodeUnit(String s)
   {
      s = s.Normalize(NormalizationForm.FormC);
      return (int) Convert.ToUInt16(s[0]);
   }

   // CLS-compliant alternative for ToUTF16(Char).
   public static int ToUTF16CodeUnit(Char ch)
   {
      return Convert.ToInt32(ch);
   }

   public bool HasMultipleRepresentations(String s)
   {
      String s1 = s.Normalize(NormalizationForm.FormC);
      return s.Equals(s1);
   }

   public int GetUnicodeCodePoint(Char ch)
   {
      if (Char.IsSurrogate(ch))
         throw new ArgumentException("ch cannot be a high or low surrogate.");

      return Char.ConvertToUtf32(ch.ToString(), 0);
   }

   public int GetUnicodeCodePoint(Char[] chars)
   {
      if (chars.Length > 2)
         throw new ArgumentException("The array has too many characters.");

      if (chars.Length == 2) {
         if (! Char.IsSurrogatePair(chars[0], chars[1]))
            throw new ArgumentException("The array must contain a low and a high surrogate.");
         else
            return Char.ConvertToUtf32(chars[0], chars[1]);
      }
      else {
         return Char.ConvertToUtf32(chars.ToString(), 0);
      }
   }
}
```

```vb
Imports System.Text

<Assembly:CLSCompliant(True)>

Public Class CharacterUtilities
   <CLSCompliant(False)> Public Shared Function ToUTF16(s As String) As UShort
      s = s.Normalize(NormalizationForm.FormC)
      Return Convert.ToUInt16(s(0))
   End Function

   <CLSCompliant(False)> Public Shared Function ToUTF16(ch As Char) As UShort
      Return Convert.ToUInt16(ch)
   End Function

   ' CLS-compliant alternative for ToUTF16(String).
   Public Shared Function ToUTF16CodeUnit(s As String) As Integer
      s = s.Normalize(NormalizationForm.FormC)
      Return CInt(Convert.ToInt16(s(0)))
   End Function

   ' CLS-compliant alternative for ToUTF16(Char).
   Public Shared Function ToUTF16CodeUnit(ch As Char) As Integer
      Return Convert.ToInt32(ch)
   End Function

   Public Function HasMultipleRepresentations(s As String) As Boolean
      Dim s1 As String = s.Normalize(NormalizationForm.FormC)
      Return s.Equals(s1)
   End Function

   Public Function GetUnicodeCodePoint(ch As Char) As Integer
      If Char.IsSurrogate(ch) Then
         Throw New ArgumentException("ch cannot be a high or low surrogate.")
      End If
      Return Char.ConvertToUtf32(ch.ToString(), 0)
   End Function

   Public Function GetUnicodeCodePoint(chars() As Char) As Integer
      If chars.Length > 2 Then
         Throw New ArgumentException("The array has too many characters.")
      End If
      If chars.Length = 2 Then
         If Not Char.IsSurrogatePair(chars(0), chars(1)) Then
            Throw New ArgumentException("The array must contain a low and a high surrogate.")
         Else
            Return Char.ConvertToUtf32(chars(0), chars(1))
         End If
      Else
         Return Char.ConvertToUtf32(chars.ToString(), 0)
      End If
   End Function
End Class
```

<span data-ttu-id="384c1-685">Pokud vyvíjíte aplikaci, nikoli knihovnu (to znamená, že nevystavujete typy nebo členy, které mohou využívat jiní vývojáři aplikací), dodržování předpisů CLS pro prvky programu, které vaše aplikace využívá, je zajímavé pouze v případě, že je váš jazyk nepodporuje .</span><span class="sxs-lookup"><span data-stu-id="384c1-685">If you are developing an app rather than a library (that is, if you aren't exposing types or members that can be consumed by other app developers), the CLS compliance of the program elements that your app consumes are of interest only if your language does not support them.</span></span> <span data-ttu-id="384c1-686">V takovém případě kompilátor jazyka vygeneruje chybu při pokusu o použití prvku, který není kompatibilní se standardem CLS.</span><span class="sxs-lookup"><span data-stu-id="384c1-686">In that case, your language compiler will generate an error when you try to use a non-CLS-compliant element.</span></span>

## <a name="cross-language-interoperability"></a><span data-ttu-id="384c1-687">Vzájemná funkční spolupráce mezi jazyky</span><span class="sxs-lookup"><span data-stu-id="384c1-687">Cross-Language Interoperability</span></span>

<span data-ttu-id="384c1-688">Jazyková nezávislost má několik možných významů.</span><span class="sxs-lookup"><span data-stu-id="384c1-688">Language independence has a number of possible meanings.</span></span> <span data-ttu-id="384c1-689">Jeden význam zahrnuje bezproblémovou konzumaci typů napsaných v jednom jazyce z aplikace napsané v jiném jazyce.</span><span class="sxs-lookup"><span data-stu-id="384c1-689">One meaning involves seamlessly consuming types written in one language from an app written in another language.</span></span> <span data-ttu-id="384c1-690">Druhý význam, který je hlavním cílem tohoto článku, zahrnuje sloučení kódu napsaného ve více jazycích do jediného sestavení rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="384c1-690">A second meaning, which is the focus of this article, involves combining code written in multiple languages into a single .NET Framework assembly.</span></span>

<span data-ttu-id="384c1-691">Následující příklad znázorňuje interoperabilitu mezi jazyky vytvořením knihovny tříd s názvem Utilities.dll, která obsahuje dvě třídy `NumericLib` a `StringLib`.</span><span class="sxs-lookup"><span data-stu-id="384c1-691">The following example illustrates cross-language interoperability by creating a class library named Utilities.dll that includes two classes, `NumericLib` and `StringLib`.</span></span> <span data-ttu-id="384c1-692">Třída `NumericLib` je napsána v jazyce C# a třída `StringLib` je napsána v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="384c1-692">The `NumericLib` class is written in C#, and the `StringLib` class is written in Visual Basic.</span></span> <span data-ttu-id="384c1-693">Zde je zdrojový kód `StringUtil.vb`pro , který `ToTitleCase`zahrnuje jeden `StringLib` člen, , ve své třídě.</span><span class="sxs-lookup"><span data-stu-id="384c1-693">Here's the source code for `StringUtil.vb`, which includes a single member, `ToTitleCase`, in its `StringLib` class.</span></span>

```vb
Imports System.Collections.Generic
Imports System.Runtime.CompilerServices

Public Module StringLib
   Private exclusions As List(Of String)

   Sub New()
      Dim words() As String = { "a", "an", "and", "of", "the" }
      exclusions = New List(Of String)
      exclusions.AddRange(words)
   End Sub

   <Extension()> _
   Public Function ToTitleCase(title As String) As String
      Dim words() As String = title.Split()
      Dim result As String = String.Empty

      For ctr As Integer = 0 To words.Length - 1
         Dim word As String = words(ctr)
         If ctr = 0 OrElse Not exclusions.Contains(word.ToLower()) Then
            result += word.Substring(0, 1).ToUpper() + _
                      word.Substring(1).ToLower()
         Else
            result += word.ToLower()
         End If
         If ctr <= words.Length - 1 Then
            result += " "
         End If
      Next
      Return result
   End Function
End Module
```

<span data-ttu-id="384c1-694">Zde je zdrojový kód pro NumberUtil.cs, který definuje třídu `NumericLib` se dvěma členy `IsEven` a `NearZero`.</span><span class="sxs-lookup"><span data-stu-id="384c1-694">Here's the source code for NumberUtil.cs, which defines a `NumericLib` class that has two members, `IsEven` and `NearZero`.</span></span>

```csharp
using System;

public static class NumericLib
{
   public static bool IsEven(this IConvertible number)
   {
      if (number is Byte ||
          number is SByte ||
          number is Int16 ||
          number is UInt16 ||
          number is Int32 ||
          number is UInt32 ||
          number is Int64)
         return ((long) number) % 2 == 0;
      else if (number is UInt64)
         return ((ulong) number) %2 == 0;
      else
         throw new NotSupportedException("IsEven called for a non-integer value.");
   }

   public static bool NearZero(double number)
   {
      return number < .00001;
   }
}
```

<span data-ttu-id="384c1-695">Chcete-li zabalit dvě třídy do jednoho sestavení, musíte je zkompilovat do modulů.</span><span class="sxs-lookup"><span data-stu-id="384c1-695">To package the two classes in a single assembly, you must compile them into modules.</span></span> <span data-ttu-id="384c1-696">Pro kompilaci zdrojového kódu jazyka Visual Basic do modulu použijte tento příkaz:</span><span class="sxs-lookup"><span data-stu-id="384c1-696">To compile the Visual Basic source code file into a module, use this command:</span></span>

```console
vbc /t:module StringUtil.vb
```

<span data-ttu-id="384c1-697">Pro kompilaci zdrojového kódu jazyka C# do modulu použijte tento příkaz:</span><span class="sxs-lookup"><span data-stu-id="384c1-697">To compile the C# source code file into a module, use this command:</span></span>

```console
csc /t:module NumberUtil.cs
```

<span data-ttu-id="384c1-698">Potom pomocí nástroje Link (Link.exe) zkompilujte dva moduly do sestavení:</span><span class="sxs-lookup"><span data-stu-id="384c1-698">You then use the Link tool (Link.exe) to compile the two modules into an assembly:</span></span>

```console
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll
```

<span data-ttu-id="384c1-699">Následující příklad následně volá metody `NumericLib.NearZero` a `StringLib.ToTitleCase`.</span><span class="sxs-lookup"><span data-stu-id="384c1-699">The following example then calls the `NumericLib.NearZero` and `StringLib.ToTitleCase` methods.</span></span> <span data-ttu-id="384c1-700">Kód jazyka Visual Basic i kód jazyka C# může přistupovat k metodám v obou třídách.</span><span class="sxs-lookup"><span data-stu-id="384c1-700">Note that both the Visual Basic code and the C# code are able to access the methods in both classes.</span></span>

```csharp
using System;

public class Example
{
   public static void Main()
   {
      Double dbl = 0.0 - Double.Epsilon;
      Console.WriteLine(NumericLib.NearZero(dbl));

      string s = "war and peace";
      Console.WriteLine(s.ToTitleCase());
   }
}
// The example displays the following output:
//       True
//       War and Peace
```

```vb
Module Example
   Public Sub Main()
      Dim dbl As Double = 0.0 - Double.Epsilon
      Console.WriteLine(NumericLib.NearZero(dbl))

      Dim s As String = "war and peace"
      Console.WriteLine(s.ToTitleCase())
   End Sub
End Module
' The example displays the following output:
'       True
'       War and Peace
```

<span data-ttu-id="384c1-701">Pro kompilaci kódu jazyka Visual Basic použijte tento příkaz:</span><span class="sxs-lookup"><span data-stu-id="384c1-701">To compile the Visual Basic code, use this command:</span></span>

```console
vbc example.vb /r:UtilityLib.dll
```

<span data-ttu-id="384c1-702">Chcete-li zkompilovat pomocí jazyka C#, změňte název kompilátoru z vbc na csc a změňte příponu souboru z .vb na .cs:</span><span class="sxs-lookup"><span data-stu-id="384c1-702">To compile with C#, change the name of the compiler from vbc to csc, and change the file extension from .vb to .cs:</span></span>

```console
csc example.cs /r:UtilityLib.dll
```
