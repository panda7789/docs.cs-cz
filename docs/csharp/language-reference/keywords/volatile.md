---
title: volatilní - C# Reference
ms.date: 10/24/2018
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: c7a6c442c33ac2b41f652805837f455a957819de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712842"
---
# <a name="volatile-c-reference"></a><span data-ttu-id="0acff-102">volatile (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="0acff-102">volatile (C# Reference)</span></span>

<span data-ttu-id="0acff-103">Klíčové `volatile` slovo označuje, že pole může být změněno více vlákny, které jsou spuštěny současně.</span><span class="sxs-lookup"><span data-stu-id="0acff-103">The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time.</span></span> <span data-ttu-id="0acff-104">Kompilátor, runtime systém a dokonce i hardware může změnit uspořádání čtení a zápisy do umístění v paměti z důvodů výkonu.</span><span class="sxs-lookup"><span data-stu-id="0acff-104">The compiler, the runtime system, and even hardware may rearrange reads and writes to memory locations for performance reasons.</span></span> <span data-ttu-id="0acff-105">Pole, která `volatile` jsou deklarována, nepodléhají těmto optimalizacím.</span><span class="sxs-lookup"><span data-stu-id="0acff-105">Fields that are declared `volatile` are not subject to these optimizations.</span></span> <span data-ttu-id="0acff-106">Přidání `volatile` modifikátor zajišťuje, že všechna vlákna budou sledovat těkavé zápisy prováděné jiným vláknem v pořadí, ve kterém byly provedeny.</span><span class="sxs-lookup"><span data-stu-id="0acff-106">Adding the `volatile` modifier ensures that all threads will observe volatile writes performed by any other thread in the order in which they were performed.</span></span> <span data-ttu-id="0acff-107">Neexistuje žádná záruka jednoho celkového pořadí volatile zápisy, jak je vidět ze všech vláken provádění.</span><span class="sxs-lookup"><span data-stu-id="0acff-107">There is no guarantee of a single total ordering of volatile writes as seen from all threads of execution.</span></span>

<span data-ttu-id="0acff-108">Klíčové `volatile` slovo lze použít pro pole těchto typů:</span><span class="sxs-lookup"><span data-stu-id="0acff-108">The `volatile` keyword can be applied to fields of these types:</span></span>

- <span data-ttu-id="0acff-109">Referenční typy.</span><span class="sxs-lookup"><span data-stu-id="0acff-109">Reference types.</span></span>
- <span data-ttu-id="0acff-110">Typy ukazatelů (v nebezpečném kontextu).</span><span class="sxs-lookup"><span data-stu-id="0acff-110">Pointer types (in an unsafe context).</span></span> <span data-ttu-id="0acff-111">Všimněte si, že i když samotný ukazatel může být volatilní, objekt, na který odkazuje, nemůže.</span><span class="sxs-lookup"><span data-stu-id="0acff-111">Note that although the pointer itself can be volatile, the object that it points to cannot.</span></span> <span data-ttu-id="0acff-112">Jinými slovy nelze deklarovat "ukazatel na volatilní."</span><span class="sxs-lookup"><span data-stu-id="0acff-112">In other words, you cannot declare a "pointer to volatile."</span></span>
- <span data-ttu-id="0acff-113">Jednoduché typy, `sbyte` `byte`například , `uint` `char`, `float` `short` `ushort` `int`, `bool`, , , a .</span><span class="sxs-lookup"><span data-stu-id="0acff-113">Simple types such as `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `char`, `float`, and `bool`.</span></span>
- <span data-ttu-id="0acff-114">Typ `enum` s jedním z následujících `byte` `sbyte`základních `short` `ushort`typů: , , , , `int`, nebo `uint`.</span><span class="sxs-lookup"><span data-stu-id="0acff-114">An `enum` type with one of the following base types: `byte`, `sbyte`, `short`, `ushort`, `int`, or `uint`.</span></span>
- <span data-ttu-id="0acff-115">Parametry obecného typu, o kterých je známo, že se považují za typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="0acff-115">Generic type parameters known to be reference types.</span></span>
- <span data-ttu-id="0acff-116"><xref:System.IntPtr> a <xref:System.UIntPtr>.</span><span class="sxs-lookup"><span data-stu-id="0acff-116"><xref:System.IntPtr> and <xref:System.UIntPtr>.</span></span>

<span data-ttu-id="0acff-117">Jiné typy, `double` `long`včetně a `volatile` , nelze označit, protože čtení a zápisy do polí těchto typů nelze zaručit, že jsou atomické.</span><span class="sxs-lookup"><span data-stu-id="0acff-117">Other types, including `double` and `long`, cannot be marked `volatile` because reads and writes to fields of those types cannot be guaranteed to be atomic.</span></span> <span data-ttu-id="0acff-118">Chcete-li chránit vícevláknový přístup k těmto <xref:System.Threading.Interlocked> typům polí, [`lock`](lock-statement.md) použijte členy třídy nebo chraňte přístup pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="0acff-118">To protect multi-threaded access to those types of fields, use the <xref:System.Threading.Interlocked> class members or protect access using the [`lock`](lock-statement.md) statement.</span></span>

<span data-ttu-id="0acff-119">Klíčové `volatile` slovo lze použít pouze `class` pro `struct`pole nebo .</span><span class="sxs-lookup"><span data-stu-id="0acff-119">The `volatile` keyword can only be applied to fields of a `class` or `struct`.</span></span> <span data-ttu-id="0acff-120">Místní proměnné nelze `volatile`deklarovat .</span><span class="sxs-lookup"><span data-stu-id="0acff-120">Local variables cannot be declared `volatile`.</span></span>

## <a name="example"></a><span data-ttu-id="0acff-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="0acff-121">Example</span></span>

<span data-ttu-id="0acff-122">Následující příklad ukazuje, jak deklarovat proměnnou veřejného pole jako `volatile`.</span><span class="sxs-lookup"><span data-stu-id="0acff-122">The following example shows how to declare a public field variable as `volatile`.</span></span>

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Declaration)]

<span data-ttu-id="0acff-123">Následující příklad ukazuje, jak pomocné nebo pracovní vlákno lze vytvořit a použít k provádění zpracování paralelně s primární vlákno.</span><span class="sxs-lookup"><span data-stu-id="0acff-123">The following example demonstrates how an auxiliary or worker thread can be created and used to perform processing in parallel with that of the primary thread.</span></span> <span data-ttu-id="0acff-124">Další informace o vícevláknovém řízení naleznete v [tématu Managed Threading](../../../standard/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="0acff-124">For more information about multithreading, see [Managed Threading](../../../standard/threading/index.md).</span></span>

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Volatile)]

<span data-ttu-id="0acff-125">S `volatile` modifikátor přidán `_shouldStop` do deklarace na místě, budete vždy získat stejné výsledky (podobně jako výňatek je uvedeno v předchozím kódu).</span><span class="sxs-lookup"><span data-stu-id="0acff-125">With the `volatile` modifier added to the declaration of `_shouldStop` in place, you'll always get the same results (similar to the excerpt shown in the preceding code).</span></span> <span data-ttu-id="0acff-126">Však bez tohoto modifikátoru `_shouldStop` na člena chování je nepředvídatelné.</span><span class="sxs-lookup"><span data-stu-id="0acff-126">However, without that modifier on the `_shouldStop` member, the behavior is unpredictable.</span></span> <span data-ttu-id="0acff-127">Metoda `DoWork` může optimalizovat přístup člena, výsledkem čtení zastaralých dat.</span><span class="sxs-lookup"><span data-stu-id="0acff-127">The `DoWork` method may optimize the member access, resulting in reading stale data.</span></span> <span data-ttu-id="0acff-128">Vzhledem k povaze vícevláknové programování počet zastaralých čtení je nepředvídatelné.</span><span class="sxs-lookup"><span data-stu-id="0acff-128">Because of the nature of multi-threaded programming, the number of stale reads is unpredictable.</span></span> <span data-ttu-id="0acff-129">Různé běhy programu bude produkovat poněkud odlišné výsledky.</span><span class="sxs-lookup"><span data-stu-id="0acff-129">Different runs of the program will produce somewhat different results.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0acff-130">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0acff-130">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="0acff-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="0acff-131">See also</span></span>

- [<span data-ttu-id="0acff-132">Specifikace jazyka C#: těkavé klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="0acff-132">C# language specification: volatile keyword</span></span>](../../../../_csharplang/spec/classes.md#volatile-fields)
- [<span data-ttu-id="0acff-133">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0acff-133">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0acff-134">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0acff-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0acff-135">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="0acff-135">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="0acff-136">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="0acff-136">Modifiers</span></span>](index.md)
- [<span data-ttu-id="0acff-137">příkaz lock</span><span class="sxs-lookup"><span data-stu-id="0acff-137">lock statement</span></span>](lock-statement.md)
- <xref:System.Threading.Interlocked>
