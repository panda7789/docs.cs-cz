---
title: Protokol událostí systému nelze odstranit.
ms.date: 07/20/2015
ms.assetid: 26ca8819-4ce5-49c6-98f3-27fe9e2e8e3d
ms.openlocfilehash: adae713306412ffa315ed6a5ccc990e81835552f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509556"
---
# <a name="system-event-log-cannot-be-deleted"></a><span data-ttu-id="16146-102">Protokol událostí systému nelze odstranit.</span><span class="sxs-lookup"><span data-stu-id="16146-102">System event log cannot be deleted</span></span>
<span data-ttu-id="16146-103">Byl proveden pokus o odstranění protokolu událostí systému, kterou nejde odstranit.</span><span class="sxs-lookup"><span data-stu-id="16146-103">An attempt has been made to delete the system event log, which cannot be deleted.</span></span> <span data-ttu-id="16146-104">Systémového protokolu se sleduje systémové události, jako je například selhání spuštění a hardware systému.</span><span class="sxs-lookup"><span data-stu-id="16146-104">The system log tracks system events such as system startup and hardware failures.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="16146-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="16146-105">To correct this error</span></span>  
  
-   <span data-ttu-id="16146-106">Zvažte, jestli by vaše aplikace napsat do aplikace nebo vlastního protokolu, nikoli protokol událostí systému.</span><span class="sxs-lookup"><span data-stu-id="16146-106">Consider having your application write to an application or custom log, rather than the system event log.</span></span>  
  
-   <span data-ttu-id="16146-107">Nepokoušejte se smazat protokol událostí systému.</span><span class="sxs-lookup"><span data-stu-id="16146-107">Do not attempt to delete the system event log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16146-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="16146-108">See also</span></span>
- [<span data-ttu-id="16146-109">Správa protokolů událostí</span><span class="sxs-lookup"><span data-stu-id="16146-109">Administering Event Logs</span></span>](https://msdn.microsoft.com/library/35f53238-bdd2-417b-acd8-2fd9f7397f18)
- [<span data-ttu-id="16146-110">Postupy: Vytvářet a odstraňovat vlastní protokoly událostí</span><span class="sxs-lookup"><span data-stu-id="16146-110">How to: Create and Remove Custom Event Logs</span></span>](https://msdn.microsoft.com/library/af9b7da0-80c7-46ac-b7f7-897063ddd503)
