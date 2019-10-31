---
title: ICorConfiguration::SetGCThreadControl – metoda
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCThreadControl
helpviewer_keywords:
- ICorConfiguration::SetGCThreadControl method [.NET Framework hosting]
- SetGCThreadControl method [.NET Framework hosting]
ms.assetid: 72e38e61-3d56-4ae3-b8f6-0ab7922aaf11
topic_type:
- apiref
ms.openlocfilehash: f43ee6d9a3832fca1766ec27c9f02d1aab2f5b8d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127762"
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a><span data-ttu-id="49963-102">ICorConfiguration::SetGCThreadControl – metoda</span><span class="sxs-lookup"><span data-stu-id="49963-102">ICorConfiguration::SetGCThreadControl Method</span></span>
<span data-ttu-id="49963-103">Nastaví rozhraní zpětného volání pro plánování vláken pro neběhové úlohy, které by jinak bylo zablokováno pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="49963-103">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49963-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49963-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49963-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="49963-105">Parameters</span></span>  
 `pGCThreadControl`  
 <span data-ttu-id="49963-106">pro Ukazatel na objekt [IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) , který upozorňuje hostitele na pozastavení vláken pro úlohy mimo běhu.</span><span class="sxs-lookup"><span data-stu-id="49963-106">[in] A pointer to an [IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) object that notifies the host about the suspension of threads for non-runtime tasks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49963-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="49963-107">Remarks</span></span>  
 <span data-ttu-id="49963-108">Hostitel se může vybrat v rámci zpětného volání [IGCThreadControl:: ThreadIsBlockingForSuspension –](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) , bez ohledu na to, jestli má vlákno přeplánovat.</span><span class="sxs-lookup"><span data-stu-id="49963-108">The host may choose within the [IGCThreadControl::ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49963-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="49963-109">Requirements</span></span>  
 <span data-ttu-id="49963-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49963-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49963-111">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="49963-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="49963-112">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="49963-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="49963-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49963-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49963-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="49963-114">See also</span></span>

- [<span data-ttu-id="49963-115">ICorConfiguration – rozhraní</span><span class="sxs-lookup"><span data-stu-id="49963-115">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
