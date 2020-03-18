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
ms.openlocfilehash: 87ba1ab9ac095c733a53f766d00ebb7530a8d9c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138002"
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a><span data-ttu-id="13ef7-102">Postupy: Registrace zpětných volání pro požadavky zrušení</span><span class="sxs-lookup"><span data-stu-id="13ef7-102">How to: Register Callbacks for Cancellation Requests</span></span>
<span data-ttu-id="13ef7-103">Následující příklad ukazuje, jak zaregistrovat delegáta, <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> který bude vyvolán, když <xref:System.Threading.CancellationTokenSource.Cancel%2A> se vlastnost stane true z důvodu volání na objekt, který vytvořil token.</span><span class="sxs-lookup"><span data-stu-id="13ef7-103">The following example shows how to register a delegate that will be invoked when a <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property becomes true due to a call to <xref:System.Threading.CancellationTokenSource.Cancel%2A> on the object that created the token.</span></span> <span data-ttu-id="13ef7-104">Tento postup použijte pro zrušení asynchronních operací, které nativně nepodporují sjednocené rozhraní pro zrušení, a pro odblokovací metody, které mohou čekat na dokončení asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="13ef7-104">Use this technique for cancelling asynchronous operations that do not natively support the unified cancellation framework, and for unblocking methods that might be waiting for an asynchronous operation to finish.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="13ef7-105">Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“.</span><span class="sxs-lookup"><span data-stu-id="13ef7-105">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="13ef7-106">Tato chyba je neškodná.</span><span class="sxs-lookup"><span data-stu-id="13ef7-106">This error is benign.</span></span> <span data-ttu-id="13ef7-107">Můžete stisknout Klávesu F5 pokračovat z něj a zobrazit chování zpracování výjimek, která je znázorněna v příkladech níže.</span><span class="sxs-lookup"><span data-stu-id="13ef7-107">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="13ef7-108">Chcete-li zabránit visual studio z rozdělení na první chybu, stačí zrušit zaškrtnutí políčka "Jen můj kód" zaškrtněte políčko "Jen můj kód" v části **Nástroje, možnosti, ladění, obecné**.</span><span class="sxs-lookup"><span data-stu-id="13ef7-108">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13ef7-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="13ef7-109">Example</span></span>  
 <span data-ttu-id="13ef7-110">V následujícím příkladu <xref:System.Net.WebClient.CancelAsync%2A> je metoda registrována jako metoda, která má být vyvolána při požadavku na zrušení prostřednictvím tokenu zrušení.</span><span class="sxs-lookup"><span data-stu-id="13ef7-110">In the following example, the <xref:System.Net.WebClient.CancelAsync%2A> method is registered as the method to be invoked when cancellation is requested through the cancellation token.</span></span>  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 <span data-ttu-id="13ef7-111">Pokud zrušení již byla požadována při zpětnévolání je registrována, zpětné volání je stále zaručeno, že bude volána.</span><span class="sxs-lookup"><span data-stu-id="13ef7-111">If cancellation has already been requested when the callback is registered, the callback is still guaranteed to be called.</span></span> <span data-ttu-id="13ef7-112">V tomto konkrétním <xref:System.Net.WebClient.CancelAsync%2A> případě metoda nebude dělat nic, pokud probíhá žádná asynchronní operace, takže je vždy bezpečné volat metodu.</span><span class="sxs-lookup"><span data-stu-id="13ef7-112">In this particular case, the <xref:System.Net.WebClient.CancelAsync%2A> method will do nothing if no asynchronous operation is in progress, so it is always safe to call the method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13ef7-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="13ef7-113">See also</span></span>

- [<span data-ttu-id="13ef7-114">Zrušení ve spravovaných vláknech</span><span class="sxs-lookup"><span data-stu-id="13ef7-114">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
