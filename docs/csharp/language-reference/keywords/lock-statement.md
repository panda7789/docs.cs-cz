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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33274216"
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="276db-102">lock – příkaz (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="276db-102">lock Statement (C# Reference)</span></span>
<span data-ttu-id="276db-103">`lock` – Klíčové slovo označí blok příkaz jako důležitý oddíl získání zámku vzájemné vyloučení pro daný objekt, provádění příkazu a pak uvolnění uzamčení.</span><span class="sxs-lookup"><span data-stu-id="276db-103">The `lock` keyword marks a statement block as a critical section by obtaining the mutual-exclusion lock for a given object, executing a statement, and then releasing the lock.</span></span> <span data-ttu-id="276db-104">Následující příklad obsahuje `lock` příkaz.</span><span class="sxs-lookup"><span data-stu-id="276db-104">The following example includes a `lock` statement.</span></span>  
  
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
  
 <span data-ttu-id="276db-105">Další informace najdete v tématu [vláken synchronizace](../../programming-guide/concepts/threading/thread-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="276db-105">For more information, see [Thread Synchronization](../../programming-guide/concepts/threading/thread-synchronization.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="276db-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="276db-106">Remarks</span></span>  
 <span data-ttu-id="276db-107">`lock` – Klíčové slovo zajistí, že jedno vlákno nevstupuje kritické části kódu, zatímco jiné vlákno je v části důležité.</span><span class="sxs-lookup"><span data-stu-id="276db-107">The `lock` keyword ensures that one thread does not enter a critical section of code while another thread is in the critical section.</span></span> <span data-ttu-id="276db-108">Pokud jiné vlákno se pokusí zadejte uzamčeném kód, bude čekat, blokovat, dokud uvolnění objektu.</span><span class="sxs-lookup"><span data-stu-id="276db-108">If another thread tries to enter a locked code, it will wait, block, until the object is released.</span></span>  
  
 <span data-ttu-id="276db-109">V části [zřetězení](../../programming-guide/concepts/threading/index.md) popisuje dělení na vlákna.</span><span class="sxs-lookup"><span data-stu-id="276db-109">The section [Threading](../../programming-guide/concepts/threading/index.md) discusses threading.</span></span>  
  
 <span data-ttu-id="276db-110">`lock` – Klíčové slovo volání <xref:System.Threading.Monitor.Enter%2A> na začátku bloku a <xref:System.Threading.Monitor.Exit%2A> na konci bloku.</span><span class="sxs-lookup"><span data-stu-id="276db-110">The `lock` keyword calls <xref:System.Threading.Monitor.Enter%2A> at the start of the block and <xref:System.Threading.Monitor.Exit%2A> at the end of the block.</span></span> <span data-ttu-id="276db-111">A <xref:System.Threading.ThreadInterruptedException> je vyvolána, pokud <xref:System.Threading.Thread.Interrupt%2A> přerušení vlákno, které čeká na zadejte `lock` příkaz.</span><span class="sxs-lookup"><span data-stu-id="276db-111">A <xref:System.Threading.ThreadInterruptedException> is thrown if <xref:System.Threading.Thread.Interrupt%2A> interrupts a thread that is waiting to enter a `lock` statement.</span></span>  
  
 <span data-ttu-id="276db-112">Obecně není vhodné používat na zamykání `public` typu nebo instancí mimo kontrolu vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="276db-112">In general, avoid locking on a `public` type, or instances beyond your code's control.</span></span> <span data-ttu-id="276db-113">Běžné konstrukce `lock (this)`, `lock (typeof (MyType))`, a `lock ("myLock")` porušují tyto obecné zásady:</span><span class="sxs-lookup"><span data-stu-id="276db-113">The common constructs `lock (this)`, `lock (typeof (MyType))`, and `lock ("myLock")` violate this guideline:</span></span>  
  
-   <span data-ttu-id="276db-114">`lock (this)` problém je, pokud instance je přístupná veřejně.</span><span class="sxs-lookup"><span data-stu-id="276db-114">`lock (this)` is a problem if the instance can be accessed publicly.</span></span>  
  
-   <span data-ttu-id="276db-115">`lock (typeof (MyType))` Pokud je problém `MyType` veřejně přístupný.</span><span class="sxs-lookup"><span data-stu-id="276db-115">`lock (typeof (MyType))` is a problem if `MyType` is publicly accessible.</span></span>  
  
-   <span data-ttu-id="276db-116">`lock("myLock")` problém je, protože jiný kód v procesu pomocí jednoho řetězce, budou sdílet stejnou zámek.</span><span class="sxs-lookup"><span data-stu-id="276db-116">`lock("myLock")` is a problem because any other code in the process using the same string, will share the same lock.</span></span>  
  
 <span data-ttu-id="276db-117">Osvědčeným postupem je definovat `private` objekt, který chcete zamknout, nebo `private static` objektová proměnná k ochraně dat, které jsou společné pro všechny instance.</span><span class="sxs-lookup"><span data-stu-id="276db-117">Best practice is to define a `private` object to lock on, or a `private static` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="276db-118">Nelze použít [await](../../../csharp/language-reference/keywords/await.md) – klíčové slovo v textu `lock` příkaz.</span><span class="sxs-lookup"><span data-stu-id="276db-118">You can't use the [await](../../../csharp/language-reference/keywords/await.md) keyword in the body of a `lock` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="276db-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="276db-119">Example</span></span>  
 <span data-ttu-id="276db-120">Následující příklad ukazuje jednoduchý používání vláken bez blokování v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="276db-120">The following sample shows a simple use of threads without locking in C#.</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="276db-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="276db-121">Example</span></span>  
 <span data-ttu-id="276db-122">Následující příklad používá vláken a `lock`.</span><span class="sxs-lookup"><span data-stu-id="276db-122">The following sample uses threads and `lock`.</span></span> <span data-ttu-id="276db-123">Tak dlouho, dokud `lock` příkaz, příkaz blok je důležitý oddíl a `balance` nikdy bude záporné číslo.</span><span class="sxs-lookup"><span data-stu-id="276db-123">As long as the `lock` statement is present, the statement block is a critical section and `balance` will never become a negative number.</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="276db-124">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="276db-124">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="276db-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="276db-125">See Also</span></span>  
 <xref:System.Reflection.MethodImplAttributes>  
 <xref:System.Threading.Mutex>  
 [<span data-ttu-id="276db-126">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="276db-126">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="276db-127">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="276db-127">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="276db-128">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="276db-128">Threading</span></span>](../../programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="276db-129">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="276db-129">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="276db-130">Klíčová slova příkazů</span><span class="sxs-lookup"><span data-stu-id="276db-130">Statement Keywords</span></span>](../../../csharp/language-reference/keywords/statement-keywords.md)  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="276db-131">Propojené operace</span><span class="sxs-lookup"><span data-stu-id="276db-131">Interlocked Operations</span></span>](../../../standard/threading/interlocked-operations.md)  
 [<span data-ttu-id="276db-132">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="276db-132">AutoResetEvent</span></span>](../../../standard/threading/autoresetevent.md)  
 [<span data-ttu-id="276db-133">Synchronizace vláken</span><span class="sxs-lookup"><span data-stu-id="276db-133">Thread Synchronization</span></span>](../../programming-guide/concepts/threading/thread-synchronization.md)
