---
title: 'Postupy: Protokolování zpráv při spuštění nebo ukončení aplikace'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event [Visual Basic]
- event logs, startup
- Shutdown event [Visual Basic]
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
ms.openlocfilehash: 5a4ef3888ba8371d26204c3569b5fb9bae1f15f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352098"
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a><span data-ttu-id="eb9d8-102">Postupy: Protokolování zpráv při spuštění nebo ukončení aplikace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb9d8-102">How to: Log Messages When the Application Starts or Shuts Down (Visual Basic)</span></span>

<span data-ttu-id="eb9d8-103">Objekty `My.Application.Log` a `My.Log` můžete použít k protokolování informací o událostech, ke kterým dochází ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="eb9d8-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="eb9d8-104">Tento příklad ukazuje, `My.Application.Log.WriteEntry` jak používat `Startup` `Shutdown` metodu s a události k zápisu trasování informace.</span><span class="sxs-lookup"><span data-stu-id="eb9d8-104">This example shows how to use the `My.Application.Log.WriteEntry` method with the `Startup` and `Shutdown` events to write tracing information.</span></span>  
  
### <a name="to-access-the-applications-event-handler-code"></a><span data-ttu-id="eb9d8-105">Přístup ke kódu obslužné rutiny události aplikace</span><span class="sxs-lookup"><span data-stu-id="eb9d8-105">To access the application's event-handler code</span></span>  
  
1. <span data-ttu-id="eb9d8-106">V **Průzkumníku řešení**je vybrán projekt .</span><span class="sxs-lookup"><span data-stu-id="eb9d8-106">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="eb9d8-107">V nabídce **Projekt** zvolte **Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="eb9d8-107">On the **Project** menu, choose **Properties**.</span></span>  
  
2. <span data-ttu-id="eb9d8-108">Klikněte na kartu **Aplikace.**</span><span class="sxs-lookup"><span data-stu-id="eb9d8-108">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="eb9d8-109">Kliknutím na tlačítko **Zobrazit události aplikace** otevřete Editor kódu.</span><span class="sxs-lookup"><span data-stu-id="eb9d8-109">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="eb9d8-110">Tím se otevře soubor ApplicationEvents.vb.</span><span class="sxs-lookup"><span data-stu-id="eb9d8-110">This opens the ApplicationEvents.vb file.</span></span>  
  
### <a name="to-log-messages-when-the-application-starts"></a><span data-ttu-id="eb9d8-111">Protokolování zpráv při spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="eb9d8-111">To log messages when the application starts</span></span>  
  
1. <span data-ttu-id="eb9d8-112">Otevřete soubor ApplicationEvents.vb v Editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="eb9d8-112">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="eb9d8-113">V nabídce **Obecné** zvolte **MyApplication Events**.</span><span class="sxs-lookup"><span data-stu-id="eb9d8-113">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2. <span data-ttu-id="eb9d8-114">V nabídce **Declarations** zvolte **Startup**.</span><span class="sxs-lookup"><span data-stu-id="eb9d8-114">On the **Declarations** menu, choose **Startup**.</span></span>  
  
     <span data-ttu-id="eb9d8-115">Aplikace vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> událost před spuštěním hlavní aplikace.</span><span class="sxs-lookup"><span data-stu-id="eb9d8-115">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> event before the main application runs.</span></span>  
  
3. <span data-ttu-id="eb9d8-116">Přidejte `My.Application.Log.WriteEntry` metodu `Startup` do obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="eb9d8-116">Add the `My.Application.Log.WriteEntry` method to the `Startup` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#1)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a><span data-ttu-id="eb9d8-117">Protokolování zpráv při vypnutí aplikace</span><span class="sxs-lookup"><span data-stu-id="eb9d8-117">To log messages when the application shuts down</span></span>  
  
1. <span data-ttu-id="eb9d8-118">Otevřete soubor ApplicationEvents.vb v Editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="eb9d8-118">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="eb9d8-119">V nabídce **Obecné** zvolte **MyApplication Events**.</span><span class="sxs-lookup"><span data-stu-id="eb9d8-119">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2. <span data-ttu-id="eb9d8-120">V nabídce **Declarations** zvolte **Shutdown**.</span><span class="sxs-lookup"><span data-stu-id="eb9d8-120">On the **Declarations** menu, choose **Shutdown**.</span></span>  
  
     <span data-ttu-id="eb9d8-121">Aplikace vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> událost po spuštění hlavní aplikace, ale před jeho vypnutím.</span><span class="sxs-lookup"><span data-stu-id="eb9d8-121">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> event after the main application runs, but before it shuts down.</span></span>  
  
3. <span data-ttu-id="eb9d8-122">Přidejte `My.Application.Log.WriteEntry` metodu `Shutdown` do obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="eb9d8-122">Add the `My.Application.Log.WriteEntry` method to the `Shutdown` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="eb9d8-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="eb9d8-123">Example</span></span>  

 <span data-ttu-id="eb9d8-124">**Návrháře projektu** můžete použít pro přístup k událostem aplikace v Editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="eb9d8-124">You can use the **Project Designer** to access the application events in the Code Editor.</span></span> <span data-ttu-id="eb9d8-125">Další informace naleznete v [tématu Stránka aplikace, Návrhář projektu (Visual Basic).](/visualstudio/ide/reference/application-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="eb9d8-125">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 [!code-vb[VbVbalrMyApplicationLog#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="eb9d8-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb9d8-126">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="eb9d8-127">Stránka Aplikace, návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb9d8-127">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="eb9d8-128">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="eb9d8-128">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
