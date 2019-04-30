---
title: 'Postupy: Výjimky protokolu v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
ms.openlocfilehash: 53bf93a326123ddb1e26ef5964fa057148505116
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934378"
---
# <a name="how-to-log-exceptions-in-visual-basic"></a><span data-ttu-id="8d5fd-102">Postupy: Výjimky protokolu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8d5fd-102">How to: Log Exceptions in Visual Basic</span></span>
<span data-ttu-id="8d5fd-103">Můžete použít `My.Application.Log` a `My.Log` objekty k protokolování informací o výjimkách, ke kterým dochází ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-103">You can use the `My.Application.Log` and `My.Log` objects to log information about exceptions that occur in your application.</span></span> <span data-ttu-id="8d5fd-104">Tyto příklady ukazují, jak používat `My.Application.Log.WriteException` metody do protokolu výjimky, které explicitně a výjimek, které nejsou zpracovány.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-104">These examples show how to use the `My.Application.Log.WriteException` method to log exceptions that you catch explicitly and exceptions that are unhandled.</span></span>  
  
 <span data-ttu-id="8d5fd-105">Protokolování informací o trasování, použijte `My.Application.Log.WriteEntry` metody.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-105">For logging tracing information, use the `My.Application.Log.WriteEntry` method.</span></span> <span data-ttu-id="8d5fd-106">Další informace najdete v tématu <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span><span class="sxs-lookup"><span data-stu-id="8d5fd-106">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span></span>  
  
### <a name="to-log-a-handled-exception"></a><span data-ttu-id="8d5fd-107">Do protokolu zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="8d5fd-107">To log a handled exception</span></span>  
  
1. <span data-ttu-id="8d5fd-108">Vytvořte metodu, která bude generovat informace o výjimce.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-108">Create the method that will generate the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#9)]  
  
2. <span data-ttu-id="8d5fd-109">Použití `Try...Catch` bloku pro zachycení výjimky.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-109">Use a `Try...Catch` block to catch the exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#6)]  
  
3. <span data-ttu-id="8d5fd-110">Vložte kód, který může způsobit výjimku v `Try` bloku.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-110">Put the code that could generate an exception in the `Try` block.</span></span>  
  
     <span data-ttu-id="8d5fd-111">Zrušením komentáře u `Dim` a `MsgBox` řádky způsobí <xref:System.NullReferenceException> výjimky.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-111">Uncomment the `Dim` and `MsgBox` lines to cause a <xref:System.NullReferenceException> exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#7)]  
  
4. <span data-ttu-id="8d5fd-112">V `Catch` zablokuje, použít `My.Application.Log.WriteException` metody zapsat informace o výjimce.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-112">In the `Catch` block, use the `My.Application.Log.WriteException` method to write the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#8)]  
  
     <span data-ttu-id="8d5fd-113">Následující příklad ukazuje kompletní kód pro protokolování zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-113">The following example shows the complete code for logging a handled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#10)]  
  
### <a name="to-log-an-unhandled-exception"></a><span data-ttu-id="8d5fd-114">K protokolování neošetřené výjimky</span><span class="sxs-lookup"><span data-stu-id="8d5fd-114">To log an unhandled exception</span></span>  
  
1. <span data-ttu-id="8d5fd-115">Mají projekt vybraný v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-115">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="8d5fd-116">Na **projektu** nabídce zvolte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-116">On the **Project** menu, choose **Properties**.</span></span>  
  
2. <span data-ttu-id="8d5fd-117">Klikněte na tlačítko **aplikace** kartu.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-117">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="8d5fd-118">Klikněte na tlačítko **zobrazení události aplikace** tlačítko k otevření editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-118">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="8d5fd-119">Tím se otevře soubor ApplicationEvents.vb.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-119">This opens the ApplicationEvents.vb file.</span></span>  
  
4. <span data-ttu-id="8d5fd-120">Máte ApplicationEvents.vb soubor otevřete v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-120">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="8d5fd-121">Na **Obecné** nabídce zvolte **události MyApplication**.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-121">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
5. <span data-ttu-id="8d5fd-122">Na **deklarace** nabídce zvolte **UnhandledException**.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-122">On the **Declarations** menu, choose **UnhandledException**.</span></span>  
  
     <span data-ttu-id="8d5fd-123">Aplikace vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> událostí před spuštěním hlavní aplikace.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-123">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> event before the main application runs.</span></span>  
  
6. <span data-ttu-id="8d5fd-124">Přidat `My.Application.Log.WriteException` metodu `UnhandledException` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-124">Add the `My.Application.Log.WriteException` method to the `UnhandledException` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#4)]  
  
     <span data-ttu-id="8d5fd-125">Následující příklad ukazuje kompletní kód pro protokolování neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-125">The following example shows the complete code for logging an unhandled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="8d5fd-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d5fd-126">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="8d5fd-127">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="8d5fd-127">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="8d5fd-128">Postupy: Zápis zpráv protokolu</span><span class="sxs-lookup"><span data-stu-id="8d5fd-128">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="8d5fd-129">Návod: Určení, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="8d5fd-129">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="8d5fd-130">Návod: Změna, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="8d5fd-130">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
