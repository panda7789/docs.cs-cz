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
ms.openlocfilehash: e2d61ba254a76235a12ca5dda23fdecb8838ae75
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863579"
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a><span data-ttu-id="ca3bc-102">Postupy: Registrace zpětných volání pro požadavky zrušení</span><span class="sxs-lookup"><span data-stu-id="ca3bc-102">How to: Register Callbacks for Cancellation Requests</span></span>
<span data-ttu-id="ca3bc-103">Následující příklad ukazuje, jak zaregistrovat delegáta, který bude vyvolán při <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost stane pravdivou kvůli volání na <xref:System.Threading.CancellationTokenSource.Cancel%2A> na objekt, který vytvoří token.</span><span class="sxs-lookup"><span data-stu-id="ca3bc-103">The following example shows how to register a delegate that will be invoked when a <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property becomes true due to a call to <xref:System.Threading.CancellationTokenSource.Cancel%2A> on the object that created the token.</span></span> <span data-ttu-id="ca3bc-104">Tento postup použijte pro zrušení asynchronní operace, které nativně nepodporují zrušení jednotné rozhraní framework a pro odblokování metody, které mohou čekat na dokončení asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="ca3bc-104">Use this technique for cancelling asynchronous operations that do not natively support the unified cancellation framework, and for unblocking methods that might be waiting for an asynchronous operation to finish.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ca3bc-105">Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“.</span><span class="sxs-lookup"><span data-stu-id="ca3bc-105">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="ca3bc-106">Tato chyba je neškodná.</span><span class="sxs-lookup"><span data-stu-id="ca3bc-106">This error is benign.</span></span> <span data-ttu-id="ca3bc-107">Můžete stisknutím klávesy F5 pokračovat z něj a najdete v chování zpracování výjimek, což je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="ca3bc-107">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="ca3bc-108">Pokud chcete zabránit přerušení nebo první chybě sady Visual Studio, zrušte zaškrtnutí políčka "Jen můj kód" v části **nástroje, možnosti, ladění, Obecné**.</span><span class="sxs-lookup"><span data-stu-id="ca3bc-108">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca3bc-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="ca3bc-109">Example</span></span>  
 <span data-ttu-id="ca3bc-110">V následujícím příkladu <xref:System.Net.WebClient.CancelAsync%2A> metoda je zaregistrovaný jako metoda má být volána, když je požadováno zrušení prostřednictvím token zrušení.</span><span class="sxs-lookup"><span data-stu-id="ca3bc-110">In the following example, the <xref:System.Net.WebClient.CancelAsync%2A> method is registered as the method to be invoked when cancellation is requested through the cancellation token.</span></span>  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 <span data-ttu-id="ca3bc-111">Pokud již bylo vyžádáno zrušení při registraci zpětné volání, zpětné volání je stále zaručeně volán.</span><span class="sxs-lookup"><span data-stu-id="ca3bc-111">If cancellation has already been requested when the callback is registered, the callback is still guaranteed to be called.</span></span> <span data-ttu-id="ca3bc-112">V tomto konkrétním případě <xref:System.Net.WebClient.CancelAsync%2A> metoda neudělá Pokud žádná asynchronní operace probíhá, takže je vždy bezpečné volat metodu.</span><span class="sxs-lookup"><span data-stu-id="ca3bc-112">In this particular case, the <xref:System.Net.WebClient.CancelAsync%2A> method will do nothing if no asynchronous operation is in progress, so it is always safe to call the method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca3bc-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ca3bc-113">See also</span></span>

- [<span data-ttu-id="ca3bc-114">Zrušení ve spravovaných vláknech</span><span class="sxs-lookup"><span data-stu-id="ca3bc-114">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
