---
title: Protokolování informací z aplikace
ms.date: 07/20/2015
helpviewer_keywords:
- Log object
- My.Log object
- applications [Visual Basic], logging information from
- logging
- My.Application.Log object
- examples [Visual Basic], logging application information
ms.assetid: 8bf4f047-22d6-48d6-aec5-93b98ad5b8e8
ms.openlocfilehash: dace4bac3bf7529b8c50a492a092ad478f4d9e2d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353257"
---
# <a name="logging-information-from-the-application-visual-basic"></a><span data-ttu-id="923ab-102">Protokolování informací z aplikace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="923ab-102">Logging Information from the Application (Visual Basic)</span></span>

<span data-ttu-id="923ab-103">This section contains topics that cover how to log information from your application using the `My.Application.Log` or `My.Log` object, and how to extend the application's logging capabilities.</span><span class="sxs-lookup"><span data-stu-id="923ab-103">This section contains topics that cover how to log information from your application using the `My.Application.Log` or `My.Log` object, and how to extend the application's logging capabilities.</span></span>  
  
 <span data-ttu-id="923ab-104">The `Log` object provides methods for writing information to the application's log listeners, and the `Log` object's advanced `TraceSource` property provides detailed configuration information.</span><span class="sxs-lookup"><span data-stu-id="923ab-104">The `Log` object provides methods for writing information to the application's log listeners, and the `Log` object's advanced `TraceSource` property provides detailed configuration information.</span></span> <span data-ttu-id="923ab-105">The `Log` object is configured by the application's configuration file.</span><span class="sxs-lookup"><span data-stu-id="923ab-105">The `Log` object is configured by the application's configuration file.</span></span>  
  
 <span data-ttu-id="923ab-106">The `My.Log` object is available only for ASP.NET applications.</span><span class="sxs-lookup"><span data-stu-id="923ab-106">The `My.Log` object is available only for ASP.NET applications.</span></span> <span data-ttu-id="923ab-107">For client applications, use `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="923ab-107">For client applications, use `My.Application.Log`.</span></span> <span data-ttu-id="923ab-108">Další informace najdete v tématu <xref:Microsoft.VisualBasic.Logging.Log>.</span><span class="sxs-lookup"><span data-stu-id="923ab-108">For more information, see <xref:Microsoft.VisualBasic.Logging.Log>.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="923ab-109">Úkoly</span><span class="sxs-lookup"><span data-stu-id="923ab-109">Tasks</span></span>  
  
|<span data-ttu-id="923ab-110">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="923ab-110">To</span></span>|<span data-ttu-id="923ab-111">Další informace naleznete v tématu</span><span class="sxs-lookup"><span data-stu-id="923ab-111">See</span></span>|  
|--------|---------|  
|<span data-ttu-id="923ab-112">Write event information to the application's logs.</span><span class="sxs-lookup"><span data-stu-id="923ab-112">Write event information to the application's logs.</span></span>|[<span data-ttu-id="923ab-113">Postupy: Zápis zpráv protokolu</span><span class="sxs-lookup"><span data-stu-id="923ab-113">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)|  
|<span data-ttu-id="923ab-114">Write exception information to the application's logs.</span><span class="sxs-lookup"><span data-stu-id="923ab-114">Write exception information to the application's logs.</span></span>|[<span data-ttu-id="923ab-115">Postupy: Protokolování výjimek</span><span class="sxs-lookup"><span data-stu-id="923ab-115">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)|  
|<span data-ttu-id="923ab-116">Write trace information to the application's logs when the application starts and shuts down.</span><span class="sxs-lookup"><span data-stu-id="923ab-116">Write trace information to the application's logs when the application starts and shuts down.</span></span>|[<span data-ttu-id="923ab-117">Postupy: Protokolování zpráv při spuštění nebo ukončení aplikace</span><span class="sxs-lookup"><span data-stu-id="923ab-117">How to: Log Messages When the Application Starts or Shuts Down</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-messages-when-the-application-starts-or-shuts-down.md)|  
|<span data-ttu-id="923ab-118">Configure `My.Application.Log` to write information to a text file.</span><span class="sxs-lookup"><span data-stu-id="923ab-118">Configure `My.Application.Log` to write information to a text file.</span></span>|[<span data-ttu-id="923ab-119">Postupy: Zápis informací o události do textového souboru</span><span class="sxs-lookup"><span data-stu-id="923ab-119">How to: Write Event Information to a Text File</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)|  
|<span data-ttu-id="923ab-120">Configure `My.Application.Log` to write information to an event log.</span><span class="sxs-lookup"><span data-stu-id="923ab-120">Configure `My.Application.Log` to write information to an event log.</span></span>|[<span data-ttu-id="923ab-121">Postupy: Zápis do protokolu událostí aplikace</span><span class="sxs-lookup"><span data-stu-id="923ab-121">How to: Write to an Application Event Log</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)|  
|<span data-ttu-id="923ab-122">Change where `My.Application.Log` writes information.</span><span class="sxs-lookup"><span data-stu-id="923ab-122">Change where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="923ab-123">Návod: Změna místa, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="923ab-123">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="923ab-124">Determine where `My.Application.Log` writes information.</span><span class="sxs-lookup"><span data-stu-id="923ab-124">Determine where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="923ab-125">Návod: Zjištění, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="923ab-125">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="923ab-126">Create a custom log listener for `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="923ab-126">Create a custom log listener for `My.Application.Log`.</span></span>|[<span data-ttu-id="923ab-127">Návod: Vytváření vlastních součástí naslouchajících protokolům</span><span class="sxs-lookup"><span data-stu-id="923ab-127">Walkthrough: Creating Custom Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)|  
|<span data-ttu-id="923ab-128">Filter the output of the `My.Application.Log` logs.</span><span class="sxs-lookup"><span data-stu-id="923ab-128">Filter the output of the `My.Application.Log` logs.</span></span>|[<span data-ttu-id="923ab-129">Návod: Filtrování výstupu My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="923ab-129">Walkthrough: Filtering My.Application.Log Output</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)|  
  
## <a name="see-also"></a><span data-ttu-id="923ab-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="923ab-130">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="923ab-131">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="923ab-131">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="923ab-132">Řešení potíží: Součásti naslouchající protokolům</span><span class="sxs-lookup"><span data-stu-id="923ab-132">Troubleshooting: Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
