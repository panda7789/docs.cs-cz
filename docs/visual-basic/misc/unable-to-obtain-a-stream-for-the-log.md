---
title: Nepovedlo se získat datový proud pro protokol
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
ms.openlocfilehash: 0553da64ca8fcac148cd8da5c22227b5824387de
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628744"
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a><span data-ttu-id="c62b6-102">Nepovedlo se získat datový proud pro protokol</span><span class="sxs-lookup"><span data-stu-id="c62b6-102">Unable to obtain a stream for the log</span></span>
<span data-ttu-id="c62b6-103">Nelze získat datový proud pro protokol.</span><span class="sxs-lookup"><span data-stu-id="c62b6-103">Unable to obtain a stream for the log.</span></span> <span data-ttu-id="c62b6-104">Potenciální názvy souborů založené na \<název > se už používá.</span><span class="sxs-lookup"><span data-stu-id="c62b6-104">Potential file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="c62b6-105"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Třídu nelze vytvořit nový soubor protokolu, protože všechny potenciální názvy souborů protokolu na základě \<název > se už používá.</span><span class="sxs-lookup"><span data-stu-id="c62b6-105">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not create a new log file because all potential log file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="c62b6-106">Máte příliš mnoho souborů protokolu může znamenat architektury problém s aplikací.</span><span class="sxs-lookup"><span data-stu-id="c62b6-106">Having too many log files may indicate an architectural problem with the application.</span></span> <span data-ttu-id="c62b6-107">Najdete v dokumentaci k <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> třídy pro další informace.</span><span class="sxs-lookup"><span data-stu-id="c62b6-107">See the documentation for the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class for more information.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c62b6-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="c62b6-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="c62b6-109">Nastavte <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> vlastnost <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> nebo <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> název souboru protokolu zahrnout časové razítko.</span><span class="sxs-lookup"><span data-stu-id="c62b6-109">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> property to <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> or <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> to include a date-stamp in the log file name.</span></span>  
  
2.  <span data-ttu-id="c62b6-110">Archivovat protokoly na stávající a neodeberete z počítače, aby <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> objekt k vytvoření nové protokoly.</span><span class="sxs-lookup"><span data-stu-id="c62b6-110">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c62b6-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c62b6-111">See also</span></span>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>
- [<span data-ttu-id="c62b6-112">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="c62b6-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [<span data-ttu-id="c62b6-113">My.Application.Info.DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="c62b6-113">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
