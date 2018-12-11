---
title: Lock – příkaz - C# odkaz
ms.custom: seodec18
description: Použijte příkaz lock jazyka C# k synchronizaci přístupu vláken ke sdíleným prostředkům
ms.date: 10/01/2018
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 63fadd3c37c7533211e7bd0ac07952ca99fd6a79
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244256"
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="c5a0f-103">Lock – příkaz (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c5a0f-103">lock statement (C# Reference)</span></span>

<span data-ttu-id="c5a0f-104">`lock` Příkaz získá vyloučeného zámek pro daný objekt, provede blok příkazů a poté uvolní zámek.</span><span class="sxs-lookup"><span data-stu-id="c5a0f-104">The `lock` statement acquires the mutual-exclusion lock for a given object, executes a statement block, and then releases the lock.</span></span> <span data-ttu-id="c5a0f-105">Dokud je držen zámek, vlákna, která je držitelem zámku znovu získat a uvolní zámek.</span><span class="sxs-lookup"><span data-stu-id="c5a0f-105">While a lock is held, the thread that holds the lock can again acquire and release the lock.</span></span> <span data-ttu-id="c5a0f-106">Ostatní vlákna je blokovaný zámek získávání a čeká na zámek je uvolněn.</span><span class="sxs-lookup"><span data-stu-id="c5a0f-106">Any other thread is blocked from acquiring the lock and waits until the lock is released.</span></span>

<span data-ttu-id="c5a0f-107">`lock` Příkaz má formát</span><span class="sxs-lookup"><span data-stu-id="c5a0f-107">The `lock` statement is of the form</span></span>

```csharp
lock (x)
{
    // Your code...
}
```

<span data-ttu-id="c5a0f-108">kde `x` je výraz [odkazovat na typ](reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="c5a0f-108">where `x` is an expression of a [reference type](reference-types.md).</span></span> <span data-ttu-id="c5a0f-109">To je přesně odpovídá</span><span class="sxs-lookup"><span data-stu-id="c5a0f-109">It's precisely equivalent to</span></span>

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

<span data-ttu-id="c5a0f-110">Protože kód používá [try... finally](try-finally.md) bloku, zámek je všeobecně dostupné i v případě, že dojde k výjimce v těle `lock` příkaz.</span><span class="sxs-lookup"><span data-stu-id="c5a0f-110">Since the code uses a [try...finally](try-finally.md) block, the lock is released even if an exception is thrown within the body of a `lock` statement.</span></span>

<span data-ttu-id="c5a0f-111">Nelze použít [await](await.md) – klíčové slovo v textu `lock` příkazu.</span><span class="sxs-lookup"><span data-stu-id="c5a0f-111">You can't use the [await](await.md) keyword in the body of a `lock` statement.</span></span>

## <a name="remarks"></a><span data-ttu-id="c5a0f-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c5a0f-112">Remarks</span></span>

<span data-ttu-id="c5a0f-113">Při synchronizaci přístupu vláken ke sdíleným prostředkům uzamčení na instanci vyhrazené objektu (například `private readonly object balanceLock = new object();`) nebo do jiné instance, která pravděpodobně nebude používat jako objekt zámek nesouvisejících částí kódu.</span><span class="sxs-lookup"><span data-stu-id="c5a0f-113">When you synchronize thread access to a shared resource, lock on a dedicated object instance (for example, `private readonly object balanceLock = new object();`) or another instance that is unlikely to be used as a lock object by unrelated parts of the code.</span></span> <span data-ttu-id="c5a0f-114">Vyhněte se použití stejné instance objektu zámku pro různé sdílené prostředky, protože může dojít k zablokování nebo lock kolize.</span><span class="sxs-lookup"><span data-stu-id="c5a0f-114">Avoid using the same lock object instance for different shared resources, as it might result in deadlock or lock contention.</span></span> <span data-ttu-id="c5a0f-115">Konkrétně se vyhněte se použití následujících jako objekty zámku:</span><span class="sxs-lookup"><span data-stu-id="c5a0f-115">In particular, avoid using the following as lock objects:</span></span>

- <span data-ttu-id="c5a0f-116">`this`, jak ho můžou používat volající jako zámek.</span><span class="sxs-lookup"><span data-stu-id="c5a0f-116">`this`, as it might be used by the callers as a lock.</span></span>
- <span data-ttu-id="c5a0f-117"><xref:System.Type> instance, jako ty, může získat službou [typeof](typeof.md) operátor nebo reflexe.</span><span class="sxs-lookup"><span data-stu-id="c5a0f-117"><xref:System.Type> instances, as those might be obtained by the [typeof](typeof.md) operator or reflection.</span></span>
- <span data-ttu-id="c5a0f-118">řetězec instance, včetně řetězcové literály, protože ty můžou být [internovány](/dotnet/api/system.string.intern#remarks).</span><span class="sxs-lookup"><span data-stu-id="c5a0f-118">string instances, including string literals, as those might be [interned](/dotnet/api/system.string.intern#remarks).</span></span>

## <a name="example"></a><span data-ttu-id="c5a0f-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="c5a0f-119">Example</span></span>

<span data-ttu-id="c5a0f-120">Následující příklad definuje `Account` třídu, která se synchronizuje přístup k jeho privátní `balance` pole, a to na vyhrazené zamykání `balanceLock` instance.</span><span class="sxs-lookup"><span data-stu-id="c5a0f-120">The following example defines an `Account` class that synchronizes access to its private `balance` field by locking on a dedicated `balanceLock` instance.</span></span> <span data-ttu-id="c5a0f-121">Použití stejné instance pro uzamčení zajišťuje, že `balance` pole nejde aktualizovat současně dvěma vlákny pokusu o volání `Debit` nebo `Credit` metod současně.</span><span class="sxs-lookup"><span data-stu-id="c5a0f-121">Using the same instance for locking ensures that the `balance` field cannot be updated simultaneously by two threads attempting to call the `Debit` or `Credit` methods simultaneously.</span></span>

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## <a name="c-language-specification"></a><span data-ttu-id="c5a0f-122">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c5a0f-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c5a0f-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c5a0f-123">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="c5a0f-124">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c5a0f-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c5a0f-125">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c5a0f-125">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c5a0f-126">Klíčová slova příkazů</span><span class="sxs-lookup"><span data-stu-id="c5a0f-126">Statement Keywords</span></span>](statement-keywords.md)
- [<span data-ttu-id="c5a0f-127">Přehled primitiv synchronizace</span><span class="sxs-lookup"><span data-stu-id="c5a0f-127">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)