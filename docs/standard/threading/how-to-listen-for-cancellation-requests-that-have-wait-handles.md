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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1c8bfea5fc55bafbaa30d3b74edf60b674ef75c
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44082025"
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a><span data-ttu-id="f927c-102">Postupy: Naslouchání požadavkům zrušení, které mají obslužné rutiny čekání</span><span class="sxs-lookup"><span data-stu-id="f927c-102">How to: Listen for Cancellation Requests That Have Wait Handles</span></span>
<span data-ttu-id="f927c-103">Pokud metoda je blokovaný, když se čeká na událost má být signalizován, nemůže kontrolu hodnoty tokenu zrušení a včas reagovat.</span><span class="sxs-lookup"><span data-stu-id="f927c-103">If a method is blocked while it is waiting for an event to be signaled, it cannot check the value of the cancellation token and respond in a timely manner.</span></span> <span data-ttu-id="f927c-104">První příklad ukazuje, jak tento problém vyřešit, při práci s událostmi, jako <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> , které nativně nepodporují rozhraní unified zrušení.</span><span class="sxs-lookup"><span data-stu-id="f927c-104">The first example shows how to solve this problem when you are working with events such as <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> that do not natively support the unified cancellation framework.</span></span> <span data-ttu-id="f927c-105">Druhý příklad ukazuje jednodušší přístup, který používá <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, který nepodporuje sjednocený zrušení.</span><span class="sxs-lookup"><span data-stu-id="f927c-105">The second example shows a more streamlined approach that uses <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, which does support unified cancellation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f927c-106">Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“.</span><span class="sxs-lookup"><span data-stu-id="f927c-106">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="f927c-107">Tato chyba je neškodná.</span><span class="sxs-lookup"><span data-stu-id="f927c-107">This error is benign.</span></span> <span data-ttu-id="f927c-108">Můžete stisknutím klávesy F5 pokračovat z něj a najdete v chování zpracování výjimek, což je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="f927c-108">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="f927c-109">Pokud chcete zabránit přerušení nebo první chybě sady Visual Studio, zrušte zaškrtnutí políčka "Jen můj kód" v části **nástroje, možnosti, ladění, Obecné**.</span><span class="sxs-lookup"><span data-stu-id="f927c-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f927c-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="f927c-110">Example</span></span>  
 <span data-ttu-id="f927c-111">Následující příklad používá <xref:System.Threading.ManualResetEvent> k předvedení jak odblokovat obslužné rutiny čekání, které nepodporují jednotné zrušení.</span><span class="sxs-lookup"><span data-stu-id="f927c-111">The following example uses a <xref:System.Threading.ManualResetEvent> to demonstrate how to unblock wait handles that do not support unified cancellation.</span></span>  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="f927c-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="f927c-112">Example</span></span>  
 <span data-ttu-id="f927c-113">Následující příklad používá <xref:System.Threading.ManualResetEventSlim> ukazují, jak odblokovat koordinaci primitiv, které podporují sloučený zrušení.</span><span class="sxs-lookup"><span data-stu-id="f927c-113">The following example uses a <xref:System.Threading.ManualResetEventSlim> to demonstrate how to unblock coordination primitives that do support unified cancellation.</span></span> <span data-ttu-id="f927c-114">Stejným způsobem lze použít s další zjednodušené koordinaci primitiv, jako například <xref:System.Threading.Semaphore> `Slim` a <xref:System.Threading.CountdownEvent>.</span><span class="sxs-lookup"><span data-stu-id="f927c-114">The same approach can be used with other lightweight coordination primitives, such as <xref:System.Threading.Semaphore>`Slim` and <xref:System.Threading.CountdownEvent>.</span></span>  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="f927c-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f927c-115">See also</span></span>

- [<span data-ttu-id="f927c-116">Zrušení ve spravovaných vláknech</span><span class="sxs-lookup"><span data-stu-id="f927c-116">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
