---
title: 'Postupy: Naslouchání požadavkům zrušení, které mají obslužné rutiny čekání'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, waiting with wait handles
ms.assetid: 6e2aa49b-fc84-4bcf-962b-17db98b7edcb
ms.openlocfilehash: 43ca52359a48d3ac5a27933fcc8ce56c07159cac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73137978"
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a><span data-ttu-id="1bb30-102">Postupy: Naslouchání požadavkům zrušení, které mají obslužné rutiny čekání</span><span class="sxs-lookup"><span data-stu-id="1bb30-102">How to: Listen for Cancellation Requests That Have Wait Handles</span></span>
<span data-ttu-id="1bb30-103">Pokud je metoda blokována, zatímco čeká na signalizaci události, nemůže zkontrolovat hodnotu tokenu zrušení a reagovat včas.</span><span class="sxs-lookup"><span data-stu-id="1bb30-103">If a method is blocked while it is waiting for an event to be signaled, it cannot check the value of the cancellation token and respond in a timely manner.</span></span> <span data-ttu-id="1bb30-104">První příklad ukazuje, jak tento problém vyřešit při <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> práci s událostmi, jako jsou například nepodporují sjednocené zrušení rámce.</span><span class="sxs-lookup"><span data-stu-id="1bb30-104">The first example shows how to solve this problem when you are working with events such as <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> that do not natively support the unified cancellation framework.</span></span> <span data-ttu-id="1bb30-105">Druhý příklad ukazuje efektivnější přístup, <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>který používá , který podporuje jednotné zrušení.</span><span class="sxs-lookup"><span data-stu-id="1bb30-105">The second example shows a more streamlined approach that uses <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, which does support unified cancellation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1bb30-106">Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“.</span><span class="sxs-lookup"><span data-stu-id="1bb30-106">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="1bb30-107">Tato chyba je neškodná.</span><span class="sxs-lookup"><span data-stu-id="1bb30-107">This error is benign.</span></span> <span data-ttu-id="1bb30-108">Můžete stisknout Klávesu F5 pokračovat z něj a zobrazit chování zpracování výjimek, která je znázorněna v příkladech níže.</span><span class="sxs-lookup"><span data-stu-id="1bb30-108">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="1bb30-109">Chcete-li zabránit visual studio z rozdělení na první chybu, stačí zrušit zaškrtnutí políčka "Jen můj kód" zaškrtněte políčko "Jen můj kód" v části **Nástroje, možnosti, ladění, obecné**.</span><span class="sxs-lookup"><span data-stu-id="1bb30-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bb30-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="1bb30-110">Example</span></span>  
 <span data-ttu-id="1bb30-111">Následující příklad používá <xref:System.Threading.ManualResetEvent> a chcete-li ukázat, jak odblokovat popisovače čekání, které nepodporují jednotné zrušení.</span><span class="sxs-lookup"><span data-stu-id="1bb30-111">The following example uses a <xref:System.Threading.ManualResetEvent> to demonstrate how to unblock wait handles that do not support unified cancellation.</span></span>  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="1bb30-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="1bb30-112">Example</span></span>  
 <span data-ttu-id="1bb30-113">Následující příklad používá <xref:System.Threading.ManualResetEventSlim> a demonstrovat, jak odblokovat koordinaci primitiv, které podporují jednotné zrušení.</span><span class="sxs-lookup"><span data-stu-id="1bb30-113">The following example uses a <xref:System.Threading.ManualResetEventSlim> to demonstrate how to unblock coordination primitives that do support unified cancellation.</span></span> <span data-ttu-id="1bb30-114">Stejný přístup lze použít s jinými lehkými <xref:System.Threading.Semaphore> `Slim` <xref:System.Threading.CountdownEvent>prvky koordinace, jako jsou například a .</span><span class="sxs-lookup"><span data-stu-id="1bb30-114">The same approach can be used with other lightweight coordination primitives, such as <xref:System.Threading.Semaphore>`Slim` and <xref:System.Threading.CountdownEvent>.</span></span>  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="1bb30-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="1bb30-115">See also</span></span>

- [<span data-ttu-id="1bb30-116">Zrušení ve spravovaných vláknech</span><span class="sxs-lookup"><span data-stu-id="1bb30-116">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
