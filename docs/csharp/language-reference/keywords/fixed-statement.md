---
title: opraven příkaz - C# Reference
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: 53bee82bf24a847b0b21ed2375d09a6303d4fe48
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507188"
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="855d2-102">fixed – příkaz (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="855d2-102">fixed Statement (C# Reference)</span></span>

<span data-ttu-id="855d2-103">Příkaz `fixed` zabrání systému uvolňování paměti přemístit pohyblivou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="855d2-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="855d2-104">Příkaz `fixed` je povolen pouze v [nebezpečném](unsafe.md) kontextu.</span><span class="sxs-lookup"><span data-stu-id="855d2-104">The `fixed` statement is only permitted in an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="855d2-105">Klíčové `fixed` slovo můžete také použít k vytvoření [vyrovnávacích pamětí s pevnou velikostí](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="855d2-105">You can also use the `fixed` keyword to create [fixed size buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

<span data-ttu-id="855d2-106">Příkaz `fixed` nastaví ukazatel na spravovanou proměnnou a "kolíky" tuto proměnnou během provádění příkazu.</span><span class="sxs-lookup"><span data-stu-id="855d2-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="855d2-107">Ukazatele na pohyblivé spravované proměnné `fixed` jsou užitečné pouze v kontextu.</span><span class="sxs-lookup"><span data-stu-id="855d2-107">Pointers to movable managed variables are useful only in a `fixed` context.</span></span> <span data-ttu-id="855d2-108">Bez `fixed` kontextu uvolňování paměti může přemístit proměnné nepředvídatelně.</span><span class="sxs-lookup"><span data-stu-id="855d2-108">Without a `fixed` context, garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="855d2-109">Kompilátor Jazyka C# umožňuje pouze přiřadit ukazatel spravované `fixed` proměnné v příkazu.</span><span class="sxs-lookup"><span data-stu-id="855d2-109">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

<span data-ttu-id="855d2-110">Ukazatel můžete inicializovat pomocí pole, řetězce, vyrovnávací paměti s pevnou velikostí nebo adresy proměnné.</span><span class="sxs-lookup"><span data-stu-id="855d2-110">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="855d2-111">Následující příklad ilustruje použití proměnných adres, polí a řetězců:</span><span class="sxs-lookup"><span data-stu-id="855d2-111">The following example illustrates the use of variable addresses, arrays, and strings:</span></span>

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

<span data-ttu-id="855d2-112">Počínaje C# 7.3, `fixed` příkaz pracuje na další typy mimo pole, řetězce, vyrovnávací paměti s pevnou velikostí nebo nespravované proměnné.</span><span class="sxs-lookup"><span data-stu-id="855d2-112">Starting with C# 7.3, the `fixed` statement operates on additional types beyond arrays, strings, fixed size buffers, or unmanaged variables.</span></span> <span data-ttu-id="855d2-113">Libovolný typ, který implementuje metodu s názvem `GetPinnableReference` lze připnout.</span><span class="sxs-lookup"><span data-stu-id="855d2-113">Any type that implements a method named `GetPinnableReference` can be pinned.</span></span> <span data-ttu-id="855d2-114">Musí `GetPinnableReference` vrátit `ref` proměnnou [nespravovaného typu](../builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="855d2-114">The `GetPinnableReference` must return a `ref` variable of an [unmanaged type](../builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="855d2-115">Typy <xref:System.Span%601?displayProperty=nameWithType> .NET <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> a zavedené v rozhraní .NET Core 2.0 využívají tento vzor a lze je připnout.</span><span class="sxs-lookup"><span data-stu-id="855d2-115">The .NET types <xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> introduced in .NET Core 2.0 make use of this pattern and can be pinned.</span></span> <span data-ttu-id="855d2-116">To je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="855d2-116">This is shown in the following example:</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

<span data-ttu-id="855d2-117">Pokud vytváříte typy, které by se <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> měly účastnit tohoto vzoru, naleznete příklad implementace vzoru.</span><span class="sxs-lookup"><span data-stu-id="855d2-117">If you are creating types that should participate in this pattern, see <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> for an example of implementing the pattern.</span></span>

<span data-ttu-id="855d2-118">Více ukazatelů lze inicializovat v jednom příkazu, pokud jsou všechny stejného typu:</span><span class="sxs-lookup"><span data-stu-id="855d2-118">Multiple pointers can be initialized in one statement if they are all the same type:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

<span data-ttu-id="855d2-119">Chcete-li inicializovat ukazatele různých `fixed` typů, jednoduše vnořte příkazy, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="855d2-119">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

<span data-ttu-id="855d2-120">Po spuštění kódu v příkazu jsou všechny připnuté proměnné odepnuty a podléhají uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="855d2-120">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="855d2-121">Proto neodkazují na tyto proměnné `fixed` mimo příkaz.</span><span class="sxs-lookup"><span data-stu-id="855d2-121">Therefore, do not point to those variables outside the `fixed` statement.</span></span> <span data-ttu-id="855d2-122">Proměnné deklarované `fixed` v příkazu jsou vymezeny na toto prohlášení, což usnadňuje:</span><span class="sxs-lookup"><span data-stu-id="855d2-122">The variables declared in the `fixed` statement are scoped to that statement, making this easier:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

<span data-ttu-id="855d2-123">Ukazatele inicializované v `fixed` příkazech jsou proměnné jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="855d2-123">Pointers initialized in `fixed` statements are readonly variables.</span></span> <span data-ttu-id="855d2-124">Pokud chcete změnit hodnotu ukazatele, musíte deklarovat druhou proměnnou ukazatele a upravit ji.</span><span class="sxs-lookup"><span data-stu-id="855d2-124">If you want to modify the pointer value, you must declare a second pointer variable, and modify that.</span></span> <span data-ttu-id="855d2-125">Proměnnou uvedenou `fixed` v výkazu nelze změnit:</span><span class="sxs-lookup"><span data-stu-id="855d2-125">The variable declared in the `fixed` statement cannot be modified:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

<span data-ttu-id="855d2-126">Můžete přidělit paměť v zásobníku, kde není předmětem uvolňování paměti a proto není nutné připnout.</span><span class="sxs-lookup"><span data-stu-id="855d2-126">You can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="855d2-127">Chcete-li to provést, použijte [ `stackalloc` výraz](../operators/stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="855d2-127">To do that, use a [`stackalloc` expression](../operators/stackalloc.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="855d2-128">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="855d2-128">C# language specification</span></span>

<span data-ttu-id="855d2-129">Další informace naleznete [v části Pevný příkaz](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) specifikace jazyka [C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="855d2-129">For more information, see [The fixed statement](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="855d2-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="855d2-130">See also</span></span>

- [<span data-ttu-id="855d2-131">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="855d2-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="855d2-132">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="855d2-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="855d2-133">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="855d2-133">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="855d2-134">unsafe</span><span class="sxs-lookup"><span data-stu-id="855d2-134">unsafe</span></span>](unsafe.md)
- [<span data-ttu-id="855d2-135">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="855d2-135">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="855d2-136">Vyrovnávací paměti s pevnou velikostí</span><span class="sxs-lookup"><span data-stu-id="855d2-136">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
