---
title: fixed Statement - C# odkaz
ms.custom: seodec18
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: 2c49c8517e15534121b0f8dbc04902b46a92ef20
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959360"
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="10ee1-102">fixed – příkaz (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="10ee1-102">fixed Statement (C# Reference)</span></span>

<span data-ttu-id="10ee1-103">`fixed` Příkaz zabraňuje přemístění přesouvatelný proměnné systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="10ee1-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="10ee1-104">`fixed` Příkaz je povolen pouze v [nebezpečné](unsafe.md) kontextu.</span><span class="sxs-lookup"><span data-stu-id="10ee1-104">The `fixed` statement is only permitted in an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="10ee1-105">Můžete také použít `fixed` – klíčové slovo k vytvoření [pevných vyrovnávacích pamětí velikost](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="10ee1-105">You can also use the `fixed` keyword to create [fixed size buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

<span data-ttu-id="10ee1-106">`fixed` Příkaz nastaví ukazatel na proměnnou spravované a "kódy PIN" Tato proměnná během provádění příkazu.</span><span class="sxs-lookup"><span data-stu-id="10ee1-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="10ee1-107">Odkazy na přesouvatelný spravované proměnné jsou užitečné pouze `fixed` kontextu.</span><span class="sxs-lookup"><span data-stu-id="10ee1-107">Pointers to movable managed variables are useful only in a `fixed` context.</span></span> <span data-ttu-id="10ee1-108">Bez `fixed` kontextu, uvolňování paměti může přemístit proměnné nepředvídatelné.</span><span class="sxs-lookup"><span data-stu-id="10ee1-108">Without a `fixed` context, garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="10ee1-109">Kompilátor jazyka C# pouze umožňuje přiřadit ukazatel na proměnnou spravované v `fixed` příkazu.</span><span class="sxs-lookup"><span data-stu-id="10ee1-109">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

<span data-ttu-id="10ee1-110">Ukazatele lze inicializovat pomocí pole, řetězec, vyrovnávací paměti pevné velikosti nebo adresy proměnné.</span><span class="sxs-lookup"><span data-stu-id="10ee1-110">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="10ee1-111">Následující příklad ukazuje použití řetězce, pole a adresy proměnné:</span><span class="sxs-lookup"><span data-stu-id="10ee1-111">The following example illustrates the use of variable addresses, arrays, and strings:</span></span>

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

<span data-ttu-id="10ee1-112">Od verze C# 7.3, `fixed` příkaz funguje u dalších typů mimo pole, řetězce, vyrovnávací paměti pevné velikosti nebo nespravované proměnné.</span><span class="sxs-lookup"><span data-stu-id="10ee1-112">Starting with C# 7.3, the `fixed` statement operates on additional types beyond arrays, strings, fixed-size buffers, or unmanaged variables.</span></span> <span data-ttu-id="10ee1-113">Libovolný typ, který implementuje metodu s názvem `GetPinnableReference` je možné připnout.</span><span class="sxs-lookup"><span data-stu-id="10ee1-113">Any type that implements a method named `GetPinnableReference` can be pinned.</span></span> <span data-ttu-id="10ee1-114">`GetPinnableReference` Musí vrátit `ref` proměnné k nespravovaným typem.</span><span class="sxs-lookup"><span data-stu-id="10ee1-114">The `GetPinnableReference` must return a `ref` variable to an unmanaged type.</span></span> <span data-ttu-id="10ee1-115">Naleznete v tématu o [typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="10ee1-115">See the topic on [pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md) for more information.</span></span> <span data-ttu-id="10ee1-116">Typy .NET <xref:System.Span%601?displayProperty=nameWithType> a <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> zavedena v rozhraní .NET Core 2.0 Zkontrolujte použití tohoto modelu a je možné připnout.</span><span class="sxs-lookup"><span data-stu-id="10ee1-116">The .NET types <xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> introduced in .NET Core 2.0 make use of this pattern and can be pinned.</span></span> <span data-ttu-id="10ee1-117">To je ukázáno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="10ee1-117">This is shown in the following example:</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

<span data-ttu-id="10ee1-118">Pokud vytváříte v tomto modelu typy, které by se měly podílet, přečtěte si téma <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> příklad implementace vzoru.</span><span class="sxs-lookup"><span data-stu-id="10ee1-118">If you are creating types that should participate in this pattern, see <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> for an example of implementing the pattern.</span></span>

<span data-ttu-id="10ee1-119">Většího počtu ukazatelů lze inicializovat v jednom příkazu, pokud jsou všechny stejného typu:</span><span class="sxs-lookup"><span data-stu-id="10ee1-119">Multiple pointers can be initialized in one statement if they are all the same type:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

<span data-ttu-id="10ee1-120">K inicializaci ukazatele na různé typy, jednoduše vnořit `fixed` příkazy, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="10ee1-120">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

<span data-ttu-id="10ee1-121">Po provedení kódu v příkazu jsou všechny připnuté proměnné nepřipnuté a uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="10ee1-121">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="10ee1-122">Proto neukazují na těchto proměnných mimo `fixed` příkazu.</span><span class="sxs-lookup"><span data-stu-id="10ee1-122">Therefore, do not point to those variables outside the `fixed` statement.</span></span> <span data-ttu-id="10ee1-123">Proměnné deklarované v `fixed` příkaz mají rozsah, který tento příkaz, aby toto:</span><span class="sxs-lookup"><span data-stu-id="10ee1-123">The variables declared in the `fixed` statement are scoped to that statement, making this easier:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

<span data-ttu-id="10ee1-124">Ukazatele inicializované v `fixed` příkazy jsou proměnné určené jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="10ee1-124">Pointers initialized in `fixed` statements are readonly variables.</span></span> <span data-ttu-id="10ee1-125">Pokud chcete změnit hodnotu ukazatele, musí deklarovat proměnnou druhý ukazatel a upravit.</span><span class="sxs-lookup"><span data-stu-id="10ee1-125">If you want to modify the pointer value, you must declare a second pointer variable, and modify that.</span></span> <span data-ttu-id="10ee1-126">Proměnná deklarovaná ve `fixed` nelze upravit – příkaz:</span><span class="sxs-lookup"><span data-stu-id="10ee1-126">The variable declared in the `fixed` statement cannot be modified:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

<span data-ttu-id="10ee1-127">Můžete přidělit paměť v zásobníku, kde není časovač uvolněn z paměti a proto není potřeba připnout.</span><span class="sxs-lookup"><span data-stu-id="10ee1-127">You can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="10ee1-128">Provedete to, které používají [ `stackalloc` operátor](stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="10ee1-128">To do that use the [`stackalloc` operator](stackalloc.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="10ee1-129">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="10ee1-129">C# language specification</span></span>

<span data-ttu-id="10ee1-130">Další informace najdete v tématu [příkazu fixed](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="10ee1-130">For more information, see [The fixed statement](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="10ee1-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10ee1-131">See also</span></span>

- [<span data-ttu-id="10ee1-132">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="10ee1-132">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="10ee1-133">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="10ee1-133">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="10ee1-134">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="10ee1-134">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="10ee1-135">unsafe</span><span class="sxs-lookup"><span data-stu-id="10ee1-135">unsafe</span></span>](unsafe.md)
- [<span data-ttu-id="10ee1-136">Vyrovnávací paměti pevné velikosti</span><span class="sxs-lookup"><span data-stu-id="10ee1-136">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
