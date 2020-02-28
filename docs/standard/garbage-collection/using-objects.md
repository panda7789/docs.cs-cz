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
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160275"
---
# <a name="using-objects-that-implement-idisposable"></a><span data-ttu-id="eb022-102">Použití objektů, které implementují IDisposable</span><span class="sxs-lookup"><span data-stu-id="eb022-102">Using objects that implement IDisposable</span></span>

<span data-ttu-id="eb022-103">Systém uvolňování paměti modulu CLR (Common Language Runtime) uvolňuje paměť využívané spravovanými objekty, ale typy, které používají nespravované prostředky, implementují rozhraní <xref:System.IDisposable>, aby mohla být uvolněna paměť přidělená těmto nespravovaným prostředkům.</span><span class="sxs-lookup"><span data-stu-id="eb022-103">The common language runtime's garbage collector reclaims the memory used by managed objects, but types that use unmanaged resources implement the <xref:System.IDisposable> interface to allow the memory allocated to these unmanaged resources to be reclaimed.</span></span> <span data-ttu-id="eb022-104">Po dokončení použití objektu, který implementuje <xref:System.IDisposable>, byste měli zavolat implementaci <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> objektu.</span><span class="sxs-lookup"><span data-stu-id="eb022-104">When you finish using an object that implements <xref:System.IDisposable>, you should call the object's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="eb022-105">Toto lze provést jedním ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="eb022-105">You can do this in one of two ways:</span></span>  
  
- <span data-ttu-id="eb022-106">Pomocí příkazu C# `using` nebo příkazu Visual Basic `Using`.</span><span class="sxs-lookup"><span data-stu-id="eb022-106">With the C# `using` statement or the Visual Basic `Using` statement.</span></span>  
  
- <span data-ttu-id="eb022-107">Implementací bloku `try/finally`.</span><span class="sxs-lookup"><span data-stu-id="eb022-107">By implementing a `try/finally` block.</span></span>  

## <a name="the-using-statement"></a><span data-ttu-id="eb022-108">Pomocí příkazu using</span><span class="sxs-lookup"><span data-stu-id="eb022-108">The using statement</span></span>

<span data-ttu-id="eb022-109">Příkaz `using` v C# a příkaz `Using` v Visual Basic zjednodušuje kód, který je nutné zapsat pro vytvoření a vyčištění objektu.</span><span class="sxs-lookup"><span data-stu-id="eb022-109">The `using` statement in C# and the `Using` statement in Visual Basic simplify the code that you must write to create and clean up an object.</span></span> <span data-ttu-id="eb022-110">Příkaz `using` získá jeden nebo více prostředků, spustí příkazy, které zadáte, a automaticky odstraní objekt.</span><span class="sxs-lookup"><span data-stu-id="eb022-110">The `using` statement obtains one or more resources, executes the statements that you specify, and automatically disposes of the object.</span></span> <span data-ttu-id="eb022-111">Příkaz `using` je vhodný pouze pro objekty, které jsou používány v rámci rozsahu metody, ve které jsou vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="eb022-111">However, the `using` statement is useful only for objects that are used within the scope of the method in which they are constructed.</span></span>  
  
<span data-ttu-id="eb022-112">Následující příklad používá příkaz `using` k vytvoření a uvolnění objektu <xref:System.IO.StreamReader?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="eb022-112">The following example uses the `using` statement to create and release a <xref:System.IO.StreamReader?displayProperty=nameWithType> object.</span></span>  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
<span data-ttu-id="eb022-113">Všimněte si, že i když třída <xref:System.IO.StreamReader> implementuje rozhraní <xref:System.IDisposable>, což znamená, že používá nespravovaný prostředek, příklad explicitně nevolá metodu <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="eb022-113">Note that although the <xref:System.IO.StreamReader> class implements the <xref:System.IDisposable> interface, which indicates that it uses an unmanaged resource, the example doesn't explicitly call the <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="eb022-114">Když kompilátor C# nebo Visual Basic nalezne příkaz `using`, vygeneruje převodní jazyk (IL), který je ekvivalentní následujícímu kódu, který explicitně obsahuje blok `try/finally`.</span><span class="sxs-lookup"><span data-stu-id="eb022-114">When the C# or Visual Basic compiler encounters the `using` statement, it emits intermediate language (IL) that is equivalent to the following code that explicitly contains a `try/finally` block.</span></span>  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
<span data-ttu-id="eb022-115">Příkaz C# `using` také umožňuje získat více prostředků v jednom příkazu, který je interně ekvivalentní vnořeným `using`m příkazům.</span><span class="sxs-lookup"><span data-stu-id="eb022-115">The C# `using` statement also allows you to acquire multiple resources in a single statement, which is internally equivalent to nested `using` statements.</span></span> <span data-ttu-id="eb022-116">Následující příklad vytvoří instanci dvou objektů <xref:System.IO.StreamReader> pro čtení obsahu dvou různých souborů.</span><span class="sxs-lookup"><span data-stu-id="eb022-116">The following example instantiates two <xref:System.IO.StreamReader> objects to read the contents of two different files.</span></span>  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a><span data-ttu-id="eb022-117">Testovací blok / bezpodmínečný blok</span><span class="sxs-lookup"><span data-stu-id="eb022-117">Try/finally block</span></span>

<span data-ttu-id="eb022-118">Namísto zabalení `try/finally` bloku v příkazu `using`, můžete zvolit přímé implementace `try/finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="eb022-118">Instead of wrapping a `try/finally` block in a `using` statement, you may choose to implement the `try/finally` block directly.</span></span> <span data-ttu-id="eb022-119">Může se jednat o váš vlastní styl psaní kódu nebo tak můžete činit z jednoho z následujících důvodů:</span><span class="sxs-lookup"><span data-stu-id="eb022-119">This may be your personal coding style, or you might want to do this for one of the following reasons:</span></span>  
  
- <span data-ttu-id="eb022-120">Chcete-li zahrnout blok `catch` pro zpracování jakýchkoli výjimek vyvolaných v bloku `try`.</span><span class="sxs-lookup"><span data-stu-id="eb022-120">To include a `catch` block to handle any exceptions thrown in the `try` block.</span></span> <span data-ttu-id="eb022-121">V opačném případě jakékoli výjimky vyvolané příkazem `using` nejsou ošetřeny, stejně jako jakékoli výjimky vyvolané v rámci `using` bloku, pokud není přítomen blok `try/catch`.</span><span class="sxs-lookup"><span data-stu-id="eb022-121">Otherwise, any exceptions thrown by the `using` statement are unhandled, as are any exceptions thrown within the `using` block if a `try/catch` block isn't present.</span></span>  
  
- <span data-ttu-id="eb022-122">Chcete-li vytvořit instanci objektu, který implementuje <xref:System.IDisposable>, jehož obor není místní pro blok, ve kterém je deklarována.</span><span class="sxs-lookup"><span data-stu-id="eb022-122">To instantiate an object that implements <xref:System.IDisposable> whose scope is not local to the block within which it is declared.</span></span>  
  
<span data-ttu-id="eb022-123">Následující příklad je podobný předchozímu příkladu s tím rozdílem, že používá `try/catch/finally` blok pro vytvoření instance, použití a Dispose objektu <xref:System.IO.StreamReader> a ke zpracování jakýchkoli výjimek vyvolaných konstruktorem <xref:System.IO.StreamReader> a její <xref:System.IO.StreamReader.ReadToEnd%2A>ou metodou.</span><span class="sxs-lookup"><span data-stu-id="eb022-123">The following example is similar to the previous example, except that it uses a `try/catch/finally` block to instantiate, use, and dispose of a <xref:System.IO.StreamReader> object, and to handle any exceptions thrown by the <xref:System.IO.StreamReader> constructor and its <xref:System.IO.StreamReader.ReadToEnd%2A> method.</span></span> <span data-ttu-id="eb022-124">Všimněte si, že kód v bloku `finally` kontroluje, zda objekt, který implementuje <xref:System.IDisposable> není `null` před voláním metody <xref:System.IDisposable.Dispose%2A>.</span><span class="sxs-lookup"><span data-stu-id="eb022-124">Note that the code in the `finally` block checks that the object that implements <xref:System.IDisposable> isn't `null` before it calls the <xref:System.IDisposable.Dispose%2A> method.</span></span> <span data-ttu-id="eb022-125">V takovém případě může dojít k výjimce <xref:System.NullReferenceException> v době běhu.</span><span class="sxs-lookup"><span data-stu-id="eb022-125">Failure to do this can result in a <xref:System.NullReferenceException> exception at run time.</span></span>  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
<span data-ttu-id="eb022-126">Můžete postupovat podle tohoto základního vzoru, pokud se rozhodnete implementovat nebo musíte implementovat blok `try/finally`, protože váš programovací jazyk nepodporuje příkaz `using`, ale umožňuje přímé volání metody <xref:System.IDisposable.Dispose%2A>.</span><span class="sxs-lookup"><span data-stu-id="eb022-126">You can follow this basic pattern if you choose to implement or must implement a `try/finally` block, because your programming language doesn't support a `using` statement but does allow direct calls to the <xref:System.IDisposable.Dispose%2A> method.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="eb022-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb022-127">See also</span></span>

- [<span data-ttu-id="eb022-128">Vymazání nespravovaných prostředků</span><span class="sxs-lookup"><span data-stu-id="eb022-128">Cleaning Up Unmanaged Resources</span></span>](../../../docs/standard/garbage-collection/unmanaged.md)
- [<span data-ttu-id="eb022-129">using – příkazC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="eb022-129">using Statement (C# Reference)</span></span>](../../csharp/language-reference/keywords/using-statement.md)
- [<span data-ttu-id="eb022-130">Using – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb022-130">Using Statement (Visual Basic)</span></span>](../../visual-basic/language-reference/statements/using-statement.md)
