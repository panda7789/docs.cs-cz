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
# <a name="troubleshooting-log-listeners-visual-basic"></a><span data-ttu-id="07621-102">Řešení potíží: Součásti naslouchající protokolům (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07621-102">Troubleshooting: Log Listeners (Visual Basic)</span></span>

<span data-ttu-id="07621-103">Pomocí objektů `My.Application.Log` a `My.Log` můžete protokolovat informace o událostech, ke kterým dochází ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="07621-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span>  
  
 <span data-ttu-id="07621-104">Chcete-li zjistit, které naslouchací procesy protokolu obdrží tyto zprávy, přečtěte si [Návod: určení, kde my. Application. Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="07621-104">To determine which log listeners receive those messages, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
 <span data-ttu-id="07621-105">Objekt `Log` může použít filtrování protokolu k omezení množství informací, které protokoluje.</span><span class="sxs-lookup"><span data-stu-id="07621-105">The `Log` object can use log filtering to limit the amount of information that it logs.</span></span> <span data-ttu-id="07621-106">Pokud jsou filtry nesprávně nakonfigurované, můžou protokoly obsahovat nesprávné informace.</span><span class="sxs-lookup"><span data-stu-id="07621-106">If the filters are misconfigured, the logs might contain the wrong information.</span></span> <span data-ttu-id="07621-107">Další informace o filtrování najdete v tématu [Návod: filtrování výstupu my. Application. log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="07621-107">For more information about filtering, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>  
  
 <span data-ttu-id="07621-108">Pokud je ale protokol nesprávně nakonfigurovaný, možná budete potřebovat další informace o jeho aktuální konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="07621-108">However, if a log is configured incorrectly, you may need more information about its current configuration.</span></span> <span data-ttu-id="07621-109">K těmto informacím se můžete dostat prostřednictvím vlastnosti rozšířené `TraceSource` protokolu.</span><span class="sxs-lookup"><span data-stu-id="07621-109">You can get to this information through the log's advanced `TraceSource` property.</span></span>  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a><span data-ttu-id="07621-110">Určení naslouchacího procesu protokolu pro objekt log v kódu</span><span class="sxs-lookup"><span data-stu-id="07621-110">To determine the log listeners for the Log object in code</span></span>  
  
1. <span data-ttu-id="07621-111">Importujte <xref:System.Diagnostics> obor názvů na začátek souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="07621-111">Import the <xref:System.Diagnostics> namespace at the beginning of the code file.</span></span> <span data-ttu-id="07621-112">Další informace naleznete v tématu [příkaz Imports (obor názvů a typ rozhraní .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="07621-112">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#13)]  
  
2. <span data-ttu-id="07621-113">Vytvořte funkci, která vrátí řetězec skládající se z informací pro každý naslouchací proces protokolu.</span><span class="sxs-lookup"><span data-stu-id="07621-113">Create a function that returns a string consisting of information for each of the log's listeners.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#14)]  
  
3. <span data-ttu-id="07621-114">Předejte kolekci posluchačů trasování protokolu do funkce `GetListeners` a zobrazte návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="07621-114">Pass the collection of the log's trace listeners to the `GetListeners` function, and display the return value.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#19)]  
  
     <span data-ttu-id="07621-115">Další informace najdete v tématu <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="07621-115">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07621-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="07621-116">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="07621-117">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="07621-117">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="07621-118">Návod: Zjištění, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="07621-118">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
