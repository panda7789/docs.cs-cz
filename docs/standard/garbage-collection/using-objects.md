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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f165ab5b79abbc2b5464f40a27a580d26af163a
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106941"
---
# <a name="using-objects-that-implement-idisposable"></a><span data-ttu-id="e39ca-102">Použití objektů, které implementují IDisposable</span><span class="sxs-lookup"><span data-stu-id="e39ca-102">Using objects that implement IDisposable</span></span>

<span data-ttu-id="e39ca-103">Systém uvolňování paměti modulu CLR (Common Language Runtime) uvolňuje paměť využívané spravovanými objekty, ale typy, které <xref:System.IDisposable> používají nespravované prostředky, implementují rozhraní, aby bylo možné uvolnit paměť přidělené těmto nespravovaným prostředkům.</span><span class="sxs-lookup"><span data-stu-id="e39ca-103">The common language runtime's garbage collector reclaims the memory used by managed objects, but types that use unmanaged resources implement the <xref:System.IDisposable> interface to allow the memory allocated to these unmanaged resources to be reclaimed.</span></span> <span data-ttu-id="e39ca-104">Po dokončení použití objektu, který implementuje <xref:System.IDisposable>, byste měli zavolat <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementaci objektu.</span><span class="sxs-lookup"><span data-stu-id="e39ca-104">When you finish using an object that implements <xref:System.IDisposable>, you should call the object's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="e39ca-105">Toto lze provést jedním ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="e39ca-105">You can do this in one of two ways:</span></span>  
  
- <span data-ttu-id="e39ca-106">C# Pomocí příkazu nebo příkazu Visual Basic `Using` `using` .</span><span class="sxs-lookup"><span data-stu-id="e39ca-106">With the C# `using` statement or the Visual Basic `Using` statement.</span></span>  
  
- <span data-ttu-id="e39ca-107">Implementací `try/finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="e39ca-107">By implementing a `try/finally` block.</span></span>  

## <a name="the-using-statement"></a><span data-ttu-id="e39ca-108">Pomocí příkazu using</span><span class="sxs-lookup"><span data-stu-id="e39ca-108">The using statement</span></span>

<span data-ttu-id="e39ca-109">Příkaz v C# a`Using` příkaz v Visual Basic zjednoduší kód, který je nutné zapsat pro vytvoření a vyčištění objektu. `using`</span><span class="sxs-lookup"><span data-stu-id="e39ca-109">The `using` statement in C# and the `Using` statement in Visual Basic simplify the code that you must write to create and clean up an object.</span></span> <span data-ttu-id="e39ca-110">`using` Příkaz získá jeden nebo více prostředků, spustí příkazy, které zadáte, a automaticky odstraní objekt.</span><span class="sxs-lookup"><span data-stu-id="e39ca-110">The `using` statement obtains one or more resources, executes the statements that you specify, and automatically disposes of the object.</span></span> <span data-ttu-id="e39ca-111">`using` Příkaz je však vhodný pouze pro objekty, které jsou používány v rámci rozsahu metody, ve které jsou vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="e39ca-111">However, the `using` statement is useful only for objects that are used within the scope of the method in which they are constructed.</span></span>  
  
<span data-ttu-id="e39ca-112">Následující příklad používá `using` příkaz k vytvoření a <xref:System.IO.StreamReader?displayProperty=nameWithType> uvolnění objektu.</span><span class="sxs-lookup"><span data-stu-id="e39ca-112">The following example uses the `using` statement to create and release a <xref:System.IO.StreamReader?displayProperty=nameWithType> object.</span></span>  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
<span data-ttu-id="e39ca-113">Všimněte si, že <xref:System.IO.StreamReader> i když třída <xref:System.IDisposable> implementuje rozhraní, což znamená, že používá nespravovaný prostředek, <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> příklad explicitně nevolá metodu.</span><span class="sxs-lookup"><span data-stu-id="e39ca-113">Note that although the <xref:System.IO.StreamReader> class implements the <xref:System.IDisposable> interface, which indicates that it uses an unmanaged resource, the example doesn't explicitly call the <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e39ca-114">Když kompilátor C# nebo Visual Basic nalezne `using` příkaz, vygeneruje převodní jazyk (IL), který je ekvivalentní následujícímu kódu `try/finally` , který explicitně obsahuje blok.</span><span class="sxs-lookup"><span data-stu-id="e39ca-114">When the C# or Visual Basic compiler encounters the `using` statement, it emits intermediate language (IL) that is equivalent to the following code that explicitly contains a `try/finally` block.</span></span>  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
<span data-ttu-id="e39ca-115">Příkaz také umožňuje získat více prostředků v jednom příkazu, který je interně ekvivalentní vnořeným `using` příkazům. C# `using`</span><span class="sxs-lookup"><span data-stu-id="e39ca-115">The C# `using` statement also allows you to acquire multiple resources in a single statement, which is internally equivalent to nested `using` statements.</span></span> <span data-ttu-id="e39ca-116">Následující příklad vytvoří instanci dvou <xref:System.IO.StreamReader> objektů pro čtení obsahu dvou různých souborů.</span><span class="sxs-lookup"><span data-stu-id="e39ca-116">The following example instantiates two <xref:System.IO.StreamReader> objects to read the contents of two different files.</span></span>  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a><span data-ttu-id="e39ca-117">Testovací blok / bezpodmínečný blok</span><span class="sxs-lookup"><span data-stu-id="e39ca-117">Try/finally block</span></span>

<span data-ttu-id="e39ca-118">Místo zabalení `try/finally` bloku `using` v příkazu můžete zvolit přímé implementace `try/finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="e39ca-118">Instead of wrapping a `try/finally` block in a `using` statement, you may choose to implement the `try/finally` block directly.</span></span> <span data-ttu-id="e39ca-119">Může se jednat o váš vlastní styl psaní kódu nebo tak můžete činit z jednoho z následujících důvodů:</span><span class="sxs-lookup"><span data-stu-id="e39ca-119">This may be your personal coding style, or you might want to do this for one of the following reasons:</span></span>  
  
- <span data-ttu-id="e39ca-120">Chcete-li `catch` zahrnout blok pro zpracování jakýchkoli výjimek vyvolaných `try` v bloku.</span><span class="sxs-lookup"><span data-stu-id="e39ca-120">To include a `catch` block to handle any exceptions thrown in the `try` block.</span></span> <span data-ttu-id="e39ca-121">V opačném případě jakékoli výjimky vyvolané `using` příkazem nejsou ošetřeny, stejně jako jakékoli výjimky vyvolané `using` v rámci bloku, `try/catch` Pokud není přítomen blok.</span><span class="sxs-lookup"><span data-stu-id="e39ca-121">Otherwise, any exceptions thrown by the `using` statement are unhandled, as are any exceptions thrown within the `using` block if a `try/catch` block isn't present.</span></span>  
  
- <span data-ttu-id="e39ca-122">Pro vytvoření instance objektu, který implementuje <xref:System.IDisposable> , jehož obor není místní pro blok, ve kterém je deklarována.</span><span class="sxs-lookup"><span data-stu-id="e39ca-122">To instantiate an object that implements <xref:System.IDisposable> whose scope is not local to the block within which it is declared.</span></span>  
  
<span data-ttu-id="e39ca-123">Následující příklad je `try/catch/finally` podobný předchozímu příkladu s tím rozdílem, že používá blok pro vytvoření instance, použití a uvolnění <xref:System.IO.StreamReader> objektu a ke zpracování <xref:System.IO.StreamReader> jakýchkoli výjimek vyvolaných konstruktorem a jeho <xref:System.IO.StreamReader.ReadToEnd%2A> metodou.</span><span class="sxs-lookup"><span data-stu-id="e39ca-123">The following example is similar to the previous example, except that it uses a `try/catch/finally` block to instantiate, use, and dispose of a <xref:System.IO.StreamReader> object, and to handle any exceptions thrown by the <xref:System.IO.StreamReader> constructor and its <xref:System.IO.StreamReader.ReadToEnd%2A> method.</span></span> <span data-ttu-id="e39ca-124">Všimněte si, že kód v `finally` bloku kontroluje, zda objekt, který <xref:System.IDisposable> implementuje `null` , <xref:System.IDisposable.Dispose%2A> není před voláním metody.</span><span class="sxs-lookup"><span data-stu-id="e39ca-124">Note that the code in the `finally` block checks that the object that implements <xref:System.IDisposable> isn't `null` before it calls the <xref:System.IDisposable.Dispose%2A> method.</span></span> <span data-ttu-id="e39ca-125">V takovém případě může dojít k <xref:System.NullReferenceException> výjimce za běhu.</span><span class="sxs-lookup"><span data-stu-id="e39ca-125">Failure to do this can result in a <xref:System.NullReferenceException> exception at run time.</span></span>  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
<span data-ttu-id="e39ca-126">Můžete postupovat podle tohoto základního vzoru, pokud se rozhodnete implementovat nebo musíte `try/finally` implementovat blok, protože váš programovací jazyk `using` nepodporuje příkaz, ale <xref:System.IDisposable.Dispose%2A> umožňuje přímé volání metody.</span><span class="sxs-lookup"><span data-stu-id="e39ca-126">You can follow this basic pattern if you choose to implement or must implement a `try/finally` block, because your programming language doesn't support a `using` statement but does allow direct calls to the <xref:System.IDisposable.Dispose%2A> method.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="e39ca-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e39ca-127">See also</span></span>

- [<span data-ttu-id="e39ca-128">Vymazání nespravovaných prostředků</span><span class="sxs-lookup"><span data-stu-id="e39ca-128">Cleaning Up Unmanaged Resources</span></span>](../../../docs/standard/garbage-collection/unmanaged.md)
- [<span data-ttu-id="e39ca-129">using – příkazC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="e39ca-129">using Statement (C# Reference)</span></span>](../../csharp/language-reference/keywords/using-statement.md)
- [<span data-ttu-id="e39ca-130">Using – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e39ca-130">Using Statement (Visual Basic)</span></span>](../../visual-basic/language-reference/statements/using-statement.md)
