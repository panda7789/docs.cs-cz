---
title: 'Postupy: Zpracování výjimek v paralelních smyčkách'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to handle exceptions
ms.assetid: 512f0d5a-4636-4875-b766-88f20044f143
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ddf311ad2b79e615f5c3097686035e7bbfbc49c9
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44337782"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a><span data-ttu-id="b7bc1-102">Postupy: Zpracování výjimek v paralelních smyčkách</span><span class="sxs-lookup"><span data-stu-id="b7bc1-102">How to: Handle Exceptions in Parallel Loops</span></span>
<span data-ttu-id="b7bc1-103"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> přetížení nemají žádný zvláštní mechanismus zpracování výjimek, které mohou být vyvolány.</span><span class="sxs-lookup"><span data-stu-id="b7bc1-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> overloads do not have any special mechanism to handle exceptions that might be thrown.</span></span> <span data-ttu-id="b7bc1-104">V tomto ohledu se podobají pravidelně `for` a `foreach` smyčky (`For` a `For Each` v jazyce Visual Basic); neošetřené výjimky způsobí, že smyčku ukončit okamžitě.</span><span class="sxs-lookup"><span data-stu-id="b7bc1-104">In this respect, they resemble regular `for` and `foreach` loops (`For` and `For Each` in Visual Basic); an unhandled exception causes the loop to terminate immediately.</span></span>  
  
 <span data-ttu-id="b7bc1-105">Když přidáte vlastní logiku zpracování výjimek pro paralelní smyčky, zpracovávat tento případ, ve kterém může být podobné výjimky vyvolána z více vláken současně a tento případ, ve kterém výjimce v jednom vlákně způsobí, že další výjimku, která je vyvolána na jiném vlákno.</span><span class="sxs-lookup"><span data-stu-id="b7bc1-105">When you add your own exception-handling logic to parallel loops, handle the case in which similar exceptions might be thrown on multiple threads concurrently, and the case in which an exception thrown on one thread causes another exception to be thrown on another thread.</span></span> <span data-ttu-id="b7bc1-106">Obou případech může zpracovávat všechny výjimky ze smyčky v zabalení <xref:System.AggregateException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b7bc1-106">You can handle both cases by wrapping all exceptions from the loop in a <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b7bc1-107">Následující příklad ukazuje jednu z možných způsobů.</span><span class="sxs-lookup"><span data-stu-id="b7bc1-107">The following example shows one possible approach.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7bc1-108">Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“.</span><span class="sxs-lookup"><span data-stu-id="b7bc1-108">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="b7bc1-109">Tato chyba je neškodná.</span><span class="sxs-lookup"><span data-stu-id="b7bc1-109">This error is benign.</span></span> <span data-ttu-id="b7bc1-110">Můžete stisknutím klávesy F5 pokračovat z něj a najdete v chování zpracování výjimek, který je znázorněn v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b7bc1-110">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the example below.</span></span> <span data-ttu-id="b7bc1-111">Pokud chcete zabránit přerušení nebo první chybě sady Visual Studio, zrušte zaškrtnutí políčka "Jen můj kód" v části **nástroje, možnosti, ladění, Obecné**.</span><span class="sxs-lookup"><span data-stu-id="b7bc1-111">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7bc1-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="b7bc1-112">Example</span></span>  
 <span data-ttu-id="b7bc1-113">V tomto příkladu jsou všechny výjimky zachycena a potom zabalené v <xref:System.AggregateException?displayProperty=nameWithType> která je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="b7bc1-113">In this example, all exceptions are caught and then wrapped in an <xref:System.AggregateException?displayProperty=nameWithType> which is thrown.</span></span> <span data-ttu-id="b7bc1-114">Volající může rozhodnout, které výjimky pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="b7bc1-114">The caller can decide which exceptions to handle.</span></span>  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="b7bc1-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b7bc1-115">See also</span></span>

- [<span data-ttu-id="b7bc1-116">Datový paralelismus</span><span class="sxs-lookup"><span data-stu-id="b7bc1-116">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
- [<span data-ttu-id="b7bc1-117">Výrazy lambda v PLINQ a TPL</span><span class="sxs-lookup"><span data-stu-id="b7bc1-117">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
