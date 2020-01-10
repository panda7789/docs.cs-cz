---
title: volatile C# – odkaz
ms.date: 10/24/2018
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: c7a6c442c33ac2b41f652805837f455a957819de
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712842"
---
# <a name="volatile-c-reference"></a><span data-ttu-id="149b1-102">volatile (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="149b1-102">volatile (C# Reference)</span></span>

<span data-ttu-id="149b1-103">Klíčové slovo `volatile` označuje, že pole může být upraveno více vlákny, které jsou spuštěny ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="149b1-103">The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time.</span></span> <span data-ttu-id="149b1-104">Kompilátor, systém modulu runtime a i hardware mohou změnit uspořádání čtení a zápisů do umístění paměti z důvodů výkonu.</span><span class="sxs-lookup"><span data-stu-id="149b1-104">The compiler, the runtime system, and even hardware may rearrange reads and writes to memory locations for performance reasons.</span></span> <span data-ttu-id="149b1-105">Pro pole, která jsou deklarována `volatile`, se tyto optimalizace nevztahují.</span><span class="sxs-lookup"><span data-stu-id="149b1-105">Fields that are declared `volatile` are not subject to these optimizations.</span></span> <span data-ttu-id="149b1-106">Přidání modifikátoru `volatile` zajistí, že všechna vlákna budou sledovat nestálá zápisy provedené jakýmkoli jiným vláknem v pořadí, ve kterém byly provedeny.</span><span class="sxs-lookup"><span data-stu-id="149b1-106">Adding the `volatile` modifier ensures that all threads will observe volatile writes performed by any other thread in the order in which they were performed.</span></span> <span data-ttu-id="149b1-107">Neexistuje žádná záruka na jedno celkové řazení stálých zápisů, které se zobrazuje ze všech vláken provádění.</span><span class="sxs-lookup"><span data-stu-id="149b1-107">There is no guarantee of a single total ordering of volatile writes as seen from all threads of execution.</span></span>

<span data-ttu-id="149b1-108">Klíčové slovo `volatile` lze použít pro pole těchto typů:</span><span class="sxs-lookup"><span data-stu-id="149b1-108">The `volatile` keyword can be applied to fields of these types:</span></span>

- <span data-ttu-id="149b1-109">Odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="149b1-109">Reference types.</span></span>
- <span data-ttu-id="149b1-110">Typy ukazatelů (v nezabezpečeném kontextu).</span><span class="sxs-lookup"><span data-stu-id="149b1-110">Pointer types (in an unsafe context).</span></span> <span data-ttu-id="149b1-111">Všimněte si, že i když samotný ukazatel může být volatile, objekt, na který odkazuje, nemůže být.</span><span class="sxs-lookup"><span data-stu-id="149b1-111">Note that although the pointer itself can be volatile, the object that it points to cannot.</span></span> <span data-ttu-id="149b1-112">Jinými slovy, nelze deklarovat "ukazatel na volatili".</span><span class="sxs-lookup"><span data-stu-id="149b1-112">In other words, you cannot declare a "pointer to volatile."</span></span>
- <span data-ttu-id="149b1-113">Jednoduché typy jako `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `char`, `float`a `bool`.</span><span class="sxs-lookup"><span data-stu-id="149b1-113">Simple types such as `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `char`, `float`, and `bool`.</span></span>
- <span data-ttu-id="149b1-114">`enum` typ s jedním z následujících základních typů: `byte`, `sbyte`, `short`, `ushort`, `int`nebo `uint`.</span><span class="sxs-lookup"><span data-stu-id="149b1-114">An `enum` type with one of the following base types: `byte`, `sbyte`, `short`, `ushort`, `int`, or `uint`.</span></span>
- <span data-ttu-id="149b1-115">Parametry obecného typu označují, že se jedná o odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="149b1-115">Generic type parameters known to be reference types.</span></span>
- <span data-ttu-id="149b1-116"><xref:System.IntPtr> a <xref:System.UIntPtr>.</span><span class="sxs-lookup"><span data-stu-id="149b1-116"><xref:System.IntPtr> and <xref:System.UIntPtr>.</span></span>

<span data-ttu-id="149b1-117">Jiné typy, včetně `double` a `long`, nelze označit jako `volatile`, protože čtení a zápisy do polí těchto typů nelze zaručit jako atomické.</span><span class="sxs-lookup"><span data-stu-id="149b1-117">Other types, including `double` and `long`, cannot be marked `volatile` because reads and writes to fields of those types cannot be guaranteed to be atomic.</span></span> <span data-ttu-id="149b1-118">Chcete-li chránit více vlákenně přístup k těmto typům polí, použijte členy třídy <xref:System.Threading.Interlocked> nebo chraňte přístup pomocí příkazu [`lock`](lock-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="149b1-118">To protect multi-threaded access to those types of fields, use the <xref:System.Threading.Interlocked> class members or protect access using the [`lock`](lock-statement.md) statement.</span></span>

<span data-ttu-id="149b1-119">Klíčové slovo `volatile` lze použít pouze u polí `class` nebo `struct`.</span><span class="sxs-lookup"><span data-stu-id="149b1-119">The `volatile` keyword can only be applied to fields of a `class` or `struct`.</span></span> <span data-ttu-id="149b1-120">Místní proměnné nelze deklarovat `volatile`.</span><span class="sxs-lookup"><span data-stu-id="149b1-120">Local variables cannot be declared `volatile`.</span></span>

## <a name="example"></a><span data-ttu-id="149b1-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="149b1-121">Example</span></span>

<span data-ttu-id="149b1-122">Následující příklad ukazuje, jak deklarovat veřejnou proměnnou pole jako `volatile`.</span><span class="sxs-lookup"><span data-stu-id="149b1-122">The following example shows how to declare a public field variable as `volatile`.</span></span>

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Declaration)]

<span data-ttu-id="149b1-123">Následující příklad ukazuje, jak lze vytvořit pomocné nebo pracovní vlákno, a použít jej k paralelnímu zpracování s primárním vláknem.</span><span class="sxs-lookup"><span data-stu-id="149b1-123">The following example demonstrates how an auxiliary or worker thread can be created and used to perform processing in parallel with that of the primary thread.</span></span> <span data-ttu-id="149b1-124">Další informace o multithreading najdete v tématu [spravovaná vlákna](../../../standard/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="149b1-124">For more information about multithreading, see [Managed Threading](../../../standard/threading/index.md).</span></span>

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Volatile)]

<span data-ttu-id="149b1-125">S modifikátorem `volatile` přidaným do deklarace `_shouldStop`, vždy získáte stejné výsledky (podobně jako v výňatku zobrazeném v předchozím kódu).</span><span class="sxs-lookup"><span data-stu-id="149b1-125">With the `volatile` modifier added to the declaration of `_shouldStop` in place, you'll always get the same results (similar to the excerpt shown in the preceding code).</span></span> <span data-ttu-id="149b1-126">Nicméně bez tohoto modifikátoru u `_shouldStop` člena není chování předvídatelné.</span><span class="sxs-lookup"><span data-stu-id="149b1-126">However, without that modifier on the `_shouldStop` member, the behavior is unpredictable.</span></span> <span data-ttu-id="149b1-127">Metoda `DoWork` může optimalizovat přístup členů, což má za následek čtení zastaralých dat.</span><span class="sxs-lookup"><span data-stu-id="149b1-127">The `DoWork` method may optimize the member access, resulting in reading stale data.</span></span> <span data-ttu-id="149b1-128">Vzhledem k povaze programování s více vlákny je počet zastaralých čtení nepředvídatelný.</span><span class="sxs-lookup"><span data-stu-id="149b1-128">Because of the nature of multi-threaded programming, the number of stale reads is unpredictable.</span></span> <span data-ttu-id="149b1-129">Různá spuštění programu budou mít trochu odlišné výsledky.</span><span class="sxs-lookup"><span data-stu-id="149b1-129">Different runs of the program will produce somewhat different results.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="149b1-130">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="149b1-130">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="149b1-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="149b1-131">See also</span></span>

- [<span data-ttu-id="149b1-132">C#specifikace jazyka: klíčové slovo volatile</span><span class="sxs-lookup"><span data-stu-id="149b1-132">C# language specification: volatile keyword</span></span>](../../../../_csharplang/spec/classes.md#volatile-fields)
- [<span data-ttu-id="149b1-133">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="149b1-133">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="149b1-134">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="149b1-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="149b1-135">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="149b1-135">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="149b1-136">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="149b1-136">Modifiers</span></span>](index.md)
- [<span data-ttu-id="149b1-137">příkaz Lock</span><span class="sxs-lookup"><span data-stu-id="149b1-137">lock statement</span></span>](lock-statement.md)
- <xref:System.Threading.Interlocked>
