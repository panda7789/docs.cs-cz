---
title: Příkaz fixed – C# reference
ms.custom: seodec18
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: d3c87f0e71095bbcc7c5a1d64b026e92838a6306
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433757"
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="e152f-102">fixed – příkaz (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e152f-102">fixed Statement (C# Reference)</span></span>

<span data-ttu-id="e152f-103">`fixed` Příkaz brání systému uvolňování paměti v přemístění pohyblivé proměnné.</span><span class="sxs-lookup"><span data-stu-id="e152f-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="e152f-104">Příkaz je povolen pouze v nezabezpečeném kontextu. [nebezpečný](unsafe.md) `fixed`</span><span class="sxs-lookup"><span data-stu-id="e152f-104">The `fixed` statement is only permitted in an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="e152f-105">Pomocí `fixed` klíčového slova můžete také vytvořit [vyrovnávací paměti pevné velikosti](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="e152f-105">You can also use the `fixed` keyword to create [fixed size buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

<span data-ttu-id="e152f-106">`fixed` Příkaz nastaví ukazatel na spravovanou proměnnou a "PIN" tuto proměnnou během provádění příkazu.</span><span class="sxs-lookup"><span data-stu-id="e152f-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="e152f-107">Ukazatele na pohyblivé spravované proměnné jsou užitečné pouze v `fixed` kontextu.</span><span class="sxs-lookup"><span data-stu-id="e152f-107">Pointers to movable managed variables are useful only in a `fixed` context.</span></span> <span data-ttu-id="e152f-108">`fixed` Bez kontextu by uvolňování paměti mohlo přemístit proměnné nepředvídatelné.</span><span class="sxs-lookup"><span data-stu-id="e152f-108">Without a `fixed` context, garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="e152f-109">C# Kompilátor umožňuje přiřadit ukazatel na spravovanou proměnnou v `fixed` příkazu.</span><span class="sxs-lookup"><span data-stu-id="e152f-109">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

<span data-ttu-id="e152f-110">Můžete inicializovat ukazatel pomocí pole, řetězce, vyrovnávací paměti pevné velikosti nebo adresy proměnné.</span><span class="sxs-lookup"><span data-stu-id="e152f-110">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="e152f-111">Následující příklad ilustruje použití proměnných adres, polí a řetězců:</span><span class="sxs-lookup"><span data-stu-id="e152f-111">The following example illustrates the use of variable addresses, arrays, and strings:</span></span>

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

<span data-ttu-id="e152f-112">Počínaje C# 7,3, `fixed` příkaz funguje na dalších typech nad rámec polí, řetězců, vyrovnávací paměti pevné velikosti nebo nespravovaných proměnných.</span><span class="sxs-lookup"><span data-stu-id="e152f-112">Starting with C# 7.3, the `fixed` statement operates on additional types beyond arrays, strings, fixed size buffers, or unmanaged variables.</span></span> <span data-ttu-id="e152f-113">Libovolný typ, který implementuje metodu s `GetPinnableReference` názvem, lze připnout.</span><span class="sxs-lookup"><span data-stu-id="e152f-113">Any type that implements a method named `GetPinnableReference` can be pinned.</span></span> <span data-ttu-id="e152f-114">Musí vracet proměnnou nespravovaného [typu.](../builtin-types/unmanaged-types.md) `GetPinnableReference` `ref`</span><span class="sxs-lookup"><span data-stu-id="e152f-114">The `GetPinnableReference` must return a `ref` variable of an [unmanaged type](../builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="e152f-115">Typy <xref:System.Span%601?displayProperty=nameWithType> .NET a <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> zavedené v .NET Core 2,0 využívají tento model a dají se připnout.</span><span class="sxs-lookup"><span data-stu-id="e152f-115">The .NET types <xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> introduced in .NET Core 2.0 make use of this pattern and can be pinned.</span></span> <span data-ttu-id="e152f-116">To je ukázáno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="e152f-116">This is shown in the following example:</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

<span data-ttu-id="e152f-117">Pokud vytváříte typy, které by se měly účastnit tohoto modelu, <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> Přečtěte si příklad implementace vzoru.</span><span class="sxs-lookup"><span data-stu-id="e152f-117">If you are creating types that should participate in this pattern, see <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> for an example of implementing the pattern.</span></span>

<span data-ttu-id="e152f-118">V jednom příkazu lze inicializovat více ukazatelů, pokud jsou všechny stejného typu:</span><span class="sxs-lookup"><span data-stu-id="e152f-118">Multiple pointers can be initialized in one statement if they are all the same type:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

<span data-ttu-id="e152f-119">Chcete-li inicializovat ukazatele různých typů, jednoduše vnořovat `fixed` příkazy, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e152f-119">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

<span data-ttu-id="e152f-120">Po spuštění kódu v příkazu nejsou připnuté žádné připnuté proměnné a podléhají uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="e152f-120">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="e152f-121">Proto neodkazujte na tyto proměnné mimo `fixed` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e152f-121">Therefore, do not point to those variables outside the `fixed` statement.</span></span> <span data-ttu-id="e152f-122">Proměnné deklarované v `fixed` příkazu jsou vymezeny na tento příkaz, což usnadňuje tyto akce:</span><span class="sxs-lookup"><span data-stu-id="e152f-122">The variables declared in the `fixed` statement are scoped to that statement, making this easier:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

<span data-ttu-id="e152f-123">Ukazatelé inicializovaný v `fixed` příkazech jsou proměnné jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="e152f-123">Pointers initialized in `fixed` statements are readonly variables.</span></span> <span data-ttu-id="e152f-124">Chcete-li změnit hodnotu ukazatele, je nutné deklarovat druhý ukazatel na proměnnou a upravit ji.</span><span class="sxs-lookup"><span data-stu-id="e152f-124">If you want to modify the pointer value, you must declare a second pointer variable, and modify that.</span></span> <span data-ttu-id="e152f-125">Proměnná deklarovaná v `fixed` příkazu se nedá změnit:</span><span class="sxs-lookup"><span data-stu-id="e152f-125">The variable declared in the `fixed` statement cannot be modified:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

<span data-ttu-id="e152f-126">Můžete přidělit paměť v zásobníku, kde nepodléhá uvolňování paměti, a proto není nutné ji připnout.</span><span class="sxs-lookup"><span data-stu-id="e152f-126">You can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="e152f-127">K tomu použijte [ `stackalloc` operátor](../operators/stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="e152f-127">To do that use the [`stackalloc` operator](../operators/stackalloc.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e152f-128">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e152f-128">C# language specification</span></span>

<span data-ttu-id="e152f-129">Další informace naleznete v části s [příkazem fixed](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="e152f-129">For more information, see [The fixed statement](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e152f-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e152f-130">See also</span></span>

- [<span data-ttu-id="e152f-131">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="e152f-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e152f-132">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e152f-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e152f-133">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e152f-133">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="e152f-134">unsafe</span><span class="sxs-lookup"><span data-stu-id="e152f-134">unsafe</span></span>](unsafe.md)
- [<span data-ttu-id="e152f-135">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="e152f-135">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="e152f-136">Vyrovnávací paměti pevné velikosti</span><span class="sxs-lookup"><span data-stu-id="e152f-136">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
