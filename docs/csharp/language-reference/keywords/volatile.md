---
title: volatile – C# odkaz
ms.custom: seodec18
ms.date: 10/24/2018
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: f96b450eea5f2b45d256bfe00a18aa616d501d69
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612176"
---
# <a name="volatile-c-reference"></a><span data-ttu-id="075d2-102">volatile (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="075d2-102">volatile (C# Reference)</span></span>

<span data-ttu-id="075d2-103">`volatile` – Klíčové slovo určuje, že pole může být upraveno ve víc vláknech, které jsou spuštěny ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="075d2-103">The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time.</span></span> <span data-ttu-id="075d2-104">Kompilátor, systém modulu runtime a dokonce i hardware mohou změnit uspořádání operací čtení a zápisu do umístění v paměti z důvodů výkonu.</span><span class="sxs-lookup"><span data-stu-id="075d2-104">The compiler, the runtime system, and even hardware may rearrange reads and writes to memory locations for performance reasons.</span></span> <span data-ttu-id="075d2-105">Pole, které jsou deklarovány `volatile` se nevztahují tato optimalizace.</span><span class="sxs-lookup"><span data-stu-id="075d2-105">Fields that are declared `volatile` are not subject to these optimizations.</span></span> <span data-ttu-id="075d2-106">Přidávání `volatile` modifikátor zajistí, že všechna vlákna budou sledovat volatile zápisy provádí ostatní vlákna v pořadí, ve kterém byly provedeny.</span><span class="sxs-lookup"><span data-stu-id="075d2-106">Adding the `volatile` modifier ensures that all threads will observe volatile writes performed by any other thread in the order in which they were performed.</span></span> <span data-ttu-id="075d2-107">Není zaručeno jeden celkový řazení volatile zápisů pohledu ze všech vláken, která.</span><span class="sxs-lookup"><span data-stu-id="075d2-107">There is no guarantee of a single total ordering of volatile writes as seen from all threads of execution.</span></span>

<span data-ttu-id="075d2-108">`volatile` – Klíčové slovo lze použít u polí těchto typů:</span><span class="sxs-lookup"><span data-stu-id="075d2-108">The `volatile` keyword can be applied to fields of these types:</span></span>

- <span data-ttu-id="075d2-109">Typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="075d2-109">Reference types.</span></span>
- <span data-ttu-id="075d2-110">Typy ukazatelů (v nezabezpečeném kontextu.).</span><span class="sxs-lookup"><span data-stu-id="075d2-110">Pointer types (in an unsafe context).</span></span> <span data-ttu-id="075d2-111">Všimněte si, že i když se ukazatel sám, může být typu volatile, objekt, který odkazuje na nelze.</span><span class="sxs-lookup"><span data-stu-id="075d2-111">Note that although the pointer itself can be volatile, the object that it points to cannot.</span></span> <span data-ttu-id="075d2-112">Jinými slovy nelze deklarovat "ukazatel na volatile."</span><span class="sxs-lookup"><span data-stu-id="075d2-112">In other words, you cannot declare a "pointer to volatile."</span></span>
- <span data-ttu-id="075d2-113">Jednoduché typy, jako `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `char`, `float`, a `bool`.</span><span class="sxs-lookup"><span data-stu-id="075d2-113">Simple types such as `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `char`, `float`, and `bool`.</span></span>
- <span data-ttu-id="075d2-114">`enum` Typ s jedním z následujících základních typů: `byte`, `sbyte`, `short`, `ushort`, `int`, nebo `uint`.</span><span class="sxs-lookup"><span data-stu-id="075d2-114">An `enum` type with one of the following base types: `byte`, `sbyte`, `short`, `ushort`, `int`, or `uint`.</span></span>
- <span data-ttu-id="075d2-115">Parametry obecného typu známé jako referenční typy.</span><span class="sxs-lookup"><span data-stu-id="075d2-115">Generic type parameters known to be reference types.</span></span>
- <span data-ttu-id="075d2-116"><xref:System.IntPtr> a <xref:System.UIntPtr>.</span><span class="sxs-lookup"><span data-stu-id="075d2-116"><xref:System.IntPtr> and <xref:System.UIntPtr>.</span></span>

<span data-ttu-id="075d2-117">Jiné typy, včetně `double` a `long`, nemohou být označeny `volatile` protože čtení a zápis do polí těchto typů nelze zaručit bylo atomické.</span><span class="sxs-lookup"><span data-stu-id="075d2-117">Other types, including `double` and `long`, cannot be marked `volatile` because reads and writes to fields of those types cannot be guaranteed to be atomic.</span></span> <span data-ttu-id="075d2-118">Chcete-li chránit vícevláknový přístup k těmto typům pole, použijte <xref:System.Threading.Interlocked> členy třídy nebo chránit pomocí přístupu [ `lock` ](lock-statement.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="075d2-118">To protect multi-threaded access to those types of fields, use the <xref:System.Threading.Interlocked> class members or protect access using the [`lock`](lock-statement.md) statement.</span></span>

<span data-ttu-id="075d2-119">`volatile` – Klíčové slovo lze použít pouze pro pole `class` nebo `struct`.</span><span class="sxs-lookup"><span data-stu-id="075d2-119">The `volatile` keyword can only be applied to fields of a `class` or `struct`.</span></span> <span data-ttu-id="075d2-120">Místní proměnné nelze použít deklaraci `volatile`.</span><span class="sxs-lookup"><span data-stu-id="075d2-120">Local variables cannot be declared `volatile`.</span></span>

## <a name="example"></a><span data-ttu-id="075d2-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="075d2-121">Example</span></span>

<span data-ttu-id="075d2-122">Následující příklad ukazuje, jak deklarovat proměnnou veřejné pole jako `volatile`.</span><span class="sxs-lookup"><span data-stu-id="075d2-122">The following example shows how to declare a public field variable as `volatile`.</span></span>

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Declaration)]

<span data-ttu-id="075d2-123">Následující příklad ukazuje, jak můžete vytvořit a používá ke zpracování paralelní s ním primární vlákno pomocné nebo pracovní vlákno.</span><span class="sxs-lookup"><span data-stu-id="075d2-123">The following example demonstrates how an auxiliary or worker thread can be created and used to perform processing in parallel with that of the primary thread.</span></span> <span data-ttu-id="075d2-124">Další informace o multithreading, viz [dělení na spravovaná vlákna](../../../standard/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="075d2-124">For more information about multithreading, see [Managed Threading](../../../standard/threading/index.md).</span></span>

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Volatile)]

<span data-ttu-id="075d2-125">S `volatile` modifikátor přidána do deklarace `_shouldStop` na místě, vždy dosáhnete stejných výsledků (podobně jako výňatek je znázorněno v předchozím kódu).</span><span class="sxs-lookup"><span data-stu-id="075d2-125">With the `volatile` modifier added to the declaration of `_shouldStop` in place, you'll always get the same results (similar to the excerpt shown in the preceding code).</span></span> <span data-ttu-id="075d2-126">Ale bez tento modifikátor `_shouldStop` člen, nepředvídatelné chování.</span><span class="sxs-lookup"><span data-stu-id="075d2-126">However, without that modifier on the `_shouldStop` member, the behavior is unpredictable.</span></span> <span data-ttu-id="075d2-127">`DoWork` Metoda může optimalizovat přístup ke členu, což vede k zastaralých dat pro čtení.</span><span class="sxs-lookup"><span data-stu-id="075d2-127">The `DoWork` method may optimize the member access, resulting in reading stale data.</span></span> <span data-ttu-id="075d2-128">Vzhledem k povaze vícevláknového programování je počet zastaralých čtení nepředvídatelné.</span><span class="sxs-lookup"><span data-stu-id="075d2-128">Because of the nature of multi-threaded programming, the number of stale reads is unpredictable.</span></span> <span data-ttu-id="075d2-129">Během různých spuštění programu se poněkud liší výsledkům.</span><span class="sxs-lookup"><span data-stu-id="075d2-129">Different runs of the program will produce somewhat different results.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="075d2-130">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="075d2-130">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="075d2-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="075d2-131">See also</span></span>

- [<span data-ttu-id="075d2-132">C#Specifikace jazyka: volatile – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="075d2-132">C# language specification: volatile keyword</span></span>](../../../../_csharplang/spec/classes.md#volatile-fields)
- [<span data-ttu-id="075d2-133">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="075d2-133">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="075d2-134">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="075d2-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="075d2-135">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="075d2-135">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="075d2-136">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="075d2-136">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="075d2-137">Příkaz Lock</span><span class="sxs-lookup"><span data-stu-id="075d2-137">lock statement</span></span>](lock-statement.md)
- <span data-ttu-id="075d2-138"><xref:System.Threading.Interlocked> Třída</span><span class="sxs-lookup"><span data-stu-id="075d2-138"><xref:System.Threading.Interlocked> class</span></span>