---
title: Vzory asynchronního programování
description: Přečtěte si o asynchronním vzoru založeném na úlohách (klepněte), asynchronním vzorci založeném na událostech (EAP), & asynchronním programovacím modelu (APM) v rozhraní .NET.
ms.date: 10/16/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
ms.openlocfilehash: bd4d44d8de8a64be82e9ce6af593a86719b59fcf
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84583502"
---
# <a name="asynchronous-programming-patterns"></a><span data-ttu-id="91df3-103">Vzory asynchronního programování</span><span class="sxs-lookup"><span data-stu-id="91df3-103">Asynchronous programming patterns</span></span>

<span data-ttu-id="91df3-104">.NET nabízí tři vzory pro provádění asynchronních operací:</span><span class="sxs-lookup"><span data-stu-id="91df3-104">.NET provides three patterns for performing asynchronous operations:</span></span>  

- <span data-ttu-id="91df3-105">**Asynchronní vzor založený na úlohách (klepněte)**, který používá jedinou metodu představující zahájení a dokončení asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="91df3-105">**Task-based Asynchronous Pattern (TAP)**, which uses a single method to represent the initiation and completion of an asynchronous operation.</span></span> <span data-ttu-id="91df3-106">Klepněte na zavedený .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="91df3-106">TAP was introduced in the .NET Framework 4.</span></span> <span data-ttu-id="91df3-107">**Je to doporučený přístup k asynchronnímu programování v rozhraní .NET.**</span><span class="sxs-lookup"><span data-stu-id="91df3-107">**It's the recommended approach to asynchronous programming in .NET.**</span></span> <span data-ttu-id="91df3-108">Klíčová slova [Async](../../csharp/language-reference/keywords/async.md) a [await](../../csharp/language-reference/operators/await.md) v jazyce C# a operátory [Async](../../visual-basic/language-reference/modifiers/async.md) a [await](../../visual-basic/language-reference/operators/await-operator.md) v Visual Basic přidat jazykovou podporu pro klepněte.</span><span class="sxs-lookup"><span data-stu-id="91df3-108">The [async](../../csharp/language-reference/keywords/async.md) and [await](../../csharp/language-reference/operators/await.md) keywords in C# and the [Async](../../visual-basic/language-reference/modifiers/async.md) and [Await](../../visual-basic/language-reference/operators/await-operator.md) operators in Visual Basic add language support for TAP.</span></span> <span data-ttu-id="91df3-109">Další informace najdete v tématu [asynchronní vzor založený na úlohách (klepněte)](task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="91df3-109">For more information, see [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>  

- <span data-ttu-id="91df3-110">Asynchronní vzor založený na událostech **(EAP)**, což je starší model založený na událostech pro zajištění asynchronního chování.</span><span class="sxs-lookup"><span data-stu-id="91df3-110">**Event-based Asynchronous Pattern (EAP)**, which is the event-based legacy model for providing asynchronous behavior.</span></span> <span data-ttu-id="91df3-111">Vyžaduje metodu, která má `Async` příponu a jednu nebo více událostí, typy delegátů události a `EventArg` odvozené typy.</span><span class="sxs-lookup"><span data-stu-id="91df3-111">It requires a method that has the `Async` suffix and one or more events, event handler delegate types, and `EventArg`-derived types.</span></span> <span data-ttu-id="91df3-112">Protokol EAP byl představený v .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="91df3-112">EAP was introduced in the .NET Framework 2.0.</span></span> <span data-ttu-id="91df3-113">Už se nedoporučuje pro nový vývoj.</span><span class="sxs-lookup"><span data-stu-id="91df3-113">It's no longer recommended for new development.</span></span> <span data-ttu-id="91df3-114">Další informace najdete v tématu [asynchronní vzor založený na událostech (EAP)](event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="91df3-114">For more information, see [Event-based Asynchronous Pattern (EAP)](event-based-asynchronous-pattern-eap.md).</span></span>  

- <span data-ttu-id="91df3-115">Vzor **asynchronního programovacího modelu (APM)** (označuje se také jako <xref:System.IAsyncResult> vzor), což je starší model, který používá <xref:System.IAsyncResult> rozhraní k zajištění asynchronního chování.</span><span class="sxs-lookup"><span data-stu-id="91df3-115">**Asynchronous Programming Model (APM)** pattern (also called the <xref:System.IAsyncResult> pattern), which is the legacy model that uses the <xref:System.IAsyncResult> interface to provide asynchronous behavior.</span></span> <span data-ttu-id="91df3-116">V tomto vzoru vyžadují synchronní operace `Begin` a `End` metody (například `BeginWrite` a `EndWrite` k implementaci asynchronní operace zápisu).</span><span class="sxs-lookup"><span data-stu-id="91df3-116">In this pattern, synchronous operations require `Begin` and `End` methods (for example, `BeginWrite` and `EndWrite` to implement an asynchronous write operation).</span></span> <span data-ttu-id="91df3-117">Tento model se už nedoporučuje pro nový vývoj.</span><span class="sxs-lookup"><span data-stu-id="91df3-117">This pattern is no longer recommended for new development.</span></span> <span data-ttu-id="91df3-118">Další informace najdete v tématu [asynchronní programovací model (APM)](asynchronous-programming-model-apm.md).</span><span class="sxs-lookup"><span data-stu-id="91df3-118">For more information, see [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md).</span></span>  
  
## <a name="comparison-of-patterns"></a><span data-ttu-id="91df3-119">Porovnání vzorů</span><span class="sxs-lookup"><span data-stu-id="91df3-119">Comparison of patterns</span></span>

<span data-ttu-id="91df3-120">Chcete-li rychle porovnat, jak tři vzory modelují asynchronní operace, zvažte `Read` metodu, která načte zadané množství dat do zadané vyrovnávací paměti počínaje zadaným posunem:</span><span class="sxs-lookup"><span data-stu-id="91df3-120">For a quick comparison of how the three patterns model asynchronous operations, consider a `Read` method that reads a specified amount of data into a provided buffer starting at a specified offset:</span></span>  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  

<span data-ttu-id="91df3-121">KLEPNUTÍ na protějšek této metody vystaví následující jedinou `ReadAsync` metodu:</span><span class="sxs-lookup"><span data-stu-id="91df3-121">The TAP counterpart of this method would expose the following single `ReadAsync` method:</span></span>  
  
```csharp
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```

<span data-ttu-id="91df3-122">Protějšek protokolu EAP vystaví následující sadu typů a členů:</span><span class="sxs-lookup"><span data-stu-id="91df3-122">The EAP counterpart would expose the following set of types and members:</span></span>  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
<span data-ttu-id="91df3-123">Protějšek APM by vystavoval `BeginRead` `EndRead` metody a:</span><span class="sxs-lookup"><span data-stu-id="91df3-123">The APM counterpart would expose the `BeginRead` and `EndRead` methods:</span></span>  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  

## <a name="see-also"></a><span data-ttu-id="91df3-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="91df3-124">See also</span></span>

- [<span data-ttu-id="91df3-125">Asynchronní v hloubkě</span><span class="sxs-lookup"><span data-stu-id="91df3-125">Async in depth</span></span>](../async-in-depth.md)
- [<span data-ttu-id="91df3-126">Asynchronní programování v jazyce C #</span><span class="sxs-lookup"><span data-stu-id="91df3-126">Asynchronous programming in C#</span></span>](../../csharp/async.md)
- [<span data-ttu-id="91df3-127">Asynchronní programování v F #</span><span class="sxs-lookup"><span data-stu-id="91df3-127">Async Programming in F#</span></span>](../../fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [<span data-ttu-id="91df3-128">Asynchronní programování s modifikátorem Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91df3-128">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/async/index.md)
