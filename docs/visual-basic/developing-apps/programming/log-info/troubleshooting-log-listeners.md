---
title: 'Řešení potíží: Součásti naslouchající protokolům'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
ms.openlocfilehash: dd139935dae7fe4d1334b861e6590df29bab7202
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346859"
---
# <a name="troubleshooting-log-listeners-visual-basic"></a><span data-ttu-id="85b49-102">Řešení potíží: Součásti naslouchající protokolům (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85b49-102">Troubleshooting: Log Listeners (Visual Basic)</span></span>

<span data-ttu-id="85b49-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span><span class="sxs-lookup"><span data-stu-id="85b49-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span>  
  
 <span data-ttu-id="85b49-104">To determine which log listeners receive those messages, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="85b49-104">To determine which log listeners receive those messages, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
 <span data-ttu-id="85b49-105">The `Log` object can use log filtering to limit the amount of information that it logs.</span><span class="sxs-lookup"><span data-stu-id="85b49-105">The `Log` object can use log filtering to limit the amount of information that it logs.</span></span> <span data-ttu-id="85b49-106">If the filters are misconfigured, the logs might contain the wrong information.</span><span class="sxs-lookup"><span data-stu-id="85b49-106">If the filters are misconfigured, the logs might contain the wrong information.</span></span> <span data-ttu-id="85b49-107">For more information about filtering, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="85b49-107">For more information about filtering, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>  
  
 <span data-ttu-id="85b49-108">However, if a log is configured incorrectly, you may need more information about its current configuration.</span><span class="sxs-lookup"><span data-stu-id="85b49-108">However, if a log is configured incorrectly, you may need more information about its current configuration.</span></span> <span data-ttu-id="85b49-109">You can get to this information through the log's advanced `TraceSource` property.</span><span class="sxs-lookup"><span data-stu-id="85b49-109">You can get to this information through the log's advanced `TraceSource` property.</span></span>  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a><span data-ttu-id="85b49-110">To determine the log listeners for the Log object in code</span><span class="sxs-lookup"><span data-stu-id="85b49-110">To determine the log listeners for the Log object in code</span></span>  
  
1. <span data-ttu-id="85b49-111">Import the <xref:System.Diagnostics> namespace at the beginning of the code file.</span><span class="sxs-lookup"><span data-stu-id="85b49-111">Import the <xref:System.Diagnostics> namespace at the beginning of the code file.</span></span> <span data-ttu-id="85b49-112">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="85b49-112">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#13)]  
  
2. <span data-ttu-id="85b49-113">Create a function that returns a string consisting of information for each of the log's listeners.</span><span class="sxs-lookup"><span data-stu-id="85b49-113">Create a function that returns a string consisting of information for each of the log's listeners.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#14)]  
  
3. <span data-ttu-id="85b49-114">Pass the collection of the log's trace listeners to the `GetListeners` function, and display the return value.</span><span class="sxs-lookup"><span data-stu-id="85b49-114">Pass the collection of the log's trace listeners to the `GetListeners` function, and display the return value.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#19)]  
  
     <span data-ttu-id="85b49-115">Další informace najdete v tématu <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="85b49-115">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85b49-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85b49-116">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="85b49-117">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="85b49-117">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="85b49-118">Návod: Zjištění, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="85b49-118">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
