---
title: Co je nového v jazyce C# 7.3
description: Přehled nových funkcí v jazyce C# 7.3
ms.date: 05/16/2018
ms.openlocfilehash: 570da53059242c0242609ddcba5cb23f1728aa9f
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48028089"
---
# <a name="whats-new-in-c-73"></a><span data-ttu-id="9e4d0-103">Co je nového v jazyce C# 7.3</span><span class="sxs-lookup"><span data-stu-id="9e4d0-103">What's new in C# 7.3</span></span>

<span data-ttu-id="9e4d0-104">Existují dva hlavní motivy na verzi C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-104">There are two main themes to the C# 7.3 release.</span></span> <span data-ttu-id="9e4d0-105">Jeden motiv poskytuje funkce, které umožňují bezpečný kód, které funguje jako nezabezpečený kód.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-105">One theme provides features that enable safe code to be as performant as unsafe code.</span></span> <span data-ttu-id="9e4d0-106">Druhý motiv poskytuje několik postupných vylepšení stávajících funkcí.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-106">The second theme provides incremental improvements to existing features.</span></span> <span data-ttu-id="9e4d0-107">Kromě toho byly přidány nové možnosti kompilátoru v této verzi.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-107">In addition, new compiler options were added in this release.</span></span>

<span data-ttu-id="9e4d0-108">Následující nové funkce podporují motiv lepší výkon pro bezpečný kód:</span><span class="sxs-lookup"><span data-stu-id="9e4d0-108">The following new features support the theme of better performance for safe code:</span></span>

- <span data-ttu-id="9e4d0-109">Oprava pole máte přístup bez Připnutí.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-109">You can access fixed fields without pinning.</span></span>
- <span data-ttu-id="9e4d0-110">Můžete opětovně přiřazovat `ref` lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-110">You can reassign `ref` local variables.</span></span>
- <span data-ttu-id="9e4d0-111">Inicializátory můžete použít na `stackalloc` pole.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-111">You can use initializers on `stackalloc` arrays.</span></span>
- <span data-ttu-id="9e4d0-112">Můžete použít `fixed` příkazy s libovolný typ, který podporuje vzoru.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-112">You can use `fixed` statements with any type that supports a pattern.</span></span>
- <span data-ttu-id="9e4d0-113">Můžete použít další obecná omezení.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-113">You can use additional generic constraints.</span></span>

<span data-ttu-id="9e4d0-114">Byly provedeny následující vylepšení stávajících funkcí:</span><span class="sxs-lookup"><span data-stu-id="9e4d0-114">The following enhancements were made to existing features:</span></span>

- <span data-ttu-id="9e4d0-115">Můžete otestovat `==` a `!=` s typy řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-115">You can test `==` and `!=` with tuple types.</span></span>
- <span data-ttu-id="9e4d0-116">Proměnné výrazů můžete použít na více místech.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-116">You can use expression variables in more locations.</span></span>
- <span data-ttu-id="9e4d0-117">Atributy mohou připojit k pomocné pole automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-117">You may attach attributes to the backing field of auto-implemented properties.</span></span>
- <span data-ttu-id="9e4d0-118">Metoda rozlišení při argumenty liší `in` byla vylepšena.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-118">Method resolution when arguments differ by `in` has been improved.</span></span>
- <span data-ttu-id="9e4d0-119">Řešení přetížení má nyní méně dvojznačné případy.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-119">Overload resolution now has fewer ambiguous cases.</span></span>

<span data-ttu-id="9e4d0-120">Nové možnosti kompilátoru jsou:</span><span class="sxs-lookup"><span data-stu-id="9e4d0-120">The new compiler options are:</span></span>

- <span data-ttu-id="9e4d0-121">`-publicsign` Chcete-li povolit, Open Source Software (OSS) podepisování sestavení.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-121">`-publicsign` to enable Open Source Software (OSS) signing of assemblies.</span></span>
- <span data-ttu-id="9e4d0-122">`-pathmap` Chcete-li zadat mapování pro adresáře zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-122">`-pathmap` to provide a mapping for source directories.</span></span>

<span data-ttu-id="9e4d0-123">Zbývající část tohoto článku poskytuje podrobnosti a odkazy na další informace o každé vylepšení.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-123">The remainder of this article provides details and links to learn more about each of the improvements.</span></span>

## <a name="enabling-more-efficient-safe-code"></a><span data-ttu-id="9e4d0-124">Povolení efektivnější bezpečný kód</span><span class="sxs-lookup"><span data-stu-id="9e4d0-124">Enabling more efficient safe code</span></span>

<span data-ttu-id="9e4d0-125">Je třeba schopni napsat kód jazyka C#, bezpečně, který funguje stejně dobře jako nezabezpečený kód.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-125">You should be able to write C# code safely that performs as well as unsafe code.</span></span> <span data-ttu-id="9e4d0-126">Nouzový kód se vyhnete třídy chyb, jako je například přetečení vyrovnávací paměti, ukazatele stray a další chyby přístupu k paměti.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-126">Safe code avoids classes of errors, such as buffer overruns, stray pointers, and other memory access errors.</span></span> <span data-ttu-id="9e4d0-127">Tyto nové funkce rozšířili schopnosti ověřitelný bezpečný kód.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-127">These new features expand the capabilities of verifiable safe code.</span></span> <span data-ttu-id="9e4d0-128">Snažit se psát více kódu pomocí bezpečné konstrukce.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-128">Strive to write more of your code using safe constructs.</span></span> <span data-ttu-id="9e4d0-129">Tyto funkce to usnadní.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-129">These features make that easier.</span></span>

### <a name="indexing-fixed-fields-does-not-require-pinning"></a><span data-ttu-id="9e4d0-130">Indexování `fixed` pole nevyžaduje Připnutí</span><span class="sxs-lookup"><span data-stu-id="9e4d0-130">Indexing `fixed` fields does not require pinning</span></span>

<span data-ttu-id="9e4d0-131">Vezměte v úvahu tuto strukturu:</span><span class="sxs-lookup"><span data-stu-id="9e4d0-131">Consider this struct:</span></span>

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

<span data-ttu-id="9e4d0-132">V dřívějších verzích jazyka C#, jste museli připnout proměnnou pro přístup k jedné celých čísel, které jsou součástí `myFixedField`.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-132">In earlier versions of C#, you needed to pin a variable to access one of the integers that are part of `myFixedField`.</span></span> <span data-ttu-id="9e4d0-133">Nyní následující kód se zkompiluje v nouzovém kontextu:</span><span class="sxs-lookup"><span data-stu-id="9e4d0-133">Now, the following code compiles in a safe context:</span></span>

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

<span data-ttu-id="9e4d0-134">Proměnná `p` přistupuje k jeden prvek `myFixedField`.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-134">The variable `p` accesses one element in `myFixedField`.</span></span> <span data-ttu-id="9e4d0-135">Není nutné pro deklaraci samostatné `int*` proměnné.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-135">You don't need to declare a separate `int*` variable.</span></span> <span data-ttu-id="9e4d0-136">Všimněte si, že se můžete stále potřebovat `unsafe` kontextu.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-136">Note that you still need an `unsafe` context.</span></span> <span data-ttu-id="9e4d0-137">V dřívějších verzích jazyka C# musíte deklarovat ukazatel druhý pevné:</span><span class="sxs-lookup"><span data-stu-id="9e4d0-137">In earlier versions of C#, you need to declare a second fixed pointer:</span></span>

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

<span data-ttu-id="9e4d0-138">Další informace najdete v článku na [ `fixed` příkaz](../language-reference/keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9e4d0-138">For more information, see the article on the [`fixed` statement](../language-reference/keywords/fixed-statement.md).</span></span>

### <a name="ref-local-variables-may-be-reassigned"></a><span data-ttu-id="9e4d0-139">`ref` může být přeřazen lokální proměnné</span><span class="sxs-lookup"><span data-stu-id="9e4d0-139">`ref` local variables may be reassigned</span></span>

<span data-ttu-id="9e4d0-140">Nyní `ref` k odkazování na různých instancích po jejich inicializaci může být přeřazen místních hodnot.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-140">Now, `ref` locals may be reassigned to refer to different instances after being initialized.</span></span> <span data-ttu-id="9e4d0-141">Následující kód nyní kompiluje:</span><span class="sxs-lookup"><span data-stu-id="9e4d0-141">The following code now compiles:</span></span>

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

<span data-ttu-id="9e4d0-142">Další informace najdete v článku na [ `ref` vrátí a `ref` lokální](../programming-guide/classes-and-structs/ref-returns.md)a v článku věnovaném [ `foreach` ](../language-reference/keywords/foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="9e4d0-142">For more information, see the article on [`ref` returns and `ref` locals](../programming-guide/classes-and-structs/ref-returns.md), and the article on [`foreach`](../language-reference/keywords/foreach-in.md).</span></span>

### <a name="stackalloc-arrays-support-initializers"></a><span data-ttu-id="9e4d0-143">`stackalloc` pole podporují inicializátory</span><span class="sxs-lookup"><span data-stu-id="9e4d0-143">`stackalloc` arrays support initializers</span></span>

<span data-ttu-id="9e4d0-144">Je možné zadat hodnoty pro prvky v poli, když ji inicializovat:</span><span class="sxs-lookup"><span data-stu-id="9e4d0-144">You've been able to specify the values for elements in an array when you initialize it:</span></span>

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

<span data-ttu-id="9e4d0-145">Nyní, stejné syntaxe lze použít u polí, které jsou deklarovány pomocí `stackalloc`:</span><span class="sxs-lookup"><span data-stu-id="9e4d0-145">Now, that same syntax can be applied to arrays that are declared with `stackalloc`:</span></span>

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

<span data-ttu-id="9e4d0-146">Další informace najdete v tématu [ `stackalloc` příkaz](../language-reference/keywords/stackalloc.md) článek v referenční příručka jazyka.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-146">For more information, see the [`stackalloc` statement](../language-reference/keywords/stackalloc.md) article in the language reference.</span></span>

### <a name="more-types-support-the-fixed-statement"></a><span data-ttu-id="9e4d0-147">Podpora dalších typů `fixed` – příkaz</span><span class="sxs-lookup"><span data-stu-id="9e4d0-147">More types support the `fixed` statement</span></span>

<span data-ttu-id="9e4d0-148">`fixed` Příkaz podporován omezenou sadu typů.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-148">The `fixed` statement supported a limited set of types.</span></span> <span data-ttu-id="9e4d0-149">Od verze C# 7.3, libovolný typ, který obsahuje `GetPinnableReference()` metodu, která vrací `ref T` nebo `ref readonly T` může být `fixed`.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-149">Starting with C# 7.3, any type that contains a `GetPinnableReference()` method that returns a `ref T` or `ref readonly T` may be `fixed`.</span></span> <span data-ttu-id="9e4d0-150">Přidání této funkce znamená, že `fixed` jde použít s <xref:System.Span%601?displayProperty=nameWithType> a souvisejících typů.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-150">Adding this feature means that `fixed` can be used with <xref:System.Span%601?displayProperty=nameWithType> and related types.</span></span>

<span data-ttu-id="9e4d0-151">Další informace najdete v tématu [ `fixed` příkaz](../language-reference/keywords/fixed-statement.md) článek v referenční příručka jazyka.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-151">For more information, see the [`fixed` statement](../language-reference/keywords/fixed-statement.md) article in the language reference.</span></span>

### <a name="enhanced-generic-constraints"></a><span data-ttu-id="9e4d0-152">Vylepšené obecná omezení</span><span class="sxs-lookup"><span data-stu-id="9e4d0-152">Enhanced generic constraints</span></span>

<span data-ttu-id="9e4d0-153">Teď můžete zadat typ <xref:System.Enum?displayProperty=nameWithType> nebo <xref:System.Delegate?displayProperty=nameWithType> jako základní třída omezení parametru typu.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-153">You can now specify the type <xref:System.Enum?displayProperty=nameWithType> or <xref:System.Delegate?displayProperty=nameWithType> as base class constraints for a type parameter.</span></span>

<span data-ttu-id="9e4d0-154">Můžete také použít novou `unmanaged` omezení, chcete-li určit, že musí být parametr typu **nespravovaný typ**.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-154">You can also use the new `unmanaged` constraint, to specify that a type parameter must be an **unmanaged type**.</span></span> <span data-ttu-id="9e4d0-155">**Nespravovaný typ** je typ, který není typem odkazu a neobsahuje jakéhokoliv odkazového typu na libovolné úrovni vnoření.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-155">An **unmanaged type** is a type that isn't a reference type and doesn't contain any reference type at any level of nesting.</span></span>

<span data-ttu-id="9e4d0-156">Další informace najdete v článcích na [ `where` obecná omezení](../language-reference/keywords/where-generic-type-constraint.md) a [omezení parametrů typů](../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="9e4d0-156">For more information, see the articles on [`where` generic constraints](../language-reference/keywords/where-generic-type-constraint.md) and [constraints on type parameters](../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="9e4d0-157">Přidání k existujícím typům těchto omezení je [nekompatibilní změna](version-update-considerations.md#incompatible-changes).</span><span class="sxs-lookup"><span data-stu-id="9e4d0-157">Adding these constraints to existing types is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="9e4d0-158">Uzavřených obecných typů pravděpodobně přestane splňovat tyto nové omezení.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-158">Closed generic types may no longer meet these new constraints.</span></span>

## <a name="make-existing-features-better"></a><span data-ttu-id="9e4d0-159">Vylepšit stávajících funkcí</span><span class="sxs-lookup"><span data-stu-id="9e4d0-159">Make existing features better</span></span>

<span data-ttu-id="9e4d0-160">Druhý motiv přináší vylepšení v oblasti funkce v jazyce.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-160">The second theme provides improvements to features in the language.</span></span> <span data-ttu-id="9e4d0-161">Tyto funkce, zvyšují produktivitu při psaní C#.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-161">These features improve productivity when writing C#.</span></span>

### <a name="tuples-support--and-"></a><span data-ttu-id="9e4d0-162">Podpora řazených kolekcí členů `==` a `!=`</span><span class="sxs-lookup"><span data-stu-id="9e4d0-162">Tuples support `==` and `!=`</span></span>

<span data-ttu-id="9e4d0-163">C# řazené kolekce členů typů teď podporují `==` a `!=`.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-163">The C# tuple types now support `==` and `!=`.</span></span> <span data-ttu-id="9e4d0-164">Další informace najdete v oddílu, mezi které patří [rovnosti](../tuples.md#equality-and-tuples) v článku věnovaném [řazených kolekcí členů](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="9e4d0-164">For more information, see the section covering [equality](../tuples.md#equality-and-tuples) in the article on [tuples](../tuples.md).</span></span>

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a><span data-ttu-id="9e4d0-165">Připojit atributy na pomocné pole automaticky implementované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9e4d0-165">Attach attributes to the backing fields for auto-implemented properties</span></span>

<span data-ttu-id="9e4d0-166">Tato syntaxe se teď podporuje:</span><span class="sxs-lookup"><span data-stu-id="9e4d0-166">This syntax is now supported:</span></span>

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

<span data-ttu-id="9e4d0-167">Atribut `SomeThingAboutFieldAttribute` platí pro generovaný kompilátorem pomocné pole `SomeProperty`.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-167">The attribute `SomeThingAboutFieldAttribute` is applied to the compiler generated backing field for `SomeProperty`.</span></span> <span data-ttu-id="9e4d0-168">Další informace najdete v tématu [atributy](../programming-guide/concepts/attributes/index.md) v Průvodci programovacího jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-168">For more information, see [attributes](../programming-guide/concepts/attributes/index.md) in the C# programming guide.</span></span>

### <a name="in-method-overload-resolution-tiebreaker"></a><span data-ttu-id="9e4d0-169">`in` rozhodujícího prvku rozlišení přetížení – metoda</span><span class="sxs-lookup"><span data-stu-id="9e4d0-169">`in` method overload resolution tiebreaker</span></span>

<span data-ttu-id="9e4d0-170">Když `in` byl přidán modifikátor argument, tyto dvě metody by způsobit nejednoznačnost:</span><span class="sxs-lookup"><span data-stu-id="9e4d0-170">When the `in` argument modifier was added, these two methods would cause an ambiguity:</span></span>

```csharp
static void M(S arg);
static void M(in S arg);
```

<span data-ttu-id="9e4d0-171">Nyní podle hodnoty (první v předchozím příkladu) je lepší než přetížení odkaz verze jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-171">Now, the by value (first in the preceding example) overload is better than the by readonly reference version.</span></span> <span data-ttu-id="9e4d0-172">Pro volání verze s argumentem reference jen pro čtení, je nutné zahrnout `in` modifikátor při volání metody.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-172">To call the version with the readonly reference argument, you must include the `in` modifier when calling the method.</span></span>

> [!NOTE]
> <span data-ttu-id="9e4d0-173">To bylo implementováno jako oprava chyby.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-173">This was implemented as a bug fix.</span></span> <span data-ttu-id="9e4d0-174">To už je nejednoznačný i přes jazykové verze nastavena na "7.2".</span><span class="sxs-lookup"><span data-stu-id="9e4d0-174">This no longer is ambiguous even with the language version set to "7.2".</span></span>

<span data-ttu-id="9e4d0-175">Další informace najdete v článku na [ `in` modifikátor parametru](../language-reference/keywords/in-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="9e4d0-175">For more information, see the article on the [`in` parameter modifier](../language-reference/keywords/in-parameter-modifier.md).</span></span>

### <a name="extend-expression-variables-in-initializers"></a><span data-ttu-id="9e4d0-176">Rozšíření proměnných výrazu v inicializátorech</span><span class="sxs-lookup"><span data-stu-id="9e4d0-176">Extend expression variables in initializers</span></span>

<span data-ttu-id="9e4d0-177">Syntaxe v jazyce C# 7.0 umožňuje přidat `out` deklarace proměnných rozšířilo a obsahovat Inicializátory pole, vlastnosti, inicializátory konstruktoru a klauzulí dotazů.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-177">The syntax added in C# 7.0 to allow `out` variable declarations has been extended to include field initializers, property initializers, constructor initializers, and query clauses.</span></span> <span data-ttu-id="9e4d0-178">To umožňuje kódu jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9e4d0-178">It enables code such as the following example:</span></span>

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

### <a name="improved-overload-candidates"></a><span data-ttu-id="9e4d0-179">Vylepšené přetížení kandidáty</span><span class="sxs-lookup"><span data-stu-id="9e4d0-179">Improved overload candidates</span></span>

<span data-ttu-id="9e4d0-180">V každé verzi pravidla rozlišení přetížení aktualizovat na situace, kdy mají "viditelných" volba volání metod nejednoznačný.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-180">In every release, the overload resolution rules get updated to address situations where ambiguous method invocations have an "obvious" choice.</span></span> <span data-ttu-id="9e4d0-181">Tato verze přidává tři nová pravidla ke kompilátoru vyberte jasnou volbou:</span><span class="sxs-lookup"><span data-stu-id="9e4d0-181">This release adds three new rules to help the compiler pick the obvious choice:</span></span>

1. <span data-ttu-id="9e4d0-182">Pokud skupina metoda obsahuje instanci a statické členy, kompilátor zahodí členy instance, pokud metoda byla vyvolána bez instance příjemce nebo kontextu.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-182">When a method group contains both instance and static members, the compiler discards the instance members if the method was invoked without an instance receiver or context.</span></span> <span data-ttu-id="9e4d0-183">Kompilátor zahodí statické členy, pokud metoda byla vyvolána s přijímače instance.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-183">The compiler discards the static members if the method was invoked with an instance receiver.</span></span> <span data-ttu-id="9e4d0-184">Pokud není žádný příjemce, kompilátor obsahuje pouze statické členy ve statickém kontextu, v opačném případě statických a členy instance.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-184">When there is no receiver, the compiler includes only static members in a static context, otherwise both static and instance members.</span></span> <span data-ttu-id="9e4d0-185">Když příjemce ambiguously instance nebo typ, kompilátor obsahuje.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-185">When the receiver is ambiguously an instance or type, the compiler includes both.</span></span> <span data-ttu-id="9e4d0-186">Statického kontextu, kde je implicitní `this` příjemce instanci nelze použít, obsahuje tělo členů, pokud `this` je definován, jako je například statické členy, jakož i kdy, kde `this` nelze použít, jako je například Inicializátory polí a Inicializátory konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-186">A static context, where an implicit `this` instance receiver cannot be used, includes the body of members where no `this` is defined, such as static members, as well as places where `this` cannot be used, such as field initializers and constructor-initializers.</span></span>
1. <span data-ttu-id="9e4d0-187">Pokud metoda skupina obsahuje některé obecné metody, jejichž argumentů typu nevyhovuje požadavkům jejich omezení, tyto členy, se odeberou ze sady Release candidate.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-187">When a method group contains some generic methods whose type arguments do not satisfy their constraints, these members are removed from the candidate set.</span></span>
1. <span data-ttu-id="9e4d0-188">Pro skupiny převod metody vrátí metody Release candidate, jejíž návratový typ neshoduje s delegáta typu se odeberou ze sady.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-188">For a method group conversion, candidate methods whose return type doesn't match up with the delegate's return type are removed from the set.</span></span>

<span data-ttu-id="9e4d0-189">Tato změna všimnout pouze vzhledem k tomu, že zjistíte méně chyb kompilátoru pro přetížení metody nejednoznačný když jste si jisti, jakou metodu je lepší.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-189">You'll only notice this change because you'll find fewer compiler errors for ambiguous method overloads when you are sure which method is better.</span></span>

## <a name="new-compiler-options"></a><span data-ttu-id="9e4d0-190">Nové možnosti kompilátoru</span><span class="sxs-lookup"><span data-stu-id="9e4d0-190">New compiler options</span></span>

<span data-ttu-id="9e4d0-191">Nové možnosti kompilátoru podporují scénáře DevOps a nové sestavení pro programy C#.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-191">New compiler options support new build and DevOps scenarios for C# programs.</span></span>

### <a name="public-or-open-source-signing"></a><span data-ttu-id="9e4d0-192">Veřejný nebo podepisování Open Source</span><span class="sxs-lookup"><span data-stu-id="9e4d0-192">Public or Open Source signing</span></span>

<span data-ttu-id="9e4d0-193">`-publicsign` – Možnost kompilátoru instruuje kompilátor, aby podepište sestavení pomocí veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-193">The `-publicsign` compiler option instructs the compiler to sign the assembly using a public key.</span></span> <span data-ttu-id="9e4d0-194">Sestava je označena jako podepsané, ale signatura je převzata z veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-194">The assembly is marked as signed, but the signature is taken from the public key.</span></span> <span data-ttu-id="9e4d0-195">Tato možnost vám umožní sestavovat podepsaná sestavení z open-source projektů pomocí veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-195">This option enables you to build signed assemblies from open-source projects using a public key.</span></span>

<span data-ttu-id="9e4d0-196">Další informace najdete v tématu [– možnost kompilátoru - publicsign](../language-reference/compiler-options/publicsign-compiler-option.md) článku.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-196">For more information, see the [-publicsign compiler option](../language-reference/compiler-options/publicsign-compiler-option.md) article.</span></span>

### <a name="pathmap"></a><span data-ttu-id="9e4d0-197">pathmap</span><span class="sxs-lookup"><span data-stu-id="9e4d0-197">pathmap</span></span>

<span data-ttu-id="9e4d0-198">`-pathmap` – Možnost kompilátoru instruuje kompilátor, aby nahraďte mapované zdrojových cest zdrojových cest z prostředí pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-198">The `-pathmap` compiler option instructs the compiler to replace source paths from the build environment with mapped source paths.</span></span> <span data-ttu-id="9e4d0-199">`-pathmap` Možnost řídí napsaný v kompilátoru pro soubory PDB nebo pro zdrojovou cestu <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-199">The `-pathmap` option controls the source path written by the compiler to PDB files or for the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span></span>

<span data-ttu-id="9e4d0-200">Další informace najdete v tématu [– možnost kompilátoru - pathmap](../language-reference/compiler-options/pathmap-compiler-option.md) článku.</span><span class="sxs-lookup"><span data-stu-id="9e4d0-200">For more information, see the [-pathmap compiler option](../language-reference/compiler-options/pathmap-compiler-option.md) article.</span></span>
