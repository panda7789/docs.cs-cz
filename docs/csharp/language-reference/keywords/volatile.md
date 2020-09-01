---
description: volatile – reference jazyka C#
title: volatile – reference jazyka C#
ms.date: 10/24/2018
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: bb89e99e8e28ff1e263817f498619dbfae700a50
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141696"
---
# <a name="volatile-c-reference"></a><span data-ttu-id="f4dab-103">volatile (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="f4dab-103">volatile (C# Reference)</span></span>

<span data-ttu-id="f4dab-104">`volatile`Klíčové slovo označuje, že pole může být upraveno více vlákny, které jsou spuštěny ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="f4dab-104">The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time.</span></span> <span data-ttu-id="f4dab-105">Kompilátor, systém modulu runtime a i hardware mohou změnit uspořádání čtení a zápisů do umístění paměti z důvodů výkonu.</span><span class="sxs-lookup"><span data-stu-id="f4dab-105">The compiler, the runtime system, and even hardware may rearrange reads and writes to memory locations for performance reasons.</span></span> <span data-ttu-id="f4dab-106">Pro pole, která jsou deklarována, `volatile` se tyto optimalizace nevztahují.</span><span class="sxs-lookup"><span data-stu-id="f4dab-106">Fields that are declared `volatile` are not subject to these optimizations.</span></span> <span data-ttu-id="f4dab-107">Přidání `volatile` modifikátoru zajistí, že všechna vlákna budou sledovat nestálá zápisy provedené jakýmkoli jiným vláknem v pořadí, ve kterém byly provedeny.</span><span class="sxs-lookup"><span data-stu-id="f4dab-107">Adding the `volatile` modifier ensures that all threads will observe volatile writes performed by any other thread in the order in which they were performed.</span></span> <span data-ttu-id="f4dab-108">Neexistuje žádná záruka na jedno celkové řazení stálých zápisů, které se zobrazuje ze všech vláken provádění.</span><span class="sxs-lookup"><span data-stu-id="f4dab-108">There is no guarantee of a single total ordering of volatile writes as seen from all threads of execution.</span></span>

<span data-ttu-id="f4dab-109">`volatile`Klíčové slovo lze použít pro pole těchto typů:</span><span class="sxs-lookup"><span data-stu-id="f4dab-109">The `volatile` keyword can be applied to fields of these types:</span></span>

- <span data-ttu-id="f4dab-110">Odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="f4dab-110">Reference types.</span></span>
- <span data-ttu-id="f4dab-111">Typy ukazatelů (v nezabezpečeném kontextu).</span><span class="sxs-lookup"><span data-stu-id="f4dab-111">Pointer types (in an unsafe context).</span></span> <span data-ttu-id="f4dab-112">Všimněte si, že i když samotný ukazatel může být volatile, objekt, na který odkazuje, nemůže být.</span><span class="sxs-lookup"><span data-stu-id="f4dab-112">Note that although the pointer itself can be volatile, the object that it points to cannot.</span></span> <span data-ttu-id="f4dab-113">Jinými slovy, nelze deklarovat "ukazatel na volatili".</span><span class="sxs-lookup"><span data-stu-id="f4dab-113">In other words, you cannot declare a "pointer to volatile."</span></span>
- <span data-ttu-id="f4dab-114">Jednoduché typy jako `sbyte` , `byte` , `short` , `ushort` , `int` , `uint` ,, a `char` `float` `bool` .</span><span class="sxs-lookup"><span data-stu-id="f4dab-114">Simple types such as `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `char`, `float`, and `bool`.</span></span>
- <span data-ttu-id="f4dab-115">`enum`Typ s jedním z následujících základních typů: `byte` , `sbyte` , `short` , `ushort` , `int` , nebo `uint` .</span><span class="sxs-lookup"><span data-stu-id="f4dab-115">An `enum` type with one of the following base types: `byte`, `sbyte`, `short`, `ushort`, `int`, or `uint`.</span></span>
- <span data-ttu-id="f4dab-116">Parametry obecného typu označují, že se jedná o odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="f4dab-116">Generic type parameters known to be reference types.</span></span>
- <span data-ttu-id="f4dab-117"><xref:System.IntPtr> a <xref:System.UIntPtr>.</span><span class="sxs-lookup"><span data-stu-id="f4dab-117"><xref:System.IntPtr> and <xref:System.UIntPtr>.</span></span>

<span data-ttu-id="f4dab-118">Jiné typy, včetně `double` a `long` , nelze označit, `volatile` protože čtení a zápisy do polí těchto typů nelze zaručit jako atomické.</span><span class="sxs-lookup"><span data-stu-id="f4dab-118">Other types, including `double` and `long`, cannot be marked `volatile` because reads and writes to fields of those types cannot be guaranteed to be atomic.</span></span> <span data-ttu-id="f4dab-119">Chcete-li chránit více vlákenně přístup k těmto typům polí, použijte <xref:System.Threading.Interlocked> členy třídy nebo chraňte přístup pomocí [`lock`](lock-statement.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="f4dab-119">To protect multi-threaded access to those types of fields, use the <xref:System.Threading.Interlocked> class members or protect access using the [`lock`](lock-statement.md) statement.</span></span>

<span data-ttu-id="f4dab-120">`volatile`Klíčové slovo lze použít pouze pro pole `class` nebo `struct` .</span><span class="sxs-lookup"><span data-stu-id="f4dab-120">The `volatile` keyword can only be applied to fields of a `class` or `struct`.</span></span> <span data-ttu-id="f4dab-121">Místní proměnné nelze deklarovat `volatile` .</span><span class="sxs-lookup"><span data-stu-id="f4dab-121">Local variables cannot be declared `volatile`.</span></span>

## <a name="example"></a><span data-ttu-id="f4dab-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="f4dab-122">Example</span></span>

<span data-ttu-id="f4dab-123">Následující příklad ukazuje, jak deklarovat veřejnou proměnnou pole jako `volatile` .</span><span class="sxs-lookup"><span data-stu-id="f4dab-123">The following example shows how to declare a public field variable as `volatile`.</span></span>

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Declaration)]

<span data-ttu-id="f4dab-124">Následující příklad ukazuje, jak lze vytvořit pomocné nebo pracovní vlákno, a použít jej k paralelnímu zpracování s primárním vláknem.</span><span class="sxs-lookup"><span data-stu-id="f4dab-124">The following example demonstrates how an auxiliary or worker thread can be created and used to perform processing in parallel with that of the primary thread.</span></span> <span data-ttu-id="f4dab-125">Další informace o multithreading najdete v tématu [spravovaná vlákna](../../../standard/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="f4dab-125">For more information about multithreading, see [Managed Threading](../../../standard/threading/index.md).</span></span>

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Volatile)]

<span data-ttu-id="f4dab-126">S `volatile` modifikátorem přidaným do deklarace na `_shouldStop` místě získáte vždy stejné výsledky (podobně jako v výňatku zobrazeném v předchozím kódu).</span><span class="sxs-lookup"><span data-stu-id="f4dab-126">With the `volatile` modifier added to the declaration of `_shouldStop` in place, you'll always get the same results (similar to the excerpt shown in the preceding code).</span></span> <span data-ttu-id="f4dab-127">Nicméně bez tohoto modifikátoru u `_shouldStop` člena není chování předvídatelné.</span><span class="sxs-lookup"><span data-stu-id="f4dab-127">However, without that modifier on the `_shouldStop` member, the behavior is unpredictable.</span></span> <span data-ttu-id="f4dab-128">`DoWork`Metoda může optimalizovat přístup členů, což má za následek čtení zastaralých dat.</span><span class="sxs-lookup"><span data-stu-id="f4dab-128">The `DoWork` method may optimize the member access, resulting in reading stale data.</span></span> <span data-ttu-id="f4dab-129">Vzhledem k povaze programování s více vlákny je počet zastaralých čtení nepředvídatelný.</span><span class="sxs-lookup"><span data-stu-id="f4dab-129">Because of the nature of multi-threaded programming, the number of stale reads is unpredictable.</span></span> <span data-ttu-id="f4dab-130">Různá spuštění programu budou mít trochu odlišné výsledky.</span><span class="sxs-lookup"><span data-stu-id="f4dab-130">Different runs of the program will produce somewhat different results.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f4dab-131">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f4dab-131">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f4dab-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="f4dab-132">See also</span></span>

- [<span data-ttu-id="f4dab-133">Specifikace jazyka C#: klíčové slovo volatile</span><span class="sxs-lookup"><span data-stu-id="f4dab-133">C# language specification: volatile keyword</span></span>](../../../../_csharplang/spec/classes.md#volatile-fields)
- [<span data-ttu-id="f4dab-134">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f4dab-134">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f4dab-135">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="f4dab-135">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f4dab-136">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f4dab-136">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f4dab-137">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="f4dab-137">Modifiers</span></span>](index.md)
- [<span data-ttu-id="f4dab-138">příkaz Lock</span><span class="sxs-lookup"><span data-stu-id="f4dab-138">lock statement</span></span>](lock-statement.md)
- <xref:System.Threading.Interlocked>
