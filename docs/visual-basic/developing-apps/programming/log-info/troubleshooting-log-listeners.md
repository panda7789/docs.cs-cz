---
title: 'Řešení potíží: Součásti naslouchající protokolům (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
ms.openlocfilehash: f1201262fd09145679a9f70cd742294d248fedb3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831693"
---
# <a name="troubleshooting-log-listeners-visual-basic"></a><span data-ttu-id="65d2b-102">Řešení potíží: Součásti naslouchající protokolům (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65d2b-102">Troubleshooting: Log Listeners (Visual Basic)</span></span>
<span data-ttu-id="65d2b-103">Můžete použít `My.Application.Log` a `My.Log` objekty k protokolování informací o události, ke kterým dochází ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="65d2b-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span>  
  
 <span data-ttu-id="65d2b-104">Pokud chcete zjistit, jaké součásti naslouchající protokolům příjem těchto zpráv, najdete v článku [názorný postup: Určení, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="65d2b-104">To determine which log listeners receive those messages, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
 <span data-ttu-id="65d2b-105">`Log` Objektu můžete použít protokol filtrování a omezit tak množství informací, které zaznamenává.</span><span class="sxs-lookup"><span data-stu-id="65d2b-105">The `Log` object can use log filtering to limit the amount of information that it logs.</span></span> <span data-ttu-id="65d2b-106">Pokud jsou špatně nakonfigurované filtry, protokoly mohou obsahovat nesprávné informace.</span><span class="sxs-lookup"><span data-stu-id="65d2b-106">If the filters are misconfigured, the logs might contain the wrong information.</span></span> <span data-ttu-id="65d2b-107">Další informace o filtrování najdete v tématu [názorný postup: Filtrování výstupu My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="65d2b-107">For more information about filtering, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>  
  
 <span data-ttu-id="65d2b-108">Ale pokud protokol není správně nakonfigurovaná, můžete další informace o své aktuální konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="65d2b-108">However, if a log is configured incorrectly, you may need more information about its current configuration.</span></span> <span data-ttu-id="65d2b-109">Můžete získat tyto informace prostřednictvím protokolu rozšířeným `TraceSource` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="65d2b-109">You can get to this information through the log's advanced `TraceSource` property.</span></span>  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a><span data-ttu-id="65d2b-110">Chcete-li zjistit součásti naslouchající protokolům pro objekt protokolu v kódu</span><span class="sxs-lookup"><span data-stu-id="65d2b-110">To determine the log listeners for the Log object in code</span></span>  
  
1.  <span data-ttu-id="65d2b-111">Import <xref:System.Diagnostics> oboru názvů na začátku souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="65d2b-111">Import the <xref:System.Diagnostics> namespace at the beginning of the code file.</span></span> <span data-ttu-id="65d2b-112">Další informace najdete v tématu [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="65d2b-112">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#13)]  
  
2.  <span data-ttu-id="65d2b-113">Vytvoření funkce, která vrací řetězec obsahující informace pro všechny moduly pro naslouchání v protokolu.</span><span class="sxs-lookup"><span data-stu-id="65d2b-113">Create a function that returns a string consisting of information for each of the log's listeners.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#14)]  
  
3.  <span data-ttu-id="65d2b-114">Kolekce naslouchacích procesů trasování v protokolu k předání `GetListeners` fungovat a zobrazit návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="65d2b-114">Pass the collection of the log's trace listeners to the `GetListeners` function, and display the return value.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#19)]  
  
     <span data-ttu-id="65d2b-115">Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="65d2b-115">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65d2b-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65d2b-116">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="65d2b-117">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="65d2b-117">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="65d2b-118">Návod: Určení, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="65d2b-118">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
