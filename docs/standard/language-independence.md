---
title: Jazyková nezávislost a jazykově nezávislé komponenty
description: 'Přečtěte si, jak můžete vyvíjet v jednom z mnoha podporovaných jazyků v .NET, jako je C#, C++/CLI, F #, Ironpythonu, VB, Visual COBOL a PowerShell.'
ms.date: 07/22/2016
dev_langs:
- csharp
- vb
ms.technology: dotnet-standard
ms.assetid: 2dbed1bc-86f5-43cd-9a57-adbb1c5efba4
ms.openlocfilehash: f04ff902743c91147a6f056bca3292ee47952bbd
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420549"
---
# <a name="language-independence-and-language-independent-components"></a><span data-ttu-id="1f6b7-103">Jazyková nezávislost a jazykově nezávislé komponenty</span><span class="sxs-lookup"><span data-stu-id="1f6b7-103">Language independence and language-independent components</span></span>

<span data-ttu-id="1f6b7-104">Rozhraní .NET je nezávislé na jazyce.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-104">.NET is language independent.</span></span> <span data-ttu-id="1f6b7-105">To znamená, že jako vývojář můžete vyvíjet v jednom z mnoha jazyků, které cílí na implementace technologie .NET, jako je C#, F # a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-105">This means that, as a developer, you can develop in one of the many languages that target .NET implementations, such as C#, F#, and Visual Basic.</span></span> <span data-ttu-id="1f6b7-106">Můžete přistupovat k typům a členům knihoven tříd vyvinutým pro implementace v rozhraní .NET bez nutnosti znát jazyk, ve kterém byly původně zapsány, a aniž byste museli sledovat některé z původních konvencí jazyka.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-106">You can access the types and members of class libraries developed for .NET implementations without having to know the language in which they were originally written and without having to follow any of the original language's conventions.</span></span> <span data-ttu-id="1f6b7-107">Pokud jste vývojář komponent, k vaší komponentě se dá dostat z aplikace .NET bez ohledu na její jazyk.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-107">If you are a component developer, your component can be accessed by any .NET app regardless of its language.</span></span>

> [!NOTE]
> <span data-ttu-id="1f6b7-108">Tato první část tohoto článku popisuje vytváření komponent nezávislých na jazyce – to znamená komponenty, které mohou být spotřebovány aplikacemi, které jsou napsané v libovolném jazyce.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-108">This first part of this article discusses creating language-independent components - that is, components that can be consumed by apps that are written in any language.</span></span> <span data-ttu-id="1f6b7-109">Můžete také vytvořit jednu komponentu nebo aplikaci ze zdrojového kódu napsaného v několika jazycích. viz [interoperabilita mezi jazyky](#cross-language-interoperability) v druhé části tohoto článku.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-109">You can also create a single component or app from source code written in multiple languages; see [Cross-Language Interoperability](#cross-language-interoperability) in the second part of this article.</span></span>

<span data-ttu-id="1f6b7-110">Aby bylo možné plně spolupracovat s jinými objekty napsanými v libovolném jazyce, musí tyto objekty zveřejnit volajícím pouze ty funkce, které jsou společné pro všechny jazyky.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-110">To fully interact with other objects written in any language, objects must expose to callers only those features that are common to all languages.</span></span> <span data-ttu-id="1f6b7-111">Tato společná sada funkcí je definována specifikací CLS (Common Language Specification), což je sada pravidel, která se vztahují na generovaná sestavení.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-111">This common set of features is defined by the Common Language Specification (CLS), which is a set of rules that apply to generated assemblies.</span></span> <span data-ttu-id="1f6b7-112">Specifikace CLS (Common Language Specification) je definována v oddílu I klauzule 7 až 11 ze [standardu ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="1f6b7-112">The Common Language Specification is defined in Partition I, Clauses 7 through 11 of the [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>

<span data-ttu-id="1f6b7-113">Pokud vaše komponenta odpovídá specifikaci CLS (Common Language Specification), je zaručena, že je kompatibilní se specifikací CLS a je možné k nim přicházet z kódu v sestaveních napsaných v jakémkoli programovacím jazyce, který podporuje specifikaci CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-113">If your component conforms to the Common Language Specification, it is guaranteed to be CLS-compliant and can be accessed from code in assemblies written in any programming language that supports the CLS.</span></span> <span data-ttu-id="1f6b7-114">Můžete určit, zda vaše komponenta odpovídá specifikaci CLS (Common Language Specification) v době kompilace, a to použitím atributu [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) pro váš zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-114">You can determine whether your component conforms to the Common Language Specification at compile time by applying the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute to your source code.</span></span> <span data-ttu-id="1f6b7-115">Další informace najdete v [atributu CLSCompliantAttribute](#the-clscompliantattribute-attribute).</span><span class="sxs-lookup"><span data-stu-id="1f6b7-115">For more information, see The [CLSCompliantAttribute attribute](#the-clscompliantattribute-attribute).</span></span>

<span data-ttu-id="1f6b7-116">V tomto článku:</span><span class="sxs-lookup"><span data-stu-id="1f6b7-116">In this article:</span></span>

* [<span data-ttu-id="1f6b7-117">Pravidla dodržování předpisů CLS</span><span class="sxs-lookup"><span data-stu-id="1f6b7-117">CLS compliance rules</span></span>](#cls-compliance-rules)

  * [<span data-ttu-id="1f6b7-118">Typy a signatury členů typu</span><span class="sxs-lookup"><span data-stu-id="1f6b7-118">Types and type member signatures</span></span>](#types-and-type-member-signatures)

  * [<span data-ttu-id="1f6b7-119">Zásady vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="1f6b7-119">Naming conventions</span></span>](#naming-conventions)

  * [<span data-ttu-id="1f6b7-120">Převod typů</span><span class="sxs-lookup"><span data-stu-id="1f6b7-120">Type conversion</span></span>](#type-conversion)

  * [<span data-ttu-id="1f6b7-121">Pole</span><span class="sxs-lookup"><span data-stu-id="1f6b7-121">Arrays</span></span>](#arrays)

  * [<span data-ttu-id="1f6b7-122">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="1f6b7-122">Interfaces</span></span>](#interfaces)

  * [<span data-ttu-id="1f6b7-123">Výčty</span><span class="sxs-lookup"><span data-stu-id="1f6b7-123">Enumerations</span></span>](#enumerations)

  * [<span data-ttu-id="1f6b7-124">Obecné typy členů</span><span class="sxs-lookup"><span data-stu-id="1f6b7-124">Type members in general</span></span>](#type-members-in-general)

  * [<span data-ttu-id="1f6b7-125">Přístupnost člena</span><span class="sxs-lookup"><span data-stu-id="1f6b7-125">Member accessibility</span></span>](#member-accessibility)

  * [<span data-ttu-id="1f6b7-126">Obecné typy a členy</span><span class="sxs-lookup"><span data-stu-id="1f6b7-126">Generic types and members</span></span>](#generic-types-and-members)

  * [<span data-ttu-id="1f6b7-127">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="1f6b7-127">Constructors</span></span>](#constructors)

  * [<span data-ttu-id="1f6b7-128">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1f6b7-128">Properties</span></span>](#properties)

  * [<span data-ttu-id="1f6b7-129">Události</span><span class="sxs-lookup"><span data-stu-id="1f6b7-129">Events</span></span>](#events)

  * [<span data-ttu-id="1f6b7-130">Přetížení</span><span class="sxs-lookup"><span data-stu-id="1f6b7-130">Overloads</span></span>](#overloads)

  * [<span data-ttu-id="1f6b7-131">Výjimky</span><span class="sxs-lookup"><span data-stu-id="1f6b7-131">Exceptions</span></span>](#exceptions)

  * [<span data-ttu-id="1f6b7-132">Atributy</span><span class="sxs-lookup"><span data-stu-id="1f6b7-132">Attributes</span></span>](#attributes)

* [<span data-ttu-id="1f6b7-133">CLSCompliantAttribute – atribut</span><span class="sxs-lookup"><span data-stu-id="1f6b7-133">CLSCompliantAttribute attribute</span></span>](#the-clscompliantattribute-attribute)

* [<span data-ttu-id="1f6b7-134">Vzájemná funkční spolupráce mezi jazyky</span><span class="sxs-lookup"><span data-stu-id="1f6b7-134">Cross-Language Interoperability</span></span>](#cross-language-interoperability)

## <a name="cls-compliance-rules"></a><span data-ttu-id="1f6b7-135">Pravidla dodržování předpisů CLS</span><span class="sxs-lookup"><span data-stu-id="1f6b7-135">CLS compliance rules</span></span>

<span data-ttu-id="1f6b7-136">Tato část popisuje pravidla pro vytvoření komponenty kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-136">This section discusses the rules for creating a CLS-compliant component.</span></span> <span data-ttu-id="1f6b7-137">Úplný seznam pravidel naleznete v oddílu I klauzule 11 ve [standardu ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="1f6b7-137">For a complete list of rules, see Partition I, Clause 11 of the [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>

> [!NOTE]
> <span data-ttu-id="1f6b7-138">Specifikace CLS (Common Language Specification) se zabývá všemi pravidly dodržování specifikace CLS, protože se vztahuje na příjemce (vývojáři, kteří mají programově přístup k komponentě kompatibilní se specifikací CLS), architektury (vývojáři, kteří používají kompilátor jazyka k vytváření knihoven kompatibilních se specifikací CLS) a zařízení (vývojáři, kteří vytvářejí nástroj, jako je kompilátor jazyka nebo analyzátor kódu, který vytváří komponenty kompatibilní se specifikací CLS).</span><span class="sxs-lookup"><span data-stu-id="1f6b7-138">The Common Language Specification discusses each rule for CLS compliance as it applies to consumers (developers who are programmatically accessing a component that is CLS-compliant), frameworks (developers who are using a language compiler to create CLS-compliant libraries), and extenders (developers who are creating a tool such as a language compiler or a code parser that creates CLS-compliant components).</span></span> <span data-ttu-id="1f6b7-139">Tento článek se zaměřuje na pravidla, která se vztahují na rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-139">This article focuses on the rules as they apply to frameworks.</span></span> <span data-ttu-id="1f6b7-140">Všimněte si ale, že některá pravidla, která platí pro rozšířené, mohou platit také pro sestavení, která jsou vytvořena pomocí [reflexe. Emit](xref:System.Reflection.Emit).</span><span class="sxs-lookup"><span data-stu-id="1f6b7-140">Note, though, that some of the rules that apply to extenders may also apply to assemblies that are created using [Reflection.Emit](xref:System.Reflection.Emit).</span></span>

<span data-ttu-id="1f6b7-141">Chcete-li navrhnout komponentu, která je nezávislá na jazyce, stačí použít pravidla pro dodržování specifikace CLS pro veřejné rozhraní vaší komponenty.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-141">To design a component that is language independent, you only need to apply the rules for CLS compliance to your component's public interface.</span></span> <span data-ttu-id="1f6b7-142">Vaše soukromá implementace nemusí odpovídat specifikaci.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-142">Your private implementation does not have to conform to the specification.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1f6b7-143">Pravidla pro dodržování předpisů CLS platí pouze pro veřejné rozhraní komponenty, nikoli na jeho soukromou implementaci.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-143">The rules for CLS compliance apply only to a component's public interface, not to its private implementation.</span></span>

<span data-ttu-id="1f6b7-144">Například celá čísla bez znaménka jiná než [bajt](xref:System.Byte) nejsou kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-144">For example, unsigned integers other than [Byte](xref:System.Byte) are not CLS-compliant.</span></span> <span data-ttu-id="1f6b7-145">Vzhledem k tomu `Person` , že třída v následujícím příkladu zpřístupňuje `Age` vlastnost typu [UInt16](xref:System.UInt16), následující kód zobrazí upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-145">Because the `Person` class in the following example exposes an `Age` property of type [UInt16](xref:System.UInt16), the following code displays a compiler warning.</span></span>

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

<span data-ttu-id="1f6b7-146">Třídu person kompatibilní se specifikací CLS můžete nastavit tak, že změníte typ `Age` vlastnosti z `UInt16` na [Int16](xref:System.Int16), což je 16bitové podepsané celé číslo kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-146">You can make the Person class CLS-compliant by changing the type of `Age` property from `UInt16` to [Int16](xref:System.Int16), which is a CLS-compliant, 16-bit signed integer.</span></span> <span data-ttu-id="1f6b7-147">Nemusíte měnit typ soukromého `personAge` pole.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-147">You do not have to change the type of the private `personAge` field.</span></span>

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

<span data-ttu-id="1f6b7-148">Veřejné rozhraní knihovny se skládá z následujících:</span><span class="sxs-lookup"><span data-stu-id="1f6b7-148">A library's public interface consists of the following:</span></span>

* <span data-ttu-id="1f6b7-149">Definice veřejných tříd.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-149">Definitions of public classes.</span></span>

* <span data-ttu-id="1f6b7-150">Definice veřejných členů veřejných tříd a definice členů přístupných k odvozeným třídám (tj. chráněným členům).</span><span class="sxs-lookup"><span data-stu-id="1f6b7-150">Definitions of the public members of public classes, and definitions of members accessible to derived classes (that is, protected members).</span></span>

* <span data-ttu-id="1f6b7-151">Parametry a návratové typy veřejných tříd a parametry a návratové typy metod, které jsou přístupné pro odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-151">Parameters and return types of public methods of public classes, and parameters and return types of methods accessible to derived classes.</span></span>

<span data-ttu-id="1f6b7-152">Pravidla pro dodržování specifikace CLS jsou uvedená v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-152">The rules for CLS compliance are listed in the following table.</span></span> <span data-ttu-id="1f6b7-153">Text pravidel se bere v platnost od [standardu ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm), což je Copyright 2012 podle Ecma International.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-153">The text of the rules is taken verbatim from the [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm), which is Copyright 2012 by Ecma International.</span></span> <span data-ttu-id="1f6b7-154">Podrobnější informace o těchto pravidlech najdete v následujících oddílech.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-154">More detailed information about these rules is found in the following sections.</span></span>

<span data-ttu-id="1f6b7-155">Kategorie</span><span class="sxs-lookup"><span data-stu-id="1f6b7-155">Category</span></span> | <span data-ttu-id="1f6b7-156">Seznamte se s </span><span class="sxs-lookup"><span data-stu-id="1f6b7-156">See</span></span> | <span data-ttu-id="1f6b7-157">Pravidlo</span><span class="sxs-lookup"><span data-stu-id="1f6b7-157">Rule</span></span> | <span data-ttu-id="1f6b7-158">Číslo pravidla</span><span class="sxs-lookup"><span data-stu-id="1f6b7-158">Rule Number</span></span>
-------- | --- | ---- | -----------
<span data-ttu-id="1f6b7-159">Přístupnost</span><span class="sxs-lookup"><span data-stu-id="1f6b7-159">Accessibility</span></span> | [<span data-ttu-id="1f6b7-160">Přístupnost člena</span><span class="sxs-lookup"><span data-stu-id="1f6b7-160">Member accessibility</span></span>](#member-accessibility) | <span data-ttu-id="1f6b7-161">Při přepisu zděděných metod se přístupnost nemění, s výjimkou přepsání metody zděděné z jiného sestavení s přístupností `family-or-assembly` .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-161">Accessibility shall not be changed when overriding inherited methods, except when overriding a method inherited from a different assembly with accessibility `family-or-assembly`.</span></span> <span data-ttu-id="1f6b7-162">V takovém případě má přepsání přístup `family` .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-162">In this case, the override shall have accessibility `family`.</span></span> | <span data-ttu-id="1f6b7-163">10</span><span class="sxs-lookup"><span data-stu-id="1f6b7-163">10</span></span>
<span data-ttu-id="1f6b7-164">Přístupnost</span><span class="sxs-lookup"><span data-stu-id="1f6b7-164">Accessibility</span></span> | [<span data-ttu-id="1f6b7-165">Přístupnost člena</span><span class="sxs-lookup"><span data-stu-id="1f6b7-165">Member accessibility</span></span>](#member-accessibility) | <span data-ttu-id="1f6b7-166">Viditelnost a přístupnost typů a členů musí být takové, aby typy v signatuře kteréhokoli člena byly viditelné a přístupné, kdykoli je samotný člen viditelný a přístupný.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-166">The visibility and accessibility of types and members shall be such that types in the signature of any member shall be visible and accessible whenever the member itself is visible and accessible.</span></span> <span data-ttu-id="1f6b7-167">Například veřejná metoda, která je viditelná vně sestavení, nesmí obsahovat argument, jehož typ je viditelný pouze v rámci sestavení.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-167">For example, a public method that is visible outside its assembly shall not have an argument whose type is visible only within the assembly.</span></span> <span data-ttu-id="1f6b7-168">Viditelnost a přístupnost typů tvořících instanci obecného typu používaného v podpisu každého člena musí být viditelná a přístupná, kdykoli je samotný člen viditelný a přístupný.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-168">The visibility and accessibility of types composing an instantiated generic type used in the signature of any member shall be visible and accessible whenever the member itself is visible and accessible.</span></span> <span data-ttu-id="1f6b7-169">Například instance obecného typu přítomná v signatuře člena, který je viditelný mimo jeho sestavení, nesmí mít obecný argument, jehož typ je viditelný pouze v rámci sestavení.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-169">For example, an instantiated generic type present in the signature of a member that is visible outside its assembly shall not have a generic argument whose type is visible only within the assembly.</span></span> | <span data-ttu-id="1f6b7-170">12</span><span class="sxs-lookup"><span data-stu-id="1f6b7-170">12</span></span>
<span data-ttu-id="1f6b7-171">Pole</span><span class="sxs-lookup"><span data-stu-id="1f6b7-171">Arrays</span></span> | [<span data-ttu-id="1f6b7-172">Pole</span><span class="sxs-lookup"><span data-stu-id="1f6b7-172">Arrays</span></span>](#arrays) | <span data-ttu-id="1f6b7-173">Pole musí mít prvky s typem odpovídajícím specifikaci CLS a všechny dimenze pole musí mít nižší meze nula.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-173">Arrays shall have elements with a CLS-compliant type, and all dimensions of the array shall have lower bounds of zero.</span></span> <span data-ttu-id="1f6b7-174">Pouze skutečnost, že položka je pole a typ elementu pole musí být požadován pro rozlišení mezi přetíženími.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-174">Only the fact that an item is an array and the element type of the array shall be required to distinguish between overloads.</span></span> <span data-ttu-id="1f6b7-175">Pokud je přetížení založeno na dvou nebo více typech pole, musí být typy prvků pojmenované typy.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-175">When overloading is based on two or more array types the element types shall be named types.</span></span> | <span data-ttu-id="1f6b7-176">16</span><span class="sxs-lookup"><span data-stu-id="1f6b7-176">16</span></span>
<span data-ttu-id="1f6b7-177">Atributy</span><span class="sxs-lookup"><span data-stu-id="1f6b7-177">Attributes</span></span> | [<span data-ttu-id="1f6b7-178">Atributy</span><span class="sxs-lookup"><span data-stu-id="1f6b7-178">Attributes</span></span>](#attributes) | <span data-ttu-id="1f6b7-179">Atributy musí být typu [System. Attribute](xref:System.Attribute)nebo typu, který z něj dědí.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-179">Attributes shall be of type [System.Attribute](xref:System.Attribute), or a type inheriting from it.</span></span> | <span data-ttu-id="1f6b7-180">41</span><span class="sxs-lookup"><span data-stu-id="1f6b7-180">41</span></span>
<span data-ttu-id="1f6b7-181">Atributy</span><span class="sxs-lookup"><span data-stu-id="1f6b7-181">Attributes</span></span> | [<span data-ttu-id="1f6b7-182">Atributy</span><span class="sxs-lookup"><span data-stu-id="1f6b7-182">Attributes</span></span>](#attributes) | <span data-ttu-id="1f6b7-183">Specifikace CLS umožňuje pouze podmnožinu kódování pro vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-183">The CLS only allows a subset of the encodings of custom attributes.</span></span> <span data-ttu-id="1f6b7-184">Jediné typy, které se zobrazí v těchto kódováních, jsou (viz oddíl IV) [: System. Type](xref:System.Type), [System. String](xref:System.String), [System. Char](xref:System.Char), [System. Boolean](xref:System.Boolean), System. [Byte](xref:System.Byte), System. [Int16](xref:System.Int16), System [. Int32](xref:System.Int32), System [. Int64](xref:System.Int64), System. [Single](xref:System.Single), [System. Double](xref:System.Double)a jakýkoli typ výčtu založený na typu základního typu Integer kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-184">The only types that shall appear in these encodings are (see Partition IV): [System.Type](xref:System.Type), [System.String](xref:System.String), [System.Char](xref:System.Char), [System.Boolean](xref:System.Boolean), [System.Byte](xref:System.Byte), [System.Int16](xref:System.Int16), [System.Int32](xref:System.Int32), [System.Int64](xref:System.Int64), [System.Single](xref:System.Single), [System.Double](xref:System.Double), and any enumeration type based on a CLS-compliant base integer type.</span></span> | <span data-ttu-id="1f6b7-185">34</span><span class="sxs-lookup"><span data-stu-id="1f6b7-185">34</span></span>
<span data-ttu-id="1f6b7-186">Atributy</span><span class="sxs-lookup"><span data-stu-id="1f6b7-186">Attributes</span></span> | [<span data-ttu-id="1f6b7-187">Atributy</span><span class="sxs-lookup"><span data-stu-id="1f6b7-187">Attributes</span></span>](#attributes) | <span data-ttu-id="1f6b7-188">Specifikace CLS neumožňuje veřejně viditelné požadované modifikátory ( `modreq` , viz oddíl II), ale umožňuje volitelné modifikátory ( `modopt` , viz oddíl II), které nerozumí.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-188">The CLS does not allow publicly visible required modifiers (`modreq`, see Partition II), but does allow optional modifiers (`modopt`, see Partition II) it does not understand.</span></span> | <span data-ttu-id="1f6b7-189">35</span><span class="sxs-lookup"><span data-stu-id="1f6b7-189">35</span></span>
<span data-ttu-id="1f6b7-190">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="1f6b7-190">Constructors</span></span> | [<span data-ttu-id="1f6b7-191">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="1f6b7-191">Constructors</span></span>](#constructors) | <span data-ttu-id="1f6b7-192">Konstruktor objektu musí volat konstruktor instance své základní třídy před jakýmkoli přístupem k zděděným datům instance.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-192">An object constructor shall call some instance constructor of its base class before any access occurs to inherited instance data.</span></span> <span data-ttu-id="1f6b7-193">(To se nevztahuje na typy hodnot, které nemusí mít konstruktory.)</span><span class="sxs-lookup"><span data-stu-id="1f6b7-193">(This does not apply to value types, which need not have constructors.)</span></span>  | <span data-ttu-id="1f6b7-194">21</span><span class="sxs-lookup"><span data-stu-id="1f6b7-194">21</span></span>
<span data-ttu-id="1f6b7-195">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="1f6b7-195">Constructors</span></span> | [<span data-ttu-id="1f6b7-196">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="1f6b7-196">Constructors</span></span>](#constructors) | <span data-ttu-id="1f6b7-197">Konstruktor objektu se nesmí volat kromě v rámci vytváření objektu a objekt se nemůže inicializovat dvakrát.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-197">An object constructor shall not be called except as part of the creation of an object, and an object shall not be initialized twice.</span></span> | <span data-ttu-id="1f6b7-198">22</span><span class="sxs-lookup"><span data-stu-id="1f6b7-198">22</span></span>
<span data-ttu-id="1f6b7-199">Výčty</span><span class="sxs-lookup"><span data-stu-id="1f6b7-199">Enumerations</span></span> | [<span data-ttu-id="1f6b7-200">Výčty</span><span class="sxs-lookup"><span data-stu-id="1f6b7-200">Enumerations</span></span>](#enumerations) | <span data-ttu-id="1f6b7-201">Nadřazený typ výčtu musí být vestavěný celočíselný typ CLS, název pole musí být "value__" a toto pole musí být označeno `RTSpecialName` .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-201">The underlying type of an enum shall be a built-in CLS integer type, the name of the field shall be "value__", and that field shall be marked `RTSpecialName`.</span></span> |  <span data-ttu-id="1f6b7-202">7</span><span class="sxs-lookup"><span data-stu-id="1f6b7-202">7</span></span>
<span data-ttu-id="1f6b7-203">Výčty</span><span class="sxs-lookup"><span data-stu-id="1f6b7-203">Enumerations</span></span> | [<span data-ttu-id="1f6b7-204">Výčty</span><span class="sxs-lookup"><span data-stu-id="1f6b7-204">Enumerations</span></span>](#enumerations) | <span data-ttu-id="1f6b7-205">Existují dva různé druhy výčtů, které jsou označeny přítomností nebo nepřítomností [System. FlagsAttribute](xref:System.FlagsAttribute) (viz oddíl IV Library) vlastní atribut.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-205">There are two distinct kinds of enums, indicated by the presence or absence of the [System.FlagsAttribute](xref:System.FlagsAttribute) (see Partition IV Library) custom attribute.</span></span> <span data-ttu-id="1f6b7-206">Jedna představuje pojmenované celočíselné hodnoty; druhý představuje pojmenované bitové příznaky, které lze kombinovat pro vygenerování nepojmenované hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-206">One represents named integer values; the other represents named bit flags that can be combined to generate an unnamed value.</span></span> <span data-ttu-id="1f6b7-207">Hodnota `enum` není omezena na zadané hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-207">The value of an `enum` is not limited to the specified values.</span></span> |  <span data-ttu-id="1f6b7-208">8</span><span class="sxs-lookup"><span data-stu-id="1f6b7-208">8</span></span>
<span data-ttu-id="1f6b7-209">Výčty</span><span class="sxs-lookup"><span data-stu-id="1f6b7-209">Enumerations</span></span> | [<span data-ttu-id="1f6b7-210">Výčty</span><span class="sxs-lookup"><span data-stu-id="1f6b7-210">Enumerations</span></span>](#enumerations) | <span data-ttu-id="1f6b7-211">Literální statická pole výčtového typu musí mít typ samotného výčtu.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-211">Literal static fields of an enum shall have the type of the enum itself.</span></span> |  <span data-ttu-id="1f6b7-212">9</span><span class="sxs-lookup"><span data-stu-id="1f6b7-212">9</span></span>
<span data-ttu-id="1f6b7-213">Události</span><span class="sxs-lookup"><span data-stu-id="1f6b7-213">Events</span></span> | [<span data-ttu-id="1f6b7-214">Události</span><span class="sxs-lookup"><span data-stu-id="1f6b7-214">Events</span></span>](#events) | <span data-ttu-id="1f6b7-215">Metody, které implementují událost, musí být označené `SpecialName` v metadatech.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-215">The methods that implement an event shall be marked `SpecialName` in the metadata.</span></span> |<span data-ttu-id="1f6b7-216">29</span><span class="sxs-lookup"><span data-stu-id="1f6b7-216">29</span></span>
<span data-ttu-id="1f6b7-217">Události</span><span class="sxs-lookup"><span data-stu-id="1f6b7-217">Events</span></span> | [<span data-ttu-id="1f6b7-218">Události</span><span class="sxs-lookup"><span data-stu-id="1f6b7-218">Events</span></span>](#events) | <span data-ttu-id="1f6b7-219">Přístupnost události a jejích přistupujících objektů se musí shodovat.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-219">The accessibility of an event and of its accessors shall be identical.</span></span> |<span data-ttu-id="1f6b7-220">30</span><span class="sxs-lookup"><span data-stu-id="1f6b7-220">30</span></span>
<span data-ttu-id="1f6b7-221">Události</span><span class="sxs-lookup"><span data-stu-id="1f6b7-221">Events</span></span> | [<span data-ttu-id="1f6b7-222">Události</span><span class="sxs-lookup"><span data-stu-id="1f6b7-222">Events</span></span>](#events) | <span data-ttu-id="1f6b7-223">`add`Metody a `remove` pro událost musí být buď přítomny, nebo chybět.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-223">The `add` and `remove` methods for an event shall both either be present or absent.</span></span> |<span data-ttu-id="1f6b7-224">31</span><span class="sxs-lookup"><span data-stu-id="1f6b7-224">31</span></span>
<span data-ttu-id="1f6b7-225">Události</span><span class="sxs-lookup"><span data-stu-id="1f6b7-225">Events</span></span> | [<span data-ttu-id="1f6b7-226">Události</span><span class="sxs-lookup"><span data-stu-id="1f6b7-226">Events</span></span>](#events) | <span data-ttu-id="1f6b7-227">`add`Metody a `remove` pro událost musí mít jeden parametr, jehož typ Určuje typ události a který musí být odvozen od typu [System. Delegate](xref:System.Delegate).</span><span class="sxs-lookup"><span data-stu-id="1f6b7-227">The `add` and `remove` methods for an event shall each take one parameter whose type defines the type of the event and that shall be derived from [System.Delegate](xref:System.Delegate).</span></span> |<span data-ttu-id="1f6b7-228">32</span><span class="sxs-lookup"><span data-stu-id="1f6b7-228">32</span></span>
<span data-ttu-id="1f6b7-229">Události</span><span class="sxs-lookup"><span data-stu-id="1f6b7-229">Events</span></span> | [<span data-ttu-id="1f6b7-230">Události</span><span class="sxs-lookup"><span data-stu-id="1f6b7-230">Events</span></span>](#events) | <span data-ttu-id="1f6b7-231">Události musí dodržovat konkrétní vzor pojmenování.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-231">Events shall adhere to a specific naming pattern.</span></span> <span data-ttu-id="1f6b7-232">Atribut Special, na který se odkazuje v pravidle CLS 29, se ignoruje v odpovídajících porovnáních názvů a musí dodržovat pravidla identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-232">The SpecialName attribute referred to in CLS rule 29 shall be ignored in appropriate name comparisons and shall adhere to identifier rules.</span></span>  |<span data-ttu-id="1f6b7-233">33</span><span class="sxs-lookup"><span data-stu-id="1f6b7-233">33</span></span>
<span data-ttu-id="1f6b7-234">Výjimky</span><span class="sxs-lookup"><span data-stu-id="1f6b7-234">Exceptions</span></span> | [<span data-ttu-id="1f6b7-235">Výjimky</span><span class="sxs-lookup"><span data-stu-id="1f6b7-235">Exceptions</span></span>](#exceptions) | <span data-ttu-id="1f6b7-236">Objekty, které jsou vyvolány, musí být typu [System. Exception](xref:System.Exception) nebo typu, který z něj dědí.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-236">Objects that are thrown shall be of type [System.Exception](xref:System.Exception) or a type inheriting from it.</span></span> <span data-ttu-id="1f6b7-237">Nicméně metody kompatibilní se specifikací CLS nejsou požadovány pro blokování šíření jiných typů výjimek.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-237">Nonetheless, CLS-compliant methods are not required to block the propagation of other types of exceptions.</span></span> | <span data-ttu-id="1f6b7-238">40</span><span class="sxs-lookup"><span data-stu-id="1f6b7-238">40</span></span>
<span data-ttu-id="1f6b7-239">Obecné</span><span class="sxs-lookup"><span data-stu-id="1f6b7-239">General</span></span> | [<span data-ttu-id="1f6b7-240">Pravidla dodržování předpisů CLS</span><span class="sxs-lookup"><span data-stu-id="1f6b7-240">CLS compliance rules</span></span>](#cls-compliance-rules) | <span data-ttu-id="1f6b7-241">Pravidla CLS se vztahují pouze na ty části typu, které jsou přístupné nebo viditelné mimo definiční sestavení.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-241">CLS rules apply only to those parts of a type that are accessible or visible outside of the defining assembly.</span></span> | <span data-ttu-id="1f6b7-242">1</span><span class="sxs-lookup"><span data-stu-id="1f6b7-242">1</span></span>
<span data-ttu-id="1f6b7-243">Obecné</span><span class="sxs-lookup"><span data-stu-id="1f6b7-243">General</span></span> | [<span data-ttu-id="1f6b7-244">Pravidla dodržování předpisů CLS</span><span class="sxs-lookup"><span data-stu-id="1f6b7-244">CLS compliance rules</span></span>](#cls-compliance-rules) | <span data-ttu-id="1f6b7-245">Členy typů, které nejsou kompatibilní se specifikací CLS, nesmí být označeny jako kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-245">Members of non-CLS compliant types shall not be marked CLS-compliant.</span></span> | <span data-ttu-id="1f6b7-246">2</span><span class="sxs-lookup"><span data-stu-id="1f6b7-246">2</span></span>
<span data-ttu-id="1f6b7-247">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="1f6b7-247">Generics</span></span> | [<span data-ttu-id="1f6b7-248">Obecné typy a členy</span><span class="sxs-lookup"><span data-stu-id="1f6b7-248">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="1f6b7-249">Vnořené typy musí mít alespoň tolik obecných parametrů jako nadřazený typ.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-249">Nested types shall have at least as many generic parameters as the enclosing type.</span></span> <span data-ttu-id="1f6b7-250">Obecné parametry ve vnořeném typu odpovídají umístění obecným parametrům v nadřazeném typu.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-250">Generic parameters in a nested type correspond by position to the generic parameters in its enclosing type.</span></span>  | <span data-ttu-id="1f6b7-251">42</span><span class="sxs-lookup"><span data-stu-id="1f6b7-251">42</span></span>
<span data-ttu-id="1f6b7-252">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="1f6b7-252">Generics</span></span> | [<span data-ttu-id="1f6b7-253">Obecné typy a členy</span><span class="sxs-lookup"><span data-stu-id="1f6b7-253">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="1f6b7-254">Název obecného typu musí kódovat počet parametrů typu deklarovaných pro nevnořený typ, nebo nově zavedený na typ, pokud je vnořený, podle pravidel definovaných výše.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-254">The name of a generic type shall encode the number of type parameters declared on the non-nested type, or newly introduced to the type if nested, according to the rules defined above.</span></span> | <span data-ttu-id="1f6b7-255">43</span><span class="sxs-lookup"><span data-stu-id="1f6b7-255">43</span></span>
<span data-ttu-id="1f6b7-256">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="1f6b7-256">Generics</span></span> | [<span data-ttu-id="1f6b7-257">Obecné typy a členy</span><span class="sxs-lookup"><span data-stu-id="1f6b7-257">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="1f6b7-258">Obecný typ musí znovu deklarovat dostatečná omezení, aby bylo zaručeno, že jakákoli omezení základního typu nebo rozhraní budou splněna omezeními obecného typu.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-258">A generic type shall redeclare sufficient constraints to guarantee that any constraints on the base type, or interfaces would be satisfied by the generic type constraints.</span></span> | <span data-ttu-id="1f6b7-259">44</span><span class="sxs-lookup"><span data-stu-id="1f6b7-259">44</span></span>
<span data-ttu-id="1f6b7-260">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="1f6b7-260">Generics</span></span> | [<span data-ttu-id="1f6b7-261">Obecné typy a členy</span><span class="sxs-lookup"><span data-stu-id="1f6b7-261">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="1f6b7-262">Typy, které se používají jako omezení u obecných parametrů, samy o nich vyhovují specifikaci CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-262">Types used as constraints on generic parameters shall themselves be CLS-compliant.</span></span> | <span data-ttu-id="1f6b7-263">45</span><span class="sxs-lookup"><span data-stu-id="1f6b7-263">45</span></span>
<span data-ttu-id="1f6b7-264">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="1f6b7-264">Generics</span></span> | [<span data-ttu-id="1f6b7-265">Obecné typy a členy</span><span class="sxs-lookup"><span data-stu-id="1f6b7-265">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="1f6b7-266">Viditelnost a přístupnost členů (včetně vnořených typů) v instanci generického typu se považují za obor pro konkrétní instanci, nikoli jako deklaraci obecného typu jako celku.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-266">The visibility and accessibility of members (including nested types) in an instantiated generic type shall be considered to be scoped to the specific instantiation rather than the generic type declaration as a whole.</span></span> <span data-ttu-id="1f6b7-267">Za předpokladu, že pravidla viditelnosti a přístupnosti pravidla CLS 12 budou nadále platit.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-267">Assuming this, the visibility and accessibility rules of CLS rule 12 still apply.</span></span> | <span data-ttu-id="1f6b7-268">46</span><span class="sxs-lookup"><span data-stu-id="1f6b7-268">46</span></span>
<span data-ttu-id="1f6b7-269">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="1f6b7-269">Generics</span></span> | [<span data-ttu-id="1f6b7-270">Obecné typy a členy</span><span class="sxs-lookup"><span data-stu-id="1f6b7-270">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="1f6b7-271">Pro každou abstraktní nebo virtuální obecnou metodu musí být použita výchozí konkrétní (neabstraktní) implementace.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-271">For each abstract or virtual generic method, there shall be a default concrete (nonabstract) implementation</span></span> | <span data-ttu-id="1f6b7-272">47</span><span class="sxs-lookup"><span data-stu-id="1f6b7-272">47</span></span>
<span data-ttu-id="1f6b7-273">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="1f6b7-273">Interfaces</span></span> | [<span data-ttu-id="1f6b7-274">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="1f6b7-274">Interfaces</span></span>](#interfaces) | <span data-ttu-id="1f6b7-275">Rozhraní kompatibilní se specifikací CLS nesmí vyžadovat definici metod nekompatibilních se specifikací CLS, aby je bylo možné implementovat.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-275">CLS-compliant interfaces shall not require the definition of non-CLS compliant methods in order to implement them.</span></span> | <span data-ttu-id="1f6b7-276">18</span><span class="sxs-lookup"><span data-stu-id="1f6b7-276">18</span></span>
<span data-ttu-id="1f6b7-277">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="1f6b7-277">Interfaces</span></span> | [<span data-ttu-id="1f6b7-278">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="1f6b7-278">Interfaces</span></span>](#interfaces) | <span data-ttu-id="1f6b7-279">Rozhraní kompatibilní se specifikací CLS nesmějí definovat statické metody ani definovat pole.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-279">CLS-compliant interfaces shall not define static methods, nor shall they define fields.</span></span> | <span data-ttu-id="1f6b7-280">19</span><span class="sxs-lookup"><span data-stu-id="1f6b7-280">19</span></span>
<span data-ttu-id="1f6b7-281">Členové</span><span class="sxs-lookup"><span data-stu-id="1f6b7-281">Members</span></span> | [<span data-ttu-id="1f6b7-282">Obecné typy členů</span><span class="sxs-lookup"><span data-stu-id="1f6b7-282">Type members in general</span></span>](#type-members-in-general) | <span data-ttu-id="1f6b7-283">Globální statická pole a metody nejsou kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-283">Global static fields and methods are not CLS-compliant.</span></span> | <span data-ttu-id="1f6b7-284">36</span><span class="sxs-lookup"><span data-stu-id="1f6b7-284">36</span></span>
<span data-ttu-id="1f6b7-285">Členové</span><span class="sxs-lookup"><span data-stu-id="1f6b7-285">Members</span></span> | -- | <span data-ttu-id="1f6b7-286">Hodnota statického literálu je určena pomocí inicializačních metadat pole.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-286">The value of a literal static is specified through the use of field initialization metadata.</span></span> <span data-ttu-id="1f6b7-287">Literál kompatibilní se specifikací CLS musí mít hodnotu zadanou v metadatech inicializace pole, která jsou přesně stejného typu jako literál (nebo základního typu, pokud je tento literál typu `enum` ).</span><span class="sxs-lookup"><span data-stu-id="1f6b7-287">A CLS-compliant literal must have a value specified in field initialization metadata that is of exactly the same type as the literal (or of the underlying type, if that literal is an `enum`).</span></span> | <span data-ttu-id="1f6b7-288">13</span><span class="sxs-lookup"><span data-stu-id="1f6b7-288">13</span></span>
<span data-ttu-id="1f6b7-289">Členové</span><span class="sxs-lookup"><span data-stu-id="1f6b7-289">Members</span></span> | [<span data-ttu-id="1f6b7-290">Obecné typy členů</span><span class="sxs-lookup"><span data-stu-id="1f6b7-290">Type members in general</span></span>](#type-members-in-general) | <span data-ttu-id="1f6b7-291">Omezení vararg není součástí specifikace CLS a jediná konvence volání podporovaná specifikací CLS je standardní spravovaná konvence volání.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-291">The vararg constraint is not part of the CLS, and the only calling convention supported by the CLS is the standard managed calling convention.</span></span> | <span data-ttu-id="1f6b7-292">15</span><span class="sxs-lookup"><span data-stu-id="1f6b7-292">15</span></span>
<span data-ttu-id="1f6b7-293">Zásady vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="1f6b7-293">Naming conventions</span></span> | [<span data-ttu-id="1f6b7-294">Zásady vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="1f6b7-294">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="1f6b7-295">Sestavení se řídí podle přílohy 7 technické sestavy 15 sady Unicode Standard 3.0, která se řídí sadou znaků povolených ke spuštění a jsou součástí identifikátorů, které jsou k dispozici online ve [formulářích normalizace Unicode](https://www.unicode.org/unicode/reports/tr15/tr15-18.html).</span><span class="sxs-lookup"><span data-stu-id="1f6b7-295">Assemblies shall follow Annex 7 of Technical Report 15 of the Unicode Standard3.0 governing the set of characters permitted to start and be included in identifiers, available online at [Unicode Normalization Forms](https://www.unicode.org/unicode/reports/tr15/tr15-18.html).</span></span> <span data-ttu-id="1f6b7-296">Identifikátory musí být v kanonickém formátu definovaném formulářem normalizace Unicode C. Pro účely specifikace CLS jsou dva identifikátory stejné, pokud mapování malých písmen (podle specifikace národního prostředí Unicode rozlišuje malá a velká písmena), jsou stejná.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-296">Identifiers shall be in the canonical format defined by Unicode Normalization Form C. For CLS purposes, two identifiers are the same if their lowercase mappings (as specified by the Unicode locale-insensitive, one-to-one lowercase mappings) are the same.</span></span> <span data-ttu-id="1f6b7-297">To znamená, že u dvou identifikátorů, které se považují za odlišné v rámci specifikace CLS, se liší ve více než pouhém případě.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-297">That is, for two identifiers to be considered different under the CLS they shall differ in more than simply their case.</span></span> <span data-ttu-id="1f6b7-298">Chcete-li však přepsat zděděnou definici, rozhraní příkazového řádku vyžaduje použití přesného kódování původní deklarace.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-298">However, in order to override an inherited definition the CLI requires the precise encoding of the original declaration be used.</span></span> | <span data-ttu-id="1f6b7-299">4</span><span class="sxs-lookup"><span data-stu-id="1f6b7-299">4</span></span>
<span data-ttu-id="1f6b7-300">Přetížení</span><span class="sxs-lookup"><span data-stu-id="1f6b7-300">Overloading</span></span> | [<span data-ttu-id="1f6b7-301">Zásady vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="1f6b7-301">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="1f6b7-302">Všechny názvy zavedené v oboru kompatibilním se specifikací CLS musí být nezávislé na druhu, s výjimkou případů, kdy jsou názvy identické a vyřešeny pomocí přetížení.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-302">All names introduced in a CLS-compliant scope shall be distinct independent of kind, except where the names are identical and resolved via overloading.</span></span> <span data-ttu-id="1f6b7-303">To znamená, že když CTS umožňuje, aby jeden typ používal stejný název pro metodu a pole, specifikace CLS ne.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-303">That is, while the CTS allows a single type to use the same name for a method and a field, the CLS does not.</span></span> | <span data-ttu-id="1f6b7-304">5</span><span class="sxs-lookup"><span data-stu-id="1f6b7-304">5</span></span>
<span data-ttu-id="1f6b7-305">Přetížení</span><span class="sxs-lookup"><span data-stu-id="1f6b7-305">Overloading</span></span> | [<span data-ttu-id="1f6b7-306">Zásady vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="1f6b7-306">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="1f6b7-307">Pole a vnořené typy se liší podle porovnání identifikátorů, i když CTS umožňuje odlišit jedinečné podpisy.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-307">Fields and nested types shall be distinct by identifier comparison alone, even though the CTS allows distinct signatures to be distinguished.</span></span> <span data-ttu-id="1f6b7-308">Metody, vlastnosti a události, které mají stejný název (podle porovnání identifikátorů), se liší o více než jenom návratovým typem, s výjimkou zadání v pravidle CLS 39.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-308">Methods, properties, and events that have the same name (by identifier comparison) shall differ by more than just the return type,except as specified in CLS Rule 39</span></span> | <span data-ttu-id="1f6b7-309">6</span><span class="sxs-lookup"><span data-stu-id="1f6b7-309">6</span></span>
<span data-ttu-id="1f6b7-310">Přetížení</span><span class="sxs-lookup"><span data-stu-id="1f6b7-310">Overloading</span></span> | [<span data-ttu-id="1f6b7-311">Přetížení</span><span class="sxs-lookup"><span data-stu-id="1f6b7-311">Overloads</span></span>](#overloads) | <span data-ttu-id="1f6b7-312">Pouze vlastnosti a metody mohou být přetíženy.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-312">Only properties and methods can be overloaded.</span></span> | <span data-ttu-id="1f6b7-313">37</span><span class="sxs-lookup"><span data-stu-id="1f6b7-313">37</span></span>
<span data-ttu-id="1f6b7-314">Přetížení</span><span class="sxs-lookup"><span data-stu-id="1f6b7-314">Overloading</span></span> | [<span data-ttu-id="1f6b7-315">Přetížení</span><span class="sxs-lookup"><span data-stu-id="1f6b7-315">Overloads</span></span>](#overloads) |<span data-ttu-id="1f6b7-316">Vlastnosti a metody mohou být přetíženy pouze v závislosti na počtu a typech jejich parametrů, s výjimkou operátorů převodu s názvem `op_Implicit` a `op_Explicit` , které mohou být také přetíženy na základě jejich návratového typu.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-316">Properties and methods can be overloaded based only on the number and types of their parameters, except the conversion operators named `op_Implicit` and `op_Explicit`, which can also be overloaded based on their return type.</span></span> | <span data-ttu-id="1f6b7-317">38</span><span class="sxs-lookup"><span data-stu-id="1f6b7-317">38</span></span>
<span data-ttu-id="1f6b7-318">Přetížení</span><span class="sxs-lookup"><span data-stu-id="1f6b7-318">Overloading</span></span> | -- | <span data-ttu-id="1f6b7-319">Pokud dva nebo více metod odpovídajících specifikaci CLS mají stejný název a pro konkrétní sadu instancí typu, mají stejný parametr a návratové typy, pak všechny tyto metody musí být sémanticky rovnocenné v těchto instancích typu.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-319">If two or more CLS-compliant methods declared in a type have the same name and, for a specific set of type instantiations, they have the same parameter and return types, then all these methods shall be semantically equivalent at those type instantiations.</span></span> | <span data-ttu-id="1f6b7-320">48</span><span class="sxs-lookup"><span data-stu-id="1f6b7-320">48</span></span>
<span data-ttu-id="1f6b7-321">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1f6b7-321">Properties</span></span> | [<span data-ttu-id="1f6b7-322">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1f6b7-322">Properties</span></span>](#properties) | <span data-ttu-id="1f6b7-323">Metody, které implementují metody getter a setter vlastnosti, musí být označeny `SpecialName` v metadatech.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-323">The methods that implement the getter and setter methods of a property shall be marked `SpecialName` in the metadata.</span></span> | <span data-ttu-id="1f6b7-324">24</span><span class="sxs-lookup"><span data-stu-id="1f6b7-324">24</span></span>
<span data-ttu-id="1f6b7-325">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1f6b7-325">Properties</span></span> | [<span data-ttu-id="1f6b7-326">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1f6b7-326">Properties</span></span>](#properties) | <span data-ttu-id="1f6b7-327">Přistupující objekty vlastnosti musí být všechny statické, všechny virtuální nebo všechny instance.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-327">A property's accessors shall all be static, all be virtual, or all be instance.</span></span> | <span data-ttu-id="1f6b7-328">26</span><span class="sxs-lookup"><span data-stu-id="1f6b7-328">26</span></span>
<span data-ttu-id="1f6b7-329">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1f6b7-329">Properties</span></span> | [<span data-ttu-id="1f6b7-330">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1f6b7-330">Properties</span></span>](#properties) | <span data-ttu-id="1f6b7-331">Typ vlastnosti musí být návratový typ getter a typ posledního argumentu setter.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-331">The type of a property shall be the return type of the getter and the type of the last argument of the setter.</span></span> <span data-ttu-id="1f6b7-332">Typy parametrů vlastnosti musí být typy parametrů pro metodu getter a typy všech, ale konečný parametr metody setter.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-332">The types of the parameters of the property shall be the types of the parameters to the getter and the types of all but the final parameter of the setter.</span></span> <span data-ttu-id="1f6b7-333">Všechny tyto typy musí být kompatibilní se specifikací CLS a nesmí být spravované ukazatele (to znamená, že se nepředávají odkazem).</span><span class="sxs-lookup"><span data-stu-id="1f6b7-333">All of these types shall be CLS-compliant, and shall not be managed pointers (that is, shall not be passed by reference).</span></span> | <span data-ttu-id="1f6b7-334">27</span><span class="sxs-lookup"><span data-stu-id="1f6b7-334">27</span></span>
<span data-ttu-id="1f6b7-335">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1f6b7-335">Properties</span></span> | [<span data-ttu-id="1f6b7-336">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1f6b7-336">Properties</span></span>](#properties) | <span data-ttu-id="1f6b7-337">Vlastnosti musí splňovat konkrétní vzor pojmenování.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-337">Properties shall adhere to a specific naming pattern.</span></span> <span data-ttu-id="1f6b7-338">`SpecialName`Atribut uvedený v pravidle CLS 24 se bude ignorovat v odpovídajících porovnáních názvů a musí splňovat pravidla identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-338">The `SpecialName` attribute referred to in CLS rule 24 shall be ignored in appropriate name comparisons and shall adhere to identifier rules.</span></span> <span data-ttu-id="1f6b7-339">Vlastnost musí mít metodu getter, metodu setter nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-339">A property shall have a getter method, a setter method, or both.</span></span> | <span data-ttu-id="1f6b7-340">28</span><span class="sxs-lookup"><span data-stu-id="1f6b7-340">28</span></span>
<span data-ttu-id="1f6b7-341">Převod typů</span><span class="sxs-lookup"><span data-stu-id="1f6b7-341">Type conversion</span></span> | [<span data-ttu-id="1f6b7-342">Převod typů</span><span class="sxs-lookup"><span data-stu-id="1f6b7-342">Type conversion</span></span>](#type-conversion) | <span data-ttu-id="1f6b7-343">Pokud je k dispozici buď op_Implicit, nebo op_Explicit, je k dispozici alternativní způsob poskytnutí tohoto vynucení.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-343">If either op_Implicit or op_Explicit is provided, an alternate means of providing the coercion shall be provided.</span></span> | <span data-ttu-id="1f6b7-344">39</span><span class="sxs-lookup"><span data-stu-id="1f6b7-344">39</span></span>
<span data-ttu-id="1f6b7-345">Typy</span><span class="sxs-lookup"><span data-stu-id="1f6b7-345">Types</span></span> | [<span data-ttu-id="1f6b7-346">Typy a signatury členů typu</span><span class="sxs-lookup"><span data-stu-id="1f6b7-346">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="1f6b7-347">Typy zabalené hodnoty nejsou kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-347">Boxed value types are not CLS-compliant.</span></span> | <span data-ttu-id="1f6b7-348">3</span><span class="sxs-lookup"><span data-stu-id="1f6b7-348">3</span></span>
<span data-ttu-id="1f6b7-349">Typy</span><span class="sxs-lookup"><span data-stu-id="1f6b7-349">Types</span></span> | [<span data-ttu-id="1f6b7-350">Typy a signatury členů typu</span><span class="sxs-lookup"><span data-stu-id="1f6b7-350">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="1f6b7-351">Všechny typy, které se zobrazují v signatuře, musí být kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-351">All types appearing in a signature shall be CLS-compliant.</span></span> <span data-ttu-id="1f6b7-352">Všechny typy tvořící vytvořená instance obecného typu musí být kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-352">All types composing an instantiated generic type shall be CLS-compliant.</span></span> | <span data-ttu-id="1f6b7-353">11</span><span class="sxs-lookup"><span data-stu-id="1f6b7-353">11</span></span>
<span data-ttu-id="1f6b7-354">Typy</span><span class="sxs-lookup"><span data-stu-id="1f6b7-354">Types</span></span> | [<span data-ttu-id="1f6b7-355">Typy a signatury členů typu</span><span class="sxs-lookup"><span data-stu-id="1f6b7-355">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="1f6b7-356">Typové odkazy nejsou kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-356">Typed references are not CLS-compliant.</span></span> | <span data-ttu-id="1f6b7-357">14</span><span class="sxs-lookup"><span data-stu-id="1f6b7-357">14</span></span>
<span data-ttu-id="1f6b7-358">Typy</span><span class="sxs-lookup"><span data-stu-id="1f6b7-358">Types</span></span> | [<span data-ttu-id="1f6b7-359">Typy a signatury členů typu</span><span class="sxs-lookup"><span data-stu-id="1f6b7-359">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="1f6b7-360">Nespravované typy ukazatelů nejsou kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-360">Unmanaged pointer types are not CLS-compliant.</span></span> | <span data-ttu-id="1f6b7-361">17</span><span class="sxs-lookup"><span data-stu-id="1f6b7-361">17</span></span>
<span data-ttu-id="1f6b7-362">Typy</span><span class="sxs-lookup"><span data-stu-id="1f6b7-362">Types</span></span> | [<span data-ttu-id="1f6b7-363">Typy a signatury členů typu</span><span class="sxs-lookup"><span data-stu-id="1f6b7-363">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="1f6b7-364">Třídy kompatibilní se specifikací CLS, typy hodnot a rozhraní nevyžadují implementaci členů nekompatibilních se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-364">CLS-compliant classes, value types, and interfaces shall not require the implementation of non-CLS-compliant members</span></span> | <span data-ttu-id="1f6b7-365">20</span><span class="sxs-lookup"><span data-stu-id="1f6b7-365">20</span></span>
<span data-ttu-id="1f6b7-366">Typy</span><span class="sxs-lookup"><span data-stu-id="1f6b7-366">Types</span></span> | [<span data-ttu-id="1f6b7-367">Typy a signatury členů typu</span><span class="sxs-lookup"><span data-stu-id="1f6b7-367">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="1f6b7-368">[System. Object](xref:System.Object) je kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-368">[System.Object](xref:System.Object) is CLS-compliant.</span></span> <span data-ttu-id="1f6b7-369">Všechny ostatní třídy odpovídající specifikaci CLS dědí z třídy kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-369">Any other CLS-compliant class shall inherit from a CLS-compliant class.</span></span> | <span data-ttu-id="1f6b7-370">23</span><span class="sxs-lookup"><span data-stu-id="1f6b7-370">23</span></span>

### <a name="types-and-type-member-signatures"></a><span data-ttu-id="1f6b7-371">Typy a signatury členů typu</span><span class="sxs-lookup"><span data-stu-id="1f6b7-371">Types and type member signatures</span></span>

<span data-ttu-id="1f6b7-372">Typ [System. Object](xref:System.Object) je kompatibilní se specifikací CLS a je základní typ všech typů objektů v systému .NET Frameworkho typu.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-372">The [System.Object](xref:System.Object) type is CLS-compliant and is the base type of all object types in the .NET Framework type system.</span></span> <span data-ttu-id="1f6b7-373">Dědičnost v .NET Framework je buď implicitní (například třída [String](xref:System.String) implicitně dědí z `Object` třídy) nebo explicitní (například třída [CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) explicitně dědí ze třídy [ArgumentException](xref:System.ArgumentException) , která explicitně dědí z třídy [Exception](xref:System.Exception) .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-373">Inheritance in the .NET Framework is either implicit (for example, the [String](xref:System.String) class implicitly inherits from the `Object` class) or explicit (for example, the [CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) class explicitly inherits from the [ArgumentException](xref:System.ArgumentException) class, which explicitly inherits from the [Exception](xref:System.Exception) class.</span></span> <span data-ttu-id="1f6b7-374">Aby byl odvozený typ kompatibilní se specifikací CLS, musí být jeho základní typ také kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-374">For a derived type to be CLS compliant, its base type must also be CLS-compliant.</span></span>

<span data-ttu-id="1f6b7-375">Následující příklad ukazuje odvozený typ, jehož základní typ není kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-375">The following example shows a derived type whose base type is not CLS-compliant.</span></span> <span data-ttu-id="1f6b7-376">Definuje základní `Counter` třídu, která jako čítač používá celé číslo bez znaménka 32-bit.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-376">It defines a base `Counter` class that uses an unsigned 32-bit integer as a counter.</span></span> <span data-ttu-id="1f6b7-377">Vzhledem k tomu, že třída poskytuje funkce čítače tím, že zabalí unsigned integer, třída je označena jako nekompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-377">Because the class provides counter functionality by wrapping an unsigned integer, the class is marked as non-CLS-compliant.</span></span> <span data-ttu-id="1f6b7-378">V důsledku toho odvozená třída `NonZeroCounter` také není kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-378">As a result, a derived class, `NonZeroCounter`, is also not CLS-compliant.</span></span>

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

<span data-ttu-id="1f6b7-379">Všechny typy, které se zobrazují v podpisech členů, včetně návratového typu metody nebo typu vlastnosti, musí být kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-379">All types that appear in member signatures, including a method's return type or a property type, must be CLS-compliant.</span></span> <span data-ttu-id="1f6b7-380">Kromě toho pro obecné typy:</span><span class="sxs-lookup"><span data-stu-id="1f6b7-380">In addition, for generic types:</span></span>

* <span data-ttu-id="1f6b7-381">Všechny typy, které tvoří obecný typ s instancemi, musí být kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-381">All types that compose an instantiated generic type must be CLS-compliant.</span></span>

* <span data-ttu-id="1f6b7-382">Všechny typy použité jako omezení u obecných parametrů musí být kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-382">All types used as constraints on generic parameters must be CLS-compliant.</span></span>

<span data-ttu-id="1f6b7-383">.NET [Common Type System](common-type-system.md) zahrnuje řadu předdefinovaných typů, které jsou podporovány přímo modulem CLR (Common Language Runtime) a jsou speciálně kódovány v metadatech sestavení.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-383">The .NET [common type system](common-type-system.md) includes a number of built-in types that are supported directly by the common language runtime and are specially encoded in an assembly's metadata.</span></span> <span data-ttu-id="1f6b7-384">Z těchto vnitřních typů jsou typy uvedené v následující tabulce kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-384">Of these intrinsic types, the types listed in the following table are CLS-compliant.</span></span>

<span data-ttu-id="1f6b7-385">Typ kompatibilní se specifikací CLS</span><span class="sxs-lookup"><span data-stu-id="1f6b7-385">CLS-compliant type</span></span> | <span data-ttu-id="1f6b7-386">Popis</span><span class="sxs-lookup"><span data-stu-id="1f6b7-386">Description</span></span>
------------------ | -----------
[<span data-ttu-id="1f6b7-387">Bytové</span><span class="sxs-lookup"><span data-stu-id="1f6b7-387">Byte</span></span>](xref:System.Byte) | <span data-ttu-id="1f6b7-388">8 bitů unsigned integer</span><span class="sxs-lookup"><span data-stu-id="1f6b7-388">8-bit unsigned integer</span></span>
[<span data-ttu-id="1f6b7-389">Int16</span><span class="sxs-lookup"><span data-stu-id="1f6b7-389">Int16</span></span>](xref:System.Int16) | <span data-ttu-id="1f6b7-390">16bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="1f6b7-390">16-bit signed integer</span></span>
[<span data-ttu-id="1f6b7-391">Int32</span><span class="sxs-lookup"><span data-stu-id="1f6b7-391">Int32</span></span>](xref:System.Int32) | <span data-ttu-id="1f6b7-392">32 – celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="1f6b7-392">32-bit signed integer</span></span>
[<span data-ttu-id="1f6b7-393">Int64</span><span class="sxs-lookup"><span data-stu-id="1f6b7-393">Int64</span></span>](xref:System.Int64) | <span data-ttu-id="1f6b7-394">64 – celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="1f6b7-394">64-bit signed integer</span></span>
[<span data-ttu-id="1f6b7-395">Single</span><span class="sxs-lookup"><span data-stu-id="1f6b7-395">Single</span></span>](xref:System.Single) | <span data-ttu-id="1f6b7-396">Hodnota s plovoucí desetinnou čárkou s jednoduchou přesností</span><span class="sxs-lookup"><span data-stu-id="1f6b7-396">Single-precision floating-point value</span></span>
[<span data-ttu-id="1f6b7-397">Klepat</span><span class="sxs-lookup"><span data-stu-id="1f6b7-397">Double</span></span>](xref:System.Double) | <span data-ttu-id="1f6b7-398">Hodnota s plovoucí desetinnou čárkou s dvojitou přesností</span><span class="sxs-lookup"><span data-stu-id="1f6b7-398">Double-precision floating-point value</span></span>
[<span data-ttu-id="1f6b7-399">Logická hodnota</span><span class="sxs-lookup"><span data-stu-id="1f6b7-399">Boolean</span></span>](xref:System.Boolean) | <span data-ttu-id="1f6b7-400">Typ hodnoty true nebo false</span><span class="sxs-lookup"><span data-stu-id="1f6b7-400">true or false value type</span></span>
[<span data-ttu-id="1f6b7-401">Char</span><span class="sxs-lookup"><span data-stu-id="1f6b7-401">Char</span></span>](xref:System.Char) | <span data-ttu-id="1f6b7-402">Jednotka kódovaného kódu UTF-16</span><span class="sxs-lookup"><span data-stu-id="1f6b7-402">UTF-16 encoded code unit</span></span>
[<span data-ttu-id="1f6b7-403">Notaci</span><span class="sxs-lookup"><span data-stu-id="1f6b7-403">Decimal</span></span>](xref:System.Decimal) | <span data-ttu-id="1f6b7-404">Desítkové číslo jiné než plovoucí desetinné čárky</span><span class="sxs-lookup"><span data-stu-id="1f6b7-404">Non-floating-point decimal number</span></span>
[<span data-ttu-id="1f6b7-405">IntPtr</span><span class="sxs-lookup"><span data-stu-id="1f6b7-405">IntPtr</span></span>](xref:System.IntPtr) | <span data-ttu-id="1f6b7-406">Ukazatel nebo popisovač velikosti platformy definované platformou</span><span class="sxs-lookup"><span data-stu-id="1f6b7-406">Pointer or handle of a platform-defined size</span></span>
[<span data-ttu-id="1f6b7-407">Řetězec</span><span class="sxs-lookup"><span data-stu-id="1f6b7-407">String</span></span>](xref:System.String) | <span data-ttu-id="1f6b7-408">Kolekce nula, jednoho nebo více objektů char</span><span class="sxs-lookup"><span data-stu-id="1f6b7-408">Collection of zero, one, or more Char objects</span></span>

<span data-ttu-id="1f6b7-409">Vnitřní typy uvedené v následující tabulce nejsou kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-409">The intrinsic types listed in the following table are not CLS-Compliant.</span></span>

<span data-ttu-id="1f6b7-410">Neodpovídající typ</span><span class="sxs-lookup"><span data-stu-id="1f6b7-410">Non-compliant type</span></span> | <span data-ttu-id="1f6b7-411">Popis</span><span class="sxs-lookup"><span data-stu-id="1f6b7-411">Description</span></span> | <span data-ttu-id="1f6b7-412">Alternativa odpovídající specifikaci CLS</span><span class="sxs-lookup"><span data-stu-id="1f6b7-412">CLS-compliant alternative</span></span>
------------------ | ----------- | -------------------------
[<span data-ttu-id="1f6b7-413">SByte</span><span class="sxs-lookup"><span data-stu-id="1f6b7-413">SByte</span></span>](xref:System.SByte) | <span data-ttu-id="1f6b7-414">8bitový datový typ se znaménkem na 8bitové číslo</span><span class="sxs-lookup"><span data-stu-id="1f6b7-414">8-bit signed integer data type</span></span> | [<span data-ttu-id="1f6b7-415">Int16</span><span class="sxs-lookup"><span data-stu-id="1f6b7-415">Int16</span></span>](xref:System.Int16)
[<span data-ttu-id="1f6b7-416">UInt16</span><span class="sxs-lookup"><span data-stu-id="1f6b7-416">UInt16</span></span>](xref:System.UInt16) | <span data-ttu-id="1f6b7-417">16bitové unsigned integer</span><span class="sxs-lookup"><span data-stu-id="1f6b7-417">16-bit unsigned integer</span></span> | [<span data-ttu-id="1f6b7-418">Int32</span><span class="sxs-lookup"><span data-stu-id="1f6b7-418">Int32</span></span>](xref:System.Int32)
[<span data-ttu-id="1f6b7-419">UInt32</span><span class="sxs-lookup"><span data-stu-id="1f6b7-419">UInt32</span></span>](xref:System.UInt32) | <span data-ttu-id="1f6b7-420">32 – bitová unsigned integer</span><span class="sxs-lookup"><span data-stu-id="1f6b7-420">32-bit unsigned integer</span></span> | [<span data-ttu-id="1f6b7-421">Int64</span><span class="sxs-lookup"><span data-stu-id="1f6b7-421">Int64</span></span>](xref:System.Int64)
[<span data-ttu-id="1f6b7-422">UInt64</span><span class="sxs-lookup"><span data-stu-id="1f6b7-422">UInt64</span></span>](xref:System.UInt64) | <span data-ttu-id="1f6b7-423">64 – bitová unsigned integer</span><span class="sxs-lookup"><span data-stu-id="1f6b7-423">64-bit unsigned integer</span></span> | <span data-ttu-id="1f6b7-424">[Int64](xref:System.Int64) (může přetečení), [BigInteger](xref:System.Numerics.BigInteger)nebo [Double](xref:System.Double)</span><span class="sxs-lookup"><span data-stu-id="1f6b7-424">[Int64](xref:System.Int64) (may overflow), [BigInteger](xref:System.Numerics.BigInteger), or [Double](xref:System.Double)</span></span>
[<span data-ttu-id="1f6b7-425">UIntPtr</span><span class="sxs-lookup"><span data-stu-id="1f6b7-425">UIntPtr</span></span>](xref:System.UIntPtr) | <span data-ttu-id="1f6b7-426">Nepodepsaný ukazatel nebo popisovač</span><span class="sxs-lookup"><span data-stu-id="1f6b7-426">Unsigned pointer or handle</span></span> | [<span data-ttu-id="1f6b7-427">IntPtr</span><span class="sxs-lookup"><span data-stu-id="1f6b7-427">IntPtr</span></span>](xref:System.IntPtr)

<span data-ttu-id="1f6b7-428">Knihovna tříd .NET Framework nebo jiná knihovna tříd může obsahovat jiné typy, které nejsou kompatibilní se specifikací CLS; například:</span><span class="sxs-lookup"><span data-stu-id="1f6b7-428">The .NET Framework Class Library or any other class library may include other types that aren't CLS-compliant; for example:</span></span>

* <span data-ttu-id="1f6b7-429">Zabalené typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-429">Boxed value types.</span></span> <span data-ttu-id="1f6b7-430">Následující příklad jazyka C# vytvoří třídu, která má veřejnou vlastnost typu `int*` s názvem `Value` .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-430">The following C# example creates a class that has a public property of type `int*` named `Value`.</span></span> <span data-ttu-id="1f6b7-431">Vzhledem k tomu `int*` , že je zabalený typ hodnoty, kompilátor ho označí jako nekompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-431">Because an `int*` is a boxed value type, the compiler flags it as non-CLS-compliant.</span></span>

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

* <span data-ttu-id="1f6b7-432">Typové odkazy, což jsou speciální konstrukce, které obsahují odkaz na objekt a odkaz na typ.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-432">Typed references, which are special constructs that contain a reference to an object and a reference to a type.</span></span>

<span data-ttu-id="1f6b7-433">Pokud typ není kompatibilní se specifikací CLS, měli byste použít atribut [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) s parametrem *neodpovídajícím* hodnotě s hodnotou `false` .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-433">If a type is not CLS-compliant, you should apply the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute with an *isCompliant* parameter with a value of `false` to it.</span></span> <span data-ttu-id="1f6b7-434">Další informace najdete v části [atributu CLSCompliantAttribute](#the-clscompliantattribute-attribute) .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-434">For more information, see the [CLSCompliantAttribute attribute](#the-clscompliantattribute-attribute) section.</span></span>

<span data-ttu-id="1f6b7-435">Následující příklad ilustruje problém dodržování specifikace CLS v signatuře metody a při vytváření instancí obecného typu.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-435">The following example illustrates the problem of CLS compliance in a method signature and in generic type instantiation.</span></span> <span data-ttu-id="1f6b7-436">Definuje `InvoiceItem` třídu s vlastností typu [UInt32](xref:System.UInt32), vlastností typu [Nullable (of UInt32)](xref:System.Nullable%601)a konstruktorem s parametry typu `UInt32` a `Nullable(Of UInt32)` .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-436">It defines an `InvoiceItem` class with a property of type [UInt32](xref:System.UInt32), a property of type [Nullable(Of UInt32)](xref:System.Nullable%601), and a constructor with parameters of type `UInt32` and `Nullable(Of UInt32)`.</span></span> <span data-ttu-id="1f6b7-437">Při pokusu o zkompilování tohoto příkladu získáte čtyři upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-437">You get four compiler warnings when you try to compile this example.</span></span>

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

<span data-ttu-id="1f6b7-438">Chcete-li odstranit upozornění kompilátoru, nahraďte typy neodpovídající specifikaci CLS ve `InvoiceItem` veřejném rozhraní kompatibilními typy:</span><span class="sxs-lookup"><span data-stu-id="1f6b7-438">To eliminate the compiler warnings, replace the non-CLS-compliant types in the `InvoiceItem` public interface with compliant types:</span></span>

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

<span data-ttu-id="1f6b7-439">Kromě specifických typů uvedených v některé kategorie typů nejsou kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-439">In addition to the specific types listed, some categories of types are not CLS compliant.</span></span> <span data-ttu-id="1f6b7-440">Mezi ně patří nespravované typy ukazatelů a typy ukazatelů na funkce.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-440">These include unmanaged pointer types and function pointer types.</span></span> <span data-ttu-id="1f6b7-441">Následující příklad vygeneruje upozornění kompilátoru, protože používá ukazatel na celé číslo pro vytvoření pole celých čísel.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-441">The following example generates a compiler warning because it uses a pointer to an integer to create an array of integers.</span></span>

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

<span data-ttu-id="1f6b7-442">Pro abstraktní třídy kompatibilní se specifikací CLS (tj. třídy označené jako `abstract` v jazyce C#) musí být všechny členy třídy také kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-442">For CLS-compliant abstract classes (that is, classes marked as `abstract` in C#), all members of the class must also be CLS-compliant.</span></span>

### <a name="naming-conventions"></a><span data-ttu-id="1f6b7-443">Zásady vytváření názvů</span><span class="sxs-lookup"><span data-stu-id="1f6b7-443">Naming conventions</span></span>

<span data-ttu-id="1f6b7-444">Vzhledem k tomu, že některé programovací jazyky rozlišují velká a malá písmena, se musí identifikátory (například názvy oborů názvů, typů a členů) lišit o více než případu.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-444">Because some programming languages are case-insensitive, identifiers (such as the names of namespaces, types, and members) must differ by more than case.</span></span> <span data-ttu-id="1f6b7-445">Dva identifikátory jsou považovány za ekvivalentní, pokud je jejich mapování malých písmen stejné.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-445">Two identifiers are considered equivalent if their lowercase mappings are the same.</span></span> <span data-ttu-id="1f6b7-446">Následující příklad jazyka C# definuje dvě veřejné třídy `Person` a `person` .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-446">The following C# example defines two public classes, `Person` and `person`.</span></span> <span data-ttu-id="1f6b7-447">Protože se liší pouze v případě, kompilátor C# je označí jako nekompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-447">Because they differ only by case, the C# compiler flags them as not CLS-compliant.</span></span>

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

<span data-ttu-id="1f6b7-448">Identifikátory programovacích jazyků, jako jsou názvy oborů názvů, typů a členů, musí být v souladu se [standardem Unicode 3,0, technickým hlášením 15, přílohou 7](https://www.unicode.org/reports/tr15/tr15-18.html).</span><span class="sxs-lookup"><span data-stu-id="1f6b7-448">Programming language identifiers, such as the names of namespaces, types, and members, must conform to the [Unicode Standard 3.0, Technical Report 15, Annex 7](https://www.unicode.org/reports/tr15/tr15-18.html).</span></span> <span data-ttu-id="1f6b7-449">To znamená, že:</span><span class="sxs-lookup"><span data-stu-id="1f6b7-449">This means that:</span></span>

* <span data-ttu-id="1f6b7-450">Prvním znakem identifikátoru může být jakékoli velké písmeno Unicode, malé písmeno, název písmene, písmeno, písmeno, jiné písmeno nebo číslo písmen.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-450">The first character of an identifier can be any Unicode uppercase letter, lowercase letter, title case letter, modifier letter, other letter, or letter number.</span></span> <span data-ttu-id="1f6b7-451">Informace o kategoriích znaků Unicode naleznete v tématu výčet [System. Globalization. UnicodeCategory](xref:System.Globalization.UnicodeCategory) .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-451">For information on Unicode character categories, see the [System.Globalization.UnicodeCategory](xref:System.Globalization.UnicodeCategory) enumeration.</span></span>

* <span data-ttu-id="1f6b7-452">Další znaky mohou být z libovolné kategorie jako první znak a mohou také obsahovat značky bez mezer mezi mezerami, kombinováním značek mezer, desetinnými čísly, interpunkční znaménky konektoru a formátovacími kódy.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-452">Subsequent characters can be from any of the categories as the first character, and can also include non-spacing marks, spacing combining marks, decimal numbers, connector punctuations, and formatting codes.</span></span>

<span data-ttu-id="1f6b7-453">Před porovnáním identifikátorů byste měli odfiltrovat Formátovací kódy a převést identifikátory na normalizační formu Unicode C, protože jeden znak může být reprezentován více jednotkami kódu zakódovanými v kódování UTF-16.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-453">Before you compare identifiers, you should filter out formatting codes and convert the identifiers to Unicode Normalization Form C, because a single character can be represented by multiple UTF-16-encoded code units.</span></span> <span data-ttu-id="1f6b7-454">Sekvence znaků, které vytvářejí stejné jednotky kódu ve formě normalizace Unicode C, nejsou kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-454">Character sequences that produce the same code units in Unicode Normalization Form C are not CLS-compliant.</span></span> <span data-ttu-id="1f6b7-455">Následující příklad definuje vlastnost s názvem `Å` , která se skládá z znaku ANGSTROM Sign (U + 212B), a druhá vlastnost s názvem, `Å` která se skládá z znaku velké písmeno latinky a s výše UVEDENým prstenci (U + 00C5).</span><span class="sxs-lookup"><span data-stu-id="1f6b7-455">The following example defines a property named `Å`, which consists of the character ANGSTROM SIGN (U+212B), and a second property named `Å` which consists of the character LATIN CAPITAL LETTER A WITH RING ABOVE (U+00C5).</span></span> <span data-ttu-id="1f6b7-456">Kompilátor jazyka C# označí zdrojový kód jako nekompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-456">The C# compiler flags the source code as non-CLS-compliant.</span></span>

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

<span data-ttu-id="1f6b7-457">Názvy členů v rámci určitého oboru (například obory názvů v rámci sestavení, typy v rámci oboru názvů nebo členy v rámci typu) musí být jedinečné s výjimkou názvů, které jsou přeloženy prostřednictvím přetížení.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-457">Member names within a particular scope (such as the namespaces within an assembly, the types within a namespace, or the members within a type) must be unique except for names that are resolved through overloading.</span></span> <span data-ttu-id="1f6b7-458">Tento požadavek je přísnější než u společného systému typů, což umožňuje více členům v rámci oboru mít stejné názvy, pokud jsou různé druhy členů (například jedna je metoda a jedna je pole).</span><span class="sxs-lookup"><span data-stu-id="1f6b7-458">This requirement is more stringent than that of the common type system, which allows multiple members within a scope to have identical names as long as they are different kinds of members (for example, one is a method and one is a field).</span></span> <span data-ttu-id="1f6b7-459">Konkrétně pro členy typu:</span><span class="sxs-lookup"><span data-stu-id="1f6b7-459">In particular, for type members:</span></span>

* <span data-ttu-id="1f6b7-460">Pole a vnořené typy jsou rozlišeny pouze podle názvu.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-460">Fields and nested types are distinguished by name alone.</span></span>

* <span data-ttu-id="1f6b7-461">Metody, vlastnosti a události, které mají stejný název, se musí lišit více než pouhým návratovým typem.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-461">Methods, properties, and events that have the same name must differ by more than just return type.</span></span>

<span data-ttu-id="1f6b7-462">Následující příklad znázorňuje požadavek, aby názvy členů musely být v rámci svého oboru jedinečné.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-462">The following example illustrates the requirement that member names must be unique within their scope.</span></span> <span data-ttu-id="1f6b7-463">Definuje třídu s názvem `Converter` , která obsahuje čtyři členy s názvem `Conversion` .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-463">It defines a class named `Converter` that includes four members named `Conversion`.</span></span> <span data-ttu-id="1f6b7-464">Tři jsou metody a jedna je vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-464">Three are methods, and one is a property.</span></span> <span data-ttu-id="1f6b7-465">Metoda, která obsahuje `Int64` parametr, je jednoznačně pojmenována, ale tyto dvě metody s `Int32` parametrem nejsou, protože návratová hodnota není považována za součást signatury člena.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-465">The method that includes an `Int64` parameter is uniquely named, but the two methods with an `Int32` parameter are not, because return value is not considered a part of a member's signature.</span></span> <span data-ttu-id="1f6b7-466">`Conversion`Tato vlastnost také porušuje tento požadavek, protože vlastnosti nemohou mít stejný název jako přetížené metody.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-466">The `Conversion` property also violates this requirement, because properties cannot have the same name as overloaded methods.</span></span>

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

<span data-ttu-id="1f6b7-467">Jednotlivé jazyky obsahují jedinečná klíčová slova, takže jazyky, které cílí na modul CLR (Common Language Runtime), musí také poskytovat určitý mechanismus pro odkazování na identifikátory (například názvy typů), které se shodují s klíčovými slovy.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-467">Individual languages include unique keywords, so languages that target the common language runtime must also provide some mechanism for referencing identifiers (such as type names) that coincide with keywords.</span></span> <span data-ttu-id="1f6b7-468">Například `case` je klíčové slovo v jazyce C# i Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-468">For example, `case` is a keyword in both C# and Visual Basic.</span></span> <span data-ttu-id="1f6b7-469">Následující příklad Visual Basic však může jednoznačně určit třídu s názvem `case` z `case` klíčového slova pomocí otevírací a pravé složené závorky.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-469">However, the following Visual Basic example is able to disambiguate a class named `case` from the `case` keyword by using opening and closing braces.</span></span> <span data-ttu-id="1f6b7-470">V opačném případě by tento příklad vytvořil chybovou zprávu "klíčové slovo není platné jako identifikátor" a kompilace se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-470">Otherwise, the example would produce the error message, "Keyword is not valid as an identifier," and fail to compile.</span></span>

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

<span data-ttu-id="1f6b7-471">Následující příklad jazyka C# může vytvořit instanci `case` třídy pomocí symbolu @ pro odstranění identifikátoru z klíčového slova jazyka.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-471">The following C# example is able to instantiate the `case` class by using the @ symbol to disambiguate the identifier from the language keyword.</span></span> <span data-ttu-id="1f6b7-472">Bez něj kompilátor jazyka C# zobrazí dvě chybové zprávy, "očekával se typ" a "neplatný výraz" Case ".</span><span class="sxs-lookup"><span data-stu-id="1f6b7-472">Without it, the C# compiler would display two error messages, "Type expected" and "Invalid expression term 'case'."</span></span>

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

### <a name="type-conversion"></a><span data-ttu-id="1f6b7-473">Převod typů</span><span class="sxs-lookup"><span data-stu-id="1f6b7-473">Type conversion</span></span>

<span data-ttu-id="1f6b7-474">Specifikace CLS (Common Language Specification) definuje dva operátory převodu:</span><span class="sxs-lookup"><span data-stu-id="1f6b7-474">The Common Language Specification defines two conversion operators:</span></span>

* <span data-ttu-id="1f6b7-475">`op_Implicit`, který se používá pro rozšiřující převody, které nemají za následek ztrátu dat nebo přesnost.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-475">`op_Implicit`, which is used for widening conversions that do not result in loss of data or precision.</span></span> <span data-ttu-id="1f6b7-476">Například struktura [Decimal](xref:System.Decimal) obsahuje přetížený `op_Implicit` operátor pro převod hodnot integrálních typů a hodnot typu [char](xref:System.Char) na `Decimal` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-476">For example, the [Decimal](xref:System.Decimal) structure includes an overloaded `op_Implicit` operator to convert values of integral types and [Char](xref:System.Char) values to `Decimal` values.</span></span>

* <span data-ttu-id="1f6b7-477">`op_Explicit`, který se používá pro zúžení převodů, které mohou mít za následek ztrátu velikosti (hodnota je převedena na hodnotu, která má menší rozsah) nebo přesnost.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-477">`op_Explicit`, which is used for narrowing conversions that can result in loss of magnitude (a value is converted to a value that has a smaller range) or precision.</span></span> <span data-ttu-id="1f6b7-478">`Decimal`Struktura obsahuje například přetížený `op_Explicit` operátor pro převod [dvojitých](xref:System.Double) a [jednoduchých](xref:System.Single) hodnot na `Decimal` a pro převod `Decimal` hodnot na integrální hodnoty, `Double` , `Single` a `Char` .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-478">For example, the `Decimal` structure includes an overloaded `op_Explicit` operator to convert [Double](xref:System.Double) and [Single](xref:System.Single) values to `Decimal` and to convert `Decimal` values to integral values, `Double`, `Single`, and `Char`.</span></span>

<span data-ttu-id="1f6b7-479">Ne všechny jazyky ale podporují přetížení operátoru nebo definici vlastních operátorů.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-479">However, not all languages support operator overloading or the definition of custom operators.</span></span> <span data-ttu-id="1f6b7-480">Pokud se rozhodnete implementovat tyto operátory převodu, měli byste také poskytnout alternativní způsob, jak provést převod.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-480">If you choose to implement these conversion operators, you should also provide an alternate way to perform the conversion.</span></span> <span data-ttu-id="1f6b7-481">Doporučujeme zadat `From` metody XXX a `To` xxx.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-481">We recommend that you provide `From`Xxx and `To`Xxx methods.</span></span>

<span data-ttu-id="1f6b7-482">Následující příklad definuje implicitní a explicitní převody kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-482">The following example defines CLS-compliant implicit and explicit conversions.</span></span> <span data-ttu-id="1f6b7-483">Vytvoří `UDouble` třídu, která představuje podepsané číslo s dvojitou přesností a plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-483">It creates a `UDouble` class that represents an signed double-precision, floating-point number.</span></span> <span data-ttu-id="1f6b7-484">Poskytuje implicitní převody z `UDouble` na `Double` a pro explicitní převody z `UDouble` na `Single` , do a `Double` `UDouble` `Single` na `UDouble` .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-484">It provides for implicit conversions from `UDouble` to `Double` and for explicit conversions from `UDouble` to `Single`, `Double` to `UDouble`, and `Single` to `UDouble`.</span></span> <span data-ttu-id="1f6b7-485">Také definuje `ToDouble` metodu jako alternativu implicitního operátoru převodu a `ToSingle` `FromDouble` metody, a `FromSingle` jako alternativy pro explicitní operátory převodu.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-485">It also defines a `ToDouble` method as an alternative to the implicit conversion operator and the `ToSingle`, `FromDouble`, and `FromSingle` methods as alternatives to the explicit conversion operators.</span></span>

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

### <a name="arrays"></a><span data-ttu-id="1f6b7-486">Pole</span><span class="sxs-lookup"><span data-stu-id="1f6b7-486">Arrays</span></span>

<span data-ttu-id="1f6b7-487">Pole kompatibilní se specifikací CLS odpovídají následujícím pravidlům:</span><span class="sxs-lookup"><span data-stu-id="1f6b7-487">CLS-compliant arrays conform to the following rules:</span></span>

* <span data-ttu-id="1f6b7-488">Všechny dimenze pole musí mít dolní mez nula.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-488">All dimensions of an array must have a lower bound of zero.</span></span> <span data-ttu-id="1f6b7-489">Následující příklad vytvoří pole, které není kompatibilní se specifikací CLS, s dolní mezí jedna.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-489">The following example creates a non-CLS-compliant array with a lower bound of one.</span></span> <span data-ttu-id="1f6b7-490">Všimněte si, že navzdory přítomnosti atributu [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) kompilátor nezjistí, že pole vrácené `Numbers.GetTenPrimes` metodou není kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-490">Note that, despite the presence of the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute, the compiler does not detect that the array returned by the `Numbers.GetTenPrimes` method is not CLS-compliant.</span></span>

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

* <span data-ttu-id="1f6b7-491">Všechny prvky pole musí obsahovat typy kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-491">All array elements must consist of CLS-compliant types.</span></span> <span data-ttu-id="1f6b7-492">Následující příklad definuje dvě metody, které vracejí pole neodpovídající specifikaci CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-492">The following example defines two methods that return non-CLS-compliant arrays.</span></span> <span data-ttu-id="1f6b7-493">První vrátí pole hodnot [UInt32](xref:System.UInt32) .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-493">The first returns an array of [UInt32](xref:System.UInt32) values.</span></span> <span data-ttu-id="1f6b7-494">Druhá vrátí pole [objektu](xref:System.Object) , které zahrnuje [Int32](xref:System.Int32) a `UInt32` Values.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-494">The second returns an [Object](xref:System.Object) array that includes [Int32](xref:System.Int32) and `UInt32` values.</span></span> <span data-ttu-id="1f6b7-495">I když kompilátor identifikuje první pole jako nevyhovující z důvodu jeho `UInt32` typu, nerozpozná, že druhé pole obsahuje prvky neodpovídající specifikaci CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-495">Although the compiler identifies the first array as non-compliant because of its `UInt32` type, it fails to recognize that the second array includes non-CLS-compliant elements.</span></span>

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

* <span data-ttu-id="1f6b7-496">Rozlišení přetěžování pro metody, které mají parametry pole, je založené na tom, že se jedná o pole a na jejich typu prvku.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-496">Overload resolution for methods that have array parameters is based on the fact that they are arrays and on their element type.</span></span> <span data-ttu-id="1f6b7-497">Z tohoto důvodu je následující definice přetížené `GetSquares` metody kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-497">For this reason, the following definition of an overloaded `GetSquares` method is CLS-compliant.</span></span>

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

### <a name="interfaces"></a><span data-ttu-id="1f6b7-498">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="1f6b7-498">Interfaces</span></span>

<span data-ttu-id="1f6b7-499">Rozhraní kompatibilní se specifikací CLS mohou definovat vlastnosti, události a virtuální metody (metody bez implementace).</span><span class="sxs-lookup"><span data-stu-id="1f6b7-499">CLS-compliant interfaces can define properties, events, and virtual methods (methods with no implementation).</span></span> <span data-ttu-id="1f6b7-500">Rozhraní kompatibilní se specifikací CLS nemůže mít následující:</span><span class="sxs-lookup"><span data-stu-id="1f6b7-500">A CLS-compliant interface cannot have any of the following:</span></span>

* <span data-ttu-id="1f6b7-501">Statické metody nebo statická pole.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-501">Static methods or static fields.</span></span> <span data-ttu-id="1f6b7-502">Kompilátor jazyka C# generuje chyby kompilátoru, pokud definujete statického člena v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-502">The C# compiler generates compiler errors if you define a static member in an interface.</span></span>

* <span data-ttu-id="1f6b7-503">Pole.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-503">Fields.</span></span> <span data-ttu-id="1f6b7-504">Kompilátor jazyka C# generuje chyby kompilátoru, pokud definujete pole v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-504">The C# a compiler generates compiler errors if you define a field in an interface.</span></span>

* <span data-ttu-id="1f6b7-505">Metody, které nejsou kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-505">Methods that are not CLS-compliant.</span></span> <span data-ttu-id="1f6b7-506">Například následující definice rozhraní obsahuje metodu, `INumber.GetUnsigned` která je označena jako nekompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-506">For example, the following interface definition includes a method, `INumber.GetUnsigned`, that is marked as non-CLS-compliant.</span></span> <span data-ttu-id="1f6b7-507">Tento příklad generuje upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-507">This example generates a compiler warning.</span></span>

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

  <span data-ttu-id="1f6b7-508">Vzhledem k tomuto pravidlu nejsou typy kompatibilní se specifikací CLS vyžadovány k implementaci členů, které nedodržují specifikaci CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-508">Because of this rule, CLS-compliant types are not required to implement non-CLS-compliant members.</span></span> <span data-ttu-id="1f6b7-509">Pokud rozhraní kompatibilní se specifikací CLS zveřejňuje třídu, která implementuje rozhraní nekompatibilní se specifikací CLS, měla by také poskytnout konkrétní implementace všech členů nekompatibilních se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-509">If a CLS-compliant framework does expose a class that implements a non-CLS compliant interface, it should also provide concrete implementations of all non-CLS-compliant members.</span></span>

<span data-ttu-id="1f6b7-510">Kompilátory jazyka odpovídající specifikaci CLS musí také umožňovat třídě, aby poskytovala samostatné implementace členů, kteří mají stejný název a signaturu ve více rozhraních.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-510">CLS-compliant language compilers must also allow a class to provide separate implementations of members that have the same name and signature in multiple interfaces.</span></span> <span data-ttu-id="1f6b7-511">Jazyk C# podporuje explicitní implementace rozhraní, které poskytují různé implementace identicky pojmenovaných metod.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-511">C# supports explicit interface implementations to provide different implementations of identically named methods.</span></span> <span data-ttu-id="1f6b7-512">Následující příklad znázorňuje tento scénář definováním `Temperature` třídy, která implementuje `ICelsius` `IFahrenheit` rozhraní a jako explicitní implementace rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-512">The following example illustrates this scenario by defining a `Temperature` class that implements the `ICelsius` and `IFahrenheit` interfaces as explicit interface implementations.</span></span>

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

### <a name="enumerations"></a><span data-ttu-id="1f6b7-513">Výčty</span><span class="sxs-lookup"><span data-stu-id="1f6b7-513">Enumerations</span></span>

<span data-ttu-id="1f6b7-514">Výčty kompatibilní se specifikací CLS musí dodržovat tato pravidla:</span><span class="sxs-lookup"><span data-stu-id="1f6b7-514">CLS-compliant enumerations must follow these rules:</span></span>

* <span data-ttu-id="1f6b7-515">Podkladový typ výčtu musí být vnitřní celé číslo kompatibilní se specifikací CLS ([Byte](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32)nebo [Int64](xref:System.Int64)).</span><span class="sxs-lookup"><span data-stu-id="1f6b7-515">The underlying type of the enumeration must be an intrinsic CLS-compliant integer ([Byte](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32), or [Int64](xref:System.Int64)).</span></span> <span data-ttu-id="1f6b7-516">Například následující kód se pokusí definovat výčet, jehož nadřízený typ je [UInt32](xref:System.UInt32) a vygeneruje upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-516">For example, the following code tries to define an enumeration whose underlying type is [UInt32](xref:System.UInt32) and generates a compiler warning.</span></span>

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

* <span data-ttu-id="1f6b7-517">Typ výčtu musí mít jedno pole instance s názvem `Value__` , které je označeno `FieldAttributes.RTSpecialName` atributem.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-517">An enumeration type must have a single instance field named `Value__` that is marked with the `FieldAttributes.RTSpecialName` attribute.</span></span> <span data-ttu-id="1f6b7-518">To umožňuje implicitně odkazovat na hodnotu pole.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-518">This enables you to reference the field value implicitly.</span></span>

* <span data-ttu-id="1f6b7-519">Výčet zahrnuje statická pole literálů, jejichž typy se shodují s typem výčtu samotného.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-519">An enumeration includes literal static fields whose types match the type of the enumeration itself.</span></span> <span data-ttu-id="1f6b7-520">Například pokud definujete `State` výčet s hodnotami `State.On` a `State.Off` , `State.On` a `State.Off` jsou obě literální statická pole, jejichž typ je `State` .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-520">For example, if you define a `State` enumeration with values of `State.On` and `State.Off`, `State.On` and `State.Off` are both literal static fields whose type is `State`.</span></span>

* <span data-ttu-id="1f6b7-521">Existují dva druhy výčtů:</span><span class="sxs-lookup"><span data-stu-id="1f6b7-521">There are two kinds of enumerations:</span></span>

  * <span data-ttu-id="1f6b7-522">Výčet, který představuje sadu vzájemně se vylučujících pojmenovaných celočíselných hodnot.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-522">An enumeration that represents a set of mutually exclusive, named integer values.</span></span> <span data-ttu-id="1f6b7-523">Tento typ výčtu je označen nepřítomností vlastního atributu [System. FlagsAttribute](xref:System.FlagsAttribute) .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-523">This type of enumeration is indicated by the absence of the [System.FlagsAttribute](xref:System.FlagsAttribute) custom attribute.</span></span>

  * <span data-ttu-id="1f6b7-524">Výčet, který představuje sadu bitových příznaků, které lze kombinovat k vygenerování nepojmenované hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-524">An enumeration that represents a set of bit flags that can combine to generate an unnamed value.</span></span> <span data-ttu-id="1f6b7-525">Tento typ výčtu je označen přítomností vlastního atributu [System. FlagsAttribute](xref:System.FlagsAttribute) .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-525">This type of enumeration is indicated by the presence of the [System.FlagsAttribute](xref:System.FlagsAttribute) custom attribute.</span></span>

<span data-ttu-id="1f6b7-526">Další informace najdete v dokumentaci ke struktuře [výčtu](xref:System.Enum) .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-526">For more information, see the documentation for the [Enum](xref:System.Enum) structure.</span></span>

* <span data-ttu-id="1f6b7-527">Hodnota výčtu není omezena na rozsah zadaných hodnot.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-527">The value of an enumeration is not limited to the range of its specified values.</span></span> <span data-ttu-id="1f6b7-528">Jinými slovy rozsah hodnot ve výčtu je rozsah své základní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-528">In other words, the range of values in an enumeration is the range of its underlying value.</span></span> <span data-ttu-id="1f6b7-529">`Enum.IsDefined`K určení, zda je zadaná hodnota členem výčtu, lze použít metodu.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-529">You can use the `Enum.IsDefined` method to determine whether a specified value is a member of an enumeration.</span></span>

### <a name="type-members-in-general"></a><span data-ttu-id="1f6b7-530">Obecné typy členů</span><span class="sxs-lookup"><span data-stu-id="1f6b7-530">Type members in general</span></span>

<span data-ttu-id="1f6b7-531">Specifikace CLS (Common Language Specification) vyžaduje, aby všechna pole a metody byly dostupné jako členové konkrétní třídy.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-531">The Common Language Specification requires all fields and methods to be accessed as members of a particular class.</span></span> <span data-ttu-id="1f6b7-532">Proto globální statická pole a metody (tj. statická pole nebo metody, které jsou definovány odděleně od typu) nejsou kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-532">Therefore, global static fields and methods (that is, static fields or methods that are defined apart from a type) are not CLS-compliant.</span></span> <span data-ttu-id="1f6b7-533">Pokud se pokusíte do zdrojového kódu zahrnout globální pole nebo metodu, kompilátor jazyka C# vygeneruje chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-533">If you try to include a global field or method in your source code, the C# compiler generates a compiler error.</span></span>

<span data-ttu-id="1f6b7-534">Specifikace CLS (Common Language Specification) podporuje pouze standardní spravovanou konvenci volání.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-534">The Common Language Specification supports only the standard managed calling convention.</span></span> <span data-ttu-id="1f6b7-535">Nepodporuje konvence nespravovaného volání a metody se seznamy argumentů proměnných označenými `varargs` klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-535">It doesn't support unmanaged calling conventions and methods with variable argument lists marked with the `varargs` keyword.</span></span> <span data-ttu-id="1f6b7-536">U seznamů argumentů proměnných, které jsou kompatibilní se standardní spravovanou konvencí volání, použijte atribut [ParamArrayAttribute](xref:System.ParamArrayAttribute) nebo implementaci jednotlivého jazyka, jako je `params` klíčové slovo v jazyce C# a `ParamArray` klíčové slovo v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-536">For variable argument lists that are compatible with the standard managed calling convention, use the [ParamArrayAttribute](xref:System.ParamArrayAttribute) attribute or the individual language's implementation, such as the `params` keyword in C# and the `ParamArray` keyword in Visual Basic.</span></span>

### <a name="member-accessibility"></a><span data-ttu-id="1f6b7-537">Přístupnost člena</span><span class="sxs-lookup"><span data-stu-id="1f6b7-537">Member accessibility</span></span>

<span data-ttu-id="1f6b7-538">Přepsání zděděného člena nemůže změnit přístupnost daného člena.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-538">Overriding an inherited member cannot change the accessibility of that member.</span></span> <span data-ttu-id="1f6b7-539">Například veřejná metoda v základní třídě nemůže být přepsána soukromou metodou v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-539">For example, a public method in a base class cannot be overridden by a private method in a derived class.</span></span> <span data-ttu-id="1f6b7-540">Existuje jedna výjimka: `protected internal` člen (v jazyce C#) nebo `Protected Friend` (v Visual Basic) v jednom sestavení, který je přepsán typem v jiném sestavení.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-540">There is one exception: a `protected internal` (in C#) or `Protected Friend` (in Visual Basic) member in one assembly that is overridden by a type in a different assembly.</span></span>  <span data-ttu-id="1f6b7-541">V takovém případě je přístupnost přepsání `Protected` .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-541">In that case, the accessibility of the override is `Protected`.</span></span>

<span data-ttu-id="1f6b7-542">Následující příklad ukazuje chybu, která je generována, když je atribut [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) nastaven na hodnotu `true` a `Person` , což je třída odvozená z `Animal` , se pokusí změnit přístupnost `Species` vlastnosti z veřejné na soukromou.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-542">The following example illustrates the error that is generated when the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute is set to `true`, and `Person`, which is a class derived from `Animal`, tries to change the accessibility of the `Species` property from public to private.</span></span> <span data-ttu-id="1f6b7-543">Příklad se úspěšně zkompiluje, pokud je jeho přístupnost změněno na veřejné.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-543">The example compiles successfully if its accessibility is changed to public.</span></span>

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

<span data-ttu-id="1f6b7-544">Typy v signatuře člena musí být přístupné, kdykoli je tento člen přístupný.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-544">Types in the signature of a member must be accessible whenever that member is accessible.</span></span> <span data-ttu-id="1f6b7-545">Například to znamená, že veřejný člen nemůže obsahovat parametr, jehož typ je Private, Protected nebo Internal.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-545">For example, this means that a public member cannot include a parameter whose type is private, protected, or internal.</span></span> <span data-ttu-id="1f6b7-546">Následující příklad ukazuje chybu kompilátoru, která je výsledkem, když `StringWrapper` konstruktor třídy zpřístupňuje vnitřní `StringOperationType` hodnotu výčtu, která určuje, jak má být hodnota řetězce zabalena.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-546">The following example illustrates the compiler error that results when a `StringWrapper` class constructor exposes an internal `StringOperationType` enumeration value that determines how a string value should be wrapped.</span></span>

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

### <a name="generic-types-and-members"></a><span data-ttu-id="1f6b7-547">Obecné typy a členy</span><span class="sxs-lookup"><span data-stu-id="1f6b7-547">Generic types and members</span></span>

<span data-ttu-id="1f6b7-548">Vnořené typy mají vždy alespoň tolik obecných parametrů jako jejich nadřazený typ.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-548">Nested types always have at least as many generic parameters as their enclosing type.</span></span> <span data-ttu-id="1f6b7-549">Odpovídají umístění obecným parametrům v nadřazeném typu.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-549">These correspond by position to the generic parameters in the enclosing type.</span></span> <span data-ttu-id="1f6b7-550">Obecný typ může obsahovat také nové obecné parametry.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-550">The generic type can also include new generic parameters.</span></span>

<span data-ttu-id="1f6b7-551">Vztah mezi parametry obecného typu obsahujícího typu a jeho vnořenými typy mohou být skryty syntaxí jednotlivých jazyků.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-551">The relationship between the generic type parameters of a containing type and its nested types may be hidden by the syntax of individual languages.</span></span> <span data-ttu-id="1f6b7-552">V následujícím příkladu obecný typ `Outer<T>` obsahuje dvě vnořené třídy `Inner1A` a `Inner1B<U>` .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-552">In the following example, a generic type `Outer<T>` contains two nested classes, `Inner1A` and `Inner1B<U>`.</span></span> <span data-ttu-id="1f6b7-553">Volání `ToString` metody, ze které jednotlivé třídy dědí `Object.ToString` , ukazují, že každá vnořená třída obsahuje parametry typu své nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-553">The calls to the `ToString` method, which each class inherits from `Object.ToString`, show that each nested class includes the type parameters of its containing class.</span></span>

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

<span data-ttu-id="1f6b7-554">Názvy obecných typů jsou kódovány v *názvu*formuláře*n*, kde *název* je název typu, *\`* je znakový literál a *n* je počet parametrů deklarovaných na typ, nebo pro vnořené obecné typy počet nově zavedených parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-554">Generic type names are encoded in the form *name*'*n*, where *name* is the type name, *\`* is a character literal, and *n* is the number of parameters declared on the type, or, for nested generic types, the number of newly introduced type parameters.</span></span> <span data-ttu-id="1f6b7-555">Toto kódování názvů obecného typu je primárně v zájmu vývojářů, kteří používají reflexi pro přístup k obecným typům specifikace CLS v knihovně.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-555">This encoding of generic type names is primarily of interest to developers who use reflection to access CLS-complaint generic types in a library.</span></span>

<span data-ttu-id="1f6b7-556">Pokud jsou omezení aplikována na obecný typ, všechny typy použité jako omezení musí být také kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-556">If constraints are applied to a generic type, any types used as constraints must also be CLS-compliant.</span></span> <span data-ttu-id="1f6b7-557">Následující příklad definuje třídu s názvem `BaseClass` , která není kompatibilní se specifikací CLS, a obecnou třídu s názvem, `BaseCollection` jejíž parametr typu musí být odvozen od `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-557">The following example defines a class named `BaseClass` that is not CLS-compliant and a generic class named `BaseCollection` whose type parameter must derive from `BaseClass`.</span></span> <span data-ttu-id="1f6b7-558">Ale vzhledem `BaseClass` k tomu, že není kompatibilní se specifikací CLS, kompilátor vygeneruje upozornění.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-558">But because `BaseClass` is not CLS-compliant, the compiler emits a warning.</span></span>

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

<span data-ttu-id="1f6b7-559">Je-li obecný typ odvozen od obecného základního typu, musí znovu deklarovat jakákoli omezení, aby bylo zaručeno, že jsou také splněna omezení základního typu.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-559">If a generic type is derived from a generic base type, it must redeclare any constraints so that it can guarantee that constraints on the base type are also satisfied.</span></span> <span data-ttu-id="1f6b7-560">Následující příklad definuje `Number<T>` , který může představovat libovolný číselný typ.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-560">The following example defines a `Number<T>` that can represent any numeric type.</span></span> <span data-ttu-id="1f6b7-561">Definuje také `FloatingPoint<T>` třídu, která představuje hodnotu s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-561">It also defines a `FloatingPoint<T>` class that represents a floating point value.</span></span> <span data-ttu-id="1f6b7-562">Zdrojový kód však nelze zkompilovat, protože neaplikuje omezení na `Number<T>` (Tento T musí být typ hodnoty) na `FloatingPoint<T>` .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-562">However, the source code fails to compile, because it does not apply the constraint on `Number<T>` (that T must be a value type) to `FloatingPoint<T>`.</span></span>

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

<span data-ttu-id="1f6b7-563">Příklad se úspěšně zkompiluje, pokud je omezení přidáno do `FloatingPoint<T>` třídy.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-563">The example compiles successfully if the constraint is added to the `FloatingPoint<T>` class.</span></span>

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

<span data-ttu-id="1f6b7-564">Specifikace CLS (Common Language Specification) ukládá konzervativní model pro vytváření instancí pro vnořené typy a chráněné členy.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-564">The Common Language Specification imposes a conservative per-instantiation model for nested types and protected members.</span></span> <span data-ttu-id="1f6b7-565">Otevřené obecné typy nemohou vystavovat pole nebo členy s podpisy, které obsahují konkrétní instanci vnořeného, chráněného obecného typu.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-565">Open generic types cannot expose fields or members with signatures that contain a specific instantiation of a nested, protected generic type.</span></span> <span data-ttu-id="1f6b7-566">Neobecné typy, které rozšíří specifické instance obecné základní třídy nebo rozhraní, nemůžou vystavovat pole nebo členy s podpisy, které obsahují různé instance vnořeného, chráněného obecného typu.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-566">Non-generic types that extend a specific instantiation of a generic base class or interface cannot expose fields or members with signatures that contain a different instantiation of a nested, protected generic type.</span></span>

<span data-ttu-id="1f6b7-567">Následující příklad definuje obecný typ, `C1<T>` a chráněnou třídu `C1<T>.N` .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-567">The following example defines a generic type, `C1<T>`, and a protected class, `C1<T>.N`.</span></span> <span data-ttu-id="1f6b7-568">`C1<T>`má dvě metody `M1` a `M2` .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-568">`C1<T>` has two methods, `M1` and `M2`.</span></span> <span data-ttu-id="1f6b7-569">Není však `M1` kompatibilní se specifikací CLS, protože se pokusí vrátit `C1<int>.N` objekt z `C1<T>` .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-569">However, `M1` is not CLS-compliant because it tries to return a `C1<int>.N` object from `C1<T>`.</span></span> <span data-ttu-id="1f6b7-570">Druhá třída `C2` je odvozena z `C1<long>` .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-570">A second class, `C2`, is derived from `C1<long>`.</span></span> <span data-ttu-id="1f6b7-571">Má dvě metody, `M3` a `M4` .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-571">It has two methods, `M3` and `M4`.</span></span> <span data-ttu-id="1f6b7-572">`M3`není kompatibilní se specifikací CLS, protože se pokusí vrátit `C1<int>.N` objekt z podtřídy `C1<long>` .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-572">`M3` is not CLS-compliant because it tries to return a `C1<int>.N` object from a subclass of `C1<long>`.</span></span> <span data-ttu-id="1f6b7-573">Všimněte si, že kompilátory jazyka mohou být ještě více omezující.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-573">Note that language compilers can be even more restrictive.</span></span> <span data-ttu-id="1f6b7-574">V tomto příkladu Visual Basic při pokusu o zkompilování zobrazit chybu `M4` .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-574">In this example, Visual Basic displays an error when it tries to compile `M4`.</span></span>

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

### <a name="constructors"></a><span data-ttu-id="1f6b7-575">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="1f6b7-575">Constructors</span></span>

<span data-ttu-id="1f6b7-576">Konstruktory v třídách a strukturách odpovídajících specifikaci CLS musí dodržovat tato pravidla:</span><span class="sxs-lookup"><span data-stu-id="1f6b7-576">Constructors in CLS-compliant classes and structures must follow these rules:</span></span>

* <span data-ttu-id="1f6b7-577">Konstruktor odvozené třídy musí volat konstruktor instance své základní třídy před tím, než přistupuje k zděděným datům instance.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-577">A constructor of a derived class must call the instance constructor of its base class before it accesses inherited instance data.</span></span> <span data-ttu-id="1f6b7-578">Tento požadavek je způsoben faktem, že konstruktory základní třídy nejsou děděny jejich odvozenými třídami.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-578">This requirement is due to the fact that base class constructors are not inherited by their derived classes.</span></span> <span data-ttu-id="1f6b7-579">Toto pravidlo se nevztahuje na struktury, které nepodporují přímou dědičnost.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-579">This rule does not apply to structures, which do not support direct inheritance.</span></span>

  <span data-ttu-id="1f6b7-580">Kompilátory obvykle toto pravidlo vynutil nezávisle na kompatibilitě se specifikací CLS, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-580">Typically, compilers enforce this rule independently of CLS compliance, as the following example shows.</span></span> <span data-ttu-id="1f6b7-581">Vytvoří `Doctor` třídu, která je odvozena od `Person` třídy, ale `Doctor` Třída nevolá `Person` konstruktor třídy pro inicializaci zděděných polí instance.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-581">It creates a `Doctor` class that is derived from a `Person` class, but the `Doctor` class fails to call the `Person` class constructor to initialize inherited instance fields.</span></span>

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

* <span data-ttu-id="1f6b7-582">Nelze volat konstruktor objektu s výjimkou vytvoření objektu.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-582">An object constructor cannot be called except to create an object.</span></span> <span data-ttu-id="1f6b7-583">Kromě toho objekt nelze inicializovat dvakrát.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-583">In addition, an object cannot be initialized twice.</span></span> <span data-ttu-id="1f6b7-584">Například to znamená, že nesmí `Object.MemberwiseClone` volat konstruktory.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-584">For example, this means that `Object.MemberwiseClone` must not call constructors.</span></span>

### <a name="properties"></a><span data-ttu-id="1f6b7-585">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1f6b7-585">Properties</span></span>

<span data-ttu-id="1f6b7-586">Vlastnosti v typech odpovídajících specifikaci CLS musí dodržovat tato pravidla:</span><span class="sxs-lookup"><span data-stu-id="1f6b7-586">Properties in CLS-compliant types must follow these rules:</span></span>

* <span data-ttu-id="1f6b7-587">Vlastnost musí mít metodu Setter, getter nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-587">A property must have a setter, a getter, or both.</span></span> <span data-ttu-id="1f6b7-588">V sestavení jsou implementovány jako speciální metody, což znamená, že se zobrazí jako samostatné metody (getter má název `get` \_ *PropertyName* a metoda Setter je `set` \_ *PropertyName*) označená jako `SpecialName` v metadatech sestavení.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-588">In an assembly, these are implemented as special methods, which means that they will appear as separate methods (the getter is named `get`\_*propertyname* and the setter is `set`\_*propertyname*) marked as `SpecialName` in the assembly's metadata.</span></span> <span data-ttu-id="1f6b7-589">Kompilátor jazyka C# toto pravidlo vynutil automaticky, aniž by bylo nutné použít <xref:System.CLSCompliantAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-589">The C# compiler enforces this rule automatically without the need to apply the <xref:System.CLSCompliantAttribute> attribute.</span></span>

* <span data-ttu-id="1f6b7-590">Typ vlastnosti je návratový typ vlastnosti getter a poslední argument metody setter.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-590">A property's type is the return type of the property getter and the last argument of the setter.</span></span> <span data-ttu-id="1f6b7-591">Tyto typy musí být kompatibilní se specifikací CLS a argumenty nelze přiřadit vlastnost odkazem (to znamená, že nemohou být spravovány ukazateli).</span><span class="sxs-lookup"><span data-stu-id="1f6b7-591">These types must be CLS compliant, and arguments cannot be assigned to the property by reference (that is, they cannot be managed pointers).</span></span>

* <span data-ttu-id="1f6b7-592">Pokud má vlastnost metodu Getter i setter, musí obě být virtuální, obojí i obě instance.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-592">If a property has both a getter and a setter, they must both be virtual, both static, or both instance.</span></span> <span data-ttu-id="1f6b7-593">Kompilátor jazyka C# automaticky vynutil toto pravidlo prostřednictvím syntaxe definice vlastností.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-593">The C# compiler automatically enforces this rule through property definition syntax.</span></span>

### <a name="events"></a><span data-ttu-id="1f6b7-594">Události</span><span class="sxs-lookup"><span data-stu-id="1f6b7-594">Events</span></span>

<span data-ttu-id="1f6b7-595">Událost je definována podle jejího názvu a typu.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-595">An event is defined by its name and its type.</span></span> <span data-ttu-id="1f6b7-596">Typ události je delegát, který se používá k označení události.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-596">The event type is a delegate that is used to indicate the event.</span></span> <span data-ttu-id="1f6b7-597">Například `DbConnection.StateChange` událost je typu `StateChangeEventHandler` .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-597">For example, the `DbConnection.StateChange` event is of type `StateChangeEventHandler`.</span></span> <span data-ttu-id="1f6b7-598">Kromě samotné události představují implementaci události tři metody s názvy založenými na názvu události a jsou označeny jako `SpecialName` v metadatech sestavení:</span><span class="sxs-lookup"><span data-stu-id="1f6b7-598">In addition to the event itself, three methods with names based on the event name provide the event's implementation and are marked as `SpecialName` in the assembly's metadata:</span></span>

* <span data-ttu-id="1f6b7-599">Metoda pro přidání obslužné rutiny události s názvem `add` _*EventName*.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-599">A method for adding an event handler, named `add`_*EventName*.</span></span> <span data-ttu-id="1f6b7-600">Například metoda odběru události pro `DbConnection.StateChange` událost je pojmenována `add_StateChange` .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-600">For example, the event subscription method for the `DbConnection.StateChange` event is named `add_StateChange`.</span></span>

* <span data-ttu-id="1f6b7-601">Metoda pro odebrání obslužné rutiny události s názvem `remove` _*EventName*.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-601">A method for removing an event handler, named `remove`_*EventName*.</span></span> <span data-ttu-id="1f6b7-602">Například metoda odebrání `DbConnection.StateChange` události je pojmenována `remove_StateChange` .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-602">For example, the removal method for the `DbConnection.StateChange` event is named `remove_StateChange`.</span></span>

* <span data-ttu-id="1f6b7-603">Metoda pro indikaci, že došlo k události s názvem `raise` \_ *EventName*.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-603">A method for indicating that the event has occurred, named `raise`\_*EventName*.</span></span>

> [!NOTE]
> <span data-ttu-id="1f6b7-604">Většina pravidel specifikace CLS (Common Language Specification) týkajících se událostí je implementována kompilátory jazyka a jsou transparentní pro vývojáře komponent.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-604">Most of the Common Language Specification's rules regarding events are implemented by language compilers and are transparent to component developers.</span></span>

<span data-ttu-id="1f6b7-605">Metody pro přidání, odebrání a vyvolání události musí mít stejnou přístupnost.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-605">The methods for adding, removing, and raising the event must have the same accessibility.</span></span> <span data-ttu-id="1f6b7-606">Musí také být všechny statické, instance nebo virtuální.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-606">They must also all be static, instance, or virtual.</span></span> <span data-ttu-id="1f6b7-607">Metody pro přidání a odebrání události mají jeden parametr, jehož typ je typ delegáta události.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-607">The methods for adding and removing an event have one parameter whose type is the event delegate type.</span></span> <span data-ttu-id="1f6b7-608">Metody Add a Remove musí být buď přítomné, nebo obě chybět.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-608">The add and remove methods must both be present or both be absent.</span></span>

<span data-ttu-id="1f6b7-609">Následující příklad definuje třídu kompatibilní se specifikací CLS s názvem `Temperature` , která vyvolá `TemperatureChanged` událost, pokud změna teploty mezi dvěma čteními se rovná nebo překračuje prahovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-609">The following example defines a CLS-compliant class named `Temperature` that raises a `TemperatureChanged` event if the change in temperature between two readings equals or exceeds a threshold value.</span></span> <span data-ttu-id="1f6b7-610">`Temperature`Třída explicitně definuje `raise_TemperatureChanged` metodu, aby mohla selektivně provádět obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-610">The `Temperature` class explicitly defines a `raise_TemperatureChanged` method so that it can selectively execute event handlers.</span></span>

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

### <a name="overloads"></a><span data-ttu-id="1f6b7-611">Přetížení</span><span class="sxs-lookup"><span data-stu-id="1f6b7-611">Overloads</span></span>

<span data-ttu-id="1f6b7-612">Specifikace CLS (Common Language Specification) ukládá následující požadavky na přetížené členy:</span><span class="sxs-lookup"><span data-stu-id="1f6b7-612">The Common Language Specification imposes the following requirements on overloaded members:</span></span>

* <span data-ttu-id="1f6b7-613">Členy mohou být přetíženy na základě počtu parametrů a typu libovolného parametru.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-613">Members can be overloaded based on the number of parameters and the type of any parameter.</span></span> <span data-ttu-id="1f6b7-614">Konvence volání, návratový typ, vlastní modifikátory použité pro metodu nebo její parametr a zda jsou parametry předány hodnotou nebo odkazem, se nepovažují za rozdíl mezi přetíženími.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-614">Calling convention, return type, custom modifiers applied to the method or its parameter, and whether parameters are passed by value or by reference are not considered when differentiating between overloads.</span></span> <span data-ttu-id="1f6b7-615">Příklad naleznete v kódu pro požadavek, aby názvy musí být jedinečné v rámci oboru v části [konvence pojmenování](#naming-conventions) .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-615">For an example, see the code for the requirement that names must be unique within a scope in the [Naming conventions](#naming-conventions) section.</span></span>

* <span data-ttu-id="1f6b7-616">Pouze vlastnosti a metody mohou být přetíženy.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-616">Only properties and methods can be overloaded.</span></span> <span data-ttu-id="1f6b7-617">Pole a události nemohou být přetíženy.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-617">Fields and events cannot be overloaded.</span></span>

* <span data-ttu-id="1f6b7-618">Obecné metody mohou být přetíženy na základě počtu jejich obecných parametrů.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-618">Generic methods can be overloaded based on the number of their generic parameters.</span></span>

> [!NOTE]
> <span data-ttu-id="1f6b7-619">`op_Explicit`Operátory a `op_Implicit` jsou výjimky z pravidla, které vrací hodnotu, není považována za součást signatury metody pro řešení přetížení.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-619">The `op_Explicit` and `op_Implicit` operators are exceptions to the rule that return value is not considered part of a method signature for overload resolution.</span></span> <span data-ttu-id="1f6b7-620">Tyto dva operátory mohou být přetíženy v závislosti na jejich parametrech a jejich návratové hodnotě.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-620">These two operators can be overloaded based on both their parameters and their return value.</span></span>

### <a name="exceptions"></a><span data-ttu-id="1f6b7-621">Výjimky</span><span class="sxs-lookup"><span data-stu-id="1f6b7-621">Exceptions</span></span>

<span data-ttu-id="1f6b7-622">Objekty výjimky musí být odvozeny od třídy [System. Exception](xref:System.Exception) nebo z jiného typu odvozeného od `System.Exception` .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-622">Exception objects must derive from [System.Exception](xref:System.Exception) or from another type derived from `System.Exception`.</span></span> <span data-ttu-id="1f6b7-623">Následující příklad ukazuje chybu kompilátoru, která je výsledkem použití vlastní třídy s názvem `ErrorClass` pro zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-623">The following example illustrates the compiler error that results when a custom class named `ErrorClass` is used for exception handling.</span></span>

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

<span data-ttu-id="1f6b7-624">Chcete-li tuto chybu opravit, `ErrorClass` Třída musí dědit z `System.Exception` .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-624">To correct this error, the `ErrorClass` class must inherit from `System.Exception`.</span></span> <span data-ttu-id="1f6b7-625">Kromě toho musí být vlastnost zprávy přepsána.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-625">In addition, the Message property must be overridden.</span></span> <span data-ttu-id="1f6b7-626">Následující příklad opravuje tyto chyby k definování `ErrorClass` třídy, která je kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-626">The following example corrects these errors to define an `ErrorClass` class that is CLS-compliant.</span></span>

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

### <a name="attributes"></a><span data-ttu-id="1f6b7-627">Atributy</span><span class="sxs-lookup"><span data-stu-id="1f6b7-627">Attributes</span></span>

<span data-ttu-id="1f6b7-628">Sestavení rozhraní In.NET, vlastní atributy poskytují rozšiřitelný mechanismus pro ukládání vlastních atributů a načítání metadat o programovacích objektech, jako jsou sestavení, typy, členy a parametry metody.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-628">In.NET Framework assemblies, custom attributes provide an extensible mechanism for storing custom attributes and retrieving metadata about programming objects, such as assemblies, types, members, and method parameters.</span></span> <span data-ttu-id="1f6b7-629">Vlastní atributy musí být odvozeny od typu [System. Attribute](xref:System.Attribute) nebo z typu odvozeného z `System.Attribute` .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-629">Custom attributes must derive from [System.Attribute](xref:System.Attribute) or from a type derived from `System.Attribute`.</span></span>

<span data-ttu-id="1f6b7-630">V následujícím příkladu je toto pravidlo porušeno.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-630">The following example violates this rule.</span></span> <span data-ttu-id="1f6b7-631">Definuje `NumericAttribute` třídu, která není odvozena z `System.Attribute` .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-631">It defines a `NumericAttribute` class that does not derive from `System.Attribute`.</span></span> <span data-ttu-id="1f6b7-632">Všimněte si, že chyba kompilátoru je výsledkem pouze v případě, že je použit atribut, který není kompatibilní se specifikací CLS, nikoli při definování třídy.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-632">Note that a compiler error results only when the non-CLS-compliant attribute is applied, not when the class is defined.</span></span>

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

<span data-ttu-id="1f6b7-633">Konstruktor nebo vlastnosti atributu kompatibilního se specifikací CLS mohou vystavovat pouze následující typy:</span><span class="sxs-lookup"><span data-stu-id="1f6b7-633">The constructor or the properties of a CLS-compliant attribute can expose only the following types:</span></span>

* [<span data-ttu-id="1f6b7-634">Logická hodnota</span><span class="sxs-lookup"><span data-stu-id="1f6b7-634">Boolean</span></span>](xref:System.Boolean)

* [<span data-ttu-id="1f6b7-635">Bytové</span><span class="sxs-lookup"><span data-stu-id="1f6b7-635">Byte</span></span>](xref:System.Byte)

* [<span data-ttu-id="1f6b7-636">Char</span><span class="sxs-lookup"><span data-stu-id="1f6b7-636">Char</span></span>](xref:System.Char)

* [<span data-ttu-id="1f6b7-637">Klepat</span><span class="sxs-lookup"><span data-stu-id="1f6b7-637">Double</span></span>](xref:System.Double)

* [<span data-ttu-id="1f6b7-638">Int16</span><span class="sxs-lookup"><span data-stu-id="1f6b7-638">Int16</span></span>](xref:System.Int16)

* [<span data-ttu-id="1f6b7-639">Int32</span><span class="sxs-lookup"><span data-stu-id="1f6b7-639">Int32</span></span>](xref:System.Int32)

* [<span data-ttu-id="1f6b7-640">Int64</span><span class="sxs-lookup"><span data-stu-id="1f6b7-640">Int64</span></span>](xref:System.Int64)

* [<span data-ttu-id="1f6b7-641">Single</span><span class="sxs-lookup"><span data-stu-id="1f6b7-641">Single</span></span>](xref:System.Single)

* [<span data-ttu-id="1f6b7-642">Řetězec</span><span class="sxs-lookup"><span data-stu-id="1f6b7-642">String</span></span>](xref:System.String)

* [<span data-ttu-id="1f6b7-643">Typ</span><span class="sxs-lookup"><span data-stu-id="1f6b7-643">Type</span></span>](xref:System.Type)

* <span data-ttu-id="1f6b7-644">Jakýkoli typ výčtu, jehož základní typ je `Byte` , `Int16` , `Int32` nebo `Int64` .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-644">Any enumeration type whose underlying type is `Byte`, `Int16`, `Int32`, or `Int64`.</span></span>

<span data-ttu-id="1f6b7-645">Následující příklad definuje `DescriptionAttribute` třídu, která je odvozena z [atributu](xref:System.Attribute).</span><span class="sxs-lookup"><span data-stu-id="1f6b7-645">The following example defines a `DescriptionAttribute` class that derives from [Attribute](xref:System.Attribute).</span></span> <span data-ttu-id="1f6b7-646">Konstruktor třídy má parametr typu `Descriptor` , takže třída není kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-646">The class constructor has a parameter of type `Descriptor`, so the class is not CLS-compliant.</span></span> <span data-ttu-id="1f6b7-647">Všimněte si, že kompilátor jazyka C# generuje upozornění, ale úspěšně zkompiluje.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-647">Note that the C# compiler emits a warning but compiles successfully.</span></span>

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

## <a name="the-clscompliantattribute-attribute"></a><span data-ttu-id="1f6b7-648">Atribut CLSCompliantAttribute</span><span class="sxs-lookup"><span data-stu-id="1f6b7-648">The CLSCompliantAttribute attribute</span></span>

<span data-ttu-id="1f6b7-649">Atribut [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) slouží k označení, zda prvek programu vyhovuje specifikaci CLS (Common Language Specification).</span><span class="sxs-lookup"><span data-stu-id="1f6b7-649">The [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute is used to indicate whether a program element complies with the Common Language Specification.</span></span> <span data-ttu-id="1f6b7-650">`CLSCompliantAttribute.CLSCompliantAttribute(Boolean)`Konstruktor obsahuje jeden povinný parametr, který je v *souladu*s, který označuje, zda je element program kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-650">The `CLSCompliantAttribute.CLSCompliantAttribute(Boolean)` constructor includes a single required parameter, *isCompliant*, that indicates whether the program element is CLS-compliant.</span></span>

<span data-ttu-id="1f6b7-651">V době kompilace kompilátor detekuje nekompatibilní prvky, které se považují za kompatibilní se specifikací CLS, a vygeneruje upozornění.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-651">At compile time, the compiler detects non-compliant elements that are presumed to be CLS-compliant and emits a warning.</span></span> <span data-ttu-id="1f6b7-652">Kompilátor negeneruje upozornění pro typy nebo členy, které jsou explicitně deklarovány tak, že nejsou kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-652">The compiler does not emit warnings for types or members that are explicitly declared to be non-compliant.</span></span>

<span data-ttu-id="1f6b7-653">Vývojáři komponent mohou použít `CLSCompliantAttribute` atribut dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="1f6b7-653">Component developers can use the `CLSCompliantAttribute` attribute in two ways:</span></span>

* <span data-ttu-id="1f6b7-654">Pro definování částí veřejného rozhraní vystaveného komponentou, která je kompatibilní se specifikací CLS, a částí, které nejsou kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-654">To define the parts of the public interface exposed by a component that are CLS-compliant and the parts that are not CLS-compliant.</span></span> <span data-ttu-id="1f6b7-655">Když je atribut použit k označení určitých prvků programu jako kompatibilní se specifikací CLS, jeho použití zaručuje, že tyto prvky jsou přístupné ze všech jazyků a nástrojů, které cílí na .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-655">When the attribute is used to mark particular program elements as CLS-compliant, its use guarantees that those elements are accessible from all languages and tools that target the .NET Framework.</span></span>

* <span data-ttu-id="1f6b7-656">Aby bylo zajištěno, že veřejné rozhraní knihovny součástí zpřístupňuje pouze prvky programu, které jsou kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-656">To ensure that the component library's public interface exposes only program elements that are CLS-compliant.</span></span> <span data-ttu-id="1f6b7-657">Pokud prvky nejsou kompatibilní se specifikací CLS, kompilátory většinou vystaví upozornění.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-657">If elements are not CLS-compliant, compilers will generally issue a warning.</span></span>

> [!WARNING]
> <span data-ttu-id="1f6b7-658">V některých případech vynutily jazykové kompilátory pravidla kompatibilní se specifikací CLS bez ohledu na to, zda `CLSCompliantAttribute` je atribut použit.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-658">In some cases, language compilers enforce CLS-compliant rules regardless of whether the `CLSCompliantAttribute` attribute is used.</span></span> <span data-ttu-id="1f6b7-659">Například definování `*static` člena v rozhraní je v rozporu s pravidlem CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-659">For example, defining a `*static` member in an interface violates a CLS rule.</span></span> <span data-ttu-id="1f6b7-660">Pokud však definujete `*static` člena v rozhraní, kompilátor jazyka C# zobrazí chybovou zprávu a aplikace nebude zkompilována.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-660">However, if you define a `*static` member in an interface, the C# compiler displays an error message and fails to compile the app.</span></span>

<span data-ttu-id="1f6b7-661">`CLSCompliantAttribute`Atribut je označen atributem [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) , který má hodnotu `AttributeTargets.All` .</span><span class="sxs-lookup"><span data-stu-id="1f6b7-661">The `CLSCompliantAttribute` attribute is marked with an [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) attribute that has a value of `AttributeTargets.All`.</span></span> <span data-ttu-id="1f6b7-662">Tato hodnota umožňuje použít `CLSCompliantAttribute` atribut na jakýkoli prvek programu, včetně sestavení, modulů, typů (tříd, struktur, výčtů, rozhraní a delegátů), členů typu (konstruktory, metody, vlastnosti, pole a události), parametrů, obecných parametrů a návratových hodnot.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-662">This value allows you to apply the `CLSCompliantAttribute` attribute to any program element, including assemblies, modules, types (classes, structures, enumerations, interfaces, and delegates), type members (constructors, methods, properties, fields, and events), parameters, generic parameters, and return values.</span></span> <span data-ttu-id="1f6b7-663">Nicméně v praxi byste měli použít atribut pouze pro sestavení, typy a členy typu.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-663">However, in practice, you should apply the attribute only to assemblies, types, and type members.</span></span> <span data-ttu-id="1f6b7-664">V opačném případě kompilátory ignorují atribut a pokračují v generování upozornění kompilátoru pokaždé, když narazí na nekompatibilní parametr, obecný parametr nebo návratovou hodnotu ve veřejném rozhraní knihovny.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-664">Otherwise, compilers ignore the attribute and continue to generate compiler warnings whenever they encounter a non-compliant parameter, generic parameter, or return value in your library's public interface.</span></span>

<span data-ttu-id="1f6b7-665">Hodnota `CLSCompliantAttribute` atributu je děděna z obsažených prvků programu.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-665">The value of the `CLSCompliantAttribute` attribute is inherited by contained program elements.</span></span> <span data-ttu-id="1f6b7-666">Například pokud je sestavení označeno jako kompatibilní se specifikací CLS, jeho typy jsou také kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-666">For example, if an assembly is marked as CLS-compliant, its types are also CLS-compliant.</span></span> <span data-ttu-id="1f6b7-667">Pokud je typ označený jako kompatibilní se specifikací CLS, jeho vnořené typy a členy jsou také kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-667">If a type is marked as CLS-compliant, its nested types and members are also CLS-compliant.</span></span>

<span data-ttu-id="1f6b7-668">Zděděné dodržování předpisů lze explicitně přepsat použitím `CLSCompliantAttribute` atributu na obsažený prvek programu.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-668">You can explicitly override the inherited compliance by applying the `CLSCompliantAttribute` attribute to a contained program element.</span></span> <span data-ttu-id="1f6b7-669">Například můžete použít `CLSCompliantAttribute` atribut s hodnotou *nedodržující* předpisy `false` pro definování nekompatibilního typu v vyhovujícím sestavení a můžete použít atribut s hodnotou *nedodržující* předpisy `true` k definování kompatibilního typu v sestavení, které nedodržuje předpisy.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-669">For example, you can use the `CLSCompliantAttribute` attribute with an *isCompliant* value of `false` to define a non-compliant type in a compliant assembly, and you can use the attribute with an *isCompliant* value of `true` to define a compliant type in a non-compliant assembly.</span></span> <span data-ttu-id="1f6b7-670">Můžete také definovat nekompatibilní členy v typu, který odpovídá.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-670">You can also define non-compliant members in a compliant type.</span></span> <span data-ttu-id="1f6b7-671">Nevyhovující typ ale nemůže mít odpovídající členy, takže nemůžete použít atribut s hodnotou *neodpovídající* hodnotě `true` pro přepsání dědičnosti z nekompatibilního typu.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-671">However, a non-compliant type cannot have compliant members, so you cannot use the attribute with an *isCompliant* value of `true` to override inheritance from a non-compliant type.</span></span>

<span data-ttu-id="1f6b7-672">Při vývoji komponent byste vždy měli použít `CLSCompliantAttribute` atribut k označení, zda vaše sestavení, jeho typy a jeho členové jsou kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-672">When you are developing components, you should always use the `CLSCompliantAttribute` attribute to indicate whether your assembly, its types, and its members are CLS-compliant.</span></span>

<span data-ttu-id="1f6b7-673">Vytvoření součástí odpovídajících specifikaci CLS:</span><span class="sxs-lookup"><span data-stu-id="1f6b7-673">To create CLS-compliant components:</span></span>

1. <span data-ttu-id="1f6b7-674">Použijte `CLSCompliantAttribute` k označení sestavení jako kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-674">Use the `CLSCompliantAttribute` to mark you assembly as CLS-compliant.</span></span>

2. <span data-ttu-id="1f6b7-675">Označte všechny veřejně vystavené typy v sestavení, které nejsou kompatibilní se specifikací CLS, jako nevyhovující.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-675">Mark any publicly exposed types in the assembly that are not CLS-compliant as non-compliant.</span></span>

3. <span data-ttu-id="1f6b7-676">Označte všechny veřejně vystavené členy v typech kompatibilních se specifikací CLS jako nevyhovující.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-676">Mark any publicly exposed members in CLS-compliant types as non-compliant.</span></span>

4. <span data-ttu-id="1f6b7-677">Poskytněte alternativu kompatibilní se specifikací CLS pro členy, které nedodržují specifikaci CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-677">Provide a CLS-compliant alternative for non-CLS-compliant members.</span></span>

<span data-ttu-id="1f6b7-678">Pokud jste úspěšně označili všechny typy a členy, které nedodržují předpisy, kompilátor by neměl generovat žádná upozornění, která nedodržují předpisy.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-678">If you've successfully marked all your non-compliant types and members, your compiler should not emit any non-compliance warnings.</span></span> <span data-ttu-id="1f6b7-679">Měli byste však určit, kteří členové nejsou kompatibilní se specifikací CLS, a seznamte se s alternativami kompatibilními se specifikací CLS v dokumentaci k produktu.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-679">However, you should indicate which members are not CLS-compliant and list their CLS-compliant alternatives in your product documentation.</span></span>

<span data-ttu-id="1f6b7-680">Následující příklad používá `CLSCompliantAttribute` atribut k definování sestavení kompatibilního se specifikací CLS a typu, `CharacterUtilities` , který má dva členy nekompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-680">The following example uses the `CLSCompliantAttribute` attribute to define a CLS-compliant assembly and a type, `CharacterUtilities`, that has two non-CLS-compliant members.</span></span> <span data-ttu-id="1f6b7-681">Vzhledem k tomu, že oba členy jsou označeny `CLSCompliant(false)` atributem, kompilátor nevydá žádná upozornění.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-681">Because both members are tagged with the `CLSCompliant(false)` attribute, the compiler produces no warnings.</span></span> <span data-ttu-id="1f6b7-682">Třída také poskytuje alternativu odpovídající specifikaci CLS pro obě metody.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-682">The class also provides a CLS-compliant alternative for both methods.</span></span> <span data-ttu-id="1f6b7-683">Obvykle bychom přidali dvě přetížení do `ToUTF16` metody pro zajištění alternativ odpovídajících specifikaci CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-683">Ordinarily, we would just add two overloads to the `ToUTF16` method to provide CLS-compliant alternatives.</span></span> <span data-ttu-id="1f6b7-684">Nicméně vzhledem k tomu, že metody nemohou být přetíženy na základě návratové hodnoty, názvy metod odpovídajících specifikaci CLS se liší od názvů nevyhovujících metod.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-684">However, because methods cannot be overloaded based on return value, the names of the CLS-compliant methods are different from the names of the non-compliant methods.</span></span>

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

<span data-ttu-id="1f6b7-685">Pokud vyvíjíte aplikaci místo knihovny (tj. Pokud nezveřejňujete typy nebo členy, které mohou být spotřebovány jinými vývojáři aplikací), bude kompatibilita CLS prvků programu, které vaše aplikace spotřebovává, odpovídat pouze v případě, že je váš jazyk nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-685">If you are developing an app rather than a library (that is, if you aren't exposing types or members that can be consumed by other app developers), the CLS compliance of the program elements that your app consumes are of interest only if your language does not support them.</span></span> <span data-ttu-id="1f6b7-686">V takovém případě kompilátor jazyka vygeneruje chybu, pokud se pokusíte použít element, který není kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-686">In that case, your language compiler will generate an error when you try to use a non-CLS-compliant element.</span></span>

## <a name="cross-language-interoperability"></a><span data-ttu-id="1f6b7-687">Vzájemná funkční spolupráce mezi jazyky</span><span class="sxs-lookup"><span data-stu-id="1f6b7-687">Cross-Language Interoperability</span></span>

<span data-ttu-id="1f6b7-688">Jazyková nezávislost má několik možných významů.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-688">Language independence has a number of possible meanings.</span></span> <span data-ttu-id="1f6b7-689">Jeden z nich zahrnuje plynulé využívání typů napsaných v jednom jazyce z aplikace napsané v jiném jazyce.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-689">One meaning involves seamlessly consuming types written in one language from an app written in another language.</span></span> <span data-ttu-id="1f6b7-690">Druhý význam, který je hlavním cílem tohoto článku, zahrnuje sloučení kódu napsaného ve více jazycích do jediného sestavení rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-690">A second meaning, which is the focus of this article, involves combining code written in multiple languages into a single .NET Framework assembly.</span></span>

<span data-ttu-id="1f6b7-691">Následující příklad znázorňuje interoperabilitu mezi jazyky vytvořením knihovny tříd s názvem Utilities.dll, která obsahuje dvě třídy `NumericLib` a `StringLib`.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-691">The following example illustrates cross-language interoperability by creating a class library named Utilities.dll that includes two classes, `NumericLib` and `StringLib`.</span></span> <span data-ttu-id="1f6b7-692">Třída `NumericLib` je napsána v jazyce C# a třída `StringLib` je napsána v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-692">The `NumericLib` class is written in C#, and the `StringLib` class is written in Visual Basic.</span></span> <span data-ttu-id="1f6b7-693">Zde je zdrojový kód pro `StringUtil.vb` , který obsahuje jednoho člena, `ToTitleCase` ve své `StringLib` třídě.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-693">Here's the source code for `StringUtil.vb`, which includes a single member, `ToTitleCase`, in its `StringLib` class.</span></span>

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

<span data-ttu-id="1f6b7-694">Zde je zdrojový kód pro NumberUtil.cs, který definuje třídu `NumericLib` se dvěma členy `IsEven` a `NearZero`.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-694">Here's the source code for NumberUtil.cs, which defines a `NumericLib` class that has two members, `IsEven` and `NearZero`.</span></span>

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

<span data-ttu-id="1f6b7-695">Chcete-li zabalit dvě třídy do jednoho sestavení, musíte je zkompilovat do modulů.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-695">To package the two classes in a single assembly, you must compile them into modules.</span></span> <span data-ttu-id="1f6b7-696">Pro kompilaci zdrojového kódu jazyka Visual Basic do modulu použijte tento příkaz:</span><span class="sxs-lookup"><span data-stu-id="1f6b7-696">To compile the Visual Basic source code file into a module, use this command:</span></span>

```console
vbc /t:module StringUtil.vb
```

<span data-ttu-id="1f6b7-697">Pro kompilaci zdrojového kódu jazyka C# do modulu použijte tento příkaz:</span><span class="sxs-lookup"><span data-stu-id="1f6b7-697">To compile the C# source code file into a module, use this command:</span></span>

```console
csc /t:module NumberUtil.cs
```

<span data-ttu-id="1f6b7-698">Pak použijete nástroj Link (Link. exe) ke kompilaci dvou modulů do sestavení:</span><span class="sxs-lookup"><span data-stu-id="1f6b7-698">You then use the Link tool (Link.exe) to compile the two modules into an assembly:</span></span>

```console
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll
```

<span data-ttu-id="1f6b7-699">Následující příklad následně volá metody `NumericLib.NearZero` a `StringLib.ToTitleCase`.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-699">The following example then calls the `NumericLib.NearZero` and `StringLib.ToTitleCase` methods.</span></span> <span data-ttu-id="1f6b7-700">Kód jazyka Visual Basic i kód jazyka C# může přistupovat k metodám v obou třídách.</span><span class="sxs-lookup"><span data-stu-id="1f6b7-700">Note that both the Visual Basic code and the C# code are able to access the methods in both classes.</span></span>

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

<span data-ttu-id="1f6b7-701">Pro kompilaci kódu jazyka Visual Basic použijte tento příkaz:</span><span class="sxs-lookup"><span data-stu-id="1f6b7-701">To compile the Visual Basic code, use this command:</span></span>

```console
vbc example.vb /r:UtilityLib.dll
```

<span data-ttu-id="1f6b7-702">Chcete-li kompilovat v jazyce C#, změňte název kompilátoru z Vbc na CSC a změňte příponu souboru z. vb na. cs:</span><span class="sxs-lookup"><span data-stu-id="1f6b7-702">To compile with C#, change the name of the compiler from vbc to csc, and change the file extension from .vb to .cs:</span></span>

```console
csc example.cs /r:UtilityLib.dll
```
