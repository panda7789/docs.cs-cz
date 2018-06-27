---
title: Co je nového v C# 7.3
description: Přehled nových funkcí v C# 7.3
ms.date: 05/16/2018
ms.openlocfilehash: 96aa0290299755c00cbc698297661bd847ed4221
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948495"
---
# <a name="whats-new-in-c-73"></a><span data-ttu-id="c2e2e-103">Co je nového v C# 7.3</span><span class="sxs-lookup"><span data-stu-id="c2e2e-103">What's new in C# 7.3</span></span>

<span data-ttu-id="c2e2e-104">Existují dvě hlavní motivy na vydání 7.3 C#.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-104">There are two main themes to the C# 7.3 release.</span></span> <span data-ttu-id="c2e2e-105">Jeden motiv poskytuje funkce, které umožňují bezpečné kódu, které původce jako nezabezpečený kód.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-105">One theme provides features that enable safe code to be as performant as unsafe code.</span></span> <span data-ttu-id="c2e2e-106">Druhý motiv poskytuje postupných vylepšení stávajících funkcí.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-106">The second theme provides incremental improvements to existing features.</span></span> <span data-ttu-id="c2e2e-107">Kromě toho byly přidány nové možnosti kompilátoru v této verzi.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-107">In addition, new compiler options were added in this release.</span></span>

<span data-ttu-id="c2e2e-108">Následující nové funkce podporují motiv lepší výkon pro bezpečné kód:</span><span class="sxs-lookup"><span data-stu-id="c2e2e-108">The following new features support the theme of better performance for safe code:</span></span>

- <span data-ttu-id="c2e2e-109">Pole pevné můžete přistupovat bez Připnutí.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-109">You can access fixed fields without pinning.</span></span>
- <span data-ttu-id="c2e2e-110">Můžete opětovně přiřadit `ref` místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-110">You can reassign `ref` local variables.</span></span>
- <span data-ttu-id="c2e2e-111">Inicializátory můžete použít na `stackalloc` pole.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-111">You can use initializers on `stackalloc` arrays.</span></span>
- <span data-ttu-id="c2e2e-112">Můžete použít `fixed` příkazy s žádný typ, který podporuje vzor.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-112">You can use `fixed` statements with any type that supports a pattern.</span></span>
- <span data-ttu-id="c2e2e-113">Můžete vytvořit další obecná omezení.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-113">You can use additional generic constraints.</span></span>

<span data-ttu-id="c2e2e-114">Byly provedeny následující vylepšení stávajících funkcí:</span><span class="sxs-lookup"><span data-stu-id="c2e2e-114">The following enhancements were made to existing features:</span></span>

- <span data-ttu-id="c2e2e-115">Můžete otestovat `==` a `!=` s typy řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-115">You can test `==` and `!=` with tuple types.</span></span>
- <span data-ttu-id="c2e2e-116">Výraz proměnné můžete použít na více místech.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-116">You can use expression variables in more locations.</span></span>
- <span data-ttu-id="c2e2e-117">Atributy může připojit k poli zálohování automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-117">You may attach attributes to the backing field of auto-implemented properties.</span></span>
- <span data-ttu-id="c2e2e-118">Metoda řešení, pokud se liší argumenty `in` se zlepšila.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-118">Method resolution when arguments differ by `in` has been improved.</span></span>
- <span data-ttu-id="c2e2e-119">Řešení přetížení teď má méně dvojznačné případy.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-119">Overload resolution now has fewer ambiguous cases.</span></span>

<span data-ttu-id="c2e2e-120">Nové možnosti kompilátoru jsou:</span><span class="sxs-lookup"><span data-stu-id="c2e2e-120">The new compiler options are:</span></span>

- <span data-ttu-id="c2e2e-121">`-publicsign` Chcete-li povolit, otevřete zdroj softwaru (OSS) podepisování sestavení.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-121">`-publicsign` to enable Open Source Software (OSS) signing of assemblies.</span></span>
- <span data-ttu-id="c2e2e-122">`-pathmap` zadat mapování pro zdrojového adresáře.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-122">`-pathmap` to provide a mapping for source directories.</span></span>

<span data-ttu-id="c2e2e-123">Zbývající část tohoto článku poskytuje podrobnosti a odkazy na další informace o jednotlivých vylepšení.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-123">The remainder of this article provides details and links to learn more about each of the improvements.</span></span>

## <a name="enabling-more-performant-safe-code"></a><span data-ttu-id="c2e2e-124">Povolení více původce bezpečné kódu</span><span class="sxs-lookup"><span data-stu-id="c2e2e-124">Enabling more performant safe code</span></span>

<span data-ttu-id="c2e2e-125">Nyní byste měli mít psaní kódu jazyka C#, bezpečně provádějící i nezabezpečený kód.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-125">You should be able to write C# code safely that performs as well as unsafe code.</span></span> <span data-ttu-id="c2e2e-126">Bezpečné kód zabraňuje třídy chyb, jako je přetečení vyrovnávací paměti, ukazatele stray a dalších chyb přístupu k paměti.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-126">Safe code avoids classes of errors, such as buffer overruns, stray pointers, and other memory access errors.</span></span> <span data-ttu-id="c2e2e-127">Tyto nové funkce rozšíření schopností ověřitelný kód bezpečné.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-127">These new features expand the capabilities of verifiable safe code.</span></span> <span data-ttu-id="c2e2e-128">Snažit zapsat informace z vašeho kódu pomocí bezpečné konstrukce.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-128">Strive to write more of your code using safe constructs.</span></span> <span data-ttu-id="c2e2e-129">Tyto funkce ujistěte, že jednodušší.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-129">These features make that easier.</span></span>

### <a name="indexing-fixed-fields-does-not-require-pinning"></a><span data-ttu-id="c2e2e-130">Indexování `fixed` pole nevyžaduje Připnutí</span><span class="sxs-lookup"><span data-stu-id="c2e2e-130">Indexing `fixed` fields does not require pinning</span></span>

<span data-ttu-id="c2e2e-131">Vezměte v úvahu tato struktura:</span><span class="sxs-lookup"><span data-stu-id="c2e2e-131">Consider this struct:</span></span>

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

<span data-ttu-id="c2e2e-132">V dřívějších verzích jazyka C#, je potřeba připnout proměnnou pro přístup k jedné celých čísel, které jsou součástí `myFixedField`.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-132">In earlier versions of C#, you needed to pin a variable to access one of the integers that are part of `myFixedField`.</span></span> <span data-ttu-id="c2e2e-133">Následující kód zkompiluje teď v bezpečném kontextu:</span><span class="sxs-lookup"><span data-stu-id="c2e2e-133">Now, the following code compiles in a safe context:</span></span>

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

<span data-ttu-id="c2e2e-134">Proměnná `p` přistupuje k jeden element ve `myFixedField`.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-134">The variable `p` accesses one element in `myFixedField`.</span></span> <span data-ttu-id="c2e2e-135">Nemusíte samostatnou declare `int*` proměnné.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-135">You don't need to declare a separate `int*` variable.</span></span> <span data-ttu-id="c2e2e-136">Všimněte si, že budete potřebovat `unsafe` kontextu.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-136">Note that you still need an `unsafe` context.</span></span> <span data-ttu-id="c2e2e-137">V dřívějších verzích jazyka C# je třeba deklarovat druhý pevné ukazatel:</span><span class="sxs-lookup"><span data-stu-id="c2e2e-137">In earlier versions of C#, you need to declare a second fixed pointer:</span></span>

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

<span data-ttu-id="c2e2e-138">Další informace najdete v článku na [ `fixed` příkaz](../language-reference/keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c2e2e-138">Fore more information, see the article on the [`fixed` statement](../language-reference/keywords/fixed-statement.md).</span></span>

### <a name="ref-local-variables-may-be-reassigned"></a><span data-ttu-id="c2e2e-139">`ref` lokální proměnné mohou být přiděleny.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-139">`ref` local variables may be reassigned</span></span>

<span data-ttu-id="c2e2e-140">Nyní `ref` místní hodnoty mohou být přiděleny k odkazování na různé instance po inicializaci.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-140">Now, `ref` locals may be reassigned to refer to different instances after being initialized.</span></span> <span data-ttu-id="c2e2e-141">Následující kód nyní zkompiluje:</span><span class="sxs-lookup"><span data-stu-id="c2e2e-141">The following code now compiles:</span></span>

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

<span data-ttu-id="c2e2e-142">Další informace najdete v článku na [ `ref` vrátí a `ref` místní hodnoty –](../programming-guide/classes-and-structs/ref-returns.md).</span><span class="sxs-lookup"><span data-stu-id="c2e2e-142">For more information, see the article on [`ref` returns and `ref` locals](../programming-guide/classes-and-structs/ref-returns.md).</span></span>

### <a name="stackalloc-arrays-support-initializers"></a><span data-ttu-id="c2e2e-143">`stackalloc` pole podporují inicializátory</span><span class="sxs-lookup"><span data-stu-id="c2e2e-143">`stackalloc` arrays support initializers</span></span>

<span data-ttu-id="c2e2e-144">Bylo dříve možné zadat hodnoty pro elementy v matici, když je inicializovat:</span><span class="sxs-lookup"><span data-stu-id="c2e2e-144">You've been able to specify the values for elements in an array when you initialize it:</span></span>

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

<span data-ttu-id="c2e2e-145">Teď, může tento stejnou syntaxi použijí na pole, které jsou deklarovány s `stackalloc`:</span><span class="sxs-lookup"><span data-stu-id="c2e2e-145">Now, that same syntax can be applied to arrays that are declared with `stackalloc`:</span></span>

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

<span data-ttu-id="c2e2e-146">Další informace najdete v tématu [ `stackalloc` příkaz](../language-reference/keywords/stackalloc.md) článek v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-146">For more information, see the [`stackalloc` statement](../language-reference/keywords/stackalloc.md) article in the language reference.</span></span>

### <a name="more-types-support-the-fixed-statement"></a><span data-ttu-id="c2e2e-147">Další typy podporují `fixed` – příkaz</span><span class="sxs-lookup"><span data-stu-id="c2e2e-147">More types support the `fixed` statement</span></span>

<span data-ttu-id="c2e2e-148">`fixed` Příkaz podporován omezenou sadu typy.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-148">The `fixed` statement supported a limited set of types.</span></span> <span data-ttu-id="c2e2e-149">Od verze jazyka C# 7.3, žádný typ, který obsahuje `GetPinnableReference()` metodu, která vrátí `ref T` nebo `ref readonly T` může být `fixed`.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-149">Starting with C# 7.3, any type that contains a `GetPinnableReference()` method that returns a `ref T` or `ref readonly T` may be `fixed`.</span></span> <span data-ttu-id="c2e2e-150">Přidání této funkce znamená, že `fixed` lze použít s <xref:System.Span%601?displayProperty=nameWithType> a související typy.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-150">Adding this feature means that `fixed` can be used with <xref:System.Span%601?displayProperty=nameWithType> and related types.</span></span>

<span data-ttu-id="c2e2e-151">Další informace najdete v tématu [ `fixed` příkaz](../language-reference/keywords/fixed-statement.md) článek v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-151">For more information, see the [`fixed` statement](../language-reference/keywords/fixed-statement.md) article in the language reference.</span></span>

### <a name="enhanced-generic-constraints"></a><span data-ttu-id="c2e2e-152">Rozšířené obecná omezení</span><span class="sxs-lookup"><span data-stu-id="c2e2e-152">Enhanced generic constraints</span></span>

<span data-ttu-id="c2e2e-153">Nyní můžete určit typ <xref:System.Enum?displayProperty=nameWithType> nebo <xref:System.Delegate?displayProperty=nameWithType> jako základní třída omezení pro parametr typu.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-153">You can now specify the type <xref:System.Enum?displayProperty=nameWithType> or <xref:System.Delegate?displayProperty=nameWithType> as base class constraints for a type parameter.</span></span>

<span data-ttu-id="c2e2e-154">Můžete také použít nové `unmanaged` omezení, chcete-li určit, že musí být parametr typu **nespravované typu**.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-154">You can also use the new `unmanaged` constraint, to specify that a type parameter must be an **unmanaged type**.</span></span> <span data-ttu-id="c2e2e-155">**Nespravované typu** je typ, který není typu odkazu a neobsahuje žádné odkaz na libovolnou úroveň vnoření.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-155">An **unmanaged type** is a type that isn't a reference type and doesn't contain any reference type at any level of nesting.</span></span>

<span data-ttu-id="c2e2e-156">Další informace najdete v článcích na [ `where` obecná omezení](../language-reference/keywords/where-generic-type-constraint.md) a [omezení parametrů typů](../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="c2e2e-156">For more information, see the articles on [`where` generic constraints](../language-reference/keywords/where-generic-type-constraint.md) and [constraints on type parameters](../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="make-existing-features-better"></a><span data-ttu-id="c2e2e-157">Vylepšit stávajících funkcí</span><span class="sxs-lookup"><span data-stu-id="c2e2e-157">Make existing features better</span></span>

<span data-ttu-id="c2e2e-158">Druhý motiv poskytuje přináší vylepšení funkcí v jazyce.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-158">The second theme provides improvements to features in the language.</span></span> <span data-ttu-id="c2e2e-159">Tyto funkce zlepšit produktivitu při zápisu C#.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-159">These features improve productivity when writing C#.</span></span>

### <a name="tuples-support--and-"></a><span data-ttu-id="c2e2e-160">Podpora řazených kolekcí členů `==` a `!=`</span><span class="sxs-lookup"><span data-stu-id="c2e2e-160">Tuples support `==` and `!=`</span></span>

<span data-ttu-id="c2e2e-161">C# řazenou kolekci členů typy teď podporují `==` a `!=`.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-161">The C# tuple types now support `==` and `!=`.</span></span> <span data-ttu-id="c2e2e-162">Další informace najdete v části zahrnut [rovnosti](../tuples.md#equality-and-tuples) v článku na [řazených kolekcí členů](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="c2e2e-162">Fore more information, see the section covering [equality](../tuples.md#equality-and-tuples) in the article on [tuples](../tuples.md).</span></span>

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a><span data-ttu-id="c2e2e-163">Přiřadit atributy pole zálohování pro automaticky implementované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c2e2e-163">Attach attributes to the backing fields for auto-implemented properties</span></span>

<span data-ttu-id="c2e2e-164">Se teď podporuje tuto syntaxi:</span><span class="sxs-lookup"><span data-stu-id="c2e2e-164">This syntax is now supported:</span></span>

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

<span data-ttu-id="c2e2e-165">Atribut `SomeThingAboutFieldAttribute` se použije na pole Základní kompilátoru generované pro `SomeProperty`.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-165">The attribute `SomeThingAboutFieldAttribute` is applied to the compiler generated backing field for `SomeProperty`.</span></span> <span data-ttu-id="c2e2e-166">Další informace najdete v tématu [atributy](../programming-guide/concepts/attributes/index.md) v příručce programovacího jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-166">For more information, see [attributes](../programming-guide/concepts/attributes/index.md) in the C# programming guide.</span></span>

### <a name="in-method-overload-resolution-tiebreaker"></a><span data-ttu-id="c2e2e-167">`in` tiebreaker rozlišení přetížení – metoda</span><span class="sxs-lookup"><span data-stu-id="c2e2e-167">`in` method overload resolution tiebreaker</span></span>

<span data-ttu-id="c2e2e-168">Když `in` modifikátor argument byl přidán, tyto dvě metody způsobí to nejednoznačnost:</span><span class="sxs-lookup"><span data-stu-id="c2e2e-168">When the `in` argument modifier was added, these two methods would cause an ambiguity:</span></span>

```csharp
static void M(S arg);
static void M(in S arg);
```

<span data-ttu-id="c2e2e-169">Nyní hodnotou (nejprve v předchozím příkladu) je lepší, než přetížení verzí odkaz jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-169">Now, the by value (first in the preceding example) overload is better than the by readonly reference version.</span></span> <span data-ttu-id="c2e2e-170">K volání na verzi s argumentem odkaz jen pro čtení, je nutné zahrnout `in` modifikátor při volání metody.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-170">To call the version with the readonly reference argument, you must include the `in` modifier when calling the method.</span></span>

> [!NOTE]
> <span data-ttu-id="c2e2e-171">Tato možnost byla implementovaná jako oprava chyb.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-171">This was implemented as a bug fix.</span></span> <span data-ttu-id="c2e2e-172">To už je nejednoznačný i s jazyková verze nastavena na "7.2".</span><span class="sxs-lookup"><span data-stu-id="c2e2e-172">This no longer is ambiguous even with the language version set to "7.2".</span></span>

<span data-ttu-id="c2e2e-173">Další informace najdete v článku na [ `in` – modifikátor parametrů](../language-reference/keywords/in-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="c2e2e-173">For more information, see the article on the [`in` parameter modifier](../language-reference/keywords/in-parameter-modifier.md).</span></span>

### <a name="extend-expression-variables-in-initializers"></a><span data-ttu-id="c2e2e-174">Rozšíření proměnných výrazu v inicializátory</span><span class="sxs-lookup"><span data-stu-id="c2e2e-174">Extend expression variables in initializers</span></span>

<span data-ttu-id="c2e2e-175">Syntaxe přidali v C# 7.0 umožňuje `out` deklarace proměnných rozšířilo zahrnout pole inicializátory, vlastnost inicializátory, inicializátory konstruktoru, a dotaz klauzule.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-175">The syntax added in C# 7.0 to allow `out` variable declarations has been extended to include field initializers, property initializers, constructor initializers, and query clauses.</span></span> <span data-ttu-id="c2e2e-176">Umožňuje kódu, například v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c2e2e-176">It enables code such as the following example:</span></span>

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
   public D(int i) : B(i, out var j)
   {
      Console.WriteLine($"The value of 'j' is {j}");
   }
}
```

### <a name="improved-overload-candidates"></a><span data-ttu-id="c2e2e-177">Vylepšené přetížení kandidáty</span><span class="sxs-lookup"><span data-stu-id="c2e2e-177">Improved overload candidates</span></span>

<span data-ttu-id="c2e2e-178">V každé verzi pravidel řešení přetížení aktualizovat na situace, kdy volání metod nejednoznačný mít na volbu "zřejmé".</span><span class="sxs-lookup"><span data-stu-id="c2e2e-178">In every release, the overload resolution rules get updated to address situations where ambiguous method invocations have an "obvious" choice.</span></span> <span data-ttu-id="c2e2e-179">Tato verze přináší tři nové pravidel pomohou kompilátoru vyberte zřejmé možnost:</span><span class="sxs-lookup"><span data-stu-id="c2e2e-179">This release adds three new rules to help the compiler pick the obvious choice:</span></span>

1. <span data-ttu-id="c2e2e-180">Pokud skupina metoda obsahuje instanci a statické členy, kompilátor zahodí členů instance, pokud metoda byla volána bez příjemce instance nebo kontextu.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-180">When a method group contains both instance and static members, the compiler discards the instance members if the method was invoked without an instance receiver or context.</span></span> <span data-ttu-id="c2e2e-181">Kompilátor zahodí statické členy, pokud metoda byla volána s příjemce instance.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-181">The compiler discards the static members if the method was invoked with an instance receiver.</span></span> <span data-ttu-id="c2e2e-182">Když není žádný příjemce, kompilátor zahrnuje pouze statické členy ve statickém kontextu, v opačném případě statické a instanci členy.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-182">When there is no receiver, the compiler includes only static members in a static context, otherwise both static and instance members.</span></span> <span data-ttu-id="c2e2e-183">Když příjemce je ambiguously instance nebo typu, kompilátor zahrnuje obě.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-183">When the receiver is ambiguously an instance or type, the compiler includes both.</span></span> <span data-ttu-id="c2e2e-184">Statickém kontextu, kde implicitní `this` příjemce instanci nelze použít, obsahuje tělo členů, kde ne `this` definované, například statické členy, jakož i kdy, kde `this` nelze použít, jako je například pole inicializátory a Inicializátory konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-184">A static context, where an implicit `this` instance receiver cannot be used, includes the body of members where no `this` is defined, such as static members, as well as places where `this` cannot be used, such as field initializers and constructor-initializers.</span></span>
1. <span data-ttu-id="c2e2e-185">Pokud metoda skupina obsahuje některé obecné metody, jejichž argumenty typu nesplňují jejich omezení, tito členové budou odebrány ze sady candidate.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-185">When a method group contains some generic methods whose type arguments do not satisfy their constraints, these members are removed from the candidate set.</span></span>
1. <span data-ttu-id="c2e2e-186">Pro převod skupin metoda candidate metody, jejichž návratový typ se neshoduje společně s ním vrátí typ se odeberou ze sady.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-186">For a method group conversion, candidate methods whose return type doesn't match up with the delegate's return type are removed from the set.</span></span>

<span data-ttu-id="c2e2e-187">Tato změna můžete si všimnout pouze protože najdete méně chyby kompilátoru o přetížení metody nejednoznačný když jste si jisti, jakou metodu je lepší.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-187">You'll only notice this change because you'll find fewer compiler errors for ambiguous method overloads when you are sure which method is better.</span></span>

## <a name="new-compiler-options"></a><span data-ttu-id="c2e2e-188">Nové možnosti kompilátoru</span><span class="sxs-lookup"><span data-stu-id="c2e2e-188">New compiler options</span></span>

<span data-ttu-id="c2e2e-189">Nové možnosti kompilátoru podporu nového sestavení a DevOps scénáře pro programy C#.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-189">New compiler options support new build and DevOps scenarios for C# programs.</span></span>

### <a name="public-or-open-source-signing"></a><span data-ttu-id="c2e2e-190">Veřejné nebo podepisování Open Source</span><span class="sxs-lookup"><span data-stu-id="c2e2e-190">Public or Open Source signing</span></span>

<span data-ttu-id="c2e2e-191">`-publicsign` – Možnost kompilátoru dává pokyn kompilátoru k podepsání sestavení pomocí veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-191">The `-publicsign` compiler option instructs the compiler to sign the assembly using a public key.</span></span> <span data-ttu-id="c2e2e-192">Sestavení je označena jako podepsané, ale podpis jsou převzaty z veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-192">The assembly is marked as signed, but the signature is taken from the public key.</span></span> <span data-ttu-id="c2e2e-193">Tato možnost umožňuje vytvářet podepsaná sestavení z projektů open-source pomocí veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-193">This option enables you to build signed assemblies from open-source projects using a public key.</span></span>

<span data-ttu-id="c2e2e-194">Další informace najdete v tématu [- publicsign – možnost kompilátoru](../language-reference/compiler-options/publicsign-compiler-option.md) článku.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-194">For more information, see the [-publicsign compiler option](../language-reference/compiler-options/publicsign-compiler-option.md) article.</span></span>

### <a name="pathmap"></a><span data-ttu-id="c2e2e-195">pathmap</span><span class="sxs-lookup"><span data-stu-id="c2e2e-195">pathmap</span></span>

<span data-ttu-id="c2e2e-196">`-pathmap` – Možnost kompilátoru dává pokyn kompilátoru nahradit mapovat zdrojových cest zdrojových cest z prostředí sestavení.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-196">The `-pathmap` compiler option instructs the compiler to replace source paths from the build environment with mapped source paths.</span></span> <span data-ttu-id="c2e2e-197">`-pathmap` Možnost ovládací prvky podle kompilátor zapisují do souboru PDB soubory nebo pro zdrojovou cestu <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-197">The `-pathmap` option controls the source path written by the compiler to PDB files or for the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span></span>

<span data-ttu-id="c2e2e-198">Další informace najdete v tématu [- pathmap – možnost kompilátoru](../language-reference/compiler-options/pathmap-compiler-option.md) článku.</span><span class="sxs-lookup"><span data-stu-id="c2e2e-198">For more information, see the [-pathmap compiler option](../language-reference/compiler-options/pathmap-compiler-option.md) article.</span></span>
