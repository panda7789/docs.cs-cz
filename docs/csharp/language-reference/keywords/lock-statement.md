---
title: Lock – příkaz – reference jazyka C#
description: Použití příkazu uzamknout v jazyce C# k synchronizaci přístupu ke vláknu ke sdílenému prostředku
ms.date: 04/02/2020
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 6e9a6975977588ba7692c925d7940cd2ec26671f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406687"
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="75470-103">Lock – příkaz (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="75470-103">lock statement (C# reference)</span></span>

<span data-ttu-id="75470-104">`lock`Příkaz získá zámek vzájemného vyloučení pro daný objekt, spustí blok příkazu a pak uvolní zámek.</span><span class="sxs-lookup"><span data-stu-id="75470-104">The `lock` statement acquires the mutual-exclusion lock for a given object, executes a statement block, and then releases the lock.</span></span> <span data-ttu-id="75470-105">I když je držen zámek, vlákno, které obsahuje zámek, může znovu načíst a uvolnit zámek.</span><span class="sxs-lookup"><span data-stu-id="75470-105">While a lock is held, the thread that holds the lock can again acquire and release the lock.</span></span> <span data-ttu-id="75470-106">Jakékoli jiné vlákno zablokovalo získání zámku a čeká na uvolnění zámku.</span><span class="sxs-lookup"><span data-stu-id="75470-106">Any other thread is blocked from acquiring the lock and waits until the lock is released.</span></span>

<span data-ttu-id="75470-107">`lock`Příkaz má formu.</span><span class="sxs-lookup"><span data-stu-id="75470-107">The `lock` statement is of the form</span></span>

```csharp
lock (x)
{
    // Your code...
}
```

<span data-ttu-id="75470-108">kde `x` je výraz [typu odkazu](reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="75470-108">where `x` is an expression of a [reference type](reference-types.md).</span></span> <span data-ttu-id="75470-109">Je přesně stejný jako</span><span class="sxs-lookup"><span data-stu-id="75470-109">It's precisely equivalent to</span></span>

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

<span data-ttu-id="75470-110">Vzhledem k tomu, že kód používá [Try... finally](try-finally.md) Block, zámek je uvolněn i v případě, že je vyvolána výjimka v těle `lock` příkazu.</span><span class="sxs-lookup"><span data-stu-id="75470-110">Since the code uses a [try...finally](try-finally.md) block, the lock is released even if an exception is thrown within the body of a `lock` statement.</span></span>

<span data-ttu-id="75470-111">V těle příkazu nelze použít [operátor await](../operators/await.md) `lock` .</span><span class="sxs-lookup"><span data-stu-id="75470-111">You can't use the [await operator](../operators/await.md) in the body of a `lock` statement.</span></span>

## <a name="guidelines"></a><span data-ttu-id="75470-112">Pokyny</span><span class="sxs-lookup"><span data-stu-id="75470-112">Guidelines</span></span>

<span data-ttu-id="75470-113">Když synchronizujete přístup vlákna ke sdílenému prostředku, zamkněte instanci vyhrazeného objektu (například `private readonly object balanceLock = new object();` ) nebo jinou instanci, která je pravděpodobně použita jako objekt zámku nesouvisejícími částmi kódu.</span><span class="sxs-lookup"><span data-stu-id="75470-113">When you synchronize thread access to a shared resource, lock on a dedicated object instance (for example, `private readonly object balanceLock = new object();`) or another instance that is unlikely to be used as a lock object by unrelated parts of the code.</span></span> <span data-ttu-id="75470-114">Vyhněte se použití stejné instance uzamknutého objektu u různých sdílených prostředků, protože by mohlo dojít k zablokování nebo zamykání.</span><span class="sxs-lookup"><span data-stu-id="75470-114">Avoid using the same lock object instance for different shared resources, as it might result in deadlock or lock contention.</span></span> <span data-ttu-id="75470-115">Zejména se vyhněte použití následujícího objektu jako zámku objektů:</span><span class="sxs-lookup"><span data-stu-id="75470-115">In particular, avoid using the following as lock objects:</span></span>

- <span data-ttu-id="75470-116">`this`, jak je může používat volající jako zámek.</span><span class="sxs-lookup"><span data-stu-id="75470-116">`this`, as it might be used by the callers as a lock.</span></span>
- <span data-ttu-id="75470-117"><xref:System.Type>instance, které mohou být získány operátorem [typeof](../operators/type-testing-and-cast.md#typeof-operator) nebo reflexe.</span><span class="sxs-lookup"><span data-stu-id="75470-117"><xref:System.Type> instances, as those might be obtained by the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator or reflection.</span></span>
- <span data-ttu-id="75470-118">instance řetězců, včetně řetězcových literálů, by mohly být [interně](/dotnet/api/system.string.intern#remarks).</span><span class="sxs-lookup"><span data-stu-id="75470-118">string instances, including string literals, as those might be [interned](/dotnet/api/system.string.intern#remarks).</span></span>

<span data-ttu-id="75470-119">Pokud chcete snížit kolizí zámků, podržte zámek pro co nejkratší čas.</span><span class="sxs-lookup"><span data-stu-id="75470-119">Hold a lock for as short time as possible to reduce lock contention.</span></span>

## <a name="example"></a><span data-ttu-id="75470-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="75470-120">Example</span></span>

<span data-ttu-id="75470-121">Následující příklad definuje `Account` třídu, která synchronizuje přístup k jejímu soukromému `balance` poli uzamčením na vyhrazené `balanceLock` instanci.</span><span class="sxs-lookup"><span data-stu-id="75470-121">The following example defines an `Account` class that synchronizes access to its private `balance` field by locking on a dedicated `balanceLock` instance.</span></span> <span data-ttu-id="75470-122">Použití stejné instance pro uzamykání zajistí, že `balance` pole nelze současně aktualizovat dvěma vlákny, které se pokoušejí `Debit` současně volat metody nebo `Credit` .</span><span class="sxs-lookup"><span data-stu-id="75470-122">Using the same instance for locking ensures that the `balance` field cannot be updated simultaneously by two threads attempting to call the `Debit` or `Credit` methods simultaneously.</span></span>

[!code-csharp[lock-statement-example](snippets/LockStatementExample.cs)]

## <a name="c-language-specification"></a><span data-ttu-id="75470-123">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="75470-123">C# language specification</span></span>

<span data-ttu-id="75470-124">Další informace naleznete v části [příkaz Lock](~/_csharplang/spec/statements.md#the-lock-statement) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="75470-124">For more information, see [The lock statement](~/_csharplang/spec/statements.md#the-lock-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="75470-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="75470-125">See also</span></span>

- [<span data-ttu-id="75470-126">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="75470-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="75470-127">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="75470-127">C# keywords</span></span>](index.md)
- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="75470-128">Přehled primitiv synchronizace</span><span class="sxs-lookup"><span data-stu-id="75470-128">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
