---
title: Nepovedlo se získat datový proud pro protokol
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
ms.openlocfilehash: 45b7a16608bea4879e84fa7004097a8c38312284
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2019
ms.locfileid: "58031709"
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a><span data-ttu-id="18c6f-102">Nepovedlo se získat datový proud pro protokol</span><span class="sxs-lookup"><span data-stu-id="18c6f-102">Unable to obtain a stream for the log</span></span>
<span data-ttu-id="18c6f-103">Nelze získat datový proud pro protokol.</span><span class="sxs-lookup"><span data-stu-id="18c6f-103">Unable to obtain a stream for the log.</span></span> <span data-ttu-id="18c6f-104">Potenciální názvy souborů založené na \<název > se už používá.</span><span class="sxs-lookup"><span data-stu-id="18c6f-104">Potential file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="18c6f-105"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Třídu nelze vytvořit nový soubor protokolu, protože všechny potenciální názvy souborů protokolu na základě \<název > se už používá.</span><span class="sxs-lookup"><span data-stu-id="18c6f-105">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not create a new log file because all potential log file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="18c6f-106">Máte příliš mnoho souborů protokolu může znamenat architektury problém s aplikací.</span><span class="sxs-lookup"><span data-stu-id="18c6f-106">Having too many log files may indicate an architectural problem with the application.</span></span> <span data-ttu-id="18c6f-107">Najdete v dokumentaci k <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> třídy pro další informace.</span><span class="sxs-lookup"><span data-stu-id="18c6f-107">See the documentation for the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class for more information.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="18c6f-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="18c6f-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="18c6f-109">Nastavte <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> vlastnost <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> nebo <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> název souboru protokolu zahrnout časové razítko.</span><span class="sxs-lookup"><span data-stu-id="18c6f-109">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> property to <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> or <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> to include a date-stamp in the log file name.</span></span>  
  
2.  <span data-ttu-id="18c6f-110">Archivovat protokoly na stávající a neodeberete z počítače, aby <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> objekt k vytvoření nové protokoly.</span><span class="sxs-lookup"><span data-stu-id="18c6f-110">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18c6f-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18c6f-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>
- [<span data-ttu-id="18c6f-112">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="18c6f-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [<span data-ttu-id="18c6f-113">My.Application.Info.DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="18c6f-113">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
