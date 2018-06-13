---
title: 'Postupy: Zápis zpráv protokolu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, writing log messags
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
ms.openlocfilehash: 8b0d50e70572d849f20f01914d2380a64e4495a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587756"
---
# <a name="how-to-write-log-messages-visual-basic"></a><span data-ttu-id="7c991-102">Postupy: Zápis zpráv protokolu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c991-102">How to: Write Log Messages (Visual Basic)</span></span>
<span data-ttu-id="7c991-103">Můžete použít `My.Application.Log` a `My.Log` objekty do protokolu informace o vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7c991-103">You can use the `My.Application.Log` and `My.Log` objects to log information about your application.</span></span> <span data-ttu-id="7c991-104">Tento příklad ukazuje způsob použití `My.Application.Log.WriteEntry` metoda do protokolu informace o trasování.</span><span class="sxs-lookup"><span data-stu-id="7c991-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information.</span></span>  
  
 <span data-ttu-id="7c991-105">K protokolování informací o výjimce, použijte `My.Application.Log.WriteException` metoda; viz [postup: výjimky protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="7c991-105">For logging exception information, use the `My.Application.Log.WriteException` method; see [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c991-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="7c991-106">Example</span></span>  
 <span data-ttu-id="7c991-107">Tento příklad používá `My.Application.Log.WriteEntry` metoda k zapsání informací o trasování.</span><span class="sxs-lookup"><span data-stu-id="7c991-107">This example uses the `My.Application.Log.WriteEntry` method to write out the trace information.</span></span>  
  
 [!code-vb[VbVbalrMyApplicationLog#11](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-write-log-messages_1.vb)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="7c991-108">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7c991-108">.NET Framework Security</span></span>  
 <span data-ttu-id="7c991-109">Ujistěte se, že data, která se zapisují do protokolu neobsahuje citlivé informace, jako jsou hesla uživatele.</span><span class="sxs-lookup"><span data-stu-id="7c991-109">Make sure the data you write to the log does not include sensitive information such as user passwords.</span></span> <span data-ttu-id="7c991-110">Další informace najdete v tématu [práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="7c991-110">For more information, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c991-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c991-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [<span data-ttu-id="7c991-112">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="7c991-112">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="7c991-113">Postupy: Protokolování výjimek</span><span class="sxs-lookup"><span data-stu-id="7c991-113">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)  
 [<span data-ttu-id="7c991-114">Návod: Zjištění, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="7c991-114">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)  
 [<span data-ttu-id="7c991-115">Návod: Změna místa, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="7c991-115">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)  
 [<span data-ttu-id="7c991-116">Návod: Filtrování výstupu My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="7c991-116">Walkthrough: Filtering My.Application.Log Output</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)
