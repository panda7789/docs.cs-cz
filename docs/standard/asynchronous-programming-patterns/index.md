---
title: Vzory asynchronního programování
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET Framework
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e399a512d2bee636aec35e008c0632ce9c5fa781
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/09/2018
ms.locfileid: "44249033"
---
# <a name="asynchronous-programming-patterns"></a><span data-ttu-id="6e873-102">Vzory asynchronního programování</span><span class="sxs-lookup"><span data-stu-id="6e873-102">Asynchronous Programming Patterns</span></span>

<span data-ttu-id="6e873-103">Rozhraní .NET Framework poskytuje tři vzory pro provádění asynchronních operací:</span><span class="sxs-lookup"><span data-stu-id="6e873-103">The .NET Framework provides three patterns for performing asynchronous operations:</span></span>  
  
- <span data-ttu-id="6e873-104">**Asynchronní Programovací Model (APM)** vzor (také nazývané <xref:System.IAsyncResult> vzor), kde asynchronní operace vyžadují `Begin` a `End` metody (například `BeginWrite` a `EndWrite` pro asynchronní operace zápisu).</span><span class="sxs-lookup"><span data-stu-id="6e873-104">**Asynchronous Programming Model (APM)** pattern (also called the <xref:System.IAsyncResult> pattern), where asynchronous operations require `Begin` and `End` methods (for example, `BeginWrite` and `EndWrite` for asynchronous write operations).</span></span> <span data-ttu-id="6e873-105">Tento model už se nedoporučuje pro vývoj nových projektů.</span><span class="sxs-lookup"><span data-stu-id="6e873-105">This pattern is no longer recommended for new development.</span></span> <span data-ttu-id="6e873-106">Další informace najdete v tématu [asynchronního programovacího modelu (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md).</span><span class="sxs-lookup"><span data-stu-id="6e873-106">For more information, see [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md).</span></span>  
  
- <span data-ttu-id="6e873-107">**Událost asynchronní vzor založený (EAP)**, což vyžaduje metodu, která má `Async` příponu a také vyžaduje jeden nebo více událostí, typy delegátu obslužné rutiny událostí, a `EventArg`-odvozené typy.</span><span class="sxs-lookup"><span data-stu-id="6e873-107">**Event-based Asynchronous Pattern (EAP)**, which requires a method that has the `Async` suffix, and also requires one or more events, event handler delegate types, and `EventArg`-derived types.</span></span> <span data-ttu-id="6e873-108">EAP byla zavedena v rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="6e873-108">EAP was introduced in the .NET Framework 2.0.</span></span> <span data-ttu-id="6e873-109">Doporučuje se už pro vývoj nových projektů.</span><span class="sxs-lookup"><span data-stu-id="6e873-109">It is no longer recommended for new development.</span></span> <span data-ttu-id="6e873-110">Další informace najdete v tématu [události asynchronní vzor založený (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="6e873-110">For more information, see [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span></span>  
  
- <span data-ttu-id="6e873-111">**Založený na úlohách asynchronního vzoru (TAP)**, který používá jedinou metodu k reprezentaci zahájení a dokončení asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="6e873-111">**Task-based Asynchronous Pattern (TAP)**, which uses a single method to represent the initiation and completion of an asynchronous operation.</span></span> <span data-ttu-id="6e873-112">Klepněte na byla zavedena v rozhraní .NET Framework 4 a je doporučený postup pro asynchronní programování v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6e873-112">TAP was introduced in the .NET Framework 4 and is the recommended approach to asynchronous programming in the .NET Framework.</span></span> <span data-ttu-id="6e873-113">[Asynchronní](~/docs/csharp/language-reference/keywords/async.md) a [await](~/docs/csharp/language-reference/keywords/await.md) klíčová slova v jazyce C# a [asynchronní](~/docs/visual-basic/language-reference/modifiers/async.md) a [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) operátory v jazyce Visual Basic přidejte jazyková podpora v nástroji TAP.</span><span class="sxs-lookup"><span data-stu-id="6e873-113">The [async](~/docs/csharp/language-reference/keywords/async.md) and [await](~/docs/csharp/language-reference/keywords/await.md) keywords in C# and the [Async](~/docs/visual-basic/language-reference/modifiers/async.md) and [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) operators in Visual Basic Language add language support for TAP.</span></span> <span data-ttu-id="6e873-114">Další informace najdete v tématu [úkolově orientovanou asynchronní vzor (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="6e873-114">For more information, see [Task-based Asynchronous Pattern (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span></span>  
  
## <a name="comparing-patterns"></a><span data-ttu-id="6e873-115">Porovnávání vzorů</span><span class="sxs-lookup"><span data-stu-id="6e873-115">Comparing Patterns</span></span>  

<span data-ttu-id="6e873-116">Rychlé porovnání jak tři vzory modelu asynchronních operací, vezměte v úvahu `Read` metodu, která načte zadaného množství dat do zadané vyrovnávací paměti, počínaje od určeného posunutí:</span><span class="sxs-lookup"><span data-stu-id="6e873-116">For a quick comparison of how the three patterns model asynchronous operations, consider a `Read` method that reads a specified amount of data into a provided buffer starting at a specified offset:</span></span>  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  
  
<span data-ttu-id="6e873-117">APM protějšek této metody by vystavit `BeginRead` a `EndRead` metody:</span><span class="sxs-lookup"><span data-stu-id="6e873-117">The APM counterpart of this method would expose the `BeginRead` and `EndRead` methods:</span></span>  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,   
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  
  
<span data-ttu-id="6e873-118">Následující sada typů a členů by vystavit protějšek protokolu EAP:</span><span class="sxs-lookup"><span data-stu-id="6e873-118">The EAP counterpart would expose the following set of types and members:</span></span>  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
<span data-ttu-id="6e873-119">Protějšek TAP by vystavovat následující jedním `ReadAsync` metody:</span><span class="sxs-lookup"><span data-stu-id="6e873-119">The TAP counterpart would expose the following single `ReadAsync` method:</span></span>  
  
```csharp  
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```  
  
<span data-ttu-id="6e873-120">Komplexní informace o protokolu EAP, klepněte na a APM najdete v článku odkazů uvedených v následující části.</span><span class="sxs-lookup"><span data-stu-id="6e873-120">For a comprehensive discussion of TAP, APM, and EAP, see the links provided in the next section.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="6e873-121">Související témata</span><span class="sxs-lookup"><span data-stu-id="6e873-121">Related topics</span></span>

| <span data-ttu-id="6e873-122">Název</span><span class="sxs-lookup"><span data-stu-id="6e873-122">Title</span></span> | <span data-ttu-id="6e873-123">Popis</span><span class="sxs-lookup"><span data-stu-id="6e873-123">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="6e873-124">Model asynchronního programování (APM)</span><span class="sxs-lookup"><span data-stu-id="6e873-124">Asynchronous Programming Model (APM)</span></span>](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) | <span data-ttu-id="6e873-125">Popisuje starší verzi modelu, který používá <xref:System.IAsyncResult> rozhraní k poskytování asynchronní chování.</span><span class="sxs-lookup"><span data-stu-id="6e873-125">Describes the legacy model that uses the <xref:System.IAsyncResult> interface to provide asynchronous behavior.</span></span> <span data-ttu-id="6e873-126">Tento model už se nedoporučuje pro vývoj nových projektů.</span><span class="sxs-lookup"><span data-stu-id="6e873-126">This model is no longer recommended for new development.</span></span> |
| [<span data-ttu-id="6e873-127">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="6e873-127">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) | <span data-ttu-id="6e873-128">Popisuje starší model pro poskytování asynchronní chování založený na událostech.</span><span class="sxs-lookup"><span data-stu-id="6e873-128">Describes the event-based legacy model for providing asynchronous behavior.</span></span> <span data-ttu-id="6e873-129">Tento model už se nedoporučuje pro vývoj nových projektů.</span><span class="sxs-lookup"><span data-stu-id="6e873-129">This model is no longer recommended for new development.</span></span> |
| [<span data-ttu-id="6e873-130">Asynchronní vzor založený na úlohách (TAP)</span><span class="sxs-lookup"><span data-stu-id="6e873-130">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) | <span data-ttu-id="6e873-131">Popisuje nový asynchronní vzor založený na <xref:System.Threading.Tasks> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6e873-131">Describes the new asynchronous pattern based on the <xref:System.Threading.Tasks> namespace.</span></span> <span data-ttu-id="6e873-132">Tento model je doporučený postup pro asynchronní programování v rozhraní .NET Framework 4 a novější verze.</span><span class="sxs-lookup"><span data-stu-id="6e873-132">This model is the recommended approach to asynchronous programming in the .NET Framework 4 and later versions.</span></span> |

## <a name="see-also"></a><span data-ttu-id="6e873-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e873-133">See also</span></span>

- [<span data-ttu-id="6e873-134">Asynchronní programování v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6e873-134">Asynchronous programming in C#</span></span>](~/docs/csharp/async.md)   
- [<span data-ttu-id="6e873-135">Asynchronní programování v jazyce F #</span><span class="sxs-lookup"><span data-stu-id="6e873-135">Async Programming in F#</span></span>](~/docs/fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)   
- [<span data-ttu-id="6e873-136">Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e873-136">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](~/docs/visual-basic/programming-guide/concepts/async/index.md)
