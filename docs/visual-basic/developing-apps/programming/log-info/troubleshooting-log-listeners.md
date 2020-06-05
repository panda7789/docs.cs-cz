---
title: 'Řešení potíží: Komponenty naslouchající protokolům'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
ms.openlocfilehash: 8d2d8294d9e9bb42d72fe4f6c37bf846bd644907
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398315"
---
# <a name="troubleshooting-log-listeners-visual-basic"></a><span data-ttu-id="a7dcf-102">Řešení potíží: Součásti naslouchající protokolům (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7dcf-102">Troubleshooting: Log Listeners (Visual Basic)</span></span>

<span data-ttu-id="a7dcf-103">Pomocí `My.Application.Log` objektů a můžete `My.Log` protokolovat informace o událostech, ke kterým dochází ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a7dcf-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span>  
  
 <span data-ttu-id="a7dcf-104">Chcete-li zjistit, které naslouchací procesy protokolu obdrží tyto zprávy, přečtěte si [Návod: určení, kde my. Application. Log zapisuje informace](walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="a7dcf-104">To determine which log listeners receive those messages, see [Walkthrough: Determining Where My.Application.Log Writes Information](walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
 <span data-ttu-id="a7dcf-105">`Log`Objekt může použít filtrování protokolu k omezení množství informací, které protokoluje.</span><span class="sxs-lookup"><span data-stu-id="a7dcf-105">The `Log` object can use log filtering to limit the amount of information that it logs.</span></span> <span data-ttu-id="a7dcf-106">Pokud jsou filtry nesprávně nakonfigurované, můžou protokoly obsahovat nesprávné informace.</span><span class="sxs-lookup"><span data-stu-id="a7dcf-106">If the filters are misconfigured, the logs might contain the wrong information.</span></span> <span data-ttu-id="a7dcf-107">Další informace o filtrování najdete v tématu [Návod: filtrování výstupu my. Application. log](walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="a7dcf-107">For more information about filtering, see [Walkthrough: Filtering My.Application.Log Output](walkthrough-filtering-my-application-log-output.md).</span></span>  
  
 <span data-ttu-id="a7dcf-108">Pokud je ale protokol nesprávně nakonfigurovaný, možná budete potřebovat další informace o jeho aktuální konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="a7dcf-108">However, if a log is configured incorrectly, you may need more information about its current configuration.</span></span> <span data-ttu-id="a7dcf-109">K těmto informacím se můžete dostat prostřednictvím vlastnosti Upřesnit v protokolu `TraceSource` .</span><span class="sxs-lookup"><span data-stu-id="a7dcf-109">You can get to this information through the log's advanced `TraceSource` property.</span></span>  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a><span data-ttu-id="a7dcf-110">Určení naslouchacího procesu protokolu pro objekt log v kódu</span><span class="sxs-lookup"><span data-stu-id="a7dcf-110">To determine the log listeners for the Log object in code</span></span>  
  
1. <span data-ttu-id="a7dcf-111">Importujte <xref:System.Diagnostics> obor názvů na začátek souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="a7dcf-111">Import the <xref:System.Diagnostics> namespace at the beginning of the code file.</span></span> <span data-ttu-id="a7dcf-112">Další informace naleznete v tématu [příkaz Imports (obor názvů a typ rozhraní .NET)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="a7dcf-112">For more information, see [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#13)]  
  
2. <span data-ttu-id="a7dcf-113">Vytvořte funkci, která vrátí řetězec skládající se z informací pro každý naslouchací proces protokolu.</span><span class="sxs-lookup"><span data-stu-id="a7dcf-113">Create a function that returns a string consisting of information for each of the log's listeners.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#14)]  
  
3. <span data-ttu-id="a7dcf-114">Předejte kolekci posluchačů trasování protokolu do `GetListeners` funkce a zobrazte návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a7dcf-114">Pass the collection of the log's trace listeners to the `GetListeners` function, and display the return value.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#19)]  
  
     <span data-ttu-id="a7dcf-115">Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="a7dcf-115">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7dcf-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="a7dcf-116">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="a7dcf-117">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="a7dcf-117">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="a7dcf-118">Návod: Zjištění, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="a7dcf-118">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](walkthrough-determining-where-my-application-log-writes-information.md)
