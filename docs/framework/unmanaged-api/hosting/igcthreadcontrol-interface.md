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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c00f401bedc1a2810c4e9b3046a45e53a79f1ea
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134261"
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="5d2d4-102">IGCThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d2d4-102">IGCThreadControl Interface</span></span>
<span data-ttu-id="5d2d4-103">Poskytuje metody pro účast při plánování vláken, která by se jinak zablokovaly pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="5d2d4-103">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5d2d4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5d2d4-104">Methods</span></span>  
  
|<span data-ttu-id="5d2d4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5d2d4-105">Method</span></span>|<span data-ttu-id="5d2d4-106">Popis</span><span class="sxs-lookup"><span data-stu-id="5d2d4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5d2d4-107">SuspensionEnding – metoda</span><span class="sxs-lookup"><span data-stu-id="5d2d4-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="5d2d4-108">Upozorňuje hostitele, že modul runtime obnovuje po uvolnění paměti nebo jiných pozastavení vlákna.</span><span class="sxs-lookup"><span data-stu-id="5d2d4-108">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="5d2d4-109">SuspensionStarting – metoda</span><span class="sxs-lookup"><span data-stu-id="5d2d4-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="5d2d4-110">Upozorňuje hostitele, že modul runtime zahajuje pozastavení vláken pro uvolnění paměti nebo jiných pozastavení.</span><span class="sxs-lookup"><span data-stu-id="5d2d4-110">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="5d2d4-111">ThreadIsBlockingForSuspension – metoda</span><span class="sxs-lookup"><span data-stu-id="5d2d4-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="5d2d4-112">Upozorňuje hostitele, že vlákno uskutečněním hovoru se chystáte se zablokovat, případně pro uvolnění paměti nebo jiných pozastavení.</span><span class="sxs-lookup"><span data-stu-id="5d2d4-112">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5d2d4-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5d2d4-113">Requirements</span></span>  
 <span data-ttu-id="5d2d4-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d2d4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d2d4-115">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5d2d4-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5d2d4-116">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5d2d4-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="5d2d4-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="5d2d4-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5d2d4-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d2d4-118">See also</span></span>

- [<span data-ttu-id="5d2d4-119">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="5d2d4-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
