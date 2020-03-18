---
title: Použití objektů, které implementují IDisposable
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
ms.openlocfilehash: c5232aa89064c514e71f3a18bc754159e9c9b15b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160275"
---
# <a name="using-objects-that-implement-idisposable"></a><span data-ttu-id="b6d70-102">Použití objektů, které implementují IDisposable</span><span class="sxs-lookup"><span data-stu-id="b6d70-102">Using objects that implement IDisposable</span></span>

<span data-ttu-id="b6d70-103">Uvolňování paměti modulu COMMON Jazyka runtime uvolňuje paměť používanou spravovanými <xref:System.IDisposable> objekty, ale typy, které používají nespravované prostředky, implementují rozhraní tak, aby paměť přidělená těmto nespravovaným prostředkům byla uvolněna.</span><span class="sxs-lookup"><span data-stu-id="b6d70-103">The common language runtime's garbage collector reclaims the memory used by managed objects, but types that use unmanaged resources implement the <xref:System.IDisposable> interface to allow the memory allocated to these unmanaged resources to be reclaimed.</span></span> <span data-ttu-id="b6d70-104">Po dokončení pomocí objektu, <xref:System.IDisposable>který implementuje , <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> měli byste volat implementaci objektu.</span><span class="sxs-lookup"><span data-stu-id="b6d70-104">When you finish using an object that implements <xref:System.IDisposable>, you should call the object's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="b6d70-105">Toto lze provést jedním ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="b6d70-105">You can do this in one of two ways:</span></span>  
  
- <span data-ttu-id="b6d70-106">S c# `using` příkaz nebo `Using` visual basic prohlášení.</span><span class="sxs-lookup"><span data-stu-id="b6d70-106">With the C# `using` statement or the Visual Basic `Using` statement.</span></span>  
  
- <span data-ttu-id="b6d70-107">Implementací `try/finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="b6d70-107">By implementing a `try/finally` block.</span></span>  

## <a name="the-using-statement"></a><span data-ttu-id="b6d70-108">Pomocí příkazu using</span><span class="sxs-lookup"><span data-stu-id="b6d70-108">The using statement</span></span>

<span data-ttu-id="b6d70-109">Příkaz `using` v jazyce `Using` C# a příkaz v jazyce Visual Basic zjednodušit kód, který je nutné napsat k vytvoření a vyčištění objektu.</span><span class="sxs-lookup"><span data-stu-id="b6d70-109">The `using` statement in C# and the `Using` statement in Visual Basic simplify the code that you must write to create and clean up an object.</span></span> <span data-ttu-id="b6d70-110">Příkaz `using` získá jeden nebo více prostředků, provede příkazy, které zadáte, a automaticky nakládá s objektem.</span><span class="sxs-lookup"><span data-stu-id="b6d70-110">The `using` statement obtains one or more resources, executes the statements that you specify, and automatically disposes of the object.</span></span> <span data-ttu-id="b6d70-111">`using` Příkaz je však užitečné pouze pro objekty, které se používají v rámci rozsahu metody, ve kterém jsou vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="b6d70-111">However, the `using` statement is useful only for objects that are used within the scope of the method in which they are constructed.</span></span>  
  
<span data-ttu-id="b6d70-112">Následující příklad používá `using` příkaz k vytvoření <xref:System.IO.StreamReader?displayProperty=nameWithType> a uvolnění objektu.</span><span class="sxs-lookup"><span data-stu-id="b6d70-112">The following example uses the `using` statement to create and release a <xref:System.IO.StreamReader?displayProperty=nameWithType> object.</span></span>  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
<span data-ttu-id="b6d70-113">Všimněte si, že i když <xref:System.IO.StreamReader> třída implementuje <xref:System.IDisposable> rozhraní, což znamená, že <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> používá nespravovaný prostředek, příklad není explicitně volat metodu.</span><span class="sxs-lookup"><span data-stu-id="b6d70-113">Note that although the <xref:System.IO.StreamReader> class implements the <xref:System.IDisposable> interface, which indicates that it uses an unmanaged resource, the example doesn't explicitly call the <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b6d70-114">Když kompilátor jazyka C# nebo `using` Visual Basic narazí na příkaz, vydává zprostředkující jazyk (IL), který je ekvivalentní následující kód, který explicitně obsahuje `try/finally` blok.</span><span class="sxs-lookup"><span data-stu-id="b6d70-114">When the C# or Visual Basic compiler encounters the `using` statement, it emits intermediate language (IL) that is equivalent to the following code that explicitly contains a `try/finally` block.</span></span>  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
<span data-ttu-id="b6d70-115">Příkaz C# `using` také umožňuje získat více prostředků v jednom příkazu, který `using` je vnitřně ekvivalentní vnořené příkazy.</span><span class="sxs-lookup"><span data-stu-id="b6d70-115">The C# `using` statement also allows you to acquire multiple resources in a single statement, which is internally equivalent to nested `using` statements.</span></span> <span data-ttu-id="b6d70-116">Následující příklad inkonfikuje dva <xref:System.IO.StreamReader> objekty ke čtení obsahu dvou různých souborů.</span><span class="sxs-lookup"><span data-stu-id="b6d70-116">The following example instantiates two <xref:System.IO.StreamReader> objects to read the contents of two different files.</span></span>  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a><span data-ttu-id="b6d70-117">Testovací blok / bezpodmínečný blok</span><span class="sxs-lookup"><span data-stu-id="b6d70-117">Try/finally block</span></span>

<span data-ttu-id="b6d70-118">Namísto zabalení `try/finally` bloku `using` v příkazu, můžete `try/finally` provést blok přímo.</span><span class="sxs-lookup"><span data-stu-id="b6d70-118">Instead of wrapping a `try/finally` block in a `using` statement, you may choose to implement the `try/finally` block directly.</span></span> <span data-ttu-id="b6d70-119">Může se jednat o váš vlastní styl psaní kódu nebo tak můžete činit z jednoho z následujících důvodů:</span><span class="sxs-lookup"><span data-stu-id="b6d70-119">This may be your personal coding style, or you might want to do this for one of the following reasons:</span></span>  
  
- <span data-ttu-id="b6d70-120">Chcete-li `catch` zahrnout blok pro zpracování všech `try` výjimek vyzdvižených v bloku.</span><span class="sxs-lookup"><span data-stu-id="b6d70-120">To include a `catch` block to handle any exceptions thrown in the `try` block.</span></span> <span data-ttu-id="b6d70-121">V opačném případě jsou všechny `using` výjimky vyzdvižené příkazem neošetřené, stejně jako všechny výjimky vyzývané v `using` rámci bloku, pokud `try/catch` blok není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="b6d70-121">Otherwise, any exceptions thrown by the `using` statement are unhandled, as are any exceptions thrown within the `using` block if a `try/catch` block isn't present.</span></span>  
  
- <span data-ttu-id="b6d70-122">K vytvoření instance objektu, <xref:System.IDisposable> který implementuje, jehož obor není místní bloku, ve kterém je deklarován.</span><span class="sxs-lookup"><span data-stu-id="b6d70-122">To instantiate an object that implements <xref:System.IDisposable> whose scope is not local to the block within which it is declared.</span></span>  
  
<span data-ttu-id="b6d70-123">Následující příklad je podobný předchozímu příkladu, `try/catch/finally` s tím rozdílem, že používá blok <xref:System.IO.StreamReader> k vytvoření instance, použití a <xref:System.IO.StreamReader> vyřazení objektu a ke zpracování všech výjimek vystrutekovaných konstruktorem a jeho <xref:System.IO.StreamReader.ReadToEnd%2A> metodou.</span><span class="sxs-lookup"><span data-stu-id="b6d70-123">The following example is similar to the previous example, except that it uses a `try/catch/finally` block to instantiate, use, and dispose of a <xref:System.IO.StreamReader> object, and to handle any exceptions thrown by the <xref:System.IO.StreamReader> constructor and its <xref:System.IO.StreamReader.ReadToEnd%2A> method.</span></span> <span data-ttu-id="b6d70-124">Všimněte si, `finally` že kód v bloku <xref:System.IDisposable> kontroluje, `null` že objekt, <xref:System.IDisposable.Dispose%2A> který implementuje není před voláním metody.</span><span class="sxs-lookup"><span data-stu-id="b6d70-124">Note that the code in the `finally` block checks that the object that implements <xref:System.IDisposable> isn't `null` before it calls the <xref:System.IDisposable.Dispose%2A> method.</span></span> <span data-ttu-id="b6d70-125">Pokud tak neučiníte, <xref:System.NullReferenceException> může dojít k výjimce za běhu.</span><span class="sxs-lookup"><span data-stu-id="b6d70-125">Failure to do this can result in a <xref:System.NullReferenceException> exception at run time.</span></span>  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
<span data-ttu-id="b6d70-126">Tento základní vzor můžete sledovat, pokud se `try/finally` rozhodnete implementovat nebo musíte implementovat `using` blok, protože váš <xref:System.IDisposable.Dispose%2A> programovací jazyk nepodporuje příkaz, ale umožňuje přímé volání metody.</span><span class="sxs-lookup"><span data-stu-id="b6d70-126">You can follow this basic pattern if you choose to implement or must implement a `try/finally` block, because your programming language doesn't support a `using` statement but does allow direct calls to the <xref:System.IDisposable.Dispose%2A> method.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b6d70-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="b6d70-127">See also</span></span>

- [<span data-ttu-id="b6d70-128">Vymazání nespravovaných prostředků</span><span class="sxs-lookup"><span data-stu-id="b6d70-128">Cleaning Up Unmanaged Resources</span></span>](../../../docs/standard/garbage-collection/unmanaged.md)
- [<span data-ttu-id="b6d70-129">using – příkaz (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b6d70-129">using Statement (C# Reference)</span></span>](../../csharp/language-reference/keywords/using-statement.md)
- [<span data-ttu-id="b6d70-130">Using – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6d70-130">Using Statement (Visual Basic)</span></span>](../../visual-basic/language-reference/statements/using-statement.md)
