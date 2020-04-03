---
title: příkaz lock - odkaz Jazyka C#
description: Použití příkazu lock jazyka C# k synchronizaci přístupu podprocesu ke sdílenému prostředku
ms.date: 04/02/2020
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 2f2d42ae02a07a5e1b82cefd004f4d03b2a16dff
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635385"
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="a0004-103">příkaz lock (odkaz C# )</span><span class="sxs-lookup"><span data-stu-id="a0004-103">lock statement (C# reference)</span></span>

<span data-ttu-id="a0004-104">Příkaz `lock` získá zámek vzájemné vyloučení pro daný objekt, provede blok příkazu a potom uvolní zámek.</span><span class="sxs-lookup"><span data-stu-id="a0004-104">The `lock` statement acquires the mutual-exclusion lock for a given object, executes a statement block, and then releases the lock.</span></span> <span data-ttu-id="a0004-105">Zatímco zámek je držen, podproces, který drží zámek můžete znovu získat a uvolnit zámek.</span><span class="sxs-lookup"><span data-stu-id="a0004-105">While a lock is held, the thread that holds the lock can again acquire and release the lock.</span></span> <span data-ttu-id="a0004-106">Jakékoli jiné vlákno je blokován o získání zámku a čeká, dokud zámek je uvolněna.</span><span class="sxs-lookup"><span data-stu-id="a0004-106">Any other thread is blocked from acquiring the lock and waits until the lock is released.</span></span>

<span data-ttu-id="a0004-107">Prohlášení `lock` je ve formě</span><span class="sxs-lookup"><span data-stu-id="a0004-107">The `lock` statement is of the form</span></span>

```csharp
lock (x)
{
    // Your code...
}
```

<span data-ttu-id="a0004-108">kde `x` je výraz typu [odkazu](reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="a0004-108">where `x` is an expression of a [reference type](reference-types.md).</span></span> <span data-ttu-id="a0004-109">Je to přesně ekvivalentní</span><span class="sxs-lookup"><span data-stu-id="a0004-109">It's precisely equivalent to</span></span>

```csharp
object __lockObj = x;
bool __lockWasTaken = false;
try
{
    System.Threading.Monitor.Enter(__lockObj, ref __lockWasTaken);
    // Your code...
}
finally
{
    if (__lockWasTaken) System.Threading.Monitor.Exit(__lockObj);
}
```

<span data-ttu-id="a0004-110">Vzhledem k tomu, kód používá [try... finally](try-finally.md) blokovat, zámek je uvolněna i v případě, `lock` že je vyvolána výjimka v rámci těla příkazu.</span><span class="sxs-lookup"><span data-stu-id="a0004-110">Since the code uses a [try...finally](try-finally.md) block, the lock is released even if an exception is thrown within the body of a `lock` statement.</span></span>

<span data-ttu-id="a0004-111">Nelze použít operátor [await](../operators/await.md) v textu příkazu. `lock`</span><span class="sxs-lookup"><span data-stu-id="a0004-111">You can't use the [await operator](../operators/await.md) in the body of a `lock` statement.</span></span>

## <a name="guidelines"></a><span data-ttu-id="a0004-112">Pokyny</span><span class="sxs-lookup"><span data-stu-id="a0004-112">Guidelines</span></span>

<span data-ttu-id="a0004-113">Při synchronizaci přístupu podprocesu ke sdílenému prostředku, `private readonly object balanceLock = new object();`zámek na vyhrazené instance objektu (například) nebo jiné instance, která je nepravděpodobné, že bude použit jako objekt zámku nesouvisející části kódu.</span><span class="sxs-lookup"><span data-stu-id="a0004-113">When you synchronize thread access to a shared resource, lock on a dedicated object instance (for example, `private readonly object balanceLock = new object();`) or another instance that is unlikely to be used as a lock object by unrelated parts of the code.</span></span> <span data-ttu-id="a0004-114">Vyhněte se použití stejné instance objektu zámku pro různé sdílené prostředky, protože by mohlo vést k zablokování nebo konflikty zámku.</span><span class="sxs-lookup"><span data-stu-id="a0004-114">Avoid using the same lock object instance for different shared resources, as it might result in deadlock or lock contention.</span></span> <span data-ttu-id="a0004-115">Zejména se vyhněte použití následující jako zámek objekty:</span><span class="sxs-lookup"><span data-stu-id="a0004-115">In particular, avoid using the following as lock objects:</span></span>

- <span data-ttu-id="a0004-116">`this`, protože jej mohou volající používat jako zámek.</span><span class="sxs-lookup"><span data-stu-id="a0004-116">`this`, as it might be used by the callers as a lock.</span></span>
- <span data-ttu-id="a0004-117"><xref:System.Type>instance, protože ty mohou být získány [typem operátoru](../operators/type-testing-and-cast.md#typeof-operator) nebo odrazem.</span><span class="sxs-lookup"><span data-stu-id="a0004-117"><xref:System.Type> instances, as those might be obtained by the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator or reflection.</span></span>
- <span data-ttu-id="a0004-118">řetězcové instance, včetně řetězcových literál, protože mohou být [internovány](/dotnet/api/system.string.intern#remarks).</span><span class="sxs-lookup"><span data-stu-id="a0004-118">string instances, including string literals, as those might be [interned](/dotnet/api/system.string.intern#remarks).</span></span>

<span data-ttu-id="a0004-119">Podržte zámek tak krátkou dobu, jak je to možné snížit konflikty zámku.</span><span class="sxs-lookup"><span data-stu-id="a0004-119">Hold a lock for as short time as possible to reduce lock contention.</span></span>

## <a name="example"></a><span data-ttu-id="a0004-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0004-120">Example</span></span>

<span data-ttu-id="a0004-121">Následující příklad definuje `Account` třídu, která synchronizuje `balance` přístup k jeho `balanceLock` soukromé pole uzamčením na vyhrazené instanci.</span><span class="sxs-lookup"><span data-stu-id="a0004-121">The following example defines an `Account` class that synchronizes access to its private `balance` field by locking on a dedicated `balanceLock` instance.</span></span> <span data-ttu-id="a0004-122">Použití stejné instance pro uzamčení `balance` zajišťuje, že pole nelze aktualizovat současně dvěma vlákny, které se pokoušejí volat metody `Debit` nebo `Credit` současně.</span><span class="sxs-lookup"><span data-stu-id="a0004-122">Using the same instance for locking ensures that the `balance` field cannot be updated simultaneously by two threads attempting to call the `Debit` or `Credit` methods simultaneously.</span></span>

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## <a name="c-language-specification"></a><span data-ttu-id="a0004-123">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a0004-123">C# language specification</span></span>

<span data-ttu-id="a0004-124">Další informace naleznete v části [příkazu zámku](~/_csharplang/spec/statements.md#the-lock-statement) [ve specifikaci jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="a0004-124">For more information, see [The lock statement](~/_csharplang/spec/statements.md#the-lock-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a0004-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0004-125">See also</span></span>

- [<span data-ttu-id="a0004-126">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="a0004-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a0004-127">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a0004-127">C# keywords</span></span>](index.md)
- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="a0004-128">Přehled primitiv synchronizace</span><span class="sxs-lookup"><span data-stu-id="a0004-128">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
