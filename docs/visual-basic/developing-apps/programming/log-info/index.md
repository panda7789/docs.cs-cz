---
title: Protokolování informací z aplikace
ms.date: 07/20/2015
helpviewer_keywords:
- Log object
- My.Log object
- applications [Visual Basic], logging information from
- logging
- My.Application.Log object
- examples [Visual Basic], logging application information
ms.assetid: 8bf4f047-22d6-48d6-aec5-93b98ad5b8e8
ms.openlocfilehash: 43738b2d654435532a98654cbc40af134d43f02c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410020"
---
# <a name="logging-information-from-the-application-visual-basic"></a><span data-ttu-id="b6ec0-102">Protokolování informací z aplikace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6ec0-102">Logging Information from the Application (Visual Basic)</span></span>

<span data-ttu-id="b6ec0-103">Tato část obsahuje témata, která pokrývají, jak protokolovat informace z vaší aplikace pomocí `My.Application.Log` `My.Log` objektu nebo a jak rozšiřuje možnosti protokolování aplikace.</span><span class="sxs-lookup"><span data-stu-id="b6ec0-103">This section contains topics that cover how to log information from your application using the `My.Application.Log` or `My.Log` object, and how to extend the application's logging capabilities.</span></span>  
  
 <span data-ttu-id="b6ec0-104">`Log`Objekt poskytuje metody pro zápis informací do protokolu naslouchacího procesu aplikace a `Log` vlastnost Advanced objektu `TraceSource` poskytuje podrobné informace o konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="b6ec0-104">The `Log` object provides methods for writing information to the application's log listeners, and the `Log` object's advanced `TraceSource` property provides detailed configuration information.</span></span> <span data-ttu-id="b6ec0-105">`Log`Objekt je konfigurován pomocí konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="b6ec0-105">The `Log` object is configured by the application's configuration file.</span></span>  
  
 <span data-ttu-id="b6ec0-106">`My.Log`Objekt je k dispozici pouze pro aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b6ec0-106">The `My.Log` object is available only for ASP.NET applications.</span></span> <span data-ttu-id="b6ec0-107">Pro klientské aplikace použijte `My.Application.Log` .</span><span class="sxs-lookup"><span data-stu-id="b6ec0-107">For client applications, use `My.Application.Log`.</span></span> <span data-ttu-id="b6ec0-108">Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Logging.Log>.</span><span class="sxs-lookup"><span data-stu-id="b6ec0-108">For more information, see <xref:Microsoft.VisualBasic.Logging.Log>.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="b6ec0-109">Úlohy</span><span class="sxs-lookup"><span data-stu-id="b6ec0-109">Tasks</span></span>  
  
|<span data-ttu-id="b6ec0-110">Akce</span><span class="sxs-lookup"><span data-stu-id="b6ec0-110">To</span></span>|<span data-ttu-id="b6ec0-111">Seznamte se s </span><span class="sxs-lookup"><span data-stu-id="b6ec0-111">See</span></span>|  
|--------|---------|  
|<span data-ttu-id="b6ec0-112">Zapište informace události do protokolů aplikace.</span><span class="sxs-lookup"><span data-stu-id="b6ec0-112">Write event information to the application's logs.</span></span>|[<span data-ttu-id="b6ec0-113">Postupy: Zápis zpráv protokolu</span><span class="sxs-lookup"><span data-stu-id="b6ec0-113">How to: Write Log Messages</span></span>](how-to-write-log-messages.md)|  
|<span data-ttu-id="b6ec0-114">Zapište informace o výjimce do protokolů aplikace.</span><span class="sxs-lookup"><span data-stu-id="b6ec0-114">Write exception information to the application's logs.</span></span>|[<span data-ttu-id="b6ec0-115">Postupy: Protokolování výjimek</span><span class="sxs-lookup"><span data-stu-id="b6ec0-115">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)|  
|<span data-ttu-id="b6ec0-116">Zapište trasovací informace do protokolů aplikace při spuštění a ukončení aplikace.</span><span class="sxs-lookup"><span data-stu-id="b6ec0-116">Write trace information to the application's logs when the application starts and shuts down.</span></span>|[<span data-ttu-id="b6ec0-117">Postupy: Protokolování zpráv při spuštění nebo ukončení aplikace</span><span class="sxs-lookup"><span data-stu-id="b6ec0-117">How to: Log Messages When the Application Starts or Shuts Down</span></span>](how-to-log-messages-when-the-application-starts-or-shuts-down.md)|  
|<span data-ttu-id="b6ec0-118">Nakonfigurujte `My.Application.Log` pro zápis informací do textového souboru.</span><span class="sxs-lookup"><span data-stu-id="b6ec0-118">Configure `My.Application.Log` to write information to a text file.</span></span>|[<span data-ttu-id="b6ec0-119">Postupy: Zápis informací o události do textového souboru</span><span class="sxs-lookup"><span data-stu-id="b6ec0-119">How to: Write Event Information to a Text File</span></span>](how-to-write-event-information-to-a-text-file.md)|  
|<span data-ttu-id="b6ec0-120">Nakonfigurujte `My.Application.Log` , aby se zapisovaly informace do protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="b6ec0-120">Configure `My.Application.Log` to write information to an event log.</span></span>|[<span data-ttu-id="b6ec0-121">Postupy: Zápis do protokolu událostí aplikace</span><span class="sxs-lookup"><span data-stu-id="b6ec0-121">How to: Write to an Application Event Log</span></span>](how-to-write-to-an-application-event-log.md)|  
|<span data-ttu-id="b6ec0-122">Změnit, kde `My.Application.Log` zapisuje informace.</span><span class="sxs-lookup"><span data-stu-id="b6ec0-122">Change where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="b6ec0-123">Návod: Změna místa, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="b6ec0-123">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](walkthrough-changing-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="b6ec0-124">Určete, kde `My.Application.Log` zapisuje informace.</span><span class="sxs-lookup"><span data-stu-id="b6ec0-124">Determine where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="b6ec0-125">Návod: Zjištění, kam objekt My.Application.Log zapisuje informace</span><span class="sxs-lookup"><span data-stu-id="b6ec0-125">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](walkthrough-determining-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="b6ec0-126">Vytvořte vlastní naslouchací proces protokolu pro `My.Application.Log` .</span><span class="sxs-lookup"><span data-stu-id="b6ec0-126">Create a custom log listener for `My.Application.Log`.</span></span>|[<span data-ttu-id="b6ec0-127">Návod: Vytváření vlastních součástí naslouchajících protokolům</span><span class="sxs-lookup"><span data-stu-id="b6ec0-127">Walkthrough: Creating Custom Log Listeners</span></span>](walkthrough-creating-custom-log-listeners.md)|  
|<span data-ttu-id="b6ec0-128">Filtrujte výstup `My.Application.Log` protokolů.</span><span class="sxs-lookup"><span data-stu-id="b6ec0-128">Filter the output of the `My.Application.Log` logs.</span></span>|[<span data-ttu-id="b6ec0-129">Návod: Filtrování výstupu My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="b6ec0-129">Walkthrough: Filtering My.Application.Log Output</span></span>](walkthrough-filtering-my-application-log-output.md)|  
  
## <a name="see-also"></a><span data-ttu-id="b6ec0-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="b6ec0-130">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="b6ec0-131">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="b6ec0-131">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="b6ec0-132">Řešení potíží: Komponenty naslouchající protokolům</span><span class="sxs-lookup"><span data-stu-id="b6ec0-132">Troubleshooting: Log Listeners</span></span>](troubleshooting-log-listeners.md)
