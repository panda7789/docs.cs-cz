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
ms.openlocfilehash: 11ba240d71287be91bd0b4b40a2cb69f6e2808d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580546"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a><span data-ttu-id="5f07d-102">Postupy: Zpracování výjimek v paralelních smyčkách</span><span class="sxs-lookup"><span data-stu-id="5f07d-102">How to: Handle Exceptions in Parallel Loops</span></span>
<span data-ttu-id="5f07d-103"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> přetížení nemají žádný zvláštní mechanismus zpracování výjimek, které mohou být vyvolány.</span><span class="sxs-lookup"><span data-stu-id="5f07d-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> overloads do not have any special mechanism to handle exceptions that might be thrown.</span></span> <span data-ttu-id="5f07d-104">V tomto ohledu se podobají normálním `for` a `foreach` smyčky (`For` a `For Each` v jazyce Visual Basic); k neošetřené výjimce způsobí, že smyčky ukončit okamžitě.</span><span class="sxs-lookup"><span data-stu-id="5f07d-104">In this respect, they resemble regular `for` and `foreach` loops (`For` and `For Each` in Visual Basic); an unhandled exception causes the loop to terminate immediately.</span></span>  
  
 <span data-ttu-id="5f07d-105">Když přidáte vlastní logiku zpracování výjimek a paralelní smyčky, zpracovávat tento případ, ve kterém může být podobné výjimky vyvolány ve více vláknech souběžně a tento případ, ve kterém výjimce na jedno vlákno způsobí, že jiné na jiném vyvolání výjimky přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="5f07d-105">When you add your own exception-handling logic to parallel loops, handle the case in which similar exceptions might be thrown on multiple threads concurrently, and the case in which an exception thrown on one thread causes another exception to be thrown on another thread.</span></span> <span data-ttu-id="5f07d-106">Obou případech může zpracovávat všechny výjimky z smyčky v zabalení <xref:System.AggregateException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5f07d-106">You can handle both cases by wrapping all exceptions from the loop in a <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5f07d-107">Následující příklad ukazuje jeden možný přístup.</span><span class="sxs-lookup"><span data-stu-id="5f07d-107">The following example shows one possible approach.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f07d-108">Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“.</span><span class="sxs-lookup"><span data-stu-id="5f07d-108">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="5f07d-109">Tato chyba je neškodná.</span><span class="sxs-lookup"><span data-stu-id="5f07d-109">This error is benign.</span></span> <span data-ttu-id="5f07d-110">Můžete stisknutím klávesy F5 lze pokračovat a jejich chování zpracování výjimek, který je znázorněn v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="5f07d-110">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the example below.</span></span> <span data-ttu-id="5f07d-111">Abyste zabránili zastavení při první chybě Visual Studio, stačí zrušit zaškrtnutí políčka "Pouze můj kód" v části **nástroje, možnosti, ladění, Obecné**.</span><span class="sxs-lookup"><span data-stu-id="5f07d-111">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f07d-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="5f07d-112">Example</span></span>  
 <span data-ttu-id="5f07d-113">V tomto příkladu jsou všechny výjimky zachycení a pak uzavřen do <xref:System.AggregateException?displayProperty=nameWithType> která je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="5f07d-113">In this example, all exceptions are caught and then wrapped in an <xref:System.AggregateException?displayProperty=nameWithType> which is thrown.</span></span> <span data-ttu-id="5f07d-114">Volající můžete rozhodnout, které výjimky zpracovat.</span><span class="sxs-lookup"><span data-stu-id="5f07d-114">The caller can decide which exceptions to handle.</span></span>  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="5f07d-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="5f07d-115">See Also</span></span>  
 [<span data-ttu-id="5f07d-116">Datový paralelismus</span><span class="sxs-lookup"><span data-stu-id="5f07d-116">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [<span data-ttu-id="5f07d-117">Výrazy lambda v PLINQ a TPL</span><span class="sxs-lookup"><span data-stu-id="5f07d-117">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
