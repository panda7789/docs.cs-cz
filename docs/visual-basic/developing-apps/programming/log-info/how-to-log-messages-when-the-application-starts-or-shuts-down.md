---
title: "Postupy: Protokolování zpráv při spuštění nebo ukončení aplikace (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event [Visual Basic]
- event logs, startup
- Shutdown event [Visual Basic]
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 16235e245fd71f16edb67003cf237bcee3a6855e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a><span data-ttu-id="a5ebb-102">Postupy: Protokolování zpráv při spuštění nebo ukončení aplikace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5ebb-102">How to: Log Messages When the Application Starts or Shuts Down (Visual Basic)</span></span>
<span data-ttu-id="a5ebb-103">Můžete použít `My.Application.Log` a `My.Log` objekty k protokolování informací o událostech, ke kterým dochází ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a5ebb-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="a5ebb-104">Tento příklad ukazuje způsob použití `My.Application.Log.WriteEntry` metoda s `Startup` a `Shutdown` události zapsat informace trasování.</span><span class="sxs-lookup"><span data-stu-id="a5ebb-104">This example shows how to use the `My.Application.Log.WriteEntry` method with the `Startup` and `Shutdown` events to write tracing information.</span></span>  
  
### <a name="to-access-the-applications-event-handler-code"></a><span data-ttu-id="a5ebb-105">Pro přístup kód obslužné rutiny události aplikace</span><span class="sxs-lookup"><span data-stu-id="a5ebb-105">To access the application's event-handler code</span></span>  
  
1.  <span data-ttu-id="a5ebb-106">Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="a5ebb-106">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="a5ebb-107">Na **projektu** nabídce zvolte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="a5ebb-107">On the **Project** menu, choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="a5ebb-108">Klikněte **aplikace** kartě.</span><span class="sxs-lookup"><span data-stu-id="a5ebb-108">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="a5ebb-109">Klikněte **zobrazení události aplikace** tlačítko otevřete Editor kódu.</span><span class="sxs-lookup"><span data-stu-id="a5ebb-109">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="a5ebb-110">Otevře se soubor ApplicationEvents.vb.</span><span class="sxs-lookup"><span data-stu-id="a5ebb-110">This opens the ApplicationEvents.vb file.</span></span>  
  
### <a name="to-log-messages-when-the-application-starts"></a><span data-ttu-id="a5ebb-111">Protokolování zpráv při spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="a5ebb-111">To log messages when the application starts</span></span>  
  
1.  <span data-ttu-id="a5ebb-112">Byl ApplicationEvents.vb otevřen v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="a5ebb-112">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="a5ebb-113">Na **Obecné** nabídce zvolte **Moje_aplikace události**.</span><span class="sxs-lookup"><span data-stu-id="a5ebb-113">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2.  <span data-ttu-id="a5ebb-114">Na **deklarace** nabídce zvolte **spuštění**.</span><span class="sxs-lookup"><span data-stu-id="a5ebb-114">On the **Declarations** menu, choose **Startup**.</span></span>  
  
     <span data-ttu-id="a5ebb-115">Aplikace vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> událostí před spuštěním hlavní aplikace.</span><span class="sxs-lookup"><span data-stu-id="a5ebb-115">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> event before the main application runs.</span></span>  
  
3.  <span data-ttu-id="a5ebb-116">Přidat `My.Application.Log.WriteEntry` metodu `Startup` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="a5ebb-116">Add the `My.Application.Log.WriteEntry` method to the `Startup` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#1](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_1.vb)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a><span data-ttu-id="a5ebb-117">Protokolování zpráv při vypnutí aplikace</span><span class="sxs-lookup"><span data-stu-id="a5ebb-117">To log messages when the application shuts down</span></span>  
  
1.  <span data-ttu-id="a5ebb-118">Byl ApplicationEvents.vb otevřen v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="a5ebb-118">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="a5ebb-119">Na **Obecné** nabídce zvolte **Moje_aplikace události**.</span><span class="sxs-lookup"><span data-stu-id="a5ebb-119">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2.  <span data-ttu-id="a5ebb-120">Na **deklarace** nabídce zvolte **vypnutí**.</span><span class="sxs-lookup"><span data-stu-id="a5ebb-120">On the **Declarations** menu, choose **Shutdown**.</span></span>  
  
     <span data-ttu-id="a5ebb-121">Aplikace vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> událostí po spustí hlavní aplikace, ale předtím, než ho ukončí.</span><span class="sxs-lookup"><span data-stu-id="a5ebb-121">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> event after the main application runs, but before it shuts down.</span></span>  
  
3.  <span data-ttu-id="a5ebb-122">Přidat `My.Application.Log.WriteEntry` metodu `Shutdown` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="a5ebb-122">Add the `My.Application.Log.WriteEntry` method to the `Shutdown` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#2](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="a5ebb-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="a5ebb-123">Example</span></span>  
 <span data-ttu-id="a5ebb-124">Můžete použít **Návrhář projektu** přistupovat k událostem aplikace v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="a5ebb-124">You can use the **Project Designer** to access the application events in the Code Editor.</span></span> <span data-ttu-id="a5ebb-125">Další informace najdete v tématu [stránka aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="a5ebb-125">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 [!code-vb[VbVbalrMyApplicationLog#3](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a5ebb-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="a5ebb-126">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [<span data-ttu-id="a5ebb-127">Stránka aplikace, Návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5ebb-127">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [<span data-ttu-id="a5ebb-128">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="a5ebb-128">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
