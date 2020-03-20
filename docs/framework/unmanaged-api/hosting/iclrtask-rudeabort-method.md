---
title: ICLRTask::RudeAbort – metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.RudeAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::RudeAbort
helpviewer_keywords:
- RudeAbort method, ICLRTask interface [.NET Framework hosting]
- ICLRTask::RudeAbort method [.NET Framework hosting]
ms.assetid: b5785468-fcd7-4cc3-8a5d-8796337b53fc
topic_type:
- apiref
ms.openlocfilehash: aacf9de36dc39b63ed36b672e31f40704413d608
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176328"
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="ffa05-102">ICLRTask::RudeAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="ffa05-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="ffa05-103">Dává pokyn modulu CLR (COMMON Language runtime) k okamžitému a bezpodmínečnému přerušení úlohy reprezentované aktuální instancí [rozhraní ICLRTask.](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)</span><span class="sxs-lookup"><span data-stu-id="ffa05-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffa05-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ffa05-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();
```  
  
## <a name="return-value"></a><span data-ttu-id="ffa05-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ffa05-105">Return Value</span></span>  
  
|<span data-ttu-id="ffa05-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ffa05-106">HRESULT</span></span>|<span data-ttu-id="ffa05-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ffa05-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ffa05-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="ffa05-108">S_OK</span></span>|<span data-ttu-id="ffa05-109">`RudeAbort`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="ffa05-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="ffa05-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ffa05-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ffa05-111">CLR nebyl načten do procesu nebo CLR je ve stavu, ve kterém nelze spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="ffa05-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ffa05-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ffa05-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ffa05-113">Časový čas hovoru byl vypován.</span><span class="sxs-lookup"><span data-stu-id="ffa05-113">The call timed out.</span></span>|  
|<span data-ttu-id="ffa05-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ffa05-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ffa05-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="ffa05-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ffa05-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ffa05-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ffa05-117">Událost byla zrušena, zatímco na ní čekalo blokované vlákno nebo vlákno.</span><span class="sxs-lookup"><span data-stu-id="ffa05-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ffa05-118">E_fail</span><span class="sxs-lookup"><span data-stu-id="ffa05-118">E_FAIL</span></span>|<span data-ttu-id="ffa05-119">Došlo k neznámému katastrofickému selhání.</span><span class="sxs-lookup"><span data-stu-id="ffa05-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ffa05-120">Když metoda vrátí E_FAIL CLR již není použitelný v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="ffa05-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ffa05-121">Následná volání metod hostování vrátí HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ffa05-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ffa05-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ffa05-122">Remarks</span></span>  
 <span data-ttu-id="ffa05-123">Hostitel volá `RudeAbort` okamžitě přerušit úlohu.</span><span class="sxs-lookup"><span data-stu-id="ffa05-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="ffa05-124">Finalizační metody a rutiny zpracování výjimek není zaručeno, že budou provedeny.</span><span class="sxs-lookup"><span data-stu-id="ffa05-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffa05-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ffa05-125">Requirements</span></span>  
 <span data-ttu-id="ffa05-126">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffa05-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffa05-127">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ffa05-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ffa05-128">**Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ffa05-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ffa05-129">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffa05-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffa05-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="ffa05-130">See also</span></span>

- [<span data-ttu-id="ffa05-131">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ffa05-131">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="ffa05-132">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ffa05-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="ffa05-133">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ffa05-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="ffa05-134">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ffa05-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
