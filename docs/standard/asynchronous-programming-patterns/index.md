---
title: Vzory asynchronního programování
ms.date: 10/16/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50d76aef201fead37923a65cfeead16638b09842
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62031171"
---
# <a name="asynchronous-programming-patterns"></a><span data-ttu-id="f7b40-102">Vzory asynchronního programování</span><span class="sxs-lookup"><span data-stu-id="f7b40-102">Asynchronous programming patterns</span></span>

<span data-ttu-id="f7b40-103">.NET poskytuje tři vzory pro provádění asynchronních operací:</span><span class="sxs-lookup"><span data-stu-id="f7b40-103">.NET provides three patterns for performing asynchronous operations:</span></span>  

- <span data-ttu-id="f7b40-104">**Založený na úlohách asynchronního vzoru (TAP)**, který používá jedinou metodu k reprezentaci zahájení a dokončení asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="f7b40-104">**Task-based Asynchronous Pattern (TAP)**, which uses a single method to represent the initiation and completion of an asynchronous operation.</span></span> <span data-ttu-id="f7b40-105">Klepněte na byla zavedena v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f7b40-105">TAP was introduced in the .NET Framework 4.</span></span> <span data-ttu-id="f7b40-106">**Je doporučený postup pro asynchronní programování v rozhraní .NET.**</span><span class="sxs-lookup"><span data-stu-id="f7b40-106">**It's the recommended approach to asynchronous programming in .NET.**</span></span> <span data-ttu-id="f7b40-107">[Asynchronní](~/docs/csharp/language-reference/keywords/async.md) a [await](~/docs/csharp/language-reference/keywords/await.md) klíčových slov v C# a [asynchronní](~/docs/visual-basic/language-reference/modifiers/async.md) a [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) operátory v jazyce Visual Basic přidejte jazyková podpora v nástroji TAP.</span><span class="sxs-lookup"><span data-stu-id="f7b40-107">The [async](~/docs/csharp/language-reference/keywords/async.md) and [await](~/docs/csharp/language-reference/keywords/await.md) keywords in C# and the [Async](~/docs/visual-basic/language-reference/modifiers/async.md) and [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) operators in Visual Basic add language support for TAP.</span></span> <span data-ttu-id="f7b40-108">Další informace najdete v tématu [úkolově orientovanou asynchronní vzor (TAP)](task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="f7b40-108">For more information, see [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>  

- <span data-ttu-id="f7b40-109">**Událost asynchronní vzor založený (EAP)**, který je založený na událostech starší model pro poskytování asynchronní chování.</span><span class="sxs-lookup"><span data-stu-id="f7b40-109">**Event-based Asynchronous Pattern (EAP)**, which is the event-based legacy model for providing asynchronous behavior.</span></span> <span data-ttu-id="f7b40-110">Vyžaduje metodu, která má `Async` příponu a jeden nebo více událostí, typy delegátu obslužné rutiny událostí, a `EventArg`-odvozené typy.</span><span class="sxs-lookup"><span data-stu-id="f7b40-110">It requires a method that has the `Async` suffix and one or more events, event handler delegate types, and `EventArg`-derived types.</span></span> <span data-ttu-id="f7b40-111">EAP byla zavedena v rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="f7b40-111">EAP was introduced in the .NET Framework 2.0.</span></span> <span data-ttu-id="f7b40-112">Doporučuje se už pro vývoj nových projektů.</span><span class="sxs-lookup"><span data-stu-id="f7b40-112">It's no longer recommended for new development.</span></span> <span data-ttu-id="f7b40-113">Další informace najdete v tématu [události asynchronní vzor založený (EAP)](event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="f7b40-113">For more information, see [Event-based Asynchronous Pattern (EAP)](event-based-asynchronous-pattern-eap.md).</span></span>  

- <span data-ttu-id="f7b40-114">**Asynchronního programovacího modelu (APM)** vzor (také nazývané <xref:System.IAsyncResult> vzor), která je starší verze modelu, který používá <xref:System.IAsyncResult> rozhraní k poskytování asynchronní chování.</span><span class="sxs-lookup"><span data-stu-id="f7b40-114">**Asynchronous Programming Model (APM)** pattern (also called the <xref:System.IAsyncResult> pattern), which is the legacy model that uses the <xref:System.IAsyncResult> interface to provide asynchronous behavior.</span></span> <span data-ttu-id="f7b40-115">V tomto vzoru synchronní operace vyžadují `Begin` a `End` metod (například `BeginWrite` a `EndWrite` implementace operace asynchronní zápis).</span><span class="sxs-lookup"><span data-stu-id="f7b40-115">In this pattern, synchronous operations require `Begin` and `End` methods (for example, `BeginWrite` and `EndWrite` to implement an asynchronous write operation).</span></span> <span data-ttu-id="f7b40-116">Tento model už se nedoporučuje pro vývoj nových projektů.</span><span class="sxs-lookup"><span data-stu-id="f7b40-116">This pattern is no longer recommended for new development.</span></span> <span data-ttu-id="f7b40-117">Další informace najdete v tématu [asynchronního programovacího modelu (APM)](asynchronous-programming-model-apm.md).</span><span class="sxs-lookup"><span data-stu-id="f7b40-117">For more information, see [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md).</span></span>  
  
## <a name="comparison-of-patterns"></a><span data-ttu-id="f7b40-118">Porovnávání vzorů</span><span class="sxs-lookup"><span data-stu-id="f7b40-118">Comparison of patterns</span></span>

<span data-ttu-id="f7b40-119">Rychlé porovnání jak tři vzory modelu asynchronních operací, vezměte v úvahu `Read` metodu, která načte zadaného množství dat do zadané vyrovnávací paměti, počínaje od určeného posunutí:</span><span class="sxs-lookup"><span data-stu-id="f7b40-119">For a quick comparison of how the three patterns model asynchronous operations, consider a `Read` method that reads a specified amount of data into a provided buffer starting at a specified offset:</span></span>  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  

<span data-ttu-id="f7b40-120">TAP protějšek této metody by vystavovat následující jedním `ReadAsync` metody:</span><span class="sxs-lookup"><span data-stu-id="f7b40-120">The TAP counterpart of this method would expose the following single `ReadAsync` method:</span></span>  
  
```csharp
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```

<span data-ttu-id="f7b40-121">Následující sada typů a členů by vystavit protějšek protokolu EAP:</span><span class="sxs-lookup"><span data-stu-id="f7b40-121">The EAP counterpart would expose the following set of types and members:</span></span>  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
<span data-ttu-id="f7b40-122">APM protějšek by vystavit `BeginRead` a `EndRead` metody:</span><span class="sxs-lookup"><span data-stu-id="f7b40-122">The APM counterpart would expose the `BeginRead` and `EndRead` methods:</span></span>  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,   
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  

## <a name="see-also"></a><span data-ttu-id="f7b40-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f7b40-123">See also</span></span>

- [<span data-ttu-id="f7b40-124">Asynchronní do hloubky</span><span class="sxs-lookup"><span data-stu-id="f7b40-124">Async in depth</span></span>](../async-in-depth.md)
- [<span data-ttu-id="f7b40-125">Asynchronní programování v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f7b40-125">Asynchronous programming in C#</span></span>](~/docs/csharp/async.md)
- [<span data-ttu-id="f7b40-126">Asynchronní programování vF#</span><span class="sxs-lookup"><span data-stu-id="f7b40-126">Async Programming in F#</span></span>](~/docs/fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [<span data-ttu-id="f7b40-127">Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7b40-127">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](~/docs/visual-basic/programming-guide/concepts/async/index.md)
