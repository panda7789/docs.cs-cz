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
ms.openlocfilehash: 0482d43925f4f547114119a95909501cbf09eedb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279359"
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a><span data-ttu-id="49ceb-102">Postupy: Registrace zpětných volání pro požadavky zrušení</span><span class="sxs-lookup"><span data-stu-id="49ceb-102">How to: Register Callbacks for Cancellation Requests</span></span>
<span data-ttu-id="49ceb-103">Následující příklad ukazuje, jak zaregistrovat delegáta, který bude vyvolán, když se <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost změní na true kvůli volání <xref:System.Threading.CancellationTokenSource.Cancel%2A> na objekt, který vytvořil token.</span><span class="sxs-lookup"><span data-stu-id="49ceb-103">The following example shows how to register a delegate that will be invoked when a <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property becomes true due to a call to <xref:System.Threading.CancellationTokenSource.Cancel%2A> on the object that created the token.</span></span> <span data-ttu-id="49ceb-104">Tuto techniku použijte pro zrušení asynchronních operací, které nativně nepodporují jednotné rozhraní zrušení, a pro odblokování metod, které mohou čekat na dokončení asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="49ceb-104">Use this technique for cancelling asynchronous operations that do not natively support the unified cancellation framework, and for unblocking methods that might be waiting for an asynchronous operation to finish.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="49ceb-105">Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“.</span><span class="sxs-lookup"><span data-stu-id="49ceb-105">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="49ceb-106">Tato chyba je neškodná.</span><span class="sxs-lookup"><span data-stu-id="49ceb-106">This error is benign.</span></span> <span data-ttu-id="49ceb-107">Stiskem klávesy F5 můžete pokračovat a zobrazit chování zpracování výjimek, které je znázorněno v níže uvedených příkladech.</span><span class="sxs-lookup"><span data-stu-id="49ceb-107">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="49ceb-108">Chcete-li aplikaci Visual Studio zabránit v přerušení první chyby, zrušte zaškrtnutí políčka Pouze můj kód v části **nástroje, možnosti, ladění, obecné**.</span><span class="sxs-lookup"><span data-stu-id="49ceb-108">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49ceb-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="49ceb-109">Example</span></span>  
 <span data-ttu-id="49ceb-110">V následujícím příkladu <xref:System.Net.WebClient.CancelAsync%2A> je metoda registrována jako metoda, která má být vyvolána, když je zrušení požadováno prostřednictvím tokenu zrušení.</span><span class="sxs-lookup"><span data-stu-id="49ceb-110">In the following example, the <xref:System.Net.WebClient.CancelAsync%2A> method is registered as the method to be invoked when cancellation is requested through the cancellation token.</span></span>  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 <span data-ttu-id="49ceb-111">Pokud bylo zrušení již vyžádáno při zaregistrování zpětného volání, zpětné volání je stále zaručeno pro volání.</span><span class="sxs-lookup"><span data-stu-id="49ceb-111">If cancellation has already been requested when the callback is registered, the callback is still guaranteed to be called.</span></span> <span data-ttu-id="49ceb-112">V tomto konkrétním případě metoda neprovede <xref:System.Net.WebClient.CancelAsync%2A> žádnou akci, pokud neprobíhá žádná asynchronní operace, takže je vždy bezpečné volat metodu.</span><span class="sxs-lookup"><span data-stu-id="49ceb-112">In this particular case, the <xref:System.Net.WebClient.CancelAsync%2A> method will do nothing if no asynchronous operation is in progress, so it is always safe to call the method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49ceb-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="49ceb-113">See also</span></span>

- [<span data-ttu-id="49ceb-114">Zrušení ve spravovaných vláknech</span><span class="sxs-lookup"><span data-stu-id="49ceb-114">Cancellation in Managed Threads</span></span>](cancellation-in-managed-threads.md)
