---
title: 'Řešení potíží: Součásti naslouchající protokolům (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
ms.openlocfilehash: 54c3ed0f607edf992fa3c40a8e6214252740587c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589033"
---
# <a name="troubleshooting-log-listeners-visual-basic"></a><span data-ttu-id="fbb62-102">Řešení potíží: Součásti naslouchající protokolům (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbb62-102">Troubleshooting: Log Listeners (Visual Basic)</span></span>
<span data-ttu-id="fbb62-103">Můžete použít `My.Application.Log` a `My.Log` objekty k protokolování informací o událostech, ke kterým dochází ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fbb62-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span>  
  
 <span data-ttu-id="fbb62-104">Pokud chcete zjistit, kteří posluchači přijímat zprávy, najdete v části [návod: určení kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="fbb62-104">To determine which log listeners receive those messages, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
 <span data-ttu-id="fbb62-105">`Log` Objekt můžete použít filtrování protokolu k omezení množství informací, které zaznamenává.</span><span class="sxs-lookup"><span data-stu-id="fbb62-105">The `Log` object can use log filtering to limit the amount of information that it logs.</span></span> <span data-ttu-id="fbb62-106">Pokud jsou špatně nakonfigurované filtry, protokol může obsahovat nesprávné informace.</span><span class="sxs-lookup"><span data-stu-id="fbb62-106">If the filters are misconfigured, the logs might contain the wrong information.</span></span> <span data-ttu-id="fbb62-107">Další informace o filtrování najdete v tématu [návod: filtrování výstupu My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="fbb62-107">For more information about filtering, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>  
  
 <span data-ttu-id="fbb62-108">Ale pokud protokolu není správně nakonfigurovaná, můžete další informace o své aktuální konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="fbb62-108">However, if a log is configured incorrectly, you may need more information about its current configuration.</span></span> <span data-ttu-id="fbb62-109">Můžete získat tyto informace prostřednictvím protokolu rozšířenou `TraceSource` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fbb62-109">You can get to this information through the log's advanced `TraceSource` property.</span></span>  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a><span data-ttu-id="fbb62-110">Chcete-li zjistit naslouchací procesy pro protokoly pro objekt protokolu v kódu</span><span class="sxs-lookup"><span data-stu-id="fbb62-110">To determine the log listeners for the Log object in code</span></span>  
  
1.  <span data-ttu-id="fbb62-111">Import <xref:System.Diagnostics> oboru názvů na začátku souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="fbb62-111">Import the <xref:System.Diagnostics> namespace at the beginning of the code file.</span></span> <span data-ttu-id="fbb62-112">Další informace najdete v tématu [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="fbb62-112">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#13](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_1.vb)]  
  
2.  <span data-ttu-id="fbb62-113">Vytvoří funkci, která vrátí řetězec, který se skládá z informace o pro všechny moduly pro naslouchání v protokolu.</span><span class="sxs-lookup"><span data-stu-id="fbb62-113">Create a function that returns a string consisting of information for each of the log's listeners.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#14](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_2.vb)]  
  
3.  <span data-ttu-id="fbb62-114">Předávání kolekce v protokolu trasování – moduly naslouchání na `GetListeners` funkce a zobrazit návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="fbb62-114">Pass the collection of the log's trace listeners to the `GetListeners` function, and display the return value.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#19](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_3.vb)]  
  
     <span data-ttu-id="fbb62-115">Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="fbb62-115">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbb62-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="fbb62-116">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [<span data-ttu-id="fbb62-117">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="fbb62-117">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="fbb62-118">Návod: Zjištění, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="fbb62-118">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
