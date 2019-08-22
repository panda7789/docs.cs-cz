---
title: Vzorce asynchronního programování
ms.date: 10/16/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e3535e2979d2430fcb434a578f94d8d5b3925631
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666569"
---
# <a name="asynchronous-programming-patterns"></a><span data-ttu-id="dd259-102">Vzorce asynchronního programování</span><span class="sxs-lookup"><span data-stu-id="dd259-102">Asynchronous programming patterns</span></span>

<span data-ttu-id="dd259-103">.NET nabízí tři vzory pro provádění asynchronních operací:</span><span class="sxs-lookup"><span data-stu-id="dd259-103">.NET provides three patterns for performing asynchronous operations:</span></span>  

- <span data-ttu-id="dd259-104">**Asynchronní vzor založený na úlohách (klepněte)** , který používá jedinou metodu představující zahájení a dokončení asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="dd259-104">**Task-based Asynchronous Pattern (TAP)**, which uses a single method to represent the initiation and completion of an asynchronous operation.</span></span> <span data-ttu-id="dd259-105">Klepněte na zavedený .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="dd259-105">TAP was introduced in the .NET Framework 4.</span></span> <span data-ttu-id="dd259-106">**Je to doporučený přístup k asynchronnímu programování v rozhraní .NET.**</span><span class="sxs-lookup"><span data-stu-id="dd259-106">**It's the recommended approach to asynchronous programming in .NET.**</span></span> <span data-ttu-id="dd259-107">Klíčová slova [](../../csharp/language-reference/keywords/await.md) [Async](../../csharp/language-reference/keywords/async.md) a await C# v a operátory [Async](../../visual-basic/language-reference/modifiers/async.md) a [await](../../visual-basic/language-reference/operators/await-operator.md) v Visual Basic přidat jazykovou podporu pro klepněte.</span><span class="sxs-lookup"><span data-stu-id="dd259-107">The [async](../../csharp/language-reference/keywords/async.md) and [await](../../csharp/language-reference/keywords/await.md) keywords in C# and the [Async](../../visual-basic/language-reference/modifiers/async.md) and [Await](../../visual-basic/language-reference/operators/await-operator.md) operators in Visual Basic add language support for TAP.</span></span> <span data-ttu-id="dd259-108">Další informace najdete v tématu [asynchronní vzor založený na úlohách (klepněte)](task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="dd259-108">For more information, see [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>  

- <span data-ttu-id="dd259-109">Asynchronní vzor založený na událostech **(EAP)** , což je starší model založený na událostech pro zajištění asynchronního chování.</span><span class="sxs-lookup"><span data-stu-id="dd259-109">**Event-based Asynchronous Pattern (EAP)**, which is the event-based legacy model for providing asynchronous behavior.</span></span> <span data-ttu-id="dd259-110">Vyžaduje metodu, která má `Async` příponu a jednu nebo více událostí, typy delegátů události a `EventArg`odvozené typy.</span><span class="sxs-lookup"><span data-stu-id="dd259-110">It requires a method that has the `Async` suffix and one or more events, event handler delegate types, and `EventArg`-derived types.</span></span> <span data-ttu-id="dd259-111">Protokol EAP byl představený v .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="dd259-111">EAP was introduced in the .NET Framework 2.0.</span></span> <span data-ttu-id="dd259-112">Už se nedoporučuje pro nový vývoj.</span><span class="sxs-lookup"><span data-stu-id="dd259-112">It's no longer recommended for new development.</span></span> <span data-ttu-id="dd259-113">Další informace najdete v tématu [asynchronní vzor založený na událostech (EAP)](event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="dd259-113">For more information, see [Event-based Asynchronous Pattern (EAP)](event-based-asynchronous-pattern-eap.md).</span></span>  

- <span data-ttu-id="dd259-114">Vzor **asynchronního programovacího modelu (APM)** (označuje <xref:System.IAsyncResult> se také jako vzor), což je starší <xref:System.IAsyncResult> model, který používá rozhraní k zajištění asynchronního chování.</span><span class="sxs-lookup"><span data-stu-id="dd259-114">**Asynchronous Programming Model (APM)** pattern (also called the <xref:System.IAsyncResult> pattern), which is the legacy model that uses the <xref:System.IAsyncResult> interface to provide asynchronous behavior.</span></span> <span data-ttu-id="dd259-115">`Begin` V tomto vzoru vyžadují synchronní operace a `End` `BeginWrite` metody (například a `EndWrite` k implementaci asynchronní operace zápisu).</span><span class="sxs-lookup"><span data-stu-id="dd259-115">In this pattern, synchronous operations require `Begin` and `End` methods (for example, `BeginWrite` and `EndWrite` to implement an asynchronous write operation).</span></span> <span data-ttu-id="dd259-116">Tento model se už nedoporučuje pro nový vývoj.</span><span class="sxs-lookup"><span data-stu-id="dd259-116">This pattern is no longer recommended for new development.</span></span> <span data-ttu-id="dd259-117">Další informace najdete v tématu [asynchronní programovací model (APM)](asynchronous-programming-model-apm.md).</span><span class="sxs-lookup"><span data-stu-id="dd259-117">For more information, see [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md).</span></span>  
  
## <a name="comparison-of-patterns"></a><span data-ttu-id="dd259-118">Porovnání vzorů</span><span class="sxs-lookup"><span data-stu-id="dd259-118">Comparison of patterns</span></span>

<span data-ttu-id="dd259-119">Chcete-li rychle porovnat, jak tři vzory modelují asynchronní operace, zvažte `Read` metodu, která načte zadané množství dat do zadané vyrovnávací paměti počínaje zadaným posunem:</span><span class="sxs-lookup"><span data-stu-id="dd259-119">For a quick comparison of how the three patterns model asynchronous operations, consider a `Read` method that reads a specified amount of data into a provided buffer starting at a specified offset:</span></span>  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  

<span data-ttu-id="dd259-120">Klepnutí na protějšek této metody vystaví následující jedinou `ReadAsync` metodu:</span><span class="sxs-lookup"><span data-stu-id="dd259-120">The TAP counterpart of this method would expose the following single `ReadAsync` method:</span></span>  
  
```csharp
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```

<span data-ttu-id="dd259-121">Protějšek protokolu EAP vystaví následující sadu typů a členů:</span><span class="sxs-lookup"><span data-stu-id="dd259-121">The EAP counterpart would expose the following set of types and members:</span></span>  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
<span data-ttu-id="dd259-122">Protějšek APM by vystavoval `BeginRead` metody `EndRead` a:</span><span class="sxs-lookup"><span data-stu-id="dd259-122">The APM counterpart would expose the `BeginRead` and `EndRead` methods:</span></span>  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,   
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  

## <a name="see-also"></a><span data-ttu-id="dd259-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dd259-123">See also</span></span>

- [<span data-ttu-id="dd259-124">Asynchronní v hloubkě</span><span class="sxs-lookup"><span data-stu-id="dd259-124">Async in depth</span></span>](../async-in-depth.md)
- [<span data-ttu-id="dd259-125">Asynchronní programování vC#</span><span class="sxs-lookup"><span data-stu-id="dd259-125">Asynchronous programming in C#</span></span>](../../csharp/async.md)
- [<span data-ttu-id="dd259-126">Asynchronní programování vF#</span><span class="sxs-lookup"><span data-stu-id="dd259-126">Async Programming in F#</span></span>](../../fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [<span data-ttu-id="dd259-127">Asynchronní programování s modifikátorem Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd259-127">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/async/index.md)
