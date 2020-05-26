---
title: IGCThreadControl – rozhraní
ms.date: 03/30/2017
api_name:
- IGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCThreadControl
helpviewer_keywords:
- IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 3ff04d75-85ac-4df9-886d-dbaa037c0552
topic_type:
- apiref
ms.openlocfilehash: 78e667acf1573769a1a67b4c964d7801f11838fe
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805129"
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="d81ad-102">IGCThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d81ad-102">IGCThreadControl Interface</span></span>
<span data-ttu-id="d81ad-103">Poskytuje metody pro účast v plánování vláken, která by jinak byla zablokována pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="d81ad-103">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d81ad-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d81ad-104">Methods</span></span>  
  
|<span data-ttu-id="d81ad-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d81ad-105">Method</span></span>|<span data-ttu-id="d81ad-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d81ad-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d81ad-107">SuspensionEnding – metoda</span><span class="sxs-lookup"><span data-stu-id="d81ad-107">SuspensionEnding Method</span></span>](igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="d81ad-108">Upozorňuje hostitele, že modul runtime obnovuje vlákna po uvolnění paměti nebo jiném pozastavení.</span><span class="sxs-lookup"><span data-stu-id="d81ad-108">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="d81ad-109">SuspensionStarting – metoda</span><span class="sxs-lookup"><span data-stu-id="d81ad-109">SuspensionStarting Method</span></span>](igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="d81ad-110">Upozorňuje hostitele, že modul runtime zahajuje pozastavení vlákna pro uvolňování paměti nebo jiné pozastavení.</span><span class="sxs-lookup"><span data-stu-id="d81ad-110">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="d81ad-111">ThreadIsBlockingForSuspension – metoda</span><span class="sxs-lookup"><span data-stu-id="d81ad-111">ThreadIsBlockingForSuspension Method</span></span>](igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="d81ad-112">Upozorní hostitele, že vlákno, které provádí volání, je zablokované, třeba pro uvolňování paměti nebo jiné pozastavení.</span><span class="sxs-lookup"><span data-stu-id="d81ad-112">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d81ad-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d81ad-113">Requirements</span></span>  
 <span data-ttu-id="d81ad-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d81ad-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d81ad-115">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d81ad-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d81ad-116">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d81ad-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d81ad-117">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d81ad-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d81ad-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="d81ad-118">See also</span></span>

- [<span data-ttu-id="d81ad-119">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="d81ad-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
