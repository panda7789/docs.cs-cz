---
title: Co je nového v C# 7.3
description: Přehled nových funkcí v C# 7.3
ms.date: 05/16/2018
ms.openlocfilehash: ba4cea302d91b395e88940d087fcaed306920840
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74204557"
---
# <a name="whats-new-in-c-73"></a><span data-ttu-id="64cea-103">Co je nového v C# 7.3</span><span class="sxs-lookup"><span data-stu-id="64cea-103">What's new in C# 7.3</span></span>

<span data-ttu-id="64cea-104">Existují dvě hlavní témata verze Jazyka C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="64cea-104">There are two main themes to the C# 7.3 release.</span></span> <span data-ttu-id="64cea-105">Jeden motiv poskytuje funkce, které umožňují bezpečný kód být stejně výkonný jako nebezpečný kód.</span><span class="sxs-lookup"><span data-stu-id="64cea-105">One theme provides features that enable safe code to be as performant as unsafe code.</span></span> <span data-ttu-id="64cea-106">Druhý motiv poskytuje přírůstková vylepšení existujících funkcí.</span><span class="sxs-lookup"><span data-stu-id="64cea-106">The second theme provides incremental improvements to existing features.</span></span> <span data-ttu-id="64cea-107">Kromě toho byly přidány nové možnosti kompilátoru v této verzi.</span><span class="sxs-lookup"><span data-stu-id="64cea-107">In addition, new compiler options were added in this release.</span></span>

<span data-ttu-id="64cea-108">Následující nové funkce podporují téma lepšího výkonu pro bezpečný kód:</span><span class="sxs-lookup"><span data-stu-id="64cea-108">The following new features support the theme of better performance for safe code:</span></span>

- <span data-ttu-id="64cea-109">K pevným polím můžete přistupovat bez připnutí.</span><span class="sxs-lookup"><span data-stu-id="64cea-109">You can access fixed fields without pinning.</span></span>
- <span data-ttu-id="64cea-110">Můžete znovu `ref` přiřadit místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="64cea-110">You can reassign `ref` local variables.</span></span>
- <span data-ttu-id="64cea-111">Inicializátory `stackalloc` můžete použít na polích.</span><span class="sxs-lookup"><span data-stu-id="64cea-111">You can use initializers on `stackalloc` arrays.</span></span>
- <span data-ttu-id="64cea-112">Příkazy `fixed` můžete použít s libovolným typem, který podporuje vzorek.</span><span class="sxs-lookup"><span data-stu-id="64cea-112">You can use `fixed` statements with any type that supports a pattern.</span></span>
- <span data-ttu-id="64cea-113">Můžete použít další obecná omezení.</span><span class="sxs-lookup"><span data-stu-id="64cea-113">You can use additional generic constraints.</span></span>

<span data-ttu-id="64cea-114">Pro existující funkce byla provedena následující vylepšení:</span><span class="sxs-lookup"><span data-stu-id="64cea-114">The following enhancements were made to existing features:</span></span>

- <span data-ttu-id="64cea-115">Můžete testovat `==` `!=` a s typy řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="64cea-115">You can test `==` and `!=` with tuple types.</span></span>
- <span data-ttu-id="64cea-116">Proměnné výrazu můžete použít na více umístěních.</span><span class="sxs-lookup"><span data-stu-id="64cea-116">You can use expression variables in more locations.</span></span>
- <span data-ttu-id="64cea-117">Atributy můžete připojit k záložnímu poli automaticky implementovaných vlastností.</span><span class="sxs-lookup"><span data-stu-id="64cea-117">You may attach attributes to the backing field of auto-implemented properties.</span></span>
- <span data-ttu-id="64cea-118">Bylo vylepšeno rozlišení `in` metody, pokud se argumenty liší.</span><span class="sxs-lookup"><span data-stu-id="64cea-118">Method resolution when arguments differ by `in` has been improved.</span></span>
- <span data-ttu-id="64cea-119">Řešení přetížení má nyní méně nejednoznačných případů.</span><span class="sxs-lookup"><span data-stu-id="64cea-119">Overload resolution now has fewer ambiguous cases.</span></span>

<span data-ttu-id="64cea-120">Nové možnosti kompilátoru jsou:</span><span class="sxs-lookup"><span data-stu-id="64cea-120">The new compiler options are:</span></span>

- <span data-ttu-id="64cea-121">`-publicsign`povolení podepisování sestav pomocí softwaru s otevřeným zdrojovým kódem (OSS).</span><span class="sxs-lookup"><span data-stu-id="64cea-121">`-publicsign` to enable Open Source Software (OSS) signing of assemblies.</span></span>
- <span data-ttu-id="64cea-122">`-pathmap`pro vytvoření mapování zdrojových adresářů.</span><span class="sxs-lookup"><span data-stu-id="64cea-122">`-pathmap` to provide a mapping for source directories.</span></span>

<span data-ttu-id="64cea-123">Zbývající část tohoto článku obsahuje podrobnosti a odkazy na další informace o každé z vylepšení.</span><span class="sxs-lookup"><span data-stu-id="64cea-123">The remainder of this article provides details and links to learn more about each of the improvements.</span></span> <span data-ttu-id="64cea-124">Tyto funkce můžete prozkoumat ve `dotnet try` vašem prostředí pomocí globálního nástroje:</span><span class="sxs-lookup"><span data-stu-id="64cea-124">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="64cea-125">Nainstalujte globální nástroj [dotnet-try.](https://github.com/dotnet/try/blob/master/README.md#setup)</span><span class="sxs-lookup"><span data-stu-id="64cea-125">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="64cea-126">Klonovat úložiště [dotnet/try-samples.](https://github.com/dotnet/try-samples)</span><span class="sxs-lookup"><span data-stu-id="64cea-126">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="64cea-127">Nastavte aktuální adresář do podadresáře *csharp7* pro úložiště *try-samples.*</span><span class="sxs-lookup"><span data-stu-id="64cea-127">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="64cea-128">Spusťte `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="64cea-128">Run `dotnet try`.</span></span>

## <a name="enabling-more-efficient-safe-code"></a><span data-ttu-id="64cea-129">Povolení efektivnějšího bezpečného kódu</span><span class="sxs-lookup"><span data-stu-id="64cea-129">Enabling more efficient safe code</span></span>

<span data-ttu-id="64cea-130">Měli byste být schopni napsat kód Jazyka C# bezpečně, který provádí, stejně jako nebezpečný kód.</span><span class="sxs-lookup"><span data-stu-id="64cea-130">You should be able to write C# code safely that performs as well as unsafe code.</span></span> <span data-ttu-id="64cea-131">Bezpečný kód zabraňuje třídy chyb, jako je například přetečení vyrovnávací paměti, zbloudilé ukazatele a další chyby přístupu do paměti.</span><span class="sxs-lookup"><span data-stu-id="64cea-131">Safe code avoids classes of errors, such as buffer overruns, stray pointers, and other memory access errors.</span></span> <span data-ttu-id="64cea-132">Tyto nové funkce rozšiřují možnosti ověřitelného bezpečného kódu.</span><span class="sxs-lookup"><span data-stu-id="64cea-132">These new features expand the capabilities of verifiable safe code.</span></span> <span data-ttu-id="64cea-133">Snažte se psát více kódu pomocí bezpečných konstrukcí.</span><span class="sxs-lookup"><span data-stu-id="64cea-133">Strive to write more of your code using safe constructs.</span></span> <span data-ttu-id="64cea-134">Tyto funkce to usnadňují.</span><span class="sxs-lookup"><span data-stu-id="64cea-134">These features make that easier.</span></span>

### <a name="indexing-fixed-fields-does-not-require-pinning"></a><span data-ttu-id="64cea-135">Indexování `fixed` polí nevyžaduje připnutí</span><span class="sxs-lookup"><span data-stu-id="64cea-135">Indexing `fixed` fields does not require pinning</span></span>

<span data-ttu-id="64cea-136">Vezměme si tuto strukturu:</span><span class="sxs-lookup"><span data-stu-id="64cea-136">Consider this struct:</span></span>

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

<span data-ttu-id="64cea-137">V dřívějších verzích jazyka C# je třeba připnout proměnnou pro `myFixedField`přístup k jednomu z celá čísla, které jsou součástí .</span><span class="sxs-lookup"><span data-stu-id="64cea-137">In earlier versions of C#, you needed to pin a variable to access one of the integers that are part of `myFixedField`.</span></span> <span data-ttu-id="64cea-138">Nyní se zkompiluje následující `p` kód bez `fixed` připnutí proměnné uvnitř samostatného příkazu:</span><span class="sxs-lookup"><span data-stu-id="64cea-138">Now, the following code compiles without pinning the variable `p` inside a separate `fixed` statement:</span></span>

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        int p = s.myFixedField[5];
    }
}
```

<span data-ttu-id="64cea-139">Proměnná `p` přistupuje jeden prvek v `myFixedField`.</span><span class="sxs-lookup"><span data-stu-id="64cea-139">The variable `p` accesses one element in `myFixedField`.</span></span> <span data-ttu-id="64cea-140">Není nutné deklarovat `int*` samostatnou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="64cea-140">You don't need to declare a separate `int*` variable.</span></span> <span data-ttu-id="64cea-141">Všimněte si, `unsafe` že stále potřebujete kontext.</span><span class="sxs-lookup"><span data-stu-id="64cea-141">Note that you still need an `unsafe` context.</span></span> <span data-ttu-id="64cea-142">V dřívějších verzích jazyka C# je třeba deklarovat druhý pevný ukazatel:</span><span class="sxs-lookup"><span data-stu-id="64cea-142">In earlier versions of C#, you need to declare a second fixed pointer:</span></span>

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        fixed (int* ptr = s.myFixedField)
        {
            int p = ptr[5];
        }
    }
}
```

<span data-ttu-id="64cea-143">Další informace naleznete v článku [ `fixed` ](../language-reference/keywords/fixed-statement.md)na prohlášení .</span><span class="sxs-lookup"><span data-stu-id="64cea-143">For more information, see the article on the [`fixed` statement](../language-reference/keywords/fixed-statement.md).</span></span>

### <a name="ref-local-variables-may-be-reassigned"></a><span data-ttu-id="64cea-144">`ref`místní proměnné mohou být přeřazeny</span><span class="sxs-lookup"><span data-stu-id="64cea-144">`ref` local variables may be reassigned</span></span>

<span data-ttu-id="64cea-145">Nyní `ref` místní obyvatelé mohou být znovu přiřazeny odkazovat na různé instance po inicializování.</span><span class="sxs-lookup"><span data-stu-id="64cea-145">Now, `ref` locals may be reassigned to refer to different instances after being initialized.</span></span> <span data-ttu-id="64cea-146">Následující kód nyní zkompiluje:</span><span class="sxs-lookup"><span data-stu-id="64cea-146">The following code now compiles:</span></span>

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

<span data-ttu-id="64cea-147">Další informace naleznete v článku o [ `ref` vrácení a `ref` místní obyvatelé](../programming-guide/classes-and-structs/ref-returns.md)a článek o [`foreach`](../language-reference/keywords/foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="64cea-147">For more information, see the article on [`ref` returns and `ref` locals](../programming-guide/classes-and-structs/ref-returns.md), and the article on [`foreach`](../language-reference/keywords/foreach-in.md).</span></span>

### <a name="stackalloc-arrays-support-initializers"></a><span data-ttu-id="64cea-148">`stackalloc`pole podporují inicializátory</span><span class="sxs-lookup"><span data-stu-id="64cea-148">`stackalloc` arrays support initializers</span></span>

<span data-ttu-id="64cea-149">Při inicializaci pole jste mohli zadat hodnoty prvků v poli:</span><span class="sxs-lookup"><span data-stu-id="64cea-149">You've been able to specify the values for elements in an array when you initialize it:</span></span>

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

<span data-ttu-id="64cea-150">Nyní, že stejná syntaxe lze použít `stackalloc`na pole, která jsou deklarována s :</span><span class="sxs-lookup"><span data-stu-id="64cea-150">Now, that same syntax can be applied to arrays that are declared with `stackalloc`:</span></span>

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

<span data-ttu-id="64cea-151">Další informace naleznete v článku [ `stackalloc` operátora.](../language-reference/operators/stackalloc.md)</span><span class="sxs-lookup"><span data-stu-id="64cea-151">For more information, see the [`stackalloc` operator](../language-reference/operators/stackalloc.md) article.</span></span>

### <a name="more-types-support-the-fixed-statement"></a><span data-ttu-id="64cea-152">Prohlášení podporují `fixed` další typy</span><span class="sxs-lookup"><span data-stu-id="64cea-152">More types support the `fixed` statement</span></span>

<span data-ttu-id="64cea-153">Příkaz `fixed` podporuje omezenou sadu typů.</span><span class="sxs-lookup"><span data-stu-id="64cea-153">The `fixed` statement supported a limited set of types.</span></span> <span data-ttu-id="64cea-154">Počínaje C# 7.3, libovolný typ, který obsahuje `GetPinnableReference()` metodu, která vrací `ref T` nebo `ref readonly T` může být `fixed`.</span><span class="sxs-lookup"><span data-stu-id="64cea-154">Starting with C# 7.3, any type that contains a `GetPinnableReference()` method that returns a `ref T` or `ref readonly T` may be `fixed`.</span></span> <span data-ttu-id="64cea-155">Přidání této funkce `fixed` znamená, <xref:System.Span%601?displayProperty=nameWithType> že lze použít s a související typy.</span><span class="sxs-lookup"><span data-stu-id="64cea-155">Adding this feature means that `fixed` can be used with <xref:System.Span%601?displayProperty=nameWithType> and related types.</span></span>

<span data-ttu-id="64cea-156">Další informace naleznete [ `fixed` ](../language-reference/keywords/fixed-statement.md) v článku prohlášení v odkazu na jazyk.</span><span class="sxs-lookup"><span data-stu-id="64cea-156">For more information, see the [`fixed` statement](../language-reference/keywords/fixed-statement.md) article in the language reference.</span></span>

### <a name="enhanced-generic-constraints"></a><span data-ttu-id="64cea-157">Rozšířená obecná omezení</span><span class="sxs-lookup"><span data-stu-id="64cea-157">Enhanced generic constraints</span></span>

<span data-ttu-id="64cea-158">Nyní můžete zadat <xref:System.Enum?displayProperty=nameWithType> typ <xref:System.Delegate?displayProperty=nameWithType> nebo jako omezení základní třídy pro parametr typu.</span><span class="sxs-lookup"><span data-stu-id="64cea-158">You can now specify the type <xref:System.Enum?displayProperty=nameWithType> or <xref:System.Delegate?displayProperty=nameWithType> as base class constraints for a type parameter.</span></span>

<span data-ttu-id="64cea-159">Můžete také použít `unmanaged` nové omezení, chcete-li určit, že parametr typu musí být [neslaný typ](../language-reference/builtin-types/unmanaged-types.md)s hodnotou nesprávou, kterou nelze utnout .</span><span class="sxs-lookup"><span data-stu-id="64cea-159">You can also use the new `unmanaged` constraint, to specify that a type parameter must be a non-nullable [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span></span>

<span data-ttu-id="64cea-160">Další informace naleznete v článcích o [ `where` obecných omezeních](../language-reference/keywords/where-generic-type-constraint.md) a [omezeních parametrů typu](../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="64cea-160">For more information, see the articles on [`where` generic constraints](../language-reference/keywords/where-generic-type-constraint.md) and [constraints on type parameters](../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="64cea-161">Přidání těchto omezení do existujících typů je [nekompatibilní změna](version-update-considerations.md#incompatible-changes).</span><span class="sxs-lookup"><span data-stu-id="64cea-161">Adding these constraints to existing types is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="64cea-162">Uzavřené obecné typy již nemusí splňovat tato nová omezení.</span><span class="sxs-lookup"><span data-stu-id="64cea-162">Closed generic types may no longer meet these new constraints.</span></span>

## <a name="make-existing-features-better"></a><span data-ttu-id="64cea-163">Vylepšete stávající funkce</span><span class="sxs-lookup"><span data-stu-id="64cea-163">Make existing features better</span></span>

<span data-ttu-id="64cea-164">Druhý motiv poskytuje vylepšení funkcí v jazyce.</span><span class="sxs-lookup"><span data-stu-id="64cea-164">The second theme provides improvements to features in the language.</span></span> <span data-ttu-id="64cea-165">Tyto funkce zvyšují produktivitu při psaní jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="64cea-165">These features improve productivity when writing C#.</span></span>

### <a name="tuples-support--and-"></a><span data-ttu-id="64cea-166">Podpora n-tia `==` a`!=`</span><span class="sxs-lookup"><span data-stu-id="64cea-166">Tuples support `==` and `!=`</span></span>

<span data-ttu-id="64cea-167">C# řazené `==` kolekce `!=`členů typy nyní podporují a .</span><span class="sxs-lookup"><span data-stu-id="64cea-167">The C# tuple types now support `==` and `!=`.</span></span> <span data-ttu-id="64cea-168">Další informace naleznete v části týkající se [rovnosti](../tuples.md#equality-and-tuples) v článku [o řazených kolekcí členů](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="64cea-168">For more information, see the section covering [equality](../tuples.md#equality-and-tuples) in the article on [tuples](../tuples.md).</span></span>

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a><span data-ttu-id="64cea-169">Připojení atributů k záložním polím pro automaticky implementované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="64cea-169">Attach attributes to the backing fields for auto-implemented properties</span></span>

<span data-ttu-id="64cea-170">Tato syntaxe je nyní podporována:</span><span class="sxs-lookup"><span data-stu-id="64cea-170">This syntax is now supported:</span></span>

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

<span data-ttu-id="64cea-171">Atribut `SomeThingAboutFieldAttribute` je použit pro kompilátor generované `SomeProperty`záložní pole pro .</span><span class="sxs-lookup"><span data-stu-id="64cea-171">The attribute `SomeThingAboutFieldAttribute` is applied to the compiler generated backing field for `SomeProperty`.</span></span> <span data-ttu-id="64cea-172">Další informace naleznete v [atributy](../programming-guide/concepts/attributes/index.md) v c# programovací průvodce.</span><span class="sxs-lookup"><span data-stu-id="64cea-172">For more information, see [attributes](../programming-guide/concepts/attributes/index.md) in the C# programming guide.</span></span>

### <a name="in-method-overload-resolution-tiebreaker"></a><span data-ttu-id="64cea-173">`in`metoda řešení přetížení tiebreaker</span><span class="sxs-lookup"><span data-stu-id="64cea-173">`in` method overload resolution tiebreaker</span></span>

<span data-ttu-id="64cea-174">Při `in` přidání modifikátor argumentu by tyto dvě metody způsobit nejednoznačnost:</span><span class="sxs-lookup"><span data-stu-id="64cea-174">When the `in` argument modifier was added, these two methods would cause an ambiguity:</span></span>

```csharp
static void M(S arg);
static void M(in S arg);
```

<span data-ttu-id="64cea-175">Nyní podle hodnoty (první v předchozím příkladu) přetížení je lepší než podle referenční verze pouze pro čtení.</span><span class="sxs-lookup"><span data-stu-id="64cea-175">Now, the by value (first in the preceding example) overload is better than the by readonly reference version.</span></span> <span data-ttu-id="64cea-176">Chcete-li volat verzi s referenčním argumentem `in` jen pro čtení, musíte při volání metody zahrnout modifikátor.</span><span class="sxs-lookup"><span data-stu-id="64cea-176">To call the version with the readonly reference argument, you must include the `in` modifier when calling the method.</span></span>

> [!NOTE]
> <span data-ttu-id="64cea-177">To bylo implementováno jako oprava chyby.</span><span class="sxs-lookup"><span data-stu-id="64cea-177">This was implemented as a bug fix.</span></span> <span data-ttu-id="64cea-178">To již není nejednoznačné ani s jazykovou verzí nastavenou na "7.2".</span><span class="sxs-lookup"><span data-stu-id="64cea-178">This no longer is ambiguous even with the language version set to "7.2".</span></span>

<span data-ttu-id="64cea-179">Další informace naleznete v článku o [ `in` modifikátoru parametrů](../language-reference/keywords/in-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="64cea-179">For more information, see the article on the [`in` parameter modifier](../language-reference/keywords/in-parameter-modifier.md).</span></span>

### <a name="extend-expression-variables-in-initializers"></a><span data-ttu-id="64cea-180">Rozšířit proměnné výrazu v inicializátorech</span><span class="sxs-lookup"><span data-stu-id="64cea-180">Extend expression variables in initializers</span></span>

<span data-ttu-id="64cea-181">Syntaxe přidaná v C# `out` 7.0 povolit deklarace proměnných byla rozšířena tak, aby zahrnovala inicializátory polí, inicializátory vlastností, inicializátory konstruktérů a klauzule dotazu.</span><span class="sxs-lookup"><span data-stu-id="64cea-181">The syntax added in C# 7.0 to allow `out` variable declarations has been extended to include field initializers, property initializers, constructor initializers, and query clauses.</span></span> <span data-ttu-id="64cea-182">Umožňuje kód, například následující příklad:</span><span class="sxs-lookup"><span data-stu-id="64cea-182">It enables code such as the following example:</span></span>

```csharp
public class B
{
   public B(int i, out int j)
   {
      j = i;
   }
}

public class D : B
{
   public D(int i) : base(i, out var j)
   {
      Console.WriteLine($"The value of 'j' is {j}");
   }
}
```

### <a name="improved-overload-candidates"></a><span data-ttu-id="64cea-183">Vylepšení kandidátů přetížení</span><span class="sxs-lookup"><span data-stu-id="64cea-183">Improved overload candidates</span></span>

<span data-ttu-id="64cea-184">V každé verzi pravidla řešení přetížení získat aktualizovány k řešení situacích, kdy nejednoznačné vyvolání metody mají "zřejmou" volbu.</span><span class="sxs-lookup"><span data-stu-id="64cea-184">In every release, the overload resolution rules get updated to address situations where ambiguous method invocations have an "obvious" choice.</span></span> <span data-ttu-id="64cea-185">Tato verze přidá tři nová pravidla, která kompilátoru pomohou vybrat jasnou volbu:</span><span class="sxs-lookup"><span data-stu-id="64cea-185">This release adds three new rules to help the compiler pick the obvious choice:</span></span>

1. <span data-ttu-id="64cea-186">Pokud skupina metod obsahuje instance i statické členy, kompilátor zahodí členy instance, pokud byla metoda vyvolána bez příjemce instance nebo kontextu.</span><span class="sxs-lookup"><span data-stu-id="64cea-186">When a method group contains both instance and static members, the compiler discards the instance members if the method was invoked without an instance receiver or context.</span></span> <span data-ttu-id="64cea-187">Kompilátor zahodí statické členy, pokud byla metoda vyvolána s příjemcem instance.</span><span class="sxs-lookup"><span data-stu-id="64cea-187">The compiler discards the static members if the method was invoked with an instance receiver.</span></span> <span data-ttu-id="64cea-188">Pokud neexistuje žádný příjemce, kompilátor obsahuje pouze statické členy ve statickém kontextu, jinak statické členy i členy instance.</span><span class="sxs-lookup"><span data-stu-id="64cea-188">When there is no receiver, the compiler includes only static members in a static context, otherwise both static and instance members.</span></span> <span data-ttu-id="64cea-189">Pokud je příjemce nejednoznačně instancí nebo typem, kompilátor obsahuje obojí.</span><span class="sxs-lookup"><span data-stu-id="64cea-189">When the receiver is ambiguously an instance or type, the compiler includes both.</span></span> <span data-ttu-id="64cea-190">Statický kontext, kde `this` nelze použít implicitní instance příjemce, zahrnuje `this` tělo členů, kde není definována, `this` jako jsou statické členy, stejně jako místa, kde nelze použít, jako jsou inicializační pole a konstruktor-inicializátory.</span><span class="sxs-lookup"><span data-stu-id="64cea-190">A static context, where an implicit `this` instance receiver cannot be used, includes the body of members where no `this` is defined, such as static members, as well as places where `this` cannot be used, such as field initializers and constructor-initializers.</span></span>
1. <span data-ttu-id="64cea-191">Pokud skupina metod obsahuje některé obecné metody, jejichž argumenty typu nesplňují jejich omezení, jsou tito členové odebráni z kandidátské sady.</span><span class="sxs-lookup"><span data-stu-id="64cea-191">When a method group contains some generic methods whose type arguments do not satisfy their constraints, these members are removed from the candidate set.</span></span>
1. <span data-ttu-id="64cea-192">Pro převod skupiny metod jsou ze sady odebrány metody, jejichž návratový typ neodpovídá návratovému typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="64cea-192">For a method group conversion, candidate methods whose return type doesn't match up with the delegate's return type are removed from the set.</span></span>

<span data-ttu-id="64cea-193">Tuto změnu si všimnete pouze proto, že najdete méně chyb kompilátoru pro přetížení nejednoznačné metody, když jste si jisti, která metoda je lepší.</span><span class="sxs-lookup"><span data-stu-id="64cea-193">You'll only notice this change because you'll find fewer compiler errors for ambiguous method overloads when you are sure which method is better.</span></span>

## <a name="new-compiler-options"></a><span data-ttu-id="64cea-194">Nové možnosti kompilátoru</span><span class="sxs-lookup"><span data-stu-id="64cea-194">New compiler options</span></span>

<span data-ttu-id="64cea-195">Nové možnosti kompilátoru podporují nové scénáře sestavení a DevOps pro programy Jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="64cea-195">New compiler options support new build and DevOps scenarios for C# programs.</span></span>

### <a name="public-or-open-source-signing"></a><span data-ttu-id="64cea-196">Veřejné nebo open source podepisování</span><span class="sxs-lookup"><span data-stu-id="64cea-196">Public or Open Source signing</span></span>

<span data-ttu-id="64cea-197">Možnost `-publicsign` kompilátoru instruuje kompilátor podepsat sestavení pomocí veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="64cea-197">The `-publicsign` compiler option instructs the compiler to sign the assembly using a public key.</span></span> <span data-ttu-id="64cea-198">Sestavení je označeno jako podepsané, ale podpis je převzat z veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="64cea-198">The assembly is marked as signed, but the signature is taken from the public key.</span></span> <span data-ttu-id="64cea-199">Tato možnost umožňuje vytvářet podepsaná sestavení z open source projektů pomocí veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="64cea-199">This option enables you to build signed assemblies from open-source projects using a public key.</span></span>

<span data-ttu-id="64cea-200">Další informace naleznete v článku [možnosti kompilátoru -publicsign.](../language-reference/compiler-options/publicsign-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="64cea-200">For more information, see the [-publicsign compiler option](../language-reference/compiler-options/publicsign-compiler-option.md) article.</span></span>

### <a name="pathmap"></a><span data-ttu-id="64cea-201">mapa cesty</span><span class="sxs-lookup"><span data-stu-id="64cea-201">pathmap</span></span>

<span data-ttu-id="64cea-202">Možnost `-pathmap` kompilátoru instruuje kompilátor nahradit zdrojové cesty z prostředí sestavení mapovanými zdrojovými cestami.</span><span class="sxs-lookup"><span data-stu-id="64cea-202">The `-pathmap` compiler option instructs the compiler to replace source paths from the build environment with mapped source paths.</span></span> <span data-ttu-id="64cea-203">Tato `-pathmap` možnost řídí zdrojovou cestu napsanou kompilátorem do souborů PDB nebo pro <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>soubor .</span><span class="sxs-lookup"><span data-stu-id="64cea-203">The `-pathmap` option controls the source path written by the compiler to PDB files or for the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span></span>

<span data-ttu-id="64cea-204">Další informace naleznete v článku [možnosti kompilátoru -pathmap.](../language-reference/compiler-options/pathmap-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="64cea-204">For more information, see the [-pathmap compiler option](../language-reference/compiler-options/pathmap-compiler-option.md) article.</span></span>
