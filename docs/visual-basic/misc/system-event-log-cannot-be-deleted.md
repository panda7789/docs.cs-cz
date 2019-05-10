---
title: Protokol událostí systému nelze odstranit.
ms.date: 07/20/2015
ms.assetid: 26ca8819-4ce5-49c6-98f3-27fe9e2e8e3d
ms.openlocfilehash: 72f648751107db90449a085e1a49892927fcd29b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64620483"
---
# <a name="system-event-log-cannot-be-deleted"></a><span data-ttu-id="d5088-102">Protokol událostí systému nelze odstranit.</span><span class="sxs-lookup"><span data-stu-id="d5088-102">System event log cannot be deleted</span></span>
<span data-ttu-id="d5088-103">Byl proveden pokus o odstranění protokolu událostí systému, kterou nejde odstranit.</span><span class="sxs-lookup"><span data-stu-id="d5088-103">An attempt has been made to delete the system event log, which cannot be deleted.</span></span> <span data-ttu-id="d5088-104">Systémového protokolu se sleduje systémové události, jako je například selhání spuštění a hardware systému.</span><span class="sxs-lookup"><span data-stu-id="d5088-104">The system log tracks system events such as system startup and hardware failures.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d5088-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="d5088-105">To correct this error</span></span>  
  
- <span data-ttu-id="d5088-106">Zvažte, jestli by vaše aplikace napsat do aplikace nebo vlastního protokolu, nikoli protokol událostí systému.</span><span class="sxs-lookup"><span data-stu-id="d5088-106">Consider having your application write to an application or custom log, rather than the system event log.</span></span>  
  
- <span data-ttu-id="d5088-107">Nepokoušejte se smazat protokol událostí systému.</span><span class="sxs-lookup"><span data-stu-id="d5088-107">Do not attempt to delete the system event log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5088-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d5088-108">See also</span></span>

- <span data-ttu-id="d5088-109">[Správa protokolů událostí](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/4f69axw4(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="d5088-109">[Administering Event Logs](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/4f69axw4(v=vs.90))</span></span>
- <span data-ttu-id="d5088-110">[Postupy: Vytvářet a odstraňovat vlastní protokoly událostí](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/49dwckkz(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="d5088-110">[How to: Create and Remove Custom Event Logs](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/49dwckkz(v=vs.90))</span></span>
