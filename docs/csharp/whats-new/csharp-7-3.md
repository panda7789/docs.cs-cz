---
title: Co je nového v jazyce C# 7.3
description: Přehled nových funkcí v jazyce C# 7.3
ms.date: 05/16/2018
ms.openlocfilehash: 4e45893be671b707efbde352eef04fa92af94954
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2019
ms.locfileid: "67347409"
---
# <a name="whats-new-in-c-73"></a><span data-ttu-id="cdecb-103">Co je nového v jazyce C# 7.3</span><span class="sxs-lookup"><span data-stu-id="cdecb-103">What's new in C# 7.3</span></span>

<span data-ttu-id="cdecb-104">Existují dva hlavní motivy na verzi C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="cdecb-104">There are two main themes to the C# 7.3 release.</span></span> <span data-ttu-id="cdecb-105">Jeden motiv poskytuje funkce, které umožňují bezpečný kód, které funguje jako nezabezpečený kód.</span><span class="sxs-lookup"><span data-stu-id="cdecb-105">One theme provides features that enable safe code to be as performant as unsafe code.</span></span> <span data-ttu-id="cdecb-106">Druhý motiv poskytuje několik postupných vylepšení stávajících funkcí.</span><span class="sxs-lookup"><span data-stu-id="cdecb-106">The second theme provides incremental improvements to existing features.</span></span> <span data-ttu-id="cdecb-107">Kromě toho byly přidány nové možnosti kompilátoru v této verzi.</span><span class="sxs-lookup"><span data-stu-id="cdecb-107">In addition, new compiler options were added in this release.</span></span>

<span data-ttu-id="cdecb-108">Následující nové funkce podporují motiv lepší výkon pro bezpečný kód:</span><span class="sxs-lookup"><span data-stu-id="cdecb-108">The following new features support the theme of better performance for safe code:</span></span>

- <span data-ttu-id="cdecb-109">Oprava pole máte přístup bez Připnutí.</span><span class="sxs-lookup"><span data-stu-id="cdecb-109">You can access fixed fields without pinning.</span></span>
- <span data-ttu-id="cdecb-110">Můžete opětovně přiřazovat `ref` lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="cdecb-110">You can reassign `ref` local variables.</span></span>
- <span data-ttu-id="cdecb-111">Inicializátory můžete použít na `stackalloc` pole.</span><span class="sxs-lookup"><span data-stu-id="cdecb-111">You can use initializers on `stackalloc` arrays.</span></span>
- <span data-ttu-id="cdecb-112">Můžete použít `fixed` příkazy s libovolný typ, který podporuje vzoru.</span><span class="sxs-lookup"><span data-stu-id="cdecb-112">You can use `fixed` statements with any type that supports a pattern.</span></span>
- <span data-ttu-id="cdecb-113">Můžete použít další obecná omezení.</span><span class="sxs-lookup"><span data-stu-id="cdecb-113">You can use additional generic constraints.</span></span>

<span data-ttu-id="cdecb-114">Byly provedeny následující vylepšení stávajících funkcí:</span><span class="sxs-lookup"><span data-stu-id="cdecb-114">The following enhancements were made to existing features:</span></span>

- <span data-ttu-id="cdecb-115">Můžete otestovat `==` a `!=` s typy řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="cdecb-115">You can test `==` and `!=` with tuple types.</span></span>
- <span data-ttu-id="cdecb-116">Proměnné výrazů můžete použít na více místech.</span><span class="sxs-lookup"><span data-stu-id="cdecb-116">You can use expression variables in more locations.</span></span>
- <span data-ttu-id="cdecb-117">Atributy mohou připojit k pomocné pole automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cdecb-117">You may attach attributes to the backing field of auto-implemented properties.</span></span>
- <span data-ttu-id="cdecb-118">Metoda rozlišení při argumenty liší `in` byla vylepšena.</span><span class="sxs-lookup"><span data-stu-id="cdecb-118">Method resolution when arguments differ by `in` has been improved.</span></span>
- <span data-ttu-id="cdecb-119">Řešení přetížení má nyní méně dvojznačné případy.</span><span class="sxs-lookup"><span data-stu-id="cdecb-119">Overload resolution now has fewer ambiguous cases.</span></span>

<span data-ttu-id="cdecb-120">Nové možnosti kompilátoru jsou:</span><span class="sxs-lookup"><span data-stu-id="cdecb-120">The new compiler options are:</span></span>

- <span data-ttu-id="cdecb-121">`-publicsign` Chcete-li povolit, Open Source Software (OSS) podepisování sestavení.</span><span class="sxs-lookup"><span data-stu-id="cdecb-121">`-publicsign` to enable Open Source Software (OSS) signing of assemblies.</span></span>
- <span data-ttu-id="cdecb-122">`-pathmap` Chcete-li zadat mapování pro adresáře zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="cdecb-122">`-pathmap` to provide a mapping for source directories.</span></span>

<span data-ttu-id="cdecb-123">Zbývající část tohoto článku poskytuje podrobnosti a odkazy na další informace o každé vylepšení.</span><span class="sxs-lookup"><span data-stu-id="cdecb-123">The remainder of this article provides details and links to learn more about each of the improvements.</span></span> <span data-ttu-id="cdecb-124">Můžete prozkoumat tyto funkce v prostředí pomocí `dotnet try` globální nástroje:</span><span class="sxs-lookup"><span data-stu-id="cdecb-124">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="cdecb-125">Nainstalujte [dotnet – zkuste](https://github.com/dotnet/try/blob/master/README.md#setup) globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="cdecb-125">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="cdecb-126">Klonování [dotnet/try-samples](https://github.com/dotnet/try-samples) úložiště.</span><span class="sxs-lookup"><span data-stu-id="cdecb-126">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="cdecb-127">Nastavit aktuální adresář *csharp7* podadresář pro *try-samples* úložiště.</span><span class="sxs-lookup"><span data-stu-id="cdecb-127">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="cdecb-128">Spusťte `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="cdecb-128">Run `dotnet try`.</span></span>


## <a name="enabling-more-efficient-safe-code"></a><span data-ttu-id="cdecb-129">Povolení efektivnější bezpečný kód</span><span class="sxs-lookup"><span data-stu-id="cdecb-129">Enabling more efficient safe code</span></span>

<span data-ttu-id="cdecb-130">Je třeba schopni napsat kód jazyka C#, bezpečně, který funguje stejně dobře jako nezabezpečený kód.</span><span class="sxs-lookup"><span data-stu-id="cdecb-130">You should be able to write C# code safely that performs as well as unsafe code.</span></span> <span data-ttu-id="cdecb-131">Nouzový kód se vyhnete třídy chyb, jako je například přetečení vyrovnávací paměti, ukazatele stray a další chyby přístupu k paměti.</span><span class="sxs-lookup"><span data-stu-id="cdecb-131">Safe code avoids classes of errors, such as buffer overruns, stray pointers, and other memory access errors.</span></span> <span data-ttu-id="cdecb-132">Tyto nové funkce rozšířili schopnosti ověřitelný bezpečný kód.</span><span class="sxs-lookup"><span data-stu-id="cdecb-132">These new features expand the capabilities of verifiable safe code.</span></span> <span data-ttu-id="cdecb-133">Snažit se psát více kódu pomocí bezpečné konstrukce.</span><span class="sxs-lookup"><span data-stu-id="cdecb-133">Strive to write more of your code using safe constructs.</span></span> <span data-ttu-id="cdecb-134">Tyto funkce to usnadní.</span><span class="sxs-lookup"><span data-stu-id="cdecb-134">These features make that easier.</span></span>

### <a name="indexing-fixed-fields-does-not-require-pinning"></a><span data-ttu-id="cdecb-135">Indexování `fixed` pole nevyžaduje Připnutí</span><span class="sxs-lookup"><span data-stu-id="cdecb-135">Indexing `fixed` fields does not require pinning</span></span>

<span data-ttu-id="cdecb-136">Vezměte v úvahu tuto strukturu:</span><span class="sxs-lookup"><span data-stu-id="cdecb-136">Consider this struct:</span></span>

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

<span data-ttu-id="cdecb-137">V dřívějších verzích jazyka C#, jste museli připnout proměnnou pro přístup k jedné celých čísel, které jsou součástí `myFixedField`.</span><span class="sxs-lookup"><span data-stu-id="cdecb-137">In earlier versions of C#, you needed to pin a variable to access one of the integers that are part of `myFixedField`.</span></span> <span data-ttu-id="cdecb-138">Nyní, následující kód zkompiluje bez Připnutí proměnné `p` uvnitř samostatné `fixed` – příkaz:</span><span class="sxs-lookup"><span data-stu-id="cdecb-138">Now, the following code compiles without pinning the variable `p` inside a separate `fixed` statement:</span></span>

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

<span data-ttu-id="cdecb-139">Proměnná `p` přistupuje k jeden prvek `myFixedField`.</span><span class="sxs-lookup"><span data-stu-id="cdecb-139">The variable `p` accesses one element in `myFixedField`.</span></span> <span data-ttu-id="cdecb-140">Není nutné pro deklaraci samostatné `int*` proměnné.</span><span class="sxs-lookup"><span data-stu-id="cdecb-140">You don't need to declare a separate `int*` variable.</span></span> <span data-ttu-id="cdecb-141">Všimněte si, že se můžete stále potřebovat `unsafe` kontextu.</span><span class="sxs-lookup"><span data-stu-id="cdecb-141">Note that you still need an `unsafe` context.</span></span> <span data-ttu-id="cdecb-142">V dřívějších verzích jazyka C# musíte deklarovat ukazatel druhý pevné:</span><span class="sxs-lookup"><span data-stu-id="cdecb-142">In earlier versions of C#, you need to declare a second fixed pointer:</span></span>

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

<span data-ttu-id="cdecb-143">Další informace najdete v článku na [ `fixed` příkaz](../language-reference/keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cdecb-143">For more information, see the article on the [`fixed` statement](../language-reference/keywords/fixed-statement.md).</span></span>

### <a name="ref-local-variables-may-be-reassigned"></a><span data-ttu-id="cdecb-144">`ref` může být přeřazen lokální proměnné</span><span class="sxs-lookup"><span data-stu-id="cdecb-144">`ref` local variables may be reassigned</span></span>

<span data-ttu-id="cdecb-145">Nyní `ref` k odkazování na různých instancích po jejich inicializaci může být přeřazen místních hodnot.</span><span class="sxs-lookup"><span data-stu-id="cdecb-145">Now, `ref` locals may be reassigned to refer to different instances after being initialized.</span></span> <span data-ttu-id="cdecb-146">Následující kód nyní kompiluje:</span><span class="sxs-lookup"><span data-stu-id="cdecb-146">The following code now compiles:</span></span>

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

<span data-ttu-id="cdecb-147">Další informace najdete v článku na [ `ref` vrátí a `ref` lokální](../programming-guide/classes-and-structs/ref-returns.md)a v článku věnovaném [ `foreach` ](../language-reference/keywords/foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="cdecb-147">For more information, see the article on [`ref` returns and `ref` locals](../programming-guide/classes-and-structs/ref-returns.md), and the article on [`foreach`](../language-reference/keywords/foreach-in.md).</span></span>

### <a name="stackalloc-arrays-support-initializers"></a><span data-ttu-id="cdecb-148">`stackalloc` pole podporují inicializátory</span><span class="sxs-lookup"><span data-stu-id="cdecb-148">`stackalloc` arrays support initializers</span></span>

<span data-ttu-id="cdecb-149">Je možné zadat hodnoty pro prvky v poli, když ji inicializovat:</span><span class="sxs-lookup"><span data-stu-id="cdecb-149">You've been able to specify the values for elements in an array when you initialize it:</span></span>

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

<span data-ttu-id="cdecb-150">Nyní, stejné syntaxe lze použít u polí, které jsou deklarovány pomocí `stackalloc`:</span><span class="sxs-lookup"><span data-stu-id="cdecb-150">Now, that same syntax can be applied to arrays that are declared with `stackalloc`:</span></span>

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

<span data-ttu-id="cdecb-151">Další informace najdete v tématu [ `stackalloc` operátor](../language-reference/operators/stackalloc.md) článku.</span><span class="sxs-lookup"><span data-stu-id="cdecb-151">For more information, see the [`stackalloc` operator](../language-reference/operators/stackalloc.md) article.</span></span>

### <a name="more-types-support-the-fixed-statement"></a><span data-ttu-id="cdecb-152">Podpora dalších typů `fixed` – příkaz</span><span class="sxs-lookup"><span data-stu-id="cdecb-152">More types support the `fixed` statement</span></span>

<span data-ttu-id="cdecb-153">`fixed` Příkaz podporován omezenou sadu typů.</span><span class="sxs-lookup"><span data-stu-id="cdecb-153">The `fixed` statement supported a limited set of types.</span></span> <span data-ttu-id="cdecb-154">Od verze C# 7.3, libovolný typ, který obsahuje `GetPinnableReference()` metodu, která vrací `ref T` nebo `ref readonly T` může být `fixed`.</span><span class="sxs-lookup"><span data-stu-id="cdecb-154">Starting with C# 7.3, any type that contains a `GetPinnableReference()` method that returns a `ref T` or `ref readonly T` may be `fixed`.</span></span> <span data-ttu-id="cdecb-155">Přidání této funkce znamená, že `fixed` jde použít s <xref:System.Span%601?displayProperty=nameWithType> a souvisejících typů.</span><span class="sxs-lookup"><span data-stu-id="cdecb-155">Adding this feature means that `fixed` can be used with <xref:System.Span%601?displayProperty=nameWithType> and related types.</span></span>

<span data-ttu-id="cdecb-156">Další informace najdete v tématu [ `fixed` příkaz](../language-reference/keywords/fixed-statement.md) článek v referenční příručka jazyka.</span><span class="sxs-lookup"><span data-stu-id="cdecb-156">For more information, see the [`fixed` statement](../language-reference/keywords/fixed-statement.md) article in the language reference.</span></span>

### <a name="enhanced-generic-constraints"></a><span data-ttu-id="cdecb-157">Vylepšené obecná omezení</span><span class="sxs-lookup"><span data-stu-id="cdecb-157">Enhanced generic constraints</span></span>

<span data-ttu-id="cdecb-158">Teď můžete zadat typ <xref:System.Enum?displayProperty=nameWithType> nebo <xref:System.Delegate?displayProperty=nameWithType> jako základní třída omezení parametru typu.</span><span class="sxs-lookup"><span data-stu-id="cdecb-158">You can now specify the type <xref:System.Enum?displayProperty=nameWithType> or <xref:System.Delegate?displayProperty=nameWithType> as base class constraints for a type parameter.</span></span>

<span data-ttu-id="cdecb-159">Můžete také použít novou `unmanaged` omezení, chcete-li určit, že musí být parametr typu **nespravovaný typ**.</span><span class="sxs-lookup"><span data-stu-id="cdecb-159">You can also use the new `unmanaged` constraint, to specify that a type parameter must be an **unmanaged type**.</span></span> <span data-ttu-id="cdecb-160">**Nespravovaný typ** je typ, který není typem odkazu a neobsahuje jakéhokoliv odkazového typu na libovolné úrovni vnoření.</span><span class="sxs-lookup"><span data-stu-id="cdecb-160">An **unmanaged type** is a type that isn't a reference type and doesn't contain any reference type at any level of nesting.</span></span>

<span data-ttu-id="cdecb-161">Další informace najdete v článcích na [ `where` obecná omezení](../language-reference/keywords/where-generic-type-constraint.md) a [omezení parametrů typů](../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="cdecb-161">For more information, see the articles on [`where` generic constraints](../language-reference/keywords/where-generic-type-constraint.md) and [constraints on type parameters](../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="cdecb-162">Přidání k existujícím typům těchto omezení je [nekompatibilní změna](version-update-considerations.md#incompatible-changes).</span><span class="sxs-lookup"><span data-stu-id="cdecb-162">Adding these constraints to existing types is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="cdecb-163">Uzavřených obecných typů pravděpodobně přestane splňovat tyto nové omezení.</span><span class="sxs-lookup"><span data-stu-id="cdecb-163">Closed generic types may no longer meet these new constraints.</span></span>

## <a name="make-existing-features-better"></a><span data-ttu-id="cdecb-164">Vylepšit stávajících funkcí</span><span class="sxs-lookup"><span data-stu-id="cdecb-164">Make existing features better</span></span>

<span data-ttu-id="cdecb-165">Druhý motiv přináší vylepšení v oblasti funkce v jazyce.</span><span class="sxs-lookup"><span data-stu-id="cdecb-165">The second theme provides improvements to features in the language.</span></span> <span data-ttu-id="cdecb-166">Tyto funkce, zvyšují produktivitu při psaní C#.</span><span class="sxs-lookup"><span data-stu-id="cdecb-166">These features improve productivity when writing C#.</span></span>

### <a name="tuples-support--and-"></a><span data-ttu-id="cdecb-167">Podpora řazených kolekcí členů `==` a `!=`</span><span class="sxs-lookup"><span data-stu-id="cdecb-167">Tuples support `==` and `!=`</span></span>

<span data-ttu-id="cdecb-168">C# řazené kolekce členů typů teď podporují `==` a `!=`.</span><span class="sxs-lookup"><span data-stu-id="cdecb-168">The C# tuple types now support `==` and `!=`.</span></span> <span data-ttu-id="cdecb-169">Další informace najdete v oddílu, mezi které patří [rovnosti](../tuples.md#equality-and-tuples) v článku věnovaném [řazených kolekcí členů](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="cdecb-169">For more information, see the section covering [equality](../tuples.md#equality-and-tuples) in the article on [tuples](../tuples.md).</span></span>

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a><span data-ttu-id="cdecb-170">Připojit atributy na pomocné pole automaticky implementované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="cdecb-170">Attach attributes to the backing fields for auto-implemented properties</span></span>

<span data-ttu-id="cdecb-171">Tato syntaxe se teď podporuje:</span><span class="sxs-lookup"><span data-stu-id="cdecb-171">This syntax is now supported:</span></span>

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

<span data-ttu-id="cdecb-172">Atribut `SomeThingAboutFieldAttribute` platí pro generovaný kompilátorem pomocné pole `SomeProperty`.</span><span class="sxs-lookup"><span data-stu-id="cdecb-172">The attribute `SomeThingAboutFieldAttribute` is applied to the compiler generated backing field for `SomeProperty`.</span></span> <span data-ttu-id="cdecb-173">Další informace najdete v tématu [atributy](../programming-guide/concepts/attributes/index.md) v Průvodci programovacího jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="cdecb-173">For more information, see [attributes](../programming-guide/concepts/attributes/index.md) in the C# programming guide.</span></span>

### <a name="in-method-overload-resolution-tiebreaker"></a><span data-ttu-id="cdecb-174">`in` rozhodujícího prvku rozlišení přetížení – metoda</span><span class="sxs-lookup"><span data-stu-id="cdecb-174">`in` method overload resolution tiebreaker</span></span>

<span data-ttu-id="cdecb-175">Když `in` byl přidán modifikátor argument, tyto dvě metody by způsobit nejednoznačnost:</span><span class="sxs-lookup"><span data-stu-id="cdecb-175">When the `in` argument modifier was added, these two methods would cause an ambiguity:</span></span>

```csharp
static void M(S arg);
static void M(in S arg);
```

<span data-ttu-id="cdecb-176">Nyní podle hodnoty (první v předchozím příkladu) je lepší než přetížení odkaz verze jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="cdecb-176">Now, the by value (first in the preceding example) overload is better than the by readonly reference version.</span></span> <span data-ttu-id="cdecb-177">Pro volání verze s argumentem reference jen pro čtení, je nutné zahrnout `in` modifikátor při volání metody.</span><span class="sxs-lookup"><span data-stu-id="cdecb-177">To call the version with the readonly reference argument, you must include the `in` modifier when calling the method.</span></span>

> [!NOTE]
> <span data-ttu-id="cdecb-178">To bylo implementováno jako oprava chyby.</span><span class="sxs-lookup"><span data-stu-id="cdecb-178">This was implemented as a bug fix.</span></span> <span data-ttu-id="cdecb-179">To už je nejednoznačný i přes jazykové verze nastavena na "7.2".</span><span class="sxs-lookup"><span data-stu-id="cdecb-179">This no longer is ambiguous even with the language version set to "7.2".</span></span>

<span data-ttu-id="cdecb-180">Další informace najdete v článku na [ `in` modifikátor parametru](../language-reference/keywords/in-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="cdecb-180">For more information, see the article on the [`in` parameter modifier](../language-reference/keywords/in-parameter-modifier.md).</span></span>

### <a name="extend-expression-variables-in-initializers"></a><span data-ttu-id="cdecb-181">Rozšíření proměnných výrazu v inicializátorech</span><span class="sxs-lookup"><span data-stu-id="cdecb-181">Extend expression variables in initializers</span></span>

<span data-ttu-id="cdecb-182">Syntaxe v jazyce C# 7.0 umožňuje přidat `out` deklarace proměnných rozšířilo a obsahovat Inicializátory pole, vlastnosti, inicializátory konstruktoru a klauzulí dotazů.</span><span class="sxs-lookup"><span data-stu-id="cdecb-182">The syntax added in C# 7.0 to allow `out` variable declarations has been extended to include field initializers, property initializers, constructor initializers, and query clauses.</span></span> <span data-ttu-id="cdecb-183">To umožňuje kódu jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="cdecb-183">It enables code such as the following example:</span></span>

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

### <a name="improved-overload-candidates"></a><span data-ttu-id="cdecb-184">Vylepšení kandidátů přetížení</span><span class="sxs-lookup"><span data-stu-id="cdecb-184">Improved overload candidates</span></span>

<span data-ttu-id="cdecb-185">V každé verzi pravidla rozlišení přetížení aktualizovat na situace, kdy mají "viditelných" volba volání metod nejednoznačný.</span><span class="sxs-lookup"><span data-stu-id="cdecb-185">In every release, the overload resolution rules get updated to address situations where ambiguous method invocations have an "obvious" choice.</span></span> <span data-ttu-id="cdecb-186">Tato verze přidává tři nová pravidla ke kompilátoru vyberte jasnou volbou:</span><span class="sxs-lookup"><span data-stu-id="cdecb-186">This release adds three new rules to help the compiler pick the obvious choice:</span></span>

1. <span data-ttu-id="cdecb-187">Pokud skupina metoda obsahuje instanci a statické členy, kompilátor zahodí členy instance, pokud metoda byla vyvolána bez instance příjemce nebo kontextu.</span><span class="sxs-lookup"><span data-stu-id="cdecb-187">When a method group contains both instance and static members, the compiler discards the instance members if the method was invoked without an instance receiver or context.</span></span> <span data-ttu-id="cdecb-188">Kompilátor zahodí statické členy, pokud metoda byla vyvolána s přijímače instance.</span><span class="sxs-lookup"><span data-stu-id="cdecb-188">The compiler discards the static members if the method was invoked with an instance receiver.</span></span> <span data-ttu-id="cdecb-189">Pokud není žádný příjemce, kompilátor obsahuje pouze statické členy ve statickém kontextu, v opačném případě statických a členy instance.</span><span class="sxs-lookup"><span data-stu-id="cdecb-189">When there is no receiver, the compiler includes only static members in a static context, otherwise both static and instance members.</span></span> <span data-ttu-id="cdecb-190">Když příjemce ambiguously instance nebo typ, kompilátor obsahuje.</span><span class="sxs-lookup"><span data-stu-id="cdecb-190">When the receiver is ambiguously an instance or type, the compiler includes both.</span></span> <span data-ttu-id="cdecb-191">Statického kontextu, kde je implicitní `this` příjemce instanci nelze použít, obsahuje tělo členů, pokud `this` je definován, jako je například statické členy, jakož i kdy, kde `this` nelze použít, jako je například Inicializátory polí a Inicializátory konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="cdecb-191">A static context, where an implicit `this` instance receiver cannot be used, includes the body of members where no `this` is defined, such as static members, as well as places where `this` cannot be used, such as field initializers and constructor-initializers.</span></span>
1. <span data-ttu-id="cdecb-192">Pokud metoda skupina obsahuje některé obecné metody, jejichž argumentů typu nevyhovuje požadavkům jejich omezení, tyto členy, se odeberou ze sady Release candidate.</span><span class="sxs-lookup"><span data-stu-id="cdecb-192">When a method group contains some generic methods whose type arguments do not satisfy their constraints, these members are removed from the candidate set.</span></span>
1. <span data-ttu-id="cdecb-193">Pro skupiny převod metody vrátí metody Release candidate, jejíž návratový typ neshoduje s delegáta typu se odeberou ze sady.</span><span class="sxs-lookup"><span data-stu-id="cdecb-193">For a method group conversion, candidate methods whose return type doesn't match up with the delegate's return type are removed from the set.</span></span>

<span data-ttu-id="cdecb-194">Tato změna všimnout pouze vzhledem k tomu, že zjistíte méně chyb kompilátoru pro přetížení metody nejednoznačný když jste si jisti, jakou metodu je lepší.</span><span class="sxs-lookup"><span data-stu-id="cdecb-194">You'll only notice this change because you'll find fewer compiler errors for ambiguous method overloads when you are sure which method is better.</span></span>

## <a name="new-compiler-options"></a><span data-ttu-id="cdecb-195">Nové možnosti kompilátoru</span><span class="sxs-lookup"><span data-stu-id="cdecb-195">New compiler options</span></span>

<span data-ttu-id="cdecb-196">Nové možnosti kompilátoru podporují scénáře DevOps a nové sestavení pro programy C#.</span><span class="sxs-lookup"><span data-stu-id="cdecb-196">New compiler options support new build and DevOps scenarios for C# programs.</span></span>

### <a name="public-or-open-source-signing"></a><span data-ttu-id="cdecb-197">Veřejný nebo podepisování Open Source</span><span class="sxs-lookup"><span data-stu-id="cdecb-197">Public or Open Source signing</span></span>

<span data-ttu-id="cdecb-198">`-publicsign` – Možnost kompilátoru instruuje kompilátor, aby podepište sestavení pomocí veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="cdecb-198">The `-publicsign` compiler option instructs the compiler to sign the assembly using a public key.</span></span> <span data-ttu-id="cdecb-199">Sestava je označena jako podepsané, ale signatura je převzata z veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="cdecb-199">The assembly is marked as signed, but the signature is taken from the public key.</span></span> <span data-ttu-id="cdecb-200">Tato možnost vám umožní sestavovat podepsaná sestavení z open-source projektů pomocí veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="cdecb-200">This option enables you to build signed assemblies from open-source projects using a public key.</span></span>

<span data-ttu-id="cdecb-201">Další informace najdete v tématu [– možnost kompilátoru - publicsign](../language-reference/compiler-options/publicsign-compiler-option.md) článku.</span><span class="sxs-lookup"><span data-stu-id="cdecb-201">For more information, see the [-publicsign compiler option](../language-reference/compiler-options/publicsign-compiler-option.md) article.</span></span>

### <a name="pathmap"></a><span data-ttu-id="cdecb-202">pathmap</span><span class="sxs-lookup"><span data-stu-id="cdecb-202">pathmap</span></span>

<span data-ttu-id="cdecb-203">`-pathmap` – Možnost kompilátoru instruuje kompilátor, aby nahraďte mapované zdrojových cest zdrojových cest z prostředí pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="cdecb-203">The `-pathmap` compiler option instructs the compiler to replace source paths from the build environment with mapped source paths.</span></span> <span data-ttu-id="cdecb-204">`-pathmap` Možnost řídí napsaný v kompilátoru pro soubory PDB nebo pro zdrojovou cestu <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span><span class="sxs-lookup"><span data-stu-id="cdecb-204">The `-pathmap` option controls the source path written by the compiler to PDB files or for the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span></span>

<span data-ttu-id="cdecb-205">Další informace najdete v tématu [– možnost kompilátoru - pathmap](../language-reference/compiler-options/pathmap-compiler-option.md) článku.</span><span class="sxs-lookup"><span data-stu-id="cdecb-205">For more information, see the [-pathmap compiler option](../language-reference/compiler-options/pathmap-compiler-option.md) article.</span></span>
