---
title: "Postupy: Zápis zpráv protokolu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Application.Log object, writing log messags
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ae4d875fd4f95ca51fff565551009e780b17d07a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-log-messages-visual-basic"></a><span data-ttu-id="ebce3-102">Postupy: Zápis zpráv protokolu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ebce3-102">How to: Write Log Messages (Visual Basic)</span></span>
<span data-ttu-id="ebce3-103">Můžete použít `My.Application.Log` a `My.Log` objekty do protokolu informace o vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ebce3-103">You can use the `My.Application.Log` and `My.Log` objects to log information about your application.</span></span> <span data-ttu-id="ebce3-104">Tento příklad ukazuje způsob použití `My.Application.Log.WriteEntry` metoda do protokolu informace o trasování.</span><span class="sxs-lookup"><span data-stu-id="ebce3-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information.</span></span>  
  
 <span data-ttu-id="ebce3-105">K protokolování informací o výjimce, použijte `My.Application.Log.WriteException` metoda; viz [postup: výjimky protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="ebce3-105">For logging exception information, use the `My.Application.Log.WriteException` method; see [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ebce3-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="ebce3-106">Example</span></span>  
 <span data-ttu-id="ebce3-107">Tento příklad používá `My.Application.Log.WriteEntry` metoda k zapsání informací o trasování.</span><span class="sxs-lookup"><span data-stu-id="ebce3-107">This example uses the `My.Application.Log.WriteEntry` method to write out the trace information.</span></span>  
  
 [!code-vb[VbVbalrMyApplicationLog#11](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-write-log-messages_1.vb)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="ebce3-108">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ebce3-108">.NET Framework Security</span></span>  
 <span data-ttu-id="ebce3-109">Ujistěte se, že data, která se zapisují do protokolu neobsahuje citlivé informace, jako jsou hesla uživatele.</span><span class="sxs-lookup"><span data-stu-id="ebce3-109">Make sure the data you write to the log does not include sensitive information such as user passwords.</span></span> <span data-ttu-id="ebce3-110">Další informace najdete v tématu [práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="ebce3-110">For more information, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebce3-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="ebce3-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [<span data-ttu-id="ebce3-112">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="ebce3-112">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="ebce3-113">Postupy: protokolování výjimek</span><span class="sxs-lookup"><span data-stu-id="ebce3-113">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)  
 [<span data-ttu-id="ebce3-114">Návod: Zjištění, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="ebce3-114">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)  
 [<span data-ttu-id="ebce3-115">Návod: Změna místa, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="ebce3-115">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)  
 [<span data-ttu-id="ebce3-116">Návod: Filtrování výstupu My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="ebce3-116">Walkthrough: Filtering My.Application.Log Output</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)
