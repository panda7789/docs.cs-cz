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
ms.openlocfilehash: 20eabd08db0763ec08bb28add41ff63fa3196dd6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585627"
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a><span data-ttu-id="ba31f-102">Postupy: Protokolování zpráv při spuštění aplikace nebo jejím ukončení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba31f-102">How to: Log Messages When the Application Starts or Shuts Down (Visual Basic)</span></span>
<span data-ttu-id="ba31f-103">Můžete použít `My.Application.Log` a `My.Log` objekty k protokolování informací o události, ke kterým dochází ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ba31f-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="ba31f-104">Tento příklad ukazuje způsob použití `My.Application.Log.WriteEntry` metodou `Startup` a `Shutdown` události zapsat informace trasování.</span><span class="sxs-lookup"><span data-stu-id="ba31f-104">This example shows how to use the `My.Application.Log.WriteEntry` method with the `Startup` and `Shutdown` events to write tracing information.</span></span>  
  
### <a name="to-access-the-applications-event-handler-code"></a><span data-ttu-id="ba31f-105">Přístup ke kódu obslužnou rutinu události aplikace</span><span class="sxs-lookup"><span data-stu-id="ba31f-105">To access the application's event-handler code</span></span>  
  
1.  <span data-ttu-id="ba31f-106">Mají projekt vybraný v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="ba31f-106">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="ba31f-107">Na **projektu** nabídce zvolte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="ba31f-107">On the **Project** menu, choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="ba31f-108">Klikněte na tlačítko **aplikace** kartu.</span><span class="sxs-lookup"><span data-stu-id="ba31f-108">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="ba31f-109">Klikněte na tlačítko **zobrazení události aplikace** tlačítko k otevření editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="ba31f-109">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="ba31f-110">Tím se otevře soubor ApplicationEvents.vb.</span><span class="sxs-lookup"><span data-stu-id="ba31f-110">This opens the ApplicationEvents.vb file.</span></span>  
  
### <a name="to-log-messages-when-the-application-starts"></a><span data-ttu-id="ba31f-111">Protokolování zpráv při spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="ba31f-111">To log messages when the application starts</span></span>  
  
1.  <span data-ttu-id="ba31f-112">Máte ApplicationEvents.vb soubor otevřete v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="ba31f-112">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="ba31f-113">Na **Obecné** nabídce zvolte **události MyApplication**.</span><span class="sxs-lookup"><span data-stu-id="ba31f-113">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2.  <span data-ttu-id="ba31f-114">Na **deklarace** nabídce zvolte **spuštění**.</span><span class="sxs-lookup"><span data-stu-id="ba31f-114">On the **Declarations** menu, choose **Startup**.</span></span>  
  
     <span data-ttu-id="ba31f-115">Aplikace vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> událostí před spuštěním hlavní aplikace.</span><span class="sxs-lookup"><span data-stu-id="ba31f-115">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> event before the main application runs.</span></span>  
  
3.  <span data-ttu-id="ba31f-116">Přidat `My.Application.Log.WriteEntry` metodu `Startup` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="ba31f-116">Add the `My.Application.Log.WriteEntry` method to the `Startup` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#1](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_1.vb)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a><span data-ttu-id="ba31f-117">Protokolování zpráv při ukončení aplikace</span><span class="sxs-lookup"><span data-stu-id="ba31f-117">To log messages when the application shuts down</span></span>  
  
1.  <span data-ttu-id="ba31f-118">Máte ApplicationEvents.vb soubor otevřete v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="ba31f-118">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="ba31f-119">Na **Obecné** nabídce zvolte **události MyApplication**.</span><span class="sxs-lookup"><span data-stu-id="ba31f-119">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2.  <span data-ttu-id="ba31f-120">Na **deklarace** nabídce zvolte **vypnutí**.</span><span class="sxs-lookup"><span data-stu-id="ba31f-120">On the **Declarations** menu, choose **Shutdown**.</span></span>  
  
     <span data-ttu-id="ba31f-121">Aplikace vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> událostí po spuštění hlavní aplikace, ale předtím, než ho ukončí.</span><span class="sxs-lookup"><span data-stu-id="ba31f-121">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> event after the main application runs, but before it shuts down.</span></span>  
  
3.  <span data-ttu-id="ba31f-122">Přidat `My.Application.Log.WriteEntry` metodu `Shutdown` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="ba31f-122">Add the `My.Application.Log.WriteEntry` method to the `Shutdown` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#2](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="ba31f-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="ba31f-123">Example</span></span>  
 <span data-ttu-id="ba31f-124">Můžete použít **Návrháře projektu** přistupovat k událostem aplikace v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="ba31f-124">You can use the **Project Designer** to access the application events in the Code Editor.</span></span> <span data-ttu-id="ba31f-125">Další informace najdete v tématu [stránka aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="ba31f-125">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 [!code-vb[VbVbalrMyApplicationLog#3](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ba31f-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba31f-126">See also</span></span>
- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="ba31f-127">Stránka Aplikace, Návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba31f-127">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="ba31f-128">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="ba31f-128">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
