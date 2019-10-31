---
title: IHostTask::Start – metoda
ms.date: 03/30/2017
api_name:
- IHostTask.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Start
helpviewer_keywords:
- IHostTask::Start method [.NET Framework hosting]
- Start method, IHostTask interface [.NET Framework hosting]
ms.assetid: b18742b0-d8c4-401c-ae89-e6eccdaa81d0
topic_type:
- apiref
ms.openlocfilehash: fe93a3bab267ccca941974b734c86329ad0f4d03
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121339"
---
# <a name="ihosttaskstart-method"></a><span data-ttu-id="810f6-102">IHostTask::Start – metoda</span><span class="sxs-lookup"><span data-stu-id="810f6-102">IHostTask::Start Method</span></span>
<span data-ttu-id="810f6-103">Požaduje, aby hostitel přesunul úlohu představovanou aktuální instancí [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) z pozastaveného do aktivního stavu, ve kterém lze spustit kód.</span><span class="sxs-lookup"><span data-stu-id="810f6-103">Requests that the host move the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance from a suspended to a live state, in which code can be executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="810f6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="810f6-104">Syntax</span></span>  
  
```cpp  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="810f6-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="810f6-105">Return Value</span></span>  
  
|<span data-ttu-id="810f6-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="810f6-106">HRESULT</span></span>|<span data-ttu-id="810f6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="810f6-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="810f6-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="810f6-108">S_OK</span></span>|<span data-ttu-id="810f6-109">Začátek se úspěšně vrátil.</span><span class="sxs-lookup"><span data-stu-id="810f6-109">Start returned successfully.</span></span>|  
|<span data-ttu-id="810f6-110">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="810f6-110">E_FAIL</span></span>|<span data-ttu-id="810f6-111">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="810f6-111">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="810f6-112">Když metoda vrátí E_FAIL, modul CLR (Common Language Runtime) již nebude v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="810f6-112">When a method returns E_FAIL, the common language runtime (CLR) is no longer usable within the process.</span></span> <span data-ttu-id="810f6-113">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="810f6-113">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="810f6-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="810f6-114">Remarks</span></span>  
 <span data-ttu-id="810f6-115">`Start` vždy vrátí hodnotu HRESULT s výjimkou případů, kdy došlo k závažným chybám.</span><span class="sxs-lookup"><span data-stu-id="810f6-115">`Start` always returns an HRESULT value of S_OK, except in cases where a catastrophic failure has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="810f6-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="810f6-116">Requirements</span></span>  
 <span data-ttu-id="810f6-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="810f6-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="810f6-118">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="810f6-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="810f6-119">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="810f6-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="810f6-120">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="810f6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="810f6-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="810f6-121">See also</span></span>

- [<span data-ttu-id="810f6-122">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="810f6-122">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="810f6-123">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="810f6-123">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="810f6-124">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="810f6-124">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="810f6-125">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="810f6-125">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
