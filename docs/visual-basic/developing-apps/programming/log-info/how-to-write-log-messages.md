---
title: 'Postupy: Zápis zpráv protokolu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, writing log messages
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
ms.openlocfilehash: 007d08917ed5ecae6889d03d820d48e4695c9344
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57676119"
---
# <a name="how-to-write-log-messages-visual-basic"></a><span data-ttu-id="c96a1-102">Postupy: Zápis zpráv protokolu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c96a1-102">How to: Write Log Messages (Visual Basic)</span></span>

<span data-ttu-id="c96a1-103">Můžete použít `My.Application.Log` a `My.Log` objekty k protokolování informací o vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c96a1-103">You can use the `My.Application.Log` and `My.Log` objects to log information about your application.</span></span> <span data-ttu-id="c96a1-104">Tento příklad ukazuje způsob použití `My.Application.Log.WriteEntry` metody do protokolu informace o trasování.</span><span class="sxs-lookup"><span data-stu-id="c96a1-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information.</span></span>

<span data-ttu-id="c96a1-105">Protokolování informací o výjimce, použijte `My.Application.Log.WriteException` metoda; viz [jak: Protokolování výjimek](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="c96a1-105">For logging exception information, use the `My.Application.Log.WriteException` method; see [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>

## <a name="example"></a><span data-ttu-id="c96a1-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="c96a1-106">Example</span></span>

<span data-ttu-id="c96a1-107">V tomto příkladu `My.Application.Log.WriteEntry` metody zapsat informace trasování.</span><span class="sxs-lookup"><span data-stu-id="c96a1-107">This example uses the `My.Application.Log.WriteEntry` method to write out the trace information.</span></span>

[!code-vb[VbVbalrMyApplicationLog#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#11)]

## <a name="net-framework-security"></a><span data-ttu-id="c96a1-108">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c96a1-108">.NET Framework Security</span></span>

<span data-ttu-id="c96a1-109">Ujistěte se, že data, která se zaznamená do protokolu neobsahuje citlivé informace, jako jsou hesla uživatele.</span><span class="sxs-lookup"><span data-stu-id="c96a1-109">Make sure the data you write to the log does not include sensitive information such as user passwords.</span></span> <span data-ttu-id="c96a1-110">Další informace najdete v tématu [práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="c96a1-110">For more information, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c96a1-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c96a1-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="c96a1-112">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="c96a1-112">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="c96a1-113">Postupy: Výjimky protokolu</span><span class="sxs-lookup"><span data-stu-id="c96a1-113">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="c96a1-114">Návod: Určení, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="c96a1-114">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="c96a1-115">Návod: Změna, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="c96a1-115">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="c96a1-116">Návod: Filtrování výstupu My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="c96a1-116">Walkthrough: Filtering My.Application.Log Output</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)
