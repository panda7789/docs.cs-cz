---
title: fixed – příkaz (Referenční dokumentace jazyka C#)
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: e26e7e7f15dd48cf029d5f67bf5ef0de3e19b7bb
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2018
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="6bc15-102">fixed – příkaz (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6bc15-102">fixed Statement (C# Reference)</span></span>

<span data-ttu-id="6bc15-103">`fixed` Příkaz zabrání přemístění mobilní proměnné uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6bc15-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="6bc15-104">`fixed` Příkazu je povolená jenom v [unsafe](unsafe.md) kontextu.</span><span class="sxs-lookup"><span data-stu-id="6bc15-104">The `fixed` statement is only permitted in an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="6bc15-105">`fixed` Můžete také použít k vytvoření [pevnou velikost vyrovnávací paměti](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="6bc15-105">`fixed` can also be used to create [fixed size buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

<span data-ttu-id="6bc15-106">`fixed` Příkaz nastaví ukazatel spravované proměnné a "PIN" tuto proměnnou během provádění příkazu.</span><span class="sxs-lookup"><span data-stu-id="6bc15-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="6bc15-107">Ukazatelé na mobilní spravované proměnné jsou užitečné pouze v `fixed` kontextu.</span><span class="sxs-lookup"><span data-stu-id="6bc15-107">Pointers to movable managed variables are useful only in a `fixed` context.</span></span> <span data-ttu-id="6bc15-108">Bez `fixed` kontextu, uvolňování paměti by mohly přemístit proměnné nepředvídatelné.</span><span class="sxs-lookup"><span data-stu-id="6bc15-108">Without a `fixed` context, garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="6bc15-109">Kompilátor jazyka C# pouze umožňuje přiřadit ukazatel spravované proměnné v `fixed` příkaz.</span><span class="sxs-lookup"><span data-stu-id="6bc15-109">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

<span data-ttu-id="6bc15-110">Ukazatel lze inicializovat pomocí pole, řetězec, vyrovnávací paměti pevné velikosti nebo adresy proměnné.</span><span class="sxs-lookup"><span data-stu-id="6bc15-110">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="6bc15-111">Následující příklad ukazuje použití proměnných adresy, pole a řetězce.</span><span class="sxs-lookup"><span data-stu-id="6bc15-111">The following example illustrates the use of variable addresses, arrays, and strings.</span></span> <span data-ttu-id="6bc15-112">Další informace o pevné velikosti vyrovnávací paměti najdete v tématu [pevnou velikost vyrovnávací paměti](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="6bc15-112">For more information about fixed-size buffers, see [Fixed Size Buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

<span data-ttu-id="6bc15-113">Od verze jazyka C# 7.3, `fixed` příkaz funguje na další typy nad rámec pole řetězce, vyrovnávací paměti pevné velikosti nebo nespravované proměnné.</span><span class="sxs-lookup"><span data-stu-id="6bc15-113">Starting with C# 7.3, the `fixed` statement operates on additional types beyond arrays, strings, fixed-size buffers, or unmanaged variables.</span></span> <span data-ttu-id="6bc15-114">Žádný typ, který implementuje metodu s názvem `DangerousGetPinnableReference` lze připojit.</span><span class="sxs-lookup"><span data-stu-id="6bc15-114">Any type that implements a method named `DangerousGetPinnableReference` can be pinned.</span></span> <span data-ttu-id="6bc15-115">`DangerousGetPinnableReference` Musí vrátit `ref` nespravovaný typ proměnné.</span><span class="sxs-lookup"><span data-stu-id="6bc15-115">The `DangerousGetPinnableReference` must return a `ref` variable to an unmanaged type.</span></span> <span data-ttu-id="6bc15-116">Podívejte se na téma na [typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="6bc15-116">See the topic on [pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md) for more information.</span></span> <span data-ttu-id="6bc15-117">Typy .NET <xref:System.Span%601?displayProperty=nameWithType> a <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> byla zavedená v rozhraní .NET 2.0 základní zkontrolujte pomocí tohoto vzoru a může být připnutý.</span><span class="sxs-lookup"><span data-stu-id="6bc15-117">The .NET types <xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> introduced in .NET Core 2.0 make use of this pattern and can be pinned.</span></span> <span data-ttu-id="6bc15-118">To je ukázáno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="6bc15-118">This is shown in the following example:</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

<span data-ttu-id="6bc15-119">Pokud vytváříte typy, které by se měly podílet v tomto vzoru, přečtěte si téma <xref:System.Span%601.DangerousGetPinnableReference?displayProperty=nameWithType> příklad implementace vzoru.</span><span class="sxs-lookup"><span data-stu-id="6bc15-119">If you are creating types that should participate in this pattern, see <xref:System.Span%601.DangerousGetPinnableReference?displayProperty=nameWithType> for an example of implementing the pattern.</span></span>

<span data-ttu-id="6bc15-120">Více ukazatele jde inicializovat na jeden příkaz Pokud jsou všechny stejného typu:</span><span class="sxs-lookup"><span data-stu-id="6bc15-120">Multiple pointers can be initialized in one statement if they are all the same type:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

<span data-ttu-id="6bc15-121">K chybě při inicializaci ukazatele různých typů, jednoduše vnořit `fixed` příkazy, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6bc15-121">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

<span data-ttu-id="6bc15-122">Po spuštění kódu v příkazu, jsou všechny definovaného proměnné Odepnout a předmět pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6bc15-122">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="6bc15-123">Proto neukazují na tyto proměnné mimo `fixed` příkaz.</span><span class="sxs-lookup"><span data-stu-id="6bc15-123">Therefore, do not point to those variables outside the `fixed` statement.</span></span> <span data-ttu-id="6bc15-124">Proměnných deklarovaných v `fixed` příkaz jsou omezená na tento příkaz snadněji toto:</span><span class="sxs-lookup"><span data-stu-id="6bc15-124">The variables declared in the `fixed` statement are scoped to that statement, making this easier:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

<span data-ttu-id="6bc15-125">Ukazatele v inicializovat `fixed` příkazy jsou proměnné určené jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="6bc15-125">Pointers initialized in `fixed` statements are readonly variables.</span></span> <span data-ttu-id="6bc15-126">Pokud chcete upravit hodnota ukazatele s hodnotou, musí deklarovat druhý proměnné ukazatele a upravit.</span><span class="sxs-lookup"><span data-stu-id="6bc15-126">If you want to modify the pointer value, you must declare a second pointer variable, and modify that.</span></span> <span data-ttu-id="6bc15-127">Proměnná definovaná v `fixed` nemůže být upravena příkaz:</span><span class="sxs-lookup"><span data-stu-id="6bc15-127">The variable declared in the `fixed` statement cannot be modified:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```


<span data-ttu-id="6bc15-128">V režimu unsafe mohou přidělit paměť v zásobníku, kde se nevztahuje uvolňování paměti a proto nemusí být připojena.</span><span class="sxs-lookup"><span data-stu-id="6bc15-128">In unsafe mode, you can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="6bc15-129">Další informace najdete v tématu [stackalloc](stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="6bc15-129">For more information, see [stackalloc](stackalloc.md).</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="6bc15-130">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6bc15-130">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="6bc15-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="6bc15-131">See Also</span></span>

 [<span data-ttu-id="6bc15-132">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6bc15-132">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="6bc15-133">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6bc15-133">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="6bc15-134">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6bc15-134">C# Keywords</span></span>](index.md)  
 [<span data-ttu-id="6bc15-135">unsafe</span><span class="sxs-lookup"><span data-stu-id="6bc15-135">unsafe</span></span>](unsafe.md)  
 [<span data-ttu-id="6bc15-136">Vyrovnávací paměti pevné velikosti</span><span class="sxs-lookup"><span data-stu-id="6bc15-136">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
