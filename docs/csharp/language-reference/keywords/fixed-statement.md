---
title: fixed – příkaz – reference jazyka C#
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: d743daca2fa779e300c7e8ab430b1ffff10b434c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401911"
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="31feb-102">fixed – příkaz (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="31feb-102">fixed Statement (C# Reference)</span></span>

<span data-ttu-id="31feb-103">`fixed`Příkaz brání systému uvolňování paměti v přemístění pohyblivé proměnné.</span><span class="sxs-lookup"><span data-stu-id="31feb-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="31feb-104">`fixed`Příkaz je povolen pouze v [nezabezpečeném](unsafe.md) kontextu.</span><span class="sxs-lookup"><span data-stu-id="31feb-104">The `fixed` statement is only permitted in an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="31feb-105">Pomocí `fixed` klíčového slova můžete také vytvořit [vyrovnávací paměti pevné velikosti](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="31feb-105">You can also use the `fixed` keyword to create [fixed size buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

<span data-ttu-id="31feb-106">`fixed`Příkaz nastaví ukazatel na spravovanou proměnnou a "PIN" tuto proměnnou během provádění příkazu.</span><span class="sxs-lookup"><span data-stu-id="31feb-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="31feb-107">Ukazatele na pohyblivé spravované proměnné jsou užitečné pouze v `fixed` kontextu.</span><span class="sxs-lookup"><span data-stu-id="31feb-107">Pointers to movable managed variables are useful only in a `fixed` context.</span></span> <span data-ttu-id="31feb-108">Bez `fixed` kontextu by uvolňování paměti mohlo přemístit proměnné nepředvídatelné.</span><span class="sxs-lookup"><span data-stu-id="31feb-108">Without a `fixed` context, garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="31feb-109">Kompilátor jazyka C# umožňuje pouze přiřadit ukazatel na spravovanou proměnnou v `fixed` příkazu.</span><span class="sxs-lookup"><span data-stu-id="31feb-109">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>

[!code-csharp[Accessing fixed memory](snippets/FixedKeywordExamples.cs#1)]

<span data-ttu-id="31feb-110">Můžete inicializovat ukazatel pomocí pole, řetězce, vyrovnávací paměti pevné velikosti nebo adresy proměnné.</span><span class="sxs-lookup"><span data-stu-id="31feb-110">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="31feb-111">Následující příklad ilustruje použití proměnných adres, polí a řetězců:</span><span class="sxs-lookup"><span data-stu-id="31feb-111">The following example illustrates the use of variable addresses, arrays, and strings:</span></span>

[!code-csharp[Initializing fixed size buffers](snippets/FixedKeywordExamples.cs#2)]

<span data-ttu-id="31feb-112">Počínaje jazykem C# 7,3 `fixed` příkaz funguje na dalších typech nad rámec polí, řetězců, vyrovnávací paměti pevné velikosti nebo nespravovaných proměnných.</span><span class="sxs-lookup"><span data-stu-id="31feb-112">Starting with C# 7.3, the `fixed` statement operates on additional types beyond arrays, strings, fixed size buffers, or unmanaged variables.</span></span> <span data-ttu-id="31feb-113">Libovolný typ, který implementuje metodu s názvem, `GetPinnableReference` lze připnout.</span><span class="sxs-lookup"><span data-stu-id="31feb-113">Any type that implements a method named `GetPinnableReference` can be pinned.</span></span> <span data-ttu-id="31feb-114">`GetPinnableReference`Musí vracet `ref` proměnnou [nespravovaného typu](../builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="31feb-114">The `GetPinnableReference` must return a `ref` variable of an [unmanaged type](../builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="31feb-115">Typy .NET <xref:System.Span%601?displayProperty=nameWithType> a <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> zavedené v .net Core 2,0 využívají tento model a dají se připnout.</span><span class="sxs-lookup"><span data-stu-id="31feb-115">The .NET types <xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> introduced in .NET Core 2.0 make use of this pattern and can be pinned.</span></span> <span data-ttu-id="31feb-116">To je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="31feb-116">This is shown in the following example:</span></span>

[!code-csharp[Accessing fixed memory](snippets/FixedKeywordExamples.cs#FixedSpan)]

<span data-ttu-id="31feb-117">Pokud vytváříte typy, které by se měly účastnit tohoto modelu, přečtěte si <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> Příklad implementace vzoru.</span><span class="sxs-lookup"><span data-stu-id="31feb-117">If you are creating types that should participate in this pattern, see <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> for an example of implementing the pattern.</span></span>

<span data-ttu-id="31feb-118">V jednom příkazu lze inicializovat více ukazatelů, pokud jsou všechny stejného typu:</span><span class="sxs-lookup"><span data-stu-id="31feb-118">Multiple pointers can be initialized in one statement if they are all the same type:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

<span data-ttu-id="31feb-119">Chcete-li inicializovat ukazatele různých typů, jednoduše vnořovat `fixed` příkazy, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="31feb-119">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>

[!code-csharp[Initializing multiple pointers](snippets/FixedKeywordExamples.cs#3)]

<span data-ttu-id="31feb-120">Po spuštění kódu v příkazu nejsou připnuté žádné připnuté proměnné a podléhají uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="31feb-120">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="31feb-121">Proto neodkazujte na tyto proměnné mimo `fixed` příkaz.</span><span class="sxs-lookup"><span data-stu-id="31feb-121">Therefore, do not point to those variables outside the `fixed` statement.</span></span> <span data-ttu-id="31feb-122">Proměnné deklarované v `fixed` příkazu jsou vymezeny na tento příkaz, což usnadňuje tyto akce:</span><span class="sxs-lookup"><span data-stu-id="31feb-122">The variables declared in the `fixed` statement are scoped to that statement, making this easier:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

<span data-ttu-id="31feb-123">Ukazatelé inicializovaný v `fixed` příkazech jsou proměnné jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="31feb-123">Pointers initialized in `fixed` statements are readonly variables.</span></span> <span data-ttu-id="31feb-124">Chcete-li změnit hodnotu ukazatele, je nutné deklarovat druhý ukazatel na proměnnou a upravit ji.</span><span class="sxs-lookup"><span data-stu-id="31feb-124">If you want to modify the pointer value, you must declare a second pointer variable, and modify that.</span></span> <span data-ttu-id="31feb-125">Proměnná deklarovaná v `fixed` příkazu se nedá změnit:</span><span class="sxs-lookup"><span data-stu-id="31feb-125">The variable declared in the `fixed` statement cannot be modified:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

<span data-ttu-id="31feb-126">Můžete přidělit paměť v zásobníku, kde nepodléhá uvolňování paměti, a proto není nutné ji připnout.</span><span class="sxs-lookup"><span data-stu-id="31feb-126">You can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="31feb-127">K tomu použijte [ `stackalloc` výraz](../operators/stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="31feb-127">To do that, use a [`stackalloc` expression](../operators/stackalloc.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="31feb-128">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="31feb-128">C# language specification</span></span>

<span data-ttu-id="31feb-129">Další informace naleznete v části [fixed Statement](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="31feb-129">For more information, see [The fixed statement](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="31feb-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="31feb-130">See also</span></span>

- [<span data-ttu-id="31feb-131">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="31feb-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="31feb-132">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="31feb-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="31feb-133">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="31feb-133">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="31feb-134">UNSAFE</span><span class="sxs-lookup"><span data-stu-id="31feb-134">unsafe</span></span>](unsafe.md)
- [<span data-ttu-id="31feb-135">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="31feb-135">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="31feb-136">Vyrovnávací paměti pevné velikosti</span><span class="sxs-lookup"><span data-stu-id="31feb-136">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
