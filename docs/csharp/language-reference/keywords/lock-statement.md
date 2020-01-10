---
title: příkaz Lock – C# odkaz
description: Použití příkazu C# Lock k synchronizaci přístupu ke vláknu ke sdílenému prostředku
ms.date: 10/01/2018
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 467881dd36c97b6b18b7f31d4e4af25152b0d012
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713391"
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="9351f-103">Lock – příkazC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="9351f-103">lock statement (C# reference)</span></span>

<span data-ttu-id="9351f-104">Příkaz `lock` získá zámek vzájemného vyloučení pro daný objekt, spustí blok příkazu a pak uvolní zámek.</span><span class="sxs-lookup"><span data-stu-id="9351f-104">The `lock` statement acquires the mutual-exclusion lock for a given object, executes a statement block, and then releases the lock.</span></span> <span data-ttu-id="9351f-105">I když je držen zámek, vlákno, které obsahuje zámek, může znovu načíst a uvolnit zámek.</span><span class="sxs-lookup"><span data-stu-id="9351f-105">While a lock is held, the thread that holds the lock can again acquire and release the lock.</span></span> <span data-ttu-id="9351f-106">Jakékoli jiné vlákno zablokovalo získání zámku a čeká na uvolnění zámku.</span><span class="sxs-lookup"><span data-stu-id="9351f-106">Any other thread is blocked from acquiring the lock and waits until the lock is released.</span></span>

<span data-ttu-id="9351f-107">Příkaz `lock` má formu.</span><span class="sxs-lookup"><span data-stu-id="9351f-107">The `lock` statement is of the form</span></span>

```csharp
lock (x)
{
    // Your code...
}
```

<span data-ttu-id="9351f-108">kde `x` je výrazem [typu odkazu](reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="9351f-108">where `x` is an expression of a [reference type](reference-types.md).</span></span> <span data-ttu-id="9351f-109">Je přesně stejný jako</span><span class="sxs-lookup"><span data-stu-id="9351f-109">It's precisely equivalent to</span></span>

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

<span data-ttu-id="9351f-110">Vzhledem k tomu, že kód používá [Try... finally](try-finally.md) Block, zámek je uvolněn i v případě, že je vyvolána výjimka v těle `lock`ho příkazu.</span><span class="sxs-lookup"><span data-stu-id="9351f-110">Since the code uses a [try...finally](try-finally.md) block, the lock is released even if an exception is thrown within the body of a `lock` statement.</span></span>

<span data-ttu-id="9351f-111">V těle příkazu `lock` nelze použít [operátor await](../operators/await.md) .</span><span class="sxs-lookup"><span data-stu-id="9351f-111">You can't use the [await operator](../operators/await.md) in the body of a `lock` statement.</span></span>

## <a name="remarks"></a><span data-ttu-id="9351f-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9351f-112">Remarks</span></span>

<span data-ttu-id="9351f-113">Když synchronizujete přístup vlákna ke sdílenému prostředku, zamkněte instanci vyhrazeného objektu (například `private readonly object balanceLock = new object();`) nebo jinou instanci, která je pravděpodobně použita jako objekt zámku nesouvisejícími částmi kódu.</span><span class="sxs-lookup"><span data-stu-id="9351f-113">When you synchronize thread access to a shared resource, lock on a dedicated object instance (for example, `private readonly object balanceLock = new object();`) or another instance that is unlikely to be used as a lock object by unrelated parts of the code.</span></span> <span data-ttu-id="9351f-114">Vyhněte se použití stejné instance uzamknutého objektu u různých sdílených prostředků, protože by mohlo dojít k zablokování nebo zamykání.</span><span class="sxs-lookup"><span data-stu-id="9351f-114">Avoid using the same lock object instance for different shared resources, as it might result in deadlock or lock contention.</span></span> <span data-ttu-id="9351f-115">Zejména se vyhněte použití následujícího objektu jako zámku objektů:</span><span class="sxs-lookup"><span data-stu-id="9351f-115">In particular, avoid using the following as lock objects:</span></span>

- <span data-ttu-id="9351f-116">`this`, jak ho můžou použít volající jako zámek.</span><span class="sxs-lookup"><span data-stu-id="9351f-116">`this`, as it might be used by the callers as a lock.</span></span>
- <span data-ttu-id="9351f-117">instance <xref:System.Type>, protože by mohly být získány operátorem [typeof](../operators/type-testing-and-cast.md#typeof-operator) nebo reflexe.</span><span class="sxs-lookup"><span data-stu-id="9351f-117"><xref:System.Type> instances, as those might be obtained by the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator or reflection.</span></span>
- <span data-ttu-id="9351f-118">instance řetězců, včetně řetězcových literálů, by mohly být [interně](/dotnet/api/system.string.intern#remarks).</span><span class="sxs-lookup"><span data-stu-id="9351f-118">string instances, including string literals, as those might be [interned](/dotnet/api/system.string.intern#remarks).</span></span>

## <a name="example"></a><span data-ttu-id="9351f-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="9351f-119">Example</span></span>

<span data-ttu-id="9351f-120">Následující příklad definuje třídu `Account`, která synchronizuje přístup k jeho soukromému `balance` poli uzamčením na vyhrazené instanci `balanceLock`.</span><span class="sxs-lookup"><span data-stu-id="9351f-120">The following example defines an `Account` class that synchronizes access to its private `balance` field by locking on a dedicated `balanceLock` instance.</span></span> <span data-ttu-id="9351f-121">Použití stejné instance pro uzamykání zajistí, že pole `balance` nelze současně aktualizovat dvěma vlákny, které se pokoušejí současně volat `Debit` nebo `Credit` metody.</span><span class="sxs-lookup"><span data-stu-id="9351f-121">Using the same instance for locking ensures that the `balance` field cannot be updated simultaneously by two threads attempting to call the `Debit` or `Credit` methods simultaneously.</span></span>

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## <a name="c-language-specification"></a><span data-ttu-id="9351f-122">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9351f-122">C# language specification</span></span>

<span data-ttu-id="9351f-123">Další informace naleznete v části [příkaz Lock](~/_csharplang/spec/statements.md#the-lock-statement) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="9351f-123">For more information, see [The lock statement](~/_csharplang/spec/statements.md#the-lock-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9351f-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9351f-124">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="9351f-125">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="9351f-125">C# reference</span></span>](../index.md)
- [<span data-ttu-id="9351f-126">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9351f-126">C# keywords</span></span>](index.md)
- [<span data-ttu-id="9351f-127">Přehled primitiv synchronizace</span><span class="sxs-lookup"><span data-stu-id="9351f-127">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
