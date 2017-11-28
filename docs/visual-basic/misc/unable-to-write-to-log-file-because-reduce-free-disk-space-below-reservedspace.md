---
title: "Nelze zapisovat do souboru protokolu, protože zápis do něj by snížení volného místa na disku hodnotou ReservedSpace"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrApplicationLog_ReservedSpaceEncroached
ms.assetid: 95832e70-4ecc-47aa-90c1-f35c4d468151
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0adc3438a9473885022e9785c5381f8da0b6f303
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-reduce-free-disk-space-below-reservedspace-value"></a><span data-ttu-id="0c011-102">Nelze zapisovat do souboru protokolu, protože zápis do něj by snížení volného místa na disku hodnotou ReservedSpace</span><span class="sxs-lookup"><span data-stu-id="0c011-102">Unable to write to log file because writing to it would reduce free disk space below ReservedSpace value</span></span>
<span data-ttu-id="0c011-103"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Třída nemůže zapisovat do souboru protokolu, protože:</span><span class="sxs-lookup"><span data-stu-id="0c011-103">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not write to the log file because:</span></span>  
  
-   <span data-ttu-id="0c011-104">Množství volného místa na disku (v bajtech) je menší než hodnota <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> vlastnost</span><span class="sxs-lookup"><span data-stu-id="0c011-104">The amount of free disk space (in bytes) is less than the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> property</span></span>  
  
     <span data-ttu-id="0c011-105">– a –</span><span class="sxs-lookup"><span data-stu-id="0c011-105">—and—</span></span>  
  
-   <span data-ttu-id="0c011-106">Hodnota <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> byla vlastnost <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span><span class="sxs-lookup"><span data-stu-id="0c011-106">The value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property was <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0c011-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="0c011-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="0c011-108">Archivovat existující protokoly a je odebrat z počítače na Povolit <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> objekt k vytvoření nové protokoly.</span><span class="sxs-lookup"><span data-stu-id="0c011-108">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
2.  <span data-ttu-id="0c011-109">Změňte hodnotu <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> vlastnost na menší hodnotu tak, aby vyhradil méně místa na disku.</span><span class="sxs-lookup"><span data-stu-id="0c011-109">Change the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> property to a smaller number to reserve less disk space.</span></span>  
  
3.  <span data-ttu-id="0c011-110">Nastavte <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> vlastnost <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> vyřadí zpráv bez upozornění, pokud není k dispozici dostatek volného místa na disku.</span><span class="sxs-lookup"><span data-stu-id="0c011-110">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property to <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> to discard messages without warning if there is not enough free disk space.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c011-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="0c011-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
 [<span data-ttu-id="0c011-112">My.Application.Log – objekt</span><span class="sxs-lookup"><span data-stu-id="0c011-112">My.Application.Log Object</span></span>](../../visual-basic/language-reference/objects/my-application-log-object.md)  
 [<span data-ttu-id="0c011-113">My.log – objekt</span><span class="sxs-lookup"><span data-stu-id="0c011-113">My.Log Object</span></span>](../../visual-basic/language-reference/objects/my-log-object.md)
