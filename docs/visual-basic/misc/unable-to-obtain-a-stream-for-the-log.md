---
title: Nelze získat datový proud pro protokol
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
ms.openlocfilehash: 3f5ac83e6957d6d5883bf5ab191e2a922c874df3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33639525"
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a><span data-ttu-id="8813b-102">Nelze získat datový proud pro protokol</span><span class="sxs-lookup"><span data-stu-id="8813b-102">Unable to obtain a stream for the log</span></span>
<span data-ttu-id="8813b-103">Nelze získat datového proudu, do protokolu.</span><span class="sxs-lookup"><span data-stu-id="8813b-103">Unable to obtain a stream for the log.</span></span> <span data-ttu-id="8813b-104">Potenciální názvy souborů na základě \<název > se již používá.</span><span class="sxs-lookup"><span data-stu-id="8813b-104">Potential file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="8813b-105"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Třída nelze vytvořit nový soubor protokolu, protože všechny potenciální názvy souborů protokolu na základě \<název > se již používá.</span><span class="sxs-lookup"><span data-stu-id="8813b-105">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not create a new log file because all potential log file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="8813b-106">Má příliš mnoho souborů protokolu může znamenat, že architektury problému s aplikací.</span><span class="sxs-lookup"><span data-stu-id="8813b-106">Having too many log files may indicate an architectural problem with the application.</span></span> <span data-ttu-id="8813b-107">Najdete v dokumentaci k <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> třídu pro další informace.</span><span class="sxs-lookup"><span data-stu-id="8813b-107">See the documentation for the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class for more information.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8813b-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="8813b-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="8813b-109">Nastavte <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> vlastnost <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> nebo <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> zahrnout razítka data v názvu protokolového souboru.</span><span class="sxs-lookup"><span data-stu-id="8813b-109">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> property to <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> or <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> to include a date-stamp in the log file name.</span></span>  
  
2.  <span data-ttu-id="8813b-110">Archivovat existující protokoly a je odebrat z počítače na Povolit <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> objekt k vytvoření nové protokoly.</span><span class="sxs-lookup"><span data-stu-id="8813b-110">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8813b-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="8813b-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>  
 [<span data-ttu-id="8813b-112">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="8813b-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)  
 [<span data-ttu-id="8813b-113">My.Application.Info.DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="8813b-113">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
