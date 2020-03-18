---
title: Vzory asynchronního programování
ms.date: 10/16/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
ms.openlocfilehash: e1efe9c3eb57f317def91e527506c358eb086679
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160050"
---
# <a name="asynchronous-programming-patterns"></a><span data-ttu-id="6d3ad-102">Vzory asynchronního programování</span><span class="sxs-lookup"><span data-stu-id="6d3ad-102">Asynchronous programming patterns</span></span>

<span data-ttu-id="6d3ad-103">Rozhraní .NET poskytuje tři vzory pro provádění asynchronních operací:</span><span class="sxs-lookup"><span data-stu-id="6d3ad-103">.NET provides three patterns for performing asynchronous operations:</span></span>  

- <span data-ttu-id="6d3ad-104">**Asynchronní vzor založený na úlohách (TAP),** který používá jednu metodu k reprezentaci zahájení a dokončení asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="6d3ad-104">**Task-based Asynchronous Pattern (TAP)**, which uses a single method to represent the initiation and completion of an asynchronous operation.</span></span> <span data-ttu-id="6d3ad-105">Tap byl zaveden v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="6d3ad-105">TAP was introduced in the .NET Framework 4.</span></span> <span data-ttu-id="6d3ad-106">**Je to doporučený přístup k asynchronnímu programování v rozhraní .NET.**</span><span class="sxs-lookup"><span data-stu-id="6d3ad-106">**It's the recommended approach to asynchronous programming in .NET.**</span></span> <span data-ttu-id="6d3ad-107">[Asynchronní](../../csharp/language-reference/keywords/async.md) a [čekat](../../csharp/language-reference/operators/await.md) klíčová slova v jazyce C# a [Async](../../visual-basic/language-reference/modifiers/async.md) a [Await](../../visual-basic/language-reference/operators/await-operator.md) operátory v jazyce Visual Basic přidat jazykovou podporu pro TAP.</span><span class="sxs-lookup"><span data-stu-id="6d3ad-107">The [async](../../csharp/language-reference/keywords/async.md) and [await](../../csharp/language-reference/operators/await.md) keywords in C# and the [Async](../../visual-basic/language-reference/modifiers/async.md) and [Await](../../visual-basic/language-reference/operators/await-operator.md) operators in Visual Basic add language support for TAP.</span></span> <span data-ttu-id="6d3ad-108">Další informace naleznete [v tématu Asynchronní vzor založený na úlohách (TAP).](task-based-asynchronous-pattern-tap.md)</span><span class="sxs-lookup"><span data-stu-id="6d3ad-108">For more information, see [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>  

- <span data-ttu-id="6d3ad-109">**Asynchronní vzor založený na událostech (EAP),** což je starší model založený na událostech pro poskytování asynchronního chování.</span><span class="sxs-lookup"><span data-stu-id="6d3ad-109">**Event-based Asynchronous Pattern (EAP)**, which is the event-based legacy model for providing asynchronous behavior.</span></span> <span data-ttu-id="6d3ad-110">Vyžaduje metodu, která `Async` má příponu a jednu nebo více `EventArg`událostí, typy delegátů obslužné rutiny událostí a odvozené typy.</span><span class="sxs-lookup"><span data-stu-id="6d3ad-110">It requires a method that has the `Async` suffix and one or more events, event handler delegate types, and `EventArg`-derived types.</span></span> <span data-ttu-id="6d3ad-111">EAP byl zaveden v rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="6d3ad-111">EAP was introduced in the .NET Framework 2.0.</span></span> <span data-ttu-id="6d3ad-112">Již se nedoporučuje pro nový vývoj.</span><span class="sxs-lookup"><span data-stu-id="6d3ad-112">It's no longer recommended for new development.</span></span> <span data-ttu-id="6d3ad-113">Další informace naleznete [v tématu Asynchronní vzor založený na událostech (EAP).](event-based-asynchronous-pattern-eap.md)</span><span class="sxs-lookup"><span data-stu-id="6d3ad-113">For more information, see [Event-based Asynchronous Pattern (EAP)](event-based-asynchronous-pattern-eap.md).</span></span>  

- <span data-ttu-id="6d3ad-114">**Vzor asynchronního programovacího modelu (APM)** (nazývaný také <xref:System.IAsyncResult> vzor), <xref:System.IAsyncResult> což je starší model, který používá rozhraní k zajištění asynchronního chování.</span><span class="sxs-lookup"><span data-stu-id="6d3ad-114">**Asynchronous Programming Model (APM)** pattern (also called the <xref:System.IAsyncResult> pattern), which is the legacy model that uses the <xref:System.IAsyncResult> interface to provide asynchronous behavior.</span></span> <span data-ttu-id="6d3ad-115">V tomto vzoru `Begin` vyžadují synchronní `End` operace a `BeginWrite` metody `EndWrite` (například a implementovat operaci asynchronního zápisu).</span><span class="sxs-lookup"><span data-stu-id="6d3ad-115">In this pattern, synchronous operations require `Begin` and `End` methods (for example, `BeginWrite` and `EndWrite` to implement an asynchronous write operation).</span></span> <span data-ttu-id="6d3ad-116">Tento vzor se již nedoporučuje pro nový vývoj.</span><span class="sxs-lookup"><span data-stu-id="6d3ad-116">This pattern is no longer recommended for new development.</span></span> <span data-ttu-id="6d3ad-117">Další informace naleznete [v tématu Asynchronní programovací model (APM)](asynchronous-programming-model-apm.md).</span><span class="sxs-lookup"><span data-stu-id="6d3ad-117">For more information, see [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md).</span></span>  
  
## <a name="comparison-of-patterns"></a><span data-ttu-id="6d3ad-118">Porovnání vzorů</span><span class="sxs-lookup"><span data-stu-id="6d3ad-118">Comparison of patterns</span></span>

<span data-ttu-id="6d3ad-119">Pro rychlé porovnání, jak tři vzory model asynchronní `Read` operace, zvažte metodu, která čte zadané množství dat do zadané vyrovnávací paměti začíná na zadaný posun:</span><span class="sxs-lookup"><span data-stu-id="6d3ad-119">For a quick comparison of how the three patterns model asynchronous operations, consider a `Read` method that reads a specified amount of data into a provided buffer starting at a specified offset:</span></span>  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  

<span data-ttu-id="6d3ad-120">Protějšek TAP této metody by `ReadAsync` vystavit následující jednu metodu:</span><span class="sxs-lookup"><span data-stu-id="6d3ad-120">The TAP counterpart of this method would expose the following single `ReadAsync` method:</span></span>  
  
```csharp
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```

<span data-ttu-id="6d3ad-121">Protějšek EAP by vystavit následující sadu typů a členů:</span><span class="sxs-lookup"><span data-stu-id="6d3ad-121">The EAP counterpart would expose the following set of types and members:</span></span>  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
<span data-ttu-id="6d3ad-122">Protějšek APM by `BeginRead` `EndRead` vystavit a metody:</span><span class="sxs-lookup"><span data-stu-id="6d3ad-122">The APM counterpart would expose the `BeginRead` and `EndRead` methods:</span></span>  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  

## <a name="see-also"></a><span data-ttu-id="6d3ad-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d3ad-123">See also</span></span>

- [<span data-ttu-id="6d3ad-124">Asynchronní do hloubky</span><span class="sxs-lookup"><span data-stu-id="6d3ad-124">Async in depth</span></span>](../async-in-depth.md)
- [<span data-ttu-id="6d3ad-125">Asynchronní programování v C #</span><span class="sxs-lookup"><span data-stu-id="6d3ad-125">Asynchronous programming in C#</span></span>](../../csharp/async.md)
- [<span data-ttu-id="6d3ad-126">Asynchronní programování ve F #</span><span class="sxs-lookup"><span data-stu-id="6d3ad-126">Async Programming in F#</span></span>](../../fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [<span data-ttu-id="6d3ad-127">Asynchronní programování s asynchronní a čeká (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d3ad-127">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/async/index.md)
