---
title: Registrace zpětných volání pro žádosti o zrušení
ms.date: 08/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
ms.openlocfilehash: faa8dada5779f6eaee7a60e6210ec604f5fb4680
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608457"
---
# <a name="register-callbacks-for-cancellation-requests"></a><span data-ttu-id="14214-102">Registrace zpětných volání pro žádosti o zrušení</span><span class="sxs-lookup"><span data-stu-id="14214-102">Register callbacks for cancellation requests</span></span>

<span data-ttu-id="14214-103">Naučte se, jak zaregistrovat delegáta, který se vyvolá, když se <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost změní na true.</span><span class="sxs-lookup"><span data-stu-id="14214-103">Learn how to register a delegate that will be invoked when a <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property becomes true.</span></span> <span data-ttu-id="14214-104">Hodnota se změní z false na true, pokud <xref:System.Threading.CancellationTokenSource.Cancel%2A> je provedeno volání na objekt, který vytvořil token.</span><span class="sxs-lookup"><span data-stu-id="14214-104">The value changes from false to true when a call to <xref:System.Threading.CancellationTokenSource.Cancel%2A> on the object that created the token is made.</span></span> <span data-ttu-id="14214-105">Tuto techniku použijte pro zrušení asynchronních operací, které nativně nepodporují jednotné rozhraní zrušení, a pro odblokování metod, které mohou čekat na dokončení asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="14214-105">Use this technique for canceling asynchronous operations that do not natively support the unified cancellation framework, and for unblocking methods that might be waiting for an asynchronous operation to finish.</span></span>

> [!NOTE]
> <span data-ttu-id="14214-106">Pokud je povolena vlastnost „Pouze vlastní kód“, zastaví se sada Visual Studio v některých případech na řádce, která výjimku vyvolá, a zobrazí chybovou zprávu s upozorněním, že „výjimka není zpracována uživatelským kódem“.</span><span class="sxs-lookup"><span data-stu-id="14214-106">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="14214-107">Tato chyba je neškodná.</span><span class="sxs-lookup"><span data-stu-id="14214-107">This error is benign.</span></span> <span data-ttu-id="14214-108">Stiskem klávesy <kbd>F5</kbd> můžete pokračovat a zobrazit chování zpracování výjimek, které je znázorněno v níže uvedených příkladech.</span><span class="sxs-lookup"><span data-stu-id="14214-108">You can press <kbd>F5</kbd> to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="14214-109">Chcete-li aplikaci Visual Studio zabránit v přerušení první chyby, zrušte zaškrtnutí políčka Pouze můj kód v části **nástroje, možnosti, ladění, obecné**.</span><span class="sxs-lookup"><span data-stu-id="14214-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>

## <a name="example"></a><span data-ttu-id="14214-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="14214-110">Example</span></span>

<span data-ttu-id="14214-111">V následujícím příkladu <xref:System.Net.WebClient.CancelAsync%2A> je metoda registrována jako metoda, která má být vyvolána, když je zrušení požadováno prostřednictvím tokenu zrušení.</span><span class="sxs-lookup"><span data-stu-id="14214-111">In the following example, the <xref:System.Net.WebClient.CancelAsync%2A> method is registered as the method to be invoked when cancellation is requested through the cancellation token.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb":::

<span data-ttu-id="14214-112">Pokud bylo zrušení již vyžádáno při zaregistrování zpětného volání, zpětné volání je stále zaručeno pro volání.</span><span class="sxs-lookup"><span data-stu-id="14214-112">If cancellation has already been requested when the callback is registered, the callback is still guaranteed to be called.</span></span> <span data-ttu-id="14214-113">V tomto konkrétním případě metoda neprovede <xref:System.Net.WebClient.CancelAsync%2A> žádnou akci, pokud neprobíhá žádná asynchronní operace, takže je vždy bezpečné volat metodu.</span><span class="sxs-lookup"><span data-stu-id="14214-113">In this particular case, the <xref:System.Net.WebClient.CancelAsync%2A> method will do nothing if no asynchronous operation is in progress, so it is always safe to call the method.</span></span>

## <a name="see-also"></a><span data-ttu-id="14214-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="14214-114">See also</span></span>

- [<span data-ttu-id="14214-115">Zrušení ve spravovaných vláknech</span><span class="sxs-lookup"><span data-stu-id="14214-115">Cancellation in managed threads</span></span>](cancellation-in-managed-threads.md)
- <xref:System.Net.WebClient.DownloadStringTaskAsync(System.String)?displayProperty=nameWithType>
