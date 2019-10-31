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
ms.openlocfilehash: ae2fadd68cb211285e31e4ee990b6fb288056091
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091559"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a><span data-ttu-id="278a5-102">Postupy: Zpracování výjimek v paralelních smyčkách</span><span class="sxs-lookup"><span data-stu-id="278a5-102">How to: Handle Exceptions in Parallel Loops</span></span>
<span data-ttu-id="278a5-103">Přetížení <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> nemají žádný zvláštní mechanismus pro zpracování výjimek, které mohou být vyvolány.</span><span class="sxs-lookup"><span data-stu-id="278a5-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> overloads do not have any special mechanism to handle exceptions that might be thrown.</span></span> <span data-ttu-id="278a5-104">V tomto ohledu se podobají regulárním `for` a `foreach` smyčky (`For` a `For Each` v Visual Basic); Neošetřená výjimka způsobí, že se smyčka okamžitě ukončí.</span><span class="sxs-lookup"><span data-stu-id="278a5-104">In this respect, they resemble regular `for` and `foreach` loops (`For` and `For Each` in Visual Basic); an unhandled exception causes the loop to terminate immediately.</span></span>  
  
 <span data-ttu-id="278a5-105">Když přidáte vlastní logiku zpracování výjimek do paralelních smyček, zpracujte případ, ve kterém mohou být podobné výjimky vyvolány na více vláknech souběžně, a případ, ve kterém výjimka vyvolaná v jednom vlákně způsobí vyvolání jiné výjimky na jiném Doporučujeme.</span><span class="sxs-lookup"><span data-stu-id="278a5-105">When you add your own exception-handling logic to parallel loops, handle the case in which similar exceptions might be thrown on multiple threads concurrently, and the case in which an exception thrown on one thread causes another exception to be thrown on another thread.</span></span> <span data-ttu-id="278a5-106">Oba případy můžete zpracovat tak, že zabalíte všechny výjimky ze smyčky v <xref:System.AggregateException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="278a5-106">You can handle both cases by wrapping all exceptions from the loop in a <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="278a5-107">Následující příklad ukazuje jeden možný přístup.</span><span class="sxs-lookup"><span data-stu-id="278a5-107">The following example shows one possible approach.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="278a5-108">Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“.</span><span class="sxs-lookup"><span data-stu-id="278a5-108">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="278a5-109">Tato chyba je neškodná.</span><span class="sxs-lookup"><span data-stu-id="278a5-109">This error is benign.</span></span> <span data-ttu-id="278a5-110">Stiskem klávesy F5 můžete pokračovat a zobrazit chování zpracování výjimek, které je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="278a5-110">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the example below.</span></span> <span data-ttu-id="278a5-111">Chcete-li aplikaci Visual Studio zabránit v přerušení první chyby, zrušte zaškrtnutí políčka Pouze můj kód v části **nástroje, možnosti, ladění, obecné**.</span><span class="sxs-lookup"><span data-stu-id="278a5-111">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="278a5-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="278a5-112">Example</span></span>  
 <span data-ttu-id="278a5-113">V tomto příkladu jsou zachyceny všechny výjimky a poté zabaleny do <xref:System.AggregateException?displayProperty=nameWithType>, který je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="278a5-113">In this example, all exceptions are caught and then wrapped in an <xref:System.AggregateException?displayProperty=nameWithType> which is thrown.</span></span> <span data-ttu-id="278a5-114">Volající může rozhodnout, jaké výjimky se mají zpracovat.</span><span class="sxs-lookup"><span data-stu-id="278a5-114">The caller can decide which exceptions to handle.</span></span>  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="278a5-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="278a5-115">See also</span></span>

- [<span data-ttu-id="278a5-116">Datový paralelismus</span><span class="sxs-lookup"><span data-stu-id="278a5-116">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="278a5-117">Výrazy lambda v PLINQ a TPL</span><span class="sxs-lookup"><span data-stu-id="278a5-117">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
