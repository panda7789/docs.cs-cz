---
title: Protokol událostí systému nelze odstranit.
ms.date: 07/20/2015
ms.assetid: 26ca8819-4ce5-49c6-98f3-27fe9e2e8e3d
ms.openlocfilehash: 3dc4d624bcc0b559e9f61f51c58926588f24ee45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33639295"
---
# <a name="system-event-log-cannot-be-deleted"></a><span data-ttu-id="494ad-102">Protokol událostí systému nelze odstranit.</span><span class="sxs-lookup"><span data-stu-id="494ad-102">System event log cannot be deleted</span></span>
<span data-ttu-id="494ad-103">Byl proveden pokus o odstranění protokolu událostí systému, kterou nejde odstranit.</span><span class="sxs-lookup"><span data-stu-id="494ad-103">An attempt has been made to delete the system event log, which cannot be deleted.</span></span> <span data-ttu-id="494ad-104">Protokol systému sleduje systémové události, jako je například selhání spuštění a hardwaru systému.</span><span class="sxs-lookup"><span data-stu-id="494ad-104">The system log tracks system events such as system startup and hardware failures.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="494ad-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="494ad-105">To correct this error</span></span>  
  
-   <span data-ttu-id="494ad-106">Uvažujte aplikace zapisovat do aplikace nebo vlastního protokolu, nikoli protokol událostí systému.</span><span class="sxs-lookup"><span data-stu-id="494ad-106">Consider having your application write to an application or custom log, rather than the system event log.</span></span>  
  
-   <span data-ttu-id="494ad-107">Nepokoušejte se odstranit protokol událostí systému.</span><span class="sxs-lookup"><span data-stu-id="494ad-107">Do not attempt to delete the system event log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="494ad-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="494ad-108">See Also</span></span>  
 [<span data-ttu-id="494ad-109">Správa protokolů událostí</span><span class="sxs-lookup"><span data-stu-id="494ad-109">Administering Event Logs</span></span>](http://msdn.microsoft.com/library/35f53238-bdd2-417b-acd8-2fd9f7397f18)  
 [<span data-ttu-id="494ad-110">Postupy: vytváření a odebrání vlastní protokoly událostí</span><span class="sxs-lookup"><span data-stu-id="494ad-110">How to: Create and Remove Custom Event Logs</span></span>](http://msdn.microsoft.com/library/af9b7da0-80c7-46ac-b7f7-897063ddd503)
