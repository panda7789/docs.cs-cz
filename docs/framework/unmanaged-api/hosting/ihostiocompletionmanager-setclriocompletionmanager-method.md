---
title: IHostIoCompletionManager::SetCLRIoCompletionManager – metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetCLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager method [.NET Framework hosting]
- SetCLRIoCompletionManager method [.NET Framework hosting]
ms.assetid: 4254bb01-3a14-4f34-a3be-60ff1f5072b5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 97d4561c34c03eefc7487f5f96b7a490a480ac19
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780759"
---
# <a name="ihostiocompletionmanagersetclriocompletionmanager-method"></a><span data-ttu-id="18443-102">IHostIoCompletionManager::SetCLRIoCompletionManager – metoda</span><span class="sxs-lookup"><span data-stu-id="18443-102">IHostIoCompletionManager::SetCLRIoCompletionManager Method</span></span>
<span data-ttu-id="18443-103">Poskytuje ukazatel rozhraní na hostiteli [iclriocompletionmanager –](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implementován modulem common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="18443-103">Provides the host with an interface pointer to the [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18443-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18443-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRIoCompletionManager (  
    [in] ICLRIoCompletionManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18443-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="18443-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="18443-106">[in] Ukazatel rozhraní k `ICLRIoCompletionManager` instance k dispozici modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="18443-106">[in] An interface pointer to an `ICLRIoCompletionManager` instance provided by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="18443-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="18443-107">Return Value</span></span>  
  
|<span data-ttu-id="18443-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="18443-108">HRESULT</span></span>|<span data-ttu-id="18443-109">Popis</span><span class="sxs-lookup"><span data-stu-id="18443-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="18443-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="18443-110">S_OK</span></span>|<span data-ttu-id="18443-111">`SetCLRIoCompletionManager` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="18443-111">`SetCLRIoCompletionManager` returned successfully.</span></span>|  
|<span data-ttu-id="18443-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="18443-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="18443-113">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="18443-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="18443-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="18443-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="18443-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="18443-115">The call timed out.</span></span>|  
|<span data-ttu-id="18443-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="18443-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="18443-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="18443-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="18443-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="18443-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="18443-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="18443-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="18443-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="18443-120">E_FAIL</span></span>|<span data-ttu-id="18443-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="18443-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="18443-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="18443-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="18443-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="18443-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18443-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="18443-124">Remarks</span></span>  
 <span data-ttu-id="18443-125">Po CLR volal `SetCLRIoCompletionManager`, hostitel musí volat [iclriocompletionmanager::onComplete –](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) upozornit modul CLR, požadavek na vstupně-výstupní operace byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="18443-125">After the CLR has called `SetCLRIoCompletionManager`, the host must call [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) to notify the CLR when an I/O request has been completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18443-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="18443-126">Requirements</span></span>  
 <span data-ttu-id="18443-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18443-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18443-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="18443-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="18443-129">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="18443-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="18443-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18443-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18443-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18443-131">See also</span></span>

- [<span data-ttu-id="18443-132">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18443-132">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="18443-133">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18443-133">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
