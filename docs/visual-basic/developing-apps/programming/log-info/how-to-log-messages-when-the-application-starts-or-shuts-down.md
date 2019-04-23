---
title: 'Postupy: Protokolování zpráv při spuštění aplikace nebo jejím ukončení (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event [Visual Basic]
- event logs, startup
- Shutdown event [Visual Basic]
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
ms.openlocfilehash: 8fc7b441c6e19d70ceefa3422cf9823007280b64
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59330568"
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a><span data-ttu-id="7c1b6-102">Postupy: Protokolování zpráv při spuštění aplikace nebo jejím ukončení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c1b6-102">How to: Log Messages When the Application Starts or Shuts Down (Visual Basic)</span></span>
<span data-ttu-id="7c1b6-103">Můžete použít `My.Application.Log` a `My.Log` objekty k protokolování informací o události, ke kterým dochází ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7c1b6-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="7c1b6-104">Tento příklad ukazuje způsob použití `My.Application.Log.WriteEntry` metodou `Startup` a `Shutdown` události zapsat informace trasování.</span><span class="sxs-lookup"><span data-stu-id="7c1b6-104">This example shows how to use the `My.Application.Log.WriteEntry` method with the `Startup` and `Shutdown` events to write tracing information.</span></span>  
  
### <a name="to-access-the-applications-event-handler-code"></a><span data-ttu-id="7c1b6-105">Přístup ke kódu obslužnou rutinu události aplikace</span><span class="sxs-lookup"><span data-stu-id="7c1b6-105">To access the application's event-handler code</span></span>  
  
1. <span data-ttu-id="7c1b6-106">Mají projekt vybraný v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="7c1b6-106">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="7c1b6-107">Na **projektu** nabídce zvolte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="7c1b6-107">On the **Project** menu, choose **Properties**.</span></span>  
  
2. <span data-ttu-id="7c1b6-108">Klikněte na tlačítko **aplikace** kartu.</span><span class="sxs-lookup"><span data-stu-id="7c1b6-108">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="7c1b6-109">Klikněte na tlačítko **zobrazení události aplikace** tlačítko k otevření editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="7c1b6-109">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="7c1b6-110">Tím se otevře soubor ApplicationEvents.vb.</span><span class="sxs-lookup"><span data-stu-id="7c1b6-110">This opens the ApplicationEvents.vb file.</span></span>  
  
### <a name="to-log-messages-when-the-application-starts"></a><span data-ttu-id="7c1b6-111">Protokolování zpráv při spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="7c1b6-111">To log messages when the application starts</span></span>  
  
1. <span data-ttu-id="7c1b6-112">Máte ApplicationEvents.vb soubor otevřete v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="7c1b6-112">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="7c1b6-113">Na **Obecné** nabídce zvolte **události MyApplication**.</span><span class="sxs-lookup"><span data-stu-id="7c1b6-113">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2. <span data-ttu-id="7c1b6-114">Na **deklarace** nabídce zvolte **spuštění**.</span><span class="sxs-lookup"><span data-stu-id="7c1b6-114">On the **Declarations** menu, choose **Startup**.</span></span>  
  
     <span data-ttu-id="7c1b6-115">Aplikace vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> událostí před spuštěním hlavní aplikace.</span><span class="sxs-lookup"><span data-stu-id="7c1b6-115">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> event before the main application runs.</span></span>  
  
3. <span data-ttu-id="7c1b6-116">Přidat `My.Application.Log.WriteEntry` metodu `Startup` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="7c1b6-116">Add the `My.Application.Log.WriteEntry` method to the `Startup` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#1)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a><span data-ttu-id="7c1b6-117">Protokolování zpráv při ukončení aplikace</span><span class="sxs-lookup"><span data-stu-id="7c1b6-117">To log messages when the application shuts down</span></span>  
  
1. <span data-ttu-id="7c1b6-118">Máte ApplicationEvents.vb soubor otevřete v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="7c1b6-118">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="7c1b6-119">Na **Obecné** nabídce zvolte **události MyApplication**.</span><span class="sxs-lookup"><span data-stu-id="7c1b6-119">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2. <span data-ttu-id="7c1b6-120">Na **deklarace** nabídce zvolte **vypnutí**.</span><span class="sxs-lookup"><span data-stu-id="7c1b6-120">On the **Declarations** menu, choose **Shutdown**.</span></span>  
  
     <span data-ttu-id="7c1b6-121">Aplikace vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> událostí po spuštění hlavní aplikace, ale předtím, než ho ukončí.</span><span class="sxs-lookup"><span data-stu-id="7c1b6-121">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> event after the main application runs, but before it shuts down.</span></span>  
  
3. <span data-ttu-id="7c1b6-122">Přidat `My.Application.Log.WriteEntry` metodu `Shutdown` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="7c1b6-122">Add the `My.Application.Log.WriteEntry` method to the `Shutdown` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="7c1b6-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="7c1b6-123">Example</span></span>  
 <span data-ttu-id="7c1b6-124">Můžete použít **Návrháře projektu** přistupovat k událostem aplikace v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="7c1b6-124">You can use the **Project Designer** to access the application events in the Code Editor.</span></span> <span data-ttu-id="7c1b6-125">Další informace najdete v tématu [stránka aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="7c1b6-125">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 [!code-vb[VbVbalrMyApplicationLog#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="7c1b6-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7c1b6-126">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="7c1b6-127">Stránka Aplikace, Návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c1b6-127">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="7c1b6-128">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="7c1b6-128">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
