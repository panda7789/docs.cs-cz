---
title: lock – příkaz (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 2ce870e8caa67d780ce603a6f1dbcc7cd303b842
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960949"
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="d700f-102">lock – příkaz (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d700f-102">lock Statement (C# Reference)</span></span>
<span data-ttu-id="d700f-103">`lock` – Klíčové slovo označí blok příkazu jako kritickou sekci tak, že získání zámku vzájemné vyloučení pro daný objekt, provede příkaz a pak uzamčení uvolní.</span><span class="sxs-lookup"><span data-stu-id="d700f-103">The `lock` keyword marks a statement block as a critical section by obtaining the mutual-exclusion lock for a given object, executing a statement, and then releasing the lock.</span></span> <span data-ttu-id="d700f-104">Následující příklad obsahuje `lock` příkazu.</span><span class="sxs-lookup"><span data-stu-id="d700f-104">The following example includes a `lock` statement.</span></span>  
  
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
  
 <span data-ttu-id="d700f-105">Další informace najdete v tématu [vlákna synchronizace](../../programming-guide/concepts/threading/thread-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="d700f-105">For more information, see [Thread Synchronization](../../programming-guide/concepts/threading/thread-synchronization.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d700f-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d700f-106">Remarks</span></span>  
 <span data-ttu-id="d700f-107">`lock` – Klíčové slovo se zajistí, že jedno vlákno nezadá důležité části kódu, zatímco jiné vlákno je v části důležité.</span><span class="sxs-lookup"><span data-stu-id="d700f-107">The `lock` keyword ensures that one thread does not enter a critical section of code while another thread is in the critical section.</span></span> <span data-ttu-id="d700f-108">Pokud jiné vlákno se pokusí zadejte uzamčené kódu, bude čekat, blokovat, dokud se neuvolní objektu.</span><span class="sxs-lookup"><span data-stu-id="d700f-108">If another thread tries to enter a locked code, it will wait, block, until the object is released.</span></span>  
  
 <span data-ttu-id="d700f-109">V části [zřetězení](../../programming-guide/concepts/threading/index.md) popisuje dělení na vlákna.</span><span class="sxs-lookup"><span data-stu-id="d700f-109">The section [Threading](../../programming-guide/concepts/threading/index.md) discusses threading.</span></span>  
  
 <span data-ttu-id="d700f-110">`lock` – Klíčové slovo volání <xref:System.Threading.Monitor.Enter%2A> na začátku bloku a <xref:System.Threading.Monitor.Exit%2A> na konci bloku.</span><span class="sxs-lookup"><span data-stu-id="d700f-110">The `lock` keyword calls <xref:System.Threading.Monitor.Enter%2A> at the start of the block and <xref:System.Threading.Monitor.Exit%2A> at the end of the block.</span></span> <span data-ttu-id="d700f-111">A <xref:System.Threading.ThreadInterruptedException> je vyvolána, pokud <xref:System.Threading.Thread.Interrupt%2A> přeruší podproces, který čeká na zadání `lock` příkazu.</span><span class="sxs-lookup"><span data-stu-id="d700f-111">A <xref:System.Threading.ThreadInterruptedException> is thrown if <xref:System.Threading.Thread.Interrupt%2A> interrupts a thread that is waiting to enter a `lock` statement.</span></span>  
  
 <span data-ttu-id="d700f-112">Obecně se vyhýbejte zamykání `public` typu nebo instance mimo kontrolu kódu.</span><span class="sxs-lookup"><span data-stu-id="d700f-112">In general, avoid locking on a `public` type, or instances beyond your code's control.</span></span> <span data-ttu-id="d700f-113">Běžné konstrukce `lock (this)`, `lock (typeof (MyType))`, a `lock ("myLock")` porušují tyto obecné zásady:</span><span class="sxs-lookup"><span data-stu-id="d700f-113">The common constructs `lock (this)`, `lock (typeof (MyType))`, and `lock ("myLock")` violate this guideline:</span></span>  
  
-   <span data-ttu-id="d700f-114">`lock (this)` je nějaký problém, pokud instance je veřejně přístupný.</span><span class="sxs-lookup"><span data-stu-id="d700f-114">`lock (this)` is a problem if the instance can be accessed publicly.</span></span>  
  
-   <span data-ttu-id="d700f-115">`lock (typeof (MyType))` je nějaký problém, pokud `MyType` je veřejně dostupná.</span><span class="sxs-lookup"><span data-stu-id="d700f-115">`lock (typeof (MyType))` is a problem if `MyType` is publicly accessible.</span></span>  
  
-   <span data-ttu-id="d700f-116">`lock("myLock")` je nějaký problém, protože jakýkoli jiný kód v procesu pomocí stejného řetězce, budou sdílet stejnou zámku.</span><span class="sxs-lookup"><span data-stu-id="d700f-116">`lock("myLock")` is a problem because any other code in the process using the same string, will share the same lock.</span></span>  
  
 <span data-ttu-id="d700f-117">Osvědčeným postupem je definovat `private` objekt k uzamčení, nebo `private static` proměnné objektu k ochraně dat, které jsou společné pro všechny instance.</span><span class="sxs-lookup"><span data-stu-id="d700f-117">Best practice is to define a `private` object to lock on, or a `private static` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="d700f-118">Nelze použít [await](../../../csharp/language-reference/keywords/await.md) – klíčové slovo v textu `lock` příkazu.</span><span class="sxs-lookup"><span data-stu-id="d700f-118">You can't use the [await](../../../csharp/language-reference/keywords/await.md) keyword in the body of a `lock` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d700f-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="d700f-119">Example</span></span>  
 <span data-ttu-id="d700f-120">Následující příklad ukazuje, jednoduché použití vlákna bez nutnosti používat jenom v C#.</span><span class="sxs-lookup"><span data-stu-id="d700f-120">The following sample shows a simple use of threads without locking in C#.</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="d700f-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="d700f-121">Example</span></span>  
 <span data-ttu-id="d700f-122">Následující příklad používá vlákna a `lock`.</span><span class="sxs-lookup"><span data-stu-id="d700f-122">The following sample uses threads and `lock`.</span></span> <span data-ttu-id="d700f-123">Za předpokladu, `lock` příkaz je k dispozici, je důležité části tohoto bloku příkazů a `balance` nikdy bude záporné číslo.</span><span class="sxs-lookup"><span data-stu-id="d700f-123">As long as the `lock` statement is present, the statement block is a critical section and `balance` will never become a negative number.</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="d700f-124">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d700f-124">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d700f-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="d700f-125">See Also</span></span>  
 <xref:System.Reflection.MethodImplAttributes>  
 <xref:System.Threading.Mutex>  
 [<span data-ttu-id="d700f-126">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d700f-126">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d700f-127">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d700f-127">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d700f-128">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="d700f-128">Threading</span></span>](../../programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="d700f-129">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d700f-129">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="d700f-130">Klíčová slova příkazů</span><span class="sxs-lookup"><span data-stu-id="d700f-130">Statement Keywords</span></span>](../../../csharp/language-reference/keywords/statement-keywords.md)  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="d700f-131">Propojené operace</span><span class="sxs-lookup"><span data-stu-id="d700f-131">Interlocked Operations</span></span>](../../../standard/threading/interlocked-operations.md)  
 [<span data-ttu-id="d700f-132">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="d700f-132">AutoResetEvent</span></span>](../../../standard/threading/autoresetevent.md)  
 [<span data-ttu-id="d700f-133">Synchronizace vláken</span><span class="sxs-lookup"><span data-stu-id="d700f-133">Thread Synchronization</span></span>](../../programming-guide/concepts/threading/thread-synchronization.md)
