---
title: 'Postupy: Registrace zpětných volání pro požadavky zrušení'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a8df4c73af81580d1b242ce0ede8f8bcb4cad4fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583289"
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a><span data-ttu-id="ff442-102">Postupy: Registrace zpětných volání pro požadavky zrušení</span><span class="sxs-lookup"><span data-stu-id="ff442-102">How to: Register Callbacks for Cancellation Requests</span></span>
<span data-ttu-id="ff442-103">Následující příklad ukazuje, jak zaregistrovat delegáta, který bude vyvolán při <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost bude PRAVDA z důvodu volání <xref:System.Threading.CancellationTokenSource.Cancel%2A> na objektu, který vytvořen token.</span><span class="sxs-lookup"><span data-stu-id="ff442-103">The following example shows how to register a delegate that will be invoked when a <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property becomes true due to a call to <xref:System.Threading.CancellationTokenSource.Cancel%2A> on the object that created the token.</span></span> <span data-ttu-id="ff442-104">Tento postup použijte pro zrušení asynchronních operací, které nativně nepodporují rozhraní jednotná zrušení a odblokování metody, které může být čekání na dokončení asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="ff442-104">Use this technique for cancelling asynchronous operations that do not natively support the unified cancellation framework, and for unblocking methods that might be waiting for an asynchronous operation to finish.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff442-105">Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“.</span><span class="sxs-lookup"><span data-stu-id="ff442-105">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="ff442-106">Tato chyba je neškodná.</span><span class="sxs-lookup"><span data-stu-id="ff442-106">This error is benign.</span></span> <span data-ttu-id="ff442-107">Můžete stisknutím klávesy F5 lze pokračovat a jejich chování zpracování výjimek, která je znázorněna v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="ff442-107">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="ff442-108">Abyste zabránili zastavení při první chybě Visual Studio, stačí zrušit zaškrtnutí políčka "Pouze můj kód" v části **nástroje, možnosti, ladění, Obecné**.</span><span class="sxs-lookup"><span data-stu-id="ff442-108">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff442-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="ff442-109">Example</span></span>  
 <span data-ttu-id="ff442-110">V následujícím příkladu <xref:System.Net.WebClient.CancelAsync%2A> metoda je registrován jako metoda má být volána, pokud se požaduje zrušení prostřednictvím token zrušení.</span><span class="sxs-lookup"><span data-stu-id="ff442-110">In the following example, the <xref:System.Net.WebClient.CancelAsync%2A> method is registered as the method to be invoked when cancellation is requested through the cancellation token.</span></span>  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 <span data-ttu-id="ff442-111">Pokud po registraci zpětného volání již požadavek zrušení, zpětné volání stále záruku, že má být volána.</span><span class="sxs-lookup"><span data-stu-id="ff442-111">If cancellation has already been requested when the callback is registered, the callback is still guaranteed to be called.</span></span> <span data-ttu-id="ff442-112">V tomto konkrétním případě <xref:System.Net.WebClient.CancelAsync%2A> metoda se nic nestane. Pokud žádná asynchronní operace probíhá, takže je bezpečně volat metodu.</span><span class="sxs-lookup"><span data-stu-id="ff442-112">In this particular case, the <xref:System.Net.WebClient.CancelAsync%2A> method will do nothing if no asynchronous operation is in progress, so it is always safe to call the method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff442-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff442-113">See Also</span></span>  
 [<span data-ttu-id="ff442-114">Zrušení ve spravovaných vláknech</span><span class="sxs-lookup"><span data-stu-id="ff442-114">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
