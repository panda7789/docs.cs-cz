---
title: fixed – příkaz (Referenční dokumentace jazyka C#)
ms.date: 04/20/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5dd117461f792ec7a10b740fbad277de52d05623
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="8caa8-102">fixed – příkaz (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8caa8-102">fixed Statement (C# Reference)</span></span>

<span data-ttu-id="8caa8-103">`fixed` Příkaz zabrání přemístění mobilní proměnné uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="8caa8-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="8caa8-104">`fixed` Příkazu je povolená jenom v [unsafe](unsafe.md) kontextu.</span><span class="sxs-lookup"><span data-stu-id="8caa8-104">The `fixed` statement is only permitted in an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="8caa8-105">`Fixed` Můžete také použít k vytvoření [pevnou velikost vyrovnávací paměti](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="8caa8-105">`Fixed` can also be used to create [fixed size buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

<span data-ttu-id="8caa8-106">`fixed` Příkaz nastaví ukazatel spravované proměnné a "PIN" tuto proměnnou během provádění příkazu.</span><span class="sxs-lookup"><span data-stu-id="8caa8-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="8caa8-107">Ukazatelé na mobilní spravované proměnné jsou užitečné pouze v `fixed` kontextu.</span><span class="sxs-lookup"><span data-stu-id="8caa8-107">Pointers to movable managed variables are useful only in a `fixed` context.</span></span> <span data-ttu-id="8caa8-108">Bez `fixed` kontextu, uvolňování paměti by mohly přemístit proměnné nepředvídatelné.</span><span class="sxs-lookup"><span data-stu-id="8caa8-108">Without a `fixed` context, garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="8caa8-109">Kompilátor jazyka C# pouze umožňuje přiřadit ukazatel spravované proměnné v `fixed` příkaz.</span><span class="sxs-lookup"><span data-stu-id="8caa8-109">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

<span data-ttu-id="8caa8-110">Ukazatel lze inicializovat pomocí pole, řetězec, vyrovnávací paměti pevné velikosti nebo adresy proměnné.</span><span class="sxs-lookup"><span data-stu-id="8caa8-110">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="8caa8-111">Následující příklad ukazuje použití proměnných adresy, pole a řetězce.</span><span class="sxs-lookup"><span data-stu-id="8caa8-111">The following example illustrates the use of variable addresses, arrays, and strings.</span></span> <span data-ttu-id="8caa8-112">Další informace o pevné velikosti vyrovnávací paměti najdete v tématu [pevnou velikost vyrovnávací paměti](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="8caa8-112">For more information about fixed-size buffers, see [Fixed Size Buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

<span data-ttu-id="8caa8-113">Více ukazatele jde inicializovat na jeden příkaz Pokud jsou všechny stejného typu:</span><span class="sxs-lookup"><span data-stu-id="8caa8-113">Multiple pointers can be initialized in one statement if they are all the same type:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

<span data-ttu-id="8caa8-114">K chybě při inicializaci ukazatele různých typů, jednoduše vnořit `fixed` příkazy, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8caa8-114">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

<span data-ttu-id="8caa8-115">Po spuštění kódu v příkazu, jsou všechny definovaného proměnné Odepnout a předmět pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="8caa8-115">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="8caa8-116">Proto neukazují na tyto proměnné mimo `fixed` příkaz.</span><span class="sxs-lookup"><span data-stu-id="8caa8-116">Therefore, do not point to those variables outside the `fixed` statement.</span></span> <span data-ttu-id="8caa8-117">Proměnných deklarovaných v `fixed` příkaz jsou omezená na tento příkaz snadněji toto:</span><span class="sxs-lookup"><span data-stu-id="8caa8-117">The variables declared in the `fixed` statement are scoped to that statement, making this easier:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

<span data-ttu-id="8caa8-118">Ukazatele v inicializovat `fixed` příkazy jsou proměnné určené jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="8caa8-118">Pointers initialized in `fixed` statements are readonly variables.</span></span> <span data-ttu-id="8caa8-119">Pokud chcete upravit hodnota ukazatele s hodnotou, musí deklarovat druhý proměnné ukazatele a upravit.</span><span class="sxs-lookup"><span data-stu-id="8caa8-119">If you want to modify the pointer value, you must declare a second pointer variable, and modify that.</span></span> <span data-ttu-id="8caa8-120">Proměnná definovaná v `fixed` nemůže být upravena příkaz:</span><span class="sxs-lookup"><span data-stu-id="8caa8-120">The variable declared in the `fixed` statement cannot be modified:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```


<span data-ttu-id="8caa8-121">V režimu unsafe mohou přidělit paměť v zásobníku, kde se nevztahuje uvolňování paměti a proto nemusí být připojena.</span><span class="sxs-lookup"><span data-stu-id="8caa8-121">In unsafe mode, you can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="8caa8-122">Další informace najdete v tématu [stackalloc](stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="8caa8-122">For more information, see [stackalloc](stackalloc.md).</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="8caa8-123">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8caa8-123">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="8caa8-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="8caa8-124">See Also</span></span>

 [<span data-ttu-id="8caa8-125">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8caa8-125">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="8caa8-126">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8caa8-126">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="8caa8-127">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8caa8-127">C# Keywords</span></span>](index.md)  
 [<span data-ttu-id="8caa8-128">unsafe</span><span class="sxs-lookup"><span data-stu-id="8caa8-128">unsafe</span></span>](unsafe.md)  
 [<span data-ttu-id="8caa8-129">Vyrovnávací paměti pevné velikosti</span><span class="sxs-lookup"><span data-stu-id="8caa8-129">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
