---
title: Nelze zapisovat do souboru protokolu, protože při zápisu by došlo ke snížení volného místa na disku určeného hodnotou ReservedSpace
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_ReservedSpaceEncroached
ms.assetid: 95832e70-4ecc-47aa-90c1-f35c4d468151
ms.openlocfilehash: dc7e97bfc5aa3963e1edcd204f5b81d21edab579
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2019
ms.locfileid: "64913237"
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-reduce-free-disk-space-below-reservedspace-value"></a><span data-ttu-id="2c56f-102">Nelze zapisovat do souboru protokolu, protože při zápisu by došlo ke snížení volného místa na disku určeného hodnotou ReservedSpace</span><span class="sxs-lookup"><span data-stu-id="2c56f-102">Unable to write to log file because writing to it would reduce free disk space below ReservedSpace value</span></span>
<span data-ttu-id="2c56f-103"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Třídy nemůže zapisovat do souboru protokolu, protože:</span><span class="sxs-lookup"><span data-stu-id="2c56f-103">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not write to the log file because:</span></span>  
  
- <span data-ttu-id="2c56f-104">Množství volného místa na disku (v bajtech) je menší než hodnota <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> vlastnost</span><span class="sxs-lookup"><span data-stu-id="2c56f-104">The amount of free disk space (in bytes) is less than the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> property</span></span>  
  
     <span data-ttu-id="2c56f-105">– a –</span><span class="sxs-lookup"><span data-stu-id="2c56f-105">—and—</span></span>  
  
- <span data-ttu-id="2c56f-106">Hodnota <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> byla vlastnost <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span><span class="sxs-lookup"><span data-stu-id="2c56f-106">The value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property was <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2c56f-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="2c56f-107">To correct this error</span></span>  
  
1. <span data-ttu-id="2c56f-108">Archivovat protokoly na stávající a neodeberete z počítače, aby <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> objekt k vytvoření nové protokoly.</span><span class="sxs-lookup"><span data-stu-id="2c56f-108">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
2. <span data-ttu-id="2c56f-109">Změňte hodnotu <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> vlastnost na menší hodnotu rezervovat méně místa na disku.</span><span class="sxs-lookup"><span data-stu-id="2c56f-109">Change the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> property to a smaller number to reserve less disk space.</span></span>  
  
3. <span data-ttu-id="2c56f-110">Nastavte <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> vlastnost <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> se zahodit zprávy bez upozornění, pokud není k dispozici dostatek volného místa na disku.</span><span class="sxs-lookup"><span data-stu-id="2c56f-110">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property to <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> to discard messages without warning if there is not enough free disk space.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c56f-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2c56f-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- [<span data-ttu-id="2c56f-112">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="2c56f-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [<span data-ttu-id="2c56f-113">My.Application.Info.DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="2c56f-113">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
