---
title: Použití objektů implementujících rozhraní IDisposable
ms.date: 04/07/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25c5ffa89e6ce4e589b8f12a7b8518272426c9e9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597790"
---
# <a name="using-objects-that-implement-idisposable"></a><span data-ttu-id="fd368-102">Použití objektů implementujících rozhraní IDisposable</span><span class="sxs-lookup"><span data-stu-id="fd368-102">Using objects that implement IDisposable</span></span>

<span data-ttu-id="fd368-103">Modul common language runtime systému uvolňování paměti uvolní paměť používanou spravovanými objekty, ale implementace typy, které používají nespravované prostředky <xref:System.IDisposable> rozhraní umožňující je paměť přidělená pro tyto nespravované prostředky, které mají být získány zpět.</span><span class="sxs-lookup"><span data-stu-id="fd368-103">The common language runtime's garbage collector reclaims the memory used by managed objects, but types that use unmanaged resources implement the <xref:System.IDisposable> interface to allow the memory allocated to these unmanaged resources to be reclaimed.</span></span> <span data-ttu-id="fd368-104">Jakmile ukončíte používání objektu, který implementuje <xref:System.IDisposable>, měli byste zavolat objekt <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementace.</span><span class="sxs-lookup"><span data-stu-id="fd368-104">When you finish using an object that implements <xref:System.IDisposable>, you should call the object's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="fd368-105">Toto lze provést jedním ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="fd368-105">You can do this in one of two ways:</span></span>  
  
* <span data-ttu-id="fd368-106">V jazyce C# `using` příkazu nebo Visual Basic `Using` příkazu.</span><span class="sxs-lookup"><span data-stu-id="fd368-106">With the C# `using` statement or the Visual Basic `Using` statement.</span></span>  
  
* <span data-ttu-id="fd368-107">Implementací `try/finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="fd368-107">By implementing a `try/finally` block.</span></span>  

## <a name="the-using-statement"></a><span data-ttu-id="fd368-108">Pomocí příkazu using</span><span class="sxs-lookup"><span data-stu-id="fd368-108">The using statement</span></span>

<span data-ttu-id="fd368-109">`using` Příkaz v jazyce C# a `Using` v sadě Visual Studio zjednodušuje kód, který je třeba zapsat k vytvoření a vyčištění objektu.</span><span class="sxs-lookup"><span data-stu-id="fd368-109">The `using` statement in C# and the `Using` statement in Visual Basic simplify the code that you must write to create and clean up an object.</span></span> <span data-ttu-id="fd368-110">`using` Příkaz získá jeden nebo více zdrojů, provede zadané příkazy a automaticky uvolní objekt.</span><span class="sxs-lookup"><span data-stu-id="fd368-110">The `using` statement obtains one or more resources, executes the statements that you specify, and automatically disposes of the object.</span></span> <span data-ttu-id="fd368-111">Ale `using` příkazu je platný pouze pro objekty, které se používají v rámci oboru metody, ve kterém jsou vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="fd368-111">However, the `using` statement is useful only for objects that are used within the scope of the method in which they are constructed.</span></span>  
  
<span data-ttu-id="fd368-112">V následujícím příkladu `using` příkazu k vytvoření a vydání <xref:System.IO.StreamReader?displayProperty=nameWithType> objektu.</span><span class="sxs-lookup"><span data-stu-id="fd368-112">The following example uses the `using` statement to create and release a <xref:System.IO.StreamReader?displayProperty=nameWithType> object.</span></span>  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
<span data-ttu-id="fd368-113">Všimněte si, že i když <xref:System.IO.StreamReader> implementuje třída <xref:System.IDisposable> rozhraní, což znamená, že používá nespravovaný prostředek, příklad nevolá explicitně <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="fd368-113">Note that although the <xref:System.IO.StreamReader> class implements the <xref:System.IDisposable> interface, which indicates that it uses an unmanaged resource, the example doesn't explicitly call the <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fd368-114">Když kompilátor jazyka C# nebo Visual Basic narazí `using` prohlášení, vysílá zprostředkující jazyk (IL), který je ekvivalentní následujícímu kódu, který explicitně obsahuje `try/finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="fd368-114">When the C# or Visual Basic compiler encounters the `using` statement, it emits intermediate language (IL) that is equivalent to the following code that explicitly contains a `try/finally` block.</span></span>  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
<span data-ttu-id="fd368-115">C# `using` příkaz také umožňuje získat více zdrojů v jediném příkazu, který je interním ekvivalentem vnořených `using` příkazy.</span><span class="sxs-lookup"><span data-stu-id="fd368-115">The C# `using` statement also allows you to acquire multiple resources in a single statement, which is internally equivalent to nested `using` statements.</span></span> <span data-ttu-id="fd368-116">Následující příklad vytvoří dvě <xref:System.IO.StreamReader> objekty ke čtení obsahu dvou různých souborech.</span><span class="sxs-lookup"><span data-stu-id="fd368-116">The following example instantiates two <xref:System.IO.StreamReader> objects to read the contents of two different files.</span></span>  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a><span data-ttu-id="fd368-117">Testovací blok / bezpodmínečný blok</span><span class="sxs-lookup"><span data-stu-id="fd368-117">Try/finally block</span></span>

<span data-ttu-id="fd368-118">Namísto obtékání `try/finally` blokovat `using` příkazu, můžete se rozhodnout k implementaci `try/finally` blokovat přímo.</span><span class="sxs-lookup"><span data-stu-id="fd368-118">Instead of wrapping a `try/finally` block in a `using` statement, you may choose to implement the `try/finally` block directly.</span></span> <span data-ttu-id="fd368-119">Může se jednat o váš vlastní styl psaní kódu nebo tak můžete činit z jednoho z následujících důvodů:</span><span class="sxs-lookup"><span data-stu-id="fd368-119">This may be your personal coding style, or you might want to do this for one of the following reasons:</span></span>  
  
* <span data-ttu-id="fd368-120">Zahrnout `catch` ke zpracování jakýchkoli výjimek v bloku `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="fd368-120">To include a `catch` block to handle any exceptions thrown in the `try` block.</span></span> <span data-ttu-id="fd368-121">V opačném případě zůstanou veškeré výjimky vyvolané `using` nezpracované, stejně jako výjimky vyvolané v rámci `using` blokovat, pokud `try/catch` bloku není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="fd368-121">Otherwise, any exceptions thrown by the `using` statement are unhandled, as are any exceptions thrown within the `using` block if a `try/catch` block isn't present.</span></span>  
  
* <span data-ttu-id="fd368-122">Chcete-li vytvořit instanci objektu, který implementuje <xref:System.IDisposable> jehož rozsah není místním vyjádřením bloku, ve kterém je deklarována.</span><span class="sxs-lookup"><span data-stu-id="fd368-122">To instantiate an object that implements <xref:System.IDisposable> whose scope is not local to the block within which it is declared.</span></span>  
  
<span data-ttu-id="fd368-123">Následující příklad je podobné jako v předchozím příkladu, s tím rozdílem, že používá `try/catch/finally` blok k vytváření instancí, použití a vyřadit <xref:System.IO.StreamReader> objektu a na zpracování jakékoli výjimky vyvolané <xref:System.IO.StreamReader> konstruktoru a jeho <xref:System.IO.StreamReader.ReadToEnd%2A> – metoda.</span><span class="sxs-lookup"><span data-stu-id="fd368-123">The following example is similar to the previous example, except that it uses a `try/catch/finally` block to instantiate, use, and dispose of a <xref:System.IO.StreamReader> object, and to handle any exceptions thrown by the <xref:System.IO.StreamReader> constructor and its <xref:System.IO.StreamReader.ReadToEnd%2A> method.</span></span> <span data-ttu-id="fd368-124">Všimněte si, že kód v `finally` bloku kontroluje, zda objekt, který implementuje <xref:System.IDisposable> není `null` před voláním <xref:System.IDisposable.Dispose%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="fd368-124">Note that the code in the `finally` block checks that the object that implements <xref:System.IDisposable> isn't `null` before it calls the <xref:System.IDisposable.Dispose%2A> method.</span></span> <span data-ttu-id="fd368-125">K tomu může dojít <xref:System.NullReferenceException> výjimka za běhu.</span><span class="sxs-lookup"><span data-stu-id="fd368-125">Failure to do this can result in a <xref:System.NullReferenceException> exception at run time.</span></span>  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
<span data-ttu-id="fd368-126">Tento základní princip lze použít v případě, že se rozhodnete implementovat nebo musí implementovat `try/finally` blokovat, protože váš programovací jazyk nepodporuje `using` příkaz ale umožňuje přímá volání <xref:System.IDisposable.Dispose%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="fd368-126">You can follow this basic pattern if you choose to implement or must implement a `try/finally` block, because your programming language doesn't support a `using` statement but does allow direct calls to the <xref:System.IDisposable.Dispose%2A> method.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="fd368-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fd368-127">See also</span></span>

- [<span data-ttu-id="fd368-128">Vymazání nespravovaných prostředků</span><span class="sxs-lookup"><span data-stu-id="fd368-128">Cleaning Up Unmanaged Resources</span></span>](../../../docs/standard/garbage-collection/unmanaged.md)
- [<span data-ttu-id="fd368-129">Using – příkaz (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="fd368-129">using Statement (C# Reference)</span></span>](~/docs/csharp/language-reference/keywords/using-statement.md)
- [<span data-ttu-id="fd368-130">Using – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fd368-130">Using Statement (Visual Basic)</span></span>](~/docs/visual-basic/language-reference/statements/using-statement.md)
