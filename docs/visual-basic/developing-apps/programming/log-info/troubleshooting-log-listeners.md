---
title: "Řešení potíží: Součásti naslouchající protokolům (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 14db7019415405af89e9f5e317da617debeb0a19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-log-listeners-visual-basic"></a><span data-ttu-id="2dc4a-102">Řešení potíží: Součásti naslouchající protokolům (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2dc4a-102">Troubleshooting: Log Listeners (Visual Basic)</span></span>
<span data-ttu-id="2dc4a-103">Můžete použít `My.Application.Log` a `My.Log` objekty k protokolování informací o událostech, ke kterým dochází ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2dc4a-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span>  
  
 <span data-ttu-id="2dc4a-104">Pokud chcete zjistit, kteří posluchači přijímat zprávy, najdete v části [návod: určení kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="2dc4a-104">To determine which log listeners receive those messages, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
 <span data-ttu-id="2dc4a-105">`Log` Objekt můžete použít filtrování protokolu k omezení množství informací, které zaznamenává.</span><span class="sxs-lookup"><span data-stu-id="2dc4a-105">The `Log` object can use log filtering to limit the amount of information that it logs.</span></span> <span data-ttu-id="2dc4a-106">Pokud jsou špatně nakonfigurované filtry, protokol může obsahovat nesprávné informace.</span><span class="sxs-lookup"><span data-stu-id="2dc4a-106">If the filters are misconfigured, the logs might contain the wrong information.</span></span> <span data-ttu-id="2dc4a-107">Další informace o filtrování najdete v tématu [návod: filtrování výstupu My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="2dc4a-107">For more information about filtering, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>  
  
 <span data-ttu-id="2dc4a-108">Ale pokud protokolu není správně nakonfigurovaná, můžete další informace o své aktuální konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="2dc4a-108">However, if a log is configured incorrectly, you may need more information about its current configuration.</span></span> <span data-ttu-id="2dc4a-109">Můžete získat tyto informace prostřednictvím protokolu rozšířenou `TraceSource` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2dc4a-109">You can get to this information through the log's advanced `TraceSource` property.</span></span>  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a><span data-ttu-id="2dc4a-110">Chcete-li zjistit naslouchací procesy pro protokoly pro objekt protokolu v kódu</span><span class="sxs-lookup"><span data-stu-id="2dc4a-110">To determine the log listeners for the Log object in code</span></span>  
  
1.  <span data-ttu-id="2dc4a-111">Import <xref:System.Diagnostics> oboru názvů na začátku souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="2dc4a-111">Import the <xref:System.Diagnostics> namespace at the beginning of the code file.</span></span> <span data-ttu-id="2dc4a-112">Další informace najdete v tématu [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="2dc4a-112">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#13](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_1.vb)]  
  
2.  <span data-ttu-id="2dc4a-113">Vytvoří funkci, která vrátí řetězec, který se skládá z informace o pro všechny moduly pro naslouchání v protokolu.</span><span class="sxs-lookup"><span data-stu-id="2dc4a-113">Create a function that returns a string consisting of information for each of the log's listeners.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#14](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_2.vb)]  
  
3.  <span data-ttu-id="2dc4a-114">Předávání kolekce v protokolu trasování – moduly naslouchání na `GetListeners` funkce a zobrazit návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2dc4a-114">Pass the collection of the log's trace listeners to the `GetListeners` function, and display the return value.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#19](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_3.vb)]  
  
     <span data-ttu-id="2dc4a-115">Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="2dc4a-115">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dc4a-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="2dc4a-116">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [<span data-ttu-id="2dc4a-117">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="2dc4a-117">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="2dc4a-118">Návod: Zjištění, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="2dc4a-118">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
