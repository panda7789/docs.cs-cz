---
title: Co je nového v C# 7,3
description: Přehled nových funkcí v C# 7,3
ms.date: 05/16/2018
ms.openlocfilehash: ca53073db1b61300186a483001f79bf0caa79169
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433514"
---
# <a name="whats-new-in-c-73"></a><span data-ttu-id="8eab5-103">Co je nového v C# 7,3</span><span class="sxs-lookup"><span data-stu-id="8eab5-103">What's new in C# 7.3</span></span>

<span data-ttu-id="8eab5-104">Verze C# 7,3 obsahuje dva hlavní motivy.</span><span class="sxs-lookup"><span data-stu-id="8eab5-104">There are two main themes to the C# 7.3 release.</span></span> <span data-ttu-id="8eab5-105">Jeden motiv nabízí funkce, které umožňují bezpečný kód jako nezabezpečený kód.</span><span class="sxs-lookup"><span data-stu-id="8eab5-105">One theme provides features that enable safe code to be as performant as unsafe code.</span></span> <span data-ttu-id="8eab5-106">Druhý motiv nabízí přírůstková vylepšení existujících funkcí.</span><span class="sxs-lookup"><span data-stu-id="8eab5-106">The second theme provides incremental improvements to existing features.</span></span> <span data-ttu-id="8eab5-107">Kromě toho se v této verzi přidaly nové možnosti kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="8eab5-107">In addition, new compiler options were added in this release.</span></span>

<span data-ttu-id="8eab5-108">Následující nové funkce podporují motiv s lepším výkonem pro bezpečný kód:</span><span class="sxs-lookup"><span data-stu-id="8eab5-108">The following new features support the theme of better performance for safe code:</span></span>

- <span data-ttu-id="8eab5-109">Můžete získat přístup k pevným polím bez připnutí.</span><span class="sxs-lookup"><span data-stu-id="8eab5-109">You can access fixed fields without pinning.</span></span>
- <span data-ttu-id="8eab5-110">Můžete změnit přiřazení `ref` místních proměnných.</span><span class="sxs-lookup"><span data-stu-id="8eab5-110">You can reassign `ref` local variables.</span></span>
- <span data-ttu-id="8eab5-111">Můžete použít inicializátory u `stackalloc` polí.</span><span class="sxs-lookup"><span data-stu-id="8eab5-111">You can use initializers on `stackalloc` arrays.</span></span>
- <span data-ttu-id="8eab5-112">Můžete použít `fixed` příkazy s jakýmkoli typem, který podporuje vzor.</span><span class="sxs-lookup"><span data-stu-id="8eab5-112">You can use `fixed` statements with any type that supports a pattern.</span></span>
- <span data-ttu-id="8eab5-113">Můžete použít další obecná omezení.</span><span class="sxs-lookup"><span data-stu-id="8eab5-113">You can use additional generic constraints.</span></span>

<span data-ttu-id="8eab5-114">V existujících funkcích byly provedeny následující vylepšení:</span><span class="sxs-lookup"><span data-stu-id="8eab5-114">The following enhancements were made to existing features:</span></span>

- <span data-ttu-id="8eab5-115">Můžete testovat `==` a `!=` s typy řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="8eab5-115">You can test `==` and `!=` with tuple types.</span></span>
- <span data-ttu-id="8eab5-116">Proměnné výrazu můžete použít ve více umístěních.</span><span class="sxs-lookup"><span data-stu-id="8eab5-116">You can use expression variables in more locations.</span></span>
- <span data-ttu-id="8eab5-117">Můžete přiřazovat atributy k poli pro zálohování s automaticky implementovanými vlastnostmi.</span><span class="sxs-lookup"><span data-stu-id="8eab5-117">You may attach attributes to the backing field of auto-implemented properties.</span></span>
- <span data-ttu-id="8eab5-118">Řešení metody, když se liší `in` argumenty, které byly vylepšeny.</span><span class="sxs-lookup"><span data-stu-id="8eab5-118">Method resolution when arguments differ by `in` has been improved.</span></span>
- <span data-ttu-id="8eab5-119">Řešení přetížení teď má méně dvojznačných případů.</span><span class="sxs-lookup"><span data-stu-id="8eab5-119">Overload resolution now has fewer ambiguous cases.</span></span>

<span data-ttu-id="8eab5-120">Nové možnosti kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="8eab5-120">The new compiler options are:</span></span>

- <span data-ttu-id="8eab5-121">`-publicsign`povolení podepisování softwaru open source (OSS) pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="8eab5-121">`-publicsign` to enable Open Source Software (OSS) signing of assemblies.</span></span>
- <span data-ttu-id="8eab5-122">`-pathmap`pro poskytnutí mapování pro zdrojové adresáře.</span><span class="sxs-lookup"><span data-stu-id="8eab5-122">`-pathmap` to provide a mapping for source directories.</span></span>

<span data-ttu-id="8eab5-123">Zbývající část tohoto článku obsahuje podrobnosti a odkazy na Další informace o každé z těchto vylepšení.</span><span class="sxs-lookup"><span data-stu-id="8eab5-123">The remainder of this article provides details and links to learn more about each of the improvements.</span></span> <span data-ttu-id="8eab5-124">Pomocí `dotnet try` globálního nástroje můžete prozkoumat tyto funkce ve vašem prostředí:</span><span class="sxs-lookup"><span data-stu-id="8eab5-124">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="8eab5-125">Nainstalujte nástroj [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) Global.</span><span class="sxs-lookup"><span data-stu-id="8eab5-125">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="8eab5-126">Naklonujte úložiště [dotnet/try-Samples](https://github.com/dotnet/try-samples) .</span><span class="sxs-lookup"><span data-stu-id="8eab5-126">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="8eab5-127">Nastavte aktuální adresář do podadresáře *csharp7* pro úložiště *Try-Samples* .</span><span class="sxs-lookup"><span data-stu-id="8eab5-127">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="8eab5-128">Spusťte `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="8eab5-128">Run `dotnet try`.</span></span>

## <a name="enabling-more-efficient-safe-code"></a><span data-ttu-id="8eab5-129">Povolení efektivnějšího bezpečného kódu</span><span class="sxs-lookup"><span data-stu-id="8eab5-129">Enabling more efficient safe code</span></span>

<span data-ttu-id="8eab5-130">Měli byste být schopni bezpečně C# psát kód, který provádí a také nezabezpečený kód.</span><span class="sxs-lookup"><span data-stu-id="8eab5-130">You should be able to write C# code safely that performs as well as unsafe code.</span></span> <span data-ttu-id="8eab5-131">Bezpečný kód zabraňuje třídám chyb, jako jsou přetečení vyrovnávací paměti, osamocené ukazatele a další chyby přístupu k paměti.</span><span class="sxs-lookup"><span data-stu-id="8eab5-131">Safe code avoids classes of errors, such as buffer overruns, stray pointers, and other memory access errors.</span></span> <span data-ttu-id="8eab5-132">Tyto nové funkce rozšiřují možnosti ověřitelného bezpečného kódu.</span><span class="sxs-lookup"><span data-stu-id="8eab5-132">These new features expand the capabilities of verifiable safe code.</span></span> <span data-ttu-id="8eab5-133">Snažte se zapisovat více kódu pomocí bezpečných konstrukcí.</span><span class="sxs-lookup"><span data-stu-id="8eab5-133">Strive to write more of your code using safe constructs.</span></span> <span data-ttu-id="8eab5-134">Tyto funkce usnadňují práci.</span><span class="sxs-lookup"><span data-stu-id="8eab5-134">These features make that easier.</span></span>

### <a name="indexing-fixed-fields-does-not-require-pinning"></a><span data-ttu-id="8eab5-135">Pole `fixed` indexování nevyžaduje připnutí.</span><span class="sxs-lookup"><span data-stu-id="8eab5-135">Indexing `fixed` fields does not require pinning</span></span>

<span data-ttu-id="8eab5-136">Zvažte tuto strukturu:</span><span class="sxs-lookup"><span data-stu-id="8eab5-136">Consider this struct:</span></span>

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

<span data-ttu-id="8eab5-137">V dřívějších verzích C#nástroje bylo nutné připnout proměnnou pro přístup k jednomu z celých čísel, která jsou součástí `myFixedField`.</span><span class="sxs-lookup"><span data-stu-id="8eab5-137">In earlier versions of C#, you needed to pin a variable to access one of the integers that are part of `myFixedField`.</span></span> <span data-ttu-id="8eab5-138">Nyní následující kód zkompiluje bez připnutí proměnné `p` uvnitř samostatného `fixed` příkazu:</span><span class="sxs-lookup"><span data-stu-id="8eab5-138">Now, the following code compiles without pinning the variable `p` inside a separate `fixed` statement:</span></span>

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

<span data-ttu-id="8eab5-139">Proměnná `p` přistupuje k jednomu prvku v `myFixedField`.</span><span class="sxs-lookup"><span data-stu-id="8eab5-139">The variable `p` accesses one element in `myFixedField`.</span></span> <span data-ttu-id="8eab5-140">Nemusíte deklarovat samostatnou `int*` proměnnou.</span><span class="sxs-lookup"><span data-stu-id="8eab5-140">You don't need to declare a separate `int*` variable.</span></span> <span data-ttu-id="8eab5-141">Všimněte si, že stále potřebujete `unsafe` kontext.</span><span class="sxs-lookup"><span data-stu-id="8eab5-141">Note that you still need an `unsafe` context.</span></span> <span data-ttu-id="8eab5-142">V dřívějších verzích C#nástroje je nutné deklarovat druhý pevný ukazatel:</span><span class="sxs-lookup"><span data-stu-id="8eab5-142">In earlier versions of C#, you need to declare a second fixed pointer:</span></span>

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

<span data-ttu-id="8eab5-143">Další informace najdete v článku o [ `fixed` příkazu](../language-reference/keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8eab5-143">For more information, see the article on the [`fixed` statement](../language-reference/keywords/fixed-statement.md).</span></span>

### <a name="ref-local-variables-may-be-reassigned"></a><span data-ttu-id="8eab5-144">`ref`lokální proměnné se můžou znovu přiřadit.</span><span class="sxs-lookup"><span data-stu-id="8eab5-144">`ref` local variables may be reassigned</span></span>

<span data-ttu-id="8eab5-145">Místní proměnné `ref` se teď dají znovu přiřadit, aby po inicializaci odkazovaly na různé instance.</span><span class="sxs-lookup"><span data-stu-id="8eab5-145">Now, `ref` locals may be reassigned to refer to different instances after being initialized.</span></span> <span data-ttu-id="8eab5-146">Nyní se zkompiluje následující kód:</span><span class="sxs-lookup"><span data-stu-id="8eab5-146">The following code now compiles:</span></span>

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

<span data-ttu-id="8eab5-147">Další informace najdete v článku o [ `ref` vrácených a `ref` místních](../programming-guide/classes-and-structs/ref-returns.md)hodnotách a na článku o [`foreach`](../language-reference/keywords/foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="8eab5-147">For more information, see the article on [`ref` returns and `ref` locals](../programming-guide/classes-and-structs/ref-returns.md), and the article on [`foreach`](../language-reference/keywords/foreach-in.md).</span></span>

### <a name="stackalloc-arrays-support-initializers"></a><span data-ttu-id="8eab5-148">`stackalloc`pole podporují Inicializátory.</span><span class="sxs-lookup"><span data-stu-id="8eab5-148">`stackalloc` arrays support initializers</span></span>

<span data-ttu-id="8eab5-149">Při inicializaci je možné zadat hodnoty prvků v poli:</span><span class="sxs-lookup"><span data-stu-id="8eab5-149">You've been able to specify the values for elements in an array when you initialize it:</span></span>

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

<span data-ttu-id="8eab5-150">Nyní lze stejnou syntaxi použít pro pole, která jsou deklarována pomocí `stackalloc`:</span><span class="sxs-lookup"><span data-stu-id="8eab5-150">Now, that same syntax can be applied to arrays that are declared with `stackalloc`:</span></span>

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

<span data-ttu-id="8eab5-151">Další informace najdete v článku o [ `stackalloc` operátoru](../language-reference/operators/stackalloc.md) .</span><span class="sxs-lookup"><span data-stu-id="8eab5-151">For more information, see the [`stackalloc` operator](../language-reference/operators/stackalloc.md) article.</span></span>

### <a name="more-types-support-the-fixed-statement"></a><span data-ttu-id="8eab5-152">Další typy podporují `fixed` příkaz.</span><span class="sxs-lookup"><span data-stu-id="8eab5-152">More types support the `fixed` statement</span></span>

<span data-ttu-id="8eab5-153">`fixed` Příkaz podporuje omezené sady typů.</span><span class="sxs-lookup"><span data-stu-id="8eab5-153">The `fixed` statement supported a limited set of types.</span></span> <span data-ttu-id="8eab5-154">Počínaje C# 7,3, jakýkoli typ, který `GetPinnableReference()` obsahuje `ref T` metodu, která vrací nebo `ref readonly T` může být `fixed`.</span><span class="sxs-lookup"><span data-stu-id="8eab5-154">Starting with C# 7.3, any type that contains a `GetPinnableReference()` method that returns a `ref T` or `ref readonly T` may be `fixed`.</span></span> <span data-ttu-id="8eab5-155">Přidání této funkce znamená, `fixed` že je možné použít <xref:System.Span%601?displayProperty=nameWithType> s a související typy.</span><span class="sxs-lookup"><span data-stu-id="8eab5-155">Adding this feature means that `fixed` can be used with <xref:System.Span%601?displayProperty=nameWithType> and related types.</span></span>

<span data-ttu-id="8eab5-156">Další informace naleznete v článku o [ `fixed` příkazu](../language-reference/keywords/fixed-statement.md) v referenční příručce jazyka.</span><span class="sxs-lookup"><span data-stu-id="8eab5-156">For more information, see the [`fixed` statement](../language-reference/keywords/fixed-statement.md) article in the language reference.</span></span>

### <a name="enhanced-generic-constraints"></a><span data-ttu-id="8eab5-157">Rozšířená obecná omezení</span><span class="sxs-lookup"><span data-stu-id="8eab5-157">Enhanced generic constraints</span></span>

<span data-ttu-id="8eab5-158">Nyní můžete určit typ <xref:System.Enum?displayProperty=nameWithType> nebo <xref:System.Delegate?displayProperty=nameWithType> jako omezení základní třídy pro parametr typu.</span><span class="sxs-lookup"><span data-stu-id="8eab5-158">You can now specify the type <xref:System.Enum?displayProperty=nameWithType> or <xref:System.Delegate?displayProperty=nameWithType> as base class constraints for a type parameter.</span></span>

<span data-ttu-id="8eab5-159">Můžete také použít nové `unmanaged` omezení, chcete-li určit, že parametr typu musí být nespravovaný [typ](../language-reference/builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="8eab5-159">You can also use the new `unmanaged` constraint, to specify that a type parameter must be an [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span></span>

<span data-ttu-id="8eab5-160">Další informace najdete v článcích o [ `where` obecných omezeních](../language-reference/keywords/where-generic-type-constraint.md) a [omezeních parametrů typu](../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="8eab5-160">For more information, see the articles on [`where` generic constraints](../language-reference/keywords/where-generic-type-constraint.md) and [constraints on type parameters](../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="8eab5-161">Přidání těchto omezení do existujících typů je [nekompatibilní změna](version-update-considerations.md#incompatible-changes).</span><span class="sxs-lookup"><span data-stu-id="8eab5-161">Adding these constraints to existing types is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="8eab5-162">Uzavřené obecné typy již nesmí splňovat tato nová omezení.</span><span class="sxs-lookup"><span data-stu-id="8eab5-162">Closed generic types may no longer meet these new constraints.</span></span>

## <a name="make-existing-features-better"></a><span data-ttu-id="8eab5-163">Lepší zlepšení stávajících funkcí</span><span class="sxs-lookup"><span data-stu-id="8eab5-163">Make existing features better</span></span>

<span data-ttu-id="8eab5-164">Druhý motiv nabízí vylepšení funkcí v jazyce.</span><span class="sxs-lookup"><span data-stu-id="8eab5-164">The second theme provides improvements to features in the language.</span></span> <span data-ttu-id="8eab5-165">Tyto funkce zvyšují produktivitu při C#psaní.</span><span class="sxs-lookup"><span data-stu-id="8eab5-165">These features improve productivity when writing C#.</span></span>

### <a name="tuples-support--and-"></a><span data-ttu-id="8eab5-166">Podpora `==` řazených kolekcí členů a`!=`</span><span class="sxs-lookup"><span data-stu-id="8eab5-166">Tuples support `==` and `!=`</span></span>

<span data-ttu-id="8eab5-167">C# Řazené kolekce členů teď `==` podporují `!=`a.</span><span class="sxs-lookup"><span data-stu-id="8eab5-167">The C# tuple types now support `==` and `!=`.</span></span> <span data-ttu-id="8eab5-168">Další informace najdete v části týkající se rovnosti v článku o [řazených kolekcích členů](../tuples.md). [](../tuples.md#equality-and-tuples)</span><span class="sxs-lookup"><span data-stu-id="8eab5-168">For more information, see the section covering [equality](../tuples.md#equality-and-tuples) in the article on [tuples](../tuples.md).</span></span>

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a><span data-ttu-id="8eab5-169">Připojení atributů k zálohovaným polím pro automaticky implementované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="8eab5-169">Attach attributes to the backing fields for auto-implemented properties</span></span>

<span data-ttu-id="8eab5-170">Tato syntaxe je teď podporovaná:</span><span class="sxs-lookup"><span data-stu-id="8eab5-170">This syntax is now supported:</span></span>

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

<span data-ttu-id="8eab5-171">Atribut `SomeThingAboutFieldAttribute` se použije pro `SomeProperty`pole zálohování generované kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="8eab5-171">The attribute `SomeThingAboutFieldAttribute` is applied to the compiler generated backing field for `SomeProperty`.</span></span> <span data-ttu-id="8eab5-172">Další informace najdete v tématu [atributy](../programming-guide/concepts/attributes/index.md) v průvodci C# programováním.</span><span class="sxs-lookup"><span data-stu-id="8eab5-172">For more information, see [attributes](../programming-guide/concepts/attributes/index.md) in the C# programming guide.</span></span>

### <a name="in-method-overload-resolution-tiebreaker"></a><span data-ttu-id="8eab5-173">`in`rozhodujícího prvku rozlišení přetížení metody</span><span class="sxs-lookup"><span data-stu-id="8eab5-173">`in` method overload resolution tiebreaker</span></span>

<span data-ttu-id="8eab5-174">Při přidání modifikátoru argumentu by tyto dvě metody způsobily nejednoznačnost: `in`</span><span class="sxs-lookup"><span data-stu-id="8eab5-174">When the `in` argument modifier was added, these two methods would cause an ambiguity:</span></span>

```csharp
static void M(S arg);
static void M(in S arg);
```

<span data-ttu-id="8eab5-175">Nyní je přetížení v hodnotě (první v předchozím příkladu) lepší než referenční verze metody ReadOnly.</span><span class="sxs-lookup"><span data-stu-id="8eab5-175">Now, the by value (first in the preceding example) overload is better than the by readonly reference version.</span></span> <span data-ttu-id="8eab5-176">Chcete-li volat verzi s argumentem odkazu jen pro čtení, je `in` nutné při volání metody použít modifikátor.</span><span class="sxs-lookup"><span data-stu-id="8eab5-176">To call the version with the readonly reference argument, you must include the `in` modifier when calling the method.</span></span>

> [!NOTE]
> <span data-ttu-id="8eab5-177">Tato chyba byla implementována jako oprava chyby.</span><span class="sxs-lookup"><span data-stu-id="8eab5-177">This was implemented as a bug fix.</span></span> <span data-ttu-id="8eab5-178">Tato možnost již není jednoznačná, i když je jazyková verze nastavená na "7,2".</span><span class="sxs-lookup"><span data-stu-id="8eab5-178">This no longer is ambiguous even with the language version set to "7.2".</span></span>

<span data-ttu-id="8eab5-179">Další informace naleznete v článku o [ `in` modifikátoru parametru](../language-reference/keywords/in-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="8eab5-179">For more information, see the article on the [`in` parameter modifier](../language-reference/keywords/in-parameter-modifier.md).</span></span>

### <a name="extend-expression-variables-in-initializers"></a><span data-ttu-id="8eab5-180">Rozšiřování proměnných výrazu v inicializátorech</span><span class="sxs-lookup"><span data-stu-id="8eab5-180">Extend expression variables in initializers</span></span>

<span data-ttu-id="8eab5-181">Syntaxe přidaná v C# 7,0 pro povolení `out` deklarací proměnných byla rozšířena tak, aby zahrnovala Inicializátory polí, Inicializátory vlastností, Inicializátory konstruktorů a klauzule dotazu.</span><span class="sxs-lookup"><span data-stu-id="8eab5-181">The syntax added in C# 7.0 to allow `out` variable declarations has been extended to include field initializers, property initializers, constructor initializers, and query clauses.</span></span> <span data-ttu-id="8eab5-182">Umožňuje kód, jako je například následující příklad:</span><span class="sxs-lookup"><span data-stu-id="8eab5-182">It enables code such as the following example:</span></span>

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

### <a name="improved-overload-candidates"></a><span data-ttu-id="8eab5-183">Vylepšení kandidátů přetížení</span><span class="sxs-lookup"><span data-stu-id="8eab5-183">Improved overload candidates</span></span>

<span data-ttu-id="8eab5-184">V každém vydání se pravidla rozlišení přetížení aktualizují na situace, kdy nejednoznačná vyvolání metod mají "zřejmou" volbu.</span><span class="sxs-lookup"><span data-stu-id="8eab5-184">In every release, the overload resolution rules get updated to address situations where ambiguous method invocations have an "obvious" choice.</span></span> <span data-ttu-id="8eab5-185">Tato verze přidává tři nová pravidla, která kompilátoru pomůžou vybrat zjevné možnosti:</span><span class="sxs-lookup"><span data-stu-id="8eab5-185">This release adds three new rules to help the compiler pick the obvious choice:</span></span>

1. <span data-ttu-id="8eab5-186">Pokud skupina metod obsahuje instanci i statické členy, kompilátor zruší členy instance, pokud byla metoda vyvolána bez přijímače nebo kontextu instance.</span><span class="sxs-lookup"><span data-stu-id="8eab5-186">When a method group contains both instance and static members, the compiler discards the instance members if the method was invoked without an instance receiver or context.</span></span> <span data-ttu-id="8eab5-187">Kompilátor zahodí statické členy, pokud byla metoda vyvolána s příjemcem instance.</span><span class="sxs-lookup"><span data-stu-id="8eab5-187">The compiler discards the static members if the method was invoked with an instance receiver.</span></span> <span data-ttu-id="8eab5-188">Pokud není k dispozici žádný přijímač, kompilátor zahrnuje pouze statické členy ve statickém kontextu, jinak statických i členů instancí.</span><span class="sxs-lookup"><span data-stu-id="8eab5-188">When there is no receiver, the compiler includes only static members in a static context, otherwise both static and instance members.</span></span> <span data-ttu-id="8eab5-189">Pokud je příjemce jednoznačně instance nebo typu, kompilátor zahrnuje obojí.</span><span class="sxs-lookup"><span data-stu-id="8eab5-189">When the receiver is ambiguously an instance or type, the compiler includes both.</span></span> <span data-ttu-id="8eab5-190">Statický kontext, kde nelze použít implicitního `this` přijímače instance, zahrnuje text členů, pokud není definován žádný `this` , například statické členy, a místa, kde `this` nelze použít, jako jsou například Inicializátory polí a Inicializátory konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="8eab5-190">A static context, where an implicit `this` instance receiver cannot be used, includes the body of members where no `this` is defined, such as static members, as well as places where `this` cannot be used, such as field initializers and constructor-initializers.</span></span>
1. <span data-ttu-id="8eab5-191">Pokud skupina metod obsahuje některé obecné metody, jejichž argumenty typu nesplňují jejich omezení, jsou tyto členy ze sady kandidátů odebrány.</span><span class="sxs-lookup"><span data-stu-id="8eab5-191">When a method group contains some generic methods whose type arguments do not satisfy their constraints, these members are removed from the candidate set.</span></span>
1. <span data-ttu-id="8eab5-192">Pro převod skupiny metod se ze sady odeberou metody kandidáta, jejichž návratový typ se neshoduje s návratovým typem delegáta.</span><span class="sxs-lookup"><span data-stu-id="8eab5-192">For a method group conversion, candidate methods whose return type doesn't match up with the delegate's return type are removed from the set.</span></span>

<span data-ttu-id="8eab5-193">Tuto změnu si všimnete pouze v případě, že při zjištění, která metoda je lepší, zjistíte méně chyb kompilátoru pro přetížení dvojznačných metod.</span><span class="sxs-lookup"><span data-stu-id="8eab5-193">You'll only notice this change because you'll find fewer compiler errors for ambiguous method overloads when you are sure which method is better.</span></span>

## <a name="new-compiler-options"></a><span data-ttu-id="8eab5-194">Nové možnosti kompilátoru</span><span class="sxs-lookup"><span data-stu-id="8eab5-194">New compiler options</span></span>

<span data-ttu-id="8eab5-195">Nové možnosti kompilátoru podporují nové scénáře sestavení a DevOps pro C# programy.</span><span class="sxs-lookup"><span data-stu-id="8eab5-195">New compiler options support new build and DevOps scenarios for C# programs.</span></span>

### <a name="public-or-open-source-signing"></a><span data-ttu-id="8eab5-196">Veřejné nebo open source podepisování</span><span class="sxs-lookup"><span data-stu-id="8eab5-196">Public or Open Source signing</span></span>

<span data-ttu-id="8eab5-197">Možnost `-publicsign` kompilátoru instruuje kompilátor, aby podepsal sestavení pomocí veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="8eab5-197">The `-publicsign` compiler option instructs the compiler to sign the assembly using a public key.</span></span> <span data-ttu-id="8eab5-198">Sestavení je označeno jako signed, ale signatura je pořízena z veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="8eab5-198">The assembly is marked as signed, but the signature is taken from the public key.</span></span> <span data-ttu-id="8eab5-199">Tato možnost umožňuje sestavit podepsaná sestavení z open source projektů pomocí veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="8eab5-199">This option enables you to build signed assemblies from open-source projects using a public key.</span></span>

<span data-ttu-id="8eab5-200">Další informace najdete v článku [možnost kompilátoru-publicsign](../language-reference/compiler-options/publicsign-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="8eab5-200">For more information, see the [-publicsign compiler option](../language-reference/compiler-options/publicsign-compiler-option.md) article.</span></span>

### <a name="pathmap"></a><span data-ttu-id="8eab5-201">pathmap</span><span class="sxs-lookup"><span data-stu-id="8eab5-201">pathmap</span></span>

<span data-ttu-id="8eab5-202">Možnost `-pathmap` kompilátoru instruuje kompilátor, aby nahradil zdrojové cesty z prostředí sestavení s namapovanými zdrojovými cestami.</span><span class="sxs-lookup"><span data-stu-id="8eab5-202">The `-pathmap` compiler option instructs the compiler to replace source paths from the build environment with mapped source paths.</span></span> <span data-ttu-id="8eab5-203">Možnost řídí zdrojovou cestu zapsanou kompilátorem do souborů PDB nebo <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>pro. `-pathmap`</span><span class="sxs-lookup"><span data-stu-id="8eab5-203">The `-pathmap` option controls the source path written by the compiler to PDB files or for the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span></span>

<span data-ttu-id="8eab5-204">Další informace najdete v článku [možnost kompilátoru-pathmap](../language-reference/compiler-options/pathmap-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="8eab5-204">For more information, see the [-pathmap compiler option](../language-reference/compiler-options/pathmap-compiler-option.md) article.</span></span>
