---
title: Lock – příkaz (referenční dokumentace jazyka C#)
description: 'Lock – klíčové slovo se používá v dělení na vlákna '
ms.date: 07/20/2015
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 6ed46837482642dfd7e1a96cd120fc18023c5e9f
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42931190"
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="3cdbf-103">Lock – příkaz (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="3cdbf-103">lock statement (C# Reference)</span></span>

<span data-ttu-id="3cdbf-104">`lock` – Klíčové slovo označí blok příkazu jako kritickou sekci tak, že získání zámku vzájemné vyloučení pro daný objekt, provede příkaz a pak uzamčení uvolní.</span><span class="sxs-lookup"><span data-stu-id="3cdbf-104">The `lock` keyword marks a statement block as a critical section by obtaining the mutual-exclusion lock for a given object, executing a statement, and then releasing the lock.</span></span> <span data-ttu-id="3cdbf-105">Následující příklad obsahuje `lock` příkazu.</span><span class="sxs-lookup"><span data-stu-id="3cdbf-105">The following example includes a `lock` statement.</span></span>

```csharp
class Account
{
    decimal balance;
    private Object thisLock = new Object();

    public void Withdraw(decimal amount)
    {
        lock (thisLock)
        {
            if (amount > balance)
            {
                throw new Exception("Insufficient funds");
            }
            balance -= amount;
        }
    }
}
```

<span data-ttu-id="3cdbf-106">Další informace najdete v tématu [vlákna synchronizace](../../programming-guide/concepts/threading/thread-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="3cdbf-106">For more information, see [Thread Synchronization](../../programming-guide/concepts/threading/thread-synchronization.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="3cdbf-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3cdbf-107">Remarks</span></span>

<span data-ttu-id="3cdbf-108">`lock` – Klíčové slovo se zajistí, že jedno vlákno nezadá důležité části kódu, zatímco jiné vlákno je v části důležité.</span><span class="sxs-lookup"><span data-stu-id="3cdbf-108">The `lock` keyword ensures that one thread does not enter a critical section of code while another thread is in the critical section.</span></span> <span data-ttu-id="3cdbf-109">Pokud jiné vlákno se pokusí zadejte uzamčené kódu, bude čekat, blokovat, dokud se neuvolní objektu.</span><span class="sxs-lookup"><span data-stu-id="3cdbf-109">If another thread tries to enter a locked code, it will wait, block, until the object is released.</span></span>

<span data-ttu-id="3cdbf-110">V části [zřetězení](../../programming-guide/concepts/threading/index.md) popisuje dělení na vlákna.</span><span class="sxs-lookup"><span data-stu-id="3cdbf-110">The section [Threading](../../programming-guide/concepts/threading/index.md) discusses threading.</span></span>

<span data-ttu-id="3cdbf-111">`lock` – Klíčové slovo volání <xref:System.Threading.Monitor.Enter%2A> na začátku bloku a <xref:System.Threading.Monitor.Exit%2A> na konci bloku.</span><span class="sxs-lookup"><span data-stu-id="3cdbf-111">The `lock` keyword calls <xref:System.Threading.Monitor.Enter%2A> at the start of the block and <xref:System.Threading.Monitor.Exit%2A> at the end of the block.</span></span> <span data-ttu-id="3cdbf-112">A <xref:System.Threading.ThreadInterruptedException> je vyvolána, pokud <xref:System.Threading.Thread.Interrupt%2A> přeruší podproces, který čeká na zadání `lock` příkazu.</span><span class="sxs-lookup"><span data-stu-id="3cdbf-112">A <xref:System.Threading.ThreadInterruptedException> is thrown if <xref:System.Threading.Thread.Interrupt%2A> interrupts a thread that is waiting to enter a `lock` statement.</span></span>

<span data-ttu-id="3cdbf-113">Obecně se vyhýbejte zamykání `public` typu nebo instance mimo kontrolu kódu.</span><span class="sxs-lookup"><span data-stu-id="3cdbf-113">In general, avoid locking on a `public` type, or instances beyond your code's control.</span></span> <span data-ttu-id="3cdbf-114">Běžné konstrukce `lock (this)`, `lock (typeof (MyType))`, a `lock ("myLock")` porušují tyto obecné zásady:</span><span class="sxs-lookup"><span data-stu-id="3cdbf-114">The common constructs `lock (this)`, `lock (typeof (MyType))`, and `lock ("myLock")` violate this guideline:</span></span>

- <span data-ttu-id="3cdbf-115">`lock (this)` je nějaký problém, pokud instance je veřejně přístupný.</span><span class="sxs-lookup"><span data-stu-id="3cdbf-115">`lock (this)` is a problem if the instance can be accessed publicly.</span></span>

- <span data-ttu-id="3cdbf-116">`lock (typeof (MyType))` je nějaký problém, pokud `MyType` je veřejně dostupná.</span><span class="sxs-lookup"><span data-stu-id="3cdbf-116">`lock (typeof (MyType))` is a problem if `MyType` is publicly accessible.</span></span>

- <span data-ttu-id="3cdbf-117">`lock("myLock")` je nějaký problém, protože jakýkoli jiný kód v procesu pomocí stejného řetězce, budou sdílet stejnou zámku.</span><span class="sxs-lookup"><span data-stu-id="3cdbf-117">`lock("myLock")` is a problem because any other code in the process using the same string, will share the same lock.</span></span>

<span data-ttu-id="3cdbf-118">Osvědčeným postupem je definovat `private` objekt k uzamčení, nebo `private static` proměnné objektu k ochraně dat, které jsou společné pro všechny instance.</span><span class="sxs-lookup"><span data-stu-id="3cdbf-118">Best practice is to define a `private` object to lock on, or a `private static` object variable to protect data common to all instances.</span></span>

<span data-ttu-id="3cdbf-119">Nelze použít [await](await.md) – klíčové slovo v textu `lock` příkazu.</span><span class="sxs-lookup"><span data-stu-id="3cdbf-119">You can't use the [await](await.md) keyword in the body of a `lock` statement.</span></span>

## <a name="example---threads-without-locking"></a><span data-ttu-id="3cdbf-120">Příklad – bez blokování vlákna</span><span class="sxs-lookup"><span data-stu-id="3cdbf-120">Example - Threads without locking</span></span>

<span data-ttu-id="3cdbf-121">Následující příklad ukazuje, jednoduché použití vlákna bez nutnosti používat jenom v C#:</span><span class="sxs-lookup"><span data-stu-id="3cdbf-121">The following sample shows a simple use of threads without locking in C#:</span></span>

[!code-csharp[csrefKeywordsFixedLock#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsFixedLock/CS/csrefKeywordsFixedLock.cs#5)]

## <a name="example---threads-using-locking"></a><span data-ttu-id="3cdbf-122">Příklad: vlákna používají zamykání</span><span class="sxs-lookup"><span data-stu-id="3cdbf-122">Example - Threads using locking</span></span>

<span data-ttu-id="3cdbf-123">Následující příklad používá vlákna a `lock`.</span><span class="sxs-lookup"><span data-stu-id="3cdbf-123">The following sample uses threads and `lock`.</span></span> <span data-ttu-id="3cdbf-124">Za předpokladu, `lock` příkaz je k dispozici, je důležité části tohoto bloku příkazů a `balance` nikdy bude záporné číslo:</span><span class="sxs-lookup"><span data-stu-id="3cdbf-124">As long as the `lock` statement is present, the statement block is a critical section and `balance` will never become a negative number:</span></span>

[!code-csharp[csrefKeywordsFixedLock#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsFixedLock/CS/csrefKeywordsFixedLock.cs#6)]

## <a name="c-language-specification"></a><span data-ttu-id="3cdbf-125">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3cdbf-125">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="3cdbf-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3cdbf-126">See also</span></span>

- <xref:System.Reflection.MethodImplAttributes>
- <xref:System.Threading.Mutex>
- <xref:System.Threading.Monitor>
- [<span data-ttu-id="3cdbf-127">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3cdbf-127">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="3cdbf-128">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3cdbf-128">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3cdbf-129">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="3cdbf-129">Threading</span></span>](../../programming-guide/concepts/threading/index.md)
- [<span data-ttu-id="3cdbf-130">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3cdbf-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="3cdbf-131">Klíčová slova příkazů</span><span class="sxs-lookup"><span data-stu-id="3cdbf-131">Statement Keywords</span></span>](statement-keywords.md)
- [<span data-ttu-id="3cdbf-132">Propojené operace</span><span class="sxs-lookup"><span data-stu-id="3cdbf-132">Interlocked Operations</span></span>](../../../standard/threading/interlocked-operations.md)
- [<span data-ttu-id="3cdbf-133">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="3cdbf-133">AutoResetEvent</span></span>](../../../standard/threading/autoresetevent.md)
- [<span data-ttu-id="3cdbf-134">Synchronizace vláken</span><span class="sxs-lookup"><span data-stu-id="3cdbf-134">Thread Synchronization</span></span>](../../programming-guide/concepts/threading/thread-synchronization.md)