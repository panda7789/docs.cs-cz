---
title: 'Postupy: Zápis zpráv protokolu'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, writing log messages
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
ms.openlocfilehash: 38570047db48e009aea2af376304430db1ec29f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352060"
---
# <a name="how-to-write-log-messages-visual-basic"></a><span data-ttu-id="15650-102">Postupy: Zápis zpráv protokolu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15650-102">How to: Write Log Messages (Visual Basic)</span></span>

<span data-ttu-id="15650-103">Pomocí objektů `My.Application.Log` a `My.Log` můžete protokolovat informace o vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="15650-103">You can use the `My.Application.Log` and `My.Log` objects to log information about your application.</span></span> <span data-ttu-id="15650-104">Tento příklad ukazuje, jak použít `My.Application.Log.WriteEntry` metodu k protokolování informací o trasování.</span><span class="sxs-lookup"><span data-stu-id="15650-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information.</span></span>

<span data-ttu-id="15650-105">Pro protokolování informací o výjimce použijte `My.Application.Log.WriteException` metodu; viz [How to: log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="15650-105">For logging exception information, use the `My.Application.Log.WriteException` method; see [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>

## <a name="example"></a><span data-ttu-id="15650-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="15650-106">Example</span></span>

<span data-ttu-id="15650-107">Tento příklad používá `My.Application.Log.WriteEntry` metodu k vypsání informací o trasování.</span><span class="sxs-lookup"><span data-stu-id="15650-107">This example uses the `My.Application.Log.WriteEntry` method to write out the trace information.</span></span>

[!code-vb[VbVbalrMyApplicationLog#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#11)]

## <a name="net-framework-security"></a><span data-ttu-id="15650-108">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="15650-108">.NET Framework Security</span></span>

<span data-ttu-id="15650-109">Ujistěte se, že data, která do protokolu zapisujete, neobsahují citlivé informace, jako jsou uživatelská hesla.</span><span class="sxs-lookup"><span data-stu-id="15650-109">Make sure the data you write to the log does not include sensitive information such as user passwords.</span></span> <span data-ttu-id="15650-110">Další informace najdete v tématu [práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="15650-110">For more information, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="15650-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="15650-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="15650-112">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="15650-112">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="15650-113">Postupy: Protokolování výjimek</span><span class="sxs-lookup"><span data-stu-id="15650-113">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="15650-114">Návod: Zjištění, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="15650-114">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="15650-115">Návod: Změna místa, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="15650-115">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="15650-116">Návod: Filtrování výstupu My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="15650-116">Walkthrough: Filtering My.Application.Log Output</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)
