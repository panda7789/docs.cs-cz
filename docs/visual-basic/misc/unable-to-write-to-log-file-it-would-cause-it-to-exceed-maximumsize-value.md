---
title: Nelze zapisovat do souboru protokolu, protože zápisu by způsobilo došlo k překročení hodnoty MaximumSize objektu
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_FileExceedsMaximumSize
ms.assetid: 61747a9c-e460-424b-a365-73cdba9dd428
ms.openlocfilehash: 170612dfc294f3d2326ad34216f699cf4af6cdb0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554657"
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-cause-it-to-exceed-maximumsize-value"></a><span data-ttu-id="3d259-102">Nelze zapisovat do souboru protokolu, protože zápisu by způsobilo došlo k překročení hodnoty MaximumSize objektu</span><span class="sxs-lookup"><span data-stu-id="3d259-102">Unable to write to log file because writing to it would cause it to exceed MaximumSize value</span></span>
<span data-ttu-id="3d259-103"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Třídy nemůže zapisovat do souboru protokolu, protože:</span><span class="sxs-lookup"><span data-stu-id="3d259-103">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not write to the log file because:</span></span>  
  
-   <span data-ttu-id="3d259-104">Velikost souboru protokolu (v bajtech) je větší než hodnota <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> vlastnost</span><span class="sxs-lookup"><span data-stu-id="3d259-104">The log file size (in bytes) is greater than the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> property</span></span>  
  
     <span data-ttu-id="3d259-105">– a –</span><span class="sxs-lookup"><span data-stu-id="3d259-105">—and—</span></span>  
  
-   <span data-ttu-id="3d259-106">Hodnota <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> byla vlastnost <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span><span class="sxs-lookup"><span data-stu-id="3d259-106">The value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property was <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3d259-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="3d259-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="3d259-108">Archivovat protokoly na stávající a neodeberete z počítače, aby <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> objekt k vytvoření nové protokoly.</span><span class="sxs-lookup"><span data-stu-id="3d259-108">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
2.  <span data-ttu-id="3d259-109">Změňte hodnotu <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> vlastnost umožňující větší protokoly.</span><span class="sxs-lookup"><span data-stu-id="3d259-109">Change the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> property to allow for larger logs.</span></span>  
  
3.  <span data-ttu-id="3d259-110">Nastavte <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> vlastnost <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> se zahodit zprávy bez upozornění, pokud v protokolu je příliš velký.</span><span class="sxs-lookup"><span data-stu-id="3d259-110">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property to <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> to discard messages without warning if the log is too large.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d259-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3d259-111">See also</span></span>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- [<span data-ttu-id="3d259-112">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="3d259-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [<span data-ttu-id="3d259-113">My.Application.Info.DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="3d259-113">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
