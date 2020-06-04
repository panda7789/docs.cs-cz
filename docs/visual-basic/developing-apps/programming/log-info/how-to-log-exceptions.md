---
title: 'Postupy: Protokolování výjimek'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
ms.openlocfilehash: 59ed7b836126a38f32b7c6f479570a566d236e6c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410111"
---
# <a name="how-to-log-exceptions-in-visual-basic"></a><span data-ttu-id="3e954-102">Postupy: Protokolování výjimek v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3e954-102">How to: Log Exceptions in Visual Basic</span></span>

<span data-ttu-id="3e954-103">Pomocí `My.Application.Log` objektů a můžete `My.Log` protokolovat informace o výjimkách, ke kterým dochází ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3e954-103">You can use the `My.Application.Log` and `My.Log` objects to log information about exceptions that occur in your application.</span></span> <span data-ttu-id="3e954-104">Tyto příklady ukazují, jak použít `My.Application.Log.WriteException` metodu k protokolování výjimek, které jsou zachyceny explicitně a výjimek, které jsou neošetřené.</span><span class="sxs-lookup"><span data-stu-id="3e954-104">These examples show how to use the `My.Application.Log.WriteException` method to log exceptions that you catch explicitly and exceptions that are unhandled.</span></span>  
  
 <span data-ttu-id="3e954-105">Pro informace o trasování protokolu použijte `My.Application.Log.WriteEntry` metodu.</span><span class="sxs-lookup"><span data-stu-id="3e954-105">For logging tracing information, use the `My.Application.Log.WriteEntry` method.</span></span> <span data-ttu-id="3e954-106">Další informace najdete v tématu <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>.</span><span class="sxs-lookup"><span data-stu-id="3e954-106">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span></span>  
  
### <a name="to-log-a-handled-exception"></a><span data-ttu-id="3e954-107">Protokolování ošetřené výjimky</span><span class="sxs-lookup"><span data-stu-id="3e954-107">To log a handled exception</span></span>  
  
1. <span data-ttu-id="3e954-108">Vytvořte metodu, která bude generovat informace o výjimce.</span><span class="sxs-lookup"><span data-stu-id="3e954-108">Create the method that will generate the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#9)]  
  
2. <span data-ttu-id="3e954-109">`Try...Catch`K zachycení výjimky použijte blok.</span><span class="sxs-lookup"><span data-stu-id="3e954-109">Use a `Try...Catch` block to catch the exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#6)]  
  
3. <span data-ttu-id="3e954-110">Vložte kód, který by mohl vytvořit výjimku v `Try` bloku.</span><span class="sxs-lookup"><span data-stu-id="3e954-110">Put the code that could generate an exception in the `Try` block.</span></span>  
  
     <span data-ttu-id="3e954-111">Odkomentujte `Dim` řádky a, `MsgBox` abyste způsobili <xref:System.NullReferenceException> výjimku.</span><span class="sxs-lookup"><span data-stu-id="3e954-111">Uncomment the `Dim` and `MsgBox` lines to cause a <xref:System.NullReferenceException> exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#7)]  
  
4. <span data-ttu-id="3e954-112">V `Catch` bloku použijte `My.Application.Log.WriteException` metodu k zápisu informací o výjimce.</span><span class="sxs-lookup"><span data-stu-id="3e954-112">In the `Catch` block, use the `My.Application.Log.WriteException` method to write the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#8)]  
  
     <span data-ttu-id="3e954-113">Následující příklad ukazuje úplný kód pro protokolování ošetřené výjimky.</span><span class="sxs-lookup"><span data-stu-id="3e954-113">The following example shows the complete code for logging a handled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#10)]  
  
### <a name="to-log-an-unhandled-exception"></a><span data-ttu-id="3e954-114">Postup při protokolování neošetřené výjimky</span><span class="sxs-lookup"><span data-stu-id="3e954-114">To log an unhandled exception</span></span>  
  
1. <span data-ttu-id="3e954-115">Máte projekt vybraný v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="3e954-115">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="3e954-116">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="3e954-116">On the **Project** menu, choose **Properties**.</span></span>  
  
2. <span data-ttu-id="3e954-117">Klikněte na kartu **aplikace** .</span><span class="sxs-lookup"><span data-stu-id="3e954-117">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="3e954-118">Kliknutím na tlačítko **Zobrazit události aplikace** otevřete Editor kódu.</span><span class="sxs-lookup"><span data-stu-id="3e954-118">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="3e954-119">Tím se otevře soubor ApplicationEvents. vb.</span><span class="sxs-lookup"><span data-stu-id="3e954-119">This opens the ApplicationEvents.vb file.</span></span>  
  
4. <span data-ttu-id="3e954-120">Otevřete soubor ApplicationEvents. vb v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="3e954-120">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="3e954-121">V nabídce **Obecné** vyberte **události MyApplication**.</span><span class="sxs-lookup"><span data-stu-id="3e954-121">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
5. <span data-ttu-id="3e954-122">V nabídce **deklarace** vyberte možnost **UnhandledException**.</span><span class="sxs-lookup"><span data-stu-id="3e954-122">On the **Declarations** menu, choose **UnhandledException**.</span></span>  
  
     <span data-ttu-id="3e954-123">Aplikace vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> událost před spuštěním hlavní aplikace.</span><span class="sxs-lookup"><span data-stu-id="3e954-123">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> event before the main application runs.</span></span>  
  
6. <span data-ttu-id="3e954-124">Přidejte `My.Application.Log.WriteException` metodu do `UnhandledException` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="3e954-124">Add the `My.Application.Log.WriteException` method to the `UnhandledException` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#4)]  
  
     <span data-ttu-id="3e954-125">Následující příklad ukazuje úplný kód pro protokolování neošetřené výjimky.</span><span class="sxs-lookup"><span data-stu-id="3e954-125">The following example shows the complete code for logging an unhandled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="3e954-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="3e954-126">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="3e954-127">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="3e954-127">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="3e954-128">Postupy: Zápis zpráv protokolu</span><span class="sxs-lookup"><span data-stu-id="3e954-128">How to: Write Log Messages</span></span>](how-to-write-log-messages.md)
- [<span data-ttu-id="3e954-129">Návod: Zjištění, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="3e954-129">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="3e954-130">Návod: Změna místa, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="3e954-130">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](walkthrough-changing-where-my-application-log-writes-information.md)
