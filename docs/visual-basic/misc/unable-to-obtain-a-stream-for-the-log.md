---
title: "Nelze získat datový proud pro protokol"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dd3051b2331502c9f4f3430bbf88731b307d1b1a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a><span data-ttu-id="ab276-102">Nelze získat datový proud pro protokol</span><span class="sxs-lookup"><span data-stu-id="ab276-102">Unable to obtain a stream for the log</span></span>
<span data-ttu-id="ab276-103">Nelze získat datového proudu, do protokolu.</span><span class="sxs-lookup"><span data-stu-id="ab276-103">Unable to obtain a stream for the log.</span></span> <span data-ttu-id="ab276-104">Potenciální názvy souborů na základě \<název > se již používá.</span><span class="sxs-lookup"><span data-stu-id="ab276-104">Potential file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="ab276-105"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Třída nelze vytvořit nový soubor protokolu, protože všechny potenciální názvy souborů protokolu na základě \<název > se již používá.</span><span class="sxs-lookup"><span data-stu-id="ab276-105">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not create a new log file because all potential log file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="ab276-106">Má příliš mnoho souborů protokolu může znamenat, že architektury problému s aplikací.</span><span class="sxs-lookup"><span data-stu-id="ab276-106">Having too many log files may indicate an architectural problem with the application.</span></span> <span data-ttu-id="ab276-107">Najdete v dokumentaci k <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> třídu pro další informace.</span><span class="sxs-lookup"><span data-stu-id="ab276-107">See the documentation for the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class for more information.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ab276-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="ab276-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="ab276-109">Nastavte <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> vlastnost <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> nebo <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> zahrnout razítka data v názvu protokolového souboru.</span><span class="sxs-lookup"><span data-stu-id="ab276-109">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> property to <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> or <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> to include a date-stamp in the log file name.</span></span>  
  
2.  <span data-ttu-id="ab276-110">Archivovat existující protokoly a je odebrat z počítače na Povolit <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> objekt k vytvoření nové protokoly.</span><span class="sxs-lookup"><span data-stu-id="ab276-110">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab276-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab276-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>  
 [<span data-ttu-id="ab276-112">My.Application.Log – objekt</span><span class="sxs-lookup"><span data-stu-id="ab276-112">My.Application.Log Object</span></span>](../../visual-basic/language-reference/objects/my-application-log-object.md)  
 [<span data-ttu-id="ab276-113">My.log – objekt</span><span class="sxs-lookup"><span data-stu-id="ab276-113">My.Log Object</span></span>](../../visual-basic/language-reference/objects/my-log-object.md)
