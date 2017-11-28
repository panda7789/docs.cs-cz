---
title: "Protokolování informací z aplikace (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Log object
- My.Log object
- applications [Visual Basic], logging information from
- logging
- My.Application.Log object
- examples [Visual Basic], logging application information
ms.assetid: 8bf4f047-22d6-48d6-aec5-93b98ad5b8e8
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e52aaf4c26b4fa60ee04d7df6aa96980ebbf491
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="logging-information-from-the-application-visual-basic"></a><span data-ttu-id="d68bc-102">Protokolování informací z aplikace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d68bc-102">Logging Information from the Application (Visual Basic)</span></span>
<span data-ttu-id="d68bc-103">Tento oddíl obsahuje témata, které se týkají se protokolování informací z aplikace pomocí `My.Application.Log` nebo `My.Log` objekt a jak rozšířit možnosti protokolování aplikace.</span><span class="sxs-lookup"><span data-stu-id="d68bc-103">This section contains topics that cover how to log information from your application using the `My.Application.Log` or `My.Log` object, and how to extend the application's logging capabilities.</span></span>  
  
 <span data-ttu-id="d68bc-104">`Log` Objekt poskytuje metody pro zápis informací do naslouchací procesy pro protokoly aplikace a `Log` rozšířenou objektu `TraceSource` vlastnost poskytuje podrobné informace o konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="d68bc-104">The `Log` object provides methods for writing information to the application's log listeners, and the `Log` object's advanced `TraceSource` property provides detailed configuration information.</span></span> <span data-ttu-id="d68bc-105">`Log` Objekt je konfigurován pomocí konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="d68bc-105">The `Log` object is configured by the application's configuration file.</span></span>  
  
 <span data-ttu-id="d68bc-106">`My.Log` Objekt je k dispozici pouze pro aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d68bc-106">The `My.Log` object is available only for ASP.NET applications.</span></span> <span data-ttu-id="d68bc-107">Pro klientské aplikace, použijte `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="d68bc-107">For client applications, use `My.Application.Log`.</span></span> <span data-ttu-id="d68bc-108">Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Logging.Log>.</span><span class="sxs-lookup"><span data-stu-id="d68bc-108">For more information, see <xref:Microsoft.VisualBasic.Logging.Log>.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="d68bc-109">Úlohy</span><span class="sxs-lookup"><span data-stu-id="d68bc-109">Tasks</span></span>  
  
|<span data-ttu-id="d68bc-110">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="d68bc-110">To</span></span>|<span data-ttu-id="d68bc-111">Další informace naleznete v tématu</span><span class="sxs-lookup"><span data-stu-id="d68bc-111">See</span></span>|  
|--------|---------|  
|<span data-ttu-id="d68bc-112">Zápis informací o události do protokolů aplikace.</span><span class="sxs-lookup"><span data-stu-id="d68bc-112">Write event information to the application's logs.</span></span>|[<span data-ttu-id="d68bc-113">Postupy: zápis zpráv protokolu</span><span class="sxs-lookup"><span data-stu-id="d68bc-113">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)|  
|<span data-ttu-id="d68bc-114">Informace o výjimce zapisovat do protokolů aplikace.</span><span class="sxs-lookup"><span data-stu-id="d68bc-114">Write exception information to the application's logs.</span></span>|[<span data-ttu-id="d68bc-115">Postupy: protokolování výjimek</span><span class="sxs-lookup"><span data-stu-id="d68bc-115">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)|  
|<span data-ttu-id="d68bc-116">Když se aplikace spustí a ukončí zapsat informace trasování do protokolů aplikace.</span><span class="sxs-lookup"><span data-stu-id="d68bc-116">Write trace information to the application's logs when the application starts and shuts down.</span></span>|[<span data-ttu-id="d68bc-117">Postupy: protokolování zpráv při spuštění nebo ukončení aplikace</span><span class="sxs-lookup"><span data-stu-id="d68bc-117">How to: Log Messages When the Application Starts or Shuts Down</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-messages-when-the-application-starts-or-shuts-down.md)|  
|<span data-ttu-id="d68bc-118">Konfigurace `My.Application.Log` při zápisu informací do textového souboru.</span><span class="sxs-lookup"><span data-stu-id="d68bc-118">Configure `My.Application.Log` to write information to a text file.</span></span>|[<span data-ttu-id="d68bc-119">Postupy: zápis informací o události do textového souboru</span><span class="sxs-lookup"><span data-stu-id="d68bc-119">How to: Write Event Information to a Text File</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)|  
|<span data-ttu-id="d68bc-120">Konfigurace `My.Application.Log` při zápisu informací do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="d68bc-120">Configure `My.Application.Log` to write information to an event log.</span></span>|[<span data-ttu-id="d68bc-121">Postupy: zápis do protokolu událostí aplikace</span><span class="sxs-lookup"><span data-stu-id="d68bc-121">How to: Write to an Application Event Log</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)|  
|<span data-ttu-id="d68bc-122">Kde změnit `My.Application.Log` zapisuje informace.</span><span class="sxs-lookup"><span data-stu-id="d68bc-122">Change where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="d68bc-123">Návod: Změna místa, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="d68bc-123">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="d68bc-124">Určení místa `My.Application.Log` zapisuje informace.</span><span class="sxs-lookup"><span data-stu-id="d68bc-124">Determine where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="d68bc-125">Návod: Zjištění, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="d68bc-125">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="d68bc-126">Vytvořte naslouchací proces vlastního protokolu pro `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="d68bc-126">Create a custom log listener for `My.Application.Log`.</span></span>|[<span data-ttu-id="d68bc-127">Návod: Vytváření vlastních součástí naslouchajících protokolům</span><span class="sxs-lookup"><span data-stu-id="d68bc-127">Walkthrough: Creating Custom Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)|  
|<span data-ttu-id="d68bc-128">Provede filtrování výstupu z `My.Application.Log` protokoly.</span><span class="sxs-lookup"><span data-stu-id="d68bc-128">Filter the output of the `My.Application.Log` logs.</span></span>|[<span data-ttu-id="d68bc-129">Návod: Filtrování výstupu My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="d68bc-129">Walkthrough: Filtering My.Application.Log Output</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)|  
  
## <a name="see-also"></a><span data-ttu-id="d68bc-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="d68bc-130">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [<span data-ttu-id="d68bc-131">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="d68bc-131">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="d68bc-132">Řešení potíží: Součásti naslouchající protokolům</span><span class="sxs-lookup"><span data-stu-id="d68bc-132">Troubleshooting: Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
