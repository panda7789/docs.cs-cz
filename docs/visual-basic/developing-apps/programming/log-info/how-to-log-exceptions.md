---
title: 'Postupy: Protokolování výjimek v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
ms.openlocfilehash: b8ec45f43438f8181d9e045cdf43c81db34e4242
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588523"
---
# <a name="how-to-log-exceptions-in-visual-basic"></a><span data-ttu-id="c16fa-102">Postupy: Protokolování výjimek v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c16fa-102">How to: Log Exceptions in Visual Basic</span></span>
<span data-ttu-id="c16fa-103">Můžete použít `My.Application.Log` a `My.Log` objekty k protokolování informací o výjimkách, ke kterým dochází ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c16fa-103">You can use the `My.Application.Log` and `My.Log` objects to log information about exceptions that occur in your application.</span></span> <span data-ttu-id="c16fa-104">Tyto příklady ukazují, jak používat `My.Application.Log.WriteException` metoda do protokolu explicitně a výjimek, které nejsou zpracovány.</span><span class="sxs-lookup"><span data-stu-id="c16fa-104">These examples show how to use the `My.Application.Log.WriteException` method to log exceptions that you catch explicitly and exceptions that are unhandled.</span></span>  
  
 <span data-ttu-id="c16fa-105">Protokolování informací o trasování, použijte `My.Application.Log.WriteEntry` metoda.</span><span class="sxs-lookup"><span data-stu-id="c16fa-105">For logging tracing information, use the `My.Application.Log.WriteEntry` method.</span></span> <span data-ttu-id="c16fa-106">Další informace najdete v tématu <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span><span class="sxs-lookup"><span data-stu-id="c16fa-106">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span></span>  
  
### <a name="to-log-a-handled-exception"></a><span data-ttu-id="c16fa-107">Do protokolu zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="c16fa-107">To log a handled exception</span></span>  
  
1.  <span data-ttu-id="c16fa-108">Vytvořte metodu, která bude generovat informace o výjimce.</span><span class="sxs-lookup"><span data-stu-id="c16fa-108">Create the method that will generate the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#9](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_1.vb)]  
  
2.  <span data-ttu-id="c16fa-109">Použití `Try...Catch` blok k zachycení výjimky.</span><span class="sxs-lookup"><span data-stu-id="c16fa-109">Use a `Try...Catch` block to catch the exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#6](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_2.vb)]  
  
3.  <span data-ttu-id="c16fa-110">Vložit kód, který může generovat výjimky v `Try` bloku.</span><span class="sxs-lookup"><span data-stu-id="c16fa-110">Put the code that could generate an exception in the `Try` block.</span></span>  
  
     <span data-ttu-id="c16fa-111">Zrušením komentáře u `Dim` a `MsgBox` řádky způsobí <xref:System.NullReferenceException> výjimka.</span><span class="sxs-lookup"><span data-stu-id="c16fa-111">Uncomment the `Dim` and `MsgBox` lines to cause a <xref:System.NullReferenceException> exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#7](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_3.vb)]  
  
4.  <span data-ttu-id="c16fa-112">V `Catch` blokovat, použijte `My.Application.Log.WriteException` metoda zapsat informace o výjimce.</span><span class="sxs-lookup"><span data-stu-id="c16fa-112">In the `Catch` block, use the `My.Application.Log.WriteException` method to write the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#8](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_4.vb)]  
  
     <span data-ttu-id="c16fa-113">Následující příklad ukazuje kód dokončení pro protokolování zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="c16fa-113">The following example shows the complete code for logging a handled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#10](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_5.vb)]  
  
### <a name="to-log-an-unhandled-exception"></a><span data-ttu-id="c16fa-114">K přihlášení k neošetřené výjimce</span><span class="sxs-lookup"><span data-stu-id="c16fa-114">To log an unhandled exception</span></span>  
  
1.  <span data-ttu-id="c16fa-115">Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="c16fa-115">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="c16fa-116">Na **projektu** nabídce zvolte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="c16fa-116">On the **Project** menu, choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="c16fa-117">Klikněte **aplikace** kartě.</span><span class="sxs-lookup"><span data-stu-id="c16fa-117">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="c16fa-118">Klikněte **zobrazení události aplikace** tlačítko otevřete Editor kódu.</span><span class="sxs-lookup"><span data-stu-id="c16fa-118">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="c16fa-119">Otevře se soubor ApplicationEvents.vb.</span><span class="sxs-lookup"><span data-stu-id="c16fa-119">This opens the ApplicationEvents.vb file.</span></span>  
  
4.  <span data-ttu-id="c16fa-120">Byl ApplicationEvents.vb otevřen v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="c16fa-120">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="c16fa-121">Na **Obecné** nabídce zvolte **Moje_aplikace události**.</span><span class="sxs-lookup"><span data-stu-id="c16fa-121">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
5.  <span data-ttu-id="c16fa-122">Na **deklarace** nabídce zvolte **UnhandledException**.</span><span class="sxs-lookup"><span data-stu-id="c16fa-122">On the **Declarations** menu, choose **UnhandledException**.</span></span>  
  
     <span data-ttu-id="c16fa-123">Aplikace vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> událostí před spuštěním hlavní aplikace.</span><span class="sxs-lookup"><span data-stu-id="c16fa-123">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> event before the main application runs.</span></span>  
  
6.  <span data-ttu-id="c16fa-124">Přidat `My.Application.Log.WriteException` metodu `UnhandledException` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="c16fa-124">Add the `My.Application.Log.WriteException` method to the `UnhandledException` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#4](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_6.vb)]  
  
     <span data-ttu-id="c16fa-125">Následující příklad ukazuje kód dokončení pro protokolování neošetřené výjimky.</span><span class="sxs-lookup"><span data-stu-id="c16fa-125">The following example shows the complete code for logging an unhandled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#5](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_7.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c16fa-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="c16fa-126">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [<span data-ttu-id="c16fa-127">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="c16fa-127">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="c16fa-128">Postupy: Zápis zpráv protokolu</span><span class="sxs-lookup"><span data-stu-id="c16fa-128">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [<span data-ttu-id="c16fa-129">Návod: Zjištění, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="c16fa-129">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)  
 [<span data-ttu-id="c16fa-130">Návod: Změna místa, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="c16fa-130">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
