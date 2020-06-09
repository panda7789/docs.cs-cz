---
title: Použití objektů, které implementují IDisposable
description: Naučte se používat objekty, které implementují rozhraní IDisposable v .NET. Typy, které používají nespravované prostředky, implementují IDisposable, aby bylo možné prostředky znovu získat.
ms.date: 05/13/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
ms.openlocfilehash: 7d5d4080f22aab6870a230d495b4a4b9ebcb3b96
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599851"
---
# <a name="using-objects-that-implement-idisposable"></a><span data-ttu-id="2673e-104">Použití objektů, které implementují IDisposable</span><span class="sxs-lookup"><span data-stu-id="2673e-104">Using objects that implement IDisposable</span></span>

<span data-ttu-id="2673e-105">Systém uvolňování paměti modulu CLR (Common Language Runtime) uvolňuje paměť, kterou používají spravované objekty, ale typy, které používají nespravované prostředky, implementují <xref:System.IDisposable> rozhraní, které umožňuje, aby prostředky, které tyto nespravované prostředky potřebovaly, byly uvolněny.</span><span class="sxs-lookup"><span data-stu-id="2673e-105">The common language runtime's garbage collector reclaims the memory used by managed objects, but types that use unmanaged resources implement the <xref:System.IDisposable> interface to allow the resources needed by these unmanaged resources to be reclaimed.</span></span> <span data-ttu-id="2673e-106">Po dokončení použití objektu, který implementuje <xref:System.IDisposable> , byste měli zavolat <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementaci objektu.</span><span class="sxs-lookup"><span data-stu-id="2673e-106">When you finish using an object that implements <xref:System.IDisposable>, you should call the object's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="2673e-107">Toto lze provést jedním ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="2673e-107">You can do this in one of two ways:</span></span>

- <span data-ttu-id="2673e-108">Pomocí příkazu jazyka C# `using` ( `Using` v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="2673e-108">With the C# `using` statement (`Using` in Visual Basic).</span></span>
- <span data-ttu-id="2673e-109">Implementací `try/finally` bloku a voláním <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> v `finally` .</span><span class="sxs-lookup"><span data-stu-id="2673e-109">By implementing a `try/finally` block, and calling the <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> in the `finally`.</span></span>

## <a name="the-using-statement"></a><span data-ttu-id="2673e-110">Pomocí příkazu using</span><span class="sxs-lookup"><span data-stu-id="2673e-110">The using statement</span></span>

<span data-ttu-id="2673e-111">[ `using` Příkaz](../../csharp/language-reference/keywords/using-statement.md) v jazyce C# a [ `Using` příkaz](../../visual-basic/language-reference/statements/using-statement.md) v Visual Basic zjednoduší kód, který je nutné zapsat pro vyčištění objektu.</span><span class="sxs-lookup"><span data-stu-id="2673e-111">The [`using` statement](../../csharp/language-reference/keywords/using-statement.md) in C# and the [`Using` statement](../../visual-basic/language-reference/statements/using-statement.md) in Visual Basic simplify the code that you must write to cleanup an object.</span></span> <span data-ttu-id="2673e-112">`using`Příkaz získá jeden nebo více prostředků, spustí příkazy, které zadáte, a automaticky odstraní objekt.</span><span class="sxs-lookup"><span data-stu-id="2673e-112">The `using` statement obtains one or more resources, executes the statements that you specify, and automatically disposes of the object.</span></span> <span data-ttu-id="2673e-113">`using`Příkaz je však vhodný pouze pro objekty, které jsou používány v rámci rozsahu metody, ve které jsou vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="2673e-113">However, the `using` statement is useful only for objects that are used within the scope of the method in which they are constructed.</span></span>

<span data-ttu-id="2673e-114">Následující příklad používá `using` příkaz k vytvoření a uvolnění <xref:System.IO.StreamReader?displayProperty=nameWithType> objektu.</span><span class="sxs-lookup"><span data-stu-id="2673e-114">The following example uses the `using` statement to create and release a <xref:System.IO.StreamReader?displayProperty=nameWithType> object.</span></span>

[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]

<span data-ttu-id="2673e-115">I když <xref:System.IO.StreamReader> Třída implementuje <xref:System.IDisposable> rozhraní, což znamená, že používá nespravovaný prostředek, příklad explicitně nevolá <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="2673e-115">Although the <xref:System.IO.StreamReader> class implements the <xref:System.IDisposable> interface, which indicates that it uses an unmanaged resource, the example doesn't explicitly call the <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2673e-116">Když kompilátor jazyka C# nebo Visual Basic nalezne `using` příkaz, vygeneruje převodní jazyk (IL), který je ekvivalentní následujícímu kódu, který explicitně obsahuje `try/finally` blok.</span><span class="sxs-lookup"><span data-stu-id="2673e-116">When the C# or Visual Basic compiler encounters the `using` statement, it emits intermediate language (IL) that is equivalent to the following code that explicitly contains a `try/finally` block.</span></span>

[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]

<span data-ttu-id="2673e-117">Příkaz jazyka C# `using` také umožňuje získat více prostředků v jednom příkazu, který je interně ekvivalentní vnořeným `using` příkazům.</span><span class="sxs-lookup"><span data-stu-id="2673e-117">The C# `using` statement also allows you to acquire multiple resources in a single statement, which is internally equivalent to nested `using` statements.</span></span> <span data-ttu-id="2673e-118">Následující příklad vytvoří instanci dvou <xref:System.IO.StreamReader> objektů pro čtení obsahu dvou různých souborů.</span><span class="sxs-lookup"><span data-stu-id="2673e-118">The following example instantiates two <xref:System.IO.StreamReader> objects to read the contents of two different files.</span></span>

[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a><span data-ttu-id="2673e-119">Testovací blok / bezpodmínečný blok</span><span class="sxs-lookup"><span data-stu-id="2673e-119">Try/finally block</span></span>

<span data-ttu-id="2673e-120">Místo zabalení `try/finally` bloku v `using` příkazu můžete zvolit `try/finally` přímé implementace bloku.</span><span class="sxs-lookup"><span data-stu-id="2673e-120">Instead of wrapping a `try/finally` block in a `using` statement, you may choose to implement the `try/finally` block directly.</span></span> <span data-ttu-id="2673e-121">Může to být váš osobní styl kódování nebo to může být vhodné v jednom z následujících důvodů:</span><span class="sxs-lookup"><span data-stu-id="2673e-121">It may be your personal coding style, or you might want to do this for one of the following reasons:</span></span>

- <span data-ttu-id="2673e-122">Chcete-li zahrnout `catch` blok pro zpracování výjimek vyvolaných v `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="2673e-122">To include a `catch` block to handle exceptions thrown in the `try` block.</span></span> <span data-ttu-id="2673e-123">V opačném případě jakékoli výjimky vyvolané v rámci `using` příkazu nejsou ošetřeny.</span><span class="sxs-lookup"><span data-stu-id="2673e-123">Otherwise, any exceptions thrown within the `using` statement are unhandled.</span></span>

- <span data-ttu-id="2673e-124">Pro vytvoření instance objektu, který implementuje, <xref:System.IDisposable> jehož obor není místní pro blok, ve kterém je deklarována.</span><span class="sxs-lookup"><span data-stu-id="2673e-124">To instantiate an object that implements <xref:System.IDisposable> whose scope is not local to the block within which it is declared.</span></span>

<span data-ttu-id="2673e-125">Následující příklad je podobný předchozímu příkladu s tím rozdílem, že používá `try/catch/finally` blok pro vytvoření instance, použití a uvolnění <xref:System.IO.StreamReader> objektu a ke zpracování jakýchkoli výjimek vyvolaných <xref:System.IO.StreamReader> konstruktorem a jeho <xref:System.IO.StreamReader.ReadToEnd%2A> metodou.</span><span class="sxs-lookup"><span data-stu-id="2673e-125">The following example is similar to the previous example, except that it uses a `try/catch/finally` block to instantiate, use, and dispose of a <xref:System.IO.StreamReader> object, and to handle any exceptions thrown by the <xref:System.IO.StreamReader> constructor and its <xref:System.IO.StreamReader.ReadToEnd%2A> method.</span></span> <span data-ttu-id="2673e-126">Kód v `finally` bloku kontroluje, zda objekt, který implementuje, <xref:System.IDisposable> není `null` před voláním <xref:System.IDisposable.Dispose%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="2673e-126">The code in the `finally` block checks that the object that implements <xref:System.IDisposable> isn't `null` before it calls the <xref:System.IDisposable.Dispose%2A> method.</span></span> <span data-ttu-id="2673e-127">V takovém případě může dojít k <xref:System.NullReferenceException> výjimce za běhu.</span><span class="sxs-lookup"><span data-stu-id="2673e-127">Failure to do this can result in a <xref:System.NullReferenceException> exception at run time.</span></span>

[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]

<span data-ttu-id="2673e-128">Můžete postupovat podle tohoto základního vzoru, pokud se rozhodnete implementovat nebo musíte implementovat `try/finally` blok, protože váš programovací jazyk nepodporuje `using` příkaz, ale umožňuje přímé volání <xref:System.IDisposable.Dispose%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="2673e-128">You can follow this basic pattern if you choose to implement or must implement a `try/finally` block, because your programming language doesn't support a `using` statement but does allow direct calls to the <xref:System.IDisposable.Dispose%2A> method.</span></span>

## <a name="idisposable-instance-members"></a><span data-ttu-id="2673e-129">Členové instance IDisposable</span><span class="sxs-lookup"><span data-stu-id="2673e-129">IDisposable instance members</span></span>

<span data-ttu-id="2673e-130">Pokud třída obsahuje <xref:System.IDisposable> implementaci jako člen instance, měla by být třída také implementovaná buď pole, nebo vlastnost <xref:System.IDisposable> .</span><span class="sxs-lookup"><span data-stu-id="2673e-130">If a class holds an <xref:System.IDisposable> implementation as an instance member, either a field or a property, the class should also implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="2673e-131">Další informace najdete v tématu [implementace kaskádové likvidace](implementing-dispose.md#cascade-dispose-calls).</span><span class="sxs-lookup"><span data-stu-id="2673e-131">For more information, see [implement a cascade dispose](implementing-dispose.md#cascade-dispose-calls).</span></span>

## <a name="see-also"></a><span data-ttu-id="2673e-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="2673e-132">See also</span></span>

- [<span data-ttu-id="2673e-133">Čištění nespravovaných prostředků</span><span class="sxs-lookup"><span data-stu-id="2673e-133">Cleaning up unmanaged resources</span></span>](unmanaged.md)
- [<span data-ttu-id="2673e-134">using – příkaz (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="2673e-134">using Statement (C# Reference)</span></span>](../../csharp/language-reference/keywords/using-statement.md)
- [<span data-ttu-id="2673e-135">Using – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2673e-135">Using Statement (Visual Basic)</span></span>](../../visual-basic/language-reference/statements/using-statement.md)
